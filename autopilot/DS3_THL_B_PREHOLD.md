# DS3_THL_B_PREHOLD - loss-side rule grids, IN-SAMPLE (PRE 2024-02..2025-06) only, written before any HOLD or X number is opened

Prereg l2vast/ds3/prereg/THLB_prereg.md sha256 9ebc50f0f9bf67dfc36e880e53c0c7629a5f7a8a4b32f78ec1c690ba8756787b (DECISIONS.md). Rules 158 (rules_table.json sha256 e60d4abb...), MEASURED basis M (stop walk by year, market +1 tick, target level + P9 correction), paired per trade vs hold-to-stop on identical entries, deltas in NQ points per trade (fees cancel). These are RAW IN-SAMPLE numbers (no selection yet): every one of the 158 rules is scored on every stream. HOLD (2025-07..2026-02-06) and X (2023-04..2024-01) have not been read in this file; one logged look per group L1..L8 follows after this text is hashed.

SHORT-STOP streams (CR, D6_SM_t60_sst_ASIA) are scored but excluded from pooled sets; ES and RTY basket legs have NO 1-s path in the box (not scored). Streams scored: 22 (B3_NQ, CR, D6_HM_t75_s90_NYAM, D6_KB_t60_s75_ASIA, D6_PB7_PB5_ASIA, D6_SM_t60_sst_ASIA, D6_TB4B_ASIA, D6_TB4W_03_ASIA, DN, EM, HM, KB, MA, MV, O6_LV_RN_BH, O6_OR15m_stp_le1, O6_OR30m_stp_ge0.5, PB, PE, SM, ST, WT). Multiplicity: 158 rules x 22 streams = 3476 cells; 20 placebo draws per cell.

## 1. Per stream: sample, level, and the best-of-158 reality check (White RC, PRE, day-block bootstrap 2000 draws)

| stream | n_PRE | base_net_pts | base_win | one_rule_MDE | best_rule_PRE | best_t | RC_p |
|---|---|---|---|---|---|---|---|
| B3_NQ | 78 | +25.48 | 0.60 | 77.13 | L5e_x10_w120_t0.7 | 2.18 | 0.137 |
| CR | 1337 | -1.04 | 0.31 | 1.58 | L4_x30_n300 | 2.79 | 0.082 |
| D6_HM_t75_s90_NYAM | 427 | +10.77 | 0.62 | 9.41 | L5e_x10_w120_t0.5 | 0.00 | 1.000 |
| D6_KB_t60_s75_ASIA | 704 | +5.42 | 0.61 | 6.53 | L5e_x20_w300_t0.5 | -0.93 | 1.000 |
| D6_PB7_PB5_ASIA | 342 | +10.71 | 0.61 | 8.37 | L5e_x10_w300_t0.5 | 1.00 | 0.713 |
| D6_SM_t60_sst_ASIA | 264 | +6.32 | 0.41 | 5.87 | L5e_x20_w120_t0.5 | 1.72 | 0.387 |
| D6_TB4B_ASIA | 450 | +7.32 | 0.58 | 7.41 | L5e_x10_w300_t0.7 | 0.00 | 1.000 |
| D6_TB4W_03_ASIA | 800 | +4.37 | 0.56 | 5.09 | L6_a30_r3_w30 | 0.42 | 0.927 |
| DN | 1762 | +2.97 | 0.54 | 3.47 | L5e_x10_w120_t0.7 | 0.62 | 0.865 |
| EM | 871 | +2.03 | 0.54 | 5.01 | L3_m30_y50_n300 | 0.71 | 0.875 |
| HM | 1561 | +0.35 | 0.52 | 3.71 | L6_a30_r3_w10 | 1.81 | 0.266 |
| KB | 1854 | +3.66 | 0.55 | 3.39 | L2_x5_t60 | 0.64 | 0.879 |
| MA | 997 | +1.96 | 0.53 | 4.77 | L5e_x10_w300_t0.5 | 1.00 | 0.764 |
| MV | 2025 | +1.96 | 0.53 | 3.36 | L1_x40 | -0.74 | 1.000 |
| O6_LV_RN_BH | 134 | +11.59 | 0.62 | 13.26 | L6_a30_r3_w60 | 1.45 | 0.491 |
| O6_OR15m_stp_le1 | 179 | +14.10 | 0.64 | 10.68 | L5e_x10_w120_t0.5 | 0.00 | 1.000 |
| O6_OR30m_stp_ge0.5 | 297 | +14.85 | 0.64 | 8.31 | L5e_x10_w120_t0.5 | 0.00 | 1.000 |
| PB | 2261 | -1.43 | 0.50 | 3.10 | L3_m30_y50_n60 | 2.16 | 0.194 |
| PE | 1732 | +1.34 | 0.53 | 3.56 | L2_x20_t60 | 1.11 | 0.687 |
| SM | 774 | +3.38 | 0.55 | 5.29 | L5e_x10_w300_t0.7 | 0.00 | 1.000 |
| ST | 1717 | +1.15 | 0.52 | 3.61 | L5e_x20_w120_t0.5 | -0.04 | 0.990 |
| WT | 2567 | -0.47 | 0.59 | 1.84 | L4_x30_n600 | 0.30 | 0.975 |


