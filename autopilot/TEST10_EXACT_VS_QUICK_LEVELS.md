# TEST 10: exact vs quick on the two-sided level books: which side is right (W-TEST10)

Written 2026-11-27 01:13 UTC. Order: autopilot/DIRECTIVE_TEST10_0015Z.md (relay design under Josh's standing 18:22Z order, not Josh's words). **Research / diagnostic only: nothing live, no engine or gate change, nothing bought, nothing deleted.** QUICK = gcore2x tape walk (trade-level re-simulation of every held cell, reproduces the stored grid weekly points to the cent on 614 of the 615 blocks, the exception is named in section A2); EXACT = engine TRADES of the bare R0 sets, 1 lot per held cell, fees in. All $ are per lot, held weeks only, equal weight over the cells held that week (the Test 8 basket definition). Code: code/th_test10/. Trade-level diffs of the 10 worst books: autopilot/TEST10_TRADE_DIFFS.md.

## ANSWER FIRST

1. **Neither engine is wrong about the trades: the "exact is far weaker" result was a scoring bug in the Test 8 exact table, not a difference between the engines.** code/th_test8/exact8.py (the stage-B scorer it was copied from, th_rota/stageb_score.py mon()) reads only the TWO END MONTHS of each 13-week hold; a hold of 12 to 17 weeks spans 4 to 5 calendar months, so every held week in a middle month showed ZERO exact trades while the quick side kept its trades. Scored over ALL months of every hold (month 202511 is not in the fleet, its trades dropped on both sides), the same 615 Test 8 held blocks (615 of 630 with exact rows landed; the other 15 have months still in the queue) give, per lot per week: **quick 286, exact 400 (exact / quick 1.40)** (Asia 329 vs 353, London -171 vs -208, NY AM 437 vs 570, NY PM 195 vs 311). Test 8 section F said Asia 123 vs 378, London -162 vs -13, NY AM -66 vs +507, NY PM 90 vs 376: those exact figures are wrong. Test 5 and Test 6 exact are not affected (score5.py already expands the hold to all its months; check on the Test 5 primary blocks, exact side only: end months only would give Asia -0 and NY AM -97, all months give Asia 187 and NY AM 276, the page says 191 and 339).

2. **Trade by trade the two engines agree.** Same signals (the exact events come from the same stored bars and the same current level code; quick re-simulation reproduces the stored grid weekly points to the cent on 614 of 615 blocks (the one exception, NY PM time_m_60 + sdx3, weeks 104-117, differs by $19,312 = the only level-version case, cause 6 = -2 $/lot/wk pooled); cause 7, bar builder, is zero between the two because both read the same stored bars). Trades: quick 104167, exact 104559 (0.4% apart); 99732 matched on signal second and side (95.7% of quick); the rest are one-position blocking (an exit a few seconds earlier or later in one engine lets the next signal in or blocks it: quick-only 4406, exact-only 4827, net -10 $/lot/wk) and not one exact trade without a quick signal (cause 1 = -1). Exit kind differs on 1.3% of matched trades (whipsaw entries, entry 1.5 s later in the exact engine). **The money difference exact minus quick, +114 $/lot/wk on the basket metric (the terms below are pooled over unit-weeks and sum to +111), splits into: stop and time-exit fills +111, cost +33 (engine fee $1.18 per trade against the project standard $4.84), exit kind -23, blocking -10, different trades -1.** Section A has the table and the 10 worst books.

3. **Which side is closer to a live NT8 strategy: the exact engine, on mechanics; but its stop fills and its fee are the two things to check before trusting its extra dollars.** The engine models what gcore2x does not: entry as a market order through the depth book about 2.6 s after the signal bar closes (quick 1.05 s, first print plus a tabulated slip), the native bracket with the stop-join / stop-pump logic of the live strategy (replica/sim.py pump_stop_exit; 85% of its stop exits fill BETTER than the stop level, median $20 = 4 ticks, mean $34; the tape walk always fills at the stop print minus one tick, $5.9 worse; the link between the two is the engine code plus the fill statistics, not checked trade by trade), target fills by touch priority, one position with exit-pending blocking, session flatten at the scheduled time (both agree to 1.1 s), $1.18 per trade. The stop fill advantage is the largest single term (+111 $/lot/wk) and it runs against the only independent real-book stop-fill study in the project (DS3_DN_STOPFILL: real 1-lot stop-market walk +0.85 pt WORSE than the stop, 10-lot +1.44 pt), so **read quick (286) as the conservative bound and exact (400; 366 at the FEES.md fee $4.84) as the optimistic end until live stop fills of a book that uses the stop pump are compared with the engine**. The verdicts do not depend on which one is used (part B).

4. **B, the verdict on exact numbers: the Test 8 primary is CONFIRMED by the exact engine in every session where quick passed.** Same rule (excess over the quick drift null > 0, beats >= 95% of 200 draws, paired weekly p <= 0.10), valid cells only (475 of 606): exact summed 437 vs null 41, excess **396**, beats 100.0%, p 0.002 = **PASS**; Asia 292 vs 64 (excess 228, p 0.023) **PASS**; NY AM 604 vs 60 (excess 544, p 0.001) **PASS**; NY PM excess 340, beats 99.5%, p 0.104 **FAIL** (the quick screen also failed it); London -101 excess -113 **FAIL**. AGREE (exact within 30% of quick, same sign) holds 250 valid cells, DISAGREE 225 (70% of them with exact ABOVE quick, so the 30% rule is not selecting weak exact books): AGREE summed exact 570 vs null 54 (p 0.000), DISAGREE summed exact 300 vs null 23 (p 0.021). **This is a diagnostic, not a rule.** Recent first, summed exact L6M 471, L3M 451 (quick 382, 526); the excess is again mostly in the second half (first 80 weeks exact 246, last 80 weeks 546).

