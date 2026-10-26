# REPORT Q34 - Q34: overnight (Globex) return sign traded with/against through the RTH day

**Verdict: FOUND-CANDIDATE (needs full verification). FOUND 2, LEAD 4, INSURANCE 0.** 28 selected cells (+15 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.36; best pair-window standalone Sharpe +1.47.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: overnight (Globex) return sign traded with/against through the RTH day.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      24 |         24 |         0 |               0.132 |                1 |          0 |            3 |
| CL    |      24 |         24 |         2 |               0.664 |                2 |          2 |            0 |
| ES    |      24 |         24 |         6 |               1.452 |                2 |          3 |            0 |
| GC    |      24 |         24 |        12 |               1.643 |                2 |         10 |            0 |
| HG    |      24 |         24 |         3 |               0.605 |                2 |          3 |            3 |
| HO    |      24 |         24 |         3 |               0.9   |                2 |          3 |            3 |
| NQ    |      24 |         24 |         4 |               1.501 |                2 |          2 |            0 |
| RTY   |      24 |         24 |         4 |               1.669 |                2 |          4 |            0 |
| SI    |      24 |         24 |         1 |               0.499 |                2 |          1 |            3 |
| ZN    |      24 |         24 |         0 |              -0.021 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    6 |            2.725 |               6 |      0.035 |                       0.79  |            0.686 |           1.146 |    0.285 |       1.452 |                1.735 |
| NQ    |     200 |                    4 |            3.86  |              10 |      0.55  |                       0.925 |            0.753 |           1.133 |    0.2   |       1.501 |                1.768 |
| RTY   |     200 |                    4 |            2.9   |               7 |      0.36  |                       1.197 |            0.726 |           1.146 |    0.025 |       1.669 |                1.768 |
| GC    |     200 |                   12 |            3.285 |               8 |      0     |                       1.128 |            0.702 |           1.165 |    0.055 |       1.643 |                1.787 |
| CL    |     200 |                    2 |            2.68  |               8 |      0.79  |                       0.569 |            0.682 |           1.171 |    0.585 |       0.664 |                1.744 |
| ZN    |     200 |                    0 |            0.095 |               2 |      1     |                     nan     |            0.419 |           0.749 |  nan     |     nan     |                0.749 |
| HO    |     200 |                    3 |            3.8   |              10 |      0.77  |                       0.681 |            0.76  |           1.174 |    0.585 |       0.856 |                1.908 |
| 6E    |     200 |                    0 |            1.46  |               7 |      1     |                     nan     |            0.666 |           1.211 |  nan     |     nan     |                1.451 |
| SI    |     200 |                    1 |            2.005 |               5 |      0.895 |                       0.342 |            0.688 |           1.171 |    0.81  |       0.342 |                1.46  |
| HG    |     200 |                    3 |            2.86  |               8 |      0.575 |                       0.413 |            0.682 |           1.111 |    0.84  |       0.605 |                1.67  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | onr (0, 0.0, 180, -1) | 516 | 2 | 1.45 | -0.63 | 1.17 | 0.81 / 0.96 | 0.30 / 0.33 / 0.26 | 0.23 | -0.09 | 1.00 | 0.11 | 1.00 | 829 | FOUND-CAND |
| ES 2 | onr (30, 0.0, 180, -1) | 502 | 2 | 1.21 | -0.88 | 1.22 | 1.22 / 1.17 | 0.22 / 0.36 / 0.37 | 0.20 | -0.07 | 1.00 | 0.09 | 0.50 | 807 | LEAD(gate3-7 fail: plateau ) |
| ES 3 | onr (0, 0.2, 180, -1) | 262 | 2 | 0.68 | -0.46 | 0.25 | -0.39 / 1.43 | 0.13 / -0.19 / -0.03 | 0.01 | 0.12 | 0.79 | -0.14 | 0.50 | 431 | NO |
| NQ 1 | onr (0, 0.0, 180, -1) | 516 | 2 | 1.50 | -0.54 | 0.87 | 0.21 / 1.86 | 0.34 / -0.11 / 0.09 | 0.22 | 0.29 | 0.96 | 0.01 | 0.50 | 829 | NO |
| NQ 2 | onr (30, 0.0, 180, -1) | 502 | 2 | 1.17 | -0.90 | 0.65 | 0.17 / 1.25 | 0.24 / 0.08 / -0.12 | 0.14 | 0.38 | 0.94 | -0.08 | 0.50 | 807 | NO |
| RTY 1 | onr (0, 0.2, 180, -1) | 287 | 2 | 1.67 | -0.14 | 1.10 | 0.37 / 0.88 | 0.22 / 0.24 / 0.15 | 0.16 | -0.33 | 1.00 | 0.00 | 1.00 | 455 | FOUND-CAND |
| RTY 2 | onr (0, 0.4, 180, -1) | 126 | 2 | 1.15 | 0.25 | 1.21 | 1.15 / 1.29 | 0.19 / 0.09 / 0.39 | 0.20 | -0.10 | 1.00 | 0.02 | 1.00 | 202 | NO |
| RTY 3 | onr (30, 0.2, 180, -1) | 282 | 2 | 1.00 | 0.06 | 0.55 | -0.02 / 1.24 | 0.12 / -0.02 / 0.16 | 0.05 | -0.40 | 0.93 | -0.12 | 0.50 | 448 | NO |
| RTY 4 | onr (30, 0.4, 180, -1) | 122 | 2 | 0.96 | 0.17 | 0.86 | 0.71 / 1.44 | 0.16 / -0.12 / 0.44 | 0.15 | -0.20 | 0.95 | -0.05 | 0.50 | 196 | NO |
| GC 1 | onr (30, 0.0, 360, 1) | 498 | 2 | 1.64 | -0.22 | 0.91 | 0.65 / 1.21 | 0.25 / -0.77 / 0.45 | 0.12 | 0.30 | 0.98 | -0.15 | 1.00 | 798 | NO |
| GC 2 | onr (0, 0.0, 360, 1) | 512 | 2 | 1.37 | -0.33 | 1.47 | 1.78 / 1.47 | 0.20 / -0.33 / 1.23 | 0.32 | 0.07 | 0.99 | 0.08 | 0.50 | 818 | NO |
| GC 3 | onr (0, 0.0, 180, 1) | 516 | 2 | 1.36 | -0.15 | 1.40 | 1.68 / 1.48 | 0.23 / -0.79 / 1.40 | 0.31 | 0.22 | 0.99 | 0.05 | 0.50 | 825 | NO |
| GC 4 | onr (30, 0.0, 180, 1) | 514 | 2 | 1.35 | -0.10 | 0.81 | 0.71 / 1.20 | 0.21 / -1.18 / 0.51 | 0.06 | 0.34 | 0.99 | -0.22 | 1.00 | 823 | NO |
| GC 5 | onr (0, 0.2, 180, 1) | 296 | 2 | 1.14 | -0.13 | 1.12 | 1.34 / 1.16 | 0.17 / -0.34 / 1.04 | 0.26 | 0.14 | 1.00 | 0.01 | 0.50 | 481 | NO |
| GC 6 | onr (30, 0.2, 360, 1) | 290 | 2 | 1.04 | -0.13 | 0.33 | -0.01 / 2.00 | 0.14 / -0.40 / -0.05 | -0.01 | 0.27 | 0.75 | -0.29 | 1.00 | 469 | NO |
| GC 7 | onr (0, 0.2, 360, 1) | 295 | 2 | 0.99 | -0.32 | 1.20 | 1.57 / 1.48 | 0.14 / 0.41 / 0.77 | 0.27 | 0.13 | 0.99 | 0.03 | 1.00 | 478 | LEAD |
| GC 8 | onr (30, 0.2, 180, 1) | 296 | 2 | 0.98 | -0.04 | 0.34 | 0.08 / 1.20 | 0.13 / -0.97 / 0.22 | -0.03 | 0.23 | 0.84 | -0.33 | 1.00 | 481 | NO |
| GC 9 | onr (0, 0.4, 180, 1) | 142 | 2 | 0.78 | -0.02 | 0.98 | 1.29 / 1.50 | 0.11 / 0.37 / 0.65 | 0.24 | 0.08 | 0.95 | -0.04 | 0.50 | 239 | LEAD |
| GC 10 | onr (0, 0.4, 360, 1) | 142 | 2 | 0.63 | -0.06 | 0.91 | 1.29 / 1.32 | 0.09 / 0.89 / 0.28 | 0.23 | 0.14 | 0.95 | -0.07 | 1.00 | 237 | LEAD |
| CL 1 | onr (30, 0.4, 180, -1) | 145 | 2 | 0.66 | -0.07 | 0.43 | 0.25 / 1.26 | 0.16 / -0.08 / 0.03 | 0.07 | 0.06 | 0.88 | -0.11 | 0.00 | 261 | NO |
| CL 2 | onr (0, 0.4, 180, -1) | 145 | 2 | 0.47 | -0.29 | 0.38 | 0.37 / 1.17 | 0.08 / -0.01 / 0.04 | 0.03 | -0.00 | 0.87 | -0.17 | 1.00 | 261 | NO |
| ZN 1 (diag) | onr (0, 0.4, 180, -1) | 112 | 1 | -0.02 | -1.08 | -0.90 | -2.54 / -0.32 | 0.00 / -0.40 / -0.46 | -0.35 | 0.15 | 0.85 | -0.34 | 0.00 | 184 | diag |
| ZN 2 (diag) | onr (30, 0.4, 360, -1) | 111 | 1 | -0.18 | -1.03 | -1.10 | -2.72 / 0.54 | -0.07 / -0.48 / -0.55 | -0.42 | 0.04 | 0.39 | -0.42 | 0.00 | 182 | diag |
| ZN 3 (diag) | onr (0, 0.4, 360, -1) | 111 | 0 | -0.21 | -0.79 | -1.09 | -3.15 / 0.09 | -0.05 / -0.38 / -0.49 | -0.34 | 0.15 | 0.43 | -0.36 | 0.00 | 182 | diag |
| HO 1 | onr (0, 0.4, 360, -1) | 150 | 2 | 0.86 | -0.11 | -0.17 | -0.88 / 1.46 | 0.14 / -0.57 / -0.60 | -0.13 | -0.19 | 0.53 | -0.44 | 0.00 | 260 | NO |
| HO 2 | onr (0, 0.4, 180, -1) | 150 | 2 | 0.61 | -0.03 | -0.46 | -1.21 / 1.51 | 0.10 / -0.58 / -0.92 | -0.24 | -0.23 | 0.32 | -0.57 | 0.00 | 260 | NO |
| HO 3 | onr (30, 0.4, 180, -1) | 150 | 2 | 0.58 | -0.18 | 0.01 | -0.31 / 1.36 | 0.12 / -0.71 / -0.36 | -0.12 | -0.15 | 0.49 | -0.46 | 0.00 | 260 | NO |
| HO 4 (diag) | onr (0, 0.0, 180, -1) | 515 | 1 | 0.90 | -0.27 | 0.05 | -0.61 / 1.30 | 0.18 / -0.78 / -0.32 | -0.09 | 0.06 | 0.53 | -0.31 | 0.00 | 823 | diag |
| HO 5 (diag) | onr (0, 0.2, 180, -1) | 323 | 1 | 0.82 | -0.27 | -0.39 | -1.29 / 1.61 | 0.17 / -0.73 / -0.75 | -0.18 | 0.03 | 0.26 | -0.46 | 0.00 | 516 | diag |
| HO 6 (diag) | onr (0, 0.0, 360, -1) | 512 | 1 | 0.53 | -0.14 | 0.21 | -0.05 / 1.49 | 0.07 / -0.64 / -0.07 | -0.07 | -0.31 | 0.71 | -0.29 | 0.00 | 818 | diag |
| 6E 1 (diag) | onr (30, 0.4, 360, -1) | 143 | 1 | 0.13 | 0.02 | 0.25 | 0.60 / 0.91 | -0.04 / -0.28 / 0.24 | -0.08 | 0.36 | 0.87 | -0.22 | 0.00 | 239 | diag |
| 6E 2 (diag) | onr (0, 0.0, 360, -1) | 514 | 1 | 0.02 | -0.61 | -0.49 | -1.28 / 0.70 | -0.01 / -0.14 / -0.31 | -0.20 | 0.47 | 0.58 | -0.28 | 0.00 | 823 | diag |
| 6E 3 (diag) | onr (0, 0.4, 180, 1) | 144 | 1 | -0.00 | -0.38 | -0.22 | -0.76 / 0.86 | 0.01 / -0.08 / -0.23 | -0.13 | -0.16 | 0.75 | -0.24 | 0.00 | 240 | diag |
| SI 1 | onr (0, 0.4, 360, 1) | 141 | 2 | 0.34 | -0.27 | 0.51 | 0.71 / 1.44 | 0.05 / 0.90 / -0.82 | -0.02 | 0.24 | 0.89 | -0.45 | 0.50 | 246 | NO |
| SI 2 (diag) | onr (30, 0.2, 360, 1) | 275 | 1 | 0.50 | -0.59 | -0.11 | -0.47 / 1.44 | 0.04 / 0.01 / -0.97 | -0.26 | 0.22 | 0.56 | -0.63 | 0.00 | 454 | diag |
| SI 3 (diag) | onr (30, 0.4, 360, 1) | 135 | 1 | 0.27 | -0.38 | -0.17 | -0.41 / 1.45 | 0.04 / 0.08 / -1.50 | -0.33 | 0.34 | 0.43 | -0.85 | 0.00 | 238 | diag |
| SI 4 (diag) | onr (0, 0.2, 360, 1) | 284 | 1 | 0.24 | -0.42 | 0.77 | 1.21 / 1.42 | -0.01 / 1.70 / -0.31 | 0.05 | 0.02 | 0.97 | -0.24 | 0.50 | 468 | diag |
| HG 1 | onr (30, 0.2, 360, 1) | 320 | 2 | 0.60 | -0.78 | 0.38 | 0.12 / 1.23 | 0.07 / -0.12 / 0.09 | -0.01 | 0.03 | 0.87 | -0.15 | 1.00 | 504 | NO |
| HG 2 | onr (0, 0.2, 360, 1) | 327 | 2 | 0.38 | -0.87 | 0.43 | 0.57 / 1.07 | 0.02 / 0.10 / 0.04 | -0.02 | 0.10 | 0.89 | -0.15 | 0.50 | 512 | NO |
| HG 3 | onr (30, 0.4, 360, 1) | 171 | 2 | 0.26 | -0.77 | -0.24 | -0.69 / 1.35 | -0.03 / -0.56 / -0.12 | -0.18 | -0.12 | 0.45 | -0.35 | 0.00 | 288 | NO |
| HG 4 (diag) | onr (30, 0.4, 180, 1) | 176 | 1 | 0.40 | -0.63 | -0.15 | -0.70 / 1.45 | 0.01 / -0.61 / -0.18 | -0.18 | -0.21 | 0.57 | -0.34 | 0.00 | 294 | diag |
| HG 5 (diag) | onr (30, 0.0, 360, 1) | 500 | 1 | 0.35 | -0.82 | 0.35 | -0.45 / 0.95 | 0.13 / -0.19 / -0.06 | -0.05 | 0.04 | 0.88 | -0.19 | 0.50 | 802 | diag |
| HG 6 (diag) | onr (0, 0.0, 360, 1) | 513 | 1 | 0.24 | -0.96 | 0.50 | 0.12 / 0.76 | 0.09 / 0.21 / -0.14 | -0.03 | 0.04 | 0.93 | -0.17 | 0.50 | 821 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 28 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 2 / 5 / 6 / 3 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 9 |
| standalone pair-window Sharpe above own random-entry null p95 | 15 |
| worst-decile corr <= +0.30 | 38 |
| plateau >= 0.75 | 11 |
| all-in uplift at 2x slippage >= +0.10 | 14 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 7 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E onr (30, 0.4, 360, -1) (diag) | clean | 0.01 | 0.02 | -145583 | -117060 | 464856 | -215510 | 0.02 | 41.9 | 1.42 | -88742 | 300716 | -124976 |
| 6E onr (30, 0.4, 360, -1) (diag) | H1 | -0.47 | -0.61 | -151721 | -116414 | 282490 | -208275 | -0.39 | 42.9 | 2.55 | -82233 | 183046 | -85595 |
| 6E onr (30, 0.4, 360, -1) (diag) | H2 | 1.28 | 2.32 | -133469 | -111781 | 244252 | -153832 | 1.96 | 38.9 | 2.73 | -90859 | 229912 | -95369 |
| 6E onr (30, 0.4, 360, -1) (diag) | all | 0.25 | 0.36 | -149857 | -119896 | 729730 | -215510 | 0.52 | 41.7 | 1.89 | -89066 | 300716 | -124976 |
| CL onr (30, 0.4, 180, -1) | clean | 0.65 | 1.15 | -107576 | -92427 | 255309 | -150307 | 2.32 | 41.9 | 1.62 | -81017 | 259928 | -83324 |
| CL onr (30, 0.4, 180, -1) | H1 | -0.57 | -0.86 | -71423 | -61917 | 328948 | -89215 | -0.27 | 53.6 | 2.75 | -82142 | 154797 | -84049 |
| CL onr (30, 0.4, 180, -1) | H2 | 0.47 | 1.09 | -165374 | -147216 | 840806 | -169614 | 0.39 | 50.0 | 2.52 | -101701 | 241241 | -101968 |
| CL onr (30, 0.4, 180, -1) | all | 0.43 | 0.87 | -128645 | -108356 | 840806 | -169614 | 0.99 | 45.8 | 2.00 | -87438 | 259928 | -101968 |
| ES onr (0, 0.0, 180, -1) | clean | 1.48 | 2.45 | -116977 | -88756 | 424571 | -229749 | 3.16 | 40.0 | 1.76 | -85240 | 291275 | -89997 |
| ES onr (0, 0.0, 180, -1) | H1 | 1.57 | 2.63 | -121987 | -115022 | 286097 | -142604 | 1.50 | 42.9 | 3.16 | -75369 | 149727 | -82837 |
| ES onr (0, 0.0, 180, -1) | H2 | 0.39 | 0.57 | -196760 | -159717 | 607248 | -211055 | 0.30 | 41.7 | 2.74 | -93486 | 231857 | -98569 |
| ES onr (0, 0.0, 180, -1) | all | 1.17 | 1.84 | -155464 | -123000 | 607248 | -229749 | 3.22 | 40.5 | 2.19 | -87381 | 291275 | -98569 |
| GC onr (0, 0.0, 180, 1) | clean | 1.40 | 2.42 | -110231 | -91940 | 474945 | -170599 | 2.67 | 41.9 | 1.69 | -80144 | 264338 | -91622 |
| GC onr (0, 0.0, 180, 1) | H1 | -1.22 | -1.60 | -290666 | -269548 | 1454819 | -310378 | -0.52 | 57.1 | 2.04 | -92973 | 188239 | -122395 |
| GC onr (0, 0.0, 180, 1) | H2 | 4.06 | 10.50 | -217192 | -165381 | 533879 | -219511 | 6.16 | 30.6 | 3.88 | -102550 | 211028 | -106460 |
| GC onr (0, 0.0, 180, 1) | all | 1.40 | 2.54 | -218433 | -174344 | 1454819 | -310378 | 2.61 | 42.3 | 2.26 | -90433 | 264338 | -122395 |
| HG onr (30, 0.2, 360, 1) | clean | 0.55 | 1.02 | -104536 | -87505 | 447808 | -156822 | 1.11 | 46.7 | 1.53 | -86821 | 254548 | -93725 |
| HG onr (30, 0.2, 360, 1) | H1 | -0.79 | -0.98 | -181460 | -155026 | 522752 | -242380 | -0.44 | 46.4 | 2.71 | -74573 | 170640 | -76071 |
| HG onr (30, 0.2, 360, 1) | H2 | 0.93 | 1.66 | -115368 | -88846 | 251031 | -158390 | 1.23 | 52.8 | 2.57 | -87291 | 228318 | -89759 |
| HG onr (30, 0.2, 360, 1) | all | 0.38 | 0.61 | -130566 | -103801 | 535108 | -242380 | 1.07 | 48.2 | 1.94 | -85889 | 254548 | -93725 |
| HO onr (30, 0.4, 180, -1) | clean | 0.62 | 1.02 | -123579 | -101799 | 361492 | -210600 | 1.56 | 38.1 | 1.58 | -81319 | 285230 | -87640 |
| HO onr (30, 0.4, 180, -1) | H1 | -2.96 | -3.08 | -173087 | -156541 | 761934 | -174131 | -0.96 | 60.7 | 2.12 | -92376 | 171992 | -102714 |
| HO onr (30, 0.4, 180, -1) | H2 | 0.17 | 0.27 | -529510 | -387634 | 1563286 | -701147 | 0.14 | 50.0 | 2.12 | -118259 | 282705 | -128060 |
| HO onr (30, 0.4, 180, -1) | all | 0.01 | 0.02 | -281093 | -208422 | 1563286 | -701147 | 0.03 | 44.6 | 1.80 | -94422 | 285230 | -128060 |
| NQ onr (0, 0.0, 180, -1) | clean | 1.55 | 2.59 | -122076 | -94998 | 353572 | -169429 | 3.97 | 38.1 | 1.80 | -84567 | 246268 | -88262 |
| NQ onr (0, 0.0, 180, -1) | H1 | 0.31 | 0.43 | -148015 | -141711 | 309290 | -153865 | 0.34 | 42.9 | 2.72 | -90560 | 173749 | -106720 |
| NQ onr (0, 0.0, 180, -1) | H2 | 0.14 | 0.20 | -224529 | -204189 | 657247 | -253997 | 0.12 | 41.7 | 2.57 | -95159 | 230244 | -105352 |
| NQ onr (0, 0.0, 180, -1) | all | 0.87 | 1.28 | -173964 | -144306 | 668658 | -253997 | 2.37 | 39.3 | 2.13 | -89872 | 246268 | -106720 |
| RTY onr (0, 0.4, 180, -1) | clean | 1.24 | 2.48 | -100695 | -82381 | 523872 | -148632 | 2.17 | 32.4 | 1.65 | -83846 | 304333 | -88118 |
| RTY onr (0, 0.4, 180, -1) | H1 | 1.02 | 1.67 | -143446 | -128912 | 285199 | -166189 | 1.00 | 28.6 | 2.92 | -68059 | 144021 | -83988 |
| RTY onr (0, 0.4, 180, -1) | H2 | 1.24 | 2.37 | -127351 | -96079 | 279627 | -144100 | 1.68 | 33.3 | 2.87 | -78695 | 207198 | -80242 |
| RTY onr (0, 0.4, 180, -1) | all | 1.21 | 2.27 | -120926 | -95742 | 523872 | -166189 | 3.61 | 31.5 | 2.11 | -82821 | 304333 | -88118 |
| SI onr (0, 0.4, 360, 1) | clean | 0.38 | 0.56 | -139005 | -106110 | 396883 | -276191 | 0.87 | 40.0 | 1.51 | -83873 | 308133 | -99298 |
| SI onr (0, 0.4, 360, 1) | H1 | 1.64 | 3.69 | -505909 | -441961 | 924438 | -620644 | 2.45 | 42.9 | 3.73 | -101830 | 245357 | -150513 |
| SI onr (0, 0.4, 360, 1) | H2 | -0.59 | -0.78 | -443074 | -372162 | 1008425 | -530063 | -0.53 | 36.1 | 1.66 | -152615 | 346652 | -162318 |
| SI onr (0, 0.4, 360, 1) | all | 0.51 | 0.92 | -368755 | -255284 | 1629068 | -620644 | 1.28 | 39.9 | 1.92 | -114023 | 346652 | -162318 |
| ZN onr (0, 0.4, 180, -1) (diag) | clean | -0.08 | -0.11 | -143516 | -119266 | 614846 | -206745 | -0.12 | 32.4 | 1.46 | -81231 | 300362 | -85625 |
| ZN onr (0, 0.4, 180, -1) (diag) | H1 | -2.23 | -2.40 | -107772 | -99946 | 364921 | -125681 | -1.00 | 35.7 | 2.43 | -85267 | 158137 | -87400 |
| ZN onr (0, 0.4, 180, -1) (diag) | H2 | -2.75 | -2.78 | -170073 | -137262 | 946375 | -226047 | -0.85 | 50.0 | 2.02 | -79665 | 223004 | -82524 |
| ZN onr (0, 0.4, 180, -1) (diag) | all | -0.90 | -1.13 | -147675 | -123637 | 1598648 | -226047 | -0.78 | 36.9 | 1.74 | -82272 | 300362 | -87400 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES onr (0, 0.0, 180, -1) | -8.6 | -4.1 | 12.2 | 12.6 | 12.7 / 13.9 | 21.3 / 34.3 | NO |
| NQ onr (0, 0.0, 180, -1) | -12.7 | -18.1 | 8.1 | 36.7 | 13.6 / 18.2 | -24.5 / 0.4 | NO |
| RTY onr (0, 0.4, 180, -1) | -9.3 | 14.5 | 22.0 | 3.6 | 13.8 / 19.4 | 19.1 / 23.5 | NO |
| GC onr (0, 0.0, 180, 1) | 11.6 | -47.9 | 4.2 | -14.8 | 12.1 / 25.9 | -55.9 / -19.7 | NO |
| CL onr (30, 0.4, 180, -1) | -20.9 | -9.6 | 10.0 | 29.5 | 6.0 / 20.3 | 17.6 / 21.2 | NO |
| ZN onr (0, 0.4, 180, -1) (diag) | -43.6 | -4.9 | 18.8 | 17.5 | 18.6 / 24.4 | 11.2 / 15.2 | NO |
| HO onr (30, 0.4, 180, -1) | -29.5 | -144.6 | -24.1 | -42.7 | -16.1 / 18.8 | -16.8 / 1.5 | NO |
| 6E onr (30, 0.4, 360, -1) (diag) | -25.9 | -47.8 | 8.3 | 12.1 | -49.0 / 9.6 | 10.2 / 11.6 | NO |
| SI onr (0, 0.4, 360, 1) | -7.2 | -148.0 | -52.1 | -38.5 | -6.4 / 17.3 | -161.4 / -96.1 | NO |
| HG onr (30, 0.2, 360, 1) | -23.7 | 2.4 | 12.1 | 27.8 | 3.8 / 12.4 | -2.9 / 14.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 onr (0, 0.0, 180, -1) | negative pre-2023 | 2686 | -5.0 | -34.1 | -20.0 | 29.1 | -0.09 / -0.63 / -0.37 | 147.5 / 118.2 |
| ES 2 onr (30, 0.0, 180, -1) | negative pre-2023 | 2630 | -14.9 | -44.0 | -29.9 | 29.1 | -0.30 / -0.88 / -0.60 | 118.7 / 89.4 |
| ES 3 onr (0, 0.2, 180, -1) | negative pre-2023 | 1433 | -9.4 | -38.7 | -24.5 | 29.4 | -0.11 / -0.46 / -0.29 | 111.2 / 81.9 |
| NQ 1 onr (0, 0.0, 180, -1) | negative pre-2023 | 2685 | -35.1 | -49.4 | -40.9 | 14.3 | -0.39 / -0.54 / -0.45 | 264.3 / 250.0 |
| NQ 2 onr (30, 0.0, 180, -1) | negative pre-2023 | 2630 | -56.8 | -71.1 | -62.6 | 14.3 | -0.72 / -0.90 / -0.79 | 172.5 / 158.2 |
| RTY 1 onr (0, 0.2, 180, -1) | gross-positive, cost-negative pre-2023 | 754 | 4.0 | -10.3 | -8.0 | 14.4 | 0.05 / -0.14 / -0.11 | 131.8 / 117.5 |
| RTY 2 onr (0, 0.4, 180, -1) | positive pre-2023 | 311 | 43.4 | 29.1 | 31.6 | 14.4 | 0.38 / 0.25 / 0.27 | 160.9 / 146.6 |
| RTY 3 onr (30, 0.2, 180, -1) | positive pre-2023 | 748 | 18.0 | 3.6 | 5.9 | 14.4 | 0.29 / 0.06 / 0.10 | 76.2 / 61.8 |
| RTY 4 onr (30, 0.4, 180, -1) | positive pre-2023 | 311 | 31.9 | 17.6 | 20.1 | 14.4 | 0.31 / 0.17 / 0.19 | 115.2 / 100.8 |
| GC 1 onr (30, 0.0, 360, 1) | gross-positive, cost-negative pre-2023 | 2587 | 10.3 | -13.9 | -4.2 | 24.3 | 0.17 / -0.22 / -0.07 | 181.6 / 157.2 |
| GC 2 onr (0, 0.0, 360, 1) | gross-positive, cost-negative pre-2023 | 2606 | 1.1 | -23.1 | -13.4 | 24.3 | 0.02 / -0.33 / -0.19 | 164.0 / 139.8 |
| GC 3 onr (0, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2668 | 15.4 | -8.9 | 0.8 | 24.3 | 0.28 / -0.15 / 0.02 | 140.8 / 116.5 |
| GC 4 onr (30, 0.0, 180, 1) | gross-positive, cost-negative pre-2023 | 2658 | 18.7 | -5.6 | 4.2 | 24.3 | 0.37 / -0.10 / 0.09 | 129.0 / 104.8 |
| GC 5 onr (0, 0.2, 180, 1) | gross-positive, cost-negative pre-2023 | 1482 | 14.6 | -9.7 | 0.2 | 24.4 | 0.19 / -0.13 / 0.00 | 147.5 / 123.1 |
| GC 6 onr (30, 0.2, 360, 1) | gross-positive, cost-negative pre-2023 | 1447 | 13.6 | -10.8 | -0.9 | 24.4 | 0.16 / -0.13 / -0.01 | 141.6 / 117.2 |
| GC 7 onr (0, 0.2, 360, 1) | negative pre-2023 | 1456 | -4.5 | -28.9 | -19.0 | 24.4 | -0.05 / -0.32 / -0.21 | 144.4 / 120.0 |
| GC 8 onr (30, 0.2, 180, 1) | gross-positive, cost-negative pre-2023 | 1476 | 21.7 | -2.7 | 7.2 | 24.4 | 0.31 / -0.04 / 0.10 | 116.7 / 92.3 |
| GC 9 onr (0, 0.4, 180, 1) | gross-positive, cost-negative pre-2023 | 729 | 22.3 | -2.0 | 7.8 | 24.4 | 0.19 / -0.02 / 0.07 | 144.1 / 119.7 |
| GC 10 onr (0, 0.4, 360, 1) | gross-positive, cost-negative pre-2023 | 720 | 16.6 | -7.8 | 2.1 | 24.4 | 0.13 / -0.06 / 0.02 | 116.6 / 92.3 |
| CL 1 onr (30, 0.4, 180, -1) | gross-positive, cost-negative pre-2023 | 708 | 17.0 | -7.4 | -5.0 | 24.4 | 0.15 / -0.07 / -0.04 | 99.2 / 74.9 |
| CL 2 onr (0, 0.4, 180, -1) | negative pre-2023 | 708 | -11.5 | -35.9 | -33.5 | 24.4 | -0.09 / -0.29 / -0.27 | 73.4 / 49.1 |
| ZN 1 (diag) onr (0, 0.4, 180, -1) | negative pre-2023 | 647 | -1.7 | -37.3 | -42.4 | 35.6 | -0.05 / -1.08 / -1.23 | 32.9 / -2.7 |
| ZN 2 (diag) onr (30, 0.4, 360, -1) | negative pre-2023 | 636 | -0.1 | -35.7 | -40.8 | 35.6 | -0.00 / -1.03 / -1.17 | 26.5 / -9.1 |
| ZN 3 (diag) onr (0, 0.4, 360, -1) | gross-positive, cost-negative pre-2023 | 637 | 4.4 | -31.2 | -36.3 | 35.6 | 0.11 / -0.79 / -0.91 | 23.8 / -11.8 |
| HO 1 onr (0, 0.4, 360, -1) | negative pre-2023 | 681 | -13.4 | -26.1 | -24.6 | 12.8 | -0.06 / -0.11 / -0.10 | 176.7 / 163.9 |
| HO 2 onr (0, 0.4, 180, -1) | gross-positive, cost-negative pre-2023 | 690 | 7.9 | -4.8 | -3.3 | 12.8 | 0.05 / -0.03 / -0.02 | 109.0 / 96.2 |
| HO 3 onr (30, 0.4, 180, -1) | negative pre-2023 | 681 | -16.1 | -28.9 | -27.3 | 12.8 | -0.10 / -0.18 / -0.17 | 96.3 / 83.6 |
| HO 4 (diag) onr (0, 0.0, 180, -1) | negative pre-2023 | 2645 | -6.3 | -19.1 | -17.5 | 12.8 | -0.09 / -0.27 / -0.25 | 68.0 / 55.3 |
| HO 5 (diag) onr (0, 0.2, 180, -1) | negative pre-2023 | 1497 | -10.7 | -23.4 | -22.0 | 12.8 | -0.13 / -0.27 / -0.25 | 84.2 / 71.4 |
| HO 6 (diag) onr (0, 0.0, 360, -1) | negative pre-2023 | 2596 | -0.1 | -12.9 | -11.4 | 12.8 | -0.01 / -0.14 / -0.12 | 60.5 / 47.8 |
| 6E 1 (diag) onr (30, 0.4, 360, -1) | positive pre-2023 | 827 | 18.1 | 1.2 | 0.0 | 16.9 | 0.32 / 0.02 / 0.00 | 17.3 / 0.4 |
| 6E 2 (diag) onr (0, 0.0, 360, -1) | negative pre-2023 | 2629 | -2.7 | -19.5 | -20.7 | 16.8 | -0.09 / -0.61 / -0.64 | 15.1 / -1.7 |
| 6E 3 (diag) onr (0, 0.4, 180, 1) | negative pre-2023 | 838 | -1.8 | -18.7 | -19.9 | 16.9 | -0.04 / -0.38 / -0.41 | 19.2 / 2.3 |
| SI 1 onr (0, 0.4, 360, 1) | gross-positive, cost-negative pre-2023 | 671 | 4.1 | -50.3 | -31.2 | 54.4 | 0.02 / -0.27 / -0.17 | 150.5 / 96.2 |
| SI 2 (diag) onr (30, 0.2, 360, 1) | negative pre-2023 | 1410 | -9.5 | -63.9 | -44.8 | 54.4 | -0.09 / -0.59 / -0.41 | 143.5 / 89.2 |
| SI 3 (diag) onr (30, 0.4, 360, 1) | negative pre-2023 | 666 | -18.5 | -72.9 | -53.8 | 54.4 | -0.10 / -0.38 / -0.28 | 135.7 / 81.4 |
| SI 4 (diag) onr (0, 0.2, 360, 1) | gross-positive, cost-negative pre-2023 | 1423 | 7.7 | -46.7 | -27.6 | 54.4 | 0.07 / -0.42 / -0.25 | 100.5 / 46.2 |
| HG 1 onr (30, 0.2, 360, 1) | negative pre-2023 | 1633 | -10.8 | -40.2 | -32.3 | 29.4 | -0.22 / -0.78 / -0.63 | 83.1 / 53.8 |
| HG 2 onr (0, 0.2, 360, 1) | negative pre-2023 | 1645 | -19.2 | -48.6 | -40.7 | 29.4 | -0.35 / -0.87 / -0.73 | 64.7 / 35.4 |
| HG 3 onr (30, 0.4, 360, 1) | negative pre-2023 | 945 | -24.2 | -53.6 | -45.7 | 29.4 | -0.35 / -0.77 / -0.66 | 48.1 / 18.7 |
| HG 4 (diag) onr (30, 0.4, 180, 1) | negative pre-2023 | 968 | -9.7 | -39.1 | -31.2 | 29.4 | -0.17 / -0.63 / -0.50 | 64.8 / 35.5 |
| HG 5 (diag) onr (30, 0.0, 360, 1) | negative pre-2023 | 2597 | -5.4 | -34.5 | -26.7 | 29.2 | -0.13 / -0.82 / -0.63 | 109.2 / 80.0 |
| HG 6 (diag) onr (0, 0.0, 360, 1) | negative pre-2023 | 2618 | -13.6 | -42.8 | -35.0 | 29.2 | -0.31 / -0.96 / -0.79 | 101.6 / 72.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 1.00); CL: 2 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.79, p(top) = 0.58); ES: 6 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.04, p(top) = 0.28); GC: 12 cells pass the clean rule against a replicate mean of 3.3 (p(count) = 0.00, p(top) = 0.06); HG: 3 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.57, p(top) = 0.84); HO: 3 cells pass the clean rule against a replicate mean of 3.8 (p(count) = 0.77, p(top) = 0.58); NQ: 4 cells pass the clean rule against a replicate mean of 3.9 (p(count) = 0.55, p(top) = 0.20); RTY: 4 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 0.36, p(top) = 0.03); SI: 1 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.90, p(top) = 0.81); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 28 selected cells, 5 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.36 (GC onr (0, 0.0, 180, 1)); bootstrap lower bound > 0 for 9 cells; plateau >= 0.75 for 11; 2x-slippage all-in uplift >= +0.10 for 14; gate_add PASS at some share: 7 (cell-share pairs).
- Gate-3 cell ES onr (0, 0.0, 180, -1): uplift +0.30/+0.33/+0.26, boot lo +0.11, plateau 1.00, 2x-slip +0.23, wd corr -0.09, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell ES onr (30, 0.0, 180, -1): uplift +0.22/+0.36/+0.37, boot lo +0.09, plateau 0.50, 2x-slip +0.20, wd corr -0.07, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY onr (0, 0.2, 180, -1): uplift +0.22/+0.24/+0.15, boot lo +0.00, plateau 1.00, 2x-slip +0.16, wd corr -0.33, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell GC onr (0, 0.2, 360, 1): uplift +0.14/+0.41/+0.77, boot lo +0.03, plateau 1.00, 2x-slip +0.27, wd corr +0.13, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell GC onr (0, 0.4, 180, 1): uplift +0.11/+0.37/+0.65, boot lo -0.04, plateau 0.50, 2x-slip +0.24, wd corr +0.08, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 13, 'negative pre-2023': 12, 'positive pre-2023': 3}.

