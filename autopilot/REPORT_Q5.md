# REPORT Q5 - Q5: B7 grid on FX (6E, 6J, 6B, 6A, 6C)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 16 selected cells (+12 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +0.18; best pair-window standalone Sharpe +0.95.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: 6E, 6J, 6B, 6A, 6C. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |     288 |        288 |         0 |               0.438 |                1 |          0 |            3 |
| 6B    |     288 |        288 |         6 |               0.821 |                2 |          6 |            3 |
| 6C    |     288 |        288 |         0 |              -0.152 |                1 |          0 |            3 |
| 6E    |     288 |        288 |        10 |               1.05  |                2 |         10 |            0 |
| 6J    |     288 |        288 |         0 |               0.332 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| 6E    |     100 |                   10 |             1.59 |               4 |          0 |                       0.671 |            0.543 |           0.96  |     0.23 |       1.05  |                1.215 |
| 6J    |     100 |                    0 |             0.58 |               3 |          1 |                     nan     |            0.445 |           1.124 |   nan    |     nan     |                1.357 |
| 6B    |     100 |                    6 |             0.12 |               2 |          0 |                       0.415 |            0.578 |           1.188 |     0.06 |       0.821 |                1.188 |
| 6A    |     100 |                    0 |             0.01 |               1 |          1 |                     nan     |            0.845 |           0.845 |   nan    |     nan     |                0.845 |
| 6C    |     100 |                    0 |             0.07 |               1 |          1 |                     nan     |            0.297 |           0.438 |   nan    |     nan     |                0.438 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 304 | 2 | 1.05 | -0.55 | 0.95 | 0.94 / 0.55 | 0.19 / 0.09 / 0.26 | 0.09 | -0.04 | 1.00 | 0.02 | 0.25 | 480 | NO |
| 6E 2 | 10m vwz[2.0, 'globex'] dir=with hold=180m day | 344 | 2 | 1.01 | -0.30 | 0.81 | 0.63 / 0.06 | 0.15 / -0.02 / 0.22 | 0.02 | 0.23 | 1.00 | -0.05 | 0.50 | 545 | NO |
| 6E 3 | 15m vwz[2.0, 'globex'] dir=with hold=180m day | 313 | 2 | 0.90 | -0.21 | 0.33 | -0.58 / -0.01 | 0.18 / -0.41 / -0.03 | -0.08 | -0.07 | 1.00 | -0.13 | 0.50 | 490 | NO |
| 6E 4 | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 270 | 2 | 0.86 | -0.38 | 0.47 | -0.10 / 0.40 | 0.17 / -0.31 / 0.12 | -0.01 | -0.34 | 0.99 | -0.08 | 0.00 | 426 | NO |
| 6E 5 | 5m vwz[2.0, 'globex'] dir=with hold=240m day | 350 | 2 | 0.74 | -0.43 | 0.54 | 0.33 / 0.25 | 0.12 / -0.06 / 0.13 | -0.01 | -0.01 | 1.00 | -0.07 | 0.50 | 554 | NO |
| 6E 6 | 15m rsi[14, 30] dir=with hold=240m day | 276 | 2 | 0.74 | -0.17 | 0.37 | -0.12 / 0.59 | 0.11 / -0.34 / 0.19 | -0.02 | 0.19 | 0.97 | -0.09 | 0.17 | 430 | NO |
| 6E 7 | 15m rsi[14, 30] dir=with hold=180m day | 317 | 2 | 0.65 | -0.43 | 0.17 | -0.54 / -0.22 | 0.10 / -0.43 / 0.13 | -0.07 | 0.35 | 1.00 | -0.13 | 0.17 | 495 | NO |
| 6E 8 | 10m rsi[14, 30] dir=with hold=240m day | 316 | 2 | 0.45 | -0.29 | 0.42 | 0.54 / 0.15 | 0.09 / -0.09 / 0.21 | 0.01 | -0.05 | 1.00 | -0.07 | 0.33 | 497 | NO |
| 6E 9 | 15m macd[12, 26] dir=against hold=180m day | 333 | 2 | 0.21 | -0.11 | -0.32 | -1.56 / 0.38 | 0.03 / -0.49 / -0.13 | -0.18 | -0.32 | 0.93 | -0.23 | 0.00 | 521 | NO |
| 6E 10 | 15m macd[12, 26] dir=against hold=240m day | 276 | 2 | 0.10 | -0.03 | -0.24 | -1.12 / 0.54 | 0.00 / -0.48 / -0.04 | -0.16 | -0.20 | 0.86 | -0.23 | 0.00 | 430 | NO |
| 6J 1 (diag) | 15m macd[12, 26] dir=with hold=240m day | 261 | 1 | 0.33 | -0.13 | -0.18 | -1.43 / 0.00 | -0.00 / 0.09 / -0.32 | -0.20 | 0.31 | 0.95 | -0.24 | 0.00 | 416 | diag |
| 6J 2 (diag) | 5m vwz[2.0, 'globex'] dir=with hold=240m day | 290 | 1 | 0.19 | -0.88 | -0.54 | -1.95 / 0.08 | 0.04 / -0.54 / -0.16 | -0.19 | -0.20 | 0.94 | -0.26 | 0.00 | 434 | diag |
| 6J 3 (diag) | 5m vwz[2.0, 'globex'] dir=with hold=120m day | 406 | 1 | 0.12 | -1.22 | -0.44 | -1.68 / -1.62 | 0.03 / -0.37 / -0.11 | -0.22 | -0.33 | 1.00 | -0.22 | 0.00 | 622 | diag |
| 6B 1 | 5m don[20] dir=against hold=240m day | 621 | 2 | 0.82 | -1.36 | 0.21 | -1.07 / -0.90 | 0.16 / -0.38 / -0.01 | -0.15 | -0.26 | 1.00 | -0.14 | 0.25 | 983 | NO |
| 6B 2 | 5m rsi[14, 30] dir=with hold=240m day | 421 | 2 | 0.65 | -0.96 | 0.10 | -0.66 / -0.44 | 0.11 / -0.19 / -0.12 | -0.15 | -0.32 | 1.00 | -0.17 | 0.00 | 664 | NO |
| 6B 3 | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 298 | 2 | 0.45 | -0.79 | -0.18 | -1.10 / 0.00 | 0.08 / -0.24 / -0.20 | -0.18 | -0.12 | 0.99 | -0.22 | 0.00 | 467 | NO |
| 6B 4 | 15m don[20] dir=against hold=240m day | 444 | 2 | 0.32 | -0.71 | -0.40 | -1.83 / -0.26 | 0.11 / -0.56 / -0.19 | -0.22 | -0.19 | 1.00 | -0.23 | 0.00 | 708 | NO |
| 6B 5 | 15m rsi[14, 30] dir=with hold=240m day | 251 | 2 | 0.15 | -1.08 | -0.14 | -0.71 / 0.08 | 0.04 / -0.53 / 0.09 | -0.15 | 0.21 | 0.99 | -0.21 | 0.00 | 403 | NO |
| 6B 6 | 10m rsi[14, 30] dir=with hold=240m day | 287 | 2 | 0.10 | -0.93 | -0.41 | -1.25 / -0.20 | -0.01 / -0.40 / -0.11 | -0.23 | -0.14 | 0.97 | -0.27 | 0.00 | 460 | NO |
| 6B 7 (diag) | 15m emax[9, 21] dir=against hold=180m day | 402 | 1 | 0.25 | -1.08 | -0.45 | -1.94 / -0.71 | -0.02 / -0.13 / -0.39 | -0.32 | -0.41 | 1.00 | -0.30 | 0.00 | 624 | diag |
| 6B 8 (diag) | 15m macd[12, 26] dir=against hold=240m day | 300 | 1 | 0.11 | -0.45 | -0.32 | -1.30 / -0.30 | -0.01 / -0.22 / -0.16 | -0.23 | -0.35 | 1.00 | -0.25 | 0.00 | 463 | diag |
| 6B 9 (diag) | 5m rsi[14, 30] dir=with hold=180m day | 534 | 1 | 0.05 | -1.34 | -0.42 | -1.03 / -1.36 | 0.01 / -0.32 / -0.20 | -0.28 | -0.23 | 1.00 | -0.26 | 0.00 | 832 | diag |
| 6A 1 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 238 | 1 | 0.44 | -0.77 | -0.37 | -1.53 / -0.87 | 0.01 / -0.33 / -0.24 | -0.36 | -0.12 | 1.00 | -0.30 | 0.00 | 371 | diag |
| 6A 2 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m day | 268 | 1 | 0.31 | -1.28 | -0.61 | -2.11 / -1.38 | -0.02 / -0.34 / -0.36 | -0.43 | -0.11 | 1.00 | -0.34 | 0.00 | 425 | diag |
| 6A 3 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 262 | 1 | 0.11 | -1.18 | -0.33 | -1.04 / -0.63 | -0.02 / -0.16 / -0.16 | -0.31 | -0.13 | 1.00 | -0.27 | 0.00 | 413 | diag |
| 6C 1 (diag) | 15m emax[9, 21] dir=with hold=240m day | 329 | 1 | -0.15 | -1.00 | -0.37 | -0.79 / -0.51 | 0.01 / -0.10 / -0.22 | -0.23 | -0.16 | 0.98 | -0.22 | 0.00 | 533 | diag |
| 6C 2 (diag) | 15m st[14, 2.0] dir=with hold=240m day | 451 | 0 | -0.50 | -1.41 | -1.24 | -2.64 / -0.34 | -0.07 / -0.55 / -0.53 | -0.47 | -0.25 | 0.80 | -0.42 | 0.00 | 718 | diag |
| 6C 3 (diag) | 5m st[14, 2.0] dir=against hold=240m day | 598 | 0 | -0.56 | -0.92 | -0.36 | 0.14 / -1.52 | -0.12 / 0.03 / -0.03 | -0.29 | 0.27 | 1.00 | -0.24 | 0.00 | 954 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 16 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 24 |
| worst-decile corr <= +0.30 | 26 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | clean | 0.05 | 0.08 | -111697 | -96950 | 462533 | -172253 | 0.10 | 46.7 | 1.44 | -91219 | 301924 | -97727 |
| 6A 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H1 | -1.09 | -1.35 | -133290 | -115967 | 558371 | -145984 | -0.42 | 46.4 | 2.67 | -82219 | 148415 | -87186 |
| 6A 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | H2 | -1.00 | -1.19 | -146554 | -104657 | 445502 | -187538 | -0.59 | 47.2 | 2.13 | -90460 | 232223 | -91726 |
| 6A 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | all | -0.33 | -0.48 | -126269 | -104390 | 1116742 | -187538 | -0.41 | 47.0 | 1.77 | -90602 | 301924 | -97727 |
| 6B 5m don[20] dir=against hold=240m day | clean | 0.82 | 1.32 | -107450 | -94254 | 361347 | -122854 | 2.05 | 44.8 | 1.62 | -88445 | 261171 | -101629 |
| 6B 5m don[20] dir=against hold=240m day | H1 | -1.85 | -2.18 | -123360 | -110796 | 479222 | -153079 | -0.80 | 71.4 | 2.45 | -84668 | 169840 | -95661 |
| 6B 5m don[20] dir=against hold=240m day | H2 | -0.34 | -0.43 | -105239 | -87117 | 319031 | -132783 | -0.23 | 50.0 | 2.29 | -79656 | 226423 | -80632 |
| 6B 5m don[20] dir=against hold=240m day | all | 0.21 | 0.31 | -113800 | -97248 | 652234 | -153079 | 0.44 | 50.6 | 1.90 | -87294 | 261171 | -101629 |
| 6C 15m emax[9, 21] dir=with hold=240m day (diag) | clean | -0.18 | -0.24 | -139061 | -112593 | 936561 | -223371 | -0.17 | 50.5 | 1.47 | -81367 | 220966 | -90298 |
| 6C 15m emax[9, 21] dir=with hold=240m day (diag) | H1 | -0.30 | -0.40 | -119413 | -103324 | 427811 | -130551 | -0.14 | 53.6 | 2.73 | -77762 | 151333 | -78408 |
| 6C 15m emax[9, 21] dir=with hold=240m day (diag) | H2 | -1.21 | -1.51 | -105958 | -86696 | 504512 | -129472 | -0.54 | 58.3 | 2.08 | -90400 | 186111 | -90881 |
| 6C 15m emax[9, 21] dir=with hold=240m day (diag) | all | -0.37 | -0.49 | -133629 | -107593 | 1334958 | -223371 | -0.37 | 52.4 | 1.81 | -83300 | 220966 | -90881 |
| 6E 10m vwz[2.0, 'globex'] dir=with hold=240m day | clean | 0.92 | 1.63 | -106402 | -88048 | 348625 | -130945 | 2.43 | 44.8 | 1.65 | -82992 | 222040 | -98827 |
| 6E 10m vwz[2.0, 'globex'] dir=with hold=240m day | H1 | 0.61 | 1.00 | -115870 | -108683 | 310975 | -132402 | 0.55 | 39.3 | 2.91 | -81600 | 149365 | -96800 |
| 6E 10m vwz[2.0, 'globex'] dir=with hold=240m day | H2 | 1.34 | 2.39 | -82732 | -72773 | 213938 | -97442 | 1.49 | 44.4 | 2.55 | -79820 | 218807 | -82145 |
| 6E 10m vwz[2.0, 'globex'] dir=with hold=240m day | all | 0.95 | 1.62 | -108570 | -91369 | 348625 | -132402 | 3.83 | 43.5 | 2.04 | -83822 | 222040 | -98827 |
| 6J 5m vwz[2.0, 'globex'] dir=with hold=120m day (diag) | clean | 0.07 | 0.11 | -126300 | -102531 | 474759 | -169149 | 0.13 | 56.2 | 1.49 | -85554 | 260815 | -100504 |
| 6J 5m vwz[2.0, 'globex'] dir=with hold=120m day (diag) | H1 | -1.85 | -1.97 | -119516 | -113183 | 440082 | -122106 | -0.83 | 42.9 | 2.46 | -87382 | 163613 | -95576 |
| 6J 5m vwz[2.0, 'globex'] dir=with hold=120m day (diag) | H2 | -1.51 | -1.91 | -83514 | -69426 | 508424 | -91674 | -0.56 | 58.3 | 2.19 | -85489 | 222493 | -93563 |
| 6J 5m vwz[2.0, 'globex'] dir=with hold=120m day (diag) | all | -0.44 | -0.64 | -127090 | -106166 | 1154198 | -169149 | -0.51 | 54.2 | 1.80 | -86850 | 260815 | -100504 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| 6E 10m vwz[2.0, 'globex'] dir=with hold=240m day | -15.1 | -5.0 | 18.8 | 44.9 | -5.8 / 20.3 | -6.9 / 17.3 | NO |
| 6J 5m vwz[2.0, 'globex'] dir=with hold=120m day (diag) | -36.6 | -8.0 | 13.5 | 26.4 | -8.9 / 14.4 | -4.5 / 11.1 | NO |
| 6B 5m don[20] dir=against hold=240m day | -26.8 | -10.0 | 12.1 | 37.9 | -10.9 / 10.3 | -4.7 / 13.7 | NO |
| 6A 10m vwz[2.0, 'globex'] dir=with hold=240m day (diag) | -35.1 | -4.8 | 3.6 | 17.7 | -5.7 / 0.9 | 11.6 / 21.1 | NO |
| 6C 15m emax[9, 21] dir=with hold=240m day (diag) | -35.5 | 9.6 | 20.8 | 36.3 | 9.9 / 22.5 | 29.8 / 29.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| 6E 1 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1461 | -1.4 | -18.3 | -19.4 | 16.9 | -0.05 / -0.55 / -0.59 | 40.8 / 23.9 |
| 6E 2 10m vwz[2.0, 'globex'] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1692 | 9.2 | -7.6 | -8.8 | 16.9 | 0.34 / -0.30 / -0.35 | 35.3 / 18.4 |
| 6E 3 15m vwz[2.0, 'globex'] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1490 | 10.9 | -5.9 | -7.1 | 16.9 | 0.40 / -0.21 / -0.26 | 32.1 / 15.2 |
| 6E 4 15m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1302 | 3.9 | -13.0 | -14.1 | 16.9 | 0.12 / -0.38 / -0.41 | 35.0 / 18.2 |
| 6E 5 5m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1710 | 3.1 | -13.8 | -15.0 | 16.9 | 0.09 / -0.43 / -0.46 | 32.8 / 15.9 |
| 6E 6 15m rsi[14, 30] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1310 | 10.5 | -6.4 | -7.6 | 16.9 | 0.28 / -0.17 / -0.21 | 33.4 / 16.6 |
| 6E 7 15m rsi[14, 30] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1481 | 4.5 | -12.4 | -13.6 | 16.9 | 0.15 / -0.43 / -0.47 | 28.1 / 11.2 |
| 6E 8 10m rsi[14, 30] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1556 | 7.2 | -9.7 | -10.9 | 16.9 | 0.21 / -0.29 / -0.32 | 27.4 / 10.6 |
| 6E 9 15m macd[12, 26] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1610 | 13.5 | -3.3 | -4.5 | 16.9 | 0.50 / -0.11 / -0.16 | 22.2 / 5.3 |
| 6E 10 15m macd[12, 26] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 1373 | 15.6 | -1.2 | -2.4 | 16.9 | 0.51 / -0.03 / -0.07 | 20.3 / 3.5 |
| 6J 1 (diag) 15m macd[12, 26] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1394 | 13.4 | -3.4 | -9.0 | 16.9 | 0.52 / -0.13 / -0.34 | 24.0 / 7.1 |
| 6J 2 (diag) 5m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1577 | -6.5 | -23.3 | -28.7 | 16.9 | -0.24 / -0.88 / -1.08 | 20.1 / 3.3 |
| 6J 3 (diag) 5m vwz[2.0, 'globex'] dir=with hold=120m day | negative pre-2023 | 2282 | -5.1 | -21.9 | -27.4 | 16.9 | -0.28 / -1.22 / -1.52 | 17.8 / 1.0 |
| 6B 1 5m don[20] dir=against hold=240m day | negative pre-2023 | 3024 | -2.6 | -19.4 | -20.8 | 16.9 | -0.18 / -1.36 / -1.46 | 27.1 / 10.3 |
| 6B 2 5m rsi[14, 30] dir=with hold=240m day | negative pre-2023 | 1976 | -0.9 | -17.7 | -19.2 | 16.9 | -0.05 / -0.96 / -1.04 | 24.8 / 7.9 |
| 6B 3 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1321 | -0.1 | -17.0 | -18.3 | 16.9 | -0.01 / -0.79 / -0.85 | 21.5 / 4.7 |
| 6B 4 15m don[20] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 2113 | 4.1 | -12.8 | -14.1 | 16.9 | 0.22 / -0.71 / -0.78 | 21.3 / 4.4 |
| 6B 5 15m rsi[14, 30] dir=with hold=240m day | negative pre-2023 | 1156 | -7.7 | -24.6 | -26.0 | 16.9 | -0.34 / -1.08 / -1.14 | 19.4 / 2.5 |
| 6B 6 10m rsi[14, 30] dir=with hold=240m day | negative pre-2023 | 1399 | -4.6 | -21.4 | -22.9 | 16.9 | -0.20 / -0.93 / -1.00 | 17.2 / 0.4 |
| 6B 7 (diag) 15m emax[9, 21] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1801 | 0.4 | -16.5 | -17.9 | 16.9 | 0.02 / -1.08 / -1.18 | 19.1 / 2.2 |
| 6B 8 (diag) 15m macd[12, 26] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 1283 | 7.6 | -9.2 | -10.6 | 16.9 | 0.37 / -0.45 / -0.52 | 18.1 / 1.3 |
| 6B 9 (diag) 5m rsi[14, 30] dir=with hold=180m day | negative pre-2023 | 2356 | -3.7 | -20.6 | -22.0 | 16.9 | -0.25 / -1.34 / -1.43 | 16.2 / -0.7 |
| 6A 1 (diag) 15m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1104 | 6.5 | -17.9 | -21.7 | 24.4 | 0.28 / -0.77 / -0.93 | 29.6 / 5.3 |
| 6A 2 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m day | negative pre-2023 | 1250 | -1.9 | -26.3 | -30.0 | 24.4 | -0.09 / -1.28 / -1.46 | 27.4 / 3.1 |
| 6A 3 (diag) 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1249 | -2.9 | -27.2 | -31.0 | 24.4 | -0.12 / -1.18 / -1.34 | 25.2 / 0.8 |
| 6C 1 (diag) 15m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 1698 | -2.8 | -17.1 | -18.4 | 14.4 | -0.16 / -1.00 / -1.08 | 12.4 / -2.0 |
| 6C 2 (diag) 15m st[14, 2.0] dir=with hold=240m day | negative pre-2023 | 2167 | -7.6 | -22.0 | -23.2 | 14.4 | -0.49 / -1.41 / -1.49 | 9.7 / -4.6 |
| 6C 3 (diag) 5m st[14, 2.0] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 2946 | 2.1 | -12.3 | -13.6 | 14.4 | 0.16 / -0.92 / -1.01 | 9.0 / -5.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6B: 6 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.00, p(top) = 0.06); 6C: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); 6E: 10 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.00, p(top) = 0.23); 6J: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00).
- Of 16 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.18 (6E 10m vwz[2.0, 'globex'] dir=with hold=240m day); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10, 'negative pre-2023': 6}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q5.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q5/ (`Q5_CO_all_selected_scored.csv`).

DONE Q5
