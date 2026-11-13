# DS3_UWREGIME - Unusual Whales as a range / day-type forecaster (W-UR1). Rebuilt 2026-11-13T17:25:09Z by code/th_uwregime/ur_loop.sh (every 3 h). Research only, NO trading in this page, NO PASS claim.
Prereg: autopilot/UWREGIME_PREREG.md (sha in DECISIONS.md, logged before scoring). Question: does UW forecast, out of sample, the session range / realized vol, trend-vs-chop, pinning and time of high/low, and by how much OVER a no-UW benchmark.

## 0. Method in six lines
- Sample: 552 trading days 2024-10-02..2026-11-12 (UW history starts 2024-10-01; NQ 1-min prices; ES for SPX/SPY pin). Expanding-window ridge, min 120 days, refit every 10 trading days (= 2 weeks); out-of-sample R2 is vs the expanding mean.
- Benchmark (no UW; VIX is NOT on the box, ATR used): lag-1/5/20-day mean of the same target, lag-1 and ATR14 of the same-session range, ATR14 of the RTH range; for 08:30/09:30/10:00 readings also the range so far today, realized vol so far, |move since prior close| and that move in ATR units. UW model = benchmark + ONE input group (<= 6 features). Gain = R2(UW model) - R2(benchmark), in percentage points of variance explained (pp).
- Readings: R0 prior close (UW rows up to the prior close + prior-day EOD level files), R1 08:30, R2 09:30, R3 10:00 ET; a UW minute row is used only at start+180 s; EOD files (gex levels, spot-strike, vol stats, dp levels, IV term) only from the previous trading day; futures move since the prior close maps UW spot to the reading time. Targets: session ln range, ln realized vol (range class); efficiency ratio, close extremity, mean crossings (day-type class); time of first / last extreme (timing).
- Nulls: shifted-time null = UW inputs from k trading days earlier, k in 8..60, 20 draws, same refit; "null q95" per row, "fam q95" = q95 over draws of the MAX gain across all groups AND readings for that session-target (so picking the best group/reading is already charged). 90% CI = 5-day block bootstrap of the daily squared-error difference.
- Verdict: YES = gain > 0 and CI low > 0 and gain > family null q95; weak = gain > 0 and > per-row null q95 only (not corrected for picking among groups/readings); no = otherwise.
- NDX spot glitches: UW NDX spot is rounded and often frozen for hours; each minute row is checked against the NQ-implied price (0.4% tolerance, 0.6% for ES/RTY/YM) and dropped if off. Glitch days (>25% of rows dropped): {'DIA': 2, 'IWM': 5, 'NDX': 67, 'QQQ': 3, 'SPX': 3, 'SPY': 3}. Days with no UW file: {'DIA': 19, 'IWM': 19, 'NDX': 21, 'QQQ': 21, 'SPX': 21, 'SPY': 21}. Futures: continuous series with >1.2%/min roll jumps removed (15 on NQ).

## 1. Headline (3598 scored rows = reading x session x target x input group)
- YES rows: 123; weak rows: 487. Inputs with at least one YES (range class): ALL4:flip, ALL4:gamma, DIA:iv_level, DIA:iv_minus_rv, DIA:iv_term, IWM:absflip_wall, IWM:flip, IWM:iv_level, IWM:iv_minus_rv, IWM:iv_term, NDX:iv_level, QQQ:absflip_wall, QQQ:flip, QQQ:gamma, QQQ:iv_level, QQQ:net_premium, QQQ:vanna, QQQ:walls, SPX:absflip_wall, SPX:charm, SPX:flip, SPX:gamma, SPX:iv_level, SPX:iv_minus_rv, SPX:walls, SPY:flip, SPY:gamma, SPY:iv_level, SPY:iv_minus_rv, SPY:walls, cal:dow, tide.
- Inputs with at least one YES (day-type class): DIA:iv_term, IWM:iv_term.
- Inputs with at least one YES (timing class): SPX:vanna, cal:dow, cal:opex_day.

## 2. Per session: every input, range yes/no and day type yes/no, gain over the no-UW benchmark (pp of R2)
Columns: best reading R# for the range class (ln range / ln RV) and for the day-type class (ER / close extremity / crossings); gain full OOS / L6M / L3M in pp; CI = 90% bootstrap on the full-OOS gain; nq95 = per-row shifted null q95; fq95 = family null q95 (max over groups and readings). Bench R2 = benchmark R2 for that target (how much the no-UW model already explains). Sorted by range gain. Only the top 14 groups per session by best of (range, day-type) gain are listed; the full table is in /mnt/l2/l2vast/_uwregime/forecast_all.csv.

