# DS3_NEXT_FEATURES_F2 — desk-state family (item 2) and winning-day protection (item 5) — W-F2

Generated 2026-11-13 01:21Z. Shadow only, no PASS claim. Base sets: **L = JN05W2** (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, no WA_C1) and **J = JN05W2J** (the same five on JN04RM), both 43 / 43 months. Every cell below is the base plus ONE nf2 rule layer (outermost), reference = its own base on the same months. Prereg autopilot/NEXTF2_PREREG.md (sha line in DECISIONS.md). Exact engine, one set per job, TP engine; first-order screen only chose the cells (it overstates entry-stream rules).

## 0. Trend-week clause (first): sum of the base's 5 best weeks kept, and base winning weeks turned losing (per window)

| cell | base | window | 5 best weeks: base $ | cell $ | kept % | winning weeks turned losing | weeks |
|--|--|--|--|--|--|--|--|
| NF_D_OB_best_m2_L | JN05W2 | HOLD | 340478 | 328388 | 96.4 | 5 of 37 | 52 |
| NF_D_PL_day_half_m1p5_J | JN05W2J | HOLD | 262552 | 260843 | 99.3 | 1 of 38 | 52 |
| NF_D_PL_day_half_m1p5_L | JN05W2 | HOLD | 340478 | 324236 | 95.2 | 3 of 37 | 52 |
| NF_D_PL_day_half_m2_J | JN05W2J | HOLD | 262552 | 260027 | 99.0 | 1 of 38 | 52 |
| NF_D_PL_day_half_m2_L | JN05W2 | HOLD | 340478 | 324288 | 95.2 | 1 of 37 | 52 |
| NF_D_ST_half_2_J | JN05W2J | HOLD | 262552 | 242038 | 92.2 | 1 of 38 | 52 |
| NF_D_ST_half_2_L | JN05W2 | HOLD | 340478 | 304366 | 89.4 | 0 of 37 | 52 |
| NF_D_ST_half_3_J | JN05W2J | HOLD | 262552 | 258905 | 98.6 | 1 of 38 | 52 |
| NF_D_ST_half_4_J | JN05W2J | HOLD | 262552 | 258309 | 98.4 | 0 of 38 | 52 |
| NF_D_WD_fresh_3_J | JN05W2J | HOLD | 262552 | 113499 | 43.2 | 5 of 38 | 52 |
| NF_D_WD_fresh_3_L | JN05W2 | HOLD | 340478 | 195598 | 57.4 | 5 of 37 | 52 |
| NF_D_WD_half_3_L | JN05W2 | HOLD | 340478 | 318280 | 93.5 | 1 of 37 | 52 |
| NF_D_OB_best_m2_J | JN05W2J | L1M | 10523 | 20456 | 194.4 | 0 of 1 | 4 |
| NF_D_OB_best_m2_L | JN05W2 | L1M | 2425 | 27271 | 1124.5 | 0 of 2 | 4 |
| NF_D_PL_day_half_m1p5_J | JN05W2J | L1M | 10523 | -6709 | -63.8 | 0 of 1 | 4 |
| NF_D_PL_day_half_m1p5_L | JN05W2 | L1M | 2425 | 5317 | 219.2 | 0 of 2 | 4 |
| NF_D_PL_day_half_m2_J | JN05W2J | L1M | 10523 | -4348 | -41.3 | 0 of 1 | 4 |
| NF_D_PL_day_half_m2_L | JN05W2 | L1M | 2425 | 11301 | 466.0 | 0 of 2 | 4 |
| NF_D_ST_half_2_J | JN05W2J | L1M | 10523 | 10756 | 102.2 | 0 of 1 | 4 |
| NF_D_ST_half_2_L | JN05W2 | L1M | 2425 | 6538 | 269.6 | 0 of 2 | 4 |
| NF_D_ST_half_3_J | JN05W2J | L1M | 10523 | 9099 | 86.5 | 0 of 1 | 4 |
| NF_D_ST_half_3_L | JN05W2 | L1M | 2425 | 935 | 38.5 | 0 of 2 | 4 |
| NF_D_ST_half_4_J | JN05W2J | L1M | 10523 | 10058 | 95.6 | 0 of 1 | 4 |
| NF_D_ST_half_4_L | JN05W2 | L1M | 2425 | 3404 | 140.4 | 0 of 2 | 4 |
| NF_D_WD_fresh_3_J | JN05W2J | L1M | 10523 | -962 | -9.1 | 0 of 1 | 4 |
| NF_D_WD_fresh_3_L | JN05W2 | L1M | 2425 | -6942 | -286.2 | 1 of 2 | 4 |
| NF_D_WD_half_3_J | JN05W2J | L1M | 10523 | 8597 | 81.7 | 0 of 1 | 4 |
| NF_D_WD_half_3_L | JN05W2 | L1M | 2425 | 1520 | 62.7 | 0 of 2 | 4 |
| NF_D_OB_best_m2_J | JN05W2J | L3M | 189873 | 186333 | 98.1 | 0 of 8 | 13 |
| NF_D_OB_best_m2_L | JN05W2 | L3M | 209474 | 194782 | 93.0 | 0 of 9 | 13 |
| NF_D_PL_day_half_m1p5_J | JN05W2J | L3M | 189873 | 172743 | 91.0 | 0 of 8 | 13 |
| NF_D_PL_day_half_m1p5_L | JN05W2 | L3M | 209474 | 214945 | 102.6 | 0 of 9 | 13 |
| NF_D_PL_day_half_m2_J | JN05W2J | L3M | 189873 | 170334 | 89.7 | 0 of 8 | 13 |
| NF_D_PL_day_half_m2_L | JN05W2 | L3M | 209474 | 217139 | 103.7 | 0 of 9 | 13 |
| NF_D_ST_half_2_J | JN05W2J | L3M | 189873 | 185386 | 97.6 | 0 of 8 | 13 |
| NF_D_ST_half_2_L | JN05W2 | L3M | 209474 | 191925 | 91.6 | 0 of 9 | 13 |
| NF_D_ST_half_3_J | JN05W2J | L3M | 189873 | 185862 | 97.9 | 0 of 8 | 13 |
| NF_D_ST_half_3_L | JN05W2 | L3M | 209474 | 204758 | 97.7 | 0 of 9 | 13 |
| NF_D_ST_half_4_J | JN05W2J | L3M | 189873 | 187574 | 98.8 | 0 of 8 | 13 |
| NF_D_ST_half_4_L | JN05W2 | L3M | 209474 | 208947 | 99.7 | 0 of 9 | 13 |
| NF_D_WD_fresh_3_J | JN05W2J | L3M | 189873 | 131320 | 69.2 | 0 of 8 | 13 |
| NF_D_WD_fresh_3_L | JN05W2 | L3M | 209474 | 155829 | 74.4 | 1 of 9 | 13 |
| NF_D_WD_half_3_J | JN05W2J | L3M | 189873 | 166037 | 87.4 | 0 of 8 | 13 |
| NF_D_WD_half_3_L | JN05W2 | L3M | 209474 | 179913 | 85.9 | 0 of 9 | 13 |
| NF_D_OB_best_m2_J | JN05W2J | L6M | 250435 | 244825 | 97.8 | 2 of 20 | 26 |
| NF_D_OB_best_m2_L | JN05W2 | L6M | 337218 | 308062 | 91.4 | 2 of 19 | 26 |
| NF_D_PL_day_half_m1p5_J | JN05W2J | L6M | 250435 | 249277 | 99.5 | 0 of 20 | 26 |
| NF_D_PL_day_half_m1p5_L | JN05W2 | L6M | 337218 | 311062 | 92.2 | 1 of 19 | 26 |
| NF_D_PL_day_half_m2_J | JN05W2J | L6M | 250435 | 248462 | 99.2 | 0 of 20 | 26 |
| NF_D_PL_day_half_m2_L | JN05W2 | L6M | 337218 | 311114 | 92.3 | 0 of 19 | 26 |
| NF_D_ST_half_2_J | JN05W2J | L6M | 250435 | 225373 | 90.0 | 1 of 20 | 26 |
| NF_D_ST_half_2_L | JN05W2 | L6M | 337218 | 286968 | 85.1 | 0 of 19 | 26 |
| NF_D_ST_half_3_J | JN05W2J | L6M | 250435 | 250390 | 100.0 | 0 of 20 | 26 |
| NF_D_ST_half_3_L | JN05W2 | L6M | 337218 | 331171 | 98.2 | 0 of 19 | 26 |
| NF_D_ST_half_4_J | JN05W2J | L6M | 250435 | 249793 | 99.7 | 0 of 20 | 26 |
| NF_D_ST_half_4_L | JN05W2 | L6M | 337218 | 337958 | 100.2 | 0 of 19 | 26 |
| NF_D_WD_fresh_3_J | JN05W2J | L6M | 250435 | 126707 | 50.6 | 1 of 20 | 26 |
| NF_D_WD_fresh_3_L | JN05W2 | L6M | 337218 | 219071 | 65.0 | 1 of 19 | 26 |
| NF_D_WD_half_3_J | JN05W2J | L6M | 250435 | 227345 | 90.8 | 0 of 20 | 26 |
| NF_D_WD_half_3_L | JN05W2 | L6M | 337218 | 313459 | 93.0 | 0 of 19 | 26 |

