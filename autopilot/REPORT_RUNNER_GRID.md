# REPORT_RUNNER_GRID (trackP2, 2026-10-21)
Pre-registration: outputs/l2vast/PREREG_P2_runner_grid.md (AUTOPILOT.md block). Pair 14/14 on BENCH3, cost-corrected (ccorr, foundB v2 excess), windows 18:00-18:05 / 15:00-16:54, true entry = et_in-60 s. Code outputs/l2vast/pairP2/runner_grid.py, runner_final.py; data runner_grid_final.csv (108 cell-runs), runner_grid_nulls.json.

## Definitions and method
- R = 60-pt stop (1R). Take X% off at the +60 target (limit, no cost); runner stop = the original -60 stop; trail cells use max(-60, running max - T); fixed runner targets at 1.5/2/3/4R = 90/120/180/240 pts (limit); (c) flatten only = hold to the next 16:55 ET (market).
- Lot rounding 14 lots: X=50/67/80/90% -> 7/9/11/13 lots (runner 7/5/3/1); 8 lots (8/8 view): 4/5/6/7 (runner 4/3/2/1).
- Path source: the tape aggregated to 1-second high/low/last (BENCH3 itself is resolved on the 1-second path). Within a second the ADVERSE extreme is assumed first (pessimistic for stops and trails); the trail uses the running maximum of PREVIOUS seconds only; the target second itself is not used for the runner. 29 of 7,219 target rows disagree with the tape (stop touched first/same second) and keep the BENCH3 outcome; 7,129 rows are affected.
- Costs: runner market exits (trail/stop/flatten) pay the foundB v2 mean exit excess (per year x session) x runner lots/14; target and fixed-target fills are limits (no excess). Entry excess unchanged.
- Extra exit orders per affected trade: 1 runner exit order; trail cells also modify the stop each +1 pt of running max (mean count in the CSV column extra_orders).
- Two evaluations. A = rules-free trade-level delta on the rows that trade in the base (day rules cannot interact): the pure runner edge. B = the BENCH3 harness with each affected trade realised at the runner exit (day rules/locks see the runner P&L at its exit time; the position MTM inside the combined cap/give-back uses the full-size path after the target = distortion, documented). A third form (runner as an independent leg outside the rules) was tried and DROPPED: it inflates results by letting the main leg shrink the cap/lock triggers (+$30M, an artefact).

## Key finding: the runner is a martingale in expectation
Mean runner exit (pts from entry, over 7,129 trades): trail30/45 60.2, trail60 61.4, trail90 63.8, fixed1.5/2/3 60.0/59.9/60.1, fixed4 59.5, flatten-only 59.2, i.e. equal to the +60 given up; the only rule with a positive drift is the wide trail (T=90, +3.8 pts). Share of runners ending at -60: 0% (trails), 17.5/27.8/38.6/43.7% (fixed 1.5/2/3/4R), 48.5% (flatten-only).

## Table 1 - both books, A (rules-free runner edge, $ at 14/14, on rows that trade in the base) and B (harness) vs BENCH3 corrected
Base (60/1.0) BENCH3 corrected 14/14: all-in net $3.95M, maxDD $422k, Sharpe 1.55; OOS $3.59M / $418k / 1.61; clean $2.51M / $422k / 1.70; H2 $0.68M / $368k / 1.08; L8W -$37k / $358k.

