# DS3_L2SET_PROFIT - profit health: settings for "a thick book around a winner" (L2SP, 2026-10-30)
Research only; no live/execution change; UNTOUCHED (label day > 20260206) never read; every frame filtered to label day <= 20260206 before any grouping. vs_lib/s48score WINS (HOLD, WF, L8W have no upper bound) NOT used: own masks 2026 = 20260101..20260206 (**about 5 real weeks, so every 2026 number is mostly noise: MDE shown**), last 6 months (L6M) = 20250801..20260206, HOLD = 20250701..20260206, PRE = 20240201..20250630, X' = 20230401..20240131 (first week partial baselines).
Prereg `l2vast/ds3/prereg/L2SET_PROFIT_prereg.md` sha256 ae38ba483bed2b267df6f39c923288659efb5d95c687aefad43d25022b41b095 (DECISIONS.md, before any statistic): **23,773 cells** (F1 23,760 thick-book cells, F2 12 thin-skip cells, F0 1 plain 70% reference). PRE-only selection file `out/l2set_profit/selection_PRE.json` sha256 faf6890a...a95 written first, then ONE look at all windows (looks.jsonl). **Every cell ranked by last-6-months below is ranked on already-looked data (the directive asks for recent ranking); the PRE-selected cell beside it is the only out-of-sample choice.**
Data/fills: THL2 10-s rows of the 10 static-bracket books, MEASURED exits (market 0.995 pt; trail/lock stop 1.01 pt at the close of the breach row, conservative), paired vs the same trade held to the bracket (pts/trade over ALL trades of the scope, non-fires count 0). **MEASURED basis carries the 1.4-4.3 pt limit-target fill correction in the hold arm, so any early market exit earns it; therefore every row also shows the N basis (no target correction), the excess over a random exit at the same exit rate (the correction cancels), a 2x-cost check in the gates, and the shuffled-book placebo rank (5 draws).** MDE = 2.8 SE (day x session clusters). $/wk at live lots (LOTS) x $20/pt.
Tiers (failed gates listed): PASS = all of G1 PRE CI>0, G2 HOLD>0, G3 X'>0, G4 2x-cost PRE&HOLD>0, G5 N-basis PRE&HOLD>0, G6 excess over random exit PRE&HOLD>0, G7 White RC p<=0.05 (best-of-N over the group, PRE), G8 shuffled-book rank >=0.95, G9 PRE fires >= 200 (pooled) / 100 (sub-scope). CANDIDATE = G2-G6, G9, RC p<=0.10, placebo >=0.8, PRE>0. CANDIDATE-RECENT = 2026>0 and L6M>0 (label only). DEAD otherwise.

## Verdict (computed)
* Pooled scope, F1 (23,760 cells): 0 PASS / 0 CANDIDATE / 8589 CANDIDATE-RECENT / 15171 DEAD. F2+F0 (13 cells): {'CANDIDATE-RECENT': 13}. Across all 20 scopes x F1 cells: 0 PASS, 0 CANDIDATE, 153253 CANDIDATE-RECENT.
* White RC (PRE, best-of-N, studentised, 5-day blocks): pooled F1 p = 0.72 (t_max 1.94); per-book p range 0.36-0.97.

