# DS3 T-WASHOUT pre-holdout text (D3WO) - written 2026-10-27T11:28Z
Stage 1 = WF-PRE (2024-02..2025-06) only. 1488 cells in 64 preregs (combined prereg sha256 27750978d92cbabefe0ff7ba6103b6a963f7ec56a9a2def78e4a7246c462c570), 32 entries. Truncation/poison audit: 120 family x bar-size x parameter combos, 0 mismatches (out/WO/trunc_audit.json).
Cells with PRE lift > 0: 502; placebo rank >= 0.90: 71; >= 0.95: 27; paired CI lower bound > 0: 19; beats the entry's best-of-N placebo p95: 8. Mean PRE lift by family: cci -0.28, pb +0.01, rsi -0.73 pt/trade; mean mirror lift (entries without washout): cci -0.04, pb +2.86, rsi +0.05.
FINALISTS (rule: PRE lift_kept > 0 and placebo rank >= 0.90): 71 cells, listed below. Only these cells get the one holdout look (2025-07+) and the second-span look (2023-04..2024-01); all other cells are DEAD on the pre-holdout screen (no holdout number computed for them).

| cell | take | n kept | PRE lift pt [CI] | mirror lift | plc | nb agree | beats bestN | PRE wk d$ |
|--|--|--|--|--|--|--|--|--|
| WO_PB3E_R3_P2_40_1.5R_rsi_b5_k10 | 0.02 | 42 | +15.23 [+1.50,+30.30] | -0.36 | 0.98 | True | True | -11190 |
| WO_PB3D_R3_P2_rsi_b5_k10 | 0.02 | 37 | +13.35 [-3.71,+30.63] | -0.34 | 0.91 | True | False | -10270 |
| WO_PB3E_R3_P2_40_1.5R_rsi_b2_k18 | 0.03 | 51 | +9.17 [-5.00,+24.62] | -0.27 | 0.91 | False | False | -11572 |
| WO_KB_rsi_b3_k10 | 0.05 | 166 | +7.92 [-1.14,+15.93] | -0.45 | 0.98 | True | True | -15784 |
| WO_PRO2_RIB1m_q30_cci_b1_n40_k10 | 0.25 | 507 | +5.21 [+0.83,+9.74] | -1.70 | 0.99 | True | False | +3788 |
| WO_HM_cci_b1_n40_k10 | 0.18 | 422 | +5.19 [+0.38,+9.96] | -1.18 | 0.98 | True | False | -2512 |
| WO_HM_cci_b1_n40_k18 | 0.19 | 434 | +5.15 [+0.49,+9.85] | -1.21 | 0.98 | True | False | -2279 |
| WO_TE1_kelt_3m_rsi_b3_k18 | 0.08 | 232 | +4.87 [-2.12,+12.13] | -0.45 | 0.91 | False | False | -14680 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b5_k10 | 0.08 | 226 | +4.62 [-2.31,+11.90] | -0.42 | 0.92 | True | False | -10692 |
| WO_TE7_kelt3m_n20_m1.0_rsi_b5_k10 | 0.09 | 278 | +4.61 [-1.81,+10.87] | -0.48 | 0.93 | True | False | -15576 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b3_k18 | 0.12 | 332 | +4.23 [-1.36,+10.19] | -0.59 | 0.92 | True | False | -9614 |
| WO_PRO2_RIB1m_q30_cci_b1_n14_k10 | 0.38 | 776 | +4.04 [+0.86,+7.23] | -2.45 | 1.00 | True | False | +5281 |
| WO_PB3D_R3_P2_rsi_b5_k30 | 0.18 | 267 | +4.03 [-2.01,+10.31] | -0.87 | 0.90 | True | False | -6767 |
| WO_TE7_boll3m_n30_m1.5_rsi_b5_k18 | 0.15 | 426 | +3.91 [-0.93,+8.71] | -0.72 | 0.94 | False | False | -9036 |
| WO_PRO2_RIB1m_q30_cci_b1_n27_k10 | 0.32 | 665 | +3.74 [+0.20,+7.23] | -1.79 | 0.98 | True | False | +3720 |
| WO_HM_cci_b1_n27_k10 | 0.28 | 639 | +3.72 [-0.27,+7.38] | -1.44 | 0.97 | True | False | -194 |
| WO_PRO2_RIB1m_q30_cci_b1_n20_k10 | 0.35 | 718 | +3.67 [+0.16,+7.17] | -1.97 | 0.99 | True | False | +3341 |
| WO_TE7_boll3m_n20_m1.5_rsi_b3_k18 | 0.13 | 398 | +3.59 [-1.23,+8.10] | -0.54 | 0.93 | False | False | -5514 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b5_k18 | 0.17 | 463 | +3.36 [-1.16,+8.24] | -0.69 | 0.92 | True | False | -7416 |
| WO_TE1B_boll_3m_rsi_b3_k30 | 0.21 | 532 | +3.14 [-1.24,+7.58] | -0.82 | 0.93 | True | False | -7832 |
| WO_HM_cci_b1_n27_k18 | 0.29 | 667 | +3.00 [-0.87,+6.67] | -1.24 | 0.94 | True | False | -548 |
| WO_HM_cci_b1_n20_k10 | 0.39 | 895 | +2.97 [+0.23,+5.73] | -1.91 | 0.98 | True | False | +2482 |
| WO_TE1_kelt_3m_cci_b5_n40_k10 | 0.24 | 650 | +2.96 [-0.68,+6.70] | -0.92 | 0.94 | True | False | -10387 |
| WO_HM_cci_b1_n40_k30 | 0.26 | 585 | +2.91 [-1.08,+6.99] | -1.00 | 0.92 | True | False | -3240 |
| WO_TE7_kelt3m_n30_m1.0_rsi_b3_k30 | 0.23 | 614 | +2.78 [-1.35,+7.28] | -0.81 | 0.92 | True | False | -7696 |
| WO_PRO2_Z60_t1.0_rsi_b5_k30 | 0.23 | 718 | +2.77 [-0.87,+6.36] | -0.83 | 0.94 | False | False | -2939 |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n40_k10 | 0.25 | 668 | +2.65 [-0.86,+6.50] | -0.89 | 0.91 | True | False | -10016 |
| WO_HM_cci_b1_n14_k10 | 0.49 | 1121 | +2.64 [+0.31,+4.97] | -2.54 | 0.99 | True | False | +3909 |
| WO_PRO2_RIB1m_q30_cci_b1_n20_k18 | 0.66 | 1351 | +2.61 [+1.04,+4.34] | -5.00 | 1.00 | True | False | +9996 |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n20_k10 | 0.31 | 851 | +2.57 [-0.57,+5.75] | -1.17 | 0.95 | True | False | -3839 |
| WO_TE7_kelt3m_n30_m1.0_cci_b5_n40_k10 | 0.29 | 792 | +2.48 [-0.78,+5.84] | -1.02 | 0.94 | True | False | -5694 |
| WO_HM_cci_b1_n27_k30 | 0.37 | 848 | +2.41 [-0.90,+5.58] | -1.42 | 0.93 | True | False | +349 |
| WO_PRO2_ER4_EMA5_cci_b1_n40_k18 | 0.80 | 440 | +2.36 [+0.11,+4.77] | -9.21 | 0.97 | True | False | +1536 |
| WO_SM_cci_b5_n27_k18 | 0.59 | 534 | +2.29 [-0.59,+5.33] | -3.31 | 0.91 | True | False | -814 |
| WO_HM_cci_b1_n20_k30 | 0.52 | 1193 | +2.21 [-0.08,+4.39] | -2.41 | 0.97 | True | False | +1408 |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n40_k18 | 0.40 | 1064 | +2.20 [-0.47,+4.88] | -1.46 | 0.95 | True | False | -6146 |
| WO_TE6_st10m_n14_m3.0_cci_b10_n40_k10 | 0.59 | 542 | +2.07 [-0.98,+5.24] | -2.95 | 0.91 | True | False | -1562 |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n27_k18 | 0.46 | 1228 | +2.03 [-0.21,+4.26] | -1.73 | 0.96 | False | False | -4332 |
| WO_PB3E_R3_P2_40_1.5R_cci_b2_n20_k18 | 0.66 | 1191 | +1.92 [+0.45,+3.42] | -3.79 | 0.99 | True | False | +2355 |
| WO_PB3E_R3_P2_40_1.5R_cci_b2_n27_k18 | 0.53 | 955 | +1.90 [-0.15,+3.96] | -2.16 | 0.97 | True | False | -748 |
| WO_PB3E_R3_P2_40_1.5R_cci_b2_n40_k18 | 0.35 | 636 | +1.88 [-1.11,+4.95] | -1.03 | 0.90 | True | False | -5119 |
| WO_PB3E_R3_P2_40_1.5R_cci_b2_n27_k10 | 0.40 | 721 | +1.85 [-0.81,+4.48] | -1.24 | 0.92 | True | False | -4132 |
| WO_TE7_kelt3m_n14_m1.5_cci_b3_n27_k18 | 0.38 | 1000 | +1.84 [-1.08,+4.76] | -1.10 | 0.90 | False | False | -8673 |
| WO_PRO2_RIB1m_q30_cci_b1_n14_k18 | 0.72 | 1489 | +1.83 [+0.33,+3.30] | -4.79 | 0.99 | True | False | +6607 |
| WO_TE6_st10m_n10_m3.5_cci_b10_n27_k18 | 0.73 | 576 | +1.80 [-0.52,+4.06] | -4.86 | 0.92 | True | False | +364 |
| WO_TE7_kelt3m_n14_m1.5_cci_b3_n40_k30 | 0.49 | 1312 | +1.79 [-0.22,+3.88] | -1.74 | 0.96 | True | False | -3072 |
| WO_PRO2_RIB1m_q30_cci_b1_n27_k18 | 0.59 | 1216 | +1.74 [-0.14,+3.75] | -2.52 | 0.95 | True | False | +4629 |
| WO_PB3E_R3_P2_40_1.5R_cci_b5_n14_k10 | 0.45 | 799 | +1.74 [-0.84,+4.45] | -1.40 | 0.93 | True | False | -3771 |
| WO_TE6_st10m_n10_m3.5_cci_b10_n20_k18 | 0.74 | 583 | +1.73 [-0.58,+4.08] | -4.89 | 0.92 | False | False | +217 |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n14_k10 | 0.45 | 1239 | +1.65 [-0.60,+4.03] | -1.37 | 0.93 | True | False | -2178 |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n20_k18 | 0.50 | 1373 | +1.59 [-0.52,+3.79] | -1.61 | 0.94 | True | False | -1503 |
| WO_SM_cci_b10_n20_k18 | 0.80 | 719 | +1.58 [-0.16,+3.55] | -6.12 | 0.93 | False | False | +523 |
| WO_HM_cci_b1_n14_k30 | 0.71 | 1631 | +1.56 [+0.03,+3.03] | -3.89 | 0.97 | True | False | +2104 |
| WO_TE7_kelt3m_n14_m1.5_cci_b5_n20_k18 | 0.51 | 1369 | +1.51 [-0.46,+3.61] | -1.60 | 0.93 | False | False | -4925 |
| WO_TE7_kelt3m_n14_m1.5_cci_b3_n20_k30 | 0.69 | 1832 | +1.38 [-0.03,+2.74] | -3.04 | 0.97 | True | False | -3114 |
| WO_PRO2_ER4_EMA5_cci_b1_n27_k18 | 0.89 | 494 | +1.37 [-0.45,+3.13] | -11.46 | 0.95 | True | False | +1298 |
| WO_PRO2_ER4_EMA5_cci_b1_n40_k30 | 0.85 | 468 | +1.36 [-0.50,+3.18] | -7.49 | 0.91 | True | False | +772 |
| WO_PRO2_KAL_k0.0_cci_b1_n20_k30 | 0.57 | 2208 | +1.32 [-0.25,+2.80] | -1.73 | 0.95 | True | False | +789 |
| WO_TE6_st10m_n14_m3.0_cci_b10_n27_k18 | 0.79 | 727 | +1.30 [-0.61,+3.33] | -4.86 | 0.90 | True | False | +438 |
| WO_ST_cci_b1_n14_k10 | 0.59 | 1778 | +1.24 [-0.53,+2.94] | -1.77 | 0.92 | True | False | -4846 |
| WO_TE7_kelt3m_n30_m1.0_cci_b3_n14_k18 | 0.67 | 1826 | +1.02 [-0.43,+2.57] | -2.08 | 0.91 | True | False | +1802 |
| WO_PRO2_RIB1m_q30_cci_b1_n20_k30 | 0.88 | 1804 | +0.99 [+0.07,+1.96] | -7.08 | 0.99 | True | False | +5201 |
| WO_TE7_boll3m_n20_m1.5_pb_b5_x1.5_k10 | 0.82 | 2497 | +0.98 [+0.03,+1.96] | -4.53 | 0.98 | True | False | +5519 |
| WO_PRO2_KAL_k0.0_cci_b1_n14_k30 | 0.71 | 2759 | +0.74 [-0.42,+1.87] | -1.80 | 0.91 | False | False | +1333 |
| WO_PRO2_RIB1m_q30_pb_b1_x1.5_k10 | 0.88 | 1801 | +0.70 [-0.17,+1.58] | -4.90 | 0.93 | True | False | +716 |
| WO_TE7_boll3m_n20_m1.5_pb_b3_x1.5_k10 | 0.84 | 2564 | +0.61 [-0.21,+1.43] | -3.31 | 0.92 | True | False | -464 |
| WO_KB_pb_b3_x1.5_k10 | 0.87 | 2686 | +0.60 [-0.25,+1.37] | -3.94 | 0.93 | False | False | -136 |
| WO_PB3E_R3_P2_40_1.5R_cci_b2_n20_k30 | 0.85 | 1520 | +0.56 [-0.39,+1.49] | -3.08 | 0.91 | True | False | +671 |
| WO_PB3D_R3_P2_pb_b5_x1.5_k10 | 0.94 | 1417 | +0.53 [-0.20,+1.26] | -8.03 | 0.91 | False | False | +1317 |
| WO_TE7_kelt3m_n20_m1.0_pb_b3_x1.5_k18 | 0.99 | 2909 | +0.24 [+0.01,+0.45] | -21.15 | 0.98 | False | False | -121 |
| WO_PB3B_R5_P1_pb_b5_x1.5_k18 | 0.99 | 3014 | +0.20 [-0.02,+0.43] | -16.99 | 0.96 | False | False | +1186 |

Final procedure: WF paired lift (session-block bootstrap), holdout and second-span lifts, weekly dollars / maxDD vs base at equal lots and at equal weekly SD, placebo (WF window), 2x cost, year share, V2 verdict (s48score.verdict) plus DS3 extras (second-span lift > 0, equal-risk dollars not below base). Neighbours are the pre-holdout PRE neighbours.
