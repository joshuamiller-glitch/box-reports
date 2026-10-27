# DS3_EXITS_FINAL - exit structure on every book (D3XT, priority item 1)

Generated 2026-10-27T13:40:50Z. Research only; nothing is a live recommendation. 174 prereg'd exit cells scored (Track C 104 incl. TB7/ST10 siblings, R4 70, PB + OPP flips 72; preregs TC_G1..G5, shas in autopilot/DECISIONS.md), direct L2 basis, paired per trade on identical entries vs each book's own DS2 bracket (60/60, 1R, flat 16:55), exact per-book locks at 10 lots, price frame corrected (v1 outputs *_v1_INVALID* superseded).

## Verdict
**0 PASS, 0 CANDIDATE, 174 DEAD of 174 cells.** No exit rule is a PASS or CANDIDATE on any book, so there is no parameter spec to write and nothing to put into the DS3 container for all books at once; the live DS2 fixed bracket (60/60 flat 16:55) stays the best-supported exit on every book.

Best exit per book on the book's own entries (best = highest paired mean over all its cells; "verdict" is the V2 verdict of that cell; the best-of-N bias applies: N cells per book are shown in the next table):

* Best exit on ST10's own entries: XT_R4_PL_ST, paired +1.04 pts/trade [-0.32,+2.39] (MDE 1.94, n 7105), maxDD Delta +483,354, direct basis; holdout +0.60, 2023 span +0.03, 2x-cost paired +1.29, placebo 0.99; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse).
* Best exit on HM10's own entries: XT_C4a_HM, paired +0.10 pts/trade [-0.86,+1.04] (MDE 1.35, n 5271), maxDD Delta +171,487, direct basis; holdout +0.53, 2023 span -0.64, 2x-cost paired +0.07, placebo 1.00; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%).
* Best exit on KB (TE7_kelt3m_n14_m1.0)'s own entries: XT_R4_TNONE_KEL3, paired +1.45 pts/trade [-2.92,+6.03] (MDE 6.36, n 7339), maxDD Delta -194,347, direct basis; holdout +0.81, 2023 span -0.19, 2x-cost paired +0.42, placebo 1.00; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%).
* Best exit on SM (TE6_st10m_n7_m3.0)'s own entries: XT_C4b_ST10n7, paired +2.18 pts/trade [+0.45,+3.92] (MDE 2.48, n 1878), maxDD Delta -29,929, direct basis; holdout +3.08, 2023 span +0.13, 2x-cost paired +2.09, placebo 1.00; verdict DEAD (neighbours_agree,year_share>60%).
* Best exit on EM (TE7_emax5m_f30_s50, disabled)'s own entries: XT_R4_TD120_EMA5, paired +1.60 pts/trade [-2.66,+5.96] (MDE 6.21, n 1831), maxDD Delta +303,429, direct basis; holdout +3.45, 2023 span -4.18, 2x-cost paired +1.13, placebo 1.00; verdict DEAD (neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60%).
* PB_ST10_SWZ_T3: not scored (replay pending)
* PB3B_R5_P1: not scored (replay pending)

## One row per book: best cell, TH-loss control, fixed-bracket control
| book | n entries (WF pairs) | best cell | paired pts/trade [CI] | maxDD Delta $ | verdict | LIVE TH-loss control (G1_TH_LIVE_ST 15/3/30, live-join): paired [CI] | cells > 0 / cells scored | cells with CI excluding 0 above |
|---|---|---|---|---|---|---|---|---|
| ST10 | 7105 | XT_R4_PL_ST | +1.04 [-0.32,+2.39] | +483,354 | DEAD | -0.89 [-1.79,+0.01] (MDE 1.27) | 6/27 | 0 |
| HM10 | 5271 | XT_C4a_HM | +0.10 [-0.86,+1.04] | +171,487 | DEAD | -1.20 [-2.29,-0.14] (MDE 1.54) | 2/27 | 0 |
| KB (TE7_kelt3m_n14_m1.0) | 7339 | XT_R4_TNONE_KEL3 | +1.45 [-2.92,+6.03] | -194,347 | DEAD | -0.97 [-1.82,-0.13] (MDE 1.23) | 9/27 | 0 |
| SM (TE6_st10m_n7_m3.0) | 1878 | XT_C4b_ST10n7 | +2.18 [+0.45,+3.92] | -29,929 | DEAD | -1.02 [-2.77,+0.50] (MDE 2.34) | 4/27 | 1 |
| EM (TE7_emax5m_f30_s50, disabled) | 1831 | XT_R4_TD120_EMA5 | +1.60 [-2.66,+5.96] | +303,429 | DEAD | -1.36 [-3.13,+0.30] (MDE 2.45) | 9/27 | 0 |

