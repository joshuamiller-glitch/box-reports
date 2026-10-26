# STRUCT48 T3.2 verdict

**No second-system PASS: 0 of 54 sleeve cells (0 of 162 cell x split rows) pass all 10 conditions.** Prereg sha256 5b674a0d79f2905344499d05fa45a61cb89b3a5b53160b8579f333b8c29a2ca7; pre-holdout text autopilot/REPORT_STRUCT48_T3_2_PREHOLD.md (sha256 4dbc400b..., logged in ledger/holdout_looks.jsonl before the holdout was scored). Rows: l2vast/struct48/rows/T3_2_pre.json, T3_2_final.json; sleeve series out/T3_2/<cell>.npz (weekly on Set A week axis, 1x unit).

- Directive rule (maxDD down >=10%, mean not down, corr<=0.5, standalone holdout mean>0): 0 rows. Only one row has maxDD down >=10% with mean not down (ORB_NY_30_v0 stop 75 at 0.25x: maxDD -12.3%, d mean +$167/wk), and its standalone holdout mean is -$7.4k/wk.
- Correlation with Set A <=0.5 holds in all rows (max |corr| 0.47), but adding any sleeve scaled to 0.25-1.0x Set A's SD raised portfolio maxDD in 153 of 162 rows (only 9 rows lower it at all, 1 by >=10%): the sleeves are uncorrelated yet carry their own drawdowns at the risk-split size, so there is no diversification gain in maxDD.
- Condition tallies (final window WF, 162 rows): s1 maxDD 1, s2 mean not down 66, s3 corr 162, s4 holdout mean>0 72, s5 placebo>=0.95 21, s6 CI 6, s7 2x-cost 33, s8 year share 12, s9 DSR>=0.95 0, s10 neighbours 39.
- Closest: ORB_ASIA_15_v1 (Asia 18:00 ET OR 15 min, volume>=1.5x) stops 60/75: 8/10 at every split (fails s1 maxDD and s9 DSR only); holdout standalone +$5.1k to +$7.5k/wk, placebo 0.96, but only ~0.9 trades/wk (thin) and portfolio maxDD +9% to +100%. ORB_NY_15_v0 (best WF-PRE, +$14.0k/wk standalone, placebo 1.00) fails on holdout (standalone -$5.3k/wk), IS mean -$6.8k/wk, one year 69% of gain.
- London ORB and sweep cells are negative after cost; Donchian and VWAP-trend are near zero standalone with SD $64-81k/wk.
- ORB NY with volume filter has only ~25 trades in 3.7 years (underpowered, as specified).
- Look-ahead audit: 0/360 cut mismatches in each of 18 rules; planted-leak control caught 38/360. Placebo is unlocked (see prereg); sleeves are run with their own locks and added with no netting; implied lots at 0.5x are 8-135 (flag lots_over_50_note in rows; thin cells need >50 lots).
Full per-cell tables above (Table A at 0.5x, Table B all 162 rows with failed conditions) follow.

# STRUCT48 T3.2 - FINAL (holdout scored once after pre-holdout text) 

## Table A - every sleeve cell at split 0.5x Set A SD ($/wk, report scale 14 lots; stand = sleeve at 1x unit; port d = portfolio minus Set A)

