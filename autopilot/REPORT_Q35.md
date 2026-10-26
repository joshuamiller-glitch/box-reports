# REPORT Q35 - Q35: prior-day-level break conditioned on yesterday range state (contraction/expansion)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 22 selected cells (+30 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.16; best pair-window standalone Sharpe +1.02.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: prior-day-level break conditioned on yesterday range state (contraction/expansion).
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      32 |         16 |         0 |               1.397 |                2 |          0 |            3 |
| CL    |      32 |         16 |         0 |               0.337 |                2 |          0 |            3 |
| ES    |      32 |         32 |         3 |               1.31  |                2 |          3 |            3 |
| GC    |      32 |         32 |         6 |               1.114 |                2 |          6 |            3 |
| HG    |      32 |         16 |         0 |               0.96  |                2 |          0 |            3 |
| HO    |      32 |         16 |         4 |               1.04  |                2 |          4 |            3 |
| NQ    |      32 |         32 |         6 |               1.091 |                2 |          6 |            3 |
| RTY   |      32 |         16 |         1 |               1.082 |                2 |          1 |            3 |
| SI    |      32 |         32 |         2 |               0.794 |                2 |          2 |            3 |
| ZN    |      32 |         32 |         0 |              -0.568 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    3 |            3.175 |               8 |      0.63  |                       1.181 |            0.672 |           1.14  |    0.03  |       1.31  |                1.63  |
| NQ    |     200 |                    6 |            5.67  |              11 |      0.515 |                       0.493 |            0.748 |           1.068 |    0.925 |       0.782 |                2.017 |
| RTY   |     200 |                    1 |            3.055 |               8 |      0.98  |                       0.451 |            0.685 |           1.255 |    0.79  |       0.451 |                1.708 |
| GC    |     200 |                    6 |            2.205 |               7 |      0.005 |                       0.676 |            0.636 |           1.071 |    0.355 |       1.114 |                1.451 |
| CL    |     200 |                    0 |            1.345 |               5 |      1     |                     nan     |            0.633 |           1.203 |  nan     |     nan     |                1.457 |
| ZN    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.247 |           0.247 |  nan     |     nan     |                0.247 |
| HO    |     200 |                    4 |            3.68  |               8 |      0.515 |                       0.693 |            0.718 |           1.166 |    0.495 |       1.04  |                1.739 |
| 6E    |     200 |                    0 |            0.545 |               4 |      1     |                     nan     |            0.573 |           1.173 |  nan     |     nan     |                1.203 |
| SI    |     200 |                    2 |            1     |               4 |      0.285 |                       0.78  |            0.598 |           1.166 |    0.165 |       0.794 |                1.44  |
| HG    |     200 |                    0 |            1.255 |               5 |      1     |                     nan     |            0.649 |           1.162 |  nan     |     nan     |                1.287 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | pdstate ('fade', 1, 15, ('tr', 0.2)) | 71 | 2 | 1.31 | -0.81 | 0.67 | -1.30 / 0.93 | 0.21 / -0.22 / -0.24 | 0.02 | -0.36 | 0.95 | -0.07 | 0.00 | 109 | NO |
| ES 2 | pdstate ('fade', 1, 15, ('b1', 0.2)) | 71 | 2 | 1.24 | -0.50 | 0.20 | -0.97 / 1.53 | 0.22 / -1.01 / -0.23 | -0.09 | -0.01 | 0.68 | -0.27 | 0.00 | 109 | NO |
| ES 3 | pdstate ('fade', 1, 5, ('b1', 0.2)) | 74 | 2 | 0.99 | -0.36 | 0.64 | 0.25 / 1.09 | 0.19 / -0.31 / -0.19 | 0.02 | -0.21 | 0.95 | -0.19 | 0.50 | 113 | NO |
| ES 4 (diag) | pdstate ('fade', 1, 5, ('tr', 0.2)) | 74 | 1 | 0.82 | -0.92 | 0.58 | 0.23 / 0.84 | 0.13 / -0.19 / -0.08 | 0.02 | -0.30 | 0.97 | -0.14 | 0.50 | 113 | diag |
| ES 5 (diag) | pdstate ('with', -1, 5, ('tr', 0.2)) | 119 | 1 | 0.45 | -0.12 | 0.02 | -1.01 / 0.93 | -0.01 / -0.33 / -0.05 | -0.12 | 0.36 | 0.76 | -0.21 | 0.00 | 185 | diag |
| ES 6 (diag) | pdstate ('fade', -1, 15, ('b1', 0.2)) | 117 | 1 | 0.20 | -0.72 | 0.26 | 0.30 / 1.40 | 0.09 / -0.01 / 0.15 | 0.07 | -0.29 | 0.77 | -0.09 | 0.00 | 179 | diag |
| NQ 1 | pdstate ('fade', -1, 15, ('tr', 0.2)) | 118 | 2 | 0.78 | -0.14 | 0.39 | -0.48 / 1.49 | 0.18 / -0.20 / -0.13 | 0.06 | 0.28 | 0.82 | -0.09 | 0.50 | 176 | NO |
| NQ 2 | pdstate ('fade', -1, 15, ('b1', 0.2)) | 118 | 2 | 0.71 | -0.54 | 0.36 | -0.25 / 1.42 | 0.22 / 0.04 / -0.13 | 0.12 | 0.20 | 0.74 | -0.06 | 0.50 | 176 | NO |
| NQ 3 | pdstate ('with', -1, 5, ('tr', 0.2)) | 124 | 2 | 0.61 | 0.90 | 0.10 | -1.41 / 1.19 | 0.02 / -0.28 / -0.13 | -0.07 | -0.04 | 0.70 | -0.19 | 0.00 | 182 | NO |
| NQ 4 | pdstate ('fade', 1, 15, ('tr', 0.2)) | 61 | 2 | 0.42 | -0.48 | 0.57 | 0.80 / 1.09 | 0.03 / -0.16 / 0.26 | 0.07 | -0.07 | 0.88 | -0.16 | 0.50 | 107 | NO |
| NQ 5 | pdstate ('fade', 1, 5, ('b1', 0.2)) | 63 | 2 | 0.26 | -0.18 | -0.02 | -0.22 / 1.67 | 0.04 / -0.50 / 0.03 | -0.04 | -0.43 | 0.47 | -0.29 | 0.00 | 111 | NO |
| NQ 6 | pdstate ('fade', 1, 15, ('b1', 0.2)) | 61 | 2 | 0.17 | -0.38 | 0.11 | 0.13 / 1.24 | 0.01 / -0.29 / 0.02 | -0.02 | -0.11 | 0.55 | -0.28 | 0.00 | 107 | NO |
| NQ 7 (diag) | pdstate ('with', -1, 5, ('tr', 0.1)) | 124 | 1 | 1.09 | 0.52 | 0.60 | -0.01 / 1.18 | 0.16 / -0.33 / 0.21 | 0.08 | 0.24 | 0.95 | -0.10 | 0.00 | 182 | diag |
| NQ 8 (diag) | pdstate ('with', 1, 5, ('b1', 0.1)) | 63 | 1 | 1.00 | -0.52 | 0.57 | -0.02 / 1.63 | 0.15 / 0.25 / -0.37 | 0.03 | -0.02 | 0.87 | -0.15 | 0.00 | 111 | diag |
| NQ 9 (diag) | pdstate ('with', -1, 5, ('b1', 0.1)) | 124 | 1 | 0.62 | 0.02 | 0.87 | 1.33 / 1.71 | 0.06 / -0.29 / 0.60 | 0.11 | -0.05 | 0.94 | -0.08 | 0.00 | 182 | diag |
| RTY 1 | pdstate ('with', -1, 15, ('b1', 0.1)) | 108 | 2 | 0.45 | -0.56 | -0.45 | -1.65 / 1.29 | 0.05 / -0.52 / -0.46 | -0.19 | 0.25 | 0.42 | -0.35 | 0.00 | 166 | NO |
| RTY 2 (diag) | pdstate ('with', 1, 5, ('tr', 0.2)) | 59 | 2 | 1.08 | -0.18 | 0.82 | 0.43 / 0.96 | 0.14 / 0.07 / -0.01 | 0.07 | 0.34 | 0.98 | -0.06 | 1.00 | 102 | diag |
| RTY 3 (diag) | pdstate ('with', 1, 5, ('b1', 0.2)) | 59 | 1 | 0.88 | 0.02 | 1.02 | 1.34 / 1.27 | 0.11 / 0.64 / 0.18 | 0.16 | 0.25 | 0.98 | -0.03 | 0.50 | 102 | diag |
| RTY 4 (diag) | pdstate ('with', 1, 5, ('tr', 0.1)) | 59 | 1 | 0.62 | -0.23 | 0.99 | 1.49 / 0.90 | 0.08 / 0.12 / 0.56 | 0.14 | 0.32 | 1.00 | -0.00 | 0.50 | 102 | diag |
| GC 1 | pdstate ('with', 1, 5, ('tr', 0.1)) | 62 | 2 | 1.11 | -0.77 | -0.25 | -1.34 / 0.93 | 0.10 / -0.29 / -1.10 | -0.27 | 0.23 | 0.48 | -0.49 | 0.00 | 108 | NO |
| GC 2 | pdstate ('with', 1, 5, ('b1', 0.1)) | 62 | 2 | 0.98 | -0.84 | 0.74 | 0.84 / 1.59 | 0.15 / -0.45 / 0.15 | 0.06 | 0.40 | 0.87 | -0.23 | 0.00 | 108 | NO |
| GC 3 | pdstate ('with', 1, 5, ('b1', 0.2)) | 62 | 2 | 0.66 | -0.84 | 0.69 | 0.85 / 1.58 | 0.07 / 0.97 / -0.36 | 0.10 | 0.05 | 0.89 | -0.23 | 0.00 | 108 | NO |
| GC 4 | pdstate ('with', 1, 5, ('tr', 0.2)) | 62 | 2 | 0.59 | -1.02 | 0.23 | 0.13 / 1.14 | 0.01 / -0.42 / -0.26 | -0.13 | -0.12 | 0.68 | -0.47 | 0.00 | 108 | NO |
| GC 5 | pdstate ('fade', -1, 5, ('b1', 0.2)) | 98 | 2 | 0.39 | -0.70 | -0.14 | -0.44 / 1.60 | 0.03 / 0.17 / -1.08 | -0.21 | 0.15 | 0.53 | -0.49 | 0.00 | 161 | NO |
| GC 6 | pdstate ('with', -1, 5, ('tr', 0.1)) | 98 | 2 | 0.32 | 0.11 | 0.83 | 1.29 / 0.98 | 0.07 / -0.63 / 0.77 | 0.10 | -0.59 | 1.00 | -0.12 | 0.50 | 161 | NO |
| GC 7 (diag) | pdstate ('fade', 1, 15, ('tr', 0.2)) | 60 | 1 | 0.67 | -0.45 | -0.24 | -0.82 / 1.12 | 0.09 / -1.39 / -0.42 | -0.26 | -0.07 | 0.44 | -0.57 | 0.00 | 104 | diag |
| GC 8 (diag) | pdstate ('with', -1, 15, ('b1', 0.1)) | 93 | 1 | 0.20 | -0.40 | 0.32 | 0.40 / 1.56 | 0.05 / -0.30 / 0.10 | -0.01 | 0.05 | 0.76 | -0.28 | 0.00 | 154 | diag |
| GC 9 (diag) | pdstate ('fade', -1, 5, ('b1', 0.1)) | 98 | 1 | 0.06 | -1.58 | 0.10 | 0.20 / 1.54 | -0.05 / 0.21 / -0.15 | -0.09 | 0.24 | 0.70 | -0.28 | 0.00 | 161 | diag |
| CL 1 (diag) | pdstate ('with', 1, 15, ('b1', 0.2)) | 48 | 2 | 0.34 | -0.18 | -0.56 | -1.65 / 1.30 | 0.04 / -0.35 / -0.83 | -0.25 | 0.19 | 0.31 | -0.45 | 0.00 | 80 S | diag |
| CL 2 (diag) | pdstate ('with', -1, 5, ('b1', 0.2)) | 89 | 1 | 0.17 | 0.15 | 0.11 | 0.07 / 1.29 | 0.02 / 0.28 / -0.45 | -0.09 | -0.18 | 0.71 | -0.31 | 0.00 | 150 | diag |
| CL 3 (diag) | pdstate ('fade', 1, 15, ('b1', 0.1)) | 48 | 1 | 0.12 | -0.33 | 0.38 | 0.75 / 1.05 | -0.01 / 0.44 / 0.12 | 0.02 | -0.12 | 0.90 | -0.19 | 0.50 | 80 S | diag |
| ZN 1 (diag) | pdstate ('with', 1, 5, ('tr', 0.1)) | 63 | 0 | -0.57 | -2.52 | -1.08 | -4.07 / -1.94 | -0.16 / -0.38 / -0.24 | -0.40 | 0.31 | 1.00 | -0.33 | 0.00 | 95 S | diag |
| ZN 2 (diag) | pdstate ('with', 1, 5, ('b1', 0.2)) | 63 | 0 | -0.61 | -0.97 | -0.97 | -1.68 / -0.15 | -0.11 / -0.03 / -0.37 | -0.34 | 0.36 | 0.82 | -0.35 | 0.00 | 95 S | diag |
| ZN 3 (diag) | pdstate ('with', 1, 15, ('b1', 0.2)) | 62 | 0 | -0.82 | -0.25 | -0.90 | -1.05 / -0.00 | -0.19 / -0.13 / -0.09 | -0.36 | 0.49 | 0.86 | -0.36 | 0.00 | 93 S | diag |
| HO 1 | pdstate ('fade', -1, 15, ('tr', 0.2)) | 89 | 2 | 1.04 | -0.30 | 0.29 | 0.08 / 1.15 | 0.16 / 0.09 / -0.22 | 0.03 | -0.29 | 0.77 | -0.38 | 0.00 | 146 | NO |
| HO 2 | pdstate ('fade', -1, 15, ('b1', 0.1)) | 89 | 2 | 0.93 | -0.13 | -0.41 | -1.19 / 1.72 | 0.20 / -0.58 / -1.18 | -0.25 | -0.09 | 0.34 | -0.62 | 0.00 | 146 | NO |
| HO 3 | pdstate ('fade', -1, 5, ('b1', 0.2)) | 90 | 2 | 0.47 | -0.27 | -0.28 | -0.73 / 1.09 | 0.08 / -0.13 / -0.73 | -0.16 | -0.36 | 0.43 | -0.54 | 0.00 | 147 | NO |
| HO 4 | pdstate ('fade', -1, 5, ('tr', 0.2)) | 90 | 2 | 0.33 | -0.23 | 0.20 | 0.17 / 1.16 | 0.04 / 0.01 / -0.03 | -0.01 | -0.31 | 0.69 | -0.41 | 0.00 | 147 | NO |
| HO 5 (diag) | pdstate ('fade', -1, 15, ('b1', 0.2)) | 89 | 1 | 0.66 | -0.16 | -0.69 | -1.56 / 1.06 | 0.12 / -0.12 / -1.65 | -0.32 | -0.40 | 0.11 | -0.72 | 0.00 | 146 | diag |
| HO 6 (diag) | pdstate ('fade', -1, 5, ('b1', 0.1)) | 90 | 1 | 0.56 | -0.41 | -0.44 | -1.21 / 1.27 | 0.11 / -0.45 / -0.62 | -0.17 | -0.40 | 0.38 | -0.44 | 0.00 | 147 | diag |
| HO 7 (diag) | pdstate ('with', 1, 5, ('b1', 0.1)) | 57 | 2 | 0.54 | -0.26 | 0.19 | -0.21 / 1.44 | 0.11 / 0.04 / -0.32 | -0.01 | -0.06 | 0.62 | -0.22 | 0.50 | 94 S | diag |
| 6E 1 (diag) | pdstate ('with', 1, 15, ('b1', 0.2)) | 50 | 2 | 1.40 | -1.28 | 0.63 | -0.84 / 1.18 | 0.24 / 0.21 / -0.36 | 0.05 | 0.12 | 0.96 | -0.06 | 0.50 | 75 S | diag |
| 6E 2 (diag) | pdstate ('with', 1, 15, ('tr', 0.1)) | 50 | 2 | 0.84 | -1.10 | 0.70 | 0.41 / 0.43 | 0.13 / 0.35 / -0.17 | -0.00 | -0.10 | 1.00 | -0.08 | 0.50 | 75 S | diag |
| 6E 3 (diag) | pdstate ('with', 1, 5, ('b1', 0.2)) | 54 | 2 | 0.78 | -1.45 | 0.80 | 1.12 / 1.20 | 0.11 / 0.36 / -0.02 | 0.08 | -0.42 | 0.97 | -0.05 | 0.50 | 80 S | diag |
| SI 1 | pdstate ('fade', -1, 15, ('b1', 0.2)) | 103 | 2 | 0.79 | -0.32 | -0.82 | -1.63 / 1.62 | 0.05 / -1.26 / -2.25 | -0.85 | -0.25 | 0.12 | -1.44 | 0.00 | 165 | NO |
| SI 2 | pdstate ('fade', -1, 15, ('tr', 0.1)) | 103 | 2 | 0.77 | -1.03 | -0.44 | -0.99 / 1.07 | 0.05 / -0.92 / -1.73 | -0.72 | -0.36 | 0.53 | -1.23 | 0.00 | 165 | NO |
| SI 3 (diag) | pdstate ('fade', 1, 15, ('tr', 0.2)) | 60 | 1 | 0.62 | -0.08 | -0.98 | -2.04 / 1.16 | 0.11 / -2.92 / -0.36 | -0.63 | -0.30 | 0.11 | -1.04 | 0.00 | 95 S | diag |
| SI 4 (diag) | pdstate ('fade', 1, 15, ('b1', 0.2)) | 60 | 1 | 0.30 | -0.03 | -0.27 | -0.62 / 1.32 | 0.08 / -1.99 / -0.23 | -0.43 | -0.47 | 0.45 | -0.98 | 0.00 | 95 S | diag |
| SI 5 (diag) | pdstate ('fade', -1, 15, ('tr', 0.2)) | 103 | 1 | 0.29 | -0.17 | -0.97 | -1.72 / 1.02 | -0.05 / -1.17 / -2.32 | -0.94 | -0.46 | 0.10 | -1.48 | 0.00 | 165 | diag |
| HG 1 (diag) | pdstate ('with', 1, 15, ('b1', 0.2)) | 46 | 2 | 0.96 | -0.64 | 0.84 | 1.16 / 0.99 | 0.09 / -0.07 / 0.26 | 0.09 | 0.54 | 0.97 | -0.10 | 1.00 | 74 S | diag |
| HG 2 (diag) | pdstate ('with', 1, 15, ('tr', 0.2)) | 46 | 2 | 0.94 | -0.45 | 0.93 | 0.96 / 1.14 | 0.14 / 0.03 / 0.07 | 0.08 | 0.23 | 0.99 | -0.03 | 0.00 | 74 S | diag |
| HG 3 (diag) | pdstate ('with', 1, 5, ('tr', 0.2)) | 47 | 2 | 0.88 | -0.36 | 0.69 | 0.84 / 1.08 | 0.12 / -0.49 / 0.07 | -0.01 | 0.24 | 0.94 | -0.18 | 0.50 | 76 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 22 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 14 |
| worst-decile corr <= +0.30 | 44 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 14 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | clean | 0.64 | 1.02 | -122202 | -111060 | 302958 | -125938 | 1.94 | 14.3 | 1.57 | -80664 | 244589 | -93445 |
| 6E pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | H1 | 2.06 | 5.47 | -77171 | -59249 | 100828 | -77424 | 4.45 | 14.3 | 3.18 | -79950 | 141852 | -81613 |
| 6E pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | H2 | 0.31 | 0.40 | -137312 | -108119 | 282193 | -180765 | 0.27 | 11.1 | 2.47 | -87786 | 217425 | -95919 |
| 6E pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | all | 0.80 | 1.29 | -124640 | -107764 | 302958 | -180765 | 3.68 | 13.7 | 2.02 | -82461 | 244589 | -95919 |
| CL pdstate ('fade', 1, 15, ('b1', 0.1)) (diag) | clean | 0.03 | 0.04 | -136289 | -116983 | 426658 | -182545 | 0.06 | 18.1 | 1.45 | -80827 | 295845 | -97033 |
| CL pdstate ('fade', 1, 15, ('b1', 0.1)) (diag) | H1 | 3.05 | 7.31 | -43413 | -28942 | 135989 | -86826 | 3.42 | 3.6 | 3.27 | -65426 | 151713 | -76932 |
| CL pdstate ('fade', 1, 15, ('b1', 0.1)) (diag) | H2 | 0.36 | 0.51 | -356834 | -279551 | 698465 | -357334 | 0.36 | 13.9 | 2.60 | -79836 | 194116 | -82524 |
| CL pdstate ('fade', 1, 15, ('b1', 0.1)) (diag) | all | 0.38 | 0.55 | -203396 | -152358 | 698465 | -357334 | 1.07 | 14.9 | 1.98 | -80199 | 295845 | -97033 |
| ES pdstate ('fade', 1, 5, ('b1', 0.2)) | clean | 1.06 | 1.80 | -125353 | -102974 | 506446 | -193319 | 1.90 | 18.1 | 1.65 | -83060 | 228968 | -93103 |
| ES pdstate ('fade', 1, 5, ('b1', 0.2)) | H1 | 0.27 | 0.40 | -171334 | -148688 | 347016 | -230964 | 0.26 | 21.4 | 2.51 | -88763 | 187885 | -100628 |
| ES pdstate ('fade', 1, 5, ('b1', 0.2)) | H2 | 0.25 | 0.34 | -273583 | -237934 | 633875 | -279865 | 0.23 | 16.7 | 2.29 | -108117 | 217425 | -115262 |
| ES pdstate ('fade', 1, 5, ('b1', 0.2)) | all | 0.64 | 0.96 | -198008 | -150055 | 959588 | -279865 | 1.25 | 18.5 | 1.95 | -91159 | 256478 | -115262 |
| GC pdstate ('with', -1, 5, ('tr', 0.1)) | clean | 0.35 | 0.63 | -112124 | -91046 | 423644 | -157674 | 0.75 | 36.2 | 1.53 | -80188 | 272359 | -84142 |
| GC pdstate ('with', -1, 5, ('tr', 0.1)) | H1 | -1.41 | -1.88 | -180303 | -162118 | 849107 | -187708 | -0.55 | 28.6 | 2.20 | -77610 | 207436 | -78287 |
| GC pdstate ('with', -1, 5, ('tr', 0.1)) | H2 | 2.37 | 5.71 | -264177 | -203842 | 661796 | -265445 | 3.49 | 25.0 | 3.26 | -85191 | 246767 | -89938 |
| GC pdstate ('with', -1, 5, ('tr', 0.1)) | all | 0.83 | 1.74 | -179236 | -144788 | 849107 | -265445 | 2.54 | 32.7 | 2.06 | -81116 | 272359 | -89938 |
| HG pdstate ('with', 1, 15, ('b1', 0.2)) (diag) | clean | 0.58 | 0.88 | -168928 | -120519 | 605967 | -285138 | 0.96 | 11.4 | 1.55 | -83615 | 309678 | -111151 |
| HG pdstate ('with', 1, 15, ('b1', 0.2)) (diag) | H1 | 0.27 | 0.40 | -196320 | -173002 | 384426 | -253120 | 0.26 | 17.9 | 2.76 | -77648 | 175421 | -78287 |
| HG pdstate ('with', 1, 15, ('b1', 0.2)) (diag) | H2 | 1.83 | 3.12 | -230931 | -119054 | 308963 | -298892 | 2.86 | 8.3 | 2.75 | -85712 | 250019 | -88899 |
| HG pdstate ('with', 1, 15, ('b1', 0.2)) (diag) | all | 0.84 | 1.29 | -194194 | -146826 | 725961 | -298892 | 2.16 | 11.9 | 2.02 | -83749 | 309678 | -111151 |
| HO pdstate ('fade', -1, 15, ('tr', 0.2)) | clean | 1.15 | 2.27 | -98172 | -84651 | 466318 | -177143 | 2.27 | 28.6 | 1.62 | -85564 | 302280 | -92567 |
| HO pdstate ('fade', -1, 15, ('tr', 0.2)) | H1 | -0.33 | -0.53 | -87617 | -79620 | 229879 | -93347 | -0.28 | 35.7 | 2.92 | -61127 | 142137 | -76932 |
| HO pdstate ('fade', -1, 15, ('tr', 0.2)) | H2 | 0.14 | 0.27 | -710757 | -512981 | 2578603 | -799645 | 0.10 | 47.2 | 2.27 | -104734 | 286066 | -106525 |
| HO pdstate ('fade', -1, 15, ('tr', 0.2)) | all | 0.29 | 0.56 | -328680 | -222643 | 2578603 | -799645 | 0.49 | 33.3 | 1.95 | -91300 | 302280 | -106525 |
| NQ pdstate ('fade', -1, 15, ('b1', 0.2)) | clean | 0.77 | 1.23 | -128967 | -95478 | 537873 | -224762 | 1.30 | 36.2 | 1.68 | -80799 | 249319 | -84896 |
| NQ pdstate ('fade', -1, 15, ('b1', 0.2)) | H1 | 0.55 | 1.02 | -82055 | -78905 | 170412 | -86052 | 0.69 | 21.4 | 2.87 | -82850 | 137633 | -88768 |
| NQ pdstate ('fade', -1, 15, ('b1', 0.2)) | H2 | -0.70 | -0.96 | -169890 | -136008 | 645256 | -180259 | -0.42 | 41.7 | 2.36 | -91554 | 198656 | -93613 |
| NQ pdstate ('fade', -1, 15, ('b1', 0.2)) | all | 0.36 | 0.56 | -139321 | -107967 | 660464 | -224762 | 0.83 | 35.1 | 2.03 | -85331 | 249319 | -93613 |
| RTY pdstate ('with', -1, 15, ('b1', 0.1)) | clean | 0.45 | 0.67 | -138957 | -106119 | 375818 | -216753 | 1.08 | 30.5 | 1.51 | -86598 | 312795 | -111282 |
| RTY pdstate ('with', -1, 15, ('b1', 0.1)) | H1 | -2.64 | -2.83 | -123402 | -107300 | 762150 | -138800 | -0.69 | 42.9 | 2.31 | -77610 | 181897 | -78287 |
| RTY pdstate ('with', -1, 15, ('b1', 0.1)) | H2 | -1.30 | -1.53 | -231817 | -199138 | 765323 | -292216 | -0.79 | 36.1 | 2.03 | -95157 | 248065 | -100964 |
| RTY pdstate ('with', -1, 15, ('b1', 0.1)) | all | -0.45 | -0.58 | -176849 | -136865 | 1467014 | -292216 | -0.49 | 33.9 | 1.75 | -88077 | 312795 | -111282 |
| SI pdstate ('fade', -1, 15, ('tr', 0.1)) | clean | 0.74 | 1.66 | -76446 | -66180 | 355786 | -99123 | 1.89 | 41.0 | 1.51 | -89323 | 308685 | -96676 |
| SI pdstate ('fade', -1, 15, ('tr', 0.1)) | H1 | -2.83 | -2.68 | -228618 | -187508 | 808569 | -338155 | -0.96 | 28.6 | 1.91 | -111425 | 205264 | -144563 |
| SI pdstate ('fade', -1, 15, ('tr', 0.1)) | H2 | -0.95 | -1.09 | -1237404 | -931168 | 3982181 | -1762533 | -0.49 | 38.9 | 0.76 | -253147 | 696627 | -361001 |
| SI pdstate ('fade', -1, 15, ('tr', 0.1)) | all | -0.44 | -0.52 | -556798 | -340485 | 4860399 | -1762533 | -0.43 | 38.7 | 1.29 | -144868 | 881594 | -361001 |
| ZN pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | clean | -0.61 | -0.74 | -150302 | -132663 | 1225287 | -219229 | -0.45 | 19.0 | 1.35 | -86536 | 318809 | -110599 |
| ZN pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | H1 | -0.41 | -0.51 | -90259 | -87697 | 248973 | -94722 | -0.26 | 17.9 | 2.80 | -73910 | 152620 | -78287 |
| ZN pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | H2 | -2.44 | -2.52 | -150362 | -127381 | 739176 | -184605 | -0.94 | 30.6 | 2.11 | -81089 | 207402 | -82524 |
| ZN pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | all | -0.97 | -1.13 | -146469 | -128430 | 1952029 | -219229 | -0.67 | 21.4 | 1.74 | -84409 | 318809 | -110599 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES pdstate ('fade', 1, 5, ('b1', 0.2)) | -16.9 | -32.3 | -2.1 | 2.3 | 4.9 / 19.9 | -12.8 / -13.4 | NO |
| NQ pdstate ('fade', -1, 15, ('b1', 0.2)) | -24.0 | 7.1 | 17.5 | 31.1 | 20.2 / 23.3 | 9.9 / 19.9 | NO |
| RTY pdstate ('with', -1, 15, ('b1', 0.1)) | -37.9 | -27.6 | 10.5 | 10.3 | -28.6 / 14.9 | 30.0 / 30.0 | NO |
| GC pdstate ('with', -1, 5, ('tr', 0.1)) | -6.4 | 1.2 | 16.0 | 20.8 | 21.1 / 25.7 | 30.0 / 30.0 | NO |
| CL pdstate ('fade', 1, 15, ('b1', 0.1)) (diag) | -21.8 | -21.1 | 15.4 | 21.4 | 2.2 / 22.4 | 31.2 / 45.9 | NO |
| ZN pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | -44.4 | -21.7 | 17.0 | 9.3 | -22.6 / 14.6 | 30.0 / 37.2 | NO |
| HO pdstate ('fade', -1, 15, ('tr', 0.2)) | -16.2 | -53.7 | -18.7 | -106.8 | 5.6 / 16.7 | 31.2 / 46.0 | NO |
| 6E pdstate ('with', 1, 5, ('b1', 0.2)) (diag) | -17.8 | 0.4 | 21.4 | 24.0 | 4.3 / 25.2 | 22.2 / 25.5 | NO |
| SI pdstate ('fade', -1, 15, ('tr', 0.1)) | -52.6 | -547.9 | -132.1 | -352.4 | 2.9 / 9.3 | -98.4 / -35.4 | NO |
| HG pdstate ('with', 1, 15, ('b1', 0.2)) (diag) | -12.9 | -22.7 | 8.5 | 6.9 | -23.6 / 15.4 | -20.6 / -2.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 pdstate ('fade', 1, 15, ('tr', 0.2)) | negative pre-2023 | 326 | -24.3 | -53.7 | -39.8 | 29.4 | -0.37 / -0.81 / -0.61 | 298.8 / 269.4 |
| ES 2 pdstate ('fade', 1, 15, ('b1', 0.2)) | negative pre-2023 | 326 | -16.8 | -40.5 | -29.3 | 23.7 | -0.21 / -0.50 / -0.37 | 128.9 / 106.6 |
| ES 3 pdstate ('fade', 1, 5, ('b1', 0.2)) | negative pre-2023 | 347 | -3.8 | -27.1 | -16.0 | 23.3 | -0.05 / -0.36 / -0.21 | 119.1 / 97.2 |
| ES 4 (diag) pdstate ('fade', 1, 5, ('tr', 0.2)) | negative pre-2023 | 347 | -32.9 | -62.2 | -48.2 | 29.4 | -0.50 / -0.92 / -0.72 | 146.3 / 116.9 |
| ES 5 (diag) pdstate ('with', -1, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 599 | 21.4 | -8.0 | 6.0 | 29.4 | 0.32 / -0.12 / 0.09 | 88.2 / 58.9 |
| ES 6 (diag) pdstate ('fade', -1, 15, ('b1', 0.2)) | negative pre-2023 | 575 | -23.5 | -47.5 | -36.1 | 24.0 | -0.36 / -0.72 / -0.55 | 47.2 / 24.1 |
| NQ 1 pdstate ('fade', -1, 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 561 | 2.0 | -12.4 | -3.7 | 14.4 | 0.02 / -0.14 / -0.04 | 244.3 / 229.9 |
| NQ 2 pdstate ('fade', -1, 15, ('b1', 0.2)) | negative pre-2023 | 561 | -35.0 | -47.1 | -39.8 | 12.1 | -0.40 / -0.54 / -0.46 | 189.4 / 177.6 |
| NQ 3 pdstate ('with', -1, 5, ('tr', 0.2)) | positive pre-2023 | 581 | 110.2 | 95.8 | 104.5 | 14.4 | 1.03 / 0.90 / 0.98 | 173.4 / 159.1 |
| NQ 4 pdstate ('fade', 1, 15, ('tr', 0.2)) | negative pre-2023 | 334 | -33.3 | -47.7 | -39.1 | 14.4 | -0.34 / -0.48 / -0.39 | 104.1 / 89.7 |
| NQ 5 pdstate ('fade', 1, 5, ('b1', 0.2)) | negative pre-2023 | 356 | -8.5 | -20.5 | -13.4 | 12.0 | -0.07 / -0.18 / -0.12 | 58.4 / 46.5 |
| NQ 6 pdstate ('fade', 1, 15, ('b1', 0.2)) | negative pre-2023 | 334 | -35.6 | -47.7 | -40.5 | 12.1 | -0.28 / -0.38 / -0.32 | 34.9 / 22.8 |
| NQ 7 (diag) pdstate ('with', -1, 5, ('tr', 0.1)) | positive pre-2023 | 581 | 45.2 | 30.9 | 39.6 | 14.4 | 0.76 / 0.52 / 0.66 | 112.3 / 97.9 |
| NQ 8 (diag) pdstate ('with', 1, 5, ('b1', 0.1)) | negative pre-2023 | 356 | -18.4 | -30.4 | -23.2 | 12.0 | -0.32 / -0.52 / -0.40 | 127.7 / 116.2 |
| NQ 9 (diag) pdstate ('with', -1, 5, ('b1', 0.1)) | positive pre-2023 | 581 | 13.1 | 1.3 | 8.5 | 11.8 | 0.25 / 0.02 / 0.16 | 61.7 / 49.9 |
| RTY 1 pdstate ('with', -1, 15, ('b1', 0.1)) | negative pre-2023 | 294 | -4.1 | -16.1 | -14.2 | 12.0 | -0.15 / -0.56 / -0.50 | 25.7 / 14.1 |
| RTY 2 (diag) pdstate ('with', 1, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 181 | 2.4 | -12.0 | -9.8 | 14.4 | 0.04 / -0.18 / -0.15 | 107.2 / 92.8 |
| RTY 3 (diag) pdstate ('with', 1, 5, ('b1', 0.2)) | positive pre-2023 | 181 | 13.6 | 1.8 | 3.7 | 11.8 | 0.19 / 0.02 / 0.05 | 64.2 / 52.7 |
| RTY 4 (diag) pdstate ('with', 1, 5, ('tr', 0.1)) | gross-positive, cost-negative pre-2023 | 181 | 4.2 | -10.2 | -8.0 | 14.4 | 0.09 / -0.23 / -0.18 | 41.0 / 26.7 |
| GC 1 pdstate ('with', 1, 5, ('tr', 0.1)) | negative pre-2023 | 251 | -12.6 | -37.0 | -27.3 | 24.4 | -0.26 / -0.77 / -0.57 | 106.0 / 81.7 |
| GC 2 pdstate ('with', 1, 5, ('b1', 0.1)) | negative pre-2023 | 251 | -18.1 | -37.8 | -29.9 | 19.8 | -0.41 / -0.84 / -0.67 | 80.5 / 62.4 |
| GC 3 pdstate ('with', 1, 5, ('b1', 0.2)) | negative pre-2023 | 251 | -53.7 | -73.9 | -65.9 | 20.3 | -0.62 / -0.84 / -0.75 | 102.9 / 84.5 |
| GC 4 pdstate ('with', 1, 5, ('tr', 0.2)) | negative pre-2023 | 251 | -56.1 | -80.4 | -70.7 | 24.4 | -0.72 / -1.02 / -0.90 | 87.0 / 62.7 |
| GC 5 pdstate ('fade', -1, 5, ('b1', 0.2)) | negative pre-2023 | 586 | -22.6 | -42.4 | -34.5 | 19.8 | -0.38 / -0.70 / -0.57 | 52.2 / 32.7 |
| GC 6 pdstate ('with', -1, 5, ('tr', 0.1)) | positive pre-2023 | 586 | 28.1 | 3.7 | 13.4 | 24.4 | 0.83 / 0.11 / 0.40 | 47.4 / 23.1 |
| GC 7 (diag) pdstate ('fade', 1, 15, ('tr', 0.2)) | negative pre-2023 | 231 | -15.5 | -39.9 | -30.1 | 24.4 | -0.18 / -0.45 / -0.34 | 104.4 / 80.1 |
| GC 8 (diag) pdstate ('with', -1, 15, ('b1', 0.1)) | gross-positive, cost-negative pre-2023 | 564 | 6.2 | -13.1 | -5.4 | 19.3 | 0.19 / -0.40 / -0.17 | 35.9 / 17.0 |
| GC 9 (diag) pdstate ('fade', -1, 5, ('b1', 0.1)) | negative pre-2023 | 586 | -30.8 | -50.8 | -42.8 | 20.1 | -0.98 / -1.58 / -1.34 | 18.5 / -0.8 |
| CL 1 (diag) pdstate ('with', 1, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 254 | 3.2 | -16.2 | -14.3 | 19.4 | 0.04 / -0.18 / -0.16 | 57.5 / 38.8 |
| CL 2 (diag) pdstate ('with', -1, 5, ('b1', 0.2)) | positive pre-2023 | 512 | 28.9 | 9.5 | 12.3 | 19.4 | 0.47 / 0.15 / 0.20 | 30.2 / 10.7 |
| CL 3 (diag) pdstate ('fade', 1, 15, ('b1', 0.1)) | gross-positive, cost-negative pre-2023 | 254 | 4.5 | -14.7 | -12.8 | 19.2 | 0.10 / -0.33 / -0.28 | 20.3 / 1.4 |
| ZN 1 (diag) pdstate ('with', 1, 5, ('tr', 0.1)) | gross-positive, cost-negative pre-2023 | 294 | 0.2 | -35.4 | -40.6 | 35.6 | 0.01 / -2.52 / -2.79 | 20.3 / -15.3 |
| ZN 2 (diag) pdstate ('with', 1, 5, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 297 | 4.6 | -23.0 | -27.0 | 27.6 | 0.21 / -0.97 / -1.12 | 14.7 / -12.8 |
| ZN 3 (diag) pdstate ('with', 1, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 270 | 20.5 | -6.3 | -10.2 | 26.8 | 0.83 / -0.25 / -0.40 | 11.7 / -16.0 |
| HO 1 pdstate ('fade', -1, 15, ('tr', 0.2)) | negative pre-2023 | 517 | -16.2 | -29.0 | -27.4 | 12.8 | -0.17 / -0.30 / -0.28 | 100.9 / 88.1 |
| HO 2 pdstate ('fade', -1, 15, ('b1', 0.1)) | gross-positive, cost-negative pre-2023 | 517 | 3.7 | -7.0 | -5.6 | 10.6 | 0.07 / -0.13 / -0.10 | 56.1 / 45.9 |
| HO 3 pdstate ('fade', -1, 5, ('b1', 0.2)) | negative pre-2023 | 526 | -16.8 | -27.5 | -26.2 | 10.6 | -0.17 / -0.27 / -0.26 | 54.3 / 43.8 |
| HO 4 pdstate ('fade', -1, 5, ('tr', 0.2)) | negative pre-2023 | 526 | -7.4 | -20.2 | -18.6 | 12.8 | -0.09 / -0.23 / -0.21 | 49.1 / 36.4 |
| HO 5 (diag) pdstate ('fade', -1, 15, ('b1', 0.2)) | negative pre-2023 | 517 | -5.1 | -15.8 | -14.4 | 10.7 | -0.05 / -0.16 / -0.14 | 71.9 / 61.5 |
| HO 6 (diag) pdstate ('fade', -1, 5, ('b1', 0.1)) | negative pre-2023 | 526 | -8.7 | -19.2 | -18.0 | 10.6 | -0.18 / -0.41 / -0.38 | 40.2 / 29.9 |
| HO 7 (diag) pdstate ('with', 1, 5, ('b1', 0.1)) | negative pre-2023 | 293 | -2.2 | -12.8 | -11.6 | 10.6 | -0.04 / -0.26 / -0.23 | 40.7 / 30.5 |
| 6E 1 (diag) pdstate ('with', 1, 15, ('b1', 0.2)) | negative pre-2023 | 256 | -43.9 | -58.5 | -59.6 | 14.6 | -0.99 / -1.28 / -1.30 | 53.9 / 40.9 |
| 6E 2 (diag) pdstate ('with', 1, 15, ('tr', 0.1)) | negative pre-2023 | 256 | -9.7 | -26.5 | -27.7 | 16.9 | -0.41 / -1.10 / -1.14 | 37.2 / 20.3 |
| 6E 3 (diag) pdstate ('with', 1, 5, ('b1', 0.2)) | negative pre-2023 | 274 | -47.9 | -62.5 | -63.5 | 14.6 | -1.14 / -1.45 / -1.47 | 34.8 / 21.6 |
| SI 1 pdstate ('fade', -1, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 552 | 17.7 | -24.8 | -10.1 | 42.5 | 0.25 / -0.32 / -0.12 | 135.0 / 93.2 |
| SI 2 pdstate ('fade', -1, 15, ('tr', 0.1)) | gross-positive, cost-negative pre-2023 | 552 | 8.9 | -45.4 | -26.6 | 54.4 | 0.21 / -1.03 / -0.60 | 110.5 / 56.2 |
| SI 3 (diag) pdstate ('fade', 1, 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 230 | 44.1 | -10.2 | 8.4 | 54.4 | 0.33 / -0.08 / 0.06 | 148.9 / 94.5 |
| SI 4 (diag) pdstate ('fade', 1, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 230 | 39.0 | -2.9 | 11.5 | 42.0 | 0.36 / -0.03 / 0.11 | 113.5 / 72.1 |
| SI 5 (diag) pdstate ('fade', -1, 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 552 | 40.5 | -13.8 | 4.9 | 54.4 | 0.52 / -0.17 / 0.07 | 83.7 / 29.3 |
| HG 1 (diag) pdstate ('with', 1, 15, ('b1', 0.2)) | negative pre-2023 | 242 | -18.3 | -42.3 | -35.8 | 24.0 | -0.28 / -0.64 / -0.55 | 79.8 / 57.5 |
| HG 2 (diag) pdstate ('with', 1, 15, ('tr', 0.2)) | negative pre-2023 | 242 | -2.0 | -31.4 | -23.4 | 29.4 | -0.03 / -0.45 / -0.34 | 158.0 / 128.6 |
| HG 3 (diag) pdstate ('with', 1, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 250 | 3.2 | -26.1 | -18.2 | 29.4 | 0.04 / -0.36 / -0.25 | 76.7 / 47.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); ES: 3 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.63, p(top) = 0.03); GC: 6 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.01, p(top) = 0.35); HG: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); HO: 4 cells pass the clean rule against a replicate mean of 3.7 (p(count) = 0.52, p(top) = 0.49); NQ: 6 cells pass the clean rule against a replicate mean of 5.7 (p(count) = 0.52, p(top) = 0.93); RTY: 1 cells pass the clean rule against a replicate mean of 3.1 (p(count) = 0.98, p(top) = 0.79); SI: 2 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.28, p(top) = 0.17); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 22 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.16 (GC pdstate ('with', -1, 5, ('tr', 0.1))); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 16, 'gross-positive, cost-negative pre-2023': 4, 'positive pre-2023': 2}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q35.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q35/ (`Q35_CO_all_selected_scored.csv`).

DONE Q35