TH-loss control = the live Trade-Health loss rule (min loss 15 pts, 3 of 3 conditions, 30 s windows) from autopilot/DS3_TH_G1.md addendum (live stop-join profile), all-span paired vs the book's base bracket; the fixed bracket itself is the zero row of every table.

## Per-book consistency of each rule (paired pts/trade; * = CI excludes 0)
| rule | ST10 | HM10 | KB | SM | EM | PB_ST10_SWZ_T3 | PB3B_R5_P1 | books > 0 | books CI>0 |
|---|---|---|---|---|---|---|---|---|---|
| C1_120 | -2.79 | -1.51 | -3.13 | +0.59 | +0.42 | - | - | 2 | 0 |
| C1_60 | -1.77 | -1.35 | -2.69 | -0.25 | +0.15 | - | - | 1 | 0 |
| C1_90 | -2.68 | -1.62 | -3.46 | +0.62 | +0.69 | - | - | 2 | 0 |
| C2_120 | -0.63 | -0.52 | -0.94 | -0.86 | -0.14 | - | - | 0 | 0 |
| C2_30 | -1.33 | -1.64 | -0.81 | -2.60 | -2.02 | - | - | 0 | 0 |
| C2_60 | -1.07 | -0.64 | -1.16 | -2.50 | -1.54 | - | - | 0 | 0 |
| C3 | -1.64 | -2.30 | -1.87 | -2.09 | -1.61 | - | - | 0 | 0 |
| C4a | -0.27 | +0.10 | -0.39 | -0.40 | -0.58 | - | - | 1 | 0 |
| C4b | +0.40 | -0.46 | +0.42 | +2.18* | +1.41 | - | - | 4 | 1 |
| C4c | +0.14 | -0.45 | -0.10 | -1.85 | -0.59 | - | - | 1 | 0 |
| C5A | -0.07 | -0.09 | -0.05 | -0.05 | -0.06 | - | - | 0 | 0 |
| C5B | -0.04 | -0.03 | -0.15 | -0.06 | -0.12 | - | - | 0 | 0 |
| C5C | +0.11 | +0.05 | +0.03 | -0.08 | +0.08 | - | - | 4 | 0 |
| R4_CH2 | -2.11 | -2.83 | -3.02 | -4.85 | -4.70 | - | - | 0 | 0 |
| R4_CH25 | -2.66 | -3.21 | -3.54 | -4.24 | -4.46 | - | - | 0 | 0 |
| R4_CH3 | -3.24 | -3.55 | -3.71 | -3.75 | -4.03 | - | - | 0 | 0 |
| R4_MM | +0.01 | -1.32 | +0.12 | -1.73 | +0.12 | - | - | 3 | 0 |
| R4_ONH | -0.68 | -1.33 | +0.98 | -2.18 | +0.27 | - | - | 2 | 0 |
| R4_PL | +1.04 | -0.00 | +0.76 | -0.91 | -0.44 | - | - | 2 | 0 |
| R4_PSAR | -2.39 | -2.45 | -2.60 | -3.45 | -3.09 | - | - | 0 | 0 |
| R4_STB | -3.24 | -3.93 | -2.17 | -1.53 | -1.38 | - | - | 0 | 0 |
| R4_T15 | -0.10 | -0.41 | +0.09 | -1.41 | -1.10 | - | - | 1 | 0 |
| R4_T20 | +0.01 | -0.95 | +0.08 | -0.63 | -1.37 | - | - | 2 | 0 |
| R4_TD120 | -0.61 | -1.03 | +0.54 | +1.01 | +1.60 | - | - | 3 | 0 |
| R4_TD30 | -1.39 | -1.91 | -0.81 | -1.12 | -1.41 | - | - | 0 | 0 |
| R4_TD60 | -1.12 | -1.24 | -0.47 | -1.99 | -1.68 | - | - | 0 | 0 |
| R4_TNONE | -0.29 | -0.98 | +1.45 | -1.53 | +0.64 | - | - | 2 | 0 |

## Rule coverage (user list -> prereg'd cells)
* Chandelier k 2/2.5/3 = R4_CH2/CH25/CH3; Supertrend-band trail = R4_STB; swing-structure trail = C3; parabolic SAR = R4_PSAR.
* Opposite-flip: own book = C1_60/90/120; faster book = OPP_KB, OPP_SM, OPP_EM (EM disabled live) on ST, HM, PBS, PB3 and the other fast books.
* Time-decay tightening = R4_TD30/60/120; profit-lock +1.5R -> +0.5R, +2R -> trail 20 = R4_PL; time stop = C2.
* Overnight hold-through = C5A/B/C and R4_ONH (>= +1R at 16:55); trail-only (no target) = R4_TNONE and the trail rules; 1.5R / 2R / measured-move / next-level targets = R4_T15, R4_T20, R4_MM, C4a/b/c.

