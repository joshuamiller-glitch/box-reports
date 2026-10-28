# DS3_CZT_FINAL - T-CZT (Condition-Zone-Trigger stack), NQ, D3CZ 2026-10-28

**Verdict: 0 PASS / 0 CANDIDATE / 41 DEAD (G1 27 cells, G2 14 cells). No spec.** The premise holds only as a range effect (negative-gamma days are ~15-45% wider), not as a follow-through or reversal effect; the best pre-holdout cells (type c mixed, 10-min micro-range, mean +6..+7 pts/trade on 170-240 trades) are not distinguishable from random zones, shuffled-gamma, timing-destroyed or random-direction placebos (rank < 0.95, CI includes zero), and flip to -5..-11 pts in HOLD. The trailing management ('won battle' pivot trail) is what makes mean net positive in the pre window (fixed-target controls 2R / next level are negative or zero, G2), and it does so for random entries too (zone-touch entries average +1..+2 pts).

Prereg sha256 ac82c2c74ebba6b6624392e1ec3178043214808030a39eb18bd3e61265dfd772 (autopilot/DECISIONS.md, before any P&L). G1 pre text sha256 daadddb3982ecab40346aa18c1ad5c8203e4fb623888420c9d8e7d8a7d8b902f, G2 f586bc0d44d16e01b0c36e0ee34458e4f772c7f8412dd72dac498fe772f4d148; looks logged (DS3_CZT_G1/G2 + _SPAN2) before HOLD (2025-07..2026-10-16) and X (2023-04..2024-01) were read. UNTOUCHED never read. Code l2vast/ds3/code/czt/ (cz_prep, cz_lev, cz_core numba, cz_run, cz_score, cz_eval, cz_gates, cz_plb/plb2, cz_g1fin, cz_supp, cz_assemble); out/czt/. Basis T only (tape-direct style: ask/bid at arrival vs first print, stop slip 1 tick, target through-print, commission 4.84/lot RT), 1 contract; conservative/direct basis only.

## 1. Premise test: the gamma regime's own base rates (descriptive; NEG = net dealer gamma gex_usd < 0 of the last published options-OI date before the day, feat_NQA)
PRE (2023-02..2025-06; 205 NEG / 385 POS days) and HOLD (2025-07..2026-10-16; 101 NEG / 223 POS):
| | days | RTH range pts | range / prior-20d mean | P(break prior-day H or L) | breakout follow-through (close >= 10 pts beyond) | reversal (close back inside) | open outside value |
|---|---|---|---|---|---|---|---|
| PRE NEG | 205 | 312 | 1.136 | 0.495 | 0.562 | 0.409 | 0.639 |
| PRE POS | 385 | 227 | 0.962 | 0.475 | 0.552 | 0.415 | 0.603 |
| HOLD NEG | 101 | 449 | 1.147 | 0.485 | 0.622 | 0.357 | 0.683 |
| HOLD POS | 223 | 310 | 0.992 | 0.491 | 0.621 | 0.342 | 0.686 |
NEG vs POS range (normalised): Welch t = 3.9 (PRE), 2.4 (HOLD). zgd quartile (distance to the flip) shows the same: lowest quartile (below the flip) range/mean 1.19 PRE, 1.16 HOLD vs 0.92-1.10 for the others. So 'negative gamma = expansion' is supported for range/volatility; 'positive gamma = fade' is NOT supported (reversal frequency and follow-through are equal in the two regimes). Type (a) (continuation) therefore only has a range premise to lean on, type (b) has none.

