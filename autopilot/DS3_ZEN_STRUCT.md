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
