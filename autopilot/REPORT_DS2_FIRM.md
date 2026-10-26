# REPORT DS2-FIRM v2 (trackFIRM, 2026-10-22) - vol-normalized pair; research only, nothing live

Prereg: l2vast/PREREG_DS2_FIRM_V2.md (+ADDENDA A1 vol unit, A2 coarse subset); sha256 in autopilot/DECISIONS.md. Code: l2vast/pairP2/firm/. All numbers are weekly at 14/14 scale ($/wk), fees $4.84/contract RT (FEES.md) for every cell including the restated benchmark. IS = 2023-02-10..2024-01-31 (52 wk), WF = 12/3/3 OOS 2024-02.. (142 wk), L8W = 2026-W35..W42 (8 wk). Benchmark = corrected P9 table, windows 18:00-18:05 + 15:00-16:54, week floor 8R, tick(1-s) clock give-back 2R/keep 50%: re-run exactly in firmlib (ties to ds2lib at $4.36: WF 24,848/104,185/399,445/-137,064).

**What is exact and what is approximate.** EXACT: every bracket cell regenerates the pair's trades on the 1-second tape (stop/target resolved per second, per-book busy streams, windows, per-book/day/week locks on the 1-s tick-proxy clock); the 60-pt regeneration reproduces ROWS_bench3 row for row. APPROXIMATE: the P9 execution layer (S14x1 slice entries, XJ stop-join, 20-pt catastrophe: fill-by-fill L2 replay) for non-60 brackets is mapped by resampling replay-measured per-trade deltas (pts_P9 - natural pts) by exit type x year x bracket bin. Validation against DIRECT L2 replay (exec_engine_l2 on raw mbp-10, correct exit-arm mapping, replay4-style): 8 months of the firm cell (2023-06, 2023-11, 2024-06, 2024-10, 2025-03, 2025-08, 2026-02, 2026-09; 2,626 trades) + fixed-40 and base-60 in 2024-06 (base-60 reproduces the stored P9 S14x1/EM results bit for bit). Daily-P&L correlation replay vs mapping 0.989; mean abs monthly error 0.25 pts/trade (about $70/trade, +-$2.5k/wk) with the v2 mapping (0.48 with the first mapping; the v2 pools were fitted on those same months, so this is in-sample; a ~$3-5k/wk error band applies to every non-60 cell and means differences below that are not resolvable). Only the firm cell was replayed directly (8 of 43 months); full-period direct replay of finalists was NOT done (about 19 core-hours per cell).

## THE ONE NUMBER: weekly SD at EQUAL weekly mean (then maxDD, then worst week)

Method: each cell's daily P&L is scaled by m = benchmark WF weekly mean (25.0k) / cell WF weekly mean (linear scale = lots scaled; ignores that locks and size-cost are nonlinear in size, labelled SCALED); SD, maxDD and worst week are reported at that m for WF and for L8W (same m). Unscaled numbers are in the first and fourth columns. Cells whose WF mean is <= 0 are excluded. The ranking is selection-contaminated: the 'best' rows are picked from ~4,700 cells and must be read with the null ranks in the next section, not as findings.

Benchmark (corrected P9, 14/14): WF 25.0k / SD 104.5k / maxDD 401.3k / worst -137.1k; L8W 34.2k / SD 109.4k / maxDD 267.1k / worst -98.9k; IS 13.7k / SD 95.9k / maxDD 407.3k.

| cell | WF unscaled mean / SD / maxDD / worst wk | **WF at EQUAL mean (SD / maxDD / worst)** | L8W unscaled | L8W at the same scale m | avg/max lots | m |
|---|---|---|---|---|---|---|
| BENCHMARK 14/14 60-pt | 25.0k / 104.5k / 401.3k / -137.1k | **104.5k / 401.3k / -137.1k** | 34.2k / 109.4k / 267.1k / -98.9k | 109.4k / 267.1k / -98.9k | 14/14 | 1.00 |
| FIRM CELL (a priori): ridge/2h/k1.0/clamp, R$16.8k, cap 28, size-cost on | 5.5k / 102.1k / 852.9k / -137.1k | **459.6k / 3838.8k / -617.2k** | 18.6k / 103.4k / 256.0k / -134.8k | 465.2k / 1152.0k / -606.6k | 19/28 | 4.50 |
| firm cell, size-dependent cost OFF | 12.1k / 101.7k / 669.4k / -139.8k | **209.9k / 1380.9k / -288.4k** | 18.9k / 103.1k / 258.2k / -134.7k | 212.7k / 532.6k / -278.0k | 19/28 | 2.06 |
| firm cell, soft cap 14 lots | 20.6k / 101.6k / 622.2k / -145.0k | **123.2k / 754.4k / -175.8k** | 47.7k / 104.3k / 254.1k / -135.6k | 126.5k / 308.1k / -164.4k | 13/14 | 1.21 |
| firm bracket, fixed 14 lots | 19.7k / 111.4k / 669.9k / -141.4k | **141.4k / 849.9k / -179.4k** | 40.3k / 110.5k / 288.4k / -135.0k | 140.2k / 365.9k / -171.3k | 14/14 | 1.27 |
| ENSEMBLE (5.2): 20 nearest cells around the live params, fixed 60 pt, 14/14-equiv, no credit for fractional lots | 35.9k / 104.4k / 350.9k / -138.1k | **72.6k / 244.0k / -96.0k** | 43.5k / 99.2k / 289.7k / -95.5k | 69.0k / 201.5k / -66.4k | 1/1 | 0.70 |
| live single cell re-run in the 5.2 harness | 25.0k / 104.5k / 401.3k / -137.1k | **104.5k / 401.3k / -137.1k** | 34.2k / 109.4k / 267.1k / -98.9k | 109.4k / 267.1k / -98.9k | 14/14 | 1.00 |
| 5.3 stagger (firm bracket) | 17.3k / 102.5k / 692.5k / -138.3k | **147.8k / 998.7k / -199.4k** | 39.6k / 97.7k / 258.7k / -135.2k | 140.9k / 373.0k / -194.9k | 10/14 | 1.44 |
| 5.3 stagger (fixed 60) | 32.9k / 104.6k / 425.4k / -137.2k | **79.4k / 323.0k / -104.1k** | 22.5k / 115.8k / 395.6k / -134.6k | 87.9k / 300.3k / -102.2k | 7/7 | 0.76 |
| SIZE-ONLY control: fixed 60 pt, R$10k = 8 lots | 28.4k / 86.3k / 375.6k / -136.8k | **75.8k / 329.9k / -120.1k** | 42.0k / 111.7k / 274.6k / -122.5k | 98.1k / 241.1k / -107.6k | 8/8 | 0.88 |
| SIZE-ONLY control: fixed 60 pt, R$12k = 10 lots | 25.3k / 103.1k / 381.7k / -148.6k | **102.0k / 377.5k / -147.0k** | 34.4k / 100.7k / 259.4k / -92.0k | 99.6k / 256.5k / -91.0k | 10/10 | 0.99 |
| SIZE-ONLY control: fixed 60 pt, R$14k = 12 lots | 26.5k / 109.1k / 372.7k / -138.4k | **102.7k / 350.6k / -130.2k** | 39.3k / 82.9k / 204.6k / -95.8k | 78.0k / 192.5k / -90.2k | 12/12 | 0.94 |
| SELECTED best (14 lots): HAR_SESS_k0.6_cl_r1.0 | 40.0k / 114.7k / 567.4k / -139.6k | **71.6k / 354.1k / -87.1k** | 16.6k / 128.2k / 437.3k / -136.4k | 80.0k / 272.9k / -85.1k | 14/14 | 0.62 |
| SELECTED best (14 lots): HAR_SESS_k0.6_un_r1.0 | 38.0k / 115.3k / 665.4k / -139.6k | **75.8k / 437.2k / -91.8k** | 16.7k / 128.2k / 437.3k / -136.4k | 84.2k / 287.4k / -89.6k | 14/14 | 0.66 |
| SELECTED best (14 lots): GARCH_SESS_k0.6_un_r1.0 | 34.0k / 112.5k / 659.8k / -149.7k | **82.7k / 485.2k / -110.1k** | 55.6k / 113.8k / 261.9k / -135.5k | 83.7k / 192.5k / -99.6k | 14/14 | 0.74 |
| SELECTED best (14 lots): RIDGE_T2H_k0.8_cl_r1.25 | 30.4k / 104.7k / 480.6k / -139.2k | **86.1k / 395.1k / -114.4k** | 43.9k / 99.8k / 237.7k / -137.7k | 82.0k / 195.4k / -113.2k | 14/14 | 0.82 |
| SELECTED best (14 lots): GARCH_SESS_k0.6_cl_r1.0 | 32.5k / 112.1k / 674.0k / -149.7k | **86.1k / 517.6k / -115.0k** | 55.2k / 113.3k / 261.9k / -135.5k | 87.0k / 201.1k / -104.0k | 14/14 | 0.77 |
| SELECTED best (R$ sized): ATR20_T2H_k1.0_un_r1.0 R10000c14 | 35.1k / 86.4k / 388.5k / -139.0k | **61.5k / 276.6k / -98.9k** | 54.0k / 105.5k / 255.9k / -108.5k | 75.1k / 182.2k / -77.2k | 11/14 | 0.71 |
| SELECTED best (R$ sized): ATR20_T2H_k1.0_un_r1.0 R12000c14 | 35.9k / 93.2k / 410.7k / -137.6k | **64.8k / 285.6k / -95.7k** | 57.3k / 104.4k / 239.9k / -110.0k | 72.6k / 166.8k / -76.5k | 12/14 | 0.70 |
| SELECTED best (R$ sized): ATR20_T2H_k1.0_un_r1.0 R10000c28 | 34.6k / 89.9k / 339.2k / -138.7k | **64.9k / 244.8k / -100.1k** | 55.2k / 102.4k / 245.8k / -97.7k | 73.9k / 177.4k / -70.5k | 12/28 | 0.72 |
| SELECTED best (R$ sized): ATR20_T2H_k1.0_cl_r1.0 R10000c14 | 32.7k / 87.2k / 411.3k / -138.9k | **66.6k / 314.0k / -106.1k** | 54.0k / 105.5k / 255.9k / -108.5k | 80.5k / 195.4k / -82.8k | 10/14 | 0.76 |
| SELECTED best (R$ sized): ATR20_T2H_k1.0_un_r1.0 R14000c14 | 37.0k / 98.8k / 403.6k / -139.6k | **66.8k / 272.8k / -94.4k** | 57.1k / 110.4k / 256.6k / -105.0k | 74.6k / 173.4k / -70.9k | 13/14 | 0.68 |
| SELECTED best (R$ sized): ATR20_T4H_k0.6_un_r1.0 R10000c14 | 34.3k / 93.6k / 485.4k / -137.5k | **68.0k / 352.9k / -100.0k** | 76.3k / 122.1k / 233.0k / -86.0k | 88.8k / 169.4k / -62.5k | 11/14 | 0.73 |
| SELECTED best (R$ sized): HAR_SESS_k0.6_cl_r1.0 R16800c14 | 38.4k / 104.6k / 530.3k / -138.9k | **68.1k / 345.2k / -90.4k** | 26.4k / 115.5k / 371.5k / -135.1k | 75.2k / 241.9k / -88.0k | 13/14 | 0.65 |
| SELECTED best (R$ sized): HAR_SESS_k0.6_un_r1.0 R12000c14 | 35.3k / 96.6k / 574.2k / -136.8k | **68.4k / 406.8k / -96.9k** | 32.9k / 107.1k / 345.6k / -120.5k | 75.9k / 244.8k / -85.4k | 11/14 | 0.71 |
| Part 3 rule: fixed60|3.3_vt60k | 24.7k / 84.4k / 380.0k / -148.6k | **85.2k / 383.5k / -149.9k** | 29.1k / 129.6k / 380.0k / -134.8k | 130.8k / 383.5k / -136.0k | 8/28 | 1.01 |
| Part 3 rule: fixed60|3.5_kelly0.25 | 25.9k / 85.1k / 371.7k / -134.7k | **81.9k / 357.8k / -129.7k** | 37.4k / 116.3k / 291.8k / -116.3k | 112.0k / 280.9k / -111.9k | 8/14 | 0.96 |
| Part 3 rule: firm|3.3_vt60k | 17.5k / 92.2k / 536.6k / -136.9k | **131.3k / 764.1k / -195.0k** | 34.9k / 100.5k / 310.4k / -135.4k | 143.1k / 442.0k / -192.7k | 12/28 | 1.42 |
| Part 3 rule: firm|3.5_kelly0.25 | 16.9k / 84.9k / 466.0k / -136.1k | **125.8k / 690.6k / -201.6k** | 19.7k / 98.5k / 302.4k / -135.2k | 145.9k / 448.1k / -200.3k | 9/28 | 1.48 |
| Part 3 rule: firm|3.6_z2.0 | 14.9k / 80.5k / 327.9k / -135.8k | **134.6k / 547.9k / -227.0k** | 19.4k / 99.9k / 311.5k / -135.8k | 166.9k / 520.5k / -226.9k | 8/19 | 1.67 |


