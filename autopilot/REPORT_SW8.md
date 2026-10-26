# REPORT SW8 - lead-lag catch-up between related instruments (D07 H1/H2)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 24 selected cells (+21 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.31; best pair-window standalone Sharpe +1.55.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: driver X L-minute move minus the target's own L-minute move, both in 1-min-sigma*sqrt(L) units (EWM span 1000), crosses +-k (1.5/2.5): trade the target with (or against) X, exact hold 5/15/30/60 min. Drivers per target: ES {NQ,RTY,YM}, NQ {ES,RTY,YM}, RTY {ES,NQ,YM}, YM {ES,NQ,RTY}, GC {ZN,6E,6J}, CL {GC,ES,ZN}, ZN {ES,6J,6E}, BTC {NQ,ES,GC}; stale driver quotes (>2 min) skipped.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 144 cells per instrument = 3 drivers x 3 L x 2 k x 2 directions x 4 holds.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     144 |        144 |         3 |               1.745 |                2 |          3 |            3 |
| CL    |     144 |        144 |         0 |              -1.018 |                0 |          0 |            3 |
| ES    |     144 |        144 |         5 |               1.278 |                2 |          5 |            3 |
| GC    |     144 |        144 |         0 |              -0.464 |                1 |          0 |            3 |
| NQ    |     144 |        144 |        24 |               2.112 |                2 |         10 |            0 |
| RTY   |     144 |        144 |         6 |               1.12  |                2 |          6 |            3 |
| YM    |     144 |        144 |         0 |               0.523 |                1 |          0 |            3 |
| ZN    |     144 |        144 |         0 |              -6.489 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    5 |             0.13 |               2 |          0 |                       0.593 |            0.685 |           1.197 |     0.06 |       1.278 |                1.507 |
| NQ    |     100 |                   24 |             4.75 |              11 |          0 |                       1.415 |            0.585 |           0.877 |     0    |       2.112 |                1.584 |
| RTY   |     100 |                    6 |             0.09 |               1 |          0 |                       0.707 |            0.413 |           0.824 |     0.01 |       1.12  |                0.824 |
| YM    |     100 |                    0 |             0.42 |               3 |          1 |                     nan     |            0.448 |           0.875 |   nan    |     nan     |                0.978 |
| GC    |     100 |                    0 |             0    |               0 |          1 |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| CL    |     100 |                    0 |             0    |               0 |          1 |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| ZN    |     100 |                    0 |             0    |               0 |          1 |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                    3 |             0.29 |               1 |          0 |                       0.984 |            0.521 |           1.105 |     0.03 |       1.745 |                1.105 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | driver NQ resid15m>=2.5 dir=with X hold=60m | 215 | 2 | 1.28 | -0.64 | 0.98 | 0.61 / 0.92 | 0.21 / -0.12 / 0.24 | 0.11 | -0.14 | 1.00 | -0.03 | 0.83 | 336 | NO |
| ES 2 | driver NQ resid3m>=2.5 dir=with X hold=60m | 441 | 2 | 0.62 | -1.36 | 1.10 | 1.75 / 0.38 | 0.14 / 0.16 / 0.46 | 0.15 | -0.06 | 1.00 | 0.03 | 0.67 | 685 | LEAD(gate3-7 fail: plateau ) |
| ES 3 | driver NQ resid15m>=1.5 dir=with X hold=60m | 630 | 2 | 0.47 | -1.07 | 0.71 | 1.21 / 0.18 | 0.08 / -0.18 / 0.48 | 0.03 | 0.08 | 1.00 | -0.06 | 0.33 | 983 | NO |
| ES 4 | driver NQ resid5m>=1.5 dir=with X hold=60m | 924 | 2 | 0.36 | -1.55 | 0.23 | 0.17 / -0.40 | 0.08 / -0.23 / 0.04 | -0.10 | 0.11 | 1.00 | -0.16 | 0.00 | 1421 | NO |
| ES 5 | driver NQ resid5m>=2.5 dir=with X hold=60m | 398 | 2 | 0.23 | -1.05 | 1.00 | 2.06 / 0.40 | 0.03 / 0.26 / 0.52 | 0.11 | -0.14 | 1.00 | -0.02 | 0.83 | 599 | NO |
| ES 6 (diag) | driver NQ resid15m>=2.5 dir=with X hold=30m | 226 | 1 | 1.06 | -0.93 | 0.67 | 0.26 / 0.45 | 0.19 / 0.65 / -0.29 | 0.04 | 0.04 | 1.00 | -0.07 | 0.67 | 355 | diag |
| ES 7 (diag) | driver NQ resid15m>=2.5 dir=with X hold=15m | 256 | 1 | 0.67 | -1.48 | 0.67 | 0.72 / -0.18 | 0.12 / 0.87 / -0.32 | -0.02 | 0.24 | 1.00 | -0.08 | 0.17 | 406 | diag |
| ES 8 (diag) | driver YM resid15m>=1.5 dir=against X hold=60m | 1342 | 1 | 0.55 | -0.53 | 0.16 | -0.24 / -0.11 | 0.05 / -0.43 / -0.20 | -0.27 | 0.05 | 1.00 | -0.27 | 0.00 | 2293 | diag |
| NQ 1 | driver ES resid15m>=2.5 dir=against X hold=60m | 215 | 2 | 2.11 | 0.33 | 1.55 | 0.88 / 1.19 | 0.37 / -0.12 / 0.37 | 0.29 | -0.10 | 1.00 | 0.09 | 0.50 | 336 | NO |
| NQ 2 | driver ES resid15m>=2.5 dir=against X hold=30m | 226 | 2 | 1.87 | 0.24 | 1.12 | 0.34 / 1.21 | 0.35 / 0.85 / -0.36 | 0.23 | 0.15 | 1.00 | 0.02 | 1.00 | 355 | NO |
| NQ 3 | driver ES resid15m>=2.5 dir=against X hold=15m | 256 | 2 | 1.69 | 0.11 | 1.55 | 1.43 / 0.88 | 0.33 / 1.16 / -0.23 | 0.29 | 0.36 | 1.00 | 0.07 | 0.17 | 406 | NO |
| NQ 4 | driver YM resid15m>=2.5 dir=against X hold=30m | 1410 | 2 | 1.68 | 0.20 | 1.22 | 0.73 / 1.51 | 0.29 / 0.53 / 0.08 | 0.23 | 0.10 | 1.00 | 0.07 | 0.33 | 2286 | NO |
| NQ 5 | driver RTY resid3m>=1.5 dir=with X hold=30m | 6727 | 2 | 1.26 | -1.25 | 0.88 | 0.42 / 0.03 | 0.18 / 0.57 / -0.16 | 0.01 | -0.04 | 1.00 | -0.06 | 0.00 | 10227 | NO |
| NQ 6 | driver YM resid5m>=2.5 dir=against X hold=30m | 2036 | 2 | 1.26 | 0.23 | 0.72 | 0.07 / 1.04 | 0.20 / 0.16 / -0.16 | 0.07 | -0.13 | 0.99 | -0.09 | 0.33 | 3330 | NO |
| NQ 7 | driver YM resid15m>=2.5 dir=against X hold=60m | 1051 | 2 | 1.16 | -0.00 | 0.77 | 0.29 / 0.93 | 0.18 / 0.03 / -0.03 | 0.09 | -0.24 | 0.99 | -0.08 | 0.67 | 1711 | NO |
| NQ 8 | driver ES resid15m>=1.5 dir=against X hold=30m | 790 | 2 | 1.06 | 0.32 | 0.94 | 0.92 / 1.09 | 0.21 / 0.63 / 0.07 | 0.21 | 0.26 | 1.00 | 0.01 | 0.50 | 1224 | NO |
| NQ 9 | driver ES resid15m>=2.5 dir=against X hold=5m | 304 | 2 | 1.04 | 0.14 | 0.61 | 0.07 / 0.95 | 0.18 / 0.08 / -0.27 | 0.01 | 0.36 | 0.99 | -0.16 | 0.67 | 483 | NO |
| NQ 10 | driver ES resid15m>=1.5 dir=against X hold=60m | 630 | 2 | 1.03 | 0.31 | 1.29 | 1.73 / 1.27 | 0.18 / 0.03 / 0.54 | 0.24 | 0.01 | 1.00 | 0.02 | 0.67 | 983 | NO |
| RTY 1 | driver ES resid5m>=2.5 dir=with X hold=60m | 1119 | 2 | 1.12 | -1.01 | 0.04 | -1.71 / -0.03 | 0.11 / -0.53 / -0.26 | -0.14 | -0.19 | 1.00 | -0.24 | 0.00 | 1615 | NO |
| RTY 2 | driver ES resid3m>=2.5 dir=with X hold=30m | 1796 | 2 | 1.00 | -1.21 | 0.48 | -0.30 / -0.96 | 0.14 / -0.27 / -0.20 | -0.11 | -0.06 | 1.00 | -0.18 | 0.00 | 2570 | NO |
| RTY 3 | driver ES resid3m>=2.5 dir=with X hold=60m | 1305 | 2 | 0.86 | -0.86 | -0.11 | -1.60 / -0.14 | 0.11 / -0.68 / -0.26 | -0.16 | -0.22 | 0.99 | -0.26 | 0.00 | 1879 | NO |
| RTY 4 | driver NQ resid3m>=2.5 dir=with X hold=60m | 1809 | 2 | 0.57 | -1.12 | -0.50 | -2.38 / -0.27 | 0.06 / -0.75 / -0.24 | -0.24 | 0.30 | 1.00 | -0.30 | 0.00 | 2623 | NO |
| RTY 5 | driver ES resid15m>=2.5 dir=with X hold=60m | 727 | 2 | 0.38 | -0.50 | -0.21 | -0.92 / 0.53 | -0.02 / -0.55 / -0.18 | -0.19 | -0.05 | 0.91 | -0.33 | 0.00 | 1068 | NO |
| RTY 6 | driver NQ resid3m>=2.5 dir=with X hold=30m | 2574 | 2 | 0.31 | -1.65 | -0.15 | -0.75 / -1.44 | 0.05 / -0.46 / -0.09 | -0.21 | 0.22 | 1.00 | -0.23 | 0.00 | 3680 | NO |
| RTY 7 (diag) | driver NQ resid15m>=2.5 dir=with X hold=60m | 1094 | 1 | 0.50 | -1.30 | -0.12 | -0.97 / -0.15 | 0.04 / -0.42 / -0.13 | -0.15 | -0.01 | 0.98 | -0.25 | 0.00 | 1592 | diag |
| RTY 8 (diag) | driver ES resid5m>=2.5 dir=with X hold=30m | 1508 | 1 | 0.43 | -1.41 | -0.40 | -1.64 / -0.66 | -0.00 / -0.76 / -0.24 | -0.28 | -0.09 | 1.00 | -0.35 | 0.00 | 2161 | diag |
| RTY 9 (diag) | driver ES resid15m>=1.5 dir=with X hold=60m | 2228 | 1 | 0.37 | -1.18 | -0.47 | -1.74 / -0.30 | -0.01 / -0.57 / -0.32 | -0.28 | -0.33 | 1.00 | -0.33 | 0.00 | 3201 | diag |
| YM 1 (diag) | driver ES resid15m>=2.5 dir=against X hold=60m | 542 | 1 | 0.52 | -0.51 | 0.04 | -0.44 / 0.69 | 0.09 / -0.40 / -0.13 | -0.09 | 0.09 | 0.87 | -0.26 | 0.00 | 886 | diag |
| YM 2 (diag) | driver ES resid15m>=1.5 dir=with X hold=60m | 1341 | 1 | 0.44 | -0.37 | 0.15 | -0.17 / 0.23 | 0.05 / -0.52 / -0.07 | -0.17 | -0.13 | 0.98 | -0.27 | 0.00 | 2292 | diag |
| YM 3 (diag) | driver NQ resid15m>=2.5 dir=with X hold=60m | 1051 | 1 | 0.20 | -0.86 | -0.14 | -0.55 / 0.62 | 0.02 / -0.46 / -0.01 | -0.14 | -0.07 | 0.95 | -0.25 | 0.00 | 1710 | diag |
| GC 1 (diag) | driver 6E resid3m>=1.5 dir=with X hold=60m | 8204 | 1 | -0.46 | -4.25 | -0.55 | -0.68 / 0.23 | -0.14 / -0.11 / -0.52 | -0.61 | -0.28 | 0.99 | -0.53 | 0.00 | 13414 | diag |
| GC 2 (diag) | driver ZN resid15m>=2.5 dir=against X hold=60m | 2367 | 0 | -0.50 | -2.08 | -0.15 | 0.06 / 1.05 | -0.13 / -0.21 / -0.57 | -0.38 | 0.58 | 0.87 | -0.55 | 0.00 | 3666 | diag |
| GC 3 (diag) | driver ZN resid15m>=2.5 dir=against X hold=30m | 2998 | 0 | -0.58 | -3.24 | -1.12 | -1.62 / 0.47 | -0.19 / -0.81 / -1.24 | -0.76 | 0.40 | 0.79 | -0.83 | 0.00 | 4614 | diag |
| CL 1 (diag) | driver ES resid15m>=2.5 dir=against X hold=60m | 3596 | 0 | -1.02 | -1.89 | -1.18 | -1.51 / -0.53 | -0.21 / -0.87 / -0.48 | -0.85 | -0.30 | 0.99 | -0.64 | 0.00 | 6186 | diag |
| CL 2 (diag) | driver ZN resid15m>=2.5 dir=against X hold=60m | 3599 | 0 | -1.42 | -1.97 | -1.13 | -0.88 / -0.59 | -0.29 / -0.52 / -0.36 | -0.71 | -0.20 | 1.00 | -0.59 | 0.00 | 5920 | diag |
| CL 3 (diag) | driver ES resid5m>=2.5 dir=against X hold=60m | 4910 | 0 | -1.90 | -2.86 | -1.77 | -1.99 / -0.92 | -0.39 / -0.82 / -1.11 | -1.14 | -0.11 | 0.99 | -0.89 | 0.00 | 8365 | diag |
| ZN 1 (diag) | driver 6J resid15m>=2.5 dir=with X hold=60m | 1194 | 0 | -6.49 | -5.83 | -7.64 | -10.03 / -12.81 | -1.31 / -1.93 / -1.39 | -2.27 | -0.16 | 1.00 | -1.64 | 0.00 | 1865 | diag |
| ZN 2 (diag) | driver 6J resid15m>=2.5 dir=with X hold=30m | 1382 | 0 | -8.08 | -6.85 | -8.91 | -10.21 / -16.15 | -1.61 / -2.22 / -1.67 | -2.33 | -0.40 | 1.00 | -1.96 | 0.00 | 2140 | diag |
| ZN 3 (diag) | driver 6J resid15m>=2.5 dir=against X hold=60m | 1194 | 0 | -8.74 | -6.57 | -8.98 | -10.03 / -12.10 | -1.74 / -1.53 / -1.16 | -2.29 | -0.02 | 1.00 | -1.83 | 0.00 | 1865 | diag |
| BTC 1 | driver NQ resid3m>=2.5 dir=with X hold=60m | 3218 | 2 | 1.74 | -1.73 | 0.59 | -1.31 / 0.53 | 0.29 / -0.13 / -0.41 | -0.05 | -0.02 | 0.99 | -0.11 | 0.17 | 4787 | NO |
| BTC 2 | driver ES resid3m>=2.5 dir=with X hold=60m | 3264 | 2 | 1.05 | -2.18 | 0.51 | -0.65 / 0.44 | 0.17 / -0.07 / -0.11 | -0.05 | -0.10 | 1.00 | -0.09 | 0.00 | 4896 | NO |
| BTC 3 | driver ES resid15m>=2.5 dir=with X hold=30m | 2394 | 2 | 0.15 | -3.34 | -0.28 | -0.86 / 0.34 | 0.06 / -0.80 / -0.00 | -0.21 | 0.20 | 0.97 | -0.28 | 0.00 | 3460 | NO |
| BTC 4 (diag) | driver NQ resid15m>=2.5 dir=with X hold=60m | 1920 | 1 | 0.65 | -1.42 | 0.27 | -0.37 / 0.36 | 0.07 / -0.15 / -0.11 | -0.08 | 0.08 | 1.00 | -0.18 | 0.17 | 2753 | diag |
| BTC 5 (diag) | driver NQ resid5m>=2.5 dir=with X hold=60m | 2815 | 1 | 0.38 | -1.83 | -0.12 | -1.15 / 0.25 | 0.05 / -0.34 / -0.09 | -0.16 | 0.05 | 0.97 | -0.20 | 0.00 | 4155 | diag |
| BTC 6 (diag) | driver ES resid15m>=2.5 dir=with X hold=15m | 2877 | 1 | 0.34 | -3.04 | -0.07 | -0.87 / -0.54 | 0.05 / -0.40 / -0.20 | -0.23 | 0.25 | 1.00 | -0.23 | 0.00 | 4162 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 24 |
| diagnostic cells read | 21 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 0 |
| all-in uplift @20% > 0 (all scored) | 21 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 7 |
| standalone pair-window Sharpe above own random-entry null p95 | 41 |
| worst-decile corr <= +0.30 | 41 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 9 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 2 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC driver NQ resid3m>=2.5 dir=with X hold=60m | clean | 1.67 | 3.17 | -110475 | -86166 | 268540 | -187585 | 5.66 | 45.7 | 1.75 | -83571 | 252535 | -95016 |
| BTC driver NQ resid3m>=2.5 dir=with X hold=60m | H1 | -0.18 | -0.27 | -110436 | -96699 | 441079 | -143602 | -0.11 | 57.1 | 2.70 | -84359 | 138793 | -89106 |
| BTC driver NQ resid3m>=2.5 dir=with X hold=60m | H2 | -2.72 | -2.85 | -132646 | -103275 | 709640 | -146174 | -0.88 | 61.1 | 1.88 | -90970 | 233443 | -92763 |
| BTC driver NQ resid3m>=2.5 dir=with X hold=60m | all | 0.59 | 0.97 | -119253 | -95929 | 884196 | -187585 | 0.96 | 50.6 | 1.93 | -86464 | 252535 | -95016 |
| CL driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | clean | -1.45 | -1.66 | -165850 | -130880 | 1502469 | -299171 | -0.87 | 55.2 | 1.17 | -85050 | 320647 | -91535 |
| CL driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | H1 | -3.60 | -3.48 | -96626 | -88861 | 571820 | -107001 | -0.93 | 71.4 | 2.31 | -83814 | 158891 | -94182 |
| CL driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | H2 | -0.40 | -0.63 | -263974 | -199509 | 1172294 | -320089 | -0.23 | 63.9 | 1.94 | -103158 | 222475 | -104648 |
| CL driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | all | -1.13 | -1.51 | -188667 | -148051 | 2628508 | -320089 | -0.80 | 60.1 | 1.52 | -91518 | 320647 | -104648 |
| ES driver NQ resid3m>=2.5 dir=with X hold=60m | clean | 0.60 | 0.84 | -146411 | -110812 | 345167 | -293375 | 1.59 | 41.9 | 1.60 | -80624 | 238239 | -93200 |
| ES driver NQ resid3m>=2.5 dir=with X hold=60m | H1 | 0.95 | 1.64 | -112968 | -100937 | 425213 | -140987 | 0.67 | 46.4 | 2.99 | -66246 | 154510 | -71132 |
| ES driver NQ resid3m>=2.5 dir=with X hold=60m | H2 | 2.33 | 4.06 | -150668 | -124194 | 277983 | -158169 | 3.38 | 36.1 | 2.75 | -83963 | 226617 | -95285 |
| ES driver NQ resid3m>=2.5 dir=with X hold=60m | all | 1.10 | 1.68 | -150470 | -116075 | 425213 | -293375 | 4.17 | 41.1 | 2.08 | -80789 | 238239 | -95285 |
| GC driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | clean | -0.60 | -0.85 | -137274 | -115092 | 944309 | -182552 | -0.59 | 51.4 | 1.33 | -83808 | 278786 | -87998 |
| GC driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | H1 | 0.42 | 0.96 | -283961 | -237102 | 585562 | -398167 | 0.65 | 57.1 | 2.62 | -81173 | 189902 | -106017 |
| GC driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | H2 | -0.34 | -0.47 | -375515 | -311883 | 1288275 | -392653 | -0.22 | 55.6 | 1.73 | -137982 | 330720 | -138735 |
| GC driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | all | -0.15 | -0.25 | -260512 | -200120 | 1303242 | -398167 | -0.35 | 53.6 | 1.64 | -101546 | 330720 | -138735 |
| NQ driver ES resid15m>=2.5 dir=against X hold=15m | clean | 1.72 | 3.60 | -88890 | -77304 | 279840 | -140201 | 5.56 | 30.5 | 1.79 | -81945 | 235355 | -89023 |
| NQ driver ES resid15m>=2.5 dir=against X hold=15m | H1 | 3.23 | 10.60 | -84015 | -82142 | 188231 | -88677 | 6.44 | 28.6 | 3.99 | -74304 | 127801 | -79333 |
| NQ driver ES resid15m>=2.5 dir=against X hold=15m | H2 | 0.09 | 0.13 | -196124 | -170951 | 631280 | -224188 | 0.07 | 38.9 | 2.06 | -108889 | 285975 | -109157 |
| NQ driver ES resid15m>=2.5 dir=against X hold=15m | all | 1.55 | 2.91 | -139286 | -111361 | 631280 | -224188 | 4.45 | 32.1 | 2.17 | -89476 | 285975 | -109157 |
| RTY driver ES resid3m>=2.5 dir=with X hold=30m | clean | 0.96 | 1.71 | -100060 | -89097 | 309242 | -152371 | 2.84 | 46.7 | 1.60 | -87999 | 272846 | -93674 |
| RTY driver ES resid3m>=2.5 dir=with X hold=30m | H1 | -0.43 | -0.62 | -111102 | -102842 | 493358 | -133091 | -0.21 | 60.7 | 2.56 | -90748 | 166959 | -95552 |
| RTY driver ES resid3m>=2.5 dir=with X hold=30m | H2 | -0.20 | -0.27 | -144359 | -119780 | 556823 | -183045 | -0.12 | 47.2 | 2.10 | -100236 | 232880 | -103659 |
| RTY driver ES resid3m>=2.5 dir=with X hold=30m | all | 0.48 | 0.75 | -116394 | -100654 | 731888 | -183045 | 0.96 | 49.4 | 1.87 | -92568 | 272846 | -103659 |
| YM driver ES resid15m>=2.5 dir=against X hold=60m (diag) | clean | 0.53 | 0.78 | -130776 | -104762 | 543835 | -200390 | 0.88 | 44.8 | 1.55 | -87566 | 276069 | -98419 |
| YM driver ES resid15m>=2.5 dir=against X hold=60m (diag) | H1 | -1.27 | -1.55 | -190532 | -169847 | 732227 | -235476 | -0.60 | 50.0 | 2.43 | -75770 | 165118 | -84316 |
| YM driver ES resid15m>=2.5 dir=against X hold=60m (diag) | H2 | 0.08 | 0.10 | -268562 | -223600 | 835245 | -340000 | 0.05 | 44.4 | 2.17 | -85922 | 160139 | -100878 |
| YM driver ES resid15m>=2.5 dir=against X hold=60m (diag) | all | 0.04 | 0.06 | -195455 | -154917 | 1373490 | -340000 | 0.06 | 45.8 | 1.83 | -87752 | 276069 | -100878 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=60m (diag) | clean | -6.56 | -5.06 | -183495 | -163505 | 5977791 | -213105 | -1.00 | 86.7 | 0.15 | -96916 | 410428 | -114732 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=60m (diag) | H1 | -10.77 | -6.03 | -184190 | -168416 | 1976207 | -202099 | -1.00 | 96.4 | 0.90 | -104909 | 219623 | -117352 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=60m (diag) | H2 | -9.39 | -5.81 | -172530 | -151465 | 2294713 | -188419 | -1.00 | 91.7 | 0.91 | -95197 | 239392 | -97961 |
| ZN driver 6J resid15m>=2.5 dir=with X hold=60m (diag) | all | -7.64 | -5.39 | -185192 | -164207 | 10248711 | -213105 | -1.00 | 89.3 | 0.44 | -99602 | 410428 | -117352 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES driver NQ resid3m>=2.5 dir=with X hold=60m | -10.2 | 1.9 | 21.1 | 37.5 | 9.2 / 20.8 | 43.7 / 48.6 | NO |
| NQ driver ES resid15m>=2.5 dir=against X hold=15m | 1.4 | -23.4 | 6.0 | -3.0 | 12.7 / 22.9 | 28.0 / 36.4 | NO |
| RTY driver ES resid3m>=2.5 dir=with X hold=30m | -22.1 | -17.6 | 0.9 | 24.9 | 3.6 / 10.2 | -3.1 / 4.6 | NO |
| YM driver ES resid15m>=2.5 dir=against X hold=60m (diag) | -29.1 | -6.1 | 6.7 | 15.3 | -4.9 / 11.2 | 18.4 / 20.0 | NO |
| GC driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | -35.1 | -93.8 | -30.3 | -33.4 | 14.3 / 17.4 | -76.2 / -22.3 | NO |
| CL driver ZN resid15m>=2.5 dir=against X hold=60m (diag) | -53.6 | -39.1 | -2.3 | 0.2 | 7.7 / 13.0 | -1.8 / 18.0 | NO |
| ZN driver 6J resid15m>=2.5 dir=with X hold=60m (diag) | -144.3 | -38.7 | -13.8 | -326.2 | -34.4 / -7.6 | -46.2 / -24.8 | NO |
| BTC driver NQ resid3m>=2.5 dir=with X hold=60m | -20.5 | 4.7 | 14.6 | 31.7 | 4.0 / 19.2 | 7.9 / 17.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 driver NQ resid15m>=2.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 1374 | 4.0 | -25.4 | -11.9 | 29.4 | 0.10 / -0.64 / -0.30 | 121.2 / 91.8 |
| ES 2 driver NQ resid3m>=2.5 dir=with X hold=60m | negative pre-2023 | 2659 | -10.1 | -39.5 | -25.6 | 29.4 | -0.35 / -1.36 / -0.88 | 64.7 / 35.3 |
| ES 3 driver NQ resid15m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 4226 | 7.0 | -22.4 | -8.7 | 29.4 | 0.34 / -1.07 / -0.42 | 44.9 / 15.5 |
| ES 4 driver NQ resid5m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 6766 | 2.8 | -26.5 | -12.6 | 29.4 | 0.17 / -1.55 / -0.74 | 38.2 / 8.9 |
| ES 5 driver NQ resid5m>=2.5 dir=with X hold=60m | negative pre-2023 | 2259 | -1.5 | -30.8 | -17.0 | 29.4 | -0.05 / -1.05 / -0.58 | 42.7 / 13.4 |
| ES 6 (diag) driver NQ resid15m>=2.5 dir=with X hold=30m | gross-positive, cost-negative pre-2023 | 1508 | 2.4 | -26.9 | -13.6 | 29.4 | 0.09 / -0.93 / -0.47 | 79.1 / 49.8 |
| ES 7 (diag) driver NQ resid15m>=2.5 dir=with X hold=15m | gross-positive, cost-negative pre-2023 | 1724 | 1.0 | -28.4 | -15.2 | 29.4 | 0.04 / -1.48 / -0.80 | 50.1 / 20.8 |
| ES 8 (diag) driver YM resid15m>=1.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 2778 | 15.2 | -14.1 | -1.3 | 29.4 | 0.57 / -0.53 / -0.05 | 42.2 / 12.8 |
| NQ 1 driver ES resid15m>=2.5 dir=against X hold=60m | positive pre-2023 | 1374 | 40.1 | 25.8 | 33.8 | 14.4 | 0.51 / 0.33 / 0.43 | 331.1 / 316.8 |
| NQ 2 driver ES resid15m>=2.5 dir=against X hold=30m | positive pre-2023 | 1508 | 26.9 | 12.5 | 20.5 | 14.4 | 0.50 / 0.24 / 0.38 | 219.6 / 205.3 |
| NQ 3 driver ES resid15m>=2.5 dir=against X hold=15m | positive pre-2023 | 1724 | 18.8 | 4.4 | 12.3 | 14.4 | 0.49 / 0.11 / 0.32 | 141.6 / 127.2 |
| NQ 4 driver YM resid15m>=2.5 dir=against X hold=30m | positive pre-2023 | 4108 | 20.6 | 6.2 | 13.6 | 14.4 | 0.66 / 0.20 / 0.44 | 76.7 / 62.3 |
| NQ 5 driver RTY resid3m>=1.5 dir=with X hold=30m | negative pre-2023 | 16819 | -4.5 | -18.8 | -12.6 | 14.4 | -0.31 / -1.25 / -0.84 | 32.3 / 17.9 |
| NQ 6 driver YM resid5m>=2.5 dir=against X hold=30m | positive pre-2023 | 6120 | 20.2 | 5.9 | 13.3 | 14.4 | 0.77 / 0.23 / 0.51 | 54.1 / 39.7 |
| NQ 7 driver YM resid15m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 3314 | 14.2 | -0.2 | 7.3 | 14.4 | 0.28 / -0.00 / 0.15 | 83.6 / 69.2 |
| NQ 8 driver ES resid15m>=1.5 dir=against X hold=30m | positive pre-2023 | 5413 | 21.6 | 7.2 | 15.3 | 14.4 | 0.94 / 0.32 / 0.67 | 70.6 / 56.2 |
| NQ 9 driver ES resid15m>=2.5 dir=against X hold=5m | positive pre-2023 | 2112 | 17.2 | 2.8 | 10.7 | 14.4 | 0.83 / 0.14 / 0.52 | 57.2 / 42.8 |
| NQ 10 driver ES resid15m>=1.5 dir=against X hold=60m | positive pre-2023 | 4227 | 25.7 | 11.4 | 19.5 | 14.4 | 0.69 / 0.31 / 0.53 | 100.8 / 86.4 |
| RTY 1 driver ES resid5m>=2.5 dir=with X hold=60m | negative pre-2023 | 2285 | -11.1 | -25.5 | -23.5 | 14.4 | -0.44 / -1.01 / -0.93 | 41.3 / 26.9 |
| RTY 2 driver ES resid3m>=2.5 dir=with X hold=30m | negative pre-2023 | 3575 | -3.5 | -17.9 | -15.9 | 14.4 | -0.23 / -1.21 / -1.08 | 27.8 / 13.5 |
| RTY 3 driver ES resid3m>=2.5 dir=with X hold=60m | negative pre-2023 | 2705 | -6.7 | -21.1 | -19.1 | 14.4 | -0.27 / -0.86 / -0.78 | 32.5 / 18.1 |
| RTY 4 driver NQ resid3m>=2.5 dir=with X hold=60m | negative pre-2023 | 4338 | -3.8 | -18.2 | -16.4 | 14.4 | -0.24 / -1.12 / -1.01 | 21.0 / 6.6 |
| RTY 5 driver ES resid15m>=2.5 dir=with X hold=60m | negative pre-2023 | 1537 | -1.8 | -16.1 | -14.3 | 14.4 | -0.05 / -0.50 / -0.44 | 22.7 / 8.3 |
| RTY 6 driver NQ resid3m>=2.5 dir=with X hold=30m | negative pre-2023 | 6018 | -3.7 | -18.0 | -16.3 | 14.4 | -0.34 / -1.65 / -1.48 | 16.3 / 2.0 |
| RTY 7 (diag) driver NQ resid15m>=2.5 dir=with X hold=60m | negative pre-2023 | 2639 | -16.8 | -31.2 | -29.4 | 14.4 | -0.71 / -1.30 / -1.23 | 24.1 / 9.8 |
| RTY 8 (diag) driver ES resid5m>=2.5 dir=with X hold=30m | negative pre-2023 | 2983 | -9.2 | -23.6 | -21.7 | 14.4 | -0.55 / -1.41 / -1.30 | 19.9 / 5.6 |
| RTY 9 (diag) driver ES resid15m>=1.5 dir=with X hold=60m | negative pre-2023 | 4443 | -4.4 | -18.8 | -16.8 | 14.4 | -0.27 / -1.18 / -1.06 | 18.4 / 4.0 |
| YM 1 (diag) driver ES resid15m>=2.5 dir=against X hold=60m | negative pre-2023 | 830 | -7.5 | -21.8 | -17.3 | 14.4 | -0.18 / -0.51 / -0.41 | 30.2 / 15.8 |
| YM 2 (diag) driver ES resid15m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 2776 | 6.4 | -7.9 | -2.9 | 14.4 | 0.29 / -0.37 / -0.14 | 21.7 / 7.4 |
| YM 3 (diag) driver NQ resid15m>=2.5 dir=with X hold=60m | negative pre-2023 | 3312 | -3.6 | -17.9 | -13.0 | 14.4 | -0.18 / -0.86 / -0.63 | 18.7 / 4.3 |
| GC 1 (diag) driver 6E resid3m>=1.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 41159 | 3.1 | -21.3 | -11.5 | 24.4 | 0.63 / -4.25 / -2.29 | 19.5 / -4.9 |
| GC 2 (diag) driver ZN resid15m>=2.5 dir=against X hold=60m | negative pre-2023 | 10789 | -3.7 | -28.1 | -18.4 | 24.4 | -0.28 / -2.08 / -1.36 | 11.7 / -12.7 |
| GC 3 (diag) driver ZN resid15m>=2.5 dir=against X hold=30m | negative pre-2023 | 13297 | -5.8 | -30.2 | -20.5 | 24.4 | -0.63 / -3.24 / -2.20 | 14.8 / -9.6 |
| CL 1 (diag) driver ES resid15m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 14286 | 2.4 | -21.9 | -19.9 | 24.4 | 0.21 / -1.89 / -1.71 | 16.0 / -8.3 |
| CL 2 (diag) driver ZN resid15m>=2.5 dir=against X hold=60m | gross-positive, cost-negative pre-2023 | 18551 | 4.7 | -19.6 | -16.8 | 24.4 | 0.48 / -1.97 / -1.69 | 9.3 / -15.1 |
| CL 3 (diag) driver ES resid5m>=2.5 dir=against X hold=60m | negative pre-2023 | 21521 | -1.3 | -25.7 | -23.5 | 24.4 | -0.15 / -2.86 / -2.62 | 10.4 / -13.9 |
| ZN 1 (diag) driver 6J resid15m>=2.5 dir=with X hold=60m | gross-positive, cost-negative pre-2023 | 6424 | 2.9 | -32.7 | -38.2 | 35.6 | 0.57 / -5.83 / -6.52 | 6.5 / -29.1 |
| ZN 2 (diag) driver 6J resid15m>=2.5 dir=with X hold=30m | gross-positive, cost-negative pre-2023 | 7391 | 1.7 | -33.9 | -39.4 | 35.6 | 0.43 / -6.85 / -7.39 | 4.5 / -31.1 |
| ZN 3 (diag) driver 6J resid15m>=2.5 dir=against X hold=60m | negative pre-2023 | 6424 | -2.9 | -38.5 | -44.0 | 35.6 | -0.57 / -6.57 / -7.10 | -6.5 / -42.1 |
| BTC 1 driver NQ resid3m>=2.5 dir=with X hold=60m | negative pre-2023 | 2070 | -14.5 | -68.9 | -36.7 | 54.4 | -0.37 / -1.73 / -0.93 | 177.8 / 123.5 |
| BTC 2 driver ES resid3m>=2.5 dir=with X hold=60m | negative pre-2023 | 2111 | -15.3 | -69.7 | -37.6 | 54.4 | -0.50 / -2.18 / -1.19 | 135.4 / 81.0 |
| BTC 3 driver ES resid15m>=2.5 dir=with X hold=30m | negative pre-2023 | 1305 | -63.7 | -118.0 | -86.2 | 54.4 | -1.83 / -3.34 / -2.46 | 61.4 / 7.0 |
| BTC 4 (diag) driver NQ resid15m>=2.5 dir=with X hold=60m | negative pre-2023 | 1120 | -17.9 | -72.3 | -40.2 | 54.4 | -0.35 / -1.42 / -0.79 | 124.1 / 69.7 |
| BTC 5 (diag) driver NQ resid5m>=2.5 dir=with X hold=60m | negative pre-2023 | 1762 | -19.9 | -74.3 | -42.2 | 54.4 | -0.49 / -1.83 / -1.04 | 85.9 / 31.6 |
| BTC 6 (diag) driver ES resid15m>=2.5 dir=with X hold=15m | negative pre-2023 | 1515 | -28.5 | -82.9 | -51.1 | 54.4 | -1.06 / -3.04 / -1.89 | 73.0 / 18.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 3 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.00, p(top) = 0.03); CL: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ES: 5 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.00, p(top) = 0.06); GC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); NQ: 24 cells pass the clean rule against a replicate mean of 4.8 (p(count) = 0.00, p(top) = 0.00); RTY: 6 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.00, p(top) = 0.01); YM: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 24 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.31 (NQ driver ES resid15m>=2.5 dir=against X hold=15m); bootstrap lower bound > 0 for 7 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 9; gate_add PASS at some share: 2 (cell-share pairs).
- Gate-3 cell ES driver NQ resid3m>=2.5 dir=with X hold=60m: uplift +0.14/+0.16/+0.46, boot lo +0.03, plateau 0.67, 2x-slip +0.15, wd corr -0.06, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 12, 'positive pre-2023': 8, 'gross-positive, cost-negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_8.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw8/ (`SW8_CO_all_selected_scored.csv`).

DONE SW8
