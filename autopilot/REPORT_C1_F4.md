# C1-F4 — INDEX RELATIVE-VALUE SPREADS (NQ/ES/RTY/YM)   [AUTOPILOT cycle 1]
Registered in PREREG_AUTOPILOT.md before the first run. Pair baseline: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a clean process (1.46/2.83/2.30 clean/H1/H2); robustness line vs B.Cfg() (1.35/1.65/2.26). UNTOUCHED never read. Selection on clean only (top 10 of 480 by clean additive-20% dSharpe); H1/H2 read afterwards, all 10 reported.

## Verdict: **NOT FOUND, and not a LEAD.** 0 of 480 cells keep a +0.10 Sharpe uplift on clean, H1 and H2 together; the best clean-selected cells are daily mean-reversion spreads that lose money in H2.
- **Regime flip, not diversification:** daily MR spreads earn clean Sharpe 0.58 (median) and H1 1.72 but H2 -1.00; daily TREND spreads do the opposite (-0.73 / -1.85 / +0.90). Only 8 of 480 cells have a positive standalone Sharpe in all three spans.
- **Intraday (5-min) spreads lose at 1-tick costs:** MR median all-in Sharpe -1.24 (about 2,800 trades each, churn), trend -0.19.
- **Every clean-selected cell is small-sample** (19-56 trades in the pair window) and fails the H2 uplift gate (-0.03 to -0.16); plateau, 2x slippage and the bootstrap lower bound (<=+0.03) also fail or are marginal.

## Method (what was simulated)
- **Data:** purchased GLBX.MDP3 1-minute bars (NQ, ES, RTY, YM; 2023-01 to 2026-10-13) resampled to 5-minute bars (fills at the next bar open); daily versions use the Databento daily bars (UTC days, so the daily close is 20:00 ET; the same-close caveat of T4) over 2013-2026, scored from 2023-08. Continuous .v.0 series are **difference back-adjusted at instrument_id changes**; the spread is L = log(A)-log(B) of adjusted prices, z = (L - rolling mean)/rolling std over {1d=276, 3d=828, 10d=2760} 5-min bars or {20,60} days.
- **Rules:** MR: z>=ze -> short A/long B (z<=-ze reverse); exit when the entry-signed z <= zx; stop at zs. TREND: z>=ze -> long A/short B; exit at zx; protective stop at 2ze-zs when above zx. Intraday: entries 18:00-15:00 ET except 09:00-09:58, flat at the open of the 16:55 ET bar (also on data gaps). One position per cell. Stops are tested on bar closes (executed next open), so stop-outs can overshoot.
- **Sizing (ratio rule):** dollar-neutral legs. Each leg's notional N = RS/D, with RS = $19,200 (the pair's two-book R) and D the distance to the stop in log-ratio units, so a stop-out costs about RS. Contracts in full-equivalents rounded to 0.1 (micro lots), minimum 0.1, **cap 6 full-equivalents per leg**. The cap binds on most trades (cap_frac column of GRID.csv): the real risk per trade is below RS and the sleeve's weekly volatility is 22-49% of the pair's in the selected cells.
- **Costs:** ES 0.5 tick/side, NQ/RTY/YM 1 tick/side, plus $2.18/side per full-equivalent per leg commission, on both legs, entry and exit.
- **Scoring:** code/census/night_ins/t3_score.py (additive 10/20/30/50% and constant-risk), amended gates: own timing-destroyed null (random entries, same trade count, same hold lengths, same sizing rule, 200 draws; random dates for the daily versions) at p95 on standalone all-in Sharpe, bootstrap 90% interval of the additive uplift, worst-decile correlation <= +0.30. The circular-shift null is reported.
- Runtime: grid 480 cells in 22 s on 4 workers; selected-cell scoring (nulls, plateau, 2x slippage) a few seconds. Whole family about 25 minutes including coding.

## Grid summary (480 cells = 4 pairs x {5m: 3 lookbacks, 1d: 2 lookbacks} x MR/TREND x ze{1.5,2,2.5} x zx{0,0.5} x zs{3,4})
| tf | mode | clean | H1 | H2 | all | share net>0 all-in | cells | median trades |
|---|---|---|---|---|---|---|---|---|
| 1d | MR | 0.58 | 1.72 | -1.0 | 0.34 | 0.88 | 96 | 87.0 |
| 1d | TR | -0.73 | -1.85 | 0.9 | -0.5 | 0.08 | 96 | 79.5 |
| 5m | MR | -1.57 | 0.0 | -1.54 | -1.24 | 0.08 | 144 | 2795.5 |
| 5m | TR | 0.02 | -1.53 | 0.24 | -0.19 | 0.38 | 144 | 710.5 |

Median standalone weekly Sharpe by span. Intraday = 5m. Cells with positive standalone Sharpe in all of clean, H1 and H2: 8 of 480.

