# REPORT Q7A - Q7A: B4 grid on FX (6E, 6J, 6B, 6A, 6C)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 1 selected cells (+15 diagnostic) scored on 5 instruments; best non-diagnostic all-in additive uplift at 20% share +0.08; best pair-window standalone Sharpe +0.65.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: fade a bar close that crosses from inside to outside session VWAP +- k sigma (sigma = volume-weighted std of typical price about the session VWAP; anchor = globex 18:00 ET or the instrument RTH open). Stop s x sigma from entry, target = VWAP level at the signal (or halfway), time stop 60/180 min, flat 16:55.
- Instruments: 6E, 6J, 6B, 6A, 6C. Grid: 192 cells per instrument = 4 bar sizes x 3 band widths x 2 anchors x 2 stops x 2 targets x 2 time stops.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6A    |     192 |        184 |         0 |              -1.591 |                0 |          0 |            3 |
| 6B    |     192 |        184 |         0 |              -1.453 |                0 |          0 |            3 |
| 6C    |     192 |        192 |         0 |              -0.854 |                0 |          0 |            3 |
| 6E    |     192 |        184 |         0 |               0.42  |                2 |          0 |            3 |
| 6J    |     192 |        184 |         1 |               0.421 |                2 |          1 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| 6E    |     100 |                    0 |             0.4  |               3 |        1   |                     nan     |            0.522 |           0.962 |   nan    |     nan     |                1.036 |
| 6J    |     100 |                    1 |             0.1  |               1 |        0.1 |                       0.252 |            0.605 |           0.974 |     0.08 |       0.252 |                0.974 |
| 6B    |     100 |                    0 |             0.02 |               1 |        1   |                     nan     |            0.683 |           0.895 |   nan    |     nan     |                0.895 |
| 6A    |     100 |                    0 |             0    |               0 |        1   |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| 6C    |     100 |                    0 |             0.01 |               1 |        1   |                     nan     |            1.118 |           1.118 |   nan    |     nan     |                1.118 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m | 80 | 2 | 0.42 | 1.05 | -0.11 | -1.18 / 0.18 | 0.03 / -0.26 / -0.17 | -0.18 | 0.29 | 0.98 | -0.25 | 0.00 | 124 | diag |
| 6E 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 79 | 1 | 0.28 | 1.09 | -0.12 | -0.58 / 0.22 | -0.03 / -0.20 / -0.05 | -0.16 | 0.26 | 0.95 | -0.25 | 0.00 | 122 | diag |
| 6E 3 (diag) | 15m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | 462 | 1 | -0.02 | 1.46 | -0.34 | -0.83 / -1.42 | -0.03 / -0.13 / -0.19 | -0.25 | 0.61 | 1.00 | -0.25 | 0.00 | 783 | diag |
| 6J 1 | 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 119 | 2 | 0.25 | 0.35 | 0.65 | 1.58 / -0.41 | 0.01 / 0.54 / -0.00 | -0.06 | 0.64 | 1.00 | -0.11 | 0.50 | 214 | NO |
| 6J 2 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 118 | 1 | 0.42 | 0.88 | 0.58 | 1.01 / -0.39 | 0.05 / 0.14 / 0.10 | -0.06 | 0.57 | 1.00 | -0.10 | 0.50 | 212 | diag |
| 6J 3 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 62 | 1 | 0.20 | 0.69 | 0.27 | 0.47 / 0.13 | 0.00 / 0.15 / 0.00 | -0.09 | -0.20 | 1.00 | -0.15 | 0.17 | 106 | diag |
| 6J 4 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 62 | 1 | 0.15 | 0.63 | 0.13 | 0.08 / -0.18 | -0.00 / 0.12 / 0.04 | -0.11 | -0.23 | 1.00 | -0.15 | 0.17 | 106 | diag |
| 6B 1 (diag) | 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 97 | 0 | -1.45 | -0.20 | -1.38 | -1.29 / -0.61 | -0.31 / 0.13 / -0.32 | -0.41 | 0.43 | 0.97 | -0.45 | 0.00 | 151 | diag |
| 6B 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 94 | 0 | -1.64 | 0.11 | -1.27 | -0.42 / -0.46 | -0.35 / 0.28 / -0.17 | -0.37 | 0.35 | 0.82 | -0.42 | 0.00 | 148 | diag |
| 6B 3 (diag) | 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | 234 | 0 | -1.70 | -0.06 | -2.03 | -2.68 / -1.91 | -0.36 / -0.31 / -0.40 | -0.61 | 0.23 | 1.00 | -0.56 | 0.00 | 382 | diag |
| 6A 1 (diag) | 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | 231 | 0 | -1.59 | 0.10 | -1.79 | -2.22 / 0.34 | -0.34 / -0.54 / -0.35 | -0.74 | -0.06 | 0.18 | -0.58 | 0.00 | 396 | diag |
| 6A 2 (diag) | 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | 81 | 0 | -1.63 | 0.03 | -1.60 | -1.65 / -1.17 | -0.30 / -0.64 / -0.26 | -0.60 | -0.35 | 0.92 | -0.55 | 0.00 | 145 | diag |
| 6A 3 (diag) | 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | 395 | 0 | -1.95 | -0.10 | -2.57 | -3.56 / -0.19 | -0.39 / -0.99 / -0.52 | -0.94 | -0.28 | 0.04 | -0.72 | 0.00 | 694 | diag |
| 6C 1 (diag) | 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | 188 | 0 | -0.85 | 0.39 | -1.09 | -1.39 / -2.31 | -0.19 / -0.52 / -0.07 | -0.44 | 0.09 | 1.00 | -0.40 | 0.00 | 282 | diag |
| 6C 2 (diag) | 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | 230 | 0 | -1.02 | 0.60 | -0.71 | 0.09 / -2.49 | -0.22 / -0.41 / 0.27 | -0.36 | 0.04 | 1.00 | -0.30 | 0.00 | 366 | diag |
| 6C 3 (diag) | 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | 196 | 0 | -1.07 | 0.55 | -1.12 | -1.18 / -2.27 | -0.25 / -0.23 / -0.16 | -0.46 | 0.15 | 1.00 | -0.39 | 0.00 | 292 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 1 |
| diagnostic cells read | 15 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 4 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 11 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6A 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | clean | -1.55 | -1.74 | -182596 | -144317 | 1388639 | -258751 | -1.00 | 33.3 | 1.16 | -82054 | 355070 | -88880 |
| 6A 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | H1 | -3.54 | -3.27 | -162948 | -139698 | 749920 | -166991 | -0.94 | 42.9 | 2.19 | -79093 | 185696 | -81254 |
| 6A 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | H2 | -0.82 | -1.14 | -183028 | -156535 | 758018 | -200419 | -0.45 | 41.7 | 2.04 | -102970 | 221312 | -105652 |
| 6A 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | all | -1.60 | -1.86 | -183506 | -149917 | 2591539 | -258751 | -0.94 | 36.9 | 1.52 | -86613 | 355070 | -105652 |
| 6B 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | clean | -1.63 | -1.80 | -175483 | -142567 | 1619932 | -288354 | -0.91 | 35.2 | 1.11 | -97040 | 369033 | -139545 |
| 6B 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | H1 | 2.39 | 4.81 | -37866 | -25244 | 67501 | -67501 | 3.56 | 7.1 | 3.10 | -73099 | 151713 | -78287 |
| 6B 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | H2 | -1.81 | -1.97 | -119757 | -88238 | 581343 | -165452 | -0.65 | 41.7 | 2.13 | -81997 | 225014 | -86579 |
| 6B 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | all | -1.27 | -1.44 | -161862 | -125141 | 1778901 | -288354 | -0.91 | 32.1 | 1.62 | -91614 | 369033 | -139545 |
| 6C 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m (diag) | clean | -1.05 | -1.35 | -153003 | -125626 | 960221 | -187999 | -1.00 | 54.3 | 1.24 | -94460 | 286241 | -110700 |
| 6C 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m (diag) | H1 | -2.21 | -2.59 | -92676 | -82861 | 461932 | -102713 | -0.79 | 60.7 | 2.41 | -89006 | 168809 | -89014 |
| 6C 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m (diag) | H2 | 1.98 | 4.37 | -52709 | -46692 | 125447 | -59785 | 3.20 | 27.8 | 2.56 | -80635 | 208080 | -81605 |
| 6C 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m (diag) | all | -0.71 | -0.94 | -136972 | -109352 | 1359260 | -187999 | -0.68 | 50.0 | 1.71 | -91928 | 286241 | -110700 |
| 6E 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m (diag) | clean | 0.47 | 0.69 | -154313 | -111503 | 587563 | -270257 | 0.73 | 22.9 | 1.49 | -87744 | 324338 | -135925 |
| 6E 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m (diag) | H1 | -1.29 | -1.44 | -137604 | -105868 | 221416 | -168577 | -1.00 | 21.4 | 2.57 | -77610 | 158959 | -78287 |
| 6E 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m (diag) | H2 | -1.14 | -1.31 | -157616 | -144092 | 619522 | -158320 | -0.59 | 25.0 | 2.13 | -92782 | 223470 | -102103 |
| 6E 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m (diag) | all | -0.11 | -0.15 | -161825 | -128750 | 779641 | -270257 | -0.21 | 23.2 | 1.80 | -87813 | 324338 | -135925 |
| 6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | clean | 0.25 | 0.33 | -164878 | -118603 | 795666 | -315174 | 0.29 | 23.8 | 1.47 | -95637 | 366335 | -144909 |
| 6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | H1 | 3.32 | 7.94 | -64923 | -53250 | 109006 | -72436 | 5.41 | 17.9 | 3.37 | -78060 | 128611 | -80329 |
| 6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | H2 | 0.14 | 0.18 | -95681 | -80008 | 342796 | -96827 | 0.08 | 25.0 | 2.29 | -90501 | 212782 | -101890 |
| 6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | all | 0.65 | 0.89 | -140119 | -103303 | 795666 | -315174 | 1.06 | 23.2 | 1.93 | -92795 | 366335 | -144909 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| 6E 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m (diag) | -31.8 | -67.7 | 12.3 | 6.3 | -69.0 / 11.9 | 30.0 / 30.0 | NO |
| 6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | -20.5 | -84.0 | 1.6 | -16.2 | -85.5 / -2.8 | 24.7 / 29.1 | NO |
| 6B 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m (diag) | -48.0 | -74.3 | 2.6 | -17.6 | -75.7 / -9.5 | 30.0 / 38.7 | NO |
| 6A 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m (diag) | -57.2 | -23.9 | 5.2 | -23.2 | 0.7 / 11.6 | 24.3 / 26.1 | NO |
| 6C 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m (diag) | -40.3 | -26.4 | 3.7 | 14.5 | -27.4 / -1.5 | 8.1 / 8.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| 6E 1 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=60m | positive pre-2023 | 450 | 46.8 | 32.8 | 31.8 | 14.0 | 1.47 / 1.05 / 1.02 | 22.0 / 7.4 |
| 6E 2 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | positive pre-2023 | 449 | 49.4 | 36.0 | 35.1 | 13.4 | 1.48 / 1.09 / 1.07 | 16.9 / 2.9 |
| 6E 3 (diag) 15m VWAPband k=2.0 rth stop=2.0sd tgt=vwap time=180m | positive pre-2023 | 2513 | 46.7 | 32.1 | 31.1 | 14.6 | 2.10 / 1.46 / 1.41 | 14.1 / -0.9 |
| 6J 1 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | positive pre-2023 | 793 | 21.0 | 7.6 | 3.0 | 13.5 | 0.96 / 0.35 / 0.14 | 16.9 / 3.5 |
| 6J 2 (diag) 15m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | positive pre-2023 | 782 | 50.3 | 35.6 | 30.6 | 14.7 | 1.22 / 0.88 / 0.76 | 22.6 / 7.5 |
| 6J 3 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | positive pre-2023 | 493 | 53.0 | 38.1 | 33.1 | 14.9 | 0.94 / 0.69 / 0.60 | 19.3 / 4.2 |
| 6J 4 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | positive pre-2023 | 498 | 46.6 | 31.3 | 26.2 | 15.3 | 0.92 / 0.63 / 0.53 | 18.0 / 2.8 |
| 6B 1 (diag) 30m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 475 | 11.2 | -3.1 | -4.3 | 14.2 | 0.71 / -0.20 / -0.28 | -0.6 / -15.5 |
| 6B 2 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | positive pre-2023 | 468 | 15.6 | 2.0 | 0.7 | 13.6 | 0.83 / 0.11 / 0.04 | -5.8 / -20.2 |
| 6B 3 (diag) 10m VWAPband k=2.5 rth stop=1.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 1128 | 13.2 | -0.9 | -2.1 | 14.1 | 0.85 / -0.06 / -0.14 | 3.0 / -11.5 |
| 6A 1 (diag) 30m VWAPband k=2.5 globex stop=2.0sd tgt=vwap time=180m | positive pre-2023 | 1045 | 24.1 | 2.4 | -0.8 | 21.7 | 1.02 / 0.10 / -0.04 | 7.9 / -14.4 |
| 6A 2 (diag) 30m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=60m | positive pre-2023 | 435 | 22.8 | 0.5 | -3.3 | 22.3 | 0.81 / 0.03 / -0.11 | 2.8 / -20.1 |
| 6A 3 (diag) 15m VWAPband k=2.5 globex stop=2.0sd tgt=half time=180m | gross-positive, cost-negative pre-2023 | 1715 | 17.7 | -1.2 | -4.0 | 19.0 | 1.37 / -0.10 / -0.32 | 6.0 / -13.3 |
| 6C 1 (diag) 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m | positive pre-2023 | 879 | 16.5 | 5.0 | 3.9 | 11.5 | 1.27 / 0.39 / 0.31 | 6.2 / -5.2 |
| 6C 2 (diag) 10m VWAPband k=2.5 rth stop=2.0sd tgt=vwap time=180m | positive pre-2023 | 1159 | 24.5 | 11.8 | 10.7 | 12.7 | 1.22 / 0.60 / 0.55 | 5.3 / -7.7 |
| 6C 3 (diag) 15m VWAPband k=2.5 rth stop=1.0sd tgt=vwap time=180m | positive pre-2023 | 893 | 24.1 | 11.0 | 9.8 | 13.1 | 1.18 / 0.55 / 0.49 | 5.9 / -7.4 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): 6A: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6B: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6C: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); 6E: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00); 6J: 1 cells pass the clean rule against a replicate mean of 0.1 (p(count) = 0.10, p(top) = 0.08).
- Of 1 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.08 (6J 15m VWAPband k=2.5 rth stop=2.0sd tgt=half time=180m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q7a.py (= ap_b4.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q7a/ (`Q7A_CO_all_selected_scored.csv`).

DONE Q7A
