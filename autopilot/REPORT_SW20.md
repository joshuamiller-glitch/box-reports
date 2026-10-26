# REPORT SW20 - multi-day RTH flow persistence (D02 H5)

**Verdict: LEAD (strong, RTY only). The automatic 'FOUND-CANDIDATE' tag (RTY, section 7) was downgraded after verification. FOUND 0, LEAD 6, INSURANCE 0.** 56 selected cells (+9 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.32; best pair-window standalone Sharpe +1.73.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: day metric imb = sum(sign(c-o) v)/sum v or clv = sum(((c-l)-(h-c))/(h-l) v)/sum v over RTH rows; mean of the prior 1 or 3 days with |m| >= 0/0.02/0.05: enter at RTH open + 0/30 min with/against sign(m), hold to 16:55.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 48 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      48 |         48 |        22 |               1.799 |                2 |         10 |            0 |
| CL    |      48 |         44 |         2 |               0.918 |                2 |          2 |            3 |
| ES    |      48 |         48 |        18 |               1.196 |                2 |         10 |            0 |
| GC    |      48 |         44 |         4 |               1.204 |                2 |          4 |            3 |
| NQ    |      48 |         48 |        13 |               0.852 |                2 |         10 |            0 |
| RTY   |      48 |         48 |        19 |               2.165 |                2 |         10 |            0 |
| YM    |      48 |         44 |        11 |               1.033 |                2 |         10 |            0 |
| ZN    |      48 |         40 |         0 |              -0.123 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   18 |             8.79 |              17 |       0    |                       0.931 |            0.762 |           1.029 |     0.14 |       1.196 |                2.075 |
| NQ    |     100 |                   13 |            10.62 |              18 |       0.25 |                       0.604 |            0.861 |           1.143 |     0.92 |       0.852 |                2.011 |
| RTY   |     100 |                   19 |             8.56 |              16 |       0    |                       1.479 |            0.814 |           1.101 |     0    |       2.165 |                2.116 |
| YM    |     100 |                   11 |             9.03 |              16 |       0.29 |                       0.621 |            0.781 |           1.082 |     0.83 |       1.033 |                1.955 |
| GC    |     100 |                    4 |             8.56 |              16 |       0.98 |                       0.609 |            0.772 |           1.068 |     0.85 |       0.885 |                2.068 |
| CL    |     100 |                    2 |             7.16 |              11 |       1    |                       0.827 |            0.725 |           1.014 |     0.21 |       0.836 |                1.902 |
| ZN    |     100 |                    0 |             0.69 |               3 |       1    |                     nan     |            0.506 |           1.141 |   nan    |     nan     |                1.141 |
| BTC   |     100 |                   22 |            10.21 |              20 |       0    |                       1.338 |            0.806 |           1.083 |     0    |       1.799 |                2.005 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 117 | 2 | 1.20 | 0.23 | 0.39 | -1.07 / 1.52 | 0.23 / -0.10 / -0.25 | 0.05 | 0.22 | 0.86 | -0.11 | 0.75 | 156 | NO |
| ES 2 | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 117 | 2 | 1.17 | 0.12 | 0.71 | -0.24 / 1.32 | 0.20 / 0.15 / -0.18 | 0.09 | 0.06 | 0.89 | -0.06 | 0.50 | 156 | NO |
| ES 3 | clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 316 | 2 | 1.05 | -0.23 | 1.15 | 1.16 / 1.46 | 0.19 / 0.28 / 0.06 | 0.15 | -0.75 | 0.99 | 0.02 | 0.25 | 488 | NO |
| ES 4 | imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | 267 | 2 | 1.03 | 0.26 | 0.70 | -0.07 / 1.61 | 0.16 / 0.10 / -0.05 | 0.07 | -0.00 | 0.93 | -0.06 | 0.00 | 416 | NO |
| ES 5 | imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 125 | 2 | 0.96 | 0.16 | -0.02 | -1.07 / 1.36 | 0.16 / 0.07 / -0.55 | -0.06 | -0.09 | 0.57 | -0.28 | 0.00 | 197 | NO |
| ES 6 | imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | 404 | 2 | 0.90 | 0.30 | 0.70 | 0.15 / 1.26 | 0.15 / 0.17 / -0.18 | 0.04 | -0.23 | 0.91 | -0.08 | 0.00 | 643 | NO |
| ES 7 | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 125 | 2 | 0.78 | 0.21 | -0.27 | -1.55 / 1.38 | 0.13 / -0.27 / -0.55 | -0.11 | -0.03 | 0.43 | -0.33 | 0.00 | 197 | NO |
| ES 8 | clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | 211 | 2 | 0.76 | 0.08 | 0.64 | 0.14 / 1.30 | 0.14 / 0.06 / -0.13 | 0.06 | -0.53 | 0.91 | -0.03 | 1.00 | 308 | NO |
| ES 9 | clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | 316 | 2 | 0.75 | -0.08 | 0.84 | 0.85 / 1.44 | 0.14 / 0.23 / 0.04 | 0.11 | -0.68 | 0.93 | -0.02 | 0.25 | 488 | NO |
| ES 10 | clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 0.71 | 0.02 | 0.55 | 0.17 / 1.16 | 0.09 / 0.04 / -0.08 | 0.01 | -0.51 | 0.88 | -0.12 | 1.00 | 820 | NO |
| NQ 1 | clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 0.85 | 0.48 | 0.48 | -0.06 / 1.27 | 0.14 / -0.02 / -0.17 | 0.05 | -0.79 | 0.84 | -0.12 | 0.50 | 820 | NO |
| NQ 2 | imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | 256 | 2 | 0.79 | 0.36 | 0.80 | 0.77 / 1.21 | 0.13 / -0.04 / 0.14 | 0.10 | -0.44 | 0.93 | -0.02 | 0.00 | 411 | NO |
| NQ 3 | clv prior3d |m|>=0.0 RTHopen+30 dir=against hold=flat | 513 | 2 | 0.78 | 0.59 | 0.57 | 0.22 / 1.36 | 0.13 / -0.10 / 0.01 | 0.07 | -0.80 | 0.85 | -0.09 | 0.50 | 820 | NO |
| NQ 4 | imb prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | 256 | 2 | 0.67 | 0.47 | 0.57 | 0.33 / 1.47 | 0.09 / 0.00 / 0.04 | 0.06 | -0.31 | 0.85 | -0.07 | 0.00 | 411 | NO |
| NQ 5 | clv prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | 396 | 2 | 0.56 | 0.75 | 0.83 | 1.20 / 1.55 | 0.09 / 0.15 / 0.08 | 0.10 | -0.64 | 0.93 | -0.03 | 0.50 | 616 | LEAD |
| NQ 6 | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 139 | 2 | 0.55 | 0.45 | 0.68 | 0.81 / 1.32 | 0.08 / -0.06 / 0.43 | 0.12 | -0.52 | 0.91 | -0.05 | 0.25 | 194 | NO |
| NQ 7 | clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 139 | 2 | 0.52 | 0.41 | 0.47 | 0.30 / 1.33 | 0.09 / -0.08 / 0.33 | 0.10 | -0.63 | 0.83 | -0.05 | 0.00 | 194 | NO |
| NQ 8 | imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | 515 | 2 | 0.46 | 0.33 | 0.39 | 0.15 / 1.43 | 0.06 / -0.14 / 0.14 | 0.04 | -0.69 | 0.80 | -0.10 | 0.00 | 824 | NO |
| NQ 9 | imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | 393 | 2 | 0.44 | 0.45 | 0.46 | 0.34 / 1.54 | 0.05 / -0.17 / 0.18 | 0.03 | -0.76 | 0.82 | -0.10 | 1.00 | 633 | NO |
| NQ 10 | clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | 358 | 2 | 0.43 | 0.41 | 0.36 | 0.15 / 1.18 | 0.07 / -0.02 / 0.08 | 0.05 | -0.49 | 0.82 | -0.10 | 0.50 | 536 | NO |
| RTY 1 | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 106 | 2 | 2.17 | 0.34 | 1.73 | 1.22 / 1.22 | 0.36 / -0.10 / 0.42 | 0.30 | -0.16 | 1.00 | 0.13 | 0.00 | 180 | NO |
| RTY 2 | clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 106 | 2 | 1.84 | 0.44 | 1.45 | 0.98 / 1.53 | 0.31 / 0.10 / 0.15 | 0.24 | 0.21 | 1.00 | 0.07 | 0.00 | 180 | NO |
| RTY 3 | imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 180 | 2 | 1.83 | 0.76 | 1.05 | 0.52 / 1.42 | 0.27 / 1.04 / -0.37 | 0.20 | -0.12 | 0.96 | -0.01 | 1.00 | 280 | NO |
| RTY 4 | clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 316 | 2 | 1.49 | 0.23 | 0.52 | -0.45 / 1.21 | 0.25 / -0.42 / 0.01 | 0.08 | -0.14 | 0.87 | -0.10 | 0.75 | 515 | NO |
| RTY 5 | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 180 | 2 | 1.41 | 0.99 | 0.75 | 0.27 / 1.34 | 0.21 / 0.74 / -0.40 | 0.12 | -0.14 | 0.93 | -0.09 | 0.75 | 280 | NO |
| RTY 6 | imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 361 | 2 | 1.37 | 0.34 | 1.08 | 0.97 / 1.41 | 0.18 / 0.49 / 0.19 | 0.18 | 0.09 | 0.96 | 0.02 | 0.75 | 579 | FOUND-CAND |
| RTY 7 | imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | 515 | 2 | 1.20 | 0.49 | 0.94 | 0.59 / 1.09 | 0.14 / -0.15 / 0.14 | 0.07 | 0.06 | 0.97 | -0.07 | 0.00 | 824 | NO |
| RTY 8 | imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 1.18 | 0.44 | 0.86 | 0.64 / 1.25 | 0.14 / 0.26 / 0.18 | 0.12 | 0.25 | 0.98 | -0.04 | 0.50 | 820 | LEAD |
| RTY 9 | clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | 316 | 2 | 1.17 | 0.53 | 0.36 | -0.33 / 1.55 | 0.19 / -0.17 / -0.18 | 0.04 | -0.04 | 0.81 | -0.15 | 0.50 | 515 | NO |
| RTY 10 | imb prior1d |m|>=0.0 RTHopen+0 dir=against hold=flat | 515 | 2 | 1.14 | 0.27 | 0.94 | 0.72 / 1.50 | 0.13 / -0.16 / 0.20 | 0.07 | -0.00 | 0.95 | -0.07 | 0.00 | 824 | NO |
| YM 1 | clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | 169 | 2 | 1.03 | 0.33 | 0.56 | -0.59 / 1.42 | 0.14 / 0.04 / -0.15 | 0.04 | -0.15 | 0.96 | -0.06 | 0.50 | 266 | NO |
| YM 2 | clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 0.89 | 0.02 | 0.93 | 0.88 / 1.28 | 0.13 / 0.21 / 0.17 | 0.13 | -0.26 | 0.95 | -0.01 | 0.00 | 820 | LEAD |
| YM 3 | clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | 169 | 2 | 0.83 | 0.57 | 0.37 | -0.71 / 1.73 | 0.11 / -0.00 / -0.17 | 0.01 | -0.13 | 0.83 | -0.10 | 0.50 | 266 | NO |
| YM 4 | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 129 | 2 | 0.66 | 0.32 | 0.66 | 0.68 / 1.42 | 0.13 / -0.00 / 0.36 | 0.14 | -0.36 | 0.90 | -0.05 | 0.25 | 208 | NO |
| YM 5 | clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 277 | 2 | 0.63 | -0.07 | 1.06 | 1.62 / 1.44 | 0.14 / 0.61 / 0.08 | 0.19 | -0.41 | 0.97 | 0.05 | 0.50 | 431 | NO |
| YM 6 | clv prior3d |m|>=0.0 RTHopen+30 dir=against hold=flat | 513 | 2 | 0.49 | 0.04 | 0.66 | 0.82 / 1.72 | 0.07 / 0.19 / 0.23 | 0.09 | -0.15 | 0.86 | -0.07 | 0.00 | 820 | NO |
| YM 7 | imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 129 | 2 | 0.47 | 0.28 | 0.54 | 0.64 / 1.52 | 0.08 / 0.05 / 0.28 | 0.11 | -0.20 | 0.82 | -0.08 | 0.25 | 208 | NO |
| YM 8 | imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 513 | 2 | 0.44 | -0.16 | 0.35 | 0.27 / 1.11 | 0.08 / 0.06 / 0.09 | 0.05 | -0.60 | 0.83 | -0.08 | 0.00 | 820 | NO |
| YM 9 | clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | 277 | 2 | 0.40 | 0.13 | 0.80 | 1.42 / 1.56 | 0.10 / 0.50 / 0.11 | 0.14 | -0.55 | 0.92 | 0.00 | 0.75 | 431 | LEAD |
| YM 10 | imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 306 | 2 | 0.36 | 0.11 | 0.32 | 0.28 / 1.61 | 0.09 / -0.00 / 0.12 | 0.07 | -0.05 | 0.69 | -0.11 | 0.50 | 512 | NO |
| GC 1 | imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 516 | 2 | 0.89 | -0.33 | 0.46 | 0.37 / 1.42 | 0.09 / -0.22 / -0.09 | -0.01 | -0.12 | 0.88 | -0.31 | 0.50 | 822 | NO |
| GC 2 | clv prior1d |m|>=0.02 RTHopen+0 dir=against hold=flat | 345 | 2 | 0.77 | 0.06 | 0.74 | 0.98 / 1.64 | 0.12 / 0.38 / 0.13 | 0.16 | 0.38 | 0.88 | -0.14 | 1.00 | 544 | LEAD |
| GC 3 | clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | 122 | 2 | 0.41 | -0.16 | 0.88 | 1.35 / 1.40 | 0.06 / 1.70 / -0.15 | 0.23 | 0.20 | 0.97 | -0.05 | 0.50 | 207 | NO |
| GC 4 | clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | 122 | 2 | 0.37 | -0.06 | 0.92 | 1.49 / 1.37 | 0.05 / 1.69 / -0.06 | 0.24 | 0.21 | 0.99 | -0.07 | 0.00 | 207 | NO |
| GC 5 (diag) | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 24 | 1 | 1.20 | 0.11 | 0.97 | 1.05 / 1.61 | 0.19 / 0.15 / 0.18 | 0.20 | 0.03 | 0.95 | -0.15 | 1.00 | 49 S | diag |
| GC 6 (diag) | imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 363 | 1 | 0.94 | -0.16 | 0.47 | 0.34 / 1.75 | 0.10 / -0.23 / 0.02 | 0.02 | 0.15 | 0.82 | -0.29 | 1.00 | 578 | diag |
| GC 7 (diag) | clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 23 | 1 | 0.70 | 0.32 | 0.61 | 0.72 / 1.45 | 0.12 / 0.74 / -0.49 | 0.09 | 0.04 | 0.84 | -0.33 | 0.75 | 48 S | diag |
| CL 1 | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 117 | 2 | 0.84 | 0.02 | 0.61 | 0.54 / 1.33 | 0.11 / -0.11 / -0.04 | 0.02 | -0.22 | 0.90 | -0.20 | 0.75 | 194 | NO |
| CL 2 | imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 117 | 2 | 0.82 | 0.05 | 0.63 | 0.58 / 1.25 | 0.12 / -0.10 / 0.07 | 0.05 | -0.13 | 0.94 | -0.16 | 0.75 | 194 | NO |
| CL 3 (diag) | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 41 | 1 | 0.92 | 0.07 | 0.79 | 0.84 / 1.31 | 0.11 / -0.16 / 0.29 | 0.11 | -0.03 | 0.97 | -0.10 | 0.00 | 69 S | diag |
| CL 4 (diag) | imb prior1d |m|>=0.02 RTHopen+0 dir=against hold=flat | 413 | 1 | 0.89 | 0.02 | 0.58 | 0.46 / 1.02 | 0.12 / 0.03 / -0.13 | -0.00 | -0.37 | 0.92 | -0.17 | 0.50 | 654 | diag |
| CL 5 (diag) | imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | 413 | 1 | 0.87 | -0.16 | 0.68 | 0.70 / 1.67 | 0.10 / 0.03 / -0.04 | 0.00 | -0.33 | 0.90 | -0.16 | 0.50 | 654 | diag |
| ZN 1 (diag) | clv prior3d |m|>=0.05 RTHopen+30 dir=with hold=flat | 95 | 1 | -0.12 | -0.71 | -0.66 | -1.36 / 0.41 | -0.07 / -0.84 / -0.15 | -0.40 | 0.09 | 0.54 | -0.40 | 0.00 | 177 | diag |
| ZN 2 (diag) | clv prior3d |m|>=0.05 RTHopen+0 dir=with hold=flat | 96 | 1 | -0.35 | -0.72 | -0.90 | -1.70 / 0.65 | -0.09 / -0.80 / -0.25 | -0.38 | 0.04 | 0.31 | -0.42 | 0.00 | 177 | diag |
| ZN 3 (diag) | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 96 | 1 | -0.55 | -0.76 | -0.80 | -1.44 / 0.27 | -0.11 / -0.38 / -0.15 | -0.30 | 0.16 | 0.54 | -0.34 | 0.00 | 186 | diag |
| BTC 1 | clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 117 | 2 | 1.80 | 1.04 | 1.02 | -0.47 / 1.45 | 0.39 / 0.45 / -0.31 | 0.22 | -0.31 | 0.96 | 0.04 | 0.75 | 175 | NO |
| BTC 2 | imb prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | 387 | 2 | 1.40 | -0.35 | 0.52 | -0.26 / 1.48 | 0.28 / 0.04 / -0.12 | 0.13 | -0.19 | 0.85 | -0.06 | 0.50 | 596 | NO |
| BTC 3 | imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | 339 | 2 | 1.38 | -0.20 | 0.29 | -1.84 / 1.52 | 0.25 / -0.51 / -0.17 | 0.03 | -0.36 | 0.76 | -0.13 | 0.50 | 516 | NO |
| BTC 4 | clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | 442 | 2 | 1.37 | 1.29 | 0.34 | -1.53 / 1.56 | 0.33 / -0.39 / -0.23 | 0.09 | -0.31 | 0.76 | -0.09 | 0.50 | 686 | NO |
| BTC 5 | imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 349 | 2 | 1.35 | 0.38 | 0.79 | 0.25 / 1.35 | 0.27 / 0.33 / -0.11 | 0.17 | -0.19 | 0.95 | -0.01 | 0.50 | 537 | NO |
| BTC 6 | clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | 290 | 2 | 1.31 | 1.71 | 0.51 | -1.20 / 1.34 | 0.33 / -0.27 / -0.20 | 0.12 | -0.35 | 0.90 | -0.04 | 0.50 | 432 | NO |
| BTC 7 | imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 226 | 2 | 1.28 | 0.32 | 0.47 | -0.68 / 1.37 | 0.25 / -0.28 / -0.09 | 0.08 | -0.15 | 0.85 | -0.09 | 1.00 | 322 | NO |
| BTC 8 | imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | 493 | 2 | 1.20 | -0.35 | 0.13 | -1.99 / 1.20 | 0.21 / -0.43 / -0.30 | -0.02 | -0.12 | 0.71 | -0.17 | 0.00 | 768 | NO |
| BTC 9 | imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | 245 | 2 | 1.16 | -0.42 | 0.27 | -0.91 / 1.22 | 0.24 / -0.60 / -0.01 | 0.05 | -0.24 | 0.74 | -0.13 | 0.75 | 358 | NO |
| BTC 10 | clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | 213 | 2 | 1.15 | 0.98 | -0.20 | -2.82 / 1.18 | 0.24 / -0.68 / -0.37 | -0.05 | -0.43 | 0.34 | -0.23 | 0.00 | 322 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 56 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 5 / 5 / 5 |
| all-in uplift @20% > 0 (all scored) | 59 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 16 |
| worst-decile corr <= +0.30 | 64 |
| plateau >= 0.75 | 18 |
| all-in uplift at 2x slippage >= +0.10 | 25 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | clean | 1.79 | 3.45 | -112984 | -86612 | 234159 | -201005 | 6.93 | 18.1 | 1.85 | -82317 | 236422 | -96834 |
| BTC clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H1 | 1.35 | 2.59 | -102575 | -79311 | 145291 | -110873 | 1.99 | 21.4 | 3.27 | -74579 | 129764 | -78287 |
| BTC clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H2 | -2.15 | -2.24 | -153366 | -111775 | 504987 | -219352 | -1.00 | 41.7 | 2.17 | -85956 | 221073 | -86023 |
| BTC clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | all | 1.02 | 1.73 | -125005 | -94410 | 504987 | -219352 | 2.79 | 23.8 | 2.13 | -83467 | 236422 | -96834 |
| CL imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | clean | 0.86 | 1.24 | -158081 | -123279 | 577127 | -221203 | 1.35 | 21.9 | 1.58 | -84162 | 260991 | -99577 |
| CL imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H1 | -0.26 | -0.38 | -79574 | -70450 | 224034 | -81383 | -0.18 | 25.0 | 2.73 | -75747 | 157652 | -76932 |
| CL imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H2 | 0.83 | 2.22 | -227605 | -196892 | 722579 | -254002 | 1.16 | 36.1 | 2.55 | -97191 | 253063 | -100269 |
| CL imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | all | 0.63 | 1.35 | -180377 | -139733 | 722579 | -254002 | 2.18 | 25.6 | 1.98 | -86556 | 260991 | -100269 |
| ES clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | clean | 1.13 | 2.14 | -109219 | -86883 | 491194 | -189593 | 2.09 | 40.0 | 1.65 | -83857 | 255245 | -90892 |
| ES clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | H1 | 2.10 | 4.99 | -73022 | -65025 | 183713 | -77173 | 2.67 | 39.3 | 3.11 | -76800 | 166436 | -79111 |
| ES clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | H2 | 0.39 | 0.63 | -95197 | -86399 | 376181 | -97012 | 0.30 | 47.2 | 2.54 | -81694 | 210193 | -82530 |
| ES clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | all | 1.15 | 2.16 | -104324 | -86407 | 491194 | -189593 | 3.31 | 41.1 | 2.08 | -82969 | 255245 | -90892 |
| GC clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | clean | 0.29 | 0.40 | -164562 | -125598 | 744447 | -233455 | 0.36 | 31.4 | 1.51 | -83887 | 282113 | -112344 |
| GC clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | H1 | 2.67 | 6.58 | -220363 | -191729 | 696659 | -224332 | 2.58 | 35.7 | 4.51 | -52657 | 120642 | -69094 |
| GC clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | H2 | 0.48 | 0.78 | -312185 | -242882 | 1076033 | -395220 | 0.34 | 33.3 | 2.43 | -123312 | 293889 | -139248 |
| GC clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | all | 0.92 | 1.64 | -224971 | -175894 | 1076033 | -395220 | 2.26 | 32.7 | 2.15 | -92178 | 293889 | -139248 |
| NQ clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | clean | 0.59 | 0.85 | -152444 | -118465 | 498528 | -246460 | 1.08 | 22.9 | 1.54 | -81295 | 285606 | -94645 |
| NQ clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H1 | 0.01 | 0.01 | -127854 | -116229 | 373161 | -132029 | 0.00 | 17.9 | 2.77 | -77610 | 170527 | -78287 |
| NQ clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H2 | 1.32 | 2.14 | -155193 | -118178 | 250624 | -164135 | 1.77 | 13.9 | 2.91 | -78535 | 209237 | -79653 |
| NQ clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | all | 0.68 | 0.99 | -153290 | -121387 | 498528 | -246460 | 1.98 | 20.2 | 2.02 | -80348 | 285606 | -94645 |
| RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | clean | 2.15 | 6.81 | -68074 | -50473 | 167243 | -132546 | 11.68 | 20.0 | 1.82 | -82484 | 229678 | -99460 |
| RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H1 | 0.71 | 1.28 | -189939 | -156466 | 352447 | -210665 | 0.83 | 25.0 | 2.73 | -94531 | 158617 | -110775 |
| RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | H2 | 2.00 | 3.58 | -124453 | -84336 | 184451 | -177931 | 3.27 | 13.9 | 2.91 | -85206 | 207768 | -88314 |
| RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | all | 1.73 | 3.75 | -122176 | -85957 | 352447 | -210665 | 8.09 | 19.6 | 2.21 | -86347 | 229678 | -110775 |
| YM clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | clean | 0.69 | 1.16 | -114844 | -96419 | 614094 | -147965 | 1.02 | 39.0 | 1.60 | -83322 | 292180 | -91821 |
| YM clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | H1 | 3.38 | 9.81 | -65918 | -57901 | 103108 | -72552 | 8.16 | 28.6 | 3.44 | -74010 | 159738 | -77922 |
| YM clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | H2 | 0.28 | 0.39 | -136617 | -113889 | 496318 | -161712 | 0.18 | 30.6 | 2.57 | -81153 | 207667 | -82653 |
| YM clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | all | 1.06 | 1.80 | -117376 | -97966 | 614094 | -161712 | 2.54 | 35.1 | 2.10 | -82657 | 292180 | -91821 |
| ZN imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat (diag) | clean | -0.54 | -0.70 | -178229 | -129159 | 977069 | -241184 | -0.50 | 26.7 | 1.35 | -78131 | 288752 | -81874 |
| ZN imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat (diag) | H1 | -2.36 | -2.59 | -99922 | -92796 | 499740 | -115425 | -0.77 | 46.4 | 2.45 | -77610 | 168597 | -78287 |
| ZN imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat (diag) | H2 | -0.77 | -1.00 | -122756 | -90428 | 437410 | -126534 | -0.40 | 33.3 | 2.33 | -81935 | 210979 | -82679 |
| ZN imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat (diag) | all | -0.80 | -1.02 | -158923 | -119828 | 1690990 | -241184 | -0.62 | 31.5 | 1.74 | -79592 | 288752 | -82679 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | -12.2 | 5.5 | 19.3 | 31.3 | 4.8 / 17.9 | 28.4 / 31.6 | NO |
| NQ clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | -19.2 | 2.9 | 23.7 | 22.5 | 2.1 / 22.4 | 15.2 / 21.9 | NO |
| RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | 1.2 | -26.8 | 12.7 | 45.3 | -10.9 / 20.7 | -33.6 / -11.7 | NO |
| YM clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | -13.0 | 8.0 | 19.9 | 23.5 | 7.3 / 19.1 | 30.7 / 37.0 | NO |
| GC clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | -3.4 | -94.7 | -4.2 | -7.3 | -30.5 / 19.2 | -6.0 / 14.5 | NO |
| CL imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | -12.8 | -6.3 | 7.7 | 24.7 | -7.2 / 14.9 | 31.2 / 33.6 | NO |
| ZN imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat (diag) | -41.4 | 7.6 | 23.7 | 23.0 | 10.8 / 26.5 | 30.0 / 29.5 | NO |
| BTC clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | -14.6 | -1.4 | 20.8 | 33.3 | -2.2 / 21.4 | 30.0 / 35.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 325 | 77.1 | 47.8 | 60.4 | 29.4 | 0.37 / 0.23 / 0.29 | 251.7 / 222.3 |
| ES 2 clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 323 | 56.8 | 27.5 | 40.1 | 29.4 | 0.25 / 0.12 / 0.18 | 270.5 / 241.2 |
| ES 3 clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1351 | 2.7 | -26.7 | -13.0 | 29.4 | 0.03 / -0.23 / -0.11 | 249.7 / 220.4 |
| ES 4 imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1461 | 55.7 | 26.4 | 40.5 | 29.4 | 0.55 / 0.26 / 0.40 | 221.9 / 192.6 |
| ES 5 imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 762 | 54.0 | 24.6 | 38.3 | 29.4 | 0.35 / 0.16 / 0.25 | 191.0 / 161.6 |
| ES 6 imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2154 | 56.3 | 26.9 | 41.2 | 29.4 | 0.64 / 0.30 / 0.46 | 172.6 / 143.2 |
| ES 7 imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 764 | 61.5 | 32.1 | 45.8 | 29.4 | 0.40 / 0.21 / 0.30 | 166.5 / 137.1 |
| ES 8 clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 903 | 40.7 | 11.3 | 24.7 | 29.4 | 0.29 / 0.08 / 0.18 | 288.0 / 258.7 |
| ES 9 clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1356 | 19.9 | -9.5 | 4.2 | 29.4 | 0.19 / -0.08 / 0.04 | 178.3 / 149.0 |
| ES 10 clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 2674 | 31.0 | 1.6 | 15.9 | 29.4 | 0.36 / 0.02 / 0.19 | 137.3 / 107.9 |
| NQ 1 clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 2673 | 74.8 | 60.4 | 69.0 | 14.4 | 0.60 / 0.48 / 0.55 | 244.0 / 229.6 |
| NQ 2 imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1383 | 71.9 | 57.5 | 66.0 | 14.4 | 0.45 / 0.36 / 0.42 | 371.3 / 356.9 |
| NQ 3 clv prior3d |m|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2681 | 84.1 | 69.7 | 78.3 | 14.4 | 0.71 / 0.59 / 0.66 | 196.4 / 182.0 |
| NQ 4 imb prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1380 | 96.3 | 82.0 | 90.5 | 14.4 | 0.55 / 0.47 / 0.52 | 341.5 / 327.1 |
| NQ 5 clv prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1784 | 121.9 | 107.6 | 116.0 | 14.4 | 0.85 / 0.75 / 0.81 | 233.7 / 219.3 |
| NQ 6 clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 222 | 237.6 | 223.3 | 230.2 | 14.4 | 0.48 / 0.45 / 0.46 | 254.5 / 240.1 |
| NQ 7 clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 223 | 193.3 | 179.0 | 185.9 | 14.4 | 0.44 / 0.41 / 0.42 | 233.2 / 218.8 |
| NQ 8 imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2689 | 55.4 | 41.0 | 49.6 | 14.4 | 0.45 / 0.33 / 0.40 | 155.2 / 140.8 |
| NQ 9 imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2141 | 76.2 | 61.9 | 70.4 | 14.4 | 0.56 / 0.45 / 0.52 | 187.2 / 172.8 |
| NQ 10 clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1251 | 87.8 | 73.5 | 81.6 | 14.4 | 0.49 / 0.41 / 0.45 | 154.8 / 140.4 |
| RTY 1 clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 250 | 60.5 | 46.1 | 48.5 | 14.4 | 0.45 / 0.34 / 0.36 | 365.9 / 351.6 |
| RTY 2 clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 252 | 75.9 | 61.5 | 63.9 | 14.4 | 0.54 / 0.44 / 0.45 | 304.8 / 290.5 |
| RTY 3 imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 557 | 93.9 | 79.5 | 81.9 | 14.4 | 0.91 / 0.76 / 0.79 | 175.1 / 160.7 |
| RTY 4 clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 898 | 31.6 | 17.3 | 19.6 | 14.4 | 0.41 / 0.23 / 0.26 | 119.8 / 105.4 |
| RTY 5 imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 561 | 113.0 | 98.7 | 101.0 | 14.4 | 1.13 / 0.99 / 1.01 | 133.8 / 119.4 |
| RTY 6 imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1075 | 39.4 | 25.0 | 27.3 | 14.4 | 0.55 / 0.34 / 0.37 | 119.0 / 104.7 |
| RTY 7 imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1539 | 44.2 | 29.8 | 32.1 | 14.4 | 0.73 / 0.49 / 0.53 | 99.9 / 85.6 |
| RTY 8 imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1524 | 41.6 | 27.2 | 29.5 | 14.4 | 0.67 / 0.44 / 0.47 | 85.9 / 71.5 |
| RTY 9 clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 903 | 52.5 | 38.1 | 40.5 | 14.4 | 0.73 / 0.53 / 0.57 | 79.7 / 65.4 |
| RTY 10 imb prior1d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1529 | 33.3 | 18.9 | 21.1 | 14.4 | 0.49 / 0.27 / 0.31 | 101.7 / 87.3 |
| YM 1 clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 630 | 54.6 | 40.2 | 45.6 | 14.4 | 0.45 / 0.33 / 0.38 | 265.7 / 251.4 |
| YM 2 clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 2679 | 15.4 | 1.1 | 6.8 | 14.4 | 0.25 / 0.02 / 0.11 | 111.1 / 96.8 |
| YM 3 clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 633 | 78.7 | 64.3 | 69.7 | 14.4 | 0.70 / 0.57 / 0.62 | 182.9 / 168.6 |
| YM 4 imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 625 | 55.3 | 40.9 | 46.4 | 14.4 | 0.44 / 0.32 / 0.37 | 92.4 / 78.1 |
| YM 5 clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1126 | 6.4 | -8.0 | -2.6 | 14.4 | 0.07 / -0.07 / -0.02 | 91.1 / 76.8 |
| YM 6 clv prior3d |m|>=0.0 RTHopen+30 dir=against hold=flat | positive pre-2023 | 2684 | 16.8 | 2.4 | 8.2 | 14.4 | 0.29 / 0.04 / 0.14 | 63.6 / 49.3 |
| YM 7 imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 622 | 50.4 | 36.0 | 41.5 | 14.4 | 0.39 / 0.28 / 0.32 | 80.8 / 66.5 |
| YM 8 imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2679 | 4.5 | -9.9 | -4.1 | 14.4 | 0.07 / -0.16 / -0.07 | 46.3 / 32.0 |
| YM 9 clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | positive pre-2023 | 1131 | 26.2 | 11.9 | 17.2 | 14.4 | 0.28 / 0.13 / 0.19 | 61.4 / 47.1 |
| YM 10 imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1705 | 23.1 | 8.7 | 14.3 | 14.4 | 0.30 / 0.11 / 0.18 | 50.6 / 36.2 |
| GC 1 imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2666 | 0.8 | -23.5 | -13.7 | 24.4 | 0.02 / -0.33 / -0.19 | 98.8 / 74.4 |
| GC 2 clv prior1d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 1624 | 29.1 | 4.8 | 14.6 | 24.4 | 0.32 / 0.06 / 0.16 | 100.1 / 75.8 |
| GC 3 clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 572 | 1.0 | -23.3 | -13.5 | 24.4 | 0.02 / -0.16 / -0.09 | 109.9 / 85.6 |
| GC 4 clv prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 572 | 16.9 | -7.5 | 2.3 | 24.4 | 0.14 / -0.06 / 0.02 | 85.7 / 61.4 |
| GC 5 (diag) clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 166 | 50.6 | 26.2 | 35.9 | 24.4 | 0.21 / 0.11 / 0.15 | 556.7 / 532.3 |
| GC 6 (diag) imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 1836 | 10.1 | -14.2 | -4.4 | 24.4 | 0.13 / -0.16 / -0.05 | 119.7 / 95.4 |
| GC 7 (diag) clv prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 166 | 92.7 | 68.3 | 78.0 | 24.4 | 0.43 / 0.32 / 0.37 | 312.2 / 287.8 |
| CL 1 imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | positive pre-2023 | 746 | 26.6 | 2.2 | 4.7 | 24.4 | 0.23 / 0.02 / 0.04 | 127.9 / 103.6 |
| CL 2 imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 745 | 30.8 | 6.4 | 8.8 | 24.4 | 0.25 / 0.05 / 0.07 | 137.3 / 112.9 |
| CL 3 (diag) clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 122 | 50.5 | 26.1 | 28.3 | 24.4 | 0.14 / 0.07 / 0.08 | 331.0 / 306.6 |
| CL 4 (diag) imb prior1d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 2193 | 26.2 | 1.8 | 4.5 | 24.4 | 0.32 / 0.02 / 0.05 | 80.0 / 55.6 |
| CL 5 (diag) imb prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 2194 | 12.3 | -12.0 | -9.4 | 24.4 | 0.15 / -0.16 / -0.12 | 73.8 / 49.5 |
| ZN 1 (diag) clv prior3d |m|>=0.05 RTHopen+30 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 497 | 7.9 | -27.7 | -33.1 | 35.6 | 0.20 / -0.71 / -0.84 | 31.7 / -3.9 |
| ZN 2 (diag) clv prior3d |m|>=0.05 RTHopen+0 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 498 | 2.6 | -33.0 | -38.4 | 35.6 | 0.06 / -0.72 / -0.84 | 21.2 / -14.5 |
| ZN 3 (diag) imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | gross-positive, cost-negative pre-2023 | 666 | 5.8 | -29.8 | -35.1 | 35.6 | 0.15 / -0.76 / -0.89 | 7.0 / -28.6 |
| BTC 1 clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 78 | 576.0 | 521.6 | 553.6 | 54.4 | 1.15 / 1.04 / 1.11 | 1604.9 / 1550.6 |
| BTC 2 imb prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | negative pre-2023 | 282 | -34.0 | -88.4 | -55.9 | 54.4 | -0.13 / -0.35 / -0.22 | 537.9 / 483.5 |
| BTC 3 imb prior1d |m|>=0.05 RTHopen+30 dir=against hold=flat | negative pre-2023 | 246 | -6.7 | -61.1 | -28.7 | 54.4 | -0.02 / -0.20 / -0.09 | 754.3 / 699.9 |
| BTC 4 clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat | positive pre-2023 | 339 | 373.1 | 318.7 | 351.3 | 54.4 | 1.51 / 1.29 / 1.42 | 709.8 / 655.5 |
| BTC 5 imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 256 | 156.3 | 102.0 | 134.5 | 54.4 | 0.57 / 0.38 / 0.49 | 634.2 / 579.8 |
| BTC 6 clv prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat | positive pre-2023 | 224 | 552.9 | 498.5 | 530.9 | 54.4 | 1.90 / 1.71 / 1.83 | 822.8 / 768.5 |
| BTC 7 imb prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 159 | 173.1 | 118.8 | 150.9 | 54.4 | 0.46 / 0.32 / 0.40 | 800.4 / 746.1 |
| BTC 8 imb prior1d |m|>=0.0 RTHopen+30 dir=against hold=flat | negative pre-2023 | 368 | -28.6 | -83.0 | -50.4 | 54.4 | -0.13 / -0.35 / -0.22 | 536.8 / 482.5 |
| BTC 9 imb prior3d |m|>=0.05 RTHopen+30 dir=against hold=flat | negative pre-2023 | 170 | -105.9 | -160.2 | -128.0 | 54.4 | -0.28 / -0.42 / -0.34 | 640.7 / 586.4 |
| BTC 10 clv prior1d |m|>=0.05 RTHopen+0 dir=against hold=flat | positive pre-2023 | 150 | 456.8 | 402.5 | 435.5 | 54.4 | 1.11 / 0.98 / 1.06 | 817.5 / 763.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 22 cells pass the clean rule against a replicate mean of 10.2 (p(count) = 0.00, p(top) = 0.00); CL: 2 cells pass the clean rule against a replicate mean of 7.2 (p(count) = 1.00, p(top) = 0.21); ES: 18 cells pass the clean rule against a replicate mean of 8.8 (p(count) = 0.00, p(top) = 0.14); GC: 4 cells pass the clean rule against a replicate mean of 8.6 (p(count) = 0.98, p(top) = 0.85); NQ: 13 cells pass the clean rule against a replicate mean of 10.6 (p(count) = 0.25, p(top) = 0.92); RTY: 19 cells pass the clean rule against a replicate mean of 8.6 (p(count) = 0.00, p(top) = 0.00); YM: 11 cells pass the clean rule against a replicate mean of 9.0 (p(count) = 0.29, p(top) = 0.83); ZN: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00).
- Of 56 selected cells, 5 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.32 (RTY clv prior3d |m|>=0.05 RTHopen+0 dir=against hold=flat); bootstrap lower bound > 0 for 7 cells; plateau >= 0.75 for 15; 2x-slippage all-in uplift >= +0.10 for 23; gate_add PASS at some share: 1 (cell-share pairs).
- Gate-3 cell RTY imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat: uplift +0.18/+0.49/+0.19, boot lo +0.02, plateau 0.75, 2x-slip +0.18, wd corr +0.09, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY imb prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat: uplift +0.14/+0.26/+0.18, boot lo -0.04, plateau 0.50, 2x-slip +0.12, wd corr +0.25, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM clv prior3d |m|>=0.0 RTHopen+0 dir=against hold=flat: uplift +0.13/+0.21/+0.17, boot lo -0.01, plateau 0.00, 2x-slip +0.13, wd corr -0.26, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell YM clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat: uplift +0.10/+0.50/+0.11, boot lo +0.00, plateau 0.75, 2x-slip +0.14, wd corr -0.55, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell GC clv prior1d |m|>=0.02 RTHopen+0 dir=against hold=flat: uplift +0.12/+0.38/+0.13, boot lo -0.14, plateau 1.00, 2x-slip +0.16, wd corr +0.38, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 45, 'gross-positive, cost-negative pre-2023': 7, 'negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_20.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw20/ (`SW20_CO_all_selected_scored.csv`).