## 1. Windows (maxDD cut %, equal-mean cut %, d mean $/wk all weeks, carry week NOT dropped)

| cell | window | DD cut % | eq-mean cut % | d mean/wk | mean/wk | base mean/wk | months |
|--|--|--|--|--|--|--|--|
| NF_D_OB_best_m2_J | L1M | 15.1 | 5.0 | 2483 | 5114 | 2631 | 7 |
| NF_D_OB_best_m2_J | L3M | -74.3 | -95.1 | -1189 | 13752 | 14942 | 7 |
| NF_D_OB_best_m2_J | L6M | -29.9 | -45.4 | -3076 | 17789 | 20865 | 7 |
| NF_D_OB_best_m2_L | HOLD | -52.3 | -80.1 | -5116 | 12373 | 17489 | 16 |
| NF_D_OB_best_m2_L | L1M | 51.7 | 42.9 | 6211 | 6818 | 606 | 16 |
| NF_D_OB_best_m2_L | L3M | -59.4 | -88.5 | -2485 | 13531 | 16015 | 16 |
| NF_D_OB_best_m2_L | L6M | -59.4 | -88.5 | -5847 | 19290 | 25137 | 16 |
| NF_D_PL_day_half_m1p5_J | HOLD | 19.7 | 13.2 | -949 | 13456 | 14405 | 16 |
| NF_D_PL_day_half_m1p5_J | L1M | 13.0 | 6.1 | -4308 | -1677 | 2631 | 16 |
| NF_D_PL_day_half_m1p5_J | L3M | 10.1 | 2.9 | -2036 | 12905 | 14942 | 16 |
| NF_D_PL_day_half_m1p5_J | L6M | 0.3 | -7.7 | -2217 | 18648 | 20865 | 16 |
| NF_D_PL_day_half_m1p5_L | HOLD | 33.9 | 29.8 | -2062 | 15427 | 17489 | 16 |
| NF_D_PL_day_half_m1p5_L | L1M | 33.6 | 29.4 | 723 | 1329 | 606 | 16 |
| NF_D_PL_day_half_m1p5_L | L3M | 4.3 | -1.7 | 14 | 16030 | 16015 | 16 |
| NF_D_PL_day_half_m1p5_L | L6M | 4.3 | -1.7 | -2652 | 22485 | 25137 | 16 |
| NF_D_PL_day_half_m2_J | HOLD | 15.1 | 8.6 | -914 | 13491 | 14405 | 16 |
| NF_D_PL_day_half_m2_J | L1M | 20.0 | 13.9 | -3718 | -1087 | 2631 | 16 |
| NF_D_PL_day_half_m2_J | L3M | 20.0 | 13.9 | -1805 | 13136 | 14942 | 16 |
| NF_D_PL_day_half_m2_J | L6M | -1.2 | -8.9 | -2164 | 18701 | 20865 | 16 |
| NF_D_PL_day_half_m2_L | HOLD | 26.8 | 24.6 | -1422 | 16067 | 17489 | 16 |
| NF_D_PL_day_half_m2_L | L1M | 36.9 | 35.0 | 2219 | 2825 | 606 | 16 |
| NF_D_PL_day_half_m2_L | L3M | 4.3 | 1.3 | 106 | 16121 | 16015 | 16 |
| NF_D_PL_day_half_m2_L | L6M | 4.3 | 1.3 | -1542 | 23595 | 25137 | 16 |
| NF_D_ST_half_2_J | HOLD | 7.1 | 0.5 | -1319 | 13086 | 14405 | 16 |
| NF_D_ST_half_2_J | L1M | 12.5 | 6.3 | 58 | 2689 | 2631 | 16 |
| NF_D_ST_half_2_J | L3M | -5.7 | -13.2 | -697 | 14244 | 14942 | 16 |
| NF_D_ST_half_2_J | L6M | 2.5 | -4.5 | -2733 | 18132 | 20865 | 16 |
| NF_D_ST_half_2_L | HOLD | 18.1 | 6.9 | -1798 | 15691 | 17489 | 16 |
| NF_D_ST_half_2_L | L1M | 29.8 | 20.2 | 1028 | 1635 | 606 | 16 |
| NF_D_ST_half_2_L | L3M | -2.2 | -16.2 | -1561 | 14454 | 16015 | 16 |
| NF_D_ST_half_2_L | L6M | -2.2 | -16.2 | -3688 | 21449 | 25137 | 16 |
| NF_D_ST_half_3_J | HOLD | -19.8 | -26.4 | -947 | 13459 | 14405 | 16 |
| NF_D_ST_half_3_J | L1M | 3.5 | -1.8 | -356 | 2275 | 2631 | 16 |
| NF_D_ST_half_3_J | L3M | -50.8 | -59.2 | -1380 | 13562 | 14942 | 16 |
| NF_D_ST_half_3_J | L6M | -12.4 | -18.6 | -1430 | 19435 | 20865 | 16 |
| NF_D_ST_half_3_L | L1M | 8.7 | 4.4 | -373 | 234 | 606 | 6 |
| NF_D_ST_half_3_L | L3M | -37.0 | -43.3 | -1847 | 14168 | 16015 | 6 |
| NF_D_ST_half_3_L | L6M | -37.0 | -43.3 | -1582 | 23555 | 25137 | 6 |
| NF_D_ST_half_4_J | HOLD | -25.5 | -28.4 | -682 | 13723 | 14405 | 12 |
| NF_D_ST_half_4_J | L1M | 3.5 | 1.3 | -116 | 2514 | 2631 | 12 |
| NF_D_ST_half_4_J | L3M | -15.2 | -17.8 | -827 | 14114 | 14942 | 12 |
| NF_D_ST_half_4_J | L6M | 0.0 | -2.3 | -759 | 20106 | 20865 | 12 |
| NF_D_ST_half_4_L | L1M | 0.0 | -1.6 | 245 | 851 | 606 | 6 |
| NF_D_ST_half_4_L | L3M | -5.1 | -6.8 | -760 | 15255 | 16015 | 6 |
| NF_D_ST_half_4_L | L6M | -5.1 | -6.8 | -698 | 24439 | 25137 | 6 |
| NF_D_WD_fresh_3_J | HOLD | 8.2 | -33.1 | -5244 | 9161 | 14405 | 16 |
| NF_D_WD_fresh_3_J | L1M | 6.3 | -35.9 | -2871 | -241 | 2631 | 16 |
| NF_D_WD_fresh_3_J | L3M | 6.3 | -35.9 | -2048 | 12893 | 14942 | 16 |
| NF_D_WD_fresh_3_J | L6M | 30.2 | -1.3 | -7371 | 13494 | 20865 | 16 |
| NF_D_WD_fresh_3_L | HOLD | 5.2 | -64.7 | -7215 | 10274 | 17489 | 16 |
| NF_D_WD_fresh_3_L | L1M | 33.3 | -15.9 | -2342 | -1735 | 606 | 16 |
| NF_D_WD_fresh_3_L | L3M | 33.3 | -15.9 | -3648 | 12367 | 16015 | 16 |
| NF_D_WD_fresh_3_L | L6M | 33.3 | -15.9 | -11252 | 13885 | 25137 | 16 |
| NF_D_WD_half_3_J | L1M | 17.0 | 11.3 | -481 | 2149 | 2631 | 6 |
| NF_D_WD_half_3_J | L3M | 17.0 | 11.3 | -1602 | 13339 | 14942 | 6 |
| NF_D_WD_half_3_J | L6M | 12.5 | 6.5 | -1723 | 19142 | 20865 | 6 |
| NF_D_WD_half_3_L | HOLD | 11.6 | 8.0 | -565 | 16924 | 17489 | 16 |
| NF_D_WD_half_3_L | L1M | 23.2 | 20.1 | -226 | 380 | 606 | 16 |
| NF_D_WD_half_3_L | L3M | 12.8 | 9.3 | -2596 | 13419 | 16015 | 16 |
| NF_D_WD_half_3_L | L6M | 12.8 | 9.3 | -1544 | 23593 | 25137 | 16 |

