# REPORT BM6 - ADR exhaustion (BM batch)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 13 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.20; best pair-window standalone Sharpe +1.28.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. ADR exhaustion. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      16 |         16 |         0 |               1.155 |                1 |          0 |            3 |
| CL    |      16 |         16 |         1 |               0.468 |                2 |          1 |            3 |
| ES    |      16 |         16 |         2 |               0.494 |                2 |          2 |            3 |
| GC    |      16 |         16 |         1 |               0.949 |                2 |          1 |            3 |
| NQ    |      16 |         16 |         7 |               1.099 |                2 |          7 |            3 |
| RTY   |      16 |         16 |         2 |               0.654 |                2 |          2 |            3 |
| YM    |      16 |         16 |         0 |               0.375 |                1 |          0 |            3 |
| ZN    |      16 |         16 |         0 |              -2.146 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    2 |            2.09  |               6 |      0.58  |                       0.325 |            0.66  |           1.117 |     0.8  |       0.326 |                1.506 |
| NQ    |     200 |                    7 |            3.25  |               9 |      0.045 |                       0.71  |            0.785 |           1.245 |     0.57 |       1.099 |                1.763 |
| RTY   |     200 |                    2 |            2.02  |               7 |      0.615 |                       0.56  |            0.686 |           1.132 |     0.6  |       0.654 |                1.592 |
| YM    |     200 |                    0 |            2.415 |               6 |      1     |                     nan     |            0.711 |           1.185 |   nan    |     nan     |                1.7   |
| GC    |     200 |                    1 |            1.6   |               5 |      0.835 |                       0.166 |            0.65  |           1.189 |     0.78 |       0.166 |                1.576 |
| CL    |     200 |                    1 |            1.12  |               5 |      0.7   |                       0.468 |            0.64  |           1.207 |     0.5  |       0.468 |                1.446 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     200 |                    0 |            2.865 |               7 |      1     |                     nan     |            0.741 |           1.287 |   nan    |     nan     |                1.832 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 120 | 2 | 0.33 | -0.29 | 0.48 | 0.78 / 1.21 | -0.01 / 0.33 / 0.06 | -0.00 | 0.49 | 0.86 | -0.12 | 0.25 | 208 | NO |
| ES 2 | clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | 253 | 2 | 0.32 | -0.17 | 0.61 | 0.97 / 1.01 | 0.04 / 0.01 / 0.22 | 0.02 | 0.55 | 0.95 | -0.10 | 0.25 | 419 | NO |
| ES 3 (diag) | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | 157 | 1 | 0.49 | -0.08 | 0.94 | 1.47 / 1.11 | 0.07 / 0.13 / 0.39 | 0.11 | 0.52 | 0.99 | -0.03 | 0.00 | 260 | diag |
| ES 4 (diag) | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | 215 | 1 | 0.26 | -0.44 | 0.53 | 1.08 / 0.97 | -0.01 / 0.37 / 0.08 | 0.01 | 0.48 | 0.94 | -0.09 | 0.50 | 360 | diag |
| ES 5 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 120 | 1 | 0.24 | -0.52 | -0.37 | -1.32 / 0.99 | 0.05 / -0.43 / -0.38 | -0.15 | -0.46 | 0.49 | -0.29 | 0.00 | 208 | diag |
| NQ 1 | clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | 262 | 2 | 1.10 | 0.51 | 1.15 | 1.21 / 1.30 | 0.17 / 0.13 / 0.23 | 0.17 | 0.51 | 0.99 | 0.00 | 0.50 | 444 | LEAD |
| NQ 2 | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | 157 | 2 | 1.02 | 0.37 | 1.28 | 1.60 / 1.42 | 0.15 / 0.30 / 0.31 | 0.19 | 0.52 | 1.00 | 0.03 | 0.25 | 267 | LEAD |
| NQ 3 | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 130 | 2 | 0.76 | -0.43 | -0.11 | -1.15 / 1.41 | 0.16 / -0.42 / -0.44 | -0.05 | -0.48 | 0.46 | -0.26 | 0.00 | 230 | NO |
| NQ 4 | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=60m | 157 | 2 | 0.71 | 0.18 | 0.92 | 1.21 / 1.51 | 0.08 / 0.51 / 0.05 | 0.10 | 0.56 | 0.98 | -0.08 | 0.25 | 267 | NO |
| NQ 5 | clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=60m | 262 | 2 | 0.67 | 0.27 | 0.93 | 1.28 / 1.39 | 0.07 / 0.46 / 0.02 | 0.09 | 0.59 | 0.97 | -0.09 | 0.25 | 444 | NO |
| NQ 6 | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | 229 | 2 | 0.43 | -0.30 | 0.56 | 0.67 / 1.51 | 0.01 / 0.20 / -0.01 | 0.01 | 0.41 | 0.85 | -0.13 | 0.50 | 390 | NO |
| NQ 7 | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 130 | 2 | 0.29 | -0.22 | 0.52 | 0.87 / 1.34 | -0.02 / 0.24 / 0.10 | 0.01 | 0.54 | 0.89 | -0.13 | 0.50 | 230 | NO |
| NQ 8 (diag) | clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | 231 | 1 | 0.20 | -0.28 | -0.18 | -0.59 / 1.45 | 0.05 / -0.38 / -0.11 | -0.06 | -0.38 | 0.49 | -0.26 | 0.00 | 392 | diag |
| NQ 9 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | 130 | 0 | -0.36 | -0.01 | -0.61 | -0.97 / 1.41 | -0.05 / -0.34 / -0.17 | -0.11 | -0.54 | 0.14 | -0.28 | 0.00 | 230 | diag |
| NQ 10 (diag) | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=60m | 231 | 1 | -0.46 | -0.18 | -0.05 | 0.39 / 1.29 | -0.15 / 0.04 / -0.13 | -0.14 | 0.38 | 0.58 | -0.34 | 0.00 | 392 | diag |
| RTY 1 | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 141 | 2 | 0.65 | -0.50 | -0.46 | -1.99 / 1.15 | 0.08 / -1.25 / -0.03 | -0.19 | -0.47 | 0.39 | -0.36 | 0.00 | 230 | NO |
| RTY 2 | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | 155 | 2 | 0.47 | 0.25 | 0.24 | -0.01 / 1.22 | 0.07 / 0.16 / -0.32 | -0.03 | 0.51 | 0.79 | -0.23 | 0.25 | 260 | NO |
| RTY 3 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | 141 | 1 | 0.61 | -0.13 | 0.06 | -1.23 / 1.15 | 0.07 / -0.54 / -0.02 | -0.06 | -0.47 | 0.68 | -0.17 | 0.00 | 230 | diag |
| RTY 4 (diag) | clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | 241 | 1 | 0.34 | -0.51 | -0.40 | -1.60 / 0.90 | 0.01 / -0.96 / 0.02 | -0.19 | -0.47 | 0.51 | -0.30 | 0.00 | 410 | diag |
| RTY 5 (diag) | clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | 270 | 1 | 0.31 | 0.10 | 0.29 | 0.26 / 1.09 | 0.02 / 0.11 / -0.13 | -0.05 | 0.44 | 0.89 | -0.21 | 0.25 | 459 | diag |
| YM 1 (diag) | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 126 | 1 | 0.38 | -0.06 | 0.46 | 0.76 / 1.07 | 0.02 / 0.47 / -0.01 | 0.03 | 0.32 | 0.85 | -0.08 | 0.50 | 215 | diag |
| YM 2 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 126 | 1 | 0.33 | -0.51 | -0.26 | -1.24 / 1.04 | 0.00 / -0.89 / -0.05 | -0.17 | -0.08 | 0.53 | -0.32 | 0.00 | 215 | diag |
| YM 3 (diag) | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | 213 | 1 | 0.31 | -0.40 | 0.34 | 0.29 / 1.57 | 0.01 / 0.49 / -0.12 | 0.00 | 0.21 | 0.81 | -0.11 | 0.75 | 377 | diag |
| GC 1 | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 175 | 2 | 0.17 | -0.42 | 0.05 | 0.07 / 1.56 | -0.07 / 0.44 / -0.34 | -0.11 | -0.03 | 0.67 | -0.46 | 0.00 | 279 | NO |
| GC 2 (diag) | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | 198 | 1 | 0.95 | -0.99 | -0.09 | -0.68 / 1.45 | 0.14 / -2.33 / 0.50 | -0.25 | -0.33 | 0.59 | -0.60 | 0.00 | 305 | diag |
| GC 3 (diag) | clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | 322 | 1 | 0.30 | -1.21 | -0.53 | -1.09 / 1.34 | 0.02 / -1.55 / -0.47 | -0.40 | 0.04 | 0.27 | -0.70 | 0.00 | 506 | diag |
| GC 4 (diag) | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=60m | 175 | 1 | -0.07 | -0.50 | 0.51 | 0.99 / 1.44 | -0.10 / 1.09 / -0.17 | 0.01 | -0.10 | 0.90 | -0.27 | 0.25 | 280 | diag |
| CL 1 | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | 146 | 2 | 0.47 | -0.43 | -0.01 | -0.77 / 1.20 | 0.06 / 0.21 / -0.44 | -0.09 | -0.00 | 0.72 | -0.24 | 0.00 | 252 | NO |
| CL 2 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 146 | 1 | 0.26 | -0.29 | 0.10 | -0.14 / 0.82 | 0.07 / 0.27 / -0.42 | -0.11 | -0.06 | 0.84 | -0.25 | 0.00 | 252 | diag |
| CL 3 (diag) | clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | 255 | 1 | 0.19 | -0.87 | 0.62 | 1.10 / 1.06 | 0.02 / -0.11 / 0.38 | -0.04 | -0.21 | 0.97 | -0.15 | 0.50 | 424 | diag |
| CL 4 (diag) | clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=120m | 255 | 1 | 0.09 | -0.89 | 0.07 | 0.04 / 0.92 | -0.02 / 0.06 / -0.08 | -0.11 | -0.07 | 0.89 | -0.23 | 0.00 | 424 | diag |
| ZN 1 (diag) | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 145 | 0 | -2.15 | -1.93 | -2.10 | -2.27 / -1.62 | -0.39 / -0.33 / -0.45 | -0.75 | -0.08 | 0.82 | -0.58 | 0.00 | 240 | diag |
| ZN 2 (diag) | clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | 172 | 0 | -2.31 | -1.83 | -2.50 | -3.12 / -2.10 | -0.45 / -0.29 / -0.42 | -0.79 | -0.03 | 0.76 | -0.61 | 0.00 | 278 | diag |
| ZN 3 (diag) | clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | 145 | 0 | -2.33 | -3.22 | -3.24 | -5.24 / -2.80 | -0.52 / -0.90 / -0.76 | -1.06 | -0.12 | 0.85 | -0.83 | 0.00 | 240 | diag |
| BTC 1 (diag) | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | 238 | 1 | 1.15 | 0.66 | 1.00 | 0.77 / 1.12 | 0.17 / 0.76 / -0.21 | 0.12 | -0.06 | 0.99 | -0.02 | 0.75 | 383 | diag |
| BTC 2 (diag) | clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=60m | 239 | 1 | 1.06 | -0.95 | 0.78 | 0.44 / 0.89 | 0.17 / 0.57 / -0.27 | 0.09 | 0.28 | 0.99 | -0.06 | 0.75 | 384 | diag |
| BTC 3 (diag) | clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | 141 | 1 | 1.05 | 0.63 | 1.08 | 1.12 / 1.57 | 0.15 / 0.66 / -0.17 | 0.14 | 0.07 | 0.98 | -0.01 | 0.25 | 225 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 13 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 1 |
| all-in uplift @20% > 0 (all scored) | 19 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 23 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | clean | 1.05 | 2.03 | -101312 | -82746 | 323421 | -188284 | 2.94 | 34.3 | 1.61 | -89119 | 240913 | -115376 |
| BTC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H1 | 3.01 | 7.79 | -101652 | -73796 | 174622 | -152460 | 5.32 | 14.3 | 3.49 | -92228 | 151557 | -108779 |
| BTC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H2 | -1.97 | -2.33 | -88051 | -67803 | 372344 | -113754 | -0.87 | 52.8 | 2.32 | -82464 | 222414 | -82524 |
| BTC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | all | 1.08 | 2.14 | -104117 | -81754 | 372344 | -188284 | 4.18 | 35.1 | 2.06 | -89825 | 240913 | -115376 |
| CL clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | clean | 0.47 | 0.74 | -132685 | -89082 | 319244 | -294491 | 1.32 | 36.2 | 1.52 | -83979 | 256471 | -102910 |
| CL clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | H1 | 0.89 | 1.39 | -55431 | -52540 | 136416 | -62684 | 0.74 | 35.7 | 3.04 | -75116 | 149503 | -76568 |
| CL clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | H2 | -1.34 | -1.49 | -266206 | -182414 | 823758 | -350477 | -0.65 | 44.4 | 2.05 | -90117 | 232352 | -96592 |
| CL clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | all | -0.01 | -0.01 | -164437 | -110760 | 875780 | -350477 | -0.02 | 37.5 | 1.86 | -84666 | 256471 | -102910 |
| ES clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | clean | 0.39 | 0.60 | -136747 | -105177 | 715847 | -238221 | 0.50 | 40.0 | 1.50 | -85976 | 321353 | -115202 |
| ES clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | H1 | 0.08 | 0.14 | -107579 | -97517 | 216735 | -127868 | 0.10 | 46.4 | 2.84 | -71362 | 146868 | -86472 |
| ES clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | H2 | 2.01 | 4.21 | -77232 | -59739 | 243538 | -82836 | 1.98 | 38.9 | 2.70 | -87952 | 215851 | -89685 |
| ES clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | all | 0.61 | 0.98 | -124275 | -97835 | 715847 | -238221 | 1.20 | 40.5 | 1.97 | -86470 | 321353 | -115202 |
| GC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | clean | 0.04 | 0.06 | -153060 | -117791 | 454773 | -250203 | 0.08 | 41.9 | 1.39 | -97704 | 285626 | -127299 |
| GC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | H1 | 1.09 | 1.92 | -334231 | -285686 | 819636 | -441813 | 0.99 | 35.7 | 3.27 | -77055 | 151713 | -90006 |
| GC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | H2 | -0.65 | -0.77 | -680562 | -463745 | 1928352 | -791571 | -0.36 | 38.9 | 2.14 | -87440 | 279766 | -92355 |
| GC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | all | 0.05 | 0.07 | -348139 | -246264 | 2178110 | -791571 | 0.07 | 39.9 | 1.84 | -94568 | 285626 | -127299 |
| NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | clean | 1.06 | 1.95 | -120751 | -91073 | 710282 | -171430 | 1.35 | 33.3 | 1.61 | -85029 | 289551 | -116160 |
| NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | H1 | 1.02 | 2.03 | -109969 | -95415 | 212944 | -133035 | 1.42 | 42.9 | 3.12 | -67112 | 151224 | -90767 |
| NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | H2 | 2.13 | 4.60 | -96915 | -76766 | 202630 | -126024 | 3.37 | 30.6 | 2.80 | -90565 | 212537 | -93215 |
| NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | all | 1.28 | 2.46 | -118941 | -93500 | 710282 | -171430 | 2.74 | 33.9 | 2.10 | -86897 | 289551 | -116160 |
| RTY clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | clean | 0.46 | 0.82 | -114241 | -92936 | 586863 | -172790 | 0.72 | 43.8 | 1.53 | -87327 | 275687 | -114789 |
| RTY clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | H1 | 1.20 | 2.68 | -88449 | -87271 | 266552 | -91787 | 1.30 | 39.3 | 2.99 | -81987 | 158073 | -96645 |
| RTY clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | H2 | -0.68 | -0.75 | -346711 | -204854 | 670368 | -521081 | -0.52 | 36.1 | 2.16 | -91875 | 216127 | -93839 |
| RTY clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | all | 0.24 | 0.33 | -163527 | -120875 | 829979 | -521081 | 0.50 | 41.7 | 1.90 | -89952 | 275687 | -114789 |
| YM clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | clean | 0.37 | 0.79 | -97802 | -75089 | 335509 | -158193 | 1.01 | 31.4 | 1.48 | -87106 | 279239 | -113513 |
| YM clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H1 | 2.44 | 5.72 | -44065 | -39935 | 67576 | -50571 | 4.74 | 35.7 | 3.30 | -69080 | 148347 | -79180 |
| YM clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H2 | -0.51 | -0.61 | -99887 | -70512 | 218836 | -143318 | -0.40 | 38.9 | 2.47 | -80211 | 219660 | -82524 |
| YM clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | all | 0.46 | 0.89 | -93201 | -71141 | 335509 | -158193 | 1.70 | 33.9 | 1.94 | -84717 | 279239 | -113513 |
| ZN clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | clean | -2.04 | -2.31 | -161725 | -137161 | 2223856 | -189188 | -0.84 | 48.6 | 1.07 | -86265 | 351421 | -96160 |
| ZN clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H1 | -2.31 | -2.55 | -79108 | -73030 | 440162 | -87118 | -0.74 | 57.1 | 2.50 | -76008 | 164620 | -78653 |
| ZN clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | H2 | -2.31 | -2.62 | -125947 | -117746 | 748964 | -134873 | -0.88 | 52.8 | 2.04 | -81864 | 221148 | -84074 |
| ZN clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | all | -2.10 | -2.38 | -148078 | -128402 | 3095474 | -189188 | -0.92 | 51.2 | 1.51 | -84441 | 351421 | -96160 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | -20.6 | -30.0 | 15.9 | 1.4 | -31.1 / 15.6 | 14.3 / 35.7 | NO |
| NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | -8.7 | -31.8 | 13.2 | 14.9 | -32.8 / 14.7 | 6.1 / 32.7 | NO |
| RTY clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | -25.5 | -80.6 | -0.2 | 8.3 | -30.3 / 13.6 | -5.2 / 15.9 | NO |
| YM clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | -23.8 | -27.0 | 18.6 | 30.5 | -28.0 / 12.8 | 28.3 / 44.9 | NO |
| GC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | -28.2 | -119.5 | -30.4 | -54.8 | -57.7 / -7.0 | -23.7 / -10.7 | NO |
| CL clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | -30.1 | -29.0 | 4.1 | 23.3 | -30.0 / 9.2 | 31.9 / 34.8 | NO |
| ZN clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | -61.2 | -0.1 | 17.5 | -8.2 | -0.9 / 13.8 | 29.3 / 33.1 | NO |
| BTC clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m (diag) | -13.0 | -34.4 | 7.6 | 37.6 | -35.4 / 7.1 | -28.4 / 1.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | negative pre-2023 | 671 | -0.1 | -29.5 | -14.9 | 29.4 | -0.00 / -0.29 / -0.15 | 128.3 / 99.0 |
| ES 2 clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 1260 | 18.7 | -10.6 | 3.8 | 29.4 | 0.30 / -0.17 / 0.06 | 64.9 / 35.6 |
| ES 3 (diag) clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 799 | 22.0 | -7.4 | 7.1 | 29.4 | 0.25 / -0.08 / 0.08 | 90.3 / 60.9 |
| ES 4 (diag) clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | negative pre-2023 | 1116 | -3.3 | -32.7 | -18.3 | 29.4 | -0.04 / -0.44 / -0.24 | 84.8 / 55.4 |
| ES 5 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | negative pre-2023 | 673 | -4.3 | -33.6 | -19.1 | 29.4 | -0.07 / -0.52 / -0.29 | 56.0 / 26.7 |
| NQ 1 clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | positive pre-2023 | 1341 | 61.9 | 47.5 | 56.1 | 14.4 | 0.66 / 0.51 / 0.60 | 184.1 / 169.8 |
| NQ 2 clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | positive pre-2023 | 842 | 58.6 | 44.2 | 52.9 | 14.4 | 0.50 / 0.37 / 0.45 | 241.6 / 227.2 |
| NQ 3 clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | negative pre-2023 | 712 | -19.2 | -33.6 | -24.9 | 14.4 | -0.24 / -0.43 / -0.32 | 145.5 / 131.1 |
| NQ 4 clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=60m | positive pre-2023 | 842 | 29.4 | 15.0 | 23.7 | 14.4 | 0.36 / 0.18 / 0.29 | 134.6 / 120.2 |
| NQ 5 clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=60m | positive pre-2023 | 1341 | 31.7 | 17.3 | 25.9 | 14.4 | 0.49 / 0.27 / 0.40 | 90.6 / 76.2 |
| NQ 6 clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | negative pre-2023 | 1187 | -14.7 | -29.0 | -20.5 | 14.4 | -0.15 / -0.30 / -0.21 | 141.6 / 127.2 |
| NQ 7 clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | negative pre-2023 | 711 | -12.6 | -27.0 | -18.3 | 14.4 | -0.10 / -0.22 / -0.15 | 158.5 / 144.1 |
| NQ 8 (diag) clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | negative pre-2023 | 1192 | -3.0 | -17.3 | -8.8 | 14.4 | -0.05 / -0.28 / -0.14 | 34.4 / 20.0 |
| NQ 9 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | gross-positive, cost-negative pre-2023 | 711 | 12.6 | -1.7 | 7.0 | 14.4 | 0.10 / -0.01 / 0.06 | -158.5 / -172.9 |
| NQ 10 (diag) clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=60m | gross-positive, cost-negative pre-2023 | 1192 | 3.0 | -11.4 | -2.8 | 14.4 | 0.05 / -0.18 / -0.05 | -34.4 / -48.8 |
| RTY 1 clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | negative pre-2023 | 393 | -13.0 | -27.3 | -25.0 | 14.4 | -0.24 / -0.50 / -0.46 | 43.3 / 28.9 |
| RTY 2 clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | positive pre-2023 | 498 | 31.3 | 16.9 | 19.2 | 14.4 | 0.46 / 0.25 / 0.28 | 40.8 / 26.4 |
| RTY 3 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | gross-positive, cost-negative pre-2023 | 392 | 6.6 | -7.8 | -5.5 | 14.4 | 0.11 / -0.13 / -0.09 | 77.4 / 63.0 |
| RTY 4 (diag) clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | negative pre-2023 | 712 | -4.0 | -18.4 | -16.2 | 14.4 | -0.12 / -0.51 / -0.45 | 27.3 / 13.0 |
| RTY 5 (diag) clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | positive pre-2023 | 821 | 19.1 | 4.8 | 7.0 | 14.4 | 0.41 / 0.10 / 0.15 | 27.5 / 13.2 |
| YM 1 (diag) clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 719 | 10.0 | -4.3 | 1.5 | 14.4 | 0.14 / -0.06 / 0.02 | 71.2 / 56.8 |
| YM 2 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | negative pre-2023 | 723 | -10.0 | -24.3 | -18.5 | 14.4 | -0.21 / -0.51 / -0.39 | 33.4 / 19.1 |
| YM 3 (diag) clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | negative pre-2023 | 1186 | -7.7 | -22.1 | -16.3 | 14.4 | -0.14 / -0.40 / -0.29 | 57.6 / 43.2 |
| GC 1 clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 864 | 6.1 | -18.3 | -8.6 | 24.4 | 0.14 / -0.42 / -0.20 | 27.1 / 2.8 |
| GC 2 (diag) clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | negative pre-2023 | 935 | -22.7 | -47.0 | -37.3 | 24.4 | -0.48 / -0.99 / -0.79 | 81.7 / 57.3 |
| GC 3 (diag) clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m | negative pre-2023 | 1497 | -18.7 | -43.1 | -33.3 | 24.4 | -0.52 / -1.21 / -0.94 | 38.1 / 13.8 |
| GC 4 (diag) clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=60m | gross-positive, cost-negative pre-2023 | 869 | 6.8 | -17.5 | -7.8 | 24.4 | 0.19 / -0.50 / -0.22 | 16.0 / -8.4 |
| CL 1 clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=120m | negative pre-2023 | 774 | -3.7 | -28.0 | -25.5 | 24.4 | -0.06 / -0.43 / -0.39 | 65.1 / 40.7 |
| CL 2 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | gross-positive, cost-negative pre-2023 | 780 | 11.5 | -12.8 | -10.3 | 24.4 | 0.26 / -0.29 / -0.23 | 38.1 / 13.7 |
| CL 3 (diag) clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=60m | negative pre-2023 | 1380 | -3.6 | -28.0 | -25.6 | 24.4 | -0.12 / -0.87 / -0.80 | 29.8 / 5.4 |
| CL 4 (diag) clock 12:00 label-day range>=0.8ADR dir=against move from day open hold=120m | negative pre-2023 | 1373 | -17.0 | -41.4 | -39.0 | 24.4 | -0.37 / -0.89 / -0.84 | 28.9 / 4.5 |
| ZN 1 (diag) clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 775 | 5.2 | -30.4 | -35.6 | 35.6 | 0.33 / -1.93 / -2.25 | 5.0 / -30.7 |
| ZN 2 (diag) clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m | gross-positive, cost-negative pre-2023 | 886 | 7.9 | -27.7 | -32.9 | 35.6 | 0.53 / -1.83 / -2.14 | 1.9 / -33.7 |
| ZN 3 (diag) clock 12:00 label-day range>=1.0ADR dir=against move from day open hold=60m | negative pre-2023 | 778 | -3.6 | -39.2 | -44.4 | 35.6 | -0.33 / -3.22 / -3.55 | 8.9 / -26.7 |
| BTC 1 (diag) clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=120m | positive pre-2023 | 151 | 166.6 | 112.2 | 143.9 | 54.4 | 0.97 / 0.66 / 0.84 | 424.1 / 369.7 |
| BTC 2 (diag) clock 12:00 label-day range>=0.8ADR dir=with move from day open hold=60m | negative pre-2023 | 151 | -67.7 | -122.1 | -90.4 | 54.4 | -0.53 / -0.95 / -0.71 | 305.6 / 251.3 |
| BTC 3 (diag) clock 12:00 label-day range>=1.0ADR dir=with move from day open hold=120m | positive pre-2023 | 91 | 197.5 | 143.2 | 175.4 | 54.4 | 0.86 / 0.63 / 0.77 | 550.7 / 496.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 2.9 (p(count) = 1.00); CL: 1 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.70, p(top) = 0.50); ES: 2 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.58, p(top) = 0.80); GC: 1 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.83, p(top) = 0.78); NQ: 7 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 0.04, p(top) = 0.57); RTY: 2 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.61, p(top) = 0.60); YM: 0 cells pass the clean rule against a replicate mean of 2.4 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 13 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.20 (NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell NQ clock 13:30 label-day range>=0.8ADR dir=with move from day open hold=120m: uplift +0.17/+0.13/+0.23, boot lo +0.00, plateau 0.50, 2x-slip +0.17, wd corr +0.51, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ clock 13:30 label-day range>=1.0ADR dir=with move from day open hold=120m: uplift +0.15/+0.30/+0.31, boot lo +0.03, plateau 0.25, 2x-slip +0.19, wd corr +0.52, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 6, 'positive pre-2023': 5, 'gross-positive, cost-negative pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_6.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm6/ (`BM6_CO_all_selected_scored.csv`).

## Lead note
- NQ 13:30 ET, label-day range >= 1.0 ADR, WITH the move from the day open, hold 120 min: uplift +0.15/+0.30/+0.31 at 20% (gate-3 at 20/30/50%), null rank 1.00, bootstrap lo +0.03, ERA positive pre-2023 (+0.37). FAILS worst-decile correlation +0.52 (needs <= +0.30), plateau 0.25 and worst week +40.8% at 20% share (> the share): LEAD gate-3 only, trend-day continuation that is correlated with the pair's bad weeks. Sized: 27.0 contracts at the pair's sigma, 20% = 5.4, worst 1-contract trade -$6,864.

DONE BM6
