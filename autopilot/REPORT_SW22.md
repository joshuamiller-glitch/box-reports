# REPORT SW22 - daily option-state (gamma panel) direction sleeves (D03 H5 M1-M3)

**Verdict: LEAD. FOUND 0, LEAD 3, INSURANCE 0.** 38 selected cells (+2 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.21; best pair-window standalone Sharpe +1.61.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Features (outputs/autopilot/opt/feat_NQ|feat_ES.parquet, built from the option definition/statistics files on disk): gex_norm, zgd, skew, term. Value of the previous available date, percentile vs the prior 250 days; tails q 0.2/0.33; modes pm / hi / lo; direction +/-; entry at RTH open or at the 18:00 Globex open; hold to the 16:55 flatten. NQ uses the NQ panel; ES, RTY, YM use the ES panel. History 2019-2026 (ERA flag covers 2019-22 only).
- Instruments: ES, NQ, RTY, YM. Grid: 96 cells per instrument = 4 features x 2 tails x 3 modes x 2 directions x 2 entries.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      96 |         84 |        10 |               1.931 |                2 |         10 |            0 |
| NQ    |      96 |         84 |        20 |               1.199 |                2 |         10 |            0 |
| RTY   |      96 |         84 |         8 |               1.402 |                2 |          8 |            2 |
| YM    |      96 |         84 |        15 |               1.442 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     100 |                   10 |             4.86 |              10 |       0.01 |                       0.573 |            0.755 |           1.075 |     0.89 |       1.87  |                1.761 |
| NQ    |     100 |                   20 |             7.52 |              13 |       0    |                       0.779 |            0.801 |           1.085 |     0.48 |       1.199 |                2.038 |
| RTY   |     100 |                    8 |            12.97 |              21 |       0.95 |                       0.469 |            0.919 |           1.19  |     1    |       0.948 |                2.034 |
| YM    |     100 |                   15 |             5.48 |              10 |       0    |                       0.539 |            0.738 |           1.026 |     0.89 |       0.702 |                1.874 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | skew tail0.33 mode=lo dir=+ entry=globex | 141 | 2 | 1.87 | 0.07 | 0.53 | -0.98 / 1.47 | 0.28 / -0.06 / -0.34 | 0.05 | -0.13 | 0.94 | -0.13 | 0.50 | 262 | NO |
| ES 2 | skew tail0.33 mode=lo dir=+ entry=rth | 141 | 2 | 1.05 | -0.01 | -0.02 | -1.31 / 1.23 | 0.16 / 0.02 / -0.62 | -0.09 | 0.07 | 0.58 | -0.28 | 0.00 | 262 | NO |
| ES 3 | term tail0.2 mode=hi dir=+ entry=globex | 126 | 2 | 0.57 | 0.15 | 0.61 | 0.76 / 1.50 | 0.02 / 0.20 / 0.16 | 0.04 | 0.41 | 0.85 | -0.09 | 0.00 | 167 | NO |
| ES 4 | term tail0.2 mode=pm dir=+ entry=globex | 230 | 2 | 0.52 | 0.09 | 0.63 | 0.70 / 1.26 | 0.03 / 0.02 / 0.18 | 0.03 | 0.36 | 0.91 | -0.11 | 0.50 | 354 | NO |
| ES 5 | term tail0.33 mode=hi dir=+ entry=globex | 177 | 2 | 0.38 | 0.05 | 0.77 | 1.95 / 1.35 | 0.00 / 0.27 / 0.39 | 0.08 | 0.15 | 0.94 | -0.05 | 0.50 | 253 | NO |
| ES 6 | term tail0.33 mode=pm dir=+ entry=globex | 349 | 2 | 0.37 | -0.12 | 0.91 | 1.78 / 1.33 | 0.02 / 0.34 / 0.35 | 0.09 | 0.14 | 0.95 | -0.05 | 0.50 | 554 | NO |
| ES 7 | zgd tail0.33 mode=lo dir=+ entry=globex | 146 | 2 | 0.30 | 0.18 | 0.64 | 1.56 / 1.49 | -0.01 / 0.26 / 0.19 | 0.04 | 0.21 | 0.91 | -0.09 | 1.00 | 248 | NO |
| ES 8 | gex_norm tail0.33 mode=lo dir=+ entry=globex | 153 | 2 | 0.30 | 0.11 | 0.57 | 1.33 / 1.61 | -0.00 / 0.23 / 0.19 | 0.04 | 0.21 | 0.87 | -0.09 | 0.50 | 253 | NO |
| ES 9 | term tail0.2 mode=hi dir=+ entry=rth | 126 | 2 | 0.30 | 0.06 | 0.06 | -0.62 / 1.29 | -0.01 / 0.14 / -0.15 | -0.05 | 0.35 | 0.59 | -0.18 | 0.00 | 167 | NO |
| ES 10 | term tail0.33 mode=lo dir=- entry=globex | 172 | 2 | 0.07 | -0.39 | 0.49 | 0.79 / 1.25 | 0.02 / 0.11 / -0.06 | 0.00 | 0.00 | 0.82 | -0.20 | 0.00 | 301 | NO |
| NQ 1 | gex_norm tail0.2 mode=hi dir=- entry=rth | 134 | 2 | 1.20 | -0.46 | 1.19 | 1.20 / 1.56 | 0.18 / 0.45 / 0.10 | 0.21 | -0.33 | 0.98 | 0.03 | 0.00 | 203 | LEAD(gate3-7 fail: plateau ) |
| NQ 2 | skew tail0.33 mode=lo dir=+ entry=globex | 137 | 2 | 1.17 | 0.30 | 0.49 | 0.16 / 1.38 | 0.19 / -0.21 / -0.01 | 0.08 | -0.29 | 0.82 | -0.22 | 0.50 | 272 | NO |
| NQ 3 | gex_norm tail0.2 mode=hi dir=- entry=globex | 134 | 2 | 1.04 | -0.26 | 0.83 | 0.65 / 1.39 | 0.16 / 0.20 / 0.00 | 0.13 | -0.24 | 0.91 | -0.07 | 0.00 | 203 | NO |
| NQ 4 | zgd tail0.2 mode=hi dir=- entry=rth | 128 | 2 | 0.90 | -0.31 | 0.72 | 0.50 / 1.57 | 0.14 / 0.08 / -0.07 | 0.10 | 0.20 | 0.86 | -0.07 | 0.00 | 185 | NO |
| NQ 5 | gex_norm tail0.2 mode=pm dir=- entry=globex | 220 | 2 | 0.71 | 0.04 | 0.85 | 1.06 / 1.37 | 0.08 / 0.36 / 0.15 | 0.12 | 0.06 | 0.96 | -0.05 | 0.50 | 354 | NO |
| NQ 6 | gex_norm tail0.2 mode=pm dir=- entry=rth | 220 | 2 | 0.65 | -0.10 | 0.84 | 1.13 / 1.42 | 0.09 / 0.35 / 0.14 | 0.13 | -0.09 | 0.97 | -0.03 | 0.00 | 353 | LEAD |
| NQ 7 | term tail0.33 mode=hi dir=+ entry=globex | 164 | 2 | 0.63 | 0.22 | 0.80 | 1.08 / 1.48 | 0.05 / 0.17 / 0.33 | 0.10 | 0.16 | 0.91 | -0.05 | 1.00 | 265 | NO |
| NQ 8 | zgd tail0.2 mode=pm dir=- entry=rth | 215 | 2 | 0.57 | -0.08 | 0.65 | 0.81 / 1.31 | 0.06 / 0.15 / 0.08 | 0.07 | 0.35 | 0.92 | -0.08 | 0.00 | 322 | NO |
| NQ 9 | term tail0.2 mode=hi dir=+ entry=globex | 120 | 2 | 0.49 | 0.34 | 0.67 | 1.22 / 1.31 | 0.02 / 0.06 / 0.24 | 0.06 | 0.72 | 0.83 | -0.08 | 1.00 | 169 | NO |
| NQ 10 | term tail0.33 mode=pm dir=+ entry=globex | 386 | 2 | 0.44 | 0.07 | 0.77 | 1.24 / 1.37 | 0.04 / 0.21 / 0.32 | 0.10 | 0.12 | 0.94 | -0.06 | 1.00 | 581 | NO |
| RTY 1 | gex_norm tail0.33 mode=pm dir=- entry=rth | 355 | 2 | 0.95 | -0.09 | 1.05 | 0.94 / 1.52 | 0.18 / 0.09 / 0.03 | 0.12 | 0.07 | 0.99 | -0.03 | 1.00 | 543 | NO |
| RTY 2 | gex_norm tail0.33 mode=hi dir=- entry=globex | 201 | 2 | 0.74 | -0.10 | 0.67 | 0.26 / 1.74 | 0.16 / -0.13 / -0.13 | 0.05 | -0.03 | 0.84 | -0.12 | 0.50 | 289 | NO |
| RTY 3 | gex_norm tail0.33 mode=pm dir=- entry=globex | 353 | 2 | 0.60 | -0.19 | 1.03 | 1.56 / 1.40 | 0.10 / 0.17 / 0.25 | 0.13 | 0.06 | 0.99 | -0.03 | 0.50 | 541 | LEAD |
| RTY 4 | term tail0.2 mode=hi dir=+ entry=globex | 126 | 2 | 0.47 | -0.01 | 0.77 | 1.33 / 1.43 | 0.01 / 0.25 / 0.35 | 0.08 | 0.39 | 0.95 | -0.07 | 0.50 | 167 | NO |
| RTY 5 | term tail0.33 mode=pm dir=+ entry=globex | 347 | 2 | 0.38 | 0.01 | 0.99 | 1.87 / 1.31 | 0.04 / 0.35 / 0.40 | 0.13 | 0.24 | 0.99 | -0.03 | 0.50 | 550 | NO |
| RTY 6 | gex_norm tail0.33 mode=lo dir=+ entry=rth | 152 | 2 | 0.29 | -0.20 | 0.47 | 0.79 / 1.75 | 0.03 / 0.25 / 0.03 | 0.05 | 0.17 | 0.80 | -0.10 | 1.00 | 251 | NO |
| RTY 7 | gex_norm tail0.2 mode=pm dir=- entry=globex | 198 | 2 | 0.19 | -0.28 | 1.00 | 2.26 / 1.24 | -0.01 / 0.31 / 0.47 | 0.12 | 0.21 | 0.97 | -0.05 | 0.50 | 308 | NO |
| RTY 8 | gex_norm tail0.33 mode=lo dir=+ entry=globex | 152 | 2 | 0.16 | -0.16 | 0.76 | 1.98 / 1.64 | -0.01 / 0.30 / 0.43 | 0.11 | 0.11 | 0.95 | -0.06 | 0.50 | 252 | NO |
| RTY 9 (diag) | skew tail0.2 mode=lo dir=+ entry=globex | 88 | 2 | 1.40 | 0.26 | -0.36 | -1.86 / 1.64 | 0.28 / -0.21 / -1.08 | -0.12 | 0.34 | 0.35 | -0.38 | 0.00 | 161 | diag |
| RTY 10 (diag) | skew tail0.33 mode=hi dir=+ entry=globex | 190 | 1 | 1.34 | -0.04 | 1.61 | 2.33 / 1.46 | 0.19 / 0.70 / 0.08 | 0.22 | 0.04 | 1.00 | 0.07 | 0.00 | 309 | diag |
| YM 1 | term tail0.2 mode=pm dir=+ entry=globex | 229 | 2 | 0.70 | 0.11 | 0.65 | 0.29 / 1.28 | 0.08 / -0.06 / 0.18 | 0.05 | 0.22 | 0.87 | -0.10 | 0.00 | 350 | NO |
| YM 2 | skew tail0.33 mode=lo dir=+ entry=globex | 141 | 2 | 0.69 | 0.22 | 0.44 | 0.01 / 1.49 | 0.08 / 0.09 / -0.01 | 0.04 | -0.34 | 0.79 | -0.14 | 0.50 | 261 | NO |
| YM 3 | term tail0.2 mode=hi dir=+ entry=globex | 125 | 2 | 0.60 | 0.09 | 0.55 | 0.46 / 1.26 | 0.03 / 0.19 / 0.13 | 0.05 | 0.29 | 0.87 | -0.09 | 0.50 | 165 | NO |
| YM 4 | term tail0.2 mode=hi dir=+ entry=rth | 126 | 2 | 0.59 | 0.08 | 0.27 | -0.66 / 1.47 | 0.05 / 0.16 / -0.16 | -0.00 | 0.11 | 0.76 | -0.13 | 0.50 | 167 | NO |
| YM 5 | gex_norm tail0.33 mode=lo dir=+ entry=rth | 152 | 2 | 0.51 | 0.21 | 0.24 | -0.35 / 1.37 | 0.07 / 0.40 / -0.29 | 0.01 | 0.26 | 0.67 | -0.13 | 1.00 | 251 | NO |
| YM 6 | zgd tail0.33 mode=lo dir=+ entry=rth | 145 | 2 | 0.51 | 0.22 | 0.23 | -0.35 / 1.63 | 0.05 / 0.41 / -0.31 | 0.00 | 0.26 | 0.67 | -0.14 | 1.00 | 246 | NO |
| YM 7 | zgd tail0.33 mode=hi dir=+ entry=globex | 196 | 2 | 0.49 | -0.03 | 0.29 | 0.36 / 1.18 | 0.03 / -0.00 / 0.15 | 0.03 | 0.01 | 0.68 | -0.15 | 0.50 | 283 | NO |
| YM 8 | term tail0.33 mode=pm dir=+ entry=globex | 348 | 2 | 0.47 | -0.08 | 0.75 | 1.16 / 1.60 | 0.05 / 0.24 / 0.25 | 0.08 | 0.07 | 0.96 | -0.07 | 0.50 | 550 | NO |
| YM 9 | zgd tail0.33 mode=hi dir=+ entry=rth | 196 | 2 | 0.42 | -0.19 | -0.11 | -0.51 / 1.49 | -0.01 / -0.13 / -0.12 | -0.08 | -0.14 | 0.46 | -0.27 | 0.00 | 283 | NO |
| YM 10 | gex_norm tail0.33 mode=pm dir=- entry=globex | 354 | 2 | 0.40 | 0.11 | 0.28 | -0.20 / 1.44 | 0.05 / -0.03 / -0.09 | -0.01 | 0.29 | 0.75 | -0.16 | 1.00 | 541 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 38 |
| diagnostic cells read | 2 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 36 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 33 |
| plateau >= 0.75 | 9 |
| all-in uplift at 2x slippage >= +0.10 | 12 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 1 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES term tail0.33 mode=pm dir=+ entry=globex | clean | 0.43 | 0.62 | -141297 | -108504 | 543999 | -267067 | 0.72 | 33.3 | 1.48 | -87544 | 308947 | -106617 |
| ES term tail0.33 mode=pm dir=+ entry=globex | H1 | 1.89 | 4.12 | -60063 | -57448 | 147690 | -61529 | 2.62 | 42.9 | 3.17 | -63610 | 135817 | -71231 |
| ES term tail0.33 mode=pm dir=+ entry=globex | H2 | 1.69 | 3.04 | -110881 | -81329 | 227284 | -146808 | 2.22 | 41.7 | 2.83 | -77571 | 208676 | -77994 |
| ES term tail0.33 mode=pm dir=+ entry=globex | all | 0.91 | 1.41 | -127252 | -97256 | 543999 | -267067 | 2.36 | 36.9 | 2.01 | -84022 | 308947 | -106617 |
| NQ gex_norm tail0.2 mode=hi dir=- entry=rth | clean | 1.20 | 2.03 | -139220 | -95781 | 543490 | -208920 | 2.00 | 16.2 | 1.64 | -81368 | 280110 | -93813 |
| NQ gex_norm tail0.2 mode=hi dir=- entry=rth | H1 | 2.41 | 15.72 | -46422 | -34787 | 189905 | -62066 | 4.32 | 17.9 | 3.28 | -68212 | 151713 | -76932 |
| NQ gex_norm tail0.2 mode=hi dir=- entry=rth | H2 | 0.24 | 0.40 | -175474 | -113678 | 538650 | -278550 | 0.18 | 16.7 | 2.58 | -80179 | 217425 | -80705 |
| NQ gex_norm tail0.2 mode=hi dir=- entry=rth | all | 1.19 | 2.29 | -140140 | -95274 | 543490 | -278550 | 3.69 | 16.7 | 2.11 | -80665 | 280110 | -93813 |
| RTY gex_norm tail0.33 mode=pm dir=- entry=globex | clean | 0.71 | 0.99 | -149442 | -119705 | 489261 | -227596 | 1.33 | 35.2 | 1.56 | -84186 | 291223 | -104340 |
| RTY gex_norm tail0.33 mode=pm dir=- entry=globex | H1 | 2.00 | 4.26 | -82302 | -71855 | 235085 | -102247 | 1.97 | 42.9 | 2.99 | -74709 | 172080 | -77589 |
| RTY gex_norm tail0.33 mode=pm dir=- entry=globex | H2 | 1.20 | 2.43 | -80602 | -67752 | 253748 | -97697 | 1.38 | 41.7 | 2.73 | -77323 | 208330 | -86326 |
| RTY gex_norm tail0.33 mode=pm dir=- entry=globex | all | 1.03 | 1.58 | -134167 | -104366 | 489261 | -227596 | 3.00 | 38.1 | 2.05 | -82576 | 291223 | -104340 |
| YM term tail0.33 mode=pm dir=+ entry=globex | clean | 0.57 | 0.84 | -137562 | -111401 | 441259 | -250308 | 1.18 | 37.1 | 1.51 | -86660 | 278220 | -100027 |
| YM term tail0.33 mode=pm dir=+ entry=globex | H1 | 1.04 | 1.89 | -73974 | -67111 | 187097 | -91198 | 1.06 | 39.3 | 3.07 | -61426 | 133215 | -70567 |
| YM term tail0.33 mode=pm dir=+ entry=globex | H2 | 1.23 | 2.17 | -86843 | -76530 | 240063 | -92676 | 1.24 | 38.9 | 2.74 | -77737 | 199138 | -78327 |
| YM term tail0.33 mode=pm dir=+ entry=globex | all | 0.75 | 1.16 | -122722 | -98996 | 441259 | -250308 | 2.31 | 38.1 | 1.99 | -83361 | 278220 | -100027 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES term tail0.33 mode=pm dir=+ entry=globex | -16.0 | -14.4 | 17.0 | 14.6 | -15.3 / 8.7 | 43.5 / 51.7 | NO |
| NQ gex_norm tail0.2 mode=hi dir=- entry=rth | -8.1 | 4.8 | 25.0 | 30.0 | 4.1 / 22.6 | 31.2 / 44.6 | NO |
| RTY gex_norm tail0.33 mode=pm dir=- entry=globex | -14.0 | -10.3 | 17.3 | 17.4 | -11.2 / 12.5 | 30.0 / 35.6 | NO |
| YM term tail0.33 mode=pm dir=+ entry=globex | -18.9 | -2.4 | 18.3 | 25.4 | -3.3 / 9.9 | 44.8 / 51.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 skew tail0.33 mode=lo dir=+ entry=globex | positive pre-2023 | 370 | 62.4 | 33.1 | 41.9 | 29.4 | 0.14 / 0.07 / 0.09 | 393.4 / 364.1 |
| ES 2 skew tail0.33 mode=lo dir=+ entry=rth | gross-positive, cost-negative pre-2023 | 367 | 24.4 | -5.0 | 3.8 | 29.4 | 0.07 / -0.01 / 0.01 | 201.5 / 172.1 |
| ES 3 term tail0.2 mode=hi dir=+ entry=globex | positive pre-2023 | 187 | 149.4 | 120.0 | 129.5 | 29.4 | 0.19 / 0.15 / 0.16 | 284.0 / 254.7 |
| ES 4 term tail0.2 mode=pm dir=+ entry=globex | positive pre-2023 | 374 | 66.7 | 37.4 | 45.9 | 29.4 | 0.16 / 0.09 / 0.11 | 189.3 / 159.9 |
| ES 5 term tail0.33 mode=hi dir=+ entry=globex | positive pre-2023 | 332 | 57.0 | 27.7 | 36.9 | 29.4 | 0.10 / 0.05 / 0.06 | 170.6 / 141.2 |
| ES 6 term tail0.33 mode=pm dir=+ entry=globex | negative pre-2023 | 665 | -11.1 | -40.5 | -32.1 | 29.4 | -0.03 / -0.12 / -0.10 | 120.8 / 91.4 |
| ES 7 zgd tail0.33 mode=lo dir=+ entry=globex | positive pre-2023 | 352 | 117.8 | 88.5 | 96.8 | 29.4 | 0.24 / 0.18 / 0.20 | 168.0 / 138.6 |
| ES 8 gex_norm tail0.33 mode=lo dir=+ entry=globex | positive pre-2023 | 308 | 87.1 | 57.7 | 65.7 | 29.4 | 0.16 / 0.11 / 0.12 | 161.9 / 132.6 |
| ES 9 term tail0.2 mode=hi dir=+ entry=rth | positive pre-2023 | 181 | 63.7 | 34.4 | 43.6 | 29.4 | 0.11 / 0.06 / 0.07 | 146.2 / 116.9 |
| ES 10 term tail0.33 mode=lo dir=- entry=globex | negative pre-2023 | 333 | -79.0 | -108.4 | -100.9 | 29.4 | -0.28 / -0.39 / -0.36 | 69.5 / 40.2 |
| NQ 1 gex_norm tail0.2 mode=hi dir=- entry=rth | negative pre-2023 | 195 | -245.2 | -259.6 | -255.3 | 14.4 | -0.43 / -0.46 / -0.45 | 462.0 / 447.7 |
| NQ 2 skew tail0.33 mode=lo dir=+ entry=globex | positive pre-2023 | 426 | 196.7 | 182.3 | 187.5 | 14.4 | 0.33 / 0.30 / 0.31 | 468.5 / 454.1 |
| NQ 3 gex_norm tail0.2 mode=hi dir=- entry=globex | negative pre-2023 | 195 | -146.7 | -161.1 | -156.8 | 14.4 | -0.24 / -0.26 / -0.25 | 508.4 / 494.0 |
| NQ 4 zgd tail0.2 mode=hi dir=- entry=rth | negative pre-2023 | 236 | -152.1 | -166.5 | -161.8 | 14.4 | -0.28 / -0.31 / -0.30 | 318.2 / 303.9 |
| NQ 5 gex_norm tail0.2 mode=pm dir=- entry=globex | positive pre-2023 | 428 | 34.9 | 20.6 | 25.5 | 14.4 | 0.07 / 0.04 / 0.05 | 377.1 / 362.7 |
| NQ 6 gex_norm tail0.2 mode=pm dir=- entry=rth | negative pre-2023 | 422 | -35.1 | -49.5 | -44.6 | 14.4 | -0.07 / -0.10 / -0.09 | 305.0 / 290.6 |
| NQ 7 term tail0.33 mode=hi dir=+ entry=globex | positive pre-2023 | 331 | 192.6 | 178.2 | 183.6 | 14.4 | 0.24 / 0.22 / 0.23 | 448.3 / 433.9 |
| NQ 8 zgd tail0.2 mode=pm dir=- entry=rth | negative pre-2023 | 522 | -21.5 | -35.9 | -30.8 | 14.4 | -0.05 / -0.08 / -0.07 | 264.0 / 249.7 |
| NQ 9 term tail0.2 mode=hi dir=+ entry=globex | positive pre-2023 | 191 | 377.6 | 363.3 | 368.8 | 14.4 | 0.36 / 0.34 / 0.35 | 452.5 / 438.1 |
| NQ 10 term tail0.33 mode=pm dir=+ entry=globex | positive pre-2023 | 656 | 46.8 | 32.5 | 37.3 | 14.4 | 0.10 / 0.07 / 0.08 | 176.2 / 161.8 |
| RTY 1 gex_norm tail0.33 mode=pm dir=- entry=rth | gross-positive, cost-negative pre-2023 | 641 | 2.4 | -12.0 | -10.6 | 14.4 | 0.03 / -0.09 / -0.08 | 107.4 / 93.0 |
| RTY 2 gex_norm tail0.33 mode=hi dir=- entry=globex | negative pre-2023 | 338 | -6.6 | -20.9 | -19.2 | 14.4 | -0.02 / -0.10 / -0.09 | 118.4 / 104.0 |
| RTY 3 gex_norm tail0.33 mode=pm dir=- entry=globex | negative pre-2023 | 646 | -14.6 | -29.0 | -27.6 | 14.4 | -0.09 / -0.19 / -0.18 | 85.8 / 71.4 |
| RTY 4 term tail0.2 mode=hi dir=+ entry=globex | gross-positive, cost-negative pre-2023 | 185 | 9.6 | -4.8 | -2.4 | 14.4 | 0.03 / -0.01 / -0.01 | 103.4 / 89.1 |
| RTY 5 term tail0.33 mode=pm dir=+ entry=globex | positive pre-2023 | 663 | 14.8 | 0.5 | 1.8 | 14.4 | 0.11 / 0.01 / 0.02 | 68.1 / 53.7 |
| RTY 6 gex_norm tail0.33 mode=lo dir=+ entry=rth | negative pre-2023 | 302 | -23.1 | -37.4 | -36.5 | 14.4 | -0.12 / -0.20 / -0.19 | 53.4 / 39.1 |
| RTY 7 gex_norm tail0.2 mode=pm dir=- entry=globex | negative pre-2023 | 436 | -39.7 | -54.1 | -52.7 | 14.4 | -0.20 / -0.28 / -0.27 | 44.7 / 30.4 |
| RTY 8 gex_norm tail0.33 mode=lo dir=+ entry=globex | negative pre-2023 | 308 | -23.5 | -37.8 | -36.8 | 14.4 | -0.10 / -0.16 / -0.16 | 42.7 / 28.3 |
| RTY 9 (diag) skew tail0.2 mode=lo dir=+ entry=globex | positive pre-2023 | 278 | 69.5 | 55.1 | 57.1 | 14.4 | 0.32 / 0.26 / 0.26 | 191.9 / 177.5 |
| RTY 10 (diag) skew tail0.33 mode=hi dir=+ entry=globex | gross-positive, cost-negative pre-2023 | 333 | 7.5 | -6.9 | -6.0 | 14.4 | 0.04 / -0.04 / -0.03 | 201.1 / 186.7 |
| YM 1 term tail0.2 mode=pm dir=+ entry=globex | positive pre-2023 | 372 | 52.2 | 37.9 | 41.0 | 14.4 | 0.15 / 0.11 / 0.12 | 174.2 / 159.8 |
| YM 2 skew tail0.33 mode=lo dir=+ entry=globex | positive pre-2023 | 369 | 89.7 | 75.3 | 78.5 | 14.4 | 0.26 / 0.22 / 0.23 | 122.7 / 108.4 |
| YM 3 term tail0.2 mode=hi dir=+ entry=globex | positive pre-2023 | 185 | 75.5 | 61.1 | 64.7 | 14.4 | 0.11 / 0.09 / 0.09 | 200.3 / 186.0 |
| YM 4 term tail0.2 mode=hi dir=+ entry=rth | positive pre-2023 | 180 | 47.8 | 33.4 | 36.9 | 14.4 | 0.11 / 0.08 / 0.08 | 166.8 / 152.5 |
| YM 5 gex_norm tail0.33 mode=lo dir=+ entry=rth | positive pre-2023 | 301 | 79.3 | 64.9 | 67.7 | 14.4 | 0.25 / 0.21 / 0.22 | 138.1 / 123.8 |
| YM 6 zgd tail0.33 mode=lo dir=+ entry=rth | positive pre-2023 | 345 | 73.2 | 58.8 | 61.7 | 14.4 | 0.27 / 0.22 / 0.23 | 140.4 / 126.1 |
| YM 7 zgd tail0.33 mode=hi dir=+ entry=globex | gross-positive, cost-negative pre-2023 | 314 | 7.4 | -6.9 | -3.7 | 14.4 | 0.02 / -0.03 / -0.02 | 46.6 / 32.2 |
| YM 8 term tail0.33 mode=pm dir=+ entry=globex | negative pre-2023 | 663 | -7.2 | -21.6 | -18.6 | 14.4 | -0.02 / -0.08 / -0.07 | 101.0 / 86.6 |
| YM 9 zgd tail0.33 mode=hi dir=+ entry=rth | negative pre-2023 | 314 | -20.0 | -34.4 | -31.2 | 14.4 | -0.11 / -0.19 / -0.17 | 34.7 / 20.4 |
| YM 10 gex_norm tail0.33 mode=pm dir=- entry=globex | positive pre-2023 | 646 | 40.1 | 25.7 | 28.7 | 14.4 | 0.17 / 0.11 / 0.13 | 86.7 / 72.3 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 10 cells pass the clean rule against a replicate mean of 4.9 (p(count) = 0.01, p(top) = 0.89); NQ: 20 cells pass the clean rule against a replicate mean of 7.5 (p(count) = 0.00, p(top) = 0.48); RTY: 8 cells pass the clean rule against a replicate mean of 13.0 (p(count) = 0.95, p(top) = 1.00); YM: 15 cells pass the clean rule against a replicate mean of 5.5 (p(count) = 0.00, p(top) = 0.89).
- Of 38 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.21 (NQ gex_norm tail0.2 mode=hi dir=- entry=rth); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 9; 2x-slippage all-in uplift >= +0.10 for 11; gate_add PASS at some share: 1 (cell-share pairs).
- Gate-3 cell NQ gex_norm tail0.2 mode=hi dir=- entry=rth: uplift +0.18/+0.45/+0.10, boot lo +0.03, plateau 0.00, 2x-slip +0.21, wd corr -0.33, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell RTY gex_norm tail0.33 mode=pm dir=- entry=globex: uplift +0.10/+0.17/+0.25, boot lo -0.03, plateau 0.50, 2x-slip +0.13, wd corr +0.06, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 20, 'negative pre-2023': 14, 'gross-positive, cost-negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_22.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw22/ (`SW22_CO_all_selected_scored.csv`).

DONE SW22
