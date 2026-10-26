# PRED ROUND 53 - block B round 9 - B18+B19+B1819+BALL

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.530 [0.52,0.55]
Gap to FOUND: 0.150 AUC, 5 of 5 economic conditions short.
not found - short by 0.150 AUC and 5 of 5 economic conditions

prereg a077c1ed22e924239bb84f204720fba4fbf9ccddec3fcdc625e1be679278aea5 ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'B18 decisions 120 checks 9240 mismatches 0; B19 pure sign-flip of audited features'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1819-G | sig | POOLED | rf | 0.534 [0.52,0.55] | 0.530 [0.52,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| BALL-G | sig | POOLED | stack | 0.522 [0.51,0.53] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B18-G | sig | POOLED | logit2 | 0.521 [0.51,0.53] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B1819-G | sig | POOLED | logit2 | 0.513 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| B19-G | sig | POOLED | logit2 | 0.514 [0.50,0.53] | 0.512 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| B18-G | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| B19-G | sig | POOLED | stack | 0.519 [0.51,0.53] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| BALL-G | sig | POOLED | gbt3 | 0.510 [0.50,0.52] | 0.507 [0.49,0.52] | - | - | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |

One-sentence notes:
- B18-G -1 POOLED: selected on WF-PRE
- B19-G -1 POOLED: selected on WF-PRE
- B1819-G -1 POOLED: selected on WF-PRE
- BALL-G -1 POOLED: selected on WF-PRE
- B18-G -1 POOLED: selected on WF-PRE
- B19-G -1 POOLED: selected on WF-PRE
- B1819-G -1 POOLED: selected on WF-PRE
- BALL-G -1 POOLED: selected on WF-PRE