|   X |   lots14 | rule     |   A_clean |    A_H2 |   A_OOS |   A_OOS_ci5 |   A_OOS_ci95 |   A_L8W |   B_dOOS_net |   B_dOOS_dd |   B_dL8W_net |   B_dL8W_dd |   B_net_OOS |   B_dd_OOS |   B_sh_OOS |   B_sh_clean |   B_sh_H2 |   extra_orders |   mkt_exit_share |   runner_cost_usd | B_beats   |
|----:|---------:|:---------|----------:|--------:|--------:|------------:|-------------:|--------:|-------------:|------------:|-------------:|------------:|------------:|-----------:|-----------:|-------------:|----------:|---------------:|-----------------:|------------------:|:----------|
|  50 |        7 | trail30  |    166952 | -264597 | -251360 |     -720231 |       192805 |   10569 |      1470097 |      -27731 |       256058 |      -37876 |     5063330 |     390499 |       2.22 |         2.42 |      1.85 |          31.63 |             1    |            404446 | True      |
|  50 |        7 | trail45  |    -94078 |  -70557 | -309250 |    -1012057 |       362168 |   55474 |       261889 |      -32618 |       450436 |      -32937 |     3855122 |     385612 |       1.71 |         1.85 |      1.9  |          45.98 |             1    |            404446 | True      |
|  50 |        7 | trail60  |    676867 |  230828 | 1057185 |     -117306 |      2346211 |  -96601 |     -1097772 |      429774 |       136777 |      -24613 |     2495462 |     848004 |       1.06 |         0.89 |      1.8  |          60.67 |             1    |            404446 | False     |
|  50 |        7 | trail90  |   2549332 | 1644758 | 4867985 |     2396657 |      8242696 |  717499 |       820522 |      355782 |       272459 |        1001 |     4413756 |     774013 |       1.69 |         1.46 |      2.35 |          87.32 |             1    |            404446 | False     |
|  50 |        7 | fixed1.5 |    402573 |  127364 |  486345 |     -286797 |      1297801 |   85531 |     -2728071 |      538805 |        23797 |        5770 |      865163 |     957035 |       0.4  |         0.18 |      1.01 |           1    |             0.23 |             85548 | False     |
|  50 |        7 | fixed2.0 |    405452 |  351223 | 1077712 |      -66730 |      2419897 |  107589 |     -3932477 |      570562 |       109962 |        9748 |     -339244 |     988793 |      -0.16 |        -0.51 |      0.2  |           1    |             0.4  |            143369 | False     |
|  50 |        7 | fixed3.0 |   1645069 | 1030988 | 2840287 |      842579 |      5224245 |   73244 |     -1629490 |      327289 |       148734 |       -4751 |     1963743 |     745520 |       0.83 |         0.63 |      1.81 |           1    |             0.61 |            221636 | False     |
|  50 |        7 | fixed4.0 |   1857164 | 1328143 | 3234861 |      508992 |      6224643 | -234788 |      -222811 |      253624 |       164699 |       -5825 |     3370423 |     671854 |       1.39 |         1.18 |      2.16 |           1    |             0.75 |            278736 | False     |
|  50 |        7 | flat0    |   2066052 | 3220108 | 4253735 |      184691 |      9170101 | -176331 |      1163951 |      226718 |       353247 |       -5825 |     4757184 |     644948 |       1.84 |         1.47 |      2.95 |           1    |             1    |            404446 | False     |
|  67 |        9 | trail30  |    119251 | -188998 | -179543 |     -514451 |       137718 |    7549 |      1372528 |      -25512 |       294982 |      -36872 |     4965761 |     392718 |       2.14 |         2.15 |      2.08 |          31.63 |             1    |            288890 | True      |
|  67 |        9 | trail45  |    -67199 |  -50398 | -220893 |     -722898 |       258692 |   39624 |      1215606 |      -34243 |       429284 |      -34717 |     4808840 |     383988 |       2.13 |         2.13 |      2.44 |          45.98 |             1    |            288890 | True      |
|  67 |        9 | trail60  |    483476 |  164877 |  755132 |      -83790 |      1675865 |  -69001 |       341155 |      261928 |       132276 |      -30765 |     3934389 |     680159 |       1.67 |         1.61 |      2.6  |          60.67 |             1    |            288890 | False     |
|  67 |        9 | trail90  |   1820951 | 1174827 | 3477132 |     1711898 |      5887640 |  512499 |      1809777 |      299263 |       357623 |      -14523 |     5403010 |     717493 |       2.08 |         1.85 |      2.53 |          87.32 |             1    |            288890 | False     |
|  67 |        9 | fixed1.5 |    287552 |   90974 |  347389 |     -204855 |       927001 |   61093 |     -2911360 |      578000 |        40895 |       -4655 |      681873 |     996231 |       0.32 |         0.08 |      0.88 |           1    |             0.23 |             61106 | False     |
|  67 |        9 | fixed2.0 |    289609 |  250874 |  769794 |      -47664 |      1728498 |   76849 |     -4168192 |      679713 |        62947 |       17751 |     -574959 |    1097944 |      -0.28 |        -0.46 |     -0.07 |           1    |             0.4  |            102406 | False     |
|  67 |        9 | fixed3.0 |   1175049 |  736420 | 2028777 |      601842 |      3731603 |   52317 |     -1429293 |      332640 |       214602 |       -2378 |     2163941 |     750870 |       0.93 |         0.71 |      1.83 |           1    |             0.61 |            158311 | False     |
|  67 |        9 | fixed4.0 |   1326546 |  948674 | 2310615 |      363566 |      4446173 | -167706 |       677424 |      135269 |       230315 |       -3282 |     4270657 |     553499 |       1.69 |         1.55 |      2.25 |           1    |             0.75 |            199097 | False     |
|  67 |        9 | flat0    |   1475751 | 2300077 | 3038382 |      131922 |      6550072 | -125951 |      1566777 |      124054 |       384649 |       -3282 |     5160010 |     542284 |       1.99 |         1.69 |      2.93 |           1    |             1    |            288890 | False     |
|  80 |       11 | trail30  |     71551 | -113399 | -107726 |     -308671 |        82631 |    4530 |      1549556 |      -25509 |       281629 |      -24516 |     5142790 |     392721 |       2.23 |         2.13 |      2.06 |          31.63 |             1    |            173334 | True      |
|  80 |       11 | trail45  |    -40319 |  -30239 | -132536 |     -433739 |       155215 |   23775 |       959610 |      -34806 |       458744 |      -27186 |     4552844 |     383424 |       2.02 |         2.06 |      2.18 |          45.98 |             1    |            173334 | True      |
|  80 |       11 | trail60  |    290086 |   98926 |  453079 |      -50274 |      1005519 |  -41400 |      1047464 |       84126 |       194339 |      -35223 |     4640698 |     502356 |       2.01 |         1.88 |      2.76 |          60.67 |             1    |            173334 | False     |
|  80 |       11 | trail90  |   1092571 |  704896 | 2086279 |     1027139 |      3532584 |  307500 |      2514140 |      123258 |       364364 |      -12081 |     6107373 |     541489 |       2.36 |         2.24 |      2.89 |          87.32 |             1    |            173334 | False     |
|  80 |       11 | fixed1.5 |    172531 |   54585 |  208434 |     -122913 |       556200 |   36656 |     -3617459 |      416306 |        27037 |       15827 |      -24225 |     834536 |      -0.01 |         0.05 |      0.09 |           1    |             0.23 |             36663 | False     |
|  80 |       11 | fixed2.0 |    173765 |  150524 |  461876 |      -28598 |      1037099 |   46109 |     -5047837 |     1353640 |       -30157 |        2313 |    -1454603 |    1771871 |      -0.79 |        -0.86 |     -0.5  |           1    |             0.4  |             61444 | False     |
|  80 |       11 | fixed3.0 |    705030 |  441852 | 1217266 |      361105 |      2238962 |   31390 |     -1163592 |      283452 |        81855 |       -6853 |     2429642 |     701682 |       1.07 |         0.87 |      2.04 |           1    |             0.61 |             94987 | False     |
|  80 |       11 | fixed4.0 |    795927 |  569204 | 1386369 |      218139 |      2667704 | -100624 |      1311909 |       74855 |       240069 |      -10902 |     4905142 |     493086 |       1.98 |         1.74 |      2.88 |           1    |             0.75 |            119458 | False     |
|  80 |       11 | flat0    |    885451 | 1380046 | 1823029 |       79153 |      3930043 |  -75570 |      2946700 |       42950 |       414749 |      -10902 |     6539933 |     461181 |       2.56 |         2.06 |      4.17 |           1    |             1    |            173334 | False     |
|  90 |       13 | trail30  |     23850 |  -37800 |  -35909 |     -102890 |        27544 |    1510 |      1498820 |       -7228 |       267382 |      -15705 |     5092053 |     411002 |       2.22 |         2.22 |      2.01 |          31.63 |             1    |             57778 | True      |
|  90 |       13 | trail45  |    -13440 |  -10080 |  -44179 |     -144580 |        51738 |    7925 |      1394311 |      -34171 |       412022 |      -26330 |     4987544 |     384059 |       2.21 |         2.25 |      2.34 |          45.98 |             1    |             57778 | True      |
|  90 |       13 | trail60  |     96695 |   32975 |  151026 |      -16758 |       335173 |  -13800 |      1448341 |      -75674 |       208906 |      -29819 |     5041574 |     342556 |       2.25 |         2.32 |      2.66 |          60.67 |             1    |             57778 | True      |
|  90 |       13 | trail90  |    364190 |  234965 |  695426 |      342380 |      1177528 |  102500 |      3690286 |       22321 |       465105 |      -23974 |     7283520 |     440552 |       2.89 |         2.64 |      3.48 |          87.32 |             1    |             57778 | False     |
|  90 |       13 | fixed1.5 |     57510 |   18195 |   69478 |      -40971 |       185400 |   12219 |     -4031132 |      967963 |        39088 |        4685 |     -437898 |    1386193 |      -0.23 |         0.01 |     -0.16 |           1    |             0.23 |             12221 | False     |
|  90 |       13 | fixed2.0 |     57922 |   50175 |  153959 |       -9533 |       345700 |   15370 |     -5313975 |     1610184 |       -16159 |      -15192 |    -1720741 |    2028414 |      -0.94 |        -0.95 |     -0.97 |           1    |             0.4  |             20481 | False     |
|  90 |       13 | fixed3.0 |    235010 |  147284 |  405755 |      120368 |       746321 |   10463 |     -1697419 |      117202 |        95745 |      -16032 |     1895814 |     535432 |       0.86 |         0.65 |      1.49 |           1    |             0.61 |             31662 | False     |
|  90 |       13 | fixed4.0 |    265309 |  189735 |  462123 |       72713 |       889235 |  -33541 |      1820484 |       33628 |       243781 |       -8193 |     5413718 |     451858 |       2.19 |         1.75 |      2.99 |           1    |             0.75 |             39819 | False     |
|  90 |       13 | flat0    |    295150 |  460015 |  607676 |       26384 |      1310014 |  -25190 |      4273451 |       11233 |       410299 |       -8193 |     7866685 |     429463 |       3.04 |         2.24 |      4.95 |           1    |             1    |             57778 | False     |

