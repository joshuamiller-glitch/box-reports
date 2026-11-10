# DS3_REDO_R10_NETTING - direction conflict / netting on the state base (T-STACK-REDO R10)  [FIRST-ORDER SCREEN; PRE-PROOF until entry match >= .85; no PASS claims]
Generated 2026-11-10 04:29 UTC (elapsed 8 s). Base S1b-COMB 21,135 trades (43 months, ROLL-EXCL), windows as of 2026-11-09. Code code/th_stack_r9/r10_score.py (+ fo_lib.py). Registry /mnt/l2/l2vast/_th_joint/layers/netting/topK.json.

## 0. Definition and limits
- Event = trade B whose signal second falls while another book A holds the OPPOSITE side (A.entry <= B.signal < A.exit; one position per book as live). Policies on the newer signal B vs the older open book(s) A: BOTH (live, reference) / SKIP B / HALF B / SKIPS (skip B only when B is the smaller side) / NET (older book exits min(lots) at market at signal+1 s, mid -/+ 0.80 pt; B enters lots_B - m) / FLIP (older book(s) exit fully at market = the opposite-flip exit, currently OFF live; B unchanged).
- Deltas are per-trade first-order dollars on the base; the later trades of a changed book (locks, re-entries, the A06/B02/StackCut interactions) are not re-simulated: SCREEN ONLY. SKIP / HALF are lot-multiplier tables (exact-capable in table mode); NET / FLIP need engine hooks (code/th_stack_r9/netting_hooks.py, exact queue prefix R10_).
- Mid path: 1-s NQ mid (state days). Ranking key = mean(eq-mean maxDD cut L6M, L3M, L1M); placebo = the cell deltas permuted among the event trades of the same book x session (B=100); family max-stat over all R10 cells.

## 1. How often it happens
4560 of 21135 trades (21.6%) are signalled while an opposite book is open: 24.28 per week. Older-book lots at risk: mean 4.1; newer lots: mean 1.9; events with >1 opposite open book: 1927.

By older book x newer book (events, mean $ of B, mean $ of A over its whole trade, share where B wins, share where A wins):
| older A | newer B | events | per week | B mean $ | A mean $ | B>0 | A>0 | B and A both lose |
|---|---|---|---|---|---|---|---|---|
| P7 | K7 | 647 | 3.45 | 22 | -1699 | 0.45 | 0.28 | 0.27 |
| K7 | P7 | 608 | 3.24 | 89 | -516 | 0.48 | 0.32 | 0.22 |
| K7 | M7 | 494 | 2.63 | -33 | -1451 | 0.39 | 0.24 | 0.36 |
| P7 | M7 | 374 | 1.99 | 38 | -2230 | 0.43 | 0.27 | 0.30 |
| P7 | U7 | 281 | 1.50 | 245 | -2247 | 0.53 | 0.28 | 0.20 |
| M7 | K7 | 235 | 1.25 | 59 | -1623 | 0.50 | 0.21 | 0.29 |
| U7 | K7 | 196 | 1.04 | 117 | -2190 | 0.52 | 0.26 | 0.23 |
| K7 | U7 | 166 | 0.88 | 17 | -1873 | 0.46 | 0.27 | 0.27 |
| U7 | M7 | 155 | 0.83 | 55 | -1489 | 0.43 | 0.28 | 0.29 |
| K7 | H7 | 140 | 0.75 | 202 | -723 | 0.51 | 0.24 | 0.26 |
| P7 | H7 | 123 | 0.65 | 381 | -1423 | 0.51 | 0.33 | 0.16 |
| H7 | K7 | 117 | 0.62 | 93 | -1970 | 0.50 | 0.19 | 0.32 |
| A7 | K7 | 100 | 0.53 | -47 | -462 | 0.42 | 0.33 | 0.25 |
| P7 | A7 | 94 | 0.50 | 61 | -2783 | 0.51 | 0.21 | 0.28 |
| A7 | U7 | 86 | 0.46 | 177 | -1813 | 0.53 | 0.27 | 0.20 |
| M7 | P7 | 85 | 0.45 | 352 | -425 | 0.47 | 0.32 | 0.21 |
| U7 | P7 | 81 | 0.43 | 1018 | -2265 | 0.54 | 0.17 | 0.30 |
| A7 | M7 | 77 | 0.41 | 50 | -1553 | 0.45 | 0.27 | 0.27 |
| K7 | A7 | 74 | 0.39 | 83 | -1025 | 0.53 | 0.23 | 0.24 |
| H7 | M7 | 63 | 0.34 | 86 | -2254 | 0.44 | 0.22 | 0.33 |
| H7 | P7 | 59 | 0.31 | -231 | -1347 | 0.46 | 0.27 | 0.27 |
| A7 | P7 | 48 | 0.26 | 1059 | -1300 | 0.54 | 0.23 | 0.23 |
| M7 | U7 | 46 | 0.24 | -70 | -2355 | 0.48 | 0.17 | 0.35 |
| H7 | U7 | 44 | 0.23 | 87 | -3129 | 0.48 | 0.20 | 0.32 |
| O7 | K7 | 34 | 0.18 | -85 | -1553 | 0.44 | 0.24 | 0.35 |
| P7 | O7 | 20 | 0.11 | 456 | -3664 | 0.50 | 0.25 | 0.25 |
| K7 | O7 | 17 | 0.09 | -29 | -426 | 0.29 | 0.41 | 0.29 |
| H7 | A7 | 15 | 0.08 | 132 | -2963 | 0.53 | 0.07 | 0.40 |
| U7 | A7 | 14 | 0.07 | 91 | -3926 | 0.50 | 0.07 | 0.43 |
| U7 | H7 | 14 | 0.07 | -683 | 1570 | 0.29 | 0.64 | 0.07 |
| M7 | O7 | 13 | 0.07 | 71 | -1616 | 0.31 | 0.31 | 0.38 |
| U7 | O7 | 10 | 0.05 | -233 | -2235 | 0.20 | 0.20 | 0.60 |

