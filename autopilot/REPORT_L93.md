# REPORT L93 - GC fade cure: plateau, stop model and neighbourhood ensemble (BACKLOG2 item 93)

**Verdict: LEAD (strong; replication not met). FOUND 0.** Equal-risk ensemble of the 108-cell GC 5-min Supertrend-fade neighbourhood: uplift at 20% +0.20 / +0.95 / +0.83 on clean / H1 / H2, bootstrap lower bound +0.15, plateau 1.00, stop-model neutral, 2x-slippage +0.14/+0.87/+0.76, worst-decile correlation +0.06; fails amendment-2 replication (H0 weak only; odd-month half 34% of the uplift; SI -0.07, HG -0.12) and rests on a window whose centre cell is already read.

Pre-registered in PREREG_AUTOPILOT.md ('BACKLOG2 GROUP L') before the first run. Fill model: signal at bar close, entry next 1-minute open, 1 tick adverse per side (stop-market with slippage; targets none), $4.36 per contract round trip, 2x slippage = 2 ticks; code ap_b_base.py, L93 module, ap_l_cure.py, ap_l_era.py; data outputs/autopilot/l/l93/. Baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (clean/H1/H2 Sharpe 1.46/2.83/2.30). Selection: none (the whole pre-registered neighbourhood is averaged with equal risk; nothing is picked among cells).

IMPORTANT: this neighbourhood is built around a cell whose clean/H1/H2 results are already known (B-family lead). It is therefore a CURE ATTEMPT, not an independent test: the three spans are not untouched for the centre cell. A pass can at most make it a candidate for a rolling-data (new live weeks) read.

## 1. Grid summary
108 cells; uplift >= +0.10 on clean, H1 and H2 together in 54; positive all-in uplift in 107; median uplift clean/H1/H2 0.16 / 0.61 / 0.59; best/worst all-in 0.56 / -0.03.

## 2. Equal-risk ensembles: additive framing and all gates
| ensemble | cells | standalone Sharpe clean / H1 / H2 | OOS (H1+H2) | uplift@10% clean/H1/H2 | uplift@20% | uplift@30% | uplift@50% | boot lo @20% | worst-week chg @20% (%) | timing-destroyed ensemble null p95 (rank) | wd corr | 2x-slip uplift@20% | leave-one-value-out plateau | alt months odd / even | H0 Sharpe |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | 108 | 1.45 / 2.19 / 1.53 | 1.79 | 0.11 / 0.61 / 0.52 | 0.20 / 0.95 / 0.83 | 0.28 / 1.04 / 0.90 | 0.38 / 0.89 / 0.70 | 0.15 | 17.5 | -0.99 (1.00) | 0.06 | 0.14 / 0.87 / 0.76 | 1.00 | 0.15 / 0.68 | 0.29 |
| stop0.0 | 27 | 1.58 / 1.63 / 1.47 | 1.54 | 0.13 / 0.47 / 0.51 | 0.24 / 0.68 / 0.80 | 0.33 / 0.67 / 0.86 | 0.45 / 0.40 / 0.65 | 0.12 | 18.2 | -0.04 (1.00) | 0.10 | 0.18 / 0.61 / 0.74 | 1.00 | 0.20 / 0.60 | -0.22 |
| stop0.5 | 27 | 1.16 / 2.60 / 1.48 | 1.94 | 0.08 / 0.69 / 0.48 | 0.13 / 1.09 / 0.76 | 0.18 / 1.22 / 0.84 | 0.22 / 1.13 / 0.66 | 0.11 | 15.8 | -0.40 (1.00) | 0.05 | 0.07 / 1.01 / 0.70 | 1.00 | 0.07 / 0.70 | 0.52 |
| stop0.75 | 27 | 1.30 / 2.30 / 1.65 | 1.90 | 0.10 / 0.63 / 0.54 | 0.18 / 1.00 / 0.88 | 0.24 / 1.13 / 0.98 | 0.33 / 1.01 / 0.82 | 0.15 | 18.3 | -0.17 (1.00) | 0.03 | 0.12 / 0.93 / 0.81 | 1.00 | 0.16 / 0.67 | 0.48 |
| stop1.0 | 27 | 1.64 / 2.01 / 1.43 | 1.64 | 0.13 / 0.56 / 0.50 | 0.24 / 0.89 / 0.78 | 0.33 / 0.98 / 0.83 | 0.46 / 0.81 / 0.60 | 0.15 | 17.1 | -0.09 (1.00) | 0.08 | 0.18 / 0.81 / 0.72 | 1.00 | 0.16 / 0.67 | 0.35 |

## 3. Constant-risk framing (INSURANCE test: net >= -5% and worst week / CVaR5 improvement >= 20%)
| ensemble | const20 net % | ww impr % | CVaR5 impr % | const30 net % | ww impr % | CVaR5 impr % |
|---|---|---|---|---|---|---|
| ALL | 9.5 | 1.1 | 10.3 | 14.3 | -1.6 | 12.2 |
| stop0.0 | 7.8 | 0.6 | 10.1 | 11.8 | -6.9 | 5.3 |
| stop0.5 | 8.9 | 2.9 | 9.5 | 13.3 | -9.2 | 8.6 |
| stop0.75 | 9.3 | 0.3 | 10.0 | 14.0 | -2.8 | 12.5 |
| stop1.0 | 9.2 | 1.6 | 10.5 | 13.8 | -0.9 | 12.4 |