### asia
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SPY:flip | YES | R0 | lnrng | +8.18 | +14.56 | +15.83 | [+4.62,+12.53] | +0.03 | +2.75 | 24 | no | R0 | cext | -0.43 | +0.46 | -1.53 | [-1.40,+1.03] | -0.67 | +1.48 | -1 | no |
| QQQ:iv_level | YES | R0 | lnrng | +8.04 | +14.58 | +21.81 | [+2.99,+12.86] | -0.52 | +2.75 | 24 | no | R0 | cross | -0.72 | -5.32 | -1.23 | [-3.00,+1.36] | -0.13 | +2.07 | -7 | no |
| ALL4:flip | YES | R0 | lnrng | +7.67 | +11.78 | +12.43 | [+2.58,+11.51] | -0.35 | +2.75 | 24 | no | R0 | cross | -0.29 | +1.27 | +2.22 | [-3.77,+2.80] | -0.07 | +2.07 | -7 | no |
| SPY:iv_level | YES | R0 | lnrng | +7.29 | +11.10 | +22.41 | [+2.40,+11.51] | -0.36 | +2.75 | 24 | weak | R0 | cross | +0.70 | -0.19 | +0.41 | [-1.10,+2.48] | -0.34 | +2.07 | -7 | no |
| SPX:iv_level | YES | R0 | lnrng | +6.22 | +8.42 | +17.73 | [+2.26,+11.58] | -0.60 | +2.75 | 24 | weak | R0 | cross | +0.23 | +0.24 | +1.02 | [-0.82,+1.36] | -0.22 | +2.07 | -7 | no |
| tide | YES | R0 | lnrv | +6.02 | +7.95 | +10.04 | [+3.79,+8.62] | +0.40 | +2.01 | 56 | no | R0 | er | +0.22 | +0.09 | -1.45 | [-1.10,+1.41] | +0.42 | +1.74 | -6 | no |
| SPX:gamma | YES | R0 | lnrv | +5.76 | +6.06 | +9.20 | [+3.03,+9.08] | -0.29 | +2.01 | 56 | no | R0 | er | -1.89 | -0.71 | -2.18 | [-3.29,-0.34] | -0.47 | +1.74 | -6 | no |
| NDX:iv_level | YES | R0 | lnrv | +5.59 | +3.22 | +12.68 | [+2.54,+8.53] | -0.32 | +2.01 | 56 | no | R0 | er | -0.33 | -0.97 | -0.82 | [-1.66,+1.05] | +0.72 | +1.74 | -6 | no |
| SPY:gamma | YES | R0 | lnrv | +5.28 | +6.21 | +10.73 | [+2.51,+8.26] | -0.60 | +2.01 | 56 | no | R0 | er | -0.84 | -1.06 | -1.05 | [-3.05,+1.44] | +0.02 | +1.74 | -6 | no |
| QQQ:gamma | YES | R0 | lnrv | +5.02 | +7.89 | +10.07 | [+2.41,+8.29] | -0.32 | +2.01 | 56 | no | R0 | er | -1.80 | +0.18 | -1.13 | [-3.63,-0.08] | +0.80 | +1.74 | -6 | no |
| ALL4:gamma | YES | R0 | lnrv | +5.00 | +7.93 | +10.70 | [+2.06,+8.63] | -0.54 | +2.01 | 56 | no | R0 | cross | -0.76 | -1.87 | +1.01 | [-2.52,+1.18] | -0.45 | +2.07 | -7 | no |
| IWM:iv_term | YES | R0 | lnrng | +4.32 | -0.78 | +6.58 | [+0.30,+7.38] | -0.33 | +2.75 | 24 | YES | R0 | cross | +4.87 | +6.30 | +4.52 | [+0.22,+9.08] | +1.74 | +2.07 | -7 | weak |
| SPX:flip | YES | R0 | lnrng | +4.80 | +7.37 | +16.01 | [+1.60,+8.49] | +1.55 | +2.75 | 24 | no | R0 | cross | +0.05 | -1.40 | -2.99 | [-1.98,+1.84] | +0.17 | +2.07 | -7 | weak |
| IWM:flip | YES | R0 | lnrv | +4.71 | +3.28 | +4.34 | [+2.48,+6.39] | -0.34 | +2.01 | 56 | no | R0 | er | -0.52 | -1.16 | -5.54 | [-2.61,+1.35] | -0.37 | +1.74 | -6 | no |