## (1) Forecast skill table (Part 1)

Forecast table: l2vast/pairP2/firm/forecast_table.parquet (43,552 half-hour instants x 5 targets x 9 forecasters + range/ATR targets; documented in firm/FORECAST_TABLE.md). Truncation check (10 random instants x {cut, random-future}): 0 mismatches (firm/trunc_check.log). Skills are rank correlations of the forecast with the realised log per-minute RV of the horizon; "rhoToD" removes the time-of-day mean (the intraday seasonality alone gives ~0.7), so rhoToD is the honest skill. IS rows before 2023-07 are in-sample (earliest refit); all WF/L8W rows are walk-forward (monthly refit, 3-day embargo).

### 1.4a Forecast skill by target and window (rank corr / MAE of log sigma_min / rank corr after removing the time-of-day mean = "within-ToD skill"); IS rows before 2023-07 are in-sample

**target y2h**

| model | IS rho/MAE/rhoToD | WF rho/MAE/rhoToD | L8W rho/MAE/rhoToD |
|---|---|---|---|
| prior | 0.70/0.364/0.67 | 0.75/0.339/0.80 | 0.58/0.319/0.59 |
| atr20 | 0.68/0.357/0.34 | 0.61/0.411/0.56 | 0.35/0.393/0.28 |
| har | 0.88/0.227/0.53 | 0.81/0.293/0.68 | 0.62/0.317/0.31 |
| hari | 0.92/0.183/0.70 | 0.90/0.209/0.83 | 0.78/0.211/0.62 |
| ewma94 | 0.85/0.255/0.32 | 0.74/0.346/0.53 | 0.58/0.322/-0.01 |
| ewma97 | 0.84/0.265/0.19 | 0.70/0.370/0.43 | 0.58/0.311/-0.05 |
| garch | 0.83/0.274/-0.00 | 0.75/0.344/0.56 | 0.59/0.369/0.12 |
| ridge | 0.93/0.178/0.72 | 0.90/0.208/0.83 | 0.80/0.205/0.63 |
| lgb | 0.94/0.161/0.77 | 0.90/0.207/0.84 | 0.81/0.192/0.66 |

**target y4h**

| model | IS rho/MAE/rhoToD | WF rho/MAE/rhoToD | L8W rho/MAE/rhoToD |
|---|---|---|---|
| prior | 0.66/0.377/0.63 | 0.71/0.359/0.78 | 0.60/0.318/0.55 |
| atr20 | 0.64/0.360/0.35 | 0.60/0.400/0.56 | 0.35/0.378/0.29 |
| har | 0.88/0.217/0.55 | 0.81/0.280/0.68 | 0.65/0.300/0.32 |
| hari | 0.92/0.184/0.68 | 0.89/0.214/0.81 | 0.77/0.219/0.58 |
| ewma94 | 0.85/0.246/0.32 | 0.74/0.335/0.53 | 0.61/0.305/-0.01 |
| ewma97 | 0.83/0.256/0.19 | 0.70/0.359/0.42 | 0.61/0.297/-0.04 |
| garch | 0.82/0.264/-0.01 | 0.76/0.331/0.56 | 0.61/0.348/0.13 |
| ridge | 0.92/0.180/0.70 | 0.89/0.212/0.82 | 0.79/0.212/0.60 |
| lgb | 0.94/0.154/0.76 | 0.89/0.211/0.83 | 0.81/0.189/0.63 |

**target yrest**

