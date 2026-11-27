# EXIT ANATOMY of the live mixes (W-DYNA, 07:20Z; exact trades of the 4 live sets, 42 months, 35,236 trades)

Answer first (drawdown first).
1. In every session the 5 worst weeks and the deepest drawdown window are made by the same thing: Stop exits (-0.97 to -0.98 R each, win rate 0%) that outrun the Target exits of the same weeks. Example NY AM worst week 2025-W01: Stop -$170k (25), DayHalt -$19k (8), Target +$74k (25) = -$109k; max drawdown window NY AM Apr 7-17 2025: Stop -$697k (125 trades) vs Target +$503k (163). London worst week 2025-W14: Stop -$285k (57) vs Target +$191k (53). NY PM worst weeks add EarlyCut (-$18k to -$24k in 4 of the 5 worst weeks) and time exits (UWTime -$5k to -$11k); Asia worst weeks add EarlyCut (-$3k to -$7k) and UWTime, and are rescued by PolicyTake (+$26k in the worst week 2026-W42). No other exit name (PolicyTrail, DayHalt, BookLock, RollFlat) is ever the main cause of a worst week; time exits (UWTime) are the second-largest loss item in NY AM and London (-$0.94M and -$1.41M over 42 months) and sit in 4 of the 5 worst weeks of each.
2. Where the money is made: NY AM Target +$26.2M against Stop -$21.3M (net +$3.69M); London Target +$9.4M, Stop -$7.0M, UWTime -$1.4M (net +$1.0M); NY PM Target +$7.96M, Stop -$5.95M, EarlyCut -$0.82M, PolicyTrail +$0.26M (net +$1.2M); Asia PolicyTake +$2.68M and Target +$2.90M, Stop -$4.67M, EarlyCut -$0.49M (net +$0.99M). Only Asia has PolicyTake; only NY PM and Asia have PolicyTrail and EarlyCut; NY AM and London have none of the profit-side layer exits, only Target, Stop, UWTime, DayHalt, BookLock.
3. What the market did AFTER each exit (1-s tape, side-adjusted, in R of the book stop): almost nothing systematic. Stops are followed by -0.03 to +0.05 R at 15-60 min (London -0.03: the stop saved money; NY PM +0.05 R at 60 min = +$293k over 42 months left on the table at the stop, 47% of stopped trades touch their entry price again within 60 min, NY AM 39%, Asia 28%, London 32%): stops are neither systematically early nor late. Targets are followed by about 0 R at 15 min and +0.00 to +0.03 R at 60 min (NY AM +$685k at 60 min on $26M of target profit; 56% of NY AM targets could have run another full target distance within 60 min, 46% NY PM, 36% London, 29% Asia). Time exits (UWTime) are followed by +0.01 to +0.05 R (+$150k to +$280k per session over 42 months at 15-60 min): the market continues slightly in the trade direction past the time exit. PolicyTrail (Asia, NY PM) is followed by +0.03 to +0.11 R at 15 min (Asia +$109k): the trail exits slightly early. EarlyCut and DayHalt are followed by 0 to -0.09 R (NY PM DayHalt -0.28 R at 60 min: the halt saved money). PolicyTake (Asia, 1,448 exits, +$2.68M): 0.00 R after the exit at 5/15/60 min: it gives away nothing on average, and 27% of takes could have run another target distance.
4. So what: the live exits are not leaking on average in the minutes after they fire; the money in the loss tail is the Stop itself (a fixed -1 R x lots event in every book) and the time exit in NY AM and London. Candidate leverage points are therefore the choice of WHICH trades reach the stop (entry quality, not exit timing) and the cost of UWTime exits (-0.04 to -0.08 R mean, 23-31% of trades), which the harness found no clock rule to improve except the 15-min-before-end flatten in profit (-0.049 R) and the London 08:29 exit.
Caveats: net $ are the exact engine trades at live lot sizes (equal-weight R is mean R per trade, not per lot); weeks are ISO weeks of the exit time; drawdown window = max peak-to-trough of cumulative net by exit order; R uses the book stop distance (the 1.7 % of trades without a bracket match, e.g. NP_MF2 whose exits are all time/policy, have no R and no post-exit row); post-exit moves are descriptive means (no test, 42 months, one path); '$ at +15/+60 min' = lots x $20 x side-adjusted points after the exit (+ = money left on the table); 'losers back to entry' counts only exits at a loss; the PolicyTrail 'losers back' cell is on a handful of losing trails and is not meaningful. Post-exit windows cross session ends (Asia exits near 02:00 ET see the London pre-open etc.).

## NY AM (NY): 15952 trades, net $+3693435, 9 books, 183 weeks

### 5 worst weeks (net $, by exit name)

| week | net $ | trades | net $ by exit name (trades) |
|---|---|---|---|
| 2025-W01 | -109226 | 63 | Stop -170314 (25), DayHalt -19195 (8), UWTime +6366 (5), Target +73917 (25) |
| 2026-W08 | -95290 | 152 | Stop -313192 (58), UWTime -17965 (15), DayHalt -12236 (2), Target +248103 (77) |
| 2024-W40 | -84027 | 124 | Stop -231104 (46), UWTime -20929 (20), Target +168006 (58) |
| 2025-W16 | -73692 | 102 | Stop -255298 (44), UWTime -11064 (9), DayHalt +888 (1), Target +191783 (48) |
| 2026-W13 | -61204 | 95 | Stop -172031 (40), DayHalt -12440 (5), UWTime +3586 (7), Target +119680 (43) |

### Max drawdown window (by exit order): $-199406 from 2025-04-07 to 2025-04-17, 305 trades

| exit name | trades | net $ in window | mean R |
|---|---|---|---|
| Stop | 125 | -697131 | -0.97 |
| UWTime | 15 | -3266 | -0.01 |
| BookLock | 1 | -2429 | -0.67 |
| DayHalt | 1 | +888 | +0.37 |
| Target | 163 | +502533 | +0.60 |

### Exit anatomy, all trades (net $, mean R, share of trades)

| exit name | trades | share | net $ | $/trade | mean R | win rate |
|---|---|---|---|---|---|---|
| Stop | 3972 | 24.9% | -21304755 | -5364 | -0.98 | 0% |
| UWTime | 3628 | 22.7% | -937999 | -259 | -0.04 | 46% |
| DayHalt | 125 | 0.8% | -138308 | -1106 | -0.11 | 43% |
| BookLock | 34 | 0.2% | -136363 | -4011 | -0.53 | 0% |
| Target | 8193 | 51.4% | +26210859 | +3199 | +0.58 | 100% |

### Per book x exit name (net $ / trades)

