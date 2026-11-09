# DS3_TH_EXHAUST - every exit technique, both sides, drawdown first (auto-generated 2026-11-09 04:16Z)
**Universe shown: U1 (mixed S1 timer-close / S1b months) = SCREEN-ONLY. U2 (full S1b tick-close never-cut, 43 months + u5 live week) holds 1 cells; the page switches to U2 at 200 U2 cells and all final statistics use U2 only.** The S1b-COMB live reference row is unchanged (S1b).

## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Null audit: placebo version 2 (causal, leak-tested; EXH_API section 9). Placebo p of cells scored with the version-1 (leaky) null were recomputed or set to NaN (shown as nan, treated as 1.0 by the labels).
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.
Label: state base S1b universe (never-cut hold-to-bracket path; months not yet rebuilt are S1 timer-close, flagged src in the universe), entry match to the live week not yet >= .85 unless stated: PRE-PROOF. Windows as of 2026-11-09 (data to 2026-11-05). USD per ISO week at live lots net of 4.84/contract; delta = rule minus never-cut with the carrying week dropped; "w/wo" = with the rule / without (never-cut). LIVE REFERENCE ROW = S1b-COMB (live week from the u5 replica).
QUARANTINE: 578 cells of agent PHI from the flawed first scoring pass (nfire == ntrades, leg 2 fed back into a new Outcome) are excluded from every table, nulls and the family max-stat; they stay on disk. H/I (take / trail) section: corrected cells in the ledger 307 of 885 expected so far - **PENDING corrected scoring**.
Cells scored: 7449; families: ['A', 'A_pulled', 'B_book', 'C_flow', 'D', 'E', 'F', 'G', 'J_scale', 'K_target', 'L_cond', 'L_cross', 'L_learned', 'PHI_H']. Labels: {'no': 40856, 'CANDIDATE-DD': 11801, 'LEAD': 3272, 'CANDIDATE-DD FAILS-LIVE-WEEK': 983, 'LEAD FAILS-LIVE-WEEK': 342}

## ALL
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL never-cut level | 39,825 | 33,914 | 15,825 | 21,214 | 13,522 | 7,751 | 15,904 | 1,356 | 117,593 | 177,634 | 89,449 |
| ALL LIVE REF S1b-COMB level | 11,588 | 31,519 | 16,583 | 23,991 | 15,430 | 18,054 | 14,960 | 1,063 | 82,873 | 144,002 | 190,560 |

### ALL loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -35,997 | -4,815 | 3,055 | 677 | -4,057 | -6,204 | -10,503 | -1,219 | 32,689 / 117,593 | 174,715 / 177,634 | 145,488 / 89,449 | 10,540 | 0.02 | 1.00 / - |  | -13,072 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | -41,715 | -13,374 | -4,031 | 2,988 | -651 | 2,107 | -11,416 | -43 | 33,012 / 117,593 | 102,045 / 177,634 | 172,308 / 89,449 | 11,639 | 0.02 | 1.00 / - |  | -16,805 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -26,953 | -5,524 | 4,410 | 2,814 | -1,451 | -601 | -8,244 | -535 | 33,652 / 117,593 | 125,311 / 177,634 | 244,699 / 89,449 | 6,302 | 0.05 | 1.00 / - |  | -15,136 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | -34,280 | -13,488 | -3,327 | 4,028 | -674 | 4,042 | -11,588 | -1,105 | 36,861 / 117,593 | 87,472 / 177,634 | 221,235 / 89,449 | 11,686 | 0.02 | 1.00 / - |  | -10,106 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w30 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w3 | -35,497 | -4,140 | 3,853 | 186 | -5,311 | -9,478 | -9,629 | -1,155 | 37,689 / 117,593 | 155,330 / 177,634 | 140,368 / 89,449 | 10,291 | 0.03 | 1.00 / 0.38 | -228,215 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### ALL profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | 710 | 126 | 3,449 | 2,652 | 2,465 | 1,656 | -1,437 | -672 | 68,059 / 117,593 | 140,683 / 177,634 | 245,094 / 89,449 | 1,672 | 0.04 | 1.00 / 0.46 | -18,295 | -3,688 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 3,380 | 1,665 | 4,881 | 3,704 | 2,949 | 1,818 | -1,516 | -331 | 71,712 / 117,593 | 140,982 / 177,634 | 236,696 / 89,449 | 1,672 | 0.04 | 1.00 / 0.50 | -18,295 | -6,038 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | -1,759 | 2,218 | 5,268 | 2,464 | 2,430 | 876 | -922 | 69 | 72,838 / 117,593 | 123,392 / 177,634 | 156,493 / 89,449 | 3,646 | 0.04 | 1.00 / 0.40 | -18,295 | 2,073 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 3,437 | 1,733 | 4,824 | 3,720 | 2,906 | 1,708 | -744 | -293 | 73,379 / 117,593 | 142,529 / 177,634 | 238,861 / 89,449 | 1,672 | 0.04 | 1.00 / 0.57 | -18,295 | -6,038 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | -2,513 | 1,024 | 4,897 | 3,041 | 2,769 | 1,435 | -906 | 954 | 76,130 / 117,593 | 129,339 / 177,634 | 171,775 / 89,449 | 3,646 | 0.04 | 1.00 / 0.50 | -18,295 | 2,528 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

