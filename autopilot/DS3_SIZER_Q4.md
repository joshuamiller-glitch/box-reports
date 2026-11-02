# DS3_SIZER_Q4 - ER at the add, ER freshness / boundary fragility, smooth ladder (ZL-2, 2026-11-02T22:12Z; analysis only, the user decides)
Prereg SIZER_Q4_PREREG.md sha256 94ad2e23f66f1b844d456dc86d3c8bd0ce17ad091e6df65c73130ee11c250fdb (DECISIONS.md, before any Q4 statistic). Frame: T-SIZER ts base (V13T_LIVE costs, sequential rounding, lock R scaled only when mult > 1, A06 not modelled, zone half before ER); reference L = live ladder; ER(20) on 5-minute closes from S4b's bar builder (recomputed here, 100% exact match with feat_signal on all rows).

**HEADLINE.** (1) ER at the add: re-evaluating ER at the add-fill second cancels the add on 28183 of 46261 filled adds (61%; ER at the add is below .30 for most signals that were already below .30) and halves only 316; as a rule ADDER (cancel if ER_add < .30, halve if ER fell > 0.1) cuts L6M maxDD 31.8% (8.5% with W29-W39 dropped) but PRE -5.1%, at mean -0.5k (L6M) / -2.1k (PRE) per week (MDE 6.2k / 2.8k): it is NOT flagged (PRE gets worse). Against random cancellations of the same count the ER-at-add choice keeps more dollars (placebo mean rank 0.98 L6M, 0.87 PRE) but cuts less drawdown (cut rank 0.16 / 0.07). (2) Freshness: the engine feature uses closed bars only, no look-ahead (100/100 audit rows match the closed-bar ER exactly; 1/100 match ER with the forming bar, 0/100 one bar earlier; the bar used ends at or before the signal second on all 88,490 rows). The 0.30 boundary is moderately fragile: 7.6% of taken signals lie within +-0.02 of .30 (a +-0.02 uniform noise flips 25.9% of them across the line), 13.4% change side if the forming bar is included and 14.7% if the ER is one bar older. (3) The cliff is not costly: the smooth linear ladder changes little (L6M cut +4.1% / +7.0% dropped, PRE -6.0%, mean +1.1k / -1.0k), and forcing the whole +-0.03 band to x0.5 or to x1.5 moves the mean -3.1k / +6.6k per week in L6M with drawdown cuts +2.8% / -15.2%. No cell passes the flag test except the trivial ADDER_h (316 rows). The user decides.

## 1. The cells vs the live ladder (phase 0; ts base is phase-invariant)
| cell | definition | mean lots | L6M cut (dropped) | HOLD | MID | PRE | X' | d mean L6M (MDE) | d mean PRE (MDE) | mean in tolerance | FLAG |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ADDER | add only if ER at the add >= .30 (else cancelled); add x0.5 if ER_add < ER_signal - 0.1; else x1 | 3.22 | +31.8% (+8.5%) | +31.8% | +36.2% | -5.1% | -11.2% | -0.5k (6.2k) | -2.1k (2.8k) | True |  |
| ADDER_c | cancel the add if ER at the add < .30 | 3.22 | +12.4% (+13.7%) | +12.4% | +56.3% | -5.1% | +5.9% | -0.2k (3.6k) | -1.9k (2.2k) | True |  |
| ADDER_h | halve the add if ER dropped > 0.1 since the signal | 3.22 | -0.8% (+0.4%) | -0.8% | +6.9% | +2.2% | +6.9% | -0.1k (0.7k) | -0.5k (0.8k) | True | FLAG |
| SMOOTH | linear 0.5..1.5 between ER .25 and .35 (x1.0 at .30) | 3.18 | +4.1% (+7.0%) | +4.1% | +7.3% | -6.0% | -2.0% | +1.1k (4.5k) | -1.0k (1.9k) | True |  |
| BND_LO | signals with ER in [.27,.33] all at x0.5 (others as ladder) | 3.05 | +2.8% (-5.0%) | +2.8% | +15.5% | +2.3% | -16.5% | -3.1k (5.1k) | -1.4k (3.1k) | True |  |
| BND_HI | signals with ER in [.27,.33] all at x1.5 | 3.41 | -15.2% (-14.9%) | -15.2% | -7.5% | +4.1% | -19.3% | +6.6k (9.9k) | +0.6k (3.1k) | True |  |

## 2. Equal-risk (exact lot scan lscale 0.80-1.60, W29-W39 dropped in L6M/HOLD): mean of the cell at the ladder's maxDD (engine points within +-7.5% of the ladder's maxDD at lscale 1; n)
| cell | L6M-dropped: ladder / cell (n) | PRE: ladder / cell (n) | HOLD-dropped (n) |
|--|--|--|--|
| ADDER | 64.6k / 59.6k (2) | 16.4k / 15.2k (3) | 39.7k / 56.8k (6) |
| ADDER_c | 64.6k / 60.6k (3) | 16.4k / 15.1k (3) | 39.7k / 57.1k (6) |
| ADDER_h | 64.6k / 58.4k (6) | 16.4k / 17.1k (4) | 39.7k / 39.3k (1) |
| SMOOTH | 64.6k / 65.4k (4) | 16.4k / 16.1k (3) | 39.7k / 41.3k (1) |
| BND_LO | 64.6k / 51.6k (3) | 16.4k / 17.1k (6) | 39.7k / 38.2k (1) |
| BND_HI | 64.6k / 66.9k (5) | 16.4k / 17.9k (4) | 39.7k / 44.9k (3) |