| model | IS rho/MAE/rhoToD | WF rho/MAE/rhoToD | L8W rho/MAE/rhoToD |
|---|---|---|---|
| prior | 0.74/0.321/0.60 | 0.76/0.311/0.76 | 0.61/0.295/0.53 |
| atr20 | 0.73/0.301/0.33 | 0.65/0.363/0.55 | 0.33/0.375/0.22 |
| har | 0.86/0.235/0.52 | 0.77/0.299/0.66 | 0.50/0.336/0.29 |
| hari | 0.90/0.201/0.65 | 0.86/0.230/0.79 | 0.69/0.241/0.55 |
| ewma94 | 0.82/0.265/0.30 | 0.69/0.350/0.52 | 0.43/0.336/-0.02 |
| ewma97 | 0.80/0.274/0.18 | 0.65/0.373/0.42 | 0.43/0.325/-0.05 |
| garch | 0.79/0.283/-0.02 | 0.71/0.348/0.55 | 0.45/0.383/0.10 |
| ridge | 0.91/0.195/0.68 | 0.87/0.226/0.80 | 0.72/0.225/0.62 |
| lgb | 0.94/0.151/0.79 | 0.87/0.219/0.82 | 0.73/0.208/0.62 |

**target ysess**

| model | IS rho/MAE/rhoToD | WF rho/MAE/rhoToD | L8W rho/MAE/rhoToD |
|---|---|---|---|
| prior | 0.89/0.222/0.58 | 0.82/0.289/0.73 | 0.80/0.321/0.50 |
| atr20 | 0.86/0.233/0.36 | 0.77/0.306/0.60 | 0.75/0.279/0.26 |
| har | 0.89/0.198/0.58 | 0.83/0.255/0.73 | 0.76/0.255/0.38 |
| hari | 0.90/0.190/0.61 | 0.85/0.239/0.77 | 0.80/0.234/0.51 |
| ewma94 | 0.85/0.232/0.34 | 0.75/0.314/0.57 | 0.67/0.255/-0.02 |
| ewma97 | 0.83/0.244/0.20 | 0.71/0.338/0.46 | 0.66/0.239/-0.07 |
| garch | 0.80/0.249/-0.03 | 0.77/0.316/0.59 | 0.70/0.322/0.08 |
| ridge | 0.92/0.172/0.69 | 0.88/0.220/0.80 | 0.83/0.186/0.60 |
| lgb | 0.95/0.134/0.78 | 0.89/0.207/0.82 | 0.85/0.157/0.67 |

**target yday**

| model | IS rho/MAE/rhoToD | WF rho/MAE/rhoToD | L8W rho/MAE/rhoToD |
|---|---|---|---|
| prior | 0.63/0.197/0.63 | 0.70/0.232/0.70 | 0.38/0.165/0.38 |
| atr20 | 0.49/0.196/0.49 | 0.59/0.267/0.59 | 0.33/0.173/0.33 |
| har | 0.60/0.166/0.60 | 0.72/0.214/0.72 | 0.38/0.144/0.38 |
| hari | 0.60/0.166/0.60 | 0.72/0.214/0.72 | 0.38/0.144/0.38 |
| ewma94 | 0.35/0.211/0.35 | 0.52/0.274/0.52 | -0.07/0.166/-0.07 |
| ewma97 | 0.19/0.225/0.19 | 0.38/0.302/0.38 | -0.08/0.175/-0.08 |
| garch | -0.29/0.245/-0.29 | 0.58/0.269/0.58 | 0.13/0.205/0.13 |
| ridge | 0.79/0.139/0.79 | 0.79/0.193/0.79 | 0.62/0.127/0.62 |
| lgb | 0.80/0.149/0.80 | 0.78/0.200/0.78 | 0.61/0.134/0.61 |

### 1.4b Skill by session (WF, ridge and LGB; target 2h and session-level)

| target | model | ASIA | LONDON | NY |
|---|---|---|---|---|
| y2h | har | 0.78/0.303 | 0.80/0.254 | 0.68/0.321 |
| y2h | hari | 0.88/0.204 | 0.89/0.195 | 0.84/0.229 |
| y2h | ridge | 0.88/0.206 | 0.89/0.194 | 0.84/0.226 |
| y2h | lgb | 0.89/0.199 | 0.89/0.194 | 0.85/0.228 |
| y4h | har | 0.78/0.279 | 0.83/0.240 | 0.65/0.322 |
| y4h | hari | 0.87/0.202 | 0.89/0.199 | 0.80/0.243 |
| y4h | ridge | 0.87/0.203 | 0.89/0.197 | 0.81/0.236 |
| y4h | lgb | 0.88/0.198 | 0.90/0.196 | 0.82/0.240 |
| yrest | har | 0.79/0.300 | 0.65/0.272 | 0.64/0.326 |
| yrest | hari | 0.88/0.209 | 0.74/0.235 | 0.78/0.248 |
| yrest | ridge | 0.87/0.216 | 0.78/0.219 | 0.79/0.243 |
| yrest | lgb | 0.88/0.206 | 0.81/0.210 | 0.81/0.243 |
| ysess | har | 0.82/0.286 | 0.70/0.234 | 0.64/0.246 |
| ysess | hari | 0.82/0.285 | 0.78/0.212 | 0.71/0.221 |
| ysess | ridge | 0.84/0.244 | 0.80/0.202 | 0.73/0.214 |
| ysess | lgb | 0.85/0.226 | 0.83/0.191 | 0.76/0.205 |

### 1.4c Skill by regime (WF; previous-day VIX terciles with cut points from the IS window)

VIX cut points (IS): 14.0, 17.3

| target | model | VIX low | VIX mid | VIX high |
|---|---|---|---|---|
| y2h | har | 0.86/0.258 | 0.77/0.287 | 0.77/0.311 |
| y2h | ridge | 0.92/0.188 | 0.88/0.208 | 0.87/0.215 |
| y2h | lgb | 0.92/0.193 | 0.89/0.202 | 0.88/0.217 |
| y4h | har | 0.86/0.250 | 0.78/0.275 | 0.78/0.295 |
| y4h | ridge | 0.91/0.191 | 0.87/0.211 | 0.86/0.218 |
| y4h | lgb | 0.91/0.196 | 0.88/0.205 | 0.87/0.223 |
| yrest | har | 0.81/0.271 | 0.72/0.296 | 0.74/0.312 |
| yrest | ridge | 0.89/0.205 | 0.84/0.227 | 0.84/0.230 |
| yrest | lgb | 0.90/0.200 | 0.85/0.214 | 0.84/0.231 |
| ysess | har | 0.85/0.240 | 0.81/0.243 | 0.80/0.276 |
| ysess | ridge | 0.89/0.203 | 0.86/0.215 | 0.84/0.232 |
| ysess | lgb | 0.90/0.195 | 0.88/0.196 | 0.85/0.224 |

### 1.4d Calibration by decile of the forecast (WF, target y2h, ridge and LGB): mean realised vs mean predicted log sigma_min

| decile | ridge pred | ridge real | lgb pred | lgb real |
|---|---|---|---|---|
| 1 | -9.55 | -9.53 | -9.52 | -9.53 |
| 2 | -9.19 | -9.16 | -9.17 | -9.15 |
| 3 | -8.99 | -8.93 | -8.97 | -8.94 |
| 4 | -8.81 | -8.75 | -8.80 | -8.76 |
| 5 | -8.64 | -8.60 | -8.63 | -8.60 |
| 6 | -8.48 | -8.45 | -8.47 | -8.45 |
| 7 | -8.31 | -8.30 | -8.31 | -8.30 |
| 8 | -8.13 | -8.13 | -8.12 | -8.12 |
| 9 | -7.90 | -7.90 | -7.89 | -7.89 |
| 10 | -7.46 | -7.48 | -7.54 | -7.47 |

### 1.4e Forecast-error volatility (the model's own uncertainty): std of log-error (WF) and trailing-error-SD feature; by session

| target | model | err SD all | ASIA | LONDON | NY | median trailing err_sd feature |
|---|---|---|---|---|---|---|
| y2h | ridge | 0.285 | 0.273 | 0.264 | 0.312 | 0.274 |
| y2h | lgb | 0.278 | 0.264 | 0.258 | 0.308 | 0.267 |
| y2h | hari | 0.286 | 0.273 | 0.265 | 0.314 | 0.279 |
| y4h | ridge | 0.288 | 0.268 | 0.265 | 0.325 | 0.275 |
| y4h | lgb | 0.282 | 0.261 | 0.260 | 0.319 | 0.266 |
| y4h | hari | 0.289 | 0.268 | 0.266 | 0.329 | 0.282 |
| yrest | ridge | 0.304 | 0.275 | 0.299 | 0.332 | 0.286 |
| yrest | lgb | 0.293 | 0.272 | 0.281 | 0.324 | 0.273 |
| yrest | hari | 0.311 | 0.269 | 0.319 | 0.334 | 0.295 |
| ysess | ridge | 0.286 | 0.291 | 0.267 | 0.282 | 0.290 |
| ysess | lgb | 0.272 | 0.288 | 0.255 | 0.265 | 0.270 |
| ysess | hari | 0.313 | 0.322 | 0.275 | 0.286 | 0.310 |

