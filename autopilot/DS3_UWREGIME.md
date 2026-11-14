# DS3_UWREGIME - Unusual Whales as a range / day-type forecaster (W-UR1). Rebuilt 2026-11-14T06:44:12Z by code/th_uwregime/ur_loop.sh (every 3 h). Research only, NO trading in this page, NO PASS claim.
Prereg: autopilot/UWREGIME_PREREG.md (sha in DECISIONS.md, logged before scoring). Question: does UW forecast, out of sample, the session range / realized vol, trend-vs-chop, pinning and time of high/low, and by how much OVER a no-UW benchmark.

## 0. Method in six lines
- Sample: 552 trading days 2024-10-02..2026-11-12 (UW history starts 2024-10-01; NQ 1-min prices; ES for SPX/SPY pin). Expanding-window ridge, min 120 days, refit every 10 trading days (= 2 weeks); out-of-sample R2 is vs the expanding mean.
- Benchmark (no UW; VIX is NOT on the box, ATR used): lag-1/5/20-day mean of the same target, lag-1 and ATR14 of the same-session range, ATR14 of the RTH range; for 08:30/09:30/10:00 readings also the range so far today, realized vol so far, |move since prior close| and that move in ATR units. UW model = benchmark + ONE input group (<= 6 features). Gain = R2(UW model) - R2(benchmark), in percentage points of variance explained (pp).
- Readings: R0 prior close (UW rows up to the prior close + prior-day EOD level files), R1 08:30, R2 09:30, R3 10:00 ET; a UW minute row is used only at start+180 s; EOD files (gex levels, spot-strike, vol stats, dp levels, IV term) only from the previous trading day; futures move since the prior close maps UW spot to the reading time. Targets: session ln range, ln realized vol (range class); efficiency ratio, close extremity, mean crossings (day-type class); time of first / last extreme (timing).
- Nulls: shifted-time null = UW inputs from k trading days earlier, k in 8..60, 20 draws, same refit; "null q95" per row, "fam q95" = q95 over draws of the MAX gain across all groups AND readings for that session-target (so picking the best group/reading is already charged). 90% CI = 5-day block bootstrap of the daily squared-error difference.
- Verdict: YES = gain > 0 and CI low > 0 and gain > family null q95; weak = gain > 0 and > per-row null q95 only (not corrected for picking among groups/readings); no = otherwise.
- Caveat: the strict benchmark has no macro-event calendar (FOMC, CPI, NFP are not on the box). IV level and especially the IV term structure (front-end IV bump) partly carry that information, so gains of iv_term / iv_level are real forecasts but not necessarily gamma-specific. Gains from exposure inputs (gamma, flip, walls, charm, vanna) over ATR+IV+DOW are the cleaner UW-specific evidence.
- NDX spot glitches: UW NDX spot is rounded and often frozen for hours; each minute row is checked against the NQ-implied price (0.4% tolerance, 0.6% for ES/RTY/YM) and dropped if off. Glitch days (>25% of rows dropped): {'DIA': 2, 'IWM': 5, 'NDX': 67, 'QQQ': 3, 'SPX': 3, 'SPY': 3}. Days with no UW file: {'DIA': 21, 'IWM': 21, 'NDX': 21, 'QQQ': 21, 'SPX': 21, 'SPY': 21}. Futures: continuous series with >1.2%/min roll jumps removed (15 on NQ).

## 1. Headline (8008 scored rows = reading x session x target x input group)
- vs ATR benchmark: YES rows 225, weak rows 1028. vs the STRICT benchmark (ATR + IV level/rank + day-of-week; the VIX-alone stand-in): YES rows 95. Inputs with at least one YES (range class, vs ATR): ALL4:flip, ALL4:gamma, DIA:flip, DIA:iv_level, DIA:iv_minus_rv, DIA:iv_term, IWM:absflip_wall, IWM:flip, IWM:iv_level, IWM:iv_minus_rv, IWM:iv_term, IWM:walls, NDX:flip, NDX:iv_level, NDX:iv_minus_rv, NDX:iv_term, QQQ:absflip_wall, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:iv_level, QQQ:iv_minus_rv, QQQ:iv_term, QQQ:net_premium, QQQ:vanna, QQQ:walls, SPX:absflip_wall, SPX:charm, SPX:flip, SPX:gamma, SPX:iv_level, SPX:iv_minus_rv, SPX:iv_term, SPX:walls, SPY:flip, SPY:gamma, SPY:iv_level, SPY:iv_minus_rv, SPY:iv_term, SPY:walls, cal:dow, tide.
- Of those, YES also vs the strict benchmark (range class): ALL4:flip, DIA:iv_term, IWM:absflip_wall, IWM:flip, IWM:iv_term, NDX:flip, NDX:iv_term, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:iv_level, QQQ:iv_term, QQQ:vanna, QQQ:walls, SPX:charm, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:iv_term, SPY:walls, tide.
- YES vs strict benchmark (day-type class): DIA:iv_term, SPY:iv_term; (timing class): NDX:absflip_wall, NDX:flip, SPX:absflip_wall, cal:opex_day.
- Inputs with at least one YES (day-type class): DIA:gamma_chg, DIA:iv_term, IWM:iv_term, SPY:iv_term.
- Inputs with at least one YES (timing class): IWM:iv_term, NDX:absflip_wall, NDX:flip, SPX:vanna, cal:opex_day.


### Plain answer by session (strict benchmark = ATR + IV level/rank + day of week; "weak" = beats its own shifted-time null only)
| session | forecasts RANGE (strict YES) | best gain pp (input, reading, target) | forecasts DAY TYPE (strict YES) | forecasts TIMING of high/low (strict YES) |
|---|---|---|---|---|
| asia | ALL4:flip, NDX:iv_term, QQQ:iv_level, QQQ:iv_term, SPY:flip, tide | +9.8 (QQQ:iv_term, R0, lnrng) | SPY:iv_term | NO |
| london | ALL4:flip, NDX:iv_term, QQQ:iv_term, tide | +6.0 (QQQ:iv_term, R0, lnrv) | NO | SPX:absflip_wall |
| pre | ALL4:flip, IWM:absflip_wall, IWM:iv_term, NDX:iv_term, QQQ:iv_term, SPY:iv_term | +8.6 (IWM:iv_term, R0, lnrng) | NO | cal:opex_day |
| nyam | DIA:iv_term, IWM:iv_term, QQQ:iv_term, QQQ:vanna, SPX:charm, SPY:iv_term | +8.8 (QQQ:iv_term, R0, lnrv) | NO | NO |
| nypm | ALL4:flip, IWM:flip, NDX:flip, QQQ:flip, QQQ:iv_term, QQQ:walls, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:walls, tide | +5.0 (QQQ:flip, R3, lnrv) | DIA:iv_term | NO |
| nyam2 | IWM:iv_term, NDX:flip, SPX:charm, SPX:gamma, SPY:iv_term | +3.5 (SPX:charm, R3, lnrv) | NO | NO |
| late | ALL4:flip, IWM:flip, IWM:iv_term, NDX:flip, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:iv_term, QQQ:walls, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:iv_term, SPY:walls, tide | +6.6 (QQQ:flip, R3, lnrv) | NO | NDX:absflip_wall, NDX:flip |
## 2. Per session: every input, range yes/no and day type yes/no, gain over the no-UW benchmark (pp of R2)
Columns: best reading R# for the range class (ln range / ln RV) and for the day-type class (ER / close extremity / crossings); gain full OOS / L6M / L3M in pp; CI = 90% bootstrap on the full-OOS gain; nq95 = per-row shifted null q95; fq95 = family null q95 (max over groups and readings). Bench R2 = benchmark R2 for that target (how much the no-UW model already explains). Sorted by range gain. Only the top 14 groups per session by best of (range, day-type) gain are listed; the full table is in /mnt/l2/l2vast/_uwregime/forecast_all.csv.

### asia
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrng | +19.35 | +18.80 | +28.56 | [+9.15,+27.61] | +0.65 | +2.75 | 24 | +9.82 YES | weak | R0 | cross | +3.28 | +7.39 | +8.35 | [-0.65,+6.04] | +0.98 | +2.07 | -7 | +0.59 weak | weak |
| SPY:iv_term | YES | R0 | lnrng | +10.57 | +2.57 | +19.43 | [+5.25,+14.92] | +0.31 | +2.75 | 24 | +2.96 weak | YES | R0 | cross | +4.86 | +9.45 | +9.43 | [+0.77,+8.52] | +1.00 | +2.07 | -7 | +2.74 YES | weak |
| NDX:iv_term | YES | R0 | lnrng | +10.39 | +16.88 | +22.16 | [+6.52,+15.06] | -0.57 | +2.75 | 24 | +3.13 YES | no | R0 | er | -0.46 | -0.87 | -1.06 | [-1.63,+0.70] | -0.34 | +1.77 | -6 | +0.80 weak | no |
| SPY:flip | YES | R0 | lnrng | +8.18 | +14.56 | +15.83 | [+4.62,+12.53] | +0.03 | +2.75 | 24 | +1.93 YES | no | R0 | cext | -0.43 | +0.46 | -1.53 | [-1.57,+1.03] | -0.67 | +2.20 | -1 | -1.02 no | no |
| QQQ:iv_level | YES | R0 | lnrng | +8.04 | +14.58 | +21.81 | [+2.99,+12.86] | -0.52 | +2.75 | 24 | +2.45 YES | no | R0 | cross | -0.72 | -5.32 | -1.23 | [-3.08,+1.46] | -0.13 | +2.07 | -7 | -1.10 no | no |
| ALL4:flip | YES | R0 | lnrng | +7.67 | +11.78 | +12.43 | [+2.58,+11.51] | -0.35 | +2.75 | 24 | +2.42 YES | no | R0 | cross | -0.29 | +1.27 | +2.22 | [-3.40,+2.53] | -0.07 | +2.07 | -7 | -1.49 no | no |
| SPY:iv_level | YES | R0 | lnrng | +7.29 | +11.10 | +22.41 | [+2.40,+11.51] | -0.36 | +2.75 | 24 | +0.72 weak | weak | R0 | cross | +0.70 | -0.19 | +0.41 | [-1.22,+2.61] | -0.34 | +2.07 | -7 | +1.06 weak | no |
| SPX:iv_level | YES | R0 | lnrng | +6.22 | +8.42 | +17.73 | [+2.26,+11.58] | -0.60 | +2.75 | 24 | -0.17 no | weak | R0 | cross | +0.23 | +0.24 | +1.02 | [-0.79,+1.41] | -0.22 | +2.07 | -7 | -0.06 no | no |
| tide | YES | R0 | lnrv | +6.02 | +7.95 | +10.04 | [+3.84,+8.41] | +0.40 | +2.01 | 56 | +3.17 YES | no | R0 | er | +0.22 | +0.09 | -1.45 | [-1.14,+1.60] | +0.42 | +1.77 | -6 | +0.15 no | no |
| IWM:iv_term | YES | R0 | lnrng | +5.99 | -0.08 | +7.09 | [+1.60,+9.18] | +0.38 | +2.75 | 24 | +1.46 weak | weak | R0 | cross | +3.90 | +6.99 | +5.84 | [-0.01,+7.58] | +0.60 | +2.07 | -7 | +1.29 weak | weak |
| DIA:iv_level | YES | R0 | lnrng | +5.85 | +5.73 | +16.61 | [+1.59,+9.53] | -0.44 | +2.75 | 24 | -0.26 no | no | R0 | er | -0.09 | -0.98 | -2.08 | [-2.71,+2.14] | +0.89 | +1.77 | -6 | -0.10 weak | weak |
| DIA:iv_term | YES | R0 | lnrng | +5.80 | -4.02 | +13.27 | [-1.08,+10.21] | -0.41 | +2.75 | 24 | +0.29 weak | weak | R0 | cross | +2.24 | +4.72 | +5.02 | [-1.87,+5.80] | -0.15 | +2.07 | -7 | +0.84 weak | weak |
| SPX:gamma | YES | R0 | lnrv | +5.76 | +6.06 | +9.20 | [+3.07,+8.98] | -0.29 | +2.01 | 56 | +1.69 weak | no | R0 | er | -1.89 | -0.71 | -2.18 | [-3.51,-0.13] | -0.47 | +1.77 | -6 | -3.21 no | no |
| NDX:iv_level | YES | R0 | lnrv | +5.59 | +3.22 | +12.68 | [+2.42,+9.12] | -0.32 | +2.01 | 56 | +0.95 weak | no | R0 | er | -0.33 | -0.97 | -0.82 | [-1.49,+1.05] | +0.72 | +1.77 | -6 | -0.73 no | no |

### london
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrng | +12.66 | +15.75 | +14.87 | [+5.98,+17.83] | -0.07 | +1.61 | 19 | +4.03 YES | weak | R0 | cross | +0.62 | -4.23 | -7.65 | [-1.88,+3.11] | +0.01 | +1.93 | -2 | -0.32 no | no |
| SPY:iv_term | YES | R0 | lnrng | +8.22 | +8.66 | +6.12 | [+4.82,+12.82] | -0.23 | +1.61 | 19 | +1.27 weak | weak | R0 | cross | +0.65 | -4.41 | -7.50 | [-1.76,+2.87] | +0.08 | +1.93 | -2 | -0.61 no | no |
| NDX:iv_term | YES | R0 | lnrv | +8.21 | +10.67 | +11.13 | [+5.64,+10.69] | -0.08 | +0.93 | 51 | +2.76 YES | no | R0 | cext | -0.84 | -1.45 | -0.81 | [-2.00,+0.35] | -0.07 | +1.77 | -2 | -0.57 no | no |
| ALL4:flip | YES | R0 | lnrv | +7.78 | +0.22 | -0.70 | [+4.27,+12.14] | -0.17 | +0.93 | 51 | +3.10 YES | weak | R0 | er | +1.43 | +4.17 | +5.05 | [-0.33,+3.40] | -0.87 | +1.09 | -4 | +1.23 weak | weak |
| DIA:iv_term | YES | R0 | lnrng | +6.86 | +8.71 | +8.35 | [+3.41,+10.22] | -0.33 | +1.61 | 19 | +2.34 weak | no | R0 | cross | +0.07 | -0.70 | -3.89 | [-1.54,+1.53] | +0.19 | +1.93 | -2 | +0.01 weak | no |
| IWM:flip | YES | R0 | lnrng | +6.48 | +6.98 | +3.84 | [+1.91,+10.36] | -0.01 | +1.61 | 19 | +2.00 weak | weak | R0 | er | +1.20 | +2.79 | +0.92 | [-0.57,+3.09] | -0.00 | +1.09 | -4 | +0.13 weak | weak |
| SPY:flip | YES | R0 | lnrng | +6.33 | +9.39 | +2.49 | [+1.22,+13.85] | -0.99 | +1.61 | 19 | +1.60 weak | weak | R0 | er | +0.73 | +4.81 | +4.24 | [-1.08,+2.60] | -0.60 | +1.09 | -4 | -0.91 no | no |
| SPX:iv_term | YES | R0 | lnrng | +6.04 | +5.53 | +3.90 | [+3.15,+9.97] | -0.54 | +1.61 | 19 | +0.55 weak | no | R0 | cext | -0.71 | -2.17 | -5.99 | [-2.40,+0.63] | -0.89 | +1.77 | -2 | -0.99 no | no |
| SPX:iv_level | YES | R0 | lnrv | +5.77 | -4.29 | +1.53 | [+2.70,+8.49] | -0.39 | +0.93 | 51 | -0.09 no | no | R0 | cross | -0.58 | -1.30 | -0.12 | [-2.16,+0.89] | -0.44 | +1.93 | -2 | -0.17 no | no |
| SPY:iv_level | YES | R0 | lnrng | +5.68 | +15.82 | +18.70 | [+0.93,+13.14] | -0.49 | +1.61 | 19 | -0.02 no | no | R0 | er | -1.05 | -0.57 | -2.49 | [-2.46,+0.06] | -1.33 | +1.09 | -4 | -1.19 no | no |
| DIA:iv_level | YES | R0 | lnrv | +5.53 | -4.62 | +6.75 | [+1.37,+8.81] | -0.42 | +0.93 | 51 | -0.11 no | no | R0 | er | -0.64 | +0.06 | -1.49 | [-1.71,+0.21] | -1.19 | +1.09 | -4 | -0.42 no | no |
| SPY:gamma | YES | R0 | lnrv | +5.31 | -1.34 | +3.61 | [+2.35,+8.82] | -0.19 | +0.93 | 51 | +1.84 weak | no | R0 | cross | -1.99 | -0.77 | -2.03 | [-3.78,-0.11] | -0.64 | +1.93 | -2 | -1.56 no | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.20 | -1.59 | +2.69 | [+1.98,+8.59] | -0.46 | +0.93 | 51 | +1.53 no | no | R0 | cross | -1.44 | -5.29 | -6.06 | [-3.83,+0.69] | -1.09 | +1.93 | -2 | -1.09 no | no |
| SPX:gamma | YES | R0 | lnrv | +5.18 | +0.45 | +6.52 | [+2.64,+8.23] | -0.46 | +0.93 | 51 | +1.34 weak | weak | R0 | er | +0.87 | +1.20 | +1.11 | [-2.68,+4.40] | -0.17 | +1.09 | -4 | +1.02 weak | no |

