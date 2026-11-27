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

