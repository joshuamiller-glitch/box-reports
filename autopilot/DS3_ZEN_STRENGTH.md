# DS3_ZEN_STRENGTH - trend strength before the pullback (T-ZEN Addendum 4), D3ZSG, 2026-10-28

VERDICT: NOTHING about the trend before the touch predicts the bounce at the model's 15-pt stop (E1, PRE n = 2,521 resolved touches: out-of-fold AUC 0.48-0.51 logit / GBM, week-block nested, against a circular-shift null 95th percentile of 0.51-0.53; E2-E5 0.47-0.52), and no pre-touch gate beats random-in-regime with the same gate on HOLD: 0 of 30 cells pass G6 (the best, the fade of over-extended touches at the 60-pt bracket, ZF03_B60_FD, is +6.47 pts/trade vs random-in-regime on PRE with MDE80 7.07 and +2.31 on HOLD with MDE80 9.21, HOLD mean net -3.29 pts); 0 LEAD / 0 CANDIDATE; best-of-N over the 38 scored cells p ~ 0.12 (N = 109).

Order actually followed: (1) F2 section written first (below; the file was written, then the gate prereg was hashed at 18:31:35Z in DECISIONS.md), 2) gates scored on PRE, 3) PREHOLD text hashed and the two looks logged before any HOLD/X feature was built, 4) one HOLD look + X scored.

## F2 descriptive pass (PRE 2024-02-01..2025-06-30 only, all touches of E1, no selection)

Touch set: E1 = R1 (5-min EMA200 side) + L1 1-min EMA200 tol 5 pt + hold candle (wick reaches the line within 5 pt, close on the trend side), entry window 10:00-14:00 (entry bar start), first hold candle of each touch episode (episode = run of consecutive bars within tol while the regime side is unchanged). n = 2543 touches. E2-E5 (2,334 / 1,495 / 2,350 / 3,695 touches) are used for the AUC robustness only. Bounce = the 1R bracket target (+stop) is reached before -stop from the next-bar open, flat 15:55, unresolved at the flat = NaN (dropped from the bounce rate; counted).

### Base rates (all E1 PRE touches)
| stop | n_resolved | unresolved | unresolved_pct | bounce | ci | mean_pts_net1 | win_rate_net | breakeven_wr |
|---|---|---|---|---|---|---|---|---|
| 15 | 2521 | 22 | 0.9 | 0.474 | [0.452, 0.496] | -2.143 | 0.4707 | 0.5081 |
| 60 | 2156 | 387 | 15.2 | 0.4736 | [0.442, 0.509] | -3.57 | 0.4758 | 0.502 |

### Top 10 features by best-minus-worst decile spread, 15-pt stop (bounce-rate spread; null = circular-shift permutation, week-aware; shift_p95 = 95th percentile of the null spread, shift_p = share of null >= observed)
| rank | feature | n | spread | shift_p95 | shift_p | bottom_bucket_rate | top_bucket_rate | best_rate | worst_rate | best_pts | worst_pts | spearman |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | slope_entry_5 | 2521 | 0.171 | 0.137 | 0.0 | 0.49 | 0.389 | 0.56 | 0.389 | 0.315 | -4.66 | -0.036 |
| 2 | line_separation | 2521 | 0.159 | 0.151 | 0.037 | 0.443 | 0.46 | 0.571 | 0.413 | 0.59 | -4.163 | -0.025 |
| 3 | vol_impulse_over_pb | 2521 | 0.147 | 0.143 | 0.04 | 0.486 | 0.456 | 0.544 | 0.397 | -0.201 | -4.36 | -0.018 |
| 4 | rsi5_side | 2521 | 0.147 | 0.139 | 0.037 | 0.518 | 0.421 | 0.567 | 0.421 | 0.254 | -3.522 | -0.047 |
| 5 | slope_regime_20 | 2521 | 0.147 | 0.139 | 0.043 | 0.451 | 0.44 | 0.563 | 0.417 | 0.513 | -3.699 | -0.034 |
| 6 | leg_height | 2521 | 0.143 | 0.149 | 0.063 | 0.481 | 0.392 | 0.535 | 0.392 | -0.4 | -4.683 | -0.014 |
| 7 | pb_depth_frac | 2477 | 0.141 | 0.141 | 0.053 | 0.476 | 0.453 | 0.556 | 0.415 | 0.275 | -3.775 | -0.002 |
| 8 | line_separation_atr | 2521 | 0.131 | 0.155 | 0.173 | 0.447 | 0.484 | 0.56 | 0.429 | 0.315 | -3.396 | -0.014 |
| 9 | leg_vs_atr_median_leg | 2521 | 0.131 | 0.139 | 0.12 | 0.435 | 0.413 | 0.544 | 0.413 | -0.169 | -3.716 | -0.003 |
| 10 | slope_regime_5_atr | 2521 | 0.131 | 0.147 | 0.147 | 0.514 | 0.468 | 0.54 | 0.409 | -0.229 | -3.999 | -0.035 |

Features with shift_p < 0.05 at the 15-pt stop: 7 of 70 (chance: 3.5). Spread is information, not a verdict.