### pre
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrv | +17.49 | +16.24 | +23.12 | [+12.65,+22.61] | +1.68 | +4.18 | 31 | +7.66 YES | no | R1 | er | -0.20 | -2.16 | -5.93 | [-2.12,+1.48] | -0.07 | +1.42 | -3 | +0.19 weak | weak |
| IWM:iv_term | YES | R0 | lnrng | +16.44 | +14.32 | +17.83 | [+9.08,+22.81] | +1.30 | +4.45 | 18 | +8.58 YES | weak | R0 | cross | +0.13 | -0.61 | -3.07 | [-1.46,+1.60] | -0.30 | +1.65 | -3 | -0.55 no | YES |
| SPY:iv_term | YES | R0 | lnrv | +13.75 | +4.82 | +15.84 | [+8.08,+18.36] | +1.86 | +4.18 | 31 | +4.45 YES | no | R0 | cross | -0.35 | -0.24 | -2.01 | [-1.56,+0.78] | -0.59 | +1.65 | -3 | -0.76 no | weak |
| DIA:iv_term | YES | R0 | lnrv | +12.21 | +4.10 | +16.43 | [+7.73,+16.66] | +2.44 | +4.18 | 31 | +3.18 weak | no | R0 | cross | -1.25 | -0.28 | -2.01 | [-2.73,-0.14] | -0.99 | +1.65 | -3 | -1.12 no | weak |
| NDX:iv_term | YES | R0 | lnrv | +9.48 | +15.75 | +26.63 | [+6.47,+12.73] | -0.11 | +4.18 | 31 | +2.09 YES | weak | R1 | cross | +0.08 | -3.18 | -2.74 | [-1.91,+1.78] | -0.12 | +1.65 | -5 | -0.18 weak | weak |
| ALL4:flip | YES | R0 | lnrv | +8.43 | +7.25 | +17.09 | [+5.39,+11.92] | -0.56 | +4.18 | 31 | +2.56 YES | no | R1 | cext | -1.44 | -3.47 | -1.17 | [-3.78,+0.74] | -1.32 | +1.80 | -4 | -1.44 no | no |
| SPX:iv_level | YES | R0 | lnrv | +7.38 | +4.05 | +13.70 | [+4.23,+10.82] | -0.55 | +4.18 | 31 | -0.23 no | no | R0 | cext | -0.60 | -0.11 | -0.18 | [-1.92,+0.63] | -1.07 | +1.80 | -3 | -0.08 no | no |
| DIA:iv_level | YES | R0 | lnrng | +6.95 | +4.26 | +3.90 | [+3.06,+12.54] | +0.52 | +4.45 | 18 | -0.12 weak | no | R0 | er | -0.81 | -0.52 | -0.66 | [-2.79,+1.29] | -0.82 | +1.42 | -1 | -0.22 no | no |
| SPY:iv_level | YES | R0 | lnrng | +6.87 | +3.31 | +0.65 | [+2.62,+12.20] | -0.23 | +4.45 | 18 | -0.20 weak | no | R0 | cext | -0.56 | +0.07 | +0.62 | [-2.11,+0.83] | -1.08 | +1.80 | -3 | -0.34 no | no |
| SPY:flip | YES | R0 | lnrv | +6.16 | +7.61 | +15.47 | [+2.28,+10.16] | -0.80 | +4.18 | 31 | -0.67 weak | no | R1 | cext | -0.25 | +0.12 | -0.54 | [-2.27,+1.46] | -0.91 | +1.80 | -4 | -0.08 weak | no |
| IWM:flip | YES | R0 | lnrv | +5.96 | +4.34 | +13.73 | [+2.56,+8.93] | -0.50 | +4.18 | 31 | +1.52 weak | no | R1 | cross | -1.06 | -0.93 | -0.87 | [-2.14,-0.03] | +0.07 | +1.65 | -5 | -1.30 no | no |
| IWM:iv_level | YES | R0 | lnrv | +5.60 | +3.61 | +11.66 | [+1.98,+9.83] | -0.59 | +4.18 | 31 | -0.85 no | no | R0 | er | -0.23 | -0.35 | -0.52 | [-3.09,+3.04] | -0.70 | +1.42 | -1 | -0.24 no | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.26 | +0.34 | +12.05 | [+1.33,+8.78] | -0.62 | +4.18 | 31 | +0.66 no | no | R1 | cext | -0.08 | +2.40 | +1.21 | [-1.96,+1.76] | -1.08 | +1.80 | -4 | +1.93 weak | no |
| SPX:iv_term | YES | R0 | lnrng | +5.25 | +3.89 | +4.50 | [-0.87,+10.29] | -0.22 | +4.45 | 18 | -0.88 no | weak | R1 | cross | +0.75 | -3.13 | -0.59 | [-1.34,+2.71] | -0.69 | +1.65 | -5 | +0.05 weak | weak |

### nyam
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrv | +14.75 | +16.34 | +10.13 | [+10.58,+18.75] | +2.26 | +3.45 | 39 | +8.80 YES | no | R0 | cext | -1.05 | -0.77 | -1.28 | [-1.90,-0.05] | -0.79 | +1.79 | -2 | -1.20 no | weak |
| SPY:iv_term | YES | R0 | lnrv | +11.10 | +10.00 | +10.35 | [+6.70,+15.96] | +2.05 | +3.45 | 39 | +7.34 YES | no | R0 | cext | -1.04 | -1.54 | -2.33 | [-2.17,+0.06] | -0.13 | +1.79 | -2 | -1.20 no | weak |
| DIA:iv_term | YES | R0 | lnrv | +10.16 | +6.45 | +8.96 | [+5.55,+15.28] | +2.70 | +3.45 | 39 | +4.95 YES | no | R2 | er | -0.51 | +0.61 | +0.18 | [-2.56,+1.81] | -0.98 | +1.35 | -6 | -0.57 no | no |
| IWM:iv_term | YES | R0 | lnrv | +9.26 | +9.00 | +5.98 | [+5.35,+13.70] | +2.14 | +3.45 | 39 | +7.06 YES | no | R0 | cext | -1.29 | -1.44 | -1.68 | [-2.25,-0.38] | -0.54 | +1.79 | -2 | -1.13 no | no |
| SPX:charm | YES | R1 | lnrv | +8.46 | +11.86 | -1.19 | [+3.31,+14.47] | +0.54 | +3.45 | 54 | +7.36 YES | no | R1 | cext | -0.62 | -1.75 | -0.50 | [-2.98,+1.24] | +0.15 | +1.79 | -4 | -0.32 no | no |
| QQQ:vanna | YES | R2 | lnrv | +6.73 | +7.70 | +0.71 | [+2.90,+11.15] | +0.67 | +3.45 | 57 | +5.24 YES | no | R1 | cross | -0.65 | +1.28 | +1.57 | [-2.06,+0.71] | -1.15 | +1.88 | -2 | -0.77 no | no |
| NDX:iv_term | YES | R0 | lnrv | +5.06 | +8.42 | +5.95 | [+2.32,+7.86] | -0.26 | +3.45 | 39 | +0.34 weak | no | R0 | cext | -0.48 | -0.55 | +0.60 | [-1.40,+0.62] | -0.17 | +1.79 | -2 | -0.69 no | no |
| SPY:flip | YES | R0 | lnrv | +4.56 | -1.94 | -6.21 | [+1.69,+7.07] | -0.50 | +3.45 | 39 | +0.89 weak | no | R0 | cross | -0.20 | -0.03 | -1.01 | [-1.38,+1.09] | -0.54 | +1.88 | -1 | -0.33 no | weak |
| ALL4:flip | YES | R0 | lnrv | +4.50 | -3.11 | -14.48 | [+1.22,+7.80] | -0.81 | +3.45 | 39 | +1.48 weak | weak | R2 | cross | +0.93 | +1.14 | +1.40 | [-1.11,+2.87] | -0.55 | +1.88 | -2 | +0.82 weak | no |
| QQQ:iv_level | YES | R0 | lnrv | +4.41 | +1.65 | -6.41 | [+0.28,+8.11] | -0.27 | +3.45 | 39 | +0.66 weak | no | R2 | cross | +0.26 | +2.91 | +1.58 | [-1.07,+1.53] | +0.72 | +1.88 | -2 | +0.19 no | no |
| SPX:iv_level | YES | R0 | lnrv | +4.14 | -2.15 | -4.05 | [+0.60,+7.52] | -0.25 | +3.45 | 39 | -0.09 no | weak | R0 | cext | +1.06 | -3.02 | -0.94 | [-1.09,+3.40] | -0.36 | +1.79 | -2 | -0.03 no | weak |
| SPY:gamma | YES | R0 | lnrv | +3.81 | -2.28 | -8.47 | [+0.70,+7.03] | -0.41 | +3.45 | 39 | +0.66 weak | no | R0 | cext | -1.14 | -0.45 | +2.19 | [-3.80,+0.95] | -0.10 | +1.79 | -2 | -1.72 no | no |
| SPY:iv_level | weak | R0 | lnrv | +3.72 | -1.12 | -2.77 | [-0.59,+7.49] | -0.21 | +3.45 | 39 | -0.36 no | weak | R0 | cext | +0.72 | -1.81 | +0.11 | [-0.88,+2.42] | -0.72 | +1.79 | -2 | -0.39 no | weak |
| SPX:gamma | YES | R0 | lnrv | +3.66 | +0.84 | -4.47 | [+1.60,+7.05] | -0.44 | +3.45 | 39 | +0.74 weak | no | R1 | cross | -1.47 | +0.35 | +1.00 | [-3.38,+0.31] | -1.40 | +1.88 | -2 | -1.84 no | no |

### nypm
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrv | +9.06 | +4.33 | -1.62 | [+6.59,+12.23] | +1.70 | +4.40 | 41 | +3.24 YES | weak | R3 | cross | +1.58 | +3.26 | +0.41 | [-0.85,+3.85] | -0.10 | +1.86 | -3 | +0.93 weak | no |
| SPY:iv_term | YES | R0 | lnrv | +6.61 | +1.62 | +6.21 | [+4.12,+9.67] | +1.38 | +4.40 | 41 | +1.74 weak | weak | R3 | cross | +1.06 | +3.38 | +2.43 | [-0.50,+2.66] | +0.01 | +1.86 | -3 | +0.93 weak | no |
| IWM:iv_term | YES | R1 | lnrv | +5.95 | +9.26 | +14.42 | [+3.62,+8.44] | +1.91 | +4.40 | 45 | +1.28 weak | YES | R3 | cross | +2.48 | +4.00 | +1.42 | [+0.51,+4.53] | -0.18 | +1.86 | -3 | +2.14 weak | no |
| DIA:iv_term | YES | R0 | lnrv | +5.30 | +0.96 | +5.70 | [+3.11,+8.02] | +1.40 | +4.40 | 41 | +1.06 weak | YES | R3 | cross | +2.66 | +8.55 | +7.13 | [+0.64,+4.65] | +0.03 | +1.86 | -3 | +3.22 YES | weak |
| QQQ:flip | YES | R3 | lnrv | +4.73 | +12.44 | +15.91 | [+2.06,+8.07] | -0.36 | +4.40 | 47 | +5.02 YES | no | R3 | er | -0.47 | -3.21 | -0.71 | [-2.03,+0.93] | +0.06 | +2.10 | -4 | -0.72 no | weak |
| SPY:flip | YES | R3 | lnrv | +4.57 | +7.85 | +10.97 | [+2.41,+7.60] | -0.11 | +4.40 | 47 | +3.69 YES | no | R2 | cext | -1.07 | +0.03 | +0.92 | [-2.67,+0.40] | -0.55 | +2.82 | -4 | -1.03 no | no |
| NDX:iv_term | YES | R0 | lnrv | +4.48 | +4.87 | -0.14 | [+2.48,+6.74] | +0.05 | +4.40 | 41 | +0.54 weak | weak | R2 | cross | +0.64 | +4.42 | +4.78 | [-0.86,+1.97] | +0.51 | +1.86 | -4 | +0.62 weak | no |
| cal:dow | weak | R1 | lnrv | +4.34 | +2.86 | +4.45 | [+1.75,+6.69] | +4.40 | +4.40 | 45 | +0.01 no | no | R2 | cext | -0.62 | +1.19 | -1.46 | [-2.73,+1.42] | -0.64 | +2.82 | -4 | -0.08 no | weak |
| QQQ:walls | weak | R3 | lnrv | +4.25 | +7.90 | +8.26 | [+1.40,+6.78] | -0.60 | +4.40 | 47 | +3.78 YES | no | R0 | cross | -1.60 | -1.44 | -3.40 | [-3.25,+0.03] | -1.70 | +1.86 | -3 | -1.65 no | no |
| SPX:flip | weak | R3 | lnrv | +4.06 | +5.22 | +8.60 | [+1.71,+6.82] | +0.10 | +4.40 | 47 | +3.49 YES | weak | R0 | cext | +0.44 | +0.83 | +2.48 | [-1.08,+1.99] | +0.87 | +2.82 | -1 | -0.11 weak | weak |
| ALL4:flip | weak | R3 | lnrv | +4.04 | +7.29 | +11.74 | [+1.49,+7.21] | +0.04 | +4.40 | 47 | +3.46 YES | no | R0 | cross | -0.38 | -2.77 | -0.02 | [-3.32,+2.24] | +0.00 | +1.86 | -3 | -0.46 no | no |
| IWM:flip | weak | R2 | lnrv | +3.91 | -0.61 | +1.24 | [+1.79,+6.10] | +0.15 | +4.40 | 46 | +3.24 YES | no | R0 | cross | -1.08 | -0.59 | -0.23 | [-1.73,-0.50] | +0.21 | +1.86 | -3 | -1.37 no | no |
| SPX:gamma | weak | R3 | lnrv | +3.83 | +7.13 | +11.45 | [+1.42,+5.98] | +0.13 | +4.40 | 47 | +2.53 YES | weak | R0 | cross | +0.63 | +4.76 | +4.16 | [-1.54,+2.91] | -0.68 | +1.86 | -3 | +0.21 weak | no |
| SPX:walls | weak | R3 | lnrv | +3.68 | +2.68 | +7.76 | [+1.38,+6.79] | -0.31 | +4.40 | 47 | +3.94 YES | weak | R2 | cext | +0.35 | -1.73 | -1.24 | [-1.72,+3.22] | -0.02 | +2.82 | -4 | -0.16 no | no |

