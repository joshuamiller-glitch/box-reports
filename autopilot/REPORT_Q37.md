# REPORT Q37 - Q37: prior-week high/low breakouts (with/fade)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 10 selected cells (+30 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.48.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: prior-week high/low breakouts (with/fade).
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |       8 |          8 |         0 |               0.148 |                1 |          0 |            3 |
| CL    |       8 |          8 |         3 |               0.955 |                2 |          3 |            3 |
| ES    |       8 |          8 |         0 |               0.245 |                1 |          0 |            3 |
| GC    |       8 |          8 |         3 |               0.727 |                2 |          3 |            3 |
| HG    |       8 |          8 |         0 |               0.372 |                1 |          0 |            3 |
| HO    |       8 |          8 |         1 |               0.925 |                2 |          1 |            3 |
| NQ    |       8 |          8 |         0 |               0.296 |                1 |          0 |            3 |
| RTY   |       8 |          8 |         3 |               0.826 |                2 |          3 |            3 |
| SI    |       8 |          8 |         0 |               0.49  |                1 |          0 |            3 |
| ZN    |       8 |          8 |         0 |              -0.669 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.225 |               4 |      1     |                     nan     |            0.686 |           1.182 |  nan     |     nan     |                1.449 |
| NQ    |     200 |                    0 |            1.675 |               6 |      1     |                     nan     |            0.728 |           1.352 |  nan     |     nan     |                1.512 |
| RTY   |     200 |                    3 |            1.275 |               5 |      0.12  |                       0.746 |            0.707 |           1.295 |    0.345 |       0.826 |                1.458 |
| GC    |     200 |                    3 |            1.17  |               4 |      0.125 |                       0.591 |            0.697 |           1.271 |    0.4   |       0.727 |                1.468 |
| CL    |     200 |                    3 |            1.07  |               4 |      0.095 |                       0.585 |            0.678 |           1.297 |    0.4   |       0.955 |                1.431 |
| ZN    |     200 |                    0 |            0.045 |               1 |      1     |                     nan     |            0.341 |           0.598 |  nan     |     nan     |                0.598 |
| HO    |     200 |                    1 |            1.67  |               5 |      0.87  |                       0.925 |            0.718 |           1.258 |    0.195 |       0.925 |                1.612 |
| 6E    |     200 |                    0 |            0.55  |               3 |      1     |                     nan     |            0.586 |           1.073 |  nan     |     nan     |                1.307 |
| SI    |     200 |                    0 |            0.87  |               3 |      1     |                     nan     |            0.622 |           1.32  |  nan     |     nan     |                1.353 |
| HG    |     200 |                    0 |            1.005 |               4 |      1     |                     nan     |            0.673 |           1.194 |  nan     |     nan     |                1.448 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | week ('fade', 15, ('tr', 0.2)) | 85 | 1 | 0.25 | -1.07 | -0.22 | -1.36 / 0.45 | 0.03 / 0.04 / -0.38 | -0.10 | 0.11 | 0.64 | -0.20 | 0.00 | 142 | diag |
| ES 2 (diag) | week ('with', 15, ('tr', 0.3)) | 85 | 1 | 0.18 | -0.06 | 0.16 | 0.21 / 0.98 | -0.03 / -0.25 / -0.01 | -0.09 | -0.13 | 0.83 | -0.24 | 0.00 | 142 | diag |
| ES 3 (diag) | week ('with', 15, ('b1', 0.3)) | 85 | 1 | -0.03 | 0.21 | 0.07 | 0.32 / 1.12 | -0.08 / -0.22 / 0.03 | -0.10 | -0.39 | 0.76 | -0.26 | 0.00 | 142 | diag |
| NQ 1 (diag) | week ('with', 15, ('tr', 0.3)) | 89 | 1 | 0.30 | 0.56 | 0.17 | 0.05 / 1.26 | 0.04 / -0.05 / -0.13 | -0.02 | -0.23 | 0.74 | -0.22 | 0.00 | 143 | diag |
| NQ 2 (diag) | week ('with', 15, ('b1', 0.3)) | 89 | 1 | 0.30 | 0.50 | 0.16 | -0.02 / 1.39 | 0.04 / -0.10 / -0.15 | -0.02 | -0.23 | 0.60 | -0.24 | 0.00 | 143 | diag |
| NQ 3 (diag) | week ('fade', 15, ('tr', 0.2)) | 89 | 1 | 0.20 | -0.51 | 0.05 | -0.14 / 1.41 | -0.01 / -0.08 / -0.14 | -0.06 | 0.02 | 0.54 | -0.20 | 0.00 | 143 | diag |
| RTY 1 | week ('fade', 15, ('b1', 0.2)) | 89 | 2 | 0.83 | -0.29 | 0.88 | 0.86 / 1.25 | 0.10 / 0.31 / -0.01 | 0.08 | -0.24 | 0.99 | -0.08 | 0.00 | 143 | NO |
| RTY 2 | week ('fade', 15, ('b1', 0.3)) | 89 | 2 | 0.79 | -0.04 | 1.48 | 2.46 / 1.35 | 0.07 / 0.47 / 0.47 | 0.19 | -0.31 | 1.00 | 0.02 | 0.50 | 143 | NO |
| RTY 3 | week ('fade', 15, ('tr', 0.3)) | 89 | 2 | 0.63 | -0.32 | 1.29 | 2.18 / 1.11 | 0.05 / 0.38 / 0.38 | 0.15 | -0.38 | 1.00 | -0.01 | 1.00 | 143 | NO |
| RTY 4 (diag) | week ('fade', 15, ('tr', 0.2)) | 89 | 1 | 0.17 | -0.22 | 0.75 | 1.42 / 0.96 | -0.02 / 0.21 / 0.14 | 0.03 | -0.39 | 0.99 | -0.11 | 0.50 | 143 | diag |
| RTY 5 (diag) | week ('with', 15, ('tr', 0.3)) | 89 | 0 | -0.57 | -0.47 | -1.15 | -2.04 / 0.85 | -0.12 / -0.42 / -0.42 | -0.26 | -0.02 | 0.04 | -0.41 | 0.00 | 143 | diag |
| RTY 6 (diag) | week ('with', 15, ('tr', 0.2)) | 89 | 0 | -0.59 | -0.02 | -1.57 | -3.65 / 1.34 | -0.13 / -0.71 / -0.52 | -0.34 | -0.07 | 0.04 | -0.48 | 0.00 | 143 | diag |
| GC 1 | week ('with', 15, ('tr', 0.3)) | 87 | 2 | 0.73 | 0.03 | 0.67 | 0.74 / 1.30 | 0.11 / 1.04 / -0.49 | 0.07 | 0.47 | 0.95 | -0.21 | 0.00 | 137 | NO |
| GC 2 | week ('with', 15, ('b1', 0.2)) | 87 | 2 | 0.67 | 0.22 | 0.77 | 0.91 / 1.71 | 0.09 / 0.70 / 0.18 | 0.16 | 0.41 | 0.90 | -0.13 | 0.50 | 137 | NO |
| GC 3 | week ('with', 15, ('b1', 0.3)) | 87 | 2 | 0.38 | 0.12 | 0.67 | 0.90 / 1.54 | 0.02 / 1.23 / -0.41 | 0.08 | 0.45 | 0.89 | -0.23 | 0.50 | 137 | NO |
| GC 4 (diag) | week ('with', 15, ('tr', 0.2)) | 87 | 1 | -0.08 | -0.16 | 0.08 | 0.12 / 1.48 | -0.02 / 0.22 / -0.49 | -0.13 | 0.48 | 0.66 | -0.42 | 0.00 | 137 | diag |
| GC 5 (diag) | week ('fade', 15, ('b1', 0.3)) | 87 | 0 | -0.67 | -0.59 | -0.81 | -1.00 / 1.31 | -0.14 / -1.68 / -0.40 | -0.43 | -0.46 | 0.11 | -0.80 | 0.00 | 137 | diag |
| GC 6 (diag) | week ('fade', 15, ('b1', 0.2)) | 87 | 0 | -1.01 | -0.83 | -0.95 | -1.03 / 1.38 | -0.22 / -1.09 / -0.83 | -0.49 | -0.41 | 0.09 | -0.81 | 0.00 | 137 | diag |
| CL 1 | week ('with', 15, ('b1', 0.2)) | 85 | 2 | 0.95 | 0.20 | 0.31 | -0.23 / 1.62 | 0.22 / -0.32 / -0.47 | -0.05 | 0.18 | 0.77 | -0.26 | 0.00 | 139 | NO |
| CL 2 | week ('with', 15, ('tr', 0.3)) | 85 | 2 | 0.58 | 0.46 | 0.45 | 0.29 / 1.20 | 0.12 / -0.39 / -0.03 | -0.01 | 0.24 | 0.87 | -0.15 | 0.50 | 139 | NO |
| CL 3 | week ('with', 15, ('b1', 0.3)) | 85 | 2 | 0.22 | 0.11 | 0.40 | 0.69 / 1.44 | 0.02 / -0.30 / 0.10 | -0.02 | 0.29 | 0.90 | -0.20 | 0.50 | 139 | NO |
| CL 4 (diag) | week ('with', 15, ('tr', 0.2)) | 85 | 1 | 0.37 | 0.36 | 0.21 | 0.07 / 1.16 | 0.06 / -0.33 / -0.24 | -0.10 | 0.13 | 0.80 | -0.26 | 0.00 | 139 | diag |
| CL 5 (diag) | week ('fade', 15, ('tr', 0.2)) | 85 | 1 | -0.25 | -0.34 | -0.21 | -0.17 / 1.20 | -0.11 / 0.19 / -0.01 | -0.13 | -0.18 | 0.53 | -0.32 | 0.00 | 139 | diag |
| CL 6 (diag) | week ('fade', 15, ('b1', 0.3)) | 85 | 0 | -0.66 | -0.55 | -0.74 | -0.97 / 1.20 | -0.16 / 0.18 / -0.58 | -0.26 | -0.28 | 0.20 | -0.49 | 0.00 | 139 | diag |
| ZN 1 (diag) | week ('with', 15, ('b1', 0.3)) | 84 | 1 | -0.67 | 0.11 | -1.36 | -2.65 / -0.12 | -0.16 / -0.49 / -0.43 | -0.47 | 0.45 | 0.60 | -0.47 | 0.00 | 140 | diag |
| ZN 2 (diag) | week ('with', 15, ('b1', 0.2)) | 84 | 1 | -0.69 | -0.26 | -1.42 | -2.83 / -0.73 | -0.18 / -0.39 / -0.53 | -0.53 | 0.44 | 0.77 | -0.48 | 0.00 | 140 | diag |
| ZN 3 (diag) | week ('fade', 15, ('b1', 0.3)) | 84 | 0 | -1.80 | -2.38 | -1.25 | -0.25 / -0.14 | -0.37 / -0.19 / -0.12 | -0.46 | -0.42 | 0.64 | -0.46 | 0.00 | 140 | diag |
| HO 1 | week ('fade', 15, ('tr', 0.2)) | 83 | 2 | 0.92 | -0.13 | 0.40 | 0.16 / 1.41 | 0.13 / -0.20 / -0.06 | 0.02 | 0.30 | 0.76 | -0.21 | 1.00 | 139 | NO |
| HO 2 (diag) | week ('with', 15, ('b1', 0.3)) | 83 | 1 | 0.27 | 0.21 | -0.62 | -1.40 / 1.21 | 0.03 / -0.08 / -1.37 | -0.34 | 0.06 | 0.14 | -0.63 | 0.00 | 139 | diag |
| HO 3 (diag) | week ('fade', 15, ('b1', 0.2)) | 83 | 1 | -0.04 | -0.58 | 0.66 | 1.32 / 1.35 | -0.05 / -0.40 / 1.13 | 0.15 | 0.17 | 0.94 | -0.12 | 0.50 | 139 | diag |
| HO 4 (diag) | week ('with', 15, ('b1', 0.2)) | 83 | 1 | -0.21 | 0.34 | -0.82 | -1.44 / 0.96 | -0.06 / 0.18 / -1.57 | -0.40 | -0.16 | 0.08 | -0.67 | 0.00 | 139 | diag |
| 6E 1 (diag) | week ('with', 15, ('b1', 0.2)) | 86 | 1 | 0.15 | -1.49 | -0.21 | -1.06 / 0.90 | 0.04 / 0.05 / -0.38 | -0.13 | 0.59 | 0.80 | -0.23 | 0.00 | 133 | diag |
| 6E 2 (diag) | week ('with', 15, ('b1', 0.3)) | 86 | 1 | -0.05 | -2.02 | -0.25 | -0.80 / 0.75 | -0.02 / -0.09 / -0.25 | -0.14 | 0.59 | 0.73 | -0.25 | 0.00 | 133 | diag |
| 6E 3 (diag) | week ('fade', 15, ('b1', 0.3)) | 86 | 0 | -0.75 | 1.26 | -0.56 | -0.03 / 0.92 | -0.20 / -0.15 / 0.06 | -0.19 | -0.59 | 0.51 | -0.31 | 0.00 | 133 | diag |
| SI 1 (diag) | week ('with', 15, ('tr', 0.3)) | 91 | 1 | 0.49 | -0.35 | 1.06 | 1.64 / 1.21 | 0.06 / 0.11 / 0.33 | 0.16 | 0.39 | 1.00 | -0.12 | 0.50 | 139 | diag |
| SI 2 (diag) | week ('fade', 15, ('b1', 0.3)) | 91 | 1 | 0.12 | -0.36 | -0.69 | -1.25 / 1.14 | -0.00 / -0.67 / -1.77 | -0.52 | -0.49 | 0.17 | -1.00 | 0.00 | 139 | diag |
| SI 3 (diag) | week ('with', 15, ('tr', 0.2)) | 91 | 0 | -0.19 | -0.87 | 1.05 | 1.86 / 1.21 | -0.06 / 0.41 / 0.35 | 0.07 | 0.33 | 1.00 | -0.30 | 0.50 | 139 | diag |
| HG 1 (diag) | week ('fade', 15, ('tr', 0.3)) | 85 | 1 | 0.37 | -0.38 | 0.36 | 0.15 / 1.24 | 0.02 / 0.75 / -0.50 | -0.05 | 0.04 | 0.79 | -0.19 | 0.00 | 133 | diag |
| HG 2 (diag) | week ('fade', 15, ('tr', 0.2)) | 85 | 1 | 0.27 | -0.52 | -0.03 | -0.66 / 0.89 | -0.02 / 0.54 / -0.65 | -0.16 | 0.00 | 0.71 | -0.28 | 0.00 | 133 | diag |
| HG 3 (diag) | week ('fade', 15, ('b1', 0.3)) | 85 | 1 | 0.24 | -0.27 | 0.28 | 0.05 / 1.30 | -0.01 / 0.70 / -0.53 | -0.08 | -0.01 | 0.89 | -0.24 | 0.00 | 133 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 30 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 30 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 5 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E week ('with', 15, ('b1', 0.2)) (diag) | clean | 0.23 | 0.32 | -107678 | -100091 | 795967 | -140214 | 0.26 | 37.1 | 1.49 | -90828 | 304171 | -98468 |
| 6E week ('with', 15, ('b1', 0.2)) (diag) | H1 | -0.28 | -0.38 | -87209 | -84184 | 273388 | -93225 | -0.21 | 35.7 | 2.88 | -73311 | 163461 | -78287 |
| 6E week ('with', 15, ('b1', 0.2)) (diag) | H2 | -1.62 | -1.95 | -94617 | -89782 | 629912 | -95015 | -0.71 | 44.4 | 2.11 | -96596 | 237710 | -98497 |
| 6E week ('with', 15, ('b1', 0.2)) (diag) | all | -0.21 | -0.29 | -103275 | -96498 | 1190097 | -140214 | -0.25 | 38.7 | 1.84 | -92960 | 304171 | -98497 |
| CL week ('with', 15, ('tr', 0.3)) | clean | 0.58 | 1.21 | -78462 | -67459 | 423725 | -88238 | 1.24 | 47.6 | 1.58 | -85540 | 293540 | -94656 |
| CL week ('with', 15, ('tr', 0.3)) | H1 | -2.36 | -2.88 | -49867 | -47822 | 299832 | -50421 | -0.88 | 57.1 | 2.44 | -81983 | 161368 | -87034 |
| CL week ('with', 15, ('tr', 0.3)) | H2 | 0.92 | 1.80 | -133223 | -117456 | 349710 | -150764 | 1.32 | 47.2 | 2.45 | -105043 | 245043 | -109806 |
| CL week ('with', 15, ('tr', 0.3)) | all | 0.45 | 0.89 | -98236 | -81850 | 570034 | -150764 | 1.27 | 49.4 | 1.92 | -92341 | 293540 | -109806 |
| ES week ('with', 15, ('tr', 0.3)) (diag) | clean | 0.12 | 0.19 | -117892 | -95553 | 588538 | -213605 | 0.19 | 44.8 | 1.43 | -83679 | 245458 | -90942 |
| ES week ('with', 15, ('tr', 0.3)) (diag) | H1 | -1.52 | -1.95 | -72441 | -71094 | 265013 | -76193 | -1.00 | 53.6 | 2.57 | -80206 | 144706 | -88183 |
| ES week ('with', 15, ('tr', 0.3)) (diag) | H2 | 0.96 | 1.93 | -96538 | -90886 | 232248 | -97616 | 1.68 | 47.2 | 2.48 | -92004 | 227248 | -96769 |
| ES week ('with', 15, ('tr', 0.3)) (diag) | all | 0.16 | 0.26 | -109556 | -93168 | 1010649 | -213605 | 0.23 | 47.0 | 1.84 | -86029 | 245458 | -96769 |
| GC week ('with', 15, ('b1', 0.2)) | clean | 0.75 | 1.19 | -103263 | -90400 | 522507 | -158105 | 1.31 | 38.1 | 1.55 | -89572 | 300674 | -95086 |
| GC week ('with', 15, ('b1', 0.2)) | H1 | 1.55 | 2.51 | -193936 | -184217 | 586047 | -215700 | 1.24 | 28.6 | 3.53 | -75009 | 215994 | -78287 |
| GC week ('with', 15, ('b1', 0.2)) | H2 | 0.62 | 0.93 | -326192 | -315201 | 979985 | -327448 | 0.62 | 33.3 | 2.67 | -133250 | 262190 | -144641 |
| GC week ('with', 15, ('b1', 0.2)) | all | 0.77 | 1.16 | -251389 | -202523 | 979985 | -327448 | 2.06 | 35.7 | 2.08 | -99106 | 300674 | -144641 |
| HG week ('fade', 15, ('tr', 0.3)) (diag) | clean | 0.50 | 0.91 | -88482 | -79501 | 508655 | -104386 | 0.91 | 45.7 | 1.48 | -88746 | 314908 | -91059 |
| HG week ('fade', 15, ('tr', 0.3)) (diag) | H1 | 2.83 | 7.76 | -76523 | -67426 | 113446 | -100972 | 7.38 | 28.6 | 3.58 | -63752 | 123502 | -78287 |
| HG week ('fade', 15, ('tr', 0.3)) (diag) | H2 | -2.33 | -2.73 | -121101 | -111752 | 968991 | -133334 | -0.76 | 52.8 | 1.98 | -94710 | 249498 | -94827 |
| HG week ('fade', 15, ('tr', 0.3)) (diag) | all | 0.36 | 0.62 | -103228 | -90518 | 968991 | -133334 | 0.58 | 44.6 | 1.89 | -89170 | 314908 | -94827 |
| HO week ('fade', 15, ('tr', 0.2)) | clean | 0.84 | 1.99 | -62555 | -58470 | 224244 | -68318 | 3.39 | 41.9 | 1.59 | -81910 | 271459 | -88250 |
| HO week ('fade', 15, ('tr', 0.2)) | H1 | -2.13 | -2.61 | -62994 | -62815 | 367804 | -63172 | -0.92 | 64.3 | 2.62 | -81896 | 154092 | -84221 |
| HO week ('fade', 15, ('tr', 0.2)) | H2 | 0.55 | 1.16 | -287141 | -241921 | 771582 | -304443 | 0.71 | 44.4 | 2.43 | -116448 | 230844 | -133621 |
| HO week ('fade', 15, ('tr', 0.2)) | all | 0.40 | 0.83 | -168596 | -121577 | 771582 | -304443 | 1.26 | 46.4 | 1.94 | -93390 | 271459 | -133621 |
| NQ week ('with', 15, ('tr', 0.3)) (diag) | clean | 0.27 | 0.45 | -106016 | -88414 | 474030 | -182249 | 0.51 | 47.6 | 1.50 | -78857 | 251079 | -80784 |
| NQ week ('with', 15, ('tr', 0.3)) (diag) | H1 | 0.01 | 0.02 | -78325 | -73321 | 356569 | -90397 | 0.01 | 53.6 | 2.78 | -73779 | 172389 | -89406 |
| NQ week ('with', 15, ('tr', 0.3)) (diag) | H2 | 0.06 | 0.10 | -161560 | -140386 | 745714 | -173092 | 0.04 | 41.7 | 2.35 | -88140 | 217425 | -98864 |
| NQ week ('with', 15, ('tr', 0.3)) (diag) | all | 0.17 | 0.27 | -126579 | -108516 | 745714 | -182249 | 0.37 | 47.6 | 1.89 | -82094 | 251079 | -98864 |
| RTY week ('fade', 15, ('b1', 0.3)) | clean | 0.85 | 1.32 | -90117 | -83284 | 388001 | -116068 | 2.00 | 38.1 | 1.53 | -93352 | 299115 | -97405 |
| RTY week ('fade', 15, ('b1', 0.3)) | H1 | 3.38 | 6.77 | -79146 | -74637 | 184725 | -86532 | 4.02 | 28.6 | 3.30 | -71410 | 185552 | -78287 |
| RTY week ('fade', 15, ('b1', 0.3)) | H2 | 1.90 | 3.39 | -105801 | -92503 | 324454 | -108830 | 2.12 | 33.3 | 2.95 | -85887 | 243636 | -90322 |
| RTY week ('fade', 15, ('b1', 0.3)) | all | 1.48 | 2.44 | -93599 | -85152 | 388001 | -116068 | 5.69 | 35.7 | 2.10 | -92187 | 299115 | -97405 |
| SI week ('with', 15, ('tr', 0.3)) (diag) | clean | 0.42 | 0.92 | -63761 | -59472 | 340949 | -69504 | 1.12 | 50.5 | 1.52 | -83399 | 291182 | -87615 |
| SI week ('with', 15, ('tr', 0.3)) (diag) | H1 | 1.16 | 4.84 | -208626 | -187754 | 446621 | -215412 | 3.14 | 39.3 | 2.94 | -81891 | 139531 | -94317 |
| SI week ('with', 15, ('tr', 0.3)) (diag) | H2 | 2.15 | 6.00 | -259726 | -207666 | 387780 | -332868 | 6.45 | 30.6 | 2.82 | -133034 | 252090 | -146227 |
| SI week ('with', 15, ('tr', 0.3)) (diag) | all | 1.06 | 3.40 | -186672 | -138151 | 446621 | -332868 | 9.59 | 44.6 | 2.10 | -98753 | 291182 | -146227 |
| ZN week ('fade', 15, ('b1', 0.3)) (diag) | clean | -1.79 | -2.07 | -113644 | -108932 | 1660222 | -120371 | -0.98 | 47.6 | 1.09 | -91376 | 296341 | -101083 |
| ZN week ('fade', 15, ('b1', 0.3)) (diag) | H1 | -0.02 | -0.03 | -77300 | -75768 | 207410 | -79269 | -0.02 | 39.3 | 2.63 | -82511 | 183525 | -86734 |
| ZN week ('fade', 15, ('b1', 0.3)) (diag) | H2 | -0.40 | -0.53 | -79774 | -78638 | 379079 | -80885 | -0.31 | 41.7 | 2.37 | -79673 | 252094 | -81831 |
| ZN week ('fade', 15, ('b1', 0.3)) (diag) | all | -1.25 | -1.51 | -110710 | -104249 | 1918168 | -120371 | -0.91 | 45.2 | 1.62 | -88521 | 296341 | -101083 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES week ('with', 15, ('tr', 0.3)) (diag) | -27.4 | 1.3 | 13.8 | 38.7 | 11.4 / 18.1 | 9.7 / 25.0 | NO |
| NQ week ('with', 15, ('tr', 0.3)) (diag) | -27.0 | -2.5 | 19.9 | 29.3 | 25.7 / 27.4 | 7.3 / 21.6 | NO |
| RTY week ('fade', 15, ('b1', 0.3)) | -5.9 | 2.3 | 4.4 | 19.8 | 1.5 / 2.0 | 30.0 / 39.7 | NO |
| GC week ('with', 15, ('b1', 0.2)) | -8.0 | -85.7 | -13.1 | 11.1 | 1.0 / 8.1 | 5.4 / 17.0 | NO |
| CL week ('with', 15, ('tr', 0.3)) | -22.1 | -22.4 | 3.0 | 22.8 | 1.8 / 15.8 | 13.2 / 21.5 | NO |
| ZN week ('fade', 15, ('b1', 0.3)) (diag) | -49.1 | -9.1 | 8.0 | 3.4 | -9.9 / 1.7 | 12.4 / 20.5 | NO |
| HO week ('fade', 15, ('tr', 0.2)) | -19.4 | -65.7 | -0.0 | 29.3 | 18.3 / 23.2 | 17.2 / 21.7 | NO |
| 6E week ('with', 15, ('b1', 0.2)) (diag) | -33.3 | -1.8 | 3.3 | 7.9 | -2.4 / 6.1 | 30.0 / 34.5 | NO |
| SI week ('with', 15, ('tr', 0.3)) (diag) | 16.9 | -88.6 | -13.9 | 24.1 | 14.7 / 19.7 | -6.1 / -4.3 | NO |
| HG week ('fade', 15, ('tr', 0.3)) (diag) | -23.8 | 2.7 | 9.7 | 11.4 | 9.3 / 10.1 | 30.0 / 39.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) week ('fade', 15, ('tr', 0.2)) | negative pre-2023 | 467 | -39.2 | -68.6 | -54.4 | 29.4 | -0.61 / -1.07 / -0.85 | 66.4 / 37.1 |
| ES 2 (diag) week ('with', 15, ('tr', 0.3)) | gross-positive, cost-negative pre-2023 | 467 | 24.2 | -5.2 | 9.0 | 29.4 | 0.26 / -0.06 / 0.10 | 48.2 / 18.8 |
| ES 3 (diag) week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 467 | 44.6 | 20.1 | 31.9 | 24.5 | 0.47 / 0.21 / 0.33 | 10.0 / -14.0 |
| NQ 1 (diag) week ('with', 15, ('tr', 0.3)) | positive pre-2023 | 477 | 96.0 | 81.6 | 90.2 | 14.4 | 0.66 / 0.56 / 0.62 | 85.9 / 71.6 |
| NQ 2 (diag) week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 477 | 86.7 | 74.3 | 81.8 | 12.4 | 0.58 / 0.50 / 0.55 | 98.3 / 86.0 |
| NQ 3 (diag) week ('fade', 15, ('tr', 0.2)) | negative pre-2023 | 477 | -44.9 | -59.3 | -50.7 | 14.4 | -0.39 / -0.51 / -0.44 | 58.4 / 44.0 |
| RTY 1 week ('fade', 15, ('b1', 0.2)) | negative pre-2023 | 258 | -4.7 | -16.8 | -14.9 | 12.0 | -0.08 / -0.29 / -0.26 | 65.9 / 54.3 |
| RTY 2 week ('fade', 15, ('b1', 0.3)) | gross-positive, cost-negative pre-2023 | 258 | 9.0 | -3.4 | -1.5 | 12.4 | 0.12 / -0.04 / -0.02 | 84.7 / 72.7 |
| RTY 3 week ('fade', 15, ('tr', 0.3)) | negative pre-2023 | 258 | -8.6 | -22.9 | -20.7 | 14.4 | -0.12 / -0.32 / -0.29 | 74.1 / 59.8 |
| RTY 4 (diag) week ('fade', 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 258 | 2.1 | -12.3 | -10.1 | 14.4 | 0.04 / -0.22 / -0.18 | 31.2 / 16.8 |
| RTY 5 (diag) week ('with', 15, ('tr', 0.3)) | negative pre-2023 | 258 | -18.7 | -33.1 | -30.9 | 14.4 | -0.27 / -0.47 / -0.44 | -35.9 / -50.3 |
| RTY 6 (diag) week ('with', 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 258 | 13.3 | -1.0 | 1.1 | 14.4 | 0.23 / -0.02 / 0.02 | -19.4 / -33.7 |
| GC 1 week ('with', 15, ('tr', 0.3)) | positive pre-2023 | 431 | 26.8 | 2.4 | 12.3 | 24.4 | 0.29 / 0.03 / 0.13 | 132.9 / 108.6 |
| GC 2 week ('with', 15, ('b1', 0.2)) | positive pre-2023 | 431 | 33.7 | 14.2 | 22.2 | 19.5 | 0.52 / 0.22 / 0.34 | 106.2 / 86.6 |
| GC 3 week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 431 | 31.6 | 11.2 | 19.5 | 20.4 | 0.35 / 0.12 / 0.22 | 91.9 / 71.3 |
| GC 4 (diag) week ('with', 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 431 | 14.2 | -10.1 | -0.2 | 24.4 | 0.23 / -0.16 / -0.00 | 29.5 / 5.1 |
| GC 5 (diag) week ('fade', 15, ('b1', 0.3)) | negative pre-2023 | 431 | -31.8 | -53.0 | -44.4 | 21.2 | -0.36 / -0.59 / -0.49 | -91.9 / -113.1 |
| GC 6 (diag) week ('fade', 15, ('b1', 0.2)) | negative pre-2023 | 431 | -34.7 | -55.0 | -46.7 | 20.3 | -0.53 / -0.83 / -0.71 | -106.2 / -126.6 |
| CL 1 week ('with', 15, ('b1', 0.2)) | positive pre-2023 | 450 | 32.4 | 12.8 | 14.7 | 19.5 | 0.49 / 0.20 / 0.23 | 82.2 / 63.5 |
| CL 2 week ('with', 15, ('tr', 0.3)) | positive pre-2023 | 450 | 67.5 | 43.2 | 45.5 | 24.4 | 0.71 / 0.46 / 0.48 | 86.0 / 61.6 |
| CL 3 week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 450 | 31.9 | 11.4 | 13.4 | 20.5 | 0.34 / 0.11 / 0.14 | 31.4 / 11.4 |
| CL 4 (diag) week ('with', 15, ('tr', 0.2)) | positive pre-2023 | 450 | 51.7 | 27.3 | 29.6 | 24.4 | 0.67 / 0.36 / 0.39 | 49.9 / 25.6 |
| CL 5 (diag) week ('fade', 15, ('tr', 0.2)) | negative pre-2023 | 450 | -1.7 | -26.0 | -23.7 | 24.4 | -0.02 / -0.34 / -0.31 | 5.9 / -18.4 |
| CL 6 (diag) week ('fade', 15, ('b1', 0.3)) | negative pre-2023 | 450 | -31.9 | -52.7 | -50.7 | 20.8 | -0.34 / -0.55 / -0.53 | -31.5 / -52.0 |
| ZN 1 (diag) week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 430 | 31.6 | 2.9 | -1.2 | 28.7 | 1.25 / 0.11 / -0.05 | 13.8 / -16.6 |
| ZN 2 (diag) week ('with', 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 430 | 22.0 | -5.1 | -8.9 | 27.1 | 1.18 / -0.26 / -0.45 | 15.4 / -13.0 |
| ZN 3 (diag) week ('fade', 15, ('b1', 0.3)) | negative pre-2023 | 430 | -31.7 | -62.8 | -67.2 | 31.2 | -1.25 / -2.38 / -2.53 | -13.9 / -44.9 |
| HO 1 week ('fade', 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 463 | 0.2 | -12.6 | -11.1 | 12.8 | -0.01 / -0.13 / -0.12 | 101.6 / 88.8 |
| HO 2 (diag) week ('with', 15, ('b1', 0.3)) | positive pre-2023 | 463 | 36.7 | 25.6 | 26.9 | 11.1 | 0.29 / 0.21 / 0.22 | 56.7 / 45.7 |
| HO 3 (diag) week ('fade', 15, ('b1', 0.2)) | negative pre-2023 | 463 | -42.6 | -53.6 | -52.3 | 11.0 | -0.46 / -0.58 / -0.56 | 0.6 / -10.3 |
| HO 4 (diag) week ('with', 15, ('b1', 0.2)) | positive pre-2023 | 463 | 42.0 | 31.3 | 32.6 | 10.7 | 0.46 / 0.34 / 0.36 | -0.8 / -11.6 |
| 6E 1 (diag) week ('with', 15, ('b1', 0.2)) | negative pre-2023 | 450 | -35.5 | -49.9 | -51.0 | 14.4 | -1.08 / -1.49 / -1.52 | 19.9 / 6.0 |
| 6E 2 (diag) week ('with', 15, ('b1', 0.3)) | negative pre-2023 | 450 | -76.9 | -92.0 | -93.1 | 15.1 | -1.70 / -2.02 / -2.04 | 15.9 / 1.4 |
| 6E 3 (diag) week ('fade', 15, ('b1', 0.3)) | positive pre-2023 | 450 | 71.1 | 57.1 | 56.2 | 14.0 | 1.58 / 1.26 / 1.24 | -15.9 / -30.9 |
| SI 1 (diag) week ('with', 15, ('tr', 0.3)) | gross-positive, cost-negative pre-2023 | 440 | 8.9 | -45.5 | -26.2 | 54.4 | 0.07 / -0.35 / -0.20 | 139.1 / 84.7 |
| SI 2 (diag) week ('fade', 15, ('b1', 0.3)) | gross-positive, cost-negative pre-2023 | 440 | 6.6 | -38.6 | -22.5 | 45.2 | 0.06 / -0.36 / -0.21 | 75.1 / 31.8 |
| SI 3 (diag) week ('with', 15, ('tr', 0.2)) | negative pre-2023 | 440 | -7.3 | -61.7 | -42.4 | 54.4 | -0.10 / -0.87 / -0.59 | 24.3 / -30.1 |
| HG 1 (diag) week ('fade', 15, ('tr', 0.3)) | gross-positive, cost-negative pre-2023 | 414 | 1.8 | -27.6 | -19.5 | 29.4 | 0.03 / -0.38 / -0.26 | 80.9 / 51.6 |
| HG 2 (diag) week ('fade', 15, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 414 | 2.6 | -26.7 | -18.7 | 29.4 | 0.05 / -0.52 / -0.36 | 62.1 / 32.8 |
| HG 3 (diag) week ('fade', 15, ('b1', 0.3)) | gross-positive, cost-negative pre-2023 | 414 | 4.8 | -20.6 | -13.6 | 25.5 | 0.09 / -0.27 / -0.17 | 71.4 / 46.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00); CL: 3 cells pass the clean rule against a replicate mean of 1.1 (p(count) = 0.10, p(top) = 0.40); ES: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00); GC: 3 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.12, p(top) = 0.40); HG: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); HO: 1 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.87, p(top) = 0.20); NQ: 0 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 1.00); RTY: 3 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.12, p(top) = 0.34); SI: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 10 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (RTY week ('fade', 15, ('b1', 0.3))); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 2; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 6, 'negative pre-2023': 2, 'gross-positive, cost-negative pre-2023': 2}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q37.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q37/ (`Q37_CO_all_selected_scored.csv`).

DONE Q37