## 2. Cells and results (pts = net NQ points per 1-contract trade after commission/slippage; MDE = 2.8 sd/sqrt(n))
Triggers per day are small once the layers stack: type a 34, b 83, c 523 triggers in WFPRE at W=300 H=15 X=60 (trades/wk over the grid: a 0.1-1.0, b 0.1-4.1, c 2.3-11.4).
### G1 (27 cells: type x micro-range W {120,300,600} s x acceptance hold H {5,15,30} s; X=60; stop micro+0; trail 2-min slices; tighten T=30)
| cell | tier | pre n | /wk | pre mean pts | MDE | HOLD n | HOLD mean | X n | X mean | WF mean | WR | avg R | long / short mean (WF) | cost2x pre | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1_c_W600_H30 | DEAD | 172 | 2.29 | 7.04 | 12.26 | 74 | -10.78 | 179 | -1.65 | 1.68 | 0.41 | 0.16 | -4.51 / 11.86 | 6.30 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_c_W600_H15 | DEAD | 237 | 3.16 | 5.97 | 9.73 | 111 | -7.84 | 255 | -1.14 | 1.56 | 0.41 | 0.14 | -2.55 / 7.40 | 5.23 | beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W300_H15 | DEAD | 29 | 0.39 | 5.42 | 30.63 | 10 | 5.66 | 44 | 1.22 | 5.48 | 0.34 | 0.09 | -0.24 / 22.08 | 4.68 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_c_W600_H5 | DEAD | 353 | 4.71 | 5.31 | 8.28 | 183 | -5.28 | 365 | -0.29 | 1.70 | 0.41 | 0.14 | -1.35 / 5.72 | 4.57 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,best_of_N,hold,span2 |
| G1_a_W120_H30 | DEAD | 20 | 0.27 | 4.86 | 20.04 | 11 | -3.63 | 42 | -1.36 | 1.85 | 0.40 | 0.01 | 5.13 / -9.42 | 4.12 | min_n,beats_a,beats_b,beats_c,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_c_W300_H5 | DEAD | 560 | 7.47 | 4.44 | 6.34 | 303 | -2.94 | 502 | 2.22 | 1.85 | 0.39 | 0.15 | 0.89 / 3.00 | 3.70 | beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold |
| G1_c_W300_H30 | DEAD | 262 | 3.49 | 3.18 | 9.54 | 119 | -6.80 | 277 | 0.77 | 0.06 | 0.36 | 0.11 | -2.85 / 4.60 | 2.44 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold |
| G1_a_W300_H30 | DEAD | 16 | 0.21 | 3.15 | 27.03 | 4 | 17.76 | 34 | 1.81 | 6.07 | 0.38 | 0.06 | 9.23 / -11.83 | 2.41 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,stack_add_pre,best_of_N,hold,span2 |
| G1_c_W300_H15 | DEAD | 391 | 5.21 | 3.04 | 7.30 | 189 | -2.98 | 392 | 0.39 | 1.08 | 0.38 | 0.13 | -0.50 / 3.23 | 2.30 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold |
| G1_a_W600_H5 | DEAD | 37 | 0.49 | 3.02 | 26.88 | 13 | 11.82 | 44 | 10.22 | 5.31 | 0.43 | 0.02 | -8.70 / 35.07 | 2.28 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N |
| G1_c_W120_H30 | DEAD | 462 | 6.16 | 2.22 | 5.97 | 223 | -4.46 | 480 | -2.19 | 0.05 | 0.33 | 0.11 | -0.61 / 1.03 | 1.48 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W600_H15 | DEAD | 17 | 0.23 | 1.98 | 26.92 | 7 | 31.69 | 32 | -3.75 | 10.64 | 0.35 | -0.00 | 3.05 / 17.07 | 1.24 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W120_H5 | DEAD | 310 | 4.13 | 1.50 | 6.26 | 166 | -6.54 | 291 | 1.06 | -1.30 | 0.32 | 0.04 | -0.83 / -1.66 | 0.76 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold |
| G1_c_W120_H5 | DEAD | 853 | 11.37 | 1.41 | 4.25 | 496 | -1.84 | 762 | -0.53 | 0.22 | 0.31 | 0.10 | -1.01 / 1.67 | 0.67 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W300_H5 | DEAD | 55 | 0.73 | 0.96 | 20.72 | 27 | 1.98 | 60 | 3.60 | 1.29 | 0.36 | 0.01 | -7.31 / 17.03 | 0.22 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold |
| G1_b_W600_H30 | DEAD | 8 | 0.11 | 0.60 | 46.63 | 2 | 33.51 | 25 | -0.38 | 7.18 | 0.25 | -0.09 | -14.33 / 16.40 | -0.14 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W300_H30 | DEAD | 48 | 0.64 | 0.42 | 16.97 | 25 | -6.07 | 62 | 4.22 | -1.80 | 0.35 | -0.08 | 2.94 / -4.75 | -0.32 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold |
| G1_c_W120_H15 | DEAD | 648 | 8.64 | 0.21 | 4.62 | 342 | -1.40 | 624 | -1.58 | -0.35 | 0.32 | 0.05 | -2.40 / 2.46 | -0.53 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W300_H15 | DEAD | 80 | 1.07 | -0.22 | 12.28 | 41 | -1.18 | 99 | 0.08 | -0.55 | 0.35 | -0.07 | 6.99 / -6.23 | -0.97 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W120_H5 | DEAD | 73 | 0.97 | -0.38 | 15.96 | 34 | 0.12 | 75 | -0.30 | -0.22 | 0.27 | -0.12 | -4.96 / 8.39 | -1.12 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W300_H5 | DEAD | 144 | 1.92 | -1.90 | 8.00 | 79 | -8.27 | 154 | 1.17 | -4.16 | 0.36 | -0.12 | 2.22 / -7.87 | -2.64 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W120_H15 | DEAD | 44 | 0.59 | -2.21 | 19.83 | 16 | -0.16 | 58 | -2.01 | -1.66 | 0.27 | -0.21 | -2.23 / -0.34 | -2.95 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W600_H15 | DEAD | 21 | 0.28 | -2.27 | 38.57 | 4 | 33.01 | 32 | 1.36 | 3.38 | 0.29 | -0.07 | -7.44 / 37.63 | -3.01 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W120_H30 | DEAD | 139 | 1.85 | -2.41 | 8.24 | 72 | -5.06 | 158 | 7.50 | -3.32 | 0.32 | -0.14 | -0.23 / -5.32 | -3.16 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W120_H15 | DEAD | 205 | 2.73 | -2.55 | 6.20 | 108 | -5.98 | 222 | 2.65 | -3.74 | 0.33 | -0.18 | -1.33 / -5.46 | -3.30 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_b_W600_H5 | DEAD | 41 | 0.55 | -3.82 | 13.66 | 21 | 3.67 | 57 | -4.17 | -1.28 | 0.37 | -0.14 | -2.63 / -0.43 | -4.56 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G1_a_W600_H30 | DEAD | 11 | 0.15 | -14.47 | 21.91 | 1 | 157.01 | 26 | 11.87 | -0.18 | 0.27 | -0.30 | 3.38 / -17.99 | -15.21 | min_n,mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |

### G2 (14 cells composed by the prereg rule from G1 WFPRE: G1_c_W600_H30 and G1_c_W600_H15; variants stop+5, fixed-60 stop, 5-min trail slices, tighten 15, fixed 2R target, target = next major level, X=150)
| cell | tier | pre n | /wk | pre mean pts | MDE | HOLD n | HOLD mean | X n | X mean | WF mean | WR | avg R | long / short mean (WF) | cost2x pre | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G2_c_W600_H15_X150 | DEAD | 35 | 0.47 | 13.20 | 36.77 | 8 | 13.26 | 56 | 0.04 | 13.21 | 0.37 | 0.29 | -5.62 / 36.99 | 12.46 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N |
| G2_c_W600_H30_X150 | DEAD | 22 | 0.29 | 13.17 | 53.39 | 3 | -21.24 | 39 | -0.97 | 9.04 | 0.18 | 0.20 | -14.83 / 39.42 | 12.43 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_stop+5 | DEAD | 168 | 2.24 | 6.51 | 12.63 | 71 | -10.93 | 175 | -2.34 | 1.33 | 0.40 | 0.13 | -5.39 / 12.64 | 5.76 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_T15 | DEAD | 172 | 2.29 | 6.50 | 12.37 | 74 | -11.66 | 176 | -1.56 | 1.04 | 0.41 | 0.15 | -4.63 / 10.36 | 5.76 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_S5 | DEAD | 169 | 2.25 | 5.79 | 13.14 | 74 | -12.63 | 176 | -2.06 | 0.18 | 0.42 | 0.12 | -5.18 / 9.13 | 5.05 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_stop+5 | DEAD | 231 | 3.08 | 5.59 | 9.99 | 100 | -7.97 | 249 | -1.09 | 1.49 | 0.40 | 0.12 | -3.61 / 8.90 | 4.85 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_T15 | DEAD | 237 | 3.16 | 5.49 | 9.81 | 111 | -7.60 | 251 | -0.79 | 1.32 | 0.41 | 0.13 | -2.69 / 7.00 | 4.75 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_F60 | DEAD | 191 | 2.55 | 4.92 | 12.22 | 92 | -7.25 | 184 | -2.58 | 0.96 | 0.40 | 0.08 | -5.66 / 11.53 | 4.18 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_S5 | DEAD | 230 | 3.07 | 4.18 | 10.35 | 111 | -9.92 | 249 | -1.11 | -0.41 | 0.41 | 0.10 | -4.39 / 5.37 | 3.44 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_F60 | DEAD | 271 | 3.61 | 3.27 | 9.49 | 144 | -4.74 | 257 | -0.04 | 0.49 | 0.41 | 0.05 | -3.17 / 5.32 | 2.53 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_Tnext | DEAD | 247 | 3.29 | -1.25 | 6.39 | 103 | -9.09 | 252 | 0.92 | -3.55 | 0.65 | -0.02 | -2.31 / -5.00 | -1.99 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_Tnext | DEAD | 171 | 2.28 | -2.08 | 7.99 | 67 | -10.19 | 170 | -1.19 | -4.36 | 0.62 | -0.06 | -4.57 / -4.08 | -2.82 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H30_T2R | DEAD | 161 | 2.15 | -2.21 | 12.94 | 72 | -12.12 | 160 | -1.13 | -5.27 | 0.35 | -0.04 | -12.78 / 7.10 | -2.95 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |
| G2_c_W600_H15_T2R | DEAD | 217 | 2.89 | -3.03 | 11.44 | 104 | -9.24 | 210 | 1.60 | -5.04 | 0.35 | -0.06 | -11.90 / 4.41 | -3.77 | mean_up,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,cost2x_pre,year_share,stack_add_pre,best_of_N,hold,span2 |

