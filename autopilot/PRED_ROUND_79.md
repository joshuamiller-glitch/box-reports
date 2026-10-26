# PRED ROUND 79 - block B round 15 - B24

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.510 [0.49,0.53]
Gap to FOUND: 0.170 AUC, 5 of 5 economic conditions short.
not found - short by 0.170 AUC and 5 of 5 economic conditions

prereg 72510d45cbdb26c43f268280c2563dd63626af155326d636e70583d00e6cc25a ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': ''} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B24-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B24-G | sig | POOLED | logit2 | 0.513 [0.50,0.52] | 0.505 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B24-G -1 POOLED: selected on WF-PRE
- B24-G -1 POOLED: selected on WF-PRE
