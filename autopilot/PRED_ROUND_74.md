# PRED ROUND 74 - block X3 round 10 - X3 round 10

Best HOLDOUT F-R AUC: +15 POOLED 0.545 [0.51,0.58] | ASIA 0.565 [0.51,0.61] | LONDON 0.574 [0.52,0.63] | NY 0.537 [0.47,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.539 [0.50,0.57] | ASIA 0.580 [0.52,0.63] | LONDON 0.554 [0.51,0.61] | NY 0.549 [0.49,0.61]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.080 AUC, 5 of 5 economic conditions short.
not found - short by 0.080 AUC and 5 of 5 economic conditions

prereg f49b59274f4d4f4edcf9d68f4c26b83bac11cd09817b118eb0f83d143b70e797 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X45z | +30 | ASIA | X45z | 0.547 [-,-] | 0.580 [0.52,0.63] | - | 0.577 | - | - | - | - | - | - | stack | short by 0.080 AUC, 5 of 5 econ |
| X43 | +15 | LONDON | X43 | 0.538 [-,-] | 0.574 [0.52,0.63] | - | 0.571 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41 | +15 | ASIA | X41 | 0.544 [-,-] | 0.565 [0.51,0.61] | - | 0.562 | - | - | - | - | - | - | stack | short by 0.095 AUC, 5 of 5 econ |
| X43 | +30 | LONDON | X43 | 0.535 [-,-] | 0.554 [0.51,0.61] | - | 0.557 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | +5 | ASIA | X41in | 0.545 [-,-] | 0.551 [0.49,0.61] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| X41in | +30 | ASIA | X41in | 0.543 [-,-] | 0.550 [0.49,0.60] | - | 0.546 | - | - | - | - | - | - | stack | short by 0.110 AUC, 5 of 5 econ |
| X45 | +15 | LONDON | X45b | 0.518 [-,-] | 0.550 [0.49,0.61] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | NY | X44_diff | 0.514 [-,-] | 0.549 [0.49,0.61] | - | 0.548 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | LONDON | X44_u | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +15 | POOLED | X43 | 0.536 [-,-] | 0.545 [0.51,0.58] | - | 0.543 | - | - | - | - | - | - | stack | promising: short by 0.135 AUC, 5 of 5 econ |
| X45z | +15 | LONDON | X45z | 0.508 [-,-] | 0.543 [0.49,0.61] | - | 0.543 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X43 | +30 | NY | X43 | 0.522 [-,-] | 0.540 [0.48,0.60] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | pre | NY | X45z | 0.525 [-,-] | 0.540 [0.49,0.59] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | LONDON | X44_diff | 0.528 [-,-] | 0.539 [0.47,0.60] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +30 | POOLED | X45z | 0.521 [-,-] | 0.539 [0.50,0.57] | - | 0.536 | - | - | - | - | - | - | stack | promising: short by 0.141 AUC, 5 of 5 econ |
| X41 | pre | ASIA | X41 | 0.536 [-,-] | 0.539 [0.49,0.59] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.121 AUC, 5 of 5 econ |
| X43 | pre | NY | X43 | 0.515 [-,-] | 0.538 [0.46,0.61] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45 | +30 | ASIA | X45b | 0.548 [-,-] | 0.537 [0.48,0.59] | - | 0.526 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X41in | +15 | ASIA | X41in | 0.533 [-,-] | 0.537 [0.48,0.59] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X41in | +15 | NY | X41in | 0.511 [-,-] | 0.537 [0.47,0.59] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +15 | NY | X43 | 0.537 [-,-] | 0.536 [0.46,0.59] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +5 | ASIA | X44_u | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X44 | pre | NY | X44_l | 0.539 [-,-] | 0.535 [0.47,0.61] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +30 | NY | X45z | 0.512 [-,-] | 0.535 [0.47,0.60] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | pre | LONDON | X43 | 0.536 [-,-] | 0.535 [0.47,0.59] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | +15 | POOLED | X41in | 0.519 [-,-] | 0.534 [0.50,0.57] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.146 AUC, 5 of 5 econ |
| X44 | +15 | ASIA | X44_l | 0.512 [-,-] | 0.533 [0.48,0.58] | - | 0.538 | - | - | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| X45 | +30 | POOLED | X45b | 0.525 [-,-] | 0.532 [0.50,0.56] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.148 AUC, 5 of 5 econ |
| X45 | +30 | NY | X45b | 0.504 [-,-] | 0.532 [0.47,0.60] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | ASIA | X44_l | 0.516 [-,-] | 0.531 [0.48,0.59] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X44 | +5 | ASIA | X44_diff | 0.533 [-,-] | 0.531 [0.49,0.58] | - | 0.535 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X41 | +15 | LONDON | X41 | 0.522 [-,-] | 0.531 [0.46,0.59] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X42 | +5 | ASIA | X42 | 0.514 [-,-] | 0.531 [0.48,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X44 | +30 | LONDON | X44_l | 0.529 [-,-] | 0.530 [0.47,0.59] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | NY | X44_u | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41 | pre | LONDON | X41 | 0.530 [-,-] | 0.529 [0.47,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | ASIA | X44_u | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X42 | +30 | NY | X42 | 0.495 [-,-] | 0.528 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | NY | X44_u | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +15 | ASIA | X45z | 0.527 [-,-] | 0.527 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| X41 | pre | POOLED | X41 | 0.528 [-,-] | 0.526 [0.50,0.56] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X44 | +15 | POOLED | X44_l | 0.515 [-,-] | 0.526 [0.49,0.56] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X44 | +15 | POOLED | X44_u | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X45 | +15 | ASIA | X45b | 0.528 [-,-] | 0.526 [0.47,0.58] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.134 AUC, 5 of 5 econ |
| X45 | pre | NY | X45b | 0.510 [-,-] | 0.526 [0.46,0.58] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | POOLED | X44_u | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X43 | +15 | ASIA | X43 | 0.532 [-,-] | 0.525 [0.47,0.58] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X42 | +30 | POOLED | X42 | 0.508 [-,-] | 0.525 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | promising: short by 0.155 AUC, 5 of 5 econ |
| X41 | +5 | NY | X41 | 0.519 [-,-] | 0.524 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | POOLED | X44_l | 0.516 [-,-] | 0.524 [0.49,0.56] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X44 | pre | LONDON | X44_u | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | +15 | LONDON | X41in | 0.508 [-,-] | 0.523 [0.45,0.58] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X42 | +30 | LONDON | X42 | 0.498 [-,-] | 0.523 [0.46,0.59] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +5 | ASIA | X43 | 0.531 [-,-] | 0.523 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| X45 | +15 | POOLED | X45b | 0.521 [-,-] | 0.523 [0.48,0.57] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X44 | +15 | NY | X44_l | 0.533 [-,-] | 0.522 [0.46,0.59] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | LONDON | X44_diff | 0.519 [-,-] | 0.522 [0.46,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | pre | POOLED | X43 | 0.518 [-,-] | 0.522 [0.49,0.56] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X45 | +30 | LONDON | X45b | 0.521 [-,-] | 0.522 [0.46,0.59] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +30 | POOLED | X43 | 0.521 [-,-] | 0.522 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | promising: short by 0.158 AUC, 5 of 5 econ |
| X42 | +30 | ASIA | X42 | 0.530 [-,-] | 0.521 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X44 | +15 | NY | X44_u | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41 | +15 | POOLED | X41 | 0.525 [-,-] | 0.520 [0.49,0.56] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X42 | +15 | LONDON | X42 | 0.503 [-,-] | 0.520 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | POOLED | X44_l | 0.512 [-,-] | 0.520 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - | stack | promising: short by 0.160 AUC, 5 of 5 econ |
| X44 | pre | ASIA | X44_l | 0.505 [-,-] | 0.520 [0.46,0.59] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X41 | +30 | POOLED | X41 | 0.518 [-,-] | 0.520 [0.49,0.55] | - | 0.517 | - | - | - | - | - | - | stack | promising: short by 0.160 AUC, 5 of 5 econ |
| X42 | pre | LONDON | X42 | 0.506 [-,-] | 0.519 [0.46,0.58] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | POOLED | X44_u | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X42 | +15 | ASIA | X42 | 0.524 [-,-] | 0.518 [0.46,0.58] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X41in | pre | NY | X41in | 0.487 [-,-] | 0.518 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | LONDON | X44_u | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +5 | ASIA | X45z | 0.520 [-,-] | 0.518 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X44 | +5 | LONDON | X44_u | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +15 | POOLED | X45z | 0.516 [-,-] | 0.517 [0.48,0.56] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X42 | +15 | POOLED | X42 | 0.512 [-,-] | 0.516 [0.47,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X41 | +5 | ASIA | X41 | 0.495 [-,-] | 0.516 [0.46,0.58] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| X41 | +30 | ASIA | X41 | 0.542 [-,-] | 0.516 [0.45,0.57] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| X44 | +5 | POOLED | X44_l | 0.501 [-,-] | 0.515 [0.48,0.55] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X41 | +30 | LONDON | X41 | 0.495 [-,-] | 0.515 [0.46,0.57] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X42 | pre | POOLED | X42 | 0.519 [-,-] | 0.514 [0.48,0.54] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X42 | pre | ASIA | X42 | 0.531 [-,-] | 0.514 [0.44,0.58] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X42 | pre | NY | X42 | 0.520 [-,-] | 0.513 [0.46,0.56] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | ASIA | X44_u | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X44 | pre | ASIA | X44_diff | 0.522 [-,-] | 0.512 [0.45,0.56] | - | 0.522 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X44 | +5 | POOLED | X44_u | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X41in | +30 | POOLED | X41in | 0.505 [-,-] | 0.511 [0.48,0.54] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X45 | pre | POOLED | X45b | 0.510 [-,-] | 0.511 [0.48,0.54] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X41 | +5 | POOLED | X41 | 0.510 [-,-] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X44 | +5 | ASIA | X44_l | 0.501 [-,-] | 0.511 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| X42 | +15 | NY | X42 | 0.507 [-,-] | 0.510 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | pre | POOLED | X45z | 0.508 [-,-] | 0.509 [0.48,0.54] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X44 | +5 | LONDON | X44_diff | 0.524 [-,-] | 0.508 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | LONDON | X44_l | 0.505 [-,-] | 0.508 [0.44,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | NY | X44_diff | 0.489 [-,-] | 0.508 [0.44,0.57] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | +5 | POOLED | X41in | 0.502 [-,-] | 0.507 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X41in | +30 | NY | X41in | 0.488 [-,-] | 0.507 [0.45,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +5 | LONDON | X43 | 0.509 [-,-] | 0.506 [0.43,0.58] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45 | +5 | ASIA | X45b | 0.515 [-,-] | 0.506 [0.46,0.56] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X44 | +30 | ASIA | X44_u | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X45 | pre | ASIA | X45b | 0.503 [-,-] | 0.506 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X44 | +5 | NY | X44_l | 0.493 [-,-] | 0.505 [0.43,0.58] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | +5 | LONDON | X41in | 0.497 [-,-] | 0.504 [0.44,0.56] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41 | +30 | NY | X41 | 0.510 [-,-] | 0.504 [0.46,0.56] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +5 | LONDON | X44_l | 0.496 [-,-] | 0.503 [0.44,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | LONDON | X44_l | 0.488 [-,-] | 0.503 [0.45,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X42 | +5 | POOLED | X42 | 0.500 [-,-] | 0.502 [0.47,0.54] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| X43 | pre | ASIA | X43 | 0.510 [-,-] | 0.502 [0.45,0.56] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X42 | +5 | LONDON | X42 | 0.497 [-,-] | 0.502 [0.43,0.57] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | pre | ASIA | X45z | 0.510 [-,-] | 0.502 [0.44,0.57] | - | 0.495 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X45 | pre | LONDON | X45b | 0.516 [-,-] | 0.501 [0.44,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X45z | +30 | LONDON | X45z | 0.501 [-,-] | 0.499 [0.44,0.55] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X44 | +5 | POOLED | X44_diff | 0.507 [-,-] | 0.496 [0.46,0.53] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X41 | pre | NY | X41 | 0.520 [-,-] | 0.495 [0.43,0.57] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | POOLED | X44_diff | 0.495 [-,-] | 0.495 [0.46,0.52] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.185 AUC, 5 of 5 econ |
| X44 | +5 | NY | X44_diff | 0.484 [-,-] | 0.494 [0.42,0.55] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | pre | POOLED | X41in | 0.490 [-,-] | 0.493 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X44 | +5 | NY | X44_u | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45 | +15 | NY | X45b | 0.518 [-,-] | 0.492 [0.43,0.57] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | POOLED | X44_diff | 0.497 [-,-] | 0.491 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.189 AUC, 5 of 5 econ |
| X45z | +5 | POOLED | X45z | 0.494 [-,-] | 0.490 [0.46,0.52] | - | 0.488 | - | - | - | - | - | - | stack | short by 0.190 AUC, 5 of 5 econ |
| X45 | +5 | POOLED | X45b | 0.494 [-,-] | 0.490 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.190 AUC, 5 of 5 econ |
| X45 | +5 | LONDON | X45b | 0.485 [-,-] | 0.489 [0.42,0.55] | - | 0.493 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | POOLED | X44_diff | 0.500 [-,-] | 0.488 [0.46,0.52] | - | 0.486 | - | - | - | - | - | - | stack | short by 0.192 AUC, 5 of 5 econ |
| X44 | +30 | LONDON | X44_diff | 0.485 [-,-] | 0.487 [0.41,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +5 | POOLED | X43 | 0.502 [-,-] | 0.487 [0.45,0.52] | - | 0.481 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X41in | pre | LONDON | X41in | 0.459 [-,-] | 0.487 [0.42,0.55] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X45z | +5 | NY | X45z | 0.500 [-,-] | 0.483 [0.44,0.54] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | pre | LONDON | X45z | 0.486 [-,-] | 0.483 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41 | +5 | LONDON | X41 | 0.515 [-,-] | 0.483 [0.42,0.55] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | pre | NY | X44_diff | 0.453 [-,-] | 0.483 [0.42,0.54] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +30 | NY | X44_l | 0.482 [-,-] | 0.481 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45z | +15 | NY | X45z | 0.512 [-,-] | 0.480 [0.42,0.54] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X45 | +5 | NY | X45b | 0.476 [-,-] | 0.478 [0.42,0.55] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X42 | +5 | NY | X42 | 0.486 [-,-] | 0.477 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X41in | pre | ASIA | X41in | 0.520 [-,-] | 0.475 [0.41,0.54] | - | 0.463 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| X41in | +30 | LONDON | X41in | 0.479 [-,-] | 0.468 [0.40,0.53] | - | 0.470 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X45z | +5 | LONDON | X45z | 0.457 [-,-] | 0.465 [0.41,0.54] | - | 0.463 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X43 | +30 | ASIA | X43 | 0.502 [-,-] | 0.465 [0.41,0.52] | - | 0.460 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X41 | +15 | NY | X41 | 0.505 [-,-] | 0.463 [0.40,0.52] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X44 | +30 | ASIA | X44_diff | 0.503 [-,-] | 0.459 [0.41,0.51] | - | 0.461 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X41in | +5 | NY | X41in | 0.457 [-,-] | 0.458 [0.39,0.51] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X44 | +15 | ASIA | X44_diff | 0.494 [-,-] | 0.457 [0.39,0.52] | - | 0.455 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| X43 | +5 | NY | X43 | 0.466 [-,-] | 0.435 [0.37,0.49] | - | 0.425 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X41 0 POOLED: r10_u X41; cond hold 0.526 strata 0.522; headline=True
- X41 0 ASIA: r10_u X41; cond hold 0.539 strata 0.527; headline=True
- X41 0 LONDON: r10_u X41; cond hold 0.529 strata 0.525; headline=True
- X41 0 NY: r10_u X41; cond hold 0.495 strata 0.498; headline=True
- X41 5 POOLED: r10_u X41; cond hold 0.511 strata 0.510; headline=True
- X41 5 ASIA: r10_u X41; cond hold 0.516 strata 0.507; headline=True
- X41 5 LONDON: r10_u X41; cond hold 0.483 strata 0.483; headline=True
- X41 5 NY: r10_u X41; cond hold 0.524 strata 0.526; headline=True
- X41 15 POOLED: r10_u X41; cond hold 0.520 strata 0.521; headline=True
- X41 15 ASIA: r10_u X41; cond hold 0.565 strata 0.562; headline=True
- X41 15 LONDON: r10_u X41; cond hold 0.531 strata 0.531; headline=True
- X41 15 NY: r10_u X41; cond hold 0.463 strata 0.466; headline=True
- X41 30 POOLED: r10_u X41; cond hold 0.520 strata 0.517; headline=True
- X41 30 ASIA: r10_u X41; cond hold 0.516 strata 0.507; headline=True
- X41 30 LONDON: r10_u X41; cond hold 0.515 strata 0.514; headline=True
- X41 30 NY: r10_u X41; cond hold 0.504 strata 0.512; headline=True
- X41in 0 POOLED: r10_u X41in; cond hold 0.493 strata 0.491; headline=True
- X41in 0 ASIA: r10_u X41in; cond hold 0.475 strata 0.463; headline=True
- X41in 0 LONDON: r10_u X41in; cond hold 0.487 strata 0.480; headline=True
- X41in 0 NY: r10_u X41in; cond hold 0.518 strata 0.527; headline=True
- X41in 5 POOLED: r10_u X41in; cond hold 0.507 strata 0.507; headline=True
- X41in 5 ASIA: r10_u X41in; cond hold 0.551 strata 0.547; headline=True
- X41in 5 LONDON: r10_u X41in; cond hold 0.504 strata 0.503; headline=True
- X41in 5 NY: r10_u X41in; cond hold 0.458 strata 0.464; headline=True
- X41in 15 POOLED: r10_u X41in; cond hold 0.534 strata 0.529; headline=True
- X41in 15 ASIA: r10_u X41in; cond hold 0.537 strata 0.523; headline=True
- X41in 15 LONDON: r10_u X41in; cond hold 0.523 strata 0.518; headline=True
- X41in 15 NY: r10_u X41in; cond hold 0.537 strata 0.536; headline=True
- X41in 30 POOLED: r10_u X41in; cond hold 0.511 strata 0.509; headline=True
- X41in 30 ASIA: r10_u X41in; cond hold 0.550 strata 0.546; headline=True
- X41in 30 LONDON: r10_u X41in; cond hold 0.468 strata 0.470; headline=True
- X41in 30 NY: r10_u X41in; cond hold 0.507 strata 0.503; headline=True
- X42 0 POOLED: r10_u X42; cond hold 0.514 strata 0.511; headline=True
- X42 0 ASIA: r10_u X42; cond hold 0.514 strata 0.501; headline=True
- X42 0 LONDON: r10_u X42; cond hold 0.519 strata 0.521; headline=True
- X42 0 NY: r10_u X42; cond hold 0.513 strata 0.519; headline=True
- X42 5 POOLED: r10_u X42; cond hold 0.502 strata 0.500; headline=True
- X42 5 ASIA: r10_u X42; cond hold 0.531 strata 0.521; headline=True
- X42 5 LONDON: r10_u X42; cond hold 0.502 strata 0.498; headline=True
- X42 5 NY: r10_u X42; cond hold 0.477 strata 0.486; headline=True
- X42 15 POOLED: r10_u X42; cond hold 0.516 strata 0.512; headline=True
- X42 15 ASIA: r10_u X42; cond hold 0.518 strata 0.503; headline=True
- X42 15 LONDON: r10_u X42; cond hold 0.520 strata 0.516; headline=True
- X42 15 NY: r10_u X42; cond hold 0.510 strata 0.510; headline=True
- X42 30 POOLED: r10_u X42; cond hold 0.525 strata 0.522; headline=True
- X42 30 ASIA: r10_u X42; cond hold 0.521 strata 0.509; headline=True
- X42 30 LONDON: r10_u X42; cond hold 0.523 strata 0.529; headline=True
- X42 30 NY: r10_u X42; cond hold 0.528 strata 0.527; headline=True
- X43 0 POOLED: r10_u X43; cond hold 0.522 strata 0.521; headline=True
- X43 0 ASIA: r10_u X43; cond hold 0.502 strata 0.498; headline=True
- X43 0 LONDON: r10_u X43; cond hold 0.535 strata 0.539; headline=True
- X43 0 NY: r10_u X43; cond hold 0.538 strata 0.545; headline=True
- X43 5 POOLED: r10_u X43; cond hold 0.487 strata 0.481; headline=True
- X43 5 ASIA: r10_u X43; cond hold 0.523 strata 0.513; headline=True
- X43 5 LONDON: r10_u X43; cond hold 0.506 strata 0.499; headline=True
- X43 5 NY: r10_u X43; cond hold 0.435 strata 0.425; headline=True
- X43 15 POOLED: r10_u X43; cond hold 0.545 strata 0.543; headline=True
- X43 15 ASIA: r10_u X43; cond hold 0.525 strata 0.516; headline=True
- X43 15 LONDON: r10_u X43; cond hold 0.574 strata 0.571; headline=True
- X43 15 NY: r10_u X43; cond hold 0.536 strata 0.546; headline=True
- X43 30 POOLED: r10_u X43; cond hold 0.522 strata 0.520; headline=True
- X43 30 ASIA: r10_u X43; cond hold 0.465 strata 0.460; headline=True
- X43 30 LONDON: r10_u X43; cond hold 0.554 strata 0.557; headline=True
- X43 30 NY: r10_u X43; cond hold 0.540 strata 0.545; headline=True
- X44 0 POOLED: r10_u X44_u; cond hold 0.526 strata 0.523; headline=True
- X44 0 ASIA: r10_u X44_u; cond hold 0.529 strata 0.520; headline=True
- X44 0 LONDON: r10_u X44_u; cond hold 0.523 strata 0.516; headline=True
- X44 0 NY: r10_u X44_u; cond hold 0.527 strata 0.532; headline=True
- X44 5 POOLED: r10_u X44_u; cond hold 0.512 strata 0.511; headline=False
- X44 5 ASIA: r10_u X44_u; cond hold 0.535 strata 0.528; headline=False
- X44 5 LONDON: r10_u X44_u; cond hold 0.517 strata 0.520; headline=False
- X44 5 NY: r10_u X44_u; cond hold 0.493 strata 0.499; headline=False
- X44 15 POOLED: r10_u X44_u; cond hold 0.526 strata 0.524; headline=False
- X44 15 ASIA: r10_u X44_u; cond hold 0.513 strata 0.503; headline=False
- X44 15 LONDON: r10_u X44_u; cond hold 0.546 strata 0.542; headline=False
- X44 15 NY: r10_u X44_u; cond hold 0.520 strata 0.523; headline=False
- X44 30 POOLED: r10_u X44_u; cond hold 0.519 strata 0.515; headline=False
- X44 30 ASIA: r10_u X44_u; cond hold 0.506 strata 0.494; headline=False
- X44 30 LONDON: r10_u X44_u; cond hold 0.518 strata 0.513; headline=False
- X44 30 NY: r10_u X44_u; cond hold 0.529 strata 0.534; headline=False
- X44 0 POOLED: r10_u X44_diff; cond hold 0.495 strata 0.494; headline=False
- X44 0 ASIA: r10_u X44_diff; cond hold 0.512 strata 0.522; headline=False
- X44 0 LONDON: r10_u X44_diff; cond hold 0.522 strata 0.525; headline=False
- X44 0 NY: r10_u X44_diff; cond hold 0.483 strata 0.497; headline=False
- X44 5 POOLED: r10_u X44_diff; cond hold 0.496 strata 0.494; headline=True
- X44 5 ASIA: r10_u X44_diff; cond hold 0.531 strata 0.535; headline=True
- X44 5 LONDON: r10_u X44_diff; cond hold 0.508 strata 0.510; headline=True
- X44 5 NY: r10_u X44_diff; cond hold 0.494 strata 0.501; headline=True
- X44 15 POOLED: r10_u X44_diff; cond hold 0.488 strata 0.486; headline=True
- X44 15 ASIA: r10_u X44_diff; cond hold 0.457 strata 0.455; headline=True
- X44 15 LONDON: r10_u X44_diff; cond hold 0.539 strata 0.539; headline=True
- X44 15 NY: r10_u X44_diff; cond hold 0.508 strata 0.515; headline=True
- X44 30 POOLED: r10_u X44_diff; cond hold 0.491 strata 0.490; headline=True
- X44 30 ASIA: r10_u X44_diff; cond hold 0.459 strata 0.461; headline=True
- X44 30 LONDON: r10_u X44_diff; cond hold 0.487 strata 0.491; headline=True
- X44 30 NY: r10_u X44_diff; cond hold 0.549 strata 0.548; headline=True
- X44 0 POOLED: r10_u X44_l; cond hold 0.524 strata 0.525; headline=False
- X44 0 ASIA: r10_u X44_l; cond hold 0.520 strata 0.508; headline=False
- X44 0 LONDON: r10_u X44_l; cond hold 0.508 strata 0.510; headline=False
- X44 0 NY: r10_u X44_l; cond hold 0.535 strata 0.532; headline=False
- X44 5 POOLED: r10_u X44_l; cond hold 0.515 strata 0.516; headline=False
- X44 5 ASIA: r10_u X44_l; cond hold 0.511 strata 0.499; headline=False
- X44 5 LONDON: r10_u X44_l; cond hold 0.503 strata 0.505; headline=False
- X44 5 NY: r10_u X44_l; cond hold 0.505 strata 0.497; headline=False
- X44 15 POOLED: r10_u X44_l; cond hold 0.526 strata 0.529; headline=False
- X44 15 ASIA: r10_u X44_l; cond hold 0.533 strata 0.538; headline=False
- X44 15 LONDON: r10_u X44_l; cond hold 0.503 strata 0.504; headline=False
- X44 15 NY: r10_u X44_l; cond hold 0.522 strata 0.518; headline=False
- X44 30 POOLED: r10_u X44_l; cond hold 0.520 strata 0.519; headline=False
- X44 30 ASIA: r10_u X44_l; cond hold 0.531 strata 0.522; headline=False
- X44 30 LONDON: r10_u X44_l; cond hold 0.530 strata 0.530; headline=False
- X44 30 NY: r10_u X44_l; cond hold 0.481 strata 0.482; headline=False
- X45z 0 POOLED: r10_u X45z; cond hold 0.509 strata 0.508; headline=True
- X45z 0 ASIA: r10_u X45z; cond hold 0.502 strata 0.495; headline=True
- X45z 0 LONDON: r10_u X45z; cond hold 0.483 strata 0.475; headline=True
- X45z 0 NY: r10_u X45z; cond hold 0.540 strata 0.551; headline=True
- X45z 5 POOLED: r10_u X45z; cond hold 0.490 strata 0.488; headline=True
- X45z 5 ASIA: r10_u X45z; cond hold 0.518 strata 0.511; headline=True
- X45z 5 LONDON: r10_u X45z; cond hold 0.465 strata 0.463; headline=True
- X45z 5 NY: r10_u X45z; cond hold 0.483 strata 0.488; headline=True
- X45z 15 POOLED: r10_u X45z; cond hold 0.517 strata 0.515; headline=True
- X45z 15 ASIA: r10_u X45z; cond hold 0.527 strata 0.519; headline=True
- X45z 15 LONDON: r10_u X45z; cond hold 0.543 strata 0.543; headline=True
- X45z 15 NY: r10_u X45z; cond hold 0.480 strata 0.478; headline=True
- X45z 30 POOLED: r10_u X45z; cond hold 0.539 strata 0.536; headline=True
- X45z 30 ASIA: r10_u X45z; cond hold 0.580 strata 0.577; headline=True
- X45z 30 LONDON: r10_u X45z; cond hold 0.499 strata 0.502; headline=True
- X45z 30 NY: r10_u X45z; cond hold 0.535 strata 0.538; headline=True
- X45 0 POOLED: r10_u X45b; cond hold 0.511 strata 0.511; headline=True
- X45 0 ASIA: r10_u X45b; cond hold 0.506 strata 0.503; headline=True
- X45 0 LONDON: r10_u X45b; cond hold 0.501 strata 0.498; headline=True
- X45 0 NY: r10_u X45b; cond hold 0.526 strata 0.534; headline=True
- X45 5 POOLED: r10_u X45b; cond hold 0.490 strata 0.490; headline=True
- X45 5 ASIA: r10_u X45b; cond hold 0.506 strata 0.499; headline=True
- X45 5 LONDON: r10_u X45b; cond hold 0.489 strata 0.493; headline=True
- X45 5 NY: r10_u X45b; cond hold 0.478 strata 0.483; headline=True
- X45 15 POOLED: r10_u X45b; cond hold 0.523 strata 0.522; headline=True
- X45 15 ASIA: r10_u X45b; cond hold 0.526 strata 0.518; headline=True
- X45 15 LONDON: r10_u X45b; cond hold 0.550 strata 0.551; headline=True
- X45 15 NY: r10_u X45b; cond hold 0.492 strata 0.496; headline=True
- X45 30 POOLED: r10_u X45b; cond hold 0.532 strata 0.529; headline=True
- X45 30 ASIA: r10_u X45b; cond hold 0.537 strata 0.526; headline=True
- X45 30 LONDON: r10_u X45b; cond hold 0.522 strata 0.518; headline=True
- X45 30 NY: r10_u X45b; cond hold 0.532 strata 0.539; headline=True
- X16-cond-lgbm 0 POOLED: r10_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r10_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r10_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r10_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r10_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r10_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r10_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r10_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r10_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r10_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r10_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r10_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r10_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r10_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r10_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r10_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r10_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r10_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r10_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r10_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r10_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r10_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r10_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r10_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r10_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r10_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r10_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r10_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r10_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r10_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r10_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r10_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
