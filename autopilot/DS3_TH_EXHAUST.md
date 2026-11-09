# DS3_TH_EXHAUST - every exit technique, both sides, drawdown first (auto-generated 2026-11-09 05:10Z)
**Universe U2 = full S1b tick-close never-cut (43 months) + the u5 live-week entries; this page shows U2 cells only.** The S1b-COMB live reference row is unchanged (S1b).

**Reading guide.** ENTER = passes every gate (recents, tolerant older windows, drawdown not worse in L6M and PRE, delta above MDE, placebo p <= .10, family p <= .10, walk-forward ok, not FAILS-LIVE-WEEK). CANDIDATE-DD = lowers L6M maxDD at equal or better L6M mean and PRE maxDD within +5% (even inside MDE); LEAD = L6M mean and drawdown not worse with >60% of L1M..L6M windows positive. FAILS-LIVE-WEEK = the held-out live-week delta is below -1 MDE-week of that scope (never ENTER). Sub-flags in the label cell: rec-ok/rec-FAIL (no L1M..L6M delta below -1 MDE-week), wf-ok/wf-FAIL, plc-ok/plc-FAIL (placebo p <= .10), exposure (fires on more than 50% of trades = exposure shrink). **ENTER cells on this page: 0.**

## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Null audit: placebo version 2 (causal, leak-tested; EXH_API section 9). Placebo p of cells scored with the version-1 (leaky) null were recomputed or set to NaN (shown as nan, treated as 1.0 by the labels).
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.
Label: state base S1b universe (never-cut hold-to-bracket path; months not yet rebuilt are S1 timer-close, flagged src in the universe), entry match to the live week not yet >= .85 unless stated: PRE-PROOF. Windows as of 2026-11-09 (data to 2026-11-05). USD per ISO week at live lots net of 4.84/contract; delta = rule minus never-cut with the carrying week dropped; "w/wo" = with the rule / without (never-cut). LIVE REFERENCE ROW = S1b-COMB (live week from the u5 replica).
QUARANTINE: 0 cells of agent PHI from the flawed first scoring pass (nfire == ntrades, leg 2 fed back into a new Outcome) are excluded from every table, nulls and the family max-stat; they stay on disk. H/I (take / trail) section: corrected cells in the ledger 0 of 0 expected so far.
Cells scored: 4922; families: ['A', 'A_pulled', 'B_book', 'D', 'E', 'F', 'G', 'J_scale', 'K_target', 'L_cond', 'L_cross', 'L_learned', 'X_cross']. Labels: {'no': 28218, 'CANDIDATE-DD': 7078, 'LEAD': 2030, 'CANDIDATE-DD FAILS-LIVE-WEEK': 1431, 'LEAD FAILS-LIVE-WEEK': 512}

## ALL
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL never-cut level | 35,468 | 67,950 | 37,850 | 31,832 | 16,868 | 12,409 | 14,153 | 2,398 | 121,381 | 152,455 | 77,580 |
| ALL LIVE REF S1b-COMB level | 11,588 | 45,231 | 24,973 | 28,018 | 16,943 | 18,454 | 12,266 | 1,937 | 82,873 | 144,002 | 190,560 |

### ALL loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -19,259 | -19,329 | -8,636 | 807 | -1,810 | 11,840 | -5,789 | -69 | 63,154 / 121,381 | 112,282 / 152,455 | 160,812 / 77,580 | 8,236 | 0.02 | 1.00 / 0.76 | -704,101 | -14,809 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -13,521 | -4,004 | -439 | 4,144 | 1,547 | 1,073 | -4,551 | 602 | 63,570 / 121,381 | 81,504 / 152,455 | 196,521 / 77,580 | 6,934 | 0.02 | 1.00 / 0.81 | -704,101 | -12,691 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | -15,828 | -13,583 | -5,746 | 6,569 | 620 | -711 | -8,302 | 2,422 | 66,566 / 121,381 | 96,748 / 152,455 | 194,982 / 77,580 | 9,752 | 0.12 | 1.00 / 0.86 | -704,101 | -4,754 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 35, "blk": "A", "cancels | -14,770 | -10,567 | -5,884 | 2,685 | 511 | 3,661 | -6,527 | 1,710 | 67,962 / 121,381 | 86,837 / 152,455 | 172,738 / 77,580 | 10,310 | 0.17 | 1.00 / 0.82 | -704,101 | -16,013 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | -16,278 | -15,448 | -7,550 | 4,292 | -413 | -2,840 | -8,868 | -5 | 68,257 / 121,381 | 84,521 / 152,455 | 176,042 / 77,580 | 10,728 | 0.32 | 1.00 / 0.86 | -704,101 | -4,754 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### ALL profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | -3,002 | -5,823 | 1,357 | 574 | 2,054 | 8,213 | -3,279 | 569 | 33,846 / 121,381 | 87,136 / 152,455 | 183,145 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | -3,972 | -6,281 | 784 | 492 | 2,138 | 8,650 | -3,257 | 612 | 34,560 / 121,381 | 90,210 / 152,455 | 182,091 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 1.25, "p": 0.7, "rest": "trail", "x": 20} | -5,218 | -6,503 | 510 | 978 | 1,818 | 6,524 | -3,161 | 1,330 | 37,868 / 121,381 | 79,518 / 152,455 | 176,566 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.7, "rest": "trail", "x": 20} | -4,330 | -5,324 | 1,485 | 2,144 | 2,016 | 6,787 | -3,329 | 961 | 39,107 / 121,381 | 86,368 / 152,455 | 194,942 / 77,580 | 4,708 | 0.02 | 1.00 / 0.41 | -153,458 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.7, "rest": "trail", "x": 40} | -1,036 | -4,949 | 2,567 | 2,991 | 2,326 | 5,037 | -4,582 | 711 | 39,609 / 121,381 | 92,752 / 152,455 | 191,027 / 77,580 | 4,708 | 0.02 | 1.00 / 0.38 | -153,458 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### ALL both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -32,560 | -20,213 | -10,879 | -9,397 | -11,899 | -9,772 | -10,393 | -8 | 77,173 / 121,381 | 151,329 / 152,455 | -4,977 / 77,580 | 10,882 | 0.45 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -30,130 | -35,888 | -28,786 | -20,418 | -24,218 | -17,361 | -20,761 | -5,068 | 232,660 / 121,381 | 546,408 / 152,455 | -253,661 / 77,580 | 14,101 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -68,687 | -45,247 | -44,830 | -49,976 | -42,531 | -27,171 | -28,444 | -14,343 | 734,947 / 121,381 | 1,085,729 / 152,455 | -839,331 / 77,580 | 11,559 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -80,468 | -56,507 | -41,118 | -52,942 | -44,524 | -29,951 | -34,815 | -12,257 | 859,225 / 121,381 | 1,562,793 / 152,455 | -802,609 / 77,580 | 19,035 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -78,303 | -49,251 | -43,158 | -55,657 | -48,996 | -40,897 | -28,076 | -3,415 | 924,483 / 121,381 | 1,108,928 / 152,455 | -917,917 / 77,580 | 16,748 | 1.00 | 1.00 / - |  |  | S1 | no |

