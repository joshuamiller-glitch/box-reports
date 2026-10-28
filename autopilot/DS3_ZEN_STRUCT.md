# DS3_ZEN_STRUCT - T-ZEN Addendum 6 (S1 stops x S2 targets, S3 grid, S4 structure trails, S5 scaling, S6 map) - agent D3ZST, 2026-10-28

Research only. PRE (20240201-20250630) is the only window read so far. Section order is fixed by the plan: S6 map (descriptive, all touches, no selection, nothing ranked) FIRST; the S3 prereg is hashed after this section was written (hash line in DECISIONS.md); then scoring.

## 1. S6 - the ladder of highs and lows as a map (descriptive, PRE, all touches of E1-E5)

Entry cells (plan section 1, fixed a priori): E1 = R1 + 1-min EMA200 tol 5 pt + hold candle; E2 = R1 + EMA200 tol 2; E3 = R8 + EMA200 tol 5; E4 = R1 + session VWAP (09:30 anchor) tol 5; E5 = R3 + 1-min EMA50 tol 5. Touch bar j (closed): long low_j <= line_j + tol and close_j > line_j (short mirror); market entry at the open of bar j+1; PRIMARY window 10:00-14:00 NY; flat 14:00. PRE touch counts: E1 8,019 | E2 5,446 | E3 3,522 | E4 7,354 | E5 13,793 (every qualifying bar; consecutive touches are NOT de-duplicated in the map; the pool is every R1/R3/R8 minute in the same window: 86,252 R1 minutes).
Counting rule of the map: for each touch, from the entry bar to 14:00 the 1-min path is searched for the first touch of the stop and of the target (same kernel as the grid: stop first on a tie, gap through the stop fills at the open, entry bar included). Pairs with target < 1 tick or stop > 60 pt are SKIPPED AND COUNTED (column skipped). P(neither) = reached neither before the 14:00 flat. "pool P(T)" = the same stop/target logic applied at every regime minute (the structural odds of a random minute, the comparator). BE win = cost-adjusted break-even win rate of the REALISED mean stop / mean target ($4.84 RT + the mapped Target correction of 2.48 pts, mean over PRE entries; stop-fill correction is clipped to 0 by the library). P(T)-BE > 0 means the odds alone exceed the cost-adjusted break-even for that mean stop/target.

**S6 reachability number (the one the addendum asks for).** Probability that price reaches the nearest 1-min swing high (strength 2) before the hold-candle low is broken, from the touch: E1 46.1%, E2 49.3%, E3 45.9%, E4 47.5%, E5 50.5% (random regime minute: 39.1%). So the nearest swing high IS reachable from an EMA200 / VWAP / EMA50 touch with odds close to a coin flip and 7-11 points above a random minute, but the distance is the point: the mean target is 6.5-9 pt against a mean stop of 7.3-9 pt (R:R about 1.0), whose cost-adjusted break-even is 58-68%, i.e. 11-17 points ABOVE the odds (column P(T)-BE negative in every cell for the 1-min swing targets). Farther structure (5-min swing high, 15-min, 1-h) has lower odds (35% / 32% / 26% on E1) but a larger payoff, the break-even falls faster than the odds (P(T)-BE becomes +0.03 to +0.10 for 5-min k3 / 15-min / 1-h swing highs), which is the shape the grid screen will test against the random-minute expectation: the odds above break-even for far targets are partly a property of the cost model (large mean target, low BE) and of drift, and the random-minute column (pool P(T)) shows part of it exists at any minute. The S6 map ranks nothing and selects nothing; the S3 prereg below does not use its P&L-like columns (net1 columns were produced in the CSV but are not shown and were not used to choose the prereg).

Stop-side facts that matter for the grid: hold-candle low median 5.8 pt (p90 17), prior candle 6.0, line-1-tick 5.4, 1-min last higher low 4.0, last swing low 12.5 (p90 41), 5-min swing low 27 (p90 75), session / OR / prior-day / overnight extremes are typically 50-180 pt away (59-89% of touches exceed the 60-pt nonsense limit and are skipped), regime-line (5-min EMA200) stop median 30 pt (25% > 60). zone_far (FVG / OB far edge) is NOT defined for E1-E5 (no zone in the entry definition): 3 of the 135 stop columns are all-NaN (skipped, counted).

S6.1 stop = hold-candle low/high (buffer 0), P(target first) at the PRE touches of each entry cell (cost for BE: $4.84 RT + mean mapped Target correction 2.48 pts on PRE entries)

**E1** (touches 8019)

| target | n valid | skipped | P(T first) | P(S first) | P(neither) | mean stop pt | mean tgt pt | BE win | P(T)-BE | pool P(T) |
|---|---|---|---|---|---|---|---|---|---|---|
| swing_1m_k2_nearest_high | 7830 | 189 | 0.461 | 0.535 | 0.003 | 7.9 | 8.0 | 0.606 | -0.144 | 0.391 |
| swing_1m_k3_nearest_high | 7862 | 157 | 0.448 | 0.548 | 0.003 | 7.9 | 8.7 | 0.575 | -0.127 | 0.373 |
| swing_3m_k2_nearest_high | 7875 | 144 | 0.411 | 0.583 | 0.006 | 7.9 | 11.5 | 0.482 | -0.070 | 0.330 |
| swing_5m_k3_nearest_high | 7867 | 152 | 0.352 | 0.636 | 0.012 | 7.9 | 20.3 | 0.317 | +0.035 | 0.288 |
| swing_15m_k2_nearest_high | 7808 | 211 | 0.325 | 0.655 | 0.020 | 7.9 | 25.4 | 0.265 | +0.060 | 0.266 |
| swing_1h_nearest_high | 7269 | 750 | 0.255 | 0.721 | 0.024 | 7.9 | 44.3 | 0.164 | +0.091 | 0.215 |
| session_extreme | 7876 | 143 | 0.082 | 0.857 | 0.060 | 7.9 | 73.5 | 0.104 | -0.021 | 0.169 |
| prev_hour_extreme | 7628 | 391 | 0.136 | 0.827 | 0.037 | 7.9 | 53.4 | 0.138 | -0.002 | 0.158 |
| vwap | 3158 | 4861 | 0.341 | 0.655 | 0.003 | 8.1 | 15.4 | 0.395 | -0.054 | 0.238 |
| ema20_5m | 3907 | 4112 | 0.369 | 0.626 | 0.006 | 6.9 | 10.4 | 0.483 | -0.114 | 0.260 |
| round_50 | 7876 | 143 | 0.251 | 0.728 | 0.021 | 7.9 | 24.5 | 0.273 | -0.022 | 0.230 |
| fvg4h_edge | 6836 | 1183 | 0.150 | 0.801 | 0.049 | 8.4 | 88.0 | 0.092 | +0.058 | 0.139 |
| R1 | 7876 | 143 | 0.415 | 0.579 | 0.006 | 7.9 | 7.9 | 0.611 | -0.195 | 0.390 |
| R2 | 7876 | 143 | 0.291 | 0.697 | 0.012 | 7.9 | 15.9 | 0.383 | -0.093 | 0.284 |
| fixed20 | 7876 | 143 | 0.232 | 0.753 | 0.015 | 7.9 | 20.0 | 0.321 | -0.089 | 0.220 |
| nearer2R_swing_1m_k2_nearest_high | 7876 | 143 | 0.479 | 0.519 | 0.003 | 7.9 | 5.9 | 0.722 | -0.244 | 0.407 |

**E2** (touches 5446)

