# REPORT BJ2 - power-hour momentum (BJ batch)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 11 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.20.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BJ', before the first run)
- Rule: see IDEAS_BJ.md / PREREG_AUTOPILOT.md BATCH BJ. power-hour momentum. Null: drift- and clock-matched random entries (long/short mix of the real events).
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      12 |         12 |         2 |               0.822 |                2 |          2 |            3 |
| NQ    |      12 |         12 |         5 |               1.609 |                2 |          5 |            3 |
| RTY   |      12 |         12 |         1 |               0.507 |                2 |          1 |            3 |
| YM    |      12 |         12 |         3 |               0.557 |                2 |          3 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            0.61  |               4 |      0.13  |                       0.45  |            0.544 |           0.967 |    0.27  |       0.822 |                1.041 |
| NQ    |     200 |                    5 |            2.2   |               7 |      0.065 |                       1.181 |            0.733 |           1.328 |    0.07  |       1.609 |                1.658 |
| RTY   |     200 |                    1 |            0.505 |               3 |      0.41  |                       0.507 |            0.61  |           1.14  |    0.26  |       0.507 |                1.245 |
| YM    |     200 |                    3 |            0.965 |               4 |      0.07  |                       0.486 |            0.628 |           1.407 |    0.395 |       0.557 |                1.561 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | entry 15:30 prior 60m ret dir=against exit 15:55 | 494 | 2 | 0.82 | -1.78 | -0.01 | -1.51 / 0.78 | 0.08 / -0.56 / -0.11 | -0.20 | -0.50 | 0.91 | -0.23 | 0.00 | 795 | NO |
| ES 2 | entry 15:00 prior 30m ret dir=against exit 15:55 | 491 | 2 | 0.08 | -1.37 | -0.03 | -0.08 / 1.01 | -0.06 / 0.00 / -0.04 | -0.17 | 0.15 | 0.83 | -0.22 | 0.00 | 792 | NO |
| ES 3 (diag) | entry 15:30 prior 90m ret dir=against exit 15:55 | 492 | 1 | 0.65 | -1.70 | 0.11 | -1.02 / 0.37 | 0.12 / -0.33 / -0.04 | -0.11 | -0.38 | 0.97 | -0.15 | 0.50 | 793 | diag |
| ES 4 (diag) | entry 15:00 prior 60m ret dir=against exit 15:55 | 490 | 1 | 0.07 | -1.19 | 0.29 | 0.50 / 1.12 | -0.01 / -0.03 / 0.09 | -0.10 | 0.09 | 0.94 | -0.17 | 1.00 | 790 | diag |
| ES 5 (diag) | entry 15:30 prior 30m ret dir=against exit 15:55 | 486 | 1 | 0.07 | -1.42 | -0.45 | -1.35 / 0.43 | -0.05 / -0.82 / 0.04 | -0.30 | -0.32 | 0.78 | -0.34 | 0.00 | 780 | diag |
| NQ 1 | entry 15:30 prior 90m ret dir=against exit 15:55 | 497 | 2 | 1.61 | -0.83 | 1.20 | 0.58 / 1.37 | 0.29 / 0.00 / 0.13 | 0.18 | -0.16 | 0.99 | 0.03 | 0.50 | 800 | NO |
| NQ 2 | entry 15:30 prior 30m ret dir=against exit 15:55 | 497 | 2 | 1.44 | -0.81 | 0.54 | -0.85 / 1.26 | 0.21 / -0.42 / -0.07 | 0.01 | -0.10 | 0.92 | -0.14 | 1.00 | 799 | NO |
| NQ 3 | entry 15:30 prior 60m ret dir=against exit 15:55 | 495 | 2 | 1.29 | -1.23 | 0.38 | -0.85 / 1.34 | 0.22 / -0.44 / -0.07 | 0.02 | -0.24 | 0.88 | -0.15 | 1.00 | 796 | NO |
| NQ 4 | entry 15:00 prior 60m ret dir=against exit 15:55 | 496 | 2 | 1.10 | -0.53 | 1.08 | 1.03 / 1.48 | 0.18 / 0.19 / 0.20 | 0.16 | 0.27 | 0.98 | -0.02 | 1.00 | 799 | LEAD |
| NQ 5 | entry 15:00 prior 30m ret dir=against exit 15:55 | 495 | 2 | 0.47 | -1.01 | 0.65 | 0.93 / 1.34 | 0.04 / 0.25 / 0.26 | 0.08 | -0.49 | 0.91 | -0.08 | 0.50 | 796 | NO |
| NQ 6 (diag) | entry 15:00 prior 90m ret dir=against exit 15:55 | 496 | 1 | 0.45 | -0.75 | 0.46 | 0.52 / 1.23 | 0.08 / 0.06 / 0.13 | 0.06 | 0.22 | 0.85 | -0.11 | 1.00 | 799 | diag |
| NQ 7 (diag) | entry 15:00 prior 90m ret dir=with exit 15:55 | 496 | 0 | -0.81 | 0.10 | -0.78 | -0.80 / 1.39 | -0.20 / -0.21 / -0.39 | -0.27 | -0.22 | 0.15 | -0.44 | 0.00 | 799 | diag |
| NQ 8 (diag) | entry 15:00 prior 30m ret dir=with exit 15:55 | 495 | 0 | -0.87 | 0.39 | -1.00 | -1.22 / 1.16 | -0.18 / -0.41 / -0.52 | -0.31 | 0.48 | 0.04 | -0.49 | 0.00 | 796 | diag |
| RTY 1 | entry 15:30 prior 90m ret dir=against exit 15:55 | 497 | 2 | 0.51 | -1.10 | 0.14 | -0.48 / 0.67 | 0.10 / -0.63 / 0.09 | -0.14 | -0.30 | 0.95 | -0.20 | 0.00 | 795 | NO |
| RTY 2 (diag) | entry 15:00 prior 30m ret dir=against exit 15:55 | 488 | 1 | -0.00 | -0.92 | 0.33 | 0.74 / 0.89 | -0.05 / -0.37 / 0.46 | -0.09 | -0.31 | 0.95 | -0.17 | 0.50 | 786 | diag |
| RTY 3 (diag) | entry 15:30 prior 60m ret dir=against exit 15:55 | 497 | 1 | -0.02 | -1.08 | -0.06 | -0.13 / 0.61 | -0.07 / -0.53 / 0.14 | -0.22 | -0.46 | 0.92 | -0.28 | 0.00 | 798 | diag |
| RTY 4 (diag) | entry 15:30 prior 30m ret dir=against exit 15:55 | 490 | 0 | -0.20 | -1.28 | -0.07 | 0.15 / 0.50 | -0.09 / -0.11 / 0.01 | -0.20 | -0.27 | 0.95 | -0.26 | 0.00 | 789 | diag |
| YM 1 | entry 15:30 prior 90m ret dir=against exit 15:55 | 495 | 2 | 0.56 | -1.11 | 0.30 | -0.25 / 0.42 | 0.11 / -0.58 / 0.25 | -0.04 | -0.26 | 0.96 | -0.12 | 0.50 | 797 | NO |
| YM 2 | entry 15:00 prior 30m ret dir=against exit 15:55 | 491 | 2 | 0.48 | -0.89 | 0.54 | 0.52 / 1.01 | 0.04 / -0.00 / 0.23 | -0.01 | 0.00 | 0.96 | -0.13 | 0.50 | 789 | NO |
| YM 3 | entry 15:00 prior 60m ret dir=against exit 15:55 | 493 | 2 | 0.42 | -0.78 | 0.22 | -0.22 / 0.93 | 0.03 / -0.29 / 0.02 | -0.09 | 0.05 | 0.87 | -0.21 | 0.00 | 793 | NO |
| YM 4 (diag) | entry 15:30 prior 60m ret dir=against exit 15:55 | 492 | 1 | 0.28 | -1.46 | -0.03 | -0.52 / 0.83 | 0.02 / -0.47 / 0.08 | -0.13 | -0.41 | 0.86 | -0.21 | 0.00 | 793 | diag |
| YM 5 (diag) | entry 15:00 prior 90m ret dir=against exit 15:55 | 490 | 0 | -0.33 | -0.89 | -0.21 | -0.18 / 0.95 | -0.07 / -0.15 / -0.12 | -0.15 | 0.11 | 0.71 | -0.27 | 0.00 | 791 | diag |
| YM 6 (diag) | entry 15:30 prior 30m ret dir=with exit 15:55 | 490 | 0 | -0.49 | -0.46 | -0.87 | -1.59 / 0.85 | -0.13 / -0.01 / -0.46 | -0.29 | 0.16 | 0.34 | -0.38 | 0.00 | 790 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 22 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES entry 15:00 prior 30m ret dir=against exit 15:55 | clean | -0.00 | -0.00 | -135562 | -112803 | 642916 | -164774 | -0.00 | 49.5 | 1.40 | -85006 | 264057 | -91128 |
| ES entry 15:00 prior 30m ret dir=against exit 15:55 | H1 | -0.30 | -0.43 | -79106 | -71431 | 456006 | -101594 | -0.11 | 50.0 | 2.83 | -74137 | 166189 | -77939 |
| ES entry 15:00 prior 30m ret dir=against exit 15:55 | H2 | 0.02 | 0.04 | -116224 | -102885 | 348273 | -135861 | 0.02 | 55.6 | 2.45 | -92586 | 218511 | -101842 |
| ES entry 15:00 prior 30m ret dir=against exit 15:55 | all | -0.03 | -0.04 | -127928 | -108301 | 752754 | -164774 | -0.06 | 51.2 | 1.84 | -86106 | 264057 | -101842 |
| NQ entry 15:30 prior 90m ret dir=against exit 15:55 | clean | 1.59 | 2.97 | -111548 | -87840 | 455739 | -137347 | 3.17 | 43.8 | 1.75 | -84955 | 236237 | -90725 |
| NQ entry 15:30 prior 90m ret dir=against exit 15:55 | H1 | 0.03 | 0.04 | -109632 | -98984 | 240391 | -118468 | 0.03 | 50.0 | 2.83 | -73424 | 158825 | -76576 |
| NQ entry 15:30 prior 90m ret dir=against exit 15:55 | H2 | 0.98 | 1.62 | -113634 | -109486 | 325262 | -115598 | 1.02 | 50.0 | 2.62 | -101279 | 239472 | -102808 |
| NQ entry 15:30 prior 90m ret dir=against exit 15:55 | all | 1.20 | 2.12 | -118321 | -96902 | 455739 | -137347 | 3.91 | 45.8 | 2.11 | -87902 | 239472 | -102808 |
| RTY entry 15:30 prior 90m ret dir=against exit 15:55 | clean | 0.57 | 0.92 | -108888 | -91444 | 606991 | -171552 | 0.85 | 51.4 | 1.56 | -89337 | 252967 | -98865 |
| RTY entry 15:30 prior 90m ret dir=against exit 15:55 | H1 | -1.98 | -2.30 | -165622 | -147640 | 652076 | -209109 | -0.87 | 64.3 | 2.19 | -85902 | 196319 | -91888 |
| RTY entry 15:30 prior 90m ret dir=against exit 15:55 | H2 | 0.77 | 1.27 | -103026 | -93163 | 230263 | -103026 | 1.14 | 41.7 | 2.57 | -92347 | 235459 | -94449 |
| RTY entry 15:30 prior 90m ret dir=against exit 15:55 | all | 0.14 | 0.21 | -127580 | -106355 | 923280 | -209109 | 0.23 | 51.8 | 1.90 | -90290 | 252967 | -98865 |
| YM entry 15:00 prior 30m ret dir=against exit 15:55 | clean | 0.55 | 0.88 | -115502 | -100107 | 665802 | -132695 | 0.76 | 48.6 | 1.50 | -85689 | 262834 | -93503 |
| YM entry 15:00 prior 30m ret dir=against exit 15:55 | H1 | -0.88 | -1.18 | -103762 | -89886 | 237921 | -139972 | -0.71 | 53.6 | 2.82 | -70549 | 166867 | -74007 |
| YM entry 15:00 prior 30m ret dir=against exit 15:55 | H2 | 1.19 | 2.28 | -112622 | -100430 | 288685 | -116281 | 1.71 | 44.4 | 2.71 | -94798 | 221213 | -105781 |
| YM entry 15:00 prior 30m ret dir=against exit 15:55 | all | 0.54 | 0.89 | -117581 | -101281 | 665802 | -139972 | 1.24 | 48.8 | 1.95 | -87194 | 262834 | -105781 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES entry 15:00 prior 30m ret dir=against exit 15:55 | -30.5 | -5.1 | 11.5 | 16.0 | 4.3 / 12.6 | 30.7 / 36.7 | NO |
| NQ entry 15:30 prior 90m ret dir=against exit 15:55 | -10.5 | -6.9 | 9.7 | 33.6 | 5.1 / 13.0 | 33.3 / 35.0 | NO |
| RTY entry 15:30 prior 90m ret dir=against exit 15:55 | -27.7 | -5.1 | 4.8 | 23.5 | -5.9 / 8.2 | -3.7 / -1.5 | NO |
| YM entry 15:00 prior 30m ret dir=against exit 15:55 | -21.0 | -12.3 | 10.6 | 13.8 | 4.1 / 12.8 | 38.2 / 43.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 entry 15:30 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2550 | -16.7 | -46.1 | -31.9 | 29.4 | -0.65 / -1.78 / -1.23 | 57.1 / 27.8 |
| ES 2 entry 15:00 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 2510 | -17.7 | -47.0 | -32.9 | 29.4 | -0.52 / -1.37 / -0.95 | 29.3 / -0.0 |
| ES 3 (diag) entry 15:30 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 2550 | -10.4 | -39.7 | -25.5 | 29.4 | -0.44 / -1.70 / -1.09 | 54.2 / 24.9 |
| ES 4 (diag) entry 15:00 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2549 | -8.8 | -38.2 | -24.0 | 29.4 | -0.28 / -1.19 / -0.75 | 36.4 / 7.1 |
| ES 5 (diag) entry 15:30 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 2517 | -6.1 | -35.5 | -21.3 | 29.4 | -0.24 / -1.42 / -0.85 | 31.6 / 2.2 |
| NQ 1 entry 15:30 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 2595 | -13.3 | -27.7 | -19.1 | 14.4 | -0.40 / -0.83 / -0.58 | 110.5 / 96.1 |
| NQ 2 entry 15:30 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 2587 | -13.0 | -27.4 | -18.8 | 14.4 | -0.38 / -0.81 / -0.56 | 90.8 / 76.4 |
| NQ 3 entry 15:30 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2587 | -25.1 | -39.4 | -30.9 | 14.4 | -0.78 / -1.23 / -0.96 | 85.6 / 71.2 |
| NQ 4 entry 15:00 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2591 | -9.5 | -23.8 | -15.3 | 14.4 | -0.21 / -0.53 / -0.34 | 95.3 / 81.0 |
| NQ 5 entry 15:00 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 2578 | -32.3 | -46.7 | -38.2 | 14.4 | -0.70 / -1.01 / -0.83 | 45.7 / 31.3 |
| NQ 6 (diag) entry 15:00 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 2597 | -18.8 | -33.1 | -24.6 | 14.4 | -0.43 / -0.75 / -0.56 | 47.3 / 33.0 |
| NQ 7 (diag) entry 15:00 prior 90m ret dir=with exit 15:55 | positive pre-2023 | 2597 | 18.8 | 4.4 | 13.0 | 14.4 | 0.43 / 0.10 / 0.29 | -47.3 / -61.7 |
| NQ 8 (diag) entry 15:00 prior 30m ret dir=with exit 15:55 | positive pre-2023 | 2578 | 32.3 | 18.0 | 26.5 | 14.4 | 0.70 / 0.39 / 0.58 | -45.7 / -60.0 |
| RTY 1 entry 15:30 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 1479 | -4.3 | -18.7 | -16.4 | 14.4 | -0.25 / -1.10 / -0.96 | 22.3 / 7.9 |
| RTY 2 (diag) entry 15:00 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 1467 | -7.1 | -21.5 | -19.3 | 14.4 | -0.30 / -0.92 / -0.82 | 14.9 / 0.5 |
| RTY 3 (diag) entry 15:30 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 1479 | -5.1 | -19.5 | -17.2 | 14.4 | -0.28 / -1.08 / -0.95 | 14.1 / -0.2 |
| RTY 4 (diag) entry 15:30 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 1478 | -8.0 | -22.4 | -20.1 | 14.4 | -0.46 / -1.28 / -1.15 | 11.0 / -3.3 |
| YM 1 entry 15:30 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 2581 | -5.9 | -20.2 | -14.5 | 14.4 | -0.32 / -1.11 / -0.80 | 27.0 / 12.6 |
| YM 2 entry 15:00 prior 30m ret dir=against exit 15:55 | negative pre-2023 | 2564 | -9.2 | -23.6 | -17.9 | 14.4 | -0.35 / -0.89 / -0.67 | 30.6 / 16.2 |
| YM 3 entry 15:00 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2583 | -4.7 | -19.0 | -13.3 | 14.4 | -0.19 / -0.78 / -0.55 | 29.3 / 14.9 |
| YM 4 (diag) entry 15:30 prior 60m ret dir=against exit 15:55 | negative pre-2023 | 2579 | -14.4 | -28.7 | -23.0 | 14.4 | -0.73 / -1.46 / -1.17 | 19.5 / 5.2 |
| YM 5 (diag) entry 15:00 prior 90m ret dir=against exit 15:55 | negative pre-2023 | 2592 | -8.8 | -23.2 | -17.4 | 14.4 | -0.34 / -0.89 / -0.67 | 7.1 / -7.3 |
| YM 6 (diag) entry 15:30 prior 30m ret dir=with exit 15:55 | gross-positive, cost-negative pre-2023 | 2560 | 5.1 | -9.2 | -3.5 | 14.4 | 0.26 / -0.46 / -0.17 | 4.0 / -10.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 2 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.13, p(top) = 0.27); NQ: 5 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.07, p(top) = 0.07); RTY: 1 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 0.41, p(top) = 0.26); YM: 3 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.07, p(top) = 0.40).
- Of 11 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (NQ entry 15:30 prior 90m ret dir=against exit 15:55); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell NQ entry 15:00 prior 60m ret dir=against exit 15:55: uplift +0.18/+0.19/+0.20, boot lo -0.02, plateau 1.00, 2x-slip +0.16, wd corr +0.27, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 11}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bj_2.py, ap_bj_pipe.py (= ap_b_pipe2 with module swap), ap_bj_job.sh, ap_sw_common.py, ap_bj_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bj2/ (`BJ2_CO_all_selected_scored.csv`).