A_* = rules-free delta in $ (14/14) by window (clean 2023-08..2025-07, H2 2026-02-07.., OOS 2024-02.., L8W last 8 weeks), A_OOS_ci5/95 = 90% bootstrap interval over trading days; B_* from the harness; B_beats = beats the 60/1.0 base on net AND maxDD in BOTH OOS and L8W. runner_cost_usd = measured runner market-exit excess paid over the sample (alive rows).

## Table - ST book only (same columns)
|   X | rule     |   A_OOS |   A_OOS_ci5 |   A_OOS_ci95 |   A_L8W |   B_dOOS_net |   B_dOOS_dd |   B_dL8W_net |   B_dL8W_dd | B_beats   |
|----:|:---------|--------:|------------:|-------------:|--------:|-------------:|------------:|-------------:|------------:|:----------|
|  50 | trail30  |  -81376 |     -362296 |       240813 |    9511 |       177076 |      -13125 |       229649 |      -19544 | True      |
|  50 | trail45  | -293616 |     -683462 |       151843 |   42831 |       -70713 |       46214 |       334540 |       -6356 | False     |
|  50 | trail60  |  442819 |     -236324 |      1202539 |  -15479 |       590541 |      112961 |       395664 |      -13647 | False     |
|  50 | trail90  | 2377374 |      632542 |      3892022 |  494261 |      1155943 |      104399 |       270702 |        4263 | False     |
|  50 | fixed1.5 |  206785 |     -209221 |       680393 |   48753 |     -1627605 |      135532 |       201866 |       50954 | False     |
|  50 | fixed2.0 |  728328 |       34341 |      1382280 |   30106 |     -1222337 |       47900 |        80633 |       -4127 | False     |
|  50 | fixed3.0 | 1614047 |      410558 |      2803344 |   72635 |      -586148 |       62733 |        94682 |       -8336 | False     |
|  50 | fixed4.0 | 2043748 |      569754 |      3637784 | -117201 |       674269 |       51246 |       190691 |       -1957 | False     |
|  50 | flat0    | 2525319 |     -254901 |      5390457 |  -45719 |      1338735 |       35911 |       232355 |       -1957 | False     |
|  67 | trail30  |  -58126 |     -258783 |       172009 |    6793 |       499742 |      -10381 |       241933 |      -19233 | True      |
|  67 | trail45  | -209726 |     -488187 |       108459 |   30593 |      -169419 |       37759 |       402971 |      -10228 | False     |
|  67 | trail60  |  316299 |     -168803 |       858956 |  -11057 |      1299587 |      103485 |       384860 |       -5596 | False     |
|  67 | trail90  | 1698124 |      451816 |      2780016 |  353043 |      1777668 |      110115 |       271223 |       -8768 | False     |
|  67 | fixed1.5 |  147703 |     -149443 |       485995 |   34824 |     -1635223 |       57104 |       115705 |       28178 | False     |
|  67 | fixed2.0 |  520234 |       24529 |       987343 |   21504 |     -2226429 |      160706 |       136150 |       -7867 | False     |
|  67 | fixed3.0 | 1152891 |      293256 |      2002389 |   51882 |      -458076 |      160539 |        76232 |       -8364 | False     |
|  67 | fixed4.0 | 1459820 |      406967 |      2598417 |  -83715 |       868585 |      127437 |       193417 |       -4314 | False     |
|  67 | flat0    | 1803799 |     -182072 |      3850327 |  -32657 |      1890802 |      126756 |       216210 |       -4314 | False     |
|  80 | trail30  |  -34875 |     -155270 |       103206 |    4076 |       414205 |       -6345 |       240862 |      -15368 | True      |
|  80 | trail45  | -125835 |     -292912 |        65076 |   18356 |       317788 |       43272 |       380962 |      -12228 | False     |
|  80 | trail60  |  189780 |     -101282 |       515374 |   -6634 |      1635866 |      -27868 |       283951 |      -15150 | True      |
|  80 | trail90  | 1018875 |      271089 |      1668009 |  211826 |      2497508 |       67568 |       272980 |      -12488 | False     |
|  80 | fixed1.5 |   88622 |      -89666 |       291597 |   20894 |     -1989070 |       60227 |       112677 |       11628 | False     |
|  80 | fixed2.0 |  312141 |       14717 |       592406 |   12902 |     -2784031 |      136346 |        55134 |      -14776 | False     |
|  80 | fixed3.0 |  691734 |      175954 |      1201433 |   31129 |     -1360508 |      142966 |        92257 |      -15803 | False     |
|  80 | fixed4.0 |  875892 |      244180 |      1559050 |  -50229 |      1035690 |       79794 |       194576 |      -11422 | False     |
|  80 | flat0    | 1082280 |     -109243 |      2310196 |  -19594 |      2588306 |       79502 |       215706 |      -11422 | False     |
|  90 | trail30  |  -11625 |      -51757 |        34402 |    1359 |       445101 |        6686 |       229488 |        3281 | False     |
|  90 | trail45  |  -41945 |      -97637 |        21692 |    6119 |       900495 |       25588 |       376424 |      -14578 | False     |
|  90 | trail60  |   63260 |      -33761 |       171791 |   -2211 |      1967178 |      -15475 |       263321 |      -22371 | True      |
|  90 | trail90  |  339625 |       90363 |       556003 |   70609 |      3117023 |      -13075 |       270916 |      -13284 | True      |
|  90 | fixed1.5 |   29541 |      -29889 |        97199 |    6965 |     -2193814 |      117803 |       105434 |         764 | False     |
|  90 | fixed2.0 |  104047 |        4906 |       197469 |    4301 |     -2756604 |       59094 |        74267 |      -24232 | False     |
|  90 | fixed3.0 |  230578 |       58651 |       400478 |   10376 |     -1138104 |       11284 |       114705 |      -23854 | False     |
|  90 | fixed4.0 |  291964 |       81393 |       519683 |  -16743 |      1310732 |      -33661 |       201929 |      -18530 | True      |
|  90 | flat0    |  360760 |      -36414 |       770065 |   -6531 |      3282002 |      -33661 |       219541 |      -18530 | True      |