## K7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 never-cut level | 4,971 | 8,571 | 3,724 | 3,735 | 2,100 | 716 | 2,609 | 340 | 26,983 | 30,403 | -15,009 |
| K7 LIVE REF S1b-COMB level | 7,873 | 8,450 | 3,532 | 4,228 | 2,443 | 3,682 | 2,926 | 183 | 41,849 | 23,073 | -20,339 |

### K7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -3,000 | -47 | 2,951 | 449 | -456 | 2,063 | -1,292 | -299 | 5,160 / 26,983 | 21,469 / 30,403 | 18,128 / -15,009 | 4,209 | 0.05 | 1.00 / - |  | 3,225 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,978 | 3,833 | 5,163 | 2,076 | 208 | 146 | -689 | 104 | 5,501 / 26,983 | 24,135 / 30,403 | 44,481 / -15,009 | 3,439 | 0.02 | 1.00 / - |  | 2,830 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | -3,357 | 666 | 3,418 | 654 | -159 | -1,045 | -1,233 | -63 | 6,384 / 26,983 | 28,853 / 30,403 | 23,584 / -15,009 | 3,769 | 0.02 | 1.00 / 0.64 | -56,492 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | -2,207 | 724 | 3,253 | 377 | -236 | -1,007 | -1,286 | -79 | 7,012 / 26,983 | 29,787 / 30,403 | 17,409 / -15,009 | 3,832 | 0.12 | 1.00 / 0.59 | -56,492 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_sweep8_w60 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | -3,838 | 777 | 2,750 | 664 | -222 | -497 | -1,128 | -83 | 7,116 / 26,983 | 30,351 / 30,403 | 13,246 / -15,009 | 3,580 | 0.06 | 1.00 / 0.70 | -90,296 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### K7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,257 | -1,189 | 1,452 | 303 | -825 | -1,989 | -950 | 428 | 9,922 / 26,983 | 24,227 / 30,403 | 16,254 / -15,009 | 4,360 | 0.02 | 1.00 / 0.89 | -236,127 | -660 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 20} | 1,846 | -918 | 972 | 131 | -437 | -1,216 | -287 | 464 | 10,931 / 26,983 | 16,868 / 30,403 | 20,056 / -15,009 | 980 | 0.04 | 1.00 / 0.96 | -24,485 | 557 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H_thick | {"P": [1.0, 3.0, 2.0, 1.0, 0.5, 1.0], "arm": 0.5, "feat": "t | -49 | -971 | 672 | 57 | -212 | -1,687 | -388 | -224 | 10,997 / 26,983 | 23,591 / 30,403 | 6,330 / -15,009 | 1,713 | 0.03 | 1.00 / 0.85 |  | 1,984 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H_thick | {"P": [1.0, 3.0, 2.0, 3.0, 0.1, 1.0], "arm": 0.1, "feat": "t | 607 | -668 | 348 | 117 | -680 | -946 | -813 | 222 | 11,035 / 26,983 | 29,498 / 30,403 | -8,938 / -15,009 | 1,998 | 0.09 | 1.00 / 0.72 |  | 4,854 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,417 | -681 | 1,315 | 243 | -366 | -1,292 | -244 | 480 | 11,174 / 26,983 | 17,644 / 30,403 | 23,973 / -15,009 | 692 | 0.04 | 1.00 / 0.98 | -20,444 | 56 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

## P7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 never-cut level | 37,881 | 24,670 | 15,389 | 13,115 | 8,875 | 3,042 | 6,780 | 56 | 126,710 | 131,881 | -2,075 |
| P7 LIVE REF S1b-COMB level | 5,700 | 18,966 | 12,054 | 14,708 | 10,485 | 9,564 | 5,642 | -143 | 96,490 | 106,914 | 53,844 |

### P7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | -36,486 | -5,006 | -366 | 67 | -4,829 | -6,556 | -6,922 | -1,730 | 28,821 / 126,710 | 136,378 / 131,881 | 91,355 / -2,075 | 2,699 | 0.02 | 1.00 / 0.20 | -245,934 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -30,011 | -8,640 | -3,144 | 1,808 | -3,625 | -7,612 | -5,259 | 340 | 29,833 / 126,710 | 122,164 / 131,881 | 156,101 / -2,075 | 2,228 | 0.02 | 1.00 / - |  | -533 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -28,994 | -11,799 | -6,938 | 1,104 | -4,238 | -3,518 | -6,643 | -37 | 30,461 / 126,710 | 135,681 / 131,881 | 109,593 / -2,075 | 2,741 | 0.02 | 1.00 / - |  | -14,991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -26,469 | -5,378 | -581 | 4,363 | -1,106 | -4,997 | -3,783 | -835 | 32,017 / 126,710 | 88,612 / 131,881 | 170,806 / -2,075 | 1,806 | 0.02 | 1.00 / - |  | -2,588 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_AND | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | -33,485 | -5,583 | -2,225 | 1,933 | -1,540 | 1,259 | -5,569 | 1,228 | 33,177 / 126,710 | 68,901 / 131,881 | 99,397 / -2,075 | 2,577 | 0.02 | 1.00 / - |  | -1,693 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### P7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | -1,374 | 2,098 | 3,306 | 3,856 | 1,320 | -4,372 | 2,974 | 0 | 65,090 / 126,710 | 103,880 / 131,881 | 54,856 / -2,075 | 915 | 0.04 | 1.00 / 0.98 | -135,269 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | -5,372 | -2,594 | 84 | 744 | 1,463 | 2,954 | -642 | -923 | 78,002 / 126,710 | 113,456 / 131,881 | 94,721 / -2,075 | 947 | 0.04 | 1.00 / 1.00 | -18,442 | -3,688 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | -1,026 | -195 | 1,949 | 2,099 | 2,095 | 2,551 | -720 | -544 | 79,386 / 126,710 | 114,271 / 131,881 | 93,955 / -2,075 | 947 | 0.04 | 1.00 / 1.00 | -18,442 | -6,038 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | -1,486 | -459 | 1,883 | 1,928 | 1,997 | 2,610 | -778 | -600 | 80,884 / 126,710 | 112,722 / 131,881 | 90,835 / -2,075 | 947 | 0.04 | 1.00 / 1.00 | -18,442 | -6,038 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H_thick | {"P": [1.0, 2.0, 1.3, 30.0, 0.5, 1.0], "arm": 0.5, "feat": " | 6,011 | -739 | 1,622 | 1,695 | 1,736 | 4,577 | -2,380 | -463 | 82,486 / 126,710 | 116,156 / 131,881 | 61,085 / -2,075 | 622 | 0.12 | 1.00 / 0.99 |  | -2,478 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

