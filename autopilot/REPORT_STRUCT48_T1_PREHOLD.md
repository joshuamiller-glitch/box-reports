# STRUCT48 Track 1 - PRE-HOLDOUT report (WF-PRE 2024-02..2025-06 and IS only; holdout and L8W not read)
Prereg l2vast/struct48/prereg/T1_prereg.md (sha256 in DECISIONS.md), selection out/T15_selection.json. Benchmark Set A WF-PRE: $17,549/wk, SD 97,533, maxDD 401,293, worst week -136,494, 31.9 trades/wk (75 weeks). Engine identity with no rule exact. Cells scored: 151 (140 grid + 10 T1.5 + T14_C); DSR trials N=28,337 (corrected 27,682 + STRUCT48 ledger), SR0=0.351.

## Verdict (pre-holdout)
Cells passing all five pre-holdout conditions (mean up, maxDD not worse, CI excludes 0, placebo >= 0.95, neighbours agree): **0**. No cell's week-block bootstrap CI excludes zero (best lower bound among all 151 cells is +0). Placebo was computed (informational) for the 42 cells with mean up and maxDD not worse; 3 reach rank 0.95. Per the frozen rule the best-by-WF-PRE cells were used for T1.5, all labelled NOT PASSED: T1.1 T11_N2_book_lockon, T1.2 T12_A0000_L0800_N1100, T1.3 T13_M2_R0. Holdout conditions are added after this text is hashed.

Caveats: year share > 1.0 means one year gains more than the total (the other loses); nearly all positive window cells (NY first entry not before 11:00, cells with london cut 07:30-08:00) are 2024-heavy. Stop-count rules count phantom trades cancelled by per-book locks (see prereg). n/c = placebo not computed (mean not up or maxDD worse).

## Set A direction baseline (T1.4 first item), WF-PRE 2024-02..2025-06 and IS 2023-02..2024-01

(from code/ls_base.py, 14/14 locks on, $ per week) WF-PRE: long-only 14,591 (1,214 trades, 901 $/trade), short-only 2,958 (1,179 trades, 188 $/trade); IS: long-only 23,670 (730 trades), short-only -9,999 (662 trades, -785 $/trade). Shorts are the weak side in both pre-holdout windows (the whole-window figures are added in the final report).

## T1.1 stop-count halt (13 cells; REF = Set A with per-book -2R/+5R locks off; all deltas vs Set A locks on)
| cell | d$/wk | dMaxDD | dSD | CI95 | placebo | 2x d$/wk | yr share | DSR | IS d$/wk | fails (of c1 mean, c2 DD, c3 CI, c4 plc, c6 nb) |
|---|---|---|---|---|---|---|---|---|---|---|
| T11_N2_book_lockon | +5795 | -2087 | +2528 | [-1443,+13635] | 0.80 | +3973 | 0.71 | 0.06 | -660 | CI, placebo, nb |
| T11_N3_pool_lockon | +3196 | -64142 | -2667 | [-6951,+13989] | 0.61 | -963 | 1.28 | 0.01 | +947 | CI, placebo, nb |
| T11_N2_book_lockoff | +1876 | +80070 | +8903 | [-9714,+14249] | n/c | -2997 | 1.22 | 0.00 | -7582 | DD, CI, placebo, nb |
| T11_N1_book_lockon | +1052 | +59019 | -10249 | [-15302,+17911] | n/c | +1378 | 5.29 | 0.00 | -4114 | DD, CI, placebo, nb |
| T11_N3_book_lockoff | -40 | -21331 | +4760 | [-11176,+11378] | n/c | -11337 | 7.70 | 0.00 | -10792 | mean, CI, placebo, nb |
| T11_N2_pool_lockon | -139 | +8610 | -3358 | [-14950,+15296] | n/c | -3887 | 29.36 | 0.00 | -4630 | mean, DD, CI, placebo, nb |
| T11_N3_pool_lockoff | -358 | +82302 | +3944 | [-12769,+12948] | n/c | -5785 | 6.30 | 0.00 | -4031 | mean, DD, CI, placebo, nb |
| T11_N1_pool_lockon | -522 | +10790 | -6871 | [-17764,+16137] | n/c | -3757 | 1.65 | 0.00 | +1112 | mean, DD, CI, placebo, nb |
| T11_N3_book_lockon | -578 | +0 | -1593 | [-3414,+1541] | n/c | -907 | 1.04 | 0.00 | +1875 | mean, CI, placebo |
| T11_REF_lockoff | -4095 | +104440 | +11201 | [-14827,+6634] | n/c | -13049 | 1.03 | 0.00 | -10589 | mean, DD, CI, placebo, nb |
| T11_N1_pool_lockoff | -5197 | +82288 | -1768 | [-23121,+10686] | n/c | -8569 | 0.52 | 0.00 | +722 | mean, DD, CI, placebo, nb |
| T11_N2_pool_lockoff | -7879 | +96437 | +4386 | [-22612,+7294] | n/c | -12329 | 0.60 | 0.00 | -8178 | mean, DD, CI, placebo, nb |
| T11_N1_book_lockoff | -7966 | +130529 | +1535 | [-22877,+6323] | n/c | -6465 | 0.74 | 0.00 | -5769 | mean, DD, CI, placebo, nb |

