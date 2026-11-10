# DS3_REDO_R9_STOPEXIT - stop-exit and cut-exit mechanics on the state base (T-STACK-REDO R9)  [FIRST-ORDER SCREEN, tape microsim; PRE-PROOF until entry match >= .85; no PASS claims]
Generated 2026-11-10 04:29 UTC (elapsed 8 s). Base S1b-COMB 21,135 trades (43 months, ROLL-EXCL weights), data end 2026-11-05, windows as of 2026-11-09. Code: code/th_stack_r9 (r9_tape.py microsim, r9_run.py driver, r9_score.py, fo_lib.py).
Registry: /mnt/l2/l2vast/_th_joint/layers/stopexit/topK.json. Cell ledger: /mnt/l2/l2vast/_th_stack/r9/cells_r9.parquet.

## 0. What was measured, how, and the limits
- Universe: 3853 stop-family exits in the base (Stop / StopJoin / StopJoinFallback, 43 months); tape reproduction found a touch for 3735; **3350 (87%) reproduce the engine exit to the tick, name and time** ("matched"); first-order deltas use matched trades only (unmatched keep their engine fill, so every delta below is a LOWER bound on the policy effect).
- Method: each stop exit is re-simulated on the owned NQ tape (print stream + 100-ms 10-level book, code/hist_pipe day files) with the replica engine mechanics (sim.py: walk(), pump_stop_exit, match_resting, request_exit; LAT_BOOK .175, cancel .5, ack .5, market fill 1.0 s after request). The stop level is recovered per trade (the live stop of a 70/30 entry keeps the FIRST-fill level; the trade log has only the final average): the offset is the one that reproduces the engine fill.
- **Queue model (stated):** the join order rests at the touch-print best price (ask for a long exit), ack 0.5 s, queue ahead = displayed best-level size at the touch print, reduced only by prints AT the price, a print THROUGH the price fills all; no cancels ahead credited, no price-time loss; deadline evaluated on the first print after w s. Pessimistic row J3_i0_c20_q2 doubles the queue.
- Policies: NAT = native stop-market at the stop (no latency); STRAT0_c = strategy-worked market at the touch (native moves to catastrophe offset c); J<w>_i<0|1>_c<c> = JoinThenMarket w s, join at the touch best (i0) or 1 tick inside (i1), catastrophe c pts. wait 0 / native market = NAT (zero latency) and STRAT0 (live request path, 1.0 s).
- **Mode discrepancy (flag for the lead):** the replica engine (sim.JOIN_BOOKS, used to build the S1b base) has K7, M7, U7, P7 on JoinThenMarket and H7, A7, O7 Native; GATE0_ANSWERS s3 says K7 and H7 join, P7/U7/M7/A7/O7 Native; DS7.cs SetDefaults sets StStopExitMode = HmStopExitMode = JoinThenMarket and applies the ST value to the pb/pe/u5/p5 books after the Native line (L569-574). The frozen live week has ZERO stop exits (187 trades: 31+28+13+7 targets, cuts, 1 BookLock), so the live mode per book cannot be read from it. Both assignments are scored: REF_ENG (base itself) and REF_G0 (row below).
- Calibration against live: the live stop fills available are the old-stack figures in DECISION_PACK_20261106 (native 1.28 pt over 8 stops, join 2.45 pt over 21 stops, p_fallback 0.57); the frozen week has no stop to compare. Engine-vs-tape numbers in section 1.
- Held-out frozen live week: n/a for stops (0 stop exits); the 3 cut exits type rows are in section 6.

