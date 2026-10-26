# REPORT Q30 - Q30: Friday-afternoon position squaring: week-to-date return traded 13:00-16:00 ET with/against

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 12 selected cells (+6 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +1.05.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: Friday-afternoon position squaring: week-to-date return traded 13:00-16:00 ET with/against. Time exit, no stop.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, 6E. Grid: 36 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      36 |         36 |         0 |               0.324 |                1 |          0 |            0 |
| CL    |      36 |         36 |         9 |               0.884 |                2 |          0 |            0 |
| ES    |      36 |         36 |         2 |               1.075 |                2 |          1 |            0 |
| GC    |      36 |         36 |        12 |               1.423 |                2 |          0 |            0 |
| NQ    |      36 |         36 |         2 |               0.617 |                2 |          0 |            0 |
| RTY   |      36 |         36 |         4 |               0.906 |                2 |          4 |            3 |
| YM    |      36 |         36 |         7 |               0.827 |                2 |          7 |            0 |
| ZN    |      36 |         36 |         0 |              -0.499 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            5.085 |              12 |      0.955 |                       0.696 |            0.721 |           1.06  |    0.5   |       1.075 |                1.783 |
| NQ    |     200 |                    2 |            7.095 |              14 |      0.99  |                       0.344 |            0.77  |           1.065 |    0.995 |       0.439 |                1.923 |
| RTY   |     200 |                    4 |            5.83  |              13 |      0.865 |                       0.579 |            0.739 |           1.044 |    0.785 |       0.906 |                1.887 |
| YM    |     200 |                    7 |            5.545 |              11 |      0.285 |                       0.315 |            0.74  |           1.012 |    0.99  |       0.755 |                1.748 |
| GC    |     200 |                   12 |            4.93  |              11 |      0     |                       1.037 |            0.752 |           1.081 |    0.095 |       1.423 |                1.834 |
| CL    |     200 |                    9 |            4.295 |              10 |      0.045 |                       0.495 |            0.727 |           1.12  |    0.885 |       0.884 |                1.858 |
| ZN    |     200 |                    0 |            0.25  |               3 |      1     |                     nan     |            0.432 |           0.732 |  nan     |     nan     |                0.732 |
| 6E    |     200 |                    0 |            2.915 |               8 |      1     |                     nan     |            0.639 |           1.115 |  nan     |     nan     |                1.507 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | fri (0, 0.5, 120, 1) | 76 | 2 | 1.08 | 0.05 | 0.98 | 0.81 / 1.44 | 0.12 / -0.04 / 0.24 | 0.08 | 0.45 | 0.96 | -0.07 | 0.50 | 111 | NO |
| RTY 1 | fri (0, 0.5, 170, -1) | 69 | 2 | 0.91 | -0.29 | 1.05 | 1.25 / 1.41 | 0.20 / 0.31 / -0.00 | 0.16 | -0.47 | 0.99 | 0.01 | 0.50 | 111 | NO |
| RTY 2 | fri (0, 0.5, 120, -1) | 69 | 2 | 0.66 | -0.51 | 0.97 | 1.40 / 1.19 | 0.13 / 0.36 / 0.00 | 0.12 | -0.46 | 0.98 | -0.03 | 0.50 | 111 | NO |
| RTY 3 | fri (0, 0.5, 60, -1) | 69 | 2 | 0.52 | -0.08 | 0.75 | 1.26 / 1.08 | 0.09 / 0.14 / 0.04 | 0.07 | -0.49 | 0.96 | -0.06 | 0.50 | 111 | NO |
| RTY 4 | fri (0, 0.0, 60, -1) | 95 | 2 | 0.23 | -0.43 | 0.28 | 0.38 / 0.95 | 0.02 / 0.12 / -0.20 | -0.04 | -0.40 | 0.81 | -0.17 | 0.00 | 153 | NO |
| RTY 5 (diag) | fri (30, 1.0, 120, -1) | 48 | 1 | 0.84 | -0.51 | 0.61 | 0.42 / 1.64 | 0.14 / 0.31 / -0.30 | 0.05 | -0.41 | 0.89 | -0.15 | 0.50 | 75 S | diag |
| RTY 6 (diag) | fri (30, 1.0, 60, -1) | 48 | 1 | 0.47 | -0.63 | 0.69 | 1.06 / 1.23 | 0.05 / 0.40 / -0.15 | 0.03 | -0.50 | 0.92 | -0.11 | 0.50 | 75 S | diag |
| RTY 7 (diag) | fri (0, 1.0, 170, -1) | 47 | 1 | 0.44 | -0.24 | 0.63 | 0.86 / 1.24 | 0.11 / 0.34 / -0.17 | 0.08 | -0.47 | 0.91 | -0.09 | 0.50 | 75 S | diag |
| YM 1 | fri (30, 0.5, 120, 1) | 71 | 2 | 0.75 | 0.08 | 0.23 | -0.51 / 1.33 | 0.12 / -0.36 / -0.02 | 0.00 | 0.20 | 0.78 | -0.17 | 0.00 | 111 | NO |
| YM 2 | fri (30, 1.0, 120, 1) | 43 | 2 | 0.38 | 0.06 | -0.15 | -1.08 / 1.33 | 0.03 / -0.26 / -0.22 | -0.08 | 0.51 | 0.51 | -0.24 | 0.00 | 65 S | NO |
| YM 3 | fri (30, 0.0, 60, 1) | 95 | 2 | 0.26 | -0.22 | -0.42 | -1.58 / 1.01 | 0.04 / -0.47 / -0.18 | -0.11 | 0.18 | 0.27 | -0.28 | 0.00 | 153 | NO |
| YM 4 | fri (0, 0.5, 120, 1) | 71 | 2 | 0.24 | -0.11 | -0.22 | -1.01 / 1.30 | -0.01 / -0.20 / -0.10 | -0.09 | 0.13 | 0.36 | -0.25 | 0.00 | 110 | NO |
| YM 5 | fri (0, 0.0, 170, 1) | 95 | 2 | 0.24 | -0.05 | -0.53 | -1.72 / 1.40 | -0.02 / -0.54 / -0.21 | -0.16 | 0.22 | 0.23 | -0.34 | 0.00 | 153 | NO |
| YM 6 | fri (0, 0.5, 60, 1) | 71 | 2 | 0.17 | -0.28 | -0.18 | -0.96 / 1.18 | -0.04 / -0.30 / -0.01 | -0.11 | 0.36 | 0.57 | -0.26 | 0.00 | 110 | NO |
| YM 7 | fri (0, 1.0, 170, 1) | 46 | 2 | 0.16 | -0.04 | -0.40 | -1.50 / 1.27 | -0.03 / -0.24 / -0.22 | -0.12 | 0.54 | 0.30 | -0.30 | 0.00 | 67 S | NO |
| ZN 1 (diag) | fri (0, 0.5, 120, 1) | 67 | 0 | -0.50 | -1.70 | -0.87 | -1.78 / -0.24 | -0.11 / -0.55 / -0.07 | -0.49 | -0.10 | 0.80 | -0.34 | 0.00 | 113 | diag |
| ZN 2 (diag) | fri (0, 0.5, 170, 1) | 67 | 0 | -0.58 | -1.70 | -0.89 | -1.51 / 0.08 | -0.13 / -0.53 / -0.08 | -0.48 | -0.07 | 0.69 | -0.36 | 0.00 | 113 | diag |
| ZN 3 (diag) | fri (0, 0.0, 120, 1) | 95 | 0 | -0.61 | -2.12 | -1.05 | -2.15 / -0.14 | -0.11 / -0.74 / -0.06 | -0.60 | -0.49 | 0.87 | -0.37 | 0.00 | 153 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 12 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 8 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 5 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES fri (0, 0.5, 120, 1) | clean | 1.07 | 1.71 | -137826 | -100210 | 394608 | -210159 | 2.46 | 30.5 | 1.58 | -90096 | 332785 | -123906 |
| ES fri (0, 0.5, 120, 1) | H1 | -0.28 | -0.33 | -175707 | -139540 | 317475 | -250268 | -0.21 | 14.3 | 2.79 | -77029 | 165154 | -77125 |
| ES fri (0, 0.5, 120, 1) | H2 | 1.66 | 4.15 | -89318 | -66436 | 286048 | -99088 | 1.77 | 27.8 | 2.73 | -83060 | 217425 | -83595 |
| ES fri (0, 0.5, 120, 1) | all | 0.98 | 1.55 | -142397 | -103202 | 394608 | -250268 | 3.57 | 27.4 | 2.01 | -87529 | 332785 | -123906 |
| RTY fri (0, 0.5, 170, -1) | clean | 0.90 | 1.65 | -116822 | -90124 | 228510 | -162774 | 3.58 | 28.6 | 1.66 | -82782 | 261651 | -87587 |
| RTY fri (0, 0.5, 170, -1) | H1 | 1.90 | 3.89 | -115266 | -107631 | 230533 | -116115 | 2.49 | 21.4 | 3.13 | -76242 | 146385 | -76932 |
| RTY fri (0, 0.5, 170, -1) | H2 | 0.65 | 0.94 | -162349 | -114630 | 215371 | -215371 | 0.98 | 22.2 | 2.48 | -82605 | 225717 | -82686 |
| RTY fri (0, 0.5, 170, -1) | all | 1.05 | 1.84 | -130160 | -101843 | 230533 | -215371 | 6.96 | 26.2 | 2.09 | -82221 | 261651 | -87587 |
| YM fri (30, 0.5, 120, 1) | clean | 0.75 | 1.25 | -129497 | -101771 | 523139 | -169193 | 1.30 | 29.5 | 1.58 | -85040 | 353721 | -109850 |
| YM fri (30, 0.5, 120, 1) | H1 | -1.09 | -1.44 | -143910 | -128154 | 359170 | -160399 | -0.83 | 39.3 | 2.47 | -78480 | 169712 | -80027 |
| YM fri (30, 0.5, 120, 1) | H2 | -0.07 | -0.11 | -134017 | -114047 | 568745 | -151605 | -0.05 | 36.1 | 2.46 | -82978 | 218872 | -83431 |
| YM fri (30, 0.5, 120, 1) | all | 0.23 | 0.36 | -138169 | -114704 | 568745 | -169193 | 0.63 | 32.7 | 1.92 | -84152 | 353721 | -109850 |
| ZN fri (0, 0.5, 120, 1) (diag) | clean | -0.50 | -0.60 | -172275 | -125785 | 733650 | -294718 | -0.61 | 33.3 | 1.35 | -84636 | 334380 | -92737 |
| ZN fri (0, 0.5, 120, 1) (diag) | H1 | -3.00 | -2.98 | -121857 | -111053 | 537422 | -121857 | -0.93 | 42.9 | 2.28 | -89796 | 162004 | -101304 |
| ZN fri (0, 0.5, 120, 1) (diag) | H2 | -0.86 | -1.12 | -100249 | -86744 | 373605 | -121857 | -0.51 | 47.2 | 2.41 | -82471 | 207224 | -82524 |
| ZN fri (0, 0.5, 120, 1) (diag) | all | -0.87 | -1.04 | -156669 | -117408 | 1517541 | -294718 | -0.75 | 38.1 | 1.73 | -86007 | 334380 | -101304 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES fri (0, 0.5, 120, 1) | -14.6 | -45.8 | 9.5 | 1.8 | -47.0 / 1.3 | 31.2 / 31.1 | NO |
| RTY fri (0, 0.5, 170, -1) | -12.5 | 5.8 | 21.6 | 25.4 | 5.0 / 18.3 | 31.2 / 31.5 | NO |
| YM fri (30, 0.5, 120, 1) | -26.1 | -20.3 | 16.4 | -9.4 | -21.3 / 13.7 | 26.7 / 27.0 | NO |
| ZN fri (0, 0.5, 120, 1) (diag) | -42.5 | -9.6 | 12.1 | 0.9 | 5.3 / 11.5 | -15.5 / 6.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 fri (0, 0.5, 120, 1) | positive pre-2023 | 346 | 34.2 | 4.8 | 18.8 | 29.4 | 0.35 / 0.05 / 0.19 | 184.5 / 155.2 |
| RTY 1 fri (0, 0.5, 170, -1) | negative pre-2023 | 206 | -11.3 | -25.6 | -23.3 | 14.4 | -0.13 / -0.29 / -0.26 | 84.2 / 69.8 |
| RTY 2 fri (0, 0.5, 120, -1) | negative pre-2023 | 206 | -21.3 | -35.7 | -33.4 | 14.4 | -0.30 / -0.51 / -0.48 | 61.6 / 47.2 |
| RTY 3 fri (0, 0.5, 60, -1) | gross-positive, cost-negative pre-2023 | 206 | 10.1 | -4.3 | -2.0 | 14.4 | 0.18 / -0.08 / -0.04 | 49.5 / 35.1 |
| RTY 4 fri (0, 0.0, 60, -1) | negative pre-2023 | 288 | -6.1 | -20.4 | -18.2 | 14.4 | -0.13 / -0.43 / -0.38 | 26.2 / 11.9 |
| RTY 5 (diag) fri (30, 1.0, 120, -1) | negative pre-2023 | 142 | -30.6 | -45.0 | -42.6 | 14.4 | -0.35 / -0.51 / -0.48 | 65.5 / 51.2 |
| RTY 6 (diag) fri (30, 1.0, 60, -1) | negative pre-2023 | 142 | -24.0 | -38.3 | -35.9 | 14.4 | -0.39 / -0.63 / -0.59 | 44.6 / 30.2 |
| RTY 7 (diag) fri (0, 1.0, 170, -1) | negative pre-2023 | 141 | -11.8 | -26.1 | -23.7 | 14.4 | -0.11 / -0.24 / -0.22 | 52.1 / 37.8 |
| YM 1 fri (30, 0.5, 120, 1) | positive pre-2023 | 356 | 21.1 | 6.7 | 12.5 | 14.4 | 0.25 / 0.08 / 0.15 | 79.8 / 65.4 |
| YM 2 fri (30, 1.0, 120, 1) | positive pre-2023 | 232 | 21.4 | 7.0 | 12.8 | 14.4 | 0.19 / 0.06 / 0.11 | 55.3 / 41.0 |
| YM 3 fri (30, 0.0, 60, 1) | gross-positive, cost-negative pre-2023 | 496 | 4.6 | -9.8 | -4.1 | 14.4 | 0.10 / -0.22 / -0.09 | 32.2 / 17.9 |
| YM 4 fri (0, 0.5, 120, 1) | gross-positive, cost-negative pre-2023 | 363 | 6.4 | -8.0 | -2.2 | 14.4 | 0.09 / -0.11 / -0.03 | 39.4 / 25.1 |
| YM 5 fri (0, 0.0, 170, 1) | gross-positive, cost-negative pre-2023 | 497 | 10.5 | -3.9 | 1.8 | 14.3 | 0.13 / -0.05 / 0.02 | 38.4 / 24.1 |
| YM 6 fri (0, 0.5, 60, 1) | negative pre-2023 | 363 | -0.1 | -14.5 | -8.7 | 14.4 | -0.00 / -0.28 / -0.17 | 27.9 / 13.5 |
| YM 7 fri (0, 1.0, 170, 1) | gross-positive, cost-negative pre-2023 | 235 | 9.1 | -5.2 | 0.6 | 14.4 | 0.07 / -0.04 / 0.00 | 36.1 / 21.7 |
| ZN 1 (diag) fri (0, 0.5, 120, 1) | gross-positive, cost-negative pre-2023 | 354 | 4.1 | -31.5 | -36.7 | 35.6 | 0.22 / -1.70 / -1.97 | 25.9 / -9.7 |
| ZN 2 (diag) fri (0, 0.5, 170, 1) | gross-positive, cost-negative pre-2023 | 354 | 0.3 | -35.3 | -40.5 | 35.6 | 0.01 / -1.70 / -1.94 | 23.3 / -12.3 |
| ZN 3 (diag) fri (0, 0.0, 120, 1) | gross-positive, cost-negative pre-2023 | 494 | 1.4 | -34.1 | -39.3 | 35.5 | 0.08 / -2.12 / -2.43 | 26.3 / -9.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 1.00); CL: 9 cells pass the clean rule against a replicate mean of 4.3 (p(count) = 0.04, p(top) = 0.89); ES: 2 cells pass the clean rule against a replicate mean of 5.1 (p(count) = 0.95, p(top) = 0.50); GC: 12 cells pass the clean rule against a replicate mean of 4.9 (p(count) = 0.00, p(top) = 0.10); NQ: 2 cells pass the clean rule against a replicate mean of 7.1 (p(count) = 0.99, p(top) = 0.99); RTY: 4 cells pass the clean rule against a replicate mean of 5.8 (p(count) = 0.86, p(top) = 0.79); YM: 7 cells pass the clean rule against a replicate mean of 5.5 (p(count) = 0.28, p(top) = 0.99); ZN: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00).
- Of 12 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.19 (RTY fri (0, 0.5, 170, -1)); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 5, 'negative pre-2023': 4, 'positive pre-2023': 3}.

- Note: Selection minimum trades 40 (weekly event).

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q30.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q30/ (`Q30_CO_all_selected_scored.csv`).

DONE Q30