## K7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 never-cut level | 4,952 | 8,594 | 3,229 | 4,245 | 2,469 | 1,911 | 2,803 | -80 | 20,902 | 26,707 | 1,791 |
| K7 LIVE REF S1b-COMB level | 7,873 | 8,450 | 3,436 | 3,530 | 2,241 | 3,740 | 2,616 | -164 | 41,849 | 23,073 | -20,339 |

### K7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 5, "arm": "fixed", "armval": 45, "blk": "A", "cancels" | -357 | 315 | 768 | 590 | 418 | 457 | 85 | 59 | 13,000 / 20,902 | 22,963 / 26,707 | 18,592 / 1,791 | 844 | 1.00 | 1.00 / - |  | 476 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 3,525 | 406 | 1,412 | 1,241 | -414 | -783 | -509 | 314 | 13,113 / 20,902 | 18,680 / 26,707 | 28,911 / 1,791 | 2,387 | 0.11 | 1.00 / 1.00 | -175,021 | 311 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 40, "blk": "A", "cancels" | 850 | 669 | 666 | 429 | 325 | 406 | 75 | 7 | 14,057 / 20,902 | 27,137 / 26,707 | 8,530 / 1,791 | 337 | 0.05 | 1.00 / 1.00 | -175,021 | 580 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | 516 | 71 | 385 | 366 | 218 | 62 | 122 | 0 | 15,294 / 20,902 | 21,977 / 26,707 | 13,492 / 1,791 | 213 | 0.03 | 1.00 / 1.00 | -175,021 | 870 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LIVE_45_10x_W2_P3_V2@er_mid | {"cell": "live", "ctx": "er_mid"} | -1,898 | -54 | 353 | 297 | -27 | 411 | 75 | -105 | 15,584 / 20,902 | 22,296 / 26,707 | 7,798 / 1,791 | 312 | 0.28 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### K7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.58 | -41,710 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.02 | 1.00 / 0.79 | -20,690 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,286 | -761 | 1,258 | 270 | -409 | -1,718 | -412 | 480 | 9,389 / 20,902 | 17,644 / 26,707 | 40,236 / 1,791 | 689 | 0.02 | 1.00 / 0.84 | -46,439 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 10} | 2,146 | -846 | 1,106 | 205 | -427 | -1,502 | -395 | 479 | 9,411 / 20,902 | 18,094 / 26,707 | 37,916 / 1,791 | 689 | 0.02 | 1.00 / 0.81 | -46,439 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 1.25, "p": 0.5, "rest": "trail", "x": 10} | 2,235 | -811 | 1,130 | 204 | -422 | -1,556 | -399 | 488 | 9,411 / 20,902 | 18,094 / 26,707 | 37,734 / 1,791 | 969 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -4,471 | -69 | -51 | -2,182 | -2,464 | -180 | -2,640 | -234 | 37,843 / 20,902 | 53,526 / 26,707 | -30,807 / 1,791 | 3,296 | 0.97 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 528 | -2,881 | -1,910 | -876 | -1,378 | 1,268 | -1,570 | 464 | 43,996 / 20,902 | 30,048 / 26,707 | -4,398 / 1,791 | 3,516 | 0.97 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 3,047 | 2,293 | 1,391 | -1,373 | -1,657 | 697 | -2,376 | -45 | 51,300 / 20,902 | 30,754 / 26,707 | -21,896 / 1,791 | 4,335 | 0.97 | 1.00 / - |  |  | S1 | no |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -3,942 | -2,807 | -1,819 | -4,715 | -4,461 | -2,310 | -3,421 | 285 | 60,715 / 20,902 | 76,668 / 26,707 | -66,506 / 1,791 | 3,156 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -10,440 | -8,439 | -5,589 | -8,790 | -7,296 | -3,335 | -6,122 | -2,331 | 150,044 / 20,902 | 257,444 / 26,707 | -143,300 / 1,791 | 6,426 | 1.00 | 1.00 / - |  |  | S1 | no |

## P7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 never-cut level | 33,625 | 22,555 | 13,873 | 11,894 | 8,318 | 5,178 | 8,641 | -118 | 133,887 | 109,442 | -29,902 |
| P7 LIVE REF S1b-COMB level | 5,700 | 18,966 | 12,054 | 14,708 | 10,485 | 11,144 | 6,746 | -2 | 96,490 | 106,914 | 53,844 |

