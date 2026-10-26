# REPORT SW36 - simple weekly-horizon rules, non-ML twin of SW34 (D00/D08/D12 H6)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 75 selected cells (+5 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.00.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Signal sign of the prior 5-day / 20-day return or close vs daily EMA20, gated by VIX percentile all / hi >= 0.67 / lo <= 0.33, with/against, hold 2/3/5 label days from the RTH open; entries first label day of the week or any flat day. MINTR 60.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 108 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     108 |         42 |        13 |               1.547 |                2 |         10 |            0 |
| CL    |     108 |         42 |        11 |               1.483 |                2 |         10 |            0 |
| ES    |     108 |         42 |        10 |               1.417 |                2 |         10 |            0 |
| GC    |     108 |         42 |        10 |               2.091 |                2 |         10 |            0 |
| NQ    |     108 |         42 |         8 |               1.395 |                2 |          8 |            2 |
| RTY   |     108 |         42 |         8 |               1.274 |                2 |          8 |            2 |
| YM    |     108 |         42 |        11 |               1.237 |                2 |         10 |            0 |
| ZN    |     108 |         42 |         9 |               1.098 |                2 |          9 |            1 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   10 |           14.735 |              23 |      0.945 |                       0.84  |            0.927 |           1.217 |    0.635 |       1.417 |                2.113 |
| NQ    |     200 |                    8 |           15.73  |              28 |      0.99  |                       0.941 |            0.998 |           1.24  |    0.635 |       1.395 |                2.206 |
| RTY   |     200 |                    8 |           15.655 |              27 |      0.995 |                       0.806 |            1.009 |           1.247 |    0.905 |       1.231 |                2.237 |
| YM    |     200 |                   11 |           15.23  |              27 |      0.93  |                       0.628 |            0.961 |           1.215 |    0.965 |       0.977 |                2.223 |
| GC    |     200 |                   10 |           14.86  |              26 |      0.93  |                       0.728 |            0.944 |           1.221 |    0.895 |       2.091 |                2.142 |
| CL    |     200 |                   11 |           14.46  |              22 |      0.875 |                       0.572 |            0.953 |           1.236 |    0.99  |       1.037 |                2.211 |
| ZN    |     200 |                    9 |            8.51  |              16 |      0.49  |                       0.488 |            0.713 |           0.976 |    0.965 |       0.704 |                1.784 |
| BTC   |     200 |                   13 |           15.045 |              24 |      0.765 |                       1.062 |            0.971 |           1.258 |    0.325 |       1.547 |                2.238 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | ema vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 1.42 | 0.08 | 0.73 | -0.57 / 1.30 | 0.24 / -0.25 / -0.30 | 0.05 | 0.05 | 0.93 | -0.11 | 0.00 | 138 | NO |
| ES 2 | r20 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 1.24 | 0.27 | 0.76 | -0.20 / 1.46 | 0.19 / 0.03 / -0.29 | 0.05 | -0.05 | 0.95 | -0.11 | 0.00 | 138 | NO |
| ES 3 | r5 vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 1.16 | -0.57 | 0.51 | 0.01 / 1.45 | 0.18 / -0.67 / 0.10 | 0.03 | 0.44 | 0.80 | -0.19 | 0.50 | 121 | NO |
| ES 4 | r20 vix-all0.0 dir=with hold=2d entries=day | 172 | 2 | 1.05 | -0.03 | -0.07 | -1.72 / 1.55 | 0.22 / -0.80 / -0.37 | -0.06 | 0.46 | 0.40 | -0.24 | 0.00 | 277 | NO |
| ES 5 | r5 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.99 | 0.28 | 0.10 | -1.64 / 1.52 | 0.18 / -0.33 / -0.50 | -0.05 | 0.04 | 0.75 | -0.21 | 0.00 | 138 | NO |
| ES 6 | ema vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.93 | -0.16 | -0.09 | -1.05 / 1.72 | 0.15 / -0.74 / -0.36 | -0.10 | 0.45 | 0.51 | -0.32 | 0.00 | 122 | NO |
| ES 7 | r5 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.90 | 0.55 | 0.42 | -0.31 / 1.45 | 0.16 / 0.18 / -0.20 | 0.07 | -0.23 | 0.77 | -0.11 | 0.50 | 105 | NO |
| ES 8 | ema vix-all0.0 dir=with hold=2d entries=day | 172 | 2 | 0.39 | -0.45 | -0.21 | -1.07 / 1.23 | 0.07 / -0.91 / -0.07 | -0.11 | 0.30 | 0.34 | -0.29 | 0.00 | 277 | NO |
| ES 9 | r5 vix-all0.0 dir=against hold=3d entries=day | 129 | 2 | 0.20 | 0.46 | 0.43 | 0.78 / 1.46 | 0.01 / 0.57 / 0.13 | 0.08 | 0.21 | 0.82 | -0.10 | 0.00 | 207 | NO |
| ES 10 | r20 vix-hi0.67 dir=with hold=2d entries=day | 69 | 2 | 0.12 | -0.15 | -0.01 | -0.24 / 1.40 | 0.05 / -0.06 / -0.26 | -0.03 | 0.51 | 0.58 | -0.19 | 0.00 | 105 | NO |
| NQ 1 | ema vix-all0.0 dir=with hold=2d entries=day | 172 | 2 | 1.39 | -0.03 | 0.68 | -0.22 / 1.40 | 0.28 / -0.48 / 0.20 | 0.15 | -0.52 | 0.91 | -0.06 | 0.00 | 277 | NO |
| NQ 2 | ema vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 1.38 | 0.09 | 0.70 | -0.26 / 1.42 | 0.22 / -0.10 / -0.29 | 0.06 | 0.15 | 0.85 | -0.14 | 0.00 | 138 | NO |
| NQ 3 | r20 vix-all0.0 dir=with hold=2d entries=day | 172 | 2 | 1.20 | 0.16 | 0.13 | -1.05 / 1.51 | 0.23 / -0.61 / -0.51 | -0.05 | 0.37 | 0.58 | -0.28 | 0.00 | 277 | NO |
| NQ 4 | r5 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 1.10 | 0.49 | 0.34 | -0.63 / 1.45 | 0.13 / 0.17 / -0.26 | 0.03 | -0.34 | 0.77 | -0.17 | 0.50 | 105 | NO |
| NQ 5 | ema vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.78 | 0.08 | -0.47 | -1.52 / 1.26 | 0.10 / -0.99 / -0.60 | -0.21 | 0.39 | 0.15 | -0.52 | 0.00 | 122 | NO |
| NQ 6 | r5 vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.72 | -0.29 | -0.52 | -1.66 / 1.59 | 0.10 / -1.14 / -0.64 | -0.24 | 0.39 | 0.19 | -0.53 | 0.00 | 121 | NO |
| NQ 7 | r5 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.66 | 0.11 | -0.01 | -0.98 / 1.71 | 0.11 / -0.47 / -0.44 | -0.09 | 0.23 | 0.47 | -0.29 | 0.00 | 138 | NO |
| NQ 8 | r20 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.30 | 0.07 | -0.26 | -1.08 / 1.49 | 0.03 / -0.27 / -0.33 | -0.10 | 0.15 | 0.37 | -0.28 | 0.00 | 138 | NO |
| NQ 9 (diag) | r5 vix-hi0.67 dir=against hold=2d entries=week | 42 | 1 | 1.18 | 0.65 | 0.60 | -0.24 / 1.43 | 0.13 / 0.13 / -0.30 | 0.03 | 0.44 | 0.85 | -0.16 | 1.00 | 61 S | diag |
| NQ 10 (diag) | r5 vix-lo0.33 dir=with hold=5d entries=week | 23 | 2 | 1.17 | -0.00 | -0.19 | -1.39 / 1.69 | 0.17 / -0.08 / -1.09 | -0.15 | -0.03 | 0.43 | -0.44 | 0.00 | 40 S | diag |
| RTY 1 | ema vix-all0.0 dir=against hold=2d entries=week | 105 | 2 | 1.23 | 0.68 | 1.00 | 0.57 / 1.27 | 0.16 / 0.52 / -0.26 | 0.10 | 0.27 | 0.99 | -0.06 | 0.00 | 168 | NO |
| RTY 2 | ema vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 1.04 | 0.10 | 0.65 | -0.05 / 1.79 | 0.18 / -0.16 / -0.01 | 0.08 | -0.07 | 0.90 | -0.09 | 0.50 | 122 | NO |
| RTY 3 | ema vix-all0.0 dir=against hold=3d entries=week | 104 | 2 | 1.03 | 0.72 | 0.41 | -0.75 / 1.27 | 0.16 / 0.22 / -0.47 | 0.02 | 0.34 | 0.85 | -0.15 | 0.50 | 167 | NO |
| RTY 4 | r20 vix-all0.0 dir=with hold=3d entries=day | 129 | 2 | 0.88 | -0.04 | 0.47 | -0.33 / 1.22 | 0.12 / -0.41 / -0.02 | 0.01 | -0.26 | 0.86 | -0.15 | 0.00 | 207 | NO |
| RTY 5 | r20 vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 0.86 | -0.20 | 0.94 | 1.02 / 1.54 | 0.14 / 0.40 / 0.13 | 0.15 | 0.14 | 0.92 | -0.01 | 0.50 | 122 | LEAD |
| RTY 6 | r5 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.76 | -0.15 | 0.19 | -0.82 / 1.60 | 0.09 / -0.03 / -0.37 | -0.03 | 0.11 | 0.66 | -0.20 | 0.00 | 138 | NO |
| RTY 7 | r5 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.47 | -0.01 | 0.47 | 0.47 / 1.39 | 0.07 / 0.12 / -0.04 | 0.05 | -0.30 | 0.82 | -0.12 | 0.00 | 105 | NO |
| RTY 8 | ema vix-all0.0 dir=against hold=2d entries=day | 172 | 2 | 0.16 | 0.34 | 0.13 | -0.03 / 1.72 | 0.01 / 0.13 / -0.12 | -0.02 | 0.61 | 0.59 | -0.17 | 0.00 | 276 | NO |
| RTY 9 (diag) | ema vix-all0.0 dir=against hold=5d entries=week | 52 | 2 | 1.27 | 0.51 | 0.77 | -0.41 / 1.54 | 0.27 / -0.00 / 0.01 | 0.17 | 0.34 | 0.94 | 0.01 | 0.50 | 84 S | diag |
| RTY 10 (diag) | ema vix-hi0.67 dir=against hold=2d entries=week | 42 | 1 | 1.08 | 0.77 | 0.87 | 0.47 / 1.56 | 0.11 / 0.38 / -0.15 | 0.07 | 0.45 | 0.92 | -0.08 | 1.00 | 61 S | diag |
| YM 1 | ema vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.98 | 0.47 | 0.80 | 0.36 / 1.28 | 0.14 / -0.20 / -0.03 | 0.06 | -0.21 | 0.92 | -0.10 | 0.00 | 138 | NO |
| YM 2 | r5 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 0.96 | 0.68 | 0.86 | 0.77 / 1.54 | 0.13 / -0.39 / 0.21 | 0.08 | -0.12 | 0.93 | -0.08 | 0.00 | 138 | NO |
| YM 3 | r5 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.79 | 0.31 | 0.87 | 0.99 / 1.17 | 0.14 / 0.39 / 0.01 | 0.14 | -0.35 | 0.97 | -0.05 | 0.50 | 105 | NO |
| YM 4 | ema vix-all0.0 dir=against hold=2d entries=week | 105 | 2 | 0.65 | 0.46 | 0.70 | 0.72 / 1.38 | 0.05 / 0.21 / 0.20 | 0.09 | 0.32 | 0.92 | -0.11 | 0.00 | 168 | NO |
| YM 5 | r5 vix-all0.0 dir=against hold=3d entries=week | 104 | 2 | 0.62 | 0.54 | 0.01 | -1.22 / 1.39 | 0.10 / 0.42 / -0.64 | -0.02 | -0.10 | 0.51 | -0.19 | 0.00 | 167 | NO |
| YM 6 | r5 vix-all0.0 dir=with hold=3d entries=day | 129 | 2 | 0.60 | -0.49 | 0.38 | 0.11 / 1.71 | 0.05 / -0.53 / 0.13 | -0.01 | 0.02 | 0.76 | -0.18 | 0.00 | 207 | NO |
| YM 7 | r20 vix-all0.0 dir=with hold=2d entries=day | 172 | 2 | 0.56 | -0.22 | -0.18 | -1.49 / 1.16 | 0.10 / -0.23 / -0.49 | -0.09 | 0.06 | 0.38 | -0.26 | 0.00 | 277 | NO |
| YM 8 | r5 vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.50 | -0.28 | 0.57 | 0.69 / 1.62 | 0.07 / 0.03 / -0.06 | 0.04 | 0.04 | 0.87 | -0.15 | 0.50 | 122 | NO |
| YM 9 | r20 vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 0.39 | 0.09 | 0.78 | 1.22 / 1.51 | 0.06 / 0.43 / 0.25 | 0.14 | 0.21 | 0.91 | -0.07 | 0.00 | 122 | NO |
| YM 10 | r20 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.23 | 0.28 | 0.28 | 0.34 / 1.45 | 0.01 / 0.00 / 0.03 | 0.01 | 0.29 | 0.71 | -0.16 | 0.00 | 105 | NO |
| GC 1 | r20 vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 2.09 | -0.33 | -0.04 | -1.36 / 1.19 | 0.33 / -1.52 / -0.55 | -0.15 | 0.48 | 0.60 | -0.46 | 0.00 | 122 | NO |
| GC 2 | ema vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 1.53 | -0.43 | -0.15 | -1.11 / 1.31 | 0.27 / -1.41 / -0.57 | -0.18 | 0.47 | 0.44 | -0.51 | 0.00 | 122 | NO |
| GC 3 | ema vix-all0.0 dir=against hold=2d entries=day | 172 | 2 | 0.96 | -0.49 | 0.04 | -0.52 / 1.58 | 0.15 / -1.18 / -0.27 | -0.13 | -0.64 | 0.48 | -0.50 | 0.00 | 276 | NO |
| GC 4 | ema vix-all0.0 dir=against hold=3d entries=day | 129 | 2 | 0.57 | 0.02 | -0.23 | -0.79 / 1.52 | 0.05 / -0.82 / -0.79 | -0.26 | 0.24 | 0.33 | -0.56 | 0.00 | 207 | NO |
| GC 5 | r20 vix-all0.0 dir=against hold=5d entries=day | 87 | 2 | 0.50 | 0.18 | -0.26 | -0.83 / 1.29 | 0.11 / -0.89 / -0.63 | -0.20 | 0.12 | 0.35 | -0.56 | 0.00 | 139 | NO |
| GC 6 | r20 vix-all0.0 dir=against hold=2d entries=week | 105 | 2 | 0.46 | 0.08 | 0.00 | -0.23 / 1.38 | 0.03 / -1.58 / -0.02 | -0.21 | 0.13 | 0.46 | -0.61 | 0.00 | 168 | NO |
| GC 7 | r5 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.45 | 0.18 | 0.27 | 0.14 / 1.43 | 0.04 / -0.49 / -0.02 | -0.04 | -0.46 | 0.62 | -0.29 | 0.00 | 104 | NO |
| GC 8 | r20 vix-all0.0 dir=against hold=3d entries=week | 105 | 2 | 0.34 | 0.33 | -0.43 | -0.98 / 1.42 | 0.04 / -1.38 / -0.67 | -0.33 | 0.22 | 0.22 | -0.70 | 0.00 | 168 | NO |
| GC 9 | r20 vix-hi0.67 dir=with hold=2d entries=day | 69 | 2 | 0.29 | -0.06 | -0.65 | -1.39 / 1.43 | 0.01 / 0.48 / -1.47 | -0.32 | 0.62 | 0.11 | -0.65 | 0.00 | 104 | NO |
| GC 10 | ema vix-all0.0 dir=with hold=5d entries=day | 87 | 2 | 0.08 | -0.01 | 0.20 | 0.36 / 1.88 | -0.07 / -0.10 / -0.08 | -0.06 | 0.01 | 0.55 | -0.38 | 0.00 | 139 | NO |
| CL 1 | r20 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 1.04 | -0.54 | -0.28 | -0.93 / 1.77 | 0.13 / -0.15 / -1.44 | -0.33 | 0.10 | 0.37 | -0.82 | 0.00 | 105 | NO |
| CL 2 | r5 vix-all0.0 dir=against hold=5d entries=day | 86 | 2 | 0.86 | -0.34 | 0.80 | 0.80 / 1.36 | 0.10 / 0.29 / 0.55 | 0.19 | -0.24 | 0.95 | -0.06 | 0.00 | 138 | LEAD |
| CL 3 | r5 vix-all0.0 dir=against hold=3d entries=day | 129 | 2 | 0.77 | 0.09 | 0.74 | 0.66 / 1.25 | 0.17 / 0.21 / 0.05 | 0.14 | 0.13 | 0.95 | -0.12 | 0.00 | 207 | NO |
| CL 4 | ema vix-all0.0 dir=with hold=2d entries=week | 105 | 2 | 0.55 | 0.04 | -0.48 | -1.26 / 1.44 | 0.05 / -0.23 / -1.07 | -0.27 | -0.02 | 0.27 | -0.57 | 0.00 | 168 | NO |
| CL 5 | r5 vix-all0.0 dir=against hold=2d entries=day | 172 | 2 | 0.55 | -0.31 | 0.29 | -0.09 / 1.14 | 0.14 / 0.12 / -0.31 | 0.02 | 0.52 | 0.76 | -0.19 | 0.00 | 276 | NO |
| CL 6 | r5 vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.50 | -0.39 | 0.43 | 0.63 / 1.41 | 0.04 / -0.42 / 0.05 | -0.01 | -0.48 | 0.74 | -0.24 | 0.50 | 121 | NO |
| CL 7 | r20 vix-all0.0 dir=against hold=3d entries=day | 129 | 2 | 0.44 | -0.36 | -0.59 | -1.41 / 1.76 | 0.05 / 0.19 / -1.49 | -0.33 | 0.29 | 0.17 | -0.63 | 0.00 | 207 | NO |
| CL 8 | ema vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.39 | -0.33 | -0.17 | -0.46 / 1.29 | 0.00 / -0.12 / -1.08 | -0.31 | 0.10 | 0.47 | -0.78 | 0.00 | 105 | NO |
| CL 9 | r5 vix-all0.0 dir=against hold=3d entries=week | 105 | 2 | 0.33 | 0.15 | 0.03 | -0.28 / 1.61 | 0.08 / -0.08 / -0.31 | -0.04 | 0.11 | 0.59 | -0.30 | 0.00 | 168 | NO |
| CL 10 | r20 vix-all0.0 dir=against hold=5d entries=day | 86 | 2 | 0.30 | -0.74 | -0.51 | -1.32 / 1.32 | 0.02 / 0.19 / -1.07 | -0.23 | 0.01 | 0.11 | -0.47 | 0.00 | 139 | NO |
| ZN 1 | r5 vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 0.70 | -0.80 | 0.33 | -0.41 / 0.63 | 0.10 / -0.20 / -0.07 | -0.05 | -0.06 | 0.92 | -0.13 | 1.00 | 122 | NO |
| ZN 2 | r20 vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 0.64 | -0.29 | 0.77 | 0.70 / 0.86 | 0.12 / 0.03 / 0.04 | 0.02 | 0.08 | 0.99 | -0.07 | 0.00 | 121 | NO |
| ZN 3 | r5 vix-all0.0 dir=against hold=3d entries=week | 104 | 2 | 0.63 | 0.01 | 0.08 | -1.40 / 1.34 | 0.10 / -0.19 / -0.15 | -0.06 | -0.14 | 0.74 | -0.16 | 1.00 | 167 | NO |
| ZN 4 | r5 vix-all0.0 dir=against hold=2d entries=week | 104 | 2 | 0.59 | -0.05 | 0.25 | -0.58 / 1.15 | 0.09 / -0.13 / -0.14 | -0.06 | 0.28 | 0.89 | -0.14 | 0.00 | 167 | NO |
| ZN 5 | r20 vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.47 | -0.64 | 0.62 | 1.17 / 0.95 | 0.05 / 0.01 / 0.10 | 0.00 | -0.28 | 0.98 | -0.09 | 0.50 | 105 | NO |
| ZN 6 | r5 vix-all0.0 dir=against hold=3d entries=day | 129 | 2 | 0.46 | -0.31 | 0.10 | -0.76 / 0.97 | 0.05 / 0.04 / -0.21 | -0.09 | -0.19 | 0.87 | -0.19 | 0.00 | 208 | NO |
| ZN 7 | ema vix-hi0.67 dir=against hold=2d entries=day | 69 | 2 | 0.42 | -0.89 | 0.18 | -0.48 / 0.67 | 0.05 / -0.09 / -0.17 | -0.08 | -0.36 | 0.88 | -0.18 | 0.00 | 105 | NO |
| ZN 8 | ema vix-lo0.33 dir=against hold=2d entries=day | 69 | 2 | 0.32 | -0.73 | 0.29 | 0.14 / 0.78 | 0.03 / 0.03 / -0.05 | -0.06 | 0.04 | 0.93 | -0.16 | 0.00 | 122 | NO |
| ZN 9 | r5 vix-all0.0 dir=against hold=2d entries=day | 172 | 2 | 0.17 | -0.48 | -0.14 | -0.94 / 1.03 | 0.04 / 0.13 / -0.23 | -0.12 | -0.05 | 0.80 | -0.18 | 0.00 | 277 | NO |
| ZN 10 (diag) | ema vix-lo0.33 dir=against hold=5d entries=week | 23 | 2 | 1.10 | 0.25 | 0.70 | -0.01 / 1.41 | 0.16 / 0.03 / -0.21 | 0.03 | -0.03 | 0.95 | -0.09 | 0.00 | 40 S | diag |
| BTC 1 | r20 vix-all0.0 dir=with hold=3d entries=week | 103 | 2 | 1.55 | 0.32 | 0.92 | -0.28 / 1.49 | 0.32 / -0.06 / -0.15 | 0.17 | 0.05 | 0.90 | -0.00 | 1.00 | 145 | NO |
| BTC 2 | r20 vix-all0.0 dir=with hold=2d entries=week | 104 | 2 | 1.28 | 0.32 | 0.71 | -0.47 / 1.41 | 0.27 / -0.23 / -0.07 | 0.13 | 0.04 | 0.93 | -0.04 | 0.00 | 146 | NO |
| BTC 3 | ema vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 1.27 | -0.72 | 0.78 | 0.27 / 1.55 | 0.22 / -0.51 / 0.04 | 0.09 | -0.08 | 0.93 | -0.12 | 0.00 | 116 | NO |
| BTC 4 | r20 vix-all0.0 dir=with hold=5d entries=day | 86 | 2 | 1.14 | -1.03 | 0.26 | -1.00 / 1.36 | 0.19 / -0.68 / -0.20 | -0.01 | 0.10 | 0.78 | -0.22 | 0.00 | 138 | NO |
| BTC 5 | r5 vix-all0.0 dir=against hold=2d entries=day | 172 | 2 | 1.01 | 0.79 | 0.21 | -0.81 / 1.42 | 0.16 / -0.43 / -0.01 | 0.03 | 0.06 | 0.63 | -0.17 | 0.00 | 273 | NO |
| BTC 6 | ema vix-all0.0 dir=with hold=3d entries=week | 103 | 2 | 0.98 | -0.79 | 0.58 | -0.18 / 1.66 | 0.17 / -0.13 / -0.09 | 0.07 | 0.01 | 0.84 | -0.10 | 0.50 | 145 | NO |
| BTC 7 | r20 vix-all0.0 dir=with hold=3d entries=day | 128 | 2 | 0.96 | -0.41 | 0.18 | -0.79 / 1.46 | 0.15 / -0.59 / -0.24 | -0.04 | 0.29 | 0.65 | -0.24 | 0.00 | 202 | NO |
| BTC 8 | r5 vix-all0.0 dir=against hold=5d entries=day | 86 | 2 | 0.90 | 0.65 | 0.30 | -0.56 / 1.12 | 0.13 / 0.16 / -0.38 | 0.01 | 0.14 | 0.73 | -0.16 | 0.50 | 138 | NO |
| BTC 9 | r20 vix-lo0.33 dir=with hold=2d entries=day | 69 | 2 | 0.80 | -0.31 | 0.15 | -0.58 / 1.27 | 0.14 / -0.80 / -0.05 | -0.03 | -0.06 | 0.69 | -0.24 | 0.00 | 116 | NO |
| BTC 10 | ema vix-all0.0 dir=with hold=3d entries=day | 128 | 2 | 0.73 | -0.87 | 0.74 | 0.82 / 1.79 | 0.10 / -0.12 / 0.00 | 0.06 | 0.24 | 0.86 | -0.13 | 0.50 | 202 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 75 |
| diagnostic cells read | 5 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 42 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 62 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 10 |
| small-sample (<100 trades pair window) | 5 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC r20 vix-all0.0 dir=with hold=3d entries=week | clean | 1.52 | 2.95 | -102850 | -83787 | 250410 | -154088 | 5.52 | 48.6 | 1.78 | -80868 | 228342 | -85058 |
| BTC r20 vix-all0.0 dir=with hold=3d entries=week | H1 | 0.30 | 0.43 | -124445 | -121688 | 335843 | -128245 | 0.24 | 46.4 | 2.77 | -80796 | 193049 | -88900 |
| BTC r20 vix-all0.0 dir=with hold=3d entries=week | H2 | -1.26 | -1.46 | -104281 | -69116 | 356631 | -124758 | -0.57 | 27.8 | 2.34 | -84162 | 217425 | -85540 |
| BTC r20 vix-all0.0 dir=with hold=3d entries=week | all | 0.92 | 1.57 | -114922 | -93839 | 486852 | -154088 | 2.58 | 44.0 | 2.07 | -83232 | 228342 | -88900 |
| CL r5 vix-all0.0 dir=against hold=5d entries=day | clean | 0.85 | 1.40 | -115552 | -91838 | 428418 | -226458 | 1.81 | 36.2 | 1.56 | -93995 | 305258 | -125159 |
| CL r5 vix-all0.0 dir=against hold=5d entries=day | H1 | 1.65 | 3.47 | -60650 | -54338 | 94092 | -69238 | 2.98 | 32.1 | 3.12 | -75043 | 156683 | -78287 |
| CL r5 vix-all0.0 dir=against hold=5d entries=day | H2 | 0.71 | 1.08 | -273910 | -230587 | 573239 | -346685 | 0.89 | 38.9 | 3.03 | -77281 | 170914 | -77416 |
| CL r5 vix-all0.0 dir=against hold=5d entries=day | all | 0.80 | 1.25 | -190737 | -138250 | 591821 | -346685 | 2.64 | 36.3 | 2.09 | -89418 | 305258 | -125159 |
| ES r5 vix-all0.0 dir=against hold=3d entries=day | clean | 0.20 | 0.28 | -147141 | -114714 | 851599 | -233256 | 0.21 | 51.4 | 1.47 | -95431 | 281437 | -113732 |
| ES r5 vix-all0.0 dir=against hold=3d entries=day | H1 | 1.38 | 2.38 | -96461 | -90261 | 159430 | -101199 | 2.09 | 39.3 | 3.40 | -67711 | 129806 | -79242 |
| ES r5 vix-all0.0 dir=against hold=3d entries=day | H2 | 0.34 | 0.47 | -162555 | -126826 | 353320 | -182129 | 0.32 | 52.8 | 2.61 | -83603 | 234198 | -88509 |
| ES r5 vix-all0.0 dir=against hold=3d entries=day | all | 0.43 | 0.61 | -145462 | -115952 | 851599 | -233256 | 0.74 | 50.0 | 1.99 | -91593 | 281437 | -113732 |
| GC r5 vix-hi0.67 dir=against hold=2d entries=day | clean | 0.45 | 0.87 | -107506 | -88628 | 604232 | -138836 | 0.68 | 22.9 | 1.50 | -87407 | 283579 | -95915 |
| GC r5 vix-hi0.67 dir=against hold=2d entries=day | H1 | -1.47 | -1.64 | -156427 | -139569 | 343593 | -159270 | -0.90 | 17.9 | 2.34 | -100815 | 168349 | -107649 |
| GC r5 vix-hi0.67 dir=against hold=2d entries=day | H2 | 0.60 | 0.88 | -375741 | -282206 | 840779 | -466074 | 0.54 | 25.0 | 2.46 | -116749 | 217425 | -117286 |
| GC r5 vix-hi0.67 dir=against hold=2d entries=day | all | 0.27 | 0.41 | -203399 | -147099 | 840779 | -466074 | 0.66 | 22.6 | 1.86 | -101823 | 283579 | -117286 |
| NQ ema vix-all0.0 dir=with hold=2d entries=day | clean | 1.42 | 2.58 | -114682 | -89178 | 512382 | -132301 | 2.52 | 42.9 | 1.74 | -79670 | 238135 | -81393 |
| NQ ema vix-all0.0 dir=with hold=2d entries=day | H1 | -1.57 | -1.70 | -233608 | -181442 | 446551 | -248156 | -1.00 | 53.6 | 2.35 | -82306 | 167084 | -88596 |
| NQ ema vix-all0.0 dir=with hold=2d entries=day | H2 | 0.62 | 0.88 | -188485 | -159325 | 535152 | -219877 | 0.53 | 38.9 | 2.69 | -70665 | 209548 | -71121 |
| NQ ema vix-all0.0 dir=with hold=2d entries=day | all | 0.68 | 0.99 | -165118 | -131744 | 563959 | -248156 | 2.00 | 44.0 | 2.05 | -79752 | 238135 | -88596 |
| RTY r20 vix-lo0.33 dir=against hold=2d entries=day | clean | 0.88 | 1.49 | -130258 | -94419 | 420349 | -251272 | 1.90 | 20.0 | 1.60 | -82996 | 280110 | -88848 |
| RTY r20 vix-lo0.33 dir=against hold=2d entries=day | H1 | 1.11 | 1.99 | -118309 | -105132 | 327254 | -153343 | 0.99 | 32.1 | 3.22 | -83316 | 168078 | -88346 |
| RTY r20 vix-lo0.33 dir=against hold=2d entries=day | H2 | 0.94 | 1.89 | -90665 | -70855 | 195244 | -100722 | 1.26 | 25.0 | 2.61 | -78770 | 180148 | -79653 |
| RTY r20 vix-lo0.33 dir=against hold=2d entries=day | all | 0.94 | 1.63 | -124863 | -97936 | 420349 | -251272 | 3.26 | 23.2 | 2.06 | -82732 | 280110 | -88848 |
| YM r5 vix-hi0.67 dir=against hold=2d entries=day | clean | 0.79 | 1.47 | -117651 | -90775 | 327923 | -182595 | 2.17 | 19.0 | 1.60 | -80950 | 324399 | -87616 |
| YM r5 vix-hi0.67 dir=against hold=2d entries=day | H1 | 2.10 | 4.32 | -80637 | -53887 | 161660 | -122037 | 2.51 | 10.7 | 3.22 | -67866 | 133994 | -78364 |
| YM r5 vix-hi0.67 dir=against hold=2d entries=day | H2 | 0.51 | 0.71 | -238053 | -153174 | 444298 | -277166 | 0.48 | 25.0 | 2.49 | -98828 | 217425 | -119441 |
| YM r5 vix-hi0.67 dir=against hold=2d entries=day | all | 0.87 | 1.45 | -144908 | -104572 | 444298 | -277166 | 2.99 | 19.0 | 2.04 | -84636 | 324399 | -119441 |
| ZN r20 vix-lo0.33 dir=against hold=2d entries=day | clean | 0.81 | 1.38 | -132083 | -99047 | 399745 | -154524 | 1.78 | 21.0 | 1.58 | -84414 | 280110 | -100175 |
| ZN r20 vix-lo0.33 dir=against hold=2d entries=day | H1 | 1.37 | 3.04 | -60449 | -52951 | 179540 | -64539 | 1.41 | 42.9 | 2.86 | -80530 | 144170 | -82773 |
| ZN r20 vix-lo0.33 dir=against hold=2d entries=day | H2 | 0.04 | 0.06 | -94931 | -67322 | 231334 | -113622 | 0.04 | 25.0 | 2.52 | -78400 | 200703 | -79653 |
| ZN r20 vix-lo0.33 dir=against hold=2d entries=day | all | 0.77 | 1.32 | -117849 | -87763 | 399745 | -154524 | 2.43 | 25.6 | 1.99 | -83022 | 280110 | -100175 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES r5 vix-all0.0 dir=against hold=3d entries=day | -23.1 | -27.4 | 5.6 | 20.1 | -28.4 / -2.0 | 28.2 / 42.6 | NO |
| NQ ema vix-all0.0 dir=with hold=2d entries=day | -17.7 | -12.6 | 18.7 | 33.4 | 12.1 / 23.2 | -18.7 / -5.1 | NO |
| RTY r20 vix-lo0.33 dir=against hold=2d entries=day | -15.0 | 13.8 | 21.3 | 30.0 | 13.2 / 21.1 | 9.3 / 19.0 | NO |
| YM r5 vix-hi0.67 dir=against hold=2d entries=day | -15.5 | -39.9 | 15.6 | 6.3 | 14.7 / 25.2 | 29.9 / 45.3 | NO |
| GC r5 vix-hi0.67 dir=against hold=2d entries=day | -23.9 | -54.8 | -20.8 | 28.1 | -0.2 / 13.1 | -27.6 / -14.9 | NO |
| CL r5 vix-all0.0 dir=against hold=5d entries=day | -12.9 | -50.1 | 3.3 | 10.6 | -51.3 / 0.7 | 30.0 / 35.0 | NO |
| ZN r20 vix-lo0.33 dir=against hold=2d entries=day | -19.4 | -11.4 | 19.4 | 30.0 | -12.2 / 17.2 | 20.0 / 24.4 | NO |
| BTC r20 vix-all0.0 dir=with hold=3d entries=week | -16.2 | 13.0 | 20.1 | 40.0 | 19.7 / 24.2 | 8.3 / 12.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 ema vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 449 | 72.0 | 42.7 | 56.9 | 29.4 | 0.13 / 0.08 / 0.10 | 1394.0 / 1364.7 |
| ES 2 r20 vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 449 | 178.2 | 148.8 | 163.0 | 29.4 | 0.33 / 0.27 / 0.30 | 1239.1 / 1209.7 |
| ES 3 r5 vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 414 | -103.4 | -132.7 | -118.8 | 29.4 | -0.45 / -0.57 / -0.51 | 404.0 / 374.6 |
| ES 4 r20 vix-all0.0 dir=with hold=2d entries=day | gross-positive, cost-negative pre-2023 | 896 | 22.9 | -6.5 | 7.8 | 29.4 | 0.11 / -0.03 / 0.04 | 453.0 / 423.6 |
| ES 5 r5 vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 449 | 183.3 | 154.0 | 168.2 | 29.4 | 0.34 / 0.28 / 0.31 | 1010.9 / 981.5 |
| ES 6 ema vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 414 | -11.7 | -41.1 | -27.2 | 29.4 | -0.04 / -0.16 / -0.10 | 362.3 / 333.0 |
| ES 7 r5 vix-hi0.67 dir=against hold=2d entries=day | positive pre-2023 | 320 | 328.9 | 299.6 | 314.2 | 29.4 | 0.61 / 0.55 / 0.58 | 664.9 / 635.5 |
| ES 8 ema vix-all0.0 dir=with hold=2d entries=day | negative pre-2023 | 897 | -71.8 | -101.2 | -86.9 | 29.4 | -0.32 / -0.45 / -0.39 | 197.0 / 167.7 |
| ES 9 r5 vix-all0.0 dir=against hold=3d entries=day | positive pre-2023 | 673 | 185.6 | 156.3 | 170.5 | 29.4 | 0.55 / 0.46 / 0.51 | 123.5 / 94.2 |
| ES 10 r20 vix-hi0.67 dir=with hold=2d entries=day | negative pre-2023 | 320 | -53.6 | -83.0 | -68.3 | 29.4 | -0.10 / -0.15 / -0.12 | 119.6 / 90.2 |
| NQ 1 ema vix-all0.0 dir=with hold=2d entries=day | gross-positive, cost-negative pre-2023 | 897 | 3.0 | -11.4 | -2.8 | 14.4 | 0.01 / -0.03 / -0.01 | 1077.8 / 1063.5 |
| NQ 2 ema vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 449 | 92.0 | 77.7 | 86.3 | 14.4 | 0.11 / 0.09 / 0.10 | 2367.3 / 2353.0 |
| NQ 3 r20 vix-all0.0 dir=with hold=2d entries=day | positive pre-2023 | 896 | 67.3 | 53.0 | 61.6 | 14.4 | 0.20 / 0.16 / 0.18 | 875.3 / 860.9 |
| NQ 4 r5 vix-hi0.67 dir=against hold=2d entries=day | positive pre-2023 | 320 | 394.9 | 380.6 | 389.3 | 14.4 | 0.51 / 0.49 / 0.51 | 1402.6 / 1388.2 |
| NQ 5 ema vix-lo0.33 dir=with hold=2d entries=day | positive pre-2023 | 414 | 47.2 | 32.8 | 41.2 | 14.4 | 0.12 / 0.08 / 0.10 | 584.3 / 569.9 |
| NQ 6 r5 vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 414 | -92.1 | -106.4 | -98.0 | 14.4 | -0.25 / -0.29 / -0.26 | 568.6 / 554.3 |
| NQ 7 r5 vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 449 | 107.6 | 93.3 | 101.8 | 14.4 | 0.13 / 0.11 / 0.12 | 1177.9 / 1163.5 |
| NQ 8 r20 vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 448 | 75.9 | 61.5 | 70.1 | 14.4 | 0.09 / 0.07 / 0.08 | 555.8 / 541.5 |
| NQ 9 (diag) r5 vix-hi0.67 dir=against hold=2d entries=week | positive pre-2023 | 153 | 642.8 | 628.5 | 637.2 | 14.4 | 0.66 / 0.65 / 0.66 | 1926.5 / 1912.2 |
| NQ 10 (diag) r5 vix-lo0.33 dir=with hold=5d entries=week | gross-positive, cost-negative pre-2023 | 134 | 8.9 | -5.5 | 2.9 | 14.4 | 0.01 / -0.00 / 0.00 | 2297.8 / 2283.5 |
| RTY 1 ema vix-all0.0 dir=against hold=2d entries=week | positive pre-2023 | 308 | 168.3 | 154.0 | 156.2 | 14.4 | 0.74 / 0.68 / 0.69 | 357.2 / 342.9 |
| RTY 2 ema vix-lo0.33 dir=against hold=2d entries=day | positive pre-2023 | 214 | 43.0 | 28.7 | 30.0 | 14.4 | 0.15 / 0.10 / 0.11 | 347.8 / 333.5 |
| RTY 3 ema vix-all0.0 dir=against hold=3d entries=week | positive pre-2023 | 309 | 235.8 | 221.4 | 223.6 | 14.4 | 0.77 / 0.72 / 0.73 | 355.4 / 341.0 |
| RTY 4 r20 vix-all0.0 dir=with hold=3d entries=day | gross-positive, cost-negative pre-2023 | 384 | 1.8 | -12.6 | -10.3 | 14.4 | 0.01 / -0.04 / -0.04 | 304.3 / 290.0 |
| RTY 5 r20 vix-lo0.33 dir=against hold=2d entries=day | negative pre-2023 | 213 | -41.8 | -56.1 | -54.8 | 14.4 | -0.15 / -0.20 / -0.20 | 299.9 / 285.5 |
| RTY 6 r5 vix-all0.0 dir=with hold=5d entries=day | negative pre-2023 | 257 | -51.0 | -65.3 | -63.1 | 14.4 | -0.12 / -0.15 / -0.14 | 365.3 / 351.0 |
| RTY 7 r5 vix-hi0.67 dir=against hold=2d entries=day | gross-positive, cost-negative pre-2023 | 193 | 8.9 | -5.5 | -2.5 | 14.4 | 0.02 / -0.01 / -0.01 | 219.6 / 205.2 |
| RTY 8 ema vix-all0.0 dir=against hold=2d entries=day | positive pre-2023 | 513 | 77.8 | 63.4 | 65.6 | 14.4 | 0.42 / 0.34 / 0.35 | 66.3 / 51.9 |
| RTY 9 (diag) ema vix-all0.0 dir=against hold=5d entries=week | positive pre-2023 | 155 | 293.2 | 278.9 | 281.1 | 14.4 | 0.54 / 0.51 / 0.51 | 944.1 / 929.8 |
| RTY 10 (diag) ema vix-hi0.67 dir=against hold=2d entries=week | positive pre-2023 | 95 | 380.9 | 366.6 | 369.7 | 14.4 | 0.80 / 0.77 / 0.78 | 598.7 / 584.3 |
| YM 1 ema vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 450 | 222.2 | 207.8 | 213.6 | 14.4 | 0.51 / 0.47 / 0.49 | 659.4 / 645.1 |
| YM 2 r5 vix-all0.0 dir=with hold=5d entries=day | positive pre-2023 | 450 | 313.3 | 299.0 | 304.7 | 14.4 | 0.72 / 0.68 / 0.70 | 584.4 / 570.1 |
| YM 3 r5 vix-hi0.67 dir=against hold=2d entries=day | positive pre-2023 | 321 | 150.1 | 135.7 | 141.7 | 14.4 | 0.35 / 0.31 / 0.33 | 399.5 / 385.1 |
| YM 4 ema vix-all0.0 dir=against hold=2d entries=week | positive pre-2023 | 543 | 108.1 | 93.7 | 99.5 | 14.4 | 0.53 / 0.46 / 0.49 | 208.8 / 194.4 |
| YM 5 r5 vix-all0.0 dir=against hold=3d entries=week | positive pre-2023 | 543 | 170.9 | 156.6 | 162.3 | 14.4 | 0.59 / 0.54 / 0.56 | 286.3 / 271.9 |
| YM 6 r5 vix-all0.0 dir=with hold=3d entries=day | negative pre-2023 | 674 | -122.9 | -137.3 | -131.6 | 14.4 | -0.44 / -0.49 / -0.47 | 194.7 / 180.3 |
| YM 7 r20 vix-all0.0 dir=with hold=2d entries=day | negative pre-2023 | 898 | -29.1 | -43.5 | -37.7 | 14.4 | -0.15 / -0.22 / -0.19 | 176.0 / 161.6 |
| YM 8 r5 vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 415 | -42.1 | -56.4 | -50.8 | 14.4 | -0.21 / -0.28 / -0.25 | 150.5 / 136.1 |
| YM 9 r20 vix-lo0.33 dir=against hold=2d entries=day | positive pre-2023 | 415 | 33.7 | 19.3 | 24.9 | 14.4 | 0.16 / 0.09 / 0.11 | 139.6 / 125.3 |
| YM 10 r20 vix-hi0.67 dir=against hold=2d entries=day | positive pre-2023 | 321 | 133.1 | 118.7 | 124.7 | 14.4 | 0.31 / 0.28 / 0.29 | 139.9 / 125.6 |
| GC 1 r20 vix-lo0.33 dir=against hold=2d entries=day | negative pre-2023 | 415 | -67.5 | -91.9 | -82.4 | 24.4 | -0.25 / -0.33 / -0.30 | 1112.0 / 1087.7 |
| GC 2 ema vix-lo0.33 dir=against hold=2d entries=day | negative pre-2023 | 415 | -96.2 | -120.6 | -111.1 | 24.4 | -0.35 / -0.43 / -0.40 | 758.4 / 734.0 |
| GC 3 ema vix-all0.0 dir=against hold=2d entries=day | negative pre-2023 | 897 | -81.9 | -106.2 | -96.4 | 24.4 | -0.38 / -0.49 / -0.44 | 446.0 / 421.7 |
| GC 4 ema vix-all0.0 dir=against hold=3d entries=day | positive pre-2023 | 673 | 30.1 | 5.7 | 15.5 | 24.4 | 0.09 / 0.02 / 0.05 | 411.2 / 386.8 |
| GC 5 r20 vix-all0.0 dir=against hold=5d entries=day | positive pre-2023 | 448 | 110.4 | 86.1 | 95.9 | 24.4 | 0.23 / 0.18 / 0.20 | 536.2 / 511.8 |
| GC 6 r20 vix-all0.0 dir=against hold=2d entries=week | positive pre-2023 | 543 | 43.1 | 18.8 | 28.5 | 24.4 | 0.17 / 0.08 / 0.11 | 221.8 / 197.4 |
| GC 7 r5 vix-hi0.67 dir=against hold=2d entries=day | positive pre-2023 | 320 | 98.8 | 74.4 | 84.4 | 24.4 | 0.24 / 0.18 / 0.21 | 421.7 / 397.4 |
| GC 8 r20 vix-all0.0 dir=against hold=3d entries=week | positive pre-2023 | 544 | 129.0 | 104.7 | 114.5 | 24.4 | 0.40 / 0.33 / 0.36 | 242.8 / 218.4 |
| GC 9 r20 vix-hi0.67 dir=with hold=2d entries=day | gross-positive, cost-negative pre-2023 | 321 | 0.1 | -24.3 | -14.3 | 24.4 | 0.00 / -0.06 / -0.04 | 223.8 / 199.4 |
| GC 10 ema vix-all0.0 dir=with hold=5d entries=day | gross-positive, cost-negative pre-2023 | 448 | 18.6 | -5.7 | 4.0 | 24.4 | 0.04 / -0.01 / 0.01 | 17.8 / -6.5 |
| CL 1 r20 vix-hi0.67 dir=against hold=2d entries=day | negative pre-2023 | 320 | -224.1 | -248.5 | -245.7 | 24.4 | -0.49 / -0.54 / -0.54 | 329.9 / 305.5 |
| CL 2 r5 vix-all0.0 dir=against hold=5d entries=day | negative pre-2023 | 448 | -142.2 | -166.6 | -163.9 | 24.4 | -0.29 / -0.34 / -0.34 | 433.0 / 408.7 |
| CL 3 r5 vix-all0.0 dir=against hold=3d entries=day | positive pre-2023 | 673 | 50.9 | 26.5 | 29.1 | 24.4 | 0.16 / 0.09 / 0.10 | 312.3 / 288.0 |
| CL 4 ema vix-all0.0 dir=with hold=2d entries=week | positive pre-2023 | 544 | 34.5 | 10.1 | 12.7 | 24.4 | 0.12 / 0.04 / 0.04 | 148.1 / 123.7 |
| CL 5 r5 vix-all0.0 dir=against hold=2d entries=day | negative pre-2023 | 896 | -46.9 | -71.3 | -68.7 | 24.4 | -0.20 / -0.31 / -0.30 | 169.3 / 144.9 |
| CL 6 r5 vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 415 | -75.9 | -100.2 | -98.2 | 24.4 | -0.30 / -0.39 / -0.38 | 97.0 / 72.6 |
| CL 7 r20 vix-all0.0 dir=against hold=3d entries=day | negative pre-2023 | 673 | -99.0 | -123.4 | -120.8 | 24.4 | -0.29 / -0.36 / -0.36 | 162.2 / 137.9 |
| CL 8 ema vix-hi0.67 dir=against hold=2d entries=day | negative pre-2023 | 320 | -135.5 | -159.9 | -157.1 | 24.4 | -0.28 / -0.33 / -0.32 | 144.9 / 120.6 |
| CL 9 r5 vix-all0.0 dir=against hold=3d entries=week | positive pre-2023 | 543 | 77.5 | 53.1 | 55.7 | 24.4 | 0.22 / 0.15 / 0.16 | 160.8 / 136.4 |
| CL 10 r20 vix-all0.0 dir=against hold=5d entries=day | negative pre-2023 | 448 | -336.5 | -360.9 | -358.2 | 24.4 | -0.69 / -0.74 / -0.74 | 164.5 / 140.2 |
| ZN 1 r5 vix-lo0.33 dir=against hold=2d entries=day | negative pre-2023 | 416 | -30.8 | -66.4 | -71.6 | 35.6 | -0.37 / -0.80 / -0.86 | 102.4 / 66.7 |
| ZN 2 r20 vix-lo0.33 dir=against hold=2d entries=day | gross-positive, cost-negative pre-2023 | 416 | 9.2 | -26.4 | -31.5 | 35.6 | 0.13 / -0.29 / -0.35 | 114.4 / 78.7 |
| ZN 3 r5 vix-all0.0 dir=against hold=3d entries=week | positive pre-2023 | 543 | 36.2 | 0.6 | -4.6 | 35.6 | 0.39 / 0.01 / -0.05 | 97.1 / 61.4 |
| ZN 4 r5 vix-all0.0 dir=against hold=2d entries=week | gross-positive, cost-negative pre-2023 | 543 | 31.9 | -3.7 | -8.8 | 35.6 | 0.44 / -0.05 / -0.12 | 81.3 / 45.7 |
| ZN 5 r20 vix-hi0.67 dir=against hold=2d entries=day | negative pre-2023 | 322 | -47.2 | -82.8 | -87.9 | 35.6 | -0.37 / -0.64 / -0.68 | 84.2 / 48.6 |
| ZN 6 r5 vix-all0.0 dir=against hold=3d entries=day | gross-positive, cost-negative pre-2023 | 673 | 8.0 | -27.6 | -32.7 | 35.6 | 0.09 / -0.31 / -0.36 | 73.3 / 37.7 |
| ZN 7 ema vix-hi0.67 dir=against hold=2d entries=day | negative pre-2023 | 322 | -78.5 | -114.1 | -119.2 | 35.6 | -0.62 / -0.89 / -0.93 | 76.1 / 40.5 |
| ZN 8 ema vix-lo0.33 dir=against hold=2d entries=day | negative pre-2023 | 416 | -26.6 | -62.2 | -67.3 | 35.6 | -0.31 / -0.73 / -0.79 | 74.3 / 38.7 |
| ZN 9 r5 vix-all0.0 dir=against hold=2d entries=day | gross-positive, cost-negative pre-2023 | 897 | 6.2 | -29.4 | -34.5 | 35.6 | 0.10 / -0.48 / -0.57 | 44.5 / 8.9 |
| ZN 10 (diag) ema vix-lo0.33 dir=against hold=5d entries=week | positive pre-2023 | 134 | 91.9 | 56.3 | 51.1 | 35.6 | 0.41 / 0.25 / 0.23 | 225.5 / 189.9 |
| BTC 1 r20 vix-all0.0 dir=with hold=3d entries=week | positive pre-2023 | 77 | 406.2 | 351.8 | 384.4 | 54.4 | 0.37 / 0.32 / 0.35 | 3808.3 / 3753.9 |
| BTC 2 r20 vix-all0.0 dir=with hold=2d entries=week | positive pre-2023 | 77 | 350.6 | 296.3 | 328.9 | 54.4 | 0.38 / 0.32 / 0.36 | 2620.7 / 2566.3 |
| BTC 3 ema vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 60 | -514.2 | -568.5 | -534.2 | 54.4 | -0.65 / -0.72 / -0.68 | 2810.5 / 2756.1 |
| BTC 4 r20 vix-all0.0 dir=with hold=5d entries=day | negative pre-2023 | 64 | -2125.8 | -2180.1 | -2147.8 | 54.4 | -1.00 / -1.03 / -1.01 | 3792.2 / 3737.8 |
| BTC 5 r5 vix-all0.0 dir=against hold=2d entries=day | positive pre-2023 | 128 | 770.1 | 715.8 | 748.2 | 54.4 | 0.85 / 0.79 / 0.82 | 1358.3 / 1303.9 |
| BTC 6 ema vix-all0.0 dir=with hold=3d entries=week | negative pre-2023 | 78 | -787.8 | -842.2 | -809.7 | 54.4 | -0.74 / -0.79 / -0.76 | 2458.3 / 2403.9 |
| BTC 7 r20 vix-all0.0 dir=with hold=3d entries=day | negative pre-2023 | 96 | -427.1 | -481.4 | -449.0 | 54.4 | -0.36 / -0.41 / -0.38 | 2081.6 / 2027.3 |
| BTC 8 r5 vix-all0.0 dir=against hold=5d entries=day | positive pre-2023 | 64 | 1463.3 | 1408.9 | 1441.4 | 54.4 | 0.68 / 0.65 / 0.67 | 3100.9 / 3046.5 |
| BTC 9 r20 vix-lo0.33 dir=with hold=2d entries=day | negative pre-2023 | 60 | -181.7 | -236.0 | -201.7 | 54.4 | -0.23 / -0.31 / -0.26 | 1782.2 / 1727.9 |
| BTC 10 ema vix-all0.0 dir=with hold=3d entries=day | negative pre-2023 | 96 | -1111.7 | -1166.1 | -1133.6 | 54.4 | -0.83 / -0.87 / -0.85 | 1584.0 / 1529.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 13 cells pass the clean rule against a replicate mean of 15.0 (p(count) = 0.77, p(top) = 0.33); CL: 11 cells pass the clean rule against a replicate mean of 14.5 (p(count) = 0.88, p(top) = 0.99); ES: 10 cells pass the clean rule against a replicate mean of 14.7 (p(count) = 0.94, p(top) = 0.64); GC: 10 cells pass the clean rule against a replicate mean of 14.9 (p(count) = 0.93, p(top) = 0.90); NQ: 8 cells pass the clean rule against a replicate mean of 15.7 (p(count) = 0.99, p(top) = 0.64); RTY: 8 cells pass the clean rule against a replicate mean of 15.7 (p(count) = 0.99, p(top) = 0.91); YM: 11 cells pass the clean rule against a replicate mean of 15.2 (p(count) = 0.93, p(top) = 0.96); ZN: 9 cells pass the clean rule against a replicate mean of 8.5 (p(count) = 0.49, p(top) = 0.96).
- Of 75 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.19 (CL r5 vix-all0.0 dir=against hold=5d entries=day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 9; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell RTY r20 vix-lo0.33 dir=against hold=2d entries=day: uplift +0.14/+0.40/+0.13, boot lo -0.01, plateau 0.50, 2x-slip +0.15, wd corr +0.14, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell CL r5 vix-all0.0 dir=against hold=5d entries=day: uplift +0.10/+0.29/+0.55, boot lo -0.06, plateau 0.00, 2x-slip +0.19, wd corr -0.24, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 35, 'negative pre-2023': 30, 'gross-positive, cost-negative pre-2023': 10}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_36.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw36/ (`SW36_CO_all_selected_scored.csv`).

DONE SW36
