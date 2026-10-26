# REPORT STRUCT48 T3.6 (second-system ideas, extension) - IN PROGRESS
Proposed ideas (20, status 'proposed', with mechanism/data/grid/rationale/score): l2vast/struct48/rows/T3_6_proposed.json. Batch 1 = top 5 by score (I01 turn-of-month, I02 Asia drift, I03 intraday momentum, I04 RSI2 reversal, I05 pre-FOMC); prereg prereg/T3_6.md sha256 f3273a7aa8be0ea2ff65cbdbbe07dceead06d417167a934d944af8b0009748af.

## BATCH 1 PRE-HOLDOUT TEXT (written before the holdout stage; WF-PRE 2024-02..2025-06 scoring only)
Look-ahead audit: 360 cuts, 0 mismatches across all 30 variants. Conditions in WF-PRE (the 'p4 standalone holdout' condition is unscored at this stage and shows as failed; 'pass of 9' counts p1-p6, x2, yr, neighbours-agree).
Reading: no primary variant meets p1 (portfolio maxDD down >=10%) together with p2 (mean not down) at any ratio; ASIAL_E1140 comes closest at ratio 0.25 (dMDD -8.4%) but placebo 0.90 (always-long vs random-direction), CI includes 0, year share 0.99; RSI2_t10 has standalone placebo rank 0.97 but portfolio placebo 0.88, CI includes 0, maxDD not down; the momentum, TOM and Asia-continuation variants have negative unit means. FOMC cells have 9-11 trades in WF-PRE (CI cannot exclude 0). Per-protocol the holdout is now scored once for all 10 primaries.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IMOC_E930 | 4.65 | -348 | 0.17 | 0.16 | Y | 0.25 | -3070 | 21.6 | [-8566,2039] | 0.17 | -3679 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMOC_E930 | 4.65 | -348 | 0.17 | 0.16 | Y | 0.5 | -6139 | 56.0 | [-17131,4077] | 0.17 | -7357 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMOC_E930 | 4.65 | -348 | 0.17 | 0.16 | Y | 1.0 | -12278 | 138.7 | [-34263,8154] | 0.17 | -14715 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.65 | -30 | -0.09 | 0.52 | Y | 0.25 | -281 | 13.7 | [-5630,4968] | 0.52 | -939 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.65 | -30 | -0.09 | 0.52 | Y | 0.5 | -563 | 43.2 | [-11259,9935] | 0.52 | -1879 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.65 | -30 | -0.09 | 0.52 | Y | 1.0 | -1125 | 113.7 | [-22519,19871] | 0.52 | -3758 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n4 | 0.20 | -250 | 0.04 | 0.22 | Y | 0.25 | -1648 | 26.5 | [-7284,3449] | 0.18 | -1668 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n4 | 0.20 | -250 | 0.04 | 0.22 | Y | 0.5 | -3297 | 83.2 | [-14567,6898] | 0.18 | -3336 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n4 | 0.20 | -250 | 0.04 | 0.22 | Y | 1.0 | -6594 | 196.5 | [-29134,13795] | 0.18 | -6672 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n2 | 0.21 | -356 | -0.03 | 0.14 | Y | 0.25 | -3644 | 13.9 | [-9671,1619] | 0.05 | -3676 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n2 | 0.21 | -356 | -0.03 | 0.14 | Y | 0.5 | -7288 | 47.0 | [-19341,3238] | 0.05 | -7353 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n2 | 0.21 | -356 | -0.03 | 0.14 | Y | 1.0 | -14576 | 166.7 | [-38683,6476] | 0.05 | -14706 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| FOMC_P1_x1400 | 0.12 | 195 | 0.27 | 0.81 | Y | 0.25 | 3079 | 13.2 | [-1677,9216] | 0.80 | 3050 | 1.17 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P1_x1400 | 0.12 | 195 | 0.27 | 0.81 | Y | 0.5 | 6157 | 26.4 | [-3353,18431] | 0.80 | 6101 | 1.17 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P1_x1400 | 0.12 | 195 | 0.27 | 0.81 | Y | 1.0 | 12314 | 52.8 | [-6706,36862] | 0.80 | 12202 | 1.17 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P2_e0930 | 0.15 | 24 | 0.17 | 0.53 | N | 0.25 | 910 | 14.9 | [-4375,6745] | 0.60 | 828 | 2.84 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| FOMC_P2_e0930 | 0.15 | 24 | 0.17 | 0.53 | N | 0.5 | 1820 | 29.8 | [-8749,13491] | 0.60 | 1656 | 2.84 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| FOMC_P2_e0930 | 0.15 | 24 | 0.17 | 0.53 | N | 1.0 | 3639 | 59.5 | [-17498,26981] | 0.60 | 3312 | 2.84 | 3 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| ASIAL_E1140 | 4.79 | 382 | 0.25 | 0.87 | Y | 0.25 | 3127 | -8.4 | [-2218,8634] | 0.90 | 2545 | 0.99 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAL_E1140 | 4.79 | 382 | 0.25 | 0.87 | Y | 0.5 | 6253 | -6.8 | [-4436,17267] | 0.90 | 5091 | 0.99 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAL_E1140 | 4.79 | 382 | 0.25 | 0.87 | Y | 1.0 | 12506 | 47.1 | [-8872,34535] | 0.90 | 10181 | 0.99 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAPD_E1140 | 4.76 | -313 | -0.02 | 0.28 | Y | 0.25 | -2109 | 7.4 | [-6665,4094] | 0.29 | -2585 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ASIAPD_E1140 | 4.76 | -313 | -0.02 | 0.28 | Y | 0.5 | -4218 | 61.8 | [-13330,8189] | 0.29 | -5169 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ASIAPD_E1140 | 4.76 | -313 | -0.02 | 0.28 | Y | 1.0 | -8435 | 174.3 | [-26659,16378] | 0.29 | -10339 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| RSI2_t10 | 0.47 | 921 | 0.04 | 0.97 | Y | 0.25 | 4075 | 2.3 | [-1037,9750] | 0.88 | 4044 | 0.6 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RSI2_t10 | 0.47 | 921 | 0.04 | 0.97 | Y | 0.5 | 8149 | 4.7 | [-2073,19500] | 0.88 | 8088 | 0.6 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RSI2_t10 | 0.47 | 921 | 0.04 | 0.97 | Y | 1.0 | 16298 | 45.8 | [-4146,38999] | 0.88 | 16176 | 0.6 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| RSI2T_t10 | 0.33 | 500 | 0.03 | 0.87 | N | 0.25 | 4597 | 4.8 | [-617,9663] | 0.91 | 4552 | 0.51 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |
| RSI2T_t10 | 0.33 | 500 | 0.03 | 0.87 | N | 0.5 | 9195 | 9.7 | [-1233,19327] | 0.91 | 9104 | 0.51 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |
| RSI2T_t10 | 0.33 | 500 | 0.03 | 0.87 | N | 1.0 | 18389 | 30.7 | [-2466,38653] | 0.91 | 18207 | 0.51 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |

