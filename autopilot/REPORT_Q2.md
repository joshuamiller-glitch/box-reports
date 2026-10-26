# REPORT Q2 - Q2: B7 grid on metals/energy (SI, HG, PL, HO, RB, NG)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 48 selected cells (+8 diagnostic) scored on 6 instruments; best non-diagnostic all-in additive uplift at 20% share +0.27; best pair-window standalone Sharpe +1.02.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: SI, HG, PL, HO, RB, NG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HG    |     288 |        288 |        18 |               1.426 |                2 |         10 |            0 |
| HO    |     288 |        288 |        29 |               1.601 |                2 |         10 |            0 |
| NG    |     288 |        288 |         3 |               0.255 |                2 |          3 |            3 |
| PL    |     288 |        288 |         8 |               1.014 |                2 |          8 |            2 |
| RB    |     288 |        288 |        40 |               1.715 |                2 |         10 |            0 |
| SI    |     288 |        288 |         7 |               0.702 |                2 |          7 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SI    |     100 |                    7 |             4.81 |              10 |       0.2  |                       0.433 |            0.576 |           0.896 |     0.76 |       0.668 |                1.584 |
| HG    |     100 |                   18 |             5.02 |              11 |       0    |                       1.09  |            0.547 |           0.805 |     0    |       1.426 |                1.396 |
| PL    |     100 |                    8 |             6.38 |              12 |       0.31 |                       0.585 |            0.572 |           0.836 |     0.45 |       1.014 |                1.523 |
| HO    |     100 |                   29 |            30.57 |              47 |       0.67 |                       0.936 |            1.122 |           1.344 |     0.91 |       1.601 |                2.235 |
| RB    |     100 |                   40 |            27.44 |              43 |       0.01 |                       1.286 |            1.071 |           1.276 |     0.04 |       1.715 |                2.214 |
| NG    |     100 |                    3 |             3.71 |               9 |       0.71 |                       0.133 |            0.577 |           0.917 |     0.99 |       0.232 |                1.512 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI 1 | 10m emax[9, 21] dir=against hold=180m day | 500 | 2 | 0.67 | -1.19 | 0.19 | 0.05 / 1.28 | 0.09 / -0.90 / -0.36 | -0.24 | 0.35 | 0.84 | -0.55 | 0.00 | 804 | NO |
| SI 2 | 5m emax[9, 21] dir=against hold=240m day | 521 | 2 | 0.61 | -1.45 | 0.37 | 0.44 / 1.26 | 0.10 / -0.68 / -0.70 | -0.26 | 0.26 | 0.89 | -0.66 | 0.00 | 837 | NO |
| SI 3 | 10m vwz[2.0, 'globex'] dir=against hold=120m day | 359 | 2 | 0.49 | -1.37 | -0.11 | -0.26 / 0.95 | -0.02 / -2.84 / -0.19 | -0.70 | 0.58 | 0.70 | -1.33 | 0.00 | 530 | NO |
| SI 4 | 10m macd[12, 26] dir=against hold=240m all | 1154 | 2 | 0.42 | -1.43 | -0.23 | -0.59 / 1.40 | 0.06 / -0.61 / -1.28 | -0.52 | -0.13 | 0.59 | -0.83 | 0.00 | 1840 | NO |
| SI 5 | 10m emax[9, 21] dir=against hold=180m all | 1553 | 2 | 0.39 | -1.92 | -0.07 | -0.29 / 1.24 | 0.01 / -0.60 / -0.68 | -0.45 | 0.26 | 0.72 | -0.62 | 0.00 | 2442 | NO |
| SI 6 | 10m emax[9, 21] dir=against hold=240m day | 399 | 2 | 0.31 | -1.04 | -0.05 | -0.22 / 1.61 | 0.04 / -0.17 / -1.05 | -0.32 | 0.45 | 0.63 | -0.62 | 0.00 | 644 | NO |
| SI 7 | 5m don[20] dir=against hold=180m all | 2612 | 2 | 0.14 | -2.43 | 0.53 | 0.83 / 1.02 | 0.01 / 0.38 / -0.41 | -0.34 | 0.28 | 0.99 | -0.47 | 0.00 | 4214 | NO |
| SI 8 (diag) | 5m emax[9, 21] dir=against hold=180m day | 733 | 1 | 0.70 | -1.71 | 0.20 | 0.08 / 1.17 | 0.12 / -0.97 / -0.58 | -0.32 | 0.25 | 0.85 | -0.69 | 0.00 | 1170 | diag |
| SI 9 (diag) | 5m macd[12, 26] dir=against hold=180m day | 650 | 1 | 0.62 | -1.44 | 0.41 | 0.43 / 1.15 | 0.07 / -0.64 / -0.27 | -0.21 | 0.35 | 0.90 | -0.48 | 0.00 | 1042 | diag |
| SI 10 (diag) | 5m macd[12, 26] dir=against hold=240m day | 460 | 1 | 0.51 | -1.10 | 0.61 | 0.84 / 1.35 | 0.04 / 0.01 / -0.43 | -0.11 | 0.34 | 0.90 | -0.45 | 0.00 | 750 | diag |
| HG 1 | 10m macd[12, 26] dir=against hold=180m day | 409 | 2 | 1.43 | -1.04 | 0.05 | -1.37 / 0.61 | 0.24 / -0.74 / -0.39 | -0.13 | -0.08 | 0.87 | -0.25 | 0.00 | 659 | NO |
| HG 2 | 10m macd[12, 26] dir=against hold=240m day | 325 | 2 | 1.38 | -0.82 | 0.49 | -0.77 / 1.10 | 0.26 / -0.49 / -0.12 | 0.02 | -0.26 | 0.92 | -0.11 | 0.17 | 524 | NO |
| HG 3 | 10m macd[12, 26] dir=against hold=120m day | 503 | 2 | 1.34 | -1.16 | 0.43 | -0.56 / 0.63 | 0.22 / -0.61 / -0.01 | -0.06 | -0.49 | 1.00 | -0.13 | 0.00 | 825 | NO |
| HG 4 | 15m emax[9, 21] dir=against hold=180m day | 352 | 2 | 1.14 | -0.81 | 0.04 | -0.96 / 0.77 | 0.18 / -0.60 / -0.44 | -0.15 | 0.03 | 0.86 | -0.27 | 0.00 | 564 | NO |
| HG 5 | 10m emax[9, 21] dir=against hold=240m day | 374 | 2 | 1.12 | -1.14 | 0.28 | -0.91 / 0.97 | 0.21 / -0.54 / -0.23 | -0.05 | -0.09 | 0.90 | -0.18 | 0.50 | 603 | NO |
| HG 6 | 15m emax[9, 21] dir=against hold=240m day | 293 | 2 | 1.02 | -0.57 | 0.32 | -0.76 / 0.75 | 0.19 / -0.47 / -0.17 | -0.03 | -0.10 | 0.97 | -0.15 | 0.83 | 471 | NO |
| HG 7 | 5m don[20] dir=against hold=240m day | 615 | 2 | 1.02 | -0.72 | 0.83 | 0.69 / 0.95 | 0.18 / -0.14 / 0.05 | 0.05 | -0.07 | 0.99 | -0.07 | 0.25 | 981 | NO |
| HG 8 | 15m emax[9, 21] dir=against hold=120m day | 446 | 2 | 0.91 | -0.87 | -0.07 | -0.84 / 0.39 | 0.11 / -0.59 / -0.29 | -0.20 | -0.39 | 0.89 | -0.29 | 0.00 | 719 | NO |
| HG 9 | 15m macd[12, 26] dir=against hold=240m day | 267 | 2 | 0.78 | -0.52 | 0.68 | 0.25 / 1.07 | 0.18 / -0.36 / 0.02 | 0.02 | 0.11 | 0.97 | -0.11 | 0.67 | 428 | NO |
| HG 10 | 15m vwz[2.0, 'globex'] dir=with hold=60m day | 285 | 2 | 0.77 | -1.41 | 0.62 | 0.49 / 0.36 | 0.18 / -0.01 / 0.28 | 0.06 | -0.59 | 1.00 | -0.02 | 0.00 | 448 | NO |
| PL 1 | 15m vwz[2.0, 'globex'] dir=against hold=240m day | 203 | 2 | 1.01 | -0.46 | 0.77 | 0.69 / 1.17 | 0.18 / 0.17 / -0.35 | 0.03 | 0.29 | 1.00 | -0.26 | 0.25 | 326 | NO |
| PL 2 | 15m vwz[2.0, 'globex'] dir=against hold=180m day | 226 | 2 | 0.82 | -0.56 | 0.20 | -0.27 / 1.39 | 0.14 / -0.52 / -0.38 | -0.13 | 0.24 | 0.80 | -0.37 | 0.00 | 362 | NO |
| PL 3 | 10m vwz[2.0, 'globex'] dir=against hold=240m day | 227 | 2 | 0.69 | -0.75 | 0.19 | -0.20 / 1.29 | 0.12 / -0.82 / -0.45 | -0.18 | 0.02 | 0.74 | -0.47 | 0.00 | 359 | NO |
| PL 4 | 10m vwz[2.0, 'globex'] dir=against hold=120m day | 284 | 2 | 0.66 | -1.03 | -0.30 | -0.89 / 1.27 | 0.11 / -2.43 / -0.16 | -0.48 | -0.60 | 0.66 | -1.02 | 0.00 | 460 | NO |
| PL 5 | 10m vwz[2.0, 'globex'] dir=against hold=180m day | 251 | 2 | 0.51 | -0.98 | -0.32 | -0.75 / 1.16 | 0.06 / -2.25 / -0.41 | -0.51 | -0.06 | 0.56 | -1.11 | 0.00 | 400 | NO |
| PL 6 | 15m vwz[2.0, 'globex'] dir=against hold=120m day | 258 | 2 | 0.44 | -0.57 | 0.41 | 0.30 / 1.14 | 0.10 / -0.26 / -0.18 | -0.06 | -0.22 | 0.96 | -0.29 | 0.50 | 418 | NO |
| PL 7 | 15m vwz[2.0, 'globex'] dir=against hold=180m all | 1098 | 2 | 0.29 | -1.57 | -1.01 | -1.86 / 1.18 | -0.01 / -1.35 / -1.29 | -0.64 | -0.19 | 0.15 | -0.87 | 0.00 | 1630 | NO |
| PL 8 | 10m macd[12, 26] dir=with hold=60m day | 605 | 2 | 0.25 | -1.36 | -0.66 | -1.37 / 0.91 | 0.06 / -1.10 / -1.11 | -0.52 | -0.14 | 0.53 | -0.78 | 0.00 | 1007 | NO |
| PL 9 (diag) | 15m rsi[14, 30] dir=against hold=180m day | 324 | 1 | 0.74 | -0.41 | 0.25 | -0.04 / 1.43 | 0.09 / 1.96 / -0.87 | -0.03 | 0.32 | 0.79 | -0.28 | 0.00 | 483 | diag |
| PL 10 (diag) | 15m rsi[14, 30] dir=against hold=120m day | 369 | 1 | 0.59 | -0.40 | 0.23 | 0.06 / 1.27 | 0.04 / 1.69 / -0.91 | -0.09 | 0.03 | 0.80 | -0.30 | 0.00 | 553 | diag |
| HO 1 | 5m don[20] dir=against hold=240m day | 649 | 2 | 1.60 | -0.03 | 0.77 | 0.03 / 1.26 | 0.33 / 0.18 / -0.29 | 0.13 | 0.21 | 0.95 | -0.09 | 1.00 | 1017 | NO |
| HO 2 | 10m emax[9, 21] dir=against hold=240m day | 389 | 2 | 1.05 | 0.26 | 0.26 | -0.95 / 1.14 | 0.18 / 0.49 / -0.61 | 0.02 | 0.23 | 0.77 | -0.15 | 0.50 | 612 | NO |
| HO 3 | 15m emax[9, 21] dir=with hold=240m all | 934 | 2 | 0.98 | -0.08 | 0.83 | 0.91 / 1.75 | 0.08 / -0.33 / 0.73 | 0.11 | 0.41 | 0.91 | -0.11 | 0.00 | 1493 | NO |
| HO 4 | 5m don[20] dir=against hold=120m day | 1372 | 2 | 0.92 | -0.57 | -0.14 | -0.98 / 1.14 | 0.16 / 0.11 / -0.77 | -0.12 | 0.12 | 0.56 | -0.34 | 0.00 | 2167 | NO |
| HO 5 | 10m st[14, 2.0] dir=against hold=180m day | 664 | 2 | 0.90 | 0.40 | 0.25 | -0.29 / 1.25 | 0.13 / 0.13 / -0.31 | -0.01 | -0.13 | 0.72 | -0.24 | 0.33 | 1022 | NO |
| HO 6 | 5m don[20] dir=against hold=180m day | 955 | 2 | 0.87 | -0.58 | 0.81 | 0.72 / 1.27 | 0.19 / 0.17 / 0.25 | 0.16 | 0.26 | 0.97 | -0.03 | 0.25 | 1514 | LEAD |
| HO 7 | 10m emax[9, 21] dir=against hold=180m day | 499 | 2 | 0.81 | 0.19 | -0.00 | -1.16 / 1.35 | 0.12 / 0.29 / -0.45 | -0.03 | 0.03 | 0.64 | -0.21 | 0.00 | 776 | NO |
| HO 8 | 5m don[20] dir=against hold=60m day | 2009 | 2 | 0.77 | -0.96 | 0.27 | -0.16 / 1.34 | 0.11 / 0.06 / -0.17 | -0.04 | -0.06 | 0.89 | -0.19 | 0.50 | 3189 | NO |
| HO 9 | 5m st[14, 2.0] dir=with hold=180m day | 849 | 2 | 0.74 | -0.27 | 0.31 | 0.03 / 1.28 | 0.15 / 0.19 / -0.52 | -0.06 | -0.31 | 0.81 | -0.31 | 0.00 | 1356 | NO |
| HO 10 | 5m don[20] dir=against hold=180m all | 2674 | 2 | 0.73 | -0.76 | -0.19 | -1.15 / 1.46 | 0.17 / -0.59 / -0.34 | -0.13 | 0.29 | 0.61 | -0.30 | 0.00 | 4284 | NO |
| RB 1 | 5m don[20] dir=against hold=180m day | 944 | 2 | 1.72 | -0.45 | 1.02 | 0.56 / 1.28 | 0.31 / 0.14 / 0.22 | 0.22 | -0.08 | 1.00 | 0.03 | 0.50 | 1514 | LEAD(gate3-7 fail: plateau ) |
| RB 2 | 5m don[20] dir=against hold=240m day | 655 | 2 | 1.60 | 0.03 | 0.77 | 0.02 / 1.40 | 0.28 / 0.17 / -0.09 | 0.15 | -0.09 | 0.96 | -0.05 | 1.00 | 1042 | NO |
| RB 3 | 15m don[20] dir=against hold=180m day | 619 | 2 | 1.45 | -0.53 | 0.87 | 0.51 / 1.69 | 0.22 / 0.05 / 0.03 | 0.13 | -0.19 | 0.92 | -0.10 | 0.50 | 992 | NO |
| RB 4 | 15m macd[12, 26] dir=against hold=240m day | 298 | 2 | 1.43 | -0.38 | 0.60 | -0.28 / 1.27 | 0.23 / 0.20 / -0.45 | 0.05 | -0.23 | 0.91 | -0.13 | 0.33 | 471 | NO |
| RB 5 | 10m st[14, 2.0] dir=against hold=240m all | 1447 | 2 | 1.26 | -0.28 | 0.84 | 0.48 / 1.32 | 0.13 / 0.33 / -0.02 | 0.05 | 0.07 | 0.97 | -0.12 | 0.00 | 2357 | NO |
| RB 6 | 5m vwz[2.0, 'globex'] dir=with hold=180m day | 404 | 2 | 1.17 | -0.62 | 0.69 | 0.35 / 1.24 | 0.15 / 0.19 / -0.04 | 0.08 | -0.33 | 0.97 | -0.10 | 0.75 | 609 | NO |
| RB 7 | 15m emax[9, 21] dir=against hold=240m day | 330 | 2 | 1.07 | -0.04 | 0.29 | -0.63 / 1.64 | 0.17 / 0.12 / -0.58 | -0.02 | -0.28 | 0.77 | -0.21 | 0.00 | 519 | NO |
| RB 8 | 10m rsi[14, 30] dir=with hold=120m all | 1177 | 2 | 1.07 | -0.50 | 0.61 | 0.09 / 1.09 | 0.19 / 0.30 / -0.39 | 0.01 | 0.10 | 0.99 | -0.14 | 0.50 | 1899 | NO |
| RB 9 | 10m don[20] dir=against hold=120m all | 2626 | 2 | 1.06 | -1.05 | 0.74 | 0.58 / 0.67 | 0.18 / 0.10 / -0.06 | 0.00 | 0.02 | 0.99 | -0.12 | 0.50 | 4282 | NO |
| RB 10 | 15m macd[12, 26] dir=against hold=180m day | 355 | 2 | 1.04 | -0.37 | 0.56 | 0.09 / 1.24 | 0.15 / 0.12 / -0.32 | 0.02 | -0.10 | 0.92 | -0.16 | 0.50 | 562 | NO |
| NG 1 | 5m rsi[14, 30] dir=against hold=180m day | 560 | 2 | 0.23 | -0.23 | -0.22 | -0.99 / 0.46 | 0.08 / 0.09 / -0.37 | -0.13 | -0.23 | 0.91 | -0.20 | 0.00 | 879 | NO |
| NG 2 | 10m don[20] dir=with hold=240m day | 539 | 2 | 0.13 | -0.19 | 0.31 | 0.69 / 0.83 | 0.03 / 0.74 / -0.27 | -0.03 | -0.44 | 0.99 | -0.12 | 0.50 | 853 | NO |
| NG 3 | 15m don[20] dir=with hold=240m day | 492 | 2 | 0.04 | -0.09 | 0.03 | 0.14 / 0.87 | 0.02 / 0.14 / -0.13 | -0.08 | -0.15 | 0.93 | -0.17 | 0.50 | 772 | NO |
| NG 4 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 252 | 1 | 0.26 | -0.64 | -0.52 | -1.62 / 1.19 | -0.03 / -0.55 / -0.49 | -0.29 | 0.42 | 0.51 | -0.41 | 0.00 | 426 | diag |
| NG 5 (diag) | 5m rsi[14, 30] dir=against hold=60m day | 888 | 1 | 0.15 | -1.01 | -0.56 | -1.60 / -0.75 | 0.02 / 0.09 / -0.49 | -0.38 | -0.07 | 1.00 | -0.30 | 0.00 | 1386 | diag |
| NG 6 (diag) | 10m emax[9, 21] dir=with hold=240m day | 371 | 1 | 0.10 | -0.19 | -0.10 | -0.25 / 1.05 | 0.01 / -0.46 / -0.13 | -0.15 | -0.11 | 0.87 | -0.27 | 0.00 | 605 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 48 |
| diagnostic cells read | 8 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 0 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 18 |
| worst-decile corr <= +0.30 | 48 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HG 15m vwz[2.0, 'globex'] dir=with hold=60m day | clean | 0.73 | 1.24 | -123989 | -93454 | 437363 | -225929 | 1.50 | 41.0 | 1.64 | -79509 | 290087 | -84818 |
| HG 15m vwz[2.0, 'globex'] dir=with hold=60m day | H1 | 0.15 | 0.25 | -190159 | -145555 | 475696 | -242386 | 0.12 | 42.9 | 2.82 | -78100 | 144218 | -78287 |
| HG 15m vwz[2.0, 'globex'] dir=with hold=60m day | H2 | 0.79 | 1.34 | -155529 | -132887 | 216177 | -179290 | 1.47 | 36.1 | 2.57 | -79303 | 218987 | -81190 |
| HG 15m vwz[2.0, 'globex'] dir=with hold=60m day | all | 0.62 | 1.03 | -156604 | -115559 | 475696 | -242386 | 2.16 | 40.5 | 2.04 | -79452 | 290087 | -84818 |
| HO 5m don[20] dir=against hold=180m day | clean | 0.93 | 1.49 | -118743 | -103729 | 451038 | -135230 | 1.89 | 41.9 | 1.65 | -85645 | 254967 | -98251 |
| HO 5m don[20] dir=against hold=180m day | H1 | 0.25 | 0.38 | -87122 | -78665 | 373784 | -93156 | 0.13 | 42.9 | 3.00 | -60413 | 146068 | -62824 |
| HO 5m don[20] dir=against hold=180m day | H2 | 0.94 | 1.48 | -250944 | -189433 | 596259 | -363177 | 1.01 | 44.4 | 2.54 | -105093 | 265023 | -107396 |
| HO 5m don[20] dir=against hold=180m day | all | 0.81 | 1.27 | -153984 | -126882 | 596259 | -363177 | 2.52 | 42.9 | 2.05 | -89163 | 265023 | -107396 |
| NG 10m don[20] dir=with hold=240m day | clean | 0.06 | 0.09 | -121059 | -99579 | 473485 | -161487 | 0.11 | 51.4 | 1.49 | -77286 | 262586 | -83318 |
| NG 10m don[20] dir=with hold=240m day | H1 | 2.89 | 6.95 | -82813 | -74379 | 229219 | -107011 | 3.78 | 39.3 | 3.56 | -67424 | 128105 | -82693 |
| NG 10m don[20] dir=with hold=240m day | H2 | -1.90 | -2.26 | -100797 | -93326 | 561659 | -110267 | -0.83 | 63.9 | 2.03 | -79177 | 234722 | -80530 |
| NG 10m don[20] dir=with hold=240m day | all | 0.31 | 0.48 | -114995 | -97741 | 561659 | -161487 | 0.81 | 51.8 | 1.93 | -78797 | 262586 | -83318 |
| PL 15m vwz[2.0, 'globex'] dir=against hold=240m day | clean | 1.19 | 1.97 | -121935 | -96384 | 827442 | -230859 | 1.37 | 41.9 | 1.64 | -85444 | 266734 | -93280 |
| PL 15m vwz[2.0, 'globex'] dir=against hold=240m day | H1 | 1.01 | 2.07 | -337294 | -273177 | 674588 | -363738 | 1.25 | 53.6 | 3.00 | -113984 | 202907 | -149680 |
| PL 15m vwz[2.0, 'globex'] dir=against hold=240m day | H2 | 0.40 | 0.60 | -399100 | -296797 | 1143554 | -544308 | 0.32 | 41.7 | 1.94 | -147593 | 317276 | -169066 |
| PL 15m vwz[2.0, 'globex'] dir=against hold=240m day | all | 0.77 | 1.30 | -268346 | -198080 | 1143554 | -544308 | 2.05 | 43.5 | 1.93 | -108724 | 317276 | -169066 |
| RB 5m don[20] dir=against hold=180m day | clean | 1.51 | 2.61 | -112193 | -97594 | 394965 | -163138 | 3.55 | 41.9 | 1.77 | -83441 | 253615 | -88979 |
| RB 5m don[20] dir=against hold=180m day | H1 | 1.03 | 1.49 | -104512 | -86838 | 295597 | -156951 | 0.69 | 42.9 | 2.96 | -71225 | 166877 | -71880 |
| RB 5m don[20] dir=against hold=180m day | H2 | 0.48 | 0.74 | -237107 | -214733 | 784542 | -250525 | 0.41 | 47.2 | 2.51 | -85457 | 239383 | -92495 |
| RB 5m don[20] dir=against hold=180m day | all | 1.02 | 1.62 | -172757 | -136718 | 784542 | -250525 | 2.45 | 43.5 | 2.12 | -83015 | 253615 | -92495 |
| SI 5m don[20] dir=against hold=180m all | clean | 0.15 | 0.21 | -137527 | -114432 | 578757 | -194588 | 0.24 | 43.8 | 1.47 | -89607 | 237891 | -101038 |
| SI 5m don[20] dir=against hold=180m all | H1 | 1.16 | 4.21 | -186430 | -177196 | 1225149 | -210862 | 1.04 | 60.7 | 3.21 | -71473 | 193694 | -89206 |
| SI 5m don[20] dir=against hold=180m all | H2 | 0.62 | 1.17 | -568962 | -420172 | 2569600 | -811286 | 0.42 | 63.9 | 1.88 | -136756 | 295887 | -151880 |
| SI 5m don[20] dir=against hold=180m all | all | 0.53 | 1.10 | -300184 | -232304 | 2569600 | -811286 | 0.97 | 51.2 | 1.83 | -104033 | 295887 | -151880 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SI 5m don[20] dir=against hold=180m all | -2.1 | -186.1 | -33.1 | -114.8 | -9.8 / 8.5 | 7.7 / 7.5 | NO |
| HG 15m vwz[2.0, 'globex'] dir=with hold=60m day | -18.5 | 10.8 | 26.1 | 22.4 | 19.9 / 27.6 | 29.3 / 29.1 | NO |
| PL 15m vwz[2.0, 'globex'] dir=against hold=240m day | -3.8 | -148.9 | -31.8 | -23.5 | -1.0 / 10.5 | -108.2 / -40.7 | NO |
| HO 5m don[20] dir=against hold=180m day | -13.2 | -18.0 | 6.7 | 14.5 | -8.6 / 14.6 | 48.5 / 49.7 | NO |
| RB 5m don[20] dir=against hold=180m day | -8.5 | 10.5 | 16.0 | 23.3 | 12.5 / 18.4 | 42.3 / 42.3 | NO |
| NG 10m don[20] dir=with hold=240m day | -24.9 | 19.9 | 25.6 | 26.4 | 19.2 / 25.1 | 21.6 / 43.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SI 1 10m emax[9, 21] dir=against hold=180m day | negative pre-2023 | 2542 | -9.1 | -63.5 | -44.4 | 54.4 | -0.17 / -1.19 / -0.83 | 112.8 / 58.5 |
| SI 2 5m emax[9, 21] dir=against hold=240m day | negative pre-2023 | 2671 | -34.1 | -88.4 | -69.5 | 54.4 | -0.56 / -1.45 / -1.14 | 118.9 / 64.5 |
| SI 3 10m vwz[2.0, 'globex'] dir=against hold=120m day | negative pre-2023 | 1699 | -30.8 | -85.2 | -66.1 | 54.4 | -0.50 / -1.37 / -1.07 | 80.9 / 26.6 |
| SI 4 10m macd[12, 26] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 6103 | 9.3 | -45.1 | -26.1 | 54.4 | 0.31 / -1.43 / -0.82 | 79.5 / 25.2 |
| SI 5 10m emax[9, 21] dir=against hold=180m all | gross-positive, cost-negative pre-2023 | 8037 | 8.3 | -46.0 | -27.0 | 54.4 | 0.35 / -1.92 / -1.13 | 70.0 / 15.6 |
| SI 6 10m emax[9, 21] dir=against hold=240m day | negative pre-2023 | 2036 | -12.2 | -66.5 | -47.6 | 54.4 | -0.19 / -1.04 / -0.74 | 88.2 / 33.9 |
| SI 7 5m don[20] dir=against hold=180m all | gross-positive, cost-negative pre-2023 | 13028 | 5.4 | -48.9 | -30.0 | 54.4 | 0.27 / -2.43 / -1.50 | 58.5 / 4.1 |
| SI 8 (diag) 5m emax[9, 21] dir=against hold=180m day | negative pre-2023 | 3809 | -17.6 | -71.9 | -53.0 | 54.4 | -0.42 / -1.71 / -1.26 | 104.2 / 49.8 |
| SI 9 (diag) 5m macd[12, 26] dir=against hold=180m day | negative pre-2023 | 3370 | -11.8 | -66.2 | -47.1 | 54.4 | -0.26 / -1.44 / -1.02 | 102.3 / 48.0 |
| SI 10 (diag) 5m macd[12, 26] dir=against hold=240m day | negative pre-2023 | 2455 | -17.5 | -71.9 | -52.9 | 54.4 | -0.27 / -1.10 / -0.81 | 108.8 / 54.4 |
| HG 1 10m macd[12, 26] dir=against hold=180m day | negative pre-2023 | 2177 | -5.0 | -34.4 | -26.4 | 29.4 | -0.15 / -1.04 / -0.80 | 88.4 / 59.1 |
| HG 2 10m macd[12, 26] dir=against hold=240m day | negative pre-2023 | 1799 | -4.1 | -33.5 | -25.5 | 29.4 | -0.10 / -0.82 / -0.62 | 129.8 / 100.5 |
| HG 3 10m macd[12, 26] dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 2627 | 1.3 | -28.1 | -20.0 | 29.4 | 0.05 / -1.16 / -0.83 | 76.4 / 47.0 |
| HG 4 15m emax[9, 21] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1940 | 1.7 | -27.7 | -19.7 | 29.4 | 0.05 / -0.81 / -0.58 | 79.0 / 49.7 |
| HG 5 10m emax[9, 21] dir=against hold=240m day | negative pre-2023 | 2033 | -13.8 | -43.1 | -35.1 | 29.4 | -0.36 / -1.14 / -0.92 | 104.5 / 75.2 |
| HG 6 15m emax[9, 21] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 1639 | 5.5 | -23.9 | -15.9 | 29.4 | 0.13 / -0.57 / -0.38 | 115.2 / 85.8 |
| HG 7 5m don[20] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 3190 | 5.8 | -23.6 | -15.8 | 29.4 | 0.19 / -0.72 / -0.48 | 85.0 / 55.7 |
| HG 8 15m emax[9, 21] dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 2323 | 7.2 | -22.2 | -14.2 | 29.4 | 0.28 / -0.87 / -0.55 | 53.6 / 24.2 |
| HG 9 15m macd[12, 26] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 1460 | 8.1 | -21.3 | -13.3 | 29.4 | 0.20 / -0.52 / -0.33 | 112.6 / 83.3 |
| HG 10 15m vwz[2.0, 'globex'] dir=with hold=60m day | negative pre-2023 | 1421 | -14.3 | -43.7 | -36.1 | 29.4 | -0.46 / -1.41 / -1.16 | 59.0 / 29.7 |
| PL 1 15m vwz[2.0, 'globex'] dir=against hold=240m day | negative pre-2023 | 1150 | -4.5 | -18.8 | -19.8 | 14.4 | -0.11 / -0.46 / -0.48 | 61.6 / 47.2 |
| PL 2 15m vwz[2.0, 'globex'] dir=against hold=180m day | negative pre-2023 | 1262 | -6.4 | -20.7 | -21.8 | 14.4 | -0.17 / -0.56 / -0.59 | 50.2 / 35.9 |
| PL 3 10m vwz[2.0, 'globex'] dir=against hold=240m day | negative pre-2023 | 1369 | -15.1 | -29.5 | -30.6 | 14.4 | -0.39 / -0.75 / -0.77 | 50.0 / 35.6 |
| PL 4 10m vwz[2.0, 'globex'] dir=against hold=120m day | negative pre-2023 | 1724 | -12.6 | -27.0 | -28.1 | 14.4 | -0.49 / -1.03 / -1.07 | 42.4 / 28.0 |
| PL 5 10m vwz[2.0, 'globex'] dir=against hold=180m day | negative pre-2023 | 1508 | -18.7 | -33.1 | -34.1 | 14.4 | -0.56 / -0.98 / -1.02 | 37.7 / 23.3 |
| PL 6 15m vwz[2.0, 'globex'] dir=against hold=120m day | negative pre-2023 | 1434 | -2.7 | -17.0 | -18.0 | 14.4 | -0.09 / -0.57 / -0.61 | 36.1 / 21.7 |
| PL 7 15m vwz[2.0, 'globex'] dir=against hold=180m all | negative pre-2023 | 5186 | -7.8 | -22.2 | -23.1 | 14.4 | -0.56 / -1.57 / -1.63 | 15.2 / 0.8 |
| PL 8 10m macd[12, 26] dir=with hold=60m day | negative pre-2023 | 3162 | -4.6 | -19.0 | -20.1 | 14.4 | -0.33 / -1.36 / -1.44 | 19.3 / 5.0 |
| PL 9 (diag) 15m rsi[14, 30] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1724 | 2.4 | -12.0 | -13.2 | 14.4 | 0.06 / -0.41 / -0.45 | 37.6 / 23.3 |
| PL 10 (diag) 15m rsi[14, 30] dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 1952 | 4.3 | -10.0 | -11.2 | 14.4 | 0.15 / -0.40 / -0.45 | 27.4 / 13.1 |
| HO 1 5m don[20] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 3219 | 11.4 | -1.3 | 0.1 | 12.8 | 0.15 / -0.03 / -0.01 | 140.8 / 128.0 |
| HO 2 10m emax[9, 21] dir=against hold=240m day | positive pre-2023 | 2042 | 38.5 | 25.7 | 27.2 | 12.8 | 0.38 / 0.26 / 0.27 | 120.2 / 107.4 |
| HO 3 15m emax[9, 21] dir=with hold=240m all | gross-positive, cost-negative pre-2023 | 4759 | 8.5 | -4.3 | -2.7 | 12.8 | 0.17 / -0.08 / -0.05 | 47.3 / 34.5 |
| HO 4 5m don[20] dir=against hold=120m day | negative pre-2023 | 6949 | -4.0 | -16.8 | -15.3 | 12.8 | -0.14 / -0.57 / -0.52 | 39.5 / 26.7 |
| HO 5 10m st[14, 2.0] dir=against hold=180m day | positive pre-2023 | 3282 | 37.9 | 25.2 | 26.6 | 12.8 | 0.60 / 0.40 / 0.43 | 62.8 / 50.1 |
| HO 6 5m don[20] dir=against hold=180m day | negative pre-2023 | 4811 | -14.1 | -26.9 | -25.4 | 12.8 | -0.30 / -0.58 / -0.55 | 61.1 / 48.4 |
| HO 7 10m emax[9, 21] dir=against hold=180m day | positive pre-2023 | 2516 | 26.8 | 14.1 | 15.6 | 12.8 | 0.36 / 0.19 / 0.21 | 77.6 / 64.8 |
| HO 8 5m don[20] dir=against hold=60m day | negative pre-2023 | 9973 | -3.9 | -16.7 | -15.2 | 12.8 | -0.23 / -0.96 / -0.87 | 28.0 / 15.3 |
| HO 9 5m st[14, 2.0] dir=with hold=180m day | negative pre-2023 | 4367 | -4.3 | -17.1 | -15.6 | 12.8 | -0.07 / -0.27 / -0.25 | 47.0 / 34.2 |
| HO 10 5m don[20] dir=against hold=180m all | negative pre-2023 | 13130 | -4.0 | -16.7 | -15.2 | 12.8 | -0.18 / -0.76 / -0.69 | 29.5 / 16.7 |
| RB 1 5m don[20] dir=against hold=180m day | negative pre-2023 | 4849 | -6.3 | -19.0 | -18.1 | 12.8 | -0.16 / -0.45 / -0.43 | 66.3 / 53.5 |
| RB 2 5m don[20] dir=against hold=240m day | positive pre-2023 | 3249 | 15.3 | 2.6 | 3.5 | 12.8 | 0.22 / 0.03 / 0.05 | 97.5 / 84.8 |
| RB 3 15m don[20] dir=against hold=180m day | negative pre-2023 | 3130 | -19.7 | -32.4 | -31.6 | 12.8 | -0.32 / -0.53 / -0.52 | 74.7 / 61.9 |
| RB 4 15m macd[12, 26] dir=against hold=240m day | negative pre-2023 | 1491 | -25.2 | -38.0 | -37.1 | 12.8 | -0.25 / -0.38 / -0.37 | 114.6 / 101.8 |
| RB 5 10m st[14, 2.0] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 7012 | 3.5 | -9.2 | -8.2 | 12.8 | 0.10 / -0.28 / -0.25 | 48.5 / 35.8 |
| RB 6 5m vwz[2.0, 'globex'] dir=with hold=180m day | negative pre-2023 | 2091 | -32.7 | -45.4 | -44.7 | 12.8 | -0.45 / -0.62 / -0.61 | 75.4 / 62.7 |
| RB 7 15m emax[9, 21] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 1676 | 9.1 | -3.6 | -2.6 | 12.8 | 0.11 / -0.04 / -0.03 | 91.6 / 78.8 |
| RB 8 10m rsi[14, 30] dir=with hold=120m all | negative pre-2023 | 5924 | -0.9 | -13.6 | -12.6 | 12.8 | -0.04 / -0.50 / -0.46 | 36.9 / 24.1 |
| RB 9 10m don[20] dir=against hold=120m all | negative pre-2023 | 12702 | -5.8 | -18.5 | -17.5 | 12.8 | -0.33 / -1.05 / -0.99 | 25.4 / 12.7 |
| RB 10 15m macd[12, 26] dir=against hold=180m day | negative pre-2023 | 1745 | -15.4 | -28.1 | -27.2 | 12.8 | -0.20 / -0.37 / -0.36 | 71.2 / 58.4 |
| NG 1 5m rsi[14, 30] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 2936 | 15.6 | -8.7 | -13.6 | 24.4 | 0.40 / -0.23 / -0.35 | 31.7 / 7.4 |
| NG 2 10m don[20] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 2661 | 15.7 | -8.7 | -13.2 | 24.4 | 0.33 / -0.19 / -0.28 | 26.6 / 2.2 |
| NG 3 15m don[20] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 2452 | 20.0 | -4.3 | -8.9 | 24.4 | 0.42 / -0.09 / -0.18 | 22.9 / -1.4 |
| NG 4 (diag) 10m vwz[2.0, 'globex'] dir=with hold=240m day | negative pre-2023 | 1083 | -29.6 | -53.9 | -59.5 | 24.4 | -0.35 / -0.64 / -0.70 | 38.6 / 14.2 |
| NG 5 (diag) 5m rsi[14, 30] dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 4611 | 3.5 | -20.9 | -25.7 | 24.4 | 0.17 / -1.01 / -1.25 | 26.1 / 1.8 |
| NG 6 (diag) 10m emax[9, 21] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1931 | 11.9 | -12.5 | -16.9 | 24.4 | 0.18 / -0.19 / -0.25 | 24.7 / 0.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HG: 18 cells pass the clean rule against a replicate mean of 5.0 (p(count) = 0.00, p(top) = 0.00); HO: 29 cells pass the clean rule against a replicate mean of 30.6 (p(count) = 0.67, p(top) = 0.91); NG: 3 cells pass the clean rule against a replicate mean of 3.7 (p(count) = 0.71, p(top) = 0.99); PL: 8 cells pass the clean rule against a replicate mean of 6.4 (p(count) = 0.31, p(top) = 0.45); RB: 40 cells pass the clean rule against a replicate mean of 27.4 (p(count) = 0.01, p(top) = 0.04); SI: 7 cells pass the clean rule against a replicate mean of 4.8 (p(count) = 0.20, p(top) = 0.76).
- Of 48 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.27 (RB 5m don[20] dir=against hold=180m day); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 6; gate_add PASS at some share: 1 (cell-share pairs).
- Gate-3 cell HO 5m don[20] dir=against hold=180m day: uplift +0.19/+0.17/+0.25, boot lo -0.03, plateau 0.25, 2x-slip +0.16, wd corr +0.26, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell RB 5m don[20] dir=against hold=180m day: uplift +0.31/+0.14/+0.22, boot lo +0.03, plateau 0.50, 2x-slip +0.22, wd corr -0.08, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 28, 'gross-positive, cost-negative pre-2023': 16, 'positive pre-2023': 4}.

