# REPORT SW32 - the live pair's own recent daily P&L as the state of an NQ sleeve (D00 H5 M1-M3, NQ only)

**Verdict: LEAD. FOUND 0, LEAD 1, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.23; best pair-window standalone Sharpe +1.41.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'BATCH S (GAPMAP SWEEPER)', before the first run)
- Rule: sum of the pair's corrected-engine daily P&L over the prior N = 1/3/5 label days (rows from 2023-02-10): mode pm (long if >0, short if <0, with di), pos (long only if >0), neg (long only if <0); entry RTH open, hold 1/2/3 label days. MINTR 60 (history starts 2023-02).
- Instruments: NQ. Grid: 36 cells.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma (time-exit books have no stop: the worst single trade is in the CSV); multi-day holds carry overnight and weekend gap risk (no stop). No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| NQ    |      36 |         36 |        14 |               2.417 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| NQ    |     200 |                   14 |            5.705 |              13 |          0 |                       1.039 |            0.776 |           1.075 |    0.075 |       2.417 |                1.954 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ 1 | pair P&L prior 3d mode=pos dir=+1 hold=2d | 116 | 2 | 2.42 | 0.19 | 0.75 | -0.85 / 1.66 | 0.42 / -1.08 / -0.20 | 0.07 | -0.03 | 0.86 | -0.17 | 1.00 | 191 | NO |
| NQ 2 | pair P&L prior 1d mode=pm dir=+1 hold=2d | 169 | 2 | 1.16 | -0.30 | 0.29 | -0.72 / 1.61 | 0.14 / -0.01 / -0.54 | -0.04 | 0.60 | 0.69 | -0.24 | 0.00 | 271 | NO |
| NQ 3 | pair P&L prior 1d mode=pos dir=+1 hold=2d | 139 | 2 | 1.10 | 0.18 | 0.59 | -0.19 / 1.68 | 0.17 / -0.50 / 0.10 | 0.06 | 0.32 | 0.80 | -0.13 | 0.00 | 225 | NO |
| NQ 4 | pair P&L prior 1d mode=pos dir=+1 hold=1d | 182 | 2 | 1.05 | 0.22 | 0.29 | -0.80 / 1.42 | 0.16 / -0.32 / -0.21 | 0.00 | -0.45 | 0.76 | -0.17 | 0.00 | 302 | NO |
| NQ 5 | pair P&L prior 5d mode=pos dir=+1 hold=2d | 119 | 2 | 1.03 | 0.10 | 1.41 | 1.94 / 1.81 | 0.14 / -0.22 / 0.75 | 0.22 | -0.54 | 1.00 | 0.02 | 1.00 | 196 | NO |
| NQ 6 | pair P&L prior 1d mode=pos dir=+1 hold=3d | 106 | 2 | 1.02 | 0.57 | 0.62 | 0.03 / 1.56 | 0.19 / -0.27 / 0.04 | 0.09 | 0.33 | 0.84 | -0.12 | 0.00 | 173 | NO |
| NQ 7 | pair P&L prior 1d mode=pm dir=+1 hold=3d | 125 | 2 | 0.82 | 0.47 | 1.15 | 1.64 / 1.77 | 0.10 / 0.34 / 0.12 | 0.13 | 0.17 | 0.99 | -0.04 | 0.00 | 202 | LEAD |
| NQ 8 | pair P&L prior 5d mode=pm dir=+1 hold=3d | 129 | 2 | 0.71 | 0.21 | 0.28 | -0.31 / 1.52 | 0.14 / -0.14 / -0.01 | 0.06 | -0.63 | 0.57 | -0.13 | 0.75 | 207 | NO |
| NQ 9 | pair P&L prior 1d mode=neg dir=+1 hold=2d | 110 | 2 | 0.62 | 0.48 | 0.85 | 1.08 / 1.42 | 0.11 / 0.80 / 0.04 | 0.18 | -0.54 | 0.95 | -0.03 | 0.00 | 173 | NO |
| NQ 10 | pair P&L prior 1d mode=neg dir=+1 hold=1d | 143 | 2 | 0.45 | 0.20 | 1.24 | 2.54 / 1.46 | 0.04 / 0.86 / 0.29 | 0.21 | 0.25 | 1.00 | 0.01 | 0.00 | 224 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 1 / 1 / 1 |
| all-in uplift @20% > 0 (all scored) | 9 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 2 |
| standalone pair-window Sharpe above own random-entry null p95 | 4 |
| worst-decile corr <= +0.30 | 7 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 4 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ pair P&L prior 5d mode=pos dir=+1 hold=2d | clean | 1.02 | 1.46 | -151516 | -114461 | 397134 | -291999 | 2.34 | 32.4 | 1.60 | -81959 | 285838 | -88848 |
| NQ pair P&L prior 5d mode=pos dir=+1 hold=2d | H1 | -0.13 | -0.16 | -226637 | -187257 | 457098 | -300816 | -0.09 | 28.6 | 2.61 | -85411 | 205139 | -86547 |
| NQ pair P&L prior 5d mode=pos dir=+1 hold=2d | H2 | 4.06 | 12.42 | -74963 | -53272 | 115352 | -115352 | 11.68 | 27.8 | 3.24 | -80345 | 201903 | -83275 |
| NQ pair P&L prior 5d mode=pos dir=+1 hold=2d | all | 1.41 | 2.09 | -165427 | -123274 | 487821 | -300816 | 4.58 | 31.0 | 2.12 | -82872 | 285838 | -88848 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| NQ pair P&L prior 5d mode=pos dir=+1 hold=2d | -5.6 | -31.7 | 13.1 | 22.4 | 12.7 / 21.9 | -38.9 / -11.8 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| NQ 1 pair P&L prior 3d mode=pos dir=+1 hold=2d | positive pre-2023 | 26 | 388.7 | 374.3 | 378.4 | 14.4 | 0.20 / 0.19 / 0.19 | 2003.8 / 1989.4 |
| NQ 2 pair P&L prior 1d mode=pm dir=+1 hold=2d | negative pre-2023 | 37 | -660.9 | -675.3 | -671.2 | 14.4 | -0.29 / -0.30 / -0.30 | 728.0 / 713.6 |
| NQ 3 pair P&L prior 1d mode=pos dir=+1 hold=2d | positive pre-2023 | 28 | 497.9 | 483.5 | 487.5 | 14.4 | 0.18 / 0.18 / 0.18 | 920.1 / 905.7 |
| NQ 4 pair P&L prior 1d mode=pos dir=+1 hold=1d | positive pre-2023 | 39 | 258.2 | 243.8 | 247.9 | 14.4 | 0.23 / 0.22 / 0.22 | 671.6 / 657.3 |
| NQ 5 pair P&L prior 5d mode=pos dir=+1 hold=2d | positive pre-2023 | 26 | 310.6 | 296.2 | 300.3 | 14.4 | 0.11 / 0.10 / 0.10 | 926.4 / 912.0 |
| NQ 6 pair P&L prior 1d mode=pos dir=+1 hold=3d | positive pre-2023 | 23 | 1933.9 | 1919.6 | 1923.6 | 14.4 | 0.57 / 0.57 / 0.57 | 1175.6 / 1161.3 |
| NQ 7 pair P&L prior 1d mode=pm dir=+1 hold=3d | positive pre-2023 | 28 | 1083.2 | 1068.9 | 1073.0 | 14.4 | 0.47 / 0.47 / 0.47 | 1020.9 / 1006.6 |
| NQ 8 pair P&L prior 5d mode=pm dir=+1 hold=3d | positive pre-2023 | 29 | 469.7 | 455.3 | 459.4 | 14.4 | 0.22 / 0.21 / 0.22 | 675.9 / 661.5 |
| NQ 9 pair P&L prior 1d mode=neg dir=+1 hold=2d | positive pre-2023 | 28 | 1108.8 | 1094.4 | 1098.5 | 14.4 | 0.49 / 0.48 / 0.49 | 596.1 / 581.8 |
| NQ 10 pair P&L prior 1d mode=neg dir=+1 hold=1d | positive pre-2023 | 37 | 391.6 | 377.3 | 381.4 | 14.4 | 0.20 / 0.20 / 0.20 | 240.2 / 225.8 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): NQ: 14 cells pass the clean rule against a replicate mean of 5.7 (p(count) = 0.00, p(top) = 0.07).
- Of 10 selected cells, 1 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.23 (NQ pair P&L prior 5d mode=pos dir=+1 hold=2d); bootstrap lower bound > 0 for 2 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 4; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell NQ pair P&L prior 1d mode=pm dir=+1 hold=3d: uplift +0.10/+0.34/+0.12, boot lo -0.04, plateau 0.00, 2x-slip +0.13, wd corr +0.17, ERA positive pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 9, 'negative pre-2023': 1}.

## 7. Executability and margin
CME-group futures; executable at NinjaTrader Brokerage via Rithmic expected (not checked against the brokerage product list); new NT8 strategy needed, separate from DualStrat. Margin unverified (rough intraday margins ES ~$1.2-1.5k, NQ ~$1.5-2k, RTY ~$0.8k, YM ~$1k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k, BTC ~$20k+ overnight; unverified). Sleeve size = scale factor in the CSV (contracts matching the pair's clean weekly sigma).

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_sw_32.py, ap_sw_pipe.py (= ap_b_pipe2 with module swap), ap_sw_job.sh, ap_sw_common.py, ap_sw_report2.py in code/census/night_ins/; data in outputs/autopilot/b/sw32/ (`SW32_CO_all_selected_scored.csv`).

DONE SW32