## 0b. Stop-exit mode per book: engine vs live code vs Gate0 (one line per book)
| book | our engine (S1b base) | DS7.cs v1.4 code (panel default) | GATE0 s3 |
|---|---|---|---|
| K7 | JoinThenMarket | JoinThenMarket (ST value) | JoinThenMarket |
| M7 | JoinThenMarket | JoinThenMarket (ST value) | Native |
| U7 | JoinThenMarket | JoinThenMarket (ST value) | Native |
| P7 | JoinThenMarket | JoinThenMarket (ST value) | Native |
| H7 | Native | JoinThenMarket (HM value) | JoinThenMarket |
| A7 | Native | JoinThenMarket (ST value) | Native |
| O7 | Native | Native (hard-coded) | Native |
The code gives K7, M7, U7, P7, A7 one shared ST value and H7 its own HM value, so neither the engine split nor the Gate0 split is reachable from the code unless the panel sets ST/HM differently from the defaults; the installed panel values are the open input. Exact runs of the three candidate settings vs the as-run base (L6M): REF_R9_STOP_CODE / _G0 / _NAT in the SZ queue (tier 1); result table below when complete.
Live evidence (frozen file, 187 trades): 0 StopJoin / StopJoinFallback exits; 2 stop exits, K7 -83.00 and M7 -80.75 pts-equivalent at the native 80 level during the Tuesday stall (no join involved); the engine run of that week produced join exits (count per lead: 12). So the frozen week neither confirms nor refutes a join mode; the engine-vs-live difference there is the stall, not the join.

## 1. Calibration - what the engine and the tape say a stop costs
**Sign: positive = fill WORSE than the stop level; negative = fill BETTER than the level.** The engine's fills of the base are negative on average (engine native stops 1.9 pt BETTER than the level: a zero-latency walk of the pre-print 100-ms book), live native stops were 1.28 pt WORSE (8 stops, old stack) and join 2.45 pt worse (21 stops): the engine basis is optimistic by roughly 3 pt per native stop. NAT +.175 s = the same market order with the engine book latency (LAT_BOOK), the first realistic native basis (+0.7 pt, still below live 1.28). Mean adverse cost eng = engine fill in the base; sim = tape microsim of the same mechanics; NAT / STRAT0 / J3 = alternative on the same touch (all touched stops).
| book | mode | n stops | matched | eng cost | eng cost matched | sim ref cost | sim fallback share | engine fallback share | NAT (0 lat) | NAT +.175 s | STRAT0 | J3 i0 | J3 live-cal |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | JTM3 | 1697 | 1598 | 0.11 | 0.04 | 0.22 | 0.38 | 0.38 | -1.49 | 1.07 | 0.17 | 0.22 | 1.87 |
| M7 | JTM3 | 411 | 389 | -0.53 | -0.63 | -0.47 | 0.31 | 0.31 | -2.60 | 1.05 | 0.06 | -0.47 | 1.65 |
| U7 | JTM3 | 521 | 379 | -1.32 | -0.53 | -0.17 | 0.39 | 0.41 | -2.17 | 0.76 | 0.22 | -0.17 | 1.74 |
| P7 | JTM3 | 328 | 249 | -2.12 | -1.62 | -0.64 | 0.32 | 0.36 | -4.55 | 4.71 | -0.53 | -0.64 | 1.62 |
| H7 | Native | 294 | 251 | -2.29 | -1.46 | -1.60 |  |  | -1.60 | 0.28 | 0.27 | 0.34 | 2.10 |
| A7 | Native | 333 | 333 | -1.35 | -1.35 | -1.35 |  |  | -1.35 | 0.81 | 0.07 | -0.00 | 1.76 |
| O7 | Native | 151 | 151 | -2.19 | -2.19 | -2.19 |  |  | -2.19 | 0.60 | 0.59 | 0.56 | 2.02 |

Pooled: engine join-book stops cost -0.48 pt (fallback share 0.37); engine native-book stops cost -1.87 pt. Live reference (old stack): join 2.45 pt (p_fallback 0.57), native 1.28 pt. Same-touch alternatives pooled over ALL books: NAT -2.00, STRAT0 0.12, J1 0.09, J3 0.02, J5 -0.03, J10 -0.07 pt.

