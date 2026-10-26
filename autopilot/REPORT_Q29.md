# REPORT Q29 - Q29: London-to-New-York handoff: London return sign traded at the RTH open with/against

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 40 selected cells (+14 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.20; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: London-to-New-York handoff: London return sign traded at the RTH open with/against. Time exit, no stop.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E. Grid: 36 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      36 |         36 |         0 |               0.43  |                1 |          0 |            3 |
| CL    |      36 |         36 |         8 |               1.166 |                2 |          8 |            2 |
| ES    |      36 |         36 |        10 |               1.053 |                2 |         10 |            0 |
| GC    |      36 |         36 |         2 |               0.5   |                2 |          2 |            3 |
| HO    |      36 |         36 |         0 |               0.541 |                1 |          0 |            3 |
| NQ    |      36 |         36 |        10 |               0.996 |                2 |         10 |            0 |
| RTY   |      36 |         36 |        10 |               1.719 |                2 |         10 |            0 |
| ZN    |      36 |         36 |         0 |               0.146 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   10 |            3.59  |               9 |      0     |                       0.636 |            0.673 |           1.039 |    0.49  |       1.053 |                1.589 |
| NQ    |     200 |                   10 |            6.205 |              13 |      0.095 |                       0.711 |            0.754 |           1.087 |    0.595 |       0.996 |                1.935 |
| RTY   |     200 |                   10 |            4.005 |               9 |      0     |                       0.968 |            0.703 |           1.102 |    0.095 |       1.719 |                1.865 |
| GC    |     200 |                    2 |            3.525 |               8 |      0.875 |                       0.497 |            0.68  |           1.111 |    0.745 |       0.5   |                1.7   |
| CL    |     200 |                    8 |            2.81  |               8 |      0.005 |                       0.601 |            0.635 |           1.062 |    0.52  |       1.166 |                1.523 |
| ZN    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.926 |           0.926 |  nan     |     nan     |                0.926 |
| HO    |     200 |                    0 |            6.33  |              13 |      1     |                     nan     |            0.742 |           1.049 |  nan     |     nan     |                1.928 |
| 6E    |     200 |                    0 |            1.23  |               5 |      1     |                     nan     |            0.565 |           1.014 |  nan     |     nan     |                1.21  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | lon (5, 0.0, 180, -1) | 516 | 2 | 1.05 | -0.65 | 0.58 | 0.12 / 0.96 | 0.19 / -0.06 / -0.10 | 0.04 | 0.10 | 0.93 | -0.13 | 0.00 | 828 | NO |
| ES 2 | lon (0, 0.0, 180, -1) | 516 | 2 | 1.00 | -0.79 | 0.39 | -0.22 / 1.47 | 0.19 / -0.22 / -0.15 | 0.01 | -0.02 | 0.91 | -0.16 | 0.00 | 828 | NO |
| ES 3 | lon (0, 0.3, 180, -1) | 123 | 2 | 0.69 | -0.39 | 0.21 | -0.85 / 1.00 | 0.11 / -0.47 / 0.03 | -0.01 | 0.23 | 0.81 | -0.15 | 0.00 | 195 | NO |
| ES 4 | lon (0, 0.15, 180, -1) | 279 | 2 | 0.65 | -0.55 | 0.27 | -0.20 / 1.20 | 0.11 / -0.38 / 0.05 | -0.00 | 0.14 | 0.86 | -0.17 | 0.00 | 437 | NO |
| ES 5 | lon (5, 0.3, 180, -1) | 123 | 2 | 0.64 | -0.28 | 0.23 | -0.65 / 1.43 | 0.10 / -0.43 / 0.03 | -0.01 | 0.32 | 0.75 | -0.15 | 0.50 | 195 | NO |
| ES 6 | lon (5, 0.15, 180, -1) | 279 | 2 | 0.63 | -0.42 | 0.35 | 0.01 / 1.06 | 0.10 / -0.23 / 0.03 | 0.00 | 0.28 | 0.89 | -0.16 | 0.00 | 437 | NO |
| ES 7 | lon (0, 0.3, 120, -1) | 123 | 2 | 0.59 | -0.20 | -0.02 | -0.98 / 1.24 | 0.09 / -0.64 / -0.04 | -0.07 | 0.41 | 0.65 | -0.24 | 0.00 | 195 | NO |
| ES 8 | lon (5, 0.3, 120, -1) | 123 | 2 | 0.48 | -0.15 | 0.05 | -0.66 / 1.01 | 0.07 / -0.56 / 0.05 | -0.05 | 0.40 | 0.71 | -0.21 | 0.00 | 195 | NO |
| ES 9 | lon (0, 0.15, 120, -1) | 279 | 2 | 0.35 | -0.42 | -0.17 | -0.77 / 1.23 | 0.07 / -0.63 / -0.17 | -0.12 | 0.28 | 0.61 | -0.30 | 0.00 | 437 | NO |
| ES 10 | lon (5, 0.15, 120, -1) | 279 | 2 | 0.28 | -0.26 | -0.10 | -0.57 / 1.12 | 0.05 / -0.50 / -0.10 | -0.10 | 0.35 | 0.71 | -0.27 | 0.00 | 437 | NO |
| NQ 1 | lon (5, 0.15, 180, -1) | 282 | 2 | 1.00 | 0.12 | 0.52 | -0.02 / 1.45 | 0.21 / -0.52 / 0.30 | 0.12 | 0.36 | 0.87 | -0.10 | 1.00 | 442 | NO |
| NQ 2 | lon (0, 0.15, 120, -1) | 282 | 2 | 0.96 | 0.25 | 0.36 | -0.29 / 1.36 | 0.21 / -0.71 / 0.24 | 0.08 | 0.29 | 0.78 | -0.14 | 1.00 | 442 | NO |
| NQ 3 | lon (0, 0.15, 180, -1) | 282 | 2 | 0.91 | 0.04 | 0.32 | -0.33 / 1.44 | 0.19 / -0.73 / 0.29 | 0.07 | 0.20 | 0.74 | -0.16 | 1.00 | 442 | NO |
| NQ 4 | lon (5, 0.15, 120, -1) | 282 | 2 | 0.89 | 0.37 | 0.42 | -0.13 / 1.09 | 0.20 / -0.61 / 0.27 | 0.09 | 0.44 | 0.79 | -0.13 | 1.00 | 442 | NO |
| NQ 5 | lon (5, 0.0, 180, -1) | 516 | 2 | 0.78 | -0.20 | 0.55 | 0.34 / 1.63 | 0.14 / -0.31 / 0.23 | 0.10 | 0.20 | 0.82 | -0.12 | 0.50 | 828 | NO |
| NQ 6 | lon (0, 0.0, 180, -1) | 516 | 2 | 0.78 | -0.29 | 0.43 | 0.09 / 1.26 | 0.15 / -0.50 / 0.24 | 0.07 | 0.10 | 0.83 | -0.16 | 0.00 | 828 | NO |
| NQ 7 | lon (5, 0.3, 120, -1) | 117 | 2 | 0.49 | 0.36 | 0.18 | -0.24 / 1.59 | 0.12 / -0.47 / 0.15 | 0.04 | 0.37 | 0.72 | -0.17 | 0.50 | 193 | NO |
| NQ 8 | lon (0, 0.3, 120, -1) | 117 | 2 | 0.45 | 0.27 | -0.02 | -0.58 / 1.18 | 0.12 / -0.63 / 0.03 | -0.00 | 0.38 | 0.52 | -0.23 | 1.00 | 193 | NO |
| NQ 9 | lon (5, 0.3, 180, -1) | 117 | 2 | 0.43 | 0.09 | 0.19 | -0.15 / 1.51 | 0.11 / -0.48 / 0.17 | 0.04 | 0.17 | 0.66 | -0.17 | 0.50 | 193 | NO |
| NQ 10 | lon (5, 0.0, 120, -1) | 516 | 2 | 0.41 | -0.05 | 0.12 | -0.14 / 1.39 | 0.08 / -0.52 / 0.08 | -0.01 | 0.29 | 0.61 | -0.22 | 1.00 | 828 | NO |
| RTY 1 | lon (5, 0.15, 180, -1) | 298 | 2 | 1.72 | -0.07 | 0.57 | -0.90 / 1.35 | 0.26 / -0.38 / -0.27 | 0.02 | 0.08 | 0.90 | -0.16 | 1.00 | 464 | NO |
| RTY 2 | lon (5, 0.15, 120, -1) | 298 | 2 | 1.48 | -0.07 | 0.48 | -0.88 / 1.21 | 0.23 / -0.41 / -0.31 | -0.01 | 0.14 | 0.94 | -0.18 | 0.50 | 464 | NO |
| RTY 3 | lon (0, 0.15, 180, -1) | 298 | 2 | 1.39 | -0.14 | 0.30 | -1.11 / 1.25 | 0.22 / -0.47 / -0.27 | -0.02 | 0.01 | 0.80 | -0.20 | 0.00 | 464 | NO |
| RTY 4 | lon (0, 0.15, 120, -1) | 298 | 2 | 1.17 | -0.14 | 0.16 | -1.14 / 1.29 | 0.18 / -0.61 / -0.35 | -0.08 | 0.14 | 0.76 | -0.25 | 0.00 | 464 | NO |
| RTY 5 | lon (5, 0.3, 180, -1) | 143 | 2 | 1.07 | 0.19 | 0.53 | -0.27 / 0.87 | 0.16 / -0.46 / 0.09 | 0.04 | 0.25 | 0.92 | -0.14 | 1.00 | 219 | NO |
| RTY 6 | lon (5, 0.0, 180, -1) | 516 | 2 | 0.85 | -0.14 | 0.38 | -0.21 / 1.09 | 0.13 / 0.02 / -0.13 | 0.01 | -0.29 | 0.89 | -0.16 | 1.00 | 828 | NO |
| RTY 7 | lon (5, 0.15, 60, -1) | 298 | 2 | 0.68 | -0.22 | 0.30 | -0.26 / 0.82 | 0.10 / -0.44 / 0.04 | -0.02 | 0.27 | 0.94 | -0.19 | 1.00 | 464 | NO |
| RTY 8 | lon (5, 0.0, 120, -1) | 516 | 2 | 0.57 | -0.06 | 0.25 | -0.18 / 1.08 | 0.09 / -0.05 / -0.13 | -0.02 | -0.31 | 0.87 | -0.18 | 0.50 | 828 | NO |
| RTY 9 | lon (0, 0.0, 180, -1) | 516 | 2 | 0.55 | -0.15 | 0.19 | -0.27 / 1.15 | 0.09 / -0.02 / -0.09 | -0.01 | -0.28 | 0.83 | -0.18 | 0.50 | 828 | NO |
| RTY 10 | lon (0, 0.0, 120, -1) | 516 | 2 | 0.20 | -0.16 | -0.02 | -0.34 / 1.23 | 0.03 / -0.13 / -0.17 | -0.08 | -0.23 | 0.76 | -0.23 | 0.00 | 828 | NO |
| GC 1 | lon (5, 0.3, 60, -1) | 112 | 2 | 0.50 | -0.44 | -0.62 | -1.51 / 1.37 | 0.07 / -0.11 / -1.41 | -0.31 | -0.27 | 0.23 | -0.61 | 0.00 | 165 | NO |
| GC 2 | lon (0, 0.3, 60, -1) | 111 | 2 | 0.49 | -0.30 | -0.64 | -1.75 / 1.27 | 0.09 / 0.02 / -1.25 | -0.25 | -0.26 | 0.20 | -0.49 | 0.00 | 164 | NO |
| GC 3 (diag) | lon (5, 0.3, 180, -1) | 112 | 1 | 0.19 | -0.55 | -0.50 | -1.09 / 1.80 | 0.05 / -0.93 / -0.65 | -0.25 | -0.05 | 0.16 | -0.55 | 0.00 | 165 | diag |
| GC 4 (diag) | lon (0, 0.15, 120, 1) | 264 | 1 | 0.16 | -0.39 | 0.71 | 1.26 / 1.32 | 0.03 / 0.22 / 0.33 | 0.10 | -0.02 | 0.95 | -0.10 | 0.50 | 388 | diag |
| GC 5 (diag) | lon (0, 0.15, 180, 1) | 264 | 1 | 0.12 | -0.18 | 0.62 | 1.08 / 1.54 | 0.01 / 0.41 / 0.57 | 0.14 | -0.06 | 0.90 | -0.09 | 0.50 | 388 | diag |
| CL 1 | lon (5, 0.3, 60, -1) | 161 | 2 | 1.17 | -0.66 | 0.36 | -0.62 / 1.03 | 0.20 / -0.06 / -0.33 | -0.03 | -0.35 | 0.95 | -0.16 | 1.00 | 286 | NO |
| CL 2 | lon (0, 0.3, 60, -1) | 161 | 2 | 0.75 | -0.40 | 0.12 | -0.55 / 1.19 | 0.12 / 0.15 / -0.37 | -0.06 | -0.30 | 0.80 | -0.21 | 1.00 | 286 | NO |
| CL 3 | lon (0, 0.3, 120, -1) | 161 | 2 | 0.66 | -0.24 | 0.89 | 1.18 / 1.10 | 0.12 / 0.21 / 0.46 | 0.15 | -0.18 | 0.98 | -0.00 | 0.00 | 286 | LEAD |
| CL 4 | lon (5, 0.3, 180, -1) | 161 | 2 | 0.62 | -0.28 | 0.27 | -0.14 / 1.31 | 0.12 / -0.14 / -0.18 | -0.03 | 0.04 | 0.78 | -0.21 | 1.00 | 286 | NO |
| CL 5 | lon (0, 0.3, 180, -1) | 161 | 2 | 0.50 | -0.23 | 0.28 | 0.02 / 1.54 | 0.09 / -0.06 / -0.15 | -0.03 | 0.01 | 0.85 | -0.21 | 1.00 | 286 | NO |
| CL 6 | lon (5, 0.3, 120, -1) | 161 | 2 | 0.43 | -0.30 | 0.78 | 1.20 / 1.10 | 0.07 / 0.21 / 0.38 | 0.11 | -0.20 | 0.96 | -0.04 | 0.50 | 286 | NO |
| CL 7 | lon (5, 0.0, 180, 1) | 516 | 2 | 0.34 | -0.08 | 0.48 | 0.56 / 1.34 | 0.04 / -0.18 / 0.18 | -0.03 | 0.15 | 0.96 | -0.18 | 0.00 | 828 | NO |
| CL 8 | lon (0, 0.0, 180, 1) | 516 | 2 | 0.32 | -0.21 | 0.34 | 0.31 / 1.27 | 0.03 / -0.25 / 0.09 | -0.06 | 0.13 | 0.87 | -0.21 | 0.00 | 828 | NO |
| CL 9 (diag) | lon (0, 0.15, 120, -1) | 317 | 1 | 0.10 | -0.74 | 0.07 | 0.06 / 1.26 | -0.00 / 0.11 / -0.07 | -0.07 | 0.19 | 0.79 | -0.19 | 0.00 | 518 | diag |
| CL 10 (diag) | lon (5, 0.15, 60, -1) | 317 | 1 | 0.09 | -1.01 | -0.39 | -0.99 / 1.38 | -0.02 / -0.21 / -0.43 | -0.23 | -0.17 | 0.68 | -0.33 | 0.00 | 518 | diag |
| ZN 1 (diag) | lon (0, 0.15, 180, -1) | 264 | 1 | 0.15 | -1.55 | -0.99 | -3.29 / -1.17 | 0.02 / -0.48 / -0.54 | -0.45 | -0.13 | 0.98 | -0.36 | 0.00 | 438 | diag |
| ZN 2 (diag) | lon (5, 0.15, 180, -1) | 264 | 1 | 0.14 | -1.61 | -0.99 | -3.26 / -0.75 | 0.01 / -0.51 / -0.55 | -0.46 | -0.11 | 0.99 | -0.38 | 0.00 | 438 | diag |
| ZN 3 (diag) | lon (5, 0.3, 180, -1) | 105 | 1 | 0.01 | -1.19 | -1.14 | -3.68 / -0.58 | -0.03 / -0.56 / -0.58 | -0.40 | -0.13 | 0.68 | -0.42 | 0.00 | 179 | diag |
| HO 1 (diag) | lon (5, 0.0, 60, -1) | 488 | 1 | 0.54 | -0.61 | -0.72 | -1.67 / 1.27 | 0.04 / -0.36 / -1.32 | -0.38 | 0.10 | 0.23 | -0.63 | 0.00 | 798 | diag |
| HO 2 (diag) | lon (5, 0.15, 180, -1) | 331 | 1 | 0.46 | -0.59 | -0.59 | -1.39 / 1.44 | 0.06 / -0.54 / -1.14 | -0.33 | 0.17 | 0.15 | -0.60 | 0.00 | 532 | diag |
| HO 3 (diag) | lon (5, 0.0, 120, -1) | 488 | 1 | 0.42 | -0.49 | -0.48 | -1.25 / 1.33 | 0.05 / -0.30 / -0.90 | -0.24 | 0.29 | 0.32 | -0.46 | 0.00 | 798 | diag |
| 6E 1 (diag) | lon (5, 0.15, 60, 1) | 304 | 1 | 0.43 | -0.86 | 0.24 | -0.42 / -0.34 | 0.10 / -0.69 / 0.09 | -0.13 | -0.26 | 1.00 | -0.16 | 0.00 | 490 | diag |
| 6E 2 (diag) | lon (0, 0.15, 60, 1) | 304 | 1 | 0.21 | -0.85 | 0.05 | -0.51 / -0.28 | 0.04 / -0.75 / 0.11 | -0.18 | -0.27 | 1.00 | -0.20 | 0.00 | 490 | diag |
| 6E 3 (diag) | lon (5, 0.15, 180, 1) | 304 | 1 | 0.16 | -0.72 | 0.37 | 0.56 / 0.75 | 0.04 / -0.06 / 0.10 | -0.03 | -0.33 | 0.99 | -0.11 | 0.00 | 490 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 40 |
| diagnostic cells read | 14 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 36 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 46 |
| plateau >= 0.75 | 14 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E lon (5, 0.15, 180, 1) (diag) | clean | 0.25 | 0.37 | -124036 | -107170 | 817301 | -164984 | 0.27 | 53.3 | 1.50 | -89367 | 262533 | -110055 |
| 6E lon (5, 0.15, 180, 1) (diag) | H1 | 0.31 | 0.45 | -140937 | -123151 | 310125 | -189755 | 0.27 | 46.4 | 2.77 | -79243 | 153772 | -84562 |
| 6E lon (5, 0.15, 180, 1) (diag) | H2 | 0.85 | 1.31 | -102943 | -80852 | 250544 | -106381 | 0.78 | 50.0 | 2.58 | -79610 | 223984 | -83924 |
| 6E lon (5, 0.15, 180, 1) (diag) | all | 0.37 | 0.56 | -117509 | -102841 | 904097 | -164984 | 0.55 | 51.8 | 1.95 | -87455 | 262533 | -110055 |
| CL lon (0, 0.3, 120, -1) | clean | 0.65 | 1.17 | -105406 | -90795 | 354967 | -125119 | 1.67 | 42.9 | 1.58 | -85592 | 285456 | -93128 |
| CL lon (0, 0.3, 120, -1) | H1 | 0.86 | 1.49 | -85580 | -72846 | 216491 | -100502 | 0.78 | 46.4 | 3.03 | -75258 | 146521 | -82940 |
| CL lon (0, 0.3, 120, -1) | H2 | 1.39 | 2.86 | -199495 | -140424 | 344335 | -206633 | 2.32 | 44.4 | 2.94 | -85895 | 206933 | -85939 |
| CL lon (0, 0.3, 120, -1) | all | 0.89 | 1.69 | -125770 | -102974 | 354967 | -206633 | 4.40 | 44.0 | 2.10 | -85365 | 285456 | -93128 |
| ES lon (5, 0.0, 180, -1) | clean | 1.05 | 1.64 | -119952 | -96919 | 430324 | -255046 | 2.22 | 43.8 | 1.65 | -87592 | 295069 | -96109 |
| ES lon (5, 0.0, 180, -1) | H1 | 0.93 | 1.38 | -198018 | -165697 | 391592 | -275731 | 0.90 | 42.9 | 2.77 | -89382 | 191812 | -97234 |
| ES lon (5, 0.0, 180, -1) | H2 | -0.48 | -0.68 | -199167 | -172448 | 773870 | -222869 | -0.32 | 61.1 | 2.38 | -97107 | 232450 | -100787 |
| ES lon (5, 0.0, 180, -1) | all | 0.58 | 0.85 | -176901 | -137147 | 773870 | -275731 | 1.37 | 47.6 | 2.00 | -90834 | 295069 | -100787 |
| GC lon (0, 0.3, 60, -1) | clean | 0.49 | 0.83 | -129861 | -102405 | 320574 | -165934 | 1.39 | 33.3 | 1.55 | -84971 | 243363 | -99694 |
| GC lon (0, 0.3, 60, -1) | H1 | 0.76 | 1.06 | -160569 | -146654 | 364052 | -178602 | 0.57 | 21.4 | 2.85 | -95470 | 160368 | -114008 |
| GC lon (0, 0.3, 60, -1) | H2 | -2.99 | -2.82 | -491894 | -347000 | 1987888 | -615956 | -0.97 | 38.9 | 1.24 | -103385 | 282457 | -120039 |
| GC lon (0, 0.3, 60, -1) | all | -0.64 | -0.75 | -243745 | -184422 | 2160597 | -615956 | -0.59 | 32.7 | 1.68 | -93332 | 282457 | -120039 |
| HO lon (5, 0.0, 120, -1) (diag) | clean | 0.42 | 0.63 | -126008 | -104205 | 583119 | -168013 | 0.65 | 49.5 | 1.51 | -85255 | 257887 | -89096 |
| HO lon (5, 0.0, 120, -1) (diag) | H1 | -1.17 | -1.63 | -101260 | -88692 | 407948 | -114302 | -0.62 | 57.1 | 2.52 | -84136 | 165928 | -89643 |
| HO lon (5, 0.0, 120, -1) (diag) | H2 | -1.43 | -1.71 | -475273 | -336108 | 1725413 | -633127 | -0.69 | 66.7 | 1.58 | -109215 | 272154 | -120669 |
| HO lon (5, 0.0, 120, -1) (diag) | all | -0.48 | -0.61 | -230371 | -173752 | 2201596 | -633127 | -0.48 | 54.8 | 1.68 | -92976 | 272154 | -120669 |
| NQ lon (5, 0.15, 180, -1) | clean | 1.03 | 1.62 | -115697 | -92683 | 394660 | -260172 | 2.36 | 40.0 | 1.67 | -83848 | 240110 | -92813 |
| NQ lon (5, 0.15, 180, -1) | H1 | -1.39 | -1.52 | -229130 | -183563 | 462090 | -362467 | -1.00 | 53.6 | 2.31 | -84777 | 198307 | -98877 |
| NQ lon (5, 0.15, 180, -1) | H2 | 0.91 | 1.57 | -196695 | -150733 | 443297 | -212184 | 1.00 | 44.4 | 2.78 | -84428 | 214385 | -89203 |
| NQ lon (5, 0.15, 180, -1) | all | 0.52 | 0.76 | -169286 | -126559 | 631297 | -362467 | 1.44 | 42.9 | 2.02 | -85673 | 240110 | -98877 |
| RTY lon (5, 0.3, 180, -1) | clean | 1.06 | 1.85 | -110396 | -95497 | 542707 | -133518 | 1.78 | 28.6 | 1.62 | -83170 | 307566 | -92317 |
| RTY lon (5, 0.3, 180, -1) | H1 | -0.60 | -0.70 | -246948 | -199196 | 399779 | -269959 | -0.49 | 28.6 | 2.37 | -81166 | 171224 | -81955 |
| RTY lon (5, 0.3, 180, -1) | H2 | 0.11 | 0.18 | -98222 | -80865 | 266166 | -104899 | 0.11 | 47.2 | 2.58 | -81089 | 225983 | -82524 |
| RTY lon (5, 0.3, 180, -1) | all | 0.53 | 0.79 | -141380 | -113644 | 542707 | -269959 | 1.47 | 32.7 | 1.95 | -82828 | 307566 | -92317 |
| ZN lon (0, 0.15, 180, -1) (diag) | clean | 0.11 | 0.16 | -119991 | -103017 | 681083 | -162038 | 0.15 | 47.6 | 1.48 | -89375 | 272513 | -96119 |
| ZN lon (0, 0.15, 180, -1) (diag) | H1 | -2.13 | -2.52 | -135135 | -123418 | 628359 | -148741 | -0.74 | 64.3 | 2.34 | -83965 | 166865 | -87055 |
| ZN lon (0, 0.15, 180, -1) (diag) | H2 | -4.50 | -4.01 | -118204 | -110602 | 1024640 | -121529 | -0.95 | 77.8 | 1.94 | -82928 | 226908 | -82960 |
| ZN lon (0, 0.15, 180, -1) (diag) | all | -0.99 | -1.27 | -126236 | -110775 | 1928823 | -162038 | -0.69 | 56.5 | 1.72 | -87684 | 272513 | -96119 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES lon (5, 0.0, 180, -1) | -18.4 | -22.6 | 2.1 | 19.8 | 3.9 / 12.8 | -29.3 / -18.8 | NO |
| NQ lon (5, 0.15, 180, -1) | -20.0 | -54.1 | 10.6 | 28.3 | 9.0 / 18.2 | -62.5 / -9.9 | NO |
| RTY lon (5, 0.3, 180, -1) | -21.3 | -20.5 | 16.3 | 1.1 | 10.9 / 19.7 | -27.0 / -2.9 | NO |
| GC lon (0, 0.3, 60, -1) | -43.9 | -70.5 | -11.8 | -3.7 | -7.4 / 17.0 | -38.4 / -4.5 | NO |
| CL lon (0, 0.3, 120, -1) | -12.9 | 10.1 | 17.5 | 22.6 | 9.4 / 16.3 | 19.7 / 34.3 | NO |
| ZN lon (0, 0.15, 180, -1) (diag) | -44.6 | -0.1 | 9.8 | 25.9 | -0.9 / 5.1 | 11.8 / 17.7 | NO |
| HO lon (5, 0.0, 120, -1) (diag) | -41.7 | -42.1 | -2.3 | -18.9 | 8.1 / 13.4 | 6.9 / 17.4 | NO |
| 6E lon (5, 0.15, 180, 1) (diag) | -24.5 | -25.3 | 13.1 | 37.7 | -26.3 / 8.1 | 18.0 / 25.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 lon (5, 0.0, 180, -1) | negative pre-2023 | 2683 | -4.7 | -33.7 | -19.7 | 29.0 | -0.09 / -0.65 / -0.38 | 109.8 / 80.6 |
| ES 2 lon (0, 0.0, 180, -1) | negative pre-2023 | 2683 | -10.7 | -39.7 | -25.7 | 29.0 | -0.21 / -0.79 / -0.51 | 109.5 / 80.3 |
| ES 3 lon (0, 0.3, 180, -1) | negative pre-2023 | 677 | -16.3 | -45.7 | -31.4 | 29.4 | -0.14 / -0.39 / -0.27 | 194.3 / 164.9 |
| ES 4 lon (0, 0.15, 180, -1) | negative pre-2023 | 1452 | -11.4 | -40.7 | -26.5 | 29.4 | -0.15 / -0.55 / -0.36 | 110.5 / 81.2 |
| ES 5 lon (5, 0.3, 180, -1) | negative pre-2023 | 677 | -3.3 | -32.6 | -18.4 | 29.4 | -0.03 / -0.28 / -0.16 | 174.8 / 145.4 |
| ES 6 lon (5, 0.15, 180, -1) | negative pre-2023 | 1452 | -2.3 | -31.7 | -17.5 | 29.4 | -0.03 / -0.42 / -0.23 | 103.8 / 74.4 |
| ES 7 lon (0, 0.3, 120, -1) | gross-positive, cost-negative pre-2023 | 677 | 8.0 | -21.4 | -7.1 | 29.4 | 0.07 / -0.20 / -0.07 | 123.9 / 94.5 |
| ES 8 lon (5, 0.3, 120, -1) | gross-positive, cost-negative pre-2023 | 677 | 13.5 | -15.9 | -1.6 | 29.4 | 0.12 / -0.15 / -0.02 | 109.6 / 80.2 |
| ES 9 lon (0, 0.15, 120, -1) | gross-positive, cost-negative pre-2023 | 1452 | 1.3 | -28.0 | -13.8 | 29.4 | 0.02 / -0.42 / -0.21 | 60.5 / 31.1 |
| ES 10 lon (5, 0.15, 120, -1) | gross-positive, cost-negative pre-2023 | 1452 | 11.8 | -17.5 | -3.3 | 29.4 | 0.17 / -0.26 / -0.05 | 55.3 / 25.9 |
| NQ 1 lon (5, 0.15, 180, -1) | positive pre-2023 | 1371 | 31.1 | 16.7 | 25.3 | 14.4 | 0.23 / 0.12 / 0.19 | 274.2 / 259.8 |
| NQ 2 lon (0, 0.15, 120, -1) | positive pre-2023 | 1371 | 43.8 | 29.4 | 38.0 | 14.4 | 0.37 / 0.25 / 0.32 | 217.6 / 203.2 |
| NQ 3 lon (0, 0.15, 180, -1) | positive pre-2023 | 1371 | 19.9 | 5.5 | 14.1 | 14.4 | 0.15 / 0.04 / 0.10 | 252.4 / 238.0 |
| NQ 4 lon (5, 0.15, 120, -1) | positive pre-2023 | 1371 | 58.1 | 43.7 | 52.3 | 14.4 | 0.49 / 0.37 / 0.44 | 212.7 / 198.3 |
| NQ 5 lon (5, 0.0, 180, -1) | negative pre-2023 | 2680 | -3.5 | -17.8 | -9.3 | 14.3 | -0.04 / -0.20 / -0.10 | 145.0 / 130.7 |
| NQ 6 lon (0, 0.0, 180, -1) | negative pre-2023 | 2679 | -11.6 | -25.9 | -17.4 | 14.3 | -0.13 / -0.29 / -0.19 | 144.9 / 130.6 |
| NQ 7 lon (5, 0.3, 120, -1) | positive pre-2023 | 603 | 77.6 | 63.3 | 71.7 | 14.4 | 0.44 / 0.36 / 0.41 | 175.8 / 161.5 |
| NQ 8 lon (0, 0.3, 120, -1) | positive pre-2023 | 603 | 61.1 | 46.7 | 55.1 | 14.4 | 0.35 / 0.27 / 0.31 | 146.6 / 132.3 |
| NQ 9 lon (5, 0.3, 180, -1) | positive pre-2023 | 603 | 32.2 | 17.9 | 26.3 | 14.4 | 0.17 / 0.09 / 0.14 | 180.5 / 166.2 |
| NQ 10 lon (5, 0.0, 120, -1) | gross-positive, cost-negative pre-2023 | 2680 | 10.0 | -4.3 | 4.3 | 14.3 | 0.12 / -0.05 / 0.05 | 69.8 / 55.4 |
| RTY 1 lon (5, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 773 | 8.1 | -6.3 | -4.1 | 14.4 | 0.12 / -0.07 / -0.05 | 131.4 / 117.1 |
| RTY 2 lon (5, 0.15, 120, -1) | gross-positive, cost-negative pre-2023 | 773 | 8.9 | -5.4 | -3.3 | 14.4 | 0.14 / -0.07 / -0.04 | 103.3 / 89.0 |
| RTY 3 lon (0, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 772 | 3.0 | -11.4 | -9.2 | 14.4 | 0.05 / -0.14 / -0.12 | 111.9 / 97.6 |
| RTY 4 lon (0, 0.15, 120, -1) | gross-positive, cost-negative pre-2023 | 772 | 3.9 | -10.5 | -8.4 | 14.4 | 0.07 / -0.14 / -0.11 | 83.1 / 68.7 |
| RTY 5 lon (5, 0.3, 180, -1) | positive pre-2023 | 313 | 37.9 | 23.5 | 25.7 | 14.4 | 0.30 / 0.19 / 0.20 | 122.5 / 108.2 |
| RTY 6 lon (5, 0.0, 180, -1) | gross-positive, cost-negative pre-2023 | 1519 | 6.9 | -7.3 | -5.1 | 14.3 | 0.15 / -0.14 / -0.10 | 58.0 / 43.6 |
| RTY 7 lon (5, 0.15, 60, -1) | gross-positive, cost-negative pre-2023 | 773 | 1.8 | -12.6 | -10.4 | 14.4 | 0.05 / -0.22 / -0.18 | 53.5 / 39.2 |
| RTY 8 lon (5, 0.0, 120, -1) | gross-positive, cost-negative pre-2023 | 1519 | 11.0 | -3.3 | -1.1 | 14.3 | 0.25 / -0.06 / -0.02 | 42.2 / 27.8 |
| RTY 9 lon (0, 0.0, 180, -1) | gross-positive, cost-negative pre-2023 | 1517 | 6.5 | -7.8 | -5.6 | 14.3 | 0.14 / -0.15 / -0.10 | 43.8 / 29.5 |
| RTY 10 lon (0, 0.0, 120, -1) | gross-positive, cost-negative pre-2023 | 1517 | 6.4 | -7.9 | -5.7 | 14.3 | 0.15 / -0.16 / -0.12 | 25.4 / 11.0 |
| GC 1 lon (5, 0.3, 60, -1) | negative pre-2023 | 617 | -9.6 | -34.0 | -24.1 | 24.4 | -0.12 / -0.44 / -0.31 | 94.8 / 70.5 |
| GC 2 lon (0, 0.3, 60, -1) | gross-positive, cost-negative pre-2023 | 616 | 1.8 | -22.6 | -12.8 | 24.4 | 0.02 / -0.30 / -0.17 | 95.4 / 71.0 |
| GC 3 (diag) lon (5, 0.3, 180, -1) | negative pre-2023 | 617 | -46.6 | -71.0 | -61.1 | 24.4 | -0.36 / -0.55 / -0.48 | 65.5 / 41.2 |
| GC 4 (diag) lon (0, 0.15, 120, 1) | negative pre-2023 | 1406 | -1.4 | -25.8 | -15.9 | 24.4 | -0.03 / -0.39 / -0.24 | 43.9 / 19.5 |
| GC 5 (diag) lon (0, 0.15, 180, 1) | gross-positive, cost-negative pre-2023 | 1406 | 11.1 | -13.3 | -3.4 | 24.4 | 0.13 / -0.18 / -0.05 | 40.9 / 16.5 |
| CL 1 lon (5, 0.3, 60, -1) | negative pre-2023 | 847 | -19.2 | -43.5 | -41.1 | 24.4 | -0.29 / -0.66 / -0.63 | 93.4 / 69.0 |
| CL 2 lon (0, 0.3, 60, -1) | negative pre-2023 | 846 | -0.7 | -25.1 | -22.6 | 24.4 | -0.01 / -0.40 / -0.36 | 69.4 / 45.0 |
| CL 3 lon (0, 0.3, 120, -1) | gross-positive, cost-negative pre-2023 | 846 | 2.3 | -22.0 | -19.6 | 24.4 | 0.03 / -0.24 / -0.21 | 83.0 / 58.6 |
| CL 4 lon (5, 0.3, 180, -1) | negative pre-2023 | 847 | -7.8 | -32.1 | -29.7 | 24.4 | -0.06 / -0.28 / -0.26 | 90.9 / 66.6 |
| CL 5 lon (0, 0.3, 180, -1) | negative pre-2023 | 846 | -1.5 | -25.9 | -23.4 | 24.4 | -0.01 / -0.23 / -0.21 | 78.3 / 54.0 |
| CL 6 lon (5, 0.3, 120, -1) | negative pre-2023 | 847 | -3.5 | -27.9 | -25.4 | 24.4 | -0.04 / -0.30 / -0.28 | 61.2 / 36.9 |
| CL 7 lon (5, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2679 | 19.7 | -4.5 | -1.9 | 24.2 | 0.33 / -0.08 / -0.04 | 45.9 / 21.6 |
| CL 8 lon (0, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2678 | 12.2 | -12.0 | -9.4 | 24.2 | 0.21 / -0.21 / -0.16 | 45.1 / 20.8 |
| CL 9 (diag) lon (0, 0.15, 120, -1) | negative pre-2023 | 1623 | -21.9 | -46.3 | -43.6 | 24.4 | -0.35 / -0.74 / -0.70 | 29.0 / 4.6 |
| CL 10 (diag) lon (5, 0.15, 60, -1) | negative pre-2023 | 1624 | -21.5 | -45.8 | -43.2 | 24.4 | -0.47 / -1.01 / -0.96 | 26.8 / 2.5 |
| ZN 1 (diag) lon (0, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 1433 | 2.4 | -33.3 | -38.4 | 35.6 | 0.11 / -1.55 / -1.79 | 38.4 / 2.7 |
| ZN 2 (diag) lon (5, 0.15, 180, -1) | gross-positive, cost-negative pre-2023 | 1438 | 0.8 | -34.8 | -39.9 | 35.6 | 0.04 / -1.61 / -1.84 | 38.7 / 3.1 |
| ZN 3 (diag) lon (5, 0.3, 180, -1) | negative pre-2023 | 575 | -6.3 | -41.9 | -47.1 | 35.6 | -0.17 / -1.19 / -1.33 | 37.9 / 2.3 |
| HO 1 (diag) lon (5, 0.0, 60, -1) | negative pre-2023 | 2393 | -10.6 | -23.3 | -21.7 | 12.7 | -0.28 / -0.61 / -0.57 | 33.0 / 20.3 |
| HO 2 (diag) lon (5, 0.15, 180, -1) | negative pre-2023 | 1464 | -51.4 | -64.1 | -62.5 | 12.8 | -0.47 / -0.59 / -0.57 | 51.5 / 38.7 |
| HO 3 (diag) lon (5, 0.0, 120, -1) | negative pre-2023 | 2392 | -17.8 | -30.5 | -28.9 | 12.7 | -0.29 / -0.49 / -0.46 | 38.2 / 25.4 |
| 6E 1 (diag) lon (5, 0.15, 60, 1) | negative pre-2023 | 1676 | -3.8 | -20.6 | -21.8 | 16.9 | -0.16 / -0.86 / -0.91 | 27.9 / 11.1 |
| 6E 2 (diag) lon (0, 0.15, 60, 1) | negative pre-2023 | 1673 | -3.8 | -20.6 | -21.8 | 16.9 | -0.16 / -0.85 / -0.90 | 23.6 / 6.8 |
| 6E 3 (diag) lon (5, 0.15, 180, 1) | negative pre-2023 | 1675 | -8.1 | -25.0 | -26.2 | 16.9 | -0.23 / -0.72 / -0.75 | 24.0 / 7.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00); CL: 8 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.01, p(top) = 0.52); ES: 10 cells pass the clean rule against a replicate mean of 3.6 (p(count) = 0.00, p(top) = 0.49); GC: 2 cells pass the clean rule against a replicate mean of 3.5 (p(count) = 0.88, p(top) = 0.74); HO: 0 cells pass the clean rule against a replicate mean of 6.3 (p(count) = 1.00); NQ: 10 cells pass the clean rule against a replicate mean of 6.2 (p(count) = 0.10, p(top) = 0.59); RTY: 10 cells pass the clean rule against a replicate mean of 4.0 (p(count) = 0.00, p(top) = 0.10); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 40 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.20 (CL lon (0, 0.3, 120, -1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 14; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell CL lon (0, 0.3, 120, -1): uplift +0.12/+0.21/+0.46, boot lo -0.00, plateau 0.00, 2x-slip +0.15, wd corr -0.18, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 18, 'negative pre-2023': 14, 'positive pre-2023': 8}.

- **Manual review of the one gate-3 cell: CL London-to-New-York reversal.** When the London-session return (03:00 ET to 08:25 ET) is at least 0.3 x ADR20, trade AGAINST it at the 09:00 ET NYMEX open (signal at 08:59) and hold 120 minutes, no stop. Standalone Sharpe 0.65 / 0.86 / 1.39 on clean / H1 / H2 (out-of-selection 1.18 against null p95 1.10: passes that sub-gate); uplift at 20% share +0.12 / +0.21 / +0.46 (10%: +0.07/+0.12/+0.27; 30%: +0.15/+0.27/+0.55; 50%: +0.18/+0.32/+0.53); worst week +12.9% at 20% (inside); bootstrap lower bound -0.00 (fails); plateau 0.00; 2x slippage all-in +0.15; worst-decile correlation -0.18; 161 clean trades; ERA flag gross-positive, cost-negative pre-2023 (net -0.24, gross +0.03). Replication: 0 of 4 (H0 2023-02..07 standalone -1.40 on 44 trades; ES -0.04, RTY -0.06; alternating months odd +0.05 / even +0.28 against +0.20). Sizing: 62.9 CL contracts at 100% of pair volatility, 12.6 CL at 20% share; worst single trade -$6.9k per CL contract, about -$87k at 12.6 contracts (no stop). The large contract count comes from CL's modest weekly volatility for this sleeve; at that size slippage of 1 tick ($10) per contract per side is $252 per round trip for the sleeve. Verdict: LEAD (weak): bootstrap, plateau and replication fail.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q29.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q29/ (`Q29_CO_all_selected_scored.csv`).

DONE Q29