Pooled over the 11 intraday books ST HM WT KB SM PE EM PB DN MV MA (clusters = label day x session, shared across books): best rule L2_x10_t60, max t -0.12, RC p 0.987, n 18121.

## 2. IN-SAMPLE mean paired delta (pts/trade, mean over the rules of each group) by stream

| fam | B3_NQ | CR | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_SM_t60_sst_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1 | -17.97 | +0.04 | -7.96 | -5.39 | -6.53 | -0.89 | -3.61 | -2.12 | -0.69 | -1.11 | +0.10 | -2.27 | -1.75 | -1.95 | -6.46 | -7.72 | -6.98 | +0.64 | -1.03 | -2.73 | -1.38 | -0.49 | -1.15 |
| L2 | -3.41 | +0.06 | -2.75 | -4.18 | -5.14 | -0.17 | -2.02 | -1.88 | -0.62 | -0.28 | +0.37 | -0.87 | -1.78 | -0.98 | -0.61 | -2.71 | -2.24 | +0.94 | -0.15 | -1.85 | -0.83 | -0.24 | -0.57 |
| L3 | -3.54 | -0.06 | -4.76 | -4.64 | -6.00 | -0.64 | -2.34 | -2.18 | -0.74 | -0.41 | +0.09 | -1.71 | -1.69 | -1.41 | -3.00 | -5.82 | -4.59 | +0.99 | -0.65 | -1.86 | -1.15 | -0.26 | -0.80 |
| L4 | +4.19 | -0.02 | -3.54 | -4.76 | -5.59 | -0.58 | -2.75 | -2.15 | -0.77 | -0.43 | +0.11 | -1.41 | -1.69 | -1.69 | -1.77 | -3.96 | -3.54 | +0.54 | -0.52 | -1.92 | -1.09 | -0.38 | -0.84 |
| L5 | -5.13 | -0.03 | -4.89 | -3.45 | -4.93 | -0.75 | -2.54 | -1.64 | -0.49 | -0.79 | -0.33 | -1.40 | -1.24 | -1.36 | -5.22 | -5.32 | -4.08 | +0.17 | -1.01 | -1.76 | -0.87 | -0.38 | -0.86 |
| L6 | -15.51 | +0.00 | -7.71 | -5.18 | -6.57 | -1.15 | -2.91 | -2.16 | -0.86 | -0.79 | +0.10 | -2.08 | -1.76 | -2.06 | -6.74 | -7.63 | -6.30 | +0.70 | -1.22 | -2.35 | -1.39 | -0.42 | -1.10 |
| L7 | -9.05 | -0.08 | -6.33 | -5.96 | -6.58 | -0.81 | -3.57 | -2.99 | -1.46 | -1.53 | -0.62 | -2.44 | -2.43 | -2.53 | -3.80 | -6.66 | -5.27 | -0.16 | -1.61 | -2.72 | -1.82 | -1.00 | -1.66 |
| L8 | -12.68 | +0.02 | -5.51 | -3.67 | -4.47 | -0.58 | -2.39 | -1.52 | -0.52 | -0.74 | +0.07 | -1.51 | -1.17 | -1.36 | -4.41 | -5.29 | -4.71 | +0.45 | -0.74 | -1.79 | -0.97 | -0.34 | -0.78 |

