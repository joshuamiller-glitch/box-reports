# REPORT SW19 - prior-day VWAP / volume-profile POC / settlement-close level crossings (D01/D11 H3/H4)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 34 selected cells (+22 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.17; best pair-window standalone Sharpe +1.20.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: a 5/15-min bar close crossing the prior label day's VWAP, volume-profile POC (mode of 1-min volume at typical price, bin = ADR20/50) or last close; enter with/against the cross direction, hold 60/180 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 48 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      48 |         48 |         7 |               0.629 |                2 |          7 |            3 |
| CL    |      48 |         48 |         1 |               0.732 |                2 |          1 |            3 |
| ES    |      48 |         48 |         5 |               1.259 |                2 |          5 |            3 |
| GC    |      48 |         48 |         4 |               0.863 |                2 |          4 |            3 |
| NQ    |      48 |         48 |         9 |               1.206 |                2 |          9 |            1 |
| RTY   |      48 |         48 |         4 |               0.716 |                2 |          4 |            3 |
| YM    |      48 |         48 |         4 |               0.687 |                2 |          4 |            3 |
| ZN    |      48 |         48 |         0 |              -0.974 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    5 |             1.59 |               4 |       0    |                       0.757 |            0.607 |           1.066 |     0.24 |       1.259 |                1.301 |
| NQ    |     100 |                    9 |             6.94 |              13 |       0.28 |                       0.523 |            0.695 |           0.957 |     0.88 |       0.957 |                1.905 |
| RTY   |     100 |                    4 |             2.18 |               5 |       0.2  |                       0.463 |            0.629 |           1.218 |     0.69 |       0.716 |                1.36  |
| YM    |     100 |                    4 |             2.68 |               9 |       0.28 |                       0.543 |            0.618 |           1.024 |     0.49 |       0.687 |                1.739 |
| GC    |     100 |                    4 |             1.83 |               6 |       0.06 |                       0.447 |            0.643 |           1.109 |     0.63 |       0.863 |                1.597 |
| CL    |     100 |                    1 |             0.81 |               4 |       0.59 |                       0.732 |            0.572 |           1.159 |     0.15 |       0.732 |                1.187 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    7 |             4.73 |              10 |       0.19 |                       0.291 |            0.646 |           1.078 |     0.99 |       0.594 |                1.768 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m cross pvwap dir=with hold=60m day | 495 | 2 | 1.26 | -0.68 | 1.20 | 0.91 / 0.77 | 0.20 / 0.17 / 0.12 | 0.09 | 0.60 | 1.00 | 0.01 | 0.00 | 777 | LEAD |
| ES 2 | 15m cross pvwap dir=with hold=60m day | 422 | 2 | 0.97 | -0.46 | 0.88 | 0.73 / 0.71 | 0.15 / 0.33 / 0.21 | 0.08 | 0.45 | 1.00 | -0.02 | 0.50 | 669 | LEAD |
| ES 3 | 5m cross pvwap dir=with hold=60m all | 1097 | 2 | 0.86 | -1.69 | 0.72 | 0.41 / -0.38 | 0.11 / -0.01 / 0.06 | -0.08 | 0.41 | 1.00 | -0.09 | 0.00 | 1809 | NO |
| ES 4 | 15m cross pvwap dir=with hold=60m all | 925 | 2 | 0.56 | -1.31 | 0.16 | -0.32 / 0.23 | 0.06 / -0.05 / -0.08 | -0.16 | 0.08 | 1.00 | -0.20 | 0.00 | 1532 | NO |
| ES 5 | 5m cross pclose dir=against hold=180m all | 1147 | 2 | 0.13 | -1.08 | 0.08 | 0.06 / 0.49 | -0.02 / -0.01 / -0.08 | -0.14 | 0.48 | 1.00 | -0.18 | 0.00 | 1780 | NO |
| ES 6 (diag) | 15m cross pvwap dir=with hold=180m all | 599 | 1 | 0.39 | -0.70 | 0.52 | 0.60 / 0.69 | 0.02 / 0.08 / -0.05 | -0.08 | -0.06 | 0.99 | -0.20 | 0.00 | 1001 | diag |
| ES 7 (diag) | 15m cross pvwap dir=with hold=180m day | 258 | 1 | 0.10 | -0.21 | 0.78 | 1.56 / 0.74 | -0.02 / 0.36 / 0.21 | 0.05 | 0.29 | 0.99 | -0.10 | 0.00 | 405 | diag |
| ES 8 (diag) | 5m cross pvwap dir=with hold=180m day | 292 | 1 | 0.05 | -0.10 | 0.46 | 0.99 / 1.19 | -0.04 / 0.14 / 0.12 | -0.02 | 0.37 | 0.96 | -0.15 | 0.00 | 459 | diag |
| NQ 1 | 15m cross ppoc dir=against hold=180m day | 278 | 2 | 0.96 | 0.11 | 0.12 | -0.72 / 1.30 | 0.20 / -0.41 / -0.42 | -0.03 | 0.31 | 0.68 | -0.23 | 0.00 | 436 | NO |
| NQ 2 | 15m cross pclose dir=against hold=180m day | 341 | 2 | 0.95 | 0.64 | 0.05 | -1.34 / 1.43 | 0.20 / -0.37 / -0.41 | -0.03 | 0.40 | 0.64 | -0.20 | 0.00 | 510 | NO |
| NQ 3 | 5m cross pclose dir=against hold=180m day | 372 | 2 | 0.60 | 0.37 | -0.30 | -1.51 / 1.56 | 0.14 / -0.55 / -0.49 | -0.11 | 0.20 | 0.39 | -0.29 | 0.00 | 561 | NO |
| NQ 4 | 15m cross pvwap dir=against hold=180m all | 551 | 2 | 0.44 | 0.03 | 0.21 | 0.01 / 1.22 | 0.11 / -0.35 / 0.14 | 0.03 | -0.17 | 0.74 | -0.18 | 0.50 | 926 | NO |
| NQ 5 | 5m cross ppoc dir=against hold=180m day | 309 | 2 | 0.44 | 0.02 | -0.18 | -0.86 / 1.39 | 0.08 / -0.34 / -0.41 | -0.10 | 0.23 | 0.47 | -0.28 | 0.00 | 485 | NO |
| NQ 6 | 5m cross pvwap dir=against hold=60m all | 1000 | 2 | 0.39 | 0.01 | 0.49 | 0.63 / 1.13 | 0.08 / -0.63 / 0.57 | 0.06 | 0.23 | 0.97 | -0.15 | 0.00 | 1655 | NO |
| NQ 7 | 5m cross ppoc dir=against hold=60m day | 524 | 2 | 0.39 | 0.13 | -0.08 | -0.51 / 1.27 | 0.08 / -0.96 / 0.19 | -0.07 | 0.14 | 0.64 | -0.29 | 0.00 | 813 | NO |
| NQ 8 | 15m cross pvwap dir=against hold=60m all | 842 | 2 | 0.28 | 0.02 | 0.34 | 0.39 / 0.99 | 0.08 / -0.54 / 0.42 | 0.04 | 0.12 | 0.91 | -0.17 | 0.50 | 1402 | NO |
| NQ 9 | 15m cross pvwap dir=against hold=180m day | 251 | 2 | 0.25 | -0.26 | 0.16 | 0.08 / 1.55 | 0.06 / -0.28 / 0.12 | 0.02 | -0.26 | 0.70 | -0.20 | 0.50 | 391 | NO |
| NQ 10 (diag) | 5m cross pclose dir=against hold=60m day | 656 | 1 | 1.21 | 0.43 | 0.80 | 0.29 / 1.38 | 0.18 / -0.12 / 0.18 | 0.11 | -0.33 | 0.96 | -0.07 | 0.00 | 969 | diag |
| RTY 1 | 15m cross pvwap dir=with hold=60m day | 470 | 2 | 0.72 | 0.15 | 0.17 | -0.57 / 0.81 | 0.07 / -0.09 / -0.16 | -0.08 | 0.63 | 0.94 | -0.22 | 0.00 | 755 | NO |
| RTY 2 | 15m cross pvwap dir=against hold=180m all | 655 | 2 | 0.53 | -0.41 | 0.04 | -0.53 / 1.07 | 0.09 / -0.45 / -0.07 | -0.09 | -0.34 | 0.88 | -0.23 | 0.00 | 1057 | NO |
| RTY 3 | 15m cross pvwap dir=against hold=180m day | 290 | 2 | 0.41 | -0.17 | -0.51 | -1.73 / 1.20 | 0.06 / -0.60 / -0.34 | -0.16 | -0.44 | 0.35 | -0.34 | 0.00 | 473 | NO |
| RTY 4 | 15m cross ppoc dir=against hold=180m all | 882 | 2 | 0.19 | -0.44 | -0.07 | -0.44 / 0.61 | -0.01 / -0.19 / -0.08 | -0.13 | -0.30 | 0.84 | -0.26 | 0.00 | 1443 | NO |
| RTY 5 (diag) | 5m cross pvwap dir=with hold=60m day | 561 | 1 | 0.37 | 0.13 | -0.07 | -0.67 / 0.12 | 0.01 / -0.18 / -0.33 | -0.16 | 0.66 | 0.99 | -0.29 | 0.00 | 895 | diag |
| RTY 6 (diag) | 5m cross ppoc dir=with hold=180m day | 351 | 1 | 0.25 | -0.25 | 0.35 | 0.48 / 1.08 | 0.05 / -0.15 / 0.16 | 0.02 | -0.36 | 0.88 | -0.14 | 0.50 | 562 | diag |
| RTY 7 (diag) | 5m cross ppoc dir=with hold=60m day | 583 | 1 | 0.19 | 0.28 | 0.06 | -0.18 / 0.39 | 0.01 / -0.12 / -0.25 | -0.14 | 0.04 | 0.97 | -0.25 | 0.00 | 931 | diag |
| YM 1 | 15m cross pvwap dir=against hold=180m day | 266 | 2 | 0.69 | -0.61 | 0.56 | 0.38 / 1.19 | 0.08 / 0.00 / -0.12 | 0.00 | 0.53 | 0.93 | -0.14 | 0.50 | 438 | NO |
| YM 2 | 15m cross ppoc dir=with hold=60m day | 464 | 2 | 0.68 | -0.34 | -0.04 | -1.11 / 0.67 | 0.06 / -0.34 / -0.26 | -0.13 | -0.02 | 0.85 | -0.26 | 0.00 | 726 | NO |
| YM 3 | 5m cross ppoc dir=with hold=60m day | 531 | 2 | 0.51 | -0.27 | 0.25 | -0.11 / 0.57 | 0.03 / -0.02 / -0.15 | -0.08 | -0.20 | 0.99 | -0.22 | 0.00 | 841 | NO |
| YM 4 | 15m cross pclose dir=against hold=180m day | 361 | 2 | 0.30 | 0.16 | 0.37 | 0.40 / 1.09 | 0.01 / -0.21 / 0.06 | -0.04 | 0.28 | 0.91 | -0.18 | 0.00 | 542 | NO |
| YM 5 (diag) | 5m cross pvwap dir=with hold=60m day | 490 | 1 | 0.60 | -0.30 | 0.08 | -0.70 / 0.79 | 0.09 / -0.45 / -0.12 | -0.07 | -0.07 | 0.92 | -0.21 | 0.00 | 801 | diag |
| YM 6 (diag) | 5m cross pvwap dir=with hold=60m all | 1063 | 1 | 0.54 | -0.69 | -0.12 | -1.18 / 0.13 | 0.08 / -0.29 / -0.31 | -0.15 | -0.06 | 0.98 | -0.23 | 0.00 | 1741 | diag |
| YM 7 (diag) | 15m cross pvwap dir=with hold=60m all | 900 | 1 | 0.49 | -0.85 | -0.33 | -1.51 / 0.30 | 0.06 / -0.36 / -0.37 | -0.18 | -0.20 | 0.91 | -0.28 | 0.00 | 1473 | diag |
| GC 1 | 5m cross pclose dir=against hold=60m day | 455 | 2 | 0.86 | -0.70 | 0.68 | 0.76 / 0.95 | 0.12 / -0.91 / 0.61 | 0.01 | 0.44 | 0.99 | -0.28 | 0.50 | 702 | NO |
| GC 2 | 15m cross pclose dir=against hold=180m day | 254 | 2 | 0.39 | 0.28 | 0.35 | 0.54 / 1.35 | 0.03 / -0.33 / 0.23 | 0.00 | -0.35 | 0.85 | -0.22 | 0.50 | 388 | NO |
| GC 3 | 5m cross pclose dir=against hold=180m day | 286 | 2 | 0.28 | 0.01 | 0.47 | 0.86 / 1.04 | 0.01 / -0.54 / 0.53 | 0.03 | -0.16 | 0.95 | -0.19 | 0.50 | 434 | NO |
| GC 4 | 5m cross pvwap dir=against hold=60m day | 410 | 2 | 0.26 | -0.46 | 0.63 | 1.01 / 0.88 | 0.03 / 0.63 / 0.04 | 0.08 | 0.19 | 1.00 | -0.16 | 0.00 | 638 | NO |
| GC 5 (diag) | 15m cross pvwap dir=against hold=60m day | 334 | 1 | 0.80 | -0.73 | 0.68 | 0.83 / 1.51 | 0.13 / 0.59 / -0.18 | 0.09 | 0.11 | 0.97 | -0.15 | 0.50 | 528 | diag |
| GC 6 (diag) | 5m cross ppoc dir=against hold=60m day | 387 | 1 | 0.45 | -0.31 | -0.32 | -0.79 / 1.23 | 0.08 / -0.06 / -1.01 | -0.26 | 0.31 | 0.65 | -0.52 | 0.00 | 645 | diag |
| GC 7 (diag) | 15m cross pclose dir=against hold=60m day | 390 | 1 | 0.20 | -0.78 | 0.42 | 0.74 / 0.77 | -0.02 / -1.07 / 0.90 | -0.05 | 0.07 | 0.98 | -0.30 | 0.50 | 604 | diag |
| CL 1 | 5m cross pvwap dir=against hold=180m day | 284 | 2 | 0.73 | -0.12 | 0.56 | 0.34 / 0.48 | 0.12 / 0.29 / -0.03 | 0.05 | -0.03 | 0.99 | -0.08 | 0.50 | 411 | NO |
| CL 2 (diag) | 15m cross pvwap dir=against hold=180m day | 256 | 1 | 0.16 | -0.27 | 0.31 | 0.59 / 0.84 | -0.02 / 0.41 / -0.00 | -0.02 | -0.07 | 0.93 | -0.16 | 1.00 | 374 | diag |
| CL 3 (diag) | 5m cross pvwap dir=against hold=180m all | 643 | 1 | 0.05 | -0.63 | -0.50 | -1.02 / 0.77 | -0.05 / -0.33 / -0.31 | -0.27 | -0.03 | 0.75 | -0.39 | 0.00 | 1074 | diag |
| CL 4 (diag) | 15m cross pclose dir=against hold=60m day | 452 | 1 | -0.13 | -0.64 | 0.17 | 0.63 / 0.10 | -0.06 / -0.41 / 0.27 | -0.16 | -0.43 | 1.00 | -0.23 | 0.00 | 660 | diag |
| ZN 1 (diag) | 5m cross pclose dir=with hold=180m day | 313 | 1 | -0.97 | -1.98 | -1.32 | -2.21 / -3.48 | -0.22 / -0.49 / -0.29 | -0.58 | -0.42 | 1.00 | -0.45 | 0.00 | 498 | diag |
| ZN 2 (diag) | 15m cross ppoc dir=against hold=180m day | 249 | 0 | -1.41 | -2.08 | -1.91 | -3.48 / -3.26 | -0.31 / -0.69 / -0.29 | -0.66 | 0.28 | 1.00 | -0.53 | 0.00 | 394 | diag |
| ZN 3 (diag) | 15m cross pclose dir=with hold=180m day | 289 | 0 | -1.47 | -2.03 | -1.57 | -1.96 / -3.16 | -0.30 / -0.42 / -0.27 | -0.59 | -0.29 | 1.00 | -0.47 | 0.00 | 445 | diag |
| BTC 1 | 15m cross ppoc dir=with hold=60m all | 945 | 2 | 0.59 | 0.05 | 0.07 | -0.73 / 0.96 | 0.06 / 0.15 / -0.51 | -0.14 | -0.05 | 0.88 | -0.24 | 0.00 | 1498 | NO |
| BTC 2 | 5m cross pclose dir=with hold=180m day | 265 | 2 | 0.30 | -1.59 | 0.69 | 1.23 / 1.16 | 0.03 / 0.46 / -0.08 | 0.06 | 0.50 | 0.98 | -0.10 | 0.50 | 397 | NO |
| BTC 3 | 15m cross pclose dir=with hold=180m all | 763 | 2 | 0.30 | -1.96 | 0.04 | -0.29 / 1.37 | 0.03 / -0.26 / -0.18 | -0.10 | 0.15 | 0.80 | -0.23 | 0.00 | 1216 | NO |
| BTC 4 | 5m cross pclose dir=with hold=180m all | 883 | 2 | 0.26 | -2.07 | 0.37 | 0.53 / 1.16 | 0.05 / 0.07 / -0.08 | -0.02 | -0.04 | 0.93 | -0.15 | 1.00 | 1413 | NO |
| BTC 5 | 5m cross ppoc dir=with hold=60m all | 1144 | 2 | 0.22 | -0.84 | 0.34 | 0.32 / 0.65 | 0.01 / 0.30 / -0.21 | -0.09 | 0.11 | 0.93 | -0.18 | 0.50 | 1816 | NO |
| BTC 6 | 5m cross pvwap dir=against hold=180m day | 242 | 2 | 0.19 | -0.73 | -0.32 | -1.15 / 1.19 | 0.01 / -0.92 / 0.13 | -0.13 | -0.28 | 0.44 | -0.32 | 0.00 | 372 | NO |
| BTC 7 | 15m cross ppoc dir=with hold=60m day | 358 | 2 | 0.17 | -0.58 | 0.08 | -0.12 / 1.10 | 0.01 / 0.37 / -0.31 | -0.06 | -0.04 | 0.88 | -0.21 | 0.00 | 532 | NO |
| BTC 8 (diag) | 15m cross pvwap dir=against hold=60m day | 326 | 1 | 0.63 | -0.18 | -0.35 | -2.26 / 1.05 | 0.07 / -0.85 / 0.00 | -0.12 | -0.32 | 0.62 | -0.25 | 0.00 | 501 | diag |
| BTC 9 (diag) | 5m cross ppoc dir=with hold=60m day | 419 | 1 | 0.45 | -0.88 | 0.56 | 0.63 / 0.80 | 0.07 / 0.53 / -0.14 | 0.03 | 0.30 | 0.99 | -0.11 | 0.50 | 611 | diag |
| BTC 10 (diag) | 5m cross pclose dir=with hold=60m all | 1391 | 1 | 0.36 | -1.11 | 0.12 | -0.29 / 0.64 | 0.12 / 0.11 / -0.25 | -0.08 | -0.20 | 0.97 | -0.16 | 0.00 | 2223 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 34 |
| diagnostic cells read | 22 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 1 |
| all-in uplift @20% > 0 (all scored) | 27 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 27 |
| worst-decile corr <= +0.30 | 43 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m cross pclose dir=with hold=180m day | clean | 0.27 | 0.37 | -145568 | -118905 | 437160 | -198867 | 0.55 | 41.0 | 1.49 | -89000 | 313065 | -104085 |
| BTC 5m cross pclose dir=with hold=180m day | H1 | 2.05 | 3.71 | -171981 | -158646 | 456832 | -174966 | 1.82 | 32.1 | 3.29 | -81791 | 144551 | -93577 |
| BTC 5m cross pclose dir=with hold=180m day | H2 | 0.23 | 0.43 | -88958 | -69908 | 287644 | -97242 | 0.23 | 52.8 | 2.40 | -84215 | 222208 | -87794 |
| BTC 5m cross pclose dir=with hold=180m day | all | 0.69 | 1.09 | -149927 | -120296 | 560929 | -198867 | 2.03 | 42.3 | 1.98 | -88445 | 313065 | -104085 |
| CL 5m cross pvwap dir=against hold=180m day | clean | 0.69 | 1.16 | -113584 | -99365 | 495054 | -128842 | 1.26 | 45.7 | 1.58 | -84866 | 267147 | -98946 |
| CL 5m cross pvwap dir=against hold=180m day | H1 | 2.60 | 6.27 | -36456 | -35157 | 73660 | -38104 | 4.12 | 35.7 | 3.11 | -73583 | 138562 | -76932 |
| CL 5m cross pvwap dir=against hold=180m day | H2 | -0.29 | -0.37 | -208083 | -152676 | 533512 | -296570 | -0.22 | 47.2 | 2.46 | -81447 | 200856 | -84124 |
| CL 5m cross pvwap dir=against hold=180m day | all | 0.56 | 0.84 | -133593 | -108299 | 533512 | -296570 | 1.53 | 44.0 | 2.00 | -83278 | 267147 | -98946 |
| ES 15m cross pvwap dir=with hold=60m day | clean | 0.99 | 1.76 | -105893 | -89772 | 418665 | -135559 | 2.14 | 45.7 | 1.61 | -84957 | 280320 | -93760 |
| ES 15m cross pvwap dir=with hold=60m day | H1 | 0.79 | 1.34 | -120849 | -107410 | 246339 | -128088 | 0.97 | 35.7 | 3.16 | -64873 | 151731 | -71769 |
| ES 15m cross pvwap dir=with hold=60m day | H2 | 0.68 | 1.14 | -141865 | -112749 | 385419 | -145759 | 0.64 | 44.4 | 2.51 | -90082 | 204734 | -100612 |
| ES 15m cross pvwap dir=with hold=60m day | all | 0.88 | 1.52 | -119631 | -100697 | 585684 | -145759 | 2.36 | 44.0 | 2.03 | -85436 | 280320 | -100612 |
| GC 5m cross pvwap dir=against hold=60m day | clean | 0.15 | 0.23 | -130981 | -109504 | 504527 | -176166 | 0.28 | 47.6 | 1.49 | -87611 | 244751 | -95343 |
| GC 5m cross pvwap dir=against hold=60m day | H1 | 1.84 | 5.04 | -170036 | -167095 | 639408 | -176554 | 2.07 | 35.7 | 3.45 | -104245 | 180821 | -110991 |
| GC 5m cross pvwap dir=against hold=60m day | H2 | 0.43 | 0.83 | -288417 | -254683 | 784763 | -325943 | 0.55 | 55.6 | 2.53 | -113181 | 228139 | -125769 |
| GC 5m cross pvwap dir=against hold=60m day | all | 0.63 | 1.26 | -209297 | -169926 | 784763 | -325943 | 2.42 | 47.0 | 2.06 | -97846 | 244751 | -125769 |
| NQ 5m cross pvwap dir=against hold=60m all | clean | 0.36 | 0.61 | -106353 | -90509 | 434447 | -139393 | 0.76 | 52.4 | 1.54 | -82328 | 240250 | -94470 |
| NQ 5m cross pvwap dir=against hold=60m all | H1 | -1.35 | -1.55 | -245080 | -216211 | 885380 | -324226 | -0.59 | 46.4 | 2.20 | -112552 | 224903 | -141778 |
| NQ 5m cross pvwap dir=against hold=60m all | H2 | 2.11 | 5.09 | -116880 | -101075 | 293558 | -117585 | 3.80 | 41.7 | 3.06 | -92226 | 223452 | -96267 |
| NQ 5m cross pvwap dir=against hold=60m all | all | 0.49 | 0.79 | -155963 | -124493 | 984851 | -324226 | 0.94 | 49.4 | 2.00 | -92920 | 244958 | -141778 |
| RTY 15m cross pvwap dir=with hold=60m day | clean | 0.73 | 1.07 | -142448 | -109918 | 655592 | -218797 | 1.01 | 41.0 | 1.53 | -93882 | 330628 | -125633 |
| RTY 15m cross pvwap dir=with hold=60m day | H1 | -0.14 | -0.21 | -108497 | -96370 | 405588 | -109460 | -0.08 | 50.0 | 2.74 | -87771 | 175756 | -91296 |
| RTY 15m cross pvwap dir=with hold=60m day | H2 | -0.82 | -1.08 | -187731 | -170613 | 798795 | -202807 | -0.45 | 63.9 | 2.32 | -101411 | 237399 | -123086 |
| RTY 15m cross pvwap dir=with hold=60m day | all | 0.17 | 0.23 | -159984 | -128768 | 798795 | -218797 | 0.33 | 47.6 | 1.88 | -95769 | 330628 | -125633 |
| YM 15m cross pvwap dir=against hold=180m day | clean | 0.68 | 1.11 | -110346 | -92654 | 630817 | -202005 | 0.98 | 49.5 | 1.54 | -85084 | 308497 | -87029 |
| YM 15m cross pvwap dir=against hold=180m day | H1 | 0.60 | 0.95 | -126793 | -99303 | 206211 | -148497 | 0.68 | 42.9 | 2.83 | -77918 | 134140 | -79397 |
| YM 15m cross pvwap dir=against hold=180m day | H2 | 0.26 | 0.42 | -143785 | -118458 | 355760 | -155850 | 0.29 | 50.0 | 2.37 | -95967 | 235606 | -101255 |
| YM 15m cross pvwap dir=against hold=180m day | all | 0.56 | 0.90 | -124972 | -104332 | 630817 | -202005 | 1.36 | 48.8 | 1.93 | -86870 | 308497 | -101255 |
| ZN 5m cross pclose dir=with hold=180m day (diag) | clean | -1.00 | -1.27 | -152233 | -124607 | 1441029 | -203277 | -0.63 | 54.3 | 1.24 | -93623 | 329759 | -103774 |
| ZN 5m cross pclose dir=with hold=180m day (diag) | H1 | -2.69 | -2.82 | -100450 | -88873 | 509163 | -122832 | -0.84 | 57.1 | 2.33 | -80941 | 175550 | -86057 |
| ZN 5m cross pclose dir=with hold=180m day (diag) | H2 | -1.80 | -2.06 | -115706 | -86357 | 406811 | -122198 | -0.87 | 55.6 | 2.19 | -85152 | 243733 | -87455 |
| ZN 5m cross pclose dir=with hold=180m day (diag) | all | -1.32 | -1.62 | -140849 | -115820 | 2223929 | -203277 | -0.76 | 54.8 | 1.62 | -90900 | 329759 | -103774 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m cross pvwap dir=with hold=60m day | -14.6 | -2.9 | 17.6 | 27.2 | 8.2 / 17.8 | 31.7 / 36.5 | NO |
| NQ 5m cross pvwap dir=against hold=60m all | -19.9 | -83.1 | 1.9 | 6.8 | 6.9 / 18.2 | -93.0 / -37.5 | NO |
| RTY 15m cross pvwap dir=with hold=60m day | -27.1 | -49.0 | -2.1 | 0.7 | -50.2 / 0.5 | 5.1 / 10.4 | NO |
| YM 15m cross pvwap dir=against hold=180m day | -20.6 | -4.0 | 13.2 | 7.2 | 7.9 / 14.8 | 27.9 / 29.4 | NO |
| GC 5m cross pvwap dir=against hold=60m day | -9.3 | -48.6 | -10.0 | 19.4 | 0.7 / 11.6 | -32.7 / -21.5 | NO |
| CL 5m cross pvwap dir=against hold=180m day | -21.1 | -5.2 | 17.7 | 30.9 | -6.0 / 16.7 | 31.2 / 37.8 | NO |
| ZN 5m cross pclose dir=with hold=180m day (diag) | -48.4 | -13.3 | 4.2 | -0.8 | -14.2 / 0.2 | 15.1 / 23.6 | NO |
| BTC 5m cross pclose dir=with hold=180m day | -17.5 | -9.8 | 7.7 | 9.0 | -10.7 / 4.6 | -0.7 / 14.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m cross pvwap dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2563 | 6.7 | -22.6 | -8.4 | 29.4 | 0.20 / -0.68 / -0.25 | 113.5 / 84.2 |
| ES 2 15m cross pvwap dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2169 | 13.9 | -15.5 | -1.2 | 29.4 | 0.41 / -0.46 / -0.04 | 83.9 / 54.5 |
| ES 3 5m cross pvwap dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 5749 | 0.7 | -28.7 | -14.4 | 29.4 | 0.04 / -1.69 / -0.85 | 58.7 / 29.4 |
| ES 4 15m cross pvwap dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 4847 | 4.7 | -24.7 | -10.3 | 29.4 | 0.25 / -1.31 / -0.55 | 45.9 / 16.5 |
| ES 5 5m cross pclose dir=against hold=180m all | negative pre-2023 | 6133 | -0.4 | -29.8 | -15.6 | 29.4 | -0.01 / -1.08 / -0.56 | 33.3 / 4.0 |
| ES 6 (diag) 15m cross pvwap dir=with hold=180m all | gross-positive, cost-negative pre-2023 | 3083 | 3.1 | -26.3 | -12.0 | 29.4 | 0.08 / -0.70 / -0.32 | 50.8 / 21.5 |
| ES 7 (diag) 15m cross pvwap dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1280 | 14.2 | -15.2 | -1.0 | 29.4 | 0.19 / -0.21 / -0.01 | 49.2 / 19.8 |
| ES 8 (diag) 5m cross pvwap dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1435 | 22.6 | -6.8 | 7.4 | 29.4 | 0.33 / -0.10 / 0.11 | 44.0 / 14.6 |
| NQ 1 15m cross ppoc dir=against hold=180m day | positive pre-2023 | 1336 | 27.7 | 13.4 | 21.9 | 14.4 | 0.24 / 0.11 / 0.19 | 220.2 / 205.9 |
| NQ 2 15m cross pclose dir=against hold=180m day | positive pre-2023 | 1700 | 85.0 | 70.6 | 79.1 | 14.4 | 0.77 / 0.64 / 0.72 | 181.6 / 167.3 |
| NQ 3 5m cross pclose dir=against hold=180m day | positive pre-2023 | 1922 | 52.8 | 38.4 | 47.0 | 14.4 | 0.50 / 0.37 / 0.45 | 112.6 / 98.2 |
| NQ 4 15m cross pvwap dir=against hold=180m all | positive pre-2023 | 2883 | 15.9 | 1.6 | 10.2 | 14.4 | 0.27 / 0.03 / 0.17 | 64.3 / 49.9 |
| NQ 5 5m cross ppoc dir=against hold=180m day | positive pre-2023 | 1507 | 16.5 | 2.1 | 10.7 | 14.4 | 0.15 / 0.02 / 0.10 | 97.8 / 83.4 |
| NQ 6 5m cross pvwap dir=against hold=60m all | positive pre-2023 | 5358 | 14.7 | 0.4 | 9.0 | 14.4 | 0.54 / 0.01 / 0.33 | 32.4 / 18.0 |
| NQ 7 5m cross ppoc dir=against hold=60m day | positive pre-2023 | 2568 | 21.6 | 7.2 | 15.7 | 14.4 | 0.41 / 0.13 / 0.30 | 47.5 / 33.2 |
| NQ 8 15m cross pvwap dir=against hold=60m all | positive pre-2023 | 4537 | 15.0 | 0.7 | 9.3 | 14.4 | 0.51 / 0.02 / 0.32 | 31.1 / 16.7 |
| NQ 9 15m cross pvwap dir=against hold=180m day | negative pre-2023 | 1275 | -18.4 | -32.7 | -24.2 | 14.4 | -0.15 / -0.26 / -0.19 | 69.1 / 54.7 |
| NQ 10 (diag) 5m cross pclose dir=against hold=60m day | positive pre-2023 | 3379 | 35.0 | 20.6 | 29.2 | 14.4 | 0.73 / 0.43 / 0.61 | 109.2 / 94.8 |
| RTY 1 15m cross pvwap dir=with hold=60m day | positive pre-2023 | 1308 | 19.0 | 4.7 | 6.9 | 14.4 | 0.61 / 0.15 / 0.22 | 34.9 / 20.5 |
| RTY 2 15m cross pvwap dir=against hold=180m all | gross-positive, cost-negative pre-2023 | 1819 | 0.6 | -13.8 | -11.4 | 14.4 | 0.01 / -0.41 / -0.34 | 28.5 / 14.2 |
| RTY 3 15m cross pvwap dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 829 | 3.8 | -10.6 | -8.3 | 14.4 | 0.06 / -0.17 / -0.13 | 34.9 / 20.6 |
| RTY 4 15m cross ppoc dir=against hold=180m all | gross-positive, cost-negative pre-2023 | 2450 | 3.8 | -10.5 | -8.3 | 14.4 | 0.17 / -0.44 / -0.35 | 19.4 / 5.0 |
| RTY 5 (diag) 5m cross pvwap dir=with hold=60m day | positive pre-2023 | 1527 | 18.0 | 3.6 | 5.9 | 14.4 | 0.62 / 0.13 / 0.20 | 25.9 / 11.6 |
| RTY 6 (diag) 5m cross ppoc dir=with hold=180m day | gross-positive, cost-negative pre-2023 | 1008 | 0.8 | -13.6 | -11.3 | 14.4 | 0.01 / -0.25 / -0.21 | 30.2 / 15.8 |
| RTY 7 (diag) 5m cross ppoc dir=with hold=60m day | positive pre-2023 | 1752 | 21.6 | 7.2 | 9.5 | 14.4 | 0.83 / 0.28 / 0.37 | 20.3 / 6.0 |
| YM 1 15m cross pvwap dir=against hold=180m day | negative pre-2023 | 1251 | -20.7 | -35.1 | -29.4 | 14.4 | -0.36 / -0.61 / -0.51 | 61.8 / 47.4 |
| YM 2 15m cross ppoc dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2048 | 4.5 | -9.9 | -4.1 | 14.4 | 0.16 / -0.34 / -0.14 | 40.6 / 26.3 |
| YM 3 5m cross ppoc dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2461 | 6.8 | -7.6 | -1.9 | 14.4 | 0.24 / -0.27 / -0.07 | 33.1 / 18.7 |
| YM 4 15m cross pclose dir=against hold=180m day | positive pre-2023 | 1578 | 22.7 | 8.3 | 14.1 | 14.4 | 0.44 / 0.16 / 0.28 | 34.7 / 20.3 |
| YM 5 (diag) 5m cross pvwap dir=with hold=60m day | gross-positive, cost-negative pre-2023 | 2486 | 5.8 | -8.6 | -2.8 | 14.4 | 0.21 / -0.30 / -0.10 | 39.9 / 25.5 |
| YM 6 (diag) 5m cross pvwap dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 5567 | 5.1 | -9.3 | -3.5 | 14.4 | 0.38 / -0.69 / -0.26 | 26.4 / 12.1 |
| YM 7 (diag) 15m cross pvwap dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 4658 | 2.3 | -12.1 | -6.3 | 14.4 | 0.16 / -0.85 / -0.45 | 23.9 / 9.5 |
| GC 1 5m cross pclose dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 2595 | 2.3 | -22.1 | -12.4 | 24.4 | 0.07 / -0.70 / -0.40 | 55.1 / 30.7 |
| GC 2 15m cross pclose dir=against hold=180m day | positive pre-2023 | 1410 | 42.6 | 18.2 | 27.9 | 24.4 | 0.67 / 0.28 / 0.43 | 40.4 / 16.1 |
| GC 3 5m cross pclose dir=against hold=180m day | positive pre-2023 | 1594 | 25.7 | 1.3 | 11.0 | 24.4 | 0.42 / 0.01 / 0.17 | 30.2 / 5.9 |
| GC 4 5m cross pvwap dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 2206 | 10.1 | -14.2 | -4.6 | 24.4 | 0.32 / -0.46 / -0.15 | 31.7 / 7.3 |
| GC 5 (diag) 15m cross pvwap dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 1858 | 1.1 | -23.3 | -13.6 | 24.4 | 0.03 / -0.73 / -0.43 | 60.4 / 36.0 |
| GC 6 (diag) 5m cross ppoc dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 2268 | 15.1 | -9.2 | 0.5 | 24.4 | 0.50 / -0.31 / 0.02 | 41.5 / 17.2 |
| GC 7 (diag) 15m cross pclose dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 2179 | 0.6 | -23.7 | -14.1 | 24.4 | 0.01 / -0.78 / -0.46 | 25.9 / 1.5 |
| CL 1 5m cross pvwap dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1418 | 16.8 | -7.5 | -5.1 | 24.4 | 0.27 / -0.12 / -0.08 | 72.0 / 47.6 |
| CL 2 (diag) 15m cross pvwap dir=against hold=180m day | gross-positive, cost-negative pre-2023 | 1263 | 6.8 | -17.6 | -15.1 | 24.4 | 0.10 / -0.27 / -0.23 | 31.8 / 7.4 |
| CL 3 (diag) 5m cross pvwap dir=against hold=180m all | gross-positive, cost-negative pre-2023 | 3334 | 3.1 | -21.3 | -18.9 | 24.4 | 0.09 / -0.63 / -0.56 | 23.9 / -0.5 |
| CL 4 (diag) 15m cross pclose dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 2456 | 5.1 | -19.2 | -16.8 | 24.4 | 0.17 / -0.64 / -0.56 | 19.9 / -4.5 |
| ZN 1 (diag) 5m cross pclose dir=with hold=180m day | negative pre-2023 | 1663 | -0.1 | -35.7 | -40.9 | 35.6 | -0.01 / -1.98 / -2.26 | 15.7 / -19.9 |
| ZN 2 (diag) 15m cross ppoc dir=against hold=180m day | negative pre-2023 | 1260 | -2.8 | -38.4 | -43.6 | 35.6 | -0.16 / -2.08 / -2.35 | 6.8 / -28.8 |
| ZN 3 (diag) 15m cross pclose dir=with hold=180m day | negative pre-2023 | 1473 | -1.7 | -37.3 | -42.6 | 35.6 | -0.10 / -2.03 / -2.30 | 5.8 / -29.8 |
| BTC 1 15m cross ppoc dir=with hold=60m all | positive pre-2023 | 631 | 57.7 | 3.4 | 35.7 | 54.4 | 0.95 / 0.05 / 0.59 | 118.5 / 64.1 |
| BTC 2 5m cross pclose dir=with hold=180m day | negative pre-2023 | 197 | -267.6 | -322.0 | -289.8 | 54.4 | -1.33 / -1.59 / -1.43 | 150.9 / 96.6 |
| BTC 3 15m cross pclose dir=with hold=180m all | negative pre-2023 | 580 | -108.6 | -162.9 | -130.5 | 54.4 | -1.33 / -1.96 / -1.57 | 103.2 / 48.9 |
| BTC 4 5m cross pclose dir=with hold=180m all | negative pre-2023 | 697 | -92.0 | -146.4 | -114.0 | 54.4 | -1.29 / -2.07 / -1.60 | 97.2 / 42.9 |
| BTC 5 5m cross ppoc dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 787 | 15.2 | -39.2 | -6.7 | 54.4 | 0.33 / -0.84 / -0.15 | 88.5 / 34.1 |
| BTC 6 5m cross pvwap dir=against hold=180m day | negative pre-2023 | 172 | -92.7 | -147.1 | -114.3 | 54.4 | -0.46 / -0.73 / -0.57 | 168.4 / 114.0 |
| BTC 7 15m cross ppoc dir=with hold=60m day | negative pre-2023 | 250 | -26.7 | -81.1 | -48.4 | 54.4 | -0.19 / -0.58 / -0.35 | 98.5 / 44.1 |
| BTC 8 (diag) 15m cross pvwap dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 277 | 39.1 | -15.3 | 16.8 | 54.4 | 0.45 / -0.18 / 0.19 | 184.7 / 130.3 |
| BTC 9 (diag) 5m cross ppoc dir=with hold=60m day | negative pre-2023 | 299 | -36.6 | -91.0 | -58.2 | 54.4 | -0.35 / -0.88 / -0.56 | 143.4 / 89.1 |
| BTC 10 (diag) 5m cross pclose dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 1151 | 14.1 | -40.2 | -7.8 | 54.4 | 0.40 / -1.11 / -0.21 | 89.6 / 35.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 7 cells pass the clean rule against a replicate mean of 4.7 (p(count) = 0.19, p(top) = 0.99); CL: 1 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.59, p(top) = 0.15); ES: 5 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.00, p(top) = 0.24); GC: 4 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 0.06, p(top) = 0.63); NQ: 9 cells pass the clean rule against a replicate mean of 6.9 (p(count) = 0.28, p(top) = 0.88); RTY: 4 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.20, p(top) = 0.69); YM: 4 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.28, p(top) = 0.49); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 34 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.17 (ES 15m cross pvwap dir=with hold=60m day); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell ES 5m cross pvwap dir=with hold=60m day: uplift +0.20/+0.17/+0.12, boot lo +0.01, plateau 0.00, 2x-slip +0.09, wd corr +0.60, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- Gate-3 cell ES 15m cross pvwap dir=with hold=60m day: uplift +0.15/+0.33/+0.21, boot lo -0.02, plateau 0.50, 2x-slip +0.08, wd corr +0.45, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 13, 'positive pre-2023': 13, 'negative pre-2023': 8}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_19.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw19/ (`SW19_CO_all_selected_scored.csv`).

DONE SW19
