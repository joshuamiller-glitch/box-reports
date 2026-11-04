

## S4b - tape / L2 microstructure of NQ by quarter and around 2025-10-23 (2026-11-04 19:11Z)
Prereg autopilot/Q4_S4B_PREREG.md (sha256 in DECISIONS.md; one logged deviation before any outcome: the absorption threshold 10 saturates at 0.999, so the series is the share of seconds with ratio >= 100). Append-only; Shadow only. Data: 1-s L2 tables, NQ 20230201..20261030 label days (967), ES 839 days, RTY 839 days (2023-08..2026-10-30); windows PRE 09:00-09:29, OPEN 09:30-09:59, MID 10:00-11:29 ET; 17 series x 2 windows. Code l2vast/ds3/code/q4/ (q4_micro.py, q4_analyze.py, q4_refine.py); daily series /mnt/l2/l2vast/ds3_q4/micro.parquet, quarterly means quarterly.csv, tests shift_tests.csv / predict_tests.csv / predict_refined.csv. n_tested = 85 shift / DiD tests (33 series-windows x 3 instruments counted as in the prereg, 17 x 2 DiD) + 78 prediction tests (39 predictors x 2 targets; the prereg said 38 predictors, the pre-open set has 6 and the previous-day set 33).
### 1. NQ by quarter (daily means of the window values; units: spread in ticks, depth in contracts, shares are fractions, rate in prints/s, absorb = share of seconds with 30-s depletion >= 100 x best size, resil = depth5 at t+5s / t-1 after sweeps)
| quarter | O.spread | O.tob | O.depth5 | O.msize | O.big1 | O.sweep | O.imb | O.persist | O.can_add1 | O.refill | O.rate | O.surge | O.absorb | O.resil | M.spread | M.depth5 | M.big1 | M.can_add1 | M.rate |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2023Q1 | 2.35 | 5.53 | 54.3 | 1.53 | 0.0431 | 0.214 | 0.0164 | 0.129 | 1.08 | 0.438 | 23.8 | 8.42 | 0.886 | 1.03 | 2.08 | 64.2 | 0.0526 | 1.09 | 15.5 |
| 2023Q2 | 1.73 | 8.25 | 70.8 | 1.6 | 0.0429 | 0.176 | 0.0198 | 0.14 | 1.09 | 0.493 | 26.5 | 12.2 | 0.793 | 1.02 | 1.68 | 79.4 | 0.0539 | 1.08 | 15.6 |
| 2023Q3 | 1.93 | 6.32 | 55.3 | 1.53 | 0.0326 | 0.199 | 0.0188 | 0.107 | 1.15 | 0.476 | 28.2 | 11.6 | 0.901 | 1.02 | 1.84 | 65.1 | 0.0406 | 1.16 | 15.7 |
| 2023Q4 | 1.82 | 6.81 | 62 | 1.56 | 0.0387 | 0.203 | 0.0196 | 0.113 | 1.13 | 0.471 | 27 | 10 | 0.844 | 1.02 | 1.76 | 70.7 | 0.0475 | 1.15 | 16.2 |
| 2024Q1 | 1.89 | 6.44 | 59.7 | 1.54 | 0.0349 | 0.205 | 0.0186 | 0.115 | 1.17 | 0.48 | 28.1 | 10.9 | 0.89 | 1.02 | 1.82 | 66.4 | 0.0426 | 1.2 | 15.7 |
| 2024Q2 | 1.89 | 6.02 | 59.5 | 1.5 | 0.0333 | 0.192 | 0.0193 | 0.14 | 1.18 | 0.481 | 27.2 | 10.7 | 0.882 | 1.02 | 1.84 | 65.6 | 0.0421 | 1.2 | 15.2 |
| 2024Q3 | 2.74 | 4.43 | 40.5 | 1.42 | 0.0246 | 0.223 | 0.0182 | 0.0857 | 1.09 | 0.406 | 26.5 | 11.1 | 0.926 | 1.02 | 2.54 | 44.9 | 0.0291 | 1.14 | 17.1 |
| 2024Q4 | 2.52 | 4.29 | 43.3 | 1.45 | 0.0292 | 0.254 | 0.0211 | 0.115 | 1.18 | 0.419 | 23.1 | 9.91 | 0.914 | 1.02 | 2.32 | 48.8 | 0.0352 | 1.21 | 14 |
| 2025Q1 | 3.07 | 3.94 | 36.4 | 1.4 | 0.0231 | 0.266 | 0.021 | 0.0561 | 1.09 | 0.378 | 26.9 | 8.87 | 0.94 | 1.03 | 2.81 | 40.3 | 0.0243 | 1.13 | 17.1 |
| 2025Q2 | 3.52 | 3.73 | 31.2 | 1.37 | 0.0249 | 0.262 | 0.0154 | 0.027 | 1.08 | 0.339 | 22.6 | 8.78 | 0.902 | 1.03 | 3.16 | 37.1 | 0.026 | 1.12 | 14 |
| 2025Q3 | 2.41 | 4.95 | 41.9 | 1.47 | 0.0277 | 0.245 | 0.0223 | 0.103 | 1.08 | 0.389 | 22.9 | 12.9 | 0.842 | 1.02 | 2.18 | 54 | 0.0308 | 1.12 | 12.9 |
| 2025Q4 | 2.87 | 4.53 | 40.4 | 1.46 | 0.0285 | 0.265 | 0.0183 | 0.0909 | 1.05 | 0.364 | 25.7 | 11.3 | 0.897 | 1.03 | 2.54 | 49.9 | 0.0278 | 1.08 | 15.3 |
| 2026Q1 | 3.29 | 3.58 | 32.2 | 1.38 | 0.0255 | 0.279 | 0.0188 | 0.0578 | 1.04 | 0.35 | 27.9 | 12.3 | 0.945 | 1.03 | 2.88 | 40.6 | 0.0263 | 1.09 | 15.5 |
| 2026Q2 | 3.86 | 3.57 | 30.4 | 1.38 | 0.0248 | 0.296 | 0.0203 | 0.0613 | 1.02 | 0.304 | 26.8 | 10.5 | 0.93 | 1.03 | 3.4 | 36 | 0.0276 | 1.07 | 15.6 |
| 2026Q3 | 3.49 | 3.21 | 29 | 1.32 | 0.0233 | 0.248 | 0.016 | 0.094 | 1.04 | 0.35 | 28.2 | 12.4 | 0.95 | 1.03 | 3.09 | 34.7 | 0.0224 | 1.1 | 15.3 |
| 2026Q4 | 2.75 | 3.4 | 31.3 | 1.33 | 0.0175 | 0.219 | 0.0111 | 0.115 | 1.07 | 0.45 | 36 | 13 | 0.99 | 1.03 | 2.46 | 37.7 | 0.0211 | 1.13 | 18.1 |
### 2. Which series shift at 2025-10-23, and is it NQ-only? (120 label days after vs the 120 before, standardised by the pooled day SD; placebo = 107 break dates 2024-02..2025-04, every third day; p = share of placebo dates with |z| >= the real one)
| series | NQ z | ES z | RTY z | NQ minus ES | NQ minus RTY | placebo-date p (NQ) | p (NQ-ES) | p (NQ-RTY) | NQ mean before -> after |
|---|---|---|---|---|---|---|---|---|---|
| OPEN_spread | +0.88 | +0.98 | +1.01 | -0.10 | -0.12 | 0.19 | 0.66 | 0.71 | 2.61 -> 3.16 |
| OPEN_tob | -0.78 | -1.04 | -0.81 | +0.26 | +0.03 | 0.57 | 0.71 | 0.99 | 4.61 -> 3.93 |
| OPEN_depth5 | -0.50 | -0.92 | -0.50 | +0.43 | +0.01 | 0.88 | 0.17 | 0.99 | 39.4 -> 35.1 |
| OPEN_msize | -0.44 | -0.78 | -0.54 | +0.33 | +0.10 | 0.87 | 0.66 | 0.92 | 1.44 -> 1.41 |
| OPEN_big1 | -0.11 | -0.94 | -0.15 | +0.84 | +0.04 | 0.94 | 0.21 | 0.85 | 0.0281 -> 0.0271 |
| OPEN_big2 | +0.31 | -0.59 | +0.01 | +0.89 | +0.30 | 0.65 | 0.34 | 0.58 | 0.00958 -> 0.0117 |
| OPEN_sweep | +0.78 | +0.61 | +0.35 | +0.17 | +0.43 | 0.50 | 0.84 | 0.78 | 0.252 -> 0.276 |
| OPEN_imb | -0.11 | +0.11 | -0.56 | -0.23 | +0.44 | 0.28 | 0.03 | 0.01 | 0.0205 -> 0.0189 |
| OPEN_persist | -0.05 | +0.04 | +0.21 | -0.09 | -0.26 | 0.89 | 0.90 | 0.48 | 0.0778 -> 0.0733 |
| OPEN_can_add1 | -0.82 | +1.14 | -0.15 | -1.97 | -0.67 | 0.03 | 0.01 | 0.44 | 1.09 -> 1.04 |
| OPEN_can_add23 | +0.86 | -0.60 | +0.50 | +1.46 | +0.35 | 0.34 | 0.42 | 0.50 | 0.797 -> 0.947 |
| OPEN_refill | -0.61 | +1.43 | +0.43 | -2.04 | -1.04 | 0.69 | 0.11 | 0.46 | 0.378 -> 0.351 |
| OPEN_refail | +0.03 | -0.12 | +0.06 | +0.15 | -0.03 | 0.98 | 0.87 | 0.92 | 0.000311 -> 0.000324 |
| OPEN_rate | +0.63 | +0.83 | +0.73 | -0.20 | -0.10 | 0.07 | 0.81 | 0.73 | 21.9 -> 26.7 |
| OPEN_absorb | +0.37 | +1.35 | +0.99 | -0.98 | -0.62 | 0.05 | 0.01 | 0.14 | 0.854 -> 0.922 |
| OPEN_resil | +0.54 | +0.23 | -0.15 | +0.31 | +0.69 | 0.09 | 0.31 | 0.03 | 1.02 -> 1.03 |
| MID_spread | +0.82 | +0.74 | +1.08 | +0.08 | -0.26 | 0.29 | 0.62 | 0.61 | 2.35 -> 2.77 |
| MID_tob | -0.69 | -0.76 | -0.60 | +0.07 | -0.08 | 0.61 | 0.93 | 0.97 | 5.74 -> 4.74 |
| MID_depth5 | -0.47 | -0.69 | -0.45 | +0.22 | -0.02 | 0.80 | 0.81 | 0.99 | 49.6 -> 43.7 |
| MID_msize | -0.58 | -0.61 | -0.27 | +0.03 | -0.31 | 0.80 | 0.95 | 0.59 | 1.51 -> 1.47 |
| MID_big1 | -0.43 | -0.93 | -0.09 | +0.50 | -0.34 | 0.85 | 0.11 | 0.52 | 0.0303 -> 0.0271 |
| MID_big2 | +0.46 | -0.83 | +0.03 | +1.28 | +0.43 | 0.19 | 0.17 | 0.45 | 0.00796 -> 0.0102 |
| MID_sweep | +0.57 | +0.49 | +0.27 | +0.08 | +0.31 | 0.64 | 0.95 | 0.90 | 0.243 -> 0.262 |
| MID_imb | -0.18 | -0.39 | -0.26 | +0.21 | +0.08 | 0.29 | 0.06 | 0.71 | 0.0133 -> 0.0115 |
| MID_persist | +0.25 | +0.36 | -0.03 | -0.11 | +0.28 | 0.80 | 0.83 | 0.42 | 0.0696 -> 0.0847 |
| MID_can_add1 | -0.62 | +1.23 | -0.12 | -1.85 | -0.50 | 0.14 | 0.01 | 0.71 | 1.13 -> 1.09 |
| MID_can_add23 | +0.77 | -0.37 | +0.33 | +1.14 | +0.44 | 0.37 | 0.45 | 0.55 | 0.702 -> 0.814 |
| MID_refill | -0.40 | +1.31 | +0.83 | -1.71 | -1.24 | 0.78 | 0.18 | 0.22 | 0.404 -> 0.387 |
| MID_refail | -0.02 | -0.18 | +0.13 | +0.16 | -0.14 | 1.00 | 0.33 | 0.65 | 0.000505 -> 0.000488 |
| MID_rate | +0.55 | +0.70 | +0.50 | -0.15 | +0.04 | 0.06 | 0.80 | 0.91 | 12.6 -> 15.3 |
| MID_absorb | +0.69 | +1.00 | +0.67 | -0.32 | +0.01 | 0.09 | 0.44 | 1.00 | 0.557 -> 0.719 |
| MID_resil | +0.45 | -0.11 | -0.30 | +0.56 | +0.74 | 0.57 | 0.35 | 0.22 | 1.02 -> 1.02 |
| OPEN_surge | -0.07 | -0.21 | +0.41 | +0.15 | -0.48 | 0.90 | 0.55 | 0.41 | 11.8 -> 11.6 |
**Plain sentence:** no microstructure series shifts at the break date in an NQ-only way that survives the placebo-date test against BOTH ES and RTY (the nq_only flag, p <= .10 on NQ's own shift and on the NQ-minus-ES and NQ-minus-RTY differences with the same sign, is empty). The strongest partial candidates are the level-1 cancel / add pressure at the open (NQ -0.82 sd, p .03 against placebo dates; ES +1.14 sd, so NQ minus ES = -1.97 sd, p .01; RTY -0.15, NQ minus RTY p .44), the absorption frequency at the open (NQ +0.37, ES +1.35: NQ minus ES p .01) and the order-flow imbalance magnitude at the open (NQ -0.11, RTY -0.56: p .01 against RTY only): each separates NQ from ONE of the other two indices, never from both. What did shift on all three indices together is liquidity: spreads wider (+0.8 to +1.0 sd in the open and mid windows), top-of-book and 5-level depth thinner (-0.5 to -1.0 sd), mean trade size smaller (-0.4 to -0.8 sd), trade rate higher (+0.6 to +0.8 sd): a market-wide change in 2025-10..2026-10, not an NQ-only one. The 09:30 trade-rate surge, the sweep share, the large-print share, the aggressor-imbalance persistence and the refill rate show no significant break on NQ (|z| <= 0.8 and placebo-date p >= .5 for each).
### 3. Does any series predict (previous-day or pre-open values, causal) the day's fade-bundle P&L or the OR-break outcome?
Targets: CAL fade_cond table fade_bundle (three-book NY-AM fade bundle $, 935 days) and hit (+1 opening-range break held, -1 failed). 78 primary tests (whole sample), block permutation (5-day blocks). Count of tests with p <= .05 / <= .01 (of 78): whole sample 20 / 4, 2026 only 7 / 1 (of 78), before the break 2 / 0 (of 78); the expected numbers by chance are about 4 / 0.8.
| target | predictor | statistic (rank rho or top-minus-bottom tercile win rate) | n | block-perm p (20,000) | BH q (78 tests) | Bonferroni |
|---|---|---|---|---|---|---|
| fade_bundle | prev_MID_refail | +0.117 | 924 | 0.0008 | 0.062 | 0.06 |
| hit_win_rate | PRE_spread | -0.125 | 842 | 0.0048 | 0.134 | 0.37 |
| hit_win_rate | prev_OPEN_can_add23 | -0.125 | 842 | 0.0053 | 0.134 | 0.41 |
| hit_win_rate | PRE_depth5 | +0.117 | 842 | 0.0075 | 0.134 | 0.58 |
| hit_win_rate | PRE_big1 | +0.110 | 842 | 0.0106 | 0.134 | 0.83 |
| fade_bundle | PRE_msize | -0.084 | 922 | 0.0118 | 0.134 | 0.92 |
| hit_win_rate | prev_OPEN_depth5 | +0.110 | 842 | 0.0133 | 0.134 | 1.00 |
| hit_win_rate | prev_MID_big1 | +0.107 | 842 | 0.0144 | 0.134 | 1.00 |
| hit_win_rate | prev_MID_spread | -0.107 | 842 | 0.0155 | 0.134 | 1.00 |
| hit_win_rate | prev_OPEN_tob | +0.100 | 842 | 0.0209 | 0.156 | 1.00 |
| hit_win_rate | prev_MID_resil | -0.100 | 842 | 0.0220 | 0.156 | 1.00 |
| fade_bundle | PRE_depth5 | -0.072 | 922 | 0.0310 | 0.174 | 1.00 |
| hit_win_rate | prev_OPEN_spread | -0.096 | 842 | 0.0313 | 0.174 | 1.00 |
| hit_win_rate | prev_MID_depth5 | +0.096 | 842 | 0.0313 | 0.174 | 1.00 |
**Plain sentence:** no series survives multiplicity: the best test is the previous-day mid-session refill-failure share against the fade bundle (rho +0.117, p .0008, BH q .062, Bonferroni .062), a series that is almost always zero, and the next ones are a cluster of correlated liquidity variables on the OR-break outcome (tight pre-open spread, deep pre-open book, large prints: higher OR-break win rate; best p .005, BH q .13, Bonferroni .37). The cluster is internally consistent (a thicker, tighter pre-open book precedes a day on which the 30-minute opening range break holds more often) but it is one effective test, is concentrated after the break (7 of 78 tests at p <= .05 in 2026 only against 2 of 78 before it), and does not reach q <= .10. Not a predictor of the 2026 NY-AM reversion; no microstructure hypothesis on disk explains why NQ differs from ES / RTY at the break beyond the level-1 cancel / add and absorption differences against ES.

## Section ZL-2: statistical dating and detection of the 2026 NY-AM regime (Q4; ZL-2; 2026-11-04; append only)
Prereg l2vast/ds3/prereg/Q4_ZL2_prereg.md sha256 82e00157353f9900f91b7c8bd33d5c370666767b98cbf1f0e68fb1ae82d7e4cd (logged in DECISIONS.md before any change-point statistic; n_tested 85 registered as Q4_ZL2 in FADE_NTESTED.md). Code l2vast/ds3/code/zones3/discover/q4_tools.py; series and tables /mnt/l2/l2vast/ds3_q4/ (q4_series_px.npz, q4_bundle_{ES,RTY,YM}.npz, q4_changepoints.csv, q4_detectors.csv, q4_demo.csv). Daily label-day series 2023-04-03 .. 2026-10-30 (ES / RTY / YM bars end 2026-10-16). Model: one mean shift, unknown common variance, uniform prior over the date (>= 60 days each side), profile-likelihood posterior; placebo = 1,000 circular 20-day block shuffles of the same series; the same on rank-normal scores (robustness). Series: S1 fade bundle $/day (ONRTH + VWAPF + ORBF; NQ 2 lots library basis, ES/RTY/YM at $2,400 stop-risk per trade, YM without ORBF), S2 live NY-AM sleeve $/day (NQ), S3 OR-break indicator (+-0.25% beyond the 09:30-10:00 range after 10:00), S4 first-hour range share, S5 opening gap in % (S5b in units of the day's mean 5-min range).
**Plain sentences.** (1) The NQ fade bundle shifted once, from -$285 to +$1,427 per day, with the most likely date 2026-02-10 and a posterior median of 2025-12-18 (90% interval 2025-08-15 to 2026-02-23); the shift is real against the shuffled calendar (p 0.002) and is a step, not a ramp. (2) The ES bundle moves on the same date (most likely 2025-12-09, from -$881 to +$152 per day) but its shift alone is not significant (p 0.16) and ES never turns profitable; RTY and YM show no break at all. (3) The first-hour range share of the day jumps on NQ, ES and YM at about the same time (2025-12-02, -12-04, -12-19; p 0.018 / 0.022 / 0.001) while the OR-break hit rate does not break anywhere significant; the opening gap measured in ATR units breaks on YM (2026-02-26, tight) and NQ (2026-06) but not before the fade bundle. (4) A single shared break date for the NQ bundle and the NQ/ES/YM first-hour share fits (shared date 2025-12-15, dependence-aware 90% interval 2025-10-02 to 2026-01-28; separate dates are not rejected, p 0.21), so the break date is the same to within about two months and includes 2025-10-23 only at the edge. (5) Causal detectors need 50-60 trading days to see a shift this small against daily noise; the existing lag switches are not beaten.
### (1) Change-point dating (raw scores; rank-normal scores in q4_changepoints.csv agree in every row except where noted)
| series | break date (most likely / median) | 90% interval | before -> after | LR vs shuffled-calendar p95 | placebo p | step vs ramp |
|---|---|---|---|---|---|---|
| S1 NQ fade bundle $/day | 2026-02-10 / 2025-12-18 | 2025-08-15 .. 2026-02-23 | -285 -> +1,427 | 22.2 vs 12.4 | 0.002 | step (dBIC -8.4; best ramp 5 d) |
| S1 ES bundle | 2025-12-09 / 2025-12-04 | 2024-03-19 .. 2026-02-20 | -881 -> +152 | 9.3 vs 13.0 | 0.158 | step |
| S1 RTY bundle | 2023-07-11 / 2024-12-02 | 2023-07-21 .. 2026-05-22 | -1,325 -> -338 | 3.2 vs 9.6 | 0.66 | step |
| S1 YM bundle | 2025-03-19 / 2025-02-06 | 2023-08-04 .. 2026-03-26 | -23 -> -652 | 7.0 vs 12.1 | 0.23 (rank 0.09) | step |
| S2 NQ live NY-AM sleeve | 2025-06-04 / 2025-06-11 | 2023-09-21 .. 2026-05-27 | +983 -> +150 | 3.9 vs 8.3 | 0.40 | none |
| S3 OR-break indicator NQ / ES / RTY / YM | 2025-07-08 / 2026-04-27 / 2024-07-05 / 2026-06-15 | all wide except RTY (2024-04-12 .. 2024-09-30) | NQ .895 -> .813 | 11.7 / 7.2 / 16.2 / 7.8 vs 15 / 16 / 17 / 15 | 0.125 / 0.45 / 0.066 / 0.30 | none significant |
| S4 first-hour range share NQ | 2025-12-02 / 2025-11-24 | 2024-09-05 .. 2026-06-24 | .602 -> .673 | 21.7 vs 17.3 | 0.018 | step |
| S4 ES | 2025-12-04 / 2025-08-29 | 2024-09-05 .. 2025-12-18 | .537 -> .599 | 16.6 vs 13.7 | 0.022 | step |
| S4 YM | 2025-12-19 / 2025-10-24 | 2025-06-18 .. 2026-01-14 | .602 -> .689 | 29.7 vs 15.4 | 0.001 | step |
| S4 RTY | 2024-10-23 | 2023-10-05 .. 2025-02-25 | .697 -> .653 | 10.7 vs 17.3 | 0.25 | none |
| S5 gap % NQ / ES / RTY / YM | 2024-07-17 / 2024-12-19 / 2024-01-09 / 2024-12-19 (rank: 2026-02-25) | wide | NQ .46 -> .70 | 29.5 / 19.7 / 15.6 / 40.6 vs 32 / 36 / 27 / 40 | 0.06 / 0.22 / 0.18 / 0.05 | YM ramp 285 d |
| S5b gap in ATR units NQ | 2026-06-04 / 2026-04-21 | 2024-10-07 .. 2026-07-01 | 3.74 -> 5.39 | 17.9 vs 10.7 | 0.002 | step (15 d) |
| S5b YM | 2026-02-26 / 2026-02-25 | 2026-02-09 .. 2026-03-05 | 3.12 -> 4.90 | 39.7 vs 15.0 | 0.001 | step |
| S5b ES / RTY | 2026-02-27 / 2024-01-09 | wide | | 5.4 / 9.3 vs 8.3 / 11.4 | 0.22 / 0.10 | |
Step vs ramp: with a 5-day search grid every best ramp collapses to a 5-15 day transition (dBIC about -7 = the extra-parameter penalty): the shifts are abrupt to within the 5-day resolution; gradual only for S5 on YM and RTY (285 and 85 days) which are not significant on dBIC either. The NQ-bundle posterior is wide (and not unimodal): P(date <= 2025-10-23) = 0.14, P(2025-10-23 to 2026-01-31) = 0.50, P(after 2026-01-31) = 0.36; the later mode comes from the weak 2026Q1 (-$38.6k in the NQ NY-AM bundle) inside an otherwise strong period.
### (2) Same date across series and instruments?
| shared-date model | shared date (median) | 90% interval | test of one common date vs separate dates |
|---|---|---|---|
| first-hour share NQ + ES + YM | 2025-12-02 | 2025-11-21 .. 2025-12-18 | p 0.42 (consistent) |
| NQ bundle + first-hour share NQ/ES/YM | 2025-12-04 (MAP 2025-12-15) | 2025-11-25 .. 2025-12-18 (independence assumed); dependence-aware residual block bootstrap 2025-10-02 .. 2026-01-28 | p 0.21 (consistent) |
| NQ bundle + ES bundle | 2025-12-22 | 2025-11-03 .. 2026-02-12 | p 0.47 (consistent) |
| NQ bundle + ES + first-hour share NQ/ES/YM | 2025-12-11 | 2025-11-25 .. 2025-12-18 | p 0.27 |
| gap in ATR units NQ + YM + ES | 2026-02-26 | 2026-02-20 .. 2026-03-02 | p 0.13 (consistent, but a later date than the bundle) |
| NQ bundle + NQ gap-ATR | 2026-02-09 | 2025-10-16 .. 2026-03-05 | p 0.007 (rejected: separate dates) |
| all four bundles (NQ, ES, YM, RTY) | 2025-12-16 | 2025-11-05 .. 2026-02-12 | p 0.015 (rejected: RTY/YM do not share the break) |
Reading: the NQ and ES bundles and the first-hour share on NQ/ES/YM share an early-December 2025 break (shared date about 2025-12-04 to 2025-12-15; plausible range 2025-10 to 2026-01); the 2026-10-23 date used in earlier reports is inside the dependence-aware interval but is not the most likely date. The opening-gap-in-ATR break is later (late Feb 2026 on YM/ES, mid 2026 on NQ), so it cannot be the cause of the bundle break (it follows it). RTY and YM bundles do not break with NQ.
### (3) Causal detectors (target the NQ bundle; alarm = upward shift; lag in trading days from 2025-10-23 and from the estimated date 2025-12-15; false alarms per year over 2024-03 .. 2025-09 (1.5 baseline-valid years, 2-5 alarms per setting: coarse))
| detector | false alarms / yr | first alarm | lag from 2025-10-23 | lag from 2025-12-15 |
|---|---|---|---|---|
| lag switch R_F20 (trailing fade P&L, 20 d) | 4.6 | 2025-11-05 | 9 | -28 |
| R_F40 | 3.3 | 2025-12-01 | 27 | -10 |
| R_F40ANY / R_OHSHIT | 2.0 / 2.0 | 2025-12-01 / 2025-11-18 | 27 / 18 | -10 / -19 |
| R_OHS / R_AND / R_HIT / R_OR | 4.0 / 3.3 / 4.0 / 3.3 | 2025-12-12 / 12-12 / 11-18 / 11-18 | 36 / 36 / 18 / 18 | -1 / -1 / -19 / -19 |
| daily CUSUM on the bundle, k = 0.5 sd (too large for a 0.4 sd shift), h = 3 / 4 / 5 / 6 / 8 | 4.6 / 3.3 / 1.3 / 0.7 / 0 | 2026-01-07 / 01-08 / 02-17 / 03-27 / never | 54 / 55 / 83 / 111 / - | 17 / 18 / 46 / 74 / - |
| daily CUSUM k = 0.2 sd (tuned to the shift), h = 3 / 4 / 5 / 6 / 8 | 9.2 / 4.6 / 2.6 / 2.6 / 1.3 | 2025-11-05 / 12-01 / 12-31 / 2026-01-05 / 01-07 | 9 / 27 / 49 / 52 / 54 | -28 / -10 / 12 / 15 / 17 |
| weekly CUSUM k = 0.4, h = 3 / 4 / 5 | 2.0 / 0.7 / 0 | 2026-01-09 / 01-09 / 01-16 | 56 / 56 / 61 | 19 / 19 / 24 |
| Bayesian online change-point P(change in last 40 d) >= 0.5 / 0.8 / 0.95 | 0.7 / 0 / 0 | never | - | - |
Reading: the daily NQ bundle has a shift of 0.4 sd, so any causal detector needs roughly 50-60 trading days to alarm at 1-2 false alarms a year (weekly CUSUM h=4: 0.7 false alarms a year, alarm 56 days after 2025-10-23); the lag switches alarm earlier (9-36 days) but at 2-5 false alarms a year; at a matched 2-3 false alarms per year the tuned daily CUSUM (h=5-6) alarms at 49-52 days, so there is no improvement on the lag switches, only a different point on the same curve. Detecting the change from the features is no earlier: CUSUM k=0.2 on the first-hour share alarms at 38-46 days (NQ, ES) and 56-66 days (YM) with 1.3-7 false alarms a year, weekly CUSUM at 46-51 days with 0.7-2.6; the live NY-AM sleeve (S2) shows no significant break (the Bayesian detector's alarm on 2025-12-12 at P >= 0.95 is a coincidence with the date, not a detection of a verified shift).
### (4) Reusable function (announced to the Q4 slice owners)
`import q4_tools as Q` (code/zones3/discover): `Q.fit_changepoint(x, dates, rank=False)` (date, median, 90/95% interval, before/after means, LR, step-vs-ramp), `Q.block_placebo(x, n, block=20, ref_LR=)`, `Q.test_series_at_break(x, dates, break_date, window=120, n_placebo=500)` (does series x shift at the break by more than at placebo dates: effect, Welch t, |t| rank and p against random dates at least 60 days away), `Q.online_cusum(x, h, k, base, lag, minn)`, `Q.online_bocpd(x)`. Demonstration on the 21 series at the shared date 2025-12-15 (window 120 days each side; p against 600 placebo dates): S1 ES +$1,827/day (t 2.97, p 0.002) and S1 NQ +$1,467 (t 2.44, p 0.003), S5b YM +1.23 ATR (t 2.97, p 0.035), S4 ES +0.061 (t 2.29, p 0.059); not significant: S1 RTY/YM, S2, all S3, S4 NQ (p 0.19), S4 YM (0.37), S5 (p 0.10-0.35), S5b NQ (0.55). Candidates from other slices (volume profile, composition, options flow, microstructure daily series) are tested the same way: `Q.test_series_at_break(candidate, label_days, 20251215)`.
### Caveats
Single-break Gaussian model on heavy-tailed daily P&L (rank-normal scores agree); the interval for S1 NQ is a profile-likelihood interval, wider than 'when did it start' in practice; the full-sample test for ES is not significant although the 120-day window test around 2025-12-15 is (the windowed test compares only 120 days each side); lags are one realisation (one regime change), the false-alarm rates rest on 1.5 baseline-valid years (2-5 events), so the comparisons between detectors are indicative; ES/RTY/YM bundles use the z1 cost basis and bars to 2026-10-16.
# Q4_NQ_STRUCTURE (section Z1: cross-instrument intraday statistics around the 2025-10-23 break) 2026-11-04T19:13Z
Research only, post-hoc, no PASS. Order DIRECTIVE_Q134_20261104.md Q4. Prereg l2vast/ds3/prereg/Q4_Z1_prereg.md sha256 c33f6acc30282d59869be5394c7055a883a531ddbdf4c26524d3d3a631fa39ac and CORRECTION 1 sha256 66b0751ea406e0638cb7a0b2f25254b3cf4d9d0ad438fe841d05da15f1a6f3d9 (DECISIONS.md, before any statistic). n_tested = 232 statistics (A 72, B 56, C 12, D 64, E 12, F 16); expected false positives at 5% without correction 11.6. Data: raw 1-min Databento bars NQ, ES, RTY, YM, 881 RTH days 2023-04-03..2026-10-16 (days with >= 90% valid minutes in all four; 2026Q4 = Oct 1-16), no-roll log returns. PRE 636 days (to 2025-10-22), POST 245 days. Bootstrap: 1,000 day resamples within PRE and POST (5-day blocks for family F). Code l2vast/ds3/code/q4_z1/ (build.py, stats.py, run.py, link.py), results out/q4_z1/.

## Plain answer
Several things changed at the break date, but NONE of the 232 statistics satisfies the prereg 'NQ-specific' rule (change in NQ-ES, NQ-RTY and NQ-YM in the same direction while the control pair ES-YM does not; or NQ minus the mean of the other three for single-instrument statistics). What changed: (1) NQ's volatility relative to ES and RTY rose across the whole RTH session (NQ/ES 1-min RMS ratio 1.284 -> 1.444, +12.5%, CI excludes 0 in 13 of 14 buckets; NQ/RTY 0.850 -> 0.928; NQ/YM unchanged 1.369 -> 1.412), and NQ's beta on ES rose from 1.19 to 1.33 (first 30 min 1.27 -> 1.46) with the NQ-ES correlation unchanged (RTH 0.928 -> 0.922; first 30 min up 0.846 -> 0.868): NQ moves ~12% more per unit of ES move, not less tied to ES; this looks 'NQ vs ES and RTY' but YM also moved in the opposite way (below), so it fails the control-pair rule. (2) YM DECOUPLED: ES-YM correlation 0.884 -> 0.796, NQ-YM 0.720 -> 0.587 (1-min, RTH; first 30 min 0.335 -> 0.233) and the NQ-YM first-30 spread std rose 16.3 -> 20.3 bp: the largest structural move is in YM (price-weighted Dow), the control pair itself changed. (3) The 10:00-11:00 hour flipped from persistence to reversal on ALL four indexes: lag-1 autocorrelation of 1-min returns NQ +0.040 -> -0.024 (CI excludes 0), ES +0.053 -> -0.026, RTY +0.012 -> -0.026, YM +0.046 -> -0.026, and VR(5) NQ 1.093 -> 0.949 (CI excludes 0), ES 1.137 -> 0.935, RTY 1.073 -> 0.941, YM 1.123 -> 0.930; only NQ's CIs exclude 0 individually but the NQ-minus-others differences are +-0.03 to +-0.1 with CIs around 0: the hour-by-hour reversal is market-wide, not NQ-only (the whole-RTH AC1 and VR did not move: NQ AC1 -0.001 -> -0.006, VR5 1.017 -> 0.974, as already known). The 1-min lead-lag at 10:00-11:30 flipped from NQ_t correlated with ES_t-1 +0.027 to -0.022 (CI excludes 0), the same reversal seen at 1-min lag; at the open (first 30 min) lead-lag is zero in both periods. (4) Relative strength persistence (the mega-cap proxy: first-hour NQ-ES relative return vs rest of day, daily relative-return AC1, 5-day persistence): no change (all 16 CIs include 0; levels within +-0.1 of zero). (5) NQ-ES spread dispersion (NQ minus 1.19 ES) around the open rose 8.5 -> 9.6 bp (first 30 min) and 4.4 -> 4.8 bp (10:00-11:30), AC1 of the spread unchanged: no new spread persistence. Which changes at the break date and only on NQ: none by the prereg rule; the closest are the NQ/ES and NQ/RTY volatility ratios and the NQ beta on ES (NQ-vs-ES-and-RTY, not vs YM), plus the NQ-only individually significant 10:00-11:00 AC1 and VR5 (the same sign and size on the other three indexes).
Live-stack link: the live NY-AM sleeve (K7+P7+U7+H7+M7+A7 session nyam, Q1-A ts2) did not flatten at the break date: monthly $/wk-equivalent +17k in Apr-May 2025, then 161/wk on average June-October 2025 and 1,283/wk November 2025-October 2026 (4,008/wk over 2023-04..2025-10); its best single mean split in 2025-01..2026-04 is June 2025 (4,748 -> 953), four months before the break date. No statistic lines up under the prereg rule (best split within +-1 month AND |Spearman| >= 0.4 with p <= 0.05): the nearest monthly correlations are mean AC1 10:00-11:00 across the four indexes (Spearman +0.33, perm p 0.028, best split 2026-02) and the NQ-ES first-30-min 30-min correlation (+0.31, p 0.055); the vol-ratio and beta series split at the end of the window (2026-04, an edge artefact). So: the structure changes (NQ relative vol, YM decoupling, the 10-11 hour reversal) are real but are not tied month-for-month to the live sleeve's flattening, which started earlier (June 2025) and was dominated by one April-May 2025 spike.
Multiplicity: 99 of 232 CIs exclude 0 (expected ~12 by chance if independent; the statistics are strongly dependent: the 54 family-A and 34 family-B hits come from a few moves), BH q <= 0.10 for 93. Counts of CI-excluding-0 by family: A 54/72, B 34/56, C 4/12, D 6/64, E 1/12, F 0/16.

## Selected statistics by quarter (PRE / POST are the aggregates; Delta with the day-bootstrap 95% CI)
| statistic | PRE | POST | 2023Q2 | 2023Q3 | 2023Q4 | 2024Q1 | 2024Q2 | 2024Q3 | 2024Q4 | 2025Q1 | 2025Q2 | 2025Q3 | 2025Q4 | 2026Q1 | 2026Q2 | 2026Q3 | 2026Q4 | Delta POST-PRE [95% CI] |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B volratio NQ/ES RTH | 1.284 | 1.444 | 1.342 1.450 1.291 1.391 1.288 1.451 1.405 1.315 1.140 1.311 1.315 1.304 1.532 1.671 1.562 | +0.160 [+0.106,+0.205] |
| B volratio NQ/RTY RTH | 0.850 | 0.928 | 0.810 1.005 0.768 0.681 0.834 0.858 0.784 0.949 0.918 0.710 0.876 0.814 0.974 1.108 1.046 | +0.077 [+0.045,+0.110] |
| B volratio NQ/YM RTH | 1.369 | 1.412 | 1.397 1.609 1.407 1.471 1.317 1.528 1.354 1.456 1.263 1.186 1.377 1.233 1.545 1.555 1.375 | +0.044 [-0.012,+0.090] |
| B volratio ES/YM RTH | 1.066 | 0.978 | 1.040 1.109 1.090 1.058 1.023 1.053 0.963 1.107 1.108 0.905 1.047 0.946 1.008 0.931 0.880 | -0.088 [-0.114,-0.061] |
| B volratio NQ/ES 09:30 | 1.496 | 1.679 | 1.598 1.728 1.575 1.685 1.547 1.723 1.573 1.511 1.228 1.544 1.492 1.492 1.795 2.003 1.878 | +0.182 [+0.104,+0.246] |
| A beta NQ on ES h1 RTH | 1.192 | 1.332 | 1.171 1.309 1.171 1.237 1.183 1.342 1.258 1.248 1.104 1.202 1.253 1.237 1.411 1.464 1.367 | +0.140 [+0.099,+0.175] |
| A beta NQ on ES h1 first30 | 1.267 | 1.458 | 1.146 1.406 1.248 1.260 1.252 1.451 1.272 1.361 1.150 1.362 1.361 1.356 1.560 1.591 1.520 | +0.191 [+0.140,+0.233] |
| A corr NQ-ES h1 RTH | 0.928 | 0.922 | 0.872 0.903 0.907 0.889 0.919 0.925 0.895 0.949 0.969 0.917 0.952 0.949 0.921 0.876 0.875 | -0.006 [-0.016,+0.005] |
| A corr NQ-ES h1 first30 | 0.846 | 0.868 | 0.717 0.813 0.792 0.749 0.809 0.842 0.809 0.901 0.936 0.883 0.912 0.909 0.869 0.795 0.809 | +0.022 [+0.005,+0.040] |
| A corr NQ-YM h1 RTH | 0.720 | 0.587 | 0.632 0.655 0.700 0.596 0.623 0.552 0.544 0.768 0.908 0.593 0.711 0.719 0.522 0.414 0.347 | -0.133 [-0.185,-0.071] |
| A corr ES-YM h1 RTH | 0.884 | 0.796 | 0.884 0.865 0.891 0.833 0.817 0.777 0.796 0.899 0.960 0.811 0.850 0.860 0.752 0.710 0.671 | -0.088 [-0.113,-0.057] |
| C spread std(bp) NQ-ES first30 | 8.523 | 9.555 | 9.903 9.065 8.641 8.084 7.177 10.222 8.705 9.148 7.794 6.140 7.450 8.388 10.650 10.723 8.943 | +1.032 [+0.434,+1.595] |
| C spread std(bp) NQ-YM first30 | 16.334 | 20.268 | 16.172 15.199 14.542 14.289 15.351 22.273 16.639 18.462 15.556 13.621 17.287 19.311 23.053 19.706 19.857 | +3.934 [+2.728,+5.032] |
| D AC1 NQ 1000-1100 | 0.040 | -0.024 | 0.022 0.020 -0.003 -0.001 0.045 0.034 -0.026 0.010 0.119 -0.059 0.033 -0.081 0.004 -0.039 0.009 | -0.064 [-0.118,-0.010] |
| D AC1 ES 1000-1100 | 0.053 | -0.026 | 0.001 -0.004 -0.024 -0.029 0.022 0.037 -0.035 -0.005 0.147 -0.054 0.032 -0.070 0.006 -0.049 -0.051 | -0.079 [-0.158,+0.005] |
| D AC1 RTY 1000-1100 | 0.012 | -0.026 | 0.011 -0.003 -0.080 -0.067 -0.020 0.010 -0.066 -0.047 0.120 0.001 0.024 -0.057 0.016 -0.061 0.001 | -0.039 [-0.098,+0.023] |
| D AC1 YM 1000-1100 | 0.046 | -0.026 | 0.004 -0.004 -0.035 -0.001 -0.008 0.031 -0.041 -0.045 0.146 -0.005 0.026 -0.066 0.003 -0.028 -0.064 | -0.072 [-0.146,+0.007] |
| D VR5 NQ 1000-1100 | 1.093 | 0.949 | 0.952 1.060 1.128 0.999 1.140 1.028 0.989 1.170 1.211 0.851 0.931 0.890 1.008 0.955 1.051 | -0.145 [-0.264,-0.025] |
| D VR5 ES 1000-1100 | 1.137 | 0.935 | 0.913 0.995 1.029 1.030 1.103 1.044 0.948 1.123 1.337 0.843 0.941 0.892 1.013 0.908 1.007 | -0.202 [-0.390,+0.003] |
| D VR5 RTY 1000-1100 | 1.073 | 0.941 | 0.918 0.979 0.963 0.900 1.004 1.119 0.947 1.029 1.304 0.982 0.928 0.944 0.994 0.903 1.097 | -0.132 [-0.275,+0.009] |
| D VR5 YM 1000-1100 | 1.123 | 0.930 | 0.911 0.979 0.913 1.087 1.065 1.076 0.914 1.004 1.361 0.969 0.972 0.881 1.001 0.913 0.986 | -0.192 [-0.398,+0.017] |
| D AC1 NQ first30 | -0.004 | 0.020 | 0.036 -0.032 -0.027 0.054 -0.006 -0.026 0.011 0.049 -0.042 -0.023 -0.013 -0.021 0.069 0.064 -0.101 | +0.025 [-0.018,+0.063] |
| D VR5 NQ first30 | 0.996 | 1.014 | 1.021 0.899 0.978 1.095 0.986 1.014 1.173 1.066 0.899 0.928 1.064 0.891 1.121 1.014 0.897 | +0.018 [-0.086,+0.113] |
| D AC1 NQ RTH | -0.001 | -0.006 | 0.007 -0.019 -0.029 0.020 0.004 0.011 0.003 0.003 0.003 -0.031 -0.022 -0.033 0.019 0.012 -0.030 | -0.005 [-0.024,+0.014] |
| D VR5 NQ RTH | 1.017 | 0.974 | 0.927 0.954 1.006 1.027 1.097 1.003 1.110 1.077 1.020 0.907 0.951 0.908 1.025 1.011 0.968 | -0.043 [-0.089,+0.004] |
| E leadlag NQ_t vs ES_t-1 1000-1130 | 0.027 | -0.022 | 0.007 0.003 -0.006 -0.013 0.033 0.045 -0.022 -0.015 0.078 -0.044 0.026 -0.064 0.003 -0.035 -0.040 | -0.049 [-0.091,-0.003] |
| E leadlag ES_t vs NQ_t-1 1000-1130 | 0.039 | -0.016 | -0.005 0.010 -0.024 -0.005 0.029 0.038 -0.013 -0.008 0.119 -0.040 0.030 -0.050 -0.002 -0.029 -0.014 | -0.055 [-0.113,+0.003] |

## Live-stack link (monthly series 2023-04..2026-10, 42 months; best split searched 2025-01..2026-04; Spearman vs the NY-AM sleeve monthly mean, 2,000 permutations)
| series | best split month | mean before -> after | Spearman | perm p |
|---|---|---|---|---|
| NQ/ES vol ratio RTH | 202604 | 1.350 -> 1.574 | -0.08 | 0.643 |
| NQ beta on ES h1 RTH | 202604 | 1.237 -> 1.402 | -0.01 | 0.963 |
| NQ-YM corr h1 RTH | 202604 | 0.647 -> 0.437 | +0.17 | 0.265 |
| ES-YM corr h1 RTH | 202604 | 0.841 -> 0.714 | +0.18 | 0.235 |
| NQ-ES first30 corr h30 | 202501 | 0.751 -> 0.867 | +0.31 | 0.055 |
| NQ-ES spread std first30 | 202604 | 8.358 -> 10.235 | +0.05 | 0.741 |
| mean AC1 10-11 (4 idx) | 202602 | -0.004 -> -0.033 | +0.33 | 0.028 |
| mean VR5 10-11 (4 idx) | 202505 | 1.027 -> 0.944 | +0.21 | 0.192 |
NY-AM sleeve best split 2025-06 (4,748 -> 953 $/wk-equivalent).

## Caveats
Raw (non-adjusted) 1-min closes with roll bars removed; bars end 2026-10-16 for all four (the 1-s path of NQ continues to 10-30 but the other three have 1-min bars only). Day-level bootstrap treats days as independent (5-day blocks for F). The control-pair rule needs ES-YM to be stable and YM is not; a rule against the ES-RTY pair would be a different test (not run). Relative-strength persistence is a proxy: no index weights or constituent data are on disk. Option flow and gamma: CAL's FADE_GAMMA found no predictive power for the NY-AM reversion; not repeated here.
Correction (Z1, section Z1 above): the NQ/ES relative-volatility ratio CI excludes 0 in ALL 14 buckets (13 30-minute buckets plus RTH), not 13 of 14; and the family-F levels are within +-0.12 of zero (not +-0.1). The Q4_NQ_STRUCTURE.md file holds other sections; the section Z1 starts at its second heading line.
Correction (ZL-2) to section ZL-2: (a) 'the 2026-10-23 date used in earlier reports' should read 2025-10-23. (b) The clause in (1) attributing the later posterior mode to 'the weak 2026Q1 (-$38.6k in the NQ NY-AM bundle)' is a conjecture and the figure is the OR15 book's 2026Q1, not the bundle's; the tested fact is only that P(date after 2026-01-31) = 0.36 and that the MAP is 2026-02-10.

### Z1 robustness addendum (2026-11-04T19:15Z, post-hoc, not in the prereg): placebo-date test with ZL-2's q4_tools (Q.test_series_at_break, window 120 days, 500 placebo break dates at least 60 days away)
The day-bootstrap CIs above treat days as independent and therefore overstate the evidence (volatility clusters). On three daily series built from the same returns: log NQ/ES RTH volatility ratio: shift +0.039 at 2025-10-23 (Welch t 3.70, |t| rank 0.45 among placebo dates, p 0.55; placebo 95th percentile of |t| is 12.1) and +0.068 at 2025-12-15 (t 4.90, rank 0.55, p 0.45); mean lag-1 autocorrelation 10:00-11:00 of the four indexes (daily): +0.007 (t 0.41, p 0.69) at 10-23 and -0.014 (t -0.83, p 0.46) at 12-15; NQ-ES first-30-minute spread rms: t 4.6-4.8 with p 0.27 (10-23) and 0.19 (12-15). None of the three shifts is unusual against random placebo dates, so the 'significant' pooled changes in the tables (NQ relative volatility +12.5%, 10-11 hour reversal, YM decoupling) are within what random 120-day windows produce in this period; they are descriptive, not evidence of a structural break at 2025-10-23 or at ZL-2's 2025-12-15 estimate. This strengthens the conclusion that no statistic is NQ-specific and none is tied to a break date. (YM decoupling and the pair correlations were not re-tested with the placebo-date tool.)

## Section Z2 (Z2, 2026-11-04 ~20:00Z): volume-profile and opening-structure series, break dates and fade association. Prereg l2vast/ds3/prereg/Q4_STRUCTURE_Z2_prereg.md sha256 aec27faea54671cfb1f79ade4e5f976b44c4b902d804dcd0970f6ee768419b1b (DECISIONS.md before scoring). Research only; nothing scored as a book.
Data: 1-min bars NQ, ES, RTY, YM (cache_te2 volume, 2023-04-03..2026-10-16, 881 RTH days each; no trade counts in 1-min bars, so no bid-ask / volume-per-trade proxy beyond range-per-volume), daily NQ 3-fade bundle P&L (ONRTH + VWAPF + ORBF, FADE_XI MultiHarness version, 2 lots). Code code/q4z2/ (q4_feat.py, q4_an.py), results /mnt/l2/l2vast/ds3_zones3_new/Z2_q4/ (daily_feats.pkl, changepoints.csv, correlations.csv, q4_results.pkl). Break dating: single mean-shift per series (Welch t over weekly candidates, >= 60 days each side), 90% CI of the date from a 20-day block bootstrap of segment residuals (300 draws), permutation p of max |t| (200 block shuffles of 20 days), BH over 60 tests. Deviation from the prereg: 15 series (or_cont = continuation indicator on resolved days added to the 14 listed), so 60 change-point tests and 60 x 3 correlation families = 240 scored statistics (n_tested 240). Reference break 2025-10-23.

### Quarter-by-quarter tables (means of the daily series; the other nine series are in Z2_q4/q4_results.pkl QT)

**first-hour (09:30-10:30) range share of the RTH range**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 0.588 | 0.560 | 0.674 | 0.634 |
| 2023Q3 | 0.623 | 0.555 | 0.754 | 0.601 |
| 2023Q4 | 0.578 | 0.518 | 0.687 | 0.557 |
| 2024Q1 | 0.609 | 0.506 | 0.696 | 0.600 |
| 2024Q2 | 0.562 | 0.497 | 0.673 | 0.595 |
| 2024Q3 | 0.564 | 0.506 | 0.668 | 0.639 |
| 2024Q4 | 0.666 | 0.574 | 0.699 | 0.632 |
| 2025Q1 | 0.630 | 0.563 | 0.622 | 0.558 |
| 2025Q2 | 0.579 | 0.533 | 0.620 | 0.537 |
| 2025Q3 | 0.658 | 0.567 | 0.660 | 0.671 |
| 2025Q4 | 0.612 | 0.563 | 0.614 | 0.610 |
| 2026Q1 | 0.678 | 0.632 | 0.669 | 0.689 |
| 2026Q2 | 0.612 | 0.562 | 0.666 | 0.669 |
| 2026Q3 | 0.713 | 0.599 | 0.721 | 0.707 |
| 2026Q4 | 0.664 | 0.525 | 0.596 | 0.676 |

**share of RTH volume in 09:30-10:00**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 0.163 | 0.136 | 0.186 | 0.186 |
| 2023Q3 | 0.171 | 0.147 | 0.210 | 0.199 |
| 2023Q4 | 0.161 | 0.137 | 0.208 | 0.188 |
| 2024Q1 | 0.165 | 0.142 | 0.201 | 0.189 |
| 2024Q2 | 0.162 | 0.133 | 0.188 | 0.184 |
| 2024Q3 | 0.153 | 0.126 | 0.180 | 0.197 |
| 2024Q4 | 0.164 | 0.138 | 0.186 | 0.215 |
| 2025Q1 | 0.152 | 0.129 | 0.171 | 0.181 |
| 2025Q2 | 0.143 | 0.122 | 0.172 | 0.176 |
| 2025Q3 | 0.166 | 0.140 | 0.183 | 0.200 |
| 2025Q4 | 0.167 | 0.135 | 0.186 | 0.211 |
| 2026Q1 | 0.175 | 0.144 | 0.187 | 0.229 |
| 2026Q2 | 0.167 | 0.139 | 0.188 | 0.237 |
| 2026Q3 | 0.185 | 0.139 | 0.192 | 0.234 |
| 2026Q4 | 0.193 | 0.132 | 0.173 | 0.230 |

**opening-minute volume / median RTH 1-min volume**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 5.68 | 5.19 | 10.94 | 9.64 |
| 2023Q3 | 5.81 | 5.94 | 13.33 | 11.76 |
| 2023Q4 | 6.05 | 6.00 | 14.45 | 12.36 |
| 2024Q1 | 6.02 | 6.30 | 13.30 | 12.54 |
| 2024Q2 | 6.08 | 6.19 | 13.25 | 12.25 |
| 2024Q3 | 4.87 | 5.16 | 10.30 | 11.62 |
| 2024Q4 | 5.93 | 6.39 | 12.18 | 14.58 |
| 2025Q1 | 4.55 | 4.92 | 11.79 | 11.25 |
| 2025Q2 | 5.11 | 5.38 | 12.84 | 12.12 |
| 2025Q3 | 6.93 | 6.65 | 12.47 | 14.51 |
| 2025Q4 | 6.45 | 5.60 | 12.88 | 15.43 |
| 2026Q1 | 7.89 | 6.25 | 11.90 | 17.96 |
| 2026Q2 | 7.74 | 6.50 | 14.49 | 18.93 |
| 2026Q3 | 7.82 | 6.58 | 17.11 | 19.35 |
| 2026Q4 | 8.71 | 5.45 | 13.81 | 19.71 |

**OR-break continuation share (resolved days; CAL hit definition)**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 0.56 | 0.52 | 0.47 | 0.44 |
| 2023Q3 | 0.47 | 0.51 | 0.39 | 0.54 |
| 2023Q4 | 0.57 | 0.57 | 0.46 | 0.54 |
| 2024Q1 | 0.53 | 0.43 | 0.47 | 0.57 |
| 2024Q2 | 0.58 | 0.57 | 0.48 | 0.49 |
| 2024Q3 | 0.57 | 0.55 | 0.51 | 0.48 |
| 2024Q4 | 0.49 | 0.65 | 0.49 | 0.48 |
| 2025Q1 | 0.58 | 0.59 | 0.52 | 0.53 |
| 2025Q2 | 0.50 | 0.49 | 0.60 | 0.56 |
| 2025Q3 | 0.47 | 0.54 | 0.62 | 0.50 |
| 2025Q4 | 0.42 | 0.53 | 0.53 | 0.55 |
| 2026Q1 | 0.41 | 0.54 | 0.43 | 0.47 |
| 2026Q2 | 0.55 | 0.54 | 0.43 | 0.52 |
| 2026Q3 | 0.38 | 0.54 | 0.59 | 0.44 |
| 2026Q4 | 0.50 | 0.67 | 0.55 | 0.73 |

**absolute opening gap (bp)**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 45.3 | 32.4 | 47.6 | 23.0 |
| 2023Q3 | 49.8 | 36.9 | 41.5 | 28.9 |
| 2023Q4 | 42.0 | 32.6 | 51.7 | 25.5 |
| 2024Q1 | 49.6 | 33.0 | 68.4 | 26.6 |
| 2024Q2 | 46.5 | 36.5 | 65.1 | 33.4 |
| 2024Q3 | 66.2 | 45.3 | 72.3 | 32.6 |
| 2024Q4 | 49.3 | 34.6 | 56.5 | 33.7 |
| 2025Q1 | 64.8 | 49.5 | 65.4 | 39.2 |
| 2025Q2 | 98.2 | 80.7 | 101.1 | 71.6 |
| 2025Q3 | 34.9 | 26.5 | 42.7 | 25.1 |
| 2025Q4 | 57.2 | 38.3 | 53.7 | 28.1 |
| 2026Q1 | 60.3 | 46.6 | 69.7 | 47.3 |
| 2026Q2 | 73.9 | 45.4 | 62.5 | 43.9 |
| 2026Q3 | 71.4 | 36.6 | 46.2 | 44.3 |
| 2026Q4 | 65.0 | 30.1 | 43.2 | 38.4 |

**gap-fill rate within the RTH day**
| quarter | NQ | ES | RTY | YM |
|--|--|--|--|--|
| 2023Q2 | 0.65 | 0.57 | 0.62 | 0.70 |
| 2023Q3 | 0.62 | 0.60 | 0.67 | 0.64 |
| 2023Q4 | 0.61 | 0.64 | 0.64 | 0.66 |
| 2024Q1 | 0.50 | 0.55 | 0.52 | 0.65 |
| 2024Q2 | 0.68 | 0.69 | 0.51 | 0.71 |
| 2024Q3 | 0.69 | 0.62 | 0.60 | 0.66 |
| 2024Q4 | 0.46 | 0.57 | 0.64 | 0.62 |
| 2025Q1 | 0.61 | 0.66 | 0.64 | 0.68 |
| 2025Q2 | 0.59 | 0.58 | 0.56 | 0.61 |
| 2025Q3 | 0.65 | 0.65 | 0.69 | 0.71 |
| 2025Q4 | 0.52 | 0.67 | 0.67 | 0.66 |
| 2026Q1 | 0.52 | 0.62 | 0.67 | 0.60 |
| 2026Q2 | 0.61 | 0.59 | 0.57 | 0.61 |
| 2026Q3 | 0.48 | 0.45 | 0.48 | 0.54 |
| 2026Q4 | 0.25 | 0.50 | 0.60 | 0.67 |

### Break dates (single mean shift; 90% CI; BH q over 60 tests; diff = post minus pre; cover = CI contains 2025-10-23)
| series | inst | break date | diff | q_BH | 90% CI | cover |
|--|--|--|--|--|--|--|
| drift_fh_rev | ES | 20231018 | -0.1001 | 0.318 | 20230811-20260410 | yes |
| drift_fh_rev | NQ | 20260601 | +0.1329 | 0.191 | 20231001-20260709 | yes |
| drift_fh_rev | RTY | 20231213 | +0.09284 | 0.354 | 20230902-20251114 | yes |
| drift_fh_rev | YM | 20260325 | +0.09742 | 0.251 | 20230830-20260623 | yes |
| fh_range_share | ES | 20251126 | +0.06182 | 0.050 | 20250716-20260430 | yes |
| fh_range_share | NQ | 20251126 | +0.07049 | 0.050 | 20250217-20260430 | yes |
| fh_range_share | RTY | 20241107 | -0.04333 | 0.330 | 20231227-20260624 | yes |
| fh_range_share | YM | 20251219 | +0.08734 | 0.019 | 20250909-20260220 | yes |
| gap_bps | ES | 20240212 | +10.38 | 0.204 | 20231220-20251201 | yes |
| gap_bps | NQ | 20240718 | +18.09 | 0.048 | 20240418-20250715 | no |
| gap_bps | RTY | 20231013 | +19.32 | 0.063 | 20230823-20240509 | no |
| gap_bps | YM | 20240305 | +14.13 | 0.028 | 20240111-20240718 | no |
| gap_fill_1h | ES | 20260319 | -0.07646 | 0.597 | 20230728-20260624 | yes |
| gap_fill_1h | NQ | 20230712 | -0.1093 | 0.662 | 20230705-20260624 | yes |
| gap_fill_1h | RTY | 20231110 | -0.08804 | 0.672 | 20230823-20260608 | yes |
| gap_fill_1h | YM | 20260722 | -0.1504 | 0.134 | 20240724-20260722 | yes |
| gap_fill_day | ES | 20260701 | -0.1571 | 0.121 | 20240911-20260716 | yes |
| gap_fill_day | NQ | 20251024 | -0.1038 | 0.070 | 20231027-20260229 | yes |
| gap_fill_day | RTY | 20260508 | -0.1199 | 0.292 | 20231103-20260701 | yes |
| gap_fill_day | YM | 20260722 | -0.1477 | 0.194 | 20230921-20260722 | yes |
| globex_vol_share | ES | 20260227 | +0.02803 | 0.028 | 20250818-20260420 | yes |
| globex_vol_share | NQ | 20260227 | +0.05708 | 0.019 | 20260129-20260306 | no |
| globex_vol_share | RTY | 20260227 | +0.02491 | 0.063 | 20240716-20260427 | yes |
| globex_vol_share | YM | 20241031 | +0.02459 | 0.085 | 20231022-20250627 | no |
| illiq_fh | ES | 20240306 | +59.85 | 0.019 | 20230821-20240327 | no |
| illiq_fh | NQ | 20240614 | +1001 | 0.028 | 20240220-20240624 | no |
| illiq_fh | RTY | 20240306 | +218 | 0.058 | 20230717-20240411 | no |
| illiq_fh | YM | 20231207 | +6874 | 0.028 | 20230807-20240108 | no |
| open_spike | ES | 20251219 | +0.7139 | 0.251 | 20230826-20260420 | yes |
| open_spike | NQ | 20251205 | +2.176 | 0.019 | 20250917-20251219 | yes |
| open_spike | RTY | 20260413 | +3.318 | 0.039 | 20251120-20260616 | no |
| open_spike | YM | 20251219 | +6.481 | 0.019 | 20251111-20260107 | no |
| or_cont | ES | 20230810 | +0.06576 | 0.955 | 20230718-20260629 | yes |
| or_cont | NQ | 20251028 | -0.107 | 0.108 | 20231197-20260511 | yes |
| or_cont | RTY | 20241114 | +0.07411 | 0.430 | 20230828-20260624 | yes |
| or_cont | YM | 20230811 | +0.06778 | 0.860 | 20230804-20260615 | yes |
| premkt_range_share | ES | 20240717 | -0.09553 | 0.019 | 20240425-20240905 | no |
| premkt_range_share | NQ | 20240717 | -0.1051 | 0.019 | 20240404-20240912 | no |
| premkt_range_share | RTY | 20240828 | -0.07869 | 0.019 | 20240614-20241024 | no |
| premkt_range_share | YM | 20240717 | -0.05875 | 0.050 | 20240122-20250210 | no |
| premkt_vol_share | ES | 20250401 | -0.05831 | 0.019 | 20250117-20250507 | no |
| premkt_vol_share | NQ | 20250408 | -0.09421 | 0.019 | 20250311-20250507 | no |
| premkt_vol_share | RTY | 20240717 | -0.05489 | 0.019 | 20240523-20240905 | no |
| premkt_vol_share | YM | 20250408 | -0.03427 | 0.019 | 20241023-20250612 | no |
| rev_30_60 | ES | 20260305 | +0.06451 | 0.738 | 20230798-20260522 | yes |
| rev_30_60 | NQ | 20231121 | -0.08194 | 0.426 | 20230912-20260610 | yes |
| rev_30_60 | RTY | 20230830 | +0.1083 | 0.751 | 20230718-20260514 | yes |
| rev_30_60 | YM | 20250612 | -0.07394 | 0.546 | 20230913-20260616 | yes |
| vol_share_0930_1000 | ES | 20251219 | +0.006724 | 0.534 | 20231016-20260616 | yes |
| vol_share_0930_1000 | NQ | 20251126 | +0.01736 | 0.048 | 20250502-20260504 | yes |
| vol_share_0930_1000 | RTY | 20240320 | -0.01883 | 0.019 | 20231024-20241039 | no |
| vol_share_0930_1000 | YM | 20251219 | +0.04128 | 0.019 | 20251111-20260212 | no |
| vol_share_0930_1030 | ES | 20230919 | -0.01244 | 0.533 | 20230807-20260628 | yes |
| vol_share_0930_1030 | NQ | 20260511 | +0.02921 | 0.028 | 20250922-20260701 | yes |
| vol_share_0930_1030 | RTY | 20240320 | -0.02699 | 0.019 | 20231221-20240814 | no |
| vol_share_0930_1030 | YM | 20251219 | +0.04402 | 0.019 | 20251027-20260230 | no |
| vol_share_1500_1600 | ES | 20251001 | -0.01307 | 0.050 | 20250408-20260518 | yes |
| vol_share_1500_1600 | NQ | 20250924 | -0.01026 | 0.050 | 20241087-20260529 | yes |
| vol_share_1500_1600 | RTY | 20240313 | +0.02024 | 0.039 | 20231003-20240832 | no |
| vol_share_1500_1600 | YM | 20251001 | -0.0117 | 0.235 | 20240618-20260624 | yes |

### Association with the daily NQ 3-fade bundle P&L (Spearman; day level contemporaneous, 2026-only day level, trailing-20-day mean of the feature at day-1 predicting day d, quarter level (15 quarters)); rows with BH q <= .10 in any family
| inst | series | rho day | rho day 2026 | rho trailing-20d | rho quarter (q) |
|--|--|--|--|--|--|
| ES | drift_fh_rev | +0.106 | -0.043 | +0.025 (q 0.65) | +0.40 (q 0.33) |
| ES | gap_fill_day | +0.100 | +0.067 | +0.035 (q 0.48) | -0.13 (q 0.78) |
| ES | globex_vol_share | +0.080 | -0.033 | +0.057 (q 0.34) | +0.40 (q 0.33) |
| ES | illiq_fh | -0.049 | -0.195 | +0.100 (q 0.07) | +0.45 (q 0.26) |
| ES | or_cont | -0.292 | -0.155 | +0.108 (q 0.07) | -0.33 (q 0.42) |
| ES | premkt_vol_share | -0.041 | -0.018 | -0.091 (q 0.08) | -0.52 (q 0.19) |
| ES | rev_30_60 | +0.229 | +0.357 | -0.055 (q 0.34) | +0.35 (q 0.41) |
| ES | vol_share_0930_1000 | +0.119 | +0.030 | +0.031 (q 0.53) | +0.58 (q 0.16) |
| NQ | drift_fh_rev | +0.170 | +0.090 | -0.020 (q 0.69) | +0.20 (q 0.67) |
| NQ | gap_fill_day | +0.077 | +0.033 | -0.040 (q 0.44) | -0.29 (q 0.48) |
| NQ | globex_vol_share | +0.113 | +0.069 | +0.044 (q 0.39) | +0.32 (q 0.42) |
| NQ | illiq_fh | -0.054 | -0.182 | +0.100 (q 0.07) | +0.47 (q 0.25) |
| NQ | open_spike | +0.128 | -0.018 | +0.086 (q 0.08) | +0.76 (q 0.03) |
| NQ | or_cont | -0.550 | -0.500 | +0.004 (q 0.93) | -0.73 (q 0.04) |
| NQ | premkt_vol_share | -0.059 | +0.018 | -0.090 (q 0.08) | -0.56 (q 0.16) |
| NQ | rev_30_60 | +0.269 | +0.285 | -0.018 (q 0.69) | +0.36 (q 0.39) |
| NQ | vol_share_0930_1000 | +0.146 | +0.016 | +0.035 (q 0.48) | +0.79 (q 0.03) |
| RTY | or_cont | -0.122 | -0.150 | +0.008 (q 0.87) | -0.12 (q 0.79) |
| RTY | premkt_vol_share | -0.058 | -0.012 | -0.086 (q 0.08) | -0.58 (q 0.16) |
| RTY | rev_30_60 | +0.079 | +0.110 | -0.040 (q 0.44) | -0.14 (q 0.78) |
| YM | globex_vol_share | +0.079 | +0.006 | +0.048 (q 0.39) | +0.34 (q 0.42) |
| YM | open_spike | +0.083 | -0.112 | +0.057 (q 0.34) | +0.64 (q 0.13) |
| YM | or_cont | -0.098 | +0.016 | +0.048 (q 0.39) | -0.07 (q 0.85) |
| YM | premkt_vol_share | -0.027 | -0.090 | -0.095 (q 0.07) | -0.47 (q 0.25) |
| YM | vol_share_0930_1000 | +0.099 | -0.088 | +0.048 (q 0.39) | +0.62 (q 0.13) |
| YM | vol_share_1500_1600 | -0.032 | -0.008 | -0.084 (q 0.09) | -0.11 (q 0.80) |

### Plain sentences (Z2)
1. **Which series change AT the break date (CI contains 2025-10-23 and BH q <= .10).** First-hour range share rises on NQ (+0.071, break 2025-11-26), ES (+0.062, 2025-11-26) and YM (+0.087, 2025-12-19), not on RTY (market-wide among the three cap-weighted large-cap indices, as CAL found). On NQ also: share of RTH volume in 09:30-10:00 +1.7 pts (2025-11-26) and 09:30-10:30 +2.9 pts (2026-05-11, later), opening-minute volume spike +2.2x (2025-12-05, CI 2025-09-17..2025-12-19), closing-hour (15:00-16:00) volume share -1.0 pt (2025-09-24; ES -1.3 pts 2025-10-01), gap-fill rate within the day -10 pts (2025-10-24: the break date to the day; ES and YM later and not significant) and the OR-break continuation share -0.11 (2025-10-28, q .108, borderline; ES, RTY, YM show no break at all: NQ-ONLY, consistent with .55 -> .44).
2. **Market-wide but not at the break date.** Opening gap size jumps in mid-2024 on NQ (2024-07-18, +18 bp), RTY (2023-10), YM (2024-03) with CIs excluding 2025-10-23 (so the larger gaps are NOT the cause of an October 2025 reversion); pre-market volume share falls in April 2025 on all four (tariff-shock repricing, CI excludes the break date); pre-market range share falls in mid-2024 on all four; first-hour range per unit volume steps in 2023-2024; Globex volume share rises in 2026-02-27 on NQ, ES and RTY (+5.7 pts on NQ, CI 2026-01-29..2026-03-06, after the break date). The opening-minute volume spike also rises on RTY (2026-04) and YM (2025-12-19, CI starts 2025-11-11): same sign everywhere except ES, different dates.
3. **Which series line up with the fade bundle.** Same-day: OR-break continuation (NQ rho -0.55 over the sample, -0.50 in 2026 only; ES -0.29, RTY -0.12) and the 09:30-10:00 -> 10:00-10:30 reversal indicator (NQ +0.27, +0.29 in 2026; ES +0.23 / +0.36): these are the same event as the fade P&L (mechanically linked, not explanatory). Trailing-20-day mean predicting the next day: everything is small (|rho| <= 0.11): opening-minute spike +0.09 (q .08), first-hour illiquidity +0.10 (q .07), pre-market volume share -0.09 (q .08); no series predicts the bundle with |rho| >= .5. Quarter level (n = 15, both sides trending through the same break, so inflated): NQ share of volume in 09:30-10:00 +0.79 (q .025), opening spike +0.76 (q .032), OR-break continuation -0.73 (q .044); ES / YM show the same 09:30-10:00 and spike pattern (rho +0.58 / +0.64 not significant after BH).
4. **Decision rule (prereg).** No series explains the NQ reversion: the best candidates (opening spike, 09:30-10:00 volume share on NQ) break near the date and co-move with the bundle by quarter, but fail the trailing-20-day predictive test (|rho| < .5) and, for the volume share, the 2026-only day-level test (rho +0.02), and the quarter correlations are confounded by the common break. Descriptive picture: from Q4 2025 NQ (and, less, ES and YM) trades relatively more volume and range in the first hour, with larger opening-minute volume bursts, fewer gap fills and fewer OR-break continuations; RTY does not.
5. **NQ-only vs market-wide.** NQ-only: OR-break continuation, gap-fill rate within the day. Market-wide with NQ / ES / YM (RTY absent): first-hour range share. Market-wide at other dates: gap size (2024), pre-market volume and range share (2024-25), Globex share (Feb 2026). ZL-2 independently dates the NQ fade bundle step at 2026-02-10 (posterior median 2025-12-18, 90% interval 2025-08-15..2026-02-23), consistent with first-hour share, volume share and opening spike breaking on 2025-11-26..2025-12-19 and not with the gap-size or pre-market breaks.
Caveats: 1-min bars only (no trade counts, so no volume-per-trade proxy); change-point CIs are wide (single-break model on heavy-tailed daily series); data end 2026-10-16; sixty change-point tests with BH (q <= .10 reported); the quarter-level correlations use 15 points and trending series.
(Z2 reconciliation with section ZL-2, 2026-11-04 ~20:10Z: ZL-2's NQ OR-break hit rate has no significant break (p .125); my continuation-share series on NQ gives break 2025-10-28 with BH q .108 over 60 tests, i.e. the same borderline result - treat the "NQ-only OR-break change" as suggestive, not established. First-hour range share breaks: ZL-2 2025-12-02 (NQ), 2025-12-04 (ES), 2025-12-19 (YM); mine 2025-11-26 / 2025-11-26 / 2025-12-19: consistent within the CIs.)


## Section CAL (Q4 calendar / composition; CAL; 2026-11-04; append only). Prereg l2vast/ds3/prereg/Q4_CAL_prereg.md sha256 6c1ea96852e42f61d42aa4b211c840ef84bcfbd3b4ceec9227b61591627c6418 (before any statistic). Ledger Q4_CAL. Code l2vast/ds3/code/discover/{q4_sec_fetch,q4_study,q4_feas}.py; tables l2vast/ds3/out/q4_*.csv
Plain answer: the mix of mega-cap earnings days, index-event days, FOMC/CPI/NFP/opex days did NOT change around the 2026 NY-AM regime (shares before vs after 2025-10-23 are the same; none of the event-mix series shifts at the break dates), so the composition of event days is not the explanation. Earnings days do matter for the fade books and the live NY-AM sleeve, but in both periods: the day after a top-8 mega-cap after-close report the three-book fade bundle earns +1,230/day vs +5 on other days (p 0.013, n 88; 2023-25 +1,140, 2026 +1,541) and the live NY-AM sleeve earns +2,062/day more after any top-16 after-close report (p 0.001; 2023-25 +2,200, 2026 +1,710). A feasibility note for 'mega-cap earnings event books' is at the end: the move is large (about 63 pt in the first minutes after the release) but there is no continuation to trade without the surprise sign.

### (1) Calendar built
`autopilot/Q4_CAL_EVENTS.csv` (270 rows, DISCOVER_CALENDAR format): 250 earnings releases of AAPL, MSFT, NVDA, AMZN, GOOGL, META, TSLA, AVGO, COST, NFLX, AMD, CSCO, PEP, TMUS, ADBE, QCOM (2023-04-03..2026-11-02), each with the exact SEC EDGAR 8-K item 2.02 acceptance time (ET) from data.sec.gov/submissions, timing AMC (>= 16:00) or BMO (< 09:30); confidence 'source-confirmed' (the 8-K is filed within minutes of the press release; the first price reaction can precede it by 0-5 min); the nasdaq.com earnings API was blocked (Access Denied) and was not used. Tesla's pre-market 8-K 2.02 filings are production/delivery reports and are labelled TSLA_DELIVERIES_BMO, not earnings. Plus 15 Nasdaq-100 / S&P quarterly rebalance days (third Friday of Mar/Jun/Sep/Dec = triple witching; December = Nasdaq-100 annual reconstitution; rule-derived) and 4 Russell reconstitution Fridays (rule-derived; the 2026 date under the new schedule not verified). Gap: future earnings dates (Nov 2026 onward) are not in EDGAR until filed; the expected season is mid-January with the usual order (rule only, low confidence).
Top-8 events per year: 2023 (Apr-) 25, 2024 34, 2025 32, 2026 (to 11-02) 30.

### (3) Mix of event days before vs after the break (2025-10-23; 668 vs 267 label days)
| flag | share pre (668 days) | share post (267 days) | Fisher p |
|---|---|---|---|
| EARN_PREV_AMC8 | 0.096 | 0.090 | 0.90 |
| EARN_PREV_AMC16 | 0.186 | 0.184 | 1.00 |
| EARN_TODAY_BMO16 | 0.006 | 0.011 | 0.41 |
| EARN_WEEK8 | 0.341 | 0.326 | 0.70 |
| SEASON | 0.515 | 0.569 | 0.15 |
| INDEX_DAY | 0.015 | 0.015 | 1.00 |
| INDEX_PREV | 0.015 | 0.015 | 1.00 |
| E_FOMC_DECISION | 0.030 | 0.034 | 0.83 |
| E_CPI | 0.045 | 0.045 | 1.00 |
| E_NFP | 0.045 | 0.045 | 1.00 |
| OPEX | 0.046 | 0.045 | 1.00 |
| MAJOR_MACRO | 0.118 | 0.124 | 0.82 |
Shift tests at 2025-12-15 (ZL-2's q4_tools, window 120 days, placebo dates >= 60 days away): EARN_PREV_AMC8 +0.000 (t 0.0, p 1.00); EARN_PREV_AMC16 +0.000 (t 0.0, p 1.00); EARN_WEEK8 -0.042 (t -0.7, p 0.47); SEASON +0.125 (t 2.0, p 0.09); MAJOR_MACRO +0.025 (t 0.6, p 0.11); OPEX +0.008 (t 0.3, p 0.95); INDEX_DAY +0.008 (t 0.6, p 0.34). SEASON (days within +-10 calendar days of >= 3 top-16 reports) is higher after the break by 0.125 (t 2.0, p 0.09-0.14): 2026 contains more earnings-season days in the 120-day window after the break only because the window runs Dec-Mar and Oct-Nov; no structural change.

### (2) Day-level outcomes by flags known at the prior close (differences on flagged minus other days; $/day for the bundle at study lots (2 lots each) and the live NY-AM sleeve, points for gaps, share for the range and hit rate)
| flag | outcome | diff 2023-25 | diff 2026 | diff ALL |
|---|---|---|---|---|
| EARN_PREV_AMC8 | fade_bundle | +1140 (n 64, p 0.04) | +1541 (n 24, p 0.13) | +1229 (n 88, p 0.01) |
| EARN_PREV_AMC8 | abs_gap | +55 (n 64, p 0.00) | +73 (n 24, p 0.03) | +59 (n 88, p 0.00) |
| EARN_PREV_AMC8 | hitw | -0 (n 62, p 1.00) | -0 (n 24, p 0.48) | -0 (n 86, p 0.66) |
| EARN_PREV_AMC16 | sleeve | +2200 (n 124, p 0.00) | +1710 (n 49, p 0.03) | +2062 (n 173, p 0.00) |
| EARN_PREV_AMC16 | fade_bundle | +273 (n 124, p 0.52) | -311 (n 49, p 0.69) | +103 (n 173, p 0.78) |
| EARN_WEEK8 | fade_bundle | -117 (n 228, p 0.73) | +35 (n 87, p 0.95) | -94 (n 315, p 0.77) |
| EARN_WEEK8 | hitw | +0 (n 210, p 0.36) | -0 (n 77, p 0.87) | +0 (n 287, p 0.42) |
| SEASON | fade_bundle | +217 (n 344, p 0.48) | -464 (n 152, p 0.43) | +89 (n 496, p 0.79) |
| SEASON | hitw | +0 (n 321, p 0.25) | +0 (n 139, p 0.06) | +0 (n 460, p 0.07) |
| E_FOMC_DECISION | ohs | -0 (n 20, p 0.00) | -0 (n 9, p 0.00) | -0 (n 29, p 0.00) |
| MAJOR_MACRO | fade_bundle | -219 (n 79, p 0.68) | -82 (n 33, p 0.92) | -164 (n 112, p 0.74) |
66 cells (12 flags x 6 outcomes, ALL period): 4 with permutation p < 0.05; family max-|t| = 5.91 vs null median 2.84 / p95 4.84 (shuffled-day labels, 500 draws): family p = 0.018. The cells: EARN_PREV_AMC8 -> abs gap (+59 pt, p 0.002), EARN_PREV_AMC8 -> fade bundle (+1,229/day, p 0.013), EARN_PREV_AMC16 -> live NY-AM sleeve (+2,062/day, p 0.001), E_FOMC_DECISION -> first-hour range share (-0.20, p 0.001: the first hour holds less of the range on FOMC days). The opening-range hit rate does not depend on earnings weeks or after-earnings days in either period (EARN_PREV_AMC8 hit 0.47 vs 0.49 ALL; 2026 0.33 vs 0.42, p 0.48). What this means: the 2026 regime (bundle +1,006/day on NON-earnings days in 2026 vs -398 in 2023-25) exists independently of earnings days; earnings days are a shared amplifier of both the fades and the live sleeve in both periods (so a flag, not an explanation); the live NY-AM sleeve's money comes from post-earnings days (+2,336/day vs +274), including in 2026 (+1,680 vs -29).

### (4) Feasibility of 'mega-cap earnings event books'
117 top-8 after-close events with an 8-K accepted before 16:50 (about 33 a year; 8 names): the NQ move from 16:00 to 2 minutes after the 8-K acceptance has mean |move| 62.5 pt (MSFT 80, AMZN 95, NVDA 76, META 69, AAPL 57, GOOGL 52, AVGO 42, TSLA 29); to the next 09:30 the mean |move| is 190 pt, first hour 75-150 pt. Entering at the 1-minute close + 1 s after the filing: the continuation of the first move to 16:55 is -4.1 pt on average (hit 0.50) and to the next open -20.8 pt (hit 0.51): there is NO signless continuation or fade edge after the filing, because the price reaction is largely done by the filing time (the 8-K follows the press release by 0-5 min); AAPL releases at 16:30 and the 17:00-18:00 CME break stops trading, the window to 16:55 is 25 minutes. A book would need the EPS/guide surprise sign at the press-release second (consensus is not free; no news feed is on disk) plus a sub-second headline feed; with the live latency (signal at the 1-min close, first fill about 1 s later) the first move (the 60 pt that matters) is not capturable. Pre-market releases (PEP, TMUS, a few others) are 4 events in the sample, too few. Recommendation: no event book; the usable fact is the post-earnings-day flag for the fades and the live sleeve (known at the prior close, 9% of days for the top-8, 18% for the top-16), which is a day-selection overlay to be tested as a size modifier by its owners, not a new book.
Caveats: earnings dates from 8-K acceptance (ET) not from the press release; AAPL/AMZN 2023 filings may predate the 16:00 label; 'previous label day' uses CAL's label-day calendar; fade bundle in study lots; NY-AM sleeve from the Q1-A ts2 stack cube; day-level tests are not lot-adjusted; 66 + 12 + 22 + 8 tests registered in Q4_NTESTED.md.

## Section ZL-1: options / 0DTE structure by quarter around 2025-10-23 (broader options-flow view; ZL-1, 2026-11-04 ~20:00Z; prereg ZL1_Q4_OPTIONS_prereg.md sha256 370423a00bfe1b7c370fbb8b1b50a2d0c27211ec9aa8d9247779f50956ff6ad1, logged before any statistic; n_tested 110; append only)
**Plain sentence: the options market around NQ changed a lot between 2023 and 2026 (NDX option volume +72%, 0DTE share 59% -> 76%, CME NQ-option volume vs ES options +50%), but all of it is a steady secular climb that does not break at the NQ fade break (placebo ranks 0.04-0.89, p >= 0.115), and the only day-level associations with the fade bundle are two weak put/call effects (|rho| 0.1-0.13) that disagree in sign between targets: options flow is not a usable predictor of the 2026 reversion.**
Data used: OPRA NDX + NDXP daily bars 2023-04..2026-10-13 (volume per option symbol; expiry from the OSI symbol; 878 label days), NDX OPRA open interest (statistics type 9), CME NQ options (NQOPT_ohlcv-1d) and ES options (ES_ohlcv-1d), parent quarterly symbols only (weekly CME options are not in the parent file: coverage caveat); previous-day NQ raw close as the 'spot'. **Not on disk: SPX / SPXW OPRA (opts has only ES, NDX, NDXP, NQ), so an NDX-vs-SPX option-volume ratio cannot be built; the ES-option / NQ-option CME ratio is the substitute.** Volume features are lagged one label day (previous-day value for day d); OI is the pre-open value of day d.
### Availability (NDX-specific)
NDX open interest is essentially EMPTY 2023-04..2024-02 (mean total OI 3k-8k, a few contracts; 25k in 2024-02) and regular from 2024-03 (105-146k per day): the OI features (F7-F9) therefore cover 2024-03..2026-10 only (n 651 days). NDXP (PM-settled daily expiries) volume exists on every day from 2023-04 (mean 64k contracts/day vs NDX 6k): NDXP is 82% of NDX-complex volume in 2023Q2 and 94-95% since 2025Q3. So the 'NDX 0DTE availability dates' do not line up with the reversion regime; the OI gap ends 19 months before it.
### Level table by quarter (mean of the daily value; F1 contracts/day, F2 0DTE share, F3 NDXP share, F4 put/call volume, F5 volume within +-1% of spot, F10 NQ-option/ES-option volume, F7 OI put/call, F9 OI skew proxy; bundle = fade bundle $/day, rev = share of days the NQ OR break reversed)
| quarter | F1 | F2 | F3 | F4 | F5 | F10 | F7 | F9 | bundle | rev |
|--|--|--|--|--|--|--|--|--|--|--|
| 2023Q2 | 34.6k | .437 | .822 | .92 | .37 | .077 | n/a | n/a | -357 | .45 |
| 2023Q3 | 44.9k | .462 | .843 | 1.24 | .37 | .066 | n/a | n/a | +591 | .58 |
| 2023Q4 | 47.0k | .466 | .836 | 1.06 | .39 | .068 | n/a | n/a | -436 | .47 |
| 2024Q1 | 51.9k | .550 | .868 | .98 | .44 | .064 | 1.40 | 1.78 | -113 | .44 |
| 2024Q2 | 52.6k | .560 | .882 | 1.02 | .45 | .072 | 1.53 | 1.88 | -69 | .39 |
| 2024Q3 | 53.4k | .557 | .871 | 1.03 | .38 | .079 | 1.68 | 1.47 | -1,193 | .41 |
| 2024Q4 | 57.3k | .631 | .897 | 1.00 | .50 | .084 | 1.37 | 1.62 | -541 | .48 |
| 2025Q1 | 65.4k | .643 | .891 | .97 | .43 | .110 | 1.09 | 1.04 | -628 | .43 |
| 2025Q2 | 63.2k | .684 | .896 | 1.03 | .41 | .108 | 1.06 | 1.34 | -74 | .51 |
| 2025Q3 | 93.3k | .750 | .940 | 1.03 | .58 | .114 | 1.17 | 2.04 | +90 | .48 |
| 2025Q4 | 100.0k | .748 | .948 | 1.04 | .53 | .155 | 1.39 | 1.55 | +425 | .52 |
| 2026Q1 | 108.5k | .767 | .949 | 1.05 | .51 | .134 | 1.29 | 1.20 | +1,775 | .57 |
| 2026Q2 | 111.2k | .745 | .937 | 1.10 | .43 | .142 | .96 | 1.34 | +1,050 | .45 |
| 2026Q3 | 92.1k | .752 | .932 | 1.04 | .54 | .140 | 1.04 | 1.24 | +1,062 | .62 |
| 2026Q4 (partial) | 103.6k | .778 | .938 | 1.07 | .55 | .153 | 1.31 | 2.02 | +524 | .60 |
2026 vs 2023-25 (Welch t / Mann-Whitney): F1 volume 60.4k -> 103.8k (t 27.8); 0DTE share .590 -> .756 (t 23.7); NDXP share .881 -> .939 (14.3); F10 NQ/ES option volume .091 -> .139 (10.7); weekday-0DTE F11 .342 -> .444; put/call volume 1.029 -> 1.063 (t 2.7); volume near spot .440 -> .497 (6.0); OI put/call 1.333 -> 1.104 (t -12.1, 2024-03+); OI skew proxy 1.576 -> 1.297 (-7.0); OI within +-2% of spot .148 -> .139 (-2.4); 0DTE-near share unchanged (.562 -> .577, t 1.3). Weekday pattern: 2023-25 the 0DTE share was lowest on Friday (.573) and highest Tue/Wed (.656/.644); in 2026 it is flat across weekdays (.745-.766, daily NDXP expiries): the Mon/Wed/Fri 'expiry-day' structure disappeared.
### Do these series break where the NQ fade bundle breaks? (ZL-2 q4_tools.test_series_at_break, break 2025-12-15, window 120 days, placebo dates >= 60 days away)
F1 volume +10.8k (t 4.4, |t| rank .43, p .57); 0DTE share +.011 (rank .14, p .86); NDXP share +.001 (rank .04); put/call volume +.010 (rank .09); near-spot share -.060 (t -4.5, rank .73, p .27); 0DTE-near share -.059 (rank .84, p .16); NQ/ES -.001 (rank .05); weekday-0DTE .001; OI put/call -.120 (t -5.0, rank .13, p .87); OI near-spot share -.014 (rank .55); OI skew -.579 (t -8.6, rank .89, p .115). **None of the 11 series has a break at 2025-12-15 that exceeds the placebo dates (all p >= 0.115)**: the large 2023 -> 2026 shifts are slow trends (volume stepped +48% in 2025Q3, two quarters before the bundle regime; 0DTE share rose every year since 2023Q2).
### Day-level association with the fade bundle and with the OR-break reversal (66 Spearman tests, 3 samples x 2 targets x 11 features; features of day d-1 for volume, pre-open OI for day d; family null = 500 within-quarter label shuffles of max |rho|)
Raw p < 0.05 cells: OI put/call (F7) vs bundle $/day, all days from 2024-03: rho -0.130, p 0.0009, BH q 0.058, within-quarter rho -0.132 (p 0.0007), same sign in the 2023-25 part (-0.086) and 2026 (-0.096); put/call VOLUME (F4) vs OR-break reversal rate: rho +0.108, p 0.0018, q 0.061, 2023-25 +0.082 (p .038), 2026 +0.175 (p .017), within-quarter +0.084; others: F4 vs bundle (all) +0.074 (p .027), F1 volume vs bundle (all) +0.071, F2 0DTE share vs bundle (all) +0.070 (all q >= 0.37). Family p (max |rho| over the 11 features): bundle all 0.010, rev all 0.054, bundle 2023-25 0.24, bundle 2026 0.38, rev 2023-25 0.24, rev 2026 0.16. Rule outcome: **F7 (OI put/call) vs bundle and F4 (volume put/call) vs reversal both meet the preregistered rule (raw p <= 0.01, same sign in 2023-25 and 2026, family p <= 0.10), but they are tiny (|rho| 0.1-0.13, R-squared < 2%) and not coherent: more puts in the open interest means a LOWER fade-bundle P&L, more puts traded the previous day means MORE OR-break reversals.** Nothing else (0DTE share, NDXP share, near-spot volume, skew proxy, OI concentration, NQ/ES ratio, weekday-0DTE) is associated.
### Quarter level (15 quarters; Spearman of quarterly feature mean vs quarterly bundle mean / reversal rate)
F4 put/call volume rho +0.69 (p .004) with the bundle and +0.61 (p .015) with the reversal rate; 0DTE share +0.58 (p .023), NDXP share +0.57, total volume +0.55 (p .035), weekday-0DTE +0.54, NQ/ES ratio +0.49 (p .066) with the bundle. These are TREND-DRIVEN: every feature rises through 2023-2026 and the bundle turns positive in 2025Q3; with 15 trending points the quarter-level p-values are not valid evidence (the within-quarter day-level tests above are the clean ones). 
### Is there an NQ/NDX-specific options structure that matches the NQ-only reversion?
Descriptively yes in level: NQ-option volume relative to ES options nearly doubled (0.077 -> 0.14-0.155) and NDXP became 94-95% of NDX-complex volume with daily 0DTE expiries; but (a) these rose steadily since 2024Q4 / 2025Q1 (F10 .084 -> .110 -> .155), (b) the series do not break at the fade break (all p >= 0.115), (c) the day-level association with the fade P&L is limited to two put/call features of opposite sign. ES vs NQ comparison is only available through CME parent-option volume (SPX/SPXW OPRA is not on disk), so the 'NQ-only' contrast cannot be tested on the SPX side; with the ES / RTY / YM markets showing no reversion, the missing control is SPX/SPXW 0DTE volume, OI and the Russell/Dow option complexes.
### Gaps and caveats
SPX/SPXW OPRA absent; CME option files are parent-quarterly only (weekly NQ / ES options missing: the CME 0DTE share cannot be measured); NDX OI missing 2023-04..2024-02; NDXP OI not provided (statistics file is NDX only), so OI concentration/skew cover the PM-settled complex only through NDX monthlies and weeklies; no trade-side (customer vs dealer) information, so 'dealer gamma' signs are assumptions (CAL's FADE_GAMMA.md covers that: negative result); option volume near spot uses the futures-derived level (basis ignored).
### Program ideas from this slice (for the five-program list)
(1) SPX/SPXW + RUT + DJX OPRA 2022-2026 (daily bars + statistics) for a like-for-like NQ-vs-ES/RTY/YM options-structure panel and a difference-in-differences against the reversion (cost: OPRA daily ohlcv-1d/statistics for 3 roots, quote needed; why untested: only NDX/NDXP/ES/NQ were pulled). (2) OPRA TRADES with aggressor flags on NDXP 0DTE (2025-06..2026-06) to separate customer buying/selling and build a real intraday dealer-position proxy (cost: one year of NDXP trades; why untested: only daily bars and OI on disk). (3) CME weekly/serial NQ and ES option definitions + daily bars (all roots E1A..E5A, Q1A..Q5A, EW, QN) to measure the CME 0DTE share and the NQ-weekly volume step. 
Files: /mnt/l2/l2vast/q4_opt/ (vol_daily.parquet, oi_daily.parquet, q4_results.pkl); code code/q4_opt/ (q4_vol.py, q4_oi.py, q4_an.py).