## Table - HM book only (same columns)
|   X | rule     |   A_OOS |   A_OOS_ci5 |   A_OOS_ci95 |   A_L8W |   B_dOOS_net |   B_dOOS_dd |   B_dL8W_net |   B_dL8W_dd | B_beats   |
|----:|:---------|--------:|------------:|-------------:|--------:|-------------:|------------:|-------------:|------------:|:----------|
|  50 | trail30  | -169984 |     -429545 |       117153 |    1058 |       597993 |       -4364 |       115817 |        8303 | False     |
|  50 | trail45  |  -15634 |     -345753 |       399897 |   12643 |       146371 |       -8884 |       245049 |      -36316 | True      |
|  50 | trail60  |  614366 |       89644 |      1209230 |  -81122 |       321457 |      110363 |       203191 |      -44504 | False     |
|  50 | trail90  | 2490611 |     1350240 |      3939243 |  223238 |      1587700 |       40118 |       174074 |      -32765 | False     |
|  50 | fixed1.5 |  279560 |     -152752 |       764786 |   36778 |      -774113 |       81225 |       -64315 |       66803 | False     |
|  50 | fixed2.0 |  349384 |     -224397 |      1136810 |   77483 |     -1320801 |       12898 |         5557 |       63096 | False     |
|  50 | fixed3.0 | 1226240 |      284264 |      2343077 |     609 |     -1852249 |      156688 |        20171 |        3687 | False     |
|  50 | fixed4.0 | 1191113 |       22289 |      2745608 | -117587 |      -296085 |      191183 |        50445 |      -14097 | False     |
|  50 | flat0    | 1728416 |     -119137 |      4175100 | -130612 |       577743 |      140185 |       197328 |      -35175 | False     |
|  67 | trail30  | -121417 |     -306818 |        83681 |     756 |       327364 |       -5997 |       159145 |        9576 | False     |
|  67 | trail45  |  -11167 |     -246967 |       285641 |    9031 |       830728 |      -10137 |       227077 |      -40135 | True      |
|  67 | trail60  |  438833 |       64031 |       863736 |  -57944 |      1071806 |       13436 |       205835 |      -31804 | False     |
|  67 | trail90  | 1779008 |      964457 |      2813745 |  159456 |      2297598 |      -45197 |       283011 |      -38479 | True      |
|  67 | fixed1.5 |  199686 |     -109108 |       546276 |   26270 |     -1251298 |      221530 |       -55366 |       62241 | False     |
|  67 | fixed2.0 |  249560 |     -160283 |       812007 |   55345 |     -2100699 |       61286 |         -218 |       63950 | False     |
|  67 | fixed3.0 |  875886 |      203046 |      1673626 |     435 |     -1592641 |      112686 |        80302 |       16346 | False     |
|  67 | fixed4.0 |  850795 |       15920 |      1961148 |  -83991 |      -419609 |      166069 |       120368 |      -28770 | False     |
|  67 | flat0    | 1234583 |      -85098 |      2982215 |  -93294 |      1124654 |      116309 |       251909 |      -33256 | False     |
|  80 | trail30  |  -72850 |     -184091 |        50209 |     454 |       455348 |       -8889 |       183272 |       -8508 | True      |
|  80 | trail45  |   -6700 |     -148180 |       171384 |    5419 |       827667 |      -15029 |       203214 |       -7620 | True      |
|  80 | trail60  |  263300 |       38419 |       518241 |  -34766 |      1571197 |      -73404 |       209993 |      -39249 | True      |
|  80 | trail90  | 1067405 |      578674 |      1688247 |   95674 |      2809720 |      -55722 |       329961 |      -24486 | True      |
|  80 | fixed1.5 |  119812 |      -65465 |       327766 |   15762 |     -1564632 |       92053 |       -39148 |       52845 | False     |
|  80 | fixed2.0 |  149736 |      -96170 |       487204 |   33207 |     -2016374 |       67147 |        11663 |       64029 | False     |
|  80 | fixed3.0 |  525532 |      121827 |      1004176 |     261 |     -1882661 |        3963 |        31237 |       64645 | False     |
|  80 | fixed4.0 |  510477 |        9552 |      1176689 |  -50394 |       237808 |       26017 |       215811 |      -21251 | False     |
|  80 | flat0    |  740750 |      -51059 |      1789329 |  -55976 |      2126178 |      -40723 |       369362 |      -28391 | True      |
|  90 | trail30  |  -24283 |      -61364 |        16736 |     151 |       402168 |       -2427 |       184866 |      -13264 | True      |
|  90 | trail45  |   -2233 |      -49393 |        57128 |    1806 |       982138 |      -18942 |       209223 |      -30796 | True      |
|  90 | trail60  |   87767 |       12806 |       172747 |  -11589 |      1793720 |      -81813 |       263083 |      -31684 | True      |
|  90 | trail90  |  355802 |      192891 |       562749 |   31891 |      3598572 |      -92071 |       361042 |      -31389 | True      |
|  90 | fixed1.5 |   39937 |      -21822 |       109255 |    5254 |     -1234610 |       16528 |       -32311 |       64929 | False     |
|  90 | fixed2.0 |   49912 |      -32057 |       162401 |   11069 |     -1885683 |       17604 |         4394 |       62363 | False     |
|  90 | fixed3.0 |  175177 |       40609 |       334725 |      87 |     -1937596 |        3226 |        14105 |       63908 | False     |
|  90 | fixed4.0 |  170159 |        3184 |       392230 |  -16798 |       411961 |      -53094 |       288367 |      -27951 | True      |
|  90 | flat0    |  246917 |      -17020 |       596443 |  -18659 |      2926799 |      -76805 |       437273 |      -27951 | True      |