| cell | trades/wk | stand mean | stand SD | corr | d mean | d maxDD % | CI lo | placebo | 2x d mean | DSR | nb agree | pass/10 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ORB_NY_15_v0__s50@0.5 | 4.9 | 1,390 | 39,022 | 0.08 | 1,907 | 16.0 | -7,237 | 0.91 | -2,835 | 0.00 | False | 2 | s1,s4,s5,s6,s7,s8,s9,s10 |
| ORB_NY_15_v0__s60@0.5 | 4.9 | 4,882 | 45,979 | 0.08 | 5,564 | 7.0 | -3,582 | 0.98 | 1,753 | 0.01 | False | 4 | s1,s4,s6,s8,s9,s10 |
| ORB_NY_15_v0__s75@0.5 | 4.9 | 2,956 | 53,030 | 0.02 | 2,841 | 1.3 | -6,031 | 0.95 | -671 | 0.00 | True | 4 | s1,s4,s6,s7,s8,s9 |
| ORB_NY_15_v1__s50@0.5 | 0.2 | 467 | 6,650 | -0.02 | 3,378 | 22.0 | -3,949 | 0.85 | 2,674 | 0.00 | False | 4 | s1,s5,s6,s8,s9,s10 |
| ORB_NY_15_v1__s60@0.5 | 0.2 | 798 | 7,397 | -0.01 | 4,816 | 3.0 | -2,372 | 0.92 | 4,230 | 0.01 | True | 5 | s1,s5,s6,s8,s9 |
| ORB_NY_15_v1__s75@0.5 | 0.2 | 298 | 10,067 | -0.06 | 1,519 | 4.3 | -6,905 | 0.66 | 993 | 0.00 | True | 4 | s1,s4,s5,s6,s8,s9 |
| ORB_NY_30_v0__s50@0.5 | 4.9 | -1,471 | 40,387 | 0.03 | -1,911 | 20.7 | -10,762 | 0.68 | -6,079 | 0.00 | False | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v0__s60@0.5 | 4.9 | -1,775 | 45,472 | 0.05 | -2,136 | 27.9 | -10,988 | 0.60 | -6,038 | 0.00 | False | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v0__s75@0.5 | 4.9 | 324 | 51,795 | 0.09 | 334 | 2.8 | -8,589 | 0.78 | -3,448 | 0.00 | False | 2 | s1,s4,s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v1__s50@0.5 | 0.1 | -424 | 5,421 | -0.02 | -4,099 | 64.4 | -11,717 | 0.25 | -5,064 | 0.00 | False | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v1__s60@0.5 | 0.1 | 28 | 6,627 | 0.04 | 211 | 59.6 | -7,468 | 0.62 | -528 | 0.00 | False | 3 | s1,s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v1__s75@0.5 | 0.1 | 28 | 8,225 | 0.04 | 169 | 59.3 | -7,419 | 0.58 | -1,203 | 0.00 | True | 4 | s1,s5,s6,s7,s8,s9 |
| ORB_LON_15_v0__s50@0.5 | 4.9 | -4,673 | 37,104 | 0.12 | -6,454 | 93.1 | -14,615 | 0.23 | -10,952 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v0__s60@0.5 | 4.9 | -5,329 | 42,914 | 0.13 | -6,686 | 113.6 | -15,237 | 0.20 | -11,277 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v0__s75@0.5 | 4.9 | -12,835 | 55,438 | 0.18 | -12,611 | 154.6 | -21,470 | 0.02 | -15,871 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s50@0.5 | 0.7 | -990 | 14,993 | 0.09 | -3,008 | 50.8 | -10,408 | 0.27 | -4,344 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s60@0.5 | 0.7 | -1,120 | 16,655 | 0.02 | -3,398 | 21.0 | -12,123 | 0.22 | -4,732 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s75@0.5 | 0.7 | -2,425 | 21,539 | 0.00 | -5,425 | 43.8 | -13,630 | 0.07 | -6,421 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s50@0.5 | 4.9 | -4,007 | 39,835 | 0.19 | -4,936 | 94.2 | -13,106 | 0.26 | -8,946 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s60@0.5 | 4.9 | -3,782 | 48,930 | 0.17 | -3,838 | 76.5 | -11,790 | 0.36 | -7,849 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s75@0.5 | 4.9 | -4,111 | 60,338 | 0.23 | -3,484 | 101.2 | -11,750 | 0.45 | -6,259 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s50@0.5 | 0.7 | -1,255 | 14,663 | 0.13 | -4,015 | 28.5 | -11,582 | 0.20 | -5,501 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s60@0.5 | 0.7 | -1,730 | 16,991 | 0.11 | -4,856 | 56.9 | -12,777 | 0.15 | -6,166 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s75@0.5 | 0.7 | -2,723 | 21,653 | 0.08 | -5,966 | 81.8 | -13,739 | 0.10 | -6,996 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v0__s50@0.5 | 4.9 | 1,450 | 38,302 | 0.27 | 1,725 | 23.3 | -5,604 | 0.83 | -2,097 | 0.00 | True | 3 | s1,s4,s5,s6,s7,s8,s9 |
| ORB_ASIA_15_v0__s60@0.5 | 4.9 | 1,331 | 46,368 | 0.32 | 1,352 | 38.6 | -5,883 | 0.79 | -1,924 | 0.00 | True | 5 | s1,s5,s6,s7,s9 |
| ORB_ASIA_15_v0__s75@0.5 | 4.9 | 1,646 | 60,777 | 0.25 | 1,297 | 35.0 | -6,539 | 0.89 | -1,259 | 0.00 | False | 3 | s1,s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v1__s50@0.5 | 0.8 | 909 | 15,936 | 0.17 | 2,808 | 43.5 | -4,791 | 0.77 | 1,143 | 0.00 | True | 5 | s1,s5,s6,s8,s9 |
| ORB_ASIA_15_v1__s60@0.5 | 0.8 | 3,368 | 19,725 | 0.08 | 8,138 | 39.1 | 776 | 0.96 | 6,869 | 0.05 | True | 8 | s1,s9 |
| ORB_ASIA_15_v1__s75@0.5 | 0.8 | 3,958 | 23,128 | 0.06 | 7,727 | 32.3 | 463 | 0.96 | 6,691 | 0.05 | True | 8 | s1,s9 |
| ORB_ASIA_30_v0__s50@0.5 | 4.9 | 1,213 | 37,578 | 0.23 | 1,440 | 23.2 | -5,967 | 0.81 | -2,377 | 0.00 | True | 3 | s1,s4,s5,s6,s7,s8,s9 |
| ORB_ASIA_30_v0__s60@0.5 | 4.9 | 1,679 | 46,068 | 0.25 | 1,702 | 38.5 | -6,234 | 0.80 | -1,565 | 0.00 | False | 3 | s1,s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_30_v0__s75@0.5 | 4.9 | -718 | 56,136 | 0.20 | -616 | 45.1 | -8,570 | 0.71 | -3,732 | 0.00 | False | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_30_v1__s50@0.5 | 0.8 | 1,999 | 16,962 | 0.12 | 5,734 | 45.1 | -2,085 | 0.95 | 4,262 | 0.01 | True | 6 | s1,s6,s8,s9 |
| ORB_ASIA_30_v1__s60@0.5 | 0.8 | 3,354 | 20,734 | 0.08 | 8,001 | 44.4 | -232 | 0.98 | 6,791 | 0.03 | True | 7 | s1,s6,s9 |
| ORB_ASIA_30_v1__s75@0.5 | 0.8 | 3,566 | 23,871 | 0.02 | 7,195 | 47.1 | -1,030 | 0.96 | 6,159 | 0.03 | True | 6 | s1,s6,s8,s9 |
| DON_20__s50@0.5 | 24.5 | -5,973 | 82,741 | 0.47 | -3,602 | 76.5 | -11,492 | 0.36 | -13,187 | 0.00 | False | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| DON_20__s60@0.5 | 16.7 | 4,797 | 79,461 | 0.31 | 3,039 | 62.9 | -4,954 | 0.46 | -4,047 | 0.00 | False | 3 | s1,s5,s6,s7,s8,s9,s10 |
| DON_20__s75@0.5 | 13.1 | -170 | 85,449 | 0.36 | -104 | 102.9 | -8,382 | 0.67 | -4,994 | 0.00 | False | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| DON_55__s50@0.5 | 21.5 | -1,683 | 74,220 | 0.47 | -1,238 | 37.4 | -10,352 | 0.59 | -13,002 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| DON_55__s60@0.5 | 15.5 | -2,046 | 77,786 | 0.38 | -1,402 | 49.1 | -10,397 | 0.39 | -8,721 | 0.00 | False | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| DON_55__s75@0.5 | 12.4 | 9,604 | 81,194 | 0.44 | 6,209 | 74.5 | -2,386 | 0.77 | 927 | 0.01 | False | 4 | s1,s5,s6,s8,s9,s10 |
| VWP_15__s50@0.5 | 12.4 | -8,928 | 63,482 | 0.09 | -6,685 | 48.4 | -14,655 | 0.00 | -10,795 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| VWP_15__s60@0.5 | 10.0 | -6,941 | 64,629 | 0.09 | -5,282 | 61.8 | -13,264 | 0.00 | -8,576 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| VWP_15__s75@0.5 | 8.7 | -8,422 | 73,439 | 0.10 | -5,496 | 39.6 | -13,685 | 0.08 | -8,303 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| VWP_30__s50@0.5 | 13.5 | -9,044 | 63,133 | 0.13 | -6,919 | 45.9 | -14,907 | 0.00 | -10,922 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| VWP_30__s60@0.5 | 10.6 | -6,986 | 65,501 | 0.14 | -5,327 | 69.7 | -13,241 | 0.00 | -9,193 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| VWP_30__s75@0.5 | 9.1 | -8,294 | 72,618 | 0.09 | -5,515 | 32.7 | -13,617 | 0.08 | -9,028 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| SWP_3__s50@0.5 | 23.0 | -17,448 | 75,664 | -0.36 | -12,927 | -0.7 | -21,695 | 0.04 | -27,059 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| SWP_3__s60@0.5 | 16.2 | -7,857 | 73,613 | -0.21 | -6,025 | 13.7 | -15,168 | 0.15 | -15,020 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| SWP_3__s75@0.5 | 12.6 | -7,959 | 79,495 | -0.15 | -5,351 | 39.7 | -14,398 | 0.06 | -10,631 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |
| SWP_6__s50@0.5 | 22.6 | -20,572 | 74,453 | -0.29 | -13,878 | 53.1 | -22,257 | 0.06 | -24,316 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| SWP_6__s60@0.5 | 16.1 | -10,760 | 73,821 | -0.24 | -7,161 | 34.8 | -15,354 | 0.22 | -14,092 | 0.00 | True | 1 | s1,s2,s4,s5,s6,s7,s8,s9,s10 |
| SWP_6__s75@0.5 | 12.5 | -10,476 | 83,384 | -0.15 | -6,652 | 62.5 | -15,132 | 0.11 | -10,693 | 0.00 | True | 2 | s1,s2,s5,s6,s7,s8,s9,s10 |

