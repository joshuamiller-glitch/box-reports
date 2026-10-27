# DS3_TPBX_B4 - T-PBX block (iv): tape / footprint pullback-end triggers (D3PX, 2026-10-27)

Research output; NOT a live recommendation. MAPPED conservative basis. 3 families x 10 triggers = 30 cells (prereg TPBX4_TAPE). Tape layer: D3BX time_1m (dupwin=1 excluded). Only PBOS and ABS are reproducible from 1-min OHLCV bars; the rest are execution-server-only.

Verdicts: {'DEAD': 30}. Paired CI above 0 (per arm vs base trigger): 0 of 30; CI above 0 vs random-in-regime: 6.

**Tape triggers: no robust cell (best PBX4_ER5_f40_SW_CLZ, +20.69 pts/trade [-11.75,+50.25] vs random-in-regime, verdict DEAD).**

| cell | exec | verdict | trigger rate | WF per-arm pts (base) | paired per arm [CI] | HOLD paired | 2023 paired | WF wk mean | HOLD wk | 2x wk | vs random-in-regime (b) [CI] rank | vs (a) rank | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX4_ER5_f40_SW_CLZ | execution server / Volumetric | DEAD | 0.02 | +0.50 (+9.50) | -9.00 [-14.51,-3.48] | -8.52 | -2.52 | +404 | +351 | +386 | +20.69 [-11.75,+50.25] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_ER5_f40_SW_ABS | NT8 1-min bar | DEAD | 0.02 | +0.47 (+9.50) | -9.03 [-14.50,-3.57] | -8.89 | -1.63 | +722 | -22 | +696 | +19.45 [-18.02,+64.02] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_ER5_f40_SW_CDBOS | execution server / Volumetric | DEAD | 0.11 | +1.52 (+9.50) | -7.97 [-13.14,-2.79] | -7.80 | +1.09 | +2,300 | +1,927 | +2,184 | +11.20 [-3.13,+25.61] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, beats_(b)_CI_includes_0 |
| PBX4_ER5_f40_SW_DIV | execution server / Volumetric | DEAD | 0.36 | +3.80 (+9.50) | -5.70 [-10.06,-1.35] | -5.84 | -0.02 | +5,484 | +4,657 | +5,094 | +8.10 [-0.06,+16.63] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_ER5_f40_SW_LP | execution server (trade rows) | DEAD | 0.14 | +1.57 (+9.50) | -7.93 [-13.17,-2.68] | -8.82 | -0.69 | +1,797 | +86 | +1,678 | +8.03 [-8.63,+24.38] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_ER5_f40_SW_RUN | execution server (trade rows) | DEAD | 0.81 | +8.51 (+9.50) | -0.98 [-3.84,+1.84] | -0.42 | +1.86 | +7,265 | +7,296 | +6,652 | +6.57 [+0.54,+12.81] r1.00 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse |
| PBX4_ER5_f40_SW_DFLIP | execution server / Volumetric | DEAD | 0.80 | +8.08 (+9.50) | -1.42 [-3.94,+1.09] | -1.42 | +1.73 | +7,179 | +5,698 | +6,559 | +5.92 [+0.33,+11.79] r0.94 | r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX4_PBS_f60_T3_STK | execution server / Volumetric | DEAD | 0.26 | +0.72 (+0.70) | +0.02 [-2.47,+2.46] | +0.54 | -0.29 | +11,056 | +13,693 | +8,679 | +5.20 [+2.56,+7.69] r1.00 | r1.00 | neighbours_agree, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_PBS_f60_T3_CLZ | execution server / Volumetric | DEAD | 0.03 | -0.11 (+0.70) | -0.81 [-3.81,+2.17] | -0.11 | -0.75 | -636 | -455 | -821 | +4.96 [-5.26,+14.90] r0.94 | r0.94 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PBS_f60_T3_LP | execution server (trade rows) | DEAD | 0.13 | +0.49 (+0.70) | -0.21 [-3.13,+2.67] | +0.69 | -1.09 | +5,264 | +11,200 | +3,568 | +4.44 [+0.19,+8.79] r1.00 | r1.00 | mean_up, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_PBS_f60_T3_RUN | execution server (trade rows) | DEAD | 0.84 | +1.34 (+0.70) | +0.64 [-0.35,+1.60] | +1.21 | +0.24 | +9,267 | +16,252 | +7,574 | +2.77 [+0.86,+4.67] r1.00 | r1.00 | neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PBS_f60_T3_DFLIP | execution server / Volumetric | DEAD | 0.56 | +1.26 (+0.70) | +0.56 [-0.96,+2.07] | +1.63 | +0.45 | +7,468 | +15,780 | +4,740 | +2.62 [+0.43,+4.95] r1.00 | r1.00 | neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PBS_f60_T3_CDBOS | execution server / Volumetric | DEAD | 0.29 | +0.65 (+0.70) | -0.04 [-2.29,+2.17] | +1.06 | -0.14 | +10,952 | +19,585 | +8,781 | +2.29 [-0.77,+5.30] r1.00 | r1.00 | mean_up, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0, beats_(b)_CI_includes_0 |
| PBX4_PB3_f60_T3_CLZ | execution server / Volumetric | DEAD | 0.04 | -0.12 (+1.25) | -1.37 [-3.75,+0.96] | -1.27 | -1.79 | -913 | +573 | -1,309 | +1.97 [-2.74,+7.42] r0.81 | r0.81 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PBS_f60_T3_DIV | execution server / Volumetric | DEAD | 0.14 | +0.41 (+0.70) | -0.28 [-2.94,+2.35] | +1.00 | -0.36 | +1,160 | +4,747 | -668 | +1.37 [-2.79,+5.60] r0.88 | r1.00 | mean_up, placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_ABS | NT8 1-min bar | DEAD | 0.02 | +0.07 (+1.25) | -1.18 [-3.56,+1.20] | -1.17 | -2.21 | +2,738 | -52 | +1,418 | +1.25 [-4.12,+6.45] r0.81 | r0.81 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_DFLIP | execution server / Volumetric | DEAD | 0.85 | +1.19 (+1.25) | -0.06 [-0.55,+0.43] | +0.00 | -0.06 | +9,604 | +10,620 | +7,650 | +1.11 [-0.54,+2.70] r0.88 | r0.94 | mean_up, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_PB3_f60_T3_STK | execution server / Volumetric | DEAD | 0.33 | +0.45 (+1.25) | -0.80 [-2.67,+1.00] | -0.86 | -1.41 | +4,370 | +273 | +2,393 | +1.11 [-0.63,+2.93] r0.94 | r0.75 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX4_PBS_f60_T3_BOOK | execution server (book) | DEAD | 0.25 | +0.55 (+0.70) | -0.15 [-2.41,+2.11] | -0.07 | -0.37 | +7,240 | +6,319 | +5,114 | +0.98 [-2.38,+4.26] r0.75 | r0.88 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PBS_f60_T3_PBOS | NT8 1-min bar | DEAD | 0.26 | +0.41 (+0.70) | -0.29 [-2.65,+2.04] | +0.94 | -0.36 | +5,966 | +10,599 | +4,272 | +0.82 [-2.22,+3.82] r0.81 | r0.81 | mean_up, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_PB3_f60_T3_PBOS | NT8 1-min bar | DEAD | 0.24 | +0.20 (+1.25) | -1.05 [-2.84,+0.72] | -1.08 | -1.68 | +7,619 | +3,529 | +5,741 | +0.45 [-1.63,+2.57] r0.75 | r1.00 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_CDBOS | execution server / Volumetric | DEAD | 0.33 | +0.24 (+1.25) | -1.01 [-2.61,+0.57] | -0.84 | -1.08 | +6,154 | +2,885 | +4,083 | +0.16 [-1.83,+2.10] r0.50 | r0.81 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_ER5_f40_SW_BOOK | execution server (book) | DEAD | 0.19 | +1.43 (+9.50) | -8.06 [-13.08,-2.82] | -8.07 | -0.30 | +940 | +274 | +746 | -0.11 [-9.94,+9.92] r0.50 | r0.81 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_LP | execution server (trade rows) | DEAD | 0.15 | +0.28 (+1.25) | -0.97 [-3.26,+1.28] | -1.21 | -1.78 | +7,324 | +2,172 | +4,725 | -0.33 [-3.10,+2.70] r0.38 | r0.12 | mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree |
| PBX4_PBS_f60_T3_ABS | NT8 1-min bar | DEAD | 0.02 | +0.12 (+0.70) | -0.58 [-3.56,+2.40] | -0.04 | -0.85 | +1,756 | +2,186 | +1,163 | -0.53 [-7.77,+6.73] r0.44 | r0.69 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_DIV | execution server / Volumetric | DEAD | 0.22 | +0.20 (+1.25) | -1.05 [-3.04,+0.91] | -1.14 | -2.10 | +1,421 | -360 | -252 | -0.59 [-2.24,+1.20] r0.19 | r0.88 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_RUN | execution server (trade rows) | DEAD | 0.79 | +1.33 (+1.25) | +0.08 [-0.67,+0.82] | +0.16 | -0.52 | +7,268 | +4,134 | +5,907 | -0.76 [-2.30,+0.86] r0.06 | r0.69 | placebo>=0.90, neighbours_agree, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX4_ER5_f40_SW_STK | execution server / Volumetric | DEAD | 0.28 | +0.38 (+9.50) | -9.12 [-14.07,-4.20] | -10.15 | -0.42 | +714 | -1,985 | +405 | -1.63 [-11.00,+7.94] r0.31 | r0.62 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_PB3_f60_T3_BOOK | execution server (book) | DEAD | 0.26 | +0.31 (+1.25) | -0.94 [-2.74,+0.81] | -1.16 | -1.30 | -624 | -6,185 | -2,476 | -2.08 [-4.56,+0.36] r0.00 | r0.31 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX4_ER5_f40_SW_PBOS | NT8 1-min bar | DEAD | 0.07 | +0.02 (+9.50) | -9.47 [-14.80,-4.12] | -8.65 | -0.06 | +6 | +374 | -75 | -2.12 [-17.52,+13.70] r0.12 | r0.69 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |

## Trigger axis (mean over the 3 families)

| trigger | mean paired per arm | mean effect vs random-in-regime | mean trigger rate |
|---|---|---|---|
| ABS | -3.60 | +6.72 | 0.02 |
| BOOK | -3.05 | -0.40 | 0.23 |
| CDBOS | -3.01 | +4.55 | 0.24 |
| CLZ | -3.73 | +9.21 | 0.03 |
| DFLIP | -0.30 | +3.22 | 0.74 |
| DIV | -2.34 | +2.96 | 0.24 |
| LP | -3.04 | +4.04 | 0.14 |
| PBOS | -3.60 | -0.28 | 0.19 |
| RUN | -0.09 | +2.86 | 0.81 |
| STK | -3.30 | +1.56 | 0.29 |
