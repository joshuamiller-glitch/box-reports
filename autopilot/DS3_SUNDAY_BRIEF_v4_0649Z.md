# DS3_SUNDAY_BRIEF — v4 (stamp = file mtime; rewritten every 4 h). Deadline Sun 2026-11-01 12:00 ET = 17:00Z.
Nothing below is a PASS. Units: $k/week vs the stack as it is, lock engine, basis N, Native 1.28 stop unless stated. LIVE lots = K6 2, P6 7, U6 4, H6 4 Asia / 2 NY-AM, M6 2, A6 1 (PRE and CLOSE lot 0). RESEARCH = ST10 HM10 WT7 KB5.2 SM7.4 PE5.6. Tags: K6=KB, P6=PE, U6=SM, H6=HM, M6=MV, A6=PB, S6=ST, W6=WT. "Live = research/2.35" is an assumption that can differ 1.6x-6x from the engine at live-session lots. Detail: DS3_SUNDAY_STACK_2, DS3_UNIT_AUDIT (Brief table), DS3_SUNDAY_RISK, DS3_ER_SIZER_ROBUSTNESS, DS3_DEFECT_SWEEP, DS3_CAPPED_RERUN, FORWARD_SHADOW_RUNBOOK.

## HAZARDS (read first)
1. Recent edges do not persist: positive in the last 3 and 6 months -> positive in the next 3 months 41% of the time (CI 36-47%) vs 50% sign-flip noise, 44% same-mean baseline (RE-1); walk-forward 2024-26 of running the ledger at full size -9.6k/wk research (inside MDE 27k: not demonstrated); only 6-month t >= 3 persists (70-83%). Five of the six composite pieces were chosen after seeing L6M/HOLD.
2. Forward shadow reads are slow (pre-registered rule): ~60 weeks ER sizer, ~66 PE 45-s, ~67 second-signal skip, ~79 KB sizer, ~116 Asia cut, ~166 zone skip, ~230 HM FVG. By 13 weeks only harm/futility and live execution (fills, fire rates, governor reading) can be read.
3. Governor spec: the ER sizer's gain needs day/week locks = R x RUNNING MAX of today's ER multipliers (updated at each signal; reset at the day rollover). Planned-lot locks: sizer +2.7k L6M / -2.4k PRE (live+); day-static (not implementable) +14.1k; opener-fixed negative.
4. Much of each stack gain is lock-engine re-entry that live trading cannot be assumed to reproduce (share of L6M gain: split 47-55%, PE 58%, Asia cut 71%, second-signal 73%, 8-line skip 85%, KB sizer 88%, ER sizer 200% gross / 32% net); every candidate has > 50% of its gain in 5 weeks (the ER sizer 107%: without its top 5 weeks it is -1.1k/wk).
5. Verdict hygiene this week: defects mostly INFLATED earlier results (look-ahead vol tag, unbounded windows, per-contract-of-final-lots unit, paired-on-both-traded-days, duplicated candles, pts-scaled size-up stacks): the OFF list stands. Capping old windows at 2026-02-06 erodes struct48-era survivors (18 PASS -> 5; 6 independent exposures; year-share gate) while the live ST10 baseline improves (WF 15.1k t 2.8; HOLD 21.3k t 2.0) and HM10 weakens (HOLD 8.8k, t 0.9).

## A. SUNDAY STACK AS CODED (SS-2). CANDIDATE-RECENT
Pieces: 70/30 split + 8-line zone skip + ER(20) 5-m sizer (x1.5 >= 0.30, x0.5 below) + PE 45-s confirmation (NY, market at the confirming close, then 70/30) + Asia-stopped cut50 + Native stop. Live lots, causal running-max locks, 8 books:
| | L6M (MDE) | HOLD (MDE) | PRE (MDE) | X' (MDE) |
|---|---|---|---|---|
| D6 vs stack as it is | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
Risk (RK-1, as-is -> D6, live, $k/wk): L6M mean 24.0 -> 42.6, SD 47 -> 42, maxDD 92 -> 27; HOLD 23.7 -> 39.9, maxDD 144 -> 93; PRE 17.7 -> 22.4, maxDD 210 -> 232, worst-20 -874 -> -905 (not distinguishable). D6 raises the tail in NO window; it lowers it in L3M/L6M only through one week (2026-01-19: -91.8k as-is vs -27.2k). At equal worst-20 (D6 x1.083): +11.4k/wk full period [+4.8, +17.7]. The ER sizer alone is the only piece that clearly heavies the tail. Native stop 1.28 applies to all books but was measured on ST/HM only (+1.5k live vs join 2.45); with the join stop for all: LIVE-CAL +16.2k L6M. Half-up integer rounding of ER lots: +22.8k vs +18.5k fractional (more lots, not more edge). Cumulative-adjusted p 1.00; Romano-Wolf (PRE) 0.79. The one change before 18:00 ET: NONE to the pieces; one specification to D6: the running-max lock multiplier.