### P7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / - |  | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.51 | -483,434 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | -18,178 | -13,563 | -6,620 | 7,465 | 2,045 | 1,110 | -4,547 | 1,379 | 51,168 / 133,887 | 98,865 / 109,442 | 136,965 / -29,902 | 2,364 | 0.26 | 1.00 / 0.86 | -483,434 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | -19,121 | -14,315 | -8,032 | 5,770 | 1,127 | -927 | -4,333 | -238 | 52,253 / 133,887 | 77,452 / 109,442 | 122,418 / -29,902 | 2,617 | 0.28 | 1.00 / 0.83 | -483,434 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 30, "blk": "A", "cancels | -15,850 | -10,384 | -6,577 | 3,543 | -404 | -1,629 | -2,000 | -62 | 53,895 / 133,887 | 74,320 / 109,442 | 93,383 / -29,902 | 2,435 | 0.02 | 1.00 / 0.75 | -483,434 | -6,409 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### P7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -841 | 678 | 1,582 | 5,082 | 2,987 | 766 | -1,380 | -800 | 82,296 / 133,887 | 92,199 / 109,442 | 76,006 / -29,902 | 1,006 | 0.04 | 1.00 / 0.99 | -186,434 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -1,382 | 528 | 1,972 | 5,069 | 3,016 | 754 | -1,412 | -876 | 83,539 / 133,887 | 91,553 / 109,442 | 78,160 / -29,902 | 1,006 | 0.04 | 1.00 / 1.00 | -186,434 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | 3,029 | -7,152 | -3,235 | 1,621 | 1,825 | 2,116 | -1,081 | -832 | 87,937 / 133,887 | 97,537 / 109,442 | 63,228 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | -646 | -184 | 889 | 515 | 1,200 | 2,100 | -1,148 | -1,053 | 88,539 / 133,887 | 99,024 / 109,442 | 72,153 / -29,902 | 946 | 0.04 | 1.00 / 0.99 | -186,434 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 1,611 | 1,121 | 2,061 | 1,541 | 1,787 | 1,989 | -1,197 | -624 | 92,512 / 133,887 | 99,394 / 109,442 | 63,452 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -30,791 | -13,682 | -8,608 | -2,939 | -7,029 | -6,418 | -8,098 | -986 | 45,473 / 133,887 | 152,285 / 109,442 | -16,581 / -29,902 | 2,981 | 0.03 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -35,154 | -32,544 | -26,288 | -15,368 | -18,497 | -15,180 | -12,938 | -2,932 | 238,845 / 133,887 | 459,309 / 109,442 | -279,528 / -29,902 | 4,163 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -54,615 | -29,333 | -26,550 | -29,051 | -26,804 | -20,713 | -14,985 | -1,365 | 458,559 / 133,887 | 638,112 / 109,442 | -491,731 / -29,902 | 4,153 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -59,823 | -35,471 | -27,032 | -29,153 | -26,164 | -16,302 | -18,403 | -5,236 | 464,500 / 133,887 | 891,741 / 109,442 | -464,592 / -29,902 | 4,708 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -52,765 | -43,798 | -38,351 | -33,800 | -32,804 | -28,021 | -22,341 | -8,389 | 560,892 / 133,887 | 1,158,576 / 109,442 | -602,108 / -29,902 | 4,651 | 1.00 | 1.00 / - |  |  | S1 | no |

## M7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7 never-cut level | 419 | 3,250 | 247 | 410 | 128 | 154 | 90 | -128 | 44,425 | 50,321 | -68,299 |
| M7 LIVE REF S1b-COMB level | 40 | 2,590 | -776 | -227 | -639 | 601 | 523 | -64 | 46,547 | 25,812 | -64,633 |

### M7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / - |  | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.19 | -40,374 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -878 | -1,089 | 756 | 527 | -316 | -939 | -59 | 26 | 14,218 / 44,425 | 26,832 / 50,321 | -36,027 / -68,299 | 2,050 | 0.72 | 1.00 / 0.01 | -40,374 | -2,838 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | 1,823 | -127 | 946 | 1,345 | -350 | 707 | 32 | 113 | 17,053 / 44,425 | 35,735 / 50,321 | -27,658 / -68,299 | 1,042 | 0.02 | 1.00 / 0.33 | -40,374 | 246 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| F3_stop_extreme | {"X": 10, "k": 2} | -834 | -796 | 528 | 589 | -204 | -1,172 | -397 | -486 | 18,590 / 44,425 | 48,298 / 50,321 | -30,434 / -68,299 | 3,129 | 0.11 | 1.00 / - |  | -172 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### M7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,365 | -1,516 | -1,887 | 405 | 519 | -55 | 326 | -83 | 25,111 / 44,425 | 29,613 / 50,321 | -46,302 / -68,299 | 545 | 0.02 | 1.00 / 0.99 | 1,792 |  | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,493 | -1,577 | -1,897 | 451 | 551 | -117 | 138 | -102 | 25,462 / 44,425 | 29,064 / 50,321 | -44,834 / -68,299 | 545 | 0.03 | 1.00 / 1.00 | 1,792 |  | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | -2,620 | -1,616 | -2,047 | 314 | 426 | -268 | 199 | -102 | 28,225 / 44,425 | 34,097 / 50,321 | -49,879 / -68,299 | 545 | 0.03 | 1.00 / 1.00 | 1,792 |  | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.4, "rest": "trail", "x": 5} | -1,864 | -1,116 | -1,545 | 451 | 715 | -110 | 141 | -237 | 29,534 / 44,425 | 41,163 / 50,321 | -49,017 / -68,299 | 505 | 0.03 | 1.00 / 1.00 | 1,792 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok] |
| J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | -2,285 | -1,458 | -1,856 | 292 | 375 | -58 | 42 | 271 | 29,683 / 44,425 | 34,337 / 50,321 | -51,921 / -68,299 | 545 | 0.03 | 1.00 / 1.00 | 1,792 |  | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |

### M7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -709 | -463 | -247 | -1,778 | -1,746 | 229 | -1,355 | -543 | 47,665 / 44,425 | 113,002 / 50,321 | -68,134 / -68,299 | 2,663 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -1,042 | -1,541 | -75 | -825 | -965 | -1,299 | -466 | 98 | 50,392 / 44,425 | 55,729 / 50,321 | -61,893 / -68,299 | 2,190 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -2,181 | -2,128 | -652 | -1,397 | -2,383 | -2,044 | -1,514 | -516 | 56,566 / 44,425 | 125,306 / 50,321 | -71,757 / -68,299 | 1,938 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -1,388 | -980 | -1,018 | -1,796 | -1,764 | -3,022 | -1,348 | -1,623 | 72,377 / 44,425 | 111,494 / 50,321 | -87,150 / -68,299 | 2,060 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -5,116 | -4,440 | -2,765 | -3,371 | -3,226 | -2,653 | -2,356 | -1,458 | 105,357 / 44,425 | 188,483 / 50,321 | -100,418 / -68,299 | 3,766 | 1.00 | 1.00 / - |  |  | S1 | no |