### london
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL4:flip | YES | R0 | lnrv | +7.78 | +0.22 | -0.70 | [+4.35,+11.12] | -0.17 | +0.93 | 51 | weak | R0 | er | +1.43 | +4.17 | +5.05 | [-0.40,+3.28] | -0.87 | +1.07 | -4 | weak |
| IWM:flip | YES | R0 | lnrng | +6.74 | +5.57 | +1.41 | [+1.67,+10.90] | +0.78 | +2.38 | 19 | weak | R0 | cext | +0.16 | -0.04 | -1.16 | [-3.04,+3.11] | -0.65 | +1.77 | -2 | no |
| SPY:flip | YES | R0 | lnrng | +6.33 | +9.39 | +2.49 | [+1.70,+13.93] | -0.99 | +2.38 | 19 | weak | R0 | er | +0.73 | +4.81 | +4.24 | [-1.30,+2.54] | -0.60 | +1.07 | -4 | no |
| SPX:iv_level | YES | R0 | lnrv | +5.77 | -4.29 | +1.53 | [+2.44,+8.63] | -0.39 | +0.93 | 51 | no | R0 | cross | -0.58 | -1.30 | -0.12 | [-2.25,+1.17] | -0.44 | +1.34 | -2 | no |
| SPY:iv_level | YES | R0 | lnrng | +5.68 | +15.82 | +18.70 | [+1.13,+13.75] | -0.49 | +2.38 | 19 | no | R0 | er | -1.05 | -0.57 | -2.49 | [-2.13,+0.02] | -1.33 | +1.07 | -4 | no |
| SPY:gamma | YES | R0 | lnrv | +5.31 | -1.34 | +3.61 | [+2.40,+8.97] | -0.19 | +0.93 | 51 | no | R0 | cross | -1.99 | -0.77 | -2.03 | [-3.93,-0.40] | -0.64 | +1.34 | -2 | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.20 | -1.59 | +2.69 | [+1.34,+8.12] | -0.46 | +0.93 | 51 | no | R0 | cross | -1.44 | -5.29 | -6.06 | [-3.51,+0.75] | -1.09 | +1.34 | -2 | no |
| SPX:gamma | YES | R0 | lnrv | +5.18 | +0.45 | +6.52 | [+2.54,+8.22] | -0.46 | +0.93 | 51 | weak | R0 | er | +0.87 | +1.20 | +1.11 | [-2.97,+4.47] | -0.17 | +1.07 | -4 | no |
| tide | YES | R0 | lnrv | +5.10 | -3.00 | -1.22 | [+2.20,+7.79] | +0.68 | +0.93 | 51 | weak | R0 | er | +0.21 | +1.65 | +2.23 | [-0.76,+1.06] | -0.20 | +1.07 | -4 | no |
| DIA:iv_term | YES | R0 | lnrv | +4.96 | -8.04 | -3.54 | [+0.91,+8.97] | -0.39 | +0.93 | 51 | no | R0 | cross | -1.02 | -1.13 | -3.57 | [-3.76,+1.49] | -1.08 | +1.34 | -2 | no |
| SPX:flip | YES | R0 | lnrng | +4.86 | +11.21 | +17.04 | [+1.05,+10.37] | +0.36 | +2.38 | 19 | weak | R0 | er | +0.35 | +2.69 | +0.07 | [-1.20,+1.67] | -0.34 | +1.07 | -4 | no |
| DIA:iv_level | YES | R0 | lnrv | +4.64 | -2.50 | +6.49 | [+1.52,+7.89] | +0.46 | +0.93 | 51 | no | R0 | cross | -0.95 | -1.93 | -0.19 | [-2.70,+0.77] | -1.29 | +1.34 | -2 | no |
| QQQ:gamma | YES | R0 | lnrv | +4.13 | -0.63 | +2.58 | [+1.89,+6.59] | -0.24 | +0.93 | 51 | no | R0 | er | -0.94 | -1.12 | -2.10 | [-2.91,+1.15] | -0.34 | +1.07 | -4 | no |
| NDX:iv_level | YES | R0 | lnrv | +3.84 | -7.39 | -0.53 | [+0.07,+7.54] | -0.39 | +0.93 | 51 | no | R0 | cross | -1.04 | -4.44 | -4.44 | [-2.60,+0.89] | -0.75 | +1.34 | -2 | no |

