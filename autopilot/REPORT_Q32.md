# REPORT Q32 - Q32: morning-range state -> afternoon: narrow/wide first-90-minute range, trade with/against the open-to-11:00 direction

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 5 selected cells (+30 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.02; best pair-window standalone Sharpe +1.41.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: morning-range state -> afternoon: narrow/wide first-90-minute range, trade with/against the open-to-11:00 direction.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      16 |          8 |         0 |               0.546 |                2 |          0 |            3 |
| CL    |      16 |          8 |         0 |               1.072 |                2 |          0 |            3 |
| ES    |      16 |          8 |         0 |               0.365 |                2 |          0 |            3 |
| GC    |      16 |          8 |         1 |               1.353 |                2 |          1 |            3 |
| HG    |      16 |          8 |         0 |               0.262 |                1 |          0 |            3 |
| HO    |      16 |          8 |         1 |               1.78  |                2 |          1 |            3 |
| NQ    |      16 |         12 |         0 |               0.494 |                2 |          0 |            3 |
| RTY   |      16 |          8 |         2 |               1.225 |                2 |          2 |            3 |
| SI    |      16 |          8 |         1 |               0.395 |                2 |          1 |            3 |
| ZN    |      16 |         12 |         0 |               0.562 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.325 |               5 |      1     |                     nan     |            0.744 |           1.319 |  nan     |     nan     |                1.475 |
| NQ    |     200 |                    0 |            1.495 |               5 |      1     |                     nan     |            0.796 |           1.398 |  nan     |     nan     |                1.684 |
| RTY   |     200 |                    2 |            1.15  |               5 |      0.285 |                       0.771 |            0.76  |           1.368 |    0.305 |       0.809 |                1.536 |
| GC    |     200 |                    1 |            1.25  |               4 |      0.8   |                       0.361 |            0.739 |           1.459 |    0.69  |       0.361 |                1.642 |
| CL    |     200 |                    0 |            1.02  |               4 |      1     |                     nan     |            0.695 |           1.348 |  nan     |     nan     |                1.617 |
| ZN    |     200 |                    0 |            0.02  |               1 |      1     |                     nan     |            0.464 |           0.895 |  nan     |     nan     |                0.895 |
| HO    |     200 |                    1 |            1.515 |               5 |      0.83  |                       0.666 |            0.691 |           1.259 |    0.425 |       0.666 |                1.618 |
| 6E    |     200 |                    0 |            0.51  |               2 |      1     |                     nan     |            0.522 |           1.179 |  nan     |     nan     |                1.179 |
| SI    |     200 |                    1 |            0.83  |               4 |      0.565 |                       0.063 |            0.627 |           1.339 |    0.56  |       0.063 |                1.451 |
| HG    |     200 |                    0 |            0.885 |               4 |      1     |                     nan     |            0.656 |           1.243 |  nan     |     nan     |                1.351 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | morn (1, 1.0, 120, -1) | 20 | 2 | 0.37 | -0.36 | -0.20 | -0.87 / 1.56 | 0.07 / -0.21 / -0.43 | -0.09 | -0.32 | 0.44 | -0.30 | 0.00 | 32 S | diag |
| ES 2 (diag) | morn (1, 0.8, 240, -1) | 43 | 1 | 0.31 | 0.16 | 0.35 | 0.41 / 1.50 | 0.09 / -0.36 / 0.24 | 0.06 | -0.51 | 0.76 | -0.11 | 0.00 | 74 S | diag |
| ES 3 (diag) | morn (1, 0.8, 120, -1) | 43 | 1 | 0.13 | -0.44 | -0.10 | -0.38 / 1.26 | 0.03 / -0.13 / -0.28 | -0.06 | -0.38 | 0.56 | -0.27 | 0.00 | 74 S | diag |
| NQ 1 (diag) | morn (-1, 0.3, 240, -1) | 62 | 1 | 0.49 | -0.02 | 0.62 | 0.81 / 1.32 | 0.06 / -0.08 / 0.21 | 0.06 | 0.05 | 0.90 | -0.10 | 0.00 | 89 S | diag |
| NQ 2 (diag) | morn (-1, 0.4, 120, 1) | 155 | 1 | 0.44 | 0.09 | 0.76 | 1.14 / 1.51 | 0.04 / 0.23 / 0.05 | 0.08 | 0.21 | 0.95 | -0.11 | 0.50 | 244 | diag |
| NQ 3 (diag) | morn (-1, 0.3, 120, -1) | 62 | 1 | 0.33 | -0.20 | 0.06 | -0.48 / 1.48 | 0.02 / -0.34 / 0.04 | -0.04 | -0.01 | 0.61 | -0.21 | 0.00 | 91 S | diag |
| RTY 1 | morn (-1, 0.4, 120, -1) | 116 | 2 | 0.81 | -0.56 | 0.13 | -1.02 / 1.43 | 0.09 / -0.22 / -0.32 | -0.08 | 0.00 | 0.73 | -0.22 | 0.00 | 169 | NO |
| RTY 2 | morn (-1, 0.4, 240, -1) | 114 | 2 | 0.73 | -0.65 | 0.47 | -0.13 / 1.42 | 0.12 / -0.27 / -0.09 | -0.00 | -0.09 | 0.87 | -0.17 | 0.50 | 165 | NO |
| RTY 3 (diag) | morn (-1, 0.3, 120, -1) | 28 | 1 | 1.22 | 0.17 | 0.19 | -0.80 / 1.07 | 0.19 / -0.12 / -0.68 | -0.08 | 0.23 | 0.73 | -0.37 | 0.00 | 42 S | diag |
| RTY 4 (diag) | morn (-1, 0.3, 240, -1) | 28 | 2 | 0.65 | -0.12 | 0.42 | 0.08 / 1.37 | 0.08 / -0.08 / -0.19 | -0.01 | 0.21 | 0.81 | -0.20 | 0.00 | 41 S | diag |
| RTY 5 (diag) | morn (1, 0.8, 240, -1) | 78 | 1 | 0.30 | 0.29 | 0.29 | 0.29 / 1.60 | 0.02 / -0.64 / 0.36 | -0.01 | 0.05 | 0.82 | -0.20 | 0.00 | 124 | diag |
| GC 1 | morn (-1, 0.3, 240, -1) | 131 | 2 | 0.36 | -0.61 | 0.37 | 0.46 / 1.31 | 0.05 / 0.22 / -0.23 | -0.01 | 0.30 | 0.81 | -0.43 | 0.50 | 265 | NO |
| GC 2 (diag) | morn (1, 1.0, 240, 1) | 21 | 2 | 1.35 | 0.15 | 1.41 | 1.50 / 1.66 | 0.21 / 0.34 / 0.13 | 0.21 | 0.18 | 0.98 | 0.09 | 1.00 | 26 S | diag |
| GC 3 (diag) | morn (1, 1.0, 120, 1) | 21 | 2 | 1.34 | 0.17 | 1.26 | 1.12 / 1.49 | 0.21 / 0.30 / -0.03 | 0.16 | -0.06 | 1.00 | 0.05 | 1.00 | 26 S | diag |
| GC 4 (diag) | morn (1, 0.8, 240, 1) | 42 | 2 | 1.28 | -0.01 | -0.11 | -0.70 / 1.32 | 0.16 / -1.76 / -0.45 | -0.32 | -0.01 | 0.42 | -0.90 | 0.00 | 56 S | diag |
| CL 1 (diag) | morn (1, 1.0, 240, -1) | 13 | 2 | 1.07 | 0.04 | -0.11 | -0.97 / 1.46 | 0.19 / -0.10 / -0.95 | -0.13 | 0.15 | 0.41 | -0.54 | 0.00 | 15 S | diag |
| CL 2 (diag) | morn (-1, 0.3, 240, -1) | 92 | 1 | 0.61 | -0.35 | 0.22 | -0.08 / 1.44 | 0.11 / -0.30 / -0.52 | -0.14 | -0.53 | 0.71 | -0.40 | 0.00 | 196 | diag |
| CL 3 (diag) | morn (1, 1.0, 120, -1) | 13 | 1 | 0.54 | -0.24 | -0.40 | -0.97 /  | 0.07 / -0.14 / -1.34 | -0.34 | 0.15 | 0.39 | -0.88 | 0.00 | 15 S | diag |
| ZN 1 (diag) | morn (-1, 0.3, 240, 1) | 105 | 1 | 0.56 | -1.07 | -0.47 | -2.82 / 0.08 | 0.10 / -0.44 / -0.35 | -0.28 | -0.11 | 0.92 | -0.24 | 0.00 | 161 | diag |
| ZN 2 (diag) | morn (-1, 0.4, 240, 1) | 207 | 1 | -0.03 | -1.95 | -0.98 | -3.00 / -0.72 | -0.02 / -0.48 / -0.49 | -0.50 | 0.04 | 0.92 | -0.36 | 0.00 | 327 | diag |
| ZN 3 (diag) | morn (1, 0.8, 240, 1) | 76 | 1 | -0.08 | -0.81 | -0.67 | -2.37 / 0.64 | -0.05 / -0.26 / -0.32 | -0.28 | -0.08 | 0.58 | -0.33 | 0.00 | 108 | diag |
| HO 1 | morn (-1, 0.3, 120, 1) | 164 | 2 | 0.67 | -0.61 | -0.68 | -1.50 / 1.41 | 0.10 / -0.39 / -1.64 | -0.43 | 0.39 | 0.14 | -0.81 | 0.00 | 304 | NO |
| HO 2 (diag) | morn (1, 0.8, 240, 1) | 10 | 2 | 1.78 | 0.24 | 1.36 | 1.13 /  | 0.29 / 0.01 / 0.37 | 0.27 |  | 1.00 | 0.13 | 1.00 | 16 S | diag |
| HO 3 (diag) | morn (1, 0.8, 120, 1) | 10 | 2 | 1.44 | -0.07 | 1.11 | 0.74 /  | 0.25 / -0.00 / 0.29 | 0.22 |  | 0.98 | 0.06 | 0.50 | 16 S | diag |
| HO 4 (diag) | morn (1, 1.0, 120, 1) | 3 | 2 | 1.19 | 0.20 | 1.10 | 1.19 /  | 0.20 / 0.00 / 0.44 | 0.23 |  | 0.96 | 0.07 | 0.50 | 6 S | diag |
| 6E 1 (diag) | morn (1, 1.0, 240, -1) | 27 | 2 | 0.55 | -0.83 | 0.33 | -0.13 / 1.12 | 0.05 / 0.23 / -0.16 | -0.01 | 0.10 | 0.82 | -0.14 | 0.00 | 35 S | diag |
| 6E 2 (diag) | morn (1, 1.0, 120, -1) | 27 | 2 | 0.28 | -0.89 | -0.03 | -1.02 / 1.01 | 0.00 / 0.03 / -0.15 | -0.06 | 0.15 | 0.75 | -0.18 | 0.00 | 35 S | diag |
| 6E 3 (diag) | morn (1, 0.8, 120, -1) | 45 | 1 | 0.23 | -0.66 | 0.25 | 0.34 / 0.80 | -0.01 / 0.07 / 0.02 | -0.03 | 0.06 | 0.91 | -0.15 | 0.00 | 63 S | diag |
| SI 1 | morn (-1, 0.4, 240, 1) | 223 | 2 | 0.06 | -0.60 | -0.58 | -0.96 / 1.15 | 0.01 / -1.77 / -1.92 | -0.91 | -0.51 | 0.26 | -1.46 | 0.00 | 432 | NO |
| SI 2 (diag) | morn (1, 0.8, 240, 1) | 46 | 2 | 0.40 | -0.21 | 0.71 | 1.08 / 1.29 | 0.01 / 0.12 / 0.12 | 0.04 | -0.16 | 0.94 | -0.12 | 0.00 | 61 S | diag |
| SI 3 (diag) | morn (1, 0.8, 120, 1) | 47 | 2 | 0.28 | -0.08 | 0.43 | 0.60 / 1.64 | -0.01 / -0.37 / 0.14 | -0.04 | -0.28 | 0.79 | -0.21 | 0.00 | 62 S | diag |
| SI 4 (diag) | morn (-1, 0.3, 240, 1) | 102 | 1 | 0.03 | -0.25 | -0.83 | -1.38 / 1.64 | -0.03 / -1.44 / -2.63 | -1.07 | -0.40 | 0.07 | -1.65 | 0.00 | 229 | diag |
| HG 1 (diag) | morn (-1, 0.3, 240, 1) | 183 | 1 | 0.26 | -0.61 | -0.57 | -1.82 / 1.27 | 0.08 / -0.37 / -0.91 | -0.31 | 0.16 | 0.38 | -0.47 | 0.00 | 330 | diag |
| HG 2 (diag) | morn (1, 1.0, 240, -1) | 7 | 1 | 0.19 | -0.01 | 0.43 | 0.64 /  | 0.01 / -0.22 / 0.00 | 0.01 | 0.15 | 0.76 | -0.23 | 0.00 | 9 S | diag |
| HG 3 (diag) | morn (1, 1.0, 120, 1) | 7 | 1 | 0.13 | 0.04 | -0.38 | -0.66 /  | -0.03 / -2.44 / 0.00 | -0.60 | -0.15 | 0.34 | -1.35 | 0.00 | 9 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 5 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 15 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 30 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 22 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E morn (1, 1.0, 240, -1) (diag) | clean | 0.54 | 1.04 | -115352 | -81843 | 477969 | -234835 | 1.03 | 14.3 | 1.51 | -81296 | 286628 | -88392 |
| 6E morn (1, 1.0, 240, -1) (diag) | H1 | 1.68 |  | 0 | 0 | 0 | 0 |  | 0.0 | 3.05 | -73969 | 151713 | -78287 |
| 6E morn (1, 1.0, 240, -1) (diag) | H2 | -0.98 | -1.02 | -175351 | -97608 | 308815 | -306215 | -0.86 | 8.3 | 2.32 | -83943 | 236724 | -85362 |
| 6E morn (1, 1.0, 240, -1) (diag) | all | 0.33 | 0.54 | -121604 | -80416 | 477969 | -306215 | 0.92 | 10.7 | 1.91 | -81783 | 286628 | -88392 |
| CL morn (-1, 0.3, 240, -1) (diag) | clean | 0.71 | 1.23 | -125216 | -93362 | 630000 | -237363 | 1.02 | 25.7 | 1.57 | -87803 | 297024 | -124481 |
| CL morn (-1, 0.3, 240, -1) (diag) | H1 | -0.49 | -0.71 | -102271 | -98444 | 400283 | -103275 | -0.28 | 32.1 | 2.52 | -73180 | 169757 | -78287 |
| CL morn (-1, 0.3, 240, -1) (diag) | H2 | 0.01 | 0.01 | -382018 | -315978 | 845076 | -475035 | 0.01 | 44.4 | 1.96 | -135412 | 233135 | -149757 |
| CL morn (-1, 0.3, 240, -1) (diag) | all | 0.22 | 0.33 | -248724 | -187297 | 845076 | -475035 | 0.64 | 31.0 | 1.81 | -98285 | 297024 | -149757 |
| ES morn (1, 0.8, 240, -1) (diag) | clean | 0.31 | 0.53 | -138539 | -99184 | 502193 | -193923 | 0.56 | 13.3 | 1.55 | -78657 | 248317 | -81810 |
| ES morn (1, 0.8, 240, -1) (diag) | H1 | -0.44 | -0.56 | -221060 | -191385 | 496364 | -302844 | -0.31 | 28.6 | 2.47 | -87162 | 182282 | -96037 |
| ES morn (1, 0.8, 240, -1) (diag) | H2 | 1.70 | 10.74 | -32088 | -16044 | 82958 | -38586 | 4.99 | 5.6 | 2.73 | -81089 | 188316 | -82524 |
| ES morn (1, 0.8, 240, -1) (diag) | all | 0.35 | 0.56 | -156154 | -110222 | 502193 | -302844 | 1.07 | 14.3 | 1.97 | -81255 | 248317 | -96037 |
| GC morn (-1, 0.3, 240, -1) | clean | 0.38 | 0.62 | -132552 | -99120 | 888650 | -206178 | 0.38 | 29.5 | 1.51 | -89177 | 279861 | -118177 |
| GC morn (-1, 0.3, 240, -1) | H1 | 0.89 | 1.35 | -194312 | -172934 | 399321 | -252231 | 0.83 | 21.4 | 3.05 | -72773 | 149592 | -78287 |
| GC morn (-1, 0.3, 240, -1) | H2 | 0.41 | 0.59 | -753039 | -500272 | 1314928 | -907862 | 0.45 | 36.1 | 2.26 | -140602 | 229241 | -156531 |
| GC morn (-1, 0.3, 240, -1) | all | 0.37 | 0.53 | -337297 | -240985 | 1807189 | -907862 | 0.70 | 29.8 | 1.91 | -108592 | 336254 | -156531 |
| HG morn (1, 1.0, 240, -1) (diag) | clean | 0.19 | 0.34 | -85659 | -46723 | 438542 | -331840 | 0.39 | 3.8 | 1.47 | -78736 | 346478 | -81874 |
| HG morn (1, 1.0, 240, -1) (diag) | H1 | 0.97 | 3.87 | -218309 | -145539 | 436618 | -436618 | 2.84 | 3.6 | 2.61 | -104241 | 181561 | -130194 |
| HG morn (1, 1.0, 240, -1) (diag) | H2 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.48 | -81089 | 217425 | -82524 |
| HG morn (1, 1.0, 240, -1) (diag) | all | 0.43 | 1.40 | -105619 | -55916 | 851306 | -436618 | 1.66 | 3.0 | 1.92 | -85085 | 346478 | -130194 |
| HO morn (-1, 0.3, 120, 1) | clean | 0.61 | 0.90 | -141461 | -117004 | 736015 | -165628 | 0.75 | 29.5 | 1.56 | -88937 | 274602 | -110845 |
| HO morn (-1, 0.3, 120, 1) | H1 | -1.63 | -1.84 | -147003 | -138412 | 470086 | -165923 | -0.80 | 46.4 | 2.43 | -79037 | 161878 | -79786 |
| HO morn (-1, 0.3, 120, 1) | H2 | -1.76 | -2.03 | -706517 | -579498 | 3179804 | -896671 | -0.75 | 61.1 | 0.84 | -135240 | 380855 | -143273 |
| HO morn (-1, 0.3, 120, 1) | all | -0.68 | -0.82 | -400039 | -288088 | 3179804 | -896671 | -0.69 | 39.3 | 1.49 | -103436 | 380855 | -143273 |
| NQ morn (-1, 0.4, 120, 1) (diag) | clean | 0.43 | 0.62 | -150600 | -106892 | 639476 | -262689 | 0.61 | 31.4 | 1.50 | -79606 | 254503 | -83657 |
| NQ morn (-1, 0.4, 120, 1) (diag) | H1 | 1.55 | 5.17 | -112477 | -90242 | 150547 | -150547 | 4.52 | 21.4 | 3.06 | -71122 | 155407 | -76932 |
| NQ morn (-1, 0.4, 120, 1) (diag) | H2 | 0.73 | 1.24 | -168690 | -140681 | 241334 | -170257 | 1.35 | 30.6 | 2.53 | -97008 | 214097 | -113078 |
| NQ morn (-1, 0.4, 120, 1) (diag) | all | 0.76 | 1.36 | -162325 | -118941 | 639476 | -262689 | 2.19 | 29.8 | 1.99 | -83549 | 254503 | -113078 |
| RTY morn (-1, 0.4, 240, -1) | clean | 0.85 | 1.38 | -129362 | -104901 | 605085 | -240381 | 1.30 | 25.7 | 1.58 | -84018 | 292430 | -104795 |
| RTY morn (-1, 0.4, 240, -1) | H1 | -0.86 | -1.03 | -199552 | -156028 | 496386 | -204170 | -0.46 | 28.6 | 2.56 | -77610 | 202347 | -78287 |
| RTY morn (-1, 0.4, 240, -1) | H2 | 0.43 | 0.98 | -104344 | -72163 | 306453 | -152806 | 0.48 | 27.8 | 2.40 | -99269 | 217425 | -110215 |
| RTY morn (-1, 0.4, 240, -1) | all | 0.47 | 0.74 | -147565 | -110950 | 605085 | -240381 | 1.17 | 26.8 | 1.91 | -87322 | 292430 | -110215 |
| SI morn (-1, 0.4, 240, 1) | clean | 0.03 | 0.05 | -127267 | -103658 | 733764 | -187252 | 0.04 | 48.6 | 1.47 | -85437 | 331837 | -98379 |
| SI morn (-1, 0.4, 240, 1) | H1 | -0.53 | -0.68 | -1011707 | -791332 | 2647427 | -1541406 | -0.33 | 53.6 | 1.06 | -214259 | 545997 | -334665 |
| SI morn (-1, 0.4, 240, 1) | H2 | -1.32 | -1.47 | -1158627 | -903959 | 3153745 | -1360428 | -0.80 | 55.6 | 0.56 | -258899 | 469379 | -328391 |
| SI morn (-1, 0.4, 240, 1) | all | -0.58 | -0.69 | -740685 | -516320 | 5049581 | -1541406 | -0.66 | 51.2 | 1.08 | -175907 | 719529 | -334665 |
| ZN morn (-1, 0.3, 240, 1) (diag) | clean | 0.56 | 1.04 | -102007 | -87934 | 821967 | -132208 | 0.62 | 37.1 | 1.56 | -83081 | 308473 | -95727 |
| ZN morn (-1, 0.3, 240, 1) (diag) | H1 | -3.37 | -3.16 | -141659 | -119501 | 581103 | -153645 | -1.00 | 42.9 | 2.39 | -80915 | 149242 | -84898 |
| ZN morn (-1, 0.3, 240, 1) (diag) | H2 | -2.38 | -2.54 | -140392 | -108607 | 649741 | -151111 | -0.85 | 44.4 | 2.13 | -93275 | 256074 | -94437 |
| ZN morn (-1, 0.3, 240, 1) (diag) | all | -0.47 | -0.70 | -121461 | -99920 | 1955448 | -153645 | -0.32 | 39.9 | 1.82 | -87482 | 308473 | -95727 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES morn (1, 0.8, 240, -1) (diag) | -24.1 | 0.0 | 24.3 | 27.1 | 25.9 / 29.3 | -5.4 / 8.0 | NO |
| NQ morn (-1, 0.4, 120, 1) (diag) | -14.7 | -28.3 | 16.5 | 20.5 | -2.3 / 21.4 | 31.2 / 32.0 | NO |
| RTY morn (-1, 0.4, 240, -1) | -22.2 | -23.1 | 11.1 | 16.3 | -16.5 / 14.5 | 30.0 / 30.0 | NO |
| GC morn (-1, 0.3, 240, -1) | -16.1 | -208.8 | -51.9 | -40.5 | -41.3 / 6.4 | 26.5 / 27.6 | NO |
| CL morn (-1, 0.3, 240, -1) (diag) | -24.1 | -119.1 | -21.5 | 0.1 | -52.8 / 11.1 | 22.1 / 25.4 | NO |
| ZN morn (-1, 0.3, 240, 1) (diag) | -36.8 | -2.7 | 11.3 | 14.8 | 0.2 / 20.6 | 17.3 / 23.6 | NO |
| HO morn (-1, 0.3, 120, 1) | -54.1 | -107.3 | -49.9 | -115.7 | -27.1 / 7.0 | 25.7 / 27.2 | NO |
| 6E morn (1, 1.0, 240, -1) (diag) | -25.2 | 18.3 | 22.1 | 23.4 | 17.6 / 20.4 | 30.0 / 37.0 | NO |
| SI morn (-1, 0.4, 240, 1) | -66.7 | -482.7 | -197.7 | -281.6 | -4.9 / 15.9 | -514.3 / -301.8 | NO |
| HG morn (1, 1.0, 240, -1) (diag) | -14.6 | -95.1 | 13.6 | -5.5 | 26.8 / 27.8 | -105.6 / -39.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) morn (1, 1.0, 120, -1) | negative pre-2023 | 101 | -75.2 | -104.6 | -91.1 | 29.4 | -0.26 / -0.36 / -0.31 | 237.5 / 208.1 |
| ES 2 (diag) morn (1, 0.8, 240, -1) | positive pre-2023 | 260 | 65.1 | 35.8 | 50.2 | 29.4 | 0.29 / 0.16 / 0.23 | 161.3 / 132.0 |
| ES 3 (diag) morn (1, 0.8, 120, -1) | negative pre-2023 | 261 | -36.2 | -65.5 | -51.1 | 29.4 | -0.25 / -0.44 / -0.35 | 72.7 / 43.3 |
| NQ 1 (diag) morn (-1, 0.3, 240, -1) | gross-positive, cost-negative pre-2023 | 286 | 10.5 | -3.9 | 4.8 | 14.4 | 0.05 / -0.02 / 0.02 | 215.9 / 201.5 |
| NQ 2 (diag) morn (-1, 0.4, 120, 1) | positive pre-2023 | 833 | 21.1 | 6.7 | 15.3 | 14.4 | 0.27 / 0.09 / 0.20 | 87.4 / 73.0 |
| NQ 3 (diag) morn (-1, 0.3, 120, -1) | negative pre-2023 | 294 | -9.6 | -23.9 | -15.2 | 14.4 | -0.08 / -0.20 / -0.13 | 106.9 / 92.6 |
| RTY 1 morn (-1, 0.4, 120, -1) | negative pre-2023 | 336 | -17.4 | -31.7 | -29.3 | 14.4 | -0.31 / -0.56 / -0.52 | 59.1 / 44.7 |
| RTY 2 morn (-1, 0.4, 240, -1) | negative pre-2023 | 330 | -39.3 | -53.6 | -51.2 | 14.4 | -0.47 / -0.65 / -0.62 | 86.0 / 71.6 |
| RTY 3 (diag) morn (-1, 0.3, 120, -1) | positive pre-2023 | 77 | 35.5 | 21.2 | 23.9 | 14.4 | 0.29 / 0.17 / 0.19 | 124.1 / 109.7 |
| RTY 4 (diag) morn (-1, 0.3, 240, -1) | negative pre-2023 | 73 | -6.2 | -20.6 | -17.9 | 14.4 | -0.04 / -0.12 / -0.11 | 106.1 / 91.7 |
| RTY 5 (diag) morn (1, 0.8, 240, -1) | positive pre-2023 | 218 | 51.6 | 37.2 | 39.3 | 14.4 | 0.40 / 0.29 / 0.31 | 45.1 / 30.8 |
| GC 1 morn (-1, 0.3, 240, -1) | negative pre-2023 | 718 | -27.5 | -51.9 | -41.8 | 24.4 | -0.32 / -0.61 / -0.49 | 80.6 / 56.3 |
| GC 2 (diag) morn (1, 1.0, 240, 1) | positive pre-2023 | 108 | 70.5 | 46.1 | 55.8 | 24.4 | 0.23 / 0.15 / 0.19 | 779.5 / 755.2 |
| GC 3 (diag) morn (1, 1.0, 120, 1) | positive pre-2023 | 108 | 63.5 | 39.2 | 48.9 | 24.4 | 0.27 / 0.17 / 0.21 | 768.6 / 744.2 |
| GC 4 (diag) morn (1, 0.8, 240, 1) | gross-positive, cost-negative pre-2023 | 237 | 23.2 | -1.1 | 8.5 | 24.4 | 0.11 / -0.01 / 0.04 | 441.0 / 416.6 |
| CL 1 (diag) morn (1, 1.0, 240, -1) | positive pre-2023 | 34 | 59.1 | 34.8 | 36.8 | 24.4 | 0.07 / 0.04 / 0.04 | 457.7 / 433.3 |
| CL 2 (diag) morn (-1, 0.3, 240, -1) | negative pre-2023 | 529 | -20.8 | -45.2 | -41.5 | 24.4 | -0.16 / -0.35 / -0.32 | 94.0 / 69.7 |
| CL 3 (diag) morn (1, 1.0, 120, -1) | negative pre-2023 | 36 | -109.7 | -134.1 | -131.9 | 24.4 | -0.20 / -0.24 / -0.24 | 181.5 / 157.2 |
| ZN 1 (diag) morn (-1, 0.3, 240, 1) | gross-positive, cost-negative pre-2023 | 629 | 6.3 | -29.4 | -34.6 | 35.6 | 0.23 / -1.07 / -1.25 | 52.2 / 16.6 |
| ZN 2 (diag) morn (-1, 0.4, 240, 1) | negative pre-2023 | 1270 | -0.9 | -36.5 | -41.7 | 35.6 | -0.05 / -1.95 / -2.23 | 34.5 / -1.1 |
| ZN 3 (diag) morn (1, 0.8, 240, 1) | negative pre-2023 | 232 | -13.1 | -48.7 | -53.7 | 35.6 | -0.22 / -0.81 / -0.90 | 32.1 / -3.5 |
| HO 1 morn (-1, 0.3, 120, 1) | negative pre-2023 | 916 | -48.4 | -61.2 | -59.5 | 12.8 | -0.48 / -0.61 / -0.59 | 64.6 / 51.9 |
| HO 2 (diag) morn (1, 0.8, 240, 1) | positive pre-2023 | 39 | 291.6 | 278.9 | 279.2 | 12.8 | 0.25 / 0.24 / 0.24 | 1267.1 / 1254.4 |
| HO 3 (diag) morn (1, 0.8, 120, 1) | negative pre-2023 | 41 | -34.0 | -46.8 | -46.3 | 12.8 | -0.05 / -0.07 / -0.07 | 778.7 / 765.9 |
| HO 4 (diag) morn (1, 1.0, 120, 1) | positive pre-2023 | 11 | 279.1 | 266.3 | 266.6 | 12.8 | 0.21 / 0.20 / 0.20 | 1232.0 / 1219.2 |
| 6E 1 (diag) morn (1, 1.0, 240, -1) | negative pre-2023 | 141 | -93.1 | -109.9 | -111.6 | 16.9 | -0.71 / -0.83 / -0.84 | 64.8 / 48.0 |
| 6E 2 (diag) morn (1, 1.0, 120, -1) | negative pre-2023 | 141 | -80.1 | -97.0 | -98.7 | 16.9 | -0.74 / -0.89 / -0.91 | 41.4 / 24.6 |
| 6E 3 (diag) morn (1, 0.8, 120, -1) | negative pre-2023 | 273 | -30.8 | -47.6 | -49.3 | 16.9 | -0.43 / -0.66 / -0.68 | 32.2 / 15.4 |
| SI 1 morn (-1, 0.4, 240, 1) | gross-positive, cost-negative pre-2023 | 1177 | 9.7 | -44.6 | -25.3 | 54.4 | 0.13 / -0.60 / -0.34 | 57.5 / 3.2 |
| SI 2 (diag) morn (1, 0.8, 240, 1) | gross-positive, cost-negative pre-2023 | 228 | 0.4 | -53.9 | -35.1 | 54.4 | 0.00 / -0.21 / -0.14 | 214.7 / 160.3 |
| SI 3 (diag) morn (1, 0.8, 120, 1) | gross-positive, cost-negative pre-2023 | 229 | 36.2 | -18.1 | 0.7 | 54.4 | 0.17 / -0.08 / 0.00 | 152.1 / 97.8 |
| SI 4 (diag) morn (-1, 0.3, 240, 1) | gross-positive, cost-negative pre-2023 | 563 | 24.6 | -29.8 | -10.3 | 54.4 | 0.21 / -0.25 / -0.09 | 50.7 / -3.6 |
| HG 1 (diag) morn (-1, 0.3, 240, 1) | gross-positive, cost-negative pre-2023 | 983 | 1.2 | -28.1 | -20.1 | 29.4 | 0.03 / -0.61 / -0.44 | 66.4 / 37.0 |
| HG 2 (diag) morn (1, 1.0, 240, -1) | gross-positive, cost-negative pre-2023 | 28 | 25.4 | -3.9 | 3.7 | 29.4 | 0.05 / -0.01 / 0.01 | 141.1 / 111.7 |
| HG 3 (diag) morn (1, 1.0, 120, 1) | positive pre-2023 | 28 | 44.2 | 14.8 | 22.5 | 29.4 | 0.11 / 0.04 / 0.06 | 82.1 / 52.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); GC: 1 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.80, p(top) = 0.69); HG: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); HO: 1 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.83, p(top) = 0.42); NQ: 0 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 1.00); RTY: 2 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.28, p(top) = 0.30); SI: 1 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.56, p(top) = 0.56); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 5 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.02 (GC morn (-1, 0.3, 240, -1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 4, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q32.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q32/ (`Q32_CO_all_selected_scored.csv`).

DONE Q32
