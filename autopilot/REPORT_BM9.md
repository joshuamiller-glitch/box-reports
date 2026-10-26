# REPORT BM9 - daily z-score reversion (BM batch)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 3 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.04; best pair-window standalone Sharpe +0.82.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. daily z-score reversion. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |       8 |          6 |         1 |               1.145 |                2 |          1 |            3 |
| CL    |       8 |          4 |         0 |               0.437 |                2 |          0 |            3 |
| ES    |       8 |          6 |         0 |               0.874 |                2 |          0 |            3 |
| GC    |       8 |          6 |         0 |               0.144 |                1 |          0 |            3 |
| NQ    |       8 |          4 |         0 |               0.493 |                1 |          0 |            3 |
| RTY   |       8 |          4 |         2 |               0.551 |                2 |          2 |            3 |
| YM    |       8 |          6 |         0 |               0.375 |                2 |          0 |            3 |
| ZN    |       8 |          4 |         0 |               0.541 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            0.84  |               3 |       1    |                     nan     |            0.773 |           1.373 |  nan     |     nan     |                1.682 |
| NQ    |     200 |                    0 |            0.97  |               3 |       1    |                     nan     |            0.744 |           1.296 |  nan     |     nan     |                1.516 |
| RTY   |     200 |                    2 |            0.84  |               4 |       0.16 |                       0.209 |            0.775 |           1.429 |    0.595 |       0.248 |                1.536 |
| YM    |     200 |                    0 |            1.02  |               4 |       1    |                     nan     |            0.771 |           1.62  |  nan     |     nan     |                1.703 |
| GC    |     200 |                    0 |            0.955 |               4 |       1    |                     nan     |            0.826 |           1.529 |  nan     |     nan     |                1.726 |
| CL    |     200 |                    0 |            0.895 |               4 |       1    |                     nan     |            0.779 |           1.497 |  nan     |     nan     |                1.639 |
| ZN    |     200 |                    0 |            0.325 |               2 |       1    |                     nan     |            0.518 |           1.036 |  nan     |     nan     |                1.177 |
| BTC   |     200 |                    1 |            0.96  |               3 |       0.67 |                       1.145 |            0.813 |           1.346 |    0.095 |       1.145 |                1.577 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | 39 | 2 | 0.87 | -0.19 | -0.48 | -1.99 / 1.60 | 0.12 / -0.63 / -0.87 | -0.21 | 0.20 | 0.18 | -0.42 | 0.00 | 58 S | diag |
| ES 2 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | 98 | 1 | 0.27 | -0.57 | -0.28 | -1.40 / 1.47 | -0.01 / -0.51 / -0.21 | -0.13 | -0.26 | 0.22 | -0.28 | 0.00 | 148 | diag |
| ES 3 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | 63 | 1 | 0.19 | 0.09 | 0.50 | 1.71 / 1.54 | 0.01 / 0.33 / 0.13 | 0.06 | -0.51 | 0.83 | -0.06 | 0.50 | 88 S | diag |
| NQ 1 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | 154 | 1 | 0.49 | 0.02 | 0.16 | -0.49 / 1.27 | 0.05 / 0.42 / -0.33 | 0.00 | 0.23 | 0.69 | -0.15 | 0.50 | 238 | diag |
| NQ 2 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | 96 | 1 | 0.28 | 0.42 | 0.34 | 0.42 / 1.37 | 0.04 / 0.54 / -0.01 | 0.08 | 0.29 | 0.83 | -0.08 | 0.00 | 146 | diag |
| NQ 3 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | 52 | 1 | 0.25 | 0.43 | 0.15 | -0.41 / 1.38 | 0.03 / 0.37 / -0.20 | 0.01 | -0.48 | 0.58 | -0.11 | 0.50 | 83 S | diag |
| RTY 1 | prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | 82 | 2 | 0.25 | -0.10 | -0.30 | -1.28 / 1.62 | 0.02 / -0.74 / -0.08 | -0.12 | -0.46 | 0.20 | -0.28 | 0.00 | 144 | NO |
| RTY 2 | prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | 142 | 2 | 0.17 | -0.18 | -0.25 | -0.92 / 1.67 | 0.01 / -0.83 / -0.00 | -0.12 | -0.18 | 0.37 | -0.29 | 0.00 | 241 | NO |
| RTY 3 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | 32 | 2 | 0.55 | 0.21 | -0.28 | -1.67 / 1.49 | 0.07 / -0.79 / -0.19 | -0.11 | -0.32 | 0.34 | -0.29 | 0.00 | 51 S | diag |
| RTY 4 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | 50 | 1 | 0.16 | -0.30 | 0.82 | 2.03 / 1.31 | 0.02 / 0.58 / 0.05 | 0.11 | -0.16 | 0.96 | -0.03 | 0.00 | 77 S | diag |
| RTY 5 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d | 50 | 1 | -0.27 | 0.16 | -0.93 | -2.12 / 1.45 | -0.09 / -0.84 / -0.10 | -0.22 | 0.17 | 0.06 | -0.39 | 0.00 | 77 S | diag |
| YM 1 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | 39 | 2 | 0.37 | -0.12 | -0.76 | -2.68 / 1.36 | -0.01 / -0.54 / -0.65 | -0.24 | 0.08 | 0.06 | -0.42 | 0.00 | 59 S | diag |
| YM 2 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | 142 | 1 | 0.15 | 0.14 | -0.43 | -1.63 / 1.55 | 0.00 / -0.29 / -0.33 | -0.12 | 0.48 | 0.25 | -0.28 | 0.00 | 237 | diag |
| YM 3 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | 83 | 1 | 0.09 | -0.35 | -0.62 | -1.52 / 1.38 | -0.04 / -0.33 / -0.62 | -0.23 | 0.29 | 0.14 | -0.42 | 0.00 | 142 | diag |
| GC 1 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | 41 | 1 | 0.14 | -0.25 | 0.12 | 0.14 / 1.41 | -0.07 / -0.68 / -0.20 | -0.17 | -0.08 | 0.59 | -0.53 | 0.00 | 63 S | diag |
| GC 2 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | 62 | 1 | 0.10 | -0.49 | 0.22 | 0.37 / 1.54 | -0.08 / -0.04 / -0.23 | -0.08 | -0.34 | 0.63 | -0.37 | 0.00 | 98 S | diag |
| GC 3 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | 78 | 1 | 0.06 | -0.21 | 0.24 | 0.37 / 1.34 | -0.08 / -1.20 / 0.40 | -0.14 | -0.51 | 0.71 | -0.55 | 0.00 | 133 | diag |
| CL 1 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | 37 | 2 | 0.44 | -0.29 | 0.00 | -0.21 / 1.56 | 0.07 / -0.14 / -0.59 | -0.13 | -0.35 | 0.57 | -0.56 | 0.00 | 57 S | diag |
| CL 2 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d | 59 | 1 | 0.35 | -0.29 | 0.20 | 0.12 / 1.44 | 0.04 / -0.03 / -0.36 | -0.09 | -0.08 | 0.73 | -0.47 | 0.00 | 92 S | diag |
| CL 3 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | 84 | 1 | 0.27 | -0.08 | -0.32 | -1.02 / 1.51 | 0.05 / -0.17 / -0.77 | -0.17 | 0.52 | 0.32 | -0.41 | 0.00 | 136 | diag |
| ZN 1 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | 91 | 1 | 0.54 | -0.39 | 0.22 | -0.65 / 0.68 | 0.09 / -0.21 / -0.10 | -0.07 | 0.33 | 0.92 | -0.15 | 0.00 | 142 | diag |
| ZN 2 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | 33 | 1 | 0.22 | -0.12 | -0.07 | -1.24 / 1.03 | 0.04 / -0.22 / -0.11 | -0.06 | -0.10 | 0.71 | -0.18 | 0.00 | 57 S | diag |
| ZN 3 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | 147 | 1 | 0.19 | -0.35 | -0.25 | -1.57 / 0.30 | 0.04 / -0.19 / -0.21 | -0.18 | -0.09 | 0.89 | -0.21 | 0.00 | 230 | diag |
| BTC 1 | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | 62 | 2 | 1.14 | -0.02 | 0.76 | -0.11 / 1.44 | 0.12 / -0.08 / -0.10 | 0.03 | 0.09 | 0.95 | -0.10 | 0.50 | 88 S | NO |
| BTC 2 (diag) | prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | 43 | 1 | 0.36 | 0.21 | 0.35 | 0.33 / 1.60 | 0.00 / 0.12 / -0.07 | -0.01 | -0.33 | 0.78 | -0.18 | 0.00 | 60 S | diag |
| BTC 3 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | 85 | 1 | 0.10 | 0.55 | 0.23 | 0.40 / 1.43 | -0.04 / 0.27 / -0.01 | -0.01 | -0.07 | 0.73 | -0.22 | 0.00 | 128 | diag |
| BTC 4 (diag) | prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | 152 | 1 | -0.01 | -0.50 | 0.33 | 0.85 / 1.58 | -0.09 / 0.07 / 0.03 | -0.05 | 0.08 | 0.71 | -0.23 | 0.00 | 221 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 3 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 7 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 0 |
| standalone pair-window Sharpe above own random-entry null p95 | 2 |
| worst-decile corr <= +0.30 | 24 |
| plateau >= 0.75 | 0 |
| all-in uplift at 2x slippage >= +0.10 | 1 |
| small-sample (<100 trades pair window) | 14 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | clean | 1.14 | 2.48 | -104268 | -69480 | 556940 | -211111 | 1.85 | 11.4 | 1.58 | -89323 | 302972 | -119281 |
| BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | H1 | 0.56 | 0.82 | -115622 | -77081 | 335282 | -150298 | 0.30 | 7.1 | 2.75 | -77610 | 199785 | -78287 |
| BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | H2 | -0.74 | -0.85 | -117380 | -87413 | 282571 | -172440 | -0.50 | 11.1 | 2.39 | -81089 | 217425 | -82524 |
| BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | all | 0.76 | 1.40 | -114365 | -79128 | 556940 | -211111 | 1.78 | 10.7 | 1.94 | -86267 | 302972 | -119281 |
| CL prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d (diag) | clean | 0.39 | 0.55 | -153870 | -103855 | 745099 | -338789 | 0.48 | 14.3 | 1.50 | -78508 | 289863 | -80036 |
| CL prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d (diag) | H1 | -0.29 | -0.39 | -63637 | -47899 | 147147 | -66310 | -0.18 | 14.3 | 2.79 | -77610 | 164975 | -78287 |
| CL prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d (diag) | H2 | 0.18 | 0.22 | -613221 | -344985 | 1563792 | -1070661 | 0.13 | 11.1 | 2.12 | -157282 | 323664 | -203755 |
| CL prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d (diag) | all | 0.20 | 0.25 | -250475 | -155860 | 1563792 | -1070661 | 0.34 | 13.7 | 1.83 | -95989 | 323664 | -203755 |
| ES prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | clean | 0.20 | 0.34 | -120594 | -75142 | 378230 | -276794 | 0.47 | 14.3 | 1.47 | -78980 | 261049 | -83002 |
| ES prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | H1 | 2.89 |  | 0 | 0 | 2515 | 0 | 126.85 | 0.0 | 3.16 | -71054 | 141292 | -78287 |
| ES prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | H2 | 0.81 | 1.45 | -64493 | -42652 | 204054 | -72296 | 0.57 | 13.9 | 2.61 | -81089 | 217425 | -82524 |
| ES prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | all | 0.50 | 0.89 | -97977 | -59787 | 378230 | -276794 | 1.62 | 11.9 | 1.96 | -79372 | 261049 | -83002 |
| GC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | clean | 0.03 | 0.04 | -169450 | -117115 | 717296 | -234158 | 0.04 | 14.3 | 1.38 | -88825 | 289026 | -111807 |
| GC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | H1 | 0.93 | 2.23 | -320467 | -249903 | 801230 | -419142 | 1.01 | 14.3 | 2.79 | -119524 | 218161 | -160761 |
| GC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | H2 | -0.45 | -0.54 | -330129 | -205231 | 822692 | -541235 | -0.31 | 13.9 | 2.26 | -91738 | 217425 | -100951 |
| GC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | all | 0.22 | 0.37 | -248895 | -167954 | 822692 | -541235 | 0.70 | 14.3 | 1.82 | -97465 | 289026 | -160761 |
| NQ prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | clean | 0.29 | 0.44 | -146168 | -109679 | 395757 | -180401 | 0.66 | 27.6 | 1.50 | -79245 | 313933 | -83860 |
| NQ prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | H1 | 2.75 | 10.72 | -48448 | -37565 | 115035 | -69201 | 5.22 | 17.9 | 3.37 | -72955 | 123502 | -78287 |
| NQ prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | H2 | -1.22 | -1.37 | -187938 | -130304 | 709904 | -263418 | -0.53 | 25.0 | 2.48 | -81089 | 199916 | -82524 |
| NQ prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | all | 0.34 | 0.51 | -149619 | -109572 | 709904 | -263418 | 0.69 | 25.6 | 1.98 | -79570 | 313933 | -83860 |
| RTY prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | clean | 0.17 | 0.26 | -119359 | -91084 | 678059 | -330331 | 0.23 | 31.4 | 1.47 | -84789 | 222186 | -91170 |
| RTY prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | H1 | -2.91 | -2.92 | -168876 | -148848 | 725159 | -211400 | -0.97 | 46.4 | 2.00 | -87617 | 184693 | -96947 |
| RTY prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | H2 | 0.55 | 0.96 | -123491 | -102313 | 260853 | -136244 | 0.68 | 27.8 | 2.48 | -79635 | 214482 | -82122 |
| RTY prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | all | -0.25 | -0.36 | -147511 | -113415 | 1568083 | -330331 | -0.24 | 33.3 | 1.79 | -85121 | 222186 | -96947 |
| YM prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d (diag) | clean | 0.15 | 0.19 | -142974 | -100187 | 578721 | -432601 | 0.23 | 29.5 | 1.46 | -88045 | 268367 | -104128 |
| YM prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d (diag) | H1 | -2.04 | -2.28 | -96649 | -83557 | 319436 | -125787 | -0.91 | 39.3 | 2.54 | -77610 | 161744 | -78287 |
| YM prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d (diag) | H2 | -1.46 | -1.97 | -127838 | -105180 | 533117 | -144675 | -0.79 | 50.0 | 2.16 | -85821 | 217967 | -90412 |
| YM prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d (diag) | all | -0.43 | -0.55 | -141261 | -102945 | 1283718 | -432601 | -0.45 | 35.7 | 1.78 | -86579 | 268367 | -104128 |
| ZN prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | clean | 0.54 | 0.84 | -128706 | -108869 | 586092 | -192926 | 0.83 | 27.6 | 1.55 | -85295 | 310844 | -96169 |
| ZN prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | H1 | -1.97 | -2.11 | -58838 | -50313 | 169796 | -62209 | -0.87 | 21.4 | 2.62 | -82610 | 154576 | -83585 |
| ZN prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | H2 | -0.26 | -0.35 | -101464 | -88544 | 235882 | -107147 | -0.25 | 36.1 | 2.38 | -85570 | 222971 | -88615 |
| ZN prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | all | 0.22 | 0.33 | -120408 | -98981 | 586092 | -192926 | 0.48 | 28.6 | 1.90 | -85585 | 310844 | -96169 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | -23.3 | 23.9 | 27.7 | 33.0 | 23.3 / 26.5 | 30.0 / 42.7 | NO |
| NQ prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | -24.7 | 22.4 | 27.4 | 11.9 | 21.8 / 26.1 | 30.0 / 39.0 | NO |
| RTY prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | -34.1 | -1.6 | 14.1 | 31.0 | 9.9 / 17.8 | -7.1 / -6.5 | NO |
| YM prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d (diag) | -36.4 | -9.9 | 13.3 | 36.0 | -10.8 / 8.6 | 28.2 / 28.5 | NO |
| GC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d (diag) | -23.7 | -117.6 | -14.0 | 7.2 | -29.5 / 10.0 | -129.4 / -51.0 | NO |
| CL prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d (diag) | -24.2 | -280.4 | -19.8 | -70.2 | -4.1 / 19.0 | 30.0 / 30.0 | NO |
| ZN prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d (diag) | -26.9 | -8.7 | 13.2 | 12.7 | -9.6 / 10.6 | 18.5 / 20.3 | NO |
| BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | -19.1 | -42.1 | 15.2 | 10.3 | -43.2 / 9.7 | 18.8 / 23.7 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | negative pre-2023 | 166 | -88.3 | -117.7 | -103.4 | 29.4 | -0.14 / -0.19 / -0.17 | 467.0 / 437.6 |
| ES 2 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | negative pre-2023 | 485 | -120.9 | -150.2 | -136.3 | 29.4 | -0.46 / -0.57 / -0.51 | 169.6 / 140.3 |
| ES 3 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | positive pre-2023 | 241 | 57.2 | 27.8 | 42.2 | 29.4 | 0.19 / 0.09 / 0.14 | 160.3 / 131.0 |
| NQ 1 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | positive pre-2023 | 825 | 18.2 | 3.8 | 12.1 | 14.4 | 0.08 / 0.02 / 0.06 | 328.7 / 314.3 |
| NQ 2 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | positive pre-2023 | 488 | 184.2 | 169.9 | 178.1 | 14.4 | 0.45 / 0.42 / 0.44 | 278.0 / 263.6 |
| NQ 3 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | positive pre-2023 | 258 | 182.5 | 168.2 | 176.8 | 14.4 | 0.46 / 0.43 / 0.45 | 489.2 / 474.9 |
| RTY 1 prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | negative pre-2023 | 275 | -10.6 | -25.0 | -22.6 | 14.4 | -0.04 / -0.10 / -0.09 | 89.6 / 75.2 |
| RTY 2 prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | negative pre-2023 | 461 | -6.9 | -21.2 | -18.9 | 14.4 | -0.06 / -0.18 / -0.16 | 36.2 / 21.9 |
| RTY 3 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | positive pre-2023 | 108 | 107.1 | 92.7 | 95.0 | 14.4 | 0.24 / 0.21 / 0.22 | 267.0 / 252.7 |
| RTY 4 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | negative pre-2023 | 157 | -47.8 | -62.2 | -59.9 | 14.4 | -0.23 / -0.30 / -0.29 | 58.0 / 43.6 |
| RTY 5 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d | positive pre-2023 | 157 | 47.8 | 33.4 | 35.7 | 14.4 | 0.23 / 0.16 / 0.18 | -58.0 / -72.4 |
| YM 1 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | negative pre-2023 | 182 | -37.2 | -51.5 | -45.7 | 14.4 | -0.08 / -0.12 / -0.10 | 159.1 / 144.7 |
| YM 2 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=1d | positive pre-2023 | 776 | 31.3 | 17.0 | 22.7 | 14.4 | 0.26 / 0.14 / 0.19 | 46.7 / 32.3 |
| YM 3 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=with hold=2d | negative pre-2023 | 454 | -67.6 | -81.9 | -76.1 | 14.4 | -0.29 / -0.35 / -0.32 | 39.2 / 24.8 |
| GC 1 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | negative pre-2023 | 198 | -97.3 | -121.6 | -111.9 | 24.4 | -0.20 / -0.25 / -0.23 | 118.0 / 93.7 |
| GC 2 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | negative pre-2023 | 312 | -102.5 | -126.9 | -117.1 | 24.4 | -0.40 / -0.49 / -0.45 | 37.3 / 12.9 |
| GC 3 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | negative pre-2023 | 443 | -37.3 | -61.7 | -51.9 | 24.4 | -0.13 / -0.21 / -0.18 | 52.4 / 28.1 |
| CL 1 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=2d | negative pre-2023 | 194 | -126.9 | -151.2 | -148.9 | 24.4 | -0.24 / -0.29 / -0.28 | 163.8 / 139.4 |
| CL 2 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=with hold=1d | negative pre-2023 | 276 | -46.4 | -70.8 | -68.4 | 24.4 | -0.19 / -0.29 / -0.28 | 92.0 / 67.7 |
| CL 3 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | gross-positive, cost-negative pre-2023 | 472 | 0.3 | -24.0 | -21.4 | 24.4 | 0.01 / -0.08 / -0.07 | 133.0 / 108.6 |
| ZN 1 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | gross-positive, cost-negative pre-2023 | 465 | 5.8 | -29.8 | -34.8 | 35.6 | 0.08 / -0.39 / -0.45 | 79.8 / 44.2 |
| ZN 2 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | gross-positive, cost-negative pre-2023 | 204 | 22.4 | -13.2 | -18.3 | 35.6 | 0.20 / -0.12 / -0.17 | 75.8 / 40.1 |
| ZN 3 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | gross-positive, cost-negative pre-2023 | 757 | 22.2 | -13.4 | -18.4 | 35.6 | 0.60 / -0.35 / -0.48 | 44.3 / 8.7 |
| BTC 1 prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d | gross-positive, cost-negative pre-2023 | 34 | 30.1 | -24.2 | 9.1 | 54.4 | 0.03 / -0.02 / 0.01 | 1712.9 / 1658.5 |
| BTC 2 (diag) prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=2d | positive pre-2023 | 22 | 433.0 | 378.6 | 412.0 | 54.4 | 0.24 / 0.21 / 0.23 | 859.3 / 804.9 |
| BTC 3 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=2d | positive pre-2023 | 53 | 735.4 | 681.0 | 713.8 | 54.4 | 0.59 / 0.55 / 0.57 | 232.9 / 178.6 |
| BTC 4 (diag) prior-close z vs SMA20/sd20 >= 1.5 dir=against(revert) hold=1d | negative pre-2023 | 85 | -204.1 | -258.5 | -225.6 | 54.4 | -0.40 / -0.50 / -0.44 | 44.9 / -9.5 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 1 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.67, p(top) = 0.10); CL: 0 cells pass the clean rule against a replicate mean of 0.9 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); NQ: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); RTY: 2 cells pass the clean rule against a replicate mean of 0.8 (p(count) = 0.16, p(top) = 0.59); YM: 0 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00).
- Of 3 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.04 (BTC prior-close z vs SMA20/sd20 >= 2.0 dir=against(revert) hold=1d); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 2, 'gross-positive, cost-negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_9.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm9/ (`BM9_CO_all_selected_scored.csv`).

DONE BM9