## Cells marked by the harness (B beats the 60/1.0 base on net AND maxDD in OOS and L8W), both books
| cell              |   B_dOOS_net |   B_dOOS_dd |   B_dL8W_net |   B_dL8W_dd |   A_OOS_rules_free |   A_L8W |   null_rank |   p_null_beats_both |
|:------------------|-------------:|------------:|-------------:|------------:|-------------------:|--------:|------------:|--------------------:|
| 50% off + trail30 |      1470096 |      -27731 |       256057 |      -37875 |            -251359 |   10568 |       1     |                   0 |
| 50% off + trail45 |       261888 |      -32618 |       450436 |      -32936 |            -309249 |   55473 |       0.975 |                   0 |
| 67% off + trail30 |      1372528 |      -25511 |       294982 |      -36871 |            -179542 |    7549 |       1     |                   0 |
| 67% off + trail45 |      1215606 |      -34242 |       429283 |      -34716 |            -220892 |   39624 |       1     |                   0 |
| 80% off + trail30 |      1549556 |      -25509 |       281629 |      -24515 |            -107725 |    4529 |       1     |                   0 |
| 80% off + trail45 |       959610 |      -34806 |       458744 |      -27185 |            -132535 |   23774 |       1     |                   0 |
| 90% off + trail30 |      1498819 |       -7228 |       267382 |      -15704 |             -35908 |    1509 |       1     |                   0 |
| 90% off + trail45 |      1394310 |      -34171 |       412022 |      -26330 |             -44178 |    7924 |       1     |                   0 |
| 90% off + trail60 |      1448340 |      -75674 |       208906 |      -29818 |             151026 |  -13800 |       1     |                   0 |

