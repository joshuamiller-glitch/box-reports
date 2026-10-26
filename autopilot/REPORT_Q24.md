# REPORT Q24 - Q24: Sunday-open week structure: first-hour return of the week traded with/against for 2-12 h

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 21 selected cells (+30 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: Sunday-open week structure: first-hour return of the week traded with/against for 2-12 h. Time exit, no stop.
- Instruments: GC, SI, HG, PL, ZN, ZB, ZF, 6E, 6J, 6B. Grid: 24 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6B    |      24 |         18 |         0 |               0.834 |                1 |          0 |            3 |
| 6E    |      24 |         18 |         1 |               0.307 |                2 |          1 |            3 |
| 6J    |      24 |         24 |         3 |               1.108 |                2 |          3 |            3 |
| GC    |      24 |         24 |         3 |               0.586 |                2 |          3 |            3 |
| HG    |      24 |         24 |         3 |               1.183 |                2 |          3 |            3 |
| PL    |      24 |         24 |         4 |               0.688 |                2 |          4 |            3 |
| SI    |      24 |         24 |         6 |               0.783 |                2 |          6 |            3 |
| ZB    |      24 |         24 |         1 |               0.017 |                2 |          1 |            3 |
| ZF    |      24 |         24 |         0 |               0.161 |                1 |          0 |            3 |
| ZN    |      24 |         24 |         0 |              -0.275 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| GC    |     200 |                    3 |            3.895 |              10 |      0.8   |                       0.429 |            0.747 |           1.085 |    0.91  |       0.496 |                1.785 |
| SI    |     200 |                    6 |            3.235 |               8 |      0.12  |                       0.43  |            0.692 |           1.121 |    0.845 |       0.783 |                1.651 |
| HG    |     200 |                    3 |            3.33  |               8 |      0.675 |                       0.639 |            0.727 |           1.197 |    0.57  |       1.183 |                1.803 |
| PL    |     200 |                    4 |            4.005 |               9 |      0.565 |                       0.327 |            0.743 |           1.1   |    0.98  |       0.552 |                1.792 |
| ZN    |     200 |                    0 |            0.52  |               3 |      1     |                     nan     |            0.553 |           1.091 |  nan     |     nan     |                1.323 |
| ZB    |     200 |                    1 |            0.68  |               3 |      0.525 |                       0.017 |            0.565 |           1.056 |    0.525 |       0.017 |                1.238 |
| ZF    |     200 |                    0 |            0.93  |               4 |      1     |                     nan     |            0.635 |           1.192 |  nan     |     nan     |                1.309 |
| 6E    |     200 |                    1 |            1.48  |               5 |      0.755 |                       0.302 |            0.723 |           1.367 |    0.675 |       0.302 |                1.69  |
| 6J    |     200 |                    3 |            2.15  |               5 |      0.375 |                       0.837 |            0.698 |           1.247 |    0.285 |       1.108 |                1.583 |
| 6B    |     200 |                    0 |            0.73  |               4 |      1     |                     nan     |            0.617 |           1.415 |  nan     |     nan     |                1.456 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GC 1 | sun (60, 0.1, 360, -1) | 43 | 2 | 0.50 | 0.64 | -0.37 | -0.84 / 1.29 | 0.09 / -2.62 / 0.03 | -0.38 | 0.49 | 0.37 | -0.84 | 0.00 | 76 S | NO |
| GC 2 | sun (60, 0.0, 360, -1) | 104 | 2 | 0.46 | 0.33 | -0.24 | -0.64 / 1.43 | 0.08 / -2.29 / 0.19 | -0.29 | 0.51 | 0.39 | -0.71 | 0.00 | 167 | NO |
| GC 3 | sun (120, 0.0, 360, 1) | 104 | 2 | 0.33 | -0.58 | 0.13 | 0.08 / 1.57 | 0.01 / 1.49 / -1.59 | -0.12 | -0.20 | 0.62 | -0.47 | 0.00 | 167 | NO |
| GC 4 (diag) | sun (60, 0.1, 120, 1) | 43 | 1 | 0.59 | -1.19 | -0.04 | -0.32 / 1.29 | 0.07 / 1.08 / -1.75 | -0.23 | -0.44 | 0.58 | -0.74 | 0.00 | 76 S | diag |
| GC 5 (diag) | sun (120, 0.0, 720, 1) | 104 | 1 | 0.48 | -0.39 | 0.44 | 0.45 / 1.36 | 0.06 / 0.66 / -0.46 | 0.03 | -0.21 | 0.82 | -0.22 | 0.50 | 167 | diag |
| GC 6 (diag) | sun (60, 0.1, 720, 1) | 43 | 1 | 0.42 | -0.63 | 0.56 | 0.74 / 1.55 | 0.03 / 1.24 / -0.58 | 0.09 | -0.59 | 0.84 | -0.33 | 0.50 | 76 S | diag |
| SI 1 | sun (120, 0.1, 120, -1) | 43 | 2 | 0.78 | -0.95 | 0.50 | 0.54 / 1.50 | 0.09 / -0.22 / -0.31 | -0.03 | 0.09 | 0.87 | -0.38 | 1.00 | 85 S | NO |
| SI 2 | sun (120, 0.0, 120, -1) | 104 | 2 | 0.43 | -0.97 | 0.31 | 0.34 / 1.28 | 0.04 / -0.28 / -0.41 | -0.11 | 0.08 | 0.83 | -0.45 | 0.00 | 167 | NO |
| SI 3 | sun (60, 0.1, 360, -1) | 49 | 2 | 0.43 | 0.06 | -0.52 | -1.02 / 1.39 | 0.06 / -2.67 / -0.58 | -0.61 | 0.44 | 0.19 | -1.19 | 0.00 | 84 S | NO |
| SI 4 | sun (120, 0.0, 720, 1) | 104 | 2 | 0.40 | -0.24 | 0.80 | 1.20 / 1.43 | 0.06 / 0.45 / -0.14 | 0.08 | -0.11 | 0.97 | -0.21 | 0.00 | 167 | NO |
| SI 5 | sun (60, 0.1, 120, -1) | 49 | 2 | 0.40 | 0.51 | 0.38 | 0.56 / 1.00 | 0.03 / -1.42 / -0.73 | -0.54 | 0.21 | 0.91 | -1.22 | 0.00 | 84 S | NO |
| SI 6 | sun (120, 0.1, 360, -1) | 43 | 2 | 0.15 | -0.63 | 0.58 | 0.92 / 1.35 | -0.00 / -1.04 / 0.23 | -0.14 | -0.12 | 0.87 | -0.56 | 0.00 | 85 S | NO |
| SI 7 (diag) | sun (60, 0.1, 720, -1) | 49 | 1 | 0.39 | 0.19 | 0.13 | 0.08 / 1.29 | 0.03 / -0.93 / -0.59 | -0.25 | 0.41 | 0.65 | -0.61 | 0.00 | 84 S | diag |
| SI 8 (diag) | sun (120, 0.1, 720, -1) | 43 | 1 | 0.34 | -0.33 | -0.31 | -0.69 / 1.44 | 0.03 / -1.56 / -0.44 | -0.33 | -0.00 | 0.37 | -0.73 | 0.00 | 85 S | diag |
| SI 9 (diag) | sun (60, 0.0, 720, -1) | 104 | 1 | 0.08 | -0.21 | 0.04 | 0.03 / 1.33 | -0.02 / -1.38 / -0.17 | -0.27 | 0.24 | 0.58 | -0.65 | 0.00 | 167 | diag |
| HG 1 | sun (60, 0.1, 720, -1) | 42 | 2 | 1.18 | -0.12 | 0.89 | 0.40 / 1.18 | 0.19 / 0.01 / 0.20 | 0.14 | 0.15 | 0.96 | -0.02 | 0.00 | 70 S | NO |
| HG 2 | sun (60, 0.0, 720, -1) | 104 | 2 | 0.42 | -0.03 | -0.08 | -0.73 / 1.20 | 0.03 / -0.75 / 0.15 | -0.09 | 0.16 | 0.54 | -0.30 | 0.00 | 167 | NO |
| HG 3 | sun (60, 0.1, 360, -1) | 42 | 2 | 0.31 | -0.07 | 0.07 | -0.38 / 1.17 | 0.03 / -0.36 / 0.04 | -0.05 | -0.21 | 0.63 | -0.21 | 0.00 | 70 S | NO |
| HG 4 (diag) | sun (120, 0.0, 720, -1) | 104 | 1 | 0.86 | -0.04 | -0.01 | -1.11 / 1.12 | 0.16 / -0.92 / 0.10 | -0.04 | 0.12 | 0.62 | -0.24 | 0.00 | 167 | diag |
| HG 5 (diag) | sun (60, 0.0, 360, -1) | 104 | 1 | 0.49 | -0.12 | -0.07 | -0.85 / 1.65 | 0.06 / -0.84 / 0.10 | -0.11 | 0.29 | 0.63 | -0.27 | 0.00 | 167 | diag |
| HG 6 (diag) | sun (120, 0.1, 120, -1) | 45 | 1 | 0.12 | -0.37 | -0.50 | -1.27 / 1.23 | -0.01 / -1.09 / -0.23 | -0.25 | 0.22 | 0.27 | -0.47 | 0.00 | 74 S | diag |
| PL 1 | sun (120, 0.1, 120, -1) | 53 | 2 | 0.55 | 0.04 | 0.61 | 0.88 / 1.34 | 0.05 / -0.84 / -0.15 | -0.16 | 0.52 | 0.90 | -0.62 | 0.00 | 87 S | NO |
| PL 2 | sun (60, 0.0, 360, -1) | 102 | 2 | 0.39 | 0.29 | 0.29 | 0.40 / 1.46 | 0.03 / -2.36 / 0.99 | -0.19 | 0.36 | 0.77 | -0.73 | 0.00 | 164 | NO |
| PL 3 | sun (120, 0.0, 120, -1) | 104 | 2 | 0.33 | 0.14 | 0.86 | 1.37 / 1.33 | 0.01 / 0.17 / -0.26 | 0.02 | 0.39 | 0.95 | -0.41 | 1.00 | 167 | NO |
| PL 4 | sun (60, 0.0, 120, -1) | 102 | 2 | 0.04 | -0.28 | 0.72 | 1.21 / 1.36 | -0.03 / -1.02 / 0.49 | -0.06 | 0.18 | 0.95 | -0.59 | 0.00 | 164 | NO |
| PL 5 (diag) | sun (120, 0.1, 360, -1) | 53 | 1 | 0.69 | 0.16 | 0.03 | -0.05 / 1.13 | 0.07 / -3.11 / 0.20 | -0.65 | 0.24 | 0.60 | -1.43 | 0.00 | 87 S | diag |
| PL 6 (diag) | sun (60, 0.0, 720, -1) | 102 | 1 | 0.68 | -0.21 | 0.75 | 0.99 / 1.63 | 0.11 / -1.03 / 0.73 | 0.09 | 0.21 | 0.93 | -0.30 | 0.00 | 164 | diag |
| PL 7 (diag) | sun (60, 0.1, 120, -1) | 48 | 1 | 0.53 | 0.11 | 0.17 | 0.20 / 1.59 | 0.05 / -2.66 / 0.29 | -0.45 | 0.20 | 0.62 | -1.09 | 0.00 | 83 S | diag |
| ZN 1 (diag) | sun (60, 0.1, 360, -1) | 47 | 1 | -0.28 | -1.34 | -1.06 | -2.56 / 0.38 | -0.05 / -0.53 / -0.48 | -0.43 | 0.09 | 0.36 | -0.39 | 0.00 | 78 S | diag |
| ZN 2 (diag) | sun (60, 0.1, 120, -1) | 47 | 1 | -0.37 | -1.60 | -1.10 | -2.63 / -0.50 | -0.09 / -0.46 / -0.48 | -0.47 | 0.49 | 0.68 | -0.40 | 0.00 | 78 S | diag |
| ZN 3 (diag) | sun (120, 0.0, 720, 1) | 104 | 1 | -0.50 | -1.50 | -0.68 | -1.15 / 0.41 | -0.17 / -0.27 / -0.17 | -0.41 | 0.09 | 0.72 | -0.34 | 0.00 | 167 | diag |
| ZB 1 | sun (60, 0.1, 360, -1) | 48 | 2 | 0.02 | -0.74 | -0.91 | -2.44 / 0.45 | 0.02 / -0.56 / -0.56 | -0.41 | 0.24 | 0.37 | -0.38 | 0.00 | 76 S | NO |
| ZB 2 (diag) | sun (120, 0.1, 720, 1) | 60 | 1 | -0.35 | -0.73 | -0.52 | -0.99 / 0.73 | -0.16 / -0.22 / -0.12 | -0.32 | -0.13 | 0.57 | -0.33 | 0.00 | 97 S | diag |
| ZB 3 (diag) | sun (60, 0.1, 720, 1) | 48 | 1 | -0.52 | -0.79 | -0.36 | 0.16 / 0.54 | -0.17 / 0.31 / -0.12 | -0.23 | 0.02 | 0.69 | -0.28 | 0.00 | 76 S | diag |
| ZB 4 (diag) | sun (60, 0.1, 120, -1) | 48 | 0 | -0.71 | -1.25 | -1.29 | -2.34 / -0.56 | -0.14 / -0.46 / -0.45 | -0.49 | 0.42 | 0.48 | -0.44 | 0.00 | 76 S | diag |
| ZF 1 (diag) | sun (60, 0.1, 360, -1) | 52 | 1 | 0.16 | -1.21 | -0.66 | -2.40 / 0.57 | 0.03 / -0.44 / -0.52 | -0.31 | -0.08 | 0.56 | -0.33 | 0.00 | 83 S | diag |
| ZF 2 (diag) | sun (60, 0.1, 120, -1) | 52 | 1 | 0.08 | -1.56 | -0.53 | -2.00 / 0.29 | -0.01 / -0.24 / -0.45 | -0.31 | 0.29 | 0.91 | -0.29 | 0.00 | 83 S | diag |
| ZF 3 (diag) | sun (120, 0.1, 720, 1) | 55 | 1 | -0.31 | -0.83 | -0.69 | -1.53 / 0.62 | -0.12 / -0.47 / -0.15 | -0.31 | 0.17 | 0.46 | -0.35 | 0.00 | 90 S | diag |
| 6E 1 | sun (120, 0.0, 720, -1) | 104 | 2 | 0.30 | -0.40 | 0.01 | -0.13 / 1.17 | 0.04 / -0.08 / 0.14 | -0.01 | 0.46 | 0.59 | -0.15 | 1.00 | 167 | NO |
| 6E 2 (diag) | sun (60, 0.1, 720, 1) | 28 | 1 | 0.31 | -0.37 | -0.20 | -0.79 / 1.30 | -0.01 / -0.32 / -0.35 | -0.16 | -0.57 | 0.56 | -0.32 | 0.00 | 54 S | diag |
| 6E 3 (diag) | sun (60, 0.1, 360, 1) | 28 | 1 | 0.29 | -0.62 | -0.35 | -1.35 / 0.89 | -0.03 / -0.48 / -0.43 | -0.24 | -0.22 | 0.46 | -0.40 | 0.00 | 54 S | diag |
| 6E 4 (diag) | sun (120, 0.0, 360, 1) | 104 | 1 | 0.16 | -0.75 | -0.46 | -1.61 / 1.13 | -0.06 / -0.17 / -0.67 | -0.31 | -0.24 | 0.48 | -0.40 | 0.00 | 167 | diag |
| 6J 1 | sun (60, 0.0, 120, -1) | 101 | 2 | 1.11 | 0.13 | 0.48 | -0.89 / 0.45 | 0.19 / -0.13 / -0.26 | -0.06 | -0.16 | 0.99 | -0.13 | 0.00 | 163 | NO |
| 6J 2 | sun (120, 0.1, 360, -1) | 53 | 2 | 0.92 | -0.53 | 0.53 | -0.10 / 1.00 | 0.14 / -0.00 / -0.05 | 0.05 | 0.24 | 0.96 | -0.11 | 0.50 | 91 S | NO |
| 6J 3 | sun (120, 0.0, 360, -1) | 104 | 2 | 0.48 | -0.74 | 0.16 | -0.32 / 0.99 | 0.06 / 0.08 / -0.08 | -0.03 | 0.22 | 0.83 | -0.16 | 0.00 | 167 | NO |
| 6J 4 (diag) | sun (120, 0.1, 720, -1) | 53 | 1 | 0.38 | -0.58 | 0.05 | -0.26 / 1.48 | 0.02 / -0.03 / -0.04 | -0.03 | 0.01 | 0.71 | -0.18 | 0.50 | 91 S | diag |
| 6J 5 (diag) | sun (60, 0.0, 360, -1) | 101 | 1 | 0.37 | -0.06 | -0.13 | -1.22 / 0.82 | 0.02 / -0.06 / -0.19 | -0.10 | 0.06 | 0.75 | -0.23 | 0.00 | 163 | diag |
| 6J 6 (diag) | sun (60, 0.1, 720, -1) | 41 | 1 | 0.12 | -0.04 | -0.27 | -0.75 / 1.18 | -0.06 / 0.08 / -0.17 | -0.10 | 0.10 | 0.46 | -0.26 | 0.00 | 73 S | diag |
| 6B 1 (diag) | sun (60, 0.1, 120, 1) | 33 | 1 | 0.83 | -0.52 | 0.02 | -1.32 / 1.19 | 0.06 / -0.58 / -0.21 | -0.24 | -0.07 | 0.78 | -0.26 | 0.00 | 56 S | diag |
| 6B 2 (diag) | sun (60, 0.1, 720, 1) | 33 | 1 | 0.28 | -0.67 | -0.35 | -1.75 / 1.20 | -0.01 / -0.20 / -0.41 | -0.18 | -0.61 | 0.36 | -0.29 | 0.00 | 56 S | diag |
| 6B 3 (diag) | sun (120, 0.0, 720, -1) | 104 | 1 | -0.09 | -0.28 | 0.00 | 0.12 / 0.94 | -0.02 / -0.06 / 0.17 | -0.07 | 0.26 | 0.85 | -0.17 | 0.50 | 167 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 21 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 41 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 31 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6B sun (120, 0.0, 720, -1) (diag) | clean | -0.05 | -0.07 | -144809 | -121392 | 410465 | -179485 | -0.11 | 46.7 | 1.44 | -92126 | 287337 | -110175 |
| 6B sun (120, 0.0, 720, -1) (diag) | H1 | 0.02 | 0.03 | -72980 | -67201 | 202370 | -77109 | 0.02 | 50.0 | 2.77 | -81473 | 160660 | -83471 |
| 6B sun (120, 0.0, 720, -1) (diag) | H2 | 0.19 | 0.29 | -76283 | -70091 | 159438 | -85365 | 0.28 | 52.8 | 2.65 | -76072 | 213593 | -77976 |
| 6B sun (120, 0.0, 720, -1) (diag) | all | 0.00 | 0.00 | -132333 | -104014 | 410465 | -179485 | 0.01 | 48.8 | 1.91 | -88449 | 287337 | -110175 |
| 6E sun (120, 0.0, 720, -1) | clean | 0.08 | 0.11 | -152430 | -117062 | 414659 | -203230 | 0.19 | 45.7 | 1.50 | -87900 | 281616 | -105703 |
| 6E sun (120, 0.0, 720, -1) | H1 | -0.93 | -1.24 | -82361 | -76469 | 271425 | -91438 | -0.63 | 53.6 | 2.75 | -76692 | 156317 | -78230 |
| 6E sun (120, 0.0, 720, -1) | H2 | 0.43 | 0.67 | -94782 | -85227 | 220560 | -99082 | 0.52 | 50.0 | 2.62 | -82683 | 224954 | -84760 |
| 6E sun (120, 0.0, 720, -1) | all | 0.01 | 0.02 | -133267 | -105714 | 640729 | -203230 | 0.03 | 48.2 | 1.94 | -85666 | 281616 | -105703 |
| 6J sun (120, 0.1, 360, -1) | clean | 0.77 | 1.10 | -118936 | -74164 | 416213 | -396050 | 1.63 | 20.0 | 1.60 | -89725 | 257388 | -131375 |
| 6J sun (120, 0.1, 360, -1) | H1 | 0.15 | 0.22 | -85326 | -66806 | 208903 | -87384 | 0.10 | 32.1 | 2.82 | -74550 | 158132 | -76932 |
| 6J sun (120, 0.1, 360, -1) | H2 | -0.29 | -0.46 | -63376 | -55831 | 158847 | -66806 | -0.32 | 33.3 | 2.43 | -81712 | 217425 | -86008 |
| 6J sun (120, 0.1, 360, -1) | all | 0.53 | 0.77 | -110553 | -74553 | 416213 | -396050 | 1.56 | 25.0 | 1.98 | -86559 | 257388 | -131375 |
| GC sun (120, 0.0, 360, 1) | clean | 0.36 | 0.56 | -119742 | -97262 | 383942 | -167652 | 0.84 | 53.3 | 1.47 | -88571 | 282691 | -100898 |
| GC sun (120, 0.0, 360, 1) | H1 | 2.40 | 10.24 | -216593 | -184996 | 338620 | -244926 | 7.71 | 32.1 | 4.32 | -78788 | 128150 | -81526 |
| GC sun (120, 0.0, 360, 1) | H2 | -2.38 | -2.55 | -585963 | -437983 | 3311566 | -786361 | -0.74 | 55.6 | 0.90 | -117060 | 362817 | -122663 |
| GC sun (120, 0.0, 360, 1) | all | 0.13 | 0.22 | -325292 | -249290 | 3311566 | -786361 | 0.15 | 50.6 | 1.79 | -98395 | 362817 | -122663 |
| HG sun (60, 0.1, 720, -1) | clean | 1.23 | 2.82 | -98809 | -70923 | 202800 | -187885 | 5.52 | 18.1 | 1.65 | -81123 | 281936 | -91391 |
| HG sun (60, 0.1, 720, -1) | H1 | -0.64 | -0.74 | -139784 | -117920 | 288065 | -170394 | -0.41 | 14.3 | 2.84 | -70161 | 146533 | -78287 |
| HG sun (60, 0.1, 720, -1) | H2 | 0.86 | 1.33 | -207320 | -159705 | 588627 | -209263 | 0.65 | 13.9 | 2.68 | -79970 | 217425 | -82524 |
| HG sun (60, 0.1, 720, -1) | all | 0.89 | 1.55 | -145992 | -106373 | 588627 | -209263 | 2.35 | 16.7 | 2.05 | -80552 | 281936 | -91391 |
| PL sun (120, 0.0, 120, -1) | clean | 0.22 | 0.35 | -115210 | -95968 | 497268 | -138572 | 0.40 | 47.6 | 1.47 | -89589 | 311571 | -102957 |
| PL sun (120, 0.0, 120, -1) | H1 | 1.92 | 5.33 | -592351 | -501972 | 774615 | -754465 | 4.95 | 39.3 | 3.00 | -137446 | 210530 | -162460 |
| PL sun (120, 0.0, 120, -1) | H2 | 0.70 | 1.19 | -436608 | -344224 | 906584 | -590227 | 0.97 | 50.0 | 2.22 | -117910 | 292851 | -119017 |
| PL sun (120, 0.0, 120, -1) | all | 0.86 | 1.98 | -365265 | -271661 | 906584 | -754465 | 5.42 | 47.0 | 1.97 | -111193 | 311571 | -162460 |
| SI sun (120, 0.0, 720, 1) | clean | 0.40 | 0.59 | -135930 | -107483 | 531153 | -267439 | 0.68 | 49.5 | 1.52 | -86524 | 266660 | -104101 |
| SI sun (120, 0.0, 720, 1) | H1 | 2.05 | 4.42 | -220882 | -178874 | 310784 | -310784 | 4.16 | 50.0 | 3.27 | -95699 | 174593 | -95904 |
| SI sun (120, 0.0, 720, 1) | H2 | 0.60 | 0.91 | -393864 | -286302 | 1397152 | -518683 | 0.39 | 47.2 | 2.34 | -117921 | 216367 | -133462 |
| SI sun (120, 0.0, 720, 1) | all | 0.80 | 1.32 | -236222 | -179944 | 1525341 | -518683 | 1.44 | 49.4 | 2.02 | -97442 | 266660 | -133462 |
| ZB sun (60, 0.1, 360, -1) | clean | -0.01 | -0.01 | -114381 | -97277 | 445021 | -152007 | -0.02 | 28.6 | 1.48 | -83025 | 261959 | -92359 |
| ZB sun (60, 0.1, 360, -1) | H1 | -3.15 | -3.02 | -114381 | -105422 | 477272 | -119756 | -1.00 | 28.6 | 2.27 | -88510 | 175664 | -98734 |
| ZB sun (60, 0.1, 360, -1) | H2 | -2.27 | -2.46 | -189634 | -170821 | 1010048 | -195010 | -0.82 | 33.3 | 1.92 | -92090 | 217425 | -100025 |
| ZB sun (60, 0.1, 360, -1) | all | -0.91 | -1.24 | -147229 | -122918 | 1882586 | -195010 | -0.70 | 29.8 | 1.71 | -87081 | 261959 | -100025 |
| ZF sun (60, 0.1, 120, -1) (diag) | clean | 0.08 | 0.16 | -107474 | -87280 | 305410 | -134563 | 0.24 | 27.6 | 1.45 | -82908 | 271676 | -89343 |
| ZF sun (60, 0.1, 120, -1) (diag) | H1 | -0.29 | -0.45 | -69549 | -66840 | 177085 | -77676 | -0.23 | 17.9 | 2.59 | -83752 | 151713 | -89217 |
| ZF sun (60, 0.1, 120, -1) (diag) | H2 | -3.08 | -3.24 | -122373 | -104088 | 886184 | -158944 | -0.83 | 50.0 | 2.04 | -97131 | 234586 | -99685 |
| ZF sun (60, 0.1, 120, -1) (diag) | all | -0.53 | -0.88 | -110183 | -91061 | 1131300 | -158944 | -0.62 | 31.0 | 1.77 | -86985 | 271676 | -99685 |
| ZN sun (120, 0.0, 720, 1) (diag) | clean | -0.51 | -0.64 | -151309 | -125014 | 712000 | -236689 | -0.65 | 54.3 | 1.29 | -95266 | 275879 | -106718 |
| ZN sun (120, 0.0, 720, 1) (diag) | H1 | -2.00 | -2.11 | -87710 | -79869 | 293457 | -111233 | -0.95 | 53.6 | 2.56 | -76333 | 161997 | -78579 |
| ZN sun (120, 0.0, 720, 1) (diag) | H2 | -0.61 | -0.91 | -69414 | -61573 | 410161 | -69414 | -0.33 | 58.3 | 2.31 | -90059 | 219054 | -96407 |
| ZN sun (120, 0.0, 720, 1) (diag) | all | -0.68 | -0.86 | -136208 | -107543 | 1163973 | -236689 | -0.75 | 55.4 | 1.71 | -92823 | 275879 | -106718 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| GC sun (120, 0.0, 360, 1) | -24.6 | -117.6 | -30.3 | -128.6 | -9.4 / 9.2 | 23.8 / 27.7 | NO |
| SI sun (120, 0.0, 720, 1) | -5.9 | -65.4 | -21.1 | -18.0 | -15.5 / 13.7 | -42.7 / -25.0 | NO |
| HG sun (60, 0.1, 720, -1) | -14.9 | 9.2 | 24.5 | 29.0 | 8.5 / 25.5 | 30.0 / 38.7 | NO |
| PL sun (120, 0.0, 120, -1) | 23.8 | -184.1 | -62.3 | -7.0 | -13.4 / 8.4 | -199.5 / -146.1 | NO |
| ZN sun (120, 0.0, 720, 1) (diag) | -39.6 | -19.2 | 2.2 | 24.1 | -20.1 / -3.6 | 29.4 / 32.5 | NO |
| ZB sun (60, 0.1, 360, -1) | -44.4 | -4.9 | 10.0 | 31.7 | 6.0 / 19.3 | -10.6 / 2.2 | NO |
| ZF sun (60, 0.1, 120, -1) (diag) | -37.7 | -1.2 | 14.5 | 21.4 | 11.6 / 21.0 | 7.7 / 18.1 | NO |
| 6E sun (120, 0.0, 720, -1) | -29.8 | -12.8 | 15.5 | 29.2 | -13.7 / 10.2 | 27.5 / 28.2 | NO |
| 6J sun (120, 0.1, 360, -1) | -22.9 | -88.2 | 12.8 | 15.3 | -89.7 / 4.7 | 31.2 / 35.9 | NO |
| 6B sun (120, 0.0, 720, -1) (diag) | -30.0 | -20.9 | 7.9 | 20.9 | -21.9 / -0.3 | 20.1 / 22.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| GC 1 sun (60, 0.1, 360, -1) | positive pre-2023 | 201 | 122.0 | 97.6 | 107.3 | 24.4 | 0.79 / 0.64 / 0.70 | 174.9 / 150.5 |
| GC 2 sun (60, 0.0, 360, -1) | positive pre-2023 | 546 | 49.0 | 24.9 | 34.6 | 24.1 | 0.63 / 0.33 / 0.45 | 97.8 / 73.8 |
| GC 3 sun (120, 0.0, 360, 1) | negative pre-2023 | 549 | -20.3 | -44.2 | -34.6 | 23.8 | -0.27 / -0.58 / -0.46 | 84.3 / 60.4 |
| GC 4 (diag) sun (60, 0.1, 120, 1) | negative pre-2023 | 201 | -92.7 | -117.1 | -107.4 | 24.4 | -0.95 / -1.19 / -1.09 | 158.1 / 133.8 |
| GC 5 (diag) sun (120, 0.0, 720, 1) | negative pre-2023 | 549 | -28.3 | -52.1 | -42.6 | 23.8 | -0.21 / -0.39 / -0.32 | 151.7 / 127.8 |
| GC 6 (diag) sun (60, 0.1, 720, 1) | negative pre-2023 | 201 | -122.9 | -147.2 | -137.6 | 24.4 | -0.52 / -0.63 / -0.59 | 218.6 / 194.2 |
| SI 1 sun (120, 0.1, 120, -1) | negative pre-2023 | 251 | -66.4 | -120.8 | -101.6 | 54.4 | -0.53 / -0.95 / -0.80 | 354.7 / 300.3 |
| SI 2 sun (120, 0.0, 120, -1) | negative pre-2023 | 545 | -34.3 | -86.9 | -68.5 | 52.6 | -0.38 / -0.97 / -0.76 | 126.0 / 73.0 |
| SI 3 sun (60, 0.1, 360, -1) | positive pre-2023 | 213 | 69.4 | 15.0 | 33.6 | 54.4 | 0.29 / 0.06 / 0.14 | 196.9 / 142.6 |
| SI 4 sun (120, 0.0, 720, 1) | gross-positive, cost-negative pre-2023 | 545 | 10.7 | -41.9 | -23.5 | 52.6 | 0.06 / -0.24 / -0.13 | 160.6 / 107.7 |
| SI 5 sun (60, 0.1, 120, -1) | positive pre-2023 | 213 | 131.7 | 77.3 | 95.9 | 54.4 | 0.87 / 0.51 / 0.64 | 102.6 / 48.2 |
| SI 6 sun (120, 0.1, 360, -1) | negative pre-2023 | 251 | -47.7 | -102.1 | -82.9 | 54.4 | -0.30 / -0.63 / -0.51 | 111.6 / 57.3 |
| SI 7 (diag) sun (60, 0.1, 720, -1) | positive pre-2023 | 213 | 124.2 | 69.8 | 88.4 | 54.4 | 0.35 / 0.19 / 0.25 | 218.9 / 164.5 |
| SI 8 (diag) sun (120, 0.1, 720, -1) | negative pre-2023 | 251 | -39.1 | -93.5 | -74.3 | 54.4 | -0.14 / -0.33 / -0.26 | 215.1 / 160.8 |
| SI 9 (diag) sun (60, 0.0, 720, -1) | gross-positive, cost-negative pre-2023 | 542 | 15.1 | -36.8 | -18.7 | 52.0 | 0.09 / -0.21 / -0.11 | 74.0 / 20.6 |
| HG 1 sun (60, 0.1, 720, -1) | gross-positive, cost-negative pre-2023 | 205 | 9.0 | -20.4 | -13.0 | 29.4 | 0.04 / -0.12 / -0.08 | 372.0 / 342.7 |
| HG 2 sun (60, 0.0, 720, -1) | gross-positive, cost-negative pre-2023 | 541 | 26.1 | -2.4 | 5.2 | 28.5 | 0.25 / -0.03 / 0.05 | 101.0 / 72.1 |
| HG 3 sun (60, 0.1, 360, -1) | gross-positive, cost-negative pre-2023 | 205 | 22.1 | -7.2 | 0.2 | 29.4 | 0.15 / -0.07 / -0.01 | 125.3 / 95.9 |
| HG 4 (diag) sun (120, 0.0, 720, -1) | gross-positive, cost-negative pre-2023 | 549 | 23.7 | -4.7 | 2.9 | 28.4 | 0.23 / -0.04 / 0.03 | 172.4 / 143.7 |
| HG 5 (diag) sun (60, 0.0, 360, -1) | gross-positive, cost-negative pre-2023 | 541 | 20.3 | -8.2 | -0.6 | 28.5 | 0.27 / -0.12 / -0.02 | 91.7 / 62.8 |
| HG 6 (diag) sun (120, 0.1, 120, -1) | negative pre-2023 | 239 | -4.7 | -34.0 | -26.5 | 29.4 | -0.05 / -0.37 / -0.29 | 70.6 / 41.2 |
| PL 1 sun (120, 0.1, 120, -1) | positive pre-2023 | 275 | 16.2 | 1.9 | 0.5 | 14.4 | 0.38 / 0.04 / 0.01 | 38.4 / 24.0 |
| PL 2 sun (60, 0.0, 360, -1) | positive pre-2023 | 493 | 29.2 | 15.0 | 13.9 | 14.2 | 0.59 / 0.29 / 0.27 | 26.3 / 12.1 |
| PL 3 sun (120, 0.0, 120, -1) | positive pre-2023 | 542 | 19.4 | 5.2 | 3.9 | 14.3 | 0.58 / 0.14 / 0.11 | 21.0 / 6.7 |
| PL 4 sun (60, 0.0, 120, -1) | gross-positive, cost-negative pre-2023 | 493 | 4.8 | -9.4 | -10.5 | 14.2 | 0.13 / -0.28 / -0.31 | 12.1 / -2.2 |
| PL 5 (diag) sun (120, 0.1, 360, -1) | positive pre-2023 | 275 | 23.6 | 9.2 | 7.9 | 14.4 | 0.40 / 0.16 / 0.13 | 42.7 / 28.4 |
| PL 6 (diag) sun (60, 0.0, 720, -1) | negative pre-2023 | 493 | -2.9 | -17.1 | -18.2 | 14.2 | -0.04 / -0.21 / -0.22 | 70.7 / 56.4 |
| PL 7 (diag) sun (60, 0.1, 120, -1) | positive pre-2023 | 207 | 21.4 | 7.0 | 5.9 | 14.4 | 0.33 / 0.11 / 0.09 | 27.9 / 13.6 |
| ZN 1 (diag) sun (60, 0.1, 360, -1) | negative pre-2023 | 198 | -2.8 | -38.5 | -43.7 | 35.6 | -0.10 / -1.34 / -1.51 | 27.9 / -7.7 |
| ZN 2 (diag) sun (60, 0.1, 120, -1) | gross-positive, cost-negative pre-2023 | 198 | 1.3 | -34.3 | -39.6 | 35.6 | 0.07 / -1.60 / -1.82 | 26.3 / -9.3 |
| ZN 3 (diag) sun (120, 0.0, 720, 1) | negative pre-2023 | 547 | -11.3 | -44.3 | -49.0 | 33.0 | -0.38 / -1.50 / -1.66 | 20.6 / -13.2 |
| ZB 1 sun (60, 0.1, 360, -1) | gross-positive, cost-negative pre-2023 | 193 | 13.3 | -53.6 | -72.9 | 66.9 | 0.19 / -0.74 / -1.00 | 66.4 / -0.5 |
| ZB 2 (diag) sun (120, 0.1, 720, 1) | negative pre-2023 | 235 | -16.9 | -83.7 | -103.1 | 66.9 | -0.15 / -0.73 / -0.89 | 38.0 / -28.8 |
| ZB 3 (diag) sun (60, 0.1, 720, 1) | negative pre-2023 | 193 | -31.6 | -98.4 | -117.8 | 66.9 | -0.25 / -0.79 / -0.94 | 13.7 / -53.2 |
| ZB 4 (diag) sun (60, 0.1, 120, -1) | gross-positive, cost-negative pre-2023 | 193 | 2.6 | -64.3 | -83.6 | 66.9 | 0.05 / -1.25 / -1.59 | 31.2 / -35.6 |
| ZF 1 (diag) sun (60, 0.1, 360, -1) | gross-positive, cost-negative pre-2023 | 227 | 1.3 | -18.7 | -20.9 | 20.0 | 0.08 / -1.21 / -1.34 | 23.0 / 3.0 |
| ZF 2 (diag) sun (60, 0.1, 120, -1) | gross-positive, cost-negative pre-2023 | 227 | 0.3 | -19.7 | -21.9 | 20.0 | 0.03 / -1.56 / -1.72 | 21.3 / 1.3 |
| ZF 3 (diag) sun (120, 0.1, 720, 1) | negative pre-2023 | 270 | -6.1 | -26.1 | -28.2 | 20.0 | -0.20 / -0.83 / -0.90 | 12.2 / -7.8 |
| 6E 1 sun (120, 0.0, 720, -1) | negative pre-2023 | 549 | -6.5 | -23.0 | -24.1 | 16.5 | -0.11 / -0.40 / -0.42 | 21.6 / 4.8 |
| 6E 2 (diag) sun (60, 0.1, 720, 1) | negative pre-2023 | 115 | -35.3 | -52.1 | -53.3 | 16.9 | -0.25 / -0.37 / -0.38 | 46.9 / 30.0 |
| 6E 3 (diag) sun (60, 0.1, 360, 1) | negative pre-2023 | 115 | -35.6 | -52.5 | -53.6 | 16.9 | -0.42 / -0.62 / -0.64 | 46.0 / 29.1 |
| 6E 4 (diag) sun (120, 0.0, 360, 1) | negative pre-2023 | 549 | -4.8 | -21.3 | -22.5 | 16.5 | -0.16 / -0.75 / -0.79 | 23.9 / 7.2 |
| 6J 1 sun (60, 0.0, 120, -1) | positive pre-2023 | 530 | 19.9 | 3.4 | -1.9 | 16.5 | 0.74 / 0.13 / -0.07 | 41.2 / 24.7 |
| 6J 2 sun (120, 0.1, 360, -1) | negative pre-2023 | 283 | -8.4 | -25.3 | -30.7 | 16.9 | -0.21 / -0.53 / -0.63 | 75.2 / 58.4 |
| 6J 3 sun (120, 0.0, 360, -1) | negative pre-2023 | 549 | -7.1 | -23.6 | -29.0 | 16.5 | -0.25 / -0.74 / -0.90 | 31.3 / 14.5 |
| 6J 4 (diag) sun (120, 0.1, 720, -1) | negative pre-2023 | 283 | -22.4 | -39.3 | -44.7 | 16.9 | -0.35 / -0.58 / -0.66 | 33.8 / 17.0 |
| 6J 5 (diag) sun (60, 0.0, 360, -1) | gross-positive, cost-negative pre-2023 | 530 | 15.4 | -1.1 | -6.5 | 16.5 | 0.40 / -0.06 / -0.21 | 26.5 / 10.1 |
| 6J 6 (diag) sun (60, 0.1, 720, -1) | gross-positive, cost-negative pre-2023 | 206 | 17.6 | 0.8 | -4.8 | 16.9 | 0.17 / -0.04 / -0.11 | 2.6 / -14.3 |
| 6B 1 (diag) sun (60, 0.1, 120, 1) | negative pre-2023 | 138 | -21.7 | -38.6 | -39.7 | 16.9 | -0.30 / -0.52 / -0.54 | 31.8 / 15.0 |
| 6B 2 (diag) sun (60, 0.1, 720, 1) | negative pre-2023 | 138 | -42.3 | -59.2 | -60.3 | 16.9 | -0.48 / -0.67 / -0.68 | 33.3 / 16.5 |
| 6B 3 (diag) sun (120, 0.0, 720, -1) | gross-positive, cost-negative pre-2023 | 549 | 4.6 | -11.7 | -13.1 | 16.3 | 0.12 / -0.28 / -0.32 | 15.0 / -1.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6B: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00); 6E: 1 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.76, p(top) = 0.68); 6J: 3 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.38, p(top) = 0.28); GC: 3 cells pass the clean rule against a replicate mean of 3.9 (p(count) = 0.80, p(top) = 0.91); HG: 3 cells pass the clean rule against a replicate mean of 3.3 (p(count) = 0.68, p(top) = 0.57); PL: 4 cells pass the clean rule against a replicate mean of 4.0 (p(count) = 0.56, p(top) = 0.98); SI: 6 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.12, p(top) = 0.84); ZB: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.53, p(top) = 0.53); ZF: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00).
- Of 21 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (HG sun (60, 0.1, 720, -1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 8, 'negative pre-2023': 7, 'gross-positive, cost-negative pre-2023': 6}.

- Note: Selection minimum trades 40 (weekly event).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q24.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q24/ (`Q24_CO_all_selected_scored.csv`).

DONE Q24
