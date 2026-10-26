# REPORT SW3 - compression-then-expansion breakout sleeves (D08 H2/H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 20 selected cells (+3 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.13; best pair-window standalone Sharpe +0.99.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: previous tf bar has ATR(5)/ATR(50) < q (compressed) and the bar closes beyond the prior N-bar high/low; enter with or against, exact hold 30/60/120 min, no stop.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: 144 cells per instrument = 2 bar sizes x 3 q (0.6/0.75/0.9) x 2 N (12/24) x 2 directions x 3 holds x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |     144 |        114 |        13 |               1.218 |                2 |         10 |            0 |
| CL    |     144 |        100 |         2 |               0.903 |                2 |          2 |            0 |
| ES    |     144 |         98 |         6 |               0.672 |                2 |          2 |            0 |
| GC    |     144 |        120 |         2 |               0.888 |                2 |          2 |            0 |
| NQ    |     144 |        102 |        14 |               1.265 |                2 |          0 |            0 |
| RTY   |     144 |        102 |         1 |               1.299 |                2 |          1 |            3 |
| YM    |     144 |         98 |         3 |               1.211 |                2 |          3 |            0 |
| ZN    |     144 |        100 |         0 |               0.902 |                2 |          0 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                    6 |             2.95 |               8 |       0.09 |                       0.336 |            0.608 |           0.974 |     0.86 |       0.672 |                1.462 |
| NQ    |     100 |                   14 |            16.82 |              30 |       0.77 |                       0.667 |            0.884 |           1.095 |     0.9  |       1.084 |                1.907 |
| RTY   |     100 |                    1 |             3.76 |               9 |       0.99 |                       1.099 |            0.57  |           0.873 |     0.01 |       1.099 |                1.499 |
| YM    |     100 |                    3 |             5.32 |              11 |       0.93 |                       0.862 |            0.586 |           0.855 |     0.03 |       1.211 |                1.636 |
| GC    |     100 |                    2 |             3.95 |               9 |       0.9  |                       0.402 |            0.609 |           0.927 |     0.81 |       0.637 |                1.597 |
| CL    |     100 |                    2 |             1.01 |               4 |       0.27 |                       0.353 |            0.528 |           0.974 |     0.45 |       0.532 |                1.164 |
| ZN    |     100 |                    0 |             0    |               0 |       1    |                     nan     |          nan     |         nan     |   nan    |     nan     |              nan     |
| BTC   |     100 |                   13 |             9.84 |              18 |       0.15 |                       0.794 |            0.668 |           0.843 |     0.15 |       1.001 |                1.8   |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | 334 | 2 | 0.67 | -0.85 | 0.53 | 0.22 / 0.74 | 0.06 / -0.03 / 0.08 | -0.02 | -0.11 | 0.99 | -0.11 | 0.67 | 626 | NO |
| ES 2 | 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | 203 | 2 | 0.38 | -0.86 | 0.20 | -0.07 / -0.30 | 0.07 / -0.37 / 0.11 | -0.08 | -0.03 | 1.00 | -0.18 | 0.17 | 364 | NO |
| RTY 1 | 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | 150 | 2 | 1.10 | -0.87 | 0.33 | -0.79 / 0.34 | 0.16 / -0.37 / -0.14 | -0.02 | 0.06 | 1.00 | -0.17 | 0.17 | 283 | NO |
| RTY 2 (diag) | 15m compress atr5/atr50<0.75 break12 dir=with hold=60m day | 22 | 2 | 1.30 | -0.90 | 0.62 | 0.21 / 0.46 | 0.21 / 0.83 / -0.40 | 0.11 | -0.12 | 1.00 | -0.09 | 0.33 | 52 S | diag |
| RTY 3 (diag) | 15m compress atr5/atr50<0.6 break12 dir=against hold=60m day | 2 | 1 | 0.99 | 0.52 | 0.99 | 0.98 / 0.70 | 0.12 / 0.24 / 0.00 | 0.11 |  | 1.00 | 0.02 | 0.17 | 4 S | diag |
| RTY 4 (diag) | 15m compress atr5/atr50<0.75 break24 dir=with hold=60m day | 11 | 1 | 0.83 | -0.57 | 0.43 | 0.41 / 0.83 | 0.08 / 1.12 / -0.41 | 0.06 | 0.01 | 0.99 | -0.18 | 0.33 | 31 S | diag |
| YM 1 | 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | 190 | 2 | 1.21 | -0.90 | 0.32 | -1.61 / 0.05 | 0.24 / -0.81 / 0.04 | -0.00 | 0.04 | 1.00 | -0.14 | 0.50 | 330 | NO |
| YM 2 | 15m compress atr5/atr50<0.9 break24 dir=against hold=30m day | 131 | 2 | 0.90 | -0.70 | -0.01 | -1.91 / 0.66 | 0.20 / -0.81 / -0.10 | -0.05 | 0.05 | 0.94 | -0.19 | 0.00 | 221 | NO |
| YM 3 | 5m compress atr5/atr50<0.9 break24 dir=with hold=120m day | 279 | 2 | 0.47 | -0.23 | -0.04 | -0.98 / 0.92 | -0.00 / 0.09 / -0.36 | -0.11 | 0.27 | 0.70 | -0.23 | 0.00 | 498 | NO |
| GC 1 | 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | 180 | 2 | 0.64 | -0.46 | 0.10 | -0.32 / 1.11 | 0.10 / -1.17 / -0.11 | -0.17 | 0.33 | 0.77 | -0.46 | 0.00 | 335 | NO |
| GC 2 | 15m compress atr5/atr50<0.9 break24 dir=against hold=60m day | 129 | 2 | 0.17 | -0.44 | -0.17 | -0.28 / 0.91 | -0.03 / -0.54 / -0.74 | -0.29 | -0.15 | 0.75 | -0.65 | 0.00 | 237 | NO |
| CL 1 | 5m compress atr5/atr50<0.75 break24 dir=with hold=120m day | 136 | 2 | 0.53 | -0.25 | -0.05 | -0.64 / 0.83 | 0.08 / -0.35 / -0.19 | -0.10 | 0.06 | 0.93 | -0.23 | 0.00 | 222 | NO |
| CL 2 | 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | 105 | 2 | 0.17 | -0.22 | 0.06 | -0.02 / 0.20 | 0.02 / -0.23 / -0.14 | -0.17 | 0.27 | 1.00 | -0.30 | 0.00 | 138 | NO |
| BTC 1 | 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | 931 | 2 | 1.00 | -2.31 | 0.74 | 0.38 / 0.52 | 0.16 / -0.45 / 0.38 | 0.03 | -0.29 | 1.00 | -0.07 | 0.17 | 1532 | NO |
| BTC 2 | 15m compress atr5/atr50<0.75 break24 dir=with hold=60m all | 818 | 2 | 0.99 | -0.58 | -0.11 | -1.81 / 1.05 | 0.15 / -0.35 / -0.42 | -0.15 | -0.15 | 0.79 | -0.24 | 0.00 | 1226 | NO |
| BTC 3 | 15m compress atr5/atr50<0.75 break12 dir=with hold=60m all | 1419 | 2 | 0.87 | -1.30 | -0.16 | -1.81 / 0.93 | 0.15 / -0.38 / -0.26 | -0.16 | 0.09 | 0.88 | -0.22 | 0.00 | 2159 | NO |
| BTC 4 | 15m compress atr5/atr50<0.75 break12 dir=against hold=30m day | 122 | 2 | 0.87 | -0.52 | 0.69 | 0.41 / 0.79 | 0.14 / 0.43 / -0.09 | 0.09 | -0.02 | 0.99 | -0.07 | 0.17 | 206 | NO |
| BTC 5 | 15m compress atr5/atr50<0.75 break12 dir=with hold=120m all | 1199 | 2 | 0.85 | -0.85 | 0.27 | -0.82 / 0.94 | 0.11 / -0.00 / -0.27 | -0.08 | 0.05 | 0.90 | -0.17 | 0.33 | 1834 | NO |
| BTC 6 | 15m compress atr5/atr50<0.75 break24 dir=with hold=120m all | 740 | 2 | 0.80 | 0.22 | 0.00 | -1.11 / 1.05 | 0.11 / -0.35 / -0.34 | -0.12 | -0.30 | 0.76 | -0.24 | 0.00 | 1118 | NO |
| BTC 7 | 15m compress atr5/atr50<0.6 break12 dir=with hold=120m all | 524 | 2 | 0.68 | 0.23 | 0.10 | -0.90 / 1.02 | 0.12 / -0.24 / -0.11 | -0.05 | -0.09 | 0.79 | -0.18 | 0.50 | 750 | NO |
| BTC 8 | 15m compress atr5/atr50<0.6 break24 dir=with hold=120m all | 289 | 2 | 0.67 | 0.74 | 0.12 | -0.86 / 0.99 | 0.13 / -0.24 / -0.12 | -0.02 | -0.25 | 0.72 | -0.17 | 0.33 | 405 | NO |
| BTC 9 | 15m compress atr5/atr50<0.9 break12 dir=against hold=120m day | 239 | 2 | 0.61 | 0.55 | 0.73 | 0.87 / 1.01 | 0.12 / -0.06 / 0.00 | 0.07 | -0.44 | 0.98 | -0.10 | 0.33 | 406 | NO |
| BTC 10 | 15m compress atr5/atr50<0.9 break12 dir=with hold=120m all | 1645 | 2 | 0.60 | -1.12 | 0.12 | -0.72 / 0.75 | 0.07 / 0.33 / -0.31 | -0.10 | 0.07 | 0.87 | -0.19 | 0.00 | 2627 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 20 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 11 |
| worst-decile corr <= +0.30 | 21 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | clean | 0.95 | 1.65 | -114675 | -92876 | 553461 | -147766 | 1.56 | 47.6 | 1.62 | -89488 | 215276 | -105907 |
| BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | H1 | -1.55 | -1.89 | -110875 | -99447 | 414601 | -136379 | -0.79 | 60.7 | 2.38 | -74616 | 185865 | -89768 |
| BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | H2 | 1.75 | 2.87 | -123462 | -90757 | 312814 | -176725 | 1.69 | 36.1 | 2.68 | -74650 | 199031 | -76247 |
| BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | all | 0.74 | 1.20 | -120725 | -97554 | 553461 | -176725 | 1.92 | 47.0 | 1.98 | -86594 | 215276 | -105907 |
| CL 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | clean | 0.16 | 0.21 | -157222 | -120754 | 388749 | -309713 | 0.37 | 27.6 | 1.48 | -89236 | 284349 | -141810 |
| CL 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | H1 | -0.33 | -0.39 | -193156 | -136284 | 216865 | -204650 | -0.36 | 14.3 | 2.60 | -77610 | 164487 | -78287 |
| CL 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | H2 | 0.08 | 0.16 | -261447 | -204156 | 479524 | -309713 | 0.13 | 25.0 | 2.16 | -89955 | 217425 | -97386 |
| CL 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | all | 0.06 | 0.10 | -205718 | -150866 | 526578 | -309713 | 0.24 | 25.0 | 1.81 | -88439 | 284349 | -141810 |
| ES 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | clean | 0.68 | 1.38 | -108703 | -78993 | 261567 | -151531 | 2.36 | 42.9 | 1.52 | -82977 | 297709 | -87065 |
| ES 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | H1 | -0.40 | -0.53 | -113433 | -102123 | 275791 | -143923 | -0.30 | 57.1 | 2.79 | -62597 | 174989 | -64432 |
| ES 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | H2 | 0.71 | 1.19 | -93528 | -76194 | 180171 | -106859 | 1.01 | 44.4 | 2.37 | -82939 | 239157 | -84431 |
| ES 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | all | 0.53 | 0.95 | -110532 | -86375 | 433682 | -151531 | 1.66 | 45.8 | 1.89 | -82574 | 297709 | -87065 |
| GC 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | clean | 0.81 | 1.48 | -108125 | -93960 | 292065 | -152821 | 2.62 | 40.0 | 1.56 | -84758 | 277394 | -94952 |
| GC 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | H1 | -1.14 | -1.56 | -360582 | -339622 | 1305321 | -369065 | -0.66 | 46.4 | 1.66 | -103869 | 317337 | -136473 |
| GC 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | H2 | 0.51 | 0.75 | -306304 | -255531 | 656290 | -307137 | 0.58 | 38.9 | 2.18 | -120965 | 247089 | -143619 |
| GC 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | all | 0.10 | 0.15 | -281707 | -219663 | 1305321 | -369065 | 0.22 | 41.1 | 1.73 | -99768 | 317337 | -143619 |
| RTY 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | clean | 1.04 | 1.79 | -115003 | -94950 | 499160 | -227803 | 1.88 | 30.5 | 1.62 | -87219 | 266930 | -97725 |
| RTY 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | H1 | -1.79 | -2.10 | -113937 | -107154 | 601536 | -119481 | -0.66 | 53.6 | 2.45 | -59442 | 155609 | -62805 |
| RTY 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | H2 | -0.15 | -0.23 | -125436 | -116914 | 338020 | -128155 | -0.16 | 47.2 | 2.16 | -86508 | 195125 | -87647 |
| RTY 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | all | 0.33 | 0.51 | -124667 | -106679 | 994059 | -227803 | 0.49 | 38.1 | 1.88 | -86474 | 266930 | -97725 |
| YM 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | clean | 1.25 | 2.91 | -86532 | -69478 | 369726 | -112966 | 3.08 | 41.9 | 1.70 | -82044 | 254667 | -88147 |
| YM 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | H1 | -3.17 | -3.10 | -147982 | -139615 | 712995 | -172671 | -0.99 | 57.1 | 2.02 | -83518 | 164276 | -87011 |
| YM 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | H2 | 0.02 | 0.02 | -90048 | -73767 | 212048 | -92509 | 0.02 | 36.1 | 2.33 | -74379 | 217605 | -77416 |
| YM 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | all | 0.32 | 0.55 | -112880 | -91267 | 1160281 | -172671 | 0.38 | 43.5 | 1.90 | -81857 | 254667 | -88147 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | -22.0 | 6.2 | 19.0 | 20.6 | 5.5 / 16.2 | 48.9 / 51.6 | NO |
| RTY 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | -24.5 | -27.1 | 11.1 | 17.1 | -28.1 / 6.3 | 35.4 / 36.4 | NO |
| YM 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | -25.1 | 14.8 | 19.6 | 30.5 | 16.5 / 23.6 | 10.2 / 11.0 | NO |
| GC 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | -26.9 | -81.0 | -32.0 | -53.9 | 4.1 / 15.4 | -82.9 / -62.4 | NO |
| CL 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | -28.6 | -80.3 | 0.9 | 21.2 | -81.8 / 2.5 | -2.0 / 13.2 | NO |
| BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | -18.1 | -17.3 | 9.5 | 38.4 | -18.2 / 3.3 | 6.6 / 14.6 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 5m compress atr5/atr50<0.9 break12 dir=with hold=120m day | negative pre-2023 | 2460 | -6.4 | -35.7 | -22.0 | 29.4 | -0.15 / -0.85 / -0.53 | 99.3 / 69.9 |
| ES 2 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | negative pre-2023 | 1318 | -1.4 | -30.8 | -17.3 | 29.4 | -0.04 / -0.86 / -0.48 | 50.3 / 20.9 |
| RTY 1 15m compress atr5/atr50<0.9 break12 dir=with hold=60m day | negative pre-2023 | 789 | -22.2 | -36.6 | -34.2 | 14.4 | -0.53 / -0.87 / -0.81 | 71.1 / 56.8 |
| RTY 2 (diag) 15m compress atr5/atr50<0.75 break12 dir=with hold=60m day | negative pre-2023 | 247 | -46.4 | -60.8 | -57.9 | 14.4 | -0.70 / -0.90 / -0.87 | 100.7 / 86.3 |
| RTY 3 (diag) 15m compress atr5/atr50<0.6 break12 dir=against hold=60m day | positive pre-2023 | 25 | 209.2 | 194.8 | 198.1 | 14.4 | 0.56 / 0.52 / 0.53 | 250.0 / 235.6 |
| RTY 4 (diag) 15m compress atr5/atr50<0.75 break24 dir=with hold=60m day | negative pre-2023 | 160 | -35.7 | -50.1 | -47.2 | 14.4 | -0.42 / -0.57 / -0.54 | 80.5 / 66.1 |
| YM 1 15m compress atr5/atr50<0.9 break12 dir=against hold=30m day | negative pre-2023 | 1418 | -6.6 | -21.0 | -15.4 | 14.4 | -0.29 / -0.90 / -0.67 | 68.4 / 54.1 |
| YM 2 15m compress atr5/atr50<0.9 break24 dir=against hold=30m day | negative pre-2023 | 886 | -9.7 | -24.0 | -18.6 | 14.4 | -0.29 / -0.70 / -0.54 | 66.9 / 52.6 |
| YM 3 5m compress atr5/atr50<0.9 break24 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 2016 | 6.6 | -7.8 | -2.2 | 14.4 | 0.19 / -0.23 / -0.06 | 56.1 / 41.8 |
| GC 1 15m compress atr5/atr50<0.9 break12 dir=with hold=120m day | negative pre-2023 | 811 | -4.1 | -28.5 | -18.9 | 24.4 | -0.07 / -0.46 / -0.31 | 101.1 / 76.7 |
| GC 2 15m compress atr5/atr50<0.9 break24 dir=against hold=60m day | negative pre-2023 | 502 | -0.6 | -25.0 | -15.3 | 24.4 | -0.01 / -0.44 / -0.27 | 24.0 / -0.4 |
| CL 1 5m compress atr5/atr50<0.75 break24 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 446 | 9.0 | -15.3 | -11.0 | 24.4 | 0.15 / -0.25 / -0.18 | 59.3 / 35.0 |
| CL 2 5m compress atr5/atr50<0.6 break12 dir=against hold=60m day | gross-positive, cost-negative pre-2023 | 174 | 11.8 | -12.6 | -8.5 | 24.4 | 0.19 / -0.22 / -0.15 | 28.3 / 3.9 |
| BTC 1 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day | negative pre-2023 | 754 | -50.1 | -104.5 | -71.9 | 54.4 | -1.10 / -2.31 / -1.59 | 159.4 / 105.0 |
| BTC 2 15m compress atr5/atr50<0.75 break24 dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 467 | 26.5 | -27.9 | 4.6 | 54.4 | 0.59 / -0.58 / 0.12 | 141.4 / 87.1 |
| BTC 3 15m compress atr5/atr50<0.75 break12 dir=with hold=60m all | gross-positive, cost-negative pre-2023 | 955 | 11.0 | -43.4 | -11.0 | 54.4 | 0.36 / -1.30 / -0.32 | 113.4 / 59.0 |
| BTC 4 15m compress atr5/atr50<0.75 break12 dir=against hold=30m day | gross-positive, cost-negative pre-2023 | 110 | 2.5 | -51.9 | -18.5 | 54.4 | 0.02 / -0.52 / -0.19 | 320.3 / 265.9 |
| BTC 5 15m compress atr5/atr50<0.75 break12 dir=with hold=120m all | gross-positive, cost-negative pre-2023 | 826 | 11.0 | -43.3 | -11.0 | 54.4 | 0.25 / -0.85 / -0.20 | 150.6 / 96.3 |
| BTC 6 15m compress atr5/atr50<0.75 break24 dir=with hold=120m all | positive pre-2023 | 437 | 69.7 | 15.4 | 47.8 | 54.4 | 0.87 / 0.22 / 0.61 | 155.6 / 101.3 |
| BTC 7 15m compress atr5/atr50<0.6 break12 dir=with hold=120m all | positive pre-2023 | 392 | 68.8 | 14.4 | 47.1 | 54.4 | 1.01 / 0.23 / 0.70 | 153.7 / 99.3 |
| BTC 8 15m compress atr5/atr50<0.6 break24 dir=with hold=120m all | positive pre-2023 | 176 | 134.5 | 80.2 | 112.9 | 54.4 | 1.22 / 0.74 / 1.03 | 199.0 / 144.7 |
| BTC 9 15m compress atr5/atr50<0.9 break12 dir=against hold=120m day | positive pre-2023 | 213 | 148.7 | 94.3 | 126.9 | 54.4 | 0.88 / 0.55 / 0.75 | 337.2 / 282.9 |
| BTC 10 15m compress atr5/atr50<0.9 break12 dir=with hold=120m all | negative pre-2023 | 1157 | -4.0 | -58.4 | -26.1 | 54.4 | -0.08 / -1.12 / -0.50 | 114.2 / 59.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 13 cells pass the clean rule against a replicate mean of 9.8 (p(count) = 0.15, p(top) = 0.15); CL: 2 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.27, p(top) = 0.45); ES: 6 cells pass the clean rule against a replicate mean of 3.0 (p(count) = 0.09, p(top) = 0.86); GC: 2 cells pass the clean rule against a replicate mean of 4.0 (p(count) = 0.90, p(top) = 0.81); NQ: 14 cells pass the clean rule against a replicate mean of 16.8 (p(count) = 0.77, p(top) = 0.90); RTY: 1 cells pass the clean rule against a replicate mean of 3.8 (p(count) = 0.99, p(top) = 0.01); YM: 3 cells pass the clean rule against a replicate mean of 5.3 (p(count) = 0.93, p(top) = 0.03); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 20 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.13 (BTC 5m compress atr5/atr50<0.9 break12 dir=against hold=60m day); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 9, 'gross-positive, cost-negative pre-2023': 7, 'positive pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_3.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw3/ (`SW3_CO_all_selected_scored.csv`).

DONE SW3