### NY AM after 10:00 (10:00-12:00 ET, only from the 10:00 reading)
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R3 | lnrv | +5.38 | +9.55 | +13.28 | [+3.67,+7.74] | +2.80 | +3.27 | 60 | +3.00 YES | no | R3 | er | -0.23 | -0.75 | -0.20 | [-2.14,+1.96] | +1.43 | +2.54 | -6 | -0.48 no | no |
| SPY:iv_term | YES | R3 | lnrv | +4.53 | +7.47 | +7.95 | [+2.78,+6.39] | +2.29 | +3.27 | 60 | +2.14 YES | no | R3 | er | +0.38 | -0.14 | +1.52 | [-2.22,+2.81] | +0.80 | +2.54 | -6 | -0.04 no | weak |
| SPX:charm | YES | R3 | lnrv | +4.14 | +3.40 | -3.77 | [+1.03,+8.08] | +0.08 | +3.27 | 60 | +3.54 YES | no | R3 | cext | -1.94 | -2.27 | +0.55 | [-4.04,-0.07] | -0.89 | +2.94 | -4 | -2.49 no | weak |
| QQQ:iv_term | YES | R3 | lnrv | +3.99 | +6.23 | +5.37 | [+2.14,+5.90] | +2.68 | +3.27 | 60 | +0.53 no | no | R3 | cext | -1.18 | -0.97 | -1.29 | [-2.30,-0.15] | -0.79 | +2.94 | -4 | -0.58 no | weak |
| DIA:iv_term | YES | R3 | lnrv | +3.98 | +6.09 | +7.42 | [+2.36,+5.83] | +2.39 | +3.27 | 60 | +1.07 weak | no | R3 | er | -1.23 | -0.38 | +0.30 | [-2.93,+0.39] | +1.23 | +2.54 | -6 | -0.80 no | no |
| QQQ:vanna | YES | R3 | lnrv | +3.81 | +4.19 | -8.30 | [+0.70,+7.72] | +0.59 | +3.27 | 60 | +2.68 weak | no | R3 | er | -0.62 | -1.46 | +0.45 | [-3.33,+1.78] | -0.14 | +2.54 | -6 | -0.97 no | no |
| SPX:gamma | YES | R3 | lnrv | +3.43 | +3.06 | +0.84 | [+0.45,+7.04] | +0.02 | +3.27 | 60 | +3.01 YES | no | R3 | cext | -1.54 | +2.29 | +2.68 | [-3.42,+0.08] | -1.26 | +2.94 | -4 | -1.19 no | no |
| QQQ:zdte_share | weak | R3 | lnrv | +3.01 | +6.07 | +14.48 | [+1.46,+4.68] | +0.98 | +3.27 | 60 | +1.14 weak | no | R3 | cross | -0.89 | -1.50 | -4.63 | [-2.32,+0.81] | -0.18 | +2.37 | -8 | -0.83 no | no |
| NDX:gamma | weak | R3 | lnrv | +2.69 | +11.13 | +16.66 | [+0.07,+5.99] | +0.34 | +3.27 | 60 | +1.90 weak | no | R3 | er | -1.44 | -5.97 | -6.95 | [-4.77,+1.53] | -0.61 | +2.54 | -6 | -1.69 no | no |
| SPY:zdte_share | weak | R3 | lnrv | +2.68 | +6.17 | +12.93 | [+1.07,+4.24] | +1.09 | +3.27 | 60 | +1.23 weak | no | R3 | cross | -0.18 | +0.65 | -3.71 | [-1.89,+1.62] | -0.34 | +2.37 | -8 | -0.35 no | no |
| cal:dow | no | R3 | lnrv | +2.57 | +1.54 | +6.24 | [+1.11,+3.99] | +3.23 | +3.27 | 60 | +0.01 no | no | R3 | er | -0.01 | -0.16 | +0.72 | [-2.90,+2.38] | +0.30 | +2.54 | -6 | -0.05 no | no |
| NDX:flip | weak | R3 | lnrv | +2.29 | +2.73 | +9.28 | [+0.71,+4.17] | -0.04 | +3.27 | 60 | +2.20 YES | no | R3 | cext | +0.08 | +2.32 | +2.44 | [-1.86,+1.68] | +2.94 | +2.94 | -4 | -0.06 no | no |
| QQQ:gamma | weak | R3 | lnrv | +2.18 | +7.27 | +14.51 | [-1.96,+6.29] | +0.29 | +3.27 | 60 | +2.03 weak | no | R3 | cext | -0.66 | +0.17 | +2.61 | [-2.69,+1.15] | -1.08 | +2.94 | -4 | -1.31 no | no |
| QQQ:flip | weak | R3 | lnrv | +1.89 | +2.86 | +3.71 | [+0.13,+3.45] | +0.49 | +3.27 | 60 | +1.45 weak | no | R3 | er | -0.14 | +0.01 | -0.18 | [-1.63,+1.29] | -0.33 | +2.54 | -6 | +0.03 weak | no |

### last 90 min (14:30-16:00 ET), readings R0 and R3
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:iv_term | YES | R0 | lnrv | +7.12 | +5.67 | +2.27 | [+4.47,+9.84] | +0.60 | +2.22 | 39 | +3.40 YES | no | R3 | cross | -1.28 | -0.92 | -1.06 | [-2.41,-0.19] | +0.30 | +1.41 | -2 | -0.49 no | no |
| QQQ:flip | YES | R3 | lnrv | +6.28 | +12.94 | +14.16 | [+3.53,+9.77] | -0.45 | +2.22 | 45 | +6.64 YES | no | R3 | cross | -0.95 | -0.44 | -2.94 | [-1.96,+0.42] | -0.10 | +1.41 | -2 | -0.62 no | no |
| QQQ:walls | YES | R3 | lnrng | +6.06 | +2.48 | -3.86 | [+2.58,+10.52] | -1.07 | +2.81 | 29 | +6.08 YES | no | R0 | cross | -0.54 | -0.21 | -0.86 | [-1.95,+0.69] | -2.25 | +1.41 | -1 | -0.90 no | weak |
| SPY:iv_term | YES | R0 | lnrng | +5.57 | +9.69 | +7.33 | [+2.29,+9.77] | -0.16 | +2.81 | 27 | +2.50 YES | no | R3 | er | -0.28 | +0.74 | -0.49 | [-1.59,+0.86] | +0.05 | +1.65 | -3 | -0.36 no | no |
| DIA:iv_term | YES | R0 | lnrng | +5.49 | +8.70 | +5.57 | [+1.42,+9.00] | -0.24 | +2.81 | 27 | +2.41 weak | no | R3 | er | -0.59 | +0.55 | -2.29 | [-1.80,+0.65] | -0.05 | +1.65 | -3 | +0.41 weak | no |
| SPX:flip | YES | R3 | lnrv | +5.31 | +6.22 | +8.37 | [+3.20,+8.40] | -0.23 | +2.22 | 45 | +4.99 YES | weak | R0 | er | +0.56 | +0.59 | +0.36 | [-0.70,+1.67] | +0.00 | +1.65 | -3 | +0.48 weak | no |
| SPY:flip | YES | R3 | lnrv | +5.30 | +8.46 | +10.72 | [+3.10,+7.82] | -0.19 | +2.22 | 45 | +4.85 YES | no | R3 | er | -0.64 | +0.54 | -0.23 | [-1.81,+0.49] | -0.43 | +1.65 | -3 | -0.76 weak | no |
| ALL4:flip | YES | R3 | lnrv | +5.25 | +7.80 | +11.61 | [+2.86,+8.29] | -0.24 | +2.22 | 45 | +5.04 YES | no | R3 | cross | -1.03 | -1.56 | -2.89 | [-2.08,+0.06] | -0.07 | +1.41 | -2 | -1.03 no | weak |
| IWM:iv_term | YES | R0 | lnrng | +5.06 | +10.76 | +7.34 | [+2.34,+9.08] | -0.02 | +2.81 | 27 | +2.91 YES | no | R3 | er | -0.31 | -0.10 | -1.24 | [-1.35,+0.81] | +0.41 | +1.65 | -3 | -0.33 no | no |
| NDX:flip | YES | R3 | lnrv | +4.54 | +10.18 | +11.44 | [+2.18,+7.36] | -0.25 | +2.22 | 45 | +5.49 YES | no | R3 | er | -1.01 | -0.38 | -2.64 | [-2.18,+0.12] | -0.24 | +1.65 | -3 | -1.12 no | YES |
| SPX:walls | YES | R3 | lnrv | +4.49 | +6.42 | +11.03 | [+2.40,+7.10] | -0.37 | +2.22 | 45 | +4.66 YES | no | R3 | cext | -1.29 | +0.10 | +2.68 | [-3.51,+0.58] | -1.26 | +2.06 | -7 | -1.12 no | no |
| QQQ:impmove_vs_actual | YES | R3 | lnrv | +4.29 | +6.98 | +3.64 | [+1.18,+7.97] | -0.32 | +2.22 | 45 | +4.26 YES | no | R3 | er | -0.26 | +0.63 | +0.56 | [-1.38,+0.70] | -0.35 | +1.65 | -3 | -0.12 no | no |
| NDX:iv_term | YES | R0 | lnrv | +4.23 | +6.09 | +4.49 | [+2.26,+6.40] | +0.24 | +2.22 | 39 | +1.06 weak | no | R0 | er | -1.44 | -1.14 | -1.27 | [-3.65,+0.32] | -0.69 | +1.65 | -3 | -1.30 no | no |
| IWM:flip | YES | R0 | lnrng | +4.17 | -0.88 | -5.55 | [+1.41,+8.41] | -0.54 | +2.81 | 27 | +2.32 YES | no | R0 | er | -0.85 | -0.44 | -0.74 | [-1.86,+0.18] | -0.57 | +1.65 | -3 | -0.97 no | no |

