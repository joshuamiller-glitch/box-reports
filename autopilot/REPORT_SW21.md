# REPORT SW21 - the live pair engine (ST ATR120/2.0/EMA200 and HM 20/55 on 1-min; scaled to 5-min) as standalone sleeves on the other instruments (D00 M1-M3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 11 selected cells (+7 diagnostic) scored on 7 instruments; best non-diagnostic all-in additive uplift at 20% share +0.28; best pair-window standalone Sharpe +1.18.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: ST flip (1-min ATR 120, mult 2.0, EMA 200; 5-min ATR 24, 2.0, EMA 40) and HM cross (1-min 20/55; 5-min 4/11) of close minus the mid-anchored (04:00 UTC) VWAP, with or against, entry windows of the d1_f4 NT8 spec (18:00-09:00, 09:59-15:00 ET), exit after 60/120/240 min or at the flatten, with or without a stop of 0.15 x ADR20 (gap/stop fills as the B-engine).
- Instruments: ES, RTY, YM, GC, CL, ZN, BTC. Grid: 64 cells per instrument = 4 signal specs x 2 directions x 4 holds x 2 stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      64 |         64 |         9 |               1.178 |                2 |          9 |            1 |
| CL    |      64 |         64 |         2 |               0.682 |                2 |          0 |            0 |
| ES    |      64 |         64 |         2 |               0.784 |                2 |          0 |            0 |
| GC    |      64 |         64 |         6 |               1.275 |                2 |          0 |            0 |
| RTY   |      64 |         64 |         2 |               0.673 |                2 |          2 |            3 |
| YM    |      64 |         64 |         3 |               0.938 |                2 |          0 |            0 |
| ZN    |      64 |         64 |         0 |              -0.672 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    2 |             2.47 |               6 |       0.74 |                       0.684 |            0.635 |           1.124 |     0.37 |       0.784 |                1.441 |
| RTY   |     100 |                    2 |             2.01 |               6 |       0.59 |                       0.656 |            0.683 |           1.099 |     0.44 |       0.673 |                1.557 |
| YM    |     100 |                    3 |             2.77 |               6 |       0.58 |                       0.605 |            0.657 |           1.124 |     0.5  |       0.938 |                1.623 |
| GC    |     100 |                    6 |             5.23 |              12 |       0.46 |                       0.755 |            0.913 |           1.268 |     0.73 |       1.275 |                2.148 |
| CL    |     100 |                    2 |             1.37 |               4 |       0.41 |                       0.605 |            0.688 |           1.257 |     0.45 |       0.682 |                1.49  |
| ZN    |     100 |                    0 |             0.05 |               2 |       1    |                     nan     |            0.6   |           1.028 |   nan    |     nan     |                1.028 |
| BTC   |     100 |                    9 |             8.15 |              15 |       0.38 |                       0.703 |            0.738 |           0.982 |     0.63 |       1.178 |                1.94  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY 1 | 5m hm[4, 11, 0] dir=with hold=flat stop=0.0ADR | 517 | 2 | 0.67 | -0.43 | 0.27 | -0.22 / 1.40 | 0.14 / -0.77 / 0.15 | 0.01 | -0.10 | 0.84 | -0.16 | 0.00 | 829 | NO |
| RTY 2 | 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | 2192 | 2 | 0.64 | -0.42 | 0.47 | 0.22 / 0.50 | 0.10 / -0.07 / 0.16 | -0.02 | 0.44 | 0.98 | -0.09 | 0.00 | 3518 | NO |
| RTY 3 (diag) | 5m st[24, 2.0, 40] dir=against hold=flat stop=0.0ADR | 517 | 1 | 0.40 | -0.24 | 0.50 | 0.60 / 1.22 | 0.05 / -0.03 / 0.17 | 0.05 | -0.28 | 0.89 | -0.12 | 0.67 | 828 | diag |
| RTY 4 (diag) | 1m st[120, 2.0, 200] dir=against hold=flat stop=0.0ADR | 517 | 1 | 0.01 | 0.83 | 0.51 | 1.29 / 1.38 | 0.03 / 0.13 / 0.16 | 0.06 | -0.17 | 0.88 | -0.09 | 0.50 | 829 | diag |
| RTY 5 (diag) | 1m hm[20, 55, 0] dir=with hold=240m stop=0.0ADR | 2284 | 1 | -0.01 | -1.68 | -0.42 | -0.91 / 0.80 | -0.02 / 0.30 / -0.46 | -0.20 | -0.22 | 0.75 | -0.32 | 0.00 | 3654 | diag |
| ZN 1 (diag) | 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR | 517 | 1 | -0.67 | -0.91 | -0.97 | -1.48 / -0.39 | -0.20 / -0.39 / -0.09 | -0.48 | -0.36 | 0.82 | -0.39 | 0.00 | 831 | diag |
| ZN 2 (diag) | 5m hm[4, 11, 0] dir=against hold=flat stop=0.0ADR | 517 | 1 | -0.73 | -1.10 | -1.74 | -3.83 / -0.43 | -0.21 / -0.50 / -0.58 | -0.61 | -0.08 | 0.43 | -0.52 | 0.00 | 831 | diag |
| ZN 3 (diag) | 1m st[120, 2.0, 200] dir=with hold=flat stop=0.0ADR | 517 | 1 | -0.78 | -1.93 | -1.35 | -2.67 / -0.45 | -0.17 / -0.75 / -0.21 | -0.51 | 0.10 | 0.76 | -0.43 | 0.00 | 831 | diag |
| BTC 1 | 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | 1503 | 2 | 1.18 | 1.72 | 1.18 | 1.21 / 1.86 | 0.29 / 0.96 / -0.17 | 0.22 | 0.03 | 0.96 | 0.07 | 0.17 | 2328 | NO |
| BTC 2 | 1m st[120, 2.0, 200] dir=with hold=flat stop=0.0ADR | 517 | 2 | 1.06 | 0.83 | 1.08 | 1.20 / 1.42 | 0.18 / 0.41 / 0.04 | 0.16 | 0.43 | 0.98 | -0.02 | 0.50 | 821 | NO |
| BTC 3 | 5m st[24, 2.0, 40] dir=with hold=flat stop=0.15ADR | 1239 | 2 | 0.98 | 0.28 | 0.51 | -0.05 / 1.30 | 0.16 / 0.56 / -0.38 | 0.03 | 0.33 | 0.79 | -0.11 | 0.62 | 1991 | NO |
| BTC 4 | 5m st[24, 2.0, 40] dir=with hold=240m stop=0.0ADR | 1666 | 2 | 0.80 | -0.81 | 0.23 | -0.29 / 1.14 | 0.14 / 0.27 / -0.27 | -0.02 | 0.20 | 0.87 | -0.16 | 0.50 | 2606 | NO |
| BTC 5 | 1m st[120, 2.0, 200] dir=with hold=flat stop=0.15ADR | 1615 | 2 | 0.60 | -0.08 | 1.01 | 1.69 / 2.11 | 0.08 / 1.07 / -0.07 | 0.11 | 0.42 | 0.83 | -0.02 | 1.00 | 2482 | NO |
| BTC 6 | 5m st[24, 2.0, 40] dir=with hold=60m stop=0.15ADR | 3533 | 2 | 0.51 | -0.37 | -0.20 | -1.33 / 0.68 | 0.06 / -0.46 / -0.29 | -0.32 | 0.35 | 0.89 | -0.28 | 0.00 | 5535 | NO |
| BTC 7 | 1m st[120, 2.0, 200] dir=with hold=60m stop=0.15ADR | 7526 | 2 | 0.50 | -0.97 | -0.02 | -0.94 / 0.10 | 0.07 / 0.06 / -0.42 | -0.36 | 0.38 | 0.97 | -0.23 | 0.00 | 11789 | NO |
| BTC 8 | 5m st[24, 2.0, 40] dir=with hold=240m stop=0.15ADR | 2009 | 2 | 0.50 | -1.08 | 0.42 | 0.39 / 1.28 | 0.04 / 0.49 / -0.17 | -0.05 | 0.13 | 0.88 | -0.15 | 0.70 | 3164 | NO |
| BTC 9 | 1m hm[20, 55, 0] dir=with hold=240m stop=0.15ADR | 2582 | 2 | 0.21 | 0.14 | 0.27 | 0.31 / 1.55 | 0.03 / 0.54 / -0.18 | -0.07 | -0.09 | 0.77 | -0.16 | 0.62 | 4060 | NO |
| BTC 10 (diag) | 1m hm[20, 55, 0] dir=with hold=120m stop=0.15ADR | 3926 | 1 | 0.88 | -0.21 | -0.28 | -1.95 / 0.62 | 0.16 / -0.03 / -0.60 | -0.25 | -0.07 | 0.72 | -0.25 | 0.00 | 6189 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 7 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 12 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | clean | 1.15 | 1.72 | -141533 | -106388 | 485737 | -204464 | 2.14 | 41.9 | 1.75 | -75742 | 243204 | -81807 |
| BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | H1 | 2.66 | 6.34 | -107165 | -99302 | 270023 | -114344 | 3.58 | 39.3 | 3.79 | -68272 | 129756 | -77931 |
| BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | H2 | -0.40 | -0.56 | -110215 | -98206 | 234876 | -129130 | -0.51 | 58.3 | 2.31 | -83883 | 219932 | -92286 |
| BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | all | 1.18 | 1.95 | -134728 | -107232 | 485737 | -204464 | 3.88 | 44.6 | 2.18 | -77913 | 243204 | -92286 |
| RTY 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | clean | 0.62 | 0.97 | -118409 | -91899 | 464414 | -275549 | 1.21 | 49.5 | 1.56 | -84295 | 290725 | -98260 |
| RTY 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | H1 | -0.23 | -0.30 | -100035 | -92828 | 369011 | -111891 | -0.11 | 50.0 | 2.75 | -82521 | 157838 | -92615 |
| RTY 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | H2 | 0.45 | 0.64 | -158222 | -129152 | 473022 | -189267 | 0.34 | 38.9 | 2.64 | -93597 | 211087 | -95677 |
| RTY 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | all | 0.47 | 0.70 | -131533 | -104875 | 826011 | -275549 | 0.83 | 47.0 | 1.98 | -87716 | 290725 | -98260 |
| ZN 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR (diag) | clean | -0.75 | -0.94 | -161383 | -125720 | 1008725 | -205623 | -0.68 | 51.4 | 1.26 | -95656 | 361026 | -112337 |
| ZN 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR (diag) | H1 | -2.81 | -2.98 | -96019 | -90825 | 633040 | -96531 | -0.76 | 64.3 | 2.44 | -73181 | 169542 | -75401 |
| ZN 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR (diag) | H2 | -0.64 | -0.89 | -94927 | -83915 | 286411 | -102461 | -0.60 | 58.3 | 2.40 | -90663 | 212277 | -97639 |
| ZN 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR (diag) | all | -0.97 | -1.20 | -149728 | -117325 | 1550078 | -205623 | -0.86 | 54.8 | 1.68 | -93199 | 361026 | -112337 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| RTY 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | -22.5 | -1.2 | 13.4 | 24.3 | -2.0 / 18.8 | 1.2 / 20.5 | NO |
| ZN 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR (diag) | -44.6 | -29.5 | -1.0 | -26.4 | -30.6 / -7.9 | 34.1 / 38.6 | NO |
| BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | -9.4 | 12.3 | 23.8 | 34.2 | 12.4 / 27.1 | 29.3 / 36.5 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| RTY 1 5m hm[4, 11, 0] dir=with hold=flat stop=0.0ADR | negative pre-2023 | 1546 | -17.1 | -31.5 | -29.2 | 14.4 | -0.23 / -0.43 / -0.40 | 65.5 / 51.2 |
| RTY 2 5m hm[4, 11, 0] dir=against hold=240m stop=0.0ADR | gross-positive, cost-negative pre-2023 | 6484 | 7.8 | -6.6 | -4.4 | 14.4 | 0.50 / -0.42 / -0.28 | 28.0 / 13.6 |
| RTY 3 (diag) 5m st[24, 2.0, 40] dir=against hold=flat stop=0.0ADR | negative pre-2023 | 1544 | -3.3 | -17.7 | -15.4 | 14.4 | -0.05 / -0.24 / -0.21 | 51.9 / 37.6 |
| RTY 4 (diag) 1m st[120, 2.0, 200] dir=against hold=flat stop=0.0ADR | positive pre-2023 | 1546 | 79.0 | 64.7 | 66.9 | 14.4 | 1.01 / 0.83 / 0.86 | 17.2 / 2.9 |
| RTY 5 (diag) 1m hm[20, 55, 0] dir=with hold=240m stop=0.0ADR | negative pre-2023 | 6640 | -12.3 | -26.7 | -24.5 | 14.4 | -0.78 / -1.68 / -1.54 | 13.4 / -0.9 |
| ZN 1 (diag) 1m hm[20, 55, 0] dir=against hold=flat stop=0.0ADR | gross-positive, cost-negative pre-2023 | 2700 | 11.9 | -23.8 | -28.9 | 35.6 | 0.45 / -0.91 / -1.10 | 17.7 / -17.9 |
| ZN 2 (diag) 5m hm[4, 11, 0] dir=against hold=flat stop=0.0ADR | gross-positive, cost-negative pre-2023 | 2701 | 6.3 | -29.3 | -34.5 | 35.6 | 0.24 / -1.10 / -1.30 | 16.2 / -19.4 |
| ZN 3 (diag) 1m st[120, 2.0, 200] dir=with hold=flat stop=0.0ADR | negative pre-2023 | 2701 | -13.9 | -49.5 | -54.6 | 35.6 | -0.54 / -1.93 / -2.13 | 16.2 / -19.4 |
| BTC 1 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR | positive pre-2023 | 1029 | 206.5 | 152.2 | 184.4 | 54.4 | 2.35 / 1.72 / 2.09 | 239.6 / 185.2 |
| BTC 2 1m st[120, 2.0, 200] dir=with hold=flat stop=0.0ADR | positive pre-2023 | 388 | 299.9 | 245.5 | 278.0 | 54.4 | 1.01 / 0.83 / 0.94 | 709.6 / 655.3 |
| BTC 3 5m st[24, 2.0, 40] dir=with hold=flat stop=0.15ADR | positive pre-2023 | 904 | 84.0 | 29.6 | 62.2 | 54.4 | 0.81 / 0.28 / 0.60 | 220.0 / 165.7 |
| BTC 4 5m st[24, 2.0, 40] dir=with hold=240m stop=0.0ADR | gross-positive, cost-negative pre-2023 | 1178 | 2.2 | -52.1 | -19.6 | 54.4 | 0.02 / -0.81 / -0.32 | 145.2 / 90.8 |
| BTC 5 1m st[120, 2.0, 200] dir=with hold=flat stop=0.15ADR | gross-positive, cost-negative pre-2023 | 1180 | 46.7 | -7.7 | 24.7 | 54.4 | 0.54 / -0.08 / 0.29 | 142.8 / 88.5 |
| BTC 6 5m st[24, 2.0, 40] dir=with hold=60m stop=0.15ADR | gross-positive, cost-negative pre-2023 | 2475 | 47.0 | -7.4 | 25.3 | 54.4 | 2.45 / -0.37 / 1.34 | 76.4 / 22.0 |
| BTC 7 1m st[120, 2.0, 200] dir=with hold=60m stop=0.15ADR | gross-positive, cost-negative pre-2023 | 5299 | 39.7 | -14.7 | 17.9 | 54.4 | 2.64 / -0.97 / 1.23 | 70.0 / 15.6 |
| BTC 8 5m st[24, 2.0, 40] dir=with hold=240m stop=0.15ADR | gross-positive, cost-negative pre-2023 | 1392 | 0.5 | -53.9 | -21.2 | 54.4 | -0.01 / -1.08 / -0.44 | 98.0 / 43.7 |
| BTC 9 1m hm[20, 55, 0] dir=with hold=240m stop=0.15ADR | positive pre-2023 | 1812 | 59.5 | 5.1 | 37.6 | 54.4 | 1.41 / 0.14 / 0.89 | 74.2 / 19.8 |
| BTC 10 (diag) 1m hm[20, 55, 0] dir=with hold=120m stop=0.15ADR | gross-positive, cost-negative pre-2023 | 2752 | 49.5 | -4.9 | 27.6 | 54.4 | 2.23 / -0.21 / 1.25 | 96.4 / 42.0 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 9 cells pass the clean rule against a replicate mean of 8.2 (p(count) = 0.38, p(top) = 0.63); CL: 2 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.41, p(top) = 0.45); ES: 2 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.74, p(top) = 0.37); GC: 6 cells pass the clean rule against a replicate mean of 5.2 (p(count) = 0.46, p(top) = 0.73); RTY: 2 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.59, p(top) = 0.44); YM: 3 cells pass the clean rule against a replicate mean of 2.8 (p(count) = 0.58, p(top) = 0.50); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 11 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.28 (BTC 1m hm[20, 55, 0] dir=with hold=flat stop=0.15ADR); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 6, 'positive pre-2023': 4, 'negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_21.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw21/ (`SW21_CO_all_selected_scored.csv`).

DONE SW21