| book | BookLock | DayHalt | Stop | Target | UWTime | total |
|---|---|---|---|---|---|---|
| NY_MF1 | -80354 / 9 | -25238 / 31 | -3638609 / 387 | +4597290 / 488 | +348510 / 737 | +1201598 |
| NY_MF2 | -25588 / 9 | +13521 / 18 | -3591201 / 788 | +3930986 / 826 | +58023 / 347 | +385741 |
| NY_MF3 | +0 / 0 | -55246 / 22 | -2471278 / 274 | +2966176 / 333 | +67964 / 357 | +507617 |
| NY_MF4 | -4734 / 2 | -26231 / 17 | -4011985 / 578 | +5386592 / 2278 | -746855 / 421 | +596787 |
| NY_MF5 | -25687 / 14 | -3132 / 16 | -2711626 / 991 | +2906080 / 1039 | +115494 / 544 | +281127 |
| NY_MF6 | +0 / 0 | -25747 / 8 | -3698684 / 506 | +4702079 / 1941 | -606756 / 478 | +370892 |
| NY_MF7 | +0 / 0 | -12702 / 6 | -356012 / 112 | +575634 / 366 | -70156 / 401 | +136764 |
| NY_MF8 | +0 / 0 | -692 / 6 | -357908 / 205 | +496062 / 562 | -43963 / 154 | +93499 |
| NY_MF9 | +0 / 0 | -2839 / 1 | -467452 / 131 | +649961 / 360 | -60260 / 189 | +119411 |

### After the exit (1-s tape): side-adjusted price move vs the exit price, in R of the book stop; run-on = best favourable excursion in the next 15 min, adverse = worst; $ = lots x $20 x pts summed (+ = the market kept going the trade direction after the exit = exit left money; - = the exit saved money)

| exit name | n | move +5 min R | +15 min R | +60 min R | run-on 15 min R | adverse 15 min R | $ at +15 min | $ at +60 min | losers back to entry within 60 min | winners running >= one more target in 60 min |
|---|---|---|---|---|---|---|---|---|---|---|
| BookLock | 34 | -0.14 | -0.03 | -0.06 | +0.74 | -0.80 | +9325 | +23465 | 68% |  |
| DayHalt | 125 | -0.09 | -0.07 | -0.11 | +0.42 | -0.53 | -82435 | -61315 | 48% |  |
| Stop | 3972 | +0.01 | -0.01 | -0.01 | +0.63 | -0.65 | -471455 | -843455 | 39% |  |
| Target | 8193 | -0.01 | -0.01 | +0.00 | +0.54 | -0.56 | -221105 | +685120 |  | 56% |
| UWTime | 3628 | +0.01 | +0.01 | +0.02 | +0.22 | -0.22 | +149465 | +394995 |  |  |

## London (LO): 6093 trades, net $+1005706, 3 books, 183 weeks

### 5 worst weeks (net $, by exit name)

| week | net $ | trades | net $ by exit name (trades) |
|---|---|---|---|
| 2025-W14 | -105512 | 117 | Stop -284501 (57), UWTime -11638 (7), Target +190627 (53) |
| 2025-W10 | -63893 | 57 | Stop -112205 (25), UWTime -23649 (11), Target +71961 (21) |
| 2026-W04 | -52773 | 41 | Stop -114585 (16), UWTime -2926 (7), Target +64738 (18) |
| 2024-W32 | -48947 | 122 | Stop -228647 (53), UWTime -14510 (11), Target +194210 (58) |
| 2023-W33 | -48925 | 28 | Stop -52497 (11), UWTime -20405 (10), Target +23977 (7) |

### Max drawdown window (by exit order): $-250812 from 2025-03-03 to 2025-04-07, 272 trades

| exit name | trades | net $ in window | mean R |
|---|---|---|---|
| Stop | 115 | -564974 | -0.98 |
| UWTime | 45 | -73091 | -0.23 |
| Target | 112 | +387253 | +0.68 |

### Exit anatomy, all trades (net $, mean R, share of trades)

| exit name | trades | share | net $ | $/trade | mean R | win rate |
|---|---|---|---|---|---|---|
| Stop | 1555 | 25.5% | -6994643 | -4498 | -0.98 | 0% |
| UWTime | 1893 | 31.1% | -1410191 | -745 | -0.08 | 40% |
| Target | 2645 | 43.4% | +9410540 | +3558 | +0.69 | 100% |

### Per book x exit name (net $ / trades)

| book | Stop | Target | UWTime | total |
|---|---|---|---|---|
| LO_MF1 | -1651804 / 117 | +3210425 / 670 | -992688 / 343 | +565933 |
| LO_MF2 | -4219439 / 1201 | +4389932 / 1220 | +76489 / 676 | +246982 |
| LO_MF3 | -1123399 / 237 | +1810183 / 755 | -493993 / 874 | +192791 |

### After the exit (1-s tape): side-adjusted price move vs the exit price, in R of the book stop; run-on = best favourable excursion in the next 15 min, adverse = worst; $ = lots x $20 x pts summed (+ = the market kept going the trade direction after the exit = exit left money; - = the exit saved money)

| exit name | n | move +5 min R | +15 min R | +60 min R | run-on 15 min R | adverse 15 min R | $ at +15 min | $ at +60 min | losers back to entry within 60 min | winners running >= one more target in 60 min |
|---|---|---|---|---|---|---|---|---|---|---|
| Stop | 1555 | -0.02 | -0.02 | -0.03 | +0.56 | -0.65 | -129635 | -156735 | 32% |  |
| Target | 2645 | +0.01 | -0.00 | +0.03 | +0.43 | -0.41 | -61210 | +167660 |  | 36% |
| UWTime | 1893 | +0.04 | +0.02 | +0.02 | +0.37 | -0.32 | +182810 | +243640 |  |  |

## NY PM (NP): 7080 trades, net $+1215176, 4 books, 183 weeks

### 5 worst weeks (net $, by exit name)

| week | net $ | trades | net $ by exit name (trades) |
|---|---|---|---|
| 2025-W44 | -43616 | 36 | Stop -47750 (14), EarlyCut -23801 (2), UWTime -10933 (3), PolicyTrail +2311 (2), Target +36557 (15) |
| 2024-W45 | -43291 | 37 | Stop -35508 (15), UWTime -10436 (14), EarlyCut -5857 (1), PolicyTrail +2118 (4), Target +6391 (3) |
| 2025-W22 | -36717 | 41 | Stop -52984 (15), EarlyCut -17545 (3), UWTime -3286 (7), PolicyTrail +1751 (3), Target +35347 (13) |
| 2024-W46 | -34534 | 46 | Stop -63897 (24), UWTime -5263 (7), PolicyTrail +1113 (3), Target +33514 (12) |
| 2026-W12 | -26454 | 63 | Stop -69165 (25), EarlyCut -18135 (2), UWTime -9434 (8), PolicyTrail +2697 (5), Target +67583 (23) |