### Top 10 features by best-minus-worst decile spread, 60-pt stop (bounce-rate spread; null = circular-shift permutation, week-aware; shift_p95 = 95th percentile of the null spread, shift_p = share of null >= observed)
| rank | feature | n | spread | shift_p95 | shift_p | bottom_bucket_rate | top_bucket_rate | best_rate | worst_rate | best_pts | worst_pts | spearman |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | px_vs_daily_ema50 | 2156 | 0.276 | 0.218 | 0.0 | 0.537 | 0.417 | 0.633 | 0.356 | 13.986 | -18.246 | -0.068 |
| 2 | line_separation | 2156 | 0.256 | 0.202 | 0.003 | 0.481 | 0.486 | 0.623 | 0.367 | 13.208 | -17.173 | -0.061 |
| 3 | room_to_prior_levels | 1982 | 0.24 | 0.184 | 0.0 | 0.517 | 0.439 | 0.552 | 0.312 | 4.505 | -23.763 | -0.048 |
| 4 | line_separation_atr | 2156 | 0.239 | 0.181 | 0.0 | 0.458 | 0.486 | 0.616 | 0.377 | 12.208 | -15.959 | -0.049 |
| 5 | n_hh_k3 | 2156 | 0.226 | 0.188 | 0.013 | 0.509 | 0.465 | 0.55 | 0.324 | 4.598 | -22.101 | -0.08 |
| 6 | pb_depth_frac | 2119 | 0.217 | 0.161 | 0.0 | 0.491 | 0.434 | 0.575 | 0.358 | 7.491 | -18.101 | -0.051 |
| 7 | n_hl_k3 | 2156 | 0.211 | 0.189 | 0.033 | 0.507 | 0.455 | 0.559 | 0.347 | 5.42 | -19.323 | -0.078 |
| 8 | vwap_trend_side | 2156 | 0.202 | 0.176 | 0.013 | 0.495 | 0.477 | 0.551 | 0.349 | 4.542 | -19.315 | -0.06 |
| 9 | dist_opposing_4h_fvg | 1960 | 0.199 | 0.196 | 0.043 | 0.548 | 0.469 | 0.588 | 0.389 | 8.545 | -14.509 | -0.011 |
| 10 | n_big_vol_bars_pb | 2156 | 0.191 | 0.268 | 0.183 | 0.476 | 0.438 | 0.493 | 0.302 | -2.17 | -24.55 | -0.013 |

Features with shift_p < 0.05 at the 60-pt stop: 18 of 70 (chance: 3.5). Spread is information, not a verdict.

### Out-of-fold AUC (71 features, median-imputed + missing flags, week-block 5-fold outer with 3-fold inner tuning; PRE only)
| cell_stop_model | n | oof_auc | folds | null_p95 |
|---|---|---|---|---|
| E1_15_logit | 2521 | 0.4847 | [0.483, 0.493, 0.462, 0.461, 0.527] | 0.534 |
| E1_15_gbm | 2521 | 0.5074 | [0.524, 0.517, 0.499, 0.467, 0.545] | 0.526 |
| E1_60_logit | 2156 | 0.4894 | [0.489, 0.463, 0.465, 0.55, 0.5] | 0.518 |
| E1_60_gbm | 2156 | 0.551 | [0.505, 0.578, 0.446, 0.652, 0.622] | 0.524 |
| E2_15_logit | 2314 | 0.4993 | [0.502, 0.496, 0.506, 0.516, 0.496] | - |
| E2_15_gbm | 2314 | 0.5203 | [0.526, 0.493, 0.524, 0.52, 0.539] | - |
| E3_15_logit | 1477 | 0.4798 | [0.521, 0.449, 0.441, 0.479, 0.527] | - |
| E3_15_gbm | 1477 | 0.4693 | [0.528, 0.416, 0.483, 0.458, 0.477] | - |
| E4_15_logit | 2316 | 0.5077 | [0.545, 0.479, 0.515, 0.459, 0.539] | - |
| E4_15_gbm | 2316 | 0.5233 | [0.53, 0.487, 0.537, 0.512, 0.554] | - |
| E5_15_logit | 3673 | 0.5127 | [0.545, 0.505, 0.485, 0.49, 0.545] | - |
| E5_15_gbm | 3673 | 0.5142 | [0.541, 0.483, 0.508, 0.546, 0.496] | - |

Win-label (the label a learned gate would use; unresolved trades included):
| label | cell | auc | shift_null_p95 | folds |
|---|---|---|---|---|
| win of the traded bracket (net1>0) | win_E1_15_logit | 0.4813 | 0.522 | [0.479, 0.484, 0.441, 0.499, 0.508] |
| win of the traded bracket (net1>0) | win_E1_15_gbm | 0.5236 | 0.514 | [0.498, 0.506, 0.582, 0.491, 0.533] |
| win of the traded bracket (net1>0) | win_E1_60_logit | 0.5106 | 0.515 | [0.451, 0.611, 0.494, 0.515, 0.5] |
| win of the traded bracket (net1>0) | win_E1_60_gbm | 0.4957 | 0.507 | [0.503, 0.57, 0.451, 0.477, 0.494] |

