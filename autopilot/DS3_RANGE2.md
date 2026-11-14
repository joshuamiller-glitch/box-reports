# DS3_RANGE2 - T-RANGE2: a better range forecast than UW (W-R2). Built 2026-11-14T20:27Z. Research only, NO PASS claim.
**VERDICT (plain, page 1 of the forecast part; engine dial re-runs below are still running): the options-market number from CME NQ options, put on top of our own realised-range model (HAR), beats UW (b) in london, nyam, nyam2, nypm, late, matches in none, loses in asia, pre (out-of-sample, R2 in L3M / L6M / older, same sample start as UW). The bigger fact: the HAR realised-range model ALONE already beats UW (b) in london, nyam, nyam2, nypm and (L3M/L6M) late; UW's range signal is mostly an IV-term proxy. CME options add real, placebo-clean gain over HAR in asia (+0.10 to +0.14 R2) and the last 90 minutes (+0.12 to +0.24), small in nypm (+0.03 to +0.07), and nothing in london / nyam. Asia is where UW (b) is still the best single model (its NDX/QQQ/SPX IV term beats our CME read of the same night), so UW is not yet fully replaceable for asia. Pre (08:30-09:30) is driven by the calendar flags (CPI/NFP/FOMC), not by CME or UW. UW (c) (full UW) is worse than (b) everywhere. Whether UW is still needed: for asia yes (UW b, or Cboe VIX-family inputs, which reach nearly the same R2 free); for london, nyam, nypm, late a HAR + CME (or HAR alone) forecast replaces it. Not a PASS claim; selection of the best model per session is by mean R2 over the three windows (hindsight among ~12 models, see caveats).**

Prereg: autopilot/RANGE2_PREREG.md (sha 942f27a55458bebb, in DECISIONS.md before scoring). Order: DIRECTIVE_RANGE2_20261114.md. Code: code/th_range2. Bulk: /mnt/l2/l2vast/_range2. Causal forecast files for the dials: /mnt/l2/l2vast/_range2/fc_r2_v1.parquet (HAR + CME; var 'r'), fc_r2_har.parquet (HAR only), same schema as W-RU fc.parquet; sent to W-CH2, W-D9, W-LR.

## 0. Table: best forecaster per session (same sample start as UW, 2024-10 training start; windows L3M >= 2026-08-01 n=74, L6M >= 2026-05-01 n=140, OLDER 2025-03-19..2026-04-30 n=288)
| session | best forecaster (mean R2 L3M/L6M/OLDER) | best CME model | CME vs UW (b): R2 diff L3M/L6M/OLDER | verdict | vs UW (c) | HAR alone vs UW (b) | CME model vs HAR alone: R2 gain L3M/L6M/OLDER |
|---|---|---|---|---|---|---|---|
| asia | UW_b (0.346) | HAR+CMElite | -0.058 / +0.022 / -0.108 | **LOSES to** | LOSES to | LOSES to | +0.142 / +0.124 / +0.018 |
| london | HAR+CME (0.225) | HAR+CME | +0.110 / +0.069 / +0.153 | **BEATS** | BEATS | BEATS | -0.044 / +0.010 / +0.043 |
| pre | HAR+CAL (0.436) | HAR+CMElite | -0.028 / -0.005 / -0.357 | **LOSES to** | LOSES to | LOSES to | +0.061 / +0.042 / -0.277 |
| nyam | HAR+CMElite (0.296) | HAR+CMElite | +0.117 / +0.111 / +0.101 | **BEATS** | BEATS | BEATS | -0.005 / +0.012 / +0.020 |
| nyam2 | HAR+CMElite (0.383) | HAR+CMElite | +0.294 / +0.103 / +0.156 | **BEATS** | BEATS | BEATS | +0.016 / +0.018 / +0.007 |
| nypm | COMBINED (0.218) | HAR+CME | +0.249 / +0.180 / +0.041 | **BEATS** | BEATS | BEATS | +0.034 / +0.060 / +0.003 |
| late | HAR+CME+CBOE (0.423) | HAR+CME | +0.335 / +0.372 / +0.016 | **BEATS** | BEATS | MATCHES | +0.116 / +0.115 / +0.465 |

Verdict rule (prereg): BEATS = mean R2 difference vs UW (b) over the three windows > +0.02 with at least 2 of 3 windows positive; LOSES = < -0.02 with at most 1 positive; else MATCHES. Best CME model = better of HAR+CME (23 CME columns) and HAR+CMElite (3 columns: ln IV nearest, next, forward) per session. "Best forecaster" = highest mean R2 of the three windows among ATR, HAR, HAR+CME, HAR+CMElite, HAR+CBOE, HAR+CAL, HAR+CME+CBOE, HAR+CMElite+CBOE, COMBINED, UW b, UW c (and CME-only); this is chosen with hindsight and is optimistic.

