# REPORT Q8D - Q8D: B11 grid on ETH (ETH)

**Verdict: LEAD. FOUND 0, LEAD 2, INSURANCE 0.** 10 selected cells (+0 diagnostic) scored on 1 instruments; best non-diagnostic all-in additive uplift at 20% share +0.29; best pair-window standalone Sharpe +1.90.

## Protocol (pre-registered in PREREG_AUTOPILOT.md, 'CYCLE 12: B-FAMILIES', before the first run)
- Levels: opening range of the first 15/30/60 min of the instrument RTH (ES/RTY 09:30, GC/ZN 08:20, CL 09:00 ET) or the prior trading day's high/low. First tf-bar close beyond a level per day, trade with (breakout) or against (fade); stop a x ADR20, bracket 1R/2R target, trail, or hold to flat.
- Instruments: ETH. Grid: 192 cells per instrument = 4 levels x 2 bar sizes x 2 modes x 12 exits.
- Fill model: signal at tf-bar close, entry at the next 1-minute open, 1 tick adverse per side (ZN 1/64) on entries, stops and time/flatten exits, targets as limits without slippage, stop-first inside a 1-minute row, stop gaps at the open, + $4.36 per contract round trip (assumption, scaled by quantity). 2x slippage = 2 ticks/side. Sizing: 1 contract, then scaled to the pair's clean weekly sigma. No netting against the pair's lots.
- Selection (GATE AMENDMENT 2, clean only): >=100 trades in clean 2023-08..2025-07 and positive weekly Sharpe in both clean halves; top 10 per instrument by clean weekly Sharpe; if fewer pass, up to 3 best failing cells are read as DIAGNOSTIC (cannot be FOUND). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 read once after selection. 2013-22 (pre-2023) is not a gate: it is reported as an ERA FLAG with cost decomposition (section 6a). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30).

## 1. Clean-only selection and the false-survivor test (timing-destroyed replicates of the whole grid per instrument, same rule)
| sym   |   cells |   eligible |   passing |   best_clean_sharpe |   max_halves_pos |   selected |   diagnostic |
|:------|--------:|-----------:|----------:|--------------------:|-----------------:|-----------:|-------------:|
| ETH   |     192 |        192 |        35 |               1.921 |                2 |         10 |            0 |

| sym   |   n_rep |   cells passing rule |   replicate mean |   replicate max |   p(count) |   real top mean sel. Sharpe |   replicate mean |   replicate p95 |   p(top) |   real best |   replicate best p95 |
|:------|--------:|---------------------:|-----------------:|----------------:|-----------:|----------------------------:|-----------------:|----------------:|---------:|------------:|---------------------:|
| ETH   |     100 |                   35 |            24.52 |              43 |       0.02 |                       1.566 |            1.018 |           1.238 |        0 |       1.921 |                2.023 |

Reading: p(count) is the share of replicates with at least as many cells passing the year-consistency rule as the real grid; p(top) is the share whose top-cell mean selection Sharpe is at least the real one. Values near 0 mean the real grid holds structure beyond chance in the clean span; values above 0.05 mean nothing beyond chance was found.

