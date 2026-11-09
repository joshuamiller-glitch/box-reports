# EXH_JKL - profit families J (scale), K (target), L (crosses) - 2026-11-09 07:15Z
PRE-PROOF (entries not live-matched). 565 cells scored, all registered in the ledger (agent ex-pjkl). Stage 1 first-order on the EX-CORE universe; target cells (K, X) walk the NEW target over paths extended to the flat time (my memmap store, pjkl/ext) but with the same horizon convention as the EX-CORE U.ext(): a trade whose new target/stop is unresolved 14,400 s after the original bracket is market-exited there (type 3) - this affects only wide targets (m >= 1.5, K4 extensions) on trades whose original exit was the target; EX-FEAT panel length mismatches make feature rules inert on a few trades. Deltas are USD/week vs never-cut (hold-to-bracket), carrying week dropped; "w/wo" = with rule / without. WF = purged monthly walk-forward of the technique group (table below). Placebo for target cells = the cell's own per-trade deltas re-assigned to other trades of the same book (no decision second exists). Prereg autopilot/EXH_JKL_PREREG.md. Causality: my own noise-after-k test (code/th_exh/causality_pjkl.py, 750 decisions) and EX-CORE X.kernel_leak_test (code/th_exh/kleak_pjkl.py, 2,743 legs over J1/J2/J3/K1/X1 kernels) both show 0 legs changed when path data after second k0 is replaced by noise; K1/K2/K3 targets are functions of the entry row only; the first J2 version (second scale leg filled after the trail had already closed the position) was a look-ahead, was found by review, fixed and re-scored. Live-week column = rule applied on the 186 live trades to the ACTUAL live exit (one week; not selected on).


## ALL  (never-cut L6M weekly mean 31,832, maxDD L6M 121,381, PRE 152,455; LIVE REF S1b-COMB mean 28,018, maxDD L6M 82,873, PRE 144,002)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | -3,002 | -5,823 | 1,357 | 574 | 2,054 | 8,213 | -3,279 | 569 | 33,846 / 121,381 | 87,136 / 152,455 | 183,145 / 77,580 | 7,732 | 0.015 | 1.000 | no/not run | -21,849 | CANDIDATE-DD FAILS-LIVE-WEEK |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | -3,972 | -6,281 | 784 | 492 | 2,138 | 8,650 | -3,257 | 612 | 34,560 / 121,381 | 90,210 / 152,455 | 182,091 / 77,580 | 7,732 | 0.015 | 1.000 | no/not run | -23,321 | CANDIDATE-DD FAILS-LIVE-WEEK |
| X1_scale_target | {"m": 1.25, "p": 0.7, "rest": "trail", "x": 20} | -5,218 | -6,503 | 510 | 978 | 1,818 | 6,524 | -3,161 | 1,330 | 37,868 / 121,381 | 79,518 / 152,455 | 176,566 / 77,580 | 7,732 | 0.040 | 1.000 | no/not run | -30,559 | CANDIDATE-DD FAILS-LIVE-WEEK |
| J1_scale | {"p": 0.7, "rest": "trail", "x": 20} | -4,330 | -5,324 | 1,485 | 2,144 | 2,016 | 6,787 | -3,329 | 961 | 39,107 / 121,381 | 86,368 / 152,455 | 194,942 / 77,580 | 4,708 | 0.040 | 1.000 | no/not run | -31,151 | CANDIDATE-DD FAILS-LIVE-WEEK |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.6, "rest": "trail", "x": 5} | -1,612 | -2,443 | 3,656 | -5,361 | -3,383 | -2,339 | -5,166 | 249 | 28,893 / 121,381 | 72,571 / 152,455 | 207,574 / 77,580 | 5,026 | 0.040 | 1.000 | no/not run | -29,693 | no |
| J1_scale | {"p": 0.6, "rest": "trail", "x": 10} | -1,240 | -2,104 | 3,198 | -5,442 | -3,540 | -3,043 | -5,021 | 60 | 32,042 / 121,381 | 73,676 / 152,455 | 194,569 / 77,580 | 5,026 | 0.040 | 1.000 | no/not run | -27,225 | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 4 | K1_target | {"m": 0.5} | 43 | 2,362 / 6,369 | 19,285 / 33,629 | 748 | CANDIDATE-DD |
| 3 | J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | 2,504 | 37,207 / 81,753 | 33,015 / 53,932 | 768 | CANDIDATE-DD |
| 0 | L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,779 | 55,483 / 103,480 | 61,417 / 85,327 | 1,755 | CANDIDATE-DD |
| 1 | L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 500 | 55,652 / 69,170 | 187,482 / 137,656 | 851 | no |

