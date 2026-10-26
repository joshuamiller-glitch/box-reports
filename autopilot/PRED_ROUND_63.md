# PRED ROUND 63 - block B round 13 - B22+B23+B25+B222325

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.538 [0.52,0.55]
Gap to FOUND: 0.142 AUC, 5 of 5 economic conditions short.
not found - short by 0.142 AUC and 5 of 5 economic conditions

prereg 82f3c2b6519ca9438872151b6ca8f0e958b412d711d218a546769eb13d8c14fc ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'B25 decisions 150 checks 5400 mismatches 0; B22/B23 audited separately\nB22 independent re-slice (parquet filter ts<esec) decisions 30 checks 300 mismatches 0; B23 uses tape rows ts<esec only (searchsorted left) - same pattern as audited B21'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B222325-G | sig | POOLED | logit2 | 0.535 [0.52,0.55] | 0.538 [0.52,0.55] | - | - | - | - | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| B25-G | sig | POOLED | stack | 0.537 [0.53,0.55] | 0.529 [0.51,0.55] | - | - | - | - | - | - | - | - |  | WF-only (dead) |
| B25-G | sig | POOLED | logit2 | 0.516 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| B222325-G | sig | POOLED | logit2 | 0.516 [0.50,0.53] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| B23-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| B22-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B22-G | sig | POOLED | stack | 0.518 [0.51,0.53] | 0.509 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B23-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B22-G -1 POOLED: selected on WF-PRE
- B23-G -1 POOLED: selected on WF-PRE
- B25-G -1 POOLED: selected on WF-PRE
- B222325-G -1 POOLED: selected on WF-PRE
- B22-G -1 POOLED: selected on WF-PRE
- B23-G -1 POOLED: selected on WF-PRE
- B25-G -1 POOLED: selected on WF-PRE
- B222325-G -1 POOLED: selected on WF-PRE
