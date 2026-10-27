# DS3_EXITS_FINAL - exit structure on every book (D3XT, priority item 1)

Generated 2026-10-27T21:50:39Z. Research only; nothing is a live recommendation. 246 of 246 prereg'd exit cells scored (Track C 104 incl. TB7/ST10 siblings, R4 70, PB + OPP flips 72 ; preregs TC_G1..G5, shas in autopilot/DECISIONS.md), direct L2 basis, paired per trade on identical entries vs each book's own DS2 bracket (60/60, 1R, flat 16:55), exact per-book locks at 10 lots, price frame corrected (v1 outputs *_v1_INVALID* superseded).

## Verdict
**0 PASS, 0 CANDIDATE, 246 DEAD of 246 cells.** No exit rule is a PASS or CANDIDATE on any book, so there is no parameter spec to write and nothing to put into the DS3 container for all books at once; the live DS2 fixed bracket (60/60 flat 16:55) stays the best-supported exit on every book.

Best exit per book on the book's own entries (best = highest paired mean over all its cells; "verdict" is the V2 verdict of that cell; the best-of-N bias applies: N cells per book are shown in the next table):

* Best exit on ST10's own entries: XT_R4_PL_ST, paired +1.06 pts/trade [-0.29,+2.41] (MDE 1.93, n 6952), maxDD Delta +483,354, direct basis; holdout +0.63, 2023 span +0.03, 2x-cost paired +1.34, placebo 1.00; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse).
* Best exit on HM10's own entries: XT_R4_PL_HM, paired +0.20 pts/trade [-1.27,+1.67] (MDE 2.09, n 5162), maxDD Delta +47,410, direct basis; holdout +0.08, 2023 span +0.07, 2x-cost paired +0.33, placebo 0.97; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60%).
* Best exit on KB (TE7_kelt3m_n14_m1.0)'s own entries: XT_R4_TNONE_KEL3, paired +0.97 pts/trade [-3.40,+5.51] (MDE 6.36, n 7169), maxDD Delta -194,347, direct basis; holdout -0.06, 2023 span -0.19, 2x-cost paired -0.07, placebo 1.00; verdict DEAD (holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60%).
* Best exit on SM (TE6_st10m_n7_m3.0)'s own entries: XT_C4b_ST10n7, paired +2.25 pts/trade [+0.51,+3.99] (MDE 2.48, n 1847), maxDD Delta -29,929, direct basis; holdout +3.25, 2023 span +0.13, 2x-cost paired +2.16, placebo 1.00; verdict DEAD (neighbours_agree,year_share>60%).
* Best exit on EM (TE7_emax5m_f30_s50, disabled)'s own entries: XT_C4b_EMA5, paired +1.40 pts/trade [-0.29,+3.09] (MDE 2.44, n 1800), maxDD Delta +40,777, direct basis; holdout +2.07, 2023 span +1.14, 2x-cost paired +1.36, placebo 1.00; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60%).
* Best exit on PB_ST10_SWZ_T3's own entries: XT_OPP_SM_PBS, paired +1.61 pts/trade [-3.07,+6.52] (MDE 6.86, n 4978), maxDD Delta -13,850, direct basis; holdout -2.70, 2023 span -3.23, 2x-cost paired +0.73, placebo 1.00; verdict DEAD (holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%).
* Best exit on PB3B_R5_P1's own entries: XT_R4_PL_PB3, paired +0.98 pts/trade [-0.40,+2.35] (MDE 1.96, n 6392), maxDD Delta -298,182, direct basis; holdout +0.67, 2023 span -2.37, 2x-cost paired +1.23, placebo 0.99; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0).

## One row per book: best cell, TH-loss control, fixed-bracket control
| book | n entries (WF pairs) | best cell | paired pts/trade [CI] | maxDD Delta $ | verdict | LIVE TH-loss control (G1_TH_LIVE_ST 15/3/30, live-join): paired [CI] | cells > 0 / cells scored | cells with CI excluding 0 above |
|---|---|---|---|---|---|---|---|---|
| ST10 | 6952 | XT_R4_PL_ST | +1.06 [-0.29,+2.41] | +483,354 | DEAD | -0.89 [-1.79,+0.01] (MDE 1.27) | 4/30 | 0 |
| HM10 | 5162 | XT_R4_PL_HM | +0.20 [-1.27,+1.67] | +47,410 | DEAD | -1.20 [-2.29,-0.14] (MDE 1.54) | 2/30 | 0 |
| KB (TE7_kelt3m_n14_m1.0) | 7169 | XT_R4_TNONE_KEL3 | +0.97 [-3.40,+5.51] | -194,347 | DEAD | -0.97 [-1.82,-0.13] (MDE 1.23) | 8/29 | 0 |
| SM (TE6_st10m_n7_m3.0) | 1847 | XT_C4b_ST10n7 | +2.25 [+0.51,+3.99] | -29,929 | DEAD | -1.02 [-2.77,+0.50] (MDE 2.34) | 5/29 | 1 |
| EM (TE7_emax5m_f30_s50, disabled) | 1800 | XT_C4b_EMA5 | +1.40 [-0.29,+3.09] | +40,777 | DEAD | -1.36 [-3.13,+0.30] (MDE 2.45) | 5/29 | 0 |
| PB_ST10_SWZ_T3 | 4978 | XT_OPP_SM_PBS | +1.61 [-3.07,+6.52] | -13,850 | DEAD | not scored (TH engine not run on PB entries) | 15/30 | 0 |
| PB3B_R5_P1 | 6392 | XT_R4_PL_PB3 | +0.98 [-0.40,+2.35] | -298,182 | DEAD | not scored (TH engine not run on PB entries) | 5/30 | 0 |

TH-loss control = the live Trade-Health loss rule (min loss 15 pts, 3 of 3 conditions, 30 s windows) from autopilot/DS3_TH_G1.md addendum (live stop-join profile), all-span paired vs the book's base bracket; the fixed bracket itself is the zero row of every table.