## 2. Pair-window read of ALL selected cells (nothing omitted)
| cell | description | trades clean | halves pos | Sharpe clean | Sharpe pre-2023 (ERA) | Sharpe all-in | OOS (H1+H2) Sharpe / null p95 | uplift@20% clean / H1 / H2 | all-in uplift 2x slip | worst-decile corr | own-null rank | boot lo (20%) | plateau | trades pair win | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH 1 | PD 15m with exit=hd0.1xADR | 328 | 2 | 1.92 | 0.61 | 1.90 | 1.87 / 1.36 | 0.34 / 0.39 / -0.05 | 0.24 | -0.10 | 1.00 | 0.12 | 0.50 | 514 | NO |
| ETH 2 | PD 15m with exit=b10.1xADR | 328 | 2 | 1.78 | -1.15 | 1.63 | 1.34 / 1.10 | 0.37 / 0.21 / -0.09 | 0.16 | -0.33 | 1.00 | 0.07 | 0.50 | 514 | NO |
| ETH 3 | PD 15m with exit=hd0.2xADR | 328 | 2 | 1.76 | 0.55 | 1.80 | 1.87 / 1.38 | 0.31 / 0.46 / -0.03 | 0.23 | -0.16 | 1.00 | 0.10 | 1.00 | 514 | NO |
| ETH 4 | PD 15m with exit=b10.2xADR | 328 | 2 | 1.65 | -1.04 | 1.53 | 1.38 / 1.03 | 0.29 / 0.32 / -0.12 | 0.16 | -0.17 | 1.00 | 0.03 | 0.50 | 514 | NO |
| ETH 5 | PD 15m with exit=tr0.2xADR | 328 | 2 | 1.56 | 0.19 | 1.79 | 2.14 / 1.15 | 0.28 / 0.34 / 0.13 | 0.20 | -0.09 | 1.00 | 0.09 | 0.50 | 514 | LEAD |
| ETH 6 | PD 15m with exit=b20.1xADR | 328 | 2 | 1.46 | -0.85 | 1.78 | 2.25 / 1.15 | 0.26 / 0.52 / -0.04 | 0.19 | -0.25 | 1.00 | 0.09 | 0.50 | 514 | NO |
| ETH 7 | OR15 5m with exit=hd0.1xADR | 505 | 2 | 1.44 | 0.77 | 1.47 | 1.43 / 1.23 | 0.27 / 0.28 / 0.02 | 0.15 | 0.08 | 1.00 | 0.05 | 0.75 | 796 | NO |
| ETH 8 | PD 5m with exit=hd0.1xADR | 341 | 2 | 1.42 | -0.24 | 1.52 | 1.69 / 1.36 | 0.22 / 0.46 / 0.07 | 0.17 | -0.26 | 1.00 | 0.05 | 1.00 | 540 | NO |
| ETH 9 | PD 5m with exit=tr0.2xADR | 341 | 2 | 1.38 | -0.14 | 1.79 | 2.40 / 1.30 | 0.20 / 0.56 / 0.11 | 0.18 | -0.23 | 1.00 | 0.07 | 0.50 | 540 | LEAD |
| ETH 10 | PD 15m with exit=b20.2xADR | 328 | 2 | 1.29 | -0.38 | 1.30 | 1.35 / 1.14 | 0.21 / 0.19 / -0.07 | 0.11 | -0.36 | 1.00 | -0.02 | 0.50 | 514 | NO |