## 3. acceptance_p7 and behavioural scorecard (cells with all 43 months)


## 4. First-order screen (LPB_BASE trade list, history unmodified: OVERSTATES; used only to pick exact cells; 52 cells = family size for any selection)

| cell               |   L6M DD cut |   L6M d mean/wk |   L6M 5best kept |   L6M w->l |   HOLD DD cut |   HOLD d mean/wk |   PRE DD cut |   GAP DD cut |   X' DD cut |   signals changed |
|:-------------------|-------------:|----------------:|-----------------:|-----------:|--------------:|-----------------:|-------------:|-------------:|------------:|------------------:|
| ST_skip_2          |        42.32 |        -5412.33 |             0.84 |          4 |         37.15 |         -3254.08 |        17.41 |         8.43 |      -32.01 |              9487 |
| OB_best_-2         |        38.61 |         -954.79 |             0.99 |          4 |         12.36 |         -3057.91 |        27.88 |       -10    |        8.1  |              4941 |
| C22                |        34.49 |         2942.8  |             1.04 |          2 |         16.26 |          1489.3  |        16.33 |         0    |        0    |              1275 |
| OB_best_-3         |        33.24 |        -1130.26 |             1    |          5 |          6.47 |         -2360.62 |         2.13 |       -11.93 |        1.2  |              4452 |
| LS_skip_3of4       |        30.04 |        -4531.67 |             0.91 |          6 |         26.5  |         -1297.76 |        31.48 |         7.19 |       11.36 |              6828 |
| PL_day_skip_-1.5   |        26.91 |        -2183.76 |             0.9  |          5 |         26.43 |         -6012.9  |        24.58 |       -17.55 |        3.94 |              6320 |
| RA_session_skip_-2 |        26.39 |        -2723.69 |             0.92 |          4 |         17.78 |         -6353.22 |        21.3  |         8.18 |       -3.8  |              7278 |
| ST_skip_3          |        24.62 |        -2507.34 |             0.91 |          3 |         22.91 |          -794.7  |        32.04 |        -8.18 |       -5.5  |              6009 |
| ST_half_2          |        23.5  |        -2706.16 |             0.92 |          1 |         27.9  |         -1627.04 |        27.29 |        11.35 |       -1.68 |              9487 |
| WD_best_3          |        22.9  |        -3606.08 |             0.62 |          1 |         29.97 |         -1928.83 |        29.4  |        -7.71 |       -3.64 |              5792 |
| PL_day_skip_-2     |        22.1  |        -1420.12 |             0.94 |          4 |         17.06 |         -6155.47 |        23.3  |       -23.76 |        4.03 |              6041 |
| WD_half_3          |        21.24 |        -2489.86 |             0.7  |          0 |         17.38 |          -651.5  |        17.53 |         2.1  |        5.35 |              7272 |
| WD_fresh_3         |        16.83 |         -331.02 |             0.65 |          2 |         23.82 |          -926.92 |        29.18 |         2.4  |       -8.48 |              4347 |
| LS_half_3of4       |        16.51 |        -2265.84 |             0.96 |          3 |         23.15 |          -648.88 |        22.27 |        13.24 |       13.4  |              6828 |
| WD_fresh_5         |        16.01 |        -2810.03 |             0.69 |          1 |         19.43 |          2067.37 |        17.99 |        -1.71 |      -12.49 |              3576 |
| RA_winner_skip_-2  |        15.76 |        -2069.49 |             0.87 |          4 |         11.19 |         -7771.12 |        12.58 |        -7.07 |       29.08 |              6787 |
| PL_day_skip_-3     |        15.07 |        -1495.34 |             0.96 |          4 |         19.62 |         -4787.99 |        -8.61 |       -17.01 |      -10.59 |              5434 |
| DD_half_2          |        14.71 |        -3101.33 |             0.93 |          4 |         26.26 |         -4224.64 |        34.36 |        11.32 |       10.12 |             10699 |
| PLlots_half_-2     |        14.63 |        -1898.56 |             0.97 |          2 |         15.31 |          -313.3  |        -3.96 |        11.71 |        7.09 |              4750 |
| ST_half_3          |        13.69 |        -1253.67 |             0.96 |          0 |         14.27 |          -397.35 |        29.02 |         4.27 |       -0.31 |              6009 |
| WD_half_5          |        13.61 |        -3608.1  |             0.73 |          0 |         14.38 |           905.6  |        14.19 |         1.66 |       -0.2  |              5966 |
| PL_day_half_-1.5   |        13.46 |        -1091.88 |             0.95 |          1 |         19.49 |         -3006.45 |        14.52 |        14.61 |        6.17 |              6320 |
| RA_session_half_-2 |        13.2  |        -1361.84 |             0.96 |          2 |         22.64 |         -3176.61 |        22.78 |        17.31 |        8.92 |              7278 |
| ST_skip_4          |        13    |          453.8  |             0.93 |          2 |         11.57 |          -724.74 |        29.86 |         3.92 |      -15.09 |              3712 |
| PL_day_half_-2     |        11.06 |         -710.06 |             0.97 |          1 |         17.79 |         -3077.74 |        13.88 |        14    |        6.84 |              6041 |
| WD_best_5          |        10.58 |        -5133.72 |             0.67 |          1 |         23.96 |          -142.72 |        22.39 |        -7.03 |       -5.53 |              4777 |
| DD_skip_2          |         9.56 |        -6202.66 |             0.85 |          6 |         16.83 |         -8449.29 |        37.54 |       -16.62 |        1.74 |             10699 |
| DD_half_3          |         8.7  |        -2842.56 |             0.95 |          4 |         21.07 |         -4115.9  |        28.92 |        11.32 |       11.27 |              9636 |
| RA_winner_half_-2  |         7.89 |        -1034.74 |             0.94 |          2 |          7.04 |         -3885.56 |         9.17 |        14.01 |       15.72 |              6787 |
| PL_day_half_-3     |         7.54 |         -747.67 |             0.98 |          1 |         15.66 |         -2393.99 |         3.27 |        10.83 |        4.8  |              5434 |
| ST_half_4          |         6.94 |          226.9  |             0.97 |          0 |          5.79 |          -362.37 |        16.62 |        10.31 |       -5.69 |              3712 |
| SW_half_120        |         6.1  |        -1910.38 |             0.97 |          3 |          8.75 |          -448.9  |         3.2  |        12.19 |        9.54 |              2356 |
| SW_half_60         |         5.19 |        -2855.81 |             0.94 |          5 |         19.25 |         -1091.41 |        10.51 |        18.32 |        9.18 |              3687 |
| DD_half_4          |         3.71 |        -4671.35 |             0.94 |          4 |          6.88 |         -4850.63 |        31.74 |        14.92 |       15.04 |              8512 |
| PL_sess_skip_-3    |         2.26 |         -977.58 |             0.9  |          3 |         11.65 |         -4234.92 |        18.57 |        22.15 |        0.23 |              3285 |
| PL_sess_half_-3    |         1.14 |         -488.79 |             0.95 |          1 |         10.81 |         -2117.46 |        11.92 |        11.41 |        4.84 |              3285 |
| LS_half_4of5       |         0.19 |        -3157.71 |             0.95 |          4 |         18.96 |          -480.32 |        15.4  |        11.32 |       11.71 |              4880 |
| LS_skip_4of5       |        -1.27 |        -6315.42 |             0.9  |          6 |         20.64 |          -960.65 |        29.92 |        11.77 |       16.18 |              4880 |
| PLusd_half_-9000   |        -2.29 |         -912.95 |             0.99 |          1 |         10.35 |          -713.45 |         3.27 |        -6.68 |       -0.24 |              2830 |
| PL_sess_half_-2    |        -2.7  |        -1805.1  |             0.92 |          2 |         12.36 |         -2181.3  |        12.97 |        13.28 |        2.79 |              4050 |
| PL_sess_half_-1.5  |        -4.31 |        -2364.38 |             0.9  |          3 |         12.02 |         -2465.08 |        16.16 |        12.49 |        3.7  |              4448 |
| ST_half_2_sess     |        -5.31 |        -2746.32 |             0.92 |          1 |          9.55 |         -1200.94 |        14.99 |        14.08 |       -6.32 |              3156 |
| PL_sess_skip_-2    |        -5.41 |        -3610.2  |             0.84 |          3 |         19.04 |         -4362.6  |        25.94 |        26.56 |      -13.67 |              4050 |
| LS_half_6of8       |        -5.56 |        -1461.3  |             0.94 |          1 |          7.79 |         -1555.45 |         9.68 |        -0.79 |       -3.98 |              3514 |
| ST_half_3_sess     |        -7.7  |        -1943.89 |             0.99 |          1 |         -2.17 |         -1171.36 |        13.61 |         7.49 |       -3.65 |              1077 |
| ST_half_4_sess     |        -8.2  |        -1012.59 |             1    |          0 |          1.06 |          -136.65 |         6.89 |         3.84 |        0.34 |               373 |
| PL_sess_skip_-1.5  |        -8.63 |        -4728.77 |             0.81 |          3 |         22.08 |         -4930.16 |        32.33 |        24.98 |      -15.78 |              4448 |
| LS_skip_6of8       |       -11.12 |        -2922.59 |             0.89 |          4 |          6.67 |         -3110.9  |        18.89 |        -1.58 |       -7.96 |              3514 |
| DD_skip_3          |       -14.81 |        -5685.13 |             0.91 |          6 |         18.31 |         -8231.8  |        27.09 |       -15.88 |        0.18 |              9636 |
| DD_skip_4          |       -75.64 |        -9342.71 |             0.88 |          5 |        -25.36 |         -9701.25 |        33.56 |       -18.98 |        9.14 |              8512 |

## 5. R at the cell's own lots vs fixed dollars (transfer to x1.75 lots)
L6M closes of JN05W2 (live panel lots 7/4/4 table etc.): mean lots per trade 1.86, by book {'A7': 1.0, 'H7': 1.86, 'K7': 1.14, 'M7': 1.19, 'O7': 1.0, 'P7': 3.5, 'U7': 2.73}. R fixed = $1,200 (60 pts x $20 x 1 lot); R at the cell's own lots ('lots' mode) = $1,200 x mean lots of the last 20 closes = about $2228 at these lots. Rules written in R-at-own-lots scale with lots automatically: at the user's x1.75 lots the same R-multiple trigger is $3899. Rules written in fixed dollars (pnlusd) do NOT scale: at x1.75 lots they must be multiplied by 1.75. Count rules (stops, losers k of m, since-winner minutes, n closes) are lot-free and transfer unchanged. The fixed-R rules (R = 1,200, e.g. C22 -2R = -$2,400) are really a dollar line: at x1.75 lots, -$2,400 trips after about 0.57 x the loss in trade-size terms, so a fixed-R line becomes tighter by 1.75 in R-at-own-lots terms; re-express it as -2R(own lots) = -$4456 to keep the same behaviour.