| target | n valid | skipped | P(T first) | P(S first) | P(neither) | mean stop pt | mean tgt pt | BE win | P(T)-BE | pool P(T) |
|---|---|---|---|---|---|---|---|---|---|---|
| swing_1m_k2_nearest_high | 5336 | 110 | 0.493 | 0.503 | 0.003 | 9.1 | 8.5 | 0.618 | -0.124 | 0.391 |
| swing_1m_k3_nearest_high | 5353 | 93 | 0.480 | 0.517 | 0.004 | 9.1 | 9.3 | 0.588 | -0.108 | 0.373 |
| swing_3m_k2_nearest_high | 5361 | 85 | 0.442 | 0.553 | 0.005 | 9.1 | 12.0 | 0.502 | -0.060 | 0.330 |
| swing_5m_k3_nearest_high | 5355 | 91 | 0.377 | 0.611 | 0.012 | 9.1 | 21.1 | 0.337 | +0.041 | 0.288 |
| swing_15m_k2_nearest_high | 5313 | 133 | 0.353 | 0.626 | 0.022 | 9.1 | 26.3 | 0.283 | +0.069 | 0.266 |
| swing_1h_nearest_high | 4958 | 488 | 0.278 | 0.697 | 0.024 | 9.1 | 46.0 | 0.178 | +0.100 | 0.215 |
| session_extreme | 5362 | 84 | 0.093 | 0.844 | 0.063 | 9.1 | 77.8 | 0.111 | -0.018 | 0.169 |
| prev_hour_extreme | 5239 | 207 | 0.148 | 0.813 | 0.039 | 9.1 | 57.0 | 0.146 | +0.002 | 0.158 |
| vwap | 2360 | 3086 | 0.365 | 0.631 | 0.003 | 9.1 | 16.5 | 0.405 | -0.040 | 0.238 |
| ema20_5m | 2895 | 2551 | 0.397 | 0.597 | 0.006 | 7.9 | 10.9 | 0.496 | -0.099 | 0.260 |
| round_50 | 5362 | 84 | 0.280 | 0.700 | 0.020 | 9.1 | 24.5 | 0.301 | -0.020 | 0.230 |
| fvg4h_edge | 4677 | 769 | 0.168 | 0.781 | 0.050 | 9.7 | 90.5 | 0.101 | +0.067 | 0.139 |
| R1 | 5362 | 84 | 0.438 | 0.556 | 0.006 | 9.1 | 9.1 | 0.594 | -0.156 | 0.390 |
| R2 | 5362 | 84 | 0.303 | 0.684 | 0.012 | 9.1 | 18.3 | 0.376 | -0.073 | 0.284 |
| fixed20 | 5362 | 84 | 0.265 | 0.722 | 0.013 | 9.1 | 20.0 | 0.352 | -0.087 | 0.220 |
| nearer2R_swing_1m_k2_nearest_high | 5362 | 84 | 0.510 | 0.487 | 0.003 | 9.1 | 6.5 | 0.714 | -0.204 | 0.407 |

**E3** (touches 3522)

| target | n valid | skipped | P(T first) | P(S first) | P(neither) | mean stop pt | mean tgt pt | BE win | P(T)-BE | pool P(T) |
|---|---|---|---|---|---|---|---|---|---|---|
| swing_1m_k2_nearest_high | 3453 | 69 | 0.459 | 0.534 | 0.007 | 7.3 | 7.8 | 0.600 | -0.141 | 0.402 |
| swing_1m_k3_nearest_high | 3454 | 68 | 0.446 | 0.548 | 0.007 | 7.3 | 8.1 | 0.584 | -0.138 | 0.384 |
| swing_3m_k2_nearest_high | 3456 | 66 | 0.416 | 0.573 | 0.011 | 7.3 | 10.3 | 0.500 | -0.084 | 0.335 |
| swing_5m_k3_nearest_high | 3452 | 70 | 0.354 | 0.628 | 0.018 | 7.3 | 17.7 | 0.335 | +0.019 | 0.293 |
| swing_15m_k2_nearest_high | 3419 | 103 | 0.314 | 0.659 | 0.027 | 7.3 | 24.2 | 0.259 | +0.055 | 0.267 |
| swing_1h_nearest_high | 3074 | 448 | 0.248 | 0.719 | 0.033 | 7.4 | 48.4 | 0.143 | +0.105 | 0.211 |
| session_extreme | 3457 | 65 | 0.073 | 0.854 | 0.073 | 7.3 | 62.3 | 0.113 | -0.040 | 0.203 |
| prev_hour_extreme | 3345 | 177 | 0.116 | 0.829 | 0.055 | 7.3 | 48.3 | 0.141 | -0.025 | 0.189 |
| vwap | 19 | 3503 | 0.632 | 0.368 | 0.000 | 8.2 | 0.6 | 1.343 | -0.712 | 0.415 |
| ema20_5m | 2053 | 1469 | 0.356 | 0.634 | 0.011 | 6.2 | 10.7 | 0.449 | -0.094 | 0.299 |
| round_50 | 3457 | 65 | 0.242 | 0.727 | 0.032 | 7.3 | 23.7 | 0.266 | -0.024 | 0.232 |
| fvg4h_edge | 2915 | 607 | 0.129 | 0.802 | 0.069 | 7.8 | 90.1 | 0.084 | +0.045 | 0.139 |
| R1 | 3457 | 65 | 0.421 | 0.570 | 0.009 | 7.3 | 7.3 | 0.621 | -0.201 | 0.393 |
| R2 | 3457 | 65 | 0.288 | 0.695 | 0.018 | 7.3 | 14.7 | 0.388 | -0.100 | 0.285 |
| fixed20 | 3457 | 65 | 0.216 | 0.761 | 0.023 | 7.3 | 20.0 | 0.305 | -0.089 | 0.220 |
| nearer2R_swing_1m_k2_nearest_high | 3457 | 65 | 0.480 | 0.515 | 0.005 | 7.3 | 5.5 | 0.734 | -0.254 | 0.410 |

**E4** (touches 7354)

| target | n valid | skipped | P(T first) | P(S first) | P(neither) | mean stop pt | mean tgt pt | BE win | P(T)-BE | pool P(T) |
|---|---|---|---|---|---|---|---|---|---|---|
| swing_1m_k2_nearest_high | 7149 | 205 | 0.475 | 0.521 | 0.004 | 8.5 | 9.0 | 0.585 | -0.110 | 0.391 |
| swing_1m_k3_nearest_high | 7178 | 176 | 0.457 | 0.539 | 0.004 | 8.6 | 10.6 | 0.529 | -0.072 | 0.373 |
| swing_3m_k2_nearest_high | 7211 | 143 | 0.410 | 0.585 | 0.005 | 8.6 | 14.3 | 0.433 | -0.022 | 0.330 |
| swing_5m_k3_nearest_high | 7055 | 299 | 0.349 | 0.640 | 0.011 | 8.5 | 22.6 | 0.305 | +0.045 | 0.288 |
| swing_15m_k2_nearest_high | 6771 | 583 | 0.334 | 0.649 | 0.017 | 8.4 | 26.5 | 0.268 | +0.066 | 0.266 |
| swing_1h_nearest_high | 6457 | 897 | 0.265 | 0.712 | 0.022 | 8.6 | 43.4 | 0.178 | +0.087 | 0.215 |
| session_extreme | 7225 | 129 | 0.100 | 0.853 | 0.047 | 8.6 | 65.1 | 0.124 | -0.024 | 0.169 |
| prev_hour_extreme | 6808 | 546 | 0.168 | 0.804 | 0.028 | 8.6 | 47.1 | 0.166 | +0.002 | 0.158 |
| vwap | 64 | 7290 | 0.438 | 0.562 | 0.000 | 6.3 | 0.6 | 1.473 | -1.035 | 0.238 |
| ema20_5m | 2114 | 5240 | 0.361 | 0.625 | 0.014 | 6.8 | 11.9 | 0.432 | -0.071 | 0.260 |
| round_50 | 7225 | 129 | 0.271 | 0.712 | 0.017 | 8.6 | 24.4 | 0.289 | -0.019 | 0.230 |
| fvg4h_edge | 6405 | 949 | 0.155 | 0.800 | 0.045 | 9.0 | 91.3 | 0.094 | +0.061 | 0.139 |
| R1 | 7225 | 129 | 0.435 | 0.559 | 0.005 | 8.6 | 8.6 | 0.601 | -0.165 | 0.390 |
| R2 | 7225 | 129 | 0.298 | 0.690 | 0.012 | 8.6 | 17.2 | 0.379 | -0.081 | 0.284 |
| fixed20 | 7225 | 129 | 0.247 | 0.740 | 0.013 | 8.6 | 20.0 | 0.338 | -0.091 | 0.220 |
| nearer2R_swing_1m_k2_nearest_high | 7225 | 129 | 0.493 | 0.503 | 0.004 | 8.6 | 6.5 | 0.698 | -0.204 | 0.407 |

