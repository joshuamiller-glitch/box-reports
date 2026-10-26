# REPORT B7 - time-exit-only rule books (entry on a 5-15 min bar signal, exit after 1-4 h, no stop)

**Verdict: LEAD. FOUND 0, LEAD 3, INSURANCE 0.** 56 selected cells (+6 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.54; best pair-window standalone Sharpe +1.66.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: enter on a bar signal (ST(14,2) flip, EMA 9/21 cross, Donchian-20 break, RSI(14) 30/70 cross-in, VWAP-z 2.0 cross, MACD 12/26 zero cross), with or against the signal, hold exactly H minutes, NO stop and no target. Only holds that complete before the 16:55 flatten are taken.
- Instruments: ES, RTY, GC, CL, ZN, YM, BTC. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     288 |        288 |        57 |               1.358 |                2 |         10 |            0 |
| CL    |     288 |        288 |         6 |               0.726 |                2 |          6 |            3 |
| ES    |     288 |        288 |        30 |               1.939 |                2 |         10 |            0 |
| GC    |     288 |        288 |        16 |               1.667 |                2 |         10 |            0 |
| RTY   |     288 |        288 |        38 |               1.399 |                2 |         10 |            0 |
| YM    |     288 |        288 |        27 |               1.401 |                2 |         10 |            0 |
| ZN    |     288 |        288 |         0 |              -0.816 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   30 |           13.16  |              22 |       0    |                       1.419 |            0.724 |           0.951 |    0     |       1.939 |                1.859 |
| RTY   |     200 |                   38 |           18.57  |              33 |       0    |                       1.071 |            0.883 |           1.125 |    0.11  |       1.399 |                1.982 |
| GC    |     200 |                   16 |           15.685 |              26 |       0.51 |                       0.964 |            0.805 |           1.046 |    0.15  |       1.667 |                1.896 |
| CL    |     200 |                    6 |            7.8   |              15 |       0.84 |                       0.437 |            0.597 |           0.854 |    0.91  |       0.726 |                1.71  |
| ZN    |     200 |                    0 |            0     |               0 |       1    |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| YM    |     200 |                   27 |           21.455 |              35 |       0.14 |                       0.915 |            0.935 |           1.171 |    0.54  |       1.401 |                1.948 |
| BTC   |     200 |                   57 |           32.72  |              46 |       0    |                       1.091 |            1.129 |           1.345 |    0.585 |       1.358 |                2.138 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 10m emax[9, 21] dir=with hold=120m day | 662 | 2 | 1.94 | -1.23 | 0.55 | -0.97 / 0.89 | 0.33 / -0.34 / -0.37 | -0.02 | -0.07 | 0.99 | -0.12 | 0.83 | 1036 | NO |
| ES 2 | 5m emax[9, 21] dir=with hold=240m day | 504 | 2 | 1.67 | -0.37 | 0.75 | -0.46 / 1.26 | 0.24 / -0.10 / -0.31 | 0.03 | -0.34 | 0.97 | -0.10 | 0.33 | 809 | NO |
| ES 3 | 10m emax[9, 21] dir=with hold=240m day | 405 | 2 | 1.59 | -0.58 | 0.88 | -0.12 / 1.54 | 0.24 / -0.03 / -0.13 | 0.08 | -0.06 | 0.97 | -0.05 | 1.00 | 649 | NO |
| ES 4 | 10m st[14, 2.0] dir=with hold=180m day | 663 | 2 | 1.44 | -0.84 | 0.99 | 0.38 / 0.83 | 0.29 / 0.29 / -0.11 | 0.14 | 0.43 | 0.98 | 0.04 | 0.33 | 1036 | NO |
| ES 5 | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 284 | 2 | 1.40 | -0.24 | 0.75 | -0.21 / 1.24 | 0.24 / -0.25 / 0.12 | 0.11 | 0.25 | 0.98 | -0.03 | 0.25 | 448 | NO |
| ES 6 | 15m vwz[2.0, 'globex'] dir=with hold=180m day | 366 | 2 | 1.36 | -0.01 | 0.76 | -0.08 / 1.21 | 0.26 / -0.01 / -0.06 | 0.11 | -0.20 | 0.98 | -0.03 | 0.50 | 555 | NO |
| ES 7 | 5m macd[12, 26] dir=with hold=240m day | 482 | 2 | 1.35 | -0.42 | 0.36 | -0.93 / 1.57 | 0.20 / -0.07 / -0.48 | -0.04 | -0.02 | 0.88 | -0.17 | 0.83 | 765 | NO |
| ES 8 | 10m st[14, 2.0] dir=with hold=240m day | 486 | 2 | 1.28 | -0.79 | 0.65 | -0.21 / 1.00 | 0.20 / 0.12 / -0.17 | 0.05 | 0.38 | 0.97 | -0.05 | 0.67 | 771 | NO |
| ES 9 | 5m emax[9, 21] dir=with hold=180m day | 725 | 2 | 1.12 | -0.70 | 0.30 | -0.81 / 1.16 | 0.15 / -0.04 / -0.41 | -0.06 | 0.42 | 0.92 | -0.16 | 0.00 | 1141 | NO |
| ES 10 | 10m macd[12, 26] dir=with hold=240m day | 377 | 2 | 1.04 | -0.77 | 0.48 | -0.20 / 1.13 | 0.15 / 0.00 / -0.20 | 0.00 | -0.09 | 0.88 | -0.14 | 0.50 | 593 | NO |
| RTY 1 | 5m rsi[14, 30] dir=with hold=180m day | 578 | 2 | 1.40 | 0.31 | 1.02 | 0.36 / 0.99 | 0.25 / -0.28 / 0.21 | 0.13 | -0.42 | 1.00 | -0.01 | 0.17 | 940 | NO |
| RTY 2 | 10m rsi[14, 30] dir=with hold=240m day | 393 | 2 | 1.31 | 0.27 | 0.65 | -0.06 / 1.51 | 0.22 / -0.40 / 0.11 | 0.07 | -0.32 | 0.93 | -0.12 | 0.33 | 646 | NO |
| RTY 3 | 5m emax[9, 21] dir=with hold=120m day | 962 | 2 | 1.20 | -0.62 | 0.77 | 0.11 / 0.68 | 0.20 / 0.31 / -0.28 | 0.03 | -0.15 | 1.00 | -0.09 | 0.67 | 1503 | NO |
| RTY 4 | 5m rsi[14, 30] dir=with hold=240m day | 463 | 2 | 1.11 | 0.06 | 0.64 | -0.06 / 1.41 | 0.18 / -0.28 / -0.03 | 0.04 | -0.26 | 0.94 | -0.12 | 0.67 | 753 | NO |
| RTY 5 | 5m emax[9, 21] dir=with hold=180m day | 735 | 2 | 1.01 | -0.69 | 0.65 | 0.07 / 1.15 | 0.17 / 0.27 / -0.31 | 0.04 | -0.10 | 0.97 | -0.08 | 0.50 | 1145 | NO |
| RTY 6 | 5m rsi[14, 30] dir=with hold=120m day | 728 | 2 | 1.00 | 0.29 | 0.70 | 0.28 / 0.89 | 0.14 / -0.64 / 0.40 | 0.03 | -0.07 | 0.99 | -0.09 | 0.50 | 1189 | NO |
| RTY 7 | 5m emax[9, 21] dir=with hold=240m day | 517 | 2 | 0.95 | 0.18 | 0.51 | -0.04 / 1.45 | 0.12 / 0.11 / -0.31 | -0.00 | -0.26 | 0.89 | -0.16 | 0.67 | 817 | NO |
| RTY 8 | 10m rsi[14, 30] dir=with hold=240m all | 932 | 2 | 0.94 | 0.18 | 0.77 | 0.52 / 0.92 | 0.17 / -0.26 / 0.50 | 0.10 | -0.19 | 0.99 | -0.05 | 0.50 | 1501 | NO |
| RTY 9 | 15m emax[9, 21] dir=with hold=60m day | 608 | 2 | 0.93 | -0.29 | 0.80 | 0.60 / 0.32 | 0.17 / 0.23 / -0.03 | 0.07 | -0.23 | 1.00 | -0.05 | 0.50 | 948 | NO |
| RTY 10 | 10m rsi[14, 30] dir=with hold=180m day | 462 | 2 | 0.86 | 0.11 | 0.69 | 0.48 / 1.36 | 0.14 / -0.37 / 0.37 | 0.08 | -0.36 | 0.93 | -0.10 | 0.17 | 757 | NO |
| GC 1 | 5m st[14, 2.0] dir=against hold=240m day | 566 | 2 | 1.67 | 0.04 | 1.66 | 2.04 / 1.34 | 0.23 / 1.28 / 1.00 | 0.49 | 0.08 | 1.00 | 0.22 | 0.33 | 911 | LEAD(gate3-7 fail: plateau ) |
| GC 2 | 5m st[14, 2.0] dir=against hold=180m day | 823 | 2 | 1.64 | -0.08 | 1.38 | 1.40 / 1.54 | 0.24 / 0.62 / 0.70 | 0.31 | 0.16 | 1.00 | 0.12 | 0.50 | 1310 | LEAD(gate3-7 fail: plateau ) |
| GC 3 | 5m st[14, 2.0] dir=against hold=120m day | 1084 | 2 | 1.55 | -0.65 | 0.67 | 0.30 / 1.39 | 0.21 / 0.09 / 0.05 | 0.08 | 0.35 | 0.97 | -0.19 | 0.33 | 1757 | NO |
| GC 4 | 5m macd[12, 26] dir=against hold=240m all | 1586 | 2 | 0.96 | -0.94 | 0.14 | -0.43 / 1.02 | 0.13 / 0.40 / -1.01 | -0.15 | -0.39 | 0.87 | -0.34 | 0.00 | 2541 | NO |
| GC 5 | 5m macd[12, 26] dir=against hold=180m day | 640 | 2 | 0.73 | -0.58 | 1.21 | 1.72 / 1.34 | 0.13 / 0.84 / 0.69 | 0.34 | -0.16 | 1.00 | 0.05 | 0.17 | 1037 | LEAD |
| GC 6 | 10m emax[9, 21] dir=against hold=240m all | 1275 | 2 | 0.72 | -0.77 | -0.09 | -0.69 / 1.36 | 0.04 / -0.34 / -0.72 | -0.26 | -0.03 | 0.66 | -0.45 | 0.00 | 2046 | NO |
| GC 7 | 15m macd[12, 26] dir=with hold=240m day | 285 | 2 | 0.62 | -0.62 | 0.54 | 0.55 / 1.52 | 0.10 / -0.57 / 0.67 | 0.09 | 0.19 | 0.87 | -0.22 | 0.67 | 449 | NO |
| GC 8 | 10m st[14, 2.0] dir=against hold=240m all | 1470 | 2 | 0.59 | -0.68 | 0.03 | -0.31 / 1.29 | 0.09 / -1.19 / -0.13 | -0.23 | -0.12 | 0.80 | -0.51 | 0.00 | 2374 | NO |
| GC 9 | 5m emax[9, 21] dir=with hold=240m day | 526 | 2 | 0.58 | -0.63 | -0.22 | -0.62 / 1.49 | 0.07 / -0.73 / -0.98 | -0.35 | 0.13 | 0.54 | -0.71 | 0.00 | 841 | NO |
| GC 10 | 15m macd[12, 26] dir=with hold=180m day | 324 | 2 | 0.58 | -0.59 | 0.55 | 0.57 / 1.05 | 0.08 / -0.24 / 0.39 | 0.07 | 0.17 | 0.94 | -0.22 | 0.33 | 522 | NO |
| CL 1 | 5m macd[12, 26] dir=against hold=180m day | 631 | 2 | 0.73 | -0.51 | -0.43 | -1.89 / 1.00 | 0.11 / -0.09 / -0.96 | -0.26 | 0.17 | 0.61 | -0.38 | 0.00 | 1000 | NO |
| CL 2 | 5m emax[9, 21] dir=against hold=180m day | 704 | 2 | 0.62 | -0.61 | 0.05 | -0.44 / 0.76 | 0.07 / 0.16 / -0.53 | -0.16 | 0.12 | 0.89 | -0.28 | 0.00 | 1130 | NO |
| CL 3 | 10m vwz[2.0, 'globex'] dir=with hold=240m day | 321 | 2 | 0.44 | -0.33 | 0.90 | 1.40 / 0.80 | 0.08 / -0.00 / 0.70 | 0.16 | -0.29 | 0.99 | -0.00 | 0.25 | 468 | NO |
| CL 4 | 5m vwz[2.0, 'globex'] dir=with hold=240m day | 360 | 2 | 0.32 | -0.37 | 0.41 | 0.53 / 1.06 | 0.06 / 0.08 / 0.31 | 0.06 | -0.33 | 0.98 | -0.11 | 0.25 | 531 | NO |
| CL 5 | 5m macd[12, 26] dir=against hold=240m day | 471 | 2 | 0.29 | -0.06 | -0.75 | -1.88 / 0.91 | 0.01 / 0.33 / -1.29 | -0.33 | 0.18 | 0.25 | -0.52 | 0.00 | 753 | NO |
| CL 6 | 5m emax[9, 21] dir=against hold=240m day | 516 | 2 | 0.22 | -0.12 | -0.21 | -0.63 / 1.28 | -0.02 / 0.45 / -0.63 | -0.17 | 0.06 | 0.57 | -0.33 | 0.00 | 826 | NO |
| CL 7 (diag) | 5m don[20] dir=against hold=240m day | 622 | 1 | 0.50 | -0.12 | 0.29 | 0.15 / 0.96 | 0.09 / 0.12 / -0.00 | -0.00 | 0.05 | 0.92 | -0.14 | 0.50 | 987 | diag |
| CL 8 (diag) | 10m vwz[2.0, 'globex'] dir=with hold=120m day | 448 | 1 | 0.20 | -0.47 | 0.77 | 1.44 / 1.35 | 0.02 / -0.00 / 0.89 | 0.10 | -0.29 | 0.98 | -0.02 | 0.25 | 651 | diag |
| CL 9 (diag) | 10m emax[9, 21] dir=against hold=180m day | 491 | 1 | 0.18 | -0.18 | 0.07 | -0.04 / 0.56 | -0.02 / 0.09 / -0.22 | -0.13 | -0.04 | 0.84 | -0.26 | 0.00 | 786 | diag |
| ZN 1 (diag) | 10m emax[9, 21] dir=with hold=240m day | 376 | 0 | -0.82 | -2.39 | -1.85 | -4.71 / -1.50 | -0.17 / -0.86 / -0.54 | -0.72 | -0.19 | 0.93 | -0.54 | 0.00 | 605 | diag |
| ZN 2 (diag) | 15m macd[12, 26] dir=with hold=240m day | 292 | 0 | -0.84 | -1.98 | -1.52 | -3.19 / -1.81 | -0.16 / -0.59 / -0.54 | -0.62 | 0.11 | 0.99 | -0.48 | 0.00 | 462 | diag |
| ZN 3 (diag) | 15m don[20] dir=against hold=240m day | 469 | 0 | -0.89 | -2.44 | -1.53 | -3.00 / -1.91 | -0.17 / -0.48 / -0.32 | -0.63 | -0.50 | 0.98 | -0.44 | 0.00 | 736 | diag |
| YM 1 | 15m st[14, 2.0] dir=with hold=60m day | 973 | 2 | 1.40 | -0.71 | 0.38 | -0.50 / 1.00 | 0.19 / -0.32 / -0.36 | -0.11 | 0.15 | 0.98 | -0.23 | 0.00 | 1524 | NO |
| YM 2 | 15m macd[12, 26] dir=with hold=240m day | 318 | 2 | 1.12 | -0.68 | 0.27 | -1.10 / 1.25 | 0.19 / 0.03 / -0.50 | -0.01 | -0.06 | 0.78 | -0.18 | 0.17 | 488 | NO |
| YM 3 | 10m st[14, 2.0] dir=with hold=60m day | 1188 | 2 | 1.09 | -0.76 | 0.14 | -0.84 / 0.56 | 0.13 / -0.37 / -0.45 | -0.17 | -0.11 | 0.93 | -0.29 | 0.00 | 1853 | NO |
| YM 4 | 10m st[14, 2.0] dir=with hold=180m all | 1668 | 2 | 1.07 | -1.19 | 0.35 | -0.66 / 0.83 | 0.20 / -0.09 / -0.31 | -0.03 | -0.27 | 0.96 | -0.13 | 0.33 | 2681 | NO |
| YM 5 | 15m st[14, 2.0] dir=with hold=60m all | 1968 | 2 | 0.96 | -1.45 | 0.04 | -0.93 / 0.68 | 0.11 / -0.51 / -0.29 | -0.22 | -0.01 | 0.99 | -0.27 | 0.00 | 3191 | NO |
| YM 6 | 10m macd[12, 26] dir=with hold=180m day | 469 | 2 | 0.76 | -0.54 | -0.11 | -1.38 / 1.81 | 0.13 / -0.08 / -0.48 | -0.07 | -0.02 | 0.60 | -0.23 | 0.00 | 716 | NO |
| YM 7 | 15m vwz[2.0, 'globex'] dir=with hold=240m day | 362 | 2 | 0.76 | 0.17 | 0.33 | -0.29 / 1.07 | 0.12 / -0.32 / -0.02 | 0.01 | 0.55 | 0.85 | -0.14 | 0.25 | 564 | NO |
| YM 8 | 15m st[14, 2.0] dir=with hold=120m all | 1573 | 2 | 0.71 | -0.79 | 1.01 | 1.51 / 0.56 | 0.06 / 0.20 / 0.31 | 0.04 | -0.55 | 1.00 | -0.05 | 0.33 | 2562 | NO |
| YM 9 | 15m st[14, 2.0] dir=with hold=180m all | 1288 | 2 | 0.64 | -0.58 | -0.15 | -1.09 / 1.05 | 0.06 / -0.33 / -0.29 | -0.16 | -0.01 | 0.78 | -0.28 | 0.00 | 2093 | NO |
| YM 10 | 10m st[14, 2.0] dir=with hold=180m day | 675 | 2 | 0.62 | -0.38 | -0.01 | -0.74 / 0.83 | 0.07 / -0.13 / -0.49 | -0.11 | 0.34 | 0.74 | -0.26 | 0.00 | 1051 | NO |
| BTC 1 | 10m don[20] dir=with hold=180m all | 2086 | 2 | 1.36 | -0.28 | 0.46 | -0.96 / 0.93 | 0.24 / 0.23 / -0.51 | -0.03 | 0.19 | 0.97 | -0.13 | 0.00 | 3286 | NO |
| BTC 2 | 10m st[14, 2.0] dir=with hold=120m day | 849 | 2 | 1.33 | 0.36 | 0.15 | -1.69 / 1.57 | 0.28 / -0.81 / -0.22 | -0.03 | -0.18 | 0.79 | -0.18 | 0.67 | 1330 | NO |
| BTC 3 | 5m macd[12, 26] dir=with hold=120m day | 799 | 2 | 1.24 | -0.63 | 0.30 | -0.63 / 1.04 | 0.22 / -1.03 / 0.15 | -0.03 | -0.22 | 0.92 | -0.21 | 0.50 | 1272 | NO |
| BTC 4 | 10m emax[9, 21] dir=with hold=120m all | 1717 | 2 | 1.19 | -1.48 | 0.14 | -1.14 / 0.76 | 0.18 / -0.50 / -0.22 | -0.11 | -0.15 | 0.93 | -0.20 | 0.33 | 2687 | NO |
| BTC 5 | 5m emax[9, 21] dir=with hold=120m day | 908 | 2 | 1.12 | -0.62 | 0.05 | -1.08 / 1.28 | 0.20 / -1.20 / 0.02 | -0.10 | -0.02 | 0.81 | -0.27 | 0.00 | 1452 | NO |
| BTC 6 | 10m rsi[14, 30] dir=against hold=180m all | 985 | 2 | 1.07 | 0.22 | 0.89 | 0.65 / 1.31 | 0.19 / 0.52 / -0.14 | 0.09 | 0.45 | 0.97 | -0.04 | 0.33 | 1537 | NO |
| BTC 7 | 5m rsi[14, 30] dir=against hold=120m all | 1734 | 2 | 0.97 | -0.59 | 0.58 | 0.02 / 1.08 | 0.19 / 0.87 / -0.48 | 0.02 | 0.27 | 0.96 | -0.09 | 0.17 | 2716 | NO |
| BTC 8 | 15m macd[12, 26] dir=with hold=180m day | 329 | 2 | 0.89 | -1.68 | 0.93 | 1.29 / 1.53 | 0.13 / 0.56 / -0.19 | 0.10 | 0.03 | 0.97 | -0.04 | 0.17 | 512 | NO |
| BTC 9 | 10m vwz[2.0, 'globex'] dir=against hold=60m day | 426 | 2 | 0.87 | 0.23 | 1.12 | 1.52 / 0.94 | 0.16 / 0.84 / -0.06 | 0.15 | 0.01 | 1.00 | 0.04 | 0.75 | 634 | NO |
| BTC 10 | 10m vwz[2.0, 'globex'] dir=against hold=180m day | 286 | 2 | 0.86 | 0.76 | 0.92 | 1.06 / 1.05 | 0.11 / 0.30 / -0.05 | 0.09 | 0.38 | 0.98 | -0.09 | 0.50 | 429 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 56 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 2 / 3 / 3 / 3 |
| all-in uplift @20% > 0 (all scored) | 43 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 32 |
| worst-decile corr <= +0.30 | 54 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 11 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 6 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 10m vwz[2.0, 'globex'] dir=against hold=60m day | clean | 0.88 | 1.78 | -87256 | -77586 | 394019 | -126501 | 2.03 | 52.4 | 1.62 | -83799 | 285997 | -89590 |
| BTC 10m vwz[2.0, 'globex'] dir=against hold=60m day | H1 | 3.07 | 8.07 | -74126 | -64369 | 272905 | -97898 | 2.97 | 35.7 | 3.67 | -72969 | 137558 | -87003 |
| BTC 10m vwz[2.0, 'globex'] dir=against hold=60m day | H2 | -0.22 | -0.39 | -66403 | -58367 | 221218 | -67943 | -0.21 | 55.6 | 2.23 | -83324 | 216714 | -84333 |
| BTC 10m vwz[2.0, 'globex'] dir=against hold=60m day | all | 1.12 | 2.33 | -84582 | -73499 | 394019 | -126501 | 3.97 | 50.6 | 2.06 | -84049 | 285997 | -89590 |
| CL 10m vwz[2.0, 'globex'] dir=with hold=240m day | clean | 0.43 | 0.65 | -131631 | -104030 | 434434 | -179284 | 0.90 | 48.6 | 1.54 | -83853 | 238246 | -93771 |
| CL 10m vwz[2.0, 'globex'] dir=with hold=240m day | H1 | -0.61 | -0.93 | -51897 | -50565 | 252463 | -52979 | -0.33 | 53.6 | 2.82 | -73780 | 160815 | -75539 |
| CL 10m vwz[2.0, 'globex'] dir=with hold=240m day | H2 | 2.07 | 3.97 | -244047 | -154917 | 483790 | -394011 | 2.94 | 41.7 | 3.00 | -83201 | 219146 | -90774 |
| CL 10m vwz[2.0, 'globex'] dir=with hold=240m day | all | 0.90 | 1.56 | -150905 | -110952 | 522335 | -394011 | 3.31 | 47.6 | 2.07 | -82816 | 238246 | -93771 |
| ES 10m st[14, 2.0] dir=with hold=180m day | clean | 1.36 | 2.49 | -103514 | -80983 | 295388 | -219729 | 4.20 | 45.7 | 1.75 | -86036 | 293232 | -98982 |
| ES 10m st[14, 2.0] dir=with hold=180m day | H1 | 1.52 | 2.97 | -92391 | -87031 | 333377 | -98074 | 1.21 | 57.1 | 3.12 | -80113 | 159609 | -80371 |
| ES 10m st[14, 2.0] dir=with hold=180m day | H2 | -0.66 | -1.18 | -71291 | -67405 | 398258 | -71912 | -0.48 | 63.9 | 2.19 | -92793 | 224161 | -93787 |
| ES 10m st[14, 2.0] dir=with hold=180m day | all | 0.99 | 1.83 | -98597 | -82674 | 398258 | -219729 | 3.65 | 51.2 | 2.06 | -88299 | 293232 | -98982 |
| GC 5m st[14, 2.0] dir=against hold=240m day | clean | 1.59 | 3.23 | -90258 | -79217 | 351531 | -120251 | 4.12 | 45.7 | 1.69 | -87749 | 250962 | -93745 |
| GC 5m st[14, 2.0] dir=against hold=240m day | H1 | 2.64 | 5.57 | -197711 | -182178 | 441798 | -208711 | 3.37 | 39.3 | 4.11 | -75688 | 142466 | -85955 |
| GC 5m st[14, 2.0] dir=against hold=240m day | H2 | 1.68 | 2.68 | -426684 | -334585 | 565699 | -464489 | 2.80 | 41.7 | 3.30 | -77603 | 221415 | -87673 |
| GC 5m st[14, 2.0] dir=against hold=240m day | all | 1.66 | 2.93 | -235875 | -164463 | 565699 | -464489 | 7.99 | 44.0 | 2.39 | -86408 | 250962 | -93745 |
| RTY 10m rsi[14, 30] dir=with hold=240m all | clean | 1.00 | 1.79 | -96954 | -87276 | 456862 | -112232 | 2.00 | 48.6 | 1.63 | -89243 | 240237 | -96333 |
| RTY 10m rsi[14, 30] dir=with hold=240m all | H1 | -0.38 | -0.56 | -128745 | -115929 | 340418 | -134504 | -0.32 | 46.4 | 2.57 | -89596 | 147477 | -94992 |
| RTY 10m rsi[14, 30] dir=with hold=240m all | H2 | 1.03 | 1.74 | -181518 | -151719 | 560356 | -192318 | 0.95 | 47.2 | 2.79 | -81858 | 228635 | -85570 |
| RTY 10m rsi[14, 30] dir=with hold=240m all | all | 0.77 | 1.29 | -132416 | -111607 | 560356 | -192318 | 2.38 | 48.2 | 2.03 | -88913 | 240237 | -96333 |
| YM 15m st[14, 2.0] dir=with hold=120m all | clean | 0.70 | 1.33 | -87782 | -78919 | 708100 | -108757 | 0.89 | 53.3 | 1.52 | -85855 | 309681 | -99062 |
| YM 15m st[14, 2.0] dir=with hold=120m all | H1 | 1.43 | 2.54 | -92051 | -85566 | 358157 | -103420 | 0.98 | 42.9 | 3.02 | -74661 | 172423 | -76570 |
| YM 15m st[14, 2.0] dir=with hold=120m all | H2 | 1.55 | 2.73 | -95076 | -86969 | 335159 | -102417 | 1.52 | 41.7 | 2.60 | -79122 | 229652 | -82730 |
| YM 15m st[14, 2.0] dir=with hold=120m all | all | 1.01 | 1.86 | -92424 | -84620 | 708100 | -108757 | 2.11 | 48.8 | 1.98 | -83719 | 309681 | -99062 |
| ZN 15m don[20] dir=against hold=240m day (diag) | clean | -0.90 | -1.26 | -110842 | -99779 | 1063904 | -151452 | -0.77 | 58.1 | 1.29 | -90784 | 296041 | -107299 |
| ZN 15m don[20] dir=against hold=240m day (diag) | H1 | -3.26 | -3.20 | -117447 | -107337 | 579684 | -127556 | -1.00 | 57.1 | 2.35 | -76631 | 153371 | -76860 |
| ZN 15m don[20] dir=against hold=240m day (diag) | H2 | -2.76 | -2.96 | -89619 | -85739 | 690953 | -95796 | -0.89 | 66.7 | 1.97 | -80327 | 219716 | -82336 |
| ZN 15m don[20] dir=against hold=240m day (diag) | all | -1.53 | -1.93 | -110638 | -98878 | 2307482 | -151452 | -0.87 | 59.5 | 1.60 | -87698 | 296041 | -107299 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 10m st[14, 2.0] dir=with hold=180m day | -13.8 | -0.5 | 12.5 | 23.0 | -1.3 / 15.8 | 25.6 / 25.2 | NO |
| RTY 10m rsi[14, 30] dir=with hold=240m all | -15.1 | -0.4 | 9.9 | 31.1 | -1.2 / 8.7 | -3.4 / 6.8 | NO |
| GC 5m st[14, 2.0] dir=against hold=240m day | 20.5 | -11.5 | 9.5 | 22.4 | 3.6 / 11.9 | 13.9 / 14.9 | NO |
| CL 10m vwz[2.0, 'globex'] dir=with hold=240m day | -10.7 | 4.9 | 21.2 | 39.1 | 4.1 / 19.2 | 33.9 / 37.4 | NO |
| ZN 15m don[20] dir=against hold=240m day (diag) | -52.5 | -20.4 | 11.5 | 7.1 | -21.3 / 4.7 | 32.2 / 31.9 | NO |
| YM 15m st[14, 2.0] dir=with hold=120m all | -13.3 | -5.1 | 18.5 | 14.2 | -5.9 / 15.1 | 31.9 / 35.7 | NO |
| BTC 10m vwz[2.0, 'globex'] dir=against hold=60m day | -12.5 | 12.9 | 19.4 | 14.8 | 12.2 / 19.4 | 11.9 / 39.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 10m emax[9, 21] dir=with hold=120m day | negative pre-2023 | 3367 | -16.7 | -46.1 | -31.8 | 29.4 | -0.45 / -1.23 / -0.85 | 122.4 / 93.0 |
| ES 2 5m emax[9, 21] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 2685 | 7.2 | -22.2 | -7.9 | 29.4 | 0.12 / -0.37 / -0.13 | 178.9 / 149.5 |
| ES 3 10m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 2073 | -9.9 | -39.2 | -25.0 | 29.4 | -0.15 / -0.58 / -0.37 | 192.6 / 163.2 |
| ES 4 10m st[14, 2.0] dir=with hold=180m day | negative pre-2023 | 3187 | -11.1 | -40.5 | -26.2 | 29.4 | -0.23 / -0.84 / -0.55 | 135.7 / 106.3 |
| ES 5 15m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1234 | 8.5 | -20.9 | -6.9 | 29.4 | 0.10 / -0.24 / -0.08 | 218.5 / 189.2 |
| ES 6 15m vwz[2.0, 'globex'] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1461 | 28.6 | -0.7 | 13.4 | 29.4 | 0.41 / -0.01 / 0.19 | 152.9 / 123.6 |
| ES 7 5m macd[12, 26] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 2461 | 2.8 | -26.6 | -12.3 | 29.4 | 0.04 / -0.42 / -0.19 | 143.6 / 114.3 |
| ES 8 10m st[14, 2.0] dir=with hold=240m day | negative pre-2023 | 2458 | -19.7 | -49.0 | -34.8 | 29.4 | -0.32 / -0.79 / -0.56 | 140.9 / 111.6 |
| ES 9 5m emax[9, 21] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 3785 | 1.1 | -28.3 | -14.1 | 29.4 | 0.02 / -0.70 / -0.35 | 100.7 / 71.3 |
| ES 10 10m macd[12, 26] dir=with hold=240m day | negative pre-2023 | 1844 | -27.3 | -56.7 | -42.4 | 29.4 | -0.37 / -0.77 / -0.58 | 138.3 / 108.9 |
| RTY 1 5m rsi[14, 30] dir=with hold=180m day | positive pre-2023 | 1737 | 27.8 | 13.5 | 15.7 | 14.4 | 0.64 / 0.31 / 0.36 | 86.8 / 72.4 |
| RTY 2 10m rsi[14, 30] dir=with hold=240m day | positive pre-2023 | 1202 | 29.4 | 15.1 | 17.4 | 14.4 | 0.52 / 0.27 / 0.31 | 88.1 / 73.8 |
| RTY 3 5m emax[9, 21] dir=with hold=120m day | negative pre-2023 | 2887 | -2.0 | -16.4 | -14.1 | 14.4 | -0.07 / -0.62 / -0.53 | 48.4 / 34.0 |
| RTY 4 5m rsi[14, 30] dir=with hold=240m day | positive pre-2023 | 1413 | 17.3 | 3.0 | 5.2 | 14.4 | 0.33 / 0.06 / 0.11 | 85.3 / 71.0 |
| RTY 5 5m emax[9, 21] dir=with hold=180m day | negative pre-2023 | 2197 | -9.6 | -24.0 | -21.7 | 14.4 | -0.27 / -0.69 / -0.62 | 59.2 / 44.9 |
| RTY 6 5m rsi[14, 30] dir=with hold=120m day | positive pre-2023 | 2216 | 23.6 | 9.2 | 11.4 | 14.4 | 0.73 / 0.29 / 0.36 | 49.7 / 35.4 |
| RTY 7 5m emax[9, 21] dir=with hold=240m day | positive pre-2023 | 1551 | 23.0 | 8.6 | 10.9 | 14.4 | 0.47 / 0.18 / 0.23 | 61.3 / 46.9 |
| RTY 8 10m rsi[14, 30] dir=with hold=240m all | positive pre-2023 | 2691 | 19.6 | 5.2 | 7.5 | 14.4 | 0.65 / 0.18 / 0.25 | 41.6 / 27.3 |
| RTY 9 15m emax[9, 21] dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 1843 | 6.9 | -7.5 | -5.2 | 14.4 | 0.27 / -0.29 / -0.20 | 39.5 / 25.2 |
| RTY 10 10m rsi[14, 30] dir=with hold=180m day | positive pre-2023 | 1392 | 19.3 | 5.0 | 7.2 | 14.4 | 0.42 / 0.11 / 0.16 | 56.3 / 42.0 |
| GC 1 5m st[14, 2.0] dir=against hold=240m day | positive pre-2023 | 2908 | 26.8 | 2.5 | 12.3 | 24.4 | 0.49 / 0.04 / 0.22 | 156.2 / 131.8 |
| GC 2 5m st[14, 2.0] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 4163 | 21.7 | -2.6 | 7.1 | 24.4 | 0.57 / -0.08 / 0.18 | 121.3 / 96.9 |
| GC 3 5m st[14, 2.0] dir=against hold=120m day | gross-positive, cost-negative pre-2023 | 5513 | 7.4 | -17.0 | -7.2 | 24.4 | 0.27 / -0.65 / -0.28 | 93.0 / 68.6 |
| GC 4 5m macd[12, 26] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 8388 | 3.3 | -21.1 | -11.3 | 24.4 | 0.15 / -0.94 / -0.50 | 66.3 / 42.0 |
| GC 5 5m macd[12, 26] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 3355 | 2.2 | -22.2 | -12.4 | 24.4 | 0.06 / -0.58 / -0.32 | 72.5 / 48.1 |
| GC 6 10m emax[9, 21] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 6824 | 5.3 | -19.1 | -9.3 | 24.4 | 0.21 / -0.77 / -0.38 | 58.1 / 33.8 |
| GC 7 15m macd[12, 26] dir=with hold=240m day | negative pre-2023 | 1499 | -12.9 | -37.3 | -27.6 | 24.4 | -0.21 / -0.62 / -0.46 | 96.1 / 71.7 |
| GC 8 10m st[14, 2.0] dir=against hold=240m all | gross-positive, cost-negative pre-2023 | 7559 | 7.5 | -16.9 | -7.1 | 24.4 | 0.30 / -0.68 / -0.29 | 49.0 / 24.7 |
| GC 9 5m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 2699 | -7.4 | -31.8 | -22.0 | 24.4 | -0.15 / -0.63 / -0.44 | 62.8 / 38.5 |
| GC 10 15m macd[12, 26] dir=with hold=180m day | negative pre-2023 | 1753 | -6.0 | -30.4 | -20.6 | 24.4 | -0.12 / -0.59 / -0.40 | 83.3 / 58.9 |
| CL 1 5m macd[12, 26] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 3304 | 2.4 | -22.0 | -19.4 | 24.4 | 0.05 / -0.51 / -0.45 | 52.4 / 28.0 |
| CL 2 5m emax[9, 21] dir=against hold=180m day | negative pre-2023 | 3705 | -0.9 | -25.3 | -22.7 | 24.4 | -0.03 / -0.61 / -0.55 | 44.0 / 19.6 |
| CL 3 10m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1640 | 1.3 | -23.0 | -20.1 | 24.4 | 0.02 / -0.33 / -0.29 | 51.9 / 27.5 |
| CL 4 5m vwz[2.0, 'globex'] dir=with hold=240m day | gross-positive, cost-negative pre-2023 | 1915 | 0.2 | -24.2 | -21.4 | 24.4 | 0.00 / -0.37 / -0.33 | 42.7 / 18.4 |
| CL 5 5m macd[12, 26] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 2462 | 21.2 | -3.2 | -0.6 | 24.4 | 0.35 / -0.06 / -0.02 | 39.5 / 15.1 |
| CL 6 5m emax[9, 21] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 2641 | 17.4 | -7.0 | -4.3 | 24.4 | 0.29 / -0.12 / -0.07 | 34.6 / 10.2 |
| CL 7 (diag) 5m don[20] dir=against hold=240m day | gross-positive, cost-negative pre-2023 | 3083 | 18.1 | -6.3 | -3.7 | 24.4 | 0.34 / -0.12 / -0.07 | 46.3 / 21.9 |
| CL 8 (diag) 10m vwz[2.0, 'globex'] dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 2284 | 2.9 | -21.5 | -18.8 | 24.4 | 0.06 / -0.47 / -0.41 | 31.1 / 6.7 |
| CL 9 (diag) 10m emax[9, 21] dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 2545 | 15.1 | -9.3 | -6.7 | 24.4 | 0.28 / -0.18 / -0.13 | 32.6 / 8.2 |
| ZN 1 (diag) 10m emax[9, 21] dir=with hold=240m day | negative pre-2023 | 2045 | -4.7 | -40.3 | -45.4 | 35.6 | -0.28 / -2.39 / -2.69 | 21.7 / -13.9 |
| ZN 2 (diag) 15m macd[12, 26] dir=with hold=240m day | negative pre-2023 | 1466 | -4.9 | -40.5 | -45.6 | 35.6 | -0.24 / -1.98 / -2.23 | 19.7 / -15.9 |
| ZN 3 (diag) 15m don[20] dir=against hold=240m day | negative pre-2023 | 2340 | -2.3 | -38.0 | -43.1 | 35.6 | -0.15 / -2.44 / -2.77 | 20.8 / -14.8 |
| YM 1 15m st[14, 2.0] dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 4549 | 0.8 | -13.5 | -7.8 | 14.4 | 0.05 / -0.71 / -0.41 | 39.6 / 25.3 |
| YM 2 15m macd[12, 26] dir=with hold=240m day | negative pre-2023 | 1547 | -29.5 | -43.9 | -38.1 | 14.4 | -0.46 / -0.68 / -0.59 | 126.3 / 112.0 |
| YM 3 10m st[14, 2.0] dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 5851 | 2.0 | -12.3 | -6.6 | 14.4 | 0.13 / -0.76 / -0.40 | 34.1 / 19.7 |
| YM 4 10m st[14, 2.0] dir=with hold=180m all | negative pre-2023 | 8767 | -6.7 | -21.1 | -15.3 | 14.4 | -0.38 / -1.19 / -0.86 | 39.0 / 24.7 |
| YM 5 15m st[14, 2.0] dir=with hold=60m all | negative pre-2023 | 9957 | -0.7 | -15.0 | -9.2 | 14.4 | -0.06 / -1.45 / -0.89 | 25.3 / 10.9 |
| YM 6 10m macd[12, 26] dir=with hold=180m day | negative pre-2023 | 2257 | -8.8 | -23.2 | -17.5 | 14.4 | -0.20 / -0.54 / -0.41 | 58.6 / 44.2 |
| YM 7 15m vwz[2.0, 'globex'] dir=with hold=240m day | positive pre-2023 | 1455 | 26.1 | 11.8 | 17.3 | 14.4 | 0.39 / 0.17 / 0.26 | 73.5 / 59.2 |
| YM 8 15m st[14, 2.0] dir=with hold=120m all | gross-positive, cost-negative pre-2023 | 8090 | 1.2 | -13.2 | -7.4 | 14.4 | 0.07 / -0.79 / -0.44 | 30.6 / 16.2 |
| YM 9 15m st[14, 2.0] dir=with hold=180m all | gross-positive, cost-negative pre-2023 | 6692 | 2.1 | -12.2 | -6.5 | 14.4 | 0.10 / -0.58 / -0.31 | 28.8 / 14.4 |
| YM 10 10m st[14, 2.0] dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 3221 | 0.1 | -14.2 | -8.5 | 14.4 | 0.00 / -0.38 / -0.23 | 39.9 / 25.5 |
| BTC 1 10m don[20] dir=with hold=180m all | gross-positive, cost-negative pre-2023 | 1419 | 34.2 | -20.1 | 12.2 | 54.4 | 0.50 / -0.28 / 0.18 | 207.1 / 152.8 |
| BTC 2 10m st[14, 2.0] dir=with hold=120m day | positive pre-2023 | 633 | 86.0 | 31.6 | 64.1 | 54.4 | 1.01 / 0.36 / 0.75 | 305.4 / 251.0 |
| BTC 3 5m macd[12, 26] dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 643 | 8.2 | -46.2 | -13.4 | 54.4 | 0.09 / -0.63 / -0.19 | 231.4 / 177.0 |
| BTC 4 10m emax[9, 21] dir=with hold=120m all | negative pre-2023 | 1245 | -22.4 | -76.8 | -44.0 | 54.4 | -0.42 / -1.48 / -0.83 | 151.4 / 97.1 |
| BTC 5 5m emax[9, 21] dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 723 | 21.5 | -32.9 | -0.1 | 54.4 | 0.36 / -0.62 / -0.03 | 216.9 / 162.5 |
| BTC 6 10m rsi[14, 30] dir=against hold=180m all | positive pre-2023 | 702 | 78.3 | 24.0 | 56.2 | 54.4 | 0.72 / 0.22 / 0.52 | 243.2 / 188.8 |
| BTC 7 5m rsi[14, 30] dir=against hold=120m all | gross-positive, cost-negative pre-2023 | 1187 | 21.1 | -33.2 | -0.9 | 54.4 | 0.37 / -0.59 / -0.02 | 155.7 / 101.3 |
| BTC 8 15m macd[12, 26] dir=with hold=180m day | negative pre-2023 | 260 | -191.0 | -245.3 | -212.6 | 54.4 | -1.31 / -1.68 / -1.46 | 373.0 / 318.7 |
| BTC 9 10m vwz[2.0, 'globex'] dir=against hold=60m day | positive pre-2023 | 265 | 80.3 | 25.9 | 58.5 | 54.4 | 0.70 / 0.23 / 0.51 | 222.2 / 167.9 |
| BTC 10 10m vwz[2.0, 'globex'] dir=against hold=180m day | positive pre-2023 | 170 | 202.2 | 147.8 | 180.4 | 54.4 | 1.04 / 0.76 / 0.93 | 331.1 / 276.8 |


## 6b. Replication tests (leads only)
GC 1 (cell 15, 5m ST(14,2.0) against, 240 min, day): (a) live weeks N/A; (b) H0 2023-02..07 standalone Sharpe +1.20, 137 trades: holds; (c) ES -0.08, RTY -0.07: fails; (d) odd months +0.29, even +0.71 vs +0.54: holds. 2 of 4: replicated. GC 2 (cell 13, hold 180): (b) +0.09 on 209 trades holds (weak), (c) ES -0.30 / RTY -0.11 fails, (d) +0.37 / +0.37 vs +0.38 holds: 2 of 4. GC 5 (cell 93): (b) -0.49 fails, (c) fails, (d) +0.40 / +0.44 vs +0.41 holds: 1 of 4. Files outputs/autopilot/b/b7_co/repl_GC_15.json, _13, _93.


## 6. What this says
- **The strongest result of the B batch: a gold fade book that adds to the pair on every span, fails only the strict plateau gate.** Cell GC 1: **5-minute Supertrend(14, 2.0) flip, traded AGAINST the flip (fade), held exactly 240 minutes, no stop, day session (entries 08:00-15:30 ET, full hold must finish before the 16:55 flatten).** Clean weekly Sharpe 1.59, H1 2.64, H2 1.68 (all-in 1.66); out-of-selection (H1+H2) standalone 2.04 against its own random-entry null p95 of 1.34 (all-in null p95 0.70). Additive uplift at 20% share +0.23 / +1.28 / +1.00 on clean / H1 / H2 (10%: +0.13/+0.78/+0.62; 30%: +0.32/+1.49/+1.11; 50% +0.44/+1.42/+0.91 but worst week +99% vs the 50% share allowance), bootstrap 90% lower bound +0.22 at 20%, worst-decile correlation +0.08, all-in uplift at 2x slippage +0.49 (standalone OOS 1.95 at 2x). Gate counts for this cell: pre-registration yes; clean-only selection yes; additive +0.10 on clean, H1 and H2 yes at 10/20/30%; own null yes; bootstrap yes; 2x slippage yes; worst-decile correlation yes; NT8 spec yes; **plateau NO: 0.33** (2 of 6 +-25% neighbours keep >= 75% of the 0.54 uplift: hold 180 min 0.38, hold 300 min 0.37, ST ATR 10 0.49, ATR 18 0.52, mult 1.5 0.33, mult 2.5 0.29; all six neighbours are positive and have standalone Sharpe 1.0-1.6, so the shape is a broad positive hill with a sharp peak at the chosen cell, but the gate is 75% and is not softened). Sibling GC 2 (same signal, hold 180 min): +0.24 / +0.62 / +0.70, plateau 0.50, also a gate-3 LEAD; GC 5 (5-minute MACD 12/26 zero cross against, hold 180): +0.13 / +0.84 / +0.69, bootstrap lower bound +0.05 at 20% but plateau 0.17.
- **Replication (amendment 2) for GC 1: H0 2023-02..07 standalone Sharpe +1.20 on 137 trades holds; alternating months hold (odd +0.29, even +0.71 against +0.54 overall); cross-instrument fails (ES -0.08, RTY -0.07; the effect is gold-specific); live weeks not available.** 2 of 4: replicated. GC 2: H0 +0.09 on 209 trades (holds, weakly), alternating months hold, ES -0.30 / RTY -0.11 fail: 2 of 4. GC 5: H0 -0.49 fails, ES/RTY fail, alternating months hold: 1 of 4.
- **Cautions that keep it a LEAD:** (1) the selection-time false-survivor test is at chance on GC (16 cells pass the clean rule against a replicate mean of 15.7, p(count) = 0.51; top-10 mean 0.96 against a replicate p95 of 1.05): time-exit rules on a trending gold tape pass a clean-half screen easily, so the gating evidence is the out-of-selection result in H1+H2, which is huge (uplift +1.28 / +1.00; H1 and H2 were gold's volatile 2025-26 regime); (2) no stop: worst single trade -$19.6k PER CONTRACT (at the 20%-share size of 3.9 contracts that is -$76k with no stop and -$36k with a 0.5 ADR stop; corrected in REPORT_GC_FADE_V2.md), maximum weekly sleeve loss -$120k / -$209k / -$464k (clean/H1/H2) at 100% share; a catastrophic stop was not tested and would change the result; (3) ERA flag 'positive pre-2023' but thin: 2,908 trades in 2013-22 earn gross $27 and net $2 per trade (1 contract), weekly Sharpe gross 0.49 / net 0.04 / price-scaled net 0.22 ($12.3 per trade): i.e. a small positive gross edge that cost swallows in the older era and that 2023-26 volatility magnifies; (4) one instrument; the mechanism in one sentence: five-minute trend flips in gold are mostly noise that mean-reverts over a few hours, and the faded position collects the reversion; it plausibly depends on current structure (gold's recent volatility and algorithmic whipsaw).
- Elsewhere: ES (30 cells, p(count) = 0.00, p(top) = 0.00 on clean), RTY (38 cells, p(count) = 0.00) and YM carry clean-span structure (mostly with-trend 5-15 minute signals held 1-3 hours) that does NOT survive H1/H2: ES 1 +0.33 / -0.34 / -0.37, ES 4 +0.29 / +0.29 / -0.11, RTY 1 +0.25 / -0.28 / +0.21, YM 1 +0.19 / -0.32 / -0.36; CL has 6 cells and negative H2; ZN none. BTC: 57 cells pass the rule (replicates 33) and the best, BTC 9 (10-minute VWAP-z 2.0 fade, 60-minute hold), has +0.16 / +0.84 / -0.06: H2 fails. Only 3 cells (all GC) have +0.10 on all three spans.
- ERA flags over the 56 cells: 26 'gross-positive, cost-negative pre-2023', 17 'negative pre-2023', 13 'positive pre-2023'.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b7.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b7/ (`B7_CO_all_selected_scored.csv`).

DONE B7
