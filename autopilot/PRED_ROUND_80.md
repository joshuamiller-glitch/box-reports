# PRED ROUND 80 - block B round 16 - B26+B27+B28+B262728

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.510 [0.49,0.53]
Gap to FOUND: 0.170 AUC, 5 of 5 economic conditions short.
not found - short by 0.170 AUC and 5 of 5 economic conditions

prereg 4e8b46fe45017d2996d9f2a39e8b39443ad3162764c5e13254aadae9deea86ba ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': ''} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B27-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B28-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B26-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| B262728-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| B26-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B27-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B28-G | sig | POOLED | gbt3 | 0.512 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B262728-G | sig | POOLED | gbt3 | 0.512 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B26-G -1 POOLED: selected on WF-PRE
- B27-G -1 POOLED: selected on WF-PRE
- B28-G -1 POOLED: selected on WF-PRE
- B262728-G -1 POOLED: selected on WF-PRE
- B26-G -1 POOLED: selected on WF-PRE
- B27-G -1 POOLED: selected on WF-PRE
- B28-G -1 POOLED: selected on WF-PRE
- B262728-G -1 POOLED: selected on WF-PRE
