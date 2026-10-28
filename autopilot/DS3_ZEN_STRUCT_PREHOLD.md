# DS3_ZEN_STRUCT_PREHOLD - PRE-only text for the top 30 (D3ZST, T-ZEN). Written BEFORE any HOLD / X bar of any trade was simulated.

Selection rule (prereg ZEN_STRUCT_S3_prereg.md sha256 51e36df3b7f753f9e9d06b6ad56716ffbac2be5ea74b96aad297c80d65ec5e53): eligible = >=100 valid real PRE trades (unsequenced grid) and effect>0 vs the pool expectation, one pair per (cell, stop source, target), ordered by effect then n; top 30 of 11,073 eligible pairs (11,013 S3, 60 S4/S5). Numbers below are PRE, sequenced (one open trade), 100-draw placebos.

| # | cell | pair | n seq | mean net1 | net2 | effect vs random-in-regime [CI] | rank | MDE80 | eff vs rand dir | rank | win | BE win | stop med/p90 | G1-G5 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | E2 | cap60|prev_day_extreme+0t|swing_5m_k2_equal_highs | 31 | 0.35 | -1.72 | +5.13 [-0.82, 11.28] | 0.99 | 8.5 | +1.48 | 0.99 | 0.677 | 0.667 | 51.5 / 59.2 | fPfPf |
| 2 | E2 | cap15|swing_15m_k3_last+0t|pivot_R1 | 50 | 0.96 | -0.18 | +0.68 [-3.85, 6.94] | 0.65 | 7.7 | +0.99 | 0.85 | 0.220 | 0.194 | 7.6 / 14.2 | fffPf |
| 3 | E2 | cap20|session_extreme+5t|pivot_R1 | 36 | 1.87 | 0.75 | +1.21 [-8.82, 12.05] | 0.68 | 14.8 | -5.91 | 0.00 | 0.194 | 0.166 | 12.9 / 18.8 | ffPPf |
| 4 | E2 | atr1.5|session_extreme+2t|session_extreme | 71 | 0.28 | -0.91 | +2.79 [-5.60, 12.14] | 0.78 | 12.6 | -4.79 | 0.05 | 0.183 | 0.180 | 16.8 / 35.8 | fffPf |
| 5 | E5 | atr1.5|prev_hour_extreme+2t|swing_4h_nearest_high | 73 | 3.33 | 1.78 | +3.70 [-2.20, 12.44] | 0.99 | 10.1 | +4.01 | 1.00 | 0.329 | 0.249 | 10.5 / 24.7 | fPPPf |
| 6 | E5 | cap30|session_extreme+5t|swing_5m_k3_lower_high | 27 | -0.15 | -2.33 | +3.99 [-3.35, 15.18] | 0.98 | 12.9 | +0.94 | 0.98 | 0.370 | 0.377 | 26.2 / 29.5 | fPfff |
| 7 | E4 | cap60|prev_day_extreme+0t|swing_4h_nearest_high | 151 | 0.95 | -0.56 | +2.81 [-1.95, 9.96] | 0.91 | 8.3 | +2.54 | 1.00 | 0.325 | 0.309 | 23.8 / 52.8 | fPfPf |
| 8 | E2 | atr1.5|session_extreme+2t|donchian_100 | 71 | 0.01 | -1.15 | +2.27 [-5.82, 11.36] | 0.71 | 12.3 | -4.94 | 0.04 | 0.183 | 0.183 | 16.8 / 35.8 | fffPf |
| 9 | E2 | cap15|swing_15m_k3_last+0t|swing_4h_nearest_high | 74 | 1.21 | 0.00 | +2.03 [-1.83, 6.91] | 0.90 | 6.4 | +0.76 | 0.88 | 0.216 | 0.185 | 8.2 / 14.2 | ffPPf |
| 10 | E2 | atr1.5|session_extreme+2t|donchian_50 | 71 | -0.41 | -1.62 | +2.17 [-5.39, 10.95] | 0.74 | 11.8 | -4.87 | 0.03 | 0.183 | 0.187 | 16.8 / 35.8 | fffff |
| 11 | E5 | cap30|session_extreme+5t|swing_5m_k2_lower_high | 26 | 0.63 | -1.33 | +5.32 [-1.91, 13.56] | 1.00 | 11.1 | +1.73 | 1.00 | 0.423 | 0.402 | 25.5 / 29.4 | fPfPf |
| 12 | E3 | atr1.5|round_50+0t|prev_day_close | 136 | 1.31 | -0.07 | +1.88 [-0.96, 5.12] | 0.85 | 4.4 | +0.88 | 0.86 | 0.257 | 0.214 | 5.6 / 21.9 | fffPf |
| 13 | E2 | atr1.5|session_extreme+2t|opening_range_or30 | 71 | -0.16 | -1.35 | +2.66 [-5.64, 11.79] | 0.76 | 12.5 | -4.85 | 0.05 | 0.183 | 0.185 | 16.8 / 35.8 | fffff |
| 14 | E2 | atr1.5|session_extreme+2t|vwap_p2sd | 71 | -0.75 | -1.96 | +1.93 [-5.69, 10.56] | 0.68 | 11.6 | -5.07 | 0.01 | 0.183 | 0.191 | 16.8 / 35.8 | fffff |
| 15 | E2 | atr1.5|session_extreme+2t|prev_hour_extreme | 72 | 0.30 | -0.93 | +2.71 [-5.32, 11.44] | 0.78 | 12.0 | -4.97 | 0.02 | 0.208 | 0.205 | 16.9 / 35.5 | fffPf |
| 16 | E2 | atr1.5|session_extreme+2t|opening_range_or15 | 71 | 0.60 | -0.63 | +2.85 [-5.82, 12.22] | 0.76 | 13.1 | -3.29 | 0.08 | 0.197 | 0.191 | 16.8 / 35.8 | fffPf |
| 17 | E2 | cap20|session_extreme+5t|swing_5m_k2_lower_high | 50 | 0.62 | -1.04 | +3.84 [-1.34, 9.92] | 0.98 | 8.1 | -1.23 | 0.17 | 0.300 | 0.282 | 16.8 / 19.0 | fffPf |
| 18 | E2 | atr1.5|session_extreme+2t|swing_15m_k3_nearest_high | 90 | 3.01 | 0.79 | +4.18 [0.24, 8.56] | 0.97 | 6.0 | +1.35 | 0.88 | 0.544 | 0.435 | 16.2 / 33.1 | PfPPf |
| 19 | E2 | atr1.5|session_extreme+5t|sd_ext_2.25 | 67 | -2.99 | -4.04 | +0.97 [-7.95, 11.08] | 0.57 | 13.8 | -4.61 | 0.08 | 0.134 | 0.158 | 16.8 / 36.8 | fffff |
| 20 | E2 | atr1.5|session_extreme+2t|R3 | 77 | -0.20 | -1.58 | +2.13 [-5.10, 10.29] | 0.81 | 11.1 | -1.81 | 0.24 | 0.260 | 0.262 | 16.0 / 34.4 | fffff |
| 21 | E1 | cap60|prev_day_extreme+2t|swing_5m_k2_equal_highs | 46 | -0.49 | -2.51 | +4.19 [-1.56, 10.50] | 0.98 | 8.5 | +0.66 | 0.85 | 0.652 | 0.668 | 49.1 / 57.9 | fffff |
| 22 | E5 | cap30|session_extreme+5t|swing_3m_k3_lower_high | 44 | -1.48 | -3.42 | +3.64 [-1.29, 8.56] | 0.98 | 7.0 | -0.03 | 0.47 | 0.386 | 0.450 | 23.5 / 29.5 | fffff |
| 23 | E2 | atr1.5|session_extreme+2t|swing_5m_k2_leg_high | 72 | -0.96 | -2.18 | +1.42 [-6.03, 9.90] | 0.64 | 11.5 | -5.30 | 0.01 | 0.194 | 0.205 | 16.9 / 35.5 | fffff |
| 24 | E1 | atr1.5|session_extreme+0t|swing_5m_k2_lower_high | 51 | -4.23 | -5.91 | -1.58 [-7.84, 4.06] | 0.22 | 8.4 | -4.16 | 0.00 | 0.294 | 0.403 | 15.8 / 35.2 | fffff |
| 25 | E1 | cap15|session_extreme+5t|pivot_R1 | 32 | -2.51 | -3.67 | -3.66 [-9.76, 2.76] | 0.07 | 8.9 | -4.25 | 0.01 | 0.156 | 0.215 | 9.9 / 14.7 | fffff |
| 26 | E4 | atr1.5|swing_15m_k3_last+5t|swing_3m_k3_leg_high | 90 | 2.84 | 1.21 | +5.03 [0.43, 10.01] | 0.99 | 6.7 | +2.52 | 0.99 | 0.289 | 0.222 | 9.1 / 31.3 | PPPPf |
| 27 | E5 | atr1.5|swing_5m_k2_impulse_start+0t|prev_day_close | 98 | 6.81 | 4.83 | +4.58 [-1.78, 11.51] | 1.00 | 9.5 | +5.61 | 1.00 | 0.408 | 0.246 | 12.6 / 30.4 | fPPPf |
| 28 | E2 | cap20|swing_15m_k3_last+5t|prev_day_extreme | 75 | 1.06 | -0.32 | -1.78 [-6.35, 3.36] | 0.21 | 7.1 | +0.05 | 0.57 | 0.253 | 0.229 | 14.0 / 19.2 | fffPf |
| 29 | E5 | atr1.5|swing_5m_k3_higher+5t|prev_day_close | 107 | 4.74 | 3.05 | +3.44 [-1.41, 8.76] | 0.98 | 7.3 | +2.66 | 1.00 | 0.336 | 0.211 | 8.2 / 24.0 | fPPPf |
| 30 | E3 | cap60|prev_day_extreme+0t|swing_15m_k2_equal_highs | 43 | -3.28 | -5.43 | +3.56 [-3.18, 10.04] | 0.97 | 9.4 | -0.10 | 0.47 | 0.488 | 0.584 | 41.0 / 55.0 | fffff |