5. **Stack books (W-SPEC9) versus exact: no contradiction.** The SPEC_STACK pages test the grid against itself (stored weekly table reproduced, rebuilt bars identical, an independent print-by-print scan of the SAME simplified rules: first print through the stop, stop exit one tick adverse, target one tick through, no latency, no depth, no stop pump, $4.84 cost) on 3 dated sessions per book. That is cause 6 and 7 = 0 here too. It never ran the engine. Against the engine the 24 stack books (section A5) trade the same signals (3081 quick vs 3084 exact trades over the 23 books with trades, 97.4% matched on signal second and side, largest count gap per book 5; 13 of 23 books within 20% in $) and differ by the execution terms above.

6. **C, exact drift null:** **counted and queued, results pending (rows land about 17 h to 30 h from now).** 20 draws (not 200), same method as Test 9 T9X on the exact engine: each held cell keeps its events (side, stop, target) and the entry bar is redrawn uniformly among the eligible bars of the same bar row in the same week and session. Test 8 Asia + NY AM held cells: 459 cells, 2,348 set-months per draw, 46,960 rows (3.5 h of fleet at 13.3k rows/h); Test 5 primary Asia held cells: 1,639 cells (126 shared), 7,167 set-months per draw, 143,340 rows (10.8 h); union 179,080 rows = 13.5 h, each part under the 15 h limit. Queued 01:12Z at the END of pending_nyam_gating.txt with queue_rows_safe.py (179,080 appended, 0 lost on re-read). Rows ahead: 227,950 not-DONE rows when counted (01:05Z).

7. **D, level files:** every Test 8 held block rests on a file that is fresh (written after 18 Nov 06:00Z) and either stamp-verified (483 of 630 blocks) or unstamped but fresh (147); none on a stale or stamp-mismatching file. No Test 5, 6 or 8 conclusion changes on verified-only data: dropping the 29 fresh files whose stamp differs from today's code leaves the summed raw basket at 320 (primary 319); keeping ONLY stamp-verified level files gives 349 (L6M 431, L3M 580). Test 6 set (3) vs full: summed +139 vs +135, Asia +148 vs +178, NY AM +166 vs +172 (verdict flips by 0.006), NY PM FAIL both with the print-rule types and stale cells removed. **Module labels (51 modules in the grid: 27 STALE-DROPPED, 14 VERIFIED CURRENT, 10 STALE-REBUILT):** section D.

## A. RECONCILIATION, BOOK BY BOOK (all Test 8 held blocks with exact rows landed)

Method: each held cell (606 cells, 630 held blocks) re-simulated at trade level with the gcore2x rules (code/th_test10/recq.py, same signals, same brackets, same one-position rule; reproduces the stored grid weekly points exactly), exact trades read from the engine TRADES of the cell's bare R0 set over every month of the hold, both restricted to the held weeks; trades matched on (signal second, side). The exact events come from the SAME stored bars, so the **level file version (cause 6) and the bar builder (cause 7) are identical on both sides by construction**; what is left is what the two simulators do with the same signals. Month 202511 is not in the fleet: its trades are removed on both sides. 615 of 630 blocks complete.

### A1. Weekly points, same blocks ($ per lot per week; recent first)

| session | blocks (held cell-periods) with exact landed / of | trades quick / exact | quick $/lot/wk (same periods) | exact $/lot/wk | exact / quick | L6M quick / exact | L3M quick / exact |
|---|---|---|---|---|---|---|---|
| Asia | 137 / 144 | 13228 / 13198 | 329 | 353 | 1.07 | 722 / 692 | 415 / 330 |
| London | 75 / 75 | 6550 / 6563 | -171 | -208 | 1.22 | -324 / -336 | -647 / -671 |
| NYAM | 329 / 336 | 71822 / 72224 | 437 | 570 | 1.30 | 512 / 598 | 686 / 593 |
| NYPM | 74 / 75 | 12567 / 12574 | 195 | 311 | 1.59 | 693 / 858 | 180 / 188 |
| Four sessions summed | 615 / 630 | 104167 / 104559 | 286 | 400 | 1.40 | 344 / 425 | 463 / 386 |

Old Test 8 section F (exact8.py, end months only): Asia 123 vs 378, London -162 vs -13, NY AM -66 vs 507, NY PM 90 vs 376. Corrected here: exact is at or above quick in Asia, NY AM, NY PM and within noise in London (negative in both). The recent half-year is the same picture (L6M, L3M columns).

### A2. The difference split into the seven causes ($ per lot per week, exact minus quick, positive = exact higher)

| session | exact - quick ($/lot/wk) | (1) different trades (signal in one only) | (5) one-position blocking (signal in both, taken in one) | (2) same entry, different exit kind | (3a) fills (same entry and exit kind) | (3b) cost ($4.84 vs $1.18 per trade) | (4) week bin / window edge | (6) level file version (stored grid vs current-code quick) | (7) bar builder (quick vs exact) | residual |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 34 | -3 | -19 | -9 | 41 | 24 | 0 | -0 | 0 (same stored bars) | 0 |
| London | 1 | 0 | 0 | 6 | -27 | 22 | 0 | -0 | 0 (same stored bars) | 0 |
| NYAM | 153 | -1 | -15 | -38 | 169 | 39 | 0 | -0 | 0 (same stored bars) | -0 |
| NYPM | 110 | 0 | 15 | 3 | 62 | 30 | 0 | -13 | 0 (same stored bars) | -0 |
| Four sessions | 111 | -1 | -10 | -23 | 111 | 33 | 0 | -2 | 0 (same stored bars) | -0 |