**E5** (touches 13793)

| target | n valid | skipped | P(T first) | P(S first) | P(neither) | mean stop pt | mean tgt pt | BE win | P(T)-BE | pool P(T) |
|---|---|---|---|---|---|---|---|---|---|---|
| swing_1m_k2_nearest_high | 13576 | 217 | 0.505 | 0.492 | 0.004 | 7.6 | 6.5 | 0.679 | -0.174 | 0.388 |
| swing_1m_k3_nearest_high | 13581 | 212 | 0.480 | 0.516 | 0.004 | 7.6 | 8.1 | 0.595 | -0.116 | 0.372 |
| swing_3m_k2_nearest_high | 13535 | 258 | 0.409 | 0.585 | 0.006 | 7.6 | 13.3 | 0.426 | -0.017 | 0.326 |
| swing_5m_k3_nearest_high | 12730 | 1063 | 0.337 | 0.653 | 0.010 | 7.6 | 20.0 | 0.312 | +0.025 | 0.282 |
| swing_15m_k2_nearest_high | 11412 | 2381 | 0.312 | 0.670 | 0.018 | 7.6 | 25.8 | 0.253 | +0.059 | 0.263 |
| swing_1h_nearest_high | 10847 | 2946 | 0.252 | 0.724 | 0.025 | 7.8 | 48.5 | 0.149 | +0.103 | 0.210 |
| session_extreme | 13597 | 196 | 0.140 | 0.824 | 0.036 | 7.7 | 47.2 | 0.151 | -0.011 | 0.183 |
| prev_hour_extreme | 11614 | 2179 | 0.208 | 0.774 | 0.018 | 7.6 | 34.2 | 0.199 | +0.008 | 0.166 |
| vwap | 1097 | 12696 | 0.456 | 0.542 | 0.002 | 7.8 | 7.9 | 0.606 | -0.150 | 0.260 |
| ema20_5m | 218 | 13575 | 0.596 | 0.399 | 0.005 | 6.0 | 2.0 | 1.121 | -0.525 | 0.269 |
| round_50 | 13597 | 196 | 0.245 | 0.732 | 0.023 | 7.7 | 25.4 | 0.258 | -0.013 | 0.229 |
| fvg4h_edge | 11762 | 2031 | 0.155 | 0.798 | 0.047 | 8.1 | 88.9 | 0.088 | +0.066 | 0.139 |
| R1 | 13597 | 196 | 0.433 | 0.562 | 0.005 | 7.7 | 7.7 | 0.615 | -0.182 | 0.388 |
| R2 | 13597 | 196 | 0.302 | 0.686 | 0.012 | 7.7 | 15.3 | 0.385 | -0.084 | 0.283 |
| fixed20 | 13597 | 196 | 0.237 | 0.745 | 0.017 | 7.7 | 20.0 | 0.314 | -0.076 | 0.218 |
| nearer2R_swing_1m_k2_nearest_high | 13597 | 196 | 0.516 | 0.481 | 0.003 | 7.7 | 5.0 | 0.775 | -0.259 | 0.403 |

S6.2 by entry window (stop = hold-candle, target = nearest 1-min swing high k2 | nearest 5-min swing high k3): P(T first) [pool P(T)] n

| cell | target | W10 | W11 | W12 | W13 |
|---|---|---|---|---|---|
| E1 | swing_1m_k2 | 0.501 [0.393] n=2041 | 0.442 [0.395] n=1754 | 0.435 [0.392] n=2154 | 0.466 [0.382] n=1881 |
| E1 | swing_5m_k3 | 0.432 [0.327] n=2041 | 0.346 [0.278] n=1769 | 0.308 [0.280] n=2168 | 0.321 [0.275] n=1889 |
| E2 | swing_1m_k2 | 0.537 [0.393] n=1516 | 0.485 [0.395] n=1198 | 0.458 [0.392] n=1409 | 0.489 [0.382] n=1213 |
| E2 | swing_5m_k3 | 0.466 [0.327] n=1516 | 0.373 [0.278] n=1206 | 0.318 [0.280] n=1414 | 0.340 [0.275] n=1219 |
| E3 | swing_1m_k2 | 0.613 [0.409] n=421 | 0.463 [0.408] n=596 | 0.428 [0.404] n=1118 | 0.436 [0.389] n=1318 |
| E3 | swing_5m_k3 | 0.559 [0.339] n=417 | 0.414 [0.281] n=597 | 0.324 [0.290] n=1119 | 0.287 [0.278] n=1319 |
| E4 | swing_1m_k2 | 0.507 [0.393] n=2462 | 0.479 [0.395] n=1886 | 0.453 [0.392] n=1527 | 0.432 [0.382] n=1274 |
| E4 | swing_5m_k3 | 0.398 [0.327] n=2299 | 0.339 [0.278] n=1895 | 0.329 [0.280] n=1552 | 0.303 [0.275] n=1309 |
| E5 | swing_1m_k2 | 0.493 [0.388] n=2867 | 0.510 [0.391] n=3375 | 0.517 [0.391] n=3633 | 0.497 [0.384] n=3701 |
| E5 | swing_5m_k3 | 0.361 [0.312] n=2576 | 0.323 [0.270] n=3155 | 0.338 [0.277] n=3441 | 0.330 [0.274] n=3558 |

S6.3 stop sources: distance below entry at the touch, E1 and E4 (median / p90 pts, median in ATR14 1-min units, share of touches with stop > 60 pt = skipped)

