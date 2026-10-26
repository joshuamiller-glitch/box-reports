# PRED ROUND 61 - block B round 14 - B8c-sequence-variants

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED 0.495 [0.46,0.53] | ASIA 0.511 [0.45,0.57] | LONDON 0.518 [0.45,0.58] | NY 0.506 [0.45,0.57]
Best G HOLDOUT AUC: 0.521 [0.51,0.53]
Gap to FOUND: 0.086 AUC, 5 of 5 economic conditions short.
not found - short by 0.086 AUC and 5 of 5 economic conditions

prereg 20a21f10084fd17fe45b1f3ff16a89289af16463dfb30ab8549c4f12b1e23cc9 ; trials added 200 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'same windows as B_round6'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B8c-GRU60-cond | +20 | ASIA | GRU60 | 0.549 [0.51,0.59] | 0.574 [0.51,0.64] | - | 0.575 | - | - | - | - | - | - |  | short by 0.086 AUC, 5 of 5 econ |
| B8c-CNNLSTM30-cond | +20 | NY | CNNLSTM30 | 0.550 [0.51,0.59] | 0.539 [0.48,0.59] | - | 0.539 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-cond | +20 | POOLED | GRU60 | 0.518 [0.49,0.54] | 0.527 [0.49,0.56] | - | 0.528 | - | - | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| B8c-CNNLSTM30-G | sig | POOLED | CNNLSTM30 | 0.515 [0.51,0.53] | 0.521 [0.51,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-GRU60-cond | +20 | LONDON | GRU60 | 0.514 [0.48,0.56] | 0.520 [0.47,0.57] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-cond | +10 | NY | GRU60 | 0.517 [0.47,0.57] | 0.519 [0.45,0.59] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-cond | +30 | LONDON | GRU60 | 0.501 [0.46,0.54] | 0.518 [0.45,0.58] | - | 0.521 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-G | sig | POOLED | GRU60 | 0.519 [0.51,0.53] | 0.515 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-G | sig | POOLED | TCN200 | 0.522 [0.51,0.54] | 0.514 [0.50,0.53] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-CNNLSTM30-cond | +10 | NY | CNNLSTM30 | 0.499 [0.45,0.54] | 0.512 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +20 | ASIA | TCN200 | 0.548 [0.51,0.58] | 0.512 [0.45,0.56] | - | 0.488 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +30 | ASIA | TCN200 | 0.545 [0.51,0.58] | 0.511 [0.45,0.57] | - | 0.500 | - | - | - | - | - | - |  | short by 0.149 AUC, 5 of 5 econ |
| B8c-CNNLSTM30-cond | +20 | POOLED | CNNLSTM30 | 0.523 [0.50,0.55] | 0.511 [0.47,0.54] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-GRU60-cond | +30 | NY | GRU60 | 0.504 [0.47,0.55] | 0.506 [0.45,0.57] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-CNNLSTM30-G | sig | POOLED | CNNLSTM30 | 0.503 [0.49,0.51] | 0.503 [0.49,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-CNNLSTM30-cond | +10 | ASIA | CNNLSTM30 | 0.554 [0.50,0.60] | 0.503 [0.45,0.56] | - | 0.503 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-GRU60-cond | +10 | POOLED | GRU60 | 0.510 [0.49,0.53] | 0.500 [0.46,0.54] | - | 0.500 | - | - | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| B8c-GRU60-cond | +10 | ASIA | GRU60 | 0.521 [0.48,0.56] | 0.499 [0.44,0.57] | - | 0.493 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-CNNLSTM30-cond | +10 | POOLED | CNNLSTM30 | 0.517 [0.49,0.54] | 0.497 [0.47,0.53] | - | 0.499 | - | - | - | - | - | - |  | short by 0.183 AUC, 5 of 5 econ |
| B8c-GRU60-cond | +30 | POOLED | GRU60 | 0.504 [0.48,0.53] | 0.495 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | short by 0.185 AUC, 5 of 5 econ |
| B8c-CNNLSTM30-cond | +20 | LONDON | CNNLSTM30 | 0.509 [0.47,0.56] | 0.495 [0.43,0.56] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-G | sig | POOLED | TCN200 | 0.498 [0.49,0.51] | 0.493 [0.48,0.51] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-CNNLSTM30-cond | +20 | ASIA | CNNLSTM30 | 0.509 [0.47,0.55] | 0.493 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-GRU60-G | sig | POOLED | GRU60 | 0.496 [0.48,0.51] | 0.491 [0.48,0.50] | - | - | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +10 | ASIA | TCN200 | 0.538 [0.50,0.57] | 0.490 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-GRU60-cond | +20 | NY | GRU60 | 0.491 [0.45,0.53] | 0.481 [0.42,0.54] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-cond | +10 | LONDON | GRU60 | 0.491 [0.45,0.53] | 0.474 [0.41,0.54] | - | 0.470 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-CNNLSTM30-cond | +10 | LONDON | CNNLSTM30 | 0.497 [0.46,0.54] | 0.473 [0.40,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +10 | LONDON | TCN200 | 0.509 [0.47,0.55] | 0.468 [0.41,0.52] | - | 0.455 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +30 | LONDON | TCN200 | 0.508 [0.46,0.55] | 0.467 [0.41,0.53] | - | 0.454 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-GRU60-cond | +30 | ASIA | GRU60 | 0.507 [0.47,0.55] | 0.457 [0.40,0.52] | - | 0.449 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +20 | LONDON | TCN200 | 0.509 [0.46,0.55] | 0.455 [0.39,0.51] | - | 0.450 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +20 | POOLED | TCN200 | 0.505 [0.48,0.53] | 0.453 [0.41,0.49] | - | 0.445 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +30 | POOLED | TCN200 | 0.498 [0.47,0.53] | 0.453 [0.41,0.49] | - | 0.444 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +10 | POOLED | TCN200 | 0.502 [0.48,0.53] | 0.451 [0.41,0.49] | - | 0.445 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| B8c-TCN200-cond | +10 | NY | TCN200 | 0.459 [0.42,0.50] | 0.401 [0.34,0.46] | - | 0.409 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +20 | NY | TCN200 | 0.461 [0.41,0.51] | 0.400 [0.34,0.47] | - | 0.408 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| B8c-TCN200-cond | +30 | NY | TCN200 | 0.446 [0.40,0.49] | 0.394 [0.33,0.45] | - | 0.393 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- B8c-GRU60-cond 10 POOLED: all configs reported
- B8c-GRU60-cond 10 ASIA: all configs reported
- B8c-GRU60-cond 10 LONDON: all configs reported
- B8c-GRU60-cond 10 NY: all configs reported
- B8c-GRU60-cond 20 POOLED: all configs reported
- B8c-GRU60-cond 20 ASIA: all configs reported
- B8c-GRU60-cond 20 LONDON: all configs reported
- B8c-GRU60-cond 20 NY: all configs reported
- B8c-GRU60-cond 30 POOLED: all configs reported
- B8c-GRU60-cond 30 ASIA: all configs reported
- B8c-GRU60-cond 30 LONDON: all configs reported
- B8c-GRU60-cond 30 NY: all configs reported
- B8c-TCN200-cond 10 POOLED: all configs reported
- B8c-TCN200-cond 10 ASIA: all configs reported
- B8c-TCN200-cond 10 LONDON: all configs reported
- B8c-TCN200-cond 10 NY: all configs reported
- B8c-TCN200-cond 20 POOLED: all configs reported
- B8c-TCN200-cond 20 ASIA: all configs reported
- B8c-TCN200-cond 20 LONDON: all configs reported
- B8c-TCN200-cond 20 NY: all configs reported
- B8c-TCN200-cond 30 POOLED: all configs reported
- B8c-TCN200-cond 30 ASIA: all configs reported
- B8c-TCN200-cond 30 LONDON: all configs reported
- B8c-TCN200-cond 30 NY: all configs reported
- B8c-CNNLSTM30-cond 10 POOLED: all configs reported
- B8c-CNNLSTM30-cond 10 ASIA: all configs reported
- B8c-CNNLSTM30-cond 10 LONDON: all configs reported
- B8c-CNNLSTM30-cond 10 NY: all configs reported
- B8c-CNNLSTM30-cond 20 POOLED: all configs reported
- B8c-CNNLSTM30-cond 20 ASIA: all configs reported
- B8c-CNNLSTM30-cond 20 LONDON: all configs reported
- B8c-CNNLSTM30-cond 20 NY: all configs reported
