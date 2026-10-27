# DS3_TPBX_B3B - T-PBX block (iii-b): entry order types (D3PX, 2026-10-27)

Research output; NOT a live recommendation. MAPPED conservative basis; limit fills by 1-tick trade-through on the 1-s path (no queue model; the real-book queue replay was NOT run, so limit fill rates are upper bounds), stop-entry mapped without slippage. Four cells x six order types = 24 cells (prereg TPBX3B_TOUCH).

Verdicts: {'DEAD': 12, 'CONTROL (base)': 4}. Cells with paired CI (vs market, per arm) above 0: 0 of 12; CI vs random-in-regime above 0: 0.

**Order types: no robust cell (best PBX3_ER5_f40_SW_L10T, +5.62 pts/trade [-0.82,+12.40] vs random-in-regime, fill rate 0.73, verdict DEAD).**

| cell | verdict | fill rate | WF per-arm pts (M) | paired per arm vs M [CI] | HOLD paired | 2023 paired | WF wk mean / SD / maxDD | HOLD wk | 2x wk | vs random-in-regime (b) [CI] rank | vs timing-destroyed (a) rank | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX3_PBS_f60_SW_M | CONTROL (base) | 0.93 | +1.83 (+1.83) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +11,483 / 59,968 / 433,483 | +12,707 | +9,073 | +1.77 [+0.10,+3.38] r0.94 | +3.51 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_SW_L10T | DEAD | 0.61 | +0.85 (+1.83) | -0.98 [-1.96,+0.02] | -0.76 | -1.26 | +6,912 / 57,213 / 595,552 | +7,401 | +4,806 | +1.11 [-0.47,+2.53] r0.94 | +3.06 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_PBS_f60_SW_L30T | DEAD | 0.62 | +0.86 (+1.83) | -0.97 [-1.93,+0.01] | -0.73 | -1.27 | +7,570 / 57,135 / 551,399 | +8,267 | +5,130 | +1.23 [-0.34,+2.68] r0.94 | +3.12 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_PBS_f60_SW_LADT | DEAD | 0.62 | +0.72 (+1.83) | -1.11 [-2.42,+0.22] | -0.64 | -2.04 | +1,173 / 25,517 / 300,212 | +1,460 | +562 | +1.08 [-0.79,+2.86] r0.88 | +3.07 r1.00 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_T3_M | CONTROL (base) | 0.93 | +0.70 (+0.70) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +7,841 / 61,150 / 502,792 | +12,257 | +5,596 | +2.17 [+0.26,+4.02] r0.94 | +3.91 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PBS_f60_T3_L10T | DEAD | 0.61 | +0.41 (+0.70) | -0.29 [-1.69,+1.06] | +0.22 | -0.23 | +3,376 / 51,421 / 638,126 | +10,437 | +2,074 | +1.55 [-0.43,+3.54] r0.94 | +3.41 r0.94 | mean_up, paired_CI_excludes0&maxDD_not_worse, placebo<0.95, SPAN2<=0 |
| PBX3_PBS_f60_T3_L30T | DEAD | 0.62 | +0.38 (+0.70) | -0.32 [-1.70,+1.01] | +0.24 | -0.13 | +3,735 / 51,155 / 601,377 | +11,103 | +2,422 | +1.43 [-0.64,+3.45] r0.94 | +3.46 r0.94 | mean_up, paired_CI_excludes0&maxDD_not_worse, placebo<0.95, SPAN2<=0 |
| PBX3_PBS_f60_T3_LADT | DEAD | 0.62 | +0.50 (+0.70) | -0.19 [-2.20,+1.77] | +0.57 | -0.84 | +482 / 25,309 / 355,761 | +3,642 | -97 | +0.90 [-1.72,+3.54] r0.88 | +2.87 r0.94 | mean_up, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse, SPAN2<=0 |
| PBX3_ER5_f40_SW_M | CONTROL (base) | 0.92 | +9.50 (+9.50) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +5,607 / 27,205 / 212,674 | +5,200 | +5,046 | +5.29 [+0.26,+10.51] r1.00 | +8.03 r1.00 | mean_up, holdout_sign_agrees, neighbours_agree, paired_CI_excludes0&maxDD_not_worse |
| PBX3_ER5_f40_SW_L10T | DEAD | 0.73 | +4.12 (+9.50) | -5.38 [-8.57,-2.06] | -6.37 | -1.95 | +4,835 / 28,724 / 360,510 | +2,623 | +4,271 | +5.62 [-0.82,+12.40] r0.94 | +7.85 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_ER5_f40_SW_L30T | DEAD | 0.73 | +4.12 (+9.50) | -5.38 [-8.57,-2.06] | -6.37 | -1.95 | +4,835 / 28,724 / 360,510 | +2,623 | +4,271 | +5.45 [-1.02,+12.24] r0.94 | +7.83 r1.00 | mean_up, holdout_sign_agrees, paired_CI_excludes0&maxDD_not_worse, placebo<0.95 |
| PBX3_ER5_f40_SW_LADT | DEAD | 0.73 | +1.28 (+9.50) | -8.22 [-12.10,-4.24] | -9.14 | +0.67 | +1,451 / 14,961 / 238,484 | +141 | +1,213 | +2.21 [-5.44,+9.77] r0.81 | +4.37 r0.94 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_M | CONTROL (base) | 0.81 | +1.25 (+1.25) | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +3,876 / 50,238 / 504,891 | -1,262 | +1,694 | -1.02 [-2.79,+0.63] r0.12 | +0.70 r0.62 | mean_up, holdout_sign_agrees, placebo>=0.90, neighbours_agree |
| PBX3_PB3_f60_T3_L10T | DEAD | 0.78 | -0.44 (+1.25) | -1.69 [-2.31,-1.09] | -1.73 | -0.95 | +747 / 54,373 / 625,074 | +2,318 | -753 | -3.23 [-4.70,-1.91] r0.00 | -1.82 r0.06 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_L30T | DEAD | 0.78 | -0.44 (+1.25) | -1.69 [-2.30,-1.09] | -1.74 | -0.95 | +1,009 / 54,422 / 587,665 | +2,860 | -495 | -3.15 [-4.60,-1.81] r0.00 | -1.76 r0.06 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |
| PBX3_PB3_f60_T3_LADT | DEAD | 0.78 | -0.04 (+1.25) | -1.29 [-2.51,-0.08] | -1.45 | -2.04 | +360 / 22,797 / 258,970 | +25 | -59 | -3.87 [-5.83,-1.95] r0.00 | -3.13 r0.00 | mean_up, holdout_sign_agrees, placebo>=0.90, paired_CI_excludes0&maxDD_not_worse |

## Order-type axis (mean over the 4 cells)

| order type | mean paired per arm vs M | mean effect vs random-in-regime | mean fill rate |
|---|---|---|---|
| L10T | -2.09 | +1.26 | 0.68 |
| L30T | -2.09 | +1.24 | 0.69 |
| LADT | -2.70 | +0.08 | 0.69 |