## 3. The live TH loss rule (15 pts adverse, 3 of 3, 30 s) vs hold-to-stop, IN-SAMPLE, every stream

| stream | pre_n | delta | CI | MDE | exits_added | cut_to_tgt | saved | forfeited | win_base | win_rule | usd_wk | N_basis | C_basis | placebo |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_NQ | 78 | -5.73 | [-54.70,+43.24] | 69.96 | 65 (83%) | 0% | +74.59 | -80.32 | 0.60 | 0.17 | -119 | -5.73 | -6.01 | 0.80 |
| CR | 1337 | +0.13 | [-0.55,+0.81] | 0.97 | 188 (14%) | 18% | +1.63 | -1.50 | 0.31 | 0.28 | 463 | +0.08 | +0.18 | 0.90 |
| D6_HM_t75_s90_NYAM | 427 | -6.10 | [-12.21,+0.02] | 8.74 | 287 (67%) | 39% | +21.23 | -27.32 | 0.62 | 0.31 | -6,941 | -6.67 | -5.77 | 0.65 |
| D6_KB_t60_s75_ASIA | 704 | -4.08 | [-7.87,-0.29] | 5.41 | 467 (66%) | 42% | +18.91 | -22.98 | 0.61 | 0.32 | -7,655 | -4.74 | -3.86 | 0.40 |
| D6_PB7_PB5_ASIA | 342 | -6.37 | [-11.38,-1.35] | 7.16 | 214 (63%) | 41% | +13.66 | -20.03 | 0.61 | 0.35 | -5,808 | -6.97 | -6.27 | 0.55 |
| D6_SM_t60_sst_ASIA | 264 | -1.77 | [-5.18,+1.65] | 4.88 | 96 (36%) | 22% | +4.70 | -6.46 | 0.41 | 0.33 | -1,244 | -1.96 | -1.62 | 0.00 |
| D6_TB4B_ASIA | 450 | -3.39 | [-7.60,+0.81] | 6.01 | 286 (64%) | 36% | +14.80 | -18.20 | 0.58 | 0.35 | -4,071 | -3.90 | -3.19 | 0.05 |
| D6_TB4W_03_ASIA | 800 | -1.65 | [-4.62,+1.31] | 4.23 | 520 (65%) | 34% | +15.82 | -17.47 | 0.56 | 0.33 | -3,526 | -2.20 | -1.43 | 0.35 |
| DN | 1762 | -0.72 | [-2.73,+1.29] | 2.87 | 1126 (64%) | 32% | +15.64 | -16.36 | 0.54 | 0.33 | -3,376 | -1.18 | -0.49 | 0.35 |
| EM | 871 | -0.26 | [-3.14,+2.62] | 4.11 | 575 (66%) | 31% | +16.40 | -16.66 | 0.54 | 0.31 | -608 | -0.67 | -0.06 | 0.45 |
| HM | 1561 | +0.32 | [-1.89,+2.54] | 3.17 | 1067 (68%) | 30% | +17.06 | -16.74 | 0.52 | 0.30 | 1,346 | -0.13 | +0.58 | 0.75 |
| KB | 1854 | -2.08 | [-4.09,-0.07] | 2.88 | 1240 (67%) | 33% | +15.91 | -17.99 | 0.55 | 0.31 | -5,285 | -2.59 | -1.78 | 0.20 |
| MA | 997 | -2.35 | [-5.18,+0.48] | 4.04 | 679 (68%) | 33% | +15.94 | -18.29 | 0.53 | 0.29 | -6,240 | -2.81 | -2.18 | 0.05 |
| MV | 2025 | -2.10 | [-4.07,-0.13] | 2.81 | 1390 (69%) | 33% | +16.30 | -18.40 | 0.53 | 0.29 | -11,320 | -2.60 | -1.87 | 0.20 |
| O6_LV_RN_BH | 134 | -7.69 | [-15.40,+0.02] | 11.01 | 80 (60%) | 42% | +12.82 | -20.52 | 0.62 | 0.35 | -2,749 | -8.15 | -7.09 | 0.40 |
| O6_OR15m_stp_le1 | 179 | -9.17 | [-15.60,-2.73] | 9.19 | 104 (58%) | 42% | +11.08 | -20.24 | 0.64 | 0.37 | -4,375 | -9.66 | -9.01 | 0.05 |
| O6_OR30m_stp_ge0.5 | 297 | -6.94 | [-11.87,-2.01] | 7.04 | 166 (56%) | 42% | +11.68 | -18.62 | 0.64 | 0.40 | -5,495 | -7.34 | -6.85 | 0.20 |
| PB | 2261 | +0.10 | [-1.75,+1.94] | 2.63 | 1556 (69%) | 31% | +17.13 | -17.04 | 0.50 | 0.28 | 575 | -0.40 | +0.37 | 0.15 |
| PE | 1732 | -0.84 | [-2.95,+1.28] | 3.02 | 1186 (68%) | 32% | +16.73 | -17.57 | 0.53 | 0.30 | -2,163 | -1.32 | -0.54 | 0.50 |
| SM | 774 | -2.40 | [-5.62,+0.81] | 4.60 | 520 (67%) | 35% | +16.10 | -18.51 | 0.55 | 0.30 | -3,838 | -2.88 | -2.18 | 0.20 |
| ST | 1717 | -0.98 | [-3.07,+1.10] | 2.98 | 1176 (68%) | 31% | +16.55 | -17.53 | 0.52 | 0.30 | -4,501 | -1.47 | -0.79 | 0.25 |
| WT | 2567 | -0.77 | [-1.78,+0.24] | 1.44 | 1423 (55%) | 34% | +8.77 | -9.54 | 0.59 | 0.40 | -3,690 | -1.16 | -0.58 | 0.00 |

