# JN04_LIVE_SPEC - the four JN04 layers and the two shadow leads as coding-standard live rules (user order 2026-11-10 14:15Z; SHADOW ONLY; no PASS claims)

Assembled by SZ-IJK (JOINT). Written to be coded into D7 v1.6 as written. Evidence = the EXACT S1b engine on ROLLFIX1 (ROLL-FIXED). Companion pages: DS3_JN04_LIVE_DEFS.md (derivation, frozen-week examples), DS3_JOINT.md (stack tables).

## A. Naming - which object the exact run used (read this first)

| name in the order | what the exact JN04 run actually contains | id |
|---|---|---|
| LOT ("lot_P7_744 / cap") | **P7-only rolling-Calmar gate** (P7 shadow Calmar over the last 10 label days < 1.0 -> lots x0.5). It is NOT a lot table and NOT a cap. | p7_other:f4181da4c118 (my family I/K cell "K5 I3 book rolling Calmar on P7 only {D:10, mult:0.5, x:1.0}") |
| SIGQ | **all-books zone-distance gate**: dA >= 70th percentile of previous months -> x0.5 | signal_quality:b9a6edabcd7b (FGH qgate dA high 0.3 m0.5, scope ALL) |
| REG | **P7-only volatility regime**: 5-min ATR(14) / 20-day median-of-daily-medians >= 1.3 -> x0.5 | regime:f1f4301eae70 (FGH atr_rel_ge1.3, scope P7) |
| STACK | **same-side lots cap 6 in London, truncate**, all books | E|same_side_lots_cap|cap6_trunc|sess_london (SZ-CDE code 8) |

**The ids named in the order (SIGQ signal_quality:7f7622673f09 = qgate_x_er twap_slope_sg low q0.2 skip when ER low; REG regime:3cf7b58e25a6 = prior_trend_day halve; STACK E total_lots_cap; LOT lot_P7_744) belong to the first-order coordinate-descent optimum printed on the DS3_JOINT page, a different stack that was never run exact.** They are NOT in the exact JN04 and are not specified here; if the user wants those, they need their own exact runs.

**The 7/4/4 table and the day cap are separate from JN04.** The P7 session table 7,4,0,4,0,0 (the installed panel value; cell lot_P7_744 / FGH_P744 / KCAP) and the P7 day cap 8,400 (R1_3, P7MaxDailyLoss) are LIVE-PANEL BASE items, not JN04 layers: in the exact run JN04 = LOT + SIGQ + REG + STACK on top of the S1b-COMB base (whose P7 table is 7,7,0,7,0,0). JN03 and JP05 are stacks where the lot_P7_744 table REPLACES the Calmar gate; JN04 contains no table. Section E gives JN04 on top of the live panel base (744 table + 8,400 cap + P7 cut 40/5x/w5/p3), where the 744 table is part of the base.

## B. Composition, rounding and tie rules (all four layers)

1. Order for one signal: session lots (+ A06 slot half, B02 half) -> Q1-A ER half (ER(20) 5-min < 0.30 -> x0.5, round half up, min 1) -> **LOT, SIGQ, REG: each yields m in {1, 0.5}; lots = max(1, floor(lots_in x m_LOT x m_SIGQ x m_REG + 0.5))** (one rounding; two halvings = x0.25) -> zone HALF (x0.5, round half up, min 1) -> **STACK truncation** (below) -> order.
2. All thresholds are inclusive on the firing side (>= for SIGQ / REG, Calmar strictly < 1.0 for LOT). Any NaN / insufficient-history input = layer does not fire (multiplier 1). A layer never raises lots.
3. Evaluation moment = the signal second (the 1-min bar close at which the book signals), before the order is sized; the confirmation / L2 hold that follows does not re-evaluate it.
4. Exact-run implementation note: the evidence rows below were run in TABLE mode - one effective ratio per base signal (book, signal second), each layer rounded on its own and the product rounded again, applied after the Q1-A ladder and before zone HALF. The raw rule above (one rounding of the raw multipliers) differs from the table lots by 1 lot in 73 of 4,226 affected trades (1.7%), never by more than 1. STACK in the table is built from the BASE trades' state; a rule-mode run with the engine's own state (set JR01) is queued behind this order.