Reading: (1) different trades: none on the exact side without a quick signal; exact-only and quick-only trades that are not blocking are 0 to 6 per session; (2) exit kind: whipsaws where the later and different entry hits the other bracket leg; negative because quick-stop to exact-target trades are fewer than quick-target to exact-stop trades; (3) fills and cost: stop and time-exit fills (3a) and the fee (3b: the engine charges $1.18, FEES.md standard and the grid charge $4.84); (4) session window and flatten: not a source (both flatten at the same scheduled second, exits 1.1 s apart on median) and week binning is the same for both after the fix (0); (5) one-position blocking: exit timing differences let a signal in on one side only; (6) level file version (column = quick re-simulation minus stored grid weekly points, $/lot/wk): quick re-simulation with today's level code minus the stored grid weekly points = 0 in 614 of 615 blocks; the exception is NY PM, time_m_60 bars, trig_levels_sdx3, weeks 104-117 (re-simulated -24,127 $ vs stored -4,816 $), which is also why the NY PM column shows -13; (7) bar builder: zero between the two (same stored bars); versus a live NT8 bar builder it is the print-rule risk, see D8_PRINT_RULE.md and the SPEC_STACK flags (tsf bars).

### A3. Trade counts

| session | quick trades | exact trades | matched (same signal second and side) | quick-only: exact position open at that moment | quick-only: other | exact-only: signal exists in quick but quick was in a position | exact-only: signal absent in quick | exit kind differs among matched |
|---|---|---|---|---|---|---|---|---|
| Asia | 13228 | 13198 | 12977 | 238 | 13 | 221 | 0 | 183 (1.4%) |
| London | 6550 | 6563 | 6506 | 44 | 0 | 57 | 0 | 42 (0.6%) |
| NYAM | 71822 | 72224 | 67855 | 3961 | 6 | 4369 | 0 | 965 (1.4%) |
| NYPM | 12567 | 12574 | 12394 | 163 | 10 | 180 | 0 | 113 (0.9%) |
| Four sessions | 104167 | 104559 | 99732 | 4406 | 29 | 4827 | 0 | 1303 (1.3%) |

### A4. Matched trades by exit kind (quick exit -> exact exit) and fill terms

| quick exit -> exact exit | matched trades | mean exact gross - quick gross ($/trade) | sum ($) |
|---|---|---|---|
| Stop -> RollFlat | 25 | 5226.8 | 130670 |
| Stop -> Stop | 34168 | 42.0 | 1435798 |
| Stop -> Target | 230 | 3411.6 | 784667 |
| Stop -> UWTime | 110 | 1137.9 | 125164 |
| Target -> RollFlat | 14 | -1932.5 | -27055 |
| Target -> Stop | 361 | -3155.8 | -1139235 |
| Target -> Target | 33236 | -0.0 | -1162 |
| Target -> UWTime | 126 | -1188.5 | -149755 |
| UWTime -> Stop | 230 | -905.1 | -208182 |
| UWTime -> Target | 207 | 1124.2 | 232703 |
| UWTime -> UWTime | 31025 | -7.1 | -219457 |

| matched same-kind trades | n | mean gross diff ($/trade) | median | share of trades with exact worse | notes |
|---|---|---|---|---|---|
| Stop | 34168 | 42.0 | 25.9 | 1% | 1 tick = $5 |
| Target | 33236 | -0.0 | 0.0 | 0% | 1 tick = $5 |
| UWTime | 31025 | -7.1 | -4.1 | 55% | 1 tick = $5 |

entry delay after the signal bar closes (seconds, matched trades): quick median 1.05 (p90 1.49); exact median 2.58 (p90 2.98). Session-end exits (both UWTime): exact exit minus quick exit time median 1.1 s, mean 1.5 s (n 31025).

RollFlat exits (roll-day flatten) exist only in the engine: 39 matched trades. Targets: identical by construction (target distance is measured from the fill in both). Stops: the engine stop exit is $42 per trade better on average than the tape walk (median $26, 85% of exact stop exits fill better than the stop level, 95% at or better); time exits: exact $7 worse on average. Unmatched trades:

| side of the diff | reason | trades | sum of net $ | mean $/trade |
|---|---|---|---|---|
| exact only | signal exists in quick, quick in a position | 4827 | -159761 | -33 |
| quick only | other engine was in a position | 4406 | -54401 | -12 |
| quick only | no exact trade, no open exact position | 29 | 14610 | 504 |

### A5. The 10 worst books (largest |exact - quick| over their held weeks), trade by trade for one month each: autopilot/TEST10_TRADE_DIFFS.md

