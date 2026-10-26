# REPORT BM1 - LETF end-of-day rebalancing (BM batch)

**Verdict: LEAD (strong, NQ-only; the pipeline label FOUND-CANDIDATE is withheld because the replication leg fails: H0 +0.06, even months +0.00, ES/RTY/YM do not replicate; ERA negative pre-2023; direction opposite to the registered sign). FOUND 0.** 16 selected cells (+12 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.29; best pair-window standalone Sharpe +1.47.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see IDEAS_BM.md / PREREG_AUTOPILOT.md BATCH BM. LETF end-of-day rebalancing. Null: drift- and clock-matched random entries.
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |      18 |         12 |         5 |               1.319 |                2 |          5 |            3 |
| NQ    |      18 |         12 |         6 |               1.803 |                2 |          6 |            3 |
| RTY   |      18 |         12 |         3 |               0.983 |                2 |          3 |            3 |
| YM    |      18 |         12 |         2 |               0.802 |                2 |          2 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    5 |            1.015 |               4 |      0     |                       0.721 |            0.602 |           1.07  |    0.235 |       1.319 |                1.291 |
| NQ    |     200 |                    6 |            2.23  |               6 |      0.005 |                       1.384 |            0.721 |           1.309 |    0.025 |       1.803 |                1.716 |
| RTY   |     200 |                    3 |            1     |               4 |      0.075 |                       0.607 |            0.618 |           1.129 |    0.315 |       0.768 |                1.391 |
| YM    |     200 |                    2 |            1.365 |               5 |      0.375 |                       0.472 |            0.662 |           1.173 |    0.57  |       0.802 |                1.46  |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 131 | 2 | 1.32 | -0.81 | 0.07 | -1.93 / 0.81 | 0.24 / -0.38 / -0.36 | -0.08 | 0.19 | 0.84 | -0.17 | 0.50 | 212 | NO |
| ES 2 | entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 137 | 2 | 0.89 | -0.99 | 0.85 | 0.61 / 0.71 | 0.15 / -0.02 / 0.21 | 0.05 | -0.14 | 0.99 | -0.04 | 0.00 | 221 | NO |
| ES 3 | entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 231 | 2 | 0.68 | -1.25 | 0.28 | -0.39 / 0.72 | 0.11 / 0.08 / -0.20 | -0.09 | 0.33 | 0.97 | -0.17 | 0.50 | 392 | NO |
| ES 4 | entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 131 | 2 | 0.50 | -0.94 | 0.26 | -0.12 / 1.30 | 0.07 / -0.20 / 0.02 | -0.05 | 0.19 | 0.85 | -0.16 | 0.50 | 207 | NO |
| ES 5 | entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 230 | 2 | 0.21 | -1.58 | 0.48 | 0.75 / 0.90 | 0.01 / -0.04 / 0.33 | -0.07 | 0.29 | 0.98 | -0.13 | 0.00 | 393 | NO |
| ES 6 (diag) | entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 70 | 1 | 0.41 | -0.23 | 0.02 | -0.76 / 0.92 | 0.11 / -0.44 / -0.01 | -0.04 | -0.15 | 0.74 | -0.15 | 0.50 | 103 | diag |
| ES 7 (diag) | entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 66 | 1 | 0.29 | -0.46 | 0.31 | 0.35 / 1.15 | 0.03 / -0.32 / 0.22 | -0.03 | -0.45 | 0.90 | -0.15 | 0.50 | 102 | diag |
| ES 8 (diag) | entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 228 | 1 | 0.14 | -1.21 | -0.06 | -0.39 / 1.13 | 0.01 / 0.15 / -0.19 | -0.13 | 0.66 | 0.74 | -0.22 | 0.00 | 387 | diag |
| NQ 1 | entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 146 | 2 | 1.80 | -0.78 | 0.59 | -1.01 / 1.45 | 0.28 / -0.35 / -0.23 | 0.04 | 0.29 | 0.90 | -0.14 | 0.50 | 235 | NO |
| NQ 2 | entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 253 | 2 | 1.37 | -1.11 | 0.99 | 0.43 / 1.24 | 0.26 / 0.30 / 0.01 | 0.17 | -0.20 | 0.97 | 0.01 | 1.00 | 415 | NO |
| NQ 3 | entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 243 | 2 | 1.33 | -1.48 | 1.47 | 1.67 / 1.29 | 0.23 / 0.40 / 0.45 | 0.27 | -0.20 | 1.00 | 0.10 | 1.00 | 404 | FOUND-CAND |
| NQ 4 | entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 138 | 2 | 1.33 | -1.24 | 0.78 | 0.10 / 1.58 | 0.19 / -0.32 / 0.17 | 0.08 | 0.65 | 0.90 | -0.08 | 1.00 | 227 | NO |
| NQ 5 | entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 138 | 2 | 1.28 | -0.86 | 0.80 | -0.07 / 1.54 | 0.18 / -0.51 / 0.26 | 0.07 | -0.09 | 0.96 | -0.09 | 0.50 | 228 | NO |
| NQ 6 | entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 241 | 2 | 1.20 | -1.38 | 1.12 | 1.08 / 1.21 | 0.17 / 0.01 / 0.36 | 0.15 | 0.13 | 1.00 | 0.00 | 0.50 | 402 | NO |
| NQ 7 (diag) | entry 15:20 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 67 | 1 | 0.79 | -0.58 | 0.58 | 0.25 / 1.67 | 0.14 / -0.16 / 0.18 | 0.09 | 0.77 | 0.85 | -0.07 | 0.50 | 104 | diag |
| NQ 8 (diag) | entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 68 | 2 | 0.76 | -0.22 | -0.18 | -1.90 / 1.56 | 0.16 / -0.15 / -0.45 | -0.04 | 0.33 | 0.40 | -0.20 | 0.00 | 103 | diag |
| NQ 9 (diag) | entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 70 | 2 | 0.70 | -0.48 | 0.02 | -1.39 / 1.47 | 0.10 / -0.57 / 0.01 | -0.04 | -0.24 | 0.61 | -0.19 | 0.00 | 108 | diag |
| RTY 1 | entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 249 | 2 | 0.77 | -1.14 | 0.53 | 0.13 / 0.86 | 0.10 / -0.08 / 0.03 | -0.04 | 0.16 | 0.98 | -0.13 | 0.50 | 405 | NO |
| RTY 2 | entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 119 | 2 | 0.67 | -0.60 | 0.34 | -0.23 / 1.11 | 0.10 / -0.17 / -0.10 | -0.03 | 0.22 | 0.91 | -0.15 | 0.50 | 195 | NO |
| RTY 3 | entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 244 | 2 | 0.38 | -1.07 | 0.22 | -0.01 / 0.87 | 0.02 / -0.27 / 0.12 | -0.09 | 0.32 | 0.95 | -0.19 | 0.00 | 399 | NO |
| RTY 4 (diag) | entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 54 | 2 | 0.98 | 0.11 | 0.48 | -0.36 / 1.26 | 0.14 / -0.31 / 0.04 | 0.00 | 0.09 | 0.95 | -0.11 | 0.00 | 93 S | diag |
| RTY 5 (diag) | entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 50 | 1 | 0.44 | 0.11 | 0.07 | -0.39 / 1.06 | 0.08 / -0.46 / -0.09 | -0.07 | -0.08 | 0.79 | -0.21 | 0.00 | 87 S | diag |
| RTY 6 (diag) | entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 122 | 1 | 0.20 | -0.23 | -0.04 | -0.37 / 0.84 | 0.01 / -0.10 / -0.31 | -0.14 | 0.01 | 0.83 | -0.25 | 0.00 | 198 | diag |
| YM 1 | entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | 128 | 2 | 0.80 | -0.37 | 0.24 | -1.01 / 1.16 | 0.14 / -0.20 / -0.23 | -0.03 | -0.29 | 0.89 | -0.18 | 0.00 | 208 | NO |
| YM 2 | entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 244 | 2 | 0.14 | -0.93 | 0.43 | 1.00 / 0.73 | -0.02 / 0.13 / 0.15 | -0.04 | 0.05 | 0.98 | -0.14 | 1.00 | 401 | NO |
| YM 3 (diag) | entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 66 | 1 | 0.46 | -0.38 | 0.54 | 0.74 / 1.03 | 0.07 / -0.08 / 0.10 | 0.02 | -0.13 | 0.96 | -0.11 | 0.00 | 105 | diag |
| YM 4 (diag) | entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | 245 | 1 | 0.43 | -0.53 | -0.01 | -0.87 / 0.77 | 0.04 / 0.09 / -0.33 | -0.11 | -0.12 | 0.85 | -0.21 | 0.00 | 401 | diag |
| YM 5 (diag) | entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | 59 | 1 | 0.39 | -0.31 | -0.13 | -1.02 / 1.08 | 0.08 / -0.46 / -0.20 | -0.08 | -0.04 | 0.61 | -0.24 | 0.00 | 95 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 16 |
| diagnostic cells read | 12 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 1 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 20 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 12 |
| worst-decile corr <= +0.30 | 22 |
| plateau >= 0.75 | 4 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 3 |
| gate_add PASS at any share (non-diag) | 4 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | clean | 0.98 | 1.55 | -120019 | -86650 | 476988 | -327698 | 1.87 | 33.3 | 1.61 | -81326 | 287657 | -89574 |
| ES entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | H1 | -0.69 | -0.90 | -126814 | -107743 | 248454 | -138722 | -0.58 | 46.4 | 2.81 | -74871 | 141745 | -77106 |
| ES entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | H2 | 1.89 | 3.60 | -78285 | -60214 | 175023 | -88821 | 2.31 | 30.6 | 2.69 | -83889 | 215695 | -85790 |
| ES entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | all | 0.85 | 1.34 | -120045 | -87391 | 476988 | -327698 | 2.42 | 35.1 | 2.02 | -81625 | 287657 | -89574 |
| NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | clean | 1.33 | 2.34 | -114820 | -90919 | 299800 | -195300 | 4.01 | 41.0 | 1.69 | -83888 | 259402 | -90910 |
| NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H1 | 0.78 | 1.44 | -117976 | -99570 | 242525 | -123923 | 0.91 | 50.0 | 3.23 | -67139 | 134123 | -71370 |
| NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H2 | 2.31 | 5.51 | -80833 | -72887 | 383592 | -88332 | 2.33 | 41.7 | 2.93 | -92538 | 228505 | -94729 |
| NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | all | 1.47 | 2.80 | -112578 | -90725 | 536585 | -195300 | 4.32 | 42.9 | 2.19 | -85143 | 259402 | -94729 |
| RTY entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | clean | 0.80 | 1.40 | -90079 | -82589 | 575296 | -99963 | 1.26 | 49.5 | 1.56 | -85894 | 276197 | -91389 |
| RTY entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H1 | -0.65 | -0.94 | -117898 | -99419 | 246423 | -127872 | -0.59 | 53.6 | 2.75 | -77445 | 140992 | -85238 |
| RTY entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H2 | 0.57 | 0.85 | -160254 | -122315 | 318428 | -231659 | 0.70 | 36.1 | 2.51 | -98771 | 227605 | -100120 |
| RTY entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | all | 0.53 | 0.85 | -113980 | -96809 | 575296 | -231659 | 1.40 | 47.6 | 1.95 | -88683 | 276197 | -100120 |
| YM entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | clean | 0.16 | 0.22 | -155997 | -112094 | 610471 | -312226 | 0.24 | 48.6 | 1.44 | -84438 | 315198 | -87882 |
| YM entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H1 | 0.50 | 0.75 | -102749 | -95190 | 205656 | -122108 | 0.49 | 42.9 | 2.96 | -83200 | 142599 | -84889 |
| YM entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | H2 | 1.42 | 2.27 | -83948 | -79458 | 164825 | -86287 | 1.98 | 33.3 | 2.63 | -81531 | 215278 | -88759 |
| YM entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | all | 0.43 | 0.60 | -137204 | -105113 | 610471 | -312226 | 0.94 | 44.6 | 1.93 | -84643 | 315198 | -88759 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | -17.4 | 14.6 | 23.5 | 26.0 | 13.9 / 23.5 | 23.3 / 27.1 | NO |
| NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | -4.7 | 7.8 | 15.4 | 35.1 | 8.7 / 17.5 | 43.3 / 47.4 | NO |
| RTY entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | -21.2 | -2.0 | 10.5 | 29.9 | 8.0 / 14.7 | 15.3 / 29.4 | NO |
| YM entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | -23.7 | 15.0 | 18.9 | 11.2 | 14.3 / 18.9 | 17.4 / 19.2 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 672 | -13.9 | -43.2 | -29.0 | 29.4 | -0.26 / -0.81 / -0.55 | 105.2 / 75.8 |
| ES 2 entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 682 | -19.3 | -48.6 | -34.5 | 29.4 | -0.39 / -0.99 / -0.70 | 88.8 / 59.4 |
| ES 3 entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1227 | -13.4 | -42.7 | -28.5 | 29.4 | -0.39 / -1.25 / -0.83 | 61.5 / 32.1 |
| ES 4 entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 667 | -27.7 | -57.1 | -42.9 | 29.4 | -0.46 / -0.94 / -0.71 | 63.0 / 33.6 |
| ES 5 entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1216 | -23.3 | -52.7 | -38.5 | 29.4 | -0.70 / -1.58 / -1.15 | 43.4 / 14.0 |
| ES 6 (diag) entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | gross-positive, cost-negative pre-2023 | 337 | 13.5 | -15.8 | -1.4 | 29.4 | 0.19 / -0.23 / -0.02 | 62.7 / 33.3 |
| ES 7 (diag) entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | gross-positive, cost-negative pre-2023 | 343 | 0.6 | -28.7 | -14.4 | 29.4 | 0.01 / -0.46 / -0.23 | 55.9 / 26.5 |
| ES 8 (diag) entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1217 | -19.8 | -49.2 | -34.9 | 29.4 | -0.49 / -1.21 / -0.86 | 38.3 / 9.0 |
| NQ 1 entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 688 | -38.9 | -53.3 | -44.8 | 14.4 | -0.57 / -0.78 / -0.65 | 187.1 / 172.7 |
| NQ 2 entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1258 | -39.2 | -53.6 | -45.1 | 14.4 | -0.81 / -1.11 / -0.94 | 129.1 / 114.8 |
| NQ 3 entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1253 | -65.5 | -79.8 | -71.3 | 14.4 | -1.22 / -1.48 / -1.33 | 124.9 / 110.6 |
| NQ 4 entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 684 | -80.0 | -94.4 | -85.8 | 14.4 | -1.05 / -1.24 / -1.13 | 156.7 / 142.3 |
| NQ 5 entry 15:40 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 706 | -42.8 | -57.2 | -48.7 | 14.4 | -0.64 / -0.86 / -0.73 | 154.0 / 139.6 |
| NQ 6 entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1262 | -46.8 | -61.1 | -52.6 | 14.4 | -1.06 / -1.38 / -1.19 | 93.8 / 79.4 |
| NQ 7 (diag) entry 15:20 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | negative pre-2023 | 358 | -47.9 | -62.3 | -53.6 | 14.4 | -0.45 / -0.58 / -0.50 | 144.0 / 129.6 |
| NQ 8 (diag) entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | negative pre-2023 | 349 | -5.0 | -19.4 | -10.7 | 14.4 | -0.06 / -0.22 / -0.12 | 132.1 / 117.8 |
| NQ 9 (diag) entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | negative pre-2023 | 358 | -24.2 | -38.6 | -29.8 | 14.4 | -0.30 / -0.48 / -0.37 | 117.4 / 103.0 |
| RTY 1 entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 741 | -13.9 | -28.3 | -26.0 | 14.4 | -0.56 / -1.14 / -1.05 | 31.1 / 16.7 |
| RTY 2 entry 15:20 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 364 | -14.1 | -28.5 | -26.2 | 14.4 | -0.30 / -0.60 / -0.55 | 40.2 / 25.8 |
| RTY 3 entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 734 | -19.0 | -33.4 | -31.1 | 14.4 | -0.61 / -1.07 / -1.00 | 23.3 / 9.0 |
| RTY 4 (diag) entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | positive pre-2023 | 166 | 20.3 | 5.9 | 8.4 | 14.4 | 0.38 / 0.11 / 0.16 | 57.7 / 43.3 |
| RTY 5 (diag) entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | positive pre-2023 | 159 | 21.3 | 6.9 | 9.2 | 14.4 | 0.32 / 0.11 / 0.14 | 35.4 / 21.0 |
| RTY 6 (diag) entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | gross-positive, cost-negative pre-2023 | 368 | 5.1 | -9.2 | -7.0 | 14.4 | 0.13 / -0.23 / -0.17 | 19.9 / 5.6 |
| YM 1 entry 15:30 |px-prior RTH close|>=0.7ADR dir=against exit 15:55 | negative pre-2023 | 661 | -2.1 | -16.5 | -10.6 | 14.4 | -0.05 / -0.37 / -0.24 | 56.6 / 42.3 |
| YM 2 entry 15:40 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1223 | -9.4 | -23.7 | -17.9 | 14.4 | -0.37 / -0.93 / -0.70 | 18.8 / 4.5 |
| YM 3 (diag) entry 15:40 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | negative pre-2023 | 334 | -5.5 | -19.9 | -13.9 | 14.4 | -0.11 / -0.38 / -0.27 | 44.0 / 29.7 |
| YM 4 (diag) entry 15:30 |px-prior RTH close|>=0.4ADR dir=against exit 15:55 | negative pre-2023 | 1248 | -0.2 | -14.5 | -8.7 | 14.4 | -0.01 / -0.53 / -0.32 | 27.0 / 12.6 |
| YM 5 (diag) entry 15:30 |px-prior RTH close|>=1.0ADR dir=against exit 15:55 | negative pre-2023 | 339 | -6.1 | -20.5 | -14.5 | 14.4 | -0.09 / -0.31 / -0.22 | 42.3 / 27.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 5 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.00, p(top) = 0.23); NQ: 6 cells pass the clean rule against a replicate mean of 2.2 (p(count) = 0.01, p(top) = 0.03); RTY: 3 cells pass the clean rule against a replicate mean of 1.0 (p(count) = 0.07, p(top) = 0.32); YM: 2 cells pass the clean rule against a replicate mean of 1.4 (p(count) = 0.38, p(top) = 0.57).
- Of 16 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.29 (NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 4; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 4 (cell-share pairs).
- Gate-3 cell NQ entry 15:20 |px-prior RTH close|>=0.4ADR dir=against exit 15:55: uplift +0.23/+0.40/+0.45, boot lo +0.10, plateau 1.00, 2x-slip +0.27, wd corr -0.20, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 16}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_1.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm1/ (`BM1_CO_all_selected_scored.csv`).

