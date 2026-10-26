# REPORT Q33 - Q33: intraday time-series momentum on 10 markets: open-to-window-end return traded with/against to the afternoon

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 24 selected cells (+28 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.12; best pair-window standalone Sharpe +1.04.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: intraday time-series momentum on 10 markets: open-to-window-end return traded with/against to the afternoon.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      24 |         24 |         0 |               0.647 |                1 |          0 |            3 |
| CL    |      24 |         24 |         1 |               0.285 |                2 |          1 |            3 |
| ES    |      24 |         24 |         7 |               1.151 |                2 |          7 |            3 |
| GC    |      24 |         24 |         2 |               0.949 |                2 |          2 |            3 |
| HG    |      24 |         24 |         1 |               0.661 |                2 |          1 |            3 |
| HO    |      24 |         24 |         0 |               0.618 |                1 |          0 |            3 |
| NQ    |      24 |         24 |         9 |               1.321 |                2 |          9 |            1 |
| RTY   |      24 |         24 |         2 |               0.655 |                2 |          2 |            3 |
| SI    |      24 |         24 |         2 |               0.534 |                2 |          2 |            3 |
| ZN    |      24 |         24 |         0 |              -1.088 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    7 |            2.71  |               7 |      0.005 |                       0.665 |            0.671 |           1.133 |    0.495 |       1.151 |                1.443 |
| NQ    |     200 |                    9 |            4.89  |              11 |      0.04  |                       0.879 |            0.773 |           1.139 |    0.285 |       1.321 |                1.924 |
| RTY   |     200 |                    2 |            3.305 |              10 |      0.85  |                       0.362 |            0.669 |           1.088 |    0.875 |       0.442 |                1.785 |
| GC    |     200 |                    2 |            3.085 |               8 |      0.85  |                       0.821 |            0.698 |           1.145 |    0.27  |       0.949 |                1.773 |
| CL    |     200 |                    1 |            2.115 |               7 |      0.88  |                       0.22  |            0.632 |           1.191 |    0.825 |       0.22  |                1.6   |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| HO    |     200 |                    0 |            4.085 |              10 |      1     |                     nan     |            0.736 |           1.113 |  nan     |     nan     |                1.768 |
| 6E    |     200 |                    0 |            0.9   |               4 |      1     |                     nan     |            0.588 |           1.112 |  nan     |     nan     |                1.156 |
| SI    |     200 |                    2 |            1.29  |               5 |      0.36  |                       0.28  |            0.553 |           1.141 |    0.6   |       0.534 |                1.313 |
| HG    |     200 |                    1 |            1.74  |               5 |      0.85  |                       0.57  |            0.635 |           1.063 |    0.465 |       0.57  |                1.437 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | imom (60, 0.0, 180, 1) | 497 | 2 | 1.15 | -0.72 | 0.34 | -0.51 / 1.10 | 0.19 / -0.15 / -0.41 | -0.07 | 0.32 | 0.87 | -0.23 | 0.00 | 800 | NO |
| ES 2 | imom (60, 0.15, 180, 1) | 259 | 2 | 0.99 | -0.49 | 0.57 | -0.04 / 1.33 | 0.11 / -0.06 / -0.18 | -0.02 | -0.14 | 0.92 | -0.15 | 0.00 | 431 | NO |
| ES 3 | imom (60, 0.0, 120, 1) | 516 | 2 | 0.67 | -0.92 | -0.01 | -0.77 / 1.38 | 0.08 / -0.26 / -0.34 | -0.16 | 0.48 | 0.76 | -0.31 | 0.00 | 829 | NO |
| ES 4 | imom (60, 0.15, 120, 1) | 264 | 2 | 0.67 | -0.60 | 0.04 | -0.67 / 1.29 | 0.03 / -0.21 / -0.38 | -0.15 | 0.23 | 0.79 | -0.31 | 0.00 | 437 | NO |
| ES 5 | imom (120, 0.15, 120, 1) | 321 | 2 | 0.61 | -0.60 | 0.41 | -0.06 / 1.19 | 0.04 / 0.27 / -0.33 | -0.06 | 0.46 | 0.91 | -0.15 | 0.00 | 525 | NO |
| ES 6 | imom (120, 0.15, 180, 1) | 321 | 2 | 0.41 | -0.35 | 0.18 | -0.38 / 1.39 | -0.01 / 0.26 / -0.38 | -0.09 | 0.52 | 0.84 | -0.21 | 0.00 | 525 | NO |
| ES 7 | imom (120, 0.0, 180, 1) | 497 | 2 | 0.16 | -0.60 | 0.22 | 0.38 / 0.95 | -0.05 / 0.20 / -0.16 | -0.09 | 0.42 | 0.82 | -0.20 | 0.00 | 800 | NO |
| ES 8 (diag) | imom (120, 0.0, 120, 1) | 497 | 1 | 0.32 | -0.79 | 0.44 | 0.80 / 1.19 | -0.01 / 0.15 / -0.06 | -0.05 | 0.36 | 0.92 | -0.13 | 0.00 | 800 | diag |
| ES 9 (diag) | imom (180, 0.15, 180, 1) | 349 | 1 | -0.06 | -0.16 | 0.04 | 0.18 / 1.39 | -0.05 / -0.11 / 0.05 | -0.08 | 0.03 | 0.65 | -0.17 | 0.00 | 558 | diag |
| ES 10 (diag) | imom (180, 0.15, 120, 1) | 349 | 0 | -0.17 | -0.57 | -0.02 | 0.25 / 0.94 | -0.09 / 0.12 / -0.07 | -0.11 | 0.26 | 0.73 | -0.20 | 0.00 | 558 | diag |
| NQ 1 | imom (60, 0.0, 180, 1) | 497 | 2 | 1.32 | -0.00 | 0.71 | 0.11 / 1.38 | 0.23 / -0.09 / -0.24 | 0.07 | 0.09 | 0.90 | -0.15 | 0.50 | 800 | NO |
| NQ 2 | imom (60, 0.15, 180, 1) | 299 | 2 | 1.23 | -0.07 | 1.04 | 0.79 / 1.34 | 0.17 / 0.19 / -0.07 | 0.11 | 0.04 | 0.98 | -0.08 | 0.50 | 490 | NO |
| NQ 3 | imom (60, 0.0, 120, 1) | 516 | 2 | 1.17 | 0.08 | 0.34 | -0.53 / 1.59 | 0.19 / -0.09 / -0.44 | -0.01 | 0.36 | 0.81 | -0.22 | 1.00 | 829 | NO |
| NQ 4 | imom (60, 0.15, 120, 1) | 305 | 2 | 1.06 | -0.05 | 0.81 | 0.48 / 1.27 | 0.13 / 0.22 / -0.13 | 0.07 | 0.24 | 0.97 | -0.12 | 1.00 | 496 | NO |
| NQ 5 | imom (120, 0.15, 120, 1) | 334 | 2 | 0.76 | -0.19 | 0.82 | 0.92 / 1.02 | 0.05 / 0.23 / -0.12 | 0.02 | 0.32 | 0.99 | -0.11 | 0.50 | 553 | NO |
| NQ 6 | imom (120, 0.15, 180, 1) | 334 | 2 | 0.70 | 0.01 | 0.75 | 0.81 / 1.13 | 0.03 / 0.31 / -0.19 | 0.00 | 0.37 | 0.95 | -0.14 | 1.00 | 553 | NO |
| NQ 7 | imom (120, 0.0, 120, 1) | 497 | 2 | 0.64 | -0.41 | 0.63 | 0.59 / 1.21 | 0.02 / 0.04 / -0.11 | -0.02 | 0.41 | 0.95 | -0.15 | 0.00 | 800 | NO |
| NQ 8 | imom (180, 0.15, 180, 1) | 353 | 2 | 0.63 | 0.54 | 0.79 | 1.07 / 1.60 | 0.06 / -0.03 / 0.22 | 0.07 | -0.34 | 0.92 | -0.06 | 0.50 | 570 | NO |
| NQ 9 | imom (180, 0.15, 120, 1) | 353 | 2 | 0.40 | -0.07 | 0.67 | 1.17 / 1.19 | 0.00 / 0.19 / 0.04 | 0.02 | 0.02 | 0.95 | -0.11 | 0.50 | 570 | NO |
| NQ 10 (diag) | imom (120, 0.0, 180, 1) | 497 | 1 | 0.40 | 0.00 | 0.53 | 0.77 / 1.32 | -0.02 / 0.14 / -0.07 | -0.03 | 0.41 | 0.90 | -0.17 | 0.00 | 800 | diag |
| RTY 1 | imom (180, 0.0, 120, -1) | 497 | 2 | 0.44 | -0.55 | 0.34 | 0.09 / 1.06 | 0.09 / -0.32 / 0.11 | -0.02 | -0.52 | 0.88 | -0.14 | 0.50 | 800 | NO |
| RTY 2 | imom (60, 0.0, 120, 1) | 516 | 2 | 0.28 | -0.08 | 0.11 | -0.18 / 0.82 | 0.07 / 0.28 / -0.40 | -0.06 | 0.08 | 0.85 | -0.22 | 0.00 | 829 | NO |
| RTY 3 (diag) | imom (180, 0.15, 120, -1) | 366 | 1 | 0.65 | -0.54 | 0.17 | -0.53 / 1.35 | 0.09 / -0.59 / 0.02 | -0.08 | -0.64 | 0.84 | -0.24 | 0.00 | 589 | diag |
| RTY 4 (diag) | imom (180, 0.15, 180, -1) | 366 | 1 | 0.48 | -1.13 | 0.19 | -0.39 / 0.89 | 0.09 / -0.46 / -0.05 | -0.07 | -0.40 | 0.85 | -0.23 | 0.00 | 589 | diag |
| RTY 5 (diag) | imom (180, 0.0, 180, -1) | 497 | 1 | 0.33 | -0.99 | 0.30 | 0.03 / 0.82 | 0.10 / -0.08 / -0.08 | -0.01 | -0.46 | 0.86 | -0.13 | 0.50 | 800 | diag |
| GC 1 | imom (60, 0.15, 180, 1) | 217 | 2 | 0.95 | -0.21 | 0.44 | 0.11 / 1.28 | 0.10 / 1.47 / -0.87 | -0.01 | 0.10 | 0.88 | -0.25 | 1.00 | 322 | NO |
| GC 2 | imom (60, 0.15, 120, 1) | 217 | 2 | 0.69 | -0.17 | 0.57 | 0.49 / 1.16 | 0.05 / 1.03 / -0.56 | -0.01 | 0.09 | 0.92 | -0.23 | 0.50 | 322 | NO |
| GC 3 (diag) | imom (60, 0.0, 180, 1) | 516 | 1 | 0.91 | -0.70 | -0.13 | -0.88 / 1.49 | 0.10 / -0.21 / -0.84 | -0.22 | -0.03 | 0.58 | -0.49 | 0.00 | 824 | diag |
| GC 4 (diag) | imom (60, 0.0, 120, 1) | 516 | 1 | 0.81 | -0.61 | -0.07 | -0.69 / 1.56 | 0.09 / -0.83 / -0.47 | -0.21 | -0.05 | 0.52 | -0.49 | 0.00 | 824 | diag |
| GC 5 (diag) | imom (180, 0.15, 180, -1) | 342 | 1 | 0.09 | -0.48 | 0.21 | 0.32 / 1.46 | -0.01 / -0.69 / 0.19 | -0.11 | -0.39 | 0.65 | -0.35 | 0.00 | 533 | diag |
| CL 1 | imom (180, 0.0, 120, 1) | 514 | 2 | 0.22 | -0.34 | 0.42 | 0.57 / 0.91 | 0.07 / -0.18 / 0.19 | -0.05 | 0.17 | 0.98 | -0.17 | 0.50 | 824 | NO |
| CL 2 (diag) | imom (60, 0.0, 120, -1) | 517 | 1 | 0.28 | -1.12 | 0.46 | 0.68 / 0.81 | 0.07 / -0.05 / 0.36 | 0.02 | -0.11 | 0.98 | -0.10 | 0.50 | 830 | diag |
| CL 3 (diag) | imom (60, 0.0, 180, -1) | 516 | 1 | 0.18 | -0.71 | -0.11 | -0.43 / 0.86 | 0.03 / -0.10 / -0.11 | -0.11 | -0.45 | 0.72 | -0.26 | 0.00 | 827 | diag |
| CL 4 (diag) | imom (60, 0.15, 180, -1) | 256 | 1 | 0.16 | -0.55 | -0.05 | -0.27 / 1.35 | 0.04 / -0.05 / -0.20 | -0.08 | -0.12 | 0.70 | -0.29 | 0.00 | 393 | diag |
| ZN 1 (diag) | imom (60, 0.15, 180, 1) | 261 | 0 | -1.09 | -2.31 | -1.76 | -3.17 / -0.90 | -0.29 / -0.62 / -0.41 | -0.66 | -0.23 | 0.71 | -0.54 | 0.00 | 415 | diag |
| ZN 2 (diag) | imom (60, 0.15, 120, 1) | 261 | 0 | -1.57 | -2.30 | -2.23 | -3.44 / -1.70 | -0.39 / -0.67 / -0.47 | -0.79 | -0.41 | 0.77 | -0.63 | 0.00 | 415 | diag |
| ZN 3 (diag) | imom (120, 0.15, 180, 1) | 332 | 0 | -1.75 | -2.51 | -2.53 | -4.59 / -1.44 | -0.33 / -0.81 / -0.66 | -0.84 | 0.46 | 0.44 | -0.64 | 0.00 | 534 | diag |
| HO 1 (diag) | imom (60, 0.15, 120, 1) | 204 | 1 | 0.62 | -0.15 | 0.08 | -0.41 / 1.32 | 0.12 / -0.39 / -0.24 | -0.03 | 0.09 | 0.63 | -0.26 | 0.00 | 318 | diag |
| HO 2 (diag) | imom (60, 0.15, 180, 1) | 204 | 1 | 0.59 | 0.16 | -0.00 | -0.59 / 1.71 | 0.10 / -0.60 / -0.02 | -0.03 | 0.35 | 0.65 | -0.25 | 0.00 | 318 | diag |
| HO 3 (diag) | imom (60, 0.0, 180, 1) | 513 | 1 | 0.58 | 0.22 | -0.01 | -0.45 / 1.66 | 0.10 / -0.35 / -0.31 | -0.07 | 0.34 | 0.61 | -0.30 | 0.00 | 823 | diag |
| 6E 1 (diag) | imom (60, 0.0, 180, -1) | 516 | 1 | 0.65 | -0.71 | 0.13 | -1.11 / 0.35 | 0.09 / -0.40 / 0.01 | -0.13 | 0.42 | 0.97 | -0.17 | 0.00 | 827 | diag |
| 6E 2 (diag) | imom (60, 0.15, 180, -1) | 210 | 1 | 0.35 | -0.51 | -0.12 | -1.18 / 0.51 | 0.03 / -0.28 / -0.16 | -0.14 | 0.09 | 0.92 | -0.22 | 0.00 | 329 | diag |
| 6E 3 (diag) | imom (60, 0.0, 120, -1) | 516 | 1 | 0.03 | -0.86 | -0.23 | -1.01 / -0.02 | 0.00 / -0.26 / 0.02 | -0.20 | 0.23 | 0.98 | -0.20 | 0.00 | 827 | diag |
| SI 1 | imom (120, 0.0, 180, 1) | 507 | 2 | 0.53 | -0.82 | 0.59 | 0.86 / 1.14 | 0.02 / 0.65 / -1.19 | -0.13 | 0.00 | 0.97 | -0.49 | 0.00 | 813 | NO |
| SI 2 | imom (120, 0.0, 120, 1) | 508 | 2 | 0.02 | -1.22 | 0.40 | 0.67 / 1.21 | -0.07 / 0.88 / -0.84 | -0.17 | -0.05 | 0.91 | -0.49 | 0.00 | 816 | NO |
| SI 3 (diag) | imom (60, 0.15, 120, 1) | 213 | 1 | 0.50 | -0.63 | -0.44 | -0.93 / 1.28 | 0.00 / -2.47 / -0.34 | -0.54 | 0.29 | 0.32 | -0.96 | 0.00 | 311 | diag |
| SI 4 (diag) | imom (120, 0.15, 180, 1) | 317 | 1 | 0.09 | -0.25 | 0.53 | 0.85 / 1.47 | -0.05 / 0.22 / -0.94 | -0.17 | 0.11 | 0.87 | -0.39 | 0.00 | 479 | diag |
| SI 5 (diag) | imom (60, 0.15, 180, 1) | 213 | 1 | -0.06 | -0.68 | 0.01 | 0.09 / 1.47 | -0.10 / -0.90 / -0.17 | -0.27 | 0.12 | 0.60 | -0.52 | 0.00 | 311 | diag |
| HG 1 | imom (60, 0.0, 120, -1) | 517 | 2 | 0.57 | -1.67 | 0.40 | 0.45 / 0.92 | 0.04 / 0.17 / -0.10 | -0.07 | -0.34 | 0.98 | -0.17 | 0.50 | 827 | NO |
| HG 2 (diag) | imom (60, 0.15, 180, -1) | 193 | 1 | 0.66 | -0.43 | 0.72 | 0.85 / 1.05 | 0.10 / 0.17 / -0.04 | 0.05 | -0.44 | 0.93 | -0.11 | 1.00 | 295 | diag |
| HG 3 (diag) | imom (60, 0.15, 120, -1) | 193 | 1 | 0.61 | -0.59 | 0.75 | 0.94 / 0.97 | 0.09 / 0.29 / -0.03 | 0.05 | -0.53 | 0.97 | -0.11 | 1.00 | 295 | diag |
| HG 4 (diag) | imom (120, 0.15, 180, -1) | 289 | 1 | 0.20 | -0.38 | -0.11 | -0.53 / 0.91 | 0.03 / -0.34 / -0.02 | -0.09 | -0.38 | 0.72 | -0.21 | 0.00 | 450 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 24 |
| diagnostic cells read | 28 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 13 |
| worst-decile corr <= +0.30 | 37 |
| plateau >= 0.75 | 6 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E imom (60, 0.0, 180, -1) (diag) | clean | 0.64 | 1.02 | -106547 | -97235 | 627031 | -122906 | 0.92 | 44.8 | 1.55 | -89066 | 277172 | -106455 |
| 6E imom (60, 0.0, 180, -1) (diag) | H1 | -2.21 | -2.50 | -92992 | -88412 | 519653 | -105728 | -0.75 | 64.3 | 2.43 | -69553 | 161791 | -79530 |
| 6E imom (60, 0.0, 180, -1) (diag) | H2 | -0.14 | -0.18 | -103358 | -76850 | 218024 | -137122 | -0.12 | 50.0 | 2.50 | -82263 | 215245 | -83767 |
| 6E imom (60, 0.0, 180, -1) (diag) | all | 0.13 | 0.19 | -108907 | -94957 | 627031 | -137122 | 0.26 | 48.8 | 1.90 | -86528 | 277172 | -106455 |
| CL imom (180, 0.0, 120, 1) | clean | 0.28 | 0.46 | -111309 | -92388 | 825837 | -158725 | 0.31 | 55.2 | 1.53 | -88628 | 270228 | -93409 |
| CL imom (180, 0.0, 120, 1) | H1 | -1.32 | -1.64 | -87211 | -74295 | 291971 | -95272 | -0.68 | 60.7 | 2.65 | -86106 | 153700 | -97342 |
| CL imom (180, 0.0, 120, 1) | H2 | 1.06 | 1.89 | -247922 | -216456 | 469243 | -249743 | 1.64 | 47.2 | 2.67 | -101162 | 241817 | -109425 |
| CL imom (180, 0.0, 120, 1) | all | 0.42 | 0.71 | -162192 | -124813 | 825837 | -249743 | 1.01 | 54.8 | 1.97 | -92382 | 270228 | -109425 |
| ES imom (60, 0.15, 180, 1) | clean | 0.99 | 2.26 | -81754 | -68262 | 366126 | -152821 | 2.44 | 41.9 | 1.57 | -88019 | 297053 | -92002 |
| ES imom (60, 0.15, 180, 1) | H1 | 0.06 | 0.07 | -241653 | -178251 | 384562 | -384562 | 0.05 | 35.7 | 2.77 | -79629 | 180911 | -96681 |
| ES imom (60, 0.15, 180, 1) | H2 | -0.16 | -0.26 | -80515 | -75898 | 311885 | -82450 | -0.14 | 55.6 | 2.30 | -88454 | 222441 | -89282 |
| ES imom (60, 0.15, 180, 1) | all | 0.57 | 0.91 | -121426 | -92818 | 566859 | -384562 | 1.53 | 44.0 | 1.91 | -89082 | 297053 | -96681 |
| GC imom (60, 0.15, 120, 1) | clean | 0.73 | 1.09 | -133736 | -103465 | 527654 | -223147 | 1.26 | 43.8 | 1.51 | -86655 | 313372 | -94764 |
| GC imom (60, 0.15, 120, 1) | H1 | 2.18 | 4.96 | -154890 | -137062 | 505091 | -190561 | 1.98 | 28.6 | 3.86 | -69805 | 191730 | -73897 |
| GC imom (60, 0.15, 120, 1) | H2 | -0.69 | -1.04 | -242503 | -208543 | 1011319 | -263299 | -0.45 | 47.2 | 1.93 | -101039 | 287865 | -112533 |
| GC imom (60, 0.15, 120, 1) | all | 0.57 | 0.93 | -196929 | -152727 | 1011319 | -263299 | 1.20 | 41.7 | 1.92 | -89686 | 313372 | -112533 |
| HG imom (60, 0.0, 120, -1) | clean | 0.36 | 0.54 | -122642 | -108176 | 322080 | -147910 | 1.06 | 44.8 | 1.50 | -87440 | 294737 | -97231 |
| HG imom (60, 0.0, 120, -1) | H1 | 1.50 | 3.86 | -93981 | -86886 | 315092 | -114239 | 1.96 | 50.0 | 3.00 | -89790 | 146398 | -90446 |
| HG imom (60, 0.0, 120, -1) | H2 | -0.80 | -0.98 | -170911 | -138043 | 489432 | -233225 | -0.55 | 50.0 | 2.38 | -78682 | 219663 | -79890 |
| HG imom (60, 0.0, 120, -1) | all | 0.40 | 0.65 | -130708 | -112729 | 543129 | -233225 | 1.26 | 47.0 | 1.94 | -87219 | 294737 | -97231 |
| HO imom (60, 0.15, 180, 1) (diag) | clean | 0.55 | 0.84 | -138001 | -104353 | 718340 | -227031 | 0.69 | 38.1 | 1.56 | -85699 | 301908 | -91025 |
| HO imom (60, 0.15, 180, 1) (diag) | H1 | -2.40 | -2.71 | -126840 | -120290 | 493753 | -133167 | -1.00 | 64.3 | 2.23 | -83764 | 171104 | -85483 |
| HO imom (60, 0.15, 180, 1) (diag) | H2 | -0.02 | -0.02 | -305252 | -248098 | 642797 | -306919 | -0.01 | 38.9 | 2.47 | -85082 | 204969 | -93017 |
| HO imom (60, 0.15, 180, 1) (diag) | all | -0.00 | -0.01 | -196806 | -146475 | 1304674 | -306919 | -0.01 | 42.3 | 1.88 | -86082 | 301908 | -93017 |
| NQ imom (60, 0.15, 180, 1) | clean | 1.30 | 2.32 | -112365 | -91903 | 493478 | -136185 | 2.40 | 37.1 | 1.63 | -91563 | 295624 | -109111 |
| NQ imom (60, 0.15, 180, 1) | H1 | 1.03 | 1.42 | -194403 | -149836 | 279029 | -279029 | 1.17 | 32.1 | 3.02 | -80540 | 157393 | -98888 |
| NQ imom (60, 0.15, 180, 1) | H2 | 0.63 | 1.05 | -167420 | -153802 | 407263 | -168899 | 0.79 | 47.2 | 2.42 | -97686 | 219272 | -104790 |
| NQ imom (60, 0.15, 180, 1) | all | 1.04 | 1.69 | -155014 | -121670 | 493478 | -279029 | 3.71 | 38.7 | 2.02 | -93738 | 295624 | -109111 |
| RTY imom (180, 0.0, 120, -1) | clean | 0.48 | 0.65 | -139858 | -103849 | 663620 | -365111 | 0.65 | 47.6 | 1.55 | -82440 | 266783 | -88469 |
| RTY imom (180, 0.0, 120, -1) | H1 | -1.44 | -1.85 | -130492 | -106524 | 495906 | -163060 | -0.68 | 64.3 | 2.51 | -73628 | 168646 | -88830 |
| RTY imom (180, 0.0, 120, -1) | H2 | 1.51 | 2.33 | -101883 | -85160 | 171355 | -114783 | 2.23 | 41.7 | 2.59 | -83764 | 223599 | -84586 |
| RTY imom (180, 0.0, 120, -1) | all | 0.34 | 0.47 | -135246 | -102721 | 663620 | -365111 | 0.72 | 48.8 | 1.94 | -83529 | 266783 | -88830 |
| SI imom (120, 0.0, 180, 1) | clean | 0.50 | 0.73 | -129125 | -101834 | 377848 | -261848 | 1.21 | 46.7 | 1.48 | -96625 | 276437 | -129628 |
| SI imom (120, 0.0, 180, 1) | H1 | 2.15 | 21.21 | -168421 | -148437 | 522351 | -199598 | 9.14 | 42.9 | 3.48 | -85258 | 182752 | -88726 |
| SI imom (120, 0.0, 180, 1) | H2 | -1.15 | -1.34 | -688796 | -484572 | 1710901 | -1081094 | -0.86 | 61.1 | 1.29 | -149766 | 290129 | -191177 |
| SI imom (120, 0.0, 180, 1) | all | 0.59 | 1.46 | -348231 | -256850 | 1710901 | -1081094 | 2.20 | 48.8 | 1.87 | -108474 | 290129 | -191177 |
| ZN imom (60, 0.15, 180, 1) (diag) | clean | -1.18 | -1.44 | -142532 | -125385 | 1539229 | -231107 | -0.70 | 53.3 | 1.17 | -91007 | 319886 | -96181 |
| ZN imom (60, 0.15, 180, 1) (diag) | H1 | -4.43 | -4.10 | -94900 | -89623 | 702089 | -99286 | -0.85 | 75.0 | 2.21 | -81803 | 174693 | -83700 |
| ZN imom (60, 0.15, 180, 1) (diag) | H2 | -2.54 | -2.58 | -155461 | -116969 | 651389 | -180282 | -0.98 | 47.2 | 2.08 | -80953 | 226732 | -82288 |
| ZN imom (60, 0.15, 180, 1) (diag) | all | -1.76 | -2.04 | -141920 | -120920 | 2549679 | -231107 | -0.91 | 56.0 | 1.52 | -88540 | 319886 | -96181 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES imom (60, 0.15, 180, 1) | -20.5 | -1.2 | 9.7 | 20.9 | 6.8 / 12.0 | -6.6 / 1.8 | NO |
| NQ imom (60, 0.15, 180, 1) | -10.0 | -19.0 | -1.3 | 20.7 | -19.9 / 4.5 | -10.9 / 17.2 | NO |
| RTY imom (180, 0.0, 120, -1) | -24.8 | 13.9 | 16.6 | 31.3 | 13.2 / 17.1 | 9.8 / 11.3 | NO |
| GC imom (60, 0.15, 120, 1) | -16.7 | -29.5 | 1.6 | 3.0 | 6.4 / 10.1 | 16.9 / 26.3 | NO |
| CL imom (180, 0.0, 120, 1) | -20.9 | -40.5 | 0.8 | 20.0 | 6.9 / 8.0 | -6.5 / 13.6 | NO |
| ZN imom (60, 0.15, 180, 1) (diag) | -55.3 | -0.2 | 9.6 | 2.0 | -1.0 / 5.2 | 19.6 / 21.9 | NO |
| HO imom (60, 0.15, 180, 1) (diag) | -30.1 | -19.2 | 6.7 | 18.3 | -20.2 / 7.3 | 14.8 / 18.1 | NO |
| 6E imom (60, 0.0, 180, -1) (diag) | -28.2 | -14.1 | 14.9 | 21.1 | -15.0 / 8.8 | 27.6 / 30.5 | NO |
| SI imom (120, 0.0, 180, 1) | 11.1 | -271.8 | -45.6 | -50.6 | -62.0 / -4.4 | -13.9 / -2.9 | NO |
| HG imom (60, 0.0, 120, -1) | -22.5 | -1.9 | 11.4 | 22.2 | -2.7 / 10.8 | 5.3 / 6.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 imom (60, 0.0, 180, 1) | negative pre-2023 | 2613 | -2.8 | -31.8 | -17.8 | 29.0 | -0.06 / -0.72 / -0.40 | 109.9 / 80.8 |
| ES 2 imom (60, 0.15, 180, 1) | negative pre-2023 | 1417 | -2.7 | -32.0 | -17.9 | 29.4 | -0.04 / -0.49 / -0.27 | 182.1 / 152.8 |
| ES 3 imom (60, 0.0, 120, 1) | negative pre-2023 | 2693 | -5.7 | -34.7 | -20.7 | 29.0 | -0.15 / -0.92 / -0.55 | 68.1 / 39.1 |
| ES 4 imom (60, 0.15, 120, 1) | negative pre-2023 | 1426 | -4.5 | -33.8 | -19.7 | 29.4 | -0.08 / -0.60 / -0.35 | 96.0 / 66.6 |
| ES 5 imom (120, 0.15, 120, 1) | negative pre-2023 | 1615 | -0.1 | -29.5 | -15.2 | 29.4 | -0.00 / -0.60 / -0.31 | 115.7 / 86.4 |
| ES 6 imom (120, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1615 | 9.2 | -20.1 | -5.8 | 29.4 | 0.16 / -0.35 / -0.10 | 100.0 / 70.6 |
| ES 7 imom (120, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2613 | 2.2 | -26.9 | -12.8 | 29.1 | 0.05 / -0.60 / -0.29 | 49.8 / 20.6 |
| ES 8 (diag) imom (120, 0.0, 120, 1) | negative pre-2023 | 2613 | -1.0 | -30.1 | -16.0 | 29.1 | -0.03 / -0.79 / -0.42 | 61.3 / 32.1 |
| ES 9 (diag) imom (180, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1678 | 20.0 | -9.3 | 5.0 | 29.4 | 0.35 / -0.16 / 0.09 | 28.7 / -0.7 |
| ES 10 (diag) imom (180, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1678 | 4.0 | -25.3 | -11.0 | 29.4 | 0.09 / -0.57 / -0.25 | 15.7 / -13.7 |
| NQ 1 imom (60, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2613 | 14.0 | -0.3 | 8.2 | 14.3 | 0.22 / -0.00 / 0.13 | 204.3 / 189.9 |
| NQ 2 imom (60, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1522 | 8.5 | -5.9 | 2.7 | 14.4 | 0.10 / -0.07 / 0.03 | 274.2 / 259.8 |
| NQ 3 imom (60, 0.0, 120, 1) | positive pre-2023 | 2691 | 18.8 | 4.5 | 13.0 | 14.3 | 0.33 / 0.08 / 0.23 | 154.3 / 139.9 |
| NQ 4 imom (60, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1536 | 10.9 | -3.5 | 5.0 | 14.4 | 0.14 / -0.05 / 0.07 | 203.2 / 188.8 |
| NQ 5 imom (120, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1721 | 1.4 | -13.0 | -4.4 | 14.4 | 0.02 / -0.19 / -0.07 | 184.6 / 170.3 |
| NQ 6 imom (120, 0.15, 180, 1) | positive pre-2023 | 1721 | 15.2 | 0.8 | 9.4 | 14.4 | 0.19 / 0.01 / 0.12 | 209.0 / 194.6 |
| NQ 7 imom (120, 0.0, 120, 1) | negative pre-2023 | 2613 | -8.6 | -23.0 | -14.4 | 14.3 | -0.16 / -0.41 / -0.26 | 119.3 / 105.0 |
| NQ 8 imom (180, 0.15, 180, 1) | positive pre-2023 | 1808 | 59.8 | 45.4 | 53.9 | 14.4 | 0.71 / 0.54 / 0.64 | 163.5 / 149.1 |
| NQ 9 imom (180, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1808 | 9.9 | -4.5 | 4.0 | 14.4 | 0.15 / -0.07 / 0.06 | 96.6 / 82.3 |
| NQ 10 (diag) imom (120, 0.0, 180, 1) | positive pre-2023 | 2613 | 14.5 | 0.2 | 8.7 | 14.3 | 0.21 / 0.00 / 0.12 | 99.7 / 85.4 |
| RTY 1 imom (180, 0.0, 120, -1) | negative pre-2023 | 1490 | -1.4 | -15.8 | -13.5 | 14.4 | -0.05 / -0.55 / -0.47 | 31.4 / 17.1 |
| RTY 2 imom (60, 0.0, 120, 1) | gross-positive, cost-negative pre-2023 | 1541 | 11.6 | -2.8 | -0.5 | 14.3 | 0.33 / -0.08 / -0.01 | 25.9 / 11.6 |
| RTY 3 (diag) imom (180, 0.15, 120, -1) | negative pre-2023 | 1086 | -4.8 | -19.2 | -16.9 | 14.4 | -0.13 / -0.54 / -0.47 | 37.4 / 23.0 |
| RTY 4 (diag) imom (180, 0.15, 180, -1) | negative pre-2023 | 1086 | -34.5 | -48.9 | -46.7 | 14.4 | -0.80 / -1.13 / -1.08 | 41.1 / 26.8 |
| RTY 5 (diag) imom (180, 0.0, 180, -1) | negative pre-2023 | 1490 | -22.3 | -36.6 | -34.4 | 14.4 | -0.60 / -0.99 / -0.93 | 34.8 / 20.5 |
| GC 1 imom (60, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1174 | 9.6 | -14.8 | -5.1 | 24.4 | 0.12 / -0.21 / -0.08 | 148.5 / 124.1 |
| GC 2 imom (60, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1174 | 13.6 | -10.7 | -1.0 | 24.4 | 0.20 / -0.17 / -0.02 | 109.6 / 85.3 |
| GC 3 (diag) imom (60, 0.0, 180, 1) | negative pre-2023 | 2666 | -8.3 | -32.4 | -22.7 | 24.1 | -0.18 / -0.70 / -0.49 | 94.7 / 70.4 |
| GC 4 (diag) imom (60, 0.0, 120, 1) | negative pre-2023 | 2666 | -1.6 | -25.7 | -16.0 | 24.1 | -0.04 / -0.61 / -0.38 | 84.2 / 60.0 |
| GC 5 (diag) imom (180, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 1685 | 4.7 | -19.6 | -9.9 | 24.4 | 0.12 / -0.48 / -0.24 | 29.4 / 5.1 |
| CL 1 imom (180, 0.0, 120, 1) | gross-positive, cost-negative pre-2023 | 2623 | 13.2 | -11.1 | -8.5 | 24.3 | 0.41 / -0.34 / -0.26 | 33.9 / 9.6 |
| CL 2 (diag) imom (60, 0.0, 120, -1) | negative pre-2023 | 2687 | -25.1 | -49.3 | -46.7 | 24.2 | -0.57 / -1.12 / -1.06 | 36.6 / 12.4 |
| CL 3 (diag) imom (60, 0.0, 180, -1) | negative pre-2023 | 2643 | -11.2 | -35.3 | -32.8 | 24.2 | -0.23 / -0.71 / -0.66 | 32.7 / 8.5 |
| CL 4 (diag) imom (60, 0.15, 180, -1) | negative pre-2023 | 1240 | -17.3 | -41.6 | -39.5 | 24.4 | -0.23 / -0.55 / -0.52 | 34.5 / 10.2 |
| ZN 1 (diag) imom (60, 0.15, 180, 1) | negative pre-2023 | 1293 | -9.4 | -45.0 | -50.1 | 35.6 | -0.49 / -2.31 / -2.56 | 11.5 / -24.1 |
| ZN 2 (diag) imom (60, 0.15, 120, 1) | negative pre-2023 | 1293 | -4.0 | -39.6 | -44.7 | 35.6 | -0.24 / -2.30 / -2.58 | 5.7 / -29.9 |
| ZN 3 (diag) imom (120, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1617 | 0.2 | -35.4 | -40.5 | 35.6 | 0.02 / -2.51 / -2.86 | 8.2 / -27.4 |
| HO 1 (diag) imom (60, 0.15, 120, 1) | negative pre-2023 | 1015 | -2.4 | -15.1 | -13.6 | 12.8 | -0.03 / -0.15 / -0.14 | 85.0 / 72.2 |
| HO 2 (diag) imom (60, 0.15, 180, 1) | positive pre-2023 | 1015 | 34.0 | 21.2 | 22.8 | 12.8 | 0.26 / 0.16 / 0.17 | 89.5 / 76.8 |
| HO 3 (diag) imom (60, 0.0, 180, 1) | positive pre-2023 | 2645 | 29.8 | 17.0 | 18.6 | 12.7 | 0.39 / 0.22 / 0.24 | 52.5 / 39.8 |
| 6E 1 (diag) imom (60, 0.0, 180, -1) | gross-positive, cost-negative pre-2023 | 2690 | 1.9 | -14.8 | -15.9 | 16.7 | 0.09 / -0.71 / -0.77 | 28.5 / 11.9 |
| 6E 2 (diag) imom (60, 0.15, 180, -1) | negative pre-2023 | 1062 | -2.4 | -19.3 | -20.5 | 16.9 | -0.06 / -0.51 / -0.54 | 27.9 / 11.1 |
| 6E 3 (diag) imom (60, 0.0, 120, -1) | gross-positive, cost-negative pre-2023 | 2690 | 1.5 | -15.2 | -16.3 | 16.7 | 0.09 / -0.86 / -0.92 | 17.9 / 1.2 |
| SI 1 imom (120, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2587 | 10.3 | -43.3 | -24.6 | 53.5 | 0.19 / -0.82 / -0.47 | 92.6 / 38.3 |
| SI 2 imom (120, 0.0, 120, 1) | negative pre-2023 | 2625 | -1.1 | -54.6 | -36.0 | 53.5 | -0.03 / -1.22 / -0.81 | 54.1 / -0.2 |
| SI 3 (diag) imom (60, 0.15, 120, 1) | gross-positive, cost-negative pre-2023 | 1212 | 5.7 | -48.7 | -29.5 | 54.4 | 0.06 / -0.63 / -0.39 | 106.7 / 52.3 |
| SI 4 (diag) imom (120, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1538 | 37.1 | -17.2 | 1.8 | 54.4 | 0.53 / -0.25 / 0.02 | 63.4 / 9.0 |
| SI 5 (diag) imom (60, 0.15, 180, 1) | negative pre-2023 | 1212 | -2.2 | -56.6 | -37.4 | 54.4 | -0.04 / -0.68 / -0.45 | 38.4 / -16.0 |
| HG 1 imom (60, 0.0, 120, -1) | negative pre-2023 | 2673 | -18.9 | -47.8 | -40.1 | 28.9 | -0.66 / -1.67 / -1.39 | 45.0 / 16.0 |
| HG 2 (diag) imom (60, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 993 | 3.5 | -25.9 | -18.2 | 29.4 | 0.06 / -0.43 / -0.30 | 76.7 / 47.3 |
| HG 3 (diag) imom (60, 0.15, 120, -1) | negative pre-2023 | 993 | -0.5 | -29.8 | -22.1 | 29.4 | -0.01 / -0.59 / -0.44 | 68.8 / 39.4 |
| HG 4 (diag) imom (120, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 1448 | 14.0 | -15.4 | -7.7 | 29.4 | 0.34 / -0.38 / -0.19 | 38.1 / 8.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); CL: 1 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.88, p(top) = 0.82); ES: 7 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.01, p(top) = 0.49); GC: 2 cells pass the clean rule against a replicate mean of 3.1 (p(count) = 0.85, p(top) = 0.27); HG: 1 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.85, p(top) = 0.47); HO: 0 cells pass the clean rule against a replicate mean of 4.1 (p(count) = 1.00); NQ: 9 cells pass the clean rule against a replicate mean of 4.9 (p(count) = 0.04, p(top) = 0.28); RTY: 2 cells pass the clean rule against a replicate mean of 3.3 (p(count) = 0.85, p(top) = 0.88); SI: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.36, p(top) = 0.60); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 24 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.12 (NQ imom (60, 0.15, 180, 1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 12, 'negative pre-2023': 9, 'positive pre-2023': 3}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q33.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q33/ (`Q33_CO_all_selected_scored.csv`).

DONE Q33