- **Manual review of the two gate-3 cells (RB 1 and HO 6: 5-minute Donchian-20 breakout traded AGAINST, held 180 minutes, no stop, day session).** RB: clean Sharpe 1.72, uplift +0.31 / +0.14 / +0.22 at 20%, bootstrap lower bound +0.03, plateau 0.50, 2x-slip +0.22, worst-decile correlation -0.08; HO: +0.19 / +0.17 / +0.25, bootstrap lower bound -0.03, plateau 0.25, worst-decile correlation +0.26. Replication (amendment 2): RB: alternating months hold (odd +0.22, even +0.19 vs +0.26) but H0 2023-02..07 standalone -0.98, ES -0.08, RTY +0.07: 1 of 4; HO: H0 +0.61 holds, alternating months fail (odd -0.06), ES/RTY as above: 1 of 4. RB and HO are two refined products of the same crude complex (highly correlated), so they are one independent observation. ERA flag: negative pre-2023 for both. Cross-section of the same cell (5-min Donchian-20 fade, 180-min hold, day session, vol-matched, additive 20%, all-in uplift): NQ +0.14, RTY +0.07, SI +0.06, HG +0.03, HO +0.19, RB +0.26 positive; ES -0.08, YM -0.03, GC -0.09, CL -0.01, ZN -0.62, PL -0.12, NG -0.38, BTC -0.14, ETH -0.07 negative: positive in 6 of 15 markets, so this is not a general 'fade 5-minute breakouts' effect, but it is the same trade family as the GC 5-minute Supertrend fade (fade a fresh 5-minute trend event during the day session and hold about 3 hours), which is why the two energy cells are worth the pre-registered GC v2 battery treatment rather than dismissal. Verdict stays LEAD (weak): the plateau, bootstrap/replication gates fail.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q2.py (= ap_b7.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q2/ (`Q2_CO_all_selected_scored.csv`).

DONE Q2