## The 10 clean-selected cells, read on H1/H2
| # | pair | tf/lookback | mode | ze/zx/zs | trades in pair window | small-sample | standalone Sharpe clean/H1/H2/all | 2013-26 Sharpe | own-null p95 (rank) | add 20% dSharpe clean/H1/H2 | boot lo | worst-decile corr | plateau | 2x slip dSharpe c/H1/H2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | NQ-ES | 1d/20d | MR | 2.0/0.0/3.0 | 41 | YES | 1.92/2.69/-1.40/0.73 | 0.06 | 0.77 (0.93) | +0.12/+0.16/-0.16 | -0.01 | +0.24 | 71% | +0.11/+0.16/-0.16 |
| 2 | NQ-ES | 1d/20d | MR | 2.0/0.0/4.0 | 40 | YES | 2.46/2.53/-0.74/1.40 | 0.05 | 0.70 (1.00) | +0.09/+0.13/-0.03 | +0.03 | +0.11 | 50% | +0.09/+0.13/-0.03 |
| 3 | NQ-ES | 1d/20d | MR | 1.5/0.0/3.0 | 56 | YES | 1.49/1.60/-1.12/0.63 | 0.12 | 0.81 (0.91) | +0.09/+0.09/-0.06 | -0.01 | +0.14 | 62% | +0.09/+0.09/-0.06 |
| 4 | NQ-ES | 1d/20d | MR | 2.0/0.5/3.0 | 43 | YES | 1.46/1.90/-1.70/0.28 | -0.15 | 0.95 (0.65) | +0.08/+0.10/-0.20 | -0.05 | +0.36 | 86% | +0.07/+0.10/-0.20 |
| 5 | NQ-RTY | 1d/20d | MR | 2.5/0.0/3.0 | 19 | YES | 1.23/2.20/-1.68/0.47 | 0.41 | 0.85 (0.77) | +0.07/+0.22/-0.09 | -0.02 | -0.18 | 83% | +0.07/+0.22/-0.09 |
| 6 | NQ-RTY | 1d/20d | MR | 1.5/0.0/3.0 | 54 | YES | 0.86/2.56/-2.25/0.36 | 0.36 | 0.91 (0.77) | +0.07/+0.21/-0.10 | -0.02 | -0.25 | 75% | +0.07/+0.20/-0.10 |
| 7 | NQ-ES | 1d/20d | MR | 1.5/0.0/4.0 | 54 | YES | 1.75/2.09/-1.17/0.94 | 0.11 | 0.65 (0.98) | +0.07/+0.10/-0.03 | +0.01 | +0.15 | 62% | +0.07/+0.10/-0.03 |
| 8 | NQ-RTY | 1d/20d | MR | 2.0/0.0/3.0 | 36 | YES | 0.76/3.76/-1.86/0.32 | 0.29 | 0.78 (0.76) | +0.07/+0.30/-0.11 | -0.03 | -0.47 | 71% | +0.06/+0.30/-0.12 |
| 9 | NQ-RTY | 1d/20d | MR | 2.0/0.5/3.0 | 39 | YES | 0.92/3.46/-1.75/0.33 | 0.29 | 0.95 (0.71) | +0.06/+0.28/-0.11 | -0.02 | -0.36 | 71% | +0.06/+0.28/-0.11 |
| 10 | NQ-ES | 1d/20d | MR | 2.0/0.5/4.0 | 42 | YES | 1.96/1.63/-1.28/0.88 | -0.17 | 0.74 (0.98) | +0.06/+0.07/-0.07 | -0.00 | +0.28 | 62% | +0.06/+0.07/-0.07 |

Gate checklist (all must hold for FOUND): (3) dSharpe >= +0.10 on clean, H1 and H2 -> **fails in all 10 on H2 (-0.03 to -0.20)**; (4) own-null p95 and bootstrap lower bound > 0 -> own-null p95 on standalone Sharpe is cleared only by #2, #7 and #10; bootstrap lower bounds are -0.05 to +0.03, **fail** for all; (5) plateau >= 75% of neighbours -> 50-86%, passes for 3 of 10 but the H2 failure dominates; 2x slippage keeps clean/H1 uplift roughly (the churn is low for daily cells); (6) worst-decile correlation <= +0.30: passes for 9 of 10; (2) selection was clean-only (clean uplift +0.06 to +0.12 is the selection statistic, so it is optimistic).