## 1. What was built (all causal; each input is available at the session's own start)
- **Targets**: session ln(H/L) on our NQ 1m bars, windows identical to the UW panel (asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nyam2 10:00-12:00, nypm 12:00-17:00, late = last 90 min 14:30-16:00 ET). Reproduces the UW panel targets exactly (max abs diff 0). 987 trading days 2023-02..2026-11.
- **HAR benchmark** (replaces ATR): own-session range lag 1 / mean 5 / mean 22, own-session realised vol (sqrt sum r^2) lag 1 / 5 / 22, prior-day RTH range lag 1 / 5 / 22 + RV 5, ranges of earlier sessions of the same Globex day (overnight and prior-session terms), move so far since 18:00 (for sessions starting 09:30 or later), range of the 90 minutes before the session start, prior NY pm and prior asia ranges. Ridge (lambda 10, z-scored), expanding window, minimum 120 days, refit every 10 trading days, same engine as the UW walk-forward. ATR = mean of last 14 own-session ranges (no fit).
- **CME options**: NQ options ohlcv-1m trade bars (already on the box: 2023-04-01..2026-11-09; definitions; no purchase). Each option trade bar is inverted to a Black-76 implied vol on a variance-time clock (expected-variance clock from our own minute returns, one full trading day = 1/252 year); ATM IV per expiry = recency/volume-weighted quadratic smile fit over +-8% moneyness (the NQ options market is thin at the money: only a few % of option bars trade within 3% of the money, so a smile fit is needed); nearest expiry E1, next E2, forward vol between them (E1->E2), refreshed every 30 min from 18:00 to 16:00 ET (45 readings a day; 18:00, 02:00, 08:30, 09:30, 10:00, 12:00, 14:30 are the session starts). Features: ln IV(E1), ln IV(E2), ln forward IV, term slope, implied remaining move to E1 expiry, implied remaining minus the range made so far, data age, time to expiry.
- **Data fix found on the way**: the stored minute futures series (uwbooks/min1_NQ) is back-adjusted (strikes sit 3% to 13% from it); the true level was recovered per day from put-call parity on 161,752 same-minute call/put pairs (factor 1.03 in 2023 rising to 1.13 in 2026, 1.000 from Oct 2026); ranges (log ratios) are unaffected.
- **Cboe**: VIX, VIX9D, VIX3M, VVIX (already in _calendar), plus VIX1D (from 2022-05), VXN, VIX6M fetched free from cdn.cboe.com (the one-day index and the NDX 30-day index). All prior-day close (causal for every session); VIX1D open added only for sessions starting 10:00 or later.
- **Calendar flags**: code/th_cal event_flags (FOMC, CPI, NFP, auctions, earnings per session, opex, month/quarter end, day of week). Exist only from 2024-10, so models with calendar are trained from 2024-10 only.
- **UW (a)(b)(c)**: from W-RU fc.parquet (asia, london R0 prior close; nyam R2 09:30; nyam2/nypm R3 10:00); pre (R1 08:30) and late (R3) computed with the same code (fc_uw_extra.parquet).
- Two training starts: **prim** = 2024-10-02 (same as UW; all tables below unless marked) and **long** = 2023-05 (HAR/CME/CBOE trained on 1.5 more years; calendar blocks missing before 2024-10 so imputed 0; the engine files use long).

## 2. CME implied-vol coverage (NQ, 2023-04..2026-11-09)
Option bars with an implied vol per year: 2023: 442k bars | 2024: 698k bars | 2025: 1046k bars | 2026: 1130k bars.
Readings (987 days):

| reading | have IV (nearest) | have next expiry | have fwd vol | median age of data (min) | share with age <= 60 min | median n bars |
|---|---|---|---|---|---|---|
| 18:00 asia | 1.00 | 0.99 | 0.98 | 127 | 0.00 | 1100 |
| 02:00 london | 1.00 | 0.99 | 0.96 | 45 | 0.78 | 1257 |
| 08:30 pre | 1.00 | 0.99 | 0.97 | 36 | 0.90 | 1521 |
| 09:30 nyam | 1.00 | 0.99 | 0.97 | 33 | 0.94 | 1575 |
| 10:00 nyam2 | 1.00 | 0.99 | 0.99 | 22 | 0.98 | 1779 |
| 12:00 nypm | 1.00 | 1.00 | 0.98 | 47 | 0.93 | 2255 |
| 14:30 late | 1.00 | 0.99 | 0.99 | 48 | 0.88 | 2562 |

Age = volume-weighted mean age of the option bars used. At 18:00 the data are from the previous afternoon (median 2 hours old) and overnight data are sparse (as for UW, which is stale there too); during RTH the data are about 20 to 50 minutes old. This is the honest CME-at-the-money picture: NQ options trade thinly at the money in Globex hours.

