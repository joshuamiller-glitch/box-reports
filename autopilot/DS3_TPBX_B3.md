# DS3_TPBX_B3 - T-PBX block (iii): entry order types (D3PX, 2026-10-27)

Research output; NOT a live recommendation. MAPPED conservative basis; limit fills by 1-tick trade-through on the 1-s path (no queue model; the real-book queue replay was NOT run, so limit fill rates are upper bounds), stop-entry mapped without slippage. Four cells x six order types = 24 cells (prereg TPBX3_ORD).

Verdicts: {'DEAD': 20, 'CONTROL (base)': 4}. Cells with paired CI (vs market, per arm) above 0: 0 of 20; CI vs random-in-regime above 0: 5.

**Order types: no robust cell (best PBX3_ER5_f40_SW_SC, +9.40 pts/trade [+4.59,+14.58] vs random-in-regime, fill rate 0.92, verdict DEAD).**

| cell | verdict | fill rate | WF per-arm pts (M) | paired per arm vs M [CI] | HOLD paired | 2023 paired | WF wk mean / SD / maxDD | HOLD wk | 2x wk | vs random-in-regime (b) [CI] rank | vs timing-destroyed (a) rank | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX3_PBS_f60_SW_M | CONTROL (base) | 0.93 | +1.83 (+1.83) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +11,483 / 59,968 / 433,483 | +12,707 | +9,073 | +1.77 [+0.10,+3.38] r0.94 | +3.51 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_SW_L10 | DEAD | 0.60 | +0.82 (+1.83) | -1.02 [-2.01,-0.01] | -0.82 | -1.51 | +6,468 / 56,426 / 595,892 | +7,023 | +4,495 | +1.17 [-0.42,+2.68] r0.94 | +3.19 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_PBS_f60_SW_L30 | DEAD | 0.61 | +0.81 (+1.83) | -1.02 [-1.99,-0.01] | -0.78 | -1.43 | +6,917 / 56,429 / 593,351 | +7,629 | +4,606 | +1.29 [-0.29,+2.79] r0.94 | +3.20 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_PBS_f60_SW_SE | DEAD | 0.45 | +0.91 (+1.83) | -0.93 [-2.22,+0.33] | -0.52 | -0.96 | +13,855 / 53,196 / 346,311 | +17,231 | +12,898 | +2.28 [+0.60,+3.91] r1.00 | +4.00 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_SW_LAD | DEAD | 0.61 | +0.65 (+1.83) | -1.19 [-2.51,+0.15] | -0.72 | -2.12 | +723 / 24,972 / 307,175 | -135 | +104 | +1.09 [-0.84,+2.94] r0.88 | +3.09 r1.00 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_SW_SC | DEAD | 0.94 | -0.73 (+1.83) | -2.56 [-2.86,-2.27] | -2.88 | -1.51 | -989 / 31,942 / 483,061 | +520 | -1,690 | +0.74 [-0.80,+2.14] r0.88 | +2.12 r1.00 | mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree |
| PBX3_PBS_f60_T3_M | CONTROL (base) | 0.93 | +0.70 (+0.70) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +7,841 / 61,150 / 502,792 | +12,257 | +5,596 | +2.17 [+0.26,+4.02] r0.94 | +3.91 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_T3_L10 | DEAD | 0.60 | +0.42 (+0.70) | -0.28 [-1.71,+1.10] | +0.22 | -0.28 | +3,358 / 51,531 / 641,236 | +10,436 | +2,083 | +1.55 [-0.40,+3.52] r0.94 | +3.47 r0.94 | mean_up, paired_CI_excludes0&maxDD_not_worse, placebo<0.95, SPAN2<=0 |
| PBX3_PBS_f60_T3_L30 | DEAD | 0.61 | +0.37 (+0.70) | -0.33 [-1.74,+1.02] | +0.24 | -0.09 | +3,634 / 51,291 / 616,373 | +11,101 | +2,349 | +1.47 [-0.54,+3.45] r0.94 | +3.51 r0.94 | mean_up, paired_CI_excludes0&maxDD_not_worse, placebo<0.95, SPAN2<=0 |
| PBX3_PBS_f60_T3_SE | DEAD | 0.45 | +1.14 (+0.70) | +0.44 [-1.41,+2.22] | +1.62 | -0.49 | +11,659 / 53,604 / 319,095 | +20,942 | +9,599 | +4.58 [+2.37,+6.80] r1.00 | +6.39 r1.00 | neighbours_agree, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX3_PBS_f60_T3_LAD | DEAD | 0.61 | +0.45 (+0.70) | -0.24 [-2.28,+1.77] | +0.52 | -0.86 | +389 / 25,385 / 369,775 | +3,855 | -215 | +1.05 [-1.63,+3.75] r0.88 | +3.10 r0.94 | mean_up, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX3_PBS_f60_T3_SC | DEAD | 0.94 | -1.86 (+0.70) | -2.55 [-2.93,-2.20] | -2.90 | -1.61 | -1,831 / 29,623 / 427,042 | -3,484 | -2,313 | +2.17 [+0.16,+4.18] r0.94 | +3.94 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_ER5_f40_SW_M | CONTROL (base) | 0.92 | +9.50 (+9.50) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +5,607 / 27,205 / 212,674 | +5,200 | +5,046 | +5.29 [+0.26,+10.51] r1.00 | +8.03 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_ER5_f40_SW_L10 | DEAD | 0.70 | +3.69 (+9.50) | -5.81 [-9.09,-2.40] | -7.15 | -2.37 | +4,879 / 28,720 / 362,057 | +2,775 | +4,323 | +6.06 [-0.50,+12.93] r0.94 | +8.15 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_ER5_f40_SW_L30 | DEAD | 0.70 | +3.69 (+9.50) | -5.81 [-9.09,-2.40] | -7.15 | -2.37 | +4,879 / 28,720 / 362,057 | +2,775 | +4,323 | +5.90 [-0.62,+12.70] r0.94 | +8.21 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_ER5_f40_SW_SE | DEAD | 0.28 | +1.22 (+9.50) | -8.28 [-12.71,-3.77] | -7.63 | +1.53 | +1,994 / 16,211 / 110,572 | +2,317 | +1,756 | +1.07 [-7.47,+9.79] r0.75 | +3.46 r0.88 | mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree |
| PBX3_ER5_f40_SW_LAD | DEAD | 0.70 | +1.19 (+9.50) | -8.30 [-12.21,-4.30] | -9.33 | +0.46 | +1,453 / 14,676 / 229,876 | +473 | +1,224 | +2.79 [-5.02,+10.60] r0.94 | +4.90 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_ER5_f40_SW_SC | DEAD | 0.92 | +9.04 (+9.50) | -0.46 [-1.83,+0.99] | -0.35 | +0.24 | +4,503 / 20,847 / 141,776 | +3,748 | +4,119 | +9.40 [+4.59,+14.58] r1.00 | +12.01 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_M | CONTROL (base) | 0.81 | +1.25 (+1.25) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +3,876 / 50,238 / 504,891 | -1,262 | +1,694 | -1.02 [-2.79,+0.63] r0.12 | +0.70 r0.62 | mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree |
| PBX3_PB3_f60_T3_L10 | DEAD | 0.76 | -0.54 (+1.25) | -1.79 [-2.44,-1.15] | -1.90 | -1.15 | +1,250 / 54,208 / 592,915 | +3,033 | -262 | -3.06 [-4.51,-1.69] r0.00 | -1.62 r0.12 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_L30 | DEAD | 0.76 | -0.54 (+1.25) | -1.79 [-2.44,-1.15] | -1.91 | -1.14 | +1,512 / 54,424 / 555,505 | +3,575 | -4 | -3.00 [-4.48,-1.62] r0.00 | -1.58 r0.12 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_SE | DEAD | 0.82 | +1.25 (+1.25) | +0.00 [-0.20,+0.20] | +0.07 | +0.15 | +6,439 / 52,829 / 414,388 | +1,494 | +4,404 | -1.64 [-3.45,-0.02] r0.00 | -0.67 r0.25 | placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, beats_(b)_CI_includes_0 |
| PBX3_PB3_f60_T3_LAD | DEAD | 0.76 | -0.12 (+1.25) | -1.37 [-2.63,-0.13] | -1.57 | -2.19 | +88 / 23,035 / 259,945 | -613 | -347 | -3.75 [-5.66,-1.81] r0.00 | -3.05 r0.00 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_SC | DEAD | 0.82 | +0.68 (+1.25) | -0.57 [-0.94,-0.20] | -0.45 | -0.50 | +2,738 / 30,230 / 314,933 | +5,783 | +1,996 | +2.71 [+1.01,+4.32] r1.00 | +4.41 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |

## Order-type axis (mean over the 4 cells)

| order type | mean paired per arm vs M | mean effect vs random-in-regime | mean fill rate |
|---|---|---|---|
| L10 | -2.22 | +1.43 | 0.66 |
| L30 | -2.24 | +1.41 | 0.67 |
| LAD | -2.78 | +0.30 | 0.67 |
| SC | -1.54 | +3.75 | 0.90 |
| SE | -2.19 | +1.57 | 0.50 |
