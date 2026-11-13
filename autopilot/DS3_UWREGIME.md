# DS3_UWREGIME - Unusual Whales as a range / day-type forecaster (W-UR1). Rebuilt 2026-11-13T18:04:46Z by code/th_uwregime/ur_loop.sh (every 3 h). Research only, NO trading in this page, NO PASS claim.
Prereg: autopilot/UWREGIME_PREREG.md (sha in DECISIONS.md, logged before scoring). Question: does UW forecast, out of sample, the session range / realized vol, trend-vs-chop, pinning and time of high/low, and by how much OVER a no-UW benchmark.

## 0. Method in six lines
- Sample: 552 trading days 2024-10-02..2026-11-12 (UW history starts 2024-10-01; NQ 1-min prices; ES for SPX/SPY pin). Expanding-window ridge, min 120 days, refit every 10 trading days (= 2 weeks); out-of-sample R2 is vs the expanding mean.
- Benchmark (no UW; VIX is NOT on the box, ATR used): lag-1/5/20-day mean of the same target, lag-1 and ATR14 of the same-session range, ATR14 of the RTH range; for 08:30/09:30/10:00 readings also the range so far today, realized vol so far, |move since prior close| and that move in ATR units. UW model = benchmark + ONE input group (<= 6 features). Gain = R2(UW model) - R2(benchmark), in percentage points of variance explained (pp).
- Readings: R0 prior close (UW rows up to the prior close + prior-day EOD level files), R1 08:30, R2 09:30, R3 10:00 ET; a UW minute row is used only at start+180 s; EOD files (gex levels, spot-strike, vol stats, dp levels, IV term) only from the previous trading day; futures move since the prior close maps UW spot to the reading time. Targets: session ln range, ln realized vol (range class); efficiency ratio, close extremity, mean crossings (day-type class); time of first / last extreme (timing).
- Nulls: shifted-time null = UW inputs from k trading days earlier, k in 8..60, 20 draws, same refit; "null q95" per row, "fam q95" = q95 over draws of the MAX gain across all groups AND readings for that session-target (so picking the best group/reading is already charged). 90% CI = 5-day block bootstrap of the daily squared-error difference.
- Verdict: YES = gain > 0 and CI low > 0 and gain > family null q95; weak = gain > 0 and > per-row null q95 only (not corrected for picking among groups/readings); no = otherwise.
- NDX spot glitches: UW NDX spot is rounded and often frozen for hours; each minute row is checked against the NQ-implied price (0.4% tolerance, 0.6% for ES/RTY/YM) and dropped if off. Glitch days (>25% of rows dropped): {'DIA': 2, 'IWM': 5, 'NDX': 67, 'QQQ': 3, 'SPX': 3, 'SPY': 3}. Days with no UW file: {'DIA': 21, 'IWM': 21, 'NDX': 21, 'QQQ': 21, 'SPX': 21, 'SPY': 21}. Futures: continuous series with >1.2%/min roll jumps removed (15 on NQ).

## 1. Headline (7518 scored rows = reading x session x target x input group)
- vs ATR benchmark: YES rows 175, weak rows 948. vs the STRICT benchmark (ATR + IV level/rank + day-of-week; the VIX-alone stand-in): YES rows 76. Inputs with at least one YES (range class, vs ATR): ALL4:flip, ALL4:gamma, DIA:flip, DIA:iv_level, DIA:iv_minus_rv, DIA:iv_term, IWM:absflip_wall, IWM:flip, IWM:iv_level, IWM:iv_minus_rv, IWM:iv_term, IWM:walls, NDX:flip, NDX:iv_level, NDX:iv_minus_rv, NDX:iv_term, QQQ:absflip_wall, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:iv_level, QQQ:iv_minus_rv, QQQ:iv_term, QQQ:net_premium, QQQ:vanna, QQQ:walls, SPX:absflip_wall, SPX:charm, SPX:flip, SPX:gamma, SPX:iv_level, SPX:iv_minus_rv, SPX:walls, SPY:flip, SPY:gamma, SPY:iv_level, SPY:iv_minus_rv, SPY:iv_term, SPY:walls, cal:dow, tide.
- Of those, YES also vs the strict benchmark (range class): ALL4:flip, DIA:iv_term, IWM:absflip_wall, IWM:flip, IWM:iv_term, NDX:flip, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:iv_level, QQQ:vanna, QQQ:walls, SPX:charm, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:walls, tide.
- YES vs strict benchmark (day-type class): DIA:iv_term, IWM:iv_term; (timing class): cal:opex_day.
- Inputs with at least one YES (day-type class): DIA:gamma_chg, DIA:iv_term, IWM:iv_term.
- Inputs with at least one YES (timing class): IWM:iv_term, NDX:absflip_wall, NDX:flip, SPX:vanna, cal:dow, cal:opex_day.


### Plain answer by session (strict benchmark = ATR + IV level/rank + day of week; "weak" = beats its own shifted-time null only)
| session | forecasts RANGE (strict YES) | best gain pp (input, reading, target) | forecasts DAY TYPE (strict YES) | forecasts TIMING of high/low (strict YES) |
|---|---|---|---|---|
| asia | ALL4:flip, QQQ:iv_level, SPY:flip, tide | +3.2 (tide, R0, lnrv) | NO | NO |
| london | ALL4:flip, tide | +3.2 (tide, R0, lnrv) | NO | NO |
| pre | ALL4:flip, IWM:absflip_wall, IWM:iv_term | +8.0 (IWM:iv_term, R0, lnrng) | NO | cal:opex_day |
| nyam | DIA:iv_term, IWM:iv_term, QQQ:vanna, SPX:charm | +7.4 (SPX:charm, R1, lnrv) | NO | NO |
| nypm | ALL4:flip, IWM:flip, NDX:flip, QQQ:flip, QQQ:walls, SPX:flip, SPX:gamma, SPX:gamma_chg, SPX:walls, SPY:flip, SPY:walls, tide | +5.0 (QQQ:flip, R3, lnrv) | DIA:iv_term, IWM:iv_term | NO |
| nyam2 | IWM:iv_term, NDX:flip, SPX:charm, SPX:gamma | +3.5 (SPX:charm, R3, lnrv) | NO | NO |
| late | ALL4:flip, IWM:flip, IWM:iv_term, NDX:flip, QQQ:flip, QQQ:gamma, QQQ:impmove_vs_actual, QQQ:walls, SPX:flip, SPX:gamma, SPX:walls, SPY:flip, SPY:walls, tide | +6.6 (QQQ:flip, R3, lnrv) | NO | NO |
## 2. Per session: every input, range yes/no and day type yes/no, gain over the no-UW benchmark (pp of R2)
Columns: best reading R# for the range class (ln range / ln RV) and for the day-type class (ER / close extremity / crossings); gain full OOS / L6M / L3M in pp; CI = 90% bootstrap on the full-OOS gain; nq95 = per-row shifted null q95; fq95 = family null q95 (max over groups and readings). Bench R2 = benchmark R2 for that target (how much the no-UW model already explains). Sorted by range gain. Only the top 14 groups per session by best of (range, day-type) gain are listed; the full table is in /mnt/l2/l2vast/_uwregime/forecast_all.csv.