By session of B (events / per week / B mean $ / A mean $ / combined mean $):
| session | events | per week | B mean $ | A mean $ | sum |
|---|---|---|---|---|---|
| asia | 1631 | 8.68 | 177 | -1436 | -1258 |
| london | 2254 | 12.00 | 69 | -1643 | -1574 |
| nyam | 556 | 2.96 | -27 | -1655 | -1682 |
| nypm | 119 | 0.63 | 18 | -1571 | -1554 |

## 2. Policy on ALL conflicts (stack maxDD impact; BOTH = live = zero row)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_ALL_SKIP | SKIP | ALL | 4560 | -432143 | 1697 | -6.8 | 0.6/0.6/0.5 | 11.8 | -71.2 | 23.9 | 0.21/0.05 | 0.5 |
| R10_ALL_HALF | HALF | ALL | 1750 | -155478 | -393 | 0.6 | -0.9/-0.9/-1.0 | 6.4 | -20.0 | 11.3 | 0.17/0.07 | -0.9 |
| R10_ALL_SKIPS | SKIPS | ALL | 3632 | -178092 | -420 | -0.7 | -2.3/-2.3/-2.4 | -1.2 | -58.6 | 1.8 | 0.19/0.55 | -2.4 |
| R10_ALL_NET | NET | ALL | 6045 | -371659 | -1619 | 10.3 | 4.0/6.3/6.2 | -6.6 | -53.4 | -20.3 | 0.04/0.55 | 5.5 |
| R10_ALL_FLIP | FLIP | ALL | 4721 | -608485 | -3737 | -11.9 | -31.9/-30.8/24.9 | -11.4 | 34.6 | -41.8 | 0.24/0.53 | -12.6 |

## 3. By book pair (older > newer): best policy per pair by key