## 3. Compact answer: input family x session, best ticker. R = range, T = day type; verdict vs ATR / vs strict (ATR+IV+DOW); gain pp vs ATR / vs strict
| input family | asia | london | pre | nyam | nypm | nyam2 | late |
|---|---|---|---|---|---|---|---|
| absflip_wall | R:YES/weak +3.9/+1.5 (SPX) ; T:weak/weak +1.2/+0.9 | R:YES/weak +2.5/+0.9 (IWM) ; T:weak/weak +1.5/+1.4 | R:weak/YES +4.0/+1.8 (IWM) ; T:weak/weak +0.3/+0.4 | R:weak/weak +1.4/+0.0 (DIA) ; T:weak/weak +0.7/+0.9 | R:weak/weak +0.9/+0.3 (QQQ) ; T:weak/weak +0.5/+0.1 | R:no/no +0.6/+0.4 (IWM) ; T:weak/no +0.6/-1.4 | R:weak/weak +1.9/+0.8 (QQQ) ; T:weak/weak +0.7/+1.0 |
| charm | R:weak/weak +0.5/+0.4 (SPX) ; T:weak/weak +0.6/+0.7 | R:weak/weak +2.1/+2.2 (SPY) ; T:weak/weak +0.3/-0.3 | R:weak/weak +1.9/+0.3 (SPX) ; T:weak/weak +1.1/+1.0 | R:YES/YES +8.5/+7.4 (SPX) ; T:weak/weak +0.7/+0.7 | R:weak/weak +1.1/-0.1 (QQQ) ; T:weak/weak +0.3/+0.5 | R:YES/YES +4.1/+3.5 (SPX) ; T:no/no -0.1/-0.4 | R:weak/no +0.4/-0.4 (SPX) ; T:no/no -0.2/-0.2 |
| delta | R:no/no -4.0/-3.0 (MEGA) ; T:no/no -4.3/-5.0 | R:no/no -2.9/-1.5 (MEGA) ; T:no/no -2.9/-4.4 | R:no/no -1.9/-0.7 (MEGA) ; T:no/no -3.6/-3.3 | R:no/no -0.9/-1.8 (MEGA) ; T:no/no -4.4/-4.9 | R:no/no -3.1/-3.9 (MEGA) ; T:no/no -1.4/-2.2 | R:no/no -0.5/-0.4 (MEGA) ; T:no/no -4.1/-4.3 | R:no/no -4.2/-4.3 (MEGA) ; T:no/no -4.9/-4.2 |
| dow | R:no/no +1.8/-0.0 (cal) ; T:no/no +1.7/-0.1 | R:no/no -0.0/-0.0 (cal) ; T:no/no +0.8/-0.1 | R:YES/no +4.5/+0.1 (cal) ; T:no/no -1.4/-0.1 | R:weak/no +3.2/+0.0 (cal) ; T:no/no -0.7/-0.1 | R:weak/no +4.3/+0.0 (cal) ; T:no/no -0.6/-0.1 | R:no/no +2.6/+0.0 (cal) ; T:no/no -0.0/-0.1 | R:no/no +2.0/-0.0 (cal) ; T:no/no -0.2/-0.1 |
| dp_levels | R:no/no -0.2/-1.4 (SPY) ; T:no/no -3.2/-3.5 | R:no/no -1.0/-1.8 (SPY) ; T:no/no -0.4/-0.5 | R:no/no -0.6/-0.5 (SPY) ; T:weak/no +0.2/-0.3 | R:no/no -1.9/-2.8 (QQQ) ; T:no/no -1.0/-1.1 | R:no/no -2.0/-1.2 (SPY) ; T:no/no -2.6/-2.8 | R:no/no -2.2/-2.0 (SPY) ; T:no/no -3.0/-3.0 | R:no/no -1.5/-0.2 (SPY) ; T:no/no -2.8/-2.8 |
| flip | R:YES/YES +8.2/+1.9 (SPY) ; T:weak/weak +0.4/+0.3 | R:YES/YES +7.8/+3.1 (ALL4) ; T:weak/weak +1.4/+1.2 | R:YES/YES +8.4/+2.6 (ALL4) ; T:weak/weak +0.0/+0.1 | R:YES/weak +4.6/+0.9 (SPY) ; T:weak/weak +0.9/+0.8 | R:YES/YES +4.7/+5.0 (QQQ) ; T:weak/weak +0.4/-0.1 | R:weak/YES +2.3/+2.2 (NDX) ; T:weak/weak +1.2/+1.0 | R:YES/YES +6.3/+6.6 (QQQ) ; T:weak/weak +0.7/+0.7 |
| gamma | R:YES/weak +5.8/+1.7 (SPX) ; T:weak/no +0.4/-0.1 | R:YES/weak +5.3/+1.8 (SPY) ; T:weak/weak +0.9/+1.0 | R:YES/weak +4.5/-0.8 (SPX) ; T:no/weak -0.5/+0.0 | R:YES/weak +3.8/+0.7 (SPY) ; T:no/weak -0.3/+0.2 | R:weak/YES +3.8/+2.5 (SPX) ; T:weak/weak +2.3/+2.1 | R:YES/YES +3.4/+3.0 (SPX) ; T:no/no -0.5/-0.6 | R:YES/YES +3.5/+3.0 (SPX) ; T:weak/weak +2.1/+1.9 |
| gamma_chg | - | - | - | - | R:weak/YES +1.9/+2.5 (SPX) ; T:weak/weak +0.5/+0.5 | R:weak/weak +0.4/+1.1 (NDX) ; T:weak/weak +0.4/+0.5 | R:weak/YES +1.6/+2.3 (SPX) ; T:YES/weak +1.8/+1.4 |
| gamma_sum | R:no/weak -0.5/+0.3 (MEGA) ; T:no/no -0.9/-1.1 | R:no/no -0.4/-0.1 (MEGA) ; T:no/no -0.7/-0.7 | R:weak/no +1.3/-0.3 (MEGA) ; T:no/no -1.0/-0.5 | R:weak/weak +2.3/+1.3 (MEGA) ; T:no/no -0.1/-0.3 | R:weak/no +1.0/+0.0 (MEGA) ; T:weak/no +0.1/-0.4 | R:weak/weak +1.6/+0.9 (MEGA) ; T:weak/weak +0.4/+0.2 | R:weak/no +0.3/-0.4 (MEGA) ; T:weak/weak +0.2/+0.6 |
| impmove_vs_actual | - | - | R:weak/weak +1.4/-0.1 (QQQ) ; T:weak/weak +0.7/+1.1 | R:weak/weak +1.9/+0.9 (QQQ) ; T:weak/weak +1.4/+1.0 | R:weak/weak +3.4/+3.0 (QQQ) ; T:weak/weak +0.5/+0.2 | R:no/no +0.5/-0.3 (QQQ) ; T:weak/weak +0.5/+0.5 | R:YES/YES +4.3/+4.3 (QQQ) ; T:weak/weak +0.6/+0.8 |
| iv_level | R:YES/YES +8.0/+2.4 (QQQ) ; T:weak/weak +0.7/+1.1 | R:YES/no +5.8/-0.1 (SPX) ; T:no/no -0.6/-0.2 | R:YES/weak +7.4/-0.2 (SPX) ; T:weak/weak +0.1/+2.1 | R:YES/weak +4.4/+0.7 (QQQ) ; T:weak/no +1.1/-0.0 | R:weak/weak +2.9/-0.1 (SPX) ; T:weak/weak +1.2/+1.7 | R:weak/weak +0.5/+0.6 (QQQ) ; T:no/no -0.2/-0.2 | R:weak/weak +2.3/-0.2 (SPX) ; T:weak/weak +0.2/+0.8 |
| iv_minus_rv | R:YES/no +3.4/-0.8 (DIA) ; T:no/weak +0.6/-0.0 | R:YES/no +2.9/-3.0 (SPX) ; T:weak/weak +0.2/+0.2 | R:weak/weak +3.2/-0.4 (IWM) ; T:no/weak -0.2/+0.2 | R:weak/weak +1.7/-1.9 (SPX) ; T:no/no -0.4/-0.6 | R:weak/no +0.6/-0.4 (DIA) ; T:weak/no +1.2/-0.1 | R:no/no -0.1/-0.2 (DIA) ; T:no/no -0.7/-0.7 | R:weak/no +0.4/-0.4 (DIA) ; T:no/no +0.5/+0.8 |
| iv_term | R:YES/YES +19.4/+9.8 (QQQ) ; T:YES/YES +4.9/+2.7 | R:YES/YES +12.7/+4.0 (QQQ) ; T:weak/weak +0.8/-0.4 | R:YES/YES +17.5/+7.7 (QQQ) ; T:weak/weak +0.7/+0.1 | R:YES/YES +14.7/+8.8 (QQQ) ; T:no/no -0.1/-0.3 | R:YES/YES +9.1/+3.2 (QQQ) ; T:YES/YES +2.7/+3.2 | R:YES/YES +5.4/+3.0 (IWM) ; T:no/no +0.4/-0.0 | R:YES/YES +7.1/+3.4 (QQQ) ; T:no/weak -0.3/-0.4 |
| month_end | R:no/no -0.2/-0.2 (cal) ; T:no/no -0.2/-0.1 | R:weak/weak +0.4/+0.2 (cal) ; T:no/no -0.3/-0.5 | R:no/no -0.3/-0.1 (cal) ; T:no/no -0.2/-0.3 | R:no/no -0.0/-0.1 (cal) ; T:no/no -0.5/-0.3 | R:no/weak +0.0/+0.7 (cal) ; T:weak/no +0.0/-0.0 | R:no/no -0.1/-0.2 (cal) ; T:weak/no +0.3/+0.3 | R:no/no +0.2/+0.4 (cal) ; T:no/no -0.2/-0.3 |
| net_premium | R:YES/weak +2.5/+0.8 (QQQ) ; T:weak/no +0.1/-0.0 | R:YES/weak +2.0/+1.0 (SPX) ; T:weak/weak +0.8/+0.7 | R:weak/weak +1.8/+0.5 (SPX) ; T:weak/weak +0.3/+0.3 | R:weak/weak +0.7/+0.7 (QQQ) ; T:weak/weak +0.8/+0.6 | R:no/weak -0.0/+0.1 (QQQ) ; T:weak/no +0.2/-0.2 | R:weak/weak +1.3/+1.1 (QQQ) ; T:weak/weak +0.9/+1.0 | R:weak/weak +0.7/+1.6 (SPX) ; T:weak/weak +1.0/+0.7 |
| opex_day | R:no/no -0.0/-0.0 (cal) ; T:no/weak +0.1/+0.3 | R:no/no -0.2/-0.3 (cal) ; T:no/no -0.5/-0.6 | R:weak/no +0.5/-0.3 (cal) ; T:no/no -0.0/+0.1 | R:no/no -0.1/-0.1 (cal) ; T:weak/weak +0.1/+0.3 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.3/-0.3 | R:no/no -0.1/-0.2 (cal) ; T:no/no -0.2/-0.1 | R:no/no +0.1/-0.2 (cal) ; T:no/no -0.3/-0.3 |
| opex_week | R:no/no -0.3/-0.2 (cal) ; T:no/no -0.1/+0.1 | R:no/no -0.4/-0.2 (cal) ; T:no/no -0.4/-0.4 | R:no/no +0.3/+0.3 (cal) ; T:weak/weak +1.2/+0.9 | R:weak/no +0.2/+0.1 (cal) ; T:no/weak +0.1/+0.3 | R:no/no -0.1/-0.1 (cal) ; T:no/weak +0.0/+0.0 | R:no/no -0.0/-0.2 (cal) ; T:weak/weak +0.6/+0.7 | R:no/no -0.1/-0.2 (cal) ; T:no/no +0.5/+0.3 |
| quarter_end | R:no/no -0.1/-0.2 (cal) ; T:no/no -0.5/-0.5 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.1/-0.1 | R:no/no -0.1/-0.5 (cal) ; T:no/no -0.0/-0.1 | R:no/no -0.2/-0.6 (cal) ; T:weak/weak +0.4/+0.4 | R:no/no -0.1/+0.0 (cal) ; T:weak/weak +0.3/+0.1 | R:no/no -0.3/-0.4 (cal) ; T:weak/weak +1.1/+1.0 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.1/-0.1 |
| tide | R:YES/YES +6.0/+3.2 (mkt) ; T:no/no +0.2/+0.1 | R:YES/YES +5.1/+3.2 (mkt) ; T:weak/no +0.2/-0.3 | R:weak/weak +2.3/+0.9 (mkt) ; T:weak/no +0.9/+0.1 | R:weak/weak +0.5/+0.5 (mkt) ; T:no/no -0.1/-0.2 | R:weak/YES +2.9/+2.8 (mkt) ; T:no/no -0.4/-0.7 | R:no/no -0.5/-0.1 (mkt) ; T:no/no -0.7/-0.7 | R:YES/YES +2.2/+2.5 (mkt) ; T:no/weak +0.1/+0.2 |
| vanna | R:weak/no +1.5/-0.3 (NDX) ; T:weak/weak +0.5/+0.2 | R:YES/weak +1.9/+1.4 (QQQ) ; T:weak/no +0.2/-0.6 | R:weak/weak +1.4/-1.9 (DIA) ; T:weak/weak +0.1/+0.6 | R:YES/YES +6.7/+5.2 (QQQ) ; T:weak/no +0.4/+0.3 | R:weak/weak +2.6/+0.4 (DIA) ; T:weak/weak +1.4/+0.7 | R:YES/weak +3.8/+2.7 (QQQ) ; T:weak/weak +0.2/+0.1 | R:weak/weak +1.5/+0.7 (DIA) ; T:no/no -0.6/-0.2 |
| walls | R:YES/weak +3.9/+0.8 (QQQ) ; T:weak/weak +2.3/+1.6 | R:YES/weak +3.8/+0.8 (SPY) ; T:no/no -0.7/-0.8 | R:weak/weak +2.3/-0.6 (SPX) ; T:no/weak -0.5/+0.5 | R:weak/weak +1.4/+0.4 (QQQ) ; T:no/no -0.2/-0.8 | R:weak/YES +4.3/+3.8 (QQQ) ; T:weak/weak +0.7/+1.0 | R:weak/weak +1.6/+2.1 (QQQ) ; T:weak/weak +0.7/-0.4 | R:YES/YES +6.1/+6.1 (QQQ) ; T:no/weak -0.4/+0.3 |
| zdte_share | R:weak/weak +0.0/+1.1 (SPX) ; T:weak/weak +1.4/+0.9 | R:weak/weak +0.6/-0.4 (SPY) ; T:weak/no +0.0/-0.5 | R:weak/weak +1.2/-0.1 (QQQ) ; T:weak/weak +1.7/+2.5 | R:weak/weak +1.8/+0.6 (SPY) ; T:weak/no +0.1/-0.7 | R:weak/weak +1.8/+1.0 (QQQ) ; T:weak/weak +0.5/-0.1 | R:weak/weak +3.0/+1.1 (QQQ) ; T:no/no -0.2/-0.4 | R:weak/weak +1.8/+1.4 (QQQ) ; T:weak/no +0.1/-0.2 |

## 4. Pinning to the largest gamma strike into the close (14:30 -> 16:00 ET)
q = ln((|P16:00 - K| + d) / (|P14:30 - K| + d)), d = 3 bps; q < 0 = pulled toward K. Placebo = the mirror strike (2 x prior close - K, same distance, no gamma information). "pin gain" = q(real K) - q(mirror) (negative = the real strike pins more than a mirror); CI90 block bootstrap; K: mag = gamma magnet (oi / vol), gk = largest gross gamma strike from spot-strike (oi / vol), call / put wall, flip. Prior-day EOD levels mapped to futures by the prior-close ratio.
| ticker | K | regime | n | q real | q mirror | pin gain | CI90 | shrink share real | mirror |
|---|---|---|---|---|---|---|---|---|---|
| QQQ | call_o | near&gamma+ | 92 | +0.028 | +0.160 | -0.132 | [-0.304,+0.087] | 0.46 | 0.43 |
| QQQ | mag_v | near&gamma+ | 117 | +0.128 | +0.204 | -0.077 | [-0.233,+0.067] | 0.41 | 0.40 |
| QQQ | call_o | gamma+ | 231 | -0.035 | +0.031 | -0.066 | [-0.144,+0.025] | 0.52 | 0.45 |
| SPY | put_o | gamma+ | 201 | -0.001 | +0.062 | -0.063 | [-0.144,+0.010] | 0.50 | 0.47 |
| SPY | put_o | near&gamma+ | 97 | +0.078 | +0.135 | -0.057 | [-0.206,+0.092] | 0.43 | 0.40 |
| QQQ | gk_v | near&gamma+ | 121 | +0.138 | +0.185 | -0.048 | [-0.148,+0.063] | 0.40 | 0.39 |
| SPY | gk_o | near&gamma+ | 100 | +0.075 | +0.122 | -0.047 | [-0.169,+0.049] | 0.46 | 0.40 |
| QQQ | mag_v | gamma+ | 231 | +0.012 | +0.053 | -0.041 | [-0.115,+0.040] | 0.46 | 0.46 |
| QQQ | mag_v | all | 507 | +0.023 | +0.058 | -0.035 | [-0.080,+0.010] | 0.46 | 0.45 |
| SPX | gk_o | gamma+ | 305 | +0.020 | +0.055 | -0.034 | [-0.089,+0.025] | 0.48 | 0.47 |
| SPX | call_o | gamma+ | 305 | +0.019 | +0.051 | -0.032 | [-0.097,+0.035] | 0.50 | 0.45 |
| SPY | put_o | all | 486 | +0.006 | +0.034 | -0.029 | [-0.073,+0.013] | 0.51 | 0.46 |
| SPY | gk_o | gamma+ | 201 | -0.017 | +0.011 | -0.028 | [-0.083,+0.024] | 0.53 | 0.47 |
| SPX | call_o | near&gamma+ | 90 | +0.138 | +0.161 | -0.024 | [-0.124,+0.093] | 0.40 | 0.44 |
| SPX | mag_v | near&gamma+ | 139 | +0.151 | +0.172 | -0.021 | [-0.113,+0.063] | 0.39 | 0.35 |
| NDX | gk_o | gamma+ | 406 | +0.008 | +0.029 | -0.021 | [-0.071,+0.029] | 0.46 | 0.48 |
| QQQ | gk_v | gamma+ | 231 | +0.021 | +0.040 | -0.019 | [-0.077,+0.041] | 0.46 | 0.46 |
| SPY | gk_v | gamma+ | 201 | -0.013 | +0.004 | -0.018 | [-0.085,+0.038] | 0.49 | 0.49 |
| NDX | call_o | gamma+ | 406 | -0.004 | +0.013 | -0.017 | [-0.068,+0.035] | 0.48 | 0.47 |
| SPY | gk_v | near&gamma+ | 107 | +0.062 | +0.077 | -0.016 | [-0.144,+0.067] | 0.44 | 0.43 |
| SPX | mag_v | gamma+ | 305 | +0.016 | +0.032 | -0.015 | [-0.060,+0.030] | 0.48 | 0.46 |
| SPX | mag_v | all | 506 | +0.017 | +0.032 | -0.014 | [-0.049,+0.019] | 0.48 | 0.47 |
| SPY | mag_o | near&gamma+ | 103 | +0.050 | +0.062 | -0.012 | [-0.133,+0.086] | 0.48 | 0.43 |
| SPX | call_o | all | 506 | +0.018 | +0.026 | -0.008 | [-0.051,+0.036] | 0.46 | 0.50 |