## 1. SETTINGS TABLE per book (and pooled) - recent windows first
Per scope: the PRE-selected cell (out of sample), the rank-1 cell by last 6 months (selected on looked data; pooled shows rank 1-3), and the best G2 (thin-skip / reference) cell chosen on PRE. Scope eligibility: PRE fires >= 200 pooled / 100 sub-scope and L6M fires >= 50 / 25 (rank rows). A cell is a SETTING only if its tier row says so; a DEAD row is "best available", not advice.
| role | cell | tier | 2026 (5 wk) pts/trade [fired] | last 6 mo [fired] | HOLD | PRE | X' | N basis L6M/HOLD/PRE | vs random exit L6M/PRE | shuffled-book rank (PRE) | RC p (best-of-N, PRE) | $/wk L6M at live lots | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **pooled** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70never` | DEAD | -0.45 (MDE 0.9) [80] | -0.05 [-0.32,+0.22] MDE 0.39 [313] | -0.06 [-0.32,+0.19] MDE 0.36 [344] | +0.17 [-0.00,+0.35] MDE 0.25 [736] | +0.03 | -0.13/-0.14/+0.13 | +0.05/+0.30 | 1.00 | 0.72 | -1,680 | G1_PRE_CI,G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always` | CANDIDATE-RECENT | +1.43 (MDE 2.6) [1315] | +1.04 [+0.24,+1.83] MDE 1.14 [5648] | +1.07 [+0.33,+1.81] MDE 1.06 [6198] | +0.34 [-0.16,+0.84] MDE 0.72 [13801] | +0.43 | -1.07/-1.01/-0.96 | +2.86/+2.66 | 0.00 | 0.72 | +56,769 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| rank-2 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_tot_ge1.2|armpct0.7|d10|take|p70always` | CANDIDATE-RECENT | +1.41 (MDE 2.7) [1316] | +1.04 [+0.23,+1.84] MDE 1.15 [5656] | +1.07 [+0.32,+1.82] MDE 1.07 [6206] | +0.32 [-0.19,+0.83] MDE 0.73 [13818] | +0.41 | -1.08/-1.01/-0.98 | +2.86/+2.65 | 0.00 | 0.72 | +56,487 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| rank-3 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge1.2|armpct0.7|d30|take|p70always` | CANDIDATE-RECENT | +1.39 (MDE 2.7) [1313] | +1.04 [+0.24,+1.83] MDE 1.13 [5637] | +1.08 [+0.34,+1.81] MDE 1.05 [6186] | +0.34 [-0.16,+0.85] MDE 0.72 [13775] | +0.42 | -1.08/-1.00/-0.96 | +2.85/+2.66 | 0.00 | 0.72 | +56,129 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +1.24 (MDE 2.6) [1302] | +0.86 [+0.11,+1.62] MDE 1.08 [5565] | +0.94 [+0.24,+1.65] MDE 1.00 [6102] | +0.39 [-0.10,+0.87] MDE 0.69 [13618] | +0.35 | -1.25/-1.13/-0.91 | +2.65/+2.68 | 0.00 | 0.09 | +46,663 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **ST** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never` | DEAD | -0.26 (MDE 2.1) [15] | +0.09 [-0.52,+0.70] MDE 0.87 [48] | +0.21 [-0.38,+0.79] MDE 0.83 [53] | +0.62 [+0.18,+1.06] MDE 0.63 [138] | +0.20 | +0.02/+0.14/+0.57 | +0.19/+0.84 | 1.00 | 0.36 | +795 | G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge3.0|armpts20|d0|lock5|p70always` | CANDIDATE-RECENT | +1.70 (MDE 5.2) [178] | +2.50 [+0.78,+4.22] MDE 2.45 [766] | +2.52 [+0.89,+4.15] MDE 2.33 [834] | +0.01 [-1.02,+1.04] MDE 1.47 [1703] | -0.11 | +0.41/+0.48/-1.28 | +0.22/-1.71 | 0.00 | 0.36 | +22,433 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +1.86 (MDE 5.1) [175] | +2.05 [+0.41,+3.69] MDE 2.34 [727] | +2.00 [+0.45,+3.54] MDE 2.21 [784] | +0.26 [-0.72,+1.24] MDE 1.39 [1646] | +0.20 | -0.03/-0.04/-1.03 | +3.54/+2.83 | 0.00 | 0.39 | +18,412 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **HM** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge1.5|armpts40|d30|lock10|p70never` | DEAD | +1.03 (MDE 2.7) [10] | -0.09 [-0.88,+0.71] MDE 1.13 [42] | -0.09 [-0.87,+0.68] MDE 1.11 [52] | +0.58 [+0.04,+1.13] MDE 0.77 [121] | +0.23 | -0.20/-0.21/+0.52 | +0.13/+0.81 | 1.00 | 0.67 | -552 | G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge1.5|armpct0.3|d10|take|p70always` | CANDIDATE-RECENT | +1.08 (MDE 7.1) [135] | +1.00 [-1.35,+3.35] MDE 3.36 [603] | +1.28 [-1.00,+3.56] MDE 3.26 [671] | -0.87 [-2.32,+0.59] MDE 2.08 [1456] | +0.71 | -1.11/-0.78/-2.16 | -0.81/-3.01 | 1.00 | 0.67 | +6,510 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | DEAD | -0.29 (MDE 5.4) [116] | -0.31 [-1.97,+1.36] MDE 2.38 [512] | -0.30 [-1.87,+1.26] MDE 2.23 [556] | -0.19 [-1.26,+0.88] MDE 1.53 [1242] | -0.76 | -2.41/-2.35/-1.47 | +2.45/+2.37 | 0.00 | 0.72 | -1,988 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **WT** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge1.2|armpts30|d0|take|p70never` | CANDIDATE-RECENT | +0.33 (MDE 1.5) [115] | +0.80 [+0.26,+1.33] MDE 0.77 [532] | +0.90 [+0.38,+1.42] MDE 0.74 [600] | +0.60 [+0.24,+0.95] MDE 0.51 [1299] | -0.12 | -0.41/-0.32/-0.11 | +0.73/+1.05 | 1.00 | 0.58 | +6,792 | G3_Xp,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | CANDIDATE-RECENT | +1.61 (MDE 2.7) [249] | +2.20 [+1.27,+3.14] MDE 1.33 [1082] | +2.36 [+1.45,+3.28] MDE 1.31 [1202] | +0.51 [-0.08,+1.10] MDE 0.85 [2600] | -0.93 | -0.03/+0.15/-0.85 | +1.20/+0.07 | 1.00 | 0.58 | +18,802 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `I|z_ahead_le-1.0|d0|skip_p70_if_thin` | DEAD | -0.09 (MDE 1.7) [186] | +0.85 [+0.17,+1.52] MDE 0.97 [841] | +1.13 [+0.45,+1.81] MDE 0.97 [937] | +0.59 [+0.12,+1.07] MDE 0.68 [2038] | -0.29 | -1.04/-0.75/-0.53 | +0.98/+1.59 | 1.00 | 0.02 | +7,210 | G3_Xp,G5_Nbasis |
| **KB** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|z_ahead_ge1.5|armpct0.7|d30|lock10|p70never` | CANDIDATE-RECENT | +0.13 (MDE 2.1) [15] | +0.22 [-0.58,+1.01] MDE 1.14 [83] | +0.36 [-0.44,+1.15] MDE 1.13 [103] | +0.14 [-0.36,+0.65] MDE 0.73 [218] | +1.43 | +0.08/+0.22/+0.05 | +0.39/+0.50 | 1.00 | 0.97 | +1,015 | G1_PRE_CI,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70always` | CANDIDATE-RECENT | +2.05 (MDE 4.6) [169] | +1.36 [-0.15,+2.88] MDE 2.16 [711] | +1.58 [+0.13,+3.03] MDE 2.07 [772] | +0.04 [-0.93,+1.02] MDE 1.40 [1732] | +0.98 | -0.67/-0.41/-1.27 | +2.81/+2.88 | 1.00 | 0.97 | +6,361 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +1.40 (MDE 4.6) [166] | +0.88 [-0.60,+2.35] MDE 2.10 [699] | +1.13 [-0.28,+2.54] MDE 2.02 [758] | +0.02 [-0.93,+0.96] MDE 1.35 [1707] | +1.12 | -1.16/-0.86/-1.29 | +2.30/+2.81 | 0.00 | 0.59 | +4,096 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **SM** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge3.0|armpts30|d0|trail10|p70never` | DEAD | +1.65 (MDE 8.5) [14] | -1.02 [-2.73,+0.68] MDE 2.43 [43] | -1.11 [-2.60,+0.39] MDE 2.14 [46] | +1.16 [-0.07,+2.39] MDE 1.76 [105] | -0.28 | -1.48/-1.54/+0.99 | -1.21/+1.57 | 1.00 | 0.69 | -1,701 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70thickonly` | CANDIDATE-RECENT | +9.28 (MDE 16.4) [47] | +3.60 [-1.37,+8.58] MDE 7.11 [216] | +2.06 [-2.56,+6.68] MDE 6.60 [254] | -1.43 [-4.16,+1.29] MDE 3.89 [568] | +1.13 | +1.80/+0.19/-2.46 | -1.12/-2.08 | 0.00 | 0.69 | +5,982 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +9.85 (MDE 13.0) [42] | +1.76 [-1.45,+4.98] MDE 4.59 [176] | +2.03 [-1.04,+5.09] MDE 4.37 [209] | -0.25 [-2.05,+1.56] MDE 2.57 [506] | +2.23 | -0.27/-0.05/-1.46 | +2.44/+3.30 | 1.00 | 0.67 | +2,927 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| **PE** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|hour_ahead_ge2.0|armpts10|d30|take|p70always` | CANDIDATE-RECENT | +2.52 (MDE 5.3) [150] | +0.35 [-1.21,+1.92] MDE 2.24 [659] | +0.23 [-1.30,+1.76] MDE 2.19 [731] | +1.48 [+0.38,+2.59] MDE 1.58 [1745] | -0.44 | -1.64/-1.75/+0.21 | -4.12/-3.23 | 1.00 | 0.46 | +1,678 | G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70always` | CANDIDATE-RECENT | +2.91 (MDE 5.5) [151] | +1.01 [-0.59,+2.61] MDE 2.28 [671] | +0.71 [-0.83,+2.24] MDE 2.20 [742] | +0.87 [-0.21,+1.95] MDE 1.55 [1718] | +0.14 | -0.97/-1.28/-0.41 | +1.37/+1.79 | 0.00 | 0.46 | +4,839 | G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +2.94 (MDE 5.1) [142] | +0.57 [-0.88,+2.01] MDE 2.06 [624] | +0.44 [-0.93,+1.81] MDE 1.95 [686] | +1.13 [+0.13,+2.13] MDE 1.42 [1593] | +0.43 | -1.36/-1.48/-0.08 | +2.81/+3.20 | 0.00 | 0.02 | +2,700 | G4_2xcost,G5_Nbasis,G8_placebo95 |
| **PB** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|hour_tot_ge2.0|armpct0.3|d0|lock10|p70never` | DEAD | +0.43 (MDE 3.6) [20] | -0.77 [-2.11,+0.56] MDE 1.90 [121] | -0.61 [-1.98,+0.75] MDE 1.95 [156] | +1.22 [+0.36,+2.09] MDE 1.24 [312] | -1.04 | -1.11/-0.99/+1.04 | -0.99/+0.66 | 1.00 | 0.64 | -4,789 | G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|z_ahead_ge1.0|armpts30|d0|lock10|p70always` | CANDIDATE-RECENT | +2.85 (MDE 7.4) [134] | +1.04 [-1.35,+3.43] MDE 3.41 [595] | +1.34 [-0.94,+3.63] MDE 3.26 [655] | +0.68 [-0.85,+2.21] MDE 2.19 [1414] | -0.26 | -1.19/-0.82/-0.60 | +1.88/+1.09 | 0.00 | 0.64 | +6,448 | G1_PRE_CI,G3_Xp,G5_Nbasis,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.53 (MDE 5.1) [108] | +0.24 [-1.60,+2.07] MDE 2.62 [502] | +0.60 [-1.15,+2.35] MDE 2.50 [550] | +1.22 [+0.02,+2.43] MDE 1.72 [1195] | -0.10 | -1.92/-1.50/-0.00 | +2.61/+3.20 | 1.00 | 0.02 | +1,461 | G3_Xp,G5_Nbasis |
| **DN** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|sess_tot_ge2.0|armpct0.7|d10|trail20|p70thickonly` | DEAD | -1.81 (MDE 1.8) [15] | -0.38 [-1.10,+0.33] MDE 1.02 [85] | -0.03 [-0.81,+0.75] MDE 1.12 [97] | +0.71 [+0.10,+1.32] MDE 0.87 [179] | +0.02 | -0.81/-0.46/+0.51 | +0.07/+1.17 | 1.00 | 0.91 | -1,923 | G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge2.0|armpct0.3|d0|take|p70always` | DEAD | -0.81 (MDE 8.1) [109] | +1.28 [-1.49,+4.04] MDE 3.95 [481] | +1.29 [-1.35,+3.94] MDE 3.77 [531] | -0.51 [-2.24,+1.22] MDE 2.47 [1165] | +0.49 | -0.92/-0.86/-1.85 | -1.36/-2.30 | 0.00 | 0.91 | +6,386 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.02 (MDE 6.6) [98] | +0.20 [-1.85,+2.25] MDE 2.93 [402] | +0.45 [-1.49,+2.40] MDE 2.78 [440] | +0.28 [-1.02,+1.58] MDE 1.85 [978] | -0.26 | -1.92/-1.62/-0.99 | +2.33/+2.77 | 1.00 | 0.40 | +993 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| **MV** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|hour_ahead_ge2.0|armpts20|d30|lock10|p70never` | DEAD | -0.48 (MDE 1.8) [10] | -0.76 [-1.44,-0.07] MDE 0.98 [57] | -0.64 [-1.35,+0.07] MDE 1.01 [73] | +0.62 [+0.18,+1.06] MDE 0.63 [137] | +0.55 | -0.90/-0.79/+0.57 | -0.94/+0.53 | 1.00 | 0.46 | -6,135 | G2_HOLD,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | DEAD | -0.32 (MDE 5.3) [173] | +1.72 [-0.34,+3.78] MDE 2.94 [740] | +1.41 [-0.56,+3.38] MDE 2.82 [819] | -0.40 [-1.72,+0.91] MDE 1.88 [1893] | +1.34 | -0.34/-0.61/-1.73 | -2.19/-3.06 | 0.00 | 0.46 | +13,914 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.08 (MDE 4.4) [150] | +0.90 [-0.69,+2.50] MDE 2.27 [614] | +0.68 [-0.80,+2.16] MDE 2.11 [669] | +0.86 [-0.16,+1.87] MDE 1.45 [1552] | +1.64 | -1.08/-1.28/-0.38 | +3.45/+2.89 | 1.00 | 0.04 | +7,313 | G1_PRE_CI,G5_Nbasis |
| **MA** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|sess_ahead_ge2.0|armpts10|d30|lock10|p70never` | DEAD | -1.75 (MDE 5.6) [11] | -1.84 [-3.52,-0.17] MDE 2.39 [48] | -1.81 [-3.50,-0.12] MDE 2.42 [67] | +0.38 [-0.60,+1.35] MDE 1.39 [109] | -0.66 | -2.14/-2.16/+0.29 | -2.42/-0.24 | 1.00 | 0.90 | -5,357 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_tot_ge2.0|armpts10|d0|trail20|p70thickonly` | CANDIDATE-RECENT | +3.06 (MDE 7.7) [24] | +1.35 [-1.43,+4.13] MDE 3.97 [114] | +0.90 [-1.59,+3.39] MDE 3.56 [129] | -1.91 [-3.41,-0.41] MDE 2.14 [268] | -1.13 | +0.63/+0.19/-2.37 | -0.02/-3.41 | 0.00 | 0.90 | +3,931 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | DEAD | +0.81 (MDE 8.7) [54] | -1.38 [-3.84,+1.07] MDE 3.51 [240] | -1.35 [-3.55,+0.85] MDE 3.14 [272] | -1.35 [-2.85,+0.14] MDE 2.13 [594] | -0.33 | -3.60/-3.49/-2.60 | +2.62/+2.71 | 0.00 | 0.98 | -4,016 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |

Reference (F0) plain take-at-70%-always, every scope, for the path rule behind the 43 CANDIDATE-RECENT cells of THL2 D:
| role | cell | tier | 2026 (5 wk) pts/trade [fired] | last 6 mo [fired] | HOLD | PRE | X' | N basis L6M/HOLD/PRE | vs random exit L6M/PRE | shuffled-book rank (PRE) | RC p (best-of-N, PRE) | $/wk L6M at live lots | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| REF pooled | `REF|p70_take_always` | CANDIDATE-RECENT | +1.24 (MDE 2.6) [1302] | +0.86 [+0.11,+1.62] MDE 1.08 [5565] | +0.94 [+0.24,+1.65] MDE 1.00 [6102] | +0.39 [-0.10,+0.87] MDE 0.69 [13618] | +0.35 | -1.25/-1.13/-0.91 | +2.65/+2.68 | 0.00 | 0.09 | +46,663 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF ST | `REF|p70_take_always` | CANDIDATE-RECENT | +1.86 (MDE 5.1) [175] | +2.05 [+0.41,+3.69] MDE 2.34 [727] | +2.00 [+0.45,+3.54] MDE 2.21 [784] | +0.26 [-0.72,+1.24] MDE 1.39 [1646] | +0.20 | -0.03/-0.04/-1.03 | +3.54/+2.83 | 0.00 | 0.39 | +18,412 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF HM | `REF|p70_take_always` | DEAD | -0.29 (MDE 5.4) [116] | -0.31 [-1.97,+1.36] MDE 2.38 [512] | -0.30 [-1.87,+1.26] MDE 2.23 [556] | -0.19 [-1.26,+0.88] MDE 1.53 [1242] | -0.76 | -2.41/-2.35/-1.47 | +2.45/+2.37 | 0.00 | 0.72 | -1,988 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF WT | `REF|p70_take_always` | CANDIDATE-RECENT | +1.53 (MDE 2.4) [238] | +1.68 [+0.88,+2.49] MDE 1.15 [1009] | +1.90 [+1.11,+2.68] MDE 1.12 [1114] | +0.57 [+0.06,+1.08] MDE 0.73 [2410] | -0.15 | -0.54/-0.30/-0.78 | +1.84/+1.75 | 0.00 | 0.02 | +14,365 | G3_Xp,G5_Nbasis,G8_placebo95 |
| REF KB | `REF|p70_take_always` | CANDIDATE-RECENT | +1.40 (MDE 4.6) [166] | +0.88 [-0.60,+2.35] MDE 2.10 [699] | +1.13 [-0.28,+2.54] MDE 2.02 [758] | +0.02 [-0.93,+0.96] MDE 1.35 [1707] | +1.12 | -1.16/-0.86/-1.29 | +2.30/+2.81 | 0.00 | 0.59 | +4,096 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF SM | `REF|p70_take_always` | CANDIDATE-RECENT | +9.78 (MDE 13.0) [42] | +1.52 [-1.69,+4.74] MDE 4.59 [180] | +1.82 [-1.25,+4.88] MDE 4.37 [213] | -0.38 [-2.18,+1.42] MDE 2.57 [514] | +2.43 | -0.56/-0.31/-1.63 | +2.22/+3.22 | 0.00 | 0.67 | +2,528 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF PE | `REF|p70_take_always` | CANDIDATE-RECENT | +2.77 (MDE 5.1) [147] | +0.66 [-0.80,+2.12] MDE 2.09 [643] | +0.60 [-0.79,+1.99] MDE 1.98 [707] | +1.11 [+0.10,+2.12] MDE 1.44 [1658] | +0.42 | -1.33/-1.38/-0.16 | +2.97/+3.27 | 0.00 | 0.02 | +3,143 | G5_Nbasis,G8_placebo95 |
| REF PB | `REF|p70_take_always` | DEAD | -0.67 (MDE 5.1) [111] | +0.10 [-1.72,+1.93] MDE 2.61 [513] | +0.48 [-1.27,+2.22] MDE 2.49 [561] | +1.15 [-0.06,+2.36] MDE 1.73 [1221] | -0.13 | -2.11/-1.67/-0.11 | +2.53/+3.17 | 0.00 | 0.02 | +633 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G8_placebo95 |
| REF DN | `REF|p70_take_always` | DEAD | -0.11 (MDE 6.6) [99] | +0.37 [-1.71,+2.46] MDE 2.98 [411] | +0.58 [-1.40,+2.56] MDE 2.83 [451] | +0.22 [-1.09,+1.53] MDE 1.87 [1008] | -0.34 | -1.79/-1.54/-1.10 | +2.55/+2.78 | 0.00 | 0.40 | +1,857 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF MV | `REF|p70_take_always` | DEAD | -0.23 (MDE 4.3) [154] | +0.94 [-0.66,+2.55] MDE 2.30 [631] | +0.71 [-0.78,+2.20] MDE 2.13 [686] | +0.74 [-0.28,+1.77] MDE 1.47 [1618] | +1.71 | -1.10/-1.29/-0.57 | +3.56/+2.86 | 0.00 | 0.04 | +7,633 | G1_PRE_CI,G5_Nbasis,G8_placebo95 |
| REF MA | `REF|p70_take_always` | DEAD | +0.81 (MDE 8.7) [54] | -1.38 [-3.84,+1.07] MDE 3.51 [240] | -1.35 [-3.55,+0.85] MDE 3.14 [272] | -1.35 [-2.85,+0.14] MDE 2.13 [594] | -0.33 | -3.60/-3.49/-2.60 | +2.62/+2.71 | 0.00 | 0.98 | -4,016 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_asia | `REF|p70_take_always` | CANDIDATE-RECENT | +2.52 (MDE 6.5) [421] | +0.92 [-0.84,+2.69] MDE 2.52 [1636] | +1.03 [-0.59,+2.64] MDE 2.31 [1801] | +0.39 [-0.66,+1.44] MDE 1.50 [3686] | +0.14 | -1.35/-1.20/-1.03 | +2.54/+3.21 | 0.00 | 0.26 | +12,291 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_london | `REF|p70_take_always` | CANDIDATE-RECENT | +1.55 (MDE 4.9) [284] | +0.19 [-1.37,+1.74] MDE 2.22 [1204] | +0.38 [-1.08,+1.85] MDE 2.09 [1312] | +0.66 [-0.43,+1.74] MDE 1.55 [2901] | -0.69 | -2.03/-1.82/-0.69 | +2.94/+2.82 | 0.00 | 0.11 | +312 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_pre | `REF|p70_take_always` | CANDIDATE-RECENT | +1.23 (MDE 7.0) [58] | +2.08 [-0.78,+4.94] MDE 4.09 [266] | +2.78 [-0.11,+5.67] MDE 4.13 [285] | +1.00 [-0.82,+2.81] MDE 2.59 [772] | +0.84 | +0.07/+0.87/-0.21 | +3.64/+2.32 | 0.00 | 0.14 | +6,346 | G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_nyam | `REF|p70_take_always` | CANDIDATE-RECENT | +0.12 (MDE 3.7) [351] | +0.93 [-0.34,+2.20] MDE 1.82 [1561] | +0.77 [-0.40,+1.95] MDE 1.68 [1730] | -0.13 [-1.04,+0.77] MDE 1.29 [3742] | +0.07 | -1.15/-1.29/-1.41 | +2.66/+2.46 | 0.00 | 0.68 | +15,636 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_nypm | `REF|p70_take_always` | CANDIDATE-RECENT | +0.54 (MDE 5.4) [185] | +1.17 [-0.40,+2.73] MDE 2.23 [892] | +1.22 [-0.23,+2.68] MDE 2.08 [967] | +0.64 [-0.30,+1.57] MDE 1.34 [2495] | +1.67 | -0.64/-0.54/-0.51 | +2.26/+2.29 | 0.00 | 0.10 | +12,526 | G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF S_close | `REF|p70_take_always` | DEAD | -3.28 (MDE 7.6) [3] | -3.23 [-6.26,-0.19] MDE 4.34 [6] | +1.41 [-7.54,+10.37] MDE 12.79 [7] | -2.22 [-4.73,+0.29] MDE 3.59 [22] | +0.15 | -4.38/+0.39/-3.16 | -0.81/+1.26 | 0.00 | 0.97 | -448 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95,G9_fires |
| REF R_vol0 | `REF|p70_take_always` | CANDIDATE-RECENT | +3.01 (MDE 6.9) [118] | +0.90 [-0.52,+2.32] MDE 2.03 [1161] | +1.27 [+0.01,+2.52] MDE 1.79 [1407] | +1.80 [+0.76,+2.84] MDE 1.49 [3621] | +2.52 | -1.07/-0.61/+0.47 | +2.78/+3.23 | 0.00 | 0.00 | +11,661 | G5_Nbasis,G8_placebo95 |
| REF R_vol1 | `REF|p70_take_always` | CANDIDATE-RECENT | +2.59 (MDE 5.4) [360] | +1.59 [-0.32,+3.50] MDE 2.73 [1096] | +1.36 [-0.33,+3.05] MDE 2.41 [1285] | +0.03 [-0.85,+0.92] MDE 1.26 [3360] | -0.60 | -0.46/-0.69/-1.21 | +3.22/+2.46 | 0.00 | 0.50 | +19,634 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| REF R_vol2 | `REF|p70_take_always` | CANDIDATE-RECENT | +0.32 (MDE 3.1) [824] | +0.60 [-0.38,+1.58] MDE 1.40 [3308] | +0.64 [-0.32,+1.60] MDE 1.37 [3410] | -0.21 [-0.88,+0.46] MDE 0.95 [6637] | -0.62 | -1.59/-1.54/-1.52 | +2.41/+2.49 | 0.00 | 0.84 | +15,368 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |

## 2. By ENTRY session and by regime (vol tercile 0 low / 1 mid / 2 high) - same rows
| role | cell | tier | 2026 (5 wk) pts/trade [fired] | last 6 mo [fired] | HOLD | PRE | X' | N basis L6M/HOLD/PRE | vs random exit L6M/PRE | shuffled-book rank (PRE) | RC p (best-of-N, PRE) | $/wk L6M at live lots | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **S_asia** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|hour_ahead_ge2.0|armpct0.5|d30|lock10|p70never` | DEAD | -0.10 (MDE 3.1) [43] | -0.74 [-1.75,+0.28] MDE 1.45 [212] | -0.74 [-1.79,+0.31] MDE 1.50 [284] | +0.77 [+0.11,+1.42] MDE 0.94 [476] | +0.37 | -0.97/-1.01/+0.67 | -0.71/+0.94 | 1.00 | 0.49 | -11,297 | G2_HOLD,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_ahead_ge3.0|armpts20|d0|lock5|p70always` | CANDIDATE-RECENT | +3.12 (MDE 7.4) [441] | +1.60 [-0.53,+3.72] MDE 3.04 [1738] | +1.54 [-0.41,+3.48] MDE 2.78 [1908] | +0.30 [-0.96,+1.56] MDE 1.80 [3898] | +0.45 | -0.68/-0.69/-1.12 | +0.42/+0.01 | 0.00 | 0.49 | +25,159 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +2.52 (MDE 6.5) [421] | +0.92 [-0.84,+2.69] MDE 2.52 [1636] | +1.03 [-0.59,+2.64] MDE 2.31 [1801] | +0.39 [-0.66,+1.44] MDE 1.50 [3686] | +0.14 | -1.35/-1.20/-1.03 | +2.54/+3.21 | 0.00 | 0.26 | +12,291 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **S_london** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge3.0|armpct0.7|d0|trail30|p70never` | DEAD | -0.01 (MDE 2.4) [28] | -0.08 [-0.68,+0.52] MDE 0.86 [88] | -0.04 [-0.60,+0.51] MDE 0.79 [93] | +0.44 [-0.07,+0.94] MDE 0.72 [240] | +0.25 | -0.20/-0.16/+0.37 | +0.12/+0.62 | 1.00 | 0.88 | -655 | G1_PRE_CI,G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|z_ahead_ge1.0|armpts40|d30|trail10|p70always` | CANDIDATE-RECENT | +2.37 (MDE 5.2) [290] | +0.43 [-1.26,+2.11] MDE 2.40 [1223] | +0.50 [-1.08,+2.07] MDE 2.25 [1331] | +0.68 [-0.51,+1.86] MDE 1.70 [2960] | -0.92 | -1.79/-1.70/-0.68 | +3.19/+2.65 | 0.00 | 0.88 | +4,065 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +1.56 (MDE 4.9) [284] | +0.12 [-1.42,+1.67] MDE 2.20 [1185] | +0.32 [-1.13,+1.78] MDE 2.08 [1293] | +0.76 [-0.31,+1.84] MDE 1.54 [2785] | -0.76 | -2.06/-1.84/-0.52 | +2.83/+2.84 | 1.00 | 0.11 | -278 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| **S_pre** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge1.5|armpts30|d30|lock5|p70thickonly` | DEAD | -0.46 (MDE 2.7) [23] | +1.28 [-0.88,+3.45] MDE 3.09 [123] | +1.54 [-0.85,+3.93] MDE 3.41 [134] | +2.57 [+0.73,+4.41] MDE 2.63 [475] | -0.32 | +0.39/+0.68/+1.90 | +1.12/+2.57 | 1.00 | 0.99 | +4,048 | G3_Xp,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_tot_ge1.2|armpts20|d0|trail30|p70always` | DEAD | -0.25 (MDE 16.5) [74] | +3.86 [-1.56,+9.29] MDE 7.75 [335] | +5.33 [+0.02,+10.63] MDE 7.58 [367] | +0.54 [-2.78,+3.87] MDE 4.75 [1003] | +0.88 | +1.84/+3.40/-0.70 | +1.38/-2.65 | 1.00 | 0.99 | +11,939 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `I|z_ahead_le-1.0|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +1.73 (MDE 6.2) [44] | +1.31 [-1.18,+3.80] MDE 3.56 [217] | +2.08 [-0.51,+4.67] MDE 3.70 [236] | +1.07 [-0.70,+2.84] MDE 2.53 [674] | +1.08 | -0.35/+0.49/+0.02 | +2.58/+2.23 | 1.00 | 0.14 | +3,983 | G1_PRE_CI,G7_RC05 |
| **S_nyam** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_tot_ge1.5|armpts10|d30|trail10|p70never` | DEAD | -0.13 (MDE 0.9) [16] | +0.01 [-0.60,+0.62] MDE 0.87 [103] | -0.03 [-0.62,+0.56] MDE 0.84 [121] | +0.34 [+0.05,+0.63] MDE 0.42 [115] | +0.08 | -0.09/-0.13/+0.32 | -0.28/+0.23 | 1.00 | 0.88 | +329 | G2_HOLD,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_tot_ge2.0|armpts10|d0|trail5|p70always` | CANDIDATE-RECENT | +1.07 (MDE 4.6) [375] | +1.31 [-0.28,+2.90] MDE 2.27 [1672] | +1.05 [-0.49,+2.59] MDE 2.20 [1859] | -0.66 [-1.77,+0.45] MDE 1.59 [3910] | -0.13 | -0.79/-1.02/-1.94 | -3.44/-4.24 | 0.00 | 0.88 | +21,416 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +0.12 (MDE 3.7) [351] | +0.93 [-0.34,+2.20] MDE 1.82 [1561] | +0.77 [-0.40,+1.95] MDE 1.68 [1730] | -0.13 [-1.04,+0.77] MDE 1.29 [3742] | +0.07 | -1.15/-1.29/-1.41 | +2.66/+2.46 | 0.00 | 0.68 | +15,636 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **S_nypm** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|sess_ahead_ge1.2|armpts40|d30|trail5|p70thickonly` | DEAD | -1.73 (MDE 3.3) [88] | +0.18 [-0.97,+1.32] MDE 1.64 [528] | +0.17 [-0.92,+1.26] MDE 1.56 [579] | +0.91 [+0.15,+1.67] MDE 1.09 [1627] | +1.34 | -0.79/-0.77/+0.27 | +0.89/+1.84 | 1.00 | 0.99 | +2,168 | G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_ahead_ge1.2|armpts15|d30|lock5|p70always` | CANDIDATE-RECENT | +3.72 (MDE 9.0) [218] | +2.17 [-0.18,+4.53] MDE 3.37 [1094] | +1.98 [-0.24,+4.20] MDE 3.17 [1203] | +0.85 [-0.52,+2.22] MDE 1.95 [3038] | +2.28 | +0.36/+0.22/-0.30 | -0.96/-2.60 | 1.00 | 0.99 | +24,998 | G1_PRE_CI,G5_Nbasis,G6_vs_random,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.7|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +0.43 (MDE 4.8) [162] | +0.72 [-0.65,+2.09] MDE 1.96 [751] | +0.72 [-0.56,+1.99] MDE 1.82 [811] | +0.62 [-0.24,+1.47] MDE 1.22 [2209] | +1.63 | -0.80/-0.76/-0.37 | +1.65/+2.08 | 0.00 | 0.10 | +8,338 | G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 |
| **S_close** | | | | | | | | | | | | | |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|hour_tot_ge1.2|armpts10|d0|trail5|p70never` | DEAD | +3.67 (MDE 26.3) [4] | -2.35 [-14.52,+9.81] MDE 17.38 [10] | -0.99 [-11.71,+9.73] MDE 15.31 [12] | +0.31 [-6.73,+7.35] MDE 10.06 [26] | -0.48 | -3.12/-1.67/-0.24 | -7.75/-6.35 | 0.00 | 0.97 | -506 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95,G9_fires |
| **R_vol0** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge1.5|armpts40|d30|lock10|p70thickonly` | CANDIDATE-RECENT | +3.88 (MDE 6.8) [60] | +0.31 [-0.83,+1.44] MDE 1.62 [695] | +0.54 [-0.50,+1.57] MDE 1.47 [856] | +1.55 [+0.73,+2.37] MDE 1.17 [2285] | +1.39 | -0.87/-0.59/+0.73 | +1.40/+2.31 | 1.00 | 0.13 | +4,069 | G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|sess_tot_ge2.0|armpts10|d0|take|p70always` | CANDIDATE-RECENT | +8.54 (MDE 12.8) [141] | +1.85 [-0.79,+4.48] MDE 3.76 [1393] | +2.49 [+0.12,+4.86] MDE 3.39 [1731] | +1.50 [-0.04,+3.05] MDE 2.20 [4247] | +4.36 | -0.14/+0.60/+0.16 | -3.35/-4.37 | 0.00 | 0.13 | +23,712 | G1_PRE_CI,G6_vs_random,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +3.12 (MDE 6.9) [114] | +0.79 [-0.61,+2.19] MDE 2.00 [1127] | +1.19 [-0.04,+2.43] MDE 1.77 [1370] | +1.85 [+0.81,+2.88] MDE 1.48 [3594] | +2.49 | -1.13/-0.63/+0.53 | +2.62/+3.26 | 1.00 | 0.00 | +10,297 | G5_Nbasis |
| **R_vol1** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_tot_ge2.0|armpct0.5|d10|lock10|p70never` | DEAD | +0.05 (MDE 2.4) [40] | -0.14 [-1.10,+0.82] MDE 1.37 [96] | -0.10 [-0.96,+0.75] MDE 1.22 [110] | +0.35 [-0.07,+0.78] MDE 0.61 [256] | -0.36 | -0.26/-0.22/+0.30 | -0.10/+0.42 | 1.00 | 0.89 | -1,277 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|t60_ahead_ge1.2|armpct0.7|d30|lock5|p70thickonly` | CANDIDATE-RECENT | +3.31 (MDE 5.1) [317] | +1.85 [-0.00,+3.71] MDE 2.65 [928] | +1.54 [-0.10,+3.19] MDE 2.35 [1095] | +0.04 [-0.80,+0.88] MDE 1.20 [2928] | -0.58 | +0.16/-0.17/-0.99 | +3.24/+2.16 | 1.00 | 0.89 | +23,464 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +2.59 (MDE 5.4) [360] | +1.59 [-0.32,+3.50] MDE 2.73 [1096] | +1.36 [-0.33,+3.05] MDE 2.41 [1285] | +0.03 [-0.85,+0.92] MDE 1.26 [3360] | -0.60 | -0.46/-0.69/-1.21 | +3.22/+2.46 | 0.00 | 0.50 | +19,634 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| **R_vol2** | | | | | | | | | | | | | |
| PRE-selected G1 (only out-of-sample choice) | `P|t60_ahead_ge3.0|armpct0.7|d0|lock0|p70never` | DEAD | -0.83 (MDE 0.9) [34] | -0.06 [-0.34,+0.22] MDE 0.40 [126] | -0.05 [-0.32,+0.22] MDE 0.39 [127] | +0.25 [+0.04,+0.45] MDE 0.29 [258] | +0.10 | -0.11/-0.10/+0.22 | +0.01/+0.35 | 1.00 | 0.57 | -2,118 | G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| rank-1 by L6M G1 [SELECTED ON LOOKED DATA] | `P|hour_ahead_ge1.5|armpct0.5|d0|trail30|p70always` | DEAD | -0.08 (MDE 3.8) [884] | +0.89 [-0.40,+2.18] MDE 1.85 [3568] | +0.87 [-0.38,+2.13] MDE 1.80 [3678] | -0.46 [-1.34,+0.41] MDE 1.25 [7184] | -0.76 | -1.30/-1.31/-1.78 | +1.39/+0.96 | 0.00 | 0.57 | +27,091 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| PRE-selected G2 (thin-skip / reference) | `REF|p70_take_always` | CANDIDATE-RECENT | +0.32 (MDE 3.1) [824] | +0.60 [-0.38,+1.58] MDE 1.40 [3308] | +0.64 [-0.32,+1.60] MDE 1.37 [3410] | -0.21 [-0.88,+0.46] MDE 0.95 [6637] | -0.62 | -1.59/-1.54/-1.52 | +2.41/+2.49 | 0.00 | 0.84 | +15,368 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |

### 2b. Session and regime columns for each book's rank-1 (L6M) cell and for the pooled rank-1 cell (pts/trade vs hold, M basis; L6M / PRE; [fires L6M])
| scope | cell | S_asia | S_london | S_pre | S_nyam | S_nypm | S_close | R_vol0 | R_vol1 | R_vol2 |
|---|---|---|---|---|---|---|---|---|---|---|
| pooled | `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always` | +1.17 / +0.33 [1657] | +0.31 / +0.51 [1219] | +2.16 / +1.12 [267] | +1.01 / -0.15 [1586] | +1.49 / +0.63 [913] | -3.23 / -2.61 [6] | +1.10 / +1.70 [1195] | +1.65 / +0.04 [1111] | +0.81 / -0.26 [3342] |
| ST | `P|sess_ahead_ge3.0|armpts20|d0|lock5|p70always` | +2.75 / -0.44 [192] | +1.26 / +1.01 [150] | -1.36 / +1.60 [31] | +3.19 / -0.42 [264] | +3.38 / -0.40 [128] | -4.57 / +0.00 [1] | +4.89 / +0.97 [164] | +2.88 / -0.98 [143] | +1.52 / +0.01 [459] |
| HM | `P|sess_ahead_ge1.5|armpct0.3|d10|take|p70always` | +1.90 / -0.76 [189] | +1.65 / -0.93 [136] | +7.25 / +0.61 [27] | -2.77 / -2.88 [141] | +2.26 / +0.99 [110] | +nan / +0.00 [0] | +1.40 / +3.50 [125] | +5.61 / -2.84 [130] | -0.71 / -2.29 [348] |
| WT | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | +2.08 / +0.64 [334] | +2.33 / -0.13 [259] | +2.85 / +0.92 [52] | +0.90 / +0.52 [248] | +4.00 / +0.92 [188] | -1.81 / +15.32 [1] | +3.10 / +1.52 [234] | +2.78 / +0.12 [217] | +1.66 / +0.13 [631] |
| KB | `P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70always` | +1.89 / +0.19 [199] | -0.96 / -0.68 [144] | +2.65 / +2.04 [29] | +2.33 / -0.06 [213] | +1.07 / +0.16 [125] | -4.57 / -1.90 [1] | -0.31 / +2.12 [140] | +1.05 / -0.28 [131] | +2.01 / -0.79 [440] |
| SM | `P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70thickonly` | +0.45 / -4.10 [72] | +2.95 / -0.17 [60] | +1.35 / +10.72 [10] | +8.63 / -4.17 [52] | +2.19 / +0.18 [20] | +5.68 / +1.98 [2] | +7.74 / -0.92 [63] | -0.27 / -2.61 [51] | +3.20 / -1.01 [102] |
| PE | `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70always` | +2.68 / -1.05 [209] | +2.35 / +2.05 [132] | -0.62 / +3.06 [32] | -0.26 / +1.04 [186] | -0.23 / +1.22 [112] | +0.00 / -6.21 [0] | +0.82 / +2.53 [143] | -0.05 / -0.11 [142] | +1.46 / +0.50 [386] |
| PB | `P|z_ahead_ge1.0|armpts30|d0|lock10|p70always` | +0.82 / +1.97 [185] | -2.17 / +1.49 [131] | +10.57 / -3.01 [29] | +1.43 / -1.00 [147] | +2.17 / +1.28 [102] | -11.30 / -5.77 [1] | +0.18 / +0.63 [136] | +1.59 / +1.29 [115] | +1.18 / +0.37 [344] |
| DN | `P|sess_ahead_ge2.0|armpct0.3|d0|take|p70always` | -1.04 / +0.43 [139] | +1.39 / -1.46 [105] | +3.95 / +2.32 [25] | +3.21 / -2.50 [140] | +0.43 / +1.53 [70] | -10.46 / +2.22 [2] | +2.45 / +3.22 [119] | +4.45 / +0.62 [101] | -0.35 / -3.40 [261] |
| MV | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | +1.41 / -1.72 [210] | -0.49 / +0.42 [150] | +2.39 / +3.84 [34] | +2.06 / -1.38 [215] | +3.83 / +0.32 [130] | +11.24 / +9.09 [1] | +4.32 / -0.64 [164] | +2.72 / -0.58 [142] | +0.46 / -0.20 [434] |
| MA | `P|t60_tot_ge2.0|armpts10|d0|trail20|p70thickonly` | +2.26 / -1.70 [54] | +0.13 / -3.50 [30] | -1.77 / -2.88 [4] | +1.01 / -0.57 [16] | +2.59 / -1.30 [10] | +0.00 / -3.83 [0] | +1.67 / -3.38 [31] | -0.06 / -2.56 [24] | +1.81 / -0.34 [59] |

## 3. Walk-forward WF-N (3-month re-fit; fit only on trades closed before the re-fit)
Re-fits 1 Jan/Apr/Jul/Oct 2024..1 Jan 2026 (first has 9 months of fit data), fit window = trailing 12 months of closed trades, chosen cell = max fit-window mean (measured basis) subject to fit N-basis mean > 0, fit mean > 0 and >= 100 fires pooled / 40 per book; none -> hold. Evaluated on the entries of the following quarter; X' only covers Jan 2024. Non-fired trades count 0.
| chain | window | M basis | N basis | 2x cost | trades fired | $/wk live lots |
|---|---|---|---|---|---|---|
| WF-N pooled | 2026 (5 wk) | -0.56 [-1.61,+0.49] MDE 1.50 | -0.75 | -0.63 | 147/2229 | -32,022 |
| WF-N pooled | last 6 mo | -0.29 [-0.64,+0.06] MDE 0.50 | -0.41 | -0.33 | 428/9743 | -15,817 |
| WF-N pooled | HOLD | -0.25 [-0.65,+0.15] MDE 0.57 | -0.39 | -0.30 | 583/10805 | -13,221 |
| WF-N pooled | PRE | -0.06 [-0.36,+0.24] MDE 0.43 | -0.18 | -0.16 | 2544/24654 | -1,868 |
| WF-N pooled | X' | -0.24 [-0.55,+0.08] MDE 0.45 | -0.32 | -0.30 | 603/8926 | -7,279 |
| WF-N book | 2026 (5 wk) | -0.00 [-1.46,+1.45] MDE 2.08 | -1.02 | -0.30 | 664/2229 | -7,254 |
| WF-N book | last 6 mo | -0.02 [-0.60,+0.55] MDE 0.82 | -0.87 | -0.28 | 2466/9743 | -2,100 |
| WF-N book | HOLD | +0.07 [-0.48,+0.62] MDE 0.79 | -0.78 | -0.19 | 2778/10805 | +3,045 |
| WF-N book | PRE | -0.27 [-0.68,+0.14] MDE 0.59 | -0.79 | -0.54 | 6602/24654 | -15,820 |
| WF-N book | X' | -0.13 [-0.42,+0.16] MDE 0.41 | -0.17 | -0.17 | 351/8926 | -4,241 |

Re-fit log (cell chosen at each re-fit; fit-window stats; trades the chosen cell was applied to):
| re-fit | scope | chosen cell | fit mean | fit N mean | fit fires/n | eligible cells | applied trades |
|---|---|---|---|---|---|---|---|
| 20240101 | pooled | `P|sess_ahead_ge3.0|armpct0.3|d0|lock5|p70always` | 1.09 | 0.444 | 4747/7907 | 10150 | 2852 |
| 20240401 | pooled | `P|sess_tot_ge2.0|armpct0.3|d0|trail30|p70never` | 0.776 | 0.681 | 1942/10759 | 5085 | 3000 |
| 20240701 | pooled | `P|sess_ahead_ge3.0|armpts10|d10|trail30|p70never` | 0.486 | 0.463 | 617/11320 | 2212 | 5005 |
| 20241001 | pooled | `P|t60_ahead_ge3.0|armpct0.5|d0|trail20|p70never` | 0.347 | 0.278 | 1034/13388 | 1165 | 3705 |
| 20250101 | pooled | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never` | 0.21 | 0.186 | 565/14520 | 359 | 5182 |
| 20250401 | pooled | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never` | 0.212 | 0.17 | 688/16892 | 197 | 5929 |
| 20250701 | pooled | `P|hour_ahead_ge2.0|armpts20|d30|lock10|p70never` | 0.196 | 0.135 | 808/19821 | 220 | 3379 |
| 20251001 | pooled | `P|sess_tot_ge3.0|armpct0.7|d10|take|p70never` | 0.072 | 0.028 | 356/18194 | 18 | 5197 |
| 20260101 | pooled | `P|t60_ahead_ge3.0|armpct0.5|d0|lock10|p70never` | 0.174 | 0.033 | 1251/19687 | 88 | 2229 |
| 20240101 | ST | `P|z_ahead_ge1.5|armpct0.7|d30|trail15|p70never` | 1.5 | 1.37 | 145/878 | 4535 | 313 |
| 20240101 | HM | `P|sess_tot_ge1.5|armpts10|d0|trail20|p70never` | 3.057 | 2.697 | 437/758 | 10531 | 279 |
| 20240101 | WT | `P|hour_tot_ge1.5|armpct0.7|d30|lock5|p70thickonly` | 0.438 | 0.156 | 317/1357 | 1344 | 480 |
| 20240101 | KB | `P|t60_tot_ge1.2|armpts30|d0|trail20|p70never` | 3.003 | 2.659 | 423/914 | 21051 | 325 |
| 20240101 | SM | `P|t60_tot_ge2.0|armpts10|d30|lock5|p70always` | 2.911 | 2.26 | 238/391 | 10858 | 139 |
| 20240101 | PE | `P|sess_ahead_ge2.0|armpct0.3|d10|lock5|p70thickonly` | 2.213 | 1.906 | 355/889 | 13436 | 331 |
| 20240101 | PB | `P|sess_tot_ge2.0|armpct0.3|d10|trail30|p70thickonly` | 2.048 | 1.897 | 158/725 | 3642 | 273 |
| 20240101 | DN | `P|t60_tot_ge1.5|armpts20|d0|trail20|p70never` | 2.348 | 1.944 | 351/642 | 7033 | 235 |
| 20240101 | MV | `P|z_tot_ge1.5|armpts20|d0|lock0|p70always` | 3.408 | 2.816 | 622/887 | 21020 | 323 |
| 20240101 | MA | `P|sess_ahead_ge2.0|armpts30|d0|trail10|p70never` | 2.581 | 2.244 | 185/466 | 5223 | 154 |
| 20240401 | ST | `P|sess_ahead_ge3.0|armpts10|d0|trail30|p70never` | 1.194 | 1.134 | 158/1191 | 4347 | 353 |
| 20240401 | HM | `P|t60_ahead_ge1.2|armpts15|d0|trail20|p70never` | 2.462 | 2.003 | 701/1037 | 8039 | 286 |
| 20240401 | WT | `P|sess_tot_ge2.0|armpts20|d30|trail5|p70thickonly` | 0.385 | 0.302 | 147/1837 | 1735 | 519 |
| 20240401 | KB | `P|sess_ahead_ge2.0|armpts20|d10|trail15|p70thickonly` | 2.234 | 1.939 | 445/1239 | 16104 | 353 |
| 20240401 | SM | `P|t60_ahead_ge2.0|armpts30|d0|lock0|p70always` | 3.138 | 2.473 | 346/530 | 12014 | 138 |
| 20240401 | PE | `P|sess_tot_ge2.0|armpts20|d10|trail30|p70never` | 1.329 | 1.288 | 145/1220 | 3901 | 333 |
| 20240401 | PB | `P|sess_tot_ge2.0|armpct0.3|d10|trail30|p70thickonly` | 1.998 | 1.863 | 198/998 | 4411 | 278 |
| 20240401 | DN | `P|hour_tot_ge1.5|armpts15|d0|trail20|p70always` | 2.009 | 1.35 | 635/877 | 3942 | 228 |
| 20240401 | MV | `P|sess_ahead_ge3.0|armpts10|d0|trail30|p70always` | 2.515 | 1.893 | 718/1210 | 19163 | 345 |
| 20240401 | MA | `P|sess_ahead_ge2.0|armpts30|d0|trail10|p70thickonly` | 1.213 | 0.801 | 267/620 | 1401 | 167 |
| 20240701 | ST | `P|sess_ahead_ge3.0|armpts10|d10|trail30|p70never` | 0.947 | 0.928 | 73/1273 | 2529 | 615 |
| 20240701 | HM | `P|hour_tot_ge1.5|armpts15|d0|trail10|p70never` | 1.698 | 1.261 | 602/1081 | 2251 | 464 |
| 20240701 | WT | `P|t60_tot_ge1.2|armpts30|d0|trail30|p70never` | 0.34 | 0.306 | 100/1941 | 1517 | 855 |
| 20240701 | KB | `P|sess_ahead_ge2.0|armpts15|d30|lock0|p70never` | 0.835 | 0.802 | 115/1324 | 1019 | 656 |
| 20240701 | SM | `P|t60_ahead_ge1.5|armpts30|d30|trail10|p70always` | 2.634 | 1.953 | 336/547 | 13420 | 180 |
| 20240701 | PE | `P|z_tot_ge2.0|armpts20|d30|trail30|p70always` | 1.244 | 0.579 | 814/1279 | 5985 | 615 |
| 20240701 | PB | `P|sess_tot_ge2.0|armpct0.3|d10|trail30|p70thickonly` | 1.179 | 1.046 | 193/1048 | 3376 | 461 |
| 20240701 | DN | `P|hour_tot_ge1.5|armpts15|d0|trail30|p70always` | 2.327 | 1.65 | 655/907 | 7400 | 361 |
| 20240701 | MV | `P|hour_tot_ge1.5|armpct0.3|d30|lock0|p70thickonly` | 1.749 | 1.455 | 395/1285 | 7674 | 587 |
| 20240701 | MA | `P|z_ahead_ge1.0|armpts20|d30|lock0|p70never` | 1.406 | 1.245 | 193/635 | 1411 | 211 |
| 20241001 | ST | `P|t60_ahead_ge3.0|armpts30|d0|trail20|p70never` | 0.752 | 0.681 | 130/1565 | 1776 | 450 |
| 20241001 | HM | `P|t60_ahead_ge3.0|armpts30|d0|trail20|p70never` | 0.719 | 0.652 | 106/1268 | 524 | 348 |
| 20241001 | WT | `P|hour_ahead_ge1.2|armpts30|d0|trail10|p70never` | 0.297 | 0.169 | 256/2281 | 1767 | 666 |
| 20241001 | KB | `P|sess_ahead_ge2.0|armpct0.3|d30|lock0|p70never` | 0.322 | 0.294 | 99/1637 | 252 | 443 |
| 20241001 | SM | `P|hour_ahead_ge2.0|armpts20|d10|lock5|p70always` | 1.572 | 0.852 | 375/587 | 1916 | 158 |
| 20241001 | PE | `P|hour_tot_ge2.0|armpts10|d0|lock10|p70always` | 1.264 | 0.569 | 965/1561 | 2775 | 436 |
| 20241001 | PB | `P|sess_tot_ge2.0|armpct0.3|d0|trail10|p70never` | 1.186 | 1.028 | 267/1239 | 3145 | 344 |
| 20241001 | DN | `P|t60_ahead_ge1.5|armpts15|d0|lock0|p70never` | 0.769 | 0.439 | 527/1030 | 796 | 273 |
| 20241001 | MV | `P|t60_tot_ge2.0|armpts10|d0|lock5|p70never` | 1.722 | 1.613 | 276/1541 | 9794 | 411 |
| 20241001 | MA | `P|t60_tot_ge1.2|armpts20|d0|lock0|p70never` | 1.226 | 0.951 | 309/679 | 830 | 176 |
| 20250101 | ST | `P|t60_tot_ge1.2|armpts30|d10|trail30|p70thickonly` | 0.865 | 0.29 | 929/1727 | 1592 | 649 |
| 20250101 | HM | `P|t60_tot_ge1.2|armpct0.7|d30|lock5|p70never` | 0.778 | 0.725 | 118/1374 | 780 | 472 |
| 20250101 | WT | `P|hour_tot_ge1.5|armpct0.5|d30|trail5|p70never` | 0.227 | 0.15 | 187/2513 | 639 | 898 |
| 20250101 | KB | `P|hour_tot_ge2.0|armpts15|d30|trail30|p70never` | 0.167 | 0.147 | 46/1771 | 22 | 664 |
| 20250101 | SM | `P|t60_tot_ge2.0|armpts30|d10|trail10|p70never` | 0.675 | 0.606 | 44/614 | 327 | 165 |
| 20250101 | PE | `P|hour_ahead_ge2.0|armpts10|d30|trail10|p70always` | 0.84 | 0.129 | 1021/1709 | 274 | 658 |
| 20250101 | PB | `P|hour_tot_ge2.0|armpct0.3|d0|lock10|p70never` | 1.548 | 1.474 | 172/1351 | 5559 | 471 |
| 20250101 | DN | `P|t60_tot_ge1.2|armpts20|d0|trail30|p70thickonly` | 0.804 | 0.152 | 758/1093 | 939 | 365 |
| 20250101 | MV | `P|t60_tot_ge1.2|armpts40|d10|lock10|p70thickonly` | 1.288 | 0.717 | 820/1661 | 7270 | 621 |
| 20250101 | MA | `P|t60_tot_ge2.0|armpts20|d10|trail30|p70never` | 0.384 | 0.335 | 45/707 | 55 | 219 |
| 20250401 | ST | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never` | 0.619 | 0.583 | 87/2067 | 387 | 750 |
| 20250401 | HM | `P|t60_ahead_ge1.5|armpts40|d30|lock10|p70never` | 0.659 | 0.603 | 83/1570 | 568 | 541 |
| 20250401 | WT | `P|sess_tot_ge1.2|armpts10|d30|lock5|p70never` | 0.46 | 0.208 | 592/2938 | 577 | 1017 |
| 20250401 | KB | `P|sess_tot_ge2.0|armpct0.7|d30|lock0|p70thickonly` | 0.169 | 0.007 | 190/2116 | 47 | 771 |
| 20250401 | SM | `P|t60_tot_ge2.0|armpts30|d10|trail10|p70never` | 0.8 | 0.692 | 51/641 | 661 | 174 |
| 20250401 | PE | `P|hour_ahead_ge2.0|armpts10|d30|take|p70always` | 1.628 | 0.496 | 1210/2042 | 1275 | 788 |
| 20250401 | PB | `P|hour_tot_ge2.0|armpct0.3|d0|trail10|p70always` | 1.392 | 0.294 | 908/1554 | 1457 | 532 |
| 20250401 | DN | `P|hour_ahead_ge2.0|armpts10|d30|lock5|p70never` | 0.697 | 0.618 | 98/1227 | 1381 | 386 |
| 20250401 | MV | `P|t60_ahead_ge1.5|armpts20|d30|take|p70thickonly` | 1.354 | 0.641 | 795/1964 | 1545 | 750 |
| 20250401 | MA | `P|t60_ahead_ge3.0|armpts30|d0|trail30|p70never` | 0.562 | 0.5 | 52/773 | 251 | 220 |
| 20250701 | ST | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70thickonly` | 0.579 | 0.349 | 261/2464 | 449 | 413 |
| 20250701 | HM | `P|t60_ahead_ge1.5|armpts40|d30|lock10|p70never` | 0.602 | 0.525 | 98/1825 | 901 | 322 |
| 20250701 | WT | `P|hour_tot_ge1.5|armpts10|d30|trail5|p70thickonly` | 0.544 | 0.08 | 672/3436 | 925 | 588 |
| 20250701 | KB | `P|z_ahead_ge1.5|armpct0.7|d30|lock10|p70never` | 0.348 | 0.245 | 170/2534 | 240 | 407 |
| 20250701 | SM | `P|hour_ahead_ge3.0|armpts40|d0|take|p70never` | 0.985 | 0.788 | 62/677 | 961 | 143 |
| 20250701 | PE | `P|hour_ahead_ge2.0|armpts10|d30|take|p70always` | 1.492 | 0.083 | 1420/2497 | 781 | 385 |
| 20250701 | PB | `P|sess_ahead_ge1.5|armpts20|d30|trail10|p70always` | 1.86 | 0.44 | 1086/1808 | 1118 | 315 |
| 20250701 | DN | `P|hour_tot_ge2.0|armpct0.7|d10|lock0|p70thickonly` | 0.733 | 0.544 | 110/1385 | 1365 | 251 |
| 20250701 | MV | `P|t60_tot_ge1.2|armpct0.7|d0|lock5|p70thickonly` | 1.168 | 0.055 | 1096/2369 | 901 | 376 |
| 20250701 | MA | `P|t60_tot_ge1.5|armpts20|d30|lock10|p70never` | 0.612 | 0.517 | 60/826 | 268 | 179 |
| 20251001 | ST | `P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70thickonly` | 0.615 | 0.345 | 227/2262 | 114 | 681 |
| 20251001 | HM | `P|t60_tot_ge1.5|armpts30|d30|take|p70never` | 0.586 | 0.313 | 186/1683 | 394 | 483 |
| 20251001 | WT | `P|sess_ahead_ge1.5|armpts10|d30|take|p70thickonly` | 1.002 | 0.141 | 985/3168 | 1760 | 901 |
| 20251001 | KB | `P|hour_tot_ge1.2|armpct0.7|d30|lock10|p70never` | 0.23 | 0.083 | 189/2285 | 120 | 679 |
| 20251001 | SM | `P|t60_tot_ge1.2|armpts40|d0|take|p70never` | 1.683 | 0.164 | 351/640 | 1055 | 155 |
| 20251001 | PE | `P|t60_tot_ge1.5|armpct0.7|d30|take|p70never` | 0.174 | 0.023 | 125/2267 | 61 | 645 |
| 20251001 | PB | `P|hour_ahead_ge1.5|armpts20|d10|take|p70always` | 2.208 | 0.483 | 1082/1662 | 1164 | 455 |
| 20251001 | DN | `P|hour_ahead_ge1.5|armpts30|d10|take|p70thickonly` | 1.366 | 0.253 | 532/1275 | 2339 | 385 |
| 20251001 | MV | `P|t60_ahead_ge1.5|armpts15|d30|lock0|p70thickonly` | 1.101 | 0.06 | 823/2158 | 272 | 605 |
| 20251001 | MA | `P|t60_tot_ge1.5|armpts15|d30|trail5|p70never` | 1.244 | 0.967 | 102/794 | 236 | 208 |
| 20260101 | ST | `P|t60_ahead_ge3.0|armpts15|d0|lock5|p70always` | 1.994 | 0.026 | 1432/2493 | 928 | 288 |
| 20260101 | HM | `P|sess_tot_ge1.5|armpts10|d0|lock0|p70never` | 0.699 | 0.05 | 645/1818 | 500 | 203 |
| 20260101 | WT | `P|sess_ahead_ge1.5|armpts10|d30|take|p70thickonly` | 1.041 | 0.099 | 976/3404 | 1068 | 404 |
| 20260101 | KB | `P|hour_tot_ge1.2|armpct0.7|d30|trail30|p70thickonly` | 1.266 | 0.148 | 817/2521 | 453 | 288 |
| 20260101 | SM | `P|sess_tot_ge1.5|armpct0.3|d30|trail5|p70thickonly` | 1.502 | 0.526 | 213/637 | 1121 | 65 |
| 20260101 | PE | `P|t60_tot_ge2.0|armpts30|d0|take|p70never` | 0.621 | 0.025 | 485/2476 | 194 | 281 |
| 20260101 | PB | `P|t60_ahead_ge2.0|armpts30|d0|take|p70never` | 1.112 | 0.043 | 618/1773 | 241 | 195 |
| 20260101 | DN | `P|hour_ahead_ge1.5|armpts30|d10|take|p70thickonly` | 1.369 | 0.137 | 542/1387 | 1920 | 146 |
| 20260101 | MV | `P|t60_tot_ge1.5|armpts20|d30|trail5|p70never` | 0.373 | 0.067 | 260/2352 | 78 | 272 |
| 20260101 | MA | `P|t60_tot_ge1.5|armpts15|d30|take|p70thickonly` | 1.142 | 0.135 | 253/826 | 221 | 87 |

#### LAST RE-FIT IN FULL - re-fit 2026-01-01 (applied to 2026-01-01..2026-02-06) (pooled); fit trades 19687 (closed before re-fit, entries in the trailing 12 months)

pooled: fit n=19687, eligible cells (fires>=100, N>0, mean>0) = 88 of 23773; chosen = `P|t60_ahead_ge3.0|armpct0.5|d0|lock10|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_tot_ge3.0|armpct0.5|d0|take|p70always` | +1.133 | -0.885 | 11044 | no |
| 2 | `P|sess_tot_ge3.0|armpct0.5|d0|trail5|p70always` | +1.131 | -0.886 | 11043 | no |
| 3 | `P|sess_tot_ge3.0|armpct0.5|d0|half10|p70always` | +1.130 | -0.887 | 11044 | no |
| 4 | `P|sess_tot_ge3.0|armpct0.5|d0|trail10|p70always` | +1.128 | -0.889 | 11043 | no |
| 5 | `P|sess_tot_ge3.0|armpct0.5|d0|trail15|p70always` | +1.125 | -0.892 | 11041 | no |
| 6 | `P|sess_tot_ge3.0|armpts30|d0|take|p70always` | +1.122 | -0.895 | 11028 | no |
| 7 | `P|sess_tot_ge3.0|armpct0.5|d0|lock10|p70always` | +1.121 | -0.896 | 11026 | no |
| 8 | `P|sess_tot_ge3.0|armpts30|d0|trail5|p70always` | +1.120 | -0.897 | 11027 | no |
| 9 | `P|sess_tot_ge3.0|armpts30|d0|half10|p70always` | +1.119 | -0.898 | 11028 | no |
| 10 | `P|sess_tot_ge3.0|armpct0.5|d0|half20|p70always` | +1.117 | -0.900 | 11044 | no |
| 11 | `P|sess_tot_ge3.0|armpts30|d0|trail10|p70always` | +1.116 | -0.901 | 11027 | no |
| 12 | `P|sess_tot_ge3.0|armpts30|d0|trail15|p70always` | +1.115 | -0.902 | 11025 | no |

#### LAST RE-FIT IN FULL - re-fit 2026-01-01 (applied to 2026-01-01..2026-02-06) (book); fit trades 19687 (closed before re-fit, entries in the trailing 12 months)

ST: fit n=2493, eligible cells (fires>=40, N>0, mean>0) = 928 of 23773; chosen = `P|t60_ahead_ge3.0|armpts15|d0|lock5|p70always`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|t60_ahead_ge3.0|armpts15|d0|lock5|p70always` | +1.994 | +0.026 | 1432 | yes |
| 2 | `P|t60_ahead_ge3.0|armpts15|d0|lock0|p70always` | +1.937 | -0.031 | 1432 | no |
| 3 | `P|t60_ahead_ge3.0|armpts15|d0|lock10|p70always` | +1.931 | -0.039 | 1433 | no |
| 4 | `P|t60_ahead_ge3.0|armpct0.3|d0|lock5|p70always` | +1.900 | -0.068 | 1422 | no |
| 5 | `P|t60_ahead_ge1.2|armpts30|d30|lock5|p70always` | +1.900 | -0.075 | 1477 | no |
| 6 | `P|t60_ahead_ge1.2|armpct0.5|d30|lock5|p70always` | +1.900 | -0.075 | 1477 | no |
| 7 | `P|t60_ahead_ge3.0|armpts15|d0|trail10|p70always` | +1.895 | -0.077 | 1435 | no |
| 8 | `P|t60_ahead_ge1.5|armpts30|d10|lock5|p70always` | +1.884 | -0.092 | 1469 | no |

