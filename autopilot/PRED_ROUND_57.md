# PRED ROUND 57 - block B round 11 - B8b-cnnlstm-unlocked

Best HOLDOUT F-R AUC: +15 POOLED 0.516 [0.48,0.55] | ASIA 0.518 [0.46,0.58] | LONDON 0.517 [0.45,0.58] | NY 0.511 [0.45,0.57]
Best HOLDOUT F-R AUC: +30 POOLED 0.498 [0.46,0.54] | ASIA 0.457 [0.39,0.52] | LONDON 0.552 [0.50,0.61] | NY 0.486 [0.42,0.55]
Best G HOLDOUT AUC: 0.518 [0.50,0.53]
Gap to FOUND: 0.142 AUC, 5 of 5 economic conditions short.
not found - short by 0.142 AUC and 5 of 5 economic conditions

prereg 5a4aafcaaa5a43fa141d6a807b8bab331cbaf51275287f8573ff22004ed04d76 ; trials added 300 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'unlocked-label refit of the B_round6 net'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B8b-cnnlstm-cond | +30 | LONDON | cnnlstm | 0.521 [0.48,0.56] | 0.552 [0.50,0.61] | - | 0.550 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8b-cnnlstm-cond | +15 | ASIA | cnnlstm | 0.536 [0.49,0.58] | 0.518 [0.46,0.58] | - | 0.517 | - | - | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| B8b-cnnlstm-G | sig | POOLED | cnnlstm | 0.513 [0.50,0.52] | 0.518 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8b-cnnlstm-cond | +15 | LONDON | cnnlstm | 0.500 [0.45,0.55] | 0.517 [0.45,0.58] | - | 0.518 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8b-cnnlstm-cond | +15 | POOLED | cnnlstm | 0.508 [0.48,0.53] | 0.516 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| B8b-cnnlstm-cond | +15 | NY | cnnlstm | 0.487 [0.45,0.53] | 0.511 [0.45,0.57] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8b-cnnlstm-cond | +30 | POOLED | cnnlstm | 0.501 [0.48,0.52] | 0.498 [0.46,0.54] | - | 0.497 | - | - | - | - | - | - |  | short by 0.182 AUC, 5 of 5 econ |
| B8b-cnnlstm-G | sig | POOLED | cnnlstm | 0.499 [0.49,0.51] | 0.497 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8b-cnnlstm-cond | +30 | NY | cnnlstm | 0.480 [0.44,0.52] | 0.486 [0.42,0.55] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8b-cnnlstm-cond | +30 | ASIA | cnnlstm | 0.501 [0.46,0.55] | 0.457 [0.39,0.52] | - | 0.453 | - | - | - | - | - | - |  | dead (no gain over baseline) |

One-sentence notes:
- B8b-cnnlstm-cond 15 POOLED: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 15 ASIA: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 15 LONDON: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 15 NY: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 30 POOLED: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 30 ASIA: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 30 LONDON: unlocked label; horizons fixed in prereg
- B8b-cnnlstm-cond 30 NY: unlocked label; horizons fixed in prereg