| book | session | bar row | level module | bracket | quick $ | exact $ | exact - quick | trades Q / E | blocking | exit kind | fills (same kind) | different trades |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Wf8f607c7 | NYAM | urenko_20 | vwap | sym15u | 81273 | 128063 | 46790 | 978 / 972 | 22267 | 8637 | 12453 | 0 |
| W1ef860b8 | NYAM | rng_10 | vwap | fixed40/80 | -4902 | 39288 | 44189 | 1031 / 1036 | 23556 | -6901 | 24309 | 0 |
| Waf4a74e5 | NYAM | urenko_14 | fibr_on | asym15u/30u | -23085 | 14134 | 37218 | 216 / 213 | 24382 | 8609 | 3529 | 0 |
| Wd3cecb79 | NYAM | swing_atr_0.25 | fibr_on | sym15u | -55320 | -26878 | 28441 | 223 / 219 | 24056 | 26 | 3624 | 0 |
| W97d824da | NYAM | mrenko_20 | vwap | asym15u/30u | -17284 | 11077 | 28361 | 172 / 172 | 7372 | 17519 | 2906 | 0 |
| W4388e767 | NYAM | kagi_40 | fibr_dev | fixed60/120 | -18257 | 6383 | 24640 | 337 / 332 | 18890 | -6474 | 11107 | 0 |
| We583dde1 | NYAM | urenko_80 | fibr_dev | asym10u/20u | -31833 | -7527 | 24305 | 167 / 163 | 28121 | -6509 | 2137 | 0 |
| W5fe4c111 | NYAM | mrenko_14 | fibr_on | asym15u/30u | -67471 | -43535 | 23936 | 226 / 220 | 19412 | 107 | 3685 | 0 |
| Wd1723206 | NYAM | mrenko_14 | fibr_on | asym15u/30u | -67471 | -43535 | 23936 | 226 / 220 | 19412 | 107 | 3685 | 0 |
| W026b1e87 | NYAM | mrenko_20 | vwap | sym30u | 75729 | 52126 | -23604 | 562 / 563 | -25916 | -6841 | 7220 | 0 |

All ten are NY AM books on renko / kagi / range / swing bars with VWAP, fib-on or fib-dev levels (W5fe4c111 and Wd1723206 are twin cells). **In these ten the dominant term is one-position blocking, not fills:** blocking is +19k to +28k per book in nine of them (exact took trades that quick skipped while it was still in a position, net winners) and -26k in W026b1e87 (the other way round); exit kind and stop fills come second. Why it does not cancel here: these are wide brackets (40 to 120+ point legs = $800 to $2,400 and more per leg: sym30u, fixed 60/120, fixed 40/80, asym 15u/30u), so one trade taken by one engine and blocked in the other is worth a full leg; exact exits are earlier than quick on 20-25% of matched exits (targets fill on touch in the engine, one tick THROUGH in the tape walk; stop pump exits before the stop print) and later on 14-17%, so the engine is flat sooner and re-enters. Over all 615 blocks the same effect nets to -10 $/lot/wk (A2) because it is symmetric in sign across books and mostly small on narrow brackets.

Stack books (A4, A5, N4, N5 from the forward register) in the same terms, exact versus quick over the Test 8 held block (weeks 169-185):

| stack | book | trades quick / exact | matched | quick $ | exact $ |
|---|---|---|---|---|---|
| A4 | W73585da1 | 26 / 26 | 26 | 3818 | 3699 |
| A4 | We7eba185 | 276 / 277 | 274 | 26586 | 27043 |
| A4 | W68089a3e | 264 / 263 | 263 | 20656 | 23825 |
| A4 | W0e7037ba | 199 / 197 | 196 | 44671 | 43873 |
| A4 | Wf5779582 | 10 / 9 | 9 | 3593 | 2444 |
| A4 | W65dc0e76 | 55 / 56 | 55 | -6720 | -7151 |
| A5 | Wff6cb74e | 77 / 77 | 77 | 10452 | 10844 |
| A5 | W1539c680 | 82 / 81 | 80 | 4145 | 5429 |
| A5 | W87b89d8f | 144 / 143 | 137 | 18264 | 34826 |
| A5 | W4a911926 | 10 / 9 | 9 | 3593 | 2444 |
| A5 | W0778abb1 | 28 / 27 | 27 | 9069 | 10333 |
| A5 | W0d8714f7 | 103 / 103 | 103 | 8026 | 9898 |
| N4 | Wbcfa80fb | 123 / 121 | 120 | 70910 | 62887 |
| N4 | Wc7c3f9c5 | 675 / 677 | 653 | 63657 | 74236 |
| N4 | We3999e99 | 4 / 4 | 4 | 3539 | 3605 |
| N4 | W9fd5ca5d | 0 / 0 | 0 | 0 | 0 |
| N4 | W5ba295af | 130 / 130 | 130 | 8231 | 11112 |
| N4 | Wbb4ef729 | 524 / 529 | 492 | 119692 | 114961 |
| N5 | W3b484778 | 25 / 25 | 25 | -1626 | -1299 |
| N5 | Wb1ab799c | 39 / 41 | 39 | 19527 | 15067 |
| N5 | Wf74d00e3 | 121 / 121 | 118 | 55628 | 53927 |
| N5 | W3e503490 | 22 / 22 | 22 | 1828 | 2334 |
| N5 | W10e7f4cd | 20 / 20 | 20 | 5832 | 6211 |
| N5 | Wd5038cce | 124 / 126 | 122 | 34947 | 50766 |

## B. WHICH BOOKS SURVIVE: AGREE vs DISAGREE, and the Test 8 primary re-scored on exact numbers (DIAGNOSTIC, not a rule)

AGREE = a held cell whose exact P&L over its held weeks is within 30% of its quick P&L and has the same sign (cells with an unlanded block are in neither). Scored with the Test 8 machinery (analysis8.py: valid cells only = draw 0 re-simulation equals the stored grid, 200 drift-null draws, paired weekly bootstrap block 4, PASS rule unchanged), but with the EXACT weekly numbers in place of the quick weekly numbers for the held cells; the null is the QUICK drift null of the same cells (the exact null is section C). Weights are the Test 8 weights, so units held = cells held per week.

### B. ALL valid cells with exact landed (the Test 8 primary on exact numbers)