Cells with the CI entirely below 0 (real strike pins more than its mirror): 4 of 168 (cells are tickers x K types x regimes, so ~5% chance hits are expected). Cells with the CI entirely above 0 (strike REPELS): 22. The 24 most negative cells are listed above. In gamma+ days within 0.5 daily-sigma of the magnet (the case the user described) see regime near&gamma+.

## 5. Untested inputs: coverage and status
| input | status |
|---|---|
| IV stats (iv, iv rank, iv/rv, iv-rv) | scored above (families iv_level, iv_minus_rv) |
| IV term slope / front implied move | scored above (iv_term); history pulled for NDX SPX QQQ SPY by W-UR1 (newest first, running; rows with missing term-structure files are NaN) |
| IWM, DIA gamma/vanna/charm/levels | scored above (tickers IWM, DIA; history from 2025-02) |
| dark-pool levels (QQQ, SPY) | scored (family dp_levels); only 260 days (2025-11-14..) so the OOS sample is ~140 days: low power |
| megacap exposure (daily greek exposure NVDA AAPL MSFT AMZN META GOOGL TSLA: gamma, vanna, charm, delta, summed gamma z; prior-day value, since 2024-11-14) | scored above (tick MEGA; families gamma, vanna, charm, delta, gamma_sum) |
| megacap flow / dark-pool levels / megacap intraday spot | waiting: megacap spot_1m and net_prem_ticks pull (W-UB3 chain C) and dp_levels need the megacap price; scored when they land |
| options tape by DTE and >= $100k | tape_agg/tape_big only cover ~50 days (2026-09-03..) so no out-of-sample test is possible yet (W-UB2 filling); screened when >= 200 days |
| opex week / opex day / month-end / quarter-end | scored above (family cal) |

## 6. Status
- Page 1 (forecast test) is this page. Page 2 (use on D7 dials with the exact engine) starts only for inputs with YES or weak range/day-type rows; nothing is run on the engine yet.

## 7. PAGE 2: use on D7 dials (JN05W2 base, all layers ON; FIRST ORDER on the exact-engine trade table; exact-engine confirmation below when run)
Dial cells = (day-regime tag state) x (book) x (session scope) x action: size x0.5 / x1.5 / skip (pnl scaled on matched trades, fees not rescaled) or hold-at-cut (hold_pnl instead of the cut exit pnl on StateCut/EarlyCut/StackCut/BookLock trades). Regime tags come from the forecast inputs of sections 2-3 at the reading of the signal clock (R0 before 08:30 and after 18:00, R1 08:30, R2 09:30, R3 10:00): gamma sign (SPX QQQ NDX SPY, vote), above/below flip, nearness to flip, IV z (NDX SPX), Tide z, IV-RV, call/put room, and the walk-forward predicted RTH range from the UW model (rngU) and its excess over the ATR benchmark (rngU_ex) (first prediction after 120 days, 2025-03 on).
Gate (tolerant): L6M>0, HOLD>0, excess over the same action on the whole book x scope >0 in L6M and HOLD (removes the plain scale-up-a-profitable-book effect), L3M>=0, worst week not worse in HOLD and L6M, max DD not worse in HOLD and L6M, n>=20 in L6M. Rank = drawdown first (HOLD+L6M worst-week gain + max-DD reduction, $k) then mean. Family null = best gated drawdown score when tags are permuted within month (30 draws), q95 = 48.9 $k; placebo = same with tags from k days earlier (20 draws): max 75.4, median 36.3.
Gated cells: 515 of 15201; above the family-null q95: 0; above the placebo max: 0.

### size x1.5 (press) / x0.5 (half) / skip, best gated cell per book
| regime state | book | scope | action | n L6M | L1M $/wk | L3M | L6M | HOLD | PREUW | excess over whole-book action L6M / HOLD | worst week chg HOLD / L6M | max DD cut HOLD / L6M | full stops/wk removed | dd score $k | vs family null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tide >0 | K7 | london | 0.0 | 195 | +2318 | +951 | +769 | +401 | -649 | +966 / +700 | +2477 / +4992 | +14016 / +4992 | 0.11 | +26.5 | within null |
| tide >q50 | K7 | london | 0.0 | 215 | +1986 | +797 | +741 | +328 | -515 | +957 / +655 | +2477 / +4992 | +13268 / +4992 | 0.11 | +25.7 | within null |
| ivSPX >0 | P7 | asia | 0.0 | 171 | +950 | +436 | +250 | +293 | -1440 | +3792 / +4196 | +17009 / +10345 | +6732 / +11124 | 0.04 | +45.2 | within null |
| ivSPX >0 | P7 | asia | 0.5 | 171 | +475 | +218 | +125 | +147 | -720 | +1896 / +2098 | +8505 / +9757 | +3366 / +11025 | 0.00 | +32.7 | within null |
| abvflipQQQ >q50 | U7 | london | 0.0 | 59 | +1041 | +447 | +143 | +240 | -309 | +902 / +697 | +2327 / +7197 | +15113 / +7197 | 0.99 | +31.8 | within null |
| tide >q66 | U7 | london | 0.0 | 44 | +1746 | +352 | +569 | +160 | -262 | +1136 / +538 | +0 / +7197 | +10173 / +7197 | 0.76 | +24.6 | within null |
| nearflipSPX <q66 | M7 | all | 0.0 | 486 | +718 | +143 | +448 | +380 | -1106 | +477 / +349 | +8465 / +1919 | +16868 / +1488 | 0.76 | +28.7 | within null |
| nearflipSPX <q66 | M7 | london | 0.0 | 324 | +1371 | +791 | +772 | +817 | -425 | +554 / +618 | +8465 / +1309 | +15890 / +878 | 0.53 | +26.5 | within null |
| abvflipSPX >q50 | H7 | all | 1.5 | 98 | +1565 | +664 | +1022 | +484 | +123 | +461 / +302 | +0 / +3599 | +3302 / +3599 | 0.00 | +10.5 | within null |
| abvflipSPX >0 | H7 | all | 1.5 | 100 | +1565 | +664 | +1038 | +486 | +253 | +465 / +295 | +0 / +3599 | +3302 / +3599 | 0.00 | +10.5 | within null |
| ivrv <q50 | A7 | all | 1.5 | 158 | +276 | +79 | +203 | +322 | +461 | +30 / +142 | +0 / +964 | +1137 / +964 | 0.00 | +3.1 | within null |
| ivrv <q50 | A7 | asia | 1.5 | 158 | +276 | +79 | +203 | +322 | +461 | +30 / +142 | +0 / +964 | +1137 / +964 | 0.00 | +3.1 | within null |
| ivNDX <=0 | O7 | nyam | 1.5 | 31 | -217 | +314 | +294 | +315 | +183 | +157 / +151 | +899 / +0 | +1799 / +0 | 0.00 | +2.7 | within null |
| ivNDX <=0 | O7 | all | 1.5 | 31 | -217 | +314 | +294 | +315 | +183 | +157 / +151 | +899 / +0 | +1799 / +0 | 0.00 | +2.7 | within null |
| tide >q66 | ALL | london | 0.0 | 448 | +4011 | +2393 | +1898 | +528 | -2039 | +2551 / +1343 | +0 / +10710 | +3756 / +12318 | 1.26 | +26.8 | within null |
| tide >q66 | ALL | london | 0.5 | 448 | +2006 | +1196 | +949 | +264 | -1019 | +1276 / +672 | +0 / +6159 | +12854 / +6159 | 0.00 | +25.2 | within null |

### hold at cut (cut/lock by day type), best gated cells
| regime state | book | scope | action | n L6M | L1M $/wk | L3M | L6M | HOLD | PREUW | excess over whole-book action L6M / HOLD | worst week chg HOLD / L6M | max DD cut HOLD / L6M | full stops/wk removed | dd score $k | vs family null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| nearflipQQQ >q50 | K7 | all | H | 385 | +2066 | +290 | +543 | +793 | +1024 | +447 / +569 | +506 / +4882 | +1275 / +4882 | 0.00 | +11.5 | within null |
| nearflipNDX >q50 | K7 | all | H | 461 | +759 | +323 | +377 | +279 | +319 | +262 / +68 | +2545 / +1500 | +2018 / +1500 | 0.00 | +7.6 | within null |
| abvflipSPY <q33 | P7 | london | H | 59 | -376 | +1519 | +228 | +391 | +519 | +611 / +359 | +2219 / +0 | +9319 / +0 | 0.00 | +11.5 | within null |
| abvflipSPX <=0 | P7 | london | H | 86 | -2721 | +1656 | +207 | +523 | +1160 | +766 / +469 | +165 / +0 | +10855 / +0 | 0.00 | +11.0 | within null |
| tide <q66 | M7 | london | H | 186 | -1741 | +75 | +252 | +1150 | +685 | +159 / +684 | +13479 / +2969 | +5262 / +6135 | 0.00 | +27.8 | within null |
| abvflipSPX <q50 | M7 | london | H | 130 | -1522 | +61 | +116 | +673 | +449 | +51 / +286 | +10862 / +0 | +9284 / +3167 | 0.00 | +23.3 | within null |
| gSPX <q33 | ALL | london | H | 190 | -321 | +2145 | +281 | +1349 | +646 | +735 / +1132 | +10982 / +7860 | +5983 / +8855 | 0.00 | +33.7 | within null |
| nearflipQQQ >q66 | ALL | london | H | 218 | -901 | +1314 | +12 | +1680 | +2175 | +533 / +1446 | +347 / +7860 | +15739 / +5010 | 0.00 | +29.0 | within null |