### Max drawdown window (by exit order): $-141601 from 2024-10-15 to 2024-12-18, 353 trades

| exit name | trades | net $ in window | mean R |
|---|---|---|---|
| Stop | 122 | -315353 | -0.97 |
| UWTime | 98 | -58490 | -0.11 |
| EarlyCut | 5 | -35132 | +nan |
| PolicyTrail | 28 | +13541 | +0.30 |
| Target | 100 | +253832 | +0.86 |

### Exit anatomy, all trades (net $, mean R, share of trades)

| exit name | trades | share | net $ | $/trade | mean R | win rate |
|---|---|---|---|---|---|---|
| Stop | 2183 | 30.8% | -5949159 | -2725 | -0.97 | 0% |
| EarlyCut | 116 | 1.6% | -815714 | -7032 | -0.98 | 0% |
| UWTime | 1414 | 20.0% | -218460 | -154 | -0.06 | 45% |
| DayHalt | 96 | 1.4% | -17530 | -183 | -0.03 | 50% |
| PolicyTrail | 540 | 7.6% | +259837 | +481 | +0.26 | 89% |
| Target | 2731 | 38.6% | +7956203 | +2913 | +0.87 | 100% |

### Per book x exit name (net $ / trades)

| book | DayHalt | EarlyCut | PolicyTrail | Stop | Target | UWTime | total |
|---|---|---|---|---|---|---|---|
| NP_MF1 | +2397 / 7 | -1762 / 1 | +261039 / 441 | -2642182 / 1436 | +2617512 / 1374 | -14851 / 294 | +222154 |
| NP_MF2 | +4195 / 36 | -813953 / 115 | +0 / 0 | +0 / 0 | +1187091 / 126 | +135517 / 310 | +512851 |
| NP_MF3 | -27180 / 19 | +0 / 0 | +0 / 0 | -1117780 / 204 | +1793326 / 660 | -243738 / 255 | +404627 |
| NP_MF4 | +3057 / 34 | +0 / 0 | -1202 / 99 | -2189197 / 543 | +2358274 / 571 | -95388 / 555 | +75544 |

### After the exit (1-s tape): side-adjusted price move vs the exit price, in R of the book stop; run-on = best favourable excursion in the next 15 min, adverse = worst; $ = lots x $20 x pts summed (+ = the market kept going the trade direction after the exit = exit left money; - = the exit saved money)

| exit name | n | move +5 min R | +15 min R | +60 min R | run-on 15 min R | adverse 15 min R | $ at +15 min | $ at +60 min | losers back to entry within 60 min | winners running >= one more target in 60 min |
|---|---|---|---|---|---|---|---|---|---|---|
| DayHalt | 60 | -0.06 | -0.09 | -0.28 | +0.39 | -0.51 | -24180 | -98415 | 41% |  |
| PolicyTrail | 540 | +0.01 | +0.03 | -0.02 | +0.76 | -0.71 | +50385 | +700 | 98% |  |
| Stop | 2183 | -0.01 | +0.01 | +0.05 | +0.72 | -0.74 | +75695 | +292735 | 47% |  |
| Target | 2605 | -0.01 | -0.01 | -0.01 | +0.67 | -0.67 | -156405 | -58555 |  | 46% |
| UWTime | 1104 | +0.02 | +0.02 | +0.02 | +0.32 | -0.28 | +62010 | +75230 |  |  |

## Asia (AS): 6111 trades, net $+993425, 4 books, 184 weeks

### 5 worst weeks (net $, by exit name)

| week | net $ | trades | net $ by exit name (trades) |
|---|---|---|---|
| 2026-W42 | -38721 | 64 | Stop -84941 (29), EarlyCut -6678 (4), UWTime -1602 (2), PolicyTrail +5580 (8), Target +22660 (7), PolicyTake +26260 (14) |
| 2025-W16 | -28867 | 41 | Stop -72239 (23), UWTime -607 (1), PolicyTrail +823 (2), DayHalt +2501 (1), PolicyTake +16116 (9), Target +24539 (5) |
| 2025-W21 | -28173 | 36 | Stop -53338 (16), EarlyCut -5442 (5), PolicyTrail +661 (1), UWTime +4643 (4), PolicyTake +9770 (5), Target +15532 (5) |
| 2025-W33 | -27217 | 27 | Stop -20331 (8), UWTime -8709 (15), EarlyCut -2933 (1), PolicyTrail +546 (1), PolicyTake +4209 (2) |
| 2024-W41 | -26827 | 23 | Stop -28402 (10), UWTime -1893 (9), EarlyCut -1517 (1), DayHalt +851 (1), PolicyTake +1436 (1), Target +2696 (1) |

### Max drawdown window (by exit order): $-66959 from 2025-05-06 to 2025-05-23, 86 trades

| exit name | trades | net $ in window | mean R |
|---|---|---|---|
| Stop | 38 | -111568 | -0.97 |
| EarlyCut | 10 | -11227 | -0.52 |
| PolicyTrail | 4 | +3010 | +0.29 |
| UWTime | 12 | +4706 | +0.27 |
| Target | 5 | +15053 | +1.39 |
| PolicyTake | 17 | +33067 | +0.55 |

### Exit anatomy, all trades (net $, mean R, share of trades)

| exit name | trades | share | net $ | $/trade | mean R | win rate |
|---|---|---|---|---|---|---|
| Stop | 1604 | 26.2% | -4674468 | -2914 | -0.98 | 0% |
| EarlyCut | 303 | 5.0% | -487932 | -1610 | -0.72 | 1% |
| DayHalt | 15 | 0.2% | +3511 | +234 | +0.17 | 67% |
| RollFlat | 17 | 0.3% | +5275 | +310 | +0.16 | 76% |
| PolicyTrail | 389 | 6.4% | +240561 | +618 | +0.28 | 95% |
| UWTime | 1644 | 26.9% | +326559 | +199 | +0.10 | 54% |
| PolicyTake | 1448 | 23.7% | +2677653 | +1849 | +0.54 | 100% |
| Target | 691 | 11.3% | +2902265 | +4200 | +1.51 | 100% |

### Per book x exit name (net $ / trades)

| book | DayHalt | EarlyCut | PolicyTake | PolicyTrail | RollFlat | Stop | Target | UWTime | total |
|---|---|---|---|---|---|---|---|---|---|
| AS_MF1 | +3945 / 9 | +0 / 0 | +0 / 0 | +34140 / 55 | +4868 / 12 | -1993005 / 783 | +1896296 / 358 | +534405 / 746 | +480648 |
| AS_MF2 | -3766 / 2 | -15392 / 48 | +219331 / 56 | -1139 / 28 | +171 / 2 | -430877 / 115 | +451975 / 115 | +31710 / 272 | +252013 |
| AS_MF3 | +2186 / 3 | +0 / 0 | +2458322 / 1392 | +0 / 0 | +236 / 3 | -2228076 / 695 | +253557 / 78 | -228126 / 431 | +258100 |
| AS_MF4 | +1146 / 1 | -472540 / 255 | +0 / 0 | +207560 / 306 | +0 / 0 | -22511 / 11 | +300438 / 140 | -11429 / 195 | +2664 |