HM: fit n=1818, eligible cells (fires>=40, N>0, mean>0) = 500 of 23773; chosen = `P|sess_tot_ge1.5|armpts10|d0|lock0|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_tot_ge1.5|armpts10|d0|take|p70always` | +1.130 | -0.898 | 1281 | no |
| 2 | `P|sess_tot_ge1.5|armpts10|d0|half10|p70always` | +1.017 | -1.011 | 1281 | no |
| 3 | `P|sess_tot_ge1.5|armpts10|d0|half20|p70always` | +0.980 | -1.046 | 1281 | no |
| 4 | `P|sess_tot_ge1.5|armpts10|d0|trail5|p70always` | +0.942 | -1.084 | 1280 | no |
| 5 | `P|sess_tot_ge1.5|armpts10|d0|lock5|p70always` | +0.930 | -1.096 | 1279 | no |
| 6 | `P|sess_tot_ge1.5|armpts10|d0|trail10|p70always` | +0.903 | -1.123 | 1279 | no |
| 7 | `P|sess_tot_ge1.5|armpts10|d0|take|p70thickonly` | +0.900 | -0.408 | 938 | no |
| 8 | `P|sess_tot_ge1.5|armpts10|d0|take|p70never` | +0.900 | -0.408 | 938 | no |

WT: fit n=3404, eligible cells (fires>=40, N>0, mean>0) = 1068 of 23773; chosen = `P|sess_ahead_ge1.5|armpts10|d30|take|p70thickonly`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|t60_ahead_ge1.5|armpts15|d0|trail20|p70always` | +1.973 | -0.170 | 2192 | no |
| 2 | `P|sess_ahead_ge1.5|armpts10|d30|take|p70always` | +1.962 | -0.160 | 2044 | no |
| 3 | `P|sess_ahead_ge2.0|armpts10|d30|take|p70always` | +1.945 | -0.161 | 1966 | no |
| 4 | `P|t60_ahead_ge1.5|armpct0.5|d0|trail20|p70always` | +1.940 | -0.197 | 2137 | no |
| 5 | `P|sess_ahead_ge1.5|armpts10|d30|trail5|p70always` | +1.938 | -0.183 | 2043 | no |
| 6 | `P|t60_ahead_ge1.5|armpts15|d0|trail30|p70always` | +1.936 | -0.190 | 2177 | no |
| 7 | `P|sess_ahead_ge2.0|armpts10|d30|trail5|p70always` | +1.931 | -0.174 | 1965 | no |
| 8 | `P|t60_ahead_ge1.5|armpts15|d0|half20|p70always` | +1.931 | -0.245 | 2245 | no |

KB: fit n=2521, eligible cells (fires>=40, N>0, mean>0) = 453 of 23773; chosen = `P|hour_tot_ge1.2|armpct0.7|d30|trail30|p70thickonly`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|t60_tot_ge1.2|armpts40|d0|take|p70always` | +1.804 | -0.185 | 1480 | no |
| 2 | `P|t60_tot_ge1.2|armpct0.7|d0|trail5|p70always` | +1.744 | -0.232 | 1433 | no |
| 3 | `P|t60_tot_ge1.2|armpts40|d0|half10|p70always` | +1.740 | -0.246 | 1480 | no |
| 4 | `P|t60_tot_ge1.2|armpct0.7|d0|take|p70always` | +1.735 | -0.242 | 1434 | no |
| 5 | `P|t60_tot_ge1.2|armpct0.7|d0|half10|p70always` | +1.732 | -0.244 | 1434 | no |
| 6 | `P|t60_tot_ge1.2|armpct0.7|d0|trail10|p70always` | +1.729 | -0.245 | 1432 | no |
| 7 | `P|t60_tot_ge1.2|armpts40|d0|trail5|p70always` | +1.715 | -0.271 | 1478 | no |
| 8 | `P|sess_tot_ge1.5|armpct0.7|d0|trail10|p70always` | +1.701 | -0.265 | 1404 | no |