## LEAD detail (worker BK, after the pipeline run)
- Cell: NQ, 15:00 ET, fade the prior-60-minute return (short after a rise, long after a fall), time exit 15:55 (55 min). 496 clean / 799 pair-window trades (not small-sample). The pipeline null here is the NEW drift- and clock-matched random-entry null (entries at 15:00 only, real long/short mix, 200 replicates).
- DIRECTION: the pre-registered sign was WITH (momentum into the close); the selected cell is AGAINST (reversal). The grid contained both directions, selection was clean-only, but the result is opposite to the registered prior, so it is a post-hoc reading that needs independent confirmation.
- Standalone weekly Sharpe clean 1.13 / H1 1.57 / H2 0.80 / all-in 1.08 (null p95 0.78, rank 0.985; OOS H1+H2 1.03, null p95 1.48, rank 0.895). Additive uplift at 20% +0.18 / +0.19 / +0.20 (all-in +0.19), at 10% +0.10 / +0.11 / +0.13, at 30% +0.24 / +0.23 / +0.22, at 50% +0.32 / +0.22 / +0.11; 2x slippage uplift +0.15 / +0.16 / +0.18 (all-in +0.16); plateau 1.0 (2 of 2 neighbours); worst-decile corr +0.27 (<= +0.30, close).
- FAILED gates: bootstrap 90% CI lower bound -0.017 at 20% (needs > 0); worst week of pair + 20% sleeve -113.6k (H2) vs pair -82.9k, i.e. 37.6% worse, above the 20% share allowance; ERA flag NEGATIVE pre-2023 (gross -$9 per trade, net -$24, price-scaled net -$15; 2013-22 Sharpe -0.53), i.e. the reversal is a modern-era effect; false-selection test: 5 NQ cells pass the clean rule against a replicate mean of 2.2 (p(count) 0.065, p(top) 0.07) - at the edge of chance.
- Replication (ap_bi_rep, 20% share): H0 2023-02..07 uplift -0.24 (sleeve Sharpe -1.42; FAILS); alternating months odd/even +0.07 / +0.27 (needs >= 0.09 each; odd fails); the same cell on ES (+0.01 all-in; H0 -0.04; alt -0.02/+0.02), RTY (+0.01), YM do not replicate: the effect is NQ-only. Replications holding: none clean. LEAD only, not FOUND-PENDING.
- Insurance metrics of pair + 20% sleeve (weekly USD): clean Sharpe 1.6 (pair 1.46), Sortino 3.2, MAR 6.4, CVaR5 -81.9k, CVaR10 -78.0k, maxDD 241k, worst week -89.6k, %neg 42.9; H1 Sharpe 3.0, CVaR5 -75.4k, maxDD 134k, worst week -86.7k; H2 Sharpe 2.7, CVaR5 -99.4k, CVaR10 -82.4k, maxDD 241k, worst week -113.6k, %neg 38.9; all-in Sharpe 2.1, Sortino 4.2, MAR 12.9, CVaR5 -86.3k, CVaR10 -79.2k, maxDD 241k, worst week -113.6k, %neg 42.3. The sleeve improves Sharpe and maxDD but deepens the worst week and CVaR5 (not an insurance book).
- Sized dollars: sleeve scale 25.5 NQ contracts = the pair's clean weekly sigma; 20% share = 5.1 NQ contracts, 30% = 7.7. Worst single 1-contract trade -$6,489 (about -$33k at 5.1 contracts, -$50k at 7.7). Trades daily (about 250/yr), 55-minute hold, no stop.
- Executability: NT8 time-based strategy on NQ (or MNQ): at 15:00 ET compute the 60-minute return, enter against it at the next bar open, flat at 15:55 ET; no stop recommended by the test (a stop was not tested); separate from DualStrat but it trades the same instrument in the pair's RTH window, so it needs its own account (netting with ST/HM).

DONE BJ2