## U7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7 never-cut level | -4,186 | 275 | -125 | 3,207 | 1,811 | 1,724 | 1,437 | 1,354 | 21,561 | 42,226 | 120 |
| U7 LIVE REF S1b-COMB level | -3,377 | 1,858 | 1,576 | 3,562 | 2,081 | 2,437 | 1,419 | 1,157 | 16,419 | 39,155 | 8,146 |

### U7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback | {"X": 10, "pb": 50} | 2,921 | 107 | 228 | 963 | 235 | 1,110 | -933 | -495 | 9,322 / 21,561 | 41,470 / 42,226 | 16,033 / 120 | 860 | 0.02 | 1.00 / 0.81 | -139,434 | 346 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | 2,319 | -92 | -65 | 707 | 177 | 605 | -859 | -281 | 10,892 / 21,561 | 38,666 / 42,226 | 10,630 / 120 | 842 | 0.06 | 1.00 / 0.89 | -139,434 | 346 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 35, "blk": "A", "cancels" | 1,841 | 675 | 498 | 497 | 968 | 2,123 | -562 | 841 | 11,122 / 21,561 | 44,276 / 42,226 | 3,318 / 120 | 676 | 0.08 | 1.00 / 0.89 | -156,760 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| D15_barclose | {"X": 10, "n": 2} | 2,642 | -538 | 604 | 321 | -163 | -1,256 | -426 | -503 | 11,183 / 21,561 | 25,566 / 42,226 | -5,744 / 120 | 1,018 | 0.11 | 1.00 / - |  | 1,917 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| D3_pullback | {"X": 20, "pb": 50} | 3,403 | 388 | 541 | 958 | 409 | 1,548 | -764 | -239 | 11,697 / 21,561 | 42,251 / 42,226 | 18,365 / 120 | 823 | 0.05 | 1.00 / 0.91 | -139,434 | 346 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### U7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,557 | -148 | 1,992 | 551 | 525 | -1,411 | -704 | -575 | 10,319 / 21,561 | 38,921 / 42,226 | 20,588 / 120 | 849 | 0.03 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 2, "p": 0.7, "rest": "trail", "x": 20} | 4,928 | -1,147 | 1,772 | 600 | 502 | -744 | -359 | -270 | 11,277 / 21,561 | 30,968 / 42,226 | 28,281 / 120 | 1,135 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | 3,419 | -1,642 | 1,083 | 266 | 347 | -1,708 | -177 | -229 | 11,660 / 21,561 | 25,905 / 42,226 | 21,130 / 120 | 1,135 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | 3,471 | -1,795 | 1,018 | 203 | 284 | -1,673 | -124 | -183 | 12,029 / 21,561 | 24,988 / 42,226 | 18,811 / 120 | 1,135 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | 2,836 | -1,040 | 967 | 1,250 | 582 | 89 | -538 | -316 | 12,063 / 21,561 | 31,646 / 42,226 | 35,284 / 120 | 462 | 0.08 | 1.00 / 0.98 | -55,326 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### U7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 1,141 | -1,906 | -1,782 | -1,284 | -1,749 | -1,232 | -2,182 | -1,370 | 12,841 / 21,561 | 78,568 / 42,226 | -22,711 / 120 | 1,150 | 0.12 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 739 | -2,641 | -1,533 | -1,539 | -790 | -1,196 | -952 | 453 | 18,512 / 21,561 | 51,925 / 42,226 | -36,857 / 120 | 805 | 0.48 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -1,519 | -2,495 | -3,267 | -5,008 | -4,753 | -3,995 | -3,917 | -2,685 | 56,581 / 21,561 | 200,778 / 42,226 | -87,648 / 120 | 1,364 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | 1,410 | -733 | -875 | -4,985 | -3,648 | -2,500 | -3,111 | -2,083 | 62,594 / 21,561 | 142,148 / 42,226 | -82,127 / 120 | 1,363 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -180 | -2,512 | -3,541 | -6,001 | -4,873 | -3,995 | -3,298 | -2,764 | 81,539 / 21,561 | 156,113 / 42,226 | -106,784 / 120 | 1,031 | 1.00 | 1.00 / - |  |  | S1 | no |

## A7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 never-cut level | 389 | -97 | -190 | 601 | 538 | -81 | 989 | 207 | 12,461 | 6,089 | -17,069 |
| A7 LIVE REF S1b-COMB level | -1,287 | 217 | 169 | 821 | 731 | -228 | 937 | 240 | 8,518 | 7,325 | -11,915 |