| stop source | E1 med / p90 | E1 ATR | E1 >60 | E4 med / p90 | E4 >60 |
|---|---|---|---|---|---|
| hold_candle | 5.8 / 17.0 | 0.55 | 0.00 | 6.2 / 18.5 | 0.00 |
| prev_candle | 6.0 / 21.0 | 0.62 | 0.01 | 6.8 / 23.5 | 0.01 |
| low2 | 7.5 / 22.0 | 0.75 | 0.01 | 8.5 / 24.8 | 0.01 |
| low3 | 9.0 / 25.5 | 0.88 | 0.01 | 10.0 / 29.0 | 0.01 |
| line | 5.4 / 13.9 | 0.53 | 0.00 | 5.7 / 14.8 | 0.00 |
| regime_line | 30.1 / 102.6 | 2.86 | 0.25 | 38.7 / 128.8 | 0.33 |
| zone_far | nan / nan | nan | nan | nan / nan | nan |
| swing_1m_k2_last | 12.5 / 40.8 | 1.29 | 0.04 | 14.5 / 46.2 | 0.05 |
| swing_1m_k2_higher | 4.0 / 29.0 | 0.44 | 0.02 | 6.5 / 35.0 | 0.03 |
| swing_1m_k2_impulse_start | 10.5 / 42.8 | 1.09 | 0.05 | 13.2 / 49.2 | 0.07 |
| swing_1m_k3_last | 14.0 / 46.2 | 1.47 | 0.06 | 16.8 / 52.0 | 0.07 |
| swing_1m_k3_higher | 4.8 / 31.5 | 0.51 | 0.02 | 7.8 / 38.0 | 0.03 |
| swing_1m_k3_impulse_start | 12.0 / 47.2 | 1.27 | 0.06 | 16.0 / 54.8 | 0.08 |
| swing_3m_k2_last | 20.2 / 62.0 | 2.08 | 0.11 | 26.0 / 75.0 | 0.16 |
| swing_3m_k2_higher | 5.8 / 39.5 | 0.56 | 0.04 | 13.0 / 52.2 | 0.07 |
| swing_3m_k2_impulse_start | 17.5 / 62.8 | 1.88 | 0.11 | 26.0 / 80.2 | 0.18 |
| swing_3m_k3_last | 24.5 / 70.5 | 2.52 | 0.13 | 31.8 / 86.2 | 0.21 |
| swing_3m_k3_higher | 9.2 / 44.2 | 0.96 | 0.05 | 18.2 / 61.2 | 0.10 |
| swing_3m_k3_impulse_start | 21.8 / 68.0 | 2.25 | 0.13 | 31.5 / 91.5 | 0.23 |
| swing_5m_k2_last | 27.2 / 75.5 | 2.75 | 0.16 | 35.2 / 96.4 | 0.25 |
| swing_5m_k2_higher | 10.8 / 47.2 | 1.09 | 0.05 | 20.5 / 68.5 | 0.13 |
| swing_5m_k2_impulse_start | 25.0 / 74.2 | 2.49 | 0.16 | 35.8 / 100.5 | 0.27 |
| swing_5m_k3_last | 32.0 / 87.5 | 3.20 | 0.22 | 41.8 / 109.0 | 0.32 |
| swing_5m_k3_higher | 14.5 / 53.8 | 1.50 | 0.08 | 25.5 / 81.2 | 0.19 |
| swing_5m_k3_impulse_start | 32.8 / 92.2 | 3.18 | 0.23 | 43.8 / 119.0 | 0.36 |
| swing_15m_k2_last | 52.0 / 136.0 | 5.02 | 0.43 | 61.8 / 152.8 | 0.51 |
| swing_15m_k2_higher | 34.8 / 97.2 | 3.37 | 0.25 | 46.0 / 125.9 | 0.37 |
| swing_15m_k2_impulse_start | 55.2 / 151.2 | 5.45 | 0.46 | 68.0 / 170.2 | 0.55 |
| swing_15m_k3_last | 64.5 / 160.2 | 6.15 | 0.53 | 76.5 / 172.2 | 0.60 |
| swing_15m_k3_higher | 42.8 / 122.6 | 4.15 | 0.34 | 53.0 / 146.7 | 0.44 |
| swing_15m_k3_impulse_start | 69.0 / 179.0 | 6.56 | 0.56 | 81.2 / 186.8 | 0.62 |
| pullback_extreme | 13.0 / 41.0 | 1.22 | 0.05 | 14.2 / 46.2 | 0.06 |
| session_extreme | 69.0 / 168.8 | 6.86 | 0.59 | 75.0 / 148.2 | 0.64 |
| opening_range_or15 | 49.5 / 141.5 | 4.57 | 0.41 | 57.2 / 134.8 | 0.47 |
| opening_range_or30 | 55.5 / 150.5 | 5.23 | 0.46 | 61.8 / 139.2 | 0.52 |
| prev_hour_extreme | 36.2 / 88.5 | 3.54 | 0.23 | 46.2 / 108.8 | 0.37 |
| overnight_extreme | 110.8 / 263.2 | 10.49 | 0.85 | 120.5 / 277.9 | 0.86 |
| prev_day_extreme | 183.0 / 445.2 | 17.26 | 0.89 | 184.8 / 440.2 | 0.90 |
| donchian_10 | 14.8 / 41.5 | 1.44 | 0.04 | 16.2 / 45.8 | 0.05 |
| donchian_20 | 20.0 / 54.0 | 1.93 | 0.08 | 22.5 / 60.7 | 0.10 |
| donchian_50 | 28.8 / 73.5 | 2.83 | 0.16 | 37.5 / 90.2 | 0.25 |
| round_50 | 26.0 / 45.0 | 2.19 | 0.00 | 26.5 / 45.0 | 0.00 |
| round_100 | 48.2 / 90.8 | 4.11 | 0.40 | 44.5 / 92.5 | 0.38 |
| nearest_prior_level | 19.1 / 80.8 | 1.95 | 0.15 | 18.0 / 78.2 | 0.14 |
| vwap_1sd | 31.3 / 83.8 | 3.11 | 0.20 | 35.7 / 68.3 | 0.16 |

S6.4 target sources: distance above entry at the touch (E1; availability = touches where the level exists above entry by >= 1 tick)

| target source | available | med / p90 pts | med ATR |
|---|---|---|---|
| swing_1m_k2_nearest_high | 0.99 | 4.5 / 19.5 | 0.44 |
| swing_1m_k2_lower_high | 0.64 | 12.5 / 39.2 | 1.22 |
| swing_1m_k2_leg_high | 0.83 | 14.5 / 43.8 | 1.42 |
| swing_1m_k2_equal_highs | 0.69 | 17.5 / 59.2 | 1.95 |
| swing_1m_k3_nearest_high | 1.00 | 5.0 / 20.8 | 0.49 |
| swing_1m_k3_lower_high | 0.66 | 14.8 / 43.2 | 1.45 |
| swing_1m_k3_leg_high | 0.84 | 17.5 / 51.2 | 1.72 |
| swing_1m_k3_equal_highs | 0.64 | 18.8 / 59.8 | 2.09 |
| swing_3m_k2_nearest_high | 1.00 | 6.2 / 27.8 | 0.60 |
| swing_3m_k2_lower_high | 0.68 | 18.8 / 53.8 | 1.80 |
| swing_3m_k2_leg_high | 0.88 | 27.0 / 79.8 | 2.58 |
| swing_3m_k2_equal_highs | 0.47 | 21.0 / 59.2 | 2.34 |
| swing_3m_k3_nearest_high | 1.00 | 7.0 / 36.0 | 0.72 |
| swing_3m_k3_lower_high | 0.69 | 21.5 / 58.0 | 2.02 |
| swing_3m_k3_leg_high | 0.91 | 32.0 / 87.8 | 3.10 |
| swing_3m_k3_equal_highs | 0.36 | 22.2 / 60.3 | 2.62 |
| swing_5m_k2_nearest_high | 1.00 | 7.8 / 39.5 | 0.78 |
| swing_5m_k2_lower_high | 0.66 | 23.5 / 59.2 | 2.24 |
| swing_5m_k2_leg_high | 0.93 | 35.2 / 90.8 | 3.37 |
| swing_5m_k2_equal_highs | 0.34 | 19.8 / 57.1 | 2.29 |
| swing_5m_k3_nearest_high | 1.00 | 9.2 / 50.5 | 0.94 |
| swing_5m_k3_lower_high | 0.62 | 24.5 / 63.2 | 2.49 |
| swing_5m_k3_leg_high | 0.95 | 40.2 / 100.5 | 3.95 |
| swing_5m_k3_equal_highs | 0.29 | 18.9 / 54.2 | 2.25 |
| swing_15m_k2_nearest_high | 0.99 | 12.0 / 66.2 | 1.09 |
| swing_15m_k2_lower_high | 0.46 | 24.9 / 67.0 | 2.57 |
| swing_15m_k2_leg_high | 0.95 | 49.2 / 120.5 | 4.80 |
| swing_15m_k2_equal_highs | 0.23 | 21.0 / 48.8 | 2.33 |
| swing_15m_k3_nearest_high | 0.98 | 12.5 / 71.5 | 1.11 |
| swing_15m_k3_lower_high | 0.34 | 25.8 / 70.9 | 2.60 |
| swing_15m_k3_leg_high | 0.90 | 52.0 / 125.7 | 5.34 |
| swing_15m_k3_equal_highs | 0.20 | 22.9 / 175.2 | 2.78 |
| session_extreme | 1.00 | 63.5 / 129.2 | 5.88 |
| opening_range_or15 | 0.67 | 37.0 / 107.2 | 3.33 |
| opening_range_or30 | 0.77 | 44.0 / 108.2 | 3.94 |
| prev_hour_extreme | 0.97 | 43.5 / 103.2 | 4.14 |
| overnight_extreme | 0.79 | 45.2 / 114.5 | 4.15 |
| prev_day_extreme | 0.69 | 81.0 / 236.0 | 7.72 |
| prev_day_close | 0.23 | 27.0 / 97.0 | 2.60 |
| donchian_20 | 1.00 | 19.5 / 58.0 | 1.91 |
| donchian_50 | 1.00 | 34.0 / 89.0 | 3.31 |
| donchian_100 | 1.00 | 49.2 / 112.0 | 4.57 |
| round_50 | 1.00 | 24.0 / 45.0 | 2.00 |
| round_100 | 1.00 | 51.5 / 90.0 | 4.32 |
| vwap | 0.40 | 12.0 / 33.3 | 0.98 |
| vwap_p1sd | 0.94 | 27.7 / 68.5 | 2.52 |
| vwap_p2sd | 0.99 | 58.0 / 127.0 | 5.34 |
| ema20_5m | 0.50 | 7.6 / 22.3 | 0.69 |
| fvg4h_edge | 0.87 | 48.5 / 200.8 | 4.37 |
| swing_1h_nearest_high | 0.92 | 20.2 / 90.2 | 1.92 |
| swing_4h_nearest_high | 0.92 | 49.8 / 242.8 | 4.73 |
| pivot_R1 | 0.77 | 85.9 / 208.7 | 8.30 |
| pivot_R2 | 0.93 | 178.8 / 364.9 | 17.26 |
| sd_ext_1.5 | 0.94 | 29.9 / 76.8 | 2.92 |
| sd_ext_2.25 | 0.98 | 50.7 / 121.3 | 4.85 |