## Table B - all 162 (cell, split) rows: pass count of 10 and failed conditions (s1 maxDD down>=10%, s2 mean not down, s3 corr<=0.5, s4 standalone holdout mean>0, s5 placebo>=0.95, s6 CI lower>0, s7 2x sign, s8 year<=60%, s9 DSR>=0.95, s10 neighbours)

- ORB_NY_15_v0__s50@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s50@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s50@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s60@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s60@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s60@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v0__s75@0.25: 4/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s75@0.5: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s75@1.0: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s50@0.25: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s50@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s50@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s60@0.25: 5/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s60@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s60@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s75@0.25: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s75@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s75@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s60@0.25: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s75@0.25: 3/10 (common-6: 2/6) failed ['s4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s50@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s50@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s50@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s75@0.25: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v1__s75@0.5: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v1__s75@1.0: 4/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_LON_15_v0__s50@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s50@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s50@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s50@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s50@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s50@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s60@0.25: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s60@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s60@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s75@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s75@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s75@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s50@0.25: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s50@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s50@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s60@0.25: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s60@0.5: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s60@1.0: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s75@0.25: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s75@0.5: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s75@1.0: 8/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s60@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s60@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s60@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v1__s50@0.25: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s50@0.5: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s50@1.0: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s60@0.25: 7/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s60@0.5: 7/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s60@1.0: 7/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@0.25: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@0.5: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@1.0: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- DON_20__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@0.25: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@0.5: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@0.25: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4_stand_hold_mean_pos', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']

## Condition tallies over 162 rows

{'s1_maxdd_down_ge10pct': 1, 's2_mean_not_down': 66, 's3_corr_le_0p5': 162, 's4_stand_hold_mean_pos': 72, 's5_placebo_ge95': 21, 's6_ci_excludes0_positive': 6, 's7_2x_cost_sign_pos': 33, 's8_no_year_gt60pct': 12, 's9_dsr_ge95': 0, 's10_neighbours_agree': 39}
