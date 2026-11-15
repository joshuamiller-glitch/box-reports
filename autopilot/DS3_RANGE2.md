# DS3_RANGE2 - T-RANGE2: a better range forecast than UW (W-R2). Built 2026-11-15T11:25Z. Research only, NO PASS claim.
**VERDICT (plain, page 1 of the forecast part; engine dial re-runs below are still running): the options-market number from CME NQ options, put on top of our own realised-range model (HAR), beats UW (b) in london, nyam, nyam2, nypm, late, matches in none, loses in asia, pre (out-of-sample, R2 in L3M / L6M / older, same sample start as UW). The bigger fact: the HAR realised-range model ALONE already beats UW (b) in london, nyam, nyam2, nypm and (L3M/L6M) late; UW's range signal is mostly an IV-term proxy. CME options add real, placebo-clean gain over HAR in asia (+0.10 to +0.14 R2) and the last 90 minutes (+0.12 to +0.24), small in nypm (+0.03 to +0.07), and nothing in london / nyam. Asia is where UW (b) is still the best single model (its NDX/QQQ/SPX IV term beats our CME read of the same night), so UW is not yet fully replaceable for asia. ES options (pulled at $0.00) add on top of NQ options only in the last 90 minutes (R2 0.45/0.48/0.43 vs 0.34/0.43/0.40) and in nypm for L3M/L6M, nothing elsewhere. Pre (08:30-09:30) is driven by the calendar flags (CPI/NFP/FOMC), not by CME or UW. UW (c) (full UW) is worse than (b) everywhere. Whether UW is still needed: for asia yes (UW b, or Cboe VIX-family inputs, which reach nearly the same R2 free); for london, nyam, nypm, late a HAR + CME (or HAR alone) forecast replaces it. Not a PASS claim; selection of the best model per session is by mean R2 over the three windows (hindsight among ~12 models, see caveats).**

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


## 3c. ES options added (CME ES options: ohlcv-1m + definitions pulled at $0.00, 2023-04..2026-11; same IV pipeline, parity de-adjustment 1.00 to 1.135)
ES coverage: 99.9% of readings have a nearest and a next expiry IV (ES options trade much thicker than NQ). Models: HAR+ES (HAR + ES block), HAR+CME+ES (HAR + NQ block + ES block), HAR+CMElite+ESlite (3+3 columns). Same windows, same sample start as UW (prim).

**Plain result: ES options help only in the last 90 minutes (HAR+CME+ES R2 0.45 / 0.48 / 0.43 vs HAR+CME 0.34 / 0.43 / 0.40 and HAR 0.22 / 0.31 / -0.07; HAR+ES alone 0.49 / 0.47 / 0.38), and in nypm in L3M/L6M (HAR+ES +0.13 / +0.08 over HAR, older -0.03). For asia, london, nyam, nyam2 and pre the ES block adds nothing reliable (changes within +-0.05, shifted-day placebos ~0 to slightly negative).** So the ES read is a late-session input; it does not rescue asia against UW (b).


**asia** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | 0.165 | 0.152 | 0.292 | 0.46 | 0.59 | 0.59 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.287 | 0.253 | 0.305 | 0.50 | 0.57 | 0.63 | +0.122 (-0.005) | +0.101 (-0.007) | +0.013 (-0.011) |
| HAR+CME+ES | 0.296 | 0.206 | 0.299 | 0.47 | 0.54 | 0.60 | +0.131 (-0.008) | +0.053 (-0.006) | +0.007 (-0.021) |
| HAR+ES | 0.294 | 0.122 | 0.332 | 0.47 | 0.52 | 0.60 | +0.129 (+0.001) | -0.030 (-0.002) | +0.040 (-0.012) |
| HAR+CMElite+ESlite | 0.316 | 0.247 | 0.307 | 0.54 | 0.61 | 0.59 | +0.151 (-0.007) | +0.095 (-0.001) | +0.015 (-0.003) |
| HAR+CMElite | 0.306 | 0.277 | 0.310 | 0.53 | 0.59 | 0.60 | +0.142 (+0.004) | +0.124 (+0.002) | +0.018 (-0.001) |
| UW_b | 0.365 | 0.255 | 0.418 | 0.43 | 0.55 | 0.63 | +0.200 | +0.103 | +0.126 |

**london** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | 0.165 | 0.044 | 0.459 | 0.35 | 0.43 | 0.60 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.121 | 0.053 | 0.502 | 0.41 | 0.44 | 0.63 | -0.044 (-0.018) | +0.010 (-0.002) | +0.043 (-0.032) |
| HAR+CME+ES | 0.110 | 0.085 | 0.502 | 0.36 | 0.41 | 0.64 | -0.054 (-0.056) | +0.041 (-0.029) | +0.043 (-0.044) |
| HAR+ES | 0.119 | 0.102 | 0.493 | 0.39 | 0.46 | 0.62 | -0.045 (-0.011) | +0.058 (-0.017) | +0.034 (-0.027) |
| HAR+CMElite+ESlite | 0.124 | 0.090 | 0.495 | 0.42 | 0.44 | 0.67 | -0.041 (-0.030) | +0.047 (-0.017) | +0.036 (-0.016) |
| HAR+CMElite | 0.129 | 0.050 | 0.491 | 0.39 | 0.42 | 0.66 | -0.036 (-0.021) | +0.006 (-0.007) | +0.032 (-0.013) |
| UW_b | 0.011 | -0.015 | 0.349 | 0.36 | 0.44 | 0.64 | -0.154 | -0.059 | -0.110 |

**pre** (n L3M/L6M/OLDER = 74/140/289); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | -0.098 | -0.002 | 0.269 | 0.35 | 0.36 | 0.58 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.114 | -0.021 | 0.043 | 0.36 | 0.38 | 0.54 | -0.016 (+0.043) | -0.019 (+0.026) | -0.226 (-0.019) |
| HAR+CME+ES | -0.348 | -0.171 | -0.130 | 0.42 | 0.38 | 0.58 | -0.250 (+0.030) | -0.169 (+0.000) | -0.399 (-0.042) |
| HAR+ES | -0.310 | -0.152 | -0.064 | 0.43 | 0.42 | 0.55 | -0.212 (-0.007) | -0.150 (-0.005) | -0.332 (-0.054) |
| HAR+CMElite+ESlite | -0.049 | 0.024 | -0.092 | 0.45 | 0.41 | 0.56 | +0.048 (+0.015) | +0.026 (+0.006) | -0.361 (-0.023) |
| HAR+CMElite | -0.036 | 0.040 | -0.008 | 0.41 | 0.39 | 0.55 | +0.061 (+0.009) | +0.042 (+0.009) | -0.277 (-0.014) |
| UW_b | -0.009 | 0.045 | 0.349 | 0.49 | 0.43 | 0.54 | +0.089 | +0.047 | +0.080 |

