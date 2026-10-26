# REPORT Q38 - Q38: time-at-extreme: new day high/low after N bars since the previous extreme, with/against

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 19 selected cells (+30 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.08; best pair-window standalone Sharpe +0.81.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: time-at-extreme: new day high/low after N bars since the previous extreme, with/against.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      18 |         18 |         0 |              -0.431 |                1 |          0 |            3 |
| CL    |      18 |         18 |         4 |               0.825 |                2 |          4 |            3 |
| ES    |      18 |         18 |         3 |               1.029 |                2 |          3 |            3 |
| GC    |      18 |         18 |         1 |               0.748 |                2 |          1 |            3 |
| HG    |      18 |         18 |         0 |              -0.266 |                1 |          0 |            3 |
| HO    |      18 |         18 |         2 |               0.598 |                2 |          2 |            3 |
| NQ    |      18 |         18 |         6 |               1.133 |                2 |          6 |            3 |
| RTY   |      18 |         18 |         3 |               0.737 |                2 |          3 |            3 |
| SI    |      18 |         18 |         0 |               0.463 |                1 |          0 |            3 |
| ZN    |      18 |         18 |         0 |              -1.71  |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    3 |            1.52  |               8 |      0.165 |                       0.659 |            0.586 |           1.184 |    0.255 |       1.029 |                1.492 |
| NQ    |     200 |                    6 |            3.365 |               9 |      0.075 |                       0.819 |            0.719 |           1.139 |    0.3   |       1.133 |                1.801 |
| RTY   |     200 |                    3 |            2.11  |               7 |      0.365 |                       0.551 |            0.692 |           1.135 |    0.555 |       0.737 |                1.634 |
| GC    |     200 |                    1 |            1.58  |               5 |      0.85  |                       0.748 |            0.67  |           1.275 |    0.31  |       0.748 |                1.47  |
| CL    |     200 |                    4 |            0.99  |               5 |      0.015 |                       0.594 |            0.634 |           1.305 |    0.315 |       0.825 |                1.453 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| HO    |     200 |                    2 |            2.585 |               6 |      0.76  |                       0.534 |            0.706 |           1.192 |    0.71  |       0.598 |                1.554 |
| 6E    |     200 |                    0 |            0.265 |               2 |      1     |                     nan     |            0.473 |           0.88  |  nan     |     nan     |                0.88  |
| SI    |     200 |                    0 |            0.645 |               4 |      1     |                     nan     |            0.549 |           1.112 |  nan     |     nan     |                1.114 |
| HG    |     200 |                    0 |            0.8   |               4 |      1     |                     nan     |            0.572 |           1.259 |  nan     |     nan     |                1.423 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | ext (12, 0, 60, 1) | 548 | 2 | 1.03 | -0.30 | 0.72 | 0.05 / 0.56 | 0.13 / -0.12 / -0.09 | -0.02 | -0.26 | 1.00 | -0.08 | 0.00 | 851 | NO |
| ES 2 | ext (6, 0, 60, 1) | 931 | 2 | 0.75 | -1.08 | 0.30 | -0.70 / 0.46 | 0.07 / -0.22 / -0.20 | -0.12 | -0.07 | 0.99 | -0.17 | 0.00 | 1461 | NO |
| ES 3 | ext (12, 0, 180, -1) | 344 | 2 | 0.20 | -0.52 | 0.17 | 0.23 / 1.13 | -0.03 / -0.12 / 0.15 | -0.06 | -0.29 | 0.79 | -0.19 | 0.00 | 536 | NO |
| ES 4 (diag) | ext (12, 0, 120, 1) | 479 | 1 | 0.69 | -0.34 | 0.56 | 0.44 / 0.95 | 0.06 / 0.07 / -0.06 | -0.02 | -0.31 | 0.97 | -0.11 | 0.50 | 737 | diag |
| ES 5 (diag) | ext (24, 0, 60, 1) | 232 | 1 | 0.47 | -0.11 | 0.36 | -0.00 / 0.84 | 0.03 / -0.12 / -0.03 | -0.05 | -0.00 | 0.92 | -0.13 | 0.00 | 331 | diag |
| ES 6 (diag) | ext (24, 0, 180, 1) | 147 | 1 | 0.43 | -0.39 | 0.52 | 0.67 / 1.09 | 0.07 / -0.15 / 0.18 | 0.04 | -0.49 | 0.94 | -0.06 | 0.50 | 222 | diag |
| NQ 1 | ext (6, 0, 60, 1) | 841 | 2 | 1.13 | 0.02 | 0.81 | 0.34 / 1.21 | 0.13 / -0.01 / 0.02 | 0.06 | -0.07 | 0.97 | -0.09 | 0.50 | 1338 | NO |
| NQ 2 | ext (6, 0, 120, 1) | 674 | 2 | 1.08 | -0.39 | 0.71 | 0.29 / 1.32 | 0.13 / 0.06 / -0.07 | 0.06 | -0.16 | 0.96 | -0.12 | 0.50 | 1063 | NO |
| NQ 3 | ext (6, 0, 180, 1) | 454 | 2 | 0.95 | -0.46 | 0.61 | 0.09 / 1.32 | 0.11 / 0.13 / -0.23 | 0.02 | -0.19 | 0.91 | -0.16 | 0.50 | 737 | NO |
| NQ 4 | ext (12, 0, 120, 1) | 403 | 2 | 0.67 | -0.06 | 0.81 | 0.99 / 1.38 | 0.06 / 0.39 / -0.11 | 0.06 | -0.37 | 0.95 | -0.08 | 0.00 | 628 | NO |
| NQ 5 | ext (24, 0, 120, 1) | 203 | 2 | 0.56 | 0.14 | 0.55 | 0.47 / 1.45 | 0.05 / 0.12 / 0.02 | 0.04 | -0.49 | 0.81 | -0.10 | 0.50 | 296 | NO |
| NQ 6 | ext (12, 0, 60, 1) | 469 | 2 | 0.52 | -0.02 | 0.72 | 1.20 / 1.44 | 0.01 / 0.23 / 0.01 | 0.03 | -0.07 | 0.93 | -0.09 | 0.50 | 734 | NO |
| NQ 7 (diag) | ext (24, 0, 180, 1) | 136 | 1 | 0.79 | 0.29 | 0.67 | 0.29 / 1.21 | 0.12 / 0.13 / 0.01 | 0.08 | -0.48 | 0.91 | -0.05 | 0.50 | 207 | diag |
| NQ 8 (diag) | ext (12, 0, 180, 1) | 298 | 1 | 0.22 | 0.03 | 0.36 | 0.59 / 1.18 | -0.00 / 0.47 / -0.28 | -0.00 | -0.09 | 0.77 | -0.15 | 0.50 | 469 | diag |
| NQ 9 (diag) | ext (24, 0, 60, 1) | 216 | 1 | 0.09 | 0.28 | -0.10 | -0.53 / 1.30 | -0.06 / -0.08 / -0.14 | -0.10 | 0.51 | 0.44 | -0.23 | 0.00 | 310 | diag |
| RTY 1 | ext (24, 0, 180, 1) | 127 | 2 | 0.74 | -0.37 | 0.34 | -0.69 / 1.44 | 0.09 / -0.16 / -0.10 | -0.00 | -0.34 | 0.82 | -0.12 | 0.50 | 189 | NO |
| RTY 2 | ext (12, 0, 60, 1) | 470 | 2 | 0.61 | -0.92 | 0.28 | -0.58 / 1.12 | 0.09 / 0.10 / -0.17 | -0.02 | 0.14 | 0.88 | -0.10 | 1.00 | 749 | NO |
| RTY 3 | ext (24, 0, 60, 1) | 194 | 2 | 0.30 | -0.76 | 0.30 | 0.04 / 1.35 | 0.04 / 0.06 / -0.04 | -0.00 | 0.05 | 0.84 | -0.09 | 1.00 | 301 | NO |
| RTY 4 (diag) | ext (6, 0, 60, 1) | 777 | 1 | 0.16 | -1.23 | 0.15 | 0.10 / 0.61 | 0.01 / 0.25 / -0.23 | -0.07 | 0.55 | 0.94 | -0.15 | 0.00 | 1234 | diag |
| RTY 5 (diag) | ext (24, 0, 120, 1) | 188 | 1 | -0.09 | -0.47 | 0.10 | 0.32 / 0.92 | -0.00 / 0.11 / 0.04 | -0.00 | -0.49 | 0.74 | -0.11 | 0.50 | 291 | diag |
| RTY 6 (diag) | ext (6, 0, 180, -1) | 448 | 1 | -0.10 | 0.49 | -0.42 | -0.81 / 1.40 | -0.06 / -0.97 / 0.38 | -0.15 | -0.85 | 0.49 | -0.31 | 0.00 | 707 | diag |
| GC 1 | ext (24, 0, 120, 1) | 204 | 2 | 0.75 | -0.45 | -0.14 | -0.86 / 1.14 | 0.09 / -1.19 / 0.04 | -0.15 | -0.41 | 0.61 | -0.41 | 0.00 | 340 | NO |
| GC 2 (diag) | ext (12, 0, 120, 1) | 502 | 1 | 0.40 | -0.23 | 0.06 | -0.05 / 1.09 | -0.00 / -0.93 / -0.36 | -0.27 | -0.35 | 0.73 | -0.66 | 0.00 | 813 | diag |
| GC 3 (diag) | ext (12, 0, 60, 1) | 577 | 1 | 0.37 | -0.34 | -0.14 | -0.36 / 0.95 | -0.01 / -0.69 / -1.08 | -0.40 | 0.52 | 0.69 | -0.73 | 0.00 | 946 | diag |
| GC 4 (diag) | ext (6, 0, 60, -1) | 903 | 1 | 0.26 | -1.82 | 0.09 | 0.06 / 1.23 | 0.06 / -1.56 / 0.29 | -0.25 | -0.27 | 0.88 | -0.64 | 0.00 | 1466 | diag |
| CL 1 | ext (12, 0, 120, 1) | 503 | 2 | 0.83 | -0.49 | -0.64 | -2.13 / 0.77 | 0.14 / -0.56 / -0.97 | -0.33 | -0.37 | 0.48 | -0.47 | 0.00 | 826 | NO |
| CL 2 | ext (24, 0, 60, 1) | 216 | 2 | 0.69 | -0.23 | -0.45 | -1.49 / 1.08 | 0.07 / -0.51 / -0.61 | -0.27 | -0.40 | 0.59 | -0.43 | 0.00 | 371 | NO |
| CL 3 | ext (12, 0, 60, 1) | 570 | 2 | 0.51 | -0.34 | -0.93 | -2.46 / 0.54 | 0.08 / -0.79 / -0.88 | -0.45 | -0.07 | 0.56 | -0.52 | 0.00 | 943 | NO |
| CL 4 | ext (24, 0, 120, 1) | 209 | 2 | 0.35 | -0.10 | -0.35 | -1.03 / 0.94 | 0.03 / -0.45 / -0.39 | -0.21 | -0.39 | 0.55 | -0.38 | 0.00 | 358 | NO |
| CL 5 (diag) | ext (24, 0, 180, 1) | 152 | 1 | 0.28 | -0.18 | -0.14 | -0.52 / 0.98 | 0.02 / -0.10 / -0.48 | -0.17 | -0.41 | 0.63 | -0.34 | 0.00 | 263 | diag |
| CL 6 (diag) | ext (6, 0, 120, 1) | 763 | 1 | -0.21 | -0.33 | -0.90 | -1.67 / 0.93 | -0.06 / -0.34 / -0.94 | -0.45 | -0.27 | 0.42 | -0.55 | 0.00 | 1228 | diag |
| CL 7 (diag) | ext (12, 0, 180, 1) | 386 | 1 | -0.30 | -0.21 | -0.90 | -1.54 / 1.10 | -0.05 / -0.34 / -0.88 | -0.37 | -0.01 | 0.20 | -0.54 | 0.00 | 627 | diag |
| ZN 1 (diag) | ext (24, 0, 180, 1) | 169 | 0 | -1.71 | -1.64 | -1.87 | -2.29 / -1.30 | -0.33 / -0.64 / -0.10 | -0.67 | -0.35 | 0.75 | -0.51 | 0.00 | 279 | diag |
| ZN 2 (diag) | ext (12, 0, 180, 1) | 402 | 0 | -1.95 | -2.38 | -2.59 | -4.26 / -2.17 | -0.39 / -0.96 / -0.33 | -0.96 | -0.35 | 0.84 | -0.63 | 0.00 | 651 | diag |
| ZN 3 (diag) | ext (24, 0, 180, -1) | 169 | 0 | -2.06 | -2.39 | -2.36 | -2.97 / -1.09 | -0.46 / -0.40 / -0.66 | -0.78 | 0.41 | 0.49 | -0.68 | 0.00 | 279 | diag |
| HO 1 | ext (6, 0, 60, 1) | 1117 | 2 | 0.60 | 0.16 | -0.18 | -0.88 / 0.92 | 0.07 / -0.56 / -0.45 | -0.20 | 0.63 | 0.60 | -0.39 | 0.00 | 1812 | NO |
| HO 2 | ext (6, 0, 180, 1) | 637 | 2 | 0.47 | -0.55 | -0.05 | -0.37 / 1.34 | 0.01 / -0.29 / -0.45 | -0.17 | 0.40 | 0.57 | -0.42 | 0.00 | 1038 | NO |
| HO 3 (diag) | ext (24, 0, 120, 1) | 241 | 1 | 0.49 | 0.49 | 0.78 | 1.13 / 1.71 | 0.11 / 0.02 / 0.05 | 0.08 | 0.14 | 0.93 | -0.17 | 0.50 | 407 | diag |
| HO 4 (diag) | ext (24, 0, 60, 1) | 250 | 1 | 0.27 | 0.55 | 0.71 | 1.22 / 1.47 | 0.05 / -0.02 / 0.10 | 0.04 | -0.04 | 0.93 | -0.17 | 1.00 | 424 | diag |
| HO 5 (diag) | ext (12, 0, 180, -1) | 436 | 1 | 0.05 | -0.26 | -0.10 | -0.25 / 1.31 | -0.01 / -0.08 / -0.16 | -0.08 | -0.43 | 0.55 | -0.29 | 0.00 | 709 | diag |
| 6E 1 (diag) | ext (24, 0, 120, -1) | 238 | 1 | -0.43 | -0.70 | -0.79 | -1.26 / 0.62 | -0.13 / -0.08 / -0.55 | -0.35 | 0.53 | 0.53 | -0.40 | 0.00 | 375 | diag |
| 6E 2 (diag) | ext (24, 0, 180, -1) | 180 | 0 | -0.45 | -0.76 | -0.48 | -0.80 / 0.59 | -0.11 / -0.14 / -0.10 | -0.24 | 0.10 | 0.69 | -0.31 | 0.00 | 286 | diag |
| 6E 3 (diag) | ext (12, 0, 180, -1) | 409 | 0 | -0.59 | -0.85 | -0.62 | -0.66 / 0.28 | -0.12 / -0.29 / -0.03 | -0.26 | -0.28 | 0.80 | -0.31 | 0.00 | 655 | diag |
| SI 1 (diag) | ext (12, 0, 120, 1) | 473 | 1 | 0.46 | -1.06 | -0.27 | -0.62 / 1.25 | 0.02 / -1.20 / -0.92 | -0.53 | 0.48 | 0.46 | -0.86 | 0.00 | 782 | diag |
| SI 2 (diag) | ext (12, 0, 180, 1) | 383 | 1 | 0.31 | -0.82 | -0.45 | -0.82 / 1.20 | 0.01 / -2.44 / -0.90 | -0.74 | 0.58 | 0.46 | -1.29 | 0.00 | 630 | diag |
| SI 3 (diag) | ext (24, 0, 120, 1) | 156 | 1 | 0.17 | -0.79 | 0.54 | 0.83 / 1.38 | -0.01 / -0.99 / -0.53 | -0.43 | 0.56 | 0.92 | -0.88 | 0.00 | 294 | diag |
| HG 1 (diag) | ext (24, 0, 60, -1) | 201 | 1 | -0.27 | -1.06 | -0.09 | -1.23 / 0.70 | 0.08 / -0.54 / -0.13 | -0.17 | -0.41 | 0.86 | -0.27 | 0.00 | 338 | diag |
| HG 2 (diag) | ext (24, 0, 120, -1) | 194 | 1 | -0.28 | -0.86 | -0.34 | -1.59 / 0.97 | 0.09 / -1.14 / -0.39 | -0.30 | 0.21 | 0.51 | -0.49 | 0.00 | 325 | diag |
| HG 3 (diag) | ext (12, 0, 180, 1) | 374 | 1 | -0.33 | -1.01 | 0.30 | -0.22 / 0.79 | 0.00 / -0.15 / -0.27 | -0.19 | 0.34 | 0.94 | -0.31 | 0.00 | 614 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 19 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 17 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 38 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E ext (12, 0, 180, -1) (diag) | clean | -0.59 | -0.73 | -154773 | -119502 | 915454 | -284934 | -0.58 | 51.4 | 1.34 | -90322 | 258554 | -94584 |
| 6E ext (12, 0, 180, -1) (diag) | H1 | -0.76 | -0.91 | -154089 | -128157 | 314627 | -156215 | -0.52 | 50.0 | 2.54 | -91899 | 159118 | -108175 |
| 6E ext (12, 0, 180, -1) (diag) | H2 | -0.57 | -0.74 | -114522 | -108353 | 468144 | -115704 | -0.35 | 52.8 | 2.45 | -81087 | 237222 | -81323 |
| 6E ext (12, 0, 180, -1) (diag) | all | -0.62 | -0.76 | -153871 | -122315 | 1397359 | -284934 | -0.62 | 51.8 | 1.78 | -90674 | 258554 | -108175 |
| CL ext (24, 0, 120, 1) | clean | 0.33 | 0.59 | -99716 | -85195 | 683006 | -116820 | 0.44 | 47.6 | 1.49 | -85498 | 279309 | -93863 |
| CL ext (24, 0, 120, 1) | H1 | -2.75 | -3.00 | -106547 | -98098 | 494709 | -116359 | -1.00 | 71.4 | 2.38 | -81340 | 158900 | -87240 |
| CL ext (24, 0, 120, 1) | H2 | -0.71 | -0.94 | -312650 | -265493 | 1098873 | -324862 | -0.44 | 50.0 | 2.09 | -96590 | 231115 | -120292 |
| CL ext (24, 0, 120, 1) | all | -0.35 | -0.51 | -190647 | -143300 | 1574371 | -324862 | -0.43 | 52.4 | 1.76 | -88662 | 279309 | -120292 |
| ES ext (12, 0, 60, 1) | clean | 1.02 | 2.73 | -73401 | -58939 | 185598 | -97173 | 5.01 | 43.8 | 1.59 | -83351 | 247442 | -90637 |
| ES ext (12, 0, 60, 1) | H1 | 0.09 | 0.15 | -54766 | -52134 | 158961 | -61300 | 0.09 | 57.1 | 2.70 | -81410 | 143185 | -85550 |
| ES ext (12, 0, 60, 1) | H2 | 0.02 | 0.03 | -121446 | -82985 | 255828 | -196324 | 0.02 | 44.4 | 2.39 | -81638 | 216556 | -84328 |
| ES ext (12, 0, 60, 1) | all | 0.72 | 1.51 | -83092 | -65151 | 334294 | -196324 | 2.84 | 45.8 | 1.94 | -83362 | 247442 | -90637 |
| GC ext (24, 0, 120, 1) | clean | 0.80 | 1.35 | -125882 | -95799 | 258703 | -210444 | 2.80 | 41.9 | 1.55 | -86671 | 245616 | -98975 |
| GC ext (24, 0, 120, 1) | H1 | -2.19 | -2.31 | -339675 | -285186 | 1146070 | -453847 | -0.86 | 57.1 | 1.64 | -99296 | 237361 | -117153 |
| GC ext (24, 0, 120, 1) | H2 | -0.08 | -0.12 | -282541 | -245332 | 886420 | -330184 | -0.07 | 55.6 | 2.52 | -93212 | 233359 | -93638 |
| GC ext (24, 0, 120, 1) | all | -0.14 | -0.19 | -244985 | -188842 | 1459815 | -453847 | -0.22 | 47.6 | 1.78 | -92244 | 271081 | -117153 |
| HG ext (24, 0, 60, -1) (diag) | clean | 0.40 | 1.16 | -108327 | -90206 | 785039 | -205802 | 0.75 | 52.4 | 1.54 | -80832 | 272973 | -84256 |
| HG ext (24, 0, 60, -1) (diag) | H1 | -1.89 | -2.00 | -241351 | -219096 | 784936 | -297576 | -0.78 | 46.4 | 2.28 | -76755 | 162745 | -83339 |
| HG ext (24, 0, 60, -1) (diag) | H2 | -0.57 | -0.81 | -123836 | -107130 | 764232 | -140616 | -0.23 | 44.4 | 2.35 | -90921 | 246496 | -98827 |
| HG ext (24, 0, 60, -1) (diag) | all | -0.09 | -0.19 | -162911 | -122260 | 933284 | -297576 | -0.22 | 49.4 | 1.84 | -83409 | 272973 | -98827 |
| HO ext (6, 0, 60, 1) | clean | 0.55 | 0.83 | -127989 | -107536 | 427346 | -152698 | 1.16 | 50.5 | 1.53 | -85847 | 306744 | -99552 |
| HO ext (6, 0, 60, 1) | H1 | -3.70 | -3.44 | -145885 | -129467 | 698493 | -158527 | -0.94 | 67.9 | 2.27 | -79808 | 177643 | -81535 |
| HO ext (6, 0, 60, 1) | H2 | -0.27 | -0.35 | -287159 | -256999 | 846262 | -345315 | -0.22 | 41.7 | 2.04 | -118339 | 224742 | -122454 |
| HO ext (6, 0, 60, 1) | all | -0.18 | -0.24 | -212019 | -171949 | 1610354 | -345315 | -0.22 | 51.2 | 1.76 | -92636 | 306744 | -122454 |
| NQ ext (6, 0, 60, 1) | clean | 1.11 | 2.75 | -83393 | -67786 | 355949 | -94145 | 2.83 | 47.6 | 1.59 | -86059 | 255377 | -98697 |
| NQ ext (6, 0, 60, 1) | H1 | 0.17 | 0.23 | -133144 | -99826 | 215736 | -200172 | 0.17 | 42.9 | 2.82 | -75131 | 148655 | -76470 |
| NQ ext (6, 0, 60, 1) | H2 | 0.44 | 0.80 | -134753 | -97350 | 433771 | -170921 | 0.38 | 55.6 | 2.50 | -88141 | 229154 | -90495 |
| NQ ext (6, 0, 60, 1) | all | 0.81 | 1.60 | -107782 | -84274 | 433771 | -200172 | 2.79 | 48.2 | 1.98 | -85901 | 255377 | -98697 |
| RTY ext (12, 0, 60, 1) | clean | 0.64 | 1.35 | -85216 | -64993 | 405390 | -219859 | 1.42 | 51.4 | 1.55 | -84308 | 273692 | -92919 |
| RTY ext (12, 0, 60, 1) | H1 | 0.26 | 0.37 | -103413 | -94363 | 165768 | -108295 | 0.30 | 46.4 | 2.93 | -79731 | 143457 | -81756 |
| RTY ext (12, 0, 60, 1) | H2 | -1.50 | -1.81 | -83206 | -70806 | 344047 | -103262 | -0.77 | 61.1 | 2.32 | -89979 | 214138 | -94231 |
| RTY ext (12, 0, 60, 1) | all | 0.28 | 0.52 | -96933 | -74718 | 464974 | -219859 | 0.78 | 53.0 | 1.92 | -85392 | 273692 | -94231 |
| SI ext (24, 0, 120, 1) (diag) | clean | 0.32 | 0.64 | -97559 | -82658 | 361709 | -119007 | 0.83 | 52.4 | 1.45 | -88753 | 269840 | -100954 |
| SI ext (24, 0, 120, 1) (diag) | H1 | 1.06 | 5.03 | -655112 | -558681 | 2002091 | -910942 | 2.10 | 50.0 | 1.84 | -114313 | 388927 | -128296 |
| SI ext (24, 0, 120, 1) (diag) | H2 | 0.60 | 0.99 | -875279 | -739301 | 1320895 | -985712 | 1.01 | 38.9 | 1.96 | -190581 | 328899 | -279667 |
| SI ext (24, 0, 120, 1) (diag) | all | 0.54 | 1.62 | -575573 | -390596 | 2149479 | -985712 | 2.72 | 49.4 | 1.53 | -118260 | 388927 | -279667 |
| ZN ext (24, 0, 180, 1) (diag) | clean | -1.69 | -1.93 | -170847 | -137601 | 1803523 | -245994 | -0.85 | 55.2 | 1.13 | -94268 | 298858 | -126510 |
| ZN ext (24, 0, 180, 1) (diag) | H1 | -3.84 | -3.79 | -104594 | -100627 | 710924 | -106220 | -1.00 | 71.4 | 2.19 | -84426 | 168049 | -87355 |
| ZN ext (24, 0, 180, 1) (diag) | H2 | -1.08 | -1.48 | -105591 | -77725 | 398555 | -109471 | -0.62 | 55.6 | 2.39 | -86010 | 223591 | -90494 |
| ZN ext (24, 0, 180, 1) (diag) | all | -1.87 | -2.15 | -149945 | -124403 | 2792201 | -245994 | -0.89 | 58.3 | 1.57 | -91908 | 298858 | -126510 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES ext (12, 0, 60, 1) | -19.6 | 10.4 | 21.1 | 37.3 | 9.7 / 19.4 | 16.1 / 22.7 | NO |
| NQ ext (6, 0, 60, 1) | -16.8 | -2.0 | 16.6 | 33.3 | -2.8 / 15.1 | 33.5 / 34.8 | NO |
| RTY ext (12, 0, 60, 1) | -26.0 | 5.8 | 17.7 | 33.4 | 5.0 / 18.4 | 23.4 / 25.9 | NO |
| GC ext (24, 0, 120, 1) | -33.5 | -87.4 | -6.5 | -15.7 | -3.3 / 10.9 | -97.5 / -38.0 | NO |
| CL ext (24, 0, 120, 1) | -37.5 | -60.3 | 3.2 | 7.5 | 3.4 / 13.4 | 12.8 / 22.8 | NO |
| ZN ext (24, 0, 180, 1) (diag) | -57.1 | -55.0 | 4.0 | 8.2 | -56.2 / -1.9 | 11.2 / 16.8 | NO |
| HO ext (6, 0, 60, 1) | -33.8 | -45.4 | -4.4 | 0.1 | -2.4 / 10.2 | 22.4 / 23.2 | NO |
| 6E ext (12, 0, 180, -1) (diag) | -39.4 | -22.0 | 5.8 | 20.7 | 2.0 / 7.5 | -28.7 / 2.4 | NO |
| SI ext (24, 0, 120, 1) (diag) | 33.8 | -328.3 | -102.2 | -110.9 | -9.6 / 9.8 | -145.4 / -108.1 | NO |
| HG ext (24, 0, 60, -1) (diag) | -32.2 | -4.6 | 18.9 | 30.1 | 21.9 / 25.0 | 18.9 / 18.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 ext (12, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 2797 | 21.9 | -7.5 | 6.9 | 29.4 | 0.89 / -0.30 / 0.28 | 96.9 / 67.6 |
| ES 2 ext (6, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 4566 | 9.0 | -20.4 | -6.1 | 29.4 | 0.48 / -1.08 / -0.32 | 69.8 / 40.5 |
| ES 3 ext (12, 0, 180, -1) | negative pre-2023 | 1707 | -1.1 | -30.5 | -16.2 | 29.4 | -0.03 / -0.52 / -0.28 | 41.7 / 12.4 |
| ES 4 (diag) ext (12, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 2410 | 16.0 | -13.4 | 1.0 | 29.4 | 0.41 / -0.34 / 0.03 | 84.8 / 55.5 |
| ES 5 (diag) ext (24, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 1239 | 24.1 | -5.3 | 8.9 | 29.4 | 0.53 / -0.11 / 0.20 | 86.9 / 57.5 |
| ES 6 (diag) ext (24, 0, 180, 1) | negative pre-2023 | 705 | -8.7 | -38.1 | -23.9 | 29.4 | -0.08 / -0.39 / -0.24 | 156.4 / 127.0 |
| NQ 1 ext (6, 0, 60, 1) | positive pre-2023 | 4344 | 15.0 | 0.6 | 9.2 | 14.4 | 0.44 / 0.02 / 0.27 | 114.1 / 99.7 |
| NQ 2 ext (6, 0, 120, 1) | negative pre-2023 | 3447 | -7.2 | -21.5 | -12.9 | 14.4 | -0.13 / -0.39 / -0.23 | 147.7 / 133.3 |
| NQ 3 ext (6, 0, 180, 1) | negative pre-2023 | 2431 | -18.7 | -33.1 | -24.5 | 14.4 | -0.26 / -0.46 / -0.34 | 189.9 / 175.5 |
| NQ 4 ext (12, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 2245 | 9.5 | -4.8 | 3.9 | 14.4 | 0.12 / -0.06 / 0.05 | 137.3 / 123.0 |
| NQ 5 ext (24, 0, 120, 1) | positive pre-2023 | 1046 | 29.3 | 14.9 | 23.7 | 14.4 | 0.27 / 0.14 / 0.22 | 174.8 / 160.4 |
| NQ 6 ext (12, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 2597 | 13.6 | -0.8 | 8.0 | 14.4 | 0.32 / -0.02 / 0.19 | 76.8 / 62.5 |
| NQ 7 (diag) ext (24, 0, 180, 1) | positive pre-2023 | 652 | 59.9 | 45.6 | 54.2 | 14.4 | 0.38 / 0.29 / 0.35 | 377.8 / 363.4 |
| NQ 8 (diag) ext (12, 0, 180, 1) | positive pre-2023 | 1631 | 17.2 | 2.8 | 11.5 | 14.4 | 0.20 / 0.03 / 0.13 | 72.0 / 57.7 |
| NQ 9 (diag) ext (24, 0, 60, 1) | positive pre-2023 | 1094 | 35.3 | 21.0 | 29.6 | 14.4 | 0.47 / 0.28 / 0.40 | 30.2 / 15.9 |
| RTY 1 ext (24, 0, 180, 1) | negative pre-2023 | 352 | -17.2 | -31.5 | -29.3 | 14.4 | -0.20 / -0.37 / -0.34 | 108.7 / 94.3 |
| RTY 2 ext (12, 0, 60, 1) | negative pre-2023 | 1347 | -10.7 | -25.0 | -22.7 | 14.4 | -0.39 / -0.92 / -0.84 | 42.1 / 27.7 |
| RTY 3 ext (24, 0, 60, 1) | negative pre-2023 | 562 | -19.9 | -34.3 | -32.0 | 14.4 | -0.45 / -0.76 / -0.71 | 46.2 / 31.9 |
| RTY 4 (diag) ext (6, 0, 60, 1) | negative pre-2023 | 2326 | -11.6 | -25.9 | -23.6 | 14.4 | -0.55 / -1.23 / -1.13 | 20.2 / 5.8 |
| RTY 5 (diag) ext (24, 0, 120, 1) | negative pre-2023 | 541 | -18.0 | -32.4 | -30.1 | 14.4 | -0.26 / -0.47 / -0.43 | 14.7 / 0.3 |
| RTY 6 (diag) ext (6, 0, 180, -1) | positive pre-2023 | 1334 | 36.1 | 21.7 | 24.0 | 14.4 | 0.81 / 0.49 / 0.54 | 7.3 / -7.0 |
| GC 1 ext (24, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 1198 | 4.0 | -20.3 | -10.4 | 24.4 | 0.09 / -0.45 / -0.23 | 104.1 / 79.8 |
| GC 2 (diag) ext (12, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 2654 | 16.9 | -7.5 | 2.3 | 24.4 | 0.52 / -0.23 / 0.07 | 47.9 / 23.5 |
| GC 3 (diag) ext (12, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 3082 | 16.2 | -8.1 | 1.7 | 24.4 | 0.68 / -0.34 / 0.07 | 38.3 / 14.0 |
| GC 4 (diag) ext (6, 0, 60, -1) | negative pre-2023 | 4836 | -12.9 | -37.3 | -27.4 | 24.4 | -0.63 / -1.82 / -1.34 | 31.1 / 6.8 |
| CL 1 ext (12, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 2802 | 7.2 | -17.2 | -14.7 | 24.4 | 0.21 / -0.49 / -0.42 | 51.8 / 27.4 |
| CL 2 ext (24, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 1313 | 16.5 | -7.8 | -5.4 | 24.4 | 0.48 / -0.23 / -0.16 | 53.2 / 28.9 |
| CL 3 ext (12, 0, 60, 1) | gross-positive, cost-negative pre-2023 | 3231 | 16.3 | -8.1 | -5.6 | 24.4 | 0.67 / -0.34 / -0.23 | 34.6 / 10.3 |
| CL 4 ext (24, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 1267 | 19.5 | -4.9 | -2.5 | 24.4 | 0.40 / -0.10 / -0.05 | 41.9 / 17.5 |
| CL 5 (diag) ext (24, 0, 180, 1) | gross-positive, cost-negative pre-2023 | 777 | 10.2 | -14.2 | -12.1 | 24.4 | 0.13 / -0.18 / -0.16 | 43.3 / 18.9 |
| CL 6 (diag) ext (6, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 4037 | 14.5 | -9.9 | -7.3 | 24.4 | 0.49 / -0.33 / -0.24 | 20.4 / -3.9 |
| CL 7 (diag) ext (12, 0, 180, 1) | gross-positive, cost-negative pre-2023 | 1977 | 13.8 | -10.5 | -8.1 | 24.4 | 0.28 / -0.21 / -0.16 | 10.1 / -14.3 |
| ZN 1 (diag) ext (24, 0, 180, 1) | gross-positive, cost-negative pre-2023 | 1008 | 6.8 | -28.9 | -34.1 | 35.6 | 0.40 / -1.64 / -1.93 | 4.3 / -31.3 |
| ZN 2 (diag) ext (12, 0, 180, 1) | gross-positive, cost-negative pre-2023 | 2241 | 5.8 | -29.8 | -35.0 | 35.6 | 0.46 / -2.38 / -2.78 | 10.5 / -25.2 |
| ZN 3 (diag) ext (24, 0, 180, -1) | negative pre-2023 | 1008 | -6.8 | -42.4 | -47.6 | 35.6 | -0.40 / -2.39 / -2.67 | -4.3 / -40.0 |
| HO 1 ext (6, 0, 60, 1) | positive pre-2023 | 6040 | 16.6 | 3.9 | 5.4 | 12.8 | 0.71 / 0.16 / 0.23 | 26.6 / 13.9 |
| HO 2 ext (6, 0, 180, 1) | negative pre-2023 | 3388 | -19.6 | -32.3 | -30.8 | 12.8 | -0.33 / -0.55 / -0.52 | 35.7 / 22.9 |
| HO 3 (diag) ext (24, 0, 120, 1) | positive pre-2023 | 1497 | 42.6 | 29.8 | 31.2 | 12.8 | 0.70 / 0.49 / 0.51 | 37.2 / 24.4 |
| HO 4 (diag) ext (24, 0, 60, 1) | positive pre-2023 | 1551 | 38.6 | 25.8 | 27.2 | 12.8 | 0.82 / 0.55 / 0.58 | 24.8 / 12.1 |
| HO 5 (diag) ext (12, 0, 180, -1) | negative pre-2023 | 2258 | -6.2 | -19.0 | -17.5 | 12.8 | -0.08 / -0.26 / -0.24 | 16.8 / 4.1 |
| 6E 1 (diag) ext (24, 0, 120, -1) | negative pre-2023 | 1245 | -0.3 | -17.2 | -18.4 | 16.9 | -0.01 / -0.70 / -0.75 | 8.3 / -8.5 |
| 6E 2 (diag) ext (24, 0, 180, -1) | negative pre-2023 | 911 | -5.8 | -22.7 | -23.9 | 16.9 | -0.19 / -0.76 / -0.80 | 10.1 / -6.7 |
| 6E 3 (diag) ext (12, 0, 180, -1) | negative pre-2023 | 2105 | -0.2 | -17.0 | -18.2 | 16.9 | -0.01 / -0.85 / -0.91 | 6.5 / -10.4 |
| SI 1 (diag) ext (12, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 2556 | 10.0 | -44.4 | -25.4 | 54.4 | 0.24 / -1.06 / -0.61 | 85.1 / 30.7 |
| SI 2 (diag) ext (12, 0, 180, 1) | gross-positive, cost-negative pre-2023 | 2031 | 12.2 | -42.2 | -23.1 | 54.4 | 0.24 / -0.82 / -0.45 | 75.3 / 20.9 |
| SI 3 (diag) ext (24, 0, 120, 1) | gross-positive, cost-negative pre-2023 | 1128 | 4.5 | -49.8 | -30.7 | 54.4 | 0.07 / -0.79 / -0.49 | 87.2 / 32.8 |
| HG 1 (diag) ext (24, 0, 60, -1) | gross-positive, cost-negative pre-2023 | 1184 | 2.0 | -27.3 | -19.6 | 29.4 | 0.08 / -1.06 / -0.76 | 60.6 / 31.3 |
| HG 2 (diag) ext (24, 0, 120, -1) | gross-positive, cost-negative pre-2023 | 1147 | 0.8 | -28.6 | -20.8 | 29.4 | 0.02 / -0.86 / -0.63 | 66.3 / 36.9 |
| HG 3 (diag) ext (12, 0, 180, 1) | negative pre-2023 | 2096 | -3.2 | -32.5 | -24.6 | 29.4 | -0.09 / -1.01 / -0.76 | 80.6 / 51.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00); CL: 4 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.01, p(top) = 0.32); ES: 3 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.17, p(top) = 0.26); GC: 1 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.85, p(top) = 0.31); HG: 0 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 1.00); HO: 2 cells pass the clean rule against a replicate mean of 2.6 (p(count) = 0.76, p(top) = 0.71); NQ: 6 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.07, p(top) = 0.30); RTY: 3 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.36, p(top) = 0.56); SI: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 19 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.08 (NQ ext (6, 0, 60, 1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 9, 'negative pre-2023': 7, 'positive pre-2023': 3}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q38.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q38/ (`Q38_CO_all_selected_scored.csv`).

DONE Q38