### After the exit (1-s tape): side-adjusted price move vs the exit price, in R of the book stop; run-on = best favourable excursion in the next 15 min, adverse = worst; $ = lots x $20 x pts summed (+ = the market kept going the trade direction after the exit = exit left money; - = the exit saved money)

| exit name | n | move +5 min R | +15 min R | +60 min R | run-on 15 min R | adverse 15 min R | $ at +15 min | $ at +60 min | losers back to entry within 60 min | winners running >= one more target in 60 min |
|---|---|---|---|---|---|---|---|---|---|---|
| DayHalt | 15 | +0.01 | +0.06 | +0.12 | +0.48 | -0.46 | +1580 | +5540 | 80% |  |
| EarlyCut | 303 | +0.04 | -0.00 | +0.04 | +0.55 | -0.50 | -21961 | +17259 | 48% |  |
| PolicyTake | 1448 | +0.01 | +0.00 | -0.00 | +0.46 | -0.41 | +7010 | +29615 |  | 27% |
| PolicyTrail | 389 | +0.04 | +0.11 | +0.10 | +0.61 | -0.45 | +109495 | +87085 | 90% |  |
| RollFlat | 17 | +1.92 | +1.79 | +1.68 | +2.60 | +1.64 | +82510 | +76355 |  |  |
| Stop | 1604 | -0.02 | -0.03 | -0.04 | +0.45 | -0.54 | -110900 | -186380 | 28% |  |
| Target | 691 | +0.02 | +0.00 | -0.01 | +0.74 | -0.65 | -28160 | +5340 |  | 29% |
| UWTime | 1644 | +0.01 | +0.02 | +0.05 | +0.26 | -0.22 | +149235 | +277630 |  |  |


# UWTIME ANATOMY (W-DYNA, round 4, 07:45Z): the time exit of the live mixes