### 1.3 Intraday update vs session-open forecast (WF): skill for the REST-OF-SESSION target at instants after the open, session-open forecast (static) vs refreshed forecast

| model | session-open forecast rho / MAE (target yrest, instants after the open) | refreshed (30-min) rho / MAE |
|---|---|---|
| ridge | 0.73 / 0.320 | 0.87 / 0.224 |
| lgb | 0.73 / 0.319 | 0.87 / 0.219 |
| hari | 0.71 / 0.336 | 0.86 / 0.229 |

### 1.5 Implied vs realized (VXN-implied daily vol vs next-day realized; ratio as regime feature)

WF label days n=700: corr(log VXN-implied daily vol, log realized next-day vol)=0.74; mean(log realized - log implied)=-0.36 (variance risk premium: realized below implied); corr(log VXN-implied, log ridge forecast)=0.87; rank corr of ratio feature impl_real with next-day RV residual of HAR: 0.01

LightGBM split importance (mean over monthly refits, normalised, top 12 by target 2h): 
tod 0.247, rv30 0.058, rngsofar_atr 0.039, rvsess 0.037, sd_lsig 0.030, VIX1D 0.028, ovn 0.027, rvday 0.025, p_lsig 0.024, st_ca_15 0.024, lret_day 0.023, term 0.021


## (2) The k x R$ map (weekly mean / SD / maxDD, WF; $k at 14/14; clamp [25,150], cap 28; "14" = fixed 14 lots, no sizing)

Each cell regenerates the trades with bracket = clamp(k x forecast horizon-RV in points). Horizon: SESS = session-open forecast (static), T2H = 2-h forecast refreshed every 30 min, T4H = 4-h. WF window. Full per-cell file (all 4,671 cells, IS/WF/L8W): firm/out/p23_cells.csv.