## Cell #1 in detail (NQ-ES 20d MR, ze 2 / zx 0 / zs 3)
| framing | share | dSharpe clean/H1/H2 | worst wk chg (all-in) | net chg all-in | CVaR5 impr | maxDD impr | shift-null p95 / rank | boot 90% CI |
|---|---|---|---|---|---|---|---|---|
| additive | 10% | +0.06/+0.08/-0.07 | +3% | +1.6% | -0% | +5% | +0.04 / 0.71 | [-0.00,+0.07] |
| additive | 20% | +0.12/+0.16/-0.16 | +6% | +3.3% | -1% | +9% | +0.08 / 0.71 | [-0.01,+0.14] |
| additive | 30% | +0.17/+0.23/-0.25 | +9% | +4.9% | -2% | +14% | +0.11 / 0.71 | [-0.02,+0.20] |
| additive | 50% | +0.28/+0.36/-0.45 | +16% | +8.2% | -3% | +18% | +0.17 / 0.71 | [-0.05,+0.31] |
| constant-risk | 10% | +0.06/+0.09/-0.08 | -7% | -8.4% | +10% | +15% | +0.04 / 0.71 | [-0.00,+0.08] |
| constant-risk | 20% | +0.14/+0.19/-0.20 | -14% | -16.7% | +19% | +29% | +0.10 / 0.71 | [-0.01,+0.17] |
| constant-risk | 30% | +0.24/+0.32/-0.38 | -21% | -25.1% | +28% | +42% | +0.15 / 0.71 | [-0.04,+0.27] |
| constant-risk | 50% | +0.50/+0.61/-1.01 | -34% | -41.8% | +46% | +55% | +0.25 / 0.71 | [-0.19,+0.52] |

Versus the B.Cfg() pair (1.35/1.65/2.26):
| share | dSharpe vs B.Cfg() pair clean/H1/H2 |
|---|---|
| 10% | +0.06/+0.07/-0.08 |
| 20% | +0.11/+0.14/-0.18 |
| 30% | +0.16/+0.20/-0.28 |
| 50% | +0.26/+0.33/-0.49 |

Neighbours (+-25% one at a time): plateau fraction 71% keep >=75% of the all-in uplift.
| key | mult | all_dsharpe | clean | H1 | H2 |
|---|---|---|---|---|---|
| w | 0.75 | 0.03 | 0.05 | 0.19 | -0.13 |
| w | 1.25 | 0.08 | 0.1 | 0.16 | -0.04 |
| ze | 0.75 | 0.06 | 0.09 | 0.09 | -0.06 |
| ze | 1.25 | 0.05 | 0.05 | 0.13 | -0.01 |
| zs | 1.25 | 0.08 | 0.1 | 0.14 | -0.04 |
| zx | -0.25 | 0.06 | 0.12 | 0.16 | -0.16 |
| zx | 0.25 | 0.03 | 0.09 | 0.13 | -0.2 |

- Executability: both legs are CME index futures (NQ/MNQ, ES/MES, RTY/M2K, YM/MYM), tradable at NinjaTrader Brokerage via Rithmic as two separate orders; NT8 would need a two-leg ATM or a spread strategy running on two data series. **Margin:** assumed per full contract NQ $22k, ES $15k, RTY $9k, YM $11k, **no spread credit** (unverified; CME inter-commodity credits for NQ/ES exist but I did not verify them). Average sleeve margin at 100% share for cell #1: $220k (the sleeve at 20% share needs about a fifth of that).
- Fill model: next-bar open with 1/0.5 tick slippage per leg; no legging risk is modelled (both legs fill at the same bar open). Slippage as in the other families (1 tick/side NQ/RTY/YM, 0.5 ES).

## Why this is not a find
1. The daily MR edge is a clean/H1 effect that reverses in 2026 (all 10 selected cells have H2 standalone Sharpe -0.7 to -2.3). The TREND daily spreads show the mirror image (positive H2, negative clean), i.e. regime dependence, not a stable structure. The spreads that have been mean-reverting lately are the ones the pair hurts in; they would have added in 2023-25 but cost in 2026.
2. With 19-56 trades in the pair window the bootstrap and nulls are weak; none of the 10 clears bootstrap > 0.
3. Intraday relative value (the high-trade-count version, where a null would mean something) loses to costs.
4. The 2013-2026 daily standalone Sharpe of the selected cells is -0.17 to 0.41 (daily UTC-bar caveat), so a weak long-history positive exists, which is what a risk-premium-like MR effect would look like - but it is not enough for the gates.

Files: outputs/autopilot/c1/f4/{GRID.csv, GRID_S.npy, DAYS.npy, SELECTED.pkl}; code ap_c1_f4_core.py, ap_c1_f4_run.py, ap_c1_f4_sel.py, ap_c1_f4_report.py in code/census/night_ins/.
Costs/limits: no netting against the pair's NQ lots; legging, spread margin credits and roll costs of overnight daily positions are not modelled (positions carried through rolls pay one round-trip slippage in the daily version only in the P&L rollcost term, set to 1.0 for daily cells).

DONE C1_F4
