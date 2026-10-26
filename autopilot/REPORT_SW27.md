# REPORT SW27 - unscheduled 1-minute jump shocks, follow or fade (D08/D10 H1)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 18 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +1.03.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: |1-min return| >= k x EWM(span 1000) sigma (k 4/5/6/8), minutes within +-2 min of 08:30/10:00/14:00 ET excluded; follow or fade; exact hold 3/10/30/60 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 32 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      32 |         24 |         7 |               1.178 |                2 |          7 |            3 |
| CL    |      32 |         32 |         1 |               0.902 |                2 |          1 |            3 |
| ES    |      32 |         32 |         1 |               0.378 |                2 |          1 |            3 |
| GC    |      32 |         32 |         4 |               0.945 |                2 |          4 |            3 |
| NQ    |      32 |         32 |         4 |               1.952 |                2 |          4 |            3 |
| RTY   |      32 |         32 |         1 |               0.321 |                2 |          1 |            3 |
| YM    |      32 |         32 |         0 |               0.14  |                1 |          0 |            3 |
| ZN    |      32 |         24 |         0 |              -0.738 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    1 |             0.21 |               2 |       0.2  |                       0.378 |            0.481 |           0.986 |     0.12 |       0.378 |                0.998 |
| NQ    |     100 |                    4 |             1.77 |               5 |       0.1  |                       1.216 |            0.682 |           1.209 |     0.04 |       1.952 |                1.631 |
| RTY   |     100 |                    1 |             0.32 |               2 |       0.28 |                       0.028 |            0.553 |           0.925 |     0.28 |       0.028 |                1.024 |
| YM    |     100 |                    0 |             0.51 |               3 |       1    |                     nan     |            0.561 |           0.997 |   nan    |     nan     |                1.049 |
| GC    |     100 |                    4 |             0.27 |               2 |       0    |                       0.563 |            0.594 |           1.201 |     0.11 |       0.945 |                1.312 |
| CL    |     100 |                    1 |             0.05 |               1 |       0.05 |                       0.902 |            0.572 |           1.005 |     0.01 |       0.902 |                1.005 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    7 |             2.15 |               7 |       0.01 |                       0.614 |            0.656 |           1.23  |     0.42 |       1.178 |                1.643 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 1m jump>=5.0sigma dir=follow hold=60m | 753 | 2 | 0.38 | -0.32 | -0.70 | -2.18 / 0.32 | 0.08 / -0.30 / -0.92 | -0.33 | 0.30 | 0.81 | -0.41 | 0.00 | 1261 | NO |
| ES 2 (diag) | 1m jump>=8.0sigma dir=follow hold=3m | 143 | 1 | 0.37 | -1.28 | -0.03 | -0.71 / -0.57 | 0.03 / -0.19 / -0.25 | -0.13 | 0.21 | 1.00 | -0.20 | 0.00 | 289 | diag |
| ES 3 (diag) | 1m jump>=8.0sigma dir=follow hold=60m | 133 | 1 | 0.19 | -0.12 | -0.12 | -0.60 / 1.02 | -0.01 / -0.06 / -0.39 | -0.14 | 0.10 | 0.71 | -0.29 | 0.00 | 263 | diag |
| ES 4 (diag) | 1m jump>=8.0sigma dir=follow hold=10m | 138 | 1 | 0.15 | -0.61 | -0.19 | -0.56 / 0.46 | -0.01 / -0.28 / -0.44 | -0.22 | 0.11 | 0.96 | -0.37 | 0.00 | 278 | diag |
| NQ 1 | 1m jump>=6.0sigma dir=follow hold=60m | 495 | 2 | 1.95 | 0.32 | 1.03 | 0.04 / 1.18 | 0.34 / -0.07 / -0.49 | 0.09 | 0.36 | 0.99 | -0.10 | 0.50 | 841 | NO |
| NQ 2 | 1m jump>=5.0sigma dir=follow hold=60m | 825 | 2 | 1.57 | -0.04 | 0.56 | -0.45 / 0.83 | 0.22 / 0.50 / -0.85 | -0.01 | 0.37 | 0.98 | -0.21 | 0.75 | 1347 | NO |
| NQ 3 | 1m jump>=4.0sigma dir=follow hold=60m | 1339 | 2 | 0.75 | 0.25 | -0.07 | -0.96 / 1.40 | 0.09 / -0.04 / -0.77 | -0.15 | 0.44 | 0.75 | -0.34 | 0.00 | 2161 | NO |
| NQ 4 | 1m jump>=5.0sigma dir=follow hold=10m | 1213 | 2 | 0.59 | -0.39 | -0.24 | -1.26 / 0.51 | 0.11 / -0.21 / -0.54 | -0.15 | 0.40 | 0.91 | -0.32 | 0.00 | 1964 | NO |
| NQ 5 (diag) | 1m jump>=6.0sigma dir=follow hold=10m | 618 | 1 | 1.29 | -0.26 | 0.60 | -0.19 / 0.64 | 0.21 / 0.01 / -0.42 | -0.01 | 0.42 | 0.99 | -0.19 | 0.25 | 1058 | diag |
| NQ 6 (diag) | 1m jump>=6.0sigma dir=follow hold=30m | 542 | 1 | 0.81 | 0.22 | 0.64 | 0.43 / 1.24 | 0.15 / 0.09 / -0.29 | 0.03 | 0.35 | 0.98 | -0.15 | 0.75 | 925 | diag |
| NQ 7 (diag) | 1m jump>=8.0sigma dir=follow hold=60m | 178 | 1 | 0.61 | 0.50 | 0.12 | -0.52 / 1.50 | 0.08 / 0.25 / -0.61 | -0.06 | 0.16 | 0.62 | -0.24 | 0.00 | 319 | diag |
| RTY 1 | 1m jump>=6.0sigma dir=fade hold=30m | 541 | 2 | 0.03 | -0.86 | -0.55 | -1.14 / 0.23 | -0.02 / -0.90 / 0.16 | -0.19 | -0.23 | 0.90 | -0.34 | 0.00 | 935 | NO |
| RTY 2 (diag) | 1m jump>=4.0sigma dir=fade hold=60m | 1093 | 1 | 0.32 | -0.55 | 0.41 | 0.57 / 0.20 | 0.04 / -0.16 / 0.34 | -0.00 | -0.09 | 1.00 | -0.13 | 0.00 | 1816 | diag |
| RTY 3 (diag) | 1m jump>=4.0sigma dir=fade hold=30m | 1411 | 1 | 0.13 | -1.43 | 0.08 | 0.12 / -0.80 | 0.03 / -0.28 / 0.09 | -0.12 | 0.11 | 1.00 | -0.21 | 0.75 | 2347 | diag |
| RTY 4 (diag) | 1m jump>=5.0sigma dir=fade hold=30m | 832 | 1 | 0.10 | -1.32 | 0.04 | 0.10 / 0.01 | 0.02 / -0.50 / 0.34 | -0.07 | 0.08 | 1.00 | -0.19 | 0.50 | 1419 | diag |
| YM 1 (diag) | 1m jump>=4.0sigma dir=follow hold=60m | 1273 | 1 | 0.14 | -0.21 | -0.45 | -1.17 / 0.13 | -0.04 / 0.12 / -0.61 | -0.22 | 0.08 | 0.99 | -0.34 | 0.00 | 2060 | diag |
| YM 2 (diag) | 1m jump>=6.0sigma dir=fade hold=30m | 645 | 1 | 0.10 | -1.17 | 0.19 | 0.46 / 0.52 | -0.05 / -0.56 / 0.51 | -0.08 | 0.11 | 1.00 | -0.22 | 0.00 | 1077 | diag |
| YM 3 (diag) | 1m jump>=5.0sigma dir=follow hold=60m | 820 | 1 | 0.02 | 0.12 | -0.42 | -1.00 / 0.70 | -0.03 / 0.50 / -0.96 | -0.24 | -0.10 | 0.82 | -0.38 | 0.00 | 1356 | diag |
| GC 1 | 1m jump>=6.0sigma dir=fade hold=3m | 433 | 2 | 0.94 | -1.65 | -0.33 | -0.86 / 0.16 | 0.10 / -1.80 / -0.90 | -0.62 | -0.28 | 1.00 | -1.06 | 0.00 | 757 | NO |
| GC 2 | 1m jump>=5.0sigma dir=fade hold=3m | 921 | 2 | 0.90 | -2.82 | -0.17 | -0.48 / -0.17 | 0.08 / -2.33 / -0.33 | -0.84 | 0.05 | 1.00 | -1.39 | 0.00 | 1521 | NO |
| GC 3 | 1m jump>=8.0sigma dir=fade hold=30m | 144 | 2 | 0.36 | -0.99 | -0.11 | -0.36 / 1.15 | 0.05 / -1.25 / -0.03 | -0.20 | -0.61 | 0.70 | -0.54 | 0.00 | 240 | NO |
| GC 4 | 1m jump>=5.0sigma dir=fade hold=30m | 735 | 2 | 0.05 | -1.84 | 0.45 | 0.76 / 0.88 | -0.03 / -1.10 / 0.79 | -0.09 | -0.51 | 0.99 | -0.40 | 0.00 | 1215 | NO |
| GC 5 (diag) | 1m jump>=8.0sigma dir=fade hold=3m | 157 | 1 | 0.40 | -0.55 | -0.65 | -1.24 / 0.80 | 0.04 / -2.03 / -1.28 | -0.72 | -0.49 | 0.84 | -1.21 | 0.00 | 257 | diag |
| GC 6 (diag) | 1m jump>=4.0sigma dir=follow hold=60m | 1339 | 1 | 0.37 | -1.26 | -0.50 | -1.17 / 0.93 | -0.03 / -1.64 / -0.23 | -0.43 | 0.31 | 0.68 | -0.61 | 0.00 | 2172 | diag |
| GC 7 (diag) | 1m jump>=8.0sigma dir=follow hold=60m | 142 | 1 | -0.02 | -0.25 | -0.09 | -0.16 / 1.34 | -0.04 / 0.08 / -0.63 | -0.18 | 0.53 | 0.65 | -0.48 | 0.00 | 236 | diag |
| CL 1 | 1m jump>=5.0sigma dir=follow hold=60m | 933 | 2 | 0.90 | -1.04 | 0.44 | 0.14 / 0.37 | 0.19 / -0.48 / 0.43 | -0.04 | -0.21 | 1.00 | -0.13 | 0.25 | 1447 | NO |
| CL 2 (diag) | 1m jump>=8.0sigma dir=follow hold=60m | 162 | 1 | 0.21 | -0.30 | -0.02 | -0.24 / 0.89 | 0.06 / -0.17 / -0.32 | -0.11 | -0.14 | 0.87 | -0.31 | 0.00 | 302 | diag |
| CL 3 (diag) | 1m jump>=6.0sigma dir=follow hold=60m | 472 | 1 | -0.01 | -0.54 | 0.02 | 0.00 / 0.58 | 0.03 / -0.40 / 0.05 | -0.15 | -0.19 | 0.96 | -0.35 | 0.00 | 783 | diag |
| CL 4 (diag) | 1m jump>=8.0sigma dir=follow hold=3m | 174 | 1 | -0.20 | -1.51 | 0.06 | 0.20 / -0.66 | -0.09 / -0.19 / -0.36 | -0.28 | 0.04 | 1.00 | -0.39 | 0.00 | 322 | diag |
| ZN 1 (diag) | 1m jump>=8.0sigma dir=fade hold=30m | 59 | 0 | -0.74 | -0.94 | -1.21 | -1.90 / -2.18 | -0.20 / -0.08 / -0.43 | -0.44 | 0.34 | 1.00 | -0.42 | 0.00 | 84 S | diag |
| ZN 2 (diag) | 1m jump>=8.0sigma dir=follow hold=60m | 59 | 0 | -0.78 | -1.17 | -0.61 | -0.51 / -1.15 | -0.18 / -0.17 / -0.11 | -0.37 | -0.12 | 1.00 | -0.35 | 0.00 | 83 S | diag |
| ZN 3 (diag) | 1m jump>=6.0sigma dir=fade hold=30m | 149 | 0 | -0.98 | -1.80 | -1.47 | -2.58 / -3.35 | -0.26 / -0.18 / -0.37 | -0.58 | 0.55 | 1.00 | -0.44 | 0.00 | 224 | diag |
| BTC 1 | 1m jump>=6.0sigma dir=fade hold=3m | 205 | 2 | 1.18 | -0.27 | 0.66 | 0.04 / 0.65 | 0.18 / 0.40 / -0.19 | 0.06 | -0.04 | 1.00 | -0.08 | 0.25 | 331 | NO |
| BTC 2 | 1m jump>=5.0sigma dir=fade hold=3m | 420 | 2 | 1.12 | -0.98 | 0.38 | -0.76 / 0.15 | 0.16 / -0.32 / -0.19 | -0.07 | 0.04 | 1.00 | -0.16 | 0.25 | 696 | NO |
| BTC 3 | 1m jump>=5.0sigma dir=fade hold=10m | 380 | 2 | 0.56 | -0.74 | 0.40 | 0.10 / 0.26 | 0.04 / 0.07 / -0.07 | -0.05 | 0.11 | 1.00 | -0.16 | 0.75 | 634 | NO |
| BTC 4 | 1m jump>=4.0sigma dir=follow hold=60m | 701 | 2 | 0.50 | 0.61 | 0.31 | -0.03 / 1.34 | 0.06 / 0.38 / -0.28 | -0.04 | 0.28 | 0.94 | -0.19 | 0.50 | 1183 | NO |
| BTC 5 | 1m jump>=6.0sigma dir=follow hold=60m | 170 | 2 | 0.45 | -0.80 | -0.05 | -0.60 / 1.02 | 0.10 / -0.31 / -0.39 | -0.09 | -0.00 | 0.65 | -0.29 | 0.00 | 286 | NO |
| BTC 6 | 1m jump>=6.0sigma dir=fade hold=10m | 188 | 2 | 0.37 | -0.34 | 0.53 | 0.82 / 0.77 | 0.03 / 0.38 / 0.07 | 0.04 | 0.09 | 0.99 | -0.09 | 0.50 | 309 | NO |
| BTC 7 | 1m jump>=5.0sigma dir=fade hold=30m | 344 | 2 | 0.13 | -1.41 | -0.19 | -0.68 / 0.99 | -0.04 / -0.37 / -0.15 | -0.16 | 0.32 | 0.76 | -0.29 | 0.00 | 577 | NO |
| BTC 8 (diag) | 1m jump>=8.0sigma dir=fade hold=3m | 89 | 2 | 0.70 | -0.22 | 0.78 | 0.99 / 0.67 | 0.10 / 0.47 / 0.04 | 0.10 | 0.11 | 1.00 | -0.05 | 0.75 | 124 | diag |
| BTC 9 (diag) | 1m jump>=6.0sigma dir=follow hold=30m | 179 | 1 | 0.27 | -1.15 | -0.16 | -0.68 / 1.18 | 0.07 / -0.61 / -0.25 | -0.13 | -0.28 | 0.72 | -0.30 | 0.00 | 295 | diag |
| BTC 10 (diag) | 1m jump>=4.0sigma dir=follow hold=30m | 794 | 1 | 0.22 | 0.74 | 0.16 | -0.03 / 0.61 | 0.03 / 0.28 / -0.26 | -0.08 | 0.28 | 0.96 | -0.20 | 0.00 | 1335 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 18 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 15 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 26 |
| worst-decile corr <= +0.30 | 30 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 2 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 1m jump>=6.0sigma dir=fade hold=3m | clean | 1.17 | 2.19 | -119615 | -89807 | 403809 | -185789 | 2.63 | 29.5 | 1.64 | -94066 | 254986 | -105090 |
| BTC 1m jump>=6.0sigma dir=fade hold=3m | H1 | 1.73 | 3.05 | -90578 | -74544 | 167833 | -127428 | 2.01 | 28.6 | 3.22 | -59003 | 136317 | -60719 |
| BTC 1m jump>=6.0sigma dir=fade hold=3m | H2 | -0.62 | -0.66 | -323418 | -201897 | 577338 | -532646 | -0.54 | 33.3 | 2.30 | -79220 | 253845 | -82379 |
| BTC 1m jump>=6.0sigma dir=fade hold=3m | all | 0.66 | 0.90 | -166434 | -118102 | 577338 | -532646 | 1.89 | 30.4 | 2.02 | -89011 | 254986 | -105090 |
| CL 1m jump>=5.0sigma dir=follow hold=60m | clean | 0.95 | 1.55 | -117792 | -99808 | 394997 | -149575 | 2.17 | 44.8 | 1.65 | -83442 | 269261 | -87610 |
| CL 1m jump>=5.0sigma dir=follow hold=60m | H1 | -3.16 | -3.23 | -89859 | -80769 | 453533 | -92707 | -0.97 | 71.4 | 2.35 | -77400 | 149239 | -78978 |
| CL 1m jump>=5.0sigma dir=follow hold=60m | H2 | 0.65 | 1.46 | -255436 | -212209 | 946533 | -262660 | 0.65 | 55.6 | 2.91 | -105367 | 227992 | -115239 |
| CL 1m jump>=5.0sigma dir=follow hold=60m | all | 0.44 | 0.86 | -164117 | -130043 | 946533 | -262660 | 1.09 | 51.2 | 2.04 | -88824 | 269261 | -115239 |
| ES 1m jump>=5.0sigma dir=follow hold=60m | clean | 0.44 | 0.72 | -109151 | -94369 | 500800 | -163968 | 0.79 | 46.7 | 1.54 | -85456 | 279011 | -90761 |
| ES 1m jump>=5.0sigma dir=follow hold=60m | H1 | -0.96 | -1.23 | -162047 | -140109 | 553238 | -215967 | -0.51 | 53.6 | 2.52 | -75761 | 175788 | -79809 |
| ES 1m jump>=5.0sigma dir=follow hold=60m | H2 | -3.06 | -3.22 | -185817 | -168073 | 1280761 | -199080 | -1.00 | 69.4 | 1.56 | -106528 | 252695 | -113036 |
| ES 1m jump>=5.0sigma dir=follow hold=60m | all | -0.70 | -0.94 | -157953 | -132475 | 1964387 | -215967 | -0.59 | 53.0 | 1.69 | -91156 | 279011 | -113036 |
| GC 1m jump>=5.0sigma dir=fade hold=30m | clean | 0.05 | 0.07 | -122657 | -102686 | 826795 | -222707 | 0.05 | 50.5 | 1.43 | -88716 | 279435 | -95960 |
| GC 1m jump>=5.0sigma dir=fade hold=30m | H1 | -0.62 | -0.81 | -525082 | -428250 | 1814585 | -750978 | -0.29 | 57.1 | 1.73 | -149770 | 279310 | -161415 |
| GC 1m jump>=5.0sigma dir=fade hold=30m | H2 | 1.92 | 3.89 | -309140 | -266450 | 578756 | -347157 | 3.42 | 38.9 | 3.28 | -95609 | 195045 | -120331 |
| GC 1m jump>=5.0sigma dir=fade hold=30m | all | 0.45 | 0.71 | -309645 | -220975 | 1814585 | -750978 | 0.82 | 49.4 | 1.92 | -105797 | 279435 | -161415 |
| NQ 1m jump>=6.0sigma dir=follow hold=60m | clean | 2.00 | 3.92 | -104889 | -80112 | 283799 | -172229 | 6.40 | 37.1 | 1.80 | -84193 | 237180 | -88521 |
| NQ 1m jump>=6.0sigma dir=follow hold=60m | H1 | 1.03 | 1.76 | -139983 | -118176 | 286640 | -174494 | 1.12 | 46.4 | 2.76 | -74972 | 165303 | -87167 |
| NQ 1m jump>=6.0sigma dir=follow hold=60m | H2 | -0.56 | -0.77 | -217498 | -190161 | 681532 | -219900 | -0.43 | 55.6 | 1.99 | -100710 | 248473 | -104184 |
| NQ 1m jump>=6.0sigma dir=follow hold=60m | all | 1.03 | 1.68 | -162269 | -125225 | 693132 | -219900 | 2.67 | 42.9 | 2.00 | -90008 | 248473 | -104184 |
| RTY 1m jump>=6.0sigma dir=fade hold=30m | clean | -0.07 | -0.10 | -134571 | -114983 | 677328 | -191436 | -0.10 | 49.5 | 1.44 | -85685 | 290416 | -108393 |
| RTY 1m jump>=6.0sigma dir=fade hold=30m | H1 | -3.46 | -3.33 | -163678 | -146114 | 910833 | -199533 | -0.93 | 64.3 | 1.93 | -98659 | 167850 | -116839 |
| RTY 1m jump>=6.0sigma dir=fade hold=30m | H2 | -0.07 | -0.09 | -215069 | -186397 | 926583 | -250793 | -0.04 | 41.7 | 2.65 | -76820 | 207042 | -87523 |
| RTY 1m jump>=6.0sigma dir=fade hold=30m | all | -0.55 | -0.71 | -174453 | -144886 | 2099147 | -250793 | -0.45 | 50.6 | 1.78 | -88772 | 290416 | -116839 |
| YM 1m jump>=6.0sigma dir=fade hold=30m (diag) | clean | -0.02 | -0.03 | -129881 | -117995 | 614089 | -151296 | -0.03 | 51.4 | 1.41 | -89092 | 274076 | -110127 |
| YM 1m jump>=6.0sigma dir=fade hold=30m (diag) | H1 | -1.52 | -1.93 | -139085 | -124845 | 602763 | -169861 | -0.67 | 64.3 | 2.27 | -81230 | 148534 | -98594 |
| YM 1m jump>=6.0sigma dir=fade hold=30m (diag) | H2 | 1.73 | 3.03 | -145941 | -117714 | 423452 | -163493 | 1.72 | 38.9 | 3.00 | -75703 | 216226 | -78768 |
| YM 1m jump>=6.0sigma dir=fade hold=30m (diag) | all | 0.19 | 0.27 | -146727 | -125902 | 1216853 | -190864 | 0.25 | 50.6 | 1.89 | -87825 | 274076 | -110127 |
| ZN 1m jump>=8.0sigma dir=follow hold=60m (diag) | clean | -0.65 | -0.79 | -191234 | -138143 | 797819 | -313315 | -0.75 | 21.9 | 1.28 | -86443 | 357030 | -120425 |
| ZN 1m jump>=8.0sigma dir=follow hold=60m (diag) | H1 | -0.48 | -0.71 | -79671 | -70048 | 130473 | -79671 | -0.49 | 10.7 | 2.66 | -85577 | 161873 | -92867 |
| ZN 1m jump>=8.0sigma dir=follow hold=60m (diag) | H2 | -0.54 | -0.73 | -158000 | -118836 | 358296 | -207459 | -0.46 | 22.2 | 2.37 | -95770 | 208339 | -100383 |
| ZN 1m jump>=8.0sigma dir=follow hold=60m (diag) | all | -0.61 | -0.75 | -173591 | -127287 | 1054730 | -313315 | -0.79 | 20.2 | 1.73 | -89526 | 357030 | -120425 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 1m jump>=5.0sigma dir=follow hold=60m | -42.8 | -25.5 | 4.3 | 14.8 | 9.0 / 15.6 | 24.8 / 24.6 | NO |
| NQ 1m jump>=6.0sigma dir=follow hold=60m | -9.8 | -31.0 | 3.4 | 11.4 | 9.9 / 15.4 | 11.6 / 16.6 | NO |
| RTY 1m jump>=6.0sigma dir=fade hold=30m | -40.3 | -37.8 | 5.8 | 12.1 | -20.5 / 9.1 | -45.3 / -10.7 | NO |
| YM 1m jump>=6.0sigma dir=fade hold=30m (diag) | -26.7 | -22.7 | 7.3 | 9.3 | -23.7 / 4.6 | -10.3 / 8.9 | NO |
| GC 1m jump>=5.0sigma dir=fade hold=30m | -13.7 | -182.5 | -32.1 | -32.3 | -0.4 / 9.5 | -197.8 / -143.3 | NO |
| CL 1m jump>=5.0sigma dir=follow hold=60m | -18.7 | -34.7 | 6.6 | 20.0 | 2.6 / 15.6 | 28.7 / 30.4 | NO |
| ZN 1m jump>=8.0sigma dir=follow hold=60m (diag) | -39.1 | -44.2 | 1.8 | -24.3 | -45.4 / 2.2 | 0.7 / 14.6 | NO |
| BTC 1m jump>=6.0sigma dir=fade hold=3m | -18.1 | -16.3 | 4.4 | 8.5 | -17.3 / -0.0 | 46.6 / 54.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 1m jump>=5.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 3643 | 19.4 | -10.0 | 3.8 | 29.4 | 0.62 / -0.32 / 0.13 | 46.5 / 17.1 |
| ES 2 (diag) 1m jump>=8.0sigma dir=follow hold=3m | negative pre-2023 | 622 | -11.8 | -41.1 | -27.5 | 29.4 | -0.38 / -1.28 / -0.87 | 64.9 / 35.5 |
| ES 3 (diag) 1m jump>=8.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 568 | 17.5 | -11.9 | 1.8 | 29.4 | 0.18 / -0.12 / 0.02 | 61.4 / 32.0 |
| ES 4 (diag) 1m jump>=8.0sigma dir=follow hold=10m | gross-positive, cost-negative pre-2023 | 600 | 1.2 | -28.2 | -14.5 | 29.4 | 0.03 / -0.61 / -0.32 | 41.7 / 12.3 |
| NQ 1 1m jump>=6.0sigma dir=follow hold=60m | positive pre-2023 | 2685 | 33.7 | 19.4 | 27.7 | 14.4 | 0.55 / 0.32 / 0.45 | 248.3 / 234.0 |
| NQ 2 1m jump>=5.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 4289 | 12.9 | -1.5 | 6.9 | 14.4 | 0.28 / -0.04 / 0.15 | 122.8 / 108.4 |
| NQ 3 1m jump>=4.0sigma dir=follow hold=60m | positive pre-2023 | 7248 | 22.6 | 8.3 | 16.7 | 14.4 | 0.68 / 0.25 / 0.51 | 60.8 / 46.4 |
| NQ 4 1m jump>=5.0sigma dir=follow hold=10m | gross-positive, cost-negative pre-2023 | 6223 | 5.9 | -8.4 | 0.0 | 14.4 | 0.30 / -0.39 / 0.02 | 35.7 / 21.4 |
| NQ 5 (diag) 1m jump>=6.0sigma dir=follow hold=10m | gross-positive, cost-negative pre-2023 | 3379 | 7.0 | -7.3 | 1.0 | 14.4 | 0.23 / -0.26 / 0.03 | 82.6 / 68.2 |
| NQ 6 (diag) 1m jump>=6.0sigma dir=follow hold=30m | positive pre-2023 | 2953 | 24.6 | 10.2 | 18.6 | 14.4 | 0.53 / 0.22 / 0.40 | 80.2 / 65.9 |
| NQ 7 (diag) 1m jump>=8.0sigma dir=follow hold=60m | positive pre-2023 | 1021 | 68.6 | 54.2 | 62.5 | 14.4 | 0.63 / 0.50 / 0.58 | 167.2 / 152.8 |
| RTY 1 1m jump>=6.0sigma dir=fade hold=30m | negative pre-2023 | 1474 | -9.4 | -23.8 | -21.6 | 14.4 | -0.34 / -0.86 / -0.79 | 12.3 / -2.1 |
| RTY 2 (diag) 1m jump>=4.0sigma dir=fade hold=60m | gross-positive, cost-negative pre-2023 | 3624 | 3.4 | -11.0 | -8.8 | 14.4 | 0.18 / -0.55 / -0.43 | 22.0 / 7.6 |
| RTY 3 (diag) 1m jump>=4.0sigma dir=fade hold=30m | negative pre-2023 | 4493 | -7.9 | -22.3 | -20.1 | 14.4 | -0.51 / -1.43 / -1.29 | 15.2 / 0.8 |
| RTY 4 (diag) 1m jump>=5.0sigma dir=fade hold=30m | negative pre-2023 | 2480 | -12.1 | -26.4 | -24.3 | 14.4 | -0.60 / -1.32 / -1.21 | 14.4 / 0.0 |
| YM 1 (diag) 1m jump>=4.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 7511 | 11.2 | -3.2 | 2.5 | 14.4 | 0.73 / -0.21 / 0.17 | 16.0 / 1.7 |
| YM 2 (diag) 1m jump>=6.0sigma dir=fade hold=30m | negative pre-2023 | 2780 | -11.7 | -26.1 | -20.5 | 14.4 | -0.53 / -1.17 / -0.92 | 13.8 / -0.6 |
| YM 3 (diag) 1m jump>=5.0sigma dir=follow hold=60m | positive pre-2023 | 4279 | 16.9 | 2.6 | 8.2 | 14.4 | 0.78 / 0.12 / 0.38 | 16.4 / 2.0 |
| GC 1 1m jump>=6.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 3659 | 6.4 | -18.0 | -7.9 | 24.4 | 0.59 / -1.65 / -0.73 | 43.5 / 19.2 |
| GC 2 1m jump>=5.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 6684 | 4.2 | -20.1 | -10.2 | 24.4 | 0.60 / -2.82 / -1.44 | 34.4 / 10.0 |
| GC 3 1m jump>=8.0sigma dir=fade hold=30m | negative pre-2023 | 1347 | -14.4 | -38.8 | -28.5 | 24.4 | -0.37 / -0.99 / -0.73 | 53.2 / 28.8 |
| GC 4 1m jump>=5.0sigma dir=fade hold=30m | negative pre-2023 | 5390 | -6.2 | -30.6 | -20.6 | 24.4 | -0.38 / -1.84 / -1.23 | 26.1 / 1.7 |
| GC 5 (diag) 1m jump>=8.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 1438 | 13.5 | -10.8 | -0.5 | 24.4 | 0.69 / -0.55 / -0.02 | 36.9 / 12.5 |
| GC 6 (diag) 1m jump>=4.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 8686 | 5.4 | -18.9 | -9.0 | 24.4 | 0.37 / -1.26 / -0.60 | 37.2 / 12.9 |
| GC 7 (diag) 1m jump>=8.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 1309 | 11.4 | -12.9 | -2.6 | 24.4 | 0.24 / -0.25 / -0.04 | 25.7 / 1.3 |
| CL 1 1m jump>=5.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 5580 | 6.3 | -18.0 | -15.2 | 24.4 | 0.37 / -1.04 / -0.88 | 44.7 / 20.3 |
| CL 2 (diag) 1m jump>=8.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 1247 | 11.4 | -13.0 | -9.8 | 24.4 | 0.26 / -0.30 / -0.23 | 40.4 / 16.1 |
| CL 3 (diag) 1m jump>=6.0sigma dir=follow hold=60m | gross-positive, cost-negative pre-2023 | 3205 | 10.6 | -13.8 | -10.8 | 24.4 | 0.41 / -0.54 / -0.42 | 26.6 / 2.2 |
| CL 4 (diag) 1m jump>=8.0sigma dir=follow hold=3m | negative pre-2023 | 1382 | -3.7 | -28.1 | -24.7 | 24.4 | -0.20 / -1.51 / -1.33 | 18.3 / -6.1 |
| ZN 1 (diag) 1m jump>=8.0sigma dir=fade hold=30m | gross-positive, cost-negative pre-2023 | 290 | 3.6 | -32.0 | -36.6 | 35.6 | 0.11 / -0.94 / -1.07 | 12.7 / -22.9 |
| ZN 2 (diag) 1m jump>=8.0sigma dir=follow hold=60m | negative pre-2023 | 288 | -13.2 | -48.8 | -53.4 | 35.6 | -0.33 / -1.17 / -1.27 | 19.1 / -16.5 |
| ZN 3 (diag) 1m jump>=6.0sigma dir=fade hold=30m | gross-positive, cost-negative pre-2023 | 810 | 4.0 | -31.6 | -36.4 | 35.6 | 0.23 / -1.80 / -2.07 | 14.4 / -21.2 |
| BTC 1 1m jump>=6.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 247 | 37.6 | -16.8 | 16.3 | 54.4 | 0.61 / -0.27 / 0.27 | 250.2 / 195.9 |
| BTC 2 1m jump>=5.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 423 | 14.8 | -39.5 | -7.2 | 54.4 | 0.37 / -0.98 / -0.18 | 190.5 / 136.1 |
| BTC 3 1m jump>=5.0sigma dir=fade hold=10m | gross-positive, cost-negative pre-2023 | 388 | 5.5 | -48.9 | -16.7 | 54.4 | 0.08 / -0.74 / -0.26 | 159.1 / 104.7 |
| BTC 4 1m jump>=4.0sigma dir=follow hold=60m | positive pre-2023 | 573 | 99.6 | 45.2 | 77.2 | 54.4 | 1.34 / 0.61 / 1.04 | 154.3 / 99.9 |
| BTC 5 1m jump>=6.0sigma dir=follow hold=60m | negative pre-2023 | 203 | -56.4 | -110.8 | -77.8 | 54.4 | -0.41 / -0.80 / -0.56 | 208.1 / 153.7 |
| BTC 6 1m jump>=6.0sigma dir=fade hold=10m | gross-positive, cost-negative pre-2023 | 228 | 24.7 | -29.7 | 3.2 | 54.4 | 0.28 / -0.34 / 0.04 | 164.1 / 109.7 |
| BTC 7 1m jump>=5.0sigma dir=fade hold=30m | negative pre-2023 | 354 | -47.8 | -102.2 | -70.1 | 54.4 | -0.67 / -1.41 / -0.97 | 85.0 / 30.7 |
| BTC 8 (diag) 1m jump>=8.0sigma dir=fade hold=3m | gross-positive, cost-negative pre-2023 | 108 | 25.9 | -28.4 | 5.0 | 54.4 | 0.20 / -0.22 / 0.04 | 285.4 / 231.0 |
| BTC 9 (diag) 1m jump>=6.0sigma dir=follow hold=30m | negative pre-2023 | 215 | -61.9 | -116.2 | -83.3 | 54.4 | -0.61 / -1.15 / -0.82 | 123.7 / 69.4 |
| BTC 10 (diag) 1m jump>=4.0sigma dir=follow hold=30m | positive pre-2023 | 618 | 97.3 | 42.9 | 74.8 | 54.4 | 1.67 / 0.74 / 1.29 | 95.5 / 41.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 7 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.01, p(top) = 0.42); CL: 1 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.05, p(top) = 0.01); ES: 1 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.20, p(top) = 0.12); GC: 4 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.00, p(top) = 0.11); NQ: 4 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.10, p(top) = 0.04); RTY: 1 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.28, p(top) = 0.28); YM: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 18 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (CL 1m jump>=5.0sigma dir=follow hold=60m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10, 'negative pre-2023': 5, 'positive pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_27.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw27/ (`SW27_CO_all_selected_scored.csv`).

DONE SW27
