# REPORT SW14 - intraday-vol-regime gating (trailing 60-min range / ADR20) of trend and fade signals (D08 H2/H3)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 54 selected cells (+14 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.26; best pair-window standalone Sharpe +1.11.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: ST(14,2) flip / Donchian-20 / VWAP-band 2.0 globex on 5/15-min bars, with or against, exact hold 60/180 min; taken only when trailing-60-min range/ADR20 is hi (>= 0.25 or 0.35) or lo (<= 0.15 or 0.25).
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        17 |               1.753 |                2 |         10 |            0 |
| CL    |      96 |         96 |         2 |               0.935 |                2 |          2 |            3 |
| ES    |      96 |         96 |         7 |               2.272 |                2 |          7 |            3 |
| GC    |      96 |         96 |         7 |               0.969 |                2 |          7 |            3 |
| NQ    |      96 |         96 |        17 |               1.832 |                2 |         10 |            0 |
| RTY   |      96 |         96 |        10 |               1.08  |                2 |         10 |            0 |
| YM    |      96 |         96 |         8 |               1.524 |                2 |          8 |            2 |
| ZN    |      96 |         96 |         0 |              -1.069 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    7 |             3.19 |               8 |       0.03 |                       1.188 |            0.599 |           0.873 |     0.01 |       2.272 |                1.509 |
| NQ    |     100 |                   17 |            12.53 |              20 |       0.14 |                       1.31  |            0.808 |           1.106 |     0    |       1.832 |                1.924 |
| RTY   |     100 |                   10 |             4.89 |               9 |       0    |                       0.567 |            0.627 |           1.012 |     0.6  |       1.08  |                1.649 |
| YM    |     100 |                    8 |             5.35 |              13 |       0.21 |                       0.823 |            0.658 |           0.934 |     0.2  |       1.524 |                1.698 |
| GC    |     100 |                    7 |             3.85 |               8 |       0.04 |                       0.67  |            0.603 |           0.942 |     0.39 |       0.914 |                1.579 |
| CL    |     100 |                    2 |             1.9  |               6 |       0.6  |                       0.861 |            0.57  |           0.992 |     0.11 |       0.935 |                1.364 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                   17 |             8.88 |              15 |       0    |                       0.799 |            0.707 |           0.988 |     0.28 |       1.753 |                1.946 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 343 | 2 | 2.27 | -0.18 | 1.10 | -0.46 / 1.37 | 0.40 / -0.17 / -0.27 | 0.12 | 0.07 | 1.00 | -0.04 | 0.17 | 547 | NO |
| ES 2 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 236 | 2 | 1.60 | 0.03 | 1.11 | 0.40 / 1.38 | 0.27 / 0.08 / 0.07 | 0.15 | 0.18 | 0.99 | 0.00 | 0.50 | 378 | NO |
| ES 3 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | 388 | 2 | 1.50 | -0.31 | 0.81 | -0.12 / 0.96 | 0.26 / -0.30 / 0.11 | 0.09 | 0.40 | 1.00 | -0.06 | 0.50 | 632 | NO |
| ES 4 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | 549 | 2 | 1.21 | -0.43 | 0.40 | -0.60 / 0.79 | 0.18 / -0.24 / -0.22 | -0.04 | 0.47 | 0.94 | -0.17 | 0.50 | 891 | NO |
| ES 5 | 5m don[20] dir=with hold=180m iv60/ADR hi0.25 | 905 | 2 | 0.97 | -1.18 | 0.09 | -1.37 / 1.07 | 0.17 / -0.15 / -0.52 | -0.11 | -0.54 | 0.87 | -0.21 | 0.00 | 1521 | NO |
| ES 6 | 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | 397 | 2 | 0.58 | 0.11 | -0.24 | -1.14 / 1.26 | 0.07 / -0.77 / -0.34 | -0.20 | 0.40 | 0.49 | -0.37 | 0.00 | 660 | NO |
| ES 7 | 15m don[20] dir=against hold=180m iv60/ADR hi0.25 | 664 | 2 | 0.18 | -0.34 | 0.01 | -0.09 / 1.16 | -0.03 / -1.00 / 0.42 | -0.17 | 0.15 | 0.78 | -0.32 | 0.00 | 1108 | NO |
| ES 8 (diag) | 5m don[20] dir=with hold=60m iv60/ADR hi0.35 | 946 | 1 | 0.83 | -1.33 | 0.64 | 0.21 / 0.71 | 0.10 / 0.20 / -0.14 | -0.04 | -0.36 | 0.97 | -0.09 | 0.17 | 1487 | diag |
| ES 9 (diag) | 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | 554 | 1 | 0.75 | -0.56 | 0.57 | 0.27 / 1.22 | 0.15 / 0.09 / -0.05 | 0.05 | -0.51 | 0.97 | -0.09 | 0.17 | 906 | diag |
| ES 10 (diag) | 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.25 | 920 | 1 | 0.48 | -1.42 | 0.17 | -0.31 / 0.97 | 0.08 / 0.12 / -0.02 | -0.08 | -0.28 | 0.97 | -0.15 | 0.38 | 1467 | diag |
| NQ 1 | 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | 1724 | 2 | 1.83 | -0.23 | 1.07 | 0.45 / 1.18 | 0.35 / 0.62 / -0.27 | 0.21 | 0.42 | 1.00 | 0.03 | 0.00 | 2684 | NO |
| NQ 2 | 15m don[20] dir=against hold=180m iv60/ADR hi0.25 | 692 | 2 | 1.76 | 0.11 | 0.87 | 0.29 / 1.40 | 0.34 / -0.66 / 0.39 | 0.20 | 0.24 | 0.98 | -0.04 | 0.67 | 1145 | NO |
| NQ 3 | 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | 431 | 2 | 1.72 | -0.00 | 0.93 | 0.16 / 1.29 | 0.35 / -0.23 / 0.12 | 0.21 | 0.12 | 0.96 | -0.01 | 0.50 | 703 | NO |
| NQ 4 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | 572 | 2 | 1.60 | 0.51 | 0.52 | -0.40 / 1.72 | 0.32 / -0.78 / 0.07 | 0.09 | 0.33 | 0.85 | -0.14 | 0.00 | 911 | NO |
| NQ 5 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | 425 | 2 | 1.48 | 0.21 | 0.59 | -0.27 / 1.24 | 0.29 / -0.43 / 0.03 | 0.11 | 0.45 | 0.93 | -0.13 | 0.67 | 688 | NO |
| NQ 6 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 368 | 2 | 1.16 | 0.48 | -0.11 | -1.37 / 1.38 | 0.22 / -1.12 / -0.14 | -0.07 | 0.20 | 0.51 | -0.31 | 0.00 | 580 | NO |
| NQ 7 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 259 | 2 | 1.05 | 0.33 | 0.40 | -0.22 / 1.46 | 0.21 / -0.42 / 0.02 | 0.07 | 0.51 | 0.84 | -0.17 | 0.67 | 421 | NO |
| NQ 8 | 5m don[20] dir=with hold=60m iv60/ADR hi0.25 | 1633 | 2 | 0.95 | -0.93 | 0.48 | -0.20 / 1.29 | 0.11 / 0.35 / -0.43 | -0.02 | 0.12 | 0.94 | -0.17 | 0.33 | 2644 | NO |
| NQ 9 | 5m st[14, 2.0] dir=against hold=60m iv60/ADR hi0.35 | 519 | 2 | 0.77 | -0.72 | 0.07 | -1.07 / 1.18 | 0.10 / -0.16 / -0.44 | -0.07 | -0.24 | 0.69 | -0.25 | 0.00 | 824 | NO |
| NQ 10 | 5m st[14, 2.0] dir=against hold=180m iv60/ADR lo0.25 | 2012 | 2 | 0.77 | -0.37 | 0.73 | 0.65 / 1.47 | 0.09 / -0.02 / 0.04 | 0.02 | -0.43 | 0.95 | -0.16 | 0.38 | 3217 | NO |
| RTY 1 | 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | 444 | 2 | 1.08 | -0.31 | 0.15 | -1.32 / 1.17 | 0.17 / -0.59 / -0.06 | -0.03 | -0.13 | 0.74 | -0.16 | 0.17 | 725 | NO |
| RTY 2 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 352 | 2 | 0.96 | -0.18 | 0.04 | -1.46 / 0.87 | 0.18 / -0.58 / -0.14 | -0.04 | -0.09 | 0.73 | -0.18 | 0.33 | 574 | NO |
| RTY 3 | 5m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | 406 | 2 | 0.82 | -1.15 | 0.54 | 0.01 / 1.32 | 0.11 / 0.50 / -0.31 | 0.03 | -0.24 | 0.89 | -0.09 | 0.25 | 643 | NO |
| RTY 4 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | 448 | 2 | 0.63 | -0.48 | 0.35 | -0.05 / 0.70 | 0.11 / 0.23 / -0.17 | 0.01 | -0.41 | 0.99 | -0.10 | 0.17 | 755 | NO |
| RTY 5 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 227 | 2 | 0.61 | -0.48 | -0.11 | -1.15 / 0.91 | 0.10 / -0.93 / -0.00 | -0.10 | 0.20 | 0.73 | -0.25 | 0.00 | 398 | NO |
| RTY 6 | 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.25 | 973 | 2 | 0.48 | -1.25 | 0.50 | 0.62 / 1.03 | 0.05 / 0.27 / -0.02 | -0.00 | -0.24 | 0.99 | -0.11 | 0.25 | 1548 | NO |
| RTY 7 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | 281 | 2 | 0.36 | -0.43 | 0.14 | -0.06 / 0.74 | 0.02 / 0.25 / -0.19 | -0.05 | -0.22 | 0.84 | -0.18 | 0.50 | 473 | NO |
| RTY 8 | 15m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | 328 | 2 | 0.34 | -0.62 | 0.17 | -0.03 / 1.10 | 0.04 / -0.63 / 0.19 | -0.06 | 0.09 | 0.81 | -0.23 | 0.00 | 545 | NO |
| RTY 9 | 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | 610 | 2 | 0.30 | -1.12 | 0.67 | 1.32 / 1.20 | 0.07 / 0.26 / 0.22 | 0.06 | 0.09 | 1.00 | -0.08 | 0.50 | 930 | NO |
| RTY 10 | 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.15 | 695 | 2 | 0.09 | -1.34 | -0.75 | -2.26 / 1.05 | -0.06 / -0.44 / -0.36 | -0.28 | -0.12 | 0.49 | -0.36 | 0.00 | 1100 | NO |
| YM 1 | 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.25 | 791 | 2 | 1.52 | -0.83 | 0.54 | -0.53 / 0.62 | 0.21 / -0.07 / -0.29 | -0.02 | 0.13 | 1.00 | -0.15 | 0.50 | 1304 | NO |
| YM 2 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | 597 | 2 | 1.07 | -0.66 | 0.74 | 0.41 / 0.88 | 0.15 / 0.35 / -0.15 | 0.05 | -0.16 | 1.00 | -0.08 | 0.17 | 928 | NO |
| YM 3 | 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.35 | 483 | 2 | 1.02 | -0.68 | -0.01 | -1.07 / 1.06 | 0.12 / -0.31 / -0.44 | -0.13 | 0.52 | 0.81 | -0.28 | 0.00 | 779 | NO |
| YM 4 | 15m don[20] dir=with hold=60m iv60/ADR hi0.25 | 965 | 2 | 0.90 | -0.90 | 0.24 | -0.39 / 0.98 | 0.08 / 0.33 / -0.55 | -0.11 | 0.09 | 0.94 | -0.25 | 0.00 | 1520 | NO |
| YM 5 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | 375 | 2 | 0.77 | -0.30 | 0.13 | -0.54 / 1.14 | 0.08 / 0.04 / -0.46 | -0.08 | 0.23 | 0.80 | -0.23 | 0.00 | 587 | NO |
| YM 6 | 15m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | 342 | 2 | 0.59 | -0.14 | 0.41 | 0.23 / 1.05 | 0.14 / -0.33 / 0.15 | 0.05 | -0.42 | 0.92 | -0.13 | 0.25 | 570 | NO |
| YM 7 | 15m don[20] dir=against hold=180m iv60/ADR lo0.15 | 866 | 2 | 0.55 | -0.55 | 0.24 | -0.19 / 0.68 | 0.12 / 0.30 / -0.31 | -0.03 | -0.29 | 0.98 | -0.12 | 0.17 | 1371 | NO |
| YM 8 | 5m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | 391 | 2 | 0.16 | -0.83 | 0.03 | -0.19 / 1.02 | 0.02 / 0.41 / -0.45 | -0.06 | -0.31 | 0.67 | -0.21 | 0.00 | 659 | NO |
| YM 9 (diag) | 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | 567 | 1 | 0.89 | -0.06 | -0.22 | -2.05 / 1.07 | 0.12 / -0.26 / -0.53 | -0.12 | -0.47 | 0.57 | -0.26 | 0.00 | 933 | diag |
| YM 10 (diag) | 5m don[20] dir=with hold=60m iv60/ADR hi0.35 | 961 | 1 | 0.82 | -0.61 | -0.13 | -1.81 / 0.99 | 0.06 / -0.23 / -0.52 | -0.16 | 0.00 | 0.82 | -0.27 | 0.00 | 1522 | diag |
| GC 1 | 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.15 | 466 | 2 | 0.91 | -0.61 | 0.44 | 0.16 / 1.32 | 0.21 / -0.22 / -0.30 | -0.04 | -0.54 | 0.90 | -0.23 | 0.33 | 647 | NO |
| GC 2 | 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | 463 | 2 | 0.85 | -0.59 | -0.18 | -0.81 / 1.52 | 0.23 / -1.56 / -0.14 | -0.20 | -0.08 | 0.52 | -0.54 | 0.00 | 732 | NO |
| GC 3 | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 265 | 2 | 0.75 | -0.38 | 0.98 | 1.25 / 1.18 | 0.17 / 0.16 / 0.28 | 0.19 | -0.09 | 0.98 | -0.04 | 0.00 | 433 | LEAD |
| GC 4 | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 375 | 2 | 0.72 | -0.30 | 0.20 | -0.23 / 1.15 | 0.10 / -0.71 / -0.08 | -0.08 | -0.23 | 0.81 | -0.31 | 0.00 | 583 | NO |
| GC 5 | 5m don[20] dir=against hold=180m iv60/ADR hi0.35 | 602 | 2 | 0.58 | -0.61 | 0.07 | -0.23 / 1.60 | 0.13 / -1.34 / 0.30 | -0.11 | -0.01 | 0.61 | -0.41 | 0.00 | 971 | NO |
| GC 6 | 5m st[14, 2.0] dir=against hold=60m iv60/ADR hi0.35 | 457 | 2 | 0.46 | -0.26 | -0.20 | -0.57 / 1.15 | 0.05 / -1.97 / 0.13 | -0.32 | 0.25 | 0.67 | -0.73 | 0.00 | 777 | NO |
| GC 7 | 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.25 | 763 | 2 | 0.41 | -1.02 | -0.09 | -0.38 / 1.17 | 0.05 / -0.75 / -0.64 | -0.30 | 0.41 | 0.70 | -0.52 | 0.00 | 1251 | NO |
| GC 8 (diag) | 5m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.25 | 1154 | 1 | 0.97 | -1.01 | 0.07 | -0.44 / 1.48 | 0.17 / -0.51 / -0.84 | -0.28 | -0.02 | 0.79 | -0.54 | 0.00 | 1683 | diag |
| GC 9 (diag) | 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.25 | 811 | 1 | 0.79 | -0.88 | 0.64 | 0.65 / 0.83 | 0.16 / -0.21 / -0.11 | -0.05 | -0.02 | 0.97 | -0.26 | 0.33 | 1164 | diag |
| GC 10 (diag) | 5m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | 785 | 1 | 0.66 | -1.08 | 0.77 | 1.04 / 0.87 | 0.05 / 0.33 / -0.18 | -0.04 | 0.38 | 0.99 | -0.30 | 0.67 | 1268 | diag |
| CL 1 | 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | 468 | 2 | 0.93 | -0.36 | 0.58 | 0.25 / 1.06 | 0.14 / -0.05 / -0.06 | -0.01 | 0.17 | 0.97 | -0.14 | 0.83 | 780 | NO |
| CL 2 | 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | 325 | 2 | 0.79 | -0.37 | 0.85 | 0.94 / 0.95 | 0.17 / -0.01 / 0.50 | 0.15 | -0.13 | 1.00 | 0.01 | 0.38 | 546 | NO |
| CL 3 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | 512 | 1 | 0.40 | -0.54 | 0.46 | 0.49 / 1.03 | 0.06 / -0.11 / 0.43 | 0.02 | -0.44 | 0.96 | -0.10 | 0.50 | 818 | diag |
| CL 4 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 278 | 1 | 0.36 | -0.23 | 0.24 | 0.07 / 1.08 | 0.04 / -0.08 / 0.19 | -0.02 | -0.25 | 0.85 | -0.13 | 0.50 | 452 | diag |
| CL 5 (diag) | 15m st[14, 2.0] dir=against hold=180m iv60/ADR lo0.15 | 420 | 1 | 0.20 | -0.14 | 0.05 | -0.06 / 0.62 | 0.03 / -0.20 / -0.44 | -0.23 | 0.28 | 0.96 | -0.32 | 0.00 | 631 | diag |
| ZN 1 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 238 | 0 | -1.07 | -1.99 | -1.62 | -2.96 / -2.10 | -0.22 / -0.53 / -0.39 | -0.64 | -0.50 | 1.00 | -0.48 | 0.00 | 404 | diag |
| ZN 2 (diag) | 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | 337 | 0 | -1.23 | -2.17 | -1.93 | -4.51 / -2.84 | -0.26 / -0.61 / -0.37 | -0.64 | 0.01 | 1.00 | -0.50 | 0.00 | 546 | diag |
| ZN 3 (diag) | 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | 295 | 1 | -1.34 | -1.73 | -1.76 | -2.94 / -2.88 | -0.28 / -0.40 / -0.40 | -0.59 | 0.33 | 1.00 | -0.49 | 0.00 | 490 | diag |
| BTC 1 | 15m don[20] dir=with hold=60m iv60/ADR lo0.15 | 440 | 2 | 1.75 | 0.08 | 0.57 | -1.16 / 0.45 | 0.33 / -0.78 / 0.06 | 0.02 | -0.19 | 1.00 | -0.08 | 0.33 | 651 | NO |
| BTC 2 | 15m don[20] dir=with hold=180m iv60/ADR lo0.15 | 362 | 2 | 0.94 | 0.24 | 0.49 | -0.29 / 0.76 | 0.12 / -0.46 / 0.12 | -0.01 | -0.00 | 0.95 | -0.15 | 0.17 | 538 | NO |
| BTC 3 | 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | 1159 | 2 | 0.87 | -2.57 | 0.57 | 0.05 / 1.20 | 0.15 / -0.69 / 0.10 | -0.05 | -0.27 | 0.97 | -0.16 | 0.00 | 1800 | NO |
| BTC 4 | 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | 297 | 2 | 0.84 | -0.47 | 0.05 | -0.86 / 0.82 | 0.14 / -1.07 / -0.02 | -0.11 | 0.00 | 0.77 | -0.28 | 0.00 | 447 | NO |
| BTC 5 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | 309 | 2 | 0.78 | 1.53 | 0.55 | 0.18 / 1.01 | 0.11 / 0.12 / -0.00 | 0.04 | 0.00 | 0.92 | -0.10 | 0.67 | 461 | NO |
| BTC 6 | 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | 607 | 2 | 0.70 | 1.23 | 0.68 | 0.78 / 1.47 | 0.14 / 0.37 / -0.10 | 0.07 | -0.25 | 0.99 | -0.06 | 0.50 | 908 | NO |
| BTC 7 | 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | 698 | 2 | 0.64 | -0.43 | 0.42 | 0.28 / 1.19 | 0.07 / 0.21 / -0.14 | -0.01 | 0.20 | 0.93 | -0.17 | 0.50 | 1065 | NO |
| BTC 8 | 5m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR lo0.15 | 334 | 2 | 0.62 | 0.21 | 0.11 | -1.11 / 0.62 | 0.07 / 0.03 / -0.22 | -0.06 | 0.03 | 0.98 | -0.17 | 0.00 | 516 | NO |
| BTC 9 | 5m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.35 | 699 | 2 | 0.46 | -1.01 | 0.28 | -0.04 / 1.11 | 0.04 / -0.18 / 0.03 | -0.05 | -0.27 | 0.96 | -0.18 | 0.25 | 1032 | NO |
| BTC 10 | 15m st[14, 2.0] dir=with hold=60m iv60/ADR lo0.25 | 1231 | 2 | 0.40 | -1.83 | -0.04 | -0.58 / 0.76 | 0.03 / -0.61 / 0.10 | -0.19 | 0.04 | 0.91 | -0.25 | 0.00 | 1982 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 54 |
| diagnostic cells read | 14 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 41 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 32 |
| worst-decile corr <= +0.30 | 57 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 8 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | clean | 0.62 | 1.13 | -106715 | -86682 | 322625 | -138051 | 1.75 | 50.5 | 1.60 | -87338 | 276506 | -105693 |
| BTC 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | H1 | 1.53 | 2.83 | -95728 | -83120 | 282329 | -128806 | 1.29 | 50.0 | 3.19 | -78231 | 166468 | -79213 |
| BTC 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | H2 | -0.02 | -0.03 | -71223 | -62381 | 263339 | -71929 | -0.02 | 50.0 | 2.20 | -89942 | 214222 | -92296 |
| BTC 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | all | 0.68 | 1.22 | -101282 | -81969 | 322625 | -138051 | 2.87 | 50.6 | 1.98 | -87268 | 276506 | -105693 |
| CL 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | clean | 0.79 | 1.21 | -125397 | -100026 | 471248 | -254183 | 1.53 | 41.9 | 1.63 | -81335 | 252504 | -85317 |
| CL 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | H1 | -1.04 | -1.48 | -79705 | -71251 | 325692 | -96684 | -0.50 | 53.6 | 2.82 | -76257 | 152146 | -81234 |
| CL 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | H2 | 1.58 | 2.75 | -233562 | -193509 | 432482 | -235918 | 2.27 | 38.9 | 2.79 | -83418 | 223404 | -84311 |
| CL 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | all | 0.85 | 1.39 | -162447 | -122494 | 583511 | -254183 | 2.63 | 43.5 | 2.08 | -81787 | 252504 | -85317 |
| ES 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | clean | 1.55 | 3.41 | -96365 | -80696 | 250374 | -107511 | 5.62 | 28.6 | 1.73 | -81782 | 277833 | -90075 |
| ES 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | H1 | 0.01 | 0.02 | -154133 | -138239 | 344070 | -157542 | 0.01 | 39.3 | 2.90 | -63475 | 174569 | -66374 |
| ES 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | H2 | 0.76 | 1.17 | -126760 | -101887 | 235187 | -134937 | 0.96 | 41.7 | 2.36 | -91828 | 228946 | -101132 |
| ES 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | all | 1.11 | 2.01 | -119049 | -98887 | 524051 | -157542 | 3.12 | 33.3 | 2.04 | -83778 | 277833 | -101132 |
| GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | clean | 0.77 | 1.19 | -128483 | -107311 | 640181 | -187950 | 1.09 | 43.8 | 1.63 | -87872 | 244344 | -99253 |
| GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | H1 | 1.74 | 3.03 | -223504 | -204925 | 704823 | -276428 | 1.34 | 32.1 | 2.99 | -120677 | 198984 | -133573 |
| GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | H2 | 0.80 | 1.24 | -227703 | -191071 | 613247 | -237050 | 0.76 | 30.6 | 2.57 | -95069 | 284964 | -107614 |
| GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | all | 0.98 | 1.57 | -191251 | -155801 | 981488 | -276428 | 2.15 | 39.3 | 2.09 | -98048 | 284964 | -133573 |
| NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | clean | 1.75 | 2.95 | -104102 | -91530 | 267140 | -142473 | 5.98 | 40.0 | 1.81 | -86801 | 251351 | -95947 |
| NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | H1 | 3.34 | 7.91 | -66812 | -65776 | 142716 | -69290 | 5.78 | 35.7 | 3.45 | -72800 | 143363 | -78789 |
| NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | H2 | -0.69 | -0.86 | -314673 | -256886 | 841542 | -316003 | -0.50 | 47.2 | 2.02 | -92314 | 195369 | -105970 |
| NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | all | 1.07 | 1.56 | -183336 | -138744 | 841542 | -316003 | 2.38 | 41.1 | 2.11 | -87136 | 251351 | -105970 |
| RTY 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | clean | 0.29 | 0.42 | -135565 | -108506 | 729525 | -239847 | 0.36 | 45.7 | 1.53 | -91356 | 260542 | -125013 |
| RTY 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | H1 | 1.76 | 2.97 | -87380 | -72043 | 170120 | -93208 | 1.86 | 42.9 | 3.09 | -77012 | 155651 | -94598 |
| RTY 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | H2 | 1.11 | 2.00 | -110579 | -95072 | 250369 | -113792 | 1.51 | 41.7 | 2.51 | -84936 | 211860 | -91971 |
| RTY 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | all | 0.67 | 1.03 | -126063 | -102860 | 729525 | -239847 | 1.32 | 44.6 | 1.99 | -90290 | 260542 | -125013 |
| YM 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | clean | 1.01 | 1.66 | -105739 | -92479 | 557308 | -176104 | 1.65 | 42.9 | 1.61 | -86180 | 248992 | -95124 |
| YM 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | H1 | 2.10 | 4.98 | -79563 | -70907 | 165316 | -84828 | 3.21 | 46.4 | 3.18 | -71216 | 161639 | -79171 |
| YM 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | H2 | -0.48 | -0.63 | -222962 | -182663 | 628772 | -246324 | -0.36 | 50.0 | 2.15 | -89518 | 219378 | -94186 |
| YM 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | all | 0.74 | 1.13 | -147502 | -117361 | 628772 | -246324 | 1.94 | 45.2 | 1.97 | -86143 | 248992 | -95124 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 (diag) | clean | -1.03 | -1.45 | -126988 | -111681 | 968789 | -132843 | -0.96 | 52.4 | 1.24 | -89460 | 323847 | -99730 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 (diag) | H1 | -3.07 | -2.98 | -149676 | -132215 | 596395 | -163855 | -0.99 | 57.1 | 2.30 | -72840 | 168671 | -77868 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 (diag) | H2 | -2.84 | -3.10 | -79517 | -76933 | 613224 | -80600 | -1.00 | 63.9 | 1.91 | -77684 | 220577 | -78655 |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 (diag) | all | -1.62 | -2.05 | -130453 | -109820 | 2137549 | -163855 | -1.00 | 56.0 | 1.55 | -86108 | 323847 | -99730 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | -11.7 | -8.8 | 18.7 | 31.2 | 15.0 / 22.2 | 18.7 / 33.3 | NO |
| NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | -7.6 | -12.6 | 11.8 | 25.3 | -0.2 / 12.8 | 29.0 / 32.6 | NO |
| RTY 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | -19.3 | -52.5 | 8.1 | 15.3 | -53.8 / 5.3 | -1.3 / 23.0 | NO |
| YM 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | -16.4 | 2.4 | 14.5 | 32.3 | 1.7 / 14.2 | 26.9 / 29.9 | NO |
| GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | -6.5 | -66.9 | -10.5 | -2.9 | -6.5 / 8.1 | -75.9 / -53.2 | NO |
| CL 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | -12.8 | -14.3 | 18.3 | 32.8 | -15.2 / 15.8 | 24.4 / 32.6 | NO |
| ZN 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 (diag) | -53.9 | -6.5 | 12.9 | -7.8 | -7.3 / 7.4 | 29.4 / 29.5 | NO |
| BTC 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | -19.6 | -16.4 | 11.6 | 18.8 | -17.3 / 8.6 | 28.2 / 28.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1683 | 16.8 | -12.5 | 1.9 | 29.4 | 0.24 / -0.18 / 0.03 | 225.2 / 195.8 |
| ES 2 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | positive pre-2023 | 1111 | 32.0 | 2.6 | 16.9 | 29.4 | 0.40 / 0.03 / 0.21 | 240.4 / 211.0 |
| ES 3 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | gross-positive, cost-negative pre-2023 | 2023 | 12.2 | -17.1 | -2.9 | 29.4 | 0.22 / -0.31 / -0.05 | 162.6 / 133.2 |
| ES 4 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | gross-positive, cost-negative pre-2023 | 2944 | 9.7 | -19.7 | -5.3 | 29.4 | 0.21 / -0.43 / -0.12 | 108.5 / 79.2 |
| ES 5 5m don[20] dir=with hold=180m iv60/ADR hi0.25 | negative pre-2023 | 5298 | -8.9 | -38.3 | -23.9 | 29.4 | -0.27 / -1.18 / -0.73 | 97.9 / 68.5 |
| ES 6 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | positive pre-2023 | 2243 | 35.9 | 6.5 | 20.9 | 29.4 | 0.61 / 0.11 / 0.36 | 69.1 / 39.8 |
| ES 7 15m don[20] dir=against hold=180m iv60/ADR hi0.25 | gross-positive, cost-negative pre-2023 | 3849 | 15.6 | -13.8 | 0.6 | 29.4 | 0.38 / -0.34 / 0.01 | 35.8 / 6.4 |
| ES 8 (diag) 5m don[20] dir=with hold=60m iv60/ADR hi0.35 | negative pre-2023 | 4900 | -2.7 | -32.0 | -17.6 | 29.4 | -0.11 / -1.33 / -0.73 | 73.7 / 44.4 |
| ES 9 (diag) 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 3021 | 6.3 | -23.1 | -8.7 | 29.4 | 0.15 / -0.56 / -0.21 | 92.8 / 63.5 |
| ES 10 (diag) 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.25 | negative pre-2023 | 4564 | -5.9 | -35.3 | -21.2 | 29.4 | -0.24 / -1.42 / -0.85 | 48.4 / 19.0 |
| NQ 1 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | gross-positive, cost-negative pre-2023 | 8596 | 8.9 | -5.4 | 3.1 | 14.4 | 0.39 / -0.23 / 0.14 | 83.3 / 68.9 |
| NQ 2 15m don[20] dir=against hold=180m iv60/ADR hi0.25 | positive pre-2023 | 3734 | 21.2 | 6.8 | 15.4 | 14.4 | 0.34 / 0.11 / 0.24 | 184.5 / 170.1 |
| NQ 3 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 2281 | 14.7 | 0.3 | 8.9 | 14.4 | 0.17 / -0.00 / 0.10 | 295.3 / 280.9 |
| NQ 4 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | positive pre-2023 | 3034 | 51.8 | 37.5 | 46.0 | 14.4 | 0.71 / 0.51 / 0.63 | 181.0 / 166.6 |
| NQ 5 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | positive pre-2023 | 2127 | 30.9 | 16.6 | 25.0 | 14.4 | 0.39 / 0.21 / 0.31 | 204.2 / 189.8 |
| NQ 6 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | positive pre-2023 | 1883 | 67.1 | 52.8 | 61.4 | 14.4 | 0.62 / 0.48 / 0.56 | 173.6 / 159.2 |
| NQ 7 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | positive pre-2023 | 1260 | 52.7 | 38.3 | 46.8 | 14.4 | 0.45 / 0.33 / 0.40 | 220.9 / 206.6 |
| NQ 8 5m don[20] dir=with hold=60m iv60/ADR hi0.25 | negative pre-2023 | 8667 | -8.7 | -23.1 | -14.5 | 14.4 | -0.35 / -0.93 / -0.58 | 73.7 / 59.3 |
| NQ 9 5m st[14, 2.0] dir=against hold=60m iv60/ADR hi0.35 | negative pre-2023 | 2686 | -26.4 | -40.7 | -32.1 | 14.4 | -0.47 / -0.72 / -0.57 | 110.2 / 95.9 |
| NQ 10 5m st[14, 2.0] dir=against hold=180m iv60/ADR lo0.25 | gross-positive, cost-negative pre-2023 | 10636 | 4.2 | -10.1 | -1.5 | 14.4 | 0.16 / -0.37 / -0.05 | 50.2 / 35.9 |
| RTY 1 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1351 | -2.4 | -16.8 | -14.5 | 14.4 | -0.05 / -0.31 / -0.27 | 68.9 / 54.6 |
| RTY 2 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1139 | 4.4 | -9.9 | -7.6 | 14.4 | 0.08 / -0.18 / -0.14 | 66.3 / 51.9 |
| RTY 3 5m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1224 | -43.0 | -57.4 | -55.1 | 14.4 | -0.87 / -1.15 / -1.10 | 77.9 / 63.5 |
| RTY 4 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | gross-positive, cost-negative pre-2023 | 1581 | 2.2 | -12.1 | -9.7 | 14.4 | 0.09 / -0.48 / -0.39 | 34.0 / 19.7 |
| RTY 5 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | negative pre-2023 | 785 | -14.0 | -28.4 | -26.0 | 14.4 | -0.24 / -0.48 / -0.44 | 60.0 / 45.7 |
| RTY 6 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.25 | negative pre-2023 | 2718 | -14.5 | -28.8 | -26.6 | 14.4 | -0.63 / -1.25 / -1.15 | 25.1 / 10.8 |
| RTY 7 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | negative pre-2023 | 984 | -1.1 | -15.5 | -13.1 | 14.4 | -0.03 / -0.43 / -0.36 | 26.4 / 12.0 |
| RTY 8 15m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1033 | -21.9 | -36.3 | -34.0 | 14.4 | -0.37 / -0.62 / -0.58 | 31.4 / 17.0 |
| RTY 9 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | negative pre-2023 | 1567 | -16.2 | -30.6 | -28.4 | 14.4 | -0.60 / -1.12 / -1.04 | 22.1 / 7.7 |
| RTY 10 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.15 | negative pre-2023 | 1579 | -11.0 | -25.4 | -23.5 | 14.4 | -0.59 / -1.34 / -1.24 | 13.3 / -1.1 |
| YM 1 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.25 | negative pre-2023 | 4080 | -2.4 | -16.8 | -11.0 | 14.4 | -0.12 / -0.83 / -0.54 | 51.4 / 37.0 |
| YM 2 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | negative pre-2023 | 2817 | -1.8 | -16.1 | -10.5 | 14.4 | -0.07 / -0.66 / -0.43 | 43.3 / 28.9 |
| YM 3 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.35 | negative pre-2023 | 2142 | -7.2 | -21.6 | -15.8 | 14.4 | -0.23 / -0.68 / -0.50 | 45.7 / 31.4 |
| YM 4 15m don[20] dir=with hold=60m iv60/ADR hi0.25 | negative pre-2023 | 5386 | -1.2 | -15.6 | -9.8 | 14.4 | -0.07 / -0.90 / -0.57 | 33.3 / 19.0 |
| YM 5 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1619 | 3.5 | -10.9 | -5.2 | 14.4 | 0.09 / -0.30 / -0.14 | 42.5 / 28.1 |
| YM 6 15m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1511 | 5.9 | -8.4 | -2.7 | 14.4 | 0.10 / -0.14 / -0.05 | 46.1 / 31.8 |
| YM 7 15m don[20] dir=against hold=180m iv60/ADR lo0.15 | gross-positive, cost-negative pre-2023 | 3242 | 2.8 | -11.5 | -6.0 | 14.4 | 0.13 / -0.55 / -0.29 | 26.3 / 11.9 |
| YM 8 5m st[14, 2.0] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1765 | -34.2 | -48.6 | -42.7 | 14.4 | -0.59 / -0.83 / -0.73 | 27.5 / 13.1 |
| YM 9 (diag) 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 2993 | 11.9 | -2.4 | 3.4 | 14.4 | 0.30 / -0.06 / 0.09 | 80.5 / 66.2 |
| YM 10 (diag) 5m don[20] dir=with hold=60m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 4781 | 2.3 | -12.0 | -6.2 | 14.4 | 0.12 / -0.61 / -0.32 | 50.4 / 36.1 |
| GC 1 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.15 | gross-positive, cost-negative pre-2023 | 1840 | 6.4 | -17.9 | -8.5 | 24.4 | 0.21 / -0.61 / -0.29 | 63.2 / 38.9 |
| GC 2 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 2462 | -5.7 | -30.1 | -20.3 | 24.4 | -0.11 / -0.59 / -0.40 | 89.5 / 65.1 |
| GC 3 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1234 | -3.6 | -27.9 | -18.5 | 24.4 | -0.05 / -0.38 / -0.25 | 92.7 / 68.3 |
| GC 4 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1797 | 6.0 | -18.3 | -8.6 | 24.4 | 0.10 / -0.30 / -0.14 | 96.5 / 72.1 |
| GC 5 5m don[20] dir=against hold=180m iv60/ADR hi0.35 | negative pre-2023 | 3146 | -2.6 | -26.9 | -17.2 | 24.4 | -0.05 / -0.61 / -0.38 | 72.1 / 47.7 |
| GC 6 5m st[14, 2.0] dir=against hold=60m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 2338 | 15.1 | -9.3 | 0.3 | 24.4 | 0.41 / -0.26 / 0.00 | 50.2 / 25.9 |
| GC 7 15m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.25 | negative pre-2023 | 3913 | -0.0 | -24.4 | -14.7 | 24.4 | 0.01 / -1.02 / -0.61 | 42.4 / 18.0 |
| GC 8 (diag) 5m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.25 | gross-positive, cost-negative pre-2023 | 5279 | 4.5 | -19.8 | -10.2 | 24.4 | 0.22 / -1.01 / -0.52 | 55.0 / 30.7 |
| GC 9 (diag) 15m vwz[2.0, 'globex'] dir=against hold=180m iv60/ADR lo0.25 | gross-positive, cost-negative pre-2023 | 3465 | 4.2 | -20.2 | -10.6 | 24.4 | 0.17 / -0.88 / -0.47 | 51.2 / 26.9 |
| GC 10 (diag) 5m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | negative pre-2023 | 4008 | -1.2 | -25.5 | -15.9 | 24.4 | -0.05 / -1.08 / -0.67 | 45.6 / 21.2 |
| CL 1 15m don[20] dir=against hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 2503 | 8.3 | -16.1 | -13.8 | 24.4 | 0.18 / -0.36 / -0.31 | 74.9 / 50.5 |
| CL 2 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1695 | 2.0 | -22.4 | -19.9 | 24.4 | 0.03 / -0.37 / -0.33 | 73.3 / 49.0 |
| CL 3 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.25 | negative pre-2023 | 2428 | -2.2 | -26.5 | -24.0 | 24.4 | -0.04 / -0.54 / -0.49 | 43.7 / 19.3 |
| CL 4 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1428 | 8.1 | -16.2 | -13.7 | 24.4 | 0.12 / -0.23 / -0.19 | 47.8 / 23.4 |
| CL 5 (diag) 15m st[14, 2.0] dir=against hold=180m iv60/ADR lo0.15 | gross-positive, cost-negative pre-2023 | 2017 | 19.1 | -5.3 | -2.3 | 24.4 | 0.53 / -0.14 / -0.06 | 30.0 / 5.6 |
| ZN 1 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | negative pre-2023 | 1228 | -6.1 | -41.7 | -46.8 | 35.6 | -0.29 / -1.99 / -2.23 | 15.2 / -20.4 |
| ZN 2 (diag) 5m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1832 | 0.3 | -35.3 | -40.5 | 35.6 | 0.02 / -2.17 / -2.47 | 9.8 / -25.8 |
| ZN 3 (diag) 15m st[14, 2.0] dir=with hold=180m iv60/ADR hi0.35 | gross-positive, cost-negative pre-2023 | 1550 | 4.0 | -31.6 | -36.8 | 35.6 | 0.22 / -1.73 / -2.01 | 5.6 / -30.0 |
| BTC 1 15m don[20] dir=with hold=60m iv60/ADR lo0.15 | positive pre-2023 | 269 | 56.7 | 2.3 | 36.1 | 54.4 | 1.43 / 0.08 / 0.93 | 228.8 / 174.4 |
| BTC 2 15m don[20] dir=with hold=180m iv60/ADR lo0.15 | positive pre-2023 | 226 | 86.0 | 31.6 | 65.3 | 54.4 | 0.71 / 0.24 / 0.53 | 270.3 / 215.9 |
| BTC 3 5m don[20] dir=against hold=180m iv60/ADR lo0.15 | negative pre-2023 | 851 | -65.3 | -119.7 | -86.4 | 54.4 | -1.40 / -2.57 / -1.85 | 154.9 / 100.5 |
| BTC 4 15m st[14, 2.0] dir=with hold=180m iv60/ADR lo0.15 | gross-positive, cost-negative pre-2023 | 271 | 3.6 | -50.8 | -17.2 | 54.4 | 0.09 / -0.47 / -0.13 | 241.6 / 187.2 |
| BTC 5 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.35 | positive pre-2023 | 202 | 283.4 | 229.1 | 260.5 | 54.4 | 1.85 / 1.53 / 1.72 | 264.8 / 210.4 |
| BTC 6 15m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR hi0.25 | positive pre-2023 | 367 | 175.3 | 121.0 | 152.5 | 54.4 | 1.75 / 1.23 / 1.54 | 172.8 / 118.4 |
| BTC 7 5m don[20] dir=with hold=180m iv60/ADR hi0.35 | negative pre-2023 | 496 | -2.0 | -56.4 | -24.9 | 54.4 | -0.02 / -0.43 / -0.19 | 158.5 / 104.2 |
| BTC 8 5m vwz[2.0, 'globex'] dir=against hold=60m iv60/ADR lo0.15 | positive pre-2023 | 200 | 67.6 | 13.3 | 47.3 | 54.4 | 1.08 / 0.21 / 0.76 | 170.4 / 116.1 |
| BTC 9 5m st[14, 2.0] dir=with hold=60m iv60/ADR hi0.35 | negative pre-2023 | 456 | -58.9 | -113.3 | -81.3 | 54.4 | -0.53 / -1.01 / -0.73 | 130.5 / 76.1 |
| BTC 10 15m st[14, 2.0] dir=with hold=60m iv60/ADR lo0.25 | negative pre-2023 | 905 | -18.7 | -73.1 | -40.3 | 54.4 | -0.47 / -1.83 / -1.01 | 78.8 / 24.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 17 cells pass the clean rule against a replicate mean of 8.9 (p(count) = 0.00, p(top) = 0.28); CL: 2 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.60, p(top) = 0.11); ES: 7 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.03, p(top) = 0.01); GC: 7 cells pass the clean rule against a replicate mean of 3.9 (p(count) = 0.04, p(top) = 0.39); NQ: 17 cells pass the clean rule against a replicate mean of 12.5 (p(count) = 0.14, p(top) = 0.00); RTY: 10 cells pass the clean rule against a replicate mean of 4.9 (p(count) = 0.00, p(top) = 0.60); YM: 8 cells pass the clean rule against a replicate mean of 5.3 (p(count) = 0.21, p(top) = 0.20); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 54 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.26 (NQ 5m don[20] dir=against hold=180m iv60/ADR lo0.15); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 8; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell GC 15m vwz[2.0, 'globex'] dir=with hold=180m iv60/ADR hi0.35: uplift +0.17/+0.16/+0.28, boot lo -0.04, plateau 0.00, 2x-slip +0.19, wd corr -0.09, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 24, 'gross-positive, cost-negative pre-2023': 18, 'positive pre-2023': 12}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_14.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw14/ (`SW14_CO_all_selected_scored.csv`).

DONE SW14