### asia
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SPY:flip | YES | R0 | lnrng | +8.18 | +14.56 | +15.83 | [+4.62,+12.53] | +0.03 | +2.75 | 24 | +1.93 YES | no | R0 | cext | -0.43 | +0.46 | -1.53 | [-1.64,+0.97] | -0.67 | +1.79 | -1 | -1.02 no | no |
| QQQ:iv_level | YES | R0 | lnrng | +8.04 | +14.58 | +21.81 | [+2.99,+12.86] | -0.52 | +2.75 | 24 | +2.45 YES | no | R0 | cross | -0.72 | -5.32 | -1.23 | [-3.10,+1.66] | -0.13 | +2.07 | -7 | -1.10 no | no |
| ALL4:flip | YES | R0 | lnrng | +7.67 | +11.78 | +12.43 | [+2.58,+11.51] | -0.35 | +2.75 | 24 | +2.42 YES | no | R0 | cross | -0.29 | +1.27 | +2.22 | [-3.35,+2.23] | -0.07 | +2.07 | -7 | -1.49 no | no |
| SPY:iv_level | YES | R0 | lnrng | +7.29 | +11.10 | +22.41 | [+2.40,+11.51] | -0.36 | +2.75 | 24 | +0.72 weak | weak | R0 | cross | +0.70 | -0.19 | +0.41 | [-1.30,+2.93] | -0.34 | +2.07 | -7 | +1.06 weak | no |
| DIA:iv_level | YES | R0 | lnrng | +7.08 | +6.46 | +17.24 | [+1.36,+10.91] | -0.68 | +2.75 | 24 | -0.04 no | no | R0 | er | -0.49 | -0.81 | -1.90 | [-1.51,+0.47] | -0.70 | +1.74 | -6 | -0.27 weak | weak |
| DIA:iv_term | YES | R0 | lnrng | +6.62 | -3.95 | +13.12 | [-0.49,+11.00] | -0.39 | +2.75 | 24 | +0.75 weak | weak | R0 | cross | +1.65 | +4.52 | +5.10 | [-2.35,+5.52] | -0.17 | +2.07 | -7 | +0.45 weak | weak |
| IWM:iv_term | YES | R0 | lnrng | +6.55 | -0.57 | +6.47 | [+2.15,+9.48] | +0.30 | +2.75 | 24 | +1.66 weak | weak | R0 | cross | +3.78 | +7.11 | +5.91 | [-0.12,+7.68] | +0.89 | +2.07 | -7 | +1.17 weak | weak |
| IWM:iv_level | YES | R0 | lnrng | +6.45 | +6.35 | +14.89 | [-0.67,+9.90] | -0.13 | +2.75 | 24 | -0.85 no | no | R0 | er | -0.98 | -2.18 | -3.75 | [-2.81,+0.58] | -0.33 | +1.74 | -6 | -0.62 no | weak |
| QQQ:iv_term | YES | R0 | lnrng | +6.39 | +14.40 | +20.13 | [+2.87,+10.49] | +0.24 | +2.75 | 24 | +1.68 weak | no | R0 | cext | -1.78 | -0.92 | -1.88 | [-3.77,+0.03] | -2.16 | +1.79 | -1 | -1.60 no | no |
| SPX:iv_level | YES | R0 | lnrng | +6.22 | +8.42 | +17.73 | [+2.26,+11.58] | -0.60 | +2.75 | 24 | -0.17 no | weak | R0 | cross | +0.23 | +0.24 | +1.02 | [-0.85,+1.36] | -0.22 | +2.07 | -7 | -0.06 no | no |
| tide | YES | R0 | lnrv | +6.02 | +7.95 | +10.04 | [+3.89,+8.46] | +0.40 | +2.01 | 56 | +3.17 YES | no | R0 | er | +0.22 | +0.09 | -1.45 | [-1.32,+1.66] | +0.42 | +1.74 | -6 | +0.15 no | no |
| SPX:gamma | YES | R0 | lnrv | +5.76 | +6.06 | +9.20 | [+3.12,+9.11] | -0.29 | +2.01 | 56 | +1.69 weak | no | R0 | er | -1.89 | -0.71 | -2.18 | [-3.67,+0.08] | -0.47 | +1.74 | -6 | -3.21 no | no |
| NDX:iv_level | YES | R0 | lnrv | +5.59 | +3.22 | +12.68 | [+2.53,+8.60] | -0.32 | +2.01 | 56 | +0.95 weak | no | R0 | er | -0.33 | -0.97 | -0.82 | [-1.68,+1.15] | +0.72 | +1.74 | -6 | -0.73 no | no |
| IWM:flip | YES | R0 | lnrng | +5.36 | +5.00 | +9.40 | [+2.77,+8.31] | +0.05 | +2.75 | 24 | -0.08 weak | no | R0 | er | -0.41 | -1.16 | -4.82 | [-1.76,+1.14] | -0.01 | +1.74 | -6 | -0.65 no | no |