## C1. LOT - P7 rolling-Calmar gate

| item | definition |
|---|---|
| books / sessions | P7 only / all sessions |
| inputs | P7's own closed-trade P&L (net, fees included) per lot x its BASE lots (shadow equity; base lots = the lots P7 would trade with the live panel and none of the JN04 layers, so gated trades do not shrink the state), exit timestamps, the strategy's label-day clock (17:00 ET roll; Saturday/Sunday roll to Monday) |
| state | daily[d] = sum over P7 trades whose exit falls on label day d of (net P&L per lot x base lots). Window = the 10 label days before the signal's label day (business-day calendar Mon-Fri; a day without P7 exits counts as 0), the signal's own label day excluded entirely |
| statistic | path = cumulative sum of the 10 daily values starting from 0; S = path[10]; DD = max over the path of (running max - path) (including the start at 0); C10 = S / DD; if DD = 0 the layer does not fire |
| threshold / action | **C10 < 1.0 -> m_LOT = 0.5** (strict), else 1; applies to every P7 signal incl. re-entries |
| evaluation | at the P7 signal second; only trades closed (exit second) before the signal second enter the state |
| tie / edge rules | the state keeps updating from shadow base-lot P&L while the book is gated (it can switch itself back on); fewer than 10 prior label days: no gate; holidays are zero days |
| NOT computable from the chart alone | the SHADOW base-lot P&L: for every P7 trade the strategy must record what the trade would have made at base lots (net per lot x base lots); the live strategy has this in its own trade log but needs the base-lot number stored beside the executed number (new field, strategy-internal, no external data) |
| DS7 v1.4 fields | none (closest: group 12 RfLoserMode / RfLoserMins). **New v1.6 fields (proposed):** `P7PerfGateMode` (Off / Shadow / Live), `P7PerfGateBooks`="P7", `P7PerfGateDays`=10, `P7PerfGateCalmarBelow`=1.0, `P7PerfGateMult`=0.5 |

**Five worked rows from the exact JN04 run (L6M months; 418 P7 signals fired in L6M).**

| # | time ET | book / session / side | planned lots (base) | layer multiplier (table ratio) | Calmar10 / S10 ($) | JN04 exact lots | JN04 exact net $ | base net $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-05-24 19:01:00 | P7 / asia / long | 7 | 0.571 | -0.23 / -8649 | 4 | +4805 | +8407 |
| 2 | 2026-07-24 01:21:00 | P7 / asia / long | 4 | 0.500 | 0.17 / 9898 | 2 | -2084 | -2084 |
| 3 | 2026-08-06 21:39:00 | P7 / asia / short | 4 | 0.500 | -0.99 / -40671 | 2 | -2079 | -4154 |
| 4 | 2026-09-03 04:01:01 | P7 / london / long | 4 | 0.500 | -0.24 / -9845 | 1 | -1027 | -4079 |
| 5 | 2026-10-30 00:38:00 | P7 / asia / long | 4 | 0.500 | -0.76 / -37915 | 2 | -2039 | -4214 |

Note: "base net" is the S1b-COMB trade at base lots; the JN04 row is the engine re-run, so exits and re-entries can differ beyond the lot change. "layer multiplier" is the effective ratio the table used (rounded lots / planned lots, e.g. 4/7 = 0.571); the raw multiplier is 0.5. "JN04 exact lots" is the engine result with all four layers. Evidence rows (old base, ROLL-FIXED exact):

| exact set | what | L6M cut / d mean | HOLD (12 mo) cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD01 | JN04 minus LOT | +22.8 / +3205 | +38.0 / -321 | n/a / n/a | n/a / n/a | +16.3 / -3479 |

## C2. SIGQ - zone-distance signal-quality gate