## LEAD detail (worker BK, after the pipeline run) - strongest result of batches BI/BJ/BM, NQ only
- Cell: NQ, 15:20 ET, if |price - prior RTH close| >= 0.4 x ADR20 trade AGAINST the day's move (short after a rise, long after a fall), time exit 15:55 (35 min). 243 clean / 404 pair-window trades (not small-sample). DIRECTION: the pre-registered sign (LETF rebalancing, WITH the move) is the OPPOSITE of the selected cell (reversal into the close); both directions were in the grid, selection was clean-only, but the registered prior was wrong in sign, so this is a post-hoc reading until confirmed on new weeks. It is the same late-day reversal direction as BJ2 (NQ 15:00 fade of the prior-60-min return); the two daily series correlate only 0.05 (weekly 0.04), 465 of BM1's trades fall on days BJ2 also trades.
- Standalone weekly Sharpe clean 1.33 / H1 0.78 / H2 2.31 / all-in 1.47 (drift- and clock-matched null p95 0.87, rank 1.00; OOS H1+H2 1.67 vs p95 1.29, rank 0.97). False-selection test: 6 NQ cells pass the clean rule against a replicate mean of 2.23 (p(count) 0.005, p(top) 0.025). Additive uplift at 10/20/30/50%: clean +0.12/+0.23/+0.32/+0.44, H1 +0.22/+0.40/+0.52/+0.56, H2 +0.25/+0.45/+0.61/+0.80 (gate_add PASS at all four shares); worst week of the combination +7.4/+14.8/+22.2% worse than the pair at 10/20/30% share (within the share); bootstrap 90% lower bound +0.06/+0.10/+0.11 (10/20/30%); plateau 1.0 (2 of 2 neighbours); 2x slippage uplift +0.21/+0.37/+0.43 (clean/H1/H2); worst-decile correlation with the pair -0.20.
- FAILED / open: ERA FLAG negative pre-2023 (2013-22 Sharpe -1.48, gross -$65 per trade): a modern-era effect (this is consistent with BJ2 and with 0DTE/retail-flow era structure; Gate Amendment 2 does not gate on it); replication leg: H0 2023-02..07 uplift +0.06 (sign holds, below 50% of the clean +0.23), alternating months odd +0.60 / even +0.00 (even half fails), ES +0.07 all-in (best ES cell fails H1/H2), RTY +0.05, YM +0.03 do NOT replicate: NQ-specific. Replications that hold: none cleanly (H0 sign only). LEAD (strong), not FOUND-PENDING.
- Insurance metrics of pair + 20% sleeve (weekly USD): clean Sharpe 1.7 (pair 1.46), Sortino 3.3, MAR 6.1, CVaR5 -83.9k, CVaR10 -79.7k, maxDD 259k, worst week -90.9k, %neg 40.0; H1 Sharpe 3.2, CVaR5 -67.1k, CVaR10 -57.7k, maxDD 134k, worst week -71.4k, %neg 32.1; H2 Sharpe 2.9, CVaR5 -92.5k, CVaR10 -84.8k, maxDD 229k, worst week -94.7k, %neg 38.9; all-in Sharpe 2.2, Sortino 4.4, MAR 12.4, CVaR5 -85.1k, CVaR10 -80.0k, maxDD 259k (pair 280k), worst week -94.7k (pair -82.9k), %neg 38.7. Sharpe, MAR, H1 CVaR improve; the worst week deepens by 14%, so it is a Sharpe sleeve, not insurance.
- Sized dollars: sleeve scale 44.8 NQ contracts = the pair's clean weekly sigma; 20% share = 9.0 NQ contracts, 10% = 4.5, 30% = 13.4. Worst single 1-contract trade -$5,769 (35-minute hold, no stop) so about -$52k at 9 contracts. About 400 trades in 3.3 years (about 120/yr).
- Executability: NT8 time-based strategy on NQ (or MNQ): at 15:20 ET compute (price - prior 16:00 close)/ADR20 (20-day mean daily range, prior days only); if >= 0.4 enter against at the next bar open, flat at 15:55; margin = intraday NQ margin x 9 contracts at the 20% share; its own account (it trades the pair's instrument inside the pair's RTH window, so it would net against ST/HM).
- Causality: all inputs are bars closed before the entry minute and prior-day ADR; the cell is the clean-selected maximum of 18 on NQ (selection p(top) 0.025).

DONE BM1