## 3. Top 10 across all 41 cells by pre-window mean, regardless of verdict
| rank | cell | tier | pre n | pre mean pts | MDE | HOLD mean | X mean | failed gates |
|---|---|---|---|---|---|---|---|---|
| 1 | G2_c_W600_H15_X150 | DEAD | 35 | 13.20 | 36.77 | 13.26 | 0.04 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N |
| 2 | G2_c_W600_H30_X150 | DEAD | 22 | 13.17 | 53.39 | -21.24 | -0.97 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 3 | G1_c_W600_H30 | DEAD | 172 | 7.04 | 12.26 | -10.78 | -1.65 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 4 | G2_c_W600_H30_stop+5 | DEAD | 168 | 6.51 | 12.63 | -10.93 | -2.34 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 5 | G2_c_W600_H30_T15 | DEAD | 172 | 6.50 | 12.37 | -11.66 | -1.56 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 6 | G1_c_W600_H15 | DEAD | 237 | 5.97 | 9.73 | -7.84 | -1.14 | beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 7 | G2_c_W600_H30_S5 | DEAD | 169 | 5.79 | 13.14 | -12.63 | -2.06 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 8 | G2_c_W600_H15_stop+5 | DEAD | 231 | 5.59 | 9.99 | -7.97 | -1.09 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 9 | G2_c_W600_H15_T15 | DEAD | 237 | 5.49 | 9.81 | -7.60 | -0.79 | beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |
| 10 | G1_a_W300_H15 | DEAD | 29 | 5.42 | 30.63 | 5.66 | 1.22 | min_n,beats_a,beats_b,beats_c,beats_beta,vs_touch,vs_flow,year_share,stack_add_pre,best_of_N,hold,span2 |

## 4. Placebos, paired / layer comparisons (WFPRE; effect = real mean minus mean of 16 draws; CI week-block bootstrap)
G1 top 10 by pre mean:
| cell | (a) timing [CI] rank | (b) random zones [CI] rank | (c) shuffled gamma [CI] rank | (d) random dir [CI] rank | paired vs touch [CI] (selection-biased) | unpaired vs touch-all [CI] | vs flow trigger [CI] | draw means a/b/c/d |
|---|---|---|---|---|---|---|---|---|
| G1_c_W600_H30 | 6.36 [-1.58,15.87] 0.94 | 5.11 [-1.15,12.37] 0.94 | 0.41 [-0.82,1.86] 0.75 | 6.04 [0.42,12.52] 0.88 | -13.81 [-15.56,-11.74] | 5.14 [-1.47,12.74] | 3.02 [-8.50,14.97] | 0.68/1.93/6.64/1.01 |
| G1_c_W600_H15 | 7.03 [1.13,13.72] 1.00 | 3.61 [-0.77,8.34] 0.88 | -0.38 [-2.47,1.52] 0.31 | 3.78 [-1.08,9.22] 0.94 | -12.59 [-14.22,-10.71] | 4.04 [-1.30,9.81] | 3.09 [-6.36,13.20] | -1.06/2.36/6.35/2.19 |
| G1_a_W300_H15 | 4.60 [-13.54,29.89] 0.75 | 1.72 [-11.77,20.87] 0.69 | 5.49 [-9.98,26.81] 0.94 | 8.07 [-8.94,26.11] 0.94 | -17.91 [-25.38,-10.96] | 4.37 [-14.23,30.52] | 4.53 [-14.85,29.41] | 0.82/3.71/-0.06/-2.65 |
| G1_c_W600_H5 | 4.73 [-0.31,9.85] 0.94 | 1.65 [-2.57,5.93] 0.81 | 0.17 [-1.53,1.68] 0.56 | 3.28 [-0.84,7.60] 0.88 | -12.42 [-14.86,-10.30] | 3.39 [-1.14,8.25] | -0.15 [-7.96,7.91] | 0.59/3.66/5.15/2.04 |
| G1_a_W120_H30 | 4.40 [-6.24,13.38] 0.69 | -5.87 [-21.40,6.15] 0.25 | 7.17 [-2.27,15.38] 0.88 | 13.34 [3.86,21.33] 1.00 | -13.79 [-24.98,-6.18] | 3.88 [-5.46,12.42] | 5.71 [-6.75,16.30] | 0.46/10.73/-2.31/-8.49 |
| G1_c_W300_H5 | 4.99 [1.08,9.23] 1.00 | 2.47 [-0.79,5.90] 0.94 | -0.02 [-1.11,1.06] 0.44 | 2.15 [-1.75,6.19] 0.81 | -8.24 [-10.85,-5.50] | 3.32 [0.15,6.74] | 2.26 [-4.43,9.11] | -0.54/1.97/4.46/2.29 |
| G1_c_W300_H30 | 2.45 [-3.38,9.33] 0.81 | 3.12 [-1.64,8.62] 0.75 | -0.18 [-1.14,0.80] 0.44 | 2.32 [-2.45,7.41] 0.88 | -12.12 [-15.98,-7.59] | 2.14 [-2.90,8.14] | 4.34 [-4.77,13.71] | 0.74/0.07/3.36/0.86 |
| G1_a_W300_H30 | 7.67 [-10.38,29.21] 0.88 | -2.29 [-21.56,16.51] 0.38 | 4.79 [-11.26,22.77] 0.88 | 8.53 [-6.48,24.28] 0.88 | -19.67 [-31.13,-10.08] | 2.10 [-14.23,24.34] | 4.31 [-16.08,27.97] | -4.52/5.44/-1.64/-5.39 |
| G1_c_W300_H15 | 2.24 [-2.15,6.99] 0.81 | 1.24 [-2.22,4.66] 0.69 | -0.78 [-2.15,0.40] 0.00 | 1.27 [-1.79,4.49] 0.62 | -10.70 [-13.90,-7.18] | 1.99 [-1.66,5.72] | 2.15 [-5.98,9.75] | 0.80/1.80/3.82/1.77 |
| G1_a_W600_H5 | 3.28 [-15.67,25.33] 0.62 | -0.92 [-14.79,13.17] 0.44 | 4.67 [-11.15,22.58] 0.62 | 2.77 [-13.09,16.74] 0.75 | -15.25 [-18.54,-11.95] | 1.09 [-16.94,21.43] | -2.44 [-22.14,18.32] | -0.26/3.94/-1.65/0.25 |