## T1.3 max entries x re-arm (15 cells)
| cell | d$/wk | dMaxDD | dSD | CI95 | placebo | 2x d$/wk | yr share | DSR | IS d$/wk | fails (of c1 mean, c2 DD, c3 CI, c4 plc, c6 nb) |
|---|---|---|---|---|---|---|---|---|---|---|
| T13_M2_R0 | +10160 | +71357 | -7116 | [-3378,+23833] | n/c | +6712 | 0.69 | 0.06 | -5263 | DD, CI, placebo |
| T13_M2_R15 | +9572 | -39453 | -9158 | [-3823,+25020] | 0.93 | +5585 | 0.58 | 0.03 | -5245 | CI, placebo |
| T13_M2_R30 | +4091 | +23952 | -5905 | [-10549,+18678] | n/c | +393 | 0.62 | 0.01 | -11607 | DD, CI, placebo, nb |
| T13_R15_only | +3633 | -59812 | -5357 | [-4275,+13257] | 0.63 | +1798 | 0.64 | 0.01 | -6632 | CI, placebo, nb |
| T13_M3_R15 | +1772 | -58177 | -4405 | [-8524,+13705] | 0.53 | +1731 | 0.64 | 0.00 | -7828 | CI, placebo |
| T13_M3_R0 | +843 | +37093 | -1759 | [-9763,+10809] | n/c | +1246 | 4.40 | 0.00 | -918 | DD, CI, placebo |
| T13_M1_R60 | +117 | -46183 | -12664 | [-20839,+19405] | 0.53 | -1238 | 5.37 | 0.00 | -12487 | CI, placebo, nb |
| T13_M1_R15 | -1704 | -46705 | -7510 | [-22870,+16715] | n/c | -5060 | 2.72 | 0.00 | -13304 | mean, CI, placebo, nb |
| T13_M3_R30 | -2448 | +64977 | -5758 | [-13161,+9029] | n/c | -3676 | 0.91 | 0.00 | -5861 | mean, DD, CI, placebo |
| T13_R30_only | -3472 | +84947 | -5178 | [-13479,+6512] | n/c | -3307 | 0.85 | 0.00 | -4030 | mean, DD, CI, placebo, nb |
| T13_M1_R30 | -3906 | -9961 | -10075 | [-24088,+15046] | n/c | -5496 | 1.36 | 0.00 | -14012 | mean, CI, placebo |
| T13_M1_R0 | -4055 | +18770 | -7076 | [-25128,+14765] | n/c | -5464 | 1.26 | 0.00 | -13215 | mean, DD, CI, placebo, nb |
| T13_M2_R60 | -6552 | +72187 | -1753 | [-24280,+11408] | n/c | -11858 | 1.05 | 0.00 | -10619 | mean, DD, CI, placebo |
| T13_R60_only | -8186 | +49685 | +2232 | [-22783,+7132] | n/c | -9448 | 0.81 | 0.00 | -13050 | mean, DD, CI, placebo, nb |
| T13_M3_R60 | -10007 | +47022 | -1576 | [-22896,+4633] | n/c | -8756 | 0.73 | 0.00 | -13848 | mean, DD, CI, placebo, nb |

