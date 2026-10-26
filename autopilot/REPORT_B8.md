# REPORT B8 - conditional hedge: 5-minute NQ ensemble switched on only after a losing pair stretch
**Verdict: NO.** The switch does not carry the hedge: at 20% additive, N=13 (clean-selected) gives Sharpe uplift +0.02 / 0.00 / 0.00 (clean/H1/H2) and N=8 (assigned) +0.01 / -0.04 / -0.07, against +0.19 / +0.50 / +0.32 for the always-on static blend. Circular-shift null (gating) rank 63% clean, 40% all-in for N=13 (p95 needed); bootstrap vs static [-0.45, -0.06]. Cells 24 live-window (+24 long-history), runtime 2 s (pool of 5 for the nulls). WT variant skipped (outputs/autopilot/REPORT_WT.md does not exist). Registered in PREREG_AUTOPILOT.md (B8) before the first run.

## Set-up and fill model
- Pair: live B.Cfg(wk_floor=8,wk_loss_pb=None) 8/8 (clean process, pair_xp.npz), weekly Sharpe clean/H1/H2/all 1.46/2.83/2.30/1.86. Sleeve = the V5 P1 five-book 5-minute NQ ensemble rebuilt at 1 tick/side + commission (market entry, 60/60 bracket, 5R/-2R rule), scaled so clean weekly sigma = share x pair's (same construction as C1-F2). 2x slippage = 2 ticks/side, size fixed.
- Rule: on in week t iff the pair's realised P&L over the N completed weeks before week t is < 0 (known at the Monday open; first N weeks off). N in {4,8,13}, shares 10/20/30/50%, additive (pair + on x s x S) and constant-risk ((1-s x on) pair + s x on x S). Selection of N on clean only (add + cr at 20%): scores N=4 -0.116, N=8 -0.047, N=13 +0.026 -> N=13. H1/H2 read once afterwards.
- Long history 2013-2022: C3-H3 primary five-book ensemble vs the 1-minute-engine pair (fidelity corr 0.88), same constants.

## Why it fails (the mechanism check)
- Pair weekly P&L is not positively autocorrelated (lag-1 -0.15 live window; -0.07 on 2013-2022): a losing stretch does not predict the next week's loss, so there is nothing to insure after one. Trailing sum < 0 is rare in the live window: the sleeve is on 17% of all-in weeks for N=8 and 9% for N=13 (H1/H2: 7%/6% and 0%/0%); in H1 and H2 with N=13 the switch is never on, so uplift is exactly 0.
- When it is on, the sleeve does NOT hedge: N=8 live, mean next-week ensemble P&L after a losing stretch is $-4,208 (vs +$9,264 otherwise) while the pair earns +$20,013 in those weeks. The ensemble's negative correlation (all-weeks -0.19) is a same-week relation; it does not translate into a trailing-state signal.
- 2013-2022 (pair loses, sleeve on 51% of weeks): uplift at 20% +0.006 (N=8), +0.023 (N=13) vs static +0.001 (C3-H3: +0.001); null p95 +0.051/+0.048, rank 57%/78%; bootstrap 90% CI [-0.09, +0.10] / [-0.07, +0.12]. Only at N=13/50% does it reach +0.10 (+0.101), which is not a gated cell and has a CI spanning zero.