## B. ON (your decision)
| Rule | D6 | Evidence | Caveat |
|---|---|---|---|
| 70/30 split, dip 3 pt (the only PRE-selected piece) | `entry * * dip_X=3 basis=i confirmations_N=1 gates=default8 veto_imb5=-0.40 chase_Y=off split_F=0.7 limit_join_s=0 eval=1s` (THP v2) | one engine, six books, L6M: +5.4 live-session lots / +17.6 research (vs market); at integer live lots with modelled add slippage +4.8 (N) / +5.3 (LIVE-CAL); per book (research lots) U6 +3.0, H6 +0.8, P6 +0.8, K6 -3.0 (negative in L3M/L6M/HOLD/PRE) | structure; add slippage model +0.25 pt/lot (stress +0.45) vs break-evens +1 (PRE) / +2.3 pt (L6M); THP v2 has a P6 market-entry line: P6 does not split unless deleted |
K6 add: keep (composite +0.4..+0.7, inside MDE; default) or drop (K6 book alone -3.0k L6M at research lots, inside MDE): your call. 90/10-at-8 is an alternative only for P6 (6/1; rounds to market at K6/U6/H6 lots).

## C. SHADOW (paper), all inside MDE, all post-hoc. "Needs D6" = feature D6 v2 lacks
| Rule | L6M live-session / research (one engine) | Needs D6 | Note |
|---|---|---|---|
| ER(20) sizer, six books | +19.3 / +37.3 (running-max); +8.6 / +8.5 (planned-lot); within the composite at integer lots +12.5 (MDE 23.5), HOLD +13.7, PRE +9.5, X' +0.8; 200 shuffled-ER draws never reach it (p 0.005; the earlier "placebo earns +9k" included the other five pieces); lot-factor-matched line -2.0k | ER on closed 5-min bars (raw front-month closes), lot multiplier, running-max locks | per book (L6M): P6 +6.0, K6 +2.1, ST +3.2, WT +3.1 keep; U6 -0.8, H6 -0.2, M6 -0.7 drop; with planned-lot locks drop K6/U6/H6; A6 inconclusive |
| KB ER >= 0.20 sizer | +3.2 / +8.1 running-max; +1.4 / +3.1 planned | same | |
| PE 45-s three-bar, market at the confirming close, NY (also in the composite) | per planned lot L6M +3.29 coded (+3.57 pure wait; difference -0.65k, noise: keep coded); stack +2.4 / +3.0 | 45-s candle series; hold-until-confirmation = new order type | the value is NOT trading the 40% unconfirmed signals; RC 0.74; no live NY-PM PE lots |
| 8-line zone skip D=20 | +3.9 / +15.4 (HOLD research +12.4); the zones addendum engine says +28.3/+25.7 | rolling 8-line file | lines post-hoc; discovery chain fails forward; 85% re-entry; the LEVEL is not the information |
| Asia-stopped cut50 | +9.1 / +13.2 | stack state, cross-book exit | weakest piece in the composite (~0 live) |
| Stop-join: Native stop-market for ST/HM | +1.5 live (CI +0.9..+2.3) / +4.1 research | order type | A/B spec FORWARD_STOP_AB.md (~200 stops per arm) |
| NY-PM end skip (14:40-15:00 ET), clock only | research L6M +4.7 (MDE 4.1), positive all five windows; per signal ~0 | clock | books split (PE SM HM ST WT +; KB PB MA -) |
Not on the list: second-signal skip (+0.6 / +5.6; PRE negative), ES-led sizer (OFF: ~0, fragile to 1-3 s delay), HM FVG skip (not decidable), KB chop gate and book-lean skip (OFF).

## D. OFF (tested)
All exits keyed on price, path, time, signal state, forecast or mirror (all books incl. WT MV DN PB MA CR O6 iFVG: 0 of 85k cells); brackets; L2 trade-health rules on entry, profit and loss (IC <= 0.03-0.07 vs break-even 0.3-0.65; 29 cycles); sub-minute events; bar types as base (paired "wins" were noise); zones/POI as location, target or no-trade (the 11-line discovery fails forward); expanded no-trade states (0 PASS); cross-day tags; entry timing; stack partials; risk-off, halt-resume (12R week floor never fires), quit-when-up (-45k) on my interpretations; size-up rows from NTZ-1/ZONES-2 (inflated by pts scaling; negative on the corrected route).

## E. OPEN QUESTIONS (defaults; the rest in MORNING.md)
1. D6 lock multiplier = running max of the day's ER multipliers [specify]; today planned-lot or sized-lot R?
2. ER lot rounding on 1-2 lot books [half-up; fractional in the headline]. 3. K6 add [keep]. 4. P6 market-entry line in THP v2 [leave].
5. Live add-fill slippage per lot [model +0.25, stress +0.45]. 6. Live lots/sessions as listed? A6 = PB or PB7? [PB].
7. Original RISK-OFF / HALT-RESUME / QUIT-WHEN-UP texts [re-paste]; D6 week-floor R basis.
8. Money/data: HM forward feed = weekly NQ ohlcv-1s, ~$1.15/wk, first window Sat 11-07 [your OK]; raw MBO ($214 L6M slice, budget ~$811) [no]; paper-log books [yes]; leaderboard treatment of capped tiers [keep tier + capped column].
