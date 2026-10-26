# REPORT Q28 - Q28: daily maintenance-break gap (Mon-Thu 18:00 reopen vs previous close), with/against

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 7 selected cells (+24 diagnostic) scored on 8 instruments; best non-diagnostic all-in additive uplift at 20% share +0.01; best pair-window standalone Sharpe +1.18.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Rule: daily maintenance-break gap (Mon-Thu 18:00 reopen vs previous close), with/against. Time exit, no stop.
- Instruments: ES, NQ, RTY, GC, CL, ZN, HO, 6E. Grid: 36 cells
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. Note: no stop means unbounded single-trade loss; the worst single trade is in the CSV (worst_trade).. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| 6E    |      36 |         12 |         0 |               1.356 |                2 |          0 |            3 |
| CL    |      36 |         12 |         0 |               0.989 |                2 |          0 |            3 |
| ES    |      36 |         12 |         0 |               0.671 |                2 |          0 |            3 |
| GC    |      36 |          0 |         0 |               0.865 |                2 |          0 |            3 |
| HO    |      36 |         12 |         2 |               1.23  |                2 |          2 |            3 |
| NQ    |      36 |         12 |         5 |               0.918 |                2 |          5 |            3 |
| RTY   |      36 |         12 |         0 |               1.263 |                2 |          0 |            3 |
| ZN    |      36 |         12 |         0 |               1.152 |                1 |          0 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    0 |            1.365 |               6 |      1     |                     nan     |            0.674 |           1.207 |  nan     |     nan     |                1.426 |
| NQ    |     200 |                    5 |            2.515 |               8 |      0.09  |                       0.355 |            0.741 |           1.185 |    0.905 |       0.564 |                1.591 |
| RTY   |     200 |                    0 |            1.7   |               6 |      1     |                     nan     |            0.712 |           1.286 |  nan     |     nan     |                1.5   |
| GC    |     200 |                    0 |            1.715 |               5 |      1     |                     nan     |            0.708 |           1.261 |  nan     |     nan     |                1.602 |
| CL    |     200 |                    0 |            1.225 |               4 |      1     |                     nan     |            0.612 |           1.076 |  nan     |     nan     |                1.247 |
| ZN    |     200 |                    0 |            0     |               0 |      1     |                     nan     |          nan     |         nan     |  nan     |     nan     |              nan     |
| HO    |     200 |                    2 |            3.515 |               8 |      0.885 |                       0.882 |            0.736 |           1.167 |    0.255 |       1.175 |                1.846 |
| 6E    |     200 |                    0 |            0.39  |               2 |      1     |                     nan     |            0.597 |           1.304 |  nan     |     nan     |                1.348 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) | gap (5, 0.1, 180, -1) | 19 | 2 | 0.67 | 0.30 | -0.05 | -0.24 / 1.70 | 0.01 / -0.25 / -1.21 | -0.41 | 0.21 | 0.42 | -0.99 | 0.00 | 31 S | diag |
| ES 2 (diag) | gap (15, 0.1, 180, -1) | 19 | 2 | 0.67 | 0.37 | -0.06 | -0.30 / 1.29 | 0.06 / -0.27 / -1.02 | -0.30 | 0.21 | 0.51 | -0.80 | 0.00 | 31 S | diag |
| ES 3 (diag) | gap (5, 0.1, 60, 1) | 19 | 1 | 0.66 | -0.07 | 0.92 | 1.24 / 1.34 | 0.08 / 0.44 / 0.81 | 0.24 | -0.22 | 1.00 | 0.02 | 1.00 | 31 S | diag |
| NQ 1 | gap (15, 0.02, 120, 1) | 147 | 2 | 0.56 | -0.63 | 0.06 | -0.45 / 1.20 | 0.09 / -0.13 / -0.11 | -0.01 | -0.12 | 0.61 | -0.23 | 0.00 | 243 | NO |
| NQ 2 | gap (5, 0.02, 120, 1) | 147 | 2 | 0.49 | -0.31 | -0.02 | -0.47 / 1.31 | 0.06 / -0.38 / 0.05 | -0.03 | -0.03 | 0.53 | -0.29 | 0.00 | 243 | NO |
| NQ 3 | gap (5, 0.02, 180, 1) | 147 | 2 | 0.36 | -0.46 | -0.23 | -0.80 / 1.11 | 0.06 / -0.31 / -0.41 | -0.10 | -0.07 | 0.51 | -0.36 | 0.00 | 243 | NO |
| NQ 4 | gap (5, 0.02, 60, 1) | 147 | 2 | 0.19 | -0.53 | -0.03 | -0.20 / 1.49 | 0.01 / -0.51 / 0.15 | -0.07 | -0.14 | 0.66 | -0.34 | 0.00 | 243 | NO |
| NQ 5 | gap (15, 0.02, 180, 1) | 147 | 2 | 0.17 | -0.52 | -0.28 | -0.79 / 1.32 | 0.02 / -0.11 / -0.48 | -0.11 | -0.11 | 0.38 | -0.35 | 0.00 | 243 | NO |
| NQ 6 (diag) | gap (5, 0.05, 60, 1) | 53 | 2 | 0.92 | -0.39 | 1.18 | 1.55 / 1.34 | 0.12 / 0.17 / 1.22 | 0.33 | -0.08 | 1.00 | 0.05 | 1.00 | 90 S | diag |
| NQ 7 (diag) | gap (5, 0.05, 120, 1) | 53 | 2 | 0.48 | -0.46 | 0.81 | 1.15 / 1.51 | 0.05 / 0.10 / 0.88 | 0.22 | -0.05 | 0.89 | -0.08 | 0.50 | 90 S | diag |
| NQ 8 (diag) | gap (5, 0.1, 180, -1) | 22 | 2 | 0.40 | 0.34 | -0.37 | -0.73 / 1.54 | 0.00 / -0.03 / -1.63 | -0.49 | 0.11 | 0.27 | -1.03 | 0.00 | 34 S | diag |
| RTY 1 (diag) | gap (5, 0.05, 60, 1) | 29 | 2 | 1.26 | -1.19 | 0.74 | 0.64 / 1.14 | 0.19 / -0.06 / 0.32 | 0.15 | -0.05 | 0.95 | -0.10 | 0.00 | 49 S | diag |
| RTY 2 (diag) | gap (15, 0.05, 60, 1) | 29 | 2 | 0.86 | -1.38 | 0.69 | 0.72 / 1.39 | 0.09 / -0.28 / 0.64 | 0.11 | -0.11 | 0.93 | -0.10 | 1.00 | 49 S | diag |
| RTY 3 (diag) | gap (5, 0.1, 60, 1) | 10 | 1 | 0.80 | -0.20 | 0.66 | 0.86 / 1.34 | 0.10 / 0.00 / 0.28 | 0.12 | -0.21 | 0.91 | -0.03 | 0.50 | 13 S | diag |
| GC 1 (diag) | gap (15, 0.05, 180, -1) | 12 | 1 | 0.86 | -0.16 | -0.03 | -0.25 / 1.40 | 0.05 / -0.88 / -1.90 | -0.55 | 0.21 | 0.44 | -1.09 | 0.00 | 25 S | diag |
| GC 2 (diag) | gap (15, 0.05, 120, -1) | 12 | 2 | 0.79 | -0.27 | -0.35 | -0.68 / 1.43 | 0.08 / -2.02 / -2.67 | -1.19 | 0.21 | 0.32 | -2.01 | 0.00 | 25 S | diag |
| GC 3 (diag) | gap (5, 0.05, 180, -1) | 12 | 1 | 0.66 | -0.22 | -0.02 | -0.21 / 1.28 | 0.02 / -1.00 / -1.35 | -0.44 | 0.21 | 0.60 | -0.94 | 0.00 | 25 S | diag |
| CL 1 (diag) | gap (5, 0.1, 180, -1) | 9 | 2 | 0.99 | -0.17 | -0.60 | -1.12 /  | 0.16 / -0.01 / -3.04 | -1.35 | 0.20 | 0.15 | -2.13 | 0.00 | 19 S | diag |
| CL 2 (diag) | gap (5, 0.1, 60, -1) | 9 | 2 | 0.81 | -0.32 | -0.61 | -1.14 /  | 0.15 / -0.10 / -2.91 | -1.23 | 0.21 | 0.29 | -1.99 | 0.00 | 19 S | diag |
| CL 3 (diag) | gap (5, 0.1, 120, -1) | 9 | 2 | 0.76 | -0.41 | -0.61 | -1.15 /  | 0.13 / -0.20 / -2.75 | -1.10 | 0.20 | 0.19 | -1.86 | 0.00 | 19 S | diag |
| ZN 1 (diag) | gap (5, 0.1, 60, 1) | 5 | 1 | 1.15 | -0.98 | 0.54 | -1.43 / 0.08 | 0.15 / -0.10 / -0.20 | -0.09 | 0.01 | 1.00 | -0.09 | 0.00 | 8 S | diag |
| ZN 2 (diag) | gap (5, 0.1, 120, 1) | 5 | 1 | 0.63 | -0.75 | 0.09 | -1.57 / 0.56 | 0.03 / -0.23 / -0.19 | -0.16 | 0.01 | 0.90 | -0.21 | 0.00 | 8 S | diag |
| ZN 3 (diag) | gap (5, 0.1, 180, 1) | 5 | 1 | 0.53 | -0.46 | -0.05 | -1.17 / 0.87 | 0.03 / 0.07 / -0.38 | -0.20 | -0.01 | 0.76 | -0.23 | 0.00 | 8 S | diag |
| HO 1 | gap (5, 0.02, 180, -1) | 185 | 2 | 1.18 | 0.14 | -0.11 | -0.46 / 1.65 | 0.22 / 0.04 / -1.91 | -0.63 | 0.19 | 0.46 | -1.42 | 0.00 | 338 | NO |
| HO 2 | gap (5, 0.02, 120, -1) | 185 | 2 | 0.59 | -0.03 | -0.30 | -0.64 / 1.18 | 0.12 / -0.23 / -2.14 | -0.85 | 0.18 | 0.38 | -1.60 | 0.00 | 338 | NO |
| HO 3 (diag) | gap (5, 0.05, 180, -1) | 56 | 2 | 1.23 | -0.07 | -0.26 | -0.62 / 1.62 | 0.24 / 0.26 / -2.41 | -0.98 | 0.19 | 0.48 | -1.82 | 0.00 | 122 | diag |
| HO 4 (diag) | gap (15, 0.02, 180, -1) | 173 | 1 | 0.84 | -0.07 | -0.14 | -0.46 / 1.24 | 0.19 / 0.22 / -1.80 | -0.55 | 0.15 | 0.49 | -1.30 | 0.00 | 320 | diag |
| HO 5 (diag) | gap (15, 0.02, 120, -1) | 173 | 1 | 0.82 | -0.31 | -0.47 | -0.95 / 1.08 | 0.16 / -0.07 / -2.50 | -0.95 | 0.18 | 0.28 | -1.69 | 0.00 | 320 | diag |
| 6E 1 (diag) | gap (5, 0.1, 180, -1) | 5 | 2 | 1.36 | 0.21 | 1.06 |  / 1.15 | 0.14 / 0.00 / 0.00 | 0.07 |  | 1.00 | -0.01 | 1.00 | 5 S | diag |
| 6E 2 (diag) | gap (15, 0.1, 180, -1) | 5 | 2 | 1.23 | 0.22 | 0.96 |  / 1.14 | 0.14 / 0.00 / 0.00 | 0.07 |  | 0.97 | 0.01 | 1.00 | 5 S | diag |
| 6E 3 (diag) | gap (5, 0.1, 120, -1) | 5 | 2 | 1.09 | -0.05 | 0.86 |  / 1.47 | 0.12 / 0.00 / 0.00 | 0.06 |  | 0.97 | 0.00 | 0.50 | 5 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 7 |
| diagnostic cells read | 24 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 11 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 4 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 28 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 6 |
| small-sample (<100 trades pair window) | 21 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E gap (15, 0.1, 180, -1) (diag) | clean | 1.22 |  | 0 | 0 | 0 | 0 |  | 0.0 | 1.60 | -78736 | 280110 | -81874 |
| 6E gap (15, 0.1, 180, -1) (diag) | H1 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.83 | -77610 | 151713 | -78287 |
| 6E gap (15, 0.1, 180, -1) (diag) | H2 |  |  | 0 | 0 | 0 | 0 |  | 0.0 | 2.48 | -81089 | 217425 | -82524 |
| 6E gap (15, 0.1, 180, -1) (diag) | all | 0.96 |  | 0 | 0 | 0 | 0 |  | 0.0 | 1.97 | -79220 | 280110 | -82524 |
| CL gap (5, 0.1, 120, -1) (diag) | clean | 0.76 | 2.16 | -46393 | -25305 | 278358 | -219704 | 2.47 | 2.9 | 1.59 | -78301 | 280110 | -81874 |
| CL gap (5, 0.1, 120, -1) (diag) | H1 | -1.36 | -1.36 | -59675 | -39783 | 119350 | -119350 | -1.00 | 3.6 | 2.63 | -89545 | 151713 | -102157 |
| CL gap (5, 0.1, 120, -1) (diag) | H2 | -1.50 | -1.49 | -2558002 | -1407300 | 5528469 | -4062666 | -0.95 | 13.9 | -0.27 | -546239 | 982034 | -892187 |
| CL gap (5, 0.1, 120, -1) (diag) | all | -0.61 | -0.61 | -672423 | -355989 | 5647819 | -4062666 | -0.83 | 5.4 | 0.82 | -185534 | 982034 | -892187 |
| ES gap (5, 0.1, 60, 1) (diag) | clean | 0.79 | 1.73 | -113632 | -66714 | 442098 | -152287 | 1.65 | 6.7 | 1.54 | -78736 | 332892 | -81874 |
| ES gap (5, 0.1, 60, 1) (diag) | H1 | 1.40 | 2.88 | -95633 | -63755 | 191265 | -191265 | 2.11 | 3.6 | 3.27 | -77610 | 151713 | -78287 |
| ES gap (5, 0.1, 60, 1) (diag) | H2 | 1.43 | 30.00 | -63194 | -31597 | 126387 | -68762 | 17.72 | 5.6 | 3.29 | -86712 | 214473 | -90899 |
| ES gap (5, 0.1, 60, 1) (diag) | all | 0.92 | 5.14 | -111050 | -61853 | 442098 | -191265 | 7.64 | 6.0 | 2.18 | -80470 | 332892 | -90899 |
| GC gap (5, 0.05, 180, -1) (diag) | clean | 0.66 | 1.89 | -56406 | -30909 | 273608 | -212258 | 2.18 | 6.7 | 1.48 | -78736 | 280110 | -81874 |
| GC gap (5, 0.05, 180, -1) (diag) | H1 | 0.53 | 1.17 | -646143 | -430762 | 1183206 | -1183206 | 0.86 | 7.1 | 1.83 | -170656 | 308737 | -263025 |
| GC gap (5, 0.05, 180, -1) (diag) | H2 | -1.72 | -1.74 | -688500 | -518530 | 1881606 | -711850 | -0.90 | 11.1 | 1.13 | -207629 | 313316 | -222024 |
| GC gap (5, 0.05, 180, -1) (diag) | all | -0.02 | -0.03 | -407147 | -218024 | 3064812 | -1183206 | -0.03 | 7.7 | 1.46 | -128515 | 384264 | -263025 |
| HO gap (5, 0.02, 180, -1) | clean | 1.22 | 2.87 | -82565 | -72262 | 615073 | -102102 | 1.80 | 44.8 | 1.68 | -85515 | 246784 | -92255 |
| HO gap (5, 0.02, 180, -1) | H1 | 0.59 | 0.76 | -237543 | -185199 | 505317 | -374437 | 0.45 | 32.1 | 2.86 | -87628 | 143590 | -93035 |
| HO gap (5, 0.02, 180, -1) | H2 | -0.70 | -0.74 | -1862976 | -1072468 | 3528889 | -3214102 | -0.58 | 41.7 | 0.57 | -398785 | 745678 | -722474 |
| HO gap (5, 0.02, 180, -1) | all | -0.11 | -0.12 | -596293 | -353752 | 3528889 | -3214102 | -0.20 | 42.3 | 1.30 | -156758 | 745678 | -722474 |
| NQ gap (15, 0.02, 120, 1) | clean | 0.59 | 1.08 | -118989 | -92185 | 511893 | -176917 | 1.04 | 32.4 | 1.55 | -81941 | 267413 | -92058 |
| NQ gap (15, 0.02, 120, 1) | H1 | -0.10 | -0.14 | -89116 | -83039 | 301452 | -102993 | -0.06 | 35.7 | 2.69 | -77242 | 166938 | -80905 |
| NQ gap (15, 0.02, 120, 1) | H2 | -0.61 | -0.90 | -245967 | -229492 | 1226292 | -246220 | -0.32 | 50.0 | 2.37 | -83147 | 214593 | -84838 |
| NQ gap (15, 0.02, 120, 1) | all | 0.06 | 0.10 | -183759 | -135170 | 1226292 | -246220 | 0.10 | 36.9 | 1.90 | -82094 | 267413 | -92058 |
| RTY gap (5, 0.05, 60, 1) (diag) | clean | 1.26 | 2.97 | -98941 | -60002 | 308953 | -184257 | 3.69 | 9.5 | 1.65 | -78277 | 264944 | -81874 |
| RTY gap (5, 0.05, 60, 1) (diag) | H1 | -1.18 | -1.33 | -66002 | -51423 | 138070 | -100021 | -0.76 | 14.3 | 2.77 | -77610 | 151713 | -78287 |
| RTY gap (5, 0.05, 60, 1) (diag) | H2 | 0.94 | 3.85 | -231028 | -157321 | 462056 | -355970 | 2.73 | 22.2 | 2.80 | -115567 | 228923 | -153719 |
| RTY gap (5, 0.05, 60, 1) (diag) | all | 0.74 | 2.61 | -135927 | -88156 | 462056 | -355970 | 4.97 | 13.1 | 2.08 | -86565 | 264944 | -153719 |
| ZN gap (5, 0.1, 60, 1) (diag) | clean | 1.15 | 6.67 | -18281 | -9972 | 109687 | -109687 | 9.48 | 1.0 | 1.61 | -78736 | 280110 | -81874 |
| ZN gap (5, 0.1, 60, 1) (diag) | H1 | -1.36 | -1.36 | -30779 | -20519 | 61558 | -61558 | -1.00 | 3.6 | 2.72 | -83766 | 151713 | -90599 |
| ZN gap (5, 0.1, 60, 1) (diag) | H2 | -1.65 | -1.63 | -157816 | -78908 | 315631 | -205944 | -1.00 | 5.6 | 2.29 | -81089 | 217425 | -82524 |
| ZN gap (5, 0.1, 60, 1) (diag) | all | 0.54 | 1.39 | -54097 | -28640 | 377190 | -205944 | 1.76 | 2.4 | 1.93 | -80588 | 280110 | -90599 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES gap (5, 0.1, 60, 1) (diag) | 6.9 | 9.6 | 26.2 | 1.7 | 23.4 / 28.2 | 30.0 / 30.0 | NO |
| NQ gap (15, 0.02, 120, 1) | -28.7 | 5.0 | 20.3 | 27.9 | 11.3 / 23.2 | 23.6 / 29.7 | NO |
| RTY gap (5, 0.05, 60, 1) (diag) | -4.9 | -99.4 | 15.5 | 27.1 | 30.0 / 30.4 | 30.0 / 30.0 | NO |
| GC gap (5, 0.05, 180, -1) (diag) | -30.9 | -352.5 | -84.6 | -143.3 | 30.0 / 30.0 | -377.0 / -175.9 | NO |
| CL gap (5, 0.1, 120, -1) (diag) | -81.0 | -1444.5 | -182.5 | -437.6 | 30.0 / 30.4 | -15.7 / 6.9 | NO |
| ZN gap (5, 0.1, 60, 1) (diag) | -22.8 | 11.2 | 26.1 | 30.0 | 30.0 / 30.0 | 6.4 / 18.1 | NO |
| HO gap (5, 0.02, 180, -1) | -37.7 | -1136.0 | -122.1 | -269.9 | 6.9 / 16.4 | 0.4 / 10.6 | NO |
| 6E gap (15, 0.1, 180, -1) (diag) | -17.9 | 30.0 | 30.0 | 30.0 | 30.0 / 30.0 | 30.0 / 30.0 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 (diag) gap (5, 0.1, 180, -1) | positive pre-2023 | 59 | 116.7 | 87.4 | 101.2 | 29.4 | 0.40 / 0.30 / 0.35 | 77.6 / 48.3 |
| ES 2 (diag) gap (15, 0.1, 180, -1) | positive pre-2023 | 59 | 140.7 | 111.3 | 125.1 | 29.4 | 0.47 / 0.37 / 0.42 | 89.5 / 60.1 |
| ES 3 (diag) gap (5, 0.1, 60, 1) | gross-positive, cost-negative pre-2023 | 59 | 20.6 | -8.8 | 5.0 | 29.4 | 0.16 / -0.07 / 0.04 | 115.8 / 86.4 |
| NQ 1 gap (15, 0.02, 120, 1) | negative pre-2023 | 879 | -13.5 | -27.9 | -18.8 | 14.4 | -0.30 / -0.63 / -0.42 | 81.4 / 67.0 |
| NQ 2 gap (5, 0.02, 120, 1) | gross-positive, cost-negative pre-2023 | 880 | 0.5 | -13.9 | -4.7 | 14.4 | 0.01 / -0.31 / -0.11 | 67.8 / 53.4 |
| NQ 3 gap (5, 0.02, 180, 1) | negative pre-2023 | 880 | -9.3 | -23.7 | -14.5 | 14.4 | -0.18 / -0.46 / -0.28 | 69.6 / 55.2 |
| NQ 4 gap (5, 0.02, 60, 1) | negative pre-2023 | 880 | -2.9 | -17.2 | -8.1 | 14.4 | -0.09 / -0.53 / -0.25 | 26.6 / 12.2 |
| NQ 5 gap (15, 0.02, 180, 1) | negative pre-2023 | 879 | -13.0 | -27.3 | -18.2 | 14.4 | -0.25 / -0.52 / -0.34 | 44.4 / 30.0 |
| NQ 6 (diag) gap (5, 0.05, 60, 1) | negative pre-2023 | 224 | -19.3 | -33.7 | -24.6 | 14.4 | -0.22 / -0.39 / -0.28 | 122.1 / 107.7 |
| NQ 7 (diag) gap (5, 0.05, 120, 1) | negative pre-2023 | 224 | -29.7 | -44.1 | -35.0 | 14.4 | -0.31 / -0.46 / -0.36 | 98.7 / 84.3 |
| NQ 8 (diag) gap (5, 0.1, 180, -1) | positive pre-2023 | 63 | 162.0 | 147.6 | 156.1 | 14.4 | 0.37 / 0.34 / 0.36 | 73.9 / 59.5 |
| RTY 1 (diag) gap (5, 0.05, 60, 1) | negative pre-2023 | 112 | -33.2 | -47.5 | -44.7 | 14.4 | -0.85 / -1.19 / -1.12 | 75.0 / 60.6 |
| RTY 2 (diag) gap (15, 0.05, 60, 1) | negative pre-2023 | 110 | -33.2 | -47.5 | -44.8 | 14.4 | -0.99 / -1.38 / -1.31 | 59.8 / 45.5 |
| RTY 3 (diag) gap (5, 0.1, 60, 1) | negative pre-2023 | 27 | -4.1 | -18.4 | -15.0 | 14.4 | -0.04 / -0.20 / -0.16 | 77.0 / 62.6 |
| GC 1 (diag) gap (15, 0.05, 180, -1) | negative pre-2023 | 147 | -4.2 | -28.6 | -18.1 | 24.4 | -0.02 / -0.16 / -0.10 | 515.0 / 490.6 |
| GC 2 (diag) gap (15, 0.05, 120, -1) | negative pre-2023 | 147 | -7.2 | -31.6 | -21.1 | 24.4 | -0.06 / -0.27 / -0.18 | 230.0 / 205.6 |
| GC 3 (diag) gap (5, 0.05, 180, -1) | negative pre-2023 | 149 | -12.9 | -37.2 | -26.7 | 24.4 | -0.08 / -0.22 / -0.16 | 481.7 / 457.3 |
| CL 1 (diag) gap (5, 0.1, 180, -1) | negative pre-2023 | 20 | -64.5 | -88.9 | -87.8 | 24.4 | -0.13 / -0.17 / -0.17 | 230.0 / 205.6 |
| CL 2 (diag) gap (5, 0.1, 60, -1) | negative pre-2023 | 20 | -111.5 | -135.9 | -134.8 | 24.4 | -0.26 / -0.32 / -0.32 | 240.0 / 215.6 |
| CL 3 (diag) gap (5, 0.1, 120, -1) | negative pre-2023 | 20 | -158.0 | -182.4 | -181.3 | 24.4 | -0.36 / -0.41 / -0.41 | 283.3 / 259.0 |
| ZN 1 (diag) gap (5, 0.1, 60, 1) | negative pre-2023 | 64 | -5.6 | -41.2 | -46.8 | 35.6 | -0.15 / -0.98 / -1.09 | 103.1 / 67.5 |
| ZN 2 (diag) gap (5, 0.1, 120, 1) | gross-positive, cost-negative pre-2023 | 64 | 4.6 | -31.0 | -36.5 | 35.6 | 0.12 / -0.75 / -0.87 | 78.1 / 42.5 |
| ZN 3 (diag) gap (5, 0.1, 180, 1) | gross-positive, cost-negative pre-2023 | 64 | 6.1 | -29.5 | -35.1 | 35.6 | 0.10 / -0.46 / -0.55 | 62.5 / 26.9 |
| HO 1 gap (5, 0.02, 180, -1) | positive pre-2023 | 1239 | 17.3 | 4.5 | 6.1 | 12.8 | 0.53 / 0.14 / 0.19 | 64.0 / 51.2 |
| HO 2 gap (5, 0.02, 120, -1) | gross-positive, cost-negative pre-2023 | 1239 | 12.0 | -0.8 | 0.8 | 12.8 | 0.50 / -0.03 / 0.03 | 35.0 / 22.2 |
| HO 3 (diag) gap (5, 0.05, 180, -1) | gross-positive, cost-negative pre-2023 | 515 | 8.6 | -4.2 | -3.0 | 12.8 | 0.15 / -0.07 / -0.05 | 111.7 / 98.9 |
| HO 4 (diag) gap (15, 0.02, 180, -1) | gross-positive, cost-negative pre-2023 | 1124 | 10.4 | -2.4 | -0.9 | 12.8 | 0.31 / -0.07 / -0.03 | 64.0 / 51.2 |
| HO 5 (diag) gap (15, 0.02, 120, -1) | gross-positive, cost-negative pre-2023 | 1124 | 4.6 | -8.2 | -6.7 | 12.8 | 0.17 / -0.31 / -0.25 | 44.5 / 31.8 |
| 6E 1 (diag) gap (5, 0.1, 180, -1) | positive pre-2023 | 125 | 32.5 | 15.6 | 13.7 | 16.9 | 0.42 / 0.21 / 0.18 | 366.2 / 349.4 |
| 6E 2 (diag) gap (15, 0.1, 180, -1) | positive pre-2023 | 125 | 37.0 | 20.1 | 18.2 | 16.9 | 0.40 / 0.22 / 0.20 | 402.5 / 385.6 |
| 6E 3 (diag) gap (5, 0.1, 120, -1) | gross-positive, cost-negative pre-2023 | 125 | 14.3 | -2.6 | -4.6 | 16.9 | 0.28 / -0.05 / -0.09 | 263.7 / 246.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 200 timing-destroyed replicates): 6E: 0 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 1.00); CL: 0 cells pass the clean rule against a replicate mean of 1.2 (p(count) = 1.00); ES: 0 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 1.00); GC: 0 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 1.00); HO: 2 cells pass the clean rule against a replicate mean of 3.5 (p(count) = 0.89, p(top) = 0.26); NQ: 5 cells pass the clean rule against a replicate mean of 2.5 (p(count) = 0.09, p(top) = 0.91); RTY: 0 cells pass the clean rule against a replicate mean of 1.7 (p(count) = 1.00); ZN: 0 cells pass the clean rule against a replicate mean of 0.0 (p(count) = 1.00).
- Of 7 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.01 (NQ gap (15, 0.02, 120, 1)); bootstrap lower bound > 0 for 0 cells; plateau >= 0.75 for 0; 2x-slippage all-in uplift >= +0.10 for 0; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 4, 'gross-positive, cost-negative pre-2023': 2, 'positive pre-2023': 1}.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q28.py (ap_q_ev.py), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q28/ (`Q28_CO_all_selected_scored.csv`).

DONE Q28
