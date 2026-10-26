# PRED ROUND 45 - block B round 6 - B8b-cnnlstm

Best HOLDOUT F-R AUC: +15 POOLED 0.562 [0.52,0.60] | ASIA 0.547 [0.49,0.60] | LONDON 0.584 [0.51,0.66] | NY 0.494 [0.40,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.509 [0.46,0.55] | ASIA 0.522 [0.45,0.59] | LONDON 0.497 [0.42,0.58] | NY 0.432 [0.33,0.54]
Best G HOLDOUT AUC: 0.517 [0.50,0.54]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5a4aafcaaa5a43fa141d6a807b8bab331cbaf51275287f8573ff22004ed04d76 ; trials added 300 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'windows built from bars with minute<decision; model fixed epochs; no features stored'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B8b-cnnlstm-cond | +15 | LONDON | cnnlstm | 0.560 [0.50,0.62] | 0.584 [0.51,0.66] | - | 0.598 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +15 | POOLED | cnnlstm | 0.534 [0.51,0.56] | 0.562 [0.52,0.60] | - | 0.558 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +15 | ASIA | cnnlstm | 0.522 [0.48,0.56] | 0.547 [0.49,0.60] | - | 0.544 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +30 | ASIA | cnnlstm | 0.519 [0.47,0.57] | 0.522 [0.45,0.59] | - | 0.516 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-G | sig | POOLED | cnnlstm | 0.510 [0.49,0.53] | 0.517 [0.50,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +30 | POOLED | cnnlstm | 0.516 [0.49,0.55] | 0.509 [0.46,0.55] | - | 0.490 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-G | sig | POOLED | cnnlstm | 0.507 [0.49,0.52] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +30 | LONDON | cnnlstm | 0.508 [0.46,0.56] | 0.497 [0.42,0.58] | - | 0.486 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +15 | NY | cnnlstm | 0.490 [0.43,0.55] | 0.494 [0.40,0.59] | - | 0.509 | - | - | - | - | - | - |  | locked label (reference only) |
| B8b-cnnlstm-cond | +30 | NY | cnnlstm | 0.498 [0.43,0.57] | 0.432 [0.33,0.54] | - | 0.450 | - | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- B8b-cnnlstm-cond 15 POOLED: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 15 ASIA: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 15 LONDON: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 15 NY: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 30 POOLED: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 30 ASIA: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 30 LONDON: both horizons fixed in prereg (no selection)
- B8b-cnnlstm-cond 30 NY: both horizons fixed in prereg (no selection)
