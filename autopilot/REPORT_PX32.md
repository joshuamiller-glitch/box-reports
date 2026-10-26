# REPORT PX32 - PSAR 15-min pullback: neighbourhood-ensemble cure

**Verdict: NO. The cure fails: the equal-weight 81-cell neighbourhood ensemble E81 has additive 20% uplift +0.15 / -0.14 / -0.02 (clean / H1 / H2; all-in +0.07, vs the parent single cell +0.26 / +0.11 / +0.08), plateau 5 of 12 neighbour ensembles, 2x-slippage H1/H2 -0.18/-0.05, replication 0 of 3 available legs (H0 -0.11, ES -0.19, RTY -0.17, alternating-month post-clean odd -0.17 / even +0.07). The majority-vote book V9 is no better (+0.23 / -0.16 / -0.12). The parent's edge is a point at the default PSAR (0.02, 0.2): moving the acceleration factors +-25% alone removes it. FOUND 0, LEAD 0 (the parent weak LEAD is downgraded to NO).** Runtime about 15 min on 4 workers. Code: code/census/night_ins/ap_pd3_core.py, ap_pd3_main.py, ap_pd3_selnull.py, ap_pd3_era.py; data/pickles: outputs/autopilot/pd3/. Pre-registration: PREREG_AUTOPILOT.md section 'PX32' (written before the first ensemble cell was run; the single-cell run reproduced the parent exactly: 938 trades, +0.255/+0.111/+0.083).

## 1. What was registered and run
- Books (no selection, fixed up front): **E81** = equal-weight mean of 81 daily P&L vectors, NQ 15-min PSAR pullback, AF (step,max) x{0.75,1,1.25} jointly, trigger TCB band {0.1875,0.25,0.3125}, stop SLV {0.375,0.5,0.625}, target R {1.125,1.5,1.875}, TR_E50, RTH, flat 16:55. **E27** = same at the default AF (pipeline-comparable form). **V9** = majority vote (>=5 of 9 AF x band signals) with centre stop 0.5 / R 1.5. Scaled so clean weekly sigma = pair's; additive P+sS and constant-risk (1-s)P+sS at 10/20/30/50%, headline 20%.
- Fill model: market entry at next 1-min open, 1 tick/side + $4.36/contract commission, 2x for the slippage gate; margin: about 16.7-28 NQ-contract-equivalents per 100% share (sleeve scale factors 28.1 for E81, 24.1 for V9); about 944 trades per cell in the pair window (E81 mean), 756 for V9.
- Baseline: B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (t3_score first). Pair weekly Sharpe clean/H1/H2 1.46/2.83/2.30.

## 2. Spans: honest virginity statement
Clean 2023-08..2025-07 was the parent's selection span. H1 and H2 were read once by the parent for the single cell, so for E81 they are NON-VIRGIN (an ensemble cannot be called blind to them). H0 2023-02..07, ES, RTY and the 2013-22 ERA were read descriptively by the parent for the single cell (weak/negative). Newest live weeks: data and pair end 2026-10-13 = end of H2, so replication leg 1 is NOT AVAILABLE; E81 is logged for the FORWARD protocol. Result: even with non-virgin H1/H2 inflating the ensemble's chances, it fails.