(S = small-sample, < 100 trades in the pair window; Sharpe full history = weekly Sharpe over the whole available history; uplift = change in the pair's weekly Sharpe from adding the sleeve at 20% share.)

## 3. Gate counts
| gate | count |
|---|---|
| selected (non-diagnostic) cells scored | 10 |
| diagnostic cells read | 0 |
| uplift >= +0.10 on clean, H1, H2 together at 10/20/30/50% (non-diag) | 0 / 2 / 2 / 2 |
| all-in uplift @20% > 0 (all scored) | 10 |
| bootstrap 90% lower bound > 0 @20% (all scored) | 9 |
| standalone pair-window Sharpe above own random-entry null p95 | 10 |
| worst-decile corr <= +0.30 | 10 |
| plateau >= 0.75 | 3 |
| all-in uplift at 2x slippage >= +0.10 | 10 |
| small-sample (<100 trades pair window) | 0 |
| gate_add PASS at any share (non-diag) | 0 |

## 4. Insurance metric set (best-uplift cell per instrument; sleeve standalone at its scale, and pair + 20% sleeve)
| cell | span | sleeve Sharpe | Sortino | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | MAR | % neg wk | pair+20% Sharpe | pair+20% CVaR5 | pair+20% maxDD | pair+20% worst wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ETH PD 15m with exit=hd0.1xADR | clean | 1.90 | 4.92 | -65105 | -58946 | 233473 | -85322 | 7.39 | 48.6 | 1.80 | -84269 | 242802 | -87885 |
| ETH PD 15m with exit=hd0.1xADR | H1 | 3.00 | 8.82 | -85302 | -76884 | 174088 | -87826 | 5.53 | 39.3 | 3.22 | -82553 | 144246 | -94843 |
| ETH PD 15m with exit=hd0.1xADR | H2 | 0.58 | 1.61 | -34629 | -31737 | 247649 | -37157 | 0.56 | 66.7 | 2.25 | -84431 | 228547 | -85626 |
| ETH PD 15m with exit=hd0.1xADR | all | 1.90 | 5.12 | -69031 | -58669 | 247649 | -87826 | 11.41 | 50.6 | 2.14 | -85480 | 242802 | -94843 |


## 5. Constant-risk framing (30% share; total risk fixed, pair shrinks to fund the sleeve)
| cell | all-in net change % | worst-week improvement % | CVaR5 improvement % | maxDD improvement % | clean ww / CVaR5 | H1 ww / CVaR5 | verdict |
|---|---|---|---|---|---|---|---|
| ETH PD 15m with exit=hd0.1xADR | 1.6 | 3.5 | 16.9 | 39.7 | 14.8 / 17.9 | -1.7 / 20.4 | NO |

INSURANCE count: 0.

## 6a. ERA FLAG and cost decomposition (pre-2023 = before 2023-08; per trade in $ at the sleeve's sizing, 1 contract unless R-sized)
| cell | ERA flag | pre-2023 trades | gross $/trade | net $/trade (fixed cost) | net $/trade (price-scaled cost) | cost $/trade | pre-2023 weekly Sharpe gross / net / net scaled | clean gross / net $/trade |
|---|---|---|---|---|---|---|---|---|
| ETH 1 PD 15m with exit=hd0.1xADR | positive pre-2023 | 238 | 126.7 | 72.3 | 87.4 | 54.4 | 1.06 / 0.61 / 0.73 | 388.0 / 333.6 |
| ETH 2 PD 15m with exit=b10.1xADR | negative pre-2023 | 238 | -16.8 | -58.8 | -47.2 | 42.0 | -0.32 / -1.15 / -0.92 | 153.4 / 113.8 |
| ETH 3 PD 15m with exit=hd0.2xADR | positive pre-2023 | 238 | 140.9 | 86.5 | 101.6 | 54.4 | 0.88 / 0.55 / 0.64 | 395.5 / 341.1 |
| ETH 4 PD 15m with exit=b10.2xADR | negative pre-2023 | 238 | -69.1 | -112.5 | -100.7 | 43.4 | -0.64 / -1.04 / -0.93 | 218.1 / 176.9 |
| ETH 5 PD 15m with exit=tr0.2xADR | positive pre-2023 | 238 | 71.7 | 17.3 | 32.4 | 54.4 | 0.69 / 0.19 / 0.32 | 240.6 / 186.2 |
| ETH 6 PD 15m with exit=b20.1xADR | negative pre-2023 | 238 | -11.4 | -57.4 | -44.9 | 46.0 | -0.16 / -0.85 / -0.66 | 181.6 / 137.0 |
| ETH 7 OR15 5m with exit=hd0.1xADR | positive pre-2023 | 377 | 127.1 | 72.7 | 88.5 | 54.4 | 1.35 / 0.77 / 0.94 | 244.9 / 190.6 |
| ETH 8 PD 5m with exit=hd0.1xADR | gross-positive, cost-negative pre-2023 | 249 | 25.0 | -29.3 | -14.4 | 54.4 | 0.23 / -0.24 / -0.11 | 263.1 / 208.7 |
| ETH 9 PD 5m with exit=tr0.2xADR | gross-positive, cost-negative pre-2023 | 249 | 36.2 | -18.1 | -3.2 | 54.4 | 0.33 / -0.14 / -0.01 | 201.8 / 147.5 |
| ETH 10 PD 15m with exit=b20.2xADR | negative pre-2023 | 238 | -2.2 | -51.0 | -37.6 | 48.8 | 0.00 / -0.38 / -0.28 | 241.0 / 193.7 |


## 6b. Replication tests (leads only)
No lead reached the replication stage (replication is evaluated for leads only).

## 6. What this says
- Clean-rule structure by instrument (chance comparison from 100 timing-destroyed replicates): ETH: 35 cells pass the clean rule against a replicate mean of 24.5 (p(count) = 0.02, p(top) = 0.00).
- Of 10 selected cells, 2 have an uplift >= +0.10 on clean, H1 and H2 together at 20% share; best all-in uplift +0.29 (ETH PD 15m with exit=hd0.1xADR); bootstrap lower bound > 0 for 9 cells; plateau >= 0.75 for 3; 2x-slippage all-in uplift >= +0.10 for 10; gate_add PASS at some share: 0 (cell-share pairs).
- Gate-3 cell ETH PD 15m with exit=tr0.2xADR: uplift +0.28/+0.34/+0.13, boot lo +0.09, plateau 0.50, 2x-slip +0.20, wd corr -0.09, ERA positive pre-2023 (replication not run unless stated below).
- Gate-3 cell ETH PD 5m with exit=tr0.2xADR: uplift +0.20/+0.56/+0.11, boot lo +0.07, plateau 0.50, 2x-slip +0.18, wd corr -0.23, ERA gross-positive, cost-negative pre-2023 (replication not run unless stated below).
- ERA flags: {'positive pre-2023': 4, 'negative pre-2023': 4, 'gross-positive, cost-negative pre-2023': 2}.

- **Manual review of the lead: ETH prior-day high/low break WITH the break (first 15-minute bar close beyond the prior trading day's high or low, trail 0.2 x ADR20, hold to 16:55 or trail).** Standalone Sharpe 1.56 / 2.80 / 1.46 on clean / H1 / H2 (out-of-selection 2.14 against its null p95 1.15); uplift at 20% +0.28 / +0.34 / +0.13 (10%: +0.15/+0.20/+0.07; 30%: +0.38/+0.42/+0.18; 50%: +0.54/+0.50/+0.24); bootstrap lower bound +0.09; worst-decile correlation -0.09; 2x slippage all-in +0.20; ERA positive pre-2023 (ETH 2022 only). It fails the worst-week gate (the pair's worst week gets 20.3% worse at 20% share and 33% at 30%, just over the share allowance) and the 10% share needs H2 +0.10 (it has +0.07); plateau 0.50. Replication: H0 2023-02..07 standalone Sharpe +2.07 on 75 trades holds (counts as >= 30 trades); BTC with the same cell +0.07 uplift (25% of the ETH uplift, positive sign); ES -0.31 and RTY -0.44 fail; alternating months odd +0.39, even +0.13 against +0.28 (even half 48%, a hair below the 50% rule): 1 of 4. The BTC prior-day break with-trail cell found in B11 (+0.20/+0.59/+0.08) is the same trade type, so the crypto prior-day-break family has two observations (BTC, ETH) that are highly correlated markets; verdict LEAD (gate 3 plus bootstrap), failing worst week, plateau and replication.

## 7. Executability and margin
All instruments are CME-group futures (CME/CBOT/COMEX/NYMEX); executable at NinjaTrader Brokerage via Rithmic is expected (general knowledge, not checked against the brokerage's product list); BTC/ETH are CME crypto futures (5 BTC / 50 ETH contracts; also MBT/MET micros). Spec for a cell that passed would be: instrument, bar size, entry rule, exit rule, session window, size, roll (continuous contract, roll at expiry by volume). Margin is unverified (rough CME intraday margins: ES ~$1.2-1.5k day / ~$13-15k overnight, RTY ~$7-9k, GC ~$9-11k, CL ~$5-7k, ZN ~$2k; unverified). Sleeve sizes come from the scale factor in the CSV (contracts to match the pair's weekly volatility). A found cell would need a new NT8 strategy (or DualStrat bar/exit options) separate from the NQ DualStrat; nothing here changes the execution server, charts or DualStrat.

## 8. Limitations
1-minute bars with stop-first fills, no queue model; costs are assumptions (1 tick/side, $4.36/RT) not calibrated to live fills; the own random-entry null uses random valid bars with the same trade count and alternating sides, which loses to cost, so null ranks near 1 are weak evidence; the sleeve's volatility-matching factor is estimated on the selection span; back-adjusted differences distort long-ago price levels but not point moves; the volatility-matching factor comes from the selection span, so it can oversize a sleeve in a later high-volatility regime (e.g. GC 2025-26 weekly losses of several sigma), which inflates dollar drawdowns in section 4 but not Sharpe; RTY has 2017-07+ history and BTC/ETH 2022+ only (selection power is low there).

Code: ap_b_base.py, ap_q8d.py (= ap_b11.py grid), ap_b_pipe.py, ap_b_driver.sh, ap_b_report.py in code/census/night_ins/; data in outputs/autopilot/b/q8d/ (`Q8D_CO_all_selected_scored.csv`).

DONE Q8D