### A7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback | {"X": 20, "pb": 50} | 34 | 855 | 467 | 511 | 183 | 304 | -146 | 183 | 4,760 / 12,461 | 5,445 / 6,089 | -6,160 / -17,069 | 700 | 0.02 | 1.00 / 0.29 | -12,489 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | -11 | 288 | 199 | 129 | 24 | 223 | -207 | 201 | 4,785 / 12,461 | 4,912 / 6,089 | -4,174 / -17,069 | 713 | 0.02 | 1.00 / 0.29 | -12,489 | -1,018 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -1,359 | 469 | 197 | 60 | -86 | 140 | -263 | -96 | 5,011 / 12,461 | 5,315 / 6,089 | -15,604 / -17,069 | 573 | 0.11 | 1.00 / 0.25 | -63,333 | -1,306 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels" | -868 | 953 | 693 | 92 | -87 | -196 | -195 | 32 | 5,218 / 12,461 | 6,308 / 6,089 | -13,403 / -17,069 | 477 | 0.02 | 1.00 / 0.27 | -63,333 | -169 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| D3_pullback | {"X": 25, "pb": 50} | 4 | -47 | -23 | 495 | 317 | 376 | -165 | 143 | 5,262 / 12,461 | 5,836 / 6,089 | -8,227 / -17,069 | 679 | 0.02 | 1.00 / 0.37 | -12,489 | -723 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### A7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,706 | -707 | -222 | 171 | -71 | -296 | -119 | -180 | 5,693 / 12,461 | 4,907 / 6,089 | -543 / -17,069 | 785 | 0.02 | 1.00 / 0.46 | -11,844 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 20} | 435 | -1,645 | -771 | 303 | 80 | -616 | -159 | -145 | 6,463 / 12,461 | 5,050 / 6,089 | -10,528 / -17,069 | 831 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 20} | 199 | -1,646 | -809 | 284 | 89 | -641 | -161 | -107 | 7,617 / 12,461 | 5,050 / 6,089 | -12,003 / -17,069 | 831 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 20} | -15 | -1,826 | -824 | 209 | 21 | -539 | -208 | -145 | 7,663 / 12,461 | 4,701 / 6,089 | -11,892 / -17,069 | 831 | 0.03 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | -1,149 | -81 | -54 | 105 | 67 | -243 | -12 | 0 | 11,375 / 12,461 | 6,089 / 6,089 | -16,207 / -17,069 | 21 | 0.12 | 1.00 / 0.97 | -2,697 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### A7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -907 | 293 | 148 | 521 | 204 | 21 | -232 | 80 | 4,415 / 12,461 | 4,374 / 6,089 | -7,646 / -17,069 | 732 | 0.03 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -79 | 1,126 | 656 | 252 | -23 | 302 | -59 | 30 | 6,506 / 12,461 | 5,710 / 6,089 | -13,365 / -17,069 | 453 | 0.06 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -1,696 | -428 | -114 | -293 | -266 | 279 | -236 | -3 | 10,135 / 12,461 | 5,229 / 6,089 | -17,946 / -17,069 | 591 | 0.76 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -2,515 | 288 | -142 | 150 | 74 | -31 | -159 | 91 | 13,843 / 12,461 | 6,334 / 6,089 | -19,537 / -17,069 | 385 | 0.97 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -3,667 | -1,687 | -1,652 | -1,917 | -1,706 | -1,113 | -1,121 | -467 | 36,703 / 12,461 | 26,061 / 6,089 | -47,507 / -17,069 | 1,169 | 1.00 | 1.00 / - |  |  | S1 | no |

## H7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7 never-cut level | -88 | 1,778 | -301 | 1,647 | -73 | -2,452 | 1,623 | 103 | 15,477 | 20,667 | -32,750 |
| H7 LIVE REF S1b-COMB level | 3,186 | 1,158 | 406 | 2,545 | 625 | -1,655 | 1,574 | 220 | 8,818 | 19,256 | 11,007 |

### H7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 549 | 354 | 480 | 594 | 560 | 866 | -98 | -40 | 5,466 / 15,477 | 18,613 / 20,667 | -928 / -32,750 | 395 | 0.06 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 708 | 434 | 594 | 545 | 530 | 863 | -57 | -19 | 5,486 / 15,477 | 17,364 / 20,667 | -1,823 / -32,750 | 387 | 0.02 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 842 | 458 | 1,024 | 893 | 715 | 812 | -159 | 137 | 5,505 / 15,477 | 16,303 / 20,667 | 579 / -32,750 | 389 | 0.02 | 1.00 / - |  | 244 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 527 | 276 | 444 | 744 | 600 | 808 | -74 | -89 | 5,574 / 15,477 | 17,669 / 20,667 | 3,412 / -32,750 | 383 | 0.03 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 673 | 349 | 547 | 674 | 562 | 808 | -27 | -67 | 5,594 / 15,477 | 16,463 / 20,667 | 1,635 / -32,750 | 376 | 0.02 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### H7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,216 | 752 | 1,333 | 760 | 657 | -170 | -646 | -522 | 7,798 / 15,477 | 12,907 / 20,667 | 7,005 / -32,750 | 761 | 0.02 | 1.00 / 0.63 | -16,822 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 10} | 1,421 | 601 | 1,116 | 356 | 334 | -319 | -613 | -328 | 8,561 / 15,477 | 16,629 / 20,667 | -1,011 / -32,750 | 755 | 0.03 | 1.00 / 0.54 | -26,802 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,421 | 601 | 1,116 | 356 | 341 | -312 | -552 | -319 | 8,561 / 15,477 | 16,400 / 20,667 | -1,011 / -32,750 | 755 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 10} | 1,421 | 601 | 1,116 | 356 | 337 | -312 | -487 | -331 | 8,561 / 15,477 | 15,800 / 20,667 | -1,011 / -32,750 | 755 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 1,562 | 84 | 603 | 1,206 | 645 | -954 | -365 | 0 | 9,470 / 15,477 | 20,667 / 20,667 | 598 / -32,750 | 207 | 0.24 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### H7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -536 | -708 | 210 | -1,609 | -990 | 728 | -1,369 | -784 | 15,597 / 15,477 | 22,528 / 20,667 | -36,028 / -32,750 | 914 | 0.79 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 423 | -130 | 732 | -234 | 96 | 1,270 | -13 | 365 | 18,057 / 15,477 | 15,996 / 20,667 | -17,809 / -32,750 | 527 | 0.73 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 1,818 | 605 | 727 | 219 | 161 | 1,033 | -1,401 | -444 | 24,746 / 15,477 | 20,219 / 20,667 | -17,199 / -32,750 | 828 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 107 | -650 | -485 | -1,954 | -1,038 | 1,048 | -1,076 | -431 | 28,781 / 15,477 | 23,987 / 20,667 | -40,847 / -32,750 | 694 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -976 | -1,534 | -498 | -2,131 | -902 | 1,432 | -1,986 | -764 | 30,617 / 15,477 | 46,127 / 20,667 | -39,431 / -32,750 | 1,091 | 1.00 | 1.00 / - |  |  | S1 | no |

## O7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 never-cut level | -685 | -396 | -65 | 280 | 687 | -245 | 644 | -119 | 7,469 | 5,102 | -9,532 |
| O7 LIVE REF S1b-COMB level | -988 | -446 | -78 | 331 | 651 | -343 | 636 | -147 | 6,656 | 4,532 | -8,247 |