### pre
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R0 | lnrng | +15.80 | +13.83 | +18.42 | [+6.22,+22.06] | +0.78 | +2.93 | 18 | no | R0 | er | -0.55 | -1.14 | -1.70 | [-1.66,+0.80] | +0.42 | +1.06 | -1 | weak |
| DIA:iv_term | YES | R0 | lnrv | +11.26 | +2.93 | +15.17 | [+5.88,+16.38] | -0.74 | +2.83 | 31 | no | R0 | er | -0.93 | -1.76 | -1.60 | [-2.60,+0.85] | -0.70 | +1.06 | -1 | no |
| ALL4:flip | YES | R0 | lnrv | +8.43 | +7.25 | +17.09 | [+4.72,+11.90] | -0.56 | +2.83 | 31 | no | R0 | cext | -1.69 | -3.70 | -4.28 | [-3.85,+0.07] | -0.94 | +1.55 | -3 | no |
| SPX:iv_level | YES | R0 | lnrv | +7.38 | +4.05 | +13.70 | [+4.01,+11.31] | -0.55 | +2.83 | 31 | no | R0 | cext | -0.60 | -0.11 | -0.18 | [-2.02,+0.76] | -1.07 | +1.55 | -3 | no |
| DIA:iv_level | YES | R0 | lnrv | +7.11 | +3.91 | +13.83 | [+3.20,+11.03] | -0.91 | +2.83 | 31 | no | R0 | er | -0.27 | -0.46 | -0.59 | [-1.97,+1.68] | -1.23 | +1.06 | -1 | no |
| SPY:iv_level | YES | R0 | lnrng | +6.87 | +3.31 | +0.65 | [+2.62,+12.20] | -0.23 | +2.93 | 18 | no | R0 | cext | -0.56 | +0.07 | +0.62 | [-2.12,+0.72] | -1.08 | +1.55 | -3 | no |
| IWM:iv_level | YES | R0 | lnrv | +6.77 | +4.03 | +10.47 | [+2.52,+11.36] | -0.93 | +2.83 | 31 | no | R0 | er | -0.43 | -0.35 | -0.32 | [-2.40,+1.64] | -0.93 | +1.06 | -1 | no |
| SPY:flip | YES | R0 | lnrv | +6.16 | +7.61 | +15.47 | [+2.45,+9.89] | -0.80 | +2.83 | 31 | no | R0 | er | -1.10 | -0.28 | +0.18 | [-2.29,+0.10] | -0.78 | +1.06 | -1 | no |
| QQQ:iv_level | YES | R0 | lnrv | +5.26 | +0.34 | +12.05 | [+0.72,+9.11] | -0.62 | +2.83 | 31 | no | R0 | er | -0.25 | +0.36 | +0.24 | [-2.17,+2.03] | -0.94 | +1.06 | -1 | no |
| IWM:flip | YES | R0 | lnrv | +5.01 | +4.55 | +13.54 | [+2.03,+8.15] | -0.95 | +2.83 | 31 | no | R0 | cext | -0.71 | -0.62 | -0.83 | [-2.38,+0.80] | -1.06 | +1.55 | -3 | no |
| SPX:gamma | YES | R0 | lnrv | +4.54 | +3.14 | +14.48 | [+0.61,+8.73] | -0.93 | +2.83 | 31 | no | R0 | er | -1.06 | +1.10 | +2.22 | [-3.34,+0.85] | -1.03 | +1.06 | -1 | no |
| NDX:iv_level | YES | R0 | lnrv | +4.35 | -2.21 | +10.18 | [+0.92,+7.56] | -0.55 | +2.83 | 31 | no | R0 | cext | -0.18 | +1.00 | +1.91 | [-1.62,+1.10] | -0.85 | +1.55 | -3 | no |
| SPX:flip | YES | R0 | lnrv | +4.19 | +3.32 | +13.08 | [+1.47,+7.22] | -0.66 | +2.83 | 31 | no | R0 | cross | -0.13 | -1.92 | -2.69 | [-1.82,+1.69] | -0.30 | +1.31 | -3 | weak |
| SPY:gamma | YES | R0 | lnrv | +3.72 | +4.98 | +14.00 | [+0.46,+8.01] | -1.08 | +2.83 | 31 | no | R0 | cext | -0.61 | -1.66 | +2.02 | [-2.92,+1.87] | -1.07 | +1.55 | -3 | no |