## 2. Per-fill cost by book x session (pts past the stop; n = touched stops)
| book | session | n | NAT | STRAT0 c20 | J1 | J3 (live join) | J5 | J10 | J3 inside-1 | J3 q2 | $/stop NAT vs eng | $/stop J3 vs eng |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | asia | 530 | -1.15 | 0.43 | 0.39 | 0.35 | 0.36 | 0.37 | 0.28 | 0.37 | 38 | 0 |
| K7 | london | 424 | -2.26 | -0.09 | -0.09 | -0.13 | -0.18 | -0.28 | -0.21 | -0.12 | 48 | 0 |
| K7 | nyam | 413 | -1.19 | 0.44 | 0.58 | 0.54 | 0.52 | 0.40 | 0.18 | 0.58 | 36 | 0 |
| K7 | nypm | 330 | -1.43 | -0.23 | 0.01 | 0.04 | 0.08 | 0.02 | -0.29 | 0.05 | 35 | 0 |
| M7 | london | 206 | -3.98 | -0.63 | -1.79 | -1.71 | -1.57 | -1.63 | -1.77 | -1.57 | 55 | 0 |
| M7 | nyam | 205 | -1.22 | 0.76 | 1.10 | 0.78 | 0.52 | 0.59 | 0.11 | 0.77 | 36 | 0 |
| U7 | asia | 251 | -1.48 | 0.10 | 0.06 | -0.00 | 0.05 | 0.16 | -0.10 | 0.03 | 68 | 0 |
| U7 | london | 270 | -2.82 | 0.33 | 0.07 | -0.33 | -0.42 | -0.43 | -1.02 | -0.23 | 95 | 0 |
| P7 | asia | 132 | -3.91 | -1.23 | -1.28 | -1.23 | -1.08 | -0.93 | -0.13 | -1.21 | 198 | 0 |
| P7 | london | 111 | -7.82 | -1.03 | -1.31 | -1.29 | -1.33 | -1.66 | -3.39 | -1.29 | 524 | 0 |
| P7 | nyam | 85 | -1.28 | 1.23 | 1.36 | 1.13 | 0.95 | 0.96 | -0.49 | 1.14 | 120 | 0 |
| H7 | asia | 155 | -2.13 | -0.06 | 0.25 | 0.34 | 0.26 | 0.37 | 0.11 | 0.36 | 0 | -88 |
| H7 | nyam | 139 | -1.00 | 0.64 | 0.47 | 0.35 | 0.29 | 0.38 | 0.13 | 0.40 | 0 | -26 |
| A7 | asia | 333 | -1.35 | 0.07 | 0.11 | -0.00 | -0.14 | -0.18 | -0.15 | 0.02 | 0 | -27 |
| O7 | nyam | 151 | -2.19 | 0.59 | 0.76 | 0.56 | 0.18 | -0.17 | 0.18 | 0.56 | 0 | -55 |

## 3. Catastrophe offset (join books, wait 3 s): the native stop at S -/+ c only matters when price runs c pts before the exit completes
| c (pts) | stops where the catastrophe fires first | mean cost pts (join books) | $/week d mean (ALL join books, L6M) | L6M maxDD cut % |
|---|---|---|---|---|
| 10 | 234 | -0.35 | -10 | 0.3 |
| 20 | 114 | -0.04 | -192 | -0.3 |
| 30 | 79 | 0.01 | -134 | -2.5 |
| 40 | 55 | 0.17 | -117 | -0.5 |

## 4. Stack-wide policy (the same policy on every book that stops) - ranked by key = mean(eq-mean maxDD cut L6M, L3M, L1M)
**4a. LIVE-CALIBRATED basis (primary):** native = +1.28 pt, join fill = +0.5 pt, fallback = +3.9 pt (+ the tape drift of the longer wait), reference per book = engine assignment (join books JLIVE_3, others NATLIVE). Break-even: a native stop must cost <= 1.79 pt (mean live-calibrated J3 cost on the join-book stops) for native to beat the 3-s join; live-measured native is 1.28 pt.
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9S_ALL_NATLIVE | ALL | NATLIVE | 2615 | 1849 | 425 | 1.6 | 3.3/3.3/4.4 | 0.2 | 3.6 | 1.9 | 0.13/0.39 | 3.7 |
| R9S_ALL_JLIVE_10 | ALL | JLIVE_10 | 1658 | -6226 | 49 | 0.3 | 0.5/0.5/0.9 | -0.7 | 2.2 | -0.3 | 0.14/0.86 | 0.6 |
| R9S_ALL_JLIVE_5 | ALL | JLIVE_5 | 1603 | -9971 | -70 | 0.3 | -0.0/-0.0/0.3 | -1.1 | 2.1 | -0.6 | 0.09/1.00 | 0.1 |
| R9S_ALL_JLIVE_3 | ALL | JLIVE_3 | 735 | -13107 | -75 | -0.3 | -0.6/-0.6/-0.7 | -0.1 | 0.1 | -1.1 | 0.38/0.66 | -0.6 |
| R9S_ALL_JLIVE_1 | ALL | JLIVE_1 | 1933 | -17050 | -113 | -0.4 | -0.9/-0.9/-0.8 | -1.5 | -0.6 | -1.4 | 0.39/1.00 | -0.9 |