**RIDGE / T2H (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 14/110/888 | 10/107/883 | 11/110/924 | -2/115/1544 | -4/116/1620 | 1/118/1318 | 3/121/1338 |
| 0.8 | 18/115/716 | 16/103/608 | 17/109/672 | 9/117/1192 | 5/123/1329 | 5/119/1442 | 7/126/1474 |
| 1.0 | 20/111/670 | 15/92/548 | 16/99/578 | 11/99/650 | 6/102/853 | 5/110/1012 | 2/117/1001 |
| 1.25 | 16/112/870 | 11/88/743 | 14/94/698 | 14/101/612 | 7/104/937 | 8/108/825 | 3/113/1139 |
| 1.5 | 20/114/851 | 19/81/431 | 19/86/474 | 18/94/506 | 15/98/469 | 17/114/612 | 12/112/843 |
| 2.0 | 6/118/795 | 9/70/400 | 11/77/384 | 11/90/511 | 14/97/529 | 14/108/498 | 15/114/594 |
| 2.5 | 3/115/891 | 7/66/494 | 10/71/507 | 12/83/557 | 14/87/707 | 13/96/590 | 10/109/838 |

**RIDGE / SESS (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 15/109/798 | 18/93/637 | 17/101/614 | 17/106/692 | 13/111/846 | 5/113/1018 | 3/122/1132 |
| 0.8 | 21/108/638 | 15/82/482 | 20/90/418 | 22/102/420 | 21/108/487 | 17/112/623 | 11/116/728 |
| 1.0 | 9/113/757 | 9/72/525 | 8/79/539 | 9/89/588 | 11/94/592 | 10/103/526 | 12/107/640 |
| 1.25 | 7/117/805 | 8/67/468 | 10/70/452 | 10/81/521 | 12/88/528 | 13/95/502 | 11/101/582 |
| 1.5 | 1/117/920 | 8/68/521 | 7/72/532 | 8/84/630 | 9/87/744 | 7/99/861 | 0/107/1085 |
| 2.0 | -6/111/1956 | -1/69/1024 | -1/72/1139 | -0/84/1081 | -1/87/1348 | 2/93/1426 | -3/100/1661 |
| 2.5 | -1/107/1554 | 1/67/683 | 1/68/723 | 3/81/722 | 6/85/796 | 3/89/1034 | 6/96/1063 |

**LGB / T2H (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 18/116/955 | 11/103/997 | 11/111/959 | 2/118/1304 | -3/118/1356 | -1/119/1284 | 2/121/1255 |
| 0.8 | 25/111/650 | 16/96/611 | 19/102/691 | 12/106/1116 | 6/108/1264 | 11/114/1475 | 7/120/1539 |
| 1.0 | 15/113/765 | 12/90/671 | 13/95/695 | 6/102/748 | 2/102/998 | -0/110/1335 | -3/114/1257 |
| 1.25 | 10/110/936 | 14/83/552 | 14/87/532 | 12/98/522 | 12/106/568 | 9/108/877 | 3/107/1025 |
| 1.5 | 12/111/1013 | 14/80/460 | 17/88/491 | 16/97/587 | 15/100/591 | 15/110/502 | 12/116/836 |
| 2.0 | 10/113/768 | 9/70/453 | 11/78/448 | 11/90/555 | 13/96/669 | 13/101/628 | 16/110/612 |
| 2.5 | 5/118/757 | 6/68/513 | 7/73/533 | 7/84/657 | 10/89/833 | 7/98/874 | 8/108/892 |

**ATR20 / T2H (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 11/103/821 | 7/108/958 | 2/110/1237 | -8/112/1818 | -13/113/2436 | -15/116/2606 | -14/117/2473 |
| 0.8 | 20/108/857 | 22/106/720 | 18/114/978 | 8/120/1308 | -6/117/1609 | -8/115/1810 | -6/119/1742 |
| 1.0 | 24/104/550 | 30/92/404 | 29/101/449 | 22/109/702 | 16/109/855 | 11/113/1297 | 12/116/1277 |
| 1.25 | 25/110/807 | 21/81/513 | 19/89/605 | 20/99/655 | 13/106/876 | 10/110/1102 | 8/117/1350 |
| 1.5 | 13/109/735 | 14/81/481 | 18/86/480 | 16/96/540 | 13/98/676 | 8/102/823 | 5/109/1113 |
| 2.0 | 6/114/1030 | 13/79/466 | 13/86/475 | 14/98/495 | 11/103/772 | 10/109/756 | 6/109/933 |
| 2.5 | 14/120/631 | 13/76/464 | 16/83/461 | 17/93/547 | 17/102/595 | 21/107/659 | 20/116/591 |

**PRIOR / SESS (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 23/114/663 | 20/92/600 | 21/97/488 | 17/104/619 | 14/111/620 | 6/118/1045 | 3/121/1176 |
| 0.8 | 32/112/483 | 18/78/411 | 19/89/513 | 22/99/564 | 21/100/421 | 19/108/545 | 13/112/740 |
| 1.0 | 4/114/880 | 11/75/401 | 12/79/486 | 9/90/644 | 11/94/499 | 10/104/664 | 9/111/803 |
| 1.25 | 3/122/1176 | 7/71/526 | 7/75/560 | 7/84/609 | 6/94/839 | 4/102/936 | 3/107/959 |
| 1.5 | -1/112/1086 | 4/66/478 | 5/69/487 | 5/78/547 | 7/88/661 | 2/94/660 | -1/102/802 |
| 2.0 | -3/116/1792 | 3/71/761 | 2/74/860 | 5/86/913 | 7/90/1053 | 5/97/1337 | 3/104/1118 |
| 2.5 | 1/113/1259 | 3/69/661 | 3/70/717 | 6/83/854 | 8/88/1094 | 6/92/1082 | 7/98/1123 |

**HAR / SESS (clamped)** - benchmark: 25.0k/104.5k/401.3k

| k | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 0.6 | 40/115/567 | 26/91/498 | 28/99/506 | 29/106/515 | 23/109/654 | 19/115/787 | 14/122/743 |
| 0.8 | 16/115/758 | 14/81/447 | 14/87/492 | 14/98/540 | 15/103/679 | 15/111/674 | 14/117/727 |
| 1.0 | 14/113/763 | 10/79/575 | 13/85/466 | 13/95/531 | 11/102/557 | 16/113/625 | 15/116/736 |
| 1.25 | 11/119/800 | 11/74/496 | 12/78/520 | 13/86/559 | 16/96/686 | 12/101/778 | 17/108/804 |
| 1.5 | -3/117/1231 | 9/69/495 | 8/73/482 | 9/82/578 | 8/90/762 | 6/100/787 | 4/109/801 |
| 2.0 | -3/109/1354 | 1/66/770 | 0/68/817 | 2/82/797 | 5/85/952 | 7/93/1018 | 4/99/1239 |
| 2.5 | -1/107/1439 | 4/67/671 | 3/68/735 | 5/80/681 | 7/84/732 | 8/89/799 | 9/96/873 |

**Fixed-bracket controls** (14 lots; and size-only R$ rows): mean/SD/maxDD WF

| bracket | 14 lots | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|---|
| 30 | 8/95/904 | 8/104/958 | 7/108/847 | 5/111/905 | -3/114/1433 | -3/114/1433 | -3/114/1433 |
| 40 | 29/101/578 | 26/93/625 | 27/102/603 | 23/107/756 | 17/108/817 | 7/113/1356 | 9/117/1147 |
| 50 | 43/105/564 | 39/97/665 | 39/97/552 | 43/105/564 | 25/105/796 | 17/112/1073 | 10/119/1151 |
| 60 | 25/105/401 | 28/86/376 | 25/103/382 | 27/109/373 | 25/105/401 | 19/107/466 | 24/108/550 |
| 80 | 4/105/1064 | 6/74/1066 | 8/87/840 | 8/96/861 | 6/101/947 | 6/102/1049 | 5/111/1127 |
| 100 | -8/111/2699 | 1/70/1214 | 3/79/1103 | 4/86/1037 | 3/94/1201 | 4/98/1119 | 1/108/1794 |

**Coarse 45-cell view (SPEED addendum A2)**: see MORNING.md block / DS2_FIRM_PROGRESS.md (out/coarse_table.txt).

Other Part-2 grids (all in p23_cells.csv): 2.2 unclamped (tag _un_), 2.3 asymmetry (tag _r0.8 / _r1.25), 2.4 per-book (_kb) and per-session (_ks) k.

2.3 asymmetry: 32 cells at 14 lots; WF mean range -9.0k..30.4k, SD range 102.7k..116.5k; best mean RIDGE_T2H_k0.8_cl_r1.25|L14 30.4k; plateau: median WF mean 13.0k vs symmetric same-forecaster cells (see 2.1).
2.4 per-book k: 16 cells at 14 lots; WF mean range 10.2k..30.4k, SD range 109.1k..120.3k; best mean RIDGE_T2H_kb0.8-1.5|L14 30.4k; plateau: median WF mean 17.1k vs symmetric same-forecaster cells (see 2.1).
2.4 per-session k: 27 cells at 14 lots; WF mean range 6.6k..26.2k, SD range 103.4k..120.3k; best mean RIDGE_T2H_ks0.8-1.25-1.25|L14 26.2k; plateau: median WF mean 18.8k vs symmetric same-forecaster cells (see 2.1).


## (3) The firm cell vs the benchmark, all three windows

| cell | window | weekly mean | weekly SD | maxDD | worst wk | Sharpe | trades/wk | avg lots | max lots | peak concurrent lots |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK 14/14 | IS | 13.7k | 95.9k | 407.3k | -136.3k | 1.03 | 27 | 14.0 | 14 | 28 |
| BENCHMARK 14/14 | WF | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | 14.0 | 14 | 28 |
| BENCHMARK 14/14 | L8W | 34.2k | 109.4k | 267.1k | -98.9k | 2.25 | 40 | 14.0 | 14 | 28 |
| FIRM CELL R$16.8k cap28 | IS | 10.4k | 104.8k | 566.1k | -141.6k | 0.71 | 39 | 24.2 | 28 | 56 |
| FIRM CELL R$16.8k cap28 | WF | 5.5k | 102.1k | 852.9k | -137.1k | 0.39 | 38 | 19.3 | 28 | 56 |
| FIRM CELL R$16.8k cap28 | L8W | 18.6k | 103.4k | 256.0k | -134.8k | 1.51 | 34 | 15.3 | 28 | 54 |
| firm cell, size-cost off | IS | 25.1k | 103.4k | 469.5k | -136.9k | 1.75 | 39 | 24.1 | 28 | 56 |
| firm cell, size-cost off | WF | 12.1k | 101.7k | 669.4k | -139.8k | 0.86 | 38 | 19.3 | 28 | 56 |
| firm cell, size-cost off | L8W | 18.9k | 103.1k | 258.2k | -134.7k | 1.49 | 34 | 15.3 | 28 | 54 |
| firm cell cap 14 | IS | 15.0k | 81.8k | 278.8k | -134.8k | 1.32 | 56 | 13.6 | 14 | 28 |
| firm cell cap 14 | WF | 20.6k | 101.6k | 622.2k | -145.0k | 1.46 | 51 | 12.8 | 14 | 28 |
| firm cell cap 14 | L8W | 47.7k | 104.3k | 254.1k | -135.6k | 3.36 | 42 | 12.7 | 14 | 28 |
| firm bracket 14 lots | IS | 14.3k | 90.3k | 385.8k | -135.4k | 1.14 | 55 | 14.0 | 14 | 28 |
| firm bracket 14 lots | WF | 19.7k | 111.4k | 669.9k | -141.4k | 1.28 | 46 | 14.0 | 14 | 28 |
| firm bracket 14 lots | L8W | 40.3k | 110.5k | 288.4k | -135.0k | 2.62 | 39 | 14.0 | 14 | 28 |
| size-only fixed60 8 lots | IS | 4.0k | 56.5k | 411.7k | -134.5k | 0.52 | 38 | 8.0 | 8 | 16 |
| size-only fixed60 8 lots | WF | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | 8.0 | 8 | 16 |
| size-only fixed60 8 lots | L8W | 42.0k | 111.7k | 274.6k | -122.5k | 2.71 | 73 | 8.0 | 8 | 16 |
| fixed 50 pt, 12 lots (control) | IS | 6.1k | 73.3k | 352.6k | -135.1k | 0.60 | 40 | 12.0 | 12 | 24 |
| fixed 50 pt, 12 lots (control) | WF | 38.9k | 96.8k | 551.6k | -136.6k | 2.90 | 55 | 12.0 | 12 | 24 |
| fixed 50 pt, 12 lots (control) | L8W | 79.2k | 106.6k | 244.0k | -80.7k | 5.44 | 68 | 12.0 | 12 | 24 |
| ensemble20 (5.2), fixed 60 | IS | 6.5k | 93.0k | 586.6k | -136.0k | 0.50 | 296 | 1.4 | 1 | 28 |
| ensemble20 (5.2), fixed 60 | WF | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 395 | 1.4 | 1 | 28 |
| ensemble20 (5.2), fixed 60 | L8W | 43.5k | 99.2k | 289.7k | -95.5k | 3.18 | 433 | 1.4 | 1 | 28 |

IS note: IS is the first fit window; the forecasts in IS before 2023-07 are in-sample, later IS months walk-forward. Firm-cell size-cost decomposition (WF): R$16.8k with size cost 5.5k vs size cost off 12.1k vs no-credit variant 5.4k; i.e. at the S113 surface the 28-lot trades (24% of firm-cell trades) cost about half of the cell's edge. F2/F3 are therefore reported with and without it throughout (tags _nosc, _nocredit).

**Null N1 (shuffled forecast, circular wrap >=20 label days, whole cell regenerated; 200 worlds, common shift per world) and gates, finalist cells (14 cells / 25 variants):**

| cell | WF mean | WF SD | WF maxDD | L8W mean | rank mean | rank maxDD | rank scaled-SD | boot90 lo | halves | gates |
|---|---|---|---|---|---|---|---|---|---|---|
| ATR20_SESS_k0.6_cl_r1.0 / L14 | 30.2k | 107.4k | 561.4k | 3.4k | 0.62 | 0.83 | 0.79 | -6.0k | 16.8k/-4.3k | a0 b0 c0 d0 |
| ATR20_SESS_k0.6_un_r1.0 / L14 | 31.0k | 107.3k | 503.8k | 3.4k | 0.70 | 0.98 | 0.82 | -5.6k | 17.6k/-3.5k | a0 b0 c0 d0 |
| ATR20_T2H_k1.0_cl_r1.0 / R10000c14 | 32.7k | 87.2k | 411.3k | 54.0k | 0.96 | 1.00 | 0.99 | -3.6k | 6.0k/9.2k | a0 b1 c1 d0 |
| ATR20_T2H_k1.0_un_r1.0 / L14 | 29.3k | 102.0k | 470.0k | 54.0k | 0.89 | 0.96 | 0.94 | -8.9k | 12.1k/-2.0k | a0 b0 c0 d0 |
| ATR20_T2H_k1.0_un_r1.0 / R10000c14 | 35.1k | 86.4k | 388.5k | 54.0k | 0.98 | 0.96 | 0.99 | -1.0k | 11.9k/8.7k | a1 b1 c1 d0 |
| ATR20_T2H_k1.0_un_r1.0 / R10000c28 | 34.6k | 89.9k | 339.2k | 55.2k | 1.00 | 1.00 | 1.00 | -1.2k | 13.3k/6.6k | a1 b1 c1 d0 |
| ATR20_T2H_k1.0_un_r1.0 / R12000c14 | 35.9k | 93.2k | 410.7k | 57.3k | 0.99 | 0.93 | 0.99 | -0.8k | 11.2k/10.7k | a0 b1 c0 d0 |
| ATR20_T2H_k1.0_un_r1.0 / R12000c28 | 33.6k | 99.3k | 369.7k | 47.1k | 1.00 | 1.00 | 1.00 | -3.4k | 10.6k/6.9k | a1 b1 c1 d0 |
| ATR20_T2H_k1.0_un_r1.0 / R14000c14 | 37.0k | 98.8k | 403.6k | 57.1k | 0.99 | 0.96 | 0.99 | -0.7k | 14.1k/10.2k | a0 b1 c1 d0 |
| ATR20_T4H_k0.6_un_r1.0 / R10000c14 | 34.3k | 93.6k | 485.4k | 76.3k | 0.98 | 0.89 | 0.98 | -4.0k | 9.7k/9.1k | a0 b1 c0 d0 |
| GARCH_SESS_k0.6_cl_r1.0 / L14 | 32.5k | 112.1k | 674.0k | 55.2k | 0.47 | 0.72 | 0.69 | -6.2k | 18.6k/-1.5k | a0 b1 c0 d0 |
| GARCH_SESS_k0.6_un_r1.0 / L14 | 34.0k | 112.5k | 659.8k | 55.6k | 0.72 | 0.76 | 0.84 | -4.6k | 20.7k/-0.6k | a0 b1 c0 d0 |
| HARI_SESS_k0.6_un_r1.0 / L14 | 34.1k | 118.7k | 616.5k | 23.1k | 0.96 | 0.76 | 0.93 | -5.3k | 19.9k/0.3k | a0 b0 c0 d0 |
| HAR_SESS_k0.6_cl_r1.0 / L14 | 40.0k | 114.7k | 567.4k | 16.6k | 0.97 | 0.86 | 0.98 | 0.1k | 20.9k/10.3k | a0 b0 c0 d1 |
| HAR_SESS_k0.6_cl_r1.0 / R16800c14 | 38.4k | 104.6k | 530.3k | 26.4k | 0.96 | 0.94 | 0.98 | -0.3k | 18.9k/8.9k | a0 b0 c0 d0 |
| HAR_SESS_k0.6_un_r1.0 / L14 | 38.0k | 115.3k | 665.4k | 16.7k | 0.94 | 0.41 | 0.92 | -2.6k | 19.7k/7.5k | a0 b0 c0 d0 |
| HAR_SESS_k0.6_un_r1.0 / R12000c14 | 35.3k | 96.6k | 574.2k | 32.9k | 0.97 | 0.53 | 0.97 | -2.6k | 13.5k/7.6k | a0 b0 c0 d0 |
| HAR_SESS_k0.6_un_r1.0 / R14000c14 | 36.6k | 101.9k | 663.7k | 28.5k | 0.93 | 0.37 | 0.93 | -1.4k | 12.5k/10.9k | a0 b0 c0 d0 |
| HAR_SESS_k0.6_un_r1.0 / R16800c14 | 37.4k | 104.1k | 598.7k | 26.4k | 0.94 | 0.81 | 0.94 | -1.5k | 18.3k/7.6k | a0 b0 c0 d0 |
| HAR_T4H_k0.8_cl_r1.0 / R10000c28 | 25.9k | 92.4k | 388.6k | 51.6k | 0.96 | 1.00 | 0.97 | -13.2k | 10.0k/-6.6k | a1 b1 c1 d0 |
| PRIOR_SESS_k0.8_cl_r1.0 / L14 | 31.8k | 112.5k | 483.0k | 83.1k | 0.94 | 0.83 | 0.94 | -6.9k | 9.3k/4.7k | a0 b0 c0 d0 |
| RIDGE_T2H_k0.8_cl_r1.25 / L14 | 30.4k | 104.7k | 480.6k | 43.9k | 1.00 | 0.94 | 1.00 | -7.1k | 10.1k/1.5k | a0 b1 c0 d0 |
| RIDGE_T2H_k1.0_cl_r1.0 / L14 | 19.7k | 111.4k | 669.9k | 40.3k | 0.55 | 0.81 | 0.57 | -21.2k | 1.8k/-11.1k | a0 b0 c0 d0 |
| RIDGE_T2H_k1.0_cl_r1.0 / R16800c14 | 20.6k | 101.6k | 622.2k | 47.7k | 0.60 | 0.76 | 0.72 | -20.6k | 4.6k/-11.8k | a0 b1 c0 d0 |
| RIDGE_T2H_k1.0_cl_r1.0 / R16800c28 | 5.5k | 102.1k | 852.9k | 18.6k | 0.48 | 0.98 | 0.48 | -34.8k | -13.2k/-24.5k | a0 b0 c0 d0 |

Best-of-F (family-world scan over the 25 finalist variants; max WF mean subject to L8W mean > benchmark): real 35.3k, rank 0.790 among 200 shuffled-forecast worlds; required >= 1-0.05/3,352 = 0.99998. NOT cleared. Gates a-d passers (all four): see verdict.


## (4) Meta-labeling uplift (Part 4)

Walk-forward LightGBM classifier (monthly refit, trades closed >= 2 days before; first prediction month 2023-09), ~75 features at the signal bar incl. the Part 1 set, signal context (ST/HM distance, flip-bar range, age, previous 3 outcomes, other book direction, ES/RTY/NQ 5/15-min moves, VWAP side, range position, hour-of-week) and the 18:05/09:29 book state. OOS AUC: firm_full 0.507, firm_price 0.507, fixed60_full 0.504, fixed60_price 0.497 (0.5 = no skill). Calibration deciles (full features, firm base): d1 pred 0.41 hit 0.51; d2 pred 0.46 hit 0.52; d3 pred 0.48 hit 0.49; d4 pred 0.50 hit 0.52; d5 pred 0.51 hit 0.51; d6 pred 0.53 hit 0.53; d7 pred 0.54 hit 0.50; d8 pred 0.56 hit 0.52; d9 pred 0.58 hit 0.54; d10 pred 0.62 hit 0.52.

Top-20 mean |contribution| (firm base, full features): ema_dist 0.037, st_imb10 0.035, rv120 0.029, rngsofar_atr 0.028, lret_day 0.027, gap_atr 0.025, p_lsig 0.025, st_flowdir_15 0.023, dVXN5 0.022, st_imb5 0.020, st_sp1_15 0.018, impl_real 0.018, har_m 0.015, VIX1D 0.015, st_depth_rel20 0.015, p_4h_ridge 0.015, RTY_5m 0.015, ES_5m 0.013, har_w 0.012, vwap_side 0.012

| cell | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W maxDD | mean size mult | skipped |
|---|---|---|---|---|---|---|---|---|
| firm / base | 5.5k | 102.1k | 852.9k | -137.1k | 18.6k | 256.0k | 1.00 | 0.00 |
| firm / 4.2_binmap_full | 13.8k | 105.8k | 697.3k | -143.3k | 0.0k | 367.5k | 0.78 | 0.16 |
| firm / 4.2_skip0.4_full | 5.8k | 102.6k | 819.8k | -136.7k | 18.6k | 256.0k | 0.97 | 0.03 |
| firm / 4.2_skip0.45_full | 1.9k | 105.3k | 1033.3k | -138.3k | 13.0k | 264.4k | 0.90 | 0.10 |
| firm / 4.4_reg_full | 6.2k | 108.6k | 893.6k | -140.5k | 12.5k | 385.6k | 0.84 | 0.32 |
| firm / 4.2_binmap_price | 9.4k | 100.0k | 687.7k | -137.7k | 11.8k | 312.5k | 0.79 | 0.15 |
| firm / 4.2_skip0.4_price | 5.7k | 98.3k | 805.6k | -137.7k | 18.6k | 256.0k | 0.97 | 0.03 |
| firm / 4.2_skip0.45_price | -0.2k | 101.9k | 1079.9k | -137.5k | 17.4k | 255.5k | 0.90 | 0.10 |
| firm / 4.4_reg_price | 0.6k | 102.0k | 1059.4k | -142.1k | 8.7k | 324.5k | 0.86 | 0.30 |
| fixed60 / base | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 267.1k | 1.00 | 0.00 |
| fixed60 / 4.2_binmap_full | 15.8k | 96.5k | 627.7k | -136.5k | 13.5k | 367.4k | 0.77 | 0.17 |
| fixed60 / 4.2_skip0.4_full | 25.9k | 106.7k | 438.9k | -137.2k | 34.2k | 267.1k | 0.96 | 0.04 |
| fixed60 / 4.2_skip0.45_full | 24.3k | 106.0k | 454.8k | -138.7k | 34.2k | 267.5k | 0.87 | 0.13 |
| fixed60 / 4.4_reg_full | 7.6k | 97.6k | 821.8k | -147.1k | 18.7k | 392.5k | 0.74 | 0.39 |
| fixed60 / 4.2_binmap_price | 17.7k | 101.4k | 361.9k | -136.2k | 37.9k | 361.9k | 0.77 | 0.16 |
| fixed60 / 4.2_skip0.4_price | 27.5k | 105.0k | 429.4k | -137.3k | 34.2k | 267.1k | 0.96 | 0.04 |
| fixed60 / 4.2_skip0.45_price | 26.9k | 99.7k | 366.7k | -139.0k | 34.2k | 267.1k | 0.89 | 0.11 |
| fixed60 / 4.4_reg_price | 7.7k | 101.5k | 921.8k | -137.3k | 49.6k | 212.2k | 0.81 | 0.34 |

Shuffled-label control (40 worlds, firm base, full features; labels permuted within every training window): WF mean / maxDD of the same size maps: binmap: mean 8.4k (sd 5.1k), maxDD 832k; skip0.40: mean 1.3k (sd 1.1k), maxDD 803k; skip0.45: mean 2.0k (sd 3.3k), maxDD 910k. Real: bin map 13.8k/697.3k, skip0.40 5.8k, skip0.45 1.9k: the real classifier is NOT distinguishable from shuffled labels (AUC ~0.50). Any cell that changed the mean did so through the size map (mean multiplier < 1 shrinks lots, which relieves the size-cost surface), not through bet quality.


## (5) Portfolio / diversification (Part 5)

| cell | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD |
|---|---|---|---|---|---|---|---|
| 5.1 / NQ_share1.00 | 5.5k | 102.1k | 852.9k | -137.1k | 18.6k | 103.4k | 256.0k |
| 5.1 / NQ_share0.50 | 8.1k | 50.9k | 284.1k | -70.3k | 10.4k | 50.0k | 137.6k |
| 5.1 / NQ_share0.33 | 7.0k | 35.0k | 189.2k | -46.4k | 8.8k | 30.5k | 77.1k |
| 5.1 / ES_share1.00 | -16.0k | 97.6k | 2430.3k | -142.3k | -27.0k | 113.1k | 378.6k |
| 5.1 / ES_share0.50 | -12.1k | 51.5k | 1752.2k | -85.4k | -22.5k | 51.7k | 231.6k |
| 5.1 / ES_share0.33 | -7.1k | 34.9k | 1101.5k | -48.6k | -11.3k | 39.1k | 157.0k |
| 5.1 / RTY_share1.00 | -20.4k | 89.3k | 3176.8k | -139.6k | -16.1k | 67.3k | 343.0k |
| 5.1 / RTY_share0.50 | -19.0k | 47.0k | 2879.0k | -71.6k | -9.1k | 62.4k | 243.1k |
| 5.1 / RTY_share0.33 | -12.6k | 31.5k | 1935.7k | -52.2k | 2.3k | 37.9k | 130.8k |
| 5.1 / PORT_NQ+ES | -4.0k | 78.7k | 780.4k | -138.2k | -12.1k | 89.7k | 343.1k |
| 5.1 / PORT_NQ+RTY | -10.9k | 71.1k | 1832.9k | -137.0k | 1.3k | 85.2k | 285.4k |
| 5.1 / PORT_NQ+ES+RTY | -12.7k | 68.5k | 2110.4k | -135.4k | -0.3k | 84.4k | 313.6k |

Pairwise correlation of the per-instrument firm-cell P&L (WF): NQ-ES: daily 0.38, weekly 0.35; NQ-RTY: daily 0.11, weekly 0.15; ES-RTY: daily 0.26, weekly 0.28.

ES and RTY run the pair's own ST/HM rules on their own 1-minute bars with their own ridge/T2H vol forecasts (same pipeline), minute-bar stop-first natural fills, 1 tick/side + $4.84/contract, locks on 1-minute marks; they are NOT P9-corrected and have no 1-s tape. Cross-check: NQ through the SAME minute-bar engine (fixed 60, 14 lots, no P9, no size cost) gives WF 29.1k/wk SD 100k maxDD 362k, so the engine itself is not what makes ES/RTY lose: the pair signal has NO positive sign on ES (WF -16k/wk at equal 14/14-NQ dollar risk) or RTY (-20k/wk) with this cost model. YM is not on disk (QUESTIONS.md). GC and CL (report-only, same pipeline, own forecasts, equal $16.8k risk, natural minute-path + 1 tick/side): GC: IS -37.2k, WF 1.9k/SD 111.4k/maxDD 1149.9k, L8W 22.7k; CL: IS -57.5k, WF -61.4k/SD 73.6k/maxDD 8882.2k, L8W -23.9k - no consistent positive sign (GC flips sign across windows, CL negative everywhere). The equal-dollar-risk NQ+ES+RTY portfolio is therefore worse than NQ alone.

5.2/5.3 (NQ, exact 1-s paths, P9-mapped):

| cell | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD |
|---|---|---|---|---|---|---|---|
| firm / base (credit on for fractional/small lots) | 5.5k | 102.1k | 852.9k | -137.1k | 18.6k | 103.4k | 256.0k |
| firm / 5.3_stagger (credit on for fractional/small lots) | 17.3k | 102.5k | 692.5k | -138.3k | 39.6k | 97.7k | 258.7k |
| firm / 5.2_ensemble20 (credit on for fractional/small lots) | 29.4k | 101.7k | 480.8k | -138.4k | 52.4k | 110.0k | 216.7k |
| fixed60 / base (credit on for fractional/small lots) | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k |
| fixed60 / 5.3_stagger (credit on for fractional/small lots) | 32.9k | 104.6k | 425.4k | -137.2k | 22.5k | 115.8k | 395.6k |
| fixed60 / 5.2_ensemble20 (credit on for fractional/small lots) | 42.0k | 104.0k | 314.2k | -136.2k | 54.0k | 91.9k | 265.2k |

**5.2 post-hoc null (addendum A3, exploratory):** 25 single (ST,HM) pairs on a wide grid: WF mean 28.6k (range 20.9k..40.2k), SD 103.4k, maxDD 497.7k; live pair 25.0k is below 20 of 25. 100 ensembles (25 centred + 75 random ST/HM center combos): WF mean 31.8k (sd 3.3k), SD 104.8k, maxDD 488.2k (sd 79.1k). The live-centred ensemble (WF 35.9k / SD 104.4k / maxDD 350.9k) ranks 0.88 on mean and 0.97 on maxDD among all ensembles. Weekly SD is ~104k for every single pair and every ensemble: the lock regime, not the parameter cell, sets weekly SD, so bagging reduces neither weekly SD nor (on average) maxDD (single 497.7k vs ensemble 488.2k); the live cell's gap to the ensemble is mostly the live cell sitting below its neighbourhood mean in WF (regression to the neighbourhood, not variance reduction).


## (6) Stability and feasibility (Part 6)

6.1 Stability: for the firm family (RIDGE/T2H/clamped; 7 k x 7 size columns) the cell with the best weekly Sharpe in each of the 11 walk-forward read windows: fold1: k=1.25 R14000c28; fold2: k=2.5 R12000c28; fold3: k=1.0 R10000c28; fold4: k=1.5 L14; fold5: k=1.5 R21000c28; fold6: k=1.5 R25000c28; fold7: k=2.5 R14000c28; fold8: k=1.0 L14; fold9: k=0.8 R10000c28; fold10: k=0.6 R21000c28; fold11: k=0.8 R12000c28. Consecutive-fold moves (grid steps): [3, 4, 2, 5, 1, 3, 4, 1, 4, 3]; folds flagged (> 1 step): 8 of 10. A stable optimum would not move; here it moves across the whole map, i.e. the k x R$ surface is noise-dominated (consistent with the null ranks).

6.2 Cost: size-dependent cost per the S113 surface (14->4.60, 21->6.11, 28->7.41, 42->9.38 excess ticks per lot per round trip; credit below 14 lots applied unless stated). Table of the firm family at R$ levels with / without the surface is in section 3 and p3b_cells.csv (tags _nosc, _nocredit).

6.3 Margin and NAM ($85k loss rule), WF window: benchmark: worst day -100.8k, days < -$85k: 19; worst week -137.1k, weeks < -$85k: 28 of 142; firm cell: worst day -97.5k, days < -$85k: 16; worst week -136.7k, weeks < -$85k: 28 of 142; fixed60 8 lots: worst day -80.5k, days < -$85k: 0; worst week -136.8k, weeks < -$85k: 14 of 142; ensemble20 (credit on): worst day -94.7k, days < -$85k: 19; worst week -135.6k, weeks < -$85k: 20 of 142

Peak concurrent lots (both books, any time): benchmark WF 28 (14+14 when both books are in), firm cell WF 56 / L8W 54; max single-trade size 28. Margin per NQ contract is UNVERIFIED in the repo (REPORT notes $1.5k intraday vs $20k exchange-style): at 56 peak lots that is $84k intraday-style or $1.12M exchange-style (> the $700k account), vs 28 lots/$42k and $560k for the benchmark 14/14. Overnight (Asia) exposure at max lots: the firm cell trades 28-lot clips in ASIA whenever the 2-h bracket is < 30 pts (vol is lowest there, so the bracket is smallest and lots largest): this is exactly where the S113 cost surface bites. NAM compatibility depends on the unverified margin rule; counts above are realized P&L only.

6.4 Locks in vol-defined R (thresholds scaled by R$/16.8k): R$ 10: WF 8.0k/SD 61.0k/maxDD 359.8k; R$ 12: WF 7.1k/SD 71.5k/maxDD 523.4k; R$ 14: WF 7.6k/SD 82.7k/maxDD 582.2k; R$ 16: WF 5.5k/SD 102.1k/maxDD 852.9k; R$ 21: WF 8.9k/SD 128.2k/maxDD 1076.6k; R$ 25: WF 14.8k/SD 151.9k/maxDD 1118.7k. Scaling the locks with R$ scales SD and maxDD nearly linearly (R$10k: SD 61k, maxDD 360k) but the weekly mean does not scale (8.0k vs 5.5k at 16.8k), so SD-per-mean is no better.


## (7) Verdict

**1. The headline number.** At equal weekly mean the benchmark has weekly SD 104.5k, maxDD 401.3k, worst week -137.1k (WF). The a-priori FIRM CELL (ridge, 2-h, k=1.0, constant $16.8k per trade, cap 28 lots) does NOT lower weekly SD: unscaled it earns only 5.5k/wk (benchmark 25.0k) at SD 102.1k, so scaling it to the benchmark mean multiplies SD by 4.5x. About half of the gap is the S113 size-cost surface (28-lot clips cost about 7.4 excess ticks per lot; with the surface off 12.1k), the rest is that tight 2-h brackets in quiet sessions give more trades hitting stops (bracket median 51 pts, 25-150 range, vs 60). Weekly SD itself barely moves for any cell: it sits at 100-115k for almost every bracket, size or parameter cell because the lock regime (per-book +5R/-2R, combined 8R/give-back, week floor 8R, fixed-dollar thresholds) truncates the tails; what changes is the mean and the maxDD.

**2. What does lower SD at equal mean is mostly sizing against the fixed-dollar locks, not vol normalisation.** The size-only control (the unchanged 60-pt pair at 8 lots) has WF 28.4k/SD 86.3k/maxDD 375.6k and L8W 42.0k (equal-mean SD 75.8k), but its IS is 4.0k/wk, i.e. not stable across windows and it has no forecast to null-test. Vol-sized cells show equal-mean SDs of 60-75k (best: ATR20/T2H/k1.0 unclamped at R$10-12k: WF 34.6k/SD 89.9k/maxDD 339.2k, L8W 55.2k, equal-mean SD 64.9k) - but they are picked from ~4,700 cells.

**3. Selection control.** Of 25 finalist variants (200 shuffled-forecast worlds each) the cell ATR20/T2H/k1.0 unclamped at R$10k/cap28 passes gates a, b and c (null ranks 1.00/1.00, scaled-SD rank 1.00) but fails gate d (4-week block bootstrap 90% CI of the WF weekly delta mean is [-1.2k, +19.7k], i.e. includes zero; both halves positive 13.3k/6.6k) and fails best-of-F (family-world rank 0.79 vs required 0.99998). HAR/session k=0.6 at 14 lots passes d only. No cell passes gates a-d together and best-of-F. The a-priori firm cell has null ranks 0.48-0.98 and negative bootstrap lower bound. => no LEAD, no CONFIRMED, no forward shadow, no frozen leads JSON, no DS2_VOL_SPEC.md.

**4. Meta-labeling: no bet-quality skill.** OOS AUC 0.507 (full features) / 0.507 (price only) on the firm base; 0.504 / 0.497 on the fixed-60 base; calibration is flat (hit rate 0.51-0.54 across all prediction deciles). The size maps that moved the mean (+8k on the firm base) moved it only by shrinking lots (mean multiplier 0.78-0.79) and are indistinguishable from the 40 shuffled-label worlds.

**5. Diversification.** The pair signal has no positive sign on ES (WF -16k/wk) or RTY (-20k/wk) at equal dollar risk; the NQ+ES+RTY portfolio is worse than NQ alone (WF -12.7k/wk, maxDD 2.1M). YM missing on disk; GC/CL not run. The 20-cell ensemble (5.2) does not reduce weekly SD (104k for every single cell and ensemble) and on average does not reduce maxDD; the live-centred ensemble's mean gain over the live cell (+10.9k/wk WF at fixed 60 pt) is the live cell sitting below its neighbourhood mean (live is below 20 of 25 grid-neighbour pairs in WF). Stagger entry (5.3) on the 60-pt pair: WF +7.9k/wk but maxDD +24k and L8W worse - not a variance reducer.

**6. Stability/feasibility.** The best k x R$ cell per walk-forward fold jumps across the map (section 6.1), peak lots 56 for the firm cell (28 for the benchmark), margin/NAM unverified, costs at 28 lots take a large share of the edge. Nothing here is a candidate for live.

**7. Direct-replay status.** Direct full-period L2 replay of the best candidate (ATR20/T2H/k1.0 unclamped, R$10k cap 28): RUNNING (45 months, 7 workers); result will be appended to this section.

**Answer to "should the live pair be vol-normalised?"** On this evidence no: the benchmark's 60-pt/14-lot bracket is not improved at equal mean by vol-unit brackets or constant-dollar sizing once the S113 cost surface and the lock regime are in; the one thing that moves the equal-mean SD materially is trade size relative to the fixed-dollar locks (8-12 lots at 60 pt), which is a DS2-15/DS2-50-type lock-interplay result, not a vol-normalisation result, and it is unstable in IS. F_P after this work: 3,332 + 19 families + 1 post-hoc (5.2b) = 3,352; best-of-F line 0.999985; 0 pass.


## Files
l2vast/PREREG_DS2_FIRM_V2.md (+ADDENDA2.md, .sha256), l2vast/pairP2/firm/{firmlib,firm_p1,firm_p23,firm_p3b,firm_p4,firm_p5,firm_p52,firm_p53,firm_null,firm_replay,gates,make_report}.py, firm/forecast_table*.parquet, firm/FORECAST_TABLE.md, firm/out/{p23,p3b,p4,p5,p52,p53}_cells.csv (+_x.npz daily series), null_p2_v2.csv, null_ranks_p2_v2.csv, p4_diag.json, p4_shuffled_labels.csv, trunc_check.log, out/part1.md; replay outputs /mnt/l2/l2vast/pairP2/firm/{firm,fixed40,base60,atr20}/; v1-mapping results out_v1/.
