# EXH_JKL - profit families J (scale), K (target), L (crosses) - 2026-11-09 03:29Z
PRE-PROOF (entries not live-matched). 560 cells scored, all registered in the ledger (agent ex-pjkl). Stage 1 first-order on the EX-CORE universe; target cells (K, X) walk the NEW target over paths extended to the flat time (no unresolved trades; 5 months of EX-FEAT panels with a length mismatch make feature rules inert on 91 trades). Deltas are USD/week vs never-cut (hold-to-bracket), carrying week dropped; "w/wo" = with rule / without. WF = purged monthly walk-forward (not yet run for this family unless shown). Placebo for target cells = the cell's own per-trade deltas re-assigned to other trades of the same book (no decision second exists). Prereg autopilot/EXH_JKL_PREREG.md.


## ALL  (never-cut L6M weekly mean 29,606, maxDD L6M 117,593, PRE 177,634; LIVE REF S1b-COMB mean 25,828, maxDD L6M 82,873, PRE 144,002)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | -7,244 | -7,942 | 916 | 872 | 2,092 | 9,715 | -3,872 | 612 | 33,979 / 117,593 | 109,134 / 177,634 | 203,176 / 89,449 | 7,744 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 1.25, "p": 0.7, "rest": "trail", "x": 20} | -8,074 | -7,930 | 774 | 1,151 | 1,819 | 8,239 | -3,962 | 1,373 | 36,023 / 117,593 | 98,591 / 177,634 | 188,455 / 89,449 | 7,744 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.7, "rest": "trail", "x": 20} | -7,216 | -6,694 | 1,650 | 2,179 | 1,896 | 8,322 | -3,782 | 961 | 37,957 / 117,593 | 105,125 / 177,634 | 206,636 / 89,449 | 4,714 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 1.5, "p": 0.7, "rest": "trail", "x": 20} | -7,111 | -7,430 | 924 | 985 | 1,449 | 6,878 | -4,026 | 1,106 | 39,598 / 117,593 | 88,452 / 177,634 | 180,955 / 89,449 | 7,744 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.6, "rest": "trail", "x": 5} | -4,646 | -4,401 | 3,365 | -6,533 | -3,907 | -1,754 | -4,707 | 249 | 31,163 / 117,593 | 92,676 / 177,634 | 215,711 / 89,449 | 5,030 | 0.040 | 1.000 | no/not run |  | no |
| J1_scale | {"p": 0.6, "rest": "trail", "x": 10} | -4,552 | -4,257 | 2,829 | -6,535 | -3,917 | -1,950 | -4,597 | 60 | 31,888 / 117,593 | 93,522 / 177,634 | 204,745 / 89,449 | 5,030 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 4 | K1_target | {"m": 0.5} | 90 | 2,312 / 6,324 | 23,228 / 39,576 | 742 | CANDIDATE-DD |
| 3 | J2_thirds | {"p1": 0.3, "p2": 0.7, "rest": "trail", "x": 10} | 1,849 | 40,462 / 95,475 | 25,615 / 58,409 | 648 | CANDIDATE-DD |
| 0 | L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 36 | 60,474 / 98,954 | 57,132 / 94,157 | 1,753 | CANDIDATE-DD |
| 1 | L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 1,635 | 66,004 / 83,177 | 159,625 / 168,851 | 805 | CANDIDATE-DD |

## K7  (never-cut L6M weekly mean 3,501, maxDD L6M 26,983, PRE 30,403; LIVE REF S1b-COMB mean 3,764, maxDD L6M 41,849, PRE 23,073)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,257 | -1,189 | 1,452 | 303 | -825 | -1,989 | -950 | 428 | 9,922 / 26,983 | 24,227 / 30,403 | 16,254 / -15,009 | 4,360 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 20} | 1,846 | -918 | 972 | 131 | -437 | -1,216 | -287 | 464 | 10,931 / 26,983 | 16,868 / 30,403 | 20,056 / -15,009 | 980 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,417 | -681 | 1,315 | 243 | -366 | -1,292 | -244 | 480 | 11,174 / 26,983 | 17,644 / 30,403 | 23,973 / -15,009 | 692 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5,  | 1,725 | 723 | 2,019 | 836 | 223 | 890 | -500 | 390 | 11,251 / 26,983 | 20,936 / 30,403 | 3,538 / -15,009 | 642 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 2,082 | -1,391 | 1,467 | -324 | -994 | -3,492 | -1,106 | -54 | 9,258 / 26,983 | 31,636 / 30,403 | 22,442 / -15,009 | 4,076 | 0.040 | 1.000 | no/not run |  | no |
| K1_target | {"m": 0.5} | 1,257 | -1,189 | 1,452 | 303 | -825 | -1,989 | -950 | 428 | 9,922 / 26,983 | 24,227 / 30,403 | 16,254 / -15,009 | 4,360 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 4 | K1_target | {"m": 0.5} | 90 | 2,312 / 6,324 | 23,228 / 39,576 | 742 | CANDIDATE-DD |
| 3 | X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 20} | 161 | 5,804 / 20,697 | 11,487 / 6,231 | 1,016 | LEAD |
| 1 | K4_extend | {"a": 0.9, "f": "ahead_rel_slow", "m": 2, "th": 0.5} | 97 | 12,369 / 13,569 | 17,018 / 16,206 | 50 | no |
| 0 | J1_scale | {"p": 0.6, "rest": "trail", "x": 5} | 1,019 | 13,943 / 23,228 | 17,679 / 14,762 | 329 | LEAD |

