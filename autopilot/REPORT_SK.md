# REPORT SK - STRESS TEST OF THE K4 FAMILY (seeds, selection-aware family null, model classes, feature ablation, permuted-VIX null, trade level)

**Verdict: the K4 signal survives every stress test that could break it but remains ONE sample-limited, VIX-dependent, tree-model lead (status stays FOUND-PENDING-REPLICATION; nothing is promoted).** (1) Seeds: across 1,000 LightGBM seeds the 20%-share uplift is +0.21 / +0.28 / +0.28 / +0.23 (clean/H1/H2/all-in, sd 0.04/0.14/0.09/0.04); 90% of seeds clear +0.10 on all three spans and 98% keep 75% of the seed-0 all-in uplift: the 'seed-dependent plateau' was mostly the cell's own parameter edge (delta 0.10), not the seed. (2) Family selection-aware null (1,000 worlds, K4v2/RW12P/RX5/RW5 as one family, long-only and K4v2-convention nulls): no null world reaches any sleeve's real uplift (family-wise p < 0.001, rank > 0.999); the weakest member is the RW5 pair modulator (marginal p 0.023 on the worst-span uplift, 0.009 all-in) and RW5's headline clean uplift is NOT seed-robust (seed-mean clean +0.06 vs +0.25 for seed 0; only 30% of 200 seeds clear +0.10 on all three spans). (3) Model classes: tree ensembles reproduce the sign and rough size (random forest with a frequency-matched rule: all-in +0.20, extra-trees +0.16, weaker clean span), linear models (logit, ridge) do NOT; it is not LightGBM-specific but it is tree-specific. (4) The VIX block carries it and the real VIX dates matter: with the VIX series rolled by 6-60 months the median uplift collapses to +0.05/+0.19/-0.00/+0.05. (5) Trade level: 267 pair-window trades, 13.8% of days with a position, top 5% of position days = 67% of net P&L.

## Set-up
- Reuses the frozen K4 code (ap_k_fams features, quarterly purged walk-forward from 2016, pooled ES/NQ/RTY/YM, p >= 0.58 long-only, 16:16 ET entry/exit, 1-day hold, 1 ADR-dollar risk per signal) through ap_sk_lib.py, which reproduces ap_k_fams.ml_preds bit-for-bit and the K4v2 cell (+0.183/+0.392/+0.197/+0.203, 267 trades). Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) series of t3_score in a clean process (RW5 part asserts 1.46/2.83). Fill model: last 1-min close at/before 16:16 ET, 1 tick/side + $4.36 per contract round trip. Pre-registered in PREREG_AUTOPILOT.md block 'SK' before any SK run. 12 processes, disk < 1 GB. No new selection: every number below is a property of cells already carried by the K4 family.
- Additive 20% share unless stated; uplift = change in the pair's weekly Sharpe; the scale is recomputed per seed (sleeve scaled to the pair's clean weekly sd).

## 1. Seed stability (1,000 LightGBM random_state values; seed 0 = K4v2)
|       |    mean |    std |      5% |     50% |     95% |     min |     max |
|:------|--------:|-------:|--------:|--------:|--------:|--------:|--------:|
| clean |   0.215 |  0.043 |   0.146 |   0.214 |   0.284 |   0.066 |   0.355 |
| H1    |   0.276 |  0.142 |   0.074 |   0.256 |   0.54  |  -0.142 |   1.032 |
| H2    |   0.275 |  0.089 |   0.136 |   0.269 |   0.432 |   0.046 |   0.625 |
| all   |   0.228 |  0.041 |   0.168 |   0.226 |   0.301 |   0.106 |   0.398 |
| sa    |   1.517 |  0.199 |   1.206 |   1.512 |   1.863 |   0.827 |   2.109 |
| ntr   | 253.78  | 18.511 | 223.95  | 254     | 283     | 202     | 309     |