**nyam** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | 0.223 | 0.245 | 0.394 | 0.50 | 0.54 | 0.61 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.221 | 0.247 | 0.415 | 0.42 | 0.55 | 0.55 | -0.002 (-0.002) | +0.002 (-0.001) | +0.021 (-0.005) |
| HAR+CME+ES | 0.218 | 0.254 | 0.441 | 0.47 | 0.55 | 0.55 | -0.005 (-0.036) | +0.009 (-0.017) | +0.047 (-0.011) |
| HAR+ES | 0.264 | 0.266 | 0.439 | 0.54 | 0.61 | 0.55 | +0.041 (-0.009) | +0.021 (-0.002) | +0.045 (-0.005) |
| HAR+CMElite+ESlite | 0.213 | 0.254 | 0.416 | 0.51 | 0.58 | 0.53 | -0.010 (-0.019) | +0.009 (-0.006) | +0.022 (-0.005) |
| HAR+CMElite | 0.218 | 0.257 | 0.414 | 0.47 | 0.58 | 0.53 | -0.005 (+0.003) | +0.012 (+0.003) | +0.020 (-0.002) |
| UW_b | 0.102 | 0.146 | 0.313 | 0.42 | 0.51 | 0.55 | -0.122 | -0.099 | -0.081 |

**nyam2** (n L3M/L6M/OLDER = 74/140/288); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | 0.329 | 0.289 | 0.489 | 0.46 | 0.52 | 0.55 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.205 | 0.248 | 0.516 | 0.42 | 0.49 | 0.59 | -0.124 (-0.023) | -0.041 (-0.010) | +0.026 (-0.003) |
| HAR+CME+ES | 0.150 | 0.230 | 0.516 | 0.39 | 0.49 | 0.58 | -0.179 (-0.063) | -0.058 (-0.018) | +0.026 (-0.011) |
| HAR+ES | 0.222 | 0.226 | 0.523 | 0.39 | 0.51 | 0.57 | -0.107 (-0.039) | -0.062 (-0.010) | +0.033 (-0.006) |
| HAR+CMElite+ESlite | 0.336 | 0.312 | 0.495 | 0.41 | 0.51 | 0.56 | +0.006 (-0.030) | +0.023 (-0.011) | +0.006 (-0.002) |
| HAR+CMElite | 0.346 | 0.307 | 0.497 | 0.43 | 0.51 | 0.57 | +0.016 (-0.007) | +0.018 (-0.003) | +0.007 (+0.000) |
| UW_b | 0.052 | 0.204 | 0.341 | 0.46 | 0.51 | 0.59 | -0.278 | -0.085 | -0.149 |

**nypm** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | -0.282 | 0.096 | 0.321 | 0.47 | 0.49 | 0.49 | +0.000 | +0.000 | +0.000 |
| HAR+CME | -0.248 | 0.156 | 0.324 | 0.55 | 0.55 | 0.54 | +0.034 (-0.035) | +0.060 (-0.011) | +0.003 (-0.014) |
| HAR+CME+ES | -0.272 | 0.149 | 0.266 | 0.58 | 0.58 | 0.53 | +0.010 (-0.058) | +0.052 (-0.019) | -0.055 (-0.030) |
| HAR+ES | -0.157 | 0.178 | 0.287 | 0.53 | 0.55 | 0.56 | +0.125 (-0.011) | +0.081 (-0.011) | -0.034 (-0.016) |
| HAR+CMElite+ESlite | -0.289 | 0.183 | 0.272 | 0.52 | 0.54 | 0.57 | -0.007 (+0.006) | +0.087 (-0.000) | -0.049 (-0.009) |
| HAR+CMElite | -0.392 | 0.137 | 0.315 | 0.48 | 0.50 | 0.54 | -0.110 (+0.014) | +0.040 (+0.001) | -0.007 (-0.003) |
| UW_b | -0.496 | -0.024 | 0.283 | 0.47 | 0.49 | 0.52 | -0.214 | -0.120 | -0.039 |

**late** (n L3M/L6M/OLDER = 73/136/278); R2 | tercile accuracy | gain over HAR in R2 (placebo mean of 3 shifted-day versions in brackets)

| model | R2 L3M | R2 L6M | R2 OLDER | acc L3M | acc L6M | acc OLDER | gain L3M | gain L6M | gain OLDER |
|---|---|---|---|---|---|---|---|---|---|
| HAR | 0.224 | 0.314 | -0.069 | 0.60 | 0.59 | 0.52 | +0.000 | +0.000 | +0.000 |
| HAR+CME | 0.340 | 0.429 | 0.396 | 0.62 | 0.63 | 0.60 | +0.116 (-0.015) | +0.115 (+0.000) | +0.465 (-0.013) |
| HAR+CME+ES | 0.453 | 0.484 | 0.431 | 0.66 | 0.63 | 0.60 | +0.229 (-0.049) | +0.170 (-0.016) | +0.500 (-0.010) |
| HAR+ES | 0.492 | 0.470 | 0.381 | 0.59 | 0.59 | 0.62 | +0.268 (-0.044) | +0.157 (-0.016) | +0.450 (-0.005) |
| HAR+CMElite+ESlite | 0.352 | 0.451 | 0.394 | 0.59 | 0.58 | 0.59 | +0.128 (-0.001) | +0.137 (-0.005) | +0.463 (-0.011) |
| HAR+CMElite | 0.204 | 0.372 | 0.320 | 0.62 | 0.62 | 0.59 | -0.020 (-0.000) | +0.058 (-0.001) | +0.389 (-0.007) |
| UW_b | 0.005 | 0.056 | 0.380 | 0.52 | 0.51 | 0.50 | -0.219 | -0.258 | +0.449 |



## 3d. Trade-horizon comparison (from W-D10, autopilot/DS3_DIAL10.md; their table, read 2026-11-15, not recomputed here)
They forecast ln(high-low) over the next H minutes (H = causal median holding time of the book+session) at each JN05W2 signal second, walk-forward, R2 / Spearman, on the same trades. Median-horizon R2, window "since 2025-03" / L6M / L3M:
| session | B0 UW (b) start-of-session | B2 this page's v1 (HAR+CME, session start) | M1 own 1-min bars at the signal second | M2 = M1 + v1 + calendar flags |
|---|---|---|---|---|
| asia | 0.32 / 0.26 / 0.12 | 0.36 / 0.33 / 0.16 | 0.49 / 0.46 / 0.27 | 0.49 / 0.46 / 0.28 |
| london | 0.19 / 0.10 / 0.07 | 0.28 / 0.22 / 0.09 | 0.45 / 0.32 / 0.13 | 0.46 / 0.34 / 0.18 |
| nyam | 0.16 / 0.23 / -0.08 | 0.24 / 0.28 / 0.04 | 0.50 / 0.61 / 0.42 | 0.51 / 0.61 / 0.44 |
| nypm | 0.13 / 0.20 / -0.33 | 0.35 / 0.37 / -0.18 | 0.53 / 0.61 / 0.19 | 0.56 / 0.64 / 0.25 |
**Plain reading:** (1) At the trade horizon a forecast built from our own bars at the signal second (M1, R2 0.45 to 0.53 since 2025-03) beats every session-start forecast, including the CME/HAR v1 (0.24 to 0.36) and UW (b) (0.13 to 0.32). The session-start forecast is stale by the time the signal fires; the intraday bars carry the news. (2) The session-start v1 still beats UW (b) at that horizon in all four sessions (+0.04 asia, +0.09 london, +0.08 nyam, +0.22 nypm since 2025-03), consistent with section 3. (3) Does CME add anything at the trade horizon? Almost nothing: M2 minus M1 is 0.00 (asia), +0.01 (london, nyam), +0.03 (nypm) since 2025-03 and +0.00 to +0.06 in L3M; and M2 also carries the calendar flags, so the CME share is at most that. CME options are a session-start input; once the bars at the signal second are used the extra option information is small. No placebo for M2 in their table, so even the small gains are unproven.

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