### london
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL4:flip | YES | R0 | lnrv | +7.78 | +0.22 | -0.70 | [+4.13,+11.15] | -0.17 | +0.93 | 51 | +3.10 YES | weak | R0 | er | +1.43 | +4.17 | +5.05 | [-0.42,+3.23] | -0.87 | +1.08 | -4 | +1.23 weak | weak |
| DIA:iv_term | YES | R0 | lnrng | +7.34 | +8.46 | +8.03 | [+3.83,+11.00] | -0.10 | +1.61 | 19 | +2.68 weak | no | R0 | cross | -0.19 | -0.83 | -4.70 | [-2.22,+1.48] | +0.14 | +1.36 | -2 | +0.02 weak | no |
| IWM:flip | YES | R0 | lnrng | +6.70 | +6.95 | +3.75 | [+2.94,+11.42] | +0.01 | +1.61 | 19 | +1.98 weak | weak | R0 | er | +0.93 | +2.94 | +1.45 | [-0.78,+2.85] | -0.39 | +1.08 | -4 | -0.04 weak | weak |
| DIA:iv_level | YES | R0 | lnrng | +6.52 | +12.42 | +16.97 | [+2.00,+11.59] | -0.36 | +1.61 | 19 | -0.60 no | no | R0 | cross | -1.09 | -1.42 | -0.79 | [-2.48,+0.22] | -0.91 | +1.36 | -2 | -0.66 no | no |
| SPY:flip | YES | R0 | lnrng | +6.33 | +9.39 | +2.49 | [+2.24,+13.26] | -0.99 | +1.61 | 19 | +1.60 weak | weak | R0 | er | +0.73 | +4.81 | +4.24 | [-1.62,+2.69] | -0.60 | +1.08 | -4 | -0.91 no | no |
| SPX:iv_level | YES | R0 | lnrv | +5.77 | -4.29 | +1.53 | [+2.73,+8.72] | -0.39 | +0.93 | 51 | -0.09 no | no | R0 | cross | -0.58 | -1.30 | -0.12 | [-2.48,+0.97] | -0.44 | +1.36 | -2 | -0.17 no | no |
| SPY:iv_level | YES | R0 | lnrng | +5.68 | +15.82 | +18.70 | [+1.27,+13.34] | -0.49 | +1.61 | 19 | -0.02 no | no | R0 | er | -1.05 | -0.57 | -2.49 | [-2.70,+0.03] | -1.33 | +1.08 | -4 | -1.19 no | no |
| IWM:iv_level | YES | R0 | lnrv | +5.51 | -5.60 | +1.03 | [+1.01,+9.62] | -0.19 | +0.93 | 51 | -0.62 no | no | R0 | cross | -0.85 | -1.62 | -0.86 | [-1.77,+0.08] | -1.06 | +1.36 | -2 | -0.52 no | no |
| SPY:gamma | YES | R0 | lnrv | +5.31 | -1.34 | +3.61 | [+2.16,+8.44] | -0.19 | +0.93 | 51 | +1.84 weak | no | R0 | cross | -1.99 | -0.77 | -2.03 | [-3.83,-0.32] | -0.64 | +1.36 | -2 | -1.56 no | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.20 | -1.59 | +2.69 | [+1.77,+8.37] | -0.46 | +0.93 | 51 | +1.53 no | no | R0 | cross | -1.44 | -5.29 | -6.06 | [-3.52,+0.54] | -1.09 | +1.36 | -2 | -1.09 no | no |
| SPX:gamma | YES | R0 | lnrv | +5.18 | +0.45 | +6.52 | [+2.34,+8.09] | -0.46 | +0.93 | 51 | +1.34 weak | weak | R0 | er | +0.87 | +1.20 | +1.11 | [-2.49,+4.44] | -0.17 | +1.08 | -4 | +1.02 weak | no |
| tide | YES | R0 | lnrv | +5.10 | -3.00 | -1.22 | [+2.33,+8.13] | +0.68 | +0.93 | 51 | +3.22 YES | weak | R0 | er | +0.21 | +1.65 | +2.23 | [-0.74,+0.99] | -0.20 | +1.08 | -4 | -0.25 no | no |
| SPX:flip | YES | R0 | lnrng | +4.86 | +11.21 | +17.04 | [+0.91,+10.27] | +0.36 | +1.61 | 19 | +0.50 weak | weak | R0 | er | +0.35 | +2.69 | +0.07 | [-1.19,+1.84] | -0.34 | +1.08 | -4 | +0.81 weak | no |
| QQQ:gamma | YES | R0 | lnrv | +4.13 | -0.63 | +2.58 | [+2.05,+6.62] | -0.24 | +0.93 | 51 | +1.52 weak | no | R0 | er | -0.94 | -1.12 | -2.10 | [-2.84,+0.93] | -0.34 | +1.08 | -4 | -0.81 no | no |

### pre
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R0 | lnrng | +16.54 | +14.33 | +18.10 | [+9.56,+23.08] | +0.89 | +4.45 | 18 | +7.98 YES | weak | R0 | cross | +0.10 | -0.88 | -2.98 | [-1.26,+1.46] | -0.31 | +1.54 | -3 | -0.16 no | YES |
| DIA:iv_term | YES | R0 | lnrv | +12.78 | +3.92 | +15.81 | [+7.31,+17.48] | +1.55 | +4.18 | 31 | +2.86 weak | no | R1 | er | -1.16 | -2.78 | -1.49 | [-3.52,+1.14] | -0.13 | +1.42 | -3 | -1.29 no | no |
| ALL4:flip | YES | R0 | lnrv | +8.43 | +7.25 | +17.09 | [+4.97,+11.57] | -0.56 | +4.18 | 31 | +2.56 YES | no | R1 | cext | -1.44 | -3.47 | -1.17 | [-3.67,+0.76] | -1.32 | +1.98 | -4 | -1.44 no | no |
| SPX:iv_level | YES | R0 | lnrv | +7.38 | +4.05 | +13.70 | [+4.01,+10.18] | -0.55 | +4.18 | 31 | -0.23 no | no | R0 | cext | -0.60 | -0.11 | -0.18 | [-1.89,+0.77] | -1.07 | +1.98 | -3 | -0.08 no | no |
| DIA:iv_level | YES | R0 | lnrng | +7.22 | +4.29 | +4.03 | [+1.59,+12.85] | -0.33 | +4.45 | 18 | -0.35 no | no | R0 | er | -0.48 | -0.40 | -0.46 | [-1.71,+0.81] | -0.61 | +1.42 | -1 | -0.36 no | no |
| SPY:iv_level | YES | R0 | lnrng | +6.87 | +3.31 | +0.65 | [+2.62,+12.20] | -0.23 | +4.45 | 18 | -0.20 weak | no | R0 | cext | -0.56 | +0.07 | +0.62 | [-2.08,+0.84] | -1.08 | +1.98 | -3 | -0.34 no | no |
| IWM:iv_level | YES | R0 | lnrv | +6.75 | +3.00 | +10.59 | [+1.91,+12.05] | -0.85 | +4.18 | 31 | -0.65 no | no | R0 | er | -0.32 | -0.20 | -0.16 | [-2.11,+2.02] | -0.54 | +1.42 | -1 | -0.87 no | no |
| SPY:flip | YES | R0 | lnrv | +6.16 | +7.61 | +15.47 | [+2.50,+10.59] | -0.80 | +4.18 | 31 | -0.67 weak | no | R1 | cext | -0.25 | +0.12 | -0.54 | [-2.35,+1.36] | -0.91 | +1.98 | -4 | -0.08 weak | no |
| IWM:flip | YES | R0 | lnrv | +6.04 | +4.38 | +13.68 | [+2.92,+8.74] | -0.55 | +4.18 | 31 | +1.51 weak | no | R1 | er | -0.98 | -0.53 | -0.27 | [-1.78,-0.24] | -0.64 | +1.42 | -3 | -0.74 no | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.26 | +0.34 | +12.05 | [+1.32,+8.63] | -0.62 | +4.18 | 31 | +0.66 no | no | R1 | cext | -0.08 | +2.40 | +1.21 | [-2.25,+1.95] | -1.08 | +1.98 | -4 | +1.93 weak | no |
| SPY:iv_term | YES | R0 | lnrv | +5.06 | +8.88 | +14.47 | [+1.04,+9.49] | -0.74 | +4.18 | 31 | +0.25 weak | no | R0 | er | -2.79 | -2.77 | -4.92 | [-6.35,+0.21] | -1.34 | +1.42 | -1 | -2.35 no | weak |
| QQQ:iv_term | YES | R0 | lnrv | +4.75 | +10.88 | +15.62 | [+1.48,+9.18] | -1.73 | +4.18 | 31 | -0.18 no | no | R0 | er | -3.31 | -3.58 | -5.05 | [-6.82,+0.07] | -0.65 | +1.42 | -1 | -3.65 no | no |
| SPX:gamma | YES | R0 | lnrv | +4.54 | +3.14 | +14.48 | [+0.97,+9.02] | -0.93 | +4.18 | 31 | -0.79 no | no | R0 | er | -1.06 | +1.10 | +2.22 | [-3.10,+0.70] | -1.03 | +1.42 | -1 | -1.08 no | no |
| cal:dow | YES | R1 | lnrng | +4.51 | +2.99 | +4.50 | [-0.81,+8.06] | +4.45 | +4.45 | 18 | +0.12 no | no | R0 | cross | -1.36 | -3.48 | -2.92 | [-3.19,+0.16] | -1.48 | +1.54 | -3 | -0.10 no | weak |

