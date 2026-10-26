# REPORT SW31 - pair-internal regime states at daily horizon (1-min ST/HM trend state, daily EMA20/5d/20d) as multi-day sleeves (D00 H5 M1-M3)

**Verdict: LEAD. FOUND 0, LEAD 3, INSURANCE 0.** 77 selected cells (+3 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.35; best pair-window standalone Sharpe +1.41.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: state sampled at the RTH-open signal row (1-min ST ATR120/2.0 trend sign; 1-min HM 20/55 sign; sign of close minus daily EMA20; prior 5-day return sign; prior 20-day return sign), with or against, hold N = 1/2/3/5 label days, exit at the RTH open of day d+N or the 15:55 of day d+N-1 (multi-day exits through the 1-min simulator, rolls via the back-adjusted series). N=1,2 have no +-25% neighbours (integers round back) so plateau is only testable for N 3 and 5.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 80 cells per instrument = 5 states x 2 directions x 4 holds x 2 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      80 |         70 |        17 |               2.243 |                2 |         10 |            0 |
| CL    |      80 |         70 |        20 |               1.318 |                2 |         10 |            0 |
| ES    |      80 |         70 |        18 |               1.945 |                2 |         10 |            0 |
| GC    |      80 |         70 |        17 |               1.974 |                2 |         10 |            0 |
| NQ    |      80 |         70 |        22 |               1.951 |                2 |         10 |            0 |
| RTY   |      80 |         70 |        17 |               1.652 |                2 |         10 |            0 |
| YM    |      80 |         70 |        21 |               1.428 |                2 |         10 |            0 |
| ZN    |      80 |         70 |         7 |               0.872 |                2 |          7 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   18 |           12.32  |              22 |      0.04  |                       1.056 |            0.851 |           1.119 |    0.14  |       1.585 |                1.956 |
| NQ    |     200 |                   22 |           14.31  |              25 |      0.03  |                       1.284 |            0.933 |           1.217 |    0.01  |       1.572 |                2.173 |
| RTY   |     200 |                   17 |           13.345 |              22 |      0.15  |                       0.729 |            0.903 |           1.168 |    0.875 |       1.652 |                2.198 |
| YM    |     200 |                   21 |           13.21  |              21 |      0.005 |                       0.967 |            0.904 |           1.178 |    0.36  |       1.428 |                2.059 |
| GC    |     200 |                   17 |           13.02  |              21 |      0.145 |                       1.112 |            0.876 |           1.188 |    0.11  |       1.974 |                2.016 |
| CL    |     200 |                   20 |           11.995 |              19 |      0     |                       0.941 |            0.843 |           1.082 |    0.3   |       1.318 |                2.069 |
| ZN    |     200 |                    7 |            4.13  |              10 |      0.145 |                       0.435 |            0.638 |           1.002 |    0.88  |       0.827 |                1.607 |
| BTC   |     200 |                   17 |           14.22  |              27 |      0.26  |                       1.066 |            0.92  |           1.233 |    0.225 |       2.243 |                2.153 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | state ret20d dir=with hold=1d exit=open | 258 | 2 | 1.58 | -0.55 | 0.73 | -0.95 / 1.17 | 0.24 / -0.60 / -0.04 | 0.04 | -0.40 | 0.95 | -0.08 | 0.00 | 414 | NO |
| ES 2 | state ema20d dir=with hold=5d exit=close | 103 | 2 | 1.19 | -0.18 | 0.34 | -1.25 / 1.06 | 0.19 / -0.55 / -0.21 | -0.01 | -0.05 | 0.75 | -0.17 | 0.00 | 165 | NO |
| ES 3 | state ema20d dir=with hold=1d exit=open | 258 | 2 | 1.13 | -0.79 | 0.59 | -0.51 / 1.32 | 0.17 / -0.59 / 0.03 | 0.01 | -0.27 | 0.92 | -0.12 | 0.00 | 414 | NO |
| ES 4 | state ret5d dir=with hold=1d exit=open | 258 | 2 | 1.12 | -0.52 | 0.14 | -1.77 / 1.05 | 0.18 / -0.51 / -0.33 | -0.05 | 0.04 | 0.67 | -0.18 | 0.00 | 413 | NO |
| ES 5 | state st1m dir=with hold=1d exit=open | 258 | 2 | 1.06 | 0.11 | -0.16 | -1.77 / 1.21 | 0.22 / -0.41 / -0.72 | -0.10 | -0.50 | 0.46 | -0.29 | 0.00 | 414 | NO |
| ES 6 | state ret20d dir=with hold=2d exit=open | 172 | 2 | 1.05 | -0.03 | -0.07 | -1.72 / 1.27 | 0.22 / -0.80 / -0.37 | -0.06 | 0.46 | 0.49 | -0.24 | 0.00 | 277 | NO |
| ES 7 | state hm1m dir=with hold=1d exit=open | 258 | 2 | 0.90 | -0.13 | 0.11 | -1.60 / 1.30 | 0.14 / -0.12 / -0.32 | -0.02 | -0.38 | 0.63 | -0.14 | 0.00 | 414 | NO |
| ES 8 | state hm1m dir=with hold=2d exit=close | 253 | 2 | 0.86 | -0.34 | 0.22 | -0.70 / 1.51 | 0.12 / -0.53 / 0.02 | -0.01 | -0.32 | 0.70 | -0.17 | 0.00 | 407 | NO |
| ES 9 | state ret20d dir=with hold=5d exit=close | 103 | 2 | 0.83 | -0.26 | 0.42 | -0.36 / 1.48 | 0.10 / -0.22 / -0.12 | -0.00 | -0.21 | 0.83 | -0.17 | 0.00 | 165 | NO |
| ES 10 | state st1m dir=against hold=3d exit=close | 170 | 2 | 0.83 | 0.59 | 0.19 | -0.86 / 1.46 | 0.16 / -0.01 / -0.36 | 0.00 | 0.52 | 0.62 | -0.17 | 0.00 | 273 | NO |
| NQ 1 | state ema20d dir=with hold=1d exit=open | 258 | 2 | 1.57 | -0.58 | 0.84 | -0.17 / 1.66 | 0.25 / -0.43 / -0.00 | 0.09 | -0.44 | 0.94 | -0.09 | 0.00 | 414 | NO |
| NQ 2 | state ret20d dir=with hold=1d exit=open | 258 | 2 | 1.42 | -0.29 | 0.68 | -0.35 / 1.30 | 0.20 / -0.75 / -0.01 | 0.02 | -0.62 | 0.90 | -0.17 | 0.00 | 414 | NO |
| NQ 3 | state hm1m dir=with hold=2d exit=close | 253 | 2 | 1.40 | -0.31 | 0.60 | -0.61 / 1.62 | 0.22 / -0.67 / 0.24 | 0.09 | -0.26 | 0.79 | -0.09 | 0.00 | 407 | NO |
| NQ 4 | state ema20d dir=with hold=2d exit=open | 172 | 2 | 1.39 | -0.03 | 0.68 | -0.22 / 1.42 | 0.28 / -0.48 / 0.20 | 0.15 | -0.52 | 0.92 | -0.06 | 0.00 | 277 | NO |
| NQ 5 | state st1m dir=with hold=3d exit=open | 129 | 2 | 1.32 | 0.42 | 0.99 | 0.57 / 1.21 | 0.22 / -0.00 / 0.15 | 0.17 | -0.15 | 0.95 | -0.02 | 1.00 | 207 | NO |
| NQ 6 | state ema20d dir=with hold=5d exit=close | 103 | 2 | 1.25 | 0.01 | 0.35 | -0.87 / 1.64 | 0.19 / -0.74 / -0.08 | -0.00 | -0.01 | 0.78 | -0.19 | 0.00 | 165 | NO |
| NQ 7 | state st1m dir=with hold=1d exit=open | 258 | 2 | 1.23 | -0.13 | 0.54 | -0.37 / 1.36 | 0.18 / -0.40 / -0.07 | 0.04 | -0.42 | 0.77 | -0.15 | 0.00 | 414 | NO |
| NQ 8 | state ret20d dir=with hold=2d exit=open | 172 | 2 | 1.20 | 0.16 | 0.13 | -1.05 / 1.59 | 0.23 / -0.61 / -0.51 | -0.05 | 0.37 | 0.61 | -0.28 | 0.00 | 277 | NO |
| NQ 9 | state hm1m dir=with hold=3d exit=open | 129 | 2 | 1.12 | 0.15 | 0.55 | -0.33 / 1.42 | 0.21 / -0.49 / 0.21 | 0.10 | -0.07 | 0.86 | -0.09 | 0.00 | 207 | NO |
| NQ 10 | state hm1m dir=with hold=1d exit=open | 258 | 2 | 0.95 | -0.12 | 0.33 | -0.88 / 1.53 | 0.14 / -0.23 / -0.17 | 0.02 | -0.51 | 0.73 | -0.13 | 0.00 | 414 | NO |
| RTY 1 | state st1m dir=with hold=5d exit=close | 103 | 2 | 1.65 | 0.26 | 0.71 | -0.97 / 1.50 | 0.34 / -0.69 / 0.02 | 0.12 | -0.43 | 0.92 | -0.05 | 0.00 | 165 | NO |
| RTY 2 | state hm1m dir=with hold=5d exit=close | 103 | 2 | 1.25 | 0.19 | 1.19 | 1.12 / 1.08 | 0.21 / -0.04 / 0.29 | 0.19 | -0.44 | 0.99 | 0.02 | 0.00 | 165 | NO |
| RTY 3 | state ret20d dir=with hold=3d exit=open | 129 | 2 | 0.88 | -0.04 | 0.47 | -0.33 / 1.06 | 0.12 / -0.41 / -0.02 | 0.01 | -0.26 | 0.80 | -0.15 | 0.00 | 207 | NO |
| RTY 4 | state hm1m dir=with hold=3d exit=open | 129 | 2 | 0.62 | 0.22 | 0.49 | 0.22 / 1.40 | 0.07 / -0.11 / 0.11 | 0.04 | -0.57 | 0.87 | -0.12 | 0.00 | 207 | NO |
| RTY 5 | state ret20d dir=against hold=3d exit=close | 170 | 2 | 0.60 | 0.02 | 0.74 | 0.79 / 1.26 | 0.11 / 0.39 / 0.21 | 0.15 | 0.11 | 0.93 | -0.03 | 0.00 | 273 | LEAD |
| RTY 6 | state ema20d dir=against hold=2d exit=close | 253 | 2 | 0.50 | 0.34 | 0.67 | 0.74 / 1.13 | 0.07 / 0.36 / 0.15 | 0.10 | 0.40 | 0.92 | -0.06 | 0.00 | 407 | NO |
| RTY 7 | state hm1m dir=against hold=3d exit=close | 170 | 2 | 0.48 | 0.79 | -0.09 | -1.10 / 1.45 | 0.06 / 0.49 / -0.58 | -0.05 | -0.14 | 0.50 | -0.24 | 0.00 | 273 | NO |
| RTY 8 | state hm1m dir=with hold=2d exit=open | 172 | 2 | 0.45 | -0.33 | 0.21 | -0.08 / 1.83 | 0.07 / -0.35 / 0.09 | 0.01 | -0.62 | 0.66 | -0.16 | 0.00 | 276 | NO |
| RTY 9 | state st1m dir=with hold=2d exit=close | 253 | 2 | 0.44 | 0.38 | -0.14 | -1.03 / 1.28 | 0.06 / -0.59 / -0.25 | -0.10 | -0.08 | 0.58 | -0.27 | 0.00 | 407 | NO |
| RTY 10 | state st1m dir=with hold=3d exit=open | 129 | 2 | 0.42 | 0.59 | 0.60 | 0.96 / 1.51 | -0.00 / 0.05 / 0.22 | 0.03 | 0.09 | 0.82 | -0.12 | 0.00 | 207 | NO |
| YM 1 | state ema20d dir=with hold=1d exit=open | 258 | 2 | 1.43 | -0.30 | 0.57 | -0.91 / 1.48 | 0.23 / -0.26 / -0.35 | 0.03 | -0.30 | 0.89 | -0.12 | 0.00 | 414 | NO |
| YM 2 | state st1m dir=against hold=1d exit=close | 497 | 2 | 1.33 | -0.59 | 0.98 | 0.25 / 1.31 | 0.21 / 0.03 / 0.06 | 0.12 | -0.23 | 0.98 | -0.01 | 0.00 | 800 | NO |
| YM 3 | state ret20d dir=with hold=1d exit=open | 258 | 2 | 1.31 | -0.32 | 0.56 | -1.02 / 1.31 | 0.22 / -0.38 / -0.15 | 0.05 | -0.21 | 0.91 | -0.08 | 0.00 | 414 | NO |
| YM 4 | state ret5d dir=with hold=1d exit=open | 258 | 2 | 1.17 | -0.78 | 0.60 | -0.44 / 1.40 | 0.16 / -0.23 / -0.18 | 0.02 | 0.38 | 0.91 | -0.12 | 0.00 | 414 | NO |
| YM 5 | state hm1m dir=with hold=2d exit=open | 172 | 2 | 0.99 | 0.43 | 0.38 | -0.52 / 1.29 | 0.12 / -0.50 / -0.20 | -0.04 | 0.02 | 0.72 | -0.22 | 0.00 | 277 | NO |
| YM 6 | state st1m dir=against hold=1d exit=open | 258 | 2 | 0.77 | -0.39 | 0.71 | 0.65 / 1.33 | 0.11 / -0.15 / 0.57 | 0.14 | -0.11 | 0.92 | -0.04 | 0.00 | 414 | NO |
| YM 7 | state ema20d dir=with hold=2d exit=close | 253 | 2 | 0.76 | -0.57 | -0.21 | -1.50 / 1.44 | 0.11 / -0.51 / -0.46 | -0.11 | -0.52 | 0.37 | -0.30 | 0.00 | 407 | NO |
| YM 8 | state ema20d dir=with hold=1d exit=close | 497 | 2 | 0.66 | -0.99 | -0.27 | -1.22 / 1.15 | 0.10 / -0.32 / -0.70 | -0.16 | -0.03 | 0.42 | -0.36 | 0.00 | 800 | NO |
| YM 9 | state st1m dir=against hold=2d exit=close | 253 | 2 | 0.64 | -0.34 | 1.13 | 2.24 / 1.55 | 0.11 / 0.51 / 0.50 | 0.23 | -0.11 | 0.97 | 0.07 | 0.00 | 407 | LEAD(gate3-7 fail: plateau ) |
| YM 10 | state ret5d dir=with hold=3d exit=open | 129 | 2 | 0.60 | -0.49 | 0.38 | 0.11 / 1.36 | 0.05 / -0.53 / 0.13 | -0.01 | 0.02 | 0.80 | -0.18 | 0.00 | 207 | NO |
| GC 1 | state hm1m dir=against hold=1d exit=close | 498 | 2 | 1.97 | -0.57 | 0.77 | 0.24 / 1.28 | 0.27 / -0.63 / 0.10 | 0.09 | -0.11 | 0.94 | -0.22 | 0.00 | 800 | NO |
| GC 2 | state hm1m dir=against hold=2d exit=close | 252 | 2 | 1.52 | -0.28 | -0.51 | -1.74 / 1.43 | 0.24 / -1.60 / -1.08 | -0.35 | 0.15 | 0.16 | -0.75 | 0.00 | 404 | NO |
| GC 3 | state st1m dir=against hold=2d exit=open | 172 | 2 | 1.30 | -0.03 | 0.32 | -0.17 / 1.37 | 0.24 / -0.55 / 0.09 | 0.08 | -0.27 | 0.72 | -0.35 | 0.00 | 276 | NO |
| GC 4 | state ema20d dir=against hold=2d exit=close | 252 | 2 | 1.14 | -0.14 | -0.14 | -0.87 / 1.43 | 0.15 / -0.53 / -0.74 | -0.16 | -0.17 | 0.42 | -0.47 | 0.00 | 404 | NO |
| GC 5 | state st1m dir=against hold=2d exit=close | 252 | 2 | 1.11 | -0.29 | -0.62 | -1.69 / 1.27 | 0.15 / -1.00 / -1.54 | -0.40 | 0.27 | 0.18 | -0.81 | 0.00 | 404 | NO |
| GC 6 | state ema20d dir=against hold=2d exit=open | 172 | 2 | 0.96 | -0.49 | 0.04 | -0.52 / 1.59 | 0.15 / -1.18 / -0.27 | -0.13 | -0.64 | 0.51 | -0.50 | 0.00 | 276 | NO |
| GC 7 | state hm1m dir=against hold=3d exit=open | 129 | 2 | 0.95 | 0.51 | -0.60 | -1.62 / 1.44 | 0.18 / -2.18 / -0.82 | -0.43 | 0.25 | 0.13 | -0.79 | 0.00 | 207 | NO |
| GC 8 | state ret5d dir=against hold=1d exit=open | 258 | 2 | 0.77 | -0.43 | -0.37 | -1.04 / 1.18 | 0.11 / -1.23 / -0.70 | -0.28 | -0.21 | 0.36 | -0.67 | 0.00 | 414 | NO |
| GC 9 | state ema20d dir=against hold=3d exit=close | 170 | 2 | 0.70 | -0.43 | -0.37 | -1.05 / 1.40 | 0.09 / -0.98 / -0.99 | -0.30 | 0.11 | 0.32 | -0.63 | 0.00 | 273 | NO |
| GC 10 | state ema20d dir=against hold=1d exit=open | 258 | 2 | 0.70 | 0.11 | -0.14 | -0.63 / 1.23 | 0.13 / -0.85 / -0.54 | -0.16 | -0.02 | 0.42 | -0.54 | 0.00 | 414 | NO |
| CL 1 | state st1m dir=against hold=2d exit=open | 172 | 2 | 1.32 | 0.06 | 0.65 | 0.23 / 1.41 | 0.23 / 0.04 / -0.25 | 0.07 | -0.17 | 0.91 | -0.19 | 0.00 | 277 | NO |
| CL 2 | state ret5d dir=against hold=5d exit=close | 103 | 2 | 1.15 | 0.14 | 0.73 | 0.49 / 1.19 | 0.15 / -0.16 / 0.21 | 0.11 | -0.08 | 0.90 | -0.11 | 0.00 | 165 | NO |
| CL 3 | state ret5d dir=against hold=2d exit=close | 252 | 2 | 1.05 | -0.18 | 0.09 | -1.13 / 1.31 | 0.19 / 0.14 / -0.72 | -0.04 | 0.44 | 0.57 | -0.23 | 0.00 | 405 | NO |
| CL 4 | state ret20d dir=against hold=1d exit=open | 258 | 2 | 0.95 | -0.43 | -0.57 | -1.89 / 1.19 | 0.13 / -0.07 / -1.27 | -0.26 | 0.32 | 0.21 | -0.50 | 0.00 | 415 | NO |
| CL 5 | state ret5d dir=against hold=1d exit=open | 257 | 2 | 0.87 | 0.03 | 1.23 | 1.71 / 1.46 | 0.16 / 0.46 / 0.80 | 0.32 | -0.06 | 0.99 | 0.08 | 0.00 | 413 | LEAD |
| CL 6 | state hm1m dir=against hold=2d exit=open | 172 | 2 | 0.84 | -0.33 | 0.66 | 0.59 / 1.47 | 0.11 / 0.06 / 0.03 | 0.07 | -0.12 | 0.85 | -0.18 | 0.00 | 277 | NO |
| CL 7 | state hm1m dir=with hold=3d exit=open | 129 | 2 | 0.82 | -0.30 | -0.36 | -1.47 / 1.54 | 0.13 / 0.02 / -1.07 | -0.18 | 0.02 | 0.35 | -0.45 | 0.00 | 207 | NO |
| CL 8 | state ema20d dir=against hold=3d exit=close | 170 | 2 | 0.82 | -0.05 | 0.31 | -0.07 / 1.50 | 0.10 / 0.27 / -0.43 | -0.02 | 0.31 | 0.71 | -0.25 | 0.00 | 273 | NO |
| CL 9 | state hm1m dir=with hold=3d exit=close | 170 | 2 | 0.81 | -0.21 | -0.43 | -1.36 / 1.40 | 0.15 / -0.28 / -1.09 | -0.21 | -0.01 | 0.35 | -0.47 | 0.00 | 273 | NO |
| CL 10 | state st1m dir=against hold=1d exit=open | 258 | 2 | 0.78 | 0.38 | 0.19 | -0.34 / 1.25 | 0.16 / -0.10 / -0.29 | -0.00 | -0.03 | 0.59 | -0.22 | 0.00 | 415 | NO |
| ZN 1 | state ret5d dir=against hold=3d exit=close | 169 | 2 | 0.83 | -0.45 | 0.30 | -0.82 / 0.97 | 0.14 / -0.18 / -0.12 | -0.05 | 0.05 | 0.88 | -0.13 | 0.00 | 271 | NO |
| ZN 2 | state st1m dir=with hold=3d exit=close | 170 | 2 | 0.63 | -0.50 | 0.15 | -0.87 / 0.72 | 0.12 / -0.17 / -0.21 | -0.08 | -0.28 | 0.91 | -0.16 | 0.50 | 273 | NO |
| ZN 3 | state ret5d dir=against hold=2d exit=close | 253 | 2 | 0.61 | -0.53 | 0.28 | -0.44 / 0.47 | 0.07 / -0.29 / 0.07 | -0.11 | -0.12 | 0.98 | -0.14 | 0.00 | 405 | NO |
| ZN 4 | state ret5d dir=against hold=3d exit=open | 129 | 2 | 0.46 | -0.31 | 0.10 | -0.76 / 0.87 | 0.05 / 0.04 / -0.21 | -0.09 | -0.19 | 0.84 | -0.19 | 0.00 | 208 | NO |
| ZN 5 | state ret5d dir=against hold=1d exit=open | 258 | 2 | 0.21 | -0.66 | -0.18 | -1.26 / -0.16 | 0.02 / -0.43 / 0.10 | -0.22 | -0.29 | 0.95 | -0.19 | 0.00 | 413 | NO |
| ZN 6 | state ret5d dir=against hold=2d exit=open | 172 | 2 | 0.17 | -0.48 | -0.14 | -0.94 / 0.54 | 0.04 / 0.13 / -0.23 | -0.12 | -0.05 | 0.80 | -0.18 | 0.00 | 277 | NO |
| ZN 7 | state st1m dir=against hold=5d exit=close | 103 | 2 | 0.14 | -0.23 | 0.09 | -0.05 / 0.92 | -0.02 / 0.06 / -0.03 | -0.07 | -0.11 | 0.80 | -0.18 | 0.00 | 166 | NO |
| ZN 8 (diag) | state hm1m dir=with hold=3d exit=close | 170 | 1 | 0.87 | -0.41 | 0.64 | 0.19 / 0.78 | 0.13 / -0.18 / 0.18 | 0.00 | -0.05 | 1.00 | -0.08 | 0.00 | 273 | diag |
| ZN 9 (diag) | state st1m dir=against hold=3d exit=open | 129 | 1 | 0.49 | -0.55 | -0.14 | -1.79 / 0.74 | 0.04 / 0.16 / -0.40 | -0.13 | 0.16 | 0.74 | -0.22 | 0.00 | 207 | diag |
| ZN 10 (diag) | state hm1m dir=with hold=5d exit=close | 103 | 1 | 0.39 | -0.24 | 0.20 | -0.24 / 1.17 | 0.05 / -0.18 / -0.01 | -0.05 | 0.19 | 0.86 | -0.16 | 0.50 | 166 | diag |
| BTC 1 | state hm1m dir=with hold=3d exit=open | 128 | 2 | 2.24 | -0.39 | 1.41 | 0.33 / 1.35 | 0.43 / 0.35 / -0.13 | 0.30 | 0.36 | 1.00 | 0.11 | 0.00 | 202 | NO |
| BTC 2 | state st1m dir=against hold=5d exit=close | 102 | 2 | 1.84 | 0.15 | 1.09 | -0.08 / 1.37 | 0.35 / -0.09 / -0.20 | 0.17 | -0.20 | 0.97 | -0.02 | 0.00 | 164 | NO |
| BTC 3 | state ret5d dir=against hold=2d exit=open | 172 | 2 | 1.01 | 0.79 | 0.21 | -0.81 / 1.64 | 0.16 / -0.43 / -0.01 | 0.03 | 0.06 | 0.68 | -0.17 | 0.00 | 273 | NO |
| BTC 4 | state ema20d dir=with hold=5d exit=close | 102 | 2 | 0.99 | -1.92 | 0.78 | 0.58 / 1.43 | 0.16 / -0.08 / 0.06 | 0.11 | -0.09 | 0.96 | -0.09 | 0.00 | 164 | NO |
| BTC 5 | state ret20d dir=with hold=3d exit=open | 128 | 2 | 0.96 | -0.41 | 0.18 | -0.79 / 1.54 | 0.15 / -0.59 / -0.24 | -0.04 | 0.29 | 0.58 | -0.24 | 0.00 | 202 | NO |
| BTC 6 | state ret5d dir=against hold=3d exit=close | 168 | 2 | 0.75 | 0.79 | 0.29 | -0.21 / 1.69 | 0.10 / -0.33 / 0.11 | 0.03 | -0.15 | 0.73 | -0.17 | 0.00 | 267 | NO |
| BTC 7 | state ret20d dir=with hold=5d exit=close | 102 | 2 | 0.74 | -0.97 | 0.46 | 0.17 / 1.17 | 0.13 / -0.09 / -0.23 | 0.04 | 0.19 | 0.81 | -0.17 | 0.50 | 164 | NO |
| BTC 8 | state ret20d dir=against hold=1d exit=close | 488 | 2 | 0.73 | -0.80 | 0.51 | 0.06 / 1.07 | 0.07 / 0.10 / -0.04 | 0.01 | 0.29 | 0.88 | -0.15 | 0.00 | 764 | NO |
| BTC 9 | state ema20d dir=with hold=3d exit=open | 128 | 2 | 0.73 | -0.87 | 0.74 | 0.82 / 1.87 | 0.10 / -0.12 / 0.00 | 0.06 | 0.24 | 0.89 | -0.13 | 0.50 | 202 | NO |
| BTC 10 | state ema20d dir=with hold=1d exit=open | 257 | 2 | 0.68 | -1.65 | 0.69 | 0.73 / 1.46 | 0.17 / -0.02 / 0.10 | 0.13 | -0.33 | 0.92 | -0.03 | 0.00 | 403 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 77 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 3 / 3 / 3 |
| all-in uplift @20% > 0 (all scored) | 48 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 71 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 15 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 3 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC state hm1m dir=with hold=3d exit=open | clean | 2.17 | 4.27 | -100967 | -81930 | 397368 | -157020 | 4.97 | 35.2 | 1.89 | -81280 | 265614 | -91721 |
| BTC state hm1m dir=with hold=3d exit=open | H1 | 2.18 | 3.24 | -178495 | -140871 | 235495 | -219332 | 2.79 | 25.0 | 3.18 | -71459 | 168347 | -73237 |
| BTC state hm1m dir=with hold=3d exit=open | H2 | -1.48 | -1.67 | -169998 | -129817 | 598640 | -222037 | -0.75 | 55.6 | 2.36 | -83059 | 211484 | -93536 |
| BTC state hm1m dir=with hold=3d exit=open | all | 1.41 | 2.24 | -143796 | -108756 | 598640 | -222037 | 3.65 | 37.5 | 2.21 | -81069 | 265614 | -93536 |
| CL state ret5d dir=against hold=1d exit=open | clean | 0.82 | 1.38 | -109865 | -89277 | 350547 | -161109 | 2.13 | 47.6 | 1.62 | -81366 | 263590 | -87897 |
| CL state ret5d dir=against hold=1d exit=open | H1 | 2.77 | 5.75 | -77979 | -64487 | 92350 | -92350 | 5.84 | 35.7 | 3.28 | -69328 | 143797 | -78305 |
| CL state ret5d dir=against hold=1d exit=open | H2 | 1.75 | 4.07 | -198522 | -180737 | 454396 | -223452 | 3.58 | 44.4 | 3.28 | -107147 | 251517 | -110112 |
| CL state ret5d dir=against hold=1d exit=open | all | 1.23 | 2.59 | -159846 | -126864 | 454396 | -223452 | 6.41 | 45.2 | 2.25 | -86968 | 263590 | -110112 |
| ES state ret20d dir=with hold=1d exit=open | clean | 1.61 | 4.35 | -73847 | -62489 | 218584 | -104173 | 6.67 | 37.1 | 1.70 | -80005 | 211820 | -88986 |
| ES state ret20d dir=with hold=1d exit=open | H1 | -2.37 | -2.56 | -133255 | -126768 | 546149 | -133474 | -0.95 | 53.6 | 2.23 | -89648 | 176710 | -90170 |
| ES state ret20d dir=with hold=1d exit=open | H2 | 0.30 | 0.45 | -96237 | -81240 | 249756 | -110750 | 0.30 | 47.2 | 2.45 | -84892 | 222924 | -88166 |
| ES state ret20d dir=with hold=1d exit=open | all | 0.73 | 1.36 | -99749 | -82336 | 600195 | -133474 | 1.69 | 42.3 | 1.96 | -83892 | 222924 | -90170 |
| GC state hm1m dir=against hold=1d exit=close | clean | 1.96 | 4.03 | -93557 | -80628 | 387260 | -108227 | 4.59 | 47.6 | 1.73 | -89459 | 265192 | -97109 |
| GC state hm1m dir=against hold=1d exit=close | H1 | -0.18 | -0.26 | -353177 | -289129 | 824034 | -533696 | -0.14 | 53.6 | 2.20 | -111256 | 215358 | -117959 |
| GC state hm1m dir=against hold=1d exit=close | H2 | 0.53 | 0.76 | -407926 | -326778 | 1029016 | -410692 | 0.48 | 38.9 | 2.59 | -93554 | 189794 | -107840 |
| GC state hm1m dir=against hold=1d exit=close | all | 0.77 | 1.15 | -290385 | -205856 | 1029016 | -533696 | 2.09 | 46.4 | 2.02 | -97005 | 265192 | -117959 |
| NQ state st1m dir=with hold=3d exit=open | clean | 1.31 | 2.12 | -121783 | -96441 | 211529 | -194802 | 5.59 | 40.0 | 1.68 | -83425 | 261013 | -96385 |
| NQ state st1m dir=with hold=3d exit=open | H1 | -0.33 | -0.44 | -141009 | -134078 | 317303 | -157999 | -0.28 | 46.4 | 2.83 | -63451 | 168262 | -75125 |
| NQ state st1m dir=with hold=3d exit=open | H2 | 1.14 | 1.64 | -195230 | -158266 | 255675 | -228239 | 1.91 | 33.3 | 2.64 | -95079 | 199007 | -105852 |
| NQ state st1m dir=with hold=3d exit=open | all | 0.99 | 1.48 | -155421 | -122103 | 385919 | -228239 | 4.10 | 39.9 | 2.07 | -85464 | 261013 | -105852 |
| RTY state hm1m dir=with hold=5d exit=close | clean | 1.21 | 2.26 | -104465 | -87289 | 615838 | -120081 | 1.79 | 47.6 | 1.67 | -80200 | 247419 | -85712 |
| RTY state hm1m dir=with hold=5d exit=close | H1 | 0.05 | 0.07 | -117451 | -100727 | 216118 | -120403 | 0.05 | 53.6 | 2.78 | -69848 | 130584 | -71158 |
| RTY state hm1m dir=with hold=5d exit=close | H2 | 2.05 | 3.92 | -83001 | -71436 | 221325 | -87240 | 2.49 | 36.1 | 2.78 | -86140 | 223537 | -89755 |
| RTY state hm1m dir=with hold=5d exit=close | all | 1.19 | 2.11 | -105437 | -88010 | 615838 | -120403 | 2.70 | 46.4 | 2.09 | -80910 | 247419 | -89755 |
| YM state st1m dir=against hold=2d exit=close | clean | 0.55 | 0.82 | -127008 | -102377 | 845692 | -224003 | 0.60 | 46.7 | 1.57 | -82343 | 303074 | -89884 |
| YM state st1m dir=against hold=2d exit=close | H1 | 1.82 | 3.34 | -71157 | -70377 | 184031 | -73335 | 2.05 | 39.3 | 3.34 | -66634 | 146825 | -78420 |
| YM state st1m dir=against hold=2d exit=close | H2 | 2.54 | 4.99 | -84521 | -68624 | 166136 | -108622 | 4.15 | 33.3 | 2.98 | -84142 | 198548 | -84878 |
| YM state st1m dir=against hold=2d exit=close | all | 1.13 | 1.80 | -113466 | -92526 | 845692 | -224003 | 1.86 | 42.9 | 2.14 | -82307 | 303074 | -89884 |
| ZN state ret5d dir=against hold=3d exit=close | clean | 0.77 | 1.24 | -111591 | -93681 | 333711 | -163200 | 2.09 | 45.7 | 1.60 | -87129 | 263387 | -105390 |
| ZN state ret5d dir=against hold=3d exit=close | H1 | -1.44 | -1.70 | -76427 | -68573 | 240509 | -78634 | -0.82 | 53.6 | 2.65 | -83641 | 158859 | -83709 |
| ZN state ret5d dir=against hold=3d exit=close | H2 | -0.46 | -0.70 | -74813 | -65025 | 299940 | -77779 | -0.35 | 55.6 | 2.37 | -88425 | 217861 | -89514 |
| ZN state ret5d dir=against hold=3d exit=close | all | 0.30 | 0.47 | -105952 | -88208 | 575874 | -163200 | 0.69 | 48.8 | 1.94 | -87871 | 263387 | -105390 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES state ret20d dir=with hold=1d exit=open | -18.9 | 10.7 | 18.7 | 40.4 | 12.2 / 26.3 | 5.8 / 6.7 | NO |
| NQ state st1m dir=with hold=3d exit=open | -12.7 | -34.0 | 11.2 | 24.4 | -0.6 / 13.6 | 36.1 / 40.1 | NO |
| RTY state hm1m dir=with hold=5d exit=close | -11.8 | 11.9 | 23.1 | 39.3 | 18.2 / 23.1 | 39.4 / 41.0 | NO |
| YM state st1m dir=against hold=2d exit=close | -12.8 | 11.8 | 21.9 | 17.7 | 11.1 / 19.8 | 29.7 / 46.5 | NO |
| GC state hm1m dir=against hold=1d exit=close | -6.5 | -103.5 | -16.7 | 9.5 | 0.5 / 8.9 | -114.5 / -68.9 | NO |
| CL state ret5d dir=against hold=1d exit=open | 1.9 | -20.1 | 10.8 | 21.3 | 15.4 / 21.1 | 30.0 / 40.7 | NO |
| ZN state ret5d dir=against hold=3d exit=close | -25.6 | -16.7 | 10.0 | 28.1 | -17.6 / 7.2 | 18.2 / 18.3 | NO |
| BTC state hm1m dir=with hold=3d exit=open | -6.1 | -1.6 | 17.8 | 36.3 | 12.0 / 22.8 | -7.1 / 7.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 state ret20d dir=with hold=1d exit=open | negative pre-2023 | 1343 | -48.0 | -77.3 | -63.1 | 29.4 | -0.34 / -0.55 / -0.45 | 455.0 / 425.7 |
| ES 2 state ema20d dir=with hold=5d exit=close | negative pre-2023 | 535 | -54.2 | -83.5 | -69.3 | 29.4 | -0.12 / -0.18 / -0.15 | 993.3 / 964.0 |
| ES 3 state ema20d dir=with hold=1d exit=open | negative pre-2023 | 1343 | -81.1 | -110.4 | -96.2 | 29.4 | -0.58 / -0.79 / -0.69 | 345.9 / 316.6 |
| ES 4 state ret5d dir=with hold=1d exit=open | negative pre-2023 | 1341 | -42.5 | -71.9 | -57.7 | 29.4 | -0.31 / -0.52 / -0.41 | 350.1 / 320.7 |
| ES 5 state st1m dir=with hold=1d exit=open | positive pre-2023 | 1343 | 43.7 | 14.4 | 28.6 | 29.4 | 0.34 / 0.11 / 0.22 | 227.9 / 198.5 |
| ES 6 state ret20d dir=with hold=2d exit=open | gross-positive, cost-negative pre-2023 | 896 | 22.9 | -6.5 | 7.8 | 29.4 | 0.11 / -0.03 / 0.04 | 453.0 / 423.6 |
| ES 7 state hm1m dir=with hold=1d exit=open | gross-positive, cost-negative pre-2023 | 1343 | 11.8 | -17.5 | -3.3 | 29.4 | 0.09 / -0.13 / -0.02 | 294.7 / 265.3 |
| ES 8 state hm1m dir=with hold=2d exit=close | negative pre-2023 | 1320 | -30.6 | -60.0 | -45.8 | 29.4 | -0.17 / -0.34 / -0.26 | 249.9 / 220.5 |
| ES 9 state ret20d dir=with hold=5d exit=close | negative pre-2023 | 534 | -90.5 | -119.9 | -105.6 | 29.4 | -0.20 / -0.26 / -0.23 | 710.8 / 681.4 |
| ES 10 state st1m dir=against hold=3d exit=close | positive pre-2023 | 885 | 189.9 | 160.5 | 174.7 | 29.4 | 0.70 / 0.59 / 0.65 | 444.7 / 415.3 |
| NQ 1 state ema20d dir=with hold=1d exit=open | negative pre-2023 | 1343 | -109.9 | -124.2 | -115.7 | 14.4 | -0.51 / -0.58 / -0.54 | 675.4 / 661.0 |
| NQ 2 state ret20d dir=with hold=1d exit=open | negative pre-2023 | 1342 | -46.0 | -60.3 | -51.8 | 14.4 | -0.22 / -0.29 / -0.25 | 664.2 / 649.8 |
| NQ 3 state hm1m dir=with hold=2d exit=close | negative pre-2023 | 1320 | -68.3 | -82.7 | -74.1 | 14.4 | -0.26 / -0.31 / -0.28 | 781.6 / 767.2 |
| NQ 4 state ema20d dir=with hold=2d exit=open | gross-positive, cost-negative pre-2023 | 897 | 3.0 | -11.4 | -2.8 | 14.4 | 0.01 / -0.03 / -0.01 | 1077.8 / 1063.5 |
| NQ 5 state st1m dir=with hold=3d exit=open | positive pre-2023 | 673 | 224.3 | 209.9 | 218.5 | 14.4 | 0.45 / 0.42 / 0.44 | 1197.5 / 1183.2 |
| NQ 6 state ema20d dir=with hold=5d exit=close | positive pre-2023 | 535 | 20.0 | 5.7 | 14.2 | 14.4 | 0.03 / 0.01 / 0.02 | 1828.9 / 1814.5 |
| NQ 7 state st1m dir=with hold=1d exit=open | negative pre-2023 | 1343 | -13.1 | -27.5 | -18.9 | 14.4 | -0.06 / -0.13 / -0.09 | 510.9 / 496.6 |
| NQ 8 state ret20d dir=with hold=2d exit=open | positive pre-2023 | 896 | 67.3 | 53.0 | 61.6 | 14.4 | 0.20 / 0.16 / 0.18 | 875.3 / 860.9 |
| NQ 9 state hm1m dir=with hold=3d exit=open | positive pre-2023 | 673 | 78.9 | 64.6 | 73.1 | 14.4 | 0.18 / 0.15 / 0.17 | 1113.9 / 1099.5 |
| NQ 10 state hm1m dir=with hold=1d exit=open | negative pre-2023 | 1343 | -12.8 | -27.2 | -18.6 | 14.4 | -0.06 / -0.12 / -0.08 | 501.4 / 487.0 |
| RTY 1 state st1m dir=with hold=5d exit=close | positive pre-2023 | 306 | 113.3 | 98.9 | 101.2 | 14.4 | 0.30 / 0.26 / 0.27 | 692.2 / 677.8 |
| RTY 2 state hm1m dir=with hold=5d exit=close | positive pre-2023 | 306 | 84.5 | 70.1 | 72.4 | 14.4 | 0.23 / 0.19 / 0.19 | 513.1 / 498.7 |
| RTY 3 state ret20d dir=with hold=3d exit=open | gross-positive, cost-negative pre-2023 | 384 | 1.8 | -12.6 | -10.3 | 14.4 | 0.01 / -0.04 / -0.04 | 304.3 / 290.0 |
| RTY 4 state hm1m dir=with hold=3d exit=open | positive pre-2023 | 384 | 76.0 | 61.6 | 63.9 | 14.4 | 0.27 / 0.22 / 0.23 | 229.5 / 215.2 |
| RTY 5 state ret20d dir=against hold=3d exit=close | positive pre-2023 | 505 | 17.6 | 3.2 | 5.5 | 14.4 | 0.09 / 0.02 / 0.03 | 184.5 / 170.1 |
| RTY 6 state ema20d dir=against hold=2d exit=close | positive pre-2023 | 754 | 62.7 | 48.3 | 50.6 | 14.4 | 0.44 / 0.34 / 0.35 | 113.1 / 98.7 |
| RTY 7 state hm1m dir=against hold=3d exit=close | positive pre-2023 | 505 | 196.8 | 182.4 | 184.6 | 14.4 | 0.85 / 0.79 / 0.80 | 142.8 / 128.4 |
| RTY 8 state hm1m dir=with hold=2d exit=open | negative pre-2023 | 513 | -51.5 | -65.9 | -63.6 | 14.4 | -0.26 / -0.33 / -0.32 | 103.1 / 88.8 |
| RTY 9 state st1m dir=with hold=2d exit=close | positive pre-2023 | 754 | 72.8 | 58.4 | 60.7 | 14.4 | 0.48 / 0.38 / 0.40 | 76.8 / 62.5 |
| RTY 10 state st1m dir=with hold=3d exit=open | positive pre-2023 | 384 | 180.7 | 166.4 | 168.6 | 14.4 | 0.64 / 0.59 / 0.60 | 158.3 / 143.9 |
| YM 1 state ema20d dir=with hold=1d exit=open | negative pre-2023 | 1346 | -18.8 | -33.1 | -27.4 | 14.4 | -0.17 / -0.30 / -0.25 | 277.6 / 263.2 |
| YM 2 state st1m dir=against hold=1d exit=close | negative pre-2023 | 2609 | -21.9 | -36.2 | -30.5 | 14.4 | -0.36 / -0.59 / -0.50 | 179.6 / 165.3 |
| YM 3 state ret20d dir=with hold=1d exit=open | negative pre-2023 | 1345 | -22.3 | -36.7 | -30.9 | 14.4 | -0.20 / -0.32 / -0.27 | 256.1 / 241.7 |
| YM 4 state ret5d dir=with hold=1d exit=open | negative pre-2023 | 1345 | -76.4 | -90.8 | -85.0 | 14.4 | -0.66 / -0.78 / -0.73 | 233.7 / 219.3 |
| YM 5 state hm1m dir=with hold=2d exit=open | positive pre-2023 | 898 | 98.7 | 84.3 | 90.1 | 14.4 | 0.50 / 0.43 / 0.46 | 285.1 / 270.7 |
| YM 6 state st1m dir=against hold=1d exit=open | negative pre-2023 | 1346 | -28.8 | -43.2 | -37.5 | 14.4 | -0.26 / -0.39 / -0.34 | 115.2 / 100.9 |
| YM 7 state ema20d dir=with hold=2d exit=close | negative pre-2023 | 1324 | -66.7 | -81.0 | -75.3 | 14.4 | -0.47 / -0.57 / -0.53 | 125.2 / 110.8 |
| YM 8 state ema20d dir=with hold=1d exit=close | negative pre-2023 | 2609 | -44.5 | -58.8 | -53.1 | 14.4 | -0.75 / -0.99 / -0.90 | 54.9 / 40.5 |
| YM 9 state st1m dir=against hold=2d exit=close | negative pre-2023 | 1324 | -32.9 | -47.3 | -41.6 | 14.4 | -0.24 / -0.34 / -0.30 | 128.4 / 114.0 |
| YM 10 state ret5d dir=with hold=3d exit=open | negative pre-2023 | 674 | -122.9 | -137.3 | -131.6 | 14.4 | -0.44 / -0.49 / -0.47 | 194.7 / 180.3 |
| GC 1 state hm1m dir=against hold=1d exit=close | negative pre-2023 | 2604 | -15.6 | -39.9 | -30.2 | 24.4 | -0.22 / -0.57 / -0.43 | 243.8 / 219.4 |
| GC 2 state hm1m dir=against hold=2d exit=close | negative pre-2023 | 1315 | -22.7 | -47.1 | -37.3 | 24.4 | -0.14 / -0.28 / -0.22 | 482.4 / 458.1 |
| GC 3 state st1m dir=against hold=2d exit=open | gross-positive, cost-negative pre-2023 | 897 | 18.8 | -5.6 | 4.2 | 24.4 | 0.09 / -0.03 / 0.02 | 531.3 / 506.9 |
| GC 4 state ema20d dir=against hold=2d exit=close | gross-positive, cost-negative pre-2023 | 1315 | 3.5 | -20.8 | -11.0 | 24.4 | 0.02 / -0.14 / -0.07 | 311.2 / 286.8 |
| GC 5 state st1m dir=against hold=2d exit=close | negative pre-2023 | 1315 | -21.5 | -45.8 | -36.1 | 24.4 | -0.14 / -0.29 / -0.23 | 341.5 / 317.2 |
| GC 6 state ema20d dir=against hold=2d exit=open | negative pre-2023 | 897 | -81.9 | -106.2 | -96.4 | 24.4 | -0.38 / -0.49 / -0.44 | 446.0 / 421.7 |
| GC 7 state hm1m dir=against hold=3d exit=open | positive pre-2023 | 673 | 189.2 | 164.8 | 174.6 | 24.4 | 0.59 / 0.51 / 0.54 | 570.5 / 546.2 |
| GC 8 state ret5d dir=against hold=1d exit=open | negative pre-2023 | 1341 | -29.1 | -53.5 | -43.7 | 24.4 | -0.24 / -0.43 / -0.36 | 191.7 / 167.4 |
| GC 9 state ema20d dir=against hold=3d exit=close | negative pre-2023 | 884 | -78.9 | -103.2 | -93.5 | 24.4 | -0.33 / -0.43 / -0.39 | 339.6 / 315.3 |
| GC 10 state ema20d dir=against hold=1d exit=open | positive pre-2023 | 1342 | 38.3 | 13.9 | 23.7 | 24.4 | 0.31 / 0.11 / 0.19 | 173.6 / 149.2 |
| CL 1 state st1m dir=against hold=2d exit=open | positive pre-2023 | 896 | 39.7 | 15.3 | 17.9 | 24.4 | 0.16 / 0.06 / 0.07 | 292.1 / 267.7 |
| CL 2 state ret5d dir=against hold=5d exit=close | positive pre-2023 | 534 | 86.3 | 61.9 | 64.5 | 24.4 | 0.20 / 0.14 / 0.15 | 474.7 / 450.3 |
| CL 3 state ret5d dir=against hold=2d exit=close | negative pre-2023 | 1319 | -6.1 | -30.4 | -27.8 | 24.4 | -0.03 / -0.18 / -0.16 | 223.5 / 199.1 |
| CL 4 state ret20d dir=against hold=1d exit=open | negative pre-2023 | 1344 | -32.5 | -56.8 | -54.2 | 24.4 | -0.24 / -0.43 / -0.41 | 147.2 / 122.8 |
| CL 5 state ret5d dir=against hold=1d exit=open | positive pre-2023 | 1343 | 27.3 | 3.0 | 5.6 | 24.4 | 0.21 / 0.03 / 0.05 | 123.5 / 99.1 |
| CL 6 state hm1m dir=against hold=2d exit=open | negative pre-2023 | 896 | -54.4 | -78.8 | -76.2 | 24.4 | -0.23 / -0.33 / -0.32 | 191.4 / 167.0 |
| CL 7 state hm1m dir=with hold=3d exit=open | negative pre-2023 | 673 | -73.9 | -98.3 | -95.6 | 24.4 | -0.23 / -0.30 / -0.29 | 291.9 / 267.5 |
| CL 8 state ema20d dir=against hold=3d exit=close | gross-positive, cost-negative pre-2023 | 883 | 10.0 | -14.4 | -11.8 | 24.4 | 0.04 / -0.05 / -0.04 | 210.1 / 185.7 |
| CL 9 state hm1m dir=with hold=3d exit=close | negative pre-2023 | 883 | -33.0 | -57.3 | -54.7 | 24.4 | -0.12 / -0.21 / -0.20 | 172.9 / 148.5 |
| CL 10 state st1m dir=against hold=1d exit=open | positive pre-2023 | 1344 | 72.3 | 48.0 | 50.6 | 24.4 | 0.57 / 0.38 / 0.40 | 121.7 / 97.3 |
| ZN 1 state ret5d dir=against hold=3d exit=close | gross-positive, cost-negative pre-2023 | 886 | 4.6 | -31.0 | -36.2 | 35.6 | 0.07 / -0.45 / -0.52 | 90.1 / 54.4 |
| ZN 2 state st1m dir=with hold=3d exit=close | gross-positive, cost-negative pre-2023 | 887 | 2.1 | -33.5 | -38.6 | 35.6 | 0.03 / -0.50 / -0.58 | 79.6 / 44.0 |
| ZN 3 state ret5d dir=against hold=2d exit=close | gross-positive, cost-negative pre-2023 | 1320 | 11.5 | -24.1 | -29.2 | 35.6 | 0.26 / -0.53 / -0.65 | 63.7 / 28.1 |
| ZN 4 state ret5d dir=against hold=3d exit=open | gross-positive, cost-negative pre-2023 | 673 | 8.0 | -27.6 | -32.7 | 35.6 | 0.09 / -0.31 / -0.36 | 73.3 / 37.7 |
| ZN 5 state ret5d dir=against hold=1d exit=open | gross-positive, cost-negative pre-2023 | 1344 | 11.6 | -24.0 | -29.1 | 35.6 | 0.32 / -0.66 / -0.80 | 42.5 / 6.8 |
| ZN 6 state ret5d dir=against hold=2d exit=open | gross-positive, cost-negative pre-2023 | 897 | 6.2 | -29.4 | -34.5 | 35.6 | 0.10 / -0.48 / -0.57 | 44.5 / 8.9 |
| ZN 7 state st1m dir=against hold=5d exit=close | gross-positive, cost-negative pre-2023 | 538 | 7.7 | -27.9 | -33.0 | 35.6 | 0.06 / -0.23 / -0.27 | 53.9 / 18.2 |
| ZN 8 (diag) state hm1m dir=with hold=3d exit=close | gross-positive, cost-negative pre-2023 | 887 | 6.3 | -29.3 | -34.5 | 35.6 | 0.09 / -0.41 / -0.49 | 97.1 / 61.4 |
| ZN 9 (diag) state st1m dir=against hold=3d exit=open | negative pre-2023 | 675 | -12.8 | -48.4 | -53.6 | 35.6 | -0.14 / -0.55 / -0.61 | 83.0 / 47.4 |
| ZN 10 (diag) state hm1m dir=with hold=5d exit=close | gross-positive, cost-negative pre-2023 | 538 | 6.6 | -29.0 | -34.2 | 35.6 | 0.05 / -0.24 / -0.28 | 83.9 / 48.3 |
| BTC 1 state hm1m dir=with hold=3d exit=open | negative pre-2023 | 96 | -440.9 | -495.2 | -462.8 | 54.4 | -0.34 / -0.39 / -0.36 | 4618.8 / 4564.4 |
| BTC 2 state st1m dir=against hold=5d exit=close | positive pre-2023 | 77 | 297.1 | 242.7 | 275.2 | 54.4 | 0.18 / 0.15 / 0.17 | 5995.6 / 5941.2 |
| BTC 3 state ret5d dir=against hold=2d exit=open | positive pre-2023 | 128 | 770.1 | 715.8 | 748.2 | 54.4 | 0.85 / 0.79 / 0.82 | 1358.3 / 1303.9 |
| BTC 4 state ema20d dir=with hold=5d exit=close | negative pre-2023 | 77 | -3228.9 | -3283.3 | -3250.8 | 54.4 | -1.89 / -1.92 / -1.90 | 2942.6 / 2888.3 |
| BTC 5 state ret20d dir=with hold=3d exit=open | negative pre-2023 | 96 | -427.1 | -481.4 | -449.0 | 54.4 | -0.36 / -0.41 / -0.38 | 2081.6 / 2027.3 |
| BTC 6 state ret5d dir=against hold=3d exit=close | positive pre-2023 | 127 | 853.9 | 799.6 | 832.0 | 54.4 | 0.84 / 0.79 / 0.82 | 1142.1 / 1087.8 |
| BTC 7 state ret20d dir=with hold=5d exit=close | negative pre-2023 | 77 | -1729.9 | -1784.2 | -1751.8 | 54.4 | -0.94 / -0.97 / -0.95 | 2148.5 / 2094.2 |
| BTC 8 state ret20d dir=against hold=1d exit=close | negative pre-2023 | 367 | -93.6 | -148.0 | -115.5 | 54.4 | -0.50 / -0.80 / -0.62 | 439.2 / 384.9 |
| BTC 9 state ema20d dir=with hold=3d exit=open | negative pre-2023 | 96 | -1111.7 | -1166.1 | -1133.6 | 54.4 | -0.83 / -0.87 / -0.85 | 1584.0 / 1529.6 |
| BTC 10 state ema20d dir=with hold=1d exit=open | negative pre-2023 | 191 | -787.7 | -842.1 | -809.5 | 54.4 | -1.54 / -1.65 / -1.58 | 717.5 / 663.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 17 cells pass the clean rule against a replicate mean of 14.2 (p(count) = 0.26, p(top) = 0.23); CL: 20 cells pass the clean rule against a replicate mean of 12.0 (p(count) = 0.00, p(top) = 0.30); ES: 18 cells pass the clean rule against a replicate mean of 12.3 (p(count) = 0.04, p(top) = 0.14); GC: 17 cells pass the clean rule against a replicate mean of 13.0 (p(count) = 0.14, p(top) = 0.11); NQ: 22 cells pass the clean rule against a replicate mean of 14.3 (p(count) = 0.03, p(top) = 0.01); RTY: 17 cells pass the clean rule against a replicate mean of 13.3 (p(count) = 0.15, p(top) = 0.88); YM: 21 cells pass the clean rule against a replicate mean of 13.2 (p(count) = 0.01, p(top) = 0.36); ZN: 7 cells pass the clean rule against a replicate mean of 4.1 (p(count) = 0.14, p(top) = 0.88).
- Of 77 selected cells, 3 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.35 (CL state ret5d dir=against hold=1d exit=open); bootstrap lower bound > 0 for 4 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 15; gate_add PASS at some share: 3 (cell-share pairs).
- Gate-3 cell RTY state ret20d dir=against hold=3d exit=close: uplift +0.11/+0.39/+0.21, boot lo -0.03, plateau 0.00, 2x-slip +0.15, wd corr +0.11, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM state st1m dir=against hold=2d exit=close: uplift +0.11/+0.51/+0.50, boot lo +0.07, plateau 0.00, 2x-slip +0.23, wd corr -0.11, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell CL state ret5d dir=against hold=1d exit=open: uplift +0.16/+0.46/+0.80, boot lo +0.08, plateau 0.00, 2x-slip +0.32, wd corr -0.06, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 39, 'positive pre-2023': 24, 'gross-positive, cost-negative pre-2023': 14}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_31.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw31/ (`SW31_CO_all_selected_scored.csv`).

DONE SW31