Frozen definitions (specs) for the single HOLD look and the X look:
```json
[
{
"id": "S3|E2|cap60|prev_day_extreme+0t|swing_5m_k2_equal_highs",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "prev_day_extreme+0t",
"target": "swing_5m_k2_equal_highs",
"skip": "cap60",
"line": "ema200"
}
},
{
"id": "S3|E2|cap15|swing_15m_k3_last+0t|pivot_R1",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "swing_15m_k3_last+0t",
"target": "pivot_R1",
"skip": "cap15",
"line": "ema200"
}
},
{
"id": "S3|E2|cap20|session_extreme+5t|pivot_R1",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "pivot_R1",
"skip": "cap20",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|session_extreme",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "session_extreme",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E5|atr1.5|prev_hour_extreme+2t|swing_4h_nearest_high",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "prev_hour_extreme+2t",
"target": "swing_4h_nearest_high",
"skip": "atr1.5",
"line": "ema50"
}
},
{
"id": "S3|E5|cap30|session_extreme+5t|swing_5m_k3_lower_high",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "swing_5m_k3_lower_high",
"skip": "cap30",
"line": "ema50"
}
},
{
"id": "S3|E4|cap60|prev_day_extreme+0t|swing_4h_nearest_high",
"cell": "E4",
"spec": {
"type": "S3",
"stop": "prev_day_extreme+0t",
"target": "swing_4h_nearest_high",
"skip": "cap60",
"line": "vwap"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|donchian_100",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "donchian_100",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|cap15|swing_15m_k3_last+0t|swing_4h_nearest_high",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "swing_15m_k3_last+0t",
"target": "swing_4h_nearest_high",
"skip": "cap15",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|donchian_50",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "donchian_50",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E5|cap30|session_extreme+5t|swing_5m_k2_lower_high",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "swing_5m_k2_lower_high",
"skip": "cap30",
"line": "ema50"
}
},
{
"id": "S3|E3|atr1.5|round_50+0t|prev_day_close",
"cell": "E3",
"spec": {
"type": "S3",
"stop": "round_50+0t",
"target": "prev_day_close",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|opening_range_or30",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "opening_range_or30",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|vwap_p2sd",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "vwap_p2sd",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|prev_hour_extreme",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "prev_hour_extreme",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|opening_range_or15",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "opening_range_or15",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|cap20|session_extreme+5t|swing_5m_k2_lower_high",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "swing_5m_k2_lower_high",
"skip": "cap20",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|swing_15m_k3_nearest_high",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "swing_15m_k3_nearest_high",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+5t|sd_ext_2.25",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "sd_ext_2.25",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|R3",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "R3",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E1|cap60|prev_day_extreme+2t|swing_5m_k2_equal_highs",
"cell": "E1",
"spec": {
"type": "S3",
"stop": "prev_day_extreme+2t",
"target": "swing_5m_k2_equal_highs",
"skip": "cap60",
"line": "ema200"
}
},
{
"id": "S3|E5|cap30|session_extreme+5t|swing_3m_k3_lower_high",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "swing_3m_k3_lower_high",
"skip": "cap30",
"line": "ema50"
}
},
{
"id": "S3|E2|atr1.5|session_extreme+2t|swing_5m_k2_leg_high",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "session_extreme+2t",
"target": "swing_5m_k2_leg_high",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E1|atr1.5|session_extreme+0t|swing_5m_k2_lower_high",
"cell": "E1",
"spec": {
"type": "S3",
"stop": "session_extreme+0t",
"target": "swing_5m_k2_lower_high",
"skip": "atr1.5",
"line": "ema200"
}
},
{
"id": "S3|E1|cap15|session_extreme+5t|pivot_R1",
"cell": "E1",
"spec": {
"type": "S3",
"stop": "session_extreme+5t",
"target": "pivot_R1",
"skip": "cap15",
"line": "ema200"
}
},
{
"id": "S3|E4|atr1.5|swing_15m_k3_last+5t|swing_3m_k3_leg_high",
"cell": "E4",
"spec": {
"type": "S3",
"stop": "swing_15m_k3_last+5t",
"target": "swing_3m_k3_leg_high",
"skip": "atr1.5",
"line": "vwap"
}
},
{
"id": "S3|E5|atr1.5|swing_5m_k2_impulse_start+0t|prev_day_close",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "swing_5m_k2_impulse_start+0t",
"target": "prev_day_close",
"skip": "atr1.5",
"line": "ema50"
}
},
{
"id": "S3|E2|cap20|swing_15m_k3_last+5t|prev_day_extreme",
"cell": "E2",
"spec": {
"type": "S3",
"stop": "swing_15m_k3_last+5t",
"target": "prev_day_extreme",
"skip": "cap20",
"line": "ema200"
}
},
{
"id": "S3|E5|atr1.5|swing_5m_k3_higher+5t|prev_day_close",
"cell": "E5",
"spec": {
"type": "S3",
"stop": "swing_5m_k3_higher+5t",
"target": "prev_day_close",
"skip": "atr1.5",
"line": "ema50"
}
},
{
"id": "S3|E3|cap60|prev_day_extreme+0t|swing_15m_k2_equal_highs",
"cell": "E3",
"spec": {
"type": "S3",
"stop": "prev_day_extreme+0t",
"target": "swing_15m_k2_equal_highs",
"skip": "cap60",
"line": "ema200"
}
}
]
```

Protocol: HOLD (20250701-20260206) is simulated ONCE for exactly these 30 definitions (sequenced real list; 100-draw random-in-regime placebo and random-direction placebo with the same definitions re-derived at the random minute); X (20230401-20240131) once after. Looks logged in l2vast/ds3/out/zen/struct/looks.jsonl. No definition, rank or threshold changes after this hash.