| item | definition |
|---|---|
| books / sessions | all seven books / all sessions |
| inputs | the eight zone lines of the live no-trade set (PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62_15m, OTE705_15m, OTE79_15m) with their touched flags (the same PoiSet the NTZ layer maintains); entry price = close of the last closed 1-minute bar; side |
| feature | **dA = min over untouched lines with (line price - entry) x side > 0 of (line price - entry) x side**, in points, any distance; no such line -> dA undefined (layer does not fire) |
| threshold | **thr = the 70th percentile (numpy linear interpolation) of dA over all trades taken by all books in the previous calendar months** (history = every base-lot signal that became a trade, all books; the calendar month of the signal's label date; expanding window; active only when there are at least 200 history values and at least 6 prior months: the rule was inactive in 2023-04..2023-09) |
| action | **dA >= thr -> m_SIGQ = 0.5**, else 1 |
| evaluation | at the signal second; thr is fixed for the whole calendar month (recomputed at the first signal of a new month from previous months only) |
| tie / edge rules | NaN dA: no gate; equality fires; the live-frame check: zone lines must be in the same price frame as the entry price (raw contract prices) - on the live week after the weekend the rebuilt dA is 980+ pts, so a Shadow print must confirm the frame before Live |
| NOT computable from the chart alone | the cross-book history of dA values over previous months (needs the strategy to persist one dA per taken signal across restarts; strategy-internal) |
| DS7 v1.4 fields | none exact. Closest: group 14 SIGNAL-STATE FILTERS (Ss1..Ss4, feature PdAhead, template HalveTop3, SsMinHistory), but their rank is against the book's own history in terciles and the feature is the prior-day level, not zone lines. **New v1.6 fields (proposed):** `Ss5Mode`, `Ss5Feature`=ZoneAheadPts, `Ss5Template`=HalveAbove, `Ss5Quantile`=0.70, `Ss5PoolBooks`=true, `Ss5MinHistory`=200, `Ss5MinMonths`=6 |

**Five worked rows from the exact JN04 run (L6M; 501 signals fired in L6M).**

| # | time ET | book / session / side | planned lots (base) | layer multiplier (table ratio) | dA (pts) / thr70 (pts) | JN04 exact lots | JN04 exact net $ | base net $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-05-12 18:39:05 | P7 / asia / long | 4 | 0.500 | 156.6 / 88.0 | 2 | -2053 | -4222 |
| 2 | 2026-06-24 21:39:00 | K7 / asia / long | 2 | 0.500 | 760.6 / 89.2 | 1 | -727 | -2322 |
| 3 | 2026-07-23 00:30:02 | P7 / asia / long | 4 | 0.500 | 373.2 / 92.5 | 1 | -1005 | -4244 |
| 4 | 2026-09-03 00:09:01 | K7 / asia / long | 2 | 0.500 | 289.8 / 96.9 | 1 | -690 | -2372 |
| 5 | 2026-10-29 07:16:00 | P7 / london / long | 4 | 0.500 | 126.2 / 97.2 | 1 | -927 | -3419 |

Evidence rows (old base, exact):

| exact set | what | L6M cut / d mean | HOLD (12 mo) cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD02 | JN04 minus SIGQ | +44.9 / +4734 | +45.1 / -1602 | n/a / n/a | n/a / n/a | +9.4 / -7211 |

SIGQ is the weakest of the four layers (removing it leaves L6M cut +43.4 -> +44.9); drop it first if a simpler stack is wanted.

## C3. REG - P7 volatility-regime halving (and the same feature for the ATR-skip lead)

| item | definition |
|---|---|
| books / sessions | P7 only / all sessions |
| bars | 5-minute bars built from the 1-minute bars by epoch bucket (bucket = timestamp // 300), a 5-min bar is complete at its last 1-min bar |
| ATR | **atr5 = Wilder ATR(14) of the 5-min true range** (TR = max(H-L, |H-prevClose|, |L-prevClose|); seed = mean of the first 14 TR values; then ATR = ATR x 13/14 + TR/14; continuous over the whole history, prev close across session gaps) |
| baseline | for each trading date (18:00 ET start) the MEDIAN of atr5 over all 5-min bars of that date; **base = median of those daily medians over the previous 20 trading dates (not including the current date; at least 5 dates)** |
| feature | **atr_rel = atr5 at the signal / base**, atr5 = the value of the most recent 5-min bar completed at or before the signal second |
| threshold / action | **atr_rel >= 1.3 -> m_REG = 0.5** (P7 signals only) |
| evaluation | at the P7 signal second |
| tie / edge rules | atr_rel undefined (fewer than 5 prior dates or no completed bar): no gate; equality fires |
| NOT computable from the chart alone | nothing external: needs the 5-min bar history of the traded NQ contract for the previous 20 trading dates (continuous-contract price frame as used in the research: roll gaps removed) - the live chart must hold >= 21 days of 1-min or 5-min history |
| DS7 v1.4 fields | `Ss?Feature`=AtrRatio exists (DS7.cs 1104 atrNow/atrMed) but atrNow is a 14-RMA of 1-MINUTE true range and atrMed the median of the last 28,800 one-minute values; its templates rank by tercile. **New v1.6 fields (proposed):** `Ss6Mode`, `Ss6Books`="P7", `Ss6Feature`=AtrRel5m (definition above), `Ss6Template`=HalveAbove, `Ss6Threshold`=1.3 |

**Five worked rows from the exact JN04 run (L6M; 348 P7 signals fired in L6M).**

| # | time ET | book / session / side | planned lots (base) | layer multiplier (table ratio) | atr5 (pts) / atr_rel | JN04 exact lots | JN04 exact net $ | base net $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-05-11 21:55:00 | P7 / asia / short | 7 | 0.571 | 26.2 / 1.50 | 4 | -4062 | -6378 |
| 2 | 2026-06-10 20:28:00 | P7 / asia / long | 4 | 0.500 | 66.2 / 2.57 | 1 | +1199 | +3591 |
| 3 | 2026-07-10 10:45:00 | P7 / nyam / long | 4 | 0.500 | 67.0 / 2.36 | 1 | -1017 | -2024 |
| 4 | 2026-09-14 11:00:00 | P7 / nyam / long | 3 | 0.667 | 38.9 / 1.83 | 1 | +1199 | -804 |
| 5 | 2026-10-29 22:54:00 | P7 / asia / short | 4 | 0.500 | 34.4 / 1.41 | 1 | -1070 | -4384 |

Evidence rows (old base, exact):

| exact set | what | L6M cut / d mean | HOLD (12 mo) cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD03 | JN04 minus REG | +23.1 / +1660 | +38.3 / -1916 | n/a / n/a | n/a / n/a | -6.2 / -4993 |

## C4. STACK - same-side lots cap 6 in London (truncate)

| item | definition |
|---|---|
| books / sessions | all seven books / entry session London (02:00-08:29 ET by the signal clock) |
| inputs | the lots currently open in every other book (filled quantity of open positions; pending entries not counted), their side, the signal's side and its lots after the layers above |
| rule | **same = sum of open lots of the other books on the signal's side; room = 6 - same; if lots > room: lots = room (rounded, the truncated lots), and if room <= 0 the signal is SKIPPED; else unchanged** (note: a single signal larger than 6 lots with nothing open is truncated to 6) |
| action | truncate / skip (no halving factor) |
| evaluation | at the signal second, after all multiplier layers and zone HALF, using the positions open at that second |
| tie / edge rules | lots == room passes; opposite-side open lots do not count; the rule applies to re-entries and to sliced entries by their total lots |
| NOT computable from the chart alone | nothing external: needs the cross-book open-position view the strategy already has (StackOnStop enumerates same-side books, DS7.cs line 3090) |
| DS7 v1.4 fields | none (group 09 StackCut is stop-triggered, a different rule). **New v1.6 fields (proposed):** `ExpCapMode`, `ExpCapLots`=6, `ExpCapSessions`="0,1,0,0,0,0", `ExpCapBooks`="", `ExpCapSkipWhenFull`=true |

**Five worked rows from the exact JN04 run (L6M; 182 signals fired in L6M).** The table state counts the lots open in the cell-sized run, so the "same-side open (base lots)" column is only the base-trade view and can differ from the table decision; the multiplier is the table ratio the exact run used.

| # | time ET | book / session / side | planned lots (base) | layer multiplier (table ratio) | same-side open (base lots) / room / books open | JN04 exact lots | JN04 exact net $ | base net $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-05-13 04:37:00 | P7 / london / long | 7 | 0.857 | 0 / 6 / - | 3 | -3124 | -5198 |
| 2 | 2026-07-08 08:04:00 | P7 / london / long | 5 | 0.800 | 2 / 4 / K7 | 1 | +1199 | +5984 |
| 3 | 2026-08-12 05:31:01 | P7 / london / long | 7 | 0.857 | 0 / 6 / - | 2 | +2398 | +8382 |
| 4 | 2026-09-15 08:00:00 | P7 / london / long | 7 | 0.571 | 2 / 4 / M7 | 1 | +1199 | +8397 |
| 5 | 2026-10-29 04:02:00 | P7 / london / short | 7 | 0.571 | 6 / 0 / M7,U7 | 2 | -1874 | -3754 |

Evidence rows (old base, exact; JR01 = rule-mode STACK when done):

| exact set | what | L6M cut / d mean | HOLD (12 mo) cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD04 | JN04 minus STACK | +34.2 / -523 | +37.7 / -3064 | n/a / n/a | n/a / n/a | +4.0 / -6169 |
| JR01 | JN04 with STACK as the engine rule (cde code 8) - rule mode | n/a / n/a | n/a / n/a | n/a / n/a | n/a / n/a | n/a / n/a |

## D. The two shadow leads

### D1. P7 ATR skip (FGH_PBESTH, regime_gate atr_p7_skip16)

| item | definition |
|---|---|
| what | **P7 entries are SKIPPED (m = 0) when atr_rel >= 1.6**, atr_rel exactly as defined in C3 (Wilder ATR(14) of 5-min bars; baseline = median of the previous 20 trading dates' daily medians; signal-second value of the last completed 5-min bar) |
| books / sessions / action | P7 / all sessions / skip |
| DS7 fields | same new feature as REG: `Ss6Feature`=AtrRel5m with `Ss6Template`=SkipAbove, `Ss6Threshold`=1.6 (a second rule slot, or `Ss6Template` choice per threshold) |
| status | SZ-FGH writes its own section (to be pasted as written); the definition above is the cross-check: it reproduces FGH cell e18edff4f8d3 (rule text in the registry: "5-min ATR(14) >= 1.6 x prior-20-day median of the daily median ATR"). Exact rows: FGH_PBESTH (23 months: L6M +26.0, PRE +35.6), JQ06 = JN04 + this skip, JQ07 = JN04 with REG replaced by it (running behind this order). |

### D2. P7 post-stop same-side 30-minute blackout (R5_BO_3, cooldown_r5)

(Section by REDO-R5, included as written from autopilot/JN04_SPEC_POSTSTOP_BLACKOUT.md; the IJK cross-check of the rule against the exact rows is in section F.)

# JN04_SPEC_POSTSTOP_BLACKOUT - P7 post-stop / post-cut same-side 30-min blackout (R5_BO_3) as an exact live definition for D7 v1.6
REDO-R5, 2026-11-10 15:01Z. SHADOW / spec only, no PASS claim. **Label: LEAD (not CANDIDATE)**: exact windows below, placebo p .14 / .12, family p 1.00, HOLD window is deeper than live. Rule 2 / 2a: recents first (L6M +8%, d mean +$3.0k/wk); rule 2a PRE floor = 25% of the live PRE mean (PRE d mean +$10/wk is far inside it) -> OK-PRIOR; but the bi-weekly WF is a screen-only result and HOLD (-9%) fails, so no change is recommended on this evidence. This page only fixes WHAT the rule is, so it can be coded and run in Shadow.

## 1. The rule (exactly what the exact engine ran; code/th_r5/r5_hooks.py, `bo` key, exec_exit + try_entry)
- **Books:** P7 only (trigger book = blocked book = P7; no other book's exits trigger it, no other book's signals are blocked).
- **Trigger events (any one opens a window):** the full close of a P7 position (the last contract filled out) whose exit reason is
  1. **StateCut** (the v1.5 state loss cut; in the v1.4 file the same slot is the TH-L2 loss cut exit "ThL2Cut"),
  2. **Stop**: a stop exit of any of the three kinds the stop path produces - native stop ("Stop"), stop-join limit fill ("StopJoin"), stop-join market fallback ("StopJoinFallback"). The 80-pt catastrophe native stop, if it ever fills, is also a stop exit.
  **Not triggers:** Target, BookLock (give-back / week floor), StackCut, TimeBlock / session flat, RollFlat, day-halt exits, profit-take / tighten trail exits ("ThL2Trail", "PolicyTake"), partial target fills that leave contracts open. A **profit** exit never triggers it.
- **Side:** the side of the position that closed (long position closed -> window blocks LONG signals only; short -> SHORT only). An opposite-side signal is NOT blocked.
- **Window:** starts at the **exit FILL time** (the fill callback of the last exiting contract, i.e. the trade's exit timestamp `exit_ns`, not the decision / request time) and lasts **30 minutes of absolute time (1,800 s, UTC epoch clock; no session or ET dependence, runs across the 17:00 ET roll and the session boundaries)**. Several windows can overlap (one per qualifying exit); a signal is blocked if ANY open window has the same side. A blocked signal never creates a trade, so it never opens a window itself (no cascade).
- **What is blocked:** the P7 ENTRY SIGNAL only, evaluated at the **signal second** (the instant TryEntry would receive it: bar close for the PB3B bar logic), before the 45-s confirmation / OTE hold / L2 arm / sizing. The signal is **dropped** (not queued, not re-armed after the window). Nothing already working is touched: an open position, its resting stop / target, an armed reserve add of a still-open trade are unaffected (a window can only open when the position is flat, so there is no add to cancel). A signal that was already accepted and is waiting in the 45-s confirm before the stop cannot exist (P7 was in a trade).
- **Evaluation order inside TryEntry:** the normal skips first (book disabled, in trade, ExitPending, entry pending, DayHalt / WeekHalt, time block, session lots 0); then the blackout check. So the blackout never changes day-halt / lock accounting and a halted book logs its usual reason; a signal blocked by the blackout does not consume a daily trade count or a lock state. ExitPending: the window opens only at the FILL, so a signal arriving while the exit is still pending is skipped by ExitPending as today (not by the blackout).
- **Tie rules:** a signal is blocked iff `exit_fill_time < signal_time < exit_fill_time + 1,800 s` for a same-side window (strict at the far end: a signal at exactly +1,800.000 s is allowed; a signal in the same second as the fill, processed after the fill, is blocked). Ordering inside one second follows the engine event order (fill callbacks before the bar-close signal handler); in live code set the window inside the exit-fill handler (OnExecutionUpdate) so any later TryEntry sees it.
- **Panel / code:** there is **no D7 v1.4 panel field** for the post-STOP trigger (ThL2BlackoutMins / ThL2BlackoutBooks / ThL2BlackoutSameSideOnly act on the loss CUT only). Proposed v1.6 fields: `PostExitBlackoutMode` (Off|Shadow|Live), `PostExitBlackoutBooks` = "P7", `PostExitBlackoutMins` = 30, `PostExitBlackoutSameSide` = true, `PostExitBlackoutOn` = "Stop,StateCut". Implementation: in the exit-fill handler, when the book is flat and the exit reason is in the list, `b.BlackoutUntil = max(b.BlackoutUntil, fillTime + N min)` per SIDE (two fields BlackoutUntilLong / BlackoutUntilShort, because overlapping windows of opposite sides must not overwrite each other); TryEntry skips when `now < BlackoutUntil[side]`. Policy line: "P7: after a Stop or StateCut exit, no same-side P7 signal for 30 minutes."
- **Quantities the live strategy cannot compute from chart data:** none. Needs only the book's own exit fill time, exit reason and position side, all known in OnExecutionUpdate. (The only dependency is that the v1.5 state cut is reported as an exit with a distinguishable name; if the cut fires through a different path name, add it to the trigger list.)

## 2. Verification that the written rule reproduces the exact trade set
- Exact run R5_BO_3 (S1b-COMB base, 39 months present): 2,347 P7 trigger exits = StateCut 1,945 + StopJoin 239 + StopJoinFallback 144 + Stop 19 (other P7 exits: Target 2,283, BookLock 52, TimeBlock 38, StackCut 15, RollFlat 10, none of them triggers).
- **Rule check on the output list:** applying the written rule to the run's own P7 trades (trigger exits above, same side, signal strictly inside 30 min after the exit fill) finds **0 taken P7 signals inside an open window (0 violations)**. The same check on the live-panel-base run (LPB_BASE_BO3, 545 P7 trigger exits, L6M) also finds **0 violations**.
- **Blocked-signal reconstruction:** of the P7 trades in the unblocked exact base list (S1b-COMB) that are absent from the blackout run, **390 are explained exactly by a window** (a same-side trigger exit of the blackout run 0.6-29.9 min before the base signal, median 15.9 min, triggers StateCut 335 / StopJoin 32 / StopJoinFallback 23); 105 are absent for a different reason (follow-on divergence: a different trade history after the first blocked signal shifts later entries, caps and locks). The exact run re-simulates the follow-ons, so the trade sets are not a pure subset; the rule itself holds with zero violations.

## 3. Five worked rows from the exact run (blocked signal = a base P7 signal that the blackout removed; times ET, absolute 30-min window)
| # | run month | trigger exit (type) | exit fill time ET | blocked signal time ET | minutes after exit | side | planned lots of the blocked signal |
|---|---|---|---|---|---|---|---|
| 1 | 202605 | StateCut | 2026-04-30 18:56:54 | 2026-04-30 19:13:01 | 16.1 | long | 4 |
| 2 | 202605 | StateCut | 2026-05-01 10:33:16 | 2026-05-01 11:00:00 | 26.7 | long | 7 |
| 3 | 202606 | StopJoin | 2026-06-10 06:30:42 | 2026-06-10 06:53:00 | 22.3 | short | 4 |
| 4 | 202606 | StopJoinFallback | 2026-06-07 18:55:46 | 2026-06-07 19:08:00 | 12.2 | long | 4 |
| 5 | 202306 | StopJoinFallback | 2023-06-28 11:25:04 | 2023-06-28 11:38:00 | 12.9 | long | 4 |

## 4. Four-window numbers
**(a) Exact S1b-COMB base (engine as the other R5 rows; ROLL-EXCL, all-weeks maxDD, carrying week dropped from means only), stack, R5_BO_3 vs the exact base:**

| window | live maxDD | with blackout maxDD | cut % | live worst-20 | with worst-20 | d mean $/wk |
|---|---|---|---|---|---|---|
| L6M | 79907 | 73475 | +8.0 | 165224 | 284546 | +3026 |
| HOLD | 99496 | 108430 | -9.0 | -575167 | -458087 | +2443 |
| PRE | 140288 | 127881 | +8.8 | -699709 | -680882 | +10 |
| X' | 128944 | 134598 | -4.4 | -347890 | -345832 | -11 |

**(b) LIVE PANEL base (P7 day cap 8,400 loss cap + 7/4/4 table (asia 7, london 4, nyam 4) + P7 state cut 40 / 5x / win 5 / pers 3 no newMae, all ON; sets LPB_BASE and LPB_BASE_BO3, built by REDO-R5 because no SZ-IJK live-panel set existed on the box; interpretation of "P7 day cap 8,400" = maximum daily LOSS 8,400 for P7 with the +42,000 profit cap kept; if SZ-IJK's base differs, rerun with its sets), blackout vs the same base:**

| window | live maxDD | with blackout maxDD | cut % | live worst-20 | with worst-20 | d mean $/wk |
|---|---|---|---|---|---|---|
| L6M | 77224 | 75509 | +2.2 | 102384 | 147680 | +1674 |
| HOLD | not complete | | | | | |
| PRE | not complete | | | | | |
| X' | not complete | | | | | |

Months complete for the live-panel rows: L6M (6 months) done, HOLD queued ahead of other tiers; PRE and X' were not requested of the queue (capacity); the table shows 'not complete' where a window is missing.

## 5. Notes
- The gain is mostly the post-STOP and post-cut re-entry avoidance on P7 in L6M; on the S1b-COMB base the HOLD window (Nov 2025 - Apr 2026) is deeper than live (-9%) and X' is -4%: it does not hold across windows. On the live-panel base L6M the cut is smaller (+2%) at +$1.7k/wk.
- Everything above is Shadow evidence; nothing goes live from this page. Files: code/th_r5/r5_hooks.py (rule), r5_spec_verify.py (rule check), /mnt/l2/l2vast/_th_r5/bo3_blocked.csv (all blocked signals), exact runs under _th_state/s345/exact_b/runs/R5_BO_3 and LPB_BASE*.


## E. JN04 four-window numbers

### E1. Old base (S1b-COMB: P7 table 7,7,0,7,0,0, no day cap, S1-COMB cut) - exact, ROLL-FIXED, reference = S1b-COMB live

| exact set | what | L6M cut / d mean | HOLD (12 mo) cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 vs the S1b-COMB live | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JP07 | JP07 = JN04 + CF_EN_45 | +50.1 / +4166 | +56.1 / +465 | +46.9 / -3068 | +65.2 / +2195 | -5.7 / -7967 |

Rule 2a label (old base): RECENT-ONLY (old fixed floor: RECENT-ONLY); PRE d mean -3620 vs the floor in section 6 of DS3_JOINT.md; bi-weekly WF over the contiguous block 2023-04..2026-10: 76% of periods beaten.

### E2. LIVE PANEL BASE (P7 day cap 8,400 R1_3 + installed 7/4/4 table + P7 cut 40/5x/w5/p3, all ON) - JN04 = this base + the four layers; reference = this base without the layers (SZ-CORE LPB_BASE)

Running (LPB_JN04 via the r5_hooks panel hooks, 43 months, 4 workers; regression LPB_EMPTY vs SZ-CORE LPB_BASE on 202606). Numbers appear here when the windows are complete.

## F. Cross-checks and open items

- The four layer rules above were rebuilt from the FGH / CDE / IJK cell definitions and reproduce the table multipliers used in the exact run: the "layer multiplier" column of the worked rows is the exact-run table ratio, and the feature columns (Calmar, dA vs threshold, atr_rel, same-side lots) are recomputed from the rule text.
- Table-mode caveat (section B point 4) and the pending rule-mode STACK run JR01.
- LOT / SIGQ / REG / STACK all need new v1.6 code; none exists in DS7 v1.4. Only the entry change CF_EN_45 (`ConfirmPatternA`=Engulf) of JP07 is a pure panel value.
- The live-panel-base table multipliers (LOT state, STACK state, SIGQ history) were computed from the S1b-COMB base; on the live panel base the P7 lots and state differ (744 table), so the LPB_JN04 run applies the same per-signal multiplier table keyed by signal second, an approximation that a rule-mode run would replace.

## G. Day-cap definitions used by each stack (cross-checked against the hook code and DS7.cs CheckLimits lines 3463-3469)

| stack / base | P7 day LOSS cap | P7 day PROFIT cap | SizeMult scaling max(1, SizeMult) | source |
|---|---|---|---|---|
| S1b-COMB (old base, JN04 exact rows in E1) | 16,800 (the DS7 default P7MaxDailyLoss; the engine's sim.DAYCAP default) | 42,000 | none under Q1-A | engine default |
| LPB_BASE / LPB_JN04 (live panel base) | **fixed $8,400** (panel P7MaxDailyLoss, sim.DAYCAP[P7] = (42,000, 8,400)) | 42,000 (kept) | max(1, SizeMult) = 1 under Q1-A (the ER sizer never goes above 1.0, so the scaling factor is 1), and the JN04 multiplier table never changes size_mult | code/th_r5/r5_hooks.py panel hook |
| JP01 / JP06 (compose cells on the OLD base) | **fixed $8,400** = 1R where R is computed on BASE lots (rbasis base: base_qty 7 x stop 60 x $20 x max(1, SizeMult) = 8,400) | **$33,600** (4R, not the installed 42,000) | same: 1 | CDE_R1_3 lock via cde_exact.check_book_lock |

Correction: an earlier note of mine said R1_3 was R on SIZED lots (1R = $4,800 at 4 lots); the hook code uses BASE lots, so JP01/JP06 are the fixed-dollar $8,400 loss cap like the installed panel; the difference between them and the installed panel is the win cap (33,600 vs 42,000) and that they sit on the old base (S1b-COMB: default 16,800 loss cap, 7,7,0,7 table, S1-COMB P7 cut). The LPB row is the canonical live-panel base for every section of this spec.