SM: fit n=637, eligible cells (fires>=40, N>0, mean>0) = 1121 of 23773; chosen = `P|sess_tot_ge1.5|armpct0.3|d30|trail5|p70thickonly`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_ahead_ge1.2|armpts40|d0|trail5|p70always` | +1.708 | -0.389 | 384 | no |
| 2 | `P|sess_ahead_ge1.2|armpts40|d0|take|p70always` | +1.631 | -0.466 | 384 | no |
| 3 | `P|sess_ahead_ge1.2|armpts40|d0|half10|p70always` | +1.620 | -0.476 | 384 | no |
| 4 | `P|sess_ahead_ge1.2|armpts40|d0|trail10|p70always` | +1.610 | -0.487 | 384 | no |
| 5 | `P|sess_ahead_ge1.5|armpts40|d0|trail5|p70always` | +1.569 | -0.527 | 380 | no |
| 6 | `P|sess_ahead_ge1.2|armpts40|d0|trail15|p70always` | +1.562 | -0.534 | 384 | no |
| 7 | `P|z_ahead_ge1.0|armpts40|d0|trail5|p70always` | +1.561 | -0.536 | 384 | no |
| 8 | `P|hour_ahead_ge1.2|armpts40|d0|trail5|p70always` | +1.548 | -0.549 | 384 | no |

PE: fit n=2476, eligible cells (fires>=40, N>0, mean>0) = 194 of 23773; chosen = `P|t60_tot_ge2.0|armpts30|d0|take|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|hour_ahead_ge1.5|armpct0.7|d30|lock0|p70always` | +1.085 | -0.857 | 1324 | no |
| 2 | `P|hour_ahead_ge2.0|armpts30|d30|lock10|p70always` | +1.079 | -0.863 | 1333 | no |
| 3 | `P|hour_ahead_ge2.0|armpct0.5|d30|lock10|p70always` | +1.079 | -0.863 | 1333 | no |
| 4 | `P|hour_tot_ge3.0|armpts15|d30|trail20|p70always` | +1.070 | -0.872 | 1322 | no |
| 5 | `P|hour_ahead_ge2.0|armpts40|d30|take|p70always` | +1.070 | -0.873 | 1322 | no |
| 6 | `P|hour_ahead_ge2.0|armpts40|d30|half20|p70always` | +1.069 | -0.873 | 1322 | no |
| 7 | `P|hour_ahead_ge2.0|armpts40|d30|trail20|p70always` | +1.069 | -0.873 | 1322 | no |
| 8 | `P|hour_tot_ge3.0|armpts15|d30|half20|p70always` | +1.064 | -0.878 | 1322 | no |

PB: fit n=1773, eligible cells (fires>=40, N>0, mean>0) = 241 of 23773; chosen = `P|t60_ahead_ge2.0|armpts30|d0|take|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_ahead_ge1.5|armpts20|d10|take|p70always` | +1.577 | -0.502 | 1167 | no |
| 2 | `P|hour_ahead_ge2.0|armpts30|d0|lock10|p70always` | +1.520 | -0.548 | 1078 | no |
| 3 | `P|hour_ahead_ge2.0|armpct0.5|d0|lock10|p70always` | +1.520 | -0.548 | 1078 | no |
| 4 | `P|t60_ahead_ge2.0|armpct0.5|d0|lock10|p70always` | +1.500 | -0.570 | 1081 | no |
| 5 | `P|t60_ahead_ge2.0|armpts30|d0|lock10|p70always` | +1.500 | -0.570 | 1081 | no |
| 6 | `P|sess_ahead_ge1.5|armpts20|d10|half10|p70always` | +1.480 | -0.599 | 1167 | no |
| 7 | `P|z_ahead_ge2.0|armpct0.7|d10|take|p70always` | +1.473 | -0.590 | 1019 | no |
| 8 | `P|z_ahead_ge2.0|armpct0.7|d10|half10|p70always` | +1.473 | -0.590 | 1019 | no |

DN: fit n=1387, eligible cells (fires>=40, N>0, mean>0) = 1920 of 23773; chosen = `P|hour_ahead_ge1.5|armpts30|d10|take|p70thickonly`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|hour_ahead_ge1.5|armpct0.5|d10|take|p70always` | +1.454 | -0.620 | 850 | no |
| 2 | `P|hour_ahead_ge1.5|armpts30|d10|take|p70always` | +1.454 | -0.620 | 850 | no |
| 3 | `P|hour_ahead_ge1.5|armpts30|d10|half10|p70always` | +1.390 | -0.683 | 850 | no |
| 4 | `P|hour_ahead_ge1.5|armpct0.5|d10|half10|p70always` | +1.390 | -0.683 | 850 | no |
| 5 | `P|hour_ahead_ge1.5|armpts30|d10|trail5|p70always` | +1.384 | -0.687 | 849 | no |
| 6 | `P|hour_ahead_ge1.5|armpct0.5|d10|trail5|p70always` | +1.384 | -0.687 | 849 | no |
| 7 | `P|hour_ahead_ge1.5|armpct0.5|d10|take|p70thickonly` | +1.369 | +0.137 | 542 | yes |
| 8 | `P|hour_ahead_ge1.5|armpts30|d10|take|p70thickonly` | +1.369 | +0.137 | 542 | yes |