## T1.4 direction-asymmetric (36 cells + T14_C), sorted by WF-PRE mean delta
| cell | d$/wk | dMaxDD | dSD | CI95 | placebo | 2x d$/wk | yr share | DSR | IS d$/wk | fails (of c1 mean, c2 DD, c3 CI, c4 plc, c6 nb) |
|---|---|---|---|---|---|---|---|---|---|---|
| T14_S_s50_t1.5_n14 | +8343 | -99801 | +1595 | [-7761,+26193] | 0.91 | +15123 | 1.22 | 0.02 | -3270 | CI, placebo |
| T14_S_s50_t1.0_n14 | +6231 | -88142 | +8789 | [-9682,+23178] | 0.78 | +8849 | 1.18 | 0.01 | +8614 | CI, placebo |
| T14_L_s60_t2.0_n14 | +5305 | +10999 | +10063 | [-6108,+17266] | n/c | +5225 | 0.61 | 0.01 | -1415 | DD, CI, placebo, nb |
| T14_S_s50_t2.0_n10 | +5260 | -52095 | -4868 | [-12197,+23888] | 0.70 | +7073 | 0.86 | 0.01 | -3169 | CI, placebo |
| T14_S_s50_t1.5_n10 | +4862 | -131538 | -3184 | [-13489,+23347] | 0.63 | +7035 | 1.63 | 0.01 | -9076 | CI, placebo |
| T14_S_s50_t1.0_n10 | +3368 | -103108 | -2001 | [-14018,+22988] | 0.85 | -355 | 1.79 | 0.00 | +3244 | CI, placebo |
| T14_L_s60_t2.0_n10 | +3363 | +3541 | +5801 | [-11860,+19493] | n/c | +147 | 1.18 | 0.01 | -9070 | DD, CI, placebo, nb |
| T14_C | +3312 | +3466 | +15443 | [-17839,+24115] | n/c | +11290 | 0.62 | 0.00 | -8618 | DD, CI, placebo |
| T14_L_s50_t1.5_n10 | +2876 | -39941 | -9045 | [-13547,+20629] | 0.45 | +2032 | 1.79 | 0.00 | -14235 | CI, placebo, nb |
| T14_S_s50_t2.0_n14 | +2369 | -60452 | -1545 | [-17211,+22591] | 0.67 | +11190 | 1.11 | 0.00 | +2060 | CI, placebo |
| T14_L_s50_t2.0_n10 | +1219 | +138309 | -9711 | [-16445,+20600] | n/c | -992 | 2.45 | 0.00 | -14807 | DD, CI, placebo |
| T14_S_s60_t1.0_n14 | +0 | +0 | +0 | [+0,+0] | n/c | +0 | nan | nan | +0 | mean, CI, placebo, nb |
| T14_L_s60_t1.0_n14 | +0 | +0 | +0 | [+0,+0] | n/c | +0 | nan | nan | +0 | mean, CI, placebo, nb |
| T14_S_s60_t2.0_n14 | -564 | -37977 | +1513 | [-18011,+17265] | n/c | +4940 | 5.08 | 0.00 | -9572 | mean, CI, placebo, nb |
| T14_L_s60_t1.0_n10 | -659 | +6476 | -3270 | [-12551,+13365] | n/c | -3459 | 1.22 | 0.00 | -4456 | mean, DD, CI, placebo, nb |
| T14_L_s60_t1.5_n10 | -1703 | +5714 | -851 | [-17302,+14477] | n/c | -7259 | 1.37 | 0.00 | -11423 | mean, DD, CI, placebo, nb |
| T14_S_s60_t1.0_n10 | -2015 | -42157 | +1571 | [-13663,+9034] | n/c | -4187 | 2.97 | 0.00 | +602 | mean, CI, placebo, nb |
| T14_S_s75_t1.0_n10 | -2315 | +28608 | -7545 | [-16461,+12305] | n/c | +34 | 2.35 | 0.00 | -6672 | mean, DD, CI, placebo, nb |
| T14_L_s75_t2.0_n14 | -2747 | +41592 | +9652 | [-16922,+11351] | n/c | -7499 | 1.53 | 0.00 | -7593 | mean, DD, CI, placebo, nb |
| T14_S_s60_t1.5_n10 | -3003 | +29876 | -8782 | [-16975,+12689] | n/c | +421 | 0.65 | 0.00 | -14534 | mean, DD, CI, placebo, nb |
| T14_L_s60_t1.5_n14 | -3668 | +26453 | +1997 | [-15928,+8352] | n/c | -1537 | 0.70 | 0.00 | -8834 | mean, DD, CI, placebo, nb |
| T14_L_s75_t1.5_n10 | -3845 | +104684 | -1958 | [-20043,+12134] | n/c | -4056 | 1.88 | 0.00 | -14578 | mean, DD, CI, placebo, nb |
| T14_L_s50_t2.0_n14 | -3892 | +60200 | +2991 | [-20370,+13280] | n/c | -4796 | 0.51 | 0.00 | -7026 | mean, DD, CI, placebo |
| T14_S_s60_t1.5_n14 | -4997 | +119199 | -3788 | [-21336,+11668] | n/c | +155 | 0.69 | 0.00 | -7542 | mean, DD, CI, placebo, nb |
| T14_L_s50_t1.0_n14 | -5052 | +140806 | +541 | [-23994,+15928] | n/c | -9317 | 0.91 | 0.00 | -20294 | mean, DD, CI, placebo, nb |
| T14_L_s50_t1.5_n14 | -5194 | +73486 | -2066 | [-19658,+11368] | n/c | -11808 | 0.92 | 0.00 | -7684 | mean, DD, CI, placebo, nb |
| T14_L_s75_t1.5_n14 | -6852 | +133353 | +4516 | [-23133,+8235] | n/c | -10883 | 1.49 | 0.00 | -8124 | mean, DD, CI, placebo, nb |
| T14_S_s60_t2.0_n10 | -6881 | +81547 | -1029 | [-23355,+10670] | n/c | -4682 | 0.60 | 0.00 | -12053 | mean, DD, CI, placebo, nb |
| T14_L_s75_t1.0_n14 | -7670 | +77548 | -6293 | [-20680,+6240] | n/c | -16103 | 0.75 | 0.00 | -5784 | mean, DD, CI, placebo, nb |
| T14_L_s75_t1.0_n10 | -8277 | +300275 | -5293 | [-23964,+7843] | n/c | -11405 | 0.74 | 0.00 | -15433 | mean, DD, CI, placebo, nb |
| T14_L_s50_t1.0_n10 | -8985 | +165975 | -2327 | [-31225,+14791] | n/c | -8345 | 0.50 | 0.00 | -15347 | mean, DD, CI, placebo, nb |
| T14_S_s75_t1.5_n10 | -9771 | +176758 | +2678 | [-29248,+11859] | n/c | -9082 | 0.93 | 0.00 | -12040 | mean, DD, CI, placebo, nb |
| T14_S_s75_t1.5_n14 | -10141 | +304014 | -2287 | [-27785,+9969] | n/c | -5929 | 0.61 | 0.00 | -5999 | mean, DD, CI, placebo, nb |
| T14_S_s75_t1.0_n14 | -11227 | +193073 | -5920 | [-24974,+5882] | n/c | -10608 | 0.75 | 0.00 | -6910 | mean, DD, CI, placebo, nb |
| T14_L_s75_t2.0_n10 | -12326 | +163948 | -5049 | [-29125,+2885] | n/c | -9853 | 0.78 | 0.00 | -11801 | mean, DD, CI, placebo, nb |
| T14_S_s75_t2.0_n14 | -17125 | +238745 | +2153 | [-34714,+1625] | n/c | -11928 | 0.66 | 0.00 | -10645 | mean, DD, CI, placebo, nb |
| T14_S_s75_t2.0_n10 | -22465 | +627531 | +993 | [-42001,-2723] | n/c | -19576 | 0.63 | 0.00 | -9458 | mean, DD, CI, placebo, nb |

