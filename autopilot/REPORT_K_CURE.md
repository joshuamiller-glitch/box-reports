# REPORT K_CURE - whipsaw-probability GBM on the pair's entries with the random-removal null as the selection criterion (L2-free features)

**Verdict: NO. FOUND 0, no variant beats the random-removal p95 on both H1 and H2.** Of 90 pre-registered variants (5 feature sets x 2 parameter sets x 3 whipsaw definitions x 3 actions), 25 give a weekly-Sharpe uplift >= +0.10 on clean, H1 and H2, but only 2 beat the null p95 on H1 and 5 on H2 (about 4.5 of each expected by chance at a 5% level), and none beats it on both spans.

Pre-registered in PREREG_AUTOPILOT.md ('K CURE'). Pair = B.Cfg(wk_floor=8, wk_loss_pb=None) (1.46 / 2.83 / 2.30). Walk-forward LightGBM monthly refit as K82/83; targets: stopped within 10 / 20 / 30 minutes with a negative result; actions: skip the top-scored 5% or 10% of entries, or half-size the top 10% (cut-offs from clean predictions). Null: 200 random-removal draws per action (same nominal share of the eligible rows 2023-08 onwards, same engine), p95 of the weekly-Sharpe change per span (clean / H1 / H2): skip 5% {0.19, 0.75, 0.51}, skip 10% {0.25, 0.86, 0.51}, half 10% {0.08, 0.90, 0.55}. Fill model: the corrected NT8-faithful engine with 1 tick/side and $34.88 per 8 lots. Features: price (C2-G2) + NQ/ES signed-volume flow + lagged daily NQ gamma; no L2.

## By feature set and target
| set              |   n |   pass3 |   beatH1 |   beatH2 |
|:-----------------|----:|--------:|---------:|---------:|
| flow             |  18 |       4 |        0 |        0 |
| flow+gamma       |  18 |       3 |        0 |        2 |
| price            |  18 |       0 |        0 |        0 |
| price+flow       |  18 |       7 |        1 |        1 |
| price+flow+gamma |  18 |      11 |        1 |        2 |

| target   |   n |   pass3 |   beatH1 |   beatH2 |
|:---------|----:|--------:|---------:|---------:|
| w10      |  30 |       1 |        2 |        0 |
| w20      |  30 |      13 |        0 |        3 |
| w30      |  30 |      11 |        0 |        2 |

## Best ten by H1 uplift (all 90 variants in outputs/autopilot/k/k_cure_cells.csv)
| cell | uplift clean | H1 | H2 | null p95 H1 | null p95 H2 | beats both |
|---|---|---|---|---|---|---|
| flow|P|w30|skip10 | 0.36 | 0.85 | 0.36 | 0.86 | 0.51 | False |
| price+flow+gamma|A|w10|skip5 | 0.14 | 0.82 | 0.43 | 0.75 | 0.51 | False |
| price+flow|A|w10|skip5 | 0.21 | 0.76 | 0.10 | 0.75 | 0.51 | False |
| price+flow|P|w10|skip5 | -0.03 | 0.74 | -0.23 | 0.75 | 0.51 | False |
| price+flow|P|w20|skip5 | 0.25 | 0.73 | 0.10 | 0.75 | 0.51 | False |
| price+flow|P|w20|half10 | 0.17 | 0.68 | 0.17 | 0.90 | 0.55 | False |
| price+flow|P|w20|skip10 | 0.42 | 0.67 | 0.19 | 0.86 | 0.51 | False |
| price+flow+gamma|P|w10|skip5 | -0.04 | 0.67 | 0.12 | 0.75 | 0.51 | False |
| price+flow|P|w30|skip5 | 0.20 | 0.65 | 0.11 | 0.75 | 0.51 | False |
| price+flow|P|w10|half10 | -0.08 | 0.64 | 0.10 | 0.90 | 0.55 | False |

## The 25 variants with +0.10 on all three spans (top ten by H2)
| cell | uplift clean | H1 | H2 | p95 H1 | p95 H2 |
|---|---|---|---|---|---|
| flow+gamma|P|w20|skip10 | 0.33 | 0.16 | 0.66 | 0.86 | 0.51 |
| price+flow+gamma|P|w30|half10 | 0.21 | 0.17 | 0.64 | 0.90 | 0.55 |
| price+flow+gamma|A|w20|skip5 | 0.39 | 0.57 | 0.54 | 0.75 | 0.51 |
| price+flow+gamma|A|w10|skip5 | 0.14 | 0.82 | 0.43 | 0.75 | 0.51 |
| price+flow|A|w20|skip5 | 0.26 | 0.62 | 0.40 | 0.75 | 0.51 |
| price+flow+gamma|P|w20|half10 | 0.14 | 0.32 | 0.40 | 0.90 | 0.55 |
| flow|P|w30|skip10 | 0.36 | 0.85 | 0.36 | 0.86 | 0.51 |
| price+flow|A|w30|skip5 | 0.18 | 0.52 | 0.36 | 0.75 | 0.51 |
| price+flow+gamma|A|w20|skip10 | 0.33 | 0.32 | 0.31 | 0.86 | 0.51 |
| flow|P|w20|skip10 | 0.36 | 0.50 | 0.29 | 0.86 | 0.51 |

Reading: the null is wide in H1 (p95 +0.75 to +0.90 from removing a random 5-10% of entries) because the day lock and week floor make the engine path-dependent, so even large H1 uplifts are inside the noise band; the observed number of variants beating the p95 on a span is what chance gives. The earlier K82/83 conclusion stands: the whipsaw label is predictable (AUC 0.74-0.82) but skipping predicted whipsaws does not beat random removal.

## K-L2 status
NQ mbp-10 (job GLBX-20261013-Y3PCQ4MKV3) had not landed at the time of this run (no outputs/a5/L2-DONE; checked read-only). The K-L2 variant (top-5 book imbalance, spread, depth and queue features added to the best two action/target combinations, same 100-draw null selection) is pre-registered and will be run when the marker appears; ES mbp-10 is on disk but the pair trades NQ, so ES depth features alone are not a pair filter.

DONE K_CURE
