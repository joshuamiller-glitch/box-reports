# PRED ROUND 81 - block X3 round 11 - X3 round 11

Best HOLDOUT F-R AUC: +15 POOLED 0.529 [0.49,0.57] | ASIA 0.560 [0.50,0.62] | LONDON 0.555 [0.48,0.62] | NY 0.541 [0.47,0.61]
Best HOLDOUT F-R AUC: +30 POOLED 0.534 [0.50,0.57] | ASIA 0.564 [0.50,0.62] | LONDON 0.573 [0.52,0.64] | NY 0.537 [0.48,0.60]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.091 AUC, 5 of 5 economic conditions short.
not found - short by 0.091 AUC and 5 of 5 economic conditions

prereg 492d69a924b76bd642da16cf935c2b39262c1a5b9ab2cddcab837ce9fee88fad ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X50a | +30 | LONDON | X50a | 0.523 [-,-] | 0.573 [0.52,0.64] | - | 0.574 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | pre | ASIA | X50a | 0.544 [-,-] | 0.569 [0.50,0.63] | - | 0.563 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| X49 | +30 | ASIA | X49 | 0.533 [-,-] | 0.564 [0.50,0.62] | - | 0.554 | - | - | - | - | - | - | stack | short by 0.096 AUC, 5 of 5 econ |
| X50a | +15 | ASIA | X50a | 0.546 [-,-] | 0.560 [0.50,0.62] | - | 0.546 | - | - | - | - | - | - | stack | short by 0.100 AUC, 5 of 5 econ |
| X50 | pre | NY | X50b | 0.523 [-,-] | 0.557 [0.49,0.62] | - | 0.574 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +15 | LONDON | X48 | 0.518 [-,-] | 0.555 [0.48,0.62] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +15 | LONDON | X49 | 0.503 [-,-] | 0.554 [0.50,0.61] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +15 | ASIA | X50b | 0.532 [-,-] | 0.551 [0.50,0.61] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| X50 | pre | ASIA | X50b | 0.543 [-,-] | 0.550 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - | stack | short by 0.110 AUC, 5 of 5 econ |
| X49 | +5 | LONDON | X49 | 0.512 [-,-] | 0.549 [0.48,0.61] | - | 0.548 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +30 | ASIA | X50a | 0.559 [-,-] | 0.549 [0.49,0.61] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.111 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | pre | POOLED | X50b | 0.528 [-,-] | 0.543 [0.51,0.58] | - | 0.543 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| X47 | +15 | NY | X47 | 0.517 [-,-] | 0.541 [0.47,0.61] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X49 | pre | ASIA | X49 | 0.549 [-,-] | 0.538 [0.47,0.62] | - | 0.537 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X48 | +30 | NY | X48 | 0.501 [-,-] | 0.537 [0.48,0.60] | - | 0.541 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X50a | +30 | POOLED | X50a | 0.530 [-,-] | 0.534 [0.50,0.57] | - | 0.534 | - | - | - | - | - | - | stack | promising: short by 0.146 AUC, 5 of 5 econ |
| X48 | pre | LONDON | X48 | 0.521 [-,-] | 0.534 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X47 | +30 | NY | X47 | 0.490 [-,-] | 0.533 [0.47,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X47 | pre | ASIA | X47 | 0.506 [-,-] | 0.531 [0.49,0.59] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X49 | pre | NY | X49 | 0.505 [-,-] | 0.530 [0.46,0.58] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +30 | POOLED | X49 | 0.510 [-,-] | 0.530 [0.50,0.56] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.150 AUC, 5 of 5 econ |
| X48 | +30 | POOLED | X48 | 0.521 [-,-] | 0.530 [0.50,0.56] | - | 0.527 | - | - | - | - | - | - | stack | promising: short by 0.150 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +15 | POOLED | X49 | 0.511 [-,-] | 0.529 [0.49,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X50 | +5 | ASIA | X50b | 0.531 [-,-] | 0.528 [0.48,0.59] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| X50 | +30 | LONDON | X50b | 0.507 [-,-] | 0.527 [0.46,0.60] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +30 | ASIA | X48 | 0.548 [-,-] | 0.527 [0.47,0.58] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| X48 | +15 | POOLED | X48 | 0.522 [-,-] | 0.527 [0.49,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X47 | +30 | POOLED | X47 | 0.502 [-,-] | 0.526 [0.49,0.57] | - | 0.522 | - | - | - | - | - | - | stack | promising: short by 0.154 AUC, 5 of 5 econ |
| X48 | pre | POOLED | X48 | 0.520 [-,-] | 0.526 [0.49,0.56] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X46 | +15 | LONDON | X46 | 0.487 [-,-] | 0.526 [0.45,0.59] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | pre | POOLED | X50a | 0.511 [-,-] | 0.525 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X48 | pre | NY | X48 | 0.506 [-,-] | 0.524 [0.47,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +30 | LONDON | X49 | 0.505 [-,-] | 0.524 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +5 | ASIA | X48 | 0.534 [-,-] | 0.522 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X47 | +30 | LONDON | X47 | 0.499 [-,-] | 0.522 [0.46,0.58] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +15 | ASIA | X48 | 0.533 [-,-] | 0.522 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X49 | +15 | ASIA | X49 | 0.525 [-,-] | 0.522 [0.45,0.59] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X50 | +15 | POOLED | X50b | 0.517 [-,-] | 0.522 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X49 | pre | POOLED | X49 | 0.518 [-,-] | 0.521 [0.48,0.56] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +30 | LONDON | X48 | 0.509 [-,-] | 0.520 [0.45,0.59] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +30 | POOLED | X50b | 0.514 [-,-] | 0.520 [0.49,0.55] | - | 0.518 | - | - | - | - | - | - | stack | promising: short by 0.160 AUC, 5 of 5 econ |
| X48 | +5 | LONDON | X48 | 0.512 [-,-] | 0.520 [0.45,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X47 | +15 | LONDON | X47 | 0.484 [-,-] | 0.519 [0.46,0.57] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | pre | ASIA | X48 | 0.536 [-,-] | 0.518 [0.45,0.59] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | +30 | ASIA | X46 | 0.526 [-,-] | 0.518 [0.48,0.55] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X47 | +30 | ASIA | X47 | 0.515 [-,-] | 0.518 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X50 | pre | LONDON | X50b | 0.514 [-,-] | 0.516 [0.46,0.57] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +15 | LONDON | X50b | 0.509 [-,-] | 0.516 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +15 | POOLED | X50a | 0.511 [-,-] | 0.516 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X47 | +5 | ASIA | X47 | 0.506 [-,-] | 0.515 [0.47,0.57] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X47 | pre | NY | X47 | 0.515 [-,-] | 0.514 [0.44,0.58] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | +30 | LONDON | X46 | 0.512 [-,-] | 0.514 [0.46,0.57] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +30 | ASIA | X50b | 0.541 [-,-] | 0.513 [0.46,0.57] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X46 | +5 | NY | X46 | 0.477 [-,-] | 0.511 [0.46,0.56] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +5 | LONDON | X50b | 0.508 [-,-] | 0.511 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X47 | +15 | POOLED | X47 | 0.500 [-,-] | 0.511 [0.46,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X48 | +15 | NY | X48 | 0.515 [-,-] | 0.509 [0.46,0.56] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +5 | POOLED | X49 | 0.502 [-,-] | 0.509 [0.47,0.54] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X50 | +5 | POOLED | X50b | 0.502 [-,-] | 0.509 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X47 | pre | POOLED | X47 | 0.497 [-,-] | 0.509 [0.48,0.54] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X50 | +30 | NY | X50b | 0.483 [-,-] | 0.507 [0.44,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +5 | ASIA | X50a | 0.520 [-,-] | 0.507 [0.46,0.56] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X49 | +15 | NY | X49 | 0.501 [-,-] | 0.507 [0.44,0.58] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X49 | +5 | ASIA | X49 | 0.508 [-,-] | 0.505 [0.44,0.57] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X50a | pre | NY | X50a | 0.479 [-,-] | 0.505 [0.44,0.56] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | +30 | POOLED | X46 | 0.514 [-,-] | 0.503 [0.48,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X48 | +5 | POOLED | X48 | 0.506 [-,-] | 0.503 [0.47,0.54] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X50a | +5 | LONDON | X50a | 0.492 [-,-] | 0.502 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +15 | LONDON | X50a | 0.499 [-,-] | 0.500 [0.43,0.57] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X50a | +5 | POOLED | X50a | 0.498 [-,-] | 0.499 [0.46,0.53] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X47 | +5 | NY | X47 | 0.507 [-,-] | 0.499 [0.44,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X46 | +5 | LONDON | X46 | 0.504 [-,-] | 0.494 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | pre | LONDON | X50a | 0.507 [-,-] | 0.492 [0.42,0.56] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | +15 | POOLED | X46 | 0.484 [-,-] | 0.491 [0.45,0.53] | - | 0.487 | - | - | - | - | - | - | stack | short by 0.189 AUC, 5 of 5 econ |
| X46 | pre | LONDON | X46 | 0.516 [-,-] | 0.491 [0.44,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X49 | +30 | NY | X49 | 0.491 [-,-] | 0.490 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | +5 | POOLED | X46 | 0.494 [-,-] | 0.489 [0.46,0.52] | - | 0.486 | - | - | - | - | - | - | stack | short by 0.191 AUC, 5 of 5 econ |
| X50 | +15 | NY | X50b | 0.504 [-,-] | 0.489 [0.43,0.54] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X47 | +5 | POOLED | X47 | 0.494 [-,-] | 0.486 [0.46,0.52] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X49 | pre | LONDON | X49 | 0.489 [-,-] | 0.485 [0.42,0.55] | - | 0.487 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +5 | NY | X50a | 0.474 [-,-] | 0.483 [0.43,0.54] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50 | +5 | NY | X50b | 0.463 [-,-] | 0.483 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X46 | pre | ASIA | X46 | 0.506 [-,-] | 0.480 [0.43,0.53] | - | 0.481 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X47 | pre | LONDON | X47 | 0.468 [-,-] | 0.480 [0.41,0.54] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X46 | +15 | ASIA | X46 | 0.487 [-,-] | 0.478 [0.43,0.53] | - | 0.471 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X46 | pre | POOLED | X46 | 0.501 [-,-] | 0.476 [0.45,0.50] | - | 0.476 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X46 | +30 | NY | X46 | 0.504 [-,-] | 0.474 [0.43,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +15 | NY | X50a | 0.482 [-,-] | 0.474 [0.40,0.53] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X50a | +30 | NY | X50a | 0.499 [-,-] | 0.473 [0.41,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X48 | +5 | NY | X48 | 0.471 [-,-] | 0.473 [0.42,0.53] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X47 | +15 | ASIA | X47 | 0.499 [-,-] | 0.472 [0.42,0.52] | - | 0.479 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X46 | +15 | NY | X46 | 0.480 [-,-] | 0.471 [0.42,0.52] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| X49 | +5 | NY | X49 | 0.478 [-,-] | 0.468 [0.40,0.53] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X46 | +5 | ASIA | X46 | 0.505 [-,-] | 0.464 [0.42,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X46 | pre | NY | X46 | 0.485 [-,-] | 0.459 [0.41,0.50] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X47 | +5 | LONDON | X47 | 0.467 [-,-] | 0.442 [0.39,0.49] | - | 0.433 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X46 0 POOLED: r11_u X46; cond hold 0.476 strata 0.476; headline=True
- X46 0 ASIA: r11_u X46; cond hold 0.480 strata 0.481; headline=True
- X46 0 LONDON: r11_u X46; cond hold 0.491 strata 0.489; headline=True
- X46 0 NY: r11_u X46; cond hold 0.459 strata 0.461; headline=True
- X46 5 POOLED: r11_u X46; cond hold 0.489 strata 0.486; headline=True
- X46 5 ASIA: r11_u X46; cond hold 0.464 strata 0.459; headline=True
- X46 5 LONDON: r11_u X46; cond hold 0.494 strata 0.485; headline=True
- X46 5 NY: r11_u X46; cond hold 0.511 strata 0.515; headline=True
- X46 15 POOLED: r11_u X46; cond hold 0.491 strata 0.487; headline=True
- X46 15 ASIA: r11_u X46; cond hold 0.478 strata 0.471; headline=True
- X46 15 LONDON: r11_u X46; cond hold 0.526 strata 0.517; headline=True
- X46 15 NY: r11_u X46; cond hold 0.471 strata 0.473; headline=True
- X46 30 POOLED: r11_u X46; cond hold 0.503 strata 0.501; headline=True
- X46 30 ASIA: r11_u X46; cond hold 0.518 strata 0.512; headline=True
- X46 30 LONDON: r11_u X46; cond hold 0.514 strata 0.519; headline=True
- X46 30 NY: r11_u X46; cond hold 0.474 strata 0.467; headline=True
- X47 0 POOLED: r11_u X47; cond hold 0.509 strata 0.510; headline=True
- X47 0 ASIA: r11_u X47; cond hold 0.531 strata 0.530; headline=True
- X47 0 LONDON: r11_u X47; cond hold 0.480 strata 0.479; headline=True
- X47 0 NY: r11_u X47; cond hold 0.514 strata 0.510; headline=True
- X47 5 POOLED: r11_u X47; cond hold 0.486 strata 0.484; headline=True
- X47 5 ASIA: r11_u X47; cond hold 0.515 strata 0.513; headline=True
- X47 5 LONDON: r11_u X47; cond hold 0.442 strata 0.433; headline=True
- X47 5 NY: r11_u X47; cond hold 0.499 strata 0.504; headline=True
- X47 15 POOLED: r11_u X47; cond hold 0.511 strata 0.511; headline=True
- X47 15 ASIA: r11_u X47; cond hold 0.472 strata 0.479; headline=True
- X47 15 LONDON: r11_u X47; cond hold 0.519 strata 0.518; headline=True
- X47 15 NY: r11_u X47; cond hold 0.541 strata 0.539; headline=True
- X47 30 POOLED: r11_u X47; cond hold 0.526 strata 0.522; headline=True
- X47 30 ASIA: r11_u X47; cond hold 0.518 strata 0.511; headline=True
- X47 30 LONDON: r11_u X47; cond hold 0.522 strata 0.522; headline=True
- X47 30 NY: r11_u X47; cond hold 0.533 strata 0.533; headline=True
- X48 0 POOLED: r11_u X48; cond hold 0.526 strata 0.525; headline=True
- X48 0 ASIA: r11_u X48; cond hold 0.518 strata 0.513; headline=True
- X48 0 LONDON: r11_u X48; cond hold 0.534 strata 0.534; headline=True
- X48 0 NY: r11_u X48; cond hold 0.524 strata 0.532; headline=True
- X48 5 POOLED: r11_u X48; cond hold 0.503 strata 0.503; headline=True
- X48 5 ASIA: r11_u X48; cond hold 0.522 strata 0.516; headline=True
- X48 5 LONDON: r11_u X48; cond hold 0.520 strata 0.521; headline=True
- X48 5 NY: r11_u X48; cond hold 0.473 strata 0.480; headline=True
- X48 15 POOLED: r11_u X48; cond hold 0.527 strata 0.523; headline=True
- X48 15 ASIA: r11_u X48; cond hold 0.522 strata 0.511; headline=True
- X48 15 LONDON: r11_u X48; cond hold 0.555 strata 0.546; headline=True
- X48 15 NY: r11_u X48; cond hold 0.509 strata 0.510; headline=True
- X48 30 POOLED: r11_u X48; cond hold 0.530 strata 0.527; headline=True
- X48 30 ASIA: r11_u X48; cond hold 0.527 strata 0.523; headline=True
- X48 30 LONDON: r11_u X48; cond hold 0.520 strata 0.511; headline=True
- X48 30 NY: r11_u X48; cond hold 0.537 strata 0.541; headline=True
- X49 0 POOLED: r11_u X49; cond hold 0.521 strata 0.522; headline=True
- X49 0 ASIA: r11_u X49; cond hold 0.538 strata 0.537; headline=True
- X49 0 LONDON: r11_u X49; cond hold 0.485 strata 0.487; headline=True
- X49 0 NY: r11_u X49; cond hold 0.530 strata 0.535; headline=True
- X49 5 POOLED: r11_u X49; cond hold 0.509 strata 0.509; headline=True
- X49 5 ASIA: r11_u X49; cond hold 0.505 strata 0.501; headline=True
- X49 5 LONDON: r11_u X49; cond hold 0.549 strata 0.548; headline=True
- X49 5 NY: r11_u X49; cond hold 0.468 strata 0.468; headline=True
- X49 15 POOLED: r11_u X49; cond hold 0.529 strata 0.524; headline=True
- X49 15 ASIA: r11_u X49; cond hold 0.522 strata 0.518; headline=True
- X49 15 LONDON: r11_u X49; cond hold 0.554 strata 0.544; headline=True
- X49 15 NY: r11_u X49; cond hold 0.507 strata 0.497; headline=True
- X49 30 POOLED: r11_u X49; cond hold 0.530 strata 0.529; headline=True
- X49 30 ASIA: r11_u X49; cond hold 0.564 strata 0.554; headline=True
- X49 30 LONDON: r11_u X49; cond hold 0.524 strata 0.528; headline=True
- X49 30 NY: r11_u X49; cond hold 0.490 strata 0.499; headline=True
- X50a 0 POOLED: r11_u X50a; cond hold 0.525 strata 0.523; headline=False
- X50a 0 ASIA: r11_u X50a; cond hold 0.569 strata 0.563; headline=False
- X50a 0 LONDON: r11_u X50a; cond hold 0.492 strata 0.488; headline=False
- X50a 0 NY: r11_u X50a; cond hold 0.505 strata 0.515; headline=False
- X50a 5 POOLED: r11_u X50a; cond hold 0.499 strata 0.496; headline=False
- X50a 5 ASIA: r11_u X50a; cond hold 0.507 strata 0.498; headline=False
- X50a 5 LONDON: r11_u X50a; cond hold 0.502 strata 0.500; headline=False
- X50a 5 NY: r11_u X50a; cond hold 0.483 strata 0.485; headline=False
- X50a 15 POOLED: r11_u X50a; cond hold 0.516 strata 0.515; headline=False
- X50a 15 ASIA: r11_u X50a; cond hold 0.560 strata 0.546; headline=False
- X50a 15 LONDON: r11_u X50a; cond hold 0.500 strata 0.506; headline=False
- X50a 15 NY: r11_u X50a; cond hold 0.474 strata 0.472; headline=False
- X50a 30 POOLED: r11_u X50a; cond hold 0.534 strata 0.534; headline=True
- X50a 30 ASIA: r11_u X50a; cond hold 0.549 strata 0.548; headline=True
- X50a 30 LONDON: r11_u X50a; cond hold 0.573 strata 0.574; headline=True
- X50a 30 NY: r11_u X50a; cond hold 0.473 strata 0.475; headline=True
- X50 0 POOLED: r11_u X50b; cond hold 0.543 strata 0.543; headline=True
- X50 0 ASIA: r11_u X50b; cond hold 0.550 strata 0.546; headline=True
- X50 0 LONDON: r11_u X50b; cond hold 0.516 strata 0.516; headline=True
- X50 0 NY: r11_u X50b; cond hold 0.557 strata 0.574; headline=True
- X50 5 POOLED: r11_u X50b; cond hold 0.509 strata 0.507; headline=True
- X50 5 ASIA: r11_u X50b; cond hold 0.528 strata 0.520; headline=True
- X50 5 LONDON: r11_u X50b; cond hold 0.511 strata 0.506; headline=True
- X50 5 NY: r11_u X50b; cond hold 0.483 strata 0.482; headline=True
- X50 15 POOLED: r11_u X50b; cond hold 0.522 strata 0.520; headline=True
- X50 15 ASIA: r11_u X50b; cond hold 0.551 strata 0.548; headline=True
- X50 15 LONDON: r11_u X50b; cond hold 0.516 strata 0.520; headline=True
- X50 15 NY: r11_u X50b; cond hold 0.489 strata 0.480; headline=True
- X50 30 POOLED: r11_u X50b; cond hold 0.520 strata 0.518; headline=False
- X50 30 ASIA: r11_u X50b; cond hold 0.513 strata 0.510; headline=False
- X50 30 LONDON: r11_u X50b; cond hold 0.527 strata 0.525; headline=False
- X50 30 NY: r11_u X50b; cond hold 0.507 strata 0.512; headline=False
- X16-cond-lgbm 0 POOLED: r11_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r11_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r11_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r11_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r11_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r11_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r11_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r11_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r11_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r11_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r11_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r11_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r11_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r11_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r11_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r11_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r11_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r11_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r11_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r11_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r11_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r11_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r11_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r11_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r11_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r11_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r11_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r11_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r11_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r11_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r11_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r11_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
