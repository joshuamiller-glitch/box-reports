# REPORT Q4B - Q4B: B10 grid on metals/energy (SI, HG, PL, HO, RB, NG)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 30 selected cells (+21 diagnostic) scored on 6 instruments; best non-diagnostic all-in additive uplift at 20% share +0.36; best pair-window standalone Sharpe +1.52.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Windows (ET): Asia entries 19:00-01:30 flat 02:00; London entries 02:30-07:30 flat 08:25. Strategies: ST(14,2), EMA 9/21, Donchian 20, window opening-range breakout (first 30 min), VWAP-z 2.0 fade, RSI(14,30) fade. Exits: bracket stop=target or trail at 0.25/0.5 x SR (SR = the window's own 20-day mean range).
- Instruments: SI, HG, PL, HO, RB, NG. Grid: 144 cells per instrument = 2 windows x 3 bar sizes x 6 strategies x 4 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 5 per instrument per window (Asia, London separately) by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| HG    |     144 |        144 |         5 |               0.648 |                2 |          5 |            4 |
| HO    |     144 |        136 |        17 |               1.648 |                2 |          8 |            2 |
| NG    |     144 |        140 |         4 |               0.52  |                2 |          4 |            4 |
| PL    |     144 |        144 |         3 |               0.826 |                2 |          3 |            5 |
| RB    |     144 |        134 |        29 |               1.335 |                2 |         10 |            0 |
| SI    |     144 |        144 |         0 |              -0.232 |                1 |          0 |            6 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| SI    |     100 |                    0 |             0.41 |               2 |       1    |                     nan     |            0.455 |           0.909 |   nan    |     nan     |                0.909 |
| HG    |     100 |                    5 |             2.37 |               7 |       0.08 |                       0.334 |            0.494 |           0.865 |     0.72 |       0.648 |                1.242 |
| PL    |     100 |                    3 |             4.14 |               9 |       0.79 |                       0.705 |            0.618 |           0.986 |     0.29 |       0.826 |                1.552 |
| HO    |     100 |                   17 |            10.4  |              15 |       0    |                       1.067 |            0.901 |           1.185 |     0.14 |       1.648 |                1.921 |
| RB    |     100 |                   29 |             5.09 |              12 |       0    |                       0.968 |            0.619 |           0.901 |     0.02 |       1.335 |                1.526 |
| NG    |     100 |                    4 |             0.33 |               2 |       0    |                       0.313 |            0.527 |           1.168 |     0.19 |       0.52  |                1.168 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SI 1 (diag) | asia 30m rsi[14, 30] exit=trail0.25xSR | 140 | 1 | -0.43 | -1.00 | -0.71 | -1.06 / 1.17 | -0.12 / -2.07 / -0.92 | -0.79 | 0.35 | 0.45 | -1.19 | 0.00 | 261 | diag |
| SI 2 (diag) | asia 30m st[14, 2.0] exit=bracket0.5xSR | 244 | 1 | -0.48 | -1.83 | 0.28 | 0.57 / 1.42 | -0.14 / 0.22 / -0.75 | -0.36 | -0.22 | 0.85 | -0.88 | 0.00 | 431 | diag |
| SI 3 (diag) | asia 30m vwz[2.0] exit=bracket0.5xSR | 342 | 0 | -0.51 | -0.25 | -0.68 | -0.99 / 1.08 | -0.11 / -2.44 / -0.91 | -0.83 | 0.15 | 0.31 | -1.24 | 0.00 | 501 | diag |
| SI 4 (diag) | lon 30m vwz[2.0] exit=bracket0.25xSR | 211 | 1 | -0.23 | -0.96 | -0.59 | -0.88 / 1.27 | -0.13 / 0.22 / -1.00 | -0.44 | 0.31 | 0.52 | -0.66 | 0.00 | 291 | diag |
| SI 5 (diag) | lon 30m rsi[14, 30] exit=bracket0.5xSR | 133 | 1 | -0.24 | -1.09 | 0.64 | 1.26 / 1.40 | -0.08 / 0.91 / -0.15 | -0.02 | -0.20 | 0.93 | -0.32 | 0.17 | 210 | diag |
| SI 6 (diag) | lon 5m orb[30] exit=trail0.25xSR | 507 | 1 | -0.26 | -2.55 | -0.24 | -0.31 / 0.45 | -0.05 / 0.42 / -1.40 | -0.63 | -0.32 | 0.88 | -0.75 | 0.00 | 813 | diag |
| HG 1 | asia 15m vwz[2.0] exit=bracket0.5xSR | 514 | 2 | 0.05 | -1.05 | -0.13 | -0.39 / 0.70 | 0.00 / -0.72 / 0.40 | -0.17 | 0.51 | 0.94 | -0.24 | 0.00 | 812 | NO |
| HG 2 (diag) | asia 30m rsi[14, 30] exit=trail0.25xSR | 161 | 1 | 0.16 | -0.85 | -0.16 | -0.40 / 0.70 | 0.03 / -0.00 / -0.51 | -0.26 | 0.46 | 0.97 | -0.36 | 0.00 | 271 | diag |
| HG 3 (diag) | asia 30m rsi[14, 30] exit=bracket0.25xSR | 152 | 1 | 0.15 | -0.85 | 0.05 | 0.05 / 0.41 | 0.01 / -0.14 / 0.18 | -0.11 | -0.26 | 0.99 | -0.25 | 0.17 | 261 | diag |
| HG 4 (diag) | asia 5m rsi[14, 30] exit=bracket0.5xSR | 676 | 1 | 0.12 | -0.66 | -0.46 | -1.12 / 0.36 | 0.00 / 0.08 / -0.44 | -0.25 | 0.06 | 0.75 | -0.30 | 0.00 | 1072 | diag |
| HG 5 | lon 5m vwz[2.0] exit=trail0.5xSR | 432 | 2 | 0.65 | -1.00 | 0.27 | -0.19 / 0.78 | 0.08 / 0.24 / -0.27 | -0.11 | -0.66 | 0.96 | -0.18 | 0.00 | 616 | NO |
| HG 6 | lon 15m vwz[2.0] exit=trail0.5xSR | 309 | 2 | 0.55 | -0.82 | 0.33 | -0.10 / 0.78 | 0.06 / -0.29 / -0.08 | -0.12 | -0.48 | 0.99 | -0.19 | 0.00 | 436 | NO |
| HG 7 | lon 15m vwz[2.0] exit=bracket0.5xSR | 298 | 2 | 0.41 | -0.72 | 0.57 | 0.65 / 1.15 | 0.03 / -0.16 / 0.08 | -0.07 | -0.42 | 0.99 | -0.16 | 0.00 | 422 | NO |
| HG 8 | lon 30m vwz[2.0] exit=trail0.25xSR | 227 | 2 | 0.01 | -1.56 | -0.32 | -0.79 / 0.07 | -0.04 / -0.28 / -0.19 | -0.23 | -0.38 | 0.97 | -0.29 | 0.00 | 321 | NO |
| HG 9 (diag) | lon 5m vwz[2.0] exit=bracket0.5xSR | 421 | 1 | 0.37 | -0.99 | 0.41 | 0.42 / 0.66 | 0.02 / 0.37 / -0.30 | -0.10 | -0.55 | 0.99 | -0.17 | 0.00 | 605 | diag |
| PL 1 (diag) | asia 30m vwz[2.0] exit=bracket0.5xSR | 315 | 1 | 0.43 | -0.25 | -0.38 | -0.82 / 1.13 | 0.07 / -1.11 / -0.64 | -0.36 | 0.21 | 0.50 | -0.69 | 0.00 | 460 | diag |
| PL 2 (diag) | asia 30m vwz[2.0] exit=trail0.5xSR | 316 | 1 | 0.17 | -0.40 | -0.14 | -0.30 / 1.16 | 0.04 / -0.49 / -0.52 | -0.30 | 0.16 | 0.66 | -0.58 | 0.00 | 462 | diag |
| PL 3 (diag) | asia 15m emax[9, 21] exit=bracket0.5xSR | 405 | 1 | -0.22 | -1.58 | 0.56 | 1.15 / 1.51 | -0.10 / -0.09 / 0.05 | -0.11 | 0.30 | 0.95 | -0.41 | 0.00 | 658 | diag |
| PL 4 | lon 30m don[20] exit=trail0.5xSR | 435 | 2 | 0.83 | -0.62 | 0.28 | 0.14 / 0.97 | 0.17 / -0.38 / -0.05 | -0.02 | -0.13 | 0.88 | -0.25 | 0.25 | 619 | NO |
| PL 5 | lon 30m don[20] exit=bracket0.5xSR | 462 | 2 | 0.66 | -0.79 | -0.11 | -0.48 / 1.23 | 0.11 / -0.97 / -0.04 | -0.15 | -0.36 | 0.68 | -0.38 | 0.00 | 662 | NO |
| PL 6 | lon 30m orb[30] exit=trail0.25xSR | 513 | 2 | 0.64 | -1.86 | 0.35 | 0.26 / 0.84 | 0.13 / -0.71 / 0.42 | -0.05 | -0.33 | 0.95 | -0.23 | 0.25 | 819 | NO |
| PL 7 (diag) | lon 5m emax[9, 21] exit=trail0.5xSR | 611 | 1 | 0.53 | -1.26 | 0.19 | 0.07 / 1.08 | 0.07 / -1.19 / 0.10 | -0.19 | -0.16 | 0.74 | -0.42 | 0.00 | 990 | diag |
| PL 8 (diag) | lon 30m orb[30] exit=bracket0.25xSR | 513 | 1 | 0.36 | -1.80 | -0.34 | -0.65 / 0.99 | 0.07 / -0.65 / -0.83 | -0.34 | -0.03 | 0.67 | -0.60 | 0.00 | 819 | diag |
| HO 1 | asia 30m vwz[2.0] exit=trail0.25xSR | 349 | 2 | 0.98 | -0.74 | 0.68 | 0.61 / 0.75 | 0.11 / 0.09 / -0.04 | -0.02 | -0.23 | 0.99 | -0.19 | 0.25 | 548 | NO |
| HO 2 | asia 30m vwz[2.0] exit=bracket0.5xSR | 324 | 2 | 0.67 | -1.06 | 0.40 | 0.32 / 1.16 | 0.10 / 0.45 / -0.60 | -0.11 | 0.29 | 0.93 | -0.40 | 0.00 | 500 | NO |
| HO 3 | asia 30m vwz[2.0] exit=trail0.5xSR | 320 | 2 | 0.49 | -0.65 | 0.26 | 0.21 / 1.17 | 0.04 / 0.27 / -0.61 | -0.16 | 0.34 | 0.96 | -0.43 | 0.00 | 500 | NO |
| HO 4 (diag) | asia 15m vwz[2.0] exit=bracket0.5xSR | 445 | 1 | 0.58 | -1.29 | 0.22 | -0.08 / 1.25 | 0.08 / 0.30 / -0.52 | -0.10 | -0.00 | 0.88 | -0.32 | 0.00 | 683 | diag |
| HO 5 (diag) | asia 30m rsi[14, 30] exit=bracket0.25xSR | 80 | 1 | 0.48 | -0.24 | 0.04 | -0.25 / 1.24 | 0.03 / -0.24 / -0.41 | -0.17 | -0.32 | 0.87 | -0.44 | 0.00 | 125 | diag |
| HO 6 | lon 30m st[14, 2.0] exit=bracket0.25xSR | 471 | 2 | 1.65 | -0.72 | 0.65 | 0.04 / 1.41 | 0.32 / -0.22 / -0.12 | 0.09 | 0.63 | 0.95 | -0.16 | 0.50 | 766 | NO |
| HO 7 | lon 30m emax[9, 21] exit=bracket0.25xSR | 317 | 2 | 1.44 | -0.18 | 0.68 | 0.33 / 1.09 | 0.30 / 0.08 / 0.19 | 0.21 | -0.07 | 0.95 | -0.06 | 0.17 | 509 | NO |
| HO 8 | lon 30m st[14, 2.0] exit=trail0.25xSR | 475 | 2 | 1.25 | -0.11 | 0.73 | 0.41 / 1.02 | 0.25 / -0.02 / -0.09 | 0.07 | 0.21 | 0.97 | -0.13 | 0.33 | 770 | NO |
| HO 9 | lon 30m orb[30] exit=bracket0.25xSR | 514 | 2 | 1.04 | -0.74 | 0.07 | -0.61 / 1.02 | 0.13 / -0.39 / -0.78 | -0.21 | 0.46 | 0.83 | -0.42 | 0.00 | 821 | NO |
| HO 10 | lon 5m rsi[14, 30] exit=trail0.5xSR | 573 | 2 | 1.02 | -0.05 | 0.86 | 0.77 / 1.83 | 0.20 / 0.07 / 0.02 | 0.09 | -0.19 | 0.89 | -0.13 | 0.00 | 906 | NO |
| RB 1 | asia 15m vwz[2.0] exit=trail0.5xSR | 415 | 2 | 1.34 | -0.55 | 0.90 | 0.78 / 0.87 | 0.22 / -0.41 / 0.38 | 0.09 | -0.46 | 1.00 | -0.09 | 0.00 | 666 | NO |
| RB 2 | asia 15m vwz[2.0] exit=bracket0.25xSR | 508 | 2 | 1.27 | -1.37 | 0.30 | -0.57 / -0.01 | 0.19 / -0.32 / -0.24 | -0.12 | -0.15 | 1.00 | -0.24 | 0.25 | 820 | NO |
| RB 3 | asia 15m vwz[2.0] exit=trail0.25xSR | 498 | 2 | 0.89 | -0.56 | 0.23 | -0.24 / 0.68 | 0.11 / -0.47 / -0.08 | -0.16 | -0.25 | 0.99 | -0.28 | 0.00 | 809 | NO |
| RB 4 | asia 5m vwz[2.0] exit=bracket0.5xSR | 577 | 2 | 0.84 | -0.91 | 0.48 | 0.20 / 0.69 | 0.19 / -0.19 / 0.07 | 0.02 | 0.36 | 0.99 | -0.14 | 0.50 | 933 | NO |
| RB 5 | asia 15m rsi[14, 30] exit=bracket0.5xSR | 122 | 2 | 0.74 | -0.42 | 0.35 | 0.21 / 1.09 | 0.14 / -0.16 / -0.50 | -0.13 | 0.56 | 0.93 | -0.44 | 0.00 | 220 | NO |
| RB 6 | lon 30m rsi[14, 30] exit=trail0.25xSR | 171 | 2 | 1.09 | -0.24 | 0.46 | -0.17 / 0.73 | 0.21 / -0.10 / -0.19 | 0.03 | 0.22 | 0.98 | -0.14 | 0.33 | 281 | NO |
| RB 7 | lon 30m vwz[2.0] exit=bracket0.5xSR | 282 | 2 | 0.99 | -0.23 | 1.52 | 2.11 / 1.43 | 0.16 / -0.07 / 1.20 | 0.32 | -0.27 | 1.00 | 0.11 | 0.25 | 452 | NO |
| RB 8 | lon 30m st[14, 2.0] exit=bracket0.25xSR | 461 | 2 | 0.98 | -0.92 | -0.54 | -1.88 / 0.94 | 0.12 / -0.39 / -1.01 | -0.27 | 0.50 | 0.63 | -0.46 | 0.00 | 734 | NO |
| RB 9 | lon 30m rsi[14, 30] exit=bracket0.25xSR | 169 | 2 | 0.80 | -0.25 | 0.53 | 0.19 / 0.71 | 0.12 / 0.04 / -0.03 | 0.04 | 0.09 | 0.98 | -0.14 | 0.00 | 274 | NO |
| RB 10 | lon 30m vwz[2.0] exit=trail0.5xSR | 278 | 2 | 0.76 | -0.24 | 1.22 | 1.69 / 0.83 | 0.12 / -0.20 / 0.87 | 0.21 | -0.18 | 1.00 | 0.01 | 0.50 | 444 | NO |
| NG 1 (diag) | asia 30m st[14, 2.0] exit=trail0.5xSR | 84 | 1 | -0.07 | -0.82 | -0.45 | -0.84 / -0.08 | -0.02 / -0.95 / -0.12 | -0.33 | -0.22 | 0.95 | -0.47 | 0.00 | 164 | diag |
| NG 2 (diag) | asia 30m st[14, 2.0] exit=trail0.25xSR | 84 | 1 | -0.38 | -1.27 | -1.03 | -1.97 / -1.39 | -0.11 / -1.01 / -0.18 | -0.47 | 0.17 | 1.00 | -0.47 | 0.00 | 164 | diag |
| NG 3 (diag) | asia 30m vwz[2.0] exit=trail0.5xSR | 278 | 1 | -0.46 | -1.07 | -1.35 | -3.61 / 0.28 | -0.15 / -0.46 / -0.53 | -0.45 | 0.61 | 0.37 | -0.44 | 0.00 | 437 | diag |
| NG 4 | lon 5m rsi[14, 30] exit=bracket0.5xSR | 529 | 2 | 0.52 | -0.62 | 0.10 | -0.68 / 0.60 | 0.03 / -0.28 / -0.03 | -0.21 | -0.68 | 0.99 | -0.24 | 0.00 | 826 | NO |
| NG 5 | lon 15m rsi[14, 30] exit=trail0.5xSR | 316 | 2 | 0.38 | -0.75 | 0.27 | -0.13 / -0.43 | 0.00 / -0.47 / 0.25 | -0.16 | -0.49 | 1.00 | -0.20 | 0.00 | 467 | NO |
| NG 6 | lon 15m rsi[14, 30] exit=bracket0.5xSR | 302 | 2 | 0.21 | 0.12 | 0.46 | 0.77 / 0.59 | -0.01 / -0.29 / 0.33 | -0.10 | -0.49 | 1.00 | -0.17 | 0.67 | 451 | NO |
| NG 7 | lon 30m vwz[2.0] exit=trail0.5xSR | 256 | 2 | 0.14 | -0.63 | -0.27 | -0.91 / -0.30 | -0.04 / -0.39 / -0.15 | -0.25 | -0.38 | 0.97 | -0.30 | 0.00 | 386 | NO |
| NG 8 (diag) | lon 30m vwz[2.0] exit=bracket0.5xSR | 262 | 1 | 0.20 | -0.59 | 0.11 | -0.03 / 0.80 | -0.03 / -0.01 / 0.06 | -0.13 | -0.47 | 0.99 | -0.21 | 0.00 | 393 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 30 |
| diagnostic cells read | 21 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 27 |
| worst-decile corr <= +0.30 | 39 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HG lon 15m vwz[2.0] exit=bracket0.5xSR | clean | 0.50 | 0.81 | -117804 | -100431 | 711132 | -155993 | 0.64 | 47.6 | 1.49 | -92834 | 327150 | -108257 |
| HG lon 15m vwz[2.0] exit=bracket0.5xSR | H1 | 0.58 | 0.87 | -110839 | -102156 | 376992 | -135242 | 0.34 | 28.6 | 2.66 | -86253 | 175646 | -94219 |
| HG lon 15m vwz[2.0] exit=bracket0.5xSR | H2 | 0.70 | 1.23 | -125875 | -110290 | 482147 | -132211 | 0.63 | 44.4 | 2.37 | -102456 | 249078 | -103858 |
| HG lon 15m vwz[2.0] exit=bracket0.5xSR | all | 0.57 | 0.92 | -121555 | -105525 | 711132 | -155993 | 1.25 | 44.0 | 1.88 | -95126 | 327150 | -108257 |
| HO lon 30m emax[9, 21] exit=bracket0.25xSR | clean | 1.36 | 2.26 | -108318 | -95306 | 493227 | -146805 | 2.53 | 44.8 | 1.76 | -81311 | 257820 | -87530 |
| HO lon 30m emax[9, 21] exit=bracket0.25xSR | H1 | 1.34 | 2.74 | -64338 | -58832 | 169035 | -70014 | 1.59 | 50.0 | 2.91 | -81246 | 154889 | -83743 |
| HO lon 30m emax[9, 21] exit=bracket0.25xSR | H2 | 0.18 | 0.25 | -503323 | -349597 | 870133 | -648723 | 0.21 | 47.2 | 2.48 | -98379 | 263853 | -114233 |
| HO lon 30m emax[9, 21] exit=bracket0.25xSR | all | 0.68 | 0.97 | -241509 | -175644 | 870133 | -648723 | 1.95 | 46.4 | 2.11 | -86182 | 263853 | -114233 |
| NG lon 15m rsi[14, 30] exit=bracket0.5xSR | clean | 0.30 | 0.42 | -128541 | -108863 | 661704 | -185866 | 0.41 | 46.7 | 1.45 | -93486 | 302929 | -114181 |
| NG lon 15m rsi[14, 30] exit=bracket0.5xSR | H1 | -0.82 | -1.08 | -124719 | -108590 | 430942 | -165163 | -0.43 | 60.7 | 2.54 | -98764 | 165412 | -109965 |
| NG lon 15m rsi[14, 30] exit=bracket0.5xSR | H2 | 2.18 | 5.40 | -60286 | -53955 | 160648 | -67030 | 3.54 | 52.8 | 2.63 | -82794 | 232941 | -85675 |
| NG lon 15m rsi[14, 30] exit=bracket0.5xSR | all | 0.46 | 0.69 | -124411 | -102733 | 661704 | -185866 | 0.98 | 50.6 | 1.87 | -93791 | 302929 | -114181 |
| PL lon 30m orb[30] exit=trail0.25xSR | clean | 0.54 | 1.05 | -84727 | -75420 | 603467 | -120721 | 0.82 | 51.4 | 1.59 | -81853 | 245489 | -101297 |
| PL lon 30m orb[30] exit=trail0.25xSR | H1 | -0.61 | -0.84 | -310249 | -259681 | 1220142 | -416791 | -0.29 | 57.1 | 2.12 | -115211 | 251886 | -160291 |
| PL lon 30m orb[30] exit=trail0.25xSR | H2 | 0.93 | 1.87 | -184481 | -162469 | 727413 | -197483 | 0.96 | 58.3 | 2.72 | -82764 | 181000 | -84613 |
| PL lon 30m orb[30] exit=trail0.25xSR | all | 0.35 | 0.59 | -188178 | -154279 | 1589271 | -416791 | 0.53 | 54.2 | 1.94 | -90771 | 265831 | -160291 |
| RB lon 30m vwz[2.0] exit=bracket0.5xSR | clean | 1.03 | 1.70 | -118994 | -96707 | 539708 | -180533 | 1.74 | 46.7 | 1.62 | -84654 | 266276 | -91018 |
| RB lon 30m vwz[2.0] exit=bracket0.5xSR | H1 | 0.05 | 0.06 | -89501 | -79888 | 210107 | -110553 | 0.04 | 46.4 | 2.76 | -80138 | 133847 | -83292 |
| RB lon 30m vwz[2.0] exit=bracket0.5xSR | H2 | 2.99 | 6.31 | -195780 | -179862 | 387620 | -223244 | 5.42 | 27.8 | 3.50 | -62038 | 197365 | -63796 |
| RB lon 30m vwz[2.0] exit=bracket0.5xSR | all | 1.52 | 2.91 | -154622 | -120979 | 539708 | -223244 | 5.64 | 42.9 | 2.21 | -82677 | 266276 | -91018 |
| SI lon 30m rsi[14, 30] exit=bracket0.5xSR (diag) | clean | -0.32 | -0.45 | -134170 | -112476 | 671917 | -170107 | -0.43 | 42.9 | 1.38 | -87139 | 269372 | -108289 |
| SI lon 30m rsi[14, 30] exit=bracket0.5xSR (diag) | H1 | 2.64 | 7.61 | -139804 | -125527 | 478478 | -161897 | 3.03 | 32.1 | 3.74 | -89381 | 164276 | -101830 |
| SI lon 30m rsi[14, 30] exit=bracket0.5xSR (diag) | H2 | 0.77 | 1.25 | -563164 | -398522 | 780654 | -780654 | 1.32 | 36.1 | 2.15 | -128054 | 288898 | -131089 |
| SI lon 30m rsi[14, 30] exit=bracket0.5xSR (diag) | all | 0.64 | 1.09 | -284786 | -208092 | 1259132 | -780654 | 1.74 | 39.9 | 1.92 | -103073 | 314852 | -131089 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| SI lon 30m rsi[14, 30] exit=bracket0.5xSR (diag) | -5.5 | -162.5 | -33.1 | -50.6 | -23.2 / 13.0 | -15.1 / 7.2 | NO |
| HG lon 15m vwz[2.0] exit=bracket0.5xSR | -20.1 | -22.1 | -1.5 | 4.8 | -23.0 / 2.8 | -1.9 / 13.3 | NO |
| PL lon 30m orb[30] exit=trail0.25xSR | -20.6 | -116.8 | -0.4 | -37.1 | -10.2 / 19.7 | -128.5 / -44.5 | NO |
| HO lon 30m emax[9, 21] exit=bracket0.25xSR | -11.1 | -52.5 | 0.1 | 12.2 | 15.6 / 21.4 | 18.2 / 23.0 | NO |
| RB lon 30m vwz[2.0] exit=bracket0.5xSR | 4.0 | 5.6 | 18.1 | 17.5 | 8.5 / 18.0 | 19.0 / 25.1 | NO |
| NG lon 15m rsi[14, 30] exit=bracket0.5xSR | -22.7 | -32.9 | -0.1 | 10.7 | -33.9 / -0.6 | -32.1 / -10.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| SI 1 (diag) asia 30m rsi[14, 30] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 610 | 19.4 | -35.0 | -16.4 | 54.4 | 0.56 / -1.00 / -0.47 | 31.8 / -22.6 |
| SI 2 (diag) asia 30m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 1082 | -35.2 | -85.0 | -68.0 | 49.8 | -0.79 / -1.83 / -1.48 | 22.9 / -27.1 |
| SI 3 (diag) asia 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1149 | 37.4 | -10.8 | 5.1 | 48.2 | 0.87 / -0.25 / 0.12 | 26.7 / -21.4 |
| SI 4 (diag) lon 30m vwz[2.0] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 1142 | 13.2 | -29.0 | -13.8 | 42.3 | 0.45 / -0.96 / -0.46 | 29.4 / -12.3 |
| SI 5 (diag) lon 30m rsi[14, 30] exit=bracket0.5xSR | negative pre-2023 | 687 | -26.4 | -73.7 | -56.7 | 47.3 | -0.40 / -1.09 / -0.84 | 18.7 / -27.6 |
| SI 6 (diag) lon 5m orb[30] exit=trail0.25xSR | negative pre-2023 | 2636 | -1.9 | -56.3 | -37.2 | 54.4 | -0.08 / -2.55 / -1.68 | 47.1 / -7.3 |
| HG 1 asia 15m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 2038 | 1.5 | -24.7 | -18.1 | 26.1 | 0.06 / -1.05 / -0.77 | 28.7 / 3.1 |
| HG 2 (diag) asia 30m rsi[14, 30] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 807 | 7.3 | -22.0 | -14.3 | 29.4 | 0.29 / -0.85 / -0.55 | 33.5 / 4.2 |
| HG 3 (diag) asia 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 783 | 3.5 | -20.5 | -14.2 | 24.1 | 0.15 / -0.85 / -0.59 | 25.3 / 1.7 |
| HG 4 (diag) asia 5m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 3237 | 13.8 | -11.9 | -5.1 | 25.7 | 0.74 / -0.66 / -0.29 | 27.8 / 2.4 |
| HG 5 lon 5m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 2105 | 1.8 | -27.5 | -19.6 | 29.4 | 0.04 / -1.00 / -0.72 | 49.3 / 20.0 |
| HG 6 lon 15m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1577 | 3.9 | -25.5 | -17.6 | 29.4 | 0.12 / -0.82 / -0.56 | 52.8 / 23.4 |
| HG 7 lon 15m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1551 | 2.9 | -22.9 | -16.0 | 25.8 | 0.09 / -0.72 / -0.50 | 46.9 / 21.2 |
| HG 8 lon 30m vwz[2.0] exit=trail0.25xSR | negative pre-2023 | 1287 | -3.8 | -33.2 | -25.3 | 29.4 | -0.18 / -1.56 / -1.20 | 27.9 / -1.4 |
| HG 9 (diag) lon 5m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 2059 | -0.3 | -26.1 | -19.1 | 25.8 | -0.02 / -0.99 / -0.73 | 40.7 / 15.3 |
| PL 1 (diag) asia 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1459 | 8.8 | -4.3 | -5.1 | 13.1 | 0.54 / -0.25 / -0.30 | 18.0 / 5.1 |
| PL 2 (diag) asia 30m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1451 | 7.8 | -6.5 | -7.4 | 14.4 | 0.50 / -0.40 / -0.46 | 16.2 / 1.8 |
| PL 3 (diag) asia 15m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 2062 | -7.9 | -21.1 | -22.3 | 13.2 | -0.61 / -1.58 / -1.66 | 7.0 / -5.9 |
| PL 4 lon 30m don[20] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1912 | 1.7 | -12.7 | -13.8 | 14.4 | 0.08 / -0.62 / -0.67 | 26.4 / 12.0 |
| PL 5 lon 30m don[20] exit=bracket0.5xSR | negative pre-2023 | 2049 | -1.8 | -14.7 | -15.7 | 12.9 | -0.10 / -0.79 / -0.84 | 20.1 / 7.2 |
| PL 6 lon 30m orb[30] exit=trail0.25xSR | negative pre-2023 | 2583 | -5.2 | -19.5 | -20.7 | 14.4 | -0.49 / -1.86 / -1.97 | 22.1 / 7.7 |
| PL 7 (diag) lon 5m emax[9, 21] exit=trail0.5xSR | negative pre-2023 | 3205 | -5.7 | -20.1 | -21.4 | 14.4 | -0.36 / -1.26 / -1.34 | 22.5 / 8.1 |
| PL 8 (diag) lon 30m orb[30] exit=bracket0.25xSR | negative pre-2023 | 2583 | -7.7 | -19.8 | -20.8 | 12.0 | -0.71 / -1.80 / -1.89 | 12.9 / 1.2 |
| HO 1 asia 30m vwz[2.0] exit=trail0.25xSR | negative pre-2023 | 1422 | -2.4 | -15.1 | -13.5 | 12.8 | -0.11 / -0.74 / -0.65 | 28.2 / 15.5 |
| HO 2 asia 30m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1303 | -20.2 | -32.0 | -30.5 | 11.8 | -0.67 / -1.06 / -1.01 | 26.3 / 14.7 |
| HO 3 asia 30m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1277 | -7.1 | -19.8 | -18.2 | 12.8 | -0.23 / -0.65 / -0.59 | 22.3 / 9.6 |
| HO 4 (diag) asia 15m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1758 | -24.5 | -36.3 | -34.8 | 11.7 | -0.87 / -1.29 / -1.23 | 24.8 / 13.4 |
| HO 5 (diag) asia 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 284 | 0.6 | -10.3 | -8.7 | 10.9 | 0.02 / -0.24 / -0.20 | 25.3 / 14.7 |
| HO 6 lon 30m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 2270 | -8.7 | -19.5 | -18.3 | 10.9 | -0.31 / -0.72 / -0.67 | 48.7 / 38.1 |
| HO 7 lon 30m emax[9, 21] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 1523 | 4.9 | -5.8 | -4.7 | 10.8 | 0.18 / -0.18 / -0.15 | 53.1 / 42.5 |
| HO 8 lon 30m st[14, 2.0] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 2280 | 9.2 | -3.5 | -2.1 | 12.8 | 0.32 / -0.11 / -0.06 | 45.8 / 33.1 |
| HO 9 lon 30m orb[30] exit=bracket0.25xSR | negative pre-2023 | 2609 | -7.0 | -17.7 | -16.4 | 10.8 | -0.29 / -0.74 / -0.68 | 38.8 / 28.3 |
| HO 10 lon 5m rsi[14, 30] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 2919 | 10.7 | -2.0 | -0.4 | 12.8 | 0.26 / -0.05 / -0.01 | 63.8 / 51.0 |
| RB 1 asia 15m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1541 | -4.2 | -17.0 | -16.1 | 12.8 | -0.13 / -0.55 / -0.52 | 38.6 / 25.9 |
| RB 2 asia 15m vwz[2.0] exit=bracket0.25xSR | negative pre-2023 | 1739 | -12.7 | -23.7 | -22.9 | 11.0 | -0.74 / -1.37 / -1.32 | 22.6 / 12.0 |
| RB 3 asia 15m vwz[2.0] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 1747 | 0.3 | -12.5 | -11.6 | 12.8 | 0.01 / -0.56 / -0.52 | 22.9 / 10.1 |
| RB 4 asia 5m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 2332 | -10.0 | -21.6 | -20.7 | 11.6 | -0.42 / -0.91 / -0.87 | 24.7 / 13.3 |
| RB 5 asia 15m rsi[14, 30] exit=bracket0.5xSR | negative pre-2023 | 497 | -7.8 | -19.4 | -18.4 | 11.6 | -0.17 / -0.42 / -0.40 | 34.6 / 22.9 |
| RB 6 lon 30m rsi[14, 30] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 1011 | 4.1 | -8.7 | -7.5 | 12.8 | 0.11 / -0.24 / -0.21 | 57.8 / 45.0 |
| RB 7 lon 30m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1216 | -0.4 | -12.0 | -11.0 | 11.6 | -0.01 / -0.23 / -0.21 | 54.1 / 42.6 |
| RB 8 lon 30m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 2235 | -9.2 | -20.1 | -19.2 | 10.9 | -0.43 / -0.92 / -0.88 | 27.0 / 16.4 |
| RB 9 lon 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 973 | 2.2 | -8.7 | -7.6 | 10.9 | 0.06 / -0.25 / -0.22 | 42.4 / 31.8 |
| RB 10 lon 30m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1208 | 0.6 | -12.1 | -11.0 | 12.8 | 0.01 / -0.24 / -0.21 | 52.1 / 39.3 |
| NG 1 (diag) asia 30m st[14, 2.0] exit=trail0.5xSR | negative pre-2023 | 376 | -4.4 | -28.8 | -33.8 | 24.4 | -0.13 / -0.82 / -0.96 | 22.1 / -2.2 |
| NG 2 (diag) asia 30m st[14, 2.0] exit=trail0.25xSR | negative pre-2023 | 376 | -5.0 | -29.4 | -34.4 | 24.4 | -0.22 / -1.27 / -1.47 | 15.9 / -8.4 |
| NG 3 (diag) asia 30m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1148 | 6.6 | -17.8 | -22.2 | 24.4 | 0.40 / -1.07 / -1.33 | 13.6 / -10.8 |
| NG 4 lon 5m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 2800 | 5.8 | -15.1 | -19.0 | 21.0 | 0.24 / -0.62 / -0.77 | 31.9 / 11.4 |
| NG 5 lon 15m rsi[14, 30] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1620 | 2.8 | -21.5 | -25.9 | 24.4 | 0.10 / -0.75 / -0.89 | 37.9 / 13.5 |
| NG 6 lon 15m rsi[14, 30] exit=bracket0.5xSR | positive pre-2023 | 1557 | 24.9 | 3.9 | 0.1 | 21.0 | 0.79 / 0.12 / 0.00 | 28.4 / 7.6 |
| NG 7 lon 30m vwz[2.0] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 1220 | 1.2 | -23.1 | -27.8 | 24.4 | 0.03 / -0.63 / -0.75 | 28.1 / 3.8 |
| NG 8 (diag) lon 30m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1215 | -0.7 | -21.8 | -25.7 | 21.1 | -0.02 / -0.59 / -0.69 | 26.0 / 5.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): HG: 5 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 0.08, p(top) = 0.72); HO: 17 cells pass the clean rule against a replicate mean of 10.4 (p(count) = 0.00, p(top) = 0.14); NG: 4 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.00, p(top) = 0.19); PL: 3 cells pass the clean rule against a replicate mean of 4.1 (p(count) = 0.79, p(top) = 0.29); RB: 29 cells pass the clean rule against a replicate mean of 5.1 (p(count) = 0.00, p(top) = 0.02); SI: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00).
- Of 30 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.36 (RB lon 30m vwz[2.0] exit=bracket0.5xSR); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 15, 'negative pre-2023': 14, 'positive pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat. Overnight liquidity (Asia) is thin for ZN/RTY/CL; slippage of 1 tick may be optimistic there.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q4b.py (= ap_b10.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q4b/ (`Q4B_CO_all_selected_scored.csv`).

DONE Q4B