## Per-book consistency of each rule (paired pts/trade; * = CI excludes 0)
| rule | ST10 | HM10 | KB | SM | EM | PB_ST10_SWZ_T3 | PB3B_R5_P1 | books > 0 | books CI>0 |
|---|---|---|---|---|---|---|---|---|---|
| C1_120 | -3.91 | -1.96 | -3.19 | +0.36 | -0.52 | +1.45 | -1.73 | 2 | 0 |
| C1_60 | -2.34 | -1.71 | -2.75 | -0.12 | -0.36 | +0.88 | -0.19 | 1 | 0 |
| C1_90 | -3.45 | -1.93 | -3.53 | +0.63 | -0.07 | +0.95 | -1.80 | 2 | 0 |
| C2_120 | -0.71 | -0.56 | -1.00 | -0.94 | -0.16 | -0.54 | -0.60 | 0 | 0 |
| C2_30 | -1.36 | -1.69 | -0.83 | -2.59 | -2.11 | -0.76 | -1.98 | 0 | 0 |
| C2_60 | -1.13 | -0.64 | -1.23 | -2.61 | -1.61 | -0.59 | -1.42 | 0 | 0 |
| C3 | -1.62 | -2.27 | -1.78 | -2.11 | -1.69 | -1.12 | -1.99 | 0 | 0 |
| C4a | -0.33 | -0.01 | -0.39 | -0.45 | -0.79 | -0.37 | -1.03 | 0 | 0 |
| C4b | +0.44 | -0.40 | +0.49 | +2.25* | +1.40 | +0.60 | +0.33 | 6 | 1 |
| C4c | +0.10 | -0.43 | -0.05 | -1.76 | -0.63 | +0.10 | +0.08 | 3 | 0 |
| C5A | -0.07 | -0.09 | -0.05 | -0.05 | -0.06 | -0.08 | -0.07 | 0 | 0 |
| C5B | -0.04 | -0.04 | -0.15 | -0.06 | -0.12 | -0.25 | -0.20 | 0 | 0 |
| C5C | +0.11 | +0.03 | +0.02 | -0.08 | +0.08 | +0.07 | -0.03 | 5 | 0 |
| OPP_EM | -3.39 | -1.61 | -3.22 | +0.04 | - | -0.70 | -2.47 | 1 | 0 |
| OPP_KB | -3.47 | -3.15 | - | -4.79 | -5.11 | -1.59 | -3.75 | 0 | 0 |
| OPP_SM | -0.82 | -0.45 | -1.54 | - | +1.34 | +1.61 | -0.77 | 2 | 0 |
| R4_CH2 | -2.13 | -2.86 | -3.06 | -4.81 | -4.83 | -2.38 | -3.47 | 0 | 0 |
| R4_CH25 | -2.70 | -3.24 | -3.53 | -4.14 | -4.43 | +0.33 | -3.27 | 1 | 0 |
| R4_CH3 | -3.29 | -3.56 | -3.75 | -3.56 | -3.97 | +0.73 | -3.85 | 1 | 0 |
| R4_MM | -0.09 | -1.20 | -0.02 | -1.60 | -0.00 | -0.21 | -0.39 | 0 | 0 |
| R4_ONH | -1.28 | -1.53 | +0.54 | -2.01 | -0.31 | -0.99 | +0.34 | 2 | 0 |
| R4_PL | +1.06 | +0.20 | +0.85 | -0.73 | -0.53 | +1.12 | +0.98 | 5 | 0 |
| R4_PSAR | -2.45 | -2.49 | -2.60 | -3.27 | -3.10 | -0.03 | -3.27 | 0 | 0 |
| R4_STB | -3.33 | -3.88 | -2.09 | -1.48 | -1.75 | +0.64 | -2.56 | 1 | 0 |
| R4_T15 | -0.20 | -0.27 | +0.18 | -1.25 | -1.18 | +0.20 | -0.21 | 2 | 0 |
| R4_T20 | -0.05 | -0.81 | +0.24 | -0.41 | -1.56 | +0.20 | +0.42 | 3 | 0 |
| R4_TD120 | -1.37 | -1.34 | +0.07 | +0.98 | +1.04 | -0.04 | -0.07 | 3 | 0 |
| R4_TD30 | -1.61 | -1.97 | -0.90 | -1.13 | -1.55 | -1.18 | -1.62 | 0 | 0 |
| R4_TD60 | -1.85 | -1.60 | -0.74 | -1.76 | -1.76 | +0.33 | -1.17 | 1 | 0 |
| R4_TNONE | -0.94 | -1.23 | +0.97 | -1.37 | +0.02 | +0.88 | -0.19 | 3 | 0 |

## Rule coverage (user list -> prereg'd cells)
* Chandelier k 2/2.5/3 = R4_CH2/CH25/CH3; Supertrend-band trail = R4_STB; swing-structure trail = C3; parabolic SAR = R4_PSAR.
* Opposite-flip: own book = C1_60/90/120; faster book = OPP_KB, OPP_SM, OPP_EM (EM disabled live) on ST, HM, PBS, PB3 and the other fast books.
* Time-decay tightening = R4_TD30/60/120; profit-lock +1.5R -> +0.5R, +2R -> trail 20 = R4_PL; time stop = C2.
* Overnight hold-through = C5A/B/C and R4_ONH (>= +1R at 16:55); trail-only (no target) = R4_TNONE and the trail rules; 1.5R / 2R / measured-move / next-level targets = R4_T15, R4_T20, R4_MM, C4a/b/c.

