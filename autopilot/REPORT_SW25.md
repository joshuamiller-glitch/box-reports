# REPORT SW25 - real aggressor-flow imbalance persistence on NQ and ES (D01/D02 H2/H3)

**Verdict: NO. FOUND 0, LEAD 0, INSURANCE 0.** 15 selected cells (+3 diagnostic) scored on 2 instruments; best non-diagnostic all-in additive uplift at 20% share +0.25; best pair-window standalone Sharpe +0.92.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Per-minute aggressor buy/sell volume (trade files on disk, 2023-02..2026-10, front contract). I_W = sum(vb - vs)/sum(vb + vs) over W (15/30/60) min at 5-min bar ends; crossings of +-theta (0.03/0.06/0.10), optional persistence (previous W window same sign); with/against; hold 30/60/120 min. No pre-2023 flow exists, so the ERA flag is not applicable and selection has the clean span only.
- Instruments: NQ, ES. Grid: 216 cells per instrument.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ES    |     216 |        210 |         5 |                0.48 |                2 |          5 |            3 |
| NQ    |     216 |        202 |        15 |                1.38 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     100 |                   15 |            27.34 |              43 |       1    |                       0.769 |            1.081 |           1.304 |     1    |        1.38 |                2.093 |
| ES    |     100 |                    5 |             4.37 |               9 |       0.46 |                       0.437 |            0.581 |           0.817 |     0.81 |        0.48 |                1.514 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | aggressor imbalance W=30m theta=0.06 persist=1 dir=with hold=120m all | 2276 | 2 | 1.38 | 0.10 | 0.81 | 0.09 / 1.01 | 0.13 / 0.23 / -0.13 | -0.00 | -0.20 | 0.99 | -0.14 | 0.00 | 3585 | NO |
| NQ 2 | aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | 329 | 2 | 1.09 | 0.73 | 0.87 | 0.60 / 1.46 | 0.16 / -0.08 / 0.03 | 0.09 | 0.01 | 0.98 | -0.09 | 0.17 | 518 | NO |
| NQ 3 | aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | 597 | 2 | 1.04 | 0.13 | 0.92 | 0.90 / 1.49 | 0.28 / -0.57 / 0.60 | 0.23 | 0.22 | 0.99 | 0.01 | 0.17 | 951 | NO |
| NQ 4 | aggressor imbalance W=15m theta=0.1 persist=0 dir=with hold=120m day | 546 | 2 | 0.99 | 0.29 | 0.89 | 0.76 / 1.13 | 0.13 / 0.13 / 0.09 | 0.10 | 0.12 | 0.99 | -0.08 | 0.17 | 872 | NO |
| NQ 5 | aggressor imbalance W=60m theta=0.03 persist=0 dir=against hold=120m day | 1047 | 2 | 0.79 | -0.11 | 0.52 | 0.26 / 1.17 | 0.19 / -0.79 / 0.44 | 0.09 | 0.24 | 0.90 | -0.08 | 0.33 | 1636 | NO |
| NQ 6 | aggressor imbalance W=60m theta=0.06 persist=1 dir=against hold=120m day | 177 | 2 | 0.79 | -0.65 | 0.90 | 1.20 / 1.31 | 0.14 / -0.01 / 0.18 | 0.13 | 0.12 | 0.95 | -0.05 | 0.67 | 261 | NO |
| NQ 7 | aggressor imbalance W=15m theta=0.03 persist=0 dir=against hold=120m day | 1634 | 2 | 0.56 | -0.39 | 0.12 | -0.21 / 1.08 | 0.08 / 0.12 / -0.21 | -0.01 | 0.09 | 0.74 | -0.22 | 0.33 | 2614 | NO |
| NQ 8 | aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=60m day | 728 | 2 | 0.37 | 0.10 | 0.28 | 0.26 / 1.28 | 0.09 / -0.52 / 0.35 | 0.04 | 0.47 | 0.83 | -0.14 | 0.33 | 1167 | NO |
| NQ 9 | aggressor imbalance W=60m theta=0.06 persist=0 dir=against hold=120m day | 329 | 2 | 0.36 | -0.64 | 0.60 | 1.05 / 1.22 | 0.08 / 0.20 / 0.12 | 0.10 | 0.02 | 0.96 | -0.08 | 0.83 | 496 | NO |
| NQ 10 | aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m all | 2038 | 2 | 0.32 | -0.03 | 0.33 | 0.41 / 1.69 | 0.12 / -0.87 / 0.61 | 0.05 | 0.20 | 0.85 | -0.13 | 0.17 | 3318 | NO |
| ES 1 | aggressor imbalance W=30m theta=0.06 persist=1 dir=with hold=120m day | 596 | 2 | 0.48 | -0.10 | 0.35 | 0.19 / 0.88 | 0.03 / -0.31 / 0.07 | -0.08 | 0.29 | 0.95 | -0.18 | 0.00 | 891 | NO |
| ES 2 | aggressor imbalance W=60m theta=0.1 persist=0 dir=with hold=60m day | 143 | 2 | 0.47 | -0.53 | 0.42 | 0.34 / 0.72 | 0.07 / -0.31 / 0.02 | -0.06 | 0.22 | 0.98 | -0.17 | 0.50 | 194 | NO |
| ES 3 | aggressor imbalance W=15m theta=0.1 persist=0 dir=with hold=120m day | 790 | 2 | 0.44 | -0.13 | -0.12 | -0.96 / 0.90 | 0.01 / -0.62 / 0.01 | -0.18 | -0.08 | 0.79 | -0.27 | 0.00 | 1174 | NO |
| ES 4 | aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | 529 | 2 | 0.40 | -0.25 | 0.27 | 0.01 / 0.80 | 0.06 / -0.26 / 0.07 | -0.05 | -0.16 | 0.93 | -0.17 | 0.00 | 777 | NO |
| ES 5 | aggressor imbalance W=30m theta=0.03 persist=0 dir=against hold=120m day | 1488 | 2 | 0.39 | -0.43 | -0.02 | -0.89 / 0.79 | 0.03 / -0.31 / -0.27 | -0.19 | 0.45 | 0.92 | -0.24 | 0.00 | 2348 | NO |
| ES 6 (diag) | aggressor imbalance W=60m theta=0.1 persist=0 dir=with hold=30m day | 153 | 1 | 0.42 | -0.34 | 0.29 | 0.14 / 0.49 | 0.05 / -0.28 / -0.01 | -0.11 | 0.10 | 0.99 | -0.19 | 0.00 | 207 | diag |
| ES 7 (diag) | aggressor imbalance W=60m theta=0.06 persist=1 dir=against hold=30m day | 331 | 1 | 0.39 | 0.16 | 0.06 | -0.37 / 0.42 | 0.10 / -0.49 / 0.15 | -0.12 | -0.21 | 1.00 | -0.16 | 0.00 | 478 | diag |
| ES 8 (diag) | aggressor imbalance W=30m theta=0.06 persist=0 dir=with hold=120m day | 990 | 1 | 0.11 | -0.59 | -0.04 | -0.16 / 1.34 | -0.04 / -0.41 / 0.03 | -0.18 | 0.12 | 0.81 | -0.25 | 0.00 | 1455 | diag |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 15 |
| diagnostic cells read | 3 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 0 / 0 / 0 |
| all-in uplift @20% > 0 (all scored) | 13 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 1 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 16 |
| plateau >= 0.75 | 1 |
| all-in uplift at 2x slippage >= +0.10 | 3 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | clean | 0.41 | 0.59 | -136097 | -108498 | 717068 | -260480 | 0.52 | 45.7 | 1.52 | -84441 | 265167 | -92754 |
| ES aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | H1 | -0.42 | -0.57 | -136858 | -122460 | 537651 | -175897 | -0.20 | 46.4 | 2.57 | -100323 | 180099 | -112112 |
| ES aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | H2 | 0.40 | 0.63 | -90595 | -81375 | 225713 | -99787 | 0.50 | 44.4 | 2.55 | -70678 | 210987 | -70964 |
| ES aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | all | 0.27 | 0.38 | -133770 | -107139 | 717068 | -260480 | 0.53 | 45.8 | 1.92 | -87040 | 265167 | -112112 |
| NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | clean | 0.95 | 1.44 | -125455 | -98889 | 557071 | -272864 | 1.56 | 42.9 | 1.74 | -79440 | 236612 | -87063 |
| NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | H1 | -1.35 | -1.48 | -243735 | -211684 | 757946 | -298184 | -0.60 | 50.0 | 2.26 | -82700 | 233107 | -86021 |
| NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | H2 | 2.62 | 4.85 | -162492 | -127342 | 213354 | -184191 | 5.58 | 36.1 | 3.08 | -104028 | 219646 | -119363 |
| NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | all | 0.92 | 1.34 | -175662 | -133378 | 772397 | -298184 | 2.08 | 42.3 | 2.15 | -86100 | 268189 | -119363 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | -12.4 | -37.0 | 7.5 | -3.8 | 15.9 / 26.6 | -37.9 / -11.2 | NO |
| ES aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | -25.8 | -29.2 | 10.9 | 35.4 | 5.4 / 15.2 | -36.2 / -13.9 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 aggressor imbalance W=30m theta=0.06 persist=1 dir=with hold=120m all | positive pre-2023 | 563 | 23.3 | 8.9 | 13.1 | 14.4 | 0.27 / 0.10 / 0.15 | 56.1 / 41.8 |
| NQ 2 aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | positive pre-2023 | 80 | 337.2 | 322.9 | 326.9 | 14.4 | 0.76 / 0.73 / 0.74 | 165.9 / 151.6 |
| NQ 3 aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day | positive pre-2023 | 154 | 59.8 | 45.4 | 49.6 | 14.4 | 0.18 / 0.13 / 0.15 | 123.4 / 109.0 |
| NQ 4 aggressor imbalance W=15m theta=0.1 persist=0 dir=with hold=120m day | positive pre-2023 | 155 | 98.7 | 84.3 | 88.4 | 14.4 | 0.33 / 0.29 / 0.30 | 118.6 / 104.2 |
| NQ 5 aggressor imbalance W=60m theta=0.03 persist=0 dir=against hold=120m day | negative pre-2023 | 281 | -7.1 | -21.4 | -17.3 | 14.4 | -0.05 / -0.11 / -0.09 | 79.8 / 65.4 |
| NQ 6 aggressor imbalance W=60m theta=0.06 persist=1 dir=against hold=120m day | negative pre-2023 | 49 | -316.2 | -330.6 | -326.5 | 14.4 | -0.62 / -0.65 / -0.64 | 152.3 / 137.9 |
| NQ 7 aggressor imbalance W=15m theta=0.03 persist=0 dir=against hold=120m day | negative pre-2023 | 406 | -74.8 | -89.2 | -85.0 | 14.4 | -0.33 / -0.39 / -0.38 | 44.1 / 29.7 |
| NQ 8 aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=60m day | positive pre-2023 | 193 | 36.6 | 22.2 | 26.3 | 14.4 | 0.17 / 0.10 / 0.12 | 33.4 / 19.0 |
| NQ 9 aggressor imbalance W=60m theta=0.06 persist=0 dir=against hold=120m day | negative pre-2023 | 82 | -235.1 | -249.5 | -245.4 | 14.4 | -0.61 / -0.64 / -0.63 | 62.8 / 48.4 |
| NQ 10 aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m all | gross-positive, cost-negative pre-2023 | 499 | 8.5 | -5.9 | -1.7 | 14.4 | 0.07 / -0.03 / -0.00 | 24.9 / 10.5 |
| ES 1 aggressor imbalance W=30m theta=0.06 persist=1 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 158 | 9.3 | -20.0 | -13.2 | 29.4 | 0.05 / -0.10 / -0.07 | 54.7 / 25.3 |
| ES 2 aggressor imbalance W=60m theta=0.1 persist=0 dir=with hold=60m day | negative pre-2023 | 35 | -83.9 | -113.3 | -106.9 | 29.4 | -0.42 / -0.53 / -0.51 | 56.3 / 26.9 |
| ES 3 aggressor imbalance W=15m theta=0.1 persist=0 dir=with hold=120m day | gross-positive, cost-negative pre-2023 | 229 | 0.2 | -29.1 | -22.3 | 29.4 | 0.01 / -0.13 / -0.10 | 48.4 / 19.1 |
| ES 4 aggressor imbalance W=15m theta=0.1 persist=1 dir=with hold=120m day | negative pre-2023 | 136 | -36.1 | -65.5 | -58.8 | 29.4 | -0.13 / -0.25 / -0.22 | 53.5 / 24.1 |
| ES 5 aggressor imbalance W=30m theta=0.03 persist=0 dir=against hold=120m day | negative pre-2023 | 376 | -33.0 | -62.3 | -55.5 | 29.4 | -0.24 / -0.43 / -0.39 | 48.7 / 19.4 |
| ES 6 (diag) aggressor imbalance W=60m theta=0.1 persist=0 dir=with hold=30m day | negative pre-2023 | 37 | -28.0 | -57.4 | -51.1 | 29.4 | -0.19 / -0.34 / -0.31 | 44.2 / 14.8 |
| ES 7 (diag) aggressor imbalance W=60m theta=0.06 persist=1 dir=against hold=30m day | positive pre-2023 | 82 | 61.1 | 31.8 | 38.6 | 29.4 | 0.30 / 0.16 / 0.19 | 40.2 / 10.9 |
| ES 8 (diag) aggressor imbalance W=30m theta=0.06 persist=0 dir=with hold=120m day | negative pre-2023 | 271 | -59.8 | -89.1 | -82.3 | 29.4 | -0.40 / -0.59 / -0.55 | 31.0 / 1.6 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ES: 5 cells pass the clean rule against a replicate mean of 4.4 (p(count) = 0.46, p(top) = 0.81); NQ: 15 cells pass the clean rule against a replicate mean of 27.3 (p(count) = 1.00, p(top) = 1.00).
- Of 15 selected cells, 0 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.25 (NQ aggressor imbalance W=60m theta=0.03 persist=1 dir=against hold=120m day); bootstrap lower bound > 0 for 1 cells; plateau >= 0.75 for 1; 2x-slippage all-in uplift >= +0.10 for 3; gate_add PASS at some share: 0 (cell-share pairs).
- ERA flags: {'negative pre-2023': 7, 'positive pre-2023': 5, 'gross-positive, cost-negative pre-2023': 3}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_25.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw25/ (`SW25_CO_all_selected_scored.csv`).

DONE SW25