## M7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7 never-cut level | 406 | 2,502 | 660 | 260 | 207 | 1,989 | -254 | 29 | 43,318 | 48,984 | -68,462 |
| M7 LIVE REF S1b-COMB level | 40 | 2,251 | 278 | -823 | -930 | 965 | 402 | 86 | 46,547 | 25,812 | -64,633 |

### M7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,298 | -2,400 | -40 | 1,627 | -111 | -958 | -240 | 132 | 11,294 / 43,318 | 46,919 / 48,984 | -12,322 / -68,462 | 2,450 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,446 | 1,906 | 3,303 | 1,866 | 45 | -1,088 | 211 | 113 | 11,876 / 43,318 | 31,252 / 48,984 | -7,553 / -68,462 | 1,197 | 0.03 | 1.00 / 0.07 | -8,069 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -1,104 | -2,389 | -359 | 1,064 | -65 | -642 | -206 | -356 | 13,115 / 43,318 | 42,344 / 48,984 | -20,380 / -68,462 | 2,065 | 0.06 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 1,978 | 1,670 | 3,189 | 1,811 | -29 | -974 | 294 | 35 | 13,690 / 43,318 | 33,617 / 48,984 | -11,895 / -68,462 | 1,138 | 0.14 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 20, "blk": "A", "cancels" | -118 | 122 | 1,435 | 628 | -166 | -506 | -231 | -17 | 14,556 / 43,318 | 45,545 / 48,984 | -35,900 / -68,462 | 1,929 | 0.05 | 1.00 / 0.03 | -8,069 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### M7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 3.0, 1.3, 3.0, 0.1, 1.0], "arm": 0.1, "feat": "t | -108 | -3,016 | -468 | 1,146 | 391 | -1,304 | -78 | -1,254 | 19,558 / 43,318 | 41,987 / 48,984 | -30,085 / -68,462 | 2,422 | 0.08 | 1.00 / 0.49 |  | -1,333 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 2.0, 1.5, 1.0, 0.1, 1.0], "arm": 0.1, "feat": "t | -186 | -2,845 | -414 | 785 | -62 | -789 | -260 | -913 | 21,574 / 43,318 | 50,569 / 48,984 | -39,624 / -68,462 | 2,741 | 0.12 | 1.00 / 0.62 |  | -1,796 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,370 | -1,520 | -1,393 | 368 | 356 | -137 | 335 | -83 | 24,617 / 43,318 | 29,645 / 48,984 | -45,050 / -68,462 | 550 | 0.02 | 1.00 / 0.99 | -5,407 | -382 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,501 | -1,581 | -1,396 | 432 | 389 | -204 | 147 | -102 | 24,990 / 43,318 | 29,064 / 48,984 | -43,509 / -68,462 | 550 | 0.08 | 1.00 / 1.00 | -5,407 | -452 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | -2,625 | -1,621 | -1,529 | 301 | 269 | -175 | 212 | -102 | 26,583 / 43,318 | 34,129 / 48,984 | -48,291 / -68,462 | 550 | 0.04 | 1.00 / 1.00 | -5,407 | -939 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

## U7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7 never-cut level | -4,144 | 882 | 720 | 2,936 | 1,839 | 1,525 | 1,214 | 1,322 | 21,436 | 42,883 | 45 |
| U7 LIVE REF S1b-COMB level | -3,377 | 1,351 | 1,976 | 3,268 | 1,984 | 2,437 | 1,387 | 1,112 | 16,419 | 39,155 | 8,146 |