### nyam
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R0 | lnrv | +9.82 | +8.37 | +4.79 | [+5.62,+15.30] | +1.97 | +2.30 | 39 | no | R0 | cross | -1.00 | -1.18 | -0.65 | [-2.54,+0.35] | -0.93 | +1.75 | -1 | no |
| DIA:iv_term | YES | R0 | lnrv | +9.65 | +5.27 | +8.44 | [+3.91,+15.92] | +0.01 | +2.30 | 39 | no | R0 | er | -1.51 | -0.85 | +0.98 | [-2.98,-0.25] | -0.19 | +1.04 | -3 | no |
| SPY:flip | YES | R0 | lnrv | +4.56 | -1.94 | -6.21 | [+1.46,+7.47] | -0.50 | +2.30 | 39 | no | R0 | cross | -0.20 | -0.03 | -1.01 | [-1.67,+0.89] | -0.54 | +1.75 | -1 | no |
| ALL4:flip | YES | R0 | lnrv | +4.50 | -3.11 | -14.48 | [+0.97,+7.80] | -0.81 | +2.30 | 39 | no | R0 | cross | -0.12 | -0.48 | -0.91 | [-1.43,+1.06] | -0.56 | +1.75 | -1 | no |
| QQQ:iv_level | YES | R0 | lnrv | +4.41 | +1.65 | -6.41 | [+0.12,+7.82] | -0.27 | +2.30 | 39 | no | R0 | cext | -0.23 | -5.33 | +0.99 | [-2.81,+1.91] | -0.54 | +1.32 | -2 | no |
| SPX:iv_level | weak | R0 | lnrv | +4.14 | -2.15 | -4.05 | [-0.49,+7.43] | -0.25 | +2.30 | 39 | weak | R0 | cext | +1.06 | -3.02 | -0.94 | [-1.01,+3.71] | -0.36 | +1.32 | -2 | weak |
| SPY:gamma | YES | R0 | lnrv | +3.81 | -2.28 | -8.47 | [+1.06,+7.14] | -0.41 | +2.30 | 39 | no | R0 | cext | -1.14 | -0.45 | +2.19 | [-3.34,+1.02] | -0.10 | +1.32 | -2 | no |
| SPY:iv_level | weak | R0 | lnrv | +3.72 | -1.12 | -2.77 | [-0.44,+7.44] | -0.21 | +2.30 | 39 | weak | R0 | cext | +0.72 | -1.81 | +0.11 | [-1.12,+2.51] | -0.72 | +1.32 | -2 | weak |
| SPX:gamma | YES | R0 | lnrv | +3.66 | +0.84 | -4.47 | [+1.46,+6.42] | -0.44 | +2.30 | 39 | no | R0 | cext | -1.54 | -0.28 | +2.53 | [-3.54,+0.13] | -0.23 | +1.32 | -2 | no |
| ALL4:gamma | YES | R0 | lnrv | +3.27 | -0.30 | -9.37 | [+0.64,+6.30] | -0.83 | +2.30 | 39 | no | R0 | cross | -0.80 | +0.62 | -0.34 | [-3.51,+1.68] | -0.88 | +1.75 | -1 | no |
| DIA:iv_level | weak | R0 | lnrv | +3.16 | -2.74 | -1.33 | [-1.15,+6.82] | -0.70 | +2.30 | 39 | no | R0 | er | -0.48 | -0.45 | +1.12 | [-2.48,+1.34] | -0.36 | +1.04 | -3 | no |
| SPX:charm | YES | R0 | lnrv | +3.04 | +3.73 | +3.91 | [+0.78,+5.27] | -0.26 | +2.30 | 39 | no | R0 | cext | -1.22 | -1.01 | -1.43 | [-2.09,-0.28] | -0.33 | +1.32 | -2 | no |
| IWM:iv_level | weak | R0 | lnrv | +3.02 | -2.41 | -2.31 | [-2.21,+7.38] | -1.27 | +2.30 | 39 | weak | R0 | er | +0.23 | -0.34 | +0.11 | [-1.87,+2.41] | -0.93 | +1.04 | -3 | no |
| QQQ:gamma | YES | R0 | lnrv | +2.89 | +4.01 | +0.00 | [+0.08,+5.65] | +0.23 | +2.30 | 39 | no | R0 | cext | -0.68 | -2.85 | -0.36 | [-2.91,+1.51] | +0.21 | +1.32 | -2 | no |