**4b. ENGINE basis (secondary, optimistic native fills; deltas vs the engine fill in the base):**
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9S_ALL_NAT | ALL | NAT | 2372 | 192245 | 1373 | 5.3 | 9.9/9.9/9.8 | 7.4 | 9.5 | 19.0 | 0.18/0.49 | 9.9 |
| R9S_ALL_STRAT0_c10 | ALL | STRAT0_c10 | 3101 | -9770 | -97 | 2.2 | 1.9/1.9/1.8 | -2.0 | 0.3 | 1.1 | 0.06/0.89 | 1.9 |
| R9S_ALL_J5_i1_c10 | ALL | J5_i1_c10 | 3127 | 21470 | 104 | 0.4 | 0.9/0.9/0.8 | 0.8 | 1.4 | 1.6 | 0.32/0.59 | 0.8 |
| R9S_ALL_J10_i1_c10 | ALL | J10_i1_c10 | 3168 | 25040 | 124 | 0.1 | 0.7/0.7/0.6 | 1.1 | 2.0 | 1.9 | 0.56/0.62 | 0.6 |
| R9S_ALL_J10_i0_c10 | ALL | J10_i0_c10 | 1671 | 11930 | 94 | 0.3 | 0.7/0.7/0.5 | 1.4 | 0.4 | 3.0 | 0.22/0.51 | 0.6 |
| R9S_ALL_J10_i1_c20 | ALL | J10_i1_c20 | 3121 | 6020 | -37 | 0.7 | 0.5/0.5/0.8 | -0.3 | 2.8 | -0.0 | 0.13/0.87 | 0.6 |
| R9S_ALL_J10_i0_c40 | ALL | J10_i0_c40 | 1665 | -35125 | 6 | 0.1 | 0.1/0.1/1.5 | -4.5 | 0.3 | -0.9 | 0.17/1.00 | 0.6 |
| R9S_ALL_J5_i0_c10 | ALL | J5_i0_c10 | 1622 | 6090 | 23 | 0.5 | 0.6/0.6/0.5 | 1.1 | 0.1 | 2.2 | 0.23/0.46 | 0.5 |
| R9S_ALL_J10_i1_c30 | ALL | J10_i1_c30 | 3184 | 170 | 39 | -0.2 | 0.0/0.0/1.5 | 0.1 | 2.6 | -0.1 | 0.31/0.64 | 0.5 |
| R9S_ALL_J3_i1_c10 | ALL | J3_i1_c10 | 2620 | 20015 | 73 | 0.2 | 0.5/0.5/0.4 | 1.2 | 1.2 | 1.2 | 0.37/0.57 | 0.5 |
| R9S_ALL_J3_i0_c10 | ALL | J3_i0_c10 | 827 | 3195 | -10 | 0.3 | 0.3/0.3/0.2 | 1.3 | -0.3 | 1.8 | 0.20/0.47 | 0.2 |
| R9S_ALL_J5_i1_c20 | ALL | J5_i1_c20 | 3075 | 660 | -79 | 0.6 | 0.2/0.2/0.1 | -0.9 | 2.0 | -0.7 | 0.14/0.93 | 0.2 |

Reference row REF_G0 (Gate0 assignment, engine basis; exact-pending):
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF_G0_assignment | ALL | G0 | 1149 | 115315 | 909 | 3.9 | 7.6/7.6/7.5 | 5.3 | 5.7 | 12.4 | 0.17/0.60 | 7.6 |

