# REPORT B1 - ST / HM / WT signals at 5/10/15/30-minute bars with ATR-trail exits on ES, RTY, GC, CL, ZN, BTC, ETH

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 32 selected cells (+14 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.99.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: ES, RTY, GC, CL, ZN, BTC, ETH. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection: ES/GC/CL/ZN 2013-2022 (>=7 of 10 calendar years with positive weekly Sharpe, >=300 trades); RTY 2018-2022 (>=4 of 5, >=150 trades); BTC/ETH 2022-01..2023-07 (>=2 of 3 half-year blocks, >=100 trades; low power). Top 10 per instrument; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). Clean 2023-08..2025-07, H1 2025-08-01..2026-02-06, H2 2026-02-07..2026-10-13 read once after selection. Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Selection and the false-survivor test (200 timing-destroyed replicates of the whole grid per instrument)
| sym   |   cells |   eligible |   passing |   best_sel_sharpe |   max_yrs_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|------------------:|--------------:|-----------:|-------------:|
| BTC   |     180 |        180 |        93 |             1.686 |             3 |         10 |            0 |
| CL    |     180 |        180 |         3 |             0.668 |             8 |          3 |            3 |
| ES    |     180 |        180 |         0 |             0.234 |             6 |          0 |            3 |
| ETH   |     180 |        180 |        66 |             1.574 |             3 |         10 |            0 |
| GC    |     180 |        180 |         1 |             0.512 |             7 |          1 |            3 |
| RTY   |     180 |        180 |         8 |             0.785 |             4 |          8 |            2 |
| ZN    |     180 |        180 |         0 |            -1.356 |             1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.115 |           0.115 |  nan     |     nan     |                0.115 |
| RTY   |     200 |                    8 |            2.335 |               8 |      0.005 |                       0.632 |            0.419 |           0.736 |    0.11  |       0.785 |                1.04  |
| GC    |     200 |                    1 |            0.17  |               2 |      0.155 |                       0.512 |            0.15  |           0.369 |    0     |       0.512 |                0.413 |
| CL    |     200 |                    3 |            0.17  |               3 |      0.005 |                       0.383 |            0.199 |           0.388 |    0.02  |       0.668 |                0.481 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     200 |                   93 |           55.86  |              73 |      0     |                       1.357 |            1.116 |           1.376 |    0.055 |       1.686 |                2.189 |
| ETH   |     200 |                   66 |           33.14  |              44 |      0     |                       1.057 |            0.779 |           1.013 |    0.04  |       1.574 |                1.923 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the selection span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades sel. span | blocks pos | Sharpe sel. span | Sharpe full history | pair-window all-in Sharpe | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 1493 | 5 | 0.23 | -0.01 | -1.00 | -0.03 / -0.05 / -0.15 | -0.07 | -0.07 | 0.09 | -0.10 | 0.00 | 534 | diag |
| ES 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 1393 | 5 | -0.02 | -0.07 | -0.27 | -0.03 / -0.02 / -0.01 | -0.03 | -0.45 | 0.46 | -0.06 | 0.00 | 480 | diag |
| ES 3 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 1759 | 6 | -0.09 | -0.34 | -1.36 | -0.04 / -0.14 / -0.16 | -0.10 | -0.07 | 0.02 | -0.13 | 0.00 | 611 | diag |
| RTY 1 | 30m WT[14, 2.0, 100] exit=ATRtrail2.0 | 1464 | 4 | 0.79 | 0.21 | -0.43 | -0.02 / -0.07 / -0.15 | -0.08 | -0.06 | 0.45 | -0.13 | 0.00 | 971 | NO |
| RTY 2 | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 1393 | 4 | 0.75 | 0.59 | 0.28 | 0.00 / 0.12 / -0.07 | -0.02 | -0.15 | 0.96 | -0.05 | 0.00 | 924 | NO |
| RTY 3 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 844 | 4 | 0.71 | -0.08 | -1.07 | -0.06 / 0.06 / -0.13 | -0.07 | 0.24 | 0.06 | -0.11 | 0.00 | 585 | NO |
| RTY 4 | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 971 | 4 | 0.60 | -0.11 | -1.04 | -0.05 / 0.06 / -0.16 | -0.07 | 0.21 | 0.09 | -0.11 | 0.00 | 675 | NO |
| RTY 5 | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 1261 | 4 | 0.59 | 0.47 | 0.48 | 0.02 / 0.02 / -0.01 | 0.00 | 0.02 | 0.95 | -0.04 | 0.00 | 829 | NO |
| RTY 6 | 30m WT[20, 2.0, 100] exit=ATRtrail2.0 | 1487 | 4 | 0.58 | 0.11 | -0.63 | -0.03 / -0.14 / -0.16 | -0.10 | 0.03 | 0.38 | -0.15 | 0.00 | 952 | NO |
| RTY 7 | 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | 975 | 4 | 0.57 | -0.12 | -0.93 | -0.01 / -0.08 / -0.17 | -0.08 | 0.33 | 0.21 | -0.12 | 0.00 | 681 | NO |
| RTY 8 | 15m HM[20, 55, 200] exit=ATRtrail3.0 | 1399 | 4 | 0.47 | 0.10 | -0.81 | -0.02 / -0.08 / -0.18 | -0.09 | 0.28 | 0.34 | -0.12 | 0.00 | 912 | NO |
| RTY 9 (diag) | 30m WT[14, 2.0, 100] exit=ATRtrail3.0 | 1349 | 3 | 0.66 | 0.01 | -1.11 | -0.07 / -0.01 / -0.14 | -0.10 | -0.17 | 0.06 | -0.14 | 0.00 | 874 | diag |
| RTY 10 (diag) | 30m WT[20, 2.0, 100] exit=ATRtrail3.0 | 1379 | 3 | 0.64 | 0.00 | -1.14 | -0.06 / -0.06 / -0.14 | -0.10 | -0.04 | 0.07 | -0.14 | 0.00 | 863 | diag |
| GC 1 | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 1489 | 7 | 0.51 | 0.37 | 0.19 | -0.03 / 0.17 / -0.01 | -0.00 | 0.37 | 0.65 | -0.04 | 0.33 | 481 | NO |
| GC 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 1568 | 5 | 0.06 | -0.02 | -0.16 | -0.04 / 0.09 / 0.01 | -0.02 | 0.22 | 0.48 | -0.06 | 0.00 | 510 | diag |
| GC 3 (diag) | 30m HM[20, 55, 200] exit=ADRtrail0.2 | 1583 | 3 | -0.04 | -0.17 | -0.47 | -0.07 / 0.07 / 0.02 | -0.05 | 0.12 | 0.26 | -0.08 | 0.00 | 518 | diag |
| GC 4 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 2449 | 4 | -0.13 | 0.16 | 1.29 | 0.09 / 0.13 / 0.00 | 0.06 | 0.60 | 1.00 | 0.02 | 0.17 | 800 | diag |
| CL 1 | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 1372 | 7 | 0.67 | 0.67 | 0.78 | 0.03 / -0.07 / 0.08 | 0.02 | 0.20 | 0.99 | -0.01 | 0.33 | 467 | NO |
| CL 2 | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 2506 | 8 | 0.44 | 0.01 | -1.16 | -0.04 / -0.22 / -0.02 | -0.09 | -0.36 | 0.16 | -0.12 | 0.00 | 841 | NO |
| CL 3 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 1521 | 7 | 0.04 | 0.04 | 0.13 | 0.03 / -0.19 / 0.09 | -0.00 | -0.13 | 0.80 | -0.03 | 0.67 | 547 | NO |
| CL 4 (diag) | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 1434 | 6 | 0.41 | 0.28 | -0.12 | -0.02 / -0.08 / 0.06 | -0.03 | 0.15 | 0.81 | -0.05 | 0.00 | 492 | diag |
| CL 5 (diag) | 15m HM[20, 55, 200] exit=ATRtrail3.0 | 2811 | 6 | 0.24 | 0.02 | -0.96 | -0.08 / -0.09 / 0.01 | -0.11 | -0.50 | 0.36 | -0.12 | 0.00 | 944 | diag |
| CL 6 (diag) | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 2813 | 5 | 0.18 | -0.13 | -1.14 | -0.08 / -0.17 / 0.03 | -0.12 | 0.06 | 0.40 | -0.12 | 0.00 | 937 | diag |
| ZN 1 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 1391 | 1 | -1.36 | -1.58 | -2.29 | -0.08 / -0.15 / -0.11 | -0.19 | 0.31 | 0.41 | -0.14 | 0.00 | 447 | diag |
| ZN 2 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 1448 | 1 | -1.48 | -1.57 | -2.00 | -0.07 / -0.19 / -0.08 | -0.18 | 0.45 | 0.62 | -0.14 | 0.00 | 444 | diag |
| ZN 3 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 1656 | 1 | -1.66 | -1.74 | -2.38 | -0.09 / -0.33 / -0.10 | -0.23 | 0.39 | 0.42 | -0.18 | 0.00 | 542 | diag |
| BTC 1 | 10m WT[20, 3.0, 100] exit=ADRtrail0.15 | 743 | 3 | 1.69 | 1.38 | 1.24 | 0.07 / 0.44 / 0.09 | 0.06 | -0.03 | 1.00 | 0.03 | 0.67 | 1693 | LEAD(gate3-7 fail: plateau 2xslip) |
| BTC 2 | 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | 751 | 2 | 1.52 | 1.84 | 1.99 | 0.19 / 0.31 / 0.15 | 0.13 | -0.31 | 1.00 | 0.10 | 0.67 | 1705 | LEAD(gate3-7 fail: plateau ) |
| BTC 3 | 10m HM[20, 55, 200] exit=ATRtrail3.0 | 503 | 3 | 1.49 | 1.20 | 1.04 | 0.13 / 0.10 / 0.05 | 0.07 | 0.07 | 0.97 | 0.02 | 0.50 | 1191 | NO |
| BTC 4 | 15m ST[14, 2.0, 200] exit=ADRtrail0.2 | 680 | 2 | 1.33 | 0.74 | 0.46 | 0.05 / 0.18 / -0.13 | -0.02 | 0.17 | 0.83 | -0.07 | 0.67 | 1541 | NO |
| BTC 5 | 30m HM[9, 21, 200] exit=ADRtrail0.1 | 372 | 3 | 1.32 | 0.32 | -0.17 | -0.06 / 0.24 / -0.08 | -0.07 | 0.11 | 0.54 | -0.11 | 0.00 | 945 | NO |
| BTC 6 | 10m WT[20, 3.0, 100] exit=ADRtrail0.2 | 686 | 3 | 1.31 | 1.25 | 1.22 | 0.11 / 0.47 / -0.03 | 0.08 | -0.05 | 0.98 | 0.04 | 0.67 | 1570 | NO |
| BTC 7 | 10m HM[20, 55, 200] exit=ADRtrail0.15 | 523 | 2 | 1.27 | 0.85 | 0.65 | 0.11 / 0.01 / -0.00 | 0.02 | -0.06 | 0.95 | -0.02 | 0.83 | 1248 | NO |
| BTC 8 | 5m HM[20, 55, 200] exit=ATRtrail3.0 | 979 | 2 | 1.27 | 0.52 | 0.19 | 0.06 / -0.05 / -0.09 | -0.09 | -0.22 | 0.83 | -0.11 | 0.67 | 2224 | NO |
| BTC 9 | 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | 708 | 2 | 1.21 | 0.92 | 0.78 | 0.07 / 0.26 / -0.06 | 0.02 | 0.13 | 0.97 | -0.03 | 0.83 | 1584 | NO |
| BTC 10 | 30m HM[20, 55, 200] exit=ADRtrail0.15 | 209 | 2 | 1.16 | 0.23 | -0.28 | -0.05 / 0.11 / -0.01 | -0.04 | 0.21 | 0.46 | -0.07 | 0.00 | 503 | NO |
| ETH 1 | 5m HM[20, 55, 200] exit=ADRtrail0.15 | 863 | 3 | 1.57 | 0.14 | -0.52 | -0.08 / 0.12 / -0.16 | -0.22 | -0.27 | 0.54 | -0.18 | 0.00 | 2086 | NO |
| ETH 2 | 5m HM[20, 55, 200] exit=ADRtrail0.1 | 950 | 2 | 1.25 | -0.54 | -1.45 | -0.16 / -0.11 / -0.25 | -0.42 | -0.22 | 0.42 | -0.30 | 0.00 | 2332 | NO |
| ETH 3 | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 205 | 3 | 1.21 | 0.83 | 0.67 | 0.07 / -0.02 / -0.10 | -0.00 | -0.15 | 0.88 | -0.03 | 0.50 | 497 | NO |
| ETH 4 | 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | 205 | 3 | 1.05 | 0.41 | 0.09 | 0.03 / -0.05 / -0.12 | -0.04 | -0.26 | 0.72 | -0.06 | 0.00 | 497 | NO |
| ETH 5 | 10m HM[9, 21, 200] exit=ATRtrail3.0 | 779 | 3 | 1.01 | 0.44 | 0.21 | 0.02 / 0.11 / 0.01 | -0.09 | -0.35 | 0.78 | -0.09 | 0.33 | 1830 | NO |
| ETH 6 | 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | 464 | 2 | 1.01 | 0.83 | 0.76 | 0.07 / 0.20 / -0.17 | -0.03 | -0.13 | 0.98 | -0.04 | 0.50 | 1074 | NO |
| ETH 7 | 10m HM[20, 55, 200] exit=ATRtrail3.0 | 473 | 2 | 0.91 | 0.15 | -0.25 | 0.00 / -0.12 / -0.07 | -0.10 | -0.07 | 0.48 | -0.11 | 0.00 | 1139 | NO |
| ETH 8 | 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | 205 | 3 | 0.86 | 0.11 | -0.30 | 0.00 / -0.04 / -0.13 | -0.07 | 0.32 | 0.48 | -0.08 | 0.00 | 497 | NO |
| ETH 9 | 5m HM[20, 55, 200] exit=ADRtrail0.2 | 768 | 2 | 0.86 | 0.02 | -0.33 | -0.03 / 0.07 / -0.12 | -0.14 | -0.64 | 0.43 | -0.13 | 0.00 | 1837 | NO |
| ETH 10 | 10m HM[9, 21, 200] exit=ADRtrail0.15 | 833 | 2 | 0.85 | -0.02 | -0.39 | -0.05 / 0.05 / -0.14 | -0.20 | -0.35 | 0.65 | -0.16 | 0.00 | 1991 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 32 |
| diagnostic cells read | 14 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 17 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 11 |
| worst-decile corr <= +0.30 | 39 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 5 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | clean | 2.03 | 3.73 | -52364 | -45750 | 167732 | -65919 | 5.37 | 43.8 | 1.65 | -79345 | 301602 | -84510 |
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | H1 | 1.98 | 3.61 | -55531 | -43850 | 102528 | -63335 | 2.27 | 42.9 | 3.14 | -68116 | 148564 | -68310 |
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | H2 | 1.82 | 3.64 | -39704 | -29670 | 103975 | -57577 | 2.21 | 41.7 | 2.45 | -78960 | 209135 | -79683 |
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | all | 1.99 | 3.68 | -53647 | -44065 | 167732 | -65919 | 8.13 | 42.9 | 2.05 | -78950 | 301602 | -84510 |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | clean | 0.50 | 0.82 | -23983 | -20408 | 175889 | -36520 | 0.59 | 48.6 | 1.49 | -79427 | 256697 | -80735 |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | H1 | -0.12 | -0.21 | -18548 | -17736 | 61302 | -19012 | -0.11 | 57.1 | 2.76 | -79131 | 155952 | -82090 |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | H2 | 2.48 | 5.51 | -19373 | -14810 | 31782 | -21508 | 5.08 | 38.9 | 2.37 | -83066 | 217270 | -85972 |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | all | 0.78 | 1.36 | -22500 | -19560 | 175889 | -36520 | 1.47 | 48.2 | 1.89 | -80531 | 256697 | -85972 |
| ES 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | -0.52 | -0.76 | -23701 | -20242 | 177084 | -28344 | -0.54 | 52.4 | 1.43 | -80675 | 282512 | -85482 |
| ES 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -0.31 | -0.47 | -19192 | -17597 | 51508 | -22262 | -0.28 | 50.0 | 2.80 | -78540 | 157553 | -79130 |
| ES 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | 0.39 | 0.66 | -24964 | -20584 | 59474 | -29582 | 0.47 | 58.3 | 2.29 | -79238 | 217396 | -80095 |
| ES 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -0.27 | -0.41 | -23884 | -20228 | 216270 | -29582 | -0.38 | 53.6 | 1.83 | -80218 | 282512 | -85482 |
| ETH 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | clean | 1.33 | 2.46 | -34390 | -30023 | 96595 | -42151 | 4.62 | 46.7 | 1.53 | -81698 | 288329 | -86753 |
| ETH 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | H1 | 2.54 | 5.84 | -28296 | -26054 | 52498 | -31591 | 4.45 | 35.7 | 3.02 | -69340 | 146251 | -72388 |
| ETH 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | H2 | -1.53 | -2.04 | -48384 | -44714 | 426277 | -51459 | -0.55 | 61.1 | 2.12 | -80909 | 232957 | -82891 |
| ETH 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | all | 0.76 | 1.28 | -40838 | -36530 | 426277 | -51459 | 1.05 | 48.2 | 1.89 | -81127 | 288329 | -86753 |
| GC 30m HM[20, 55, 200] exit=ATRtrail3.0 | clean | -0.55 | -0.82 | -19442 | -17161 | 191097 | -25734 | -0.50 | 59.0 | 1.43 | -81098 | 273779 | -87021 |
| GC 30m HM[20, 55, 200] exit=ATRtrail3.0 | H1 | 3.25 | 6.83 | -26482 | -20066 | 41972 | -29681 | 4.69 | 32.1 | 3.00 | -74317 | 158614 | -78193 |
| GC 30m HM[20, 55, 200] exit=ATRtrail3.0 | H2 | -0.42 | -0.70 | -31987 | -25632 | 117199 | -34810 | -0.32 | 66.7 | 2.29 | -81543 | 216223 | -84283 |
| GC 30m HM[20, 55, 200] exit=ATRtrail3.0 | all | 0.19 | 0.31 | -24660 | -20466 | 191097 | -34810 | 0.33 | 56.5 | 1.86 | -80980 | 273779 | -87021 |
| RTY 30m HM[9, 21, 200] exit=ATRtrail3.0 | clean | 0.33 | 0.50 | -30519 | -27605 | 198935 | -34441 | 0.43 | 49.5 | 1.48 | -79464 | 275527 | -83173 |
| RTY 30m HM[9, 21, 200] exit=ATRtrail3.0 | H1 | 0.95 | 1.62 | -26023 | -23372 | 87561 | -31315 | 0.72 | 53.6 | 2.84 | -76123 | 154173 | -77864 |
| RTY 30m HM[9, 21, 200] exit=ATRtrail3.0 | H2 | 0.53 | 0.91 | -36832 | -31504 | 118553 | -38047 | 0.47 | 44.4 | 2.29 | -80885 | 214794 | -84087 |
| RTY 30m HM[9, 21, 200] exit=ATRtrail3.0 | all | 0.48 | 0.76 | -32962 | -28558 | 198935 | -38047 | 1.02 | 49.4 | 1.87 | -79602 | 275527 | -84087 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | clean | -1.58 | -2.00 | -25924 | -23078 | 314995 | -39769 | -0.98 | 61.9 | 1.39 | -80919 | 287738 | -85565 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H1 | -4.33 | -3.92 | -35954 | -32551 | 242486 | -40446 | -0.96 | 64.3 | 2.64 | -78808 | 153470 | -80331 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H2 | -1.24 | -1.77 | -16095 | -14756 | 92527 | -16746 | -0.72 | 69.4 | 2.21 | -83295 | 219060 | -84696 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | all | -2.00 | -2.37 | -28523 | -24736 | 638473 | -40446 | -0.95 | 64.3 | 1.76 | -81381 | 287738 | -85565 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -30.9 | 22.0 | 27.4 | 28.7 | 21.4 / 25.8 | 28.4 / 28.2 | NO |
| RTY 30m HM[9, 21, 200] exit=ATRtrail3.0 | -27.7 | 24.0 | 28.4 | 32.5 | 23.4 / 27.5 | 29.4 / 32.9 | NO |
| GC 30m HM[20, 55, 200] exit=ATRtrail3.0 | -29.3 | 21.2 | 26.1 | 33.4 | 20.6 / 24.9 | 30.2 / 36.4 | NO |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | -27.1 | 23.7 | 27.1 | 42.5 | 27.5 / 28.1 | 22.7 / 27.1 | NO |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | -36.8 | 23.8 | 25.7 | 25.9 | 23.2 / 25.8 | 24.7 / 27.7 | NO |
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | -14.8 | 17.1 | 28.8 | 18.5 | 16.5 / 26.9 | 48.5 / 48.3 | NO |
| ETH 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | -25.0 | 19.7 | 25.2 | 25.6 | 19.1 / 23.8 | 41.3 / 46.0 | NO |

