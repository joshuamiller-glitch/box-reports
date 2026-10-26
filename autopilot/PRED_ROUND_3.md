# PRED ROUND 3 - block I round 1 - I1-tsfresh

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.592 [0.55,0.64]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 32a2ba2477d68be0e3907aa877de2e6de070721a106498fe50d6a29a3e2d38b3 ; trials added 2428 ; truncation audit {'decisions': 480, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/I1.parquet', 'l2vast/pred/store/I1_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I1-tsfresh | sig | LONDON | logit2/GBOTH | 0.615 [0.58,0.65] | 0.592 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | POOLED | gbt3/GBOTH | 0.574 [0.56,0.59] | 0.571 [0.55,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | NY | logit2/GBOTH | 0.591 [0.56,0.62] | 0.569 [0.52,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | POOLED/ST | gbt3/GBOTH | 0.573 [0.55,0.60] | 0.567 [0.54,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | POOLED/HM | logit2/GBOTH | 0.569 [0.55,0.59] | 0.562 [0.53,0.59] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | ASIA | rf/GI1 | 0.542 [0.52,0.57] | 0.551 [0.52,0.58] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | sig | ASIA | rf/GI1 | 0.525 [0.50,0.55] | 0.529 [0.49,0.56] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | sig | POOLED | gbt3/GBOTH | 0.526 [0.51,0.54] | 0.516 [0.49,0.54] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | LONDON | logit2/GBOTH | 0.547 [0.51,0.58] | 0.512 [0.46,0.57] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | POOLED/ST | gbt3/GBOTH | 0.524 [0.50,0.55] | 0.511 [0.48,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | POOLED/HM | logit2/GBOTH | 0.522 [0.50,0.54] | 0.504 [0.47,0.54] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | sig | NY | logit2/GBOTH | 0.533 [0.50,0.57] | 0.502 [0.45,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | pre | POOLED | stack/pertype/BOTH | - | - | - | - | 0.580 | - | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | pre | ASIA | stack/pooled/BOTH | - | - | - | - | 0.513 | - | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | pre | LONDON | stack/pertype/BOTH | - | - | - | - | 0.518 | - | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | pre | NY | rf/pooled/BOTH | - | - | - | - | 0.606 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +5 | POOLED | rf/pooled/BOTH | - | - | - | - | 0.629 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +5 | ASIA | stack/pertype/BOTH | - | - | - | - | 0.497 | - | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +5 | LONDON | logit2/pooled/BOTH | - | - | - | - | 0.591 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +5 | NY | rf/pooled/BOTH | - | - | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +10 | POOLED | rf/pertype/BOTH | - | - | - | - | 0.618 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +10 | ASIA | rf/pertype/BOTH | - | - | - | - | 0.489 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +10 | LONDON | logit2/pooled/BOTH | - | - | - | - | 0.641 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +10 | NY | rf/pertype/IONLY | - | - | - | - | 0.630 | N | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +15 | POOLED | rf/pooled/BOTH | - | - | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +15 | ASIA | rf/pooled/BOTH | - | - | - | - | 0.530 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +15 | LONDON | logit2/pertype/BOTH | - | - | - | - | 0.544 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +15 | NY | logit2/pertype/IONLY | - | - | - | - | 0.664 | N | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +20 | POOLED | stack/pertype/IONLY | - | - | - | - | 0.584 | - | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +20 | ASIA | gbt3/pertype/IONLY | - | - | - | - | 0.489 | N | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +20 | LONDON | gbt3/pertype/BOTH | - | - | - | - | 0.536 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +20 | NY | logit2/pertype/IONLY | - | - | - | - | 0.645 | N | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +30 | POOLED | logit2/pooled/IONLY | - | - | - | - | 0.651 | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +30 | ASIA | logit2/pooled/IONLY | - | - | - | - | 0.543 | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +30 | LONDON | rf/pertype/BOTH | - | - | - | - | 0.612 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +30 | NY | logit2/pertype/BOTH | - | - | - | - | 0.726 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +45 | POOLED | rf/pooled/IONLY | - | - | - | - | 0.638 | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +45 | ASIA | rf/pooled/IONLY | - | - | - | - | 0.467 | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +45 | LONDON | logit2/pooled/BOTH | - | - | - | - | 0.614 | ok | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +45 | NY | logit2/pertype/BOTH | - | - | - | - | 0.721 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +60 | POOLED | rf/pertype/BOTH | - | - | - | - | 0.642 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +60 | ASIA | rf/pooled/IONLY | - | - | - | - | 0.490 | ok | - | - | - | - |  | locked label (reference only) |
| I1-tsfresh | +60 | LONDON | rf/pertype/BOTH | - | - | - | - | 0.590 | N | - | - | - | - | stack | locked label (reference only) |
| I1-tsfresh | +60 | NY | logit2/pertype/BOTH | - | - | - | - | 0.762 | N | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I1-tsfresh 0 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.646 (rf/pooled); delta hold -0.066
- I1-tsfresh 0 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.532 (rf/pooled); delta hold -0.019
- I1-tsfresh 0 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.554 (logit2/pertype); delta hold -0.037
- I1-tsfresh 0 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.680 (rf/pooled); delta hold -0.074
- I1-tsfresh 5 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.634 (rf/pooled); delta hold -0.005
- I1-tsfresh 5 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.532 (gbt3/pooled); delta hold -0.034
- I1-tsfresh 5 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.556 (logit2/pertype); delta hold +0.035
- I1-tsfresh 5 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.716 (rf/pooled); delta hold -0.083
- I1-tsfresh 10 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.672 (rf/pooled); delta hold -0.053
- I1-tsfresh 10 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.521 (rf/pooled); delta hold -0.032
- I1-tsfresh 10 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.587 (logit2/pooled); delta hold +0.054
- I1-tsfresh 10 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.765 (rf/pooled); delta hold -0.135
- I1-tsfresh 15 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.695 (rf/pooled); delta hold -0.050
- I1-tsfresh 15 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.543 (rf/pooled); delta hold -0.014
- I1-tsfresh 15 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.658 (gbt3/pooled); delta hold -0.114
- I1-tsfresh 15 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.802 (stack/pooled); delta hold -0.138
- I1-tsfresh 20 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.614 (stack/pertype); delta hold -0.030
- I1-tsfresh 20 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.510 (logit2/pertype); delta hold -0.021
- I1-tsfresh 20 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.548 (logit2/pertype); delta hold -0.013
- I1-tsfresh 20 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.832 (stack/pooled); delta hold -0.187
- I1-tsfresh 30 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.617 (stack/pertype); delta hold +0.034
- I1-tsfresh 30 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.514 (stack/pertype); delta hold +0.029
- I1-tsfresh 30 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.652 (gbt3/pooled); delta hold -0.040
- I1-tsfresh 30 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.741 (rf/pertype); delta hold -0.015
- I1-tsfresh 45 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.667 (gbt3/pooled); delta hold -0.028
- I1-tsfresh 45 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.536 (logit2/pertype); delta hold -0.069
- I1-tsfresh 45 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.627 (gbt3/pooled); delta hold -0.013
- I1-tsfresh 45 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.740 (logit2/pertype); delta hold -0.019
- I1-tsfresh 60 POOLED: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.646 (stack/pertype); delta hold -0.004
- I1-tsfresh 60 ASIA: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.538 (gbt3/pertype); delta hold -0.047
- I1-tsfresh 60 LONDON: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.663 (rf/pooled); delta hold -0.073
- I1-tsfresh 60 NY: I1-tsfresh: best I-arm by WF-PRE; same-cell BASE (FAILPRED) hold AUC 0.878 (gbt3/pooled); delta hold -0.116
- I1-tsfresh -1 POOLED: G ALL: same-cell GBASE hold AUC 0.582; delta -0.011
- I1-tsfresh -1 ASIA: G ASIA: same-cell GBASE hold AUC 0.562; delta -0.010
- I1-tsfresh -1 POOLED: G HM: same-cell GBASE hold AUC 0.579; delta -0.017
- I1-tsfresh -1 LONDON: G LONDON: same-cell GBASE hold AUC 0.607; delta -0.014
- I1-tsfresh -1 NY: G NY: same-cell GBASE hold AUC 0.603; delta -0.033
- I1-tsfresh -1 POOLED: G ST: same-cell GBASE hold AUC 0.587; delta -0.021
- I1-tsfresh -1 POOLED: G ALL: same-cell GBASE hold AUC 0.582; delta -0.011 [stop_vs_target, model chosen on stop_vs_rest pre]
- I1-tsfresh -1 ASIA: G ASIA: same-cell GBASE hold AUC 0.562; delta -0.010 [stop_vs_target, model chosen on stop_vs_rest pre]
- I1-tsfresh -1 POOLED: G HM: same-cell GBASE hold AUC 0.579; delta -0.017 [stop_vs_target, model chosen on stop_vs_rest pre]
- I1-tsfresh -1 LONDON: G LONDON: same-cell GBASE hold AUC 0.607; delta -0.014 [stop_vs_target, model chosen on stop_vs_rest pre]
- I1-tsfresh -1 NY: G NY: same-cell GBASE hold AUC 0.603; delta -0.033 [stop_vs_target, model chosen on stop_vs_rest pre]
- I1-tsfresh -1 POOLED: G ST: same-cell GBASE hold AUC 0.587; delta -0.021 [stop_vs_target, model chosen on stop_vs_rest pre]