## T1.5 combination (T1.1 N2 book lockon x T1.2 A0000_L0800_N1100 x T1.3 M2_R0) with neighbours
| cell | d$/wk | dMaxDD | dSD | CI95 | placebo | 2x d$/wk | yr share | DSR | IS d$/wk | fails (of c1 mean, c2 DD, c3 CI, c4 plc, c6 nb) |
|---|---|---|---|---|---|---|---|---|---|---|
| T15_COMBO | +9094 | -13289 | -7370 | [-7297,+25030] | 0.91 | +8674 | 0.98 | 0.03 | -2749 | CI, placebo |
| T15_NB_0_T11_N3_book_lockon | +9094 | -13289 | -7370 | [-7297,+25030] | 0.89 | +8674 | 0.98 | 0.03 | -2749 | CI, placebo, nb |
| T15_NB_1_T12_A0000_L0730_N1100 | +8831 | +6327 | -6224 | [-7293,+25657] | n/c | +9397 | 0.95 | 0.03 | -814 | DD, CI, placebo, nb |
| T15_NB_2_T13_M2_R15 | +7627 | -75827 | -7866 | [-10554,+25247] | 0.86 | +9534 | 1.14 | 0.01 | -5943 | CI, placebo, nb |
| T15_NB_1_T12_A0030_L0800_N1100 | +7040 | +27455 | -6135 | [-9435,+23813] | n/c | +6783 | 1.20 | 0.01 | -2749 | DD, CI, placebo, nb |
| T15_NB_2_T13_M3_R0 | +6662 | -26432 | -4225 | [-11098,+24539] | 0.82 | +4491 | 1.81 | 0.01 | -2314 | CI, placebo, nb |
| T15_NB_1_T12_A0000_L0830_N1100 | +5463 | -42129 | -7715 | [-10836,+21699] | 0.77 | +5272 | 1.25 | 0.01 | -1700 | CI, placebo, nb |
| T15_NB_1_T12_A0000_L0800_N1030 | +4510 | -52544 | -7653 | [-11379,+20763] | 0.70 | +4268 | 1.26 | 0.01 | -1520 | CI, placebo, nb |
| T15_NB_2_T13_M1_R0 | +2154 | -87448 | -11323 | [-17327,+20371] | 0.59 | +1608 | 3.31 | 0.00 | -12645 | CI, placebo, nb |
| T15_NB_0_T11_N1_book_lockon | -1104 | +73019 | -12225 | [-18921,+16937] | n/c | +1432 | 6.90 | 0.00 | -11104 | mean, DD, CI, placebo, nb |

