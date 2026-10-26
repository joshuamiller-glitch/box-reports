# PRED ROUND 94 - block B round 17 - B29+B30+B31+B32+B33+B2933

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.514 [0.50,0.53]
Gap to FOUND: 0.166 AUC, 5 of 5 economic conditions short.
not found - short by 0.166 AUC and 5 of 5 economic conditions

prereg c45fff13280ac01ec228dd2fcd3cacfe6a6b559027adfd4e2987728bdeadc729 ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'T5 (B29-B33) decisions 120 checks 4629 mismatches 0'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B2933-G | sig | POOLED | rf | 0.517 [0.51,0.53] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B29-G | sig | POOLED | rf | 0.516 [0.50,0.53] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B30-G | sig | POOLED | rf | 0.518 [0.51,0.53] | 0.513 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B30-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B2933-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B29-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B31-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B32-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B33-G | sig | POOLED | rf | 0.512 [0.50,0.52] | 0.506 [0.49,0.52] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| B31-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B32-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B33-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B29-G -1 POOLED: selected on WF-PRE
- B30-G -1 POOLED: selected on WF-PRE
- B31-G -1 POOLED: selected on WF-PRE
- B32-G -1 POOLED: selected on WF-PRE
- B33-G -1 POOLED: selected on WF-PRE
- B2933-G -1 POOLED: selected on WF-PRE
- B29-G -1 POOLED: selected on WF-PRE
- B30-G -1 POOLED: selected on WF-PRE
- B31-G -1 POOLED: selected on WF-PRE
- B32-G -1 POOLED: selected on WF-PRE
- B33-G -1 POOLED: selected on WF-PRE
- B2933-G -1 POOLED: selected on WF-PRE