## K7  (never-cut L6M weekly mean 4,293, maxDD L6M 20,902, PRE 26,707; LIVE REF S1b-COMB mean 3,712, maxDD L6M 41,849, PRE 23,073)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5,  | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.015 | 1.000 | no/not run | 0 | CANDIDATE-DD |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.040 | 1.000 | no/not run | -40 | CANDIDATE-DD |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,286 | -761 | 1,258 | 270 | -409 | -1,718 | -412 | 480 | 9,389 / 20,902 | 17,644 / 26,707 | 40,236 / 1,791 | 689 | 0.040 | 1.000 | no/not run | 56 | CANDIDATE-DD |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 10} | 2,146 | -846 | 1,106 | 205 | -427 | -1,502 | -395 | 479 | 9,411 / 20,902 | 18,094 / 26,707 | 37,916 / 1,791 | 689 | 0.040 | 1.000 | no/not run | -472 | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 2,086 | -935 | 1,768 | -279 | -1,032 | -3,755 | -1,174 | -54 | 6,748 / 20,902 | 31,841 / 26,707 | 40,050 / 1,791 | 4,114 | 0.015 | 1.000 | no/not run | -3,720 | no |
| K1_target | {"m": 0.5} | 1,717 | -986 | 1,433 | -729 | -992 | -2,479 | -1,034 | 428 | 8,253 / 20,902 | 24,342 / 26,707 | 25,298 / 1,791 | 4,397 | 0.015 | 1.000 | no/not run | -660 | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 4 | K1_target | {"m": 0.5} | 43 | 2,362 / 6,369 | 19,285 / 33,629 | 748 | CANDIDATE-DD |
| 3 | K1_target | {"m": 0.5} | 263 | 6,912 / 23,185 | 6,924 / 6,211 | 1,040 | LEAD |
| 1 | L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 548 | 10,131 / 14,952 | 12,250 / 18,704 | 310 | CANDIDATE-DD |
| 0 | J1_scale | {"p": 0.6, "rest": "trail", "x": 5} | 1,126 | 13,885 / 22,104 | 15,360 / 13,344 | 326 | LEAD |

