# REPORT SW29 - session-specific effectiveness of bar signals: asia / europe / RTH-AM / RTH-PM windows (D06 H3)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 49 selected cells (+13 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.20; best pair-window standalone Sharpe +0.80.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: ST(14,2) / Donchian-20 / EMA 9-21 / VWAP-band 2.0 / RSI(14,30) on 5/15-min bars restricted to one session window (asia SM<480, europe 480..RTH open, rthAM +0..150 min, rthPM +150..360 min), with/against, hold 30/60 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 160 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     160 |        160 |        12 |               1.021 |                2 |         10 |            0 |
| CL    |     160 |        160 |         1 |               0.773 |                2 |          1 |            3 |
| ES    |     160 |        160 |         5 |               0.938 |                2 |          5 |            3 |
| GC    |     160 |        160 |         4 |               0.86  |                2 |          4 |            3 |
| NQ    |     160 |        160 |        23 |               1.034 |                2 |         10 |            0 |
| RTY   |     160 |        160 |        14 |               1.82  |                2 |         10 |            0 |
| YM    |     160 |        160 |         9 |               1.373 |                2 |          9 |            1 |
| ZN    |     160 |        160 |         0 |              -1.056 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    5 |             1.08 |               3 |       0    |                       0.421 |            0.552 |           1.066 |     0.44 |       0.938 |                1.315 |
| NQ    |     100 |                   23 |            13.22 |              21 |       0    |                       0.711 |            0.801 |           1.039 |     0.73 |       1.034 |                2.058 |
| RTY   |     100 |                   14 |             2.14 |               6 |       0    |                       1.088 |            0.547 |           0.939 |     0.02 |       1.82  |                1.373 |
| YM    |     100 |                    9 |             3.1  |               8 |       0    |                       0.706 |            0.573 |           1.005 |     0.18 |       1.373 |                1.533 |
| GC    |     100 |                    4 |             1.75 |               5 |       0.08 |                       0.407 |            0.524 |           0.922 |     0.57 |       0.603 |                1.144 |
| CL    |     100 |                    1 |             0.55 |               4 |       0.42 |                       0.218 |            0.506 |           1.012 |     0.31 |       0.218 |                1.219 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                   12 |             7.77 |              16 |       0.09 |                       0.549 |            0.632 |           0.855 |     0.67 |       0.911 |                1.783 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m st[14, 2.0] dir=with hold=60m session=rthPM | 313 | 2 | 0.94 | -0.42 | 0.26 | -0.67 / 0.16 | 0.15 / -0.23 / -0.32 | -0.08 | 0.33 | 0.99 | -0.20 | 0.00 | 471 | NO |
| ES 2 | 5m rsi[14, 30] dir=with hold=30m session=rthAM | 511 | 2 | 0.53 | -1.17 | -0.10 | -1.15 / 0.26 | 0.07 / -0.40 / 0.14 | -0.10 | 0.11 | 0.97 | -0.15 | 0.00 | 822 | NO |
| ES 3 | 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | 334 | 2 | 0.30 | -0.79 | -0.01 | -1.29 / 0.49 | -0.01 / -0.30 / -0.09 | -0.12 | -0.19 | 0.91 | -0.19 | 0.00 | 477 | NO |
| ES 4 | 15m rsi[14, 30] dir=against hold=30m session=rthPM | 224 | 2 | 0.25 | -1.17 | -0.16 | -1.16 / 0.20 | 0.00 / -0.49 / -0.16 | -0.18 | -0.08 | 0.97 | -0.26 | 0.00 | 331 | NO |
| ES 5 | 5m st[14, 2.0] dir=against hold=30m session=rthAM | 859 | 2 | 0.09 | -1.62 | -0.30 | -0.62 / 0.13 | -0.07 / 0.62 / -0.78 | -0.33 | 0.11 | 0.99 | -0.38 | 0.00 | 1372 | NO |
| ES 6 (diag) | 5m emax[9, 21] dir=with hold=60m session=rthAM | 501 | 1 | 0.41 | -0.87 | 0.24 | 0.06 / 0.63 | 0.02 / -0.30 / -0.16 | -0.17 | 0.63 | 0.99 | -0.27 | 0.00 | 805 | diag |
| ES 7 (diag) | 15m st[14, 2.0] dir=with hold=60m session=rthAM | 422 | 1 | 0.38 | -0.76 | 0.23 | 0.16 / 0.99 | 0.01 / -0.45 / 0.04 | -0.13 | 0.64 | 0.96 | -0.23 | 0.00 | 688 | diag |
| ES 8 (diag) | 15m don[20] dir=against hold=30m session=rthAM | 594 | 1 | 0.22 | -1.13 | 0.12 | -0.00 / 0.38 | 0.02 / 0.24 / 0.04 | -0.08 | -0.12 | 0.99 | -0.12 | 0.00 | 977 | diag |
| NQ 1 | 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | 259 | 2 | 1.03 | -0.08 | -0.07 | -1.39 / 1.11 | 0.26 / -1.09 / -0.09 | -0.02 | 0.27 | 0.63 | -0.23 | 0.00 | 384 | NO |
| NQ 2 | 5m emax[9, 21] dir=with hold=60m session=rthPM | 589 | 2 | 1.01 | 0.01 | 0.04 | -0.76 / 1.40 | 0.10 / -0.01 / -0.47 | -0.10 | 0.31 | 0.76 | -0.32 | 0.00 | 939 | NO |
| NQ 3 | 15m emax[9, 21] dir=with hold=30m session=rthAM | 289 | 2 | 0.97 | -0.94 | 0.35 | -0.17 / 1.09 | 0.17 / 0.26 / -0.87 | -0.04 | 0.24 | 0.91 | -0.25 | 0.00 | 461 | NO |
| NQ 4 | 5m vwz[2.0, 'globex'] dir=with hold=30m session=rthAM | 440 | 2 | 0.78 | 0.10 | 0.43 | -0.12 / 1.11 | 0.18 / -0.56 / 0.37 | 0.09 | -0.46 | 0.89 | -0.08 | 0.00 | 646 | NO |
| NQ 5 | 15m st[14, 2.0] dir=with hold=60m session=asia | 306 | 2 | 0.62 | -0.70 | 0.61 | 0.67 / 0.94 | 0.12 / 0.18 / 0.10 | 0.09 | -0.42 | 0.99 | -0.09 | 0.17 | 636 | LEAD |
| NQ 6 | 5m rsi[14, 30] dir=against hold=60m session=rthPM | 363 | 2 | 0.61 | 0.06 | 0.27 | -0.71 / 1.51 | 0.08 / -0.19 / -0.02 | 0.00 | -0.16 | 0.81 | -0.11 | 0.17 | 546 | NO |
| NQ 7 | 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | 281 | 2 | 0.60 | 0.20 | -0.06 | -1.63 / 0.93 | 0.05 / -0.24 / -0.31 | -0.08 | -0.49 | 0.71 | -0.22 | 0.00 | 398 | NO |
| NQ 8 | 15m st[14, 2.0] dir=with hold=60m session=rthPM | 304 | 2 | 0.52 | -0.07 | 0.03 | -0.50 / 1.11 | 0.05 / -0.22 / -0.36 | -0.09 | 0.44 | 0.73 | -0.29 | 0.00 | 456 | NO |
| NQ 9 | 5m emax[9, 21] dir=with hold=60m session=rthAM | 509 | 2 | 0.50 | -0.28 | 0.75 | 1.12 / 1.61 | 0.08 / 0.12 / -0.04 | 0.06 | -0.19 | 0.97 | -0.11 | 0.33 | 808 | NO |
| NQ 10 | 15m vwz[2.0, 'globex'] dir=against hold=60m session=asia | 635 | 2 | 0.48 | -0.53 | 0.08 | -0.38 / 0.87 | 0.08 / 0.08 / -0.43 | -0.08 | 0.35 | 0.88 | -0.23 | 0.00 | 1075 | NO |
| RTY 1 | 5m rsi[14, 30] dir=with hold=30m session=rthAM | 512 | 2 | 1.82 | -0.03 | 0.37 | -2.05 / 0.46 | 0.34 / -0.42 / -0.38 | -0.01 | 0.07 | 0.99 | -0.12 | 0.50 | 858 | NO |
| RTY 2 | 5m rsi[14, 30] dir=with hold=60m session=rthAM | 449 | 2 | 1.58 | -0.12 | 0.34 | -1.66 / 1.08 | 0.32 / -0.83 / -0.09 | 0.01 | -0.35 | 0.94 | -0.13 | 0.33 | 746 | NO |
| RTY 3 | 15m don[20] dir=against hold=30m session=rthAM | 567 | 2 | 1.28 | -0.54 | -0.02 | -1.62 / 0.60 | 0.20 / -0.35 / -0.59 | -0.15 | -0.33 | 0.99 | -0.27 | 0.00 | 942 | NO |
| RTY 4 | 15m st[14, 2.0] dir=with hold=60m session=rthPM | 261 | 2 | 1.04 | -0.09 | 0.75 | 0.01 / 0.45 | 0.21 / -0.03 / -0.05 | 0.07 | 0.26 | 1.00 | -0.05 | 0.50 | 408 | NO |
| RTY 5 | 15m rsi[14, 30] dir=against hold=30m session=rthPM | 174 | 2 | 1.01 | -1.12 | 0.11 | -2.02 / 0.19 | 0.17 / -0.30 / -0.41 | -0.07 | -0.19 | 0.99 | -0.17 | 0.00 | 287 | NO |
| RTY 6 | 15m rsi[14, 30] dir=with hold=30m session=rthAM | 332 | 2 | 0.91 | -0.39 | 0.05 | -1.12 / 0.76 | 0.10 / -0.62 / -0.24 | -0.15 | -0.03 | 0.94 | -0.26 | 0.00 | 569 | NO |
| RTY 7 | 15m rsi[14, 30] dir=with hold=60m session=rthAM | 296 | 2 | 0.87 | -0.03 | 0.08 | -0.90 / 1.15 | 0.10 / -0.72 / -0.07 | -0.10 | -0.26 | 0.91 | -0.24 | 0.00 | 519 | NO |
| RTY 8 | 15m vwz[2.0, 'globex'] dir=against hold=30m session=rthPM | 171 | 2 | 0.85 | -0.40 | 0.25 | -1.47 / 0.05 | 0.12 / -0.16 / -0.32 | -0.05 | -0.33 | 1.00 | -0.15 | 0.00 | 262 | NO |
| RTY 9 | 15m st[14, 2.0] dir=with hold=30m session=rthPM | 268 | 2 | 0.78 | 0.07 | 0.16 | -1.09 / 0.26 | 0.17 / -0.23 / -0.37 | -0.06 | 0.19 | 0.99 | -0.18 | 0.50 | 420 | NO |
| RTY 10 | 15m don[20] dir=against hold=60m session=rthAM | 502 | 2 | 0.75 | -0.56 | -0.82 | -2.87 / 0.75 | 0.13 / -1.14 / -0.69 | -0.30 | -0.48 | 0.40 | -0.46 | 0.00 | 826 | NO |
| YM 1 | 15m st[14, 2.0] dir=with hold=60m session=rthPM | 329 | 2 | 1.37 | -0.19 | 0.47 | -0.56 / 0.98 | 0.24 / -0.01 / -0.36 | 0.01 | -0.29 | 0.97 | -0.13 | 0.17 | 489 | NO |
| YM 2 | 15m st[14, 2.0] dir=with hold=30m session=rthPM | 339 | 2 | 1.22 | -0.28 | -0.01 | -1.21 / 0.23 | 0.19 / -0.60 / -0.51 | -0.15 | 0.06 | 0.97 | -0.32 | 0.00 | 508 | NO |
| YM 3 | 15m st[14, 2.0] dir=with hold=60m session=rthAM | 459 | 2 | 1.06 | -0.55 | -0.11 | -1.43 / 0.87 | 0.09 / -0.58 / -0.48 | -0.19 | 0.54 | 0.76 | -0.34 | 0.00 | 747 | NO |
| YM 4 | 5m emax[9, 21] dir=with hold=60m session=rthAM | 518 | 2 | 0.74 | -0.43 | -0.04 | -0.87 / 0.86 | 0.06 / -0.16 / -0.40 | -0.15 | 0.11 | 0.79 | -0.30 | 0.00 | 846 | NO |
| YM 5 | 5m st[14, 2.0] dir=with hold=60m session=rthAM | 698 | 2 | 0.67 | -0.40 | 0.31 | -0.12 / 1.19 | 0.04 / -0.17 / -0.08 | -0.09 | -0.02 | 0.94 | -0.22 | 0.00 | 1115 | NO |
| YM 6 | 15m rsi[14, 30] dir=against hold=30m session=rthPM | 221 | 2 | 0.62 | -0.66 | -0.14 | -1.41 / 0.79 | 0.09 / -0.40 / -0.33 | -0.14 | -0.15 | 0.95 | -0.26 | 0.00 | 315 | NO |
| YM 7 | 15m don[20] dir=with hold=60m session=rthAM | 487 | 2 | 0.45 | -0.74 | -0.23 | -1.06 / 0.98 | -0.01 / 0.27 / -0.79 | -0.20 | 0.30 | 0.70 | -0.36 | 0.00 | 797 | NO |
| YM 8 | 5m don[20] dir=with hold=60m session=rthAM | 757 | 2 | 0.18 | -0.60 | -0.89 | -2.14 / 1.14 | -0.06 / -0.15 / -0.96 | -0.36 | 0.31 | 0.37 | -0.52 | 0.00 | 1235 | NO |
| YM 9 | 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | 281 | 2 | 0.04 | -0.45 | -0.55 | -1.73 / 0.79 | 0.02 / -0.78 / 0.04 | -0.13 | 0.07 | 0.46 | -0.25 | 0.00 | 438 | NO |
| YM 10 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | 255 | 1 | 0.60 | -0.62 | 0.18 | -1.07 / 1.00 | 0.04 / -0.18 / -0.10 | -0.06 | -0.18 | 0.95 | -0.17 | 0.00 | 350 | diag |
| GC 1 | 15m rsi[14, 30] dir=against hold=30m session=rthPM | 171 | 2 | 0.60 | -0.68 | -0.61 | -1.34 / 1.10 | 0.10 / -0.54 / -1.98 | -0.59 | 0.67 | 0.50 | -0.98 | 0.00 | 264 | NO |
| GC 2 | 15m st[14, 2.0] dir=with hold=60m session=rthAM | 411 | 2 | 0.46 | -0.92 | -0.12 | -0.52 / 1.32 | 0.08 / 0.17 / -1.41 | -0.28 | 0.05 | 0.68 | -0.55 | 0.00 | 648 | NO |
| GC 3 | 5m st[14, 2.0] dir=against hold=60m session=rthAM | 691 | 2 | 0.32 | -0.98 | 0.77 | 1.15 / 1.47 | 0.01 / 1.19 / 0.16 | 0.12 | 0.21 | 0.97 | -0.12 | 0.67 | 1108 | NO |
| GC 4 | 5m don[20] dir=against hold=30m session=rthAM | 975 | 2 | 0.24 | -1.12 | -0.70 | -1.38 / 0.97 | 0.03 / -1.53 / -0.29 | -0.40 | -0.37 | 0.44 | -0.60 | 0.00 | 1541 | NO |
| GC 5 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthAM | 220 | 1 | 0.86 | -0.64 | 0.67 | 0.47 / 1.39 | 0.16 / -0.02 / -0.24 | 0.01 | 0.33 | 0.96 | -0.20 | 0.25 | 328 | diag |
| GC 6 (diag) | 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthAM | 333 | 1 | 0.59 | -0.79 | 0.72 | 0.87 / 1.08 | 0.08 / 0.31 / -0.46 | -0.03 | 0.41 | 0.97 | -0.28 | 0.25 | 485 | diag |
| GC 7 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=30m session=rthAM | 240 | 1 | 0.56 | -1.10 | 0.23 | 0.09 / 1.19 | 0.10 / -0.15 / -0.93 | -0.19 | 0.29 | 0.89 | -0.45 | 0.00 | 360 | diag |
| CL 1 | 5m rsi[14, 30] dir=against hold=60m session=rthPM | 328 | 2 | 0.22 | -0.46 | -0.66 | -1.60 / 0.60 | -0.03 / -0.13 / -0.78 | -0.37 | -0.10 | 0.85 | -0.46 | 0.00 | 538 | NO |
| CL 2 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | 196 | 1 | 0.77 | -0.33 | -0.28 | -1.38 / 0.69 | 0.09 / 0.05 / -0.99 | -0.26 | 0.14 | 0.93 | -0.44 | 0.00 | 289 | diag |
| CL 3 (diag) | 15m emax[9, 21] dir=with hold=30m session=rthPM | 226 | 1 | 0.47 | -0.85 | 0.11 | -0.45 / 0.23 | 0.09 / 0.17 / -0.38 | -0.14 | -0.06 | 1.00 | -0.20 | 0.17 | 365 | diag |
| CL 4 (diag) | 15m emax[9, 21] dir=with hold=60m session=rthPM | 210 | 1 | 0.45 | -0.77 | 0.34 | 0.21 / 0.48 | 0.09 / 0.11 / -0.04 | -0.02 | -0.13 | 0.99 | -0.15 | 0.33 | 344 | diag |
| ZN 1 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | 246 | 1 | -1.06 | -1.72 | -1.48 | -2.37 / -4.56 | -0.26 / -0.56 / -0.16 | -0.70 | -0.35 | 1.00 | -0.48 | 0.00 | 372 | diag |
| ZN 2 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=30m session=rthAM | 260 | 0 | -1.44 | -2.39 | -2.06 | -4.24 / -7.00 | -0.34 / -0.53 / -0.34 | -0.81 | -0.35 | 1.00 | -0.56 | 0.00 | 396 | diag |
| ZN 3 (diag) | 5m rsi[14, 30] dir=with hold=60m session=rthAM | 437 | 0 | -2.10 | -3.26 | -2.32 | -2.95 / -5.76 | -0.46 / -0.56 / -0.25 | -0.90 | -0.24 | 1.00 | -0.62 | 0.00 | 656 | diag |
| BTC 1 | 15m rsi[14, 30] dir=against hold=60m session=asia | 281 | 2 | 0.91 | -0.08 | 0.72 | 0.48 / 1.23 | 0.16 / -0.13 / 0.25 | 0.09 | 0.25 | 1.00 | -0.09 | 0.33 | 446 | NO |
| BTC 2 | 15m emax[9, 21] dir=with hold=60m session=asia | 515 | 2 | 0.83 | -1.59 | 0.80 | 0.92 / 0.75 | 0.10 / 0.89 / -0.16 | 0.04 | 0.50 | 1.00 | -0.07 | 0.50 | 819 | NO |
| BTC 3 | 5m emax[9, 21] dir=with hold=60m session=asia | 1181 | 2 | 0.76 | -1.64 | 0.25 | -0.42 / 0.67 | 0.10 / -0.10 / -0.12 | -0.11 | -0.33 | 1.00 | -0.17 | 0.33 | 1899 | NO |
| BTC 4 | 15m vwz[2.0, 'globex'] dir=against hold=60m session=asia | 614 | 2 | 0.57 | 1.00 | 0.12 | -0.81 / 1.00 | 0.13 / 0.04 / -0.29 | -0.04 | -0.49 | 0.87 | -0.14 | 0.50 | 940 | NO |
| BTC 5 | 5m don[20] dir=with hold=60m session=europe | 2030 | 2 | 0.49 | -1.89 | 0.17 | -0.30 / 0.50 | 0.02 / -0.47 / 0.03 | -0.20 | 0.27 | 1.00 | -0.23 | 0.00 | 3181 | NO |
| BTC 6 | 5m st[14, 2.0] dir=against hold=60m session=rthPM | 775 | 2 | 0.48 | -0.11 | 0.20 | -0.40 / 0.85 | 0.07 / -0.30 / 0.07 | -0.06 | 0.25 | 0.91 | -0.16 | 0.33 | 1219 | NO |
| BTC 7 | 15m rsi[14, 30] dir=with hold=60m session=rthPM | 188 | 2 | 0.45 | -1.79 | 0.66 | 1.04 / 0.96 | 0.05 / -0.20 / 0.25 | 0.04 | -0.08 | 0.99 | -0.11 | 0.17 | 267 | NO |
| BTC 8 | 15m emax[9, 21] dir=with hold=60m session=rthPM | 213 | 2 | 0.37 | 0.02 | -0.05 | -0.89 / 0.77 | 0.06 / -0.03 / -0.25 | -0.06 | 0.19 | 0.77 | -0.20 | 0.00 | 311 | NO |
| BTC 9 | 15m emax[9, 21] dir=with hold=30m session=rthAM | 289 | 2 | 0.36 | -0.06 | 0.40 | 0.68 / 0.71 | -0.00 / -0.09 / 0.13 | -0.03 | -0.00 | 0.99 | -0.16 | 0.17 | 452 | NO |
| BTC 10 | 5m rsi[14, 30] dir=against hold=60m session=rthPM | 339 | 2 | 0.27 | 0.97 | -0.25 | -1.39 / 0.85 | 0.03 / 0.12 / -0.44 | -0.11 | 0.04 | 0.72 | -0.22 | 0.00 | 490 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 49 |
| diagnostic cells read | 13 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 22 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 33 |
| worst-decile corr <= +0.30 | 49 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m emax[9, 21] dir=with hold=60m session=asia | clean | 0.71 | 1.15 | -123463 | -96840 | 547690 | -208244 | 1.19 | 51.4 | 1.56 | -93587 | 269726 | -112328 |
| BTC 15m emax[9, 21] dir=with hold=60m session=asia | H1 | 2.83 | 6.03 | -115795 | -104943 | 227787 | -121380 | 4.06 | 42.9 | 3.72 | -59212 | 160479 | -69997 |
| BTC 15m emax[9, 21] dir=with hold=60m session=asia | H2 | -0.85 | -1.02 | -182366 | -137467 | 723593 | -261318 | -0.40 | 47.2 | 2.32 | -92738 | 240515 | -101513 |
| BTC 15m emax[9, 21] dir=with hold=60m session=asia | all | 0.80 | 1.27 | -138886 | -111588 | 723593 | -261318 | 1.78 | 49.4 | 2.04 | -92348 | 269726 | -112328 |
| CL 5m rsi[14, 30] dir=against hold=60m session=rthPM | clean | 0.21 | 0.34 | -118223 | -94921 | 583344 | -188375 | 0.32 | 47.6 | 1.43 | -91623 | 320466 | -103857 |
| CL 5m rsi[14, 30] dir=against hold=60m session=rthPM | H1 | -1.19 | -1.30 | -156045 | -123661 | 332855 | -251072 | -0.79 | 53.6 | 2.70 | -78520 | 155547 | -81439 |
| CL 5m rsi[14, 30] dir=against hold=60m session=rthPM | H2 | -1.87 | -2.12 | -272420 | -255925 | 1537526 | -293769 | -0.75 | 55.6 | 1.70 | -83998 | 201472 | -85420 |
| CL 5m rsi[14, 30] dir=against hold=60m session=rthPM | all | -0.66 | -0.84 | -222789 | -171438 | 1911329 | -293769 | -0.65 | 50.6 | 1.67 | -88877 | 320466 | -103857 |
| ES 5m rsi[14, 30] dir=with hold=30m session=rthAM | clean | 0.48 | 1.05 | -81962 | -65427 | 284077 | -198377 | 1.54 | 53.3 | 1.53 | -82780 | 262271 | -87109 |
| ES 5m rsi[14, 30] dir=with hold=30m session=rthAM | H1 | -3.05 | -3.23 | -124578 | -115525 | 703210 | -131913 | -0.99 | 67.9 | 2.43 | -71984 | 153209 | -82314 |
| ES 5m rsi[14, 30] dir=with hold=30m session=rthAM | H2 | 0.47 | 0.74 | -93717 | -80719 | 136450 | -107655 | 0.89 | 47.2 | 2.62 | -87593 | 212502 | -90379 |
| ES 5m rsi[14, 30] dir=with hold=30m session=rthAM | all | -0.10 | -0.17 | -110252 | -88997 | 1067267 | -198377 | -0.13 | 54.2 | 1.89 | -84210 | 262271 | -90379 |
| GC 5m st[14, 2.0] dir=against hold=60m session=rthAM | clean | 0.40 | 0.61 | -127185 | -100125 | 600542 | -213191 | 0.61 | 54.3 | 1.47 | -92076 | 355689 | -99995 |
| GC 5m st[14, 2.0] dir=against hold=60m session=rthAM | H1 | 1.83 | 4.70 | -219619 | -187461 | 419924 | -227174 | 3.25 | 39.3 | 4.02 | -57201 | 125643 | -68228 |
| GC 5m st[14, 2.0] dir=against hold=60m session=rthAM | H2 | 0.51 | 0.75 | -357125 | -287228 | 766881 | -410572 | 0.53 | 44.4 | 2.65 | -91514 | 260362 | -93333 |
| GC 5m st[14, 2.0] dir=against hold=60m session=rthAM | all | 0.77 | 1.37 | -234403 | -176174 | 766881 | -410572 | 2.78 | 50.0 | 2.10 | -90926 | 355689 | -99995 |
| NQ 15m st[14, 2.0] dir=with hold=60m session=asia | clean | 0.58 | 0.78 | -172485 | -114037 | 732442 | -287546 | 0.72 | 38.1 | 1.58 | -86669 | 255560 | -98999 |
| NQ 15m st[14, 2.0] dir=with hold=60m session=asia | H1 | 1.31 | 2.85 | -89047 | -80629 | 260840 | -101660 | 1.30 | 57.1 | 3.01 | -78710 | 134078 | -80315 |
| NQ 15m st[14, 2.0] dir=with hold=60m session=asia | H2 | 0.37 | 0.54 | -205021 | -179436 | 668501 | -240753 | 0.30 | 44.4 | 2.59 | -83608 | 233198 | -106497 |
| NQ 15m st[14, 2.0] dir=with hold=60m session=asia | all | 0.61 | 0.88 | -188704 | -145727 | 732442 | -287546 | 1.46 | 42.9 | 2.03 | -87328 | 255560 | -106497 |
| RTY 15m st[14, 2.0] dir=with hold=60m session=rthPM | clean | 1.18 | 2.11 | -111492 | -93434 | 431727 | -148431 | 2.55 | 46.7 | 1.67 | -88064 | 267722 | -95847 |
| RTY 15m st[14, 2.0] dir=with hold=60m session=rthPM | H1 | 0.01 | 0.02 | -75345 | -73538 | 323905 | -78508 | 0.01 | 50.0 | 2.80 | -71882 | 165445 | -80331 |
| RTY 15m st[14, 2.0] dir=with hold=60m session=rthPM | H2 | 0.01 | 0.02 | -137529 | -108893 | 449906 | -154642 | 0.01 | 41.7 | 2.44 | -98479 | 214137 | -110582 |
| RTY 15m st[14, 2.0] dir=with hold=60m session=rthPM | all | 0.75 | 1.29 | -114554 | -95056 | 456536 | -154642 | 2.42 | 45.8 | 2.02 | -89980 | 267722 | -110582 |
| YM 15m st[14, 2.0] dir=with hold=60m session=rthPM | clean | 1.26 | 2.48 | -86925 | -79282 | 488966 | -101817 | 2.36 | 44.8 | 1.70 | -84113 | 254963 | -91621 |
| YM 15m st[14, 2.0] dir=with hold=60m session=rthPM | H1 | -0.16 | -0.23 | -181488 | -168856 | 560533 | -201828 | -0.10 | 42.9 | 2.82 | -74666 | 189966 | -75232 |
| YM 15m st[14, 2.0] dir=with hold=60m session=rthPM | H2 | -0.96 | -1.38 | -143497 | -118590 | 739413 | -160055 | -0.44 | 63.9 | 2.12 | -107100 | 224923 | -111664 |
| YM 15m st[14, 2.0] dir=with hold=60m session=rthPM | all | 0.47 | 0.78 | -137137 | -109430 | 994479 | -201828 | 0.77 | 48.2 | 1.96 | -88907 | 254963 | -111664 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM (diag) | clean | -1.10 | -1.35 | -164259 | -123604 | 1218254 | -273943 | -0.83 | 55.2 | 1.20 | -97371 | 336013 | -131797 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM (diag) | H1 | -3.53 | -3.34 | -133633 | -111667 | 660419 | -193046 | -0.95 | 64.3 | 2.27 | -79739 | 182832 | -82913 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM (diag) | H2 | -1.45 | -1.84 | -99184 | -82710 | 437279 | -106345 | -0.74 | 58.3 | 2.33 | -84882 | 221683 | -86918 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM (diag) | all | -1.48 | -1.76 | -152996 | -115407 | 2028061 | -273943 | -0.96 | 57.7 | 1.60 | -93276 | 336013 | -131797 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 5m rsi[14, 30] dir=with hold=30m session=rthAM | -31.5 | 15.7 | 19.9 | 30.1 | 16.0 / 22.0 | 22.3 / 35.1 | NO |
| NQ 15m st[14, 2.0] dir=with hold=60m session=asia | -18.3 | -28.0 | 7.6 | 31.6 | -29.0 / 5.8 | 24.7 / 27.9 | NO |
| RTY 15m st[14, 2.0] dir=with hold=60m session=rthPM | -17.9 | -23.8 | 9.2 | 33.8 | 3.5 / 11.6 | 26.1 / 36.4 | NO |
| YM 15m st[14, 2.0] dir=with hold=60m session=rthPM | -21.6 | -25.7 | 7.3 | 23.6 | 7.4 / 18.3 | 0.8 / 17.6 | NO |
| GC 5m st[14, 2.0] dir=against hold=60m session=rthAM | -6.7 | -6.8 | 2.9 | -10.5 | -7.7 / 2.9 | -4.3 / 4.6 | NO |
| CL 5m rsi[14, 30] dir=against hold=60m session=rthPM | -43.5 | -13.4 | -1.9 | 8.4 | -14.3 / -1.6 | 22.6 / 28.2 | NO |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM (diag) | -51.4 | -64.9 | 2.3 | -14.3 | -66.2 / -6.5 | 21.1 / 25.9 | NO |
| BTC 15m emax[9, 21] dir=with hold=60m session=asia | -15.9 | -24.8 | 4.6 | 21.3 | -25.8 / 1.4 | 34.2 / 39.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m st[14, 2.0] dir=with hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 1589 | 12.5 | -16.9 | -2.8 | 29.4 | 0.31 / -0.42 / -0.07 | 80.6 / 51.3 |
| ES 2 5m rsi[14, 30] dir=with hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 2608 | 0.4 | -29.0 | -14.9 | 29.4 | 0.01 / -1.17 / -0.60 | 55.0 / 25.7 |
| ES 3 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | negative pre-2023 | 1505 | -5.8 | -35.1 | -20.8 | 29.4 | -0.13 / -0.79 / -0.47 | 58.7 / 29.3 |
| ES 4 15m rsi[14, 30] dir=against hold=30m session=rthPM | negative pre-2023 | 1115 | -15.8 | -45.2 | -31.0 | 29.4 | -0.42 / -1.17 / -0.81 | 49.4 / 20.1 |
| ES 5 5m st[14, 2.0] dir=against hold=30m session=rthAM | negative pre-2023 | 4280 | -1.3 | -30.6 | -16.5 | 29.4 | -0.07 / -1.62 / -0.87 | 29.4 / 0.0 |
| ES 6 (diag) 5m emax[9, 21] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 2667 | 0.6 | -28.7 | -14.5 | 29.4 | 0.02 / -0.87 / -0.44 | 46.5 / 17.2 |
| ES 7 (diag) 15m st[14, 2.0] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 2206 | 2.5 | -26.9 | -12.6 | 29.4 | 0.07 / -0.76 / -0.36 | 43.6 / 14.2 |
| ES 8 (diag) 15m don[20] dir=against hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 3081 | 5.1 | -24.3 | -10.2 | 29.4 | 0.24 / -1.13 / -0.47 | 38.6 / 9.2 |
| NQ 1 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 1187 | 8.6 | -5.8 | 2.8 | 14.4 | 0.12 / -0.08 / 0.04 | 153.2 / 138.9 |
| NQ 2 5m emax[9, 21] dir=with hold=60m session=rthPM | positive pre-2023 | 3126 | 14.9 | 0.5 | 9.1 | 14.4 | 0.36 / 0.01 / 0.22 | 62.8 / 48.4 |
| NQ 3 15m emax[9, 21] dir=with hold=30m session=rthAM | negative pre-2023 | 1637 | -38.1 | -52.4 | -43.8 | 14.4 | -0.69 / -0.94 / -0.79 | 102.2 / 87.9 |
| NQ 4 5m vwz[2.0, 'globex'] dir=with hold=30m session=rthAM | positive pre-2023 | 2188 | 18.9 | 4.6 | 13.0 | 14.4 | 0.40 / 0.10 / 0.28 | 79.6 / 65.2 |
| NQ 5 15m st[14, 2.0] dir=with hold=60m session=asia | negative pre-2023 | 1758 | -8.4 | -22.8 | -14.4 | 14.4 | -0.26 / -0.70 / -0.45 | 51.3 / 36.9 |
| NQ 6 5m rsi[14, 30] dir=against hold=60m session=rthPM | positive pre-2023 | 1865 | 18.1 | 3.7 | 12.2 | 14.4 | 0.28 / 0.06 / 0.19 | 114.8 / 100.4 |
| NQ 7 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | positive pre-2023 | 1388 | 28.2 | 13.8 | 22.5 | 14.4 | 0.40 / 0.20 / 0.32 | 109.0 / 94.7 |
| NQ 8 15m st[14, 2.0] dir=with hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 1582 | 10.1 | -4.2 | 4.4 | 14.4 | 0.16 / -0.07 / 0.07 | 65.4 / 51.0 |
| NQ 9 5m emax[9, 21] dir=with hold=60m session=rthAM | negative pre-2023 | 2725 | -1.9 | -16.2 | -7.7 | 14.4 | -0.03 / -0.28 / -0.13 | 61.0 / 46.6 |
| NQ 10 15m vwz[2.0, 'globex'] dir=against hold=60m session=asia | gross-positive, cost-negative pre-2023 | 3301 | 4.6 | -9.7 | -1.3 | 14.4 | 0.24 / -0.53 / -0.07 | 31.4 / 17.0 |
| RTY 1 5m rsi[14, 30] dir=with hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 1732 | 13.7 | -0.7 | 1.6 | 14.4 | 0.53 / -0.03 / 0.06 | 64.0 / 49.6 |
| RTY 2 5m rsi[14, 30] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 1488 | 10.2 | -4.2 | -1.9 | 14.4 | 0.31 / -0.12 / -0.06 | 74.0 / 59.7 |
| RTY 3 15m don[20] dir=against hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 1947 | 2.5 | -11.9 | -9.6 | 14.4 | 0.12 / -0.54 / -0.43 | 42.9 / 28.5 |
| RTY 4 15m st[14, 2.0] dir=with hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 886 | 11.6 | -2.7 | -0.4 | 14.4 | 0.38 / -0.09 / -0.01 | 61.0 / 46.7 |
| RTY 5 15m rsi[14, 30] dir=against hold=30m session=rthPM | negative pre-2023 | 569 | -20.3 | -34.7 | -32.5 | 14.4 | -0.66 / -1.12 / -1.05 | 68.2 / 53.8 |
| RTY 6 15m rsi[14, 30] dir=with hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 1121 | 3.9 | -10.4 | -8.2 | 14.4 | 0.16 / -0.39 / -0.31 | 39.8 / 25.4 |
| RTY 7 15m rsi[14, 30] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 1031 | 13.0 | -1.3 | 0.9 | 14.4 | 0.36 / -0.03 / 0.03 | 50.3 / 35.9 |
| RTY 8 15m vwz[2.0, 'globex'] dir=against hold=30m session=rthPM | gross-positive, cost-negative pre-2023 | 631 | 2.4 | -12.0 | -9.6 | 14.4 | 0.08 / -0.40 / -0.32 | 61.4 / 47.0 |
| RTY 9 15m st[14, 2.0] dir=with hold=30m session=rthPM | positive pre-2023 | 931 | 16.0 | 1.6 | 3.9 | 14.4 | 0.73 / 0.07 / 0.18 | 41.4 / 27.1 |
| RTY 10 15m don[20] dir=against hold=60m session=rthAM | negative pre-2023 | 1679 | -2.6 | -17.0 | -14.7 | 14.4 | -0.08 / -0.56 / -0.49 | 39.3 / 24.9 |
| YM 1 15m st[14, 2.0] dir=with hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 1571 | 8.3 | -6.0 | -0.3 | 14.4 | 0.27 / -0.19 / -0.01 | 60.4 / 46.0 |
| YM 2 15m st[14, 2.0] dir=with hold=30m session=rthPM | gross-positive, cost-negative pre-2023 | 1649 | 8.9 | -5.5 | 0.3 | 14.4 | 0.45 / -0.28 / 0.01 | 42.6 / 28.3 |
| YM 3 15m st[14, 2.0] dir=with hold=60m session=rthAM | negative pre-2023 | 2168 | -0.4 | -14.8 | -9.0 | 14.4 | -0.01 / -0.55 / -0.34 | 48.0 / 33.6 |
| YM 4 5m emax[9, 21] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 2662 | 4.4 | -10.0 | -4.2 | 14.4 | 0.20 / -0.43 / -0.18 | 37.3 / 22.9 |
| YM 5 5m st[14, 2.0] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 3546 | 5.3 | -9.1 | -3.4 | 14.4 | 0.22 / -0.40 / -0.15 | 33.7 / 19.3 |
| YM 6 15m rsi[14, 30] dir=against hold=30m session=rthPM | negative pre-2023 | 1019 | -6.9 | -21.2 | -15.4 | 14.4 | -0.22 / -0.66 / -0.48 | 33.8 / 19.4 |
| YM 7 15m don[20] dir=with hold=60m session=rthAM | negative pre-2023 | 2619 | -3.5 | -17.9 | -12.2 | 14.4 | -0.15 / -0.74 / -0.50 | 30.0 / 15.6 |
| YM 8 5m don[20] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 4016 | 1.8 | -12.6 | -6.9 | 14.4 | 0.08 / -0.60 / -0.33 | 19.8 / 5.4 |
| YM 9 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | negative pre-2023 | 1081 | -2.7 | -17.1 | -11.5 | 14.4 | -0.07 / -0.45 / -0.30 | 17.1 / 2.7 |
| YM 10 (diag) 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | negative pre-2023 | 1049 | -13.6 | -27.9 | -22.3 | 14.4 | -0.30 / -0.62 / -0.50 | 49.6 / 35.3 |
| GC 1 15m rsi[14, 30] dir=against hold=30m session=rthPM | gross-positive, cost-negative pre-2023 | 860 | 0.9 | -23.4 | -13.6 | 24.4 | 0.03 / -0.68 / -0.39 | 53.5 / 29.1 |
| GC 2 15m st[14, 2.0] dir=with hold=60m session=rthAM | negative pre-2023 | 2039 | -7.3 | -31.7 | -22.0 | 24.4 | -0.21 / -0.92 / -0.64 | 58.0 / 33.6 |
| GC 3 5m st[14, 2.0] dir=against hold=60m session=rthAM | negative pre-2023 | 3458 | -2.4 | -26.7 | -17.1 | 24.4 | -0.08 / -0.98 / -0.62 | 43.1 / 18.7 |
| GC 4 5m don[20] dir=against hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 4456 | 2.6 | -21.8 | -12.2 | 24.4 | 0.14 / -1.12 / -0.62 | 27.4 / 3.1 |
| GC 5 (diag) 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthAM | negative pre-2023 | 990 | -11.2 | -35.6 | -26.2 | 24.4 | -0.21 / -0.64 / -0.47 | 106.3 / 82.0 |
| GC 6 (diag) 5m vwz[2.0, 'globex'] dir=against hold=60m session=rthAM | negative pre-2023 | 1553 | -10.0 | -34.4 | -24.9 | 24.4 | -0.23 / -0.79 / -0.57 | 71.2 / 46.8 |
| GC 7 (diag) 15m vwz[2.0, 'globex'] dir=against hold=30m session=rthAM | negative pre-2023 | 1048 | -20.6 | -44.9 | -35.5 | 24.4 | -0.51 / -1.10 / -0.87 | 69.2 / 44.8 |
| CL 1 5m rsi[14, 30] dir=against hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 1783 | 10.4 | -13.9 | -11.5 | 24.4 | 0.35 / -0.46 / -0.38 | 30.6 / 6.2 |
| CL 2 (diag) 15m vwz[2.0, 'globex'] dir=against hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 899 | 9.2 | -15.2 | -12.7 | 24.4 | 0.20 / -0.33 / -0.28 | 61.0 / 36.7 |
| CL 3 (diag) 15m emax[9, 21] dir=with hold=30m session=rthPM | negative pre-2023 | 1222 | -1.3 | -25.7 | -23.2 | 24.4 | -0.04 / -0.85 / -0.77 | 38.1 / 13.7 |
| CL 4 (diag) 15m emax[9, 21] dir=with hold=60m session=rthPM | negative pre-2023 | 1146 | -4.9 | -29.3 | -26.8 | 24.4 | -0.13 / -0.77 / -0.71 | 43.6 / 19.3 |
| ZN 1 (diag) 15m vwz[2.0, 'globex'] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 996 | 7.2 | -28.5 | -33.5 | 35.6 | 0.42 / -1.72 / -2.01 | 20.3 / -15.3 |
| ZN 2 (diag) 15m vwz[2.0, 'globex'] dir=with hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 1072 | 6.2 | -29.4 | -34.5 | 35.6 | 0.51 / -2.39 / -2.77 | 16.7 / -18.9 |
| ZN 3 (diag) 5m rsi[14, 30] dir=with hold=60m session=rthAM | gross-positive, cost-negative pre-2023 | 2133 | 3.1 | -32.5 | -37.6 | 35.6 | 0.32 / -3.26 / -3.75 | 10.9 / -24.7 |
| BTC 1 15m rsi[14, 30] dir=against hold=60m session=asia | gross-positive, cost-negative pre-2023 | 230 | 47.5 | -6.9 | 25.7 | 54.4 | 0.36 / -0.08 / 0.18 | 268.0 / 213.6 |
| BTC 2 15m emax[9, 21] dir=with hold=60m session=asia | negative pre-2023 | 345 | -64.9 | -119.3 | -86.2 | 54.4 | -0.88 / -1.59 / -1.16 | 124.2 / 69.9 |
| BTC 3 5m emax[9, 21] dir=with hold=60m session=asia | gross-positive, cost-negative pre-2023 | 882 | 4.1 | -50.3 | -17.7 | 54.4 | 0.13 / -1.64 / -0.58 | 105.3 / 51.0 |
| BTC 4 15m vwz[2.0, 'globex'] dir=against hold=60m session=asia | positive pre-2023 | 329 | 152.4 | 98.1 | 130.6 | 54.4 | 1.55 / 1.00 / 1.33 | 131.2 / 76.8 |
| BTC 5 5m don[20] dir=with hold=60m session=europe | gross-positive, cost-negative pre-2023 | 1347 | 3.1 | -51.2 | -18.8 | 54.4 | 0.12 / -1.89 / -0.69 | 83.1 / 28.7 |
| BTC 6 5m st[14, 2.0] dir=against hold=60m session=rthPM | gross-positive, cost-negative pre-2023 | 556 | 48.7 | -5.7 | 26.6 | 54.4 | 0.88 / -0.11 / 0.48 | 117.6 / 63.2 |
| BTC 7 15m rsi[14, 30] dir=with hold=60m session=rthPM | negative pre-2023 | 157 | -184.9 | -239.2 | -207.1 | 54.4 | -1.39 / -1.79 / -1.55 | 199.1 / 144.7 |
| BTC 8 15m emax[9, 21] dir=with hold=60m session=rthPM | positive pre-2023 | 184 | 56.1 | 1.8 | 34.7 | 54.4 | 0.50 / 0.02 / 0.31 | 131.2 / 76.9 |
| BTC 9 15m emax[9, 21] dir=with hold=30m session=rthAM | gross-positive, cost-negative pre-2023 | 205 | 51.6 | -2.8 | 29.5 | 54.4 | 0.78 / -0.06 / 0.44 | 108.0 / 53.6 |
| BTC 10 5m rsi[14, 30] dir=against hold=60m session=rthPM | positive pre-2023 | 291 | 136.6 | 82.2 | 114.4 | 54.4 | 1.61 / 0.97 / 1.35 | 118.8 / 64.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 12 cells pass the clean rule against a replicate mean of 7.8 (p(count) = 0.09, p(top) = 0.67); CL: 1 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.42, p(top) = 0.31); ES: 5 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.00, p(top) = 0.44); GC: 4 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.08, p(top) = 0.57); NQ: 23 cells pass the clean rule against a replicate mean of 13.2 (p(count) = 0.00, p(top) = 0.73); RTY: 14 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.00, p(top) = 0.02); YM: 9 cells pass the clean rule against a replicate mean of 3.1 (p(count) = 0.00, p(top) = 0.18); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 49 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.20 (GC 5m st[14, 2.0] dir=against hold=60m session=rthAM); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell NQ 15m st[14, 2.0] dir=with hold=60m session=asia: uplift +0.12/+0.18/+0.10, boot lo -0.09, plateau 0.17, 2x-slip +0.09, wd corr -0.42, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 25, 'negative pre-2023': 16, 'positive pre-2023': 8}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_29.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw29/ (`SW29_CO_all_selected_scored.csv`).

DONE SW29