G2 top 6:
| cell | (a) timing [CI] rank | (b) random zones [CI] rank | (c) shuffled gamma [CI] rank | (d) random dir [CI] rank | paired vs touch [CI] (selection-biased) | unpaired vs touch-all [CI] | vs flow trigger [CI] | draw means a/b/c/d |
|---|---|---|---|---|---|---|---|---|
| G2_c_W600_H15_X150 | 14.87 [-6.48,42.99] 1.00 | 11.52 [-2.89,31.18] 0.88 | -2.64 [-7.66,2.88] 0.06 | 5.11 [-11.14,23.38] 0.75 | -16.41 [-19.41,-13.43] | n/a | 10.32 [-13.25,40.16] | -1.67/1.68/15.84/8.09 |
| G2_c_W600_H30_X150 | 14.34 [-16.67,53.04] 0.94 | 11.99 [-9.69,42.33] 0.88 | -2.27 [-5.65,2.18] 0.12 | 3.97 [-13.66,23.20] 0.56 | -17.51 [-21.44,-12.81] | n/a | 9.14 [-23.79,51.11] | -1.17/1.18/15.44/9.19 |
| G2_c_W600_H30_stop+5 | 6.94 [-1.06,16.37] 1.00 | 5.18 [-1.32,12.46] 1.00 | 0.49 [-0.83,1.99] 0.81 | 3.72 [-2.70,11.01] 0.94 | -11.44 [-14.14,-7.58] | n/a | 4.10 [-7.96,16.41] | -0.43/1.33/6.02/2.78 |
| G2_c_W600_H30_T15 | 6.90 [-0.80,15.56] 0.94 | 4.43 [-1.92,11.84] 0.88 | 0.55 [-0.59,1.96] 0.88 | 5.66 [-0.26,12.31] 1.00 | -13.80 [-15.51,-11.72] | n/a | 3.33 [-8.30,15.06] | -0.40/2.07/5.95/0.84 |
| G2_c_W600_H30_S5 | 6.97 [-0.99,16.68] 0.94 | 5.77 [-1.20,13.68] 0.88 | 0.08 [-1.26,1.62] 0.50 | 3.93 [-2.79,11.55] 0.81 | -13.62 [-16.05,-11.19] | n/a | 2.44 [-10.80,15.32] | -1.18/0.02/5.71/1.86 |
| G2_c_W600_H15_stop+5 | 5.53 [-0.39,12.31] 0.81 | 3.02 [-1.72,8.08] 0.88 | -0.64 [-2.79,1.33] 0.25 | 3.52 [-1.61,9.08] 0.81 | -9.99 [-12.57,-6.96] | n/a | 2.66 [-7.19,13.08] | 0.06/2.58/6.23/2.07 |

