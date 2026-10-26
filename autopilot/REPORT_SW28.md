# REPORT SW28 - opening-activity regime x first-15-min / gap direction (D08 H4)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 20 selected cells (+21 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.32; best pair-window standalone Sharpe +1.24.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: first-15-RTH-minute volume / median of the prior 20 days hi (>= 1.5/2.0) or lo (<= 0.8/0.65); enter at RTH open + 15 min with/against the first-15-min move or the overnight gap direction; hold to the flatten or 120 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 32 cells per instrument (many instruments will have < 100 clean trades: then DIAGNOSTIC only).
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      32 |         24 |         4 |               1.577 |                2 |          4 |            3 |
| CL    |      32 |          8 |         1 |               1.492 |                2 |          1 |            3 |
| ES    |      32 |          8 |         2 |               0.923 |                2 |          2 |            3 |
| GC    |      32 |         24 |         7 |               1.91  |                2 |          7 |            3 |
| NQ    |      32 |          0 |         0 |               1.234 |                2 |          0 |            0 |
| RTY   |      32 |          8 |         2 |               1.43  |                2 |          2 |            3 |
| YM    |      32 |          8 |         4 |               1.931 |                2 |          4 |            3 |
| ZN    |      32 |         32 |         0 |              -0.01  |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    2 |             0.76 |               3 |       0.22 |                       0.374 |            0.683 |           1.127 |     0.46 |       0.408 |                1.558 |
| NQ    |     100 |                    0 |             0.09 |               1 |       1    |                     nan     |            0.785 |           1.544 |   nan    |     nan     |                1.544 |
| RTY   |     100 |                    2 |             0.05 |               1 |       0    |                       0.499 |            0.628 |           0.751 |     0.05 |       0.603 |                0.751 |
| YM    |     100 |                    4 |             1    |               5 |       0.02 |                       1.235 |            0.713 |           1.137 |     0.03 |       1.931 |                1.393 |
| GC    |     100 |                    7 |             3.03 |               7 |       0.03 |                       0.828 |            0.719 |           1.114 |     0.31 |       1.398 |                1.72  |
| CL    |     100 |                    1 |             1.29 |               4 |       0.71 |                       0.466 |            0.657 |           1.139 |     0.52 |       0.466 |                1.367 |
| ZN    |     100 |                    0 |             0.3  |               3 |       1    |                     nan     |            0.561 |           0.806 |   nan    |     nan     |                1.061 |
| BTC   |     100 |                    4 |             3.43 |              10 |       0.46 |                       0.449 |            0.709 |           1.067 |     0.84 |       0.812 |                1.693 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | 117 | 2 | 0.41 | -0.31 | -0.04 | -0.66 / 1.15 | 0.11 / -0.26 / 0.05 | 0.02 | -0.35 | 0.53 | -0.14 | 0.50 | 168 | NO |
| ES 2 | RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=120m | 117 | 2 | 0.34 | -0.15 | -0.28 | -1.44 / 1.41 | 0.14 / -0.06 / -0.30 | -0.02 | 0.19 | 0.51 | -0.14 | 0.50 | 168 | NO |
| ES 3 (diag) | RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | 54 | 1 | 0.92 | 0.14 | 0.21 | -1.88 / 1.42 | 0.13 / -0.13 / -0.31 | -0.02 | 0.39 | 0.70 | -0.16 | 0.00 | 77 S | diag |
| ES 4 (diag) | RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=flat | 49 | 2 | 0.86 | -0.24 | 0.78 | 0.39 / 1.25 | 0.15 / -0.12 / 0.04 | 0.08 | -0.57 | 0.92 | -0.06 | 0.50 | 70 S | diag |
| ES 5 (diag) | RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=120m | 49 | 2 | 0.74 | -0.74 | 0.95 | 1.56 / 1.53 | 0.07 / 0.11 / 0.21 | 0.08 | 0.30 | 0.98 | -0.04 | 0.75 | 70 S | diag |
| RTY 1 | RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | 104 | 2 | 0.60 | 0.19 | -0.61 | -2.02 / 1.56 | 0.12 / -0.84 / -0.37 | -0.14 | 0.53 | 0.16 | -0.35 | 0.00 | 155 | NO |
| RTY 2 | RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=120m | 104 | 2 | 0.40 | -0.28 | -0.62 | -2.08 / 1.23 | 0.08 / -0.62 / -0.45 | -0.16 | 0.42 | 0.21 | -0.35 | 0.00 | 155 | NO |
| RTY 3 (diag) | RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | 47 | 2 | 1.43 | 0.17 | 0.45 | -1.25 / 1.50 | 0.26 / -0.44 / -0.30 | 0.03 | 0.53 | 0.82 | -0.16 | 0.00 | 71 S | diag |
| RTY 4 (diag) | RTHopen+15 ref=ft open15vol hi1.5 dir=against hold=120m | 39 | 2 | 1.28 | -0.05 | 0.91 | 0.16 / 1.49 | 0.22 / -0.16 / 0.01 | 0.12 | -0.54 | 0.98 | -0.02 | 0.50 | 51 S | diag |
| RTY 5 (diag) | RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=120m | 47 | 2 | 1.19 | -0.07 | 0.29 | -1.82 / 1.08 | 0.19 / -0.29 / -0.34 | -0.01 | 0.46 | 0.81 | -0.17 | 0.25 | 71 S | diag |
| YM 1 | RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | 125 | 2 | 1.93 | -0.41 | 1.12 | -0.02 / 1.04 | 0.36 / -0.16 / 0.05 | 0.19 | -0.26 | 0.99 | -0.00 | 0.25 | 188 | NO |
| YM 2 | RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=flat | 125 | 2 | 1.45 | -0.32 | 0.74 | -0.60 / 1.22 | 0.22 / -0.30 / -0.04 | 0.06 | 0.23 | 0.95 | -0.10 | 0.50 | 188 | NO |
| YM 3 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | 124 | 2 | 0.79 | 0.38 | 0.06 | -0.90 / 1.39 | 0.14 / 0.24 / -0.70 | -0.05 | 0.29 | 0.56 | -0.24 | 0.00 | 187 | NO |
| YM 4 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | 124 | 2 | 0.76 | -0.09 | 0.09 | -1.00 / 0.73 | 0.17 / 0.19 / -0.68 | -0.02 | -0.16 | 0.70 | -0.19 | 0.00 | 187 | NO |
| YM 5 (diag) | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | 52 | 2 | 1.46 | 0.20 | 0.63 | -0.75 / 1.47 | 0.31 / 0.23 / -0.47 | 0.12 | 0.07 | 0.86 | -0.03 | 0.00 | 78 S | diag |
| YM 6 (diag) | RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=120m | 37 | 2 | 1.19 | -0.21 | 1.07 | 0.82 / 1.10 | 0.18 / 0.32 / 0.06 | 0.16 | 0.50 | 1.00 | 0.02 | 0.50 | 52 S | diag |
| YM 7 (diag) | RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=flat | 37 | 2 | 1.03 | 0.06 | 1.00 | 1.05 / 1.75 | 0.14 / 0.20 / 0.03 | 0.12 | 0.04 | 1.00 | 0.02 | 0.00 | 52 S | diag |
| GC 1 | RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | 178 | 2 | 1.40 | -0.40 | 1.15 | 1.13 / 1.37 | 0.26 / 0.02 / 0.67 | 0.30 | -0.47 | 0.98 | 0.04 | 0.00 | 282 | NO |
| GC 2 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | 175 | 2 | 1.03 | -0.67 | 0.06 | -0.48 / 1.56 | 0.16 / -0.50 / -0.92 | -0.20 | 0.52 | 0.58 | -0.62 | 0.00 | 279 | NO |
| GC 3 | RTHopen+15 ref=gap open15vol hi1.5 dir=with hold=flat | 118 | 2 | 0.95 | 0.15 | 1.23 | 1.67 / 1.29 | 0.10 / 1.61 / 0.21 | 0.29 | 0.27 | 0.99 | -0.04 | 0.00 | 198 | LEAD |
| GC 4 | RTHopen+15 ref=ft open15vol hi1.5 dir=against hold=120m | 118 | 2 | 0.76 | -0.81 | 0.42 | 0.29 / 1.57 | 0.13 / -0.68 / 0.53 | 0.07 | 0.12 | 0.90 | -0.26 | 0.50 | 197 | NO |
| GC 5 | RTHopen+15 ref=gap open15vol hi1.5 dir=with hold=120m | 118 | 2 | 0.67 | 0.43 | 1.01 | 1.41 / 1.57 | 0.09 / 0.70 / -0.01 | 0.13 | 0.22 | 0.99 | -0.11 | 0.50 | 198 | NO |
| GC 6 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | 175 | 2 | 0.66 | -0.44 | 0.35 | 0.34 / 1.49 | 0.12 / -0.89 / -0.30 | -0.16 | -0.02 | 0.74 | -0.58 | 0.00 | 279 | NO |
| GC 7 | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | 122 | 2 | 0.33 | -0.64 | 0.53 | 0.74 / 1.41 | 0.09 / -0.65 / 0.04 | -0.05 | -0.38 | 0.89 | -0.41 | 0.00 | 174 | NO |
| GC 8 (diag) | RTHopen+15 ref=ft open15vol hi2.0 dir=against hold=120m | 57 | 2 | 1.91 | -0.53 | 1.24 | 0.92 / 1.43 | 0.35 / 0.24 / 0.37 | 0.34 | 0.19 | 1.00 | 0.06 | 0.75 | 102 | diag |
| GC 9 (diag) | RTHopen+15 ref=ft open15vol hi2.0 dir=against hold=flat | 57 | 2 | 1.49 | -0.42 | 0.84 | 0.80 / 1.60 | 0.28 / -0.20 / 0.24 | 0.23 | 0.24 | 0.91 | -0.16 | 0.50 | 102 | diag |
| GC 10 (diag) | RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | 122 | 1 | 1.15 | -0.23 | 1.20 | 1.36 / 1.78 | 0.26 / -0.38 / 1.15 | 0.36 | -0.45 | 0.96 | 0.10 | 0.50 | 174 | diag |
| CL 1 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | 134 | 2 | 0.47 | -0.16 | 0.16 | -0.29 / 0.89 | 0.11 / -0.02 / -0.08 | 0.00 | -0.34 | 0.84 | -0.15 | 0.50 | 224 | NO |
| CL 2 (diag) | RTHopen+15 ref=gap open15vol hi2.0 dir=with hold=120m | 22 | 2 | 1.49 | -0.28 | 0.87 | 0.66 / 1.47 | 0.23 / -0.68 / 0.17 | 0.08 | -0.07 | 0.96 | -0.14 | 0.25 | 46 S | diag |
| CL 3 (diag) | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | 70 | 2 | 1.16 | -0.15 | 0.33 | -0.84 / 1.11 | 0.27 / -0.00 / -0.36 | 0.05 | -0.35 | 0.88 | -0.11 | 1.00 | 126 | diag |
| CL 4 (diag) | RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | 71 | 2 | 0.72 | -0.08 | 0.51 | 0.29 / 1.31 | 0.12 / -0.03 / 0.12 | 0.07 | 0.07 | 0.88 | -0.10 | 0.00 | 129 | diag |
| ZN 1 (diag) | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | 176 | 1 | -0.01 | -0.79 | -0.68 | -2.12 / 0.32 | -0.01 / -0.47 / -0.14 | -0.34 | 0.27 | 0.67 | -0.29 | 0.00 | 271 | diag |
| ZN 2 (diag) | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | 111 | 1 | -0.40 | -0.69 | -0.53 | -0.88 / 0.71 | -0.06 / -0.36 / 0.08 | -0.25 | 0.36 | 0.70 | -0.25 | 0.00 | 170 | diag |
| ZN 3 (diag) | RTHopen+15 ref=ft open15vol hi2.0 dir=with hold=flat | 118 | 0 | -0.41 | -1.23 | -0.99 | -2.22 / 0.51 | -0.11 / 0.00 / -0.71 | -0.35 | 0.11 | 0.32 | -0.41 | 0.00 | 166 | diag |
| BTC 1 | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | 100 | 2 | 0.81 | 0.42 | 0.14 | -0.66 / 1.29 | 0.13 / -0.46 / -0.13 | -0.02 | -0.16 | 0.64 | -0.22 | 0.00 | 150 | NO |
| BTC 2 | RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | 155 | 2 | 0.51 | 1.87 | 0.49 | 0.45 / 1.29 | 0.09 / -0.13 / 0.04 | 0.05 | 0.08 | 0.78 | -0.13 | 0.00 | 245 | NO |
| BTC 3 | RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | 106 | 2 | 0.26 | 1.33 | 0.22 | 0.14 / 1.33 | 0.03 / -0.09 / -0.05 | -0.00 | 0.13 | 0.68 | -0.18 | 0.50 | 159 | NO |
| BTC 4 | RTHopen+15 ref=gap open15vol lo0.65 dir=against hold=flat | 109 | 2 | 0.22 | -0.70 | 0.13 | -0.02 / 1.48 | -0.01 / -0.28 / 0.13 | -0.03 | -0.27 | 0.63 | -0.21 | 0.00 | 163 | NO |
| BTC 5 (diag) | RTHopen+15 ref=ft open15vol hi2.0 dir=with hold=flat | 64 | 2 | 1.58 | 0.14 | 0.58 | -1.04 / 1.32 | 0.31 / -0.71 / -0.02 | 0.09 | -0.23 | 0.92 | -0.09 | 0.50 | 101 | diag |
| BTC 6 (diag) | RTHopen+15 ref=gap open15vol hi2.0 dir=against hold=120m | 64 | 2 | 0.96 | 0.32 | -0.08 | -1.49 / 1.13 | 0.12 / -0.56 / -0.17 | -0.06 | -0.03 | 0.50 | -0.25 | 0.00 | 101 | diag |
| BTC 7 (diag) | RTHopen+15 ref=ft open15vol hi1.5 dir=with hold=flat | 126 | 1 | 0.91 | 0.34 | 0.59 | -0.10 / 1.64 | 0.18 / -0.46 / 0.15 | 0.08 | -0.14 | 0.90 | -0.08 | 0.50 | 196 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 20 |
| diagnostic cells read | 21 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 32 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 11 |
| small-sample (<100 trades pair window) | 10 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | clean | 0.50 | 0.81 | -131418 | -105950 | 608878 | -183662 | 0.75 | 41.0 | 1.55 | -84276 | 286012 | -99451 |
| BTC RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | H1 | 0.44 | 0.71 | -166755 | -142588 | 315613 | -215589 | 0.51 | 39.3 | 2.69 | -88321 | 143637 | -97138 |
| BTC RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | H2 | 0.57 | 0.88 | -88047 | -69955 | 194100 | -90768 | 0.58 | 30.6 | 2.53 | -87823 | 209803 | -97807 |
| BTC RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | all | 0.49 | 0.77 | -135141 | -110021 | 608878 | -215589 | 1.20 | 38.7 | 1.96 | -86678 | 286012 | -99451 |
| CL RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | clean | 0.46 | 0.75 | -127583 | -102528 | 472974 | -159418 | 0.89 | 29.5 | 1.57 | -79104 | 287400 | -81874 |
| CL RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | H1 | -0.67 | -0.90 | -65466 | -55267 | 223111 | -68763 | -0.33 | 42.9 | 2.81 | -76858 | 161252 | -78287 |
| CL RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | H2 | -0.23 | -0.34 | -188158 | -158927 | 771566 | -211593 | -0.14 | 36.1 | 2.41 | -88022 | 206619 | -95185 |
| CL RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | all | 0.16 | 0.24 | -144816 | -115919 | 771566 | -211593 | 0.31 | 33.3 | 1.95 | -81022 | 287400 | -95185 |
| ES RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | clean | 0.41 | 0.64 | -137825 | -104855 | 483240 | -249000 | 0.76 | 28.6 | 1.57 | -82590 | 257522 | -89452 |
| ES RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | H1 | -2.10 | -2.24 | -105704 | -93857 | 394496 | -128581 | -0.79 | 35.7 | 2.56 | -72476 | 183509 | -78287 |
| ES RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | H2 | -0.26 | -0.39 | -209850 | -180830 | 839287 | -227656 | -0.15 | 27.8 | 2.53 | -78535 | 206652 | -79653 |
| ES RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | all | -0.04 | -0.06 | -163574 | -125435 | 935322 | -249000 | -0.07 | 29.8 | 1.94 | -81211 | 257522 | -89452 |
| GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | clean | 1.53 | 3.20 | -105614 | -83404 | 239285 | -136226 | 5.95 | 30.5 | 1.72 | -81562 | 252359 | -89851 |
| GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | H1 | 0.23 | 0.39 | -187193 | -166095 | 668517 | -229290 | 0.15 | 46.4 | 2.84 | -88246 | 152124 | -101712 |
| GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | H2 | 1.58 | 3.35 | -290229 | -247478 | 419555 | -298305 | 3.81 | 41.7 | 3.16 | -98876 | 183839 | -105625 |
| GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | all | 1.15 | 2.32 | -200655 | -158518 | 668517 | -298305 | 4.67 | 35.7 | 2.22 | -87672 | 252359 | -105625 |
| RTY RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | clean | 0.46 | 0.86 | -114517 | -94936 | 485836 | -162951 | 0.87 | 25.7 | 1.58 | -81619 | 274214 | -87216 |
| RTY RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | H1 | -2.50 | -2.42 | -318018 | -262736 | 947846 | -472790 | -1.00 | 39.3 | 1.98 | -78515 | 188796 | -86733 |
| RTY RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | H2 | -1.54 | -1.78 | -203498 | -148458 | 547945 | -221426 | -0.92 | 27.8 | 2.12 | -112284 | 217552 | -126810 |
| RTY RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | all | -0.61 | -0.79 | -189029 | -141014 | 1818876 | -472790 | -0.56 | 28.6 | 1.77 | -89029 | 274214 | -126810 |
| YM RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | clean | 2.00 | 4.27 | -104771 | -80479 | 250882 | -135637 | 7.27 | 20.0 | 1.82 | -85474 | 282235 | -104685 |
| YM RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | H1 | -0.58 | -0.72 | -124282 | -113442 | 360807 | -151865 | -0.33 | 25.0 | 2.67 | -71525 | 156956 | -74254 |
| YM RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | H2 | 0.22 | 0.34 | -208455 | -168482 | 357782 | -218639 | 0.29 | 27.8 | 2.53 | -85145 | 224509 | -92874 |
| YM RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | all | 1.12 | 1.91 | -147451 | -114158 | 550054 | -218639 | 3.29 | 22.6 | 2.12 | -84478 | 282235 | -104685 |
| ZN RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat (diag) | clean | -0.37 | -0.48 | -161776 | -127915 | 975116 | -205335 | -0.34 | 31.4 | 1.40 | -86509 | 291104 | -94594 |
| ZN RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat (diag) | H1 | -2.09 | -2.27 | -162054 | -138495 | 565239 | -162885 | -0.78 | 42.9 | 2.47 | -78949 | 151590 | -79611 |
| ZN RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat (diag) | H2 | 0.40 | 0.62 | -74441 | -58970 | 281482 | -95140 | 0.27 | 33.3 | 2.56 | -83662 | 199447 | -89719 |
| ZN RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat (diag) | all | -0.53 | -0.67 | -155387 | -120579 | 1539476 | -205335 | -0.45 | 33.9 | 1.83 | -85265 | 291104 | -94594 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | -30.8 | 14.8 | 24.5 | 32.3 | 14.2 / 21.4 | 30.0 / 39.9 | NO |
| RTY RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | -41.2 | -50.5 | 3.7 | 25.8 | 15.4 / 20.4 | -16.0 / -2.7 | NO |
| YM RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | -10.2 | -15.1 | 14.9 | 16.6 | -16.0 / 15.2 | 36.3 / 41.4 | NO |
| GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | 4.2 | -33.6 | 5.5 | 27.8 | 11.7 / 23.3 | -16.3 / 3.0 | NO |
| CL RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | -27.4 | 1.8 | 23.1 | 23.1 | 26.4 / 28.2 | 30.0 / 31.5 | NO |
| ZN RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat (diag) | -37.6 | -9.3 | 11.7 | 21.9 | -10.2 / 6.0 | 26.1 / 27.4 | NO |
| BTC RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | -22.0 | -6.1 | 13.5 | 26.8 | -6.9 / 16.8 | -6.1 / 9.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=flat | negative pre-2023 | 585 | -12.9 | -42.3 | -27.6 | 29.4 | -0.09 / -0.31 / -0.20 | 101.8 / 72.5 |
| ES 2 RTHopen+15 ref=ft open15vol lo0.8 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 585 | 14.1 | -15.3 | -0.6 | 29.4 | 0.14 / -0.15 / -0.01 | 71.2 / 41.8 |
| ES 3 (diag) RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | positive pre-2023 | 225 | 60.9 | 31.6 | 46.4 | 29.4 | 0.27 / 0.14 / 0.20 | 273.6 / 244.3 |
| ES 4 (diag) RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=flat | negative pre-2023 | 254 | -33.5 | -62.8 | -48.4 | 29.4 | -0.13 / -0.24 / -0.18 | 683.2 / 653.8 |
| ES 5 (diag) RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=120m | negative pre-2023 | 254 | -112.4 | -141.7 | -127.3 | 29.4 | -0.59 / -0.74 / -0.67 | 366.3 / 337.0 |
| RTY 1 RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | positive pre-2023 | 278 | 39.2 | 24.8 | 27.2 | 14.4 | 0.31 / 0.19 / 0.21 | 74.7 / 60.4 |
| RTY 2 RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=120m | negative pre-2023 | 278 | -8.0 | -22.4 | -20.0 | 14.4 | -0.10 / -0.28 / -0.25 | 53.9 / 39.5 |
| RTY 3 (diag) RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | positive pre-2023 | 90 | 51.4 | 37.0 | 39.0 | 14.4 | 0.24 / 0.17 / 0.18 | 291.5 / 277.1 |
| RTY 4 (diag) RTHopen+15 ref=ft open15vol hi1.5 dir=against hold=120m | gross-positive, cost-negative pre-2023 | 126 | 6.2 | -8.2 | -5.2 | 14.4 | 0.04 / -0.05 / -0.03 | 312.1 / 297.7 |
| RTY 5 (diag) RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 90 | 4.7 | -9.6 | -7.6 | 14.4 | 0.03 / -0.07 / -0.05 | 192.3 / 178.0 |
| YM 1 RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=120m | negative pre-2023 | 597 | -10.1 | -24.4 | -18.5 | 14.4 | -0.17 / -0.41 / -0.31 | 162.2 / 147.8 |
| YM 2 RTHopen+15 ref=gap open15vol lo0.8 dir=against hold=flat | negative pre-2023 | 597 | -22.6 | -37.0 | -31.0 | 14.4 | -0.19 / -0.32 / -0.26 | 199.4 / 185.1 |
| YM 3 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | positive pre-2023 | 586 | 55.6 | 41.3 | 47.2 | 14.4 | 0.51 / 0.38 / 0.43 | 114.9 / 100.5 |
| YM 4 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 586 | 5.8 | -8.6 | -2.6 | 14.4 | 0.07 / -0.09 / -0.03 | 89.5 / 75.2 |
| YM 5 (diag) RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | positive pre-2023 | 238 | 50.7 | 36.3 | 42.4 | 14.4 | 0.28 / 0.20 / 0.24 | 255.0 / 240.6 |
| YM 6 (diag) RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=120m | negative pre-2023 | 272 | -14.5 | -28.9 | -22.8 | 14.4 | -0.11 / -0.21 / -0.17 | 426.2 / 411.9 |
| YM 7 (diag) RTHopen+15 ref=gap open15vol hi1.5 dir=against hold=flat | positive pre-2023 | 272 | 29.5 | 15.1 | 21.2 | 14.4 | 0.13 / 0.06 / 0.09 | 698.2 / 683.9 |
| GC 1 RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat | negative pre-2023 | 881 | -16.0 | -40.4 | -30.6 | 24.4 | -0.16 / -0.40 / -0.30 | 295.8 / 271.5 |
| GC 2 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | negative pre-2023 | 868 | -46.4 | -70.8 | -61.0 | 24.4 | -0.44 / -0.67 / -0.57 | 204.6 / 180.3 |
| GC 3 RTHopen+15 ref=gap open15vol hi1.5 dir=with hold=flat | positive pre-2023 | 710 | 46.1 | 21.8 | 31.7 | 24.4 | 0.32 / 0.15 / 0.22 | 243.2 / 218.9 |
| GC 4 RTHopen+15 ref=ft open15vol hi1.5 dir=against hold=120m | negative pre-2023 | 706 | -56.2 | -80.6 | -70.6 | 24.4 | -0.57 / -0.81 / -0.71 | 160.6 / 136.2 |
| GC 5 RTHopen+15 ref=gap open15vol hi1.5 dir=with hold=120m | positive pre-2023 | 710 | 69.5 | 45.2 | 55.2 | 24.4 | 0.66 / 0.43 / 0.52 | 147.9 / 123.5 |
| GC 6 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | negative pre-2023 | 867 | -4.9 | -29.3 | -19.5 | 24.4 | -0.07 / -0.44 / -0.30 | 98.7 / 74.3 |
| GC 7 RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | negative pre-2023 | 545 | -27.0 | -51.4 | -41.6 | 24.4 | -0.34 / -0.64 / -0.52 | 81.0 / 56.6 |
| GC 8 (diag) RTHopen+15 ref=ft open15vol hi2.0 dir=against hold=120m | negative pre-2023 | 384 | -50.6 | -75.0 | -64.9 | 24.4 | -0.36 / -0.53 / -0.46 | 558.1 / 533.7 |
| GC 9 (diag) RTHopen+15 ref=ft open15vol hi2.0 dir=against hold=flat | negative pre-2023 | 384 | -57.9 | -82.3 | -72.2 | 24.4 | -0.30 / -0.42 / -0.37 | 472.1 / 447.7 |
| GC 10 (diag) RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | negative pre-2023 | 556 | -2.9 | -27.3 | -17.5 | 24.4 | -0.02 / -0.23 / -0.15 | 289.4 / 265.1 |
| CL 1 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 793 | 11.7 | -12.6 | -9.9 | 24.4 | 0.15 / -0.16 / -0.13 | 62.5 / 38.1 |
| CL 2 (diag) RTHopen+15 ref=gap open15vol hi2.0 dir=with hold=120m | negative pre-2023 | 115 | -64.0 | -88.4 | -86.0 | 24.4 | -0.20 / -0.28 / -0.27 | 260.5 / 236.1 |
| CL 3 (diag) RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | gross-positive, cost-negative pre-2023 | 452 | 7.1 | -17.3 | -14.5 | 24.4 | 0.06 / -0.15 / -0.13 | 144.4 / 120.1 |
| CL 4 (diag) RTHopen+15 ref=gap open15vol lo0.65 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 455 | 12.3 | -12.1 | -9.3 | 24.4 | 0.08 / -0.08 / -0.06 | 145.8 / 121.4 |
| ZN 1 (diag) RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 800 | 7.5 | -28.1 | -33.2 | 35.6 | 0.21 / -0.79 / -0.93 | 36.0 / 0.3 |
| ZN 2 (diag) RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | gross-positive, cost-negative pre-2023 | 502 | 5.9 | -29.7 | -34.7 | 35.6 | 0.14 / -0.69 / -0.81 | 23.1 / -12.5 |
| ZN 3 (diag) RTHopen+15 ref=ft open15vol hi2.0 dir=with hold=flat | negative pre-2023 | 400 | -32.9 | -68.5 | -73.5 | 35.6 | -0.60 / -1.23 / -1.32 | 18.8 / -16.8 |
| BTC 1 RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=120m | positive pre-2023 | 65 | 171.2 | 116.8 | 148.0 | 54.4 | 0.61 / 0.42 / 0.53 | 505.0 / 450.6 |
| BTC 2 RTHopen+15 ref=ft open15vol lo0.8 dir=with hold=flat | positive pre-2023 | 112 | 802.2 | 747.9 | 780.1 | 54.4 | 2.00 / 1.87 / 1.95 | 416.9 / 362.6 |
| BTC 3 RTHopen+15 ref=ft open15vol lo0.65 dir=with hold=flat | positive pre-2023 | 69 | 748.2 | 693.8 | 725.1 | 54.4 | 1.43 / 1.33 / 1.39 | 271.5 / 217.1 |
| BTC 4 RTHopen+15 ref=gap open15vol lo0.65 dir=against hold=flat | negative pre-2023 | 69 | -251.8 | -306.2 | -274.9 | 54.4 | -0.58 / -0.70 / -0.63 | 223.2 / 168.8 |
| BTC 5 (diag) RTHopen+15 ref=ft open15vol hi2.0 dir=with hold=flat | positive pre-2023 | 45 | 188.9 | 134.5 | 167.9 | 54.4 | 0.20 / 0.14 / 0.18 | 2135.9 / 2081.6 |
| BTC 6 (diag) RTHopen+15 ref=gap open15vol hi2.0 dir=against hold=120m | positive pre-2023 | 45 | 162.8 | 108.4 | 141.8 | 54.4 | 0.48 / 0.32 / 0.42 | 968.4 / 914.0 |
| BTC 7 (diag) RTHopen+15 ref=ft open15vol hi1.5 dir=with hold=flat | positive pre-2023 | 93 | 248.1 | 193.8 | 225.7 | 54.4 | 0.44 / 0.34 / 0.40 | 1016.5 / 962.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 4 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.46, p(top) = 0.84); CL: 1 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.71, p(top) = 0.52); ES: 2 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.22, p(top) = 0.46); GC: 7 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.03, p(top) = 0.31); NQ: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); RTY: 2 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.00, p(top) = 0.05); YM: 4 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.02, p(top) = 0.03); ZN: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00).
- Of 20 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.32 (GC RTHopen+15 ref=gap open15vol lo0.8 dir=with hold=flat); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell GC RTHopen+15 ref=gap open15vol hi1.5 dir=with hold=flat: uplift +0.10/+1.61/+0.21, boot lo -0.04, plateau 0.00, 2x-slip +0.29, wd corr +0.27, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 10, 'positive pre-2023': 7, 'gross-positive, cost-negative pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_28.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw28/ (`SW28_CO_all_selected_scored.csv`).

DONE SW28