## All 24 live-window cells (additive Sharpe uplift vs the pair; static blend for reference)
| N | share | framing | clean | H1 | H2 | all | static clean / H1 / H2 | on-fraction (all-in) |
|---|---|---|---|---|---|---|---|---|
| 4 | 10% | add | +0.00 | -0.04 | +0.08 | +0.02 | +0.10 / +0.28 / +0.17 | 30% |
| 4 | 10% | cr | -0.05 | -0.11 | +0.06 | -0.03 | +0.11 / +0.30 / +0.19 | 30% |
| 4 | 20% | add | +0.00 | -0.08 | +0.16 | +0.03 | +0.19 / +0.50 / +0.32 | 30% |
| 4 | 20% | cr | -0.12 | -0.23 | +0.10 | -0.08 | +0.23 / +0.58 / +0.39 | 30% |
| 4 | 30% | add | -0.01 | -0.13 | +0.23 | +0.04 | +0.26 / +0.65 / +0.45 | 30% |
| 4 | 30% | cr | -0.20 | -0.37 | +0.14 | -0.14 | +0.33 / +0.75 / +0.56 | 30% |
| 4 | 50% | add | -0.03 | -0.24 | +0.37 | +0.03 | +0.35 / +0.77 / +0.59 | 30% |
| 4 | 50% | cr | -0.40 | -0.70 | +0.15 | -0.31 | +0.30 / +0.51 / +0.39 | 30% |
| 8 | 10% | add | +0.00 | -0.02 | -0.04 | -0.01 | +0.10 / +0.28 / +0.17 | 17% |
| 8 | 10% | cr | -0.02 | -0.04 | -0.07 | -0.03 | +0.11 / +0.30 / +0.19 | 17% |
| 8 | 20% | add | +0.01 | -0.04 | -0.07 | -0.01 | +0.19 / +0.50 / +0.32 | 17% |
| 8 | 20% | cr | -0.05 | -0.09 | -0.14 | -0.07 | +0.23 / +0.58 / +0.39 | 17% |
| 8 | 30% | add | +0.00 | -0.06 | -0.11 | -0.03 | +0.26 / +0.65 / +0.45 | 17% |
| 8 | 30% | cr | -0.09 | -0.13 | -0.22 | -0.12 | +0.33 / +0.75 / +0.56 | 17% |
| 8 | 50% | add | -0.01 | -0.10 | -0.19 | -0.06 | +0.35 / +0.77 / +0.59 | 17% |
| 8 | 50% | cr | -0.18 | -0.23 | -0.39 | -0.23 | +0.30 / +0.51 / +0.39 | 17% |
| 13 | 10% | add | +0.01 | +0.00 | +0.00 | +0.01 | +0.10 / +0.28 / +0.17 | 9% |
| 13 | 10% | cr | +0.00 | +0.00 | +0.00 | +0.01 | +0.11 / +0.30 / +0.19 | 9% |
| 13 | 20% | add | +0.02 | +0.00 | +0.00 | +0.02 | +0.19 / +0.50 / +0.32 | 9% |
| 13 | 20% | cr | +0.00 | +0.00 | +0.00 | +0.01 | +0.23 / +0.58 / +0.39 | 9% |
| 13 | 30% | add | +0.03 | +0.00 | +0.00 | +0.02 | +0.26 / +0.65 / +0.45 | 9% |
| 13 | 30% | cr | -0.00 | +0.00 | +0.00 | +0.01 | +0.33 / +0.75 / +0.56 | 9% |
| 13 | 50% | add | +0.04 | +0.00 | +0.00 | +0.03 | +0.35 / +0.77 / +0.59 | 9% |
| 13 | 50% | cr | -0.02 | +0.00 | +0.00 | -0.01 | +0.30 / +0.51 / +0.39 | 9% |

Additive uplift and worst-week change (all-in, % of pair worst week) by N and share:
| N | share | clean | H1 | H2 | all | worst week change |
|---|---|---|---|---|---|---|
| 4 | 10% | +0.00 | -0.04 | +0.08 | +0.02 | +1.0% |
| 4 | 20% | +0.00 | -0.08 | +0.16 | +0.03 | -4.3% |
| 4 | 30% | -0.01 | -0.13 | +0.23 | +0.04 | -9.6% |
| 4 | 50% | -0.03 | -0.24 | +0.37 | +0.03 | -20.3% |
| 8 | 10% | +0.00 | -0.02 | -0.04 | -0.01 | +0.0% |
| 8 | 20% | +0.01 | -0.04 | -0.07 | -0.01 | -1.3% |
| 8 | 30% | +0.00 | -0.06 | -0.11 | -0.03 | -5.3% |
| 8 | 50% | -0.01 | -0.10 | -0.19 | -0.06 | -13.3% |
| 13 | 10% | +0.01 | +0.00 | +0.00 | +0.01 | +0.0% |
| 13 | 20% | +0.02 | +0.00 | +0.00 | +0.02 | -1.3% |
| 13 | 30% | +0.03 | +0.00 | +0.00 | +0.02 | -5.3% |
| 13 | 50% | +0.04 | +0.00 | +0.00 | +0.03 | -13.3% |