### U7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 2,967 | -1,050 | -654 | 650 | 531 | 1,774 | -413 | 476 | 6,204 / 21,436 | 41,216 / 42,883 | 10,054 / 45 | 842 | 0.06 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 3,789 | -1,498 | -31 | 860 | 787 | -1,245 | 67 | -1,105 | 6,611 / 21,436 | 23,521 / 42,883 | 25,888 / 45 | 794 | 0.02 | 1.00 / 0.76 | -120,053 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 3,212 | -441 | 96 | 1,206 | 702 | 535 | -367 | 419 | 6,838 / 21,436 | 36,040 / 42,883 | 26,405 / 45 | 683 | 0.03 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_r_ab8 | {"arm": 45.0, "arm_kind": "abs", "dir": 1, "feat": "r_ab8",  | 3,951 | 1,893 | 1,005 | 389 | 784 | 2,215 | 364 | 987 | 7,075 / 21,436 | 40,937 / 42,883 | 21,088 / 45 | 492 | 0.02 | 1.00 / 0.77 | -39,278 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dlt_med_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": -1, "feat": "dlt_med_ | 3,149 | -1,219 | -406 | 1,108 | 704 | 710 | -424 | 440 | 7,091 / 21,436 | 44,486 / 42,883 | 24,060 / 45 | 694 | 0.02 | 1.00 / 0.80 | -103,473 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### U7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,564 | -136 | 2,015 | 786 | 542 | -1,525 | -654 | -575 | 10,406 / 21,436 | 38,921 / 42,883 | 20,186 / 45 | 846 | 0.03 | 1.00 / 0.99 | -54,239 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| K1_target | {"m": 0.75} | 2,249 | -1,892 | 1,000 | 294 | 182 | -1,458 | -63 | -451 | 10,576 / 21,436 | 21,039 / 42,883 | 18,548 / 45 | 829 | 0.04 | 1.00 / 0.98 | -54,933 | -2,110 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "hold"} | 2,845 | -183 | 1,038 | 255 | 247 | -1,168 | -178 | -276 | 11,056 / 21,436 | 23,979 / 42,883 | 17,279 / 45 | 1,143 | 0.04 | 1.00 / 0.98 | -35,428 | -1,990 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 2, "p": 0.7, "rest": "trail", "x": 20} | 4,925 | -1,142 | 1,600 | 677 | 695 | -18 | -412 | -210 | 11,142 / 21,436 | 30,968 / 42,883 | 22,632 / 45 | 1,143 | 0.08 | 1.00 / 0.99 | -35,428 | -1,085 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | 3,409 | -1,646 | 1,151 | 477 | 513 | -1,195 | -238 | -229 | 11,565 / 21,436 | 25,905 / 42,883 | 19,632 / 45 | 1,143 | 0.02 | 1.00 / 0.99 | -35,428 | -1,990 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

## A7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 never-cut level | 394 | -104 | -96 | 596 | 562 | 244 | 946 | 234 | 12,456 | 6,208 | -17,012 |
| A7 LIVE REF S1b-COMB level | -1,287 | 217 | 169 | 821 | 731 | 430 | 882 | 268 | 8,518 | 7,325 | -11,915 |

### A7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -938 | 811 | 484 | 234 | 159 | 668 | -275 | 86 | 4,410 / 12,456 | 5,886 / 6,208 | -10,266 / -17,012 | 574 | 0.06 | 1.00 / - |  | 529 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -938 | 811 | 484 | 234 | 159 | 668 | -275 | 86 | 4,410 / 12,456 | 5,886 / 6,208 | -10,266 / -17,012 | 574 | 0.05 | 1.00 / - |  | 529 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -938 | 811 | 495 | 209 | 125 | 618 | -271 | 79 | 4,410 / 12,456 | 5,886 / 6,208 | -10,891 / -17,012 | 556 | 0.08 | 1.00 / 0.35 | -68,429 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -554 | 889 | 345 | 324 | -140 | -400 | -192 | 94 | 4,561 / 12,456 | 5,999 / 6,208 | -8,910 / -17,012 | 560 | 0.02 | 1.00 / 0.36 | -68,429 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -522 | 751 | 366 | 442 | 34 | 305 | -226 | -61 | 4,616 / 12,456 | 5,306 / 6,208 | -9,388 / -17,012 | 441 | 0.02 | 1.00 / 0.38 | -68,429 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### A7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 0.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 140 | -819 | 6 | 6 | -188 | 137 | -511 | 33 | 4,562 / 12,456 | 5,931 / 6,208 | -4,332 / -17,012 | 879 | 0.02 | 1.00 / 0.41 | -48,392 | -921 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 3.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 34 | -867 | 54 | 77 | -226 | 94 | -358 | 61 | 5,248 / 12,456 | 4,081 / 6,208 | -4,555 / -17,012 | 855 | 0.02 | 1.00 / 0.44 |  | -160 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 2.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | -588 | -1,144 | -99 | 5 | -200 | 187 | -506 | 127 | 5,501 / 12,456 | 6,101 / 6,208 | -3,922 / -17,012 | 881 | 0.02 | 1.00 / 0.49 |  | -115 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 1.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 389 | -712 | 159 | 56 | -113 | 355 | -378 | 12 | 5,934 / 12,456 | 4,515 / 6,208 | -4,007 / -17,012 | 863 | 0.03 | 1.00 / 0.51 |  | -696 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["d_pd_ahead", "d_or_ahe | 166 | -222 | 242 | 240 | 252 | 73 | 16 | 0 | 7,737 / 12,456 | 6,183 / 6,208 | -13,630 / -17,012 | 265 | 0.76 | 1.00 / 0.73 | -5,922 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

## H7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7 never-cut level | -58 | 1,928 | -302 | 1,933 | 169 | -2,206 | 1,688 | 463 | 16,682 | 20,667 | -36,140 |
| H7 LIVE REF S1b-COMB level | 3,186 | 1,572 | 682 | 2,840 | 770 | -1,655 | 1,574 | 431 | 8,818 | 19,256 | 11,007 |

