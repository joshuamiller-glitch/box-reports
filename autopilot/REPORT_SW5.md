# REPORT SW5 - clock-anchored short-hold sleeves (D06 H1/H2)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 59 selected cells (+8 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.29; best pair-window standalone Sharpe +1.90.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: at each of 12 ET anchor minutes (03:00, 08:00, 08:30, 09:00, 09:30, 10:00, 11:00, 12:00, 13:30, 14:00, 15:00, 15:30) enter with or against the sign of the prior 15/30/60-min return, exact hold 5/15/30/60 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 288 cells per instrument = 12 anchors x 3 lookbacks x 2 directions x 4 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     288 |        288 |        23 |               1.427 |                2 |         10 |            0 |
| CL    |     288 |        288 |         1 |               0.742 |                2 |          1 |            3 |
| ES    |     288 |        288 |        11 |               1.37  |                2 |         10 |            0 |
| GC    |     288 |        288 |         8 |               0.885 |                2 |          8 |            2 |
| NQ    |     288 |        288 |        38 |               1.878 |                2 |         10 |            0 |
| RTY   |     288 |        288 |        17 |               0.94  |                2 |         10 |            0 |
| YM    |     288 |        288 |        27 |               2.266 |                2 |         10 |            0 |
| ZN    |     288 |        288 |         0 |              -2.157 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   11 |            2.41  |               7 |      0     |                       0.585 |            0.516 |           0.876 |    0.31  |       1.37  |                1.262 |
| NQ    |     200 |                   38 |           29.135 |              41 |      0.06  |                       1.21  |            1.072 |           1.306 |    0.14  |       1.878 |                2.045 |
| RTY   |     200 |                   17 |            5.395 |              11 |      0     |                       0.606 |            0.541 |           0.848 |    0.32  |       0.901 |                1.611 |
| YM    |     200 |                   27 |            6.56  |              14 |      0     |                       1.744 |            0.571 |           0.805 |    0     |       2.266 |                1.624 |
| GC    |     200 |                    8 |            4.675 |              12 |      0.095 |                       0.437 |            0.54  |           0.798 |    0.735 |       0.885 |                1.54  |
| CL    |     100 |                    1 |            1.23  |               4 |      0.73  |                       0.6   |            0.473 |           0.861 |    0.21  |       0.6   |                1.16  |
| ZN    |     100 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| BTC   |     100 |                   23 |           25.19  |              36 |      0.68  |                       0.869 |            0.983 |           1.196 |    0.79  |       1.427 |                2.093 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | clock 09:30 ret30m dir=against hold=30m | 509 | 2 | 1.37 | -0.80 | 0.64 | -0.36 / 0.50 | 0.19 / -0.22 / -0.17 | -0.07 | 0.10 | 1.00 | -0.15 | 0.25 | 808 | NO |
| ES 2 | clock 09:30 ret30m dir=against hold=60m | 509 | 2 | 0.93 | -0.78 | -0.18 | -1.71 / 0.65 | 0.14 / -0.95 / -0.22 | -0.19 | 0.19 | 0.85 | -0.30 | 0.00 | 808 | NO |
| ES 3 | clock 08:00 ret60m dir=against hold=60m | 513 | 2 | 0.72 | -0.46 | -0.13 | -1.65 / 0.70 | 0.08 / -0.23 / -0.32 | -0.17 | 0.16 | 0.80 | -0.24 | 0.00 | 817 | NO |
| ES 4 | clock 10:00 ret15m dir=with hold=60m | 509 | 2 | 0.67 | -1.10 | 0.06 | -0.97 / 0.56 | 0.07 / -0.16 / -0.20 | -0.12 | -0.50 | 0.93 | -0.22 | 0.00 | 815 | NO |
| ES 5 | clock 13:30 ret30m dir=with hold=60m | 490 | 2 | 0.44 | -0.99 | -0.98 | -3.28 / 0.75 | 0.08 / -1.12 / -0.54 | -0.36 | -0.20 | 0.38 | -0.44 | 0.00 | 788 | NO |
| ES 6 | clock 11:00 ret15m dir=against hold=30m | 509 | 2 | 0.42 | -1.50 | -0.42 | -1.37 / 0.36 | 0.09 / 0.62 / -0.90 | -0.24 | 0.02 | 0.89 | -0.28 | 0.00 | 815 | NO |
| ES 7 | clock 12:00 ret60m dir=with hold=60m | 497 | 2 | 0.41 | -0.96 | 0.66 | 1.13 / 0.61 | -0.02 / 0.48 / 0.03 | -0.06 | 0.14 | 1.00 | -0.11 | 0.25 | 798 | NO |
| ES 8 | clock 13:30 ret15m dir=with hold=60m | 485 | 2 | 0.34 | -0.69 | -0.24 | -1.35 / 0.77 | 0.03 / -0.26 / -0.31 | -0.19 | 0.71 | 0.82 | -0.26 | 0.00 | 779 | NO |
| ES 9 | clock 14:00 ret60m dir=with hold=30m | 492 | 2 | 0.27 | -1.54 | -0.69 | -2.48 / 0.27 | 0.10 / -0.24 / -0.62 | -0.28 | -0.01 | 0.75 | -0.30 | 0.00 | 785 | NO |
| ES 10 | clock 15:30 ret30m dir=against hold=60m | 486 | 2 | 0.26 | -1.11 | -0.36 | -1.45 / 0.96 | 0.00 / -0.49 / -0.24 | -0.25 | -0.35 | 0.78 | -0.32 | 0.00 | 777 | NO |
| NQ 1 | clock 10:00 ret15m dir=with hold=15m | 515 | 2 | 1.88 | 0.11 | 1.07 | 0.02 / 1.03 | 0.35 / -0.08 / 0.03 | 0.18 | -0.07 | 0.99 | 0.03 | 0.25 | 825 | NO |
| NQ 2 | clock 10:00 ret15m dir=with hold=5m | 515 | 2 | 1.37 | 0.07 | 0.28 | -1.05 / 0.46 | 0.27 / 0.08 / -0.44 | 0.02 | 0.25 | 0.99 | -0.14 | 0.75 | 825 | NO |
| NQ 3 | clock 09:30 ret30m dir=against hold=30m | 507 | 2 | 1.28 | -0.04 | -0.34 | -2.03 / 1.07 | 0.19 / -0.87 / -0.61 | -0.17 | -0.40 | 0.32 | -0.38 | 0.00 | 817 | NO |
| NQ 4 | clock 10:00 ret15m dir=with hold=60m | 515 | 2 | 1.19 | 0.05 | 0.17 | -0.98 / 1.42 | 0.21 / -0.10 / -0.37 | 0.00 | -0.64 | 0.77 | -0.19 | 0.25 | 825 | NO |
| NQ 5 | clock 14:00 ret30m dir=with hold=5m | 497 | 2 | 1.16 | -1.16 | 0.09 | -1.18 / 0.95 | 0.21 / 0.17 / -0.89 | -0.13 | 0.19 | 0.90 | -0.27 | 0.00 | 796 | NO |
| NQ 6 | clock 10:00 ret60m dir=with hold=15m | 516 | 2 | 1.13 | -0.25 | 0.59 | -0.24 / 0.90 | 0.13 / -0.26 / -0.07 | 0.00 | 0.43 | 0.99 | -0.15 | 0.00 | 825 | NO |
| NQ 7 | clock 15:30 ret30m dir=against hold=60m | 497 | 2 | 1.04 | -0.68 | 0.09 | -1.22 / 1.29 | 0.18 / -0.31 / -0.40 | -0.05 | -0.09 | 0.68 | -0.22 | 0.00 | 796 | NO |
| NQ 8 | clock 15:00 ret15m dir=against hold=60m | 493 | 2 | 1.03 | -1.06 | 1.23 | 1.54 / 1.08 | 0.18 / 0.66 / 0.06 | 0.20 | 0.16 | 1.00 | 0.04 | 0.75 | 793 | NO |
| NQ 9 | clock 15:30 ret30m dir=against hold=30m | 497 | 2 | 1.02 | -1.01 | 0.27 | -0.85 / 1.45 | 0.16 / -0.22 / -0.20 | -0.02 | -0.11 | 0.82 | -0.19 | 0.50 | 796 | NO |
| NQ 10 | clock 14:00 ret60m dir=with hold=30m | 495 | 2 | 1.02 | -0.52 | -0.22 | -2.01 / 1.03 | 0.23 / -0.33 / -0.65 | -0.10 | -0.04 | 0.49 | -0.26 | 0.00 | 795 | NO |
| RTY 1 | clock 09:00 ret60m dir=against hold=30m | 510 | 2 | 0.90 | -0.82 | 0.40 | -0.28 / 0.79 | 0.13 / -0.07 / -0.22 | -0.15 | 0.41 | 1.00 | -0.17 | 0.25 | 817 | NO |
| RTY 2 | clock 09:30 ret30m dir=against hold=15m | 505 | 2 | 0.86 | -0.07 | 0.67 | 0.50 / 0.09 | 0.09 / 0.31 / -0.33 | -0.06 | 0.39 | 1.00 | -0.17 | 0.25 | 812 | NO |
| RTY 3 | clock 08:00 ret60m dir=against hold=60m | 505 | 2 | 0.74 | 0.15 | -0.08 | -1.74 / 1.10 | 0.10 / -0.22 / -0.30 | -0.10 | -0.04 | 0.86 | -0.22 | 0.00 | 811 | NO |
| RTY 4 | clock 09:30 ret30m dir=against hold=5m | 505 | 2 | 0.66 | -0.65 | 0.29 | -0.20 / -1.03 | 0.08 / 0.46 / -0.55 | -0.12 | 0.39 | 1.00 | -0.20 | 0.00 | 812 | NO |
| RTY 5 | clock 08:00 ret30m dir=against hold=60m | 501 | 2 | 0.62 | -0.17 | 0.02 | -1.14 / 0.96 | 0.08 / -0.30 / -0.23 | -0.10 | 0.40 | 0.87 | -0.22 | 0.00 | 803 | NO |
| RTY 6 | clock 08:30 ret15m dir=with hold=5m | 501 | 2 | 0.62 | -1.56 | 0.52 | 0.33 / -0.96 | 0.09 / 0.09 / 0.01 | -0.02 | -0.13 | 1.00 | -0.11 | 0.25 | 800 | NO |
| RTY 7 | clock 08:30 ret60m dir=against hold=60m | 504 | 2 | 0.48 | -0.22 | -0.32 | -2.48 / 0.73 | 0.06 / -0.33 / -0.26 | -0.13 | 0.17 | 0.72 | -0.24 | 0.00 | 807 | NO |
| RTY 8 | clock 10:00 ret60m dir=against hold=60m | 515 | 2 | 0.42 | -1.16 | 0.04 | -0.49 / 0.76 | 0.09 / -0.40 / -0.05 | -0.06 | -0.40 | 0.92 | -0.21 | 0.00 | 822 | NO |
| RTY 9 | clock 08:30 ret15m dir=with hold=30m | 501 | 2 | 0.41 | -1.15 | 0.21 | -0.23 / 0.21 | 0.06 / 0.14 / -0.13 | -0.05 | 0.09 | 0.95 | -0.16 | 0.25 | 800 | NO |
| RTY 10 | clock 09:30 ret15m dir=against hold=5m | 508 | 2 | 0.34 | -1.34 | 0.07 | -0.23 / -0.98 | 0.01 / -0.15 / -0.27 | -0.17 | 0.40 | 1.00 | -0.25 | 0.00 | 808 | NO |
| YM 1 | clock 09:30 ret15m dir=against hold=30m | 511 | 2 | 2.27 | -0.81 | 1.45 | 0.51 / 0.64 | 0.40 / -0.03 / 0.18 | 0.23 | -0.22 | 1.00 | 0.08 | 0.75 | 819 | NO |
| YM 2 | clock 09:30 ret15m dir=against hold=60m | 511 | 2 | 2.25 | -1.00 | 1.32 | 0.22 / 0.76 | 0.41 / -0.35 / 0.25 | 0.22 | -0.13 | 1.00 | 0.05 | 0.75 | 819 | NO |
| YM 3 | clock 09:30 ret15m dir=against hold=5m | 511 | 2 | 1.99 | -0.70 | 1.09 | 0.14 / -0.40 | 0.32 / -0.35 / 0.08 | 0.07 | -0.09 | 1.00 | -0.03 | 0.50 | 819 | NO |
| YM 4 | clock 09:30 ret15m dir=against hold=15m | 511 | 2 | 1.88 | -0.66 | 0.97 | 0.06 / 0.44 | 0.35 / -0.51 / 0.24 | 0.12 | -0.25 | 1.00 | -0.01 | 0.50 | 819 | NO |
| YM 5 | clock 09:30 ret30m dir=against hold=30m | 511 | 2 | 1.79 | -0.26 | 1.90 | 2.05 / 0.50 | 0.24 / 0.29 / 0.51 | 0.24 | -0.17 | 1.00 | 0.11 | 0.50 | 820 | LEAD(gate3-7 fail: plateau ) |
| YM 6 | clock 09:30 ret30m dir=against hold=60m | 511 | 2 | 1.75 | -0.45 | 1.57 | 1.35 / 1.37 | 0.23 / -0.14 / 0.54 | 0.19 | -0.17 | 1.00 | 0.04 | 0.75 | 820 | NO |
| YM 7 | clock 09:00 ret30m dir=with hold=60m | 506 | 2 | 1.67 | -0.35 | 0.86 | -0.05 / 0.68 | 0.30 / -0.13 / 0.05 | 0.12 | -0.21 | 1.00 | -0.04 | 0.00 | 811 | NO |
| YM 8 | clock 09:30 ret30m dir=against hold=15m | 511 | 2 | 1.49 | -0.43 | 1.52 | 1.57 / 0.15 | 0.21 / -0.04 / 0.49 | 0.16 | -0.14 | 1.00 | 0.04 | 0.50 | 820 | NO |
| YM 9 | clock 09:30 ret30m dir=against hold=5m | 511 | 2 | 1.38 | -0.87 | 1.16 | 0.89 / -0.50 | 0.19 / -0.14 / 0.22 | 0.07 | 0.20 | 1.00 | -0.03 | 0.50 | 820 | NO |
| YM 10 | clock 13:30 ret15m dir=with hold=60m | 493 | 2 | 1.00 | -0.13 | 0.22 | -1.20 / 0.95 | 0.17 / -0.17 / -0.36 | -0.06 | -0.08 | 0.91 | -0.16 | 0.50 | 790 | NO |
| GC 1 | clock 14:00 ret15m dir=against hold=60m | 479 | 2 | 0.89 | -0.77 | 1.18 | 1.61 / 0.94 | 0.09 / -0.48 / 1.09 | 0.14 | -0.50 | 1.00 | -0.08 | 0.50 | 774 | NO |
| GC 2 | clock 15:00 ret60m dir=with hold=60m | 472 | 2 | 0.73 | -1.44 | 0.51 | 0.55 / 1.25 | 0.10 / -0.54 / 0.11 | -0.11 | -0.16 | 0.93 | -0.38 | 0.25 | 761 | NO |
| GC 3 | clock 09:30 ret15m dir=with hold=60m | 506 | 2 | 0.52 | -0.67 | -0.04 | -0.37 / 1.34 | 0.10 / -1.76 / -0.09 | -0.30 | -0.30 | 0.66 | -0.68 | 0.00 | 813 | NO |
| GC 4 | clock 08:30 ret30m dir=with hold=30m | 506 | 2 | 0.37 | -1.25 | 0.72 | 1.03 / 1.05 | 0.10 / 0.24 / -0.14 | -0.02 | 0.20 | 0.99 | -0.20 | 0.00 | 812 | NO |
| GC 5 | clock 15:00 ret60m dir=with hold=30m | 472 | 2 | 0.33 | -1.99 | 0.37 | 0.51 / 1.17 | -0.02 / -0.68 / 0.20 | -0.23 | -0.39 | 0.92 | -0.42 | 0.00 | 761 | NO |
| GC 6 | clock 03:00 ret15m dir=against hold=60m | 499 | 2 | 0.32 | -0.73 | -0.32 | -0.94 / 1.16 | 0.01 / -0.70 / -0.43 | -0.29 | 0.30 | 0.54 | -0.45 | 0.00 | 803 | NO |
| GC 7 | clock 12:00 ret60m dir=with hold=30m | 510 | 2 | 0.21 | -1.74 | -0.11 | -0.28 / 1.01 | 0.03 / -0.78 / -0.32 | -0.32 | -0.30 | 0.82 | -0.52 | 0.00 | 815 | NO |
| GC 8 | clock 09:00 ret30m dir=against hold=60m | 508 | 2 | 0.13 | -1.17 | 0.68 | 1.18 / 0.90 | 0.06 / 0.07 / 0.70 | 0.16 | -0.14 | 0.98 | -0.13 | 0.25 | 815 | NO |
| GC 9 (diag) | clock 14:00 ret60m dir=against hold=60m | 480 | 1 | 0.50 | -1.05 | 0.27 | 0.20 / 1.23 | 0.02 / -0.49 / -0.14 | -0.20 | -0.65 | 0.92 | -0.44 | 0.00 | 774 | diag |
| GC 10 (diag) | clock 09:30 ret30m dir=with hold=60m | 505 | 1 | 0.47 | -0.30 | 0.06 | -0.12 / 1.19 | 0.03 / -1.35 / -0.08 | -0.25 | -0.45 | 0.77 | -0.65 | 0.00 | 812 | diag |
| CL 1 | clock 14:00 ret60m dir=against hold=60m | 493 | 2 | 0.60 | -0.90 | 0.58 | 0.59 / 0.69 | 0.17 / -0.50 / 0.53 | -0.04 | 0.37 | 0.99 | -0.09 | 0.50 | 785 | NO |
| CL 2 (diag) | clock 11:00 ret60m dir=with hold=60m | 514 | 1 | 0.74 | -0.58 | 0.03 | -0.82 / 0.56 | 0.16 / -0.60 / -0.30 | -0.20 | -0.06 | 0.96 | -0.30 | 0.00 | 821 | diag |
| CL 3 (diag) | clock 11:00 ret30m dir=with hold=60m | 508 | 1 | 0.62 | -0.62 | 0.27 | -0.18 / 0.77 | 0.15 / -0.26 / -0.15 | -0.11 | -0.31 | 0.98 | -0.19 | 0.25 | 813 | diag |
| CL 4 (diag) | clock 11:00 ret60m dir=with hold=30m | 514 | 1 | 0.54 | -1.07 | -0.40 | -1.87 / 0.66 | 0.08 / -0.59 / -0.37 | -0.31 | -0.08 | 0.93 | -0.32 | 0.00 | 821 | diag |
| ZN 1 (diag) | clock 08:00 ret30m dir=with hold=60m | 454 | 0 | -2.16 | -3.67 | -2.45 | -3.68 / -4.45 | -0.45 / -0.59 / -0.36 | -0.84 | 0.12 | 1.00 | -0.62 | 0.00 | 709 | diag |
| ZN 2 (diag) | clock 08:30 ret15m dir=with hold=30m | 457 | 0 | -2.27 | -3.98 | -2.54 | -3.69 / -6.38 | -0.45 / -0.57 / -0.46 | -0.95 | 0.15 | 1.00 | -0.64 | 0.00 | 705 | diag |
| ZN 3 (diag) | clock 08:00 ret15m dir=against hold=60m | 408 | 0 | -2.29 | -2.45 | -2.91 | -4.64 / -4.48 | -0.48 / -0.72 / -0.49 | -0.94 | -0.07 | 1.00 | -0.70 | 0.00 | 654 | diag |
| BTC 1 | clock 08:00 ret30m dir=against hold=60m | 206 | 2 | 1.43 | 0.33 | 0.46 | -1.16 / 1.02 | 0.29 / -0.08 / -0.40 | 0.04 | -0.25 | 0.88 | -0.10 | 0.00 | 293 | NO |
| BTC 2 | clock 15:00 ret15m dir=against hold=15m | 384 | 2 | 1.29 | -2.48 | 1.01 | 0.51 / 1.02 | 0.22 / -0.14 / 0.15 | 0.05 | 0.22 | 1.00 | -0.01 | 0.00 | 588 | NO |
| BTC 3 | clock 10:00 ret15m dir=against hold=30m | 467 | 2 | 0.85 | -1.62 | 0.67 | 0.38 / 0.80 | 0.10 / 0.48 / -0.33 | 0.01 | 0.06 | 1.00 | -0.11 | 0.50 | 732 | NO |
| BTC 4 | clock 09:30 ret15m dir=with hold=60m | 362 | 2 | 0.81 | 0.28 | 0.59 | 0.27 / 1.49 | 0.17 / -0.36 / 0.12 | 0.06 | -0.33 | 0.91 | -0.09 | 0.25 | 557 | NO |
| BTC 5 | clock 10:00 ret30m dir=against hold=30m | 424 | 2 | 0.78 | -0.93 | 0.54 | 0.20 / 0.86 | 0.08 / 0.19 / -0.15 | -0.01 | -0.35 | 0.94 | -0.14 | 0.25 | 653 | NO |
| BTC 6 | clock 08:00 ret15m dir=against hold=60m | 210 | 2 | 0.75 | -0.07 | 0.34 | -0.27 / 0.99 | 0.16 / -0.37 / 0.10 | 0.03 | -0.21 | 0.87 | -0.11 | 0.25 | 287 | NO |
| BTC 7 | clock 15:30 ret15m dir=with hold=30m | 397 | 2 | 0.73 | -0.68 | -0.01 | -1.69 / 1.45 | 0.11 / -0.44 / -0.26 | -0.13 | 0.40 | 0.68 | -0.22 | 0.00 | 618 | NO |
| BTC 8 | clock 10:00 ret30m dir=against hold=60m | 423 | 2 | 0.72 | -0.53 | 0.57 | 0.49 / 1.09 | 0.06 / 0.02 / -0.02 | 0.00 | -0.35 | 0.94 | -0.14 | 0.25 | 649 | NO |
| BTC 9 | clock 10:00 ret15m dir=against hold=60m | 463 | 2 | 0.67 | -1.42 | 0.80 | 1.16 / 1.28 | 0.09 / 0.50 / -0.12 | 0.07 | -0.02 | 0.97 | -0.08 | 0.75 | 727 | NO |
| BTC 10 | clock 11:00 ret15m dir=with hold=15m | 425 | 2 | 0.66 | 0.37 | 0.40 | -0.00 / 0.82 | 0.08 / -0.29 / 0.06 | -0.04 | 0.01 | 0.99 | -0.12 | 0.25 | 671 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 59 |
| diagnostic cells read | 8 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 37 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 34 |
| worst-decile corr <= +0.30 | 57 |
| plateau >= 0.75 | 6 |
| all-in uplift at 2x slippage >= +0.10 | 11 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC clock 15:00 ret15m dir=against hold=15m | clean | 1.25 | 2.14 | -122282 | -90737 | 409381 | -247540 | 2.78 | 48.6 | 1.68 | -84633 | 228408 | -100399 |
| BTC clock 15:00 ret15m dir=against hold=15m | H1 | -0.16 | -0.21 | -136183 | -131373 | 668010 | -138875 | -0.07 | 35.7 | 2.69 | -81563 | 212090 | -94557 |
| BTC clock 15:00 ret15m dir=against hold=15m | H2 | 1.80 | 3.10 | -55451 | -44856 | 92231 | -59616 | 2.98 | 38.9 | 2.45 | -86505 | 217935 | -94448 |
| BTC clock 15:00 ret15m dir=against hold=15m | all | 1.01 | 1.58 | -129859 | -98400 | 668010 | -247540 | 2.05 | 44.0 | 2.01 | -86399 | 228408 | -100399 |
| CL clock 14:00 ret60m dir=against hold=60m | clean | 0.64 | 0.94 | -132941 | -112591 | 577633 | -176507 | 1.01 | 44.8 | 1.63 | -87026 | 254856 | -110018 |
| CL clock 14:00 ret60m dir=against hold=60m | H1 | -2.07 | -2.33 | -117566 | -110466 | 480351 | -118061 | -0.87 | 57.1 | 2.32 | -82159 | 166295 | -85995 |
| CL clock 14:00 ret60m dir=against hold=60m | H2 | 1.33 | 2.94 | -223840 | -189912 | 402493 | -242878 | 2.74 | 47.2 | 2.82 | -97794 | 232550 | -123485 |
| CL clock 14:00 ret60m dir=against hold=60m | all | 0.58 | 1.05 | -163045 | -133459 | 1301024 | -242878 | 0.98 | 47.0 | 2.03 | -89996 | 254856 | -123485 |
| ES clock 09:30 ret30m dir=against hold=30m | clean | 1.38 | 2.36 | -124144 | -94595 | 447425 | -172785 | 2.79 | 41.0 | 1.65 | -88886 | 254188 | -110103 |
| ES clock 09:30 ret30m dir=against hold=30m | H1 | -0.33 | -0.46 | -131599 | -126781 | 574148 | -135691 | -0.15 | 53.6 | 2.60 | -94602 | 209916 | -104071 |
| ES clock 09:30 ret30m dir=against hold=30m | H2 | -0.38 | -0.50 | -171967 | -148374 | 437264 | -190787 | -0.35 | 47.2 | 2.13 | -93618 | 232644 | -102103 |
| ES clock 09:30 ret30m dir=against hold=30m | all | 0.64 | 0.96 | -147874 | -125155 | 676027 | -190787 | 1.49 | 44.6 | 1.90 | -91937 | 254188 | -110103 |
| GC clock 14:00 ret15m dir=against hold=60m | clean | 0.84 | 1.45 | -122201 | -89315 | 570584 | -181988 | 1.34 | 48.6 | 1.55 | -85994 | 307097 | -111203 |
| GC clock 14:00 ret15m dir=against hold=60m | H1 | -0.20 | -0.28 | -261911 | -254891 | 830566 | -279441 | -0.13 | 42.9 | 2.35 | -91326 | 175392 | -91746 |
| GC clock 14:00 ret15m dir=against hold=60m | H2 | 2.74 | 6.08 | -299122 | -193613 | 970461 | -479827 | 2.70 | 25.0 | 3.38 | -93344 | 209953 | -101099 |
| GC clock 14:00 ret15m dir=against hold=60m | all | 1.18 | 2.17 | -232065 | -169409 | 1543245 | -479827 | 2.12 | 42.3 | 2.11 | -89753 | 307097 | -111203 |
| NQ clock 15:00 ret15m dir=against hold=60m | clean | 1.01 | 1.58 | -129159 | -95693 | 335021 | -257235 | 2.73 | 49.5 | 1.64 | -83097 | 236742 | -85181 |
| NQ clock 15:00 ret15m dir=against hold=60m | H1 | 3.42 | 7.98 | -60420 | -58261 | 115642 | -61046 | 6.10 | 28.6 | 3.49 | -67506 | 146562 | -77020 |
| NQ clock 15:00 ret15m dir=against hold=60m | H2 | 0.72 | 1.27 | -139247 | -118951 | 308797 | -173048 | 1.04 | 50.0 | 2.35 | -105354 | 222583 | -117134 |
| NQ clock 15:00 ret15m dir=against hold=60m | all | 1.23 | 2.06 | -132921 | -104359 | 335021 | -257235 | 5.79 | 46.4 | 2.08 | -87769 | 236742 | -117134 |
| RTY clock 08:30 ret15m dir=with hold=5m | clean | 0.61 | 0.92 | -141400 | -110832 | 267808 | -224276 | 2.07 | 45.7 | 1.55 | -89370 | 297482 | -101183 |
| RTY clock 08:30 ret15m dir=with hold=5m | H1 | 0.04 | 0.06 | -89965 | -81849 | 242686 | -91485 | 0.03 | 60.7 | 2.91 | -83741 | 155854 | -96584 |
| RTY clock 08:30 ret15m dir=with hold=5m | H2 | 0.55 | 1.04 | -72378 | -61514 | 190874 | -91485 | 0.74 | 52.8 | 2.30 | -85315 | 230277 | -86199 |
| RTY clock 08:30 ret15m dir=with hold=5m | all | 0.52 | 0.81 | -124424 | -98093 | 267808 | -224276 | 2.62 | 49.4 | 1.92 | -89648 | 297482 | -101183 |
| YM clock 09:30 ret30m dir=against hold=30m | clean | 1.80 | 3.23 | -108271 | -92175 | 383291 | -140943 | 4.26 | 42.9 | 1.70 | -89916 | 289295 | -103635 |
| YM clock 09:30 ret30m dir=against hold=30m | H1 | 1.75 | 3.29 | -95084 | -84669 | 258634 | -105415 | 1.68 | 42.9 | 3.12 | -91235 | 139996 | -99370 |
| YM clock 09:30 ret30m dir=against hold=30m | H2 | 2.23 | 4.14 | -119273 | -106864 | 263720 | -124061 | 3.23 | 36.1 | 2.81 | -79718 | 220435 | -81264 |
| YM clock 09:30 ret30m dir=against hold=30m | all | 1.90 | 3.46 | -112834 | -95973 | 383291 | -140943 | 7.62 | 41.7 | 2.15 | -89248 | 289295 | -103635 |
| ZN clock 08:00 ret30m dir=with hold=60m (diag) | clean | -2.14 | -2.51 | -143448 | -127092 | 2187367 | -187434 | -0.89 | 67.6 | 1.01 | -94650 | 324501 | -114745 |
| ZN clock 08:00 ret30m dir=with hold=60m (diag) | H1 | -4.31 | -3.89 | -103047 | -90398 | 578208 | -127061 | -0.95 | 78.6 | 2.24 | -81448 | 171763 | -84141 |
| ZN clock 08:00 ret30m dir=with hold=60m (diag) | H2 | -3.19 | -3.29 | -87906 | -79467 | 643112 | -94126 | -0.87 | 69.4 | 1.94 | -88959 | 220376 | -91281 |
| ZN clock 08:00 ret30m dir=with hold=60m (diag) | all | -2.45 | -2.77 | -135928 | -115755 | 3316439 | -187434 | -0.92 | 69.6 | 1.41 | -92339 | 324501 | -114745 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES clock 09:30 ret30m dir=against hold=30m | -18.7 | -20.8 | 2.0 | 19.2 | -21.7 / 5.8 | -20.8 / -2.8 | NO |
| NQ clock 15:00 ret15m dir=against hold=60m | -8.3 | -32.9 | 10.3 | 29.3 | 15.2 / 19.4 | 32.4 / 49.5 | NO |
| RTY clock 08:30 ret15m dir=with hold=5m | -22.1 | -9.2 | 6.8 | 20.7 | -10.1 / 3.9 | -5.1 / 18.2 | NO |
| YM clock 09:30 ret30m dir=against hold=30m | 2.6 | -13.7 | 8.4 | 19.2 | -14.6 / 6.5 | -10.4 / 3.7 | NO |
| GC clock 14:00 ret15m dir=against hold=60m | 6.6 | -65.6 | -14.5 | -17.9 | -25.7 / 14.5 | -32.0 / -25.6 | NO |
| CL clock 14:00 ret60m dir=against hold=60m | -15.8 | -44.5 | 9.2 | 16.5 | -23.5 / 14.1 | 13.8 / 21.2 | NO |
| ZN clock 08:00 ret30m dir=with hold=60m (diag) | -64.1 | -33.7 | 4.4 | 4.4 | -34.7 / -1.4 | 18.8 / 22.6 | NO |
| BTC clock 15:00 ret15m dir=against hold=15m | -14.7 | -5.1 | 11.5 | 29.8 | -5.9 / 13.8 | -1.2 / 4.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 clock 09:30 ret30m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2546 | 6.4 | -22.9 | -8.8 | 29.4 | 0.23 / -0.80 / -0.30 | 85.6 / 56.3 |
| ES 2 clock 09:30 ret30m dir=against hold=60m | negative pre-2023 | 2546 | -1.7 | -31.0 | -16.9 | 29.4 | -0.04 / -0.78 / -0.42 | 76.1 / 46.8 |
| ES 3 clock 08:00 ret60m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2575 | 16.0 | -13.3 | 0.8 | 29.4 | 0.56 / -0.46 / 0.03 | 59.4 / 30.0 |
| ES 4 clock 10:00 ret15m dir=with hold=60m | negative pre-2023 | 2590 | -8.2 | -37.6 | -23.4 | 29.4 | -0.24 / -1.10 / -0.69 | 64.9 / 35.6 |
| ES 5 clock 13:30 ret30m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2499 | 1.8 | -27.6 | -13.4 | 29.4 | 0.06 / -0.99 / -0.48 | 45.3 / 15.9 |
| ES 6 clock 11:00 ret15m dir=against hold=30m | negative pre-2023 | 2591 | -4.8 | -34.2 | -20.0 | 29.4 | -0.21 / -1.50 / -0.87 | 39.6 / 10.2 |
| ES 7 clock 12:00 ret60m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2570 | 4.2 | -25.2 | -11.0 | 29.4 | 0.15 / -0.96 / -0.42 | 49.4 / 20.0 |
| ES 8 clock 13:30 ret15m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2450 | 10.2 | -19.1 | -5.0 | 29.4 | 0.37 / -0.69 / -0.18 | 47.3 / 17.9 |
| ES 9 clock 14:00 ret60m dir=with hold=30m | negative pre-2023 | 2550 | -1.7 | -31.0 | -16.8 | 29.4 | -0.08 / -1.54 / -0.84 | 37.8 / 8.5 |
| ES 10 clock 15:30 ret30m dir=against hold=60m | negative pre-2023 | 2517 | -6.5 | -35.9 | -21.7 | 29.4 | -0.21 / -1.11 / -0.67 | 43.4 / 14.0 |
| NQ 1 clock 10:00 ret15m dir=with hold=15m | positive pre-2023 | 2662 | 17.4 | 3.0 | 11.5 | 14.4 | 0.58 / 0.11 / 0.39 | 144.5 / 130.2 |
| NQ 2 clock 10:00 ret15m dir=with hold=5m | positive pre-2023 | 2662 | 15.7 | 1.4 | 9.9 | 14.4 | 0.77 / 0.07 / 0.49 | 70.1 / 55.8 |
| NQ 3 clock 09:30 ret30m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2630 | 12.3 | -2.1 | 6.4 | 14.4 | 0.26 / -0.04 / 0.14 | 124.2 / 109.8 |
| NQ 4 clock 10:00 ret15m dir=with hold=60m | positive pre-2023 | 2662 | 16.9 | 2.5 | 11.1 | 14.4 | 0.34 / 0.05 / 0.22 | 125.1 / 110.7 |
| NQ 5 clock 14:00 ret30m dir=with hold=5m | negative pre-2023 | 2572 | -5.0 | -19.3 | -10.8 | 14.4 | -0.30 / -1.16 / -0.65 | 40.6 / 26.2 |
| NQ 6 clock 10:00 ret60m dir=with hold=15m | gross-positive, cost-negative pre-2023 | 2675 | 7.1 | -7.3 | 1.3 | 14.4 | 0.26 / -0.25 / 0.05 | 96.5 / 82.1 |
| NQ 7 clock 15:30 ret30m dir=against hold=60m | negative pre-2023 | 2587 | -16.7 | -31.0 | -22.5 | 14.4 | -0.37 / -0.68 / -0.49 | 95.7 / 81.3 |
| NQ 8 clock 15:00 ret15m dir=against hold=60m | negative pre-2023 | 2566 | -41.9 | -56.3 | -47.7 | 14.4 | -0.79 / -1.06 / -0.90 | 103.0 / 88.7 |
| NQ 9 clock 15:30 ret30m dir=against hold=30m | negative pre-2023 | 2587 | -25.3 | -39.7 | -31.1 | 14.4 | -0.65 / -1.01 / -0.80 | 79.5 / 65.2 |
| NQ 10 clock 14:00 ret60m dir=with hold=30m | negative pre-2023 | 2581 | -1.2 | -15.6 | -7.0 | 14.4 | -0.04 / -0.52 / -0.23 | 64.4 / 50.0 |
| RTY 1 clock 09:00 ret60m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 1492 | 6.7 | -7.6 | -5.4 | 14.4 | 0.71 / -0.82 / -0.59 | 24.8 / 10.4 |
| RTY 2 clock 09:30 ret30m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 1507 | 13.2 | -1.2 | 1.0 | 14.4 | 0.55 / -0.07 / 0.03 | 33.7 / 19.4 |
| RTY 3 clock 08:00 ret60m dir=against hold=60m | positive pre-2023 | 1475 | 18.0 | 3.6 | 5.8 | 14.4 | 0.79 / 0.15 / 0.25 | 37.7 / 23.3 |
| RTY 4 clock 09:30 ret30m dir=against hold=5m | gross-positive, cost-negative pre-2023 | 1507 | 3.3 | -11.0 | -8.8 | 14.4 | 0.17 / -0.65 / -0.52 | 25.5 / 11.2 |
| RTY 5 clock 08:00 ret30m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 1447 | 10.6 | -3.8 | -1.6 | 14.4 | 0.45 / -0.17 / -0.07 | 34.1 / 19.7 |
| RTY 6 clock 08:30 ret15m dir=with hold=5m | negative pre-2023 | 1458 | -6.1 | -20.5 | -18.3 | 14.4 | -0.47 / -1.56 / -1.40 | 29.1 / 14.8 |
| RTY 7 clock 08:30 ret60m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 1457 | 9.1 | -5.3 | -3.1 | 14.4 | 0.39 / -0.22 / -0.13 | 29.6 / 15.2 |
| RTY 8 clock 10:00 ret60m dir=against hold=60m | negative pre-2023 | 1525 | -21.4 | -35.8 | -33.5 | 14.4 | -0.69 / -1.16 / -1.08 | 29.1 / 14.7 |
| RTY 9 clock 08:30 ret15m dir=with hold=30m | negative pre-2023 | 1458 | -6.8 | -21.1 | -18.9 | 14.4 | -0.37 / -1.15 / -1.03 | 26.5 / 12.2 |
| RTY 10 clock 09:30 ret15m dir=against hold=5m | negative pre-2023 | 1481 | -6.8 | -21.2 | -19.0 | 14.4 | -0.45 / -1.34 / -1.20 | 19.5 / 5.1 |
| YM 1 clock 09:30 ret15m dir=against hold=30m | negative pre-2023 | 2595 | -6.7 | -21.0 | -15.3 | 14.4 | -0.26 / -0.81 / -0.59 | 89.7 / 75.4 |
| YM 2 clock 09:30 ret15m dir=against hold=60m | negative pre-2023 | 2595 | -16.1 | -30.5 | -24.8 | 14.4 | -0.53 / -1.00 / -0.81 | 113.1 / 98.8 |
| YM 3 clock 09:30 ret15m dir=against hold=5m | gross-positive, cost-negative pre-2023 | 2595 | 5.2 | -9.1 | -3.4 | 14.4 | 0.40 / -0.70 / -0.26 | 53.8 / 39.4 |
| YM 4 clock 09:30 ret15m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 2595 | 0.5 | -13.8 | -8.1 | 14.4 | 0.02 / -0.66 / -0.39 | 61.5 / 47.1 |
| YM 5 clock 09:30 ret30m dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2623 | 7.9 | -6.4 | -0.7 | 14.4 | 0.33 / -0.26 / -0.03 | 77.8 / 63.4 |
| YM 6 clock 09:30 ret30m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2622 | 0.6 | -13.7 | -8.0 | 14.4 | 0.02 / -0.45 / -0.26 | 88.7 / 74.3 |
| YM 7 clock 09:00 ret30m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2625 | 4.6 | -9.8 | -4.1 | 14.4 | 0.17 / -0.35 / -0.15 | 69.1 / 54.8 |
| YM 8 clock 09:30 ret30m dir=against hold=15m | gross-positive, cost-negative pre-2023 | 2623 | 6.1 | -8.2 | -2.5 | 14.4 | 0.31 / -0.43 / -0.13 | 53.4 / 39.1 |
| YM 9 clock 09:30 ret30m dir=against hold=5m | gross-positive, cost-negative pre-2023 | 2623 | 3.3 | -11.0 | -5.3 | 14.4 | 0.26 / -0.87 / -0.42 | 45.6 / 31.2 |
| YM 10 clock 13:30 ret15m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2540 | 11.7 | -2.7 | 3.0 | 14.4 | 0.59 / -0.13 / 0.15 | 46.7 / 32.3 |
| GC 1 clock 14:00 ret15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2411 | 6.8 | -17.6 | -7.9 | 24.4 | 0.28 / -0.77 / -0.35 | 51.5 / 27.2 |
| GC 2 clock 15:00 ret60m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2487 | 0.4 | -24.0 | -14.2 | 24.4 | 0.02 / -1.44 / -0.85 | 43.1 / 18.7 |
| GC 3 clock 09:30 ret15m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2559 | 1.1 | -23.2 | -13.5 | 24.4 | 0.03 / -0.67 / -0.39 | 61.4 / 37.1 |
| GC 4 clock 08:30 ret30m dir=with hold=30m | negative pre-2023 | 2607 | -8.6 | -33.0 | -23.2 | 24.4 | -0.33 / -1.25 / -0.88 | 41.6 / 17.2 |
| GC 5 clock 15:00 ret60m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2487 | 2.2 | -22.2 | -12.4 | 24.4 | 0.20 / -1.99 / -1.11 | 29.2 / 4.8 |
| GC 6 clock 03:00 ret15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2519 | 9.4 | -14.9 | -5.2 | 24.4 | 0.46 / -0.73 / -0.25 | 38.0 / 13.6 |
| GC 7 clock 12:00 ret60m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2592 | 0.6 | -23.7 | -14.0 | 24.4 | 0.04 / -1.74 / -1.03 | 28.7 / 4.3 |
| GC 8 clock 09:00 ret30m dir=against hold=60m | negative pre-2023 | 2608 | -13.4 | -37.8 | -28.0 | 24.4 | -0.41 / -1.17 / -0.87 | 27.6 / 3.2 |
| GC 9 (diag) clock 14:00 ret60m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2509 | 2.3 | -22.1 | -12.3 | 24.4 | 0.11 / -1.05 / -0.59 | 39.8 / 15.4 |
| GC 10 (diag) clock 09:30 ret30m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2603 | 13.6 | -10.8 | -1.0 | 24.4 | 0.38 / -0.30 / -0.03 | 52.0 / 27.6 |
| CL 1 clock 14:00 ret60m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2560 | 2.1 | -22.3 | -19.7 | 24.4 | 0.09 / -0.90 / -0.79 | 36.3 / 12.0 |
| CL 2 (diag) clock 11:00 ret60m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2649 | 7.0 | -17.3 | -14.7 | 24.4 | 0.24 / -0.58 / -0.49 | 45.5 / 21.1 |
| CL 3 (diag) clock 11:00 ret30m dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2649 | 5.3 | -19.0 | -16.4 | 24.4 | 0.18 / -0.62 / -0.54 | 43.2 / 18.8 |
| CL 4 (diag) clock 11:00 ret60m dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2649 | 1.9 | -22.4 | -19.8 | 24.4 | 0.10 / -1.07 / -0.94 | 36.7 / 12.4 |
| ZN 1 (diag) clock 08:00 ret30m dir=with hold=60m | negative pre-2023 | 2268 | -8.2 | -43.9 | -48.9 | 35.6 | -0.69 / -3.67 / -4.10 | 3.4 / -32.2 |
| ZN 2 (diag) clock 08:30 ret15m dir=with hold=30m | negative pre-2023 | 2340 | -6.9 | -42.5 | -47.6 | 35.6 | -0.65 / -3.98 / -4.46 | 7.8 / -27.8 |
| ZN 3 (diag) clock 08:00 ret15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2154 | 4.4 | -31.2 | -36.3 | 35.6 | 0.34 / -2.45 / -2.85 | 1.7 / -33.9 |
| BTC 1 clock 08:00 ret30m dir=against hold=60m | positive pre-2023 | 121 | 95.5 | 41.1 | 74.1 | 54.4 | 0.76 / 0.33 / 0.59 | 326.1 / 271.7 |
| BTC 2 clock 15:00 ret15m dir=against hold=15m | negative pre-2023 | 252 | -90.0 | -144.3 | -112.0 | 54.4 | -1.57 / -2.48 / -1.94 | 166.9 / 112.6 |
| BTC 3 clock 10:00 ret15m dir=against hold=30m | negative pre-2023 | 339 | -50.0 | -104.4 | -71.9 | 54.4 | -0.78 / -1.62 / -1.11 | 224.1 / 169.7 |
| BTC 4 clock 09:30 ret15m dir=with hold=60m | positive pre-2023 | 275 | 95.0 | 40.6 | 72.9 | 54.4 | 0.68 / 0.28 / 0.52 | 284.8 / 230.4 |
| BTC 5 clock 10:00 ret30m dir=against hold=30m | negative pre-2023 | 316 | -11.1 | -65.4 | -32.8 | 54.4 | -0.15 / -0.93 / -0.46 | 192.0 / 137.7 |
| BTC 6 clock 08:00 ret15m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 111 | 43.5 | -10.9 | 21.6 | 54.4 | 0.28 / -0.07 / 0.14 | 190.5 / 136.1 |
| BTC 7 clock 15:30 ret15m dir=with hold=30m | negative pre-2023 | 247 | -1.1 | -55.5 | -23.2 | 54.4 | 0.01 / -0.68 / -0.27 | 159.8 / 105.5 |
| BTC 8 clock 10:00 ret30m dir=against hold=60m | gross-positive, cost-negative pre-2023 | 314 | 1.4 | -53.0 | -20.3 | 54.4 | 0.03 / -0.53 / -0.20 | 213.2 / 158.8 |
| BTC 9 clock 10:00 ret15m dir=against hold=60m | negative pre-2023 | 333 | -81.8 | -136.2 | -103.8 | 54.4 | -0.85 / -1.42 / -1.08 | 228.9 / 174.5 |
| BTC 10 clock 11:00 ret15m dir=with hold=15m | positive pre-2023 | 306 | 72.4 | 18.0 | 50.5 | 54.4 | 1.44 / 0.37 / 1.02 | 137.9 / 83.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 23 cells pass the clean rule against a replicate mean of 25.2 (p(count) = 0.68, p(top) = 0.79); CL: 1 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.73, p(top) = 0.21); ES: 11 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.00, p(top) = 0.31); GC: 8 cells pass the clean rule against a replicate mean of 4.7 (p(count) = 0.10, p(top) = 0.73); NQ: 38 cells pass the clean rule against a replicate mean of 29.1 (p(count) = 0.06, p(top) = 0.14); RTY: 17 cells pass the clean rule against a replicate mean of 5.4 (p(count) = 0.00, p(top) = 0.32); YM: 27 cells pass the clean rule against a replicate mean of 6.6 (p(count) = 0.00, p(top) = 0.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 59 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.29 (YM clock 09:30 ret30m dir=against hold=30m); bootstrap lower bound > 0 for 7 cells; plateau >= 0.75 for 6; 2x-slippage all-in uplift >= +0.10 for 11; gate_add PASS at some share: 1 (cell-share pairs).
- Gate-3 cell YM clock 09:30 ret30m dir=against hold=30m: uplift +0.24/+0.29/+0.51, boot lo +0.11, plateau 0.50, 2x-slip +0.24, wd corr -0.17, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 29, 'negative pre-2023': 23, 'positive pre-2023': 7}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_5.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/sw5/ (`SW5_CO_all_selected_scored.csv`).

DONE SW5
