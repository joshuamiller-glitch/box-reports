# REPORT SW15 - 1-minute price patterns with 1-10 minute holds (D11 H1)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 0 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +nan; best pair-window standalone Sharpe -0.31.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: run-k (k=3,4,5 consecutive same-colour closes, fire at the k-th), pin-p (wick >= 0.6/0.7/0.8 of range, range >= 1.5x 20-bar mean; enter against the wick), out-q (outside bar with range >= 1.0/1.5/2.0 x mean; enter with/against the bar colour); exact hold 1/3/5/10 min. Cost-dominated by construction; included because the D11 H1 cells are untested.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 72 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      72 |         72 |         0 |              -0.151 |                0 |          0 |            3 |
| CL    |      72 |         72 |         0 |              -6.543 |                0 |          0 |            3 |
| ES    |      72 |         72 |         0 |              -4.974 |                0 |          0 |            3 |
| GC    |      72 |         72 |         0 |              -4.227 |                0 |          0 |            3 |
| NQ    |      72 |         72 |         0 |              -0.116 |                1 |          0 |            3 |
| RTY   |      72 |         72 |         0 |              -4.237 |                0 |          0 |            3 |
| YM    |      72 |         72 |         0 |              -2.905 |                0 |          0 |            3 |
| ZN    |      72 |         72 |         0 |              -6.273 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| NQ    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| RTY   |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| YM    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| GC    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| CL    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| ZN    |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |
| BTC   |     100 |                    0 |                0 |               0 |          1 |                         nan |              nan |             nan |      nan |         nan |                  nan |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | 1m run5 dir=against hold=10m | 8240 | 0 | -4.97 | -6.13 | -5.39 | -6.04 / -5.53 | -1.02 / -1.04 / -1.85 | -2.26 | 0.42 | 0.98 | -1.43 | 0.00 | 14474 | diag |
| ES 2 (diag) | 1m out2.0 dir=against hold=10m | 4688 | 0 | -5.85 | -6.52 | -4.70 | -3.61 / -4.20 | -1.18 / -1.36 / -1.29 | -2.26 | 0.20 | 0.97 | -1.48 | 0.00 | 7684 | diag |
| ES 3 (diag) | 1m pin0.8 dir=against hold=10m | 2241 | 0 | -5.97 | -8.28 | -4.54 | -3.06 / -4.67 | -1.17 / -1.39 / -0.66 | -1.88 | -0.15 | 1.00 | -1.31 | 0.00 | 3298 | diag |
| NQ 1 (diag) | 1m pin0.8 dir=with hold=5m | 1523 | 1 | -0.12 | -4.25 | -0.58 | -1.37 / -0.35 | -0.09 / -0.23 / -0.40 | -0.33 | -0.10 | 1.00 | -0.35 | 0.00 | 2351 | diag |
| NQ 2 (diag) | 1m out2.0 dir=against hold=10m | 5294 | 1 | -0.68 | -2.90 | -0.82 | -0.98 / -0.23 | -0.19 / -0.59 / -0.35 | -0.49 | 0.28 | 0.98 | -0.48 | 0.00 | 8765 | diag |
| NQ 3 (diag) | 1m pin0.8 dir=with hold=3m | 1539 | 0 | -0.81 | -5.16 | -0.76 | -0.70 / -0.72 | -0.22 / -0.36 / -0.17 | -0.44 | 0.39 | 1.00 | -0.42 | 0.00 | 2375 | diag |
| RTY 1 (diag) | 1m pin0.8 dir=against hold=10m | 3042 | 0 | -4.24 | -6.36 | -3.90 | -3.27 / -2.33 | -0.86 / -0.79 / -0.63 | -1.36 | 0.37 | 0.81 | -1.00 | 0.00 | 4674 | diag |
| RTY 2 (diag) | 1m run5 dir=against hold=10m | 9878 | 0 | -4.44 | -5.31 | -4.64 | -4.85 / -4.90 | -0.89 / -1.05 / -1.05 | -1.77 | 0.42 | 0.99 | -1.17 | 0.00 | 16426 | diag |
| RTY 3 (diag) | 1m pin0.8 dir=with hold=10m | 3042 | 0 | -5.19 | -5.93 | -5.21 | -5.20 / -2.53 | -1.05 / -1.26 / -0.94 | -1.68 | -0.39 | 0.11 | -1.27 | 0.00 | 4674 | diag |
| YM 1 (diag) | 1m pin0.8 dir=with hold=10m | 2904 | 0 | -2.91 | -7.56 | -3.61 | -4.62 / -2.11 | -0.64 / -1.05 / -1.09 | -1.34 | 0.11 | 0.79 | -1.01 | 0.00 | 4699 | diag |
| YM 2 (diag) | 1m out2.0 dir=against hold=10m | 7615 | 0 | -4.84 | -6.69 | -4.94 | -5.01 / -3.52 | -0.99 / -1.49 / -1.20 | -1.85 | -0.26 | 0.80 | -1.35 | 0.00 | 12784 | diag |
| YM 3 (diag) | 1m pin0.8 dir=against hold=10m | 2904 | 0 | -5.21 | -6.65 | -4.27 | -3.00 / -1.96 | -1.02 / -1.02 / -0.49 | -1.45 | -0.06 | 0.51 | -1.12 | 0.00 | 4699 | diag |
| GC 1 (diag) | 1m pin0.8 dir=against hold=10m | 2255 | 0 | -4.23 | -7.56 | -1.51 | -0.14 / -0.01 | -0.88 / -0.18 / -0.53 | -1.28 | -0.25 | 0.90 | -1.01 | 0.00 | 3339 | diag |
| GC 2 (diag) | 1m pin0.7 dir=with hold=10m | 4794 | 0 | -4.51 | -9.11 | -2.62 | -1.77 / -0.38 | -0.92 / -1.08 / -1.01 | -1.66 | 0.20 | 0.79 | -1.30 | 0.00 | 7335 | diag |
| GC 3 (diag) | 1m pin0.8 dir=with hold=5m | 2317 | 0 | -4.95 | -8.96 | -2.62 | -1.70 / -0.42 | -0.99 / -1.60 / -0.67 | -1.63 | 0.19 | 0.80 | -1.35 | 0.00 | 3421 | diag |
| CL 1 (diag) | 1m run5 dir=against hold=10m | 7191 | 0 | -6.54 | -6.65 | -5.88 | -5.99 / -3.73 | -1.31 / -1.39 / -2.82 | -2.99 | 0.45 | 0.98 | -1.95 | 0.00 | 12779 | diag |
| CL 2 (diag) | 1m run5 dir=with hold=10m | 7191 | 0 | -8.77 | -7.74 | -7.20 | -5.72 / -4.16 | -1.75 / -1.72 / -1.84 | -2.84 | -0.44 | 0.86 | -2.09 | 0.00 | 12779 | diag |
| CL 3 (diag) | 1m pin0.8 dir=with hold=10m | 3516 | 0 | -10.40 | -7.19 | -7.14 | -4.72 / -2.43 | -2.07 / -2.09 / -1.59 | -2.96 | -0.22 | 0.28 | -2.28 | 0.00 | 5305 | diag |
| ZN 1 (diag) | 1m run5 dir=with hold=10m | 1272 | 0 | -6.27 | -7.74 | -7.02 | -12.97 / -15.73 | -1.26 / -1.08 / -0.93 | -1.54 | 0.14 | 1.00 | -1.38 | 0.00 | 1952 | diag |
| ZN 2 (diag) | 1m run5 dir=with hold=5m | 1311 | 0 | -7.40 | -8.27 | -8.45 | -15.44 / -16.91 | -1.48 / -1.36 / -1.18 | -1.74 | 0.05 | 1.00 | -1.63 | 0.00 | 2014 | diag |
| ZN 3 (diag) | 1m run5 dir=with hold=3m | 1317 | 0 | -8.22 | -7.95 | -9.22 | -15.56 / -18.23 | -1.64 / -1.48 / -1.28 | -1.83 | -0.16 | 1.00 | -1.79 | 0.00 | 2021 | diag |
| BTC 1 (diag) | 1m run5 dir=against hold=5m | 4479 | 0 | -0.15 | -4.24 | -0.31 | -0.57 / -2.09 | -0.06 / -0.11 / 0.00 | -0.49 | -0.26 | 1.00 | -0.24 | 0.00 | 7133 | diag |
| BTC 2 (diag) | 1m run5 dir=against hold=10m | 4148 | 0 | -0.73 | -3.26 | -0.34 | 0.47 / -0.88 | -0.18 / -0.23 / 0.27 | -0.42 | 0.32 | 1.00 | -0.27 | 0.00 | 6582 | diag |
| BTC 3 (diag) | 1m run5 dir=against hold=3m | 4541 | 0 | -0.97 | -5.56 | -1.26 | -1.72 / -2.78 | -0.21 / -0.26 / -0.24 | -0.80 | -0.38 | 1.00 | -0.43 | 0.00 | 7239 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 0 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 0 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 14 |
| worst-decile corr <= +0.30 | 18 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 1m run5 dir=against hold=5m (diag) | clean | -0.17 | -0.27 | -127135 | -101876 | 686584 | -207773 | -0.23 | 58.1 | 1.40 | -84137 | 287582 | -94212 |
| BTC 1m run5 dir=against hold=5m (diag) | H1 | -0.70 | -0.99 | -82857 | -79596 | 467959 | -91676 | -0.32 | 50.0 | 2.72 | -79496 | 149280 | -92902 |
| BTC 1m run5 dir=against hold=5m (diag) | H2 | -0.47 | -0.55 | -147789 | -111352 | 326704 | -215232 | -0.40 | 44.4 | 2.30 | -85130 | 197855 | -93941 |
| BTC 1m run5 dir=against hold=5m (diag) | all | -0.31 | -0.45 | -129548 | -104409 | 756862 | -215232 | -0.58 | 53.6 | 1.79 | -85364 | 287582 | -94212 |
| CL 1m run5 dir=against hold=10m (diag) | clean | -6.56 | -4.95 | -198127 | -166493 | 5951518 | -400758 | -1.00 | 83.8 | 0.15 | -110091 | 469893 | -160019 |
| CL 1m run5 dir=against hold=10m (diag) | H1 | -7.17 | -5.15 | -169049 | -152682 | 1453709 | -180907 | -0.97 | 85.7 | 1.43 | -90860 | 180926 | -102277 |
| CL 1m run5 dir=against hold=10m (diag) | H2 | -6.85 | -5.04 | -410333 | -386276 | 4725799 | -420133 | -1.00 | 83.3 | -0.52 | -146464 | 346736 | -163680 |
| CL 1m run5 dir=against hold=10m (diag) | all | -5.88 | -4.61 | -342828 | -273197 | 12087452 | -420133 | -1.00 | 84.5 | 0.18 | -123038 | 469893 | -163680 |
| ES 1m pin0.8 dir=against hold=10m (diag) | clean | -5.81 | -4.87 | -161795 | -144147 | 5379090 | -185144 | -0.99 | 84.8 | 0.29 | -99901 | 397276 | -116615 |
| ES 1m pin0.8 dir=against hold=10m (diag) | H1 | -5.46 | -4.58 | -169507 | -163225 | 1649386 | -175337 | -0.92 | 75.0 | 1.43 | -77346 | 222063 | -89860 |
| ES 1m pin0.8 dir=against hold=10m (diag) | H2 | -1.69 | -2.03 | -185379 | -168125 | 917567 | -192213 | -0.84 | 58.3 | 1.64 | -110150 | 247375 | -115363 |
| ES 1m pin0.8 dir=against hold=10m (diag) | all | -4.54 | -4.22 | -172021 | -156288 | 7677271 | -192213 | -0.99 | 77.4 | 0.78 | -101542 | 397276 | -116615 |
| GC 1m pin0.8 dir=against hold=10m (diag) | clean | -4.29 | -3.99 | -177898 | -150176 | 3979662 | -238545 | -1.00 | 75.2 | 0.58 | -94304 | 330623 | -103967 |
| GC 1m pin0.8 dir=against hold=10m (diag) | H1 | 0.24 | 0.41 | -252076 | -229616 | 1344286 | -273291 | 0.12 | 53.6 | 2.65 | -74609 | 238048 | -101058 |
| GC 1m pin0.8 dir=against hold=10m (diag) | H2 | -0.44 | -0.60 | -367326 | -300081 | 1397523 | -465012 | -0.28 | 52.8 | 1.76 | -121660 | 279397 | -153207 |
| GC 1m pin0.8 dir=against hold=10m (diag) | all | -1.51 | -1.97 | -263723 | -219416 | 4743042 | -465012 | -0.88 | 66.7 | 1.19 | -101134 | 330623 | -153207 |
| NQ 1m pin0.8 dir=with hold=5m (diag) | clean | -0.14 | -0.26 | -90679 | -76398 | 756752 | -134430 | -0.16 | 56.2 | 1.37 | -88424 | 246829 | -104444 |
| NQ 1m pin0.8 dir=with hold=5m (diag) | H1 | -1.07 | -1.54 | -63906 | -61621 | 416795 | -69135 | -0.42 | 57.1 | 2.60 | -82746 | 154003 | -84361 |
| NQ 1m pin0.8 dir=with hold=5m (diag) | H2 | -1.55 | -1.78 | -169461 | -133348 | 813072 | -236270 | -0.64 | 58.3 | 1.90 | -94437 | 209858 | -102633 |
| NQ 1m pin0.8 dir=with hold=5m (diag) | all | -0.58 | -0.90 | -113924 | -92922 | 1388596 | -236270 | -0.59 | 57.1 | 1.67 | -89309 | 246829 | -104444 |
| RTY 1m pin0.8 dir=against hold=10m (diag) | clean | -4.22 | -4.04 | -152720 | -141974 | 3881927 | -177402 | -0.99 | 71.4 | 0.60 | -96360 | 366813 | -110497 |
| RTY 1m pin0.8 dir=against hold=10m (diag) | H1 | -4.10 | -4.07 | -96161 | -93400 | 925591 | -101253 | -0.89 | 78.6 | 2.04 | -71799 | 169910 | -77853 |
| RTY 1m pin0.8 dir=against hold=10m (diag) | H2 | -2.73 | -2.98 | -147800 | -130744 | 1065283 | -153250 | -0.81 | 66.7 | 1.67 | -105642 | 228520 | -113175 |
| RTY 1m pin0.8 dir=against hold=10m (diag) | all | -3.90 | -3.83 | -150392 | -135646 | 5600471 | -177402 | -0.99 | 71.4 | 1.05 | -97977 | 366813 | -113175 |
| YM 1m pin0.8 dir=with hold=10m (diag) | clean | -2.98 | -3.11 | -173723 | -144821 | 2729989 | -254035 | -1.00 | 71.4 | 0.82 | -99271 | 356118 | -121042 |
| YM 1m pin0.8 dir=with hold=10m (diag) | H1 | -3.78 | -3.66 | -142345 | -139548 | 1124365 | -150680 | -0.84 | 75.0 | 1.78 | -95414 | 161384 | -103735 |
| YM 1m pin0.8 dir=with hold=10m (diag) | H2 | -5.23 | -4.44 | -201185 | -174085 | 1863788 | -235384 | -0.97 | 77.8 | 1.21 | -93962 | 270437 | -95073 |
| YM 1m pin0.8 dir=with hold=10m (diag) | all | -3.61 | -3.53 | -181142 | -156473 | 5482025 | -254035 | -1.00 | 73.2 | 1.05 | -98588 | 356118 | -121042 |
| ZN 1m run5 dir=with hold=10m (diag) | clean | -6.31 | -4.77 | -211400 | -159397 | 5723424 | -591071 | -1.00 | 96.2 | 0.20 | -93729 | 450084 | -102990 |
| ZN 1m run5 dir=with hold=10m (diag) | H1 | -15.21 | -6.54 | -72499 | -69372 | 1163499 | -80550 | -0.99 | 96.4 | 1.75 | -85686 | 186929 | -86087 |
| ZN 1m run5 dir=with hold=10m (diag) | H2 | -11.74 | -6.17 | -105646 | -95073 | 1530691 | -119236 | -1.00 | 100.0 | 1.37 | -87441 | 230830 | -87471 |
| ZN 1m run5 dir=with hold=10m (diag) | all | -7.02 | -5.04 | -177291 | -136201 | 8403788 | -591071 | -1.00 | 97.6 | 0.69 | -91482 | 450084 | -102990 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 1m pin0.8 dir=against hold=10m (diag) | -115.1 | -34.5 | -15.8 | -224.3 | -35.6 / -11.4 | 6.4 / 16.3 | NO |
| NQ 1m pin0.8 dir=with hold=5m (diag) | -39.1 | -14.7 | 8.9 | 19.2 | -15.6 / 10.0 | 17.0 / 20.1 | NO |
| RTY 1m pin0.8 dir=against hold=10m (diag) | -91.7 | -25.7 | -8.5 | -119.6 | -22.4 / -8.0 | 29.4 / 34.6 | NO |
| YM 1m pin0.8 dir=with hold=10m (diag) | -91.1 | -45.4 | -12.5 | -23.8 | -46.6 / -14.6 | -20.1 / -4.4 | NO |
| GC 1m pin0.8 dir=against hold=10m (diag) | -76.9 | -120.1 | -21.8 | -52.7 | -15.2 / -2.6 | -15.0 / 1.2 | NO |
| CL 1m run5 dir=against hold=10m (diag) | -165.0 | -120.3 | -59.7 | -525.4 | -115.1 / -30.1 | -16.0 / 1.5 | NO |
| ZN 1m run5 dir=with hold=10m (diag) | -123.9 | -45.5 | -2.6 | -221.5 | -46.7 / -10.7 | 13.7 / 14.4 | NO |
| BTC 1m run5 dir=against hold=5m (diag) | -34.9 | 3.9 | 16.2 | 12.9 | 3.2 / 17.8 | 2.0 / 16.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) 1m run5 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 28769 | 4.8 | -24.5 | -12.1 | 29.4 | 1.31 / -6.13 / -3.14 | 4.0 / -25.3 |
| ES 2 (diag) 1m out2.0 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 21070 | 2.7 | -26.6 | -13.0 | 29.4 | 0.68 / -6.52 / -3.18 | 3.3 / -26.0 |
| ES 3 (diag) 1m pin0.8 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 21848 | 0.6 | -28.8 | -12.6 | 29.4 | 0.29 / -8.28 / -5.72 | 2.9 / -26.5 |
| NQ 1 (diag) 1m pin0.8 dir=with hold=5m | gross-positive, cost-negative pre-2023 | 16824 | 2.1 | -12.3 | -2.5 | 14.4 | 0.80 / -4.25 / -0.97 | 12.6 / -1.8 |
| NQ 2 (diag) 1m out2.0 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 31788 | 1.7 | -12.6 | -3.8 | 14.4 | 0.39 / -2.90 / -0.88 | 8.0 / -6.3 |
| NQ 3 (diag) 1m pin0.8 dir=with hold=3m | gross-positive, cost-negative pre-2023 | 17361 | 1.6 | -12.7 | -2.9 | 14.4 | 0.79 / -5.16 / -1.38 | 7.4 / -6.9 |
| RTY 1 (diag) 1m pin0.8 dir=against hold=10m | negative pre-2023 | 9668 | -0.5 | -14.9 | -12.5 | 14.4 | -0.22 / -6.36 / -5.55 | 1.3 / -13.1 |
| RTY 2 (diag) 1m run5 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 25968 | 1.9 | -12.4 | -10.4 | 14.4 | 0.84 / -5.31 / -4.45 | 3.2 / -11.2 |
| RTY 3 (diag) 1m pin0.8 dir=with hold=10m | gross-positive, cost-negative pre-2023 | 9668 | 0.5 | -13.9 | -11.5 | 14.4 | 0.22 / -5.93 / -4.91 | -1.3 / -15.6 |
| YM 1 (diag) 1m pin0.8 dir=with hold=10m | negative pre-2023 | 19520 | -0.9 | -15.3 | -8.8 | 14.4 | -0.51 / -7.56 / -4.76 | 3.8 / -10.5 |
| YM 2 (diag) 1m out2.0 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 34652 | 0.5 | -13.9 | -8.1 | 14.4 | 0.24 / -6.69 / -3.86 | 1.4 / -13.0 |
| YM 3 (diag) 1m pin0.8 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 19520 | 0.9 | -13.5 | -7.0 | 14.4 | 0.51 / -6.65 / -3.93 | -3.8 / -18.2 |
| GC 1 (diag) 1m pin0.8 dir=against hold=10m | negative pre-2023 | 15517 | -1.1 | -25.5 | -15.3 | 24.4 | -0.37 / -7.56 / -4.85 | 1.7 / -22.6 |
| GC 2 (diag) 1m pin0.7 dir=with hold=10m | gross-positive, cost-negative pre-2023 | 29983 | 0.7 | -23.6 | -13.6 | 24.4 | 0.29 / -9.11 / -5.31 | 2.7 / -21.7 |
| GC 3 (diag) 1m pin0.8 dir=with hold=5m | gross-positive, cost-negative pre-2023 | 16233 | 0.9 | -23.5 | -13.2 | 24.4 | 0.39 / -8.96 / -5.68 | 1.9 / -22.5 |
| CL 1 (diag) 1m run5 dir=against hold=10m | gross-positive, cost-negative pre-2023 | 33582 | 2.1 | -22.2 | -20.2 | 24.4 | 0.69 / -6.65 / -5.55 | 4.6 / -19.8 |
| CL 2 (diag) 1m run5 dir=with hold=10m | negative pre-2023 | 33582 | -2.1 | -26.5 | -24.4 | 24.4 | -0.69 / -7.74 / -6.64 | -4.6 / -28.9 |
| CL 3 (diag) 1m pin0.8 dir=with hold=10m | gross-positive, cost-negative pre-2023 | 19128 | 0.2 | -24.1 | -23.2 | 24.4 | 0.10 / -7.19 / -5.84 | -1.2 / -25.6 |
| ZN 1 (diag) 1m run5 dir=with hold=10m | negative pre-2023 | 5875 | -2.5 | -38.1 | -43.0 | 35.6 | -0.90 / -7.74 / -8.01 | -2.5 / -38.1 |
| ZN 2 (diag) 1m run5 dir=with hold=5m | negative pre-2023 | 6070 | -2.1 | -37.7 | -42.6 | 35.6 | -1.00 / -8.27 / -8.48 | -1.6 / -37.2 |
| ZN 3 (diag) 1m run5 dir=with hold=3m | negative pre-2023 | 6093 | -2.0 | -37.6 | -42.6 | 35.6 | -1.24 / -7.95 / -8.08 | -1.4 / -37.0 |
| BTC 1 (diag) 1m run5 dir=against hold=5m | negative pre-2023 | 2100 | 0.0 | -54.4 | -22.4 | 54.4 | 0.00 / -4.24 / -1.84 | 50.2 / -4.2 |
| BTC 2 (diag) 1m run5 dir=against hold=10m | negative pre-2023 | 1964 | -8.5 | -62.9 | -30.9 | 54.4 | -0.46 / -3.26 / -1.66 | 31.6 / -22.8 |
| BTC 3 (diag) 1m run5 dir=against hold=3m | negative pre-2023 | 2136 | -2.4 | -56.7 | -24.7 | 54.4 | -0.26 / -5.56 / -2.71 | 36.7 / -17.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); NQ: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); RTY: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); YM: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- No cell passed the clean rule on any instrument; the pair window was read only for the diagnostic cells.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_15.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw15/ (`SW15_CO_all_selected_scored.csv`).

DONE SW15