| scope | cells (valid) | units held (mean) | exact $/lot/wk | quick $/lot/wk same cells | quick null | excess (exact - null) | exact beats share of 200 draws | paired p | verdict | L6M exact / quick / null | L3M exact / quick / null |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 90 | 8.1 | 292 | 307 | 64 | 228 | 1.000 | 0.023 | **PASS** | 744 / 786 / 6 | 470 / 519 / -128 |
| London | 61 | 5.5 | -101 | -68 | 11 | -113 | 0.260 | 0.766 | **FAIL** | -336 / -324 / -10 | -671 / -647 / -20 |
| NY AM | 267 | 32.8 | 604 | 500 | 60 | 544 | 1.000 | 0.001 | **PASS** | 576 / 512 / 57 | 604 / 741 / 292 |
| NY PM | 57 | 7.7 | 340 | 290 | 0 | 340 | 0.995 | 0.104 | **FAIL** | 871 / 676 / 220 | -9 / -16 / 272 |
| Four sessions summed | 475 | 54.1 | 437 | 353 | 41 | 396 | 1.000 | 0.002 | **PASS** | 471 / 382 / 4 | 451 / 526 / 84 |

| scope | 2023 Q4 exact / quick / null | 2024 | 2025 | 2026 | first 80 wk exact / quick / null (beats) | last 80 wk exact / quick / null (beats) |
|---|---|---|---|---|---|---|
| Asia | 177 / 173 / -64 | 158 / 32 / 108 | -1 / 146 / 79 | 863 / 892 / 29 | 119 / 32 / 64 (0.69) | 465 / 582 / 64 (1.00) |
| London | -218 / -228 / 62 | -320 / -270 / 56 | 226 / 276 / -31 | -208 / -200 / -6 | -59 / -78 / 30 (0.30) | -144 / -57 / -7 (0.32) |
| NY AM | -106 / -210 / -158 | 687 / 587 / 138 | 819 / 703 / 21 | 448 / 354 / 80 | 497 / 326 / 60 (1.00) | 710 / 674 / 60 (1.00) |
| NY PM | -612 / -685 / -108 | 61 / -97 / -7 | 1010 / 1156 / -109 | 136 / -22 / 180 | 283 / 153 / -47 (0.95) | 398 / 427 / 48 (0.94) |
| Four sessions summed | -186 / -238 / -44 | 352 / 244 / 104 | 752 / 699 / -2 | 337 / 231 / 43 | 297 / 141 / 51 (1.00) | 577 / 564 / 31 (1.00) |

### B. AGREE cells only

| scope | cells (valid) | units held (mean) | exact $/lot/wk | quick $/lot/wk same cells | quick null | excess (exact - null) | exact beats share of 200 draws | paired p | verdict | L6M exact / quick / null | L3M exact / quick / null |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 42 | 4.1 | 297 | 381 | 93 | 204 | 0.980 | 0.062 | **PASS** | 725 / 803 / 19 | 302 / 427 / -98 |
| London | 43 | 3.6 | -214 | -198 | 0 | -215 | 0.005 | 0.979 | **FAIL** | -336 / -324 / -10 | -671 / -647 / -20 |
| NY AM | 134 | 17.7 | 850 | 818 | 76 | 775 | 1.000 | 0.000 | **PASS** | 1332 / 1468 / 92 | 1192 / 1482 / 376 |
| NY PM | 31 | 4.5 | 345 | 401 | 9 | 336 | 0.955 | 0.163 | **FAIL** | 1540 / 1438 / 333 | -152 / -161 / 241 |
| Four sessions summed | 250 | 29.9 | 570 | 572 | 54 | 516 | 1.000 | 0.000 | **PASS** | 839 / 897 / 45 | 555 / 725 / 124 |

| scope | 2023 Q4 exact / quick / null | 2024 | 2025 | 2026 | first 80 wk exact / quick / null (beats) | last 80 wk exact / quick / null (beats) |
|---|---|---|---|---|---|---|
| Asia | 400 / 615 / 169 | 106 / 118 / 128 | -15 / 137 / 78 | 893 / 941 / 43 | 121 / 160 / 115 (0.56) | 472 / 602 / 70 (1.00) |
| London | -372 / -378 / 47 | -369 / -320 / 85 | -29 / -33 / -89 | -208 / -200 / -6 | -320 / -291 / 4 (0.01) | -109 / -105 / -3 (0.24) |
| NY AM | -252 / -316 / -186 | 822 / 769 / 157 | 999 / 914 / 38 | 1040 / 1107 / 103 | 583 / 501 / 68 (1.00) | 1118 / 1134 / 83 (1.00) |
| NY PM | -903 / -981 / -149 | -132 / -178 / 11 | 1034 / 1349 / -164 | 454 / 351 / 273 | 85 / 78 / -60 (0.71) | 606 / 725 / 79 (0.97) |
| Four sessions summed | -353 / -384 / -58 | 414 / 380 / 136 | 868 / 901 / -13 | 674 / 692 / 72 | 335 / 278 / 62 (0.99) | 806 / 867 / 46 (1.00) |

### B. DISAGREE cells only

| scope | cells (valid) | units held (mean) | exact $/lot/wk | quick $/lot/wk same cells | quick null | excess (exact - null) | exact beats share of 200 draws | paired p | verdict | L6M exact / quick / null | L3M exact / quick / null |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 48 | 4.0 | 140 | 69 | 23 | 118 | 0.900 | 0.092 | **FAIL** | 598 / 618 / 7 | 646 / 606 / -164 |
| London | 18 | 1.9 | 21 | 25 | 24 | -3 | 0.465 | 0.490 | **FAIL** | 0 / 0 / 0 | 0 / 0 / 0 |
| NY AM | 133 | 15.1 | 218 | 52 | -20 | 239 | 0.875 | 0.105 | **FAIL** | -395 / -669 / -43 | -596 / -659 / 79 |
| NY PM | 26 | 3.2 | 270 | 107 | 39 | 231 | 0.840 | 0.145 | **FAIL** | 378 / 123 / 120 | 262 / 201 / 278 |
| Four sessions summed | 225 | 24.2 | 300 | 111 | 23 | 278 | 0.995 | 0.021 | **PASS** | 47 / -195 / -45 | 267 / 245 / 30 |

