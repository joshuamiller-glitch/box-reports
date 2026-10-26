# REPORT B10 - overnight-session specialists (Asia and London windows) with session-scaled brackets

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 35 selected cells (+26 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.17; best pair-window standalone Sharpe +1.23.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Windows (ET): Asia entries 19:00-01:30 flat 02:00; London entries 02:30-07:30 flat 08:25. Strategies: ST(14,2), EMA 9/21, Donchian 20, window opening-range breakout (first 30 min), VWAP-z 2.0 fade, RSI(14,30) fade. Exits: bracket stop=target or trail at 0.25/0.5 x SR (SR = the window's own 20-day mean range).
- Instruments: ES, RTY, GC, CL, ZN, YM, BTC. Grid: 144 cells per instrument = 2 windows x 3 bar sizes x 6 strategies x 4 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 5 per instrument per window (Asia, London separately) by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     144 |        144 |        30 |               1.42  |                2 |         10 |            0 |
| CL    |     144 |        140 |         6 |               0.736 |                2 |          6 |            4 |
| ES    |     144 |        136 |         6 |               0.911 |                2 |          5 |            3 |
| GC    |     144 |        144 |         3 |               1.106 |                2 |          3 |            6 |
| RTY   |     144 |        136 |         2 |               0.729 |                2 |          2 |            6 |
| YM    |     144 |        136 |         9 |               1.322 |                2 |          9 |            1 |
| ZN    |     144 |        140 |         0 |              -2.197 |                0 |          0 |            6 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    6 |            0.84  |               4 |      0     |                       0.385 |            0.504 |           1.022 |    0.365 |       0.614 |                1.177 |
| RTY   |     200 |                    2 |            2.385 |               8 |      0.68  |                       0.687 |            0.57  |           0.956 |    0.28  |       0.729 |                1.397 |
| GC    |     200 |                    3 |            4.52  |              10 |      0.845 |                       0.714 |            0.579 |           0.931 |    0.215 |       1.071 |                1.621 |
| CL    |     200 |                    6 |            1.155 |               5 |      0     |                       0.426 |            0.497 |           1.07  |    0.395 |       0.736 |                1.185 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| YM    |     200 |                    9 |            1.91  |               6 |      0     |                       0.766 |            0.539 |           0.952 |    0.155 |       1.322 |                1.35  |
| BTC   |     200 |                   30 |           17.12  |              28 |      0     |                       0.888 |            0.875 |           1.092 |    0.435 |       1.42  |                1.896 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | asia 15m emax[9, 21] exit=bracket0.5xSR | 296 | 1 | 0.56 | -1.75 | 0.31 | 0.13 / 0.70 | 0.05 / -0.50 / 0.21 | -0.17 | -0.11 | 0.99 | -0.26 | 0.17 | 510 | diag |
| ES 2 (diag) | asia 15m emax[9, 21] exit=bracket0.25xSR | 364 | 1 | 0.41 | -2.20 | 0.04 | -0.41 / -0.38 | 0.04 / -0.64 / 0.08 | -0.27 | 0.00 | 1.00 | -0.27 | 0.00 | 624 | diag |
| ES 3 (diag) | asia 15m emax[9, 21] exit=trail0.5xSR | 315 | 1 | 0.22 | -2.17 | 0.04 | -0.10 / 0.37 | -0.01 / 0.14 / -0.23 | -0.27 | -0.13 | 0.99 | -0.29 | 0.00 | 547 | diag |
| ES 4 | lon 15m vwz[2.0] exit=bracket0.5xSR | 405 | 2 | 0.61 | -1.24 | 0.12 | -0.72 / 0.72 | 0.07 / 0.01 / -0.24 | -0.12 | 0.09 | 0.94 | -0.20 | 0.00 | 576 | NO |
| ES 5 | lon 15m vwz[2.0] exit=trail0.5xSR | 410 | 2 | 0.54 | -1.38 | -0.26 | -2.01 / 0.46 | 0.09 / -0.11 / -0.45 | -0.18 | -0.15 | 0.89 | -0.23 | 0.00 | 594 | NO |
| ES 6 | lon 5m vwz[2.0] exit=trail0.5xSR | 515 | 2 | 0.34 | -1.31 | -0.02 | -0.67 / 0.44 | 0.06 / 0.10 / -0.22 | -0.12 | 0.21 | 0.96 | -0.17 | 0.25 | 755 | NO |
| ES 7 | lon 15m rsi[14, 30] exit=trail0.5xSR | 271 | 2 | 0.25 | -1.13 | -0.04 | -0.44 / 0.34 | 0.04 / -0.23 / -0.15 | -0.16 | -0.42 | 0.96 | -0.24 | 0.00 | 438 | NO |
| ES 8 | lon 30m vwz[2.0] exit=bracket0.5xSR | 298 | 2 | 0.18 | -0.74 | -0.29 | -1.13 / 0.47 | 0.01 / 0.07 / -0.36 | -0.16 | 0.16 | 0.82 | -0.23 | 0.00 | 424 | NO |
| RTY 1 | asia 15m st[14, 2.0] exit=bracket0.5xSR | 225 | 2 | 0.65 | -1.19 | -0.29 | -0.94 / 0.39 | 0.10 / -0.38 / -0.63 | -0.24 | -0.30 | 0.96 | -0.45 | 0.00 | 406 | NO |
| RTY 2 (diag) | asia 15m st[14, 2.0] exit=trail0.5xSR | 231 | 1 | 0.62 | -1.70 | 0.03 | -0.31 / 0.22 | 0.09 / -0.26 / -0.38 | -0.18 | -0.31 | 0.99 | -0.35 | 0.00 | 422 | diag |
| RTY 3 (diag) | asia 15m rsi[14, 30] exit=trail0.5xSR | 126 | 1 | 0.45 | -0.41 | 0.02 | -0.74 / 0.32 | 0.03 / -0.34 / 0.07 | -0.07 | -0.16 | 0.96 | -0.16 | 0.00 | 217 | diag |
| RTY 4 (diag) | asia 15m rsi[14, 30] exit=bracket0.5xSR | 118 | 1 | 0.30 | -0.17 | -0.01 | -0.34 / 0.81 | 0.06 / -0.41 / 0.17 | -0.05 | -0.16 | 0.99 | -0.18 | 0.17 | 200 | diag |
| RTY 5 | lon 15m rsi[14, 30] exit=bracket0.25xSR | 332 | 2 | 0.73 | -0.80 | -0.02 | -1.04 / 0.26 | 0.12 / 0.36 / -0.43 | -0.09 | -0.27 | 1.00 | -0.18 | 0.17 | 487 | NO |
| RTY 6 (diag) | lon 30m rsi[14, 30] exit=bracket0.25xSR | 158 | 1 | 0.39 | -0.75 | 0.46 | 0.57 / 0.78 | 0.05 / 0.05 / 0.21 | 0.02 | 0.00 | 0.98 | -0.11 | 0.17 | 231 | diag |
| RTY 7 (diag) | lon 5m vwz[2.0] exit=trail0.5xSR | 525 | 1 | 0.16 | -1.16 | 0.13 | 0.10 / 0.33 | 0.03 / 0.09 / -0.07 | -0.07 | -0.13 | 0.96 | -0.17 | 0.25 | 799 | diag |
| RTY 8 (diag) | lon 5m vwz[2.0] exit=bracket0.5xSR | 517 | 1 | -0.02 | -0.80 | -0.10 | -0.20 / 0.74 | -0.02 / 0.02 / -0.04 | -0.11 | -0.37 | 0.90 | -0.21 | 0.00 | 796 | diag |
| GC 1 | asia 30m st[14, 2.0] exit=bracket0.5xSR | 239 | 2 | 1.07 | -0.92 | -0.06 | -0.56 / 1.38 | 0.11 / -0.21 / -1.20 | -0.32 | 0.18 | 0.75 | -0.73 | 0.00 | 419 | NO |
| GC 2 (diag) | asia 5m orb[30] exit=bracket0.5xSR | 512 | 1 | 1.11 | -1.34 | 0.98 | 1.13 / 0.94 | 0.14 / 0.34 / 0.42 | 0.19 | -0.25 | 1.00 | -0.09 | 0.50 | 820 | diag |
| GC 3 (diag) | asia 30m st[14, 2.0] exit=bracket0.25xSR | 247 | 1 | 1.09 | -1.10 | 0.57 | 0.30 / 1.38 | 0.14 / -0.02 / -0.18 | -0.02 | 0.50 | 0.95 | -0.23 | 0.50 | 436 | diag |
| GC 4 (diag) | asia 5m orb[30] exit=trail0.5xSR | 512 | 1 | 1.07 | -1.58 | 0.96 | 1.14 / 1.35 | 0.11 / 0.50 / 0.27 | 0.14 | -0.24 | 0.97 | -0.13 | 0.75 | 820 | diag |
| GC 5 | lon 5m orb[30] exit=bracket0.5xSR | 512 | 2 | 0.74 | -0.60 | -0.08 | -0.55 / 1.28 | 0.07 / -0.09 / -0.64 | -0.18 | -0.36 | 0.66 | -0.45 | 0.00 | 819 | NO |
| GC 6 | lon 30m orb[30] exit=bracket0.5xSR | 506 | 2 | 0.33 | -0.27 | -0.55 | -1.25 / 1.51 | 0.00 / -0.80 / -0.88 | -0.37 | -0.21 | 0.28 | -0.62 | 0.00 | 807 | NO |
| GC 7 (diag) | lon 30m emax[9, 21] exit=bracket0.5xSR | 206 | 1 | 0.46 | -0.50 | -0.68 | -1.42 / 0.95 | 0.02 / -0.83 / -1.17 | -0.45 | -0.10 | 0.24 | -0.78 | 0.00 | 300 | diag |
| GC 8 (diag) | lon 5m don[20] exit=bracket0.5xSR | 833 | 1 | 0.19 | -1.02 | -1.26 | -2.40 / 0.98 | 0.01 / -1.78 / -1.22 | -0.63 | -0.40 | 0.09 | -0.90 | 0.00 | 1337 | diag |
| GC 9 (diag) | lon 15m orb[30] exit=bracket0.25xSR | 510 | 1 | 0.18 | -0.81 | -0.68 | -1.38 / 1.37 | 0.02 / -0.77 / -0.76 | -0.37 | -0.22 | 0.38 | -0.58 | 0.00 | 815 | diag |
| CL 1 | asia 30m vwz[2.0] exit=bracket0.5xSR | 285 | 2 | 0.48 | -0.68 | -0.07 | -0.48 / 0.79 | 0.05 / 0.09 / -0.51 | -0.25 | -0.02 | 0.95 | -0.37 | 0.00 | 453 | NO |
| CL 2 | asia 30m emax[9, 21] exit=bracket0.25xSR | 133 | 2 | 0.27 | -0.59 | -0.23 | -0.43 / 0.19 | 0.03 / -0.41 / -0.93 | -0.48 | -0.24 | 0.99 | -0.75 | 0.00 | 268 | NO |
| CL 3 (diag) | asia 30m emax[9, 21] exit=trail0.5xSR | 130 | 1 | 0.16 | -1.01 | -0.06 | -0.11 / 0.58 | -0.00 / -0.13 / -0.59 | -0.34 | -0.09 | 1.00 | -0.53 | 0.00 | 254 | diag |
| CL 4 (diag) | asia 5m orb[30] exit=bracket0.5xSR | 515 | 1 | 0.10 | -1.10 | -0.33 | -0.67 / 1.06 | 0.03 / -0.08 / -0.82 | -0.38 | 0.11 | 0.78 | -0.48 | 0.00 | 821 | diag |
| CL 5 (diag) | asia 15m rsi[14, 30] exit=bracket0.5xSR | 152 | 1 | 0.07 | -0.04 | 0.07 | 0.09 / 0.45 | 0.01 / 0.10 / -0.54 | -0.24 | -0.02 | 1.00 | -0.43 | 0.00 | 272 | diag |
| CL 6 | lon 5m orb[30] exit=bracket0.5xSR | 517 | 2 | 0.74 | -1.15 | 0.51 | 0.52 / 1.20 | 0.04 / -0.39 / 0.23 | -0.09 | -0.03 | 0.96 | -0.22 | 0.50 | 826 | NO |
| CL 7 | lon 15m orb[30] exit=bracket0.5xSR | 517 | 2 | 0.62 | -1.20 | 0.16 | -0.23 / 0.82 | 0.02 / -0.41 / 0.10 | -0.13 | 0.08 | 0.89 | -0.25 | 0.00 | 825 | NO |
| CL 8 | lon 15m rsi[14, 30] exit=trail0.5xSR | 382 | 2 | 0.26 | -0.90 | 0.20 | 0.15 / 1.04 | 0.09 / -0.04 / -0.37 | -0.17 | -0.14 | 0.93 | -0.34 | 0.00 | 587 | NO |
| CL 9 | lon 15m orb[30] exit=bracket0.25xSR | 517 | 2 | 0.20 | -1.47 | -0.03 | -0.19 / 0.67 | -0.04 / -0.41 / -0.23 | -0.30 | -0.00 | 0.95 | -0.38 | 0.00 | 825 | NO |
| CL 10 (diag) | lon 30m rsi[14, 30] exit=bracket0.5xSR | 203 | 1 | 0.22 | -0.57 | -0.47 | -1.19 / 1.14 | 0.01 / -0.46 / -0.74 | -0.31 | -0.02 | 0.53 | -0.48 | 0.00 | 314 | diag |
| ZN 1 (diag) | asia 30m rsi[14, 30] exit=bracket0.25xSR | 88 | 0 | -2.20 | -2.47 | -2.44 | -2.78 / -6.38 | -0.46 / -0.13 / -0.77 | -0.76 | -0.10 | 1.00 | -0.71 | 0.00 | 135 | diag |
| ZN 2 (diag) | asia 30m rsi[14, 30] exit=bracket0.5xSR | 82 | 0 | -2.24 | -1.89 | -2.31 | -2.42 / -5.84 | -0.47 / -0.38 / -0.47 | -0.68 | -0.18 | 1.00 | -0.67 | 0.00 | 127 | diag |
| ZN 3 (diag) | asia 15m rsi[14, 30] exit=bracket0.5xSR | 135 | 0 | -2.56 | -2.80 | -3.04 | -4.10 / -6.78 | -0.52 / -0.72 / -0.71 | -0.89 | 0.46 | 1.00 | -0.79 | 0.00 | 212 | diag |
| ZN 4 (diag) | lon 30m rsi[14, 30] exit=bracket0.5xSR | 137 | 0 | -2.67 | -1.73 | -2.37 | -1.84 / -3.33 | -0.55 / -0.29 / -0.41 | -0.80 | -0.21 | 1.00 | -0.68 | 0.00 | 214 | diag |
| ZN 5 (diag) | lon 5m orb[30] exit=bracket0.5xSR | 509 | 0 | -2.79 | -4.07 | -4.16 | -7.30 / -2.85 | -0.60 / -1.23 / -0.94 | -1.31 | 0.18 | 0.20 | -0.96 | 0.00 | 816 | diag |
| ZN 6 (diag) | lon 30m rsi[14, 30] exit=bracket0.25xSR | 154 | 0 | -3.16 | -2.39 | -2.76 | -2.14 / -5.75 | -0.63 / -0.25 / -0.57 | -0.95 | -0.05 | 1.00 | -0.77 | 0.00 | 242 | diag |
| YM 1 | asia 15m emax[9, 21] exit=bracket0.5xSR | 304 | 2 | 1.32 | -1.50 | 0.79 | 0.19 / 0.38 | 0.16 / -0.49 / 0.14 | -0.05 | 0.26 | 1.00 | -0.11 | 0.33 | 501 | NO |
| YM 2 | asia 15m st[14, 2.0] exit=bracket0.5xSR | 166 | 2 | 1.08 | -1.24 | -0.21 | -1.12 / 0.24 | 0.16 / -0.47 / -0.93 | -0.28 | -0.24 | 0.95 | -0.47 | 0.00 | 324 | NO |
| YM 3 | asia 15m rsi[14, 30] exit=trail0.5xSR | 104 | 2 | 0.65 | -0.58 | -0.22 | -1.36 / 0.14 | 0.06 / -0.49 / -0.44 | -0.17 | 0.48 | 0.97 | -0.31 | 0.00 | 183 | NO |
| YM 4 | asia 15m rsi[14, 30] exit=bracket0.5xSR | 100 | 2 | 0.58 | -0.61 | -0.44 | -1.72 / 0.44 | 0.08 / -0.66 / -0.54 | -0.21 | 0.36 | 0.84 | -0.37 | 0.00 | 174 | NO |
| YM 5 (diag) | asia 15m st[14, 2.0] exit=trail0.5xSR | 169 | 1 | 0.71 | -1.52 | 0.00 | -0.46 / 0.61 | 0.11 / -0.15 / -0.80 | -0.25 | -0.20 | 0.99 | -0.39 | 0.00 | 333 | diag |
| YM 6 | lon 5m emax[9, 21] exit=trail0.5xSR | 665 | 2 | 0.77 | -0.57 | 0.81 | 0.86 / 2.07 | 0.16 / 0.37 / -0.09 | 0.06 | 0.37 | 0.97 | -0.06 | 0.67 | 1050 | NO |
| YM 7 | lon 30m rsi[14, 30] exit=trail0.25xSR | 149 | 2 | 0.76 | -0.68 | 0.14 | -0.65 / 0.99 | 0.15 / 0.19 / -0.57 | -0.08 | -0.49 | 0.98 | -0.19 | 0.00 | 240 | NO |
| YM 8 | lon 30m rsi[14, 30] exit=trail0.5xSR | 133 | 2 | 0.60 | -0.51 | -0.56 | -1.68 / 1.41 | 0.09 / 0.28 / -1.38 | -0.28 | -0.22 | 0.22 | -0.46 | 0.00 | 219 | NO |
| YM 9 | lon 30m rsi[14, 30] exit=bracket0.25xSR | 142 | 2 | 0.60 | -0.54 | -0.21 | -1.01 / 0.67 | 0.14 / 0.34 / -0.91 | -0.15 | -0.44 | 0.86 | -0.31 | 0.00 | 230 | NO |
| YM 10 | lon 30m rsi[14, 30] exit=bracket0.5xSR | 129 | 2 | 0.53 | -0.09 | -0.11 | -0.69 / 0.89 | 0.06 / 0.24 / -0.91 | -0.18 | -0.15 | 0.78 | -0.38 | 0.00 | 211 | NO |
| BTC 1 | asia 15m emax[9, 21] exit=trail0.5xSR | 344 | 2 | 1.42 | -0.91 | 1.23 | 0.87 / 1.13 | 0.20 / 0.52 / -0.07 | 0.13 | 0.19 | 0.99 | 0.01 | 1.00 | 552 | NO |
| BTC 2 | asia 30m st[14, 2.0] exit=trail0.5xSR | 192 | 2 | 1.13 | 0.03 | 0.95 | 0.55 / 1.28 | 0.18 / 0.30 / -0.19 | 0.09 | 0.12 | 0.96 | -0.03 | 0.67 | 344 | NO |
| BTC 3 | asia 15m emax[9, 21] exit=bracket0.5xSR | 324 | 2 | 1.00 | -1.65 | 0.80 | 0.47 / 1.12 | 0.14 / 0.09 / -0.19 | 0.03 | 0.36 | 0.99 | -0.14 | 1.00 | 521 | NO |
| BTC 4 | asia 5m emax[9, 21] exit=trail0.5xSR | 641 | 2 | 0.97 | 2.05 | 0.37 | -0.38 / 1.33 | 0.09 / 0.71 / -0.36 | -0.02 | 0.01 | 0.71 | -0.15 | 0.67 | 1002 | NO |
| BTC 5 | asia 30m st[14, 2.0] exit=bracket0.5xSR | 191 | 2 | 0.69 | 0.49 | 0.79 | 0.88 / 1.12 | 0.10 / 0.40 / -0.30 | 0.03 | 0.27 | 0.98 | -0.13 | 0.33 | 337 | NO |
| BTC 6 | lon 15m don[20] exit=trail0.25xSR | 575 | 2 | 0.88 | -0.45 | 0.33 | -0.53 / 0.92 | 0.10 / -0.36 / -0.17 | -0.12 | -0.15 | 0.95 | -0.20 | 0.00 | 903 | NO |
| BTC 7 | lon 15m don[20] exit=bracket0.25xSR | 627 | 2 | 0.80 | 0.00 | -0.01 | -1.42 / 0.11 | 0.08 / -0.60 / -0.13 | -0.15 | -0.05 | 0.98 | -0.24 | 0.00 | 988 | NO |
| BTC 8 | lon 15m orb[30] exit=trail0.25xSR | 460 | 2 | 0.76 | -1.32 | 0.61 | 0.59 / 1.24 | 0.11 / -0.10 / 0.14 | 0.01 | -0.25 | 0.93 | -0.08 | 0.75 | 722 | NO |
| BTC 9 | lon 5m don[20] exit=bracket0.5xSR | 865 | 2 | 0.65 | -0.40 | -0.02 | -1.06 / 1.29 | 0.06 / -0.10 / -0.35 | -0.12 | -0.32 | 0.86 | -0.23 | 0.00 | 1349 | NO |
| BTC 10 | lon 5m orb[30] exit=trail0.5xSR | 485 | 2 | 0.59 | -0.81 | 0.69 | 0.96 / 1.18 | 0.06 / 0.12 / 0.08 | 0.03 | -0.21 | 0.97 | -0.09 | 0.00 | 753 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 35 |
| diagnostic cells read | 26 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 39 |
| worst-decile corr <= +0.30 | 55 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC asia 15m emax[9, 21] exit=trail0.5xSR | clean | 1.44 | 3.56 | -81845 | -64435 | 283083 | -125421 | 4.60 | 48.6 | 1.66 | -86911 | 247891 | -92118 |
| BTC asia 15m emax[9, 21] exit=trail0.5xSR | H1 | 2.14 | 5.76 | -66902 | -57153 | 176124 | -94332 | 3.01 | 46.4 | 3.35 | -62028 | 150929 | -78464 |
| BTC asia 15m emax[9, 21] exit=trail0.5xSR | H2 | -0.21 | -0.30 | -111678 | -95912 | 393742 | -134574 | -0.15 | 58.3 | 2.22 | -94414 | 223335 | -94903 |
| BTC asia 15m emax[9, 21] exit=trail0.5xSR | all | 1.23 | 2.66 | -94484 | -76658 | 393742 | -134574 | 4.50 | 50.6 | 2.03 | -88599 | 247891 | -94903 |
| CL lon 5m orb[30] exit=bracket0.5xSR | clean | 0.56 | 0.81 | -127827 | -107400 | 607275 | -177141 | 0.84 | 42.9 | 1.50 | -91651 | 274949 | -100265 |
| CL lon 5m orb[30] exit=bracket0.5xSR | H1 | -1.54 | -1.79 | -152194 | -130197 | 398118 | -179412 | -0.92 | 57.1 | 2.43 | -78350 | 177051 | -81811 |
| CL lon 5m orb[30] exit=bracket0.5xSR | H2 | 1.22 | 2.32 | -223775 | -193303 | 814916 | -247037 | 1.13 | 52.8 | 2.52 | -87567 | 232081 | -89064 |
| CL lon 5m orb[30] exit=bracket0.5xSR | all | 0.51 | 0.83 | -171943 | -142142 | 1297455 | -247037 | 0.82 | 47.0 | 1.88 | -90001 | 274949 | -100265 |
| ES lon 5m vwz[2.0] exit=trail0.5xSR | clean | 0.35 | 0.56 | -121645 | -95504 | 531155 | -191245 | 0.60 | 51.4 | 1.52 | -86806 | 289078 | -90319 |
| ES lon 5m vwz[2.0] exit=trail0.5xSR | H1 | 0.33 | 0.61 | -67253 | -62164 | 193306 | -82055 | 0.34 | 53.6 | 2.93 | -80701 | 140551 | -83115 |
| ES lon 5m vwz[2.0] exit=trail0.5xSR | H2 | -1.35 | -1.71 | -127217 | -107145 | 630826 | -160706 | -0.64 | 61.1 | 2.08 | -88993 | 210571 | -92346 |
| ES lon 5m vwz[2.0] exit=trail0.5xSR | all | -0.02 | -0.02 | -119167 | -98674 | 665482 | -191245 | -0.03 | 54.2 | 1.86 | -86927 | 289078 | -92346 |
| GC lon 5m orb[30] exit=bracket0.5xSR | clean | 0.59 | 0.93 | -126576 | -103238 | 525233 | -159324 | 1.03 | 45.7 | 1.53 | -90042 | 313872 | -109018 |
| GC lon 5m orb[30] exit=bracket0.5xSR | H1 | 0.24 | 0.36 | -265455 | -217154 | 647835 | -347216 | 0.20 | 50.0 | 2.73 | -81292 | 178154 | -95827 |
| GC lon 5m orb[30] exit=bracket0.5xSR | H2 | -1.06 | -1.42 | -292111 | -285908 | 1457269 | -294015 | -0.60 | 63.9 | 1.65 | -99505 | 177077 | -114895 |
| GC lon 5m orb[30] exit=bracket0.5xSR | all | -0.08 | -0.12 | -245960 | -196579 | 2098890 | -347216 | -0.10 | 50.0 | 1.75 | -92788 | 313872 | -114895 |
| RTY lon 15m rsi[14, 30] exit=bracket0.25xSR | clean | 0.73 | 1.15 | -111615 | -98265 | 538250 | -123535 | 1.22 | 49.5 | 1.58 | -85147 | 211702 | -98883 |
| RTY lon 15m rsi[14, 30] exit=bracket0.25xSR | H1 | 0.91 | 1.48 | -95344 | -90184 | 192133 | -101436 | 1.10 | 39.3 | 3.19 | -59464 | 128020 | -69274 |
| RTY lon 15m rsi[14, 30] exit=bracket0.25xSR | H2 | -2.20 | -2.34 | -258588 | -187196 | 1180799 | -302536 | -0.76 | 63.9 | 1.87 | -78260 | 234886 | -78390 |
| RTY lon 15m rsi[14, 30] exit=bracket0.25xSR | all | -0.02 | -0.03 | -146280 | -120425 | 1252357 | -302536 | -0.02 | 51.2 | 1.87 | -82832 | 234886 | -98883 |
| YM lon 5m emax[9, 21] exit=trail0.5xSR | clean | 0.78 | 1.52 | -96983 | -76989 | 415589 | -157417 | 1.70 | 52.4 | 1.62 | -86611 | 248727 | -93048 |
| YM lon 5m emax[9, 21] exit=trail0.5xSR | H1 | 2.85 | 5.05 | -85319 | -80450 | 182425 | -89132 | 3.32 | 25.0 | 3.20 | -75394 | 156656 | -75833 |
| YM lon 5m emax[9, 21] exit=trail0.5xSR | H2 | 0.06 | 0.09 | -192622 | -153805 | 432812 | -214032 | 0.07 | 44.4 | 2.21 | -95409 | 224053 | -101825 |
| YM lon 5m emax[9, 21] exit=trail0.5xSR | all | 0.81 | 1.39 | -129754 | -105467 | 432812 | -214032 | 3.10 | 46.4 | 2.01 | -88740 | 248727 | -101825 |
| ZN asia 30m rsi[14, 30] exit=bracket0.5xSR (diag) | clean | -2.25 | -2.30 | -190829 | -157264 | 2168886 | -279660 | -0.94 | 35.2 | 0.99 | -88723 | 437673 | -96204 |
| ZN asia 30m rsi[14, 30] exit=bracket0.5xSR (diag) | H1 | -2.49 | -2.48 | -118254 | -105463 | 473533 | -150368 | -0.82 | 25.0 | 2.45 | -77959 | 152251 | -78287 |
| ZN asia 30m rsi[14, 30] exit=bracket0.5xSR (diag) | H2 | -2.44 | -2.54 | -192656 | -148007 | 869377 | -199881 | -0.86 | 44.4 | 1.82 | -83758 | 215620 | -90370 |
| ZN asia 30m rsi[14, 30] exit=bracket0.5xSR (diag) | all | -2.31 | -2.36 | -186740 | -151454 | 3366943 | -279660 | -0.94 | 35.7 | 1.39 | -86514 | 437673 | -96204 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES lon 5m vwz[2.0] exit=trail0.5xSR | -30.3 | -9.5 | 12.2 | 24.5 | 10.5 / 13.8 | 19.4 / 24.0 | NO |
| RTY lon 15m rsi[14, 30] exit=bracket0.25xSR | -30.3 | -5.1 | 20.0 | 34.0 | -5.9 / 14.4 | 42.7 / 44.5 | NO |
| GC lon 5m orb[30] exit=bracket0.5xSR | -32.3 | -48.6 | -6.9 | -30.0 | -24.3 / 7.0 | -56.6 / -21.4 | NO |
| CL lon 5m orb[30] exit=bracket0.5xSR | -18.1 | -7.5 | 7.1 | 5.7 | -8.3 / 3.3 | 7.7 / 14.0 | NO |
| ZN asia 30m rsi[14, 30] exit=bracket0.5xSR (diag) | -65.5 | -12.2 | 4.8 | -67.5 | -13.1 / -2.4 | 19.3 / 23.9 | NO |
| YM lon 5m emax[9, 21] exit=trail0.5xSR | -15.0 | -8.7 | 9.0 | 37.3 | 4.9 / 14.8 | 27.5 / 29.8 | NO |
| BTC asia 15m emax[9, 21] exit=trail0.5xSR | -10.2 | 2.3 | 11.9 | 34.2 | 6.7 / 14.2 | 28.3 / 41.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) asia 15m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 1663 | -12.8 | -39.7 | -26.7 | 26.9 | -0.58 / -1.75 / -1.19 | 40.5 / 13.8 |
| ES 2 (diag) asia 15m emax[9, 21] exit=bracket0.25xSR | negative pre-2023 | 2039 | -6.3 | -31.1 | -19.0 | 24.8 | -0.48 / -2.20 / -1.38 | 31.3 / 7.5 |
| ES 3 (diag) asia 15m emax[9, 21] exit=trail0.5xSR | negative pre-2023 | 1805 | -17.5 | -46.9 | -32.6 | 29.4 | -0.84 / -2.17 / -1.53 | 33.8 / 4.5 |
| ES 4 lon 15m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1611 | -12.2 | -38.5 | -26.0 | 26.3 | -0.40 / -1.24 / -0.84 | 47.6 / 22.2 |
| ES 5 lon 15m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1654 | -9.3 | -38.6 | -24.7 | 29.4 | -0.33 / -1.38 / -0.88 | 50.3 / 21.0 |
| ES 6 lon 5m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 2304 | -5.1 | -34.5 | -20.4 | 29.4 | -0.20 / -1.31 / -0.78 | 42.5 / 13.2 |
| ES 7 lon 15m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 1438 | -3.5 | -32.9 | -18.7 | 29.4 | -0.12 / -1.13 / -0.65 | 40.1 / 10.7 |
| ES 8 lon 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1184 | 2.5 | -23.9 | -11.5 | 26.4 | 0.08 / -0.74 / -0.36 | 32.4 / 6.6 |
| RTY 1 asia 15m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 743 | -10.1 | -23.4 | -21.4 | 13.3 | -0.53 / -1.19 / -1.09 | 22.9 / 9.6 |
| RTY 2 (diag) asia 15m st[14, 2.0] exit=trail0.5xSR | negative pre-2023 | 772 | -19.3 | -33.7 | -31.4 | 14.4 | -0.99 / -1.70 / -1.59 | 23.7 / 9.3 |
| RTY 3 (diag) asia 15m rsi[14, 30] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 429 | 4.0 | -10.4 | -8.1 | 14.4 | 0.16 / -0.41 / -0.32 | 30.5 / 16.2 |
| RTY 4 (diag) asia 15m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 393 | 8.4 | -4.6 | -2.5 | 13.0 | 0.32 / -0.17 / -0.09 | 19.2 / 6.3 |
| RTY 5 lon 15m rsi[14, 30] exit=bracket0.25xSR | negative pre-2023 | 859 | -0.4 | -12.6 | -10.8 | 12.2 | -0.03 / -0.80 / -0.69 | 21.4 / 9.6 |
| RTY 6 (diag) lon 30m rsi[14, 30] exit=bracket0.25xSR | negative pre-2023 | 380 | -4.4 | -16.6 | -14.7 | 12.2 | -0.20 / -0.75 / -0.66 | 20.2 / 8.4 |
| RTY 7 (diag) lon 5m vwz[2.0] exit=trail0.5xSR | negative pre-2023 | 1254 | -8.2 | -22.5 | -20.4 | 14.4 | -0.42 / -1.16 / -1.05 | 17.5 / 3.1 |
| RTY 8 (diag) lon 5m vwz[2.0] exit=bracket0.5xSR | negative pre-2023 | 1217 | -3.2 | -16.2 | -14.3 | 13.0 | -0.16 / -0.80 / -0.71 | 12.3 / -0.6 |
| GC 1 asia 30m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 1018 | -6.3 | -28.8 | -19.9 | 22.4 | -0.20 / -0.92 / -0.64 | 90.1 / 68.1 |
| GC 2 (diag) asia 5m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2644 | -10.8 | -31.8 | -23.4 | 21.1 | -0.46 / -1.34 / -0.99 | 77.9 / 57.4 |
| GC 3 (diag) asia 30m st[14, 2.0] exit=bracket0.25xSR | negative pre-2023 | 1032 | -3.1 | -23.3 | -15.3 | 20.2 | -0.16 / -1.10 / -0.74 | 69.7 / 50.1 |
| GC 4 (diag) asia 5m orb[30] exit=trail0.5xSR | negative pre-2023 | 2644 | -10.2 | -34.5 | -24.7 | 24.4 | -0.47 / -1.58 / -1.13 | 79.9 / 55.6 |
| GC 5 lon 5m orb[30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 2643 | 2.7 | -18.2 | -9.8 | 20.9 | 0.08 / -0.60 / -0.33 | 48.4 / 27.4 |
| GC 6 lon 30m orb[30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 2599 | 12.8 | -8.2 | 0.2 | 21.0 | 0.44 / -0.27 / 0.01 | 36.7 / 15.6 |
| GC 7 (diag) lon 30m emax[9, 21] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1194 | 2.5 | -19.2 | -10.6 | 21.7 | 0.06 / -0.50 / -0.28 | 43.4 / 21.7 |
| GC 8 (diag) lon 5m don[20] exit=bracket0.5xSR | negative pre-2023 | 4163 | -2.4 | -23.6 | -15.2 | 21.1 | -0.12 / -1.02 / -0.66 | 25.1 / 4.2 |
| GC 9 (diag) lon 15m orb[30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 2625 | 5.6 | -13.7 | -6.0 | 19.3 | 0.34 / -0.81 / -0.35 | 24.0 / 4.8 |
| CL 1 asia 30m vwz[2.0] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 1184 | 4.5 | -17.7 | -16.0 | 22.1 | 0.16 / -0.68 / -0.61 | 30.2 / 8.7 |
| CL 2 asia 30m emax[9, 21] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 862 | 7.4 | -12.8 | -10.8 | 20.2 | 0.35 / -0.59 / -0.50 | 21.5 / 1.5 |
| CL 3 (diag) asia 30m emax[9, 21] exit=trail0.5xSR | negative pre-2023 | 804 | -4.8 | -29.2 | -26.8 | 24.4 | -0.17 / -1.01 / -0.93 | 25.2 / 0.9 |
| CL 4 (diag) asia 5m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2636 | -2.6 | -23.7 | -21.4 | 21.1 | -0.12 / -1.10 / -0.99 | 22.3 / 1.8 |
| CL 5 (diag) asia 15m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 749 | 20.5 | -1.2 | 1.4 | 21.7 | 0.66 / -0.04 / 0.05 | 23.2 / 1.8 |
| CL 6 lon 5m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2678 | -15.3 | -36.2 | -33.9 | 20.9 | -0.49 / -1.15 / -1.08 | 36.2 / 15.8 |
| CL 7 lon 15m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2675 | -13.6 | -34.6 | -32.3 | 21.0 | -0.48 / -1.20 / -1.12 | 36.0 / 15.5 |
| CL 8 lon 15m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 1802 | -4.6 | -29.0 | -26.4 | 24.4 | -0.14 / -0.90 / -0.82 | 36.1 / 11.7 |
| CL 9 lon 15m orb[30] exit=bracket0.25xSR | negative pre-2023 | 2675 | -5.1 | -24.6 | -22.5 | 19.5 | -0.31 / -1.47 / -1.34 | 21.9 / 2.8 |
| CL 10 (diag) lon 30m rsi[14, 30] exit=bracket0.5xSR | negative pre-2023 | 910 | -2.4 | -24.4 | -21.8 | 22.1 | -0.05 / -0.57 / -0.51 | 34.3 / 13.0 |
| ZN 1 (diag) asia 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 408 | 2.7 | -25.5 | -29.6 | 28.2 | 0.35 / -2.47 / -2.72 | 9.9 / -17.2 |
| ZN 2 (diag) asia 30m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 412 | 4.7 | -26.8 | -31.4 | 31.5 | 0.38 / -1.89 / -2.15 | 0.4 / -31.0 |
| ZN 3 (diag) asia 15m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 730 | 0.7 | -31.0 | -35.7 | 31.7 | 0.07 / -2.80 / -3.11 | 2.4 / -29.0 |
| ZN 4 (diag) lon 30m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 714 | 4.1 | -26.9 | -31.3 | 30.9 | 0.28 / -1.73 / -1.99 | -1.7 / -33.7 |
| ZN 5 (diag) lon 5m orb[30] exit=bracket0.5xSR | negative pre-2023 | 2677 | -4.1 | -34.8 | -39.3 | 30.7 | -0.51 / -4.07 / -4.56 | 4.9 / -25.3 |
| ZN 6 (diag) lon 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 804 | 3.4 | -24.3 | -28.2 | 27.8 | 0.38 / -2.39 / -2.72 | 3.2 / -25.1 |
| YM 1 asia 15m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 1674 | -14.4 | -27.7 | -22.4 | 13.4 | -0.79 / -1.50 / -1.22 | 32.0 / 18.9 |
| YM 2 asia 15m st[14, 2.0] exit=bracket0.5xSR | negative pre-2023 | 1375 | -13.5 | -26.9 | -21.5 | 13.4 | -0.63 / -1.24 / -1.00 | 33.6 / 20.5 |
| YM 3 asia 15m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 831 | -1.0 | -15.4 | -9.7 | 14.4 | -0.04 / -0.58 / -0.37 | 41.9 / 27.5 |
| YM 4 asia 15m rsi[14, 30] exit=bracket0.5xSR | negative pre-2023 | 783 | -4.5 | -17.7 | -12.4 | 13.1 | -0.16 / -0.61 / -0.43 | 34.8 / 22.0 |
| YM 5 (diag) asia 15m st[14, 2.0] exit=trail0.5xSR | negative pre-2023 | 1429 | -16.9 | -31.3 | -25.6 | 14.4 | -0.83 / -1.52 / -1.24 | 28.8 / 14.4 |
| YM 6 lon 5m emax[9, 21] exit=trail0.5xSR | gross-positive, cost-negative pre-2023 | 3525 | 5.5 | -8.9 | -3.1 | 14.4 | 0.35 / -0.57 / -0.20 | 31.7 / 17.3 |
| YM 7 lon 30m rsi[14, 30] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 784 | 0.7 | -13.7 | -7.8 | 14.4 | 0.03 / -0.68 / -0.39 | 33.6 / 19.3 |
| YM 8 lon 30m rsi[14, 30] exit=trail0.5xSR | negative pre-2023 | 719 | -1.2 | -15.6 | -9.7 | 14.4 | -0.04 / -0.51 / -0.32 | 35.3 / 21.0 |
| YM 9 lon 30m rsi[14, 30] exit=bracket0.25xSR | gross-positive, cost-negative pre-2023 | 744 | 1.2 | -11.0 | -6.0 | 12.2 | 0.06 / -0.54 / -0.30 | 25.0 / 13.3 |
| YM 10 lon 30m rsi[14, 30] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 692 | 9.9 | -3.1 | 2.2 | 13.0 | 0.28 / -0.09 / 0.06 | 33.8 / 21.0 |
| BTC 1 asia 15m emax[9, 21] exit=trail0.5xSR | negative pre-2023 | 235 | -67.3 | -121.7 | -88.8 | 54.4 | -0.51 / -0.91 / -0.67 | 419.6 / 365.2 |
| BTC 2 asia 30m st[14, 2.0] exit=trail0.5xSR | positive pre-2023 | 112 | 58.5 | 4.2 | 37.1 | 54.4 | 0.45 / 0.03 / 0.29 | 461.3 / 406.9 |
| BTC 3 asia 15m emax[9, 21] exit=bracket0.5xSR | negative pre-2023 | 229 | -109.5 | -159.8 | -129.3 | 50.3 | -1.14 / -1.65 / -1.34 | 268.5 / 220.4 |
| BTC 4 asia 5m emax[9, 21] exit=trail0.5xSR | positive pre-2023 | 452 | 243.1 | 188.7 | 221.3 | 54.4 | 2.64 / 2.05 / 2.41 | 183.7 / 129.3 |
| BTC 5 asia 30m st[14, 2.0] exit=bracket0.5xSR | positive pre-2023 | 111 | 107.7 | 59.9 | 89.0 | 47.8 | 0.89 / 0.49 / 0.73 | 220.3 / 170.8 |
| BTC 6 lon 15m don[20] exit=trail0.25xSR | gross-positive, cost-negative pre-2023 | 366 | 26.0 | -28.4 | 3.8 | 54.4 | 0.45 / -0.45 / 0.08 | 135.0 / 80.6 |
| BTC 7 lon 15m don[20] exit=bracket0.25xSR | positive pre-2023 | 397 | 40.9 | -1.0 | 23.9 | 41.9 | 0.88 / 0.00 / 0.52 | 108.2 / 66.3 |
| BTC 8 lon 15m orb[30] exit=trail0.25xSR | negative pre-2023 | 328 | -19.1 | -73.5 | -40.9 | 54.4 | -0.35 / -1.32 / -0.74 | 125.8 / 71.4 |
| BTC 9 lon 5m don[20] exit=bracket0.5xSR | gross-positive, cost-negative pre-2023 | 605 | 22.1 | -24.5 | 3.4 | 46.6 | 0.37 / -0.40 / 0.06 | 110.5 / 64.5 |
| BTC 10 lon 5m orb[30] exit=trail0.5xSR | negative pre-2023 | 348 | -8.6 | -63.0 | -30.3 | 54.4 | -0.11 / -0.81 / -0.39 | 157.9 / 103.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- **Clean-only selection finds a little in-sample structure and none of it carries.** With the clean rule the number of qualifying cells is above chance on ES, CL, YM, BTC (p(count) = 0.00; e.g. ES 6 cells against a replicate mean of 0.8, CL 6 against 1.2) but the top-cell mean Sharpe is at chance everywhere (p(top) 0.16-0.44), and ZN has no qualifying cell. In H1/H2 (read once) 4 of 35 selected cells have an uplift >= +0.10 at 20% in H2 and 11 in H1; none has all three spans at +0.10, the bootstrap lower bound is <= 0 for every non-crypto cell, and the equity/metals/energy cells have H2 uplifts from -1.38 to +0.23 (mostly negative). London-window cells on ES/GC/CL (ORB, VWAP-z, RSI) and Asia-window cells on YM/GC/CL were the strongest in clean (Sharpe 0.5-1.4) and do not hold out of selection.
- BTC (GAPMAP D06 cell) has 30 qualifying cells (replicate mean 17: weak), the best clean Sharpe 1.42 (Asia 15m EMA 9/21 trail 0.5 SR); its uplifts are +0.20 / +0.52 / -0.07 (H2 negative), plateau 1.00 but bootstrap lower bound +0.01 and H2 fails the +0.10 gate: NO. The BTC London ORB cell (BTC 8, +0.11 / -0.10 / +0.14) fails H1.
- ERA flag: of 35 cells 20 'negative pre-2023', 11 'gross-positive, cost-negative pre-2023', 4 'positive pre-2023' (session-timing rules look like the same cost-bound pattern as the daytime families in 2017-22).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat. Overnight liquidity (Asia) is thin for ZN/RTY/CL; slippage of 1 tick may be optimistic there.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_b10.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/b10/ (`B10_CO_all_selected_scored.csv`).

DONE B10