## P7  (never-cut L6M weekly mean 20,702, maxDD L6M 133,887, PRE 109,442; LIVE REF S1b-COMB mean 17,718, maxDD L6M 96,490, PRE 106,914)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "c | -841 | 678 | 1,582 | 5,082 | 2,987 | 766 | -1,380 | -800 | 82,296 / 133,887 | 92,199 / 109,442 | 76,006 / -29,902 | 1,006 | 0.015 | 1.000 | no/not run | -6,398 | CANDIDATE-DD |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "c | -1,382 | 528 | 1,972 | 5,069 | 3,016 | 754 | -1,412 | -876 | 83,539 / 133,887 | 91,553 / 109,442 | 78,160 / -29,902 | 1,006 | 0.040 | 1.000 | no/not run | -6,398 | CANDIDATE-DD |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech": "J1_scale" | 3,029 | -7,152 | -3,235 | 1,621 | 1,825 | 2,116 | -1,081 | -832 | 87,937 / 133,887 | 97,537 / 109,442 | 63,228 / -29,902 | 946 | 0.040 | 1.000 | no/not run | -5,288 | CANDIDATE-DD |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech": "J1_scale" | -646 | -184 | 889 | 515 | 1,200 | 2,100 | -1,148 | -1,053 | 88,539 / 133,887 | 99,024 / 109,442 | 72,153 / -29,902 | 946 | 0.040 | 1.000 | no/not run | -3,688 | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.75} | -6,188 | -6,189 | 52 | -1,634 | 206 | -515 | -2,873 | -1,071 | 73,600 / 133,887 | 101,053 / 109,442 | 16,862 / -29,902 | 2,813 | 0.080 | 1.000 | no/not run | -8,395 | no |
| J3_statescale | {"a": 0.6, "f": "tot_rel_slow", "rest": "trail", "s": 3, "th": 2, "x": | 3,758 | -1,608 | 1,352 | -627 | -759 | -930 | -2,274 | -994 | 79,815 / 133,887 | 125,220 / 109,442 | 21,221 / -29,902 | 699 | 0.040 | 1.000 | no/not run | 0 | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | 2,504 | 25,381 / 86,629 | 33,479 / 77,956 | 768 | CANDIDATE-DD |
| 1 | L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 2,454 | 35,906 / 51,796 | 138,573 / 150,275 | 312 | CANDIDATE-DD |
| 0 | K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,062 | 98,912 / 116,210 | 85,586 / 66,531 | 56 | LEAD |

## M7  (never-cut L6M weekly mean 198, maxDD L6M 44,425, PRE 50,321; LIVE REF S1b-COMB mean -475, maxDD L6M 46,547, PRE 25,812)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,365 | -1,516 | -1,887 | 405 | 519 | -55 | 326 | -83 | 25,111 / 44,425 | 29,613 / 50,321 | -46,302 / -68,299 | 545 | 0.015 | 1.000 | ok | -382 | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,493 | -1,577 | -1,897 | 451 | 551 | -117 | 138 | -102 | 25,462 / 44,425 | 29,064 / 50,321 | -44,834 / -68,299 | 545 | 0.040 | 1.000 | ok | -452 | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | -2,620 | -1,616 | -2,047 | 314 | 426 | -268 | 199 | -102 | 28,225 / 44,425 | 34,097 / 50,321 | -49,879 / -68,299 | 545 | 0.080 | 1.000 | ok | -939 | CANDIDATE-DD |
| J1_scale | {"p": 0.4, "rest": "trail", "x": 5} | -1,864 | -1,116 | -1,545 | 451 | 715 | -110 | 141 | -237 | 29,534 / 44,425 | 41,163 / 50,321 | -49,017 / -68,299 | 505 | 0.080 | 1.000 | ok | -1,747 | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,365 | -1,516 | -1,887 | 405 | 519 | -55 | 326 | -83 | 25,111 / 44,425 | 29,613 / 50,321 | -46,302 / -68,299 | 545 | 0.015 | 1.000 | ok | -382 | CANDIDATE-DD |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,493 | -1,577 | -1,897 | 451 | 551 | -117 | 138 | -102 | 25,462 / 44,425 | 29,064 / 50,321 | -44,834 / -68,299 | 545 | 0.040 | 1.000 | ok | -452 | CANDIDATE-DD |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | K1_target | {"m": 0.75} | 75 | 8,992 / 11,667 | 9,078 / 7,583 | 890 | LEAD |
| 1 | L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 582 | 28,446 / 38,178 | 64,823 / 69,890 | 183 | CANDIDATE-DD |

## U7  (never-cut L6M weekly mean 3,739, maxDD L6M 21,561, PRE 42,226; LIVE REF S1b-COMB mean 3,881, maxDD L6M 16,419, PRE 39,155)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,557 | -148 | 1,992 | 551 | 525 | -1,411 | -704 | -575 | 10,319 / 21,561 | 38,921 / 42,226 | 20,588 / 120 | 849 | 0.031 | 1.000 | no/not run |  | CANDIDATE-DD |
| X1_scale_target | {"m": 2, "p": 0.7, "rest": "trail", "x": 20} | 4,928 | -1,147 | 1,772 | 600 | 502 | -744 | -359 | -270 | 11,277 / 21,561 | 30,968 / 42,226 | 28,281 / 120 | 1,135 | 0.040 | 1.000 | no/not run | -1,085 | CANDIDATE-DD |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | 3,419 | -1,642 | 1,083 | 266 | 347 | -1,708 | -177 | -229 | 11,660 / 21,561 | 25,905 / 42,226 | 21,130 / 120 | 1,135 | 0.015 | 1.000 | no/not run | -1,990 | CANDIDATE-DD |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | 3,471 | -1,795 | 1,018 | 203 | 284 | -1,673 | -124 | -183 | 12,029 / 21,561 | 24,988 / 42,226 | 18,811 / 120 | 1,135 | 0.015 | 1.000 | no/not run | -1,990 | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | 4,091 | -2,041 | -1,450 | -1,367 | -521 | -516 | -1,724 | -271 | 9,067 / 21,561 | 47,182 / 42,226 | 7,724 / 120 | 899 | 0.040 | 1.000 | no/not run | 5,808 | no |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | 4,978 | -1,750 | -1,037 | -275 | -566 | -1,395 | -1,713 | -391 | 9,548 / 21,561 | 41,862 / 42,226 | 6,142 / 120 | 899 | 0.040 | 1.000 | no/not run | 5,463 | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 0 | L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 219 | 5,897 / 9,906 | 22,862 / 31,026 | 231 | CANDIDATE-DD |
| 1 | J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 451 | 15,679 / 32,749 | 59,879 / 33,984 | 350 | LEAD |

## A7  (never-cut L6M weekly mean 639, maxDD L6M 12,461, PRE 6,089; LIVE REF S1b-COMB mean 543, maxDD L6M 8,518, PRE 7,325)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,706 | -707 | -222 | 171 | -71 | -296 | -119 | -180 | 5,693 / 12,461 | 4,907 / 6,089 | -543 / -17,069 | 785 | 0.015 | 1.000 | no/not run | 930 | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 20} | 435 | -1,645 | -771 | 303 | 80 | -616 | -159 | -145 | 6,463 / 12,461 | 5,050 / 6,089 | -10,528 / -17,069 | 831 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 20} | 199 | -1,646 | -809 | 284 | 89 | -641 | -161 | -107 | 7,617 / 12,461 | 5,050 / 6,089 | -12,003 / -17,069 | 831 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 20} | -15 | -1,826 | -824 | 209 | 21 | -539 | -208 | -145 | 7,663 / 12,461 | 4,701 / 6,089 | -11,892 / -17,069 | 831 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 649 | -1,476 | -477 | -102 | -56 | -589 | -72 | -139 | 4,913 / 12,461 | 4,259 / 6,089 | -5,798 / -17,069 | 838 | 0.015 | 1.000 | no/not run | 775 | no |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 498 | -1,717 | -612 | -271 | -194 | -397 | -99 | -155 | 5,588 / 12,461 | 4,420 / 6,089 | -10,078 / -17,069 | 831 | 0.040 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 0 | K1_target | {"m": 0.6} | 171 | 5,693 / 12,461 | 4,907 / 6,089 | 785 | CANDIDATE-DD |

## H7  (never-cut L6M weekly mean 1,647, maxDD L6M 15,477, PRE 20,667; LIVE REF S1b-COMB mean 2,545, maxDD L6M 8,818, PRE 19,256)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,216 | 752 | 1,333 | 760 | 657 | -170 | -646 | -522 | 7,798 / 15,477 | 12,907 / 20,667 | 7,005 / -32,750 | 761 | 0.015 | 1.000 | no/not run | 3,175 | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,421 | 601 | 1,116 | 356 | 341 | -312 | -552 | -319 | 8,561 / 15,477 | 16,400 / 20,667 | -1,011 / -32,750 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 10} | 1,421 | 601 | 1,116 | 356 | 337 | -312 | -487 | -331 | 8,561 / 15,477 | 15,800 / 20,667 | -1,011 / -32,750 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 10} | 1,421 | 601 | 1,116 | 356 | 334 | -319 | -613 | -328 | 8,561 / 15,477 | 16,629 / 20,667 | -1,011 / -32,750 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,216 | 752 | 1,333 | 760 | 657 | -170 | -646 | -522 | 7,798 / 15,477 | 12,907 / 20,667 | 7,005 / -32,750 | 761 | 0.015 | 1.000 | no/not run | 3,175 | CANDIDATE-DD |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,421 | 601 | 1,116 | 356 | 341 | -312 | -552 | -319 | 8,561 / 15,477 | 16,400 / 20,667 | -1,011 / -32,750 | 755 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 61 | 2,395 / 3,762 | 23,608 / 23,608 | 58 | CANDIDATE-DD |
| 0 | L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,368 | 6,802 / 14,606 | 17,912 / 17,912 | 239 | CANDIDATE-DD |

## O7  (never-cut L6M weekly mean 279, maxDD L6M 7,469, PRE 5,102; LIVE REF S1b-COMB mean 324, maxDD L6M 6,656, PRE 4,532)
Candidates (L6M mean >= never-cut and PRE maxDD within 5%):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.015 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.080 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.040 | 1.000 | no/not run |  | CANDIDATE-DD |

Lowest-drawdown cells regardless of cost (profit given up shown in the L6M column):

| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p | WF | live | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,062 | -303 | -125 | 23 | -213 | -589 | -396 | 50 | 4,703 / 7,469 | 6,353 / 5,102 | -5,667 / -9,532 | 250 | 0.015 | 1.000 | no/not run | 805 | no |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,141 | -60 | 35 | -2 | -245 | -318 | -411 | 27 | 5,257 / 7,469 | 7,259 / 5,102 | -5,067 / -9,532 | 263 | 0.080 | 1.000 | no/not run |  | no |

Best candidate by entry session:

| sess | technique | params | L6M mean | maxDD L6M w/wo | maxDD PRE w/wo | nfire | label |
|---|---|---|---|---|---|---|---|
| 3 | K1_target | {"m": 0.6} | 23 | 4,703 / 7,469 | 6,353 / 5,102 | 250 | no |

## Purged monthly walk-forward of the picking procedure (pick on trailing 26 weeks by drawdown-first key subject to mean >= never-cut, apply next month, 7-day embargo; 2024-02..2026-10 so PRE is covered from 2024-02 and X' not at all)

| book | technique group | cells | WF total vs never (USD) | maxDD never / WF | share of months positive | wf_ok |
|---|---|---|---|---|---|---|
| ALL | J1_scale | 49 | -153,458 | 153,255 / 152,455 | 0.26 | False |
| ALL | J2_thirds | 27 | -77,053 | 153,255 / 153,255 | 0.03 | False |
| ALL | J3_statescale | 144 | -383,659 | 153,255 / 179,287 | 0.17 | False |
| ALL | K1_target | 10 | -218,536 | 153,255 / 191,022 | 0.26 | False |
| ALL | K2_atrtarget | 8 | -392,426 | 153,255 / 372,432 | 0.26 | False |
| ALL | K3_structtarget | 12 | -51,297 | 153,255 / 151,138 | 0.26 | False |
| ALL | K4_extend | 81 | -94,887 | 153,255 / 236,351 | 0.43 | False |
| ALL | L1_cond | 191 | -216,598 | 153,255 / 128,606 | 0.49 | False |
| ALL | L3_tree_profit | 6 | -403,704 | 153,255 / 153,255 | 0.06 | False |
| ALL | X1_scale_target | 24 | -278,977 | 153,255 / 195,479 | 0.17 | False |
| ALL | X2_target_trail | 12 | -55,556 | 153,255 / 153,255 | 0.03 | False |
| ALL | ALLGROUPS | 564 | -675,395 | 153,255 / 200,591 | 0.26 | False |
| K7 | J1_scale | 49 | -46,439 | 42,831 / 41,437 | 0.26 | False |
| K7 | J3_statescale | 122 | -41,710 | 42,831 / 41,051 | 0.31 | False |
| K7 | K1_target | 10 | -129,634 | 42,831 / 50,890 | 0.23 | False |
| K7 | K2_atrtarget | 8 | -71,438 | 42,831 / 59,287 | 0.31 | False |
| K7 | K3_structtarget | 12 | -23,635 | 42,831 / 44,788 | 0.31 | False |
| K7 | K4_extend | 81 | -17,969 | 42,831 / 39,503 | 0.51 | False |
| K7 | L1_cond | 169 | -19,811 | 42,831 / 38,091 | 0.40 | False |
| K7 | L3_tree_profit | 6 | -80,008 | 42,831 / 40,458 | 0.06 | False |
| K7 | X1_scale_target | 24 | -34,760 | 42,831 / 37,182 | 0.29 | False |
| K7 | X2_target_trail | 12 | -73,628 | 42,831 / 42,831 | 0.00 | False |
| K7 | ALLGROUPS | 493 | -87,590 | 42,831 / 58,216 | 0.46 | False |
| P7 | J1_scale | 49 | -346,755 | 144,370 / 119,681 | 0.17 | False |
| P7 | J2_thirds | 27 | -146,812 | 144,370 / 144,370 | 0.03 | False |
| P7 | J3_statescale | 142 | -284,844 | 144,370 / 139,509 | 0.23 | False |
| P7 | K1_target | 10 | 140,088 | 144,370 / 220,385 | 0.37 | False |
| P7 | K2_atrtarget | 8 | -10,719 | 144,370 / 256,400 | 0.37 | False |
| P7 | K3_structtarget | 12 | -49,059 | 144,370 / 156,100 | 0.29 | False |
| P7 | K4_extend | 81 | -192,922 | 144,370 / 200,490 | 0.40 | False |
| P7 | L1_cond | 184 | -186,434 | 144,370 / 148,644 | 0.49 | False |
| P7 | L3_tree_profit | 6 | -140,372 | 144,370 / 144,370 | 0.06 | False |
| P7 | X1_scale_target | 24 | -259,876 | 144,370 / 200,390 | 0.20 | False |
| P7 | X2_target_trail | 12 | -54,805 | 144,370 / 129,397 | 0.09 | False |
| P7 | ALLGROUPS | 555 | -381,361 | 144,370 / 193,891 | 0.37 | False |
| M7 | J1_scale | 49 | 1,792 | 68,802 / 57,760 | 0.40 | True |
| M7 | J3_statescale | 112 | -40,854 | 68,802 / 60,224 | 0.29 | False |
| M7 | K1_target | 10 | 11,490 | 68,802 / 52,415 | 0.51 | True |
| M7 | K2_atrtarget | 8 | -24,942 | 68,802 / 82,856 | 0.34 | False |
| M7 | K3_structtarget | 12 | -9,721 | 68,802 / 83,797 | 0.40 | False |
| M7 | K4_extend | 81 | -27,918 | 68,802 / 83,375 | 0.37 | False |
| M7 | L1_cond | 139 | 7,626 | 68,802 / 63,888 | 0.46 | True |
| M7 | L3_tree_profit | 6 | -5,476 | 68,802 / 68,802 | 0.23 | False |
| M7 | X1_scale_target | 24 | 28,884 | 68,802 / 56,589 | 0.54 | True |
| M7 | X2_target_trail | 12 | -40,736 | 68,802 / 62,848 | 0.17 | False |
| M7 | ALLGROUPS | 453 | -19,679 | 68,802 / 79,123 | 0.43 | False |
| U7 | J1_scale | 49 | -82,937 | 42,226 / 34,622 | 0.20 | False |
| U7 | J2_thirds | 27 | -51,769 | 42,226 / 42,285 | 0.09 | False |
| U7 | J3_statescale | 128 | -115,421 | 42,226 / 47,067 | 0.29 | False |
| U7 | K1_target | 10 | -50,054 | 42,226 / 37,349 | 0.40 | False |
| U7 | K2_atrtarget | 8 | -39,581 | 42,226 / 43,573 | 0.46 | False |
| U7 | K3_structtarget | 12 | 23,501 | 42,226 / 42,536 | 0.26 | True |
| U7 | K4_extend | 81 | -113,213 | 42,226 / 65,001 | 0.23 | False |
| U7 | L1_cond | 165 | -55,326 | 42,226 / 34,172 | 0.31 | False |
| U7 | L3_tree_profit | 6 | -16,505 | 42,226 / 42,226 | 0.20 | False |
| U7 | X1_scale_target | 24 | -59,612 | 42,226 / 34,622 | 0.29 | False |
| U7 | X2_target_trail | 12 | -76,727 | 42,226 / 39,922 | 0.17 | False |
| U7 | ALLGROUPS | 522 | -98,069 | 42,226 / 48,580 | 0.37 | False |
| A7 | K1_target | 10 | -1,340 | 14,181 / 16,209 | 0.49 | False |
| A7 | K2_atrtarget | 8 | -7,629 | 14,181 / 26,445 | 0.43 | False |
| A7 | K3_structtarget | 10 | -9,203 | 14,181 / 13,892 | 0.09 | False |
| A7 | K4_extend | 78 | 19,220 | 14,181 / 20,770 | 0.60 | False |
| A7 | L3_tree_profit | 6 | -4,413 | 14,181 / 14,181 | 0.14 | False |
| A7 | X2_target_trail | 12 | -47,075 | 14,181 / 22,209 | 0.09 | False |
| A7 | ALLGROUPS | 124 | 6,226 | 14,181 / 13,799 | 0.54 | True |
| H7 | J1_scale | 49 | -30,189 | 57,397 / 38,959 | 0.40 | False |
| H7 | J2_thirds | 27 | -417 | 57,397 / 55,524 | 0.23 | False |
| H7 | J3_statescale | 122 | 20,956 | 57,397 / 35,477 | 0.49 | True |
| H7 | K1_target | 10 | -47,880 | 57,397 / 98,287 | 0.43 | False |
| H7 | K2_atrtarget | 8 | 21,899 | 57,397 / 69,300 | 0.49 | False |
| H7 | K3_structtarget | 12 | -25,294 | 57,397 / 74,244 | 0.26 | False |
| H7 | K4_extend | 75 | -2,478 | 57,397 / 67,036 | 0.46 | False |
| H7 | L1_cond | 136 | 15,757 | 57,397 / 50,120 | 0.31 | True |
| H7 | L3_tree_profit | 6 | 19,568 | 57,397 / 33,618 | 0.14 | True |
| H7 | X1_scale_target | 24 | -30,217 | 57,397 / 62,085 | 0.34 | False |
| H7 | X2_target_trail | 12 | -33,598 | 57,397 / 62,573 | 0.26 | False |
| H7 | ALLGROUPS | 481 | -1,732 | 57,397 / 37,692 | 0.46 | False |
| O7 | K1_target | 10 | -9,785 | 7,469 / 11,523 | 0.46 | False |
| O7 | K2_atrtarget | 8 | 27,033 | 7,469 / 12,552 | 0.51 | False |
| O7 | K3_structtarget | 12 | -6,496 | 7,469 / 7,469 | 0.40 | False |
| O7 | K4_extend | 63 | 4,104 | 7,469 / 11,523 | 0.43 | False |
| O7 | L3_tree_profit | 6 | 0 | 7,469 / 7,469 | 0.00 | True |
| O7 | X2_target_trail | 12 | -6,079 | 7,469 / 7,469 | 0.11 | False |
| O7 | ALLGROUPS | 111 | -14,782 | 7,469 / 11,523 | 0.40 | False |

## Plain sentences
- ALL profit: the profit technique that lowers drawdown most without costing profit is X1_scale_target {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10}; L6M maxDD 33,846 vs 121,381 never-cut, it earns 574 USD/week vs never-cut (-2,664 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD FAILS-LIVE-WEEK.
- K7 profit: the profit technique that lowers drawdown most without costing profit is J3_statescale {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, ; L6M maxDD 8,893 vs 20,902 never-cut, it earns 666 USD/week vs never-cut (1,385 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.
- P7 profit: the profit technique that lowers drawdown most without costing profit is L1_cond {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "c; L6M maxDD 82,296 vs 133,887 never-cut, it earns 5,082 USD/week vs never-cut (2,268 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.
- M7 profit: the profit technique that lowers drawdown most without costing profit is J1_scale {"p": 0.3, "rest": "trail", "x": 10}; L6M maxDD 25,111 vs 44,425 never-cut, it earns 405 USD/week vs never-cut (1,250 vs the live line); it does not yet hold out of sample because family p 1.00. Label CANDIDATE-DD.
- U7 profit: the profit technique that lowers drawdown most without costing profit is X2_target_trail {"arm": 0.7, "m": 2, "x": 20}; L6M maxDD 10,319 vs 21,561 never-cut, it earns 551 USD/week vs never-cut (545 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.
- A7 profit: the profit technique that lowers drawdown most without costing profit is K1_target {"m": 0.6}; L6M maxDD 5,693 vs 12,461 never-cut, it earns 171 USD/week vs never-cut (308 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.
- H7 profit: the profit technique that lowers drawdown most without costing profit is K1_target {"m": 0.5}; L6M maxDD 7,798 vs 15,477 never-cut, it earns 760 USD/week vs never-cut (-511 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.
- O7 profit: the profit technique that lowers drawdown most without costing profit is K3_structtarget {"buf": 0, "level": "prior_day", "lim": 90}; L6M maxDD 5,487 vs 7,469 never-cut, it earns 27 USD/week vs never-cut (2 vs the live line); it does not yet hold out of sample because family p 1.00, the purged walk-forward of this technique group is not positive. Label CANDIDATE-DD.

## K5/K6 per-session target table and per-session scale table (purged monthly WF of picking m / scale pct per book x entry session from the K1 / J1 lattices; sessions: 0 asia 1 london 3 nyam 4 nypm)

| table | book | session | WF total vs never (USD) | maxDD never / WF | share of months positive | wf_ok |
|---|---|---|---|---|---|---|
| K1_target | K7 | 0 | -31,277 | 22,348 / 33,842 | 0.34 | False |
| K1_target | K7 | 1 | 3,904 | 28,123 / 48,431 | 0.46 | False |
| K1_target | K7 | 3 | -12,806 | 43,037 / 48,565 | 0.40 | False |
| K1_target | K7 | 4 | -55,059 | 33,629 / 45,458 | 0.37 | False |
| K1_target | P7 | 0 | 11,476 | 116,210 / 172,050 | 0.43 | False |
| K1_target | P7 | 1 | 97,316 | 150,275 / 196,689 | 0.46 | False |
| K1_target | P7 | 3 | -9,646 | 91,489 / 92,598 | 0.43 | False |
| K1_target | M7 | 1 | 38,651 | 84,525 / 56,868 | 0.60 | True |
| K1_target | M7 | 3 | 536 | 20,068 / 31,920 | 0.37 | False |
| K1_target | U7 | 0 | -11,098 | 31,026 / 42,864 | 0.46 | False |
| K1_target | U7 | 1 | -86,925 | 33,984 / 75,309 | 0.31 | False |
| K1_target | A7 | 0 | -1,340 | 14,181 / 16,209 | 0.49 | False |
| K1_target | H7 | 0 | -37,311 | 61,332 / 91,247 | 0.49 | False |
| K1_target | H7 | 3 | -3,954 | 22,413 / 23,985 | 0.46 | False |
| K1_target | O7 | 3 | -9,785 | 7,469 / 11,523 | 0.46 | False |
| J1_scale | K7 | 0 | 891 | 22,348 / 22,348 | 0.23 | True |
| J1_scale | K7 | 1 | 11,567 | 28,123 / 34,262 | 0.37 | False |
| J1_scale | K7 | 4 | -15,236 | 33,629 / 28,395 | 0.14 | False |
| J1_scale | P7 | 0 | -156,003 | 116,210 / 94,160 | 0.20 | False |
| J1_scale | P7 | 1 | -255,984 | 150,275 / 237,886 | 0.34 | False |
| J1_scale | P7 | 3 | 42,106 | 91,489 / 77,956 | 0.31 | True |
| J1_scale | M7 | 1 | 19,526 | 84,525 / 78,737 | 0.37 | True |
| J1_scale | U7 | 0 | -38,324 | 31,026 / 22,893 | 0.26 | False |
| J1_scale | U7 | 1 | -50,890 | 33,984 / 34,400 | 0.34 | False |
| J1_scale | H7 | 0 | -17,052 | 61,332 / 45,380 | 0.46 | False |

Not scored (stated): J4 scale-and-re-add (report row only, needs a second entry leg); K structure target "flip level ahead" (no state series in the store); K target extension on "delta with" (dlt sign convention not verified); time-of-day target table (the hour blocks enter only as L1 conditioners hour0..7, with the K/J cells as the rule inside the block). Tight-target cells (K1 m < 1, X1 m < 1) change the bracket itself, i.e. a different 30/60 style bracket rather than an exit technique.

Stage 2 kernel validation (validate_kernel_s2.py, pjkl_PB, month 202606): K7 (K1 target 0.5) Stage 1 kernel fires 220, engine ExhCut on 193 of them, equal second (+-1 s) 172, equal price 160; H7 (K1 0.5) 32 fires, 32 ExhCut, 24 equal second, 15 equal price; M7 (J1 scale 0.3 + trail 10) Stage 1 fires 24, engine ExhCut 0: the engine position quantity at the first manage call is the first-fill lot count, so multi-lot scale-outs on books that stage their fills (M7, P7, U7) are largely INERT in Stage 2 (a stated limit of the ExhRep hook: the kernel lots are the entry-time quantity). Tight-target legs (K1) agree on most trades; differences of 1-3 points are fill/state-time differences between the universe path and the engine.

## Stage 2 (replica engine cascade; ExhRep; months not yet run are filled from engine never-cut so a partial run shows what it has)

| set | months run | book | L6M mean delta vs engine never-cut | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo |
|---|---|---|---|---|---|---|
| PJKL_perbook_best | 39 | ALL |  |  /  | 149,858 / 130,824 |  /  |
| PJKL_perbook_best | 39 | K7 |  |  /  | 25,019 / 22,188 |  /  |
| PJKL_perbook_best | 39 | P7 |  |  /  | 120,071 / 122,169 |  /  |
| PJKL_perbook_best | 39 | M7 |  |  /  | 43,648 / 44,205 |  /  |
| PJKL_perbook_best | 39 | U7 |  |  /  | 30,546 / 39,542 |  /  |
| PJKL_perbook_best | 39 | A7 |  |  /  | 7,355 / 8,625 |  /  |
| PJKL_perbook_best | 39 | H7 |  |  /  | 11,190 / 18,436 |  /  |
| PJKL_perbook_best | 39 | O7 |  |  /  | 4,797 / 4,797 |  /  |

## Finalists (<=12; held-out live week where the cell is a scale/limit rule; K1 cells with m <= 1 are evaluated on the live week (a tighter target is checked against the path up to the actual exit); wider-target, ATR and extension cells have no live evaluation because the live bracket is the actual exit)

| cell | params | live-week delta USD (ALL) | live fires | L6M maxDD w/wo |
|---|---|---|---|---|
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | -21,849 | 81 | 33,846 / 121,381 |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | -23,321 | 81 | 34,560 / 121,381 |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, "x": 10} | 0 | 0 | 182,135 / 121,381 |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "cond": "atr | -6,398 | 1 | 55,296 / 121,381 |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -39,305 | 62 | 117,326 / 121,381 |
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} |  |  | 105,756 / 121,381 |
| K1_target | {"m": 0.6} | -29,763 | 110 | 40,529 / 121,381 |
| K1_target | {"m": 0.5} | -35,933 | 121 | 49,610 / 121,381 |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} |  |  | 111,434 / 121,381 |