Notes: (b) = static zones displaced to open + offset drawn from another day, trigger / labels recomputed; (a) timing destroyed; (c) shuffled gamma labels (membership only); (d) random direction at the same entry second and risk (bracket-beta). The 'paired vs touch' column is the preregistered gate (same episode, same side, same management); it is strongly negative everywhere because it conditions on episodes in which a trigger later occurred, and the zone-touch entry at the episode start gets the whole move at a better price, i.e. the pairing is biased against the trigger by selection. The unpaired comparison with all zone-touch trades is the fair layer measure and is positive but not significant for the best cells (e.g. c_W600_H30 +5.1 [-1.5,12.7]); only c_W300_H5 is marginally above zero ([+0.2,+6.7]) and it fails HOLD (-2.9 pts). Both are reported; the gate stays as preregistered.

## 5. Layer contributions (pre / HOLD; n, mean pts)
| W s | H s | zone-touch all (n, mean) | flow trigger no zone/cond (n, mean) | zone+trigger all types (n, mean) | type a | type b | type c |
|---|---|---|---|---|---|---|---|
| 120 | 5 | 4481, 1.09 / 4030, -2.68 | 428, 0.94 / 254, -0.14 | 1024, 1.08 / 602, -2.50 | 73, -0.38 / 34, 0.12 | 310, 1.50 / 166, -6.54 | 853, 1.41 / 496, -1.84 |
| 120 | 15 | 4428, 0.99 / 4017, -2.64 | 307, 0.99 / 183, 0.89 | 789, 0.02 / 420, -2.88 | 44, -2.21 / 16, -0.16 | 205, -2.55 / 108, -5.98 | 648, 0.21 / 342, -1.40 |
| 120 | 30 | 4422, 0.98 / 4012, -2.63 | 225, -0.86 / 130, 1.39 | 563, 1.81 / 277, -5.98 | 20, 4.86 / 11, -3.63 | 139, -2.41 / 72, -5.06 | 462, 2.22 / 223, -4.46 |
| 300 | 5 | 4761, 1.12 / 4011, -2.44 | 267, 2.18 / 146, 3.01 | 667, 3.00 / 375, -2.82 | 55, 0.96 / 27, 1.98 | 144, -1.90 / 79, -8.27 | 560, 4.44 / 303, -2.94 |
| 300 | 15 | 4743, 1.05 / 4008, -2.43 | 194, 0.89 / 105, 6.48 | 461, 2.85 / 225, -1.51 | 29, 5.42 / 10, 5.66 | 80, -0.22 / 41, -1.18 | 391, 3.04 / 189, -2.98 |
| 300 | 30 | 4738, 1.04 / 4006, -2.42 | 151, -1.16 / 72, 13.51 | 308, 3.31 / 142, -6.06 | 16, 3.15 / 4, 17.76 | 48, 0.42 / 25, -6.07 | 262, 3.18 / 119, -6.80 |
| 600 | 5 | 4788, 1.93 / 3758, -2.35 | 178, 5.46 / 83, -5.25 | 409, 4.12 / 209, -3.47 | 37, 3.02 / 13, 11.82 | 41, -3.82 / 21, 3.67 | 353, 5.31 / 183, -5.28 |
| 600 | 15 | 4788, 1.93 / 3758, -2.34 | 131, 2.88 / 57, -0.33 | 267, 5.77 / 119, -3.48 | 21, -2.27 / 4, 33.01 | 17, 1.98 / 7, 31.69 | 237, 5.97 / 111, -7.84 |
| 600 | 30 | 4786, 1.91 / 3758, -2.34 | 100, 4.02 / 41, -5.75 | 189, 5.85 / 77, -7.45 | 11, -14.47 / 1, 157.01 | 8, 0.60 / 2, 33.51 | 172, 7.04 / 74, -10.78 |
Zone-touch all = every episode start on both sides with the same stop / management (no trigger, no condition); flow = the same machine on rolling 10-min extremes (no zone, no condition); zone+trigger = all types pooled and sequenced; a/b/c = the condition layer.
Condition split (W=300 H=15, trigger events, cells with >= 15 events):
| window | location (1 above VAH, 0 inside, -1 below VAL) | gamma | path ahead | n | mean pts | win |
|---|---|---|---|---|---|---|
| WFPRE | -1 | neg | LVN | 23 | 17.58 | 0.43 |
| WFPRE | -1 | pos | HVN/normal | 31 | -2.25 | 0.45 |
| WFPRE | -1 | pos | LVN | 74 | 0.58 | 0.36 |
| WFPRE | 0 | neg | HVN/normal | 54 | 12.09 | 0.46 |
| WFPRE | 0 | pos | HVN/normal | 171 | 4.89 | 0.40 |
| WFPRE | 0 | pos | LVN | 39 | 8.48 | 0.49 |
| WFPRE | 1 | neg | LVN | 46 | -0.61 | 0.37 |
| WFPRE | 1 | pos | HVN/normal | 24 | -5.85 | 0.29 |
| WFPRE | 1 | pos | LVN | 142 | -5.34 | 0.32 |
| HOLD | -1 | pos | LVN | 38 | 6.69 | 0.39 |
| HOLD | 0 | pos | HVN/normal | 86 | 2.21 | 0.37 |
| HOLD | 0 | pos | LVN | 18 | 0.58 | 0.44 |
| HOLD | 1 | neg | LVN | 15 | 3.67 | 0.53 |
| HOLD | 1 | pos | HVN/normal | 17 | -10.89 | 0.18 |
| HOLD | 1 | pos | LVN | 80 | -3.81 | 0.39 |