MV: fit n=2352, eligible cells (fires>=40, N>0, mean>0) = 78 of 23773; chosen = `P|t60_tot_ge1.5|armpts20|d30|trail5|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_tot_ge1.2|armpts10|d30|take|p70always` | +1.465 | -0.533 | 1532 | no |
| 2 | `P|sess_tot_ge1.2|armpts10|d30|trail5|p70always` | +1.419 | -0.577 | 1531 | no |
| 3 | `P|sess_tot_ge1.2|armpct0.3|d30|take|p70always` | +1.395 | -0.601 | 1470 | no |
| 4 | `P|sess_tot_ge1.2|armpts20|d30|take|p70always` | +1.351 | -0.645 | 1455 | no |
| 5 | `P|sess_tot_ge1.2|armpts15|d30|take|p70always` | +1.349 | -0.648 | 1488 | no |
| 6 | `P|sess_tot_ge1.2|armpts10|d30|half10|p70always` | +1.343 | -0.654 | 1532 | no |
| 7 | `P|sess_tot_ge1.2|armpct0.3|d30|trail5|p70always` | +1.333 | -0.662 | 1469 | no |
| 8 | `P|sess_tot_ge1.2|armpts20|d30|trail5|p70always` | +1.323 | -0.672 | 1454 | no |