Answer first.
1. What UWTime is in the engine: the scheduled SESSION-END FLATTEN (mf_multi pushes an 'mmtime' event at the event row's exit_ts and requests exit 'UWTime'; code/th_sessend/se_hooks.py): Asia 02:00 ET, NY AM 12:00 ET, London 08:30 ET, NY PM 16:00 ET (a few NY PM trades end 12:59-13:15, the early flatten); no condition: any trade still open at that time is closed at market (+1 s). Every trade that does not stop or hit its target ends there. Share of trades: NY AM 23% (3,617), London 29% (1,695), Asia 27% (1,644), NY PM 17% (1,103). Net: NY AM -$936k, London -$1,224k, NY PM -$354k, Asia +$327k. By book it is concentrated: NY_MF4 -$747k and NY_MF6 -$607k (small-target books, T0 < S0), LO_MF1 -$893k, LO_MF3 -$435k, NY_MF1 +$357k and AS_MF1 +$534k are the positive ones (Asia MF1 and London MF2 reach +0.5R before the end in 68% / 54% of their time-exit trades).
2. R at the exit: mean -0.045 R (NY AM), -0.072 (London), -0.061 (NY PM), +0.100 (Asia); by book 23-68% of UWTime trades are positive. The path after the exit is flat: +0.00 to +0.05 R at 15 min (book table), so the exit is not early; the loss is in what the trades did before it.
3. Before the exit: 43-61% of UWTime trades reached only 10-50% of the way to target and finish at -0.16 to -0.19 R (NY AM -$1.62M, London -$0.99M, NY PM -$0.37M); 9-11% never were in profit (MFE < 10% of target distance) and end at -0.30 R (-$0.57M NY AM, -$0.35M London); the 46-47% that got at least half way to target finish positive on average (NY AM +0.11 R, +$1.26M; Asia +0.62 R, +$0.64M) but still give back on average 0.5R of their MFE (give-back column). In the strict 'once >= +0.5R' split only books with T0 >= 0.5 S0 can qualify (25% of NY AM, 20% London): they average +0.22 to +0.26 R at the exit after a +0.74 MFE: give-back +0.48 to +0.54 R, net still positive (+$1.66M NY AM). Open R at 30/60/90 min: a trade at <= -0.5R after 60 min ends on UWTime 46% (NY AM) / 28% (London) of the time and at -0.41 / -0.34 R; at 0..+0.5R after 60 min 68% / 39% end on UWTime at +0.13 / +0.02 R.
4. ROOM (no rule proposed): perfect hindsight is huge by construction (per trade the best of 17 alternatives: change vs baseline NY AM +$4.41M, London +$1.78M, NY PM +$0.89M, Asia +$0.92M; exit at each trade's own best open R: +$8.9M / +$3.8M / +$1.9M / +$2.0M) and means nothing for a rule. One-setting rules replayed on ALL trades (harm to Target/Stop trades counted, exit slippage 0.5 pt): the only settings positive in both the first 60% and last 40% of trades are NY AM 'C90_0.25' (at 90 min in, if open R <= -0.25 R exit at market: total +$85,955 = fit +$44k, hold +$42k; it costs the UWTime trades -$227k and saves +$313k on trades that would have gone on to the stop; 550 trades touched) and, much smaller, NY AM C60_0.5 (+$23k) and C90_0.5 (+$11k); London: B1.0_0.25 (once open R >= +1.0R move the stop to +0.25R: +$29k on 19 trades, both halves positive; too few trades); Asia B1.0_0.0 (+$19k, fit -$13k hold +$31k: not stable); NY PM: nothing positive in both halves (best -$17k). Earlier time exits E15..E120 (exit 15-120 min before the session end) lose on the UWTime trades alone in NY AM and Asia and gain there in London (+$143k..+$196k) and mixed in NY PM (, but -$193k..-$625k on the trades that would have hit their target in that window: net -$50k to -$441k); breakeven/lock stops B(0.5..0.75) lose heavily in NY AM (-$0.7M to -$1.0M): they cut targets. Partial exits at the time are linear in E (half of the E rows), so they cannot turn a negative E row positive.
5. So: the room for a different handling of the time-exit trades exists only in hindsight. The best one-setting variant on this path replay is NY AM C90_0.25 = +$86k over 42 months (about 9% of the NY AM UWTime loss, 0.2% of the NY AM total net; positive in both halves; not tested on the exact engine, and the Trade Health / layers interactions are not in this replay).
Row spec for W-PLAN-NY: one-setting variant 'C90_0.25' = for NY AM trades (all nine books, live lots), at 90 minutes after entry, if the trade is still open and its open R (side x (price - entry) / book stop distance S0) is <= -0.25, close at market (one order, 1 order change per trade, no widening); otherwise unchanged. Replay result: 550 of 15,745 NY AM trades touched, +$313k on trades that would have ended Stop/other, -$227k on trades that would have ended UWTime, net +$85,955 (fit +$44,260 / hold +$41,695), market-exit slippage 0.5 pt per lot included. For W-PLAN-LO: no variant has a positive result in both halves with a meaningful count (best B1.0_0.25, 19 trades, +$29k): London time exits are not helped by a one-setting rule here.
Caveats: replay on the 5-s path of the trade (bar high/low touches, no queue); the baseline exit of each trade is the exact engine's (Trade Health, layers, DayHalt included); a rule can only remove the later part of a trade, so it ignores what the engine's layers would have done differently in the changed trades; 17 settings x 4 sessions were tried (luck charge 68 for the 'best' choice); post-exit moves descriptive.

ok
### 1. UWTime exits per book (all = scheduled session-end flatten: Asia 02:00 ET, NY AM 12:00, London 08:30, NY PM 16:00 (a few NY PM at 13:00-13:15, the early flatten))

| book | UWTime trades | share of book trades | mean R at exit | median R | R>0 | net $ | mean MFE R before | mean MAE R before | once >= +0.5R | never in profit (MFE<0.1R) | move 15 min after (R) | median minutes in trade |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AS_MF1 | 746 | 38% | +0.30 | +0.24 | 68% | +534405 | +0.80 | -0.44 | 68% | 5% | +0.034 | 368 |
| AS_MF2 | 272 | 43% | +0.03 | +0.03 | 55% | +31710 | +0.39 | -0.35 | 36% | 18% | +0.034 | 255 |
| AS_MF3 | 431 | 17% | -0.15 | -0.12 | 35% | -228126 | +0.26 | -0.47 | 6% | 17% | +0.009 | 209 |
| AS_MF4 | 195 | 22% | -0.03 | -0.05 | 40% | -11429 | +0.27 | -0.33 | 10% | 24% | +0.012 | 52 |
| LO_MF1 | 312 | 29% | -0.20 | -0.16 | 26% | -893073 | +0.15 | -0.42 | 0% | 38% | -0.007 | 151 |
| LO_MF2 | 604 | 20% | +0.05 | +0.04 | 54% | +103654 | +0.53 | -0.48 | 54% | 9% | -0.015 | 83 |
| LO_MF3 | 779 | 44% | -0.12 | -0.07 | 38% | -435058 | +0.23 | -0.39 | 1% | 24% | +0.007 | 290 |
| NP_MF1 | 293 | 8% | -0.01 | -0.03 | 47% | -15093 | +0.49 | -0.56 | 52% | 9% | +0.049 | 16 |
| NP_MF3 | 255 | 23% | -0.18 | -0.17 | 27% | -243738 | +0.27 | -0.51 | 0% | 16% | +0.009 | 90 |
| NP_MF4 | 555 | 31% | -0.03 | -0.04 | 46% | -95388 | +0.41 | -0.48 | 38% | 13% | +0.014 | 56 |
| NY_MF1 | 735 | 45% | +0.03 | +0.04 | 54% | +357273 | +0.45 | -0.43 | 42% | 10% | +0.006 | 115 |
| NY_MF2 | 344 | 18% | +0.02 | -0.01 | 49% | +61237 | +0.50 | -0.50 | 49% | 13% | +0.006 | 52 |
| NY_MF3 | 355 | 36% | +0.02 | +0.03 | 53% | +63310 | +0.47 | -0.46 | 46% | 8% | +0.009 | 149 |
| NY_MF4 | 420 | 13% | -0.25 | -0.21 | 23% | -746903 | +0.17 | -0.51 | 0% | 28% | +0.002 | 45 |
| NY_MF5 | 542 | 21% | +0.08 | +0.08 | 58% | +110322 | +0.49 | -0.47 | 48% | 11% | +0.008 | 44 |
| NY_MF6 | 478 | 16% | -0.17 | -0.12 | 32% | -606756 | +0.17 | -0.47 | 0% | 29% | +0.010 | 41 |
| NY_MF7 | 400 | 46% | -0.06 | -0.02 | 47% | -70253 | +0.22 | -0.37 | 0% | 25% | +0.005 | 67 |
| NY_MF8 | 154 | 17% | -0.15 | -0.07 | 40% | -43963 | +0.27 | -0.53 | 0% | 15% | -0.014 | 67 |
| NY_MF9 | 189 | 28% | -0.08 | -0.02 | 46% | -60260 | +0.25 | -0.47 | 0% | 21% | +0.001 | 50 |

## NY AM: 3617 UWTime trades of 15745 (23%), net $-935992, mean R -0.045

**Give-back versus stuck (UWTime trades, by the best open R the trade reached before the time exit)**

| class | n | share | mean R at exit | mean MFE R | give-back (MFE - exit R) | mean MAE R | net $ | $/trade |
|---|---|---|---|---|---|---|---|---|
| once >= +0.5R (give-back) | 899 | 25% | +0.26 | +0.74 | +0.48 | -0.43 | +1662362 | +1849 |
| reached +0.1..+0.5R only | 2094 | 58% | -0.10 | +0.27 | +0.38 | -0.47 | -1523572 | -728 |
| never in profit (stuck, MFE<0.1R) | 624 | 17% | -0.28 | +0.06 | +0.34 | -0.48 | -1074783 | -1722 |

**Same split in units of the book target distance T0 (books with T0 < S0 can never reach +0.5R: the target takes them out first)**

| class | n | share | mean R at exit | mean MFE / T0 | net $ | $/trade |
|---|---|---|---|---|---|---|
| reached >= 50% of the way to target | 1703 | 47% | +0.11 | +0.74 | +1259089 | +739 |
| reached 10..50% of the way | 1595 | 44% | -0.16 | +0.30 | -1623714 | -1018 |
| never in profit (< 10% of target distance) | 319 | 9% | -0.30 | +0.05 | -571367 | -1791 |

**By open R at 30 / 60 / 90 minutes in (all trades still open then): how many end on the time exit and how they end**

| at | open R | trades open | end on UWTime | mean final R (all) | net $ (all) | mean final R of the UWTime ones | net $ of UWTime ones | end Target | end Stop |
|---|---|---|---|---|---|---|---|---|---|
| 30 min | <= -0.5R | 719 | 33% | -0.62 | -2888328 | -0.35 | -502437 | 10% | 56% |
| 30 min | -0.5..0 | 2368 | 55% | -0.18 | -2683437 | -0.14 | -1185097 | 22% | 23% |
| 30 min | 0..+0.5 | 2020 | 49% | +0.23 | +2875337 | +0.10 | +769862 | 40% | 9% |
| 30 min | >= +0.5R | 396 | 26% | +0.72 | +1887744 | +0.26 | +189166 | 70% | 4% |
| 60 min | <= -0.5R | 414 | 46% | -0.66 | -1856088 | -0.41 | -563332 | 3% | 50% |
| 60 min | -0.5..0 | 1262 | 74% | -0.20 | -1731326 | -0.18 | -1096941 | 12% | 13% |
| 60 min | 0..+0.5 | 1038 | 68% | +0.24 | +1807496 | +0.13 | +734926 | 28% | 4% |
| 60 min | >= +0.5R | 255 | 44% | +0.70 | +1421413 | +0.45 | +398092 | 53% | 2% |
| 90 min | <= -0.5R | 249 | 66% | -0.65 | -1184708 | -0.50 | -595362 | 1% | 33% |
| 90 min | -0.5..0 | 728 | 87% | -0.24 | -1189509 | -0.20 | -870768 | 4% | 9% |
| 90 min | 0..+0.5 | 622 | 81% | +0.24 | +1128467 | +0.19 | +762137 | 17% | 2% |
| 90 min | >= +0.5R | 187 | 56% | +0.70 | +1072327 | +0.49 | +430049 | 43% | 0% |

**Room: UWTime trades only. Upper bounds with hindsight (per trade the best alternative) versus one-setting rules (replayed on ALL trades; harm to other exit types counted)**

Baseline net $ of the UWTime trades: -935992. Upper bound A = change vs baseline if per trade the best of the 17 menu alternatives below, hindsight): +4414345. Upper bound B = change vs baseline if exit at the best open R the trade ever reached, perfect hindsight, minus 0.5 pt): +8908865.