- Fraction of seeds with uplift >= +0.10 on clean AND H1 AND H2: **90.0%** (clean alone 99.3%, H1 alone 91.8%, H2 alone 98.8%). All-in uplift > 0 in 100.0%; >= 75% of seed 0 (+0.152) in 98.5% (seed plateau P1). Seed 0 sits at the 29% percentile of the all-in distribution (a slightly below-median draw: the headline K4v2 number is NOT a lucky seed). Pre-registered criteria (P(all three) >= 0.75 and P1 >= 0.75): MET.

Parameter x seed plateau (exact +-25% neighbours):
| configuration (100 seeds each)   |   clean (seed median) |    H1 |    H2 |   all-in |   share of seeds with all three >= +0.10 |
|:---------------------------------|----------------------:|------:|------:|---------:|-----------------------------------------:|
| base (seeds 0-99)                |                 0.214 | 0.249 | 0.271 |    0.223 |                                     0.87 |
| trees 112                        |                 0.181 | 0.224 | 0.303 |    0.205 |                                     0.79 |
| trees 188                        |                 0.222 | 0.338 | 0.239 |    0.235 |                                     0.96 |
| lr 0.0375                        |                 0.19  | 0.224 | 0.306 |    0.215 |                                     0.82 |
| lr 0.0625                        |                 0.224 | 0.334 | 0.23  |    0.238 |                                     0.95 |
| delta 0.06                       |                 0.184 | 0.617 | 0.232 |    0.24  |                                     0.93 |
| delta 0.1                        |                 0.149 | 0.081 | 0.209 |    0.15  |                                     0.28 |

Seed-median all-in uplift >= 75% of the base configuration's seed-median in 5 of 6 neighbours (criterion >= 5): **MET**. The one failing neighbour is delta 0.10 (fewer, higher-conviction signals; H1 uplift collapses to +0.08).

Seed ensembles (mean probability, RX5 analogue): 5 seeds (200 disjoint groups) all-in +0.205 (sd 0.025), clean +0.210, H1 +0.170, H2 +0.253, 96% with all three >= +0.10; 25 seeds (40 groups) all-in +0.184 (sd 0.014), clean +0.191, H1 +0.131, H2 +0.241, 100% with all three >= +0.10. Averaging seeds lowers variance (sd 0.04 -> 0.025 -> 0.014) and trades the high-H1 tail for a steadier +0.13-0.24.

## 2. Selection-aware family null (1,000 worlds, month-stratified, family = K4v2 + RW12P + RX5 + RW5)
| null convention                    | member   |   real W=min(clean,H1,H2) uplift |   null p (W) |   real all-in uplift |   null p (all-in) |   null p (standalone Sharpe) |
|:-----------------------------------|:---------|---------------------------------:|-------------:|---------------------:|------------------:|-----------------------------:|
| random side by p (K4v2 convention) | K4V2     |                            0.183 |        0     |                0.203 |             0     |                            0 |
| random side by p (K4v2 convention) | RW12P    |                            0.265 |        0     |                0.337 |             0.001 |                            0 |
| random side by p (K4v2 convention) | RX5      |                            0.202 |        0     |                0.27  |             0     |                            0 |
| random side by p (K4v2 convention) | RW5      |                            0.253 |        0.023 |                0.467 |             0.009 |                          nan |
| long-only random entries           | K4V2     |                            0.183 |        0     |                0.203 |             0     |                            0 |
| long-only random entries           | RW12P    |                            0.265 |        0     |                0.337 |             0     |                            0 |
| long-only random entries           | RX5      |                            0.202 |        0     |                0.27  |             0     |                            0 |
| long-only random entries           | RW5      |                            0.253 |        0.023 |                0.467 |             0.009 |                          nan |

- Family-wise (Westfall-Young min-p over the four members, independent draws per member = conservative), random side by p: observed min marginal p 0.000 on W and 0.000 on all-in uplift; fraction of null worlds with a min-p at least that small: **0.000 (W), 0.000 (all-in)**; 95th percentile of best-of-three sleeve W in the null +0.083, of best-of-three all-in +0.148 (real best W +0.265, real best all-in +0.337).

