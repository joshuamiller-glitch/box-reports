# REPORT SW34 - weekly-horizon frozen LightGBM on daily features, own instrument (D12 H6 M1-M3)

**Verdict: LEAD. FOUND 0, LEAD 5, INSURANCE 0.** 46 selected cells (+15 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.24; best pair-window standalone Sharpe +1.55.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Model: LightGBM (100 trees, 4 leaves, min 40/leaf, subsample 0.7, colsample 0.8, L2 5, seed 11), frozen, trained once on label days <= 2022-12-31 (BTC <= 2023-07-31) on causal daily features (returns 1/5/20/60 in ATR units, range ratio, close location, distance to 60-day extremes, 5/20 vol ratio, VIX percentile vs prior 250 days, VIX/VIX3M, day of week); target sign of the N-day open-to-open move from the RTH open. Entries at the RTH open on the first label day of the week or any flat day; P >= th long, P <= 1-th short (th 0.5 = always trade); hold N = 2/3/5 label days. MINTR 60 (weekly cadence cannot reach 100 clean trades): every cell with < 100 trades in the pair window carries the small-sample flag and cannot be FOUND.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 18 cells per instrument = 3 holds x 3 th x 2 entry modes.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      18 |         15 |         0 |               0.071 |                1 |          0 |            3 |
| CL    |      18 |         13 |         0 |               0.11  |                1 |          0 |            3 |
| ES    |      18 |         15 |         8 |               1.777 |                2 |          8 |            2 |
| GC    |      18 |         13 |         9 |               1.277 |                2 |          9 |            1 |
| NQ    |      18 |         15 |        12 |               1.78  |                2 |         10 |            0 |
| RTY   |      18 |         13 |         2 |               0.861 |                2 |          2 |            3 |
| YM    |      18 |         14 |        10 |               1.189 |                2 |         10 |            0 |
| ZN    |      18 |         13 |         7 |               1.286 |                2 |          7 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    8 |            2.82  |               7 |       0    |                       1.259 |            0.758 |           1.187 |    0.04  |       1.777 |                1.71  |
| NQ    |     200 |                   12 |            3.265 |               7 |       0    |                       1.136 |            0.762 |           1.188 |    0.06  |       1.78  |                1.801 |
| RTY   |     200 |                    2 |            2.79  |               8 |       0.83 |                       0.441 |            0.785 |           1.314 |    0.855 |       0.673 |                1.822 |
| YM    |     200 |                   10 |            2.655 |               7 |       0    |                       0.736 |            0.741 |           1.167 |    0.505 |       1.189 |                1.885 |
| GC    |     200 |                    9 |            2.43  |               6 |       0    |                       1.024 |            0.785 |           1.299 |    0.175 |       1.277 |                1.772 |
| CL    |     200 |                    0 |            2.49  |               5 |       1    |                     nan     |            0.783 |           1.275 |  nan     |     nan     |                1.734 |
| ZN    |     200 |                    7 |            1.47  |               5 |       0    |                       0.75  |            0.714 |           1.318 |    0.29  |       1.221 |                1.487 |
| BTC   |     200 |                    0 |            2.84  |               7 |       1    |                     nan     |            0.77  |           1.198 |  nan     |     nan     |                1.905 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | LGBM(<=2022) 3d P>=0.5 entries=week | 104 | 2 | 1.78 | 0.76 | 1.55 | 1.16 / 1.48 | 0.26 / 0.35 / 0.01 | 0.20 | 0.34 | 1.00 | 0.05 | 0.50 | 167 | NO |
| ES 2 | LGBM(<=2022) 3d P>=0.52 entries=week | 97 | 2 | 1.66 | 0.89 | 1.43 | 1.07 / 1.62 | 0.24 / 0.30 / 0.01 | 0.18 | 0.37 | 0.99 | 0.03 | 0.75 | 157 | NO |
| ES 3 | LGBM(<=2022) 3d P>=0.55 entries=week | 71 | 2 | 1.59 | 0.86 | 1.18 | 0.47 / 1.29 | 0.22 / 0.26 / -0.14 | 0.13 | 0.37 | 1.00 | -0.02 | 0.50 | 123 | NO |
| ES 4 | LGBM(<=2022) 2d P>=0.5 entries=week | 105 | 2 | 1.31 | 0.66 | 1.47 | 1.73 / 1.43 | 0.17 / 0.46 / 0.23 | 0.20 | 0.19 | 0.99 | 0.02 | 0.00 | 168 | LEAD |
| ES 5 | LGBM(<=2022) 3d P>=0.55 entries=day | 113 | 2 | 1.24 | 1.02 | 0.66 | -0.12 / 1.38 | 0.13 / -0.25 / -0.08 | 0.02 | 0.05 | 0.84 | -0.15 | 0.75 | 185 | NO |
| ES 6 | LGBM(<=2022) 2d P>=0.55 entries=week | 69 | 2 | 0.98 | 1.08 | 1.05 | 1.15 / 1.40 | 0.11 / 0.25 / 0.14 | 0.12 | 0.21 | 0.99 | -0.07 | 1.00 | 105 | LEAD |
| ES 7 | LGBM(<=2022) 2d P>=0.52 entries=week | 94 | 2 | 0.98 | 0.79 | 1.37 | 1.95 / 1.31 | 0.11 / 0.45 / 0.35 | 0.18 | 0.19 | 0.99 | -0.00 | 1.00 | 149 | LEAD |
| ES 8 | LGBM(<=2022) 2d P>=0.5 entries=day | 172 | 2 | 0.55 | 0.51 | 0.51 | 0.41 / 1.25 | 0.06 / -0.03 / 0.19 | 0.05 | -0.10 | 0.83 | -0.13 | 0.00 | 277 | NO |
| ES 9 (diag) | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 1 | 0.53 | 0.53 | 0.79 | 1.38 / 1.20 | 0.05 / 0.48 / 0.13 | 0.10 | 0.21 | 0.91 | -0.07 | 1.00 | 138 | diag |
| ES 10 (diag) | LGBM(<=2022) 5d P>=0.52 entries=day | 86 | 1 | 0.47 | 0.88 | 0.41 | 0.41 / 1.45 | 0.05 / 0.20 / -0.06 | 0.03 | 0.04 | 0.78 | -0.14 | 1.00 | 138 | diag |
| NQ 1 | LGBM(<=2022) 3d P>=0.5 entries=week | 104 | 2 | 1.78 | 0.90 | 1.28 | 0.51 / 1.34 | 0.27 / 0.28 / -0.17 | 0.16 | 0.28 | 0.99 | -0.01 | 0.00 | 167 | NO |
| NQ 2 | LGBM(<=2022) 3d P>=0.55 entries=week | 87 | 2 | 1.74 | 1.21 | 1.19 | 0.39 / 1.43 | 0.28 / 0.18 / -0.19 | 0.16 | -0.02 | 0.96 | -0.02 | 0.50 | 142 | NO |
| NQ 3 | LGBM(<=2022) 3d P>=0.52 entries=week | 100 | 2 | 1.60 | 1.06 | 1.22 | 0.63 / 1.39 | 0.23 / 0.28 / -0.12 | 0.15 | 0.27 | 0.98 | -0.02 | 0.75 | 158 | NO |
| NQ 4 | LGBM(<=2022) 2d P>=0.52 entries=week | 100 | 2 | 1.15 | 1.20 | 1.17 | 1.22 / 1.36 | 0.15 / 0.17 / 0.18 | 0.15 | 0.08 | 0.99 | -0.05 | 1.00 | 156 | LEAD |
| NQ 5 | LGBM(<=2022) 3d P>=0.52 entries=day | 127 | 2 | 1.14 | 0.78 | 1.28 | 1.48 / 1.28 | 0.20 / 0.01 / 0.45 | 0.23 | -0.23 | 0.99 | 0.03 | 0.00 | 203 | NO |
| NQ 6 | LGBM(<=2022) 2d P>=0.55 entries=week | 79 | 2 | 1.00 | 1.26 | 0.92 | 0.83 / 1.65 | 0.12 / -0.06 / 0.14 | 0.09 | 0.12 | 0.97 | -0.11 | 0.50 | 127 | NO |
| NQ 7 | LGBM(<=2022) 2d P>=0.5 entries=week | 105 | 2 | 0.91 | 1.18 | 0.94 | 0.99 / 1.51 | 0.10 / 0.10 / 0.13 | 0.10 | 0.08 | 0.94 | -0.11 | 0.00 | 168 | NO |
| NQ 8 | LGBM(<=2022) 5d P>=0.52 entries=day | 86 | 2 | 0.69 | 0.45 | 1.05 | 1.52 / 1.66 | 0.09 / 0.06 / 0.36 | 0.14 | 0.06 | 0.95 | -0.04 | 0.75 | 137 | NO |
| NQ 9 | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 2 | 0.68 | 0.75 | 0.90 | 1.16 / 1.00 | 0.07 / 0.51 / 0.11 | 0.12 | -0.03 | 0.96 | -0.07 | 1.00 | 138 | NO |
| NQ 10 | LGBM(<=2022) 2d P>=0.5 entries=day | 172 | 2 | 0.67 | 0.66 | 0.30 | -0.13 / 1.19 | 0.07 / -0.56 / 0.08 | -0.01 | -0.29 | 0.75 | -0.25 | 0.00 | 277 | NO |
| RTY 1 | LGBM(<=2022) 5d P>=0.52 entries=day | 84 | 2 | 0.67 | 1.16 | 0.40 | -0.08 / 1.71 | 0.11 / 0.21 / -0.07 | 0.07 | 0.41 | 0.73 | -0.11 | 0.25 | 135 | NO |
| RTY 2 | LGBM(<=2022) 2d P>=0.52 entries=day | 151 | 2 | 0.21 | 2.48 | -0.61 | -1.96 / 1.61 | 0.03 / -0.72 / -0.30 | -0.16 | -0.01 | 0.18 | -0.33 | 0.00 | 245 | NO |
| RTY 3 (diag) | LGBM(<=2022) 2d P>=0.52 entries=week | 74 | 1 | 0.86 | 1.84 | 0.29 | -0.65 / 1.31 | 0.11 / -0.52 / 0.13 | 0.01 | -0.41 | 0.70 | -0.16 | 0.50 | 120 | diag |
| RTY 4 (diag) | LGBM(<=2022) 5d P>=0.5 entries=week | 52 | 1 | 0.55 | 1.24 | -0.14 | -1.97 / 1.38 | 0.09 / -0.20 / -0.29 | -0.04 | 0.03 | 0.41 | -0.23 | 0.00 | 84 S | diag |
| RTY 5 (diag) | LGBM(<=2022) 2d P>=0.5 entries=day | 172 | 1 | 0.53 | 1.90 | 0.21 | -0.42 / 1.30 | 0.07 / -0.38 / 0.06 | -0.01 | 0.06 | 0.66 | -0.18 | 0.00 | 276 | diag |
| YM 1 | LGBM(<=2022) 3d P>=0.55 entries=day | 114 | 2 | 1.19 | 1.32 | 1.18 | 1.15 / 1.38 | 0.19 / 0.51 / -0.05 | 0.17 | -0.13 | 0.98 | 0.02 | 0.25 | 184 | NO |
| YM 2 | LGBM(<=2022) 2d P>=0.52 entries=week | 82 | 2 | 1.13 | 1.49 | 1.31 | 1.61 / 1.58 | 0.14 / 0.63 / 0.24 | 0.21 | 0.30 | 1.00 | 0.02 | 1.00 | 133 | LEAD |
| YM 3 | LGBM(<=2022) 2d P>=0.5 entries=week | 105 | 2 | 1.10 | 1.29 | 1.05 | 1.03 / 1.48 | 0.18 / 0.44 / 0.09 | 0.19 | 0.35 | 1.00 | -0.00 | 0.00 | 168 | NO |
| YM 4 | LGBM(<=2022) 3d P>=0.5 entries=week | 104 | 2 | 0.87 | 0.99 | 0.66 | 0.37 / 1.21 | 0.13 / 0.38 / -0.18 | 0.09 | 0.27 | 0.85 | -0.08 | 0.50 | 167 | NO |
| YM 5 | LGBM(<=2022) 2d P>=0.5 entries=day | 172 | 2 | 0.60 | 0.72 | 0.26 | -0.25 / 1.06 | 0.07 / 0.14 / -0.07 | 0.03 | -0.50 | 0.78 | -0.15 | 0.00 | 277 | NO |
| YM 6 | LGBM(<=2022) 2d P>=0.55 entries=day | 135 | 2 | 0.58 | 1.19 | 0.85 | 1.45 / 1.66 | 0.06 / 0.30 / 0.19 | 0.11 | 0.05 | 0.93 | -0.06 | 1.00 | 203 | NO |
| YM 7 | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 2 | 0.55 | 0.88 | 0.58 | 0.54 / 1.41 | 0.06 / 0.34 / -0.01 | 0.07 | -0.26 | 0.86 | -0.10 | 0.00 | 138 | NO |
| YM 8 | LGBM(<=2022) 3d P>=0.52 entries=week | 99 | 2 | 0.52 | 1.16 | 0.37 | 0.21 / 1.44 | 0.08 / 0.26 / -0.19 | 0.04 | 0.27 | 0.65 | -0.14 | 0.75 | 150 | NO |
| YM 9 | LGBM(<=2022) 5d P>=0.52 entries=day | 84 | 2 | 0.49 | 0.50 | 0.32 | -0.00 / 1.55 | 0.06 / 0.18 / -0.12 | 0.03 | -0.07 | 0.70 | -0.14 | 0.50 | 135 | NO |
| YM 10 | LGBM(<=2022) 5d P>=0.55 entries=day | 80 | 2 | 0.35 | 0.85 | 0.58 | 0.97 / 1.78 | 0.01 / 0.36 / 0.04 | 0.05 | -0.14 | 0.86 | -0.12 | 0.50 | 125 | NO |
| GC 1 | LGBM(<=2022) 3d P>=0.52 entries=day | 119 | 2 | 1.28 | 1.60 | 0.06 | -0.46 / 1.38 | 0.21 / -0.82 / -0.92 | -0.20 | -0.28 | 0.57 | -0.62 | 0.00 | 190 | NO |
| GC 2 | LGBM(<=2022) 3d P>=0.5 entries=week | 105 | 2 | 1.24 | 1.27 | -0.01 | -0.72 / 1.76 | 0.17 / -1.53 / -0.43 | -0.22 | 0.31 | 0.64 | -0.59 | 0.00 | 168 | NO |
| GC 3 | LGBM(<=2022) 2d P>=0.5 entries=week | 105 | 2 | 1.19 | 1.03 | -0.13 | -0.81 / 1.70 | 0.17 / -2.08 / -0.08 | -0.24 | 0.12 | 0.45 | -0.67 | 0.00 | 168 | NO |
| GC 4 | LGBM(<=2022) 3d P>=0.5 entries=day | 129 | 2 | 1.17 | 1.14 | -0.00 | -0.68 / 1.67 | 0.16 / -1.04 / -0.52 | -0.17 | 0.47 | 0.55 | -0.48 | 0.00 | 207 | NO |
| GC 5 | LGBM(<=2022) 5d P>=0.55 entries=day | 66 | 2 | 1.04 | 1.57 | -0.24 | -0.94 / 1.59 | 0.13 / -0.93 / -1.01 | -0.28 | -0.17 | 0.34 | -0.63 | 0.00 | 101 | NO |
| GC 6 | LGBM(<=2022) 2d P>=0.52 entries=week | 77 | 2 | 0.97 | 1.36 | -0.37 | -1.05 / 1.49 | 0.12 / -2.31 / -0.47 | -0.42 | 0.06 | 0.27 | -0.88 | 0.00 | 124 | NO |
| GC 7 | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 2 | 0.90 | 1.40 | -0.01 | -0.47 / 1.63 | 0.14 / -0.50 / -0.87 | -0.17 | -0.27 | 0.58 | -0.51 | 0.00 | 138 | NO |
| GC 8 | LGBM(<=2022) 3d P>=0.52 entries=week | 82 | 2 | 0.78 | 1.44 | -0.39 | -1.16 / 1.18 | 0.08 / -1.64 / -0.66 | -0.35 | 0.31 | 0.19 | -0.72 | 0.00 | 130 | NO |
| GC 9 | LGBM(<=2022) 2d P>=0.5 entries=day | 172 | 2 | 0.66 | 1.59 | -0.24 | -0.80 / 1.41 | 0.12 / -2.17 / 0.04 | -0.26 | -0.48 | 0.34 | -0.71 | 0.00 | 276 | NO |
| GC 10 (diag) | LGBM(<=2022) 5d P>=0.55 entries=week | 31 | 2 | 1.22 | 1.66 | 0.50 | 0.07 / 1.37 | 0.24 / 0.06 / -0.49 | 0.05 | -0.09 | 0.87 | -0.25 | 0.50 | 49 S | diag |
| CL 1 (diag) | LGBM(<=2022) 3d P>=0.5 entries=week | 105 | 1 | 0.11 | 1.10 | -0.21 | -0.59 / 1.15 | -0.01 / -0.44 / -0.25 | -0.13 | 0.09 | 0.29 | -0.39 | 0.00 | 168 | diag |
| CL 2 (diag) | LGBM(<=2022) 5d P>=0.55 entries=week | 33 | 1 | 0.08 | 0.73 | -0.06 | -0.20 / 1.64 | -0.02 / -0.08 / -0.26 | -0.09 | 0.25 | 0.43 | -0.37 | 0.00 | 54 S | diag |
| CL 3 (diag) | LGBM(<=2022) 5d P>=0.5 entries=week | 52 | 1 | 0.02 | 0.51 | -0.18 | -0.36 / 1.37 | -0.03 / -0.28 / -0.00 | -0.08 | 0.12 | 0.39 | -0.32 | 0.00 | 84 S | diag |
| ZN 1 | LGBM(<=2022) 5d P>=0.55 entries=day | 70 | 2 | 1.22 | 1.48 | 0.92 | 0.14 / 0.99 | 0.19 / 0.03 / 0.07 | 0.10 | 0.40 | 0.98 | -0.01 | 0.00 | 109 | NO |
| ZN 2 | LGBM(<=2022) 3d P>=0.55 entries=day | 91 | 2 | 0.91 | 1.73 | 0.83 | 0.69 / 1.30 | 0.14 / 0.09 / -0.02 | 0.04 | -0.27 | 0.99 | -0.07 | 0.25 | 133 | NO |
| ZN 3 | LGBM(<=2022) 3d P>=0.5 entries=week | 105 | 2 | 0.70 | 0.99 | 0.17 | -1.39 / 1.00 | 0.13 / -0.28 / -0.23 | -0.07 | 0.06 | 0.81 | -0.16 | 0.00 | 168 | NO |
| ZN 4 | LGBM(<=2022) 5d P>=0.52 entries=day | 83 | 2 | 0.69 | 1.06 | 0.14 | -1.30 / 0.86 | 0.09 / -0.10 / -0.21 | -0.04 | -0.19 | 0.76 | -0.16 | 0.00 | 132 | NO |
| ZN 5 | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 2 | 0.61 | 1.35 | 0.34 | -0.55 / 1.10 | 0.07 / -0.15 / -0.16 | -0.06 | -0.24 | 0.92 | -0.18 | 0.00 | 138 | NO |
| ZN 6 | LGBM(<=2022) 3d P>=0.52 entries=week | 88 | 2 | 0.59 | 1.29 | 0.12 | -1.29 / 0.91 | 0.13 / -0.20 / -0.24 | -0.05 | 0.02 | 0.79 | -0.16 | 0.75 | 136 | NO |
| ZN 7 | LGBM(<=2022) 3d P>=0.52 entries=day | 119 | 2 | 0.53 | 1.68 | 0.17 | -0.78 / 0.63 | 0.08 / -0.05 / -0.30 | -0.08 | -0.05 | 0.83 | -0.18 | 0.00 | 190 | NO |
| ZN 8 (diag) | LGBM(<=2022) 3d P>=0.55 entries=week | 51 | 2 | 1.29 | 1.21 | 1.09 | 0.67 / 1.21 | 0.21 / -0.02 / 0.05 | 0.11 | 0.15 | 1.00 | -0.02 | 0.50 | 74 S | diag |
| ZN 9 (diag) | LGBM(<=2022) 5d P>=0.55 entries=week | 34 | 2 | 0.61 | 0.93 | 0.42 | -0.49 / 1.25 | 0.07 / 0.01 / -0.01 | 0.01 | 0.01 | 0.89 | -0.13 | 1.00 | 51 S | diag |
| ZN 10 (diag) | LGBM(<=2022) 3d P>=0.5 entries=day | 129 | 1 | 0.30 | 1.18 | -0.33 | -1.96 / 0.74 | 0.10 / -0.08 / -0.43 | -0.12 | 0.15 | 0.56 | -0.22 | 0.00 | 207 | diag |
| BTC 1 (diag) | LGBM(<=2022) 3d P>=0.52 entries=day | 126 | 1 | 0.07 | 2.35 | 0.38 | 0.79 / 1.74 | 0.01 / 0.39 / -0.21 | 0.03 | -0.05 | 0.71 | -0.14 | 0.00 | 198 | diag |
| BTC 2 (diag) | LGBM(<=2022) 5d P>=0.55 entries=week | 47 | 1 | -0.10 | 2.20 | 0.01 | 0.17 / 1.37 | -0.04 / -0.22 / -0.01 | -0.05 | 0.07 | 0.52 | -0.22 | 0.00 | 66 S | diag |
| BTC 3 (diag) | LGBM(<=2022) 5d P>=0.5 entries=day | 86 | 1 | -0.19 | 2.85 | 0.05 | 0.34 / 1.68 | -0.08 / 0.23 / -0.09 | -0.05 | -0.09 | 0.39 | -0.22 | 0.00 | 138 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 46 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 5 / 5 / 5 |
| all-in uplift @20% > 0 (all scored) | 39 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 6 |
| standalone pair-window Sharpe above own random-entry null p95 | 20 |
| worst-decile corr <= +0.30 | 52 |
| plateau >= 0.75 | 15 |
| all-in uplift at 2x slippage >= +0.10 | 20 |
| small-sample (<100 trades pair window) | 7 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC LGBM(<=2022) 3d P>=0.52 entries=day (diag) | clean | 0.13 | 0.20 | -112792 | -97645 | 861819 | -180580 | 0.13 | 49.5 | 1.47 | -89979 | 257347 | -113175 |
| BTC LGBM(<=2022) 3d P>=0.52 entries=day (diag) | H1 | 2.55 | 5.70 | -94328 | -88102 | 222290 | -104540 | 3.33 | 39.3 | 3.22 | -76285 | 179115 | -86337 |
| BTC LGBM(<=2022) 3d P>=0.52 entries=day (diag) | H2 | -1.41 | -1.61 | -128438 | -98770 | 349756 | -150164 | -0.88 | 47.2 | 2.28 | -91216 | 221646 | -95076 |
| BTC LGBM(<=2022) 3d P>=0.52 entries=day (diag) | all | 0.38 | 0.60 | -115352 | -98376 | 861819 | -180580 | 0.64 | 47.6 | 1.93 | -89856 | 257347 | -113175 |
| CL LGBM(<=2022) 5d P>=0.5 entries=week (diag) | clean | 0.02 | 0.02 | -151352 | -120363 | 1067907 | -202086 | 0.01 | 25.7 | 1.43 | -85571 | 292561 | -96320 |
| CL LGBM(<=2022) 5d P>=0.5 entries=week (diag) | H1 | -2.53 | -2.58 | -128969 | -108245 | 467294 | -166605 | -0.88 | 35.7 | 2.54 | -76331 | 168748 | -78287 |
| CL LGBM(<=2022) 5d P>=0.5 entries=week (diag) | H2 | 0.06 | 0.08 | -386453 | -314580 | 606777 | -396732 | 0.07 | 19.4 | 2.48 | -81089 | 252161 | -82524 |
| CL LGBM(<=2022) 5d P>=0.5 entries=week (diag) | all | -0.18 | -0.23 | -235577 | -174856 | 1620541 | -396732 | -0.22 | 26.2 | 1.83 | -83766 | 292561 | -96320 |
| ES LGBM(<=2022) 3d P>=0.5 entries=week | clean | 1.75 | 3.39 | -104585 | -83953 | 328931 | -154653 | 4.83 | 41.9 | 1.72 | -87872 | 299561 | -112805 |
| ES LGBM(<=2022) 3d P>=0.5 entries=week | H1 | 2.12 | 3.68 | -68405 | -66760 | 76874 | -70597 | 4.67 | 28.6 | 3.17 | -72927 | 133980 | -77533 |
| ES LGBM(<=2022) 3d P>=0.5 entries=week | H2 | 0.70 | 1.17 | -101570 | -93987 | 320074 | -109519 | 0.74 | 41.7 | 2.50 | -84260 | 218953 | -86411 |
| ES LGBM(<=2022) 3d P>=0.5 entries=week | all | 1.55 | 2.83 | -103468 | -87301 | 328931 | -154653 | 6.64 | 39.9 | 2.11 | -86044 | 299561 | -112805 |
| GC LGBM(<=2022) 3d P>=0.5 entries=day | clean | 1.09 | 1.99 | -106007 | -83805 | 255940 | -194838 | 3.89 | 42.9 | 1.62 | -86754 | 262512 | -91266 |
| GC LGBM(<=2022) 3d P>=0.5 entries=day | H1 | -0.83 | -1.30 | -308411 | -281401 | 1664975 | -387635 | -0.38 | 50.0 | 1.79 | -101375 | 237756 | -114004 |
| GC LGBM(<=2022) 3d P>=0.5 entries=day | H2 | -0.53 | -0.78 | -260651 | -217882 | 1263140 | -323420 | -0.30 | 52.8 | 1.96 | -99115 | 260500 | -99564 |
| GC LGBM(<=2022) 3d P>=0.5 entries=day | all | -0.00 | -0.00 | -236887 | -197250 | 1664975 | -387635 | -0.00 | 46.4 | 1.74 | -96143 | 262512 | -114004 |
| NQ LGBM(<=2022) 3d P>=0.52 entries=day | clean | 1.14 | 1.67 | -140380 | -111643 | 517368 | -188809 | 2.00 | 36.2 | 1.66 | -84070 | 314448 | -104270 |
| NQ LGBM(<=2022) 3d P>=0.52 entries=day | H1 | 0.23 | 0.32 | -115319 | -105043 | 129390 | -116519 | 0.39 | 39.3 | 2.83 | -75066 | 139828 | -79499 |
| NQ LGBM(<=2022) 3d P>=0.52 entries=day | H2 | 2.14 | 4.07 | -166711 | -130023 | 189110 | -177773 | 5.25 | 36.1 | 2.94 | -89426 | 217182 | -95759 |
| NQ LGBM(<=2022) 3d P>=0.52 entries=day | all | 1.28 | 2.03 | -145195 | -118103 | 517368 | -188809 | 4.02 | 36.9 | 2.13 | -84753 | 314448 | -104270 |
| RTY LGBM(<=2022) 5d P>=0.52 entries=day | clean | 0.67 | 1.00 | -140643 | -105613 | 487366 | -256706 | 1.25 | 35.2 | 1.57 | -86662 | 327834 | -105055 |
| RTY LGBM(<=2022) 5d P>=0.52 entries=day | H1 | -0.12 | -0.16 | -117301 | -111475 | 180727 | -133601 | -0.14 | 32.1 | 3.04 | -74186 | 130552 | -79997 |
| RTY LGBM(<=2022) 5d P>=0.52 entries=day | H2 | -0.04 | -0.06 | -118910 | -96739 | 337936 | -154297 | -0.04 | 38.9 | 2.41 | -84092 | 200648 | -85659 |
| RTY LGBM(<=2022) 5d P>=0.52 entries=day | all | 0.40 | 0.59 | -138665 | -109574 | 487366 | -256706 | 1.17 | 35.7 | 1.97 | -85350 | 327834 | -105055 |
| YM LGBM(<=2022) 2d P>=0.52 entries=week | clean | 1.08 | 1.78 | -122214 | -98262 | 447816 | -246951 | 2.19 | 30.5 | 1.60 | -91103 | 316936 | -131264 |
| YM LGBM(<=2022) 2d P>=0.52 entries=week | H1 | 2.14 | 4.05 | -123805 | -108323 | 162240 | -162240 | 3.92 | 28.6 | 3.46 | -61686 | 147778 | -64315 |
| YM LGBM(<=2022) 2d P>=0.52 entries=week | H2 | 1.20 | 2.11 | -166160 | -112897 | 472653 | -231440 | 1.02 | 38.9 | 2.73 | -83632 | 217425 | -89849 |
| YM LGBM(<=2022) 2d P>=0.52 entries=week | all | 1.31 | 2.25 | -136484 | -106525 | 472653 | -246951 | 4.44 | 32.1 | 2.11 | -87893 | 316936 | -131264 |
| ZN LGBM(<=2022) 5d P>=0.55 entries=day | clean | 1.23 | 1.88 | -144874 | -108748 | 390577 | -236953 | 2.85 | 28.6 | 1.65 | -81580 | 293786 | -92786 |
| ZN LGBM(<=2022) 5d P>=0.55 entries=day | H1 | 0.65 | 1.25 | -46628 | -42223 | 107580 | -57202 | 0.71 | 25.0 | 2.86 | -80951 | 136649 | -84970 |
| ZN LGBM(<=2022) 5d P>=0.55 entries=day | H2 | -0.15 | -0.20 | -114035 | -82314 | 198653 | -127252 | -0.16 | 33.3 | 2.55 | -79970 | 219614 | -82524 |
| ZN LGBM(<=2022) 5d P>=0.55 entries=day | all | 0.92 | 1.39 | -130923 | -97086 | 390577 | -236953 | 2.97 | 29.2 | 2.03 | -81614 | 293786 | -92786 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES LGBM(<=2022) 3d P>=0.5 entries=week | -6.1 | -25.7 | 14.1 | 10.4 | -26.7 / 11.5 | 31.4 / 39.1 | NO |
| NQ LGBM(<=2022) 3d P>=0.52 entries=day | -7.3 | -15.7 | 14.4 | 6.5 | -11.0 / 16.5 | 26.3 / 34.9 | NO |
| RTY LGBM(<=2022) 5d P>=0.52 entries=day | -23.8 | -11.6 | 15.9 | 2.6 | -12.5 / 11.8 | 25.3 / 36.6 | NO |
| YM LGBM(<=2022) 2d P>=0.52 entries=week | -7.1 | -59.2 | 12.8 | -2.2 | -60.5 / 5.9 | 43.7 / 44.9 | NO |
| GC LGBM(<=2022) 3d P>=0.5 entries=day | -30.1 | -50.4 | -14.4 | -20.4 | 10.8 / 14.5 | -58.6 / -50.5 | NO |
| CL LGBM(<=2022) 5d P>=0.5 entries=week (diag) | -33.9 | -0.4 | 9.2 | -2.1 | -1.2 / 9.2 | 30.0 / 32.5 | NO |
| ZN LGBM(<=2022) 5d P>=0.55 entries=day | -17.3 | 7.9 | 21.4 | 6.8 | 7.2 / 19.0 | 17.2 / 23.5 | NO |
| BTC LGBM(<=2022) 3d P>=0.52 entries=day (diag) | -24.0 | -31.0 | 6.3 | 21.9 | -32.1 / 5.4 | 14.6 / 17.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 531 | 298.4 | 269.0 | 283.1 | 29.4 | 0.85 / 0.76 / 0.80 | 1075.4 / 1046.0 |
| ES 2 LGBM(<=2022) 3d P>=0.52 entries=week | positive pre-2023 | 486 | 360.0 | 330.6 | 344.8 | 29.4 | 0.97 / 0.89 / 0.93 | 1051.9 / 1022.6 |
| ES 3 LGBM(<=2022) 3d P>=0.55 entries=week | positive pre-2023 | 381 | 390.5 | 361.1 | 375.4 | 29.4 | 0.93 / 0.86 / 0.89 | 1299.3 / 1269.9 |
| ES 4 LGBM(<=2022) 2d P>=0.5 entries=week | positive pre-2023 | 532 | 194.7 | 165.4 | 179.5 | 29.4 | 0.78 / 0.66 / 0.72 | 574.4 / 545.0 |
| ES 5 LGBM(<=2022) 3d P>=0.55 entries=day | positive pre-2023 | 594 | 378.1 | 348.7 | 362.9 | 29.4 | 1.10 / 1.02 / 1.06 | 693.1 / 663.8 |
| ES 6 LGBM(<=2022) 2d P>=0.55 entries=week | positive pre-2023 | 356 | 356.4 | 327.0 | 341.0 | 29.4 | 1.18 / 1.08 / 1.13 | 541.7 / 512.3 |
| ES 7 LGBM(<=2022) 2d P>=0.52 entries=week | positive pre-2023 | 473 | 245.0 | 215.6 | 229.7 | 29.4 | 0.90 / 0.79 / 0.85 | 446.7 / 417.3 |
| ES 8 LGBM(<=2022) 2d P>=0.5 entries=day | positive pre-2023 | 883 | 149.9 | 120.5 | 134.7 | 29.4 | 0.63 / 0.51 / 0.57 | 252.0 / 222.6 |
| ES 9 (diag) LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 442 | 325.6 | 296.2 | 310.3 | 29.4 | 0.59 / 0.53 / 0.56 | 449.4 / 420.1 |
| ES 10 (diag) LGBM(<=2022) 5d P>=0.52 entries=day | positive pre-2023 | 438 | 483.8 | 454.4 | 468.6 | 29.4 | 0.94 / 0.88 / 0.91 | 403.2 / 373.8 |
| NQ 1 LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 531 | 498.4 | 484.0 | 492.5 | 14.4 | 0.93 / 0.90 / 0.92 | 2036.8 / 2022.4 |
| NQ 2 LGBM(<=2022) 3d P>=0.55 entries=week | positive pre-2023 | 437 | 737.5 | 723.2 | 731.6 | 14.4 | 1.23 / 1.21 / 1.22 | 2175.2 / 2160.8 |
| NQ 3 LGBM(<=2022) 3d P>=0.52 entries=week | positive pre-2023 | 498 | 598.0 | 583.6 | 592.1 | 14.4 | 1.09 / 1.06 / 1.08 | 1887.4 / 1873.0 |
| NQ 4 LGBM(<=2022) 2d P>=0.52 entries=week | positive pre-2023 | 494 | 516.2 | 501.8 | 510.3 | 14.4 | 1.24 / 1.20 / 1.22 | 958.9 / 944.5 |
| NQ 5 LGBM(<=2022) 3d P>=0.52 entries=day | positive pre-2023 | 647 | 430.9 | 416.6 | 425.1 | 14.4 | 0.81 / 0.78 / 0.80 | 1099.1 / 1084.7 |
| NQ 6 LGBM(<=2022) 2d P>=0.55 entries=week | positive pre-2023 | 411 | 582.8 | 568.5 | 576.9 | 14.4 | 1.29 / 1.26 / 1.28 | 875.6 / 861.2 |
| NQ 7 LGBM(<=2022) 2d P>=0.5 entries=week | positive pre-2023 | 532 | 496.0 | 481.6 | 490.1 | 14.4 | 1.21 / 1.18 / 1.20 | 749.3 / 734.9 |
| NQ 8 LGBM(<=2022) 5d P>=0.52 entries=day | positive pre-2023 | 437 | 402.5 | 388.2 | 396.7 | 14.4 | 0.47 / 0.45 / 0.46 | 1255.9 / 1241.5 |
| NQ 9 LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 442 | 668.5 | 654.1 | 662.6 | 14.4 | 0.77 / 0.75 / 0.76 | 1166.7 / 1152.4 |
| NQ 10 LGBM(<=2022) 2d P>=0.5 entries=day | positive pre-2023 | 883 | 254.1 | 239.8 | 248.3 | 14.4 | 0.70 / 0.66 / 0.68 | 526.9 / 512.6 |
| RTY 1 LGBM(<=2022) 5d P>=0.52 entries=day | positive pre-2023 | 239 | 568.7 | 554.3 | 556.5 | 14.4 | 1.19 / 1.16 / 1.17 | 351.4 / 337.0 |
| RTY 2 LGBM(<=2022) 2d P>=0.52 entries=day | positive pre-2023 | 464 | 499.6 | 485.2 | 487.4 | 14.4 | 2.55 / 2.48 / 2.49 | 75.1 / 60.7 |
| RTY 3 (diag) LGBM(<=2022) 2d P>=0.52 entries=week | positive pre-2023 | 253 | 456.6 | 442.2 | 444.4 | 14.4 | 1.90 / 1.84 / 1.85 | 314.5 / 300.1 |
| RTY 4 (diag) LGBM(<=2022) 5d P>=0.5 entries=week | positive pre-2023 | 150 | 719.3 | 704.9 | 707.1 | 14.4 | 1.26 / 1.24 / 1.24 | 422.8 / 408.4 |
| RTY 5 (diag) LGBM(<=2022) 2d P>=0.5 entries=day | positive pre-2023 | 500 | 391.5 | 377.1 | 379.3 | 14.4 | 1.97 / 1.90 / 1.91 | 139.6 / 125.2 |
| YM 1 LGBM(<=2022) 3d P>=0.55 entries=day | positive pre-2023 | 574 | 359.9 | 345.5 | 351.3 | 14.4 | 1.37 / 1.32 / 1.34 | 526.7 / 512.3 |
| YM 2 LGBM(<=2022) 2d P>=0.52 entries=week | positive pre-2023 | 420 | 370.6 | 356.2 | 362.0 | 14.4 | 1.55 / 1.49 / 1.52 | 365.1 / 350.8 |
| YM 3 LGBM(<=2022) 2d P>=0.5 entries=week | positive pre-2023 | 534 | 275.8 | 261.4 | 267.1 | 14.4 | 1.36 / 1.29 / 1.32 | 316.1 / 301.8 |
| YM 4 LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 535 | 301.6 | 287.2 | 292.9 | 14.4 | 1.04 / 0.99 / 1.01 | 351.3 / 336.9 |
| YM 5 LGBM(<=2022) 2d P>=0.5 entries=day | positive pre-2023 | 885 | 165.0 | 150.6 | 156.3 | 14.4 | 0.79 / 0.72 / 0.75 | 189.6 / 175.3 |
| YM 6 LGBM(<=2022) 2d P>=0.55 entries=day | positive pre-2023 | 694 | 294.3 | 280.0 | 285.6 | 14.4 | 1.25 / 1.19 / 1.21 | 195.3 / 180.9 |
| YM 7 LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 443 | 403.2 | 388.9 | 394.5 | 14.4 | 0.91 / 0.88 / 0.89 | 395.2 / 380.9 |
| YM 8 LGBM(<=2022) 3d P>=0.52 entries=week | positive pre-2023 | 466 | 380.1 | 365.8 | 371.5 | 14.4 | 1.21 / 1.16 / 1.18 | 191.8 / 177.5 |
| YM 9 LGBM(<=2022) 5d P>=0.52 entries=day | positive pre-2023 | 432 | 247.7 | 233.3 | 239.0 | 14.4 | 0.53 / 0.50 / 0.51 | 347.7 / 333.4 |
| YM 10 LGBM(<=2022) 5d P>=0.55 entries=day | positive pre-2023 | 401 | 417.1 | 402.8 | 408.5 | 14.4 | 0.88 / 0.85 / 0.87 | 231.5 / 217.1 |
| GC 1 LGBM(<=2022) 3d P>=0.52 entries=day | positive pre-2023 | 610 | 528.1 | 503.8 | 513.6 | 24.4 | 1.68 / 1.60 / 1.63 | 685.8 / 661.4 |
| GC 2 LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 535 | 428.6 | 404.2 | 414.0 | 24.4 | 1.35 / 1.27 / 1.30 | 720.5 / 696.1 |
| GC 3 LGBM(<=2022) 2d P>=0.5 entries=week | positive pre-2023 | 534 | 280.0 | 255.7 | 265.5 | 24.4 | 1.13 / 1.03 / 1.07 | 517.6 / 493.3 |
| GC 4 LGBM(<=2022) 3d P>=0.5 entries=day | positive pre-2023 | 662 | 369.6 | 345.2 | 355.0 | 24.4 | 1.22 / 1.14 / 1.17 | 684.3 / 660.0 |
| GC 5 LGBM(<=2022) 5d P>=0.55 entries=day | positive pre-2023 | 328 | 857.8 | 833.4 | 843.2 | 24.4 | 1.62 / 1.57 / 1.59 | 892.1 / 867.8 |
| GC 6 LGBM(<=2022) 2d P>=0.52 entries=week | positive pre-2023 | 373 | 406.8 | 382.5 | 392.3 | 24.4 | 1.45 / 1.36 / 1.40 | 463.8 / 439.4 |
| GC 7 LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 442 | 703.8 | 679.4 | 689.2 | 24.4 | 1.45 / 1.40 / 1.42 | 728.7 / 704.4 |
| GC 8 LGBM(<=2022) 3d P>=0.52 entries=week | positive pre-2023 | 395 | 552.6 | 528.2 | 538.0 | 24.4 | 1.50 / 1.44 / 1.47 | 545.0 / 520.6 |
| GC 9 LGBM(<=2022) 2d P>=0.5 entries=day | positive pre-2023 | 883 | 364.0 | 339.7 | 349.5 | 24.4 | 1.70 / 1.59 / 1.64 | 270.3 / 246.0 |
| GC 10 (diag) LGBM(<=2022) 5d P>=0.55 entries=week | positive pre-2023 | 153 | 1219.2 | 1194.8 | 1204.6 | 24.4 | 1.68 / 1.66 / 1.67 | 1670.0 / 1645.6 |
| CL 1 (diag) LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 535 | 407.4 | 383.0 | 385.8 | 24.4 | 1.17 / 1.10 / 1.11 | 90.3 / 65.9 |
| CL 2 (diag) LGBM(<=2022) 5d P>=0.55 entries=week | positive pre-2023 | 159 | 559.1 | 534.7 | 537.9 | 24.4 | 0.77 / 0.73 / 0.74 | 81.2 / 56.9 |
| CL 3 (diag) LGBM(<=2022) 5d P>=0.5 entries=week | positive pre-2023 | 268 | 371.6 | 347.2 | 350.0 | 24.4 | 0.54 / 0.51 / 0.51 | 33.1 / 8.7 |
| ZN 1 LGBM(<=2022) 5d P>=0.55 entries=day | positive pre-2023 | 373 | 263.6 | 228.0 | 222.9 | 35.6 | 1.71 / 1.48 / 1.45 | 223.7 / 188.1 |
| ZN 2 LGBM(<=2022) 3d P>=0.55 entries=day | positive pre-2023 | 466 | 208.0 | 172.4 | 167.4 | 35.6 | 2.08 / 1.73 / 1.69 | 123.5 / 87.8 |
| ZN 3 LGBM(<=2022) 3d P>=0.5 entries=week | positive pre-2023 | 536 | 127.4 | 91.8 | 86.7 | 35.6 | 1.38 / 0.99 / 0.94 | 108.9 / 73.3 |
| ZN 4 LGBM(<=2022) 5d P>=0.52 entries=day | positive pre-2023 | 423 | 173.4 | 137.7 | 132.6 | 35.6 | 1.34 / 1.06 / 1.02 | 139.3 / 103.7 |
| ZN 5 LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 443 | 214.6 | 178.9 | 173.8 | 35.6 | 1.61 / 1.35 / 1.31 | 129.2 / 93.6 |
| ZN 6 LGBM(<=2022) 3d P>=0.52 entries=week | positive pre-2023 | 416 | 165.2 | 129.5 | 124.4 | 35.6 | 1.63 / 1.29 / 1.23 | 102.1 / 66.5 |
| ZN 7 LGBM(<=2022) 3d P>=0.52 entries=day | positive pre-2023 | 609 | 183.1 | 147.5 | 142.3 | 35.6 | 2.08 / 1.68 / 1.62 | 88.6 / 53.0 |
| ZN 8 (diag) LGBM(<=2022) 3d P>=0.55 entries=week | positive pre-2023 | 239 | 186.5 | 150.8 | 145.9 | 35.6 | 1.48 / 1.21 / 1.17 | 228.2 / 192.6 |
| ZN 9 (diag) LGBM(<=2022) 5d P>=0.55 entries=week | positive pre-2023 | 184 | 228.2 | 192.6 | 187.4 | 35.6 | 1.10 / 0.93 / 0.91 | 223.3 / 187.7 |
| ZN 10 (diag) LGBM(<=2022) 3d P>=0.5 entries=day | positive pre-2023 | 665 | 136.2 | 100.6 | 95.5 | 35.6 | 1.59 / 1.18 / 1.12 | 66.7 / 31.1 |
| BTC 1 (diag) LGBM(<=2022) 3d P>=0.52 entries=day | positive pre-2023 | 83 | 2540.7 | 2486.3 | 2520.0 | 54.4 | 2.40 / 2.35 / 2.39 | 340.1 / 285.7 |
| BTC 2 (diag) LGBM(<=2022) 5d P>=0.55 entries=week | positive pre-2023 | 28 | 5383.9 | 5329.6 | 5362.8 | 54.4 | 2.22 / 2.20 / 2.21 | -372.3 / -426.7 |
| BTC 3 (diag) LGBM(<=2022) 5d P>=0.5 entries=day | positive pre-2023 | 57 | 4747.4 | 4693.0 | 4726.9 | 54.4 | 2.88 / 2.85 / 2.87 | -434.0 / -488.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 1.00); ES: 8 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.00, p(top) = 0.04); GC: 9 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.00, p(top) = 0.17); NQ: 12 cells pass the clean rule against a replicate mean of 3.3 (p(count) = 0.00, p(top) = 0.06); RTY: 2 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.83, p(top) = 0.85); YM: 10 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.00, p(top) = 0.51); ZN: 7 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.00, p(top) = 0.29).
- Of 46 selected cells, 5 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.24 (NQ LGBM(<=2022) 3d P>=0.52 entries=day); bootstrap lower bound > 0 for 6 cells; plateau >= 0.75 for 12; 2x-slippage all-in uplift >= +0.10 for 18; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell ES LGBM(<=2022) 2d P>=0.5 entries=week: uplift +0.17/+0.46/+0.23, boot lo +0.02, plateau 0.00, 2x-slip +0.20, wd corr +0.19, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES LGBM(<=2022) 2d P>=0.55 entries=week: uplift +0.11/+0.25/+0.14, boot lo -0.07, plateau 1.00, 2x-slip +0.12, wd corr +0.21, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ES LGBM(<=2022) 2d P>=0.52 entries=week: uplift +0.11/+0.45/+0.35, boot lo -0.00, plateau 1.00, 2x-slip +0.18, wd corr +0.19, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ LGBM(<=2022) 2d P>=0.52 entries=week: uplift +0.15/+0.17/+0.18, boot lo -0.05, plateau 1.00, 2x-slip +0.15, wd corr +0.08, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM LGBM(<=2022) 2d P>=0.52 entries=week: uplift +0.14/+0.63/+0.24, boot lo +0.02, plateau 1.00, 2x-slip +0.21, wd corr +0.30, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 46}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_34.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw34/ (`SW34_CO_all_selected_scored.csv`).

DONE SW34