### O7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 612 | 616 | 335 | 144 | 25 | 218 | 36 | 33 | 5,063 / 7,469 | 4,480 / 5,102 | -5,398 / -9,532 | 160 | 0.03 | 1.00 / 0.77 | -46,487 | 76 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_TREE_WF | {"cov": "WF months only; other months never-cut", "leaves":  | 87 | 553 | 344 | 52 | -20 | -3 | -184 | 4 | 5,953 / 7,469 | 4,559 / 5,102 | -8,996 / -9,532 | 212 | 0.14 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| G_TREE_WF | {"cov": "WF months only; other months never-cut", "leaves":  | 87 | 553 | 344 | 52 | -33 | -3 | -184 | 4 | 5,953 / 7,469 | 4,559 / 5,102 | -8,996 / -9,532 | 223 | 0.18 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 179 | 244 | 293 | 212 | -8 | -42 | -127 | 6 | 5,954 / 7,469 | 4,495 / 5,102 | -6,137 / -9,532 | 310 | 0.17 | 1.00 / 0.97 | -46,487 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 179 | 244 | 293 | 212 | -8 | -42 | -130 | 52 | 5,954 / 7,469 | 4,495 / 5,102 | -6,137 / -9,532 | 308 | 0.25 | 1.00 / 0.97 | -46,487 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### O7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.05 | 1.00 / 0.88 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.02 | 1.00 / 0.88 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.03 | 1.00 / 0.93 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.02 | 1.00 / 0.93 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 0 | -47 | 52 | 44 | -273 | -296 | 6 | 0 | 7,104 / 7,469 | 4,578 / 5,102 | -7,351 / -9,532 | 76 | 0.60 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### O7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | 248 | 151 | -87 | -248 | -657 | -51 | -785 | -74 | 4,786 / 7,469 | 17,226 / 5,102 | -7,262 / -9,532 | 506 | 0.36 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 211 | 59 | -79 | -150 | -274 | 43 | -246 | 9 | 5,408 / 7,469 | 12,407 / 5,102 | -8,281 / -9,532 | 324 | 0.21 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 86 | 81 | -43 | -161 | -263 | -21 | -343 | 115 | 5,713 / 7,469 | 10,713 / 5,102 | -9,553 / -9,532 | 267 | 0.18 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 147 | 300 | 242 | 212 | -80 | -87 | 83 | -27 | 8,203 / 7,469 | 4,656 / 5,102 | -5,463 / -9,532 | 227 | 0.91 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -33 | 30 | -118 | -333 | -701 | -414 | -589 | -356 | 8,634 / 7,469 | 6,509 / 5,102 | -11,943 / -9,532 | 382 | 1.00 | 1.00 / - |  |  | S1 | no |

## X3
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X3 never-cut level | -166 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 664 | 0 | -664 |
| X3 LIVE REF S1b-COMB level | -448 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1,794 | 0 | -1,794 |

### X3 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 30, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 228 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.49 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 235 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.48 | 1.00 / - |  | 1,481 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 50, "blk": "A", "cancels | 211 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.55 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 182 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.49 | 1.00 / - |  | 1,166 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 336 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.51 | 1.00 / - |  | 1,941 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### X3 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K2_atrtarget | {"c": 6} | 393 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| K1_target | {"m": 1.1} | 120 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 184 / 664 | 0 / 0 | -184 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| J1_scale | {"b": 0, "p": 0.9, "rest": "be"} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.83 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.9, "rest": "trail", "x": 40} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.83 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.9, "rest": "trail", "x": 20} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.91 | 1.00 / - |  |  | S1 | no |

### X3 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 379 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 0.52 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | 97 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 275 / 664 | 0 / 0 | -275 / -664 | 4 | 0.48 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 650 / 664 | 0 / 0 | -650 / -664 | 3 | 0.61 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -101 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1,068 / 664 | 0 / 0 | -1,068 / -664 | 4 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -394 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 2,238 / 664 | 0 / 0 | -2,238 / -664 | 3 | 0.94 | 1.00 / - |  |  | S1 | no |

## X4
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X4 never-cut level | 1,195 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X4 LIVE REF S1b-COMB level | 795 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X4 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels" | -874 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 513 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -904 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 538 | S1 | no |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 30, "blk": "A", "cancels | -883 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 533 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | -686 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 1,223 | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 20, "blk": "A", "cancels | -842 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 568 | S1 | no |

### X4 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.8, "rest": "trail", "x": 40} | -418 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 40} | -598 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "tot_rel_slow", "rest": "hold", "s": 3, "th" | -393 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | -388 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "hold"} | -450 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |

### X4 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -1,121 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -480 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -853 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -1,296 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 402 / 0 | 0 / 0 | -402 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | -1,411 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 863 / 0 | 0 / 0 | -863 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |

## X5
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X5 never-cut level | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X5 LIVE REF S1b-COMB level | 95 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X5 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 424 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 788 | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 50, "blk": "A", "cancels | 44 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 471 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 973 | S1 | no |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | 232 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 18 | S1 | no |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 414 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 748 | S1 | no |

### X5 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 1.1} | 60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.4, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.6, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"b": 0, "p": 0.9, "rest": "be"} | -30 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 69 / 0 | 0 / 0 | -69 / 0 | 1 | 0.55 | 1.00 / - |  |  | S1 | no |

### X5 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | 121 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 99 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 0.76 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 108 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 439 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -40 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 110 / 0 | 0 / 0 | -110 / 0 | 2 | 0.82 | 1.00 / - |  |  | S1 | no |