| scope | 2023 Q4 exact / quick / null | 2024 | 2025 | 2026 | first 80 wk exact / quick / null (beats) | last 80 wk exact / quick / null (beats) |
|---|---|---|---|---|---|---|
| Asia | 122 / 62 / -122 | 227 / 26 / 87 | -49 / -64 / 17 | 279 / 291 / -4 | 167 / 27 / 37 (0.90) | 114 / 110 / 9 (0.77) |
| London | 157 / 135 / 98 | -256 / -205 / 16 | 277 / 242 / 34 | 0 / 0 / 0 | 77 / 1 / 53 (0.52) | -35 / 49 / -4 (0.47) |
| NY AM | 187 / 2 / -102 | 49 / 18 / -49 | 769 / 545 / -1 | -256 / -513 / 16 | 121 / -91 / -54 (0.70) | 316 / 194 / 13 (0.93) |
| NY PM | -126 / -192 / -39 | 440 / 121 / -21 | 443 / 434 / 66 | -38 / -232 / 102 | 426 / 179 / 13 (0.85) | 113 / 34 / 64 (0.56) |
| Four sessions summed | 139 / 47 / -16 | 198 / 8 / 57 | 700 / 520 / 9 | -27 / -258 / 9 | 226 / -54 / 33 (0.93) | 374 / 276 / 12 (0.99) |

Reading: (a) on exact numbers the primary passes where it passed on quick (summed, Asia, NY AM), fails where it failed (London; NY PM p just above 0.10); exact is above quick in the sum, so the quick screen was not flattering the books. (b) AGREE holds 324 cells (157 in NY AM), DISAGREE 267 (all cells with every block landed; 250 and 225 of them are valid cells and enter the null scoring above): DISAGREE cells are mostly cells where exact is ABOVE quick (stop fills), so DISAGREE is not a bucket of broken books. (c) The second-half concentration found in Test 8 is unchanged on exact numbers (rows above). (d) London is negative on every cut and is not rescued by either filter.

Composition (held cells ever, all 606; level type from the module name):

| level type | AGREE cells | DISAGREE cells | share AGREE |
|---|---|---|---|
| VWAP | 59 | 75 | 44% |
| other levels | 70 | 41 | 63% |
| swing S/R, trendline, channel | 50 | 34 | 60% |
| prior day / session / opens / range | 46 | 28 | 62% |
| fib | 37 | 29 | 56% |
| pivot | 25 | 31 | 45% |
| profile / zones / stack | 24 | 16 | 60% |
| round numbers | 9 | 10 | 47% |
| book walls | 3 | 2 | 60% |
| supply-demand (sd/sdx) | 1 | 1 | 50% |

By session (AGREE / DISAGREE cells): Asia 72 / 61; London 55 / 20; NYAM 157 / 155; NYPM 40 / 31.

## C. EXACT DRIFT NULL, SMALL (20 draws on the exact engine)

**Status: counted, built and queued at 01:12Z; nothing landed yet, so there is no exact-null result on this page.** The quick-screen drift null is the same engine on the same signals as the quick re-simulation, so the exact null is the check that includes the engine's stop fills, blocking and latency in the null as well as in the real rows.

| scope | held cells | set-months per draw | x 20 draws = rows | hours of fleet at 13.3k rows/h (10k-14k: range) |
|---|---|---|---|---|
| Test 8 Asia | 140 | 618 | 12,360 | 0.9 (0.9-1.2) |
| Test 8 NY AM | 319 | 1,730 | 34,600 | 2.6 (2.5-3.5) |
| Test 5 primary, Asia (126 cells shared with Test 8) | 1,639 | 7,167 | 143,340 | 10.8 (10.2-14.3) |
| union queued | 1,972 | 8,954 | 179,080 | 13.5 (12.8-17.9) |

Draw files: events /mnt/l2/l2vast/_rota/ev/T10X_<cell>_<dd>.parquet (39,440 files, 1.2 GB), sets /mnt/l2/l2vast/_th_sz/ijk/exact/sets/TL3_ALN_<AS|NY>_<cell>_T10X<dd>.json, rows files /mnt/l2/l2vast/_test10/rows_T10X_0.txt and _1.txt. **Rows ahead:** 227,950 not-DONE rows in pending_nyam_gating.txt at 01:05Z (the directive said about 234k); at the measured fleet rate of 13.3k rows/h (HEALTH 00:17Z) the first of my rows starts in about 17 h, the last lands about 30 h from the posting (Saturday 28 Nov about 07:30Z); at 10k rows/h about 40 h. Nothing was moved ahead of the other rows and nothing was reordered. **Scoring:** code/th_test10/score_null10.py (run when the rows land; reports real vs the 20 draws, excess and the share of draws beaten for the three scopes on blocks whose real and all 20 draw months are DONE; the resolution of 20 draws is p = 1/21).


## D. LEVEL FILES: VERIFIED CURRENT / STALE-REBUILT / STALE-DROPPED (read-only)

