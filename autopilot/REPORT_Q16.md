# REPORT Q16 - Q16: time-of-day drift buckets (long or short at each 30-minute start 08:00-14:30 ET, hold 30/60/120 min)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 28 selected cells (+17 diagnostic) scored on 9 instruments; best non-diagnostic all-in additive uplift at 20% share +0.23; best pair-window standalone Sharpe +0.90.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter at a fixed ET clock time in a fixed direction, time exit; direction is not fitted on history, both signs are cells and selection is clean-only.
- Instruments: RTY, YM, GC, CL, ZN, BTC, ETH, SI, HG. Grid: 84 cells = 14 bucket starts x 2 directions x 3 holds
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      84 |         78 |         9 |               1.13  |                2 |          9 |            1 |
| CL    |      84 |         78 |         6 |               2.024 |                2 |          2 |            0 |
| ETH   |      84 |         78 |        11 |               1.105 |                2 |          5 |            0 |
| GC    |      84 |         78 |         2 |               0.985 |                2 |          2 |            1 |
| HG    |      84 |         78 |         2 |               0.776 |                2 |          2 |            3 |
| RTY   |      84 |         78 |         1 |               0.543 |                2 |          1 |            3 |
| SI    |      84 |         78 |         1 |               0.48  |                2 |          1 |            3 |
| YM    |      84 |         78 |         6 |               0.54  |                2 |          6 |            3 |
| ZN    |      84 |         78 |         0 |              -2.263 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| RTY   |     200 |                    1 |            8.08  |              15 |      1     |                       0.354 |            0.685 |           0.974 |    0.99  |       0.354 |                1.815 |
| YM    |     200 |                    6 |            9.005 |              19 |      0.895 |                       0.375 |            0.689 |           0.922 |    0.995 |       0.54  |                1.802 |
| GC    |     200 |                    2 |            5.83  |              12 |      0.99  |                       0.883 |            0.63  |           0.966 |    0.08  |       0.985 |                1.72  |
| CL    |     200 |                    6 |            3.11  |              10 |      0.075 |                       1.13  |            0.586 |           0.959 |    0.015 |       2.024 |                1.464 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                    9 |           11.985 |              21 |      0.87  |                       0.504 |            0.771 |           1.022 |    0.965 |       1.13  |                1.987 |
| ETH   |     200 |                   11 |            7.555 |              18 |      0.135 |                       0.599 |            0.663 |           0.913 |    0.645 |       1.105 |                1.815 |
| SI    |     200 |                    1 |            1.745 |               6 |      0.855 |                       0.155 |            0.526 |           1.086 |    0.81  |       0.155 |                1.284 |
| HG    |     200 |                    2 |            1.705 |               6 |      0.46  |                       0.209 |            0.537 |           1.026 |    0.74  |       0.264 |                1.261 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY 1 | TOD bucket 14:00 ET dir=short hold 120m | 497 | 2 | 0.35 | -0.04 | 0.07 | -0.62 / 1.41 | 0.05 / -0.47 / -0.00 | -0.08 | -0.81 | 0.70 | -0.19 | 0.00 | 797 | NO |
| RTY 2 (diag) | TOD bucket 09:00 ET dir=short hold 120m | 515 | 1 | 0.54 | 0.02 | 0.25 | -0.19 / 1.24 | 0.07 / -0.58 / 0.09 | -0.06 | -0.32 | 0.78 | -0.23 | 0.00 | 825 | diag |
| RTY 3 (diag) | TOD bucket 09:00 ET dir=short hold 60m | 515 | 1 | 0.47 | -0.45 | -0.02 | -0.69 / 0.84 | 0.10 / -0.94 / 0.01 | -0.12 | -0.18 | 0.80 | -0.29 | 0.00 | 825 | diag |
| RTY 4 (diag) | TOD bucket 08:30 ET dir=short hold 120m | 516 | 1 | 0.38 | -0.28 | 0.19 | -0.12 / 1.15 | 0.04 / -0.49 / 0.09 | -0.06 | -0.08 | 0.80 | -0.20 | 0.00 | 824 | diag |
| YM 1 | TOD bucket 13:00 ET dir=long hold 120m | 497 | 2 | 0.54 | -0.52 | 0.26 | -0.09 / 1.08 | 0.07 / 0.25 / -0.17 | 0.00 | 0.50 | 0.85 | -0.11 | 0.00 | 797 | NO |
| YM 2 | TOD bucket 09:00 ET dir=long hold 120m | 515 | 2 | 0.41 | -0.40 | 0.36 | 0.39 / 1.44 | 0.02 / 1.07 / -0.31 | 0.01 | 0.08 | 0.89 | -0.18 | 0.00 | 825 | NO |
| YM 3 | TOD bucket 12:00 ET dir=long hold 120m | 497 | 2 | 0.39 | -0.65 | 0.17 | -0.19 / 0.96 | 0.03 / -0.16 / -0.00 | -0.04 | -0.33 | 0.74 | -0.14 | 0.00 | 797 | NO |
| YM 4 | TOD bucket 08:30 ET dir=long hold 120m | 513 | 2 | 0.35 | -0.27 | 0.32 | 0.32 / 1.44 | -0.00 / 0.93 / -0.33 | -0.01 | -0.10 | 0.86 | -0.20 | 1.00 | 822 | NO |
| YM 5 | TOD bucket 13:00 ET dir=long hold 60m | 497 | 2 | 0.33 | -1.12 | 0.15 | -0.20 / 1.21 | 0.03 / -0.10 / 0.03 | -0.02 | 0.13 | 0.83 | -0.10 | 0.00 | 797 | NO |
| YM 6 | TOD bucket 08:30 ET dir=long hold 60m | 513 | 2 | 0.23 | -0.82 | 0.25 | 0.33 / 0.96 | -0.01 / -0.02 / 0.06 | -0.07 | -0.25 | 0.90 | -0.20 | 0.00 | 822 | NO |
| YM 7 (diag) | TOD bucket 09:00 ET dir=long hold 60m | 515 | 1 | 0.38 | -0.22 | 0.30 | 0.26 / 1.30 | 0.00 / 1.01 / -0.41 | -0.03 | 0.23 | 0.88 | -0.20 | 0.00 | 825 | diag |
| YM 8 (diag) | TOD bucket 11:30 ET dir=long hold 120m | 497 | 1 | 0.33 | -0.45 | 0.08 | -0.28 / 1.14 | 0.03 / -0.28 / -0.03 | -0.07 | -0.40 | 0.73 | -0.19 | 0.00 | 797 | diag |
| YM 9 (diag) | TOD bucket 12:30 ET dir=long hold 120m | 497 | 1 | 0.19 | -0.54 | 0.10 | 0.01 / 1.26 | -0.00 / -0.02 / -0.01 | -0.04 | 0.22 | 0.77 | -0.13 | 0.00 | 797 | diag |
| GC 1 | TOD bucket 13:30 ET dir=long hold 120m | 497 | 2 | 0.98 | -0.97 | 0.29 | 0.04 / 1.31 | 0.16 / 0.71 / -0.94 | -0.13 | 0.54 | 0.79 | -0.44 | 0.00 | 794 | NO |
| GC 2 | TOD bucket 13:30 ET dir=long hold 60m | 498 | 2 | 0.78 | -1.17 | 0.64 | 0.64 / 1.20 | 0.15 / 1.18 / -0.52 | -0.03 | 0.43 | 0.95 | -0.23 | 0.50 | 796 | NO |
| GC 3 (diag) | TOD bucket 14:00 ET dir=long hold 120m | 491 | 1 | 0.48 | -1.15 | -0.19 | -0.60 / 1.33 | 0.06 / 0.62 / -1.21 | -0.28 | 0.55 | 0.60 | -0.58 | 0.00 | 787 | diag |
| CL 1 | TOD bucket 14:30 ET dir=long hold 60m | 500 | 2 | 2.02 | -2.36 | 0.66 | -0.35 / 0.98 | 0.38 / 0.02 / 0.02 | -0.07 | -0.12 | 1.00 | -0.07 | 0.50 | 800 | NO |
| CL 2 | TOD bucket 14:30 ET dir=long hold 30m | 500 | 2 | 1.64 | -3.23 | 0.55 | -0.31 / 0.88 | 0.35 / -0.67 / 0.48 | -0.19 | -0.08 | 1.00 | -0.05 | 0.50 | 800 | NO |
| ZN 1 (diag) | TOD bucket 08:30 ET dir=short hold 120m | 517 | 0 | -2.26 | -2.42 | -2.42 | -2.78 / -2.47 | -0.46 / -0.57 / -0.28 | -0.90 | 0.01 | 0.93 | -0.63 | 0.00 | 826 | diag |
| ZN 2 (diag) | TOD bucket 08:30 ET dir=short hold 30m | 517 | 0 | -2.52 | -3.31 | -3.20 | -5.16 / -5.93 | -0.51 / -0.75 / -0.57 | -1.12 | 0.40 | 1.00 | -0.73 | 0.00 | 826 | diag |
| ZN 3 (diag) | TOD bucket 09:00 ET dir=long hold 120m | 515 | 0 | -2.68 | -2.51 | -3.41 | -4.88 / -2.41 | -0.55 / -0.81 / -0.94 | -1.21 | 0.51 | 0.47 | -0.86 | 0.00 | 826 | diag |
| BTC 1 | TOD bucket 13:00 ET dir=long hold 60m | 413 | 2 | 1.13 | -1.82 | 0.46 | -0.63 / 0.97 | 0.18 / -0.63 / 0.08 | -0.01 | 0.31 | 0.95 | -0.12 | 0.00 | 645 | NO |
| BTC 2 | TOD bucket 14:00 ET dir=short hold 120m | 425 | 2 | 0.65 | -0.84 | 0.63 | 0.48 / 1.40 | 0.05 / -0.09 / 0.08 | -0.01 | -0.60 | 0.86 | -0.12 | 0.00 | 663 | NO |
| BTC 3 | TOD bucket 12:00 ET dir=long hold 120m | 427 | 2 | 0.54 | -1.63 | -0.05 | -0.93 / 0.94 | 0.07 / -0.79 / 0.07 | -0.09 | -0.18 | 0.61 | -0.24 | 0.00 | 676 | NO |
| BTC 4 | TOD bucket 09:30 ET dir=short hold 30m | 439 | 2 | 0.50 | -0.73 | 0.28 | -0.15 / 1.39 | 0.11 / 0.11 / -0.12 | 0.01 | -0.38 | 0.94 | -0.11 | 0.50 | 681 | NO |
| BTC 5 | TOD bucket 13:00 ET dir=long hold 120m | 412 | 2 | 0.43 | -1.55 | -0.13 | -1.16 / 1.52 | 0.07 / -0.29 / -0.12 | -0.06 | 0.52 | 0.55 | -0.18 | 0.00 | 644 | NO |
| BTC 6 | TOD bucket 09:30 ET dir=short hold 60m | 439 | 2 | 0.42 | -0.85 | 0.35 | 0.15 / 1.60 | 0.08 / 0.18 / -0.15 | 0.01 | -0.44 | 0.83 | -0.12 | 0.00 | 681 | NO |
| BTC 7 | TOD bucket 09:00 ET dir=long hold 30m | 370 | 2 | 0.37 | -0.38 | -0.33 | -1.39 / 1.49 | -0.00 / 0.25 / -0.58 | -0.21 | -0.23 | 0.49 | -0.30 | 0.00 | 575 | NO |
| BTC 8 | TOD bucket 08:30 ET dir=long hold 60m | 390 | 2 | 0.36 | -1.39 | -0.34 | -1.33 / 1.44 | 0.01 / -0.30 / -0.48 | -0.20 | 0.02 | 0.40 | -0.33 | 0.00 | 596 | NO |
| BTC 9 | TOD bucket 14:30 ET dir=long hold 60m | 396 | 2 | 0.15 | -0.05 | -0.40 | -1.55 / 1.38 | 0.05 / -0.04 / -0.24 | -0.09 | 0.28 | 0.39 | -0.20 | 0.00 | 619 | NO |
| BTC 10 (diag) | TOD bucket 13:00 ET dir=long hold 30m | 414 | 1 | 0.60 | -2.45 | 0.30 | -0.18 / 1.04 | 0.07 / -0.41 / 0.07 | -0.06 | 0.26 | 0.89 | -0.18 | 1.00 | 646 | diag |
| ETH 1 | TOD bucket 09:30 ET dir=short hold 120m | 363 | 2 | 1.11 | -1.43 | 0.89 | 0.51 / 0.97 | 0.22 / 0.14 / -0.11 | 0.09 | -0.22 | 0.98 | -0.04 | 1.00 | 621 | NO |
| ETH 2 | TOD bucket 09:30 ET dir=short hold 60m | 366 | 2 | 0.96 | -1.81 | 0.55 | -0.31 / 0.84 | 0.20 / -0.06 / -0.09 | 0.01 | -0.19 | 0.98 | -0.10 | 0.50 | 627 | NO |
| ETH 3 | TOD bucket 10:00 ET dir=short hold 120m | 421 | 2 | 0.88 | -0.51 | 0.90 | 0.86 / 0.96 | 0.15 / 0.00 / 0.03 | 0.06 | -0.12 | 0.98 | -0.07 | 1.00 | 688 | NO |
| ETH 4 | TOD bucket 09:30 ET dir=short hold 30m | 366 | 2 | 0.71 | -1.45 | 0.18 | -0.61 / 0.45 | 0.12 / -0.00 / -0.17 | -0.08 | -0.29 | 0.97 | -0.17 | 1.00 | 627 | NO |
| ETH 5 | TOD bucket 10:00 ET dir=short hold 60m | 422 | 2 | 0.60 | -0.60 | 0.55 | 0.38 / 0.97 | 0.09 / -0.24 / -0.06 | -0.05 | 0.10 | 0.98 | -0.16 | 0.50 | 689 | NO |
| SI 1 | TOD bucket 12:30 ET dir=long hold 120m | 491 | 2 | 0.16 | -1.61 | -0.35 | -0.59 / 1.53 | 0.01 / -2.88 / -0.19 | -1.03 | 0.47 | 0.47 | -1.73 | 0.00 | 786 | NO |
| SI 2 (diag) | TOD bucket 09:30 ET dir=short hold 60m | 513 | 1 | 0.48 | -1.32 | 0.47 | 0.62 / 0.93 | 0.04 / 0.48 / -0.91 | -0.17 | -0.31 | 0.99 | -0.52 | 0.00 | 819 | diag |
| SI 3 (diag) | TOD bucket 09:30 ET dir=short hold 120m | 513 | 1 | 0.30 | -0.93 | 0.06 | -0.01 / 1.39 | 0.02 / -1.05 / -0.49 | -0.37 | -0.40 | 0.66 | -0.76 | 0.00 | 819 | diag |
| SI 4 (diag) | TOD bucket 13:30 ET dir=long hold 120m | 490 | 1 | 0.27 | -1.76 | 0.33 | 0.50 / 1.21 | 0.00 / 1.46 / -1.13 | -0.24 | 0.63 | 0.85 | -0.49 | 0.00 | 784 | diag |
| HG 1 | TOD bucket 09:30 ET dir=short hold 120m | 517 | 2 | 0.26 | -1.19 | 0.04 | -0.45 / 0.76 | 0.02 / -0.02 / -0.36 | -0.17 | -0.01 | 0.84 | -0.29 | 0.00 | 821 | NO |
| HG 2 | TOD bucket 09:30 ET dir=short hold 60m | 517 | 2 | 0.15 | -1.37 | 0.11 | -0.16 / 0.46 | 0.02 / 0.55 / -0.74 | -0.21 | -0.16 | 0.93 | -0.30 | 0.00 | 821 | NO |
| HG 3 (diag) | TOD bucket 12:30 ET dir=long hold 120m | 501 | 1 | 0.78 | -1.72 | -0.36 | -1.87 / 0.86 | -0.02 / -0.32 / -0.25 | -0.20 | 0.48 | 0.58 | -0.39 | 0.00 | 798 | diag |
| HG 4 (diag) | TOD bucket 12:30 ET dir=long hold 30m | 515 | 1 | 0.72 | -1.57 | 0.07 | -2.48 / 0.29 | 0.17 / -0.13 / -0.27 | -0.07 | 0.46 | 0.96 | -0.11 | 0.00 | 818 | diag |
| HG 5 (diag) | TOD bucket 11:00 ET dir=long hold 120m | 516 | 1 | 0.57 | -0.50 | 0.12 | -0.86 / 0.89 | 0.14 / 0.13 / -0.32 | -0.05 | -0.01 | 0.92 | -0.13 | 0.00 | 822 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 28 |
| diagnostic cells read | 17 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 21 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 33 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC TOD bucket 09:30 ET dir=short hold 30m | clean | 0.51 | 0.82 | -119023 | -102454 | 794419 | -154536 | 0.58 | 44.8 | 1.57 | -79766 | 226810 | -83935 |
| BTC TOD bucket 09:30 ET dir=short hold 30m | H1 | 0.37 | 0.56 | -89378 | -85921 | 257580 | -95733 | 0.36 | 46.4 | 2.93 | -79125 | 141704 | -90718 |
| BTC TOD bucket 09:30 ET dir=short hold 30m | H2 | -0.74 | -1.05 | -81223 | -71249 | 549831 | -96529 | -0.30 | 58.3 | 2.18 | -85571 | 224305 | -87237 |
| BTC TOD bucket 09:30 ET dir=short hold 30m | all | 0.28 | 0.44 | -111386 | -95610 | 794419 | -154536 | 0.49 | 48.2 | 1.92 | -83097 | 226810 | -90718 |
| CL TOD bucket 14:30 ET dir=long hold 60m | clean | 2.02 | 4.09 | -91613 | -77340 | 432768 | -137016 | 4.23 | 39.0 | 1.84 | -82037 | 287322 | -88355 |
| CL TOD bucket 14:30 ET dir=long hold 60m | H1 | -1.08 | -1.28 | -211495 | -170289 | 485516 | -323338 | -0.74 | 57.1 | 2.85 | -75115 | 155264 | -93871 |
| CL TOD bucket 14:30 ET dir=long hold 60m | H2 | -0.05 | -0.07 | -346883 | -264146 | 1153985 | -461997 | -0.03 | 50.0 | 2.31 | -85788 | 199593 | -89553 |
| CL TOD bucket 14:30 ET dir=long hold 60m | all | 0.66 | 0.99 | -207579 | -150841 | 1344005 | -461997 | 1.07 | 44.0 | 2.08 | -84671 | 287322 | -93871 |
| ETH TOD bucket 09:30 ET dir=short hold 120m | clean | 1.18 | 2.04 | -113742 | -94067 | 419625 | -165515 | 2.57 | 44.8 | 1.68 | -86628 | 226525 | -93325 |
| ETH TOD bucket 09:30 ET dir=short hold 120m | H1 | 1.42 | 2.46 | -163371 | -132086 | 396785 | -250601 | 1.35 | 42.9 | 2.97 | -78367 | 201260 | -92191 |
| ETH TOD bucket 09:30 ET dir=short hold 120m | H2 | -0.75 | -0.95 | -144600 | -107210 | 458610 | -160795 | -0.43 | 58.3 | 2.19 | -83442 | 231194 | -89245 |
| ETH TOD bucket 09:30 ET dir=short hold 120m | all | 0.89 | 1.47 | -135806 | -106135 | 458610 | -250601 | 3.10 | 47.6 | 2.00 | -86538 | 231194 | -93325 |
| GC TOD bucket 13:30 ET dir=long hold 60m | clean | 0.83 | 1.64 | -89810 | -81146 | 495594 | -110049 | 1.53 | 60.0 | 1.61 | -86021 | 303089 | -93049 |
| GC TOD bucket 13:30 ET dir=long hold 60m | H1 | 1.92 | 4.17 | -216788 | -181542 | 732620 | -241076 | 1.47 | 42.9 | 4.00 | -69815 | 225684 | -99142 |
| GC TOD bucket 13:30 ET dir=long hold 60m | H2 | -0.09 | -0.14 | -380133 | -310694 | 1628915 | -440852 | -0.06 | 52.8 | 1.78 | -142155 | 341443 | -170695 |
| GC TOD bucket 13:30 ET dir=long hold 60m | all | 0.64 | 1.07 | -239350 | -181945 | 1628915 | -440852 | 1.07 | 56.0 | 1.96 | -104519 | 341443 | -170695 |
| HG TOD bucket 09:30 ET dir=short hold 60m | clean | 0.43 | 0.71 | -114080 | -96801 | 467994 | -161599 | 0.89 | 48.6 | 1.48 | -91430 | 277100 | -97135 |
| HG TOD bucket 09:30 ET dir=short hold 60m | H1 | 1.66 | 5.93 | -129947 | -112831 | 530321 | -149642 | 1.99 | 46.4 | 3.38 | -65194 | 141378 | -71780 |
| HG TOD bucket 09:30 ET dir=short hold 60m | H2 | -3.27 | -3.29 | -184108 | -168809 | 1374581 | -190438 | -0.90 | 72.2 | 1.56 | -85194 | 225041 | -88646 |
| HG TOD bucket 09:30 ET dir=short hold 60m | all | 0.11 | 0.20 | -153862 | -128263 | 1412630 | -190438 | 0.17 | 53.6 | 1.79 | -89032 | 277100 | -97135 |
| RTY TOD bucket 14:00 ET dir=short hold 120m | clean | 0.44 | 0.76 | -109933 | -84036 | 440428 | -243461 | 0.90 | 52.4 | 1.51 | -84329 | 309226 | -89831 |
| RTY TOD bucket 14:00 ET dir=short hold 120m | H1 | -1.35 | -1.71 | -117732 | -113751 | 390289 | -127261 | -0.78 | 64.3 | 2.36 | -84454 | 178545 | -87741 |
| RTY TOD bucket 14:00 ET dir=short hold 120m | H2 | 0.01 | 0.01 | -88965 | -76081 | 418042 | -92664 | 0.01 | 55.6 | 2.29 | -86174 | 218945 | -86977 |
| RTY TOD bucket 14:00 ET dir=short hold 120m | all | 0.07 | 0.11 | -114808 | -91422 | 909002 | -243461 | 0.11 | 54.8 | 1.82 | -85667 | 309226 | -89831 |
| SI TOD bucket 12:30 ET dir=long hold 120m | clean | 0.14 | 0.22 | -112301 | -97218 | 689420 | -143662 | 0.18 | 51.4 | 1.47 | -81195 | 323054 | -89079 |
| SI TOD bucket 12:30 ET dir=long hold 120m | H1 | -1.04 | -1.07 | -2260008 | -1566950 | 4181012 | -3967579 | -0.75 | 53.6 | -0.05 | -460489 | 917876 | -804736 |
| SI TOD bucket 12:30 ET dir=long hold 120m | H2 | 0.23 | 0.34 | -501384 | -412827 | 1476216 | -564893 | 0.19 | 44.4 | 2.11 | -145710 | 308723 | -170099 |
| SI TOD bucket 12:30 ET dir=long hold 120m | all | -0.35 | -0.37 | -754476 | -470353 | 4261118 | -3967579 | -0.64 | 50.6 | 0.98 | -181938 | 946139 | -804736 |
| YM TOD bucket 09:00 ET dir=long hold 120m | clean | 0.33 | 0.47 | -135182 | -109553 | 430043 | -187329 | 0.70 | 48.6 | 1.48 | -88746 | 308139 | -102145 |
| YM TOD bucket 09:00 ET dir=long hold 120m | H1 | 2.03 | 3.94 | -120232 | -114909 | 194472 | -134080 | 3.54 | 42.9 | 3.90 | -48926 | 108116 | -51318 |
| YM TOD bucket 09:00 ET dir=long hold 120m | H2 | -0.72 | -0.93 | -215651 | -198006 | 895709 | -217885 | -0.40 | 41.7 | 1.99 | -89224 | 213591 | -94033 |
| YM TOD bucket 09:00 ET dir=long hold 120m | all | 0.36 | 0.51 | -170334 | -139789 | 895709 | -217885 | 0.71 | 45.8 | 1.91 | -87991 | 308139 | -102145 |
| ZN TOD bucket 08:30 ET dir=short hold 120m (diag) | clean | -2.24 | -2.52 | -141776 | -124259 | 2098065 | -195101 | -0.97 | 61.0 | 1.00 | -92495 | 320950 | -107784 |
| ZN TOD bucket 08:30 ET dir=short hold 120m (diag) | H1 | -3.62 | -3.42 | -152785 | -138756 | 735754 | -153881 | -0.98 | 64.3 | 2.26 | -83065 | 152404 | -86687 |
| ZN TOD bucket 08:30 ET dir=short hold 120m (diag) | H2 | -2.08 | -2.37 | -98920 | -91559 | 704256 | -100883 | -0.70 | 58.3 | 2.02 | -89020 | 217233 | -96420 |
| ZN TOD bucket 08:30 ET dir=short hold 120m (diag) | all | -2.42 | -2.64 | -141013 | -121782 | 3500141 | -195101 | -0.93 | 61.3 | 1.41 | -91199 | 320950 | -107784 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| RTY TOD bucket 14:00 ET dir=short hold 120m | -28.9 | 11.7 | 16.1 | 14.4 | 11.0 / 17.8 | 10.5 / 16.8 | NO |
| YM TOD bucket 09:00 ET dir=long hold 120m | -22.9 | -10.8 | 8.3 | 8.7 | -11.6 / 7.9 | 62.3 / 68.1 | NO |
| GC TOD bucket 13:30 ET dir=long hold 60m | -10.5 | -130.3 | -26.1 | -26.1 | 5.3 / 14.7 | -11.3 / 26.3 | NO |
| CL TOD bucket 14:30 ET dir=long hold 60m | -14.0 | -59.1 | 7.1 | -1.5 | 13.4 / 22.6 | -1.2 / 28.8 | NO |
| ZN TOD bucket 08:30 ET dir=short hold 120m (diag) | -66.2 | -21.3 | 4.8 | -5.0 | -22.2 / 0.5 | 13.9 / 19.5 | NO |
| BTC TOD bucket 09:30 ET dir=short hold 30m | -25.7 | 11.0 | 20.3 | 36.8 | 22.2 / 24.9 | 6.2 / 27.1 | NO |
| ETH TOD bucket 09:30 ET dir=short hold 120m | -14.1 | 1.9 | 11.8 | 29.9 | 1.1 / 9.7 | 3.4 / 24.9 | NO |
| SI TOD bucket 12:30 ET dir=long hold 120m | -60.7 | -1351.8 | -196.8 | -372.6 | 12.6 / 19.4 | -1430.4 / -781.3 | NO |
| HG TOD bucket 09:30 ET dir=short hold 60m | -27.3 | 0.9 | 9.1 | 31.2 | 0.1 / 5.6 | 34.7 / 36.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| RTY 1 TOD bucket 14:00 ET dir=short hold 120m | gross-positive, cost-negative pre-2023 | 1493 | 12.8 | -1.5 | 0.7 | 14.4 | 0.43 / -0.04 / 0.03 | 31.2 / 16.8 |
| RTY 2 (diag) TOD bucket 09:00 ET dir=short hold 120m | positive pre-2023 | 1526 | 15.0 | 0.6 | 2.9 | 14.4 | 0.35 / 0.02 / 0.07 | 41.5 / 27.1 |
| RTY 3 (diag) TOD bucket 09:00 ET dir=short hold 60m | negative pre-2023 | 1526 | -0.0 | -14.4 | -12.2 | 14.4 | 0.01 / -0.45 / -0.38 | 31.8 / 17.4 |
| RTY 4 (diag) TOD bucket 08:30 ET dir=short hold 120m | gross-positive, cost-negative pre-2023 | 1524 | 1.0 | -13.4 | -11.1 | 14.4 | 0.03 / -0.28 / -0.24 | 35.1 / 20.7 |
| YM 1 TOD bucket 13:00 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2615 | 0.3 | -14.0 | -8.3 | 14.4 | 0.01 / -0.52 / -0.31 | 37.7 / 23.4 |
| YM 2 TOD bucket 09:00 ET dir=long hold 120m | negative pre-2023 | 2685 | -0.6 | -14.9 | -9.2 | 14.4 | -0.01 / -0.40 / -0.25 | 30.8 / 16.5 |
| YM 3 TOD bucket 12:00 ET dir=long hold 120m | negative pre-2023 | 2616 | -4.0 | -18.4 | -12.6 | 14.4 | -0.14 / -0.65 / -0.45 | 35.5 / 21.1 |
| YM 4 TOD bucket 08:30 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2688 | 4.0 | -10.3 | -4.6 | 14.4 | 0.10 / -0.27 / -0.12 | 31.2 / 16.8 |
| YM 5 TOD bucket 13:00 ET dir=long hold 60m | negative pre-2023 | 2615 | -8.3 | -22.6 | -16.9 | 14.4 | -0.41 / -1.12 / -0.84 | 29.8 / 15.4 |
| YM 6 TOD bucket 08:30 ET dir=long hold 60m | negative pre-2023 | 2689 | -2.6 | -17.0 | -11.2 | 14.4 | -0.12 / -0.82 / -0.54 | 19.4 / 5.0 |
| YM 7 (diag) TOD bucket 09:00 ET dir=long hold 60m | gross-positive, cost-negative pre-2023 | 2686 | 8.7 | -5.6 | 0.1 | 14.4 | 0.34 / -0.22 / 0.01 | 26.1 / 11.7 |
| YM 8 (diag) TOD bucket 11:30 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2616 | 0.7 | -13.6 | -7.9 | 14.4 | 0.03 / -0.45 / -0.26 | 29.9 / 15.5 |
| YM 9 (diag) TOD bucket 12:30 ET dir=long hold 120m | negative pre-2023 | 2616 | -0.8 | -15.1 | -9.4 | 14.4 | -0.03 / -0.54 / -0.34 | 23.3 / 8.9 |
| GC 1 TOD bucket 13:30 ET dir=long hold 120m | negative pre-2023 | 2598 | -0.3 | -24.6 | -14.8 | 24.4 | -0.00 / -0.97 / -0.58 | 64.9 / 40.5 |
| GC 2 TOD bucket 13:30 ET dir=long hold 60m | gross-positive, cost-negative pre-2023 | 2598 | 2.4 | -22.0 | -12.2 | 24.4 | 0.13 / -1.17 / -0.64 | 48.1 / 23.8 |
| GC 3 (diag) TOD bucket 14:00 ET dir=long hold 120m | negative pre-2023 | 2571 | -5.4 | -29.8 | -20.0 | 24.4 | -0.20 / -1.15 / -0.77 | 45.8 / 21.5 |
| CL 1 TOD bucket 14:30 ET dir=long hold 60m | negative pre-2023 | 2606 | -11.4 | -35.7 | -33.1 | 24.4 | -0.75 / -2.36 / -2.17 | 52.3 / 28.0 |
| CL 2 TOD bucket 14:30 ET dir=long hold 30m | negative pre-2023 | 2606 | -13.5 | -37.8 | -35.2 | 24.4 | -1.15 / -3.23 / -2.98 | 41.4 / 17.0 |
| ZN 1 (diag) TOD bucket 08:30 ET dir=short hold 120m | gross-positive, cost-negative pre-2023 | 2691 | 0.8 | -34.8 | -39.9 | 35.6 | 0.06 / -2.42 / -2.77 | 4.4 / -31.3 |
| ZN 2 (diag) TOD bucket 08:30 ET dir=short hold 30m | gross-positive, cost-negative pre-2023 | 2692 | 4.5 | -31.1 | -36.2 | 35.6 | 0.48 / -3.31 / -3.85 | 7.8 / -27.8 |
| ZN 3 (diag) TOD bucket 09:00 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2673 | 5.6 | -30.1 | -35.2 | 35.6 | 0.46 / -2.51 / -2.94 | 5.1 / -30.5 |
| BTC 1 TOD bucket 13:00 ET dir=long hold 60m | negative pre-2023 | 265 | -131.3 | -185.7 | -153.0 | 54.4 | -1.29 / -1.82 / -1.50 | 247.6 / 193.3 |
| BTC 2 TOD bucket 14:00 ET dir=short hold 120m | negative pre-2023 | 295 | -47.4 | -101.7 | -69.4 | 54.4 | -0.39 / -0.84 / -0.57 | 229.8 / 175.5 |
| BTC 3 TOD bucket 12:00 ET dir=long hold 120m | negative pre-2023 | 297 | -150.6 | -204.9 | -172.6 | 54.4 | -1.20 / -1.63 / -1.38 | 189.2 / 134.9 |
| BTC 4 TOD bucket 09:30 ET dir=short hold 30m | gross-positive, cost-negative pre-2023 | 337 | 5.8 | -48.6 | -16.0 | 54.4 | 0.06 / -0.73 / -0.26 | 158.7 / 104.3 |
| BTC 5 TOD bucket 13:00 ET dir=long hold 120m | negative pre-2023 | 265 | -153.8 | -208.1 | -175.5 | 54.4 | -1.15 / -1.55 / -1.31 | 131.6 / 77.2 |
| BTC 6 TOD bucket 09:30 ET dir=short hold 60m | negative pre-2023 | 337 | -19.4 | -73.8 | -41.3 | 54.4 | -0.24 / -0.85 / -0.49 | 164.4 / 110.0 |
| BTC 7 TOD bucket 09:00 ET dir=long hold 30m | gross-positive, cost-negative pre-2023 | 281 | 34.5 | -19.8 | 12.5 | 54.4 | 0.71 / -0.38 / 0.27 | 83.0 / 28.7 |
| BTC 8 TOD bucket 08:30 ET dir=long hold 60m | negative pre-2023 | 301 | -72.1 | -126.5 | -93.7 | 54.4 | -0.79 / -1.39 / -1.03 | 98.5 / 44.1 |
| BTC 9 TOD bucket 14:30 ET dir=long hold 60m | gross-positive, cost-negative pre-2023 | 281 | 49.5 | -4.9 | 27.5 | 54.4 | 0.47 / -0.05 / 0.26 | 75.4 / 21.1 |
| BTC 10 (diag) TOD bucket 13:00 ET dir=long hold 30m | negative pre-2023 | 265 | -100.0 | -154.4 | -121.7 | 54.4 | -1.59 / -2.45 / -1.93 | 132.5 / 78.1 |
| ETH 1 TOD bucket 09:30 ET dir=short hold 120m | negative pre-2023 | 285 | -101.8 | -156.1 | -139.3 | 54.4 | -0.94 / -1.43 / -1.27 | 256.1 / 201.8 |
| ETH 2 TOD bucket 09:30 ET dir=short hold 60m | negative pre-2023 | 288 | -94.7 | -149.1 | -132.3 | 54.4 | -1.16 / -1.81 / -1.61 | 188.7 / 134.4 |
| ETH 3 TOD bucket 10:00 ET dir=short hold 120m | negative pre-2023 | 312 | -6.2 | -60.6 | -44.6 | 54.4 | -0.06 / -0.51 / -0.38 | 189.3 / 135.0 |
| ETH 4 TOD bucket 09:30 ET dir=short hold 30m | negative pre-2023 | 288 | -35.9 | -90.2 | -73.4 | 54.4 | -0.59 / -1.45 / -1.18 | 123.8 / 69.4 |
| ETH 5 TOD bucket 10:00 ET dir=short hold 60m | gross-positive, cost-negative pre-2023 | 313 | 6.4 | -48.0 | -32.1 | 54.4 | 0.07 / -0.60 / -0.41 | 136.1 / 81.7 |
| SI 1 TOD bucket 12:30 ET dir=long hold 120m | negative pre-2023 | 2524 | -0.4 | -54.8 | -35.8 | 54.4 | -0.01 / -1.61 / -1.05 | 60.1 / 5.7 |
| SI 2 (diag) TOD bucket 09:30 ET dir=short hold 60m | gross-positive, cost-negative pre-2023 | 2641 | 0.4 | -54.0 | -34.9 | 54.4 | 0.02 / -1.32 / -0.85 | 85.1 / 30.7 |
| SI 3 (diag) TOD bucket 09:30 ET dir=short hold 120m | gross-positive, cost-negative pre-2023 | 2641 | 7.5 | -46.9 | -27.9 | 54.4 | 0.16 / -0.93 / -0.55 | 79.8 / 25.5 |
| SI 4 (diag) TOD bucket 13:30 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2549 | 0.4 | -54.0 | -35.0 | 54.4 | 0.02 / -1.76 / -1.14 | 60.2 / 5.8 |
| HG 1 TOD bucket 09:30 ET dir=short hold 120m | negative pre-2023 | 2678 | -2.3 | -31.6 | -23.7 | 29.4 | -0.07 / -1.19 / -0.89 | 52.0 / 22.6 |
| HG 2 TOD bucket 09:30 ET dir=short hold 60m | negative pre-2023 | 2678 | -0.5 | -29.8 | -21.9 | 29.4 | -0.01 / -1.37 / -1.01 | 43.7 / 14.4 |
| HG 3 (diag) TOD bucket 12:30 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2580 | 0.5 | -28.9 | -21.0 | 29.4 | 0.03 / -1.72 / -1.25 | 23.2 / -6.2 |
| HG 4 (diag) TOD bucket 12:30 ET dir=long hold 30m | gross-positive, cost-negative pre-2023 | 2606 | 13.2 | -16.2 | -8.3 | 29.4 | 1.27 / -1.57 / -0.81 | 63.1 / 33.7 |
| HG 5 (diag) TOD bucket 11:00 ET dir=long hold 120m | gross-positive, cost-negative pre-2023 | 2633 | 18.7 | -10.7 | -2.8 | 29.4 | 0.88 / -0.50 / -0.13 | 64.8 / 35.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 9 cells pass the clean rule against a replicate mean of 12.0 (p(count) = 0.87, p(top) = 0.96); CL: 6 cells pass the clean rule against a replicate mean of 3.1 (p(count) = 0.07, p(top) = 0.01); ETH: 11 cells pass the clean rule against a replicate mean of 7.6 (p(count) = 0.14, p(top) = 0.65); GC: 2 cells pass the clean rule against a replicate mean of 5.8 (p(count) = 0.99, p(top) = 0.08); HG: 2 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.46, p(top) = 0.74); RTY: 1 cells pass the clean rule against a replicate mean of 8.1 (p(count) = 1.00, p(top) = 0.99); SI: 1 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.85, p(top) = 0.81); YM: 6 cells pass the clean rule against a replicate mean of 9.0 (p(count) = 0.90, p(top) = 0.99); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 28 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.23 (CL TOD bucket 14:30 ET dir=long hold 60m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 20, 'gross-positive, cost-negative pre-2023': 8}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q16.py (ap_q_sig.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q16/ (`Q16_CO_all_selected_scored.csv`).

DONE Q16