### nypm
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R3 | lnrv | +5.15 | +8.10 | +12.86 | [+3.06,+7.40] | +0.95 | +4.05 | 47 | YES | R3 | cross | +2.34 | +4.05 | +1.46 | [+0.75,+3.95] | -0.35 | +1.83 | -3 | weak |
| QQQ:flip | YES | R3 | lnrv | +4.73 | +12.44 | +15.91 | [+1.85,+8.31] | -0.36 | +4.05 | 47 | no | R3 | er | -0.47 | -3.21 | -0.71 | [-2.10,+0.94] | +0.06 | +2.10 | -4 | weak |
| DIA:iv_term | YES | R0 | lnrv | +4.60 | -0.18 | +5.81 | [+1.98,+7.46] | +0.34 | +4.05 | 41 | YES | R3 | cross | +2.42 | +8.71 | +7.06 | [+0.71,+4.27] | -0.35 | +1.83 | -3 | weak |
| SPY:flip | YES | R3 | lnrv | +4.57 | +7.85 | +10.97 | [+2.30,+7.03] | -0.11 | +4.05 | 47 | no | R3 | er | -1.11 | -0.91 | -0.73 | [-2.38,+0.25] | -0.41 | +2.10 | -4 | no |
| QQQ:walls | YES | R3 | lnrv | +4.25 | +7.90 | +8.26 | [+1.64,+7.13] | -0.60 | +4.05 | 47 | no | R0 | cross | -1.60 | -1.44 | -3.40 | [-3.26,-0.01] | -1.70 | +1.83 | -3 | no |
| SPX:flip | YES | R3 | lnrv | +4.06 | +5.22 | +8.60 | [+1.64,+6.84] | +0.10 | +4.05 | 47 | weak | R0 | cext | +0.44 | +0.83 | +2.48 | [-1.00,+2.12] | +0.87 | +2.36 | -1 | weak |
| ALL4:flip | weak | R3 | lnrv | +4.04 | +7.29 | +11.74 | [+1.23,+7.01] | +0.04 | +4.05 | 47 | no | R0 | cross | -0.38 | -2.77 | -0.02 | [-3.25,+1.92] | +0.00 | +1.83 | -3 | no |
| cal:dow | weak | R3 | lnrv | +4.00 | +3.39 | +5.44 | [+1.61,+6.62] | +4.05 | +4.05 | 47 | no | R0 | cext | -0.86 | +1.43 | -0.93 | [-2.86,+1.04] | -0.87 | +2.36 | -1 | weak |
| SPX:gamma | weak | R3 | lnrv | +3.83 | +7.13 | +11.45 | [+1.70,+6.18] | +0.13 | +4.05 | 47 | weak | R0 | cross | +0.63 | +4.76 | +4.16 | [-1.48,+2.66] | -0.68 | +1.83 | -3 | no |
| SPX:walls | weak | R3 | lnrv | +3.68 | +2.68 | +7.76 | [+1.14,+6.38] | -0.31 | +4.05 | 47 | weak | R3 | er | +0.08 | +3.78 | +5.35 | [-2.20,+2.69] | -0.44 | +2.10 | -4 | no |
| NDX:flip | weak | R3 | lnrv | +3.60 | +9.97 | +14.44 | [+1.02,+6.29] | -0.20 | +4.05 | 47 | no | R0 | cross | -1.08 | -2.02 | -3.00 | [-2.60,+0.28] | -0.52 | +1.83 | -3 | no |
| QQQ:impmove_vs_actual | weak | R3 | lnrv | +3.42 | +4.95 | +1.95 | [-0.01,+7.21] | -0.24 | +4.05 | 47 | no | R3 | er | -0.10 | -0.24 | -0.72 | [-0.60,+0.48] | +0.85 | +2.10 | -4 | no |
| QQQ:gamma | weak | R3 | lnrv | +3.26 | +10.39 | +19.44 | [+0.68,+6.19] | +0.72 | +4.05 | 47 | no | R3 | cross | -0.72 | +0.90 | -2.46 | [-3.87,+1.67] | +0.29 | +1.83 | -3 | no |
| tide | weak | R3 | lnrv | +2.92 | +9.95 | +15.46 | [+1.36,+4.69] | -0.21 | +4.05 | 47 | no | R0 | cext | -0.50 | -0.36 | -0.31 | [-1.05,+0.04] | -0.30 | +2.36 | -1 | no |