- **Manual review of the FOUND-CANDIDATE tags: ES 1 and RTY 1 (overnight-return reversal at the US index open).** Rule: Globex return (18:00 ET open to the 09:29 ET close) of the index future, trade AGAINST it from the 09:30 RTH open (entry at the open, signal row 09:29), hold 180 minutes, no stop. ES: threshold 0 (all days); RTY: only when the overnight move is at least 0.2 x ADR20. **ES 1:** standalone Sharpe 1.48 / 1.57 / 0.39 on clean / H1 / H2; uplift at 20% share +0.30 / +0.33 / +0.26 (10%: +0.16/+0.19/+0.15; 30%: +0.42/+0.42/+0.30; 50%: +0.59/+0.45/+0.20); bootstrap lower bound +0.11; worst week +19.4% at 20% (inside the 20% allowance by 0.6 points; +32.3% at 30% fails); own null (all-in) p95 0.61 vs 1.17 passes, out-of-selection (H1+H2) Sharpe 0.81 vs null p95 0.96 does not; plateau 1.00; 2x slippage all-in +0.23; worst-decile correlation -0.09; ERA flag NEGATIVE pre-2023 (net weekly Sharpe -0.63, gross -0.09 in 2013-22: the effect does not exist before 2023, so it depends on the modern structure). **RTY 1:** +0.22 / +0.24 / +0.15 at 20%, bootstrap lower bound +0.00, plateau 1.00, 2x-slip +0.16, wd corr -0.33, standalone Sharpe H2 -0.04 (out-of-selection 0.37 vs null 0.88), ERA gross-positive, cost-negative. **Pre-registered replication (amendment 2): ES 1 holds 1 of 4** (H0 2023-02..07 standalone Sharpe +0.88 on 128 trades holds; cross-instrument RTY +0.12 is 39% of ES's +0.29 and fails the 50% rule; alternating months odd +0.11 / even +0.41: odd is 36% of the full uplift and fails); RTY 1 also 1 of 4 (H0 +1.08 on 67 trades; ES cross +0.05; odd +0.06 / even +0.27). Therefore LEAD (strong), not FOUND-PENDING. **Same ES cell on other markets (no selection on them, all-in uplift at 20%):** ES +0.29, NQ +0.23, RTY +0.12, YM +0.09 positive; GC -0.72, CL -0.18, ZN -0.32, HO -0.07, 6E -0.18, SI -0.84, HG -0.26 negative: the effect is confined to the four US equity-index futures (NQ included), a coherent cross-section. Sizing: ES 22.0 contracts at 100% of pair volatility, 4.4 ES at 20% share; worst single trade -$10.3k per ES contract = about -$45k at 4.4 contracts (no stop); RTY 46.0 contracts at 100%, 9.2 at 20%, worst trade -$3.6k per contract = about -$33k. Because the sleeve would trade ES (or NQ) in the same session as the pair, an ES sleeve does not net against the NQ pair lots; an NQ version would need its own account. Mechanism in one sentence: part of the index future's overnight (Asia/London) move is liquidity-driven and reverts when US cash-market liquidity arrives at the open; it plausibly depends on the current structure (zero before 2023). Forward test: the frozen ES 1 definition goes to the forward-weeks watcher (R5-style) and the sign test needs >= 8 post-freeze weeks.

- GC overnight CONTINUATION (Q34 GC 7: Globex return >= 0.2 x ADR20 traded WITH it from the RTH open, hold 360 min): uplift +0.14 / +0.41 / +0.77 at 20%, bootstrap lower bound +0.03, plateau 1.00, 2x-slip +0.27, wd corr +0.13, but worst week +33.6% at 20% (fails the allowance), H1 standalone Sharpe 0.16, out-of-selection 1.57 vs null 1.48, replication 0 of 4 (H0 -0.52 on 57 trades; ES -0.06, RTY -0.15; odd months 0.43 / even 0.15), ERA negative pre-2023; 22.9 GC contracts at 100%, 4.6 at 20% share, worst trade -$12.5k per contract = about -$57k: weak LEAD.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q34.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q34/ (`Q34_CO_all_selected_scored.csv`).

DONE Q34