## Survivors per book (CANDIDATE-DD and rec-ok and plc-ok and not FAILS-LIVE-WEEK; wf shown, not required; top 3 by drawdown-first)
### ALL survivors (299 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | -3,002 | -5,823 | 1,357 | 574 | 2,054 | 8,213 | -3,279 | 569 | 33,846 / 121,381 | 87,136 / 152,455 | 183,145 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | -3,972 | -6,281 | 784 | 492 | 2,138 | 8,650 | -3,257 | 612 | 34,560 / 121,381 | 90,210 / 152,455 | 182,091 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 1.25, "p": 0.7, "rest": "trail", "x": 20} | -5,218 | -6,503 | 510 | 978 | 1,818 | 6,524 | -3,161 | 1,330 | 37,868 / 121,381 | 79,518 / 152,455 | 176,566 / 77,580 | 7,732 | 0.02 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 survivors (69 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.58 | -41,710 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.02 | 1.00 / 0.79 | -20,690 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,286 | -761 | 1,258 | 270 | -409 | -1,718 | -412 | 480 | 9,389 / 20,902 | 17,644 / 26,707 | 40,236 / 1,791 | 689 | 0.02 | 1.00 / 0.84 | -46,439 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 survivors (108 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / - |  | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.51 | -483,434 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 30, "blk": "A", "cancels | -15,850 | -10,384 | -6,577 | 3,543 | -404 | -1,629 | -2,000 | -62 | 53,895 / 133,887 | 74,320 / 109,442 | 93,383 / -29,902 | 2,435 | 0.02 | 1.00 / 0.75 | -483,434 | -6,409 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### M7 survivors (234 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / - |  | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.19 | -40,374 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | 1,823 | -127 | 946 | 1,345 | -350 | 707 | 32 | 113 | 17,053 / 44,425 | 35,735 / 50,321 | -27,658 / -68,299 | 1,042 | 0.02 | 1.00 / 0.33 | -40,374 | 246 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### U7 survivors (109 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback | {"X": 10, "pb": 50} | 2,921 | 107 | 228 | 963 | 235 | 1,110 | -933 | -495 | 9,322 / 21,561 | 41,470 / 42,226 | 16,033 / 120 | 860 | 0.02 | 1.00 / 0.81 | -139,434 | 346 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,557 | -148 | 1,992 | 551 | 525 | -1,411 | -704 | -575 | 10,319 / 21,561 | 38,921 / 42,226 | 20,588 / 120 | 849 | 0.03 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | 2,319 | -92 | -65 | 707 | 177 | 605 | -859 | -281 | 10,892 / 21,561 | 38,666 / 42,226 | 10,630 / 120 | 842 | 0.06 | 1.00 / 0.89 | -139,434 | 346 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### A7 survivors (240 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -907 | 293 | 148 | 521 | 204 | 21 | -232 | 80 | 4,415 / 12,461 | 4,374 / 6,089 | -7,646 / -17,069 | 732 | 0.03 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 20, "pb": 50} | 34 | 855 | 467 | 511 | 183 | 304 | -146 | 183 | 4,760 / 12,461 | 5,445 / 6,089 | -6,160 / -17,069 | 700 | 0.02 | 1.00 / 0.29 | -12,489 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | -11 | 288 | 199 | 129 | 24 | 223 | -207 | 201 | 4,785 / 12,461 | 4,912 / 6,089 | -4,174 / -17,069 | 713 | 0.02 | 1.00 / 0.29 | -12,489 | -1,018 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### H7 survivors (110 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 549 | 354 | 480 | 594 | 560 | 866 | -98 | -40 | 5,466 / 15,477 | 18,613 / 20,667 | -928 / -32,750 | 395 | 0.06 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 708 | 434 | 594 | 545 | 530 | 863 | -57 | -19 | 5,486 / 15,477 | 17,364 / 20,667 | -1,823 / -32,750 | 387 | 0.02 | 1.00 / - |  | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 842 | 458 | 1,024 | 893 | 715 | 812 | -159 | 137 | 5,505 / 15,477 | 16,303 / 20,667 | 579 / -32,750 | 389 | 0.02 | 1.00 / - |  | 244 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### O7 survivors (26 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 612 | 616 | 335 | 144 | 25 | 218 | 36 | 33 | 5,063 / 7,469 | 4,480 / 5,102 | -5,398 / -9,532 | 160 | 0.03 | 1.00 / 0.77 | -46,487 | 76 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.05 | 1.00 / 0.88 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.02 | 1.00 / 0.88 | -8,210 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### X3 survivors (1 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 55, "k": 2} | 164 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 9 / 664 | 0 / 0 | -9 / -664 | 1 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

- X4: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)
- X5: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)

## Walk-forward of the picking procedure (all cells of a book/side; purged monthly, 7-day embargo, trailing 26 weeks, key = maxDD, worst-20, Ulcer, -mean)
| book   | side   |   ncells |   total |   dd_never |   dd_wf |   share_pos |   npick |   months | wf_ok   |
|:-------|:-------|---------:|--------:|-----------:|--------:|------------:|--------:|---------:|:--------|
| ALL    | loss   |     2300 | -870563 |     153255 |  193924 |           0 |      35 |       35 | False   |
| ALL    | profit |      427 | -400389 |     153255 |  169314 |           0 |      35 |       35 | False   |
| K7     | loss   |     2287 | -152415 |      42831 |   38612 |           0 |      35 |       35 | False   |
| K7     | profit |      356 |  -81360 |      42831 |   37835 |           0 |      35 |       35 | False   |
| P7     | loss   |     2277 | -513557 |     144370 |  185332 |           0 |      35 |       35 | False   |
| P7     | profit |      418 | -428886 |     144370 |  151086 |           0 |      35 |       35 | False   |
| M7     | loss   |     2209 |  -35412 |      68802 |   43361 |           1 |      35 |       35 | False   |
| M7     | profit |      316 |  -47752 |      68802 |   59671 |           0 |      35 |       35 | False   |
| U7     | loss   |     2111 | -123004 |      42226 |   55955 |           1 |      35 |       35 | False   |
| U7     | profit |      385 |  -74279 |      42226 |   48580 |           0 |      35 |       35 | False   |
| A7     | loss   |     2110 |  -38102 |      14181 |   17209 |           0 |      35 |       35 | False   |
| A7     | profit |       11 |  -12951 |      14181 |    8898 |           0 |      26 |       35 | False   |
| H7     | loss   |     2107 |  -44501 |      57397 |   24100 |           1 |      35 |       35 | False   |
| H7     | profit |      350 |   -5812 |      57397 |   24775 |           0 |      35 |       35 | False   |
| O7     | loss   |     1281 |  -46295 |       7469 |    7787 |           0 |      35 |       35 | False   |
| O7     | profit |       13 |  -13496 |       7469 |    7469 |           0 |      23 |       35 | False   |

## Stack view and one rule for all books (first-order, IN-SAMPLE best-of-thousands picks per book: read them against the walk-forward table above, which is negative for almost every book/side)
Per-book picks stacked: L6M maxDD 47,773 vs never-cut 121,381; PRE maxDD 140,349 vs 152,455; L6M dmean 13,504. Best single cell on all books: X1_scale_target ({"m": 0.75, "p": 0.7, "rest": "trail", "x": 10}), L6M maxDD 33,846, dmean 574.