## P7  (never-cut L6M weekly mean 20,723, maxDD L6M 126,710, PRE 131,881; LIVE REF S1b-COMB mean 16,403, maxDD L6M 96,490, PRE 106,914)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech": "J1_scale" | -5,372 | -2,594 | 84 | 744 | 1,463 | 2,954 | -642 | -923 | 78,002 / 126,710 | 113,456 / 131,881 | 94,721 / -2,075 | 947 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_scale", "c | -1,026 | -195 | 1,949 | 2,099 | 2,095 | 2,551 | -720 | -544 | 79,386 / 126,710 | 114,271 / 131,881 | 93,955 / -2,075 | 947 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_scale", "c | -1,486 | -459 | 1,883 | 1,928 | 1,997 | 2,610 | -778 | -600 | 80,884 / 126,710 | 112,722 / 131,881 | 90,835 / -2,075 | 947 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| L1_cond | {"base": {"a": 0.4, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "t | -4,072 | -2,237 | 188 | 410 | -431 | -3,133 | -855 | -275 | 85,718 / 126,710 | 133,234 / 131,881 | 12,091 / -2,075 | 220 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 40} | -24,965 | -14,919 | -8,873 | -2,902 | -3,925 | 1,291 | -4,239 | 465 | 71,202 / 126,710 | 72,798 / 131,881 | 30,937 / -2,075 | 3,479 | 0.040 | 1.000 | no/not run |  | no |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "hold"} | -10,767 | -8,845 | -3,102 | -2,706 | -1,501 | -371 | -2,579 | 14 | 77,040 / 126,710 | 76,694 / 131,881 | 12,655 / -2,075 | 4,394 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | 2,073 | 33,890 / 103,128 | 33,436 / 75,038 | 757 | CANDIDATE-DD |
| 1 | K4_extend | {"a": 0.7, "f": "ahead_rel_slow", "m": 1.5, "th": 0.5} | 1,430 | 34,670 / 44,287 | 113,904 / 160,840 | 210 | CANDIDATE-DD |
| 0 | L1_cond | {"base": {"a": 0.4, "f": "ahead_rel_slow", "rest": "trail",  | 2,085 | 83,894 / 106,637 | 87,550 / 78,845 | 91 | LEAD |

## M7  (never-cut L6M weekly mean 369, maxDD L6M 43,318, PRE 48,984; LIVE REF S1b-COMB mean -581, maxDD L6M 46,547, PRE 25,812)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,370 | -1,520 | -1,393 | 368 | 356 | -137 | 335 | -83 | 24,617 / 43,318 | 29,645 / 48,984 | -45,050 / -68,462 | 550 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,501 | -1,581 | -1,396 | 432 | 389 | -204 | 147 | -102 | 24,990 / 43,318 | 29,064 / 48,984 | -43,509 / -68,462 | 550 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | -2,625 | -1,621 | -1,529 | 301 | 269 | -175 | 212 | -102 | 26,583 / 43,318 | 34,129 / 48,984 | -48,291 / -68,462 | 550 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.6, "rest": "trail", "x": 10} | -1,198 | -746 | 104 | 525 | 515 | -651 | -124 | 72 | 27,863 / 43,318 | 40,534 / 48,984 | -43,414 / -68,462 | 442 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,370 | -1,520 | -1,393 | 368 | 356 | -137 | 335 | -83 | 24,617 / 43,318 | 29,645 / 48,984 | -45,050 / -68,462 | 550 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,501 | -1,581 | -1,396 | 432 | 389 | -204 | 147 | -102 | 24,990 / 43,318 | 29,064 / 48,984 | -43,509 / -68,462 | 550 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | K1_target | {"m": 0.75} | 113 | 9,276 / 12,246 | 9,918 / 7,533 | 886 | LEAD |
| 1 | L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 491 | 24,243 / 34,745 | 68,495 / 70,941 | 174 | CANDIDATE-DD |

## U7  (never-cut L6M weekly mean 2,927, maxDD L6M 21,436, PRE 42,883; LIVE REF S1b-COMB mean 3,041, maxDD L6M 16,419, PRE 39,155)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,564 | -136 | 2,015 | 786 | 542 | -1,525 | -654 | -575 | 10,406 / 21,436 | 38,921 / 42,883 | 20,186 / 45 | 846 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| K1_target | {"m": 0.75} | 2,249 | -1,892 | 1,000 | 294 | 182 | -1,458 | -63 | -451 | 10,576 / 21,436 | 21,039 / 42,883 | 18,548 / 45 | 829 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "hold"} | 2,845 | -183 | 1,038 | 255 | 247 | -1,168 | -178 | -276 | 11,056 / 21,436 | 23,979 / 42,883 | 17,279 / 45 | 1,143 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 2, "p": 0.7, "rest": "trail", "x": 20} | 4,925 | -1,142 | 1,600 | 677 | 695 | -18 | -412 | -210 | 11,142 / 21,436 | 30,968 / 42,883 | 22,632 / 45 | 1,143 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | 4,032 | -2,055 | -1,235 | -1,296 | -339 | 344 | -1,679 | -271 | 8,956 / 21,436 | 55,971 / 42,883 | 7,700 / 45 | 905 | 0.040 | 1.000 | no/not run |  | no |
| J1_scale | {"b": 0, "p": 0.3, "rest": "be"} | 3,622 | -2,038 | -1,118 | -107 | -253 | 20 | -1,567 | -345 | 9,086 / 21,436 | 53,758 / 42,883 | 11,936 / 45 | 905 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 0 | L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 237 | 5,897 / 9,836 | 22,862 / 31,041 | 230 | CANDIDATE-DD |
| 1 | J1_scale | {"p": 0.3, "rest": "trail", "x": 40} | 451 | 15,411 / 33,738 | 47,663 / 39,568 | 423 | LEAD |

## A7  (never-cut L6M weekly mean 488, maxDD L6M 12,456, PRE 6,208; LIVE REF S1b-COMB mean 521, maxDD L6M 8,518, PRE 7,325)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d_or_ahead" | 407 | -6 | 37 | 101 | -115 | -196 | 47 | 0 | 8,053 / 12,456 | 6,183 / 6,208 | -18,000 / -17,012 | 255 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | -1,149 | -81 | -54 | 107 | 68 | -243 | -13 | 0 | 10,787 / 12,456 | 6,183 / 6,208 | -16,096 / -17,012 | 21 | 0.120 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | -1,149 | -81 | -54 | 107 | 68 | -243 | -13 | 0 | 10,787 / 12,456 | 6,183 / 6,208 | -16,096 / -17,012 | 21 | 0.120 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | -1,036 | -173 | -115 | 20 | 15 | -12 | -12 | 0 | 10,919 / 12,456 | 6,183 / 6,208 | -16,630 / -17,012 | 31 | 0.160 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,106 | -999 | -577 | -2 | -261 | -295 | -165 | -180 | 5,688 / 12,456 | 4,907 / 6,208 | -4,853 / -17,012 | 777 | 0.040 | 1.000 | no/not run |  | no |
| K1_target | {"m": 0.5} | 46 | -1,769 | -824 | -436 | -303 | -586 | -40 | -139 | 7,055 / 12,456 | 4,259 / 6,208 | -9,208 / -17,012 | 832 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 0 | L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 101 | 8,053 / 12,456 | 6,183 / 6,208 | 255 | CANDIDATE-DD |

## H7  (never-cut L6M weekly mean 744, maxDD L6M 16,682, PRE 20,667; LIVE REF S1b-COMB mean 2,103, maxDD L6M 8,818, PRE 19,256)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,205 | 747 | 1,478 | 805 | 653 | -392 | -678 | -522 | 7,803 / 16,682 | 12,070 / 20,667 | 5,401 / -36,140 | 762 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,410 | 740 | 1,339 | 476 | 300 | -531 | -570 | -319 | 8,536 / 16,682 | 14,267 / 20,667 | -1,071 / -36,140 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 10} | 1,410 | 740 | 1,339 | 476 | 292 | -538 | -631 | -328 | 8,536 / 16,682 | 14,501 / 20,667 | -1,071 / -36,140 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 10} | 1,410 | 740 | 1,339 | 476 | 295 | -531 | -505 | -331 | 8,536 / 16,682 | 13,667 / 20,667 | -1,071 / -36,140 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,205 | 747 | 1,478 | 805 | 653 | -392 | -678 | -522 | 7,803 / 16,682 | 12,070 / 20,667 | 5,401 / -36,140 | 762 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,410 | 740 | 1,339 | 476 | 300 | -531 | -570 | -319 | 8,536 / 16,682 | 14,267 / 20,667 | -1,071 / -36,140 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | K1_target | {"m": 0.9} | 25 | 2,395 / 3,747 | 27,192 / 23,673 | 215 | no |
| 0 | K1_target | {"m": 0.5} | 793 | 7,797 / 16,891 | 16,782 / 17,912 | 489 | CANDIDATE-DD |

## O7  (never-cut L6M weekly mean 211, maxDD L6M 7,489, PRE 5,097; LIVE REF S1b-COMB mean 247, maxDD L6M 6,656, PRE 4,532)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,191 | 372 | 462 | 24 | -187 | 89 | -56 | -31 | 5,612 / 7,489 | 3,915 / 5,097 | -2,601 / -9,447 | 151 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,191 | 372 | 462 | 24 | -187 | 89 | -56 | -31 | 5,612 / 7,489 | 3,915 / 5,097 | -2,601 / -9,447 | 151 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | 1,131 | 518 | 530 | 26 | -253 | -44 | 5 | 0 | 5,812 / 7,489 | 3,914 / 5,097 | -3,862 / -9,447 | 129 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | 1,131 | 518 | 530 | 26 | -253 | -44 | 5 | 0 | 5,812 / 7,489 | 3,914 / 5,097 | -3,862 / -9,447 | 129 | 0.120 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,055 | -303 | -127 | 19 | -214 | -589 | -338 | 50 | 4,828 / 7,489 | 6,338 / 5,097 | -5,702 / -9,447 | 251 | 0.040 | 1.000 | no/not run |  | no |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,141 | -244 | -86 | -61 | -226 | -102 | -376 | 27 | 5,377 / 7,489 | 7,244 / 5,097 | -6,391 / -9,447 | 263 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | K1_target | {"m": 0.6} | 19 | 4,828 / 7,489 | 6,338 / 5,097 | 251 | no |

## Plain sentences
- ALL profit: the profit technique that lowers drawdown most without costing profit is X1_scale_target {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20}; L6M maxDD 33,979 vs 117,593 never-cut, it earns 872 USD/week vs never-cut (-1,905 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- K7 profit: the profit technique that lowers drawdown most without costing profit is K1_target {"m": 0.5}; L6M maxDD 9,922 vs 26,983 never-cut, it earns 303 USD/week vs never-cut (-398 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- P7 profit: the profit technique that lowers drawdown most without costing profit is L1_cond {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech": "J1_scale"; L6M maxDD 78,002 vs 126,710 never-cut, it earns 744 USD/week vs never-cut (5,704 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- M7 profit: the profit technique that lowers drawdown most without costing profit is J1_scale {"p": 0.3, "rest": "trail", "x": 10}; L6M maxDD 24,617 vs 43,318 never-cut, it earns 368 USD/week vs never-cut (1,258 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- U7 profit: the profit technique that lowers drawdown most without costing profit is X2_target_trail {"arm": 0.7, "m": 2, "x": 20}; L6M maxDD 10,406 vs 21,436 never-cut, it earns 786 USD/week vs never-cut (689 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- A7 profit: the profit technique that lowers drawdown most without costing profit is L3_tree_profit {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d_or_ahead"; L6M maxDD 8,053 vs 12,456 never-cut, it earns 101 USD/week vs never-cut (67 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- H7 profit: the profit technique that lowers drawdown most without costing profit is K1_target {"m": 0.5}; L6M maxDD 7,803 vs 16,682 never-cut, it earns 805 USD/week vs never-cut (-555 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
- O7 profit: the profit technique that lowers drawdown most without costing profit is K3_structtarget {"buf": 0, "level": "prior_day", "lim": 90}; L6M maxDD 5,612 vs 7,489 never-cut, it earns 24 USD/week vs never-cut (1 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward is not positive/not run. Label CANDIDATE-DD.
