# REPORT SW23 - return-persistence (lag-1 autocorrelation) regime gating of trend and fade signals (D02 H2/H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 42 selected cells (+16 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.17; best pair-window standalone Sharpe +1.02.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: rolling lag-1 autocorrelation of 5-min returns over the trailing 48 completed bars gates 5-min trend signals (ST/Donchian/EMA) and fade signals (VWAP-band/RSI): hi (>= 0.05/0.10) or lo (<= -0.05/-0.10), with or against, hold 60/180 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument = 6 signals x 2 directions x 2 holds x 4 regimes.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        13 |               1.379 |                2 |         10 |            0 |
| CL    |      96 |         96 |         9 |               0.845 |                2 |          9 |            1 |
| ES    |      96 |         96 |         2 |               0.757 |                2 |          2 |            3 |
| GC    |      96 |         96 |         2 |               1.415 |                2 |          2 |            3 |
| NQ    |      96 |         96 |        12 |               1.029 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         7 |               1.024 |                2 |          7 |            3 |
| YM    |      96 |         96 |         2 |               0.84  |                2 |          2 |            3 |
| ZN    |      96 |         88 |         0 |              -0.35  |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    2 |             1.81 |               6 |       0.57 |                       0.509 |            0.548 |           1.093 |     0.44 |       0.555 |                1.378 |
| NQ    |     100 |                   12 |            11.88 |              20 |       0.48 |                       0.624 |            0.792 |           1.062 |     0.84 |       0.999 |                1.946 |
| RTY   |     100 |                    7 |             3.39 |               9 |       0.06 |                       0.7   |            0.599 |           0.897 |     0.23 |       1.024 |                1.466 |
| YM    |     100 |                    2 |             3.39 |              10 |       0.85 |                       0.589 |            0.568 |           0.948 |     0.41 |       0.655 |                1.446 |
| GC    |     100 |                    2 |             3.16 |              10 |       0.85 |                       1.223 |            0.614 |           1.197 |     0.03 |       1.415 |                1.513 |
| CL    |     100 |                    9 |             0.92 |               5 |       0    |                       0.456 |            0.538 |           1.305 |     0.35 |       0.845 |                1.326 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                   13 |             9.23 |              16 |       0.12 |                       0.654 |            0.685 |           0.9   |     0.57 |       1.379 |                1.929 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | 399 | 2 | 0.55 | -0.56 | -0.36 | -1.47 / 0.27 | 0.06 / -0.38 / -0.59 | -0.23 | 0.52 | 0.91 | -0.34 | 0.00 | 584 | NO |
| ES 2 | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | 328 | 2 | 0.46 | -0.56 | -0.35 | -1.61 / 1.20 | 0.05 / 0.02 / -0.62 | -0.17 | 0.04 | 0.68 | -0.29 | 0.00 | 492 | NO |
| ES 3 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | 282 | 1 | 0.76 | -0.40 | -0.28 | -1.61 / 0.42 | 0.08 / -0.51 / -0.52 | -0.20 | 0.32 | 0.88 | -0.32 | 0.00 | 417 | diag |
| ES 4 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | 230 | 1 | 0.58 | -0.53 | -0.19 | -1.60 / 1.00 | 0.06 / -0.05 / -0.46 | -0.12 | -0.00 | 0.78 | -0.24 | 0.00 | 349 | diag |
| ES 5 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | 554 | 1 | 0.32 | -1.17 | 0.26 | 0.13 / 0.40 | 0.00 / -0.03 / -0.04 | -0.10 | -0.03 | 1.00 | -0.14 | 0.00 | 860 | diag |
| NQ 1 | 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | 679 | 2 | 1.00 | -0.18 | 0.34 | -0.29 / 1.58 | 0.24 / -0.69 / 0.24 | 0.09 | 0.35 | 0.79 | -0.10 | 0.50 | 1058 | NO |
| NQ 2 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | 490 | 2 | 0.99 | -0.66 | 0.50 | -0.86 / 1.34 | 0.12 / -0.19 / -0.10 | 0.00 | 0.46 | 0.92 | -0.11 | 0.50 | 763 | NO |
| NQ 3 | 5m st[14, 2.0] dir=with hold=180m ac48 lo-0.1 | 1098 | 2 | 0.91 | -0.17 | -0.09 | -1.20 / 1.28 | 0.13 / -0.55 / -0.29 | -0.08 | 0.65 | 0.69 | -0.25 | 0.00 | 1725 | NO |
| NQ 4 | 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | 498 | 2 | 0.89 | -0.63 | 0.23 | -0.49 / 1.25 | 0.21 / -0.68 / 0.08 | 0.05 | -0.01 | 0.75 | -0.14 | 0.50 | 773 | NO |
| NQ 5 | 5m st[14, 2.0] dir=with hold=180m ac48 lo-0.05 | 1364 | 2 | 0.79 | -0.57 | 0.64 | 0.55 / 1.17 | 0.12 / -0.12 / 0.22 | 0.08 | 0.56 | 0.96 | -0.06 | 0.25 | 2174 | NO |
| NQ 6 | 5m vwz[2.0, 'globex'] dir=against hold=60m ac48 lo-0.05 | 1270 | 2 | 0.44 | -0.48 | -0.02 | -0.85 / 0.99 | 0.02 / -0.21 / -0.32 | -0.13 | 0.21 | 0.81 | -0.25 | 0.00 | 1946 | NO |
| NQ 7 | 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | 618 | 2 | 0.41 | 0.16 | 0.48 | 0.62 / 1.40 | 0.06 / 0.17 / 0.19 | 0.09 | -0.20 | 0.93 | -0.10 | 0.25 | 993 | NO |
| NQ 8 | 5m emax[9, 21] dir=with hold=60m ac48 lo-0.05 | 1848 | 2 | 0.32 | -0.80 | 0.59 | 1.03 / 0.96 | 0.01 / 0.45 / -0.02 | -0.00 | 0.47 | 1.00 | -0.13 | 0.25 | 2910 | NO |
| NQ 9 | 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.05 | 806 | 2 | 0.29 | 0.12 | 0.15 | 0.05 / 1.31 | 0.04 / -0.03 / 0.19 | 0.03 | 0.02 | 0.74 | -0.15 | 0.25 | 1308 | NO |
| NQ 10 | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | 241 | 2 | 0.21 | -0.04 | 0.16 | -0.04 / 0.99 | 0.01 / 0.16 / -0.22 | -0.02 | 0.33 | 0.73 | -0.15 | 0.00 | 346 | NO |
| RTY 1 | 5m don[20] dir=against hold=180m ac48 lo-0.1 | 1398 | 2 | 1.02 | -0.41 | 0.61 | 0.13 / 0.60 | 0.14 / -0.19 / 0.22 | -0.00 | -0.10 | 0.99 | -0.11 | 0.17 | 2174 | NO |
| RTY 2 | 5m don[20] dir=with hold=180m ac48 hi0.05 | 1226 | 2 | 0.90 | -0.38 | 0.35 | -0.27 / 0.76 | 0.12 / 0.59 / -0.58 | -0.06 | -0.20 | 0.98 | -0.19 | 0.00 | 1987 | NO |
| RTY 3 | 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | 601 | 2 | 0.84 | 0.89 | 0.67 | 0.47 / 0.95 | 0.11 / -0.10 / 0.39 | 0.07 | 0.02 | 0.99 | -0.06 | 0.12 | 972 | NO |
| RTY 4 | 5m don[20] dir=with hold=180m ac48 hi0.1 | 919 | 2 | 0.71 | -0.10 | 0.13 | -0.63 / 0.93 | 0.07 / 0.22 / -0.47 | -0.12 | -0.04 | 0.91 | -0.24 | 0.00 | 1473 | NO |
| RTY 5 | 5m st[14, 2.0] dir=with hold=180m ac48 hi0.1 | 784 | 2 | 0.66 | -0.17 | -0.01 | -0.99 / 0.74 | 0.06 / -0.67 / 0.14 | -0.12 | 0.08 | 0.83 | -0.23 | 0.00 | 1270 | NO |
| RTY 6 | 5m don[20] dir=against hold=180m ac48 lo-0.05 | 1667 | 2 | 0.61 | -0.62 | 0.46 | 0.34 / 0.83 | 0.04 / -0.07 / 0.12 | -0.08 | -0.04 | 0.99 | -0.17 | 0.17 | 2658 | NO |
| RTY 7 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | 419 | 2 | 0.15 | -0.17 | -0.17 | -0.55 / 0.47 | -0.03 / -0.27 / -0.10 | -0.15 | -0.26 | 0.94 | -0.29 | 0.00 | 661 | NO |
| RTY 8 (diag) | 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.05 | 773 | 1 | 0.72 | 0.84 | 0.35 | -0.14 / 0.81 | 0.10 / -0.17 / 0.16 | -0.01 | -0.14 | 0.99 | -0.13 | 0.38 | 1257 | diag |
| RTY 9 (diag) | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.05 | 452 | 1 | 0.43 | -0.05 | 0.04 | -0.34 / 1.28 | 0.02 / -0.19 / -0.10 | -0.11 | -0.25 | 0.84 | -0.25 | 0.00 | 741 | diag |
| RTY 10 (diag) | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | 353 | 1 | 0.11 | 0.19 | 0.30 | 0.58 / 1.15 | -0.03 / 0.06 / 0.24 | -0.02 | 0.26 | 0.90 | -0.17 | 0.33 | 592 | diag |
| YM 1 | 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | 1016 | 2 | 0.66 | -0.77 | 0.34 | -0.18 / 0.99 | 0.06 / -0.17 / -0.16 | -0.07 | -0.25 | 0.93 | -0.20 | 0.00 | 1678 | NO |
| YM 2 | 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | 613 | 2 | 0.52 | -0.19 | -0.15 | -0.96 / 1.02 | 0.09 / -0.57 / -0.19 | -0.12 | 0.19 | 0.74 | -0.28 | 0.00 | 984 | NO |
| YM 3 (diag) | 5m don[20] dir=with hold=180m ac48 lo-0.05 | 1722 | 1 | 0.84 | -1.45 | 0.27 | -0.54 / 0.88 | 0.08 / -0.36 / -0.20 | -0.14 | 0.04 | 0.91 | -0.22 | 0.00 | 2714 | diag |
| YM 4 (diag) | 5m st[14, 2.0] dir=with hold=180m ac48 hi0.1 | 742 | 1 | 0.78 | -0.02 | -0.19 | -1.44 / 1.11 | 0.10 / -0.00 / -0.61 | -0.13 | -0.00 | 0.61 | -0.28 | 0.00 | 1254 | diag |
| YM 5 (diag) | 5m emax[9, 21] dir=with hold=180m ac48 lo-0.05 | 1276 | 1 | 0.59 | -0.86 | 0.33 | 0.03 / 0.88 | 0.07 / -0.26 / 0.05 | -0.07 | 0.22 | 0.95 | -0.17 | 0.50 | 1997 | diag |
| GC 1 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | 342 | 2 | 1.41 | -0.61 | 0.54 | 0.04 / 1.04 | 0.24 / -1.35 / 0.32 | -0.05 | -0.66 | 1.00 | -0.30 | 0.50 | 519 | NO |
| GC 2 | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | 314 | 2 | 1.03 | -0.49 | 0.63 | 0.59 / 1.40 | 0.11 / -0.95 / 0.63 | 0.02 | -0.47 | 0.96 | -0.38 | 0.33 | 469 | NO |
| GC 3 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | 229 | 1 | 1.01 | -0.80 | 0.86 | 0.90 / 1.15 | 0.14 / 0.06 / 0.07 | 0.08 | -0.22 | 0.99 | -0.14 | 0.50 | 360 | diag |
| GC 4 (diag) | 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 hi0.05 | 644 | 1 | 0.72 | -0.71 | 0.76 | 0.86 / 1.40 | 0.07 / 0.69 / -0.10 | 0.04 | -0.08 | 0.99 | -0.18 | 0.50 | 979 | diag |
| GC 5 (diag) | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | 287 | 1 | 0.62 | -0.18 | 0.51 | 0.67 / 1.35 | 0.11 / -0.53 / 0.15 | 0.00 | 0.07 | 0.91 | -0.32 | 0.50 | 441 | diag |
| CL 1 | 5m rsi[14, 30] dir=against hold=180m ac48 hi0.05 | 725 | 2 | 0.85 | -0.95 | -0.71 | -1.98 / 0.99 | 0.13 / -0.17 / -1.24 | -0.35 | -0.19 | 0.56 | -0.51 | 0.00 | 1184 | NO |
| CL 2 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | 215 | 2 | 0.58 | -0.01 | 0.20 | 0.03 / 0.68 | 0.09 / -0.30 / -0.51 | -0.23 | 0.29 | 0.99 | -0.45 | 0.00 | 346 | NO |
| CL 3 | 5m rsi[14, 30] dir=against hold=180m ac48 hi0.1 | 550 | 2 | 0.56 | -0.68 | -0.20 | -0.84 / 0.82 | 0.07 / 0.07 / -0.75 | -0.23 | 0.03 | 0.80 | -0.40 | 0.00 | 887 | NO |
| CL 4 | 5m rsi[14, 30] dir=against hold=60m ac48 hi0.05 | 972 | 2 | 0.50 | -1.52 | -0.03 | -0.52 / 0.37 | 0.05 / -0.29 / -0.43 | -0.31 | -0.27 | 1.00 | -0.32 | 0.00 | 1593 | NO |
| CL 5 | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.05 | 365 | 2 | 0.47 | -0.61 | -0.43 | -1.32 / 0.96 | 0.10 / -0.04 / -0.88 | -0.25 | -0.16 | 0.65 | -0.39 | 0.00 | 623 | NO |
| CL 6 | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | 273 | 2 | 0.32 | -0.71 | -0.30 | -1.10 / 0.92 | 0.04 / -0.10 / -0.56 | -0.20 | -0.22 | 0.71 | -0.34 | 0.00 | 463 | NO |
| CL 7 | 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 lo-0.1 | 749 | 2 | 0.30 | -0.90 | -0.22 | -0.69 / 0.99 | 0.06 / -0.24 / -0.49 | -0.24 | 0.08 | 0.85 | -0.33 | 0.00 | 1155 | NO |
| CL 8 | 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 hi0.1 | 485 | 2 | 0.28 | -0.61 | -0.17 | -0.54 / 1.06 | 0.03 / -0.14 / -0.72 | -0.28 | 0.14 | 0.82 | -0.43 | 0.00 | 769 | NO |
| CL 9 | 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | 711 | 2 | 0.25 | -1.03 | 0.34 | 0.42 / 0.44 | 0.01 / -0.10 / 0.01 | -0.18 | -0.12 | 1.00 | -0.23 | 0.00 | 1155 | NO |
| CL 10 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | 305 | 1 | 0.58 | -0.46 | 0.04 | -0.36 / 1.02 | 0.08 / -0.26 / -0.54 | -0.23 | 0.26 | 0.96 | -0.39 | 0.00 | 489 | diag |
| ZN 1 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | 43 | 1 | -0.35 | -1.03 | -0.54 | -1.36 / -0.59 | -0.09 / -0.11 / -0.20 | -0.22 | -0.18 | 1.00 | -0.28 | 0.00 | 63 S | diag |
| ZN 2 (diag) | 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | 152 | 1 | -0.72 | -0.87 | -0.93 | -1.15 / -1.39 | -0.20 / -0.29 / -0.08 | -0.46 | 0.25 | 1.00 | -0.38 | 0.00 | 212 | diag |
| ZN 3 (diag) | 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | 68 | 0 | -0.78 | -1.45 | -1.12 | -1.62 / -1.12 | -0.20 / -0.78 / -0.32 | -0.43 | -0.07 | 1.00 | -0.52 | 0.00 | 104 | diag |
| BTC 1 | 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | 861 | 2 | 1.38 | -0.47 | 1.02 | 0.27 / 0.85 | 0.25 / -0.32 / 0.22 | 0.08 | 0.03 | 1.00 | -0.02 | 0.25 | 1400 | NO |
| BTC 2 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | 414 | 2 | 0.83 | 0.76 | -0.04 | -1.47 / 1.15 | 0.09 / -0.26 / -0.32 | -0.11 | -0.22 | 0.74 | -0.24 | 0.00 | 640 | NO |
| BTC 3 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | 199 | 2 | 0.82 | -1.14 | 0.21 | -1.05 / 1.13 | 0.15 / -0.22 / -0.21 | -0.01 | -0.11 | 0.88 | -0.18 | 0.67 | 321 | NO |
| BTC 4 | 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 lo-0.1 | 579 | 2 | 0.76 | 0.85 | 0.19 | -0.75 / 1.23 | 0.09 / -0.06 / -0.13 | -0.03 | -0.10 | 0.85 | -0.17 | 0.33 | 880 | NO |
| BTC 5 | 5m rsi[14, 30] dir=against hold=180m ac48 lo-0.1 | 561 | 2 | 0.75 | -0.01 | 0.71 | 0.72 / 1.38 | 0.13 / 0.52 / -0.29 | 0.05 | 0.14 | 0.96 | -0.09 | 0.25 | 872 | NO |
| BTC 6 | 5m emax[9, 21] dir=against hold=180m ac48 lo-0.1 | 917 | 2 | 0.63 | -1.70 | 0.33 | -0.02 / 1.10 | 0.17 / -0.02 / -0.24 | 0.01 | -0.18 | 0.93 | -0.13 | 0.38 | 1437 | NO |
| BTC 7 | 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | 314 | 2 | 0.42 | 0.60 | -0.01 | -0.96 / 1.24 | 0.04 / -0.51 / 0.03 | -0.06 | -0.10 | 0.65 | -0.21 | 0.00 | 476 | NO |
| BTC 8 | 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.1 | 304 | 2 | 0.41 | 0.93 | -0.13 | -0.92 / 1.19 | 0.01 / -0.26 / -0.19 | -0.12 | -0.09 | 0.78 | -0.26 | 0.00 | 480 | NO |
| BTC 9 | 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 hi0.1 | 120 | 2 | 0.30 | 1.66 | -0.22 | -1.30 / 1.54 | 0.02 / -0.22 / -0.11 | -0.07 | -0.15 | 0.44 | -0.23 | 0.00 | 181 | NO |
| BTC 10 | 5m emax[9, 21] dir=with hold=180m ac48 hi0.1 | 442 | 2 | 0.26 | 0.23 | 0.50 | 0.95 / 0.76 | -0.02 / 0.10 / -0.04 | -0.02 | -0.30 | 0.93 | -0.18 | 0.38 | 729 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 42 |
| diagnostic cells read | 16 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 25 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 22 |
| worst-decile corr <= +0.30 | 50 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 1 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | clean | 1.43 | 2.45 | -116414 | -97891 | 524246 | -184500 | 2.47 | 43.8 | 1.71 | -88360 | 246386 | -95270 |
| BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | H1 | -0.53 | -0.77 | -134249 | -114374 | 390787 | -162447 | -0.36 | 64.3 | 2.51 | -83339 | 161616 | -88672 |
| BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | H2 | 1.22 | 2.21 | -83745 | -62601 | 161098 | -112169 | 1.71 | 44.4 | 2.70 | -83063 | 199152 | -90737 |
| BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | all | 1.02 | 1.69 | -119906 | -97853 | 538763 | -184500 | 2.65 | 47.6 | 2.06 | -87859 | 246386 | -95270 |
| CL 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | clean | 0.27 | 0.44 | -116498 | -97352 | 559688 | -146530 | 0.44 | 53.3 | 1.47 | -88380 | 339678 | -102536 |
| CL 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | H1 | -0.51 | -0.75 | -67894 | -64585 | 291493 | -75253 | -0.27 | 53.6 | 2.72 | -87710 | 151573 | -89039 |
| CL 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | H2 | 0.68 | 1.20 | -273564 | -229479 | 496682 | -294484 | 1.05 | 50.0 | 2.49 | -107288 | 228612 | -118805 |
| CL 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | all | 0.34 | 0.57 | -169427 | -131527 | 559688 | -294484 | 1.23 | 53.0 | 1.89 | -95245 | 339678 | -118805 |
| ES 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | clean | 0.49 | 0.83 | -116943 | -96329 | 686142 | -179675 | 0.64 | 46.7 | 1.51 | -86509 | 270758 | -100803 |
| ES 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | H1 | 0.36 | 0.75 | -75084 | -68674 | 335942 | -82658 | 0.26 | 53.6 | 2.85 | -76035 | 214909 | -80111 |
| ES 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | H2 | -3.03 | -3.02 | -195865 | -176923 | 1103862 | -196594 | -0.96 | 55.6 | 1.87 | -81102 | 221417 | -82051 |
| ES 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | all | -0.35 | -0.50 | -146506 | -118331 | 1550922 | -196594 | -0.34 | 50.0 | 1.80 | -84815 | 270758 | -100803 |
| GC 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | clean | 1.03 | 1.94 | -101581 | -86391 | 337333 | -159693 | 2.78 | 46.7 | 1.57 | -79574 | 273730 | -94627 |
| GC 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | H1 | -0.33 | -0.39 | -587045 | -449682 | 1390343 | -984952 | -0.21 | 42.9 | 1.88 | -148391 | 346262 | -208210 |
| GC 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | H2 | 1.43 | 2.50 | -378667 | -271618 | 724686 | -504761 | 1.95 | 41.7 | 3.11 | -76606 | 173311 | -79774 |
| GC 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | all | 0.63 | 0.88 | -306522 | -219953 | 1584663 | -984952 | 1.29 | 45.2 | 1.97 | -94889 | 374520 | -208210 |
| NQ 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | clean | 0.98 | 1.70 | -118273 | -94524 | 348784 | -158395 | 2.54 | 47.6 | 1.70 | -80739 | 246641 | -85730 |
| NQ 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | H1 | -2.73 | -3.16 | -143714 | -124159 | 743945 | -195857 | -0.91 | 71.4 | 2.14 | -86567 | 175375 | -89867 |
| NQ 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | H2 | 0.71 | 1.13 | -265588 | -187856 | 577215 | -275342 | 0.73 | 52.8 | 2.73 | -92486 | 261265 | -104532 |
| NQ 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | all | 0.34 | 0.54 | -163548 | -130161 | 1055366 | -275342 | 0.60 | 53.0 | 2.01 | -85313 | 261265 | -104532 |
| RTY 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | clean | 0.81 | 1.33 | -124301 | -97636 | 318086 | -167934 | 2.32 | 48.6 | 1.57 | -87301 | 220743 | -99960 |
| RTY 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | H1 | -0.64 | -0.85 | -124206 | -114969 | 361764 | -132093 | -0.42 | 57.1 | 2.73 | -62344 | 143832 | -64686 |
| RTY 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | H2 | 1.10 | 1.83 | -161404 | -132832 | 383436 | -182187 | 1.21 | 50.0 | 2.88 | -83114 | 220377 | -87292 |
| RTY 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | all | 0.67 | 1.05 | -139122 | -113661 | 480457 | -182187 | 2.19 | 50.0 | 2.03 | -85738 | 220743 | -99960 |
| YM 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | clean | 0.66 | 1.05 | -122343 | -100347 | 380926 | -151944 | 1.56 | 50.5 | 1.52 | -84987 | 259375 | -99629 |
| YM 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | H1 | -0.05 | -0.07 | -141898 | -123190 | 445918 | -143347 | -0.03 | 50.0 | 2.66 | -87224 | 167057 | -88075 |
| YM 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | H2 | -0.28 | -0.37 | -129363 | -120708 | 269085 | -135153 | -0.32 | 50.0 | 2.32 | -81195 | 222913 | -83883 |
| YM 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | all | 0.34 | 0.50 | -133690 | -111119 | 448189 | -151944 | 1.11 | 50.0 | 1.88 | -85396 | 259375 | -99629 |
| ZN 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 (diag) | clean | -0.35 | -0.44 | -178931 | -128519 | 614679 | -297195 | -0.51 | 18.1 | 1.37 | -89454 | 246274 | -117704 |
| ZN 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 (diag) | H1 | -1.01 | -1.12 | -79059 | -53331 | 91780 | -82415 | -1.00 | 14.3 | 2.71 | -77610 | 151713 | -78287 |
| ZN 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 (diag) | H2 | -1.57 | -1.73 | -105907 | -75703 | 351670 | -129398 | -0.72 | 22.2 | 2.29 | -94029 | 217425 | -105533 |
| ZN 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 (diag) | all | -0.54 | -0.68 | -153679 | -110273 | 951518 | -297195 | -0.70 | 18.5 | 1.78 | -89259 | 246274 | -117704 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | -35.8 | -5.8 | 14.5 | 28.2 | -6.6 / 12.4 | 26.5 / 33.0 | NO |
| NQ 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | -23.1 | -10.0 | 15.0 | 7.7 | 14.8 / 19.8 | 7.8 / 12.7 | NO |
| RTY 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | -18.5 | -4.3 | 17.1 | 42.9 | -5.1 / 13.3 | 31.8 / 37.5 | NO |
| YM 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | -24.6 | -6.5 | 13.5 | 29.0 | -7.3 / 13.1 | 9.9 / 11.4 | NO |
| GC 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | -7.6 | -267.6 | -29.1 | -64.4 | 2.6 / 26.7 | -287.5 / -141.7 | NO |
| CL 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | -22.5 | -38.7 | -1.5 | -1.9 | -7.9 / 10.3 | 8.0 / 10.5 | NO |
| ZN 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 (diag) | -37.2 | -39.2 | 5.7 | 35.0 | -40.3 / 1.6 | 30.0 / 30.0 | NO |
| BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | -14.4 | 2.0 | 12.7 | 13.3 | 1.2 / 10.7 | 10.1 / 18.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | gross-positive, cost-negative pre-2023 | 1351 | 1.8 | -27.5 | -14.6 | 29.4 | 0.04 / -0.56 / -0.30 | 52.8 / 23.5 |
| ES 2 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 1132 | -10.5 | -39.9 | -27.0 | 29.4 | -0.15 / -0.56 / -0.38 | 64.6 / 35.2 |
| ES 3 (diag) 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 903 | 4.7 | -24.7 | -11.8 | 29.4 | 0.08 / -0.40 / -0.19 | 74.0 / 44.6 |
| ES 4 (diag) 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | negative pre-2023 | 762 | -15.9 | -45.3 | -32.5 | 29.4 | -0.19 / -0.53 / -0.38 | 102.0 / 72.7 |
| ES 5 (diag) 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | negative pre-2023 | 2592 | -5.4 | -34.7 | -20.9 | 29.4 | -0.18 / -1.17 / -0.71 | 48.0 / 18.6 |
| NQ 1 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.05 | gross-positive, cost-negative pre-2023 | 3178 | 4.5 | -9.9 | -1.6 | 14.4 | 0.09 / -0.18 / -0.03 | 101.0 / 86.6 |
| NQ 2 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | negative pre-2023 | 2624 | -8.2 | -22.6 | -14.0 | 14.4 | -0.24 / -0.66 / -0.41 | 133.3 / 118.9 |
| NQ 3 5m st[14, 2.0] dir=with hold=180m ac48 lo-0.1 | gross-positive, cost-negative pre-2023 | 5809 | 8.3 | -6.1 | 2.7 | 14.4 | 0.22 / -0.17 / 0.07 | 79.6 / 65.2 |
| NQ 4 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | negative pre-2023 | 2303 | -23.0 | -37.4 | -29.1 | 14.4 | -0.39 / -0.63 / -0.49 | 118.0 / 103.7 |
| NQ 5 5m st[14, 2.0] dir=with hold=180m ac48 lo-0.05 | negative pre-2023 | 7373 | -3.6 | -17.9 | -9.2 | 14.4 | -0.12 / -0.57 / -0.29 | 67.9 / 53.5 |
| NQ 6 5m vwz[2.0, 'globex'] dir=against hold=60m ac48 lo-0.05 | gross-positive, cost-negative pre-2023 | 6366 | 3.6 | -10.7 | -2.1 | 14.4 | 0.16 / -0.48 / -0.10 | 33.3 / 19.0 |
| NQ 7 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | positive pre-2023 | 3153 | 23.0 | 8.6 | 17.3 | 14.4 | 0.42 / 0.16 / 0.32 | 46.5 / 32.2 |
| NQ 8 5m emax[9, 21] dir=with hold=60m ac48 lo-0.05 | gross-positive, cost-negative pre-2023 | 10039 | 0.6 | -13.7 | -5.0 | 14.4 | 0.03 / -0.80 / -0.30 | 24.9 / 10.6 |
| NQ 9 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.05 | positive pre-2023 | 4201 | 20.5 | 6.1 | 14.7 | 14.4 | 0.42 / 0.12 / 0.30 | 34.0 / 19.6 |
| NQ 10 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 1092 | 10.9 | -3.4 | 4.9 | 14.4 | 0.11 / -0.04 / 0.05 | 79.0 / 64.6 |
| RTY 1 5m don[20] dir=against hold=180m ac48 lo-0.1 | gross-positive, cost-negative pre-2023 | 4146 | 7.1 | -7.3 | -5.1 | 14.4 | 0.40 / -0.41 / -0.29 | 32.4 / 18.1 |
| RTY 2 5m don[20] dir=with hold=180m ac48 hi0.05 | gross-positive, cost-negative pre-2023 | 3265 | 5.6 | -8.7 | -6.5 | 14.4 | 0.24 / -0.38 / -0.29 | 32.8 / 18.4 |
| RTY 3 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | positive pre-2023 | 1839 | 40.6 | 26.2 | 28.4 | 14.4 | 1.37 / 0.89 / 0.96 | 42.7 / 28.3 |
| RTY 4 5m don[20] dir=with hold=180m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 2348 | 11.8 | -2.6 | -0.4 | 14.4 | 0.42 / -0.10 / -0.02 | 30.4 / 16.0 |
| RTY 5 5m st[14, 2.0] dir=with hold=180m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 2001 | 9.0 | -5.3 | -3.1 | 14.4 | 0.27 / -0.17 / -0.10 | 29.8 / 15.5 |
| RTY 6 5m don[20] dir=against hold=180m ac48 lo-0.05 | gross-positive, cost-negative pre-2023 | 5067 | 4.6 | -9.8 | -7.6 | 14.4 | 0.29 / -0.62 / -0.48 | 23.6 / 9.2 |
| RTY 7 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | gross-positive, cost-negative pre-2023 | 976 | 8.9 | -5.5 | -3.3 | 14.4 | 0.29 / -0.17 / -0.10 | 17.0 / 2.7 |
| RTY 8 (diag) 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.05 | positive pre-2023 | 2415 | 37.8 | 23.5 | 25.7 | 14.4 | 1.35 / 0.84 / 0.92 | 34.8 / 20.4 |
| RTY 9 (diag) 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.05 | gross-positive, cost-negative pre-2023 | 1337 | 12.8 | -1.6 | 0.6 | 14.4 | 0.36 / -0.05 / 0.02 | 25.3 / 11.0 |
| RTY 10 (diag) 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | positive pre-2023 | 1051 | 21.9 | 7.5 | 9.7 | 14.4 | 0.54 / 0.19 / 0.24 | 16.9 / 2.6 |
| YM 1 5m st[14, 2.0] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 4779 | -6.8 | -21.1 | -15.4 | 14.4 | -0.25 / -0.77 / -0.56 | 36.2 / 21.9 |
| YM 2 5m rsi[14, 30] dir=with hold=180m ac48 lo-0.1 | gross-positive, cost-negative pre-2023 | 3217 | 9.1 | -5.3 | 0.5 | 14.4 | 0.33 / -0.19 / 0.02 | 32.6 / 18.3 |
| YM 3 (diag) 5m don[20] dir=with hold=180m ac48 lo-0.05 | negative pre-2023 | 8676 | -8.6 | -23.0 | -17.2 | 14.4 | -0.55 / -1.45 / -1.09 | 31.7 / 17.3 |
| YM 4 (diag) 5m st[14, 2.0] dir=with hold=180m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 3415 | 13.7 | -0.6 | 5.0 | 14.4 | 0.46 / -0.02 / 0.17 | 43.4 / 29.1 |
| YM 5 (diag) 5m emax[9, 21] dir=with hold=180m ac48 lo-0.05 | negative pre-2023 | 6858 | -2.2 | -16.6 | -10.8 | 14.4 | -0.12 / -0.86 / -0.56 | 25.0 / 10.6 |
| GC 1 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | negative pre-2023 | 1125 | -2.5 | -26.9 | -17.3 | 24.4 | -0.06 / -0.61 / -0.39 | 88.9 / 64.6 |
| GC 2 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 995 | -6.6 | -31.0 | -21.4 | 24.4 | -0.11 / -0.49 / -0.34 | 91.7 / 67.4 |
| GC 3 (diag) 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | negative pre-2023 | 753 | -17.2 | -41.6 | -32.0 | 24.4 | -0.34 / -0.80 / -0.62 | 80.7 / 56.3 |
| GC 4 (diag) 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 2684 | -2.3 | -26.6 | -17.2 | 24.4 | -0.07 / -0.71 / -0.46 | 65.8 / 41.4 |
| GC 5 (diag) 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | gross-positive, cost-negative pre-2023 | 1351 | 16.2 | -8.2 | 1.4 | 24.4 | 0.36 / -0.18 / 0.03 | 66.7 / 42.3 |
| CL 1 5m rsi[14, 30] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 3511 | -7.4 | -31.8 | -29.4 | 24.4 | -0.23 / -0.95 / -0.88 | 47.8 / 23.5 |
| CL 2 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 911 | 23.8 | -0.5 | 1.5 | 24.4 | 0.51 / -0.01 / 0.03 | 44.1 / 19.8 |
| CL 3 5m rsi[14, 30] dir=against hold=180m ac48 hi0.1 | negative pre-2023 | 2545 | -2.5 | -26.8 | -24.6 | 24.4 | -0.07 / -0.68 / -0.62 | 44.1 / 19.7 |
| CL 4 5m rsi[14, 30] dir=against hold=60m ac48 hi0.05 | negative pre-2023 | 4703 | -1.7 | -26.1 | -23.7 | 24.4 | -0.10 / -1.52 / -1.38 | 34.1 / 9.7 |
| CL 5 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.05 | negative pre-2023 | 1908 | -8.1 | -32.5 | -30.3 | 24.4 | -0.15 / -0.61 / -0.57 | 43.4 / 19.0 |
| CL 6 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 lo-0.1 | negative pre-2023 | 1455 | -18.2 | -42.6 | -40.4 | 24.4 | -0.30 / -0.71 / -0.67 | 40.9 / 16.6 |
| CL 7 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 lo-0.1 | negative pre-2023 | 3718 | -0.4 | -24.7 | -22.3 | 24.4 | -0.01 / -0.90 / -0.81 | 31.2 / 6.9 |
| CL 8 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 hi0.1 | negative pre-2023 | 2049 | -2.9 | -27.3 | -24.8 | 24.4 | -0.06 / -0.61 / -0.55 | 34.5 / 10.1 |
| CL 9 5m rsi[14, 30] dir=against hold=60m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 3282 | 2.4 | -21.9 | -19.7 | 24.4 | 0.11 / -1.03 / -0.92 | 30.4 / 6.0 |
| CL 10 (diag) 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | gross-positive, cost-negative pre-2023 | 1324 | 8.1 | -16.3 | -14.4 | 24.4 | 0.22 / -0.46 / -0.41 | 43.9 / 19.5 |
| ZN 1 (diag) 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.1 | negative pre-2023 | 229 | -8.5 | -44.1 | -49.2 | 35.6 | -0.20 / -1.03 / -1.14 | 18.5 / -17.1 |
| ZN 2 (diag) 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 682 | 13.2 | -22.5 | -27.4 | 35.6 | 0.52 / -0.87 / -1.06 | 19.0 / -16.6 |
| ZN 3 (diag) 5m vwz[2.5, 'rth'] dir=against hold=180m ac48 hi0.05 | negative pre-2023 | 378 | -15.0 | -50.6 | -55.8 | 35.6 | -0.45 / -1.45 / -1.59 | 0.2 / -35.4 |
| BTC 1 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1 | gross-positive, cost-negative pre-2023 | 488 | 14.9 | -39.5 | -7.8 | 54.4 | 0.18 / -0.47 / -0.09 | 217.1 / 162.7 |
| BTC 2 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.05 | positive pre-2023 | 319 | 107.2 | 52.9 | 85.5 | 54.4 | 1.59 / 0.76 / 1.26 | 186.2 / 131.9 |
| BTC 3 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 hi0.05 | negative pre-2023 | 153 | -76.6 | -131.0 | -97.9 | 54.4 | -0.67 / -1.14 / -0.85 | 333.8 / 279.4 |
| BTC 4 5m vwz[2.0, 'globex'] dir=against hold=180m ac48 lo-0.1 | positive pre-2023 | 383 | 141.1 | 86.7 | 119.6 | 54.4 | 1.41 / 0.85 / 1.19 | 203.0 / 148.7 |
| BTC 5 5m rsi[14, 30] dir=against hold=180m ac48 lo-0.1 | gross-positive, cost-negative pre-2023 | 411 | 52.9 | -1.5 | 31.1 | 54.4 | 0.38 / -0.01 / 0.23 | 212.0 / 157.7 |
| BTC 6 5m emax[9, 21] dir=against hold=180m ac48 lo-0.1 | negative pre-2023 | 832 | -83.1 | -137.4 | -104.6 | 54.4 | -1.03 / -1.70 / -1.30 | 147.7 / 93.3 |
| BTC 7 5m vwz[2.0, 'globex'] dir=with hold=180m ac48 hi0.1 | positive pre-2023 | 175 | 162.4 | 108.1 | 139.5 | 54.4 | 0.89 / 0.60 / 0.77 | 218.9 / 164.5 |
| BTC 8 5m vwz[2.5, 'rth'] dir=against hold=60m ac48 lo-0.1 | positive pre-2023 | 231 | 137.3 | 83.0 | 115.7 | 54.4 | 1.58 / 0.93 / 1.32 | 121.7 / 67.4 |
| BTC 9 5m vwz[2.5, 'rth'] dir=with hold=180m ac48 hi0.1 | positive pre-2023 | 70 | 530.0 | 475.6 | 508.8 | 54.4 | 1.85 / 1.66 / 1.77 | 264.2 / 209.8 |
| BTC 10 5m emax[9, 21] dir=with hold=180m ac48 hi0.1 | positive pre-2023 | 257 | 88.4 | 34.1 | 65.5 | 54.4 | 0.60 / 0.23 / 0.44 | 111.0 / 56.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 13 cells pass the clean rule against a replicate mean of 9.2 (p(count) = 0.12, p(top) = 0.57); CL: 9 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.00, p(top) = 0.35); ES: 2 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.57, p(top) = 0.44); GC: 2 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.85, p(top) = 0.03); NQ: 12 cells pass the clean rule against a replicate mean of 11.9 (p(count) = 0.48, p(top) = 0.84); RTY: 7 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.06, p(top) = 0.23); YM: 2 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.85, p(top) = 0.41); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 42 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.17 (BTC 5m st[14, 2.0] dir=with hold=60m ac48 hi0.1); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 17, 'negative pre-2023': 16, 'positive pre-2023': 9}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_23.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw23/ (`SW23_CO_all_selected_scored.csv`).

DONE SW23
