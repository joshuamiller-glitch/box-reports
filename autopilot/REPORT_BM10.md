# REPORT BM10 - overnight persistence (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 4 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share -0.03; best pair-window standalone Sharpe +0.64.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. overnight persistence. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          8 |         0 |               0.727 |                1 |          0 |            3 |
| CL    |       8 |          8 |         2 |               1.057 |                2 |          2 |            3 |
| ES    |       8 |          8 |         0 |               1.06  |                1 |          0 |            3 |
| GC    |       8 |          8 |         0 |               0.361 |                1 |          0 |            3 |
| NQ    |       8 |          8 |         0 |               1.046 |                1 |          0 |            3 |
| RTY   |       8 |          8 |         1 |               0.934 |                2 |          1 |            3 |
| YM    |       8 |          8 |         1 |               1.274 |                2 |          1 |            3 |
| ZN    |       8 |          8 |         0 |              -1.002 |                0 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.225 |               4 |      1     |                     nan     |            0.726 |           1.338 |   nan    |     nan     |                1.523 |
| NQ    |     200 |                    0 |            1.525 |               4 |      1     |                     nan     |            0.769 |           1.526 |   nan    |     nan     |                1.657 |
| RTY   |     200 |                    1 |            1.29  |               4 |      0.735 |                       0.934 |            0.711 |           1.248 |     0.14 |       0.934 |                1.538 |
| YM    |     200 |                    1 |            1.24  |               4 |      0.74  |                       1.274 |            0.73  |           1.41  |     0.05 |       1.274 |                1.55  |
| GC    |     200 |                    0 |            1.545 |               5 |      1     |                     nan     |            0.745 |           1.339 |   nan    |     nan     |                1.593 |
| CL    |     200 |                    2 |            1.38  |               5 |      0.365 |                       0.877 |            0.813 |           1.344 |     0.31 |       1.057 |                1.821 |
| ZN    |     200 |                    0 |            0.405 |               3 |      1     |                     nan     |            0.627 |           1.186 |   nan    |     nan     |                1.231 |
| BTC   |     200 |                    0 |            0.015 |               1 |      1     |                     nan     |            0.766 |           1.189 |   nan    |     nan     |                1.189 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 515 | 1 | 1.06 | -1.04 | 0.09 | -1.30 / 1.31 | 0.19 / -0.52 / -0.47 | -0.10 | -0.24 | 0.56 | -0.25 | 0.00 | 827 | diag |
| ES 2 (diag) | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 309 | 1 | 0.86 | -0.69 | -0.11 | -1.49 / 1.73 | 0.13 / -0.51 / -0.45 | -0.13 | -0.11 | 0.41 | -0.29 | 0.00 | 508 | diag |
| ES 3 (diag) | prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 402 | 0 | -0.18 | -0.86 | -1.00 | -2.14 / 1.63 | -0.08 / -0.04 / -0.87 | -0.31 | -0.01 | 0.04 | -0.44 | 0.00 | 655 | diag |
| NQ 1 (diag) | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 516 | 1 | 1.05 | -0.58 | 0.25 | -0.54 / 1.58 | 0.16 / -0.12 / -0.57 | -0.05 | -0.22 | 0.65 | -0.27 | 0.00 | 828 | diag |
| NQ 2 (diag) | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 315 | 1 | 0.73 | -0.35 | -0.13 | -1.04 / 1.30 | 0.11 / -0.46 / -0.53 | -0.12 | -0.18 | 0.41 | -0.35 | 0.00 | 522 | diag |
| NQ 3 (diag) | prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | 515 | 1 | 0.32 | 0.02 | 0.50 | 0.67 / 1.76 | 0.06 / -0.14 / 0.11 | 0.05 | -0.10 | 0.80 | -0.17 | 0.00 | 828 | diag |
| RTY 1 | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 511 | 2 | 0.93 | -0.44 | 0.17 | -1.07 / 1.37 | 0.14 / -0.52 / -0.23 | -0.06 | -0.22 | 0.70 | -0.21 | 0.00 | 817 | NO |
| RTY 2 (diag) | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 331 | 1 | 0.51 | -0.65 | -0.11 | -1.20 / 1.33 | 0.07 / -0.39 / -0.27 | -0.09 | -0.29 | 0.41 | -0.26 | 0.00 | 531 | diag |
| RTY 3 (diag) | prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 412 | 1 | 0.10 | -0.40 | -0.66 | -1.95 / 1.63 | -0.05 / 0.00 / -0.56 | -0.19 | -0.31 | 0.14 | -0.35 | 0.00 | 664 | diag |
| RTY 4 (diag) | prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 513 | 1 | 0.05 | -0.29 | -0.67 | -1.97 / 1.51 | -0.06 / 0.03 / -0.61 | -0.20 | -0.37 | 0.15 | -0.34 | 0.00 | 823 | diag |
| YM 1 | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 296 | 2 | 1.27 | -0.40 | -0.03 | -1.63 / 1.33 | 0.23 / -0.44 / -0.70 | -0.09 | -0.29 | 0.47 | -0.28 | 0.00 | 495 | NO |
| YM 2 (diag) | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 511 | 1 | 0.97 | -0.65 | -0.14 | -1.62 / 1.46 | 0.19 / -0.35 / -0.72 | -0.12 | -0.36 | 0.46 | -0.29 | 0.00 | 822 | diag |
| YM 3 (diag) | prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 404 | 1 | 0.07 | -0.55 | -0.60 | -1.35 / 1.63 | -0.04 / -0.36 / -0.57 | -0.23 | -0.11 | 0.13 | -0.40 | 0.00 | 649 | diag |
| YM 4 (diag) | prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 511 | 1 | -0.25 | -0.53 | -0.87 | -1.55 / 1.40 | -0.09 / -0.30 / -0.77 | -0.30 | -0.00 | 0.06 | -0.48 | 0.00 | 823 | diag |
| GC 1 (diag) | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 378 | 1 | 0.36 | -0.39 | -0.29 | -0.77 / 1.46 | 0.12 / -0.73 / -0.77 | -0.21 | -0.11 | 0.29 | -0.50 | 0.00 | 599 | diag |
| GC 2 (diag) | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 507 | 1 | 0.22 | -0.50 | -0.64 | -1.31 / 1.63 | 0.08 / -0.71 / -1.23 | -0.36 | -0.00 | 0.13 | -0.66 | 0.00 | 817 | diag |
| GC 3 (diag) | prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | 414 | 1 | 0.12 | -0.50 | 0.11 | 0.10 / 1.65 | -0.08 / -1.43 / 0.57 | -0.16 | 0.20 | 0.58 | -0.53 | 0.00 | 658 | diag |
| CL 1 | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 514 | 2 | 1.06 | -0.41 | -0.70 | -2.06 / 1.48 | 0.19 / -0.10 / -1.70 | -0.37 | 0.19 | 0.14 | -0.68 | 0.00 | 824 | NO |
| CL 2 | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 369 | 2 | 0.70 | -0.66 | -0.75 | -1.86 / 1.46 | 0.12 / -0.11 / -1.60 | -0.40 | 0.12 | 0.12 | -0.71 | 0.00 | 602 | NO |
| CL 3 (diag) | prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | 515 | 1 | -0.20 | -0.34 | 0.09 | 0.31 / 1.27 | -0.06 / -0.13 / -0.09 | -0.13 | 0.19 | 0.64 | -0.30 | 0.00 | 825 | diag |
| CL 4 (diag) | prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 421 | 1 | -0.32 | -0.27 | -0.69 | -0.99 / 1.38 | -0.10 / -0.14 / -0.59 | -0.27 | -0.26 | 0.15 | -0.50 | 0.00 | 676 | diag |
| CL 5 (diag) | prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | 421 | 1 | -0.38 | -0.39 | 0.18 | 0.62 / 1.26 | -0.09 / -0.10 / 0.00 | -0.12 | 0.26 | 0.70 | -0.30 | 0.00 | 676 | diag |
| ZN 1 (diag) | prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 427 | 0 | -1.00 | -2.18 | -1.98 | -3.93 / 0.72 | -0.24 / -0.65 / -0.68 | -0.72 | 0.19 | 0.02 | -0.58 | 0.00 | 685 | diag |
| ZN 2 (diag) | prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | 395 | 0 | -1.13 | -1.84 | -1.77 | -3.08 / 0.59 | -0.28 / -0.44 / -0.55 | -0.61 | 0.00 | 0.03 | -0.55 | 0.00 | 631 | diag |
| ZN 3 (diag) | prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 503 | 0 | -1.26 | -2.48 | -2.09 | -3.89 / 0.57 | -0.26 / -0.74 / -0.60 | -0.75 | 0.09 | 0.04 | -0.57 | 0.00 | 809 | diag |
| BTC 1 (diag) | prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | 409 | 1 | 0.73 | -1.15 | 0.64 | 0.45 / 1.40 | 0.13 / 0.31 / 0.06 | 0.11 | 0.31 | 0.92 | -0.05 | 0.00 | 626 | diag |
| BTC 2 (diag) | prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | 335 | 1 | 0.67 | -1.31 | 0.40 | -0.14 / 1.41 | 0.12 / 0.19 / -0.09 | 0.06 | 0.39 | 0.78 | -0.10 | 0.50 | 519 | diag |
| BTC 3 (diag) | prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | 354 | 1 | 0.36 | 0.07 | -0.10 | -0.89 / 1.28 | 0.04 / -0.55 / -0.05 | -0.07 | -0.34 | 0.46 | -0.23 | 0.00 | 536 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 4 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 3 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 0 |
| worst-decile corr <= +0.30 | 26 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | clean | 0.74 | 1.09 | -123964 | -107350 | 631946 | -143808 | 1.06 | 40.0 | 1.59 | -92722 | 270088 | -108711 |
| BTC prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | H1 | 1.08 | 2.02 | -91880 | -82245 | 255449 | -107632 | 1.03 | 46.4 | 3.14 | -64084 | 141269 | -75704 |
| BTC prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | H2 | -0.21 | -0.31 | -108211 | -73564 | 292045 | -128494 | -0.17 | 61.1 | 2.55 | -82609 | 200624 | -82616 |
| BTC prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | all | 0.64 | 0.98 | -120091 | -101794 | 631946 | -143808 | 1.40 | 45.8 | 2.03 | -88726 | 270088 | -108711 |
| CL prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | clean | 1.11 | 1.68 | -132926 | -103734 | 524486 | -231438 | 1.92 | 39.0 | 1.65 | -90594 | 261078 | -124626 |
| CL prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | H1 | -0.75 | -1.10 | -72129 | -69628 | 242327 | -78785 | -0.54 | 57.1 | 2.73 | -71219 | 145941 | -81134 |
| CL prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | H2 | -2.72 | -2.77 | -515078 | -432348 | 2767316 | -664474 | -0.96 | 58.3 | 0.79 | -154943 | 313988 | -212548 |
| CL prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | all | -0.70 | -0.80 | -350770 | -252698 | 3129750 | -664474 | -0.57 | 46.4 | 1.59 | -104992 | 313988 | -212548 |
| ES prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 (diag) | clean | 1.07 | 1.80 | -118350 | -92415 | 431376 | -190311 | 2.26 | 46.7 | 1.65 | -86936 | 246284 | -105549 |
| ES prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 (diag) | H1 | -1.65 | -2.04 | -106918 | -94283 | 360887 | -120757 | -0.91 | 60.7 | 2.31 | -75022 | 176641 | -75483 |
| ES prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 (diag) | H2 | -1.18 | -1.44 | -190913 | -169532 | 916871 | -194644 | -0.55 | 55.6 | 2.01 | -101268 | 227674 | -112308 |
| ES prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 (diag) | all | 0.09 | 0.13 | -151152 | -120265 | 1039363 | -194644 | 0.14 | 51.2 | 1.85 | -90107 | 246284 | -112308 |
| GC prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 (diag) | clean | 0.16 | 0.27 | -114003 | -97214 | 393394 | -146820 | 0.37 | 56.2 | 1.38 | -93521 | 295554 | -109232 |
| GC prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 (diag) | H1 | -1.27 | -1.47 | -624503 | -480122 | 1562130 | -910708 | -0.72 | 60.7 | 1.39 | -151597 | 337595 | -193361 |
| GC prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 (diag) | H2 | 1.64 | 2.87 | -268488 | -214926 | 723156 | -356862 | 1.79 | 44.4 | 3.05 | -95371 | 242599 | -104408 |
| GC prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 (diag) | all | 0.11 | 0.15 | -294406 | -215319 | 1816705 | -910708 | 0.18 | 54.8 | 1.76 | -107998 | 337595 | -193361 |
| NQ prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | clean | 0.35 | 0.51 | -130404 | -108665 | 417809 | -209779 | 0.76 | 45.7 | 1.51 | -84344 | 267137 | -93704 |
| NQ prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | H1 | 0.42 | 0.64 | -121448 | -104118 | 365606 | -138476 | 0.29 | 50.0 | 2.69 | -93439 | 197038 | -97816 |
| NQ prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | H2 | 0.80 | 1.32 | -182973 | -165523 | 726587 | -200332 | 0.65 | 47.2 | 2.59 | -102421 | 267729 | -110538 |
| NQ prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | all | 0.50 | 0.77 | -156146 | -128403 | 726587 | -209779 | 1.23 | 47.0 | 1.96 | -90963 | 267729 | -110538 |
| RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | clean | 0.90 | 1.37 | -146509 | -106332 | 481259 | -187598 | 1.71 | 47.6 | 1.59 | -90472 | 283495 | -104470 |
| RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | H1 | -2.25 | -2.56 | -81089 | -76323 | 378885 | -94496 | -1.00 | 64.3 | 2.31 | -78768 | 171084 | -79132 |
| RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | H2 | -0.55 | -0.70 | -149314 | -144403 | 531511 | -158252 | -0.36 | 44.4 | 2.26 | -96288 | 203414 | -107643 |
| RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | all | 0.17 | 0.24 | -151948 | -116070 | 742188 | -187598 | 0.34 | 49.4 | 1.87 | -90697 | 283495 | -107643 |
| YM prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | clean | 1.26 | 2.26 | -116133 | -87544 | 290062 | -215447 | 3.94 | 41.0 | 1.69 | -87967 | 252219 | -98120 |
| YM prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | H1 | -0.87 | -1.07 | -132745 | -122789 | 316145 | -149667 | -0.60 | 50.0 | 2.39 | -75664 | 172763 | -78287 |
| YM prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | H2 | -2.06 | -2.36 | -250503 | -211776 | 1188014 | -299800 | -0.85 | 61.1 | 1.78 | -107812 | 200792 | -119895 |
| YM prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | all | -0.03 | -0.04 | -178274 | -138053 | 1450039 | -299800 | -0.04 | 47.0 | 1.83 | -91302 | 252219 | -119895 |
| ZN prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 (diag) | clean | -1.16 | -1.45 | -139104 | -113504 | 1226919 | -250483 | -0.86 | 58.1 | 1.18 | -87600 | 388407 | -93467 |
| ZN prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 (diag) | H1 | -2.82 | -3.24 | -79236 | -74661 | 512587 | -91944 | -0.84 | 75.0 | 2.39 | -79800 | 159561 | -83121 |
| ZN prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 (diag) | H2 | -3.27 | -3.30 | -159918 | -127696 | 963181 | -186549 | -0.91 | 69.4 | 1.94 | -84065 | 216847 | -85302 |
| ZN prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 (diag) | all | -1.77 | -2.09 | -140372 | -113559 | 2457226 | -250483 | -0.96 | 63.1 | 1.53 | -86317 | 388407 | -93467 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 (diag) | -28.4 | -26.9 | 5.3 | 26.5 | -17.9 / 12.2 | 26.9 / 27.9 | NO |
| NQ prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | -20.2 | -25.9 | 4.8 | 15.3 | 3.6 / 15.8 | -8.8 / -0.6 | NO |
| RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | -27.3 | -18.4 | 5.8 | 15.1 | -15.9 / 5.9 | 28.4 / 27.8 | NO |
| YM prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | -30.6 | -40.7 | 0.5 | 26.7 | -4.4 / 10.2 | 19.1 / 23.8 | NO |
| GC prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 (diag) | -26.5 | -240.6 | -36.6 | -48.6 | -22.1 / 0.9 | -259.0 / -147.6 | NO |
| CL prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | -49.3 | -209.1 | -37.4 | -64.1 | -50.3 / 6.4 | 23.2 / 37.1 | NO |
| ZN prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 (diag) | -55.8 | -7.6 | 10.9 | -41.1 | -8.5 / 5.6 | 20.7 / 25.8 | NO |
| BTC prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 (diag) | -20.3 | -18.2 | 8.6 | 34.1 | -19.2 / -0.4 | 33.6 / 43.1 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2639 | -32.1 | -61.5 | -47.3 | 29.4 | -0.55 / -1.04 / -0.80 | 127.6 / 98.3 |
| ES 2 (diag) prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1702 | -27.1 | -56.5 | -42.3 | 29.4 | -0.33 / -0.69 / -0.51 | 130.8 / 101.4 |
| ES 3 (diag) prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2115 | -28.1 | -57.5 | -43.3 | 29.4 | -0.42 / -0.86 / -0.65 | 11.0 / -18.4 |
| NQ 1 (diag) prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2660 | -34.1 | -48.5 | -39.9 | 14.4 | -0.41 / -0.58 / -0.48 | 187.0 / 172.7 |
| NQ 2 (diag) prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1614 | -24.4 | -38.7 | -30.2 | 14.4 | -0.22 / -0.35 / -0.28 | 176.2 / 161.9 |
| NQ 3 (diag) prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | positive pre-2023 | 2679 | 16.1 | 1.8 | 10.3 | 14.4 | 0.20 / 0.02 / 0.13 | 65.6 / 51.2 |
| RTY 1 prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1510 | -5.0 | -19.3 | -17.1 | 14.4 | -0.12 / -0.44 / -0.39 | 68.3 / 53.9 |
| RTY 2 (diag) prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 918 | -22.1 | -36.4 | -34.2 | 14.4 | -0.39 / -0.65 / -0.61 | 52.0 / 37.6 |
| RTY 3 (diag) prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1246 | -3.9 | -18.2 | -16.0 | 14.4 | -0.09 / -0.40 / -0.35 | 17.8 / 3.5 |
| RTY 4 (diag) prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | gross-positive, cost-negative pre-2023 | 1525 | 2.6 | -11.7 | -9.5 | 14.4 | 0.06 / -0.29 / -0.23 | 14.8 / 0.4 |
| YM 1 prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1694 | -11.5 | -25.9 | -20.1 | 14.4 | -0.18 / -0.40 / -0.31 | 113.0 / 98.7 |
| YM 2 (diag) prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2659 | -16.4 | -30.7 | -25.0 | 14.4 | -0.35 / -0.65 / -0.53 | 73.6 / 59.3 |
| YM 3 (diag) prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2081 | -14.2 | -28.6 | -22.9 | 14.4 | -0.27 / -0.55 / -0.44 | 14.7 / 0.4 |
| YM 4 (diag) prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2675 | -10.7 | -25.1 | -19.4 | 14.4 | -0.23 / -0.53 / -0.41 | -1.8 / -16.1 |
| GC 1 (diag) prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1849 | -5.2 | -29.6 | -19.7 | 24.4 | -0.07 / -0.39 / -0.26 | 86.3 / 61.9 |
| GC 2 (diag) prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2628 | -9.5 | -33.8 | -24.1 | 24.4 | -0.14 / -0.50 / -0.36 | 52.2 / 27.8 |
| GC 3 (diag) prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | negative pre-2023 | 2088 | -12.4 | -36.8 | -27.0 | 24.4 | -0.17 / -0.50 / -0.36 | 48.8 / 24.5 |
| CL 1 prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2633 | -2.8 | -27.1 | -24.5 | 24.4 | -0.04 / -0.41 / -0.37 | 93.6 / 69.2 |
| CL 2 prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1858 | -29.4 | -53.8 | -51.2 | 24.4 | -0.36 / -0.66 / -0.63 | 75.9 / 51.5 |
| CL 3 (diag) prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | gross-positive, cost-negative pre-2023 | 2648 | 2.2 | -22.2 | -19.5 | 24.4 | 0.04 / -0.34 / -0.30 | 15.9 / -8.5 |
| CL 4 (diag) prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | gross-positive, cost-negative pre-2023 | 2122 | 4.5 | -19.9 | -17.3 | 24.4 | 0.06 / -0.27 / -0.24 | -3.9 / -28.3 |
| CL 5 (diag) prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | negative pre-2023 | 2122 | -4.5 | -28.8 | -26.3 | 24.4 | -0.06 / -0.39 / -0.35 | 3.9 / -20.5 |
| ZN 1 (diag) prior_cc sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2186 | -7.8 | -43.4 | -48.5 | 35.6 | -0.39 / -2.18 / -2.43 | 15.3 / -20.3 |
| ZN 2 (diag) prior_on sign thr=0.15ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 1995 | -1.0 | -36.6 | -41.7 | 35.6 | -0.05 / -1.84 / -2.10 | 6.1 / -29.5 |
| ZN 3 (diag) prior_cc sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | negative pre-2023 | 2619 | -9.5 | -45.1 | -50.2 | 35.6 | -0.52 / -2.48 / -2.77 | 12.1 / -23.5 |
| BTC 1 (diag) prior_cc sign thr=0.0ATR dir=against entry 18:01 exit 09:25 | negative pre-2023 | 226 | -287.5 | -341.9 | -309.5 | 54.4 | -0.97 / -1.15 / -1.04 | 442.8 / 388.4 |
| BTC 2 (diag) prior_cc sign thr=0.15ATR dir=against entry 18:01 exit 09:25 | negative pre-2023 | 177 | -427.4 | -481.8 | -449.8 | 54.4 | -1.17 / -1.31 / -1.23 | 475.2 / 420.9 |
| BTC 3 (diag) prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25 | positive pre-2023 | 195 | 76.5 | 22.2 | 54.7 | 54.4 | 0.23 / 0.07 / 0.17 | 221.3 / 166.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00); CL: 2 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.36, p(top) = 0.31); ES: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 1.00); NQ: 0 cells pass the clean rule against a replicate mean of 1.5 (p(count) = 1.00); RTY: 1 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.73, p(top) = 0.14); YM: 1 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 0.74, p(top) = 0.05); ZN: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00).
- Of 4 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift -0.03 (RTY prior_on sign thr=0.0ATR dir=with entry 18:01 exit 09:25); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 4}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_10.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm10/ (`BM10_CO_all_selected_scored.csv`).

DONE BM10