| rule | change on UWTime trades $ | change on other trades $ | total change $ | trades touched | fit 60% $ | hold 40% $ |
|---|---|---|---|---|---|---|
| C90_0.25 | -227320 | +313275 | +85955 | 550 | +44260 | +41695 |
| C60_0.5 | -271475 | +294130 | +22655 | 414 | +16090 | +6565 |
| C90_0.5 | -135660 | +146420 | +10760 | 249 | +4940 | +5820 |
| B1.0_0.0 | +0 | -8480 | -8480 | 3 | +0 | -8480 |
| B1.0_0.25 | +0 | -11855 | -11855 | 4 | -5475 | -6380 |
| C60_0.25 | -590295 | +533840 | -56455 | 952 | -95120 | +38665 |
| C30_0.5 | -443100 | +262815 | -180285 | 719 | -54330 | -125955 |
| B0.75_0.0 | -27220 | -266660 | -293880 | 727 | +12270 | -306150 |
| C30_0.25 | -882420 | +544290 | -338130 | 1679 | -176700 | -161430 |
| E15 | -188680 | -175030 | -363710 | 3590 | -252330 | -111380 |
| B0.75_0.25 | +164135 | -605835 | -441700 | 1052 | -82360 | -359340 |
| E30 | -238685 | -313075 | -551760 | 3576 | -517355 | -34405 |
| E60 | -136610 | -575890 | -712500 | 3578 | -461455 | -251045 |
| B0.5_0.0 | -246935 | -476975 | -723910 | 1885 | -150865 | -573045 |
| E90 | -146845 | -703895 | -850740 | 3588 | -564435 | -286305 |
| B0.5_0.25 | +334790 | -1290405 | -955615 | 2721 | -380135 | -575480 |
| E120 | -99730 | -1176520 | -1276250 | 3685 | -833035 | -443215 |

## London: 1695 UWTime trades of 5799 (29%), net $-1224478, mean R -0.072

**Give-back versus stuck (UWTime trades, by the best open R the trade reached before the time exit)**

| class | n | share | mean R at exit | mean MFE R | give-back (MFE - exit R) | mean MAE R | net $ | $/trade |
|---|---|---|---|---|---|---|---|---|
| once >= +0.5R (give-back) | 332 | 20% | +0.22 | +0.76 | +0.54 | -0.45 | +267819 | +807 |
| reached +0.1..+0.5R only | 1006 | 59% | -0.10 | +0.27 | +0.37 | -0.40 | -726661 | -722 |
| never in profit (stuck, MFE<0.1R) | 357 | 21% | -0.28 | +0.05 | +0.33 | -0.47 | -765636 | -2145 |

**Same split in units of the book target distance T0 (books with T0 < S0 can never reach +0.5R: the target takes them out first)**

| class | n | share | mean R at exit | mean MFE / T0 | net $ | $/trade |
|---|---|---|---|---|---|---|
| reached >= 50% of the way to target | 782 | 46% | +0.09 | +0.76 | +115008 | +147 |
| reached 10..50% of the way | 725 | 43% | -0.18 | +0.29 | -993873 | -1371 |
| never in profit (< 10% of target distance) | 188 | 11% | -0.30 | +0.05 | -345613 | -1838 |

**By open R at 30 / 60 / 90 minutes in (all trades still open then): how many end on the time exit and how they end**

| at | open R | trades open | end on UWTime | mean final R (all) | net $ (all) | mean final R of the UWTime ones | net $ of UWTime ones | end Target | end Stop |
|---|---|---|---|---|---|---|---|---|---|
| 30 min | <= -0.5R | 215 | 17% | -0.57 | -640490 | -0.11 | -45874 | 16% | 67% |
| 30 min | -0.5..0 | 1712 | 43% | -0.15 | -1660288 | -0.15 | -935263 | 29% | 27% |
| 30 min | 0..+0.5 | 1590 | 34% | +0.20 | +1785837 | -0.01 | -151840 | 52% | 14% |
| 30 min | >= +0.5R | 202 | 13% | +0.71 | +514092 | +0.40 | +37327 | 76% | 11% |
| 60 min | <= -0.5R | 200 | 28% | -0.62 | -735448 | -0.34 | -153406 | 11% | 62% |
| 60 min | -0.5..0 | 1234 | 51% | -0.18 | -1421282 | -0.17 | -871567 | 24% | 25% |
| 60 min | 0..+0.5 | 1190 | 39% | +0.24 | +1449938 | +0.02 | -27895 | 51% | 10% |
| 60 min | >= +0.5R | 178 | 20% | +0.69 | +440825 | +0.32 | +39870 | 71% | 9% |
| 90 min | <= -0.5R | 188 | 27% | -0.62 | -688575 | -0.34 | -155089 | 12% | 61% |
| 90 min | -0.5..0 | 954 | 57% | -0.16 | -1086138 | -0.17 | -784276 | 23% | 20% |
| 90 min | 0..+0.5 | 906 | 46% | +0.23 | +1019683 | +0.03 | -1188 | 46% | 8% |
| 90 min | >= +0.5R | 117 | 15% | +0.70 | +294653 | +0.15 | +9425 | 76% | 9% |