### NY AM after 10:00 (10:00-12:00 ET, only from the 10:00 reading)
| input | range | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | day type | rd | metric | gain full | L6M | L3M | CI90 | nq95 | fq95 | bench R2 | timing |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IWM:iv_term | YES | R3 | lnrv | +5.96 | +9.81 | +13.14 | [+3.78,+8.64] | +3.04 | +3.23 | 60 | weak | R3 | er | +0.39 | -0.38 | +0.37 | [-1.90,+2.39] | -0.36 | +2.54 | -6 | no |
| DIA:iv_term | YES | R3 | lnrv | +4.65 | +6.68 | +8.45 | [+2.26,+7.06] | +1.66 | +3.23 | 60 | no | R3 | cross | -0.06 | +2.35 | +0.10 | [-1.61,+1.72] | -0.63 | +2.76 | -8 | no |
| SPX:charm | YES | R3 | lnrv | +4.14 | +3.40 | -3.77 | [+1.22,+8.09] | +0.08 | +3.23 | 60 | no | R3 | cext | -1.94 | -2.27 | +0.55 | [-3.85,-0.23] | -0.89 | +2.94 | -4 | weak |
| QQQ:vanna | YES | R3 | lnrv | +3.81 | +4.19 | -8.30 | [+0.32,+7.36] | +0.59 | +3.23 | 60 | no | R3 | er | -0.62 | -1.46 | +0.45 | [-3.17,+1.85] | -0.14 | +2.54 | -6 | no |
| SPX:gamma | YES | R3 | lnrv | +3.43 | +3.06 | +0.84 | [+0.23,+7.00] | +0.02 | +3.23 | 60 | no | R3 | cext | -1.54 | +2.29 | +2.68 | [-3.54,+0.08] | -1.26 | +2.94 | -4 | no |
| QQQ:zdte_share | weak | R3 | lnrv | +3.01 | +6.07 | +14.48 | [+1.29,+4.39] | +0.98 | +3.23 | 60 | no | R3 | cross | -0.89 | -1.50 | -4.63 | [-2.74,+0.99] | -0.18 | +2.76 | -8 | no |
| NDX:gamma | weak | R3 | lnrv | +2.69 | +11.13 | +16.66 | [-0.30,+6.08] | +0.34 | +3.23 | 60 | no | R3 | er | -1.44 | -5.97 | -6.95 | [-3.76,+1.79] | -0.61 | +2.54 | -6 | no |
| SPY:zdte_share | weak | R3 | lnrv | +2.68 | +6.17 | +12.93 | [+1.23,+4.16] | +1.09 | +3.23 | 60 | no | R3 | cross | -0.18 | +0.65 | -3.71 | [-1.98,+1.37] | -0.34 | +2.76 | -8 | no |
| cal:dow | no | R3 | lnrv | +2.57 | +1.54 | +6.24 | [+0.92,+4.03] | +3.23 | +3.23 | 60 | no | R3 | er | -0.01 | -0.16 | +0.72 | [-2.71,+2.39] | +0.30 | +2.54 | -6 | no |
| NDX:flip | weak | R3 | lnrv | +2.29 | +2.73 | +9.28 | [+0.59,+4.16] | -0.04 | +3.23 | 60 | no | R3 | cext | +0.08 | +2.32 | +2.44 | [-1.69,+1.83] | +2.94 | +2.94 | -4 | no |
| IWM:iv_level | weak | R3 | lnrng | +2.21 | +1.13 | +1.42 | [-4.19,+6.21] | +5.47 | +5.47 | 34 | no | R3 | cross | -1.47 | -1.61 | -2.69 | [-3.15,+0.35] | +0.99 | +2.76 | -8 | no |
| QQQ:gamma | weak | R3 | lnrv | +2.18 | +7.27 | +14.51 | [-1.95,+6.63] | +0.29 | +3.23 | 60 | no | R3 | cext | -0.66 | +0.17 | +2.61 | [-2.67,+1.15] | -1.08 | +2.94 | -4 | no |
| QQQ:flip | weak | R3 | lnrv | +1.89 | +2.86 | +3.71 | [-0.08,+3.50] | +0.49 | +3.23 | 60 | no | R3 | er | -0.14 | +0.01 | -0.18 | [-1.52,+1.25] | -0.33 | +2.54 | -6 | no |
| ALL4:flip | weak | R3 | lnrv | +1.87 | +1.41 | +2.46 | [-0.06,+3.89] | +0.06 | +3.23 | 60 | weak | R3 | er | +0.75 | +1.95 | +3.01 | [-2.19,+3.62] | +0.05 | +2.54 | -6 | no |