## 3. Comparison per session, out of sample, walk-forward (prim: same start as UW)
R2 is against the eval-window mean of the target (the UW pages' definition); accuracy = share of days with big / normal / small (expanding past terciles of the target, expanding terciles of the prediction) called right, chance about 0.33. Gain over HAR with shifted-day placebos in brackets (the CME / CBOE / calendar block replaced by that of a day 11 / 23 / 37 days earlier, mean of three).

**asia** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.072 | 0.126 | 0.066 | 0.41 | 0.54 | 0.49 | -0.093 | -0.027 | -0.226 |
| HAR | 0.165 | 0.152 | 0.292 | 0.46 | 0.59 | 0.59 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.287 | 0.253 | 0.305 | 0.50 | 0.57 | 0.63 | +0.122 (-0.005) | +0.101 (-0.007) | +0.013 (-0.011) |
| HAR+CMElite | 0.306 | 0.277 | 0.310 | 0.53 | 0.59 | 0.60 | +0.142 (+0.004) | +0.124 (+0.002) | +0.018 (-0.001) |
| CMElite | 0.306 | 0.259 | 0.294 | 0.53 | 0.58 | 0.63 | +0.141 (+0.000) | +0.107 (+0.000) | +0.002 (+0.000) |
| CME_only | 0.290 | 0.237 | 0.297 | 0.49 | 0.59 | 0.62 | +0.125 (-0.240) | +0.084 (-0.326) | +0.005 (-0.355) |
| HAR+CME+CBOE | 0.338 | 0.231 | 0.252 | 0.46 | 0.56 | 0.60 | +0.174 (-0.054) | +0.079 (-0.007) | -0.040 (-0.049) |
| HAR+CMElite+CBOE | 0.362 | 0.255 | 0.257 | 0.54 | 0.58 | 0.59 | +0.197 (-0.040) | +0.102 (+0.004) | -0.035 (-0.034) |
| HAR+CBOE | 0.394 | 0.245 | 0.282 | 0.53 | 0.58 | 0.56 | +0.230 (-0.044) | +0.092 (+0.006) | -0.010 (-0.037) |
| HAR+CAL | 0.136 | 0.122 | 0.285 | 0.49 | 0.58 | 0.57 | -0.029 (-0.038) | -0.030 (-0.031) | -0.007 (-0.015) |
| COMBINED | 0.296 | 0.187 | 0.217 | 0.47 | 0.54 | 0.60 | +0.132 (-0.082) | +0.034 (-0.035) | -0.075 (-0.059) |
| UW_a | 0.106 | 0.072 | 0.204 | 0.45 | 0.55 | 0.56 | -0.058 | -0.081 | -0.088 |
| UW_b | 0.365 | 0.255 | 0.418 | 0.43 | 0.55 | 0.63 | +0.200 | +0.103 | +0.126 |
| UW_c | 0.342 | 0.260 | 0.366 | 0.49 | 0.57 | 0.63 | +0.177 | +0.108 | +0.074 |

**london** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.066 | -0.069 | 0.158 | 0.45 | 0.42 | 0.53 | -0.231 | -0.113 | -0.301 |
| HAR | 0.165 | 0.044 | 0.459 | 0.35 | 0.43 | 0.60 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.121 | 0.053 | 0.502 | 0.41 | 0.44 | 0.63 | -0.044 (-0.018) | +0.010 (-0.002) | +0.043 (-0.032) |
| HAR+CMElite | 0.129 | 0.050 | 0.491 | 0.39 | 0.42 | 0.66 | -0.036 (-0.021) | +0.006 (-0.007) | +0.032 (-0.013) |
| CMElite | -0.154 | -0.018 | 0.396 | 0.41 | 0.43 | 0.66 | -0.319 (+0.000) | -0.062 (+0.000) | -0.064 (+0.000) |
| CME_only | -0.064 | -0.017 | 0.400 | 0.38 | 0.40 | 0.67 | -0.229 (-0.224) | -0.061 (-0.102) | -0.059 (-0.539) |
| HAR+CME+CBOE | 0.059 | 0.092 | 0.446 | 0.39 | 0.42 | 0.61 | -0.106 (-0.072) | +0.048 (-0.008) | -0.014 (-0.078) |
| HAR+CMElite+CBOE | 0.064 | 0.100 | 0.439 | 0.43 | 0.44 | 0.64 | -0.101 (-0.078) | +0.057 (-0.011) | -0.020 (-0.053) |
| HAR+CBOE | 0.143 | 0.098 | 0.425 | 0.43 | 0.45 | 0.63 | -0.021 (-0.058) | +0.054 (-0.007) | -0.034 (-0.048) |
| HAR+CAL | 0.151 | 0.003 | 0.443 | 0.43 | 0.48 | 0.59 | -0.013 (-0.027) | -0.041 (-0.067) | -0.016 (-0.004) |
| COMBINED | 0.088 | 0.059 | 0.440 | 0.43 | 0.45 | 0.62 | -0.076 (-0.100) | +0.016 (-0.075) | -0.020 (-0.090) |
| UW_a | -0.065 | -0.166 | 0.211 | 0.41 | 0.40 | 0.57 | -0.230 | -0.210 | -0.248 |
| UW_b | 0.011 | -0.015 | 0.349 | 0.36 | 0.44 | 0.64 | -0.154 | -0.059 | -0.110 |
| UW_c | -0.128 | -0.194 | 0.240 | 0.43 | 0.45 | 0.64 | -0.292 | -0.237 | -0.220 |

**pre** (n L3M/L6M/OLDER = 74/140/289); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.100 | -0.083 | 0.121 | 0.31 | 0.34 | 0.49 | -0.003 | -0.081 | -0.148 |
| HAR | -0.098 | -0.002 | 0.269 | 0.35 | 0.36 | 0.58 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.114 | -0.021 | 0.043 | 0.36 | 0.38 | 0.54 | -0.016 (+0.043) | -0.019 (+0.026) | -0.226 (-0.019) |
| HAR+CMElite | -0.036 | 0.040 | -0.008 | 0.41 | 0.39 | 0.55 | +0.061 (+0.009) | +0.042 (+0.009) | -0.277 (-0.014) |
| CMElite | 0.009 | 0.066 | 0.347 | 0.46 | 0.44 | 0.55 | +0.107 (+0.000) | +0.068 (+0.000) | +0.078 (+0.000) |
| CME_only | -0.040 | 0.015 | 0.326 | 0.41 | 0.43 | 0.56 | +0.057 (+0.132) | +0.016 (+0.007) | +0.057 (-0.358) |
| HAR+CME+CBOE | -0.160 | -0.163 | -0.080 | 0.39 | 0.42 | 0.54 | -0.063 (+0.047) | -0.161 (+0.021) | -0.349 (-0.034) |
| HAR+CMElite+CBOE | -0.058 | -0.074 | -0.190 | 0.42 | 0.43 | 0.58 | +0.040 (+0.003) | -0.072 (+0.001) | -0.459 (-0.025) |
| HAR+CBOE | -0.089 | -0.135 | -0.028 | 0.41 | 0.41 | 0.56 | +0.008 (-0.005) | -0.133 (-0.005) | -0.297 (-0.031) |
| HAR+CAL | 0.465 | 0.401 | 0.443 | 0.49 | 0.51 | 0.61 | +0.563 (+0.048) | +0.403 (+0.022) | +0.174 (-0.032) |
| COMBINED | 0.371 | 0.302 | 0.202 | 0.47 | 0.46 | 0.61 | +0.469 (+0.062) | +0.304 (+0.019) | -0.066 (-0.080) |
| UW_a | -0.106 | -0.032 | 0.210 | 0.46 | 0.46 | 0.50 | -0.008 | -0.030 | -0.059 |
| UW_b | -0.009 | 0.045 | 0.349 | 0.49 | 0.43 | 0.54 | +0.089 | +0.047 | +0.080 |
| UW_c | 0.072 | 0.063 | 0.243 | 0.51 | 0.48 | 0.53 | +0.169 | +0.065 | -0.025 |

**nyam** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.018 | 0.053 | 0.120 | 0.54 | 0.54 | 0.51 | -0.205 | -0.192 | -0.274 |
| HAR | 0.223 | 0.245 | 0.394 | 0.50 | 0.54 | 0.61 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.221 | 0.247 | 0.415 | 0.42 | 0.55 | 0.55 | -0.002 (-0.002) | +0.002 (-0.001) | +0.021 (-0.005) |
| HAR+CMElite | 0.218 | 0.257 | 0.414 | 0.47 | 0.58 | 0.53 | -0.005 (+0.003) | +0.012 (+0.003) | +0.020 (-0.002) |
| CMElite | 0.178 | 0.215 | 0.332 | 0.53 | 0.57 | 0.57 | -0.045 (+0.000) | -0.030 (+0.000) | -0.062 (+0.000) |
| CME_only | 0.167 | 0.204 | 0.334 | 0.42 | 0.50 | 0.58 | -0.056 (-0.218) | -0.041 (-0.245) | -0.060 (-0.458) |
| HAR+CME+CBOE | 0.169 | 0.221 | 0.403 | 0.42 | 0.53 | 0.54 | -0.054 (-0.030) | -0.024 (-0.019) | +0.009 (-0.009) |
| HAR+CMElite+CBOE | 0.161 | 0.231 | 0.399 | 0.43 | 0.51 | 0.53 | -0.062 (-0.024) | -0.014 (-0.015) | +0.005 (-0.004) |
| HAR+CBOE | 0.131 | 0.213 | 0.397 | 0.42 | 0.52 | 0.56 | -0.092 (-0.023) | -0.031 (-0.012) | +0.003 (-0.001) |
| HAR+CAL | 0.185 | 0.211 | 0.379 | 0.50 | 0.59 | 0.58 | -0.038 (-0.011) | -0.033 (-0.014) | -0.015 (-0.009) |
| COMBINED | 0.143 | 0.197 | 0.375 | 0.46 | 0.53 | 0.57 | -0.080 (-0.041) | -0.047 (-0.036) | -0.019 (-0.019) |
| UW_a | 0.192 | 0.202 | 0.275 | 0.46 | 0.51 | 0.57 | -0.031 | -0.043 | -0.119 |
| UW_b | 0.102 | 0.146 | 0.313 | 0.42 | 0.51 | 0.55 | -0.122 | -0.099 | -0.081 |
| UW_c | 0.004 | 0.078 | 0.290 | 0.41 | 0.49 | 0.52 | -0.219 | -0.167 | -0.105 |

**nyam2** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.065 | 0.082 | 0.069 | 0.54 | 0.52 | 0.54 | -0.264 | -0.207 | -0.421 |
| HAR | 0.329 | 0.289 | 0.489 | 0.46 | 0.52 | 0.55 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.205 | 0.248 | 0.516 | 0.42 | 0.49 | 0.59 | -0.124 (-0.023) | -0.041 (-0.010) | +0.026 (-0.003) |
| HAR+CMElite | 0.346 | 0.307 | 0.497 | 0.43 | 0.51 | 0.57 | +0.016 (-0.007) | +0.018 (-0.003) | +0.007 (+0.000) |
| CMElite | 0.276 | 0.260 | 0.354 | 0.51 | 0.55 | 0.63 | -0.053 (+0.000) | -0.029 (+0.000) | -0.135 (+0.000) |
| CME_only | 0.227 | 0.251 | 0.362 | 0.47 | 0.52 | 0.59 | -0.102 (-0.373) | -0.037 (-0.297) | -0.127 (-0.558) |
| HAR+CME+CBOE | 0.163 | 0.238 | 0.487 | 0.43 | 0.50 | 0.57 | -0.167 (-0.087) | -0.050 (-0.037) | -0.002 (-0.022) |
| HAR+CMElite+CBOE | 0.287 | 0.291 | 0.460 | 0.45 | 0.54 | 0.56 | -0.042 (-0.066) | +0.002 (-0.029) | -0.030 (-0.015) |
| HAR+CBOE | 0.264 | 0.291 | 0.455 | 0.46 | 0.54 | 0.52 | -0.066 (-0.060) | +0.002 (-0.023) | -0.034 (-0.014) |
| HAR+CAL | 0.293 | 0.258 | 0.476 | 0.49 | 0.57 | 0.57 | -0.036 (-0.028) | -0.031 (-0.026) | -0.013 (-0.007) |
| COMBINED | 0.131 | 0.212 | 0.470 | 0.43 | 0.52 | 0.57 | -0.199 (-0.125) | -0.077 (-0.072) | -0.019 (-0.028) |
| UW_a | 0.127 | 0.262 | 0.338 | 0.53 | 0.57 | 0.57 | -0.202 | -0.027 | -0.151 |
| UW_b | 0.052 | 0.204 | 0.341 | 0.46 | 0.51 | 0.59 | -0.278 | -0.085 | -0.149 |
| UW_c | -0.166 | 0.164 | 0.306 | 0.49 | 0.56 | 0.57 | -0.495 | -0.124 | -0.184 |

**nypm** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.083 | 0.010 | 0.091 | 0.37 | 0.41 | 0.53 | +0.199 | -0.086 | -0.231 |
| HAR | -0.282 | 0.096 | 0.321 | 0.47 | 0.49 | 0.49 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.248 | 0.156 | 0.324 | 0.55 | 0.55 | 0.54 | +0.034 (-0.035) | +0.060 (-0.011) | +0.003 (-0.014) |
| HAR+CMElite | -0.392 | 0.137 | 0.315 | 0.48 | 0.50 | 0.54 | -0.110 (+0.014) | +0.040 (+0.001) | -0.007 (-0.003) |
| CMElite | -0.181 | 0.270 | 0.316 | 0.58 | 0.59 | 0.62 | +0.101 (+0.000) | +0.173 (+0.000) | -0.005 (+0.000) |
| CME_only | -0.090 | 0.266 | 0.318 | 0.59 | 0.62 | 0.61 | +0.192 (-0.080) | +0.170 (-0.129) | -0.003 (-0.433) |
| HAR+CME+CBOE | 0.063 | 0.168 | 0.192 | 0.55 | 0.51 | 0.56 | +0.345 (-0.004) | +0.072 (-0.021) | -0.129 (-0.051) |
| HAR+CMElite+CBOE | -0.140 | 0.129 | 0.168 | 0.56 | 0.52 | 0.57 | +0.142 (+0.049) | +0.032 (-0.006) | -0.153 (-0.037) |
| HAR+CBOE | -0.103 | -0.013 | 0.171 | 0.47 | 0.43 | 0.54 | +0.179 (+0.049) | -0.109 (-0.001) | -0.151 (-0.034) |
| HAR+CAL | 0.068 | 0.178 | 0.310 | 0.52 | 0.47 | 0.50 | +0.350 (-0.024) | +0.081 (-0.016) | -0.012 (-0.061) |
| COMBINED | 0.232 | 0.175 | 0.249 | 0.55 | 0.51 | 0.55 | +0.514 (+0.053) | +0.078 (-0.022) | -0.073 (-0.129) |
| UW_a | -0.427 | -0.044 | 0.309 | 0.47 | 0.49 | 0.50 | -0.145 | -0.141 | -0.013 |
| UW_b | -0.496 | -0.024 | 0.283 | 0.47 | 0.49 | 0.52 | -0.214 | -0.120 | -0.039 |
| UW_c | -0.983 | -0.159 | 0.176 | 0.48 | 0.53 | 0.47 | -0.701 | -0.256 | -0.145 |

**late** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.167 | -0.050 | 0.150 | 0.42 | 0.40 | 0.46 | -0.392 | -0.364 | +0.219 |
| HAR | 0.224 | 0.314 | -0.069 | 0.60 | 0.59 | 0.52 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.340 | 0.429 | 0.396 | 0.62 | 0.63 | 0.60 | +0.116 (-0.015) | +0.115 (+0.000) | +0.465 (-0.013) |
| HAR+CMElite | 0.204 | 0.372 | 0.320 | 0.62 | 0.62 | 0.59 | -0.020 (-0.000) | +0.058 (-0.001) | +0.389 (-0.007) |
| CMElite | 0.064 | 0.340 | 0.534 | 0.52 | 0.53 | 0.62 | -0.161 (+0.000) | +0.026 (+0.000) | +0.604 (+0.000) |
| CME_only | 0.282 | 0.429 | 0.513 | 0.59 | 0.59 | 0.64 | +0.058 (-0.498) | +0.115 (-0.359) | +0.582 (+0.000) |
| HAR+CME+CBOE | 0.402 | 0.465 | 0.401 | 0.56 | 0.59 | 0.62 | +0.177 (-0.000) | +0.151 (-0.005) | +0.470 (+0.049) |
| HAR+CMElite+CBOE | 0.262 | 0.421 | 0.361 | 0.58 | 0.56 | 0.59 | +0.038 (+0.019) | +0.107 (-0.000) | +0.430 (+0.039) |
| HAR+CBOE | 0.374 | 0.370 | 0.141 | 0.62 | 0.56 | 0.54 | +0.149 (+0.019) | +0.056 (+0.008) | +0.210 (+0.025) |
| HAR+CAL | 0.284 | 0.405 | 0.016 | 0.60 | 0.57 | 0.57 | +0.060 (+0.002) | +0.091 (+0.009) | +0.085 (-0.027) |
| COMBINED | 0.385 | 0.482 | 0.397 | 0.63 | 0.62 | 0.62 | +0.161 (+0.004) | +0.168 (+0.010) | +0.466 (+0.044) |
| UW_a | -0.166 | -0.068 | 0.375 | 0.45 | 0.46 | 0.49 | -0.391 | -0.382 | +0.444 |
| UW_b | 0.005 | 0.056 | 0.380 | 0.52 | 0.51 | 0.50 | -0.219 | -0.258 | +0.449 |
| UW_c | -0.100 | 0.087 | 0.308 | 0.51 | 0.51 | 0.47 | -0.324 | -0.227 | +0.377 |


### 3b. Longer training (long: 2023-05 start)

**asia** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.072 | 0.126 | 0.066 | 0.41 | 0.54 | 0.49 | -0.113 | -0.044 | -0.176 |
| HAR | 0.185 | 0.170 | 0.242 | 0.53 | 0.61 | 0.56 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.301 | 0.266 | 0.340 | 0.51 | 0.56 | 0.64 | +0.116 (+0.007) | +0.096 (+0.002) | +0.098 (-0.006) |
| HAR+CMElite | 0.315 | 0.284 | 0.317 | 0.53 | 0.61 | 0.61 | +0.130 (+0.007) | +0.114 (+0.005) | +0.075 (-0.004) |
| CMElite | 0.203 | 0.140 | 0.303 | 0.50 | 0.56 | 0.65 | +0.018 (+0.000) | -0.030 (+0.000) | +0.061 (+0.000) |
| CME_only | 0.222 | 0.135 | 0.314 | 0.49 | 0.58 | 0.62 | +0.037 (-0.379) | -0.034 (-0.572) | +0.072 (-0.353) |
| HAR+CME+CBOE | 0.349 | 0.243 | 0.343 | 0.49 | 0.56 | 0.64 | +0.164 (-0.010) | +0.073 (-0.008) | +0.101 (-0.017) |
| HAR+CMElite+CBOE | 0.375 | 0.267 | 0.321 | 0.51 | 0.59 | 0.60 | +0.190 (-0.008) | +0.097 (-0.004) | +0.079 (-0.016) |
| HAR+CBOE | 0.386 | 0.256 | 0.328 | 0.51 | 0.58 | 0.62 | +0.201 (-0.007) | +0.086 (-0.004) | +0.086 (-0.015) |
| HAR+CAL | 0.173 | 0.150 | 0.256 | 0.51 | 0.61 | 0.57 | -0.012 (-0.012) | -0.020 (-0.025) | +0.014 (-0.003) |
| COMBINED | 0.324 | 0.204 | 0.332 | 0.53 | 0.59 | 0.64 | +0.139 (-0.017) | +0.034 (-0.026) | +0.091 (-0.023) |
| UW_a | 0.106 | 0.072 | 0.204 | 0.45 | 0.55 | 0.56 | -0.078 | -0.098 | -0.038 |
| UW_b | 0.365 | 0.255 | 0.418 | 0.43 | 0.55 | 0.63 | +0.180 | +0.085 | +0.176 |
| UW_c | 0.342 | 0.260 | 0.366 | 0.49 | 0.57 | 0.63 | +0.157 | +0.091 | +0.124 |

**london** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.066 | -0.069 | 0.158 | 0.45 | 0.42 | 0.53 | -0.250 | -0.188 | -0.329 |
| HAR | 0.184 | 0.119 | 0.487 | 0.41 | 0.46 | 0.65 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.172 | 0.130 | 0.520 | 0.41 | 0.45 | 0.65 | -0.012 (-0.012) | +0.012 (+0.000) | +0.033 (-0.010) |
| HAR+CMElite | 0.175 | 0.127 | 0.521 | 0.39 | 0.44 | 0.67 | -0.009 (-0.015) | +0.009 (-0.000) | +0.034 (-0.007) |
| CMElite | -0.116 | 0.037 | 0.387 | 0.41 | 0.43 | 0.68 | -0.300 (+0.000) | -0.082 (+0.000) | -0.100 (+0.000) |
| CME_only | 0.027 | 0.052 | 0.407 | 0.38 | 0.39 | 0.67 | -0.157 (-0.297) | -0.067 (-0.227) | -0.080 (-0.543) |
| HAR+CME+CBOE | 0.141 | 0.144 | 0.523 | 0.41 | 0.44 | 0.64 | -0.044 (-0.043) | +0.025 (-0.006) | +0.036 (-0.021) |
| HAR+CMElite+CBOE | 0.146 | 0.144 | 0.519 | 0.41 | 0.44 | 0.66 | -0.038 (-0.046) | +0.025 (-0.008) | +0.032 (-0.016) |
| HAR+CBOE | 0.206 | 0.145 | 0.501 | 0.42 | 0.46 | 0.65 | +0.022 (-0.030) | +0.026 (-0.006) | +0.014 (-0.012) |
| HAR+CAL | 0.178 | 0.090 | 0.472 | 0.45 | 0.47 | 0.61 | -0.006 (-0.024) | -0.028 (-0.049) | -0.015 (-0.009) |
| COMBINED | 0.156 | 0.135 | 0.508 | 0.46 | 0.46 | 0.65 | -0.028 (-0.061) | +0.016 (-0.055) | +0.021 (-0.030) |
| UW_a | -0.065 | -0.166 | 0.211 | 0.41 | 0.40 | 0.57 | -0.249 | -0.285 | -0.276 |
| UW_b | 0.011 | -0.015 | 0.349 | 0.36 | 0.44 | 0.64 | -0.173 | -0.134 | -0.138 |
| UW_c | -0.128 | -0.194 | 0.240 | 0.43 | 0.45 | 0.64 | -0.312 | -0.312 | -0.247 |

**pre** (n L3M/L6M/OLDER = 74/140/289); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.100 | -0.083 | 0.121 | 0.31 | 0.34 | 0.49 | +0.011 | -0.107 | -0.312 |
| HAR | -0.112 | 0.024 | 0.433 | 0.38 | 0.41 | 0.57 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.147 | -0.029 | 0.418 | 0.49 | 0.46 | 0.54 | -0.036 (+0.052) | -0.053 (+0.028) | -0.015 (-0.019) |
| HAR+CMElite | -0.063 | 0.050 | 0.307 | 0.46 | 0.42 | 0.55 | +0.048 (+0.006) | +0.027 (+0.006) | -0.126 (-0.012) |
| CMElite | -0.002 | 0.046 | 0.396 | 0.47 | 0.44 | 0.56 | +0.110 (+0.000) | +0.022 (+0.000) | -0.037 (+0.000) |
| CME_only | -0.047 | 0.001 | 0.401 | 0.42 | 0.43 | 0.56 | +0.065 (+0.167) | -0.023 (-0.012) | -0.032 (-0.455) |
| HAR+CME+CBOE | -0.189 | -0.157 | 0.370 | 0.46 | 0.42 | 0.54 | -0.078 (+0.045) | -0.181 (+0.016) | -0.063 (-0.010) |
| HAR+CMElite+CBOE | -0.060 | -0.029 | 0.265 | 0.47 | 0.44 | 0.56 | +0.052 (-0.008) | -0.053 (-0.005) | -0.168 (-0.004) |
| HAR+CBOE | -0.092 | -0.128 | 0.271 | 0.46 | 0.45 | 0.56 | +0.019 (-0.009) | -0.152 (-0.005) | -0.162 (+0.000) |
| HAR+CAL | 0.390 | 0.326 | 0.479 | 0.51 | 0.57 | 0.58 | +0.502 (+0.052) | +0.303 (+0.008) | +0.046 (-0.035) |
| COMBINED | 0.297 | 0.258 | 0.440 | 0.61 | 0.55 | 0.62 | +0.409 (+0.053) | +0.234 (-0.005) | +0.007 (-0.046) |
| UW_a | -0.106 | -0.032 | 0.210 | 0.46 | 0.46 | 0.50 | +0.006 | -0.056 | -0.223 |
| UW_b | -0.009 | 0.045 | 0.349 | 0.49 | 0.43 | 0.54 | +0.103 | +0.021 | -0.084 |
| UW_c | 0.072 | 0.063 | 0.243 | 0.51 | 0.48 | 0.53 | +0.183 | +0.039 | -0.190 |

**nyam** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.018 | 0.053 | 0.120 | 0.54 | 0.54 | 0.51 | -0.194 | -0.192 | -0.343 |
| HAR | 0.212 | 0.246 | 0.463 | 0.53 | 0.56 | 0.60 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.192 | 0.249 | 0.472 | 0.45 | 0.56 | 0.58 | -0.020 (-0.006) | +0.004 (-0.002) | +0.009 (-0.009) |
| HAR+CMElite | 0.215 | 0.265 | 0.478 | 0.50 | 0.61 | 0.59 | +0.003 (-0.000) | +0.019 (+0.002) | +0.015 (-0.006) |
| CMElite | 0.179 | 0.215 | 0.355 | 0.51 | 0.57 | 0.58 | -0.033 (+0.000) | -0.030 (+0.000) | -0.108 (+0.000) |
| CME_only | 0.158 | 0.204 | 0.368 | 0.43 | 0.54 | 0.58 | -0.054 (-0.199) | -0.041 (-0.273) | -0.094 (-0.486) |
| HAR+CME+CBOE | 0.159 | 0.238 | 0.452 | 0.42 | 0.53 | 0.57 | -0.053 (-0.028) | -0.008 (-0.015) | -0.011 (-0.007) |
| HAR+CMElite+CBOE | 0.179 | 0.252 | 0.462 | 0.49 | 0.60 | 0.57 | -0.033 (-0.020) | +0.007 (-0.011) | -0.001 (-0.004) |
| HAR+CBOE | 0.143 | 0.232 | 0.465 | 0.50 | 0.58 | 0.59 | -0.069 (-0.015) | -0.013 (-0.006) | +0.002 (-0.001) |
| HAR+CAL | 0.181 | 0.213 | 0.446 | 0.46 | 0.56 | 0.60 | -0.031 (-0.013) | -0.033 (-0.016) | -0.016 (-0.020) |
| COMBINED | 0.126 | 0.212 | 0.433 | 0.41 | 0.54 | 0.57 | -0.086 (-0.039) | -0.034 (-0.033) | -0.030 (-0.027) |
| UW_a | 0.192 | 0.202 | 0.275 | 0.46 | 0.51 | 0.57 | -0.020 | -0.044 | -0.188 |
| UW_b | 0.102 | 0.146 | 0.313 | 0.42 | 0.51 | 0.55 | -0.110 | -0.099 | -0.150 |
| UW_c | 0.004 | 0.078 | 0.290 | 0.41 | 0.49 | 0.52 | -0.208 | -0.168 | -0.173 |

**nyam2** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | 0.065 | 0.082 | 0.069 | 0.54 | 0.52 | 0.54 | -0.260 | -0.203 | -0.427 |
| HAR | 0.325 | 0.285 | 0.496 | 0.51 | 0.55 | 0.60 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.204 | 0.260 | 0.492 | 0.45 | 0.49 | 0.62 | -0.121 (-0.009) | -0.025 (-0.005) | -0.004 (+0.001) |
| HAR+CMElite | 0.357 | 0.310 | 0.505 | 0.46 | 0.53 | 0.62 | +0.032 (+0.003) | +0.025 (+0.000) | +0.009 (-0.001) |
| CMElite | 0.289 | 0.264 | 0.378 | 0.51 | 0.54 | 0.63 | -0.036 (+0.000) | -0.022 (+0.000) | -0.118 (+0.000) |
| CME_only | 0.211 | 0.247 | 0.393 | 0.49 | 0.53 | 0.59 | -0.114 (-0.334) | -0.038 (-0.312) | -0.103 (-0.507) |
| HAR+CME+CBOE | 0.165 | 0.245 | 0.462 | 0.46 | 0.52 | 0.62 | -0.160 (-0.058) | -0.040 (-0.026) | -0.034 (-0.002) |
| HAR+CMElite+CBOE | 0.307 | 0.295 | 0.484 | 0.49 | 0.56 | 0.57 | -0.018 (-0.044) | +0.010 (-0.019) | -0.012 (-0.003) |
| HAR+CBOE | 0.283 | 0.295 | 0.482 | 0.51 | 0.59 | 0.57 | -0.042 (-0.040) | +0.010 (-0.017) | -0.014 (-0.003) |
| HAR+CAL | 0.308 | 0.257 | 0.493 | 0.47 | 0.55 | 0.61 | -0.017 (-0.025) | -0.028 (-0.026) | -0.003 (-0.011) |
| COMBINED | 0.130 | 0.223 | 0.455 | 0.46 | 0.54 | 0.63 | -0.195 (-0.086) | -0.063 (-0.053) | -0.041 (-0.019) |
| UW_a | 0.127 | 0.262 | 0.338 | 0.53 | 0.57 | 0.57 | -0.198 | -0.023 | -0.158 |
| UW_b | 0.052 | 0.204 | 0.341 | 0.46 | 0.51 | 0.59 | -0.274 | -0.081 | -0.155 |
| UW_c | -0.166 | 0.164 | 0.306 | 0.49 | 0.56 | 0.57 | -0.491 | -0.121 | -0.190 |

**nypm** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.083 | 0.010 | 0.091 | 0.37 | 0.41 | 0.53 | +0.047 | -0.146 | -0.259 |
| HAR | -0.129 | 0.156 | 0.349 | 0.48 | 0.53 | 0.47 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.101 | 0.221 | 0.379 | 0.56 | 0.57 | 0.60 | +0.029 (-0.011) | +0.065 (-0.005) | +0.030 (-0.005) |
| HAR+CMElite | -0.121 | 0.227 | 0.352 | 0.55 | 0.57 | 0.58 | +0.008 (+0.007) | +0.071 (-0.001) | +0.002 (-0.001) |
| CMElite | -0.049 | 0.302 | 0.332 | 0.56 | 0.59 | 0.62 | +0.081 (+0.000) | +0.146 (+0.000) | -0.018 (+0.000) |
| CME_only | -0.011 | 0.299 | 0.339 | 0.59 | 0.61 | 0.61 | +0.118 (-0.120) | +0.143 (-0.159) | -0.010 (-0.374) |
| HAR+CME+CBOE | 0.161 | 0.282 | 0.373 | 0.56 | 0.51 | 0.57 | +0.290 (+0.028) | +0.126 (+0.001) | +0.024 (-0.006) |
| HAR+CMElite+CBOE | 0.062 | 0.267 | 0.339 | 0.53 | 0.51 | 0.58 | +0.191 (+0.058) | +0.111 (+0.008) | -0.010 (-0.002) |
| HAR+CBOE | 0.028 | 0.171 | 0.309 | 0.44 | 0.42 | 0.53 | +0.158 (+0.063) | +0.015 (+0.014) | -0.040 (-0.004) |
| HAR+CAL | 0.103 | 0.219 | 0.342 | 0.55 | 0.50 | 0.53 | +0.233 (-0.035) | +0.063 (-0.010) | -0.007 (-0.042) |
| COMBINED | 0.259 | 0.279 | 0.336 | 0.51 | 0.47 | 0.58 | +0.388 (+0.062) | +0.123 (+0.003) | -0.014 (-0.061) |
| UW_a | -0.427 | -0.044 | 0.309 | 0.47 | 0.49 | 0.50 | -0.298 | -0.200 | -0.041 |
| UW_b | -0.496 | -0.024 | 0.283 | 0.47 | 0.49 | 0.52 | -0.367 | -0.180 | -0.066 |
| UW_c | -0.983 | -0.159 | 0.176 | 0.48 | 0.53 | 0.47 | -0.854 | -0.315 | -0.173 |

**late** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| ATR | -0.167 | -0.050 | 0.150 | 0.42 | 0.40 | 0.46 | -0.392 | -0.378 | -0.202 |
| HAR | 0.225 | 0.328 | 0.353 | 0.58 | 0.60 | 0.57 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.375 | 0.446 | 0.589 | 0.60 | 0.62 | 0.64 | +0.151 (-0.006) | +0.118 (+0.004) | +0.237 (-0.002) |
| HAR+CMElite | 0.253 | 0.404 | 0.578 | 0.58 | 0.60 | 0.60 | +0.028 (+0.001) | +0.076 (+0.001) | +0.225 (-0.004) |
| CMElite | 0.143 | 0.361 | 0.527 | 0.52 | 0.53 | 0.63 | -0.081 (+0.000) | +0.032 (+0.000) | +0.174 (+0.000) |
| CME_only | 0.303 | 0.430 | 0.523 | 0.53 | 0.56 | 0.62 | +0.079 (-0.404) | +0.102 (-0.347) | +0.171 (-0.352) |
| HAR+CME+CBOE | 0.464 | 0.494 | 0.609 | 0.63 | 0.63 | 0.67 | +0.239 (+0.015) | +0.166 (+0.009) | +0.256 (-0.000) |
| HAR+CMElite+CBOE | 0.339 | 0.457 | 0.592 | 0.62 | 0.59 | 0.60 | +0.114 (+0.029) | +0.129 (+0.011) | +0.239 (-0.000) |
| HAR+CBOE | 0.399 | 0.417 | 0.504 | 0.62 | 0.60 | 0.56 | +0.175 (+0.028) | +0.088 (+0.014) | +0.151 (+0.001) |
| HAR+CAL | 0.272 | 0.399 | 0.375 | 0.53 | 0.56 | 0.59 | +0.048 (+0.022) | +0.070 (+0.021) | +0.023 (-0.001) |
| COMBINED | 0.482 | 0.528 | 0.597 | 0.63 | 0.62 | 0.67 | +0.257 (+0.062) | +0.199 (+0.039) | +0.245 (+0.006) |
| UW_a | -0.166 | -0.068 | 0.375 | 0.45 | 0.46 | 0.49 | -0.391 | -0.396 | +0.023 |
| UW_b | 0.005 | 0.056 | 0.380 | 0.52 | 0.51 | 0.50 | -0.220 | -0.272 | +0.027 |
| UW_c | -0.100 | 0.087 | 0.308 | 0.51 | 0.51 | 0.47 | -0.324 | -0.241 | -0.044 |


_ES options: $0.00 pulls downloading; NQ-only in this page._

## 4. Reading the table (plain)
- ATR alone is poor everywhere (R2 -0.2 to 0.15). The HAR benchmark is far stronger than ATR and is the right baseline; the UW pages' "gain over ATR" overstated what the options data add.
- **asia**: CME (HAR+CME or +CMElite) adds +0.12 to +0.14 R2 over HAR in L3M and L6M, placebo ~0, but only about +0.02 in older data; UW (b) is better than HAR+CME in L3M and older; VIX-family prior close (HAR+CBOE) reaches 0.39 in L3M. CME LOSES to UW (b) overall in asia by the rule. The overnight CME reading is stale at 18:00 (median age about 2 h).
- **london**: CME adds nothing over HAR; HAR itself is far above UW (b) (UW (b) is about zero in L3M / L6M). CME/HAR BEATS UW. For the London range-used-up rule the HAR forecast is the better input.
- **pre**: calendar flags carry the session (L3M R2 0.37 to 0.47 with flags vs -0.1 without); CME and UW add nothing.
- **nyam / nyam2**: HAR (+CMElite +0.02) beats UW (b) by 0.10 to 0.28 R2; CME is not needed.
- **nypm**: CME adds +0.03 to +0.07 over HAR (rank accuracy 0.54 to 0.55 vs 0.47 to 0.49); UW (b) is negative in L3M. CME BEATS UW.
- **late (last 90 min)**: the CME 0DTE implied vol is the winner: R2 0.34 / 0.43 / 0.40 vs HAR 0.22 / 0.31 / -0.07 and UW (b) 0.00 / 0.06 / 0.38; rank accuracy 0.62 vs 0.52 to 0.60.
- Placebos: with the CME block shifted by 11 / 23 / 37 days the gain over HAR falls to about 0 (e.g. late -0.015 / 0.000 / -0.013 vs real +0.116 / +0.115 / +0.465), so the real gains are not an artefact of the block count.

## 5. Outside vendors (QUOTE ONLY, nothing bought)
- **ORATS** (public pages, as of Nov 2026): Data API plans Delayed $199/mo (20k requests), Live $299, Live Intraday $599, All-In $899; bulk files sold separately: daily history since 2007 from $599, 1-minute intraday since Aug 2020 from $1,500 (their own comparison page; one aggregator shows $99-399/mo, so confirm on orats.com/data-api). It adds: 17 years of daily implied vol surfaces for SPX/NDX/QQQ/single names, a built-in forward (event-stripped) implied volatility and earnings-stripped IV, smoothed-surface ATM vol at every day without our thin-trade problem, and a 2007 start that spans 2008 / 2020 / 2022. It does NOT carry CME NQ futures options; it is the equity-index (NDX, QQQ) option market, i.e. the same family as UW, so it would add history and forward/event-stripped vol but not the direct Globex read.
- **ThetaData** (public pages): Options Value $40/mo, Standard $80/mo, Pro $160/mo (history roughly 4 to 6 yr / 8 to 10 yr / 12 to 14 yr depending on the snapshot; Pro to about 2012; sources disagree, check thetadata.net/pricing). Adds: tick/NBBO quotes (so true bid-ask mid ATM straddles at any minute instead of our trade bars), intraday greeks/IV for SPX/NDX/QQQ options, history before 2023. It also does not carry CME futures options.
- What neither adds that the CME build has: the Globex overnight read from the actual NQ/ES futures options. What the CME build lacks and they have: longer history (we have 3.6 years of NQ options; ORATS 2007+), event-stripped forward vol (we only have E1->E2 forward vol, which isolates the next session but is not stripped of events), and quote-based mids.
- Recommendation: do not buy now; the gain from CME over HAR is concentrated in the last 90 minutes and asia, where the extra history would help the fit more than the vendor numbers. Re-quote if the dials below succeed.

_Engine re-runs (dial 9, one-sided nearer target, London range-used-up on the R2 forecast): queued under tag R2; section appended when results land._

## 6. Caveats
- Model choice per session is by hindsight over 12 models and three windows; the headline beats are large (late, nypm, nyam vs UW) or placebo-clean (CME in asia / late), but the small gaps (+-0.02) are noise. Windows L3M n=74 days is small: R2 differences below 0.1 there are not decisive.
- The variance-time clock, the seasonal profile and the parity de-adjustment factor use data around the same dates (smooth, tiny look-ahead on levels only); the shifted-day placebos do not test that.
- ES options: see section above. UW (b) for asia/london is the prior-close read; the CME read at 18:00/02:00 is later information, which is part of the comparison, as the order intended.