**Room: UWTime trades only. Upper bounds with hindsight (per trade the best alternative) versus one-setting rules (replayed on ALL trades; harm to other exit types counted)**

Baseline net $ of the UWTime trades: -1224478. Upper bound A = change vs baseline if per trade the best of the 17 menu alternatives below, hindsight): +1784985. Upper bound B = change vs baseline if exit at the best open R the trade ever reached, perfect hindsight, minus 0.5 pt): +3835795.

| rule | change on UWTime trades $ | change on other trades $ | total change $ | trades touched | fit 60% $ | hold 40% $ |
|---|---|---|---|---|---|---|
| B1.0_0.25 | +3530 | +25940 | +29470 | 19 | +21345 | +8125 |
| B0.75_0.0 | -21735 | +36370 | +14635 | 338 | +51885 | -37250 |
| B1.0_0.0 | +830 | +11540 | +12370 | 19 | +13245 | -875 |
| B0.5_0.0 | -49030 | +56670 | +7640 | 827 | +87910 | -80270 |
| B0.75_0.25 | +32225 | -57025 | -24800 | 487 | +14790 | -39590 |
| C60_0.5 | -80765 | +49515 | -31250 | 200 | +42370 | -73620 |
| E15 | +142840 | -193365 | -50525 | 1718 | +17965 | -68490 |
| C90_0.5 | -99355 | +47885 | -51470 | 188 | -3520 | -47950 |
| C60_0.25 | -133595 | +65835 | -67760 | 606 | +68065 | -135825 |
| B0.5_0.25 | +85960 | -170280 | -84320 | 1188 | +9895 | -94215 |
| C90_0.25 | -165355 | +59325 | -106030 | 534 | -6800 | -99230 |
| C30_0.5 | -75805 | -47880 | -123685 | 215 | -65655 | -58030 |
| E30 | +153175 | -303445 | -150270 | 1705 | -7020 | -143250 |
| C30_0.25 | -141775 | -52320 | -194095 | 689 | -28555 | -165540 |
| E60 | +196580 | -450555 | -253975 | 1731 | -91580 | -162395 |
| E90 | +182240 | -572950 | -390710 | 1762 | -205715 | -184995 |
| E120 | +183825 | -625135 | -441310 | 1775 | -273985 | -167325 |

## NY PM: 1103 UWTime trades of 6445 (17%), net $-354219, mean R -0.061

**Give-back versus stuck (UWTime trades, by the best open R the trade reached before the time exit)**

| class | n | share | mean R at exit | mean MFE R | give-back (MFE - exit R) | mean MAE R | net $ | $/trade |
|---|---|---|---|---|---|---|---|---|
| once >= +0.5R (give-back) | 364 | 33% | +0.19 | +0.69 | +0.50 | -0.48 | +228983 | +629 |
| reached +0.1..+0.5R only | 603 | 55% | -0.15 | +0.30 | +0.45 | -0.51 | -398028 | -660 |
| never in profit (stuck, MFE<0.1R) | 136 | 12% | -0.34 | +0.06 | +0.40 | -0.57 | -185174 | -1362 |

**Same split in units of the book target distance T0 (books with T0 < S0 can never reach +0.5R: the target takes them out first)**

| class | n | share | mean R at exit | mean MFE / T0 | net $ | $/trade |
|---|---|---|---|---|---|---|
| reached >= 50% of the way to target | 512 | 46% | +0.11 | +0.71 | +151083 | +295 |
| reached 10..50% of the way | 482 | 44% | -0.19 | +0.30 | -373979 | -776 |
| never in profit (< 10% of target distance) | 109 | 10% | -0.33 | +0.06 | -131324 | -1205 |

**By open R at 30 / 60 / 90 minutes in (all trades still open then): how many end on the time exit and how they end**

| at | open R | trades open | end on UWTime | mean final R (all) | net $ (all) | mean final R of the UWTime ones | net $ of UWTime ones | end Target | end Stop |
|---|---|---|---|---|---|---|---|---|---|
| 30 min | <= -0.5R | 286 | 14% | -0.61 | -592787 | -0.24 | -47661 | 13% | 70% |
| 30 min | -0.5..0 | 1025 | 32% | -0.18 | -746083 | -0.15 | -245999 | 26% | 36% |
| 30 min | 0..+0.5 | 969 | 27% | +0.21 | +750923 | -0.00 | -25158 | 47% | 18% |
| 30 min | >= +0.5R | 212 | 8% | +0.69 | +445771 | +0.38 | +24628 | 66% | 5% |
| 60 min | <= -0.5R | 189 | 26% | -0.62 | -439126 | -0.23 | -54908 | 9% | 64% |
| 60 min | -0.5..0 | 540 | 46% | -0.22 | -495118 | -0.17 | -207972 | 21% | 31% |
| 60 min | 0..+0.5 | 462 | 33% | +0.26 | +488038 | +0.07 | +28861 | 46% | 13% |
| 60 min | >= +0.5R | 112 | 13% | +0.64 | +256499 | +0.19 | +11101 | 62% | 4% |
| 90 min | <= -0.5R | 116 | 32% | -0.62 | -320958 | -0.16 | -31258 | 5% | 61% |
| 90 min | -0.5..0 | 326 | 55% | -0.19 | -281891 | -0.18 | -154464 | 20% | 24% |
| 90 min | 0..+0.5 | 257 | 44% | +0.27 | +264129 | +0.01 | -14770 | 42% | 8% |
| 90 min | >= +0.5R | 78 | 15% | +0.54 | +170245 | +0.31 | +12224 | 54% | 6% |

**Room: UWTime trades only. Upper bounds with hindsight (per trade the best alternative) versus one-setting rules (replayed on ALL trades; harm to other exit types counted)**

Baseline net $ of the UWTime trades: -354219. Upper bound A = change vs baseline if per trade the best of the 17 menu alternatives below, hindsight): +891760. Upper bound B = change vs baseline if exit at the best open R the trade ever reached, perfect hindsight, minus 0.5 pt): +1905490.