MA: fit n=826, eligible cells (fires>=40, N>0, mean>0) = 221 of 23773; chosen = `P|t60_tot_ge1.5|armpts15|d30|take|p70thickonly`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|t60_tot_ge1.5|armpts15|d30|take|p70thickonly` | +1.142 | +0.135 | 253 | yes |
| 2 | `P|t60_tot_ge1.5|armpts15|d30|trail5|p70thickonly` | +1.142 | +0.135 | 253 | yes |
| 3 | `P|t60_tot_ge1.5|armpct0.3|d30|trail5|p70thickonly` | +1.116 | +0.114 | 251 | yes |
| 4 | `P|t60_tot_ge1.5|armpct0.3|d30|take|p70thickonly` | +1.113 | +0.111 | 251 | yes |
| 5 | `P|t60_tot_ge1.5|armpts15|d30|half20|p70thickonly` | +1.084 | +0.092 | 253 | yes |
| 6 | `P|t60_tot_ge1.5|armpts15|d30|half10|p70thickonly` | +1.074 | +0.067 | 253 | yes |
| 7 | `P|t60_tot_ge1.5|armpct0.3|d30|half20|p70thickonly` | +1.072 | +0.085 | 251 | yes |
| 8 | `P|t60_tot_ge1.5|armpct0.3|d30|half10|p70thickonly` | +1.051 | +0.049 | 251 | yes |

#### LAST RE-FIT IN FULL - as-of 2026-02-06 (what the nightly script would publish for the next label day) (pooled); fit trades 19905 (closed before re-fit, entries in the trailing 12 months)

pooled: fit n=19905, eligible cells (fires>=100, N>0, mean>0) = 61 of 23773; chosen = `P|sess_tot_ge3.0|armpct0.5|d0|trail5|p70never`
| rank by fit mean | cell | fit mean | fit N mean | fires | eligible |
|---|---|---|---|---|---|
| 1 | `P|sess_tot_ge1.5|armpct0.7|d0|take|p70always` | +1.139 | -0.899 | 11186 | no |
| 2 | `P|sess_tot_ge1.5|armpct0.7|d0|half10|p70always` | +1.136 | -0.901 | 11186 | no |
| 3 | `P|sess_tot_ge3.0|armpct0.5|d0|trail5|p70always` | +1.135 | -0.903 | 11250 | no |
| 4 | `P|sess_tot_ge1.5|armpct0.7|d0|trail10|p70always` | +1.134 | -0.903 | 11182 | no |
| 5 | `P|t60_ahead_ge2.0|armpct0.7|d0|trail15|p70always` | +1.134 | -0.904 | 11146 | no |
| 6 | `P|sess_tot_ge1.5|armpct0.7|d0|trail30|p70always` | +1.133 | -0.903 | 11174 | no |
| 7 | `P|t60_tot_ge1.5|armpct0.7|d0|take|p70always` | +1.132 | -0.911 | 11258 | no |
| 8 | `P|sess_tot_ge3.0|armpct0.5|d0|take|p70always` | +1.132 | -0.906 | 11255 | no |

## 4. Cross with the take-at-70% path rule: only-when-thick vs always vs never
For the pooled PRE-selected cell and the rank-1 cell of each scope, the same arm/thick/duration/action under the three path-rule modes (never = cell alone; always = cell + unconditional take at pct >= 0.70; thickonly = cell + take at pct >= 0.70 only when the same thick definition holds). "d vs REF" = cell minus the plain take-at-70% (REF) mean, same scope, same window, M basis.
| scope | variant | tier | L6M | HOLD | PRE | N L6M/HOLD/PRE | d vs REF L6M / HOLD / PRE | failed gates |
|---|---|---|---|---|---|---|---|---|
| pooled | `P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70never` | DEAD | -0.05 [-0.32,+0.22] MDE 0.39 [313] | -0.06 [-0.32,+0.19] MDE 0.36 [344] | +0.17 [-0.00,+0.35] MDE 0.25 [736] | -0.13/-0.14/+0.13 | -0.91 / -1.01 / -0.21 | G1_PRE_CI,G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05 |
| pooled | `P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70always` | CANDIDATE-RECENT | +0.89 [+0.13,+1.66] MDE 1.09 [5578] | +0.97 [+0.26,+1.67] MDE 1.01 [6116] | +0.38 [-0.10,+0.87] MDE 0.69 [13665] | -1.22/-1.11/-0.91 | +0.03 / +0.02 / -0.00 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| pooled | `P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70thickonly` | DEAD | +0.10 [-0.19,+0.38] MDE 0.40 [694] | +0.09 [-0.17,+0.36] MDE 0.38 [769] | +0.15 [-0.04,+0.33] MDE 0.27 [1505] | -0.15/-0.15/+0.02 | -0.76 / -0.85 / -0.24 | G1_PRE_CI,G3_Xp,G5_Nbasis,G7_RC05 |
| pooled | `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70never` | DEAD | -0.21 [-0.77,+0.34] MDE 0.80 [1163] | -0.25 [-0.78,+0.28] MDE 0.75 [1379] | -0.22 [-0.57,+0.13] MDE 0.50 [3167] | -0.52/-0.57/-0.43 | -1.08 / -1.19 / -0.61 | G1_PRE_CI,G2_HOLD,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| pooled | `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always` | CANDIDATE-RECENT | +1.04 [+0.24,+1.83] MDE 1.14 [5648] | +1.07 [+0.33,+1.81] MDE 1.06 [6198] | +0.34 [-0.16,+0.84] MDE 0.72 [13801] | -1.07/-1.01/-0.96 | +0.18 / +0.12 / -0.05 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| pooled | `P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70thickonly` | CANDIDATE-RECENT | +0.18 [-0.44,+0.80] MDE 0.88 [3211] | +0.26 [-0.32,+0.85] MDE 0.83 [3653] | -0.00 [-0.40,+0.40] MDE 0.57 [8332] | -0.99/-0.92/-0.75 | -0.68 / -0.68 / -0.39 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| ST | `P|sess_ahead_ge3.0|armpts20|d0|lock5|p70never` | DEAD | +0.71 [-0.10,+1.52] MDE 1.16 [98] | +0.75 [-0.03,+1.54] MDE 1.12 [115] | -0.26 [-0.80,+0.28] MDE 0.77 [237] | +0.60/+0.64/-0.36 | -1.34 / -1.24 / -0.52 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| ST | `P|sess_ahead_ge3.0|armpts20|d0|lock5|p70always` | CANDIDATE-RECENT | +2.50 [+0.78,+4.22] MDE 2.45 [766] | +2.52 [+0.89,+4.15] MDE 2.33 [834] | +0.01 [-1.02,+1.04] MDE 1.47 [1703] | +0.41/+0.48/-1.28 | +0.45 / +0.52 / -0.25 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| ST | `P|sess_ahead_ge3.0|armpts20|d0|lock5|p70thickonly` | CANDIDATE-RECENT | +0.86 [+0.03,+1.69] MDE 1.18 [147] | +0.91 [+0.11,+1.71] MDE 1.14 [173] | -0.21 [-0.76,+0.34] MDE 0.79 [351] | +0.59/+0.63/-0.41 | -1.19 / -1.09 / -0.47 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| HM | `P|sess_ahead_ge1.5|armpct0.3|d10|take|p70never` | CANDIDATE-RECENT | +0.91 [-1.12,+2.94] MDE 2.90 [342] | +1.11 [-0.88,+3.10] MDE 2.85 [403] | -0.67 [-1.97,+0.64] MDE 1.86 [894] | -0.09/+0.07/-1.33 | +1.22 / +1.41 / -0.47 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| HM | `P|sess_ahead_ge1.5|armpct0.3|d10|take|p70always` | CANDIDATE-RECENT | +1.00 [-1.35,+3.35] MDE 3.36 [603] | +1.28 [-1.00,+3.56] MDE 3.26 [671] | -0.87 [-2.32,+0.59] MDE 2.08 [1456] | -1.11/-0.78/-2.16 | +1.31 / +1.58 / -0.67 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| HM | `P|sess_ahead_ge1.5|armpct0.3|d10|take|p70thickonly` | CANDIDATE-RECENT | +0.94 [-1.13,+3.01] MDE 2.96 [397] | +1.19 [-0.85,+3.24] MDE 2.92 [459] | -0.68 [-2.01,+0.64] MDE 1.90 [1009] | -0.30/-0.07/-1.47 | +1.25 / +1.50 / -0.49 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| WT | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70never` | DEAD | +0.30 [-0.37,+0.96] MDE 0.95 [265] | +0.44 [-0.24,+1.13] MDE 0.98 [330] | +0.04 [-0.41,+0.49] MDE 0.64 [750] | -0.08/+0.02/-0.23 | -1.39 / -1.45 / -0.53 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| WT | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | CANDIDATE-RECENT | +2.20 [+1.27,+3.14] MDE 1.33 [1082] | +2.36 [+1.45,+3.28] MDE 1.31 [1202] | +0.51 [-0.08,+1.10] MDE 0.85 [2600] | -0.03/+0.15/-0.85 | +0.52 / +0.47 / -0.06 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| WT | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70thickonly` | CANDIDATE-RECENT | +0.90 [+0.15,+1.64] MDE 1.06 [656] | +1.13 [+0.37,+1.88] MDE 1.08 [761] | +0.37 [-0.14,+0.88] MDE 0.73 [1718] | -0.42/-0.22/-0.47 | -0.79 / -0.77 / -0.19 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| KB | `P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70never` | CANDIDATE-RECENT | +0.09 [-0.91,+1.10] MDE 1.44 [148] | +0.02 [-0.94,+0.98] MDE 1.37 [166] | -0.19 [-0.87,+0.48] MDE 0.97 [401] | -0.21/-0.29/-0.42 | -0.78 / -1.11 / -0.21 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| KB | `P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70always` | CANDIDATE-RECENT | +1.36 [-0.15,+2.88] MDE 2.16 [711] | +1.58 [+0.13,+3.03] MDE 2.07 [772] | +0.04 [-0.93,+1.02] MDE 1.40 [1732] | -0.67/-0.41/-1.27 | +0.49 / +0.45 / +0.03 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| KB | `P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70thickonly` | CANDIDATE-RECENT | +0.40 [-0.66,+1.45] MDE 1.51 [269] | +0.33 [-0.68,+1.34] MDE 1.44 [298] | -0.28 [-0.97,+0.42] MDE 1.00 [736] | -0.31/-0.39/-0.78 | -0.48 / -0.80 / -0.29 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| SM | `P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70never` | CANDIDATE-RECENT | +3.57 [-1.40,+8.55] MDE 7.11 [215] | +2.02 [-2.60,+6.64] MDE 6.60 [253] | -1.45 [-4.17,+1.27] MDE 3.89 [564] | +1.79/+0.16/-2.46 | +2.05 / +0.20 / -1.06 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| SM | `P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70always` | CANDIDATE-RECENT | +3.48 [-1.53,+8.48] MDE 7.15 [240] | +2.01 [-2.65,+6.66] MDE 6.66 [279] | -1.41 [-4.24,+1.42] MDE 4.04 [659] | +1.37/-0.14/-2.69 | +1.95 / +0.19 / -1.03 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| SM | `P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70thickonly` | CANDIDATE-RECENT | +3.60 [-1.37,+8.58] MDE 7.11 [216] | +2.06 [-2.56,+6.68] MDE 6.60 [254] | -1.43 [-4.16,+1.29] MDE 3.89 [568] | +1.80/+0.19/-2.46 | +2.08 / +0.25 / -1.05 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PE | `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70never` | DEAD | -0.30 [-1.21,+0.61] MDE 1.30 [178] | -0.55 [-1.50,+0.39] MDE 1.34 [224] | -0.34 [-0.95,+0.28] MDE 0.88 [462] | -0.78/-1.09/-0.62 | -0.96 / -1.15 / -1.45 | G1_PRE_CI,G2_HOLD,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| PE | `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70always` | CANDIDATE-RECENT | +1.01 [-0.59,+2.61] MDE 2.28 [671] | +0.71 [-0.83,+2.24] MDE 2.20 [742] | +0.87 [-0.21,+1.95] MDE 1.55 [1718] | -0.97/-1.28/-0.41 | +0.36 / +0.11 / -0.24 | G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 |
| PE | `P|hour_ahead_ge1.5|armpct0.5|d30|take|p70thickonly` | DEAD | -0.08 [-1.15,+1.00] MDE 1.53 [339] | -0.30 [-1.39,+0.78] MDE 1.56 [396] | +0.16 [-0.64,+0.96] MDE 1.15 [931] | -1.07/-1.34/-0.50 | -0.73 / -0.90 / -0.95 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 |
| PB | `P|z_ahead_ge1.0|armpts30|d0|lock10|p70never` | DEAD | -0.01 [-2.07,+2.04] MDE 2.94 [281] | +0.20 [-1.79,+2.18] MDE 2.83 [321] | +0.26 [-1.05,+1.57] MDE 1.87 [721] | -0.76/-0.55/-0.19 | -0.12 / -0.28 / -0.89 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| PB | `P|z_ahead_ge1.0|armpts30|d0|lock10|p70always` | CANDIDATE-RECENT | +1.04 [-1.35,+3.43] MDE 3.41 [595] | +1.34 [-0.94,+3.63] MDE 3.26 [655] | +0.68 [-0.85,+2.21] MDE 2.19 [1414] | -1.19/-0.82/-0.60 | +0.94 / +0.87 / -0.47 | G1_PRE_CI,G3_Xp,G5_Nbasis,G7_RC05,G8_placebo95 |
| PB | `P|z_ahead_ge1.0|armpts30|d0|lock10|p70thickonly` | CANDIDATE-RECENT | +0.42 [-1.78,+2.62] MDE 3.14 [470] | +0.60 [-1.51,+2.70] MDE 3.01 [526] | +0.34 [-1.11,+1.78] MDE 2.07 [1179] | -1.24/-1.04/-0.65 | +0.32 / +0.12 / -0.81 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| DN | `P|sess_ahead_ge2.0|armpct0.3|d0|take|p70never` | DEAD | +0.81 [-1.57,+3.19] MDE 3.40 [287] | +0.74 [-1.55,+3.03] MDE 3.27 [328] | -0.75 [-2.30,+0.79] MDE 2.21 [747] | -0.35/-0.44/-1.50 | +0.44 / +0.16 / -0.98 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| DN | `P|sess_ahead_ge2.0|armpct0.3|d0|take|p70always` | DEAD | +1.28 [-1.49,+4.04] MDE 3.95 [481] | +1.29 [-1.35,+3.94] MDE 3.77 [531] | -0.51 [-2.24,+1.22] MDE 2.47 [1165] | -0.92/-0.86/-1.85 | +0.90 / +0.72 / -0.73 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| DN | `P|sess_ahead_ge2.0|armpct0.3|d0|take|p70thickonly` | DEAD | +0.81 [-1.57,+3.19] MDE 3.40 [287] | +0.74 [-1.55,+3.03] MDE 3.27 [328] | -0.75 [-2.30,+0.79] MDE 2.21 [747] | -0.35/-0.44/-1.50 | +0.44 / +0.16 / -0.98 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MV | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70never` | DEAD | +0.36 [-1.30,+2.02] MDE 2.37 [320] | +0.24 [-1.40,+1.88] MDE 2.35 [381] | -1.00 [-2.08,+0.08] MDE 1.54 [936] | -0.30/-0.46/-1.49 | -0.59 / -0.47 / -1.74 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MV | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always` | DEAD | +1.72 [-0.34,+3.78] MDE 2.94 [740] | +1.41 [-0.56,+3.38] MDE 2.82 [819] | -0.40 [-1.72,+0.91] MDE 1.88 [1893] | -0.34/-0.61/-1.73 | +0.78 / +0.70 / -1.15 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MV | `P|sess_ahead_ge1.2|armpts15|d30|trail20|p70thickonly` | CANDIDATE-RECENT | +1.10 [-0.69,+2.89] MDE 2.56 [512] | +0.91 [-0.84,+2.66] MDE 2.50 [586] | -0.70 [-1.89,+0.50] MDE 1.70 [1417] | -0.22/-0.42/-1.59 | +0.15 / +0.20 / -1.44 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MA | `P|t60_tot_ge2.0|armpts10|d0|trail20|p70never` | CANDIDATE-RECENT | +1.13 [-1.66,+3.91] MDE 3.98 [103] | +0.68 [-1.80,+3.17] MDE 3.55 [117] | -1.93 [-3.43,-0.44] MDE 2.13 [248] | +0.51/+0.08/-2.34 | +2.51 / +2.03 / -0.58 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MA | `P|t60_tot_ge2.0|armpts10|d0|trail20|p70always` | DEAD | -0.19 [-3.43,+3.05] MDE 4.63 [269] | -0.44 [-3.34,+2.46] MDE 4.15 [304] | -2.70 [-4.54,-0.85] MDE 2.64 [650] | -2.42/-2.59/-3.95 | +1.19 / +0.91 / -1.34 | G1_PRE_CI,G2_HOLD,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |
| MA | `P|t60_tot_ge2.0|armpts10|d0|trail20|p70thickonly` | CANDIDATE-RECENT | +1.35 [-1.43,+4.13] MDE 3.97 [114] | +0.90 [-1.59,+3.39] MDE 3.56 [129] | -1.91 [-3.41,-0.41] MDE 2.14 [268] | +0.63/+0.19/-2.37 | +2.73 / +2.25 / -0.56 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 |

Marginal over ALL F1 cells, pooled (mean of the cell means; share of cells > 0):
| path-rule mode | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| never | 7920 | -0.347 / 0.11 | -0.412 / 0.05 | -0.491 / 0.04 | -0.325 / 0.28 | -0.694 / -0.979 / -1.044 | -0.669 / -0.932 |
| always | 7920 | +0.063 / 0.64 | +0.635 / 0.93 | +0.538 / 0.88 | +0.814 / 0.89 | -1.245 / -1.450 / -1.584 | -0.358 / -0.305 |
| thickonly | 7920 | -0.261 / 0.22 | -0.157 / 0.29 | -0.253 / 0.23 | +0.025 / 0.56 | -0.855 / -1.124 / -1.211 | -0.572 / -0.762 |

## 5. Inverse: thin book ahead -> do nothing (skip the 70% take) / widen the target
"Widen target by 10-20 pts when the book ahead is thin" is **UNTESTABLE on this store** (the 10-s path ends at the original bracket exit; a widened target needs the post-exit 1-s price path; not built). Do-nothing cells (take at 70% except when thin) vs hold, and vs REF (the plain 70% rule), pooled and per book:
| role | cell | tier | 2026 (5 wk) pts/trade [fired] | last 6 mo [fired] | HOLD | PRE | X' | N basis L6M/HOLD/PRE | vs random exit L6M/PRE | shuffled-book rank (PRE) | RC p (best-of-N, PRE) | $/wk L6M at live lots | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE-selected G2 WT | `I|z_ahead_le-1.0|d0|skip_p70_if_thin` | DEAD | -0.09 (MDE 1.7) [186] | +0.85 [+0.17,+1.52] MDE 0.97 [841] | +1.13 [+0.45,+1.81] MDE 0.97 [937] | +0.59 [+0.12,+1.07] MDE 0.68 [2038] | -0.29 | -1.04/-0.75/-0.53 | +0.98/+1.59 | 1.00 | 0.02 | +7,210 | G3_Xp,G5_Nbasis |
| PRE-selected G2 SM | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +9.85 (MDE 13.0) [42] | +1.76 [-1.45,+4.98] MDE 4.59 [176] | +2.03 [-1.04,+5.09] MDE 4.37 [209] | -0.25 [-2.05,+1.56] MDE 2.57 [506] | +2.23 | -0.27/-0.05/-1.46 | +2.44/+3.30 | 1.00 | 0.67 | +2,927 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05 |
| PRE-selected G2 PE | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +2.94 (MDE 5.1) [142] | +0.57 [-0.88,+2.01] MDE 2.06 [624] | +0.44 [-0.93,+1.81] MDE 1.95 [686] | +1.13 [+0.13,+2.13] MDE 1.42 [1593] | +0.43 | -1.36/-1.48/-0.08 | +2.81/+3.20 | 0.00 | 0.02 | +2,700 | G4_2xcost,G5_Nbasis,G8_placebo95 |
| PRE-selected G2 PB | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.53 (MDE 5.1) [108] | +0.24 [-1.60,+2.07] MDE 2.62 [502] | +0.60 [-1.15,+2.35] MDE 2.50 [550] | +1.22 [+0.02,+2.43] MDE 1.72 [1195] | -0.10 | -1.92/-1.50/-0.00 | +2.61/+3.20 | 1.00 | 0.02 | +1,461 | G3_Xp,G5_Nbasis |
| PRE-selected G2 DN | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.02 (MDE 6.6) [98] | +0.20 [-1.85,+2.25] MDE 2.93 [402] | +0.45 [-1.49,+2.40] MDE 2.78 [440] | +0.28 [-1.02,+1.58] MDE 1.85 [978] | -0.26 | -1.92/-1.62/-0.99 | +2.33/+2.77 | 1.00 | 0.40 | +993 | G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05 |
| PRE-selected G2 MV | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | DEAD | -0.08 (MDE 4.4) [150] | +0.90 [-0.69,+2.50] MDE 2.27 [614] | +0.68 [-0.80,+2.16] MDE 2.11 [669] | +0.86 [-0.16,+1.87] MDE 1.45 [1552] | +1.64 | -1.08/-1.28/-0.38 | +3.45/+2.89 | 1.00 | 0.04 | +7,313 | G1_PRE_CI,G5_Nbasis |

All 12 thin-skip cells, pooled:
| role | cell | tier | 2026 (5 wk) pts/trade [fired] | last 6 mo [fired] | HOLD | PRE | X' | N basis L6M/HOLD/PRE | vs random exit L6M/PRE | shuffled-book rank (PRE) | RC p (best-of-N, PRE) | $/wk L6M at live lots | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| thin-skip | `I|hour_ahead_le0.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +1.26 (MDE 2.5) [1278] | +0.75 [+0.01,+1.49] MDE 1.06 [5420] | +0.83 [+0.14,+1.52] MDE 0.99 [5950] | +0.38 [-0.10,+0.86] MDE 0.68 [13166] | +0.34 | -1.31/-1.19/-0.87 | +2.50/+2.60 | 0.00 | 0.09 | +41,014 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|hour_ahead_le0.5|d10|skip_p70_if_thin` | CANDIDATE-RECENT | +1.26 (MDE 2.5) [1278] | +0.75 [+0.01,+1.49] MDE 1.06 [5420] | +0.83 [+0.14,+1.52] MDE 0.99 [5950] | +0.38 [-0.10,+0.86] MDE 0.68 [13166] | +0.34 | -1.31/-1.19/-0.87 | +2.50/+2.60 | 0.00 | 0.09 | +41,014 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|hour_ahead_le0.5|d30|skip_p70_if_thin` | CANDIDATE-RECENT | +1.26 (MDE 2.5) [1278] | +0.75 [+0.01,+1.49] MDE 1.06 [5420] | +0.83 [+0.14,+1.52] MDE 0.99 [5950] | +0.38 [-0.10,+0.86] MDE 0.68 [13166] | +0.34 | -1.31/-1.19/-0.87 | +2.50/+2.60 | 0.00 | 0.09 | +41,014 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|hour_ahead_le0.7|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +0.99 (MDE 2.4) [1205] | +0.65 [-0.07,+1.36] MDE 1.02 [5124] | +0.72 [+0.05,+1.39] MDE 0.96 [5630] | +0.19 [-0.27,+0.65] MDE 0.66 [12471] | +0.35 | -1.31/-1.20/-0.99 | +2.30/+2.29 | 0.00 | 0.09 | +35,808 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|hour_ahead_le0.7|d10|skip_p70_if_thin` | CANDIDATE-RECENT | +0.99 (MDE 2.4) [1205] | +0.65 [-0.07,+1.36] MDE 1.02 [5124] | +0.72 [+0.05,+1.39] MDE 0.96 [5630] | +0.19 [-0.27,+0.65] MDE 0.66 [12471] | +0.35 | -1.31/-1.20/-0.99 | +2.30/+2.29 | 0.00 | 0.09 | +35,808 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|hour_ahead_le0.7|d30|skip_p70_if_thin` | CANDIDATE-RECENT | +0.99 (MDE 2.4) [1205] | +0.65 [-0.07,+1.36] MDE 1.02 [5124] | +0.72 [+0.05,+1.39] MDE 0.96 [5630] | +0.19 [-0.27,+0.65] MDE 0.66 [12471] | +0.35 | -1.31/-1.20/-0.99 | +2.30/+2.29 | 0.00 | 0.09 | +35,808 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.0|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +0.67 (MDE 2.3) [1112] | +0.39 [-0.29,+1.08] MDE 0.98 [4798] | +0.49 [-0.15,+1.13] MDE 0.92 [5295] | +0.17 [-0.28,+0.61] MDE 0.64 [11830] | +0.36 | -1.45/-1.32/-0.94 | +1.94/+2.16 | 0.00 | 0.09 | +20,064 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.0|d10|skip_p70_if_thin` | CANDIDATE-RECENT | +0.67 (MDE 2.3) [1112] | +0.39 [-0.29,+1.08] MDE 0.98 [4798] | +0.49 [-0.15,+1.13] MDE 0.92 [5295] | +0.17 [-0.28,+0.61] MDE 0.64 [11830] | +0.36 | -1.45/-1.32/-0.94 | +1.94/+2.16 | 0.00 | 0.09 | +20,064 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.0|d30|skip_p70_if_thin` | CANDIDATE-RECENT | +0.67 (MDE 2.3) [1112] | +0.39 [-0.29,+1.08] MDE 0.98 [4798] | +0.49 [-0.15,+1.13] MDE 0.92 [5295] | +0.17 [-0.28,+0.61] MDE 0.64 [11830] | +0.36 | -1.45/-1.32/-0.94 | +1.94/+2.16 | 0.00 | 0.09 | +20,064 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.5|d0|skip_p70_if_thin` | CANDIDATE-RECENT | +0.82 (MDE 2.4) [1163] | +0.56 [-0.15,+1.27] MDE 1.01 [4985] | +0.64 [-0.03,+1.30] MDE 0.95 [5487] | +0.14 [-0.32,+0.60] MDE 0.65 [12280] | +0.32 | -1.34/-1.24/-1.02 | +2.17/+2.21 | 0.00 | 0.09 | +30,530 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.5|d10|skip_p70_if_thin` | CANDIDATE-RECENT | +0.82 (MDE 2.4) [1163] | +0.56 [-0.15,+1.27] MDE 1.01 [4985] | +0.64 [-0.03,+1.30] MDE 0.95 [5487] | +0.14 [-0.32,+0.60] MDE 0.65 [12280] | +0.32 | -1.34/-1.24/-1.02 | +2.17/+2.21 | 0.00 | 0.09 | +30,530 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |
| thin-skip | `I|z_ahead_le-1.5|d30|skip_p70_if_thin` | CANDIDATE-RECENT | +0.82 (MDE 2.4) [1163] | +0.56 [-0.15,+1.27] MDE 1.01 [4985] | +0.64 [-0.03,+1.30] MDE 0.95 [5487] | +0.14 [-0.32,+0.60] MDE 0.65 [12280] | +0.32 | -1.34/-1.24/-1.02 | +2.17/+2.21 | 0.00 | 0.09 | +30,530 | G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 |

