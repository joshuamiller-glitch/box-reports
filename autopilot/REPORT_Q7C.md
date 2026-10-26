# REPORT Q7C - Q7C: B11 grid on FX (6E, 6J, 6B, 6A, 6C)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe +0.12.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: 6E, 6J, 6B, 6A, 6C. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |     192 |        192 |         0 |              -0.092 |                1 |          0 |            3 |
| 6B    |     192 |        192 |         0 |               0.065 |                1 |          0 |            3 |
| 6C    |     192 |        192 |         0 |              -0.682 |                1 |          0 |            3 |
| 6E    |     192 |        192 |         0 |               0.485 |                1 |          0 |            3 |
| 6J    |     192 |        192 |         0 |              -0.068 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| 6E    |     100 |                    0 |             2.78 |               9 |          1 |                         nan |            0.49  |           0.854 |      nan |         nan |                1.248 |
| 6J    |     100 |                    0 |             1.14 |               5 |          1 |                         nan |            0.496 |           0.922 |      nan |         nan |                1.153 |
| 6B    |     100 |                    0 |             0.33 |               2 |          1 |                         nan |            0.503 |           0.916 |      nan |         nan |                1.05  |
| 6A    |     100 |                    0 |             0.09 |               1 |          1 |                         nan |            0.272 |           0.475 |      nan |         nan |                0.475 |
| 6C    |     100 |                    0 |             0.18 |               2 |          1 |                         nan |            0.42  |           0.655 |      nan |         nan |                0.655 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) | PD 5m with exit=b10.3xADR | 387 | 1 | 0.48 | -2.70 | 0.12 | -0.71 / 0.18 | 0.12 / 0.02 / -0.24 | -0.09 | -0.25 | 0.98 | -0.16 | 0.00 | 602 | diag |
| 6E 2 (diag) | OR60 5m fade exit=hd0.2xADR | 489 | 1 | -0.05 | -0.56 | -0.62 | -1.66 / 0.63 | -0.07 / -0.61 / -0.18 | -0.30 | -0.35 | 0.71 | -0.33 | 0.00 | 785 | diag |
| 6E 3 (diag) | OR60 5m fade exit=b20.2xADR | 489 | 1 | -0.06 | 1.26 | -0.75 | -2.09 / 0.30 | -0.07 / -0.80 / -0.11 | -0.32 | -0.38 | 0.76 | -0.35 | 0.00 | 785 | diag |
| 6J 1 (diag) | OR60 5m fade exit=tr0.3xADR | 481 | 1 | -0.07 | -1.91 | -0.90 | -3.30 / -0.82 | -0.02 / -0.72 / -0.16 | -0.36 | 0.11 | 0.94 | -0.32 | 0.00 | 771 | diag |
| 6J 2 (diag) | OR60 5m fade exit=b20.3xADR | 481 | 1 | -0.23 | -0.25 | -0.64 | -1.44 / -0.63 | -0.06 / -0.57 / -0.03 | -0.30 | 0.05 | 0.94 | -0.29 | 0.00 | 771 | diag |
| 6J 3 (diag) | OR60 15m with exit=hd0.3xADR | 472 | 1 | -0.27 | -2.59 | -0.72 | -1.75 / -0.22 | -0.10 / -0.04 / -0.44 | -0.35 | -0.30 | 0.84 | -0.35 | 0.00 | 757 | diag |
| 6B 1 (diag) | OR60 5m fade exit=b20.3xADR | 493 | 1 | 0.06 | -1.02 | -0.68 | -1.87 / -0.14 | -0.03 / -0.51 / -0.27 | -0.38 | -0.39 | 0.92 | -0.34 | 0.00 | 790 | diag |
| 6B 2 (diag) | OR60 5m fade exit=hd0.3xADR | 493 | 1 | -0.08 | -2.07 | -0.83 | -2.10 / -0.08 | -0.05 / -0.54 / -0.29 | -0.40 | -0.42 | 0.87 | -0.37 | 0.00 | 790 | diag |
| 6B 3 (diag) | OR60 5m fade exit=b10.3xADR | 493 | 1 | -0.27 | -0.78 | -1.03 | -2.28 / -0.27 | -0.13 / -0.52 / -0.31 | -0.45 | -0.48 | 0.94 | -0.41 | 0.00 | 790 | diag |
| 6A 1 (diag) | OR60 5m fade exit=b20.2xADR | 493 | 1 | -0.09 | -0.68 | -1.06 | -2.65 / -1.41 | -0.11 / -0.68 / -0.37 | -0.65 | 0.09 | 1.00 | -0.43 | 0.00 | 791 | diag |
| 6A 2 (diag) | OR60 5m fade exit=hd0.2xADR | 493 | 1 | -0.18 | -2.53 | -1.14 | -2.93 / -0.99 | -0.11 / -0.70 / -0.40 | -0.66 | -0.05 | 0.98 | -0.44 | 0.00 | 791 | diag |
| 6A 3 (diag) | OR60 5m fade exit=b20.3xADR | 493 | 0 | -0.35 | -0.48 | -1.31 | -3.01 / -0.75 | -0.15 / -0.67 / -0.46 | -0.66 | -0.31 | 0.91 | -0.49 | 0.00 | 791 | diag |
| 6C 1 (diag) | PD 15m fade exit=hd0.3xADR | 379 | 1 | -0.68 | -0.51 | -1.11 | -1.93 / -0.52 | -0.15 / -0.40 / -0.28 | -0.43 | 0.21 | 0.79 | -0.40 | 0.00 | 607 | diag |
| 6C 2 (diag) | OR30 15m with exit=b20.3xADR | 500 | 0 | -0.73 | -2.58 | -1.29 | -2.31 / -0.84 | -0.14 / -0.42 / -0.43 | -0.47 | -0.32 | 0.84 | -0.43 | 0.00 | 802 | diag |
| 6C 3 (diag) | PD 15m fade exit=hd0.2xADR | 379 | 0 | -0.88 | -0.75 | -1.13 | -1.63 / -0.30 | -0.19 / -0.40 / -0.15 | -0.42 | 0.38 | 0.79 | -0.39 | 0.00 | 607 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 1 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 3 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A OR60 5m fade exit=b20.2xADR (diag) | clean | -0.25 | -0.36 | -109775 | -98731 | 1023339 | -146022 | -0.22 | 53.3 | 1.35 | -87211 | 330875 | -95893 |
| 6A OR60 5m fade exit=b20.2xADR (diag) | H1 | -3.59 | -3.60 | -107169 | -100599 | 669344 | -119577 | -0.99 | 67.9 | 2.15 | -84242 | 159753 | -84645 |
| 6A OR60 5m fade exit=b20.2xADR (diag) | H2 | -2.03 | -2.34 | -130637 | -110549 | 671967 | -155529 | -0.85 | 66.7 | 1.92 | -85517 | 229997 | -86545 |
| 6A OR60 5m fade exit=b20.2xADR (diag) | all | -1.06 | -1.39 | -115772 | -102817 | 1991526 | -155529 | -0.74 | 58.9 | 1.60 | -86829 | 330875 | -95893 |
| 6B OR60 5m fade exit=b20.3xADR (diag) | clean | -0.01 | -0.01 | -123822 | -101571 | 714749 | -171558 | -0.01 | 50.5 | 1.43 | -87568 | 293321 | -104725 |
| 6B OR60 5m fade exit=b20.3xADR (diag) | H1 | -1.90 | -2.22 | -114845 | -107053 | 439289 | -135869 | -0.89 | 50.0 | 2.31 | -86546 | 173779 | -87541 |
| 6B OR60 5m fade exit=b20.3xADR (diag) | H2 | -1.84 | -2.13 | -123085 | -112297 | 713140 | -130833 | -0.79 | 61.1 | 2.03 | -90004 | 219780 | -103314 |
| 6B OR60 5m fade exit=b20.3xADR (diag) | all | -0.68 | -0.90 | -126707 | -109970 | 1427259 | -171558 | -0.67 | 53.0 | 1.70 | -89151 | 293321 | -104725 |
| 6C PD 15m fade exit=hd0.2xADR (diag) | clean | -0.91 | -1.37 | -94781 | -88034 | 1361375 | -100955 | -0.61 | 61.0 | 1.27 | -89971 | 303101 | -102065 |
| 6C PD 15m fade exit=hd0.2xADR (diag) | H1 | -1.37 | -1.91 | -83320 | -77862 | 401465 | -98897 | -0.63 | 64.3 | 2.42 | -87440 | 176433 | -90269 |
| 6C PD 15m fade exit=hd0.2xADR (diag) | H2 | -1.82 | -2.23 | -95670 | -80621 | 526420 | -112020 | -0.79 | 63.9 | 2.15 | -84839 | 196619 | -90505 |
| 6C PD 15m fade exit=hd0.2xADR (diag) | all | -1.13 | -1.61 | -96548 | -87644 | 2142275 | -112020 | -0.70 | 61.9 | 1.65 | -89468 | 303101 | -102065 |
| 6E PD 5m with exit=b10.3xADR (diag) | clean | 0.52 | 0.75 | -117948 | -106032 | 683172 | -126748 | 0.69 | 47.6 | 1.58 | -84283 | 262025 | -97168 |
| 6E PD 5m with exit=b10.3xADR (diag) | H1 | -0.03 | -0.04 | -78055 | -73618 | 348736 | -84801 | -0.02 | 57.1 | 2.85 | -77896 | 181670 | -87500 |
| 6E PD 5m with exit=b10.3xADR (diag) | H2 | -1.20 | -1.51 | -105770 | -89508 | 552088 | -109620 | -0.55 | 58.3 | 2.05 | -88601 | 224458 | -99071 |
| 6E PD 5m with exit=b10.3xADR (diag) | all | 0.12 | 0.17 | -113656 | -100336 | 683172 | -126748 | 0.24 | 51.8 | 1.89 | -86168 | 262025 | -99071 |
| 6J OR60 5m fade exit=b20.3xADR (diag) | clean | -0.32 | -0.49 | -112257 | -94980 | 1057203 | -135980 | -0.28 | 60.0 | 1.40 | -84388 | 293422 | -89804 |
| 6J OR60 5m fade exit=b20.3xADR (diag) | H1 | -3.26 | -3.37 | -93805 | -91412 | 590779 | -97770 | -0.95 | 67.9 | 2.25 | -80820 | 178417 | -93411 |
| 6J OR60 5m fade exit=b20.3xADR (diag) | H2 | 0.10 | 0.16 | -55208 | -50472 | 195871 | -55915 | 0.10 | 61.1 | 2.26 | -86193 | 204431 | -88047 |
| 6J OR60 5m fade exit=b20.3xADR (diag) | all | -0.64 | -0.93 | -107607 | -92420 | 1261895 | -135980 | -0.66 | 61.3 | 1.73 | -85792 | 293422 | -93411 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| 6E PD 5m with exit=b10.3xADR (diag) | -28.2 | -5.9 | 11.3 | 22.8 | -6.7 / 13.1 | 12.3 / 23.1 | NO |
| 6J OR60 5m fade exit=b20.3xADR (diag) | -39.4 | 4.8 | 15.5 | 22.9 | 11.3 / 17.2 | -0.4 / 20.8 | NO |
| 6B OR60 5m fade exit=b20.3xADR (diag) | -40.8 | -15.7 | 5.3 | 21.6 | -16.6 / 5.5 | 10.9 / 12.7 | NO |
| 6A OR60 5m fade exit=b20.2xADR (diag) | -46.4 | 5.1 | 14.0 | 2.6 | 4.3 / 12.5 | 17.8 / 17.2 | NO |
| 6C PD 15m fade exit=hd0.2xADR (diag) | -46.8 | -6.1 | 10.0 | 6.3 | -7.0 / 8.2 | 5.7 / 11.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) PD 5m with exit=b10.3xADR | negative pre-2023 | 1924 | -51.5 | -66.2 | -67.3 | 14.7 | -2.12 / -2.70 / -2.73 | 23.1 / 8.8 |
| 6E 2 (diag) OR60 5m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 2515 | 5.2 | -11.7 | -12.8 | 16.9 | 0.23 / -0.56 / -0.61 | 14.7 / -2.2 |
| 6E 3 (diag) OR60 5m fade exit=b20.2xADR | positive pre-2023 | 2515 | 41.8 | 26.5 | 25.5 | 15.3 | 2.01 / 1.26 / 1.21 | 13.8 / -1.8 |
| 6J 1 (diag) OR60 5m fade exit=tr0.3xADR | negative pre-2023 | 2490 | -10.4 | -27.3 | -32.8 | 16.9 | -0.73 / -1.91 / -2.30 | 15.4 / -1.5 |
| 6J 2 (diag) OR60 5m fade exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2490 | 11.3 | -4.9 | -10.2 | 16.2 | 0.58 / -0.25 / -0.53 | 12.0 / -4.5 |
| 6J 3 (diag) OR60 15m with exit=hd0.3xADR | negative pre-2023 | 2428 | -33.5 | -50.3 | -55.9 | 16.9 | -1.72 / -2.59 / -2.87 | 13.7 / -3.1 |
| 6B 1 (diag) OR60 5m fade exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2539 | 1.8 | -14.4 | -15.7 | 16.3 | 0.13 / -1.02 / -1.12 | 16.2 / -0.1 |
| 6B 2 (diag) OR60 5m fade exit=hd0.3xADR | negative pre-2023 | 2539 | -11.3 | -28.2 | -29.6 | 16.9 | -0.83 / -2.07 / -2.17 | 15.2 / -1.7 |
| 6B 3 (diag) OR60 5m fade exit=b10.3xADR | gross-positive, cost-negative pre-2023 | 2539 | 5.4 | -9.4 | -10.6 | 14.8 | 0.44 / -0.78 / -0.88 | 11.1 / -3.4 |
| 6A 1 (diag) OR60 5m fade exit=b20.2xADR | gross-positive, cost-negative pre-2023 | 2538 | 13.3 | -9.0 | -12.6 | 22.3 | 1.00 / -0.68 / -0.95 | 20.0 / -2.2 |
| 6A 2 (diag) OR60 5m fade exit=hd0.2xADR | negative pre-2023 | 2538 | -8.0 | -32.4 | -36.4 | 24.4 | -0.63 / -2.53 / -2.85 | 21.5 / -2.8 |
| 6A 3 (diag) OR60 5m fade exit=b20.3xADR | gross-positive, cost-negative pre-2023 | 2538 | 15.4 | -7.9 | -11.7 | 23.3 | 0.93 / -0.48 / -0.70 | 18.9 / -4.6 |
| 6C 1 (diag) PD 15m fade exit=hd0.3xADR | gross-positive, cost-negative pre-2023 | 1908 | 6.3 | -8.1 | -9.4 | 14.4 | 0.40 / -0.51 / -0.59 | 7.6 / -6.7 |
| 6C 2 (diag) OR30 15m with exit=b20.3xADR | negative pre-2023 | 2560 | -18.9 | -32.6 | -33.8 | 13.8 | -1.50 / -2.58 / -2.67 | 7.3 / -6.3 |
| 6C 3 (diag) PD 15m fade exit=hd0.2xADR | gross-positive, cost-negative pre-2023 | 1908 | 4.0 | -10.4 | -11.6 | 14.4 | 0.29 / -0.75 / -0.84 | 5.5 / -8.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00); 6B: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00); 6C: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00); 6E: 0 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 1.00); 6J: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q7c.py (= ap_b11.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q7c/ (`Q7C_CO_all_selected_scored.csv`).

DONE Q7C
