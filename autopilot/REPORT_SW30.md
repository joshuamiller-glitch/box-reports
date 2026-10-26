# REPORT SW30 - VIX-state gating of equity-index trend/fade sleeves (D08 H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 11 selected cells (+6 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.19; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- State of the previous available day from data/gap/vix: VIX level percentile vs prior 250 days (hi >= 0.67 / lo <= 0.33) or VIX/VIX3M ratio (hi >= 1.0 / lo <= 0.85). ST(14,2) / Donchian-20 / VWAP-band 2.0 on 5/15-min bars, with/against, hold 60/180 min.
- Instruments: ES, NQ, RTY, YM. Grid: 96 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      96 |         92 |         2 |               1.189 |                2 |          2 |            3 |
| NQ    |      96 |         92 |        15 |               1.226 |                2 |          0 |            0 |
| RTY   |      96 |         92 |         6 |               1.049 |                2 |          6 |            3 |
| YM    |      96 |         92 |         5 |               1.516 |                2 |          3 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    2 |             2.08 |               5 |       0.66 |                       0.721 |            0.511 |           0.975 |     0.2  |       1.141 |                1.367 |
| NQ    |     100 |                   15 |             9.35 |              16 |       0.04 |                       0.811 |            0.697 |           0.964 |     0.23 |       1.226 |                1.852 |
| RTY   |     100 |                    6 |             3.18 |               8 |       0.08 |                       0.545 |            0.589 |           1.123 |     0.45 |       0.947 |                1.732 |
| YM    |     100 |                    5 |             3.96 |              12 |       0.34 |                       0.41  |            0.527 |           0.835 |     0.73 |       0.7   |                1.483 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | 645 | 2 | 1.14 | 0.05 | 0.67 | -0.04 / 1.28 | 0.19 / -0.30 / 0.26 | 0.04 | -0.09 | 0.98 | -0.05 | 0.50 | 939 | NO |
| ES 2 | 5m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | 573 | 2 | 0.30 | -0.39 | 0.18 | -0.01 / 1.17 | 0.08 / 0.10 / -0.19 | -0.05 | -0.12 | 0.85 | -0.16 | 0.50 | 810 | NO |
| ES 3 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-term hi1.0 | 88 | 1 | 1.19 | 0.24 | 0.51 | -0.85 / 1.07 | 0.18 / -0.08 / -0.27 | 0.03 | -0.54 | 0.87 | -0.11 | 0.50 | 114 | diag |
| ES 4 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=60m VIX-term hi1.0 | 121 | 1 | 0.97 | -0.44 | 0.79 | 0.41 / 1.15 | 0.15 / -0.01 / 0.04 | 0.07 | -0.54 | 0.97 | -0.03 | 0.33 | 155 | diag |
| ES 5 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | 430 | 1 | 0.84 | -0.08 | 0.82 | 0.78 / 1.17 | 0.12 / 0.41 / 0.00 | 0.06 | -0.28 | 0.99 | -0.03 | 0.50 | 609 | diag |
| RTY 1 | 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | 618 | 2 | 0.95 | 0.27 | 0.89 | 0.82 / 1.40 | 0.18 / -0.14 / 0.49 | 0.15 | -0.56 | 0.97 | 0.02 | 0.17 | 907 | NO |
| RTY 2 | 5m st[14, 2.0] dir=against hold=180m VIX-lvl lo0.33 | 904 | 2 | 0.77 | -1.10 | 0.39 | -0.02 / 0.92 | 0.14 / 0.10 / -0.40 | -0.08 | 0.10 | 0.97 | -0.20 | 0.25 | 1485 | NO |
| RTY 3 | 5m don[20] dir=against hold=180m VIX-lvl hi0.67 | 1008 | 2 | 0.66 | -0.48 | 0.13 | -0.55 / 0.71 | 0.14 / -0.81 / 0.26 | -0.03 | 0.08 | 0.94 | -0.18 | 0.67 | 1451 | NO |
| RTY 4 | 15m vwz[2.0, 'globex'] dir=against hold=60m VIX-lvl lo0.33 | 636 | 2 | 0.44 | -1.33 | -0.45 | -1.54 / 0.09 | 0.06 / -0.50 / -0.46 | -0.27 | -0.00 | 0.99 | -0.33 | 0.00 | 1072 | NO |
| RTY 5 | 15m don[20] dir=against hold=60m VIX-lvl hi0.67 | 992 | 2 | 0.40 | -0.10 | -0.14 | -0.81 / 0.56 | 0.10 / -0.51 / -0.07 | -0.13 | -0.36 | 0.96 | -0.22 | 0.00 | 1463 | NO |
| RTY 6 | 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | 439 | 2 | 0.06 | -0.31 | 0.36 | 1.03 / 0.91 | 0.02 / -0.03 / 0.33 | 0.04 | 0.14 | 0.95 | -0.08 | 0.33 | 624 | NO |
| RTY 7 (diag) | 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-term hi1.0 | 84 | 1 | 1.05 | -0.08 | 0.74 | -0.19 / 1.34 | 0.19 / -0.02 / -0.05 | 0.10 | 0.54 | 0.90 | -0.01 | 0.67 | 109 | diag |
| RTY 8 (diag) | 5m vwz[2.0, 'globex'] dir=with hold=60m VIX-term hi1.0 | 171 | 1 | 0.98 | -0.54 | 0.30 | -0.81 / 1.14 | 0.17 / -0.04 / -0.44 | -0.03 | 0.07 | 0.92 | -0.17 | 0.17 | 220 | diag |
| RTY 9 (diag) | 5m st[14, 2.0] dir=with hold=180m VIX-lvl hi0.67 | 889 | 1 | 0.96 | -0.59 | 0.34 | -0.63 / 1.08 | 0.09 / -0.22 / -0.02 | -0.05 | 0.21 | 0.94 | -0.16 | 0.25 | 1294 | diag |
| YM 1 | 5m don[20] dir=with hold=180m VIX-lvl hi0.67 | 1007 | 2 | 0.70 | -0.50 | 0.21 | -0.76 / 0.99 | 0.08 / 0.13 / -0.32 | -0.06 | 0.28 | 0.88 | -0.16 | 0.00 | 1450 | NO |
| YM 2 | 5m vwz[2.0, 'globex'] dir=against hold=180m VIX-lvl hi0.67 | 609 | 2 | 0.48 | -0.20 | 0.44 | 0.36 / 1.37 | 0.02 / 0.18 / -0.04 | -0.02 | 0.20 | 0.93 | -0.17 | 0.33 | 863 | NO |
| YM 3 | 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | 883 | 2 | 0.38 | -0.48 | 0.57 | 0.80 / 0.86 | 0.06 / -0.11 / 0.11 | 0.01 | -0.08 | 0.96 | -0.13 | 0.38 | 1283 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 6 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 14 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 9 |
| worst-decile corr <= +0.30 | 16 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | clean | 1.14 | 2.30 | -109557 | -85900 | 333098 | -140161 | 3.09 | 22.9 | 1.65 | -82859 | 250145 | -93375 |
| ES 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | H1 | -2.64 | -2.59 | -110138 | -99221 | 426251 | -116336 | -0.86 | 21.4 | 2.53 | -70771 | 152849 | -70938 |
| ES 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | H2 | 0.84 | 1.79 | -103543 | -96457 | 393333 | -105648 | 0.88 | 25.0 | 2.74 | -93165 | 217425 | -98277 |
| ES 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | all | 0.67 | 1.28 | -113136 | -95458 | 621610 | -140161 | 1.62 | 23.2 | 2.02 | -84578 | 250145 | -98277 |
| RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | clean | 0.94 | 2.15 | -92077 | -78329 | 396873 | -99752 | 2.15 | 21.9 | 1.64 | -80590 | 261133 | -86096 |
| RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | H1 | -1.83 | -2.14 | -72445 | -64013 | 247326 | -94317 | -0.89 | 25.0 | 2.69 | -65354 | 169785 | -69079 |
| RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | H2 | 1.62 | 3.48 | -156589 | -117611 | 319601 | -207753 | 2.40 | 19.4 | 2.98 | -86834 | 217425 | -91958 |
| RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | all | 0.89 | 1.90 | -107376 | -86997 | 437217 | -207753 | 3.20 | 22.0 | 2.09 | -81735 | 261133 | -91958 |
| YM 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | clean | 0.38 | 0.67 | -121352 | -99498 | 426197 | -157829 | 0.82 | 23.8 | 1.52 | -80434 | 279919 | -85989 |
| YM 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | H1 | -0.39 | -0.51 | -145170 | -133390 | 370563 | -152510 | -0.24 | 14.3 | 2.72 | -95496 | 165199 | -104498 |
| YM 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | H2 | 1.42 | 2.86 | -163119 | -126264 | 315847 | -174973 | 2.09 | 16.7 | 2.60 | -102553 | 217425 | -109907 |
| YM 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | all | 0.57 | 0.99 | -145938 | -115903 | 426197 | -174973 | 2.15 | 20.8 | 1.95 | -89913 | 279919 | -109907 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | -19.0 | -3.8 | 16.3 | 42.3 | 8.9 / 17.9 | 32.3 / 37.0 | NO |
| RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | -14.7 | 7.6 | 23.8 | 40.2 | 17.5 / 25.0 | 40.8 / 43.7 | NO |
| YM 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | -20.0 | -22.6 | 4.4 | 27.7 | -1.8 / 21.7 | -21.6 / -4.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | positive pre-2023 | 2656 | 32.5 | 3.1 | 17.6 | 29.4 | 0.56 / 0.05 / 0.31 | 90.8 / 61.4 |
| ES 2 5m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 2359 | 11.2 | -18.2 | -3.8 | 29.4 | 0.24 / -0.39 / -0.08 | 45.8 / 16.4 |
| ES 3 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-term hi1.0 | positive pre-2023 | 421 | 62.8 | 33.5 | 48.9 | 29.4 | 0.44 / 0.24 / 0.34 | 280.5 / 251.2 |
| ES 4 (diag) 15m vwz[2.0, 'globex'] dir=with hold=60m VIX-term hi1.0 | negative pre-2023 | 556 | -6.4 | -35.7 | -20.3 | 29.4 | -0.08 / -0.44 / -0.25 | 146.0 / 116.6 |
| ES 5 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 1720 | 24.7 | -4.7 | 9.5 | 29.4 | 0.41 / -0.08 / 0.16 | 87.7 / 58.3 |
| RTY 1 15m don[20] dir=against hold=180m VIX-lvl hi0.67 | positive pre-2023 | 1707 | 23.8 | 9.5 | 12.6 | 14.4 | 0.68 / 0.27 / 0.36 | 54.8 / 40.4 |
| RTY 2 5m st[14, 2.0] dir=against hold=180m VIX-lvl lo0.33 | negative pre-2023 | 2659 | -7.0 | -21.4 | -20.1 | 14.4 | -0.38 / -1.10 / -1.03 | 30.1 / 15.8 |
| RTY 3 5m don[20] dir=against hold=180m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 2735 | 1.1 | -13.2 | -10.1 | 14.4 | 0.04 / -0.48 / -0.36 | 33.4 / 19.0 |
| RTY 4 15m vwz[2.0, 'globex'] dir=against hold=60m VIX-lvl lo0.33 | negative pre-2023 | 1794 | -5.1 | -19.4 | -18.3 | 14.4 | -0.36 / -1.33 / -1.25 | 18.6 / 4.2 |
| RTY 5 15m don[20] dir=against hold=60m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 2730 | 12.8 | -1.5 | 1.6 | 14.4 | 0.81 / -0.10 / 0.10 | 21.0 / 6.7 |
| RTY 6 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 1143 | 2.4 | -12.0 | -8.9 | 14.4 | 0.06 / -0.31 / -0.23 | 16.8 / 2.4 |
| RTY 7 (diag) 15m vwz[2.0, 'globex'] dir=with hold=180m VIX-term hi1.0 | gross-positive, cost-negative pre-2023 | 302 | 6.4 | -7.9 | -3.7 | 14.4 | 0.07 / -0.08 / -0.04 | 191.2 / 176.9 |
| RTY 8 (diag) 5m vwz[2.0, 'globex'] dir=with hold=60m VIX-term hi1.0 | negative pre-2023 | 622 | -7.2 | -21.6 | -17.4 | 14.4 | -0.18 / -0.54 / -0.44 | 55.6 / 41.2 |
| RTY 9 (diag) 5m st[14, 2.0] dir=with hold=180m VIX-lvl hi0.67 | negative pre-2023 | 2476 | -5.3 | -19.7 | -16.5 | 14.4 | -0.16 / -0.59 / -0.50 | 46.0 / 31.6 |
| YM 1 5m don[20] dir=with hold=180m VIX-lvl hi0.67 | negative pre-2023 | 4287 | -1.7 | -16.1 | -10.1 | 14.4 | -0.05 / -0.50 / -0.32 | 42.4 / 28.0 |
| YM 2 5m vwz[2.0, 'globex'] dir=against hold=180m VIX-lvl hi0.67 | gross-positive, cost-negative pre-2023 | 2466 | 6.5 | -7.9 | -2.0 | 14.4 | 0.16 / -0.20 / -0.05 | 33.8 / 19.4 |
| YM 3 5m st[14, 2.0] dir=against hold=180m VIX-lvl hi0.67 | negative pre-2023 | 3872 | -7.2 | -21.6 | -15.7 | 14.4 | -0.16 / -0.48 / -0.35 | 27.8 / 13.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 2 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.66, p(top) = 0.20); NQ: 15 cells pass the clean rule against a replicate mean of 9.3 (p(count) = 0.04, p(top) = 0.23); RTY: 6 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.08, p(top) = 0.45); YM: 5 cells pass the clean rule against a replicate mean of 4.0 (p(count) = 0.34, p(top) = 0.73).
- Of 11 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.19 (RTY 15m don[20] dir=against hold=180m VIX-lvl hi0.67); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 5, 'negative pre-2023': 4, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_30.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw30/ (`SW30_CO_all_selected_scored.csv`).

DONE SW30