### The user hypothesis: mean reversion (K7) favoured in POSITIVE gamma, trend/pullback (P7, U7) in NEGATIVE gamma; size x0.5 / x1.5 by book, all sessions (not gated; every row shown)
| regime state | book | scope | action | n L6M | L1M $/wk | L3M | L6M | HOLD | PREUW | excess over whole-book action L6M / HOLD | worst week chg HOLD / L6M | max DD cut HOLD / L6M | full stops/wk removed | dd score $k | vs family null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| gSPX <=0 | K7 | all | 0.5 | 486 | -1602 | -381 | -309 | -7 | -610 | +470 / +693 | -4557 / +171 | +7262 / +2740 | 0.00 | +5.6 | within null |
| gSPX <=0 | K7 | all | 1.5 | 486 | +1602 | +381 | +309 | +7 | +610 | -470 / -693 | +2898 / -171 | -7262 / -2740 | 0.00 | -7.3 | within null |
| gSPX >0 | K7 | all | 0.5 | 1012 | -1041 | -1338 | -1962 | -1434 | -57 | -339 / -448 | +2808 / +4567 | +12867 / +4567 | 0.00 | +24.8 | within null |
| gSPX >0 | K7 | all | 1.5 | 1012 | +1041 | +1338 | +1962 | +1434 | +57 | +339 / +448 | -2808 / -4567 | -12867 / -4567 | 0.00 | -24.8 | within null |
| gSPX <=0 | P7 | all | 0.5 | 301 | +2774 | -517 | -471 | -770 | -1021 | +1408 / +1244 | +10816 / +6820 | +12599 / +11125 | 0.00 | +41.4 | within null |
| gSPX <=0 | P7 | all | 1.5 | 301 | -2774 | +517 | +471 | +770 | +1021 | -1408 / -1244 | -10816 / -6820 | -12599 / -11125 | 0.00 | -41.4 | within null |
| gSPX >0 | P7 | all | 0.5 | 698 | -877 | -3640 | -5554 | -4188 | -1108 | -1196 / -1187 | +1608 / +8706 | -4586 / +8706 | 0.00 | +14.4 | within null |
| gSPX >0 | P7 | all | 1.5 | 698 | +877 | +3640 | +5554 | +4188 | +1108 | +1196 / +1187 | -1608 / -8706 | +4586 / -8706 | 0.00 | -14.4 | within null |
| gSPX <=0 | U7 | all | 0.5 | 80 | -682 | -310 | -457 | -215 | -573 | +129 / +216 | +3154 / -459 | +9748 / -1061 | 0.00 | +11.4 | within null |
| gSPX <=0 | U7 | all | 1.5 | 80 | +682 | +310 | +457 | +215 | +573 | -129 / -216 | -3154 / +459 | -9748 / +1061 | 0.00 | -11.4 | within null |
| gSPX >0 | U7 | all | 0.5 | 184 | -1269 | -1711 | -1216 | -875 | -24 | +132 / -170 | +3222 / +1203 | -636 / +1203 | 0.00 | +5.0 | within null |
| gSPX >0 | U7 | all | 1.5 | 184 | +1269 | +1711 | +1216 | +875 | +24 | -132 / +170 | -5728 / -1203 | +636 / -1203 | 0.00 | -7.5 | within null |
| gQQQ <=0 | K7 | all | 0.5 | 961 | -1031 | -154 | -991 | -404 | -403 | +550 / +719 | -1750 / +4738 | +5440 / +7307 | 0.00 | +15.7 | within null |
| gQQQ <=0 | K7 | all | 1.5 | 961 | +1031 | +154 | +991 | +404 | +403 | -550 / -719 | +1750 / -4738 | -5440 / -7307 | 0.00 | -15.7 | within null |
| gQQQ >0 | K7 | all | 0.5 | 537 | -1613 | -1565 | -1280 | -1037 | -263 | -419 / -475 | +0 / +0 | +14688 / +0 | 0.00 | +14.7 | within null |
| gQQQ >0 | K7 | all | 1.5 | 537 | +1613 | +1565 | +1280 | +1037 | +263 | +419 / +475 | +0 / +0 | -14688 / +0 | 0.00 | -14.7 | within null |
| gQQQ <=0 | P7 | all | 0.5 | 613 | +3674 | -687 | -2490 | -2529 | -470 | +1338 / +722 | +12424 / +15027 | +6814 / +16397 | 0.00 | +50.7 | ABOVE null |
| gQQQ <=0 | P7 | all | 1.5 | 613 | -3674 | +687 | +2490 | +2529 | +470 | -1338 / -722 | -12424 / -15526 | -6814 / -19831 | 0.00 | -54.6 | within null |
| gQQQ >0 | P7 | all | 0.5 | 386 | -1777 | -3470 | -3535 | -2429 | -1660 | -1125 / -665 | +0 / +0 | +1199 / +0 | 0.00 | +1.2 | within null |
| gQQQ >0 | P7 | all | 1.5 | 386 | +1777 | +3470 | +3535 | +2429 | +1660 | +1125 / +665 | +0 / +0 | -1199 / +0 | 0.00 | -1.2 | within null |
| gQQQ <=0 | U7 | all | 0.5 | 159 | -564 | -935 | -1130 | -375 | -294 | +35 / +308 | +8721 / +744 | +2676 / +142 | 0.00 | +12.3 | within null |
| gQQQ <=0 | U7 | all | 1.5 | 159 | +564 | +935 | +1130 | +375 | +294 | -35 / -308 | -8883 / -744 | -2676 / -142 | 0.00 | -12.4 | within null |
| gQQQ >0 | U7 | all | 0.5 | 105 | -1388 | -1087 | -543 | -715 | -304 | +226 / -262 | +0 / +0 | +6437 / +0 | 0.00 | +6.4 | within null |
| gQQQ >0 | U7 | all | 1.5 | 105 | +1388 | +1087 | +543 | +715 | +304 | -226 / +262 | +0 / +0 | -6437 / +0 | 0.00 | -6.4 | within null |
| gNDX <=0 | K7 | all | 0.5 | 341 | -1318 | -532 | -259 | -234 | -153 | +288 / +94 | -3021 / +1869 | +1269 / +4438 | 0.00 | +4.6 | within null |
| gNDX <=0 | K7 | all | 1.5 | 341 | +1318 | +532 | +259 | +234 | +153 | -288 / -94 | +165 / -1869 | -1269 / -4438 | 0.00 | -7.4 | within null |
| gNDX >0 | K7 | all | 0.5 | 1157 | -1325 | -1187 | -2012 | -1207 | -514 | -157 / +151 | +490 / +2869 | +12380 / +2869 | 0.00 | +18.6 | within null |
| gNDX >0 | K7 | all | 1.5 | 1157 | +1325 | +1187 | +2012 | +1207 | +514 | +157 / -151 | -1271 / -2869 | -18860 / -2869 | 0.00 | -25.9 | within null |
| gNDX <=0 | P7 | all | 0.5 | 188 | +1695 | -478 | +60 | -403 | -448 | +1234 / +518 | +1844 / +2463 | +1352 / +6769 | 0.00 | +12.4 | within null |
| gNDX <=0 | P7 | all | 1.5 | 188 | -1695 | +478 | -60 | +403 | +448 | -1234 / -518 | -1844 / -2463 | -1352 / -6769 | 0.00 | -12.4 | within null |
| gNDX >0 | P7 | all | 0.5 | 811 | +202 | -3678 | -6085 | -4554 | -1681 | -1021 / -461 | +10580 / +13063 | +6661 / +13063 | 0.00 | +43.4 | within null |
| gNDX >0 | P7 | all | 1.5 | 811 | -202 | +3678 | +6085 | +4554 | +1681 | +1021 / +461 | -10580 / -13063 | -6661 / -13063 | 0.00 | -43.4 | within null |
| gNDX <=0 | U7 | all | 0.5 | 62 | +7 | +467 | -66 | +71 | -673 | +388 / +306 | +2455 / +3137 | +3493 / +2535 | 0.00 | +11.6 | within null |
| gNDX <=0 | U7 | all | 1.5 | 62 | -7 | -467 | +66 | -71 | +673 | -388 / -306 | -2455 / -3137 | -3493 / -2535 | 0.00 | -11.6 | within null |
| gNDX >0 | U7 | all | 0.5 | 202 | -1958 | -2488 | -1607 | -1161 | +76 | -127 / -260 | +4543 / -2393 | +5620 / -2393 | 0.00 | +5.4 | within null |
| gNDX >0 | U7 | all | 1.5 | 202 | +1958 | +2488 | +1607 | +1161 | -76 | +127 / +260 | -6428 / +2393 | -5620 / +2393 | 0.00 | -7.3 | within null |
| gSPY <=0 | K7 | all | 0.5 | 985 | -2165 | -405 | -1092 | -767 | -774 | +487 / +409 | -4557 / +4738 | +9569 / +7307 | 0.00 | +17.1 | within null |
| gSPY <=0 | K7 | all | 1.5 | 985 | +2165 | +405 | +1092 | +767 | +774 | -487 / -409 | +2898 / -4738 | -9569 / -7307 | 0.00 | -18.7 | within null |
| gSPY >0 | K7 | all | 0.5 | 513 | -479 | -1314 | -1179 | -674 | +107 | -356 / -165 | +2808 / +0 | +10560 / +0 | 0.00 | +13.4 | within null |
| gSPY >0 | K7 | all | 1.5 | 513 | +479 | +1314 | +1179 | +674 | -107 | +356 / +165 | -2808 / +0 | -10560 / +0 | 0.00 | -13.4 | within null |
| gSPY <=0 | P7 | all | 0.5 | 617 | +4694 | -1978 | -2801 | -2522 | -2146 | +1051 / +856 | +10816 / +15526 | +8164 / +17651 | 0.00 | +52.2 | ABOVE null |
| gSPY <=0 | P7 | all | 1.5 | 617 | -4694 | +1978 | +2801 | +2522 | +2146 | -1051 / -856 | -10816 / -15526 | -8164 / -19831 | 0.00 | -54.3 | within null |
| gSPY >0 | P7 | all | 0.5 | 382 | -2797 | -2179 | -3223 | -2436 | +16 | -838 / -799 | +1608 / +0 | -151 / +0 | 0.00 | +1.5 | within null |
| gSPY >0 | P7 | all | 1.5 | 382 | +2797 | +2179 | +3223 | +2436 | -16 | +838 / +799 | -1608 / +0 | +151 / +0 | 0.00 | -1.5 | within null |
| gSPY <=0 | U7 | all | 0.5 | 156 | -1192 | -1348 | -1581 | -1058 | -438 | -438 / -350 | +3154 / +744 | +2623 / +142 | 0.00 | +6.7 | within null |
| gSPY <=0 | U7 | all | 1.5 | 156 | +1192 | +1348 | +1581 | +1058 | +438 | +438 / +350 | -3154 / -744 | -2623 / -142 | 0.00 | -6.7 | within null |
| gSPY >0 | U7 | all | 0.5 | 108 | -759 | -673 | -92 | -32 | -159 | +699 / +396 | +3222 / +0 | +6489 / +0 | 0.00 | +9.7 | within null |
| gSPY >0 | U7 | all | 1.5 | 108 | +759 | +673 | +92 | +32 | +159 | -699 / -396 | -5728 / +0 | -6489 / +0 | 0.00 | -12.2 | within null |
| gvote <=0 | K7 | all | 0.5 | 941 | -2782 | -650 | -1117 | -751 | -615 | +391 / +357 | -4557 / +4738 | +5971 / +7307 | 0.00 | +13.5 | within null |
| gvote <=0 | K7 | all | 1.5 | 941 | +2782 | +650 | +1117 | +751 | +615 | -391 / -357 | +2898 / -4738 | -5971 / -7307 | 0.00 | -15.1 | within null |
| gvote >0 | K7 | all | 0.5 | 612 | +139 | -1124 | -1372 | -999 | -168 | -391 / -357 | +2808 / +0 | +12958 / +0 | 0.00 | +15.8 | within null |
| gvote >0 | K7 | all | 1.5 | 612 | -139 | +1124 | +1372 | +999 | +168 | +391 / +357 | -2808 / +0 | -12958 / +0 | 0.00 | -15.8 | within null |
| gvote <=0 | P7 | all | 0.5 | 593 | +4740 | -219 | -1750 | -2048 | -820 | +1953 / +1154 | +10816 / +15027 | +4659 / +14464 | 0.00 | +45.0 | within null |
| gvote <=0 | P7 | all | 1.5 | 593 | -4740 | +219 | +1750 | +2048 | +820 | -1953 / -1154 | -10816 / -15526 | -4659 / -19831 | 0.00 | -50.8 | within null |
| gvote >0 | P7 | all | 0.5 | 444 | -2843 | -4279 | -4725 | -3165 | -881 | -1953 / -1154 | +1608 / +0 | +959 / +0 | 0.00 | +2.6 | within null |
| gvote >0 | P7 | all | 1.5 | 444 | +2843 | +4279 | +4725 | +3165 | +881 | +1953 / +1154 | -1608 / +0 | -959 / +0 | 0.00 | -2.6 | within null |
| gvote <=0 | U7 | all | 0.5 | 155 | -1065 | -1340 | -1447 | -801 | -613 | -312 / -113 | +3154 / +744 | +3810 / +142 | 0.00 | +7.9 | within null |
| gvote <=0 | U7 | all | 1.5 | 155 | +1065 | +1340 | +1447 | +801 | +613 | +312 / +113 | -3154 / -744 | -3810 / -142 | 0.00 | -7.9 | within null |
| gvote >0 | U7 | all | 0.5 | 116 | -887 | -1045 | -538 | -384 | -261 | +312 / +113 | +3222 / +0 | +7635 / +0 | 0.00 | +10.9 | within null |
| gvote >0 | U7 | all | 1.5 | 116 | +887 | +1045 | +538 | +384 | +261 | -312 / -113 | -5728 / +0 | -7635 / +0 | 0.00 | -13.4 | within null |

Best gated cell overall, every action, top 12 by drawdown score:
| regime state | book | scope | action | n L6M | L1M $/wk | L3M | L6M | HOLD | PREUW | excess over whole-book action L6M / HOLD | worst week chg HOLD / L6M | max DD cut HOLD / L6M | full stops/wk removed | dd score $k | vs family null |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ivSPX >0 | P7 | asia | 0.0 | 171 | +950 | +436 | +250 | +293 | -1440 | +3792 / +4196 | +17009 / +10345 | +6732 / +11124 | 0.04 | +45.2 | within null |
| gSPX <q33 | ALL | london | H | 190 | -321 | +2145 | +281 | +1349 | +646 | +735 / +1132 | +10982 / +7860 | +5983 / +8855 | 0.00 | +33.7 | within null |
| ivSPX >0 | P7 | asia | 0.5 | 171 | +475 | +218 | +125 | +147 | -720 | +1896 / +2098 | +8505 / +9757 | +3366 / +11025 | 0.00 | +32.7 | within null |
| abvflipQQQ >q50 | U7 | london | 0.0 | 59 | +1041 | +447 | +143 | +240 | -309 | +902 / +697 | +2327 / +7197 | +15113 / +7197 | 0.99 | +31.8 | within null |
| nearflipQQQ >q66 | ALL | london | H | 218 | -901 | +1314 | +12 | +1680 | +2175 | +533 / +1446 | +347 / +7860 | +15739 / +5010 | 0.00 | +29.0 | within null |
| nearflipSPX <q66 | M7 | all | 0.0 | 486 | +718 | +143 | +448 | +380 | -1106 | +477 / +349 | +8465 / +1919 | +16868 / +1488 | 0.76 | +28.7 | within null |
| tide <q66 | M7 | london | H | 186 | -1741 | +75 | +252 | +1150 | +685 | +159 / +684 | +13479 / +2969 | +5262 / +6135 | 0.00 | +27.8 | within null |
| tide >q66 | ALL | london | 0.0 | 448 | +4011 | +2393 | +1898 | +528 | -2039 | +2551 / +1343 | +0 / +10710 | +3756 / +12318 | 1.26 | +26.8 | within null |
| nearflipSPX <q66 | M7 | london | 0.0 | 324 | +1371 | +791 | +772 | +817 | -425 | +554 / +618 | +8465 / +1309 | +15890 / +878 | 0.53 | +26.5 | within null |
| tide >0 | K7 | london | 0.0 | 195 | +2318 | +951 | +769 | +401 | -649 | +966 / +700 | +2477 / +4992 | +14016 / +4992 | 0.11 | +26.5 | within null |
| tide >q50 | K7 | london | 0.0 | 215 | +1986 | +797 | +741 | +328 | -515 | +957 / +655 | +2477 / +4992 | +13268 / +4992 | 0.11 | +25.7 | within null |
| tide >q33 | K7 | london | 0.0 | 288 | +33 | +10 | +423 | +172 | -266 | +713 / +589 | +2477 / +4992 | +13096 / +4992 | 0.15 | +25.6 | within null |

Widths by forecast range, day-done / stack caps by forecast range and the last-90-minute fade need re-simulation (exact engine) or a new book: the last-90 fade has NO footing (section 4: no pinning above a mirror-strike placebo); widths and caps: see section 8 when exact sets finish.

## 8. Exact-engine sets (tag UR, JN05W2 base, all layers ON, TP engine, measured fills)
Reading: cut % > 0 = max drawdown smaller than JN05W2 in the window; d mean = cell minus JN05W2 in $/wk (all weeks; "carry weeks dropped" in the raw block); wins turned losing = how many of the 20 best weeks became losing. Identity gates first (empty rules reproduce JN05W2 exactly, also the width / day-cap code path).

| set (dial) | L3M cut % | L3M d mean | L6M cut % | L6M d mean | HOLD cut % | HOLD d mean | placebo sets L6M cut % / d mean (tags shifted 11, 23, 37 days) |
|---|---|---|---|---|---|---|---|
| TL3_UR_P7ASIA_IVHI_SK | -26.3 | +269 | -26.3 | -464 | +27.3 | +238 | n/a |
| TL3_UR_LDN_GLO_HOLD | +17.3 | +591 | +17.3 | -297 | -34.5 | +238 | +0.0 / -2581; -1.3 / -2223; -1.5 / -1046 |
| TL3_UR_GAMMA_BOOKS | -11.5 | +2028 | -11.5 | +223 | -64.9 | +247 | -4.7 / +2347; -5.8 / +1020; +10.8 / +1720 |
| TL3_UR_K7LDN_TIDEPOS_SK | +4.8 | +339 | +4.8 | -384 | -10.0 | -102 | n/a |
| TL3_UR_NEARFLIPQ_HOLD | +19.6 | +928 | +19.6 | -1106 | -11.9 | +1090 | -10.3 / -859; +0.0 / -1875; -14.6 / -2744 |
| TL3_UR_M7LDN_TIDELO_HOLD | -3.7 | +512 | -3.7 | +179 | +20.0 | +862 | n/a |
| TL3_UR_ALL_LDN_TIDEHI_SK | +23.5 | +2174 | +9.0 | +829 | -58.4 | -524 | -17.9 / -599; +0.0 / -1488; -34.0 / -1019 |
| TL3_UR_WID_RNG | -21.8 | -1239 | -21.8 | +750 | -33.7 | +2761 | n/a |
| TL3_UR_CAPS_RNG | -12.6 | -2178 | -12.6 | -39 | +35.2 | +896 | n/a |

Compact (from score_nf.py; cut % > 0 = maxDD smaller than JN05W2; d mean = cell minus JN05W2 in $/wk):

