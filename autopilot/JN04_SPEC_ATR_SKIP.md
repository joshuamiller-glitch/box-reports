# JN04_SPEC_ATR_SKIP - P7 ATR >= 1.6x median skip, exact live definition for D7 v1.6 (SZ-FGH, 2026-11-10 16:02Z)

> Label: EXACT engine rows (ROLLFIX1 patched S1b engine) where stated; PRE-PROOF; post-hoc; Shadow only; no PASS claim. The rule was selected as the best of 854 first-order H cells (family p ~1, own-draw placebo p .02), so it is a LEAD+, not a CANDIDATE. Layers stay ON: this is an ADDITIONAL P7 entry gate, nothing is dropped.

## 1. The rule (what D7 v1.6 must compute)
1. **Scope.** P7 only, every session in the P7 session table (asia, london, nyam; the table 7,4,0,4,0,0 gives P7 no lots in pre / nypm / close). Not applied to K7, M7, U7, A7, H7, O7.
2. **Action.** At the entry decision of a P7 signal, if the test below is true the signal is SKIPPED: lots x0, no order, no slice, no L2-gate arm. It is not retried later for the same signal. Every other layer (Q1-A, zones HALF, L2 gate, state cut, locks, day cap 8,400, session table 7/4/4, P7 cut) runs unchanged on the signals that pass.
3. **Evaluation moment.** The signal second (the second at which the P7 strategy decides to enter, the `sig_ns` of the trade). The inputs are only bars COMPLETED at or before that second: the last completed 5-minute bar is the one whose end time is <= the signal second (a bar ending exactly at the signal second counts as completed).
4. **ATR.** NinjaTrader-style ATR(14) on NQ 5-minute bars (NQ front month, 24 h chart, one 5-min series): TR = max(High-Low, |High-PrevClose|, |Low-PrevClose|) (first bar: High-Low); Wilder smoothing ATR = ((14-1) x ATR_prev + TR) / 14, seeded with the mean of the first 14 TRs (NT8 `ATR(14)`; the seed is irrelevant after warm-up). Units: index points. ATR_now = the ATR of the last completed 5-minute bar (see 3).
5. **Median (the denominator).** For every TRADING DAY (day label rolls at 17:00 ET: the trading day runs 18:00 ET of the previous calendar day to 17:00 ET; Sunday evening belongs to Monday) take the median of ATR(14) sampled at every 5-minute bar close of that trading day (about 276 values; equivalent to the per-minute forward-filled sampling used in research). Median_ref = the median of the daily medians of the 20 trading days BEFORE the signal's trading day (the current day is excluded; a day with data counts; at least 5 prior days are required, otherwise the test is false). Updated once per day at the trading-day rollover; the research uses one global median (all sessions pooled), not per-session medians.
6. **Test.** ratio = ATR_now / Median_ref. **Skip if ratio >= 1.6** (greater-or-equal; exactly 1.6 skips). If ATR_now or Median_ref is unavailable (fewer than 5 prior trading days, no completed bar within 15 minutes of the signal) the test is FALSE (enter normally).
7. **Ties / rounding.** Compare in double precision on the unrounded ATR values; there is no hysteresis and no persistence requirement. Borderline ratios (within about 0.01 of 1.6) can flip between implementations (4 of 5,270 P7 signals differ between the research code and an independent re-implementation); that is inside the noise of NT's ATR seed.
8. **Not computable by the strategy from its own chart without care** (named per the order):
   - 20 prior trading days of 5-minute ATR history must be loaded (at least 1,700 five-minute bars plus ATR warm-up: set BarsRequiredToTrade / days to load >= 25 trading days) or the median must be persisted across restarts.
   - The chart must be the single front-month NQ series with the roll handled: the research removes contract-roll jumps (every >120 pt gap between consecutive 1-min bars within 5 minutes, i.e. the quarterly rolls about 00:00 UTC Mar/Jun/Sep/Dec) before computing TR. On an unadjusted NT chart the roll bar adds one false TR of about 180-280 points for the next hours; use a back-adjusted merge policy or discard the TR of the roll bar.
   - The research bars are mid-session 1-min NQ bars aggregated to 5-min; NT 5-min bars built from tick data are the same bars (bar boundaries at :00/:05 ET clock).

