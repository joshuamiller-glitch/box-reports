# DS3_TC5: D3XT, DS3 addendum-2 track C exit alternatives (G3)

Generated 2026-10-27T13:23:24Z. Research only; nothing is a live recommendation. **V2 pipeline**: the first (v1) run priced exits in the wrong price frame (raw L2 contract prices vs the back-adjusted harness bars); v1 outputs are kept as *_v1_INVALID* and must not be used. The holdout and the 2023 span were read once in v1 (invalid numbers) and are read again here; treat the holdout evidence as second-look.

## Verdict
24 cells scored: **PASS 0, CANDIDATE 0, DEAD 24**. (verdict = s48score.verdict, trade-modifier object, paired vs the same stream's DS2 bracket; PASS downgraded to CANDIDATE if 2023-span, 2x-cost or year-share fails.)

| cell | n pairs WF | n changed | paired WF pts/trade [95% CI] | MDE | HOLD paired | SPAN2 paired | WF d wk $ | HOLD d wk $ | SPAN2 d wk $ | d maxDD (ALL) $ | 1.5x d wk | 2x d wk | placebo | nbrs | peak lots (+DS2) | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | 7105 | 234 | -0.07 [-0.10,-0.04] | 0.05 | -0.07 | -0.18 | -658 | -1,862 | -101 | +22,728 | -663 | -1,085 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_HM | 5271 | 234 | -0.09 [-0.13,-0.05] | 0.06 | -0.05 | -0.29 | -834 | -1,024 | -228 | +38,235 | -441 | -319 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n7 | 1878 | 78 | -0.05 [-0.11,+0.02] | 0.09 | -0.04 | -0.42 | +19 | +51 | -951 | +15,984 | +57 | -46 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n10 | 1864 | 77 | -0.06 [-0.11,-0.01] | 0.07 | -0.05 | -0.32 | -176 | -85 | -571 | -650 | -312 | -475 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n14 | 1898 | 85 | -0.07 [-0.12,-0.03] | 0.07 | -0.06 | -0.33 | -131 | -126 | +193 | +2,890 | -212 | -368 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_KEL3 | 7339 | 253 | -0.05 [-0.11,+0.00] | 0.08 | -0.02 | -0.26 | -419 | +1,303 | -1,046 | -8,998 | -673 | -1,609 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_EMA5 | 1831 | 91 | -0.06 [-0.14,+0.04] | 0.13 | -0.08 | -0.25 | -117 | -200 | -1,080 | +21,842 | -198 | -188 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_TB7 | 898 | 75 | -0.13 [-0.27,-0.01] | 0.19 | -0.05 | -0.54 | -57 | -56 | -667 | +38,380 | -125 | -285 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST | 7105 | 315 | -0.04 [-0.11,+0.04] | 0.11 | -0.06 | -0.24 | -737 | -2,200 | -559 | +24,545 | -1,114 | -1,846 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_HM | 5271 | 297 | -0.03 [-0.15,+0.08] | 0.16 | -0.04 | -0.30 | -665 | -1,360 | -79 | +30,154 | -201 | +58 | 1.00 | False | 10 (34) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n7 | 1878 | 96 | -0.06 [-0.23,+0.10] | 0.23 | -0.06 | -0.58 | -99 | -203 | -1,057 | +32,731 | -283 | -391 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n10 | 1864 | 93 | -0.07 [-0.24,+0.09] | 0.23 | -0.08 | -0.46 | -303 | -359 | -632 | -650 | -665 | -835 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n14 | 1898 | 102 | -0.13 [-0.28,-0.03] | 0.18 | -0.18 | -0.55 | -182 | -318 | -114 | +20,279 | -527 | -695 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_KEL3 | 7339 | 341 | -0.15 [-0.29,-0.03] | 0.19 | -0.09 | -0.36 | -989 | +1,201 | -2,064 | +61,491 | -1,844 | -3,097 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_EMA5 | 1831 | 116 | -0.12 [-0.26,+0.02] | 0.20 | -0.15 | -0.55 | -256 | -392 | -1,294 | +21,573 | -358 | -370 | 1.00 | False | 10 (44) | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_TB7 | 898 | 96 | +0.02 [-0.39,+0.45] | 0.60 | -0.03 | -0.43 | +98 | -33 | -518 | +11,020 | -81 | -271 | 1.00 | False | 10 (44) | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST | 7105 | 234 | +0.11 [-0.08,+0.28] | 0.25 | +0.05 | +0.65 | +19 | -804 | +2,229 | -48,055 | -454 | -282 | 1.00 | False | 10 (34) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_HM | 5271 | 234 | +0.05 [-0.20,+0.29] | 0.35 | +0.16 | +1.51 | +1,208 | +4,733 | +4,866 | -82,825 | +508 | +447 | 1.00 | False | 10 (34) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_ST10n7 | 1878 | 78 | -0.08 [-0.45,+0.30] | 0.53 | +0.05 | -1.17 | +107 | +193 | -1,899 | +75,225 | +255 | +355 | 1.00 | True | 10 (44) | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n10 | 1864 | 77 | -0.17 [-0.54,+0.20] | 0.52 | -0.07 | -0.83 | -222 | +435 | -3,841 | -18,538 | -185 | -166 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n14 | 1898 | 85 | -0.04 [-0.41,+0.32] | 0.53 | -0.20 | -0.97 | -289 | -374 | +269 | -24,263 | -60 | +8 | 1.00 | True | 10 (44) | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_KEL3 | 7339 | 253 | +0.03 [-0.16,+0.22] | 0.27 | +0.08 | +0.42 | -1,022 | +3,255 | -1,484 | -137,708 | -717 | -528 | 1.00 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_EMA5 | 1831 | 91 | +0.08 [-0.36,+0.53] | 0.64 | +0.00 | +0.18 | +330 | +83 | +3,534 | -31,354 | +379 | +429 | 0.96 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_TB7 | 898 | 75 | +0.46 [-0.36,+1.28] | 1.17 | +0.44 | +2.57 | +487 | +486 | +1,463 | -149,256 | +546 | +514 | 0.98 | False | 10 (44) | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |

## Long / short / quiet / wide columns (paired pts/trade [95% CI], n) on the scoring window (WF)
| cell | long | short | quiet | wide |
|---|---|---|---|---|
| XT_C5A_ST | -0.07 [-0.12,-0.03] n3313 | -0.07 [-0.12,-0.01] n3792 | -0.15 [-0.23,-0.06] n2128 | -0.03 [-0.07,-0.00] n4897 |
| XT_C5A_HM | -0.07 [-0.13,-0.01] n2705 | -0.10 [-0.16,-0.05] n2566 | -0.13 [-0.21,-0.06] n1687 | -0.07 [-0.12,-0.02] n3522 |
| XT_C5A_ST10n7 | -0.01 [-0.10,+0.10] n923 | -0.09 [-0.16,-0.02] n955 | -0.00 [-0.14,+0.15] n673 | -0.08 [-0.13,-0.03] n1189 |
| XT_C5A_ST10n10 | -0.04 [-0.12,+0.05] n914 | -0.08 [-0.15,-0.02] n950 | -0.00 [-0.09,+0.10] n662 | -0.09 [-0.16,-0.03] n1187 |
| XT_C5A_ST10n14 | -0.06 [-0.13,+0.00] n932 | -0.08 [-0.15,-0.02] n966 | -0.06 [-0.15,+0.01] n676 | -0.07 [-0.13,-0.02] n1208 |
| XT_C5A_KEL3 | -0.09 [-0.19,-0.02] n3777 | -0.01 [-0.06,+0.05] n3562 | -0.08 [-0.16,-0.01] n2174 | -0.04 [-0.11,+0.03] n5071 |
| XT_C5A_EMA5 | -0.10 [-0.17,-0.03] n882 | -0.03 [-0.16,+0.16] n949 | -0.13 [-0.25,-0.03] n659 | -0.02 [-0.12,+0.13] n1150 |
| XT_C5A_TB7 | -0.10 [-0.24,+0.07] n463 | -0.16 [-0.41,-0.01] n435 | -0.12 [-0.31,+0.06] n322 | -0.13 [-0.35,+0.02] n576 |
| XT_C5B_ST | -0.00 [-0.12,+0.11] n3313 | -0.07 [-0.17,+0.05] n3792 | -0.05 [-0.22,+0.13] n2128 | -0.03 [-0.11,+0.05] n4897 |
| XT_C5B_HM | +0.04 [-0.15,+0.22] n2705 | -0.11 [-0.23,+0.03] n2566 | -0.10 [-0.35,+0.17] n1687 | -0.00 [-0.11,+0.11] n3522 |
| XT_C5B_ST10n7 | -0.06 [-0.33,+0.16] n923 | -0.06 [-0.24,+0.17] n955 | +0.12 [-0.20,+0.49] n673 | -0.16 [-0.35,-0.04] n1189 |
| XT_C5B_ST10n10 | -0.09 [-0.37,+0.13] n914 | -0.05 [-0.23,+0.16] n950 | +0.12 [-0.16,+0.49] n662 | -0.18 [-0.37,-0.05] n1187 |
| XT_C5B_ST10n14 | -0.16 [-0.41,+0.01] n932 | -0.11 [-0.24,+0.01] n966 | -0.14 [-0.30,-0.01] n676 | -0.13 [-0.33,+0.01] n1208 |
| XT_C5B_KEL3 | -0.20 [-0.46,+0.01] n3777 | -0.09 [-0.20,+0.01] n3562 | -0.16 [-0.41,+0.06] n2174 | -0.15 [-0.31,-0.00] n5071 |
| XT_C5B_EMA5 | -0.07 [-0.23,+0.09] n882 | -0.17 [-0.39,+0.06] n949 | -0.14 [-0.37,+0.08] n659 | -0.11 [-0.30,+0.07] n1150 |
| XT_C5B_TB7 | +0.24 [-0.40,+0.96] n463 | -0.21 [-0.68,+0.28] n435 | +0.09 [-0.55,+0.81] n322 | -0.02 [-0.56,+0.53] n576 |
| XT_C5C_ST | +0.15 [-0.14,+0.45] n3313 | +0.06 [-0.15,+0.28] n3792 | +0.21 [-0.22,+0.66] n2128 | +0.06 [-0.11,+0.24] n4897 |
| XT_C5C_HM | +0.04 [-0.35,+0.44] n2705 | +0.06 [-0.22,+0.33] n2566 | +0.00 [-0.56,+0.57] n1687 | +0.07 [-0.18,+0.32] n3522 |
| XT_C5C_ST10n7 | +0.13 [-0.46,+0.70] n923 | -0.28 [-0.77,+0.19] n955 | +0.15 [-0.67,+1.01] n673 | -0.21 [-0.58,+0.12] n1189 |
| XT_C5C_ST10n10 | -0.14 [-0.70,+0.41] n914 | -0.21 [-0.67,+0.27] n950 | -0.12 [-0.96,+0.79] n662 | -0.21 [-0.54,+0.13] n1187 |
| XT_C5C_ST10n14 | +0.04 [-0.53,+0.57] n932 | -0.12 [-0.62,+0.39] n966 | +0.12 [-0.73,+0.95] n676 | -0.13 [-0.45,+0.19] n1208 |
| XT_C5C_KEL3 | -0.04 [-0.37,+0.27] n3777 | +0.11 [-0.11,+0.32] n3562 | +0.16 [-0.26,+0.60] n2174 | -0.02 [-0.23,+0.19] n5071 |
| XT_C5C_EMA5 | -0.11 [-0.73,+0.47] n882 | +0.26 [-0.41,+0.98] n949 | +0.08 [-0.93,+1.10] n659 | +0.08 [-0.34,+0.48] n1150 |
| XT_C5C_TB7 | -0.31 [-1.60,+0.90] n463 | +1.28 [+0.24,+2.43] n435 | +1.19 [-0.63,+3.17] n322 | +0.06 [-0.77,+0.84] n576 |

## Weekly P&L (10 lots, exact per-book locks, WF 2024-02+; base = same stream fixed bracket)
| cell | WF wk mean rule | WF wk mean base | WF wk SD rule | base | WF worst wk rule | base | maxDD ALL rule | base | trades/wk rule | base | taken rule | taken base |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | 3,758 | 4,417 | 56,095 | 56,718 | -110,468 | -96,575 | 464,224 | 441,496 | 24.4 | 24.1 | 8308 | 8309 |
| XT_C5A_HM | -2,671 | -1,837 | 51,583 | 51,840 | -138,460 | -138,460 | 660,024 | 621,790 | 22.4 | 22.3 | 6311 | 6311 |
| XT_C5A_ST10n7 | 2,937 | 2,918 | 37,877 | 37,985 | -90,867 | -90,867 | 277,442 | 261,458 | 11.8 | 11.8 | 2397 | 2397 |
| XT_C5A_ST10n10 | 3,354 | 3,530 | 42,211 | 42,122 | -95,479 | -95,479 | 371,686 | 372,336 | 11.8 | 11.7 | 2392 | 2392 |
| XT_C5A_ST10n14 | 3,817 | 3,948 | 40,392 | 40,424 | -89,306 | -89,306 | 315,237 | 312,347 | 11.7 | 11.7 | 2439 | 2439 |
| XT_C5A_KEL3 | 715 | 1,134 | 55,972 | 55,868 | -122,271 | -121,961 | 838,725 | 847,723 | 24.7 | 24.6 | 8593 | 8593 |
| XT_C5A_EMA5 | 2,885 | 3,002 | 36,864 | 36,762 | -83,696 | -83,696 | 285,782 | 263,940 | 11.4 | 11.4 | 2335 | 2335 |
| XT_C5A_TB7 | -4,478 | -4,421 | 31,775 | 31,908 | -83,752 | -83,764 | 1,074,803 | 1,036,423 | 6.1 | 6.1 | 1213 | 1213 |
| XT_C5B_ST | 3,680 | 4,417 | 56,633 | 56,718 | -121,066 | -96,575 | 466,040 | 441,496 | 24.4 | 24.1 | 8308 | 8309 |
| XT_C5B_HM | -2,501 | -1,837 | 51,918 | 51,840 | -138,460 | -138,460 | 651,943 | 621,790 | 22.3 | 22.3 | 6311 | 6311 |
| XT_C5B_ST10n7 | 2,819 | 2,918 | 37,849 | 37,985 | -90,867 | -90,867 | 294,188 | 261,458 | 11.8 | 11.8 | 2397 | 2397 |
| XT_C5B_ST10n10 | 3,227 | 3,530 | 42,076 | 42,122 | -95,479 | -95,479 | 371,686 | 372,336 | 11.7 | 11.7 | 2392 | 2392 |
| XT_C5B_ST10n14 | 3,765 | 3,948 | 40,393 | 40,424 | -89,306 | -89,306 | 332,626 | 312,347 | 11.8 | 11.7 | 2439 | 2439 |
| XT_C5B_KEL3 | 146 | 1,134 | 56,255 | 55,868 | -144,340 | -121,961 | 909,214 | 847,723 | 24.8 | 24.6 | 8593 | 8593 |
| XT_C5B_EMA5 | 2,747 | 3,002 | 36,815 | 36,762 | -83,696 | -83,696 | 285,513 | 263,940 | 11.4 | 11.4 | 2335 | 2335 |
| XT_C5B_TB7 | -4,323 | -4,421 | 31,974 | 31,908 | -83,752 | -83,764 | 1,047,443 | 1,036,423 | 6.1 | 6.1 | 1213 | 1213 |
| XT_C5C_ST | 4,436 | 4,417 | 55,193 | 56,718 | -105,813 | -96,575 | 393,441 | 441,496 | 23.5 | 24.1 | 8066 | 8309 |
| XT_C5C_HM | -628 | -1,837 | 51,843 | 51,840 | -114,402 | -138,460 | 538,965 | 621,790 | 21.4 | 22.3 | 6064 | 6311 |
| XT_C5C_ST10n7 | 3,025 | 2,918 | 37,292 | 37,985 | -90,867 | -90,867 | 336,683 | 261,458 | 11.6 | 11.8 | 2339 | 2397 |
| XT_C5C_ST10n10 | 3,308 | 3,530 | 42,546 | 42,122 | -95,479 | -95,479 | 353,798 | 372,336 | 11.6 | 11.7 | 2348 | 2392 |
| XT_C5C_ST10n14 | 3,658 | 3,948 | 40,989 | 40,424 | -106,819 | -89,306 | 288,084 | 312,347 | 11.5 | 11.7 | 2386 | 2439 |
| XT_C5C_KEL3 | 113 | 1,134 | 56,823 | 55,868 | -118,205 | -121,961 | 710,015 | 847,723 | 24.0 | 24.6 | 8309 | 8593 |
| XT_C5C_EMA5 | 3,333 | 3,002 | 37,886 | 36,762 | -90,792 | -83,696 | 232,586 | 263,940 | 11.2 | 11.4 | 2274 | 2335 |
| XT_C5C_TB7 | -3,934 | -4,421 | 32,570 | 31,908 | -83,752 | -83,764 | 887,167 | 1,036,423 | 6.1 | 6.1 | 1206 | 1213 |

## Exit mix, duration and pricing diagnostics
| cell | exit reasons (0 stop,1 tgt,2 flat,3 time,4 opp,5 horizon,6 trail) | median hold min | mean exit friction S / M (pts) | missing exit fills | seq dropped | placebo mean pts / sd | overnight trades | peak lots DS2 alone | cap50 ok |
|---|---|---|---|---|---|---|---|---|---|
| XT_C5A_ST | {'1': 4137, '0': 3866, '5': 225, '2': 81} | 45 | 2.24 / 2.77 | 82 | 1 | -1.91 / 0.26 | 169 | 34 | True |
| XT_C5A_HM | {'1': 3146, '0': 2872, '5': 230, '2': 63} | 60 | 2.22 / 2.92 | 60 | 0 | -1.98 / 0.31 | 181 | 34 | True |
| XT_C5A_ST10n7 | {'1': 1221, '0': 1083, '5': 75, '2': 18} | 75 | 1.77 / 2.88 | 18 | 0 | -2.71 / 0.57 | 68 | 34 | True |
| XT_C5A_ST10n10 | {'1': 1226, '0': 1075, '5': 75, '2': 16} | 73 | 1.84 / 2.95 | 20 | 0 | -2.45 / 0.48 | 67 | 34 | True |
| XT_C5A_ST10n14 | {'1': 1243, '0': 1097, '5': 82, '2': 17} | 71 | 1.68 / 2.84 | 22 | 0 | -2.54 / 0.55 | 74 | 34 | True |
| XT_C5A_KEL3 | {'1': 4234, '0': 4027, '5': 243, '2': 89} | 48 | 2.57 / 2.66 | 91 | 0 | -1.84 / 0.26 | 181 | 34 | True |
| XT_C5A_EMA5 | {'1': 1170, '0': 1050, '5': 89, '2': 26} | 85 | 1.97 / 2.42 | 18 | 0 | -1.65 / 0.52 | 76 | 34 | True |
| XT_C5A_TB7 | {'1': 576, '0': 546, '5': 70, '2': 21} | 34 | 2.26 / 2.41 | 1 | 0 | -1.84 / 0.70 | 73 | 34 | True |
| XT_C5B_ST | {'1': 4148, '0': 3873, '5': 288} | 45 | 2.26 / 3.66 | 83 | 1 | -2.34 / 0.25 | 224 | 34 | True |
| XT_C5B_HM | {'1': 3157, '0': 2878, '5': 276} | 60 | 2.26 / 3.56 | 61 | 0 | -2.25 / 0.32 | 218 | 34 | True |
| XT_C5B_ST10n7 | {'1': 1224, '0': 1085, '5': 88} | 75 | 1.82 / 3.44 | 18 | 0 | -2.98 / 0.57 | 83 | 34 | True |
| XT_C5B_ST10n10 | {'1': 1229, '0': 1077, '5': 86} | 74 | 1.89 / 3.50 | 20 | 0 | -2.71 / 0.48 | 80 | 34 | True |
| XT_C5B_ST10n14 | {'1': 1244, '0': 1099, '5': 96} | 71 | 1.72 / 3.37 | 22 | 0 | -2.81 / 0.54 | 87 | 34 | True |
| XT_C5B_KEL3 | {'1': 4246, '0': 4038, '5': 308, '2': 1} | 48 | 2.70 / 3.38 | 92 | 0 | -2.23 / 0.26 | 246 | 34 | True |
| XT_C5B_EMA5 | {'1': 1171, '0': 1052, '5': 111, '2': 1} | 85 | 1.99 / 3.02 | 18 | 0 | -1.95 / 0.53 | 97 | 34 | True |
| XT_C5B_TB7 | {'1': 581, '0': 548, '5': 84} | 34 | 2.31 / 2.91 | 1 | 0 | -2.05 / 0.71 | 92 | 34 | True |
| XT_C5C_ST | {'1': 4262, '0': 3961, '2': 81, '5': 5} | 45 | 2.21 / 0.72 | 76 | 243 | -0.87 / 0.26 | 162 | 34 | True |
| XT_C5C_HM | {'1': 3274, '0': 2969, '2': 63, '5': 5} | 60 | 2.21 / 0.87 | 53 | 247 | -0.94 / 0.31 | 177 | 34 | True |
| XT_C5C_ST10n7 | {'1': 1249, '0': 1129, '2': 18, '5': 1} | 75 | 1.77 / 1.33 | 17 | 58 | -1.94 / 0.58 | 66 | 34 | True |
| XT_C5C_ST10n10 | {'1': 1255, '0': 1120, '2': 16, '5': 1} | 73 | 1.85 / 1.38 | 19 | 44 | -1.67 / 0.48 | 64 | 34 | True |
| XT_C5C_ST10n14 | {'1': 1277, '0': 1143, '2': 17, '5': 2} | 71 | 1.66 / 1.13 | 19 | 53 | -1.68 / 0.54 | 70 | 34 | True |
| XT_C5C_KEL3 | {'1': 4365, '0': 4133, '2': 89, '5': 6} | 48 | 2.55 / 0.83 | 82 | 284 | -0.92 / 0.26 | 171 | 34 | True |
| XT_C5C_EMA5 | {'1': 1216, '0': 1090, '2': 26, '5': 3} | 85 | 1.97 / 0.84 | 17 | 61 | -0.84 / 0.53 | 74 | 34 | True |
| XT_C5C_TB7 | {'1': 622, '0': 569, '2': 21, '5': 1} | 34 | 2.10 / 0.72 | 1 | 7 | -0.94 / 0.70 | 72 | 34 | True |

## Weekend / Sunday-open gap risk (NQ, all Friday 16:55 -> Sunday 18:00 opens 2023-02..2026-10): n 1106, mean -3.7 pts, SD 98.8, 5th/95th pct -213.1/+104.8, min -405.0, max +415.2. A 10-lot book carries $200 per point: a 1-SD gap is $19,752, the worst gap $-81,000/83,050. Stops are market-stop orders: a Sunday gap through the 60-pt stop fills at the open (in the L2 replay at the actual book), not at the stop.

## Caveats
- Sequence uses the BASE entry set only: a rule that exits earlier (time stop, trail) does not create new entries; a rule that holds longer skips base entries that arrive while it is open (counted in `seq dropped`).
- Exit prices are direct L2 (stop-join / market / limit-at-level); the placebo uses the nominal 1-s path with the rule's mean friction (ranking only).
- 2023-04..2024-01 span: entries and exits replayed directly too (L2 on disk from 2023-02).
- Target fills assume a limit at the level fills on touch (identical in base and rule).
- Holdout looked once per prereg group (pre-holdout texts autopilot/DS3_TC_<G>_PREHOLD.md); books reusing T-ENTRY/T-B series have had earlier holdout looks.
