# REPORT BM13 - BM1 reference test, small thresholds for VWAP references (BL3 amendment 1)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 1.** 10 selected cells (+11 diagnostic) scored on 4 instruments; best non-diagnostic all-in additive uplift at 20% share +0.39; best pair-window standalone Sharpe +1.88.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH BM', before the first run)
- Rule: see PREREG_AUTOPILOT.md BL3. Entry 15:20 against, six reference prices.
- Instruments: ES, NQ, RTY, YM. Grid: see PREREG
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |       6 |          3 |         3 |               0.88  |                2 |          3 |            3 |
| NQ    |       6 |          3 |         3 |               1.932 |                2 |          3 |            2 |
| RTY   |       6 |          3 |         1 |               0.889 |                2 |          1 |            3 |
| YM    |       6 |          3 |         3 |               1.019 |                2 |          3 |            3 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ES    |     200 |                    3 |            0.29  |               2 |      0     |                       0.655 |            0.626 |           1.11  |    0.13  |       0.88  |                1.286 |
| NQ    |     200 |                    3 |            0.56  |               3 |      0.005 |                       1.751 |            0.652 |           1.387 |    0.01  |       1.932 |                1.549 |
| RTY   |     200 |                    1 |            0.285 |               2 |      0.27  |                       0.482 |            0.673 |           1.492 |    0.165 |       0.482 |                1.492 |
| YM    |     200 |                    3 |            0.405 |               2 |      0     |                       0.816 |            0.616 |           1.2   |    0.095 |       1.019 |                1.356 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES 1 | ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 268 | 2 | 0.88 | -1.19 | 0.61 | 0.32 / 0.92 | 0.14 / 0.04 / -0.02 | -0.01 | -0.10 | 0.97 | -0.09 | 1.00 | 428 | NO |
| ES 2 | ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 173 | 2 | 0.61 | -1.12 | 0.20 | -0.31 / 1.02 | 0.11 / -0.15 / -0.03 | -0.04 | -0.07 | 0.86 | -0.14 | 1.00 | 264 | NO |
| ES 3 | ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 344 | 2 | 0.48 | -1.43 | 0.48 | 0.58 / 1.17 | 0.05 / 0.08 / 0.07 | -0.06 | -0.15 | 0.95 | -0.12 | 0.50 | 539 | NO |
| ES 4 (diag) | ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 48 | 1 | -0.05 | -0.91 | -0.39 | -0.68 / 1.15 | -0.01 / 0.07 / -0.45 | -0.12 | -0.10 | 0.47 | -0.30 | 0.00 | 75 S | diag |
| ES 5 (diag) | ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 25 | 1 | -0.74 | -0.39 | -0.67 | -0.63 / 1.09 | -0.13 / -0.10 / -0.58 | -0.23 | 0.72 | 0.20 | -0.46 | 0.00 | 37 S | diag |
| ES 6 (diag) | ref=vwap30 |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 5 | 0 | -1.02 | -0.02 | -0.57 | -0.12 /  | -0.17 / 0.00 / -0.20 | -0.14 | 0.54 | 0.23 | -0.38 | 0.00 | 8 S | diag |
| NQ 1 | ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 169 | 2 | 1.93 | -1.00 | 1.88 | 1.91 / 1.65 | 0.36 / 0.28 / 0.56 | 0.37 | -0.42 | 1.00 | 0.20 | 0.50 | 258 | LEAD(gate3-7 fail: plateau ) |
| NQ 2 | ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 267 | 2 | 1.73 | -1.22 | 1.65 | 1.73 / 1.21 | 0.33 / 0.20 / 0.52 | 0.34 | 0.17 | 1.00 | 0.14 | 1.00 | 421 | LEAD |
| NQ 3 | ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 336 | 2 | 1.59 | -1.41 | 1.41 | 1.33 / 1.39 | 0.29 / 0.08 / 0.43 | 0.27 | 0.26 | 0.99 | 0.06 | 1.00 | 534 | NO |
| NQ 4 (diag) | ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 43 | 1 | 0.03 | -0.60 | -0.32 | -0.68 / 1.29 | 0.03 / -0.04 / -0.59 | -0.12 | 0.08 | 0.35 | -0.36 | 0.00 | 69 S | diag |
| NQ 5 (diag) | ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 18 | 1 | -0.73 | -0.67 | -0.47 | -0.32 / 1.49 | -0.13 / -0.08 / -0.50 | -0.20 | 0.36 | 0.22 | -0.49 | 0.00 | 28 S | diag |
| RTY 1 | ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 151 | 2 | 0.48 | -0.60 | 0.37 | 0.14 / 1.01 | 0.05 / -0.29 / 0.08 | -0.04 | -0.07 | 0.94 | -0.17 | 1.00 | 248 | NO |
| RTY 2 (diag) | ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 259 | 1 | 0.89 | -1.20 | 0.86 | 0.86 / 0.99 | 0.13 / -0.13 / 0.23 | 0.03 | -0.07 | 1.00 | -0.07 | 0.50 | 426 | diag |
| RTY 3 (diag) | ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 324 | 1 | 0.85 | -1.11 | 0.41 | -0.16 / 1.00 | 0.12 / -0.36 / -0.01 | -0.07 | 0.02 | 0.96 | -0.17 | 0.50 | 526 | diag |
| RTY 4 (diag) | ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 34 | 1 | 0.01 | -0.55 | 0.08 | 0.11 / 1.19 | 0.03 / 0.10 / -0.20 | -0.02 | 0.53 | 0.70 | -0.17 | 0.00 | 54 S | diag |
| YM 1 | ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 282 | 2 | 1.02 | -0.89 | 0.19 | -1.14 / 1.07 | 0.15 / -0.14 / -0.34 | -0.07 | -0.26 | 0.85 | -0.19 | 0.00 | 434 | NO |
| YM 2 | ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 185 | 2 | 0.72 | -0.87 | -0.01 | -1.05 / 1.32 | 0.11 / -0.21 / -0.26 | -0.07 | -0.14 | 0.68 | -0.21 | 0.00 | 281 | NO |
| YM 3 | ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 343 | 2 | 0.71 | -0.99 | -0.01 | -1.33 / 1.23 | 0.11 / -0.23 / -0.28 | -0.10 | -0.30 | 0.81 | -0.20 | 0.00 | 546 | NO |
| YM 4 (diag) | ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | 50 | 1 | -0.71 | -1.01 | -0.93 | -1.33 / 1.39 | -0.10 / -0.23 / -0.58 | -0.24 | 0.60 | 0.10 | -0.43 | 0.00 | 70 S | diag |
| YM 5 (diag) | ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | 19 | 1 | -0.81 | -0.44 | -1.05 | -1.35 / 1.58 | -0.13 / -0.08 / -0.91 | -0.31 | 0.67 | 0.03 | -0.53 | 0.00 | 26 S | diag |
| YM 6 (diag) | ref=vwap30 |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 4 | 0 | -0.91 | -0.07 | -0.40 | 0.90 /  | -0.13 / 0.00 / 0.06 | -0.06 | 0.54 | 0.38 | -0.16 | 0.00 | 5 S | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 11 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 2 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 9 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 3 |
| standalone pair-window Sharpe above own random-entry null p95 | 7 |
| worst-decile corr <= +0.30 | 14 |
| plateau >= 0.75 | 5 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 9 |
| gate_add PASS at any share (non-diag) | 4 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | clean | 0.80 | 1.42 | -105954 | -88648 | 612659 | -137331 | 1.19 | 44.8 | 1.60 | -85922 | 240955 | -91400 |
| ES ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | H1 | 0.16 | 0.28 | -90788 | -78366 | 253909 | -112285 | 0.14 | 50.0 | 2.87 | -74368 | 154601 | -75578 |
| ES ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | H2 | 0.41 | 0.59 | -175968 | -140022 | 483635 | -201013 | 0.34 | 44.4 | 2.47 | -104316 | 212489 | -112709 |
| ES ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | all | 0.61 | 0.99 | -126365 | -103877 | 612659 | -201013 | 1.52 | 45.8 | 1.99 | -89206 | 240955 | -112709 |
| NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | clean | 1.86 | 3.70 | -109817 | -82266 | 375399 | -185162 | 4.51 | 31.4 | 1.81 | -81790 | 245096 | -87880 |
| NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | H1 | 0.55 | 1.00 | -127316 | -107629 | 205180 | -149910 | 0.75 | 32.1 | 3.11 | -74176 | 160123 | -78287 |
| NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | H2 | 2.89 | 7.47 | -113870 | -80076 | 282528 | -157023 | 4.08 | 25.0 | 3.04 | -82447 | 212064 | -85241 |
| NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | all | 1.88 | 3.91 | -120038 | -88822 | 375399 | -185162 | 7.99 | 30.4 | 2.28 | -81633 | 245096 | -87880 |
| RTY ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | clean | 0.51 | 0.85 | -120543 | -97537 | 642470 | -166459 | 0.71 | 36.2 | 1.51 | -87627 | 288203 | -105618 |
| RTY ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | H1 | -1.58 | -1.98 | -112610 | -93936 | 317298 | -129266 | -0.99 | 50.0 | 2.54 | -74704 | 152413 | -79468 |
| RTY ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | H2 | 1.16 | 1.76 | -173981 | -113959 | 189171 | -189171 | 2.07 | 33.3 | 2.56 | -97068 | 223878 | -114283 |
| RTY ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | all | 0.37 | 0.58 | -134397 | -103988 | 642470 | -189171 | 0.83 | 38.1 | 1.91 | -88839 | 288203 | -114283 |
| YM ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | clean | 0.95 | 1.67 | -102057 | -90429 | 596664 | -154953 | 1.46 | 46.7 | 1.61 | -85998 | 238914 | -91765 |
| YM ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | H1 | -1.37 | -1.73 | -77369 | -70648 | 277019 | -94043 | -0.75 | 50.0 | 2.69 | -74162 | 154771 | -74993 |
| YM ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | H2 | -1.10 | -1.29 | -189630 | -149479 | 577138 | -243213 | -0.68 | 50.0 | 2.14 | -97054 | 223202 | -109734 |
| YM ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | all | 0.19 | 0.28 | -125914 | -105295 | 892076 | -243213 | 0.31 | 48.2 | 1.89 | -88628 | 238914 | -109734 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ES ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | -19.8 | -24.9 | 9.5 | 25.5 | 8.0 / 14.1 | 33.8 / 36.3 | NO |
| NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | 2.8 | 11.4 | 21.4 | 23.3 | 10.7 / 18.1 | 30.0 / 36.6 | INSURANCE |
| RTY ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | -24.1 | -27.7 | 6.8 | -0.7 | -18.2 / 6.1 | 26.4 / 26.0 | NO |
| YM ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | -27.0 | -19.5 | 9.8 | 33.8 | 6.2 / 13.9 | 36.3 / 36.7 | NO |

