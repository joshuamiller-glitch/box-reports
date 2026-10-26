# REPORT Q23 - Q23: settlement-window drift: with/against the day direction from 30/15 minutes before the instrument settlement

**Verdict: FOUND-CANDIDATE (needs full verification). FOUND 1, LEAD 1, INSURANCE 0.** 17 selected cells (+42 diagnostic) scored on 14 instruments; best non-diagnostic all-in additive uplift at 20% share +0.22; best pair-window standalone Sharpe +1.12.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: settlement-window drift: with/against the day direction from 30/15 minutes before the instrument settlement. Time exit, no stop.
- Instruments: ES, NQ, RTY, YM, GC, SI, HG, CL, HO, RB, NG, ZN, ZB, 6E. Grid: 24 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      24 |         24 |         0 |              -0.167 |                1 |          0 |            3 |
| CL    |      24 |         24 |         0 |              -0.167 |                1 |          0 |            3 |
| ES    |      24 |         24 |         0 |               0.455 |                1 |          0 |            3 |
| GC    |      24 |         24 |         0 |              -0.217 |                1 |          0 |            3 |
| HG    |      24 |         16 |         0 |               0.505 |                1 |          0 |            3 |
| HO    |      24 |         24 |         4 |               0.903 |                2 |          4 |            3 |
| NG    |      24 |         24 |         3 |               1.242 |                2 |          3 |            3 |
| NQ    |      24 |         24 |         7 |               0.979 |                2 |          7 |            3 |
| RB    |      24 |         24 |         1 |               0.634 |                2 |          1 |            3 |
| RTY   |      24 |         24 |         2 |               0.485 |                2 |          2 |            3 |
| SI    |      24 |         24 |         0 |              -0.366 |                1 |          0 |            3 |
| YM    |      24 |         24 |         0 |               0.656 |                1 |          0 |            3 |
| ZB    |      24 |         24 |         0 |              -3.776 |                0 |          0 |            3 |
| ZN    |      24 |         24 |         0 |              -3.371 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            0.77  |               5 |      1     |                     nan     |            0.545 |           1.006 |  nan     |     nan     |                1.136 |
| NQ    |     200 |                    7 |            3.655 |               8 |      0.05  |                       0.618 |            0.706 |           1.141 |    0.61  |       0.979 |                1.807 |
| RTY   |     200 |                    2 |            1.345 |               4 |      0.39  |                       0.367 |            0.578 |           1.042 |    0.62  |       0.485 |                1.385 |
| YM    |     200 |                    0 |            1.615 |               5 |      1     |                     nan     |            0.634 |           1.103 |  nan     |     nan     |                1.494 |
| GC    |     200 |                    0 |            0.895 |               6 |      1     |                     nan     |            0.588 |           1.157 |  nan     |     nan     |                1.332 |
| SI    |     200 |                    0 |            0.155 |               2 |      1     |                     nan     |            0.574 |           1.206 |  nan     |     nan     |                1.308 |
| HG    |     200 |                    0 |            0.22  |               3 |      1     |                     nan     |            0.478 |           0.977 |  nan     |     nan     |                1.232 |
| CL    |     200 |                    0 |            0.5   |               3 |      1     |                     nan     |            0.555 |           1.028 |  nan     |     nan     |                1.245 |
| HO    |     200 |                    4 |            2.51  |               8 |      0.235 |                       0.632 |            0.667 |           1.121 |    0.505 |       0.903 |                1.612 |
| RB    |     200 |                    1 |            2.005 |               6 |      0.905 |                       0.257 |            0.627 |           1.192 |    0.825 |       0.257 |                1.534 |
| NG    |     200 |                    3 |            0.175 |               2 |      0     |                       0.796 |            0.498 |           1.013 |    0.035 |       1.242 |                1.013 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZB    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| 6E    |     200 |                    0 |            0.045 |               1 |      1     |                     nan     |            0.283 |           0.741 |  nan     |     nan     |                0.741 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | settle (30, 0.0, 0, -1) | 497 | 1 | 0.45 | -1.52 | 0.77 | 1.35 / 0.03 | 0.11 / 0.56 / 0.06 | 0.04 | -0.31 | 1.00 | -0.00 | 1.00 | 800 | diag |
| ES 2 (diag) | settle (30, 0.0, 15, -1) | 497 | 1 | 0.27 | -1.18 | 0.57 | 1.04 / 0.56 | 0.11 / 0.62 / -0.07 | 0.03 | -0.41 | 1.00 | -0.02 | 1.00 | 800 | diag |
| ES 3 (diag) | settle (30, 0.25, 0, -1) | 306 | 1 | 0.18 | -1.43 | 0.75 | 1.79 / 0.79 | 0.06 / 0.56 / 0.12 | 0.06 | -0.35 | 1.00 | -0.02 | 1.00 | 495 | diag |
| NQ 1 | settle (30, 0.5, 0, -1) | 164 | 2 | 0.98 | -0.56 | 1.04 | 1.17 / 1.43 | 0.21 / 0.50 / 0.09 | 0.21 | -0.01 | 0.98 | 0.04 | 1.00 | 267 | NO |
| NQ 2 | settle (15, 0.5, 0, -1) | 166 | 2 | 0.78 | -1.01 | 0.86 | 1.09 / 1.32 | 0.11 / -0.05 / 0.39 | 0.12 | -0.09 | 0.97 | -0.04 | 1.00 | 265 | NO |
| NQ 3 | settle (30, 0.25, 0, -1) | 304 | 2 | 0.74 | -0.84 | 0.96 | 1.21 / 1.23 | 0.17 / 0.65 / 0.06 | 0.18 | -0.04 | 0.97 | 0.01 | 1.00 | 495 | NO |
| NQ 4 | settle (30, 0.0, 0, -1) | 497 | 2 | 0.53 | -0.94 | 0.88 | 1.39 / 1.26 | 0.13 / 0.71 / 0.04 | 0.16 | -0.13 | 0.98 | 0.01 | 1.00 | 800 | NO |
| NQ 5 | settle (15, 0.0, 0, -1) | 497 | 2 | 0.50 | -1.42 | 1.12 | 2.10 / 1.10 | 0.09 / 0.32 / 0.52 | 0.18 | -0.37 | 1.00 | 0.04 | 1.00 | 800 | FOUND-CAND |
| NQ 6 | settle (15, 0.25, 0, -1) | 310 | 2 | 0.44 | -1.36 | 1.08 | 2.18 / 1.30 | 0.07 / 0.42 / 0.41 | 0.16 | -0.16 | 1.00 | 0.01 | 1.00 | 498 | NO |
| NQ 7 | settle (15, 0.5, 15, -1) | 166 | 2 | 0.35 | -0.49 | 0.41 | 0.63 / 1.26 | 0.05 / 0.02 / 0.16 | 0.06 | -0.34 | 0.87 | -0.10 | 1.00 | 265 | NO |
| NQ 8 (diag) | settle (30, 0.5, 15, -1) | 164 | 1 | 0.47 | -0.17 | 0.56 | 0.81 / 1.44 | 0.12 / 0.41 / -0.02 | 0.12 | -0.08 | 0.85 | -0.03 | 1.00 | 267 | diag |
| NQ 9 (diag) | settle (30, 0.25, 15, -1) | 304 | 1 | 0.33 | -0.61 | 0.64 | 0.88 / 1.46 | 0.12 / 0.61 / -0.07 | 0.13 | -0.13 | 0.94 | -0.04 | 1.00 | 495 | diag |
| NQ 10 (diag) | settle (30, 0.0, 15, -1) | 497 | 1 | -0.04 | -0.78 | 0.52 | 1.18 / 1.55 | 0.05 / 0.73 / 0.02 | 0.11 | -0.17 | 0.82 | -0.05 | 0.50 | 800 | diag |
| RTY 1 | settle (30, 0.0, 15, -1) | 497 | 2 | 0.49 | -0.93 | 0.68 | 0.93 / 1.05 | 0.10 / 0.39 / -0.05 | 0.00 | -0.53 | 0.99 | -0.07 | 1.00 | 800 | NO |
| RTY 2 | settle (15, 0.0, 15, -1) | 497 | 2 | 0.25 | -1.30 | 0.65 | 1.09 / 0.81 | 0.07 / 0.02 / 0.05 | -0.06 | -0.16 | 1.00 | -0.11 | 0.50 | 800 | NO |
| RTY 3 (diag) | settle (30, 0.5, 0, -1) | 154 | 1 | 0.29 | -0.96 | 0.68 | 1.34 / 0.96 | 0.08 / 0.00 / 0.23 | 0.05 | -0.46 | 0.98 | -0.06 | 1.00 | 246 | diag |
| RTY 4 (diag) | settle (30, 0.25, 0, -1) | 300 | 1 | 0.23 | -0.74 | 0.54 | 0.90 / 0.93 | 0.04 / 0.12 / 0.14 | -0.01 | -0.40 | 0.99 | -0.11 | 1.00 | 486 | diag |
| RTY 5 (diag) | settle (30, 0.0, 0, -1) | 497 | 1 | 0.20 | -1.19 | 0.56 | 1.02 / 0.45 | 0.02 / 0.25 / 0.15 | -0.04 | -0.53 | 1.00 | -0.11 | 1.00 | 800 | diag |
| YM 1 (diag) | settle (15, 0.5, 0, -1) | 175 | 1 | 0.66 | -1.20 | 1.12 | 2.37 / 0.68 | 0.10 / 0.26 / 0.29 | 0.12 | -0.35 | 1.00 | 0.00 | 1.00 | 262 | diag |
| YM 2 (diag) | settle (15, 0.25, 0, -1) | 295 | 1 | 0.35 | -1.74 | 0.81 | 1.91 / 0.80 | 0.04 / 0.35 / 0.19 | 0.04 | 0.34 | 1.00 | -0.06 | 1.00 | 473 | diag |
| YM 3 (diag) | settle (15, 0.5, 15, -1) | 175 | 1 | 0.22 | -0.81 | 0.24 | 0.12 / 1.20 | 0.04 / -0.08 / 0.05 | -0.01 | -0.44 | 0.85 | -0.14 | 0.50 | 262 | diag |
| GC 1 (diag) | settle (30, 0.25, 0, 1) | 259 | 1 | -0.22 | -1.22 | 0.40 | 0.84 / 1.28 | -0.10 / 0.59 / -0.12 | -0.07 | 0.10 | 0.91 | -0.21 | 1.00 | 383 | diag |
| GC 2 (diag) | settle (15, 0.5, 0, 1) | 110 | 1 | -0.24 | -0.62 | 0.44 | 0.91 / 1.04 | -0.03 / 0.37 / 0.01 | 0.01 | 0.17 | 0.94 | -0.15 | 1.00 | 149 | diag |
| GC 3 (diag) | settle (30, 0.5, 15, -1) | 108 | 1 | -0.27 | -0.70 | 0.02 | 0.18 / 1.56 | -0.09 / -1.21 / 0.23 | -0.21 | -0.06 | 0.67 | -0.57 | 0.00 | 147 | diag |
| SI 1 (diag) | settle (30, 0.5, 15, 1) | 104 | 1 | -0.37 | -1.82 | -0.89 | -1.38 / 1.13 | -0.12 / -0.93 / -2.34 | -0.87 | 0.06 | 0.13 | -1.29 | 0.00 | 156 | diag |
| SI 2 (diag) | settle (30, 0.5, 0, 1) | 105 | 1 | -0.41 | -1.69 | -0.10 | -0.07 / 1.04 | -0.14 / -0.74 / -1.81 | -0.67 | -0.01 | 0.66 | -1.07 | 0.00 | 157 | diag |
| SI 3 (diag) | settle (30, 0.25, 15, -1) | 268 | 1 | -1.08 | -1.55 | 0.17 | 0.72 / 1.14 | -0.23 / -1.16 / 0.22 | -0.45 | 0.16 | 0.88 | -0.62 | 0.00 | 405 | diag |
| HG 1 (diag) | settle (30, 0.5, 15, -1) | 72 | 1 | 0.51 | -0.77 | 0.06 | -0.84 / 1.15 | 0.11 / -0.34 / -0.02 | -0.03 | -0.20 | 0.82 | -0.16 | 0.50 | 120 | diag |
| HG 2 (diag) | settle (30, 0.5, 0, -1) | 73 | 1 | 0.19 | -0.88 | -0.52 | -1.20 / 0.98 | 0.04 / -1.08 / -0.15 | -0.25 | -0.01 | 0.61 | -0.49 | 0.00 | 121 | diag |
| HG 3 (diag) | settle (15, 0.25, 0, 1) | 235 | 1 | 0.12 | -3.92 | 0.07 | 0.08 / 0.42 | -0.03 / -0.17 / -0.21 | -0.33 | -0.22 | 0.99 | -0.27 | 0.00 | 360 | diag |
| CL 1 (diag) | settle (30, 0.25, 15, -1) | 296 | 1 | -0.17 | -1.23 | 0.55 | 1.19 / 0.64 | -0.03 / 0.22 / 0.71 | 0.01 | -0.20 | 1.00 | -0.10 | 1.00 | 442 | diag |
| CL 2 (diag) | settle (15, 0.5, 15, -1) | 142 | 1 | -0.17 | -0.89 | 0.23 | 0.57 / 0.80 | -0.07 / 0.13 / 0.17 | -0.11 | 0.27 | 0.96 | -0.28 | 0.50 | 197 | diag |
| CL 3 (diag) | settle (15, 0.25, 15, -1) | 284 | 0 | -0.34 | -1.44 | 0.07 | 0.48 / 1.09 | -0.08 / -0.17 / 0.40 | -0.18 | -0.26 | 0.92 | -0.23 | 0.50 | 425 | diag |
| HO 1 | settle (15, 0.5, 0, 1) | 137 | 2 | 0.90 | 0.13 | -0.95 | -2.38 / 1.19 | 0.18 / -0.18 / -1.88 | -0.42 | -0.05 | 0.11 | -0.75 | 0.00 | 208 | NO |
| HO 2 | settle (30, 0.5, 0, 1) | 134 | 2 | 0.75 | -0.05 | -0.60 | -1.56 / 1.38 | 0.14 / 0.07 / -1.57 | -0.33 | -0.24 | 0.24 | -0.69 | 0.00 | 201 | NO |
| HO 3 | settle (15, 0.5, 15, 1) | 137 | 2 | 0.58 | -0.29 | -0.29 | -0.83 / 1.53 | 0.11 / -0.01 / -1.18 | -0.28 | -0.13 | 0.43 | -0.63 | 0.00 | 208 | NO |
| HO 4 | settle (30, 0.5, 15, 1) | 134 | 2 | 0.30 | -0.30 | -0.31 | -0.69 / 1.26 | 0.05 / 0.08 / -1.22 | -0.31 | -0.26 | 0.46 | -0.70 | 0.00 | 201 | NO |
| HO 5 (diag) | settle (30, 0.0, 15, -1) | 499 | 1 | 0.03 | -0.35 | 0.58 | 1.02 / 1.28 | -0.00 / -0.27 / 0.99 | 0.11 | -0.05 | 0.93 | -0.13 | 1.00 | 800 | diag |
| HO 6 (diag) | settle (30, 0.0, 0, -1) | 500 | 1 | -0.02 | -0.56 | 0.76 | 1.45 / 0.97 | 0.00 / -0.11 / 1.11 | 0.15 | -0.23 | 0.97 | -0.05 | 1.00 | 801 | diag |
| HO 7 (diag) | settle (30, 0.25, 15, -1) | 298 | 0 | -0.34 | 0.07 | 0.67 | 1.41 / 1.41 | -0.06 / -0.01 / 0.95 | 0.14 | -0.00 | 0.95 | -0.10 | 1.00 | 454 | diag |
| RB 1 | settle (15, 0.25, 15, -1) | 297 | 2 | 0.26 | -0.09 | 0.05 | -0.08 / 1.13 | -0.00 / -0.49 / 0.08 | -0.12 | 0.43 | 0.74 | -0.29 | 0.00 | 459 | NO |
| RB 2 (diag) | settle (30, 0.0, 15, -1) | 499 | 1 | 0.63 | 0.14 | 0.72 | 0.96 / 1.22 | 0.06 / -0.23 / 0.45 | 0.04 | -0.07 | 0.98 | -0.12 | 0.50 | 802 | diag |
| RB 3 (diag) | settle (15, 0.5, 0, 1) | 153 | 1 | 0.60 | 0.06 | -0.30 | -1.31 / 1.09 | 0.14 / 0.04 / -0.89 | -0.16 | -0.10 | 0.54 | -0.38 | 0.00 | 226 | diag |
| RB 4 (diag) | settle (15, 0.0, 15, -1) | 499 | 1 | 0.44 | -0.32 | 0.62 | 0.84 / 0.90 | 0.02 / -0.41 / 0.54 | -0.01 | 0.04 | 0.98 | -0.17 | 0.50 | 802 | diag |
| NG 1 | settle (30, 0.5, 15, -1) | 138 | 2 | 1.24 | -0.87 | 1.10 | 0.81 / 0.48 | 0.22 / 0.35 / 0.08 | 0.09 | 0.10 | 1.00 | 0.02 | 1.00 | 206 | LEAD(gate3-7 fail: 2xslip) |
| NG 2 | settle (30, 0.5, 0, -1) | 138 | 2 | 0.97 | -1.52 | 0.82 | 0.55 / 0.58 | 0.17 / 0.03 / 0.16 | 0.04 | 0.23 | 1.00 | -0.02 | 1.00 | 207 | NO |
| NG 3 | settle (30, 0.25, 15, -1) | 281 | 2 | 0.18 | -1.34 | 0.69 | 1.51 / 0.21 | 0.00 / 1.12 / 0.03 | -0.08 | 0.27 | 1.00 | -0.06 | 1.00 | 445 | NO |
| NG 4 (diag) | settle (15, 0.5, 15, -1) | 143 | 1 | 0.16 | -0.81 | -0.04 | -0.39 / 0.38 | -0.02 / -0.24 / -0.00 | -0.19 | 0.30 | 0.95 | -0.23 | 0.00 | 212 | diag |
| NG 5 (diag) | settle (30, 0.25, 0, -1) | 281 | 1 | 0.14 | -1.88 | 0.45 | 1.16 / -0.10 | -0.01 / 0.54 / 0.01 | -0.13 | 0.63 | 1.00 | -0.11 | 1.00 | 446 | diag |
| NG 6 (diag) | settle (15, 0.5, 0, -1) | 143 | 0 | -0.17 | -1.53 | -0.38 | -0.88 / -0.12 | -0.07 / -0.37 / 0.04 | -0.23 | 0.53 | 0.99 | -0.26 | 0.00 | 213 | diag |
| ZN 1 (diag) | settle (30, 0.5, 15, -1) | 152 | 0 | -3.37 | -3.18 | -3.31 | -3.79 / -2.04 | -0.68 / -0.23 / -0.47 | -1.08 | 0.03 | 0.59 | -0.76 | 0.00 | 229 | diag |
| ZN 2 (diag) | settle (30, 0.5, 0, 1) | 152 | 0 | -3.76 | -2.23 | -4.61 | -6.48 / -2.98 | -0.78 / -0.98 / -1.12 | -1.37 | 0.31 | 0.17 | -1.10 | 0.00 | 229 | diag |
| ZN 3 (diag) | settle (15, 0.5, 15, -1) | 155 | 0 | -3.95 | -3.69 | -3.93 | -4.12 / -3.21 | -0.82 / -0.49 / -0.57 | -1.23 | 0.07 | 0.59 | -0.93 | 0.00 | 232 | diag |
| ZB 1 (diag) | settle (30, 0.5, 15, -1) | 156 | 0 | -3.78 | -2.57 | -3.99 | -4.42 / -2.21 | -0.77 / -0.47 / -0.86 | -1.31 | 0.11 | 0.05 | -0.96 | 0.00 | 236 | diag |
| ZB 2 (diag) | settle (15, 0.5, 15, -1) | 159 | 0 | -4.03 | -3.13 | -4.10 | -4.19 / -3.19 | -0.84 / -0.49 / -0.80 | -1.35 | 0.08 | 0.29 | -1.01 | 0.00 | 242 | diag |
| ZB 3 (diag) | settle (15, 0.5, 0, 1) | 159 | 0 | -4.71 | -2.61 | -5.51 | -6.98 / -4.06 | -0.94 / -1.31 / -1.38 | -1.64 | 0.18 | 0.20 | -1.33 | 0.00 | 242 | diag |
| 6E 1 (diag) | settle (30, 0.5, 15, 1) | 110 | 1 | -0.17 | -0.60 | -0.25 | -0.59 / 0.31 | -0.06 / -0.07 / -0.10 | -0.18 | -0.06 | 0.90 | -0.22 | 0.00 | 162 | diag |
| 6E 2 (diag) | settle (15, 0.5, 15, -1) | 113 | 0 | -0.35 | -0.93 | -0.85 | -2.02 / -0.26 | -0.12 / -0.78 / 0.01 | -0.38 | -0.07 | 0.78 | -0.37 | 0.00 | 171 | diag |
| 6E 3 (diag) | settle (15, 0.5, 0, -1) | 113 | 0 | -0.78 | -0.71 | -0.85 | -0.94 / -0.58 | -0.20 / -0.88 / -0.09 | -0.63 | -0.19 | 0.93 | -0.47 | 0.00 | 171 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 17 |
| diagnostic cells read | 42 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 36 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 29 |
| worst-decile corr <= +0.30 | 53 |
| plateau >= 0.75 | 28 |
| all-in uplift at 2x slippage >= +0.10 | 13 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 2 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E settle (30, 0.5, 15, 1) (diag) | clean | -0.14 | -0.22 | -129162 | -105893 | 494499 | -162986 | -0.25 | 32.4 | 1.40 | -87586 | 311595 | -100805 |
| 6E settle (30, 0.5, 15, 1) (diag) | H1 | -0.18 | -0.20 | -100360 | -73361 | 171293 | -171293 | -0.15 | 28.6 | 2.76 | -75118 | 157699 | -78287 |
| 6E settle (30, 0.5, 15, 1) (diag) | H2 | -0.94 | -1.09 | -120104 | -81054 | 323456 | -126773 | -0.52 | 33.3 | 2.39 | -82158 | 217624 | -82524 |
| 6E settle (30, 0.5, 15, 1) (diag) | all | -0.25 | -0.38 | -131830 | -102609 | 494499 | -171293 | -0.64 | 32.1 | 1.82 | -85561 | 311595 | -100805 |
| CL settle (30, 0.25, 15, -1) (diag) | clean | -0.18 | -0.24 | -139875 | -111349 | 834955 | -219650 | -0.19 | 54.3 | 1.43 | -84800 | 285051 | -89321 |
| CL settle (30, 0.25, 15, -1) (diag) | H1 | 1.41 | 2.30 | -66900 | -56583 | 158868 | -94547 | 1.27 | 35.7 | 3.05 | -74756 | 143730 | -78287 |
| CL settle (30, 0.25, 15, -1) (diag) | H2 | 1.38 | 2.84 | -261847 | -214913 | 472502 | -286153 | 2.47 | 36.1 | 3.20 | -94974 | 239139 | -109738 |
| CL settle (30, 0.25, 15, -1) (diag) | all | 0.55 | 0.98 | -183806 | -140232 | 834955 | -286153 | 1.45 | 47.6 | 2.06 | -86496 | 285051 | -109738 |
| ES settle (30, 0.0, 0, -1) (diag) | clean | 0.49 | 0.72 | -139992 | -102330 | 642260 | -257997 | 0.69 | 46.7 | 1.57 | -82716 | 256518 | -91879 |
| ES settle (30, 0.0, 0, -1) (diag) | H1 | 2.72 | 6.83 | -48200 | -41669 | 135068 | -56300 | 3.19 | 35.7 | 3.39 | -69936 | 125666 | -74884 |
| ES settle (30, 0.0, 0, -1) (diag) | H2 | 0.62 | 1.00 | -93138 | -82034 | 290781 | -102805 | 0.61 | 47.2 | 2.55 | -87785 | 225382 | -88941 |
| ES settle (30, 0.0, 0, -1) (diag) | all | 0.77 | 1.20 | -123184 | -92446 | 642260 | -257997 | 1.63 | 44.6 | 2.06 | -82972 | 256518 | -91879 |
| GC settle (15, 0.5, 0, 1) (diag) | clean | -0.23 | -0.30 | -160574 | -118325 | 918619 | -325531 | -0.23 | 35.2 | 1.42 | -81080 | 292575 | -89759 |
| GC settle (15, 0.5, 0, 1) (diag) | H1 | 1.40 | 5.86 | -229874 | -174298 | 324870 | -276464 | 4.53 | 21.4 | 3.20 | -75322 | 151713 | -81677 |
| GC settle (15, 0.5, 0, 1) (diag) | H2 | 0.05 | 0.08 | -127506 | -93718 | 357435 | -155394 | 0.04 | 16.7 | 2.50 | -81089 | 206457 | -82524 |
| GC settle (15, 0.5, 0, 1) (diag) | all | 0.44 | 1.10 | -177440 | -126542 | 918619 | -325531 | 1.39 | 29.2 | 1.99 | -81160 | 292575 | -89759 |
| HG settle (30, 0.5, 15, -1) (diag) | clean | 0.50 | 1.75 | -60915 | -48986 | 304624 | -83510 | 1.48 | 29.5 | 1.57 | -79390 | 275457 | -81874 |
| HG settle (30, 0.5, 15, -1) (diag) | H1 | -1.01 | -1.04 | -184749 | -131356 | 350385 | -340775 | -0.75 | 32.1 | 2.49 | -78831 | 199948 | -79375 |
| HG settle (30, 0.5, 15, -1) (diag) | H2 | -0.70 | -0.95 | -54551 | -52339 | 207464 | -55334 | -0.49 | 30.6 | 2.46 | -81089 | 213151 | -82524 |
| HG settle (30, 0.5, 15, -1) (diag) | all | 0.06 | 0.12 | -92510 | -67345 | 466474 | -340775 | 0.19 | 30.4 | 1.92 | -79855 | 275457 | -82524 |
| HO settle (15, 0.5, 15, 1) | clean | 0.59 | 1.04 | -113394 | -89819 | 446253 | -169921 | 1.18 | 39.0 | 1.57 | -90274 | 257669 | -106935 |
| HO settle (15, 0.5, 15, 1) | H1 | -0.60 | -0.83 | -76429 | -69911 | 234408 | -80095 | -0.39 | 35.7 | 2.82 | -77610 | 151713 | -78287 |
| HO settle (15, 0.5, 15, 1) | H2 | -1.04 | -1.33 | -678039 | -454991 | 2355810 | -971065 | -0.54 | 58.3 | 1.30 | -140668 | 274216 | -183836 |
| HO settle (15, 0.5, 15, 1) | all | -0.29 | -0.39 | -291182 | -199713 | 2355810 | -971065 | -0.36 | 42.9 | 1.65 | -100612 | 274216 | -183836 |
| NG settle (30, 0.5, 15, -1) | clean | 1.25 | 2.41 | -109604 | -85387 | 587711 | -145379 | 1.93 | 31.4 | 1.68 | -83695 | 247673 | -88181 |
| NG settle (30, 0.5, 15, -1) | H1 | 1.11 | 2.12 | -116453 | -101258 | 251111 | -150615 | 1.31 | 35.7 | 3.18 | -64654 | 148770 | -76932 |
| NG settle (30, 0.5, 15, -1) | H2 | 0.44 | 0.74 | -56157 | -54486 | 160940 | -56157 | 0.49 | 33.3 | 2.56 | -88089 | 207669 | -93197 |
| NG settle (30, 0.5, 15, -1) | all | 1.10 | 2.07 | -106916 | -83959 | 587711 | -150615 | 2.62 | 32.7 | 2.10 | -84613 | 247673 | -93197 |
| NQ settle (30, 0.5, 0, -1) | clean | 0.95 | 1.60 | -133476 | -97078 | 424358 | -205671 | 2.03 | 30.5 | 1.67 | -79703 | 240225 | -88633 |
| NQ settle (30, 0.5, 0, -1) | H1 | 1.42 | 2.68 | -114099 | -101667 | 286387 | -121228 | 1.30 | 28.6 | 3.33 | -70788 | 164168 | -74709 |
| NQ settle (30, 0.5, 0, -1) | H2 | 0.95 | 1.44 | -143001 | -97513 | 254278 | -211899 | 1.16 | 33.3 | 2.57 | -102279 | 220977 | -124904 |
| NQ settle (30, 0.5, 0, -1) | all | 1.04 | 1.73 | -138468 | -101860 | 424358 | -211899 | 3.60 | 31.0 | 2.12 | -84439 | 240225 | -124904 |
| RB settle (15, 0.25, 15, -1) | clean | 0.18 | 0.27 | -123390 | -107971 | 451904 | -177424 | 0.37 | 45.7 | 1.46 | -83796 | 298893 | -97895 |
| RB settle (15, 0.25, 15, -1) | H1 | -3.19 | -3.20 | -77702 | -76696 | 453494 | -78552 | -0.99 | 60.7 | 2.34 | -76233 | 173510 | -78287 |
| RB settle (15, 0.25, 15, -1) | H2 | 0.51 | 0.81 | -268357 | -236450 | 939611 | -300694 | 0.40 | 36.1 | 2.56 | -107827 | 214135 | -109274 |
| RB settle (15, 0.25, 15, -1) | all | 0.05 | 0.07 | -186778 | -146241 | 1069317 | -300694 | 0.09 | 45.8 | 1.85 | -90454 | 298893 | -109274 |
| RTY settle (30, 0.0, 15, -1) | clean | 0.52 | 0.81 | -126482 | -98782 | 442537 | -174980 | 1.06 | 49.5 | 1.56 | -90942 | 281649 | -106928 |
| RTY settle (30, 0.0, 15, -1) | H1 | 2.06 | 4.26 | -84047 | -76647 | 248734 | -103190 | 1.85 | 39.3 | 3.22 | -82138 | 150969 | -97570 |
| RTY settle (30, 0.0, 15, -1) | H2 | 0.20 | 0.32 | -140071 | -101596 | 398401 | -214219 | 0.18 | 58.3 | 2.43 | -83069 | 214148 | -84073 |
| RTY settle (30, 0.0, 15, -1) | all | 0.68 | 1.09 | -127310 | -97920 | 442537 | -214219 | 2.26 | 50.0 | 2.01 | -89929 | 281649 | -106928 |
| SI settle (30, 0.25, 15, -1) (diag) | clean | -1.06 | -1.28 | -162015 | -126533 | 1312716 | -299272 | -0.73 | 59.0 | 1.23 | -93391 | 289362 | -102058 |
| SI settle (30, 0.25, 15, -1) (diag) | H1 | -0.66 | -0.84 | -514789 | -482331 | 3661236 | -605353 | -0.16 | 50.0 | 1.66 | -115710 | 717492 | -132290 |
| SI settle (30, 0.25, 15, -1) (diag) | H2 | 1.71 | 3.23 | -445220 | -350303 | 834503 | -496587 | 2.63 | 38.9 | 2.70 | -142246 | 236969 | -158424 |
| SI settle (30, 0.25, 15, -1) (diag) | all | 0.17 | 0.26 | -382972 | -289569 | 3661236 | -605353 | 0.17 | 53.0 | 1.69 | -114124 | 722694 | -158424 |
| YM settle (15, 0.5, 0, -1) (diag) | clean | 0.71 | 1.15 | -124104 | -89490 | 449973 | -289996 | 1.44 | 33.3 | 1.56 | -79365 | 252692 | -82861 |
| YM settle (15, 0.5, 0, -1) (diag) | H1 | 2.54 | 4.44 | -62817 | -49235 | 112819 | -89003 | 2.88 | 21.4 | 3.08 | -78424 | 142827 | -78924 |
| YM settle (15, 0.5, 0, -1) (diag) | H2 | 2.25 | 4.11 | -77931 | -59509 | 121247 | -78488 | 3.59 | 22.2 | 2.77 | -76947 | 217411 | -77401 |
| YM settle (15, 0.5, 0, -1) (diag) | all | 1.12 | 1.83 | -109944 | -79728 | 449973 | -289996 | 3.13 | 29.2 | 2.05 | -78938 | 252692 | -82861 |
| ZB settle (30, 0.5, 15, -1) (diag) | clean | -3.80 | -3.56 | -202363 | -160604 | 3447111 | -258172 | -1.00 | 66.7 | 0.69 | -93861 | 386435 | -108402 |
| ZB settle (30, 0.5, 15, -1) (diag) | H1 | -3.75 | -3.79 | -59954 | -58128 | 497096 | -65431 | -0.88 | 60.7 | 2.35 | -84153 | 157160 | -90019 |
| ZB settle (30, 0.5, 15, -1) (diag) | H2 | -5.17 | -4.28 | -216278 | -168537 | 1556727 | -258172 | -0.98 | 66.7 | 1.62 | -81089 | 217425 | -82524 |
| ZB settle (30, 0.5, 15, -1) (diag) | all | -3.99 | -3.66 | -197906 | -154583 | 5442607 | -258172 | -0.99 | 65.5 | 1.14 | -90743 | 386435 | -108402 |
| ZN settle (30, 0.5, 15, -1) (diag) | clean | -3.38 | -3.26 | -189799 | -157143 | 3065348 | -241619 | -1.00 | 61.9 | 0.78 | -95717 | 418922 | -125332 |
| ZN settle (30, 0.5, 15, -1) (diag) | H1 | -2.53 | -2.88 | -58578 | -51074 | 311152 | -63646 | -0.84 | 50.0 | 2.60 | -77610 | 158360 | -78287 |
| ZN settle (30, 0.5, 15, -1) (diag) | H2 | -4.70 | -4.13 | -94643 | -84920 | 816545 | -102540 | -0.95 | 61.1 | 2.01 | -83294 | 228693 | -84063 |
| ZN settle (30, 0.5, 15, -1) (diag) | all | -3.31 | -3.21 | -166842 | -136374 | 4143541 | -241619 | -0.99 | 59.5 | 1.32 | -91193 | 418922 | -125332 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES settle (30, 0.0, 0, -1) (diag) | -18.5 | 7.8 | 19.6 | 32.3 | 7.1 / 18.5 | 35.1 / 44.8 | NO |
| NQ settle (30, 0.5, 0, -1) | -13.3 | -47.0 | 18.9 | 32.6 | 8.9 / 26.5 | 35.5 / 43.2 | NO |
| RTY settle (30, 0.0, 15, -1) | -19.1 | -23.6 | 6.9 | 14.8 | -24.6 / 4.3 | -8.3 / 13.9 | NO |
| YM settle (15, 0.5, 0, -1) (diag) | -14.6 | 23.1 | 26.9 | 44.7 | 22.5 / 24.7 | 27.4 / 28.4 | NO |
| GC settle (15, 0.5, 0, 1) (diag) | -16.1 | -22.9 | 19.6 | 23.3 | 11.3 / 24.5 | -29.5 / 7.7 | NO |
| SI settle (30, 0.25, 15, -1) (diag) | -23.1 | -129.6 | -65.0 | -286.0 | -11.7 / 0.5 | -142.0 / -109.3 | NO |
| HG settle (30, 0.5, 15, -1) (diag) | -29.1 | -33.4 | 20.5 | 25.2 | 25.5 / 27.5 | -40.6 / -6.2 | NO |
| CL settle (30, 0.25, 15, -1) (diag) | -16.7 | -24.4 | 12.5 | 27.4 | 11.8 / 15.2 | 30.0 / 35.5 | NO |
| HO settle (15, 0.5, 15, 1) | -39.3 | -244.2 | -29.3 | -33.3 | -24.6 / 5.8 | 30.0 / 30.0 | NO |
| RB settle (15, 0.25, 15, -1) | -29.0 | -18.6 | 1.0 | 19.9 | -1.3 / 15.8 | 30.0 / 32.7 | NO |
| NG settle (30, 0.5, 15, -1) | -13.2 | 10.6 | 18.8 | 34.0 | 14.2 / 19.3 | 31.2 / 31.1 | NO |
| ZN settle (30, 0.5, 15, -1) (diag) | -74.9 | -53.2 | 3.8 | -57.4 | -54.4 / -3.8 | 30.0 / 30.0 | NO |
| ZB settle (30, 0.5, 15, -1) (diag) | -89.2 | -17.7 | 1.3 | -50.0 | -18.6 / -4.8 | 6.1 / 17.4 | NO |
| 6E settle (30, 0.5, 15, 1) (diag) | -33.5 | -8.3 | 16.7 | 13.1 | -9.1 / 12.1 | 24.3 / 26.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) settle (30, 0.0, 0, -1) | negative pre-2023 | 2613 | -16.8 | -45.9 | -31.8 | 29.1 | -0.56 / -1.52 / -1.05 | 50.6 / 21.2 |
| ES 2 (diag) settle (30, 0.0, 15, -1) | negative pre-2023 | 2613 | -5.4 | -34.5 | -20.4 | 29.1 | -0.19 / -1.18 / -0.70 | 47.0 / 17.6 |
| ES 3 (diag) settle (30, 0.25, 0, -1) | negative pre-2023 | 1471 | -29.9 | -59.3 | -45.0 | 29.4 | -0.72 / -1.43 / -1.09 | 43.7 / 14.3 |
| NQ 1 settle (30, 0.5, 0, -1) | negative pre-2023 | 823 | -29.6 | -44.0 | -35.6 | 14.4 | -0.38 / -0.56 / -0.46 | 149.4 / 135.1 |
| NQ 2 settle (15, 0.5, 0, -1) | negative pre-2023 | 830 | -49.8 | -64.1 | -55.7 | 14.4 | -0.79 / -1.01 / -0.88 | 92.6 / 78.2 |
| NQ 3 settle (30, 0.25, 0, -1) | negative pre-2023 | 1536 | -36.3 | -50.7 | -42.2 | 14.4 | -0.60 / -0.84 / -0.70 | 87.7 / 73.3 |
| NQ 4 settle (30, 0.0, 0, -1) | negative pre-2023 | 2613 | -24.6 | -39.0 | -30.4 | 14.3 | -0.60 / -0.94 / -0.74 | 54.1 / 39.7 |
| NQ 5 settle (15, 0.0, 0, -1) | negative pre-2023 | 2613 | -27.4 | -41.7 | -33.2 | 14.3 | -0.94 / -1.42 / -1.13 | 43.4 / 29.0 |
| NQ 6 settle (15, 0.25, 0, -1) | negative pre-2023 | 1563 | -47.4 | -61.8 | -53.3 | 14.4 | -1.05 / -1.36 / -1.18 | 53.4 / 39.0 |
| NQ 7 settle (15, 0.5, 15, -1) | negative pre-2023 | 830 | -19.4 | -33.8 | -25.3 | 14.4 | -0.28 / -0.49 / -0.37 | 58.3 / 44.0 |
| NQ 8 (diag) settle (30, 0.5, 15, -1) | gross-positive, cost-negative pre-2023 | 823 | 0.2 | -14.2 | -5.8 | 14.4 | 0.00 / -0.17 / -0.07 | 89.9 / 75.6 |
| NQ 9 (diag) settle (30, 0.25, 15, -1) | negative pre-2023 | 1536 | -21.6 | -36.0 | -27.5 | 14.4 | -0.36 / -0.61 / -0.46 | 65.3 / 51.0 |
| NQ 10 (diag) settle (30, 0.0, 15, -1) | negative pre-2023 | 2613 | -18.6 | -33.0 | -24.4 | 14.3 | -0.44 / -0.78 / -0.58 | 19.5 / 5.2 |
| RTY 1 settle (30, 0.0, 15, -1) | negative pre-2023 | 1492 | -3.7 | -18.0 | -15.8 | 14.3 | -0.18 / -0.93 / -0.81 | 23.6 / 9.2 |
| RTY 2 settle (15, 0.0, 15, -1) | negative pre-2023 | 1492 | -5.5 | -19.9 | -17.6 | 14.3 | -0.35 / -1.30 / -1.15 | 19.1 / 4.8 |
| RTY 3 (diag) settle (30, 0.5, 0, -1) | negative pre-2023 | 500 | -21.8 | -36.1 | -33.9 | 14.4 | -0.58 / -0.96 / -0.90 | 28.9 / 14.5 |
| RTY 4 (diag) settle (30, 0.25, 0, -1) | negative pre-2023 | 951 | -4.7 | -19.0 | -16.8 | 14.4 | -0.17 / -0.74 / -0.65 | 22.8 / 8.4 |
| RTY 5 (diag) settle (30, 0.0, 0, -1) | negative pre-2023 | 1492 | -8.6 | -22.9 | -20.7 | 14.3 | -0.44 / -1.19 / -1.07 | 19.2 / 4.8 |
| YM 1 (diag) settle (15, 0.5, 0, -1) | negative pre-2023 | 737 | -35.1 | -49.5 | -43.7 | 14.4 | -0.86 / -1.20 / -1.06 | 47.6 / 33.2 |
| YM 2 (diag) settle (15, 0.25, 0, -1) | negative pre-2023 | 1464 | -27.6 | -42.0 | -36.3 | 14.4 | -1.15 / -1.74 / -1.50 | 27.0 / 12.6 |
| YM 3 (diag) settle (15, 0.5, 15, -1) | negative pre-2023 | 737 | -18.0 | -32.3 | -26.5 | 14.4 | -0.45 / -0.81 / -0.67 | 29.1 / 14.8 |
| GC 1 (diag) settle (30, 0.25, 0, 1) | gross-positive, cost-negative pre-2023 | 1308 | 2.4 | -22.0 | -12.3 | 24.4 | 0.14 / -1.22 / -0.68 | 18.0 / -6.4 |
| GC 2 (diag) settle (15, 0.5, 0, 1) | gross-positive, cost-negative pre-2023 | 564 | 8.1 | -16.2 | -6.7 | 24.4 | 0.32 / -0.62 / -0.25 | 15.4 / -9.0 |
| GC 3 (diag) settle (30, 0.5, 15, -1) | negative pre-2023 | 549 | -1.9 | -26.3 | -16.8 | 24.4 | -0.05 / -0.70 / -0.45 | 8.1 / -16.3 |
| SI 1 (diag) settle (30, 0.5, 15, 1) | negative pre-2023 | 549 | -29.4 | -83.8 | -64.9 | 54.4 | -0.66 / -1.82 / -1.42 | 32.7 / -21.7 |
| SI 2 (diag) settle (30, 0.5, 0, 1) | negative pre-2023 | 551 | -15.7 | -70.1 | -51.2 | 54.4 | -0.39 / -1.69 / -1.24 | 32.1 / -22.2 |
| SI 3 (diag) settle (30, 0.25, 15, -1) | gross-positive, cost-negative pre-2023 | 1302 | 14.4 | -39.9 | -21.1 | 54.4 | 0.57 / -1.55 / -0.82 | 19.5 / -34.9 |
| HG 1 (diag) settle (30, 0.5, 15, -1) | gross-positive, cost-negative pre-2023 | 459 | 6.5 | -22.8 | -15.4 | 29.4 | 0.22 / -0.77 / -0.52 | 79.3 / 50.0 |
| HG 2 (diag) settle (30, 0.5, 0, -1) | gross-positive, cost-negative pre-2023 | 461 | 8.8 | -20.5 | -13.0 | 29.4 | 0.38 / -0.88 / -0.56 | 39.7 / 10.4 |
| HG 3 (diag) settle (15, 0.25, 0, 1) | negative pre-2023 | 1165 | -2.4 | -31.8 | -24.2 | 29.4 | -0.33 / -3.92 / -3.04 | 30.6 / 1.2 |
| CL 1 (diag) settle (30, 0.25, 15, -1) | negative pre-2023 | 1433 | -13.6 | -37.9 | -35.4 | 24.4 | -0.44 / -1.23 / -1.14 | 20.2 / -4.2 |
| CL 2 (diag) settle (15, 0.5, 15, -1) | negative pre-2023 | 705 | -9.8 | -34.1 | -31.7 | 24.4 | -0.26 / -0.89 / -0.83 | 17.0 / -7.4 |
| CL 3 (diag) settle (15, 0.25, 15, -1) | negative pre-2023 | 1443 | -12.0 | -36.4 | -33.9 | 24.4 | -0.48 / -1.44 / -1.34 | 16.9 / -7.5 |
| HO 1 settle (15, 0.5, 0, 1) | positive pre-2023 | 705 | 19.8 | 7.1 | 8.4 | 12.8 | 0.39 / 0.13 / 0.16 | 39.1 / 26.3 |
| HO 2 settle (30, 0.5, 0, 1) | gross-positive, cost-negative pre-2023 | 691 | 10.7 | -2.1 | -0.7 | 12.8 | 0.17 / -0.05 / -0.02 | 46.2 / 33.5 |
| HO 3 settle (15, 0.5, 15, 1) | negative pre-2023 | 705 | -0.2 | -13.0 | -11.6 | 12.8 | -0.02 / -0.29 / -0.26 | 39.1 / 26.4 |
| HO 4 settle (30, 0.5, 15, 1) | negative pre-2023 | 691 | -3.8 | -16.6 | -15.3 | 12.8 | -0.08 / -0.30 / -0.27 | 30.5 / 17.8 |
| HO 5 (diag) settle (30, 0.0, 15, -1) | gross-positive, cost-negative pre-2023 | 2584 | 1.9 | -10.8 | -9.3 | 12.7 | 0.07 / -0.35 / -0.30 | 13.8 / 1.1 |
| HO 6 (diag) settle (30, 0.0, 0, -1) | negative pre-2023 | 2584 | -4.1 | -16.8 | -15.3 | 12.7 | -0.13 / -0.56 / -0.51 | 13.1 / 0.4 |
| HO 7 (diag) settle (30, 0.25, 15, -1) | positive pre-2023 | 1471 | 15.0 | 2.2 | 3.7 | 12.8 | 0.39 / 0.07 / 0.10 | 2.5 / -10.3 |
| RB 1 settle (15, 0.25, 15, -1) | gross-positive, cost-negative pre-2023 | 1525 | 10.0 | -2.8 | -1.9 | 12.8 | 0.30 / -0.09 / -0.06 | 17.1 / 4.3 |
| RB 2 (diag) settle (30, 0.0, 15, -1) | positive pre-2023 | 2573 | 17.6 | 4.9 | 5.8 | 12.8 | 0.54 / 0.14 / 0.17 | 25.7 / 12.9 |
| RB 3 (diag) settle (15, 0.5, 0, 1) | positive pre-2023 | 780 | 15.5 | 2.8 | 3.6 | 12.8 | 0.33 / 0.06 / 0.08 | 33.6 / 20.8 |
| RB 4 (diag) settle (15, 0.0, 15, -1) | gross-positive, cost-negative pre-2023 | 2574 | 4.2 | -8.5 | -7.6 | 12.7 | 0.17 / -0.32 / -0.28 | 20.7 / 7.9 |
| NG 1 settle (30, 0.5, 15, -1) | negative pre-2023 | 668 | -18.8 | -43.1 | -48.2 | 24.4 | -0.38 / -0.87 / -0.96 | 66.5 / 42.2 |
| NG 2 settle (30, 0.5, 0, -1) | negative pre-2023 | 668 | -43.0 | -67.3 | -72.4 | 24.4 | -0.98 / -1.52 / -1.61 | 58.7 / 34.3 |
| NG 3 settle (30, 0.25, 15, -1) | negative pre-2023 | 1460 | -15.6 | -40.0 | -44.8 | 24.4 | -0.53 / -1.34 / -1.48 | 27.7 / 3.4 |
| NG 4 (diag) settle (15, 0.5, 15, -1) | negative pre-2023 | 685 | -10.7 | -35.1 | -40.3 | 24.4 | -0.25 / -0.81 / -0.92 | 28.3 / 4.0 |
| NG 5 (diag) settle (30, 0.25, 0, -1) | negative pre-2023 | 1460 | -29.8 | -54.2 | -59.0 | 24.4 | -1.04 / -1.88 / -2.00 | 26.4 / 2.1 |
| NG 6 (diag) settle (15, 0.5, 0, -1) | negative pre-2023 | 685 | -32.2 | -56.5 | -61.8 | 24.4 | -0.88 / -1.53 / -1.63 | 19.9 / -4.4 |
| ZN 1 (diag) settle (30, 0.5, 15, -1) | negative pre-2023 | 686 | -8.2 | -43.8 | -48.9 | 35.6 | -0.62 / -3.18 / -3.51 | 4.5 / -31.1 |
| ZN 2 (diag) settle (30, 0.5, 0, 1) | gross-positive, cost-negative pre-2023 | 686 | 8.8 | -26.8 | -31.9 | 35.6 | 0.77 / -2.23 / -2.61 | 6.5 / -29.1 |
| ZN 3 (diag) settle (15, 0.5, 15, -1) | negative pre-2023 | 713 | -4.7 | -40.3 | -45.3 | 35.6 | -0.46 / -3.69 / -4.08 | 4.7 / -30.9 |
| ZB 1 (diag) settle (30, 0.5, 15, -1) | negative pre-2023 | 715 | -14.4 | -81.2 | -99.7 | 66.9 | -0.47 / -2.57 / -3.09 | 12.6 / -54.2 |
| ZB 2 (diag) settle (15, 0.5, 15, -1) | negative pre-2023 | 728 | -12.8 | -79.7 | -98.2 | 66.9 | -0.53 / -3.13 / -3.75 | 9.2 / -57.6 |
| ZB 3 (diag) settle (15, 0.5, 0, 1) | gross-positive, cost-negative pre-2023 | 728 | 16.6 | -50.3 | -68.8 | 66.9 | 0.88 / -2.61 / -3.47 | 15.3 / -51.5 |
| 6E 1 (diag) settle (30, 0.5, 15, 1) | gross-positive, cost-negative pre-2023 | 520 | 3.9 | -13.0 | -14.1 | 16.9 | 0.18 / -0.60 / -0.65 | 14.1 / -2.8 |
| 6E 2 (diag) settle (15, 0.5, 15, -1) | gross-positive, cost-negative pre-2023 | 527 | 0.2 | -16.6 | -17.7 | 16.9 | 0.01 / -0.93 / -0.99 | 12.1 / -4.7 |
| 6E 3 (diag) settle (15, 0.5, 0, -1) | gross-positive, cost-negative pre-2023 | 527 | 3.8 | -13.0 | -14.1 | 16.9 | 0.21 / -0.71 / -0.77 | 12.4 / -4.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); HG: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); HO: 4 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.23, p(top) = 0.51); NG: 3 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.00, p(top) = 0.04); NQ: 7 cells pass the clean rule against a replicate mean of 3.7 (p(count) = 0.05, p(top) = 0.61); RB: 1 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.91, p(top) = 0.82); RTY: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.39, p(top) = 0.62); SI: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); YM: 0 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 1.00); ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 17 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.22 (NQ settle (30, 0.5, 0, -1)); bootstrap lower bound > 0 for 6 cells; plateau >= 0.75 for 11; 2x-slippage all-in uplift >= +0.10 for 6; gate_add PASS at some share: 2 (cell-share pairs).
- ERA flags: {'negative pre-2023': 14, 'gross-positive, cost-negative pre-2023': 2, 'positive pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q23.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q23/ (`Q23_CO_all_selected_scored.csv`).

DONE Q23