## BATCH 1 FINAL (WF 2024-02+, holdout 2025-07+ scored once; holdout look logged in ledger/holdout_looks.jsonl track T3.6b1)
Result: 0/10 primary variants PASS (rows/T3_6_b1_final.json; 30 variants counted as trials; weekly unit series out/T3_6/).
Near-miss and only lead: RSI2_t10 (RSI(2)<10 at 15:55, long NQ, hold 1 trading day; unit = 1 lot): trades 0.49/wk, WF unit +$1,005/wk, holdout +$1,084/wk, weekly corr to Set A -0.05, standalone placebo 0.99, portfolio placebo 0.978, CI of portfolio-minus-Set-A mean excludes 0 at all ratios (ratio 0.25: +$5,099/wk, CI [980, 10,121]), 2x-cost sign +, year share <= 0.6, neighbours agree (thr 5, 15), 2013-2023 outside-sample unit +$598/wk, 8 of 11 years positive. Fails ONLY p1: portfolio maxDD is +2.7% (0.25), +5.3% (0.5), +64% (1.0) vs Set A, i.e. not down >= 10%; also DSR 0.10 (reported, not part of PASS; ~28,300 cumulative trials). RSI2T_t10 (SMA200 filter): same pattern, fails only p1 (maxDD +3.8%/+7.6%/+17.2%), placebo 0.956. Interpretation: a genuine, uncorrelated mean-adder (about +4-5% of Set A's mean at ratio 0.25) but a long-only dip-buy cannot cut Set A's maxDD; treat as a LEAD (needs its own confirmation prereg if the owner wants a mean-adding sleeve; second-system PASS as defined requires maxDD down >=10%).
Everything else fails: IMOC and IMF30 intraday momentum negative (unit -471 and -200/wk WF; holdout negative); TOM +344/wk (n4) / -10 (n2) with 15-16 trades in the window, neighbours disagree, CI includes 0; pre-FOMC P1 +90/wk, holdout -27; ASIAL +155/wk WF, holdout -98, placebo 0.71 (2013-2023 +49k total, 7/11 yrs); ASIAPD negative.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IMOC_E930 | 4.74 | -471 | 0.14 | 0.04 | Y | 0.25 | -4747 | 25.5 | [-8975,-376] | 0.04 | -5455 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| IMOC_E930 | 4.74 | -471 | 0.14 | 0.04 | Y | 0.5 | -9493 | 66.2 | [-17950,-752] | 0.04 | -10911 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| IMOC_E930 | 4.74 | -471 | 0.14 | 0.04 | Y | 1.0 | -18986 | 247.5 | [-35899,-1504] | 0.04 | -21821 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.74 | -200 | 0.11 | 0.31 | Y | 0.25 | -1910 | 13.7 | [-5831,2833] | 0.33 | -2580 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.74 | -200 | 0.11 | 0.31 | Y | 0.5 | -3819 | 43.2 | [-11662,5666] | 0.33 | -5160 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| IMF30_E930 | 4.74 | -200 | 0.11 | 0.31 | Y | 1.0 | -7639 | 113.7 | [-23323,11331] | 0.33 | -10320 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n4 | 0.20 | 344 | -0.03 | 0.59 | N | 0.25 | 1822 | 15.3 | [-2251,5754] | 0.60 | 1806 | 1.55 | 4 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| TOM_a-1_n4 | 0.20 | 344 | -0.03 | 0.59 | N | 0.5 | 3644 | 60.8 | [-4502,11509] | 0.60 | 3612 | 1.55 | 4 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| TOM_a-1_n4 | 0.20 | 344 | -0.03 | 0.59 | N | 1.0 | 7288 | 151.8 | [-9004,23018] | 0.60 | 7224 | 1.55 | 4 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok,neighbours_agree |
| TOM_a-1_n2 | 0.22 | -10 | 0.01 | 0.34 | Y | 0.25 | -75 | 8.7 | [-4521,4688] | 0.34 | -100 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n2 | 0.22 | -10 | 0.01 | 0.34 | Y | 0.5 | -151 | 29.3 | [-9043,9377] | 0.34 | -201 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| TOM_a-1_n2 | 0.22 | -10 | 0.01 | 0.34 | Y | 1.0 | -301 | 102.1 | [-18086,18753] | 0.34 | -402 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| FOMC_P1_x1400 | 0.11 | 90 | 0.15 | 0.64 | Y | 0.25 | 1873 | 17.4 | [-2051,6194] | 0.69 | 1838 | 1.34 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P1_x1400 | 0.11 | 90 | 0.15 | 0.64 | Y | 0.5 | 3746 | 34.8 | [-4101,12388] | 0.69 | 3676 | 1.34 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P1_x1400 | 0.11 | 90 | 0.15 | 0.64 | Y | 1.0 | 7492 | 69.7 | [-8202,24775] | 0.69 | 7353 | 1.34 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| FOMC_P2_e0930 | 0.15 | -30 | 0.08 | 0.36 | Y | 0.25 | -1222 | 16.1 | [-5819,2770] | 0.27 | -1311 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| FOMC_P2_e0930 | 0.15 | -30 | 0.08 | 0.36 | Y | 0.5 | -2444 | 32.2 | [-11638,5540] | 0.27 | -2623 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| FOMC_P2_e0930 | 0.15 | -30 | 0.08 | 0.36 | Y | 1.0 | -4889 | 116.1 | [-23275,11080] | 0.27 | -5246 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ASIAL_E1140 | 4.87 | 155 | 0.01 | 0.68 | Y | 0.25 | 1114 | -7.4 | [-3017,5261] | 0.71 | 594 | 1.29 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAL_E1140 | 4.87 | 155 | 0.01 | 0.68 | Y | 0.5 | 2228 | -2.7 | [-6034,10523] | 0.71 | 1188 | 1.29 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAL_E1140 | 4.87 | 155 | 0.01 | 0.68 | Y | 1.0 | 4456 | 59.2 | [-12068,21046] | 0.71 | 2375 | 1.29 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ASIAPD_E1140 | 4.86 | -324 | 0.04 | 0.25 | Y | 0.25 | -1804 | 1.9 | [-6191,2695] | 0.27 | -2205 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ASIAPD_E1140 | 4.86 | -324 | 0.04 | 0.25 | Y | 0.5 | -3607 | 42.4 | [-12381,5389] | 0.27 | -4411 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ASIAPD_E1140 | 4.86 | -324 | 0.04 | 0.25 | Y | 1.0 | -7215 | 135.4 | [-24762,10778] | 0.27 | -8822 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| RSI2_t10 | 0.49 | 1005 | -0.05 | 0.99 | Y | 0.25 | 5099 | 2.7 | [980,10121] | 0.98 | 5061 | 0.42 | 8 | p1_maxdd_down_10pct |
| RSI2_t10 | 0.49 | 1005 | -0.05 | 0.99 | Y | 0.5 | 10197 | 5.3 | [1961,20243] | 0.98 | 10123 | 0.42 | 8 | p1_maxdd_down_10pct |
| RSI2_t10 | 0.49 | 1005 | -0.05 | 0.99 | Y | 1.0 | 20394 | 64.3 | [3922,40486] | 0.98 | 20246 | 0.42 | 8 | p1_maxdd_down_10pct |
| RSI2T_t10 | 0.39 | 617 | -0.09 | 0.96 | Y | 0.25 | 4441 | 3.8 | [548,9523] | 0.96 | 4399 | 0.43 | 8 | p1_maxdd_down_10pct |
| RSI2T_t10 | 0.39 | 617 | -0.09 | 0.96 | Y | 0.5 | 8882 | 7.6 | [1096,19045] | 0.96 | 8798 | 0.43 | 8 | p1_maxdd_down_10pct |
| RSI2T_t10 | 0.39 | 617 | -0.09 | 0.96 | Y | 1.0 | 17765 | 17.2 | [2193,38091] | 0.96 | 17596 | 0.43 | 8 | p1_maxdd_down_10pct |

## BATCH 2 PRE-HOLDOUT TEXT (ideas I06-I10; prereg prereg/T3_6b2.md sha256 b247c9db3a5abb6e7da1045dbd1a65a1f55cb9b168abeb1369d635e019f97f0a; WF-PRE scoring only; written before the batch-2 holdout stage)
Look-ahead audit: 360 cuts (NQ, NKD and ES all replaced by noise after the cut), 0 mismatches over 30 variants. No primary variant meets p1 (maxDD down >=10%) with p2 at any ratio in WF-PRE: VIXS_t15_n2 (+$2.9k/wk @0.25, placebo 0.78), GAP_t5_x690 (placebo 0.79), SPR_w20_z15 (placebo 0.89, neighbours disagree) are the only positive-mean cells; pre-holiday, VIXS_n1, GAP_x630 and NKD-B have negative unit means. Holdout now scored once for all 10 batch-2 primaries.

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| VIXS_t15_n1 | 0.24 | -52 | 0.05 | 0.34 | Y | 0.25 | -740 | -0.2 | [-6441,4947] | 0.32 | -791 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n1 | 0.24 | -52 | 0.05 | 0.34 | Y | 0.5 | -1480 | 22.5 | [-12882,9894] | 0.32 | -1582 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n1 | 0.24 | -52 | 0.05 | 0.34 | Y | 1.0 | -2960 | 90.7 | [-25765,19788] | 0.32 | -3163 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n2 | 0.23 | 468 | -0.01 | 0.84 | Y | 0.25 | 2922 | 6.7 | [-1877,9167] | 0.78 | 2901 | 0.78 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| VIXS_t15_n2 | 0.23 | 468 | -0.01 | 0.84 | Y | 0.5 | 5845 | 13.3 | [-3754,18334] | 0.78 | 5803 | 0.78 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| VIXS_t15_n2 | 0.23 | 468 | -0.01 | 0.84 | Y | 1.0 | 11690 | 26.7 | [-7508,36667] | 0.78 | 11606 | 0.78 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| PHON_E955 | 0.05 | -68 | 0.06 | 0.20 | Y | 0.25 | -2160 | -1.8 | [-8418,2702] | 0.24 | -2186 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHON_E955 | 0.05 | -68 | 0.06 | 0.20 | Y | 0.5 | -4321 | 11.0 | [-16836,5404] | 0.24 | -4371 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHON_E955 | 0.05 | -68 | 0.06 | 0.20 | Y | 1.0 | -8641 | 73.0 | [-33672,10808] | 0.24 | -8742 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.05 | -216 | 0.01 | 0.06 | Y | 0.25 | -4028 | -1.5 | [-10324,81] | 0.06 | -4043 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.05 | -216 | 0.01 | 0.06 | Y | 0.5 | -8056 | 18.6 | [-20648,162] | 0.06 | -8085 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.05 | -216 | 0.01 | 0.06 | Y | 1.0 | -16112 | 106.7 | [-41295,323] | 0.06 | -16171 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAP_t5_x630 | 2.16 | -74 | -0.22 | 0.43 | Y | 0.25 | -515 | 3.0 | [-6610,4743] | 0.44 | -738 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAP_t5_x630 | 2.16 | -74 | -0.22 | 0.43 | Y | 0.5 | -1031 | 15.8 | [-13219,9487] | 0.44 | -1476 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAP_t5_x630 | 2.16 | -74 | -0.22 | 0.43 | Y | 1.0 | -2061 | 50.2 | [-26439,18974] | 0.44 | -2953 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAP_t5_x690 | 2.16 | 328 | -0.20 | 0.79 | Y | 0.25 | 2019 | -2.4 | [-3768,7600] | 0.79 | 1822 | 0.8 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAP_t5_x690 | 2.16 | 328 | -0.20 | 0.79 | Y | 0.5 | 4038 | 4.9 | [-7537,15200] | 0.79 | 3643 | 0.8 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAP_t5_x690 | 2.16 | 328 | -0.20 | 0.79 | Y | 1.0 | 8077 | 23.3 | [-15074,30399] | 0.79 | 7286 | 0.8 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDA_x565 | 4.51 | 108 | 0.14 | 0.62 | Y | 0.25 | 571 | 4.7 | [-4800,6129] | 0.62 | 217 | 1.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDA_x565 | 4.51 | 108 | 0.14 | 0.62 | Y | 0.5 | 1141 | 12.9 | [-9601,12258] | 0.62 | 435 | 1.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDA_x565 | 4.51 | 108 | 0.14 | 0.62 | Y | 1.0 | 2282 | 45.4 | [-19202,24515] | 0.62 | 870 | 1.9 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDB_x565 | 4.49 | -233 | 0.11 | 0.39 | Y | 0.25 | -1243 | 5.6 | [-6656,4158] | 0.39 | -1599 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| NKDB_x565 | 4.49 | -233 | 0.11 | 0.39 | Y | 0.5 | -2487 | 14.6 | [-13312,8315] | 0.39 | -3198 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| NKDB_x565 | 4.49 | -233 | 0.11 | 0.39 | Y | 1.0 | -4973 | 73.0 | [-26624,16630] | 0.39 | -6396 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| SPR_w20_z15 | 1.20 | 176 | -0.06 | 0.84 | N | 0.25 | 2586 | -1.4 | [-3232,8112] | 0.89 | 1580 | 0.59 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |
| SPR_w20_z15 | 1.20 | 176 | -0.06 | 0.84 | N | 0.5 | 5172 | 25.8 | [-6465,16224] | 0.89 | 3160 | 0.59 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |
| SPR_w20_z15 | 1.20 | 176 | -0.06 | 0.84 | N | 1.0 | 10345 | 95.3 | [-12930,32449] | 0.89 | 6320 | 0.59 | 4 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,neighbours_agree |
| SPR_w20_z20 | 0.43 | 17 | -0.13 | 0.63 | N | 0.25 | 393 | 4.0 | [-5176,5615] | 0.65 | -188 | 4.18 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| SPR_w20_z20 | 0.43 | 17 | -0.13 | 0.63 | N | 0.5 | 787 | 44.3 | [-10352,11230] | 0.65 | -376 | 4.18 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| SPR_w20_z20 | 0.43 | 17 | -0.13 | 0.63 | N | 1.0 | 1573 | 134.9 | [-20705,22460] | 0.65 | -751 | 4.18 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |

## BATCH 2 FINAL (holdout scored once, ledger/holdout_looks.jsonl track T3.6b2)
0/10 primary variants PASS (rows/T3_6_b2_final.json). Best by pass count: GAP_t5_x690 (gap fade, exit 11:30; 6 of 9 at every ratio; fails p1 maxDD (-3.3% at 0.25, +6.5% at 0.5), CI includes 0 [-2,571, 6,016], placebo 0.80), VIXS_t15_n2 (5 of 9: maxDD +8.3%, CI/placebo 0.74 fail, year share), GAP_t5_x630, NKDA_x565 (5 of 9). Pre-holiday and Nikkei-B negative; NQ/ES spread WF unit +45/wk and holdout negative, neighbours disagree. Truncation audit 0 mismatches (NQ, NKD, ES all noised).

| cell | trades/wk | unit mean/wk (window) | corr SetA | stand placebo | nb agree | ratio | port dMean | dMaxDD % | CI | port placebo | x2 | yr max | pass of 9 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| VIXS_t15_n1 | 0.18 | -19 | -0.02 | 0.33 | Y | 0.25 | -298 | 1.2 | [-4647,3486] | 0.31 | -341 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n1 | 0.18 | -19 | -0.02 | 0.33 | Y | 0.5 | -597 | 31.5 | [-9293,6972] | 0.31 | -681 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n1 | 0.18 | -19 | -0.02 | 0.33 | Y | 1.0 | -1194 | 134.0 | [-18586,13943] | 0.31 | -1362 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| VIXS_t15_n2 | 0.18 | 287 | -0.02 | 0.75 | Y | 0.25 | 2224 | 8.3 | [-1872,6976] | 0.74 | 2203 | 0.85 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| VIXS_t15_n2 | 0.18 | 287 | -0.02 | 0.75 | Y | 0.5 | 4447 | 16.5 | [-3745,13952] | 0.74 | 4407 | 0.85 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| VIXS_t15_n2 | 0.18 | 287 | -0.02 | 0.75 | Y | 1.0 | 8895 | 81.8 | [-7490,27904] | 0.74 | 8814 | 0.85 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| PHON_E955 | 0.04 | -2 | 0.04 | 0.44 | Y | 0.25 | -72 | -2.3 | [-4318,4178] | 0.44 | -98 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHON_E955 | 0.04 | -2 | 0.04 | 0.44 | Y | 0.5 | -145 | 25.8 | [-8637,8355] | 0.44 | -196 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHON_E955 | 0.04 | -2 | 0.04 | 0.44 | Y | 1.0 | -290 | 142.7 | [-17273,16711] | 0.44 | -391 | None | 3 | p1_maxdd_down_10pct,p2_mean_not_down,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.04 | -114 | -0.00 | 0.11 | Y | 0.25 | -2983 | -0.3 | [-8154,582] | 0.06 | -3000 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.04 | -114 | -0.00 | 0.11 | Y | 0.5 | -5967 | 44.0 | [-16309,1165] | 0.06 | -6000 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| PHDAY_E955 | 0.04 | -114 | -0.00 | 0.11 | Y | 1.0 | -11934 | 225.6 | [-32618,2330] | 0.06 | -11999 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| GAP_t5_x630 | 2.27 | 230 | -0.04 | 0.80 | Y | 0.25 | 1428 | 1.7 | [-2630,5938] | 0.77 | 1218 | 0.94 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAP_t5_x630 | 2.27 | 230 | -0.04 | 0.80 | Y | 0.5 | 2856 | 13.1 | [-5260,11875] | 0.77 | 2436 | 0.94 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAP_t5_x630 | 2.27 | 230 | -0.04 | 0.80 | Y | 1.0 | 5712 | 38.2 | [-10520,23750] | 0.77 | 4873 | 0.94 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| GAP_t5_x690 | 2.27 | 330 | -0.06 | 0.82 | Y | 0.25 | 1791 | -3.3 | [-2571,6016] | 0.80 | 1608 | 0.47 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| GAP_t5_x690 | 2.27 | 330 | -0.06 | 0.82 | Y | 0.5 | 3582 | 6.5 | [-5142,12032] | 0.80 | 3216 | 0.47 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| GAP_t5_x690 | 2.27 | 330 | -0.06 | 0.82 | Y | 1.0 | 7164 | 65.8 | [-10283,24063] | 0.80 | 6431 | 0.47 | 6 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95 |
| NKDA_x565 | 4.23 | 233 | 0.15 | 0.77 | Y | 0.25 | 1293 | 5.1 | [-2806,5322] | 0.78 | 945 | 0.68 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDA_x565 | 4.23 | 233 | 0.15 | 0.77 | Y | 0.5 | 2586 | 13.7 | [-5612,10643] | 0.78 | 1890 | 0.68 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDA_x565 | 4.23 | 233 | 0.15 | 0.77 | Y | 1.0 | 5172 | 66.4 | [-11224,21286] | 0.78 | 3780 | 0.68 | 5 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| NKDB_x565 | 4.31 | -484 | 0.05 | 0.17 | Y | 0.25 | -2376 | 5.2 | [-6504,1805] | 0.18 | -2690 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| NKDB_x565 | 4.31 | -484 | 0.05 | 0.17 | Y | 0.5 | -4752 | 13.2 | [-13009,3609] | 0.18 | -5381 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| NKDB_x565 | 4.31 | -484 | 0.05 | 0.17 | Y | 1.0 | -9505 | 84.6 | [-26017,7219] | 0.18 | -10761 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| SPR_w20_z15 | 1.30 | 45 | -0.18 | 0.73 | N | 0.25 | 369 | -6.9 | [-3827,4666] | 0.72 | -254 | 3.99 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| SPR_w20_z15 | 1.30 | 45 | -0.18 | 0.73 | N | 0.5 | 737 | 1.2 | [-7654,9331] | 0.72 | -508 | 3.99 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| SPR_w20_z15 | 1.30 | 45 | -0.18 | 0.73 | N | 1.0 | 1474 | 96.2 | [-15308,18663] | 0.72 | -1015 | 3.99 | 2 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok,neighbours_agree |
| SPR_w20_z20 | 0.47 | -60 | -0.19 | 0.44 | Y | 0.25 | -896 | -5.7 | [-5507,2968] | 0.44 | -1309 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| SPR_w20_z20 | 0.47 | -60 | -0.19 | 0.44 | Y | 0.5 | -1792 | 14.7 | [-11013,5935] | 0.44 | -2618 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| SPR_w20_z20 | 0.47 | -60 | -0.19 | 0.44 | Y | 1.0 | -3584 | 177.0 | [-22026,11870] | 0.44 | -5235 | None | 2 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |

## SUMMARY (T3.6)
- 20 ideas: rows/T3_6_proposed.json. Batches run: 1 (I01-I05) and 2 (I06-I10); 60 variants / 20 primary cells logged as trials (ledger T3.6b1, T3.6b2). Prereg sha256: T3_6.md f3273a7aa8be0ea2ff65cbdbbe07dceead06d417167a934d944af8b0009748af; T3_6b2.md b247c9db3a5abb6e7da1045dbd1a65a1f55cb9b168abeb1369d635e019f97f0a.
- PASS: none (0/20 primary cells). Lead: RSI2_t10 / RSI2T_t10 (fail only p1: portfolio maxDD not down >=10%; mean +$5.1k/wk @0.25, CI excludes 0, placebo 0.978/0.956, holdout positive, corr -0.05).
- Most frequently failed conditions: p1 maxDD down >=10% (all), p6 placebo >=0.95, p5 CI excludes 0, yr (small-n cells), neighbours_agree.
- Caveats: 1-min conservative fills; no stops in these clock rules; pre-FOMC/pre-holiday/TOM have 9-40 trades in window (power low); NKD/ES costs are proxies ($4.84 + 1 tick/side); remaining 10 unrun ideas (I11-I20) are listed as 'proposed'.
- Files: rows/T3_6_b{1,2}_{pre,final}.json, out/T3_6/*.npz (weekly unit series), audit/T3_6b{1,2}_trunc.json, code/t36*.py.