## Plain sentences
- ALL loss: the technique that lowers drawdown most is A_pulled ({"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels": "net", "maeW": 5, "med": "e001", "mult": 15, "newmae": 1, "pers": 3, "pulled": "own"}); L6M maxDD 63,154 vs 121,381 never-cut (-58,227); it costs 2,431 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- ALL profit: the technique that lowers drawdown most is X1_scale_target ({"m": 0.75, "p": 0.7, "rest": "trail", "x": 10}); L6M maxDD 33,846 vs 121,381 never-cut (-87,535); it costs 2,664 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- ALL both: the technique that lowers drawdown most is CROSS[254d02cb61ad+9cdf7469ba89] ({"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba89"}); L6M maxDD 77,173 vs 121,381 never-cut (-44,208); it costs 12,635 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.45, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- K7 loss: the technique that lowers drawdown most is A_pulled ({"W": 5, "arm": "fixed", "armval": 45, "blk": "A", "cancels": "net", "maeW": 5, "med": "e001", "mult": 8, "newmae": 1, "pers": 10, "pulled": "own"}); L6M maxDD 13,000 vs 20,902 never-cut (-7,902); it earns 603 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- K7 profit: the technique that lowers drawdown most is J3_statescale ({"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, "x": 10}); L6M maxDD 8,893 vs 20,902 never-cut (-12,009); it earns 1,385 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 both: the technique that lowers drawdown most is CROSS[d8088d34f428+87cd2ee2381f] ({"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee2381f"}); L6M maxDD 37,843 vs 20,902 never-cut (+16,941); it costs 1,466 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.97, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- P7 loss: the technique that lowers drawdown most is D0_plain@after30 ({"X": 30, "ctx": "after30"}); L6M maxDD 45,910 vs 133,887 never-cut (-87,977); it costs 619 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- P7 profit: the technique that lowers drawdown most is L1_cond ({"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "cond": "atr_mid"}); L6M maxDD 82,296 vs 133,887 never-cut (-51,591); it earns 2,268 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 both: the technique that lowers drawdown most is CROSS[254d02cb61ad+9cdf7469ba89] ({"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba89"}); L6M maxDD 45,473 vs 133,887 never-cut (-88,414); it costs 5,753 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- M7 loss: the technique that lowers drawdown most is F3_stop_extreme ({"X": 10, "k": 0}); L6M maxDD 13,450 vs 44,425 never-cut (-30,976); it earns 1,349 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- M7 profit: the technique that lowers drawdown most is J1_scale ({"p": 0.3, "rest": "trail", "x": 10}); L6M maxDD 25,111 vs 44,425 never-cut (-19,314); it earns 1,250 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00. Label CANDIDATE-DD.
- M7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 47,665 vs 44,425 never-cut (+3,240); it costs 698 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- U7 loss: the technique that lowers drawdown most is D3_pullback ({"X": 10, "pb": 50}); L6M maxDD 9,322 vs 21,561 never-cut (-12,239); it earns 836 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- U7 profit: the technique that lowers drawdown most is X2_target_trail ({"arm": 0.7, "m": 2, "x": 20}); L6M maxDD 10,319 vs 21,561 never-cut (-11,242); it earns 545 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- U7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 12,841 vs 21,561 never-cut (-8,720); it costs 1,411 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.12, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- A7 loss: the technique that lowers drawdown most is D3_pullback ({"X": 20, "pb": 50}); L6M maxDD 4,760 vs 12,461 never-cut (-7,701); it earns 606 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 profit: the technique that lowers drawdown most is K1_target ({"m": 0.6}); L6M maxDD 5,693 vs 12,461 never-cut (-6,767); it earns 308 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 4,415 vs 12,461 never-cut (-8,046); it earns 301 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- H7 loss: the technique that lowers drawdown most is LBC_sweep8_w30 ({"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w30", "mode": "latch", "months": "202304-202611(44)", "pers": 1, "thr": 6.0}); L6M maxDD 5,466 vs 15,477 never-cut (-10,010); it costs 676 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- H7 profit: the technique that lowers drawdown most is K1_target ({"m": 0.5}); L6M maxDD 7,798 vs 15,477 never-cut (-7,679); it costs 511 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 both: the technique that lowers drawdown most is CROSS[afa4804db573+e1e6e2a7d150] ({"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d150"}); L6M maxDD 15,597 vs 15,477 never-cut (+120); it costs 2,833 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.79, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- O7 loss: the technique that lowers drawdown most is A_pulled ({"W": 15, "arm": "fixed", "armval": 10, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 60, "newmae": 0, "pers": 1, "pulled": "own"}); L6M maxDD 5,063 vs 7,469 never-cut (-2,405); it earns 93 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- O7 profit: the technique that lowers drawdown most is K3_structtarget ({"buf": 0, "level": "prior_day", "lim": 150}); L6M maxDD 5,487 vs 7,469 never-cut (-1,982); it earns 2 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- O7 both: the technique that lowers drawdown most is CROSS[3442b23cadf7+55aab8e87e08] ({"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e08"}); L6M maxDD 4,786 vs 7,469 never-cut (-2,682); it costs 299 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.36, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- X3 loss: the technique that lowers drawdown most is A_pulled ({"W": 30, "arm": "fixed", "armval": 10, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 120, "newmae": 0, "pers": 2, "pulled": "own"}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.49, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 profit: the technique that lowers drawdown most is K2_atrtarget ({"c": 6}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.52, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X4 loss: the technique that lowers drawdown most is A_pulled ({"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 15, "newmae": 0, "pers": 3, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X4 profit: the technique that lowers drawdown most is J1_scale ({"p": 0.8, "rest": "trail", "x": 40}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X4 both: the technique that lowers drawdown most is CROSS[afa4804db573+e1e6e2a7d150] ({"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d150"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 loss: the technique that lowers drawdown most is A_pulled ({"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels": "net", "maeW": 15, "med": "e001", "mult": 15, "newmae": 1, "pers": 1, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 profit: the technique that lowers drawdown most is K1_target ({"m": 1.1}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 both: the technique that lowers drawdown most is CROSS[afa4804db573+e1e6e2a7d150] ({"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d150"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.

---
universe U2: U2 = full S1b tick-close never-cut (43 months), U1 kept on disk (universe_U1/) as screen-only
