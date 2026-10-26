# REPORT B11 - opening-range and prior-day-level breakouts / fades on ES, RTY, GC, CL, ZN

**Verdict: LEAD. FOUND 0, LEAD 4, INSURANCE 0.** 54 selected cells (+6 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.25; best pair-window standalone Sharpe +1.39.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: ES, RTY, GC, CL, ZN, YM, BTC. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     192 |        192 |        59 |               1.82  |                2 |         10 |            0 |
| CL    |     192 |        192 |        24 |               0.955 |                2 |         10 |            0 |
| ES    |     192 |        192 |        27 |               1.304 |                2 |         10 |            0 |
| GC    |     192 |        192 |        20 |               1.376 |                2 |         10 |            0 |
| RTY   |     192 |        192 |         4 |               1.085 |                2 |          4 |            3 |
| YM    |     192 |        192 |        41 |               1.14  |                2 |         10 |            0 |
| ZN    |     192 |        192 |         0 |              -1.096 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                   27 |           18.795 |              30 |      0.03  |                       1.024 |            0.847 |           1.077 |    0.11  |       1.304 |                1.845 |
| RTY   |     200 |                    4 |           16.935 |              29 |      1     |                       0.403 |            0.817 |           1.053 |    1     |       0.552 |                2.003 |
| GC    |     200 |                   20 |           18.855 |              34 |      0.425 |                       0.746 |            0.891 |           1.141 |    0.82  |       1.376 |                2.079 |
| CL    |     200 |                   24 |            8.26  |              17 |      0     |                       0.766 |            0.583 |           0.801 |    0.085 |       0.955 |                1.562 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| YM    |     200 |                   41 |           28.545 |              40 |      0     |                       0.956 |            1.055 |           1.268 |    0.8   |       1.14  |                2.018 |
| BTC   |     200 |                   59 |           33.95  |              49 |      0     |                       1.395 |            1.192 |           1.4   |    0.065 |       1.82  |                2.239 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | PD 15m fade exit=b20.2xADR | 393 | 2 | 1.30 | -0.98 | 0.92 | 0.48 / 1.11 | 0.23 / -0.30 / 0.23 | 0.09 | 0.15 | 0.98 | -0.05 | 0.00 | 620 | NO |
| ES 2 | PD 15m fade exit=hd0.2xADR | 393 | 2 | 1.16 | -1.14 | 0.62 | -0.79 / 0.85 | 0.20 / -0.19 / -0.11 | 0.03 | -0.05 | 0.96 | -0.06 | 0.50 | 620 | NO |
| ES 3 | OR15 5m with exit=b20.3xADR | 515 | 2 | 1.15 | -0.14 | 0.77 | 0.21 / 1.06 | 0.16 / 0.19 / -0.31 | -0.00 | -0.21 | 0.93 | -0.13 | 0.00 | 824 | NO |
| ES 4 | OR15 15m with exit=b20.3xADR | 513 | 2 | 1.09 | -0.24 | 0.64 | 0.08 / 1.04 | 0.13 / 0.03 / -0.26 | -0.04 | 0.14 | 0.94 | -0.17 | 0.75 | 821 | NO |
| ES 5 | OR15 15m with exit=b20.2xADR | 513 | 2 | 0.98 | -0.06 | 0.52 | -0.21 / 0.95 | 0.10 / -0.19 / -0.19 | -0.07 | 0.21 | 0.96 | -0.18 | 0.00 | 821 | NO |
| ES 6 | OR15 5m with exit=b10.3xADR | 515 | 2 | 0.95 | -0.59 | 0.71 | 0.34 / 1.09 | 0.15 / 0.05 / -0.27 | -0.02 | -0.11 | 0.99 | -0.16 | 0.00 | 824 | NO |
| ES 7 | PD 15m fade exit=hd0.3xADR | 393 | 2 | 0.95 | -0.66 | 0.83 | 0.38 / 1.33 | 0.18 / -0.01 / 0.07 | 0.09 | 0.13 | 0.94 | -0.01 | 0.50 | 620 | NO |
| ES 8 | PD 15m fade exit=b10.2xADR | 393 | 2 | 0.91 | -1.28 | 0.30 | -0.46 / 0.85 | 0.18 / -0.53 / 0.08 | -0.02 | -0.24 | 0.92 | -0.15 | 0.50 | 620 | NO |
| ES 9 | PD 5m fade exit=hd0.3xADR | 405 | 2 | 0.88 | -0.68 | 0.62 | 0.08 / 1.05 | 0.18 / -0.21 / -0.12 | 0.02 | -0.01 | 0.91 | -0.10 | 0.50 | 641 | NO |
| ES 10 | PD 5m fade exit=hd0.2xADR | 405 | 2 | 0.86 | -1.05 | 0.26 | -0.90 / 0.77 | 0.18 / -0.43 / -0.21 | -0.04 | -0.14 | 0.87 | -0.15 | 0.50 | 641 | NO |
| RTY 1 | PD 5m fade exit=hd0.3xADR | 382 | 2 | 0.55 | -0.26 | 0.11 | -0.48 / 0.96 | 0.05 / -0.31 / -0.29 | -0.09 | -0.37 | 0.77 | -0.23 | 0.00 | 606 | NO |
| RTY 2 | PD 5m fade exit=b20.3xADR | 382 | 2 | 0.52 | -0.39 | 0.22 | -0.07 / 1.35 | 0.05 / -0.30 / -0.25 | -0.09 | -0.22 | 0.80 | -0.25 | 0.00 | 606 | NO |
| RTY 3 | OR30 5m fade exit=hd0.1xADR | 494 | 2 | 0.45 | -0.57 | 0.08 | -0.63 / 0.90 | 0.05 / -0.49 / 0.01 | -0.08 | 0.26 | 0.89 | -0.20 | 0.00 | 798 | NO |
| RTY 4 | OR30 15m with exit=hd0.3xADR | 471 | 2 | 0.09 | 0.02 | 0.10 | 0.11 / 1.29 | -0.01 / 0.47 / -0.32 | -0.06 | 0.35 | 0.76 | -0.23 | 0.00 | 767 | NO |
| RTY 5 (diag) | PD 15m fade exit=b20.3xADR | 364 | 1 | 1.08 | -0.27 | 0.49 | -0.25 / 1.11 | 0.15 / -0.51 / -0.09 | -0.03 | -0.29 | 0.95 | -0.18 | 0.50 | 580 | diag |
| RTY 6 (diag) | PD 15m fade exit=hd0.3xADR | 364 | 1 | 1.00 | -0.15 | 0.40 | -0.78 / 1.29 | 0.13 / -0.47 / -0.11 | -0.03 | -0.35 | 0.87 | -0.15 | 0.00 | 580 | diag |
| RTY 7 (diag) | PD 15m fade exit=tr0.3xADR | 364 | 1 | 0.96 | -0.65 | 0.52 | -0.09 / 0.94 | 0.12 / -0.36 / -0.17 | -0.05 | -0.04 | 0.99 | -0.18 | 0.00 | 580 | diag |
| GC 1 | PD 5m with exit=tr0.1xADR | 376 | 2 | 1.38 | -0.74 | 0.40 | -0.54 / 1.15 | 0.20 / -0.63 / -0.28 | -0.13 | -0.15 | 0.95 | -0.27 | 0.00 | 606 | NO |
| GC 2 | OR30 15m fade exit=hd0.1xADR | 504 | 2 | 1.14 | -0.63 | 0.17 | -0.58 / 0.98 | 0.19 / -0.79 / -0.19 | -0.10 | 0.13 | 0.81 | -0.27 | 0.00 | 805 | NO |
| GC 3 | PD 5m with exit=b10.1xADR | 376 | 2 | 1.05 | -0.70 | 0.65 | 0.49 / 1.09 | 0.17 / 0.05 / -0.23 | -0.01 | 0.35 | 1.00 | -0.22 | 0.00 | 606 | NO |
| GC 4 | PD 5m with exit=b20.2xADR | 376 | 2 | 0.87 | -0.79 | -0.09 | -0.87 / 1.17 | 0.11 / -0.64 / -0.54 | -0.19 | 0.55 | 0.65 | -0.43 | 0.00 | 606 | NO |
| GC 5 | OR60 5m fade exit=hd0.1xADR | 493 | 2 | 0.79 | -0.87 | 0.78 | 0.96 / 1.42 | 0.14 / 0.49 / 0.09 | 0.16 | -0.55 | 0.96 | -0.09 | 0.00 | 784 | NO |
| GC 6 | OR60 5m fade exit=tr0.3xADR | 493 | 2 | 0.55 | -1.05 | 0.47 | 0.55 / 1.05 | 0.07 / 0.17 / 0.09 | 0.06 | -0.48 | 0.88 | -0.21 | 0.50 | 784 | NO |
| GC 7 | OR30 15m fade exit=tr0.3xADR | 504 | 2 | 0.52 | -0.79 | 0.39 | 0.43 / 1.11 | 0.06 / -0.09 / 0.19 | 0.02 | -0.06 | 0.88 | -0.19 | 0.25 | 805 | NO |
| GC 8 | OR60 5m fade exit=b10.3xADR | 493 | 2 | 0.40 | -0.94 | 0.18 | 0.13 / 1.41 | 0.05 / -0.14 / -0.17 | -0.05 | -0.37 | 0.78 | -0.34 | 0.00 | 784 | NO |
| GC 9 | OR60 5m fade exit=b20.2xADR | 493 | 2 | 0.39 | -0.67 | 0.57 | 0.79 / 1.60 | 0.07 / 0.08 / 0.12 | 0.07 | -0.39 | 0.94 | -0.18 | 0.25 | 784 | NO |
| GC 10 | OR60 15m fade exit=b20.1xADR | 479 | 2 | 0.38 | -1.70 | -0.09 | -0.32 / 0.80 | 0.01 / -0.67 / -0.23 | -0.22 | 0.07 | 0.74 | -0.49 | 0.00 | 765 | NO |
| CL 1 | OR15 5m fade exit=hd0.1xADR | 516 | 2 | 0.95 | -1.03 | 0.08 | -0.88 / 0.68 | 0.19 / -0.54 / -0.41 | -0.15 | 0.03 | 0.95 | -0.26 | 0.00 | 825 | NO |
| CL 2 | OR15 15m fade exit=hd0.2xADR | 516 | 2 | 0.91 | -1.30 | 0.94 | 1.04 / 0.78 | 0.21 / 0.16 / 0.34 | 0.16 | 0.11 | 1.00 | 0.00 | 0.25 | 825 | LEAD |
| CL 3 | OR30 5m fade exit=hd0.2xADR | 515 | 2 | 0.79 | -0.75 | 0.18 | -0.35 / 0.69 | 0.19 / 0.29 / -0.45 | -0.03 | -0.53 | 0.91 | -0.18 | 0.25 | 822 | NO |
| CL 4 | OR15 15m fade exit=hd0.3xADR | 516 | 2 | 0.79 | -1.41 | 0.96 | 1.20 / 1.11 | 0.16 / 0.39 / 0.28 | 0.15 | 0.14 | 1.00 | -0.01 | 0.00 | 825 | LEAD |
| CL 5 | OR15 5m fade exit=hd0.3xADR | 516 | 2 | 0.76 | -0.81 | 0.63 | 0.53 / 0.96 | 0.14 / -0.05 / 0.04 | 0.03 | -0.12 | 0.96 | -0.11 | 0.25 | 825 | NO |
| CL 6 | OR15 5m fade exit=hd0.2xADR | 516 | 2 | 0.74 | -0.82 | 0.31 | -0.12 / 0.89 | 0.16 / -0.29 / -0.13 | -0.04 | -0.10 | 0.94 | -0.17 | 0.50 | 825 | NO |
| CL 7 | OR30 5m fade exit=hd0.1xADR | 515 | 2 | 0.73 | -0.99 | -0.13 | -1.06 / 0.52 | 0.12 / -0.25 / -0.55 | -0.20 | -0.12 | 0.87 | -0.30 | 0.00 | 822 | NO |
| CL 8 | OR30 5m fade exit=tr0.3xADR | 515 | 2 | 0.67 | -0.63 | 0.55 | 0.44 / 1.21 | 0.11 / 0.07 / 0.11 | 0.01 | -0.35 | 1.00 | -0.11 | 0.50 | 822 | NO |
| CL 9 | OR15 15m fade exit=b10.3xADR | 516 | 2 | 0.67 | -1.38 | 0.62 | 0.66 / 0.96 | 0.14 / 0.23 / 0.21 | 0.09 | 0.04 | 0.95 | -0.09 | 0.00 | 825 | LEAD |
| CL 10 | OR15 15m fade exit=hd0.1xADR | 516 | 2 | 0.65 | -1.41 | 0.30 | 0.08 / 0.48 | 0.13 / -0.39 / -0.18 | -0.12 | 0.25 | 0.99 | -0.26 | 0.00 | 825 | NO |
| ZN 1 (diag) | OR30 5m fade exit=hd0.3xADR | 497 | 0 | -1.10 | -2.54 | -1.55 | -2.72 / -1.56 | -0.20 / -0.50 / -0.34 | -0.65 | -0.36 | 0.96 | -0.44 | 0.00 | 792 | diag |
| ZN 2 (diag) | OR15 15m fade exit=hd0.3xADR | 494 | 0 | -1.29 | -2.74 | -1.78 | -3.13 / -1.81 | -0.21 / -0.54 / -0.44 | -0.69 | -0.66 | 0.95 | -0.47 | 0.00 | 793 | diag |
| ZN 3 (diag) | OR30 5m fade exit=b20.3xADR | 497 | 0 | -1.42 | -2.61 | -1.84 | -2.74 / -2.20 | -0.28 / -0.50 / -0.41 | -0.72 | -0.18 | 0.95 | -0.52 | 0.00 | 792 | diag |
| YM 1 | PD 15m fade exit=hd0.2xADR | 367 | 2 | 1.14 | 0.12 | 0.53 | -0.83 / 1.12 | 0.16 / -0.18 / -0.13 | 0.03 | -0.63 | 0.93 | -0.09 | 0.50 | 584 | NO |
| YM 2 | OR30 15m with exit=b20.1xADR | 492 | 2 | 1.11 | -0.54 | 0.59 | -0.32 / 0.89 | 0.15 / -0.01 / -0.17 | -0.01 | 0.50 | 0.98 | -0.12 | 0.25 | 783 | NO |
| YM 3 | PD 15m fade exit=tr0.3xADR | 367 | 2 | 1.10 | -0.13 | 0.73 | 0.20 / 1.08 | 0.15 / -0.05 / -0.14 | 0.03 | 0.17 | 0.98 | -0.12 | 0.50 | 584 | NO |
| YM 4 | PD 15m fade exit=b20.2xADR | 367 | 2 | 1.04 | -0.06 | 0.47 | -0.44 / 0.87 | 0.19 / -0.50 / -0.03 | 0.01 | -0.25 | 0.89 | -0.15 | 0.00 | 584 | NO |
| YM 5 | OR30 15m with exit=b10.2xADR | 492 | 2 | 0.93 | -0.48 | 0.31 | -0.61 / 1.12 | 0.14 / -0.08 / -0.29 | -0.03 | 0.52 | 0.89 | -0.18 | 0.25 | 783 | NO |
| YM 6 | OR60 15m with exit=b10.1xADR | 457 | 2 | 0.90 | -0.61 | 0.24 | -0.90 / 0.99 | 0.13 / -0.43 / -0.09 | -0.09 | 0.39 | 0.94 | -0.17 | 0.00 | 711 | NO |
| YM 7 | PD 15m fade exit=hd0.3xADR | 367 | 2 | 0.86 | 0.13 | 0.32 | -0.71 / 1.34 | 0.11 / -0.07 / -0.23 | -0.01 | -0.65 | 0.78 | -0.13 | 0.50 | 584 | NO |
| YM 8 | OR15 15m with exit=b10.3xADR | 505 | 2 | 0.84 | -0.69 | 0.16 | -0.76 / 1.09 | 0.08 / 0.13 / -0.54 | -0.09 | 0.21 | 0.88 | -0.25 | 0.00 | 809 | NO |
| YM 9 | OR30 15m with exit=b10.3xADR | 492 | 2 | 0.83 | -0.38 | 0.40 | -0.27 / 1.39 | 0.10 / 0.15 / -0.26 | -0.02 | 0.46 | 0.87 | -0.17 | 0.50 | 783 | NO |
| YM 10 | OR15 5m with exit=b20.3xADR | 511 | 2 | 0.82 | -0.07 | 0.41 | -0.15 / 1.09 | 0.06 / 0.44 / -0.44 | -0.04 | 0.23 | 0.82 | -0.19 | 0.00 | 817 | NO |
| BTC 1 | OR30 5m with exit=b10.1xADR | 505 | 2 | 1.82 | 0.37 | 0.95 | -0.52 / 1.23 | 0.28 / -0.06 / -0.29 | 0.04 | -0.30 | 0.98 | -0.07 | 0.50 | 787 | NO |
| BTC 2 | OR30 5m with exit=b20.2xADR | 505 | 2 | 1.62 | 1.90 | 1.05 | 0.20 / 0.87 | 0.28 / 0.22 / -0.26 | 0.13 | 0.09 | 0.98 | -0.03 | 0.25 | 787 | NO |
| BTC 3 | OR30 5m with exit=b10.2xADR | 505 | 2 | 1.54 | 0.92 | 0.79 | -0.46 / 1.30 | 0.24 / -0.36 / -0.16 | 0.03 | 0.10 | 0.98 | -0.11 | 0.50 | 787 | NO |
| BTC 4 | OR30 15m with exit=b10.1xADR | 501 | 2 | 1.39 | -0.46 | 0.53 | -0.83 / 0.96 | 0.18 / -0.13 / -0.38 | -0.05 | -0.25 | 0.93 | -0.16 | 0.25 | 777 | NO |
| BTC 5 | OR30 5m with exit=tr0.1xADR | 505 | 2 | 1.34 | 0.77 | 1.13 | 0.79 / 1.16 | 0.21 / 0.18 / 0.00 | 0.07 | -0.29 | 1.00 | -0.02 | 0.50 | 787 | NO |
| BTC 6 | OR30 5m with exit=hd0.2xADR | 505 | 2 | 1.32 | 2.57 | 0.90 | 0.33 / 0.87 | 0.23 / 0.14 / -0.23 | 0.10 | 0.01 | 0.97 | -0.05 | 0.25 | 787 | NO |
| BTC 7 | OR60 15m with exit=b10.3xADR | 459 | 2 | 1.28 | 1.10 | 0.68 | -0.23 / 1.12 | 0.26 / 0.26 / -0.31 | 0.10 | -0.03 | 0.95 | -0.06 | 1.00 | 708 | NO |
| BTC 8 | OR30 5m with exit=tr0.2xADR | 505 | 2 | 1.26 | 1.70 | 0.85 | 0.32 / 0.62 | 0.21 / 0.11 / -0.30 | 0.05 | 0.04 | 1.00 | -0.09 | 0.25 | 787 | NO |
| BTC 9 | OR30 15m with exit=b20.3xADR | 501 | 2 | 1.22 | 1.89 | 0.77 | 0.08 / 0.87 | 0.19 / 0.24 / -0.42 | 0.04 | -0.21 | 0.91 | -0.12 | 0.50 | 777 | NO |
| BTC 10 | PD 5m with exit=tr0.1xADR | 347 | 2 | 1.15 | 0.56 | 1.39 | 1.66 / 1.17 | 0.20 / 0.59 / 0.08 | 0.15 | 0.37 | 0.99 | 0.03 | 0.50 | 560 | LEAD |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 54 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 3 / 4 / 3 |
| all-in uplift @20% > 0 (all scored) | 39 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 29 |
| worst-decile corr <= +0.30 | 52 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC PD 5m with exit=tr0.1xADR | clean | 1.25 | 2.30 | -109346 | -90941 | 324359 | -135327 | 3.54 | 48.6 | 1.66 | -91651 | 260431 | -99275 |
| BTC PD 5m with exit=tr0.1xADR | H1 | 2.09 | 4.17 | -117425 | -108594 | 268192 | -128504 | 2.28 | 39.3 | 3.42 | -73734 | 153992 | -77958 |
| BTC PD 5m with exit=tr0.1xADR | H2 | 1.22 | 2.15 | -71059 | -61539 | 168041 | -87207 | 1.62 | 44.4 | 2.37 | -88325 | 210289 | -91253 |
| BTC PD 5m with exit=tr0.1xADR | all | 1.39 | 2.62 | -109759 | -89857 | 324359 | -135327 | 6.26 | 46.4 | 2.07 | -89825 | 260431 | -99275 |
| CL OR15 15m fade exit=hd0.2xADR | clean | 0.89 | 1.54 | -93152 | -81099 | 309540 | -118323 | 2.62 | 51.4 | 1.67 | -89622 | 307396 | -100673 |
| CL OR15 15m fade exit=hd0.2xADR | H1 | 1.33 | 2.15 | -59292 | -55107 | 177002 | -67606 | 1.13 | 42.9 | 2.99 | -80547 | 139987 | -87479 |
| CL OR15 15m fade exit=hd0.2xADR | H2 | 1.15 | 2.64 | -145637 | -128387 | 545973 | -165358 | 1.53 | 52.8 | 2.64 | -91023 | 201372 | -102330 |
| CL OR15 15m fade exit=hd0.2xADR | all | 0.94 | 1.88 | -116573 | -100701 | 545973 | -165358 | 3.38 | 50.0 | 2.10 | -89896 | 307396 | -102330 |
| ES PD 15m fade exit=b20.2xADR | clean | 1.35 | 2.33 | -105380 | -92206 | 339040 | -153489 | 3.62 | 42.9 | 1.69 | -88560 | 283364 | -97819 |
| ES PD 15m fade exit=b20.2xADR | H1 | -0.39 | -0.51 | -154372 | -136175 | 540619 | -174827 | -0.19 | 53.6 | 2.53 | -76676 | 173099 | -85694 |
| ES PD 15m fade exit=b20.2xADR | H2 | 0.91 | 2.03 | -127695 | -108236 | 401989 | -147300 | 1.27 | 61.1 | 2.53 | -93446 | 214741 | -99190 |
| ES PD 15m fade exit=b20.2xADR | all | 0.92 | 1.64 | -124548 | -105808 | 582873 | -174827 | 2.80 | 48.2 | 2.02 | -89330 | 283364 | -99190 |
| GC OR60 5m fade exit=hd0.1xADR | clean | 0.78 | 1.74 | -69267 | -62001 | 632442 | -100624 | 1.13 | 58.1 | 1.60 | -83756 | 264811 | -90759 |
| GC OR60 5m fade exit=hd0.1xADR | H1 | 1.31 | 5.62 | -123578 | -112790 | 425347 | -153593 | 2.45 | 57.1 | 3.32 | -82701 | 152829 | -95175 |
| GC OR60 5m fade exit=hd0.1xADR | H2 | 0.66 | 1.58 | -210842 | -190299 | 754645 | -217835 | 0.86 | 55.6 | 2.38 | -90548 | 243882 | -94889 |
| GC OR60 5m fade exit=hd0.1xADR | all | 0.78 | 2.14 | -155296 | -123556 | 754645 | -217835 | 3.19 | 57.7 | 2.07 | -86534 | 264811 | -95175 |
| RTY OR30 15m with exit=hd0.3xADR | clean | 0.10 | 0.14 | -118238 | -102036 | 590637 | -145586 | 0.15 | 50.5 | 1.45 | -91521 | 305303 | -101447 |
| RTY OR30 15m with exit=hd0.3xADR | H1 | 1.74 | 3.81 | -90644 | -85505 | 217585 | -99844 | 2.52 | 42.9 | 3.30 | -77884 | 150620 | -79500 |
| RTY OR30 15m with exit=hd0.3xADR | H2 | -1.22 | -1.51 | -169989 | -153455 | 734609 | -177573 | -0.64 | 61.1 | 1.98 | -89135 | 230430 | -89570 |
| RTY OR30 15m with exit=hd0.3xADR | all | 0.10 | 0.15 | -137052 | -114670 | 734609 | -177573 | 0.23 | 51.8 | 1.84 | -90050 | 305303 | -101447 |
| YM PD 15m fade exit=tr0.3xADR | clean | 1.10 | 2.16 | -80940 | -74120 | 300316 | -91744 | 3.32 | 50.5 | 1.61 | -81249 | 285409 | -89849 |
| YM PD 15m fade exit=tr0.3xADR | H1 | 0.55 | 1.04 | -100165 | -86075 | 438775 | -114638 | 0.36 | 57.1 | 2.78 | -94863 | 172765 | -101215 |
| YM PD 15m fade exit=tr0.3xADR | H2 | -0.10 | -0.15 | -121356 | -98764 | 455342 | -121676 | -0.07 | 55.6 | 2.16 | -93033 | 232201 | -96016 |
| YM PD 15m fade exit=tr0.3xADR | all | 0.73 | 1.33 | -95646 | -83224 | 732105 | -121676 | 1.53 | 53.0 | 1.92 | -87235 | 285409 | -101215 |
| ZN OR30 5m fade exit=hd0.3xADR (diag) | clean | -1.09 | -1.53 | -105293 | -94157 | 1146398 | -133704 | -0.86 | 61.9 | 1.26 | -87594 | 254873 | -94327 |
| ZN OR30 5m fade exit=hd0.3xADR (diag) | H1 | -3.20 | -3.69 | -71450 | -67237 | 504763 | -83566 | -0.93 | 85.7 | 2.33 | -76260 | 159170 | -81717 |
| ZN OR30 5m fade exit=hd0.3xADR (diag) | H2 | -2.40 | -2.67 | -104685 | -92242 | 587460 | -115546 | -0.95 | 61.1 | 1.95 | -81141 | 203174 | -86691 |
| ZN OR30 5m fade exit=hd0.3xADR (diag) | all | -1.55 | -2.05 | -103121 | -92054 | 2125477 | -133704 | -0.95 | 66.1 | 1.59 | -85881 | 254873 | -94327 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES PD 15m fade exit=b20.2xADR | -11.8 | -3.1 | 7.9 | 26.0 | -4.0 / 9.3 | 15.8 / 19.8 | NO |
| RTY OR30 15m with exit=hd0.3xADR | -28.1 | -7.0 | 7.6 | 16.5 | -7.8 / 3.3 | 27.7 / 29.5 | NO |
| GC OR60 5m fade exit=hd0.1xADR | -3.1 | 1.6 | 11.3 | 30.2 | 8.9 / 19.4 | -3.7 / 18.0 | NO |
| CL OR15 15m fade exit=hd0.2xADR | -9.4 | -11.2 | 8.6 | 13.2 | -9.2 / 9.0 | 12.4 / 24.3 | NO |
| ZN OR30 5m fade exit=hd0.3xADR (diag) | -52.5 | 3.2 | 14.5 | 26.4 | 2.5 / 11.4 | 23.4 / 32.6 | NO |
| YM PD 15m fade exit=tr0.3xADR | -17.5 | -8.1 | 11.7 | 24.9 | 10.6 / 22.1 | -13.9 / -3.3 | NO |
| BTC PD 5m with exit=tr0.1xADR | -7.3 | -3.0 | 8.0 | 37.6 | -3.8 / 3.1 | 30.6 / 37.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 PD 15m fade exit=b20.2xADR | negative pre-2023 | 1895 | -18.8 | -45.1 | -32.5 | 26.3 | -0.41 / -0.98 / -0.70 | 102.9 / 77.1 |
| ES 2 PD 15m fade exit=hd0.2xADR | negative pre-2023 | 1895 | -33.0 | -62.4 | -48.3 | 29.4 | -0.61 / -1.14 / -0.88 | 173.6 / 144.2 |
| ES 3 OR15 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2680 | 20.1 | -7.2 | 6.0 | 27.3 | 0.42 / -0.14 / 0.13 | 123.1 / 96.2 |
| ES 4 OR15 15m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2663 | 15.3 | -12.1 | 1.2 | 27.4 | 0.32 / -0.24 / 0.03 | 107.2 / 80.0 |
| ES 5 OR15 15m with exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2663 | 23.6 | -2.5 | 10.2 | 26.1 | 0.64 / -0.06 / 0.28 | 90.7 / 65.0 |
| ES 6 OR15 5m with exit=b10.3xADR | negative pre-2023 | 2680 | -0.3 | -24.6 | -12.8 | 24.4 | -0.00 / -0.59 / -0.31 | 83.0 / 59.3 |
| ES 7 PD 15m fade exit=hd0.3xADR | negative pre-2023 | 1895 | -12.3 | -41.6 | -27.5 | 29.4 | -0.20 / -0.66 / -0.44 | 161.4 / 132.0 |
| ES 8 PD 15m fade exit=b10.2xADR | negative pre-2023 | 1895 | -17.6 | -41.4 | -29.9 | 23.9 | -0.55 / -1.28 / -0.93 | 66.3 / 43.3 |
| ES 9 PD 5m fade exit=hd0.3xADR | negative pre-2023 | 1981 | -17.1 | -46.4 | -32.2 | 29.4 | -0.25 / -0.68 / -0.47 | 125.9 / 96.5 |
| ES 10 PD 5m fade exit=hd0.2xADR | negative pre-2023 | 1981 | -32.0 | -61.3 | -47.1 | 29.4 | -0.55 / -1.05 / -0.81 | 112.4 / 83.0 |
| RTY 1 PD 5m fade exit=hd0.3xADR | negative pre-2023 | 1183 | -0.4 | -14.7 | -12.5 | 14.4 | 0.00 / -0.26 / -0.22 | 45.9 / 31.5 |
| RTY 2 PD 5m fade exit=b20.3xADR | negative pre-2023 | 1183 | -7.0 | -20.6 | -18.5 | 13.5 | -0.13 / -0.39 / -0.35 | 36.5 / 23.0 |
| RTY 3 OR30 5m fade exit=hd0.1xADR | negative pre-2023 | 1491 | -4.6 | -18.9 | -16.7 | 14.4 | -0.13 / -0.57 / -0.50 | 32.9 / 18.5 |
| RTY 4 OR30 15m with exit=hd0.3xADR | positive pre-2023 | 1459 | 15.3 | 1.0 | 3.2 | 14.4 | 0.36 / 0.02 / 0.08 | 18.5 / 4.1 |
| RTY 5 (diag) PD 15m fade exit=b20.3xADR | negative pre-2023 | 1123 | -1.0 | -14.6 | -12.4 | 13.5 | -0.01 / -0.27 / -0.23 | 66.6 / 53.1 |
| RTY 6 (diag) PD 15m fade exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 1123 | 5.8 | -8.6 | -6.3 | 14.4 | 0.11 / -0.15 / -0.11 | 88.2 / 73.8 |
| RTY 7 (diag) PD 15m fade exit=tr0.3xADR | negative pre-2023 | 1123 | -11.6 | -26.0 | -23.7 | 14.4 | -0.29 / -0.65 / -0.59 | 53.2 / 38.8 |
| GC 1 PD 5m with exit=tr0.1xADR | gross-positive, cost-negative pre-2023 | 1843 | 10.8 | -13.5 | -3.8 | 24.4 | 0.60 / -0.74 / -0.21 | 77.8 / 53.5 |
| GC 2 OR30 15m fade exit=hd0.1xADR | gross-positive, cost-negative pre-2023 | 2550 | 4.3 | -20.1 | -10.3 | 24.4 | 0.14 / -0.63 / -0.32 | 90.5 / 66.1 |
| GC 3 PD 5m with exit=b10.1xADR | gross-positive, cost-negative pre-2023 | 1843 | 7.5 | -11.6 | -4.0 | 19.2 | 0.46 / -0.70 / -0.25 | 50.4 / 31.7 |
| GC 4 PD 5m with exit=b20.2xADR | negative pre-2023 | 1843 | -11.5 | -33.4 | -24.7 | 21.9 | -0.28 / -0.79 / -0.58 | 102.3 / 80.9 |
| GC 5 OR60 5m fade exit=hd0.1xADR | negative pre-2023 | 2461 | -3.7 | -28.1 | -18.4 | 24.4 | -0.11 / -0.87 / -0.57 | 79.5 / 55.1 |
| GC 6 OR60 5m fade exit=tr0.3xADR | negative pre-2023 | 2461 | -14.3 | -38.6 | -28.9 | 24.4 | -0.38 / -1.05 / -0.78 | 61.4 / 37.0 |
| GC 7 OR30 15m fade exit=tr0.3xADR | negative pre-2023 | 2550 | -6.9 | -31.3 | -21.5 | 24.4 | -0.17 / -0.79 / -0.54 | 52.0 / 27.6 |
| GC 8 OR60 5m fade exit=b10.3xADR | negative pre-2023 | 2461 | -13.1 | -34.4 | -25.9 | 21.3 | -0.36 / -0.94 / -0.71 | 45.1 / 24.1 |
| GC 9 OR60 5m fade exit=b20.2xADR | negative pre-2023 | 2461 | -1.3 | -23.8 | -14.8 | 22.5 | -0.03 / -0.67 / -0.42 | 52.4 / 30.0 |
| GC 10 OR60 15m fade exit=b20.1xADR | negative pre-2023 | 2369 | -13.5 | -35.1 | -26.5 | 21.6 | -0.66 / -1.70 / -1.29 | 30.1 / 9.0 |
| CL 1 OR15 5m fade exit=hd0.1xADR | negative pre-2023 | 2680 | -8.7 | -33.1 | -30.4 | 24.4 | -0.28 / -1.03 / -0.95 | 59.2 / 34.9 |
| CL 2 OR15 15m fade exit=hd0.2xADR | negative pre-2023 | 2670 | -33.4 | -57.8 | -55.1 | 24.4 | -0.75 / -1.30 / -1.24 | 65.1 / 40.8 |
| CL 3 OR30 5m fade exit=hd0.2xADR | negative pre-2023 | 2665 | -6.8 | -31.2 | -28.5 | 24.4 | -0.17 / -0.75 / -0.69 | 55.4 / 31.0 |
| CL 4 OR15 15m fade exit=hd0.3xADR | negative pre-2023 | 2670 | -45.9 | -70.3 | -67.6 | 24.4 | -0.92 / -1.41 / -1.36 | 64.3 / 39.9 |
| CL 5 OR15 5m fade exit=hd0.3xADR | negative pre-2023 | 2680 | -16.8 | -41.2 | -38.5 | 24.4 | -0.33 / -0.81 / -0.76 | 64.0 / 39.6 |
| CL 6 OR15 5m fade exit=hd0.2xADR | negative pre-2023 | 2680 | -11.9 | -36.3 | -33.6 | 24.4 | -0.27 / -0.82 / -0.76 | 57.6 / 33.2 |
| CL 7 OR30 5m fade exit=hd0.1xADR | negative pre-2023 | 2665 | -8.3 | -32.7 | -30.0 | 24.4 | -0.26 / -0.99 / -0.91 | 47.7 / 23.4 |
| CL 8 OR30 5m fade exit=tr0.3xADR | negative pre-2023 | 2665 | -1.3 | -25.7 | -23.0 | 24.4 | -0.03 / -0.63 / -0.56 | 52.1 / 27.7 |
| CL 9 OR15 15m fade exit=b10.3xADR | negative pre-2023 | 2670 | -33.0 | -53.4 | -51.2 | 20.4 | -0.86 / -1.38 / -1.32 | 43.4 / 23.4 |
| CL 10 OR15 15m fade exit=hd0.1xADR | negative pre-2023 | 2670 | -23.4 | -47.8 | -45.2 | 24.4 | -0.69 / -1.41 / -1.33 | 47.1 / 22.8 |
| ZN 1 (diag) OR30 5m fade exit=hd0.3xADR | negative pre-2023 | 2622 | -0.2 | -35.8 | -40.9 | 35.6 | -0.01 / -2.54 / -2.90 | 17.5 / -18.1 |
| ZN 2 (diag) OR15 15m fade exit=hd0.3xADR | negative pre-2023 | 2643 | -3.5 | -39.1 | -44.2 | 35.6 | -0.24 / -2.74 / -3.10 | 15.7 / -19.9 |
| ZN 3 (diag) OR30 5m fade exit=b20.3xADR | negative pre-2023 | 2622 | -0.2 | -33.8 | -38.6 | 33.6 | -0.01 / -2.61 / -2.98 | 12.5 / -20.7 |
| YM 1 PD 15m fade exit=hd0.2xADR | positive pre-2023 | 1885 | 21.1 | 6.7 | 12.5 | 14.4 | 0.38 / 0.12 / 0.22 | 108.6 / 94.3 |
| YM 2 OR30 15m with exit=b20.1xADR | gross-positive, cost-negative pre-2023 | 2550 | 2.9 | -9.9 | -4.8 | 12.7 | 0.16 / -0.54 / -0.27 | 42.7 / 30.3 |
| YM 3 PD 15m fade exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 1885 | 8.6 | -5.8 | -0.0 | 14.4 | 0.20 / -0.13 / -0.00 | 69.2 / 54.9 |
| YM 4 PD 15m fade exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 1885 | 10.6 | -2.5 | 2.8 | 13.1 | 0.28 / -0.06 / 0.07 | 64.3 / 51.6 |
| YM 5 OR30 15m with exit=b10.2xADR | gross-positive, cost-negative pre-2023 | 2550 | 0.1 | -11.9 | -7.1 | 12.1 | 0.01 / -0.48 / -0.29 | 41.5 / 29.7 |
| YM 6 OR60 15m with exit=b10.1xADR | gross-positive, cost-negative pre-2023 | 2349 | 3.4 | -8.5 | -3.8 | 11.9 | 0.24 / -0.61 / -0.27 | 27.7 / 16.1 |
| YM 7 PD 15m fade exit=hd0.3xADR | positive pre-2023 | 1885 | 22.1 | 7.7 | 13.5 | 14.4 | 0.37 / 0.13 / 0.23 | 84.0 / 69.7 |
| YM 8 OR15 15m with exit=b10.3xADR | negative pre-2023 | 2650 | -11.6 | -24.1 | -19.1 | 12.5 | -0.33 / -0.69 / -0.55 | 49.0 / 36.9 |
| YM 9 OR30 15m with exit=b10.3xADR | negative pre-2023 | 2550 | -0.4 | -13.0 | -8.0 | 12.5 | -0.01 / -0.38 / -0.24 | 49.5 / 37.2 |
| YM 10 OR15 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2673 | 10.6 | -3.0 | 2.5 | 13.6 | 0.26 / -0.07 / 0.06 | 58.6 / 45.2 |
| BTC 1 OR30 5m with exit=b10.1xADR | positive pre-2023 | 367 | 61.0 | 20.0 | 44.3 | 40.9 | 1.19 / 0.37 / 0.85 | 226.8 / 186.3 |
| BTC 2 OR30 5m with exit=b20.2xADR | positive pre-2023 | 367 | 254.3 | 206.0 | 234.8 | 48.3 | 2.36 / 1.90 / 2.18 | 421.5 / 373.8 |
| BTC 3 OR30 5m with exit=b10.2xADR | positive pre-2023 | 367 | 118.6 | 76.0 | 101.4 | 42.6 | 1.47 / 0.92 / 1.25 | 332.1 / 290.0 |
| BTC 4 OR30 15m with exit=b10.1xADR | gross-positive, cost-negative pre-2023 | 358 | 21.2 | -20.6 | 4.3 | 41.7 | 0.43 / -0.46 / 0.07 | 182.2 / 141.7 |
| BTC 5 OR30 5m with exit=tr0.1xADR | positive pre-2023 | 367 | 106.4 | 52.0 | 84.3 | 54.4 | 1.58 / 0.77 / 1.26 | 190.6 / 136.3 |
| BTC 6 OR30 5m with exit=hd0.2xADR | positive pre-2023 | 367 | 430.3 | 375.9 | 408.2 | 54.4 | 2.93 / 2.57 / 2.79 | 410.8 / 356.4 |
| BTC 7 OR60 15m with exit=b10.3xADR | positive pre-2023 | 323 | 165.1 | 118.9 | 146.2 | 46.2 | 1.54 / 1.10 / 1.36 | 347.9 / 302.8 |
| BTC 8 OR30 5m with exit=tr0.2xADR | positive pre-2023 | 367 | 206.5 | 152.2 | 184.4 | 54.4 | 2.30 / 1.70 / 2.06 | 278.7 / 224.3 |
| BTC 9 OR30 15m with exit=b20.3xADR | positive pre-2023 | 358 | 301.5 | 250.6 | 280.9 | 50.9 | 2.28 / 1.89 / 2.13 | 410.1 / 359.5 |
| BTC 10 PD 5m with exit=tr0.1xADR | positive pre-2023 | 243 | 92.9 | 38.6 | 70.9 | 54.4 | 1.29 / 0.56 / 1.00 | 233.6 / 179.2 |


## 6b. Replication tests (leads only)
CL 2 (cell 46): (b) H0 standalone -0.99 on 128 trades fails; (c) ES -0.19, RTY -0.11 fails; (d) odd +0.22 / even +0.19 vs +0.25 holds: 1 of 4. CL 4 (cell 47): (b) -0.18 fails; (c) ES -0.20, RTY -0.05 fails; (d) +0.22/+0.16 vs +0.23 holds: 1 of 4. BTC 10 (cell 150): (b) -0.88 fails; (c) fails; (d) holds: 1 of 4. None replicated. Files outputs/autopilot/b/b11_co/repl_*.json.


## 6. What this says
- **Opening-range / prior-day-level breakouts add nothing that survives.** The clean rule finds structure beyond chance by count on ES (p(count) = 0.03), CL (0.00), YM and BTC (0.00) but the top-cell means are at chance (p(top) 0.07-0.80) and ZN has no qualifying cell. In H1/H2 only 3 non-diagnostic cells (all CL) have +0.10 on all three spans at 20% share.
- **CL OR15 15-minute FADE (first close beyond the 09:00-09:15 ET opening range, trade against it, stop 0.2-0.3 x ADR20, hold to 16:55)** - cells CL 2 (0.2 ADR), CL 4 (0.3 ADR), CL 9 (1R bracket 0.3 ADR): uplift at 20% +0.21 / +0.16 / +0.34, +0.16 / +0.39 / +0.28, +0.14 / +0.23 / +0.21 (clean / H1 / H2); out-of-selection (H1+H2) standalone Sharpe 1.04 for CL 2 against a null p95 of 0.78; 2x slippage all-in uplift +0.16/+0.15/+0.09; worst-decile correlation +0.11/+0.14/+0.04. They fail: worst week (CL 2 at 20% share worsens the pair's worst week by 24%, above the 20% allowance), the plateau (0.25, 0.00, 0.00), bootstrap (lower bound +0.003, -0.006, -0.093) and replication (CL 2: H0 2023-02..07 standalone -0.99 fails, ES -0.19 / RTY -0.11 fail, alternating months hold: 1 of 4; CL 4: H0 -0.18, ES/RTY fail, alternating months hold: 1 of 4, not replicated). ERA flag 'negative pre-2023' (2013-22/2017-22 net weekly Sharpe -1.3 for CL 2, gross -$33 per trade at 1 contract), which fits an old-vs-new structure story but is not a gate. A LEAD at gate 3 only, not a candidate.
- BTC 10 (prior-day high/low breakout with-trend, 5-minute, 0.1 ADR trail): +0.20 / +0.59 / +0.08 at 20% - H2 below +0.10, H0 fails (-0.88), ES/RTY fail: NO.
- ERA flags over 54 cells: 29 'negative pre-2023', 13 'gross-positive, cost-negative pre-2023', 12 'positive pre-2023'.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b11.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b11/ (`B11_CO_all_selected_scored.csv`).

DONE B11