### nyam
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DIA:iv_term | YES | R0 | lnrv | +10.29 | +5.95 | +8.70 | [+5.15,+15.81] | +2.69 | +3.43 | 39 | +4.60 YES | no | R2 | er | -0.45 | +0.40 | +0.41 | [-2.04,+1.64] | -0.89 | +1.35 | -6 | -0.61 no | no |
| IWM:iv_term | YES | R0 | lnrv | +9.33 | +8.74 | +5.56 | [+5.02,+14.37] | +2.15 | +3.43 | 39 | +6.50 YES | no | R0 | cross | -0.61 | -0.89 | -0.41 | [-1.74,+0.45] | -0.48 | +1.88 | -1 | -1.02 no | no |
| SPX:charm | YES | R1 | lnrv | +8.46 | +11.86 | -1.19 | [+3.33,+14.40] | +0.54 | +3.43 | 54 | +7.36 YES | no | R1 | cext | -0.62 | -1.75 | -0.50 | [-2.32,+1.21] | +0.15 | +1.79 | -4 | -0.32 no | no |
| SPY:iv_term | YES | R0 | lnrv | +7.64 | +12.82 | +6.25 | [+2.51,+12.79] | -0.00 | +3.43 | 39 | +2.13 weak | no | R2 | cext | -1.95 | -1.93 | -2.46 | [-5.58,+1.20] | -2.43 | +1.79 | -5 | -2.04 no | no |
| QQQ:vanna | YES | R2 | lnrv | +6.73 | +7.70 | +0.71 | [+2.61,+10.82] | +0.67 | +3.43 | 57 | +5.24 YES | no | R1 | cross | -0.65 | +1.28 | +1.57 | [-2.13,+0.71] | -1.15 | +1.88 | -2 | -0.77 no | no |
| QQQ:iv_term | weak | R0 | lnrv | +5.46 | +15.75 | +7.45 | [-2.05,+11.31] | -0.15 | +3.43 | 39 | -0.07 no | no | R1 | cext | -2.65 | -1.84 | -1.77 | [-6.04,+0.90] | -2.67 | +1.79 | -4 | -3.42 no | no |
| SPY:flip | YES | R0 | lnrv | +4.56 | -1.94 | -6.21 | [+1.69,+7.49] | -0.50 | +3.43 | 39 | +0.89 weak | no | R0 | cross | -0.20 | -0.03 | -1.01 | [-1.59,+0.86] | -0.54 | +1.88 | -1 | -0.33 no | weak |
| ALL4:flip | YES | R0 | lnrv | +4.50 | -3.11 | -14.48 | [+1.10,+7.69] | -0.81 | +3.43 | 39 | +1.48 weak | weak | R2 | cross | +0.93 | +1.14 | +1.40 | [-0.93,+2.99] | -0.55 | +1.88 | -2 | +0.82 weak | no |
| QQQ:iv_level | YES | R0 | lnrv | +4.41 | +1.65 | -6.41 | [+0.44,+8.17] | -0.27 | +3.43 | 39 | +0.66 weak | no | R2 | cross | +0.26 | +2.91 | +1.58 | [-1.03,+1.51] | +0.72 | +1.88 | -2 | +0.19 no | no |
| SPX:iv_level | YES | R0 | lnrv | +4.14 | -2.15 | -4.05 | [+1.02,+7.79] | -0.25 | +3.43 | 39 | -0.09 no | weak | R0 | cext | +1.06 | -3.02 | -0.94 | [-0.85,+3.40] | -0.36 | +1.79 | -2 | -0.03 no | weak |
| SPY:gamma | YES | R0 | lnrv | +3.81 | -2.28 | -8.47 | [+0.86,+7.09] | -0.41 | +3.43 | 39 | +0.66 weak | no | R0 | cext | -1.14 | -0.45 | +2.19 | [-3.52,+1.03] | -0.10 | +1.79 | -2 | -1.72 no | no |
| SPY:iv_level | YES | R0 | lnrv | +3.72 | -1.12 | -2.77 | [+0.27,+7.51] | -0.21 | +3.43 | 39 | -0.36 no | weak | R0 | cext | +0.72 | -1.81 | +0.11 | [-1.37,+2.56] | -0.72 | +1.79 | -2 | -0.39 no | weak |
| SPX:gamma | YES | R0 | lnrv | +3.66 | +0.84 | -4.47 | [+1.68,+6.55] | -0.44 | +3.43 | 39 | +0.74 weak | no | R1 | cross | -1.47 | +0.35 | +1.00 | [-3.63,+0.33] | -1.40 | +1.88 | -2 | -1.84 no | no |
| ALL4:gamma | weak | R0 | lnrv | +3.27 | -0.30 | -9.37 | [+0.89,+6.45] | -0.83 | +3.43 | 39 | +0.92 weak | no | R0 | cross | -0.80 | +0.62 | -0.34 | [-3.58,+1.75] | -0.88 | +1.88 | -1 | -1.95 no | no |