- Family-wise (Westfall-Young min-p over the four members, independent draws per member = conservative), long-only: observed min marginal p 0.000 on W and 0.000 on all-in uplift; fraction of null worlds with a min-p at least that small: **0.000 (W), 0.000 (all-in)**; 95th percentile of best-of-three sleeve W in the null +0.057, of best-of-three all-in +0.117 (real best W +0.265, real best all-in +0.337).

Final rank statement: the three sleeves beat a month-stratified random-entry family in all 1,000 worlds (marginal p = 0.000) and the RW5 pair modulator in 97.7% (W) / 99.1% (all-in) of its permutation worlds (largest marginal p over members: W 0.023, all-in 0.009), and after the best-of-four correction no world has a best member as extreme as the real one: family-wise p < 0.001 on both W and all-in (0 of 1,000 worlds; rank > 0.999) in the conservative independent-draw construction and in the long-only drift-matched convention alike. Caveats: (i) this is a null of random timing, it does not test the 145 hand-picked variants (RY7: effective independent trials about 3.9) or look-ahead in the cell choice; (ii) RW5's null permutes the probability series within calendar months (pair-side), the sleeves' nulls draw random entries with the real monthly counts; (iii) drift: long-only random entries earn the market drift minus costs, so the long-only convention is the drift-matched one.

RW5 (pair modulator) seed stability, seeds 0-199: all-in uplift +0.277 (sd 0.071), clean +0.055, H1 +0.982, H2 +0.388; 30% of seeds with all three >= +0.10 (real seed 0: +0.253/+1.062/+0.629/+0.467).

## 3. Alternative model classes (same features, purge, quarterly walk-forward)
| model   | rule                                              |   n runs |   median pair-window trades |   clean |      H1 |      H2 |   all-in |   share all three >= +0.10 |
|:--------|:--------------------------------------------------|---------:|----------------------------:|--------:|--------:|--------:|---------:|---------------------------:|
| logit   | p>=0.58                                           |        1 |                       486   |   0.024 |   0.284 |   0.006 |    0.042 |                       0    |
| logit   | freq-matched 21.2% of all 2016-26 days            |        1 |                       713   |  -0.012 |   0.539 |   0.107 |    0.067 |                       0    |
| ridge   | p>=0.58                                           |        1 |                       470   |   0.024 |   0.286 |   0.007 |    0.043 |                       0    |
| ridge   | freq-matched 21.2% of all 2016-26 days            |        1 |                       717   |   0.006 |   0.559 |   0.115 |    0.083 |                       0    |
| rf      | p>=0.58                                           |       20 |                        17.5 |   0.107 |   0     |   0.044 |    0.065 |                       0    |
| rf      | freq-matched 21.2% of all 2016-26 days            |       20 |                       743.5 |   0.097 |   0.811 |   0.367 |    0.224 |                       0.45 |
| et      | p>=0.58                                           |       20 |                         0   | nan     | nan     | nan     |  nan     |                     nan    |
| et      | freq-matched 21.2% of all 2016-26 days            |       20 |                       739.5 |  -0.039 |   0.492 |   0.11  |    0.054 |                       0    |
| gbm     | freq-matched 8.3% (pair-window frequency of K4v2) |       20 |                       346.5 |   0.215 |   0.235 |   0.229 |    0.205 |                       0.9  |
| logit   | freq-matched 8.3% (pair-window frequency of K4v2) |        1 |                       309   |  -0.018 |   0.501 |   0.092 |    0.06  |                       0    |
| ridge   | freq-matched 8.3% (pair-window frequency of K4v2) |        1 |                       318   |  -0.014 |   0.538 |   0.089 |    0.064 |                       0    |
| rf      | freq-matched 8.3% (pair-window frequency of K4v2) |       20 |                       327.5 |   0.114 |   0.781 |   0.228 |    0.202 |                       0.6  |
| et      | freq-matched 8.3% (pair-window frequency of K4v2) |       20 |                       367   |   0.097 |   0.443 |   0.221 |    0.16  |                       0.4  |

