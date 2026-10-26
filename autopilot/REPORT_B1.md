# REPORT B1 - ST / HM / WT signals at 5/10/15/30-minute bars with ATR-trail exits on ES, RTY, GC, CL, ZN, BTC, ETH

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 56 selected cells (+9 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.99.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: ES, RTY, GC, CL, ZN, BTC, ETH, YM. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     180 |        180 |       113 |               2.397 |                2 |         10 |            0 |
| CL    |     180 |        180 |         3 |               0.606 |                2 |          3 |            3 |
| ES    |     180 |        180 |        14 |               1.574 |                2 |         10 |            0 |
| ETH   |     180 |        180 |        89 |               2.225 |                2 |         10 |            0 |
| GC    |     180 |        180 |        17 |               1.279 |                2 |         10 |            0 |
| RTY   |     180 |        180 |         3 |               0.652 |                2 |          3 |            3 |
| YM    |     180 |        180 |        20 |               2.186 |                2 |         10 |            0 |
| ZN    |     180 |        180 |         0 |              -1.579 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   14 |            5.34  |              13 |      0     |                       0.998 |            0.617 |           0.915 |    0.02  |       1.574 |                1.594 |
| RTY   |     200 |                    3 |            4.75  |              15 |      0.835 |                       0.297 |            0.555 |           0.857 |    0.955 |       0.652 |                1.488 |
| GC    |     200 |                   17 |            7.33  |              14 |      0     |                       0.83  |            0.626 |           0.876 |    0.09  |       1.279 |                1.609 |
| CL    |     200 |                    3 |            2.06  |               6 |      0.33  |                       0.561 |            0.54  |           1.002 |    0.395 |       0.606 |                1.273 |
| ZN    |     200 |                    0 |            0.005 |               1 |      1     |                     nan     |            0.108 |           0.108 |  nan     |     nan     |                0.108 |
| BTC   |     200 |                  113 |           36.1   |              50 |      0     |                       2.073 |            1.259 |           1.483 |    0     |       2.397 |                2.245 |
| ETH   |     200 |                   89 |           24.525 |              33 |      0     |                       1.926 |            1.123 |           1.373 |    0     |       2.225 |                2.348 |
| YM    |     200 |                   20 |            9.93  |              17 |      0     |                       1.359 |            0.652 |           0.862 |    0     |       2.186 |                1.679 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | 572 | 2 | 1.57 | -1.72 | 0.93 | -0.15 / 0.75 | 0.09 / -0.13 / 0.02 | -0.01 | -0.10 | 1.00 | -0.02 | 0.17 | 948 | NO |
| ES 2 | 30m WT[20, 2.0, 100] exit=ATRtrail2.0 | 579 | 2 | 1.21 | -1.02 | 0.22 | -1.57 / 0.95 | 0.05 / -0.10 / -0.15 | -0.06 | 0.05 | 0.97 | -0.07 | 0.00 | 954 | NO |
| ES 3 | 30m WT[14, 2.0, 100] exit=ADRtrail0.2 | 569 | 2 | 1.18 | -1.53 | 0.88 | 0.38 / 0.77 | 0.06 / -0.08 / 0.03 | -0.01 | 0.14 | 0.98 | -0.03 | 0.17 | 943 | NO |
| ES 4 | 30m WT[14, 2.0, 100] exit=ATRtrail2.0 | 572 | 2 | 1.07 | -1.01 | 0.35 | -0.95 / 0.54 | 0.04 / -0.06 / -0.10 | -0.05 | 0.17 | 0.97 | -0.06 | 0.00 | 946 | NO |
| ES 5 | 30m ST[14, 2.0, 200] exit=ADRtrail0.2 | 535 | 2 | 1.04 | -1.49 | 0.88 | 0.59 / 0.67 | 0.06 / 0.02 / -0.00 | -0.01 | -0.07 | 1.00 | -0.03 | 0.33 | 886 | NO |
| ES 6 | 30m ST[14, 2.0, 200] exit=ATRtrail2.0 | 535 | 2 | 1.03 | -0.98 | 0.48 | -0.47 / 0.65 | 0.04 / 0.08 / -0.14 | -0.04 | -0.12 | 0.95 | -0.06 | 0.00 | 884 | NO |
| ES 7 | 15m HM[20, 55, 200] exit=ADRtrail0.2 | 558 | 2 | 0.83 | -1.18 | 0.75 | 0.65 / 0.41 | 0.04 / -0.09 / 0.05 | -0.01 | -0.16 | 0.99 | -0.03 | 0.00 | 925 | NO |
| ES 8 | 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | 976 | 2 | 0.77 | -2.52 | -0.13 | -1.33 / 0.08 | 0.05 / -0.13 / -0.22 | -0.11 | 0.08 | 0.91 | -0.12 | 0.00 | 1600 | NO |
| ES 9 | 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | 953 | 2 | 0.68 | -2.57 | 0.01 | -0.87 / 0.67 | 0.05 / -0.15 / -0.13 | -0.10 | 0.08 | 0.84 | -0.10 | 0.00 | 1567 | NO |
| ES 10 | 15m ST[14, 2.0, 200] exit=ADRtrail0.2 | 931 | 2 | 0.60 | -2.43 | 0.17 | -0.43 / 0.71 | 0.04 / -0.04 / -0.10 | -0.08 | -0.06 | 0.95 | -0.08 | 0.33 | 1537 | NO |
| RTY 1 | 30m HM[9, 21, 200] exit=ADRtrail0.15 | 583 | 2 | 0.65 | 0.01 | 0.65 | 0.78 / 0.62 | 0.03 / 0.14 / -0.07 | -0.01 | 0.30 | 1.00 | -0.04 | 0.17 | 953 | NO |
| RTY 2 | 15m HM[3, 6, 20] exit=ATRtrail3.0 | 1602 | 2 | 0.15 | -0.75 | -0.28 | -0.84 / 0.51 | -0.04 / 0.04 / -0.27 | -0.15 | 0.08 | 0.85 | -0.19 | 0.00 | 2588 | NO |
| RTY 3 | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 303 | 2 | 0.09 | 0.54 | -0.25 | -0.86 / 0.87 | 0.00 / -0.05 / -0.10 | -0.04 | 0.13 | 0.61 | -0.07 | 0.00 | 503 | NO |
| RTY 4 (diag) | 30m HM[9, 21, 200] exit=ADRtrail0.2 | 565 | 1 | 0.41 | 0.22 | 0.21 | 0.08 / 1.20 | 0.02 / 0.10 / -0.13 | -0.03 | 0.02 | 0.91 | -0.06 | 0.33 | 923 | diag |
| RTY 5 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 520 | 1 | 0.36 | 0.45 | 0.48 | 0.69 / 1.17 | 0.02 / 0.02 / -0.01 | 0.00 | 0.02 | 0.95 | -0.04 | 0.00 | 829 | diag |
| RTY 6 (diag) | 30m ST[4, 2.0, 20] exit=ATRtrail2.0 | 980 | 1 | 0.35 | -0.45 | -0.18 | -1.18 / 0.61 | 0.01 / 0.10 / -0.27 | -0.09 | 0.35 | 0.73 | -0.13 | 0.00 | 1566 | diag |
| GC 1 | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 500 | 2 | 1.28 | -0.20 | 1.29 | 1.15 / 1.51 | 0.09 / 0.13 / 0.00 | 0.06 | 0.60 | 1.00 | 0.02 | 0.17 | 800 | NO |
| GC 2 | 10m HM[20, 55, 200] exit=ADRtrail0.2 | 838 | 2 | 1.01 | -0.53 | 0.28 | -1.01 / 1.17 | 0.08 / -0.04 / -0.09 | -0.02 | -0.01 | 0.85 | -0.06 | 0.50 | 1328 | NO |
| GC 3 | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 565 | 2 | 0.96 | -0.69 | 0.93 | 0.76 / 1.30 | 0.07 / 0.10 / 0.00 | 0.04 | 0.31 | 1.00 | -0.01 | 0.17 | 916 | NO |
| GC 4 | 5m HM[20, 55, 200] exit=ADRtrail0.2 | 1321 | 2 | 0.92 | -0.46 | 0.68 | 0.45 / 1.25 | 0.06 / 0.04 / 0.03 | -0.02 | 0.06 | 0.99 | -0.05 | 0.50 | 2106 | NO |
| GC 5 | 30m HM[9, 21, 200] exit=ADRtrail0.15 | 605 | 2 | 0.89 | -1.09 | 0.55 | -0.13 / 1.42 | 0.08 / 0.00 / -0.01 | 0.00 | 0.32 | 0.97 | -0.03 | 0.00 | 994 | NO |
| GC 6 | 10m HM[20, 55, 200] exit=ADRtrail0.15 | 904 | 2 | 0.72 | -0.91 | 0.25 | -0.44 / 1.14 | 0.06 / -0.06 / -0.05 | -0.04 | 0.01 | 0.97 | -0.07 | 0.17 | 1432 | NO |
| GC 7 | 30m HM[9, 21, 200] exit=ADRtrail0.2 | 579 | 2 | 0.68 | -0.74 | 0.34 | -0.40 / 1.12 | 0.06 / -0.04 / -0.04 | -0.00 | 0.37 | 0.87 | -0.04 | 0.33 | 943 | NO |
| GC 8 | 10m HM[20, 55, 200] exit=ATRtrail3.0 | 851 | 2 | 0.65 | -0.50 | 0.47 | 0.32 / 0.96 | 0.05 / 0.13 / -0.04 | -0.00 | 0.05 | 0.98 | -0.05 | 0.17 | 1345 | NO |
| GC 9 | 15m WT[20, 2.0, 100] exit=ATRtrail3.0 | 1002 | 2 | 0.63 | -1.01 | 0.65 | 0.84 / 1.23 | 0.04 / 0.07 / 0.09 | 0.01 | 0.20 | 0.99 | -0.03 | 0.00 | 1588 | NO |
| GC 10 | 10m ST[14, 3.0, 200] exit=ADRtrail0.2 | 859 | 2 | 0.56 | -1.11 | 0.13 | -0.37 / 1.29 | 0.03 / -0.26 / 0.10 | -0.04 | 0.06 | 0.77 | -0.09 | 0.67 | 1392 | NO |
| CL 1 | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 372 | 2 | 0.61 | 0.03 | 0.26 | -0.16 / 0.94 | 0.03 / -0.15 / 0.09 | -0.01 | -0.02 | 0.93 | -0.03 | 0.50 | 613 | NO |
| CL 2 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 339 | 2 | 0.60 | 0.02 | 0.13 | -0.44 / 0.67 | 0.03 / -0.19 / 0.09 | -0.00 | -0.13 | 0.83 | -0.03 | 0.67 | 547 | NO |
| CL 3 | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 279 | 2 | 0.48 | 0.63 | 0.78 | 1.26 / 0.72 | 0.03 / -0.07 / 0.08 | 0.02 | 0.20 | 1.00 | -0.01 | 0.33 | 467 | NO |
| CL 4 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | 374 | 1 | 0.39 | -0.13 | 0.00 | -0.48 / 0.44 | 0.02 / -0.18 / 0.05 | -0.03 | 0.41 | 0.89 | -0.05 | 0.00 | 617 | diag |
| CL 5 (diag) | 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | 340 | 1 | 0.33 | -0.33 | -0.13 | -0.74 / 0.92 | 0.02 / -0.20 / 0.05 | -0.04 | 0.21 | 0.75 | -0.06 | 0.00 | 549 | diag |
| CL 6 (diag) | 30m WT[20, 3.0, 100] exit=ADRtrail0.2 | 374 | 1 | 0.33 | -0.44 | -0.12 | -0.60 / 0.84 | 0.01 / -0.17 / 0.02 | -0.05 | 0.35 | 0.80 | -0.06 | 0.00 | 617 | diag |
| ZN 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 282 | 0 | -1.58 | -1.44 | -2.00 | -2.69 / -1.06 | -0.07 / -0.19 / -0.08 | -0.18 | 0.45 | 0.64 | -0.14 | 0.00 | 444 | diag |
| ZN 2 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 341 | 0 | -1.60 | -1.54 | -2.38 | -3.66 / -0.88 | -0.09 / -0.33 / -0.10 | -0.23 | 0.39 | 0.43 | -0.18 | 0.00 | 542 | diag |
| ZN 3 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 272 | 0 | -1.85 | -1.37 | -2.29 | -2.77 / -0.66 | -0.08 / -0.15 / -0.11 | -0.19 | 0.31 | 0.30 | -0.14 | 0.00 | 447 | diag |
| BTC 1 | 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | 679 | 2 | 2.40 | 0.18 | 1.67 | 0.27 / 1.49 | 0.19 / 0.24 / -0.12 | 0.11 | 0.01 | 1.00 | 0.06 | 0.50 | 1083 | NO |
| BTC 2 | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 748 | 2 | 2.36 | 0.18 | 1.38 | 0.31 / 1.36 | 0.13 / 0.23 / -0.17 | 0.06 | -0.02 | 0.98 | 0.02 | 0.17 | 1185 | NO |
| BTC 3 | 15m ST[8, 2.0, 20] exit=ATRtrail3.0 | 1265 | 2 | 2.16 | 0.63 | 1.29 | -0.08 / 1.22 | 0.22 / 0.30 / -0.18 | 0.10 | 0.40 | 1.00 | 0.05 | 0.33 | 2036 | NO |
| BTC 4 | 5m ST[14, 3.0, 200] exit=ADRtrail0.2 | 1498 | 2 | 2.05 | 0.09 | 1.50 | 0.66 / 1.22 | 0.19 / 0.51 / -0.01 | 0.10 | -0.06 | 1.00 | 0.06 | 0.67 | 2391 | NO |
| BTC 5 | 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | 687 | 2 | 2.05 | -0.73 | 1.21 | -0.49 / 1.28 | 0.18 / 0.09 / -0.06 | 0.07 | 0.00 | 0.99 | 0.03 | 0.67 | 1091 | NO |
| BTC 6 | 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | 1060 | 2 | 2.02 | 1.52 | 1.99 | 1.90 / 1.09 | 0.19 / 0.31 / 0.15 | 0.13 | -0.31 | 1.00 | 0.10 | 0.67 | 1705 | LEAD(gate3-7 fail: plateau ) |
| BTC 7 | 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | 667 | 2 | 2.01 | -0.45 | 1.15 | -0.55 / 1.27 | 0.17 / 0.24 / -0.17 | 0.07 | 0.27 | 0.98 | 0.03 | 0.67 | 1065 | NO |
| BTC 8 | 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | 686 | 2 | 1.95 | -0.43 | 1.19 | -0.25 / 1.27 | 0.17 / 0.12 / -0.07 | 0.07 | 0.04 | 1.00 | 0.02 | 0.83 | 1089 | NO |
| BTC 9 | 5m ST[24, 2.0, 40] exit=ADRtrail0.2 | 2214 | 2 | 1.88 | -0.36 | 1.07 | -0.02 / 1.22 | 0.19 / 0.31 / -0.12 | 0.02 | 0.29 | 0.97 | 0.00 | 0.33 | 3456 | NO |
| BTC 10 | 15m ST[14, 3.0, 200] exit=ATRtrail3.0 | 600 | 2 | 1.86 | -0.15 | 0.76 | -1.39 / 0.87 | 0.12 / 0.05 / -0.14 | 0.03 | -0.07 | 0.95 | -0.01 | 0.67 | 963 | NO |
| ETH 1 | 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | 663 | 2 | 2.22 | 0.60 | 1.25 | -0.17 / 1.01 | 0.16 / 0.08 / -0.15 | 0.00 | 0.16 | 1.00 | -0.00 | 0.50 | 1103 | NO |
| ETH 2 | 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | 653 | 2 | 2.09 | 0.67 | 1.14 | -0.30 / 1.14 | 0.14 / 0.10 / -0.17 | 0.01 | 0.06 | 0.99 | -0.01 | 0.67 | 1090 | NO |
| ETH 3 | 10m HM[3, 6, 20] exit=ADRtrail0.2 | 2430 | 2 | 2.07 | -1.03 | 0.81 | -1.39 / 0.53 | 0.26 / 0.06 / -0.44 | -0.13 | -0.07 | 0.99 | -0.06 | 0.33 | 3877 | NO |
| ETH 4 | 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | 1698 | 2 | 1.97 | 0.01 | 1.10 | -0.16 / 0.46 | 0.23 / 0.46 / -0.25 | -0.05 | -0.18 | 1.00 | 0.02 | 0.00 | 2732 | NO |
| ETH 5 | 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | 932 | 2 | 1.90 | -0.65 | 0.97 | -0.40 / 0.80 | 0.15 / 0.13 / -0.17 | -0.01 | -0.10 | 1.00 | -0.01 | 0.83 | 1528 | NO |
| ETH 6 | 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | 925 | 2 | 1.89 | -0.19 | 0.92 | -0.47 / 0.94 | 0.15 / 0.12 / -0.17 | -0.01 | -0.13 | 1.00 | -0.01 | 0.83 | 1512 | NO |
| ETH 7 | 15m WT[14, 2.0, 100] exit=ATRtrail3.0 | 915 | 2 | 1.83 | -0.08 | 1.05 | -0.08 / 1.02 | 0.14 / 0.15 / -0.13 | 0.00 | -0.15 | 0.96 | 0.00 | 0.50 | 1473 | NO |
| ETH 8 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 312 | 2 | 1.79 | 0.85 | 1.03 | -0.17 / 1.52 | 0.08 / -0.01 / -0.06 | 0.02 | -0.33 | 0.97 | -0.01 | 0.17 | 495 | NO |
| ETH 9 | 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | 666 | 2 | 1.78 | -0.09 | 1.18 | 0.35 / 1.08 | 0.11 / 0.14 / -0.08 | -0.01 | -0.19 | 1.00 | -0.01 | 0.50 | 1106 | NO |
| ETH 10 | 15m WT[14, 2.0, 100] exit=ADRtrail0.15 | 992 | 2 | 1.71 | -0.40 | 1.18 | 0.48 / 0.74 | 0.15 / 0.20 / -0.07 | -0.01 | 0.22 | 1.00 | 0.02 | 0.33 | 1640 | NO |
| YM 1 | 15m HM[20, 55, 200] exit=ATRtrail2.0 | 559 | 2 | 2.19 | -0.63 | 1.13 | -0.43 / 0.98 | 0.15 / -0.09 / 0.01 | 0.05 | -0.11 | 1.00 | 0.02 | 0.00 | 929 | NO |
| YM 2 | 15m HM[20, 55, 200] exit=ADRtrail0.2 | 541 | 2 | 1.71 | -0.44 | 1.29 | 0.57 / 1.15 | 0.12 / -0.04 / 0.08 | 0.06 | -0.10 | 1.00 | 0.02 | 0.17 | 901 | NO |
| YM 3 | 15m HM[20, 55, 200] exit=ADRtrail0.15 | 558 | 2 | 1.63 | -1.10 | 1.42 | 1.10 / 0.88 | 0.10 / 0.01 / 0.10 | 0.05 | -0.35 | 1.00 | 0.03 | 0.33 | 927 | NO |
| YM 4 | 15m HM[20, 55, 200] exit=ADRtrail0.1 | 571 | 2 | 1.31 | -1.87 | 1.08 | 0.55 / 1.06 | 0.10 / -0.13 / 0.10 | 0.02 | -0.40 | 1.00 | -0.00 | 0.17 | 948 | NO |
| YM 5 | 15m HM[20, 55, 200] exit=ATRtrail3.0 | 538 | 2 | 1.26 | -0.39 | 0.83 | 0.20 / 1.34 | 0.06 / -0.11 / 0.08 | 0.02 | -0.35 | 0.98 | -0.02 | 0.17 | 885 | NO |
| YM 6 | 30m HM[20, 55, 200] exit=ADRtrail0.2 | 284 | 2 | 1.26 | 0.29 | 0.49 | -0.77 / 1.60 | 0.05 / -0.00 / -0.10 | -0.01 | 0.03 | 0.88 | -0.04 | 0.17 | 491 | NO |
| YM 7 | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 284 | 2 | 1.22 | 0.61 | 0.10 | -1.72 / 1.57 | 0.04 / -0.12 / -0.08 | -0.02 | -0.23 | 0.68 | -0.06 | 0.00 | 488 | NO |
| YM 8 | 30m WT[20, 2.0, 100] exit=ADRtrail0.1 | 581 | 2 | 1.12 | -1.68 | 0.38 | -0.63 / 0.89 | 0.08 / -0.18 / 0.02 | -0.02 | 0.01 | 0.98 | -0.05 | 0.33 | 952 | NO |
| YM 9 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 342 | 2 | 0.98 | 0.35 | 0.31 | -0.96 / 1.43 | 0.05 / 0.05 / -0.11 | 0.00 | 0.09 | 0.85 | -0.04 | 0.17 | 541 | NO |
| YM 10 | 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | 537 | 2 | 0.92 | -0.34 | -0.12 | -1.91 / 0.95 | 0.04 / -0.05 / -0.10 | -0.02 | -0.07 | 0.54 | -0.07 | 0.00 | 865 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 56 |
| diagnostic cells read | 9 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 50 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 16 |
| standalone pair-window Sharpe above own random-entry null p95 | 44 |
| worst-decile corr <= +0.30 | 54 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 3 |

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
| ES 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | clean | 1.59 | 3.10 | -32967 | -27005 | 122763 | -46807 | 4.06 | 51.4 | 1.55 | -80762 | 284670 | -83310 |
| ES 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | H1 | -1.37 | -1.61 | -48799 | -42335 | 174064 | -66653 | -0.69 | 50.0 | 2.69 | -76428 | 168096 | -84169 |
| ES 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | H2 | 0.89 | 1.33 | -42387 | -32289 | 128811 | -54625 | 0.71 | 41.7 | 2.32 | -83340 | 219528 | -83529 |
| ES 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | all | 0.93 | 1.51 | -39211 | -33244 | 204536 | -66653 | 2.29 | 49.4 | 1.90 | -81713 | 284670 | -84169 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | clean | 1.84 | 3.07 | -70789 | -63503 | 238531 | -78455 | 4.61 | 37.1 | 1.69 | -79516 | 309862 | -90843 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | H1 | 2.12 | 3.83 | -69686 | -56163 | 218214 | -70340 | 1.47 | 32.1 | 3.28 | -72652 | 144097 | -73339 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | H2 | -2.00 | -2.33 | -83842 | -74143 | 502788 | -88377 | -0.74 | 61.1 | 2.04 | -82375 | 219535 | -84088 |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | all | 1.10 | 1.73 | -74044 | -66757 | 502788 | -88377 | 2.08 | 41.7 | 2.00 | -80007 | 309862 | -90843 |
| GC 30m HM[9, 21, 200] exit=ATRtrail3.0 | clean | 1.36 | 2.38 | -35402 | -29221 | 94408 | -54547 | 4.29 | 40.0 | 1.55 | -80371 | 275621 | -86678 |
| GC 30m HM[9, 21, 200] exit=ATRtrail3.0 | H1 | 1.87 | 3.68 | -29569 | -27220 | 105429 | -32466 | 1.46 | 35.7 | 2.96 | -73658 | 164502 | -74531 |
| GC 30m HM[9, 21, 200] exit=ATRtrail3.0 | H2 | 0.38 | 0.61 | -24284 | -20586 | 87327 | -26039 | 0.31 | 52.8 | 2.30 | -82362 | 214210 | -84692 |
| GC 30m HM[9, 21, 200] exit=ATRtrail3.0 | all | 1.29 | 2.28 | -33065 | -27867 | 105429 | -54547 | 5.57 | 41.7 | 1.93 | -80423 | 275621 | -86678 |
| RTY 30m HM[9, 21, 200] exit=ADRtrail0.15 | clean | 0.57 | 0.92 | -35318 | -31411 | 192732 | -46922 | 0.90 | 51.4 | 1.49 | -82319 | 279684 | -86537 |
| RTY 30m HM[9, 21, 200] exit=ADRtrail0.15 | H1 | 2.41 | 5.67 | -27316 | -23426 | 74853 | -33164 | 2.83 | 46.4 | 2.97 | -75521 | 152214 | -77720 |
| RTY 30m HM[9, 21, 200] exit=ADRtrail0.15 | H2 | -0.35 | -0.56 | -40409 | -36727 | 209546 | -45920 | -0.21 | 61.1 | 2.23 | -83397 | 222639 | -86062 |
| RTY 30m HM[9, 21, 200] exit=ADRtrail0.15 | all | 0.65 | 1.10 | -36751 | -32839 | 209546 | -46922 | 1.63 | 52.4 | 1.88 | -82053 | 279684 | -86537 |
| YM 15m HM[20, 55, 200] exit=ADRtrail0.2 | clean | 1.69 | 3.25 | -38361 | -31271 | 92044 | -44162 | 6.27 | 41.0 | 1.58 | -79744 | 250473 | -80588 |
| YM 15m HM[20, 55, 200] exit=ADRtrail0.2 | H1 | -0.45 | -0.60 | -39041 | -35784 | 87478 | -46938 | -0.38 | 50.0 | 2.78 | -76477 | 160856 | -78287 |
| YM 15m HM[20, 55, 200] exit=ADRtrail0.2 | H2 | 1.22 | 2.10 | -43412 | -33591 | 139246 | -50234 | 1.04 | 44.4 | 2.38 | -82130 | 198852 | -83282 |
| YM 15m HM[20, 55, 200] exit=ADRtrail0.2 | all | 1.29 | 2.29 | -40649 | -33269 | 163115 | -50234 | 4.22 | 43.5 | 1.95 | -80151 | 250473 | -83282 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | clean | -1.58 | -2.00 | -25924 | -23078 | 314995 | -39769 | -0.98 | 61.9 | 1.39 | -80919 | 287738 | -85565 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H1 | -4.33 | -3.92 | -35954 | -32551 | 242486 | -40446 | -0.96 | 64.3 | 2.64 | -78808 | 153470 | -80331 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H2 | -1.24 | -1.77 | -16095 | -14756 | 92527 | -16746 | -0.72 | 69.4 | 2.21 | -83295 | 219060 | -84696 |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | all | -2.00 | -2.37 | -28523 | -24736 | 638473 | -40446 | -0.95 | 64.3 | 1.76 | -81381 | 287738 | -85565 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | -24.8 | 22.9 | 24.5 | 27.6 | 22.9 / 24.9 | 18.7 / 27.2 | NO |
| RTY 30m HM[9, 21, 200] exit=ADRtrail0.15 | -26.2 | 17.5 | 24.1 | 30.2 | 16.8 / 22.8 | 29.7 / 34.0 | NO |
| GC 30m HM[9, 21, 200] exit=ATRtrail3.0 | -23.4 | 21.8 | 27.6 | 32.4 | 21.2 / 26.8 | 37.2 / 37.6 | NO |
| CL 30m HM[20, 55, 200] exit=ATRtrail3.0 | -27.1 | 23.7 | 27.1 | 42.5 | 27.5 / 28.1 | 22.7 / 27.1 | NO |
| ZN 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | -36.8 | 23.8 | 25.7 | 25.9 | 23.2 / 25.8 | 24.7 / 27.7 | NO |
| BTC 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | -14.8 | 17.1 | 28.8 | 18.5 | 16.5 / 26.9 | 48.5 / 48.3 | NO |
| ETH 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | -18.3 | 9.6 | 25.9 | 14.1 | 8.9 / 27.8 | 39.5 / 39.6 | NO |
| YM 15m HM[20, 55, 200] exit=ADRtrail0.2 | -22.3 | 25.8 | 27.4 | 34.4 | 27.9 / 27.0 | 30.0 / 32.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 30m WT[20, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 2915 | 51.8 | -985.1 | -417.8 | 1036.9 | 0.10 / -1.72 / -0.75 | 1334.2 / 871.5 |
| ES 2 30m WT[20, 2.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2913 | 250.6 | -572.7 | -122.3 | 823.3 | 0.48 / -1.02 / -0.22 | 1005.9 / 610.9 |
| ES 3 30m WT[14, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 2924 | 158.2 | -882.3 | -312.5 | 1040.5 | 0.29 / -1.53 / -0.56 | 1121.8 / 656.2 |
| ES 4 30m WT[14, 2.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2923 | 274.1 | -561.0 | -104.1 | 835.1 | 0.53 / -1.01 / -0.19 | 968.0 / 565.6 |
| ES 5 30m ST[14, 2.0, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 2721 | 149.3 | -883.8 | -319.5 | 1033.1 | 0.27 / -1.49 / -0.55 | 1059.4 / 597.3 |
| ES 6 30m ST[14, 2.0, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2720 | 265.0 | -560.9 | -110.4 | 825.9 | 0.49 / -0.98 / -0.19 | 947.8 / 545.9 |
| ES 7 15m HM[20, 55, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 3048 | 384.9 | -685.5 | -93.7 | 1070.4 | 0.70 / -1.18 / -0.16 | 962.8 / 497.9 |
| ES 8 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | negative pre-2023 | 5177 | -69.2 | -1108.3 | -538.0 | 1039.1 | -0.17 / -2.52 / -1.28 | 745.7 / 273.2 |
| ES 9 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | negative pre-2023 | 5145 | -124.1 | -1162.3 | -591.9 | 1038.3 | -0.29 / -2.57 / -1.37 | 712.9 / 238.0 |
| ES 10 15m ST[14, 2.0, 200] exit=ADRtrail0.2 | negative pre-2023 | 4893 | -106.0 | -1136.0 | -571.4 | 1030.0 | -0.24 / -2.43 / -1.27 | 696.2 / 223.4 |
| RTY 1 30m HM[9, 21, 200] exit=ADRtrail0.15 | positive pre-2023 | 1736 | 626.3 | 15.0 | 127.8 | 611.3 | 1.13 / 0.01 / 0.21 | 769.6 / 298.0 |
| RTY 2 15m HM[3, 6, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 4741 | 135.0 | -218.3 | -154.3 | 353.3 | 0.46 / -0.75 / -0.53 | 304.2 / 10.3 |
| RTY 3 30m HM[20, 55, 200] exit=ATRtrail2.0 | positive pre-2023 | 920 | 786.6 | 409.6 | 479.3 | 377.0 | 1.04 / 0.54 / 0.63 | 393.3 / 105.2 |
| RTY 4 (diag) 30m HM[9, 21, 200] exit=ADRtrail0.2 | positive pre-2023 | 1663 | 597.6 | 138.4 | 223.3 | 459.3 | 1.05 / 0.22 / 0.37 | 508.1 / 153.3 |
| RTY 5 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | positive pre-2023 | 1490 | 516.8 | 252.3 | 300.5 | 264.5 | 0.94 / 0.45 / 0.54 | 385.3 / 162.6 |
| RTY 6 (diag) 30m ST[4, 2.0, 20] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2807 | 206.1 | -209.3 | -134.1 | 415.4 | 0.46 / -0.45 / -0.29 | 503.8 / 159.3 |
| GC 1 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2594 | 236.5 | -111.6 | 36.6 | 348.1 | 0.44 / -0.20 / 0.07 | 1010.7 / 810.7 |
| GC 2 10m HM[20, 55, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 4187 | 408.6 | -237.0 | 37.6 | 645.6 | 0.91 / -0.53 / 0.08 | 835.1 / 466.6 |
| GC 3 30m HM[9, 21, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 2910 | 159.1 | -361.6 | -140.0 | 520.7 | 0.30 / -0.69 / -0.27 | 934.5 / 631.2 |
| GC 4 5m HM[20, 55, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 6849 | 474.6 | -175.0 | 102.1 | 649.6 | 1.25 / -0.46 / 0.27 | 652.7 / 281.1 |
| GC 5 30m HM[9, 21, 200] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 3118 | 255.2 | -601.7 | -237.4 | 857.0 | 0.46 / -1.09 / -0.43 | 1053.4 / 554.2 |
| GC 6 10m HM[20, 55, 200] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 4475 | 447.1 | -413.1 | -47.0 | 860.2 | 1.00 / -0.91 / -0.10 | 795.0 / 304.3 |
| GC 7 30m HM[9, 21, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 2984 | 220.9 | -421.8 | -148.6 | 642.7 | 0.39 / -0.74 / -0.26 | 794.9 / 419.6 |
| GC 8 10m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 4233 | 419.2 | -217.9 | 53.5 | 637.1 | 0.97 / -0.50 / 0.12 | 650.0 / 281.8 |
| GC 9 15m WT[20, 2.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 5145 | 138.1 | -382.5 | -160.9 | 520.6 | 0.36 / -1.01 / -0.43 | 546.6 / 245.5 |
| GC 10 10m ST[14, 3.0, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 4436 | 154.2 | -483.3 | -213.2 | 637.5 | 0.35 / -1.11 / -0.50 | 587.2 / 210.6 |
| CL 1 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | positive pre-2023 | 1833 | 355.7 | 18.7 | 63.8 | 337.0 | 0.58 / 0.03 / 0.10 | 587.7 / 295.2 |
| CL 2 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | positive pre-2023 | 1612 | 349.5 | 10.9 | 55.1 | 338.6 | 0.51 / 0.02 / 0.08 | 612.6 / 314.2 |
| CL 3 30m HM[20, 55, 200] exit=ATRtrail3.0 | positive pre-2023 | 1445 | 769.9 | 437.7 | 484.6 | 332.2 | 1.12 / 0.63 / 0.70 | 664.9 / 370.3 |
| CL 4 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1840 | 418.3 | -87.8 | -20.6 | 506.1 | 0.61 / -0.13 / -0.03 | 652.5 / 214.2 |
| CL 5 (diag) 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1622 | 389.7 | -261.5 | -177.0 | 651.2 | 0.50 / -0.33 / -0.23 | 763.5 / 197.7 |
| CL 6 (diag) 30m WT[20, 3.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1840 | 330.3 | -323.7 | -238.8 | 654.0 | 0.46 / -0.44 / -0.33 | 733.9 / 168.0 |
| ZN 1 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1532 | 519.7 | -1024.0 | -1253.6 | 1543.7 | 0.78 / -1.44 / -1.74 | 336.5 / -1094.1 |
| ZN 2 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1756 | 555.2 | -988.7 | -1216.9 | 1543.9 | 0.92 / -1.54 / -1.87 | 307.4 / -1119.7 |
| ZN 3 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1461 | 553.4 | -989.5 | -1217.4 | 1542.8 | 0.80 / -1.37 / -1.67 | 97.4 / -1361.3 |
| BTC 1 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | positive pre-2023 | 476 | 546.7 | 103.4 | 387.7 | 443.3 | 0.96 / 0.18 / 0.68 | 1560.1 / 1338.4 |
| BTC 2 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | positive pre-2023 | 529 | 391.5 | 102.5 | 286.9 | 289.0 | 0.80 / 0.18 / 0.58 | 1017.7 / 882.4 |
| BTC 3 15m ST[8, 2.0, 20] exit=ATRtrail3.0 | positive pre-2023 | 953 | 695.1 | 247.9 | 531.8 | 447.2 | 1.76 / 0.63 / 1.35 | 1005.2 / 800.3 |
| BTC 4 5m ST[14, 3.0, 200] exit=ADRtrail0.2 | positive pre-2023 | 1042 | 488.4 | 38.7 | 321.9 | 449.7 | 1.36 / 0.09 / 0.89 | 880.7 / 646.8 |
| BTC 5 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 483 | 164.5 | -502.3 | -75.5 | 666.8 | 0.25 / -0.73 / -0.11 | 1523.9 / 1192.3 |
| BTC 6 10m WT[20, 3.0, 100] exit=ATRtrail3.0 | positive pre-2023 | 751 | 1247.6 | 641.9 | 1026.4 | 605.7 | 2.99 / 1.52 / 2.46 | 1147.5 / 849.9 |
| BTC 7 15m WT[20, 3.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 470 | 181.5 | -277.9 | 14.1 | 459.3 | 0.30 / -0.45 / 0.02 | 1364.4 / 1132.8 |
| BTC 8 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 479 | 342.1 | -272.7 | 118.8 | 614.7 | 0.55 / -0.43 / 0.19 | 1453.5 / 1141.0 |
| BTC 9 5m ST[24, 2.0, 40] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1493 | 351.9 | -105.3 | 183.4 | 457.2 | 1.03 / -0.36 / 0.52 | 691.5 / 453.4 |
| BTC 10 15m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 418 | 342.9 | -114.0 | 179.8 | 456.9 | 0.57 / -0.15 / 0.31 | 1190.6 / 960.9 |
| ETH 1 15m WT[20, 3.0, 100] exit=ADRtrail0.15 | positive pre-2023 | 475 | 1121.9 | 400.5 | 647.7 | 721.4 | 1.67 / 0.60 / 0.96 | 1857.4 / 1289.2 |
| ETH 2 15m WT[20, 3.0, 100] exit=ATRtrail3.0 | positive pre-2023 | 472 | 909.0 | 381.7 | 566.0 | 527.2 | 1.60 / 0.67 / 0.99 | 1607.3 / 1195.1 |
| ETH 3 10m HM[3, 6, 20] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1732 | 247.6 | -294.9 | -111.1 | 542.5 | 0.87 / -1.03 / -0.40 | 997.9 / 559.1 |
| ETH 4 5m ST[14, 3.0, 200] exit=ADRtrail0.15 | positive pre-2023 | 1205 | 729.5 | 9.0 | 248.7 | 720.5 | 1.96 / 0.01 / 0.65 | 1218.2 / 648.0 |
| ETH 5 15m WT[20, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 692 | 221.3 | -311.6 | -133.2 | 532.9 | 0.46 / -0.65 / -0.28 | 1254.8 / 831.6 |
| ETH 6 15m WT[14, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 686 | 445.4 | -92.1 | 89.0 | 537.5 | 0.86 / -0.19 / 0.16 | 1259.9 / 835.9 |
| ETH 7 15m WT[14, 2.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 684 | 513.7 | -18.2 | 165.4 | 531.8 | 1.11 / -0.08 / 0.33 | 1145.8 / 739.9 |
| ETH 8 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | positive pre-2023 | 205 | 1198.5 | 853.0 | 970.1 | 345.5 | 1.19 / 0.85 / 0.96 | 1711.6 / 1450.4 |
| ETH 9 15m WT[20, 3.0, 100] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 476 | 733.1 | -53.8 | 220.7 | 786.9 | 1.11 / -0.09 / 0.33 | 1630.2 / 1010.1 |
| ETH 10 15m WT[14, 2.0, 100] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 739 | 527.0 | -188.3 | 52.8 | 715.3 | 1.05 / -0.40 / 0.08 | 1308.9 / 743.5 |
| YM 1 15m HM[20, 55, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 3058 | 368.2 | -360.4 | -17.6 | 728.6 | 0.67 / -0.63 / -0.03 | 1590.0 / 1190.9 |
| YM 2 15m HM[20, 55, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 2951 | 349.1 | -270.8 | 21.0 | 619.9 | 0.59 / -0.44 / 0.04 | 1390.8 / 1067.0 |
| YM 3 15m HM[20, 55, 200] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 3068 | 171.2 | -651.6 | -265.1 | 822.9 | 0.30 / -1.10 / -0.45 | 1337.6 / 907.2 |
| YM 4 15m HM[20, 55, 200] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 3137 | 123.6 | -1111.7 | -531.1 | 1235.2 | 0.22 / -1.87 / -0.91 | 1523.5 / 881.2 |
| YM 5 15m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2873 | 264.7 | -219.9 | 8.2 | 484.6 | 0.49 / -0.39 / 0.02 | 914.5 / 648.3 |
| YM 6 30m HM[20, 55, 200] exit=ADRtrail0.2 | positive pre-2023 | 1590 | 872.5 | 256.4 | 541.7 | 616.2 | 0.99 / 0.29 / 0.61 | 1473.9 / 1150.8 |
| YM 7 30m HM[20, 55, 200] exit=ATRtrail2.0 | positive pre-2023 | 1557 | 1022.7 | 523.0 | 754.1 | 499.7 | 1.22 / 0.61 / 0.89 | 1214.0 / 947.9 |
| YM 8 30m WT[20, 2.0, 100] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 2959 | 128.7 | -1090.9 | -523.5 | 1219.6 | 0.20 / -1.68 / -0.82 | 1292.2 / 654.5 |
| YM 9 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | positive pre-2023 | 1626 | 563.1 | 234.3 | 387.5 | 328.8 | 0.86 / 0.35 / 0.59 | 910.6 / 725.4 |
| YM 10 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2585 | 147.2 | -190.5 | -32.6 | 337.7 | 0.27 / -0.34 / -0.06 | 649.8 / 460.2 |


## 6b. Replication tests (leads only)
Lead: BTC 10m WT(20,3.0,100) ATR(14)x3 trail (cell 89). (a) live weeks: none exist (N/A). (b) H0 2023-02..07 standalone weekly Sharpe +2.17 on 251 trades: HOLDS. (c) cross-instrument, same cell, vol-matched, additive 20%, 2023-08..2026-10: ES uplift -0.06, RTY -0.12: FAILS. (d) alternating months, uplift at 20% on odd months +0.12 and even months +0.21 against +0.19 overall: HOLDS. 2 of 4 hold: replication condition met. File: outputs/autopilot/b/b1_co/repl_BTC_89.json.


## 6. What this says
- **Clean-only selection changes the picture for BTC and ETH, and for ES and GC in the selection span only.** With selection on clean 2023-08..2025-07 the false-survivor test now says there is structure: BTC top-10 mean clean Sharpe 2.07 against a replicate p95 of 1.48 (p = 0.00), ETH 1.93 against 1.37 (p = 0.00), ES 1.00 against 0.92 (p = 0.02), GC 0.83 against 0.88 (p = 0.09, count p = 0.00). None of ES, GC, RTY, CL, ZN carries into H1/H2 as an addition to the pair: the best ES cell (30m WT ADR-trail 0.2, clean Sharpe 1.57) has uplifts +0.09/-0.13/+0.02; GC HM 9/21 cells +0.09/+0.13/+0.00; every ES, GC, RTY, CL cell has at least one span below +0.10, bootstrap lower bounds <= +0.02, and ZN has no cell with positive weekly Sharpe in both clean halves. These are in-sample selection effects, with out-of-selection (H1+H2) standalone Sharpe frequently negative (ES: -1.6 to +0.6).
- **YM (GAPMAP D11 cell, added after the main batch):** 20 cells pass the rule against a replicate mean of 9.9 and the top-10 mean clean Sharpe 1.36 beats the replicate p95 of 0.86 (p = 0.00), but the best cells (15m HM 20/55 with ATR/ADR trails) carry +0.15/-0.09/+0.01 (ATR x2), +0.12/-0.04/+0.08, +0.10/+0.01/+0.10: H1 fails, bootstrap lower bounds <= +0.03, plateau <= 0.33: NO.
- **One lead, the same cell the legacy 2013-22-selected run found: BTC 10-minute WT (ATR 20, mult 3.0, EMA 100) with an ATR(14) x3 trailing stop, equal R.** Standalone weekly Sharpe clean 2.03 / H1 1.98 / H2 1.82 (all-in 1.99; H1+H2 out-of-selection 1.90 against its own random-entry null p95 of 1.09), additive uplift at 20% share +0.19 / +0.31 / +0.15 on clean / H1 / H2 (10%: +0.10/+0.16/+0.08; 30%: +0.27/+0.46/+0.22; 50%: +0.43/+0.72/+0.35), bootstrap 90% lower bound +0.10, worst-decile correlation -0.31 (17 weeks), all-in uplift at 2x slippage +0.13, worst week within the share (+2.4% at 20%). It fails exactly one gate: the plateau, 0.67 of the +-25% neighbours keep >= 75% of the uplift (needed 0.75). Not softened. Rank-1 BTC cell (15m WT ATR-trail x3) has +0.19/+0.24/-0.12, i.e. H2 negative. Replication (amendment 2): H0 2023-02..07 standalone Sharpe +2.17 (251 trades) holds; alternating months hold (odd +0.12, even +0.21 against +0.19 overall); cross-instrument fails (the same cell on ES -0.06, RTY -0.12), live weeks not available: 2 of 4, so replication holds but the plateau failure keeps it a LEAD, not a find.
- **ERA flag** of the lead: 'positive pre-2023' (2022 only for BTC futures: 751 trades, gross +$1,248, net +$642 fixed cost, +$1,026 price-scaled cost per trade at the sizing used; weekly Sharpe gross 2.99 / net 1.52). Of the 55 scored cells, 36 are 'gross-positive, cost-negative pre-2023', 16 'positive pre-2023' (mostly crypto, 2022 bear-market trend), 3 'negative pre-2023'. Mechanism in one sentence: BTC futures trend persistence at 10-15 minute scale with a wide ATR trail, which clears cost because intraday range is large relative to the tick and the ADR-scaled stop; it plausibly depends on the current crypto structure (ETF-era flow, 2023-26 trending regime) and on one asset.
- Caveats: the BTC futures history is 2022-01 onward only, so there is no long independent sample; ETH shows the same family on clean (top-10 mean 1.93) but its H2 uplifts are negative (-0.15 to -0.44) so the signal is not shared; the lead is one cell among 113 BTC cells that pass the rule (a trending-market effect that most BTC trend cells share), so its specific rank is not information.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b1.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b1/ (`B1_CO_all_selected_scored.csv`).

DONE B1