## 2013-2022 long history (pair+sleeve uplift over the whole 10 years; per-year for headline 20%)
| N | share | framing | switch uplift | static blend | on-fraction |
|---|---|---|---|---|---|
| 4 | 10% | add | +0.002 | -0.005 | 49% |
| 4 | 10% | cr | -0.016 | -0.004 | 49% |
| 4 | 20% | add | +0.011 | +0.001 | 49% |
| 4 | 20% | cr | -0.022 | +0.007 | 49% |
| 4 | 30% | add | +0.024 | +0.015 | 49% |
| 4 | 30% | cr | -0.014 | +0.047 | 49% |
| 4 | 50% | add | +0.066 | +0.069 | 49% |
| 4 | 50% | cr | +0.056 | +0.252 | 49% |
| 8 | 10% | add | -0.000 | -0.005 | 51% |
| 8 | 10% | cr | -0.025 | -0.004 | 51% |
| 8 | 20% | add | +0.006 | +0.001 | 51% |
| 8 | 20% | cr | -0.042 | +0.007 | 51% |
| 8 | 30% | add | +0.018 | +0.015 | 51% |
| 8 | 30% | cr | -0.043 | +0.047 | 51% |
| 8 | 50% | add | +0.060 | +0.069 | 51% |
| 8 | 50% | cr | +0.020 | +0.252 | 51% |
| 13 | 10% | add | +0.008 | -0.005 | 50% |
| 13 | 10% | cr | -0.009 | -0.004 | 50% |
| 13 | 20% | add | +0.023 | +0.001 | 50% |
| 13 | 20% | cr | -0.006 | +0.007 | 50% |
| 13 | 30% | add | +0.044 | +0.015 | 50% |
| 13 | 30% | cr | +0.013 | +0.047 | 50% |
| 13 | 50% | add | +0.101 | +0.069 | 50% |
| 13 | 50% | cr | +0.112 | +0.252 | 50% |

Per year (20%, additive): N=8: 2013: -0.19 | 2014: +0.19 | 2015: -0.00 | 2016: +0.02 | 2017: -0.02 | 2018: -0.05 | 2019: -0.09 | 2020: +0.17 | 2021: +0.01 | 2022: +0.04. N=13: 2013: -0.06 | 2014: +0.07 | 2015: -0.09 | 2016: +0.01 | 2017: -0.06 | 2018: +0.08 | 2019: -0.16 | 2020: +0.20 | 2021: +0.17 | 2022: -0.01.

