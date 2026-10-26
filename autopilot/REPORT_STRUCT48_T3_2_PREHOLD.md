# STRUCT48 T3.2 - PRE-HOLDOUT text (written before the holdout is scored)

Prereg l2vast/struct48/prereg/T3_2.md (sha256 5b674a0d79f2905344499d05fa45a61cb89b3a5b53160b8579f333b8c29a2ca7). Window: WF-PRE (2024-02..2025-06) plus IS. Holdout and L8W not computed. Look-ahead audit: 0/360 mismatches in all 18 rules, planted-leak control caught (38/360).

## Table A - every sleeve cell at split 0.5x Set A SD ($/wk, report scale 14 lots; stand = sleeve at 1x unit; port d = portfolio minus Set A)

| cell | trades/wk | stand mean | stand SD | corr | d mean | d maxDD % | CI lo | placebo | 2x d mean | DSR | nb agree | pass/10 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ORB_NY_15_v0__s50@0.5 | 4.8 | 8,015 | 35,536 | -0.00 | 10,999 | 16.0 | -620 | 0.99 | 6,744 | 0.57 | True | 5 | s1,s4(not looked),s6,s8,s9 |
| ORB_NY_15_v0__s60@0.5 | 4.8 | 14,005 | 42,788 | 0.00 | 15,962 | 7.0 | 4,369 | 1.00 | 12,178 | 0.86 | True | 6 | s1,s4(not looked),s8,s9 |
| ORB_NY_15_v0__s75@0.5 | 4.8 | 13,124 | 50,750 | -0.04 | 12,611 | -7.1 | 1,193 | 1.00 | 9,199 | 0.68 | True | 6 | s1,s4(not looked),s8,s9 |
| ORB_NY_15_v1__s50@0.5 | 0.1 | 872 | 6,737 | -0.05 | 6,313 | 3.2 | -3,654 | 0.88 | 5,734 | 0.24 | False | 3 | s1,s4(not looked),s5,s6,s8,s9,s10 |
| ORB_NY_15_v1__s60@0.5 | 0.1 | 1,059 | 8,085 | -0.05 | 6,386 | 3.0 | -3,608 | 0.90 | 5,904 | 0.24 | False | 3 | s1,s4(not looked),s5,s6,s8,s9,s10 |
| ORB_NY_15_v1__s75@0.5 | 0.1 | 787 | 9,573 | -0.13 | 4,010 | 4.3 | -6,666 | 0.79 | 3,584 | 0.13 | False | 3 | s1,s4(not looked),s5,s6,s8,s9,s10 |
| ORB_NY_30_v0__s50@0.5 | 4.8 | 1,705 | 37,534 | -0.03 | 2,216 | 17.6 | -9,120 | 0.86 | -1,878 | 0.08 | True | 3 | s1,s4(not looked),s5,s6,s7,s8,s9 |
| ORB_NY_30_v0__s60@0.5 | 4.8 | 5,036 | 40,532 | 0.02 | 6,058 | 15.8 | -4,782 | 0.95 | 2,246 | 0.24 | True | 5 | s1,s4(not looked),s6,s8,s9 |
| ORB_NY_30_v0__s75@0.5 | 4.8 | 7,307 | 47,337 | 0.16 | 7,528 | 2.8 | -3,246 | 0.97 | 3,580 | 0.33 | True | 5 | s1,s4(not looked),s6,s8,s9 |
| ORB_NY_30_v1__s50@0.5 | 0.1 | -1,010 | 5,046 | 0.02 | -9,757 | 64.4 | -20,734 | 0.13 | -10,675 | 0.00 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v1__s60@0.5 | 0.1 | -633 | 6,455 | 0.11 | -4,779 | 59.6 | -15,808 | 0.20 | -5,468 | 0.01 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_NY_30_v1__s75@0.5 | 0.1 | -773 | 8,049 | 0.11 | -4,681 | 59.3 | -15,731 | 0.26 | -6,709 | 0.01 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v0__s50@0.5 | 4.9 | -8,947 | 35,314 | 0.05 | -12,355 | 93.1 | -23,096 | 0.05 | -16,833 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v0__s60@0.5 | 4.9 | -10,550 | 38,870 | 0.02 | -13,236 | 113.6 | -24,371 | 0.06 | -18,250 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v0__s75@0.5 | 4.9 | -20,267 | 49,634 | 0.10 | -19,913 | 154.6 | -31,432 | 0.00 | -23,164 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s50@0.5 | 0.7 | -2,145 | 16,044 | -0.01 | -6,521 | 50.8 | -17,475 | 0.15 | -7,947 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s60@0.5 | 0.7 | -1,936 | 16,068 | -0.02 | -5,877 | 21.0 | -16,354 | 0.16 | -7,289 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_15_v1__s75@0.5 | 0.7 | -2,328 | 21,800 | -0.09 | -5,208 | 43.8 | -16,513 | 0.18 | -6,250 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s50@0.5 | 4.9 | -7,063 | 39,593 | 0.10 | -8,700 | 94.2 | -19,554 | 0.13 | -12,680 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s60@0.5 | 4.9 | -5,753 | 48,047 | 0.04 | -5,839 | 76.5 | -16,893 | 0.26 | -9,868 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v0__s75@0.5 | 4.9 | -9,264 | 57,550 | 0.07 | -7,850 | 101.2 | -19,284 | 0.22 | -10,613 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s50@0.5 | 0.7 | -1,319 | 15,241 | 0.05 | -4,221 | 28.5 | -15,272 | 0.28 | -5,785 | 0.01 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s60@0.5 | 0.7 | -1,506 | 17,372 | 0.05 | -4,228 | 56.9 | -15,028 | 0.29 | -5,599 | 0.01 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_LON_30_v1__s75@0.5 | 0.7 | -3,727 | 22,262 | -0.05 | -8,165 | 81.8 | -18,307 | 0.10 | -9,260 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v0__s50@0.5 | 4.9 | 3,422 | 40,999 | 0.30 | 4,071 | 23.3 | -7,619 | 0.90 | 330 | 0.15 | True | 4 | s1,s4(not looked),s5,s6,s8,s9 |
| ORB_ASIA_15_v0__s60@0.5 | 4.9 | 2,064 | 48,004 | 0.34 | 2,097 | 38.6 | -9,130 | 0.78 | -1,124 | 0.08 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v0__s75@0.5 | 4.9 | -1,091 | 61,873 | 0.32 | -860 | 35.0 | -12,585 | 0.68 | -3,388 | 0.03 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v1__s50@0.5 | 0.9 | -642 | 15,791 | 0.21 | -1,983 | 43.5 | -12,759 | 0.38 | -3,771 | 0.02 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_15_v1__s60@0.5 | 0.9 | 1,782 | 20,181 | 0.28 | 4,306 | 39.1 | -6,520 | 0.70 | 2,943 | 0.15 | False | 3 | s1,s4(not looked),s5,s6,s8,s9,s10 |
| ORB_ASIA_15_v1__s75@0.5 | 0.9 | 677 | 24,981 | 0.21 | 1,321 | 32.3 | -9,075 | 0.55 | 192 | 0.06 | True | 4 | s1,s4(not looked),s5,s6,s8,s9 |
| ORB_ASIA_30_v0__s50@0.5 | 4.9 | 3,446 | 41,102 | 0.16 | 4,088 | 23.2 | -7,054 | 0.90 | 353 | 0.14 | True | 4 | s1,s4(not looked),s5,s6,s8,s9 |
| ORB_ASIA_30_v0__s60@0.5 | 4.9 | 1,599 | 48,111 | 0.19 | 1,620 | 38.5 | -9,554 | 0.75 | -1,597 | 0.07 | True | 3 | s1,s4(not looked),s5,s6,s7,s8,s9 |
| ORB_ASIA_30_v0__s75@0.5 | 4.9 | 564 | 56,784 | 0.20 | 484 | 45.1 | -10,743 | 0.76 | -2,875 | 0.05 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| ORB_ASIA_30_v1__s50@0.5 | 0.9 | 561 | 17,003 | 0.08 | 1,609 | 45.1 | -9,787 | 0.70 | 18 | 0.07 | False | 3 | s1,s4(not looked),s5,s6,s8,s9,s10 |
| ORB_ASIA_30_v1__s60@0.5 | 0.9 | 1,292 | 20,442 | 0.10 | 3,081 | 44.4 | -8,349 | 0.68 | 1,768 | 0.11 | True | 4 | s1,s4(not looked),s5,s6,s8,s9 |
| ORB_ASIA_30_v1__s75@0.5 | 0.9 | 346 | 24,169 | 0.07 | 699 | 47.1 | -10,597 | 0.54 | -435 | 0.05 | True | 3 | s1,s4(not looked),s5,s6,s7,s8,s9 |
| DON_20__s50@0.5 | 23.1 | -6,974 | 80,871 | 0.48 | -4,206 | 76.5 | -14,810 | 0.47 | -12,678 | 0.01 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| DON_20__s60@0.5 | 15.6 | 7,862 | 76,985 | 0.31 | 4,980 | 62.9 | -5,597 | 0.78 | -2,867 | 0.18 | False | 3 | s1,s4(not looked),s5,s6,s7,s9,s10 |
| DON_20__s75@0.5 | 12.1 | -1,230 | 79,292 | 0.23 | -757 | 102.9 | -11,690 | 0.92 | -5,231 | 0.03 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| DON_55__s50@0.5 | 20.0 | -4,059 | 66,289 | 0.44 | -2,986 | 37.4 | -14,167 | 0.41 | -13,823 | 0.01 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| DON_55__s60@0.5 | 14.5 | 1,620 | 71,162 | 0.49 | 1,110 | 49.1 | -10,150 | 0.67 | -4,530 | 0.06 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| DON_55__s75@0.5 | 11.5 | 4,350 | 75,423 | 0.37 | 2,813 | 74.5 | -8,029 | 0.86 | -2,705 | 0.10 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_15__s50@0.5 | 11.9 | -1,434 | 65,132 | 0.19 | -1,074 | 48.4 | -12,980 | 0.20 | -4,361 | 0.03 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_15__s60@0.5 | 9.7 | 2,879 | 64,084 | 0.17 | 2,191 | 61.8 | -9,259 | 0.40 | -1,329 | 0.08 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_15__s75@0.5 | 8.3 | -100 | 74,728 | 0.19 | -65 | 39.6 | -11,709 | 0.51 | -2,300 | 0.04 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_30__s50@0.5 | 12.7 | -1,026 | 63,747 | 0.19 | -785 | 45.9 | -12,806 | 0.27 | -4,633 | 0.03 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_30__s60@0.5 | 10.1 | 601 | 63,949 | 0.24 | 458 | 69.7 | -11,033 | 0.50 | -3,927 | 0.05 | False | 2 | s1,s4(not looked),s5,s6,s7,s8,s9,s10 |
| VWP_30__s75@0.5 | 8.6 | -1,710 | 73,349 | 0.18 | -1,137 | 32.7 | -12,448 | 0.59 | -3,870 | 0.02 | False | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_3__s50@0.5 | 21.7 | -9,546 | 65,821 | -0.38 | -7,072 | -4.1 | -18,289 | 0.15 | -21,662 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_3__s60@0.5 | 15.3 | -10,146 | 63,592 | -0.16 | -7,781 | 13.7 | -18,591 | 0.07 | -16,727 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_3__s75@0.5 | 12.0 | -16,024 | 72,536 | -0.22 | -10,773 | 39.7 | -22,162 | 0.03 | -17,954 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_6__s50@0.5 | 21.2 | -14,429 | 72,286 | -0.27 | -9,734 | 53.1 | -20,000 | 0.21 | -20,807 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_6__s60@0.5 | 14.6 | -13,019 | 73,269 | -0.25 | -8,665 | 34.8 | -18,614 | 0.09 | -15,274 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |
| SWP_6__s75@0.5 | 11.7 | -22,818 | 76,800 | -0.17 | -14,489 | 62.5 | -24,970 | 0.05 | -18,993 | 0.00 | True | 1 | s1,s2,s4(not looked),s5,s6,s7,s8,s9,s10 |

