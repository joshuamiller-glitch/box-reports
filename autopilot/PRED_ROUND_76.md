# PRED ROUND 76 - block A round 9 - A-r9-unlocked

Best HOLDOUT F-R AUC: +15 POOLED 0.528 [0.49,0.56] | ASIA 0.559 [0.50,0.62] | LONDON 0.546 [0.48,0.60] | NY 0.556 [0.49,0.61]
Best HOLDOUT F-R AUC: +30 POOLED 0.529 [0.50,0.56] | ASIA 0.569 [0.50,0.63] | LONDON 0.525 [0.47,0.59] | NY 0.541 [0.48,0.60]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.091 AUC, 5 of 5 economic conditions short.
not found - short by 0.091 AUC and 5 of 5 economic conditions

prereg 35359bf413e08bea191b76f7b89661c3e67267aee46c7765169c272ec0e017f1 ; trials added 1000 ; truncation audit {'decisions': 74810, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A/r4_preds_u.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-r9-unlocked | +5 | LONDON | A9_pneg|fixed | 0.520 [-,-] | 0.577 [0.51,0.64] | - | 0.578 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A8_H4|fixed | 0.547 [-,-] | 0.569 [0.50,0.63] | - | 0.562 | - | - | - | - | - | - |  | short by 0.091 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | ASIA | A6_bE|fixed | 0.532 [-,-] | 0.566 [0.51,0.63] | - | 0.560 | - | - | - | - | - | - |  | short by 0.094 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A9_pneg|fixed | 0.537 [-,-] | 0.566 [0.51,0.62] | - | 0.563 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A6_lamS|fixed | 0.538 [-,-] | 0.564 [0.49,0.62] | - | 0.568 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A9_pneg|fixed | 0.558 [-,-] | 0.563 [0.51,0.61] | - | 0.549 | - | - | - | - | - | - |  | short by 0.097 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A8_H1|fixed | 0.535 [-,-] | 0.562 [0.49,0.62] | - | 0.565 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A8_H2|fixed | 0.535 [-,-] | 0.562 [0.49,0.62] | - | 0.565 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A6_bP|fixed | 0.493 [-,-] | 0.561 [0.50,0.62] | - | 0.567 | - | - | - | - | - | - |  | short by 0.099 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A6_sP|fixed | 0.520 [-,-] | 0.559 [0.50,0.62] | - | 0.555 | - | - | - | - | - | - |  | short by 0.101 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A8_H4|fixed | 0.547 [-,-] | 0.559 [0.50,0.62] | - | 0.553 | - | - | - | - | - | - |  | short by 0.101 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A7_lamS|fixed | 0.536 [-,-] | 0.557 [0.49,0.61] | - | 0.553 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A6_bP|fixed | 0.517 [-,-] | 0.557 [0.49,0.62] | - | 0.545 | - | - | - | - | - | - |  | short by 0.103 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A8_H1|fixed | 0.525 [-,-] | 0.556 [0.49,0.61] | - | 0.543 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A8_H2|fixed | 0.525 [-,-] | 0.556 [0.49,0.61] | - | 0.543 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A7_sE|fixed | 0.554 [-,-] | 0.555 [0.50,0.61] | - | 0.540 | - | - | - | - | - | - |  | short by 0.105 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A9_q25|fixed | 0.491 [-,-] | 0.553 [0.50,0.60] | - | 0.560 | - | - | - | - | - | - |  | short by 0.107 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A7_lamS|fixed | 0.518 [-,-] | 0.551 [0.48,0.61] | - | 0.538 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A6_sP|fixed | 0.499 [-,-] | 0.550 [0.49,0.61] | - | 0.544 | - | - | - | - | - | - |  | short by 0.110 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A6_sE|fixed | 0.534 [-,-] | 0.550 [0.48,0.62] | - | 0.549 | - | - | - | - | - | - |  | short by 0.110 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A6_lamS|fixed | 0.523 [-,-] | 0.549 [0.49,0.61] | - | 0.537 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A6_sE|fixed | 0.531 [-,-] | 0.548 [0.49,0.61] | - | 0.540 | - | - | - | - | - | - |  | short by 0.112 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | LONDON | A9_pneg|fixed | 0.507 [-,-] | 0.546 [0.48,0.60] | - | 0.538 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A6_lamS|fixed | 0.522 [-,-] | 0.546 [0.49,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A8_H1|fixed | 0.519 [-,-] | 0.545 [0.49,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A8_H2|fixed | 0.519 [-,-] | 0.545 [0.49,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A7_lamS|fixed | 0.528 [-,-] | 0.543 [0.49,0.60] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A6_sE|fixed | 0.504 [-,-] | 0.543 [0.47,0.61] | - | 0.552 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A7_sP|fixed | 0.515 [-,-] | 0.543 [0.47,0.60] | - | 0.541 | - | - | - | - | - | - |  | short by 0.117 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A9_q25|fixed | 0.508 [-,-] | 0.542 [0.47,0.61] | - | 0.549 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A8_H1|fixed | 0.511 [-,-] | 0.541 [0.48,0.60] | - | 0.557 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A8_H2|fixed | 0.511 [-,-] | 0.541 [0.48,0.60] | - | 0.557 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A8_H4|fixed | 0.500 [-,-] | 0.539 [0.46,0.60] | - | 0.547 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_lamS|fixed | 0.503 [-,-] | 0.538 [0.48,0.60] | - | 0.553 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A9_pneg|fixed | 0.554 [-,-] | 0.538 [0.48,0.60] | - | 0.524 | - | - | - | - | - | - |  | short by 0.122 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A6_bE|fixed | 0.528 [-,-] | 0.537 [0.47,0.60] | - | 0.525 | - | - | - | - | - | - |  | short by 0.123 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | LONDON | A7_sP|oriented | 0.540 [-,-] | 0.536 [0.47,0.60] | - | 0.535 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A6_sE|fixed | 0.514 [-,-] | 0.536 [0.50,0.57] | - | 0.531 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A9_pneg|fixed | 0.523 [-,-] | 0.536 [0.50,0.57] | - | 0.535 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A6_bE|fixed | 0.503 [-,-] | 0.533 [0.47,0.59] | - | 0.540 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A6_sP|fixed | 0.494 [-,-] | 0.533 [0.46,0.60] | - | 0.546 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A7_sE|oriented | 0.519 [-,-] | 0.533 [0.47,0.59] | - | 0.536 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A6_sE|fixed | 0.504 [-,-] | 0.533 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A7_sP|fixed | 0.522 [-,-] | 0.532 [0.46,0.60] | - | 0.528 | - | - | - | - | - | - |  | short by 0.128 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A7_sE|fixed | 0.534 [-,-] | 0.531 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - |  | short by 0.129 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | NY | A7_lamS|fixed | 0.509 [-,-] | 0.531 [0.47,0.59] | - | 0.554 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A9_q25|fixed | 0.487 [-,-] | 0.530 [0.47,0.59] | - | 0.541 | - | - | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A9_pneg|fixed | 0.521 [-,-] | 0.529 [0.50,0.56] | - | 0.526 | - | - | - | - | - | - |  | promising: short by 0.151 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A7_sP|oriented | 0.524 [-,-] | 0.529 [0.46,0.59] | - | 0.529 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A7_sE|fixed | 0.503 [-,-] | 0.529 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A9_pneg|fixed | 0.516 [-,-] | 0.528 [0.49,0.56] | - | 0.525 | - | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A9_q25|fixed | 0.498 [-,-] | 0.528 [0.49,0.57] | - | 0.532 | - | - | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A8_H4|fixed | 0.526 [-,-] | 0.527 [0.46,0.59] | - | 0.523 | - | - | - | - | - | - |  | short by 0.133 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A6_sP|fixed | 0.495 [-,-] | 0.526 [0.48,0.57] | - | 0.523 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A6_bE|fixed | 0.492 [-,-] | 0.526 [0.45,0.59] | - | 0.523 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_sP|fixed | 0.498 [-,-] | 0.526 [0.49,0.56] | - | 0.529 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A8_H4|fixed | 0.498 [-,-] | 0.526 [0.45,0.60] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A6_bE|fixed | 0.542 [-,-] | 0.526 [0.46,0.59] | - | 0.510 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | NY | A7_sE|fixed | 0.495 [-,-] | 0.526 [0.46,0.60] | - | 0.526 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A6_sP|fixed | 0.481 [-,-] | 0.526 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A6_sE|fixed | 0.534 [-,-] | 0.525 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | LONDON | A9_pneg|fixed | 0.511 [-,-] | 0.525 [0.47,0.59] | - | 0.525 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A7_sP|fixed | 0.493 [-,-] | 0.525 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_sE|fixed | 0.512 [-,-] | 0.524 [0.49,0.56] | - | 0.527 | - | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A7_sE|fixed | 0.522 [-,-] | 0.524 [0.46,0.59] | - | 0.520 | - | - | - | - | - | - |  | short by 0.136 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A9_q25|fixed | 0.513 [-,-] | 0.524 [0.46,0.58] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A8_H4|fixed | 0.514 [-,-] | 0.524 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A6_bE|fixed | 0.505 [-,-] | 0.524 [0.49,0.55] | - | 0.521 | - | - | - | - | - | - |  | promising: short by 0.156 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A7_sE|fixed | 0.521 [-,-] | 0.523 [0.49,0.55] | - | 0.521 | - | - | - | - | - | - |  | promising: short by 0.157 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A9_pneg|fixed | 0.499 [-,-] | 0.523 [0.48,0.56] | - | 0.521 | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A7_sE|fixed | 0.533 [-,-] | 0.523 [0.45,0.60] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | ASIA | A8_H4|fixed | 0.539 [-,-] | 0.523 [0.46,0.58] | - | 0.507 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A8_H4|fixed | 0.507 [-,-] | 0.523 [0.49,0.55] | - | 0.517 | - | - | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A6_sP|oriented | 0.516 [-,-] | 0.523 [0.46,0.58] | - | 0.525 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A6_sE|fixed | 0.508 [-,-] | 0.523 [0.46,0.58] | - | 0.514 | - | - | - | - | - | - |  | short by 0.137 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A9_q25|fixed | 0.491 [-,-] | 0.522 [0.48,0.55] | - | 0.526 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A6_lamS|fixed | 0.492 [-,-] | 0.522 [0.48,0.56] | - | 0.541 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A6_bE|fixed | 0.510 [-,-] | 0.522 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A7_lamS|fixed | 0.496 [-,-] | 0.522 [0.48,0.55] | - | 0.538 | - | - | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | NY | A6_sE|fixed | 0.483 [-,-] | 0.522 [0.47,0.58] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A6_bP|fixed | 0.489 [-,-] | 0.521 [0.48,0.56] | - | 0.525 | - | - | - | - | - | - |  | promising: short by 0.159 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A7_sP|fixed | 0.505 [-,-] | 0.521 [0.48,0.56] | - | 0.524 | - | - | - | - | - | - |  | promising: short by 0.159 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A6_bP|fixed | 0.493 [-,-] | 0.521 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - |  | short by 0.139 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A8_H4|fixed | 0.510 [-,-] | 0.521 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - |  | promising: short by 0.159 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A6_bP|fixed | 0.495 [-,-] | 0.521 [0.45,0.58] | - | 0.529 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A8_H1|fixed | 0.491 [-,-] | 0.520 [0.48,0.56] | - | 0.535 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A8_H2|fixed | 0.491 [-,-] | 0.520 [0.48,0.56] | - | 0.535 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A6_bE|fixed | 0.502 [-,-] | 0.520 [0.49,0.55] | - | 0.517 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A7_lamS|fixed | 0.493 [-,-] | 0.520 [0.48,0.56] | - | 0.531 | - | - | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A6_bE|fixed | 0.518 [-,-] | 0.520 [0.45,0.58] | - | 0.502 | - | - | - | - | - | - |  | short by 0.140 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A9_pneg|fixed | 0.507 [-,-] | 0.520 [0.46,0.58] | - | 0.528 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A7_sP|fixed | 0.518 [-,-] | 0.520 [0.45,0.59] | - | 0.508 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | ASIA | A9_q25|fixed | 0.489 [-,-] | 0.519 [0.46,0.57] | - | 0.526 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | LONDON | A7_sE|fixed | 0.522 [-,-] | 0.518 [0.46,0.57] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A6_sE|fixed | 0.505 [-,-] | 0.518 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - |  | promising: short by 0.162 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A8_H1|oriented | 0.534 [-,-] | 0.517 [0.48,0.57] | - | 0.486 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | ASIA | A8_H2|oriented | 0.534 [-,-] | 0.517 [0.48,0.57] | - | 0.486 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | NY | A9_pneg|oriented | 0.513 [-,-] | 0.517 [0.46,0.58] | - | 0.510 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_sE|fixed | 0.511 [-,-] | 0.517 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_bP|oriented | 0.532 [-,-] | 0.517 [0.45,0.57] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A8_H1|oriented | 0.549 [-,-] | 0.516 [0.46,0.57] | - | 0.485 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | ASIA | A8_H2|oriented | 0.549 [-,-] | 0.516 [0.46,0.57] | - | 0.485 | - | - | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A6_sP|fixed | 0.509 [-,-] | 0.516 [0.45,0.57] | - | 0.496 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A8_H4|fixed | 0.504 [-,-] | 0.516 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - |  | short by 0.164 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A8_H4|fixed | 0.501 [-,-] | 0.516 [0.46,0.57] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A6_lamS|oriented | 0.538 [-,-] | 0.516 [0.47,0.57] | - | 0.484 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | ASIA | A8_H1|oriented | 0.539 [-,-] | 0.515 [0.47,0.56] | - | 0.491 | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A8_H2|oriented | 0.539 [-,-] | 0.515 [0.47,0.56] | - | 0.491 | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A6_lamS|fixed | 0.486 [-,-] | 0.515 [0.47,0.55] | - | 0.529 | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A8_H1|oriented | 0.539 [-,-] | 0.515 [0.47,0.56] | - | 0.491 | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A8_H2|oriented | 0.539 [-,-] | 0.515 [0.47,0.56] | - | 0.491 | - | - | - | - | - | - |  | short by 0.145 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A7_lamS|fixed | 0.489 [-,-] | 0.515 [0.47,0.55] | - | 0.536 | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A9_pneg|fixed | 0.520 [-,-] | 0.515 [0.45,0.59] | - | 0.505 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A6_sE|fixed | 0.491 [-,-] | 0.515 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A6_lamS|fixed | 0.483 [-,-] | 0.515 [0.46,0.58] | - | 0.533 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A6_lamS|oriented | 0.518 [-,-] | 0.514 [0.46,0.57] | - | 0.510 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_lamS|fixed | 0.487 [-,-] | 0.514 [0.47,0.55] | - | 0.526 | - | - | - | - | - | - |  | short by 0.166 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A9_q25|fixed | 0.496 [-,-] | 0.514 [0.46,0.57] | - | 0.522 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A7_lamS|oriented | 0.544 [-,-] | 0.514 [0.46,0.57] | - | 0.478 | - | - | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A6_bP|fixed | 0.511 [-,-] | 0.514 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | LONDON | A8_H1|oriented | 0.527 [-,-] | 0.514 [0.45,0.57] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A8_H2|oriented | 0.527 [-,-] | 0.514 [0.45,0.57] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A6_sP|fixed | 0.487 [-,-] | 0.513 [0.48,0.54] | - | 0.512 | - | - | - | - | - | - |  | promising: short by 0.167 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | POOLED | A7_sE|fixed | 0.510 [-,-] | 0.513 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - |  | short by 0.167 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A8_H1|fixed | 0.478 [-,-] | 0.513 [0.46,0.58] | - | 0.525 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A8_H2|fixed | 0.478 [-,-] | 0.513 [0.46,0.58] | - | 0.525 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A7_sP|fixed | 0.497 [-,-] | 0.513 [0.44,0.58] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A8_H4|oriented | 0.505 [-,-] | 0.512 [0.46,0.57] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_bE|fixed | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - |  | short by 0.168 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A6_sE|fixed | 0.480 [-,-] | 0.512 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A8_H1|fixed | 0.486 [-,-] | 0.511 [0.47,0.55] | - | 0.521 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | POOLED | A8_H2|fixed | 0.486 [-,-] | 0.511 [0.47,0.55] | - | 0.521 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A8_H1|fixed | 0.485 [-,-] | 0.511 [0.47,0.54] | - | 0.520 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | POOLED | A8_H2|fixed | 0.485 [-,-] | 0.511 [0.47,0.54] | - | 0.520 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A7_sP|fixed | 0.499 [-,-] | 0.511 [0.44,0.58] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A9_pneg|oriented | 0.535 [-,-] | 0.511 [0.45,0.57] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_bP|fixed | 0.494 [-,-] | 0.511 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A9_q25|oriented | 0.510 [-,-] | 0.511 [0.45,0.57] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_sP|fixed | 0.486 [-,-] | 0.511 [0.44,0.57] | - | 0.513 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A7_lamS|oriented | 0.533 [-,-] | 0.511 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A6_bP|fixed | 0.481 [-,-] | 0.511 [0.47,0.55] | - | 0.511 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A6_lamS|oriented | 0.539 [-,-] | 0.510 [0.46,0.56] | - | 0.475 | - | - | - | - | - | - |  | short by 0.150 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A7_sE|oriented | 0.518 [-,-] | 0.510 [0.44,0.58] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A6_bP|fixed | 0.492 [-,-] | 0.510 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A6_lamS|fixed | 0.480 [-,-] | 0.510 [0.45,0.58] | - | 0.521 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_sP|oriented | 0.542 [-,-] | 0.510 [0.45,0.56] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A7_sP|oriented | 0.520 [-,-] | 0.510 [0.44,0.58] | - | 0.507 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A8_H4|fixed | 0.481 [-,-] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A7_lamS|fixed | 0.482 [-,-] | 0.510 [0.47,0.55] | - | 0.523 | - | - | - | - | - | - |  | short by 0.170 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A7_sP|oriented | 0.528 [-,-] | 0.509 [0.45,0.56] | - | 0.516 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A6_sP|fixed | 0.489 [-,-] | 0.509 [0.45,0.57] | - | 0.494 | - | - | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A9_q25|fixed | 0.493 [-,-] | 0.509 [0.47,0.55] | - | 0.513 | - | - | - | - | - | - |  | short by 0.171 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A9_q25|oriented | 0.522 [-,-] | 0.509 [0.45,0.56] | - | 0.508 | - | - | - | - | - | - |  | short by 0.151 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A6_bE|fixed | 0.495 [-,-] | 0.509 [0.44,0.58] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A7_lamS|fixed | 0.479 [-,-] | 0.509 [0.45,0.57] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A6_bP|oriented | 0.522 [-,-] | 0.508 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A9_pneg|oriented | 0.515 [-,-] | 0.508 [0.44,0.57] | - | 0.501 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A8_H4|fixed | 0.492 [-,-] | 0.508 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A7_sE|fixed | 0.508 [-,-] | 0.508 [0.47,0.55] | - | 0.508 | - | - | - | - | - | - |  | short by 0.172 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A6_bP|fixed | 0.480 [-,-] | 0.508 [0.43,0.58] | - | 0.510 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A6_sE|fixed | 0.492 [-,-] | 0.508 [0.44,0.58] | - | 0.505 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A6_bP|oriented | 0.504 [-,-] | 0.507 [0.43,0.58] | - | 0.512 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A9_q25|fixed | 0.501 [-,-] | 0.507 [0.43,0.58] | - | 0.494 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_sP|fixed | 0.478 [-,-] | 0.507 [0.46,0.56] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A8_H1|oriented | 0.526 [-,-] | 0.507 [0.44,0.56] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A8_H2|oriented | 0.526 [-,-] | 0.507 [0.44,0.56] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A6_sP|fixed | 0.489 [-,-] | 0.507 [0.43,0.57] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A7_sE|fixed | 0.502 [-,-] | 0.507 [0.47,0.54] | - | 0.508 | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A6_bP|oriented | 0.532 [-,-] | 0.507 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A6_lamS|fixed | 0.483 [-,-] | 0.507 [0.47,0.54] | - | 0.521 | - | - | - | - | - | - |  | short by 0.173 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A6_lamS|oriented | 0.536 [-,-] | 0.506 [0.46,0.56] | - | 0.477 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A9_q25|oriented | 0.525 [-,-] | 0.506 [0.45,0.57] | - | 0.520 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A7_lamS|fixed | 0.479 [-,-] | 0.506 [0.46,0.56] | - | 0.529 | - | - | - | - | - | - |  | short by 0.154 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | POOLED | A7_sP|oriented | 0.517 [-,-] | 0.506 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - |  | short by 0.174 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A8_H4|fixed | 0.483 [-,-] | 0.506 [0.43,0.57] | - | 0.506 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_bP|fixed | 0.493 [-,-] | 0.505 [0.44,0.56] | - | 0.514 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A6_lamS|oriented | 0.542 [-,-] | 0.505 [0.45,0.56] | - | 0.474 | - | - | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A8_H1|fixed | 0.482 [-,-] | 0.505 [0.47,0.54] | - | 0.518 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A8_H2|fixed | 0.482 [-,-] | 0.505 [0.47,0.54] | - | 0.518 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | ASIA | A7_sP|fixed | 0.490 [-,-] | 0.505 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - |  | short by 0.155 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A6_bE|oriented | 0.505 [-,-] | 0.505 [0.43,0.58] | - | 0.505 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A7_sP|fixed | 0.495 [-,-] | 0.505 [0.47,0.54] | - | 0.505 | - | - | - | - | - | - |  | short by 0.175 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A7_lamS|fixed | 0.480 [-,-] | 0.504 [0.44,0.57] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_bE|fixed | 0.496 [-,-] | 0.504 [0.45,0.56] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A7_sP|fixed | 0.492 [-,-] | 0.503 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - |  | short by 0.177 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A6_bE|fixed | 0.491 [-,-] | 0.503 [0.45,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_bE|oriented | 0.509 [-,-] | 0.503 [0.43,0.57] | - | 0.511 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_bE|fixed | 0.490 [-,-] | 0.503 [0.44,0.56] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A7_sP|fixed | 0.499 [-,-] | 0.502 [0.45,0.56] | - | 0.504 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A6_sP|fixed | 0.472 [-,-] | 0.502 [0.47,0.53] | - | 0.500 | - | - | - | - | - | - |  | short by 0.178 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | NY | A7_sE|oriented | 0.507 [-,-] | 0.502 [0.44,0.55] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A7_sE|fixed | 0.505 [-,-] | 0.502 [0.46,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A9_q25|oriented | 0.516 [-,-] | 0.501 [0.44,0.57] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A7_lamS|fixed | 0.461 [-,-] | 0.501 [0.44,0.56] | - | 0.536 | - | - | - | - | - | - |  | short by 0.159 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A6_bP|oriented | 0.530 [-,-] | 0.501 [0.44,0.56] | - | 0.507 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A7_lamS|fixed | 0.481 [-,-] | 0.501 [0.44,0.56] | - | 0.509 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A9_q25|oriented | 0.506 [-,-] | 0.501 [0.44,0.57] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_lamS|fixed | 0.479 [-,-] | 0.501 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A9_q25|oriented | 0.513 [-,-] | 0.501 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - |  | short by 0.179 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A8_H1|oriented | 0.523 [-,-] | 0.500 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A8_H2|oriented | 0.523 [-,-] | 0.500 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A7_lamS|fixed | 0.477 [-,-] | 0.500 [0.44,0.55] | - | 0.538 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | LONDON | A6_sE|oriented | 0.516 [-,-] | 0.500 [0.44,0.55] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A6_sP|fixed | 0.470 [-,-] | 0.500 [0.43,0.57] | - | 0.501 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A6_sP|oriented | 0.530 [-,-] | 0.500 [0.43,0.57] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_sE|fixed | 0.484 [-,-] | 0.500 [0.45,0.56] | - | 0.502 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A7_lamS|oriented | 0.523 [-,-] | 0.500 [0.45,0.56] | - | 0.462 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | LONDON | A8_H1|fixed | 0.477 [-,-] | 0.500 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A8_H2|fixed | 0.477 [-,-] | 0.500 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A9_q25|fixed | 0.487 [-,-] | 0.499 [0.46,0.54] | - | 0.501 | - | - | - | - | - | - |  | short by 0.181 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | LONDON | A6_lamS|oriented | 0.521 [-,-] | 0.499 [0.43,0.56] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A9_q25|fixed | 0.494 [-,-] | 0.499 [0.43,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A7_lamS|oriented | 0.519 [-,-] | 0.499 [0.44,0.56] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_bP|fixed | 0.470 [-,-] | 0.499 [0.44,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A7_lamS|oriented | 0.539 [-,-] | 0.499 [0.44,0.56] | - | 0.464 | - | - | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | LONDON | A9_q25|fixed | 0.484 [-,-] | 0.499 [0.43,0.56] | - | 0.508 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A7_sE|fixed | 0.493 [-,-] | 0.498 [0.45,0.56] | - | 0.503 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A9_pneg|fixed | 0.508 [-,-] | 0.498 [0.45,0.55] | - | 0.489 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A6_sP|oriented | 0.528 [-,-] | 0.498 [0.47,0.53] | - | 0.500 | - | - | - | - | - | - |  | short by 0.182 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | NY | A7_sP|oriented | 0.501 [-,-] | 0.498 [0.44,0.55] | - | 0.496 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_bE|oriented | 0.510 [-,-] | 0.497 [0.44,0.56] | - | 0.496 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_bE|fixed | 0.491 [-,-] | 0.497 [0.43,0.57] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A6_bE|oriented | 0.509 [-,-] | 0.497 [0.44,0.55] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A7_sP|oriented | 0.508 [-,-] | 0.497 [0.46,0.53] | - | 0.496 | - | - | - | - | - | - |  | short by 0.183 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | LONDON | A6_bE|oriented | 0.504 [-,-] | 0.496 [0.44,0.55] | - | 0.492 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A7_lamS|oriented | 0.520 [-,-] | 0.496 [0.43,0.56] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A7_sP|oriented | 0.505 [-,-] | 0.495 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - |  | short by 0.185 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A6_bE|fixed | 0.495 [-,-] | 0.495 [0.42,0.57] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A7_sP|oriented | 0.510 [-,-] | 0.495 [0.43,0.56] | - | 0.497 | - | - | - | - | - | - |  | short by 0.165 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A8_H1|oriented | 0.518 [-,-] | 0.495 [0.46,0.53] | - | 0.482 | - | - | - | - | - | - |  | short by 0.185 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A8_H2|oriented | 0.518 [-,-] | 0.495 [0.46,0.53] | - | 0.482 | - | - | - | - | - | - |  | short by 0.185 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | ASIA | A6_lamS|fixed | 0.458 [-,-] | 0.495 [0.44,0.55] | - | 0.526 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | LONDON | A7_sE|fixed | 0.507 [-,-] | 0.495 [0.44,0.55] | - | 0.477 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_bP|oriented | 0.507 [-,-] | 0.495 [0.44,0.56] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A8_H4|oriented | 0.517 [-,-] | 0.494 [0.43,0.57] | - | 0.494 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A7_sP|fixed | 0.483 [-,-] | 0.494 [0.46,0.53] | - | 0.498 | - | - | - | - | - | - |  | short by 0.186 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A7_lamS|oriented | 0.521 [-,-] | 0.494 [0.44,0.54] | - | 0.471 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | NY | A9_q25|fixed | 0.475 [-,-] | 0.494 [0.43,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | ASIA | A6_lamS|fixed | 0.464 [-,-] | 0.494 [0.44,0.54] | - | 0.523 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | POOLED | A6_lamS|oriented | 0.517 [-,-] | 0.493 [0.46,0.53] | - | 0.479 | - | - | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A6_bP|fixed | 0.468 [-,-] | 0.493 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A7_sE|oriented | 0.498 [-,-] | 0.493 [0.46,0.53] | - | 0.492 | - | - | - | - | - | - |  | short by 0.187 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | NY | A6_sP|oriented | 0.511 [-,-] | 0.493 [0.43,0.57] | - | 0.500 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A8_H1|fixed | 0.474 [-,-] | 0.493 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A8_H2|fixed | 0.474 [-,-] | 0.493 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_sP|oriented | 0.522 [-,-] | 0.493 [0.44,0.54] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A6_bP|fixed | 0.496 [-,-] | 0.493 [0.42,0.57] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A6_sE|oriented | 0.508 [-,-] | 0.492 [0.42,0.56] | - | 0.495 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A6_bP|oriented | 0.520 [-,-] | 0.492 [0.42,0.57] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A8_H4|oriented | 0.508 [-,-] | 0.492 [0.43,0.55] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A9_pneg|fixed | 0.485 [-,-] | 0.492 [0.43,0.56] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A6_bP|fixed | 0.478 [-,-] | 0.492 [0.42,0.56] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A7_lamS|oriented | 0.521 [-,-] | 0.491 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A6_bE|oriented | 0.505 [-,-] | 0.491 [0.42,0.56] | - | 0.498 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A9_q25|fixed | 0.478 [-,-] | 0.491 [0.44,0.55] | - | 0.492 | - | - | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A9_q25|oriented | 0.507 [-,-] | 0.491 [0.45,0.53] | - | 0.487 | - | - | - | - | - | - |  | short by 0.189 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A6_sP|oriented | 0.511 [-,-] | 0.491 [0.43,0.55] | - | 0.506 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | LONDON | A7_sP|fixed | 0.472 [-,-] | 0.491 [0.44,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A7_lamS|oriented | 0.518 [-,-] | 0.490 [0.45,0.53] | - | 0.477 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | LONDON | A8_H4|oriented | 0.519 [-,-] | 0.490 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A7_sP|fixed | 0.480 [-,-] | 0.490 [0.42,0.56] | - | 0.493 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_sP|fixed | 0.458 [-,-] | 0.490 [0.44,0.55] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | LONDON | A6_lamS|oriented | 0.520 [-,-] | 0.490 [0.42,0.55] | - | 0.479 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A6_bP|oriented | 0.508 [-,-] | 0.490 [0.45,0.53] | - | 0.491 | - | - | - | - | - | - |  | short by 0.190 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A7_sE|fixed | 0.482 [-,-] | 0.490 [0.42,0.56] | - | 0.489 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A6_lamS|fixed | 0.461 [-,-] | 0.490 [0.44,0.54] | - | 0.525 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A6_bP|oriented | 0.519 [-,-] | 0.489 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | LONDON | A7_lamS|fixed | 0.467 [-,-] | 0.489 [0.43,0.55] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A6_sP|oriented | 0.514 [-,-] | 0.489 [0.43,0.56] | - | 0.487 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A9_q25|fixed | 0.490 [-,-] | 0.489 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_bP|oriented | 0.506 [-,-] | 0.489 [0.45,0.52] | - | 0.487 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A9_pneg|fixed | 0.465 [-,-] | 0.489 [0.43,0.55] | - | 0.497 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A7_sP|oriented | 0.501 [-,-] | 0.489 [0.42,0.56] | - | 0.488 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A8_H1|oriented | 0.515 [-,-] | 0.489 [0.46,0.53] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| A-r9-unlocked | +5 | POOLED | A8_H2|oriented | 0.515 [-,-] | 0.489 [0.46,0.53] | - | 0.480 | - | - | - | - | - | - |  | WF-only (dead) |
| A-r9-unlocked | +15 | POOLED | A8_H1|oriented | 0.514 [-,-] | 0.489 [0.45,0.53] | - | 0.479 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | POOLED | A8_H2|oriented | 0.514 [-,-] | 0.489 [0.45,0.53] | - | 0.479 | - | - | - | - | - | - |  | short by 0.191 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A6_sE|oriented | 0.520 [-,-] | 0.488 [0.42,0.56] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A8_H4|fixed | 0.495 [-,-] | 0.488 [0.43,0.54] | - | 0.491 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A7_sP|oriented | 0.503 [-,-] | 0.487 [0.42,0.56] | - | 0.486 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A8_H1|oriented | 0.522 [-,-] | 0.487 [0.42,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A8_H2|oriented | 0.522 [-,-] | 0.487 [0.42,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A6_sP|oriented | 0.513 [-,-] | 0.487 [0.46,0.52] | - | 0.488 | - | - | - | - | - | - |  | short by 0.193 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A8_H1|fixed | 0.473 [-,-] | 0.486 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A8_H2|fixed | 0.473 [-,-] | 0.486 [0.43,0.55] | - | 0.484 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | ASIA | A7_lamS|fixed | 0.456 [-,-] | 0.486 [0.43,0.54] | - | 0.522 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | LONDON | A9_q25|oriented | 0.504 [-,-] | 0.486 [0.43,0.54] | - | 0.478 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_lamS|oriented | 0.513 [-,-] | 0.486 [0.45,0.53] | - | 0.474 | - | - | - | - | - | - |  | short by 0.194 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | LONDON | A6_lamS|fixed | 0.482 [-,-] | 0.486 [0.43,0.54] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A6_lamS|oriented | 0.517 [-,-] | 0.485 [0.42,0.54] | - | 0.467 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A6_sE|oriented | 0.509 [-,-] | 0.485 [0.45,0.52] | - | 0.486 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | LONDON | A8_H4|fixed | 0.496 [-,-] | 0.485 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A7_lamS|oriented | 0.511 [-,-] | 0.485 [0.45,0.53] | - | 0.464 | - | - | - | - | - | - |  | short by 0.195 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A8_H1|fixed | 0.461 [-,-] | 0.485 [0.44,0.53] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | ASIA | A8_H2|fixed | 0.461 [-,-] | 0.485 [0.44,0.53] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A6_lamS|oriented | 0.514 [-,-] | 0.485 [0.45,0.53] | - | 0.471 | - | - | - | - | - | - |  | WF-only (dead) |
| A-r9-unlocked | +15 | ASIA | A8_H1|fixed | 0.461 [-,-] | 0.485 [0.44,0.53] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | ASIA | A8_H2|fixed | 0.461 [-,-] | 0.485 [0.44,0.53] | - | 0.509 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | ASIA | A6_lamS|fixed | 0.462 [-,-] | 0.484 [0.43,0.53] | - | 0.516 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | LONDON | A8_H4|oriented | 0.499 [-,-] | 0.484 [0.43,0.54] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A8_H4|oriented | 0.496 [-,-] | 0.484 [0.45,0.52] | - | 0.485 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | LONDON | A6_sE|fixed | 0.502 [-,-] | 0.484 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A8_H1|fixed | 0.451 [-,-] | 0.484 [0.43,0.54] | - | 0.515 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | ASIA | A8_H2|fixed | 0.451 [-,-] | 0.484 [0.43,0.54] | - | 0.515 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | LONDON | A6_bP|fixed | 0.468 [-,-] | 0.483 [0.43,0.55] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A9_pneg|fixed | 0.487 [-,-] | 0.483 [0.42,0.54] | - | 0.490 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | ASIA | A8_H1|fixed | 0.466 [-,-] | 0.483 [0.43,0.52] | - | 0.514 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | ASIA | A8_H2|fixed | 0.466 [-,-] | 0.483 [0.43,0.52] | - | 0.514 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | POOLED | A6_sE|oriented | 0.495 [-,-] | 0.482 [0.45,0.52] | - | 0.484 | - | - | - | - | - | - |  | short by 0.198 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | ASIA | A9_q25|oriented | 0.511 [-,-] | 0.481 [0.43,0.54] | - | 0.474 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | NY | A9_pneg|oriented | 0.493 [-,-] | 0.480 [0.42,0.54] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | POOLED | A7_lamS|oriented | 0.507 [-,-] | 0.480 [0.44,0.52] | - | 0.469 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A6_bE|oriented | 0.498 [-,-] | 0.480 [0.45,0.51] | - | 0.483 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A8_H1|oriented | 0.509 [-,-] | 0.480 [0.44,0.52] | - | 0.465 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A8_H2|oriented | 0.509 [-,-] | 0.480 [0.44,0.52] | - | 0.465 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | NY | A6_bP|oriented | 0.505 [-,-] | 0.479 [0.42,0.55] | - | 0.471 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | POOLED | A8_H4|oriented | 0.490 [-,-] | 0.479 [0.44,0.51] | - | 0.478 | - | - | - | - | - | - |  | short by 0.201 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | ASIA | A6_bP|oriented | 0.507 [-,-] | 0.479 [0.42,0.55] | - | 0.490 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | POOLED | A7_sP|oriented | 0.495 [-,-] | 0.479 [0.44,0.52] | - | 0.476 | - | - | - | - | - | - |  | short by 0.201 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | POOLED | A6_bP|oriented | 0.511 [-,-] | 0.479 [0.44,0.52] | - | 0.475 | - | - | - | - | - | - |  | short by 0.201 AUC, 5 of 5 econ |
| A-r9-unlocked | +30 | NY | A6_sE|oriented | 0.517 [-,-] | 0.478 [0.42,0.53] | - | 0.480 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A7_lamS|oriented | 0.504 [-,-] | 0.478 [0.45,0.52] | - | 0.462 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A6_bE|oriented | 0.490 [-,-] | 0.478 [0.44,0.51] | - | 0.481 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A6_lamS|oriented | 0.508 [-,-] | 0.478 [0.44,0.52] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A9_q25|oriented | 0.509 [-,-] | 0.478 [0.45,0.52] | - | 0.474 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | ASIA | A6_sE|oriented | 0.492 [-,-] | 0.477 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | LONDON | A6_sP|fixed | 0.484 [-,-] | 0.477 [0.42,0.54] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A8_H4|oriented | 0.493 [-,-] | 0.477 [0.45,0.51] | - | 0.483 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | POOLED | A9_pneg|oriented | 0.501 [-,-] | 0.477 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | POOLED | A6_bE|oriented | 0.495 [-,-] | 0.476 [0.45,0.51] | - | 0.479 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| A-r9-unlocked | +15 | POOLED | A6_sE|oriented | 0.488 [-,-] | 0.476 [0.44,0.51] | - | 0.473 | - | - | - | - | - | - |  | short by 0.204 AUC, 5 of 5 econ |
| A-r9-unlocked | pre | NY | A7_sP|oriented | 0.507 [-,-] | 0.475 [0.40,0.54] | - | 0.473 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | LONDON | A9_pneg|oriented | 0.489 [-,-] | 0.475 [0.41,0.53] | - | 0.475 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A6_sP|oriented | 0.519 [-,-] | 0.474 [0.41,0.54] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A7_sE|oriented | 0.505 [-,-] | 0.474 [0.40,0.54] | - | 0.474 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | NY | A8_H4|oriented | 0.502 [-,-] | 0.474 [0.40,0.55] | - | 0.476 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | POOLED | A6_sP|oriented | 0.502 [-,-] | 0.474 [0.44,0.51] | - | 0.471 | - | - | - | - | - | - |  | short by 0.206 AUC, 5 of 5 econ |
| A-r9-unlocked | +5 | NY | A6_bE|oriented | 0.508 [-,-] | 0.474 [0.41,0.55] | - | 0.477 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A6_sP|oriented | 0.505 [-,-] | 0.474 [0.43,0.52] | - | 0.477 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | POOLED | A9_q25|oriented | 0.502 [-,-] | 0.472 [0.43,0.51] | - | 0.468 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | POOLED | A9_pneg|oriented | 0.484 [-,-] | 0.472 [0.44,0.51] | - | 0.475 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | NY | A7_sE|oriented | 0.497 [-,-] | 0.471 [0.41,0.54] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | LONDON | A7_sP|fixed | 0.476 [-,-] | 0.471 [0.41,0.54] | - | 0.471 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A9_q25|oriented | 0.513 [-,-] | 0.470 [0.41,0.53] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | LONDON | A6_sE|oriented | 0.496 [-,-] | 0.467 [0.41,0.52] | - | 0.472 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A7_sE|fixed | 0.481 [-,-] | 0.467 [0.41,0.53] | - | 0.464 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A6_sP|oriented | 0.506 [-,-] | 0.467 [0.40,0.54] | - | 0.454 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A6_bE|oriented | 0.497 [-,-] | 0.467 [0.41,0.53] | - | 0.460 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | POOLED | A6_sE|oriented | 0.486 [-,-] | 0.464 [0.43,0.50] | - | 0.469 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | LONDON | A7_sP|fixed | 0.460 [-,-] | 0.464 [0.40,0.53] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | NY | A6_lamS|oriented | 0.497 [-,-] | 0.462 [0.40,0.52] | - | 0.447 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A8_H4|oriented | 0.500 [-,-] | 0.461 [0.40,0.54] | - | 0.453 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | pre | NY | A9_q25|oriented | 0.492 [-,-] | 0.458 [0.39,0.53] | - | 0.451 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A7_sP|oriented | 0.485 [-,-] | 0.457 [0.40,0.53] | - | 0.459 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | pre | NY | A6_sE|oriented | 0.496 [-,-] | 0.457 [0.39,0.53] | - | 0.448 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A8_H1|oriented | 0.481 [-,-] | 0.455 [0.40,0.51] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +5 | NY | A8_H2|oriented | 0.481 [-,-] | 0.455 [0.40,0.51] | - | 0.465 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +15 | LONDON | A9_pneg|oriented | 0.493 [-,-] | 0.454 [0.40,0.52] | - | 0.462 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| A-r9-unlocked | +30 | ASIA | A6_sP|oriented | 0.501 [-,-] | 0.450 [0.39,0.51] | - | 0.456 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | ASIA | A9_q25|oriented | 0.509 [-,-] | 0.447 [0.40,0.50] | - | 0.440 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +15 | ASIA | A6_sP|oriented | 0.480 [-,-] | 0.441 [0.38,0.50] | - | 0.445 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | ASIA | A6_bP|oriented | 0.507 [-,-] | 0.439 [0.38,0.50] | - | 0.433 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +30 | ASIA | A6_bE|oriented | 0.468 [-,-] | 0.434 [0.37,0.49] | - | 0.440 | - | - | - | - | - | - |  | dead (no gain over baseline) |
| A-r9-unlocked | +5 | LONDON | A9_pneg|oriented | 0.480 [-,-] | 0.423 [0.36,0.49] | - | 0.422 | - | - | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 POOLED: R0u_B strata hold 0.464
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 ASIA: R0u_B strata hold 0.490
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 LONDON: R0u_B strata hold 0.448
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 0 NY: R0u_B strata hold 0.455
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 POOLED: R0u_B strata hold 0.469
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 ASIA: R0u_B strata hold 0.464
- A-r9-unlocked 5 LONDON: R0u_B strata hold 0.494
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 5 NY: R0u_B strata hold 0.447
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 POOLED: R0u_B strata hold 0.443
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 ASIA: R0u_B strata hold 0.458
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 LONDON: R0u_B strata hold 0.425
- A-r9-unlocked 15 NY: R0u_B strata hold 0.452
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 POOLED: R0u_B strata hold 0.437
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 ASIA: R0u_B strata hold 0.463
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 LONDON: R0u_B strata hold 0.444
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
- A-r9-unlocked 30 NY: R0u_B strata hold 0.404
