# REPORT Q6 - Q6: B1 grid on FX (6E, 6J, 6B, 6A, 6C)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 1 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +0.02; best pair-window standalone Sharpe +0.49.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: 6E, 6J, 6B, 6A, 6C. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |     180 |        180 |         0 |              -1.477 |                0 |          0 |            3 |
| 6B    |     180 |        180 |         0 |              -0.526 |                1 |          0 |            3 |
| 6C    |     180 |        180 |         0 |              -1.267 |                0 |          0 |            3 |
| 6E    |     180 |        180 |         0 |              -0.664 |                0 |          0 |            3 |
| 6J    |     180 |        180 |         1 |               0.961 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| 6E    |     100 |                    0 |             0.22 |               2 |       1    |                     nan     |            0.361 |           1.024 |      nan |     nan     |                1.024 |
| 6J    |     100 |                    1 |             0.24 |               2 |       0.21 |                       0.961 |            0.354 |           0.826 |        0 |       0.961 |                0.826 |
| 6B    |     100 |                    0 |             0.04 |               1 |       1    |                     nan     |            0.447 |           0.537 |      nan |     nan     |                0.537 |
| 6A    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |      nan |     nan     |              nan     |
| 6C    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |      nan |     nan     |              nan     |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 347 | 0 | -0.66 | -1.80 | -0.79 | -1.16 / 0.23 | -0.03 / -0.10 / -0.08 | -0.09 | 0.26 | 0.75 | -0.11 | 0.00 | 556 | diag |
| 6E 2 (diag) | 10m ST[14, 3.0, 200] exit=ADRtrail0.2 | 963 | 0 | -1.05 | -3.01 | -1.32 | -2.21 / -1.11 | -0.07 / -0.21 / -0.25 | -0.29 | -0.13 | 0.96 | -0.23 | 0.00 | 1558 | diag |
| 6E 3 (diag) | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 583 | 0 | -1.10 | -2.96 | -1.16 | -1.62 / -0.15 | -0.08 / -0.02 / -0.21 | -0.18 | 0.62 | 0.77 | -0.17 | 0.00 | 940 | diag |
| 6J 1 | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 369 | 2 | 0.96 | -1.52 | 0.49 | -0.44 / 0.18 | 0.05 / 0.07 / -0.08 | -0.02 | 0.27 | 1.00 | -0.03 | 0.17 | 593 | NO |
| 6J 2 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 313 | 1 | 0.80 | -1.68 | 0.05 | -1.41 / 0.33 | 0.03 / -0.08 / -0.06 | -0.04 | 0.10 | 0.97 | -0.05 | 0.00 | 495 | diag |
| 6J 3 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 328 | 1 | 0.36 | -0.78 | -0.40 | -1.72 / 0.40 | 0.01 / -0.13 / -0.05 | -0.07 | 0.40 | 0.88 | -0.07 | 0.00 | 536 | diag |
| 6J 4 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | 371 | 1 | 0.25 | -1.51 | -0.54 | -2.18 / -0.58 | 0.01 / -0.06 / -0.15 | -0.10 | 0.26 | 0.96 | -0.09 | 0.00 | 595 | diag |
| 6B 1 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 294 | 1 | -0.53 | -1.48 | -0.49 | -0.52 / -0.22 | -0.02 / -0.03 / -0.06 | -0.07 | 0.24 | 0.90 | -0.07 | 0.00 | 491 | diag |
| 6B 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 306 | 0 | -0.84 | -1.80 | -1.16 | -1.78 / -0.63 | -0.04 / -0.12 / -0.09 | -0.13 | 0.03 | 0.93 | -0.11 | 0.00 | 514 | diag |
| 6B 3 (diag) | 30m HM[20, 55, 200] exit=ADRtrail0.2 | 306 | 0 | -0.99 | -2.04 | -1.46 | -2.35 / -0.77 | -0.04 / -0.19 / -0.11 | -0.16 | -0.12 | 0.80 | -0.13 | 0.00 | 517 | diag |
| 6A 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 370 | 0 | -1.48 | -2.20 | -1.39 | -1.49 / -0.67 | -0.07 / -0.11 / -0.12 | -0.16 | 0.44 | 0.70 | -0.14 | 0.00 | 571 | diag |
| 6A 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 346 | 0 | -1.50 | -1.97 | -1.65 | -1.83 / -0.71 | -0.08 / 0.02 / -0.15 | -0.16 | 0.12 | 0.64 | -0.14 | 0.00 | 532 | diag |
| 6A 3 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 370 | 0 | -2.16 | -2.36 | -1.72 | -1.57 / -1.47 | -0.12 / -0.08 / -0.16 | -0.23 | 0.36 | 0.85 | -0.19 | 0.00 | 572 | diag |
| 6C 1 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 347 | 0 | -1.27 | -2.42 | -0.74 | -0.00 / -0.65 | -0.05 / 0.03 / -0.04 | -0.09 | 0.20 | 0.97 | -0.08 | 0.00 | 544 | diag |
| 6C 2 (diag) | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 290 | 0 | -1.45 | -2.09 | -1.65 | -1.96 / -0.53 | -0.07 / -0.12 / -0.06 | -0.12 | -0.33 | 0.38 | -0.12 | 0.00 | 470 | diag |
| 6C 3 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 509 | 0 | -1.62 | -3.10 | -1.61 | -1.81 / -0.66 | -0.10 / -0.07 / -0.13 | -0.19 | 0.13 | 0.78 | -0.16 | 0.00 | 818 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 1 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 1 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 5 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | clean | -1.29 | -1.59 | -34507 | -30282 | 412438 | -43824 | -0.74 | 57.1 | 1.39 | -81949 | 287711 | -85551 |
| 6A 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H1 | -1.51 | -1.88 | -40284 | -34588 | 216212 | -49535 | -0.51 | 64.3 | 2.72 | -81897 | 160728 | -88194 |
| 6A 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H2 | -1.45 | -1.86 | -34853 | -31202 | 160791 | -38148 | -0.76 | 63.9 | 2.18 | -82906 | 217952 | -87240 |
| 6A 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | all | -1.39 | -1.70 | -36545 | -31675 | 608172 | -49535 | -0.88 | 59.5 | 1.77 | -82932 | 287711 | -88194 |
| 6B 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | clean | -0.47 | -0.70 | -28668 | -24785 | 197019 | -36529 | -0.54 | 56.2 | 1.44 | -80077 | 274554 | -85739 |
| 6B 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H1 | -0.19 | -0.26 | -30242 | -26490 | 47678 | -32032 | -0.23 | 39.3 | 2.80 | -82489 | 150127 | -83339 |
| 6B 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | H2 | -0.75 | -1.09 | -30961 | -25821 | 142602 | -35186 | -0.42 | 58.3 | 2.23 | -84090 | 221245 | -86024 |
| 6B 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | all | -0.49 | -0.71 | -30232 | -25674 | 221165 | -36529 | -0.80 | 54.2 | 1.83 | -81930 | 274554 | -86024 |
| 6C 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | clean | -1.27 | -1.51 | -42819 | -33575 | 381000 | -56073 | -0.76 | 57.1 | 1.41 | -79899 | 279367 | -84309 |
| 6C 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H1 | 0.17 | 0.28 | -29320 | -26836 | 101671 | -33548 | 0.13 | 53.6 | 2.86 | -77289 | 143462 | -78825 |
| 6C 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | H2 | -0.14 | -0.22 | -36801 | -30196 | 90785 | -41191 | -0.15 | 55.6 | 2.25 | -82578 | 223353 | -83729 |
| 6C 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | all | -0.74 | -0.97 | -40452 | -32518 | 441405 | -56073 | -0.65 | 56.0 | 1.82 | -80576 | 279367 | -84309 |
| 6E 30m ST[14, 3.0, 200] exit=ATRtrail2.0 (diag) | clean | -0.56 | -0.81 | -34988 | -29490 | 337852 | -49167 | -0.42 | 58.1 | 1.43 | -80630 | 286701 | -87262 |
| 6E 30m ST[14, 3.0, 200] exit=ATRtrail2.0 (diag) | H1 | -2.68 | -3.03 | -27036 | -22931 | 135039 | -34811 | -0.88 | 78.6 | 2.73 | -78695 | 158968 | -81231 |
| 6E 30m ST[14, 3.0, 200] exit=ATRtrail2.0 (diag) | H2 | -0.62 | -0.93 | -43179 | -34266 | 209252 | -44167 | -0.33 | 61.1 | 2.21 | -81589 | 224180 | -82526 |
| 6E 30m ST[14, 3.0, 200] exit=ATRtrail2.0 (diag) | all | -0.79 | -1.13 | -36788 | -30941 | 501420 | -49167 | -0.66 | 61.9 | 1.80 | -81007 | 286701 | -87262 |
| 6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | clean | 1.01 | 1.66 | -30659 | -26183 | 116296 | -56906 | 2.23 | 44.8 | 1.51 | -78815 | 283436 | -81144 |
| 6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | H1 | 0.43 | 0.72 | -29921 | -27526 | 120717 | -35202 | 0.27 | 50.0 | 2.89 | -76106 | 155646 | -78945 |
| 6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | H2 | -1.47 | -1.82 | -26588 | -23092 | 154052 | -32677 | -0.63 | 55.6 | 2.21 | -83943 | 220718 | -86189 |
| 6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | all | 0.49 | 0.77 | -30720 | -26187 | 192185 | -56906 | 1.02 | 48.2 | 1.87 | -80550 | 283436 | -86189 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| 6E 30m ST[14, 3.0, 200] exit=ATRtrail2.0 (diag) | -33.7 | 18.8 | 26.4 | 26.5 | 18.2 / 26.2 | 24.4 / 27.9 | NO |
| 6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | -27.8 | 20.6 | 27.4 | 28.2 | 27.6 / 29.8 | 28.7 / 32.9 | NO |
| 6B 30m HM[20, 55, 200] exit=ATRtrail3.0 (diag) | -32.0 | 21.6 | 24.3 | 33.0 | 21.0 / 26.6 | 18.9 / 20.6 | NO |
| 6A 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | -36.0 | 15.6 | 22.8 | 25.9 | 20.4 / 23.8 | 11.0 / 21.7 | NO |
| 6C 30m ST[14, 3.0, 200] exit=ATRtrail3.0 (diag) | -33.2 | 25.0 | 27.1 | 30.4 | 25.5 / 27.5 | 29.0 / 30.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | negative pre-2023 | 1572 | -697.8 | -1316.2 | -1356.8 | 618.4 | -0.96 / -1.80 / -1.85 | 336.0 / -410.5 |
| 6E 2 (diag) 10m ST[14, 3.0, 200] exit=ADRtrail0.2 | negative pre-2023 | 4720 | -526.1 | -1354.9 | -1412.2 | 828.9 | -1.20 / -3.01 / -3.13 | 479.8 / -453.0 |
| 6E 3 (diag) 30m HM[9, 21, 200] exit=ATRtrail2.0 | negative pre-2023 | 2978 | -911.2 | -1529.5 | -1572.3 | 618.3 | -1.77 / -2.96 / -3.03 | 282.5 / -489.7 |
| 6J 1 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | negative pre-2023 | 1811 | -400.3 | -929.9 | -1100.5 | 529.6 | -0.66 / -1.52 / -1.79 | 1326.2 / 703.6 |
| 6J 2 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | negative pre-2023 | 1534 | -574.4 | -1111.0 | -1282.9 | 536.5 | -0.88 / -1.68 / -1.93 | 1278.6 / 663.4 |
| 6J 3 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | negative pre-2023 | 1512 | -20.7 | -539.1 | -708.1 | 518.4 | -0.03 / -0.78 / -1.02 | 886.5 / 262.8 |
| 6J 4 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | negative pre-2023 | 1812 | -243.6 | -1038.2 | -1294.0 | 794.5 | -0.36 / -1.51 / -1.87 | 1177.4 / 244.9 |
| 6B 1 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | negative pre-2023 | 1522 | -407.6 | -1010.9 | -1064.7 | 603.3 | -0.61 / -1.48 / -1.55 | 434.9 / -361.6 |
| 6B 2 (diag) 30m HM[20, 55, 200] exit=ATRtrail2.0 | negative pre-2023 | 1587 | -459.0 | -1361.3 | -1442.0 | 902.3 | -0.62 / -1.80 / -1.90 | 628.7 / -567.5 |
| 6B 3 (diag) 30m HM[20, 55, 200] exit=ADRtrail0.2 | negative pre-2023 | 1596 | -557.3 | -1758.3 | -1871.3 | 1201.1 | -0.66 / -2.04 / -2.15 | 794.4 / -694.4 |
| 6A 1 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | negative pre-2023 | 1651 | -528.1 | -1362.3 | -1483.6 | 834.3 | -0.88 / -2.20 / -2.38 | 213.4 / -822.7 |
| 6A 2 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | negative pre-2023 | 1600 | -404.3 | -1222.2 | -1349.6 | 817.8 | -0.66 / -1.97 / -2.16 | 72.6 / -985.1 |
| 6A 3 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | negative pre-2023 | 1654 | -443.8 | -1695.0 | -1877.1 | 1251.2 | -0.63 / -2.36 / -2.59 | 218.0 / -1336.1 |
| 6C 1 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | negative pre-2023 | 1691 | -874.5 | -1549.3 | -1601.6 | 674.8 | -1.40 / -2.42 / -2.49 | 163.7 / -831.8 |
| 6C 2 (diag) 30m HM[20, 55, 200] exit=ATRtrail3.0 | negative pre-2023 | 1486 | -726.4 | -1378.5 | -1430.5 | 652.2 | -1.12 / -2.09 / -2.15 | -81.7 / -1082.1 |
| 6C 3 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | negative pre-2023 | 2634 | -900.7 | -1565.0 | -1617.1 | 664.3 | -1.82 / -3.10 / -3.19 | 146.3 / -864.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6B: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6C: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6E: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); 6J: 1 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 0.21, p(top) = 0.00).
- Of 1 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.02 (6J 30m WT[20, 3.0, 100] exit=ATRtrail3.0); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q6.py (= ap_b1.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q6/ (`Q6_CO_all_selected_scored.csv`).

DONE Q6