### F2 reading (plain)
- At the model's 15-pt stop nothing is predictable: out-of-fold AUC 0.48-0.52 on E1 (null p95 0.51-0.53) and 0.47-0.52 on E2-E5; the top 10 spreads are non-monotone (e.g. the best feature, 5-bar entry-line slope, has a top-minus-bottom decile gap of -0.10 but the deciles in between zig-zag 0.39-0.56). 7 of 70 features clear their week-aware null at 5%, about twice chance, none monotone.
- At the 60-pt stop 18 of 70 features clear the null (chance 3.5) and the GBM OOF AUC is 0.551 (null p95 0.524, folds 0.45-0.65), BUT: the logit is 0.489, the same GBM on the traded win label is 0.496, and the signal-bearing features are the trend-size ones (price vs daily EMA50, 1m-200 / 5m-200 line separation, room to prior levels, number of higher highs, pullback depth): wide separation / extended / many higher highs go with LOWER bounce, i.e. the F4 direction (over-extension), not "stronger trend bounces more". 60-pt outcomes are day-level (15% unresolved, day-clustered); the touches within a day are not independent, which is why the plain permutation null (24 of 70) was replaced by the circular-shift null above.
- The learned-gate stop rule (OOF AUC < 0.55 => no gate): bounce label 15-pt: stop; bounce label 60-pt GBM 0.551 is a marginal pass; but the traded WIN label (what a gate would trade) is 0.496 (60) and 0.524 (15, null p95 0.514 GBM / logit 0.481). Decision (pre-declared here, before the prereg): NO learned-gate cell is created in STRENGTH (MX's M10 is the learned-gate cell of the program; it will see the same AUCs).
- Base rate: E1 bounces 47.4% at 15 pt (CI 45.2-49.6) against the cost-adjusted break-even 50.8%; mean -2.14 pts/trade net1. The entry itself is already below break-even at 15 pt before any gate.

## Gate prereg and scoring (F3 / F4)

Prereg l2vast/ds3/prereg/ZEN_STRENGTH_GATES_prereg.md sha256 532fed42be258da6a63cca125175d037c48e62a109741b22cf0d8680fae64589 (DECISIONS.md line, written AFTER the F2 section above and BEFORE any gate was scored). Pre-holdout text autopilot/DS3_STRENGTH_PREHOLD.md sha256 8fca81f2b02fd98d3aacd464d767bae3e972d548987723ff1ce0702c160dbf21; looks logged in l2vast/ds3/out/zen/strength/looks.jsonl (tracks D3ZSG_GD, D3ZSG_GD_SPAN2) before HOLD / X features or outcomes were built. Holdout looks used: 1 (HOLD) + 1 (X); 30 of 38 cell-directions looked at.

### Counts
- 38 cell-directions scored on PRE (18 F3 gate cells = 9 rules x {15/15, 60/60}; 20 F4 cell-directions = 5 over-extension rules x 2 brackets x {with-trend, fade}); 2 ungated base cells (E1 touches at 15/15 and 60/60) as controls.
- Screen gates: G1 (CI lower > 0 and rank >= 0.95 vs random-in-regime with the same rule) passed by 4 cells (ZF03_B60_FD, ZF01_B60_FD, ZF04_B60_FD, ZF03_B15_FD), G1-G5 all five by 0 (every one fails G5, effect inside MDE80; the best, ZF03_B60_FD, passes G1-G4 and misses G5 only: effect 6.47 vs MDE80 7.07).
- Best-of-N: reality-check (Z.bestofN over the 38 scored cells, shared draws) rank of the best effect (+6.47 pts, ZF03_B60_FD) = 0.88 => p ~ 0.12 over the 38; scaled to N = 109 (x109/38) p ~ 0.34. G8 fails for every cell.
- Holdout stage: G6 (HOLD sign agrees and CI lower > 0 vs random-in-regime with the same rule) passed by 0 of 30. G10 (direct 1-s/L2 replay) NOT RUN (no replay launched in this family): the best possible label here would be LEAD; no cell reaches it. Result: 0 LEAD, 0 CANDIDATE, 0 CONFIRMED; best-of-F label none.

### Ungated E1 touches (the base every gate is compared with; sequenced one-open-trade, net1 pts per contract, 10-lot $ = pts x 200)
| base | n_PRE | PRE_mean | PRE_win | PRE_be | PRE_eff_vs_rand | PRE_rank | HOLD_n | HOLD_mean | HOLD_eff | X_n | X_mean | X_eff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BASE_B15 | 1890 | -2.28 | 0.469 | 0.552 | -0.55 | 0.02 | 678 | -2.36 | 0.15 | 1005 | -0.8 | 0.12 |
| BASE_B60 | 697 | -4.66 | 0.475 | 0.517 | -4.42 | 0.01 | 282 | 1.15 | 0.72 | 335 | -2.16 | -0.56 |
(PRE effect vs random-in-regime is negative: the touch entry is WORSE than a random minute in the same regime at 60 pt (-4.4, rank 0.01); the base touch is not an edge.)

### F3 gate cells, all 18, PRE (random-in-regime column on every row; gate incr = mean(kept touches) - mean(excluded touches), unsequenced, week-block CI)
| cell | touches | kept% | n | mean1x | mean2x | win | BE | rand mean | eff vs rand | ci_lo | ci_hi | rank | MDE80 | eff vs dir | rank dir | excluded mean | gate incr | incr lo | incr hi | incr MDE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZG01_B15 | 2136 | 84.0 | 1689 | -2.25 | -4.15 | 0.47 | 0.55 | -1.75 | -0.51 | -1.14 | 0.16 | 0.07 | 0.91 | -0.5 | 0.05 | -1.93 | -0.26 | -2.07 | 1.62 | 2.6 |
| ZG01_B60 | 2136 | 84.0 | 686 | -4.67 | -6.64 | 0.47 | 0.52 | -0.11 | -4.57 | -8.09 | -1.43 | 0.0 | 4.75 | -2.97 | 0.04 | -0.8 | -3.3 | -13.26 | 5.72 | 13.5 |
| ZG02_B15 | 471 | 18.5 | 389 | -2.12 | -3.97 | 0.47 | 0.55 | -1.62 | -0.5 | -1.94 | 0.89 | 0.21 | 2.03 | -0.51 | 0.2 | -2.2 | 0.31 | -1.29 | 1.95 | 2.3 |
| ZG02_B60 | 471 | 18.5 | 274 | -4.55 | -6.44 | 0.47 | 0.52 | 1.38 | -5.94 | -13.28 | 0.94 | 0.01 | 10.2 | -2.92 | 0.19 | -3.1 | -2.53 | -10.4 | 5.07 | 11.05 |
| ZG03_B15 | 268 | 10.5 | 231 | -2.47 | -4.34 | 0.46 | 0.55 | -1.24 | -1.23 | -2.93 | 0.44 | 0.07 | 2.49 | -0.82 | 0.19 | -2.15 | 0.1 | -1.78 | 1.99 | 2.71 |
| ZG03_B60 | 268 | 10.5 | 165 | -6.02 | -7.82 | 0.45 | 0.51 | 0.44 | -6.46 | -15.07 | 1.97 | 0.02 | 12.15 | -5.1 | 0.14 | -3.72 | 1.46 | -8.76 | 10.83 | 13.68 |
| ZG04_B15 | 875 | 34.4 | 705 | -2.17 | -4.04 | 0.47 | 0.55 | -1.46 | -0.71 | -1.65 | 0.33 | 0.06 | 1.45 | -0.52 | 0.17 | -2.2 | 0.17 | -0.96 | 1.31 | 1.6 |
| ZG04_B60 | 875 | 34.4 | 339 | -4.18 | -6.13 | 0.47 | 0.51 | 0.77 | -4.95 | -10.26 | 0.05 | 0.01 | 7.59 | -2.07 | 0.25 | -4.24 | 1.94 | -4.96 | 8.46 | 9.39 |
| ZG05_B15 | 543 | 21.4 | 483 | -3.25 | -5.03 | 0.43 | 0.55 | -1.77 | -1.48 | -2.62 | -0.33 | 0.0 | 1.64 | -1.63 | 0.01 | -1.79 | -1.66 | -3.09 | -0.33 | 1.98 |
| ZG05_B60 | 543 | 21.4 | 302 | 0.48 | -1.56 | 0.52 | 0.51 | 1.09 | -0.61 | -6.77 | 5.43 | 0.4 | 8.64 | 2.23 | 0.73 | -3.9 | 1.52 | -3.81 | 6.53 | 7.39 |
| ZG06_B15 | 1051 | 41.3 | 666 | -1.63 | -3.49 | 0.49 | 0.55 | -1.73 | 0.1 | -0.96 | 1.06 | 0.61 | 1.43 | -0.17 | 0.32 | -2.62 | 1.15 | -0.22 | 2.5 | 1.93 |
| ZG06_B60 | 1051 | 41.3 | 197 | 6.68 | 4.61 | 0.56 | 0.5 | 2.76 | 3.92 | -4.45 | 12.06 | 0.99 | 11.78 | 8.94 | 0.99 | -7.24 | 8.89 | 1.43 | 16.18 | 10.38 |
| ZG07_B15 | 1376 | 54.1 | 963 | -1.65 | -3.54 | 0.49 | 0.55 | -1.59 | -0.06 | -0.88 | 0.7 | 0.47 | 1.14 | -0.01 | 0.47 | -2.89 | 1.38 | -0.01 | 2.75 | 1.98 |
| ZG07_B60 | 1376 | 54.1 | 329 | -1.19 | -3.2 | 0.51 | 0.52 | 1.35 | -2.54 | -7.79 | 2.39 | 0.07 | 7.21 | 1.22 | 0.65 | -8.0 | 8.2 | 1.16 | 15.1 | 9.97 |
| ZG08_B15 | 1271 | 50.0 | 1077 | -1.65 | -3.61 | 0.49 | 0.55 | -1.97 | 0.31 | -0.4 | 1.08 | 0.8 | 1.03 | 0.05 | 0.57 | -2.53 | 0.77 | -0.18 | 1.73 | 1.42 |
| ZG08_B60 | 1271 | 50.0 | 553 | -5.91 | -7.88 | 0.46 | 0.52 | -4.01 | -1.91 | -5.82 | 1.8 | 0.13 | 5.42 | -4.55 | 0.02 | -3.2 | -0.74 | -6.27 | 4.95 | 7.91 |
| ZG09_B15 | 2290 | 90.1 | 1654 | -1.88 | -3.78 | 0.48 | 0.55 | -1.87 | -0.01 | -0.62 | 0.65 | 0.46 | 0.89 | -0.3 | 0.15 | -4.7 | 2.84 | 0.62 | 4.9 | 3.04 |
| ZG09_B60 | 2290 | 90.1 | 615 | -4.44 | -6.38 | 0.48 | 0.52 | -3.91 | -0.53 | -3.27 | 2.1 | 0.38 | 3.84 | -2.89 | 0.07 | -9.17 | 6.22 | -0.99 | 13.65 | 10.45 |

Holdout / X for the F3 gate cells that were in the top 30 (the 8 cells below the PRE-effect cut had no look: ZF01_B60_WT, ZF02_B60_WT, ZF03_B60_WT, ZF04_B60_WT, ZG01_B60, ZG02_B60, ZG03_B60, ZG04_B60):
| cell | HOLD_n | HOLD_mean | HOLD_eff | HOLD_ci | HOLD_mde | X_n | X_mean | X_eff | X_ci |
|---|---|---|---|---|---|---|---|---|---|
| ZG01_B15 | 617 | -2.25 | 0.22 | [-0.68, 1.15] | 1.32 | 893 | -0.83 | 0.05 | [-0.79, 0.89] |
| ZG02_B15 | 147 | -3.49 | -1.25 | [-3.02, 0.46] | 2.49 | 254 | -0.93 | -0.02 | [-1.84, 1.84] |
| ZG03_B15 | 87 | -0.94 | 1.38 | [-0.69, 3.18] | 2.72 | 137 | -0.28 | 0.2 | [-2.70, 2.82] |
| ZG04_B15 | 250 | -2.22 | 0.45 | [-1.11, 2.16] | 2.31 | 388 | -1.01 | -0.27 | [-1.74, 1.25] |
| ZG05_B15 | 175 | -1.68 | 0.83 | [-0.73, 2.52] | 2.35 | 302 | -0.87 | 0.27 | [-1.39, 2.05] |
| ZG05_B60 | 105 | 1.76 | 1.01 | [-9.14, 10.71] | 14.38 | 179 | 2.4 | 4.83 | [-2.68, 12.38] |
| ZG06_B15 | 200 | -2.46 | -0.43 | [-2.15, 1.40] | 2.48 | 419 | 0.2 | 1.42 | [0.32, 2.62] |
| ZG06_B60 | 60 | -6.36 | -7.69 | [-22.58, 6.78] | 21.15 | 119 | 5.88 | 8.39 | [-1.58, 19.48] |
| ZG07_B15 | 338 | -1.96 | 0.5 | [-0.60, 1.69] | 1.63 | 526 | -0.52 | 0.76 | [-0.35, 1.93] |
| ZG07_B60 | 126 | -1.84 | -1.68 | [-12.34, 8.44] | 14.92 | 175 | 4.46 | 7.45 | [0.14, 14.36] |
| ZG08_B15 | 389 | -2.89 | -0.29 | [-1.61, 1.00] | 1.86 | 532 | -0.83 | 0.25 | [-0.81, 1.30] |
| ZG08_B60 | 222 | -0.84 | 1.73 | [-4.08, 7.19] | 8.11 | 267 | -6.38 | -2.25 | [-6.64, 1.86] |
| ZG09_B15 | 602 | -2.14 | 0.31 | [-0.57, 1.29] | 1.33 | 956 | -0.77 | 0.31 | [-0.43, 1.10] |
| ZG09_B60 | 247 | 3.07 | 4.02 | [-0.89, 8.83] | 6.93 | 325 | -2.69 | -0.72 | [-4.79, 2.91] |

### F4 inverse: over-extension rules, 20 cell-directions, PRE (WT = with-trend entry = the skip-filter test; FD = fade, opposite side same bracket = reversal entry)
| cell | n | kept_pct | mean_net1 | win | be_wr | rand_mean | eff_rand | ci_lo | ci_hi | rank_rand | mde80 | incr | incr_lo | incr_hi | HOLD eff (CI) | X eff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZF01_B15_WT | 625 | 30.9 | -2.82 | 0.45 | 0.56 | -1.64 | -1.18 | -2.4 | -0.04 | 0.0 | 1.67 | -0.87 | -2.28 | 0.52 | -0.91 [-2.45, 0.56] | -0.25 |
| ZF01_B15_FD | 625 | 30.9 | -0.68 | 0.53 | 0.56 | -1.57 | 0.89 | -0.3 | 2.15 | 0.97 | 1.75 | 0.64 | -0.76 | 2.06 | 0.98 [-0.53, 2.50] | 0.16 |
| ZF01_B60_WT | 309 | 30.9 | -5.48 | 0.47 | 0.52 | -0.4 | -5.08 | -10.74 | -0.32 | 0.0 | 7.58 | -8.06 | -16.1 | -0.22 | not looked (outside top 30) | - |
| ZF01_B60_FD | 309 | 30.9 | 2.27 | 0.53 | 0.51 | -2.84 | 5.11 | 0.32 | 10.83 | 1.0 | 7.6 | 7.71 | -0.08 | 15.86 | 1.48 [-5.73, 7.90] | 2.57 |
| ZF02_B15_WT | 241 | 10.0 | -3.61 | 0.41 | 0.55 | -1.73 | -1.88 | -3.82 | -0.09 | 0.02 | 2.66 | -1.69 | -3.6 | 0.1 | -0.62 [-3.21, 2.15] | 0.54 |
| ZF02_B15_FD | 241 | 10.0 | 0.21 | 0.56 | 0.55 | -1.44 | 1.65 | -0.12 | 3.45 | 0.96 | 2.58 | 1.53 | -0.2 | 3.33 | 0.32 [-2.37, 2.90] | -0.86 |
| ZF02_B60_WT | 172 | 10.0 | -2.72 | 0.48 | 0.51 | 1.79 | -4.5 | -12.19 | 3.19 | 0.1 | 11.16 | 1.78 | -4.62 | 8.16 | not looked (outside top 30) | - |
| ZF02_B60_FD | 172 | 10.0 | -0.09 | 0.51 | 0.51 | -4.87 | 4.78 | -2.91 | 12.48 | 0.91 | 11.14 | -1.57 | -7.87 | 4.77 | 11.19 [-1.99, 23.81] | -2.64 |
| ZF03_B15_WT | 754 | 36.5 | -3.27 | 0.44 | 0.56 | -1.75 | -1.53 | -2.54 | -0.6 | 0.0 | 1.4 | -1.36 | -2.76 | 0.01 | -0.08 [-1.47, 1.24] | -0.31 |
| ZF03_B15_FD | 754 | 36.5 | -0.36 | 0.54 | 0.56 | -1.47 | 1.11 | 0.14 | 2.14 | 0.99 | 1.44 | 0.98 | -0.37 | 2.37 | 0.01 [-1.35, 1.43] | 0.24 |
| ZF03_B60_WT | 369 | 36.5 | -7.65 | 0.45 | 0.52 | -1.23 | -6.42 | -11.74 | -1.77 | 0.0 | 7.1 | -12.0 | -18.94 | -4.66 | not looked (outside top 30) | - |
| ZF03_B60_FD | 369 | 36.5 | 4.51 | 0.55 | 0.51 | -1.96 | 6.47 | 1.86 | 11.8 | 1.0 | 7.07 | 11.8 | 4.5 | 18.69 | 2.31 [-4.43, 8.48] | 2.87 |
| ZF04_B15_WT | 840 | 39.3 | -2.16 | 0.47 | 0.55 | -1.69 | -0.47 | -1.45 | 0.51 | 0.16 | 1.36 | 0.02 | -1.2 | 1.19 | -0.10 [-1.38, 1.09] | 0.35 |
| ZF04_B15_FD | 840 | 39.3 | -1.27 | 0.5 | 0.55 | -1.48 | 0.21 | -0.74 | 1.16 | 0.65 | 1.33 | -0.18 | -1.34 | 1.0 | 0.27 [-0.92, 1.57] | -0.46 |
| ZF04_B60_WT | 483 | 39.3 | -3.97 | 0.48 | 0.52 | 0.57 | -4.55 | -9.08 | -0.47 | 0.0 | 6.19 | 0.05 | -6.15 | 6.01 | not looked (outside top 30) | - |
| ZF04_B60_FD | 483 | 39.3 | 0.77 | 0.51 | 0.5 | -3.7 | 4.47 | 0.25 | 9.1 | 1.0 | 6.37 | -0.1 | -6.08 | 6.13 | -0.27 [-6.11, 6.03] | -0.8 |
| ZF05_B15_WT | 428 | 19.7 | -2.42 | 0.46 | 0.55 | -1.65 | -0.77 | -2.09 | 0.65 | 0.1 | 1.98 | -0.26 | -1.56 | 1.09 | 0.29 [-1.71, 2.34] | -0.72 |
| ZF05_B15_FD | 428 | 19.7 | -0.56 | 0.53 | 0.55 | -1.55 | 0.99 | -0.46 | 2.31 | 0.94 | 2.0 | 0.65 | -0.69 | 1.94 | -0.01 [-2.01, 1.94] | 0.76 |
| ZF05_B60_WT | 268 | 19.7 | -3.8 | 0.48 | 0.51 | 0.25 | -4.06 | -8.95 | 0.71 | 0.05 | 6.9 | 0.92 | -5.25 | 6.88 | -0.59 [-9.79, 8.25] | -1.84 |
| ZF05_B60_FD | 268 | 19.7 | 0.8 | 0.51 | 0.5 | -3.43 | 4.23 | -0.54 | 9.09 | 0.95 | 6.86 | -0.76 | -6.71 | 5.39 | 0.58 [-8.27, 9.86] | 1.86 |

Reading F4: over-extended touches (leg >= 3 ATR off the entry line, >= 5 higher highs, top-decile RSI, leg >= 4 ATR) do fail MORE than a random in-regime minute with the same rule in PRE (with-trend effect -1.2 to -1.9 pts at 15 pt for the three rules with CI below 0, rank 0.00-0.02, CI excludes 0 for ZF01/ZF02/ZF03 at 15; -4.5 to -6.4 at 60 pt), and the fade is the mirror (ZF03_B60_FD +6.47 vs random, n = 369, win 55.0% vs break-even 50.9%, mean +4.5 pts net, +2.3 at 2x cost). It does not survive the HOLD look: ZF03_B60_FD HOLD effect +2.31 (CI -4.43..+8.48, MDE80 9.21, n = 155) with mean net -3.29 pts; ZF01_B60_FD +1.48 [-5.73, 7.90]; ZF04_B60_FD -0.27; the 15-pt fades have HOLD effects -0.01 to +0.98 with every CI spanning 0. G6 fails for all 30; the PRE effect of the best cell (6.47) is below its own MDE80 (7.07), i.e. inside noise on PRE too. The with-trend skip-filter B60 cells with the strongest PRE negative effect (ZF01/ZF02/ZF03/ZF04 at 60 pt, -4.5 to -6.4) were by the prereg rule (top 30 by effect) NOT among the looked cells; their fade mirrors were looked and show the same-sign but insignificant HOLD effect; the skip rule is therefore a hint, not a result.

## Top 10 cells by PRE effect vs random-in-regime (mandatory, regardless of verdict). win vs be_wr = realised win rate vs the cost-adjusted empirical break-even; fwd_weeks_80 = forward weeks for 80% power if the PRE effect were real = 74 x (MDE80/effect)^2
| cell | n_PRE | win | be_wr | trades_wk | PRE_mean | PRE_eff | PRE_ci | PRE_rank | MDE80 | HOLD_n | HOLD_mean | HOLD_eff | HOLD_ci | HOLD_mde | X_n | X_mean | X_eff | fwd_weeks_80 | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZF03_B60_FD | 369 | 0.55 | 0.509 | 5.0 | 4.51 | 6.47 | [1.86, 11.80] | 1.0 | 7.07 | 155 | -3.29 | 2.31 | [-4.43, 8.48] | 9.21 | 186 | 2.18 | 2.87 | 88.0 | G5,G6,G8,G9 |
| ZF01_B60_FD | 309 | 0.531 | 0.509 | 4.2 | 2.27 | 5.11 | [0.32, 10.83] | 1.0 | 7.6 | 137 | -3.2 | 1.48 | [-5.73, 7.90] | 9.67 | 156 | 1.4 | 2.57 | 163.0 | G2,G5,G6,G8,G9 |
| ZF02_B60_FD | 172 | 0.512 | 0.512 | 2.6 | -0.09 | 4.78 | [-2.91, 12.48] | 0.91 | 11.14 | 76 | 5.25 | 11.19 | [-1.99, 23.81] | 18.22 | 111 | -3.79 | -2.64 | 402.0 | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| ZF04_B60_FD | 483 | 0.511 | 0.504 | 6.4 | 0.77 | 4.47 | [0.25, 9.10] | 1.0 | 6.37 | 198 | -6.31 | -0.27 | [-6.11, 6.03] | 8.9 | 268 | -0.58 | -0.8 | 150.0 | G2,G3,G5,G6,G7,G8,G9 |
| ZF05_B60_FD | 268 | 0.511 | 0.504 | 3.6 | 0.8 | 4.23 | [-0.54, 9.09] | 0.95 | 6.86 | 108 | -2.52 | 0.58 | [-8.27, 9.86] | 13.17 | 150 | 2.64 | 1.86 | 195.0 | G1,G2,G3,G5,G6,G8,G9 |
| ZG06_B60 | 197 | 0.563 | 0.503 | 2.8 | 6.68 | 3.92 | [-4.45, 12.06] | 0.99 | 11.78 | 60 | -6.36 | -7.69 | [-22.58, 6.78] | 21.15 | 119 | 5.88 | 8.39 | 668.0 | G1,G5,G6,G8,G9 |
| ZF02_B15_FD | 241 | 0.556 | 0.548 | 3.6 | 0.21 | 1.65 | [-0.12, 3.45] | 0.96 | 2.58 | 95 | -2.55 | 0.32 | [-2.37, 2.90] | 3.68 | 169 | -2.42 | -0.86 | 182.0 | G1,G3,G5,G6,G7,G8,G9 |
| ZF03_B15_FD | 754 | 0.544 | 0.557 | 10.2 | -0.36 | 1.11 | [0.14, 2.14] | 0.99 | 1.44 | 274 | -2.25 | 0.01 | [-1.35, 1.43] | 1.95 | 402 | -1.23 | 0.24 | 124.0 | G3,G4,G5,G6,G8,G9 |
| ZF05_B15_FD | 428 | 0.53 | 0.551 | 5.8 | -0.56 | 0.99 | [-0.46, 2.31] | 0.94 | 2.0 | 165 | -2.63 | -0.01 | [-2.01, 1.94] | 2.85 | 242 | -0.47 | 0.76 | 306.0 | G1,G2,G3,G4,G5,G6,G8,G9 |
| ZF01_B15_FD | 625 | 0.534 | 0.559 | 8.4 | -0.68 | 0.89 | [-0.30, 2.15] | 0.97 | 1.75 | 256 | -1.23 | 0.98 | [-0.53, 2.50] | 2.15 | 351 | -1.45 | 0.16 | 287.0 | G1,G3,G4,G5,G6,G8,G9 |

### By year (WF = PRE + HOLD, mean net1 pts per trade; max year share of WF P&L) and gate status for the top 10
| cell | yr_2024 | yr_2025 | yr_2026 | maxyear_share | pass_all |
|---|---|---|---|---|---|
| ZF03_B60_FD | 5.42 | -0.9 | 8.46 | 1.0 | False |
| ZF01_B60_FD | 1.5 | -1.49 | 14.58 | 1.43 | False |
| ZF02_B60_FD | -4.07 | 6.17 | 14.54 | 1.89 | False |
| ZF04_B60_FD | 0.82 | -4.84 | 19.11 | nan | False |
| ZF05_B60_FD | -1.48 | 0.57 | 7.0 | nan | False |
| ZG06_B60 | 8.38 | -0.48 | -16.86 | 1.2 | False |
| ZF02_B15_FD | 0.72 | -1.76 | -4.97 | nan | False |
| ZF03_B15_FD | 0.47 | -1.78 | -2.88 | nan | False |
| ZF05_B15_FD | 0.07 | -1.95 | -8.11 | nan | False |
| ZF01_B15_FD | 0.26 | -1.43 | -2.65 | nan | False |

### By entry window (WF real trades, net1 pts and n; 09:30-10:00 and 14:00-15:30 are outside the PRIMARY screen window and were not run; the screen window is 10:00-14:00 only)
| cell | PRIMARY_pts | W10_pts | W11_pts | W12_pts | W13_pts | PRIMARY_n | W10_n | W11_n | W12_n | W13_n |
|---|---|---|---|---|---|---|---|---|---|---|
| ZF01_B15_FD | -0.84 | 0.54 | -3.12 | 0.04 | -0.87 | 881 | 165 | 181 | 219 | 316 |
| ZF01_B60_FD | 0.59 | 1.29 | 4.09 | -1.03 | -0.91 | 446 | 102 | 92 | 113 | 139 |
| ZF02_B15_FD | -0.57 | -0.35 | -0.7 | 0.01 | -1.48 | 336 | 154 | 67 | 53 | 62 |
| ZF02_B60_FD | 1.55 | 10.72 | -14.95 | 2.34 | -11.33 | 248 | 131 | 44 | 34 | 39 |
| ZF03_B15_FD | -0.86 | -0.21 | -1.55 | -0.96 | -0.99 | 1028 | 294 | 193 | 212 | 329 |
| ZF03_B60_FD | 2.2 | 3.64 | 7.76 | -0.36 | -1.14 | 524 | 164 | 99 | 112 | 149 |
| ZF04_B60_FD | -1.29 | -2.34 | -5.0 | 3.59 | -0.06 | 681 | 239 | 157 | 132 | 153 |
| ZF05_B15_FD | -1.14 | -1.43 | -1.08 | 0.1 | -2.07 | 593 | 203 | 131 | 135 | 124 |
| ZF05_B60_FD | -0.16 | 2.08 | 0.2 | -6.96 | 2.3 | 376 | 150 | 80 | 78 | 68 |
| ZG06_B60 | 3.63 | 4.23 | 4.19 | -1.34 | 3.03 | 257 | 151 | 56 | 21 | 29 |

Not produced (stated): long/short split and half-year tables for the 30 (the real trade frames do not carry the signed side column; the F4/F3 touches are 53-59% long in all cells); structural stop/target heat tables (not a STRENGTH item).

## The plain sentence

Nothing about the trend before the touch predicts the bounce: the only pre-touch feature family with a visible link is leg over-extension (entry line >= 3 ATR from the 5-minute EMA200, >= 5 higher highs, leg >= 4 ATR), and gating on it (fading the touch) changes pts/trade by +6.5 on PRE (MDE80 7.1, inside noise, best-of-N p ~ 0.12) and by +2.3 on HOLD (MDE80 9.2, mean net -3.3 pts), so it does not matter; at the 15-pt stop no feature and no combination carries information (OOF AUC 0.48-0.52 vs null 0.51-0.53).

## Deviations, assumptions and disclosures

- Touch = first hold candle per touch episode (2,543 E1 PRE touches); the plan's 5,446 per (regime, line) cell counts every qualifying bar. E1 is the primary cell; E2-E5 were used only for the AUC. Gates were applied to E1 only. Feature ranking/deciles are E1 only (70 of 71 features had variation; one is constant/missing in PRE and still counted).
- Flat 15:55 only (the plan's STRENGTH N has no flat doubling); flat 14:00 was not run. The 15-pt bracket is the 1R 15/15 label bracket, not the model's nearest-swing target. Unresolved trades at the flat: 0.9% (15 pt), 15.2% (60 pt), dropped from bounce rates (F2) and kept as trades (scoring).
- Circular-shift null (my addition): touches in one day/week share outcomes, so the plain permutation null (24 of 70 features significant at 60 pt) was too tight; the week-aware shift null gives 18 of 70 at 60 pt and 7 of 70 at 15 pt (chance 3.5). The 60-pt bounce GBM AUC 0.551 (null p95 0.524) is above the M10 0.55 line by 0.001 on the bounce label but 0.496 on the traded win label; no learned-gate cell was created (MX owns the program's M10 cell; same data).
- Random-in-regime pool = all 86,252 PRE R1 PRIMARY minutes with the same rule. Pool minutes are not pullbacks: first_touch is true at 98% of pool minutes vs 84% of touches; rule-true pool shares differ a lot from touch shares (e.g. slope < 0.229 keeps 90% of touches, 37% of the pool). G1 therefore partly measures touch + rule vs any minute + rule; the gate increment (kept minus excluded touches) is reported beside it. Ungated E1 touches themselves are WORSE than random in-regime minutes at 60 pt on PRE (-4.4, rank 0.01).
- The Addendum's RSI > 75 never occurs at a touch (0 of 2,543); replaced by the PRE top decile (>= 55.639). '5+ higher highs without a 20-line touch': no 20-line-touch feature exists in the vector; n_hh_k3 >= 5 used. Features not buildable/approximate: scheduled-release minutes are the fixed 08:30/10:00/14:00 proxy; day-type = first-hour ratio (NaN before 11:00 touches only matters for gates not run); ES/RTY agreement NaN before 2023-08 (not used in any rule).
- Skip-test selection effect: the top-30 rule (by effect) excluded the four B60 with-trend F4 cells that have the strongest PRE negative effect (-4.5 to -6.4); they have no HOLD look. Their fades did get a look and failed G6.
- G10 (direct 1-s/L2 replay) not run (no replay launched); the screen is on the mapped conservative basis (1-min bars are 0.05-0.13 pts/trade more conservative than the 1-s path on tight stops). Prereg header timestamp (18:35:00Z) was typed ahead; the DECISIONS.md line (18:31:35Z) is the clock record. This report's top lines (verdict/order) were rewritten after scoring; the F2 section text is unchanged from the version written before the prereg hash.
- Holdout looks used: 1 HOLD (2025-07-01..2026-02-06, capped by the standing rule) + 1 X (2023-04-01..2024-01-31). UNTOUCHED never read. No library bug found; HOLD/X feature builds ran only after the looks were logged.
- Screened N = 109 (plan 101: the fade direction of the 10 F4 cells adds 10, 20 F3 cells became 18).

## Files
- Code: l2vast/ds3/code/zen/strength/{st_common,f2_build,f2_analyze,f2_null,f2_winauc,f2_report,cand_build,st_score,st_select,st_final,st_report,st_test}.py (tests: out/zen/strength/st_test.log 8/8)
- Out: l2vast/ds3/out/zen/strength/{f2_feature_ranking_E1.csv,f2_decile_tables_E1.csv (all 71 features, deciles with n/CI/mean pts, 15 and 60 pt),f2_auc.json,screen_PRE_gates.csv,score_{PRE,HOLD,X}.csv,final_top30.csv,final_windows.csv,looks.jsonl}
- Prereg: l2vast/ds3/prereg/ZEN_STRENGTH_GATES_prereg.md (+ .sha256); autopilot/DS3_STRENGTH_PREHOLD.md

DONE STRENGTH