## 6. Equal-risk and DS3-mix lines (additive, no lock engine; only cells with >= 30 pre trades and positive pre mean)
| cell | window | d_Sharpe | d_mean $/wk | CI d_mean | d_maxDD $ |
|---|---|---|---|---|---|
| G1_c_W600_H30 | WFPRE | 0.206 | 4182 | [-359,8839] | -4284 |
| G1_c_W600_H30 | HOLD | -0.164 | -2810 | [-4784,-822] | 26940 |
| G1_c_W600_H30 | X | -0.155 | -1828 | [-7136,3730] | 11898 |
| G1_c_W600_H15 | WFPRE | 0.240 | 5150 | [-399,10712] | -3059 |
| G1_c_W600_H15 | HOLD | -0.165 | -3247 | [-5927,-290] | 6359 |
| G1_c_W600_H15 | X | -0.166 | -1787 | [-8554,5856] | 14994 |
| G1_c_W600_H5 | WFPRE | 0.343 | 8055 | [1131,14846] | -24745 |
| G1_c_W600_H5 | HOLD | -0.161 | -2904 | [-6227,889] | -36263 |
| G1_c_W600_H5 | X | -0.088 | -1121 | [-8784,7077] | 21511 |
| G1_c_W300_H5 | WFPRE | 0.360 | 13583 | [1504,25714] | 18603 |
| G1_c_W300_H5 | HOLD | -0.282 | -4647 | [-12580,3447] | -8693 |
| G1_c_W300_H5 | X | 0.341 | 9920 | [-4892,26094] | 160431 |
| G1_c_W300_H30 | WFPRE | 0.075 | 4375 | [-3422,13540] | 10015 |
| G1_c_W300_H30 | HOLD | -0.231 | -3948 | [-7316,-322] | 47080 |
| G1_c_W300_H30 | X | -0.027 | 2579 | [-7922,13806] | -5128 |
| G1_c_W300_H15 | WFPRE | 0.196 | 8114 | [-2140,18555] | -17451 |
| G1_c_W300_H15 | HOLD | -0.227 | -3488 | [-8932,1940] | 5791 |
| G1_c_W300_H15 | X | -0.134 | 1988 | [-10194,15878] | 31905 |
| G1_a_W600_H5 | WFPRE | -0.007 | 104 | [-1802,2285] | -3054 |
| G1_a_W600_H5 | HOLD | 0.006 | 319 | [-929,1845] | 0 |
| G1_a_W600_H5 | X | 0.242 | 3525 | [-707,8267] | -60514 |
| G1_c_W120_H30 | WFPRE | 0.047 | 8145 | [-4273,22834] | 53191 |
| G1_c_W120_H30 | HOLD | -0.298 | -5337 | [-12298,2123] | 6108 |
| G1_c_W120_H30 | X | -1.210 | -16825 | [-31642,-1471] | 161405 |
| cell | window | d_Sharpe | d_mean $/wk | CI d_mean | d_maxDD $ |
|---|---|---|---|---|---|
| G2_c_W600_H15_X150 | WFPRE | 0.040 | 1614 | [-1074,5015] | -12105 |
| G2_c_W600_H15_X150 | HOLD | 0.011 | 220 | [-648,1309] | 0 |
| G2_c_W600_H15_X150 | X | 0.048 | 949 | [-2200,5142] | -3917 |
| G2_c_W600_H30_stop+5 | WFPRE | 0.161 | 3252 | [-675,7405] | -6319 |
| G2_c_W600_H30_stop+5 | HOLD | -0.136 | -2403 | [-4362,-613] | 25704 |
| G2_c_W600_H30_stop+5 | X | -0.206 | -2436 | [-6944,2372] | 8649 |
| G2_c_W600_H30_T15 | WFPRE | 0.188 | 3944 | [-639,8668] | 2746 |
| G2_c_W600_H30_T15 | HOLD | -0.184 | -3109 | [-5174,-1050] | 40365 |
| G2_c_W600_H30_T15 | X | -0.167 | -2135 | [-7511,3243] | 3020 |
| G2_c_W600_H30_S5 | WFPRE | 0.147 | 3174 | [-1445,8122] | -2304 |
| G2_c_W600_H30_S5 | HOLD | -0.177 | -3025 | [-5589,-296] | 15435 |
| G2_c_W600_H30_S5 | X | -0.219 | -2260 | [-8987,5224] | 33451 |
| G2_c_W600_H15_stop+5 | WFPRE | 0.198 | 4164 | [-569,8859] | -4484 |
| G2_c_W600_H15_stop+5 | HOLD | -0.133 | -2664 | [-5471,183] | 6823 |
| G2_c_W600_H15_stop+5 | X | -0.130 | -1381 | [-7679,5355] | 170 |
| G2_c_W600_H15_T15 | WFPRE | 0.215 | 4846 | [-718,10280] | 3971 |
| G2_c_W600_H15_T15 | HOLD | -0.171 | -3319 | [-6067,-324] | 20359 |
| G2_c_W600_H15_T15 | X | -0.131 | -1415 | [-8424,6178] | 5163 |
| G2_c_W600_H30_F60 | WFPRE | 0.079 | 2505 | [-1153,6748] | -15376 |
| G2_c_W600_H30_F60 | HOLD | -0.099 | -1963 | [-4640,544] | 17281 |
| G2_c_W600_H30_F60 | X | -0.173 | -2155 | [-5869,1755] | 25482 |
| G2_c_W600_H15_S5 | WFPRE | 0.141 | 3744 | [-1678,9256] | -1244 |
| G2_c_W600_H15_S5 | HOLD | -0.185 | -3885 | [-7169,-288] | -5196 |
| G2_c_W600_H15_S5 | X | -0.201 | -1633 | [-11168,7981] | 12013 |
| G2_c_W600_H15_F60 | WFPRE | 0.059 | 2366 | [-1810,6479] | -13230 |
| G2_c_W600_H15_F60 | HOLD | -0.083 | -2009 | [-5783,2232] | 10429 |
| G2_c_W600_H15_F60 | X | -0.016 | -47 | [-5084,5151] | -8737 |