### nypm
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R1 | lnrv | +6.07 | +9.51 | +14.91 | [+3.70,+8.54] | +1.85 | +4.40 | 45 | +1.23 weak | YES | R3 | cross | +2.45 | +4.20 | +1.53 | [+0.67,+3.98] | +0.02 | +1.86 | -3 | +2.66 YES | no |
| DIA:iv_term | YES | R0 | lnrv | +5.44 | +0.75 | +5.85 | [+2.91,+8.30] | +1.64 | +4.40 | 41 | +0.85 weak | YES | R3 | cross | +1.98 | +7.36 | +6.23 | [+0.47,+3.48] | +0.29 | +1.86 | -3 | +3.03 YES | weak |
| QQQ:flip | YES | R3 | lnrv | +4.73 | +12.44 | +15.91 | [+2.03,+8.09] | -0.36 | +4.40 | 47 | +5.02 YES | no | R3 | er | -0.47 | -3.21 | -0.71 | [-2.06,+0.88] | +0.06 | +2.10 | -4 | -0.72 no | weak |
| SPY:flip | YES | R3 | lnrv | +4.57 | +7.85 | +10.97 | [+2.46,+7.10] | -0.11 | +4.40 | 47 | +3.69 YES | no | R2 | cext | -1.07 | +0.03 | +0.92 | [-2.78,+0.46] | -0.55 | +2.63 | -4 | -1.03 no | no |
| cal:dow | weak | R1 | lnrv | +4.34 | +2.86 | +4.45 | [+1.94,+7.21] | +4.40 | +4.40 | 45 | +0.01 no | no | R2 | cext | -0.62 | +1.19 | -1.46 | [-2.48,+1.47] | -0.64 | +2.63 | -4 | -0.08 no | weak |
| QQQ:walls | weak | R3 | lnrv | +4.25 | +7.90 | +8.26 | [+1.78,+7.15] | -0.60 | +4.40 | 47 | +3.78 YES | no | R0 | cross | -1.60 | -1.44 | -3.40 | [-2.98,+0.02] | -1.70 | +1.86 | -3 | -1.65 no | no |
| SPX:flip | weak | R3 | lnrv | +4.06 | +5.22 | +8.60 | [+1.44,+6.67] | +0.10 | +4.40 | 47 | +3.49 YES | weak | R0 | cext | +0.44 | +0.83 | +2.48 | [-0.94,+1.89] | +0.87 | +2.63 | -1 | -0.11 weak | weak |
| ALL4:flip | weak | R3 | lnrv | +4.04 | +7.29 | +11.74 | [+1.23,+7.05] | +0.04 | +4.40 | 47 | +3.46 YES | no | R0 | cross | -0.38 | -2.77 | -0.02 | [-2.93,+1.90] | +0.00 | +1.86 | -3 | -0.46 no | no |
| SPX:gamma | weak | R3 | lnrv | +3.83 | +7.13 | +11.45 | [+1.54,+6.71] | +0.13 | +4.40 | 47 | +2.53 YES | weak | R0 | cross | +0.63 | +4.76 | +4.16 | [-1.49,+3.06] | -0.68 | +1.86 | -3 | +0.21 weak | no |
| IWM:flip | weak | R2 | lnrv | +3.82 | -0.74 | +1.06 | [+1.54,+5.99] | +0.26 | +4.40 | 46 | +3.13 YES | no | R3 | cross | -0.77 | -0.22 | -1.04 | [-2.19,+0.85] | -0.26 | +1.86 | -3 | -1.71 no | no |
| SPX:walls | weak | R3 | lnrv | +3.68 | +2.68 | +7.76 | [+1.02,+6.77] | -0.31 | +4.40 | 47 | +3.94 YES | weak | R2 | cext | +0.35 | -1.73 | -1.24 | [-1.89,+3.65] | -0.02 | +2.63 | -4 | -0.16 no | no |
| NDX:flip | weak | R3 | lnrv | +3.60 | +9.97 | +14.44 | [+1.18,+6.40] | -0.20 | +4.40 | 47 | +4.24 YES | no | R0 | cross | -1.08 | -2.02 | -3.00 | [-2.54,+0.42] | -0.52 | +1.86 | -3 | -1.01 no | no |
| QQQ:impmove_vs_actual | weak | R3 | lnrv | +3.42 | +4.95 | +1.95 | [-0.25,+6.50] | -0.24 | +4.40 | 47 | +2.97 weak | weak | R2 | cext | +0.53 | +0.30 | +1.10 | [-1.06,+1.98] | -0.27 | +2.63 | -4 | +0.24 weak | no |
| QQQ:gamma | weak | R3 | lnrv | +3.26 | +10.39 | +19.44 | [+0.50,+5.95] | +0.72 | +4.40 | 47 | +1.84 weak | no | R1 | cross | -0.23 | +1.92 | -3.89 | [-3.24,+2.33] | +0.51 | +1.86 | -4 | -0.87 no | no |

### NY AM after 10:00 (10:00-12:00 ET, only from the 10:00 reading)
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R3 | lnrv | +5.49 | +9.45 | +12.61 | [+3.36,+7.28] | +2.87 | +3.24 | 60 | +3.18 YES | no | R3 | er | +0.28 | -0.54 | -0.04 | [-1.72,+2.14] | +0.98 | +2.54 | -6 | -0.29 no | no |
| DIA:iv_term | YES | R3 | lnrv | +4.40 | +6.42 | +7.77 | [+2.69,+6.14] | +2.46 | +3.24 | 60 | +1.40 weak | no | R3 | cross | -0.05 | +1.94 | -0.43 | [-1.20,+1.08] | -0.22 | +2.37 | -8 | +0.04 no | no |
| SPX:charm | YES | R3 | lnrv | +4.14 | +3.40 | -3.77 | [+1.17,+7.69] | +0.08 | +3.24 | 60 | +3.54 YES | no | R3 | cext | -1.94 | -2.27 | +0.55 | [-4.17,-0.35] | -0.89 | +2.94 | -4 | -2.49 no | weak |
| QQQ:vanna | YES | R3 | lnrv | +3.81 | +4.19 | -8.30 | [+0.80,+7.29] | +0.59 | +3.24 | 60 | +2.68 weak | no | R3 | er | -0.62 | -1.46 | +0.45 | [-3.23,+2.39] | -0.14 | +2.54 | -6 | -0.97 no | no |
| SPX:gamma | YES | R3 | lnrv | +3.43 | +3.06 | +0.84 | [+0.71,+7.28] | +0.02 | +3.24 | 60 | +3.01 YES | no | R3 | cext | -1.54 | +2.29 | +2.68 | [-3.53,+0.35] | -1.26 | +2.94 | -4 | -1.19 no | no |
| QQQ:zdte_share | weak | R3 | lnrv | +3.01 | +6.07 | +14.48 | [+1.56,+4.57] | +0.98 | +3.24 | 60 | +1.14 weak | no | R3 | cross | -0.89 | -1.50 | -4.63 | [-2.54,+0.77] | -0.18 | +2.37 | -8 | -0.83 no | no |
| NDX:gamma | weak | R3 | lnrv | +2.69 | +11.13 | +16.66 | [-0.06,+5.64] | +0.34 | +3.24 | 60 | +1.90 weak | no | R3 | er | -1.44 | -5.97 | -6.95 | [-4.11,+1.47] | -0.61 | +2.54 | -6 | -1.69 no | no |
| SPY:zdte_share | weak | R3 | lnrv | +2.68 | +6.17 | +12.93 | [+1.03,+3.99] | +1.09 | +3.24 | 60 | +1.23 weak | no | R3 | cross | -0.18 | +0.65 | -3.71 | [-1.82,+1.36] | -0.34 | +2.37 | -8 | -0.35 no | no |
| SPY:iv_term | weak | R3 | lnrv | +2.60 | +8.26 | +7.00 | [-2.60,+6.65] | +0.22 | +3.24 | 60 | -0.94 no | no | R3 | er | -2.26 | -1.65 | -0.95 | [-6.18,+0.48] | -0.91 | +2.54 | -6 | -1.97 no | no |
| cal:dow | no | R3 | lnrv | +2.57 | +1.54 | +6.24 | [+1.05,+4.02] | +3.23 | +3.24 | 60 | +0.01 no | no | R3 | er | -0.01 | -0.16 | +0.72 | [-2.54,+2.30] | +0.30 | +2.54 | -6 | -0.05 no | no |
| NDX:flip | weak | R3 | lnrv | +2.29 | +2.73 | +9.28 | [+0.84,+3.96] | -0.04 | +3.24 | 60 | +2.20 YES | no | R3 | cext | +0.08 | +2.32 | +2.44 | [-1.66,+1.53] | +2.94 | +2.94 | -4 | -0.06 no | no |
| QQQ:gamma | weak | R3 | lnrv | +2.18 | +7.27 | +14.51 | [-2.27,+6.28] | +0.29 | +3.24 | 60 | +2.03 weak | no | R3 | cext | -0.66 | +0.17 | +2.61 | [-2.40,+1.19] | -1.08 | +2.94 | -4 | -1.31 no | no |
| QQQ:flip | weak | R3 | lnrv | +1.89 | +2.86 | +3.71 | [+0.30,+3.71] | +0.49 | +3.24 | 60 | +1.45 weak | no | R3 | er | -0.14 | +0.01 | -0.18 | [-1.59,+1.23] | -0.33 | +2.54 | -6 | +0.03 weak | no |
| ALL4:flip | weak | R3 | lnrv | +1.87 | +1.41 | +2.46 | [+0.17,+3.81] | +0.06 | +3.24 | 60 | +1.46 weak | weak | R3 | er | +0.75 | +1.95 | +3.01 | [-1.53,+4.03] | +0.05 | +2.54 | -6 | +0.55 weak | no |

