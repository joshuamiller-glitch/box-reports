# PRED ROUND 44 - block B round 3 - B469+B4+B6+B9

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.586 [0.56,0.61]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg ab53addd9edd67c9a9a1c4978cb3d60683c264d235781584e95981de7fb890ed ; trials added 100 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': True, 'detail': 'engine decisions 160 checks 50560 mismatches 0 {}; builder months 0 mismatching columns [] round3: volume-bar stamp leak found by builder audit, fixed, rebuilt, clean'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B6-G | sig | POOLED | rf | 0.582 [0.56,0.60] | 0.586 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-G | sig | POOLED | logit2 | 0.582 [0.57,0.60] | 0.584 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.580 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-G | sig | POOLED | logit2 | 0.580 [0.56,0.60] | 0.577 [0.55,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-G | sig | POOLED | logit2 | 0.508 [0.49,0.53] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-G | sig | POOLED | rf | 0.507 [0.49,0.53] | 0.494 [0.47,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B469-G | sig | POOLED | rf | 0.512 [0.49,0.53] | 0.493 [0.47,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B4-G | sig | POOLED | logit2 | 0.498 [0.48,0.51] | 0.486 [0.46,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- B469-G -1 POOLED: selected on WF-PRE
- B4-G -1 POOLED: selected on WF-PRE
- B6-G -1 POOLED: selected on WF-PRE
- B9-G -1 POOLED: selected on WF-PRE
- B469-G -1 POOLED: selected on WF-PRE
- B4-G -1 POOLED: selected on WF-PRE
- B6-G -1 POOLED: selected on WF-PRE
- B9-G -1 POOLED: selected on WF-PRE
