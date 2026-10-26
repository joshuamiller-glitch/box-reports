# REPORT Q3 - Q3: B1 grid on metals/energy (SI, HG, PL, HO, RB, NG)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 32 selected cells (+14 diagnostic) scored on 6 instruments; best non-diagnostic all-in additive uplift at 20% share +0.07; best pair-window standalone Sharpe +1.03.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Signals: ST = Supertrend (Wilder ATR, close source) flip with EMA filter (live NQ ST: ATR 120 / 2.0 / EMA 200 on 1-min); HM = HMA(a) x HMA(b) of close minus session VWAP with slope and EMA filter (live NQ HM 20/55); WT = Wilder-ATR trailing-stop flip (WT_MODAL: ATR 20 / 2.0 / close / EMA 100, from b3_refs). Another worker re-scores WT on NQ; this family covers the other instruments only.
- Exits: initial stop = trailing distance D (ratchet from the favourable extreme), no target, flat 16:55 ET. D = k x ADR20 (k 0.10/0.15/0.20) or m x ATR(14) of the tf bar (m 2/3). Entry windows 18:00-09:00 and 09:59-15:00 ET (NT8 windows of d1_f4_core).
- Instruments: SI, HG, PL, HO, RB, NG. Grid: 180 cells per instrument = 4 bar sizes x 9 signal parameter sets x 5 trail exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: equal R: every full-size stop = $9,600 (qty = R / (D x $/pt), fractional contracts as in d1_f4_core); sleeve not volatility-rescaled. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HG    |     180 |        180 |         3 |               0.704 |                2 |          3 |            3 |
| HO    |     180 |        180 |         8 |               0.721 |                2 |          8 |            2 |
| NG    |     180 |        180 |         2 |               0.596 |                2 |          2 |            3 |
| PL    |     180 |        180 |        12 |               1.527 |                2 |         10 |            0 |
| RB    |     180 |        180 |         4 |               0.589 |                2 |          4 |            3 |
| SI    |     180 |        180 |         5 |               0.56  |                2 |          5 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SI    |     100 |                    5 |             0.93 |               5 |       0.01 |                       0.281 |            0.554 |           1.013 |     0.56 |       0.56  |                1.187 |
| HG    |     100 |                    3 |             1.49 |               4 |       0.19 |                       0.581 |            0.583 |           1.154 |     0.37 |       0.704 |                1.461 |
| PL    |     100 |                   12 |             2.65 |               7 |       0    |                       0.986 |            0.578 |           0.878 |     0.03 |       1.527 |                1.325 |
| HO    |     100 |                    8 |            17.03 |              28 |       1    |                       0.499 |            0.84  |           1.074 |     0.98 |       0.721 |                1.94  |
| RB    |     100 |                    4 |             7.25 |              15 |       0.92 |                       0.371 |            0.571 |           0.752 |     0.97 |       0.589 |                1.616 |
| NG    |     100 |                    2 |             1.25 |               5 |       0.33 |                       0.412 |            0.489 |           0.896 |     0.43 |       0.596 |                1.139 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI 1 | 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | 320 | 2 | 0.56 | -2.24 | 0.71 | 0.93 / 1.26 | 0.03 / 0.09 / 0.01 | -0.01 | 0.06 | 1.00 | -0.02 | 0.33 | 510 | NO |
| SI 2 | 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | 320 | 2 | 0.40 | -1.70 | 0.54 | 0.76 / 1.00 | 0.02 / 0.04 / 0.00 | -0.01 | 0.31 | 1.00 | -0.03 | 0.50 | 510 | NO |
| SI 3 | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 320 | 2 | 0.25 | -1.59 | 0.78 | 1.57 / 1.24 | 0.01 / 0.15 / 0.01 | 0.00 | 0.19 | 1.00 | -0.02 | 0.33 | 510 | NO |
| SI 4 | 30m ST[14, 3.0, 200] exit=ADRtrail0.1 | 320 | 2 | 0.13 | -2.80 | -0.04 | -0.43 / 1.25 | 0.01 / 0.06 / -0.06 | -0.07 | 0.10 | 0.98 | -0.05 | 0.00 | 510 | NO |
| SI 5 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 320 | 2 | 0.07 | -1.07 | 0.69 | 1.84 / 1.22 | -0.00 / 0.16 / 0.02 | 0.01 | -0.02 | 0.99 | -0.02 | 0.33 | 510 | NO |
| SI 6 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 487 | 1 | 0.54 | -1.18 | 0.27 | -0.20 / 1.28 | 0.02 / 0.04 / -0.14 | -0.04 | 0.37 | 0.85 | -0.07 | 0.00 | 773 | diag |
| SI 7 (diag) | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 363 | 1 | 0.17 | -0.99 | 0.78 | 2.06 / 1.59 | -0.01 / 0.12 / 0.05 | 0.00 | -0.24 | 0.97 | -0.02 | 0.50 | 576 | diag |
| SI 8 (diag) | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 549 | 1 | 0.08 | -2.20 | 0.38 | 0.74 / 1.22 | -0.00 / 0.18 / -0.13 | -0.05 | 0.36 | 0.98 | -0.06 | 0.00 | 875 | diag |
| HG 1 | 30m HM[9, 21, 200] exit=ADRtrail0.2 | 661 | 2 | 0.70 | -1.14 | 0.72 | 0.48 / 0.49 | 0.07 / -0.09 / 0.04 | -0.02 | -0.35 | 1.00 | -0.03 | 0.00 | 1008 | NO |
| HG 2 | 30m HM[20, 55, 200] exit=ATRtrail2.0 | 331 | 2 | 0.53 | -0.64 | 0.25 | -0.48 / 0.93 | 0.03 / -0.07 / -0.04 | -0.03 | 0.05 | 0.90 | -0.05 | 0.00 | 532 | NO |
| HG 3 | 30m HM[20, 55, 200] exit=ATRtrail3.0 | 314 | 2 | 0.51 | -0.28 | 0.24 | -0.48 / 0.79 | 0.03 / -0.11 / -0.00 | -0.02 | 0.30 | 0.91 | -0.05 | 0.00 | 503 | NO |
| HG 4 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 564 | 1 | 0.29 | -0.45 | 0.10 | -0.25 / 0.56 | 0.00 / -0.13 / 0.01 | -0.04 | 0.10 | 0.86 | -0.07 | 0.00 | 870 | diag |
| HG 5 (diag) | 30m HM[20, 55, 200] exit=ADRtrail0.2 | 332 | 1 | 0.26 | -0.57 | 0.37 | 0.27 / 0.65 | 0.02 / -0.00 / 0.01 | -0.03 | -0.08 | 0.98 | -0.04 | 0.17 | 534 | diag |
| HG 6 (diag) | 30m HM[9, 21, 200] exit=ATRtrail2.0 | 637 | 1 | 0.10 | -0.76 | -0.03 | -0.42 / 0.57 | 0.01 / -0.07 / -0.05 | -0.07 | -0.42 | 0.97 | -0.08 | 0.00 | 986 | diag |
| PL 1 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 332 | 2 | 1.53 | -0.17 | 1.03 | 0.18 / 1.47 | 0.08 / 0.02 / 0.02 | 0.05 | 0.09 | 0.97 | 0.01 | 0.50 | 538 | NO |
| PL 2 | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 332 | 2 | 1.33 | -0.66 | 0.69 | -0.16 / 1.33 | 0.08 / 0.00 / 0.03 | 0.04 | -0.12 | 0.96 | -0.00 | 0.67 | 538 | NO |
| PL 3 | 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | 395 | 2 | 1.30 | -0.26 | 0.88 | 0.11 / 1.32 | 0.07 / 0.04 / 0.02 | 0.04 | 0.03 | 0.99 | 0.00 | 0.67 | 622 | NO |
| PL 4 | 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | 332 | 2 | 1.23 | -1.10 | 0.66 | -0.17 / 1.07 | 0.07 / -0.09 / 0.03 | 0.01 | -0.03 | 0.99 | -0.02 | 0.50 | 538 | NO |
| PL 5 | 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | 395 | 2 | 1.00 | -0.84 | 0.88 | 0.74 / 0.93 | 0.06 / 0.08 / 0.11 | 0.05 | -0.07 | 0.99 | 0.01 | 0.50 | 622 | LEAD(gate3-7 fail: plateau 2xslip) |
| PL 6 | 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | 332 | 2 | 0.91 | -1.16 | 0.40 | -0.34 / 1.18 | 0.06 / -0.05 / 0.04 | 0.02 | -0.13 | 1.00 | -0.02 | 0.83 | 538 | NO |
| PL 7 | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 899 | 2 | 0.80 | -0.76 | 0.56 | 0.02 / 1.19 | 0.07 / 0.02 / 0.05 | 0.02 | 0.12 | 0.92 | -0.02 | 0.33 | 1386 | NO |
| PL 8 | 30m WT[20, 3.0, 100] exit=ADRtrail0.15 | 395 | 2 | 0.74 | -1.47 | 0.52 | 0.34 / 1.27 | 0.04 / -0.03 / 0.07 | -0.00 | -0.13 | 0.99 | -0.03 | 0.50 | 622 | NO |
| PL 9 | 30m ST[14, 3.0, 200] exit=ADRtrail0.1 | 332 | 2 | 0.63 | -1.62 | 0.27 | -0.43 / 1.07 | 0.03 / -0.03 / -0.04 | -0.04 | -0.19 | 1.00 | -0.05 | 0.33 | 538 | NO |
| PL 10 | 30m WT[20, 3.0, 100] exit=ADRtrail0.2 | 395 | 2 | 0.39 | -1.41 | 0.55 | 0.89 / 0.91 | 0.03 / 0.09 / 0.11 | 0.02 | -0.07 | 1.00 | -0.02 | 0.50 | 622 | NO |
| HO 1 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 366 | 2 | 0.72 | -0.05 | 0.91 | 1.56 / 1.41 | 0.02 / 0.06 / 0.12 | 0.04 | 0.06 | 0.96 | 0.00 | 0.33 | 568 | NO |
| HO 2 | 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | 629 | 2 | 0.60 | 0.08 | 0.77 | 1.34 / 1.12 | 0.05 / 0.12 / 0.08 | 0.04 | 0.28 | 0.98 | -0.01 | 0.33 | 1007 | NO |
| HO 3 | 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | 366 | 2 | 0.60 | -0.01 | 0.57 | 0.86 / 1.47 | 0.03 / 0.05 / 0.04 | 0.03 | 0.42 | 0.91 | -0.02 | 0.67 | 568 | NO |
| HO 4 | 5m WT[14, 2.0, 100] exit=ADRtrail0.15 | 2684 | 2 | 0.54 | -0.68 | 0.41 | 0.40 / 1.27 | 0.06 / -0.28 / 0.19 | -0.05 | -0.12 | 0.96 | -0.10 | 0.33 | 4379 | NO |
| HO 5 | 5m WT[20, 2.0, 100] exit=ADRtrail0.2 | 2175 | 2 | 0.41 | -0.22 | 0.24 | 0.16 / 1.62 | 0.02 / -0.26 / 0.10 | -0.06 | -0.12 | 0.89 | -0.11 | 0.67 | 3574 | NO |
| HO 6 | 5m WT[14, 2.0, 100] exit=ADRtrail0.2 | 2146 | 2 | 0.40 | -0.14 | 0.06 | -0.35 / 2.07 | 0.03 / -0.31 / 0.02 | -0.08 | -0.01 | 0.74 | -0.14 | 0.00 | 3535 | NO |
| HO 7 | 5m WT[20, 2.0, 100] exit=ADRtrail0.15 | 2722 | 2 | 0.38 | -0.88 | 0.35 | 0.54 / 1.38 | 0.04 / -0.25 / 0.19 | -0.06 | -0.15 | 0.93 | -0.11 | 0.50 | 4450 | NO |
| HO 8 | 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | 366 | 2 | 0.36 | 0.04 | 0.48 | 0.87 / 1.34 | 0.02 / 0.06 / 0.05 | 0.02 | 0.31 | 0.78 | -0.02 | 0.67 | 568 | NO |
| HO 9 (diag) | 30m ST[14, 2.0, 200] exit=ADRtrail0.2 | 596 | 1 | 0.68 | 0.32 | 0.59 | 0.77 / 1.74 | 0.04 / 0.08 / 0.01 | 0.03 | 0.38 | 0.88 | -0.02 | 0.50 | 957 | diag |
| HO 10 (diag) | 30m ST[14, 2.0, 200] exit=ADRtrail0.15 | 597 | 1 | 0.64 | -0.03 | 0.68 | 0.96 / 1.17 | 0.05 / 0.11 / 0.03 | 0.04 | 0.28 | 0.96 | -0.01 | 0.33 | 960 | diag |
| RB 1 | 30m WT[20, 2.0, 100] exit=ADRtrail0.15 | 644 | 2 | 0.59 | 0.24 | 0.27 | -0.35 / 1.23 | 0.03 / -0.12 / -0.02 | -0.03 | -0.15 | 0.85 | -0.07 | 0.00 | 1021 | NO |
| RB 2 | 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | 641 | 2 | 0.57 | 0.36 | 0.19 | -0.48 / 1.00 | 0.03 / -0.13 / -0.01 | -0.03 | -0.12 | 0.87 | -0.07 | 0.00 | 1026 | NO |
| RB 3 | 30m ST[14, 2.0, 200] exit=ADRtrail0.15 | 613 | 2 | 0.22 | 0.43 | -0.17 | -0.92 / 1.15 | 0.00 / -0.12 / -0.04 | -0.05 | -0.13 | 0.71 | -0.09 | 0.00 | 984 | NO |
| RB 4 | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 870 | 2 | 0.10 | -0.03 | -0.11 | -0.51 / 1.15 | 0.01 / 0.07 / -0.13 | -0.04 | 0.23 | 0.70 | -0.09 | 0.00 | 1400 | NO |
| RB 5 (diag) | 10m ST[14, 3.0, 200] exit=ADRtrail0.1 | 1110 | 1 | 0.50 | -0.68 | 0.10 | -0.73 / 0.78 | 0.07 / -0.28 / -0.06 | -0.08 | 0.22 | 0.93 | -0.10 | 0.00 | 1784 | diag |
| RB 6 (diag) | 30m WT[20, 2.0, 100] exit=ADRtrail0.1 | 644 | 1 | 0.34 | -0.31 | 0.21 | -0.06 / 0.81 | 0.03 / -0.14 / 0.07 | -0.03 | -0.01 | 0.96 | -0.06 | 0.67 | 1021 | diag |
| RB 7 (diag) | 30m WT[14, 2.0, 100] exit=ADRtrail0.1 | 641 | 1 | 0.34 | -0.36 | 0.27 | 0.18 / 1.14 | 0.03 / -0.13 / 0.13 | -0.02 | -0.03 | 0.96 | -0.05 | 0.17 | 1026 | diag |
| NG 1 | 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | 327 | 2 | 0.60 | -0.08 | 0.41 | 0.02 / 0.50 | 0.03 / 0.13 / -0.06 | -0.00 | 0.21 | 0.91 | -0.03 | 0.67 | 531 | NO |
| NG 2 | 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | 828 | 2 | 0.23 | -1.05 | -0.27 | -1.01 / 0.16 | 0.05 / 0.03 / -0.17 | -0.07 | 0.37 | 0.92 | -0.08 | 0.00 | 1364 | NO |
| NG 3 (diag) | 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | 331 | 1 | 0.38 | -0.57 | 0.21 | -0.08 / 0.34 | 0.03 / 0.17 / -0.07 | -0.02 | 0.26 | 1.00 | -0.03 | 0.50 | 536 | diag |
| NG 4 (diag) | 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | 521 | 1 | 0.34 | -0.73 | -0.38 | -1.63 / 0.29 | 0.02 / -0.06 / -0.11 | -0.06 | 0.18 | 0.72 | -0.08 | 0.00 | 852 | diag |
| NG 5 (diag) | 30m HM[9, 21, 200] exit=ATRtrail3.0 | 521 | 1 | 0.32 | -0.43 | -0.10 | -0.64 / 0.36 | 0.01 / 0.17 / -0.12 | -0.04 | 0.06 | 0.90 | -0.05 | 0.50 | 829 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 32 |
| diagnostic cells read | 14 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 1 |
| all-in uplift @20% > 0 (all scored) | 32 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 26 |
| worst-decile corr <= +0.30 | 38 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HG 30m HM[9, 21, 200] exit=ADRtrail0.2 | clean | 0.88 | 1.59 | -33568 | -31395 | 176487 | -45556 | 1.70 | 55.2 | 1.53 | -80351 | 272681 | -83123 |
| HG 30m HM[9, 21, 200] exit=ADRtrail0.2 | H1 | -0.02 | -0.02 | -54049 | -47158 | 134144 | -69717 | -0.01 | 46.4 | 2.74 | -79532 | 144904 | -84963 |
| HG 30m HM[9, 21, 200] exit=ADRtrail0.2 | H2 | 0.96 | 1.94 | -32458 | -28246 | 98000 | -38850 | 1.15 | 52.8 | 2.34 | -80333 | 213205 | -83496 |
| HG 30m HM[9, 21, 200] exit=ADRtrail0.2 | all | 0.72 | 1.23 | -39430 | -34803 | 176487 | -69717 | 2.33 | 53.6 | 1.90 | -81109 | 272681 | -84963 |
| HO 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | clean | 0.42 | 0.75 | -37209 | -32008 | 319966 | -66741 | 0.50 | 52.4 | 1.50 | -81404 | 285604 | -83311 |
| HO 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | H1 | 1.19 | 2.55 | -28180 | -27847 | 81863 | -28935 | 1.47 | 46.4 | 2.95 | -78134 | 146759 | -79587 |
| HO 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | H2 | 1.45 | 3.00 | -36381 | -30134 | 135573 | -46397 | 1.37 | 50.0 | 2.37 | -84228 | 214364 | -86877 |
| HO 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | all | 0.77 | 1.45 | -36379 | -31518 | 386139 | -68141 | 1.21 | 50.6 | 1.92 | -82082 | 285604 | -86877 |
| NG 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | clean | 0.69 | 1.14 | -24917 | -21121 | 95330 | -38207 | 1.58 | 52.4 | 1.49 | -80410 | 279935 | -81881 |
| NG 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | H1 | 1.07 | 2.43 | -24557 | -22806 | 84327 | -28103 | 1.07 | 60.7 | 2.96 | -71164 | 156105 | -80772 |
| NG 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | H2 | -1.24 | -1.79 | -22130 | -20304 | 136527 | -23818 | -0.63 | 72.2 | 2.24 | -80812 | 219701 | -81376 |
| NG 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | all | 0.41 | 0.71 | -25104 | -21537 | 155101 | -38207 | 0.99 | 57.7 | 1.88 | -80555 | 279935 | -81881 |
| PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | clean | 0.96 | 1.61 | -35333 | -30127 | 152405 | -47463 | 1.79 | 45.7 | 1.52 | -79769 | 276437 | -81833 |
| PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | H1 | 0.04 | 0.06 | -27643 | -25996 | 69020 | -29690 | 0.03 | 53.6 | 2.91 | -70111 | 156350 | -71154 |
| PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | H2 | 1.19 | 2.65 | -27932 | -24232 | 87078 | -30302 | 1.43 | 50.0 | 2.40 | -79961 | 221589 | -81792 |
| PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | all | 0.88 | 1.55 | -33097 | -28693 | 152405 | -47463 | 2.62 | 48.2 | 1.93 | -79560 | 276437 | -81833 |
| RB 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | clean | 0.57 | 0.97 | -42098 | -35642 | 352370 | -56553 | 0.59 | 52.4 | 1.49 | -80637 | 296200 | -84559 |
| RB 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | H1 | -0.87 | -1.19 | -40384 | -39713 | 267922 | -40807 | -0.32 | 53.6 | 2.70 | -81269 | 163790 | -86280 |
| RB 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | H2 | -0.12 | -0.19 | -36901 | -32761 | 86608 | -37504 | -0.15 | 55.6 | 2.29 | -80962 | 221659 | -81440 |
| RB 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | all | 0.19 | 0.31 | -42509 | -36880 | 537311 | -56553 | 0.21 | 53.6 | 1.86 | -81336 | 296200 | -86280 |
| SI 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | clean | 0.29 | 0.48 | -33103 | -28371 | 119853 | -39285 | 0.64 | 50.5 | 1.47 | -81636 | 274526 | -87056 |
| SI 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | H1 | 2.13 | 6.11 | -16545 | -14847 | 46174 | -16693 | 3.09 | 50.0 | 2.97 | -78482 | 141293 | -78877 |
| SI 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | H2 | 1.16 | 2.11 | -28611 | -23306 | 64384 | -34523 | 1.66 | 47.2 | 2.31 | -84725 | 225266 | -85398 |
| SI 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | all | 0.78 | 1.39 | -31616 | -25822 | 119853 | -39285 | 2.72 | 50.0 | 1.89 | -82016 | 274526 | -87056 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SI 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | -26.4 | 19.2 | 24.1 | 33.0 | 18.5 / 24.3 | 27.5 / 28.3 | NO |
| HG 30m HM[9, 21, 200] exit=ADRtrail0.2 | -25.4 | 21.5 | 25.3 | 30.9 | 25.8 / 25.9 | 17.2 / 26.3 | NO |
| PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | -25.5 | 28.5 | 28.7 | 32.0 | 29.2 / 27.4 | 43.7 / 44.5 | NO |
| HO 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | -24.8 | 22.1 | 24.4 | 27.1 | 22.8 / 24.6 | 27.5 / 29.0 | NO |
| RB 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | -28.8 | 19.1 | 24.5 | 21.4 | 23.1 / 25.0 | 14.7 / 22.9 | NO |
| NG 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | -28.3 | 27.3 | 27.4 | 30.1 | 26.8 / 26.7 | 25.2 / 42.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SI 1 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | negative pre-2023 | 1665 | -92.5 | -1784.0 | -1128.9 | 1691.5 | -0.11 / -2.24 / -1.43 | 1523.0 / 577.9 |
| SI 2 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | negative pre-2023 | 1665 | -68.9 | -1337.5 | -846.3 | 1268.6 | -0.08 / -1.70 / -1.09 | 1084.1 / 375.3 |
| SI 3 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | negative pre-2023 | 1665 | -120.5 | -1156.5 | -756.6 | 1036.1 | -0.16 / -1.59 / -1.05 | 813.5 / 238.2 |
| SI 4 30m ST[14, 3.0, 200] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 1665 | 119.5 | -2417.7 | -1435.2 | 2537.2 | 0.15 / -2.80 / -1.70 | 1563.6 / 146.0 |
| SI 5 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | negative pre-2023 | 1664 | -36.6 | -727.4 | -460.7 | 690.8 | -0.05 / -1.07 / -0.68 | 453.7 / 70.2 |
| SI 6 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2655 | 61.9 | -638.1 | -365.3 | 700.0 | 0.12 / -1.18 / -0.68 | 702.5 / 309.1 |
| SI 7 (diag) 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1934 | 64.7 | -625.6 | -356.9 | 690.3 | 0.09 / -0.99 / -0.58 | 462.3 / 67.8 |
| SI 8 (diag) 30m HM[9, 21, 200] exit=ATRtrail2.0 | negative pre-2023 | 2995 | -165.7 | -1214.0 | -805.9 | 1048.3 | -0.31 / -2.20 / -1.49 | 629.8 / 48.1 |
| HG 1 30m HM[9, 21, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 3126 | 276.3 | -698.5 | -400.9 | 974.8 | 0.47 / -1.14 / -0.65 | 1103.0 / 454.3 |
| HG 2 30m HM[20, 55, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1757 | 329.0 | -443.5 | -205.5 | 772.4 | 0.48 / -0.64 / -0.30 | 1066.0 / 551.5 |
| HG 3 30m HM[20, 55, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1666 | 334.0 | -182.6 | -23.4 | 516.5 | 0.53 / -0.28 / -0.04 | 824.9 / 482.9 |
| HG 4 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2655 | 289.4 | -240.2 | -79.6 | 529.6 | 0.52 / -0.45 / -0.16 | 495.7 / 149.6 |
| HG 5 (diag) 30m HM[20, 55, 200] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 1770 | 554.3 | -437.3 | -131.3 | 991.6 | 0.74 / -0.57 / -0.17 | 1016.2 / 347.9 |
| HG 6 (diag) 30m HM[9, 21, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 3007 | 351.8 | -438.6 | -197.1 | 790.4 | 0.61 / -0.76 / -0.35 | 615.2 / 101.3 |
| PL 1 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1739 | 228.1 | -111.1 | -132.5 | 339.2 | 0.35 / -0.17 / -0.20 | 1272.8 / 979.9 |
| PL 2 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1741 | 66.3 | -442.7 | -474.7 | 508.9 | 0.10 / -0.66 / -0.70 | 1339.4 / 900.1 |
| PL 3 30m WT[20, 3.0, 100] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1976 | 177.4 | -158.9 | -181.8 | 336.3 | 0.30 / -0.26 / -0.30 | 1076.2 / 784.2 |
| PL 4 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | negative pre-2023 | 1741 | -22.2 | -867.5 | -921.0 | 845.3 | -0.04 / -1.10 / -1.17 | 1738.1 / 994.8 |
| PL 5 30m WT[20, 3.0, 100] exit=ATRtrail2.0 | negative pre-2023 | 1983 | -17.9 | -522.4 | -556.9 | 504.4 | -0.03 / -0.84 / -0.90 | 1127.4 / 689.5 |
| PL 6 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | negative pre-2023 | 1740 | -188.6 | -822.8 | -862.9 | 634.2 | -0.27 / -1.16 / -1.21 | 1219.8 / 662.3 |
| PL 7 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 4467 | 40.9 | -301.7 | -326.5 | 342.6 | 0.10 / -0.76 / -0.83 | 650.3 / 343.5 |
| PL 8 30m WT[20, 3.0, 100] exit=ADRtrail0.15 | negative pre-2023 | 1983 | -190.6 | -1037.6 | -1094.8 | 846.9 | -0.28 / -1.47 / -1.55 | 1243.8 / 495.2 |
| PL 9 30m ST[14, 3.0, 200] exit=ADRtrail0.1 | negative pre-2023 | 1741 | -84.5 | -1352.3 | -1432.6 | 1267.9 | -0.10 / -1.62 / -1.72 | 1694.7 / 579.8 |
| PL 10 30m WT[20, 3.0, 100] exit=ADRtrail0.2 | negative pre-2023 | 1983 | -297.1 | -932.3 | -975.3 | 635.2 | -0.46 / -1.41 / -1.47 | 841.8 / 280.4 |
| HO 1 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1818 | 127.2 | -30.1 | -4.6 | 157.4 | 0.18 / -0.05 / -0.01 | 430.3 / 308.8 |
| HO 2 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | positive pre-2023 | 3111 | 421.4 | 42.3 | 105.6 | 379.1 | 0.74 / 0.08 / 0.19 | 546.4 / 253.4 |
| HO 3 30m ST[14, 3.0, 200] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 1824 | 367.4 | -11.9 | 49.0 | 379.3 | 0.49 / -0.01 / 0.07 | 605.7 / 314.8 |
| HO 4 5m WT[14, 2.0, 100] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 13116 | 184.2 | -199.1 | -135.4 | 383.2 | 0.63 / -0.68 / -0.46 | 402.2 / 113.9 |
| HO 5 5m WT[20, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 10824 | 223.6 | -64.1 | -17.2 | 287.7 | 0.76 / -0.22 / -0.06 | 295.1 / 78.0 |
| HO 6 5m WT[14, 2.0, 100] exit=ADRtrail0.2 | gross-positive, cost-negative pre-2023 | 10633 | 247.4 | -39.5 | 7.3 | 286.9 | 0.82 / -0.14 / 0.02 | 297.7 / 81.2 |
| HO 7 5m WT[20, 2.0, 100] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 13358 | 134.8 | -249.4 | -185.5 | 384.1 | 0.47 / -0.88 / -0.65 | 354.1 / 65.4 |
| HO 8 30m ST[14, 3.0, 200] exit=ADRtrail0.2 | positive pre-2023 | 1824 | 315.3 | 30.8 | 76.5 | 284.5 | 0.42 / 0.04 / 0.10 | 359.1 / 141.0 |
| HO 9 (diag) 30m ST[14, 2.0, 200] exit=ADRtrail0.2 | positive pre-2023 | 2968 | 471.2 | 186.1 | 233.2 | 285.1 | 0.81 / 0.32 / 0.40 | 481.6 / 262.4 |
| HO 10 (diag) 30m ST[14, 2.0, 200] exit=ADRtrail0.15 | gross-positive, cost-negative pre-2023 | 2981 | 357.6 | -22.5 | 40.6 | 380.2 | 0.62 / -0.03 / 0.08 | 595.3 / 303.1 |
| RB 1 30m WT[20, 2.0, 100] exit=ADRtrail0.15 | positive pre-2023 | 3081 | 503.3 | 148.2 | 186.1 | 355.1 | 0.83 / 0.24 / 0.31 | 691.3 / 357.6 |
| RB 2 30m WT[14, 2.0, 100] exit=ADRtrail0.15 | positive pre-2023 | 3142 | 565.7 | 210.9 | 249.2 | 354.8 | 0.97 / 0.36 / 0.42 | 661.7 / 326.9 |
| RB 3 30m ST[14, 2.0, 200] exit=ADRtrail0.15 | positive pre-2023 | 2989 | 616.4 | 261.9 | 299.9 | 354.4 | 1.02 / 0.43 / 0.49 | 458.6 / 124.5 |
| RB 4 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 4487 | 155.1 | -11.6 | 5.6 | 166.7 | 0.36 / -0.03 / 0.01 | 214.6 / 66.6 |
| RB 5 (diag) 10m ST[14, 3.0, 200] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 5228 | 200.7 | -331.0 | -273.7 | 531.8 | 0.41 / -0.68 / -0.57 | 751.9 / 252.0 |
| RB 6 (diag) 30m WT[20, 2.0, 100] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 3082 | 342.8 | -189.9 | -133.1 | 532.7 | 0.55 / -0.31 / -0.22 | 712.6 / 212.0 |
| RB 7 (diag) 30m WT[14, 2.0, 100] exit=ADRtrail0.1 | gross-positive, cost-negative pre-2023 | 3144 | 322.2 | -210.1 | -152.5 | 532.3 | 0.53 / -0.36 / -0.26 | 691.1 / 189.0 |
| NG 1 30m ST[14, 3.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 1635 | 509.2 | -57.2 | -88.7 | 566.4 | 0.77 / -0.08 / -0.13 | 896.4 / 460.2 |
| NG 2 30m ST[4, 2.0, 20] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 4350 | 204.7 | -440.7 | -472.1 | 645.4 | 0.50 / -1.05 / -1.12 | 571.9 / 86.5 |
| NG 3 (diag) 30m ST[14, 3.0, 200] exit=ATRtrail2.0 | gross-positive, cost-negative pre-2023 | 1644 | 431.9 | -417.1 | -464.6 | 849.0 | 0.60 / -0.57 / -0.64 | 956.1 / 301.6 |
| NG 4 (diag) 30m ST[14, 2.0, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2630 | 198.8 | -389.3 | -423.7 | 588.0 | 0.38 / -0.73 / -0.79 | 592.0 / 142.5 |
| NG 5 (diag) 30m HM[9, 21, 200] exit=ATRtrail3.0 | gross-positive, cost-negative pre-2023 | 2672 | 367.6 | -237.5 | -266.8 | 605.1 | 0.70 / -0.43 / -0.49 | 583.3 / 124.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HG: 3 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.19, p(top) = 0.37); HO: 8 cells pass the clean rule against a replicate mean of 17.0 (p(count) = 1.00, p(top) = 0.98); NG: 2 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.33, p(top) = 0.43); PL: 12 cells pass the clean rule against a replicate mean of 2.6 (p(count) = 0.00, p(top) = 0.03); RB: 4 cells pass the clean rule against a replicate mean of 7.2 (p(count) = 0.92, p(top) = 0.97); SI: 5 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.01, p(top) = 0.56).
- Of 32 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.07 (PL 30m WT[20, 3.0, 100] exit=ATRtrail2.0); bootstrap lower bound > 0 for 4 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 1 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 17, 'negative pre-2023': 10, 'positive pre-2023': 5}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q3.py (= ap_b1.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q3/ (`Q3_CO_all_selected_scored.csv`).

DONE Q3