### last 90 min (14:30-16:00 ET), readings R0 and R3
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | vs ATR+IV+DOW (gain, verdict) | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QQQ:flip | YES | R3 | lnrv | +6.28 | +12.94 | +14.16 | [+3.96,+9.49] | -0.45 | +2.31 | 45 | +6.64 YES | no | R3 | cross | -0.95 | -0.44 | -2.94 | [-2.14,+0.38] | -0.10 | +1.39 | -2 | -0.62 no | no |
| QQQ:walls | YES | R3 | lnrng | +6.06 | +2.48 | -3.86 | [+1.56,+10.07] | -1.07 | +2.23 | 29 | +6.08 YES | no | R0 | cross | -0.54 | -0.21 | -0.86 | [-1.80,+1.00] | -2.25 | +1.39 | -1 | -0.90 no | weak |
| DIA:iv_term | YES | R0 | lnrng | +5.82 | +8.59 | +5.52 | [+1.21,+8.90] | +0.67 | +2.23 | 27 | +2.42 weak | no | R3 | er | -0.18 | -0.58 | -2.86 | [-1.29,+0.71] | +0.48 | +1.65 | -3 | +0.62 no | no |
| SPX:flip | YES | R3 | lnrv | +5.31 | +6.22 | +8.37 | [+3.02,+7.75] | -0.23 | +2.31 | 45 | +4.99 YES | weak | R0 | er | +0.56 | +0.59 | +0.36 | [-0.78,+1.77] | +0.00 | +1.65 | -3 | +0.48 weak | no |
| SPY:flip | YES | R3 | lnrv | +5.30 | +8.46 | +10.72 | [+3.23,+8.22] | -0.19 | +2.31 | 45 | +4.85 YES | no | R3 | er | -0.64 | +0.54 | -0.23 | [-1.60,+0.29] | -0.43 | +1.65 | -3 | -0.76 weak | no |
| ALL4:flip | YES | R3 | lnrv | +5.25 | +7.80 | +11.61 | [+2.68,+7.96] | -0.24 | +2.31 | 45 | +5.04 YES | no | R3 | cross | -1.03 | -1.56 | -2.89 | [-2.20,+0.21] | -0.07 | +1.39 | -2 | -1.03 no | weak |
| IWM:iv_term | YES | R0 | lnrng | +5.18 | +10.65 | +6.76 | [+2.15,+8.79] | -0.11 | +2.23 | 27 | +2.74 YES | no | R3 | er | -0.13 | -0.88 | -1.94 | [-1.72,+1.16] | +0.73 | +1.65 | -3 | -0.09 no | no |
| NDX:flip | YES | R3 | lnrv | +4.54 | +10.18 | +11.44 | [+2.37,+7.15] | -0.25 | +2.31 | 45 | +5.49 YES | no | R3 | er | -1.01 | -0.38 | -2.64 | [-2.36,+0.15] | -0.24 | +1.65 | -3 | -1.12 no | YES |
| SPX:walls | YES | R3 | lnrv | +4.49 | +6.42 | +11.03 | [+2.05,+7.27] | -0.37 | +2.31 | 45 | +4.66 YES | no | R3 | cext | -1.29 | +0.10 | +2.68 | [-3.50,+0.60] | -1.26 | +1.93 | -7 | -1.12 no | no |
| QQQ:impmove_vs_actual | YES | R3 | lnrv | +4.29 | +6.98 | +3.64 | [+1.23,+7.57] | -0.32 | +2.31 | 45 | +4.26 YES | no | R3 | er | -0.26 | +0.63 | +0.56 | [-1.26,+0.68] | -0.35 | +1.65 | -3 | -0.12 no | no |
| IWM:flip | YES | R0 | lnrng | +4.24 | -1.00 | -5.86 | [+1.00,+7.98] | -0.62 | +2.23 | 27 | +2.45 YES | no | R0 | er | -0.60 | -0.46 | -0.60 | [-1.37,+0.26] | -0.64 | +1.65 | -3 | -0.71 weak | no |
| SPX:gamma | YES | R3 | lnrv | +3.53 | +7.15 | +11.64 | [+1.25,+5.76] | +0.04 | +2.31 | 45 | +3.03 YES | no | R0 | cext | -0.80 | -0.95 | +0.80 | [-3.03,+1.45] | -0.83 | +1.93 | -4 | +0.60 weak | no |
| SPY:walls | YES | R3 | lnrv | +3.41 | +6.95 | +9.36 | [+1.21,+6.22] | -0.84 | +2.31 | 45 | +4.01 YES | no | R0 | cext | -0.36 | +0.32 | +1.68 | [-2.34,+2.33] | -0.67 | +1.93 | -4 | +0.32 weak | no |
| NDX:impmove_vs_actual | weak | R3 | lnrv | +3.34 | +4.02 | -2.02 | [-1.02,+7.03] | -0.16 | +2.31 | 45 | +4.13 weak | no | R3 | er | -0.53 | +0.96 | +0.42 | [-2.05,+0.63] | -0.30 | +1.65 | -3 | -0.43 no | no |