### H7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 866 | 1,336 | 1,140 | 1,025 | 864 | 1,136 | -153 | -134 | 4,733 / 16,682 | 13,517 / 20,667 | -267 / -36,140 | 362 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,880 | 1,062 | 1,034 | 1,311 | 932 | 1,703 | -140 | -63 | 4,769 / 16,682 | 13,517 / 20,667 | 11,605 / -36,140 | 379 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,066 | 321 | 1,153 | 1,262 | 868 | 743 | -154 | -22 | 5,354 / 16,682 | 15,643 / 20,667 | 3,826 / -36,140 | 338 | 0.02 | 1.00 / 0.68 | -34,370 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | -475 | 313 | 269 | 593 | 782 | 907 | -31 | 417 | 5,606 / 16,682 | 12,568 / 20,667 | 18 / -36,140 | 477 | 0.02 | 1.00 / 0.40 | -8,304 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "adv_best | 197 | 84 | -110 | 366 | 765 | 596 | -105 | 137 | 5,637 / 16,682 | 19,423 / 20,667 | -6,645 / -36,140 | 496 | 0.02 | 1.00 / 0.25 | -21,775 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### H7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 0.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 2,523 | 1,088 | 2,016 | 432 | 581 | -206 | -517 | -349 | 6,546 / 16,682 | 9,332 / 20,667 | 6,057 / -36,140 | 800 | 0.02 | 1.00 / 0.40 | -82,134 | 2,406 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 0.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 2,175 | 851 | 1,821 | 240 | 482 | -355 | -563 | -467 | 6,579 / 16,682 | 9,387 / 20,667 | 4,092 / -36,140 | 824 | 0.02 | 1.00 / 0.34 | -82,134 | 2,216 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 2.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 2,459 | 1,017 | 1,936 | 205 | 577 | -429 | -567 | -379 | 7,318 / 16,682 | 9,187 / 20,667 | 1,600 / -36,140 | 803 | 0.03 | 1.00 / 0.40 |  | 2,296 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 1.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 2,794 | 1,229 | 2,061 | 329 | 510 | 42 | -431 | -330 | 7,370 / 16,682 | 9,162 / 20,667 | 1,628 / -36,140 | 787 | 0.02 | 1.00 / 0.45 |  | 3,082 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| K1_target | {"m": 0.5} | 1,205 | 747 | 1,478 | 805 | 653 | -392 | -678 | -522 | 7,803 / 16,682 | 12,070 / 20,667 | 5,401 / -36,140 | 762 | 0.02 | 1.00 / 0.73 | -59,397 | 3,175 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

## O7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 never-cut level | -667 | -41 | -60 | 285 | 706 | 149 | 625 | -119 | 7,489 | 5,097 | -9,447 |
| O7 LIVE REF S1b-COMB level | -988 | -93 | 115 | 331 | 673 | -55 | 635 | -147 | 6,656 | 4,532 | -8,247 |

### O7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 551 | -26 | -61 | 123 | -175 | 299 | -379 | 97 | 3,323 / 7,489 | 5,345 / 5,097 | -2,066 / -9,447 | 414 | 0.03 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 321 | 309 | 118 | 27 | -313 | 123 | -467 | 165 | 3,453 / 7,489 | 4,701 / 5,097 | -4,822 / -9,447 | 449 | 0.17 | 1.00 / 0.36 | -4,547 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 321 | 309 | 118 | 27 | -311 | 123 | -467 | 152 | 3,453 / 7,489 | 4,701 / 5,097 | -4,822 / -9,447 | 452 | 0.09 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 321 | 309 | 118 | 27 | -313 | 123 | -467 | 165 | 3,453 / 7,489 | 4,701 / 5,097 | -4,822 / -9,447 | 449 | 0.09 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 321 | 309 | 118 | 20 | -315 | 123 | -465 | 178 | 3,453 / 7,489 | 4,417 / 5,097 | -5,010 / -9,447 | 452 | 0.09 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### O7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 3.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 728 | 205 | 286 | 260 | -151 | -201 | -474 | 85 | 4,455 / 7,489 | 4,960 / 5,097 | -1,707 / -9,447 | 299 | 0.05 | 1.00 / 0.92 |  | 636 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,191 | 372 | 462 | 24 | -187 | 89 | -56 | -31 | 5,612 / 7,489 | 3,915 / 5,097 | -2,601 / -9,447 | 151 | 0.08 | 1.00 / 0.98 | -636 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,191 | 372 | 462 | 24 | -187 | 89 | -56 | -31 | 5,612 / 7,489 | 3,915 / 5,097 | -2,601 / -9,447 | 151 | 0.02 | 1.00 / 0.98 | -636 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | 1,131 | 518 | 530 | 26 | -253 | -44 | 5 | 0 | 5,812 / 7,489 | 3,914 / 5,097 | -3,862 / -9,447 | 129 | 0.08 | 1.00 / 0.98 | -636 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | 1,131 | 518 | 530 | 26 | -253 | -44 | 5 | 0 | 5,812 / 7,489 | 3,914 / 5,097 | -3,862 / -9,447 | 129 | 0.12 | 1.00 / 0.98 | -636 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

## X3
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X3 never-cut level | -166 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 664 | 0 | -664 |
| X3 LIVE REF S1b-COMB level | -448 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1,794 | 0 | -1,794 |