| set | window | maxDD cut % | d mean $/wk (all weeks) | d mean (carry weeks dropped) | maxDD | maxDD ref | wins turned losing | months |
|---|---|---|---|---|---|---|---|---|
| TL3_UR_P7ASIA_IVHI_SK | L1M | -26.3 | -947.6 | 10323.3 | 45945.7 | 36370.5 | 1 |  |
| TL3_UR_P7ASIA_IVHI_SK | L3M | -26.3 | 269.1 | 3188.2 | 45945.7 | 36370.5 | 1 |  |
| TL3_UR_P7ASIA_IVHI_SK | L6M | -26.3 | -464.4 | 907.4 | 45945.7 | 36370.5 | 1 |  |
| TL3_UR_P7ASIA_IVHI_SK | HOLD | 27.3 | 237.7 | -538.7 | 45945.7 | 63185.1 | 1 |  |
| TL3_UR_LDN_GLO_HOLD | L1M | 19.6 | 412.8 | -1829.2 | 29231.7 | 36370.5 | 0 |  |
| TL3_UR_LDN_GLO_HOLD | L3M | 17.3 | 590.6 | -146.9 | 30071.9 | 36370.5 | 0 |  |
| TL3_UR_LDN_GLO_HOLD | L6M | 17.3 | -297.4 | 210.9 | 30071.9 | 36370.5 | 0 |  |
| TL3_UR_LDN_GLO_HOLD | HOLD | -34.5 | 237.5 | -220.3 | 84982.8 | 63185.1 | 0 |  |
| TL3_UR_GAMMA_BOOKS | L1M | -11.5 | 3984.4 | 1699.2 | 40546.0 | 36370.5 | 1 |  |
| TL3_UR_GAMMA_BOOKS | L3M | -11.5 | 2028.3 | 1277.0 | 40546.0 | 36370.5 | 1 |  |
| TL3_UR_GAMMA_BOOKS | L6M | -11.5 | 222.8 | 1514.5 | 40546.0 | 36370.5 | 1 |  |
| TL3_UR_GAMMA_BOOKS | HOLD | -64.9 | 247.0 | 880.6 | 104217.4 | 63185.1 | 1 |  |
| TL3_UR_K7LDN_TIDEPOS_SK | L1M | 4.8 | 625.7 | -158.4 | 34634.8 | 36370.5 | 1 |  |
| TL3_UR_K7LDN_TIDEPOS_SK | L3M | 4.8 | 338.9 | 108.8 | 34634.8 | 36370.5 | 1 |  |
| TL3_UR_K7LDN_TIDEPOS_SK | L6M | 4.8 | -383.9 | -117.9 | 34634.8 | 36370.5 | 1 |  |
| TL3_UR_K7LDN_TIDEPOS_SK | HOLD | -10.0 | -101.8 | -280.5 | 69485.8 | 63185.1 | 1 |  |
| TL3_UR_NEARFLIPQ_HOLD | L1M | 19.6 | 873.1 | -1215.5 | 29231.7 | 36370.5 | 0 |  |
| TL3_UR_NEARFLIPQ_HOLD | L3M | 19.6 | 928.1 | 283.3 | 29231.7 | 36370.5 | 0 |  |
| TL3_UR_NEARFLIPQ_HOLD | L6M | 19.6 | -1105.8 | -255.6 | 29231.7 | 36370.5 | 0 |  |
| TL3_UR_NEARFLIPQ_HOLD | HOLD | -11.9 | 1090.3 | 582.6 | 70703.9 | 63185.1 | 0 |  |
| TL3_UR_M7LDN_TIDELO_HOLD | L1M | 8.2 | 1112.6 | 493.0 | 33399.2 | 36370.5 | 0 |  |
| TL3_UR_M7LDN_TIDELO_HOLD | L3M | -3.7 | 511.6 | -297.0 | 37702.8 | 36370.5 | 0 |  |
| TL3_UR_M7LDN_TIDELO_HOLD | L6M | -3.7 | 178.6 | 600.8 | 37702.8 | 36370.5 | 0 |  |
| TL3_UR_M7LDN_TIDELO_HOLD | HOLD | 20.0 | 861.5 | 629.8 | 50543.4 | 63185.1 | 0 |  |
| TL3_UR_ALL_LDN_TIDEHI_SK | L1M | 23.5 | 2578.1 | 591.9 | 27833.9 | 36370.5 | 1 |  |
| TL3_UR_ALL_LDN_TIDEHI_SK | L3M | 23.5 | 2173.9 | 1217.7 | 27833.9 | 36370.5 | 1 |  |
| TL3_UR_ALL_LDN_TIDEHI_SK | L6M | 9.0 | 828.8 | 204.0 | 33114.1 | 36370.5 | 1 |  |
| TL3_UR_ALL_LDN_TIDEHI_SK | HOLD | -58.4 | -524.2 | 5.3 | 100113.8 | 63185.1 | 1 |  |
| TL3_UR_PL11_LDN_GLO_HOLD | L1M | 0.0 | -647.5 | 0.0 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL11_LDN_GLO_HOLD | L3M | 0.0 | -467.1 | -1090.2 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL11_LDN_GLO_HOLD | L6M | 0.0 | -2580.7 | -1620.3 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL11_GAMMA_BOOKS | L1M | 14.6 | 3412.8 | 2116.0 | 31044.0 | 36370.5 | 0 |  |
| TL3_UR_PL11_GAMMA_BOOKS | L3M | 14.6 | 4372.7 | 2128.8 | 31044.0 | 36370.5 | 0 |  |
| TL3_UR_PL11_GAMMA_BOOKS | L6M | -4.7 | 2346.7 | 1188.5 | 38079.8 | 36370.5 | 0 |  |
| TL3_UR_PL23_LDN_GLO_HOLD | L1M | 0.0 | -2566.1 | -1252.9 | 36370.5 | 36370.5 | 0 |  |
| TL3_UR_PL23_LDN_GLO_HOLD | L3M | -1.3 | -1742.8 | -1098.9 | 36856.0 | 36370.5 | 0 |  |
| TL3_UR_PL23_LDN_GLO_HOLD | L6M | -1.3 | -2223.2 | -1377.7 | 36856.0 | 36370.5 | 0 |  |
| TL3_UR_PL23_GAMMA_BOOKS | L1M | 14.6 | 8223.3 | 4618.9 | 31044.0 | 36370.5 | 1 |  |
| TL3_UR_PL23_GAMMA_BOOKS | L3M | -5.8 | 4893.4 | 3511.5 | 38489.0 | 36370.5 | 1 |  |
| TL3_UR_PL23_GAMMA_BOOKS | L6M | -5.8 | 1020.4 | 2267.2 | 38489.0 | 36370.5 | 1 |  |
| TL3_UR_PL37_LDN_GLO_HOLD | L1M | 0.0 | -716.8 | 624.7 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL37_LDN_GLO_HOLD | L3M | 0.0 | -39.2 | -627.6 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL37_LDN_GLO_HOLD | L6M | -1.5 | -1046.3 | -624.4 | 36907.2 | 36370.5 | 1 |  |
| TL3_UR_PL37_GAMMA_BOOKS | L1M | 28.5 | 9256.1 | 3657.9 | 26009.8 | 36370.5 | 1 |  |
| TL3_UR_PL37_GAMMA_BOOKS | L3M | 28.5 | 4286.8 | 2473.1 | 26009.8 | 36370.5 | 1 |  |
| TL3_UR_PL37_GAMMA_BOOKS | L6M | 10.8 | 1719.6 | 3521.7 | 32444.2 | 36370.5 | 1 |  |
| TL3_UR_PL11_ALL_LDN_TIDEHI_SK | L1M | 0.0 | 1753.8 | 0.0 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL11_ALL_LDN_TIDEHI_SK | L3M | -17.9 | -2577.7 | -1135.9 | 42895.2 | 36370.5 | 1 |  |
| TL3_UR_PL11_ALL_LDN_TIDEHI_SK | L6M | -17.9 | -599.0 | 172.2 | 42895.2 | 36370.5 | 1 |  |
| TL3_UR_PL11_NEARFLIPQ_HOLD | L1M | -3.8 | 430.5 | -459.3 | 37748.5 | 36370.5 | 0 |  |
| TL3_UR_PL11_NEARFLIPQ_HOLD | L3M | -10.3 | -1248.7 | -179.1 | 40108.9 | 36370.5 | 0 |  |
| TL3_UR_PL11_NEARFLIPQ_HOLD | L6M | -10.3 | -859.0 | -330.0 | 40108.9 | 36370.5 | 0 |  |
| TL3_UR_PL23_ALL_LDN_TIDEHI_SK | L1M | 0.0 | -1134.7 | 0.0 | 36370.5 | 36370.5 | 2 |  |
| TL3_UR_PL23_ALL_LDN_TIDEHI_SK | L3M | 0.0 | -1539.9 | 128.2 | 36370.5 | 36370.5 | 2 |  |
| TL3_UR_PL23_ALL_LDN_TIDEHI_SK | L6M | 0.0 | -1488.4 | -420.6 | 36370.5 | 36370.5 | 2 |  |
| TL3_UR_PL23_NEARFLIPQ_HOLD | L1M | 0.0 | -1246.1 | 0.0 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL23_NEARFLIPQ_HOLD | L3M | 0.0 | 155.8 | -545.5 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL23_NEARFLIPQ_HOLD | L6M | 0.0 | -1874.9 | -867.0 | 36370.5 | 36370.5 | 1 |  |
| TL3_UR_PL37_ALL_LDN_TIDEHI_SK | L1M | -14.8 | -1012.9 | 442.9 | 41750.9 | 36370.5 | 0 |  |
| TL3_UR_PL37_ALL_LDN_TIDEHI_SK | L3M | -34.0 | -2790.4 | -2251.7 | 48738.2 | 36370.5 | 0 |  |
| TL3_UR_PL37_ALL_LDN_TIDEHI_SK | L6M | -34.0 | -1018.7 | -263.2 | 48738.2 | 36370.5 | 0 |  |
| TL3_UR_PL37_NEARFLIPQ_HOLD | L1M | -14.6 | -2245.6 | -1228.2 | 41668.3 | 36370.5 | 1 |  |
| TL3_UR_PL37_NEARFLIPQ_HOLD | L3M | -14.6 | -1170.1 | -1899.0 | 41668.3 | 36370.5 | 1 |  |
| TL3_UR_PL37_NEARFLIPQ_HOLD | L6M | -14.6 | -2744.0 | -1818.1 | 41668.3 | 36370.5 | 1 |  |
| TL3_UR_WID_RNG | L1M | -21.8 | -4402.1 | -3009.2 | 44285.9 | 36370.5 | 1 |  |
| TL3_UR_WID_RNG | L3M | -21.8 | -1238.9 | 778.8 | 44285.9 | 36370.5 | 1 |  |
| TL3_UR_WID_RNG | L6M | -21.8 | 749.9 | -480.6 | 44285.9 | 36370.5 | 1 |  |
| TL3_UR_WID_RNG | HOLD | -33.7 | 2760.6 | 3452.6 | 84453.6 | 63185.1 | 1 |  |
| TL3_UR_CAPS_RNG | L1M | -12.6 | -3294.7 | -2401.9 | 40939.3 | 36370.5 | 0 |  |
| TL3_UR_CAPS_RNG | L3M | -12.6 | -2178.2 | -1852.6 | 40939.3 | 36370.5 | 0 |  |
| TL3_UR_CAPS_RNG | L6M | -12.6 | -39.3 | -848.6 | 40939.3 | 36370.5 | 0 |  |
| TL3_UR_CAPS_RNG | HOLD | 35.2 | 896.5 | 167.1 | 40939.3 | 63185.1 | 0 |  |

Raw:
Identity gates: TL3_UR_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_UR_WID_ID 202610 (width/daycap code path, w=1): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

### TL3_UR_P7ASIA_IVHI_SK: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_P7ASIA_IVHI_SK vs JN05W2
                    cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_P7ASIA_IVHI_SK    L1M -26.3     10323.3     -947.6  45945.7  36370.5    -341.3      9.0      6.0         13.0          6.0         56             50      12   316288.0    290349.8                1         20