## 6. Descriptive marginals of the F1 grid, pooled (what each setting does on average; not a selection)

**action**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| trail 5 | 2160 | -0.184 / 0.32 | +0.056 / 0.43 | -0.051 / 0.39 | +0.198 / 0.61 | -0.980 / -1.227 / -1.338 | -0.544 / -0.670 |
| trail 10 | 2160 | -0.186 / 0.33 | +0.008 / 0.41 | -0.088 / 0.37 | +0.199 / 0.61 | -0.966 / -1.246 / -1.346 | -0.546 / -0.701 |
| trail 15 | 2160 | -0.204 / 0.31 | -0.030 / 0.39 | -0.127 / 0.36 | +0.183 / 0.59 | -0.963 / -1.253 / -1.353 | -0.558 / -0.729 |
| trail 20 | 2160 | -0.215 / 0.30 | -0.003 / 0.42 | -0.081 / 0.39 | +0.142 / 0.57 | -0.954 / -1.192 / -1.274 | -0.560 / -0.670 |
| trail 30 | 2160 | -0.169 / 0.34 | +0.016 / 0.42 | -0.051 / 0.39 | +0.174 / 0.58 | -0.873 / -1.115 / -1.188 | -0.495 / -0.610 |
| take | 2160 | -0.161 / 0.33 | +0.102 / 0.47 | -0.006 / 0.42 | +0.215 / 0.62 | -0.967 / -1.198 / -1.310 | -0.520 / -0.628 |
| half-take + trail 10 | 2160 | -0.173 / 0.33 | +0.055 / 0.43 | -0.047 / 0.39 | +0.207 / 0.61 | -0.966 / -1.222 / -1.328 | -0.533 / -0.669 |
| half-take + trail 20 | 2160 | -0.188 / 0.32 | +0.049 / 0.43 | -0.044 / 0.39 | +0.179 / 0.58 | -0.960 / -1.195 / -1.292 | -0.547 / -0.665 |
| lock +0 | 2160 | -0.173 / 0.32 | -0.019 / 0.40 | -0.105 / 0.36 | +0.084 / 0.52 | -0.856 / -1.118 / -1.210 | -0.506 / -0.665 |
| lock +5 | 2160 | -0.178 / 0.32 | -0.006 / 0.42 | -0.087 / 0.38 | +0.130 / 0.53 | -0.876 / -1.129 / -1.216 | -0.524 / -0.664 |
| lock +10 | 2160 | -0.168 / 0.35 | +0.014 / 0.42 | -0.067 / 0.39 | +0.172 / 0.54 | -0.883 / -1.137 / -1.223 | -0.529 / -0.661 |

**arm level**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| +10 pts | 2970 | -0.431 / 0.16 | -0.334 / 0.25 | -0.529 / 0.20 | -0.260 / 0.41 | -1.232 / -1.628 / -1.828 | -3.263 / -3.449 |
| +15 pts | 2970 | -0.360 / 0.19 | -0.150 / 0.32 | -0.287 / 0.29 | -0.025 / 0.52 | -1.146 / -1.418 / -1.558 | -1.992 / -2.113 |
| +20 pts | 2970 | -0.302 / 0.21 | -0.002 / 0.40 | -0.130 / 0.34 | +0.086 / 0.57 | -1.071 / -1.241 / -1.373 | -0.976 / -1.111 |
| +30 pts | 2970 | -0.086 / 0.36 | +0.110 / 0.45 | +0.088 / 0.44 | +0.300 / 0.63 | -0.815 / -1.060 / -1.087 | +0.512 / +0.356 |
| +40 pts | 2970 | +0.058 / 0.53 | +0.232 / 0.56 | +0.194 / 0.52 | +0.569 / 0.75 | -0.632 / -0.876 / -0.920 | +1.273 / +1.130 |
| 30% of target | 2970 | -0.328 / 0.19 | -0.099 / 0.33 | -0.220 / 0.29 | -0.072 / 0.48 | -1.112 / -1.362 / -1.486 | -1.597 / -1.698 |
| 50% of target | 2970 | -0.101 / 0.35 | +0.107 / 0.44 | +0.077 / 0.42 | +0.245 / 0.58 | -0.845 / -1.089 / -1.124 | +0.390 / +0.305 |
| 70% of target | 2970 | +0.096 / 0.61 | +0.312 / 0.63 | +0.257 / 0.57 | +0.527 / 0.69 | -0.597 / -0.804 / -0.864 | +1.390 / +1.249 |
| 900% of target | 0 | +nan / nan | +nan / nan | +nan / nan | +nan / nan | +nan / +nan / +nan | +nan / +nan |

**thick duration (5 s = 0 s on the 10-s store)**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| 0 s | 7920 | -0.295 / 0.24 | -0.049 / 0.39 | -0.164 / 0.33 | -0.130 / 0.42 | -1.121 / -1.372 / -1.497 | -0.741 / -0.895 |
| 10 s | 7920 | -0.201 / 0.32 | -0.020 / 0.40 | -0.105 / 0.36 | +0.236 / 0.60 | -0.944 / -1.213 / -1.302 | -0.547 / -0.689 |
| 30 s | 7920 | -0.049 / 0.41 | +0.135 / 0.49 | +0.064 / 0.46 | +0.407 / 0.71 | -0.730 / -0.969 / -1.041 | -0.311 / -0.415 |