Worst stack-wide cells (engine basis):
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9S_ALL_NAT175 | ALL | NAT175 | 3165 | -268020 | -540 | -1.1 | -3.4/-3.4/-1.9 | -4.4 | -1.3 | -10.5 | 0.07/0.30 | -2.9 |
| R9S_ALL_J3_i0_c30 | ALL | J3_i0_c30 | 743 | -38660 | -134 | -2.5 | -3.0/-3.0/-0.8 | 0.4 | -1.3 | -3.3 | 0.72/0.19 | -2.3 |
| R9S_ALL_J1_i0_c30 | ALL | J1_i0_c30 | 1911 | -51315 | -265 | -1.8 | -2.8/-2.8/-1.1 | -3.5 | -2.0 | -3.2 | 0.55/0.96 | -2.2 |
| R9S_ALL_J5_i0_c30 | ALL | J5_i0_c30 | 1601 | -34375 | -61 | -2.4 | -2.7/-2.7/0.7 | -0.2 | 0.3 | -2.3 | 0.75/0.42 | -1.5 |

## 5. Per-book best policy (single book changed, the rest stays at the live reference)
| book | best policy by key | dmean L6M $/wk | L6M cut % | eq cut L6M | PRE cut / dmean | WF2w beat % | prior label |
|---|---|---|---|---|---|---|---|
| K7 | NATLIVE | 169 | 0.5 | 1.2 | -0.1 / 124 | 41 | OK-PRIOR |
| M7 | NATLIVE | 35 | 0.1 | 0.2 | -1.1 / 37 | 28 | OK-PRIOR |
| U7 | NATLIVE | 97 | -0.0 | 0.4 | 0.1 / 30 | 38 | OK-PRIOR |
| P7 | NATLIVE | 215 | 0.6 | 1.5 | 1.3 / 83 | 31 | OK-PRIOR |
| H7 | JLIVE_10 | 8 | 0.0 | 0.1 | 0.0 / -60 | 43 | OK-PRIOR |
| A7 | NATLIVE | 0 | 0.0 | 0.0 | 0.0 / 0 | 0 | OK-PRIOR |
| O7 | JLIVE_10 | -0 | 0.0 | -0.0 | 0.0 / 1 | 11 | OK-PRIOR |

## 6. Cut exit (StateCut): market vs join 1 / 2 / 3 s (tape; market baseline = walk at cut + 1.0 s request path; delta applied to the engine StateCut fill)
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_ALL_CJ1_i1 | ALL | CJ1_i1 | 5759 | 22905 | 318 | -0.7 | 0.7/0.7/0.6 | 0.5 | 1.3 | 2.9 | 0.90/0.50 | 0.7 |
| R9C_ALL_CJ2_i1 | ALL | CJ2_i1 | 5759 | 22905 | 318 | -0.7 | 0.7/0.7/0.6 | 0.5 | 1.3 | 2.9 | 0.94/0.50 | 0.7 |
| R9C_ALL_CJ3_i1 | ALL | CJ3_i1 | 5759 | 22905 | 318 | -0.7 | 0.7/0.7/0.6 | 0.5 | 1.3 | 2.9 | 0.88/0.48 | 0.7 |
| R9C_ALL_CJ1_i0 | ALL | CJ1_i0 | 5604 | 11855 | 214 | -0.9 | 0.1/0.1/-0.0 | 0.0 | 0.6 | 1.5 | 0.93/0.72 | 0.0 |
| R9C_ALL_CJ2_i0 | ALL | CJ2_i0 | 5604 | 11855 | 214 | -0.9 | 0.1/0.1/-0.0 | 0.0 | 0.6 | 1.5 | 0.92/0.74 | 0.0 |
| R9C_ALL_CJ3_i0 | ALL | CJ3_i0 | 5604 | 11855 | 214 | -0.9 | 0.1/0.1/-0.0 | 0.0 | 0.6 | 1.5 | 0.90/0.79 | 0.0 |

