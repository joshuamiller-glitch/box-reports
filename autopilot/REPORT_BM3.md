# REPORT BM3 - Faber SMA timing (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 6 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +0.71.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. Faber SMA timing. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          5 |         0 |               0.114 |                1 |          0 |            3 |
| CL    |       8 |          8 |         0 |              -0.29  |                1 |          0 |            3 |
| ES    |       8 |          5 |         1 |               0.587 |                2 |          1 |            3 |
| GC    |       8 |          4 |         2 |               1.379 |                2 |          2 |            3 |
| NQ    |       8 |          5 |         0 |               0.564 |                1 |          0 |            3 |
| RTY   |       8 |          7 |         1 |               0.899 |                2 |          1 |            3 |
| YM    |       8 |          6 |         2 |               0.41  |                2 |          2 |            3 |
| ZN    |       8 |          7 |         0 |              -0.518 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            1.975 |               5 |      0.935 |                       0.587 |            0.692 |           1.103 |    0.635 |       0.587 |                1.421 |
| NQ    |     200 |                    0 |            1.825 |               5 |      1     |                     nan     |            0.742 |           1.225 |  nan     |     nan     |                1.506 |
| RTY   |     200 |                    1 |            1.705 |               5 |      0.885 |                       0.609 |            0.627 |           1.11  |    0.45  |       0.609 |                1.493 |
| YM    |     200 |                    2 |            1.94  |               4 |      0.67  |                       0.367 |            0.678 |           1.161 |    0.86  |       0.41  |                1.316 |
| GC    |     200 |                    2 |            2.07  |               5 |      0.66  |                       0.454 |            0.904 |           1.605 |    0.885 |       0.492 |                1.988 |
| CL    |     200 |                    0 |            1.325 |               4 |      1     |                     nan     |            0.649 |           1.221 |  nan     |     nan     |                1.404 |
| ZN    |     200 |                    0 |            0.16  |               2 |      1     |                     nan     |            0.438 |           0.87  |  nan     |     nan     |                0.87  |
| BTC   |     200 |                    0 |            2.11  |               6 |      1     |                     nan     |            0.795 |           1.376 |  nan     |     nan     |                1.829 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | SMA200 timing above_long hold=c2c | 213 | 2 | 0.59 | 0.13 | 0.71 | 0.92 / 1.93 | 0.06 / 0.39 / 0.14 | 0.09 | -0.06 | 0.73 | -0.10 | 0.50 | 354 | NO |
| ES 2 (diag) | SMA100 timing above_long hold=c2c | 193 | 1 | 0.02 | 0.01 | 0.10 | 0.25 / 1.91 | -0.05 / 0.31 / -0.11 | -0.05 | -0.03 | 0.26 | -0.24 | 0.00 | 325 | diag |
| ES 3 (diag) | SMA100 timing above_long hold=rth | 409 | 1 | -0.23 | -0.10 | -0.44 | -0.58 / 1.33 | -0.09 / -0.03 / -0.30 | -0.18 | 0.40 | 0.05 | -0.33 | 0.00 | 683 | diag |
| ES 4 (diag) | SMA200 timing above_long hold=rth | 449 | 1 | -0.36 | -0.13 | -0.22 | 0.10 / 1.47 | -0.12 / 0.13 / -0.13 | -0.14 | 0.58 | 0.17 | -0.29 | 0.00 | 745 | diag |
| NQ 1 (diag) | SMA200 timing below_short hold=c2c | 30 | 1 | 0.56 | 0.02 | 0.67 | 0.93 / 1.22 | 0.06 / 0.00 / 0.08 | 0.05 | -0.12 | 0.96 | -0.07 | 0.00 | 40 S | diag |
| NQ 2 (diag) | SMA100 timing below_short hold=c2c | 61 | 1 | 0.23 | -0.07 | -0.36 | -1.32 / 1.01 | -0.01 / -0.21 / -0.36 | -0.12 | -0.23 | 0.41 | -0.29 | 0.00 | 93 S | diag |
| NQ 3 (diag) | SMA100 timing above_long hold=c2c | 190 | 1 | -0.00 | 0.24 | -0.20 | -0.41 / 1.41 | -0.05 / -0.06 / -0.33 | -0.12 | -0.24 | 0.09 | -0.35 | 0.00 | 311 | diag |
| RTY 1 | SMA100 timing above_long hold=c2c | 143 | 2 | 0.61 | -0.50 | 0.66 | 0.79 / 1.46 | 0.12 / 0.46 / 0.03 | 0.13 | -0.09 | 0.91 | -0.07 | 0.50 | 266 | NO |
| RTY 2 (diag) | SMA200 timing below_short hold=c2c | 81 | 1 | 0.90 | -0.11 | 0.30 | -1.65 / 0.95 | 0.12 / -0.02 / -0.26 | 0.00 | -0.47 | 0.81 | -0.14 | 1.00 | 89 S | diag |
| RTY 3 (diag) | SMA100 timing below_short hold=c2c | 114 | 1 | 0.56 | -0.23 | 0.46 | 0.23 / 0.91 | 0.06 / -0.24 / 0.09 | 0.02 | -0.33 | 0.91 | -0.13 | 0.50 | 142 | diag |
| RTY 4 (diag) | SMA200 timing above_long hold=c2c | 168 | 1 | -0.22 | -0.62 | -0.09 | 0.10 / 1.79 | -0.08 / 0.74 / -0.47 | -0.08 | -0.45 | 0.45 | -0.28 | 0.00 | 310 | diag |
| YM 1 | SMA100 timing above_long hold=c2c | 166 | 2 | 0.41 | -0.14 | 0.66 | 1.03 / 1.89 | 0.02 / 0.73 / 0.31 | 0.13 | -0.10 | 0.76 | -0.10 | 1.00 | 290 | NO |
| YM 2 | SMA200 timing above_long hold=c2c | 190 | 2 | 0.32 | 0.00 | 0.64 | 1.08 / 2.09 | -0.02 / 0.68 / 0.24 | 0.08 | -0.18 | 0.71 | -0.13 | 0.50 | 330 | NO |
| YM 3 (diag) | SMA100 timing below_short hold=c2c | 86 | 1 | 0.25 | -0.39 | -0.09 | -1.05 / 1.02 | -0.02 / -0.05 / -0.17 | -0.08 | -0.16 | 0.74 | -0.21 | 0.00 | 114 | diag |
| YM 4 (diag) | SMA100 timing above_long hold=rth | 343 | 1 | 0.15 | -0.01 | -0.10 | -0.23 / 1.66 | -0.01 / 0.73 / -0.49 | -0.05 | 0.23 | 0.21 | -0.24 | 0.00 | 603 | diag |
| YM 5 (diag) | SMA200 timing above_long hold=rth | 399 | 1 | 0.13 | -0.05 | -0.08 | -0.17 / 1.53 | -0.03 / 0.75 / -0.48 | -0.07 | 0.31 | 0.20 | -0.26 | 0.00 | 694 | diag |
| GC 1 | SMA100 timing above_long hold=rth | 439 | 2 | 0.49 | -0.46 | -0.38 | -0.91 / 1.07 | 0.08 / -0.36 / -1.05 | -0.26 | -0.17 | 0.26 | -0.58 | 0.00 | 622 | NO |
| GC 2 | SMA200 timing above_long hold=rth | 450 | 2 | 0.42 | -0.48 | -0.28 | -0.65 / 1.10 | 0.06 / -0.23 / -0.87 | -0.21 | -0.21 | 0.28 | -0.53 | 0.00 | 666 | NO |
| GC 3 (diag) | SMA100 timing above_long hold=c2c | 210 | 1 | 1.38 | -0.18 | 0.59 | 0.16 / 1.67 | 0.20 / -0.14 / -0.24 | 0.06 | -0.16 | 0.64 | -0.25 | 0.00 | 300 | diag |
| GC 4 (diag) | SMA200 timing above_long hold=c2c | 216 | 1 | 0.78 | 0.22 | 0.25 | -0.05 / 1.61 | 0.10 / -0.11 / -0.38 | -0.04 | -0.19 | 0.45 | -0.33 | 0.00 | 321 | diag |
| GC 5 (diag) | SMA100 timing below_short hold=rth | 78 | 1 | -0.07 | -0.46 | 0.18 | 0.27 / 1.63 | -0.00 / -0.56 / -0.44 | -0.21 | -0.49 | 0.67 | -0.65 | 0.00 | 206 | diag |
| CL 1 (diag) | SMA100 timing below_short hold=rth | 258 | 1 | -0.29 | 0.08 | -0.64 | -1.47 / 0.95 | -0.06 / 0.00 / -0.48 | -0.18 | 0.29 | 0.28 | -0.31 | 0.00 | 389 | diag |
| CL 2 (diag) | SMA200 timing below_short hold=rth | 231 | 1 | -0.40 | 0.02 | -0.58 | -1.09 / 0.83 | -0.07 / -0.10 / -0.25 | -0.15 | 0.04 | 0.26 | -0.27 | 0.00 | 338 | diag |
| CL 3 (diag) | SMA100 timing below_short hold=c2c | 126 | 0 | -0.71 | 0.18 | -1.05 | -1.48 / 0.83 | -0.16 / -0.09 / -0.79 | -0.30 | -0.36 | 0.07 | -0.51 | 0.00 | 188 | diag |
| ZN 1 (diag) | SMA200 timing below_short hold=c2c | 173 | 1 | -0.52 | -0.26 | -0.34 | 0.08 / 0.47 | -0.12 / -0.07 / 0.07 | -0.22 | 0.42 | 0.78 | -0.26 | 0.00 | 254 | diag |
| ZN 2 (diag) | SMA100 timing below_short hold=c2c | 137 | 1 | -0.54 | -0.40 | -0.01 | 0.88 / 0.49 | -0.15 / -0.02 / 0.17 | -0.21 | 0.26 | 0.94 | -0.25 | 0.00 | 234 | diag |
| ZN 3 (diag) | SMA100 timing above_long hold=c2c | 118 | 0 | -0.80 | -0.64 | -1.02 | -1.56 / -0.05 | -0.20 / -0.48 / -0.17 | -0.34 | 0.35 | 0.55 | -0.41 | 0.00 | 172 | diag |
| BTC 1 (diag) | SMA100 timing above_long hold=c2c | 155 | 1 | 0.11 | -0.58 | -0.23 | -1.08 / 0.66 | -0.02 / -0.25 / -0.16 | -0.10 | -0.01 | 0.27 | -0.24 | 0.00 | 198 | diag |
| BTC 2 (diag) | SMA100 timing below_short hold=rth | 175 | 1 | -0.23 | -1.05 | 0.07 | 0.36 / 1.44 | -0.05 / 0.25 / -0.27 | -0.04 | -0.52 | 0.62 | -0.24 | 0.00 | 377 | diag |
| BTC 3 (diag) | SMA200 timing above_long hold=c2c | 196 | 1 | -0.38 | -0.29 | -0.52 | -0.87 / 0.44 | -0.13 / -0.33 / -0.10 | -0.16 | 0.02 | 0.15 | -0.32 | 0.00 | 236 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 6 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 8 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 1 |
| worst-decile corr <= +0.30 | 25 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 2 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC SMA100 timing below_short hold=rth (diag) | clean | -0.24 | -0.31 | -184356 | -129862 | 604624 | -231156 | -0.36 | 16.2 | 1.41 | -88463 | 235508 | -102102 |
| BTC SMA100 timing below_short hold=rth (diag) | H1 | 1.62 | 3.40 | -190824 | -172030 | 567336 | -207965 | 1.58 | 32.1 | 3.08 | -82937 | 242561 | -97898 |
| BTC SMA100 timing below_short hold=rth (diag) | H2 | -1.68 | -1.90 | -188895 | -147852 | 599766 | -213769 | -0.91 | 44.4 | 2.21 | -87989 | 217425 | -98563 |
| BTC SMA100 timing below_short hold=rth (diag) | all | 0.07 | 0.10 | -193364 | -154050 | 803192 | -231156 | 0.16 | 25.0 | 1.88 | -89440 | 242561 | -102102 |
| CL SMA200 timing below_short hold=rth (diag) | clean | -0.39 | -0.53 | -151855 | -123961 | 802556 | -221769 | -0.45 | 28.6 | 1.38 | -81015 | 264701 | -93922 |
| CL SMA200 timing below_short hold=rth (diag) | H1 | 0.18 | 0.26 | -68872 | -62918 | 168222 | -75226 | 0.16 | 35.7 | 2.72 | -87168 | 169173 | -88489 |
| CL SMA200 timing below_short hold=rth (diag) | H2 | -2.12 | -2.06 | -160385 | -103533 | 414131 | -175533 | -1.00 | 11.1 | 2.23 | -81089 | 217425 | -82524 |
| CL SMA200 timing below_short hold=rth (diag) | all | -0.58 | -0.75 | -148603 | -116567 | 1137794 | -221769 | -0.65 | 26.2 | 1.79 | -82816 | 264701 | -93922 |
| ES SMA200 timing above_long hold=c2c | clean | 0.56 | 0.83 | -133809 | -111586 | 452180 | -201531 | 1.12 | 41.0 | 1.52 | -91231 | 314707 | -105351 |
| ES SMA200 timing above_long hold=c2c | H1 | 0.76 | 1.19 | -161214 | -140960 | 328386 | -175418 | 0.82 | 42.9 | 3.22 | -64212 | 122109 | -69297 |
| ES SMA200 timing above_long hold=c2c | H2 | 1.07 | 1.62 | -131876 | -121345 | 378999 | -141699 | 1.03 | 38.9 | 2.62 | -79126 | 226208 | -83601 |
| ES SMA200 timing above_long hold=c2c | all | 0.71 | 1.07 | -146539 | -123917 | 452180 | -201531 | 2.58 | 40.5 | 2.01 | -87380 | 314707 | -105351 |
| GC SMA200 timing above_long hold=rth | clean | 0.22 | 0.31 | -157383 | -123152 | 532596 | -183215 | 0.38 | 41.9 | 1.52 | -86848 | 224351 | -109971 |
| GC SMA200 timing above_long hold=rth | H1 | 0.32 | 0.44 | -414455 | -374351 | 1053259 | -485092 | 0.22 | 42.9 | 2.60 | -89841 | 264185 | -94470 |
| GC SMA200 timing above_long hold=rth | H2 | -1.67 | -1.81 | -408957 | -348164 | 1465765 | -508149 | -0.80 | 27.8 | 1.61 | -106263 | 280357 | -118258 |
| GC SMA200 timing above_long hold=rth | all | -0.28 | -0.35 | -325714 | -244924 | 2125761 | -508149 | -0.34 | 39.3 | 1.72 | -93473 | 281690 | -118258 |
| NQ SMA200 timing below_short hold=c2c (diag) | clean | 0.56 | 1.28 | -107508 | -58641 | 454693 | -164453 | 1.12 | 5.7 | 1.52 | -86238 | 286758 | -110202 |
| NQ SMA200 timing below_short hold=c2c (diag) | H1 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.83 | -77610 | 151713 | -78287 |
| NQ SMA200 timing below_short hold=c2c (diag) | H2 | 1.24 | 5.35 | -59576 | -31031 | 181753 | -74793 | 2.13 | 8.3 | 2.57 | -88568 | 217425 | -94612 |
| NQ SMA200 timing below_short hold=c2c (diag) | all | 0.67 | 1.70 | -85464 | -45245 | 556569 | -164453 | 1.61 | 5.4 | 1.95 | -85872 | 286758 | -110202 |
| RTY SMA100 timing above_long hold=c2c | clean | 0.56 | 0.87 | -132972 | -110957 | 604305 | -183552 | 0.84 | 31.4 | 1.58 | -89257 | 299032 | -112983 |
| RTY SMA100 timing above_long hold=c2c | H1 | 1.29 | 2.11 | -133473 | -119433 | 196466 | -173308 | 1.99 | 35.7 | 3.29 | -73348 | 134643 | -75772 |
| RTY SMA100 timing above_long hold=c2c | H2 | 0.37 | 0.55 | -149776 | -131033 | 499917 | -151741 | 0.27 | 36.1 | 2.51 | -88250 | 265469 | -90633 |
| RTY SMA100 timing above_long hold=c2c | all | 0.66 | 1.00 | -148648 | -122036 | 604305 | -183552 | 1.71 | 32.7 | 2.04 | -88436 | 299032 | -112983 |
| YM SMA100 timing above_long hold=c2c | clean | 0.34 | 0.45 | -158406 | -125195 | 565315 | -197226 | 0.54 | 29.5 | 1.48 | -90167 | 279370 | -116037 |
| YM SMA100 timing above_long hold=c2c | H1 | 0.96 | 1.88 | -139340 | -128746 | 293719 | -150448 | 1.45 | 46.4 | 3.56 | -64250 | 126284 | -65061 |
| YM SMA100 timing above_long hold=c2c | H2 | 1.11 | 1.90 | -139134 | -128364 | 475752 | -142914 | 0.97 | 27.8 | 2.79 | -83464 | 226640 | -87275 |
| YM SMA100 timing above_long hold=c2c | all | 0.66 | 1.02 | -159590 | -135241 | 662503 | -197226 | 1.81 | 31.5 | 2.04 | -87249 | 279370 | -116037 |
| ZN SMA100 timing below_short hold=c2c (diag) | clean | -0.46 | -0.61 | -155831 | -125635 | 945060 | -209759 | -0.44 | 34.3 | 1.31 | -93603 | 352683 | -118960 |
| ZN SMA100 timing below_short hold=c2c (diag) | H1 | 0.45 | 0.63 | -41713 | -34782 | 81236 | -60317 | 0.39 | 10.7 | 2.80 | -83642 | 147996 | -88996 |
| ZN SMA100 timing below_short hold=c2c (diag) | H2 | 1.11 | 1.79 | -127072 | -106979 | 204415 | -141299 | 1.85 | 38.9 | 2.65 | -94247 | 203842 | -100716 |
| ZN SMA100 timing below_short hold=c2c (diag) | all | -0.01 | -0.01 | -143691 | -114756 | 950756 | -209759 | -0.01 | 31.5 | 1.83 | -93234 | 352683 | -118960 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES SMA200 timing above_long hold=c2c | -17.2 | -17.5 | 7.4 | 10.1 | -18.4 / -1.7 | 32.0 / 39.1 | NO |
| NQ SMA200 timing below_short hold=c2c (diag) | -20.2 | -25.4 | 17.3 | 26.4 | -26.4 / 15.6 | 30.0 / 30.0 | NO |
| RTY SMA100 timing above_long hold=c2c | -18.7 | -30.5 | 8.9 | 16.3 | -31.5 / 9.1 | 33.4 / 34.1 | NO |
| YM SMA100 timing above_long hold=c2c | -16.9 | -36.0 | 6.0 | 15.6 | -37.1 / -0.2 | 40.9 / 47.0 | NO |
| GC SMA200 timing above_long hold=rth | -38.0 | -74.2 | -30.0 | -69.3 | -26.2 / 13.0 | -83.6 / -64.1 | NO |
| CL SMA200 timing below_short hold=rth (diag) | -38.1 | -6.3 | 14.4 | 31.0 | -7.2 / 12.4 | 10.5 / 11.5 | NO |
| ZN SMA100 timing below_short hold=c2c (diag) | -30.1 | -41.6 | 0.3 | -8.9 | -42.7 / -2.8 | 8.1 / 18.3 | NO |
| BTC SMA100 timing below_short hold=rth (diag) | -28.6 | -28.3 | 6.1 | 13.4 | -29.3 / 6.3 | -7.6 / 8.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 SMA200 timing above_long hold=c2c | positive pre-2023 | 969 | 47.5 | 18.1 | 32.2 | 29.4 | 0.34 / 0.13 / 0.23 | 140.8 / 111.5 |
| ES 2 (diag) SMA100 timing above_long hold=c2c | positive pre-2023 | 992 | 30.8 | 1.4 | 15.7 | 29.4 | 0.24 / 0.01 / 0.12 | 26.7 / -2.7 |
| ES 3 (diag) SMA100 timing above_long hold=rth | gross-positive, cost-negative pre-2023 | 2034 | 22.2 | -7.2 | 7.1 | 29.4 | 0.31 / -0.10 / 0.10 | -11.6 / -41.0 |
| ES 4 (diag) SMA200 timing above_long hold=rth | gross-positive, cost-negative pre-2023 | 2013 | 20.0 | -9.4 | 4.7 | 29.4 | 0.27 / -0.13 / 0.06 | -24.1 / -53.4 |
| NQ 1 (diag) SMA200 timing below_short hold=c2c | positive pre-2023 | 243 | 33.1 | 18.8 | 26.2 | 14.4 | 0.04 / 0.02 / 0.03 | 951.0 / 936.6 |
| NQ 2 (diag) SMA100 timing below_short hold=c2c | negative pre-2023 | 285 | -33.7 | -48.0 | -40.1 | 14.4 | -0.05 / -0.07 / -0.06 | 284.1 / 269.7 |
| NQ 3 (diag) SMA100 timing above_long hold=c2c | positive pre-2023 | 996 | 67.5 | 53.2 | 61.8 | 14.4 | 0.30 / 0.24 / 0.28 | 18.8 / 4.4 |
| RTY 1 SMA100 timing above_long hold=c2c | negative pre-2023 | 413 | -56.5 | -70.8 | -68.9 | 14.4 | -0.40 / -0.50 / -0.48 | 100.7 / 86.3 |
| RTY 2 (diag) SMA200 timing below_short hold=c2c | negative pre-2023 | 315 | -11.7 | -26.1 | -23.4 | 14.4 | -0.05 / -0.11 / -0.10 | 204.3 / 189.9 |
| RTY 3 (diag) SMA100 timing below_short hold=c2c | negative pre-2023 | 303 | -42.2 | -56.6 | -54.2 | 14.4 | -0.17 / -0.23 / -0.22 | 112.2 / 97.9 |
| RTY 4 (diag) SMA200 timing above_long hold=c2c | negative pre-2023 | 350 | -89.3 | -103.7 | -102.3 | 14.4 | -0.53 / -0.62 / -0.61 | -19.8 / -34.1 |
| YM 1 SMA100 timing above_long hold=c2c | negative pre-2023 | 944 | -1.3 | -15.6 | -9.9 | 14.4 | -0.01 / -0.14 / -0.09 | 62.1 / 47.8 |
| YM 2 SMA200 timing above_long hold=c2c | positive pre-2023 | 982 | 14.9 | 0.5 | 6.1 | 14.4 | 0.13 / 0.00 / 0.05 | 47.3 / 32.9 |
| YM 3 (diag) SMA100 timing below_short hold=c2c | negative pre-2023 | 341 | -140.0 | -154.3 | -148.9 | 14.4 | -0.35 / -0.39 / -0.38 | 83.9 / 69.5 |
| YM 4 (diag) SMA100 timing above_long hold=rth | gross-positive, cost-negative pre-2023 | 1943 | 14.1 | -0.2 | 5.5 | 14.4 | 0.25 / -0.01 / 0.09 | 14.2 / -0.1 |
| YM 5 (diag) SMA200 timing above_long hold=rth | gross-positive, cost-negative pre-2023 | 2030 | 11.6 | -2.8 | 2.8 | 14.4 | 0.20 / -0.05 / 0.04 | 13.5 / -0.9 |
| GC 1 SMA100 timing above_long hold=rth | negative pre-2023 | 1334 | -21.2 | -45.6 | -36.3 | 24.4 | -0.21 / -0.46 / -0.37 | 60.7 / 36.3 |
| GC 2 SMA200 timing above_long hold=rth | negative pre-2023 | 1319 | -22.9 | -47.3 | -38.3 | 24.4 | -0.24 / -0.48 / -0.39 | 47.4 / 23.0 |
| GC 3 (diag) SMA100 timing above_long hold=c2c | negative pre-2023 | 651 | -12.7 | -37.1 | -27.8 | 24.4 | -0.06 / -0.18 / -0.13 | 378.7 / 354.3 |
| GC 4 (diag) SMA200 timing above_long hold=c2c | positive pre-2023 | 642 | 65.4 | 41.0 | 50.0 | 24.4 | 0.35 / 0.22 / 0.27 | 222.7 / 198.4 |
| GC 5 (diag) SMA100 timing below_short hold=rth | negative pre-2023 | 1270 | -17.1 | -41.4 | -31.1 | 24.4 | -0.18 / -0.46 / -0.34 | 40.9 / 16.5 |
| CL 1 (diag) SMA100 timing below_short hold=rth | positive pre-2023 | 1249 | 33.0 | 8.7 | 13.3 | 24.4 | 0.32 / 0.08 / 0.13 | -2.9 / -27.3 |
| CL 2 (diag) SMA200 timing below_short hold=rth | positive pre-2023 | 1390 | 26.6 | 2.2 | 7.9 | 24.4 | 0.30 / 0.02 / 0.09 | -12.7 / -37.1 |
| CL 3 (diag) SMA100 timing below_short hold=c2c | positive pre-2023 | 612 | 60.1 | 35.7 | 40.3 | 24.4 | 0.31 / 0.18 / 0.21 | -104.8 / -129.1 |
| ZN 1 (diag) SMA200 timing below_short hold=c2c | gross-positive, cost-negative pre-2023 | 565 | 20.3 | -15.3 | -19.4 | 35.6 | 0.35 / -0.26 / -0.33 | 14.3 / -21.3 |
| ZN 2 (diag) SMA100 timing below_short hold=c2c | gross-positive, cost-negative pre-2023 | 602 | 13.5 | -22.1 | -26.6 | 35.6 | 0.24 / -0.40 / -0.48 | 13.9 / -21.7 |
| ZN 3 (diag) SMA100 timing above_long hold=c2c | gross-positive, cost-negative pre-2023 | 677 | 3.8 | -31.8 | -37.4 | 35.6 | 0.08 / -0.64 / -0.75 | -2.0 / -37.6 |
| BTC 1 (diag) SMA100 timing above_long hold=c2c | negative pre-2023 | 61 | -388.5 | -442.9 | -409.9 | 54.4 | -0.51 / -0.58 / -0.54 | 162.1 / 107.7 |
| BTC 2 (diag) SMA100 timing below_short hold=rth | negative pre-2023 | 174 | -198.4 | -252.8 | -215.7 | 54.4 | -0.83 / -1.05 / -0.90 | -106.6 / -160.9 |
| BTC 3 (diag) SMA200 timing above_long hold=c2c | negative pre-2023 | 61 | -173.4 | -227.7 | -195.5 | 54.4 | -0.22 / -0.29 / -0.25 | -372.3 / -426.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 0 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 1.00); ES: 1 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.94, p(top) = 0.64); GC: 2 cells pass the clean rule against a replicate mean of 2.1 (p(count) = 0.66, p(top) = 0.89); NQ: 0 cells pass the clean rule against a replicate mean of 1.8 (p(count) = 1.00); RTY: 1 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.89, p(top) = 0.45); YM: 2 cells pass the clean rule against a replicate mean of 1.9 (p(count) = 0.67, p(top) = 0.86); ZN: 0 cells pass the clean rule against a replicate mean of 0.2 (p(count) = 1.00).
- Of 6 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (YM SMA100 timing above_long hold=c2c); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 2; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 4, 'positive pre-2023': 2}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_3.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm3/ (`BM3_CO_all_selected_scored.csv`).

DONE BM3