**normal (hour = box rel_*8, sess = session median, t60 = trailing 60 min, z = z-score vs ET-30-min bucket)**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| hour-norm | 6336 | -0.140 / 0.37 | +0.071 / 0.42 | -0.021 / 0.38 | +0.279 / 0.64 | -0.834 / -1.044 / -1.136 | -0.445 / -0.548 |
| sess-norm | 6336 | -0.139 / 0.32 | +0.082 / 0.45 | +0.009 / 0.41 | +0.196 / 0.56 | -0.834 / -1.036 / -1.109 | -0.451 / -0.531 |
| t60-norm | 6336 | -0.097 / 0.42 | +0.002 / 0.42 | -0.067 / 0.40 | +0.083 / 0.54 | -0.840 / -1.197 / -1.282 | -0.438 / -0.661 |
| z-norm | 4752 | -0.408 / 0.14 | -0.096 / 0.40 | -0.238 / 0.33 | +0.112 / 0.58 | -1.312 / -1.554 / -1.698 | -0.885 / -1.012 |

**measure (tot = rel_tot8, ahead = rel_ahead8)**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| tot | 11880 | -0.146 / 0.35 | +0.059 / 0.45 | -0.032 / 0.41 | +0.168 / 0.58 | -0.863 / -1.098 / -1.193 | -0.470 / -0.596 |
| ahead | 11880 | -0.217 / 0.30 | -0.015 / 0.40 | -0.105 / 0.36 | +0.174 / 0.58 | -1.000 / -1.272 / -1.367 | -0.596 / -0.738 |

**threshold (ratio >= x, or z >= x for the z-norm)**
| level | cells | PRE mean / share>0 | HOLD | L6M | 2026 | N basis PRE / HOLD / L6M | vs random PRE / L6M |
|---|---|---|---|---|---|---|---|
| 1.2 | 4752 | -0.366 / 0.18 | -0.122 / 0.39 | -0.252 / 0.34 | +0.064 / 0.54 | -1.319 / -1.641 / -1.780 | -0.880 / -1.079 |
| 1.5 | 6336 | -0.259 / 0.26 | -0.020 / 0.43 | -0.123 / 0.38 | +0.086 / 0.54 | -1.078 / -1.334 / -1.437 | -0.665 / -0.793 |
| 2.0 | 6336 | -0.107 / 0.40 | +0.065 / 0.43 | -0.016 / 0.39 | +0.205 / 0.61 | -0.783 / -1.028 / -1.109 | -0.400 / -0.530 |
| 3.0 | 4752 | +0.089 / 0.51 | +0.213 / 0.45 | +0.186 / 0.46 | +0.383 / 0.63 | -0.398 / -0.586 / -0.624 | -0.050 / -0.125 |
| 1.0 | 1584 | -0.432 / 0.15 | -0.121 / 0.39 | -0.275 / 0.31 | +0.066 / 0.57 | -1.375 / -1.640 / -1.799 | -0.941 / -1.096 |

## 7. Drift by calendar quarter (pooled scope; pts/trade vs hold, M basis / N basis; MDE 2.8 SE; [fired])

`P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70never` (pooled PRE-selected)
| quarter | M | MDE | N basis | fired/trades |
|---|---|---|---|---|
| 2023Q2 | +0.21 | 1.10 | +0.18 | 106/2439 |
| 2023Q3 | +0.06 | 0.53 | +0.05 | 68/2937 |
| 2023Q4 | +0.02 | 0.75 | -0.00 | 68/2531 |
| 2024Q1 | +0.15 | 0.84 | +0.12 | 83/2852 |
| 2024Q2 | +0.30 | 0.59 | +0.28 | 82/3000 |
| 2024Q3 | +0.23 | 0.58 | +0.20 | 155/5005 |
| 2024Q4 | -0.08 | 0.59 | -0.09 | 79/3705 |
| 2025Q1 | +0.03 | 0.55 | -0.04 | 164/5182 |
| 2025Q2 | +0.24 | 0.50 | +0.17 | 192/5929 |
| 2025Q3 | -0.21 | 0.54 | -0.28 | 85/3379 |
| 2025Q4 | +0.20 | 0.55 | +0.12 | 179/5197 |
| 2026Q1 | -0.45 | 0.88 | -0.56 | 80/2229 |

`P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always` (pooled rank-1 by L6M [looked data])
| quarter | M | MDE | N basis | fired/trades |
|---|---|---|---|---|
| 2023Q2 | +1.22 | 2.63 | +0.61 | 1327/2439 |
| 2023Q3 | +0.98 | 2.39 | +0.33 | 1683/2937 |
| 2023Q4 | -0.21 | 2.31 | -0.88 | 1452/2531 |
| 2024Q1 | -0.66 | 2.24 | -1.39 | 1649/2852 |
| 2024Q2 | +0.42 | 2.18 | -0.27 | 1650/3000 |
| 2024Q3 | -0.30 | 1.64 | -1.04 | 2817/5005 |
| 2024Q4 | -0.91 | 1.91 | -1.67 | 2202/3705 |
| 2025Q1 | +0.60 | 1.45 | -1.48 | 2922/5182 |
| 2025Q2 | +1.56 | 1.38 | -0.37 | 3160/5929 |
| 2025Q3 | +0.84 | 1.73 | -1.16 | 1919/3379 |
| 2025Q4 | +1.06 | 1.51 | -1.01 | 2964/5197 |
| 2026Q1 | +1.43 | 2.64 | -0.76 | 1315/2229 |

`REF|p70_take_always` (REF plain take at 70%)
| quarter | M | MDE | N basis | fired/trades |
|---|---|---|---|---|
| 2023Q2 | +0.97 | 2.53 | +0.36 | 1302/2439 |
| 2023Q3 | +1.01 | 2.31 | +0.36 | 1664/2937 |
| 2023Q4 | -0.30 | 2.25 | -0.97 | 1433/2531 |
| 2024Q1 | -0.59 | 2.21 | -1.32 | 1632/2852 |
| 2024Q2 | +0.35 | 2.12 | -0.33 | 1620/3000 |
| 2024Q3 | -0.28 | 1.61 | -1.01 | 2784/5005 |
| 2024Q4 | -0.73 | 1.84 | -1.49 | 2174/3705 |
| 2025Q1 | +0.72 | 1.40 | -1.35 | 2893/5182 |
| 2025Q2 | +1.53 | 1.27 | -0.39 | 3106/5929 |
| 2025Q3 | +0.96 | 1.62 | -1.04 | 1883/3379 |
| 2025Q4 | +0.81 | 1.42 | -1.26 | 2917/5197 |
| 2026Q1 | +1.24 | 2.58 | -0.95 | 1302/2229 |

## 8. Stack-level lines through the exact lock engine
(stack lines not yet run)

## 9. Policy text (THP_POLICY format) - `l2vast/ds3/out/l2set/profit_policy_candidate.txt`
```
# THP_POLICY_PROFIT_L2SET v1 | fit=2026-10-30T00:44Z | valid=asof+1 label day | window=PRE 2024-02..2025-06 / HOLD 2025-07..2026-02-06 / X' 2023-04..2024-01 (store capped 2026-02-06) | selection=L6M rank on LOOKED data + PRE-selected beside it | wf_profit_pooled(L6M)=-0.29
# Features used: pct, curDepthRel (8-tick depth_rel = rel_tot8, same-ET-hour median of prior 20 label days). Active lines = CANDIDATE-RECENT settings (2026>0 AND last-6-months>0 on the M basis, gates NOT passed: see tier and failed gates in the comment). Lines starting '#!' are DEAD best-available settings (user decides; uncomment to run).
# Approximations: arm '+X pts' -> current pct >= X/target (D6 has no latched-MFE arm in this syntax); thick duration dropped when > 0; half-take / lock / trail-half and non-hour normalisations are not expressible (see DS3_THL2_NEEDS.md).
# === profit (L2SET thick-book rules; first match per side wins; p70 rule first) ===
# S6 (ST) CANDIDATE-RECENT: P|hour_tot_ge3.0|armpts15|d0|trail10|p70always | 2026 +1.76 (MDE 5.2) L6M +2.48 (MDE 2.40) HOLD +2.45 (MDE 2.27) PRE +0.22 | N basis L6M +0.39 HOLD +0.41 PRE -1.07 | vs random exit L6M -0.86 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: arm +15 pts expressed as pct >= 0.250 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for ST: P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never (PRE +0.62, fires 138)
profit S6 * pct >= 0.7 take
profit S6 * pct >= 0.250 curDepthRel >= 3 tighten 10
# H6 (HM) CANDIDATE-RECENT: P|hour_tot_ge2.0|armpts10|d30|trail15|p70never | 2026 +1.17 (MDE 2.6) L6M +0.46 (MDE 1.07) HOLD +0.72 (MDE 1.11) PRE +0.05 | N basis L6M +0.37 HOLD +0.61 PRE -0.02 | vs random exit L6M +0.18 | failed: G1_PRE_CI,G5_Nbasis,G6_vs_random,G7_RC05 | SELECTED ON LOOKED DATA
#   approximations: thick duration 4 samples dropped; arm +10 pts expressed as pct >= 0.167 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for HM: P|t60_ahead_ge1.5|armpts40|d30|lock10|p70never (PRE +0.58, fires 121)
profit H6 * pct >= 0.167 curDepthRel >= 2 tighten 15
# W6 (WT) CANDIDATE-RECENT: P|hour_tot_ge1.2|armpts20|d0|trail20|p70always | 2026 +1.51 (MDE 2.5) L6M +2.05 (MDE 1.32) HOLD +2.30 (MDE 1.31) PRE +0.30 | N basis L6M -0.19 HOLD +0.08 PRE -1.06 | vs random exit L6M +2.09 | failed: G1_PRE_CI,G3_Xp,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: arm +20 pts expressed as pct >= 0.593 of the book target 33.75 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for WT: P|t60_ahead_ge1.2|armpts30|d0|take|p70never (PRE +0.60, fires 1299)
profit W6 * pct >= 0.7 take
profit W6 * pct >= 0.593 curDepthRel >= 1.2 tighten 20
# K6 (KB) CANDIDATE-RECENT: P|hour_tot_ge1.2|armpct0.7|d0|trail30|p70always | 2026 +2.53 (MDE 4.6) L6M +1.18 (MDE 2.20) HOLD +1.46 (MDE 2.11) PRE +0.10 | N basis L6M -0.85 HOLD -0.53 PRE -1.22 | vs random exit L6M +2.64 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   PRE-selected (out-of-sample) cell for KB: P|z_ahead_ge1.5|armpct0.7|d30|lock10|p70never (PRE +0.14, fires 218)
profit K6 * pct >= 0.7 take
profit K6 * pct >= 0.700 curDepthRel >= 1.2 tighten 30
# U6 (SM) CANDIDATE-RECENT: P|hour_tot_ge1.5|armpts10|d30|take|p70always | 2026 +8.97 (MDE 13.7) L6M +3.07 (MDE 5.53) HOLD +2.11 (MDE 5.38) PRE -0.32 | N basis L6M +0.96 HOLD -0.05 PRE -1.56 | vs random exit L6M -3.23 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05 | SELECTED ON LOOKED DATA
#   approximations: thick duration 4 samples dropped; arm +10 pts expressed as pct >= 0.167 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for SM: P|t60_ahead_ge3.0|armpts30|d0|trail10|p70never (PRE +1.16, fires 105)
profit U6 * pct >= 0.7 take
profit U6 * pct >= 0.167 curDepthRel >= 1.5 take
# P6 (PE) CANDIDATE-RECENT: P|hour_tot_ge1.5|armpts30|d30|take|p70always | 2026 +3.10 (MDE 5.4) L6M +0.94 (MDE 2.26) HOLD +0.65 (MDE 2.18) PRE +1.01 | N basis L6M -1.05 HOLD -1.33 PRE -0.27 | vs random exit L6M +1.29 | failed: G1_PRE_CI,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: thick duration 4 samples dropped; arm +30 pts expressed as pct >= 0.500 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for PE: P|hour_ahead_ge2.0|armpts10|d30|take|p70always (PRE +1.48, fires 1745)
profit P6 * pct >= 0.7 take
profit P6 * pct >= 0.500 curDepthRel >= 1.5 take
# A6 (PB) CANDIDATE-RECENT: P|hour_tot_ge1.2|armpct0.5|d0|trail30|p70always | 2026 +2.07 (MDE 7.1) L6M +0.84 (MDE 3.29) HOLD +1.09 (MDE 3.13) PRE +0.85 | N basis L6M -1.38 HOLD -1.06 PRE -0.42 | vs random exit L6M +1.66 | failed: G1_PRE_CI,G3_Xp,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   PRE-selected (out-of-sample) cell for PB: P|hour_tot_ge2.0|armpct0.3|d0|lock10|p70never (PRE +1.22, fires 312)
profit A6 * pct >= 0.7 take
profit A6 * pct >= 0.500 curDepthRel >= 1.2 tighten 30
# N6 (DN) CANDIDATE-RECENT: P|hour_tot_ge1.2|armpts40|d0|trail20|p70always | 2026 +1.05 (MDE 7.3) L6M +1.01 (MDE 3.31) HOLD +1.21 (MDE 3.12) PRE -0.25 | N basis L6M -1.15 HOLD -0.91 PRE -1.58 | vs random exit L6M +2.88 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: arm +40 pts expressed as pct >= 0.667 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for DN: P|sess_tot_ge2.0|armpct0.7|d10|trail20|p70thickonly (PRE +0.71, fires 179)
profit N6 * pct >= 0.7 take
profit N6 * pct >= 0.667 curDepthRel >= 1.2 tighten 20
# M6 (MV) CANDIDATE-RECENT: P|hour_tot_ge1.2|armpts40|d0|trail30|p70always | 2026 +0.84 (MDE 4.6) L6M +1.13 (MDE 2.44) HOLD +0.80 (MDE 2.27) PRE +0.45 | N basis L6M -0.91 HOLD -1.21 PRE -0.87 | vs random exit L6M +3.11 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: arm +40 pts expressed as pct >= 0.667 of the book target 60.00 (current pct, not latched MFE)
#   PRE-selected (out-of-sample) cell for MV: P|hour_ahead_ge2.0|armpts20|d30|lock10|p70never (PRE +0.62, fires 137)
profit M6 * pct >= 0.7 take
profit M6 * pct >= 0.667 curDepthRel >= 1.2 tighten 30
# MA6 (MA) DEAD: P|hour_tot_ge1.5|armpct0.3|d30|trail5|p70thickonly | 2026 -2.52 (MDE 6.0) L6M +0.38 (MDE 3.42) HOLD +0.04 (MDE 3.31) PRE -0.45 | N basis L6M -0.60 HOLD -0.99 PRE -0.97 | vs random exit L6M -0.26 | failed: G1_PRE_CI,G4_2xcost,G5_Nbasis,G6_vs_random,G7_RC05,G8_placebo95 | SELECTED ON LOOKED DATA
#   approximations: thick duration 4 samples dropped
#   PRE-selected (out-of-sample) cell for MA: P|sess_ahead_ge2.0|armpts10|d30|lock10|p70never (PRE +0.38, fires 109)
#! profit MA6 * pct >= 0.7 curDepthRel >= 1.5 take
#! profit MA6 * pct >= 0.300 curDepthRel >= 1.5 tighten 5
```

## 10. Reproduction and caveats
* Code `l2vast/ds3/code/l2set_profit/` (lp_feat, lp_cells, lp_kern, lp_sweep, lp_select, lp_look, lp_report, lp_stack, lp_wf, lp_rc, lp_policy); outputs `l2vast/ds3/out/l2set_profit/` (D_real.npy cells x trades, W_real.npy, selection_PRE.json, look_arrays.npz, agg_plc_*.npz). One-command nightly re-fit: `bash l2vast/ds3/code/l2set_profit/lp_nightly.sh [asof]`.
* 10-s store: 5 s thick duration is not separable (alias of 0 s); trail/lock exits are taken at the CLOSE of the breach row (conservative vs a live stop order). Only 10 static-bracket books; CR excluded; 6 of them are in the lock engine.
* Normals: box rel_*8 = same ET hour, prior 20 days (the minute-of-day median of the directive is approximated by the hour; z-scores use ET 30-minute buckets, prior 20 days, scale = median within-bucket MAD).
* The 2026 window is about 5 real weeks (25 trading days): its sign is nearly uninformative; CANDIDATE-RECENT is a label, not a gate.
