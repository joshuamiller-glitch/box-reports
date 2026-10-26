# REPORT BI1 - same-half-hour return persistence (Heston-Korajczyk-Sadka) (BI batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 20 selected cells (+10 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.12; best pair-window standalone Sharpe +0.83.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BI', before the first run)
- Rule: see IDEAS_BI.md / PREREG_AUTOPILOT.md BATCH BI (frozen before the first run). same-half-hour return persistence (Heston-Korajczyk-Sadka)
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      52 |         52 |         1 |               0.69  |                2 |          1 |            3 |
| NQ    |      52 |         52 |         9 |               1.129 |                2 |          9 |            1 |
| RTY   |      52 |         52 |         4 |               0.688 |                2 |          4 |            3 |
| YM    |      52 |         52 |         6 |               1.121 |                2 |          6 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.365 |               3 |      0.32  |                       0.283 |            0.398 |           0.9   |    0.19  |       0.283 |                1.07  |
| NQ    |     200 |                    9 |            6.66  |              14 |      0.22  |                       0.619 |            0.676 |           0.919 |    0.645 |       1.129 |                1.792 |
| RTY   |     200 |                    4 |            1.23  |               6 |      0.04  |                       0.42  |            0.502 |           0.966 |    0.42  |       0.688 |                1.077 |
| YM    |     200 |                    6 |            1.475 |               6 |      0.005 |                       0.666 |            0.518 |           1.036 |    0.18  |       1.121 |                1.171 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | 479 | 2 | 0.28 | -1.41 | -0.44 | -1.45 / 0.33 | -0.02 / -0.64 / -0.20 | -0.28 | 0.51 | 0.90 | -0.33 | 0.00 | 765 | NO |
| ES 2 (diag) | slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | 510 | 1 | 0.69 | -0.72 | 0.50 | 0.34 / 0.23 | 0.08 / 0.06 / -0.11 | -0.10 | -0.02 | 1.00 | -0.16 | 0.00 | 818 | diag |
| ES 3 (diag) | slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | 469 | 1 | 0.63 | -1.64 | 0.37 | -0.18 / 0.37 | 0.07 / 0.14 / -0.05 | -0.04 | -0.50 | 0.99 | -0.08 | 0.00 | 760 | diag |
| ES 4 (diag) | slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | 511 | 1 | 0.26 | -1.17 | -0.30 | -1.11 / 0.38 | 0.03 / -0.29 / -0.58 | -0.27 | -0.38 | 0.95 | -0.33 | 0.00 | 818 | diag |
| NQ 1 | slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | 511 | 2 | 1.13 | -0.38 | 0.22 | -0.87 / 1.12 | 0.19 / -0.10 / -0.46 | -0.02 | -0.15 | 0.82 | -0.20 | 0.00 | 819 | NO |
| NQ 2 | slot 12:30 mean of prior 5d same-slot ret dir=with hold=30m | 427 | 2 | 0.89 | -1.06 | 0.27 | -0.52 / 1.32 | 0.10 / -0.30 / -0.11 | -0.05 | -0.33 | 0.78 | -0.21 | 0.00 | 686 | NO |
| NQ 3 | slot 11:30 mean of prior 5d same-slot ret dir=against hold=30m | 511 | 2 | 0.81 | -0.32 | 0.16 | -0.44 / 1.11 | 0.10 / -0.53 / -0.15 | -0.07 | 0.06 | 0.84 | -0.23 | 0.00 | 818 | NO |
| NQ 4 | slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | 480 | 2 | 0.73 | -0.49 | 0.35 | -0.05 / 1.24 | 0.09 / -0.07 / -0.07 | -0.01 | 0.60 | 0.86 | -0.17 | 0.00 | 772 | NO |
| NQ 5 | slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | 479 | 2 | 0.66 | -0.54 | 0.83 | 1.09 / 1.41 | 0.10 / 0.16 / 0.08 | 0.09 | -0.78 | 0.96 | -0.06 | 0.00 | 771 | NO |
| NQ 6 | slot 12:30 mean of prior 1d same-slot ret dir=with hold=30m | 487 | 2 | 0.58 | -0.44 | 0.79 | 1.18 / 1.16 | 0.08 / -0.10 / 0.37 | 0.08 | -0.37 | 0.98 | -0.05 | 0.00 | 783 | NO |
| NQ 7 | slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | 515 | 2 | 0.44 | 0.78 | -0.20 | -0.83 / 1.05 | 0.11 / 0.17 / -0.46 | -0.04 | 0.30 | 0.61 | -0.25 | 0.00 | 827 | NO |
| NQ 8 | slot 12:00 mean of prior 5d same-slot ret dir=with hold=30m | 510 | 2 | 0.29 | -0.03 | -0.48 | -1.32 / 1.16 | 0.02 / -0.90 / -0.44 | -0.25 | -0.19 | 0.36 | -0.45 | 0.00 | 818 | NO |
| NQ 9 | slot 11:00 mean of prior 5d same-slot ret dir=with hold=30m | 510 | 2 | 0.04 | -0.82 | -0.61 | -1.33 / 1.30 | -0.03 / -0.36 / -0.55 | -0.22 | -0.40 | 0.32 | -0.42 | 0.00 | 818 | NO |
| NQ 10 (diag) | slot 14:00 mean of prior 5d same-slot ret dir=with hold=30m | 417 | 1 | 0.86 | -0.41 | -0.16 | -1.81 / 1.43 | 0.14 / -0.63 / -0.28 | -0.10 | -0.54 | 0.60 | -0.26 | 0.00 | 669 | diag |
| RTY 1 | slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | 476 | 2 | 0.69 | -0.76 | 0.28 | -0.68 / 0.65 | 0.06 / -0.12 / -0.05 | -0.08 | -0.21 | 0.99 | -0.12 | 0.00 | 764 | NO |
| RTY 2 | slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | 513 | 2 | 0.64 | -0.14 | -0.07 | -0.91 / 0.50 | 0.07 / -0.48 / -0.28 | -0.14 | -0.03 | 0.95 | -0.28 | 0.00 | 823 | NO |
| RTY 3 | slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | 475 | 2 | 0.32 | -0.87 | 0.12 | 0.02 / 0.49 | -0.01 / -0.28 / 0.10 | -0.12 | 0.38 | 0.97 | -0.20 | 0.00 | 764 | NO |
| RTY 4 | slot 15:30 mean of prior 5d same-slot ret dir=with hold=30m | 417 | 2 | 0.03 | -0.22 | -0.28 | -0.59 / 0.47 | -0.09 / 0.07 / -0.35 | -0.23 | 0.65 | 0.85 | -0.32 | 0.00 | 670 | NO |
| RTY 5 (diag) | slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | 480 | 1 | 0.49 | -0.87 | 0.08 | -0.42 / 0.44 | 0.08 / -0.11 / 0.06 | -0.06 | -0.39 | 0.98 | -0.16 | 0.00 | 771 | diag |
| RTY 6 (diag) | slot 14:00 mean of prior 1d same-slot ret dir=with hold=30m | 477 | 1 | 0.21 | -1.33 | -0.20 | -0.85 / 0.56 | -0.01 / 0.08 / -0.28 | -0.16 | -0.55 | 0.93 | -0.25 | 0.00 | 767 | diag |
| RTY 7 (diag) | slot 13:30 mean of prior 5d same-slot ret dir=with hold=30m | 415 | 1 | 0.15 | -1.02 | 0.21 | 0.28 / 0.36 | -0.01 / -0.12 / 0.15 | -0.08 | -0.05 | 0.98 | -0.12 | 0.00 | 663 | diag |
| YM 1 | slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | 509 | 2 | 1.12 | -0.44 | 0.14 | -0.83 / 0.73 | 0.19 / -0.37 / -0.52 | -0.13 | -0.37 | 0.95 | -0.27 | 0.00 | 816 | NO |
| YM 2 | slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | 512 | 2 | 0.88 | -0.90 | 0.32 | -0.38 / 0.72 | 0.11 / 0.11 / -0.28 | -0.07 | 0.24 | 0.98 | -0.16 | 0.00 | 819 | NO |
| YM 3 | slot 09:30 mean of prior 5d same-slot ret dir=against hold=30m | 511 | 2 | 0.64 | -0.18 | 0.28 | -0.28 / 0.72 | 0.07 / -0.20 / -0.10 | -0.06 | -0.62 | 0.97 | -0.20 | 0.00 | 818 | NO |
| YM 4 | slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | 474 | 2 | 0.63 | -1.06 | 0.09 | -0.78 / 0.77 | 0.04 / -0.26 / -0.12 | -0.13 | 0.31 | 0.95 | -0.22 | 0.00 | 762 | NO |
| YM 5 | slot 11:30 mean of prior 5d same-slot ret dir=against hold=30m | 509 | 2 | 0.48 | -0.75 | -0.24 | -0.92 / 0.57 | 0.03 / -0.02 / -0.58 | -0.20 | -0.46 | 0.88 | -0.32 | 0.00 | 802 | NO |
| YM 6 | slot 12:30 mean of prior 5d same-slot ret dir=with hold=30m | 426 | 2 | 0.25 | -1.42 | 0.04 | -0.18 / 0.64 | -0.02 / -0.48 / 0.16 | -0.15 | 0.12 | 0.96 | -0.26 | 0.00 | 670 | NO |
| YM 7 (diag) | slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | 512 | 1 | 0.56 | -0.08 | 0.71 | 0.91 / 0.93 | 0.01 / 0.15 / 0.16 | 0.00 | -0.27 | 1.00 | -0.14 | 0.00 | 824 | diag |
| YM 8 (diag) | slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | 476 | 1 | 0.53 | -0.69 | 0.48 | 0.51 / 0.76 | 0.07 / 0.10 / 0.08 | 0.02 | -0.42 | 0.99 | -0.06 | 0.00 | 767 | diag |
| YM 9 (diag) | slot 15:30 mean of prior 1d same-slot ret dir=against hold=30m | 479 | 1 | 0.49 | -0.75 | 0.26 | -0.21 / 0.50 | 0.06 / 0.05 / -0.09 | -0.06 | 0.34 | 0.97 | -0.14 | 0.00 | 768 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 20 |
| diagnostic cells read | 10 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 18 |
| worst-decile corr <= +0.30 | 24 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | clean | 0.15 | 0.25 | -120967 | -100456 | 417436 | -166376 | 0.33 | 54.3 | 1.44 | -88684 | 275998 | -106950 |
| ES slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | H1 | -3.30 | -3.20 | -145335 | -137830 | 775092 | -159524 | -0.88 | 67.9 | 2.18 | -94955 | 185512 | -108837 |
| ES slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | H2 | -0.28 | -0.41 | -137872 | -114973 | 392336 | -159330 | -0.23 | 55.6 | 2.29 | -84598 | 213940 | -85522 |
| ES slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | all | -0.44 | -0.63 | -133516 | -113761 | 1455326 | -166376 | -0.43 | 57.1 | 1.75 | -90123 | 275998 | -108837 |
| NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | clean | 0.62 | 1.15 | -96501 | -81601 | 388284 | -122358 | 1.44 | 51.4 | 1.56 | -86804 | 277320 | -91122 |
| NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | H1 | 2.13 | 4.13 | -95973 | -75608 | 175828 | -156169 | 2.97 | 35.7 | 2.99 | -90749 | 167252 | -108166 |
| NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | H2 | 0.63 | 1.12 | -170559 | -135616 | 504357 | -192866 | 0.64 | 52.8 | 2.56 | -92340 | 240974 | -93745 |
| NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | all | 0.83 | 1.51 | -124720 | -103140 | 504357 | -192866 | 2.79 | 49.4 | 2.02 | -90416 | 277320 | -108166 |
| RTY slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | clean | 0.67 | 1.69 | -79865 | -60184 | 270290 | -137704 | 2.26 | 49.5 | 1.52 | -81285 | 318136 | -83681 |
| RTY slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | H1 | -1.49 | -1.80 | -78973 | -70871 | 317580 | -94356 | -0.62 | 50.0 | 2.71 | -85306 | 164740 | -89221 |
| RTY slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | H2 | -0.21 | -0.31 | -79322 | -73309 | 311807 | -80324 | -0.15 | 47.2 | 2.43 | -77564 | 223126 | -78898 |
| RTY slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | all | 0.28 | 0.58 | -85764 | -70438 | 399909 | -137704 | 0.91 | 49.4 | 1.90 | -81997 | 318136 | -89221 |
| YM slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | clean | 0.82 | 1.41 | -111228 | -92095 | 350266 | -137267 | 2.13 | 46.7 | 1.57 | -86668 | 266648 | -92806 |
| YM slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | H1 | 0.69 | 1.44 | -104340 | -93848 | 320698 | -133943 | 0.71 | 53.6 | 2.94 | -70119 | 140154 | -74827 |
| YM slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | H2 | -1.59 | -1.87 | -120465 | -113181 | 547512 | -129841 | -0.86 | 55.6 | 2.20 | -97163 | 231374 | -105622 |
| YM slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | all | 0.32 | 0.53 | -126008 | -106425 | 670964 | -141837 | 0.75 | 49.4 | 1.92 | -88304 | 266648 | -105622 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | -36.9 | -23.2 | 6.7 | 13.1 | -15.9 / 10.2 | -29.9 / -3.5 | NO |
| NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | -14.6 | -22.0 | 5.1 | 31.2 | 8.3 / 13.1 | -28.6 / 4.6 | NO |
| RTY slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | -26.0 | 13.7 | 23.4 | 9.6 | 22.5 / 24.2 | 9.1 / 15.1 | NO |
| YM slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | -24.5 | -14.8 | 7.9 | 36.0 | 5.4 / 10.4 | 36.6 / 44.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | negative pre-2023 | 2448 | -0.8 | -30.1 | -15.9 | 29.4 | -0.04 / -1.41 / -0.75 | 35.0 / 5.7 |
| ES 2 (diag) slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2629 | 9.0 | -20.3 | -6.1 | 29.4 | 0.32 / -0.72 / -0.22 | 53.0 / 23.7 |
| ES 3 (diag) slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | negative pre-2023 | 2415 | -0.1 | -29.5 | -15.3 | 29.4 | -0.01 / -1.64 / -0.85 | 66.1 / 36.7 |
| ES 4 (diag) slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 2643 | -2.7 | -32.0 | -17.8 | 29.4 | -0.09 / -1.17 / -0.65 | 39.8 / 10.4 |
| NQ 1 slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 2633 | -2.6 | -17.0 | -8.5 | 14.4 | -0.05 / -0.38 / -0.19 | 94.3 / 80.0 |
| NQ 2 slot 12:30 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 2316 | -14.1 | -28.4 | -19.8 | 14.4 | -0.53 / -1.06 / -0.74 | 57.8 / 43.5 |
| NQ 3 slot 11:30 mean of prior 5d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2622 | 5.4 | -9.0 | -0.5 | 14.4 | 0.19 / -0.32 / -0.02 | 50.8 / 36.4 |
| NQ 4 slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | negative pre-2023 | 2512 | -1.0 | -15.4 | -6.8 | 14.4 | -0.04 / -0.49 / -0.22 | 53.6 / 39.3 |
| NQ 5 slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m | negative pre-2023 | 2511 | -1.0 | -15.4 | -6.8 | 14.4 | -0.03 / -0.54 / -0.24 | 47.8 / 33.4 |
| NQ 6 slot 12:30 mean of prior 1d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2531 | 2.9 | -11.4 | -2.9 | 14.4 | 0.10 / -0.44 / -0.12 | 49.8 / 35.4 |
| NQ 7 slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | positive pre-2023 | 2660 | 53.7 | 39.3 | 47.9 | 14.4 | 1.06 / 0.78 / 0.95 | 48.9 / 34.5 |
| NQ 8 slot 12:00 mean of prior 5d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2593 | 13.4 | -0.9 | 7.6 | 14.4 | 0.44 / -0.03 / 0.25 | 27.2 / 12.8 |
| NQ 9 slot 11:00 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 2636 | -14.1 | -28.4 | -19.9 | 14.4 | -0.40 / -0.82 / -0.57 | 15.2 / 0.8 |
| NQ 10 (diag) slot 14:00 mean of prior 5d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2250 | 1.3 | -13.1 | -4.4 | 14.4 | 0.04 / -0.41 / -0.14 | 68.6 / 54.3 |
| RTY 1 slot 13:30 mean of prior 1d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 1416 | 2.3 | -12.0 | -9.8 | 14.4 | 0.14 / -0.76 / -0.62 | 30.3 / 16.0 |
| RTY 2 slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 1516 | 9.7 | -4.7 | -2.5 | 14.4 | 0.34 / -0.14 / -0.07 | 33.0 / 18.7 |
| RTY 3 slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | negative pre-2023 | 1417 | -0.5 | -14.9 | -12.6 | 14.4 | -0.04 / -0.87 / -0.74 | 18.2 / 3.9 |
| RTY 4 slot 15:30 mean of prior 5d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 1255 | 10.1 | -4.3 | -2.0 | 14.4 | 0.50 / -0.22 / -0.11 | 12.5 / -1.8 |
| RTY 5 (diag) slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 1420 | 1.6 | -12.8 | -10.6 | 14.4 | 0.10 / -0.87 / -0.72 | 22.8 / 8.5 |
| RTY 6 (diag) slot 14:00 mean of prior 1d same-slot ret dir=with hold=30m | negative pre-2023 | 1419 | -10.3 | -24.7 | -22.5 | 14.4 | -0.56 / -1.33 / -1.21 | 18.5 / 4.1 |
| RTY 7 (diag) slot 13:30 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 1242 | -1.7 | -16.1 | -13.9 | 14.4 | -0.11 / -1.02 / -0.88 | 19.2 / 4.9 |
| YM 1 slot 10:00 mean of prior 5d same-slot ret dir=with hold=30m | gross-positive, cost-negative pre-2023 | 2607 | 5.2 | -9.2 | -3.5 | 14.4 | 0.24 / -0.44 / -0.17 | 41.3 / 26.9 |
| YM 2 slot 11:30 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2620 | 1.4 | -13.0 | -7.3 | 14.4 | 0.10 / -0.90 / -0.50 | 31.9 / 17.6 |
| YM 3 slot 09:30 mean of prior 5d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2626 | 10.0 | -4.4 | 1.3 | 14.4 | 0.42 / -0.18 / 0.06 | 39.5 / 25.2 |
| YM 4 slot 14:30 mean of prior 1d same-slot ret dir=with hold=30m | negative pre-2023 | 2492 | -3.1 | -17.4 | -11.7 | 14.4 | -0.19 / -1.06 / -0.71 | 29.1 / 14.8 |
| YM 5 slot 11:30 mean of prior 5d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2591 | 3.5 | -10.9 | -5.2 | 14.4 | 0.23 / -0.75 / -0.36 | 21.0 / 6.6 |
| YM 6 slot 12:30 mean of prior 5d same-slot ret dir=with hold=30m | negative pre-2023 | 2293 | -6.3 | -20.6 | -14.8 | 14.4 | -0.43 / -1.42 / -1.02 | 18.4 / 4.0 |
| YM 7 (diag) slot 09:30 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2658 | 12.4 | -1.9 | 3.8 | 14.4 | 0.53 / -0.08 / 0.16 | 33.3 / 18.9 |
| YM 8 (diag) slot 13:00 mean of prior 1d same-slot ret dir=against hold=30m | gross-positive, cost-negative pre-2023 | 2476 | 4.1 | -10.2 | -4.5 | 14.4 | 0.27 / -0.69 / -0.31 | 34.9 / 20.5 |
| YM 9 (diag) slot 15:30 mean of prior 1d same-slot ret dir=against hold=30m | negative pre-2023 | 2502 | -4.6 | -19.0 | -13.2 | 14.4 | -0.18 / -0.75 / -0.52 | 26.9 / 12.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 1 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 0.32, p(top) = 0.19); NQ: 9 cells pass the clean rule against a replicate mean of 6.7 (p(count) = 0.22, p(top) = 0.65); RTY: 4 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.04, p(top) = 0.42); YM: 6 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 0.01, p(top) = 0.18).
- Of 20 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.12 (NQ slot 15:00 mean of prior 1d same-slot ret dir=against hold=30m); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'gross-positive, cost-negative pre-2023': 10, 'negative pre-2023': 9, 'positive pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bi_1.py, ap_bi_pipe.py (= ap_b_pipe2 with module swap), ap_bi_job.sh, ap_sw_common.py, ap_bi_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bi1/ (`BI1_CO_all_selected_scored.csv`).

DONE BI1
