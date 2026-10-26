# REPORT BM11 - BM1 replication probe on all outrights at shifted clocks (BL3)

**Verdict: FOUND-CANDIDATE (needs full verification). FOUND 1, LEAD 1, INSURANCE 0.** 17 selected cells (+83 diagnostic) scored on 28 instruments; best non-diagnostic all-in additive uplift at 20% share +0.29; best pair-window standalone Sharpe +1.47.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see PREREG_AUTOPILOT.md BL3. Fade of the move since the prior RTH close into the instrument close, clocks close-60/-50/-40/-30, x 0.4/0.7.
- Instruments: ES, NQ, RTY, YM, GC, SI, HG, PL, CL, NG, RB, HO, ZN, ZB, ZF, ZT, 6E, 6J, 6B, 6A, 6C, ZC, ZS, ZW, LE, HE, BTC, ETH. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |       8 |          8 |         0 |              -1.177 |                0 |          0 |            3 |
| 6B    |       8 |          8 |         0 |              -1.416 |                0 |          0 |            3 |
| 6C    |       8 |          8 |         0 |              -1.863 |                0 |          0 |            3 |
| 6E    |       8 |          8 |         0 |               0.027 |                1 |          0 |            3 |
| 6J    |       8 |          8 |         0 |              -0.072 |                1 |          0 |            3 |
| BTC   |       8 |          8 |         2 |               1.112 |                2 |          2 |            3 |
| CL    |       8 |          8 |         0 |               0.308 |                1 |          0 |            3 |
| ES    |       8 |          8 |         5 |               1.319 |                2 |          5 |            3 |
| ETH   |       8 |          8 |         0 |               1.17  |                1 |          0 |            3 |
| GC    |       8 |          8 |         0 |              -0.263 |                0 |          0 |            3 |
| HE    |       8 |          8 |         0 |              -0.637 |                1 |          0 |            3 |
| HG    |       8 |          8 |         0 |              -0.389 |                0 |          0 |            3 |
| HO    |       8 |          8 |         0 |               0.202 |                1 |          0 |            3 |
| LE    |       8 |          8 |         0 |              -2.012 |                0 |          0 |            3 |
| NG    |       8 |          8 |         0 |              -1.18  |                0 |          0 |            3 |
| NQ    |       8 |          8 |         6 |               1.803 |                2 |          6 |            2 |
| PL    |       8 |          8 |         0 |               0.215 |                1 |          0 |            3 |
| RB    |       8 |          8 |         0 |               0.224 |                1 |          0 |            3 |
| RTY   |       8 |          8 |         3 |               0.768 |                2 |          3 |            3 |
| SI    |       8 |          8 |         0 |              -1.877 |                0 |          0 |            3 |
| YM    |       8 |          8 |         1 |               0.802 |                2 |          1 |            3 |
| ZB    |       8 |          8 |         0 |              -3.277 |                0 |          0 |            3 |
| ZC    |       8 |          8 |         0 |              -3.229 |                0 |          0 |            3 |
| ZF    |       8 |          8 |         0 |              -2.585 |                0 |          0 |            3 |
| ZN    |       8 |          8 |         0 |              -3.267 |                0 |          0 |            3 |
| ZS    |       8 |          8 |         0 |              -2.764 |                0 |          0 |            3 |
| ZT    |       8 |          8 |         0 |              -2.205 |                0 |          0 |            3 |
| ZW    |       8 |          8 |         0 |              -1.04  |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    5 |            0.865 |               3 |       0    |                       0.658 |            0.689 |           1.366 |    0.305 |       1.319 |                1.412 |
| NQ    |     200 |                    6 |            1.605 |               5 |       0    |                       1.305 |            0.743 |           1.267 |    0.035 |       1.803 |                1.504 |
| RTY   |     200 |                    3 |            0.925 |               4 |       0.05 |                       0.607 |            0.627 |           1.206 |    0.315 |       0.768 |                1.496 |
| YM    |     200 |                    1 |            1.005 |               4 |       0.66 |                       0.802 |            0.701 |           1.238 |    0.22  |       0.802 |                1.4   |
| GC    |     200 |                    0 |            0.585 |               3 |       1    |                     nan     |            0.664 |           1.118 |  nan     |     nan     |                1.263 |
| SI    |     200 |                    0 |            0.04  |               1 |       1    |                     nan     |            0.611 |           1.084 |  nan     |     nan     |                1.084 |
| HG    |     200 |                    0 |            0.155 |               2 |       1    |                     nan     |            0.486 |           1.104 |  nan     |     nan     |                1.17  |
| PL    |     200 |                    0 |            0.215 |               2 |       1    |                     nan     |            0.507 |           1.14  |  nan     |     nan     |                1.305 |
| CL    |     200 |                    0 |            0.49  |               3 |       1    |                     nan     |            0.588 |           1.202 |  nan     |     nan     |                1.338 |
| NG    |     200 |                    0 |            0.22  |               2 |       1    |                     nan     |            0.565 |           1.044 |  nan     |     nan     |                1.044 |
| RB    |     200 |                    0 |            1.085 |               5 |       1    |                     nan     |            0.686 |           1.303 |  nan     |     nan     |                1.401 |
| HO    |     200 |                    0 |            1.125 |               4 |       1    |                     nan     |            0.705 |           1.319 |  nan     |     nan     |                1.407 |
| ZN    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZB    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZF    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZT    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| 6E    |     200 |                    0 |            0.015 |               1 |       1    |                     nan     |            0.367 |           0.46  |  nan     |     nan     |                0.46  |
| 6J    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| 6B    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| 6A    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| 6C    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZC    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| ZS    |     200 |                    0 |            0.01  |               1 |       1    |                     nan     |            0.254 |           0.435 |  nan     |     nan     |                0.435 |
| ZW    |     200 |                    0 |            0.005 |               1 |       1    |                     nan     |            0.31  |           0.31  |  nan     |     nan     |                0.31  |
| LE    |     200 |                    0 |            0.09  |               1 |       1    |                     nan     |            0.427 |           0.764 |  nan     |     nan     |                0.764 |
| HE    |     200 |                    0 |            0.005 |               1 |       1    |                     nan     |            0.173 |           0.173 |  nan     |     nan     |                0.173 |
| BTC   |     200 |                    2 |            1.265 |               4 |       0.34 |                       0.54  |            0.705 |           1.288 |    0.52  |       0.667 |                1.553 |
| ETH   |     200 |                    0 |            0.655 |               3 |       1    |                     nan     |            0.635 |           1.279 |  nan     |     nan     |                1.367 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 131 | 2 | 1.32 | -0.81 | 0.07 | -1.93 / 0.81 | 0.24 / -0.38 / -0.36 | -0.08 | 0.19 | 0.84 | -0.17 | 0.50 | 212 | NO |
| ES 2 | entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 231 | 2 | 0.68 | -1.25 | 0.28 | -0.39 / 0.67 | 0.11 / 0.08 / -0.20 | -0.09 | 0.33 | 0.94 | -0.17 | 0.50 | 392 | NO |
| ES 3 | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 131 | 2 | 0.50 | -0.94 | 0.26 | -0.12 / 1.15 | 0.07 / -0.20 / 0.02 | -0.05 | 0.19 | 0.84 | -0.16 | 0.50 | 207 | NO |
| ES 4 | entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 131 | 2 | 0.43 | -0.68 | 0.17 | -0.34 / 1.17 | 0.07 / 0.03 / -0.07 | -0.04 | 0.15 | 0.80 | -0.15 | 0.00 | 202 | NO |
| ES 5 | entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 230 | 2 | 0.37 | -1.00 | -0.22 | -1.44 / 1.19 | 0.07 / -0.09 / -0.26 | -0.12 | 0.44 | 0.69 | -0.23 | 0.00 | 386 | NO |
| ES 6 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 228 | 1 | 0.14 | -1.21 | -0.06 | -0.39 / 1.04 | 0.01 / 0.15 / -0.19 | -0.13 | 0.66 | 0.70 | -0.22 | 0.00 | 387 | diag |
| ES 7 (diag) | entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 220 | 0 | -0.19 | -1.27 | -0.71 | -1.75 / 1.06 | -0.06 / -0.09 / -0.31 | -0.21 | 0.57 | 0.24 | -0.33 | 0.00 | 376 | diag |
| ES 8 (diag) | entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 122 | 1 | -0.25 | -0.85 | -0.35 | -0.58 / 1.11 | -0.06 / -0.08 / -0.08 | -0.12 | 0.34 | 0.45 | -0.25 | 0.00 | 194 | diag |
| NQ 1 | entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 146 | 2 | 1.80 | -0.78 | 0.59 | -1.01 / 1.45 | 0.28 / -0.35 / -0.23 | 0.04 | 0.29 | 0.90 | -0.14 | 0.50 | 235 | NO |
| NQ 2 | entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 253 | 2 | 1.37 | -1.11 | 0.99 | 0.43 / 1.24 | 0.26 / 0.30 / 0.01 | 0.17 | -0.20 | 0.97 | 0.01 | 1.00 | 415 | NO |
| NQ 3 | entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 243 | 2 | 1.33 | -1.48 | 1.47 | 1.67 / 1.29 | 0.23 / 0.40 / 0.45 | 0.27 | -0.20 | 1.00 | 0.10 | 1.00 | 404 | FOUND-CAND |
| NQ 4 | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 138 | 2 | 1.33 | -1.24 | 0.78 | 0.10 / 1.58 | 0.19 / -0.32 / 0.17 | 0.08 | 0.65 | 0.90 | -0.08 | 1.00 | 227 | NO |
| NQ 5 | entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 137 | 2 | 1.05 | -0.75 | 0.34 | -0.69 / 1.60 | 0.17 / -0.20 / -0.16 | 0.01 | 0.54 | 0.76 | -0.17 | 1.00 | 226 | NO |
| NQ 6 | entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 245 | 2 | 0.95 | -1.11 | 0.74 | 0.39 / 1.47 | 0.16 / 0.10 / 0.09 | 0.11 | -0.17 | 0.90 | -0.06 | 0.50 | 404 | LEAD |
| NQ 7 (diag) | entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 120 | 1 | 0.32 | -1.23 | -0.09 | -0.77 / 1.37 | 0.03 / -0.10 / -0.18 | -0.06 | 0.63 | 0.47 | -0.23 | 0.00 | 205 | diag |
| NQ 8 (diag) | entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 234 | 0 | -0.20 | -1.50 | -0.34 | -0.56 / 1.28 | -0.08 / 0.02 / -0.09 | -0.11 | 0.40 | 0.30 | -0.28 | 0.00 | 396 | diag |
| RTY 1 | entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 249 | 2 | 0.77 | -1.14 | 0.53 | 0.13 / 0.86 | 0.10 / -0.08 / 0.03 | -0.04 | 0.16 | 0.98 | -0.13 | 0.50 | 405 | NO |
| RTY 2 | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 119 | 2 | 0.67 | -0.60 | 0.34 | -0.23 / 1.11 | 0.10 / -0.17 / -0.10 | -0.03 | 0.22 | 0.91 | -0.15 | 0.50 | 195 | NO |
| RTY 3 | entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 244 | 2 | 0.38 | -1.07 | 0.22 | -0.01 / 0.87 | 0.02 / -0.27 / 0.12 | -0.09 | 0.32 | 0.95 | -0.19 | 0.00 | 399 | NO |
| RTY 4 (diag) | entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 122 | 1 | 0.20 | -0.23 | -0.04 | -0.37 / 1.12 | 0.01 / -0.10 / -0.31 | -0.14 | 0.01 | 0.78 | -0.25 | 0.00 | 198 | diag |
| RTY 5 (diag) | entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 114 | 1 | 0.19 | -0.49 | -0.24 | -1.31 / 1.12 | 0.01 / -0.29 / -0.23 | -0.12 | 0.48 | 0.52 | -0.23 | 0.00 | 188 | diag |
| RTY 6 (diag) | entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 118 | 1 | -0.09 | -0.15 | -0.11 | -0.15 / 1.05 | -0.03 / -0.03 / -0.10 | -0.08 | 0.29 | 0.68 | -0.20 | 0.00 | 195 | diag |
| YM 1 | entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 128 | 2 | 0.80 | -0.37 | 0.24 | -1.01 / 1.16 | 0.14 / -0.20 / -0.23 | -0.03 | -0.29 | 0.89 | -0.18 | 0.00 | 208 | NO |
| YM 2 (diag) | entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 245 | 1 | 0.43 | -0.53 | -0.01 | -0.87 / 0.65 | 0.04 / 0.09 / -0.33 | -0.11 | -0.12 | 0.82 | -0.21 | 0.00 | 401 | diag |
| YM 3 (diag) | entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 236 | 1 | -0.03 | -0.28 | 0.01 | -0.00 / 1.02 | -0.03 / 0.11 / -0.05 | -0.07 | 0.24 | 0.75 | -0.20 | 0.00 | 390 | diag |
| YM 4 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 123 | 1 | -0.08 | -0.45 | -0.36 | -0.95 / 1.31 | -0.03 / -0.31 / -0.22 | -0.15 | -0.09 | 0.47 | -0.29 | 0.00 | 200 | diag |
| GC 1 (diag) | entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 | 258 | 0 | -0.26 | -1.24 | 0.22 | 0.52 / 1.16 | -0.04 / -1.32 / 0.43 | -0.17 | -0.36 | 0.78 | -0.40 | 0.00 | 413 | diag |
| GC 2 (diag) | entry 12:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 13:25 | 261 | 0 | -0.31 | -1.35 | 0.18 | 0.53 / 1.32 | -0.04 / -1.49 / 0.56 | -0.19 | -0.50 | 0.83 | -0.37 | 0.00 | 417 | diag |
| GC 3 (diag) | entry 12:40 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:25 | 259 | 0 | -0.41 | -1.23 | 0.17 | 0.51 / 1.39 | -0.09 / -1.57 / 0.54 | -0.22 | -0.50 | 0.72 | -0.46 | 0.00 | 410 | diag |
| SI 1 (diag) | entry 12:25 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:20 | 232 | 0 | -1.88 | -1.31 | -0.61 | -0.78 / 1.27 | -0.39 / -4.13 / 0.47 | -1.65 | -0.61 | 0.35 | -2.39 | 0.00 | 389 | diag |
| SI 2 (diag) | entry 12:35 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:20 | 128 | 0 | -1.89 | -0.99 | -0.45 | -0.53 / 1.33 | -0.38 / -3.89 / 1.24 | -1.50 | -0.54 | 0.35 | -2.32 | 0.00 | 223 | diag |
| SI 3 (diag) | entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 | 229 | 0 | -1.91 | -1.41 | -0.48 | -0.56 / 1.15 | -0.40 / -3.93 / 0.73 | -1.55 | -0.69 | 0.44 | -2.33 | 0.00 | 385 | diag |
| HG 1 (diag) | entry 12:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 12:55 | 117 | 0 | -0.39 | -0.98 | -0.77 | -1.22 / 0.83 | -0.06 / -0.88 / -0.24 | -0.30 | -0.10 | 0.44 | -0.43 | 0.00 | 189 | diag |
| HG 2 (diag) | entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 | 254 | 0 | -0.68 | -0.90 | -0.78 | -0.87 / 0.36 | -0.10 / -0.14 / -0.52 | -0.37 | -0.24 | 0.72 | -0.41 | 0.00 | 403 | diag |
| HG 3 (diag) | entry 12:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 12:55 | 246 | 0 | -0.68 | -1.15 | -1.70 | -3.21 / 0.78 | -0.11 / -1.08 / -0.67 | -0.53 | -0.09 | 0.10 | -0.59 | 0.00 | 395 | diag |
| PL 1 (diag) | entry 12:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 13:00 | 151 | 1 | 0.21 | -0.13 | -0.53 | -0.95 / 0.96 | 0.02 / -2.94 / -0.39 | -0.78 | -0.15 | 0.54 | -1.24 | 0.00 | 223 | diag |
| PL 2 (diag) | entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 | 282 | 1 | -0.11 | -0.73 | -0.08 | -0.06 / 0.99 | -0.02 / -1.86 / 0.22 | -0.39 | -0.06 | 0.74 | -0.80 | 0.00 | 422 | diag |
| PL 3 (diag) | entry 12:25 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:00 | 151 | 1 | -0.16 | -0.35 | -0.55 | -0.80 / 1.25 | -0.07 / -2.26 / -0.50 | -0.65 | -0.12 | 0.39 | -1.05 | 0.00 | 221 | diag |
| CL 1 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 118 | 1 | 0.31 | -0.44 | -0.07 | -0.30 / 1.10 | -0.01 / -0.07 / -0.47 | -0.21 | 0.23 | 0.76 | -0.38 | 0.00 | 205 | diag |
| CL 2 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | 259 | 1 | 0.12 | -0.83 | -0.10 | -0.18 / 1.02 | -0.07 / 0.06 / -0.15 | -0.21 | 0.26 | 0.82 | -0.33 | 0.00 | 426 | diag |
| CL 3 (diag) | entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 128 | 1 | -0.14 | -0.63 | -0.18 | -0.15 / 0.82 | -0.09 / -0.17 / -0.24 | -0.23 | 0.31 | 0.78 | -0.35 | 0.00 | 215 | diag |
| NG 1 (diag) | entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 154 | 0 | -1.18 | -1.59 | -0.86 | -0.17 / 0.27 | -0.23 / -0.03 / 0.03 | -0.27 | -0.26 | 0.68 | -0.31 | 0.00 | 239 | diag |
| NG 2 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 152 | 0 | -1.46 | -1.32 | -0.99 | -0.31 / 0.58 | -0.31 / -0.73 / 0.20 | -0.37 | -0.12 | 0.35 | -0.46 | 0.00 | 240 | diag |
| NG 3 (diag) | entry 13:40 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 156 | 0 | -1.81 | -1.66 | -1.46 | -0.82 / 0.53 | -0.36 / -0.58 / 0.08 | -0.41 | -0.25 | 0.12 | -0.47 | 0.00 | 240 | diag |
| RB 1 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 110 | 1 | 0.22 | -0.08 | -0.30 | -0.62 / 1.37 | -0.05 / 0.04 / -0.45 | -0.17 | 0.15 | 0.46 | -0.36 | 0.00 | 196 | diag |
| RB 2 (diag) | entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 115 | 1 | -0.10 | -0.18 | 0.11 | 0.36 / 1.34 | -0.08 / -0.23 / 0.20 | -0.08 | 0.11 | 0.76 | -0.29 | 0.00 | 202 | diag |
| RB 3 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | 258 | 1 | -0.34 | -0.53 | -0.55 | -0.63 / 1.09 | -0.12 / -0.06 / -0.35 | -0.22 | 0.16 | 0.29 | -0.39 | 0.00 | 431 | diag |
| HO 1 (diag) | entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 | 262 | 1 | 0.20 | -0.22 | 0.55 | 0.88 / 1.59 | -0.01 / -0.13 / 0.72 | 0.07 | 0.01 | 0.89 | -0.16 | 0.00 | 429 | diag |
| HO 2 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | 255 | 1 | 0.12 | -0.32 | 0.49 | 0.90 / 1.33 | -0.01 / -0.15 / 0.53 | 0.05 | -0.04 | 0.89 | -0.15 | 0.50 | 422 | diag |
| HO 3 (diag) | entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | 146 | 1 | -0.02 | -0.21 | 0.05 | 0.12 / 1.23 | -0.02 / 0.12 / -0.21 | -0.07 | 0.32 | 0.58 | -0.28 | 0.00 | 238 | diag |
| ZN 1 (diag) | entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 126 | 0 | -3.27 | -3.35 | -3.79 | -5.56 / -2.25 | -0.66 / -0.56 / -0.73 | -1.07 | -0.31 | 0.61 | -0.85 | 0.00 | 190 | diag |
| ZN 2 (diag) | entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 124 | 0 | -3.44 | -2.32 | -3.40 | -3.30 / -2.09 | -0.70 / -0.48 / -0.78 | -1.05 | -0.40 | 0.36 | -0.89 | 0.00 | 187 | diag |
| ZN 3 (diag) | entry 14:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 122 | 0 | -3.69 | -3.69 | -4.15 | -5.72 / -2.85 | -0.75 / -0.53 / -0.80 | -1.15 | -0.39 | 0.70 | -0.92 | 0.00 | 187 | diag |
| ZB 1 (diag) | entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 118 | 0 | -3.28 | -2.61 | -3.37 | -3.61 / -2.24 | -0.67 / -0.48 / -0.55 | -1.00 | -0.27 | 0.83 | -0.82 | 0.00 | 182 | diag |
| ZB 2 (diag) | entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 120 | 0 | -3.57 | -2.30 | -3.54 | -3.47 / -2.75 | -0.72 / -0.53 / -0.68 | -1.05 | -0.44 | 0.67 | -0.90 | 0.00 | 185 | diag |
| ZB 3 (diag) | entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 119 | 0 | -3.62 | -1.75 | -4.14 | -5.11 / -2.69 | -0.73 / -0.63 / -1.01 | -1.15 | -0.28 | 0.07 | -0.99 | 0.00 | 181 | diag |
| ZF 1 (diag) | entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 128 | 0 | -2.58 | -2.60 | -3.24 | -5.06 / -1.43 | -0.53 / -0.54 / -0.74 | -0.95 | -0.25 | 0.54 | -0.76 | 0.00 | 197 | diag |
| ZF 2 (diag) | entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 122 | 0 | -2.90 | -1.63 | -2.66 | -2.31 / -1.53 | -0.60 / -0.60 / -0.72 | -0.99 | -0.33 | 0.42 | -0.84 | 0.00 | 190 | diag |
| ZF 3 (diag) | entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 122 | 0 | -2.96 | -2.12 | -3.24 | -4.53 / -1.52 | -0.60 / -0.46 / -0.52 | -0.86 | -0.46 | 0.35 | -0.76 | 0.00 | 190 | diag |
| ZT 1 (diag) | entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 105 | 0 | -2.20 | -2.52 | -2.13 | -2.03 / -1.45 | -0.46 / -0.60 / -0.72 | -0.87 | -0.37 | 0.69 | -0.73 | 0.00 | 168 | diag |
| ZT 2 (diag) | entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 112 | 0 | -2.53 | -2.80 | -3.34 | -6.17 / -2.47 | -0.52 / -0.60 / -0.79 | -0.97 | -0.32 | 0.70 | -0.77 | 0.00 | 181 | diag |
| ZT 3 (diag) | entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | 103 | 0 | -2.77 | -2.49 | -3.26 | -5.72 / -1.82 | -0.57 / -0.56 / -0.60 | -0.86 | -0.31 | 0.45 | -0.76 | 0.00 | 169 | diag |
| 6E 1 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 132 | 1 | 0.03 | -1.21 | 0.14 | 0.47 / 0.13 | -0.04 / -0.35 / 0.29 | -0.18 | -0.21 | 0.99 | -0.20 | 0.00 | 200 | diag |
| 6E 2 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:55 | 264 | 1 | -0.67 | -1.60 | -0.67 | -0.64 / -0.53 | -0.17 / -0.71 / 0.17 | -0.46 | 0.16 | 1.00 | -0.36 | 0.00 | 416 | diag |
| 6E 3 (diag) | entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 133 | 0 | -1.11 | -1.33 | -0.38 | 0.61 / -0.20 | -0.24 / -0.40 / 0.33 | -0.36 | 0.34 | 0.99 | -0.33 | 0.00 | 200 | diag |
| 6J 1 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 129 | 1 | -0.07 | -0.77 | -0.45 | -2.01 / -0.77 | -0.06 / -0.26 / -0.19 | -0.27 | -0.37 | 0.99 | -0.23 | 0.00 | 207 | diag |
| 6J 2 (diag) | entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 130 | 0 | -0.84 | -0.85 | -1.16 | -2.39 / -0.48 | -0.20 / -0.26 / -0.29 | -0.40 | -0.48 | 0.88 | -0.35 | 0.00 | 209 | diag |
| 6J 3 (diag) | entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 123 | 0 | -0.90 | -1.02 | -1.31 | -2.87 / -0.82 | -0.21 / -0.34 / -0.34 | -0.44 | -0.39 | 0.90 | -0.39 | 0.00 | 199 | diag |
| 6B 1 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 119 | 0 | -1.42 | -1.73 | -0.95 | 0.01 / -0.80 | -0.35 / -0.35 / 0.13 | -0.50 | -0.09 | 0.97 | -0.44 | 0.00 | 183 | diag |
| 6B 2 (diag) | entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 122 | 0 | -1.94 | -1.35 | -1.23 | -0.12 / -1.00 | -0.43 / -0.46 / 0.08 | -0.60 | 0.17 | 0.98 | -0.53 | 0.00 | 187 | diag |
| 6B 3 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:55 | 235 | 0 | -2.48 | -2.21 | -2.16 | -1.30 / -1.69 | -0.56 / -0.37 / -0.08 | -0.85 | 0.21 | 0.93 | -0.64 | 0.00 | 363 | diag |
| 6A 1 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 112 | 0 | -1.18 | -2.07 | -1.24 | -1.50 / -1.07 | -0.27 / -0.57 / -0.16 | -0.61 | -0.27 | 0.96 | -0.45 | 0.00 | 185 | diag |
| 6A 2 (diag) | entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 108 | 0 | -1.73 | -1.92 | -1.91 | -2.54 / -1.52 | -0.38 / -0.53 / -0.37 | -0.75 | -0.01 | 0.88 | -0.57 | 0.00 | 175 | diag |
| 6A 3 (diag) | entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 115 | 0 | -2.29 | -1.86 | -2.13 | -1.95 / -1.41 | -0.46 / -0.39 / -0.35 | -0.77 | -0.12 | 0.94 | -0.60 | 0.00 | 186 | diag |
| 6C 1 (diag) | entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 106 | 0 | -1.86 | -1.75 | -1.90 | -2.16 / -1.89 | -0.39 / -0.29 / -0.30 | -0.61 | -0.07 | 0.73 | -0.57 | 0.00 | 185 | diag |
| 6C 2 (diag) | entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 109 | 0 | -2.09 | -1.82 | -2.31 | -2.85 / -2.25 | -0.45 / -0.38 / -0.53 | -0.74 | -0.02 | 0.89 | -0.66 | 0.00 | 186 | diag |
| 6C 3 (diag) | entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | 107 | 0 | -2.17 | -2.03 | -2.23 | -2.56 / -2.23 | -0.45 / -0.26 / -0.45 | -0.69 | 0.27 | 0.65 | -0.62 | 0.00 | 185 | diag |
| ZC 1 (diag) | entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 108 | 0 | -3.23 | -1.44 | -2.85 | -2.38 / -1.32 | -0.64 / -0.73 / -0.53 | -1.03 | -0.25 | 0.33 | -0.87 | 0.00 | 186 | diag |
| ZC 2 (diag) | entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 114 | 0 | -3.74 | -2.05 | -3.24 | -2.63 / -1.56 | -0.72 / -0.75 / -0.60 | -1.11 | -0.19 | 0.25 | -0.93 | 0.00 | 195 | diag |
| ZC 3 (diag) | entry 13:40 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 117 | 0 | -4.63 | -2.18 | -4.00 | -3.11 / -1.51 | -0.91 / -0.74 / -0.68 | -1.23 | -0.29 | 0.06 | -1.06 | 0.00 | 198 | diag |
| ZS 1 (diag) | entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 114 | 0 | -2.76 | -0.87 | -2.18 | -1.00 / -0.12 | -0.55 / -0.42 / -0.18 | -0.62 | -0.07 | 0.09 | -0.64 | 0.00 | 190 | diag |
| ZS 2 (diag) | entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 114 | 0 | -3.05 | -0.95 | -2.06 | -0.51 / -0.11 | -0.60 / -0.35 / -0.15 | -0.66 | -0.11 | 0.17 | -0.66 | 0.00 | 193 | diag |
| ZS 3 (diag) | entry 13:20 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:15 | 235 | 0 | -3.36 | -1.42 | -2.62 | -1.24 / -0.69 | -0.71 / -0.69 / -0.03 | -0.88 | 0.08 | 0.14 | -0.76 | 0.00 | 378 | diag |
| ZW 1 (diag) | entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 104 | 0 | -1.04 | -0.80 | -0.69 | -0.22 / -0.28 | -0.24 / -0.43 / 0.11 | -0.55 | 0.20 | 0.97 | -0.43 | 0.00 | 195 | diag |
| ZW 2 (diag) | entry 13:40 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 111 | 0 | -1.31 | -1.39 | -1.32 | -1.09 / -0.64 | -0.31 / -0.41 / -0.22 | -0.67 | 0.38 | 0.94 | -0.51 | 0.00 | 203 | diag |
| ZW 3 (diag) | entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | 105 | 0 | -1.49 | -1.08 | -1.06 | -0.33 / -0.75 | -0.33 / -0.46 / 0.07 | -0.61 | 0.29 | 0.96 | -0.48 | 0.00 | 197 | diag |
| LE 1 (diag) | entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 | 121 | 0 | -2.01 | -0.42 | -1.13 | -0.28 / 0.83 | -0.42 / 0.01 / -0.51 | -0.49 | 0.36 | 0.25 | -0.57 | 0.00 | 201 | diag |
| LE 2 (diag) | entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 | 141 | 0 | -2.33 | -0.42 | -1.90 | -1.00 / 0.55 | -0.51 / -0.07 / -0.38 | -0.57 | 0.11 | 0.10 | -0.62 | 0.00 | 225 | diag |
| LE 3 (diag) | entry 13:15 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:00 | 120 | 0 | -2.41 | -0.38 | -1.96 | -1.11 / 0.62 | -0.50 / -0.04 / -0.41 | -0.55 | 0.01 | 0.04 | -0.60 | 0.00 | 205 | diag |
| HE 1 (diag) | entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 | 130 | 0 | -0.64 | -1.08 | -1.45 | -2.83 / -0.27 | -0.17 / -0.38 / -0.79 | -0.58 | -0.01 | 0.52 | -0.55 | 0.00 | 227 | diag |
| HE 2 (diag) | entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 | 132 | 1 | -0.74 | -1.33 | -1.44 | -2.94 / -1.19 | -0.20 / -0.28 / -0.55 | -0.61 | -0.38 | 0.92 | -0.49 | 0.00 | 229 | diag |
| HE 3 (diag) | entry 13:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:00 | 255 | 0 | -0.97 | -1.55 | -1.58 | -2.88 / -0.99 | -0.20 / -0.31 / -0.66 | -0.63 | 0.01 | 0.81 | -0.50 | 0.00 | 423 | diag |
| BTC 1 | entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 129 | 2 | 0.67 | -1.13 | 0.55 | 0.35 / 1.40 | 0.11 / -0.14 / 0.07 | 0.04 | -0.03 | 0.92 | -0.11 | 0.50 | 199 | NO |
| BTC 2 | entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 242 | 2 | 0.41 | -0.12 | 0.21 | -0.20 / 1.01 | 0.07 / -0.29 / 0.11 | -0.02 | -0.17 | 0.80 | -0.15 | 1.00 | 377 | NO |
| BTC 3 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 131 | 1 | 1.11 | -0.58 | 1.00 | 0.77 / 1.30 | 0.20 / -0.09 / 0.02 | 0.10 | -0.02 | 0.98 | -0.02 | 1.00 | 201 | diag |
| BTC 4 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 253 | 1 | 0.81 | -0.41 | 0.55 | -0.41 / 1.10 | 0.15 / -0.31 / 0.02 | 0.01 | -0.21 | 0.93 | -0.10 | 0.50 | 388 | diag |
| BTC 5 (diag) | entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 131 | 1 | 0.59 | -0.84 | 0.45 | 0.17 / 1.46 | 0.08 / -0.25 / 0.03 | -0.00 | 0.04 | 0.88 | -0.13 | 1.00 | 201 | diag |
| ETH 1 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 227 | 1 | 1.17 | -1.21 | -0.09 | -2.28 / 0.94 | 0.18 / -1.19 / -0.04 | -0.18 | 0.37 | 0.83 | -0.24 | 0.00 | 370 | diag |
| ETH 2 (diag) | entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | 135 | 1 | 0.75 | -0.59 | 0.07 | -1.19 / 0.91 | 0.10 / -0.72 / 0.05 | -0.11 | 0.13 | 0.82 | -0.19 | 0.00 | 215 | diag |
| ETH 3 (diag) | entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | 236 | 1 | 0.28 | -0.95 | -0.46 | -1.62 / 0.77 | 0.04 / -1.39 / 0.18 | -0.26 | -0.01 | 0.60 | -0.36 | 0.00 | 376 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 17 |
| diagnostic cells read | 83 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 2 / 1 |
| all-in uplift @20% > 0 (all scored) | 20 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 14 |
| worst-decile corr <= +0.30 | 83 |
| plateau >= 0.75 | 7 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 4 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | clean | -1.14 | -1.62 | -129229 | -105988 | 1453457 | -172113 | -0.71 | 41.9 | 1.19 | -87491 | 293330 | -111466 |
| 6A entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H1 | -3.76 | -3.57 | -75464 | -74875 | 535915 | -77229 | -0.92 | 53.6 | 2.26 | -80652 | 168480 | -83017 |
| 6A entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H2 | -0.38 | -0.54 | -131055 | -93549 | 313182 | -143414 | -0.31 | 38.9 | 2.32 | -84643 | 228544 | -86671 |
| 6A entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | all | -1.24 | -1.70 | -124199 | -101521 | 1814859 | -172113 | -0.89 | 43.5 | 1.61 | -86704 | 293330 | -111466 |
| 6B entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | clean | -1.51 | -1.82 | -147842 | -126435 | 1379253 | -197589 | -1.00 | 43.8 | 1.11 | -89781 | 345186 | -116561 |
| 6B entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H1 | -1.54 | -1.81 | -98794 | -92272 | 265799 | -111660 | -0.90 | 42.9 | 2.48 | -79202 | 161694 | -80116 |
| 6B entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H2 | 0.68 | 1.20 | -137630 | -107920 | 261377 | -165156 | 0.94 | 36.1 | 2.61 | -88788 | 218143 | -94564 |
| 6B entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | all | -0.95 | -1.24 | -141553 | -121065 | 1617163 | -197589 | -0.85 | 42.3 | 1.65 | -88509 | 345186 | -116561 |
| 6C entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | clean | -1.84 | -1.93 | -193588 | -145514 | 2131238 | -408263 | -0.78 | 42.9 | 1.07 | -94253 | 292221 | -111038 |
| 6C entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H1 | -2.65 | -2.76 | -79282 | -74550 | 375620 | -79606 | -0.93 | 42.9 | 2.54 | -71348 | 167323 | -76674 |
| 6C entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H2 | -1.88 | -2.26 | -104564 | -88909 | 428408 | -104887 | -1.00 | 52.8 | 2.18 | -90135 | 234851 | -92378 |
| 6C entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | all | -1.90 | -2.03 | -162825 | -125150 | 2845426 | -408263 | -0.86 | 45.2 | 1.53 | -92048 | 292221 | -111038 |
| 6E entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | clean | -0.02 | -0.03 | -124385 | -98304 | 562244 | -207442 | -0.03 | 43.8 | 1.42 | -93276 | 270162 | -118532 |
| 6E entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H1 | -1.68 | -1.94 | -112860 | -98289 | 384273 | -139216 | -0.76 | 50.0 | 2.48 | -74500 | 160715 | -78287 |
| 6E entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H2 | 1.98 | 5.59 | -63054 | -48353 | 123062 | -75240 | 4.04 | 19.4 | 2.77 | -81876 | 227046 | -86605 |
| 6E entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | all | 0.14 | 0.22 | -116363 | -92027 | 923276 | -207442 | 0.20 | 39.3 | 1.88 | -89141 | 270162 | -118532 |
| 6J entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | clean | -0.04 | -0.11 | -80760 | -67079 | 423870 | -103494 | -0.10 | 49.5 | 1.40 | -83764 | 292340 | -92203 |
| 6J entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H1 | -2.02 | -2.15 | -86506 | -75996 | 250172 | -104559 | -0.97 | 42.9 | 2.57 | -84643 | 152125 | -87012 |
| 6J entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | H2 | -1.97 | -2.06 | -82338 | -67309 | 326776 | -104309 | -0.80 | 41.7 | 2.30 | -83095 | 213539 | -83440 |
| 6J entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | all | -0.45 | -0.88 | -84862 | -69990 | 771960 | -104559 | -0.71 | 47.0 | 1.78 | -84442 | 292340 | -92203 |
| BTC entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | clean | 0.66 | 1.04 | -127492 | -100406 | 784687 | -261430 | 0.77 | 33.3 | 1.57 | -90915 | 241180 | -129344 |
| BTC entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | H1 | 0.12 | 0.18 | -166154 | -148091 | 397436 | -172040 | 0.10 | 39.3 | 2.68 | -76372 | 174329 | -78099 |
| BTC entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | H2 | 1.06 | 2.12 | -41961 | -35335 | 115506 | -42278 | 1.15 | 27.8 | 2.55 | -85888 | 225754 | -86031 |
| BTC entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | all | 0.55 | 0.86 | -134358 | -101609 | 784687 | -261430 | 0.99 | 33.3 | 1.97 | -88865 | 241180 | -129344 |
| CL entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | clean | -0.02 | -0.03 | -159209 | -126335 | 590992 | -226819 | -0.04 | 48.6 | 1.39 | -87895 | 293331 | -112296 |
| CL entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | H1 | 0.64 | 0.95 | -72868 | -54238 | 184605 | -96644 | 0.44 | 53.6 | 2.89 | -76573 | 142552 | -76611 |
| CL entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | H2 | -0.35 | -0.57 | -290248 | -239424 | 1175383 | -306788 | -0.23 | 58.3 | 2.33 | -92565 | 249041 | -96691 |
| CL entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | all | -0.10 | -0.16 | -200227 | -156209 | 1175383 | -306788 | -0.18 | 51.2 | 1.82 | -88078 | 293331 | -112296 |
| ES entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | clean | 0.74 | 1.17 | -128116 | -99093 | 475439 | -216579 | 1.42 | 41.9 | 1.57 | -85873 | 295629 | -95880 |
| ES entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H1 | -0.19 | -0.34 | -83528 | -81331 | 349378 | -84096 | -0.14 | 60.7 | 2.91 | -75008 | 177200 | -84132 |
| ES entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H2 | -0.52 | -0.66 | -193693 | -141635 | 371060 | -234011 | -0.52 | 52.8 | 2.28 | -104757 | 228201 | -113199 |
| ES entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | all | 0.28 | 0.42 | -139103 | -110656 | 520575 | -234011 | 0.83 | 47.6 | 1.92 | -89876 | 295629 | -113199 |
| ETH entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 (diag) | clean | 0.75 | 1.30 | -121159 | -91142 | 401929 | -217591 | 1.69 | 32.4 | 1.56 | -87719 | 245954 | -110745 |
| ETH entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 (diag) | H1 | -2.10 | -2.40 | -187992 | -169436 | 869058 | -189015 | -0.73 | 57.1 | 2.11 | -87378 | 149486 | -90484 |
| ETH entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 (diag) | H2 | 0.69 | 1.23 | -33297 | -26334 | 87121 | -34188 | 0.71 | 27.8 | 2.53 | -82633 | 218996 | -82742 |
| ETH entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 (diag) | all | 0.07 | 0.11 | -144533 | -107435 | 1132133 | -217591 | 0.09 | 35.7 | 1.87 | -87286 | 245954 | -110745 |
| GC entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 (diag) | clean | -0.23 | -0.32 | -136626 | -111206 | 799594 | -247073 | -0.26 | 49.5 | 1.42 | -81114 | 314498 | -88011 |
| GC entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 (diag) | H1 | -1.79 | -1.91 | -463438 | -414692 | 1507454 | -531018 | -0.74 | 50.0 | 1.51 | -123645 | 232997 | -156104 |
| GC entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 (diag) | H2 | 2.11 | 4.47 | -261129 | -210881 | 442336 | -264993 | 4.34 | 41.7 | 2.92 | -87918 | 225177 | -90854 |
| GC entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 (diag) | all | 0.22 | 0.32 | -286250 | -209705 | 1846210 | -531018 | 0.33 | 48.2 | 1.82 | -92603 | 314498 | -156104 |
| HE entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | clean | -0.72 | -1.02 | -120687 | -107341 | 925870 | -146790 | -0.70 | 47.6 | 1.26 | -91225 | 332008 | -97185 |
| HE entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | H1 | -2.25 | -2.38 | -138033 | -119658 | 496075 | -141876 | -0.86 | 42.9 | 2.54 | -68979 | 171671 | -76932 |
| HE entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | H2 | -3.44 | -3.30 | -151389 | -126977 | 906214 | -180559 | -0.99 | 55.6 | 1.93 | -94490 | 215208 | -101591 |
| HE entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | all | -1.44 | -1.81 | -134708 | -115572 | 2172051 | -180559 | -0.91 | 48.8 | 1.59 | -90984 | 332008 | -101591 |
| HG entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 (diag) | clean | -0.71 | -0.97 | -146569 | -117330 | 876991 | -196961 | -0.73 | 53.3 | 1.36 | -81519 | 243661 | -93828 |
| HG entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 (diag) | H1 | 0.02 | 0.03 | -200742 | -166464 | 317108 | -273693 | 0.02 | 53.6 | 2.68 | -82052 | 185601 | -82980 |
| HG entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 (diag) | H2 | -1.79 | -2.35 | -139524 | -125615 | 804683 | -147741 | -0.84 | 61.1 | 1.97 | -91293 | 233491 | -95016 |
| HG entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 (diag) | all | -0.78 | -1.08 | -162117 | -133053 | 1513814 | -273693 | -0.87 | 55.4 | 1.71 | -85365 | 243661 | -95016 |
| HO entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | clean | 0.20 | 0.27 | -158183 | -118875 | 484359 | -234745 | 0.38 | 42.9 | 1.45 | -90737 | 286425 | -108510 |
| HO entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | H1 | -0.35 | -0.47 | -125945 | -110810 | 323471 | -143919 | -0.24 | 53.6 | 2.70 | -66312 | 156980 | -72426 |
| HO entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | H2 | 1.31 | 2.30 | -292271 | -237616 | 630045 | -384307 | 1.76 | 50.0 | 3.21 | -76448 | 197003 | -79541 |
| HO entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | all | 0.55 | 0.87 | -203117 | -158556 | 630045 | -384307 | 1.93 | 46.4 | 2.02 | -86075 | 286425 | -108510 |
| LE entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | clean | -2.13 | -2.38 | -173235 | -145291 | 1987160 | -210718 | -1.00 | 49.5 | 1.04 | -89855 | 309344 | -101100 |
| LE entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | H1 | 0.73 | 1.46 | -230750 | -201387 | 442885 | -303061 | 0.94 | 35.7 | 2.83 | -93294 | 166953 | -109975 |
| LE entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | H2 | -1.75 | -2.16 | -174835 | -152858 | 836191 | -215153 | -0.84 | 50.0 | 1.97 | -103037 | 236636 | -108293 |
| LE entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | all | -1.13 | -1.57 | -193194 | -159606 | 2273229 | -303061 | -1.00 | 47.6 | 1.55 | -95831 | 309344 | -109975 |
| NG entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | clean | -1.17 | -2.01 | -104128 | -88140 | 1666572 | -129789 | -0.64 | 55.2 | 1.23 | -82178 | 297647 | -84806 |
| NG entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | H1 | -0.20 | -0.28 | -140632 | -114124 | 316547 | -146536 | -0.14 | 50.0 | 2.80 | -63963 | 175055 | -74637 |
| NG entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | H2 | -0.13 | -0.20 | -68047 | -49100 | 136658 | -75785 | -0.14 | 38.9 | 2.52 | -81383 | 198091 | -82524 |
| NG entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | all | -0.86 | -1.40 | -109090 | -88663 | 1734278 | -146536 | -0.65 | 51.2 | 1.75 | -81717 | 297647 | -84806 |
| NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | clean | 1.33 | 2.34 | -114820 | -90919 | 299800 | -195300 | 4.01 | 41.0 | 1.69 | -83888 | 259402 | -90910 |
| NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H1 | 0.78 | 1.44 | -117976 | -99570 | 242525 | -123923 | 0.91 | 50.0 | 3.23 | -67139 | 134123 | -71370 |
| NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H2 | 2.31 | 5.51 | -80833 | -72887 | 383592 | -88332 | 2.33 | 41.7 | 2.93 | -92538 | 228505 | -94729 |
| NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | all | 1.47 | 2.80 | -112578 | -90725 | 536585 | -195300 | 4.32 | 42.9 | 2.19 | -85143 | 259402 | -94729 |
| PL entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 (diag) | clean | -0.16 | -0.25 | -112784 | -97229 | 1230242 | -139089 | -0.12 | 53.3 | 1.44 | -81206 | 311518 | -91788 |
| PL entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 (diag) | H1 | -1.06 | -1.15 | -929864 | -701296 | 2122607 | -1402698 | -0.61 | 39.3 | 0.97 | -205123 | 393041 | -291760 |
| PL entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 (diag) | H2 | 1.69 | 3.53 | -192196 | -174902 | 461430 | -199703 | 2.53 | 33.3 | 2.71 | -107115 | 248183 | -114085 |
| PL entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 (diag) | all | -0.08 | -0.09 | -354099 | -242019 | 2417363 | -1402698 | -0.11 | 46.4 | 1.63 | -119094 | 393041 | -291760 |
| RB entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | clean | -0.14 | -0.19 | -167503 | -124472 | 512263 | -313273 | -0.25 | 39.0 | 1.38 | -94157 | 308405 | -114764 |
| RB entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | H1 | -1.05 | -1.33 | -91645 | -78023 | 214819 | -115067 | -0.73 | 57.1 | 2.60 | -77625 | 165428 | -87180 |
| RB entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | H2 | 0.73 | 1.29 | -212965 | -192745 | 717031 | -234009 | 0.68 | 41.7 | 2.69 | -99031 | 221854 | -110125 |
| RB entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | all | 0.11 | 0.16 | -186836 | -144699 | 739641 | -313273 | 0.27 | 42.9 | 1.86 | -94465 | 308405 | -114764 |
| RTY entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | clean | 0.80 | 1.40 | -90079 | -82589 | 575296 | -99963 | 1.26 | 49.5 | 1.56 | -85894 | 276197 | -91389 |
| RTY entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H1 | -0.65 | -0.94 | -117898 | -99419 | 246423 | -127872 | -0.59 | 53.6 | 2.75 | -77445 | 140992 | -85238 |
| RTY entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | H2 | 0.57 | 0.85 | -160254 | -122315 | 318428 | -231659 | 0.70 | 36.1 | 2.51 | -98771 | 227605 | -100120 |
| RTY entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | all | 0.53 | 0.85 | -113980 | -96809 | 575296 | -231659 | 1.40 | 47.6 | 1.95 | -88683 | 276197 | -100120 |
| SI entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 (diag) | clean | -1.88 | -2.14 | -166595 | -140636 | 1914184 | -202049 | -0.89 | 56.2 | 1.06 | -87130 | 282692 | -95207 |
| SI entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 (diag) | H1 | -1.74 | -1.73 | -3789174 | -2685687 | 9011314 | -6968382 | -0.99 | 64.3 | -1.10 | -765343 | 1714232 | -1404896 |
| SI entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 (diag) | H2 | 2.60 | 4.90 | -624181 | -478712 | 1340386 | -713598 | 3.21 | 36.1 | 3.21 | -113655 | 295949 | -117678 |
| SI entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 (diag) | all | -0.48 | -0.50 | -1184623 | -727853 | 11392973 | -6968382 | -0.56 | 53.6 | 0.47 | -253991 | 1858008 | -1404896 |
| YM entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | clean | 0.87 | 1.34 | -139992 | -96000 | 443795 | -271470 | 1.78 | 34.3 | 1.60 | -84685 | 237968 | -96905 |
| YM entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | H1 | -1.07 | -1.40 | -107162 | -90852 | 228350 | -155265 | -0.86 | 42.9 | 2.63 | -78604 | 163176 | -79105 |
| YM entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | H2 | -0.96 | -1.20 | -144040 | -117249 | 511189 | -165489 | -0.53 | 41.7 | 2.26 | -91194 | 224342 | -102565 |
| YM entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | all | 0.24 | 0.34 | -148776 | -105368 | 739539 | -271470 | 0.44 | 36.9 | 1.90 | -85512 | 237968 | -102565 |
| ZB entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | clean | -3.30 | -3.19 | -194764 | -155567 | 3092068 | -340410 | -0.97 | 55.2 | 0.79 | -87441 | 450214 | -99159 |
| ZB entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H1 | -4.03 | -3.76 | -90442 | -84629 | 555631 | -96256 | -0.95 | 53.6 | 2.35 | -77610 | 161338 | -78287 |
| ZB entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H2 | -3.53 | -3.68 | -142761 | -117007 | 1065028 | -177640 | -0.89 | 66.7 | 1.93 | -81089 | 217539 | -82524 |
| ZB entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | all | -3.37 | -3.28 | -176318 | -140105 | 4584022 | -340410 | -0.97 | 57.1 | 1.27 | -85170 | 450214 | -99159 |
| ZC entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | clean | -3.22 | -3.18 | -173499 | -149008 | 2959794 | -239387 | -0.99 | 46.7 | 0.82 | -90232 | 341120 | -93002 |
| ZC entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H1 | -3.12 | -3.20 | -171631 | -147800 | 786903 | -175119 | -0.97 | 64.3 | 2.10 | -80499 | 158239 | -86249 |
| ZC entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H2 | -2.01 | -2.25 | -255703 | -211923 | 1224820 | -289705 | -0.75 | 47.2 | 1.95 | -81089 | 218173 | -82524 |
| ZC entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | all | -2.85 | -2.93 | -201053 | -167294 | 4911481 | -289705 | -0.94 | 50.0 | 1.26 | -88016 | 341120 | -93002 |
| ZF entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | clean | -2.98 | -2.93 | -194521 | -155082 | 2726566 | -411967 | -0.99 | 50.5 | 0.86 | -85323 | 393938 | -94099 |
| ZF entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H1 | -6.07 | -4.70 | -70953 | -63070 | 474861 | -83366 | -1.00 | 64.3 | 2.37 | -80176 | 156845 | -83420 |
| ZF entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H2 | -4.24 | -3.97 | -105423 | -94814 | 866356 | -113055 | -1.00 | 66.7 | 1.97 | -85690 | 220478 | -92378 |
| ZF entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | all | -3.24 | -3.13 | -169677 | -134635 | 4053010 | -411967 | -1.00 | 56.0 | 1.33 | -85251 | 393938 | -94099 |
| ZN entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | clean | -3.30 | -3.32 | -188441 | -156362 | 3089817 | -325377 | -0.97 | 62.9 | 0.79 | -87849 | 402728 | -93037 |
| ZN entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H1 | -5.44 | -4.45 | -75153 | -72388 | 590080 | -80477 | -1.00 | 60.7 | 2.26 | -80037 | 156566 | -83141 |
| ZN entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H2 | -5.84 | -4.62 | -132231 | -112421 | 1207896 | -155012 | -1.00 | 66.7 | 1.75 | -90781 | 222279 | -99037 |
| ZN entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | all | -3.79 | -3.63 | -171713 | -139601 | 4791706 | -325377 | -1.00 | 63.1 | 1.23 | -87977 | 402728 | -99037 |
| ZS entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | clean | -2.86 | -2.86 | -184748 | -155948 | 2609262 | -280690 | -0.98 | 47.6 | 0.91 | -89010 | 381490 | -94309 |
| ZS entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H1 | -1.88 | -1.97 | -141211 | -117073 | 350195 | -174182 | -1.00 | 39.3 | 2.41 | -77039 | 157583 | -79470 |
| ZS entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H2 | -0.48 | -0.63 | -148448 | -125388 | 463126 | -175508 | -0.33 | 33.3 | 2.30 | -86965 | 244554 | -91406 |
| ZS entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | all | -2.18 | -2.32 | -176799 | -147629 | 3112434 | -280690 | -0.99 | 43.5 | 1.46 | -87710 | 381490 | -94309 |
| ZT entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | clean | -2.21 | -2.46 | -166874 | -143672 | 2035926 | -266338 | -0.98 | 43.8 | 1.00 | -88073 | 345283 | -89903 |
| ZT entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H1 | -4.92 | -4.25 | -71596 | -68438 | 570997 | -81069 | -1.00 | 57.1 | 2.23 | -80980 | 161405 | -85028 |
| ZT entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | H2 | -1.64 | -2.73 | -176346 | -139502 | 1214475 | -204215 | -0.68 | 66.7 | 1.76 | -100257 | 234630 | -117990 |
| ZT entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | all | -2.13 | -2.68 | -164830 | -137555 | 3821398 | -266338 | -0.89 | 50.6 | 1.36 | -90442 | 345283 | -117990 |
| ZW entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | clean | -1.12 | -1.32 | -171135 | -139007 | 1136848 | -230460 | -0.89 | 38.1 | 1.22 | -83957 | 355768 | -98604 |
| ZW entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H1 | -1.62 | -1.83 | -113162 | -103698 | 418287 | -123420 | -0.66 | 42.9 | 2.40 | -94978 | 156752 | -101617 |
| ZW entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | H2 | 0.19 | 0.36 | -189584 | -149584 | 720475 | -239684 | 0.15 | 41.7 | 2.60 | -84826 | 174401 | -86785 |
| ZW entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | all | -0.69 | -0.97 | -170923 | -138614 | 2099064 | -239684 | -0.56 | 39.9 | 1.71 | -87416 | 355768 | -101617 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | -25.3 | -25.8 | 7.3 | 21.7 | 0.6 / 12.9 | 17.4 / 35.0 | NO |
| NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | -4.7 | 7.8 | 15.4 | 35.1 | 8.7 / 17.5 | 43.3 / 47.4 | NO |
| RTY entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | -21.2 | -2.0 | 10.5 | 29.9 | 8.0 / 14.7 | 15.3 / 29.4 | NO |
| YM entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | -26.4 | -9.2 | 14.1 | 31.6 | -1.2 / 16.0 | 16.9 / 21.3 | NO |
| GC entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 (diag) | -23.4 | -109.2 | -10.4 | -4.4 | 14.0 / 24.7 | -120.5 / -81.0 | NO |
| SI entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 (diag) | -99.6 | -2442.7 | -355.6 | -883.7 | 1.1 / 10.6 | -2580.3 / -1368.6 | NO |
| HG entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 (diag) | -44.4 | -21.9 | 7.6 | 15.6 | 3.4 / 16.1 | -28.5 / -4.6 | NO |
| PL entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 (diag) | -32.9 | -419.4 | -69.4 | -116.3 | 7.1 / 19.0 | -447.6 / -267.1 | NO |
| CL entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | -32.4 | -26.7 | 4.2 | -4.1 | -27.7 / 0.5 | 32.0 / 32.0 | NO |
| NG entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | -42.3 | 16.6 | 23.5 | 12.3 | 15.9 / 21.4 | 35.6 / 36.4 | NO |
| RB entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 (diag) | -27.8 | -35.8 | -7.8 | 8.7 | -36.9 / -8.5 | 13.0 / 22.0 | NO |
| HO entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 (diag) | -16.7 | -42.0 | 5.2 | 10.8 | -23.4 / 5.9 | 34.8 / 34.3 | NO |
| ZN entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | -82.4 | -5.2 | 10.5 | -66.7 | 4.7 / 10.7 | 20.7 / 25.3 | NO |
| ZB entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | -78.9 | -5.3 | 8.9 | -97.3 | -6.2 / 2.3 | 30.0 / 30.0 | NO |
| ZF entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | -74.2 | -13.0 | 10.2 | -62.0 | -13.9 / 7.1 | 20.2 / 25.0 | NO |
| ZT entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 (diag) | -67.2 | -39.7 | 6.8 | -20.3 | 10.8 / 10.9 | 17.1 / 23.5 | NO |
| 6E entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | -28.0 | -40.8 | 8.9 | 22.7 | -41.9 / 0.3 | 23.1 / 25.9 | NO |
| 6J entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | -36.0 | 7.1 | 19.1 | 8.5 | 6.4 / 19.3 | 11.9 / 16.4 | NO |
| 6B entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | -45.0 | -37.2 | 7.3 | -21.1 | -38.3 / 1.9 | 25.1 / 26.9 | NO |
| 6A entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | -47.7 | -27.9 | 11.7 | 0.0 | -28.9 / 6.7 | 19.6 / 24.1 | NO |
| 6C entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 (diag) | -56.8 | -70.3 | -2.4 | -1.3 | -71.7 / -9.4 | 31.7 / 41.1 | NO |
| ZC entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | -80.4 | -14.0 | 5.9 | -33.4 | 5.1 / 6.7 | 13.4 / 14.5 | NO |
| ZS entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | -63.6 | -11.6 | 4.0 | -38.9 | 2.5 / 3.8 | 26.1 / 26.3 | NO |
| ZW entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 (diag) | -42.9 | -10.1 | 6.9 | -25.4 | -5.4 / 12.5 | -16.1 / -3.6 | NO |
| LE entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | -54.9 | -24.7 | -6.1 | -12.3 | -7.2 / 4.4 | -30.7 / -0.3 | NO |
| HE entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 (diag) | -51.5 | -9.9 | 4.3 | -10.9 | -1.8 / 2.6 | 31.2 / 37.7 | NO |
| BTC entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | -21.5 | -60.4 | 9.3 | 27.0 | -61.7 / 6.5 | 10.5 / 19.0 | NO |
| ETH entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 (diag) | -28.9 | -26.7 | 14.1 | 35.2 | -27.7 / 12.4 | 6.6 / 11.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 672 | -13.9 | -43.2 | -29.0 | 29.4 | -0.26 / -0.81 / -0.55 | 105.2 / 75.8 |
| ES 2 entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1227 | -13.4 | -42.7 | -28.5 | 29.4 | -0.39 / -1.25 / -0.83 | 61.5 / 32.1 |
| ES 3 entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 667 | -27.7 | -57.1 | -42.9 | 29.4 | -0.46 / -0.94 / -0.71 | 63.0 / 33.6 |
| ES 4 entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 651 | -14.9 | -44.3 | -30.0 | 29.4 | -0.23 / -0.68 / -0.46 | 63.3 / 33.9 |
| ES 5 entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1210 | -12.6 | -41.9 | -27.6 | 29.4 | -0.30 / -1.00 / -0.66 | 54.9 / 25.5 |
| ES 6 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1217 | -19.8 | -49.2 | -34.9 | 29.4 | -0.49 / -1.21 / -0.86 | 38.3 / 9.0 |
| ES 7 (diag) entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1181 | -34.1 | -63.4 | -49.0 | 29.4 | -0.69 / -1.27 / -0.98 | 16.8 / -12.6 |
| ES 8 (diag) entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 646 | -36.3 | -65.7 | -51.5 | 29.4 | -0.47 / -0.85 / -0.67 | -0.1 / -29.5 |
| NQ 1 entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 688 | -38.9 | -53.3 | -44.8 | 14.4 | -0.57 / -0.78 / -0.65 | 187.1 / 172.7 |
| NQ 2 entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1258 | -39.2 | -53.6 | -45.1 | 14.4 | -0.81 / -1.11 / -0.94 | 129.1 / 114.8 |
| NQ 3 entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1253 | -65.5 | -79.8 | -71.3 | 14.4 | -1.22 / -1.48 / -1.33 | 124.9 / 110.6 |
| NQ 4 entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 684 | -80.0 | -94.4 | -85.8 | 14.4 | -1.05 / -1.24 / -1.13 | 156.7 / 142.3 |
| NQ 5 entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 671 | -41.9 | -56.3 | -47.7 | 14.4 | -0.56 / -0.75 / -0.64 | 153.2 / 138.9 |
| NQ 6 entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1246 | -49.5 | -63.9 | -55.4 | 14.4 | -0.86 / -1.11 / -0.96 | 111.6 / 97.2 |
| NQ 7 (diag) entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 659 | -102.6 | -116.9 | -108.3 | 14.4 | -1.08 / -1.23 / -1.14 | 79.0 / 64.6 |
| NQ 8 (diag) entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1231 | -95.7 | -110.0 | -101.5 | 14.4 | -1.31 / -1.50 / -1.38 | -9.7 / -24.1 |
| RTY 1 entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 741 | -13.9 | -28.3 | -26.0 | 14.4 | -0.56 / -1.14 / -1.05 | 31.1 / 16.7 |
| RTY 2 entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 364 | -14.1 | -28.5 | -26.2 | 14.4 | -0.30 / -0.60 / -0.55 | 40.2 / 25.8 |
| RTY 3 entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 734 | -19.0 | -33.4 | -31.1 | 14.4 | -0.61 / -1.07 / -1.00 | 23.3 / 9.0 |
| RTY 4 (diag) entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | gross-positive, cost-negative pre-2023 | 368 | 5.1 | -9.2 | -7.0 | 14.4 | 0.13 / -0.23 / -0.17 | 19.9 / 5.6 |
| RTY 5 (diag) entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 355 | -14.9 | -29.3 | -27.0 | 14.4 | -0.25 / -0.49 / -0.46 | 26.2 / 11.9 |
| RTY 6 (diag) entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | gross-positive, cost-negative pre-2023 | 359 | 6.8 | -7.6 | -5.3 | 14.4 | 0.14 / -0.15 / -0.11 | 9.6 / -4.8 |
| YM 1 entry 15:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 661 | -2.1 | -16.5 | -10.6 | 14.4 | -0.05 / -0.37 / -0.24 | 56.6 / 42.3 |
| YM 2 (diag) entry 15:30 (close-30m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 1248 | -0.2 | -14.5 | -8.7 | 14.4 | -0.01 / -0.53 / -0.32 | 27.0 / 12.6 |
| YM 3 (diag) entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | gross-positive, cost-negative pre-2023 | 1212 | 4.4 | -10.0 | -4.1 | 14.4 | 0.12 / -0.28 / -0.12 | 14.7 / 0.4 |
| YM 4 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 640 | -7.6 | -21.9 | -16.0 | 14.4 | -0.16 / -0.45 / -0.33 | 13.2 / -1.1 |
| GC 1 (diag) entry 12:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:25 | negative pre-2023 | 1144 | -9.6 | -34.0 | -24.2 | 24.4 | -0.35 / -1.24 / -0.88 | 15.5 / -8.9 |
| GC 2 (diag) entry 12:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 13:25 | negative pre-2023 | 1149 | -7.2 | -31.5 | -21.8 | 24.4 | -0.31 / -1.35 / -0.93 | 14.4 / -10.0 |
| GC 3 (diag) entry 12:40 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:25 | negative pre-2023 | 1143 | -7.1 | -31.4 | -21.6 | 24.4 | -0.28 / -1.23 / -0.85 | 10.9 / -13.5 |
| SI 1 (diag) entry 12:25 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:20 | negative pre-2023 | 1089 | -24.2 | -78.6 | -59.7 | 54.4 | -0.41 / -1.31 / -1.00 | -19.1 / -73.4 |
| SI 2 (diag) entry 12:35 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:20 | negative pre-2023 | 544 | -7.3 | -61.7 | -42.9 | 54.4 | -0.12 / -0.99 / -0.69 | -60.7 / -115.1 |
| SI 3 (diag) entry 12:35 (close-50m) |px-prior RTH close|>=0.4ADR against exit 13:20 | negative pre-2023 | 1110 | -17.8 | -72.2 | -53.2 | 54.4 | -0.35 / -1.41 / -1.04 | -15.4 / -69.8 |
| HG 1 (diag) entry 12:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 12:55 | negative pre-2023 | 625 | -2.4 | -31.8 | -24.1 | 29.4 | -0.07 / -0.98 / -0.74 | 9.9 / -19.4 |
| HG 2 (diag) entry 12:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 12:55 | gross-positive, cost-negative pre-2023 | 1242 | 11.4 | -17.9 | -10.2 | 29.4 | 0.59 / -0.90 / -0.51 | 11.3 / -18.0 |
| HG 3 (diag) entry 12:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 12:55 | gross-positive, cost-negative pre-2023 | 1240 | 3.7 | -25.6 | -17.8 | 29.4 | 0.18 / -1.15 / -0.80 | 7.8 / -21.6 |
| PL 1 (diag) entry 12:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 13:00 | gross-positive, cost-negative pre-2023 | 647 | 12.7 | -1.7 | -2.9 | 14.4 | 0.82 / -0.13 / -0.21 | 16.7 / 2.3 |
| PL 2 (diag) entry 12:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:00 | gross-positive, cost-negative pre-2023 | 1278 | 3.5 | -10.8 | -12.1 | 14.4 | 0.23 / -0.73 / -0.81 | 12.1 / -2.3 |
| PL 3 (diag) entry 12:25 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:00 | gross-positive, cost-negative pre-2023 | 642 | 8.9 | -5.5 | -6.7 | 14.4 | 0.52 / -0.35 / -0.42 | 10.2 / -4.1 |
| CL 1 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 623 | -0.5 | -24.9 | -22.5 | 24.4 | -0.01 / -0.44 / -0.40 | 37.4 / 13.0 |
| CL 2 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | negative pre-2023 | 1240 | -6.4 | -30.8 | -28.4 | 24.4 | -0.17 / -0.83 / -0.77 | 23.7 / -0.7 |
| CL 3 (diag) entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 648 | -0.1 | -24.5 | -21.8 | 24.4 | -0.00 / -0.63 / -0.57 | 15.5 / -8.8 |
| NG 1 (diag) entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 697 | -36.0 | -60.3 | -65.6 | 24.4 | -0.95 / -1.59 / -1.69 | -13.3 / -37.7 |
| NG 2 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 679 | -34.5 | -58.9 | -64.3 | 24.4 | -0.78 / -1.32 / -1.42 | -22.3 / -46.7 |
| NG 3 (diag) entry 13:40 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 678 | -50.2 | -74.6 | -79.9 | 24.4 | -1.13 / -1.66 / -1.74 | -32.1 / -56.4 |
| RB 1 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | gross-positive, cost-negative pre-2023 | 601 | 6.8 | -5.9 | -5.2 | 12.8 | 0.09 / -0.08 / -0.07 | 12.1 / -0.6 |
| RB 2 (diag) entry 14:00 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:25 | gross-positive, cost-negative pre-2023 | 619 | 2.5 | -10.3 | -9.5 | 12.8 | 0.04 / -0.18 / -0.17 | 6.8 / -6.0 |
| RB 3 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | negative pre-2023 | 1278 | -11.0 | -23.8 | -23.1 | 12.8 | -0.25 / -0.53 / -0.52 | -3.3 / -16.0 |
| HO 1 (diag) entry 13:50 (close-40m) |px-prior RTH close|>=0.4ADR against exit 14:25 | gross-positive, cost-negative pre-2023 | 1272 | 2.3 | -10.5 | -9.2 | 12.8 | 0.05 / -0.22 / -0.19 | 18.9 / 6.2 |
| HO 2 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:25 | negative pre-2023 | 1260 | -4.6 | -17.3 | -16.0 | 12.8 | -0.08 / -0.32 / -0.29 | 16.5 / 3.8 |
| HO 3 (diag) entry 13:30 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:25 | negative pre-2023 | 628 | -3.6 | -16.3 | -14.9 | 12.8 | -0.05 / -0.21 / -0.19 | 11.6 / -1.1 |
| ZN 1 (diag) entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | negative pre-2023 | 624 | -0.5 | -36.1 | -41.2 | 35.6 | -0.04 / -3.35 / -3.74 | 0.7 / -34.9 |
| ZN 2 (diag) entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 609 | 6.1 | -29.6 | -34.7 | 35.6 | 0.48 / -2.32 / -2.69 | 2.1 / -33.5 |
| ZN 3 (diag) entry 14:30 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:55 | negative pre-2023 | 624 | -1.9 | -37.5 | -42.6 | 35.6 | -0.20 / -3.69 / -4.08 | -1.0 / -36.6 |
| ZB 1 (diag) entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 638 | 8.6 | -58.2 | -77.3 | 66.9 | 0.39 / -2.61 / -3.40 | -1.3 / -68.2 |
| ZB 2 (diag) entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 630 | 11.6 | -55.3 | -74.5 | 66.9 | 0.48 / -2.30 / -3.06 | -4.7 / -71.5 |
| ZB 3 (diag) entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 616 | 20.1 | -46.7 | -65.9 | 66.9 | 0.75 / -1.75 / -2.43 | 0.3 / -66.6 |
| ZF 1 (diag) entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | negative pre-2023 | 596 | -0.8 | -20.8 | -22.9 | 20.0 | -0.11 / -2.60 / -2.82 | 2.9 / -17.1 |
| ZF 2 (diag) entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 584 | 5.0 | -15.0 | -17.1 | 20.0 | 0.54 / -1.63 / -1.85 | 3.1 / -16.9 |
| ZF 3 (diag) entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 598 | 0.3 | -19.7 | -21.8 | 20.0 | 0.03 / -2.12 / -2.33 | -4.0 / -24.0 |
| ZT 1 (diag) entry 14:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 529 | 1.4 | -18.6 | -19.6 | 20.0 | 0.19 / -2.52 / -2.65 | 4.2 / -15.7 |
| ZT 2 (diag) entry 14:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 567 | 1.2 | -18.8 | -19.9 | 20.0 | 0.17 / -2.80 / -2.94 | 2.7 / -17.3 |
| ZT 3 (diag) entry 14:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:55 | gross-positive, cost-negative pre-2023 | 558 | 0.7 | -19.3 | -20.3 | 20.0 | 0.09 / -2.49 / -2.61 | -3.7 / -23.7 |
| 6E 1 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 612 | -7.1 | -23.9 | -25.1 | 16.9 | -0.36 / -1.21 / -1.26 | 16.6 / -0.3 |
| 6E 2 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:55 | negative pre-2023 | 1272 | -3.9 | -20.7 | -21.9 | 16.9 | -0.30 / -1.60 / -1.69 | 11.0 / -5.9 |
| 6E 3 (diag) entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 628 | -3.4 | -20.3 | -21.4 | 16.9 | -0.22 / -1.33 / -1.41 | 5.9 / -10.9 |
| 6J 1 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | gross-positive, cost-negative pre-2023 | 645 | 3.7 | -13.1 | -18.5 | 16.9 | 0.22 / -0.77 / -1.08 | 16.1 / -0.7 |
| 6J 2 (diag) entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | gross-positive, cost-negative pre-2023 | 630 | 4.2 | -12.6 | -18.0 | 16.9 | 0.29 / -0.85 / -1.20 | 5.0 / -11.8 |
| 6J 3 (diag) entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | gross-positive, cost-negative pre-2023 | 652 | 2.7 | -14.2 | -19.5 | 16.9 | 0.20 / -1.02 / -1.39 | 5.1 / -11.7 |
| 6B 1 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 598 | -7.6 | -24.5 | -25.9 | 16.9 | -0.55 / -1.73 / -1.82 | 2.8 / -14.1 |
| 6B 2 (diag) entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 615 | -3.4 | -20.3 | -21.6 | 16.9 | -0.23 / -1.35 / -1.43 | 1.8 / -15.1 |
| 6B 3 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 13:55 | negative pre-2023 | 1268 | -3.1 | -20.0 | -21.4 | 16.9 | -0.35 / -2.21 / -2.35 | 0.9 / -16.0 |
| 6A 1 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 595 | -5.7 | -30.1 | -34.1 | 24.4 | -0.40 / -2.07 / -2.32 | 11.4 / -13.0 |
| 6A 2 (diag) entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 588 | -0.3 | -24.6 | -28.7 | 24.4 | -0.02 / -1.92 / -2.21 | 8.7 / -15.7 |
| 6A 3 (diag) entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | gross-positive, cost-negative pre-2023 | 597 | 3.9 | -20.4 | -24.5 | 24.4 | 0.37 / -1.86 / -2.20 | 3.2 / -21.1 |
| 6C 1 (diag) entry 13:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 603 | -2.8 | -17.2 | -18.4 | 14.4 | -0.30 / -1.75 / -1.86 | -1.2 / -15.6 |
| 6C 2 (diag) entry 13:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 618 | -2.3 | -16.7 | -17.9 | 14.4 | -0.27 / -1.82 / -1.94 | -0.2 / -14.5 |
| 6C 3 (diag) entry 13:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 13:55 | negative pre-2023 | 617 | -2.6 | -17.0 | -18.2 | 14.4 | -0.33 / -2.03 / -2.16 | -1.5 / -15.9 |
| ZC 1 (diag) entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | gross-positive, cost-negative pre-2023 | 504 | 0.6 | -28.7 | -29.8 | 29.4 | 0.03 / -1.44 / -1.51 | -2.2 / -31.6 |
| ZC 2 (diag) entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | negative pre-2023 | 499 | -6.4 | -35.8 | -36.7 | 29.4 | -0.38 / -2.05 / -2.10 | -5.8 / -35.2 |
| ZC 3 (diag) entry 13:40 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:15 | negative pre-2023 | 499 | -6.3 | -35.7 | -36.7 | 29.4 | -0.40 / -2.18 / -2.25 | -10.8 / -40.2 |
| ZS 1 (diag) entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | gross-positive, cost-negative pre-2023 | 503 | 1.9 | -27.5 | -29.2 | 29.4 | 0.04 / -0.87 / -0.92 | -34.9 / -64.2 |
| ZS 2 (diag) entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | gross-positive, cost-negative pre-2023 | 510 | 1.1 | -28.2 | -29.9 | 29.4 | 0.03 / -0.95 / -1.00 | -28.8 / -58.2 |
| ZS 3 (diag) entry 13:20 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:15 | negative pre-2023 | 1009 | -1.4 | -30.7 | -32.3 | 29.4 | -0.07 / -1.42 / -1.49 | -22.7 / -52.0 |
| ZW 1 (diag) entry 13:20 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:15 | gross-positive, cost-negative pre-2023 | 498 | 6.9 | -22.5 | -23.7 | 29.4 | 0.23 / -0.80 / -0.85 | 11.7 / -17.7 |
| ZW 2 (diag) entry 13:40 (close-40m) |px-prior RTH close|>=0.7ADR against exit 14:15 | negative pre-2023 | 502 | -0.2 | -29.6 | -31.0 | 29.4 | -0.03 / -1.39 / -1.45 | 8.6 / -20.8 |
| ZW 3 (diag) entry 13:30 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:15 | gross-positive, cost-negative pre-2023 | 490 | 2.2 | -27.2 | -28.7 | 29.4 | 0.08 / -1.08 / -1.14 | 4.6 / -24.7 |
| LE 1 (diag) entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 | gross-positive, cost-negative pre-2023 | 673 | 15.3 | -9.1 | -1.6 | 24.4 | 0.71 / -0.42 / -0.07 | -33.6 / -57.9 |
| LE 2 (diag) entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 | gross-positive, cost-negative pre-2023 | 696 | 16.9 | -7.5 | 0.1 | 24.4 | 0.94 / -0.42 / 0.01 | -35.9 / -60.2 |
| LE 3 (diag) entry 13:15 (close-50m) |px-prior RTH close|>=0.7ADR against exit 14:00 | gross-positive, cost-negative pre-2023 | 674 | 16.5 | -7.8 | -0.3 | 24.4 | 0.79 / -0.38 / -0.02 | -47.1 / -71.4 |
| HE 1 (diag) entry 13:05 (close-60m) |px-prior RTH close|>=0.7ADR against exit 14:00 | negative pre-2023 | 736 | -3.7 | -28.0 | -26.5 | 24.4 | -0.14 / -1.08 / -1.02 | 13.6 / -10.7 |
| HE 2 (diag) entry 13:35 (close-30m) |px-prior RTH close|>=0.7ADR against exit 14:00 | negative pre-2023 | 767 | -1.1 | -25.5 | -23.9 | 24.4 | -0.06 / -1.33 / -1.24 | 14.3 / -10.0 |
| HE 3 (diag) entry 13:05 (close-60m) |px-prior RTH close|>=0.4ADR against exit 14:00 | negative pre-2023 | 1324 | -3.2 | -27.5 | -25.9 | 24.4 | -0.18 / -1.55 / -1.46 | 12.2 / -12.2 |
| BTC 1 entry 15:00 (close-60m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 81 | -205.6 | -259.9 | -228.4 | 54.4 | -0.90 / -1.13 / -1.00 | 238.0 / 183.6 |
| BTC 2 entry 15:00 (close-60m) |px-prior RTH close|>=0.4ADR against exit 15:55 | gross-positive, cost-negative pre-2023 | 162 | 36.0 | -18.4 | 13.5 | 54.4 | 0.23 / -0.12 / 0.09 | 135.3 / 81.0 |
| BTC 3 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 79 | -54.4 | -108.8 | -77.4 | 54.4 | -0.29 / -0.58 / -0.41 | 323.3 / 268.9 |
| BTC 4 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | gross-positive, cost-negative pre-2023 | 157 | 3.0 | -51.3 | -19.1 | 54.4 | 0.02 / -0.41 / -0.15 | 231.3 / 177.0 |
| BTC 5 (diag) entry 15:10 (close-50m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 82 | -116.5 | -170.8 | -139.5 | 54.4 | -0.58 / -0.84 / -0.69 | 201.0 / 146.6 |
| ETH 1 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 149 | -37.8 | -92.1 | -77.6 | 54.4 | -0.50 / -1.21 / -1.03 | 152.5 / 98.2 |
| ETH 2 (diag) entry 15:20 (close-40m) |px-prior RTH close|>=0.7ADR against exit 15:55 | negative pre-2023 | 86 | -13.4 | -67.7 | -52.2 | 54.4 | -0.12 / -0.59 / -0.46 | 137.4 / 83.0 |
| ETH 3 (diag) entry 15:10 (close-50m) |px-prior RTH close|>=0.4ADR against exit 15:55 | negative pre-2023 | 155 | -29.7 | -84.0 | -69.7 | 54.4 | -0.34 / -0.95 / -0.80 | 91.2 / 36.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6B: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6C: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6E: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6J: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); BTC: 2 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.34, p(top) = 0.52); CL: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00); ES: 5 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.00, p(top) = 0.30); ETH: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00); HE: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); HG: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); HO: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00); LE: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); NG: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); NQ: 6 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.00, p(top) = 0.04); PL: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); RB: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00); RTY: 3 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.05, p(top) = 0.32); SI: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); YM: 1 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.66, p(top) = 0.22); ZB: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZF: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZS: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZT: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZW: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 17 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.29 (NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 5; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 4 (cell-share pairs).
- Gate-3 cell NQ entry 15:20 (close-40m) |px-prior RTH close|>=0.4ADR against exit 15:55: uplift +0.23/+0.40/+0.45, boot lo +0.10, plateau 1.00, 2x-slip +0.27, wd corr -0.20, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 16, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_11.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm11/ (`BM11_CO_all_selected_scored.csv`).

DONE BM11
