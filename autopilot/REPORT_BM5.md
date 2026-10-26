# REPORT BM5 - monthly reversal/continuation at month start (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 5 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.14; best pair-window standalone Sharpe +1.19.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. monthly reversal/continuation at month start. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          2 |         0 |               0.781 |                2 |          0 |            3 |
| CL    |       8 |          2 |         0 |               0.285 |                1 |          0 |            3 |
| ES    |       8 |          2 |         1 |               0.82  |                2 |          1 |            3 |
| GC    |       8 |          2 |         1 |               0.53  |                2 |          1 |            3 |
| NQ    |       8 |          2 |         1 |               0.925 |                2 |          1 |            3 |
| RTY   |       8 |          2 |         1 |               1.262 |                2 |          1 |            3 |
| YM    |       8 |          2 |         1 |               0.696 |                2 |          1 |            3 |
| ZN    |       8 |          2 |         0 |               0.179 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            0.45  |               2 |      0.4   |                       0.82  |            0.812 |           1.608 |    0.17  |       0.82  |                1.665 |
| NQ    |     200 |                    1 |            0.655 |               2 |      0.525 |                       0.854 |            0.784 |           1.385 |    0.205 |       0.854 |                1.613 |
| RTY   |     200 |                    1 |            0.62  |               3 |      0.465 |                       0.52  |            0.759 |           1.392 |    0.33  |       0.52  |                1.658 |
| YM    |     200 |                    1 |            0.545 |               2 |      0.44  |                       0.401 |            0.804 |           1.483 |    0.375 |       0.401 |                1.555 |
| GC    |     200 |                    1 |            0.585 |               3 |      0.48  |                       0.53  |            0.81  |           1.439 |    0.37  |       0.53  |                1.439 |
| CL    |     200 |                    0 |            0.595 |               3 |      1     |                     nan     |            0.696 |           1.308 |  nan     |     nan     |                1.315 |
| ZN    |     200 |                    0 |            0.23  |               2 |      1     |                     nan     |            0.564 |           1.23  |  nan     |     nan     |                1.23  |
| BTC   |     200 |                    0 |            0.565 |               3 |      1     |                     nan     |            0.843 |           1.627 |  nan     |     nan     |                1.859 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 2 | 0.82 | -1.01 | -0.03 | -1.32 / 1.32 | 0.16 / -0.26 / -0.43 | -0.04 | -0.26 | 0.47 | -0.22 | 0.00 | 116 | NO |
| ES 2 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 2 | 0.76 | -0.06 | 0.28 | -0.61 / 1.44 | 0.18 / 0.14 / -0.29 | 0.07 | -0.54 | 0.71 | -0.09 | 0.00 | 39 S | diag |
| ES 3 (diag) | first 1 trading day(s) of month dir=against prior-month ret hold=c2c | 22 | 2 | 0.59 | 0.66 | 0.66 | 0.75 / 1.58 | 0.07 / 0.39 / 0.02 | 0.09 | 0.38 | 0.90 | -0.09 | 0.00 | 36 S | diag |
| ES 4 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=c2c | 44 | 1 | 0.29 | -0.65 | 0.05 | -0.37 / 1.42 | 0.05 / -0.46 / -0.05 | -0.04 | -0.55 | 0.54 | -0.21 | 0.00 | 71 S | diag |
| NQ 1 | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 2 | 0.85 | -0.53 | 0.23 | -0.59 / 1.44 | 0.11 / -0.43 / -0.10 | -0.01 | -0.13 | 0.66 | -0.21 | 0.00 | 116 | NO |
| NQ 2 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 2 | 0.92 | 0.10 | 0.56 | -0.03 / 1.56 | 0.17 / 0.19 / -0.14 | 0.11 | -0.45 | 0.84 | -0.07 | 0.00 | 39 S | diag |
| NQ 3 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=c2c | 44 | 1 | 0.57 | -0.10 | 0.32 | 0.04 / 1.36 | 0.08 / -0.69 / 0.17 | -0.00 | -0.53 | 0.72 | -0.21 | 0.00 | 71 S | diag |
| NQ 4 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=c2c | 22 | 1 | 0.38 | -0.15 | -0.01 | -0.37 / 1.45 | 0.02 / -0.78 / -0.05 | -0.11 | -0.21 | 0.50 | -0.35 | 0.00 | 36 S | diag |
| RTY 1 | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 2 | 0.52 | -0.31 | 0.27 | -0.15 / 1.37 | 0.11 / -0.06 / -0.20 | 0.02 | -0.29 | 0.74 | -0.14 | 0.00 | 116 | NO |
| RTY 2 (diag) | first 1 trading day(s) of month dir=against prior-month ret hold=c2c | 22 | 2 | 1.26 | 0.18 | 1.19 | 1.06 / 1.35 | 0.19 / 0.12 / 0.15 | 0.16 | 0.23 | 0.99 | 0.02 | 0.00 | 36 S | diag |
| RTY 3 (diag) | first 3 trading day(s) of month dir=against prior-month ret hold=c2c | 44 | 2 | 0.76 | 0.28 | 0.69 | 0.57 / 1.08 | 0.08 / 0.20 / -0.04 | 0.06 | 0.36 | 0.91 | -0.07 | 0.00 | 71 S | diag |
| RTY 4 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 2 | 0.33 | 0.09 | 0.28 | 0.18 / 1.42 | 0.08 / 0.17 / -0.13 | 0.05 | -0.56 | 0.69 | -0.11 | 0.00 | 39 S | diag |
| YM 1 | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 2 | 0.40 | -0.86 | 0.72 | 1.17 / 1.54 | 0.08 / 0.84 / -0.07 | 0.13 | -0.37 | 0.91 | -0.04 | 0.00 | 116 | NO |
| YM 2 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 2 | 0.70 | -0.23 | 0.64 | 0.53 / 1.57 | 0.16 / 0.26 / -0.12 | 0.11 | -0.55 | 0.86 | -0.05 | 0.00 | 39 S | diag |
| YM 3 (diag) | first 1 trading day(s) of month dir=against prior-month ret hold=c2c | 22 | 2 | 0.69 | 0.58 | 0.63 | 0.56 / 1.42 | 0.08 / -0.28 / 0.05 | 0.03 | 0.42 | 0.88 | -0.15 | 0.00 | 36 S | diag |
| YM 4 (diag) | first 3 trading day(s) of month dir=against prior-month ret hold=c2c | 44 | 1 | -0.02 | 0.45 | 0.30 | 0.89 / 1.43 | -0.05 / 0.22 / 0.01 | -0.00 | 0.55 | 0.81 | -0.16 | 0.00 | 71 S | diag |
| GC 1 | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 2 | 0.53 | -0.42 | -0.37 | -0.95 / 1.54 | 0.09 / -1.58 / -0.38 | -0.26 | -0.21 | 0.30 | -0.65 | 0.00 | 117 | NO |
| GC 2 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 2 | 0.23 | 0.27 | -1.20 | -2.42 / 1.47 | 0.01 / -2.19 / -0.81 | -0.51 | -0.39 | 0.02 | -0.86 | 0.00 | 39 S | diag |
| GC 3 (diag) | first 3 trading day(s) of month dir=against prior-month ret hold=c2c | 44 | 1 | 0.17 | 0.33 | 0.33 | 0.48 / 1.57 | -0.04 / -0.92 / 0.20 | -0.09 | -0.05 | 0.74 | -0.36 | 0.00 | 72 S | diag |
| GC 4 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=c2c | 22 | 1 | 0.10 | -0.51 | 0.28 | 0.44 / 1.31 | 0.05 / -0.06 / -0.78 | -0.11 | -0.12 | 0.73 | -0.73 | 0.00 | 36 S | diag |
| CL 1 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 1 | 0.29 | 0.23 | -0.05 | -0.70 / 1.40 | 0.03 / -0.27 / -0.02 | -0.03 | -0.12 | 0.51 | -0.21 | 0.00 | 39 S | diag |
| CL 2 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 1 | 0.15 | 0.32 | 0.05 | -0.09 / 1.47 | 0.00 / 0.17 / -0.08 | -0.01 | -0.10 | 0.61 | -0.21 | 0.00 | 117 | diag |
| CL 3 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=c2c | 22 | 1 | 0.04 | 0.17 | 0.41 | 0.72 / 1.59 | -0.08 / 0.30 / -0.08 | -0.04 | -0.13 | 0.77 | -0.26 | 0.00 | 36 S | diag |
| ZN 1 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=c2c | 22 | 1 | 0.18 | -0.26 | -0.10 | -1.30 / 0.94 | -0.02 / -0.14 / -0.09 | -0.10 | 0.07 | 0.68 | -0.19 | 0.00 | 36 S | diag |
| ZN 2 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=rth | 72 | 1 | 0.09 | -0.76 | -0.27 | -1.29 / 0.56 | -0.04 / -0.42 / -0.05 | -0.17 | -0.03 | 0.78 | -0.26 | 0.00 | 117 | diag |
| ZN 3 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=c2c | 44 | 1 | -0.06 | -0.39 | -0.41 | -1.49 / 1.06 | -0.09 / -0.32 / -0.15 | -0.20 | 0.16 | 0.56 | -0.31 | 0.00 | 71 S | diag |
| BTC 1 (diag) | first 3 trading day(s) of month dir=with prior-month ret hold=c2c | 46 | 2 | 0.78 | -1.00 | 0.93 | 1.13 / 1.38 | 0.07 / 0.35 / -0.03 | 0.10 | 0.05 | 0.94 | -0.08 | 0.00 | 70 S | diag |
| BTC 2 (diag) | first 1 trading day(s) of month dir=with prior-month ret hold=rth | 24 | 1 | 0.27 | 0.68 | -0.13 | -1.27 / 1.36 | 0.08 / -0.18 / -0.17 | -0.01 | -0.55 | 0.46 | -0.16 | 0.00 | 37 S | diag |
| BTC 3 (diag) | first 1 trading day(s) of month dir=against prior-month ret hold=c2c | 23 | 1 | 0.21 | 0.15 | 0.05 | -0.15 / 1.49 | 0.08 / -0.11 / 0.03 | 0.04 | -0.56 | 0.52 | -0.15 | 0.00 | 35 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 5 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 14 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 25 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 22 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC first 3 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | clean | 0.78 | 1.92 | -92893 | -67026 | 323980 | -136259 | 2.17 | 14.3 | 1.53 | -79534 | 311541 | -86666 |
| BTC first 3 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | H1 | 1.65 | 4.67 | -165252 | -130734 | 393764 | -210580 | 2.18 | 10.7 | 3.18 | -81137 | 193829 | -83986 |
| BTC first 3 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | H2 | 0.40 | 0.69 | -75293 | -54560 | 144941 | -86235 | 0.47 | 11.1 | 2.45 | -88594 | 234672 | -94663 |
| BTC first 3 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | all | 0.93 | 2.40 | -110588 | -78099 | 393764 | -210580 | 4.14 | 13.1 | 2.00 | -82383 | 311541 | -94663 |
| CL first 3 trading day(s) of month dir=with prior-month ret hold=rth (diag) | clean | 0.15 | 0.19 | -177197 | -119967 | 419377 | -282477 | 0.33 | 11.4 | 1.46 | -81457 | 281738 | -98663 |
| CL first 3 trading day(s) of month dir=with prior-month ret hold=rth (diag) | H1 | 0.91 | 1.71 | -78011 | -57850 | 152019 | -126455 | 1.08 | 17.9 | 3.00 | -77610 | 152467 | -78287 |
| CL first 3 trading day(s) of month dir=with prior-month ret hold=rth (diag) | H2 | -0.50 | -0.64 | -251246 | -187486 | 571671 | -324940 | -0.39 | 19.4 | 2.40 | -88653 | 240469 | -94783 |
| CL first 3 trading day(s) of month dir=with prior-month ret hold=rth (diag) | all | 0.05 | 0.07 | -195989 | -133044 | 762599 | -324940 | 0.10 | 14.3 | 1.90 | -82704 | 281738 | -98663 |
| ES first 3 trading day(s) of month dir=with prior-month ret hold=rth | clean | 0.82 | 1.31 | -137096 | -90295 | 430681 | -285367 | 1.72 | 10.5 | 1.62 | -83742 | 256885 | -112375 |
| ES first 3 trading day(s) of month dir=with prior-month ret hold=rth | H1 | -0.37 | -0.50 | -95576 | -92851 | 238802 | -98294 | -0.26 | 14.3 | 2.57 | -77610 | 170284 | -78287 |
| ES first 3 trading day(s) of month dir=with prior-month ret hold=rth | H2 | -1.80 | -1.84 | -288562 | -219979 | 867058 | -292994 | -0.83 | 19.4 | 2.05 | -83164 | 192984 | -83804 |
| ES first 3 trading day(s) of month dir=with prior-month ret hold=rth | all | -0.03 | -0.04 | -187867 | -127596 | 1105860 | -292994 | -0.04 | 13.1 | 1.88 | -83274 | 256885 | -112375 |
| GC first 3 trading day(s) of month dir=with prior-month ret hold=rth | clean | 0.53 | 0.83 | -148318 | -105171 | 603865 | -211474 | 0.79 | 14.3 | 1.55 | -82743 | 251055 | -106342 |
| GC first 3 trading day(s) of month dir=with prior-month ret hold=rth | H1 | -1.99 | -2.18 | -451167 | -396833 | 1302098 | -600602 | -1.00 | 25.0 | 1.25 | -112396 | 257753 | -146504 |
| GC first 3 trading day(s) of month dir=with prior-month ret hold=rth | H2 | -0.25 | -0.30 | -605518 | -404479 | 1247584 | -882534 | -0.20 | 11.1 | 2.10 | -106410 | 180286 | -111145 |
| GC first 3 trading day(s) of month dir=with prior-month ret hold=rth | all | -0.37 | -0.44 | -375336 | -257585 | 2672777 | -882534 | -0.40 | 15.5 | 1.65 | -95776 | 368202 | -146504 |
| NQ first 3 trading day(s) of month dir=with prior-month ret hold=rth | clean | 0.85 | 1.61 | -121869 | -86827 | 485527 | -201291 | 1.59 | 15.2 | 1.57 | -85439 | 260009 | -107388 |
| NQ first 3 trading day(s) of month dir=with prior-month ret hold=rth | H1 | -1.06 | -1.29 | -154637 | -129125 | 360556 | -159565 | -0.63 | 17.9 | 2.40 | -77610 | 181655 | -78287 |
| NQ first 3 trading day(s) of month dir=with prior-month ret hold=rth | H2 | -0.39 | -0.48 | -275364 | -199745 | 506026 | -301462 | -0.35 | 11.1 | 2.39 | -81089 | 192579 | -82524 |
| NQ first 3 trading day(s) of month dir=with prior-month ret hold=rth | all | 0.23 | 0.33 | -183093 | -124552 | 866583 | -301462 | 0.42 | 14.9 | 1.89 | -83677 | 260009 | -107388 |
| RTY first 3 trading day(s) of month dir=with prior-month ret hold=rth | clean | 0.52 | 0.85 | -136088 | -96612 | 504359 | -231519 | 0.93 | 15.2 | 1.57 | -82592 | 239875 | -105476 |
| RTY first 3 trading day(s) of month dir=with prior-month ret hold=rth | H1 | 0.75 | 1.05 | -112335 | -83170 | 235810 | -197461 | 0.66 | 14.3 | 2.77 | -77610 | 140436 | -78287 |
| RTY first 3 trading day(s) of month dir=with prior-month ret hold=rth | H2 | -0.75 | -1.02 | -173750 | -125411 | 492647 | -181469 | -0.48 | 13.9 | 2.28 | -81089 | 215566 | -82524 |
| RTY first 3 trading day(s) of month dir=with prior-month ret hold=rth | all | 0.27 | 0.42 | -156377 | -105850 | 504359 | -231519 | 0.77 | 14.9 | 1.93 | -81780 | 239875 | -105476 |
| YM first 3 trading day(s) of month dir=with prior-month ret hold=rth | clean | 0.40 | 0.60 | -148467 | -104138 | 872093 | -307201 | 0.42 | 13.3 | 1.54 | -83573 | 268668 | -111358 |
| YM first 3 trading day(s) of month dir=with prior-month ret hold=rth | H1 | 2.58 | 8.46 | -58564 | -39043 | 126952 | -117128 | 5.73 | 3.6 | 3.67 | -77610 | 127487 | -78287 |
| YM first 3 trading day(s) of month dir=with prior-month ret hold=rth | H2 | 0.09 | 0.14 | -150829 | -128073 | 379386 | -171749 | 0.08 | 13.9 | 2.41 | -91742 | 201796 | -100960 |
| YM first 3 trading day(s) of month dir=with prior-month ret hold=rth | all | 0.72 | 1.21 | -149320 | -107509 | 872093 | -307201 | 1.28 | 11.9 | 2.04 | -85067 | 268668 | -111358 |
| ZN first 1 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | clean | 0.18 | 0.32 | -127685 | -97477 | 563556 | -191976 | 0.29 | 10.5 | 1.44 | -85122 | 284623 | -102410 |
| ZN first 1 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | H1 | -2.18 | -2.15 | -53919 | -47152 | 140794 | -70161 | -1.00 | 14.3 | 2.69 | -77610 | 150315 | -78287 |
| ZN first 1 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | H2 | -0.97 | -1.19 | -84373 | -60010 | 215016 | -122948 | -0.67 | 16.7 | 2.39 | -82520 | 222524 | -82524 |
| ZN first 1 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | all | -0.10 | -0.17 | -114827 | -83776 | 919367 | -191976 | -0.13 | 12.5 | 1.84 | -84017 | 284623 | -102410 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES first 3 trading day(s) of month dir=with prior-month ret hold=rth | -30.4 | -29.6 | 19.1 | 17.0 | -30.6 / 19.6 | 27.0 / 27.9 | NO |
| NQ first 3 trading day(s) of month dir=with prior-month ret hold=rth | -26.0 | -20.5 | 13.6 | 23.6 | -21.5 / 12.1 | 5.2 / 9.4 | NO |
| RTY first 3 trading day(s) of month dir=with prior-month ret hold=rth | -25.7 | -17.1 | 23.3 | 39.2 | -18.0 / 21.8 | 19.2 / 23.9 | NO |
| YM first 3 trading day(s) of month dir=with prior-month ret hold=rth | -17.8 | -27.8 | 18.3 | 10.7 | -28.8 / 19.9 | 30.0 / 30.0 | NO |
| GC first 3 trading day(s) of month dir=with prior-month ret hold=rth | -41.7 | -165.4 | -32.6 | -76.7 | -18.9 / 21.5 | -153.7 / -85.1 | NO |
| CL first 3 trading day(s) of month dir=with prior-month ret hold=rth (diag) | -29.1 | -37.4 | 11.4 | 21.3 | -38.5 / 7.1 | 30.0 / 30.0 | NO |
| ZN first 1 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | -31.3 | -11.5 | 20.4 | 27.6 | -12.4 / 17.1 | 30.0 / 30.0 | NO |
| BTC first 3 trading day(s) of month dir=with prior-month ret hold=c2c (diag) | -12.2 | -12.1 | 19.6 | 13.2 | 21.2 / 27.9 | -18.1 / 5.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 375 | -179.5 | -208.9 | -194.6 | 29.4 | -0.87 / -1.01 / -0.94 | 304.9 / 275.5 |
| ES 2 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | gross-positive, cost-negative pre-2023 | 126 | 6.7 | -22.6 | -8.3 | 29.4 | 0.02 / -0.06 / -0.02 | 533.3 / 504.0 |
| ES 3 (diag) first 1 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 116 | 355.5 | 326.1 | 340.5 | 29.4 | 0.72 / 0.66 / 0.69 | 464.2 / 434.8 |
| ES 4 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 229 | -210.2 | -239.6 | -225.2 | 29.4 | -0.57 / -0.65 / -0.61 | 240.6 / 211.3 |
| NQ 1 first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 375 | -175.0 | -189.3 | -180.7 | 14.4 | -0.49 / -0.53 / -0.50 | 601.1 / 586.8 |
| NQ 2 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 126 | 72.1 | 57.7 | 66.3 | 14.4 | 0.12 / 0.10 / 0.11 | 1261.2 / 1246.9 |
| NQ 3 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 229 | -41.1 | -55.5 | -46.9 | 14.4 | -0.07 / -0.10 / -0.08 | 688.2 / 673.8 |
| NQ 4 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 116 | -101.6 | -116.0 | -107.3 | 14.4 | -0.13 / -0.15 / -0.14 | 528.4 / 514.0 |
| RTY 1 first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 211 | -45.7 | -60.1 | -57.8 | 14.4 | -0.23 / -0.31 / -0.29 | 124.4 / 110.1 |
| RTY 2 (diag) first 1 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 64 | 89.9 | 75.6 | 77.8 | 14.4 | 0.22 / 0.18 / 0.19 | 628.4 / 614.0 |
| RTY 3 (diag) first 3 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 128 | 102.4 | 88.0 | 90.3 | 14.4 | 0.32 / 0.28 / 0.28 | 305.0 / 290.6 |
| RTY 4 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 71 | 44.3 | 29.9 | 32.2 | 14.4 | 0.14 / 0.09 / 0.10 | 152.7 / 138.3 |
| YM 1 first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 375 | -121.5 | -135.8 | -130.0 | 14.4 | -0.77 / -0.86 / -0.82 | 106.8 / 92.4 |
| YM 2 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 126 | -49.9 | -64.2 | -58.5 | 14.4 | -0.18 / -0.23 / -0.21 | 344.6 / 330.2 |
| YM 3 (diag) first 1 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 116 | 250.3 | 236.0 | 241.8 | 14.4 | 0.62 / 0.58 / 0.60 | 355.9 / 341.5 |
| YM 4 (diag) first 3 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 229 | 155.7 | 141.3 | 147.1 | 14.4 | 0.50 / 0.45 / 0.47 | 2.8 / -11.5 |
| GC 1 first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 378 | -56.0 | -80.3 | -70.5 | 24.4 | -0.29 / -0.42 / -0.37 | 176.8 / 152.4 |
| GC 2 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 126 | 108.4 | 84.1 | 93.9 | 24.4 | 0.35 / 0.27 / 0.30 | 136.3 / 111.9 |
| GC 3 (diag) first 3 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 234 | 136.2 | 111.9 | 121.7 | 24.4 | 0.40 / 0.33 / 0.36 | 118.0 / 93.6 |
| GC 4 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 118 | -208.2 | -232.6 | -222.8 | 24.4 | -0.46 / -0.51 / -0.49 | 82.3 / 57.9 |
| CL 1 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 126 | 110.6 | 86.2 | 88.8 | 24.4 | 0.30 / 0.23 / 0.24 | 164.6 / 140.2 |
| CL 2 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 378 | 95.2 | 70.9 | 73.4 | 24.4 | 0.43 / 0.32 / 0.33 | 56.1 / 31.8 |
| CL 3 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=c2c | positive pre-2023 | 118 | 101.2 | 76.8 | 79.5 | 24.4 | 0.22 / 0.17 / 0.17 | 39.5 / 15.2 |
| ZN 1 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=c2c | gross-positive, cost-negative pre-2023 | 117 | 0.3 | -35.3 | -40.6 | 35.6 | 0.00 / -0.26 / -0.30 | 63.9 / 28.3 |
| ZN 2 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=rth | negative pre-2023 | 377 | -7.5 | -43.2 | -48.3 | 35.6 | -0.13 / -0.76 / -0.85 | 42.8 / 7.1 |
| ZN 3 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 232 | -1.1 | -36.7 | -41.9 | 35.6 | -0.01 / -0.39 / -0.45 | 29.1 / -6.5 |
| BTC 1 (diag) first 3 trading day(s) of month dir=with prior-month ret hold=c2c | negative pre-2023 | 36 | -1250.7 | -1305.1 | -1273.1 | 54.4 | -0.96 / -1.00 / -0.97 | 1929.3 / 1875.0 |
| BTC 2 (diag) first 1 trading day(s) of month dir=with prior-month ret hold=rth | positive pre-2023 | 18 | 770.8 | 716.5 | 748.2 | 54.4 | 0.73 / 0.68 / 0.71 | 970.8 / 916.5 |
| BTC 3 (diag) first 1 trading day(s) of month dir=against prior-month ret hold=c2c | positive pre-2023 | 18 | 173.6 | 119.3 | 151.1 | 54.4 | 0.22 / 0.15 / 0.19 | 703.3 / 648.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 1.00); ES: 1 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 0.40, p(top) = 0.17); GC: 1 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.48, p(top) = 0.37); NQ: 1 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 0.53, p(top) = 0.20); RTY: 1 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.47, p(top) = 0.33); YM: 1 cells pass the clean rule against a replicate mean of 0.5 (p(count) = 0.44, p(top) = 0.38); ZN: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00).
- Of 5 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.14 (YM first 3 trading day(s) of month dir=with prior-month ret hold=rth); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 1; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 5}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_5.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm5/ (`BM5_CO_all_selected_scored.csv`).

DONE BM5