State read: grid extract on server C of 26 Nov 16:03Z (10274 level files in 51 modules, the same file list Test 6 and 8 used; a re-stat of 3,000 files of the extract found 0 changed mtimes), result stamps checked against today's module code on 26 Nov 21:21Z (W-TEST7 stampcheck, re-read here), module code mtimes (all 51 modules last edited 17-18 Nov 00:11Z at the latest, i.e. BEFORE the 18 Nov 06:00Z cut), SEARCH_STATUS.md stale table (re-run owners W-SHORT / W-GRIDOPS; MORNING 00:00Z: Dallas 12 stale real files, Frankfurt 1,660, Singapore 1,657 before their merge: the re-run is NOT finished, so the C copy still holds 1,095 stale level files = 10.7% of the level files). Rule used for the label: **STALE-DROPPED** = more than 10% of the module's grid files are still pre-cut (re-run incomplete; those files are dropped by Tests 6 set (3) and 8, the module's fresh files are kept); **STALE-REBUILT** = at least 90% fresh and at least one fresh file whose result stamp differs from today's code (rebuilt after the cut but under a different dependency/store version: unverified until re-stamped); **VERIFIED CURRENT** = at least 90% fresh and no stamp mismatch (stamp-equal or unstamped-but-fresh files; the unstamped files are verified by mtime only, module code is older than the file). Counts: 27 STALE-DROPPED, 14 VERIFIED CURRENT, 10 STALE-REBUILT.

| level module (trig_levels_...) | grid files | fresh (>= 18 Nov 06:00Z) | stale (dropped) | fresh, stamp = today code | fresh, unstamped | fresh, stamp differs | Test 8 held blocks | label |
|---|---|---|---|---|---|---|---|---|
| book_walls | 193 | 151 | 42 | 0 | 151 | 0 | 1 | **STALE-DROPPED** |
| book_walls_loose | 207 | 168 | 39 | 22 | 146 | 0 | 6 | **STALE-DROPPED** |
| channel | 194 | 179 | 15 | 45 | 134 | 0 | 33 | **VERIFIED CURRENT** |
| fib15 | 258 | 252 | 6 | 120 | 131 | 1 | 18 | **STALE-REBUILT** |
| fib5 | 227 | 216 | 11 | 79 | 135 | 2 | 10 | **STALE-REBUILT** |
| fib60 | 221 | 209 | 12 | 70 | 139 | 0 | 12 | **VERIFIED CURRENT** |
| fibr_dev | 197 | 188 | 9 | 60 | 127 | 1 | 20 | **STALE-REBUILT** |
| fibr_ib | 182 | 167 | 15 | 20 | 146 | 1 | 7 | **STALE-REBUILT** |
| fibr_on | 173 | 161 | 12 | 19 | 141 | 1 | 22 | **STALE-REBUILT** |
| fibr_or | 180 | 162 | 18 | 18 | 144 | 0 | 7 | **VERIFIED CURRENT** |
| fibr_pd | 203 | 191 | 12 | 52 | 137 | 2 | 12 | **STALE-REBUILT** |
| fvg15 | 181 | 162 | 19 | 16 | 146 | 0 | 1 | **STALE-DROPPED** |
| fvg5 | 234 | 222 | 12 | 96 | 125 | 1 | 18 | **STALE-REBUILT** |
| gaps | 192 | 173 | 19 | 31 | 142 | 0 | 4 | **VERIFIED CURRENT** |
| mmove | 183 | 173 | 10 | 37 | 136 | 0 | 14 | **VERIFIED CURRENT** |
| ob15 | 172 | 151 | 21 | 0 | 151 | 0 | 11 | **STALE-DROPPED** |
| ob5 | 180 | 161 | 19 | 14 | 145 | 2 | 9 | **STALE-DROPPED** |
| open_range | 222 | 187 | 35 | 39 | 148 | 0 | 4 | **STALE-DROPPED** |
| opens | 252 | 227 | 25 | 90 | 136 | 1 | 6 | **STALE-REBUILT** |
| piv_cama | 181 | 166 | 15 | 23 | 143 | 0 | 0 | **VERIFIED CURRENT** |
| piv_floor | 192 | 182 | 10 | 47 | 135 | 0 | 48 | **VERIFIED CURRENT** |
| piv_wf | 180 | 166 | 14 | 20 | 146 | 0 | 12 | **VERIFIED CURRENT** |
| prior_day | 225 | 191 | 34 | 49 | 142 | 0 | 45 | **STALE-DROPPED** |
| profile_nodes | 261 | 234 | 27 | 106 | 127 | 1 | 31 | **STALE-DROPPED** |
| profile_va | 255 | 224 | 31 | 97 | 127 | 0 | 14 | **STALE-DROPPED** |
| round | 269 | 241 | 28 | 107 | 126 | 8 | 19 | **STALE-DROPPED** |
| sd15 | 172 | 151 | 21 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| sd5 | 172 | 151 | 21 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| sd60 | 172 | 151 | 21 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| sdx15 | 173 | 152 | 21 | 2 | 150 | 0 | 4 | **STALE-DROPPED** |
| sdx3 | 174 | 163 | 11 | 21 | 142 | 0 | 4 | **VERIFIED CURRENT** |
| sdx30 | 172 | 151 | 21 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| sdx5 | 173 | 157 | 16 | 9 | 148 | 0 | 1 | **VERIFIED CURRENT** |
| sdx60 | 172 | 151 | 21 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| sdx_renko28 | 172 | 153 | 19 | 7 | 146 | 0 | 0 | **STALE-DROPPED** |
| sdx_rng28 | 172 | 155 | 17 | 8 | 147 | 0 | 1 | **VERIFIED CURRENT** |
| sdx_vol1100 | 172 | 153 | 19 | 10 | 143 | 0 | 1 | **STALE-DROPPED** |
| session_hl | 257 | 231 | 26 | 95 | 136 | 0 | 5 | **STALE-DROPPED** |
| stack | 202 | 185 | 17 | 42 | 143 | 0 | 2 | **VERIFIED CURRENT** |
| swcluster | 177 | 156 | 21 | 11 | 142 | 3 | 2 | **STALE-DROPPED** |
| swsr15 | 180 | 169 | 11 | 25 | 144 | 0 | 2 | **VERIFIED CURRENT** |
| swsr5 | 207 | 195 | 12 | 64 | 131 | 0 | 18 | **VERIFIED CURRENT** |
| swsr60 | 178 | 160 | 18 | 19 | 141 | 0 | 5 | **STALE-DROPPED** |
| trendline | 235 | 227 | 8 | 98 | 128 | 1 | 55 | **STALE-REBUILT** |
| uw_dp | 194 | 150 | 44 | 0 | 150 | 0 | 0 | **STALE-DROPPED** |
| uw_ndx | 194 | 151 | 43 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| uw_qqq | 194 | 151 | 43 | 0 | 151 | 0 | 0 | **STALE-DROPPED** |
| vwap | 291 | 272 | 19 | 147 | 123 | 2 | 133 | **STALE-REBUILT** |
| vwap_bands | 247 | 216 | 31 | 79 | 136 | 1 | 10 | **STALE-DROPPED** |
| week_month | 195 | 151 | 44 | 1 | 150 | 0 | 0 | **STALE-DROPPED** |
| zones | 213 | 173 | 40 | 28 | 144 | 1 | 3 | **STALE-DROPPED** |

Test 8 held blocks (630) by file class: fresh and stamp-equal 483, fresh and unstamped 147, stale 0, stamp-mismatch 0, no file 0: **every Test 8 held block rests on a verified-or-fresh file**, because the Test 6 set (3) rule (mtime >= 18 Nov 06:00Z) is part of the Test 8 walk. The 29 stamp-mismatch files are all outside the held blocks.

**Does any conclusion change on verified-only data?** Test 5 vs Test 6 set (3) is the stale-dropped re-score and is on the Test 6 page (summed +135 -> +139, Asia +178 -> +148, NY AM +172 -> +166, NY PM +190 -> +276 with print-rule types also removed; set (2) = stale only: +132, Asia +176, NY AM +166, NY PM +185): no pass flips except NY AM by 0.006 in set (3). Test 8 already sits on set (3). Two further re-walks of the Test 8 primary on server C (code/th_test10/walk8v.py = walk8.py plus a stamp filter; raw quick baskets, no null draws for the new cells, so read them against the primary's own null of +41 summed):

| scope | primary raw $/lot/wk (L6M / L3M) | drop the 29 stamp-mismatch files: raw (L6M / L3M) | keep ONLY stamp-verified level files: raw (L6M / L3M) | units held, mean (primary / mismatch dropped / verified only) |
|---|---|---|---|---|
| Asia | 383 (689 / 387) | 383 (689 / 387) | 346 (656 / 553) | 13 / 13 / 8 |
| London | -108 (-324 / -647) | -86 (-324 / -647) | -44 (-324 / -647) | 7 / 7 / 6 |
| NY AM | 450 (512 / 686) | 454 (512 / 686) | 500 (591 / 819) | 40 / 41 / 34 |
| NY PM | 282 (686 / 167) | 282 (686 / 167) | 257 (699 / 30) | 10 / 10 / 8 |
| Four sessions summed | 319 (340 / 439) | 320 (340 / 439) | 349 (431 / 580) | 70 / 70 / 55 |

Nothing changes: dropping the mismatching files moves the summed basket by 1 $/lot/wk; the stamp-verified-only basket (smaller, 55 units instead of 70) is higher, not lower (349 vs 319; London -44, still negative). The Test 8 verdicts do not depend on unverified level files. What stays open: the re-run is unfinished (1,095 stale files in the C copy; the live Dallas merge may be further along), and 7207 of 9179 fresh level files are unstamped (mtime-verified only).

## E. HOUSEKEEPING (belongs to W-SCORE, not done here)

Scorers for Test 6 exact and Part C rows, Q2 re-queue, queue_rows_safe.py for every agent: W-SCORE's part E. Seen from here: the MORNING 00:23Z LEAD TO JOSH says Test 6 exact is scored; the Q2 rows are in the queue tail. I used only queue_rows_safe.py.

## FILES AND CAVEATS

- Code: code/th_test10/ (recq.py trade-level quick re-simulation, runq.py, recon10.py, analyze10.py, tradediff10.py, anal10B.py [server C], anal10D.py + walk8v.py [server C], build_null10.py, modtable10.py, t5check10.py, midmonths10.py, build10.py). Data: box1 /mnt/l2/l2vast/_test10 (q/ quick trade lists per cell, recon10.pkl, rows_T10X_*.txt), server C /mnt/l2/l2vast/_test10 (anal10B.pkl, out_v/ walks).
- Cell identity: 606 cells, 630 blocks; 15 blocks (NY AM 7, Asia 7, NY PM 1) still have a month in the queue and are excluded from every table above; a block with a quick-only or exact-only trade is counted as such, never dropped.
- The quick re-simulation is the same code path as the grid (gcore2x single-bracket copy); verified equal to the stored grid weekly points on every block (cause 6 row).
- Fees: engine $1.18 per trade vs FEES.md $4.84 round trip for NQ. The exact numbers in this page are as the engine produces them; at the standard fee exact falls by about 33 $/lot/wk (cost row). Which fee the engine should carry is not mine to change.
- Stop fills better than the stop level (85% of exact stop exits) look like the engine's stop-join / stop-pump logic (pump_stop_exit in replica/sim.py, the port of the live strategy code); I did not check them against live stop fills of a book that uses the pump. That is the one open item that could move exact down by up to the +111 $/lot/wk fill term.
- B uses the quick null for an exact result (the exact null is C); valid cells only (475 of 606); AGREE/DISAGREE is computed per cell over all of its blocks.
