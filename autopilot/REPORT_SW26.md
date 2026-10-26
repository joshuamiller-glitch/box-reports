# REPORT SW26 - correlation-gated lead-lag catch-up (D07 H2)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 31 selected cells (+15 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.43; best pair-window standalone Sharpe +1.66.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- SW8 residual events (L 5/15, k 1.5/2.5) taken only when the trailing-60-min correlation of 1-min returns target/driver is hi (>= 0.7) or lo (<= 0.5); with/against; hold 15/30 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         64 |         4 |               1.294 |                2 |          4 |            2 |
| CL    |      96 |         48 |         0 |               1.112 |                2 |          0 |            1 |
| ES    |      96 |         80 |         0 |               1.406 |                2 |          0 |            3 |
| GC    |      96 |         84 |         0 |               0.423 |                1 |          0 |            3 |
| NQ    |      96 |         80 |        15 |               2.581 |                2 |         10 |            0 |
| RTY   |      96 |         96 |        10 |               1.06  |                2 |         10 |            0 |
| YM    |      96 |         96 |         7 |               0.746 |                2 |          7 |            3 |
| ZN    |      96 |         78 |         0 |              -0.642 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    0 |             0.03 |               1 |       1    |                     nan     |            0.475 |           0.746 |   nan    |     nan     |                0.746 |
| NQ    |     100 |                   15 |             3.05 |               9 |       0    |                       1.31  |            0.542 |           0.804 |     0    |       2.581 |                1.383 |
| RTY   |     100 |                   10 |             0.01 |               1 |       0    |                       0.655 |            0.179 |           0.179 |     0    |       1.06  |                0.179 |
| YM    |     100 |                    7 |             0.23 |               3 |       0    |                       0.602 |            0.534 |           1.144 |     0.06 |       0.746 |                1.203 |
| GC    |     100 |                    0 |             1.13 |               5 |       1    |                     nan     |            0.67  |           1.145 |   nan    |     nan     |                1.472 |
| CL    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    4 |             1.97 |               6 |       0.11 |                       0.782 |            0.561 |           1.061 |     0.14 |       1.256 |                1.432 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 | 191 | 1 | 1.41 | -1.01 | 0.88 | 0.23 / 0.15 | 0.28 / 0.80 / -0.51 | 0.06 | 0.28 | 1.00 | -0.03 | 0.25 | 305 | diag |
| ES 2 (diag) | driver NQ resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | 174 | 1 | 1.23 | -0.81 | 0.58 | -0.09 / 0.10 | 0.24 / 0.56 / -0.42 | 0.05 | 0.18 | 1.00 | -0.09 | 0.75 | 276 | diag |
| ES 3 (diag) | driver NQ resid5m>=2.5 dir=against X hold=15m corr60 lo0.5 | 19 | 2 | 0.69 | -0.79 | -0.09 | -0.66 / 1.21 | 0.16 / 0.55 / -1.03 | -0.12 | 0.18 | 0.87 | -0.39 | 0.00 | 34 S | diag |
| NQ 1 | driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | 1006 | 2 | 2.58 | 0.46 | 1.66 | 0.97 / 1.03 | 0.49 / 0.79 / 0.01 | 0.38 | -0.04 | 1.00 | 0.18 | 0.25 | 1686 | NO |
| NQ 2 | driver ES resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | 191 | 2 | 2.10 | 0.05 | 1.53 | 0.86 / 0.98 | 0.43 / 0.88 / -0.37 | 0.29 | 0.30 | 1.00 | 0.09 | 0.25 | 305 | NO |
| NQ 3 | driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 174 | 2 | 1.85 | 0.05 | 0.93 | 0.10 / 1.33 | 0.36 / 0.64 / -0.42 | 0.21 | 0.25 | 1.00 | -0.02 | 0.75 | 276 | NO |
| NQ 4 | driver ES resid15m>=1.5 dir=against X hold=30m corr60 hi0.7 | 722 | 2 | 1.22 | 0.35 | 0.75 | 0.34 / 0.92 | 0.25 / 0.51 / -0.16 | 0.17 | 0.36 | 1.00 | -0.03 | 0.50 | 1114 | NO |
| NQ 5 | driver RTY resid5m>=1.5 dir=with X hold=30m corr60 hi0.7 | 1515 | 2 | 1.14 | 0.12 | 1.19 | 1.21 / 0.53 | 0.21 / 0.52 / -0.03 | 0.14 | 0.28 | 1.00 | 0.00 | 0.12 | 2544 | NO |
| NQ 6 | driver YM resid15m>=2.5 dir=against X hold=15m corr60 lo0.5 | 1325 | 2 | 1.01 | -0.03 | 0.28 | -0.49 / 0.81 | 0.14 / 0.23 / -0.55 | -0.06 | -0.21 | 0.96 | -0.22 | 0.50 | 2226 | NO |
| NQ 7 | driver ES resid5m>=2.5 dir=against X hold=30m corr60 hi0.7 | 371 | 2 | 0.91 | -0.00 | 0.96 | 1.08 / 0.85 | 0.19 / 0.92 / -0.06 | 0.21 | 0.30 | 0.99 | 0.01 | 0.75 | 550 | NO |
| NQ 8 | driver RTY resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | 938 | 2 | 0.88 | 0.76 | 0.63 | 0.43 / 0.92 | 0.16 / 0.59 / -0.23 | 0.09 | -0.05 | 0.98 | -0.10 | 0.50 | 1365 | NO |
| NQ 9 | driver YM resid5m>=2.5 dir=against X hold=30m corr60 lo0.5 | 1353 | 2 | 0.86 | 0.42 | 0.95 | 1.11 / 0.85 | 0.16 / 0.78 / 0.01 | 0.16 | -0.30 | 1.00 | 0.00 | 0.62 | 2310 | NO |
| NQ 10 | driver YM resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | 1871 | 2 | 0.55 | 0.48 | 0.74 | 1.00 / 0.70 | 0.08 / 0.32 / 0.30 | 0.09 | -0.27 | 0.99 | -0.05 | 0.50 | 3355 | NO |
| RTY 1 | driver ES resid5m>=2.5 dir=with X hold=30m corr60 lo0.5 | 612 | 2 | 1.06 | -0.69 | 0.32 | -0.89 / 0.26 | 0.18 / -0.64 / 0.02 | -0.06 | -0.18 | 1.00 | -0.16 | 0.38 | 862 | NO |
| RTY 2 | driver NQ resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | 190 | 2 | 0.87 | 0.33 | 0.15 | -1.22 / -1.29 | 0.13 / -0.46 / 0.01 | -0.04 | -0.02 | 1.00 | -0.17 | 0.25 | 294 | NO |
| RTY 3 | driver NQ resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 176 | 2 | 0.78 | 0.03 | -0.01 | -0.96 / -0.54 | 0.12 / -0.67 / -0.18 | -0.09 | 0.07 | 1.00 | -0.27 | 0.00 | 273 | NO |
| RTY 4 | driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 224 | 2 | 0.77 | -0.76 | 0.25 | -0.34 / -0.12 | 0.16 / 0.00 / -0.16 | 0.01 | -0.15 | 1.00 | -0.19 | 0.50 | 346 | NO |
| RTY 5 | driver ES resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | 418 | 2 | 0.73 | -0.69 | 0.35 | -0.14 / 0.66 | 0.08 / -0.18 / -0.05 | -0.05 | 0.03 | 1.00 | -0.16 | 0.25 | 601 | NO |
| RTY 6 | driver YM resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | 1138 | 2 | 0.72 | -1.02 | 0.29 | -0.25 / -1.09 | 0.08 / 0.13 / -0.28 | -0.11 | -0.54 | 1.00 | -0.18 | 0.00 | 1810 | NO |
| RTY 7 | driver YM resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | 211 | 2 | 0.62 | -0.54 | 0.25 | -0.14 / -0.37 | 0.07 / -0.50 / 0.07 | -0.07 | -0.58 | 1.00 | -0.22 | 0.00 | 350 | NO |
| RTY 8 | driver ES resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | 240 | 2 | 0.55 | -0.36 | -0.10 | -0.93 / -0.59 | 0.04 / -0.20 / -0.16 | -0.12 | 0.03 | 1.00 | -0.28 | 0.00 | 377 | NO |
| RTY 9 | driver ES resid5m>=2.5 dir=with X hold=15m corr60 lo0.5 | 811 | 2 | 0.43 | -1.23 | -0.09 | -1.08 / -0.59 | 0.04 / -0.54 / -0.17 | -0.21 | 0.13 | 1.00 | -0.27 | 0.00 | 1132 | NO |
| RTY 10 | driver YM resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | 1009 | 2 | 0.03 | -0.57 | 0.34 | 0.95 / -0.38 | -0.01 / -0.04 / 0.14 | -0.09 | 0.18 | 1.00 | -0.14 | 0.25 | 1395 | NO |
| YM 1 | driver ES resid15m>=2.5 dir=against X hold=15m corr60 lo0.5 | 309 | 2 | 0.75 | -0.28 | 0.59 | 0.42 / 0.36 | 0.15 / -0.62 / 0.32 | -0.00 | -0.14 | 1.00 | -0.14 | 0.38 | 561 | NO |
| YM 2 | driver RTY resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 211 | 2 | 0.72 | -0.42 | -0.33 | -1.39 / -0.01 | 0.10 / -0.95 / -0.32 | -0.20 | -0.29 | 0.94 | -0.39 | 0.00 | 350 | NO |
| YM 3 | driver NQ resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 158 | 2 | 0.67 | -0.48 | 0.33 | -0.27 / 0.71 | 0.14 / -0.39 / 0.03 | 0.00 | -0.08 | 1.00 | -0.15 | 0.25 | 236 | NO |
| YM 4 | driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | 452 | 2 | 0.67 | -1.10 | 1.21 | 2.02 / 0.25 | 0.05 / 0.03 / 0.53 | 0.08 | -0.15 | 1.00 | -0.03 | 0.38 | 662 | NO |
| YM 5 | driver ES resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | 249 | 2 | 0.63 | -0.26 | 0.57 | 0.55 / 0.80 | 0.08 / -0.95 / 0.74 | -0.00 | -0.33 | 0.98 | -0.18 | 0.38 | 448 | NO |
| YM 6 | driver RTY resid5m>=2.5 dir=with X hold=30m corr60 lo0.5 | 659 | 2 | 0.47 | -0.86 | 0.88 | 1.50 / 0.07 | 0.04 / -0.05 / 0.36 | 0.03 | -0.10 | 1.00 | -0.07 | 0.25 | 937 | NO |
| YM 7 | driver RTY resid15m>=1.5 dir=with X hold=30m corr60 lo0.5 | 1014 | 2 | 0.31 | -0.81 | 0.77 | 1.54 / -0.36 | 0.00 / -0.08 / 0.47 | -0.02 | -0.20 | 1.00 | -0.09 | 0.00 | 1401 | NO |
| YM 8 (diag) | driver ES resid5m>=2.5 dir=against X hold=30m corr60 lo0.5 | 347 | 1 | 0.69 | -0.19 | 0.80 | 0.94 / 0.54 | 0.09 / -0.46 / 0.87 | 0.08 | -0.21 | 1.00 | -0.06 | 0.12 | 613 | diag |
| YM 9 (diag) | driver ES resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | 447 | 1 | 0.59 | -0.43 | 0.37 | 0.23 / 0.10 | 0.07 / -0.78 / 0.61 | -0.04 | -0.29 | 1.00 | -0.19 | 0.25 | 829 | diag |
| YM 10 (diag) | driver ES resid5m>=2.5 dir=against X hold=30m corr60 hi0.7 | 411 | 1 | 0.38 | -0.66 | -0.09 | -0.60 / 0.59 | -0.01 / 0.47 / -0.79 | -0.21 | -0.22 | 0.94 | -0.38 | 0.00 | 659 | diag |
| GC 1 (diag) | driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | 89 | 1 | 0.42 | -0.68 | 0.24 | 0.14 / 0.86 | 0.07 / 0.22 / -0.17 | -0.03 | 0.14 | 0.92 | -0.28 | 0.38 | 126 | diag |
| GC 2 (diag) | driver 6E resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | 140 | 1 | 0.22 | -0.05 | 0.41 | 0.60 / 1.42 | 0.00 / 0.40 / -0.39 | -0.08 | -0.52 | 0.88 | -0.42 | 0.00 | 216 | diag |
| GC 3 (diag) | driver ZN resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 77 | 1 | 0.10 | -0.42 | -0.43 | -0.91 / 1.18 | -0.03 / -0.06 / -0.63 | -0.21 | -0.32 | 0.32 | -0.47 | 0.00 | 111 | diag |
| CL 1 (diag) | driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | 6 | 2 | 1.11 | 0.08 | 0.83 | -0.90 / 0.90 | 0.21 / 0.00 / -0.03 | 0.12 |  | 1.00 | 0.01 | 0.25 | 7 S | diag |
| ZN 1 (diag) | driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | 64 | 0 | -0.64 | -0.50 | -0.43 | 0.10 / -2.94 | -0.18 / 0.09 / -0.02 | -0.29 | -0.07 | 1.00 | -0.29 | 0.00 | 84 S | diag |
| ZN 2 (diag) | driver 6E resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | 68 | 1 | -0.67 | -0.50 | -0.92 | -1.49 / -1.67 | -0.20 / -0.49 / -0.08 | -0.39 | -0.08 | 1.00 | -0.38 | 0.00 | 97 S | diag |
| ZN 3 (diag) | driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | 40 | 0 | -0.93 | -0.64 | -1.16 | -1.72 / -2.77 | -0.20 / -0.48 / -0.17 | -0.40 | -0.11 | 1.00 | -0.41 | 0.00 | 58 S | diag |
| BTC 1 | driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | 114 | 2 | 1.26 | -0.25 | 0.48 | -0.21 / -0.34 | 0.28 / -0.36 / -0.09 | 0.07 | 0.67 | 1.00 | -0.17 | 0.50 | 220 | NO |
| BTC 2 | driver NQ resid5m>=1.5 dir=with X hold=15m corr60 hi0.7 | 206 | 2 | 0.78 | -0.94 | 0.47 | 0.06 / -0.79 | 0.14 / -0.28 / 0.11 | 0.02 | 0.50 | 1.00 | -0.14 | 0.12 | 388 | NO |
| BTC 3 | driver NQ resid5m>=1.5 dir=with X hold=30m corr60 hi0.7 | 166 | 2 | 0.77 | -0.45 | -0.06 | -1.10 / -0.34 | 0.15 / -0.55 / -0.27 | -0.08 | 0.67 | 0.45 | -0.25 | 0.00 | 311 | NO |
| BTC 4 | driver ES resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | 121 | 2 | 0.33 | 0.58 | -0.26 | -0.92 / 2.33 | 0.09 / -0.73 / -0.08 | -0.10 | -0.06 | 0.51 | -0.30 | 0.00 | 235 | NO |
| BTC 5 (diag) | driver NQ resid15m>=1.5 dir=with X hold=15m corr60 hi0.7 | 139 | 1 | 1.29 | 0.19 | 0.49 | -0.42 / -0.79 | 0.25 / -0.69 / 0.12 | 0.05 | 0.66 | 1.00 | -0.13 | 0.50 | 264 | diag |
| BTC 6 (diag) | driver NQ resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | 66 | 2 | 1.08 | -0.45 | 0.16 | -0.89 / 0.76 | 0.18 / -0.70 / -0.18 | -0.04 | 0.49 | 0.80 | -0.26 | 0.00 | 122 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 31 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 30 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 6 |
| standalone pair-window Sharpe above own random-entry null p95 | 37 |
| worst-decile corr <= +0.30 | 37 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 8 |
| small-sample (<100 trades pair window) | 5 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | clean | 1.25 | 2.43 | -120681 | -84644 | 428089 | -169486 | 2.65 | 16.2 | 1.74 | -80921 | 263599 | -85974 |
| BTC driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | H1 | -0.90 | -1.08 | -283923 | -256174 | 978829 | -286625 | -0.40 | 25.0 | 2.46 | -75816 | 164067 | -83140 |
| BTC driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | H2 | 0.34 | 0.49 | -272741 | -191779 | 503352 | -360790 | 0.37 | 41.7 | 2.39 | -121026 | 233773 | -154682 |
| BTC driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | all | 0.48 | 0.69 | -216993 | -155271 | 1277984 | -360790 | 0.73 | 23.2 | 2.01 | -90701 | 263599 | -154682 |
| CL driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | clean | 1.11 | 24.65 | -4777 | -2605 | 28660 | -28660 | 35.02 | 1.0 | 1.67 | -78736 | 280110 | -81874 |
| CL driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | H1 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.83 | -77610 | 151713 | -78287 |
| CL driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | H2 | -1.20 | -1.20 | -22238 | -11119 | 44476 | -44476 | -1.00 | 2.8 | 2.46 | -81089 | 217425 | -82524 |
| CL driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | all | 0.83 | 10.09 | -8126 | -4302 | 44476 | -44476 | 21.57 | 1.2 | 2.02 | -79220 | 280110 | -82524 |
| ES driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 (diag) | clean | 1.40 | 2.74 | -101000 | -85940 | 527924 | -127790 | 2.40 | 34.3 | 1.74 | -80864 | 256949 | -83563 |
| ES driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 (diag) | H1 | 2.21 | 5.13 | -112842 | -104448 | 269547 | -128337 | 3.10 | 35.7 | 3.63 | -70788 | 128790 | -78661 |
| ES driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 (diag) | H2 | -2.34 | -2.51 | -172554 | -132440 | 859389 | -182723 | -0.78 | 44.4 | 1.97 | -92910 | 270719 | -93138 |
| ES driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 (diag) | all | 0.88 | 1.56 | -122645 | -102729 | 859389 | -182723 | 1.66 | 36.9 | 2.07 | -84378 | 270719 | -93138 |
| GC driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 (diag) | clean | 0.42 | 0.66 | -136727 | -113357 | 897132 | -167568 | 0.43 | 23.8 | 1.53 | -82960 | 290856 | -102714 |
| GC driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 (diag) | H1 | 0.24 | 0.43 | -136107 | -120122 | 232237 | -144084 | 0.31 | 17.9 | 3.05 | -59901 | 169343 | -76932 |
| GC driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 (diag) | H2 | 0.11 | 0.16 | -428980 | -347706 | 1308320 | -483163 | 0.08 | 25.0 | 2.32 | -146267 | 247199 | -174048 |
| GC driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 (diag) | all | 0.24 | 0.34 | -247545 | -188067 | 1308320 | -483163 | 0.42 | 23.2 | 1.93 | -96661 | 290856 | -174048 |
| NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | clean | 2.55 | 5.23 | -89419 | -79552 | 307321 | -104080 | 7.58 | 33.3 | 1.95 | -84357 | 238488 | -97859 |
| NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | H1 | 3.23 | 8.56 | -75764 | -69845 | 230355 | -88167 | 3.93 | 28.6 | 3.62 | -64835 | 181370 | -69519 |
| NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | H2 | 0.11 | 0.15 | -293001 | -244419 | 847084 | -347051 | 0.09 | 47.2 | 2.50 | -101423 | 271337 | -122332 |
| NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | all | 1.66 | 2.76 | -170911 | -130051 | 847084 | -347051 | 3.90 | 35.7 | 2.33 | -87452 | 271337 | -122332 |
| RTY driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | clean | 0.90 | 1.48 | -116778 | -102838 | 667315 | -134438 | 1.25 | 35.2 | 1.62 | -84024 | 339449 | -104058 |
| RTY driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | H1 | -0.00 | -0.01 | -292423 | -231599 | 458913 | -385447 | -0.00 | 39.3 | 2.83 | -69529 | 153400 | -78287 |
| RTY driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | H2 | -0.59 | -0.79 | -299691 | -234893 | 885026 | -306072 | -0.39 | 47.2 | 2.33 | -84687 | 238488 | -85175 |
| RTY driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | all | 0.25 | 0.34 | -212940 | -158895 | 885026 | -385447 | 0.56 | 38.1 | 1.96 | -84235 | 339449 | -104058 |
| YM driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | clean | 0.71 | 1.26 | -104817 | -88569 | 401888 | -174988 | 1.61 | 44.8 | 1.51 | -88984 | 278779 | -99232 |
| YM driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | H1 | 1.01 | 1.70 | -100248 | -87342 | 281520 | -111032 | 0.79 | 39.3 | 2.86 | -84157 | 166724 | -96180 |
| YM driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | H2 | 2.70 | 5.95 | -83118 | -77880 | 293136 | -89931 | 3.02 | 25.0 | 3.01 | -81431 | 215324 | -84929 |
| YM driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | all | 1.21 | 2.21 | -102148 | -87428 | 475556 | -174988 | 3.69 | 39.9 | 2.04 | -88442 | 278779 | -99232 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | clean | -0.64 | -0.80 | -187288 | -136199 | 870747 | -262612 | -0.67 | 23.8 | 1.28 | -105485 | 313453 | -129531 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | H1 | 0.58 | 0.88 | -58641 | -42308 | 129026 | -100101 | 0.51 | 14.3 | 2.91 | -77610 | 149118 | -78287 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | H2 | -0.16 | -0.26 | -85024 | -71833 | 242976 | -92563 | -0.13 | 16.7 | 2.47 | -79836 | 208800 | -82524 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | all | -0.43 | -0.56 | -156550 | -114713 | 870747 | -262612 | -0.63 | 20.8 | 1.77 | -96868 | 313453 | -129531 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 (diag) | -14.4 | -10.1 | 16.4 | 2.6 | 22.7 / 25.8 | 29.3 / 35.7 | NO |
| NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | 6.2 | -47.3 | 10.7 | 14.3 | -4.0 / 17.4 | 38.3 / 42.0 | NO |
| RTY driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | -24.6 | -14.3 | 15.5 | -1.8 | -15.2 / 17.1 | 3.8 / 16.2 | NO |
| YM driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | -10.8 | -5.0 | 9.8 | 15.3 | -5.9 / 8.2 | -4.3 / 7.1 | NO |
| GC driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 (diag) | -23.9 | -141.3 | -9.4 | -30.1 | -12.9 / 17.8 | 31.2 / 36.9 | NO |
| CL driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | -19.5 | 30.0 | 30.0 | 30.0 | 30.0 / 30.0 | 30.0 / 30.0 | NO |
| ZN driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 (diag) | -36.0 | -60.8 | -4.6 | 10.4 | -62.1 / -22.3 | 30.0 / 30.0 | NO |
| BTC driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | -19.8 | -101.2 | 2.3 | 18.5 | 20.5 / 25.8 | -32.9 / 2.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) driver NQ resid15m>=2.5 dir=with X hold=15m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 1002 | 0.8 | -28.5 | -15.0 | 29.4 | 0.03 / -1.01 / -0.53 | 89.2 / 59.8 |
| ES 2 (diag) driver NQ resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | negative pre-2023 | 925 | -3.4 | -32.8 | -19.1 | 29.4 | -0.08 / -0.81 / -0.47 | 100.6 / 71.2 |
| ES 3 (diag) driver NQ resid5m>=2.5 dir=against X hold=15m corr60 lo0.5 | gross-positive, cost-negative pre-2023 | 334 | 1.6 | -27.8 | -15.2 | 29.4 | 0.05 / -0.79 / -0.45 | 88.2 / 58.8 |
| NQ 1 driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | positive pre-2023 | 1804 | 35.1 | 20.7 | 26.8 | 14.4 | 0.76 / 0.46 / 0.59 | 123.4 / 109.0 |
| NQ 2 driver ES resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | positive pre-2023 | 1002 | 16.9 | 2.5 | 10.7 | 14.4 | 0.34 / 0.05 / 0.22 | 228.4 / 214.0 |
| NQ 3 driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | positive pre-2023 | 925 | 17.9 | 3.6 | 11.8 | 14.4 | 0.23 / 0.05 / 0.15 | 251.7 / 237.3 |
| NQ 4 driver ES resid15m>=1.5 dir=against X hold=30m corr60 hi0.7 | positive pre-2023 | 4029 | 23.7 | 9.3 | 17.4 | 14.4 | 0.87 / 0.35 / 0.65 | 85.8 / 71.4 |
| NQ 5 driver RTY resid5m>=1.5 dir=with X hold=30m corr60 hi0.7 | positive pre-2023 | 4905 | 18.5 | 4.1 | 10.8 | 14.4 | 0.52 / 0.12 / 0.30 | 55.2 / 40.9 |
| NQ 6 driver YM resid15m>=2.5 dir=against X hold=15m corr60 lo0.5 | gross-positive, cost-negative pre-2023 | 2293 | 13.8 | -0.5 | 5.4 | 14.4 | 0.41 / -0.03 / 0.15 | 41.8 / 27.5 |
| NQ 7 driver ES resid5m>=2.5 dir=against X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 1741 | 14.5 | 0.1 | 8.4 | 14.4 | 0.25 / -0.00 / 0.15 | 101.6 / 87.2 |
| NQ 8 driver RTY resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | positive pre-2023 | 1866 | 50.9 | 36.6 | 42.1 | 14.4 | 1.05 / 0.76 / 0.87 | 48.7 / 34.4 |
| NQ 9 driver YM resid5m>=2.5 dir=against X hold=30m corr60 lo0.5 | positive pre-2023 | 2531 | 30.9 | 16.6 | 22.6 | 14.4 | 0.76 / 0.42 / 0.56 | 45.1 / 30.7 |
| NQ 10 driver YM resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | positive pre-2023 | 3446 | 30.4 | 16.1 | 22.0 | 14.4 | 0.89 / 0.48 / 0.65 | 32.6 / 18.2 |
| RTY 1 driver ES resid5m>=2.5 dir=with X hold=30m corr60 lo0.5 | negative pre-2023 | 766 | -10.8 | -25.1 | -24.2 | 14.4 | -0.29 / -0.69 / -0.66 | 36.5 / 22.1 |
| RTY 2 driver NQ resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | positive pre-2023 | 670 | 22.2 | 7.9 | 10.4 | 14.4 | 0.94 / 0.33 / 0.44 | 43.2 / 28.8 |
| RTY 3 driver NQ resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | positive pre-2023 | 610 | 15.6 | 1.3 | 3.8 | 14.4 | 0.42 / 0.03 / 0.10 | 45.9 / 31.6 |
| RTY 4 driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 694 | -12.6 | -26.9 | -24.6 | 14.4 | -0.35 / -0.76 / -0.69 | 50.0 / 35.6 |
| RTY 5 driver ES resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | negative pre-2023 | 503 | -18.6 | -32.9 | -32.2 | 14.4 | -0.39 / -0.69 / -0.67 | 32.8 / 18.5 |
| RTY 6 driver YM resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 3165 | 0.8 | -13.6 | -11.3 | 14.4 | 0.05 / -1.02 / -0.85 | 25.8 / 11.4 |
| RTY 7 driver YM resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | negative pre-2023 | 727 | -5.0 | -19.3 | -16.9 | 14.4 | -0.14 / -0.54 / -0.47 | 37.6 / 23.2 |
| RTY 8 driver ES resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 759 | 5.3 | -9.0 | -6.7 | 14.4 | 0.22 / -0.36 / -0.27 | 33.9 / 19.6 |
| RTY 9 driver ES resid5m>=2.5 dir=with X hold=15m corr60 lo0.5 | negative pre-2023 | 980 | -13.5 | -27.9 | -27.0 | 14.4 | -0.61 / -1.23 / -1.19 | 21.1 / 6.7 |
| RTY 10 driver YM resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | gross-positive, cost-negative pre-2023 | 2007 | 6.1 | -8.2 | -6.7 | 14.4 | 0.40 / -0.57 / -0.47 | 14.3 / -0.0 |
| YM 1 driver ES resid15m>=2.5 dir=against X hold=15m corr60 lo0.5 | negative pre-2023 | 98 | -1.5 | -15.9 | -11.3 | 14.4 | -0.03 / -0.28 / -0.20 | 32.9 / 18.5 |
| YM 2 driver RTY resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 725 | -10.4 | -24.8 | -20.7 | 14.4 | -0.18 / -0.42 / -0.36 | 43.9 / 29.5 |
| YM 3 driver NQ resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 1157 | -0.4 | -14.8 | -8.8 | 14.4 | -0.01 / -0.48 / -0.29 | 51.9 / 37.5 |
| YM 4 driver RTY resid15m>=2.5 dir=with X hold=30m corr60 lo0.5 | negative pre-2023 | 973 | -16.2 | -30.6 | -26.8 | 14.4 | -0.60 / -1.10 / -0.97 | 33.2 / 18.9 |
| YM 5 driver ES resid15m>=2.5 dir=against X hold=30m corr60 lo0.5 | negative pre-2023 | 94 | -7.2 | -21.5 | -16.9 | 14.4 | -0.09 / -0.26 / -0.21 | 34.0 / 19.7 |
| YM 6 driver RTY resid5m>=2.5 dir=with X hold=30m corr60 lo0.5 | negative pre-2023 | 1396 | -5.5 | -19.8 | -16.0 | 14.4 | -0.25 / -0.86 / -0.70 | 24.3 / 9.9 |
| YM 7 driver RTY resid15m>=1.5 dir=with X hold=30m corr60 lo0.5 | gross-positive, cost-negative pre-2023 | 2077 | 1.1 | -13.3 | -9.5 | 14.4 | 0.06 / -0.81 / -0.58 | 18.5 / 4.2 |
| YM 8 (diag) driver ES resid5m>=2.5 dir=against X hold=30m corr60 lo0.5 | gross-positive, cost-negative pre-2023 | 146 | 2.7 | -11.6 | -6.6 | 14.4 | 0.04 / -0.19 / -0.11 | 32.9 / 18.6 |
| YM 9 (diag) driver ES resid15m>=1.5 dir=against X hold=30m corr60 lo0.5 | negative pre-2023 | 225 | -2.4 | -16.8 | -11.5 | 14.4 | -0.06 / -0.43 / -0.29 | 27.1 / 12.7 |
| YM 10 (diag) driver ES resid5m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 1106 | -8.3 | -22.7 | -18.0 | 14.4 | -0.24 / -0.66 / -0.52 | 26.7 / 12.3 |
| GC 1 (diag) driver ZN resid15m>=2.5 dir=against X hold=15m corr60 hi0.7 | negative pre-2023 | 246 | -35.5 | -59.9 | -50.9 | 24.4 | -0.40 / -0.68 / -0.58 | 48.9 / 24.5 |
| GC 2 (diag) driver 6E resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 576 | 20.9 | -3.4 | 6.3 | 24.4 | 0.33 / -0.05 / 0.10 | 45.1 / 20.7 |
| GC 3 (diag) driver ZN resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 224 | -29.7 | -54.1 | -45.1 | 24.4 | -0.23 / -0.42 / -0.35 | 36.0 / 11.6 |
| CL 1 (diag) driver ZN resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | positive pre-2023 | 25 | 58.8 | 34.4 | 31.5 | 24.4 | 0.14 / 0.08 / 0.07 | 341.7 / 317.3 |
| ZN 1 (diag) driver 6J resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 274 | 18.1 | -17.5 | -22.0 | 35.6 | 0.51 / -0.50 / -0.62 | 16.8 / -18.8 |
| ZN 2 (diag) driver 6E resid15m>=2.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 171 | 14.5 | -21.1 | -25.6 | 35.6 | 0.35 / -0.50 / -0.60 | 17.0 / -18.6 |
| ZN 3 (diag) driver ES resid15m>=2.5 dir=against X hold=30m corr60 hi0.7 | negative pre-2023 | 60 | -17.7 | -53.3 | -56.3 | 35.6 | -0.22 / -0.64 / -0.67 | 5.5 / -30.1 |
| BTC 1 driver NQ resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 298 | 33.1 | -21.2 | 12.1 | 54.4 | 0.39 / -0.25 / 0.14 | 430.3 / 375.9 |
| BTC 2 driver NQ resid5m>=1.5 dir=with X hold=15m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 538 | 8.3 | -46.0 | -12.6 | 54.4 | 0.17 / -0.94 / -0.26 | 224.3 / 169.9 |
| BTC 3 driver NQ resid5m>=1.5 dir=with X hold=30m corr60 hi0.7 | gross-positive, cost-negative pre-2023 | 398 | 23.0 | -31.4 | 2.1 | 54.4 | 0.33 / -0.45 / 0.03 | 263.1 / 208.7 |
| BTC 4 driver ES resid15m>=1.5 dir=with X hold=30m corr60 hi0.7 | positive pre-2023 | 276 | 86.7 | 32.3 | 65.9 | 54.4 | 1.53 / 0.58 / 1.17 | 160.1 / 105.8 |
| BTC 5 (diag) driver NQ resid15m>=1.5 dir=with X hold=15m corr60 hi0.7 | positive pre-2023 | 360 | 63.8 | 9.4 | 42.8 | 54.4 | 1.23 / 0.19 / 0.83 | 393.0 / 338.6 |
| BTC 6 (diag) driver NQ resid5m>=2.5 dir=with X hold=30m corr60 hi0.7 | negative pre-2023 | 174 | -14.9 | -69.3 | -35.9 | 54.4 | -0.10 / -0.45 / -0.23 | 594.7 / 540.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 4 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.11, p(top) = 0.14); CL: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00); NQ: 15 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.00, p(top) = 0.00); RTY: 10 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 0.00, p(top) = 0.00); YM: 7 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.00, p(top) = 0.06); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 31 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.43 (NQ driver YM resid15m>=2.5 dir=against X hold=30m corr60 lo0.5); bootstrap lower bound > 0 for 5 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 7; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 11, 'negative pre-2023': 11, 'gross-positive, cost-negative pre-2023': 9}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_26.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw26/ (`SW26_CO_all_selected_scored.csv`).

DONE SW26