## Table B - all 162 (cell, split) rows: pass count of 10 and failed conditions (s1 maxDD down>=10%, s2 mean not down, s3 corr<=0.5, s4 standalone holdout mean>0, s5 placebo>=0.95, s6 CI lower>0, s7 2x sign, s8 year<=60%, s9 DSR>=0.95, s10 neighbours)

- ORB_NY_15_v0__s50@0.25: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s50@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s50@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s60@0.25: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s60@0.5: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s60@1.0: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s75@0.25: 6/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s75@0.5: 6/10 (common-6: 5/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v0__s75@1.0: 6/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_15_v1__s50@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s50@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s50@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s60@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s60@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s60@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s75@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s75@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_15_v1__s75@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v0__s50@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s50@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s50@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s60@0.25: 5/10 (common-6: 4/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s60@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s60@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s75@0.25: 6/10 (common-6: 4/6) failed ['s4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s75@0.5: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v0__s75@1.0: 5/10 (common-6: 3/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_NY_30_v1__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_NY_30_v1__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v0__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_15_v1__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v0__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_LON_30_v1__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s50@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s50@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s50@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v0__s60@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s60@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s60@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v0__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s60@0.25: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s60@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s60@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_15_v1__s75@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s75@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_15_v1__s75@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s50@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s60@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s60@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s60@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v0__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v0__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v1__s50@0.25: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v1__s50@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v1__s50@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- ORB_ASIA_30_v1__s60@0.25: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s60@0.5: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s60@1.0: 4/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@0.25: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@0.5: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- ORB_ASIA_30_v1__s75@1.0: 3/10 (common-6: 2/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95']
- DON_20__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@0.25: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@0.5: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s60@1.0: 3/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_20__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s60@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- DON_55__s75@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s60@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_15__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@0.25: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@0.5: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s60@1.0: 2/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- VWP_30__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@0.25: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@0.5: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@0.25: 1/10 (common-6: 1/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_3__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s50@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s60@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@0.25: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@0.5: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']
- SWP_6__s75@1.0: 1/10 (common-6: 0/6) failed ['s1_maxdd_down_ge10pct', 's2_mean_not_down', 's4(not looked)', 's5_placebo_ge95', 's6_ci_excludes0_positive', 's7_2x_cost_sign_pos', 's8_no_year_gt60pct', 's9_dsr_ge95', 's10_neighbours_agree']

## Condition tallies over 162 rows

{'s1_maxdd_down_ge10pct': 1, 's2_mean_not_down': 72, 's3_corr_le_0p5': 162, 's4_stand_hold_mean_pos': 0, 's5_placebo_ge95': 15, 's6_ci_excludes0_positive': 6, 's7_2x_cost_sign_pos': 42, 's8_no_year_gt60pct': 3, 's9_dsr_ge95': 0, 's10_neighbours_agree': 36}