Per book (best join variant by key):
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_K7_CJ1_i0 | K7 | CJ1_i0 | 1451 | 1660 | 18 | 0.0 | 0.1/0.1/0.1 | 0.0 | 0.0 | 0.6 | 0.40/0.53 | 0.1 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_M7_CJ1_i1 | M7 | CJ1_i1 | 1807 | 4535 | 44 | 0.0 | 0.2/0.2/0.6 | 0.4 | 0.2 | 0.8 | 0.54/0.01 | 0.4 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_U7_CJ1_i1 | U7 | CJ1_i1 | 106 | 0 | -18 | -0.2 | -0.2/-0.2/-0.4 | 0.1 | -0.0 | -0.4 | 0.88/0.22 | -0.3 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_P7_CJ1_i1 | P7 | CJ1_i1 | 1929 | 14300 | 202 | -0.7 | 0.1/0.1/-0.1 | -0.1 | 1.2 | 1.6 | 0.89/0.81 | 0.0 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_H7_CJ1_i1 | H7 | CJ1_i1 | 199 | 1155 | 13 | -0.1 | -0.0/-0.0/0.0 | 0.0 | -0.0 | 0.3 | 0.66/0.20 | -0.0 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_A7_CJ1_i1 | A7 | CJ1_i1 | 84 | 530 | 2 | -0.0 | 0.0/0.0/-0.1 | -0.0 | 0.0 | 0.0 | 0.57/0.75 | -0.0 |
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9C_O7_CJ1_i0 | O7 | CJ1_i0 | 151 | 125 | 6 | 0.0 | 0.1/0.1/0.0 | -0.0 | -0.0 | 0.0 | 0.12/0.81 | 0.1 |

Mean $ per cut (matched = all cuts) of join vs market, by session (ALL books): asia: CJ1_i0 6 / CJ3_i0 6; london: CJ1_i0 2 / CJ3_i0 2; nyam: CJ1_i0 -3 / CJ3_i0 -3; nypm: CJ1_i0 2 / CJ3_i0 2
Cut-exit join fill share: CJ1_i0 0.10, CJ2_i0 0.10, CJ3_i0 0.10 (fallback = market after the wait; the price path after a cut signal runs against the position, so a join that waits pays the drift).

## 6b. EXACT engine rows (SZ queue, hooks exit_hooks.py; identity test REF_R9_ID on 202610: 823 trades, net 45,346.92, all columns identical to base_b/S1-COMB: PASSED)
Exact L6M (202605-202610) vs the as-run base (engine assignment K7 M7 U7 P7 join, H7 A7 O7 native), ENGINE fill basis (native fills optimistic, see section 1):
| set | setting | months | L6M maxDD cut % | L6M d mean $/wk | w20 cut % | eq-mean cut % | L3M cut % | L1M cut % |
|---|---|---|---|---|---|---|---|---|
Reading: moving M7/U7/P7 (and A7/O7 as listed) to Native on the engine basis gains because the engine fills a native stop 1.9 pt BETTER than the level (live: 1.28 pt worse). The gain is a fill-basis artefact until the native fill is re-based: at +1.28 pt the same exact change is worth about the first-order live-calibrated row NATLIVE (section 4a), i.e. a few hundred $/wk, inside noise.

## 7. Family null, procedure walk-forward, old-vs-new
- Family max-stat over all 400 R9 cells (own-draw p beside it): best-key cell R9S_ALL_NAT p_own L6M 0.18 / PRE 0.49, p_family 1.00.
- Bi-weekly re-pick WF of the whole R9 grid (train 26 weeks -> next 2 weeks, purged, lowest trailing maxDD else live): OOS maxDD cut 1.4%, d mean +1028 $/wk, beat live in 78% of 74 refit periods (74 switches away from live).
- Old-vs-new: DECISION_PACK_20261106 row 5 (old engine, 8 native / 21 join stops): native on all books +$3,097/week (PE +$1,711), +$0.6k if native costs 2.20. New (state base, tape): NAT on all books +1373 $/wk L6M, +1029 $/wk pooled over 43 months (first-order, matched trades only); join 3 s -> native shifts the stop cost by 2.02 pt per stop. Base-change proof: no previously published cell is reproduced to the dollar (the stop book moved from the optimistic old fills to the tape walk).