Files: l2vast/ds3/out/zen/struct/s6_map_stopbuf0.csv (cell x window x 45 stops(buffer 0) x 64 targets: n, skipped, P(T), P(S), P(neither), mean stop / target, pool P(T)), s6_distances.csv (stop and target distances at the touch, pts and ATR), s6_md.txt; code l2vast/ds3/code/zen/struct/st_s6.py.

## 2. Counts and grid (from the prereg, plus what was actually scored)

- Prereg sha256 51e36df3b7f753f9e9d06b6ad56716ffbac2be5ea74b96aad297c80d65ec5e53 (hash line in DECISIONS.md written before scoring). Enumeration: 5 cells x 5 skip variants x 135 stops x 64 targets = 216,000 S3 + S4 120 + S5 80 + ladders 6 = **screened N upper bound 216,206**.
- Actually scored on PRE: S3 216,000 enumerated, 205,721 valid (>= 30 real and pool trades), 10,279 not eligible (4,800 zone_far all-NaN pairs + 5,479 with fewer than 30 trades, counted); 198,761 with >= 100 valid real PRE trades; S4/S5 206 of 206 scored (all n >= 100).
- Pair-level noise check: 4,079 of 205,721 valid pairs (2.0%) have effect CI lower bound > 0 (3,995 with n >= 100); the nominal one-sided false-positive rate is 2.5%. 458 pairs with n >= 100 have effect >= their own MDE80.
- **Reality check (White max-statistic, week-block bootstrap 1,000, N=216,206, 205,721 eligible pairs): p = 0.964 for the best pair over all pairs.** By cell: E1 0.627, E2 0.549, E3 0.734, E4 0.951, E5 0.861. No cell passes G8.
- Best-of-N is therefore the verdict that matters: the best of 205,721 pairs by effect (+9.8 pts, E2 prev-day-extreme stop / 5-min equal highs, n=102, CI lower +1.5 only because that pair's pool is -5.8) is what the max of 205k noisy estimates looks like (MDE80 for these pairs is 12-30 pts because wide stops and far targets give n of 100-200 trades with a 40-100 pt payoff).
- Holdout looks used: 1 for HOLD (30 definitions), 1 for X (same 30); logged in out/zen/struct/looks.jsonl and DECISIONS.md BEFORE the runs. S4/S5 cells were not in the top 30 (their effects are 0.1-0.3 pt against S3 effects of 3-10 pt) so they have PRE results only.
- Program N reference: 291,130 (plan).

## 3. S3 best pairs by effect (PRE grid, n >= 100 raw, unsequenced) and the plain fixed-bracket comparator

Fixed 15 pt stop / 20 pt target on the same entries, sequenced, full 100-draw placebo: E1 n=2465 mean -1.83 effect -0.32 rank 0.03 MDE80 0.77 win 0.413 vs BE 0.470; E2 n=2096 mean -1.71 effect -0.21 rank 0.16 MDE80 0.92 win 0.416 vs BE 0.470; E3 n=1117 mean -1.25 effect +0.13 rank 0.68 MDE80 1.07 win 0.429 vs BE 0.469; E4 n=2397 mean -1.52 effect -0.02 rank 0.46 MDE80 0.85 win 0.423 vs BE 0.470; E5 n=4018 mean -1.50 effect +0.01 rank 0.54 MDE80 0.64 win 0.424 vs BE 0.471. The fixed bracket is at or below zero vs random-in-regime and loses 1.25-1.83 pts/trade net (about $250-370 per 10-lot trade) in every cell. Same-bracket pool means: -1.0 to -1.2 pts for the plain structural hold-candle stop with fixed20 / 2R targets (grid, heat table).

### 4. Top-10 table (top 10 of the 30 by PRE grid effect vs random-in-regime, regardless of verdict)

PRE/HOLD/X = mean net1 pts/trade of the sequenced list [effect vs random-in-regime]; $ = pts x 200 (10 lots). trades/wk on PRE. fwd wks = weeks for 80% power at the PRE effect = 75 x (MDE80/effect)^2.

| # | pair (cell | skip | stop | target) | n PRE seq | PRE [eff] | MDE80 | win vs BE | trades/wk | HOLD n [eff, CI lo] | X n [eff] | PRE gates G1-G5 | failed | fwd wks |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | E2 cap60|prev_day_extreme+0t|swing_5m_k2_equal_highs | 31 | 0.35 [+5.13] | 8.5 | 0.677 vs 0.667 | 0.41 | 26 [-0.32, -8.5] | 81 [+3.00] | fPfPf | G1 G3 G5 G6 G8 (p=0.964) G9 G10 not run | 208 |
| 2 | E2 cap15|swing_15m_k3_last+0t|pivot_R1 | 50 | 0.96 [+0.68] | 7.7 | 0.220 vs 0.194 | 0.67 | 15 [+0.90, -11.2] | 71 [+2.86] | fffPf | G1 G2 G3 G5 G6 G8 (p=0.964) G9 G10 not run | 9612 |
| 3 | E2 cap20|session_extreme+5t|pivot_R1 | 36 | 1.87 [+1.21] | 14.8 | 0.194 vs 0.166 | 0.48 | 7 [-0.55, -12.6] | 38 [-1.55] | ffPPf | G1 G2 G5 G6 G7 G8 (p=0.964) G9 G10 not run | 11167 |
| 4 | E2 atr1.5|session_extreme+2t|session_extreme | 71 | 0.28 [+2.79] | 12.6 | 0.183 vs 0.180 | 0.95 | 20 [+14.10, -10.2] | 35 [-3.43] | fffPf | G1 G2 G3 G5 G6 G7 G8 (p=0.964) G9 G10 not run | 1532 |
| 5 | E5 atr1.5|prev_hour_extreme+2t|swing_4h_nearest_high | 73 | 3.33 [+3.70] | 10.1 | 0.329 vs 0.249 | 0.97 | 24 [-4.58, -10.8] | 47 [+0.77] | fPPPf | G1 G5 G6 G8 (p=0.964) G9 G10 not run | 562 |
| 6 | E5 cap30|session_extreme+5t|swing_5m_k3_lower_high | 27 | -0.15 [+3.99] | 12.9 | 0.370 vs 0.377 | 0.36 | 15 [+0.74, -23.0] | 34 [+1.27] | fPfff | G1 G3 G4 G5 G6 G8 (p=0.964) G9 G10 not run | 790 |
| 7 | E4 cap60|prev_day_extreme+0t|swing_4h_nearest_high | 151 | 0.95 [+2.81] | 8.3 | 0.325 vs 0.309 | 2.01 | 38 [+2.08, -9.3] | 91 [+0.79] | fPfPf | G1 G3 G5 G6 G8 (p=0.964) G9 G10 not run | 660 |
| 8 | E2 atr1.5|session_extreme+2t|donchian_100 | 71 | 0.01 [+2.27] | 12.3 | 0.183 vs 0.183 | 0.95 | 20 [+14.70, -9.5] | 35 [-3.47] | fffPf | G1 G2 G3 G5 G6 G7 G8 (p=0.964) G9 G10 not run | 2224 |
| 9 | E2 cap15|swing_15m_k3_last+0t|swing_4h_nearest_high | 74 | 1.21 [+2.03] | 6.4 | 0.216 vs 0.185 | 0.99 | 24 [-4.02, -11.5] | 78 [-1.17] | ffPPf | G1 G2 G5 G6 G7 G8 (p=0.964) G9 G10 not run | 749 |
| 10 | E2 atr1.5|session_extreme+2t|donchian_50 | 71 | -0.41 [+2.17] | 11.8 | 0.183 vs 0.187 | 0.95 | 20 [+14.91, -10.2] | 35 [-3.89] | fffff | G1 G2 G3 G4 G5 G6 G7 G8 (p=0.964) G9 G10 not run | 2221 |

### 5. By entry window, by year, long/short (top 10; PRE+HOLD sequenced list = WF)

Entry windows other than 10:00-14:00 (09:30-10:00, 14:00-15:30) are outside the screened PRIMARY window and were not scored (disclosed). Random-in-regime column = the pool mean over the same window is in the grid CSV; the placebo effect per row above is the pooled-window number.

| # | W10 | W11 | W12 | W13 | 2024 | 2025 | 2026 | long | short |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 6.5 (n=21) | -15.2 (n=8) | 5.7 (n=15) | -2.0 (n=13) | -0.5 (n=29) | 3.2 (n=28) | - | -7.0 (n=14) | 4.0 (n=43) |
| 2 | 4.4 (n=36) | -4.4 (n=11) | -1.0 (n=14) | 3.4 (n=4) | 2.9 (n=40) | -0.2 (n=25) | - | 3.3 (n=35) | -0.2 (n=30) |
| 3 | 0.1 (n=39) | 9.9 (n=3) | -6.1 (n=1) | - | 5.1 (n=29) | -7.9 (n=13) | -18.0 (n=1) | 15.7 (n=16) | -8.3 (n=27) |
| 4 | 2.2 (n=90) | 75.9 (n=1) | - | - | -2.9 (n=47) | 13.6 (n=40) | -32.9 (n=4) | 6.8 (n=40) | 0.1 (n=51) |
| 5 | -0.6 (n=28) | -2.4 (n=12) | 14.4 (n=14) | -0.7 (n=43) | -0.6 (n=51) | 4.3 (n=44) | -16.6 (n=2) | 0.6 (n=44) | 1.8 (n=53) |
| 6 | -2.9 (n=24) | -0.7 (n=16) | -0.8 (n=2) | - | 1.2 (n=23) | -5.7 (n=19) | - | -8.7 (n=14) | 1.4 (n=28) |
| 7 | 4.1 (n=77) | -3.6 (n=55) | 5.6 (n=25) | -1.0 (n=32) | 1.8 (n=92) | 0.6 (n=97) | - | -5.0 (n=52) | 3.5 (n=137) |
| 8 | 2.0 (n=90) | 75.9 (n=1) | - | - | -2.9 (n=47) | 13.1 (n=40) | -32.9 (n=4) | 6.3 (n=40) | 0.1 (n=51) |
| 9 | 2.8 (n=47) | -2.4 (n=17) | -2.6 (n=24) | 1.1 (n=10) | 2.2 (n=61) | -2.6 (n=36) | -0.5 (n=1) | -0.9 (n=56) | 2.2 (n=42) |
| 10 | 1.6 (n=90) | 79.2 (n=1) | - | - | -2.4 (n=47) | 11.8 (n=40) | -32.9 (n=4) | 5.1 (n=40) | 0.5 (n=51) |

### 6. Heat tables (PRE, all touches, skip variant cap60, buffer 0; cell E1 shown, all five cells x 5 skips x 135 stops in s3_pairs_PRE.parquet / heat_*.csv)

Rows = stop source, columns = target. Cell = mean net1 pts/trade of the real touches | effect vs pool | target-first rate minus break-even rate (BE of the realised mean stop/target, Target correction 2.48 pt). Positive win-BE means the target-first share exceeds break-even.

| stop \ target | sw1m_k2 | sw5m_k3 | sw15m_k2 | session_extreme | prev_hour_extreme | vwap | ema20_5m | R1 | R2 | fixed20 | fixed40 | nearer2R_sw1m_k2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| hold_candle | -1.89 / -0.12 / -0.14 | -1.83 / -0.37 / +0.03 | -1.36 / +0.00 / +0.06 | -0.68 / +0.20 / -0.02 | -0.86 / +0.08 / -0.00 | -1.40 / -0.10 / -0.05 | -1.71 / -0.16 / -0.11 | -1.47 / +0.22 / -0.20 | -1.02 / +0.14 / -0.09 | -1.01 / -0.13 / -0.09 | -0.82 / -0.25 / -0.05 | -1.94 / -0.08 / -0.24 |
| prev_candle | -1.88 / +0.03 / -0.14 | -1.96 / -0.33 / +0.02 | -1.51 / +0.02 / +0.05 | -0.93 / +0.13 / -0.03 | -0.93 / +0.18 / -0.01 | -1.42 / +0.13 / -0.05 | -1.93 / -0.01 / -0.13 | -1.55 / -0.03 / -0.14 | -1.14 / -0.11 / -0.08 | -1.11 / -0.10 / -0.10 | -0.94 / -0.37 / -0.06 | -1.92 / -0.06 / -0.20 |
| low3 | -1.87 / +0.03 / -0.13 | -2.09 / -0.37 / +0.02 | -1.61 / +0.05 / +0.05 | -1.18 / -0.08 / -0.04 | -1.12 / +0.12 / -0.02 | -1.56 / +0.03 / -0.06 | -1.85 / +0.03 / -0.12 | -1.53 / +0.00 / -0.13 | -1.13 / -0.04 / -0.07 | -1.18 / -0.08 / -0.11 | -1.02 / -0.34 / -0.07 | -1.89 / -0.03 / -0.18 |
| line | -1.93 / +0.30 / -0.13 | -1.77 / +0.09 / +0.05 | -1.42 / +0.69 / +0.07 | -0.91 / +0.86 / -0.01 | -0.96 / +1.24 / +0.01 | -1.25 / +0.76 / -0.03 | -1.65 / +0.26 / -0.09 | -1.61 / -0.39 / -0.22 | -1.15 / -0.83 / -0.11 | -1.00 / +0.76 / -0.08 | -0.97 / +0.47 / -0.05 | -1.95 / +0.15 / -0.25 |
| regime_line | -1.46 / +0.65 / -0.12 | -1.77 / +0.60 / -0.08 | -1.65 / +0.51 / -0.09 | 0.03 / +1.52 / -0.12 | -0.53 / +1.48 / -0.09 | -1.09 / +0.29 / -0.08 | -1.59 / +0.78 / -0.11 | -1.05 / +0.67 / -0.12 | -1.08 / +0.36 / -0.12 | -1.63 / +0.46 / -0.15 | -0.80 / +0.73 / -0.14 | -1.50 / +0.63 / -0.13 |
| swing_1m_k2_higher | -1.91 / +0.11 / -0.18 | -2.27 / -0.36 / -0.02 | -1.82 / +0.25 / +0.01 | -1.00 / +0.34 / -0.07 | -0.95 / +0.40 / -0.03 | -1.00 / +0.18 / -0.07 | -1.91 / +0.32 / -0.17 | -1.48 / -0.31 / -0.11 | -1.36 / -0.81 / -0.09 | -1.46 / -0.36 / -0.13 | -1.32 / -0.71 / -0.10 | -1.95 / -0.29 / -0.19 |
| swing_1m_k2_last | -1.91 / +0.04 / -0.14 | -2.48 / -0.55 / -0.01 | -2.07 / -0.01 / +0.01 | -1.09 / +0.23 / -0.08 | -1.31 / +0.19 / -0.04 | -1.57 / -0.03 / -0.07 | -2.21 / +0.04 / -0.14 | -1.70 / -0.50 / -0.11 | -1.62 / -1.00 / -0.10 | -1.66 / -0.33 / -0.13 | -1.38 / -0.63 / -0.11 | -1.98 / -0.23 / -0.15 |
| swing_5m_k2_higher | -2.54 / -0.02 / -0.16 | -2.53 / -0.19 / -0.04 | -2.38 / +0.08 / -0.03 | -1.20 / +0.74 / -0.09 | -2.02 / +0.47 / -0.05 | -1.44 / -0.13 / -0.09 | -2.37 / +0.29 / -0.19 | -1.96 / -0.44 / -0.12 | -1.91 / -1.10 / -0.11 | -1.90 / +0.13 / -0.15 | -1.80 / -0.39 / -0.13 | -2.54 / -0.20 / -0.17 |
| swing_5m_k2_last | -2.39 / -0.12 / -0.13 | -2.62 / -0.43 / -0.04 | -2.78 / -0.29 / -0.04 | -1.76 / -0.11 / -0.13 | -2.01 / +0.12 / -0.08 | -1.77 / -0.84 / -0.08 | -2.35 / -0.38 / -0.15 | -2.39 / -0.85 / -0.15 | -2.51 / -1.74 / -0.15 | -2.14 / -0.18 / -0.15 | -1.80 / -0.51 / -0.16 | -2.43 / -0.27 / -0.13 |
| swing_15m_k2_last | -2.31 / +0.15 / -0.10 | -3.71 / -0.09 / -0.09 | -3.64 / -0.72 / -0.06 | -4.17 / -1.58 / -0.17 | -3.67 / -0.47 / -0.13 | -2.20 / -0.25 / -0.06 | -2.66 / +0.66 / -0.12 | -4.48 / -1.47 / -0.18 | -5.28 / -2.05 / -0.20 | -3.89 / -1.23 / -0.18 | -4.21 / -1.47 / -0.22 | -2.38 / +0.20 / -0.10 |
| pullback_extreme | -1.98 / -0.07 / -0.14 | -2.51 / -0.67 / -0.01 | -2.02 / -0.06 / +0.02 | -1.38 / -0.17 / -0.07 | -1.42 / -0.05 / -0.04 | -1.71 / -0.14 / -0.07 | -1.91 / +0.08 / -0.13 | -1.91 / -0.51 / -0.12 | -1.57 / -0.66 / -0.09 | -1.55 / -0.27 / -0.13 | -1.40 / -0.59 / -0.10 | -2.01 / -0.19 / -0.17 |
| session_extreme | -2.27 / +0.03 / -0.08 | -3.96 / -0.42 / -0.06 | -4.25 / -1.31 / -0.07 | -5.66 / -2.64 / -0.17 | -4.82 / -1.70 / -0.11 | -2.03 / -0.13 / -0.05 | -3.27 / -0.36 / -0.10 | -6.02 / -2.52 / -0.21 | -7.09 / -2.74 / -0.21 | -4.84 / -2.17 / -0.18 | -5.09 / -2.35 / -0.21 | -2.35 / +0.12 / -0.08 |
| prev_hour_extreme | -2.41 / +0.11 / -0.11 | -3.18 / -0.19 / -0.05 | -3.44 / -0.27 / -0.03 | -2.54 / -0.45 / -0.15 | -1.99 / +0.23 / -0.10 | -1.63 / +0.31 / -0.07 | -2.51 / +0.29 / -0.13 | -3.13 / -0.55 / -0.16 | -3.76 / -1.56 / -0.18 | -2.69 / -0.23 / -0.17 | -2.65 / -0.24 / -0.19 | -2.45 / +0.12 / -0.12 |
| donchian_20 | -2.06 / -0.05 / -0.12 | -2.37 / -0.46 / -0.01 | -2.21 / +0.10 / +0.01 | -0.94 / +0.44 / -0.09 | -1.19 / +0.41 / -0.05 | -1.46 / +0.07 / -0.06 | -1.83 / +0.25 / -0.12 | -1.87 / -0.55 / -0.11 | -1.42 / -0.79 / -0.11 | -1.74 / -0.19 / -0.14 | -1.44 / -0.40 / -0.12 | -2.09 / -0.19 / -0.14 |
| round_50 | -1.86 / +0.37 / -0.12 | -2.29 / -0.35 / -0.03 | -1.65 / +0.33 / -0.01 | -1.62 / -0.24 / -0.10 | -1.21 / +0.33 / -0.07 | -0.92 / +0.45 / -0.05 | -1.83 / +0.22 / -0.11 | -1.67 / -0.22 / -0.14 | -1.64 / -0.89 / -0.14 | -1.78 / -0.25 / -0.16 | -1.67 / -0.61 / -0.15 | -1.86 / +0.21 / -0.13 |
| nearest_prior_level | -2.10 / +0.05 / -0.17 | -2.08 / +0.20 / -0.04 | -2.24 / +0.47 / -0.05 | -0.96 / +1.17 / -0.10 | -1.38 / +0.85 / -0.07 | -1.39 / +0.65 / -0.11 | -2.16 / +0.39 / -0.17 | -1.75 / +0.22 / -0.15 | -2.15 / -0.21 / -0.13 | -1.43 / +0.41 / -0.16 | -1.18 / +0.52 / -0.14 | -2.16 / -0.07 / -0.19 |
| vwap_1sd | -2.16 / +0.15 / -0.11 | -1.69 / -0.25 / -0.04 | -2.01 / -0.12 / -0.03 | -0.79 / +0.55 / -0.12 | -0.97 / +0.28 / -0.08 | -1.26 / +0.52 / -0.07 | -1.75 / +0.97 / -0.13 | -2.40 / +0.10 / -0.14 | -1.44 / +0.19 / -0.13 | -2.19 / +0.21 / -0.16 | -1.83 / +0.75 / -0.16 | -2.23 / +0.07 / -0.11 |

(* = n < 100: a count, not a verdict.) Full per-cell heat CSVs: out/zen/struct/heat_E{1..5}_cap60_{pts,effect,n}.csv.

### 6b. S4 trails and S5 scaling (PRE; base stop = hold-candle +2 ticks, entries with stop > 20 pt skipped; effect vs the pool running the same rule at every regime minute; paired = rule minus the plain 15/20 bracket and minus the same stop with a 2R target on identical entries)

| cell | rule | n | mean net1 | pool | effect [CI lo] | MDE80 | paired vs 15/20 [CI lo] (MDE) | paired vs 2R [CI lo] |
|---|---|---|---|---|---|---|---|---|
| E2 | S5 f0.50 t2=prev_day_extreme noBE | 3155 | -0.90 | -1.20 | +0.30 [-0.34] | 0.94 | +0.38 [-0.71] (1.45) | -0.09 [-0.64] |
| E5 | LADDER25/25/50 setB | 10559 | -1.03 | -1.29 | +0.27 [+0.12] | 0.20 | +0.48 [-0.15] (0.91) | -0.09 [-0.28] |
| E5 | S5 f0.50 t2=2R BE | 10559 | -1.44 | -1.70 | +0.26 [+0.14] | 0.17 | +0.07 [-0.58] (0.94) | -0.50 [-0.74] |
| E5 | S4 rule12 noscale | 12922 | -0.45 | -0.70 | +0.25 [-0.05] | 0.45 | +1.24 [+0.63] (0.90) | +0.57 [+0.20] |
| E5 | S5 f0.75 t2=2R BE | 10559 | -1.73 | -1.97 | +0.24 [+0.13] | 0.16 | -0.22 [-0.87] (0.97) | -0.79 [-1.05] |
| E5 | S5 f0.50 t2=2R noBE | 10559 | -1.55 | -1.79 | +0.24 [+0.10] | 0.20 | -0.05 [-0.64] (0.87) | -0.61 [-0.76] |
| E5 | S5 f0.75 t2=2R noBE | 10559 | -1.78 | -2.01 | +0.23 [+0.12] | 0.17 | -0.28 [-0.91] (0.93) | -0.85 [-1.07] |
| E1 | S5 f0.50 t2=prev_day_extreme noBE | 4831 | -0.99 | -1.20 | +0.22 [-0.31] | 0.79 | +0.38 [-0.61] (1.35) | -0.06 [-0.51] |
| E3 | S5 f0.50 t2=2R BE | 2382 | -1.47 | -1.68 | +0.21 [-0.14] | 0.49 | +0.24 [-0.79] (1.54) | -0.27 [-0.65] |
| E3 | S5 f0.75 t2=2R BE | 2382 | -1.75 | -1.95 | +0.20 [-0.14] | 0.48 | -0.04 [-1.10] (1.57) | -0.55 [-0.98] |

Mean effect over the five cells by rule: every S4 trail rule averages -0.1 to -0.8 pt vs the random-regime pool (worst: no trail / BE after scale control -0.76, 1-min higher low trails -0.4 to -0.5, best: previous-candle low after +10/+15 pt and EMA20 exit -0.1); S5 scaling averages -0.23 to +0.18 pt, positive only with the 2R second target (+0.11 to +0.18) and ladder set B (+0.17); first-scale versions are slightly better than no-scale for the trails. No S4/S5 cell has positive mean net (best -0.45 pt/trade, E5 EMA20 exit after +1R, no scale). Largest positive effects: E5 ladder 25/25/50 with 2R/3R (+0.27 [0.12], MDE80 0.20, net -1.03 pt/trade) and E5 50% at structure + 2R (+0.26 [0.14], net -1.44). They beat the pool by about 0.25 pt and still lose after costs. E5 EMA20-exit-after-+1R without scale beats the plain 15/20 bracket paired by +1.24 pt [0.63] (MDE80 0.90) and the 2R target by +0.57 [0.20], but only because the bracket comparators lose 1.7 pt; its own effect vs random is +0.25 [-0.05], net -0.45, not tested on HOLD (not in the top 30). BE after the first scale (the S5 control pair) makes no systematic difference (2R: +0.02 to +0.04 pt in favour of BE) - the dead-BE finding stands at the 15-pt-class stop. Ladders ran on E5, E2, E1 (best S5 effect).

## 7. Realised stop and target distributions and R:R (top 10 on PRE, sequenced)

| # | stop med / p90 pts | realised mean R:R (mean target dist / mean stop) | win | BE win |
|---|---|---|---|---|
| 1 | 51.5 / 59.2 | 0.3 | 0.677 | 0.667 |
| 2 | 7.6 / 14.2 | 10.3 | 0.220 | 0.194 |
| 3 | 12.9 / 18.8 | 7.3 | 0.194 | 0.166 |
| 4 | 16.8 / 35.8 | 4.9 | 0.183 | 0.180 |
| 5 | 10.5 / 24.7 | 6.8 | 0.329 | 0.249 |
| 6 | 26.2 / 29.5 | 0.4 | 0.370 | 0.377 |
| 7 | 23.8 / 52.8 | 4.9 | 0.325 | 0.309 |
| 8 | 16.8 / 35.8 | 5.1 | 0.183 | 0.183 |
| 9 | 8.2 / 14.2 | 10.9 | 0.216 | 0.185 |
| 10 | 16.8 / 35.8 | 4.7 | 0.183 | 0.187 |

Stops at the touch (S6.3): hold-candle 5.8 pt median (p90 17), line 5.4, last 1-min higher low 4.0, swing lows 12-32 pt, session / OR / prior-day extremes 50-180 pt. The top pairs are wide-stop / far-target structures (stop 8-50 pt, R:R of 3-9), win rates of 18-37% against break-evens of 17-31%: payoff shape, not edge - the random-regime pool with the same logic wins nearly as often.

## 8. Gate outcome for the top 30 (G10 not run by this agent)

PRE: G1 passes 2 of 30, G2 8, G3 7, G4 18, G5 0 (no top-30 pair has n >= 100 sequenced trades and effect >= MDE80). Only #26 (E4, stop 15-min last swing low +5t, target 3-min leg high, 1.5 ATR cap) passes G1-G4 on PRE (eff +5.03, CI [0.43, 10.0], n=90, MDE80 6.7: inside MDE). **HOLD: G6 passes for 0 of 30** (HOLD effect > 0 for 19 of 30, mean +4.1, but no CI lower bound above 0, largest HOLD n is 73; #26 HOLD effect -1.53). X: effect >= 0 for 13 of 30 (G7). G8 fails for all (p=0.964). G9 passes for none. Label: none (LEAD requires G1-G7; there is no LEAD, no CANDIDATE, no CONFIRMED). The HOLD effects of +12 to +17 for several session-extreme-stop pairs are 20 trades, all the same handful of trades in one regime (the 8 identical-n rows), CI lower about -10.

## 9. Deviations and disclosures

- BUG found and fixed by me before any look (my own wrapper, not the shared lib): in `st_common.run_grid` the ATR-cap flag was tested as `is None`, so all five skip variants had the 1.5 x ATR cap applied on the first S3 run (log s3_run_BUGGY_atrcap_all.log; best-of-N p was 0.817 then). Detected by the sim_spec vs grid identity test (12/40 matched), fixed, S3 rerun in full (identity now 40/40: n and mean net1 equal between `Z.simulate` and `grid_eval` for 40 random pairs across all skip variants). The prereg hash predates both runs; no cell definition changed. Reported numbers are from the corrected run.
- Coordinator warning (fill_mode=1 grid bug in zen_struct._grid): STRUCT uses market entries only (fill_mode=0), never fill_mode=1. Spot identity check against `Z.simulate()` done as above (40/40), and all 30 top cells and S4/S5 are simulated with Z.simulate directly. Not affected.
- Screen grid is unsequenced (every touch); the top 30 are sequenced (one open trade) and have fewer trades (26-151), which is why G5 fails everywhere. The ranking used the unsequenced effect as preregistered; sequenced effects differ (e.g. #1: +9.8 grid, +5.1 sequenced).
- Heat table win rate = target-first share (a time-flat exit with positive net is not a win); break-even uses the PRE mean mapped Target correction 2.48 pt (target fills are penalised heavily in 2025 by the P9 map: -4.2 pt; this lowers every target-based result, and the pool/random-regime comparator is subject to the same correction).
- The 'line' stop source at a random minute is often far from price (skipped or wide), so its pool is a different (closer-to-line) subset; effects of line-based stops vs the pool are therefore not comparable to candle stops (visible in the heat table, e.g. line row effects +0.3 to +1.2).
- zone_far undefined for E1-E5: 4,800 pairs skipped, counted. Entry windows 09:30-10:00 and 14:00-15:30 and the 15:55 flat were not screened (prereg). Direct 1-s/L2 replay (G10) not run: no cell can reach CANDIDATE here. Mapped basis is 0.05-0.13 pt/trade more conservative than the 1-s path on tight stops.
- S4/S5 were not holdout-tested (not in the top 30); S4 'higher low' trails use the confirmed swing as-of the close and are accepted only if below the close; 5-min candle low trail is a stop-order ratchet, not the 5-min-close exit of Addendum 1 Z2c. Ladder BE=yes (prereg silent). 
- Leak tests: st_tests.py 17/17 (touch masks of E1-E5 and 12 trail arrays unchanged when bars after 20250102 are deleted); zen_lib_test 63/63 covers the swing ladders.
- Selection: top 30 chosen by PRE effect only, one pair per (cell, stop source, target), best buffer x skip variant per key.

## 10. Files

Code l2vast/ds3/code/zen/struct/{st_common,st_specs,st_trails,st_tests,st_s6,st_s6_md,st_s3,st_s45,st_top,st_prehold,st_hold,st_report,st_md2}.py. Output l2vast/ds3/out/zen/struct/ (s6_*.csv, s3_pairs_PRE.parquet, s3_grids_PRE.pkl, s45_PRE.pkl, top30_PRE.pkl, hold_x_results.pkl, final_top30.pkl, heat_*.csv, looks.jsonl, logs). Prereg l2vast/ds3/prereg/ZEN_STRUCT_S3_prereg.md (+ .sha256, cells.csv.gz). Pre-holdout text autopilot/DS3_ZEN_STRUCT_PREHOLD.md.

## 11. Verdict

S6: the nearest 1-min swing high is reached before the hold-candle low breaks in 46-51% of touches (random minute 39%), but the target is about as far as the stop (R:R about 1.0) and the cost-adjusted break-even is 58-68%, so near structure is reachable and not payable; far structure (5-min, 15-min, 1-h swing highs) pays but its odds are mostly shared with a random minute. S3: of 205,721 eligible stop x target pairs the best-of-N reality-check p is 0.964 (4,079 pairs have CI lower > 0 against about 5,100 expected from noise at 2.5%); the top 30 fail the holdout (G6 0 of 30). The plain 15/20 bracket is at zero vs random-in-regime and nets -1.5 pt/trade; structural brackets reshape the payoff (win rate 18-37% against break-even 17-31%) without changing the mean vs a random minute. S4/S5: the best structural management effects are +0.25 pt vs random minutes (MDE80 0.2) with net -1.0 to -1.4 pt/trade; nothing is positive after costs.

no structural pair beats the fixed bracket

DONE STRUCT