## 3. Gate checklist for E81 (additive 20% unless stated)
| gate | result | pass |
|---|---|---|
| 1 uplift >= +0.10 on clean/H1/H2, worst-week change <= +20% | +0.15 / -0.14 / -0.02; worst week +20.4% | FAIL |
| 2a own timing-destroyed null (300 common-random-entry ensembles) | standalone all-in Sharpe 0.78 vs p95 0.65 (rank 96.7%) | pass |
| 2b bootstrap 90% CI of additive uplift > 0 | [-0.12, +0.26] | FAIL |
| circular-shift null (reported) | p95 0.17 vs all-in uplift +0.07 | not passed |
| 3 selection-corrected null (pipeline re-run in 30 random-level worlds, section 5) | real PSAR E27 min-uplift +0.052 vs null best-of-12 p95 0.190 (rank 40%) | FAIL |
| 4 plateau (12 neighbour ensembles, keep >= 75% of +0.065 all-in uplift) | 5 of 12 = 42% (need 9) | FAIL |
| 5 2x slippage | +0.11 / -0.18 / -0.05 (standalone all-in 0.61) | FAIL |
| 6 worst-decile-week corr with pair | -0.55 (17 weeks; sleeve mean -$11.1k in the pair's worst weeks) | pass |
| 7 NT8 spec + margin | not reached; 81 virtual cells would need a custom aggregated order engine | n/a |
| Replication (>= 2 of 3 legs, same sign, >= 50% of uplift) | H0 -0.11; ES -0.19 / RTY -0.17; alt-month post odd -0.17, even +0.07 -> 0 of 3 (leg 1 unavailable) | FAIL |

Plateau detail (all-in uplift of each neighbour ensemble; keeps if >= +0.049): spread x0.75 +0.06 yes; spread x1.25 -0.02; joint centre x0.75 -0.08; joint x1.25 +0.06 yes; AF x0.75 +0.02; AF x1.25 -0.01; trigger x0.75 +0.03; trigger x1.25 +0.10 yes; stop x0.75 +0.02; stop x1.25 +0.07 yes; target x0.75 +0.01; target x1.25 +0.08 yes.

Uplift table (E81; clean / H1 / H2 / all-in):
| framing | share | clean | H1 | H2 | all | worst-week chg % | verdict |
|---|---|---|---|---|---|---|---|
| add | 10 | +0.08 | -0.05 | 0.00 | +0.04 | +7.1 | NO |
| add | 20 | +0.15 | -0.14 | -0.02 | +0.07 | +20.4 | NO |
| add | 30 | +0.19 | -0.26 | -0.07 | +0.07 | +33.8 | NO |
| add | 50 | +0.25 | -0.53 | -0.21 | +0.04 | +60.6 | NO |
| const | 10 | +0.09 | -0.06 | 0.00 | +0.05 | -2.3 | NO |
| const | 20 | +0.17 | -0.20 | -0.04 | +0.07 | +1.7 | NO |
| const | 30 | +0.23 | -0.43 | -0.16 | +0.05 | +5.7 | NO |
| const | 50 | +0.25 | -1.15 | -0.59 | -0.14 | +13.8 | NO |

Comparators (additive 20%, clean/H1/H2/all): parent single cell +0.26/+0.11/+0.08/+0.20; E27 (default AF, 27 cells) +0.22/+0.05/+0.12/+0.17 (fails gate 1 on H1; ww +15.6%; boot CI [0.00, +0.35]; E27 plateau and slippage not run since it is not the registered primary); V9 +0.23/-0.16/-0.12/+0.09 (ww +19.3%).

Standalone 1-contract-equivalent weekly Sharpe (clean/H1/H2/all): E81 1.17 / -0.07 / 0.42 / 0.78; E27 1.50 / 0.80 / 0.88 / 1.25; V9 1.30 / -0.53 / 0.06 / 0.72; parent 1.64 / 1.19 / 0.78 / 1.41.

## 4. Insurance metrics, E81 vs pair (USD)
| span | book | Sharpe | Sortino | MAR | maxDD | worst week | CVaR5 | CVaR10 |
|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | 280,110 | -81,874 | -78,736 | -78,009 |
| clean | add 20% | 1.61 | 3.13 | 6.11 | 252,526 | -99,399 | -87,484 | -82,987 |
| clean | const 20% | 1.63 | 3.20 | 6.21 | 205,674 | -83,937 | -71,926 | -67,401 |
| H1 | pair | 2.83 | 6.09 | 3.91 | 151,713 | -78,287 | -77,610 | -66,030 |
| H1 | add 20% | 2.68 | 5.29 | 3.75 | 157,397 | -88,951 | -86,193 | -74,817 |
| H1 | const 20% | 2.63 | 5.10 | 3.71 | 127,054 | -73,564 | -70,671 | -61,678 |
| H2 | pair | 2.30 | 4.69 | 3.50 | 217,425 | -82,524 | -81,089 | -79,185 |
| H2 | add 20% | 2.27 | 4.71 | 3.20 | 248,451 | -97,537 | -97,088 | -83,104 |
| H2 | const 20% | 2.25 | 4.64 | 3.13 | 204,966 | -82,054 | -81,381 | -68,656 |
| all-in | pair | 1.86 | 3.63 | 9.59 | 280,110 | -82,524 | -79,220 | -78,243 |
| all-in | add 20% | 1.92 | 3.79 | 11.6 | 252,526 | -99,399 | -90,273 | -83,869 |
| all-in | const 20% | 1.92 | 3.80 | 11.63 | 205,674 | -83,937 | -74,726 | -68,294 |
Constant-risk framing: verdict NO at every share (no INSURANCE: the all-in worst-week and CVaR5 do not improve >= 20% and H1/H2 Sharpe falls). Additive: worst week deteriorates (-99k vs -83k all-in).

## 5. Selection-corrected null (full pipeline on replicates)
Pipeline: stage-1 grid (3,280 cells), top-12 distinct (bar, level, trigger) finalists by clean Sharpe (n >= 150), each expanded to its +-25% trigger x stop x target neighbourhood (E27 form, up to 27 cells), statistic = best finalist's min(clean, H1, H2) additive-20% uplift. Re-run in the parent's 30 random-level null worlds (360 finalist ensembles): null best-of-12 mean +0.039, p95 +0.190, max +0.203; 7 of 30 worlds (23%) contain at least one finalist ensemble that passes gate 1, 7 of 360 (1.9%) finalist ensembles. Real: best of the 12 real finalists' ensembles = PSAR E27 at +0.052 (rank 40% against the null worlds); 0 of 12 pass gate 1. The real pipeline is no better than random levels. Caveat: top-12 of stage 1 only (stage-2 expansion not replicated), non-PSAR finalists expanded on the scalable parameters only.

## 6. ERA flag (not gating): NQ 2013-2026, cost decomposition per trade (mean over cells)
| book | period | trades/cell | gross $ | net fixed-cost $ | net price-scaled $ |
|---|---|---|---|---|---|
| E81 | 2013-2022 | 2,842 | +0.6 | -13.7 | -4.2 |
| E81 | 2023-2026 | 1,109 | +60.8 | +46.4 | +47.4 |
| E27 | 2013-2022 | 2,834 | -7.8 | -22.1 | -12.6 |
| E27 | 2023-2026 | 1,112 | +108.7 | +94.3 | +95.3 |
| parent | 2013-2022 | 2,829 | -6.1 | -20.5 | -11.0 |
| parent | 2023-2026 | 1,109 | +145.7 | +131.3 | +132.3 |
Ensemble weekly Sharpe 2013-22 at fixed cost / price-scaled cost: E81 -0.52 / -0.16; E27 -0.70 / -0.40; parent -0.58 / -0.31. ERA FLAG: E81 'gross-positive (+$0.6/trade, i.e. zero), cost-negative pre-2023'; E27 and parent 'negative pre-2023'. Mechanism in one sentence: in the trending 2023-26 tape a first dip to the 15-min SAR inside RTH continued; it depends on current structure and on the exact default PSAR constants.

## 7. Diagnostics
Odd/even months, clean (in-sample for the parent selection): E81 +0.12 / +0.19; post-clean (2025-08..2026-10) odd -0.17 / even +0.07, pooled -0.07. H0 window: E81 uplift -0.11 (standalone weekly Sharpe -0.87). ES standalone all-in -0.65 (clean +0.23), RTY -0.74. V9: plateau 1 of 4 (thr4 +0.18 keeps, others no), 2x slippage +0.20/-0.19/-0.14, null p95 0.59 vs 0.72 (pass), ES -0.11 / RTY -0.17, H0 +0.09, selection-corrected null not run (V9 already fails gate 1).

## 8. Reading
(i) The parent plateau failure was not an accident of two bad neighbours: averaging the neighbourhood moves the all-in uplift from +0.20 to +0.07 and flips H1/H2 negative; the dependence on the PSAR AF constants is the dominant sensitivity (AF x1.25 alone: all-in -0.01). (ii) The parent's H1/H2 strength (+0.11/+0.08) was a point estimate at the default constants; averaged cells have standalone H1 -0.07. (iii) The selection-corrected null shows the pipeline manufactures ensembles of this size by chance in 23% of null worlds. No ensemble is carried forward; E81/E27/V9 saved to the library (outputs/library, family PX32, tag ensemble, verdict NO) for portfolio assembly only. Chance-pass accounting: 2 ensembles tested; per-ensemble chance of passing gate 1 from null worlds about 2% (7/360), expected false passes 0.04; observed 0.

DONE PX32