## All cells (sorted by paired mean)
| cell | n | paired [CI] | MDE | holdout | 2023 span | maxDD Delta | d wk $ (WF) | placebo | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|
| XT_C1_60_TB7 | 895 | +3.28 [-3.41,+10.46] | 9.99 | +0.55 | +3.98 | -597,118 | +7,728 | 0.92 | DEAD | paired_CI_excludes0&maxDD_not_worse,placebo<0.95,year_share>60% |
| XT_C1_90_TB7 | 895 | +3.11 [-4.54,+11.36] | 11.37 | +0.84 | +8.89 | -481,232 | +7,416 | 0.63 | DEAD | placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4b_ST10n10 | 1833 | +2.57 [+0.78,+4.35] | 2.54 | +3.69 | -0.49 | -92,075 | +4,229 | 1.00 | DEAD | neighbours_agree,SPAN2<=0 |
| XT_C4b_ST10n7 | 1847 | +2.25 [+0.51,+3.99] | 2.48 | +3.25 | +0.13 | -29,929 | +4,083 | 1.00 | DEAD | neighbours_agree,year_share>60% |
| XT_C4b_ST10n14 | 1868 | +1.69 [-0.04,+3.44] | 2.51 | +2.72 | -1.63 | +12,960 | +4,859 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_OPP_SM_PBS | 4978 | +1.61 [-3.07,+6.52] | 6.86 | -2.70 | -3.23 | -13,850 | +1,431 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C4b_TB7 | 895 | +1.56 [-0.26,+3.39] | 2.59 | +2.58 | +2.52 | -407,386 | +1,971 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C1_120_PBS | 4978 | +1.45 [-4.23,+7.31] | 8.11 | -3.77 | +1.75 | +8,326 | -863 | 0.80 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4b_EMA5 | 1800 | +1.40 [-0.29,+3.09] | 2.44 | +2.07 | +1.14 | +40,777 | +560 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_OPP_SM_EMA5 | 1800 | +1.34 [-3.98,+6.92] | 7.78 | +4.51 | -0.05 | +160,705 | +4,608 | 0.97 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C1_120_TB7 | 895 | +1.17 [-7.17,+9.99] | 12.26 | -0.36 | +9.10 | -385,880 | +7,495 | 0.49 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_PL_PBS | 4978 | +1.12 [-0.44,+2.65] | 2.20 | +0.54 | -0.36 | +61,260 | -2,726 | 0.86 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_R4_PL_ST | 6952 | +1.06 [-0.29,+2.41] | 1.93 | +0.63 | +0.03 | +483,354 | -4,390 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |
| XT_R4_TD120_EMA5 | 1800 | +1.04 [-3.27,+5.34] | 6.15 | +2.43 | -4.18 | +303,429 | +4,072 | 0.95 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_PL_PB3 | 6392 | +0.98 [-0.40,+2.35] | 1.96 | +0.67 | -2.37 | -298,182 | +1,373 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_R4_TD120_ST10n7 | 1847 | +0.98 [-3.52,+5.59] | 6.51 | +2.07 | -2.56 | +361,000 | +5,048 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_TNONE_KEL3 | 7169 | +0.97 [-3.40,+5.51] | 6.36 | -0.06 | -0.19 | -194,347 | +2,199 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_PBS | 4978 | +0.95 [-4.02,+6.11] | 7.20 | -4.29 | +1.24 | -143,234 | +2,265 | 0.70 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4c_TB7 | 895 | +0.93 [-0.77,+2.67] | 2.47 | +2.11 | -0.51 | -124,545 | +1,259 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C1_60_PBS | 4978 | +0.88 [-3.29,+5.25] | 6.08 | -2.03 | -0.08 | -83,581 | -333 | 0.76 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_TNONE_PBS | 4978 | +0.88 [-3.29,+5.25] | 6.08 | -2.03 | -0.08 | -83,581 | -333 | 0.76 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_PL_KEL3 | 7169 | +0.85 [-0.38,+2.08] | 1.73 | +0.86 | -0.76 | -206,667 | +4,960 | 0.95 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_R4_CH3_PBS | 4978 | +0.73 [-2.44,+4.18] | 4.72 | -2.49 | -4.00 | -118,306 | +4,991 | 0.86 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_PBS | 4978 | +0.64 [-2.95,+4.51] | 5.32 | -2.77 | -3.50 | -169,113 | +4,470 | 0.79 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n7 | 1847 | +0.63 [-4.70,+6.29] | 7.96 | +1.60 | +1.60 | +90,558 | +6,617 | 0.95 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4b_PBS | 4978 | +0.60 [-0.37,+1.59] | 1.39 | +0.27 | -0.74 | +19,146 | +390 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_R4_ONH_KEL3 | 7169 | +0.54 [-3.76,+5.01] | 6.30 | -0.66 | -0.76 | -270,457 | +4,187 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4b_KEL3 | 7169 | +0.49 [-0.31,+1.28] | 1.14 | +0.75 | -0.23 | +61,836 | +1,920 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C5C_TB7 | 895 | +0.46 [-0.36,+1.30] | 1.17 | +0.45 | +2.57 | -149,256 | +487 | 0.97 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |
| XT_C4b_ST | 6952 | +0.44 [-0.36,+1.28] | 1.17 | +0.21 | -0.60 | +69,951 | -219 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_T20_PB3 | 6392 | +0.42 [-1.03,+1.89] | 2.09 | -0.15 | -2.81 | -176,176 | +913 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C1_120_ST10n7 | 1847 | +0.36 [-5.35,+6.36] | 8.42 | +0.85 | +1.64 | +44,850 | +8,682 | 0.90 | DEAD | paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_R4_ONH_PB3 | 6392 | +0.34 [-4.47,+5.32] | 6.94 | -1.17 | -1.70 | -361,319 | +8,701 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_PBS | 4978 | +0.33 [-2.57,+3.56] | 4.36 | -2.62 | -3.76 | -182,008 | -3,193 | 0.71 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4b_PB3 | 6392 | +0.33 [-0.48,+1.14] | 1.16 | -0.11 | -1.25 | -191,158 | -1,548 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_TD60_PBS | 4978 | +0.33 [-2.64,+3.48] | 4.31 | -2.52 | -1.20 | -265,696 | -583 | 0.57 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_KEL3 | 7169 | +0.24 [-1.07,+1.58] | 1.89 | +0.13 | -1.00 | -17,427 | +4,190 | 0.96 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_PBS | 4978 | +0.20 [-1.52,+1.96] | 2.49 | -0.80 | -1.33 | +103,774 | -4,811 | 0.84 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PL_HM | 5162 | +0.20 [-1.27,+1.67] | 2.09 | +0.08 | +0.07 | +47,410 | +5,791 | 0.97 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_T15_PBS | 4978 | +0.20 [-1.01,+1.37] | 1.67 | -0.08 | -0.74 | +232,955 | -1,835 | 0.90 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_KEL3 | 7169 | +0.18 [-0.79,+1.12] | 1.36 | -0.44 | -0.19 | -362,436 | +3,533 | 0.97 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST | 6952 | +0.11 [-0.08,+0.30] | 0.27 | +0.05 | +0.65 | -48,055 | +19 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4c_PBS | 4978 | +0.10 [-1.00,+1.22] | 1.59 | -0.07 | -1.34 | +48,836 | -2,898 | 0.88 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C4c_ST | 6952 | +0.10 [-0.80,+1.02] | 1.29 | +0.04 | -0.23 | +95,544 | -430 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C5C_EMA5 | 1800 | +0.08 [-0.37,+0.53] | 0.65 | +0.00 | +0.18 | -31,354 | +330 | 0.96 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4c_PB3 | 6392 | +0.08 [-0.81,+0.96] | 1.25 | -0.43 | -1.27 | -187,266 | -1,689 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_TD120_KEL3 | 7169 | +0.07 [-3.35,+3.57] | 4.91 | +0.20 | -3.80 | -48,436 | +5,995 | 0.90 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_PBS | 4978 | +0.07 [-0.17,+0.30] | 0.34 | +0.17 | +0.74 | -104,661 | -112 | 0.88 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_OPP_EM_ST10n7 | 1847 | +0.04 [-5.73,+6.25] | 8.55 | +0.41 | +4.15 | +275,820 | +1,495 | 0.89 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5C_HM | 5162 | +0.03 [-0.22,+0.29] | 0.36 | +0.13 | +1.51 | -82,825 | +1,168 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_KEL3 | 7169 | +0.02 [-0.17,+0.22] | 0.28 | +0.06 | +0.42 | -137,708 | -1,062 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_EMA5 | 1800 | +0.02 [-5.42,+5.71] | 7.90 | +0.77 | +4.70 | +200,843 | +4,180 | 0.82 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5B_TB7 | 895 | +0.02 [-0.39,+0.45] | 0.60 | -0.03 | -0.43 | +11,020 | +98 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_EMA5 | 1800 | -0.00 [-1.81,+1.74] | 2.54 | -0.24 | +0.67 | -3,632 | +2,577 | 0.98 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4a_HM | 5162 | -0.01 [-0.96,+0.94] | 1.36 | +0.35 | -0.64 | +171,487 | +1,713 | 0.99 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_KEL3 | 7169 | -0.02 [-1.04,+1.00] | 1.45 | +0.01 | -0.77 | -157,544 | +3,950 | 0.99 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_PB3 | 6392 | -0.03 [-0.24,+0.18] | 0.30 | +0.08 | +0.75 | +61,554 | -2,535 | 1.00 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_PBS | 4978 | -0.03 [-2.43,+2.52] | 3.53 | -1.84 | -3.26 | -199,977 | -7,174 | 0.48 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_HM | 5162 | -0.04 [-0.15,+0.08] | 0.17 | -0.04 | -0.30 | +30,154 | -679 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD120_PBS | 4978 | -0.04 [-3.66,+3.79] | 5.28 | -1.91 | -5.09 | -169,602 | -1,689 | 0.33 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST | 6952 | -0.04 [-0.12,+0.04] | 0.11 | -0.07 | -0.24 | +24,545 | -737 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n14 | 1868 | -0.04 [-0.41,+0.33] | 0.53 | -0.21 | -0.97 | -16,357 | -289 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n7 | 1847 | -0.05 [-0.11,+0.01] | 0.09 | -0.04 | -0.42 | +15,984 | +19 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_ST | 6952 | -0.05 [-1.53,+1.44] | 2.10 | -0.26 | -0.81 | +203,703 | -1,111 | 0.97 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_KEL3 | 7169 | -0.05 [-0.84,+0.73] | 1.13 | +0.58 | -0.58 | -241,470 | +3,022 | 0.99 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_KEL3 | 7169 | -0.05 [-0.11,-0.00] | 0.08 | -0.03 | -0.26 | -8,998 | -419 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n10 | 1833 | -0.06 [-0.11,-0.01] | 0.08 | -0.05 | -0.32 | -650 | -176 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n7 | 1847 | -0.06 [-0.23,+0.10] | 0.23 | -0.07 | -0.58 | +32,731 | -99 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_EMA5 | 1800 | -0.06 [-0.14,+0.04] | 0.13 | -0.08 | -0.25 | +21,842 | -117 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD120_PB3 | 6392 | -0.07 [-4.00,+4.22] | 5.88 | -0.71 | -4.12 | -249,950 | +4,453 | 0.98 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST | 6952 | -0.07 [-0.11,-0.03] | 0.05 | -0.07 | -0.18 | +22,728 | -658 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n14 | 1868 | -0.07 [-0.12,-0.03] | 0.07 | -0.06 | -0.33 | +2,890 | -131 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n10 | 1833 | -0.07 [-0.24,+0.08] | 0.23 | -0.08 | -0.46 | -650 | -303 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_EMA5 | 1800 | -0.07 [-5.56,+5.53] | 7.83 | +2.84 | +1.67 | +269,508 | +2,845 | 0.85 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5A_PB3 | 6392 | -0.07 [-0.12,-0.03] | 0.07 | -0.09 | -0.23 | -40,095 | +288 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_PBS | 4978 | -0.08 [-0.12,-0.04] | 0.06 | -0.05 | -0.22 | -28,350 | +594 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n7 | 1847 | -0.08 [-0.46,+0.30] | 0.54 | +0.05 | -1.17 | +75,225 | +107 | 1.00 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_ST | 6952 | -0.09 [-1.08,+0.93] | 1.44 | +0.10 | +0.18 | +90,351 | -3,107 | 1.00 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5A_HM | 5162 | -0.09 [-0.13,-0.05] | 0.06 | -0.05 | -0.29 | +38,235 | -848 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n7 | 1847 | -0.12 [-4.82,+4.80] | 6.86 | +1.38 | +0.91 | +7,252 | +5,267 | 0.99 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C5B_EMA5 | 1800 | -0.12 [-0.26,+0.02] | 0.20 | -0.16 | -0.55 | +21,573 | -256 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_TB7 | 895 | -0.13 [-0.27,-0.01] | 0.19 | -0.05 | -0.54 | +38,380 | -57 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n14 | 1868 | -0.13 [-0.27,-0.03] | 0.18 | -0.18 | -0.55 | +20,279 | -182 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_KEL3 | 7169 | -0.15 [-0.29,-0.03] | 0.19 | -0.10 | -0.36 | +61,491 | -1,216 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_EMA5 | 1800 | -0.16 [-1.67,+1.32] | 2.16 | -0.60 | -1.08 | -26,721 | -992 | 0.98 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n10 | 1833 | -0.18 [-0.54,+0.19] | 0.53 | -0.07 | -0.83 | -18,538 | -222 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_ST10n10 | 1833 | -0.18 [-6.12,+5.98] | 8.64 | +0.39 | -0.11 | +66,013 | +9,299 | 0.92 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_PB3 | 6392 | -0.19 [-4.06,+4.07] | 5.81 | -3.44 | -2.08 | -129,099 | +2,858 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_PB3 | 6392 | -0.19 [-4.06,+4.07] | 5.81 | -3.44 | -2.08 | -129,099 | +2,858 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_PB3 | 6392 | -0.20 [-0.38,-0.05] | 0.24 | -0.29 | -0.27 | -108,778 | -403 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_ST | 6952 | -0.20 [-1.23,+0.86] | 1.50 | -0.71 | +0.62 | +392,830 | -5,253 | 0.98 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_MM_PBS | 4978 | -0.21 [-0.84,+0.43] | 0.89 | -0.40 | +0.62 | +17,811 | -3,987 | 0.64 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_T15_PB3 | 6392 | -0.21 [-1.25,+0.82] | 1.48 | -0.24 | -1.82 | +16,009 | +1,066 | 0.97 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_PBS | 4978 | -0.25 [-0.47,-0.06] | 0.30 | -0.36 | -0.26 | -23,660 | -304 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_HM | 5162 | -0.27 [-1.42,+0.88] | 1.66 | -1.02 | +0.45 | +7,064 | +4,714 | 0.85 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_ONH_EMA5 | 1800 | -0.31 [-5.77,+5.34] | 7.89 | +0.47 | +4.60 | +88,197 | +8,705 | 0.93 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_C4a_ST | 6952 | -0.33 [-1.19,+0.49] | 1.21 | -0.04 | -0.96 | -36,616 | +67 | 0.96 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_EMA5 | 1800 | -0.36 [-5.12,+4.47] | 6.90 | +1.15 | +2.97 | +181,590 | +5,359 | 0.93 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_C4a_PBS | 4978 | -0.37 [-1.43,+0.71] | 1.52 | -0.00 | +0.52 | +150,641 | -1,355 | 0.38 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_MM_PB3 | 6392 | -0.39 [-1.34,+0.56] | 1.36 | -0.62 | -0.74 | -107,055 | -1,776 | 0.98 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_KEL3 | 7169 | -0.39 [-1.21,+0.41] | 1.16 | -0.03 | -0.96 | +383,709 | -4,935 | 0.88 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4b_HM | 5162 | -0.40 [-1.33,+0.52] | 1.32 | -0.49 | -0.98 | -47,040 | +1,695 | 0.89 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_ST10n7 | 1847 | -0.41 [-3.16,+2.27] | 3.90 | +1.14 | +0.77 | +323,183 | -2,402 | 0.96 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_HM | 5162 | -0.43 [-1.32,+0.45] | 1.26 | -0.27 | -0.02 | +219,346 | -885 | 0.93 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_SM_HM | 5162 | -0.45 [-5.14,+4.40] | 6.84 | -1.95 | -1.56 | -295,366 | +14,470 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n7 | 1847 | -0.45 [-2.35,+1.40] | 2.67 | +1.11 | -2.18 | +385,152 | -3,376 | 0.98 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n14 | 1868 | -0.50 [-2.41,+1.39] | 2.68 | +0.79 | -3.36 | +430,666 | -1,588 | 0.93 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_EMA5 | 1800 | -0.52 [-6.29,+5.52] | 8.33 | +1.79 | +1.15 | +343,305 | +3,332 | 0.77 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_PL_EMA5 | 1800 | -0.53 [-2.87,+1.92] | 3.44 | +0.37 | +0.99 | +144,110 | +2,182 | 0.62 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_120_PBS | 4978 | -0.54 [-1.34,+0.24] | 1.13 | -1.11 | -1.94 | -4,529 | -5,422 | 0.56 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_HM | 5162 | -0.56 [-1.33,+0.19] | 1.10 | -0.44 | -0.33 | +798,770 | -4,373 | 0.96 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_PBS | 4978 | -0.59 [-1.64,+0.43] | 1.46 | -1.55 | -2.69 | -246,993 | -2,641 | 0.63 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_PB3 | 6392 | -0.60 [-1.24,+0.04] | 0.91 | -0.82 | -1.57 | +307,169 | -9,424 | 0.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_EMA5 | 1800 | -0.63 [-2.08,+0.79] | 2.08 | -1.41 | -0.44 | +137,904 | -1,033 | 0.81 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_HM | 5162 | -0.64 [-1.68,+0.36] | 1.44 | -0.44 | -0.19 | +830,085 | -5,175 | 0.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n10 | 1833 | -0.64 [-2.50,+1.20] | 2.65 | +1.29 | -2.76 | +250,761 | -3,271 | 0.84 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_EM_PBS | 4978 | -0.70 [-5.39,+4.21] | 6.79 | -5.40 | -3.80 | +3,775 | -3,281 | 0.37 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_ST | 6952 | -0.71 [-1.31,-0.13] | 0.85 | -0.45 | -1.74 | +902,292 | -9,258 | 0.92 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PL_ST10n7 | 1847 | -0.73 [-3.22,+1.74] | 3.56 | -0.13 | +0.93 | +149,916 | -1,320 | 0.88 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD60_KEL3 | 7169 | -0.74 [-3.34,+1.98] | 3.83 | -1.01 | -3.10 | +456,822 | -2,800 | 0.40 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_TB7 | 895 | -0.75 [-3.08,+1.49] | 3.23 | +0.27 | +1.20 | +35,040 | -605 | 0.63 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_PBS | 4978 | -0.76 [-2.01,+0.46] | 1.76 | -1.09 | -1.93 | -208,865 | -3,809 | 0.62 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_SM_PB3 | 6392 | -0.77 [-5.62,+4.34] | 7.17 | -3.17 | -3.70 | -43,630 | +5,417 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_EMA5 | 1800 | -0.79 [-2.69,+1.16] | 2.75 | -0.07 | -2.36 | +156,798 | -2,825 | 0.47 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_TB7 | 895 | -0.81 [-2.82,+1.21] | 2.87 | -1.64 | -0.16 | +97,170 | -56 | 0.55 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_HM | 5162 | -0.81 [-2.45,+0.86] | 2.36 | -0.33 | +0.02 | +429,327 | +3,206 | 0.71 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_OPP_SM_ST | 6952 | -0.82 [-5.80,+4.49] | 7.36 | -2.62 | -2.62 | +495,024 | -2,587 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_KEL3 | 7169 | -0.83 [-1.82,+0.16] | 1.42 | -0.54 | +0.60 | +2,604,299 | -21,042 | 0.63 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n10 | 1833 | -0.83 [-6.36,+4.86] | 7.98 | +0.70 | +0.14 | +79,047 | +5,210 | 0.87 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD30_KEL3 | 7169 | -0.90 [-2.96,+1.12] | 2.92 | -0.85 | -0.74 | +956,294 | -7,333 | 0.33 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n10 | 1833 | -0.90 [-5.54,+4.00] | 6.87 | +0.90 | -0.28 | +29,823 | +3,601 | 0.95 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n7 | 1847 | -0.94 [-2.43,+0.51] | 2.10 | +0.12 | -0.14 | -4,589 | -2,183 | 0.97 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_ST | 6952 | -0.94 [-5.38,+3.82] | 6.66 | -2.01 | -1.80 | +652,583 | -8,141 | 0.80 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_ONH_PBS | 4978 | -0.99 [-5.58,+3.73] | 6.70 | -4.42 | -1.65 | -95,302 | +1,130 | 0.64 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_KEL3 | 7169 | -1.00 [-1.60,-0.39] | 0.87 | -0.78 | -0.38 | +1,503,544 | -10,213 | 0.50 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_TB7 | 895 | -1.02 [-2.66,+0.64] | 2.37 | -1.00 | +1.25 | +76,766 | -1,134 | 0.51 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4a_PB3 | 6392 | -1.03 [-1.90,-0.14] | 1.25 | -0.95 | -1.16 | +27,819 | -6,955 | 0.33 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n10 | 1833 | -1.07 [-2.52,+0.39] | 2.09 | -0.14 | -2.08 | -24,792 | -3,429 | 0.88 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_ST10n14 | 1868 | -1.10 [-6.92,+4.76] | 8.37 | -2.54 | +0.59 | +207,288 | +6,865 | 0.86 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C3_PBS | 4978 | -1.12 [-2.33,+0.13] | 1.76 | -2.16 | -0.83 | +198,668 | -9,697 | 0.12 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_ST10n7 | 1847 | -1.13 [-4.35,+2.11] | 4.62 | +0.74 | -2.00 | +123,640 | -1,024 | 0.95 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST | 6952 | -1.13 [-1.90,-0.36] | 1.11 | -0.66 | -0.90 | +1,411,746 | -14,479 | 0.69 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_PB3 | 6392 | -1.17 [-4.13,+1.97] | 4.39 | -3.02 | -3.04 | -166,939 | -348 | 0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_PBS | 4978 | -1.18 [-3.48,+1.24] | 3.37 | -3.17 | -1.49 | +115,763 | -9,855 | 0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_EMA5 | 1800 | -1.18 [-3.13,+0.84] | 2.82 | -0.32 | +0.29 | +231,649 | -1,666 | 0.60 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_MM_HM | 5162 | -1.20 [-2.27,-0.14] | 1.51 | -1.20 | +0.76 | +119,743 | -901 | 0.13 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n14 | 1868 | -1.21 [-2.65,+0.18] | 2.01 | -0.71 | -1.89 | -9,489 | -4,994 | 0.91 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_HM | 5162 | -1.23 [-5.90,+3.61] | 6.84 | -0.46 | +0.05 | +158,980 | +11,160 | 0.77 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_60_KEL3 | 7169 | -1.23 [-2.03,-0.41] | 1.14 | -1.19 | +0.39 | +2,133,467 | -16,910 | 0.34 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_T15_ST10n7 | 1847 | -1.25 [-3.34,+0.72] | 2.88 | +0.12 | +1.03 | +68,818 | -1,011 | 0.71 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n10 | 1833 | -1.26 [-2.82,+0.32] | 2.25 | -2.67 | -0.94 | +140,078 | -3,369 | 0.63 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_ONH_ST | 6952 | -1.28 [-5.72,+3.46] | 6.62 | -2.51 | -2.25 | +73,901 | +3,712 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD120_HM | 5162 | -1.34 [-4.89,+2.35] | 5.16 | +0.12 | -3.17 | -14,115 | +15,853 | 0.53 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_ST | 6952 | -1.36 [-2.36,-0.39] | 1.41 | -0.77 | -1.20 | +2,402,198 | -20,575 | 0.46 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_ST10n7 | 1847 | -1.37 [-6.87,+4.25] | 8.09 | +0.12 | +5.12 | +92,986 | +4,204 | 0.72 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD120_ST | 6952 | -1.37 [-4.92,+2.34] | 5.18 | -0.98 | -6.09 | +255,782 | +2,800 | 0.42 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_PB3 | 6392 | -1.42 [-2.26,-0.58] | 1.19 | -1.89 | -0.43 | +813,686 | -15,196 | 0.65 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_TB7 | 895 | -1.43 [-2.56,-0.26] | 1.65 | -0.53 | +1.54 | +134,442 | -1,579 | 0.24 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_STB_ST10n7 | 1847 | -1.48 [-5.70,+2.97] | 6.17 | -2.66 | +0.23 | +196,247 | +681 | 0.76 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_ONH_HM | 5162 | -1.53 [-6.22,+3.36] | 6.84 | -1.02 | -0.49 | -221,334 | +15,030 | 0.95 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_SM_KEL3 | 7169 | -1.54 [-5.91,+3.10] | 6.46 | -3.31 | -3.62 | -256,903 | +7,279 | 0.96 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_EMA5 | 1800 | -1.55 [-4.53,+1.49] | 4.33 | -0.00 | -1.38 | +279,051 | -2,723 | 0.54 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_EMA5 | 1800 | -1.56 [-4.21,+1.19] | 3.81 | -0.15 | +2.03 | +301,346 | -1,524 | 0.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_OPP_KB_PBS | 4978 | -1.59 [-4.36,+1.48] | 4.20 | -5.13 | -3.72 | -155,143 | -9,525 | 0.93 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_ST10n7 | 1847 | -1.60 [-3.66,+0.42] | 2.93 | -2.49 | +1.06 | +265,107 | -1,453 | 0.62 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD60_HM | 5162 | -1.60 [-4.39,+1.24] | 4.08 | -1.60 | -1.21 | +36,665 | +13,450 | 0.45 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_EMA5 | 1800 | -1.61 [-3.53,+0.27] | 2.72 | -2.04 | -0.73 | +238,473 | -4,473 | 0.71 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_EM_HM | 5162 | -1.61 [-6.48,+3.49] | 7.04 | -2.81 | -0.21 | -319,645 | +13,041 | 0.81 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_ST | 6952 | -1.61 [-3.74,+0.68] | 3.16 | -1.21 | -1.23 | +447,219 | -7,215 | 0.15 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST | 6952 | -1.62 [-2.83,-0.35] | 1.76 | -2.04 | -1.42 | +184,639 | -2,083 | 0.37 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_PB3 | 6392 | -1.62 [-3.92,+0.81] | 3.37 | -2.65 | -0.73 | +220,617 | -8,416 | 0.32 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_EMA5 | 1800 | -1.69 [-3.51,+0.19] | 2.66 | -1.84 | +0.30 | +122,883 | +1,167 | 0.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_HM | 5162 | -1.69 [-2.90,-0.48] | 1.74 | -1.78 | -0.25 | +1,983,029 | -13,374 | 0.57 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_HM | 5162 | -1.71 [-5.09,+1.86] | 5.00 | -2.97 | -1.72 | +64,019 | +6,717 | 0.98 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_PB3 | 6392 | -1.73 [-7.29,+4.24] | 8.29 | -6.08 | -1.94 | -6,305 | +3,200 | 0.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_EMA5 | 1800 | -1.75 [-5.07,+1.66] | 4.77 | -1.39 | -1.21 | +107,473 | +1,498 | 0.45 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n7 | 1847 | -1.76 [-3.28,-0.30] | 2.14 | -2.05 | +0.69 | +225,051 | -3,966 | 0.51 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD60_EMA5 | 1800 | -1.76 [-5.26,+1.79] | 5.04 | -1.23 | -3.27 | +341,022 | -507 | 0.33 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_ST10n7 | 1847 | -1.76 [-5.40,+1.86] | 5.22 | -1.52 | -2.79 | +200,805 | -1,619 | 0.70 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n14 | 1868 | -1.77 [-3.32,-0.20] | 2.24 | -2.77 | -1.83 | +166,653 | -4,343 | 0.31 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_KEL3 | 7169 | -1.78 [-2.84,-0.68] | 1.54 | -2.02 | -2.15 | +209,092 | -2,677 | 0.05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_PB3 | 6392 | -1.80 [-6.25,+2.88] | 6.59 | -5.84 | -1.90 | -8,771 | +5,111 | 0.95 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_ST | 6952 | -1.85 [-4.57,+1.10] | 4.04 | -2.56 | -3.46 | +217,579 | +46 | 0.14 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_HM | 5162 | -1.93 [-6.04,+2.27] | 5.95 | -3.74 | -1.43 | -3,875 | +5,169 | 0.92 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_HM | 5162 | -1.96 [-6.46,+2.66] | 6.53 | -4.37 | -1.08 | +61,737 | +1,483 | 0.96 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_HM | 5162 | -1.97 [-4.13,+0.27] | 3.15 | -1.05 | +0.29 | +226,659 | +3,924 | 0.24 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_PB3 | 6392 | -1.98 [-3.03,-0.95] | 1.49 | -2.62 | -1.58 | +2,248,622 | -23,208 | 0.23 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_PB3 | 6392 | -1.99 [-3.15,-0.76] | 1.71 | -3.05 | -0.87 | -182,573 | -1,813 | 0.22 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST10n10 | 1833 | -1.99 [-3.95,+0.01] | 2.86 | -1.71 | -0.27 | +212,935 | -315 | 0.62 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_ONH_ST10n7 | 1847 | -2.01 [-7.50,+3.60] | 8.05 | -0.56 | +4.88 | +61,793 | +3,382 | 0.83 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_STB_KEL3 | 7169 | -2.09 [-4.53,+0.40] | 3.49 | -2.78 | -1.05 | +1,333,740 | -8,845 | 0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_EMA5 | 1800 | -2.11 [-4.36,+0.09] | 3.18 | -2.32 | -2.49 | +394,646 | -5,779 | 0.50 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST10n7 | 1847 | -2.11 [-4.03,-0.15] | 2.79 | -1.78 | -0.30 | +156,812 | -507 | 0.66 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_ST | 6952 | -2.13 [-3.46,-0.81] | 1.88 | -1.81 | -1.32 | +3,225,134 | -25,890 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_TB7 | 895 | -2.15 [-4.92,+0.91] | 4.15 | +0.12 | +1.00 | +53,598 | -727 | 0.02 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n10 | 1833 | -2.22 [-4.36,-0.09] | 3.07 | -1.54 | -4.20 | +553,980 | -7,948 | 0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST10n14 | 1868 | -2.23 [-4.18,-0.20] | 2.83 | -2.80 | -0.71 | +278,506 | -1,008 | 0.77 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_HM | 5162 | -2.27 [-3.42,-1.07] | 1.68 | -2.30 | -1.44 | -111,647 | +323 | 0.18 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n14 | 1868 | -2.31 [-4.06,-0.61] | 2.48 | -1.46 | -1.81 | +439,589 | -8,095 | 0.53 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST | 6952 | -2.34 [-5.83,+1.49] | 5.22 | -3.81 | -3.64 | +303,039 | -379 | 0.64 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_PBS | 4978 | -2.38 [-4.22,-0.51] | 2.66 | -4.44 | -3.56 | -89,123 | -7,495 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n14 | 1868 | -2.39 [-6.99,+2.45] | 6.77 | -2.38 | -0.05 | +163,326 | -234 | 0.88 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n14 | 1868 | -2.40 [-4.49,-0.29] | 3.02 | -1.81 | -3.56 | +688,295 | -8,755 | 0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n10 | 1833 | -2.43 [-4.27,-0.63] | 2.60 | -1.61 | -2.33 | +312,392 | -7,221 | 0.38 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_ST | 6952 | -2.45 [-3.72,-1.17] | 1.83 | -2.20 | -1.87 | +3,554,259 | -27,859 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_EM_PB3 | 6392 | -2.47 [-7.43,+2.67] | 7.24 | -4.69 | -1.97 | -245,591 | +5,213 | 0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_HM | 5162 | -2.49 [-3.96,-1.07] | 2.07 | -2.79 | -0.29 | +2,213,314 | -15,586 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_PB3 | 6392 | -2.56 [-5.14,+0.23] | 3.88 | -4.15 | -1.53 | +679,011 | -11,801 | 0.07 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n7 | 1847 | -2.59 [-4.67,-0.52] | 2.98 | -0.80 | -2.30 | +772,207 | -8,277 | 0.60 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_KEL3 | 7169 | -2.60 [-3.85,-1.33] | 1.81 | -2.45 | -1.18 | +2,891,358 | -20,115 | 0.94 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n7 | 1847 | -2.61 [-4.40,-0.88] | 2.51 | -1.31 | -0.77 | +539,536 | -7,227 | 0.47 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_ST | 6952 | -2.70 [-4.05,-1.38] | 1.90 | -2.55 | -1.92 | +3,564,855 | -27,736 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_KEL3 | 7169 | -2.75 [-5.28,-0.11] | 3.70 | -3.36 | -1.48 | +1,646,366 | -10,317 | 0.37 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_HM | 5162 | -2.86 [-4.39,-1.38] | 2.12 | -3.42 | -1.06 | +3,044,521 | -21,063 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n14 | 1868 | -2.91 [-8.22,+2.52] | 7.76 | -4.16 | +0.50 | +273,885 | -21 | 0.60 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_CH2_KEL3 | 7169 | -3.06 [-4.37,-1.77] | 1.85 | -2.39 | -0.02 | +3,055,105 | -23,143 | 0.03 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_EMA5 | 1800 | -3.10 [-5.63,-0.52] | 3.64 | -3.48 | -0.41 | +222,876 | -5,162 | 0.12 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_KB_HM | 5162 | -3.15 [-6.16,+0.10] | 4.47 | -4.53 | -0.93 | +373,392 | +1,652 | 0.75 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_KEL3 | 7169 | -3.19 [-6.42,+0.26] | 4.76 | -4.25 | -1.45 | +1,549,842 | -10,247 | 0.48 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_EM_KEL3 | 7169 | -3.22 [-7.66,+1.52] | 6.53 | -4.91 | -2.41 | -393,912 | +5,211 | 0.20 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_HM | 5162 | -3.24 [-4.78,-1.74] | 2.15 | -3.68 | -1.33 | +2,984,281 | -19,846 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_PB3 | 6392 | -3.27 [-4.65,-1.88] | 1.99 | -4.48 | -1.64 | +1,773,296 | -20,074 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_PB3 | 6392 | -3.27 [-4.88,-1.65] | 2.29 | -4.35 | -1.53 | +1,566,753 | -18,302 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_ST10n7 | 1847 | -3.27 [-6.37,-0.21] | 4.43 | -2.61 | -2.08 | +362,875 | -4,315 | 0.25 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_ST | 6952 | -3.29 [-4.64,-1.93] | 1.96 | -3.29 | -1.27 | +3,450,701 | -27,736 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_ST | 6952 | -3.33 [-4.84,-1.83] | 2.15 | -3.30 | -1.67 | +2,580,650 | -20,458 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_EM_ST | 6952 | -3.39 [-8.41,+1.93] | 7.42 | -4.94 | -1.06 | -163,222 | +3,370 | 0.17 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST | 6952 | -3.45 [-7.68,+1.26] | 6.46 | -5.72 | -3.37 | +488,039 | -2,168 | 0.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_PB3 | 6392 | -3.47 [-4.88,-2.05] | 2.02 | -4.44 | -1.46 | +2,528,383 | -25,219 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_KB_ST | 6952 | -3.47 [-6.51,-0.04] | 4.65 | -3.27 | -2.67 | +940,909 | -8,428 | 0.92 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_KEL3 | 7169 | -3.53 [-4.92,-2.15] | 1.97 | -3.13 | +0.07 | +2,464,886 | -18,546 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_90_KEL3 | 7169 | -3.53 [-6.45,-0.46] | 4.25 | -4.62 | -1.79 | +1,595,829 | -10,070 | 0.38 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_HM | 5162 | -3.56 [-5.14,-1.99] | 2.24 | -4.26 | -0.60 | +2,868,436 | -19,479 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_ST10n7 | 1847 | -3.56 [-6.78,-0.29] | 4.65 | -3.86 | -1.92 | +266,089 | -2,084 | 0.15 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_KEL3 | 7169 | -3.75 [-5.32,-2.17] | 2.25 | -3.62 | +0.09 | +1,993,799 | -15,029 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_OPP_KB_PB3 | 6392 | -3.75 [-7.01,-0.07] | 4.95 | -5.46 | -2.99 | +430,247 | -10,577 | 0.99 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_PB3 | 6392 | -3.85 [-5.62,-2.05] | 2.54 | -4.86 | -1.84 | +1,155,302 | -15,345 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_HM | 5162 | -3.88 [-5.50,-2.30] | 2.27 | -4.97 | -1.29 | +2,224,601 | -13,670 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_ST | 6952 | -3.91 [-8.80,+1.56] | 7.53 | -6.27 | -3.39 | +236,200 | -870 | 0.44 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_EMA5 | 1800 | -3.97 [-6.67,-1.22] | 3.89 | -4.52 | -0.89 | +283,511 | -5,623 | 0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_ST10n7 | 1847 | -4.14 [-7.03,-1.17] | 4.20 | -3.42 | -1.25 | +383,245 | -3,960 | 0.05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_EMA5 | 1800 | -4.43 [-6.97,-1.81] | 3.68 | -4.13 | -1.67 | +854,703 | -9,512 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_KB_ST10n7 | 1847 | -4.79 [-8.14,-1.26] | 4.94 | -5.79 | -3.08 | +341,998 | -3,923 | 0.12 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_ST10n7 | 1847 | -4.81 [-7.45,-2.13] | 3.82 | -3.60 | -0.76 | +692,721 | -7,945 | 0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_EMA5 | 1800 | -4.83 [-7.38,-2.35] | 3.59 | -4.66 | -1.72 | +1,139,829 | -11,218 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_OPP_KB_EMA5 | 1800 | -5.11 [-8.22,-1.86] | 4.53 | -6.30 | -3.24 | +488,478 | -6,546 | 0.05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |

## Caveats
* Direct L2 replay prices every stop-type and market exit; target exits are limits at the level (identical machinery for the base). Sequences use the base entry set (PB3: 7,656 of 8,339 rows after one-open-trade-per-book). Equal-risk columns / DS3 marginal Sharpe: not computed because no cell is PASS or CANDIDATE.
* Holdout (2025-07+) and the 2023 span were read once in the invalid v1 pipeline and again in v2; per-group looks are logged (…_V2). Details of each family are in DS3_TC1C2 / TC3C4 / TC5 / TC4R4 / TC6PB.

## Disclosure (looks and exclusions)
* v1 (invalid price frame) read the holdout and the 2023 span once; v2 re-read them (looks logged as DS3_TC_<G>_V2 and _SPAN2_V2; G5 groups logged at their pre stage); a final-stage re-run (V2b) of C, R4 and G5 followed the exclusion below. So the holdout evidence is a third read for C/R4 and a first-and-second read for G5; no cell definition or parameter changed between reads.
* The L2 raw on disk ends 2026-10-09; trades entered after 2026-10-09 20:00 UTC (about 1.5% of trades) are excluded from every cell and every base (identical filter, so pairs stay matched). The 2% missing-fill gate was NOT loosened: after this exclusion missing fills are 0.1-0.2% entries / 0.04-0.08% exits; no replay month needed re-running (done5 45/45 complete).
* 246 cells total (Track C 104, R4 70, G5 72), all DEAD; best-of-246 leads are noted per book above (C4b overnight-level target on SM +2.25 [+0.51,+3.99], holdout +3.25, fails neighbours/year share).
