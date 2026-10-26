# PRED ROUND 88 - block X3 round 13 - X3 round 13

Best HOLDOUT F-R AUC: +15 POOLED 0.550 [0.51,0.59] | ASIA 0.562 [0.51,0.61] | LONDON 0.560 [0.50,0.63] | NY 0.579 [0.50,0.65]
Best HOLDOUT F-R AUC: +30 POOLED 0.528 [0.50,0.56] | ASIA 0.566 [0.51,0.62] | LONDON 0.553 [0.49,0.61] | NY 0.566 [0.51,0.62]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.094 AUC, 5 of 5 economic conditions short.
not found - short by 0.094 AUC and 5 of 5 economic conditions

prereg ffdf0325c1c470cc2367be4dae050e2e1672eb7b692f6e95695d9e6d948cf861 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X59 | +5 | NY | X59b | 0.543 [-,-] | 0.590 [0.52,0.66] | - | 0.587 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59 | +15 | NY | X59b | 0.535 [-,-] | 0.579 [0.50,0.65] | - | 0.578 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +30 | ASIA | X60_pq | 0.546 [-,-] | 0.566 [0.51,0.62] | - | 0.552 | - | - | - | - | - | - | stack | short by 0.094 AUC, 5 of 5 econ |
| X59 | +30 | NY | X59b | 0.530 [-,-] | 0.566 [0.51,0.62] | - | 0.565 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +30 | ASIA | X60_sE | 0.546 [-,-] | 0.563 [0.51,0.62] | - | 0.550 | - | - | - | - | - | - | stack | short by 0.097 AUC, 5 of 5 econ |
| X56 | +15 | ASIA | X56 | 0.557 [-,-] | 0.562 [0.51,0.61] | - | 0.559 | - | - | - | - | - | - | stack | short by 0.098 AUC, 5 of 5 econ |
| X56 | +15 | LONDON | X56 | 0.512 [-,-] | 0.560 [0.50,0.63] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +30 | LONDON | X56 | 0.515 [-,-] | 0.553 [0.49,0.61] | - | 0.557 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +15 | POOLED | X56 | 0.529 [-,-] | 0.550 [0.51,0.59] | - | 0.548 | - | - | - | - | - | - | stack | promising: short by 0.130 AUC, 5 of 5 econ |
| X59a | pre | NY | X59a | 0.512 [-,-] | 0.548 [0.47,0.60] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | +30 | NY | X59a | 0.521 [-,-] | 0.546 [0.47,0.60] | - | 0.547 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | pre | NY | X58 | 0.519 [-,-] | 0.540 [0.49,0.60] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X59 | pre | NY | X59b | 0.525 [-,-] | 0.537 [0.46,0.61] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +15 | ASIA | X60_pq | 0.522 [-,-] | 0.537 [0.47,0.61] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X56 | +30 | ASIA | X56 | 0.547 [-,-] | 0.536 [0.49,0.59] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X59a | +15 | NY | X59a | 0.496 [-,-] | 0.536 [0.46,0.60] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | pre | ASIA | X56 | 0.542 [-,-] | 0.536 [0.47,0.59] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X59 | +15 | POOLED | X59b | 0.500 [-,-] | 0.535 [0.49,0.57] | - | 0.537 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X58 | pre | ASIA | X58 | 0.518 [-,-] | 0.535 [0.47,0.61] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X58 | +30 | ASIA | X58 | 0.564 [-,-] | 0.535 [0.47,0.59] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X59 | +15 | LONDON | X59b | 0.497 [-,-] | 0.534 [0.46,0.59] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +15 | ASIA | X60_sE | 0.521 [-,-] | 0.534 [0.47,0.61] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| X59a | +5 | NY | X59a | 0.501 [-,-] | 0.532 [0.46,0.59] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X60 | +5 | ASIA | X60_pq | 0.516 [-,-] | 0.530 [0.46,0.59] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.130 AUC, 5 of 5 econ |
| X59 | +5 | POOLED | X59b | 0.497 [-,-] | 0.530 [0.48,0.57] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X60 | +30 | POOLED | X60_pq | 0.510 [-,-] | 0.528 [0.50,0.56] | - | 0.528 | - | - | - | - | - | - | stack | promising: short by 0.152 AUC, 5 of 5 econ |
| X60 | pre | ASIA | X60_sE | 0.538 [-,-] | 0.528 [0.47,0.59] | - | 0.517 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X56 | +30 | POOLED | X56 | 0.517 [-,-] | 0.528 [0.50,0.56] | - | 0.524 | - | - | - | - | - | - | stack | promising: short by 0.152 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +15 | LONDON | X58 | 0.517 [-,-] | 0.527 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +30 | POOLED | X60_sE | 0.506 [-,-] | 0.527 [0.49,0.56] | - | 0.527 | - | - | - | - | - | - | stack | promising: short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X60 | +30 | LONDON | X60_pq | 0.504 [-,-] | 0.526 [0.45,0.60] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | pre | POOLED | X58 | 0.510 [-,-] | 0.526 [0.49,0.56] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X56 | +5 | LONDON | X56 | 0.514 [-,-] | 0.525 [0.46,0.60] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +5 | ASIA | X60_sE | 0.511 [-,-] | 0.524 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X60 | pre | ASIA | X60_pq | 0.535 [-,-] | 0.524 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +5 | ASIA | X56 | 0.537 [-,-] | 0.523 [0.47,0.58] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| X60 | +30 | LONDON | X60_sE | 0.502 [-,-] | 0.523 [0.45,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | pre | POOLED | X56 | 0.523 [-,-] | 0.522 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X59 | +5 | LONDON | X59b | 0.495 [-,-] | 0.522 [0.44,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | pre | NY | X56 | 0.511 [-,-] | 0.521 [0.46,0.58] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +15 | NY | X56 | 0.510 [-,-] | 0.521 [0.46,0.58] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | pre | LONDON | X60_pq | 0.512 [-,-] | 0.519 [0.46,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +5 | ASIA | X58 | 0.506 [-,-] | 0.519 [0.46,0.57] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.141 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X59 | +30 | POOLED | X59b | 0.493 [-,-] | 0.518 [0.47,0.55] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X59 | pre | LONDON | X59b | 0.494 [-,-] | 0.518 [0.44,0.59] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | pre | LONDON | X56 | 0.517 [-,-] | 0.518 [0.45,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X60 | pre | LONDON | X60_sE | 0.507 [-,-] | 0.516 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +15 | POOLED | X58 | 0.504 [-,-] | 0.515 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X60 | pre | POOLED | X60_pq | 0.511 [-,-] | 0.515 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X60 | pre | POOLED | X60_sE | 0.506 [-,-] | 0.515 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X57 | +30 | LONDON | X57 | 0.512 [-,-] | 0.515 [0.46,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +15 | ASIA | X58 | 0.495 [-,-] | 0.513 [0.46,0.58] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X57 | +15 | NY | X57 | 0.491 [-,-] | 0.510 [0.45,0.57] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +15 | POOLED | X60_pq | 0.500 [-,-] | 0.510 [0.48,0.55] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X59 | pre | POOLED | X59b | 0.489 [-,-] | 0.509 [0.46,0.55] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X60 | +15 | NY | X60_sE | 0.482 [-,-] | 0.509 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +5 | POOLED | X56 | 0.509 [-,-] | 0.509 [0.48,0.55] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X60 | +15 | NY | X60_pq | 0.480 [-,-] | 0.508 [0.45,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +15 | NY | X58 | 0.503 [-,-] | 0.508 [0.45,0.57] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +15 | POOLED | X60_sE | 0.497 [-,-] | 0.508 [0.47,0.55] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X58 | +30 | POOLED | X58 | 0.505 [-,-] | 0.507 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X60 | +30 | NY | X60_sE | 0.486 [-,-] | 0.506 [0.45,0.56] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | pre | LONDON | X58 | 0.494 [-,-] | 0.506 [0.45,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X60 | pre | NY | X60_sE | 0.488 [-,-] | 0.506 [0.44,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +5 | POOLED | X60_pq | 0.495 [-,-] | 0.505 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| X60 | pre | NY | X60_pq | 0.487 [-,-] | 0.504 [0.44,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | pre | LONDON | X59a | 0.491 [-,-] | 0.503 [0.42,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59 | +30 | LONDON | X59b | 0.493 [-,-] | 0.503 [0.43,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X59a | +30 | POOLED | X59a | 0.490 [-,-] | 0.502 [0.46,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| X60 | +5 | NY | X60_pq | 0.477 [-,-] | 0.501 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +30 | NY | X58 | 0.483 [-,-] | 0.501 [0.43,0.57] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X60 | +5 | NY | X60_sE | 0.481 [-,-] | 0.500 [0.44,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +30 | NY | X60_pq | 0.484 [-,-] | 0.500 [0.45,0.55] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | +5 | LONDON | X59a | 0.489 [-,-] | 0.499 [0.42,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | +15 | LONDON | X57 | 0.508 [-,-] | 0.498 [0.44,0.56] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X57 | pre | LONDON | X57 | 0.517 [-,-] | 0.498 [0.45,0.55] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +5 | POOLED | X58 | 0.501 [-,-] | 0.497 [0.46,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| X60 | +5 | POOLED | X60_sE | 0.488 [-,-] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X59a | +15 | LONDON | X59a | 0.487 [-,-] | 0.495 [0.42,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59 | +15 | ASIA | X59b | 0.468 [-,-] | 0.495 [0.44,0.54] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X57 | +15 | POOLED | X57 | 0.497 [-,-] | 0.493 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X57 | +30 | POOLED | X57 | 0.494 [-,-] | 0.493 [0.45,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | +15 | POOLED | X59a | 0.478 [-,-] | 0.492 [0.44,0.54] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| X58 | +5 | NY | X58 | 0.508 [-,-] | 0.490 [0.43,0.55] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | +30 | LONDON | X59a | 0.484 [-,-] | 0.490 [0.43,0.54] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X57 | +5 | LONDON | X57 | 0.514 [-,-] | 0.490 [0.44,0.54] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59a | pre | POOLED | X59a | 0.475 [-,-] | 0.488 [0.44,0.53] | - | 0.490 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X59 | +30 | ASIA | X59b | 0.459 [-,-] | 0.488 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | +5 | NY | X57 | 0.473 [-,-] | 0.486 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +30 | NY | X56 | 0.485 [-,-] | 0.486 [0.43,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X58 | +5 | LONDON | X58 | 0.487 [-,-] | 0.485 [0.41,0.55] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X58 | +30 | LONDON | X58 | 0.470 [-,-] | 0.484 [0.42,0.55] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X59 | +5 | ASIA | X59b | 0.456 [-,-] | 0.483 [0.44,0.53] | - | 0.476 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X59a | +5 | POOLED | X59a | 0.472 [-,-] | 0.483 [0.44,0.53] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | +30 | NY | X57 | 0.467 [-,-] | 0.483 [0.43,0.54] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X56 | +5 | NY | X56 | 0.476 [-,-] | 0.482 [0.42,0.54] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X57 | +5 | POOLED | X57 | 0.494 [-,-] | 0.482 [0.45,0.51] | - | 0.478 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X60 | +5 | LONDON | X60_pq | 0.486 [-,-] | 0.479 [0.42,0.54] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X59 | pre | ASIA | X59b | 0.451 [-,-] | 0.476 [0.42,0.52] | - | 0.470 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X60 | +15 | LONDON | X60_sE | 0.497 [-,-] | 0.473 [0.41,0.54] | - | 0.470 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +5 | LONDON | X60_sE | 0.485 [-,-] | 0.471 [0.42,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X60 | +15 | LONDON | X60_pq | 0.495 [-,-] | 0.471 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X57 | pre | POOLED | X57 | 0.488 [-,-] | 0.471 [0.44,0.50] | - | 0.466 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | +30 | ASIA | X57 | 0.492 [-,-] | 0.465 [0.41,0.53] | - | 0.452 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | pre | NY | X57 | 0.464 [-,-] | 0.462 [0.40,0.52] | - | 0.456 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X57 | +5 | ASIA | X57 | 0.485 [-,-] | 0.461 [0.41,0.51] | - | 0.455 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | +15 | ASIA | X57 | 0.484 [-,-] | 0.460 [0.40,0.52] | - | 0.451 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X57 | pre | ASIA | X57 | 0.477 [-,-] | 0.447 [0.40,0.50] | - | 0.443 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| X59a | +30 | ASIA | X59a | 0.456 [-,-] | 0.441 [0.37,0.48] | - | 0.438 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| X59a | +15 | ASIA | X59a | 0.448 [-,-] | 0.426 [0.36,0.48] | - | 0.420 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |
| X59a | +5 | ASIA | X59a | 0.419 [-,-] | 0.398 [0.33,0.45] | - | 0.399 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X59a | pre | ASIA | X59a | 0.418 [-,-] | 0.394 [0.33,0.44] | - | 0.397 | - | - | - | - | - | - | stack | dead (no gain over baseline) |

One-sentence notes:
- X56 0 POOLED: r13_u X56; cond hold 0.522 strata 0.519; headline=True
- X56 0 ASIA: r13_u X56; cond hold 0.536 strata 0.524; headline=True
- X56 0 LONDON: r13_u X56; cond hold 0.518 strata 0.511; headline=True
- X56 0 NY: r13_u X56; cond hold 0.521 strata 0.531; headline=True
- X56 5 POOLED: r13_u X56; cond hold 0.509 strata 0.507; headline=True
- X56 5 ASIA: r13_u X56; cond hold 0.523 strata 0.511; headline=True
- X56 5 LONDON: r13_u X56; cond hold 0.525 strata 0.526; headline=True
- X56 5 NY: r13_u X56; cond hold 0.482 strata 0.488; headline=True
- X56 15 POOLED: r13_u X56; cond hold 0.550 strata 0.548; headline=True
- X56 15 ASIA: r13_u X56; cond hold 0.562 strata 0.559; headline=True
- X56 15 LONDON: r13_u X56; cond hold 0.560 strata 0.551; headline=True
- X56 15 NY: r13_u X56; cond hold 0.521 strata 0.522; headline=True
- X56 30 POOLED: r13_u X56; cond hold 0.528 strata 0.524; headline=True
- X56 30 ASIA: r13_u X56; cond hold 0.536 strata 0.524; headline=True
- X56 30 LONDON: r13_u X56; cond hold 0.553 strata 0.557; headline=True
- X56 30 NY: r13_u X56; cond hold 0.486 strata 0.489; headline=True
- X57 0 POOLED: r13_u X57; cond hold 0.471 strata 0.466; headline=True
- X57 0 ASIA: r13_u X57; cond hold 0.447 strata 0.443; headline=True
- X57 0 LONDON: r13_u X57; cond hold 0.498 strata 0.492; headline=True
- X57 0 NY: r13_u X57; cond hold 0.462 strata 0.456; headline=True
- X57 5 POOLED: r13_u X57; cond hold 0.482 strata 0.478; headline=True
- X57 5 ASIA: r13_u X57; cond hold 0.461 strata 0.455; headline=True
- X57 5 LONDON: r13_u X57; cond hold 0.490 strata 0.484; headline=True
- X57 5 NY: r13_u X57; cond hold 0.486 strata 0.486; headline=True
- X57 15 POOLED: r13_u X57; cond hold 0.493 strata 0.491; headline=True
- X57 15 ASIA: r13_u X57; cond hold 0.460 strata 0.451; headline=True
- X57 15 LONDON: r13_u X57; cond hold 0.498 strata 0.492; headline=True
- X57 15 NY: r13_u X57; cond hold 0.510 strata 0.515; headline=True
- X57 30 POOLED: r13_u X57; cond hold 0.493 strata 0.490; headline=True
- X57 30 ASIA: r13_u X57; cond hold 0.465 strata 0.452; headline=True
- X57 30 LONDON: r13_u X57; cond hold 0.515 strata 0.511; headline=True
- X57 30 NY: r13_u X57; cond hold 0.483 strata 0.485; headline=True
- X58 0 POOLED: r13_u X58; cond hold 0.526 strata 0.524; headline=True
- X58 0 ASIA: r13_u X58; cond hold 0.535 strata 0.528; headline=True
- X58 0 LONDON: r13_u X58; cond hold 0.506 strata 0.503; headline=True
- X58 0 NY: r13_u X58; cond hold 0.540 strata 0.538; headline=True
- X58 5 POOLED: r13_u X58; cond hold 0.497 strata 0.497; headline=True
- X58 5 ASIA: r13_u X58; cond hold 0.519 strata 0.515; headline=True
- X58 5 LONDON: r13_u X58; cond hold 0.485 strata 0.491; headline=True
- X58 5 NY: r13_u X58; cond hold 0.490 strata 0.498; headline=True
- X58 15 POOLED: r13_u X58; cond hold 0.515 strata 0.515; headline=True
- X58 15 ASIA: r13_u X58; cond hold 0.513 strata 0.512; headline=True
- X58 15 LONDON: r13_u X58; cond hold 0.527 strata 0.527; headline=True
- X58 15 NY: r13_u X58; cond hold 0.508 strata 0.508; headline=True
- X58 30 POOLED: r13_u X58; cond hold 0.507 strata 0.504; headline=True
- X58 30 ASIA: r13_u X58; cond hold 0.535 strata 0.529; headline=True
- X58 30 LONDON: r13_u X58; cond hold 0.484 strata 0.479; headline=True
- X58 30 NY: r13_u X58; cond hold 0.501 strata 0.500; headline=True
- X59a 0 POOLED: r13_u X59a; cond hold 0.488 strata 0.490; headline=True
- X59a 0 ASIA: r13_u X59a; cond hold 0.394 strata 0.397; headline=True
- X59a 0 LONDON: r13_u X59a; cond hold 0.503 strata 0.504; headline=True
- X59a 0 NY: r13_u X59a; cond hold 0.548 strata 0.539; headline=True
- X59a 5 POOLED: r13_u X59a; cond hold 0.483 strata 0.484; headline=True
- X59a 5 ASIA: r13_u X59a; cond hold 0.398 strata 0.399; headline=True
- X59a 5 LONDON: r13_u X59a; cond hold 0.499 strata 0.498; headline=True
- X59a 5 NY: r13_u X59a; cond hold 0.532 strata 0.530; headline=True
- X59a 15 POOLED: r13_u X59a; cond hold 0.492 strata 0.491; headline=True
- X59a 15 ASIA: r13_u X59a; cond hold 0.426 strata 0.420; headline=True
- X59a 15 LONDON: r13_u X59a; cond hold 0.495 strata 0.494; headline=True
- X59a 15 NY: r13_u X59a; cond hold 0.536 strata 0.530; headline=True
- X59a 30 POOLED: r13_u X59a; cond hold 0.502 strata 0.501; headline=True
- X59a 30 ASIA: r13_u X59a; cond hold 0.441 strata 0.438; headline=True
- X59a 30 LONDON: r13_u X59a; cond hold 0.490 strata 0.486; headline=True
- X59a 30 NY: r13_u X59a; cond hold 0.546 strata 0.547; headline=True
- X59 0 POOLED: r13_u X59b; cond hold 0.509 strata 0.508; headline=True
- X59 0 ASIA: r13_u X59b; cond hold 0.476 strata 0.470; headline=True
- X59 0 LONDON: r13_u X59b; cond hold 0.518 strata 0.518; headline=True
- X59 0 NY: r13_u X59b; cond hold 0.537 strata 0.538; headline=True
- X59 5 POOLED: r13_u X59b; cond hold 0.530 strata 0.528; headline=True
- X59 5 ASIA: r13_u X59b; cond hold 0.483 strata 0.476; headline=True
- X59 5 LONDON: r13_u X59b; cond hold 0.522 strata 0.528; headline=True
- X59 5 NY: r13_u X59b; cond hold 0.590 strata 0.587; headline=True
- X59 15 POOLED: r13_u X59b; cond hold 0.535 strata 0.537; headline=True
- X59 15 ASIA: r13_u X59b; cond hold 0.495 strata 0.494; headline=True
- X59 15 LONDON: r13_u X59b; cond hold 0.534 strata 0.538; headline=True
- X59 15 NY: r13_u X59b; cond hold 0.579 strata 0.578; headline=True
- X59 30 POOLED: r13_u X59b; cond hold 0.518 strata 0.519; headline=True
- X59 30 ASIA: r13_u X59b; cond hold 0.488 strata 0.489; headline=True
- X59 30 LONDON: r13_u X59b; cond hold 0.503 strata 0.499; headline=True
- X59 30 NY: r13_u X59b; cond hold 0.566 strata 0.565; headline=True
- X60 0 POOLED: r13_u X60_pq; cond hold 0.515 strata 0.514; headline=True
- X60 0 ASIA: r13_u X60_pq; cond hold 0.524 strata 0.514; headline=True
- X60 0 LONDON: r13_u X60_pq; cond hold 0.519 strata 0.520; headline=True
- X60 0 NY: r13_u X60_pq; cond hold 0.504 strata 0.510; headline=True
- X60 5 POOLED: r13_u X60_pq; cond hold 0.505 strata 0.502; headline=True
- X60 5 ASIA: r13_u X60_pq; cond hold 0.530 strata 0.520; headline=True
- X60 5 LONDON: r13_u X60_pq; cond hold 0.479 strata 0.483; headline=True
- X60 5 NY: r13_u X60_pq; cond hold 0.501 strata 0.500; headline=True
- X60 15 POOLED: r13_u X60_pq; cond hold 0.510 strata 0.508; headline=True
- X60 15 ASIA: r13_u X60_pq; cond hold 0.537 strata 0.527; headline=True
- X60 15 LONDON: r13_u X60_pq; cond hold 0.471 strata 0.468; headline=True
- X60 15 NY: r13_u X60_pq; cond hold 0.508 strata 0.511; headline=True
- X60 30 POOLED: r13_u X60_pq; cond hold 0.528 strata 0.528; headline=True
- X60 30 ASIA: r13_u X60_pq; cond hold 0.566 strata 0.552; headline=True
- X60 30 LONDON: r13_u X60_pq; cond hold 0.526 strata 0.526; headline=True
- X60 30 NY: r13_u X60_pq; cond hold 0.500 strata 0.507; headline=True
- X60 0 POOLED: r13_u X60_sE; cond hold 0.515 strata 0.517; headline=True
- X60 0 ASIA: r13_u X60_sE; cond hold 0.528 strata 0.517; headline=True
- X60 0 LONDON: r13_u X60_sE; cond hold 0.516 strata 0.516; headline=True
- X60 0 NY: r13_u X60_sE; cond hold 0.506 strata 0.513; headline=True
- X60 5 POOLED: r13_u X60_sE; cond hold 0.496 strata 0.495; headline=True
- X60 5 ASIA: r13_u X60_sE; cond hold 0.524 strata 0.512; headline=True
- X60 5 LONDON: r13_u X60_sE; cond hold 0.471 strata 0.475; headline=True
- X60 5 NY: r13_u X60_sE; cond hold 0.500 strata 0.501; headline=True
- X60 15 POOLED: r13_u X60_sE; cond hold 0.508 strata 0.507; headline=True
- X60 15 ASIA: r13_u X60_sE; cond hold 0.534 strata 0.522; headline=True
- X60 15 LONDON: r13_u X60_sE; cond hold 0.473 strata 0.470; headline=True
- X60 15 NY: r13_u X60_sE; cond hold 0.509 strata 0.512; headline=True
- X60 30 POOLED: r13_u X60_sE; cond hold 0.527 strata 0.527; headline=True
- X60 30 ASIA: r13_u X60_sE; cond hold 0.563 strata 0.550; headline=True
- X60 30 LONDON: r13_u X60_sE; cond hold 0.523 strata 0.525; headline=True
- X60 30 NY: r13_u X60_sE; cond hold 0.506 strata 0.511; headline=True
- X16-cond-lgbm 0 POOLED: r13_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r13_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r13_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r13_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r13_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r13_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r13_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r13_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r13_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r13_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r13_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r13_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r13_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r13_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r13_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r13_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r13_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r13_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r13_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r13_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r13_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r13_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r13_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r13_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r13_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r13_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r13_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r13_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r13_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r13_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r13_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r13_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