### X3 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 30, "arm": "fixed", "armval": 30, "blk": "A", "cancels | 211 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.46 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 35, "blk": "A", "cancels" | 541 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 0.52 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 207 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.54 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 458 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.55 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 35, "blk": "A", "cancels | 343 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.55 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### X3 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K2_atrtarget | {"c": 6} | 393 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| K1_target | {"m": 1.1} | 120 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 184 / 664 | 0 / 0 | -184 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| J1_scale | {"p": 0.9, "rest": "hold"} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.80 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.9, "rest": "trail", "x": 20} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.96 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"b": 2, "p": 0.9, "rest": "be"} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.88 | 1.00 / - |  | 0 | S1 | no |

## X4
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X4 never-cut level | 1,195 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X4 LIVE REF S1b-COMB level | 795 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X4 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -853 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -897 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -884 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 20, "blk": "A", "cancels | -842 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -899 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |

### X4 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 0.0, 1.3, 1.0, 0.5, 1.0], "arm": 0.5, "feat": "a | -594 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  | -327 | S1 | no |
| H_thick | {"P": [1.0, 0.0, 2.0, 1.0, 0.75, 1.0], "arm": 0.75, "feat":  | -271 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| H_thick | {"P": [1.0, 0.0, 1.3, 10.0, 0.5, 1.0], "arm": 0.5, "feat": " | -234 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| H_thick | {"P": [1.0, 0.0, 1.3, 3.0, 0.5, 1.0], "arm": 0.5, "feat": "a | -561 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  | -157 | S1 | no |
| H_thick | {"P": [1.0, 0.0, 1.3, 1.0, 0.75, 1.0], "arm": 0.75, "feat":  | -326 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  | 0 | S1 | no |

## X5
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X5 never-cut level | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X5 LIVE REF S1b-COMB level | 95 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X5 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 25, "blk": "A", "cancels | 276 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | 232 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 30, "blk": "A", "cancels | 232 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 389 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 35, "blk": "A", "cancels" | 224 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |

### X5 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 1.1} | 60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.6, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| J3_statescale | {"a": 0.4, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| J1_scale | {"p": 0.9, "rest": "hold"} | -30 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 69 / 0 | 0 / 0 | -69 / 0 | 1 | 0.52 | 1.00 / - |  |  | S1 | no |

## Survivors per book (CANDIDATE-DD and rec-ok and plc-ok and not FAILS-LIVE-WEEK; wf shown, not required; top 3 by drawdown-first)
### ALL survivors (475 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -35,997 | -4,815 | 3,055 | 677 | -4,057 | -6,204 | -10,503 | -1,219 | 32,689 / 117,593 | 174,715 / 177,634 | 145,488 / 89,449 | 10,540 | 0.02 | 1.00 / - |  | -13,072 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | -41,715 | -13,374 | -4,031 | 2,988 | -651 | 2,107 | -11,416 | -43 | 33,012 / 117,593 | 102,045 / 177,634 | 172,308 / 89,449 | 11,639 | 0.02 | 1.00 / - |  | -16,805 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -26,953 | -5,524 | 4,410 | 2,814 | -1,451 | -601 | -8,244 | -535 | 33,652 / 117,593 | 125,311 / 177,634 | 244,699 / 89,449 | 6,302 | 0.05 | 1.00 / - |  | -15,136 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 survivors (117 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -3,000 | -47 | 2,951 | 449 | -456 | 2,063 | -1,292 | -299 | 5,160 / 26,983 | 21,469 / 30,403 | 18,128 / -15,009 | 4,209 | 0.05 | 1.00 / - |  | 3,225 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,978 | 3,833 | 5,163 | 2,076 | 208 | 146 | -689 | 104 | 5,501 / 26,983 | 24,135 / 30,403 | 44,481 / -15,009 | 3,439 | 0.02 | 1.00 / - |  | 2,830 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | -3,357 | 666 | 3,418 | 654 | -159 | -1,045 | -1,233 | -63 | 6,384 / 26,983 | 28,853 / 30,403 | 23,584 / -15,009 | 3,769 | 0.02 | 1.00 / 0.64 | -56,492 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### P7 survivors (555 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w30 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | -36,486 | -5,006 | -366 | 67 | -4,829 | -6,556 | -6,922 | -1,730 | 28,821 / 126,710 | 136,378 / 131,881 | 91,355 / -2,075 | 2,699 | 0.02 | 1.00 / 0.20 | -245,934 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -30,011 | -8,640 | -3,144 | 1,808 | -3,625 | -7,612 | -5,259 | 340 | 29,833 / 126,710 | 122,164 / 131,881 | 156,101 / -2,075 | 2,228 | 0.02 | 1.00 / - |  | -533 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -28,994 | -11,799 | -6,938 | 1,104 | -4,238 | -3,518 | -6,643 | -37 | 30,461 / 126,710 | 135,681 / 131,881 | 109,593 / -2,075 | 2,741 | 0.02 | 1.00 / - |  | -14,991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### M7 survivors (428 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,298 | -2,400 | -40 | 1,627 | -111 | -958 | -240 | 132 | 11,294 / 43,318 | 46,919 / 48,984 | -12,322 / -68,462 | 2,450 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,446 | 1,906 | 3,303 | 1,866 | 45 | -1,088 | 211 | 113 | 11,876 / 43,318 | 31,252 / 48,984 | -7,553 / -68,462 | 1,197 | 0.03 | 1.00 / 0.07 | -8,069 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_AND | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -1,104 | -2,389 | -359 | 1,064 | -65 | -642 | -206 | -356 | 13,115 / 43,318 | 42,344 / 48,984 | -20,380 / -68,462 | 2,065 | 0.06 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### U7 survivors (159 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 2,967 | -1,050 | -654 | 650 | 531 | 1,774 | -413 | 476 | 6,204 / 21,436 | 41,216 / 42,883 | 10,054 / 45 | 842 | 0.06 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 3,789 | -1,498 | -31 | 860 | 787 | -1,245 | 67 | -1,105 | 6,611 / 21,436 | 23,521 / 42,883 | 25,888 / 45 | 794 | 0.02 | 1.00 / 0.76 | -120,053 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_AND | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 3,212 | -441 | 96 | 1,206 | 702 | 535 | -367 | 419 | 6,838 / 21,436 | 36,040 / 42,883 | 26,405 / 45 | 683 | 0.03 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### A7 survivors (300 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -938 | 811 | 484 | 234 | 159 | 668 | -275 | 86 | 4,410 / 12,456 | 5,886 / 6,208 | -10,266 / -17,012 | 574 | 0.06 | 1.00 / - |  | 529 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | -938 | 811 | 484 | 234 | 159 | 668 | -275 | 86 | 4,410 / 12,456 | 5,886 / 6,208 | -10,266 / -17,012 | 574 | 0.05 | 1.00 / - |  | 529 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 2, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -938 | 811 | 495 | 209 | 125 | 618 | -271 | 79 | 4,410 / 12,456 | 5,886 / 6,208 | -10,891 / -17,012 | 556 | 0.08 | 1.00 / 0.35 | -68,429 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### H7 survivors (258 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 866 | 1,336 | 1,140 | 1,025 | 864 | 1,136 | -153 | -134 | 4,733 / 16,682 | 13,517 / 20,667 | -267 / -36,140 | 362 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 1,880 | 1,062 | 1,034 | 1,311 | 932 | 1,703 | -140 | -63 | 4,769 / 16,682 | 13,517 / 20,667 | 11,605 / -36,140 | 379 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,066 | 321 | 1,153 | 1,262 | 868 | 743 | -154 | -22 | 5,354 / 16,682 | 15,643 / 20,667 | 3,826 / -36,140 | 338 | 0.02 | 1.00 / 0.68 | -34,370 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### O7 survivors (219 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G_OR | {"fams": ["A", "B_book"], "note": "sticky combination of sin | 551 | -26 | -61 | 123 | -175 | 299 | -379 | 97 | 3,323 / 7,489 | 5,345 / 5,097 | -2,066 / -9,447 | 414 | 0.03 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 321 | 309 | 118 | 27 | -311 | 123 | -467 | 152 | 3,453 / 7,489 | 4,701 / 5,097 | -4,822 / -9,447 | 452 | 0.09 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| G_OR | {"fams": ["A", "C_flow"], "note": "sticky combination of sin | 321 | 309 | 118 | 27 | -313 | 123 | -467 | 165 | 3,453 / 7,489 | 4,701 / 5,097 | -4,822 / -9,447 | 449 | 0.09 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### X3 survivors (1 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 55, "k": 2} | 164 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 9 / 664 | 0 / 0 | -9 / -664 | 1 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

- X4: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)
- X5: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)

## Walk-forward of the picking procedure (all cells of a book/side; purged monthly, 7-day embargo, trailing 26 weeks, key = maxDD, worst-20, Ulcer, -mean)
| book   | side   |   ncells |   total |   dd_never |   dd_wf |   share_pos |   npick |   months | wf_ok   |
|:-------|:-------|---------:|--------:|-----------:|--------:|------------:|--------:|---------:|:--------|
| ALL    | loss   |     4467 | -888119 |     177634 |  207259 |           0 |      35 |       35 | False   |
| ALL    | profit |      645 | -259737 |     177634 |  173159 |           0 |      35 |       35 | False   |
| K7     | loss   |     4033 | -148987 |      51147 |   37726 |           0 |      35 |       35 | False   |
| K7     | profit |      559 | -106426 |      51147 |   77800 |           0 |      35 |       35 | False   |
| P7     | loss   |     4078 | -580222 |     142472 |  208287 |           0 |      35 |       35 | False   |
| P7     | profit |      635 | -368711 |     142472 |  160566 |           0 |      35 |       35 | False   |
| M7     | loss   |     3941 |   29713 |      67465 |   32796 |           1 |      35 |       35 | True    |
| M7     | profit |      520 |  -43513 |      67465 |   63645 |           0 |      35 |       35 | False   |
| U7     | loss   |     3779 |  -31967 |      42883 |   33074 |           0 |      35 |       35 | False   |
| U7     | profit |      590 | -155492 |      42883 |   70931 |           0 |      35 |       35 | False   |
| A7     | loss   |     3727 |  -69796 |      14132 |   16127 |           0 |      35 |       35 | False   |
| A7     | profit |      203 |  -49596 |      14132 |   38427 |           0 |      35 |       35 | False   |
| H7     | loss   |     3717 |  -66229 |      54450 |   38982 |           1 |      35 |       35 | False   |
| H7     | profit |      535 |  -45225 |      54450 |   31728 |           0 |      35 |       35 | False   |
| O7     | loss   |     2852 |  -51080 |       7489 |    7438 |           0 |      35 |       35 | False   |
| O7     | profit |      166 |  -31454 |       7489 |    7489 |           0 |      35 |       35 | False   |

## Stack view and one rule for all books (first-order, IN-SAMPLE best-of-thousands picks per book: read them against the walk-forward table above, which is negative for almost every book/side)
Per-book picks stacked: L6M maxDD 23,344 vs never-cut 117,593; PRE maxDD 150,873 vs 177,634; L6M dmean 5,841. Best single cell on all books: G_OR ({"fams": ["A", "B_book"], "note": "sticky combinat), L6M maxDD 32,689, dmean 677.

## Plain sentences
- ALL loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["a0e786835d91", "02b6f4d55147"]}); L6M maxDD 32,689 vs 117,593 never-cut (-84,904); it costs 2,101 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- ALL profit: the technique that lowers drawdown most is L1_cond ({"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech": "J1_scale", "cond": "atr_mid"}); L6M maxDD 68,059 vs 117,593 never-cut (-49,534); it earns 7,116 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["55462e9fab3f", "cd3f0c8f96d5"]}); L6M maxDD 5,160 vs 26,983 never-cut (-21,823); it costs 251 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- K7 profit: the technique that lowers drawdown most is K1_target ({"m": 0.5}); L6M maxDD 9,922 vs 26,983 never-cut (-17,060); it costs 398 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 loss: the technique that lowers drawdown most is LBC_sweep8_w30 ({"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w30", "mode": "latch", "months": "202304-202611(44)", "pers": 8, "thr": 4.0}); L6M maxDD 28,821 vs 126,710 never-cut (-97,890); it costs 1,526 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 profit: the technique that lowers drawdown most is L3_tree_profit ({"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d_or_ahead", "k"], "first_test": 202502, "leaves": 8, "seed": 1, "tau": 0.0}); L6M maxDD 65,090 vs 126,710 never-cut (-61,620); it earns 7,849 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- M7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["55462e9fab3f", "4fdbf5914108"]}); L6M maxDD 11,294 vs 43,318 never-cut (-32,024); it earns 2,277 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- M7 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 3.0, 1.3, 3.0, 0.1, 1.0], "arm": 0.1, "feat": "tot_rel_slow", "secs": 3, "thr": 1.3}); L6M maxDD 19,558 vs 43,318 never-cut (-23,761); it earns 1,795 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- U7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "C_flow"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["3d852783ada6", "10c66fe5e3fc"]}); L6M maxDD 6,204 vs 21,436 never-cut (-15,232); it earns 434 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- U7 profit: the technique that lowers drawdown most is X2_target_trail ({"arm": 0.7, "m": 2, "x": 20}); L6M maxDD 10,406 vs 21,436 never-cut (-11,030); it earns 689 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["503ce144003c", "6e114e4ea813"]}); L6M maxDD 4,410 vs 12,456 never-cut (-8,046); it earns 9 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- A7 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 0.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat": "ahead_rel_fast", "secs": 1, "thr": 1.5}); L6M maxDD 4,562 vs 12,456 never-cut (-7,893); it costs 28 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["a0e786835d91", "2170e73cc6ab"]}); L6M maxDD 4,733 vs 16,682 never-cut (-11,949); it costs 335 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- H7 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 0.0, 1.5, 1.0, 0.25, 1.0], "arm": 0.25, "feat": "ahead_rel_fast", "secs": 1, "thr": 1.5}); L6M maxDD 6,546 vs 16,682 never-cut (-10,135); it costs 927 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- O7 loss: the technique that lowers drawdown most is G_OR ({"fams": ["A", "B_book"], "note": "sticky combination of single-rule fire legs (per-trade out files)", "rules": ["145ef7bf3f99", "a44a782bd01b"]}); L6M maxDD 3,323 vs 7,489 never-cut (-4,166); it earns 74 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- O7 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 3.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat": "tot_rel_slow", "secs": 1, "thr": 1.3}); L6M maxDD 4,455 vs 7,489 never-cut (-3,034); it earns 212 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 loss: the technique that lowers drawdown most is A_pulled ({"W": 30, "arm": "fixed", "armval": 30, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 120, "newmae": 0, "pers": 1, "pulled": "own"}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.46, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 profit: the technique that lowers drawdown most is K2_atrtarget ({"c": 6}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X4 loss: the technique that lowers drawdown most is A_pulled ({"W": 15, "arm": "fixed", "armval": 25, "blk": "A", "cancels": "net", "maeW": 15, "med": "e001", "mult": 2, "newmae": 1, "pers": 2, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X4 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 0.0, 1.3, 1.0, 0.5, 1.0], "arm": 0.5, "feat": "ahead_rel_fast", "secs": 1, "thr": 1.3}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 loss: the technique that lowers drawdown most is A_pulled ({"W": 15, "arm": "fixed", "armval": 25, "blk": "A", "cancels": "net", "maeW": 15, "med": "e001", "mult": 2, "newmae": 1, "pers": 2, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 profit: the technique that lowers drawdown most is K1_target ({"m": 1.1}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.

---
universe U1: U1 mixed (screen-only) shown; U2 = full S1b tick-close never-cut (43 months) is built, U2 cells so far: 1