## FOUND gate checklist (selected N=13 and assigned N=8, 20% additive)
| gate | N=13 | N=8 | pass |
|---|---|---|---|
| 1 pre-registered, clean-only selection, H1/H2 read once | yes | yes | PASS |
| 3 uplift >= +0.10 on clean/H1/H2 | +0.02 / +0.00 / +0.00 | +0.01 / -0.04 / -0.07 | FAIL (all shares: see table) |
| 3 worst week not worse than share | -1.3% | -1.3% | PASS |
| 4 circular-shift null (GATING, hedge claim) p95 vs real, rank (clean/H1/H2/all) | real +0.02 vs p95 +0.10; rank 63%/14%/17%/40% | real -0.01 vs p95 +0.13; rank 34%/19%/10%/7% | FAIL |
| 4 worst-decile corr of contribution with pair < 0 | undefined (sleeve off in the pair's worst weeks; on-fraction there 0%) | -0.01 (on in 10% of them) | N=13 n/a (no hedge), N=8 PASS on sign but contributes ~nothing |
| 4 bootstrap 90% CI of all-in uplift > 0 (vs pair) | [-0.04, +0.07] | [-0.08, +0.05] | FAIL |
| 4 bootstrap vs the static blend (incremental value of the switch) | [-0.45, -0.06] | [-0.48, -0.09] | FAIL (significantly WORSE than static) |
| 4 own timing-destroyed null on standalone Sharpe | sleeve: C3-H3 rank 97.5% vs 200 random-entry draws, but net Sharpe ~0 (+0.07); the switch is tested by the shift null above | | cited |
| 5 plateau (N x0.75/x1.25, share +-25%; 8 neighbours) | 0% | 0% | FAIL |
| 5 2x slippage (clean/H1/H2) | +0.01 / +0.00 / +0.00 | -0.01 / -0.04 / -0.08 | FAIL (no uplift to survive) |
| 6 worst-decile corr <= +0.30 | passes trivially (sleeve rarely on) | -0.01 | PASS (vacuous) |
| 7 executable | NT8: a new 5-minute NQ multi-book strategy + a Monday-open sizing step reading the pair's trailing 13/8-week realised P&L (account performance export or small script); NinjaTrader Brokerage via Rithmic; NQ margin ~$22k overnight/contract assumed | | spec only |

## Insurance metrics, selected N=13 20% (vs pair; improvement = switch vs pair)
Additive:
| span | Sharpe | Sortino | MAR | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | % neg wk | CVaR5 / worst wk / DD improvement | net cost |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.48 | 2.82 | 4.79 | -79,785 | -78,606 | 280,110 | -83,609 | 44% | -1.3% / -2.1% / +0.0% | +0.9% |
| H1 | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39% | +0.0% / +0.0% / +0.0% | +0.0% |
| H2 | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44% | +0.0% / +0.0% / +0.0% | +0.0% |
| all | 1.87 | 3.67 | 9.63 | -79,908 | -78,631 | 280,110 | -83,609 | 43% | -0.9% / -1.3% / +0.0% | +0.5% |

Constant-risk:
| span | Sharpe | Sortino | MAR | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | % neg wk | CVaR5 / worst wk / DD improvement | net cost |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 2.79 | 4.66 | -78,736 | -78,009 | 280,110 | -81,874 | 44% | +0.0% / +0.0% / +0.0% | -1.8% |
| H1 | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39% | +0.0% / +0.0% / +0.0% | +0.0% |
| H2 | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44% | +0.0% / +0.0% / +0.0% | +0.0% |
| all | 1.86 | 3.66 | 9.50 | -79,220 | -78,239 | 280,110 | -82,524 | 43% | +0.0% / +0.0% / +0.0% | -0.9% |

Verdict (rep_common INSURANCE rule): additive N=13 NO, constant-risk NO; N=8 NO/NO (all-in CVaR5 -0.9%, worst week -1.3%, max DD +2.5%).

N=8 insurance metrics (additive):
| span | Sharpe | Sortino | MAR | CVaR5 $ | CVaR10 $ | max DD $ | worst wk $ | % neg wk | CVaR5 / worst wk / DD improvement | net cost |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.47 | 2.79 | 4.87 | -79,785 | -78,581 | 272,984 | -83,609 | 43% | -1.3% / -2.1% / +2.5% | -0.1% |
| H1 | 2.79 | 6.07 | 3.90 | -77,610 | -66,030 | 151,713 | -78,287 | 43% | +0.0% / +0.0% / +0.0% | -0.3% |
| H2 | 2.22 | 4.51 | 3.37 | -81,089 | -79,185 | 217,425 | -82,524 | 44% | +0.0% / +0.0% / +0.0% | -3.8% |
| all | 1.84 | 3.60 | 9.72 | -79,908 | -78,610 | 272,984 | -83,609 | 43% | -0.9% / -1.3% / +2.5% | -1.2% |

## Difference from C1-F2 (allocation tilt: NO)
C1-F2 tilted an always-on 80/20 blend by +-25/50% using trailing inverse-vol / correlation / Sharpe statistics of both streams, so the sleeve was always present and inherited the static blend's +0.19..+0.50 uplift (F2's tilt then added nothing over it). B8 is a binary on/off on one statistic, the sign of the pair's own trailing P&L, so the exposure to the sleeve is cut to 17%/9% of weeks and the static blend's uplift disappears with it. Same family of conclusion (trailing P&L statistics have no predictive power for the relative contribution), different cell: F2's tilt could not lose the blend; the switch does, and is significantly worse than the static blend. Equal-exposure static (share x on-fraction) uplift for N=8 is +0.04/+0.10/+0.06, i.e. the switch picks weeks no better than random ones. The hedge benefit that exists is in the always-on blend (V5 P1 lead, known failing plateau and 2013-2022).

## WT version
Skipped: outputs/autopilot/REPORT_WT.md does not exist after the main work.

Files: code/census/night_ins/ap_b8_run.py, ap_b8_rep.py, ap_b8_doc.py; outputs/autopilot/b8/{b8_stage1,b8_stage2,b8_diag}.pkl.

DONE B8