1  TL3_UR_P7ASIA_IVHI_SK    L3M -26.3      3188.2      269.1  45945.7  36370.5   16284.3     10.0      5.0         13.0          6.0        167            161      12   316288.0    290349.8                1         20
2  TL3_UR_P7ASIA_IVHI_SK    L6M -26.3       907.4     -464.4  45945.7  36370.5   24672.5     10.0      6.0         13.0          6.0        356            350      12   316288.0    290349.8                1         20
3  TL3_UR_P7ASIA_IVHI_SK   HOLD  27.3      -538.7      237.7  45945.7  63185.1   17727.1     10.0      6.0         13.0          6.0        621            631      12   316288.0    290349.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 290349.7800000089, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_LDN_GLO_HOLD: months done 21 (202410,202411,202412,202501,202502,202503,202504,202505,202506,202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_LDN_GLO_HOLD vs JN05W2
                  cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_LDN_GLO_HOLD    L1M  19.6     -1829.2      412.8  29231.7  36370.5    1019.1     13.0      6.0         13.0          6.0         49             50      21   316288.0    291943.7                0         20
1  TL3_UR_LDN_GLO_HOLD    L3M  17.3      -146.9      590.6  30071.9  36370.5   16605.8     13.0      6.0         13.0          6.0        159            161      21   316288.0    291943.7                0         20
2  TL3_UR_LDN_GLO_HOLD    L6M  17.3       210.9     -297.4  30071.9  36370.5   24839.5     13.0      6.0         13.0          6.0        343            350      21   316288.0    291943.7                0         20
3  TL3_UR_LDN_GLO_HOLD   HOLD -34.5      -220.3      237.5  84982.8  63185.1   17726.8     13.0      6.0         13.0          6.0        614            631      21   316288.0    291943.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 291943.66000000865, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_GAMMA_BOOKS: months done 21 (202410,202411,202412,202501,202502,202503,202504,202505,202506,202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_GAMMA_BOOKS vs JN05W2
                 cell window   cut  dmean_drop  dmean_all        dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_GAMMA_BOOKS    L1M -11.5      1699.2     3984.4   40546.0  36370.5    4590.7     12.0      6.0         13.0          6.0         45             50      21   316288.0    299137.7                1         20
1  TL3_UR_GAMMA_BOOKS    L3M -11.5      1277.0     2028.3   40546.0  36370.5   18043.5     12.0      5.0         13.0          6.0        142            161      21   316288.0    299137.7                1         20
2  TL3_UR_GAMMA_BOOKS    L6M -11.5      1514.5      222.8   40546.0  36370.5   25359.7     12.0      6.0         13.0          6.0        307            350      21   316288.0    299137.7                1         20
3  TL3_UR_GAMMA_BOOKS   HOLD -64.9       880.6      247.0  104217.4  63185.1   17736.3     12.0      5.0         13.0          6.0        558            631      21   316288.0    299137.7                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 299137.660000009, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_K7LDN_TIDEPOS_SK: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_K7LDN_TIDEPOS_SK vs JN05W2
                      cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_K7LDN_TIDEPOS_SK    L1M   4.8      -158.4      625.7  34634.8  36370.5    1232.0     13.0      6.0         13.0          6.0         46             50      12   316288.0    313185.4                1         20
1  TL3_UR_K7LDN_TIDEPOS_SK    L3M   4.8       108.8      338.9  34634.8  36370.5   16354.1     13.0      5.7         13.0          6.0        149            161      12   316288.0    313185.4                1         20
2  TL3_UR_K7LDN_TIDEPOS_SK    L6M   4.8      -117.9     -383.9  34634.8  36370.5   24753.0     13.0      6.0         13.0          6.0        328            350      12   316288.0    313185.4                1         20
3  TL3_UR_K7LDN_TIDEPOS_SK   HOLD -10.0      -280.5     -101.8  69485.8  63185.1   17387.5     13.0      5.4         13.0          6.0        592            631      12   316288.0    313185.4                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 313185.42000000924, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_NEARFLIPQ_HOLD: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_NEARFLIPQ_HOLD vs JN05W2
                    cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_NEARFLIPQ_HOLD    L1M  19.6     -1215.5      873.1  29231.7  36370.5    1479.4     13.0      6.0         13.0          6.0         48             50      12   316288.0    297169.6                0         20
1  TL3_UR_NEARFLIPQ_HOLD    L3M  19.6       283.3      928.1  29231.7  36370.5   16943.3     13.0      5.1         13.0          6.0        152            161      12   316288.0    297169.6                0         20
2  TL3_UR_NEARFLIPQ_HOLD    L6M  19.6      -255.6    -1105.8  29231.7  36370.5   24031.1     13.0      6.0         13.0          6.0        337            350      12   316288.0    297169.6                0         20
3  TL3_UR_NEARFLIPQ_HOLD   HOLD -11.9       582.6     1090.3  70703.9  63185.1   18579.6     13.0      6.0         13.0          6.0        602            631      12   316288.0    297169.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 297169.60000000877, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_M7LDN_TIDELO_HOLD: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_M7LDN_TIDELO_HOLD vs JN05W2
                       cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_M7LDN_TIDELO_HOLD    L1M   8.2       493.0     1112.6  33399.2  36370.5    1718.9     13.0      6.0         13.0          6.0         48             50      12   316288.0    328090.2                0         20
1  TL3_UR_M7LDN_TIDELO_HOLD    L3M  -3.7      -297.0      511.6  37702.8  36370.5   16526.8     13.0      5.1         13.0          6.0        155            161      12   316288.0    328090.2                0         20
2  TL3_UR_M7LDN_TIDELO_HOLD    L6M  -3.7       600.8      178.6  37702.8  36370.5   25315.5     13.0      6.0         13.0          6.0        337            350      12   316288.0    328090.2                0         20
3  TL3_UR_M7LDN_TIDELO_HOLD   HOLD  20.0       629.8      861.5  50543.4  63185.1   18350.8     13.0      6.0         13.0          6.0        608            631      12   316288.0    328090.2                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 328090.1600000091, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_ALL_LDN_TIDEHI_SK: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_ALL_LDN_TIDEHI_SK vs JN05W2
                       cell window   cut  dmean_drop  dmean_all        dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_ALL_LDN_TIDEHI_SK    L1M  23.5       591.9     2578.1   27833.9  36370.5    3184.4     13.0      6.0         13.0          6.0         48             50      12   316288.0    306671.9                1         20
1  TL3_UR_ALL_LDN_TIDEHI_SK    L3M  23.5      1217.7     2173.9   27833.9  36370.5   18189.1     13.0      6.0         13.0          6.0        152            161      12   316288.0    306671.9                1         20
2  TL3_UR_ALL_LDN_TIDEHI_SK    L6M   9.0       204.0      828.8   33114.1  36370.5   25965.7     13.0      6.0         13.0          6.0        311            350      12   316288.0    306671.9                1         20
3  TL3_UR_ALL_LDN_TIDEHI_SK   HOLD -58.4         5.3     -524.2  100113.8  63185.1   16965.2     13.0      6.0         13.0          6.0        555            631      12   316288.0    306671.9                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 306671.9200000083, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL11_LDN_GLO_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL11_LDN_GLO_HOLD vs JN05W2
                       cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL11_LDN_GLO_HOLD    L1M  0.0         0.0     -647.5  36370.5  36370.5     -41.2     13.0      6.0         13.0          6.0         51             50       6   316288.0    274675.8                1         20
1  TL3_UR_PL11_LDN_GLO_HOLD    L3M  0.0     -1090.2     -467.1  36370.5  36370.5   15548.1     13.0      6.0         13.0          6.0        160            161       6   316288.0    274675.8                1         20
2  TL3_UR_PL11_LDN_GLO_HOLD    L6M  0.0     -1620.3    -2580.7  36370.5  36370.5   22556.2     13.0      6.0         13.0          6.0        347            350       6   316288.0    274675.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 274675.82000000833, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL11_GAMMA_BOOKS: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL11_GAMMA_BOOKS vs JN05W2
                      cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL11_GAMMA_BOOKS    L1M  14.6      2116.0     3412.8  31044.0  36370.5    4019.1     13.0      5.9         13.0          6.0         46             50       6   316288.0    331025.0                0         20
1  TL3_UR_PL11_GAMMA_BOOKS    L3M  14.6      2128.8     4372.7  31044.0  36370.5   20387.9     13.0      5.0         13.0          6.0        150            161       6   316288.0    331025.0                0         20
2  TL3_UR_PL11_GAMMA_BOOKS    L6M  -4.7      1188.5     2346.7  38079.8  36370.5   27483.5     13.0      6.0         13.0          6.0        312            350       6   316288.0    331025.0                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 331025.0000000107, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_PL23_LDN_GLO_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL23_LDN_GLO_HOLD vs JN05W2
                       cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL23_LDN_GLO_HOLD    L1M  0.0     -1252.9    -2566.1  36370.5  36370.5   -1959.8     13.0      6.0         13.0          6.0         49             50       6   316288.0    293418.9                0         20
1  TL3_UR_PL23_LDN_GLO_HOLD    L3M -1.3     -1098.9    -1742.8  36856.0  36370.5   14272.4     13.0      5.2         13.0          6.0        159            161       6   316288.0    293418.9                0         20
2  TL3_UR_PL23_LDN_GLO_HOLD    L6M -1.3     -1377.7    -2223.2  36856.0  36370.5   22913.7     13.0      6.0         13.0          6.0        347            350       6   316288.0    293418.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 293418.88000000914, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_PL23_GAMMA_BOOKS: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL23_GAMMA_BOOKS vs JN05W2
                      cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL23_GAMMA_BOOKS    L1M  14.6      4618.9     8223.3  31044.0  36370.5    8829.6     13.0      5.7         13.0          6.0         47             50       6   316288.0    304148.1                1         20
1  TL3_UR_PL23_GAMMA_BOOKS    L3M  -5.8      3511.5     4893.4  38489.0  36370.5   20908.6     13.0      5.0         13.0          6.0        149            161       6   316288.0    304148.1                1         20
2  TL3_UR_PL23_GAMMA_BOOKS    L6M  -5.8      2267.2     1020.4  38489.0  36370.5   26157.3     13.0      6.0         13.0          6.0        312            350       6   316288.0    304148.1                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 304148.1200000108, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL37_LDN_GLO_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL37_LDN_GLO_HOLD vs JN05W2
                       cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL37_LDN_GLO_HOLD    L1M  0.0       624.7     -716.8  36370.5  36370.5    -110.5     13.0      6.0         13.0          6.0         49             50       6   316288.0    311748.8                1         20
1  TL3_UR_PL37_LDN_GLO_HOLD    L3M  0.0      -627.6      -39.2  36370.5  36370.5   15976.0     13.0      6.0         13.0          6.0        155            161       6   316288.0    311748.8                1         20
2  TL3_UR_PL37_LDN_GLO_HOLD    L6M -1.5      -624.4    -1046.3  36907.2  36370.5   24090.6     13.0      6.0         13.0          6.0        339            350       6   316288.0    311748.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 311748.84000000847, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL37_GAMMA_BOOKS: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL37_GAMMA_BOOKS vs JN05W2
                      cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL37_GAMMA_BOOKS    L1M  28.5      3657.9     9256.1  26009.8  36370.5    9862.4     12.0      5.8         13.0          6.0         45             50       6   316288.0    300401.8                1         20
1  TL3_UR_PL37_GAMMA_BOOKS    L3M  28.5      2473.1     4286.8  26009.8  36370.5   20301.9     12.0      5.0         13.0          6.0        144            161       6   316288.0    300401.8                1         20
2  TL3_UR_PL37_GAMMA_BOOKS    L6M  10.8      3521.7     1719.6  32444.2  36370.5   26856.5     12.0      6.0         13.0          6.0        308            350       6   316288.0    300401.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 300401.7800000111, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL11_ALL_LDN_TIDEHI_SK: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL11_ALL_LDN_TIDEHI_SK vs JN05W2
                            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL11_ALL_LDN_TIDEHI_SK    L1M   0.0         0.0     1753.8  36370.5  36370.5    2360.1     13.0      6.0         13.0          6.0         51             50       6   316288.0    323953.8                1         20
1  TL3_UR_PL11_ALL_LDN_TIDEHI_SK    L3M -17.9     -1135.9    -2577.7  42895.2  36370.5   13437.5     13.0      6.0         13.0          6.0        151            161       6   316288.0    323953.8                1         20
2  TL3_UR_PL11_ALL_LDN_TIDEHI_SK    L6M -17.9       172.2     -599.0  42895.2  36370.5   24537.9     13.0      6.0         13.0          6.0        315            350       6   316288.0    323953.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 323953.8000000091, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL11_NEARFLIPQ_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL11_NEARFLIPQ_HOLD vs JN05W2
                         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL11_NEARFLIPQ_HOLD    L1M  -3.8      -459.3      430.5  37748.5  36370.5    1036.8     13.0      6.0         13.0          6.0         50             50       6   316288.0    314066.6                0         20
1  TL3_UR_PL11_NEARFLIPQ_HOLD    L3M -10.3      -179.1    -1248.7  40108.9  36370.5   14766.5     13.0      6.0         13.0          6.0        158            161       6   316288.0    314066.6                0         20
2  TL3_UR_PL11_NEARFLIPQ_HOLD    L6M -10.3      -330.0     -859.0  40108.9  36370.5   24277.9     13.0      6.0         13.0          6.0        343            350       6   316288.0    314066.6                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 314066.6200000087, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_PL23_ALL_LDN_TIDEHI_SK: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL23_ALL_LDN_TIDEHI_SK vs JN05W2
                            cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL23_ALL_LDN_TIDEHI_SK    L1M  0.0         0.0    -1134.7  36370.5  36370.5    -528.4     13.0      6.0         13.0          6.0         49             50       6   316288.0    307529.9                2         20
1  TL3_UR_PL23_ALL_LDN_TIDEHI_SK    L3M  0.0       128.2    -1539.9  36370.5  36370.5   14475.3     13.0      5.8         13.0          6.0        149            161       6   316288.0    307529.9                2         20
2  TL3_UR_PL23_ALL_LDN_TIDEHI_SK    L6M  0.0      -420.6    -1488.4  36370.5  36370.5   23648.5     13.0      6.0         13.0          6.0        316            350       6   316288.0    307529.9                2         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307529.9400000088, 'win_turn_losing': 2, 'win_weeks': 20}
```

### TL3_UR_PL23_NEARFLIPQ_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL23_NEARFLIPQ_HOLD vs JN05W2
                         cell window  cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL23_NEARFLIPQ_HOLD    L1M  0.0         0.0    -1246.1  36370.5  36370.5    -639.8     13.0      6.0         13.0          6.0         50             50       6   316288.0    307145.7                1         20
1  TL3_UR_PL23_NEARFLIPQ_HOLD    L3M  0.0      -545.5      155.8  36370.5  36370.5   16171.0     13.0      6.0         13.0          6.0        156            161       6   316288.0    307145.7                1         20
2  TL3_UR_PL23_NEARFLIPQ_HOLD    L6M  0.0      -867.0    -1874.9  36370.5  36370.5   23262.0     13.0      6.0         13.0          6.0        340            350       6   316288.0    307145.7                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307145.72000000795, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_PL37_ALL_LDN_TIDEHI_SK: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL37_ALL_LDN_TIDEHI_SK vs JN05W2
                            cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL37_ALL_LDN_TIDEHI_SK    L1M -14.8       442.9    -1012.9  41750.9  36370.5    -406.6     13.0      6.0         13.0          6.0         49             50       6   316288.0    346910.9                0         20
1  TL3_UR_PL37_ALL_LDN_TIDEHI_SK    L3M -34.0     -2251.7    -2790.4  48738.2  36370.5   13224.8     13.0      5.2         13.0          6.0        145            161       6   316288.0    346910.9                0         20
2  TL3_UR_PL37_ALL_LDN_TIDEHI_SK    L6M -34.0      -263.2    -1018.7  48738.2  36370.5   24118.2     13.0      6.0         13.0          6.0        309            350       6   316288.0    346910.9                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 346910.88000000786, 'win_turn_losing': 0, 'win_weeks': 20}
```

### TL3_UR_PL37_NEARFLIPQ_HOLD: months done 6 (202605,202606,202607,202608,202609,202610)
```
TL3_UR_PL37_NEARFLIPQ_HOLD vs JN05W2
                         cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_PL37_NEARFLIPQ_HOLD    L1M -14.6     -1228.2    -2245.6  41668.3  36370.5   -1639.3     13.0      6.0         13.0          6.0         51             50       6   316288.0    311315.3                1         20
1  TL3_UR_PL37_NEARFLIPQ_HOLD    L3M -14.6     -1899.0    -1170.1  41668.3  36370.5   14845.1     13.0      5.2         13.0          6.0        158            161       6   316288.0    311315.3                1         20
2  TL3_UR_PL37_NEARFLIPQ_HOLD    L6M -14.6     -1818.1    -2744.0  41668.3  36370.5   22392.9     13.0      6.0         13.0          6.0        342            350       6   316288.0    311315.3                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 311315.3000000087, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_WID_RNG: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_WID_RNG vs JN05W2
             cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_WID_RNG    L1M -21.8     -3009.2    -4402.1  44285.9  36370.5   -3795.8     13.0      6.0         13.0          6.0         51             50      12   316288.0    315093.8                1         20
1  TL3_UR_WID_RNG    L3M -21.8       778.8    -1238.9  44285.9  36370.5   14776.3     13.0      6.0         13.0          6.0        155            161      12   316288.0    315093.8                1         20
2  TL3_UR_WID_RNG    L6M -21.8      -480.6      749.9  44285.9  36370.5   25886.8     13.0      6.0         13.0          6.0        347            350      12   316288.0    315093.8                1         20
3  TL3_UR_WID_RNG   HOLD -33.7      3452.6     2760.6  84453.6  63185.1   20249.9     13.0      6.0         13.0          6.0        635            631      12   316288.0    315093.8                1         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 315093.76000000915, 'win_turn_losing': 1, 'win_weeks': 20}
```

### TL3_UR_CAPS_RNG: months done 12 (202511,202512,202601,202602,202603,202604,202605,202606,202607,202608,202609,202610)
```
TL3_UR_CAPS_RNG vs JN05W2
              cell window   cut  dmean_drop  dmean_all       dd   dd_ref  mean_all  run_max  run_p95  run_max_ref  run_p95_ref  sess_run3  sess_run3_ref  months  best5_ref  best5_cell  win_turn_losing  win_weeks
0  TL3_UR_CAPS_RNG    L1M -12.6     -2401.9    -3294.7  40939.3  36370.5   -2688.4     15.0      6.0         13.0          6.0         50             50      12   316288.0    307928.7                0         20
1  TL3_UR_CAPS_RNG    L3M -12.6     -1852.6    -2178.2  40939.3  36370.5   13837.0     15.0      6.0         13.0          6.0        156            161      12   316288.0    307928.7                0         20
2  TL3_UR_CAPS_RNG    L6M -12.6      -848.6      -39.3  40939.3  36370.5   25097.6     15.0      6.0         13.0          6.0        343            350      12   316288.0    307928.7                0         20
3  TL3_UR_CAPS_RNG   HOLD  35.2       167.1      896.5  40939.3  63185.1   18385.8     15.0      6.0         13.0          6.0        612            631      12   316288.0    307928.7                0         20
trend {'best5_ref': 316287.98000000964, 'best5_cell': 307928.6600000098, 'win_turn_losing': 0, 'win_weeks': 20}
```