## 7. Executability
Condition and zones (prior-day / prior-week value area, POC, VWAP, ON high/low, HVN/LVN, options-OI gamma sign from the daily file) are daily/bar logic and deliverable on a chart. The trigger (30-s aggressor delta, top-3 depth reload, 1-s acceptance with volume) needs the tape: execution-server logic. A bar-based proxy was NOT run: no cell reached CANDIDATE, so none is warranted.

## 8. Deviations / caveats
Reduced grid (41 of ~600 combinations; X fixed at 60 contracts per 30 s except G2 X150, T only 15/30); zones use HVN/LVN peaks and troughs rather than edges; VA is mine (70%, 1-pt bins from per-second VWAP prices) and differs from PRO_levels pdVAH/pdVAL by about 15-25 pts on the check day; prior-week VA needs >= 3 days; own 1-s simulator (not corepool, no DS replay); basis M not run; stack/mix lines additive without the lock engine; paired-vs-touch gate selection-biased (stated); placebo (b) pool days have missing zone slots; (a)(d) placebos not sequenced. The G2 composition used G1 WFPRE numbers only (prereg rule). Gamma is the last OI date before the day (feat_NQA: all NQ option families); days without a gamma value, outside 2023-02-10..2026-10-16, or with < 20,000 RTH seconds (half days) are excluded (914 scored days).

## 9. By session (entry time ET; n, mean pts; pre / HOLD) for the top G1 cells

| cell | 09:30-11:00 | 11:00-14:00 | 14:00-15:30 |
|---|---|---|---|
| G1_c_W600_H30 | 102, 5.0 / 44, -9.2 | 61, 6.5 / 23, -12.4 | 9, 34.1 / 7, -15.2 |
| G1_c_W600_H15 | 143, 4.5 / 68, -5.5 | 83, 5.9 / 35, -10.4 | 11, 25.1 / 8, -16.2 |
| G1_c_W600_H5 | 228, 4.7 / 111, -2.4 | 109, 4.0 / 60, -8.3 | 16, 22.9 / 12, -16.7 |
| G1_c_W300_H5 | 378, 4.5 / 202, -0.0 | 154, 3.5 / 82, -8.2 | 28, 9.0 / 19, -11.1 |

The afternoon slice is thin (<= 28 pre trades) and the sign flips between pre and HOLD in every session; there is no session in which the stack holds.
