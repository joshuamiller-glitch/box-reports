# REPORT SW18 - long-window lead-lag, L = 30/60/120 min (D07 H3)

**Verdict: LEAD. FOUND 0, LEAD 4, INSURANCE 0.** 52 selected cells (+12 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.38; best pair-window standalone Sharpe +1.78.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Same residual definition as SW8 with L 30/60/120, k 1.5/2.5, hold 60/120/180 min, drivers as SW8.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 108 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     108 |        108 |         6 |               0.804 |                2 |          6 |            3 |
| CL    |     108 |        108 |         2 |               0.767 |                2 |          2 |            3 |
| ES    |     108 |         94 |        18 |               2.25  |                2 |         10 |            0 |
| GC    |     108 |        108 |         4 |               0.504 |                2 |          4 |            3 |
| NQ    |     108 |         96 |        32 |               2.389 |                2 |         10 |            0 |
| RTY   |     108 |        108 |        12 |               1.112 |                2 |         10 |            0 |
| YM    |     108 |        106 |        15 |               1.471 |                2 |         10 |            0 |
| ZN    |     108 |        108 |         0 |              -1.373 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   18 |             5.4  |              11 |       0    |                       1.339 |            0.64  |           0.998 |     0    |       2.25  |                1.711 |
| NQ    |     100 |                   32 |            15.61 |              25 |       0    |                       1.713 |            0.889 |           1.102 |     0    |       2.389 |                1.962 |
| RTY   |     100 |                   12 |             4.64 |              12 |       0.01 |                       0.709 |            0.623 |           0.98  |     0.29 |       1.058 |                1.526 |
| YM    |     100 |                   15 |             7.27 |              14 |       0    |                       0.869 |            0.64  |           0.895 |     0.06 |       1.471 |                1.704 |
| GC    |     100 |                    4 |             1.71 |               6 |       0.09 |                       0.374 |            0.573 |           0.947 |     0.61 |       0.504 |                1.423 |
| CL    |     100 |                    2 |             0.18 |               2 |       0.02 |                       0.76  |            0.327 |           0.572 |     0    |       0.767 |                0.572 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    6 |             6.51 |              13 |       0.66 |                       0.422 |            0.626 |           0.827 |     0.92 |       0.642 |                1.629 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | driver NQ resid30m>=1.5 dir=with X hold=180m | 387 | 2 | 2.25 | -0.39 | 1.56 | 0.87 / 0.84 | 0.38 / -0.17 / 0.29 | 0.23 | 0.15 | 1.00 | 0.07 | 0.83 | 604 | NO |
| ES 2 | driver NQ resid30m>=1.5 dir=with X hold=120m | 414 | 2 | 1.85 | -0.69 | 1.25 | 0.57 / 0.62 | 0.37 / -0.08 / 0.15 | 0.20 | 0.23 | 1.00 | 0.06 | 0.50 | 646 | NO |
| ES 3 | driver NQ resid30m>=1.5 dir=with X hold=60m | 477 | 2 | 1.58 | -0.94 | 1.46 | 1.26 / 0.04 | 0.31 / 0.16 / 0.32 | 0.19 | 0.16 | 1.00 | 0.10 | 0.50 | 743 | LEAD |
| ES 4 | driver NQ resid30m>=2.5 dir=with X hold=180m | 119 | 2 | 1.47 | -0.12 | 0.87 | 0.32 / 1.24 | 0.21 / 0.21 / -0.17 | 0.09 | -0.11 | 0.99 | -0.08 | 0.67 | 182 | NO |
| ES 5 | driver RTY resid120m>=2.5 dir=against X hold=60m | 190 | 2 | 1.28 | -0.41 | 0.59 | -0.31 / 0.96 | 0.22 / -0.17 / -0.08 | 0.02 | 0.05 | 1.00 | -0.10 | 0.17 | 285 | NO |
| ES 6 | driver NQ resid120m>=1.5 dir=with X hold=180m | 128 | 2 | 1.16 | 0.19 | 0.75 | 0.40 / 1.12 | 0.15 / -0.16 / 0.07 | 0.05 | -0.14 | 0.99 | -0.11 | 0.50 | 198 | NO |
| ES 7 | driver YM resid30m>=2.5 dir=against X hold=120m | 350 | 2 | 1.08 | -0.16 | 1.03 | 1.07 / 1.21 | 0.18 / 0.24 / 0.00 | 0.10 | -0.09 | 0.98 | -0.04 | 0.67 | 585 | NO |
| ES 8 | driver RTY resid120m>=2.5 dir=against X hold=180m | 142 | 2 | 0.99 | -0.12 | 1.02 | 0.99 / 1.13 | 0.17 / -0.05 / 0.25 | 0.12 | -0.21 | 0.97 | -0.02 | 0.33 | 217 | NO |
| ES 9 | driver NQ resid120m>=1.5 dir=with X hold=60m | 166 | 2 | 0.94 | -0.52 | 0.51 | 0.03 / 0.61 | 0.16 / -0.10 / -0.11 | -0.02 | -0.10 | 0.99 | -0.14 | 0.33 | 263 | NO |
| ES 10 | driver YM resid30m>=2.5 dir=against X hold=180m | 331 | 2 | 0.79 | 0.05 | 0.87 | 1.05 / 0.90 | 0.10 / 0.27 / -0.04 | 0.05 | -0.21 | 1.00 | -0.09 | 1.00 | 559 | NO |
| NQ 1 | driver ES resid30m>=1.5 dir=against X hold=180m | 387 | 2 | 2.39 | 0.48 | 1.73 | 1.29 / 1.24 | 0.40 / -0.05 / 0.45 | 0.34 | 0.03 | 1.00 | 0.12 | 0.50 | 604 | NO |
| NQ 2 | driver ES resid30m>=1.5 dir=against X hold=120m | 414 | 2 | 2.11 | 0.30 | 1.64 | 1.22 / 1.42 | 0.40 / 0.01 / 0.32 | 0.32 | 0.15 | 1.00 | 0.11 | 0.50 | 646 | NO |
| NQ 3 | driver ES resid30m>=1.5 dir=against X hold=60m | 477 | 2 | 1.92 | 0.25 | 1.78 | 1.59 / 1.56 | 0.36 / 0.32 / 0.34 | 0.33 | 0.14 | 1.00 | 0.13 | 0.67 | 743 | LEAD |
| NQ 4 | driver YM resid30m>=2.5 dir=against X hold=180m | 560 | 2 | 1.77 | 0.59 | 1.71 | 1.85 / 1.48 | 0.26 / 0.24 / 0.78 | 0.37 | -0.39 | 1.00 | 0.15 | 0.67 | 925 | LEAD |
| NQ 5 | driver ES resid30m>=2.5 dir=against X hold=180m | 119 | 2 | 1.73 | 0.49 | 0.98 | 0.55 / 1.35 | 0.26 / 0.36 / -0.11 | 0.18 | -0.33 | 0.96 | -0.03 | 0.67 | 182 | NO |
| NQ 6 | driver YM resid30m>=2.5 dir=against X hold=120m | 641 | 2 | 1.70 | 0.25 | 1.50 | 1.43 / 1.27 | 0.30 / 0.06 / 0.51 | 0.31 | -0.31 | 1.00 | 0.08 | 0.67 | 1049 | NO |
| NQ 7 | driver RTY resid120m>=2.5 dir=against X hold=60m | 392 | 2 | 1.50 | 0.57 | 1.32 | 1.10 / 1.01 | 0.20 / -0.03 / 0.39 | 0.18 | -0.17 | 0.99 | -0.00 | 0.50 | 582 | NO |
| NQ 8 | driver ES resid120m>=1.5 dir=against X hold=180m | 128 | 2 | 1.45 | 0.73 | 0.93 | 0.66 / 1.24 | 0.20 / -0.07 / 0.09 | 0.13 | -0.33 | 0.95 | -0.08 | 0.50 | 198 | NO |
| NQ 9 | driver ES resid120m>=1.5 dir=against X hold=60m | 166 | 2 | 1.30 | 0.38 | 0.77 | 0.37 / 1.47 | 0.21 / 0.07 / -0.09 | 0.11 | -0.12 | 0.98 | -0.08 | 0.33 | 263 | NO |
| NQ 10 | driver RTY resid120m>=2.5 dir=against X hold=120m | 320 | 2 | 1.26 | 0.74 | 1.35 | 1.46 / 1.22 | 0.16 / 0.01 / 0.44 | 0.19 | -0.35 | 1.00 | -0.01 | 0.33 | 465 | NO |
| RTY 1 | driver ES resid60m>=1.5 dir=with X hold=180m | 707 | 2 | 1.06 | -0.08 | 0.33 | -1.07 / 0.74 | 0.19 / -0.38 / -0.09 | 0.01 | -0.33 | 0.97 | -0.14 | 0.17 | 1035 | NO |
| RTY 2 | driver ES resid120m>=2.5 dir=with X hold=180m | 142 | 2 | 1.02 | -0.48 | 0.91 | 0.63 / 0.93 | 0.15 / 0.01 / -0.00 | 0.08 | 0.04 | 0.99 | -0.07 | 0.33 | 217 | NO |
| RTY 3 | driver ES resid60m>=1.5 dir=with X hold=120m | 893 | 2 | 1.00 | -0.82 | 0.06 | -1.59 / 0.54 | 0.15 / -0.53 / -0.16 | -0.07 | 0.03 | 0.97 | -0.20 | 0.00 | 1299 | NO |
| RTY 4 | driver NQ resid30m>=2.5 dir=with X hold=60m | 824 | 2 | 0.90 | -1.03 | -0.15 | -1.65 / -0.06 | 0.14 / -0.57 / -0.37 | -0.15 | -0.35 | 0.99 | -0.28 | 0.00 | 1205 | NO |
| RTY 5 | driver ES resid30m>=2.5 dir=with X hold=180m | 392 | 2 | 0.81 | -0.32 | 0.47 | 0.02 / 0.79 | 0.13 / -0.29 / 0.06 | 0.03 | -0.04 | 0.95 | -0.13 | 0.00 | 606 | NO |
| RTY 6 | driver YM resid120m>=2.5 dir=against X hold=60m | 223 | 2 | 0.74 | -0.03 | 0.91 | 1.22 / 0.79 | 0.14 / 0.10 / 0.41 | 0.15 | -0.20 | 1.00 | 0.02 | 0.33 | 326 | LEAD(gate3-7 fail: plateau ) |
| RTY 7 | driver YM resid120m>=2.5 dir=against X hold=120m | 178 | 2 | 0.62 | -0.08 | 0.72 | 0.91 / 0.93 | 0.12 / -0.04 / 0.40 | 0.13 | -0.49 | 0.99 | -0.02 | 0.33 | 260 | NO |
| RTY 8 | driver ES resid60m>=1.5 dir=with X hold=60m | 1210 | 2 | 0.42 | -1.08 | -0.71 | -2.39 / 0.31 | 0.03 / -0.61 / -0.51 | -0.27 | -0.21 | 0.89 | -0.38 | 0.00 | 1751 | NO |
| RTY 9 | driver YM resid120m>=2.5 dir=against X hold=180m | 166 | 2 | 0.33 | 0.15 | 0.33 | 0.37 / 0.96 | 0.07 / -0.18 / 0.28 | 0.06 | -0.19 | 0.90 | -0.09 | 0.33 | 245 | NO |
| RTY 10 | driver NQ resid120m>=2.5 dir=with X hold=180m | 287 | 2 | 0.20 | -0.10 | 0.55 | 1.02 / 0.85 | -0.01 / -0.25 / 0.27 | -0.00 | -0.28 | 1.00 | -0.17 | 0.83 | 423 | NO |
| YM 1 | driver NQ resid30m>=2.5 dir=with X hold=180m | 559 | 2 | 1.47 | 0.05 | 1.15 | 0.74 / 0.77 | 0.23 / -0.33 / 0.25 | 0.12 | 0.08 | 1.00 | -0.02 | 0.67 | 924 | NO |
| YM 2 | driver NQ resid30m>=2.5 dir=with X hold=120m | 640 | 2 | 1.18 | -0.29 | 0.44 | -0.42 / 0.95 | 0.20 / -0.48 / -0.15 | -0.02 | -0.06 | 0.93 | -0.18 | 0.67 | 1048 | NO |
| YM 3 | driver ES resid30m>=2.5 dir=with X hold=120m | 350 | 2 | 0.95 | -0.33 | 0.64 | 0.31 / 1.36 | 0.15 / -0.07 / -0.11 | 0.03 | 0.30 | 0.97 | -0.12 | 0.67 | 585 | NO |
| YM 4 | driver ES resid30m>=2.5 dir=with X hold=180m | 331 | 2 | 0.90 | -0.09 | 0.63 | 0.38 / 0.82 | 0.14 / -0.17 / -0.04 | 0.03 | 0.21 | 0.97 | -0.13 | 1.00 | 559 | NO |
| YM 5 | driver NQ resid60m>=2.5 dir=with X hold=120m | 479 | 2 | 0.81 | -0.08 | 0.09 | -0.55 / 0.98 | 0.10 / -0.48 / -0.41 | -0.15 | 0.24 | 0.82 | -0.35 | 0.00 | 799 | NO |
| YM 6 | driver ES resid120m>=2.5 dir=with X hold=120m | 107 | 2 | 0.80 | -0.11 | 0.92 | 1.10 / 1.72 | 0.13 / 0.10 / -0.02 | 0.10 | 0.15 | 0.96 | -0.09 | 0.50 | 195 | NO |
| YM 7 | driver RTY resid120m>=2.5 dir=with X hold=60m | 221 | 2 | 0.77 | -0.49 | 0.81 | 0.91 / 0.95 | 0.15 / -0.19 / 0.28 | 0.10 | -0.24 | 0.99 | -0.06 | 0.33 | 325 | NO |
| YM 8 | driver RTY resid120m>=2.5 dir=with X hold=120m | 178 | 2 | 0.65 | -0.35 | 0.70 | 0.81 / 1.19 | 0.13 / -0.26 / 0.32 | 0.10 | -0.28 | 0.97 | -0.07 | 0.33 | 260 | NO |
| YM 9 | driver NQ resid60m>=2.5 dir=with X hold=180m | 436 | 2 | 0.64 | 0.07 | 0.39 | 0.17 / 0.96 | 0.04 / -0.46 / 0.03 | -0.06 | 0.18 | 0.95 | -0.24 | 0.00 | 726 | NO |
| YM 10 | driver RTY resid60m>=2.5 dir=with X hold=180m | 292 | 2 | 0.53 | -0.70 | 0.51 | 0.58 / 1.36 | 0.09 / -0.35 / 0.27 | 0.05 | -0.01 | 0.90 | -0.15 | 0.67 | 450 | NO |
| GC 1 | driver ZN resid60m>=2.5 dir=against X hold=120m | 848 | 2 | 0.50 | -1.14 | -0.80 | -1.71 / 1.27 | 0.04 / -1.85 / -0.78 | -0.51 | 0.24 | 0.34 | -0.84 | 0.00 | 1267 | NO |
| GC 2 | driver 6J resid30m>=2.5 dir=against X hold=180m | 1257 | 2 | 0.49 | -0.90 | 0.32 | 0.34 / 1.31 | 0.08 / 0.68 / -1.03 | -0.17 | 0.19 | 0.92 | -0.45 | 0.00 | 2022 | NO |
| GC 3 | driver 6J resid120m>=2.5 dir=against X hold=180m | 552 | 2 | 0.33 | -0.79 | -0.11 | -0.39 / 1.10 | 0.03 / -0.46 / -0.49 | -0.21 | 0.19 | 0.69 | -0.47 | 0.00 | 889 | NO |
| GC 4 | driver 6E resid120m>=2.5 dir=against X hold=120m | 619 | 2 | 0.17 | -0.28 | -0.28 | -0.54 / 1.41 | 0.00 / -0.29 / -0.64 | -0.23 | 0.31 | 0.50 | -0.43 | 0.00 | 920 | NO |
| GC 5 (diag) | driver 6E resid120m>=2.5 dir=against X hold=60m | 782 | 1 | 0.32 | -0.51 | -0.93 | -2.01 / 1.05 | 0.00 / -1.45 / -0.61 | -0.44 | 0.39 | 0.33 | -0.60 | 0.00 | 1150 | diag |
| GC 6 (diag) | driver ZN resid120m>=2.5 dir=with X hold=60m | 662 | 1 | 0.13 | -0.70 | 0.97 | 1.62 / 1.41 | -0.00 / 0.97 / 0.21 | 0.14 | -0.31 | 0.99 | -0.08 | 0.33 | 944 | diag |
| GC 7 (diag) | driver ZN resid60m>=2.5 dir=against X hold=180m | 732 | 1 | 0.10 | -0.93 | -0.07 | -0.17 / 1.17 | -0.06 / -0.73 / -0.00 | -0.20 | 0.08 | 0.62 | -0.45 | 0.00 | 1104 | diag |
| CL 1 | driver ES resid120m>=2.5 dir=against X hold=180m | 806 | 2 | 0.77 | -0.59 | 0.26 | -0.14 / 1.22 | 0.17 / -0.21 / -0.38 | -0.13 | 0.26 | 0.97 | -0.24 | 0.00 | 1432 | NO |
| CL 2 | driver GC resid60m>=2.5 dir=against X hold=180m | 1176 | 2 | 0.75 | -0.79 | 0.45 | 0.14 / 0.78 | 0.15 / 0.10 / -0.40 | -0.14 | 0.35 | 0.99 | -0.27 | 0.17 | 2055 | NO |
| CL 3 (diag) | driver GC resid120m>=2.5 dir=against X hold=180m | 844 | 1 | 0.39 | -0.57 | 1.08 | 1.80 / 0.68 | 0.06 / 0.26 / 0.67 | 0.09 | 0.09 | 1.00 | 0.01 | 0.00 | 1492 | diag |
| CL 4 (diag) | driver ZN resid30m>=1.5 dir=with X hold=180m | 2483 | 1 | 0.14 | -1.57 | -0.22 | -0.57 / 0.55 | -0.01 / -0.09 / -0.57 | -0.36 | 0.46 | 0.98 | -0.41 | 0.00 | 4021 | diag |
| CL 5 (diag) | driver ES resid120m>=2.5 dir=against X hold=60m | 1339 | 1 | 0.12 | -0.85 | -0.27 | -0.67 / -0.12 | 0.03 / -0.50 / -0.39 | -0.44 | 0.01 | 1.00 | -0.41 | 0.00 | 2376 | diag |
| ZN 1 (diag) | driver 6J resid120m>=2.5 dir=against X hold=180m | 164 | 0 | -1.37 | -1.96 | -1.94 | -2.84 / -3.51 | -0.28 / -0.56 / -0.63 | -0.74 | -0.26 | 1.00 | -0.57 | 0.00 | 266 | diag |
| ZN 2 (diag) | driver 6E resid60m>=2.5 dir=with X hold=180m | 707 | 0 | -1.75 | -3.52 | -2.05 | -2.56 / -6.50 | -0.35 / -0.38 / -0.55 | -0.96 | -0.08 | 1.00 | -0.59 | 0.00 | 989 | diag |
| ZN 3 (diag) | driver 6J resid120m>=2.5 dir=with X hold=120m | 175 | 0 | -2.15 | -2.03 | -2.54 | -3.15 / -4.17 | -0.47 / -0.65 / -0.52 | -0.85 | 0.17 | 1.00 | -0.70 | 0.00 | 284 | diag |
| BTC 1 | driver ES resid30m>=2.5 dir=against X hold=120m | 1003 | 2 | 0.64 | 1.36 | 0.26 | -0.15 / 0.89 | 0.07 / -0.14 / -0.10 | -0.05 | 0.28 | 0.92 | -0.19 | 0.17 | 1458 | NO |
| BTC 2 | driver NQ resid60m>=2.5 dir=against X hold=120m | 709 | 2 | 0.56 | 0.81 | 0.78 | 1.06 / 1.04 | 0.12 / 0.25 / 0.07 | 0.09 | 0.31 | 1.00 | -0.04 | 0.33 | 1025 | NO |
| BTC 3 | driver GC resid30m>=2.5 dir=against X hold=180m | 1242 | 2 | 0.46 | 1.00 | -0.03 | -1.12 / 1.08 | 0.06 / 0.07 / -0.27 | -0.08 | -0.02 | 0.81 | -0.20 | 0.00 | 1843 | NO |
| BTC 4 | driver GC resid60m>=2.5 dir=with X hold=60m | 1374 | 2 | 0.38 | -1.67 | -0.05 | -0.97 / 0.74 | 0.01 / -0.45 / -0.04 | -0.15 | -0.19 | 0.94 | -0.24 | 0.00 | 1944 | NO |
| BTC 5 | driver NQ resid60m>=2.5 dir=with X hold=180m | 601 | 2 | 0.28 | -1.53 | -0.45 | -1.36 / 1.22 | -0.04 / -0.44 / -0.20 | -0.18 | -0.14 | 0.39 | -0.33 | 0.00 | 884 | NO |
| BTC 6 | driver NQ resid120m>=1.5 dir=against X hold=180m | 1247 | 2 | 0.21 | -0.02 | 0.25 | 0.36 / 0.91 | 0.03 / 0.16 / -0.08 | -0.02 | 0.39 | 0.93 | -0.15 | 0.67 | 1872 | NO |
| BTC 7 (diag) | driver ES resid60m>=2.5 dir=against X hold=120m | 658 | 1 | 0.80 | 1.31 | 1.15 | 1.70 / 0.93 | 0.12 / 0.89 / -0.02 | 0.16 | 0.27 | 1.00 | 0.02 | 0.17 | 965 | diag |
| BTC 8 (diag) | driver NQ resid30m>=2.5 dir=with X hold=60m | 1386 | 1 | 0.58 | -2.91 | -0.20 | -1.70 / 0.67 | 0.07 / -0.51 / -0.22 | -0.15 | 0.10 | 0.90 | -0.25 | 0.00 | 1966 | diag |
| BTC 9 (diag) | driver NQ resid60m>=1.5 dir=with X hold=60m | 2952 | 1 | 0.48 | -2.79 | -0.51 | -2.24 / 0.35 | 0.01 / -0.56 / -0.36 | -0.27 | -0.04 | 0.89 | -0.31 | 0.00 | 4356 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 52 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 3 / 4 / 3 / 2 |
| all-in uplift @20% > 0 (all scored) | 42 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 11 |
| standalone pair-window Sharpe above own random-entry null p95 | 46 |
| worst-decile corr <= +0.30 | 58 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 20 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC driver NQ resid60m>=2.5 dir=against X hold=120m | clean | 0.61 | 0.95 | -128041 | -100348 | 468944 | -231222 | 1.18 | 48.6 | 1.58 | -82663 | 266140 | -91095 |
| BTC driver NQ resid60m>=2.5 dir=against X hold=120m | H1 | 1.41 | 2.69 | -101887 | -92026 | 285990 | -130916 | 1.37 | 46.4 | 3.07 | -58525 | 161488 | -69460 |
| BTC driver NQ resid60m>=2.5 dir=against X hold=120m | H2 | 0.70 | 1.18 | -87655 | -78504 | 248854 | -96251 | 0.73 | 50.0 | 2.36 | -81056 | 216661 | -81280 |
| BTC driver NQ resid60m>=2.5 dir=against X hold=120m | all | 0.78 | 1.27 | -119386 | -96484 | 511603 | -231222 | 2.21 | 48.2 | 1.99 | -81568 | 266140 | -91095 |
| CL driver GC resid60m>=2.5 dir=against X hold=180m | clean | 0.85 | 1.36 | -124999 | -99332 | 386559 | -198169 | 2.02 | 47.6 | 1.61 | -80119 | 280738 | -82909 |
| CL driver GC resid60m>=2.5 dir=against X hold=180m | H1 | 0.80 | 1.19 | -88207 | -83556 | 320522 | -98400 | 0.50 | 42.9 | 2.93 | -86905 | 140633 | -89375 |
| CL driver GC resid60m>=2.5 dir=against X hold=180m | H2 | -0.00 | -0.00 | -394635 | -283935 | 810421 | -523363 | -0.00 | 47.2 | 2.09 | -152444 | 255448 | -184326 |
| CL driver GC resid60m>=2.5 dir=against X hold=180m | all | 0.45 | 0.62 | -208475 | -158573 | 810421 | -523363 | 1.16 | 46.4 | 1.92 | -98005 | 280738 | -184326 |
| ES driver NQ resid30m>=1.5 dir=with X hold=60m | clean | 1.62 | 2.78 | -114552 | -98280 | 404475 | -177200 | 3.64 | 39.0 | 1.77 | -88121 | 262917 | -102853 |
| ES driver NQ resid30m>=1.5 dir=with X hold=60m | H1 | 1.14 | 2.22 | -131912 | -112052 | 275371 | -166407 | 1.48 | 39.3 | 2.98 | -75749 | 149778 | -82055 |
| ES driver NQ resid30m>=1.5 dir=with X hold=60m | H2 | 1.39 | 2.05 | -149719 | -121745 | 532462 | -183338 | 0.86 | 38.9 | 2.62 | -93630 | 233197 | -114083 |
| ES driver NQ resid30m>=1.5 dir=with X hold=60m | all | 1.46 | 2.49 | -129557 | -108373 | 532462 | -183338 | 4.39 | 39.3 | 2.16 | -89016 | 262917 | -114083 |
| GC driver 6J resid30m>=2.5 dir=against X hold=180m | clean | 0.46 | 0.64 | -134350 | -108643 | 527077 | -303766 | 0.78 | 47.6 | 1.54 | -83255 | 262124 | -86304 |
| GC driver 6J resid30m>=2.5 dir=against X hold=180m | H1 | 1.97 | 5.43 | -226886 | -192721 | 581539 | -312360 | 2.79 | 50.0 | 3.51 | -87991 | 237256 | -104342 |
| GC driver 6J resid30m>=2.5 dir=against X hold=180m | H2 | -0.92 | -1.14 | -511085 | -464142 | 1235626 | -561333 | -0.79 | 52.8 | 1.27 | -142480 | 367531 | -155907 |
| GC driver 6J resid30m>=2.5 dir=against X hold=180m | all | 0.32 | 0.49 | -339521 | -236445 | 1365116 | -561333 | 0.77 | 49.4 | 1.77 | -107576 | 367531 | -155907 |
| NQ driver YM resid30m>=2.5 dir=against X hold=180m | clean | 1.75 | 3.48 | -92428 | -79453 | 345303 | -115401 | 4.60 | 48.6 | 1.72 | -84211 | 242266 | -89390 |
| NQ driver YM resid30m>=2.5 dir=against X hold=180m | H1 | 2.07 | 4.54 | -104300 | -94462 | 336803 | -121941 | 2.02 | 42.9 | 3.06 | -80957 | 210644 | -90649 |
| NQ driver YM resid30m>=2.5 dir=against X hold=180m | H2 | 1.81 | 3.36 | -261368 | -207811 | 498983 | -314576 | 2.61 | 38.9 | 3.08 | -102458 | 264983 | -119048 |
| NQ driver YM resid30m>=2.5 dir=against X hold=180m | all | 1.71 | 3.30 | -151547 | -117235 | 498983 | -314576 | 7.16 | 45.2 | 2.24 | -88981 | 264983 | -119048 |
| RTY driver YM resid120m>=2.5 dir=against X hold=60m | clean | 0.69 | 1.06 | -120392 | -102845 | 457935 | -158785 | 1.36 | 34.3 | 1.60 | -86604 | 272326 | -94252 |
| RTY driver YM resid120m>=2.5 dir=against X hold=60m | H1 | 0.95 | 1.87 | -91287 | -85120 | 341535 | -94619 | 0.71 | 25.0 | 2.93 | -80038 | 142842 | -92845 |
| RTY driver YM resid120m>=2.5 dir=against X hold=60m | H2 | 1.40 | 2.33 | -172793 | -120418 | 379590 | -178973 | 1.38 | 25.0 | 2.71 | -81886 | 204640 | -84118 |
| RTY driver YM resid120m>=2.5 dir=against X hold=60m | all | 0.91 | 1.47 | -130268 | -108128 | 586294 | -178973 | 2.37 | 31.0 | 2.05 | -86249 | 272326 | -94252 |
| YM driver NQ resid30m>=2.5 dir=with X hold=180m | clean | 1.46 | 2.68 | -101433 | -86779 | 364583 | -123994 | 3.64 | 41.0 | 1.69 | -85131 | 272149 | -100369 |
| YM driver NQ resid30m>=2.5 dir=with X hold=180m | H1 | -0.66 | -0.92 | -111353 | -105258 | 441212 | -120459 | -0.39 | 50.0 | 2.50 | -82248 | 195444 | -82390 |
| YM driver NQ resid30m>=2.5 dir=with X hold=180m | H2 | 1.64 | 3.31 | -108306 | -98403 | 406375 | -110948 | 1.66 | 44.4 | 2.55 | -93374 | 239567 | -95222 |
| YM driver NQ resid30m>=2.5 dir=with X hold=180m | all | 1.15 | 2.05 | -107209 | -96970 | 636769 | -123994 | 2.87 | 43.5 | 2.01 | -88627 | 272149 | -100369 |
| ZN driver 6J resid120m>=2.5 dir=against X hold=180m (diag) | clean | -1.46 | -1.78 | -152024 | -131662 | 1486596 | -176916 | -0.90 | 46.7 | 1.18 | -90595 | 269885 | -109159 |
| ZN driver 6J resid120m>=2.5 dir=against X hold=180m (diag) | H1 | -2.39 | -2.40 | -150729 | -139202 | 550039 | -167644 | -0.82 | 46.4 | 2.27 | -96442 | 171763 | -110461 |
| ZN driver 6J resid120m>=2.5 dir=against X hold=180m (diag) | H2 | -3.13 | -3.02 | -214191 | -157244 | 918401 | -225405 | -1.00 | 52.8 | 1.85 | -108956 | 252934 | -118011 |
| ZN driver 6J resid120m>=2.5 dir=against X hold=180m (diag) | all | -1.94 | -2.18 | -167908 | -141649 | 2852167 | -225405 | -0.95 | 48.2 | 1.51 | -98407 | 269885 | -118011 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES driver NQ resid30m>=1.5 dir=with X hold=60m | -3.9 | -32.3 | 7.9 | 20.7 | -8.4 / 9.3 | 22.8 / 33.6 | NO |
| NQ driver YM resid30m>=2.5 dir=against X hold=180m | 9.9 | -41.3 | 8.6 | 20.2 | 11.6 / 18.7 | 6.3 / 10.3 | NO |
| RTY driver YM resid120m>=2.5 dir=against X hold=60m | -14.5 | 3.3 | 14.9 | 7.5 | 2.5 / 13.2 | 2.1 / 25.3 | NO |
| YM driver NQ resid30m>=2.5 dir=with X hold=180m | -9.6 | -7.8 | 11.0 | 32.0 | -8.7 / 15.1 | 20.8 / 21.0 | NO |
| GC driver 6J resid30m>=2.5 dir=against X hold=180m | -18.2 | -118.0 | -48.2 | -47.5 | 18.2 / 20.7 | -57.1 / -8.8 | NO |
| CL driver GC resid60m>=2.5 dir=against X hold=180m | -19.7 | -157.8 | -12.5 | 14.7 | 23.3 / 25.1 | 8.8 / 12.0 | NO |
| ZN driver 6J resid120m>=2.5 dir=against X hold=180m (diag) | -59.5 | -39.5 | -9.9 | 22.2 | -24.7 / 0.7 | -33.0 / -6.4 | NO |
| BTC driver NQ resid60m>=2.5 dir=against X hold=120m | -17.4 | -7.5 | 19.6 | 25.8 | -8.3 / 14.7 | 45.5 / 49.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 driver NQ resid30m>=1.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 2223 | 10.9 | -18.4 | -4.7 | 29.4 | 0.23 / -0.39 / -0.10 | 202.5 / 173.1 |
| ES 2 driver NQ resid30m>=1.5 dir=with X hold=120m | gross-positive, cost-negative pre-2023 | 2479 | 3.3 | -26.0 | -12.3 | 29.4 | 0.09 / -0.69 / -0.33 | 162.2 / 132.8 |
| ES 3 driver NQ resid30m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 3042 | 6.4 | -22.9 | -9.3 | 29.4 | 0.27 / -0.94 / -0.39 | 103.1 / 73.7 |
| ES 4 driver NQ resid30m>=2.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 746 | 19.5 | -9.8 | 3.5 | 29.4 | 0.24 / -0.12 / 0.04 | 204.3 / 174.9 |
| ES 5 driver RTY resid120m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 348 | 3.3 | -26.0 | -16.6 | 29.4 | 0.03 / -0.41 / -0.27 | 107.8 / 78.4 |
| ES 6 driver NQ resid120m>=1.5 dir=with X hold=180m | positive pre-2023 | 902 | 42.8 | 13.5 | 26.7 | 29.4 | 0.61 / 0.19 / 0.38 | 154.3 / 124.9 |
| ES 7 driver YM resid30m>=2.5 dir=against X hold=120m | gross-positive, cost-negative pre-2023 | 415 | 13.5 | -15.9 | -4.9 | 29.4 | 0.14 / -0.16 / -0.05 | 99.5 / 70.1 |
| ES 8 driver RTY resid120m>=2.5 dir=against X hold=180m | gross-positive, cost-negative pre-2023 | 265 | 13.2 | -16.2 | -6.6 | 29.4 | 0.09 / -0.12 / -0.05 | 161.0 / 131.6 |
| ES 9 driver NQ resid120m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 1241 | 10.8 | -18.6 | -5.5 | 29.4 | 0.30 / -0.52 / -0.15 | 81.9 / 52.6 |
| ES 10 driver YM resid30m>=2.5 dir=against X hold=180m | positive pre-2023 | 404 | 35.6 | 6.3 | 17.2 | 29.4 | 0.29 / 0.05 / 0.14 | 91.9 / 62.6 |
| NQ 1 driver ES resid30m>=1.5 dir=against X hold=180m | positive pre-2023 | 2223 | 53.3 | 38.9 | 47.1 | 14.4 | 0.66 / 0.48 / 0.58 | 368.4 / 354.0 |
| NQ 2 driver ES resid30m>=1.5 dir=against X hold=120m | positive pre-2023 | 2478 | 33.9 | 19.5 | 27.7 | 14.4 | 0.53 / 0.30 / 0.43 | 300.4 / 286.1 |
| NQ 3 driver ES resid30m>=1.5 dir=against X hold=60m | positive pre-2023 | 3042 | 26.1 | 11.7 | 19.9 | 14.4 | 0.57 / 0.25 / 0.43 | 205.5 / 191.1 |
| NQ 4 driver YM resid30m>=2.5 dir=against X hold=180m | positive pre-2023 | 1762 | 69.6 | 55.2 | 62.8 | 14.4 | 0.74 / 0.59 / 0.67 | 231.7 / 217.3 |
| NQ 5 driver ES resid30m>=2.5 dir=against X hold=180m | positive pre-2023 | 746 | 85.6 | 71.2 | 79.2 | 14.4 | 0.59 / 0.49 / 0.55 | 427.3 / 413.0 |
| NQ 6 driver YM resid30m>=2.5 dir=against X hold=120m | positive pre-2023 | 1924 | 33.9 | 19.6 | 27.1 | 14.4 | 0.43 / 0.25 / 0.34 | 181.2 / 166.8 |
| NQ 7 driver RTY resid120m>=2.5 dir=against X hold=60m | positive pre-2023 | 896 | 68.8 | 54.5 | 60.4 | 14.4 | 0.72 / 0.57 / 0.63 | 163.7 / 149.4 |
| NQ 8 driver ES resid120m>=1.5 dir=against X hold=180m | positive pre-2023 | 901 | 107.8 | 93.5 | 101.3 | 14.4 | 0.85 / 0.73 / 0.80 | 332.6 / 318.3 |
| NQ 9 driver ES resid120m>=1.5 dir=against X hold=60m | positive pre-2023 | 1240 | 39.6 | 25.3 | 33.1 | 14.4 | 0.60 / 0.38 / 0.50 | 176.9 / 162.5 |
| NQ 10 driver RTY resid120m>=2.5 dir=against X hold=120m | positive pre-2023 | 698 | 115.1 | 100.7 | 106.6 | 14.4 | 0.84 / 0.74 / 0.78 | 183.1 / 168.8 |
| RTY 1 driver ES resid60m>=1.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 1464 | 10.9 | -3.4 | -1.5 | 14.4 | 0.27 / -0.08 / -0.03 | 63.5 / 49.2 |
| RTY 2 driver ES resid120m>=2.5 dir=with X hold=180m | negative pre-2023 | 265 | -27.6 | -41.9 | -40.7 | 14.4 | -0.31 / -0.48 / -0.46 | 102.7 / 88.4 |
| RTY 3 driver ES resid60m>=1.5 dir=with X hold=120m | negative pre-2023 | 1769 | -11.2 | -25.6 | -23.7 | 14.4 | -0.35 / -0.82 / -0.76 | 44.4 / 30.0 |
| RTY 4 driver NQ resid30m>=2.5 dir=with X hold=60m | negative pre-2023 | 1982 | -12.3 | -26.7 | -24.9 | 14.4 | -0.48 / -1.03 / -0.96 | 35.1 / 20.8 |
| RTY 5 driver ES resid30m>=2.5 dir=with X hold=180m | negative pre-2023 | 833 | -3.7 | -18.1 | -16.3 | 14.4 | -0.06 / -0.32 / -0.28 | 56.1 / 41.7 |
| RTY 6 driver YM resid120m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 537 | 13.7 | -0.7 | 1.1 | 14.4 | 0.29 / -0.03 / 0.01 | 42.9 / 28.6 |
| RTY 7 driver YM resid120m>=2.5 dir=against X hold=120m | gross-positive, cost-negative pre-2023 | 436 | 10.8 | -3.6 | -1.8 | 14.4 | 0.16 / -0.08 / -0.05 | 49.1 / 34.7 |
| RTY 8 driver ES resid60m>=1.5 dir=with X hold=60m | negative pre-2023 | 2367 | -7.7 | -22.0 | -20.2 | 14.4 | -0.38 / -1.08 / -0.99 | 21.2 / 6.8 |
| RTY 9 driver YM resid120m>=2.5 dir=against X hold=180m | positive pre-2023 | 410 | 26.3 | 12.0 | 13.7 | 14.4 | 0.34 / 0.15 / 0.17 | 33.5 / 19.2 |
| RTY 10 driver NQ resid120m>=2.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 618 | 8.0 | -6.4 | -4.8 | 14.4 | 0.14 / -0.10 / -0.08 | 24.2 / 9.8 |
| YM 1 driver NQ resid30m>=2.5 dir=with X hold=180m | positive pre-2023 | 1761 | 16.8 | 2.4 | 7.4 | 14.4 | 0.37 / 0.05 / 0.16 | 89.8 / 75.4 |
| YM 2 driver NQ resid30m>=2.5 dir=with X hold=120m | gross-positive, cost-negative pre-2023 | 1923 | 3.8 | -10.6 | -5.7 | 14.4 | 0.10 / -0.29 / -0.16 | 58.0 / 43.6 |
| YM 3 driver ES resid30m>=2.5 dir=with X hold=120m | negative pre-2023 | 415 | -10.0 | -24.3 | -20.2 | 14.4 | -0.14 / -0.33 / -0.28 | 61.9 / 47.6 |
| YM 4 driver ES resid30m>=2.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 404 | 6.8 | -7.6 | -3.5 | 14.4 | 0.07 / -0.09 / -0.04 | 65.7 / 51.3 |
| YM 5 driver NQ resid60m>=2.5 dir=with X hold=120m | gross-positive, cost-negative pre-2023 | 1324 | 10.9 | -3.5 | 1.2 | 14.4 | 0.25 / -0.08 / 0.03 | 45.3 / 30.9 |
| YM 6 driver ES resid120m>=2.5 dir=with X hold=120m | negative pre-2023 | 57 | -4.0 | -18.4 | -14.8 | 14.4 | -0.02 / -0.11 / -0.09 | 82.1 / 67.7 |
| YM 7 driver RTY resid120m>=2.5 dir=with X hold=60m | negative pre-2023 | 552 | -11.1 | -25.4 | -21.6 | 14.4 | -0.22 / -0.49 / -0.42 | 46.7 / 32.3 |
| YM 8 driver RTY resid120m>=2.5 dir=with X hold=120m | negative pre-2023 | 446 | -11.5 | -25.8 | -22.0 | 14.4 | -0.16 / -0.35 / -0.30 | 57.1 / 42.7 |
| YM 9 driver NQ resid60m>=2.5 dir=with X hold=180m | positive pre-2023 | 1238 | 18.1 | 3.8 | 8.5 | 14.4 | 0.35 / 0.07 / 0.16 | 46.4 / 32.1 |
| YM 10 driver RTY resid60m>=2.5 dir=with X hold=180m | negative pre-2023 | 758 | -34.8 | -49.2 | -45.4 | 14.4 | -0.50 / -0.70 / -0.64 | 42.3 / 28.0 |
| GC 1 driver ZN resid60m>=2.5 dir=against X hold=120m | negative pre-2023 | 3531 | -14.9 | -39.3 | -29.6 | 24.4 | -0.43 / -1.14 / -0.86 | 47.9 / 23.5 |
| GC 2 driver 6J resid30m>=2.5 dir=against X hold=180m | negative pre-2023 | 4914 | -4.1 | -28.4 | -18.9 | 24.4 | -0.13 / -0.90 / -0.60 | 43.1 / 18.8 |
| GC 3 driver 6J resid120m>=2.5 dir=against X hold=180m | negative pre-2023 | 1793 | -21.0 | -45.3 | -36.1 | 24.4 | -0.37 / -0.79 / -0.63 | 44.7 / 20.4 |
| GC 4 driver 6E resid120m>=2.5 dir=against X hold=120m | gross-positive, cost-negative pre-2023 | 2438 | 13.4 | -11.0 | -1.6 | 24.4 | 0.34 / -0.28 / -0.04 | 25.1 / 0.8 |
| GC 5 (diag) driver 6E resid120m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 3027 | 11.4 | -13.0 | -3.6 | 24.4 | 0.44 / -0.51 / -0.14 | 30.2 / 5.8 |
| GC 6 (diag) driver ZN resid120m>=2.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 2446 | 2.8 | -21.6 | -12.0 | 24.4 | 0.08 / -0.70 / -0.39 | 30.3 / 6.0 |
| GC 7 (diag) driver ZN resid60m>=2.5 dir=against X hold=180m | negative pre-2023 | 3131 | -16.0 | -40.4 | -30.8 | 24.4 | -0.37 / -0.93 / -0.71 | 27.2 / 2.9 |
| CL 1 driver ES resid120m>=2.5 dir=against X hold=180m | negative pre-2023 | 2709 | -2.8 | -27.2 | -25.6 | 24.4 | -0.06 / -0.59 / -0.55 | 49.4 / 25.1 |
| CL 2 driver GC resid60m>=2.5 dir=against X hold=180m | gross-positive, cost-negative pre-2023 | 5678 | 2.7 | -21.6 | -18.7 | 24.4 | 0.10 / -0.79 / -0.68 | 46.0 / 21.7 |
| CL 3 (diag) driver GC resid120m>=2.5 dir=against X hold=180m | gross-positive, cost-negative pre-2023 | 3949 | 4.2 | -20.2 | -17.2 | 24.4 | 0.12 / -0.57 / -0.49 | 37.6 / 13.2 |
| CL 4 (diag) driver ZN resid30m>=1.5 dir=with X hold=180m | negative pre-2023 | 12588 | -1.9 | -26.3 | -23.5 | 24.4 | -0.11 / -1.57 / -1.40 | 26.7 / 2.3 |
| CL 5 (diag) driver ES resid120m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 4193 | 4.2 | -20.2 | -18.7 | 24.4 | 0.17 / -0.85 / -0.79 | 27.1 / 2.7 |
| ZN 1 (diag) driver 6J resid120m>=2.5 dir=against X hold=180m | negative pre-2023 | 801 | -5.0 | -40.6 | -46.3 | 35.6 | -0.25 / -1.96 / -2.20 | 12.0 / -23.6 |
| ZN 2 (diag) driver 6E resid60m>=2.5 dir=with X hold=180m | gross-positive, cost-negative pre-2023 | 4134 | 2.4 | -33.2 | -38.5 | 35.6 | 0.26 / -3.52 / -4.05 | 19.7 / -15.9 |
| ZN 3 (diag) driver 6J resid120m>=2.5 dir=with X hold=120m | gross-positive, cost-negative pre-2023 | 869 | 0.8 | -34.8 | -40.6 | 35.6 | 0.05 / -2.03 / -2.30 | 3.7 / -31.9 |
| BTC 1 driver ES resid30m>=2.5 dir=against X hold=120m | positive pre-2023 | 573 | 184.6 | 130.3 | 162.2 | 54.4 | 1.92 / 1.36 / 1.69 | 148.5 / 94.1 |
| BTC 2 driver NQ resid60m>=2.5 dir=against X hold=120m | positive pre-2023 | 366 | 164.6 | 110.3 | 142.0 | 54.4 | 1.20 / 0.81 / 1.04 | 171.5 / 117.2 |
| BTC 3 driver GC resid30m>=2.5 dir=against X hold=180m | positive pre-2023 | 772 | 139.2 | 84.8 | 116.7 | 54.4 | 1.64 / 1.00 / 1.38 | 143.8 / 89.4 |
| BTC 4 driver GC resid60m>=2.5 dir=with X hold=60m | negative pre-2023 | 833 | -63.5 | -117.9 | -86.5 | 54.4 | -0.90 / -1.67 / -1.22 | 98.6 / 44.2 |
| BTC 5 driver NQ resid60m>=2.5 dir=with X hold=180m | negative pre-2023 | 320 | -208.0 | -262.4 | -230.5 | 54.4 | -1.22 / -1.53 / -1.35 | 81.0 / 26.7 |
| BTC 6 driver NQ resid120m>=1.5 dir=against X hold=180m | gross-positive, cost-negative pre-2023 | 761 | 52.3 | -2.1 | 30.0 | 54.4 | 0.62 / -0.02 / 0.36 | 95.4 / 41.0 |
| BTC 7 (diag) driver ES resid60m>=2.5 dir=against X hold=120m | positive pre-2023 | 321 | 255.3 | 200.9 | 233.0 | 54.4 | 1.66 / 1.31 / 1.52 | 205.7 / 151.3 |
| BTC 8 (diag) driver NQ resid30m>=2.5 dir=with X hold=60m | negative pre-2023 | 735 | -121.4 | -175.8 | -143.9 | 54.4 | -2.04 / -2.91 / -2.41 | 119.0 / 64.6 |
| BTC 9 (diag) driver NQ resid60m>=1.5 dir=with X hold=60m | negative pre-2023 | 1765 | -43.1 | -97.4 | -65.4 | 54.4 | -1.25 / -2.79 / -1.88 | 87.3 / 32.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 6 cells pass the clean rule against a replicate mean of 6.5 (p(count) = 0.66, p(top) = 0.92); CL: 2 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.02, p(top) = 0.00); ES: 18 cells pass the clean rule against a replicate mean of 5.4 (p(count) = 0.00, p(top) = 0.00); GC: 4 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.09, p(top) = 0.61); NQ: 32 cells pass the clean rule against a replicate mean of 15.6 (p(count) = 0.00, p(top) = 0.00); RTY: 12 cells pass the clean rule against a replicate mean of 4.6 (p(count) = 0.01, p(top) = 0.29); YM: 15 cells pass the clean rule against a replicate mean of 7.3 (p(count) = 0.00, p(top) = 0.06); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 52 selected cells, 4 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.38 (NQ driver YM resid30m>=2.5 dir=against X hold=180m); bootstrap lower bound > 0 for 9 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 18; gate_add PASS at some share: 1 (cell-share pairs).
- Gate-3 cell ES driver NQ resid30m>=1.5 dir=with X hold=60m: uplift +0.31/+0.16/+0.32, boot lo +0.10, plateau 0.50, 2x-slip +0.19, wd corr +0.16, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ driver ES resid30m>=1.5 dir=against X hold=60m: uplift +0.36/+0.32/+0.34, boot lo +0.13, plateau 0.67, 2x-slip +0.33, wd corr +0.14, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ driver YM resid30m>=2.5 dir=against X hold=180m: uplift +0.26/+0.24/+0.78, boot lo +0.15, plateau 0.67, 2x-slip +0.37, wd corr -0.39, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY driver YM resid120m>=2.5 dir=against X hold=60m: uplift +0.14/+0.10/+0.41, boot lo +0.02, plateau 0.33, 2x-slip +0.15, wd corr -0.20, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 18, 'positive pre-2023': 18, 'negative pre-2023': 16}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_18.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw18/ (`SW18_CO_all_selected_scored.csv`).

DONE SW18
