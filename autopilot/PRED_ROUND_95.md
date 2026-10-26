# PRED ROUND 95 - block B round 18 - B34+B35+B36+B37+B38+B3438

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.527 [0.51,0.54]
Gap to FOUND: 0.153 AUC, 5 of 5 economic conditions short.
not found - short by 0.153 AUC and 5 of 5 economic conditions

prereg c8d7ae3b2c16966a032e835fb82d6d009d1b207f2ce1ca553a67094ca8a690fe ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'T6 (B34-B38) decisions 120 checks 3867 mismatches 0'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B35-G | sig | POOLED | rf | 0.523 [0.51,0.53] | 0.527 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B3438-G | sig | POOLED | stack | 0.519 [0.51,0.53] | 0.520 [0.51,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B36-G | sig | POOLED | gbt3 | 0.521 [0.51,0.53] | 0.519 [0.51,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B34-G | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B3438-G | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B38-G | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B35-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B36-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B37-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B34-G | sig | POOLED | rf | 0.513 [0.50,0.52] | 0.508 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B38-G | sig | POOLED | rf | 0.513 [0.50,0.52] | 0.508 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B37-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B34-G -1 POOLED: selected on WF-PRE
- B35-G -1 POOLED: selected on WF-PRE
- B36-G -1 POOLED: selected on WF-PRE
- B37-G -1 POOLED: selected on WF-PRE
- B38-G -1 POOLED: selected on WF-PRE
- B3438-G -1 POOLED: selected on WF-PRE
- B34-G -1 POOLED: selected on WF-PRE
- B35-G -1 POOLED: selected on WF-PRE
- B36-G -1 POOLED: selected on WF-PRE
- B37-G -1 POOLED: selected on WF-PRE
- B38-G -1 POOLED: selected on WF-PRE
- B3438-G -1 POOLED: selected on WF-PRE