## 7. Verification of the automatic FOUND-CANDIDATE: RTY, 'imb prior3d |m|>=0.02, RTH open, AGAINST the sign, hold to the 16:55 flatten' (cell 17)
Verdict: **LEAD (strong inside RTY, does not transfer), not FOUND-PENDING.**
- Rule: m_d = sum(sign(close-open) x volume)/sum(volume) over the RTH rows of a label day (bar proxy for signed flow); mean of the prior 3 label days; if |m| >= 0.02 enter at the RTH open (09:30 ET) AGAINST sign(m) (a fade of three days of net buying/selling), exit at the 16:55 flatten. Trades 361 in the clean span, 579 in the pair window.
- Gates at 20% share: additive uplift clean/H1/H2 +0.18/+0.49/+0.19, boot lo +0.017, worst week +12.7%, standalone pair-window Sharpe 1.08 vs own null p95 0.83 (rank 0.96), 2x-slip +0.18, wd corr +0.09, plateau 3 of 4. It passes at 20% ONLY: at 10% the clean uplift is +0.0997 (just under +0.10), at 30% boot lo -0.008, at 50% boot lo -0.12.
- ERA: positive pre-2023 (weekly Sharpe +0.34 net, 1,075 trades, +$25 net per trade at 1 contract; per-year 2017 +0.29, 2018 -0.64, 2019 -0.44, 2020 +0.74, 2021 +0.38, 2022 +1.80, 2023 +0.20, 2024 +1.71, 2025 +0.33, 2026 +1.28). This is the best ERA record of any SW cell.
- Grid structure: the RTY SW20 grid shows structure beyond chance (19 cells pass the clean rule vs replicate mean 8.6, p(count) 0.00; top-10 mean 1.48 vs replicate p95 1.10, p(top) 0.00; best cell 2.17 vs replicate-best p95 2.12), but the ten selected RTY cells are one idea (against, flat hold, prior 3 days, RTH open) and the best of them (clv prior3d >= 0.05) failed H1.
- Replication: H0 (2023-02-10..07-31) sleeve Sharpe -0.02, uplift -0.03 (FAIL, marginal); alternating months odd +0.11 / even +0.32 (both >= 50% of the all-in 0.205 -> 0.10; PASS); same cell on other instruments does not replicate: ES -0.13/-0.27 uplift in H1/H2, NQ -0.07 clean, YM +0.09/0.00/+0.08, GC -0.35 in H1, BTC +0.28/+0.31/-0.12 (R3 FAIL). One of three replications passes, so by the K4v2 convention this would be FOUND-PENDING; it is NOT labelled that way because it passes only at one share, H1+H2 standalone Sharpe (0.97) is below its null p95 (1.41, rank 0.89), the signal is the bar-volume proxy of flow (not aggressor volume) and it does not appear in the neighbouring equity indices.
- Executability: RTY (M2K for size) market order at 09:30 ET open, exit 16:55; no stop (worst single trade -$5,879 per RTY contract; the sleeve is 28 contracts at 100% of pair sigma, 5.7 contracts at 20% share). Margin unverified.
```
== R1/R2 on RTY cell 17 imb prior3d |m|>=0.02 RTHopen+0 dir=against hold=flat scale 27.96
                        n_wk  sleeve_sh  pair_sh  uplift
H0 2023-02..07          25.0      -0.02     0.72   -0.03
clean                  104.0       1.37     1.39    0.21
H1                      28.0       0.76     3.09    0.41
H2                      35.0       0.81     2.40    0.19
odd months 2023-08..    85.0       0.47     2.22    0.11
even months 2023-08..   83.0       1.63     1.55    0.32
per-year weekly Sharpe (sleeve standalone): {2017: 0.29, 2018: -0.64, 2019: -0.44, 2020: 0.74, 2021: 0.38, 2022: 1.8, 2023: 0.2, 2024: 1.71, 2025: 0.33, 2026: 1.28}
== R3 same cell, other instruments (no re-selection)
   sym  scale  sh_pre2023  sh_clean  sh_H1  sh_H2  up_clean  up_H1  up_H2  H0_sh
0   ES   19.7       -0.04      0.34  -0.97  -1.50      0.05  -0.13  -0.27   0.69
1   NQ    8.9        0.46     -0.21   0.44   0.09     -0.07   0.23   0.01   1.32
2   YM   30.2        0.11      0.36   0.37   0.02      0.09   0.00   0.08   0.51
3   GC   20.4       -0.17      0.94   0.02   0.37      0.12  -0.35   0.01   3.01
4   CL   30.2       -0.24      0.52  -0.23   1.83      0.07  -0.14   0.42   0.54
5   ZN   93.5       -1.25     -1.59  -2.50   0.29     -0.33  -0.37   0.05   0.32
6  BTC    5.6        0.35      1.35   0.40  -0.35      0.28   0.31  -0.12   1.36

```

DONE SW20
