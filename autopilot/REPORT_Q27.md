# REPORT Q27 - Q27: round-number reaction: break or reject of a round level, with/against, time exit

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 22 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.14; best pair-window standalone Sharpe +0.96.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: round-number reaction: break or reject of a round level, with/against, time exit. Time exit, no stop.
- Instruments: ES, NQ, RTY, GC, CL, ZN, BTC, HO. Grid: 48 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      48 |         48 |         2 |               0.849 |                2 |          2 |            3 |
| CL    |      48 |         48 |         2 |               0.524 |                2 |          2 |            3 |
| ES    |      48 |         48 |         2 |               0.566 |                2 |          2 |            3 |
| GC    |      48 |         48 |         5 |               1.524 |                2 |          5 |            3 |
| HO    |      48 |         48 |         5 |               1.343 |                2 |          5 |            3 |
| NQ    |      48 |         48 |         4 |               1.338 |                2 |          4 |            3 |
| RTY   |      48 |         48 |         2 |               0.602 |                2 |          2 |            3 |
| ZN    |      48 |         48 |         0 |              -3.267 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            0.315 |               2 |      0.035 |                       0.189 |            0.493 |           1.127 |    0.225 |       0.248 |                1.127 |
| NQ    |     200 |                    4 |            5.435 |              11 |      0.82  |                       0.983 |            0.684 |           0.977 |    0.045 |       1.338 |                1.888 |
| RTY   |     200 |                    2 |            1.145 |               4 |      0.31  |                       0.269 |            0.577 |           1.193 |    0.62  |       0.334 |                1.288 |
| GC    |     200 |                    5 |            1.015 |               4 |      0     |                       0.903 |            0.625 |           1.287 |    0.14  |       1.524 |                1.429 |
| CL    |     200 |                    2 |            0.115 |               2 |      0.015 |                       0.388 |            0.489 |           0.928 |    0.05  |       0.524 |                0.928 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                    2 |            3.415 |               8 |      0.895 |                       0.529 |            0.622 |           1.027 |    0.62  |       0.849 |                1.56  |
| HO    |     200 |                    5 |            2.35  |               7 |      0.08  |                       0.732 |            0.611 |           1.041 |    0.255 |       1.343 |                1.385 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | round (5, 2, 'reject', -1, 180) | 1127 | 2 | 0.25 | -0.57 | -0.32 | -0.88 / 0.57 | 0.05 / -0.68 / -0.46 | -0.28 | -0.25 | 0.84 | -0.41 | 0.00 | 2024 | NO |
| ES 2 | round (5, 2, 'break', 1, 120) | 1409 | 2 | 0.13 | -0.63 | -0.68 | -1.64 / 0.21 | -0.07 / -0.07 / -0.64 | -0.37 | 0.06 | 0.87 | -0.44 | 0.00 | 2538 | NO |
| ES 3 (diag) | round (15, 2, 'reject', -1, 180) | 1011 | 1 | 0.57 | -0.48 | 0.17 | -0.23 / 0.93 | 0.11 / -0.18 / -0.43 | -0.16 | -0.26 | 0.96 | -0.28 | 0.00 | 1845 | diag |
| ES 4 (diag) | round (15, 1, 'break', 1, 180) | 1665 | 1 | 0.34 | -0.63 | 0.14 | -0.22 / 0.55 | -0.04 / -0.02 / -0.19 | -0.19 | -0.04 | 0.99 | -0.24 | 0.00 | 2897 | diag |
| ES 5 (diag) | round (5, 1, 'break', 1, 120) | 2432 | 1 | 0.28 | -1.31 | -0.24 | -1.37 / 0.10 | -0.03 / -0.36 / -0.02 | -0.24 | -0.09 | 0.99 | -0.24 | 0.00 | 4267 | diag |
| NQ 1 | round (5, 1, 'break', 1, 120) | 2408 | 2 | 1.34 | -0.30 | 0.43 | -0.31 / 1.03 | 0.12 / -0.07 / -0.27 | -0.06 | -0.06 | 0.88 | -0.25 | 0.00 | 4348 | NO |
| NQ 2 | round (5, 1, 'break', 1, 180) | 1837 | 2 | 0.98 | -0.51 | 0.78 | 0.54 / 1.34 | 0.14 / 0.42 / -0.30 | 0.05 | 0.18 | 0.97 | -0.14 | 0.00 | 3281 | NO |
| NQ 3 | round (15, 1, 'break', 1, 60) | 3014 | 2 | 0.88 | -0.41 | 0.72 | 0.51 / 0.73 | 0.08 / 0.22 / -0.18 | -0.01 | 0.58 | 0.99 | -0.11 | 0.00 | 5553 | NO |
| NQ 4 | round (15, 1, 'break', 1, 180) | 1655 | 2 | 0.73 | -0.08 | 0.60 | 0.40 / 1.26 | 0.11 / -0.03 / -0.13 | 0.02 | -0.05 | 0.92 | -0.16 | 0.50 | 2985 | NO |
| NQ 5 (diag) | round (5, 2, 'break', 1, 180) | 1153 | 1 | 0.91 | -0.48 | 0.54 | 0.19 / 1.35 | 0.15 / 0.56 / -0.70 | -0.02 | -0.40 | 0.94 | -0.24 | 0.00 | 2135 | diag |
| NQ 6 (diag) | round (5, 2, 'break', 1, 120) | 1460 | 1 | 0.81 | -0.16 | 0.19 | -0.45 / 0.89 | 0.08 / 0.00 / -0.64 | -0.13 | -0.42 | 0.81 | -0.35 | 0.00 | 2698 | diag |
| NQ 7 (diag) | round (15, 2, 'break', 1, 120) | 1299 | 1 | 0.71 | -0.13 | -0.10 | -1.16 / 1.03 | 0.04 / -0.04 / -0.74 | -0.19 | -0.32 | 0.52 | -0.35 | 0.00 | 2395 | diag |
| RTY 1 | round (5, 2, 'break', 1, 120) | 927 | 2 | 0.33 | -1.50 | -0.42 | -1.46 / 0.40 | 0.02 / -0.01 / -0.64 | -0.22 | -0.11 | 0.90 | -0.36 | 0.00 | 1662 | NO |
| RTY 2 | round (15, 2, 'reject', 1, 120) | 787 | 2 | 0.20 | -1.03 | 0.06 | -0.24 / 0.54 | -0.00 / -0.67 / 0.19 | -0.13 | 0.26 | 0.98 | -0.26 | 0.00 | 1428 | NO |
| RTY 3 (diag) | round (5, 2, 'reject', 1, 120) | 909 | 1 | 0.60 | -0.66 | 0.12 | -0.54 / 0.12 | 0.08 / -0.56 / -0.15 | -0.14 | -0.22 | 0.99 | -0.25 | 0.00 | 1622 | diag |
| RTY 4 (diag) | round (15, 2, 'reject', 1, 180) | 651 | 1 | 0.40 | -0.92 | -0.51 | -2.10 / 1.03 | 0.02 / -0.80 / -0.31 | -0.22 | 0.21 | 0.53 | -0.34 | 0.00 | 1169 | diag |
| RTY 5 (diag) | round (5, 2, 'reject', 1, 180) | 719 | 1 | 0.37 | -0.39 | -0.56 | -1.71 / 0.91 | 0.03 / -0.49 / -0.77 | -0.29 | -0.24 | 0.56 | -0.45 | 0.00 | 1288 | diag |
| GC 1 | round (5, 1, 'reject', 1, 180) | 1402 | 2 | 1.52 | -0.81 | 0.22 | -0.21 / 1.19 | 0.23 / -1.69 / 0.02 | -0.26 | -0.31 | 0.90 | -0.70 | 0.00 | 3020 | NO |
| GC 2 | round (15, 1, 'reject', 1, 180) | 1287 | 2 | 1.11 | -1.03 | 0.96 | 1.27 / 1.20 | 0.11 / 0.63 / -0.55 | -0.01 | 0.03 | 0.99 | -0.31 | 0.00 | 2761 | NO |
| GC 3 | round (5, 2, 'break', -1, 120) | 981 | 2 | 0.72 | -0.43 | -1.01 | -2.34 / 1.11 | 0.14 / -1.45 / -1.27 | -0.51 | 0.25 | 0.23 | -0.74 | 0.00 | 2331 | NO |
| GC 4 | round (15, 2, 'reject', 1, 180) | 748 | 2 | 0.64 | -0.72 | 0.45 | 0.55 / 1.12 | 0.06 / -0.43 / -0.66 | -0.22 | 0.17 | 0.96 | -0.68 | 0.00 | 1758 | NO |
| GC 5 | round (15, 2, 'break', -1, 60) | 1119 | 2 | 0.52 | -0.97 | -1.14 | -2.17 / 1.02 | 0.11 / -2.99 / -1.21 | -1.00 | -0.00 | 0.12 | -1.32 | 0.00 | 2758 | NO |
| GC 6 (diag) | round (15, 2, 'break', -1, 120) | 872 | 1 | 0.37 | -0.41 | -0.28 | -0.66 / 1.02 | 0.08 / -1.36 / -0.40 | -0.33 | 0.32 | 0.59 | -0.58 | 0.00 | 2090 | diag |
| GC 7 (diag) | round (5, 1, 'break', -1, 120) | 1733 | 1 | 0.12 | -0.89 | -0.63 | -1.15 / 1.02 | -0.02 / -1.97 / -0.57 | -0.58 | -0.31 | 0.55 | -0.87 | 0.00 | 3899 | diag |
| GC 8 (diag) | round (15, 1, 'break', -1, 60) | 2025 | 1 | -0.02 | -1.82 | -0.05 | -0.07 / 1.05 | -0.01 / -0.73 / -0.58 | -0.41 | -0.03 | 0.91 | -0.60 | 0.00 | 4838 | diag |
| CL 1 | round (15, 2, 'break', -1, 180) | 799 | 2 | 0.52 | 0.16 | -0.02 | -0.58 / 0.84 | 0.07 / 0.06 / -0.59 | -0.19 | 0.23 | 0.93 | -0.32 | 0.00 | 1487 | NO |
| CL 2 | round (5, 2, 'break', -1, 180) | 877 | 2 | 0.25 | -0.01 | 0.29 | 0.35 / 0.44 | 0.02 / 0.10 / -0.14 | -0.10 | 0.27 | 0.99 | -0.22 | 0.00 | 1648 | NO |
| CL 3 (diag) | round (5, 2, 'break', -1, 120) | 1080 | 1 | 0.03 | -0.37 | -0.23 | -0.46 / 0.32 | -0.05 / 0.07 / -0.50 | -0.29 | 0.08 | 0.98 | -0.36 | 0.00 | 2058 | diag |
| CL 4 (diag) | round (15, 2, 'break', -1, 120) | 954 | 0 | -0.04 | -0.32 | -0.52 | -0.95 / 0.52 | -0.05 / -0.14 / -0.92 | -0.41 | 0.19 | 0.89 | -0.54 | 0.00 | 1812 | diag |
| CL 5 (diag) | round (5, 2, 'reject', -1, 180) | 874 | 1 | -0.20 | -0.82 | -0.73 | -1.24 / 0.90 | -0.02 / -0.15 / -0.96 | -0.38 | -0.38 | 0.66 | -0.59 | 0.00 | 1630 | diag |
| ZN 1 (diag) | round (5, 2, 'break', -1, 180) | 1133 | 0 | -3.27 | -3.50 | -3.62 | -4.63 / -7.49 | -0.67 / -0.61 / -0.58 | -1.32 | 0.41 | 1.00 | -0.84 | 0.00 | 1714 | diag |
| ZN 2 (diag) | round (15, 1, 'break', -1, 180) | 1752 | 0 | -3.42 | -5.34 | -4.66 | -8.19 / -7.86 | -0.69 / -0.81 / -1.26 | -1.81 | 0.03 | 1.00 | -1.04 | 0.00 | 2684 | diag |
| ZN 3 (diag) | round (15, 2, 'break', -1, 180) | 1019 | 0 | -3.45 | -2.73 | -4.02 | -5.89 / -6.59 | -0.68 / -0.71 / -0.70 | -1.33 | 0.32 | 1.00 | -0.88 | 0.00 | 1529 | diag |
| BTC 1 | round (15, 1, 'break', 1, 180) | 1649 | 2 | 0.85 | -0.46 | 0.68 | 0.39 / 1.30 | 0.15 / 0.31 / -0.15 | 0.03 | 0.22 | 0.95 | -0.08 | 0.00 | 2718 | NO |
| BTC 2 | round (15, 2, 'reject', 1, 180) | 873 | 2 | 0.21 | 1.24 | 0.52 | 1.02 / 1.34 | 0.09 / 0.66 / -0.09 | 0.09 | -0.07 | 0.90 | -0.05 | 0.00 | 1438 | NO |
| BTC 3 (diag) | round (15, 2, 'break', 1, 180) | 984 | 1 | 0.17 | -0.49 | 0.78 | 1.78 / 0.89 | -0.01 / 0.60 / -0.08 | 0.02 | -0.10 | 1.00 | -0.12 | 0.50 | 1619 | diag |
| BTC 4 (diag) | round (5, 1, 'reject', 1, 60) | 2836 | 1 | 0.14 | -0.88 | -0.26 | -0.91 / 0.62 | 0.06 / -0.34 / -0.15 | -0.16 | -0.07 | 0.89 | -0.22 | 0.00 | 4614 | diag |
| BTC 5 (diag) | round (15, 1, 'reject', 1, 180) | 1490 | 1 | 0.09 | -0.07 | -0.28 | -0.99 / 1.29 | 0.03 / -0.18 / -0.21 | -0.11 | 0.22 | 0.67 | -0.24 | 0.00 | 2430 | diag |
| HO 1 | round (15, 2, 'reject', -1, 60) | 1785 | 2 | 1.34 | 0.14 | 0.09 | -0.40 / 0.93 | 0.25 / 0.26 / -1.04 | -0.20 | -0.31 | 0.90 | -0.53 | 0.00 | 3757 | NO |
| HO 2 | round (5, 2, 'reject', -1, 180) | 1224 | 2 | 0.99 | 0.43 | 0.64 | 0.62 / 1.52 | 0.15 / 0.53 / -0.31 | 0.03 | 0.14 | 0.96 | -0.27 | 0.00 | 2364 | NO |
| HO 3 | round (5, 1, 'break', -1, 120) | 2844 | 2 | 0.58 | -0.74 | -0.09 | -0.58 / 1.44 | 0.09 / -0.37 / -0.52 | -0.21 | 0.06 | 0.80 | -0.39 | 0.00 | 5097 | NO |
| HO 4 | round (5, 1, 'reject', -1, 180) | 1854 | 2 | 0.40 | -0.21 | 0.59 | 0.87 / 1.34 | -0.03 / 0.08 / 0.40 | 0.01 | -0.21 | 0.94 | -0.22 | 0.00 | 3342 | NO |
| HO 5 | round (15, 1, 'reject', -1, 60) | 3137 | 2 | 0.35 | -1.00 | 0.62 | 0.89 / 1.25 | 0.04 / 0.48 / -0.11 | -0.07 | -0.55 | 0.99 | -0.22 | 0.00 | 5921 | NO |
| HO 6 (diag) | round (15, 2, 'break', 1, 180) | 1202 | 1 | 0.35 | 0.04 | 0.39 | 0.49 / 1.44 | 0.04 / -0.34 / 0.13 | -0.04 | -0.26 | 0.89 | -0.25 | 0.00 | 2330 | diag |
| HO 7 (diag) | round (15, 1, 'reject', -1, 180) | 1712 | 1 | 0.25 | -0.18 | 0.32 | 0.43 / 1.25 | -0.01 / -0.32 / -0.04 | -0.12 | -0.28 | 0.84 | -0.42 | 0.00 | 3096 | diag |
| HO 8 (diag) | round (5, 2, 'reject', -1, 120) | 1556 | 1 | 0.17 | -0.05 | 0.31 | 0.49 / 1.34 | -0.01 / 0.19 / -0.40 | -0.15 | 0.20 | 0.90 | -0.46 | 0.00 | 3094 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 22 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 18 |
| worst-decile corr <= +0.30 | 42 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC round (15, 2, 'reject', 1, 180) | clean | 0.22 | 0.36 | -120697 | -101458 | 625756 | -150524 | 0.32 | 54.3 | 1.55 | -81732 | 281278 | -87130 |
| BTC round (15, 2, 'reject', 1, 180) | H1 | 2.51 | 5.50 | -88041 | -83919 | 266280 | -89320 | 2.56 | 35.7 | 3.49 | -78204 | 136831 | -94285 |
| BTC round (15, 2, 'reject', 1, 180) | H2 | -0.64 | -0.84 | -105148 | -86475 | 417347 | -139000 | -0.35 | 55.6 | 2.39 | -84721 | 205706 | -85639 |
| BTC round (15, 2, 'reject', 1, 180) | all | 0.52 | 0.85 | -115665 | -97164 | 625756 | -150524 | 1.18 | 51.2 | 2.03 | -84270 | 281278 | -94285 |
| CL round (5, 2, 'break', -1, 180) | clean | 0.25 | 0.36 | -141642 | -105844 | 473260 | -270178 | 0.47 | 53.3 | 1.48 | -91530 | 288763 | -133903 |
| CL round (5, 2, 'break', -1, 180) | H1 | 1.63 | 3.05 | -54150 | -47121 | 113934 | -57685 | 1.90 | 50.0 | 2.92 | -76683 | 159595 | -87056 |
| CL round (5, 2, 'break', -1, 180) | H2 | 0.14 | 0.21 | -224121 | -197167 | 705341 | -241636 | 0.12 | 50.0 | 2.34 | -84847 | 199453 | -86938 |
| CL round (5, 2, 'break', -1, 180) | all | 0.29 | 0.44 | -181400 | -141624 | 705341 | -270178 | 0.75 | 51.8 | 1.90 | -89547 | 288763 | -133903 |
| ES round (5, 2, 'reject', -1, 180) | clean | 0.25 | 0.36 | -145433 | -116176 | 413228 | -232401 | 0.56 | 46.7 | 1.51 | -81904 | 272964 | -90140 |
| ES round (5, 2, 'reject', -1, 180) | H1 | -0.77 | -0.90 | -278832 | -216711 | 730927 | -427631 | -0.44 | 53.6 | 2.15 | -104061 | 208122 | -111341 |
| ES round (5, 2, 'reject', -1, 180) | H2 | -0.95 | -1.31 | -204071 | -187155 | 874338 | -211657 | -0.62 | 58.3 | 2.02 | -98279 | 240648 | -99103 |
| ES round (5, 2, 'reject', -1, 180) | all | -0.32 | -0.43 | -205344 | -161984 | 1333189 | -427631 | -0.47 | 50.6 | 1.75 | -92552 | 272964 | -111341 |
| GC round (15, 1, 'reject', 1, 180) | clean | 1.08 | 1.97 | -97869 | -84695 | 421772 | -154793 | 2.33 | 48.6 | 1.57 | -91637 | 298497 | -95415 |
| GC round (15, 1, 'reject', 1, 180) | H1 | 2.02 | 8.11 | -313519 | -256640 | 948300 | -442376 | 3.30 | 35.7 | 3.46 | -79742 | 216957 | -88600 |
| GC round (15, 1, 'reject', 1, 180) | H2 | 0.46 | 0.69 | -548215 | -477042 | 1716253 | -550299 | 0.36 | 47.2 | 1.94 | -179572 | 362544 | -189713 |
| GC round (15, 1, 'reject', 1, 180) | all | 0.96 | 2.09 | -359369 | -247944 | 1716253 | -550299 | 2.76 | 45.8 | 2.00 | -114110 | 362544 | -189713 |
| HO round (5, 2, 'reject', -1, 180) | clean | 0.91 | 1.38 | -125671 | -111150 | 326993 | -165409 | 2.55 | 45.7 | 1.61 | -82221 | 261676 | -94218 |
| HO round (5, 2, 'reject', -1, 180) | H1 | 2.63 | 4.91 | -73486 | -61901 | 182495 | -85040 | 2.42 | 32.1 | 3.35 | -70723 | 135624 | -78903 |
| HO round (5, 2, 'reject', -1, 180) | H2 | 0.49 | 0.79 | -382019 | -357183 | 1329034 | -389295 | 0.47 | 47.2 | 2.17 | -124612 | 210388 | -128934 |
| HO round (5, 2, 'reject', -1, 180) | all | 0.64 | 1.01 | -289595 | -219298 | 1329034 | -389295 | 1.43 | 43.5 | 1.98 | -92725 | 261676 | -128934 |
| NQ round (5, 1, 'break', 1, 180) | clean | 1.03 | 1.64 | -120890 | -98980 | 610002 | -227359 | 1.54 | 43.8 | 1.60 | -87068 | 283047 | -127346 |
| NQ round (5, 1, 'break', 1, 180) | H1 | 2.10 | 5.31 | -88573 | -79526 | 336749 | -113458 | 2.06 | 46.4 | 3.25 | -71295 | 156034 | -90142 |
| NQ round (5, 1, 'break', 1, 180) | H2 | -0.45 | -0.59 | -190733 | -180022 | 687176 | -199789 | -0.34 | 52.8 | 2.18 | -92206 | 239712 | -96540 |
| NQ round (5, 1, 'break', 1, 180) | all | 0.78 | 1.21 | -166384 | -131715 | 718470 | -227359 | 1.95 | 46.4 | 1.98 | -88551 | 283047 | -127346 |
| RTY round (15, 2, 'reject', 1, 120) | clean | 0.29 | 0.50 | -104824 | -87397 | 592059 | -156554 | 0.45 | 54.3 | 1.46 | -84337 | 299882 | -95542 |
| RTY round (15, 2, 'reject', 1, 120) | H1 | -2.08 | -2.22 | -192354 | -164489 | 594419 | -227488 | -0.91 | 64.3 | 2.15 | -85283 | 214016 | -98684 |
| RTY round (15, 2, 'reject', 1, 120) | H2 | 0.91 | 1.61 | -155220 | -116943 | 376794 | -169927 | 1.01 | 58.3 | 2.68 | -93850 | 216480 | -95914 |
| RTY round (15, 2, 'reject', 1, 120) | all | 0.06 | 0.10 | -142484 | -111584 | 855206 | -227488 | 0.12 | 57.1 | 1.84 | -88045 | 299882 | -98684 |
| ZN round (5, 2, 'break', -1, 180) (diag) | clean | -3.26 | -3.46 | -148078 | -129746 | 2978965 | -183283 | -0.98 | 71.4 | 0.79 | -97582 | 327151 | -118530 |
| ZN round (5, 2, 'break', -1, 180) (diag) | H1 | -5.15 | -4.32 | -96793 | -83330 | 644429 | -107485 | -0.99 | 71.4 | 2.21 | -75158 | 168515 | -76805 |
| ZN round (5, 2, 'break', -1, 180) (diag) | H2 | -4.46 | -4.10 | -129776 | -114994 | 1074936 | -143616 | -0.98 | 75.0 | 1.91 | -88213 | 222193 | -98842 |
| ZN round (5, 2, 'break', -1, 180) (diag) | all | -3.62 | -3.67 | -140020 | -123765 | 4649597 | -183283 | -1.00 | 72.0 | 1.24 | -95186 | 327151 | -118530 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES round (5, 2, 'reject', -1, 180) | -36.9 | -77.4 | -6.4 | 14.8 | 3.5 / 18.0 | -87.0 / -47.5 | NO |
| NQ round (5, 1, 'break', 1, 180) | -14.7 | -52.1 | 7.1 | 26.4 | -53.3 / 14.0 | 7.3 / 24.9 | NO |
| RTY round (15, 2, 'reject', 1, 120) | -28.9 | -5.1 | 7.6 | 18.4 | 3.0 / 19.1 | -10.8 / -11.6 | NO |
| GC round (15, 1, 'reject', 1, 180) | 21.7 | -167.6 | -54.0 | -49.7 | 0.7 / 4.1 | -47.1 / -20.2 | NO |
| CL round (5, 2, 'break', -1, 180) | -24.2 | -66.0 | 5.4 | 3.5 | -67.3 / 2.5 | 11.8 / 30.5 | NO |
| ZN round (5, 2, 'break', -1, 180) (diag) | -80.6 | -36.1 | -1.5 | -33.2 | -37.2 / -6.2 | 31.5 / 34.7 | NO |
| BTC round (15, 2, 'reject', 1, 180) | -22.0 | 3.2 | 18.9 | 28.5 | 16.7 / 20.9 | -2.0 / 27.7 | NO |
| HO round (5, 2, 'reject', -1, 180) | -9.2 | -65.6 | -15.6 | -4.5 | 2.8 / 21.0 | 28.8 / 43.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 round (5, 2, 'reject', -1, 180) | gross-positive, cost-negative pre-2023 | 3913 | 4.4 | -25.0 | -12.6 | 29.4 | 0.10 / -0.57 / -0.29 | 39.8 / 10.4 |
| ES 2 round (5, 2, 'break', 1, 120) | gross-positive, cost-negative pre-2023 | 4835 | 8.1 | -21.2 | -9.0 | 29.4 | 0.24 / -0.63 / -0.27 | 32.9 / 3.5 |
| ES 3 (diag) round (15, 2, 'reject', -1, 180) | gross-positive, cost-negative pre-2023 | 3562 | 5.8 | -23.6 | -11.2 | 29.4 | 0.12 / -0.48 / -0.23 | 56.9 / 27.6 |
| ES 4 (diag) round (15, 1, 'break', 1, 180) | gross-positive, cost-negative pre-2023 | 5986 | 7.8 | -21.6 | -9.0 | 29.4 | 0.23 / -0.63 / -0.27 | 46.1 / 16.7 |
| ES 5 (diag) round (5, 1, 'break', 1, 120) | negative pre-2023 | 8684 | -1.3 | -30.6 | -18.2 | 29.4 | -0.06 / -1.31 / -0.78 | 39.2 / 9.8 |
| NQ 1 round (5, 1, 'break', 1, 120) | negative pre-2023 | 6538 | -0.9 | -15.3 | -8.4 | 14.4 | -0.02 / -0.30 / -0.17 | 64.8 / 50.4 |
| NQ 2 round (5, 1, 'break', 1, 180) | negative pre-2023 | 5045 | -17.4 | -31.7 | -24.7 | 14.4 | -0.28 / -0.51 / -0.40 | 75.8 / 61.5 |
| NQ 3 round (15, 1, 'break', 1, 60) | gross-positive, cost-negative pre-2023 | 7819 | 2.1 | -12.2 | -5.4 | 14.4 | 0.07 / -0.41 / -0.18 | 51.6 / 37.2 |
| NQ 4 round (15, 1, 'break', 1, 180) | gross-positive, cost-negative pre-2023 | 4517 | 9.3 | -5.1 | 1.9 | 14.4 | 0.14 / -0.08 / 0.03 | 70.7 / 56.3 |
| NQ 5 (diag) round (5, 2, 'break', 1, 180) | negative pre-2023 | 2844 | -27.6 | -42.0 | -35.1 | 14.4 | -0.32 / -0.48 / -0.40 | 95.0 / 80.7 |
| NQ 6 (diag) round (5, 2, 'break', 1, 120) | gross-positive, cost-negative pre-2023 | 3583 | 2.9 | -11.4 | -4.6 | 14.4 | 0.04 / -0.16 / -0.06 | 69.4 / 55.0 |
| NQ 7 (diag) round (15, 2, 'break', 1, 120) | gross-positive, cost-negative pre-2023 | 3167 | 4.5 | -9.9 | -3.0 | 14.4 | 0.06 / -0.13 / -0.04 | 62.0 / 47.6 |
| RTY 1 round (5, 2, 'break', 1, 120) | negative pre-2023 | 2702 | -24.1 | -38.5 | -36.4 | 14.4 | -0.95 / -1.50 / -1.43 | 26.8 / 12.4 |
| RTY 2 round (15, 2, 'reject', 1, 120) | negative pre-2023 | 2325 | -15.4 | -29.7 | -27.7 | 14.4 | -0.54 / -1.03 / -0.96 | 23.2 / 8.8 |
| RTY 3 (diag) round (5, 2, 'reject', 1, 120) | negative pre-2023 | 2583 | -5.8 | -20.1 | -18.1 | 14.4 | -0.19 / -0.66 / -0.60 | 29.9 / 15.5 |
| RTY 4 (diag) round (15, 2, 'reject', 1, 180) | negative pre-2023 | 1884 | -18.5 | -32.9 | -30.9 | 14.4 | -0.52 / -0.92 / -0.87 | 33.1 / 18.7 |
| RTY 5 (diag) round (5, 2, 'reject', 1, 180) | gross-positive, cost-negative pre-2023 | 2074 | 0.0 | -14.4 | -12.3 | 14.4 | 0.00 / -0.39 / -0.34 | 26.6 / 12.2 |
| GC 1 round (5, 1, 'reject', 1, 180) | negative pre-2023 | 4231 | -8.1 | -32.4 | -23.4 | 24.4 | -0.20 / -0.81 / -0.58 | 83.8 / 59.4 |
| GC 2 round (15, 1, 'reject', 1, 180) | negative pre-2023 | 3926 | -15.5 | -39.8 | -30.8 | 24.4 | -0.40 / -1.03 / -0.79 | 63.6 / 39.2 |
| GC 3 round (5, 2, 'break', -1, 120) | gross-positive, cost-negative pre-2023 | 2529 | 5.8 | -18.6 | -9.6 | 24.4 | 0.13 / -0.43 / -0.22 | 63.8 / 39.5 |
| GC 4 round (15, 2, 'reject', 1, 180) | negative pre-2023 | 2022 | -17.6 | -41.9 | -33.0 | 24.4 | -0.30 / -0.72 / -0.57 | 60.6 / 36.2 |
| GC 5 round (15, 2, 'break', -1, 60) | negative pre-2023 | 2858 | -3.8 | -28.2 | -19.3 | 24.4 | -0.13 / -0.97 / -0.67 | 38.1 / 13.7 |
| GC 6 (diag) round (15, 2, 'break', -1, 120) | gross-positive, cost-negative pre-2023 | 2217 | 6.2 | -18.1 | -9.2 | 24.4 | 0.14 / -0.41 / -0.21 | 42.6 / 18.2 |
| GC 7 (diag) round (5, 1, 'break', -1, 120) | negative pre-2023 | 4982 | -1.9 | -26.2 | -17.2 | 24.4 | -0.07 / -0.89 / -0.59 | 27.5 / 3.2 |
| GC 8 (diag) round (15, 1, 'break', -1, 60) | negative pre-2023 | 5655 | -10.0 | -34.3 | -25.3 | 24.4 | -0.54 / -1.82 / -1.35 | 23.5 / -0.8 |
| CL 1 round (15, 2, 'break', -1, 180) | positive pre-2023 | 3760 | 31.5 | 7.1 | 8.6 | 24.4 | 0.69 / 0.16 / 0.19 | 46.7 / 22.4 |
| CL 2 round (5, 2, 'break', -1, 180) | gross-positive, cost-negative pre-2023 | 4161 | 24.1 | -0.3 | 1.2 | 24.4 | 0.67 / -0.01 / 0.03 | 34.8 / 10.5 |
| CL 3 (diag) round (5, 2, 'break', -1, 120) | gross-positive, cost-negative pre-2023 | 5239 | 14.0 | -10.4 | -8.9 | 24.4 | 0.48 / -0.37 / -0.31 | 23.7 / -0.7 |
| CL 4 (diag) round (15, 2, 'break', -1, 120) | gross-positive, cost-negative pre-2023 | 4626 | 14.7 | -9.6 | -8.1 | 24.4 | 0.49 / -0.32 / -0.27 | 22.4 / -1.9 |
| CL 5 (diag) round (5, 2, 'reject', -1, 180) | negative pre-2023 | 4357 | -7.5 | -31.8 | -30.4 | 24.4 | -0.19 / -0.82 / -0.78 | 18.1 / -6.3 |
| ZN 1 (diag) round (5, 2, 'break', -1, 180) | gross-positive, cost-negative pre-2023 | 5869 | 6.7 | -28.9 | -33.9 | 35.6 | 0.84 / -3.50 / -4.09 | 7.7 / -27.9 |
| ZN 2 (diag) round (15, 1, 'break', -1, 180) | gross-positive, cost-negative pre-2023 | 8964 | 4.6 | -31.0 | -36.0 | 35.6 | 0.82 / -5.34 / -6.19 | 14.5 / -21.1 |
| ZN 3 (diag) round (15, 2, 'break', -1, 180) | gross-positive, cost-negative pre-2023 | 5270 | 8.7 | -27.0 | -32.0 | 35.6 | 0.87 / -2.73 / -3.24 | 6.8 / -28.8 |
| BTC 1 round (15, 1, 'break', 1, 180) | negative pre-2023 | 627 | -18.1 | -72.4 | -42.0 | 54.4 | -0.12 / -0.46 / -0.27 | 177.0 / 122.7 |
| BTC 2 round (15, 2, 'reject', 1, 180) | positive pre-2023 | 310 | 263.0 | 208.6 | 238.8 | 54.4 | 1.55 / 1.24 / 1.41 | 105.7 / 51.3 |
| BTC 3 (diag) round (15, 2, 'break', 1, 180) | negative pre-2023 | 338 | -64.7 | -119.1 | -88.7 | 54.4 | -0.27 / -0.49 / -0.36 | 85.3 / 30.9 |
| BTC 4 (diag) round (5, 1, 'reject', 1, 60) | negative pre-2023 | 956 | -15.7 | -70.0 | -39.8 | 54.4 | -0.20 / -0.88 / -0.50 | 64.0 / 9.6 |
| BTC 5 (diag) round (15, 1, 'reject', 1, 180) | gross-positive, cost-negative pre-2023 | 576 | 43.6 | -10.7 | 19.6 | 54.4 | 0.30 / -0.07 / 0.13 | 69.5 / 15.1 |
| HO 1 round (15, 2, 'reject', -1, 60) | positive pre-2023 | 7457 | 18.3 | 5.6 | 5.9 | 12.8 | 0.48 / 0.14 / 0.15 | 37.2 / 24.4 |
| HO 2 round (5, 2, 'reject', -1, 180) | positive pre-2023 | 5003 | 37.2 | 24.5 | 25.2 | 12.8 | 0.66 / 0.43 / 0.45 | 43.8 / 31.1 |
| HO 3 round (5, 1, 'break', -1, 120) | negative pre-2023 | 12212 | -3.8 | -16.5 | -15.6 | 12.8 | -0.18 / -0.74 / -0.69 | 22.5 / 9.7 |
| HO 4 round (5, 1, 'reject', -1, 180) | gross-positive, cost-negative pre-2023 | 8200 | 5.9 | -6.8 | -5.7 | 12.8 | 0.16 / -0.21 / -0.18 | 22.5 / 9.7 |
| HO 5 round (15, 1, 'reject', -1, 60) | negative pre-2023 | 13262 | -3.0 | -15.7 | -14.9 | 12.8 | -0.20 / -1.00 / -0.95 | 17.6 / 4.9 |
| HO 6 (diag) round (15, 2, 'break', 1, 180) | positive pre-2023 | 4924 | 14.3 | 1.5 | 2.1 | 12.8 | 0.31 / 0.04 / 0.05 | 24.5 / 11.7 |
| HO 7 (diag) round (15, 1, 'reject', -1, 180) | gross-positive, cost-negative pre-2023 | 7439 | 6.8 | -6.0 | -4.9 | 12.8 | 0.20 / -0.18 / -0.15 | 19.2 / 6.4 |
| HO 8 (diag) round (5, 2, 'reject', -1, 120) | gross-positive, cost-negative pre-2023 | 6358 | 11.1 | -1.6 | -1.0 | 12.8 | 0.29 / -0.05 / -0.04 | 15.5 / 2.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): BTC: 2 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 0.90, p(top) = 0.62); CL: 2 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.01, p(top) = 0.05); ES: 2 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.04, p(top) = 0.23); GC: 5 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.00, p(top) = 0.14); HO: 5 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.08, p(top) = 0.26); NQ: 4 cells pass the clean rule against a replicate mean of 5.4 (p(count) = 0.82, p(top) = 0.04); RTY: 2 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.31, p(top) = 0.62); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 22 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.14 (BTC round (15, 2, 'reject', 1, 180)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 11, 'gross-positive, cost-negative pre-2023': 7, 'positive pre-2023': 4}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q27.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q27/ (`Q27_CO_all_selected_scored.csv`).

DONE Q27
