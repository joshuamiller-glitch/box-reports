# REPORT BM8 - up-day fraction (BM batch)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 11 selected cells (+16 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.15; best pair-window standalone Sharpe +0.99.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. up-day fraction. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM, GC, CL, ZN, BTC. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| BTC   |      12 |          8 |         4 |               1.08  |                2 |          4 |            0 |
| CL    |      12 |          6 |         0 |               1.421 |                2 |          0 |            3 |
| ES    |      12 |         10 |         1 |               0.941 |                2 |          1 |            3 |
| GC    |      12 |          6 |         0 |               0.927 |                2 |          0 |            1 |
| NQ    |      12 |          6 |         1 |               1.323 |                2 |          1 |            2 |
| RTY   |      12 |          8 |         4 |               1.694 |                2 |          4 |            1 |
| YM    |      12 |          8 |         1 |               0.774 |                2 |          1 |            3 |
| ZN    |      12 |          6 |         0 |               1.095 |                2 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    1 |            1.74  |               5 |      0.87  |                       0.236 |            0.742 |           1.334 |    0.855 |       0.236 |                1.554 |
| NQ    |     200 |                    1 |            2.005 |               6 |      0.915 |                       0.056 |            0.795 |           1.342 |    0.915 |       0.056 |                1.721 |
| RTY   |     200 |                    4 |            1.31  |               4 |      0.02  |                       0.837 |            0.696 |           1.23  |    0.205 |       1.348 |                1.529 |
| YM    |     200 |                    1 |            1.6   |               6 |      0.835 |                       0.774 |            0.759 |           1.389 |    0.38  |       0.774 |                1.667 |
| GC    |     200 |                    0 |            1.215 |               4 |      1     |                     nan     |            0.815 |           1.54  |  nan     |     nan     |                1.749 |
| CL    |     200 |                    0 |            1.42  |               5 |      1     |                     nan     |            0.735 |           1.242 |  nan     |     nan     |                1.608 |
| ZN    |     200 |                    0 |            0.255 |               2 |      1     |                     nan     |            0.517 |           1.27  |  nan     |     nan     |                1.317 |
| BTC   |     200 |                    4 |            1.43  |               4 |      0.03  |                       0.643 |            0.745 |           1.276 |    0.445 |       1.08  |                1.597 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 87 | 2 | 0.24 | -0.09 | 0.70 | 1.12 / 1.28 | 0.04 / 0.00 / 0.62 | 0.13 | -0.63 | 0.95 | -0.07 | 0.00 | 114 | NO |
| ES 2 (diag) | up-day fraction last 20d >= 0.8 (or <= 0.2) dir=against majority hold flat | 6 | 1 | 0.94 | -0.17 | 0.67 | 0.27 / 1.36 | 0.17 / 0.00 / -0.05 | 0.07 | -0.16 | 0.95 | -0.07 | 0.50 | 13 S | diag |
| ES 3 (diag) | up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | 203 | 1 | 0.21 | -0.31 | 0.24 | 0.23 / 1.31 | -0.01 / 0.23 / -0.14 | -0.03 | 0.10 | 0.80 | -0.14 | 0.00 | 307 | diag |
| ES 4 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 62 | 1 | 0.08 | -0.61 | -0.17 | -0.37 / 1.26 | 0.04 / 0.00 / -0.41 | -0.09 | 0.00 | 0.51 | -0.34 | 0.00 | 80 S | diag |
| NQ 1 | up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | 193 | 2 | 0.06 | 0.30 | -0.24 | -0.76 / 1.52 | -0.04 / 0.19 / -0.29 | -0.08 | -0.20 | 0.41 | -0.23 | 0.00 | 305 | NO |
| NQ 2 (diag) | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 54 | 2 | 1.32 | -0.27 | 0.66 | 0.31 / 1.30 | 0.29 / 0.20 / -0.15 | 0.18 | -0.63 | 0.90 | -0.09 | 0.50 | 92 S | diag |
| NQ 3 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 52 | 2 | 0.79 | 0.48 | 0.12 | -0.35 / 1.36 | 0.19 / 0.00 / -0.38 | 0.04 | 0.15 | 0.63 | -0.19 | 0.00 | 72 S | diag |
| RTY 1 | up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | 107 | 2 | 1.35 | 0.17 | 0.85 | 0.01 / 1.02 | 0.23 / -0.03 / -0.10 | 0.11 | -0.02 | 0.96 | -0.05 | 0.00 | 169 | NO |
| RTY 2 | up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | 183 | 2 | 0.91 | 0.35 | 0.81 | 0.57 / 1.24 | 0.10 / 0.23 / -0.07 | 0.06 | 0.11 | 0.93 | -0.07 | 0.00 | 279 | NO |
| RTY 3 | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 63 | 2 | 0.75 | 0.23 | 0.76 | 0.86 / 1.47 | 0.15 / 0.14 / -0.02 | 0.11 | -0.29 | 0.94 | -0.06 | 0.50 | 84 S | NO |
| RTY 4 | up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | 153 | 2 | 0.34 | -0.74 | -0.17 | -0.88 / 1.37 | 0.05 / -0.43 / -0.17 | -0.08 | -0.14 | 0.43 | -0.25 | 0.00 | 233 | NO |
| RTY 5 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 15 | 2 | 1.69 | 0.35 | 0.99 | 0.19 / 1.33 | 0.31 / 0.33 / 0.20 | 0.26 | -0.41 | 0.96 | 0.08 | 0.00 | 35 S | diag |
| YM 1 | up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | 137 | 2 | 0.77 | 0.32 | -0.08 | -1.75 / 1.76 | 0.10 / 0.02 / -0.41 | -0.06 | 0.40 | 0.34 | -0.21 | 0.00 | 210 | NO |
| YM 2 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=with majority hold flat | 42 | 2 | 0.33 | 0.04 | -0.34 | -2.13 / 1.24 | -0.01 / -0.11 / -0.38 | -0.12 |  | 0.23 | -0.25 | 0.00 | 59 S | diag |
| YM 3 (diag) | up-day fraction last 20d >= 0.8 (or <= 0.2) dir=with majority hold flat | 8 | 1 | 0.10 | 0.42 | 0.08 |  /  | -0.02 / 0.00 / 0.00 | -0.02 |  | 0.49 | -0.20 | 0.00 | 8 S | diag |
| YM 4 (diag) | up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | 213 | 1 | 0.05 | -0.15 | -0.36 | -1.25 / 1.41 | -0.02 / -0.36 / -0.10 | -0.10 | 0.23 | 0.27 | -0.27 | 0.00 | 301 | diag |
| GC 1 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 29 | 2 | 0.93 | -0.32 | 0.21 | -0.04 / 1.13 | 0.22 / -1.57 / 0.63 | -0.01 | -0.14 | 0.71 | -0.57 | 1.00 | 53 S | diag |
| CL 1 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 23 | 2 | 1.42 | -0.09 | 0.26 | -0.60 / 1.24 | 0.32 / 0.03 / -0.73 | 0.02 | -0.32 | 0.74 | -0.37 | 0.00 | 37 S | diag |
| CL 2 (diag) | up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | 103 | 1 | 0.49 | 0.51 | 0.13 | -0.15 / 1.23 | 0.08 / -0.27 / -0.39 | -0.10 | -0.14 | 0.68 | -0.37 | 0.00 | 171 | diag |
| CL 3 (diag) | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 39 | 2 | 0.39 | -0.22 | -0.15 | -0.77 / 1.38 | 0.08 / -0.48 / -0.35 | -0.11 | -0.29 | 0.49 | -0.34 | 0.00 | 75 S | diag |
| ZN 1 (diag) | up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | 21 | 2 | 1.09 | -0.09 | 0.99 | 0.99 / 1.05 | 0.21 / 0.12 / 0.01 | 0.12 | -0.54 | 0.99 | 0.01 | 0.00 | 23 S | diag |
| ZN 2 (diag) | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 56 | 1 | 0.25 | -0.39 | -0.20 | -1.04 / 0.73 | 0.00 / -0.03 / -0.19 | -0.13 | -0.52 | 0.76 | -0.24 | 0.00 | 82 S | diag |
| ZN 3 (diag) | up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | 97 | 1 | 0.08 | -0.07 | 0.11 | 0.33 / 0.74 | 0.03 / -0.04 / 0.06 | -0.04 | -0.26 | 0.94 | -0.11 | 0.50 | 126 | diag |
| BTC 1 | up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | 91 | 2 | 1.08 | 0.79 | 0.54 | -0.53 / 1.54 | 0.18 / -0.08 / -0.21 | 0.06 | -0.05 | 0.88 | -0.10 | 0.50 | 145 | NO |
| BTC 2 | up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | 67 | 2 | 0.72 | 0.02 | 0.93 | 1.20 / 1.54 | 0.09 / 0.30 / 0.15 | 0.13 | 0.41 | 0.96 | -0.03 | 0.50 | 102 | LEAD |
| BTC 3 | up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | 170 | 2 | 0.48 | 0.55 | 0.27 | 0.11 / 1.42 | 0.04 / 0.06 / -0.13 | 0.00 | 0.18 | 0.69 | -0.17 | 1.00 | 280 | NO |
| BTC 4 | up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | 158 | 2 | 0.29 | -0.02 | -0.18 | -1.07 / 1.36 | 0.11 / -0.70 / -0.02 | -0.04 | -0.25 | 0.45 | -0.24 | 0.00 | 244 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 11 |
| diagnostic cells read | 16 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 15 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 6 |
| worst-decile corr <= +0.30 | 23 |
| plateau >= 0.75 | 2 |
| all-in uplift at 2x slippage >= +0.10 | 7 |
| small-sample (<100 trades pair window) | 13 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BTC up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | clean | 0.72 | 1.43 | -116500 | -70267 | 286280 | -219442 | 2.28 | 9.5 | 1.55 | -78841 | 280110 | -81874 |
| BTC up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | H1 | 1.36 |  | 0 | 0 | 0 | 0 |  | 0.0 | 3.13 | -77610 | 137633 | -78287 |
| BTC up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | H2 | 1.07 | 2.68 | -122798 | -96586 | 370280 | -132845 | 1.23 | 11.1 | 2.63 | -92364 | 249537 | -105075 |
| BTC up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | all | 0.93 | 2.20 | -115878 | -68193 | 370280 | -219442 | 4.06 | 8.3 | 2.03 | -81802 | 280110 | -105075 |
| CL up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | clean | 1.41 | 4.15 | -62687 | -34193 | 363868 | -135216 | 3.52 | 2.9 | 1.78 | -78736 | 214509 | -81874 |
| CL up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H1 | 0.90 | 1.98 | -66188 | -44125 | 132375 | -87986 | 1.08 | 7.1 | 2.86 | -76599 | 162086 | -78287 |
| CL up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H2 | -0.98 | -1.00 | -542518 | -272505 | 1312896 | -1014424 | -0.64 | 8.3 | 1.75 | -136081 | 270185 | -192508 |
| CL up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | all | 0.26 | 0.31 | -177613 | -94030 | 1387934 | -1014424 | 0.42 | 4.8 | 1.94 | -91441 | 270185 | -192508 |
| ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | clean | 0.34 | 0.53 | -153257 | -112813 | 500696 | -208612 | 0.62 | 13.3 | 1.50 | -84237 | 280110 | -110318 |
| ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | H1 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.83 | -77610 | 151713 | -78287 |
| ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | H2 | 1.50 | 6.16 | -122007 | -70126 | 429662 | -138130 | 2.12 | 8.3 | 3.11 | -88989 | 217425 | -98324 |
| ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | all | 0.70 | 1.51 | -138048 | -90791 | 830694 | -208612 | 1.47 | 10.1 | 2.05 | -84632 | 280110 | -110318 |
| GC up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | clean | 0.92 | 1.76 | -94487 | -51538 | 550096 | -267336 | 1.52 | 3.8 | 1.68 | -78671 | 333577 | -81874 |
| GC up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H1 | -0.97 | -1.05 | -925964 | -642093 | 2652503 | -1323344 | -0.42 | 10.7 | 1.26 | -183708 | 540387 | -290483 |
| GC up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H2 | 1.20 |  | 0 | 0 | 0 | 0 |  | 0.0 | 3.11 | -79970 | 217425 | -82524 |
| GC up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | all | 0.21 | 0.28 | -277022 | -146659 | 2652503 | -1323344 | 0.28 | 4.2 | 1.91 | -102494 | 540387 | -290483 |
| NQ up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | clean | 0.06 | 0.10 | -116743 | -90202 | 546354 | -189662 | 0.09 | 36.2 | 1.42 | -84141 | 356291 | -86764 |
| NQ up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | H1 | 1.36 | 2.04 | -80077 | -68162 | 179109 | -87628 | 1.12 | 28.6 | 3.02 | -70963 | 166989 | -78287 |
| NQ up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | H2 | -1.74 | -1.91 | -208267 | -159653 | 608799 | -256003 | -0.97 | 38.9 | 2.20 | -84615 | 207597 | -86706 |
| NQ up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | all | -0.24 | -0.35 | -141301 | -107182 | 654895 | -256003 | -0.51 | 35.7 | 1.82 | -83879 | 356291 | -86764 |
| RTY up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | clean | 1.43 | 2.74 | -120504 | -87369 | 330489 | -183030 | 3.88 | 19.0 | 1.69 | -82451 | 268448 | -102327 |
| RTY up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | H1 | 0.45 | 0.67 | -108993 | -104127 | 265684 | -111854 | 0.37 | 25.0 | 2.80 | -88223 | 159856 | -98159 |
| RTY up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | H2 | -0.23 | -0.29 | -221013 | -149026 | 645435 | -335002 | -0.14 | 19.4 | 2.38 | -89237 | 217425 | -101058 |
| RTY up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | all | 0.85 | 1.33 | -145316 | -110372 | 807703 | -335002 | 1.59 | 20.2 | 2.02 | -85828 | 268448 | -102327 |
| YM up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | clean | 0.76 | 1.42 | -106396 | -89650 | 553479 | -153221 | 1.24 | 28.6 | 1.56 | -87803 | 276330 | -95846 |
| YM up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | H1 | -1.00 | -1.34 | -93081 | -84799 | 240756 | -109949 | -0.73 | 35.7 | 2.85 | -67471 | 138924 | -76932 |
| YM up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | H2 | -2.23 | -2.34 | -159845 | -145052 | 638307 | -172061 | -0.98 | 30.6 | 2.07 | -95019 | 218167 | -110384 |
| YM up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | all | -0.08 | -0.13 | -130587 | -105373 | 824772 | -172061 | -0.14 | 30.4 | 1.85 | -88286 | 276330 | -110384 |
| ZN up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | clean | 1.09 | 2.88 | -65078 | -35497 | 468725 | -199519 | 2.11 | 2.9 | 1.67 | -77966 | 268163 | -79868 |
| ZN up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H1 | 1.36 |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.95 | -77610 | 151713 | -78287 |
| ZN up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | H2 | 1.20 |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.49 | -81089 | 217425 | -82524 |
| ZN up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | all | 0.99 | 2.70 | -43385 | -22969 | 468725 | -199519 | 2.49 | 1.8 | 2.05 | -78713 | 268163 | -82524 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | -16.6 | -25.7 | 16.1 | 23.7 | -26.7 / 14.9 | 30.0 / 30.0 | NO |
| NQ up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | -33.7 | 4.9 | 18.0 | -10.8 | 4.2 / 14.9 | 30.0 / 39.6 | NO |
| RTY up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | -15.9 | -11.3 | 14.1 | 36.2 | -12.2 / 18.7 | -9.5 / 9.5 | NO |
| YM up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | -31.3 | -20.6 | 12.2 | 19.7 | -0.3 / 12.6 | 31.2 / 41.3 | NO |
| GC up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | -21.8 | -403.0 | -23.6 | -180.9 | 30.0 / 30.1 | -430.2 / -217.8 | NO |
| CL up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | -23.6 | -260.0 | -4.9 | -27.5 | 30.0 / 29.3 | 30.0 / 32.0 | NO |
| ZN up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat (diag) | -17.2 | 16.2 | 28.3 | 10.8 | 15.6 / 27.5 | 30.0 / 30.0 | NO |
| BTC up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | -13.5 | -11.0 | 21.5 | 16.5 | 1.0 / 24.4 | 30.0 / 30.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | gross-positive, cost-negative pre-2023 | 391 | 15.1 | -14.3 | 0.1 | 29.4 | 0.09 / -0.09 / 0.00 | 97.6 / 68.2 |
| ES 2 (diag) up-day fraction last 20d >= 0.8 (or <= 0.2) dir=against majority hold flat | negative pre-2023 | 67 | -14.9 | -44.3 | -27.5 | 29.4 | -0.06 / -0.17 / -0.11 | 237.5 / 208.1 |
| ES 3 (diag) up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | negative pre-2023 | 1012 | -7.5 | -36.9 | -22.8 | 29.4 | -0.06 / -0.31 / -0.19 | 90.1 / 60.7 |
| ES 4 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | negative pre-2023 | 265 | -65.5 | -94.9 | -80.1 | 29.4 | -0.43 / -0.61 / -0.52 | 46.0 / 16.6 |
| NQ 1 up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | positive pre-2023 | 1032 | 70.6 | 56.3 | 64.8 | 14.4 | 0.38 / 0.30 / 0.35 | 39.2 / 24.9 |
| NQ 2 (diag) up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | negative pre-2023 | 414 | -50.2 | -64.6 | -55.9 | 14.4 | -0.21 / -0.27 / -0.23 | 655.1 / 640.7 |
| NQ 3 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | positive pre-2023 | 297 | 124.4 | 110.0 | 119.0 | 14.4 | 0.54 / 0.48 / 0.52 | 396.1 / 381.7 |
| RTY 1 up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | positive pre-2023 | 340 | 29.4 | 15.1 | 17.5 | 14.4 | 0.30 / 0.17 / 0.19 | 198.8 / 184.5 |
| RTY 2 up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | positive pre-2023 | 525 | 49.1 | 34.8 | 37.1 | 14.4 | 0.49 / 0.35 / 0.38 | 127.2 / 112.9 |
| RTY 3 up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | positive pre-2023 | 154 | 54.4 | 40.0 | 43.0 | 14.4 | 0.31 / 0.23 / 0.24 | 131.5 / 117.1 |
| RTY 4 up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | negative pre-2023 | 486 | -65.8 | -80.1 | -77.6 | 14.4 | -0.61 / -0.74 / -0.71 | 49.1 / 34.7 |
| RTY 5 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | positive pre-2023 | 94 | 81.4 | 67.1 | 70.3 | 14.4 | 0.43 / 0.35 / 0.37 | 562.7 / 548.3 |
| YM 1 up-day fraction last 5d >= 0.8 (or <= 0.2) dir=with majority hold flat | positive pre-2023 | 756 | 46.2 | 31.8 | 37.6 | 14.4 | 0.46 / 0.32 / 0.38 | 121.1 / 106.7 |
| YM 2 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=with majority hold flat | positive pre-2023 | 294 | 20.1 | 5.7 | 11.9 | 14.4 | 0.16 / 0.04 / 0.09 | 91.4 / 77.1 |
| YM 3 (diag) up-day fraction last 20d >= 0.8 (or <= 0.2) dir=with majority hold flat | positive pre-2023 | 50 | 95.9 | 81.5 | 89.2 | 14.4 | 0.48 / 0.42 / 0.45 | 61.9 / 47.5 |
| YM 4 (diag) up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | gross-positive, cost-negative pre-2023 | 1049 | 1.4 | -13.0 | -7.1 | 14.4 | 0.01 / -0.15 / -0.08 | 19.3 / 4.9 |
| GC 1 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | negative pre-2023 | 138 | -71.8 | -96.2 | -86.3 | 24.4 | -0.24 / -0.32 / -0.29 | 240.7 / 216.3 |
| CL 1 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | gross-positive, cost-negative pre-2023 | 183 | 4.5 | -19.8 | -16.4 | 24.4 | 0.02 / -0.09 / -0.07 | 331.3 / 306.9 |
| CL 2 (diag) up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | positive pre-2023 | 612 | 93.3 | 68.9 | 71.7 | 24.4 | 0.68 / 0.51 / 0.53 | 96.2 / 71.9 |
| CL 3 (diag) up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | negative pre-2023 | 399 | -12.2 | -36.6 | -32.2 | 24.4 | -0.07 / -0.22 / -0.19 | 131.3 / 106.9 |
| ZN 1 (diag) up-day fraction last 10d >= 0.8 (or <= 0.2) dir=against majority hold flat | gross-positive, cost-negative pre-2023 | 111 | 25.3 | -10.3 | -15.9 | 35.6 | 0.21 / -0.09 / -0.13 | 159.2 / 123.6 |
| ZN 2 (diag) up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | gross-positive, cost-negative pre-2023 | 235 | 1.4 | -34.2 | -39.0 | 35.6 | 0.02 / -0.39 / -0.45 | 53.6 / 18.0 |
| ZN 3 (diag) up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | gross-positive, cost-negative pre-2023 | 530 | 32.5 | -3.1 | -8.5 | 35.6 | 0.72 / -0.07 / -0.18 | 41.1 / 5.5 |
| BTC 1 up-day fraction last 5d >= 0.8 (or <= 0.2) dir=against majority hold flat | positive pre-2023 | 73 | 529.8 | 475.4 | 508.1 | 54.4 | 0.89 / 0.79 / 0.85 | 1262.1 / 1207.7 |
| BTC 2 up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat | positive pre-2023 | 27 | 71.3 | 16.9 | 51.6 | 54.4 | 0.10 / 0.02 / 0.07 | 779.5 / 725.1 |
| BTC 3 up-day fraction last 5d >= 0.7 (or <= 0.3) dir=against majority hold flat | positive pre-2023 | 140 | 266.6 | 212.2 | 245.0 | 54.4 | 0.69 / 0.55 / 0.63 | 341.8 / 287.4 |
| BTC 4 up-day fraction last 10d >= 0.7 (or <= 0.3) dir=with majority hold flat | gross-positive, cost-negative pre-2023 | 100 | 48.0 | -6.4 | 26.3 | 54.4 | 0.12 / -0.02 / 0.06 | 426.3 / 371.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): BTC: 4 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.03, p(top) = 0.45); CL: 0 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 1.00); ES: 1 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 0.87, p(top) = 0.85); GC: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00); NQ: 1 cells pass the clean rule against a replicate mean of 2.0 (p(count) = 0.92, p(top) = 0.92); RTY: 4 cells pass the clean rule against a replicate mean of 1.3 (p(count) = 0.02, p(top) = 0.20); YM: 1 cells pass the clean rule against a replicate mean of 1.6 (p(count) = 0.83, p(top) = 0.38); ZN: 0 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 1.00).
- Of 11 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.15 (ES up-day fraction last 20d >= 0.7 (or <= 0.3) dir=against majority hold flat); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'positive pre-2023': 8, 'gross-positive, cost-negative pre-2023': 2, 'negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_8.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm8/ (`BM8_CO_all_selected_scored.csv`).

## Lead note
- BTC, up-day fraction of the last 20 days >= 0.7 (or <= 0.3), AGAINST the majority, flat: uplift +0.09/+0.30/+0.15 at 20% (gate-3 at 30/50%), null rank 0.96, 102 pair-window trades; FAILS bootstrap (lo -0.03), worst-decile correlation +0.41, worst week +27% at 20% share; BTC-only (the equity indices do not show it). LEAD gate-3 only.

DONE BM8