## T1.2 entry-window grid (76 cells): top 25 by WF-PRE mean delta; all cells in out/T1_pre_all_cells.csv
| cell | d$/wk | dMaxDD | dSD | CI95 | placebo | 2x d$/wk | yr share | DSR | IS d$/wk | fails (of c1 mean, c2 DD, c3 CI, c4 plc, c6 nb) |
|---|---|---|---|---|---|---|---|---|---|---|
| T12_A0000_L0800_N1100 | +12531 | -81373 | -7458 | [-3531,+30472] | 0.97 | +5239 | 1.04 | 0.05 | -2110 | CI |
| T12_A0000_L0730_N1100 | +11562 | -129481 | -2656 | [-4705,+28562] | 0.96 | +4986 | 1.06 | 0.04 | -633 | CI |
| T12_A0030_L0800_N1100 | +11249 | -81373 | -9186 | [-3977,+28358] | 0.94 | +2298 | 1.15 | 0.05 | -2110 | CI, placebo |
| T12_A0100_L0800_N1100 | +9761 | -81373 | -8677 | [-5545,+26103] | 0.92 | +3870 | 1.25 | 0.03 | -2100 | CI, placebo |
| T12_A0030_L0730_N1100 | +8842 | -40212 | -2123 | [-6639,+25712] | 0.89 | +1518 | 1.27 | 0.02 | -633 | CI, placebo |
| T12_A0100_L0730_N1100 | +8565 | -23715 | -2907 | [-6722,+25248] | 0.90 | +3051 | 1.23 | 0.02 | -624 | CI, placebo |
| T12_A0130_L0730_N1100 | +8510 | +24521 | -340 | [-5819,+24620] | n/c | +4044 | 1.25 | 0.03 | +96 | DD, CI, placebo |
| T12_A0000_L0830_N1100 | +8440 | -15775 | -3990 | [-8219,+26794] | 0.91 | +2103 | 1.26 | 0.02 | -1358 | CI, placebo |
| T12_A0130_L0800_N1100 | +8432 | -71645 | -4669 | [-6039,+24311] | 0.89 | +3550 | 1.44 | 0.03 | -762 | CI, placebo |
| T12_A0000_L0900_N1100 | +8400 | -16958 | -1448 | [-8637,+26696] | 0.92 | +2523 | 1.02 | 0.02 | +2799 | CI, placebo |
| T12_A0030_L0900_N1100 | +6612 | -17387 | -2444 | [-9040,+22854] | 0.88 | +908 | 1.11 | 0.01 | +2799 | CI, placebo |
| T12_A0030_L0830_N1100 | +6598 | -16204 | -5063 | [-8681,+24028] | 0.83 | -917 | 1.58 | 0.01 | -1358 | CI, placebo |
| T12_N1100_only | +5532 | -42018 | +1594 | [-6562,+17935] | 0.98 | +4640 | 0.79 | 0.01 | +2789 | CI, nb |
| T12_L0800_only | +5043 | +62542 | +2608 | [-2240,+13029] | n/c | +5948 | 0.73 | 0.04 | -7108 | DD, CI, placebo |
| T12_A0100_L0900_N1100 | +4551 | -20207 | -3092 | [-9993,+20363] | 0.81 | +3043 | 1.25 | 0.01 | +2828 | CI, placebo |
| T12_L0730_only | +4479 | +46418 | +3014 | [-3197,+12798] | n/c | +5480 | 0.87 | 0.02 | -8970 | DD, CI, placebo |
| T12_A0130_L0900_N1100 | +4399 | -17003 | -153 | [-9044,+19187] | 0.80 | +3138 | 1.43 | 0.01 | +4672 | CI, placebo |
| T12_A0100_L0830_N1100 | +3956 | -15823 | -5622 | [-11116,+20563] | 0.69 | +917 | 2.24 | 0.01 | -1349 | CI, placebo |
| T12_A0130_L0830_N1100 | +2574 | -15823 | -1513 | [-11288,+18114] | 0.58 | +916 | 3.30 | 0.00 | -11 | CI, placebo |
| T12_A0000_L0900_N1030 | +2450 | -18063 | -3318 | [-13202,+18750] | 0.67 | -1630 | 2.99 | 0.00 | +6230 | CI, placebo, nb |
| T12_L0830_only | +2215 | +110261 | +1239 | [-3703,+8380] | n/c | +820 | 0.89 | 0.01 | -5074 | DD, CI, placebo |
| T12_A0000_L0800_N1030 | +1927 | +8157 | -4710 | [-14132,+19572] | n/c | -921 | 3.84 | 0.00 | +1804 | DD, CI, placebo, nb |
| T12_A0130_L0800_N1000 | +1894 | -94598 | +1273 | [-7611,+11809] | 0.36 | +1803 | 1.99 | 0.00 | +1170 | CI, placebo |
| T12_A0000_L0900_N0930 | +1373 | +30384 | +1608 | [-9042,+13980] | n/c | -1294 | 2.20 | 0.00 | -2824 | DD, CI, placebo, nb |
| T12_A0100_L0800_N1000 | +1255 | -94598 | -2649 | [-8584,+12939] | 0.41 | -1095 | 1.44 | 0.00 | -649 | CI, placebo, nb |

Reference line in T1.1: Set A with per-book locks off is -4,095 $/wk and +104,440 maxDD vs locks on (WF-PRE): the per-book lock is worth that. Stop-count halts with locks off recover the mean in the N=2 per-book variant (+1,876 vs Set A) but every lockoff variant has maxDD worse than Set A (+80k to +130k, except N=3 variants -21k for per-book) and no CI excludes 0: the halt does not replace the -2R day lock on this evidence.