INSURANCE count: 1.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ES 1 ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1373 | -22.1 | -51.4 | -37.3 | 29.4 | -0.51 / -1.19 / -0.86 | 66.1 / 36.8 |
| ES 2 ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 805 | -32.9 | -62.2 | -48.0 | 29.4 | -0.59 / -1.12 / -0.86 | 62.9 / 33.6 |
| ES 3 ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1722 | -21.8 | -51.2 | -37.0 | 29.4 | -0.61 / -1.43 / -1.04 | 46.6 / 17.3 |
| ES 4 (diag) ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 331 | -68.1 | -97.4 | -83.1 | 29.4 | -0.64 / -0.91 / -0.78 | -7.0 / -36.4 |
| ES 5 (diag) ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 124 | -29.7 | -59.1 | -44.4 | 29.4 | -0.20 / -0.39 / -0.30 | -144.5 / -173.9 |
| ES 6 (diag) ref=vwap30 |dist|>=0.25ADR against, entry 15:20 exit 15:55 | gross-positive, cost-negative pre-2023 | 28 | 19.2 | -10.2 | 3.4 | 29.4 | 0.05 / -0.02 / 0.01 | -917.5 / -946.9 |
| NQ 1 ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 834 | -53.6 | -67.9 | -59.5 | 14.4 | -0.79 / -1.00 / -0.87 | 220.5 / 206.1 |
| NQ 2 ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1390 | -55.6 | -69.9 | -61.5 | 14.4 | -0.97 / -1.22 / -1.08 | 141.3 / 127.0 |
| NQ 3 ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1760 | -51.1 | -65.4 | -56.9 | 14.4 | -1.10 / -1.41 / -1.23 | 118.1 / 103.7 |
| NQ 4 (diag) ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 317 | -73.2 | -87.5 | -78.9 | 14.4 | -0.50 / -0.60 / -0.54 | 23.4 / 9.0 |
| NQ 5 (diag) ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 112 | -154.4 | -168.7 | -159.8 | 14.4 | -0.62 / -0.67 / -0.64 | -348.1 / -362.4 |
| RTY 1 ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 465 | -7.8 | -22.1 | -19.9 | 14.4 | -0.21 / -0.60 / -0.54 | 34.4 / 20.0 |
| RTY 2 (diag) ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 827 | -17.8 | -32.2 | -29.9 | 14.4 | -0.67 / -1.20 / -1.12 | 36.7 / 22.4 |
| RTY 3 (diag) ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1027 | -12.7 | -27.1 | -24.8 | 14.4 | -0.52 / -1.11 / -1.02 | 32.2 / 17.8 |
| RTY 4 (diag) ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 150 | -34.4 | -48.8 | -46.5 | 14.4 | -0.39 / -0.55 / -0.52 | 20.6 / 6.2 |
| YM 1 ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1301 | -17.5 | -31.8 | -26.1 | 14.4 | -0.49 / -0.89 / -0.73 | 42.0 / 27.6 |
| YM 2 ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 763 | -25.6 | -39.9 | -34.2 | 14.4 | -0.56 / -0.87 / -0.74 | 38.1 / 23.7 |
| YM 3 ref=sess_vwap |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 1700 | -15.3 | -29.6 | -23.9 | 14.4 | -0.51 / -0.99 / -0.80 | 32.3 / 18.0 |
| YM 4 (diag) ref=vwap30 |dist|>=0.1ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 296 | -73.6 | -87.9 | -82.0 | 14.4 | -0.85 / -1.01 / -0.94 | -47.0 / -61.4 |
| YM 5 (diag) ref=vwap30 |dist|>=0.15ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 103 | -45.3 | -59.7 | -53.7 | 14.4 | -0.34 / -0.44 / -0.40 | -131.6 / -145.9 |
| YM 6 (diag) ref=vwap30 |dist|>=0.25ADR against, entry 15:20 exit 15:55 | negative pre-2023 | 22 | -13.2 | -27.5 | -22.0 | 14.4 | -0.03 / -0.07 / -0.05 | -542.5 / -556.9 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 3 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.00, p(top) = 0.13); NQ: 3 cells pass the clean rule against a replicate mean of 0.6 (p(count) = 0.01, p(top) = 0.01); RTY: 1 cells pass the clean rule against a replicate mean of 0.3 (p(count) = 0.27, p(top) = 0.17); YM: 3 cells pass the clean rule against a replicate mean of 0.4 (p(count) = 0.00, p(top) = 0.10).
- Of 10 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.39 (NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55); bootstrap lower bound > 0 for 3 cells; plateau >= 0.75 for 5; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 4 (cell-share pairs).
- Gate-3 cell NQ ref=sess_vwap |dist|>=0.25ADR against, entry 15:20 exit 15:55: uplift +0.36/+0.28/+0.56, boot lo +0.20, plateau 0.50, 2x-slip +0.37, wd corr -0.42, ERA negative pre-2023 (replication not run unless stated below).
- Gate-3 cell NQ ref=sess_vwap |dist|>=0.15ADR against, entry 15:20 exit 15:55: uplift +0.33/+0.20/+0.52, boot lo +0.14, plateau 1.00, 2x-slip +0.34, wd corr +0.17, ERA negative pre-2023 (replication not run unless stated below).
- ERA flags: {'negative pre-2023': 10}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_bm_13.py, ap_bm_pipe.py (= ap_b_pipe2 with module swap), ap_bm_job.sh, ap_sw_common.py, ap_bm_report2.py in code/census/night_ins/; data in outputs/autopilot/b/bm13/ (`BM13_CO_all_selected_scored.csv`).

DONE BM13