INSURANCE count: 0.

## 6. What this says
- **Equity/rates/energy/metals: nothing.** ES (0 of 180 cells pass the year rule, best selection Sharpe +0.23), ZN (best -1.36), GC (1 cell, uplift -0.03/+0.17/-0.01), CL (3 cells, H1 uplifts -0.07/-0.22/-0.19) and RTY (8 cells with selection Sharpe up to 0.79 but pair-window Sharpe mostly negative and H2 uplifts -0.01 to -0.18) add nothing; no cell has +0.10 on clean, H1 and H2. The live NQ signals at 5-30 minutes with equal-R trails earn nothing after cost on the other contracts: on ES the median selection-span Sharpe by bar size is -5.3 (5m), -3.7 (10m), -2.8 (15m), -1.7 (30m) and the best cell of each is -2.5, -1.3, -0.7, +0.23: cost falls with the bar size but never turns positive. The NQ edge is not a generic ST/HM/WT property.
- **CME crypto (BTC, ETH): one lead.** BTC has only 2022-01 onward, so selection used 2022-01..2023-07 (3 half-year blocks, 1.6 years, low power) and 93 of 180 cells passed (replicates pass 56 on average: the rule is almost uninformative there; top-10 mean selection Sharpe 1.36 against a replicate p95 of 1.38, p = 0.055). Read once on the pair window, the rank-2 cell, **BTC 10-minute WT (ATR 20, mult 3.0, EMA 100), ATR(14) x3 trail**, earns a pair-window standalone Sharpe of 1.99 (clean 2.03 / H1 1.98 / H2 1.82; selection span 1.52), adds +0.19 / +0.31 / +0.15 to the pair's weekly Sharpe on clean / H1 / H2 at 20% share (+0.10/+0.16/+0.08 at 10%, +0.27/+0.46/+0.22 at 30%, +0.43/+0.72/+0.35 at 50%), bootstrap 90% lower bound +0.10 at 20%, worst-decile correlation -0.31 (17 weeks), standalone above its own random-entry null (p95 0.96), all-in uplift at 2x slippage +0.13, worst week within the share (+2.4% at 20%). It fails exactly one gate: the plateau, 0.67 of +-25% neighbours keep >= 75% of the uplift (needs 0.75). Its ADR-trail sibling (rank 1) passes the uplift gate only at 30% and 50%, plateau 0.67, 2x-slippage uplift +0.06. Everything else on BTC and all ETH cells fail the uplift gate on at least one span.
- **Why this stays a LEAD and not a FIND:** (1) plateau gate failed (0.67 < 0.75) - not softened; (2) the selection history is 1.6 years and the 'full history' Sharpe for BTC is just selection plus pair window (BTC futures start 2022-01), so there is no independent long-history confirmation; the false-survivor top-10 test is at the margin (p = 0.055); (3) the sleeve is a BTC trend sleeve in a window (2023-08..2026) in which BTC trended strongly; a BTC regime change would end it. It is a candidate for a pre-registered out-of-sample continuation (new weekly data, same cell frozen) rather than a find.
- Closest misses used for the follow-up list: BTC/ETH on the other B families (B4/B7/B10/B11 cells on crypto), BTC WT plateau neighbourhood at 5/15-min, and the 30-minute ATR-trail cells on RTY/GC/CL (selection Sharpe 0.5-0.8, flat in the pair window).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b1.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b1/ (`B1_all_selected_scored.csv`).

DONE B1