## 7. Engine re-runs on the R2 forecast (exact engine, JN05W2 base, all layers ON, drawdown first)

Identity: TL3_R2_ID 202610 (hook active at W=60): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

Delta vs JN05W2 on the same months (positive DD = smaller drawdown). Windows need all months present: L3M = 2026-08..10, L6M = 2026-05..10, HOLD = 2025-11..2026-10. Gate = tolerant gate of W-RU (DD and worst week not worse by >2%, mean not lower by >3%), W44 = same with week 2026-W44 removed from both. Forecast: R2 = HAR + CME (fc_r2_v1), HAR = HAR only (ablation).

Lot basis: JN05W2-family sets run at BASE (box) lots, live = x1.75; raw engine net_fee charges $1.18 per contract round trip with the engine fills, not FEES.md $4.84. Column FEES repeats the mean change repriced at $4.84 RT per contract on the change in contracts per week (page code only, no rerun).

| cell | scope | L3M | L6M | HOLD | gate L3M | gate L6M | L6M without W44 | FEES $4.84: d mean $/wk L3M / L6M |
|---|---|---|---|---|---|---|---|---|
| TL3_R2_D9A_C_B | all | +370 $/wk, DD -0.4%, ww +225, stops 10.35(10.35), b5 102%, w2l 0 | -144 $/wk, DD -0.4%, ww +225, stops 10.88(10.99), b5 100%, w2l 0 | n/a | False | False | -152 $/wk, DD -3.5%, ww -1036, stops 10.42(10.54), b5 100%, w2l 0 | +366 / -145 |
| TL3_R2_D9A_C_B | asia | +136 $/wk, DD -8.4%, ww -3577, stops 6.24(6.24), b5 102%, w2l 0 | -523 $/wk, DD -8.4%, ww -3577, stops 6.24(6.35), b5 98%, w2l 0 | n/a | False | False | -387 $/wk, DD -4.3%, ww +231, stops 5.90(6.01), b5 98%, w2l 0 | +134 / -524 |
| TL3_R2_D9A_C_B | london | +592 $/wk, DD +0.7%, ww -5, stops 2.74(2.74), b5 99%, w2l 0 | +778 $/wk, DD +0.7%, ww -5, stops 2.97(2.89), b5 102%, w2l 0 | n/a | True | True | +630 $/wk, DD +0.7%, ww -5, stops 2.89(2.82), b5 102%, w2l 0 | +592 / +778 |
| TL3_R2_D9A_C_B | nyam | +24 $/wk, DD -6.8%, ww -250, stops 1.29(1.29), b5 93%, w2l 0 | -215 $/wk, DD -24.1%, ww -369, stops 1.64(1.67), b5 101%, w2l 1 | n/a | False | False | -351 $/wk, DD -24.1%, ww -369, stops 1.60(1.64), b5 101%, w2l 1 | +22 / -216 |
| TL3_R2_D9A_C_B | nypm | -382 $/wk, DD -27.3%, ww -286, stops 0.08(0.08), b5 100%, w2l 1 | -184 $/wk, DD -27.3%, ww -286, stops 0.04(0.08), b5 107%, w2l 1 | n/a | False | False | -45 $/wk, DD +0.0%, ww +0, stops 0.04(0.08), b5 107%, w2l 1 | -383 / -183 |
| TL3_R2_D9A_C_B_HAR | all | +113 $/wk, DD +6.4%, ww +3343, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | True | None | n/a | +110 / n/a |
| TL3_R2_D9A_C_B_HAR | asia | -412 $/wk, DD -0.9%, ww -435, stops 6.32(6.24), b5 95%, w2l 0 | n/a | n/a | False | None | n/a | -413 / n/a |
| TL3_R2_D9A_C_B_HAR | london | +828 $/wk, DD +4.6%, ww +2502, stops 2.66(2.74), b5 100%, w2l 0 | n/a | n/a | True | None | n/a | +828 / n/a |
| TL3_R2_D9A_C_B_HAR | nyam | -16 $/wk, DD -6.8%, ww -250, stops 1.37(1.29), b5 93%, w2l 0 | n/a | n/a | False | None | n/a | -17 / n/a |
| TL3_R2_D9A_C_B_HAR | nypm | -286 $/wk, DD -28.2%, ww -286, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -288 / n/a |
| TL3_R2_D9A_C_N | all | -114 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -114 / n/a |
| TL3_R2_D9A_C_N | asia | +5 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | +5 / n/a |
| TL3_R2_D9A_C_N | london | -3 $/wk, DD -0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -3 / n/a |
| TL3_R2_D9A_C_N | nyam | -12 $/wk, DD -0.3%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -12 / n/a |
| TL3_R2_D9A_C_N | nypm | -105 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 99%, w2l 1 | n/a | n/a | False | None | n/a | -104 / n/a |
| TL3_R2_D9A_C_N_HAR | all | -13 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -13 / n/a |
| TL3_R2_D9A_C_N_HAR | asia | +0 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | +0 / n/a |
| TL3_R2_D9A_C_N_HAR | london | -1 $/wk, DD -0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -1 / n/a |
| TL3_R2_D9A_C_N_HAR | nyam | -7 $/wk, DD -0.2%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -7 / n/a |
| TL3_R2_D9A_C_N_HAR | nypm | -5 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -5 / n/a |
| TL3_R2_D9A_T1_B | all | -9605 $/wk, DD -78.1%, ww -3267, stops 8.90(10.35), b5 85%, w2l 3 | n/a | n/a | False | None | n/a | -9471 / n/a |
| TL3_R2_D9A_T1_B | asia | -4397 $/wk, DD -15.4%, ww -14649, stops 4.64(6.24), b5 74%, w2l 1 | n/a | n/a | False | None | n/a | -4246 / n/a |
| TL3_R2_D9A_T1_B | london | -6008 $/wk, DD -5.1%, ww +11241, stops 3.12(2.74), b5 50%, w2l 3 | n/a | n/a | False | None | n/a | -5975 / n/a |
| TL3_R2_D9A_T1_B | nyam | +675 $/wk, DD +21.4%, ww -1597, stops 1.14(1.29), b5 57%, w2l 1 | n/a | n/a | False | None | n/a | +641 / n/a |
| TL3_R2_D9A_T1_B | nypm | +125 $/wk, DD -14.4%, ww -4086, stops 0.00(0.08), b5 83%, w2l 1 | n/a | n/a | False | None | n/a | +109 / n/a |
| TL3_R2_D9A_T1_N | all | +1392 $/wk, DD +0.0%, ww +0, stops 10.65(10.35), b5 101%, w2l 0 | +386 $/wk, DD +0.0%, ww +0, stops 11.30(10.99), b5 101%, w2l 1 | -916 $/wk, DD -24.4%, ww +0, stops 11.30(10.66), b5 96%, w2l 3 | True | True | +386 $/wk, DD +22.0%, ww +713, stops 10.84(10.54), b5 101%, w2l 1 | +1311 / +345 |
| TL3_R2_D9A_T1_N | asia | +108 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | +54 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 100%, w2l 1 | -1033 $/wk, DD -0.0%, ww +0, stops 6.04(5.87), b5 97%, w2l 2 | False | False | +54 $/wk, DD +0.0%, ww +0, stops 6.05(6.01), b5 100%, w2l 1 | +101 / +51 |
| TL3_R2_D9A_T1_N | london | +6 $/wk, DD +10.4%, ww +4733, stops 3.04(2.74), b5 102%, w2l 0 | +3 $/wk, DD +10.4%, ww +4733, stops 3.04(2.89), b5 102%, w2l 0 | -228 $/wk, DD -5.2%, ww +4733, stops 2.86(2.61), b5 102%, w2l 1 | True | True | +3 $/wk, DD +10.4%, ww +4733, stops 2.97(2.82), b5 102%, w2l 0 | -28 / -14 |
| TL3_R2_D9A_T1_N | nyam | +791 $/wk, DD +15.7%, ww +20, stops 1.22(1.29), b5 91%, w2l 0 | +101 $/wk, DD -1.2%, ww +0, stops 1.79(1.67), b5 92%, w2l 0 | +307 $/wk, DD +15.7%, ww +4335, stops 2.36(2.15), b5 108%, w2l 0 | True | True | +101 $/wk, DD -1.2%, ww +0, stops 1.75(1.64), b5 92%, w2l 0 | +770 / +89 |
| TL3_R2_D9A_T1_N | nypm | +486 $/wk, DD -13.0%, ww +1545, stops 0.08(0.08), b5 114%, w2l 1 | +228 $/wk, DD -13.0%, ww +1545, stops 0.08(0.08), b5 100%, w2l 1 | +39 $/wk, DD -4.9%, ww +0, stops 0.04(0.04), b5 100%, w2l 3 | False | False | +228 $/wk, DD -13.0%, ww +1545, stops 0.08(0.08), b5 100%, w2l 1 | +468 / +219 |
| TL3_R2_D9S_C_B | all | -521 $/wk, DD -5.5%, ww -2905, stops 10.27(10.35), b5 100%, w2l 0 | -67 $/wk, DD -5.5%, ww -2905, stops 10.77(10.99), b5 101%, w2l 0 | n/a | False | False | +44 $/wk, DD +0.1%, ww -218, stops 10.31(10.54), b5 101%, w2l 0 | -521 / -65 |
| TL3_R2_D9S_C_B | asia | -426 $/wk, DD -6.0%, ww -2905, stops 6.16(6.24), b5 100%, w2l 0 | -191 $/wk, DD -6.0%, ww -2905, stops 6.20(6.35), b5 100%, w2l 0 | n/a | False | False | -81 $/wk, DD -9.3%, ww -2819, stops 5.86(6.01), b5 100%, w2l 0 | -426 / -190 |
| TL3_R2_D9S_C_B | london | +138 $/wk, DD +0.1%, ww +0, stops 2.74(2.74), b5 104%, w2l 0 | +298 $/wk, DD +0.1%, ww +0, stops 2.93(2.89), b5 105%, w2l 0 | n/a | True | True | +298 $/wk, DD +0.1%, ww +0, stops 2.85(2.82), b5 105%, w2l 0 | +138 / +296 |
| TL3_R2_D9S_C_B | nyam | -222 $/wk, DD -7.3%, ww +0, stops 1.29(1.29), b5 93%, w2l 0 | -83 $/wk, DD +5.4%, ww +1161, stops 1.60(1.67), b5 101%, w2l 2 | n/a | False | False | -83 $/wk, DD +5.4%, ww +1161, stops 1.56(1.64), b5 101%, w2l 2 | -222 / -83 |
| TL3_R2_D9S_C_B | nypm | -12 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | -90 $/wk, DD +0.0%, ww +0, stops 0.04(0.08), b5 101%, w2l 0 | n/a | False | False | -90 $/wk, DD +0.0%, ww +0, stops 0.04(0.08), b5 101%, w2l 0 | -12 / -89 |
| TL3_R2_D9S_C_N | all | -20 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -20 / n/a |
| TL3_R2_D9S_C_N | asia | +3 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | +3 / n/a |
| TL3_R2_D9S_C_N | london | -3 $/wk, DD -0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -3 / n/a |
| TL3_R2_D9S_C_N | nyam | -12 $/wk, DD -0.3%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -12 / n/a |
| TL3_R2_D9S_C_N | nypm | -8 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 99%, w2l 0 | n/a | n/a | False | None | n/a | -8 / n/a |
| TL3_R2_D9S_T1_B | all | -6331 $/wk, DD -37.7%, ww +10114, stops 11.95(10.35), b5 95%, w2l 3 | -8813 $/wk, DD -37.7%, ww +10114, stops 8.60(10.99), b5 73%, w2l 4 | n/a | False | False | -9227 $/wk, DD -65.6%, ww -230, stops 8.48(10.54), b5 73%, w2l 4 | -6217 / -8530 |
| TL3_R2_D9S_T1_B | asia | -3526 $/wk, DD +17.7%, ww -8854, stops 4.41(6.24), b5 78%, w2l 1 | -4739 $/wk, DD +7.7%, ww -8854, stops 3.01(6.35), b5 71%, w2l 3 | n/a | False | False | -5064 $/wk, DD -48.4%, ww -9288, stops 2.93(6.01), b5 71%, w2l 3 | -3396 / -4494 |
| TL3_R2_D9S_T1_B | london | -3977 $/wk, DD +14.5%, ww +13917, stops 3.88(2.74), b5 66%, w2l 2 | -2666 $/wk, DD +14.5%, ww +13917, stops 2.78(2.89), b5 62%, w2l 5 | n/a | False | False | -2661 $/wk, DD +14.5%, ww +13917, stops 2.74(2.82), b5 62%, w2l 5 | -3952 / -2609 |
| TL3_R2_D9S_T1_B | nyam | +966 $/wk, DD -18.9%, ww -829, stops 2.43(1.29), b5 77%, w2l 1 | -372 $/wk, DD -65.5%, ww -1209, stops 2.13(1.67), b5 109%, w2l 3 | n/a | False | False | -584 $/wk, DD -65.5%, ww -1209, stops 2.13(1.64), b5 109%, w2l 3 | +939 / -386 |
| TL3_R2_D9S_T1_B | nypm | +206 $/wk, DD +15.6%, ww +271, stops 1.22(0.08), b5 110%, w2l 1 | -1036 $/wk, DD -1.8%, ww +271, stops 0.68(0.08), b5 47%, w2l 4 | n/a | True | False | -918 $/wk, DD -1.8%, ww +967, stops 0.68(0.08), b5 47%, w2l 4 | +192 / -1040 |
| TL3_R2_D9S_T1_N | all | +953 $/wk, DD +0.0%, ww +0, stops 14.99(10.35), b5 104%, w2l 0 | +151 $/wk, DD +0.0%, ww +0, stops 13.54(10.99), b5 104%, w2l 1 | -485 $/wk, DD -7.5%, ww +0, stops 13.75(10.66), b5 103%, w2l 1 | True | True | +151 $/wk, DD -1.4%, ww +713, stops 13.09(10.54), b5 104%, w2l 1 | +881 / +114 |
| TL3_R2_D9S_T1_N | asia | +272 $/wk, DD +0.0%, ww +0, stops 6.39(6.24), b5 100%, w2l 1 | +136 $/wk, DD +0.0%, ww +0, stops 6.43(6.35), b5 100%, w2l 1 | -998 $/wk, DD -0.7%, ww +0, stops 6.23(5.87), b5 99%, w2l 1 | False | False | +136 $/wk, DD +0.0%, ww +0, stops 6.09(6.01), b5 100%, w2l 1 | +267 / +134 |
| TL3_R2_D9S_T1_N | london | -89 $/wk, DD +7.1%, ww +5997, stops 4.18(2.74), b5 106%, w2l 0 | -44 $/wk, DD +7.1%, ww +5997, stops 3.61(2.89), b5 106%, w2l 0 | +219 $/wk, DD +2.3%, ww +5691, stops 3.45(2.61), b5 105%, w2l 0 | True | True | -44 $/wk, DD +7.1%, ww +5997, stops 3.54(2.82), b5 106%, w2l 0 | -119 / -60 |
| TL3_R2_D9S_T1_N | nyam | +624 $/wk, DD -12.8%, ww +345, stops 2.59(1.29), b5 101%, w2l 0 | +9 $/wk, DD -2.2%, ww +0, stops 2.51(1.67), b5 102%, w2l 0 | +301 $/wk, DD +11.5%, ww +4335, stops 3.26(2.15), b5 104%, w2l 0 | False | False | +9 $/wk, DD -2.2%, ww +0, stops 2.47(1.64), b5 102%, w2l 0 | +605 / -1 |
| TL3_R2_D9S_T1_N | nypm | +146 $/wk, DD -22.6%, ww -1637, stops 1.83(0.08), b5 130%, w2l 1 | +50 $/wk, DD -22.6%, ww -1637, stops 0.99(0.08), b5 100%, w2l 1 | -7 $/wk, DD -0.3%, ww -33, stops 0.81(0.04), b5 100%, w2l 1 | False | False | +50 $/wk, DD -22.6%, ww -1637, stops 0.99(0.08), b5 100%, w2l 1 | +128 / +41 |
| TL3_R2_LR1 | all | -2467 $/wk, DD +0.8%, ww +1717, stops 10.04(10.35), b5 91%, w2l 1 | n/a | n/a | False | None | n/a | -2386 / n/a |
| TL3_R2_LR1 | london | -1244 $/wk, DD +32.0%, ww +10574, stops 1.98(2.74), b5 73%, w2l 0 | n/a | n/a | False | None | n/a | -1143 / n/a |
| TL3_R2_LR125 | all | -1282 $/wk, DD +3.0%, ww +1551, stops 9.97(10.35), b5 95%, w2l 0 | n/a | n/a | False | None | n/a | -1218 / n/a |
| TL3_R2_LR125 | london | -513 $/wk, DD +17.6%, ww +10574, stops 2.05(2.74), b5 85%, w2l 0 | n/a | n/a | False | None | n/a | -435 / n/a |
| TL3_R2_LR125_HAR | all | +30 $/wk, DD -5.4%, ww +1551, stops 9.89(10.35), b5 97%, w2l 0 | n/a | n/a | False | None | n/a | +88 / n/a |
| TL3_R2_LR125_HAR | london | +354 $/wk, DD +31.4%, ww +11322, stops 2.05(2.74), b5 90%, w2l 0 | n/a | n/a | True | None | n/a | +427 / n/a |
| TL3_R2_LR1_HAR | all | -761 $/wk, DD -5.2%, ww +1717, stops 9.97(10.35), b5 94%, w2l 0 | n/a | n/a | False | None | n/a | -698 / n/a |
| TL3_R2_LR1_HAR | london | -329 $/wk, DD +33.7%, ww +13238, stops 2.05(2.74), b5 76%, w2l 0 | n/a | n/a | False | None | n/a | -247 / n/a |
| TL3_R2_OS10_5 | all | +42 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 98%, w2l 0 | -2 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 99%, w2l 0 | n/a | False | False | -2 $/wk, DD -0.9%, ww +591, stops 10.54(10.54), b5 99%, w2l 0 | +38 / -4 |
| TL3_R2_OS10_5 | asia | +407 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | +203 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | False | False | +203 $/wk, DD +0.0%, ww +0, stops 6.01(6.01), b5 100%, w2l 0 | +405 / +203 |
| TL3_R2_OS10_5 | london | -197 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | -98 $/wk, DD +0.0%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | False | False | -98 $/wk, DD +0.0%, ww +0, stops 2.82(2.82), b5 100%, w2l 0 | -197 / -99 |
| TL3_R2_OS10_5 | nyam | +152 $/wk, DD +6.8%, ww +658, stops 1.29(1.29), b5 98%, w2l 0 | +53 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | True | True | +53 $/wk, DD +0.0%, ww +0, stops 1.64(1.64), b5 100%, w2l 0 | +152 / +53 |
| TL3_R2_OS10_5 | nypm | -320 $/wk, DD -16.2%, ww -398, stops 0.08(0.08), b5 92%, w2l 3 | -160 $/wk, DD -16.2%, ww -398, stops 0.08(0.08), b5 100%, w2l 3 | n/a | False | False | -160 $/wk, DD -16.2%, ww -398, stops 0.08(0.08), b5 100%, w2l 3 | -322 / -161 |
| TL3_R2_OS10_67 | all | +233 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | False | None | n/a | +231 / n/a |
| TL3_R2_OS10_67 | asia | +327 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | +325 / n/a |
| TL3_R2_OS10_67 | london | -140 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | -140 / n/a |
| TL3_R2_OS10_67 | nyam | +206 $/wk, DD +6.8%, ww +658, stops 1.29(1.29), b5 98%, w2l 0 | n/a | n/a | True | None | n/a | +207 / n/a |
| TL3_R2_OS10_67 | nypm | -160 $/wk, DD -0.0%, ww +1652, stops 0.08(0.08), b5 80%, w2l 3 | n/a | n/a | False | None | n/a | -161 / n/a |
| TL3_R2_OS3_5 | all | -1153 $/wk, DD +0.0%, ww +0, stops 10.20(10.35), b5 91%, w2l 0 | n/a | n/a | False | None | n/a | -1182 / n/a |
| TL3_R2_OS3_5 | asia | +45 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | n/a | n/a | False | None | n/a | +43 / n/a |
| TL3_R2_OS3_5 | london | -553 $/wk, DD -0.4%, ww +4295, stops 2.74(2.74), b5 101%, w2l 1 | n/a | n/a | False | None | n/a | -567 / n/a |
| TL3_R2_OS3_5 | nyam | -269 $/wk, DD +7.0%, ww +1274, stops 1.07(1.29), b5 70%, w2l 1 | n/a | n/a | False | None | n/a | -273 / n/a |
| TL3_R2_OS3_5 | nypm | -377 $/wk, DD -7.1%, ww +843, stops 0.08(0.08), b5 90%, w2l 4 | n/a | n/a | False | None | n/a | -386 / n/a |
| TL3_R2_OS3_67 | all | -244 $/wk, DD +0.0%, ww +0, stops 10.27(10.35), b5 96%, w2l 0 | n/a | n/a | False | None | n/a | -260 / n/a |
| TL3_R2_OS3_67 | asia | -35 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | n/a | n/a | False | None | n/a | -37 / n/a |
| TL3_R2_OS3_67 | london | -118 $/wk, DD +9.4%, ww +5780, stops 2.74(2.74), b5 104%, w2l 0 | n/a | n/a | False | None | n/a | -128 / n/a |
| TL3_R2_OS3_67 | nyam | +35 $/wk, DD +2.6%, ww +1274, stops 1.14(1.29), b5 81%, w2l 1 | n/a | n/a | True | None | n/a | +34 / n/a |
| TL3_R2_OS3_67 | nypm | -125 $/wk, DD -2.0%, ww +1547, stops 0.08(0.08), b5 93%, w2l 4 | n/a | n/a | False | None | n/a | -129 / n/a |
| TL3_R2_OS3_67_HAR | all | -1212 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 95%, w2l 0 | n/a | n/a | False | None | n/a | -1221 / n/a |
| TL3_R2_OS3_67_HAR | asia | +0 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | False | None | n/a | +0 / n/a |
| TL3_R2_OS3_67_HAR | london | -871 $/wk, DD -8.5%, ww +0, stops 2.74(2.74), b5 99%, w2l 0 | n/a | n/a | False | None | n/a | -875 / n/a |
| TL3_R2_OS3_67_HAR | nyam | +75 $/wk, DD -0.2%, ww +475, stops 1.29(1.29), b5 93%, w2l 0 | n/a | n/a | False | None | n/a | +73 / n/a |
| TL3_R2_OS3_67_HAR | nypm | -416 $/wk, DD -8.0%, ww +743, stops 0.08(0.08), b5 71%, w2l 4 | n/a | n/a | False | None | n/a | -419 / n/a |
| TL3_R2_OS3_8 | all | -666 $/wk, DD +0.0%, ww +0, stops 10.27(10.35), b5 95%, w2l 0 | n/a | n/a | False | None | n/a | -677 / n/a |
| TL3_R2_OS3_8 | asia | +334 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | n/a | n/a | False | None | n/a | +335 / n/a |
| TL3_R2_OS3_8 | london | -316 $/wk, DD -0.3%, ww +3016, stops 2.74(2.74), b5 102%, w2l 1 | n/a | n/a | False | None | n/a | -321 / n/a |
| TL3_R2_OS3_8 | nyam | -319 $/wk, DD -11.2%, ww -1200, stops 1.14(1.29), b5 88%, w2l 1 | n/a | n/a | False | None | n/a | -323 / n/a |
| TL3_R2_OS3_8 | nypm | -365 $/wk, DD -2.2%, ww +0, stops 0.08(0.08), b5 75%, w2l 3 | n/a | n/a | False | None | n/a | -368 / n/a |
| TL3_R2_OS5_5 | all | -1233 $/wk, DD +0.0%, ww +0, stops 10.42(10.35), b5 93%, w2l 0 | -639 $/wk, DD +0.0%, ww +0, stops 11.03(10.99), b5 98%, w2l 0 | n/a | False | False | -639 $/wk, DD -6.6%, ww -908, stops 10.58(10.54), b5 98%, w2l 0 | -1249 / -647 |
| TL3_R2_OS5_5 | asia | +45 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | +22 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 100%, w2l 1 | n/a | False | False | +22 $/wk, DD +0.0%, ww +0, stops 6.05(6.01), b5 100%, w2l 1 | +43 / +22 |
| TL3_R2_OS5_5 | london | -837 $/wk, DD -10.7%, ww +0, stops 2.74(2.74), b5 99%, w2l 1 | -419 $/wk, DD -10.7%, ww +0, stops 2.89(2.89), b5 99%, w2l 1 | n/a | False | False | -419 $/wk, DD -10.7%, ww +0, stops 2.82(2.82), b5 99%, w2l 1 | -845 / -423 |
| TL3_R2_OS5_5 | nyam | +46 $/wk, DD +0.4%, ww +1274, stops 1.29(1.29), b5 95%, w2l 0 | -0 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | True | True | -0 $/wk, DD +0.0%, ww +0, stops 1.64(1.64), b5 100%, w2l 0 | +44 / -1 |
| TL3_R2_OS5_5 | nypm | -486 $/wk, DD -15.7%, ww +843, stops 0.08(0.08), b5 74%, w2l 4 | -243 $/wk, DD -15.7%, ww +843, stops 0.08(0.08), b5 100%, w2l 4 | n/a | False | False | -243 $/wk, DD -15.7%, ww +843, stops 0.08(0.08), b5 100%, w2l 4 | -491 / -246 |
| TL3_R2_OS5_67 | all | -949 $/wk, DD +0.0%, ww +0, stops 10.50(10.35), b5 96%, w2l 0 | n/a | n/a | False | None | n/a | -959 / n/a |
| TL3_R2_OS5_67 | asia | -35 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 100%, w2l 1 | n/a | n/a | False | None | n/a | -37 / n/a |
| TL3_R2_OS5_67 | london | -561 $/wk, DD -6.7%, ww +0, stops 2.74(2.74), b5 99%, w2l 0 | n/a | n/a | False | None | n/a | -566 / n/a |
| TL3_R2_OS5_67 | nyam | -7 $/wk, DD -8.2%, ww +1274, stops 1.37(1.29), b5 98%, w2l 0 | n/a | n/a | False | None | n/a | -7 / n/a |
| TL3_R2_OS5_67 | nypm | -346 $/wk, DD -2.0%, ww +1547, stops 0.08(0.08), b5 77%, w2l 4 | n/a | n/a | False | None | n/a | -349 / n/a |
| TL3_R2_PL11_D9A_T1_N | all | -1270 $/wk, DD -25.2%, ww -18090, stops 10.12(10.35), b5 100%, w2l 0 | -1436 $/wk, DD -25.2%, ww -18090, stops 10.99(10.99), b5 101%, w2l 0 | -1278 $/wk, DD -4.8%, ww +685, stops 10.85(10.66), b5 90%, w2l 2 | False | False | -1499 $/wk, DD -50.7%, ww -28435, stops 10.54(10.54), b5 101%, w2l 0 | -1332 / -1474 |
| TL3_R2_PL11_D9A_T1_N | asia | +1072 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 107%, w2l 0 | +536 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 105%, w2l 0 | -596 $/wk, DD +2.2%, ww +0, stops 5.98(5.87), b5 87%, w2l 0 | False | False | +536 $/wk, DD +0.0%, ww +0, stops 6.01(6.01), b5 105%, w2l 0 | +1059 / +530 |
| TL3_R2_PL11_D9A_T1_N | london | -1476 $/wk, DD -22.1%, ww +0, stops 2.59(2.74), b5 105%, w2l 0 | -639 $/wk, DD -22.1%, ww +0, stops 2.82(2.89), b5 105%, w2l 0 | -35 $/wk, DD -22.1%, ww +0, stops 2.65(2.61), b5 104%, w2l 2 | False | False | -639 $/wk, DD -22.1%, ww +0, stops 2.74(2.82), b5 105%, w2l 0 | -1501 / -653 |
| TL3_R2_PL11_D9A_T1_N | nyam | -673 $/wk, DD +0.1%, ww -665, stops 1.22(1.29), b5 84%, w2l 1 | -1368 $/wk, DD +1.0%, ww +0, stops 1.75(1.67), b5 51%, w2l 3 | -463 $/wk, DD +26.3%, ww +0, stops 2.17(2.15), b5 73%, w2l 2 | False | False | -1430 $/wk, DD +1.0%, ww +0, stops 1.71(1.64), b5 51%, w2l 3 | -690 / -1380 |
| TL3_R2_PL11_D9A_T1_N | nypm | -193 $/wk, DD -14.5%, ww +704, stops 0.08(0.08), b5 69%, w2l 3 | +34 $/wk, DD -14.5%, ww +704, stops 0.08(0.08), b5 115%, w2l 3 | -185 $/wk, DD -38.3%, ww +420, stops 0.06(0.04), b5 115%, w2l 5 | False | False | +34 $/wk, DD -14.5%, ww +704, stops 0.08(0.08), b5 115%, w2l 3 | -199 / +30 |
| TL3_R2_PL11_D9S_T1_N | all | -415 $/wk, DD -0.3%, ww +114, stops 12.93(10.35), b5 102%, w2l 0 | -648 $/wk, DD -0.3%, ww +114, stops 12.78(10.99), b5 102%, w2l 0 | -490 $/wk, DD -5.2%, ww +3222, stops 13.69(10.66), b5 94%, w2l 2 | False | False | -652 $/wk, DD -20.6%, ww -6825, stops 12.25(10.54), b5 102%, w2l 0 | -475 / -684 |
| TL3_R2_PL11_D9S_T1_N | asia | +790 $/wk, DD +0.0%, ww +0, stops 6.32(6.24), b5 105%, w2l 0 | +395 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 104%, w2l 0 | -317 $/wk, DD +2.2%, ww +0, stops 6.23(5.87), b5 93%, w2l 0 | False | False | +395 $/wk, DD +0.0%, ww +0, stops 6.05(6.01), b5 104%, w2l 0 | +779 / +389 |
| TL3_R2_PL11_D9S_T1_N | london | -1331 $/wk, DD -14.9%, ww +0, stops 4.03(2.74), b5 102%, w2l 1 | -589 $/wk, DD -14.9%, ww +0, stops 3.58(2.89), b5 102%, w2l 1 | -40 $/wk, DD -14.9%, ww +0, stops 3.59(2.61), b5 102%, w2l 1 | False | False | -589 $/wk, DD -14.9%, ww +0, stops 3.50(2.82), b5 102%, w2l 1 | -1358 / -603 |
| TL3_R2_PL11_D9S_T1_N | nyam | +167 $/wk, DD +8.9%, ww -160, stops 1.83(1.29), b5 97%, w2l 1 | -529 $/wk, DD +1.0%, ww +0, stops 2.36(1.67), b5 76%, w2l 2 | +12 $/wk, DD +17.7%, ww -573, stops 3.13(2.15), b5 87%, w2l 2 | True | False | -533 $/wk, DD +1.0%, ww +0, stops 2.24(1.64), b5 76%, w2l 2 | +150 / -541 |
| TL3_R2_PL11_D9S_T1_N | nypm | -41 $/wk, DD -12.4%, ww +759, stops 0.76(0.08), b5 104%, w2l 3 | +75 $/wk, DD -12.4%, ww +759, stops 0.46(0.08), b5 112%, w2l 3 | -145 $/wk, DD -34.8%, ww +564, stops 0.75(0.04), b5 112%, w2l 4 | False | False | +75 $/wk, DD -12.4%, ww +759, stops 0.46(0.08), b5 112%, w2l 3 | -46 / +70 |
| TL3_R2_PL23_D9A_T1_N | all | +154 $/wk, DD +0.0%, ww +0, stops 10.58(10.35), b5 103%, w2l 0 | +252 $/wk, DD +0.0%, ww +0, stops 11.49(10.99), b5 109%, w2l 1 | +517 $/wk, DD +14.9%, ww +3222, stops 11.16(10.66), b5 96%, w2l 2 | False | False | +252 $/wk, DD +0.0%, ww -1016, stops 11.03(10.54), b5 109%, w2l 1 | +127 / +228 |
| TL3_R2_PL23_D9A_T1_N | asia | +0 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | +403 $/wk, DD +2.2%, ww +0, stops 5.93(5.87), b5 96%, w2l 0 | False | False | +0 $/wk, DD +0.0%, ww +0, stops 6.01(6.01), b5 100%, w2l 0 | +0 / +0 |
| TL3_R2_PL23_D9A_T1_N | london | +47 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 102%, w2l 0 | +288 $/wk, DD +0.0%, ww +0, stops 3.04(2.89), b5 102%, w2l 0 | +170 $/wk, DD +0.0%, ww +0, stops 2.78(2.61), b5 101%, w2l 2 | False | False | +288 $/wk, DD +0.0%, ww +0, stops 2.97(2.82), b5 102%, w2l 0 | +34 / +276 |
| TL3_R2_PL23_D9A_T1_N | nyam | -249 $/wk, DD -48.1%, ww +0, stops 1.52(1.29), b5 102%, w2l 2 | -448 $/wk, DD -15.5%, ww +0, stops 2.02(1.67), b5 105%, w2l 2 | -152 $/wk, DD +22.9%, ww +4335, stops 2.40(2.15), b5 96%, w2l 6 | False | False | -448 $/wk, DD -15.5%, ww +0, stops 1.98(1.64), b5 105%, w2l 2 | -257 / -454 |
| TL3_R2_PL23_D9A_T1_N | nypm | +356 $/wk, DD -29.4%, ww +0, stops 0.08(0.08), b5 145%, w2l 1 | +411 $/wk, DD -29.4%, ww +0, stops 0.08(0.08), b5 118%, w2l 1 | +97 $/wk, DD -26.3%, ww -28, stops 0.06(0.04), b5 118%, w2l 3 | False | False | +411 $/wk, DD -29.4%, ww +0, stops 0.08(0.08), b5 118%, w2l 1 | +350 / +407 |
| TL3_R2_PL23_D9S_T1_N | all | +133 $/wk, DD +0.0%, ww +0, stops 12.33(10.35), b5 103%, w2l 0 | +108 $/wk, DD +0.0%, ww +0, stops 12.97(10.99), b5 108%, w2l 1 | -93 $/wk, DD +2.9%, ww +3222, stops 14.13(10.66), b5 100%, w2l 4 | False | False | +108 $/wk, DD +0.0%, ww -5485, stops 12.52(10.54), b5 108%, w2l 1 | +110 / +87 |
| TL3_R2_PL23_D9S_T1_N | asia | +0 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | -554 $/wk, DD +2.2%, ww +0, stops 6.64(5.87), b5 99%, w2l 1 | False | False | +0 $/wk, DD +0.0%, ww +0, stops 6.01(6.01), b5 100%, w2l 0 | +0 / +0 |
| TL3_R2_PL23_D9S_T1_N | london | -432 $/wk, DD +0.0%, ww +0, stops 3.58(2.74), b5 95%, w2l 0 | -3 $/wk, DD +0.0%, ww +0, stops 3.77(2.89), b5 95%, w2l 0 | +153 $/wk, DD +0.0%, ww +0, stops 4.07(2.61), b5 96%, w2l 3 | False | False | -3 $/wk, DD +0.0%, ww +0, stops 3.69(2.82), b5 95%, w2l 0 | -444 / -15 |
| TL3_R2_PL23_D9S_T1_N | nyam | -181 $/wk, DD -40.2%, ww -1126, stops 2.21(1.29), b5 108%, w2l 1 | -466 $/wk, DD -9.3%, ww +0, stops 2.55(1.67), b5 105%, w2l 2 | +6 $/wk, DD +31.3%, ww +3596, stops 3.05(2.15), b5 100%, w2l 5 | False | False | -466 $/wk, DD -9.3%, ww +0, stops 2.51(1.64), b5 105%, w2l 2 | -189 / -472 |
| TL3_R2_PL23_D9S_T1_N | nypm | +747 $/wk, DD +18.7%, ww +0, stops 0.30(0.08), b5 183%, w2l 1 | +577 $/wk, DD +18.7%, ww +0, stops 0.30(0.08), b5 117%, w2l 1 | +301 $/wk, DD +7.1%, ww +0, stops 0.38(0.04), b5 117%, w2l 3 | True | True | +577 $/wk, DD +18.7%, ww +0, stops 0.30(0.08), b5 117%, w2l 1 | +743 / +574 |
| TL3_R2_PL37_D9A_T1_N | all | +762 $/wk, DD +11.0%, ww +5729, stops 10.27(10.35), b5 102%, w2l 0 | -404 $/wk, DD +11.0%, ww +5729, stops 10.99(10.99), b5 101%, w2l 0 | -1139 $/wk, DD -10.6%, ww +3222, stops 11.22(10.66), b5 101%, w2l 3 | True | True | -622 $/wk, DD +0.0%, ww +0, stops 10.54(10.54), b5 101%, w2l 0 | +744 / -417 |
| TL3_R2_PL37_D9A_T1_N | asia | +0 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | -896 $/wk, DD -11.0%, ww +0, stops 6.14(5.87), b5 100%, w2l 3 | False | False | +0 $/wk, DD +0.0%, ww +0, stops 6.01(6.01), b5 100%, w2l 0 | +0 / +0 |
| TL3_R2_PL37_D9A_T1_N | london | -18 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 98%, w2l 0 | +72 $/wk, DD +0.0%, ww +0, stops 2.85(2.89), b5 100%, w2l 0 | -197 $/wk, DD -4.1%, ww +0, stops 2.78(2.61), b5 97%, w2l 1 | False | False | -5 $/wk, DD +0.0%, ww +0, stops 2.78(2.82), b5 100%, w2l 0 | -34 / +61 |
| TL3_R2_PL37_D9A_T1_N | nyam | +547 $/wk, DD +6.8%, ww +0, stops 1.22(1.29), b5 100%, w2l 0 | -246 $/wk, DD -8.7%, ww +0, stops 1.71(1.67), b5 99%, w2l 1 | +40 $/wk, DD +47.2%, ww +4335, stops 2.24(2.15), b5 91%, w2l 4 | True | False | -388 $/wk, DD -8.7%, ww +0, stops 1.67(1.64), b5 99%, w2l 1 | +546 / -249 |
| TL3_R2_PL37_D9A_T1_N | nypm | +234 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 123%, w2l 0 | -229 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 75%, w2l 0 | -86 $/wk, DD -1.6%, ww +1798, stops 0.06(0.04), b5 75%, w2l 0 | False | False | -229 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 75%, w2l 0 | +233 / -228 |

Cells with results: 27. Placebo cells (forecast shifted 11/23/37 days) are named TL3_R2_PL*; a lead needs to beat them.


## 6. Caveats
- Model choice per session is by hindsight over 12 models and three windows; the headline beats are large (late, nypm, nyam vs UW) or placebo-clean (CME in asia / late), but the small gaps (+-0.02) are noise. Windows L3M n=74 days is small: R2 differences below 0.1 there are not decisive.
- The variance-time clock, the seasonal profile and the parity de-adjustment factor use data around the same dates (smooth, tiny look-ahead on levels only); the shifted-day placebos do not test that.
- ES options: see section above. UW (b) for asia/london is the prior-close read; the CME read at 18:00/02:00 is later information, which is part of the comparison, as the order intended.