## 3. Placebos (100 draws; ADDER family: the (add_mult, add_only_if) pair permuted within book x session over rows with an add fill; SMOOTH: multipliers permuted within book x session; rank = share of draws below the real cell)
| cell | real L6M cut / d mean | PRE cut / d mean | rank cut L6M | rank mean L6M | rank cut PRE | rank mean PRE | draw medians (L6M cut, d mean, PRE cut, d mean) |
|--|--|--|--|--|--|--|--|
| ADDER | +31.8% / -0.5k | -5.1% / -2.1k | 0.16 | 0.98 | 0.07 | 0.87 | 44.6 / -5.0 / 9.8 / -3.2 |
| ADDER_c | +12.4% / -0.2k | -5.1% / -1.9k | 0.02 | 0.99 | 0.08 | 0.93 | 44.3 / -5.0 / 9.2 / -3.2 |
| ADDER_h | -0.8% / -0.1k | +2.2% / -0.5k | 0.16 | 0.55 | 0.78 | 0.13 | 2.2 / -0.2 / 1.2 / -0.2 |
| SMOOTH | real vs L: see section 1 | | 0.08 | 0.96 | 0.12 | 0.78 | (multiplier placebo, kind perm) |

## 4. Exposure (engine run of each cell)
| cell | mean lots | max lots | worst net signed lots (day) | worst stack risk $ (day) |
|--|--|--|--|--|
| L | 3.01 | 11 | 28 (20240220) | 33,600 (20230623) |
| ADDER | 3.13 | 11 | 28 (20240220) | 33,600 (20230623) |
| ADDER_c | 2.98 | 11 | 28 (20240220) | 33,600 (20230623) |
| ADDER_h | 3.01 | 11 | 28 (20240220) | 33,600 (20230623) |
| SMOOTH | 2.96 | 11 | 28 (20240401) | 33,600 (20230623) |
| BND_LO | 2.84 | 11 | 28 (20240220) | 33,600 (20230623) |
| BND_HI | 3.20 | 11 | 28 (20240220) | 37,200 (20230829) |

## 5. ER freshness and the .30 boundary
100-row audit (seeded random taken rows): exact match with the closed-bar ER 100/100 (max diff 2.8e-08), with the forming-bar ER 1/100 (mean abs diff 0.060), with the one-bar-earlier ER 0/100 (mean abs diff 0.072). Leak check on all 88,490 signals: bars used with an end second after the signal second: 0 (min age of the bar 0 s; max 263040 s after weekends / gaps, where the last closed bar is stale by construction). Note: the last closed bar can be minutes old at the start of a session (stale ER at the first signals after a gap); not a look-ahead.

| group | n | within +-0.02 of .30 | within +-0.03 | flip share under uniform +-0.02 noise (of all) | side differs forming vs closed | side differs one bar older vs closed | corr(ER forming, ER) | corr(ER lag, ER) |
|--|--|--|--|--|--|--|--|--|
| all signals | 88490 | 7.7% | 11.7% | 1.91% | 13.2% | 14.3% | 0.889 | 0.871 |
| taken signals | 17396 | 7.6% | 11.6% | 1.97% | 13.4% | 14.7% | 0.877 | 0.863 |

## 6. Boundary trades (ER in [.27,.33]): net $ per trade at lots x1 (sizer-off table) and the effect of the whole band at x0.5 vs x1.5
| window | below .30 (.27-.30): n / $ per trade | above .30 (.30-.33): n / $ per trade | BND_HI minus BND_LO: total $k in window | weekly maxDD of that difference series $k |
|--|--|--|--|--|
| L6M | 223 / +223 | 183 / +413 | +263.1 | 48.7 |
| HOLD | 422 / +226 | 350 / +254 | +285.3 | 55.2 |
| PRE | 388 / +119 | 380 / +259 | +146.8 | 73.0 |
| X' | 164 / +218 | 156 / -117 | +36.2 | 63.0 |
| ALL | 1058 / +151 | 962 / +247 | +507.1 | nan |

Reading: the boundary band carries about 12% of all taken signals (2,020). Boundary trades are profitable on both sides of .30 at equal lots (ALL +151 vs +247 $/trade below vs above; L6M +223 vs +413; PRE +119 vs +259; X' +218 vs -117), above .30 earning roughly 1.6x more, so the cliff itself is not costly: moving the whole band between x0.5 and x1.5 is worth +507k over the history in total but that is a lot-size effect, not a threshold effect; the smooth linear ladder (x1.0 at .30) is neutral at equal risk (exact scan: L6M-dropped 65.4k vs ladder 64.6k, PRE 16.1k vs 16.4k, placebo ranks in section 3). The ER-at-the-add rule cancels 61% of all filled adds (most signals that start below .30 also have ER below .30 at the add), keeps more dollars than random cancellations of the same count (mean rank 0.98 L6M) but gives no consistent drawdown benefit (PRE -5.1%).

