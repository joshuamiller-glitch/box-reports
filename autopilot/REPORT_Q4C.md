# REPORT Q4C - Q4C: B11 grid on metals/energy (SI, HG, PL, HO, RB, NG)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 48 selected cells (+5 diagnostic) scored on 6 instruments; best non-diagnostic all-in additive uplift at 20% share +0.31; best pair-window standalone Sharpe +0.96.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: SI, HG, PL, HO, RB, NG. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HG    |     192 |        192 |         0 |               0.682 |                1 |          0 |            3 |
| HO    |     192 |        192 |        44 |               1.737 |                2 |         10 |            0 |
| NG    |     192 |        192 |        11 |               1.161 |                2 |         10 |            0 |
| PL    |     192 |        192 |        15 |               1.027 |                2 |         10 |            0 |
| RB    |     192 |        192 |        43 |               1.661 |                2 |         10 |            0 |
| SI    |     192 |        192 |         8 |               1.046 |                2 |          8 |            2 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SI    |     100 |                    8 |             7.6  |              15 |       0.48 |                       0.523 |            0.604 |           0.839 |     0.73 |       0.963 |                1.62  |
| HG    |     100 |                    0 |             8.84 |              15 |       1    |                     nan     |            0.581 |           0.777 |   nan    |     nan     |                1.524 |
| PL    |     100 |                   15 |             8.76 |              15 |       0.04 |                       0.712 |            0.581 |           0.812 |     0.17 |       1.027 |                1.611 |
| HO    |     100 |                   44 |            30.43 |              43 |       0    |                       1.265 |            1.099 |           1.277 |     0.06 |       1.737 |                1.999 |
| RB    |     100 |                   43 |            23.04 |              35 |       0    |                       1.338 |            1.01  |           1.244 |     0.01 |       1.661 |                2.011 |
| NG    |     100 |                   11 |             7.63 |              15 |       0.12 |                       0.717 |            0.56  |           0.769 |     0.12 |       1.161 |                1.543 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI 1 | OR15 15m fade exit=tr0.3xADR | 514 | 2 | 0.96 | -1.65 | 0.96 | 1.28 / 1.20 | 0.16 / 0.10 / 0.61 | 0.18 | -0.40 | 1.00 | -0.17 | 0.50 | 821 | LEAD |
| SI 2 | OR60 5m with exit=hd0.3xADR | 482 | 2 | 0.89 | -0.59 | 0.31 | 0.23 / 1.20 | 0.04 / -0.64 / -0.28 | -0.22 | 0.07 | 0.81 | -0.55 | 0.00 | 782 | NO |
| SI 3 | OR15 15m fade exit=b20.3xADR | 514 | 2 | 0.58 | -1.22 | 0.39 | 0.45 / 1.27 | 0.12 / -0.76 / 0.02 | -0.11 | -0.09 | 0.86 | -0.58 | 0.00 | 821 | NO |
| SI 4 | PD 5m with exit=b10.2xADR | 374 | 2 | 0.55 | -1.18 | 0.76 | 1.10 / 1.40 | 0.04 / -0.16 / 0.24 | -0.01 | 0.38 | 0.96 | -0.38 | 1.00 | 593 | NO |
| SI 5 | OR60 5m with exit=hd0.2xADR | 482 | 2 | 0.52 | -0.73 | 0.60 | 0.84 / 0.83 | -0.01 / 0.25 / -0.14 | -0.10 | -0.09 | 0.97 | -0.37 | 0.25 | 782 | NO |
| SI 6 | OR15 15m fade exit=b10.3xADR | 514 | 2 | 0.39 | -1.49 | 0.58 | 0.80 / 1.34 | 0.07 / -0.86 / 0.35 | -0.08 | -0.38 | 0.90 | -0.46 | 1.00 | 821 | NO |
| SI 7 | PD 5m with exit=b10.3xADR | 374 | 2 | 0.16 | -1.28 | 0.56 | 0.91 / 1.44 | 0.01 / 0.40 / -0.18 | -0.06 | 0.58 | 0.89 | -0.44 | 0.50 | 593 | NO |
| SI 8 | PD 15m with exit=hd0.1xADR | 358 | 2 | 0.14 | -0.84 | 0.41 | 0.62 / 1.17 | -0.04 / 0.16 / -0.55 | -0.23 | 0.59 | 0.91 | -0.56 | 0.00 | 573 | NO |
| SI 9 (diag) | OR60 5m with exit=b10.3xADR | 482 | 1 | 1.05 | -1.08 | 0.92 | 1.19 / 1.14 | 0.10 / 0.58 / 0.27 | 0.13 | -0.54 | 0.97 | -0.17 | 0.00 | 782 | diag |
| SI 10 (diag) | OR60 5m with exit=b20.3xADR | 482 | 1 | 0.78 | -0.76 | 0.53 | 0.65 / 1.15 | 0.04 / 0.35 / -0.39 | -0.10 | 0.12 | 0.95 | -0.45 | 0.25 | 782 | diag |
| HG 1 (diag) | OR60 5m with exit=b10.2xADR | 500 | 1 | 0.68 | -0.84 | -0.34 | -1.70 / 0.81 | 0.09 / -0.40 / -0.62 | -0.25 | -0.05 | 0.75 | -0.36 | 0.00 | 799 | diag |
| HG 2 (diag) | OR15 15m with exit=b10.2xADR | 515 | 1 | 0.49 | -1.29 | -0.06 | -1.03 / 1.16 | 0.08 / 0.05 / -0.62 | -0.21 | -0.07 | 0.89 | -0.31 | 0.00 | 824 | diag |
| HG 3 (diag) | PD 15m fade exit=tr0.3xADR | 358 | 1 | 0.49 | -0.53 | 0.19 | -0.45 / 0.59 | 0.09 / -0.30 / -0.17 | -0.09 | -0.33 | 0.88 | -0.20 | 0.00 | 552 | diag |
| PL 1 | OR30 15m with exit=b10.3xADR | 505 | 2 | 1.03 | -0.42 | 0.25 | -0.15 / 1.11 | 0.13 / 0.18 / -1.29 | -0.23 | 0.35 | 0.82 | -0.56 | 0.00 | 807 | NO |
| PL 2 | OR30 15m with exit=hd0.3xADR | 505 | 2 | 1.00 | -0.75 | 0.11 | -0.48 / 1.00 | 0.17 / -0.66 / -1.04 | -0.29 | 0.28 | 0.81 | -0.64 | 0.00 | 807 | NO |
| PL 3 | OR30 15m with exit=b20.3xADR | 505 | 2 | 0.97 | -0.59 | 0.21 | -0.18 / 1.08 | 0.12 / -0.32 / -1.08 | -0.27 | 0.23 | 0.80 | -0.62 | 0.00 | 807 | NO |
| PL 4 | OR30 15m with exit=hd0.2xADR | 505 | 2 | 0.72 | -0.75 | 0.03 | -0.55 / 0.55 | 0.14 / -0.48 / -1.11 | -0.30 | 0.16 | 0.88 | -0.58 | 0.00 | 807 | NO |
| PL 5 | PD 5m with exit=hd0.3xADR | 406 | 2 | 0.59 | -0.84 | -0.10 | -0.50 / 1.11 | 0.06 / 0.07 / -1.06 | -0.28 | 0.28 | 0.61 | -0.65 | 0.00 | 623 | NO |
| PL 6 | PD 15m with exit=hd0.3xADR | 390 | 2 | 0.58 | -0.81 | -0.05 | -0.52 / 0.88 | 0.08 / 0.20 / -0.83 | -0.21 | 0.21 | 0.64 | -0.53 | 0.00 | 598 | NO |
| PL 7 | OR60 15m with exit=hd0.3xADR | 478 | 2 | 0.57 | -0.86 | -0.31 | -1.10 / 1.04 | 0.10 / -1.11 / -1.12 | -0.45 | 0.04 | 0.52 | -0.76 | 0.00 | 772 | NO |
| PL 8 | OR30 15m with exit=b20.2xADR | 505 | 2 | 0.56 | -0.47 | 0.07 | -0.24 / 0.84 | 0.05 / -0.12 / -1.12 | -0.28 | 0.23 | 0.83 | -0.57 | 0.00 | 807 | NO |
| PL 9 | OR60 5m with exit=hd0.3xADR | 495 | 2 | 0.56 | -0.83 | -0.26 | -0.98 / 1.14 | 0.09 / -0.50 / -1.36 | -0.41 | 0.36 | 0.57 | -0.72 | 0.00 | 796 | NO |
| PL 10 | OR60 5m with exit=b20.3xADR | 495 | 2 | 0.54 | -0.67 | -0.06 | -0.48 / 0.87 | 0.05 / 0.02 / -1.32 | -0.35 | 0.35 | 0.71 | -0.68 | 0.00 | 796 | NO |
| HO 1 | PD 15m fade exit=b20.2xADR | 393 | 2 | 1.74 | -0.18 | 0.46 | -0.57 / 1.40 | 0.31 / -0.78 / 0.00 | 0.07 | -0.08 | 0.82 | -0.17 | 0.00 | 617 | NO |
| HO 2 | PD 15m fade exit=b10.2xADR | 393 | 2 | 1.51 | -0.27 | -0.37 | -1.96 / 1.39 | 0.27 / -0.65 / -0.94 | -0.17 | 0.12 | 0.37 | -0.41 | 0.00 | 617 | NO |
| HO 3 | PD 15m fade exit=hd0.2xADR | 393 | 2 | 1.36 | -0.40 | 0.75 | 0.40 / 1.17 | 0.24 / -0.67 / 0.29 | 0.11 | -0.13 | 0.94 | -0.12 | 0.50 | 617 | NO |
| HO 4 | PD 5m fade exit=b10.2xADR | 409 | 2 | 1.30 | -0.52 | -0.18 | -1.30 / 1.29 | 0.23 / -0.85 / -0.58 | -0.15 | 0.45 | 0.46 | -0.40 | 0.00 | 639 | NO |
| HO 5 | PD 5m fade exit=hd0.3xADR | 409 | 2 | 1.25 | -0.32 | 0.43 | -0.42 / 1.50 | 0.22 / -0.41 / -0.30 | -0.01 | 0.36 | 0.83 | -0.20 | 1.00 | 639 | NO |
| HO 6 | PD 15m fade exit=tr0.3xADR | 393 | 2 | 1.15 | -0.37 | 0.60 | 0.23 / 1.41 | 0.19 / -0.57 / 0.23 | 0.07 | 0.07 | 0.83 | -0.17 | 1.00 | 617 | NO |
| HO 7 | PD 5m fade exit=hd0.2xADR | 409 | 2 | 1.13 | -0.42 | 0.66 | 0.18 / 1.10 | 0.19 / -0.52 / 0.11 | 0.06 | 0.20 | 0.95 | -0.13 | 0.50 | 639 | NO |
| HO 8 | PD 5m fade exit=tr0.3xADR | 409 | 2 | 1.10 | -0.32 | 0.42 | -0.10 / 1.69 | 0.21 / -0.70 / 0.02 | 0.02 | 0.43 | 0.80 | -0.21 | 1.00 | 639 | NO |
| HO 9 | PD 5m fade exit=b10.3xADR | 409 | 2 | 1.10 | -0.38 | -0.14 | -1.19 / 1.51 | 0.18 / -0.41 / -0.75 | -0.15 | 0.39 | 0.42 | -0.39 | 0.00 | 639 | NO |
| HO 10 | PD 15m fade exit=b20.1xADR | 393 | 2 | 1.02 | -0.26 | -0.18 | -1.18 / 1.35 | 0.23 / -0.60 / -0.64 | -0.13 | 0.29 | 0.44 | -0.35 | 0.00 | 617 | NO |
| RB 1 | OR30 15m fade exit=hd0.3xADR | 517 | 2 | 1.66 | -0.27 | 0.81 | -0.12 / 1.42 | 0.30 / -0.05 / 0.07 | 0.17 | -0.06 | 0.98 | -0.03 | 0.75 | 827 | NO |
| RB 2 | OR30 5m fade exit=hd0.3xADR | 517 | 2 | 1.43 | 0.01 | 0.35 | -0.85 / 1.48 | 0.26 / -0.12 / -0.12 | 0.09 | -0.04 | 0.83 | -0.11 | 0.75 | 827 | NO |
| RB 3 | PD 5m fade exit=tr0.1xADR | 408 | 2 | 1.40 | -0.65 | 0.95 | 0.45 / 1.00 | 0.20 / 0.11 / -0.17 | 0.03 | -0.04 | 0.98 | -0.08 | 0.50 | 632 | NO |
| RB 4 | PD 5m fade exit=hd0.3xADR | 408 | 2 | 1.35 | -0.11 | 0.15 | -1.15 / 1.24 | 0.21 / -0.11 / -0.41 | 0.00 | -0.17 | 0.73 | -0.19 | 0.00 | 632 | NO |
| RB 5 | PD 5m fade exit=b10.2xADR | 408 | 2 | 1.35 | -0.99 | 0.45 | -0.38 / 1.52 | 0.19 / 0.16 / -0.39 | 0.01 | -0.44 | 0.88 | -0.20 | 0.00 | 632 | NO |
| RB 6 | PD 5m fade exit=hd0.2xADR | 408 | 2 | 1.34 | -0.16 | 0.18 | -1.12 / 1.35 | 0.19 / -0.10 / -0.46 | -0.02 | -0.18 | 0.74 | -0.21 | 0.50 | 632 | NO |
| RB 7 | PD 5m fade exit=tr0.2xADR | 408 | 2 | 1.30 | -0.33 | 0.61 | -0.32 / 1.26 | 0.18 / 0.25 / -0.26 | 0.04 | -0.22 | 0.93 | -0.11 | 0.50 | 632 | NO |
| RB 8 | PD 15m fade exit=tr0.2xADR | 387 | 2 | 1.22 | -0.35 | 0.74 | 0.22 / 1.13 | 0.18 / 0.12 / -0.04 | 0.07 | -0.37 | 0.95 | -0.09 | 0.00 | 604 | NO |
| RB 9 | OR30 15m fade exit=hd0.2xADR | 517 | 2 | 1.17 | -0.15 | 0.50 | -0.29 / 1.04 | 0.20 / -0.23 / 0.09 | 0.09 | 0.18 | 0.86 | -0.09 | 1.00 | 827 | NO |
| RB 10 | OR30 5m fade exit=hd0.2xADR | 517 | 2 | 1.16 | 0.17 | 0.09 | -1.27 / 1.28 | 0.20 / -0.12 / -0.41 | -0.01 | 0.14 | 0.67 | -0.20 | 0.75 | 827 | NO |
| NG 1 | OR15 5m fade exit=hd0.2xADR | 516 | 2 | 1.16 | -0.48 | 0.48 | -0.81 / 0.64 | 0.15 / -0.32 / -0.20 | -0.12 | 0.12 | 1.00 | -0.16 | 0.25 | 826 | NO |
| NG 2 | PD 15m with exit=b20.3xADR | 386 | 2 | 0.98 | -0.21 | -0.08 | -1.83 / 0.98 | 0.20 / -0.71 / -0.38 | -0.14 | -0.27 | 0.74 | -0.25 | 0.00 | 613 | NO |
| NG 3 | PD 5m with exit=b20.3xADR | 407 | 2 | 0.90 | -0.19 | -0.10 | -1.91 / 1.06 | 0.18 / -0.56 / -0.43 | -0.15 | -0.37 | 0.70 | -0.25 | 0.00 | 641 | NO |
| NG 4 | PD 15m with exit=hd0.3xADR | 386 | 2 | 0.78 | -0.24 | 0.05 | -1.11 / 1.27 | 0.17 / -0.46 / -0.33 | -0.12 | -0.14 | 0.80 | -0.22 | 0.00 | 613 | NO |
| NG 5 | OR30 5m fade exit=hd0.2xADR | 513 | 2 | 0.76 | -0.44 | 0.62 | 0.46 / 0.59 | 0.09 / 0.45 / -0.11 | -0.03 | -0.04 | 0.99 | -0.08 | 0.00 | 820 | NO |
| NG 6 | PD 5m with exit=hd0.3xADR | 407 | 2 | 0.72 | -0.19 | 0.08 | -0.97 / 1.16 | 0.15 / -0.27 / -0.36 | -0.11 | -0.31 | 0.80 | -0.21 | 0.00 | 641 | NO |
| NG 7 | PD 15m with exit=b10.3xADR | 386 | 2 | 0.55 | -0.42 | -0.60 | -2.47 / 0.76 | 0.12 / -0.98 / -0.47 | -0.26 | -0.07 | 0.61 | -0.36 | 0.00 | 613 | NO |
| NG 8 | OR15 5m fade exit=tr0.2xADR | 516 | 2 | 0.54 | -0.50 | -0.46 | -2.03 / 0.40 | 0.00 / -0.71 / -0.34 | -0.37 | -0.20 | 0.83 | -0.36 | 0.00 | 826 | NO |
| NG 9 | OR15 5m fade exit=hd0.3xADR | 516 | 2 | 0.42 | -0.47 | 0.06 | -0.55 / 0.69 | 0.01 / -0.10 / -0.25 | -0.18 | -0.09 | 0.90 | -0.24 | 0.00 | 826 | NO |
| NG 10 | OR30 5m fade exit=tr0.2xADR | 513 | 2 | 0.36 | -0.74 | 0.18 | -0.05 / 0.29 | 0.00 / 0.28 / -0.15 | -0.18 | -0.26 | 0.99 | -0.17 | 0.00 | 820 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 48 |
| diagnostic cells read | 5 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 25 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 43 |
| plateau >= 0.75 | 9 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HG PD 15m fade exit=tr0.3xADR (diag) | clean | 0.60 | 1.07 | -96962 | -84369 | 640129 | -131070 | 0.85 | 50.5 | 1.55 | -82059 | 259175 | -103367 |
| HG PD 15m fade exit=tr0.3xADR (diag) | H1 | 0.14 | 0.22 | -137697 | -121693 | 326157 | -145816 | 0.13 | 50.0 | 2.52 | -81889 | 168265 | -96224 |
| HG PD 15m fade exit=tr0.3xADR (diag) | H2 | -1.04 | -1.34 | -110770 | -106039 | 425475 | -114777 | -0.72 | 61.1 | 2.12 | -82008 | 204405 | -83240 |
| HG PD 15m fade exit=tr0.3xADR (diag) | all | 0.19 | 0.30 | -116179 | -101225 | 689335 | -145816 | 0.41 | 53.0 | 1.85 | -84465 | 259175 | -103367 |
| HO PD 15m fade exit=hd0.2xADR | clean | 1.38 | 2.64 | -93473 | -81330 | 397047 | -111014 | 3.15 | 45.7 | 1.70 | -86016 | 237343 | -97916 |
| HO PD 15m fade exit=hd0.2xADR | H1 | -7.49 | -5.33 | -59762 | -58665 | 754962 | -61914 | -0.93 | 85.7 | 2.16 | -88417 | 167427 | -89161 |
| HO PD 15m fade exit=hd0.2xADR | H2 | 1.30 | 3.17 | -212433 | -178669 | 1119094 | -214141 | 1.07 | 52.8 | 2.58 | -96101 | 250522 | -101924 |
| HO PD 15m fade exit=hd0.2xADR | all | 0.75 | 1.65 | -141940 | -114422 | 1119094 | -214141 | 1.57 | 54.2 | 1.99 | -90022 | 250522 | -101924 |
| NG OR30 5m fade exit=hd0.2xADR | clean | 0.70 | 1.23 | -97529 | -85718 | 463905 | -118432 | 1.37 | 48.6 | 1.55 | -87220 | 278607 | -94766 |
| NG OR30 5m fade exit=hd0.2xADR | H1 | 1.37 | 2.55 | -85390 | -78520 | 186209 | -87481 | 1.94 | 42.9 | 3.28 | -79426 | 147353 | -94947 |
| NG OR30 5m fade exit=hd0.2xADR | H2 | -0.71 | -1.08 | -62086 | -58186 | 441319 | -62217 | -0.32 | 58.3 | 2.18 | -85604 | 232698 | -86202 |
| NG OR30 5m fade exit=hd0.2xADR | all | 0.62 | 1.08 | -92650 | -80506 | 463905 | -118432 | 1.85 | 50.0 | 1.94 | -88155 | 278607 | -94947 |
| PL PD 15m with exit=hd0.3xADR | clean | 0.80 | 1.53 | -87876 | -80478 | 807743 | -109266 | 0.98 | 52.4 | 1.54 | -90543 | 295906 | -98861 |
| PL PD 15m with exit=hd0.3xADR | H1 | -0.00 | -0.01 | -461661 | -368575 | 1089615 | -722009 | -0.00 | 57.1 | 3.02 | -67857 | 169030 | -68315 |
| PL PD 15m with exit=hd0.3xADR | H2 | -1.05 | -1.48 | -270825 | -254992 | 1311211 | -275274 | -0.71 | 63.9 | 1.46 | -110608 | 226429 | -123059 |
| PL PD 15m with exit=hd0.3xADR | all | -0.05 | -0.07 | -281213 | -222943 | 1781172 | -722009 | -0.08 | 56.0 | 1.70 | -95498 | 295906 | -123059 |
| RB OR30 15m fade exit=hd0.3xADR | clean | 1.54 | 3.16 | -93122 | -75469 | 364849 | -116730 | 3.85 | 46.7 | 1.76 | -84216 | 287401 | -89695 |
| RB OR30 15m fade exit=hd0.3xADR | H1 | -0.51 | -0.69 | -54408 | -51754 | 299266 | -59910 | -0.22 | 42.9 | 2.78 | -76921 | 153932 | -77486 |
| RB OR30 15m fade exit=hd0.3xADR | H2 | -0.04 | -0.06 | -176451 | -168301 | 525516 | -178852 | -0.04 | 47.2 | 2.37 | -81645 | 193358 | -82598 |
| RB OR30 15m fade exit=hd0.3xADR | all | 0.81 | 1.32 | -141514 | -113873 | 525516 | -178852 | 2.51 | 45.8 | 2.05 | -82897 | 287401 | -89695 |
| SI OR15 15m fade exit=tr0.3xADR | clean | 1.01 | 1.96 | -89258 | -76139 | 444305 | -116398 | 2.05 | 53.3 | 1.62 | -83039 | 270139 | -92009 |
| SI OR15 15m fade exit=tr0.3xADR | H1 | 1.07 | 2.15 | -272908 | -237408 | 934744 | -379139 | 0.89 | 60.7 | 2.93 | -98631 | 214655 | -110214 |
| SI OR15 15m fade exit=tr0.3xADR | H2 | 1.44 | 2.65 | -634957 | -565554 | 1753123 | -698174 | 1.60 | 44.4 | 2.91 | -96364 | 189213 | -118455 |
| SI OR15 15m fade exit=tr0.3xADR | all | 0.96 | 1.79 | -398132 | -275627 | 1753123 | -698174 | 2.59 | 52.4 | 2.16 | -91263 | 270139 | -118455 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SI OR15 15m fade exit=tr0.3xADR | 20.8 | -98.4 | -33.7 | -2.7 | 9.5 / 18.3 | -55.3 / -45.2 | NO |
| HG PD 15m fade exit=tr0.3xADR (diag) | -26.8 | -13.1 | 19.3 | 26.7 | -14.0 / 22.6 | -4.4 / 14.1 | NO |
| PL PD 15m with exit=hd0.3xADR | -31.6 | -64.1 | -17.6 | -4.0 | -5.9 / 6.1 | -73.0 / -31.7 | NO |
| HO PD 15m fade exit=hd0.2xADR | -10.4 | -10.2 | 7.3 | 26.5 | -4.1 / 14.1 | 9.2 / 9.1 | NO |
| RB OR30 15m fade exit=hd0.3xADR | -15.3 | 4.4 | 19.2 | 25.2 | 13.7 / 19.3 | 31.5 / 31.3 | NO |
| NG OR30 5m fade exit=hd0.2xADR | -20.4 | 3.3 | 11.0 | 25.8 | 3.7 / 10.6 | -1.9 / 20.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SI 1 OR15 15m fade exit=tr0.3xADR | negative pre-2023 | 2605 | -16.1 | -70.5 | -51.4 | 54.4 | -0.37 / -1.65 / -1.20 | 121.8 / 67.4 |
| SI 2 OR60 5m with exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 2423 | 23.3 | -31.1 | -12.1 | 54.4 | 0.43 / -0.59 / -0.23 | 117.9 / 63.6 |
| SI 3 OR15 15m fade exit=b20.3xADR | negative pre-2023 | 2605 | -9.4 | -61.2 | -43.1 | 51.8 | -0.18 / -1.22 / -0.86 | 98.6 / 47.8 |
| SI 4 PD 5m with exit=b10.2xADR | negative pre-2023 | 1837 | -3.0 | -45.8 | -30.8 | 42.8 | -0.09 / -1.18 / -0.80 | 70.4 / 28.9 |
| SI 5 OR60 5m with exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2423 | 17.8 | -36.5 | -17.5 | 54.4 | 0.35 / -0.73 / -0.36 | 87.8 / 33.4 |
| SI 6 OR15 15m fade exit=b10.3xADR | negative pre-2023 | 2605 | -16.1 | -61.8 | -45.8 | 45.8 | -0.39 / -1.49 / -1.11 | 76.0 / 31.4 |
| SI 7 PD 5m with exit=b10.3xADR | negative pre-2023 | 1837 | -20.7 | -65.6 | -49.9 | 44.9 | -0.42 / -1.28 / -0.98 | 52.5 / 8.9 |
| SI 8 PD 15m with exit=hd0.1xADR | gross-positive, cost-negative pre-2023 | 1735 | 9.1 | -45.3 | -26.2 | 54.4 | 0.15 / -0.84 / -0.49 | 69.8 / 15.4 |
| SI 9 (diag) OR60 5m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2423 | 5.2 | -41.1 | -24.9 | 46.3 | 0.13 / -1.08 / -0.66 | 105.5 / 60.7 |
| SI 10 (diag) OR60 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2423 | 16.7 | -34.8 | -16.8 | 51.6 | 0.36 / -0.76 / -0.37 | 104.8 / 53.4 |
| HG 1 (diag) OR60 5m with exit=b10.2xADR | gross-positive, cost-negative pre-2023 | 2545 | 6.7 | -17.3 | -10.8 | 24.1 | 0.34 / -0.84 / -0.52 | 50.4 / 26.6 |
| HG 2 (diag) OR15 15m with exit=b10.2xADR | negative pre-2023 | 2675 | -3.8 | -27.6 | -21.2 | 23.8 | -0.18 / -1.29 / -0.99 | 46.2 / 23.1 |
| HG 3 (diag) PD 15m fade exit=tr0.3xADR | gross-positive, cost-negative pre-2023 | 1793 | 10.9 | -18.5 | -10.6 | 29.4 | 0.32 / -0.53 / -0.30 | 62.9 / 33.6 |
| PL 1 OR30 15m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2612 | 3.7 | -8.9 | -9.9 | 12.6 | 0.17 / -0.42 / -0.47 | 38.3 / 25.9 |
| PL 2 OR30 15m with exit=hd0.3xADR | negative pre-2023 | 2612 | -4.4 | -18.7 | -19.9 | 14.4 | -0.18 / -0.75 / -0.80 | 50.1 / 35.7 |
| PL 3 OR30 15m with exit=b20.3xADR | negative pre-2023 | 2612 | -0.6 | -14.4 | -15.6 | 13.8 | -0.03 / -0.59 / -0.64 | 41.2 / 27.4 |
| PL 4 OR30 15m with exit=hd0.2xADR | negative pre-2023 | 2612 | -2.2 | -16.5 | -17.7 | 14.4 | -0.10 / -0.75 / -0.80 | 42.6 / 28.2 |
| PL 5 PD 5m with exit=hd0.3xADR | negative pre-2023 | 2000 | -12.4 | -26.7 | -27.9 | 14.4 | -0.39 / -0.84 / -0.87 | 36.8 / 22.5 |
| PL 6 PD 15m with exit=hd0.3xADR | negative pre-2023 | 1906 | -11.2 | -25.6 | -26.8 | 14.4 | -0.36 / -0.81 / -0.85 | 40.5 / 26.1 |
| PL 7 OR60 15m with exit=hd0.3xADR | negative pre-2023 | 2457 | -5.6 | -20.0 | -21.2 | 14.4 | -0.24 / -0.86 / -0.91 | 38.9 / 24.6 |
| PL 8 OR30 15m with exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2612 | 3.8 | -9.4 | -10.6 | 13.2 | 0.18 / -0.47 / -0.53 | 28.6 / 15.5 |
| PL 9 OR60 5m with exit=hd0.3xADR | negative pre-2023 | 2541 | -5.6 | -19.9 | -21.2 | 14.4 | -0.23 / -0.83 / -0.89 | 40.2 / 25.8 |
| PL 10 OR60 5m with exit=b20.3xADR | negative pre-2023 | 2541 | -1.6 | -15.5 | -16.7 | 13.9 | -0.07 / -0.67 / -0.73 | 32.3 / 18.4 |
| HO 1 PD 15m fade exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 1983 | 1.4 | -10.3 | -9.0 | 11.7 | 0.01 / -0.18 / -0.15 | 115.0 / 103.5 |
| HO 2 PD 15m fade exit=b10.2xADR | negative pre-2023 | 1983 | -1.7 | -12.4 | -11.2 | 10.8 | -0.04 / -0.27 / -0.25 | 77.5 / 67.0 |
| HO 3 PD 15m fade exit=hd0.2xADR | negative pre-2023 | 1983 | -16.9 | -29.6 | -28.2 | 12.8 | -0.23 / -0.40 / -0.38 | 120.2 / 107.4 |
| HO 4 PD 5m fade exit=b10.2xADR | negative pre-2023 | 2058 | -12.6 | -23.4 | -22.2 | 10.8 | -0.29 / -0.52 / -0.50 | 60.5 / 49.9 |
| HO 5 PD 5m fade exit=hd0.3xADR | negative pre-2023 | 2058 | -16.3 | -29.0 | -27.6 | 12.8 | -0.18 / -0.32 / -0.31 | 129.1 / 116.3 |
| HO 6 PD 15m fade exit=tr0.3xADR | negative pre-2023 | 1983 | -12.0 | -24.7 | -23.3 | 12.8 | -0.18 / -0.37 / -0.34 | 86.1 / 73.3 |
| HO 7 PD 5m fade exit=hd0.2xADR | negative pre-2023 | 2058 | -18.7 | -31.5 | -30.0 | 12.8 | -0.25 / -0.42 / -0.40 | 111.7 / 98.9 |
| HO 8 PD 5m fade exit=tr0.3xADR | negative pre-2023 | 2058 | -8.2 | -21.0 | -19.5 | 12.8 | -0.12 / -0.32 / -0.29 | 80.1 / 67.3 |
| HO 9 PD 5m fade exit=b10.3xADR | negative pre-2023 | 2058 | -13.4 | -24.4 | -23.2 | 11.0 | -0.21 / -0.38 / -0.36 | 72.1 / 61.3 |
| HO 10 PD 15m fade exit=b20.1xADR | gross-positive, cost-negative pre-2023 | 1983 | 2.4 | -9.0 | -7.7 | 11.4 | 0.08 / -0.26 / -0.22 | 46.8 / 35.6 |
| RB 1 OR30 15m fade exit=hd0.3xADR | negative pre-2023 | 2693 | -4.2 | -16.9 | -16.0 | 12.8 | -0.08 / -0.27 / -0.26 | 120.8 / 108.1 |
| RB 2 OR30 5m fade exit=hd0.3xADR | positive pre-2023 | 2695 | 13.1 | 0.3 | 1.3 | 12.8 | 0.21 / 0.01 / 0.03 | 117.3 / 104.6 |
| RB 3 PD 5m fade exit=tr0.1xADR | gross-positive, cost-negative pre-2023 | 2123 | 0.6 | -12.1 | -11.2 | 12.8 | 0.02 / -0.65 / -0.60 | 39.5 / 26.7 |
| RB 4 PD 5m fade exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 2123 | 5.8 | -7.0 | -6.1 | 12.8 | 0.06 / -0.11 / -0.09 | 102.9 / 90.2 |
| RB 5 PD 5m fade exit=b10.2xADR | negative pre-2023 | 2123 | -24.5 | -35.4 | -34.6 | 10.8 | -0.69 / -0.99 / -0.97 | 55.4 / 44.8 |
| RB 6 PD 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2123 | 3.5 | -9.3 | -8.4 | 12.8 | 0.04 / -0.16 / -0.15 | 93.7 / 80.9 |
| RB 7 PD 5m fade exit=tr0.2xADR | gross-positive, cost-negative pre-2023 | 2123 | 0.1 | -12.6 | -11.7 | 12.8 | -0.00 / -0.33 / -0.30 | 61.2 / 48.4 |
| RB 8 PD 15m fade exit=tr0.2xADR | negative pre-2023 | 2044 | -1.4 | -14.2 | -13.3 | 12.8 | -0.04 / -0.35 / -0.32 | 58.1 / 45.3 |
| RB 9 OR30 15m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2693 | 4.7 | -8.0 | -7.1 | 12.8 | 0.07 / -0.15 / -0.14 | 82.1 / 69.3 |
| RB 10 OR30 5m fade exit=hd0.2xADR | positive pre-2023 | 2695 | 22.0 | 9.3 | 10.2 | 12.8 | 0.39 / 0.17 / 0.18 | 93.4 / 80.7 |
| NG 1 OR15 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2677 | 4.1 | -20.3 | -24.7 | 24.4 | 0.10 / -0.48 / -0.59 | 60.7 / 36.4 |
| NG 2 PD 15m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 1962 | 13.3 | -9.7 | -14.0 | 23.1 | 0.30 / -0.21 / -0.31 | 59.8 / 36.7 |
| NG 3 PD 5m with exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2028 | 13.9 | -9.0 | -13.3 | 22.9 | 0.30 / -0.19 / -0.28 | 57.3 / 34.3 |
| NG 4 PD 15m with exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 1962 | 13.1 | -11.2 | -15.8 | 24.4 | 0.28 / -0.24 / -0.34 | 54.9 / 30.5 |
| NG 5 OR30 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2636 | 7.4 | -17.0 | -21.5 | 24.4 | 0.19 / -0.44 / -0.56 | 48.9 / 24.5 |
| NG 6 PD 5m with exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 2028 | 15.1 | -9.3 | -13.8 | 24.4 | 0.31 / -0.19 / -0.28 | 52.3 / 28.0 |
| NG 7 PD 15m with exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 1962 | 2.9 | -17.6 | -21.4 | 20.6 | 0.07 / -0.42 / -0.50 | 37.8 / 17.4 |
| NG 8 OR15 5m fade exit=tr0.2xADR | gross-positive, cost-negative pre-2023 | 2677 | 11.0 | -13.4 | -17.8 | 24.4 | 0.41 / -0.50 / -0.66 | 34.7 / 10.3 |
| NG 9 OR15 5m fade exit=hd0.3xADR | negative pre-2023 | 2677 | -0.1 | -24.4 | -28.9 | 24.4 | -0.00 / -0.47 / -0.56 | 39.2 / 14.8 |
| NG 10 OR30 5m fade exit=tr0.2xADR | gross-positive, cost-negative pre-2023 | 2636 | 5.9 | -18.4 | -22.9 | 24.4 | 0.24 / -0.74 / -0.92 | 31.6 / 7.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HG: 0 cells pass the clean rule against a replicate mean of 8.8 (p(count) = 1.00); HO: 44 cells pass the clean rule against a replicate mean of 30.4 (p(count) = 0.00, p(top) = 0.06); NG: 11 cells pass the clean rule against a replicate mean of 7.6 (p(count) = 0.12, p(top) = 0.12); PL: 15 cells pass the clean rule against a replicate mean of 8.8 (p(count) = 0.04, p(top) = 0.17); RB: 43 cells pass the clean rule against a replicate mean of 23.0 (p(count) = 0.00, p(top) = 0.01); SI: 8 cells pass the clean rule against a replicate mean of 7.6 (p(count) = 0.48, p(top) = 0.73).
- Of 48 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.31 (SI OR15 15m fade exit=tr0.3xADR); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 9; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell SI OR15 15m fade exit=tr0.3xADR: uplift +0.16/+0.10/+0.61, boot lo -0.17, plateau 0.50, 2x-slip +0.18, wd corr -0.40, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 25, 'gross-positive, cost-negative pre-2023': 21, 'positive pre-2023': 2}.

- Manual note: the only gate-3 cell (SI 15-minute fade of the first 15-minute opening range, trail 0.3 x ADR20) is the same trade type as the B11 CL OR15 fade lead (opening-range fade, first close beyond the first 15 minutes, 08:20 ET for metals, 09:00 ET for CL): uplift +0.16 / +0.10 / +0.61, bootstrap lower bound -0.17, plateau 0.50, ERA negative pre-2023. Two commodities with the same type of lead, both with failed bootstrap/plateau/replication gates: a LEAD (weak), logged as a family observation (opening-range fade on commodities).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q4c.py (= ap_b11.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q4c/ (`Q4C_CO_all_selected_scored.csv`).

DONE Q4C
