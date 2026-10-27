# DS3 TPBX4_TAPE pre-holdout text (D3PX T-PBX block iv), written before the holdout and the 2023 span are read

Prereg sha256: e7f148c4fd277b57e7c07844d7be1d8f3485339e7cd76d0e2bfd8607869ded45. WF-PRE, MAPPED conservative basis, per-arm paired vs the base trigger.

| cell | exec | trigger rate | trades PRE | per-arm pts (base) | paired per arm [CI] | MDE | vs random-in-regime (b) [CI] rank | vs (a) rank | PRE wk mean $ |
|---|---|---|---|---|---|---|---|---|---|
| PBX4_PBS_f60_T3_PBOS | NT8 1-min bar | 0.26 | 859 | -0.15 (+1.28) | -1.43 [-4.86,+2.06] | 4.94 | -0.05 [-4.09,+4.30] r0.50 | 0.62 | +1,624 |
| PBX4_PBS_f60_T3_ABS | NT8 1-min bar | 0.02 | 170 | +0.20 (+1.28) | -1.09 [-5.47,+3.29] | 6.26 | +0.08 [-11.44,+11.48] r0.56 | 0.62 | +1,337 |
| PBX4_PBS_f60_T3_DFLIP | execution server / Volumetric | 0.56 | 1158 | +0.84 (+1.28) | -0.44 [-2.73,+1.81] | 3.24 | +2.02 [-1.11,+5.16] r0.94 | 1.00 | -278 |
| PBX4_PBS_f60_T3_CDBOS | execution server / Volumetric | 0.29 | 899 | +0.21 (+1.28) | -1.07 [-4.36,+2.22] | 4.69 | +1.87 [-2.99,+6.41] r0.88 | 1.00 | +2,864 |
| PBX4_PBS_f60_T3_STK | execution server / Volumetric | 0.26 | 978 | +0.81 (+1.28) | -0.47 [-4.10,+3.20] | 5.22 | +4.93 [+1.68,+8.28] r1.00 | 1.00 | +8,481 |
| PBX4_PBS_f60_T3_DIV | execution server / Volumetric | 0.14 | 661 | -0.20 (+1.28) | -1.48 [-5.43,+2.52] | 5.65 | +0.51 [-5.40,+6.31] r0.62 | 0.94 | -2,156 |
| PBX4_PBS_f60_T3_CLZ | execution server / Volumetric | 0.03 | 125 | -0.18 (+1.28) | -1.47 [-5.80,+2.88] | 6.22 | +2.32 [-9.95,+13.18] r0.69 | 0.81 | -794 |
| PBX4_PBS_f60_T3_RUN | execution server (trade rows) | 0.84 | 1341 | +1.39 (+1.28) | +0.11 [-1.35,+1.50] | 2.03 | +1.96 [-0.89,+4.81] r0.94 | 1.00 | +2,717 |
| PBX4_PBS_f60_T3_LP | execution server (trade rows) | 0.13 | 688 | +0.24 (+1.28) | -1.05 [-5.24,+3.21] | 6.07 | +1.19 [-4.27,+6.88] r0.75 | 0.94 | -268 |
| PBX4_PBS_f60_T3_BOOK | execution server (book) | 0.25 | 768 | +1.05 (+1.28) | -0.23 [-3.46,+3.10] | 4.74 | +4.04 [-0.69,+8.99] r1.00 | 1.00 | +7,992 |
| PBX4_ER5_f40_SW_PBOS | NT8 1-min bar | 0.07 | 40 | -0.19 (+10.13) | -10.32 [-19.18,-1.94] | 12.36 | -4.55 [-27.82,+15.44] r0.06 | 0.19 | -332 |
| PBX4_ER5_f40_SW_ABS | NT8 1-min bar | 0.02 | 11 | +0.96 (+10.13) | -9.17 [-17.73,-0.91] | 12.11 | +38.24 [-23.65,+135.83] r1.00 | 1.00 | +1,396 |
| PBX4_ER5_f40_SW_DFLIP | execution server / Volumetric | 0.80 | 295 | +8.71 (+10.13) | -1.42 [-5.32,+2.50] | 5.58 | +7.71 [-1.19,+15.69] r1.00 | 1.00 | +8,447 |
| PBX4_ER5_f40_SW_CDBOS | execution server / Volumetric | 0.11 | 58 | +1.98 (+10.13) | -8.15 [-16.48,-0.15] | 11.78 | +13.23 [-5.99,+34.28] r1.00 | 1.00 | +2,612 |
| PBX4_ER5_f40_SW_STK | execution server / Volumetric | 0.28 | 141 | +2.08 (+10.13) | -8.05 [-15.89,-0.53] | 11.01 | +3.64 [-11.54,+18.62] r0.75 | 1.00 | +3,189 |
| PBX4_ER5_f40_SW_DIV | execution server / Volumetric | 0.36 | 171 | +4.58 (+10.13) | -5.55 [-12.09,+1.08] | 9.35 | +11.43 [-1.49,+23.36] r0.88 | 1.00 | +6,172 |
| PBX4_ER5_f40_SW_CLZ | execution server / Volumetric | 0.02 | 8 | +0.64 (+10.13) | -9.49 [-18.38,-0.97] | 12.56 | +19.04 [-21.79,+55.30] r0.94 | 1.00 | +447 |
| PBX4_ER5_f40_SW_RUN | execution server (trade rows) | 0.81 | 294 | +8.57 (+10.13) | -1.56 [-6.14,+2.59] | 6.21 | +6.01 [-4.04,+15.35] r1.00 | 1.00 | +7,140 |
| PBX4_ER5_f40_SW_LP | execution server (trade rows) | 0.14 | 70 | +3.11 (+10.13) | -7.02 [-15.75,+1.15] | 11.96 | +13.93 [-9.02,+38.30] r0.94 | 1.00 | +3,347 |
| PBX4_ER5_f40_SW_BOOK | execution server (book) | 0.19 | 96 | +2.08 (+10.13) | -8.05 [-15.92,-0.53] | 11.07 | +1.06 [-14.09,+14.40] r0.69 | 0.75 | +1,539 |
| PBX4_PB3_f60_T3_PBOS | NT8 1-min bar | 0.24 | 1255 | +0.27 (+1.29) | -1.02 [-3.59,+1.54] | 3.69 | +0.90 [-2.28,+3.89] r0.75 | 0.94 | +11,280 |
| PBX4_PB3_f60_T3_ABS | NT8 1-min bar | 0.02 | 373 | +0.10 (+1.29) | -1.19 [-4.58,+2.18] | 4.85 | +4.92 [-2.77,+12.38] r1.00 | 0.88 | +5,269 |
| PBX4_PB3_f60_T3_DFLIP | execution server / Volumetric | 0.85 | 1749 | +1.18 (+1.29) | -0.12 [-0.77,+0.55] | 0.94 | -0.32 [-3.07,+2.28] r0.38 | 0.88 | +8,541 |
| PBX4_PB3_f60_T3_CDBOS | execution server / Volumetric | 0.33 | 1409 | +0.12 (+1.29) | -1.17 [-3.46,+1.09] | 3.26 | -0.42 [-2.98,+1.83] r0.38 | 0.44 | +9,079 |
| PBX4_PB3_f60_T3_STK | execution server / Volumetric | 0.33 | 1634 | +0.54 (+1.29) | -0.75 [-3.43,+1.89] | 3.80 | +1.02 [-1.72,+3.58] r0.81 | 0.81 | +8,080 |
| PBX4_PB3_f60_T3_DIV | execution server / Volumetric | 0.22 | 1353 | +0.32 (+1.29) | -0.97 [-3.79,+1.82] | 4.03 | +0.16 [-2.39,+2.65] r0.56 | 0.88 | +3,041 |
| PBX4_PB3_f60_T3_CLZ | execution server / Volumetric | 0.04 | 207 | -0.18 (+1.29) | -1.47 [-4.77,+1.81] | 4.76 | +1.87 [-3.51,+7.60] r0.81 | 1.00 | -2,268 |
| PBX4_PB3_f60_T3_RUN | execution server (trade rows) | 0.79 | 1770 | +1.30 (+1.29) | +0.00 [-1.07,+1.07] | 1.52 | -0.15 [-2.58,+2.43] r0.50 | 0.81 | +10,054 |
| PBX4_PB3_f60_T3_LP | execution server (trade rows) | 0.15 | 1177 | +0.55 (+1.29) | -0.74 [-3.97,+2.45] | 4.62 | +0.41 [-4.02,+5.04] r0.56 | 0.88 | +11,965 |
| PBX4_PB3_f60_T3_BOOK | execution server (book) | 0.26 | 1226 | +0.56 (+1.29) | -0.73 [-3.25,+1.77] | 3.59 | -1.94 [-6.17,+2.19] r0.06 | 0.81 | +4,501 |

Frozen rule: every cell scored once on 2025-07+ and 2023-04..2024-01, definitions unchanged.
