# PRED ROUND 56 - block B round 10 - B0+B123+B57+B469+B1015+B16+B17+B8

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.534 [0.51,0.55]
Gap to FOUND: 0.146 AUC, 5 of 5 economic conditions short.
not found - short by 0.146 AUC and 5 of 5 economic conditions

prereg ea86954d90c97f6520246400662f37976bd6aa254744981cabdaa70c60056665 ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': ''} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B16-G | sig | POOLED | logit2 | 0.530 [0.52,0.54] | 0.534 [0.51,0.55] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B57-G | sig | POOLED | logit2 | 0.527 [0.52,0.54] | 0.527 [0.51,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B1015-G | sig | POOLED | rf | 0.525 [0.51,0.54] | 0.520 [0.50,0.54] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B469-G | sig | POOLED | logit2 | 0.525 [0.51,0.54] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8-G | sig | POOLED | rf | 0.524 [0.51,0.53] | 0.517 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B16-G | sig | POOLED | logit2 | 0.515 [0.50,0.53] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| B469-G | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.513 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| B8-G | sig | POOLED | rf | 0.512 [0.50,0.52] | 0.511 [0.50,0.52] | - | - | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| B123-G | sig | POOLED | gbt3 | 0.519 [0.51,0.53] | 0.511 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B0-G | sig | POOLED | logit2 | 0.512 [0.50,0.53] | 0.510 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| B57-G | sig | POOLED | logit2 | 0.511 [0.50,0.52] | 0.509 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| B123-G | sig | POOLED | logit2 | 0.508 [0.50,0.52] | 0.508 [0.49,0.53] | - | - | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| B0-G | sig | POOLED | gbt3 | 0.511 [0.50,0.52] | 0.504 [0.49,0.52] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| B17-G | sig | POOLED | gbt3 | 0.513 [0.50,0.53] | 0.500 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B17-G | sig | POOLED | rf | 0.504 [0.49,0.52] | 0.495 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B1015-G | sig | POOLED | stack | 0.490 [0.47,0.50] | 0.478 [0.46,0.50] | - | - | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- B0-G -1 POOLED: selected on WF-PRE
- B123-G -1 POOLED: selected on WF-PRE
- B57-G -1 POOLED: selected on WF-PRE
- B469-G -1 POOLED: selected on WF-PRE
- B1015-G -1 POOLED: selected on WF-PRE
- B16-G -1 POOLED: selected on WF-PRE
- B17-G -1 POOLED: selected on WF-PRE
- B8-G -1 POOLED: selected on WF-PRE
- B0-G -1 POOLED: selected on WF-PRE
- B123-G -1 POOLED: selected on WF-PRE
- B57-G -1 POOLED: selected on WF-PRE
- B469-G -1 POOLED: selected on WF-PRE
- B1015-G -1 POOLED: selected on WF-PRE
- B16-G -1 POOLED: selected on WF-PRE
- B17-G -1 POOLED: selected on WF-PRE
- B8-G -1 POOLED: selected on WF-PRE
