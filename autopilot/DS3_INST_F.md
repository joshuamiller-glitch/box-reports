# DS3_INST_F - flow calendar (T-INSTITUTIONAL section F, INST-3, 2026-10-31 16:38Z)

**DATA line.** On disk and used: CPI / NFP / FOMC statement dates (`l2vast/standS/event_calendar_core.csv`), Treasury auction closes (`data/gap/ds50/treasury_auctions.csv`, 588), NQ per-contract minutes with volume (`rootmoves/data_databento/NQ/contract_minutes_NQ.parquet`, 12 rolls 2023-06..2025-12 in the sample), NQ/ES 1-min bars, the 6 live books' held-signal trades. Derived by rule (no download): month-end / first-of-month / quarter-end, third-Friday opex and quad witching (= S&P / NDX quarterly rebalance), Russell reconstitution (3 days), coupon-settlement day (15th), NQ roll day (first day the next contract carries more RTH volume), Fed blackout (second Saturday before the first meeting day through the statement day). NOT on disk: the Fed-speaker calendar (speaker days cannot be separated from blackout days; named gap), MSCI dates. Nothing to buy for F.

## Page 1 - the answer

**Plain sentence.** Of 110 pre-registered flow-calendar cells (11 day classes x 5 time windows x skip / size-up x1.5), 15 were positive in both PRE and X' on measured and no-correction fills with enough signals on both sides, 21 were selected on PRE+X' alone and looked at once on the recent windows: 5 are positive in L3M and L6M (per contract and on the stack), 2 STRICT, **1 TOLERANT (literal gate, headline)**; post-hoc: 1 under TOL-B (PRE gain > -1.0 x L6M gain), 1 with clause 5 dropped. The TOLERANT cell is `fl.ROLLPRE.RTH.up` (size up x1.5 every live-book signal fired 09:30-16:00 in the four trading days before the NQ volume-crossover roll day, i.e. the roll-Thursday week; 2.5% of signals): those signals pay +5.34 pts per contract more than all others (L6M, MDE 13.2), PRE +1.71 (MDE 13.8), X' +5.81, HOLD +5.86; on the one-convention stack the x1.5 is +1.6k/wk L6M (MDE +3.3), +1.1 PRE, +0.0 X': inside MDE everywhere, on 8 class days in L6M (two rolls, two weeks), cell placebo p 0.16, program placebo p 0.83. Month-end, first-of-month, quarter-end, opex, quad witching, coupon-settlement day, roll day and Fed blackout: no class of signals is reliably better or worse than the rest in the recent windows (selected set mean L6M lift -2.37 pts per contract vs a shuffled-calendar null +0.10, 5-95% -5.65 to +4.97). As close-window books (15:00 bar open to 15:59 close, 1 contract, $4.84, sign fixed on PRE+X') 6 of 22 class x instrument books are TOLERANT-positive and none is beyond its MDE (n = 3-183 trades, L6M MDE $254-2093); the three best L6M books are close|OPEXMON|NQ (short, n 23, L6M +935 vs MDE 1601); close|OPEXMON|ES (short, n 23, L6M +542 vs MDE 672); close|ROLLDAY|NQ (short, n 11, L6M +233 vs MDE 2094), all inside MDE (LEADS at n < 30 or inside MDE). **Verdict: DEAD for the flow calendar as a take / skip state; one LEAD (roll-week size-up), nothing promoted.** Persistence score 0.52 (regime / day-type base rate), shrunk size 0.00: shadow only.

### The three T-SIXTY columns

| column | state cells of 21 selected | close-window books of 22 | persistence |
|---|---|---|---|
| STRICT | 2 | 6 | regime / day-type base rate 52% (DS3_PERSISTENCE); no walk-forward possible at these n |
| TOLERANT literal (headline; clause 5 => PRE gain > 0) | 1 | 6 (close books use PRE > -L6M, i.e. TOL-B) | same |
| TOL-B (post-hoc) | 1 | 6 | same |
| TOL-nc (post-hoc, no clause 5) | 1 | - | same |
| NOW-ONLY | 5 | 7 | same |

STRICT cells: `fl.ROLLPRE.AM.up`, `fl.ROLLPRE.RTH.up`. NOW-ONLY: `fl.FM.AM.skip`, `fl.FM.PM.skip`, `fl.ROLLPRE.AM.up`, `fl.ROLLPRE.RTH.up`, `fl.SETTLE15.DAY.up`. The STRICT size-up `fl.ROLLPRE.AM.up` fails TOLERANT only on the PRE worst-20-weeks clause (x1.5 lots deepen the worst PRE weeks by $3.1k), the RTH version passes it.

**Status line.** The two LEADs of INST-3 (`xm.led_YM_60.ge+0.0` skip in C, `fl.ROLLPRE.RTH.up` in F) are shadow-only and not independent evidence (cell placebo p 0.32 / 0.16; program placebo 0.41 / 0.83).

## 1. Method (prereg `l2vast/ds3/prereg/INST_F_prereg.md` sha256 `272967287013295a1fd7cb041f06d6d71ec59368b7478d2c2e7a9cb37e3f8915` + AMEND1; selection sha256 `00da3e10bedbc6bcdad0369f78a1b6c9afb9fb67f8f9b08726822b4978c9b4e4`, logged before the look)

Same outcome frame as section C (6 live books, 25,941 signals, per contract M headline / N / LC, lift stratified by book). Class days (trading days 2023-04-03..2026-02-06): BLACKOUT 183, FM 35, ME 35, ME2 70, OPEXMON 23, QE2 22, QUAD 11, ROLLDAY 11, ROLLPRE 44, RUSSELL 3, SETTLE15 34. Windows: DAY (label day), RTH 09:30-16:00, AM 09:30-12:00, PM 12:00-15:00, CLOSE 15:00-16:00 ET. skip: keep = not(class and window); up: keep = class and window (stack: engine multiplier x1.5, integer half-up, governors see the unrounded multiplier). Selection PRE+X' only (n_small = min(kept, skipped) >= 100 / 40, top 15 pooled + 2 per live book; AMEND1: the per-book branch also needs the pooled floors). **AMEND2 (reporting only, selection untouched): MDE = 2.8 x max(week-cluster SE, day-cluster SE, trade-level SE)**, because the week-clustered SE of a class that touches 2 weeks of a window (the roll-week AM cell had 81 signals in 2 weeks of L6M) came out at 1.4 pts against a trade-level 6.1 and understated the MDE 4x; the stack MDE is the paired weekly delta MDE of the engine (unchanged). Whole-day flags (monthend, monthend3, monthstart, opexday, quadday, opexweek, quadweek, holidays, events) and the 10:00 / 15:00 clock-window skips were scored by EINT2 (DEAD_CELLS), Treasury auction windows and earnings nights by NTE / NT-3 (`cal.auct.*`, `cal.earn.*`): not re-scored; this section adds the window splits, quarter-end, first-of-month, non-quarter opex, coupon settlement, roll day / roll-Thursday week, the Fed blackout, and the close-window books.

## 2. Class by class, PRE and X' (all 110 cells; the recent columns of the unselected are sealed)

Lift of the CLASS signals minus all other signals, pts per contract M (positive = class signals better), PRE / X' with PRE MDE. DAY window.

| class | days | PRE | X' | PRE MDE | n class signals PRE |
|---|---|---|---|---|---|
| ME | 35 | -2.41 | -11.33 | 12.6 | 687 |
| ME2 | 70 | -0.23 | -6.03 | 9.6 | 1390 |
| FM | 35 | -1.91 | -2.37 | 9.9 | 781 |
| QE2 | 22 | -3.88 | -7.04 | 12.8 | 425 |
| QUAD | 11 | +5.12 | +2.96 | 22.5 | 248 |
| OPEXMON | 23 | +7.98 | +3.33 | 21.8 | 411 |
| SETTLE15 | 34 | +12.26 | -4.76 | 12.0 | 578 |
| ROLLDAY | 11 | -5.32 | +14.21 | 16.0 | 196 |
| ROLLPRE | 44 | +2.73 | +2.73 | 10.0 | 948 |
| BLACKOUT | 183 | +1.36 | +2.15 | 5.6 | 3516 |
| RUSSELL | 3 | +0.50 | +0.86 | 16.0 | 63 |

Classes with |lift| beyond the window's MDE in PRE or X': SETTLE15. Classes whose PRE and X' lifts have the same sign: ME, ME2, FM, QE2, QUAD, OPEXMON, ROLLPRE, BLACKOUT, RUSSELL; opposite sign: SETTLE15, ROLLDAY.

## 3. Selected cells (all 21; the stack column is C1 no combined lock, $k/wk delta vs the composite with MDE)

| cell | keep L6M | X' | PRE | HOLD | L6M [MDE] | L3M | N L6M | LC L6M | stack L3M | L6M [MDE] | HOLD | PRE | X' | 12R L6M | 20R L6M | PRE worst-20 d | plc p | S/T/N | failed gates | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fl.BLACKOUT.DAY.up | 19.4% | +2.15 | +1.36 | -3.26 | -3.88 [10.3] | -8.80 | -4.05 | -3.90 | -0.5 | +2.6 [+7.4] | +2.8 | +4.2 | +0.3 | +3.4 | +4.5 | -105.2 | 0.94 | n/n/n | L3M_pc,L6M_pc,L3M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.SETTLE15.DAY.up | 4.8% | -4.76 | +12.26 | +3.53 | +7.42 [14.0] | +13.49 | +7.70 | +7.69 | +4.3 | +2.4 [+3.7] | +2.0 | +2.4 | -0.5 | +2.2 | +2.2 | -50.0 | 0.21 | n/n/Y | PRE_worst20 | DEAD |
| fl.FM.AM.skip | 98.2% | +1.63 | -0.42 | +6.69 | +4.68 [16.5] | +0.53 | +4.75 | +4.72 | +0.3 | +1.6 [+3.3] | +1.8 | -1.8 | +0.2 | +5.9 | +1.1 | -77.6 | 0.36 | n/n/Y | PRE_stack_tol,PRE_worst20,drop<100% | DEAD |
| fl.ROLLPRE.RTH.up | 2.5% | +5.81 | +1.71 | +5.86 | +5.34 [13.2] | +3.57 | +5.45 | +5.31 | +2.2 | +1.6 [+3.3] | +1.4 | +1.1 | +0.0 | +0.5 | +1.9 | +3.6 | 0.16 | Y/Y/Y | - | LEAD |
| fl.ROLLPRE.AM.up | 1.4% | +8.78 | +1.89 | +10.34 | +9.85 [17.0] | +10.09 | +10.08 | +9.94 | +2.3 | +1.6 [+3.4] | +1.4 | +1.0 | +0.0 | +0.4 | +0.6 | -3.1 | 0.11 | Y/n/Y | PRE_worst20 | DEAD |
| fl.ME2.AM.up | 3.3% | +0.05 | +0.45 | -7.15 | -8.65 [18.4] | -2.41 | -8.88 | -8.77 | +1.0 | +0.9 [+2.4] | +1.0 | +0.4 | +0.9 | +0.9 | +0.9 | -57.4 | 0.82 | n/n/n | L3M_pc,L6M_pc,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.ROLLPRE.DAY.up | 5.0% | +2.73 | +2.73 | -0.22 | -0.76 [15.4] | -1.80 | -0.79 | -0.79 | -0.1 | +0.7 [+2.2] | +0.6 | +1.3 | -0.1 | +0.5 | +1.8 | -68.1 | 0.46 | n/n/n | L3M_pc,L6M_pc,L3M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.FM.PM.skip | 99.0% | +4.74 | -0.81 | +15.98 | +12.63 [32.4] | +41.83 | +13.26 | +12.63 | +0.3 | +0.0 [+0.4] | -0.0 | -0.1 | +0.0 | -0.0 | -0.0 | -1.9 | 0.20 | n/n/Y | PRE_worst20,drop<100% | DEAD |
| fl.ROLLPRE.PM.skip | 98.9% | +1.16 | -1.44 | +0.32 | +0.89 [32.6] | +4.72 | +0.94 | +1.06 | +0.1 | -0.0 [+0.2] | -0.0 | +0.0 | +0.0 | -0.0 | -0.0 | -10.1 | 0.58 | n/n/n | L6M_stack,PRE_worst20 | DEAD |
| fl.ME.RTH.skip | 97.4% | +19.14 | -2.46 | -0.54 | +2.44 [23.0] | -7.27 | +2.51 | +2.59 | +1.0 | -0.0 [+2.5] | -0.3 | -0.7 | +0.6 | +0.2 | +0.2 | -21.4 | 0.48 | n/n/n | L3M_pc,L6M_stack,N_L3M,PRE_worst20,drop<100% | DEAD |
| fl.ME.PM.skip | 99.1% | +25.80 | +1.53 | -8.65 | -6.20 [27.3] | -25.31 | -6.38 | -6.17 | +0.0 | -0.0 [+0.1] | +0.0 | -0.1 | +0.2 | -0.0 | -0.0 | -0.7 | 0.81 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20,drop<100% | DEAD |
| fl.OPEXMON.AM.up | 1.1% | +8.72 | +8.98 | -1.28 | -0.34 [22.0] | -6.12 | -0.33 | -0.09 | -0.5 | -0.2 [+1.0] | -0.2 | +0.3 | -0.1 | -0.3 | -0.3 | -22.1 | 0.45 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.OPEXMON.RTH.up | 1.8% | +7.20 | +4.03 | -7.27 | -7.12 [15.5] | -11.22 | -7.58 | -6.88 | -0.5 | -0.2 [+1.0] | -0.2 | +0.3 | -0.0 | -0.3 | -0.3 | -23.8 | 0.74 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.OPEXMON.DAY.up | 4.4% | +3.33 | +7.98 | -7.30 | -7.97 [19.5] | -14.21 | -8.30 | -7.75 | -2.2 | -0.2 [+3.3] | -0.3 | +0.9 | +0.1 | -0.4 | -0.4 | -26.8 | 0.82 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.QUAD.DAY.up | 1.1% | +2.96 | +5.12 | -7.25 | -7.75 [20.0] | +0.32 | -8.23 | -7.49 | -0.2 | -0.4 [+0.9] | -0.3 | +1.1 | +0.5 | -0.4 | -0.4 | -5.2 | 0.71 | n/n/n | L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.BLACKOUT.PM.up | 3.6% | +3.01 | +0.37 | -4.91 | -6.85 [18.2] | -17.46 | -7.33 | -6.86 | -1.3 | -0.4 [+1.3] | +0.0 | +0.6 | +0.3 | +0.0 | +1.3 | -0.5 | 0.83 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20 | DEAD |
| fl.QE2.DAY.skip | 98.0% | +7.04 | +3.88 | +6.62 | +7.14 [33.4] | -3.40 | +7.35 | +7.28 | -0.8 | -1.3 [+2.7] | -1.1 | +1.4 | -0.8 | -1.3 | -1.3 | +55.8 | 0.18 | n/n/n | L3M_pc,L3M_stack,L6M_stack,N_L3M | DEAD |
| fl.ROLLPRE.RTH.skip | 97.5% | -5.81 | -1.71 | -5.86 | -5.34 [13.2] | -3.57 | -5.45 | -5.31 | -3.1 | -2.3 [+4.7] | -2.0 | -1.2 | -0.5 | -0.8 | -0.7 | -24.5 | 0.85 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20,drop<100% | DEAD |
| fl.ME2.DAY.skip | 88.0% | +6.03 | +0.23 | -1.17 | +0.96 [10.2] | -0.59 | +0.91 | +1.01 | -5.5 | -5.2 [+8.1] | -5.8 | -1.9 | -1.6 | -5.5 | -4.2 | +36.4 | 0.48 | n/n/n | L3M_pc,L3M_stack,L6M_stack,N_L3M,drop<100% | DEAD |
| fl.FM.DAY.skip | 93.0% | +2.37 | +1.91 | -4.05 | -6.31 [14.1] | -4.09 | -6.60 | -6.39 | -4.8 | -5.6 [+9.1] | -4.7 | -1.0 | -0.4 | +1.4 | -3.2 | -37.9 | 0.77 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,PRE_worst20,drop<100% | DEAD |
| fl.ME.DAY.skip | 94.0% | +11.33 | +2.41 | -6.00 | -2.92 [14.2] | -6.21 | -3.10 | -2.76 | -7.7 | -6.2 [+7.5] | -6.9 | +0.0 | +1.2 | -5.3 | -4.7 | +41.3 | 0.74 | n/n/n | L3M_pc,L6M_pc,L3M_stack,L6M_stack,N_L6M,N_L3M,drop<100% | DEAD |

Skip cells are almost all negative on the stack (skipping a class of signals loses their volume); the up cells with positive stack lines are the roll-week pair. Mean stack L6M delta across the 21 selected cells: -0.5 k/wk.

## 4. The TOLERANT cell by session

`fl.ROLLPRE.RTH.up`, pts per contract M (MDE), n in L6M:

| session | PRE | X' | HOLD | L6M [MDE] | n L6M |
|---|---|---|---|---|---|
| nyam | +0.10 | +7.18 | +11.22 | +11.31 [17.4] | 81 |
| nypm | +3.40 | +1.05 | +1.35 | +1.03 [33.4] | 60 |

All signals are inside the class window by construction. L6M lift by book (kept minus rest, per contract M): K6 +16.2 (n 30); P6 +4.5 (n 34); U6 -11.3 (n 8); H6 -17.4 (n 22); M6 +10.6 (n 23); A6 +14.3 (n 24). The L6M kept set is 141 signals from 8 days; per-day mean per signal: 20250910 +27.3 (n 15), 20250912 +17.2 (n 8), 20251211 +16.6 (n 24), 20251212 +9.7 (n 28), 20250909 +6.9 (n 12), 20250911 -0.6 (n 9), 20251210 -8.2 (n 33), 20251209 -15.0 (n 12).

## 5. The NQ roll, derived (descriptive; 11 rolls 2023-06..2025-12; day 0 = the volume-crossover day, always the Monday of expiry week)

| offset (trading days) | new contract share of RTH volume | new-minus-old close (index pts) | day change of the spread | total RTH volume |
|---|---|---|---|---|
| -6 | 0.5% | 226.7 | - | 473,381 |
| -5 | 0.8% | 225.2 | -1.5 | 448,605 |
| -4 | 1.1% | 226.5 | +1.3 | 447,686 |
| -3 | 1.5% | 226.6 | +0.1 | 515,182 |
| -2 | 4.3% | 230.2 | +3.6 | 461,251 |
| -1 | 20.8% | 231.7 | +1.5 | 516,960 |
| +0 | 63.2% | 233.8 | +2.0 | 487,660 |
| +1 | 80.7% | 231.7 | -2.0 | 503,321 |
| +2 | 87.4% | 228.5 | -3.2 | 576,234 |
| +3 | 93.9% | 222.8 | -5.8 | 526,144 |
| +4 | 100.0% | - | - | 442,768 |
| +5 | 100.0% | - | - | 366,454 |

Volume stays in the front contract until the Monday of expiry week (1% / 4% in the new contract on days -4 / -2, 21% on day -1, 63% on the crossover day, 94% on day +3); the new-minus-old spread widens 8.5 index points from day -5 to day 0 and then falls 11.0 points by day +3 (carry roll-down). The ROLLPRE window (days -4..-1) is the quiet week before the crossover: the live books' signals there are in thin-roll liquidity; they pay more in every window, but on only 2-6 roll events per window (L6M: 2) the lift cannot be separated from the days' own range (no regime variable explains it; cell placebo p 0.11 AM / 0.16 RTH).

## 6. Close-window books by class (15:00 open -> 15:59 close, 1 contract, $4.84 RT, 1 tick adverse each side, sign = PRE+X' mean drift)

| book | days | sign | gross pts (all) | PRE | X' | HOLD | L6M [MDE] | purged CV $ | placebo p (HOLD) | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|
| close|OPEXMON|NQ | 23 | short | -12.7 | +79 | +195 | +653 | +935 [1601] | +239 | 0.14 | Y/Y/Y |
| close|OPEXMON|ES | 23 | short | -3.6 | +74 | +97 | +390 | +542 [672] | +150 | 0.10 | Y/Y/Y |
| close|ROLLDAY|NQ | 11 | short | -2.6 | +205 | -427 | +233 | +233 [2094] | -100 | 0.30 | n/n/Y |
| close|ROLLPRE|NQ | 44 | short | -6.9 | +95 | +172 | +141 | +141 [495] | +124 | 0.40 | Y/Y/Y |
| close|ALL|NQ | 737 | short | -2.8 | +11 | +66 | +79 | +76 [308] | +42 | 1.00 | Y/Y/Y |
| close|ME|NQ | 35 | long | +12.6 | +717 | -315 | -90 | +72 [1077] | -268 | 0.67 | n/n/n |
| close|ROLLPRE|ES | 44 | short | -1.4 | +22 | +55 | +70 | +70 [293] | +40 | 0.40 | Y/Y/Y |
| close|ME|ES | 35 | long | +3.3 | +427 | -167 | -110 | +38 [732] | +134 | 0.75 | n/n/n |
| close|BLACKOUT|ES | 183 | short | -2.6 | +166 | +65 | +12 | +31 [254] | +102 | 0.34 | Y/Y/Y |
| close|ALL|ES | 737 | short | -0.5 | -29 | +8 | +24 | +22 [164] | -7 | 1.00 | n/n/Y |
| close|BLACKOUT|NQ | 183 | short | -10.4 | +307 | +135 | +17 | +13 [488] | +192 | 0.43 | Y/Y/Y |
| close|ME2|ES | 70 | long | +1.5 | +184 | -138 | -31 | -14 [555] | -122 | 0.52 | n/n/n |
| close|ME2|NQ | 70 | long | +2.0 | +218 | -266 | -17 | -34 [1008] | -214 | 0.50 | n/n/n |
| close|ROLLDAY|ES | 11 | long | +1.6 | -32 | +266 | -36 | -36 [928] | +49 | 0.53 | n/n/n |
| close|SETTLE15|ES | 34 | short | -1.2 | +55 | +25 | -19 | -122 [788] | +31 | 0.47 | n/n/n |
| close|QE2|ES | 22 | long | +3.0 | +320 | -119 | -130 | -130 [953] | +118 | 0.68 | n/n/n |
| close|SETTLE15|NQ | 34 | short | -3.0 | +99 | -10 | -1 | -139 [1484] | +46 | 0.49 | n/n/n |
| close|QUAD|ES | 11 | short | +0.2 | -88 | +133 | -149 | -149 [260] | -153 | 0.67 | n/n/n |
| close|FM|ES | 35 | short | +0.4 | +123 | -271 | -131 | -173 [443] | -177 | 0.74 | n/n/n |
| close|FM|NQ | 35 | short | +2.3 | +280 | -489 | -250 | -311 [695] | -345 | 0.77 | n/n/n |
| close|QE2|NQ | 22 | long | +2.2 | +264 | -212 | -311 | -311 [1427] | -288 | 0.74 | n/n/n |
| close|QUAD|NQ | 11 | short | +1.6 | +18 | +112 | -482 | -482 [480] | -346 | 0.85 | n/n/n |
| close|RUSSELL|NQ | 3 | long | +21.9 | +595 | +80 | +nan | +nan [nan] | +nan | nan | n/n/n |
| close|RUSSELL|ES | 3 | long | +10.0 | +639 | +133 | +nan | +nan [nan] | +nan | nan | n/n/n |

$ per trade net of fee and slippage; PRE and X' are in-sample for the sign. Classes with n < 30 (QUAD, ROLLDAY, RUSSELL, QE2, OPEXMON) are LEAD at best by rule; the well-powered ones are BLACKOUT (n 183) and the ALL-days control (n 737): the Fed-blackout NQ book (short) has X' +135 / PRE +307 / HOLD +17 / L6M +13 per contract (MDE 488), the all-days control (short) X' +66 / PRE +11 / HOLD +79 / L6M +76: the blackout excess over all days is not distinguishable from the unconditional close-window drift of this sample, and the six TOLERANT-positive class books (OPEXMON, ROLLPRE, BLACKOUT on NQ and ES) are all SHORT, i.e. the same direction as the all-days control: they re-describe a weak negative 15:00-15:59 drift (all-days short NQ +$76 L6M, MDE $308) rather than a flow-class effect.

## 7. Placebos and notes

* Shuffled same-weekday calendar days, 200 draws: cell p range 0.11-0.94; the program-level null (whole selection re-run on shuffled calendars) selects 15 eligible cells on average (real 15) with a mean L6M lift of its top 15 of +0.10 (real -2.37); p = 0.83.
* Decision delay: calendar states are known the day before: n/a. Capacity: the x1.5 adds 0.5 lot to each live signal in the window (K6 2 -> 3 lots etc.); depth at the fire seconds was not re-measured here (the l2 depth store is INST-2's).
* TOLERANT clause 3 reading: as section C (PRE gain > -1.0 x L6M gain; flag tolA = literal): STRICT cells fl.ROLLPRE.AM.up tolA=False; fl.ROLLPRE.RTH.up tolA=True.
* Questions: none new beyond section C's clause-3 question; PPI / GDP / retail-sales and Fed-speaker calendars remain named data gaps (a CSV from the user would unlock them).

## 8. Files
Code `l2vast/ds3/code/inst/F/` (f_cal, f_cells, f_prereg, f_prog, f_score, f_look, f_stack, f_rows, f_close, f_roll, f_report); outputs `l2vast/ds3/out/inst/F/`; rows `l2vast/ds3/out/recent_wins/inst_F.csv`; dead cells appended to `out/uf/DEAD_CELLS.csv` (program INST3F).
