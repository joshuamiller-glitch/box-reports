# DS3_TC5: D3XT, DS3 addendum-2 track C exit alternatives (G3)

Generated 2026-10-27T21:42:13Z. Research only; nothing is a live recommendation. **V2 pipeline**: the first (v1) run priced exits in the wrong price frame (raw L2 contract prices vs the back-adjusted harness bars); v1 outputs are kept as *_v1_INVALID* and must not be used. The holdout and the 2023 span were read once in v1 (invalid numbers) and are read again here; treat the holdout evidence as second-look.

## Verdict
24 cells scored: **PASS 0, CANDIDATE 0, DEAD 24**. (verdict = s48score.verdict, trade-modifier object, paired vs the same stream's DS2 bracket; PASS downgraded to CANDIDATE if 2023-span, 2x-cost or year-share fails.)

| cell | n pairs WF | n changed | paired WF pts/trade [95% CI] | MDE | HOLD paired | SPAN2 paired | WF d wk $ | HOLD d wk $ | SPAN2 d wk $ | d maxDD (ALL) $ | 1.5x d wk | 2x d wk | placebo | nbrs | peak lots (+DS2) | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | 6952 | 234 | -0.07 [-0.11,-0.03] | 0.05 | -0.07 | -0.18 | -658 | -1,862 | -101 | +22,728 | -663 | -1,085 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_HM | 5162 | 233 | -0.09 [-0.13,-0.05] | 0.06 | -0.05 | -0.29 | -848 | -1,053 | -228 | +38,235 | -455 | -333 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n7 | 1847 | 78 | -0.05 [-0.11,+0.01] | 0.09 | -0.04 | -0.42 | +19 | +51 | -951 | +15,984 | +57 | -46 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n10 | 1833 | 77 | -0.06 [-0.11,-0.01] | 0.08 | -0.05 | -0.32 | -176 | -85 | -571 | -650 | -312 | -475 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n14 | 1868 | 85 | -0.07 [-0.12,-0.03] | 0.07 | -0.06 | -0.33 | -131 | -126 | +193 | +2,890 | -212 | -368 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_KEL3 | 7169 | 252 | -0.05 [-0.11,-0.00] | 0.08 | -0.03 | -0.26 | -419 | +1,303 | -1,046 | -8,998 | -673 | -1,609 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_EMA5 | 1800 | 91 | -0.06 [-0.14,+0.04] | 0.13 | -0.08 | -0.25 | -117 | -200 | -1,080 | +21,842 | -198 | -188 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_TB7 | 895 | 75 | -0.13 [-0.27,-0.01] | 0.19 | -0.05 | -0.54 | -57 | -56 | -667 | +38,380 | -125 | -285 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST | 6952 | 315 | -0.04 [-0.12,+0.04] | 0.11 | -0.07 | -0.24 | -737 | -2,200 | -559 | +24,545 | -1,114 | -1,846 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_HM | 5162 | 296 | -0.04 [-0.15,+0.08] | 0.17 | -0.04 | -0.30 | -679 | -1,389 | -79 | +30,154 | -215 | +44 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n7 | 1847 | 96 | -0.06 [-0.23,+0.10] | 0.23 | -0.07 | -0.58 | -99 | -203 | -1,057 | +32,731 | -283 | -391 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n10 | 1833 | 93 | -0.07 [-0.24,+0.08] | 0.23 | -0.08 | -0.46 | -303 | -359 | -632 | -650 | -665 | -835 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n14 | 1868 | 102 | -0.13 [-0.27,-0.03] | 0.18 | -0.18 | -0.55 | -182 | -318 | -114 | +20,279 | -527 | -695 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_KEL3 | 7169 | 340 | -0.15 [-0.29,-0.03] | 0.19 | -0.10 | -0.36 | -1,216 | +729 | -2,064 | +61,491 | -2,077 | -3,338 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_EMA5 | 1800 | 116 | -0.12 [-0.26,+0.02] | 0.20 | -0.16 | -0.55 | -256 | -392 | -1,294 | +21,573 | -358 | -370 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_TB7 | 895 | 96 | +0.02 [-0.39,+0.45] | 0.60 | -0.03 | -0.43 | +98 | -33 | -518 | +11,020 | -81 | -271 | 1.00 | False | 10 (44) | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST | 6952 | 234 | +0.11 [-0.08,+0.30] | 0.27 | +0.05 | +0.65 | +19 | -804 | +2,229 | -48,055 | -454 | -282 | 1.00 | False | 10 (34) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_HM | 5162 | 233 | +0.03 [-0.22,+0.29] | 0.36 | +0.13 | +1.51 | +1,168 | +4,651 | +4,866 | -82,825 | +467 | +405 | 1.00 | False | 10 (34) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_ST10n7 | 1847 | 78 | -0.08 [-0.46,+0.30] | 0.54 | +0.05 | -1.17 | +107 | +193 | -1,899 | +75,225 | +255 | +355 | 1.00 | True | 10 (44) | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n10 | 1833 | 77 | -0.18 [-0.54,+0.19] | 0.53 | -0.07 | -0.83 | -222 | +435 | -3,841 | -18,538 | -185 | -166 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n14 | 1868 | 85 | -0.04 [-0.41,+0.33] | 0.53 | -0.21 | -0.97 | -289 | -374 | +269 | -16,357 | -60 | +8 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_KEL3 | 7169 | 252 | +0.02 [-0.17,+0.22] | 0.28 | +0.06 | +0.42 | -1,062 | +3,171 | -1,484 | -137,708 | -759 | -572 | 0.99 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5C_EMA5 | 1800 | 91 | +0.08 [-0.37,+0.53] | 0.65 | +0.00 | +0.18 | +330 | +83 | +3,534 | -31,354 | +379 | +429 | 0.96 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_TB7 | 895 | 75 | +0.46 [-0.36,+1.30] | 1.17 | +0.45 | +2.57 | +487 | +486 | +1,463 | -149,256 | +546 | +514 | 0.97 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |

## Long / short / quiet / wide columns (paired pts/trade [95% CI], n) on the scoring window (WF)
| cell | long | short | quiet | wide |
|---|---|---|---|---|
| XT_C5A_ST | -0.07 [-0.12,-0.03] n3257 | -0.07 [-0.12,-0.02] n3695 | -0.15 [-0.23,-0.06] n2117 | -0.03 [-0.07,-0.00] n4831 |
| XT_C5A_HM | -0.07 [-0.13,-0.02] n2660 | -0.11 [-0.17,-0.06] n2502 | -0.13 [-0.21,-0.06] n1681 | -0.07 [-0.12,-0.03] n3477 |
| XT_C5A_ST10n7 | -0.01 [-0.10,+0.10] n907 | -0.09 [-0.17,-0.02] n940 | -0.00 [-0.14,+0.14] n671 | -0.08 [-0.13,-0.03] n1175 |
| XT_C5A_ST10n10 | -0.04 [-0.12,+0.05] n898 | -0.08 [-0.15,-0.02] n935 | -0.00 [-0.09,+0.11] n660 | -0.09 [-0.16,-0.03] n1173 |
| XT_C5A_ST10n14 | -0.06 [-0.13,+0.00] n916 | -0.08 [-0.16,-0.02] n952 | -0.06 [-0.15,+0.02] n674 | -0.07 [-0.13,-0.02] n1194 |
| XT_C5A_KEL3 | -0.09 [-0.19,-0.02] n3709 | -0.01 [-0.07,+0.06] n3460 | -0.08 [-0.16,-0.01] n2165 | -0.04 [-0.12,+0.03] n4999 |
| XT_C5A_EMA5 | -0.10 [-0.17,-0.03] n868 | -0.03 [-0.16,+0.17] n932 | -0.13 [-0.25,-0.03] n659 | -0.02 [-0.12,+0.13] n1139 |
| XT_C5A_TB7 | -0.10 [-0.24,+0.06] n462 | -0.16 [-0.41,-0.01] n433 | -0.12 [-0.31,+0.06] n322 | -0.13 [-0.34,+0.01] n573 |
| XT_C5B_ST | -0.00 [-0.12,+0.12] n3257 | -0.07 [-0.17,+0.04] n3695 | -0.05 [-0.23,+0.14] n2117 | -0.03 [-0.12,+0.05] n4831 |
| XT_C5B_HM | +0.04 [-0.15,+0.21] n2660 | -0.11 [-0.25,+0.02] n2502 | -0.10 [-0.36,+0.17] n1681 | -0.00 [-0.12,+0.11] n3477 |
| XT_C5B_ST10n7 | -0.06 [-0.35,+0.18] n907 | -0.06 [-0.24,+0.16] n940 | +0.12 [-0.19,+0.45] n671 | -0.16 [-0.36,-0.04] n1175 |
| XT_C5B_ST10n10 | -0.09 [-0.36,+0.15] n898 | -0.05 [-0.24,+0.17] n935 | +0.12 [-0.16,+0.47] n660 | -0.18 [-0.39,-0.05] n1173 |
| XT_C5B_ST10n14 | -0.16 [-0.42,+0.01] n916 | -0.11 [-0.25,+0.00] n952 | -0.14 [-0.31,-0.01] n674 | -0.13 [-0.34,+0.01] n1194 |
| XT_C5B_KEL3 | -0.21 [-0.47,+0.01] n3709 | -0.09 [-0.21,+0.01] n3460 | -0.16 [-0.40,+0.07] n2165 | -0.15 [-0.33,+0.00] n4999 |
| XT_C5B_EMA5 | -0.07 [-0.24,+0.09] n868 | -0.17 [-0.40,+0.07] n932 | -0.14 [-0.37,+0.08] n659 | -0.11 [-0.29,+0.08] n1139 |
| XT_C5B_TB7 | +0.24 [-0.42,+0.99] n462 | -0.21 [-0.66,+0.29] n433 | +0.09 [-0.55,+0.81] n322 | -0.02 [-0.53,+0.51] n573 |
| XT_C5C_ST | +0.16 [-0.14,+0.48] n3257 | +0.06 [-0.15,+0.28] n3695 | +0.21 [-0.21,+0.63] n2117 | +0.06 [-0.12,+0.24] n4831 |
| XT_C5C_HM | +0.04 [-0.37,+0.45] n2660 | +0.03 [-0.25,+0.30] n2502 | +0.00 [-0.55,+0.56] n1681 | +0.05 [-0.21,+0.30] n3477 |
| XT_C5C_ST10n7 | +0.13 [-0.46,+0.74] n907 | -0.28 [-0.76,+0.17] n940 | +0.15 [-0.67,+1.03] n671 | -0.22 [-0.59,+0.15] n1175 |
| XT_C5C_ST10n10 | -0.14 [-0.74,+0.45] n898 | -0.21 [-0.71,+0.24] n935 | -0.12 [-0.94,+0.72] n660 | -0.21 [-0.57,+0.12] n1173 |
| XT_C5C_ST10n14 | +0.04 [-0.53,+0.61] n916 | -0.12 [-0.64,+0.36] n952 | +0.12 [-0.74,+1.04] n674 | -0.13 [-0.45,+0.18] n1194 |
| XT_C5C_KEL3 | -0.04 [-0.34,+0.26] n3709 | +0.09 [-0.13,+0.32] n3460 | +0.16 [-0.28,+0.58] n2165 | -0.04 [-0.24,+0.17] n4999 |
| XT_C5C_EMA5 | -0.11 [-0.71,+0.50] n868 | +0.26 [-0.41,+0.94] n932 | +0.08 [-0.93,+1.10] n659 | +0.08 [-0.33,+0.49] n1139 |
| XT_C5C_TB7 | -0.31 [-1.53,+0.89] n462 | +1.29 [+0.23,+2.48] n433 | +1.19 [-0.63,+3.17] n322 | +0.06 [-0.71,+0.84] n573 |

## Weekly P&L (10 lots, exact per-book locks, WF 2024-02+; base = same stream fixed bracket)
| cell | WF wk mean rule | WF wk mean base | WF wk SD rule | base | WF worst wk rule | base | maxDD ALL rule | base | trades/wk rule | base | taken rule | taken base |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | 3,285 | 3,943 | 55,950 | 56,580 | -110,468 | -96,575 | 464,224 | 441,496 | 24.0 | 23.7 | 8155 | 8156 |
| XT_C5A_HM | -2,594 | -1,746 | 51,489 | 51,751 | -138,460 | -138,460 | 660,024 | 621,790 | 22.0 | 22.0 | 6202 | 6202 |
| XT_C5A_ST10n7 | 3,493 | 3,475 | 37,426 | 37,536 | -90,867 | -90,867 | 277,442 | 261,458 | 11.6 | 11.6 | 2366 | 2366 |
| XT_C5A_ST10n10 | 3,989 | 4,166 | 41,755 | 41,663 | -95,479 | -95,479 | 371,686 | 372,336 | 11.6 | 11.6 | 2361 | 2361 |
| XT_C5A_ST10n14 | 4,453 | 4,584 | 39,908 | 39,938 | -89,306 | -89,306 | 307,331 | 304,441 | 11.6 | 11.6 | 2409 | 2409 |
| XT_C5A_KEL3 | 34 | 453 | 55,639 | 55,539 | -122,271 | -121,961 | 838,725 | 847,723 | 24.2 | 24.0 | 8423 | 8423 |
| XT_C5A_EMA5 | 3,182 | 3,300 | 36,398 | 36,293 | -83,696 | -83,696 | 285,782 | 263,940 | 11.2 | 11.2 | 2304 | 2304 |
| XT_C5A_TB7 | -4,557 | -4,500 | 31,749 | 31,882 | -83,752 | -83,764 | 1,074,803 | 1,036,423 | 6.1 | 6.1 | 1210 | 1210 |
| XT_C5B_ST | 3,206 | 3,943 | 56,488 | 56,580 | -121,066 | -96,575 | 466,040 | 441,496 | 24.0 | 23.7 | 8155 | 8156 |
| XT_C5B_HM | -2,425 | -1,746 | 51,824 | 51,751 | -138,460 | -138,460 | 651,943 | 621,790 | 22.0 | 22.0 | 6202 | 6202 |
| XT_C5B_ST10n7 | 3,375 | 3,475 | 37,399 | 37,536 | -90,867 | -90,867 | 294,188 | 261,458 | 11.6 | 11.6 | 2366 | 2366 |
| XT_C5B_ST10n10 | 3,862 | 4,166 | 41,621 | 41,663 | -95,479 | -95,479 | 371,686 | 372,336 | 11.6 | 11.6 | 2361 | 2361 |
| XT_C5B_ST10n14 | 4,401 | 4,584 | 39,910 | 39,938 | -89,306 | -89,306 | 324,720 | 304,441 | 11.6 | 11.6 | 2409 | 2409 |
| XT_C5B_KEL3 | -763 | 453 | 55,488 | 55,539 | -144,340 | -121,961 | 909,214 | 847,723 | 24.3 | 24.0 | 8423 | 8423 |
| XT_C5B_EMA5 | 3,044 | 3,300 | 36,349 | 36,293 | -83,696 | -83,696 | 285,513 | 263,940 | 11.2 | 11.2 | 2304 | 2304 |
| XT_C5B_TB7 | -4,402 | -4,500 | 31,948 | 31,882 | -83,752 | -83,764 | 1,047,443 | 1,036,423 | 6.1 | 6.1 | 1210 | 1210 |
| XT_C5C_ST | 3,963 | 3,943 | 55,051 | 56,580 | -105,813 | -96,575 | 393,441 | 441,496 | 23.1 | 23.7 | 7913 | 8156 |
| XT_C5C_HM | -578 | -1,746 | 51,735 | 51,751 | -114,402 | -138,460 | 538,965 | 621,790 | 21.0 | 22.0 | 5957 | 6202 |
| XT_C5C_ST10n7 | 3,582 | 3,475 | 36,833 | 37,536 | -90,867 | -90,867 | 336,683 | 261,458 | 11.4 | 11.6 | 2308 | 2366 |
| XT_C5C_ST10n10 | 3,944 | 4,166 | 42,095 | 41,663 | -95,479 | -95,479 | 353,798 | 372,336 | 11.4 | 11.6 | 2317 | 2361 |
| XT_C5C_ST10n14 | 4,294 | 4,584 | 40,514 | 39,938 | -106,819 | -89,306 | 288,084 | 304,441 | 11.3 | 11.6 | 2356 | 2409 |
| XT_C5C_KEL3 | -609 | 453 | 56,437 | 55,539 | -118,205 | -121,961 | 710,015 | 847,723 | 23.5 | 24.0 | 8140 | 8423 |
| XT_C5C_EMA5 | 3,630 | 3,300 | 37,428 | 36,293 | -90,792 | -83,696 | 232,586 | 263,940 | 11.0 | 11.2 | 2243 | 2304 |
| XT_C5C_TB7 | -4,013 | -4,500 | 32,546 | 31,882 | -83,752 | -83,764 | 887,167 | 1,036,423 | 6.1 | 6.1 | 1203 | 1210 |

## Exit mix, duration and pricing diagnostics
| cell | exit reasons (0 stop,1 tgt,2 flat,3 time,4 opp,5 horizon,6 trail) | median hold min | mean exit friction S / M (pts) | missing exit fills | seq dropped | placebo mean pts / sd | overnight trades | peak lots DS2 alone | cap50 ok |
|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | {'1': 4060, '0': 3790, '5': 225, '2': 81} | 46 | 2.27 / 2.77 | 6 | 1 | -1.94 / 0.27 | 169 | 34 | True |
| XT_C5A_HM | {'1': 3090, '0': 2820, '5': 229, '2': 63} | 61 | 2.24 / 2.92 | 7 | 0 | -2.02 / 0.33 | 180 | 34 | True |
| XT_C5A_ST10n7 | {'1': 1207, '0': 1066, '5': 75, '2': 18} | 76 | 1.78 / 2.88 | 1 | 0 | -2.80 / 0.58 | 68 | 34 | True |
| XT_C5A_ST10n10 | {'1': 1214, '0': 1056, '5': 75, '2': 16} | 74 | 1.85 / 2.95 | 1 | 0 | -2.47 / 0.57 | 67 | 34 | True |
| XT_C5A_ST10n14 | {'1': 1232, '0': 1078, '5': 82, '2': 17} | 71 | 1.69 / 2.84 | 3 | 0 | -2.53 / 0.53 | 74 | 34 | True |
| XT_C5A_KEL3 | {'1': 4146, '0': 3947, '5': 242, '2': 88} | 49 | 2.60 / 2.67 | 9 | 0 | -1.80 / 0.31 | 181 | 34 | True |
| XT_C5A_EMA5 | {'1': 1156, '0': 1034, '5': 89, '2': 25} | 85 | 1.99 / 2.43 | 1 | 0 | -1.78 / 0.57 | 76 | 34 | True |
| XT_C5A_TB7 | {'1': 574, '0': 545, '5': 70, '2': 21} | 34 | 2.26 / 2.41 | 0 | 0 | -1.78 / 0.74 | 73 | 34 | True |
| XT_C5B_ST | {'1': 4071, '0': 3797, '5': 288} | 46 | 2.28 / 3.66 | 7 | 1 | -2.37 / 0.27 | 224 | 34 | True |
| XT_C5B_HM | {'1': 3101, '0': 2826, '5': 275} | 61 | 2.28 / 3.57 | 8 | 0 | -2.29 / 0.34 | 217 | 34 | True |
| XT_C5B_ST10n7 | {'1': 1210, '0': 1068, '5': 88} | 76 | 1.83 / 3.44 | 1 | 0 | -3.09 / 0.59 | 83 | 34 | True |
| XT_C5B_ST10n10 | {'1': 1217, '0': 1058, '5': 86} | 74 | 1.90 / 3.50 | 1 | 0 | -2.74 / 0.57 | 80 | 34 | True |
| XT_C5B_ST10n14 | {'1': 1233, '0': 1080, '5': 96} | 71 | 1.74 / 3.37 | 3 | 0 | -2.80 / 0.53 | 87 | 34 | True |
| XT_C5B_KEL3 | {'1': 4158, '0': 3958, '5': 307} | 49 | 2.73 / 3.39 | 10 | 0 | -2.20 / 0.31 | 245 | 34 | True |
| XT_C5B_EMA5 | {'1': 1157, '0': 1036, '5': 111} | 85 | 2.00 / 3.04 | 1 | 0 | -2.10 / 0.56 | 97 | 34 | True |
| XT_C5B_TB7 | {'1': 579, '0': 547, '5': 84} | 34 | 2.31 / 2.91 | 0 | 0 | -2.00 / 0.75 | 92 | 34 | True |
| XT_C5C_ST | {'1': 4185, '0': 3885, '2': 81, '5': 5} | 46 | 2.24 / 0.72 | 0 | 243 | -0.90 / 0.27 | 162 | 34 | True |
| XT_C5C_HM | {'1': 3217, '0': 2917, '2': 63, '5': 5} | 61 | 2.23 / 0.87 | 1 | 245 | -0.97 / 0.33 | 176 | 34 | True |
| XT_C5C_ST10n7 | {'1': 1235, '0': 1112, '2': 18, '5': 1} | 76 | 1.78 / 1.33 | 0 | 58 | -2.03 / 0.59 | 66 | 34 | True |
| XT_C5C_ST10n10 | {'1': 1243, '0': 1101, '2': 16, '5': 1} | 74 | 1.87 / 1.38 | 0 | 44 | -1.69 / 0.56 | 64 | 34 | True |
| XT_C5C_ST10n14 | {'1': 1266, '0': 1124, '2': 17, '5': 2} | 71 | 1.68 / 1.13 | 0 | 53 | -1.66 / 0.55 | 70 | 34 | True |
| XT_C5C_KEL3 | {'1': 4276, '0': 4053, '2': 88, '5': 6} | 49 | 2.58 / 0.83 | 1 | 283 | -0.87 / 0.31 | 171 | 34 | True |
| XT_C5C_EMA5 | {'1': 1202, '0': 1074, '2': 25, '5': 3} | 85 | 1.98 / 0.84 | 0 | 61 | -0.98 / 0.58 | 74 | 34 | True |
| XT_C5C_TB7 | {'1': 620, '0': 568, '2': 21, '5': 1} | 34 | 2.11 / 0.72 | 0 | 7 | -0.89 / 0.74 | 72 | 34 | True |

## Weekend / Sunday-open gap risk (NQ, all Friday 16:55 -> Sunday 18:00 opens 2023-02..2026-10): n 1106, mean -3.7 pts, SD 98.8, 5th/95th pct -213.1/+104.8, min -405.0, max +415.2. A 10-lot book carries $200 per point: a 1-SD gap is $19,752, the worst gap $-81,000/83,050. Stops are market-stop orders: a Sunday gap through the 60-pt stop fills at the open (in the L2 replay at the actual book), not at the stop.

## Caveats
- Sequence uses the BASE entry set only: a rule that exits earlier (time stop, trail) does not create new entries; a rule that holds longer skips base entries that arrive while it is open (counted in `seq dropped`).
- Exit prices are direct L2 (stop-join / market / limit-at-level); the placebo uses the nominal 1-s path with the rule's mean friction (ranking only).
- 2023-04..2024-01 span: entries and exits replayed directly too (L2 on disk from 2023-02).
- Target fills assume a limit at the level fills on touch (identical in base and rule).
- Holdout looked once per prereg group (pre-holdout texts autopilot/DS3_TC_<G>_PREHOLD.md); books reusing T-ENTRY/T-B series have had earlier holdout looks.