## 2. Verification that the written rule reproduces the exact trade set
Independent re-implementation of the text above from the raw 1-min NQ bars (code/th_sz/fgh_atrspec.py, written from the rule, not from the research feature code). Over all 5270 P7 signals of the S1b-COMB list: skip by the written rule 1929, skip by the research M table (the table the exact run used) 1929, agreement 99.92% (4 borderline signals with ratio 1.592-1.604 flip). Against the EXACT run FGH_PBESTH (33 months: L6M, PRE, X'): of 1417 P7 signals the rule skips, 52 appear in the exact trade list (3.7%); of 2512 signals it keeps, 2440 appear (97.1%). The mismatches are second-order engine effects (a kept signal can be displaced or a later same-second re-entry can appear because the skipped trades change locks, day caps and open lots), not rule differences. The rule skips 36.6% of all P7 signals (36.1% in the exact months) and 52% of the skipped signals (L6M) were net losers at base lots (L6M: skipped signals net -22844 at base lots, kept signals net +435089).

## 3. Five worked rows (from the exact run FGH_PBESTH, L6M)
| signal time (ET) | side | session | ATR(14,5m) pts | Median_ref pts | ratio | decision | in the exact trade list? | base P&L of that signal (S1b-COMB lots) |
|--|--|--|--|--|--|--|--|--|
| 2026-06-10 04:27:00 | short | london | 38.42 | 23.93 | 1.606 | SKIP | no (skipped) | +4795 |
| 2026-10-01 03:49:00 | short | london | 40.30 | 19.36 | 2.082 | SKIP | no (skipped) | -3082 |
| 2026-06-25 11:42:00 | long | nyam | 114.52 | 27.31 | 4.193 | SKIP | no (skipped) | -1132 |
| 2026-05-05 10:03:00 | long | nyam | 24.33 | 17.00 | 1.431 | enter | yes | -4074 |
| 2026-05-04 23:22:00 | long | asia | 12.35 | 17.00 | 0.726 | enter | yes | +4800 |

## 4. Numbers
### 4a. Exact vs S1b-COMB live (earlier run, base without the P7 day cap and cut 40/5x; FGH_PBESTH, ROLLFIX1)
L6M cut +26.0 (d mean +1903), L3M +26.8 (+1817), PRE +35.6 (-262), X' see the EXACT block of SZ_FGH.md, worst-20 L6M +30. Rule 2a (floor = 25% of the live PRE mean): OK-PRIOR (old -$1k label also OK-PRIOR). Bi-weekly exact WF vs live: 36% of periods beat live (block 202402-202506).

### 4b. On the LIVE PANEL base (LPB_BASE: P7 day cap 8,400, 7/4/4 table, P7 cut 40/5x/w5/p3 ON) - EXACT, reference = LPB_BASE
Months present for both ATRSKIP_P7 and LPB_BASE: 39 (202307..202610). Windows reported only when complete.

| window | maxDD LPB (live panel) | maxDD with ATR skip | cut % | d mean $/wk | equal-mean cut % | worst-20 cut % (+ better) |
|--|--|--|--|--|--|--|
| L1M | 51253 | 35881 | +30.0 | -1073 | +33.4 | +892 |
| L2M | 51253 | 35881 | +30.0 | -323 | +33.4 | +6 |
| L3M | 77224 | 76858 | +0.5 | -308 | +5.3 | +8 |
| L6M | 77224 | 76858 | +0.5 | +945 | +5.3 | +61 |
| HOLD | 78842 | 85372 | -8.3 | +493 | -3.1 | +10 |
| MID | 78842 | 85372 | -8.3 | -2430 | -3.1 | -17 |
| PRE | 99479 | 83529 | +16.0 | -222 | +20.1 | +10 |

Rule 2a on the live-panel base (PRE mean floor = 25% of the live PRE mean = -3146 $/wk; bi-weekly WF on this base not yet computed): **OK-PRIOR-UNKNOWN-WF** (old fixed-floor label OK-PRIOR-UNKNOWN-WF).

Interaction note: on the live-panel base the L6M benefit of the ATR skip is +0.5% maxDD (d mean +945 $/wk) against +26.0% on the S1b-COMB base; the installed 7/4/4 table, the P7 day cap 8,400 and the P7 cut 40/5x absorb most of what the skip removed (a layer-overlap, exactly what T-JOINT is meant to expose). The +30% on L1M/L2M versus +0.5% on L3M/L6M is small-window noise: L1M and L2M contain only 3 and 7 weeks, so their maxDD rests on one or two episodes; the L3M/L6M window (11 and 24 weeks) is the one to read. The skip is therefore NOT recommended on top of the live panel unless PRE/X'/HOLD above show an independent gain.

## 5. Notes for the coder
- The M table of the exact run is keyed on (book, signal second); in v1.6 the test must be evaluated at the same second (before any slice, before the L2-gate arm).
- Because the rule removes about 37% of P7 signals over the full history (+$163k of base P&L skipped over 3.5 years, -$22.8k in L6M), it is a drawdown/regime filter that costs mean outside the recent window: PRE d mean -$262/wk, X' and HOLD in section 4. Read it with the label LEAD+.
- Shadow-only until the 2026-11-22 refit; nothing here changes the live panel today.