## All cells (sorted by paired mean)
| cell | n | paired [CI] | MDE | holdout | 2023 span | maxDD Delta | d wk $ (WF) | placebo | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|
| XT_C1_90_TB7 | 898 | +4.04 [-3.97,+12.25] | 11.55 | +3.09 | +8.89 | -481,232 | +7,711 | 0.68 | DEAD | placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C1_60_TB7 | 898 | +3.83 [-2.92,+10.99] | 10.09 | +1.89 | +3.98 | -597,118 | +7,783 | 0.92 | DEAD | paired_CI_excludes0&maxDD_not_worse,placebo<0.95,year_share>60% |
| XT_C4b_ST10n10 | 1864 | +2.49 [+0.75,+4.24] | 2.48 | +3.49 | -0.49 | -92,075 | +4,311 | 1.00 | DEAD | neighbours_agree,SPAN2<=0 |
| XT_C4b_ST10n7 | 1878 | +2.18 [+0.45,+3.92] | 2.48 | +3.08 | +0.13 | -29,929 | +4,138 | 1.00 | DEAD | neighbours_agree,year_share>60% |
| XT_C1_120_TB7 | 898 | +2.11 [-6.52,+10.89] | 12.43 | +1.89 | +9.10 | -385,880 | +7,790 | 0.59 | DEAD | placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4b_ST10n14 | 1898 | +1.62 [-0.10,+3.37] | 2.48 | +2.56 | -1.63 | +5,054 | +4,885 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_R4_TD120_EMA5 | 1831 | +1.60 [-2.66,+5.96] | 6.21 | +3.45 | -4.18 | +303,429 | +5,983 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C4b_TB7 | 898 | +1.55 [-0.21,+3.35] | 2.53 | +2.56 | +2.52 | -407,386 | +1,971 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_TNONE_KEL3 | 7339 | +1.45 [-2.92,+6.03] | 6.36 | +0.81 | -0.19 | -194,347 | +1,187 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C4b_EMA5 | 1831 | +1.41 [-0.31,+3.13] | 2.42 | +2.07 | +1.14 | +40,777 | +764 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_PL_ST | 7105 | +1.04 [-0.32,+2.39] | 1.94 | +0.60 | +0.03 | +483,354 | -3,723 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |
| XT_R4_TD120_ST10n7 | 1878 | +1.01 [-3.55,+5.80] | 6.58 | +2.10 | -2.56 | +361,000 | +6,201 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_ONH_KEL3 | 7339 | +0.98 [-3.38,+5.55] | 6.30 | +0.15 | -0.76 | -270,457 | +3,089 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_TB7 | 898 | +0.97 [-0.78,+2.71] | 2.49 | +2.20 | -0.51 | -124,545 | +1,311 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_PL_KEL3 | 7339 | +0.76 [-0.45,+1.94] | 1.72 | +0.70 | -0.76 | -206,667 | +4,175 | 0.98 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0 |
| XT_C1_90_EMA5 | 1831 | +0.69 [-4.62,+6.37] | 7.86 | +4.20 | +1.67 | +269,508 | +4,009 | 0.94 | DEAD | paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_EMA5 | 1831 | +0.64 [-4.80,+6.43] | 8.07 | +1.93 | +4.70 | +200,843 | +4,824 | 0.89 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n7 | 1878 | +0.62 [-4.67,+6.32] | 7.93 | +1.56 | +1.60 | +90,558 | +6,303 | 0.99 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_120_ST10n7 | 1878 | +0.59 [-5.09,+6.66] | 8.36 | +1.27 | +1.64 | +44,850 | +8,444 | 0.94 | DEAD | paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_R4_TD120_KEL3 | 7339 | +0.54 [-2.76,+4.08] | 4.85 | +1.01 | -3.80 | -48,436 | +4,648 | 0.92 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,year_share>60% |
| XT_C5C_TB7 | 898 | +0.46 [-0.36,+1.28] | 1.17 | +0.44 | +2.57 | -149,256 | +487 | 0.98 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse |
| XT_C1_120_EMA5 | 1831 | +0.42 [-5.17,+6.43] | 8.30 | +3.51 | +1.15 | +343,305 | +4,493 | 0.95 | DEAD | paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4b_KEL3 | 7339 | +0.42 [-0.38,+1.22] | 1.15 | +0.60 | -0.23 | +61,836 | +1,544 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_C4b_ST | 7105 | +0.40 [-0.39,+1.21] | 1.14 | +0.14 | -0.60 | +69,951 | -614 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_ONH_EMA5 | 1831 | +0.27 [-5.16,+6.05] | 8.04 | +1.54 | +4.60 | +88,197 | +9,596 | 0.97 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_120_ST10n10 | 1864 | +0.20 [-5.83,+6.31] | 8.63 | +1.12 | -0.11 | +66,013 | +9,816 | 0.90 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_EMA5 | 1831 | +0.15 [-4.52,+5.24] | 6.96 | +2.06 | +2.97 | +181,590 | +6,284 | 0.97 | DEAD | paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_ST | 7105 | +0.14 [-0.73,+1.03] | 1.26 | +0.11 | -0.23 | +95,544 | -687 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_MM_EMA5 | 1831 | +0.12 [-1.64,+1.89] | 2.53 | +0.00 | +0.67 | -3,632 | +3,206 | 0.97 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_MM_KEL3 | 7339 | +0.12 [-0.89,+1.12] | 1.42 | +0.25 | -0.77 | -157,544 | +4,166 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST | 7105 | +0.11 [-0.08,+0.28] | 0.25 | +0.05 | +0.65 | -48,055 | +19 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C4a_HM | 5271 | +0.10 [-0.86,+1.04] | 1.35 | +0.53 | -0.64 | +171,487 | +2,203 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,year_share>60% |
| XT_R4_T15_KEL3 | 7339 | +0.09 [-0.86,+1.02] | 1.33 | -0.59 | -0.19 | -362,436 | +2,981 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_EMA5 | 1831 | +0.08 [-0.36,+0.53] | 0.64 | +0.00 | +0.18 | -31,354 | +330 | 0.96 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_R4_T20_KEL3 | 7339 | +0.08 [-1.25,+1.38] | 1.89 | -0.15 | -1.00 | -17,427 | +3,434 | 0.96 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_HM | 5271 | +0.05 [-0.20,+0.29] | 0.35 | +0.16 | +1.51 | -82,825 | +1,208 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5C_KEL3 | 7339 | +0.03 [-0.16,+0.22] | 0.27 | +0.08 | +0.42 | -137,708 | -1,022 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,year_share>60% |
| XT_C5B_TB7 | 898 | +0.02 [-0.39,+0.45] | 0.60 | -0.03 | -0.43 | +11,020 | +98 | 1.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_ST | 7105 | +0.01 [-0.98,+1.01] | 1.42 | +0.26 | +0.18 | +90,351 | -3,542 | 1.00 | DEAD | neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_T20_ST | 7105 | +0.01 [-1.47,+1.48] | 2.11 | -0.16 | -0.81 | +203,703 | -1,455 | 0.98 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PL_HM | 5271 | -0.00 [-1.46,+1.43] | 2.06 | -0.27 | +0.07 | +47,410 | +5,786 | 0.92 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,year_share>60% |
| XT_C5B_HM | 5271 | -0.03 [-0.15,+0.08] | 0.16 | -0.04 | -0.30 | +30,154 | -665 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST | 7105 | -0.04 [-0.11,+0.04] | 0.11 | -0.06 | -0.24 | +24,545 | -737 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n14 | 1898 | -0.04 [-0.41,+0.32] | 0.53 | -0.20 | -0.97 | -24,263 | -289 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n7 | 1878 | -0.05 [-0.11,+0.02] | 0.09 | -0.04 | -0.42 | +15,984 | +19 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_KEL3 | 7339 | -0.05 [-0.11,+0.00] | 0.08 | -0.02 | -0.26 | -8,998 | -419 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n10 | 1864 | -0.06 [-0.11,-0.01] | 0.07 | -0.05 | -0.32 | -650 | -176 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n7 | 1878 | -0.06 [-0.23,+0.10] | 0.23 | -0.06 | -0.58 | +32,731 | -99 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_EMA5 | 1831 | -0.06 [-0.14,+0.04] | 0.13 | -0.08 | -0.25 | +21,842 | -117 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST | 7105 | -0.07 [-0.10,-0.04] | 0.05 | -0.07 | -0.18 | +22,728 | -658 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_ST10n14 | 1898 | -0.07 [-0.12,-0.03] | 0.07 | -0.06 | -0.33 | +2,890 | -131 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n10 | 1864 | -0.07 [-0.24,+0.09] | 0.23 | -0.08 | -0.46 | -650 | -303 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n7 | 1878 | -0.08 [-0.45,+0.30] | 0.53 | +0.05 | -1.17 | +75,225 | +107 | 1.00 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_HM | 5271 | -0.09 [-0.13,-0.05] | 0.06 | -0.05 | -0.29 | +38,235 | -834 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_ST | 7105 | -0.10 [-1.15,+0.94] | 1.50 | -0.52 | +0.62 | +392,830 | -4,612 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_KEL3 | 7339 | -0.10 [-0.87,+0.68] | 1.12 | +0.47 | -0.58 | -241,470 | +2,162 | 1.00 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_EMA5 | 1831 | -0.12 [-0.26,+0.02] | 0.20 | -0.15 | -0.55 | +21,573 | -256 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5A_TB7 | 898 | -0.13 [-0.27,-0.01] | 0.19 | -0.05 | -0.54 | +38,380 | -57 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_ST10n14 | 1898 | -0.13 [-0.28,-0.03] | 0.18 | -0.18 | -0.55 | +20,279 | -182 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_EMA5 | 1831 | -0.14 [-1.60,+1.32] | 2.10 | -0.55 | -1.08 | -26,721 | -1,038 | 0.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5B_KEL3 | 7339 | -0.15 [-0.29,-0.03] | 0.19 | -0.09 | -0.36 | +61,491 | -989 | 1.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C5C_ST10n10 | 1864 | -0.17 [-0.54,+0.20] | 0.52 | -0.07 | -0.83 | -18,538 | -222 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n7 | 1878 | -0.25 [-4.98,+4.66] | 6.87 | +1.07 | +0.91 | +7,252 | +5,258 | 0.98 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4a_ST | 7105 | -0.27 [-1.09,+0.53] | 1.17 | +0.06 | -0.96 | -36,616 | +584 | 0.99 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_ST | 7105 | -0.29 [-4.83,+4.56] | 6.75 | -0.85 | -1.80 | +652,583 | -8,856 | 0.91 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_KEL3 | 7339 | -0.39 [-1.20,+0.42] | 1.16 | -0.04 | -0.96 | +383,709 | -4,894 | 0.96 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n7 | 1878 | -0.40 [-2.25,+1.48] | 2.66 | +1.15 | -2.18 | +385,152 | -3,241 | 0.95 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_HM | 5271 | -0.41 [-1.57,+0.72] | 1.66 | -1.25 | +0.45 | +7,064 | +5,728 | 0.76 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n14 | 1898 | -0.42 [-2.32,+1.46] | 2.68 | +0.91 | -3.36 | +422,759 | -1,359 | 0.97 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PL_EMA5 | 1831 | -0.44 [-2.86,+1.96] | 3.47 | +0.52 | +0.99 | +144,110 | +2,916 | 0.68 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_HM | 5271 | -0.45 [-1.32,+0.43] | 1.24 | -0.31 | -0.02 | +219,346 | -911 | 0.90 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4b_HM | 5271 | -0.46 [-1.37,+0.42] | 1.29 | -0.58 | -0.98 | -47,040 | +2,324 | 0.90 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_KEL3 | 7339 | -0.47 [-3.03,+2.25] | 3.74 | -0.54 | -3.10 | +456,822 | -4,082 | 0.64 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n10 | 1864 | -0.49 [-6.06,+5.20] | 8.01 | +1.32 | +0.14 | +79,047 | +5,541 | 0.91 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_C2_120_HM | 5271 | -0.52 [-1.29,+0.21] | 1.07 | -0.38 | -0.33 | +798,770 | -3,897 | 0.91 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_TB7 | 898 | -0.56 [-2.63,+1.46] | 2.87 | -1.05 | -0.16 | +97,170 | +96 | 0.65 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_EMA5 | 1831 | -0.58 [-2.51,+1.31] | 2.72 | +0.31 | -2.36 | +156,798 | -2,343 | 0.61 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_EMA5 | 1831 | -0.59 [-2.00,+0.84] | 2.03 | -1.31 | -0.44 | +137,904 | -840 | 0.72 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4a_ST10n10 | 1864 | -0.60 [-2.43,+1.22] | 2.65 | +1.30 | -2.76 | +250,761 | -3,166 | 0.85 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD120_ST | 7105 | -0.61 [-4.23,+3.29] | 5.33 | +0.34 | -6.09 | +255,782 | +3,822 | 0.68 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_ST10n7 | 1878 | -0.63 [-3.36,+2.05] | 3.85 | +0.67 | +0.77 | +323,183 | -2,015 | 0.92 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_C2_120_ST | 7105 | -0.63 [-1.21,-0.05] | 0.84 | -0.32 | -1.74 | +902,292 | -9,242 | 0.93 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_HM | 5271 | -0.64 [-1.64,+0.35] | 1.42 | -0.44 | -0.19 | +830,085 | -4,394 | 0.96 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_ST10n14 | 1898 | -0.68 [-6.39,+5.30] | 8.41 | -1.68 | +0.59 | +199,382 | +6,746 | 0.91 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,2x_cost<=0,year_share>60% |
| XT_R4_ONH_ST | 7105 | -0.68 [-5.23,+4.10] | 6.71 | -1.43 | -2.25 | +73,901 | +2,814 | 0.99 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_TB7 | 898 | -0.74 [-3.05,+1.52] | 3.26 | +0.27 | +1.20 | +35,740 | -605 | 0.65 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_KEL3 | 7339 | -0.81 [-1.80,+0.17] | 1.41 | -0.52 | +0.60 | +2,609,685 | -21,182 | 0.80 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD30_KEL3 | 7339 | -0.81 [-2.76,+1.18] | 2.78 | -0.70 | -0.74 | +956,294 | -8,077 | 0.46 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n7 | 1878 | -0.86 [-2.29,+0.57] | 2.06 | +0.23 | -0.14 | -4,589 | -1,867 | 0.95 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n10 | 1864 | -0.89 [-5.65,+3.88] | 6.84 | +0.86 | -0.28 | +29,823 | +3,574 | 0.91 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PL_ST10n7 | 1878 | -0.91 [-3.41,+1.54] | 3.51 | -0.50 | +0.93 | +149,916 | -1,083 | 0.88 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_120_KEL3 | 7339 | -0.94 [-1.53,-0.34] | 0.85 | -0.68 | -0.38 | +1,503,544 | -10,090 | 0.62 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_HM | 5271 | -0.95 [-2.57,+0.67] | 2.33 | -0.58 | +0.02 | +429,327 | +3,134 | 0.60 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n10 | 1864 | -0.97 [-2.41,+0.48] | 2.06 | +0.02 | -2.08 | -24,792 | -3,311 | 0.92 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_HM | 5271 | -0.98 [-5.53,+3.85] | 6.76 | -0.04 | +0.05 | +158,980 | +12,144 | 0.78 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_60_TB7 | 898 | -1.02 [-2.65,+0.65] | 2.37 | -0.99 | +1.25 | +78,843 | -1,134 | 0.47 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD120_HM | 5271 | -1.03 [-4.50,+2.56] | 5.07 | +0.63 | -3.17 | -14,115 | +16,298 | 0.57 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST | 7105 | -1.07 [-1.84,-0.30] | 1.10 | -0.57 | -0.90 | +1,411,746 | -14,236 | 0.71 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_ST10n14 | 1898 | -1.10 [-2.48,+0.34] | 2.02 | -0.50 | -1.89 | +32,456 | -4,824 | 0.94 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_EMA5 | 1831 | -1.10 [-3.12,+0.84] | 2.84 | -0.19 | +0.29 | +231,649 | -1,066 | 0.67 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD60_ST | 7105 | -1.12 [-3.91,+1.88] | 4.11 | -1.26 | -3.46 | +217,579 | +1,151 | 0.36 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_ST10n7 | 1878 | -1.12 [-4.30,+2.19] | 4.61 | +0.68 | -2.00 | +123,640 | -711 | 0.99 | DEAD | mean_up,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_KEL3 | 7339 | -1.16 [-1.96,-0.40] | 1.12 | -1.07 | +0.39 | +2,139,452 | -16,785 | 0.55 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n10 | 1864 | -1.22 [-2.77,+0.32] | 2.21 | -2.55 | -0.94 | +166,049 | -3,317 | 0.68 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_HM | 5271 | -1.24 [-4.02,+1.63] | 4.05 | -0.97 | -1.21 | +36,665 | +14,314 | 0.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_HM | 5271 | -1.32 [-2.36,-0.28] | 1.49 | -1.41 | +0.76 | +119,743 | -1,176 | 0.09 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_ST | 7105 | -1.33 [-2.30,-0.36] | 1.39 | -0.74 | -1.20 | +2,402,198 | -20,776 | 0.54 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_ONH_HM | 5271 | -1.33 [-5.92,+3.45] | 6.77 | -0.68 | -0.49 | -221,334 | +16,208 | 0.92 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,placebo<0.95,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_HM | 5271 | -1.35 [-4.72,+2.23] | 4.99 | -2.29 | -1.72 | +64,019 | +7,121 | 0.95 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T20_EMA5 | 1831 | -1.37 [-4.07,+1.29] | 3.85 | +0.16 | +2.03 | +301,346 | -535 | 0.61 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_STB_EMA5 | 1831 | -1.38 [-4.72,+2.05] | 4.84 | -0.70 | -1.21 | +107,473 | +2,967 | 0.66 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_ST | 7105 | -1.39 [-3.52,+0.85] | 3.14 | -0.84 | -1.23 | +447,219 | -7,035 | 0.19 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_T15_ST10n7 | 1878 | -1.41 [-3.44,+0.60] | 2.88 | -0.23 | +1.03 | +68,818 | -726 | 0.73 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TD30_EMA5 | 1831 | -1.41 [-4.37,+1.65] | 4.26 | +0.21 | -1.38 | +279,051 | -2,546 | 0.65 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_120_TB7 | 898 | -1.43 [-2.57,-0.27] | 1.67 | -0.53 | +1.54 | +134,442 | -1,579 | 0.25 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_120_HM | 5271 | -1.51 [-5.96,+3.16] | 6.53 | -3.49 | -1.08 | +61,737 | +1,703 | 0.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_ST10n7 | 1878 | -1.53 [-5.79,+2.93] | 6.21 | -2.71 | +0.23 | +196,247 | +619 | 0.76 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_TNONE_ST10n7 | 1878 | -1.53 [-7.10,+4.17] | 8.07 | -0.25 | +5.12 | +92,986 | +3,944 | 0.74 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_60_EMA5 | 1831 | -1.54 [-3.38,+0.29] | 2.64 | -1.89 | -0.73 | +238,473 | -4,435 | 0.62 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_EMA5 | 1831 | -1.61 [-3.40,+0.28] | 2.66 | -1.69 | +0.30 | +122,883 | +1,321 | 0.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_90_HM | 5271 | -1.62 [-5.66,+2.62] | 5.96 | -3.11 | -1.43 | -3,875 | +5,363 | 0.97 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST | 7105 | -1.64 [-2.84,-0.41] | 1.74 | -2.06 | -1.42 | +184,639 | -2,109 | 0.27 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_HM | 5271 | -1.64 [-2.84,-0.47] | 1.72 | -1.70 | -0.25 | +1,983,029 | -13,203 | 0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_EMA5 | 1831 | -1.68 [-5.15,+1.80] | 4.98 | -1.11 | -3.27 | +341,022 | +38 | 0.40 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_MM_ST10n7 | 1878 | -1.73 [-3.82,+0.34] | 2.93 | -2.72 | +1.06 | +265,107 | -1,120 | 0.41 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_60_ST | 7105 | -1.77 [-5.32,+2.05] | 5.31 | -2.76 | -3.64 | +303,039 | -1,196 | 0.80 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n14 | 1898 | -1.77 [-3.35,-0.18] | 2.26 | -2.74 | -1.83 | +199,905 | -4,427 | 0.32 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C4c_ST10n7 | 1878 | -1.85 [-3.32,-0.38] | 2.08 | -2.21 | +0.69 | +297,136 | -4,197 | 0.41 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C3_KEL3 | 7339 | -1.87 [-2.90,-0.80] | 1.52 | -2.16 | -2.15 | +209,092 | -3,559 | 0.03 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD30_HM | 5271 | -1.91 [-4.08,+0.28] | 3.15 | -0.98 | +0.29 | +226,659 | +4,044 | 0.13 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C3_ST10n10 | 1864 | -1.95 [-3.89,+0.08] | 2.85 | -1.65 | -0.27 | +212,935 | -113 | 0.72 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_TD60_ST10n7 | 1878 | -1.99 [-5.62,+1.76] | 5.26 | -1.95 | -2.79 | +200,805 | -1,441 | 0.69 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_EMA5 | 1831 | -2.02 [-4.17,+0.13] | 3.09 | -2.13 | -2.49 | +394,646 | -5,588 | 0.47 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST10n7 | 1878 | -2.09 [-3.99,-0.11] | 2.77 | -1.73 | -0.30 | +156,812 | -349 | 0.73 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_ST | 7105 | -2.11 [-3.38,-0.84] | 1.83 | -1.78 | -1.32 | +3,288,109 | -26,929 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_TB7 | 898 | -2.11 [-4.97,+0.88] | 4.19 | +0.19 | +1.00 | +53,598 | -691 | 0.02 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n10 | 1864 | -2.13 [-4.30,-0.01] | 3.06 | -1.40 | -4.20 | +553,980 | -7,945 | 0.61 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_ST10n14 | 1898 | -2.16 [-4.10,-0.13] | 2.84 | -2.65 | -0.71 | +299,738 | -857 | 0.84 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n14 | 1898 | -2.17 [-3.93,-0.41] | 2.54 | -1.21 | -1.81 | +431,682 | -7,911 | 0.61 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_KEL3 | 7339 | -2.17 [-4.50,+0.24] | 3.40 | -2.89 | -1.05 | +1,333,740 | -9,526 | 0.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_ONH_ST10n7 | 1878 | -2.18 [-7.76,+3.56] | 8.03 | -0.93 | +4.88 | +61,793 | +3,295 | 0.82 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n10 | 1864 | -2.25 [-4.03,-0.48] | 2.55 | -1.27 | -2.33 | +312,392 | -6,936 | 0.41 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C3_HM | 5271 | -2.30 [-3.46,-1.12] | 1.66 | -2.36 | -1.44 | -111,647 | +100 | 0.13 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_ST10n14 | 1898 | -2.31 [-6.95,+2.53] | 6.83 | -2.22 | -0.05 | +155,420 | -308 | 0.89 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n14 | 1898 | -2.35 [-4.44,-0.22] | 3.05 | -1.74 | -3.56 | +728,529 | -8,863 | 0.54 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_ST | 7105 | -2.39 [-3.67,-1.14] | 1.80 | -2.11 | -1.87 | +3,655,823 | -29,043 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_HM | 5271 | -2.45 [-3.91,-1.00] | 2.06 | -2.71 | -0.29 | +2,213,314 | -15,409 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_60_ST10n7 | 1878 | -2.50 [-4.25,-0.72] | 2.50 | -1.13 | -0.77 | +539,536 | -6,876 | 0.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_KEL3 | 7339 | -2.60 [-3.83,-1.37] | 1.76 | -2.45 | -1.18 | +2,920,390 | -20,616 | 0.99 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C2_30_ST10n7 | 1878 | -2.60 [-4.68,-0.52] | 2.95 | -0.89 | -2.30 | +773,863 | -8,382 | 0.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_ST | 7105 | -2.66 [-3.99,-1.37] | 1.86 | -2.49 | -1.92 | +3,666,135 | -29,110 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST | 7105 | -2.68 [-7.12,+2.03] | 6.52 | -4.30 | -3.37 | +488,039 | -3,053 | 0.65 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_60_KEL3 | 7339 | -2.69 [-5.12,-0.07] | 3.59 | -3.24 | -1.48 | +1,646,366 | -11,137 | 0.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_ST10n14 | 1898 | -2.69 [-8.03,+2.83] | 7.83 | -3.70 | +0.50 | +265,979 | -301 | 0.72 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_C1_120_ST | 7105 | -2.79 [-7.91,+2.72] | 7.65 | -4.24 | -3.39 | +236,200 | -1,759 | 0.74 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_HM | 5271 | -2.83 [-4.32,-1.34] | 2.12 | -3.34 | -1.06 | +3,055,515 | -21,025 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_KEL3 | 7339 | -3.02 [-4.28,-1.75] | 1.80 | -2.36 | -0.02 | +3,075,273 | -23,810 | 0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_EMA5 | 1831 | -3.09 [-5.61,-0.53] | 3.60 | -3.45 | -0.41 | +222,876 | -5,101 | 0.14 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_120_KEL3 | 7339 | -3.13 [-6.32,+0.27] | 4.66 | -4.10 | -1.45 | +1,549,842 | -11,425 | 0.41 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_HM | 5271 | -3.21 [-4.71,-1.69] | 2.12 | -3.60 | -1.33 | +3,002,601 | -19,884 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_ST | 7105 | -3.24 [-4.60,-1.90] | 1.93 | -3.21 | -1.27 | +3,467,459 | -28,311 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_ST | 7105 | -3.24 [-4.72,-1.71] | 2.14 | -3.14 | -1.67 | +2,580,650 | -21,091 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_PSAR_ST10n7 | 1878 | -3.45 [-6.47,-0.32] | 4.39 | -2.97 | -2.08 | +362,875 | -4,421 | 0.38 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_C1_90_KEL3 | 7339 | -3.46 [-6.31,-0.44] | 4.16 | -4.45 | -1.79 | +1,595,829 | -11,234 | 0.34 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_KEL3 | 7339 | -3.54 [-4.87,-2.22] | 1.91 | -3.17 | +0.07 | +2,464,886 | -18,992 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_CH3_HM | 5271 | -3.55 [-5.13,-1.99] | 2.22 | -4.23 | -0.60 | +2,889,116 | -19,494 | 1.00 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_KEL3 | 7339 | -3.71 [-5.20,-2.17] | 2.18 | -3.55 | +0.09 | +1,993,799 | -15,761 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,2x_cost<=0,year_share>60% |
| XT_R4_CH3_ST10n7 | 1878 | -3.75 [-6.92,-0.50] | 4.61 | -4.20 | -1.92 | +266,089 | -1,984 | 0.13 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_STB_HM | 5271 | -3.93 [-5.50,-2.33] | 2.25 | -5.01 | -1.29 | +2,250,574 | -13,800 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH3_EMA5 | 1831 | -4.03 [-6.65,-1.31] | 3.83 | -4.62 | -0.89 | +283,511 | -5,374 | 0.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_ST10n7 | 1878 | -4.24 [-7.10,-1.28] | 4.15 | -3.63 | -1.25 | +383,245 | -3,908 | 0.07 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH25_EMA5 | 1831 | -4.46 [-6.95,-1.86] | 3.61 | -4.19 | -1.67 | +854,703 | -9,258 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_EMA5 | 1831 | -4.70 [-7.12,-2.21] | 3.53 | -4.41 | -1.72 | +1,139,829 | -10,865 | 0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |
| XT_R4_CH2_ST10n7 | 1878 | -4.85 [-7.41,-2.19] | 3.77 | -3.72 | -0.76 | +692,721 | -8,065 | 0.04 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0&maxDD_not_worse,SPAN2<=0,2x_cost<=0,year_share>60% |

## Caveats
* Direct L2 replay prices every stop-type and market exit; target exits are limits at the level (identical machinery for the base). Sequences use the base entry set (PB3: 7,656 of 8,339 rows after one-open-trade-per-book). Equal-risk columns / DS3 marginal Sharpe: not computed because no cell is PASS or CANDIDATE.
* Holdout (2025-07+) and the 2023 span were read once in the invalid v1 pipeline and again in v2; per-group looks are logged (…_V2). Details of each family are in DS3_TC1C2 / TC3C4 / TC5 / TC4R4 / TC6PB.