## 4. Top 10 cells by IN-SAMPLE delta (n_PRE >= 100), regardless of verdict (HOLD-side kills are added after the look)

| stream | rule | desc | pre_n | delta | CI | MDE | exits | cut_to_tgt | saved | forfeited | usd_wk | N_basis | C_basis | placebo | nb | rc_p_stream |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O6_LV_RN_BH | L6_a30_r3_w60 | live TH loss grid: adverse 30, 3 of 3, window 60s | 134 | +2.78 | [-0.98,+6.54] | 5.37 | 43 (32%) | 9% | +6.54 | -3.75 | 994 | +2.71 | +3.14 | 0.95 | False | 0.4915 |
| O6_LV_RN_BH | L4_x30_n60 | stall under water: below -30, no new MAE and recovery <= 2 pts for 60s | 134 | +2.29 | [-1.11,+5.69] | 4.86 | 38 (28%) | 8% | +5.43 | -3.14 | 819 | +2.25 | +2.12 | 0.95 | False | 0.4915 |
| O6_LV_RN_BH | L6_a30_r3_w30 | live TH loss grid: adverse 30, 3 of 3, window 30s | 134 | +2.26 | [-2.09,+6.61] | 6.22 | 48 (36%) | 15% | +7.43 | -5.17 | 807 | +2.11 | +2.76 | 1.00 | False | 0.4915 |
| PB | L3_m20_y50_n60 | MAE>=20: cut if recovery < 50% of MAE 60s after the MAE | 2261 | +2.07 | [+0.24,+3.90] | 2.61 | 1529 (68%) | 30% | +18.12 | -16.05 | 12,472 | +1.59 | +2.19 | 1.00 | True | 0.194 |
| O6_LV_RN_BH | L6_a30_r3_w120 | live TH loss grid: adverse 30, 3 of 3, window 120s | 134 | +1.99 | [-1.37,+5.35] | 4.80 | 34 (25%) | 9% | +5.07 | -3.08 | 712 | +1.95 | +2.27 | 1.00 | False | 0.4915 |
| O6_LV_RN_BH | L2_x20_t5 | cut after 5 cumulative min below -20 | 134 | +1.94 | [-1.65,+5.54] | 5.14 | 33 (25%) | 12% | +5.44 | -3.50 | 695 | +1.89 | +1.99 | 1.00 | False | 0.4915 |
| PB | L3_m30_y50_n60 | MAE>=30: cut if recovery < 50% of MAE 60s after the MAE | 2261 | +1.75 | [+0.18,+3.31] | 2.24 | 1307 (58%) | 23% | +13.64 | -11.89 | 10,530 | +1.42 | +1.87 | 0.95 | True | 0.194 |
| PB | L3_m20_y25_n60 | MAE>=20: cut if recovery < 25% of MAE 60s after the MAE | 2261 | +1.56 | [-0.20,+3.33] | 2.52 | 1486 (66%) | 28% | +16.81 | -15.24 | 9,429 | +1.14 | +1.73 | 0.70 | True | 0.194 |
| PB | L6_a25_r3_w30 | live TH loss grid: adverse 25, 3 of 3, window 30s | 2261 | +1.45 | [-0.07,+2.96] | 2.17 | 1300 (57%) | 22% | +12.75 | -11.30 | 8,726 | +1.15 | +1.65 | 0.70 | True | 0.194 |
| HM | L6_a30_r3_w10 | live TH loss grid: adverse 30, 3 of 3, window 10s | 1561 | +1.37 | [-0.05,+2.79] | 2.03 | 692 (44%) | 15% | +8.24 | -6.87 | 5,690 | +1.22 | +1.45 | 1.00 | True | 0.266 |

