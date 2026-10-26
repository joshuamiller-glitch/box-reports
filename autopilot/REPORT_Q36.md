# REPORT Q36 - Q36: opening-range breakout with relative-volume confirmation

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 14 selected cells (+27 diagnostic) scored on 10 instruments; best non-diagnostic all-in additive uplift at 20% share +0.09; best pair-window standalone Sharpe +0.89.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: opening-range breakout with relative-volume confirmation.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E, SI, HG. Grid: 288 cells per instrument = 3 bar sizes x 6 signals x 2 directions x 4 holds (60/120/180/240 min) x 2 sessions.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      48 |         48 |         0 |               0.05  |                1 |          0 |            3 |
| CL    |      48 |         48 |         0 |              -0.215 |                1 |          0 |            3 |
| ES    |      48 |         48 |         1 |               0.924 |                2 |          1 |            3 |
| GC    |      48 |         48 |         0 |               0.354 |                1 |          0 |            3 |
| HG    |      48 |         48 |         0 |               0.573 |                1 |          0 |            3 |
| HO    |      48 |         48 |         3 |               1.042 |                2 |          3 |            3 |
| NQ    |      48 |         48 |        15 |               1.878 |                2 |         10 |            0 |
| RTY   |      48 |         48 |         0 |               0.289 |                1 |          0 |            3 |
| SI    |      48 |         48 |         0 |              -0.451 |                1 |          0 |            3 |
| ZN    |      48 |         48 |         0 |              -1.22  |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            2.705 |               7 |      0.92  |                       0.814 |            0.588 |           0.961 |    0.135 |       0.814 |                1.572 |
| NQ    |     200 |                   15 |            7.96  |              16 |      0.01  |                       0.789 |            0.718 |           0.968 |    0.295 |       1.254 |                1.955 |
| RTY   |     200 |                    0 |            3.23  |              10 |      1     |                     nan     |            0.628 |           1.009 |  nan     |     nan     |                1.566 |
| GC    |     200 |                    0 |            3.4   |              10 |      1     |                     nan     |            0.623 |           1.053 |  nan     |     nan     |                1.691 |
| CL    |     200 |                    0 |            1.61  |               5 |      1     |                     nan     |            0.529 |           0.878 |  nan     |     nan     |                1.247 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| HO    |     200 |                    3 |            7.025 |              16 |      0.975 |                       0.301 |            0.713 |           0.964 |    0.99  |       0.403 |                1.867 |
| 6E    |     200 |                    0 |            0.66  |               4 |      1     |                     nan     |            0.562 |           1.135 |  nan     |     nan     |                1.21  |
| SI    |     200 |                    0 |            0.865 |               4 |      1     |                     nan     |            0.545 |           0.994 |  nan     |     nan     |                1.159 |
| HG    |     200 |                    0 |            1.52  |               5 |      1     |                     nan     |            0.515 |           0.918 |  nan     |     nan     |                1.208 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | 320 | 2 | 0.81 | -0.56 | 0.53 | 0.01 / 0.75 | 0.06 / -0.24 / -0.06 | -0.09 | 0.02 | 0.99 | -0.16 | 0.00 | 494 | NO |
| ES 2 (diag) | orvol (('or', 30), 2.5, 5, ('tr', 0.2)) | 138 | 1 | 0.92 | -0.23 | 0.89 | 0.82 / 1.12 | 0.09 / -0.10 / 0.15 | 0.03 | 0.10 | 1.00 | -0.06 | 0.00 | 197 | diag |
| ES 3 (diag) | orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | 513 | 1 | 0.69 | -0.38 | 0.50 | 0.18 / 0.94 | 0.09 / -0.01 / -0.15 | -0.05 | -0.01 | 0.97 | -0.15 | 0.50 | 824 | diag |
| ES 4 (diag) | orvol (('or', 15), 1.5, 15, ('b1', 0.2)) | 482 | 1 | 0.55 | -0.42 | 0.43 | 0.22 / 1.27 | 0.06 / -0.00 / -0.14 | -0.07 | -0.14 | 0.95 | -0.16 | 0.50 | 782 | diag |
| NQ 1 | orvol (('or', 15), 0.0, 5, ('b1', 0.1)) | 515 | 2 | 1.25 | -0.53 | 0.01 | -1.24 / 1.53 | 0.22 / -0.22 / -1.04 | -0.17 | 0.27 | 0.69 | -0.37 | 0.00 | 827 | NO |
| NQ 2 | orvol (('or', 15), 0.0, 5, ('tr', 0.2)) | 515 | 2 | 0.95 | 0.38 | 0.23 | -0.58 / 0.79 | 0.13 / -0.05 / -0.65 | -0.10 | 0.41 | 0.83 | -0.27 | 0.00 | 827 | NO |
| NQ 3 | orvol (('or', 15), 1.5, 5, ('tr', 0.2)) | 427 | 2 | 0.83 | 0.31 | 0.28 | -0.34 / 0.78 | 0.09 / 0.08 / -0.58 | -0.09 | 0.30 | 0.88 | -0.26 | 0.00 | 687 | NO |
| NQ 4 | orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | 512 | 2 | 0.79 | 0.15 | 0.77 | 0.68 / 1.28 | 0.10 / 0.65 / -0.23 | 0.07 | -0.47 | 0.92 | -0.11 | 0.50 | 820 | NO |
| NQ 5 | orvol (('or', 30), 0.0, 15, ('tr', 0.2)) | 498 | 2 | 0.76 | 0.12 | 0.42 | 0.01 / 0.91 | 0.02 / 0.05 / -0.40 | -0.09 | 0.28 | 0.93 | -0.23 | 0.00 | 793 | NO |
| NQ 6 | orvol (('or', 30), 0.0, 5, ('tr', 0.2)) | 509 | 2 | 0.72 | 0.07 | 0.54 | 0.32 / 0.92 | 0.02 / 0.15 / -0.32 | -0.06 | 0.09 | 0.95 | -0.21 | 0.00 | 810 | NO |
| NQ 7 | orvol (('or', 30), 0.0, 5, ('b1', 0.1)) | 509 | 2 | 0.68 | -0.14 | 0.37 | 0.09 / 1.25 | 0.04 / -0.19 / -0.26 | -0.08 | -0.36 | 0.86 | -0.26 | 0.00 | 810 | NO |
| NQ 8 | orvol (('or', 30), 1.5, 15, ('tr', 0.2)) | 436 | 2 | 0.66 | 0.13 | 0.43 | 0.08 / 0.84 | 0.01 / -0.11 / -0.26 | -0.09 | 0.12 | 0.92 | -0.23 | 0.00 | 686 | NO |
| NQ 9 | orvol (('or', 15), 0.0, 15, ('tr', 0.2)) | 512 | 2 | 0.63 | 0.48 | 0.52 | 0.42 / 1.19 | 0.05 / 0.24 / -0.21 | -0.01 | 0.22 | 0.97 | -0.18 | 0.00 | 820 | NO |
| NQ 10 | orvol (('or', 15), 1.5, 15, ('tr', 0.2)) | 481 | 2 | 0.61 | 0.43 | 0.61 | 0.62 / 1.10 | 0.05 / 0.17 / -0.09 | 0.01 | 0.27 | 0.98 | -0.16 | 0.00 | 770 | NO |
| RTY 1 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | 73 | 1 | 0.29 | -0.10 | 0.30 | 0.31 / 1.20 | 0.03 / -0.43 / 0.44 | 0.02 | -0.30 | 0.76 | -0.15 | 0.50 | 107 | diag |
| RTY 2 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.1)) | 73 | 1 | 0.11 | -0.12 | 0.17 | 0.26 / 1.19 | 0.03 / -0.01 / 0.19 | 0.01 | -0.34 | 0.77 | -0.14 | 0.00 | 107 | diag |
| RTY 3 (diag) | orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | 493 | 1 | 0.10 | 0.23 | 0.13 | 0.18 / 1.12 | -0.03 / 0.03 / -0.01 | -0.08 | -0.06 | 0.86 | -0.21 | 0.00 | 804 | diag |
| GC 1 (diag) | orvol (('or', 15), 1.5, 15, ('b1', 0.2)) | 384 | 1 | 0.35 | -0.82 | 0.04 | -0.17 / 1.33 | 0.01 / 0.01 / -0.90 | -0.28 | 0.37 | 0.70 | -0.55 | 0.00 | 586 | diag |
| GC 2 (diag) | orvol (('or', 30), 2.5, 5, ('tr', 0.1)) | 86 | 1 | 0.33 | -1.07 | -0.07 | -0.32 / 1.23 | -0.02 / -0.26 / -0.45 | -0.19 | 0.57 | 0.73 | -0.41 | 0.00 | 148 | diag |
| GC 3 (diag) | orvol (('or', 30), 0.0, 5, ('b1', 0.2)) | 511 | 1 | 0.27 | -1.02 | -0.42 | -0.90 / 1.55 | -0.01 / -0.72 / -1.18 | -0.43 | 0.42 | 0.36 | -0.78 | 0.00 | 815 | diag |
| CL 1 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | 132 | 0 | -0.22 | -0.02 | -0.87 | -1.71 / 1.46 | -0.08 / 0.10 / -0.84 | -0.28 | 0.47 | 0.14 | -0.44 | 0.00 | 186 | diag |
| CL 2 (diag) | orvol (('or', 15), 1.5, 5, ('b1', 0.1)) | 336 | 1 | -0.40 | -1.30 | 0.07 | 0.53 / 0.63 | -0.13 / 0.06 / 0.27 | -0.18 | -0.43 | 0.94 | -0.26 | 0.00 | 502 | diag |
| CL 3 (diag) | orvol (('or', 30), 1.5, 5, ('b1', 0.2)) | 341 | 0 | -0.46 | -0.37 | -0.93 | -1.48 / 1.11 | -0.17 / -0.11 / -0.66 | -0.36 | 0.14 | 0.21 | -0.50 | 0.00 | 506 | diag |
| ZN 1 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | 86 | 0 | -1.22 | -1.91 | -1.54 | -2.30 / -0.74 | -0.25 / -0.47 / -0.29 | -0.49 | 0.24 | 0.79 | -0.47 | 0.00 | 134 | diag |
| ZN 2 (diag) | orvol (('or', 15), 2.5, 5, ('b1', 0.2)) | 123 | 0 | -1.36 | -1.87 | -1.40 | -1.25 / -1.27 | -0.29 / -0.54 / 0.05 | -0.50 | -0.01 | 0.94 | -0.43 | 0.00 | 190 | diag |
| ZN 3 (diag) | orvol (('or', 30), 2.5, 15, ('b1', 0.2)) | 204 | 0 | -1.77 | -2.39 | -1.88 | -2.15 / -2.07 | -0.38 / -0.30 / -0.39 | -0.66 | -0.15 | 0.97 | -0.55 | 0.00 | 321 | diag |
| HO 1 | orvol (('or', 30), 2.5, 15, ('tr', 0.1)) | 453 | 2 | 0.40 | 0.09 | 0.53 | 0.72 / 1.84 | 0.08 / -0.06 / 0.18 | 0.03 | -0.35 | 0.80 | -0.15 | 0.50 | 709 | NO |
| HO 2 | orvol (('or', 30), 0.0, 15, ('tr', 0.1)) | 517 | 2 | 0.27 | 0.35 | 0.47 | 0.71 / 1.82 | 0.06 / -0.10 / 0.20 | 0.01 | -0.43 | 0.80 | -0.20 | 0.50 | 829 | NO |
| HO 3 | orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | 510 | 2 | 0.23 | 0.31 | 0.47 | 0.73 / 1.26 | 0.05 / -0.06 / 0.25 | 0.02 | -0.49 | 0.82 | -0.18 | 0.50 | 807 | NO |
| HO 4 (diag) | orvol (('or', 30), 2.5, 5, ('tr', 0.2)) | 226 | 1 | 1.04 | -0.39 | 0.58 | 0.45 / 1.33 | 0.14 / -0.33 / 0.18 | 0.07 | -0.18 | 0.88 | -0.18 | 0.50 | 358 | diag |
| HO 5 (diag) | orvol (('or', 15), 2.5, 5, ('tr', 0.2)) | 148 | 1 | 0.31 | -0.26 | 0.39 | 0.57 / 1.38 | 0.01 / 0.00 / -0.07 | -0.02 | 0.31 | 0.79 | -0.27 | 0.50 | 224 | diag |
| HO 6 (diag) | orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | 378 | 1 | 0.22 | -0.09 | 0.01 | -0.06 / 1.35 | -0.02 / -0.30 / -0.34 | -0.16 | -0.17 | 0.55 | -0.41 | 0.00 | 604 | diag |
| 6E 1 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | 71 | 1 | 0.05 | -1.83 | -0.32 | -0.92 / 0.88 | -0.01 / 0.05 / -0.34 | -0.14 | 0.21 | 0.68 | -0.26 | 0.00 | 129 | diag |
| 6E 2 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.1)) | 71 | 1 | -0.06 | -1.29 | -0.86 | -2.10 / 0.11 | -0.04 / -0.10 / -0.81 | -0.34 | -0.04 | 0.62 | -0.43 | 0.00 | 129 | diag |
| 6E 3 (diag) | orvol (('or', 30), 0.0, 15, ('b1', 0.2)) | 502 | 1 | -0.31 | -2.60 | -0.86 | -1.92 / -0.04 | -0.07 / -0.07 / -0.47 | -0.32 | 0.03 | 0.85 | -0.34 | 0.00 | 806 | diag |
| SI 1 (diag) | orvol (('or', 30), 1.5, 15, ('b1', 0.2)) | 443 | 1 | -0.45 | -0.90 | -0.19 | -0.13 / 1.43 | -0.16 / -1.06 / -0.87 | -0.58 | -0.37 | 0.52 | -1.01 | 0.00 | 703 | diag |
| SI 2 (diag) | orvol (('or', 15), 1.5, 5, ('tr', 0.1)) | 353 | 0 | -0.56 | -2.15 | -0.84 | -1.16 / 0.89 | -0.15 / 0.25 / -1.78 | -0.79 | 0.49 | 0.30 | -0.99 | 0.00 | 546 | diag |
| SI 3 (diag) | orvol (('or', 15), 2.5, 5, ('tr', 0.2)) | 177 | 0 | -0.58 | -0.85 | -0.31 | -0.24 / 1.31 | -0.15 / -0.19 / -1.13 | -0.51 | 0.47 | 0.48 | -0.75 | 0.00 | 271 | diag |
| HG 1 (diag) | orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | 125 | 1 | 0.57 | -0.93 | 0.32 | 0.02 / 1.25 | 0.08 / 0.44 / -0.51 | -0.08 | 0.26 | 0.88 | -0.25 | 0.00 | 213 | diag |
| HG 2 (diag) | orvol (('or', 15), 2.5, 5, ('b1', 0.2)) | 98 | 1 | 0.50 | -0.93 | 0.24 | -0.06 / 1.07 | 0.09 / -0.18 / -0.32 | -0.08 | 0.18 | 0.91 | -0.27 | 0.00 | 176 | diag |
| HG 3 (diag) | orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | 515 | 1 | 0.49 | -1.29 | -0.05 | -1.00 / 0.76 | 0.08 / 0.05 / -0.62 | -0.21 | -0.07 | 0.88 | -0.31 | 0.00 | 827 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 14 |
| diagnostic cells read | 27 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 8 |
| worst-decile corr <= +0.30 | 33 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 0 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | clean | 0.05 | 0.07 | -130102 | -109291 | 751894 | -177803 | 0.06 | 24.8 | 1.45 | -85741 | 285939 | -94208 |
| 6E orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | H1 | 0.48 | 0.79 | -100499 | -88378 | 263925 | -119334 | 0.41 | 35.7 | 2.88 | -82528 | 157236 | -86769 |
| 6E orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | H2 | -1.94 | -2.43 | -124369 | -108303 | 671806 | -148547 | -0.90 | 47.2 | 2.14 | -87509 | 221825 | -95312 |
| 6E orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | all | -0.32 | -0.45 | -127898 | -108024 | 800581 | -177803 | -0.57 | 31.5 | 1.82 | -86422 | 285939 | -95312 |
| CL orvol (('or', 15), 1.5, 5, ('b1', 0.1)) (diag) | clean | -0.41 | -0.55 | -131165 | -110982 | 770843 | -143953 | -0.48 | 55.2 | 1.33 | -91632 | 328603 | -97093 |
| CL orvol (('or', 15), 1.5, 5, ('b1', 0.1)) (diag) | H1 | -0.10 | -0.16 | -62622 | -54668 | 201191 | -63413 | -0.08 | 60.7 | 2.89 | -76919 | 136596 | -90970 |
| CL orvol (('or', 15), 1.5, 5, ('b1', 0.1)) (diag) | H2 | 0.75 | 1.02 | -339979 | -253285 | 876304 | -462634 | 0.59 | 44.4 | 2.76 | -64268 | 229562 | -68331 |
| CL orvol (('or', 15), 1.5, 5, ('b1', 0.1)) (diag) | all | 0.07 | 0.09 | -189025 | -145154 | 876304 | -462634 | 0.14 | 53.6 | 1.87 | -89427 | 328603 | -97093 |
| ES orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | clean | 0.81 | 1.72 | -81151 | -68686 | 318715 | -114851 | 2.30 | 56.2 | 1.52 | -81884 | 305487 | -88301 |
| ES orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | H1 | -0.50 | -0.77 | -83614 | -77320 | 362509 | -87372 | -0.27 | 60.7 | 2.59 | -74387 | 156171 | -82968 |
| ES orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | H2 | 0.34 | 0.62 | -68964 | -66360 | 239453 | -70109 | 0.43 | 52.8 | 2.42 | -90599 | 220483 | -93085 |
| ES orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | all | 0.53 | 1.03 | -80479 | -71514 | 463316 | -114851 | 1.60 | 56.0 | 1.88 | -84271 | 305487 | -93085 |
| GC orvol (('or', 30), 2.5, 5, ('tr', 0.1)) (diag) | clean | 0.29 | 0.58 | -88911 | -77945 | 559298 | -120178 | 0.47 | 40.0 | 1.44 | -86591 | 317753 | -98204 |
| GC orvol (('or', 30), 2.5, 5, ('tr', 0.1)) (diag) | H1 | 0.54 | 1.43 | -113861 | -105037 | 372399 | -134057 | 0.72 | 42.9 | 2.56 | -89410 | 163154 | -93311 |
| GC orvol (('or', 30), 2.5, 5, ('tr', 0.1)) (diag) | H2 | -0.83 | -1.20 | -289398 | -268447 | 1108734 | -313681 | -0.63 | 41.7 | 2.04 | -112457 | 280177 | -145261 |
| GC orvol (('or', 30), 2.5, 5, ('tr', 0.1)) (diag) | all | -0.07 | -0.11 | -219203 | -165864 | 1258609 | -313681 | -0.13 | 41.1 | 1.77 | -93736 | 317753 | -145261 |
| HG orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | clean | 0.57 | 0.80 | -152418 | -114658 | 565537 | -283052 | 0.91 | 31.4 | 1.54 | -84687 | 264420 | -96871 |
| HG orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | H1 | 1.09 | 1.89 | -132043 | -114171 | 229257 | -136029 | 1.35 | 39.3 | 3.26 | -57588 | 142783 | -57635 |
| HG orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | H2 | -0.61 | -0.79 | -235742 | -189000 | 648413 | -304822 | -0.45 | 44.4 | 1.97 | -127119 | 250549 | -138380 |
| HG orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | all | 0.32 | 0.44 | -179156 | -141310 | 648413 | -304822 | 0.82 | 35.7 | 1.87 | -93641 | 264420 | -138380 |
| HO orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | clean | 0.19 | 0.34 | -93741 | -83420 | 547270 | -132879 | 0.32 | 56.2 | 1.51 | -86814 | 308057 | -92742 |
| HO orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | H1 | -0.66 | -1.02 | -50537 | -48713 | 275237 | -52755 | -0.36 | 64.3 | 2.77 | -77351 | 142969 | -87301 |
| HO orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | H2 | 1.09 | 2.29 | -257190 | -229626 | 743639 | -302570 | 1.43 | 58.3 | 2.73 | -117299 | 265055 | -119335 |
| HO orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | all | 0.47 | 0.93 | -170378 | -128440 | 743639 | -302570 | 1.53 | 57.7 | 1.99 | -95136 | 308057 | -119335 |
| NQ orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | clean | 0.85 | 1.29 | -136080 | -107229 | 464806 | -204530 | 1.66 | 45.7 | 1.56 | -92295 | 289270 | -101401 |
| NQ orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | H1 | 2.82 | 5.31 | -81450 | -76764 | 215759 | -87912 | 2.78 | 32.1 | 3.48 | -66761 | 141407 | -71802 |
| NQ orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | H2 | -0.14 | -0.19 | -213278 | -182975 | 829330 | -240496 | -0.09 | 50.0 | 2.26 | -95901 | 226685 | -101047 |
| NQ orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | all | 0.77 | 1.12 | -166374 | -133356 | 829330 | -240496 | 1.56 | 44.6 | 1.99 | -92439 | 289270 | -101401 |
| RTY orvol (('or', 30), 2.5, 5, ('b1', 0.1)) (diag) | clean | 0.11 | 0.15 | -125662 | -108296 | 818716 | -149027 | 0.12 | 27.6 | 1.49 | -89087 | 283081 | -102543 |
| RTY orvol (('or', 30), 2.5, 5, ('b1', 0.1)) (diag) | H1 | -0.92 | -1.16 | -102799 | -96881 | 291483 | -108969 | -0.62 | 28.6 | 2.82 | -71126 | 141674 | -78287 |
| RTY orvol (('or', 30), 2.5, 5, ('b1', 0.1)) (diag) | H2 | 0.98 | 1.58 | -115198 | -113033 | 272929 | -115631 | 1.18 | 19.4 | 2.67 | -79830 | 192897 | -82513 |
| RTY orvol (('or', 30), 2.5, 5, ('b1', 0.1)) (diag) | all | 0.17 | 0.24 | -122401 | -109057 | 818716 | -149027 | 0.29 | 26.2 | 1.95 | -85893 | 283081 | -102543 |
| SI orvol (('or', 15), 2.5, 5, ('tr', 0.2)) (diag) | clean | -0.68 | -1.21 | -96663 | -87929 | 728379 | -112037 | -0.86 | 65.7 | 1.31 | -89179 | 301752 | -99451 |
| SI orvol (('or', 15), 2.5, 5, ('tr', 0.2)) (diag) | H1 | 0.30 | 0.49 | -141806 | -128427 | 292308 | -170850 | 0.35 | 39.3 | 2.64 | -87777 | 164907 | -98621 |
| SI orvol (('or', 15), 2.5, 5, ('tr', 0.2)) (diag) | H2 | -0.39 | -0.72 | -506139 | -425268 | 1544787 | -619485 | -0.41 | 55.6 | 1.35 | -150728 | 299081 | -161083 |
| SI orvol (('or', 15), 2.5, 5, ('tr', 0.2)) (diag) | all | -0.31 | -0.56 | -306208 | -223003 | 1898778 | -619485 | -0.61 | 59.5 | 1.48 | -107981 | 341846 | -161083 |
| ZN orvol (('or', 15), 2.5, 5, ('b1', 0.2)) (diag) | clean | -1.46 | -1.78 | -149283 | -126000 | 1709309 | -173760 | -0.79 | 45.7 | 1.17 | -90171 | 335642 | -107772 |
| ZN orvol (('or', 15), 2.5, 5, ('b1', 0.2)) (diag) | H1 | -2.67 | -2.67 | -142950 | -134449 | 648359 | -161322 | -0.86 | 39.3 | 2.29 | -74581 | 151097 | -78287 |
| ZN orvol (('or', 15), 2.5, 5, ('b1', 0.2)) (diag) | H2 | 0.12 | 0.18 | -73744 | -67889 | 273971 | -81633 | 0.09 | 30.6 | 2.54 | -82509 | 227172 | -82524 |
| ZN orvol (('or', 15), 2.5, 5, ('b1', 0.2)) (diag) | all | -1.40 | -1.68 | -144338 | -120159 | 2398483 | -173760 | -0.78 | 41.7 | 1.64 | -87546 | 335642 | -107772 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | -21.9 | 8.0 | 18.7 | 16.4 | 13.5 / 21.6 | 19.6 / 35.1 | NO |
| NQ orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | -15.8 | -8.9 | 3.5 | 10.2 | -7.7 / 3.1 | 36.7 / 39.1 | NO |
| RTY orvol (('or', 30), 2.5, 5, ('b1', 0.1)) (diag) | -27.4 | -11.6 | 13.5 | 13.3 | -12.5 / 5.9 | 30.0 / 42.5 | NO |
| GC orvol (('or', 30), 2.5, 5, ('tr', 0.1)) (diag) | -31.8 | -84.0 | -1.4 | 1.5 | 0.1 / 13.0 | -0.2 / 4.7 | NO |
| CL orvol (('or', 15), 1.5, 5, ('b1', 0.1)) (diag) | -28.6 | -1.5 | 7.3 | 4.0 | -2.3 / 3.9 | 5.7 / 31.3 | NO |
| ZN orvol (('or', 15), 2.5, 5, ('b1', 0.2)) (diag) | -50.5 | -20.9 | 10.0 | 0.3 | -21.9 / 4.2 | 17.3 / 23.0 | NO |
| HO orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | -17.5 | -56.4 | -6.0 | -0.8 | 5.5 / 10.7 | 12.7 / 29.8 | NO |
| 6E orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | -35.0 | 3.4 | 10.5 | 13.8 | 2.6 / 7.9 | 12.4 / 20.5 | NO |
| SI orvol (('or', 15), 2.5, 5, ('tr', 0.2)) (diag) | -42.6 | -139.2 | -41.1 | -59.7 | -6.9 / 9.3 | -9.0 / 10.4 | NO |
| HG orvol (('or', 30), 2.5, 5, ('b1', 0.2)) (diag) | -24.2 | -76.5 | -2.1 | 18.1 | -1.7 / 13.0 | 54.2 / 58.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 1590 | 8.1 | -21.2 | -6.9 | 29.4 | 0.22 / -0.56 / -0.18 | 79.9 / 50.5 |
| ES 2 (diag) orvol (('or', 30), 2.5, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 608 | 15.8 | -13.6 | 1.1 | 29.4 | 0.27 / -0.23 / 0.02 | 127.6 / 98.2 |
| ES 3 (diag) orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 2663 | 12.5 | -10.8 | 0.5 | 23.3 | 0.45 / -0.38 / 0.02 | 57.6 / 34.6 |
| ES 4 (diag) orvol (('or', 15), 1.5, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 2497 | 10.6 | -12.7 | -1.3 | 23.3 | 0.37 / -0.42 / -0.04 | 52.0 / 29.0 |
| NQ 1 orvol (('or', 15), 0.0, 5, ('b1', 0.1)) | negative pre-2023 | 2676 | -1.0 | -12.9 | -5.8 | 11.9 | -0.04 / -0.53 / -0.23 | 61.4 / 49.7 |
| NQ 2 orvol (('or', 15), 0.0, 5, ('tr', 0.2)) | positive pre-2023 | 2676 | 30.6 | 16.2 | 24.8 | 14.4 | 0.72 / 0.38 / 0.58 | 106.0 / 91.6 |
| NQ 3 orvol (('or', 15), 1.5, 5, ('tr', 0.2)) | positive pre-2023 | 2161 | 30.0 | 15.6 | 24.2 | 14.4 | 0.60 / 0.31 / 0.48 | 106.0 / 91.6 |
| NQ 4 orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | positive pre-2023 | 2654 | 17.8 | 5.9 | 13.0 | 11.9 | 0.45 / 0.15 / 0.33 | 80.4 / 68.5 |
| NQ 5 orvol (('or', 30), 0.0, 15, ('tr', 0.2)) | positive pre-2023 | 2567 | 19.6 | 5.3 | 13.8 | 14.4 | 0.45 / 0.12 / 0.32 | 82.8 / 68.4 |
| NQ 6 orvol (('or', 30), 0.0, 5, ('tr', 0.2)) | positive pre-2023 | 2609 | 17.5 | 3.2 | 11.7 | 14.4 | 0.41 / 0.07 / 0.27 | 82.4 / 68.0 |
| NQ 7 orvol (('or', 30), 0.0, 5, ('b1', 0.1)) | gross-positive, cost-negative pre-2023 | 2609 | 8.5 | -3.4 | 3.7 | 11.9 | 0.35 / -0.14 / 0.15 | 39.5 / 27.8 |
| NQ 8 orvol (('or', 30), 1.5, 15, ('tr', 0.2)) | positive pre-2023 | 2167 | 20.8 | 6.4 | 14.9 | 14.4 | 0.43 / 0.13 / 0.31 | 82.1 / 67.7 |
| NQ 9 orvol (('or', 15), 0.0, 15, ('tr', 0.2)) | positive pre-2023 | 2654 | 33.9 | 19.6 | 28.1 | 14.4 | 0.83 / 0.48 / 0.69 | 68.4 / 54.1 |
| NQ 10 orvol (('or', 15), 1.5, 15, ('tr', 0.2)) | positive pre-2023 | 2450 | 32.6 | 18.3 | 26.8 | 14.4 | 0.77 / 0.43 / 0.63 | 69.1 / 54.8 |
| RTY 1 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 183 | 4.7 | -7.2 | -5.3 | 11.9 | 0.07 / -0.10 / -0.07 | 29.2 / 17.3 |
| RTY 2 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.1)) | gross-positive, cost-negative pre-2023 | 183 | 7.3 | -4.5 | -2.6 | 11.8 | 0.20 / -0.12 / -0.07 | 15.3 / 3.6 |
| RTY 3 (diag) orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | positive pre-2023 | 1510 | 17.4 | 5.6 | 7.4 | 11.9 | 0.70 / 0.23 / 0.30 | 14.5 / 2.5 |
| GC 1 (diag) orvol (('or', 15), 1.5, 15, ('b1', 0.2)) | negative pre-2023 | 2138 | -7.3 | -27.0 | -19.1 | 19.7 | -0.23 / -0.82 / -0.58 | 43.0 / 23.6 |
| GC 2 (diag) orvol (('or', 30), 2.5, 5, ('tr', 0.1)) | negative pre-2023 | 882 | -0.8 | -25.2 | -15.0 | 24.4 | -0.04 / -1.07 / -0.64 | 43.0 / 18.6 |
| GC 3 (diag) orvol (('or', 30), 0.0, 5, ('b1', 0.2)) | negative pre-2023 | 2592 | -11.0 | -30.8 | -22.8 | 19.8 | -0.36 / -1.02 / -0.76 | 37.2 / 17.6 |
| CL 1 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 890 | 18.3 | -1.1 | 0.8 | 19.4 | 0.38 / -0.02 / 0.02 | 5.0 / -14.5 |
| CL 2 (diag) orvol (('or', 15), 1.5, 5, ('b1', 0.1)) | negative pre-2023 | 1916 | -1.6 | -21.1 | -19.0 | 19.5 | -0.10 / -1.30 / -1.17 | 11.9 / -7.2 |
| CL 3 (diag) orvol (('or', 30), 1.5, 5, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 1909 | 6.9 | -12.6 | -10.4 | 19.5 | 0.21 / -0.37 / -0.31 | 3.8 / -15.7 |
| ZN 1 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | negative pre-2023 | 515 | -7.5 | -36.1 | -40.1 | 28.6 | -0.44 / -1.91 / -2.09 | 5.6 / -23.5 |
| ZN 2 (diag) orvol (('or', 15), 2.5, 5, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 776 | 0.1 | -27.9 | -31.8 | 28.0 | 0.01 / -1.87 / -2.10 | 4.8 / -23.5 |
| ZN 3 (diag) orvol (('or', 30), 2.5, 15, ('b1', 0.2)) | negative pre-2023 | 1122 | -2.2 | -30.6 | -34.7 | 28.3 | -0.19 / -2.39 / -2.68 | 3.6 / -24.5 |
| HO 1 orvol (('or', 30), 2.5, 15, ('tr', 0.1)) | positive pre-2023 | 2450 | 14.5 | 1.7 | 3.3 | 12.8 | 0.70 / 0.09 / 0.16 | 21.8 / 9.0 |
| HO 2 orvol (('or', 30), 0.0, 15, ('tr', 0.1)) | positive pre-2023 | 2693 | 20.8 | 8.0 | 9.6 | 12.8 | 0.91 / 0.35 / 0.42 | 17.7 / 4.9 |
| HO 3 orvol (('or', 30), 1.5, 15, ('tr', 0.1)) | positive pre-2023 | 2649 | 20.0 | 7.2 | 8.8 | 12.8 | 0.85 / 0.31 / 0.38 | 17.1 / 4.4 |
| HO 4 (diag) orvol (('or', 30), 2.5, 5, ('tr', 0.2)) | negative pre-2023 | 1532 | -6.4 | -19.2 | -17.5 | 12.8 | -0.14 / -0.39 / -0.36 | 69.5 / 56.7 |
| HO 5 (diag) orvol (('or', 15), 2.5, 5, ('tr', 0.2)) | negative pre-2023 | 1181 | -2.2 | -14.9 | -13.4 | 12.8 | -0.04 / -0.26 / -0.23 | 28.4 / 15.7 |
| HO 6 (diag) orvol (('or', 30), 1.5, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 2283 | 8.6 | -4.1 | -2.5 | 12.8 | 0.18 / -0.09 / -0.06 | 18.3 / 5.6 |
| 6E 1 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | negative pre-2023 | 533 | -45.7 | -60.1 | -61.5 | 14.4 | -1.43 / -1.83 / -1.86 | 15.4 / 1.6 |
| 6E 2 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.1)) | negative pre-2023 | 533 | -8.6 | -22.5 | -23.8 | 13.9 | -0.51 / -1.29 / -1.36 | 12.4 / -1.0 |
| 6E 3 (diag) orvol (('or', 30), 0.0, 15, ('b1', 0.2)) | negative pre-2023 | 2573 | -25.1 | -39.4 | -40.4 | 14.3 | -1.68 / -2.60 / -2.66 | 9.6 / -4.4 |
| SI 1 (diag) orvol (('or', 30), 1.5, 15, ('b1', 0.2)) | gross-positive, cost-negative pre-2023 | 2150 | 11.9 | -30.6 | -15.8 | 42.5 | 0.35 / -0.90 / -0.47 | 14.4 / -28.2 |
| SI 2 (diag) orvol (('or', 15), 1.5, 5, ('tr', 0.1)) | gross-positive, cost-negative pre-2023 | 1761 | 6.4 | -47.9 | -29.1 | 54.4 | 0.27 / -2.15 / -1.31 | 30.5 / -23.8 |
| SI 3 (diag) orvol (('or', 15), 2.5, 5, ('tr', 0.2)) | gross-positive, cost-negative pre-2023 | 917 | 8.1 | -46.3 | -27.7 | 54.4 | 0.14 / -0.85 / -0.51 | -7.1 / -61.5 |
| HG 1 (diag) orvol (('or', 30), 2.5, 5, ('b1', 0.2)) | negative pre-2023 | 823 | -12.2 | -36.2 | -29.3 | 23.9 | -0.32 / -0.93 / -0.76 | 62.3 / 39.3 |
| HG 2 (diag) orvol (('or', 15), 2.5, 5, ('b1', 0.2)) | negative pre-2023 | 695 | -16.4 | -40.1 | -33.6 | 23.7 | -0.39 / -0.93 / -0.78 | 68.1 / 45.3 |
| HG 3 (diag) orvol (('or', 15), 0.0, 15, ('b1', 0.2)) | negative pre-2023 | 2675 | -3.8 | -27.6 | -21.2 | 23.8 | -0.18 / -1.29 / -0.99 | 46.2 / 23.1 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.7 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 1.00); ES: 1 cells pass the clean rule against a replicate mean of 2.7 (p(count) = 0.92, p(top) = 0.14); GC: 0 cells pass the clean rule against a replicate mean of 3.4 (p(count) = 1.00); HG: 0 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 1.00); HO: 3 cells pass the clean rule against a replicate mean of 7.0 (p(count) = 0.97, p(top) = 0.99); NQ: 15 cells pass the clean rule against a replicate mean of 8.0 (p(count) = 0.01, p(top) = 0.29); RTY: 0 cells pass the clean rule against a replicate mean of 3.2 (p(count) = 1.00); SI: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 14 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.09 (HO orvol (('or', 30), 1.5, 15, ('tr', 0.1))); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 11, 'gross-positive, cost-negative pre-2023': 2, 'negative pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q36.py, ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q36/ (`Q36_CO_all_selected_scored.csv`).

DONE Q36