| rule | change on UWTime trades $ | change on other trades $ | total change $ | trades touched | fit 60% $ | hold 40% $ |
|---|---|---|---|---|---|---|
| B1.0_0.0 | +0 | +1275 | +1275 | 1 | +0 | +1275 |
| B1.0_0.25 | +0 | -6770 | -6770 | 6 | -5635 | -1135 |
| C90_0.5 | -68285 | +50780 | -17505 | 116 | -20340 | +2835 |
| B0.75_0.0 | +3445 | -32962 | -29517 | 344 | -41260 | +11743 |
| C60_0.5 | -74865 | +35330 | -39535 | 189 | -16320 | -23215 |
| C90_0.25 | -117345 | +64030 | -53315 | 259 | -38140 | -15175 |
| B0.75_0.25 | +12470 | -75547 | -63077 | 587 | -79435 | +16358 |
| C30_0.5 | -54995 | -17825 | -72820 | 286 | -44875 | -27945 |
| C60_0.25 | -139415 | +58990 | -80425 | 446 | -28915 | -51510 |
| E60 | +57610 | -142190 | -84580 | 1133 | -14335 | -70245 |
| C30_0.25 | -125395 | +20420 | -104975 | 706 | -31995 | -72980 |
| E15 | +9650 | -122075 | -112425 | 1219 | -98500 | -13925 |
| E90 | +39880 | -195030 | -155150 | 1097 | -49900 | -105250 |
| B0.5_0.0 | +7515 | -182207 | -174692 | 1303 | -126760 | -47932 |
| E30 | -1360 | -176925 | -178285 | 1104 | -91805 | -86480 |
| E120 | +21125 | -211777 | -190652 | 1071 | -149235 | -41417 |
| B0.5_0.25 | +119465 | -392492 | -273027 | 1973 | -231130 | -41897 |

## Asia: 1644 UWTime trades of 6062 (27%), net $+326559, mean R +0.100

**Give-back versus stuck (UWTime trades, by the best open R the trade reached before the time exit)**

| class | n | share | mean R at exit | mean MFE R | give-back (MFE - exit R) | mean MAE R | net $ | $/trade |
|---|---|---|---|---|---|---|---|---|
| once >= +0.5R (give-back) | 650 | 40% | +0.47 | +0.97 | +0.51 | -0.38 | +777587 | +1196 |
| reached +0.1..+0.5R only | 784 | 48% | -0.11 | +0.29 | +0.40 | -0.44 | -274087 | -350 |
| never in profit (stuck, MFE<0.1R) | 210 | 13% | -0.26 | +0.05 | +0.31 | -0.44 | -176940 | -843 |

**Same split in units of the book target distance T0 (books with T0 < S0 can never reach +0.5R: the target takes them out first)**

| class | n | share | mean R at exit | mean MFE / T0 | net $ | $/trade |
|---|---|---|---|---|---|---|
| reached >= 50% of the way to target | 396 | 24% | +0.62 | +0.69 | +641859 | +1621 |
| reached 10..50% of the way | 995 | 61% | -0.02 | +0.29 | -112918 | -113 |
| never in profit (< 10% of target distance) | 253 | 15% | -0.26 | +0.05 | -202382 | -800 |

**By open R at 30 / 60 / 90 minutes in (all trades still open then): how many end on the time exit and how they end**

| at | open R | trades open | end on UWTime | mean final R (all) | net $ (all) | mean final R of the UWTime ones | net $ of UWTime ones | end Target | end Stop |
|---|---|---|---|---|---|---|---|---|---|
| 30 min | <= -0.5R | 295 | 13% | -0.60 | -535125 | -0.17 | -24047 | 2% | 65% |
| 30 min | -0.5..0 | 1647 | 42% | -0.15 | -688402 | +0.01 | -42306 | 5% | 30% |
| 30 min | 0..+0.5 | 1455 | 42% | +0.27 | +1202040 | +0.21 | +323524 | 12% | 15% |
| 30 min | >= +0.5R | 286 | 23% | +0.86 | +656416 | +0.59 | +94031 | 43% | 15% |
| 60 min | <= -0.5R | 232 | 20% | -0.61 | -432405 | -0.02 | -10781 | 0% | 63% |
| 60 min | -0.5..0 | 1164 | 51% | -0.15 | -485868 | +0.00 | -44189 | 4% | 27% |
| 60 min | 0..+0.5 | 1068 | 51% | +0.22 | +726536 | +0.18 | +242661 | 10% | 14% |
| 60 min | >= +0.5R | 283 | 30% | +0.96 | +739292 | +0.73 | +140261 | 42% | 11% |
| 90 min | <= -0.5R | 214 | 23% | -0.68 | -425729 | -0.13 | -24337 | 0% | 66% |
| 90 min | -0.5..0 | 871 | 58% | -0.15 | -361564 | -0.03 | -91293 | 2% | 23% |
| 90 min | 0..+0.5 | 838 | 61% | +0.21 | +538934 | +0.20 | +256395 | 7% | 11% |
| 90 min | >= +0.5R | 288 | 37% | +0.99 | +745172 | +0.73 | +176338 | 40% | 9% |

**Room: UWTime trades only. Upper bounds with hindsight (per trade the best alternative) versus one-setting rules (replayed on ALL trades; harm to other exit types counted)**

Baseline net $ of the UWTime trades: +326559. Upper bound A = change vs baseline if per trade the best of the 17 menu alternatives below, hindsight): +916730. Upper bound B = change vs baseline if exit at the best open R the trade ever reached, perfect hindsight, minus 0.5 pt): +2009545.

| rule | change on UWTime trades $ | change on other trades $ | total change $ | trades touched | fit 60% $ | hold 40% $ |
|---|---|---|---|---|---|---|
| B1.0_0.0 | -60115 | +78970 | +18855 | 201 | -12620 | +31475 |
| C90_0.5 | -65420 | +73180 | +7760 | 214 | -6153 | +13913 |
| E15 | -35275 | +28131 | -7143 | 1612 | -16314 | +9170 |
| B1.0_0.25 | -55155 | +36975 | -18180 | 307 | -18600 | +420 |
| C60_0.5 | -76645 | +35933 | -40712 | 232 | -22043 | -18669 |
| C90_0.25 | -169780 | +110039 | -59741 | 557 | -60723 | +982 |
| C30_0.5 | -41205 | -21206 | -62411 | 295 | -9833 | -52578 |
| B0.75_0.0 | -108885 | +23009 | -85876 | 412 | -49530 | -36346 |
| C60_0.25 | -196145 | +104350 | -91795 | 665 | -37118 | -54677 |
| E30 | -121415 | -37497 | -158912 | 1640 | -141347 | -17565 |
| C30_0.25 | -186250 | +21533 | -164717 | 846 | -82789 | -81929 |
| B0.75_0.25 | -85945 | -91026 | -176971 | 599 | -100025 | -76946 |
| E60 | -129940 | -67374 | -197314 | 1668 | -173417 | -23897 |
| E90 | -135585 | -87608 | -223193 | 1680 | -196887 | -26306 |
| B0.5_0.0 | -184020 | -55101 | -239121 | 1027 | -119568 | -119553 |
| B0.5_0.25 | -104555 | -193231 | -297786 | 1526 | -144968 | -152818 |
| E120 | -161265 | -147009 | -308274 | 1651 | -227698 | -80575 |