Null (runner outcome AND duration permuted together across the affected rows within book, 40 reps, harness B, rank of OOS dnet; P(null beats the base in both windows)): ranks 0.98-1.00, P = 0.0 for every marked cell. The marked cells are all the SHORT-trail cells (T = 30/45, and 60 at X = 90%): fast exits that bank the runner quickly. BUT their rules-free edge (column A) is NEGATIVE or about zero (e.g. 50% + trail30: A_OOS -$251k): the harness gain comes from how an earlier/later realisation of the runner shifts the day caps, locks and the MTM path (the full-size MTM after the target is a known distortion), not from a better exit. Treat the B marks as a harness-interplay result, not a runner edge.

## Verdict
1. In expectation the runner is a martingale (mean runner exit ~ +60 pts = what the target gave up) before costs; runner market exits then cost the measured excess over the sample (runner_cost_usd: $404k at 50% off for any market-exit rule, $289k at 67%, less at larger X; $86-279k for the fixed-target cells, which exit by limit when they hit). Only the widest trail (T = 90) shows a positive pure drift (+3.8 pts mean).
2. Pure runner edge (A, rules-free, on rows that trade in the base, 14/14, OOS 2024-02..): trail90 +$4.87M (50% off), +$3.48M (67%), +$2.09M (80%), +$0.70M (90%), 90% intervals above zero, all positive in clean and H2; L8W +$717k / +$512k / +$308k / +$103k. Fixed 3R/4R and hold-to-flatten at 50-67% off are also positive OOS (+$1.2M-4.3M) but negative in L8W (fixed4/flat -$126k to -$235k at 50-67%). Tight trails (30/45) are negative or zero.
3. Cost of that edge: the harness maxDD rises with the runner size (OOS maxDD $0.60M-$1.27M vs $0.42M for the 60/1.0 base for 50-67% off with trail60-90/fixed/flat; trail90 at 90% off $0.44M). No wide-runner cell beats the base on maxDD in BOTH OOS and L8W (B_dOOS_dd positive for every cell with positive A and L8W), so none passes the net AND maxDD bar.
4. Walk-forward 12/3/3 (cell chosen per fold on the fit window by the rules-free net; base kept if none improves): picks 50%-off wide runners (trail45, fixed4, flat, then trail90 from 2025) ; OOS dnet +$263k but maxDD +$356k worse (774k vs 418k); L8W +$353k / -$6k; does not beat; null (random cell per fold, 60 reps) rank 0.57-0.63.
5. Extra orders: +1 runner exit order per affected trade (target limit + runner exit) plus stop moves for trails (extra_orders column: 1 for fixed/flatten cells; for trails 1 + the number of +1-pt steps of the running maximum = about 32 / 46 / 61 / 87 stop modifications per trade for T = 30 / 45 / 60 / 90 - a live implementation would move the stop in coarser steps); lots rounding as logged. No gate softened; no cell is recommended. If the user wants the wide-trail idea tested live: 50%/T90 is the cell with the largest pure edge (+$4.9M OOS rules-free) and it needs a risk budget for maxDD +$356k.
Caveats: 1-second path (adverse extreme first inside a second) is conservative for trails; flatten for the runner = next 16:55 ET; the day-rule harness treats the whole trade as realised at the runner exit; the per-book scope tables (ST/HM) are in the CSV and the per-book sections above.