## 8. Verdict (screen) and what goes to the joint stage
Best 8 cells overall by key:
| cell | scope | policy | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq-mean cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R9S_ALL_NAT | ALL | NAT | 2372 | 192245 | 1373 | 5.3 | 9.9/9.9/9.8 | 7.4 | 9.5 | 19.0 | 0.18/0.49 | 9.9 |
| R9S_P7_NAT | P7 | NAT | 229 | 78790 | 570 | 2.6 | 5.0/5.0/4.9 | 4.0 | 3.2 | 7.8 | 0.25/0.63 | 5.0 |
| R9S_ALL_NATLIVE | ALL | NATLIVE | 2615 | 1849 | 425 | 1.6 | 3.3/3.3/4.4 | 0.2 | 3.6 | 1.9 | 0.13/0.39 | 3.7 |
| R9S_K7_NAT | K7 | NAT | 1455 | 63105 | 412 | 1.5 | 3.0/3.0/2.9 | 2.1 | 3.4 | 6.5 | 0.03/0.10 | 3.0 |
| R9S_P7_J10_i0_c40 | P7 | J10_i0_c40 | 93 | 9370 | 200 | 1.0 | 1.8/1.8/2.9 | -2.4 | 1.3 | 0.3 | 0.11/0.98 | 2.2 |
| R9S_P7_J10_i1_c30 | P7 | J10_i1_c30 | 239 | 12330 | 151 | 0.9 | 1.5/1.5/2.6 | -1.5 | 2.5 | 1.2 | 0.13/0.90 | 1.9 |
| R9S_ALL_STRAT0_c10 | ALL | STRAT0_c10 | 3101 | -9770 | -97 | 2.2 | 1.9/1.9/1.8 | -2.0 | 0.3 | 1.1 | 0.06/0.89 | 1.9 |
| R9S_P7_J10_i1_c20 | P7 | J10_i1_c20 | 224 | 13405 | 141 | 0.9 | 1.5/1.5/2.5 | -0.4 | 2.5 | 2.0 | 0.05/0.90 | 1.8 |

The live setting stays unless an exact-engine row beats it with the walk-forward; the screen only nominates candidates. Join waits >= 5 s and inside-1 joins are the questions that can move the stop cost; the tape queue model makes the first-order sign trustworthy, the size is an upper/lower bound as stated in s0.

## REFIT 2026-11-22
Trailing 26 weeks to the data end, drawdown first: pick = **R9S_ALL_NAT** (live retained: False). Top 5:
| cell               |   maxdd |   worst20 |   ulcer |    mean | live   | prior         |
|:-------------------|--------:|----------:|--------:|--------:|:-------|:--------------|
| R9S_ALL_NAT        | 75685.5 |    161129 | 31559.4 | 25710.1 | False  | PRIOR-UNKNOWN |
| R9S_ALL_STRAT0_c10 | 78115.5 |    131774 | 33666.6 | 24094.4 | False  | PRIOR-UNKNOWN |
| R9S_ALL_NATLIVE    | 78594.7 |    133370 | 33786.4 | 24262.9 | False  | PRIOR-UNKNOWN |
| R9S_ALL_J10_i1_c20 | 79377.3 |    129819 | 33863.6 | 24452.7 | False  | PRIOR-UNKNOWN |
| R9S_P7_NATLIVE     | 79438.1 |    127499 | 34241.9 | 24074.5 | False  | PRIOR-UNKNOWN |

## EXACT rows (appended)
Exact engine, SZ queue (hooks netting_hooks.py / exit_hooks.py or M_R11 table mode), cuts vs the exact S1b-COMB list (all weeks, ROLL-EXCL); a window is reported only when all its months are done. Months done per set: R9_J5_i1_c10 0, R9_J10_i1_c10 0, R9_J10_i0_c10 0, R9_STRAT0_c10 0
no exact month finished yet (queue tier of R10_/R11_/R9_ prefixes pending).
