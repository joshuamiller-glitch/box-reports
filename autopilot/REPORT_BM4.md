# REPORT BM4 - weekly reversal (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 9 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.10; best pair-window standalone Sharpe +0.95.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. weekly reversal. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          4 |         1 |               0.413 |                2 |          1 |            3 |
| CL    |       8 |          4 |         2 |               0.735 |                2 |          2 |            3 |
| ES    |       8 |          4 |         1 |               0.733 |                2 |          1 |            3 |
| GC    |       8 |          4 |         1 |               0.779 |                2 |          1 |            3 |
| NQ    |       8 |          4 |         1 |               0.542 |                2 |          1 |            3 |
| RTY   |       8 |          4 |         1 |               1.526 |                2 |          1 |            3 |
| YM    |       8 |          4 |         0 |               0.874 |                2 |          0 |            3 |
| ZN    |       8 |          4 |         2 |               0.46  |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.9   |               3 |      0.625 |                       0.135 |            0.762 |           1.311 |    0.61  |       0.135 |                1.458 |
| NQ    |     200 |                    1 |            0.915 |               4 |      0.66  |                       0.542 |            0.822 |           1.465 |    0.48  |       0.542 |                1.578 |
| RTY   |     200 |                    1 |            0.88  |               4 |      0.635 |                       1.072 |            0.737 |           1.481 |    0.08  |       1.072 |                1.585 |
| YM    |     200 |                    0 |            0.95  |               3 |      1     |                     nan     |            0.742 |           1.362 |  nan     |     nan     |                1.566 |
| GC    |     200 |                    1 |            0.88  |               4 |      0.625 |                       0.779 |            0.759 |           1.482 |    0.26  |       0.779 |                1.498 |
| CL    |     200 |                    2 |            0.805 |               3 |      0.2   |                       0.691 |            0.787 |           1.382 |    0.35  |       0.735 |                1.454 |
| ZN    |     200 |                    2 |            0.31  |               2 |      0.03  |                       0.261 |            0.641 |           1.212 |    0.255 |       0.415 |                1.248 |
| BTC   |     200 |                    1 |            1.04  |               3 |      0.695 |                       0.413 |            0.769 |           1.29  |    0.605 |       0.413 |                1.669 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | prior-week ret z>=0.0 dir=with hold=2d from Monday open | 104 | 2 | 0.14 | -0.93 | 0.14 | 0.19 / 1.58 | 0.02 / 0.28 / -0.33 | -0.03 | -0.55 | 0.55 | -0.21 | 0.00 | 167 | NO |
| ES 2 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 54 | 2 | 0.73 | 0.07 | 0.24 | -0.85 / 1.28 | 0.11 / 0.04 / -0.28 | 0.00 | 0.17 | 0.72 | -0.15 | 0.00 | 79 S | diag |
| ES 3 (diag) | prior-week ret z>=0.0 dir=against hold=1d from Monday open | 104 | 1 | 0.28 | -0.18 | -0.25 | -1.09 / 1.20 | 0.05 / -0.34 / -0.24 | -0.09 | 0.60 | 0.45 | -0.25 | 0.00 | 167 | diag |
| ES 4 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 53 | 2 | 0.13 | 0.85 | 0.23 | 0.31 / 1.36 | 0.00 / 0.14 / 0.01 | 0.01 | 0.19 | 0.73 | -0.16 | 0.00 | 78 S | diag |
| NQ 1 | prior-week ret z>=0.0 dir=with hold=2d from Monday open | 104 | 2 | 0.54 | -0.78 | -0.11 | -0.76 / 1.45 | 0.11 / 0.10 / -0.64 | -0.06 | -0.31 | 0.36 | -0.30 | 0.00 | 167 | NO |
| NQ 2 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 50 | 2 | 0.47 | 0.13 | -0.29 | -1.47 / 1.23 | 0.03 / -0.24 / -0.42 | -0.11 | 0.65 | 0.40 | -0.29 | 0.00 | 77 S | diag |
| NQ 3 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 50 | 2 | 0.23 | 0.61 | 0.10 | -0.07 / 1.57 | -0.01 / -0.26 / 0.16 | -0.02 | 0.32 | 0.61 | -0.22 | 0.00 | 77 S | diag |
| NQ 4 (diag) | prior-week ret z>=0.0 dir=with hold=1d from Monday open | 104 | 1 | 0.05 | 0.31 | 0.15 | 0.26 / 1.47 | -0.03 / 0.19 / -0.07 | -0.02 | -0.63 | 0.61 | -0.22 | 0.00 | 167 | diag |
| RTY 1 | prior-week ret z>=0.0 dir=against hold=1d from Monday open | 104 | 2 | 1.07 | -0.25 | 0.95 | 0.61 / 1.41 | 0.14 / 0.28 / -0.08 | 0.09 | 0.26 | 0.98 | -0.09 | 0.00 | 167 | NO |
| RTY 2 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 44 | 2 | 1.53 | 1.01 | 0.55 | -1.05 / 1.57 | 0.28 / -0.23 / -0.22 | 0.09 | -0.30 | 0.85 | -0.09 | 0.50 | 67 S | diag |
| RTY 3 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 45 | 2 | 1.27 | 0.50 | 0.47 | -0.81 / 1.26 | 0.18 / -0.21 / -0.23 | 0.03 | -0.52 | 0.87 | -0.13 | 0.50 | 68 S | diag |
| RTY 4 (diag) | prior-week ret z>=0.0 dir=against hold=2d from Monday open | 104 | 1 | 0.74 | 0.40 | 0.76 | 0.71 / 1.38 | 0.11 / 0.42 / -0.08 | 0.10 | 0.25 | 0.95 | -0.08 | 0.00 | 167 | diag |
| YM 1 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 47 | 2 | 0.87 | 0.37 | 0.65 | 0.18 / 1.11 | 0.15 / 0.33 / -0.14 | 0.10 | 0.27 | 0.93 | -0.05 | 0.50 | 67 S | diag |
| YM 2 (diag) | prior-week ret z>=0.5 dir=with hold=2d from Monday open | 46 | 2 | 0.62 | -1.08 | 0.05 | -0.74 / 1.46 | 0.04 / -0.45 / -0.18 | -0.09 | -0.32 | 0.50 | -0.26 | 0.00 | 66 S | diag |
| YM 3 (diag) | prior-week ret z>=0.0 dir=against hold=1d from Monday open | 104 | 1 | 0.17 | -0.20 | 0.43 | 0.80 / 1.38 | 0.04 / 0.56 / -0.15 | 0.07 | -0.17 | 0.80 | -0.10 | 0.00 | 167 | diag |
| GC 1 | prior-week ret z>=0.0 dir=against hold=1d from Monday open | 104 | 2 | 0.78 | -0.06 | -0.30 | -1.00 / 1.32 | 0.10 / -0.67 / -0.81 | -0.21 | -0.15 | 0.36 | -0.49 | 0.00 | 167 | NO |
| GC 2 (diag) | prior-week ret z>=0.5 dir=with hold=2d from Monday open | 46 | 1 | 0.05 | -0.51 | 0.18 | 0.29 / 1.50 | 0.01 / -1.02 / 0.55 | -0.04 | 0.23 | 0.60 | -0.40 | 0.00 | 69 S | diag |
| GC 3 (diag) | prior-week ret z>=0.0 dir=with hold=2d from Monday open | 104 | 1 | -0.00 | -0.25 | 0.05 | 0.08 / 1.60 | 0.02 / -0.65 / -0.20 | -0.11 | 0.23 | 0.56 | -0.49 | 0.00 | 167 | diag |
| GC 4 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 46 | 1 | -0.02 | 0.15 | 0.13 | 0.27 / 1.41 | -0.03 / -0.13 / -0.14 | -0.05 | -0.31 | 0.65 | -0.29 | 0.00 | 69 S | diag |
| CL 1 | prior-week ret z>=0.0 dir=with hold=2d from Monday open | 104 | 2 | 0.73 | -0.38 | 0.13 | -0.26 / 1.36 | 0.06 / -0.01 / -0.57 | -0.11 | -0.12 | 0.57 | -0.37 | 0.00 | 167 | NO |
| CL 2 | prior-week ret z>=0.0 dir=with hold=1d from Monday open | 104 | 2 | 0.65 | -0.15 | 0.15 | -0.15 / 1.30 | 0.07 / -0.09 / -0.49 | -0.11 | 0.29 | 0.69 | -0.43 | 0.00 | 167 | NO |
| CL 3 (diag) | prior-week ret z>=0.5 dir=with hold=2d from Monday open | 45 | 1 | 0.25 | -0.21 | 0.06 | -0.04 / 1.61 | -0.01 / 0.31 / -0.75 | -0.18 | -0.64 | 0.49 | -0.56 | 0.00 | 68 S | diag |
| CL 4 (diag) | prior-week ret z>=0.5 dir=with hold=1d from Monday open | 44 | 2 | 0.20 | -0.14 | -0.36 | -0.67 / 1.38 | -0.00 / -0.12 / -1.35 | -0.41 | 0.40 | 0.33 | -1.00 | 0.00 | 67 S | diag |
| CL 5 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 45 | 1 | -0.41 | 0.09 | -0.13 | -0.00 / 1.31 | -0.08 / -0.41 / -0.14 | -0.13 | 0.65 | 0.41 | -0.42 | 0.00 | 68 S | diag |
| ZN 1 | prior-week ret z>=0.0 dir=against hold=1d from Monday open | 103 | 2 | 0.41 | -0.45 | -0.23 | -2.11 / 0.25 | 0.09 / -0.33 / -0.19 | -0.19 | 0.39 | 0.86 | -0.19 | 0.00 | 166 | NO |
| ZN 2 | prior-week ret z>=0.0 dir=against hold=2d from Monday open | 103 | 2 | 0.11 | -0.02 | -0.21 | -0.93 / 1.00 | 0.00 / -0.23 / -0.08 | -0.13 | 0.25 | 0.66 | -0.21 | 0.00 | 166 | NO |
| ZN 3 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 48 | 1 | 0.46 | -0.16 | 0.23 | -0.57 / 1.02 | 0.08 / -0.20 / 0.00 | -0.02 | 0.38 | 0.84 | -0.13 | 0.00 | 68 S | diag |
| ZN 4 (diag) | prior-week ret z>=0.5 dir=against hold=1d from Monday open | 48 | 2 | 0.25 | -0.17 | -0.05 | -1.14 / 1.10 | 0.04 / -0.25 / -0.05 | -0.10 | 0.50 | 0.83 | -0.17 | 0.00 | 68 S | diag |
| ZN 5 (diag) | prior-week ret z>=0.5 dir=with hold=2d from Monday open | 48 | 0 | -1.05 | -0.48 | -0.86 | -0.38 / 0.95 | -0.24 / 0.12 / -0.11 | -0.22 | -0.32 | 0.19 | -0.34 | 0.00 | 68 S | diag |
| BTC 1 | prior-week ret z>=0.0 dir=with hold=1d from Monday open | 103 | 2 | 0.41 | -0.06 | 0.19 | -0.46 / 1.55 | 0.07 / -0.19 / -0.02 | 0.01 | -0.25 | 0.56 | -0.16 | 0.00 | 145 | NO |
| BTC 2 (diag) | prior-week ret z>=0.5 dir=against hold=2d from Monday open | 37 | 1 | 0.39 | 0.59 | 0.34 | 0.24 / 1.71 | 0.02 / 0.23 / 0.02 | 0.03 | 0.20 | 0.71 | -0.15 | 1.00 | 55 S | diag |
| BTC 3 (diag) | prior-week ret z>=0.5 dir=with hold=1d from Monday open | 38 | 1 | 0.32 | -0.19 | 0.11 | -0.52 / 1.26 | 0.07 / -0.32 / -0.02 | 0.00 | -0.33 | 0.60 | -0.16 | 0.50 | 56 S | diag |
| BTC 4 (diag) | prior-week ret z>=0.0 dir=against hold=2d from Monday open | 103 | 1 | 0.05 | -0.32 | -0.08 | -0.32 / 1.31 | 0.00 / -0.17 / -0.01 | -0.02 | 0.13 | 0.48 | -0.20 | 0.00 | 145 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 9 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 12 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 2 |
| worst-decile corr <= +0.30 | 25 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 18 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC prior-week ret z>=0.0 dir=with hold=1d from Monday open | clean | 0.42 | 0.70 | -125653 | -102849 | 448418 | -142647 | 0.86 | 49.5 | 1.53 | -88519 | 243699 | -104563 |
| BTC prior-week ret z>=0.0 dir=with hold=1d from Monday open | H1 | -0.87 | -1.09 | -103811 | -93785 | 211711 | -110752 | -0.68 | 46.4 | 2.64 | -78756 | 169247 | -81334 |
| BTC prior-week ret z>=0.0 dir=with hold=1d from Monday open | H2 | -0.01 | -0.01 | -89351 | -58406 | 141742 | -131740 | -0.01 | 16.7 | 2.47 | -82070 | 217425 | -82524 |
| BTC prior-week ret z>=0.0 dir=with hold=1d from Monday open | all | 0.19 | 0.30 | -121475 | -96783 | 672633 | -142647 | 0.36 | 42.3 | 1.91 | -86287 | 243699 | -104563 |
| CL prior-week ret z>=0.0 dir=with hold=1d from Monday open | clean | 0.58 | 1.01 | -102641 | -91746 | 314876 | -121555 | 1.66 | 47.6 | 1.53 | -85880 | 285763 | -99596 |
| CL prior-week ret z>=0.0 dir=with hold=1d from Monday open | H1 | -0.48 | -0.64 | -55923 | -49212 | 244343 | -72919 | -0.21 | 50.0 | 2.74 | -77865 | 160635 | -82412 |
| CL prior-week ret z>=0.0 dir=with hold=1d from Monday open | H2 | -0.15 | -0.17 | -532862 | -330608 | 1164953 | -918022 | -0.12 | 47.2 | 1.99 | -132239 | 216680 | -173227 |
| CL prior-week ret z>=0.0 dir=with hold=1d from Monday open | all | 0.15 | 0.18 | -208947 | -148502 | 1365811 | -918022 | 0.25 | 48.2 | 1.81 | -96186 | 287423 | -173227 |
| ES prior-week ret z>=0.0 dir=with hold=2d from Monday open | clean | 0.10 | 0.15 | -122316 | -102910 | 610396 | -152769 | 0.15 | 43.8 | 1.48 | -85367 | 237318 | -93446 |
| ES prior-week ret z>=0.0 dir=with hold=2d from Monday open | H1 | 1.42 | 2.22 | -115504 | -99777 | 172212 | -156976 | 1.95 | 39.3 | 3.11 | -63116 | 186155 | -66348 |
| ES prior-week ret z>=0.0 dir=with hold=2d from Monday open | H2 | -0.48 | -0.73 | -135339 | -128577 | 314371 | -145556 | -0.65 | 63.9 | 2.15 | -88916 | 224379 | -93064 |
| ES prior-week ret z>=0.0 dir=with hold=2d from Monday open | all | 0.14 | 0.21 | -134938 | -115151 | 610396 | -156976 | 0.36 | 47.6 | 1.88 | -85652 | 237318 | -93446 |
| GC prior-week ret z>=0.0 dir=against hold=1d from Monday open | clean | 0.65 | 1.05 | -134154 | -102002 | 359202 | -193010 | 1.66 | 54.3 | 1.56 | -92200 | 268052 | -104551 |
| GC prior-week ret z>=0.0 dir=against hold=1d from Monday open | H1 | -0.28 | -0.44 | -303118 | -272102 | 1288226 | -346566 | -0.15 | 60.7 | 2.16 | -112959 | 222681 | -130221 |
| GC prior-week ret z>=0.0 dir=against hold=1d from Monday open | H2 | -1.73 | -2.03 | -271573 | -254809 | 1433094 | -289429 | -0.79 | 55.6 | 1.68 | -99868 | 213923 | -102734 |
| GC prior-week ret z>=0.0 dir=against hold=1d from Monday open | all | -0.30 | -0.42 | -250764 | -204867 | 1481644 | -346566 | -0.49 | 56.0 | 1.70 | -99723 | 268052 | -130221 |
| NQ prior-week ret z>=0.0 dir=with hold=2d from Monday open | clean | 0.53 | 0.83 | -114867 | -98594 | 400827 | -165065 | 1.21 | 43.8 | 1.57 | -83063 | 216858 | -90400 |
| NQ prior-week ret z>=0.0 dir=with hold=2d from Monday open | H1 | 0.41 | 0.55 | -159682 | -133796 | 260420 | -170479 | 0.40 | 42.9 | 2.93 | -67756 | 169336 | -67802 |
| NQ prior-week ret z>=0.0 dir=with hold=2d from Monday open | H2 | -1.29 | -1.55 | -320914 | -259941 | 1257655 | -365960 | -0.62 | 58.3 | 1.84 | -95015 | 254611 | -95769 |
| NQ prior-week ret z>=0.0 dir=with hold=2d from Monday open | all | -0.11 | -0.14 | -197383 | -151214 | 1257655 | -365960 | -0.15 | 47.0 | 1.84 | -86424 | 254611 | -95769 |
| RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open | clean | 1.19 | 1.91 | -113949 | -98508 | 341647 | -188445 | 3.14 | 40.0 | 1.60 | -89735 | 305142 | -119563 |
| RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open | H1 | 1.66 | 3.03 | -94044 | -82112 | 225696 | -118753 | 1.78 | 39.3 | 3.11 | -87517 | 135151 | -89937 |
| RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open | H2 | -0.05 | -0.09 | -130949 | -108616 | 615137 | -163103 | -0.03 | 63.9 | 2.41 | -86161 | 223428 | -87692 |
| RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open | all | 0.95 | 1.57 | -118331 | -100361 | 615137 | -188445 | 2.36 | 45.2 | 2.00 | -89462 | 305142 | -119563 |
| YM prior-week ret z>=0.5 dir=against hold=1d from Monday open (diag) | clean | 0.88 | 1.56 | -123838 | -86826 | 368819 | -223011 | 2.17 | 15.2 | 1.61 | -81218 | 281297 | -87345 |
| YM prior-week ret z>=0.5 dir=against hold=1d from Monday open (diag) | H1 | 2.10 | 4.50 | -71220 | -47480 | 104071 | -104071 | 3.52 | 7.1 | 3.16 | -77610 | 138824 | -78287 |
| YM prior-week ret z>=0.5 dir=against hold=1d from Monday open (diag) | H2 | -0.99 | -1.28 | -170111 | -109799 | 456544 | -219304 | -0.61 | 22.2 | 2.34 | -93181 | 217425 | -103837 |
| YM prior-week ret z>=0.5 dir=against hold=1d from Monday open (diag) | all | 0.65 | 1.07 | -131925 | -90732 | 456544 | -223011 | 1.94 | 15.5 | 2.01 | -83580 | 281297 | -103837 |
| ZN prior-week ret z>=0.0 dir=against hold=1d from Monday open | clean | 0.43 | 0.73 | -110324 | -91797 | 382535 | -150861 | 1.02 | 49.5 | 1.55 | -85404 | 316062 | -112046 |
| ZN prior-week ret z>=0.0 dir=against hold=1d from Monday open | H1 | -2.95 | -3.43 | -54239 | -52017 | 427321 | -54239 | -0.85 | 75.0 | 2.50 | -85126 | 158934 | -87136 |
| ZN prior-week ret z>=0.0 dir=against hold=1d from Monday open | H2 | -1.60 | -2.06 | -77561 | -69232 | 542462 | -87557 | -0.59 | 63.9 | 2.29 | -86582 | 229125 | -87169 |
| ZN prior-week ret z>=0.0 dir=against hold=1d from Monday open | all | -0.23 | -0.36 | -99773 | -82657 | 894544 | -150861 | -0.33 | 57.1 | 1.86 | -87875 | 316062 | -112046 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-week ret z>=0.0 dir=with hold=2d from Monday open | -27.6 | 4.3 | 11.8 | 27.4 | 3.5 / 11.6 | 45.6 / 48.8 | NO |
| NQ prior-week ret z>=0.0 dir=with hold=2d from Monday open | -32.1 | -4.3 | 8.5 | -29.1 | -5.1 / 15.9 | 48.7 / 48.2 | NO |
| RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open | -14.1 | -38.0 | 9.0 | 9.8 | -39.0 / 7.5 | 7.7 / 10.9 | NO |
| YM prior-week ret z>=0.5 dir=against hold=1d from Monday open (diag) | -20.3 | -11.5 | 20.7 | 23.5 | 15.3 / 23.6 | 30.0 / 30.0 | NO |
| GC prior-week ret z>=0.0 dir=against hold=1d from Monday open | -38.0 | -60.8 | -21.7 | -14.3 | -16.3 / 1.4 | -69.5 / -64.4 | NO |
| CL prior-week ret z>=0.0 dir=with hold=1d from Monday open | -26.3 | -224.9 | -13.0 | -34.2 | -2.5 / 14.1 | 22.1 / 29.5 | NO |
| ZN prior-week ret z>=0.0 dir=against hold=1d from Monday open | -33.2 | -24.3 | 12.4 | 10.7 | -25.3 / 16.4 | 13.0 / 15.5 | NO |
| BTC prior-week ret z>=0.0 dir=with hold=1d from Monday open | -27.4 | -14.4 | 12.9 | 26.1 | -15.3 / 6.2 | 24.2 / 27.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 prior-week ret z>=0.0 dir=with hold=2d from Monday open | negative pre-2023 | 538 | -195.8 | -225.2 | -210.9 | 29.4 | -0.81 / -0.93 / -0.87 | 66.2 / 36.9 |
| ES 2 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | positive pre-2023 | 241 | 47.1 | 17.7 | 31.9 | 29.4 | 0.19 / 0.07 / 0.13 | 338.0 / 308.6 |
| ES 3 (diag) prior-week ret z>=0.0 dir=against hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 544 | 1.3 | -28.1 | -13.9 | 29.4 | 0.01 / -0.18 / -0.09 | 106.5 / 77.1 |
| ES 4 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | positive pre-2023 | 237 | 356.2 | 326.8 | 341.0 | 29.4 | 0.92 / 0.85 / 0.88 | 115.1 / 85.7 |
| NQ 1 prior-week ret z>=0.0 dir=with hold=2d from Monday open | negative pre-2023 | 538 | -296.1 | -310.4 | -301.8 | 14.4 | -0.75 / -0.78 / -0.76 | 384.5 / 370.2 |
| NQ 2 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | positive pre-2023 | 252 | 60.9 | 46.5 | 54.9 | 14.4 | 0.17 / 0.13 / 0.15 | 404.2 / 389.8 |
| NQ 3 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | positive pre-2023 | 247 | 399.5 | 385.1 | 393.5 | 14.4 | 0.63 / 0.61 / 0.62 | 257.0 / 242.6 |
| NQ 4 (diag) prior-week ret z>=0.0 dir=with hold=1d from Monday open | positive pre-2023 | 544 | 91.5 | 77.2 | 85.7 | 14.4 | 0.36 / 0.31 / 0.34 | 46.4 / 32.0 |
| RTY 1 prior-week ret z>=0.0 dir=against hold=1d from Monday open | negative pre-2023 | 310 | -22.4 | -36.7 | -34.5 | 14.4 | -0.14 / -0.25 / -0.24 | 177.0 / 162.6 |
| RTY 2 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | positive pre-2023 | 131 | 341.9 | 327.6 | 330.0 | 14.4 | 1.06 / 1.01 / 1.02 | 583.4 / 569.0 |
| RTY 3 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | positive pre-2023 | 134 | 117.6 | 103.3 | 105.7 | 14.4 | 0.56 / 0.50 / 0.51 | 308.2 / 293.9 |
| RTY 4 (diag) prior-week ret z>=0.0 dir=against hold=2d from Monday open | positive pre-2023 | 306 | 100.3 | 86.0 | 88.2 | 14.4 | 0.47 / 0.40 / 0.41 | 191.7 / 177.4 |
| YM 1 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | positive pre-2023 | 240 | 93.5 | 79.1 | 85.0 | 14.4 | 0.44 / 0.37 / 0.40 | 267.1 / 252.8 |
| YM 2 (diag) prior-week ret z>=0.5 dir=with hold=2d from Monday open | negative pre-2023 | 236 | -325.3 | -339.6 | -333.7 | 14.4 | -1.03 / -1.08 / -1.06 | 197.3 / 182.9 |
| YM 3 (diag) prior-week ret z>=0.0 dir=against hold=1d from Monday open | negative pre-2023 | 544 | -11.6 | -26.0 | -20.2 | 14.4 | -0.09 / -0.20 / -0.16 | 52.7 / 38.4 |
| GC 1 prior-week ret z>=0.0 dir=against hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 546 | 17.5 | -6.8 | 3.0 | 24.4 | 0.12 / -0.06 / 0.01 | 168.8 / 144.4 |
| GC 2 (diag) prior-week ret z>=0.5 dir=with hold=2d from Monday open | negative pre-2023 | 218 | -208.9 | -233.2 | -223.3 | 24.4 | -0.46 / -0.51 / -0.49 | 55.4 / 31.1 |
| GC 3 (diag) prior-week ret z>=0.0 dir=with hold=2d from Monday open | negative pre-2023 | 537 | -38.0 | -62.3 | -52.5 | 24.4 | -0.15 / -0.25 / -0.21 | 33.7 / 9.4 |
| GC 4 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | positive pre-2023 | 221 | 59.3 | 34.9 | 44.9 | 24.4 | 0.25 / 0.15 / 0.19 | 15.2 / -9.1 |
| CL 1 prior-week ret z>=0.0 dir=with hold=2d from Monday open | negative pre-2023 | 533 | -71.5 | -95.9 | -93.2 | 24.4 | -0.28 / -0.38 / -0.37 | 171.8 / 147.5 |
| CL 2 prior-week ret z>=0.0 dir=with hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 545 | 4.0 | -20.4 | -17.8 | 24.4 | 0.02 / -0.15 / -0.13 | 120.5 / 96.1 |
| CL 3 (diag) prior-week ret z>=0.5 dir=with hold=2d from Monday open | negative pre-2023 | 222 | -61.1 | -85.4 | -82.6 | 24.4 | -0.15 / -0.21 / -0.20 | 104.2 / 79.9 |
| CL 4 (diag) prior-week ret z>=0.5 dir=with hold=1d from Monday open | negative pre-2023 | 226 | -6.3 | -30.6 | -27.9 | 24.4 | -0.04 / -0.14 / -0.13 | 52.5 / 28.1 |
| CL 5 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | positive pre-2023 | 222 | 61.1 | 36.7 | 39.6 | 24.4 | 0.15 / 0.09 / 0.10 | -104.2 / -128.6 |
| ZN 1 prior-week ret z>=0.0 dir=against hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 542 | 18.2 | -17.4 | -22.5 | 35.6 | 0.47 / -0.45 / -0.59 | 53.4 / 17.8 |
| ZN 2 prior-week ret z>=0.0 dir=against hold=2d from Monday open | gross-positive, cost-negative pre-2023 | 536 | 34.1 | -1.5 | -6.7 | 35.6 | 0.51 / -0.02 / -0.10 | 38.4 / 2.8 |
| ZN 3 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | gross-positive, cost-negative pre-2023 | 222 | 18.2 | -17.5 | -22.5 | 35.6 | 0.16 / -0.16 / -0.20 | 90.5 / 54.9 |
| ZN 4 (diag) prior-week ret z>=0.5 dir=against hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 226 | 24.8 | -10.9 | -15.8 | 35.6 | 0.39 / -0.17 / -0.25 | 53.7 / 18.1 |
| ZN 5 (diag) prior-week ret z>=0.5 dir=with hold=2d from Monday open | negative pre-2023 | 222 | -18.2 | -53.8 | -58.8 | 35.6 | -0.16 / -0.48 / -0.53 | -90.5 / -126.1 |
| BTC 1 prior-week ret z>=0.0 dir=with hold=1d from Monday open | gross-positive, cost-negative pre-2023 | 79 | 44.3 | -10.1 | 22.4 | 54.4 | 0.06 / -0.06 / 0.01 | 619.4 / 565.1 |
| BTC 2 (diag) prior-week ret z>=0.5 dir=against hold=2d from Monday open | positive pre-2023 | 28 | 748.2 | 693.9 | 725.9 | 54.4 | 0.63 / 0.59 / 0.61 | 1316.9 / 1262.5 |
| BTC 3 (diag) prior-week ret z>=0.5 dir=with hold=1d from Monday open | negative pre-2023 | 28 | -88.4 | -142.8 | -110.7 | 54.4 | -0.12 / -0.19 / -0.14 | 881.6 / 827.2 |
| BTC 4 (diag) prior-week ret z>=0.0 dir=against hold=2d from Monday open | negative pre-2023 | 78 | -186.5 | -240.9 | -208.4 | 54.4 | -0.24 / -0.32 / -0.27 | 82.5 / 28.2 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 1 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.69, p(top) = 0.60); CL: 2 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.20, p(top) = 0.35); ES: 1 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.62, p(top) = 0.61); GC: 1 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.62, p(top) = 0.26); NQ: 1 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.66, p(top) = 0.48); RTY: 1 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 0.64, p(top) = 0.08); YM: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); ZN: 2 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.03, p(top) = 0.26).
- Of 9 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.10 (RTY prior-week ret z>=0.0 dir=against hold=1d from Monday open); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 5, 'negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_4.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm4/ (`BM4_CO_all_selected_scored.csv`).

DONE BM4
