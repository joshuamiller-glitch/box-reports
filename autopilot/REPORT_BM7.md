# REPORT BM7 - high/low time order (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 2 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.06; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. high/low time order. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          4 |         0 |               0.362 |                2 |          0 |            3 |
| CL    |       8 |          4 |         0 |               1.27  |                2 |          0 |            3 |
| ES    |       8 |          8 |         0 |               0.715 |                1 |          0 |            3 |
| GC    |       8 |          4 |         1 |               0.91  |                2 |          1 |            3 |
| NQ    |       8 |          8 |         0 |               1.068 |                1 |          0 |            3 |
| RTY   |       8 |          8 |         0 |               0.77  |                1 |          0 |            3 |
| YM    |       8 |          8 |         1 |               0.699 |                2 |          1 |            3 |
| ZN    |       8 |          8 |         0 |               0.041 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.07  |               5 |      1     |                     nan     |            0.711 |           1.353 |  nan     |     nan     |                1.67  |
| NQ    |     200 |                    0 |            1.76  |               6 |      1     |                     nan     |            0.782 |           1.386 |  nan     |     nan     |                1.727 |
| RTY   |     200 |                    0 |            1.26  |               5 |      1     |                     nan     |            0.739 |           1.443 |  nan     |     nan     |                1.639 |
| YM    |     200 |                    1 |            1.315 |               6 |      0.745 |                       0.337 |            0.747 |           1.287 |    0.66  |       0.337 |                1.55  |
| GC    |     200 |                    1 |            0.66  |               3 |      0.515 |                       0.91  |            0.668 |           1.279 |    0.125 |       0.91  |                1.505 |
| CL    |     200 |                    0 |            0.375 |               3 |      1     |                     nan     |            0.649 |           1.297 |  nan     |     nan     |                1.297 |
| ZN    |     200 |                    0 |            0.07  |               2 |      1     |                     nan     |            0.608 |           1.151 |  nan     |     nan     |                1.151 |
| BTC   |     200 |                    0 |            0.78  |               3 |      1     |                     nan     |            0.758 |           1.674 |  nan     |     nan     |                1.7   |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 129 | 1 | 0.72 | 0.30 | 0.45 | -0.34 / 1.12 | 0.09 / 0.03 / -0.07 | 0.03 | -0.31 | 0.86 | -0.05 | 0.50 | 191 | diag |
| ES 2 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | 129 | 1 | 0.59 | 0.22 | 0.17 | -0.44 / 1.17 | 0.04 / 0.12 / -0.36 | -0.06 | 0.70 | 0.77 | -0.19 | 0.00 | 191 | diag |
| ES 3 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 515 | 1 | 0.42 | -0.29 | 0.04 | -0.69 / 1.51 | 0.00 / 0.01 / -0.12 | -0.06 | -0.27 | 0.60 | -0.17 | 0.00 | 827 | diag |
| NQ 1 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 120 | 1 | 1.07 | 0.69 | 0.83 | 0.36 / 1.58 | 0.16 / -0.04 / 0.06 | 0.10 | -0.47 | 0.97 | 0.01 | 0.00 | 186 | diag |
| NQ 2 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 515 | 1 | 0.48 | 0.60 | 0.45 | 0.50 / 1.50 | 0.02 / -0.06 / 0.31 | 0.04 | -0.64 | 0.83 | -0.09 | 0.00 | 827 | diag |
| NQ 3 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | 120 | 1 | 0.19 | 0.73 | 0.00 | -0.13 / 1.48 | -0.04 / -0.03 / -0.17 | -0.07 | 0.15 | 0.52 | -0.25 | 0.00 | 186 | diag |
| RTY 1 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=120m | 117 | 1 | 0.77 | -0.40 | 0.40 | 0.00 / 1.25 | 0.19 / 0.03 / -0.01 | 0.10 | -0.17 | 0.88 | -0.09 | 0.50 | 191 | diag |
| RTY 2 (diag) | prior-day high/low order, range>=0.0ADR dir=against hold=120m | 515 | 1 | 0.49 | -0.79 | 0.02 | -0.59 / 0.94 | 0.16 / 0.12 / -0.26 | 0.02 | -0.16 | 0.80 | -0.16 | 1.00 | 827 | diag |
| RTY 3 (diag) | prior-day high/low order, range>=0.0ADR dir=against hold=flat | 515 | 1 | 0.17 | -0.67 | -0.16 | -0.82 / 1.14 | 0.05 / 0.10 / -0.39 | -0.06 | 0.10 | 0.56 | -0.22 | 0.00 | 827 | diag |
| YM 1 | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | 515 | 2 | 0.34 | -0.38 | 0.10 | -0.04 / 1.33 | -0.07 / -0.36 / -0.23 | -0.17 | 0.26 | 0.81 | -0.33 | 0.00 | 827 | NO |
| YM 2 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 141 | 1 | 0.70 | 0.59 | 0.60 | 0.55 / 1.44 | 0.07 / 0.07 / 0.03 | 0.05 | 0.22 | 0.91 | -0.04 | 0.00 | 217 | diag |
| YM 3 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 515 | 1 | 0.23 | -0.02 | 0.05 | -0.20 / 1.21 | -0.05 / -0.15 / -0.07 | -0.09 | -0.41 | 0.71 | -0.20 | 0.00 | 827 | diag |
| YM 4 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | 141 | 1 | 0.18 | 0.57 | 0.13 | 0.13 / 1.29 | -0.06 / -0.02 / -0.06 | -0.07 | 0.70 | 0.74 | -0.22 | 0.00 | 217 | diag |
| GC 1 | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 517 | 2 | 0.91 | -0.54 | 0.65 | 0.55 / 1.39 | 0.13 / -0.57 / 0.20 | 0.03 | 0.03 | 0.89 | -0.24 | 0.00 | 828 | NO |
| GC 2 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | 517 | 1 | 0.81 | -0.80 | 0.88 | 1.05 / 1.31 | 0.15 / 0.23 / 0.13 | 0.12 | 0.42 | 0.98 | -0.11 | 0.00 | 828 | diag |
| GC 3 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=120m | 95 | 1 | 0.09 | 0.05 | -0.52 | -1.02 / 1.24 | -0.05 / -1.46 / -0.43 | -0.37 | -0.03 | 0.28 | -0.72 | 0.00 | 145 | diag |
| GC 4 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=flat | 95 | 1 | 0.01 | 0.20 | -0.24 | -0.49 / 1.49 | -0.05 / -0.78 / -0.41 | -0.23 | -0.12 | 0.42 | -0.54 | 0.00 | 145 | diag |
| CL 1 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 90 | 2 | 1.27 | 0.02 | 0.89 | 0.67 / 1.52 | 0.20 / -0.32 / 0.25 | 0.12 | 0.02 | 0.96 | -0.05 | 0.50 | 124 | diag |
| CL 2 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | 90 | 2 | 1.01 | -0.22 | 0.38 | -0.14 / 1.21 | 0.19 / -0.14 / -0.33 | 0.00 | -0.14 | 0.89 | -0.25 | 0.50 | 124 | diag |
| CL 3 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 517 | 1 | 0.88 | 0.34 | 0.17 | -0.37 / 1.35 | 0.08 / -0.19 / -0.31 | -0.11 | -0.46 | 0.72 | -0.29 | 0.00 | 830 | diag |
| ZN 1 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=120m | 134 | 1 | 0.04 | -1.76 | -0.47 | -1.85 / -1.05 | -0.06 / -0.10 / -0.30 | -0.29 | 0.03 | 1.00 | -0.28 | 0.00 | 199 | diag |
| ZN 2 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=flat | 134 | 1 | -0.62 | -1.35 | -0.88 | -1.82 / 0.45 | -0.19 / -0.07 / -0.30 | -0.31 | 0.40 | 0.48 | -0.34 | 0.00 | 199 | diag |
| ZN 3 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 134 | 1 | -0.70 | 0.07 | -0.58 | -0.42 / 0.08 | -0.13 / -0.16 / 0.07 | -0.19 | -0.34 | 0.73 | -0.24 | 0.00 | 199 | diag |
| BTC 1 (diag) | prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | 79 | 2 | 0.36 | 0.21 | -0.10 | -1.03 / 1.20 | 0.02 / -0.27 / -0.12 | -0.07 | -0.56 | 0.51 | -0.22 | 0.00 | 120 | diag |
| BTC 2 (diag) | prior-day high/low order, range>=1.0ADR dir=against hold=120m | 78 | 1 | 0.33 | -0.35 | 0.42 | 0.68 / 1.31 | 0.09 / -0.08 / 0.12 | 0.07 | 0.30 | 0.84 | -0.09 | 0.75 | 116 | diag |
| BTC 3 (diag) | prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | 511 | 1 | 0.04 | -0.26 | -0.33 | -0.95 / 1.33 | -0.04 / -0.14 / -0.11 | -0.09 | -0.26 | 0.36 | -0.24 | 0.00 | 801 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 2 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 21 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | clean | 0.33 | 0.55 | -132234 | -92871 | 343037 | -227932 | 0.86 | 25.7 | 1.55 | -85837 | 268773 | -97627 |
| BTC prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | H1 | -0.37 | -0.60 | -90803 | -78369 | 327722 | -92972 | -0.22 | 25.0 | 2.74 | -76962 | 142028 | -82847 |
| BTC prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | H2 | 1.84 | 4.52 | -52678 | -40000 | 67802 | -56789 | 4.77 | 16.7 | 2.61 | -82190 | 216174 | -84727 |
| BTC prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | all | 0.42 | 0.72 | -114645 | -83598 | 343037 | -227932 | 1.60 | 23.8 | 1.98 | -84695 | 268773 | -97627 |
| CL prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | clean | 1.21 | 2.29 | -113878 | -90820 | 338226 | -159832 | 3.25 | 23.8 | 1.66 | -84996 | 232514 | -101687 |
| CL prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H1 | -3.06 | -2.87 | -100114 | -89520 | 436411 | -124080 | -0.86 | 25.0 | 2.50 | -84247 | 151713 | -91562 |
| CL prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H2 | 1.42 | 6.93 | -114633 | -85312 | 352042 | -116261 | 3.06 | 19.4 | 2.74 | -85406 | 228298 | -88288 |
| CL prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | all | 0.89 | 2.35 | -115396 | -92146 | 495903 | -159832 | 3.62 | 23.2 | 2.04 | -86050 | 232514 | -101687 |
| ES prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | clean | 0.67 | 2.92 | -49018 | -38105 | 126663 | -80009 | 4.78 | 29.5 | 1.55 | -78266 | 263601 | -79868 |
| ES prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H1 | 0.73 | 1.14 | -40735 | -35189 | 98067 | -48066 | 0.56 | 25.0 | 2.86 | -74297 | 156344 | -79180 |
| ES prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H2 | -1.03 | -1.35 | -60758 | -46395 | 235293 | -78337 | -0.51 | 30.6 | 2.41 | -81376 | 214845 | -83099 |
| ES prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | all | 0.45 | 1.52 | -54293 | -42322 | 275513 | -80009 | 1.96 | 28.6 | 1.94 | -79059 | 263601 | -83099 |
| GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | clean | 0.96 | 1.43 | -138891 | -111514 | 458989 | -205949 | 1.90 | 47.6 | 1.59 | -85615 | 269455 | -96427 |
| GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | H1 | -0.46 | -0.72 | -206027 | -189140 | 816144 | -233188 | -0.30 | 57.1 | 2.26 | -66634 | 195243 | -73022 |
| GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | H2 | 1.19 | 1.91 | -358951 | -270426 | 896465 | -397551 | 1.11 | 44.4 | 2.68 | -96272 | 232305 | -117053 |
| GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | all | 0.65 | 1.02 | -226287 | -181540 | 1122905 | -397551 | 1.45 | 48.8 | 1.96 | -86950 | 269455 | -117053 |
| NQ prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | clean | 1.03 | 5.20 | -40888 | -34469 | 184363 | -56859 | 5.06 | 24.8 | 1.62 | -77847 | 242744 | -79868 |
| NQ prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H1 | -0.20 | -0.29 | -77635 | -70092 | 302641 | -96070 | -0.10 | 42.9 | 2.78 | -71701 | 177862 | -76902 |
| NQ prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H2 | 0.96 | 2.85 | -33737 | -25705 | 148559 | -35780 | 0.91 | 27.8 | 2.55 | -81887 | 217425 | -82524 |
| NQ prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | all | 0.83 | 2.84 | -55907 | -43337 | 429455 | -96070 | 2.42 | 28.0 | 2.00 | -78987 | 242744 | -82524 |
| RTY prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | clean | 0.77 | 1.20 | -143236 | -104329 | 954825 | -200900 | 0.73 | 25.7 | 1.65 | -80226 | 277090 | -83471 |
| RTY prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | H1 | -0.05 | -0.07 | -215938 | -206654 | 652245 | -219832 | -0.03 | 32.1 | 2.85 | -77942 | 141112 | -85535 |
| RTY prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | H2 | 0.05 | 0.07 | -175809 | -152465 | 378946 | -193163 | 0.06 | 33.3 | 2.47 | -78592 | 202191 | -79653 |
| RTY prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | all | 0.40 | 0.57 | -186682 | -151279 | 1228218 | -219832 | 0.57 | 28.6 | 2.02 | -80453 | 277090 | -85535 |
| YM prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | clean | 0.23 | 0.37 | -112865 | -97249 | 447022 | -145483 | 0.47 | 44.8 | 1.39 | -92048 | 317345 | -105778 |
| YM prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | H1 | 0.07 | 0.10 | -108018 | -104957 | 547417 | -111468 | 0.04 | 50.0 | 2.47 | -85690 | 161349 | -97459 |
| YM prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | H2 | -0.12 | -0.17 | -180647 | -149555 | 481438 | -183441 | -0.11 | 52.8 | 2.26 | -94266 | 246872 | -95775 |
| YM prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | all | 0.10 | 0.16 | -136612 | -117696 | 692647 | -183441 | 0.25 | 47.0 | 1.76 | -93142 | 317345 | -105778 |
| ZN prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | clean | -0.67 | -0.78 | -167429 | -117991 | 1058142 | -427574 | -0.57 | 40.0 | 1.33 | -82074 | 271109 | -97267 |
| ZN prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H1 | -2.80 | -2.91 | -49107 | -47392 | 251358 | -52302 | -0.93 | 42.9 | 2.66 | -79418 | 153770 | -80549 |
| ZN prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | H2 | 0.84 | 1.53 | -61503 | -43204 | 199691 | -80991 | 0.66 | 30.6 | 2.55 | -82028 | 222211 | -82202 |
| ZN prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | all | -0.58 | -0.70 | -134598 | -94615 | 1263724 | -427574 | -0.56 | 38.7 | 1.81 | -82169 | 271109 | -97267 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | -24.1 | 26.3 | 29.2 | 35.2 | 25.7 / 29.3 | 28.3 / 36.4 | NO |
| NQ prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | -18.7 | 27.1 | 29.7 | 37.3 | 31.7 / 30.8 | 32.7 / 41.4 | NO |
| RTY prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | -22.3 | -2.3 | 22.1 | 13.9 | 22.5 / 26.2 | -7.8 / 3.3 | NO |
| YM prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | -28.1 | -15.7 | 1.3 | 10.1 | -13.8 / 4.4 | -6.7 / 14.0 | NO |
| GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | -12.3 | -35.7 | -0.5 | 6.2 | -1.4 / 15.5 | -12.9 / 1.5 | NO |
| CL prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | -10.4 | -7.4 | 14.7 | 36.6 | -8.3 / 15.3 | 4.6 / 17.2 | NO |
| ZN prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat (diag) | -37.8 | -2.0 | 21.2 | 16.4 | -2.8 / 18.9 | 24.3 / 26.5 | NO |
| BTC prior-day high/low order, range>=1.0ADR dir=against hold=120m (diag) | -24.0 | -22.5 | 16.0 | 23.0 | -23.5 / 12.1 | 21.3 / 31.3 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 666 | 87.5 | 58.1 | 72.4 | 29.4 | 0.45 / 0.30 / 0.37 | 485.9 / 456.5 |
| ES 2 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | positive pre-2023 | 666 | 55.0 | 25.7 | 39.9 | 29.4 | 0.46 / 0.22 / 0.34 | 133.4 / 104.1 |
| ES 3 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | gross-positive, cost-negative pre-2023 | 2682 | 6.8 | -22.6 | -8.4 | 29.4 | 0.09 / -0.29 / -0.11 | 99.9 / 70.5 |
| NQ 1 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 709 | 204.4 | 190.0 | 198.6 | 14.4 | 0.74 / 0.69 / 0.72 | 1182.2 / 1167.8 |
| NQ 2 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | positive pre-2023 | 2683 | 92.1 | 77.7 | 86.3 | 14.4 | 0.71 / 0.60 / 0.67 | 157.1 / 142.8 |
| NQ 3 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | positive pre-2023 | 709 | 154.4 | 140.0 | 148.6 | 14.4 | 0.80 / 0.73 / 0.77 | 49.4 / 35.1 |
| RTY 1 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=120m | negative pre-2023 | 402 | -25.6 | -39.9 | -37.6 | 14.4 | -0.26 / -0.40 / -0.38 | 90.1 / 75.7 |
| RTY 2 (diag) prior-day high/low order, range>=0.0ADR dir=against hold=120m | negative pre-2023 | 1533 | -18.9 | -33.2 | -31.0 | 14.4 | -0.45 / -0.79 / -0.74 | 36.8 / 22.4 |
| RTY 3 (diag) prior-day high/low order, range>=0.0ADR dir=against hold=flat | negative pre-2023 | 1533 | -26.0 | -40.3 | -38.1 | 14.4 | -0.43 / -0.67 / -0.63 | 32.0 / 17.7 |
| YM 1 prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | negative pre-2023 | 2686 | -0.2 | -14.6 | -8.8 | 14.4 | -0.01 / -0.38 / -0.23 | 26.8 / 12.4 |
| YM 2 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 639 | 102.9 | 88.5 | 94.3 | 14.4 | 0.68 / 0.59 / 0.62 | 293.4 / 279.0 |
| YM 3 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | gross-positive, cost-negative pre-2023 | 2687 | 13.4 | -1.0 | 4.7 | 14.4 | 0.21 / -0.02 / 0.07 | 34.1 / 19.8 |
| YM 4 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | positive pre-2023 | 639 | 66.2 | 51.8 | 57.5 | 14.4 | 0.73 / 0.57 / 0.63 | 33.8 / 19.4 |
| GC 1 prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | negative pre-2023 | 2681 | -13.6 | -37.9 | -28.1 | 24.4 | -0.19 / -0.54 / -0.40 | 132.5 / 108.1 |
| GC 2 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=120m | negative pre-2023 | 2680 | -15.4 | -39.8 | -30.0 | 24.4 | -0.30 / -0.80 / -0.60 | 79.1 / 54.7 |
| GC 3 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=120m | positive pre-2023 | 522 | 30.0 | 5.6 | 15.3 | 24.4 | 0.26 / 0.05 / 0.13 | 49.8 / 25.4 |
| GC 4 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=flat | positive pre-2023 | 522 | 56.4 | 32.0 | 41.7 | 24.4 | 0.34 / 0.20 / 0.25 | 44.6 / 20.3 |
| CL 1 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 541 | 28.7 | 4.4 | 6.6 | 24.4 | 0.15 / 0.02 / 0.04 | 211.6 / 187.2 |
| CL 2 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=120m | negative pre-2023 | 541 | -1.0 | -25.4 | -23.1 | 24.4 | -0.01 / -0.22 / -0.20 | 135.0 / 110.6 |
| CL 3 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | positive pre-2023 | 2688 | 47.8 | 23.4 | 26.0 | 24.4 | 0.69 / 0.34 / 0.38 | 71.8 / 47.4 |
| ZN 1 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=120m | negative pre-2023 | 590 | -23.0 | -58.6 | -63.8 | 35.6 | -0.72 / -1.76 / -1.91 | 35.7 / 0.1 |
| ZN 2 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=flat | negative pre-2023 | 590 | -39.5 | -75.1 | -80.3 | 35.6 | -0.71 / -1.35 / -1.44 | 0.7 / -34.9 |
| ZN 3 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 590 | 39.5 | 3.9 | -1.3 | 35.6 | 0.71 / 0.07 / -0.02 | -0.7 / -36.3 |
| BTC 1 (diag) prior-day high/low order, range>=1.0ADR dir=with late extreme hold=flat | positive pre-2023 | 53 | 172.2 | 117.8 | 151.1 | 54.4 | 0.31 / 0.21 / 0.27 | 638.0 / 583.6 |
| BTC 2 (diag) prior-day high/low order, range>=1.0ADR dir=against hold=120m | negative pre-2023 | 52 | -45.2 | -99.6 | -66.1 | 54.4 | -0.16 / -0.35 / -0.23 | 401.0 / 346.6 |
| BTC 3 (diag) prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat | negative pre-2023 | 383 | -1.1 | -55.5 | -23.0 | 54.4 | -0.02 / -0.26 / -0.12 | 21.0 / -33.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 1.00); GC: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.52, p(top) = 0.12); NQ: 0 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 1.00); RTY: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); YM: 1 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.74, p(top) = 0.66); ZN: 0 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 1.00).
- Of 2 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.06 (GC prior-day high/low order, range>=0.0ADR dir=with late extreme hold=flat); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_7.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm7/ (`BM7_CO_all_selected_scored.csv`).

DONE BM7