## 4. Replication (amendment 2)
Alternating months and H0 are in the ensemble table. Cross-instrument (same grid, same ensemble recipe):
| instrument | standalone Sharpe all-in | OOS | uplift clean / H1 / H2 | all-in |
|---|---|---|---|---|
| SI | 0.51 | 0.92 | -0.10 / -0.10 / -0.34 | -0.07 |
| HG | -0.39 | 0.84 | -0.27 / -0.02 / 0.19 | -0.12 |

## 5. ERA FLAG and cost decomposition
L93 GC cells 108 pre-2023 weekly Sharpe gross/net/netscaled 0.58 -0.11 0.16 | clean 1.88 1.45 1.45 mean per-trade pre-2023 ($ at 1 contract-equivalent) gross/net/netscaled 19.8 -4.6 5.2 trades/cell 3292 ERA FLAG: gross-positive, cost-negative pre-2023 

## 6. What this says
- **The whole GC fade neighbourhood, averaged with equal risk, adds to the pair on H1 and H2 by a wide margin and survives the plateau and the stop-model questions.** ALL-108 ensemble: standalone Sharpe 1.45 / 2.19 / 1.53 on clean / H1 / H2, out-of-selection (H1+H2) 1.79; uplift at 10% share +0.11 / +0.61 / +0.52, at 20% +0.20 / +0.95 / +0.83 (all-in +0.44), at 30% +0.28 / +1.04 / +0.90, at 50% +0.38 / +0.89 / +0.70 (but the worst week worsens by 54%, above the 50% allowance, and the bootstrap lower bound is -0.04); worst week +5.5% / +17.5% / +29.6% at 10/20/30% (inside the share allowances); bootstrap 90% lower bound +0.10 / +0.15 / +0.13 at 10/20/30%; worst-decile correlation +0.06; 2x slippage uplift at 20% +0.14 / +0.87 / +0.76; leave-one-value-out plateau 1.00 (every axis value dropped keeps >= 75% of the uplift); timing-destroyed ensemble null p95 -0.99 (rank 1.00; lenient, independent random books diversify). **Stop model:** the same ensemble at each stop level (none, 0.5, 0.75, 1.0 x ADR20) is essentially identical (all-in uplift +0.42 / +0.41 / +0.45 / +0.45), so a catastrophic stop of 0.5 ADR costs nothing in this window: the no-stop worry of B7 is answered for this sample. Of the 108 single cells the number with +0.10 on all three spans is in section 1.
- **Replication fails, so this is a strong LEAD and not FOUND-PENDING.** H0 2023-02..07: ensemble standalone Sharpe +0.29 (weak positive; no-stop sub-ensemble -0.22). Alternating months: odd months +0.15 and even months +0.68 against +0.44 overall; the pre-registered rule needs BOTH halves >= 50% of the overall uplift (0.22) and the odd half is 34% of it: fails. Cross-metal (same recipe on SI and HG): uplift -0.07 and -0.12 all-in: fails; ES/RTY cross-instrument was shown to fail for the centre cell in B7 (-0.08 / -0.07). Live weeks: none yet. So 1 of 4 (H0, weak): amendment-2 replication is NOT met. 
- **ERA FLAG: gross-positive, cost-negative pre-2023** (2013-2022: weekly Sharpe gross +0.58, net at fixed cost -0.11, net at price-scaled cost +0.16; $19.8 gross / -$4.6 net / +$5.2 price-scaled per trade at one contract-equivalent over about 3,300 trades per cell). In 2023-26 clean the same ensemble earns 1.88 gross / 1.45 net: the fade edge exists in gross terms in both eras and the modern price level (about 8x, so ~8x lower relative cost) makes it net-positive. Mechanism in one sentence: five-minute Supertrend flips in gold are mostly noise that mean-reverts over three to five hours, and faded entries harvest that reversion; it plausibly depends on current structure (relative cost) and on gold's 2025-26 volatility (the spread of uplift is much larger in H1/H2 than in clean).
- **What it would take to call it FOUND:** (1) new rolling-data weeks (live weeks) from now on with the ensemble frozen as pre-registered here (a sleeve of 108 cells is NT8-codable as one strategy with 3 parameters per leg; or the single 5-min ST(14,2.0) fade cell with a 0.5 ADR stop and a 240-minute hold as its centre); (2) a second metal or an independent period to confirm; neither exists yet. Sizing: the vol-matched ensemble at 20% share is about 4-6 GC contracts (the centre cell needed 19.4 contracts at 100% of pair volatility; its worst single trade is -$19.6k per contract, i.e. -$76k at 3.9 contracts without a stop and -$36k with the 0.5 ADR stop (corrected in REPORT_GC_FADE_V2.md)); margin about $10-12k per contract overnight, day-session-only entries with all trades flat by 16:55 ET so intraday margin applies.


DONE L93
