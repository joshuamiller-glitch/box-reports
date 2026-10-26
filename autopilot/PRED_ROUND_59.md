# PRED ROUND 59 - block B round 12 - B20+B21+B2021

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.520 [0.51,0.53]
Gap to FOUND: 0.160 AUC, 5 of 5 economic conditions short.
not found - short by 0.160 AUC and 5 of 5 economic conditions

prereg 56ff359471d865a9d61e5d65188e1d91a59fe7c922d21ff8188be083f21ba9d0 ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'B20/B21 decisions 100 checks 3600 mismatches 0'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B2021-G | sig | POOLED | rf | 0.522 [0.51,0.54] | 0.520 [0.51,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B20-G | sig | POOLED | rf | 0.522 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B21-G | sig | POOLED | gbt3 | 0.520 [0.51,0.53] | 0.516 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B21-G | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| B2021-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B20-G | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.508 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |

One-sentence notes:
- B20-G -1 POOLED: selected on WF-PRE
- B21-G -1 POOLED: selected on WF-PRE
- B2021-G -1 POOLED: selected on WF-PRE
- B20-G -1 POOLED: selected on WF-PRE
- B21-G -1 POOLED: selected on WF-PRE
- B2021-G -1 POOLED: selected on WF-PRE