## 3. Compact answer: input family x session, best ticker. R = range, T = day type; verdict vs ATR / vs strict (ATR+IV+DOW); gain pp vs ATR / vs strict
| input family | asia | london | pre | nyam | nypm | nyam2 | late |
|---|---|---|---|---|---|---|---|
| absflip_wall | R:YES/weak +3.9/+1.5 (SPX) ; T:weak/weak +1.2/+0.9 | R:YES/weak +2.4/+0.3 (QQQ) ; T:weak/weak +1.5/+1.4 | R:weak/YES +3.9/+1.8 (IWM) ; T:weak/weak +0.3/+0.4 | R:weak/weak +1.4/+0.1 (DIA) ; T:weak/weak +0.7/+0.9 | R:weak/weak +0.9/+0.3 (QQQ) ; T:weak/weak +0.5/+0.1 | R:no/no +0.6/+0.5 (IWM) ; T:weak/weak +0.8/-1.0 | R:weak/weak +1.9/+0.8 (QQQ) ; T:weak/weak +0.7/+1.0 |
| charm | R:weak/weak +0.5/+0.4 (SPX) ; T:weak/weak +0.3/+0.1 | R:weak/weak +2.1/+2.2 (SPY) ; T:weak/weak +0.3/-0.3 | R:weak/weak +1.9/+0.3 (SPX) ; T:weak/weak +1.1/+1.0 | R:YES/YES +8.5/+7.4 (SPX) ; T:weak/weak +0.7/+0.4 | R:weak/weak +1.1/-0.1 (QQQ) ; T:weak/no +0.4/-0.3 | R:YES/YES +4.1/+3.5 (SPX) ; T:no/no -0.1/-0.4 | R:weak/no +0.6/+0.2 (DIA) ; T:no/no -0.2/-0.2 |
| dow | R:no/no +1.8/-0.0 (cal) ; T:no/no +1.7/-0.1 | R:no/no -0.0/-0.0 (cal) ; T:no/no +0.8/-0.1 | R:YES/no +4.5/+0.1 (cal) ; T:no/no -1.4/-0.1 | R:weak/no +3.2/+0.0 (cal) ; T:no/no -0.7/-0.1 | R:weak/no +4.3/+0.0 (cal) ; T:no/no -0.6/-0.1 | R:no/no +2.6/+0.0 (cal) ; T:no/no -0.0/-0.1 | R:no/no +2.0/-0.0 (cal) ; T:no/no -0.2/-0.1 |
| dp_levels | R:no/no -0.2/-1.4 (SPY) ; T:no/no -3.2/-3.5 | R:no/no -1.0/-1.8 (SPY) ; T:no/no -0.4/-0.5 | R:no/no -0.6/-0.5 (SPY) ; T:weak/no +0.2/-0.3 | R:no/no -1.9/-2.8 (QQQ) ; T:no/no -1.0/-1.1 | R:no/no -2.0/-1.2 (SPY) ; T:no/no -2.6/-2.8 | R:no/no -2.2/-2.0 (SPY) ; T:no/no -3.0/-3.0 | R:no/no -1.5/-0.2 (SPY) ; T:no/no -2.8/-2.8 |
| flip | R:YES/YES +8.2/+1.9 (SPY) ; T:weak/weak +0.4/+0.3 | R:YES/YES +7.8/+3.1 (ALL4) ; T:weak/weak +1.5/+0.8 | R:YES/YES +8.4/+2.6 (ALL4) ; T:weak/weak +0.0/+0.1 | R:YES/weak +4.6/+0.9 (SPY) ; T:weak/weak +0.9/+0.8 | R:YES/YES +4.7/+5.0 (QQQ) ; T:weak/weak +0.4/-0.1 | R:weak/YES +2.3/+2.2 (NDX) ; T:weak/weak +1.2/+1.0 | R:YES/YES +6.3/+6.6 (QQQ) ; T:weak/weak +0.6/+0.5 |
| gamma | R:YES/weak +5.8/+1.7 (SPX) ; T:weak/weak +0.4/-0.1 | R:YES/weak +5.3/+1.8 (SPY) ; T:weak/weak +0.9/+1.0 | R:YES/weak +4.5/-0.8 (SPX) ; T:no/weak -0.5/+0.0 | R:YES/weak +3.8/+0.7 (SPY) ; T:no/no -0.2/-0.9 | R:weak/YES +3.8/+2.5 (SPX) ; T:weak/weak +2.3/+2.1 | R:YES/YES +3.4/+3.0 (SPX) ; T:no/no -0.7/-1.3 | R:YES/YES +3.5/+3.0 (SPX) ; T:weak/weak +1.7/+1.7 |
| gamma_chg | - | - | - | - | R:weak/YES +1.9/+2.5 (SPX) ; T:weak/weak +0.5/+0.5 | R:weak/weak +0.4/+1.1 (NDX) ; T:weak/weak +0.3/-0.2 | R:weak/weak +1.6/+2.3 (SPX) ; T:YES/weak +1.9/+1.6 |
| impmove_vs_actual | - | - | R:weak/weak +1.4/-0.1 (QQQ) ; T:weak/weak +0.7/+1.0 | R:weak/weak +1.9/+0.9 (QQQ) ; T:weak/weak +1.1/+1.0 | R:weak/weak +3.4/+3.0 (QQQ) ; T:weak/weak +0.5/+0.2 | R:no/weak +0.5/-0.3 (QQQ) ; T:weak/weak +0.5/+0.5 | R:YES/YES +4.3/+4.3 (QQQ) ; T:weak/weak +0.8/+1.0 |
| iv_level | R:YES/YES +8.0/+2.4 (QQQ) ; T:weak/weak +0.7/+1.1 | R:YES/no +6.5/-0.6 (DIA) ; T:no/no -0.6/-0.2 | R:YES/weak +7.4/-0.2 (SPX) ; T:weak/weak +0.1/+2.1 | R:YES/weak +4.4/+0.7 (QQQ) ; T:weak/weak +1.1/-0.0 | R:weak/weak +2.9/-0.1 (SPX) ; T:weak/weak +1.2/+1.7 | R:no/no +0.5/+0.6 (QQQ) ; T:no/no -0.2/-0.2 | R:weak/weak +2.3/-0.2 (SPX) ; T:weak/weak +0.2/+0.8 |
| iv_minus_rv | R:weak/weak +3.1/-1.2 (SPX) ; T:weak/weak +0.6/-0.0 | R:YES/no +2.9/-3.0 (SPX) ; T:weak/weak +0.1/+0.2 | R:weak/weak +3.1/-0.5 (IWM) ; T:no/weak -0.2/-0.1 | R:weak/weak +1.7/-1.9 (SPX) ; T:no/no -0.3/-0.6 | R:weak/no +0.4/-0.6 (DIA) ; T:weak/no +0.7/-0.7 | R:no/no -0.3/-0.0 (IWM) ; T:weak/weak +0.2/+0.5 | R:no/no -0.0/-0.8 (SPX) ; T:no/no +0.1/+0.2 |
| iv_term | R:YES/weak +6.6/+0.8 (DIA) ; T:weak/weak +3.8/+1.2 | R:YES/weak +7.3/+2.7 (DIA) ; T:weak/weak +0.8/-0.4 | R:YES/YES +16.5/+8.0 (IWM) ; T:weak/no +0.1/-0.2 | R:YES/YES +10.3/+4.6 (DIA) ; T:no/no -0.4/-0.6 | R:YES/weak +6.1/+1.2 (IWM) ; T:YES/YES +2.4/+2.7 | R:YES/YES +5.5/+3.2 (IWM) ; T:no/no +0.3/-0.3 | R:YES/YES +5.8/+2.4 (DIA) ; T:no/no -0.1/-0.1 |
| month_end | R:no/no -0.2/-0.2 (cal) ; T:no/no -0.2/-0.1 | R:weak/weak +0.4/+0.2 (cal) ; T:no/no -0.3/-0.5 | R:no/no -0.3/-0.1 (cal) ; T:no/no -0.2/-0.3 | R:no/no -0.0/-0.1 (cal) ; T:no/no -0.5/-0.3 | R:no/weak +0.0/+0.7 (cal) ; T:weak/no +0.0/-0.0 | R:no/no -0.1/-0.2 (cal) ; T:weak/no +0.3/+0.3 | R:no/no +0.2/+0.4 (cal) ; T:no/no -0.2/-0.3 |
| net_premium | R:YES/weak +2.5/+0.8 (QQQ) ; T:weak/no +0.1/-0.0 | R:YES/weak +2.0/+1.0 (SPX) ; T:weak/weak +0.8/+0.7 | R:weak/weak +1.8/+0.5 (SPX) ; T:weak/weak +0.3/+0.3 | R:weak/weak +0.7/+0.7 (QQQ) ; T:weak/weak +0.8/+0.6 | R:no/weak -0.0/+0.1 (QQQ) ; T:weak/no +0.2/-0.2 | R:weak/weak +1.3/+1.1 (QQQ) ; T:weak/weak +0.9/+1.0 | R:weak/weak +0.7/+1.6 (SPX) ; T:weak/weak +1.0/+0.7 |
| opex_day | R:no/no -0.0/-0.0 (cal) ; T:no/weak +0.1/+0.3 | R:no/no -0.2/-0.3 (cal) ; T:no/no -0.5/-0.6 | R:weak/no +0.5/-0.3 (cal) ; T:no/no -0.0/+0.1 | R:no/no -0.1/-0.1 (cal) ; T:weak/weak +0.1/+0.3 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.3/-0.3 | R:no/no -0.1/-0.2 (cal) ; T:no/no -0.2/-0.1 | R:no/no +0.1/-0.2 (cal) ; T:no/no -0.3/-0.3 |
| opex_week | R:no/no -0.3/-0.2 (cal) ; T:no/no -0.1/+0.1 | R:no/no -0.4/-0.2 (cal) ; T:no/no -0.4/-0.4 | R:no/no +0.3/+0.3 (cal) ; T:weak/weak +1.2/+0.9 | R:weak/no +0.2/+0.1 (cal) ; T:no/weak +0.1/+0.3 | R:no/no -0.1/-0.1 (cal) ; T:no/weak +0.0/+0.0 | R:no/no -0.0/-0.2 (cal) ; T:weak/weak +0.6/+0.7 | R:no/no -0.1/-0.2 (cal) ; T:no/no +0.5/+0.3 |
| quarter_end | R:no/no -0.1/-0.2 (cal) ; T:no/no -0.5/-0.5 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.1/-0.1 | R:no/no -0.1/-0.5 (cal) ; T:no/no -0.0/-0.1 | R:no/no -0.2/-0.6 (cal) ; T:weak/weak +0.4/+0.4 | R:no/no -0.1/+0.0 (cal) ; T:weak/weak +0.3/+0.1 | R:no/no -0.3/-0.4 (cal) ; T:weak/weak +1.1/+1.0 | R:no/no -0.1/-0.1 (cal) ; T:no/no -0.1/-0.1 |
| tide | R:YES/YES +6.0/+3.2 (mkt) ; T:no/no +0.2/+0.1 | R:YES/YES +5.1/+3.2 (mkt) ; T:weak/no +0.2/-0.3 | R:weak/weak +2.3/+0.9 (mkt) ; T:weak/no +0.9/+0.1 | R:weak/weak +0.5/+0.5 (mkt) ; T:no/no -0.1/-0.2 | R:weak/YES +2.9/+2.8 (mkt) ; T:no/no -0.4/-0.7 | R:no/no -0.5/-0.1 (mkt) ; T:no/no -0.7/-0.7 | R:weak/YES +2.2/+2.5 (mkt) ; T:no/weak +0.1/+0.2 |
| vanna | R:weak/no +1.5/-0.3 (NDX) ; T:weak/weak +0.5/+0.2 | R:YES/weak +1.9/+1.4 (QQQ) ; T:weak/no +0.2/-0.6 | R:weak/weak +0.6/+0.4 (NDX) ; T:weak/weak +0.1/+0.5 | R:YES/YES +6.7/+5.2 (QQQ) ; T:no/no -0.1/+0.2 | R:weak/weak +2.1/-0.8 (DIA) ; T:weak/weak +1.4/+0.7 | R:YES/weak +3.8/+2.7 (QQQ) ; T:no/weak -0.1/+0.1 | R:no/no +1.0/-0.3 (DIA) ; T:no/no -0.7/-0.7 |
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
| dark-pool levels (QQQ, SPY) | scored (family dp_levels) from the next rebuild; only 260 days (2025-11-14..) so the OOS sample is ~140 days: low power |
| dark-pool levels megacaps, megacap exposure / flow | waiting: megacap spot_1m and net_prem_ticks pull (W-UB3 chain C ETA ~22:00Z) |
| options tape by DTE and >= $100k | tape_agg/tape_big only cover ~31 days (2026-10-01..) so no out-of-sample test is possible yet (W-UB2 filling); screened when >= 200 days |
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

## 8. Exact-engine sets (tag UR)
None launched yet.