**A7>K7** (100 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_A7>K7_SKIP | SKIP | A7>K7 | 100 | 4734 | 202 | 1.0 | 1.8/1.8/2.9 | 0.0 | 4.5 | 1.4 | 0.08/0.76 | 2.2 |
| R10_A7>K7_SKIPS | SKIPS | A7>K7 | 96 | 1007 | 138 | 1.0 | 1.6/1.6/2.7 | 0.0 | 1.0 | 1.4 | 0.09/0.72 | 1.9 |

**A7>M7** (77 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_A7>M7_SKIP | SKIP | A7>M7 | 77 | -3839 | 128 | 0.1 | 0.6/0.6/0.5 | 0.0 | -3.2 | 3.2 | 0.21/0.86 | 0.6 |
| R10_A7>M7_SKIPS | SKIPS | A7>M7 | 76 | -1447 | 128 | 0.1 | 0.6/0.6/0.5 | 0.0 | -3.2 | 3.2 | 0.27/0.83 | 0.6 |

**A7>P7** (48 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_A7>P7_SKIPS | SKIPS | A7>P7 | 13 | -6653 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 0.81/0.94 | 0.0 |
| R10_A7>P7_FLIP | FLIP | A7>P7 | 31 | -2834 | -60 | 0.0 | -0.2/-0.2/-0.2 | 0.0 | 0.0 | 2.8 | 0.80/0.99 | -0.2 |

**A7>U7** (86 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_A7>U7_SKIPS | SKIPS | A7>U7 | 75 | -5963 | 231 | 0.1 | 1.1/1.1/1.0 | 0.0 | -3.4 | 3.5 | 0.28/0.85 | 1.1 |
| R10_A7>U7_FLIP | FLIP | A7>U7 | 151 | -38062 | 156 | 0.1 | 0.7/0.7/0.6 | 0.0 | -13.0 | 4.2 | 0.39/0.69 | 0.6 |

**H7>K7** (117 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_H7>K7_FLIP | FLIP | H7>K7 | 156 | 46767 | 545 | 0.1 | 2.3/2.3/2.2 | 0.0 | 5.3 | 1.6 | 0.52/0.91 | 2.3 |
| R10_H7>K7_HALF | HALF | H7>K7 | 9 | -1477 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 0.83/0.97 | 0.0 |

**H7>M7** (63 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_H7>M7_SKIP | SKIP | H7>M7 | 63 | -5419 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | -0.4 | 0.0 | 0.61/0.81 | 0.0 |
| R10_H7>M7_HALF | HALF | H7>M7 | 11 | -3200 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 0.87/0.94 | 0.0 |

**H7>P7** (59 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_H7>P7_FLIP | FLIP | H7>P7 | 34 | -938 | 0 | 0.1 | 0.1/0.1/0.0 | 0.0 | -3.7 | 1.4 | 0.26/0.91 | 0.1 |
| R10_H7>P7_NET | NET | H7>P7 | 102 | 4490 | 0 | -0.1 | -0.1/-0.1/0.0 | 0.0 | -6.2 | -0.0 | 0.49/0.79 | -0.1 |

**H7>U7** (44 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_H7>U7_SKIPS | SKIPS | H7>U7 | 37 | -5108 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | -3.8 | 1.4 | 0.68/0.87 | 0.0 |
| R10_H7>U7_NET | NET | H7>U7 | 87 | -8247 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 1.0 | -1.1 | 0.56/0.85 | 0.0 |

**K7>A7** (74 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_K7>A7_SKIP | SKIP | K7>A7 | 74 | -6158 | 34 | 0.1 | 0.3/0.3/0.2 | 0.0 | -0.9 | 1.2 | 0.23/0.93 | 0.2 |
| R10_K7>A7_SKIPS | SKIPS | K7>A7 | 74 | -6158 | 34 | 0.1 | 0.3/0.3/0.2 | 0.0 | -0.9 | 1.2 | 0.16/0.92 | 0.2 |

**K7>H7** (140 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_K7>H7_SKIPS | SKIPS | K7>H7 | 76 | -8319 | 180 | 0.1 | 0.9/0.9/0.8 | 0.0 | -8.5 | 3.4 | 0.33/0.95 | 0.9 |
| R10_K7>H7_FLIP | FLIP | K7>H7 | 104 | -12716 | 43 | 0.1 | 0.3/0.3/0.2 | 0.1 | 2.6 | 0.6 | 0.38/0.46 | 0.2 |

**K7>M7** (494 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_K7>M7_HALF | HALF | K7>M7 | 62 | 1295 | 29 | 0.0 | 0.1/0.1/0.1 | 1.0 | -1.7 | -0.7 | 0.48/0.03 | 0.1 |
| R10_K7>M7_FLIP | FLIP | K7>M7 | 500 | -35819 | 263 | -1.9 | -0.8/-0.8/1.6 | -1.3 | 7.3 | 9.1 | 0.34/0.75 | 0.0 |

**K7>P7** (608 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_K7>P7_FLIP | FLIP | K7>P7 | 553 | -11375 | 95 | 3.1 | 3.5/3.5/3.4 | -3.6 | 3.1 | -2.4 | 0.10/0.97 | 3.4 |
| R10_K7>P7_HALF | HALF | K7>P7 | 568 | -18580 | 1181 | -3.0 | 2.1/2.1/2.0 | 8.1 | -12.6 | 15.2 | 0.42/0.02 | 2.0 |

**K7>U7** (166 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_K7>U7_SKIPS | SKIPS | K7>U7 | 104 | 22293 | -8 | 0.1 | 0.1/0.1/-0.0 | 0.0 | 2.6 | -0.1 | 0.30/0.88 | 0.0 |
| R10_K7>U7_HALF | HALF | K7>U7 | 138 | -385 | -78 | 0.1 | -0.3/-0.3/-0.4 | 0.0 | 1.8 | -1.2 | 0.33/0.83 | -0.3 |

**M7>K7** (235 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_M7>K7_SKIP | SKIP | M7>K7 | 235 | -13981 | -178 | 1.4 | 0.7/0.7/0.6 | 0.9 | 0.0 | -1.2 | 0.10/0.21 | 0.7 |
| R10_M7>K7_SKIPS | SKIPS | M7>K7 | 230 | -5965 | -178 | 1.4 | 0.7/0.7/0.6 | 0.9 | 1.9 | -1.2 | 0.14/0.24 | 0.7 |

**M7>P7** (85 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_M7>P7_SKIP | SKIP | M7>P7 | 85 | -29907 | 238 | 0.0 | 0.9/0.9/2.5 | 0.0 | -4.7 | 10.2 | 0.42/0.43 | 1.4 |
| R10_M7>P7_HALF | HALF | M7>P7 | 71 | -11729 | 140 | 0.0 | 0.5/0.5/2.8 | 0.0 | -0.9 | 5.4 | 0.50/0.63 | 1.3 |

**M7>U7** (46 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_M7>U7_SKIP | SKIP | M7>U7 | 46 | 3203 | 189 | 0.0 | 0.8/0.8/3.7 | 0.0 | 5.2 | 1.4 | 0.67/0.83 | 1.7 |
| R10_M7>U7_SKIPS | SKIPS | M7>U7 | 32 | 13399 | 189 | 0.0 | 0.8/0.8/3.7 | 0.0 | 5.2 | 1.4 | 0.82/0.90 | 1.7 |

**O7>K7** (34 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_O7>K7_SKIP | SKIP | O7>K7 | 34 | 2881 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | -0.6 | 0.0 | 0.74/0.97 | 0.0 |
| R10_O7>K7_HALF | HALF | O7>K7 | 0 | 0 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 1.00/1.00 | 0.0 |

**P7>A7** (94 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_P7>A7_SKIP | SKIP | P7>A7 | 94 | -5751 | 137 | 0.1 | 0.7/0.7/0.5 | 0.0 | -4.9 | 0.6 | 0.19/0.94 | 0.6 |
| R10_P7>A7_SKIPS | SKIPS | P7>A7 | 94 | -5751 | 137 | 0.1 | 0.7/0.7/0.5 | 0.0 | -4.9 | 0.6 | 0.20/0.94 | 0.6 |

**P7>H7** (123 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_P7>H7_SKIP | SKIP | P7>H7 | 123 | -46838 | -11 | 0.1 | 0.1/0.1/-0.0 | 0.0 | -8.3 | 1.0 | 0.30/0.21 | 0.0 |
| R10_P7>H7_SKIPS | SKIPS | P7>H7 | 120 | -38656 | -11 | 0.1 | 0.1/0.1/-0.0 | 0.0 | -8.3 | 1.0 | 0.33/0.26 | 0.0 |

**P7>K7** (647 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_P7>K7_SKIP | SKIP | P7>K7 | 647 | -14441 | 915 | -1.7 | 1.9/1.9/1.8 | -1.6 | -6.3 | 1.9 | 0.39/0.75 | 1.9 |
| R10_P7>K7_SKIPS | SKIPS | P7>K7 | 645 | -13413 | 915 | -1.7 | 1.9/1.9/1.8 | 0.1 | -6.3 | 1.9 | 0.36/0.49 | 1.9 |

**P7>M7** (374 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_P7>M7_HALF | HALF | P7>M7 | 37 | 268 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 0.60/0.86 | 0.0 |
| R10_P7>M7_FLIP | FLIP | P7>M7 | 341 | -27822 | 330 | -3.1 | -1.7/-1.7/1.3 | 1.9 | 10.2 | -3.5 | 0.54/0.25 | -0.7 |

**P7>U7** (281 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_P7>U7_NET | NET | P7>U7 | 572 | -101763 | 199 | 2.0 | 2.9/2.9/2.7 | 0.0 | -12.6 | -1.3 | 0.10/0.53 | 2.8 |
| R10_P7>U7_SKIP | SKIP | P7>U7 | 281 | -68902 | -122 | 3.1 | 2.6/2.6/2.5 | 0.0 | -16.5 | 1.2 | 0.03/0.69 | 2.6 |

**U7>K7** (196 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_U7>K7_FLIP | FLIP | U7>K7 | 343 | -32511 | 915 | 7.3 | 10.4/10.4/10.3 | 3.8 | -23.1 | 20.8 | 0.01/0.11 | 10.3 |
| R10_U7>K7_NET | NET | U7>K7 | 355 | -28143 | 119 | 2.9 | 3.4/3.4/5.4 | -0.7 | -2.7 | 2.2 | 0.03/0.72 | 4.1 |

**U7>M7** (155 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_U7>M7_FLIP | FLIP | U7>M7 | 173 | -77457 | 15 | 0.2 | 0.2/0.2/0.1 | 1.6 | -1.6 | 2.5 | 0.15/0.17 | 0.2 |
| R10_U7>M7_HALF | HALF | U7>M7 | 22 | -1445 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | -0.4 | 0.0 | 0.78/0.89 | 0.0 |

**U7>P7** (81 events)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_U7>P7_SKIPS | SKIPS | U7>P7 | 44 | -20959 | -22 | -3.0 | -3.1/-3.1/-0.1 | 0.0 | -7.0 | -3.2 | 0.67/0.72 | -2.1 |
| R10_U7>P7_FLIP | FLIP | U7>P7 | 36 | 8763 | -126 | -4.2 | -4.7/-4.7/0.4 | 0.0 | 1.1 | -6.6 | 0.98/0.99 | -3.0 |

## 4. By session of the newer signal

**sess_asia**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_sess_asia_FLIP | FLIP | sess_asia | 1677 | -233663 | -2083 | -6.4 | -16.2/-5.1/7.7 | -10.4 | 8.3 | -35.9 | 0.24/0.80 | -4.5 |
| R10_sess_asia_SKIPS | SKIPS | sess_asia | 1144 | -138580 | -1088 | -0.4 | -4.6/-4.6/-4.7 | 0.1 | -36.1 | -6.2 | 0.17/0.45 | -4.7 |

**sess_london**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_sess_london_SKIP | SKIP | sess_london | 2254 | -156116 | 1961 | 4.9 | 12.2/12.2/12.1 | 6.3 | -44.0 | 23.9 | 0.06/0.19 | 12.2 |
| R10_sess_london_HALF | HALF | sess_london | 790 | -46099 | 888 | 6.0 | 9.4/9.4/9.3 | 5.4 | -10.2 | 14.5 | 0.04/0.07 | 9.4 |

**sess_nyam**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_sess_nyam_SKIP | SKIP | sess_nyam | 556 | 15255 | 625 | 4.4 | 6.6/6.6/6.4 | 1.3 | 19.1 | 12.3 | 0.02/0.15 | 6.5 |
| R10_sess_nyam_HALF | HALF | sess_nyam | 90 | 10331 | 202 | 0.8 | 1.6/1.6/2.2 | 0.0 | 9.6 | 4.1 | 0.12/0.27 | 1.8 |

**sess_nypm**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_sess_nypm_FLIP | FLIP | sess_nypm | 147 | -3972 | 127 | 0.1 | 0.6/0.6/0.5 | 0.0 | 3.1 | 0.3 | 0.52/0.91 | 0.6 |
| R10_sess_nypm_SKIP | SKIP | sess_nypm | 119 | -2119 | 81 | 0.1 | 0.4/0.4/0.3 | 0.0 | 1.6 | 2.0 | 0.45/1.00 | 0.4 |

## 5. By newer book

**newer_K7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_K7_NET | NET | newer_K7 | 2458 | -105853 | -566 | 12.2 | 10.1/10.1/13.4 | -2.6 | -5.5 | -3.9 | 0.01/0.75 | 11.2 |
| R10_newer_K7_SKIPS | SKIPS | newer_K7 | 1317 | -46885 | 561 | 3.3 | 5.6/5.6/5.5 | -0.7 | -2.5 | 2.5 | 0.07/0.54 | 5.5 |

**newer_M7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_M7_HALF | HALF | newer_M7 | 143 | -1321 | 103 | 0.1 | 0.5/0.5/0.4 | 1.0 | -1.9 | -0.2 | 0.23/0.09 | 0.5 |
| R10_newer_M7_FLIP | FLIP | newer_M7 | 1153 | -179172 | 608 | -4.6 | -2.0/-2.0/3.1 | 2.2 | 35.5 | 12.4 | 0.26/0.33 | -0.3 |

**newer_U7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_U7_SKIPS | SKIPS | newer_U7 | 520 | -65170 | -112 | 6.1 | 5.7/5.7/5.6 | 0.0 | -21.7 | 7.3 | 0.04/0.55 | 5.6 |
| R10_newer_U7_NET | NET | newer_U7 | 1191 | -132835 | -183 | 4.9 | 4.2/4.2/4.4 | 0.0 | -12.2 | -1.8 | 0.12/0.52 | 4.3 |

**newer_P7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_P7_FLIP | FLIP | newer_P7 | 734 | -29194 | -128 | 2.5 | 2.0/2.0/3.8 | -3.6 | -1.7 | -4.9 | 0.07/0.96 | 2.6 |
| R10_newer_P7_HALF | HALF | newer_P7 | 823 | -83402 | 730 | -2.9 | 0.3/0.3/0.2 | 8.1 | -15.2 | 10.9 | 0.23/0.02 | 0.2 |

**newer_H7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_H7_SKIPS | SKIPS | newer_H7 | 221 | -30273 | 60 | 0.1 | 0.3/0.3/0.2 | 0.0 | -6.8 | 4.4 | 0.28/0.31 | 0.3 |
| R10_newer_H7_NET | NET | newer_H7 | 441 | -17799 | -275 | 0.1 | -1.1/-1.1/-1.2 | -0.8 | -8.2 | -3.7 | 0.27/0.64 | -1.2 |

**newer_A7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_A7_SKIP | SKIP | newer_A7 | 199 | -15565 | 123 | 0.1 | 0.6/0.6/0.5 | 0.0 | -5.4 | 2.6 | 0.18/0.73 | 0.5 |
| R10_newer_A7_SKIPS | SKIPS | newer_A7 | 199 | -15565 | 123 | 0.1 | 0.6/0.6/0.5 | 0.0 | -5.4 | 2.6 | 0.21/0.81 | 0.5 |

**newer_O7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R10_newer_O7_SKIP | SKIP | newer_O7 | 64 | -6762 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | -0.6 | 0.0 | 1.00/1.00 | 0.0 |
| R10_newer_O7_HALF | HALF | newer_O7 | 0 | 0 | 0 | 0.0 | 0.0/0.0/0.0 | 0.0 | 0.0 | 0.0 | 1.00/1.00 | 0.0 |

## 6. Top cells overall with the bi-weekly WF column and the prior label (rule 2a)
| cell | key | L6M cut % | dmean L6M | PRE cut / dmean | WF2w beat % (cell vs live) | WF2w cut % | label | p fam |
|---|---|---|---|---|---|---|---|---|
| R10_sess_london_SKIP | 12.2 | 4.9 | 1961 | 6.3 / -656 | 30 | 6.3 | OK-PRIOR | 1.00 |
| R10_newer_K7_NET | 11.2 | 12.2 | -566 | -2.6 / -409 | 27 | -2.6 | OK-PRIOR | 1.00 |
| R10_U7>K7_FLIP | 10.3 | 7.3 | 915 | 3.8 / -659 | 42 | 0.0 | OK-PRIOR | 1.00 |
| R10_sess_london_HALF | 9.4 | 6.0 | 888 | 5.4 / -310 | 39 | 5.4 | OK-PRIOR | 1.00 |
| R10_sess_nyam_SKIP | 6.5 | 4.4 | 625 | 1.3 / 333 | 14 | 0.0 | OK-PRIOR | 1.00 |
| R10_newer_U7_SKIPS | 5.6 | 6.1 | -112 | 0.0 / 157 | 19 | 0.0 | OK-PRIOR | 1.00 |
| R10_newer_K7_SKIPS | 5.5 | 3.3 | 561 | -0.7 / -24 | 14 | -0.7 | OK-PRIOR | 1.00 |
| R10_ALL_NET | 5.5 | 10.3 | -1619 | -6.6 / -1326 | 23 | -6.6 | RECENT-ONLY | 1.00 |
| R10_newer_U7_NET | 4.3 | 4.9 | -183 | 0.0 / -757 | 20 | 0.0 | OK-PRIOR | 1.00 |
| R10_U7>K7_NET | 4.1 | 2.9 | 119 | -0.7 / -345 | 16 | 0.0 | OK-PRIOR | 1.00 |

Procedure WF over the whole R10 grid (train 26 w -> 2 w, purged): OOS cut 11.8%, d mean -733 $/wk, beat live in 53% of 74 periods, 74 switches.
Held-out frozen live week: the live week (187 trades) has conflict events only where K7/P7/M7 overlap opposite; first-order held-out read pending (the week is inside the L1M window of the base list only through the engine, not through the live file).
Old-vs-new: no previously published R10 cell exists (never scored); nothing to compare.

## 7. Verdict (screen)
The live behaviour (take both) is the reference. A policy is only a candidate when it beats BOTH on maxDD at equal or better mean in L6M/L3M/L1M, is OK-PRIOR, and the engine-hook run agrees; see section 6 for labels. Exact (netting_hooks) rows: PENDING.

## REFIT 2026-11-22
Trailing 26 weeks, drawdown first: pick **R10_newer_K7_NET** (live retained: False).
| cell               |   maxdd |   worst20 |   ulcer |    mean | live   | prior         |
|:-------------------|--------:|----------:|--------:|--------:|:-------|:--------------|
| R10_newer_K7_NET   | 70176.6 |  120774   | 31266.3 | 23319.1 | False  | PRIOR-UNKNOWN |
| R10_ALL_NET        | 71639.2 |   91001.1 | 32551.2 | 22060.8 | False  | PRIOR-UNKNOWN |
| R10_U7>K7_FLIP     | 74081.5 |  174693   | 31065.6 | 25678.1 | False  | PRIOR-UNKNOWN |
| R10_newer_U7_SKIPS | 75070.8 |  142692   | 31342.6 | 24390   | False  | PRIOR-UNKNOWN |
| R10_newer_U7_SKIP  | 75070.8 |  135978   | 32112.7 | 23782.6 | False  | PRIOR-UNKNOWN |

## EXACT rows (appended)
Exact engine, SZ queue (hooks netting_hooks.py / exit_hooks.py or M_R11 table mode), cuts vs the exact S1b-COMB list (all weeks, ROLL-EXCL); a window is reported only when all its months are done. Months done per set: R10_sess_london_SKIP 0, R10_newer_K7_NET 0, R10_U7_K7_FLIP 0, R10_ALL_FLIP 0
no exact month finished yet (queue tier of R10_/R11_/R9_ prefixes pending).