## 3. Compact answer: input family x session, best ticker (YES / weak / no) for RANGE and for DAY TYPE
| input family | asia | london | pre | nyam | nypm | nyam2 |
|---|---|---|---|---|---|---|
| absflip_wall | R:YES +3.9 (SPX) / T:weak +1.2 | R:YES +2.4 (QQQ) / T:weak +1.5 | R:YES +3.2 (IWM) / T:weak +0.3 | R:weak +1.1 (DIA) / T:weak +0.1 | R:weak +0.9 (QQQ) / T:weak +0.5 | R:weak +1.7 (IWM) / T:weak +0.5 |
| charm | R:weak +0.5 (SPX) / T:weak +0.0 | R:weak +2.1 (SPY) / T:weak +0.3 | R:weak +1.9 (SPX) / T:no -0.1 | R:YES +3.0 (SPX) / T:weak +0.1 | R:weak +0.6 (QQQ) / T:weak +0.1 | R:YES +4.1 (SPX) / T:no -0.1 |
| dow | R:no +1.8 (cal) / T:no +1.7 | R:no -0.0 (cal) / T:no +0.8 | R:YES +3.0 (cal) / T:no -1.4 | R:YES +2.4 (cal) / T:no -1.4 | R:weak +4.0 (cal) / T:no -0.9 | R:no +2.6 (cal) / T:no -0.0 |
| flip | R:YES +8.2 (SPY) / T:weak +0.4 | R:YES +7.8 (ALL4) / T:weak +1.4 | R:YES +8.4 (ALL4) / T:no -0.1 | R:YES +4.6 (SPY) / T:weak +0.8 | R:YES +4.7 (QQQ) / T:weak +0.4 | R:weak +2.3 (NDX) / T:weak +1.2 |
| gamma | R:YES +5.8 (SPX) / T:weak +0.4 | R:YES +5.3 (SPY) / T:weak +0.9 | R:YES +4.5 (SPX) / T:no -0.5 | R:YES +3.8 (SPY) / T:no -0.6 | R:weak +3.8 (SPX) / T:weak +1.8 | R:YES +3.4 (SPX) / T:no -0.7 |
| gamma_chg | - | - | - | - | R:weak +1.9 (SPX) / T:weak +0.5 | R:weak +0.4 (NDX) / T:weak +0.3 |
| impmove_vs_actual | - | - | - | - | R:weak +3.4 (QQQ) / T:no -0.1 | R:weak +0.7 (IWM) / T:weak +0.5 |
| iv_level | R:YES +8.0 (QQQ) / T:weak +0.7 | R:YES +5.8 (SPX) / T:no -0.6 | R:YES +7.4 (SPX) / T:no -0.2 | R:YES +4.4 (QQQ) / T:weak +1.1 | R:weak +2.9 (SPX) / T:weak +1.4 | R:weak +2.2 (IWM) / T:no -0.2 |
| iv_minus_rv | R:weak +3.1 (SPX) / T:no +0.6 | R:YES +2.9 (SPX) / T:no -0.2 | R:weak +2.8 (SPX) / T:no -0.3 | R:weak +1.7 (SPX) / T:no -0.5 | R:weak +0.2 (SPX) / T:no +0.4 | R:no -0.3 (SPX) / T:no -0.6 |
| iv_term | R:YES +4.3 (IWM) / T:YES +4.9 | R:YES +5.0 (DIA) / T:weak +0.2 | R:YES +15.8 (IWM) / T:no -0.5 | R:YES +9.8 (IWM) / T:no -0.2 | R:YES +5.1 (IWM) / T:YES +2.4 | R:YES +6.0 (IWM) / T:weak +0.4 |
| month_end | R:no -0.2 (cal) / T:no -0.2 | R:weak +0.4 (cal) / T:no -0.3 | R:no -0.3 (cal) / T:no -0.2 | R:no -0.3 (cal) / T:no -0.5 | R:no -0.0 (cal) / T:weak +0.0 | R:no -0.1 (cal) / T:weak +0.3 |
| net_premium | R:YES +2.5 (QQQ) / T:weak +0.1 | R:YES +2.0 (SPX) / T:weak +0.8 | R:weak +1.8 (SPX) / T:weak +0.3 | R:weak +0.0 (NDX) / T:weak +0.3 | R:no -0.0 (QQQ) / T:weak +0.2 | R:weak +1.3 (QQQ) / T:weak +0.9 |
| opex_day | R:no -0.0 (cal) / T:no +0.1 | R:no -0.2 (cal) / T:no -0.5 | R:weak +0.3 (cal) / T:no -0.0 | R:no -0.2 (cal) / T:weak +0.1 | R:no -0.1 (cal) / T:no -0.3 | R:no -0.1 (cal) / T:no -0.2 |
| opex_week | R:no -0.3 (cal) / T:no -0.1 | R:no -0.4 (cal) / T:no -0.4 | R:no +0.0 (cal) / T:weak +1.0 | R:no -0.3 (cal) / T:no +0.0 | R:no -0.1 (cal) / T:no +0.0 | R:no -0.0 (cal) / T:weak +0.6 |
| quarter_end | R:no -0.1 (cal) / T:no -0.5 | R:no -0.1 (cal) / T:no -0.1 | R:no -0.1 (cal) / T:no -0.0 | R:no -0.2 (cal) / T:weak +0.4 | R:no -0.1 (cal) / T:weak +0.3 | R:no -0.3 (cal) / T:weak +1.1 |
| tide | R:YES +6.0 (mkt) / T:no +0.2 | R:YES +5.1 (mkt) / T:weak +0.2 | R:weak +2.3 (mkt) / T:weak +0.5 | R:weak +0.5 (mkt) / T:no -0.5 | R:weak +2.9 (mkt) / T:no -0.5 | R:no -0.5 (mkt) / T:no -0.7 |
| vanna | R:weak +1.5 (NDX) / T:weak +0.5 | R:weak +1.9 (QQQ) / T:weak +0.2 | R:weak +0.6 (NDX) / T:weak +0.1 | R:weak +1.6 (SPY) / T:no -1.0 | R:weak +0.7 (DIA) / T:weak +1.4 | R:YES +3.8 (QQQ) / T:no -0.1 |
| walls | R:YES +3.9 (QQQ) / T:weak +2.3 | R:YES +3.8 (SPY) / T:no -0.7 | R:weak +2.3 (SPX) / T:no -0.9 | R:weak +1.4 (QQQ) / T:no -1.6 | R:YES +4.3 (QQQ) / T:weak +0.7 | R:weak +1.6 (QQQ) / T:weak +0.7 |
| zdte_share | R:weak +0.0 (SPX) / T:weak +1.4 | R:weak +0.6 (SPY) / T:weak +0.0 | R:weak +0.4 (QQQ) / T:weak +1.7 | R:weak +0.4 (QQQ) / T:weak +0.1 | R:weak +1.8 (QQQ) / T:weak +0.5 | R:weak +3.0 (QQQ) / T:no -0.2 |

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
