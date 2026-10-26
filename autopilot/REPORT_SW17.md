# REPORT SW17 - intraday reference-state x clock anchor (D06/D02 H2/H3)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 52 selected cells (+12 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.24; best pair-window standalone Sharpe +1.53.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: at anchor 10:30/11:30/12:30/13:30/14:30/15:00 ET enter with/against the sign of close minus RTH VWAP / Globex VWAP / RTH open / 18:00 open; hold to the flatten or 60 min.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 96 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      96 |         96 |        14 |               1.682 |                2 |         10 |            0 |
| CL    |      96 |         96 |         3 |               0.67  |                2 |          3 |            3 |
| ES    |      96 |         96 |        10 |               1.596 |                2 |         10 |            0 |
| GC    |      96 |         96 |         6 |               0.743 |                2 |          6 |            3 |
| NQ    |      96 |         96 |        23 |               2.138 |                2 |         10 |            0 |
| RTY   |      96 |         96 |         3 |               0.503 |                2 |          3 |            3 |
| YM    |      96 |         96 |        11 |               0.709 |                2 |         10 |            0 |
| ZN    |      96 |         96 |         0 |              -1.887 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   10 |            10.09 |              20 |       0.53 |                       0.568 |            0.755 |           0.953 |     0.92 |       1.596 |                1.892 |
| NQ    |     100 |                   23 |            18.5  |              26 |       0.12 |                       1.013 |            0.997 |           1.208 |     0.47 |       2.138 |                2.111 |
| RTY   |     100 |                    3 |            11.35 |              18 |       1    |                       0.426 |            0.786 |           1.079 |     0.98 |       0.483 |                2.106 |
| YM    |     100 |                   11 |            12.93 |              21 |       0.74 |                       0.417 |            0.853 |           1.095 |     0.99 |       0.709 |                2.009 |
| GC    |     100 |                    6 |            11.35 |              20 |       0.99 |                       0.467 |            0.782 |           1.081 |     0.95 |       0.696 |                2.042 |
| CL    |     100 |                    3 |             8.36 |              18 |       1    |                       0.396 |            0.707 |           0.981 |     0.97 |       0.67  |                1.981 |
| ZN    |     100 |                    0 |             0.51 |               4 |       1    |                     nan     |            0.475 |           0.947 |   nan    |     nan     |                1.052 |
| BTC   |     100 |                   14 |            16.59 |              25 |       0.79 |                       1.049 |            0.968 |           1.262 |     0.33 |       1.682 |                2.153 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | anchor 10:30 ref=rd dir=with hold=flat | 510 | 2 | 1.60 | -0.46 | 0.58 | -0.67 / 1.16 | 0.29 / -0.29 / -0.34 | 0.00 | 0.33 | 0.90 | -0.15 | 0.50 | 819 | NO |
| ES 2 | anchor 14:30 ref=gd dir=with hold=60m | 496 | 2 | 1.12 | -0.63 | 0.54 | -0.19 / 0.50 | 0.18 / -0.37 / 0.07 | -0.06 | -0.45 | 1.00 | -0.11 | 0.50 | 796 | NO |
| ES 3 | anchor 10:30 ref=gd dir=against hold=60m | 514 | 2 | 0.78 | -0.43 | 0.38 | -0.15 / 0.87 | 0.16 / -0.43 / 0.03 | -0.05 | 0.11 | 0.99 | -0.16 | 0.50 | 823 | NO |
| ES 4 | anchor 14:30 ref=rd dir=with hold=60m | 497 | 2 | 0.48 | -0.57 | 0.54 | 0.76 / 0.58 | 0.03 / -0.34 / 0.41 | -0.06 | -0.66 | 0.99 | -0.13 | 0.00 | 797 | NO |
| ES 5 | anchor 11:30 ref=rd dir=with hold=flat | 512 | 2 | 0.42 | 0.01 | 0.37 | 0.21 / 1.51 | 0.01 / -0.03 / -0.08 | -0.05 | 0.17 | 0.81 | -0.14 | 0.00 | 821 | NO |
| ES 6 | anchor 11:30 ref=gd dir=with hold=flat | 514 | 2 | 0.40 | -0.30 | 0.34 | 0.16 / 1.26 | 0.08 / -0.25 / 0.02 | -0.03 | -0.04 | 0.84 | -0.16 | 0.50 | 824 | NO |
| ES 7 | anchor 10:30 ref=gv dir=with hold=flat | 516 | 2 | 0.32 | -0.35 | 0.20 | -0.10 / 1.21 | 0.04 / -0.05 / -0.26 | -0.10 | 0.44 | 0.73 | -0.24 | 0.00 | 826 | NO |
| ES 8 | anchor 14:30 ref=gd dir=with hold=flat | 496 | 2 | 0.30 | -0.13 | -0.02 | -0.65 / 1.24 | 0.01 / -0.50 / -0.07 | -0.16 | -0.28 | 0.66 | -0.26 | 0.00 | 796 | NO |
| ES 9 | anchor 11:30 ref=rv dir=with hold=flat | 516 | 2 | 0.18 | 0.01 | -0.32 | -1.24 / 1.68 | -0.03 / -0.22 / -0.39 | -0.19 | 0.31 | 0.35 | -0.30 | 0.00 | 826 | NO |
| ES 10 | anchor 11:30 ref=gd dir=with hold=60m | 514 | 2 | 0.09 | -1.03 | -0.44 | -1.08 / 0.61 | -0.02 / -0.75 / -0.32 | -0.31 | 0.03 | 0.74 | -0.40 | 0.00 | 824 | NO |
| NQ 1 | anchor 10:30 ref=rd dir=with hold=flat | 516 | 2 | 2.14 | 0.32 | 0.91 | -0.46 / 1.23 | 0.43 / -0.22 / -0.30 | 0.16 | -0.10 | 0.97 | -0.05 | 0.50 | 826 | NO |
| NQ 2 | anchor 14:30 ref=gd dir=with hold=60m | 496 | 2 | 1.36 | 0.45 | 1.22 | 1.08 / 1.34 | 0.27 / -0.18 / 0.41 | 0.22 | -0.46 | 0.99 | 0.06 | 0.50 | 796 | NO |
| NQ 3 | anchor 14:30 ref=rd dir=with hold=60m | 496 | 2 | 1.13 | 0.52 | 1.08 | 1.09 / 1.22 | 0.17 / 0.01 / 0.45 | 0.18 | -0.56 | 1.00 | 0.01 | 1.00 | 795 | NO |
| NQ 4 | anchor 10:30 ref=rd dir=with hold=60m | 516 | 2 | 0.97 | -0.28 | 0.19 | -0.65 / 1.27 | 0.19 / -0.15 / -0.38 | -0.01 | -0.16 | 0.73 | -0.22 | 1.00 | 826 | NO |
| NQ 5 | anchor 10:30 ref=gd dir=with hold=flat | 515 | 2 | 0.89 | 0.19 | 0.70 | 0.40 / 1.47 | 0.17 / -0.04 / -0.10 | 0.06 | 0.18 | 0.91 | -0.13 | 1.00 | 825 | NO |
| NQ 6 | anchor 14:30 ref=rd dir=with hold=flat | 496 | 2 | 0.79 | 0.42 | 0.39 | -0.24 / 1.44 | 0.11 / -0.35 / -0.03 | -0.00 | -0.18 | 0.84 | -0.17 | 0.00 | 795 | NO |
| NQ 7 | anchor 15:00 ref=rd dir=with hold=flat | 496 | 2 | 0.75 | 0.71 | -0.14 | -1.16 / 1.70 | 0.09 / -0.26 / -0.55 | -0.12 | -0.01 | 0.39 | -0.30 | 0.00 | 796 | NO |
| NQ 8 | anchor 11:30 ref=gd dir=with hold=flat | 516 | 2 | 0.72 | 0.25 | 1.00 | 1.28 / 1.28 | 0.14 / -0.09 / 0.13 | 0.11 | 0.27 | 0.96 | -0.06 | 1.00 | 826 | NO |
| NQ 9 | anchor 11:30 ref=rd dir=with hold=60m | 516 | 2 | 0.69 | -0.10 | 0.30 | -0.25 / 1.23 | 0.03 / 0.13 / -0.46 | -0.09 | 0.53 | 0.77 | -0.25 | 0.00 | 825 | NO |
| NQ 10 | anchor 11:30 ref=gd dir=with hold=60m | 516 | 2 | 0.68 | -0.47 | 0.25 | -0.13 / 1.35 | 0.05 / -0.42 / -0.32 | -0.11 | -0.14 | 0.81 | -0.32 | 0.00 | 826 | NO |
| RTY 1 | anchor 10:30 ref=gd dir=against hold=60m | 516 | 2 | 0.48 | -0.45 | 0.39 | 0.15 / 0.89 | 0.03 / -0.39 / 0.22 | -0.07 | 0.14 | 0.99 | -0.19 | 0.00 | 826 | NO |
| RTY 2 | anchor 11:30 ref=gv dir=with hold=flat | 516 | 2 | 0.46 | -0.13 | 0.47 | 0.62 / 1.41 | 0.04 / 0.37 / -0.08 | 0.01 | 0.60 | 0.88 | -0.12 | 0.00 | 826 | NO |
| RTY 3 | anchor 10:30 ref=rd dir=with hold=60m | 515 | 2 | 0.34 | -0.25 | 0.05 | -0.32 / 1.00 | 0.11 / 0.17 / -0.51 | -0.09 | -0.30 | 0.91 | -0.24 | 0.00 | 824 | NO |
| RTY 4 (diag) | anchor 14:30 ref=rd dir=with hold=60m | 496 | 1 | 0.50 | 0.04 | 0.16 | -0.02 / 0.94 | 0.00 / -0.06 / 0.09 | -0.09 | -0.65 | 0.95 | -0.20 | 0.00 | 796 | diag |
| RTY 5 (diag) | anchor 11:30 ref=rd dir=with hold=60m | 515 | 1 | 0.45 | -0.76 | 0.31 | 0.17 / 0.54 | 0.01 / 0.51 / -0.18 | -0.06 | 0.40 | 0.98 | -0.18 | 0.50 | 823 | diag |
| RTY 6 (diag) | anchor 10:30 ref=gd dir=against hold=flat | 516 | 1 | 0.22 | -0.27 | 0.39 | 0.50 / 1.44 | -0.02 / -0.27 / 0.20 | -0.04 | -0.31 | 0.80 | -0.16 | 0.00 | 826 | diag |
| YM 1 | anchor 13:30 ref=gv dir=with hold=flat | 497 | 2 | 0.71 | 0.13 | 0.09 | -1.03 / 1.46 | 0.07 / -0.29 / -0.24 | -0.10 | 0.35 | 0.55 | -0.24 | 0.00 | 797 | NO |
| YM 2 | anchor 11:30 ref=gd dir=with hold=flat | 516 | 2 | 0.61 | -0.45 | 0.51 | 0.24 / 1.30 | 0.12 / 0.19 / -0.10 | 0.04 | 0.66 | 0.84 | -0.09 | 0.50 | 826 | NO |
| YM 3 | anchor 11:30 ref=gv dir=with hold=flat | 516 | 2 | 0.60 | -0.68 | 0.46 | 0.14 / 1.19 | 0.06 / 0.23 / -0.17 | -0.01 | 0.77 | 0.85 | -0.14 | 1.00 | 826 | NO |
| YM 4 | anchor 11:30 ref=rd dir=with hold=flat | 515 | 2 | 0.47 | -0.26 | 0.25 | -0.30 / 1.19 | 0.03 / 0.03 / -0.15 | -0.04 | 0.66 | 0.74 | -0.15 | 0.00 | 825 | NO |
| YM 5 | anchor 11:30 ref=gd dir=with hold=60m | 516 | 2 | 0.45 | -0.88 | -0.28 | -1.14 / 0.80 | 0.03 / -0.38 / -0.42 | -0.20 | -0.03 | 0.70 | -0.33 | 0.00 | 826 | NO |
| YM 6 | anchor 15:00 ref=gd dir=with hold=flat | 497 | 2 | 0.43 | -0.25 | 0.21 | -0.24 / 1.65 | 0.02 / -0.37 / 0.02 | -0.08 | -0.17 | 0.65 | -0.18 | 0.00 | 796 | NO |
| YM 7 | anchor 14:30 ref=gd dir=with hold=flat | 497 | 2 | 0.31 | -0.12 | 0.01 | -0.51 / 1.32 | -0.02 / -0.61 / 0.12 | -0.12 | -0.01 | 0.55 | -0.24 | 0.00 | 796 | NO |
| YM 8 | anchor 15:00 ref=rd dir=with hold=flat | 497 | 2 | 0.25 | -0.38 | 0.26 | 0.32 / 1.22 | -0.02 / -0.26 / 0.14 | -0.07 | 0.07 | 0.82 | -0.17 | 0.00 | 797 | NO |
| YM 9 | anchor 10:30 ref=gv dir=against hold=60m | 516 | 2 | 0.21 | -0.33 | 0.35 | 0.65 / 0.77 | 0.01 / -0.29 / 0.28 | -0.02 | -0.23 | 0.96 | -0.17 | 0.00 | 826 | NO |
| YM 10 | anchor 10:30 ref=rd dir=with hold=flat | 509 | 2 | 0.14 | -0.40 | -0.11 | -0.36 / 1.55 | -0.02 / 0.09 / -0.08 | -0.07 | -0.21 | 0.47 | -0.22 | 0.00 | 817 | NO |
| GC 1 | anchor 10:30 ref=gd dir=with hold=flat | 515 | 2 | 0.70 | -0.62 | 0.71 | 0.85 / 1.39 | 0.08 / 1.14 / -0.29 | 0.11 | 0.42 | 0.89 | -0.17 | 0.00 | 823 | NO |
| GC 2 | anchor 11:30 ref=rd dir=with hold=flat | 510 | 2 | 0.61 | -0.37 | 0.28 | 0.18 / 1.43 | 0.07 / 0.39 / -0.76 | -0.10 | 0.58 | 0.80 | -0.41 | 0.00 | 814 | NO |
| GC 3 | anchor 14:30 ref=gd dir=with hold=flat | 491 | 2 | 0.53 | -0.46 | 0.50 | 0.63 / 1.27 | 0.05 / 0.12 / 0.24 | 0.01 | -0.23 | 0.87 | -0.25 | 0.50 | 786 | NO |
| GC 4 | anchor 13:30 ref=rv dir=against hold=60m | 498 | 2 | 0.36 | -1.05 | 0.78 | 1.20 / 1.49 | 0.07 / 1.20 / -0.37 | 0.04 | -0.51 | 0.95 | -0.14 | 0.50 | 796 | NO |
| GC 5 | anchor 12:30 ref=rd dir=with hold=flat | 508 | 2 | 0.34 | -0.97 | 0.26 | 0.25 / 1.55 | 0.01 / -0.07 / -0.00 | -0.08 | 0.51 | 0.69 | -0.37 | 0.00 | 812 | NO |
| GC 6 | anchor 13:30 ref=rd dir=with hold=flat | 507 | 2 | 0.26 | -1.05 | 0.04 | -0.05 / 1.39 | -0.01 / -1.39 / 0.12 | -0.28 | 0.45 | 0.51 | -0.71 | 0.00 | 808 | NO |
| GC 7 (diag) | anchor 11:30 ref=gd dir=with hold=flat | 513 | 1 | 0.74 | -0.68 | 0.49 | 0.40 / 1.40 | 0.05 / 0.32 / -0.14 | -0.00 | 0.46 | 0.85 | -0.24 | 0.00 | 821 | diag |
| GC 8 (diag) | anchor 10:30 ref=rd dir=with hold=flat | 515 | 1 | 0.68 | -0.39 | -0.02 | -0.51 / 1.58 | 0.07 / 0.17 / -0.96 | -0.21 | 0.57 | 0.46 | -0.49 | 0.00 | 818 | diag |
| GC 9 (diag) | anchor 13:30 ref=gd dir=with hold=flat | 509 | 1 | 0.58 | -1.19 | 0.36 | 0.32 / 1.41 | 0.05 / -0.44 / 0.17 | -0.07 | 0.56 | 0.80 | -0.35 | 0.00 | 813 | diag |
| CL 1 | anchor 13:30 ref=rv dir=against hold=flat | 512 | 2 | 0.67 | -1.46 | 0.29 | 0.02 / 1.55 | 0.10 / 0.23 / -0.44 | -0.15 | 0.43 | 0.76 | -0.29 | 0.00 | 819 | NO |
| CL 2 | anchor 10:30 ref=gd dir=against hold=60m | 512 | 2 | 0.27 | -0.65 | 0.02 | -0.17 / 0.76 | 0.04 / -0.30 / -0.05 | -0.15 | -0.17 | 0.96 | -0.26 | 0.00 | 821 | NO |
| CL 3 | anchor 12:30 ref=rd dir=with hold=60m | 513 | 2 | 0.24 | -1.14 | 0.12 | -0.02 / 0.63 | 0.05 / -0.12 / -0.07 | -0.14 | 0.37 | 0.98 | -0.24 | 0.00 | 819 | NO |
| CL 4 (diag) | anchor 13:30 ref=rd dir=against hold=flat | 509 | 1 | 0.56 | -1.29 | 0.90 | 1.29 / 1.25 | 0.07 / 0.31 / 0.48 | 0.05 | -0.19 | 0.98 | -0.05 | 0.00 | 814 | diag |
| CL 5 (diag) | anchor 13:30 ref=gv dir=against hold=flat | 512 | 1 | 0.33 | -1.50 | 0.21 | 0.19 / 1.34 | 0.01 / 0.12 / -0.24 | -0.17 | 0.19 | 0.86 | -0.28 | 0.00 | 819 | diag |
| CL 6 (diag) | anchor 13:30 ref=rd dir=against hold=60m | 496 | 1 | 0.30 | -1.61 | 0.86 | 1.44 / 0.84 | 0.03 / 0.15 / 0.98 | 0.05 | -0.30 | 1.00 | -0.03 | 0.50 | 795 | diag |
| ZN 1 (diag) | anchor 11:30 ref=gd dir=with hold=flat | 508 | 0 | -1.89 | -2.27 | -2.16 | -2.74 / -0.46 | -0.42 / -0.33 / -0.58 | -0.92 | 0.61 | 0.09 | -0.63 | 0.00 | 805 | diag |
| ZN 2 (diag) | anchor 10:30 ref=gd dir=with hold=flat | 506 | 0 | -2.02 | -2.18 | -2.26 | -2.96 / -0.01 | -0.42 / -0.37 / -0.55 | -0.85 | 0.58 | 0.04 | -0.62 | 0.00 | 813 | diag |
| ZN 3 (diag) | anchor 11:30 ref=gv dir=with hold=flat | 514 | 0 | -2.02 | -2.09 | -2.56 | -4.05 / -0.04 | -0.44 / -0.62 / -0.57 | -1.01 | 0.65 | 0.01 | -0.68 | 0.00 | 821 | diag |
| BTC 1 | anchor 10:30 ref=gd dir=with hold=flat | 458 | 2 | 1.68 | -0.05 | 0.73 | -0.25 / 1.37 | 0.28 / 0.23 / -0.40 | 0.09 | -0.13 | 0.94 | -0.08 | 1.00 | 720 | NO |
| BTC 2 | anchor 15:00 ref=gv dir=against hold=flat | 443 | 2 | 1.43 | -1.46 | 1.52 | 1.77 / 1.10 | 0.20 / 0.01 / 0.39 | 0.17 | -0.17 | 1.00 | 0.02 | 1.00 | 683 | NO |
| BTC 3 | anchor 15:00 ref=rd dir=against hold=flat | 440 | 2 | 1.23 | -1.52 | 1.46 | 2.12 / 1.40 | 0.16 / 0.01 / 0.48 | 0.15 | -0.17 | 1.00 | 0.03 | 1.00 | 680 | NO |
| BTC 4 | anchor 14:30 ref=gv dir=against hold=flat | 396 | 2 | 1.23 | -1.05 | 0.73 | 0.04 / 1.37 | 0.22 / -0.23 / 0.08 | 0.09 | -0.26 | 0.94 | -0.05 | 1.00 | 619 | NO |
| BTC 5 | anchor 11:30 ref=gd dir=with hold=60m | 442 | 2 | 1.14 | -1.69 | 0.70 | 0.04 / 1.00 | 0.26 / 0.22 / -0.30 | 0.08 | -0.08 | 0.95 | -0.07 | 0.00 | 693 | NO |
| BTC 6 | anchor 15:00 ref=rv dir=against hold=flat | 443 | 2 | 1.06 | -2.20 | 1.53 | 2.50 / 1.27 | 0.11 / 0.40 / 0.37 | 0.15 | -0.18 | 1.00 | 0.03 | 0.00 | 683 | LEAD |
| BTC 7 | anchor 10:30 ref=gd dir=with hold=60m | 458 | 2 | 0.94 | 0.09 | 0.54 | 0.13 / 1.23 | 0.16 / 0.09 / -0.25 | 0.02 | 0.04 | 0.93 | -0.13 | 0.50 | 720 | NO |
| BTC 8 | anchor 13:30 ref=rd dir=with hold=60m | 411 | 2 | 0.61 | 1.50 | 0.31 | -0.44 / 0.90 | 0.08 / -0.14 / -0.14 | -0.05 | -0.30 | 0.90 | -0.18 | 1.00 | 639 | NO |
| BTC 9 | anchor 11:30 ref=gd dir=with hold=flat | 442 | 2 | 0.61 | -1.01 | 0.27 | -0.21 / 1.31 | 0.11 / 0.20 / -0.33 | 0.00 | -0.39 | 0.75 | -0.14 | 0.50 | 693 | NO |
| BTC 10 | anchor 10:30 ref=rd dir=with hold=60m | 455 | 2 | 0.55 | 0.13 | 0.28 | -0.07 / 1.04 | 0.09 / -0.08 / -0.20 | -0.04 | 0.26 | 0.89 | -0.20 | 1.00 | 715 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 52 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 37 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 5 |
| standalone pair-window Sharpe above own random-entry null p95 | 20 |
| worst-decile corr <= +0.30 | 42 |
| plateau >= 0.75 | 11 |
| all-in uplift at 2x slippage >= +0.10 | 8 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC anchor 15:00 ref=gv dir=against hold=flat | clean | 1.37 | 2.19 | -125426 | -90110 | 465807 | -291400 | 2.68 | 41.9 | 1.66 | -93504 | 249551 | -135338 |
| BTC anchor 15:00 ref=gv dir=against hold=flat | H1 | 1.03 | 1.68 | -140354 | -122905 | 206693 | -176750 | 1.47 | 46.4 | 2.84 | -71147 | 153123 | -73488 |
| BTC anchor 15:00 ref=gv dir=against hold=flat | H2 | 3.37 | 7.18 | -55036 | -43196 | 116651 | -62836 | 4.91 | 27.8 | 2.69 | -80833 | 216449 | -84629 |
| BTC anchor 15:00 ref=gv dir=against hold=flat | all | 1.52 | 2.46 | -126694 | -92601 | 465807 | -291400 | 4.56 | 39.3 | 2.07 | -89048 | 249551 | -135338 |
| CL anchor 12:30 ref=rd dir=with hold=60m | clean | 0.26 | 0.37 | -136983 | -99198 | 547348 | -328476 | 0.43 | 49.5 | 1.51 | -83199 | 252327 | -91530 |
| CL anchor 12:30 ref=rd dir=with hold=60m | H1 | -1.33 | -1.67 | -64153 | -59968 | 175061 | -72943 | -0.89 | 53.6 | 2.71 | -81086 | 143061 | -85593 |
| CL anchor 12:30 ref=rd dir=with hold=60m | H2 | 0.21 | 0.31 | -293003 | -217505 | 731151 | -389377 | 0.19 | 50.0 | 2.22 | -96348 | 265604 | -102458 |
| CL anchor 12:30 ref=rd dir=with hold=60m | all | 0.12 | 0.17 | -183453 | -133886 | 987922 | -389377 | 0.22 | 50.6 | 1.86 | -86387 | 265604 | -102458 |
| ES anchor 14:30 ref=gd dir=with hold=60m | clean | 1.01 | 1.73 | -109624 | -95649 | 430073 | -139823 | 2.16 | 43.8 | 1.64 | -84297 | 270245 | -92093 |
| ES anchor 14:30 ref=gd dir=with hold=60m | H1 | -2.13 | -2.46 | -86436 | -77586 | 423537 | -105785 | -0.84 | 64.3 | 2.46 | -89229 | 160793 | -91705 |
| ES anchor 14:30 ref=gd dir=with hold=60m | H2 | 0.62 | 0.91 | -182233 | -140306 | 466473 | -233303 | 0.53 | 47.2 | 2.36 | -86052 | 222391 | -88757 |
| ES anchor 14:30 ref=gd dir=with hold=60m | all | 0.54 | 0.85 | -128106 | -105608 | 1135631 | -233303 | 0.72 | 47.6 | 1.93 | -86482 | 270245 | -92093 |
| GC anchor 13:30 ref=rv dir=against hold=60m | clean | 0.33 | 0.55 | -117184 | -99381 | 438016 | -122872 | 0.69 | 54.3 | 1.53 | -86543 | 292579 | -101037 |
| GC anchor 13:30 ref=rv dir=against hold=60m | H1 | 2.87 | 11.07 | -124718 | -117689 | 568099 | -137844 | 3.66 | 35.7 | 4.02 | -88553 | 233941 | -104501 |
| GC anchor 13:30 ref=rv dir=against hold=60m | H2 | -0.46 | -0.60 | -324253 | -266858 | 991451 | -359088 | -0.32 | 44.4 | 1.92 | -127016 | 260849 | -132022 |
| GC anchor 13:30 ref=rv dir=against hold=60m | all | 0.78 | 1.45 | -199408 | -159415 | 991451 | -359088 | 2.08 | 48.8 | 2.03 | -99138 | 292579 | -132022 |
| NQ anchor 14:30 ref=gd dir=with hold=60m | clean | 1.29 | 2.40 | -100416 | -85128 | 413081 | -131253 | 2.85 | 47.6 | 1.73 | -83044 | 260758 | -86057 |
| NQ anchor 14:30 ref=gd dir=with hold=60m | H1 | -1.25 | -1.64 | -83388 | -78432 | 290995 | -94604 | -0.70 | 64.3 | 2.65 | -85016 | 178279 | -87766 |
| NQ anchor 14:30 ref=gd dir=with hold=60m | H2 | 2.15 | 4.18 | -120176 | -100738 | 374407 | -138948 | 2.22 | 44.4 | 2.71 | -83774 | 215308 | -83862 |
| NQ anchor 14:30 ref=gd dir=with hold=60m | all | 1.22 | 2.22 | -105915 | -89409 | 961627 | -138948 | 1.87 | 50.0 | 2.10 | -84055 | 260758 | -87766 |
| RTY anchor 11:30 ref=gv dir=with hold=flat | clean | 0.37 | 0.55 | -129971 | -105759 | 662291 | -201654 | 0.51 | 45.7 | 1.50 | -90917 | 327421 | -117081 |
| RTY anchor 11:30 ref=gv dir=with hold=flat | H1 | 1.32 | 2.27 | -133773 | -114387 | 334862 | -147424 | 1.09 | 35.7 | 3.20 | -75828 | 137683 | -77590 |
| RTY anchor 11:30 ref=gv dir=with hold=flat | H2 | 0.00 | 0.01 | -122366 | -108107 | 513829 | -133960 | 0.00 | 55.6 | 2.21 | -82860 | 203465 | -83174 |
| RTY anchor 11:30 ref=gv dir=with hold=flat | all | 0.47 | 0.71 | -138053 | -110772 | 662291 | -201654 | 1.06 | 45.8 | 1.91 | -88083 | 327421 | -117081 |
| YM anchor 11:30 ref=gd dir=with hold=flat | clean | 0.65 | 0.93 | -133263 | -110375 | 432381 | -234459 | 1.36 | 40.0 | 1.58 | -85977 | 274937 | -99584 |
| YM anchor 11:30 ref=gd dir=with hold=flat | H1 | 0.25 | 0.35 | -111706 | -101933 | 371951 | -119515 | 0.14 | 50.0 | 3.01 | -69304 | 133943 | -69776 |
| YM anchor 11:30 ref=gd dir=with hold=flat | H2 | 0.23 | 0.34 | -108555 | -90642 | 356999 | -116638 | 0.18 | 50.0 | 2.19 | -94237 | 216185 | -102619 |
| YM anchor 11:30 ref=gd dir=with hold=flat | all | 0.51 | 0.73 | -127843 | -106565 | 432381 | -234459 | 1.64 | 43.5 | 1.93 | -86964 | 274937 | -102619 |
| ZN anchor 10:30 ref=gd dir=with hold=flat (diag) | clean | -1.99 | -2.24 | -158454 | -136542 | 1965388 | -236968 | -0.92 | 61.0 | 1.04 | -99324 | 405168 | -129267 |
| ZN anchor 10:30 ref=gd dir=with hold=flat (diag) | H1 | -2.03 | -2.36 | -86731 | -75708 | 328812 | -104684 | -0.90 | 60.7 | 2.46 | -77707 | 149032 | -84862 |
| ZN anchor 10:30 ref=gd dir=with hold=flat (diag) | H2 | -3.58 | -3.51 | -116967 | -108804 | 971595 | -117912 | -0.88 | 72.2 | 1.75 | -104482 | 218031 | -105729 |
| ZN anchor 10:30 ref=gd dir=with hold=flat (diag) | all | -2.26 | -2.49 | -144940 | -125601 | 3038710 | -236968 | -0.97 | 63.7 | 1.41 | -99099 | 405168 | -129267 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES anchor 14:30 ref=gd dir=with hold=60m | -20.9 | 7.4 | 13.2 | 22.0 | 6.7 / 15.6 | 4.3 / 7.5 | NO |
| NQ anchor 14:30 ref=gd dir=with hold=60m | -9.9 | 16.4 | 18.9 | 38.6 | 17.7 / 19.3 | 11.8 / 15.7 | NO |
| RTY anchor 11:30 ref=gv dir=with hold=flat | -22.1 | -33.4 | 12.5 | 4.7 | -34.5 / 6.6 | 31.3 / 33.4 | NO |
| YM anchor 11:30 ref=gd dir=with hold=flat | -22.1 | -6.5 | 13.2 | 23.6 | -2.4 / 14.0 | 46.3 / 46.1 | NO |
| GC anchor 13:30 ref=rv dir=against hold=60m | -6.9 | -81.6 | -15.2 | 9.3 | -9.6 / 13.8 | -21.6 / -2.2 | NO |
| CL anchor 12:30 ref=rd dir=with hold=60m | -27.6 | -41.3 | 2.7 | 7.9 | -42.4 / 7.3 | 16.0 / 23.3 | NO |
| ZN anchor 10:30 ref=gd dir=with hold=flat (diag) | -63.1 | -55.6 | -9.1 | -57.5 | -56.8 / -10.7 | 17.4 / 26.5 | NO |
| BTC anchor 15:00 ref=gv dir=against hold=flat | -6.3 | -71.3 | 9.0 | 30.7 | -72.7 / 0.3 | 25.1 / 30.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 anchor 10:30 ref=rd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2649 | 0.6 | -28.8 | -14.6 | 29.4 | 0.01 / -0.46 / -0.23 | 180.4 / 151.0 |
| ES 2 anchor 14:30 ref=gd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2594 | 10.3 | -19.1 | -4.9 | 29.4 | 0.34 / -0.63 / -0.16 | 66.3 / 36.9 |
| ES 3 anchor 10:30 ref=gd dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2670 | 16.4 | -12.9 | 1.3 | 29.4 | 0.54 / -0.43 / 0.04 | 68.5 / 39.1 |
| ES 4 anchor 14:30 ref=rd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2580 | 11.5 | -17.9 | -3.7 | 29.4 | 0.36 / -0.57 / -0.12 | 45.8 / 16.5 |
| ES 5 anchor 11:30 ref=rd dir=with hold=flat | positive pre-2023 | 2663 | 29.7 | 0.4 | 14.6 | 29.4 | 0.45 / 0.01 / 0.22 | 96.4 / 67.0 |
| ES 6 anchor 11:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2660 | 10.4 | -19.0 | -4.8 | 29.4 | 0.16 / -0.30 / -0.08 | 69.4 / 40.0 |
| ES 7 anchor 10:30 ref=gv dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2693 | 6.3 | -23.1 | -8.9 | 29.4 | 0.09 / -0.35 / -0.14 | 70.2 / 40.8 |
| ES 8 anchor 14:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2594 | 23.2 | -6.2 | 8.0 | 29.4 | 0.51 / -0.13 / 0.18 | 51.1 / 21.7 |
| ES 9 anchor 11:30 ref=rv dir=with hold=flat | positive pre-2023 | 2693 | 30.1 | 0.8 | 15.0 | 29.4 | 0.46 / 0.01 / 0.23 | 51.4 / 22.0 |
| ES 10 anchor 11:30 ref=gd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2660 | 3.6 | -25.8 | -11.6 | 29.4 | 0.15 / -1.03 / -0.46 | 31.3 / 2.0 |
| NQ 1 anchor 10:30 ref=rd dir=with hold=flat | positive pre-2023 | 2679 | 46.7 | 32.4 | 40.9 | 14.4 | 0.46 / 0.32 / 0.40 | 413.0 / 398.7 |
| NQ 2 anchor 14:30 ref=gd dir=with hold=60m | positive pre-2023 | 2609 | 35.6 | 21.2 | 29.8 | 14.4 | 0.76 / 0.45 / 0.64 | 105.3 / 91.0 |
| NQ 3 anchor 14:30 ref=rd dir=with hold=60m | positive pre-2023 | 2603 | 36.3 | 21.9 | 30.5 | 14.4 | 0.85 / 0.52 / 0.72 | 95.6 / 81.3 |
| NQ 4 anchor 10:30 ref=rd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2679 | 0.4 | -14.0 | -5.4 | 14.4 | 0.01 / -0.28 / -0.11 | 97.1 / 82.7 |
| NQ 5 anchor 10:30 ref=gd dir=with hold=flat | positive pre-2023 | 2680 | 33.5 | 19.1 | 27.7 | 14.4 | 0.34 / 0.19 / 0.28 | 181.6 / 167.2 |
| NQ 6 anchor 14:30 ref=rd dir=with hold=flat | positive pre-2023 | 2603 | 42.5 | 28.1 | 36.7 | 14.4 | 0.63 / 0.42 / 0.55 | 108.8 / 94.5 |
| NQ 7 anchor 15:00 ref=rd dir=with hold=flat | positive pre-2023 | 2605 | 55.2 | 40.8 | 49.4 | 14.4 | 0.96 / 0.71 / 0.86 | 81.2 / 66.9 |
| NQ 8 anchor 11:30 ref=gd dir=with hold=flat | positive pre-2023 | 2684 | 39.2 | 24.9 | 33.4 | 14.4 | 0.40 / 0.25 / 0.34 | 148.4 / 134.1 |
| NQ 9 anchor 11:30 ref=rd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 2684 | 10.4 | -3.9 | 4.6 | 14.4 | 0.27 / -0.10 / 0.12 | 79.8 / 65.4 |
| NQ 10 anchor 11:30 ref=gd dir=with hold=60m | negative pre-2023 | 2684 | -4.4 | -18.8 | -10.2 | 14.4 | -0.11 / -0.47 / -0.26 | 57.3 / 42.9 |
| RTY 1 anchor 10:30 ref=gd dir=against hold=60m | gross-positive, cost-negative pre-2023 | 1537 | 1.4 | -13.0 | -10.7 | 14.4 | 0.05 / -0.45 / -0.37 | 29.5 / 15.1 |
| RTY 2 anchor 11:30 ref=gv dir=with hold=flat | gross-positive, cost-negative pre-2023 | 1542 | 9.1 | -5.3 | -3.0 | 14.4 | 0.21 / -0.13 / -0.08 | 31.9 / 17.6 |
| RTY 3 anchor 10:30 ref=rd dir=with hold=60m | gross-positive, cost-negative pre-2023 | 1536 | 7.2 | -7.1 | -4.9 | 14.4 | 0.25 / -0.25 / -0.17 | 24.2 / 9.9 |
| RTY 4 (diag) anchor 14:30 ref=rd dir=with hold=60m | positive pre-2023 | 1487 | 15.3 | 1.0 | 3.2 | 14.4 | 0.67 / 0.04 / 0.14 | 20.8 / 6.4 |
| RTY 5 (diag) anchor 11:30 ref=rd dir=with hold=60m | negative pre-2023 | 1533 | -2.0 | -16.4 | -14.1 | 14.4 | -0.09 / -0.76 / -0.66 | 24.1 / 9.8 |
| RTY 6 (diag) anchor 10:30 ref=gd dir=against hold=flat | negative pre-2023 | 1537 | -0.8 | -15.2 | -12.9 | 14.4 | -0.01 / -0.27 / -0.23 | 36.8 / 22.4 |
| YM 1 anchor 13:30 ref=gv dir=with hold=flat | positive pre-2023 | 2614 | 19.0 | 4.7 | 10.4 | 14.4 | 0.53 / 0.13 / 0.29 | 57.9 / 43.6 |
| YM 2 anchor 11:30 ref=gd dir=with hold=flat | negative pre-2023 | 2683 | -8.4 | -22.8 | -17.0 | 14.4 | -0.17 / -0.45 / -0.34 | 56.0 / 41.7 |
| YM 3 anchor 11:30 ref=gv dir=with hold=flat | negative pre-2023 | 2696 | -17.0 | -31.4 | -25.6 | 14.4 | -0.37 / -0.68 / -0.56 | 59.0 / 44.6 |
| YM 4 anchor 11:30 ref=rd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2680 | 1.4 | -13.0 | -7.3 | 14.4 | 0.02 / -0.26 / -0.15 | 53.8 / 39.5 |
| YM 5 anchor 11:30 ref=gd dir=with hold=60m | negative pre-2023 | 2683 | -3.0 | -17.3 | -11.6 | 14.4 | -0.15 / -0.88 / -0.59 | 22.2 / 7.9 |
| YM 6 anchor 15:00 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2610 | 6.6 | -7.8 | -2.0 | 14.4 | 0.20 / -0.25 / -0.07 | 30.8 / 16.4 |
| YM 7 anchor 14:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2608 | 10.3 | -4.1 | 1.7 | 14.4 | 0.27 / -0.12 / 0.04 | 26.0 / 11.7 |
| YM 8 anchor 15:00 ref=rd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2602 | 4.4 | -9.9 | -4.2 | 14.4 | 0.16 / -0.38 / -0.16 | 24.0 / 9.6 |
| YM 9 anchor 10:30 ref=gv dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2695 | 6.1 | -8.3 | -2.5 | 14.4 | 0.24 / -0.33 / -0.10 | 18.9 / 4.5 |
| YM 10 anchor 10:30 ref=rd dir=with hold=flat | negative pre-2023 | 2677 | -6.2 | -20.5 | -14.8 | 14.4 | -0.12 / -0.40 / -0.29 | 18.2 / 3.9 |
| GC 1 anchor 10:30 ref=gd dir=with hold=flat | negative pre-2023 | 2649 | -2.4 | -26.8 | -17.0 | 24.4 | -0.06 / -0.62 / -0.39 | 84.0 / 59.7 |
| GC 2 anchor 11:30 ref=rd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2639 | 10.1 | -14.3 | -4.5 | 24.4 | 0.27 / -0.37 / -0.11 | 62.5 / 38.1 |
| GC 3 anchor 14:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2556 | 14.7 | -9.6 | 0.1 | 24.4 | 0.72 / -0.46 / 0.01 | 40.6 / 16.3 |
| GC 4 anchor 13:30 ref=rv dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2598 | 4.6 | -19.8 | -10.0 | 24.4 | 0.24 / -1.05 / -0.53 | 33.5 / 9.2 |
| GC 5 anchor 12:30 ref=rd dir=with hold=flat | negative pre-2023 | 2584 | -6.1 | -30.5 | -20.7 | 24.4 | -0.19 / -0.97 / -0.66 | 43.5 / 19.1 |
| GC 6 anchor 13:30 ref=rd dir=with hold=flat | negative pre-2023 | 2585 | -4.9 | -29.3 | -19.5 | 24.4 | -0.17 / -1.05 / -0.69 | 35.8 / 11.4 |
| GC 7 (diag) anchor 11:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2645 | 0.8 | -23.6 | -13.8 | 24.4 | 0.03 / -0.68 / -0.40 | 72.3 / 47.9 |
| GC 8 (diag) anchor 10:30 ref=rd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2642 | 5.9 | -18.5 | -8.7 | 24.4 | 0.13 / -0.39 / -0.18 | 84.4 / 60.0 |
| GC 9 (diag) anchor 13:30 ref=gd dir=with hold=flat | negative pre-2023 | 2595 | -9.4 | -33.8 | -24.0 | 24.4 | -0.33 / -1.19 / -0.84 | 48.2 / 23.9 |
| CL 1 anchor 13:30 ref=rv dir=against hold=flat | negative pre-2023 | 2622 | -22.7 | -47.1 | -44.5 | 24.4 | -0.71 / -1.46 / -1.38 | 41.6 / 17.3 |
| CL 2 anchor 10:30 ref=gd dir=against hold=60m | gross-positive, cost-negative pre-2023 | 2675 | 2.0 | -22.4 | -19.7 | 24.4 | 0.06 / -0.65 / -0.58 | 31.2 / 6.9 |
| CL 3 anchor 12:30 ref=rd dir=with hold=60m | negative pre-2023 | 2621 | -0.2 | -24.6 | -22.1 | 24.4 | -0.01 / -1.14 / -1.02 | 31.6 / 7.2 |
| CL 4 (diag) anchor 13:30 ref=rd dir=against hold=flat | negative pre-2023 | 2606 | -19.8 | -44.1 | -41.6 | 24.4 | -0.58 / -1.29 / -1.22 | 40.0 / 15.6 |
| CL 5 (diag) anchor 13:30 ref=gv dir=against hold=flat | negative pre-2023 | 2622 | -25.2 | -49.5 | -47.0 | 24.4 | -0.76 / -1.50 / -1.42 | 31.1 / 6.7 |
| CL 6 (diag) anchor 13:30 ref=rd dir=against hold=60m | negative pre-2023 | 2588 | -22.6 | -47.0 | -44.4 | 24.4 | -0.77 / -1.61 / -1.52 | 30.4 / 6.1 |
| ZN 1 (diag) anchor 11:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2609 | 8.6 | -27.0 | -32.2 | 35.6 | 0.72 / -2.27 / -2.69 | 11.5 / -24.1 |
| ZN 2 (diag) anchor 10:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2624 | 3.6 | -32.0 | -37.1 | 35.6 | 0.24 / -2.18 / -2.52 | 6.1 / -29.5 |
| ZN 3 (diag) anchor 11:30 ref=gv dir=with hold=flat | gross-positive, cost-negative pre-2023 | 2683 | 9.5 | -26.1 | -31.3 | 35.6 | 0.76 / -2.09 / -2.49 | 11.9 / -23.8 |
| BTC 1 anchor 10:30 ref=gd dir=with hold=flat | gross-positive, cost-negative pre-2023 | 333 | 41.1 | -13.2 | 19.2 | 54.4 | 0.20 / -0.05 / 0.10 | 577.2 / 522.9 |
| BTC 2 anchor 15:00 ref=gv dir=against hold=flat | negative pre-2023 | 315 | -97.5 | -151.8 | -119.5 | 54.4 | -0.94 / -1.46 / -1.15 | 325.1 / 270.7 |
| BTC 3 anchor 15:00 ref=rd dir=against hold=flat | negative pre-2023 | 313 | -108.5 | -162.9 | -130.6 | 54.4 | -1.01 / -1.52 / -1.22 | 271.4 / 217.1 |
| BTC 4 anchor 14:30 ref=gv dir=against hold=flat | negative pre-2023 | 281 | -77.9 | -132.3 | -99.9 | 54.4 | -0.61 / -1.05 / -0.79 | 308.2 / 253.8 |
| BTC 5 anchor 11:30 ref=gd dir=with hold=60m | negative pre-2023 | 310 | -77.0 | -131.4 | -99.1 | 54.4 | -0.99 / -1.69 / -1.28 | 246.6 / 192.2 |
| BTC 6 anchor 15:00 ref=rv dir=against hold=flat | negative pre-2023 | 315 | -159.0 | -213.4 | -181.0 | 54.4 | -1.64 / -2.20 / -1.87 | 226.4 / 172.1 |
| BTC 7 anchor 10:30 ref=gd dir=with hold=60m | positive pre-2023 | 333 | 61.9 | 7.6 | 40.0 | 54.4 | 0.67 / 0.09 / 0.44 | 216.8 / 162.4 |
| BTC 8 anchor 13:30 ref=rd dir=with hold=60m | positive pre-2023 | 268 | 187.2 | 132.9 | 165.6 | 54.4 | 2.10 / 1.50 / 1.86 | 162.7 / 108.4 |
| BTC 9 anchor 11:30 ref=gd dir=with hold=flat | negative pre-2023 | 310 | -159.6 | -214.0 | -181.7 | 54.4 | -0.75 / -1.01 / -0.86 | 243.8 / 189.5 |
| BTC 10 anchor 10:30 ref=rd dir=with hold=60m | positive pre-2023 | 332 | 68.0 | 13.6 | 46.2 | 54.4 | 0.69 / 0.13 / 0.47 | 151.0 / 96.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 14 cells pass the clean rule against a replicate mean of 16.6 (p(count) = 0.79, p(top) = 0.33); CL: 3 cells pass the clean rule against a replicate mean of 8.4 (p(count) = 1.00, p(top) = 0.97); ES: 10 cells pass the clean rule against a replicate mean of 10.1 (p(count) = 0.53, p(top) = 0.92); GC: 6 cells pass the clean rule against a replicate mean of 11.3 (p(count) = 0.99, p(top) = 0.95); NQ: 23 cells pass the clean rule against a replicate mean of 18.5 (p(count) = 0.12, p(top) = 0.47); RTY: 3 cells pass the clean rule against a replicate mean of 11.3 (p(count) = 1.00, p(top) = 0.98); YM: 11 cells pass the clean rule against a replicate mean of 12.9 (p(count) = 0.74, p(top) = 0.99); ZN: 0 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 1.00).
- Of 52 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.24 (NQ anchor 14:30 ref=gd dir=with hold=60m); bootstrap lower bound > 0 for 5 cells; plateau >= 0.75 for 11; 2x-slippage all-in uplift >= +0.10 for 8; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell BTC anchor 15:00 ref=rv dir=against hold=flat: uplift +0.11/+0.40/+0.37, boot lo +0.03, plateau 0.00, 2x-slip +0.15, wd corr -0.18, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'gross-positive, cost-negative pre-2023': 23, 'negative pre-2023': 16, 'positive pre-2023': 13}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_17.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw17/ (`SW17_CO_all_selected_scored.csv`).

DONE SW17