The rule (c) frequency-matched at the pair-window frequency was added after seeing rules (a) and (b) (disclosed: rule (b) matched the frequency over all 2016-26 days, which is 2.5x higher than K4v2's frequency inside the pair window). Rule (a) is not usable for linear models and extra-trees (probabilities never reach 0.58: 0 trades for extra-trees, about 480 for the linear models whose p barely moves). Reading: **the signal is not LightGBM-specific**: with the frequency-matched rule a random forest reproduces the sign and about the size on all-in (and H1/H2, with a weaker clean span), extra-trees reproduce it with lower hit-rate; **logistic and ridge do not** (clean about 0, all-in +0.06). So the information is a non-linear interaction available to tree ensembles (consistent with RW3), not an artefact of one library or seed.

## 4. Feature ablation and the permuted-VIX null
| feature set (200 seeds each)                 |   clean (median) |    H1 |     H2 |   all-in |   all-in 5% |   all-in 95% |   share all three >= +0.10 |
|:---------------------------------------------|-----------------:|------:|-------:|---------:|------------:|-------------:|---------------------------:|
| PRICE                                        |            0.143 | 0.266 | -0.051 |    0.104 |       0.046 |        0.157 |                      0.02  |
| VIX                                          |            0.182 | 0.239 |  0.155 |    0.187 |       0.111 |        0.292 |                      0.425 |
| VIX+iid                                      |            0.176 | 0.296 |  0.154 |    0.189 |       0.118 |        0.291 |                      0.645 |
| PRICE+VIX                                    |            0.221 | 0.207 |  0.125 |    0.189 |       0.137 |        0.244 |                      0.48  |
| FULL-VIX                                     |            0.098 | 0.154 | -0.046 |    0.065 |       0.007 |        0.118 |                      0     |
| FULL(set order)                              |            0.211 | 0.281 |  0.265 |    0.227 |       0.165 |        0.299 |                      0.915 |
| FULL(K4 order)                               |            0.214 | 0.264 |  0.266 |    0.225 |       0.155 |        0.306 |                      0.895 |
| FULL with VIX rolled 6-60 months (500 perms) |            0.051 | 0.194 | -0.001 |    0.048 |      -0.079 |        0.207 |                      0.076 |

- Permuted-VIX null: real-VIX seed-median all-in uplift +0.226; 3.4% of the 500 permuted-VIX runs reach it (clean 4.4%; worst-span 0.8%); only 7.6% of permuted runs clear +0.10 on all three spans (real VIX: 90%). Rolling the VIX series keeps its distribution and persistence but destroys the date alignment, so the information is in WHEN the VIX state occurred, not in having VIX-like features.
- Ablation: the VIX block alone (4 features, no price, no calendar, no COT) delivers most of the effect (all-in about +0.19), price alone is weaker and fails H2 (about -0.05), FULL minus VIX is weak (+0.07 all-in, H2 negative), PRICE+VIX is close to FULL on all-in but weaker in H2/H1 stability; COT and calendar add little to the average uplift (RW2) but the full feature set is clearly more STABLE than PRICE+VIX or VIX alone (90% of FULL seeds clear +0.10 on all three spans vs 48% for PRICE+VIX and 43% for VIX alone). The 'edge' is therefore: trees conditioning daily index direction on the VIX state (level percentile, term structure, VVIX, 5-day change) - a market-timing signal on a rising sample (always-long equal-risk basket Sharpe 0.65), which is why the beta and equal-exposure tests (RW1: CI of the Sharpe difference includes 0) remain the limiting evidence.

## 5. Trade-level view

### K4v2 seed 0
- Signals per year (entries; 2016-2022 are walk-forward out-of-sample ERA, 2023-26 the pair window):
|      |   ES |   NQ |   RTY |   YM |   all |
|-----:|-----:|-----:|------:|-----:|------:|
| 2016 |   63 |   65 |     0 |   65 |   193 |
| 2017 |   66 |   90 |    70 |   63 |   289 |
| 2018 |   88 |   55 |    85 |  102 |   330 |
| 2019 |   53 |   55 |    35 |   55 |   198 |
| 2020 |  100 |  102 |    78 |   87 |   367 |
| 2021 |   49 |   78 |   104 |   68 |   299 |
| 2022 |   73 |   62 |    68 |   55 |   258 |
| 2023 |    6 |   10 |     1 |    4 |    21 |
| 2024 |   25 |   25 |    24 |   20 |    94 |
| 2025 |   35 |   27 |    10 |   18 |    90 |
| 2026 |   22 |   17 |    22 |   13 |    74 |
- Pair-window trades 267 (of 2213 since 2016): 81 per year over 4 instruments; days with at least one position 115 of 831 = 13.8% (mean 0.32 open positions per day vs 4 for always-long) - long exposure fraction about 14%; long-only, so no short exposure at all.
- Concentration: best 5% of POSITION days (6 days) carry 67% of the net pair-window P&L (22.2% of gross absolute daily P&L vs 15.5% median / 19.3% 95th percentile for random long entries with the same monthly counts - the real sleeve is more right-skewed than random longs). Removing those best position days (the 6 best of 115 position days): additive-20% uplift +0.08 / +0.59 / +0.05 / +0.14 (from +0.18 / +0.39 / +0.20 / +0.20). Removing the best 5% of ALL window days (42 days) gives -0.40 / -0.09 / -0.56 / -0.40 - not informative alone because removing the best 5% of days destroys any long strategy; use the null comparison above.
- Sized contracts at 20% share (per signal; mean / p95 / max; trades in window) and assumed initial margin: ES: 1.6/2.4/3.0 (84 trades; $13,000), NQ: 0.8/1.4/1.5 (76 trades; $18,000), RTY: 2.6/3.5/3.8 (56 trades; $8,000), YM: 2.3/3.0/3.4 (51 trades; $10,000); peak concurrent margin 120,621 USD, mean 45,393 USD (margins are ASSUMPTIONS, not verified); the 100%-share scale factor is 31363.3.

Sized dollars and insurance metric set (weekly; $):

| span | row | Sharpe | Sortino | MAR | net $/yr | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | 1,329,959 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | sleeve alone (100%) | 1.23 | 3.45 | 3.65 | 1,124,230 | -86,225 | -53,116 | 307,937 | -136,683 | 11.4 |
| clean | pair + 20% sleeve (add) | 1.64 | 3.33 | 5.82 | 1,554,805 | -80,799 | -78,740 | 267,055 | -92,240 | 42.9 |
| clean | pair + 30% sleeve (add) | 1.71 | 3.60 | 6.40 | 1,667,228 | -81,852 | -79,314 | 260,528 | -97,422 | 43.8 |
| clean | constant-risk 30% | 1.77 | 3.92 | 7.19 | 1,268,240 | -58,244 | -56,037 | 176,495 | -72,860 | 44.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | 593,797 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | sleeve alone (100%) | 2.51 | 10.43 | 5.21 | 379,181 | -32,121 | -24,557 | 72,717 | -44,365 | 10.7 |
| H1 | pair + 20% sleeve (add) | 3.22 | 7.81 | 4.95 | 669,634 | -65,861 | -58,197 | 135,171 | -67,748 | 35.7 |
| H1 | pair + 30% sleeve (add) | 3.39 | 8.71 | 5.35 | 707,552 | -59,987 | -54,281 | 132,228 | -63,156 | 35.7 |
| H1 | constant-risk 30% | 3.58 | 9.94 | 5.87 | 529,413 | -36,704 | -34,472 | 90,250 | -40,077 | 35.7 |
| H2 | pair | 2.48 | 5.08 | 3.77 | 819,748 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | sleeve alone (100%) | 1.72 | 2.95 | 1.79 | 297,847 | -72,810 | -49,867 | 166,282 | -109,560 | 11.1 |
| H2 | pair + 20% sleeve (add) | 2.68 | 5.68 | 4.04 | 879,317 | -79,970 | -76,128 | 217,425 | -82,524 | 41.7 |
| H2 | pair + 30% sleeve (add) | 2.77 | 5.97 | 4.18 | 909,102 | -79,970 | -74,599 | 217,425 | -82,524 | 41.7 |
| H2 | constant-risk 30% | 2.87 | 6.32 | 4.36 | 663,177 | -55,979 | -51,344 | 152,198 | -57,767 | 38.9 |
| all | pair | 1.90 | 3.71 | 9.79 | 2,743,504 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | sleeve alone (100%) | 1.43 | 3.80 | 5.85 | 1,801,259 | -78,593 | -50,361 | 307,937 | -136,683 | 11.3 |
| all | pair + 20% sleeve (add) | 2.10 | 4.37 | 11.62 | 3,103,755 | -80,221 | -77,115 | 267,055 | -92,240 | 41.7 |
| all | pair + 30% sleeve (add) | 2.18 | 4.69 | 12.60 | 3,283,881 | -80,923 | -76,893 | 260,528 | -97,422 | 42.3 |
| all | constant-risk 30% | 2.25 | 5.07 | 13.94 | 2,460,830 | -57,278 | -53,790 | 176,495 | -72,860 | 42.3 |

### ensemble seeds 0-4
- Signals per year (entries; 2016-2022 are walk-forward out-of-sample ERA, 2023-26 the pair window):
|      |   ES |   NQ |   RTY |   YM |   all |
|-----:|-----:|-----:|------:|-----:|------:|
| 2016 |   61 |   67 |     0 |   63 |   191 |
| 2017 |   63 |   83 |    65 |   67 |   278 |
| 2018 |   88 |   57 |    78 |  108 |   331 |
| 2019 |   57 |   64 |    39 |   54 |   214 |
| 2020 |   99 |  109 |    78 |   82 |   368 |
| 2021 |   43 |   67 |   111 |   64 |   285 |
| 2022 |   64 |   67 |    70 |   50 |   251 |
| 2023 |    3 |   10 |     0 |    3 |    16 |
| 2024 |   24 |   23 |    19 |   16 |    82 |
| 2025 |   26 |   21 |    11 |   13 |    71 |
| 2026 |   20 |   15 |    20 |   14 |    69 |
- Pair-window trades 232 (of 2156 since 2016): 70 per year over 4 instruments; days with at least one position 95 of 831 = 11.4% (mean 0.28 open positions per day vs 4 for always-long) - long exposure fraction about 11%; long-only, so no short exposure at all.
- Concentration: best 5% of POSITION days (5 days) carry 61% of the net pair-window P&L (23.5% of gross absolute daily P&L vs 15.8% median / 19.5% 95th percentile for random long entries with the same monthly counts - the real sleeve is more right-skewed than random longs). Removing those best position days (the 6 best of 95 position days): additive-20% uplift +0.10 / +0.49 / +0.23 / +0.18 (from +0.21 / +0.26 / +0.25 / +0.21). Removing the best 5% of ALL window days (42 days) gives -0.38 / -0.31 / -0.63 / -0.43 - not informative alone because removing the best 5% of days destroys any long strategy; use the null comparison above.
- Sized contracts at 20% share (per signal; mean / p95 / max; trades in window) and assumed initial margin: ES: 1.6/2.4/3.2 (72 trades; $13,000), NQ: 0.9/1.4/1.6 (67 trades; $18,000), RTY: 2.7/3.7/4.0 (50 trades; $8,000), YM: 2.4/3.1/3.6 (43 trades; $10,000); peak concurrent margin 126,377 USD, mean 49,334 USD (margins are ASSUMPTIONS, not verified); the 100%-share scale factor is 32859.8.

Sized dollars and insurance metric set (weekly; $):

| span | row | Sharpe | Sortino | MAR | net $/yr | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | 1,329,959 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | sleeve alone (100%) | 1.39 | 4.87 | 3.73 | 1,262,560 | -67,976 | -40,863 | 338,562 | -115,769 | 10.5 |
| clean | pair + 20% sleeve (add) | 1.67 | 3.42 | 5.46 | 1,582,471 | -79,088 | -76,893 | 289,746 | -84,042 | 43.8 |
| clean | pair + 30% sleeve (add) | 1.74 | 3.73 | 5.80 | 1,708,727 | -79,269 | -76,546 | 294,564 | -85,126 | 44.8 |
| clean | constant-risk 30% | 1.81 | 4.11 | 6.22 | 1,309,739 | -55,651 | -53,269 | 210,531 | -60,564 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | 593,797 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | sleeve alone (100%) | 2.02 | 5.48 | 2.51 | 257,476 | -44,695 | -29,796 | 102,679 | -51,854 | 7.1 |
| H1 | pair + 20% sleeve (add) | 3.08 | 7.30 | 4.51 | 645,293 | -67,877 | -59,542 | 143,131 | -78,287 | 39.3 |
| H1 | pair + 30% sleeve (add) | 3.20 | 7.88 | 4.64 | 671,040 | -63,011 | -56,297 | 144,734 | -78,287 | 39.3 |
| H1 | constant-risk 30% | 3.32 | 8.54 | 4.80 | 492,901 | -42,405 | -36,488 | 102,756 | -54,801 | 35.7 |
| H2 | pair | 2.48 | 5.08 | 3.77 | 819,748 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | sleeve alone (100%) | 1.78 | 3.23 | 2.09 | 358,726 | -81,638 | -57,569 | 171,766 | -114,788 | 11.1 |
| H2 | pair + 20% sleeve (add) | 2.73 | 5.95 | 4.10 | 891,493 | -79,970 | -73,467 | 217,425 | -82,524 | 41.7 |
| H2 | pair + 30% sleeve (add) | 2.84 | 6.37 | 4.27 | 927,365 | -79,970 | -73,348 | 217,425 | -82,524 | 41.7 |
| H2 | constant-risk 30% | 2.97 | 6.87 | 4.48 | 681,441 | -55,979 | -51,344 | 152,198 | -57,767 | 38.9 |
| all | pair | 1.90 | 3.71 | 9.79 | 2,743,504 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | sleeve alone (100%) | 1.48 | 4.45 | 5.55 | 1,878,762 | -70,392 | -45,245 | 338,562 | -115,769 | 10.1 |
| all | pair + 20% sleeve (add) | 2.11 | 4.44 | 10.77 | 3,119,256 | -79,195 | -76,568 | 289,746 | -84,042 | 42.9 |
| all | pair + 30% sleeve (add) | 2.18 | 4.79 | 11.23 | 3,307,132 | -79,316 | -75,939 | 294,564 | -85,126 | 43.5 |
| all | constant-risk 30% | 2.26 | 5.20 | 11.80 | 2,484,081 | -55,629 | -52,784 | 210,531 | -60,564 | 41.7 |

## Reading and status
- Nothing here changes the family status: it is ONE signal (daily walk-forward trees on ES/NQ/RTY/YM driven by the VIX state), FOUND-PENDING-REPLICATION, not FOUND. What the stress test adds: (a) the headline is not a lucky seed (90% of 1,000 seeds clear +0.10 on all three spans; seed 0 is a below-median draw); (b) the earlier worry about a seed-dependent plateau is mostly a threshold-edge effect (delta 0.10), and seed ensembles stabilise it; (c) it is not LightGBM-specific but it is tree-specific; (d) the VIX block is the carrier and its date alignment matters (the permuted-VIX null collapses the effect); (e) the sleeve is concentrated (a few large winning days) and long-only exposure is only about 14% of days, with 267 trades in 3.2 years - the sample for a live decision is small.
- What it does not fix: one rising market sample (always-long equal-exposure Sharpe 0.65 and RW1's Sharpe-difference CI includes zero), H0 (2023-02..07) fails in every variant, no independent market (NKD and other asset classes fail), and the 145 hand-picked variants (effective ~3.9 independent trials). The forward lines (PRED_EXTRA.json) remain the arbiter.
- Execution: unchanged from K4v2 (daily signal file after 16:15 ET, market orders at 16:16 ET, whole contracts; at 20% share about 1 ES-equivalent contract per signal). Margin figures above are assumptions.

Files: code/census/night_ins/ap_sk_lib.py, ap_sk_run.py (sk1, sk3, sk3c, sk4), ap_sk_fam.py, ap_sk_rw5.py, ap_sk_trade.py, ap_sk_rep.py; data in outputs/autopilot/sk/.

DONE SK