## 5. Top 10 rules pooled over the 11 intraday books (IN-SAMPLE, trade-weighted)

| rule | desc | n | delta | CI | MDE |
|---|---|---|---|---|---|
| L5e_x10_w300_t0.7 | efficiency against: below -10 and directional ER(300s)>=0.7 against | 18121 | -0.03 | [-0.09,+0.03] | 0.09 |
| L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 18121 | -0.03 | [-0.09,+0.03] | 0.09 |
| L2_x10_t60 | cut after 60 cumulative min below -10 | 18121 | -0.04 | [-0.62,+0.55] | 0.83 |
| L5e_x10_w300_t0.5 | efficiency against: below -10 and directional ER(300s)>=0.5 against | 18121 | -0.04 | [-0.12,+0.04] | 0.12 |
| L5e_x20_w300_t0.5 | efficiency against: below -20 and directional ER(300s)>=0.5 against | 18121 | -0.05 | [-0.12,+0.03] | 0.11 |
| L2_x5_t60 | cut after 60 cumulative min below -5 | 18121 | -0.10 | [-0.77,+0.56] | 0.95 |
| L2_x20_t60 | cut after 60 cumulative min below -20 | 18121 | -0.12 | [-0.53,+0.30] | 0.59 |
| L5e_x20_w120_t0.7 | efficiency against: below -20 and directional ER(120s)>=0.7 against | 18121 | -0.12 | [-0.28,+0.03] | 0.22 |
| L8_p40 | half cut at -40, rest to bracket | 18121 | -0.14 | [-0.46,+0.19] | 0.47 |
| L5e_x10_w120_t0.7 | efficiency against: below -10 and directional ER(120s)>=0.7 against | 18121 | -0.14 | [-0.35,+0.07] | 0.30 |


Cells with PRE delta > 0: 445 of 3476; cells with CI lower bound > 0: 5 (chance expectation at 2.5% one-sided: 87).


Frozen: gates, rules and the hold-to-stop baseline are unchanged from the prereg. Next: log one holdout look per group L1..L8 (tracks THLB_L1..THLB_L8, this file as the pre-holdout text), then open HOLD and X.
