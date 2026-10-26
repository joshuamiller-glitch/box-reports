# PRED ROUND 67 - block X3 round 9 - X3 round 9

Best HOLDOUT F-R AUC: +15 POOLED 0.529 [0.49,0.57] | ASIA 0.541 [0.49,0.60] | LONDON 0.553 [0.48,0.62] | NY 0.522 [0.46,0.58]
Best HOLDOUT F-R AUC: +30 POOLED 0.538 [0.50,0.57] | ASIA 0.540 [0.48,0.60] | LONDON 0.547 [0.48,0.61] | NY 0.549 [0.49,0.61]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.119 AUC, 5 of 5 economic conditions short.
not found - short by 0.119 AUC and 5 of 5 economic conditions

prereg 5f43b2a4b4929a3a0ac3cb2d5ba1cba292ed35a456cf0ba84a71e182bc7a2a4d ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X36 | +15 | LONDON | X36b | 0.526 [-,-] | 0.553 [0.48,0.62] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +30 | NY | X39b | 0.516 [-,-] | 0.549 [0.49,0.61] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | NY | X38b | 0.522 [-,-] | 0.548 [0.49,0.61] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | LONDON | X36b | 0.531 [-,-] | 0.547 [0.48,0.61] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | pre | LONDON | X39o | 0.536 [-,-] | 0.545 [0.48,0.61] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | +15 | LONDON | XALL2 | 0.530 [-,-] | 0.543 [0.47,0.61] | - | 0.541 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | LONDON | X38b | 0.520 [-,-] | 0.542 [0.48,0.61] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +15 | ASIA | X39b | 0.547 [-,-] | 0.541 [0.49,0.60] | - | 0.535 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| XALL2 | +30 | LONDON | XALL2 | 0.527 [-,-] | 0.541 [0.48,0.61] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +15 | ASIA | X38b | 0.543 [-,-] | 0.541 [0.49,0.60] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X40 | +30 | LONDON | X40 | 0.536 [-,-] | 0.540 [0.48,0.61] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | POOLED | X38b | 0.527 [-,-] | 0.538 [0.50,0.57] | - | 0.534 | - | - | - | - | - | - | stack | promising: short by 0.142 AUC, 5 of 5 econ |
| X40 | +15 | LONDON | X40 | 0.517 [-,-] | 0.537 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +15 | LONDON | X37o | 0.540 [-,-] | 0.536 [0.48,0.60] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | pre | NY | X39b | 0.517 [-,-] | 0.536 [0.48,0.59] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | NY | X36b | 0.515 [-,-] | 0.535 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X37 | pre | NY | X37b | 0.523 [-,-] | 0.535 [0.48,0.59] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | pre | NY | X40 | 0.516 [-,-] | 0.534 [0.48,0.59] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +30 | LONDON | X39b | 0.522 [-,-] | 0.534 [0.47,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | pre | POOLED | X40 | 0.531 [-,-] | 0.533 [0.50,0.57] | - | 0.535 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X40 | pre | ASIA | X40 | 0.550 [-,-] | 0.533 [0.47,0.60] | - | 0.541 | - | - | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| X39 | +30 | POOLED | X39b | 0.525 [-,-] | 0.533 [0.49,0.56] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.147 AUC, 5 of 5 econ |
| X40 | pre | LONDON | X40 | 0.527 [-,-] | 0.532 [0.46,0.61] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +15 | LONDON | X37b | 0.503 [-,-] | 0.531 [0.46,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| XALL2 | pre | LONDON | XALL2 | 0.539 [-,-] | 0.530 [0.46,0.60] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | pre | LONDON | X36b | 0.525 [-,-] | 0.530 [0.46,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +15 | POOLED | X39b | 0.524 [-,-] | 0.529 [0.49,0.57] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X38 | +15 | POOLED | X38b | 0.518 [-,-] | 0.529 [0.48,0.57] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| XALL2 | +5 | LONDON | XALL2 | 0.527 [-,-] | 0.528 [0.46,0.60] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | POOLED | X36b | 0.531 [-,-] | 0.527 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | promising: short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X38 | +15 | LONDON | X38b | 0.499 [-,-] | 0.526 [0.45,0.59] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | pre | NY | XALL2 | 0.522 [-,-] | 0.525 [0.47,0.58] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +15 | POOLED | X40 | 0.524 [-,-] | 0.525 [0.48,0.57] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X40 | +15 | ASIA | X40 | 0.533 [-,-] | 0.524 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | pre | POOLED | XALL2 | 0.529 [-,-] | 0.523 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X38 | +15 | LONDON | X38o | 0.535 [-,-] | 0.523 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +15 | ASIA | X39o | 0.507 [-,-] | 0.523 [0.47,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| X37 | +15 | ASIA | X37b | 0.537 [-,-] | 0.522 [0.47,0.58] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X37 | +30 | NY | X37b | 0.504 [-,-] | 0.522 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | pre | POOLED | X37b | 0.516 [-,-] | 0.522 [0.49,0.56] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X39 | +15 | NY | X39b | 0.528 [-,-] | 0.522 [0.46,0.58] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +5 | LONDON | X38b | 0.525 [-,-] | 0.522 [0.46,0.58] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | ASIA | X38o | 0.503 [-,-] | 0.521 [0.46,0.58] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X38 | +30 | ASIA | X38b | 0.537 [-,-] | 0.521 [0.46,0.57] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X39 | +15 | LONDON | X39b | 0.495 [-,-] | 0.521 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | pre | LONDON | X37o | 0.527 [-,-] | 0.521 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +15 | ASIA | X38o | 0.518 [-,-] | 0.521 [0.47,0.57] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X37 | +15 | POOLED | X37b | 0.519 [-,-] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X36 | pre | POOLED | X36b | 0.523 [-,-] | 0.520 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | pre | ASIA | XALL2 | 0.531 [-,-] | 0.520 [0.46,0.58] | - | 0.518 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X38 | pre | NY | X38b | 0.503 [-,-] | 0.520 [0.47,0.57] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +30 | ASIA | X39o | 0.488 [-,-] | 0.520 [0.46,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X36 | pre | ASIA | X36b | 0.529 [-,-] | 0.520 [0.45,0.59] | - | 0.513 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X38 | pre | LONDON | X38b | 0.524 [-,-] | 0.520 [0.45,0.59] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | +15 | ASIA | XALL2 | 0.540 [-,-] | 0.520 [0.46,0.59] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X38 | +15 | NY | X38b | 0.510 [-,-] | 0.519 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +5 | LONDON | X40 | 0.521 [-,-] | 0.519 [0.45,0.59] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | pre | POOLED | X38b | 0.515 [-,-] | 0.519 [0.48,0.56] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | pre | POOLED | X39b | 0.513 [-,-] | 0.517 [0.48,0.55] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| XALL2 | +5 | ASIA | XALL2 | 0.536 [-,-] | 0.516 [0.46,0.59] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| XALL2 | +15 | POOLED | XALL2 | 0.528 [-,-] | 0.516 [0.48,0.56] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X38 | pre | LONDON | X38o | 0.513 [-,-] | 0.515 [0.45,0.58] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +5 | ASIA | X40 | 0.526 [-,-] | 0.515 [0.45,0.58] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X37 | pre | ASIA | X37b | 0.520 [-,-] | 0.515 [0.45,0.58] | - | 0.508 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X38 | pre | ASIA | X38o | 0.508 [-,-] | 0.515 [0.46,0.57] | - | 0.511 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X37 | +30 | LONDON | X37o | 0.535 [-,-] | 0.514 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +5 | LONDON | X39b | 0.521 [-,-] | 0.514 [0.46,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | pre | ASIA | X38b | 0.519 [-,-] | 0.514 [0.44,0.58] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X36 | pre | NY | X36b | 0.517 [-,-] | 0.514 [0.46,0.57] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +15 | NY | X40 | 0.519 [-,-] | 0.514 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +15 | POOLED | X36b | 0.522 [-,-] | 0.513 [0.47,0.56] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X39 | +15 | LONDON | X39o | 0.541 [-,-] | 0.513 [0.44,0.58] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| XALL2 | +30 | POOLED | XALL2 | 0.519 [-,-] | 0.513 [0.48,0.55] | - | 0.509 | - | - | - | - | - | - | stack | promising: short by 0.167 AUC, 5 of 5 econ |
| X39 | pre | POOLED | X39o | 0.501 [-,-] | 0.513 [0.48,0.54] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X39 | pre | LONDON | X39b | 0.517 [-,-] | 0.512 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X40 | +30 | POOLED | X40 | 0.525 [-,-] | 0.512 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X37 | +5 | LONDON | X37b | 0.511 [-,-] | 0.511 [0.44,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +15 | NY | X37b | 0.517 [-,-] | 0.510 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +15 | LONDON | X36o | 0.516 [-,-] | 0.510 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +5 | ASIA | X37b | 0.515 [-,-] | 0.510 [0.45,0.56] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X37 | +30 | POOLED | X37b | 0.510 [-,-] | 0.510 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X37 | pre | LONDON | X37b | 0.503 [-,-] | 0.510 [0.45,0.57] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +15 | ASIA | X36o | 0.543 [-,-] | 0.509 [0.45,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X39 | +30 | ASIA | X39b | 0.535 [-,-] | 0.509 [0.45,0.56] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X39 | +5 | ASIA | X39b | 0.525 [-,-] | 0.508 [0.45,0.57] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X36 | +5 | LONDON | X36b | 0.509 [-,-] | 0.508 [0.44,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +30 | POOLED | X37o | 0.516 [-,-] | 0.507 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X39 | pre | ASIA | X39o | 0.497 [-,-] | 0.507 [0.45,0.55] | - | 0.511 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X37 | +30 | ASIA | X37o | 0.506 [-,-] | 0.507 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X37 | +30 | LONDON | X37b | 0.496 [-,-] | 0.507 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL2 | +5 | POOLED | XALL2 | 0.513 [-,-] | 0.506 [0.47,0.55] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X37 | +15 | ASIA | X37o | 0.497 [-,-] | 0.506 [0.45,0.57] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X37 | +30 | NY | X37o | 0.510 [-,-] | 0.506 [0.44,0.58] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +5 | ASIA | X38o | 0.501 [-,-] | 0.505 [0.46,0.56] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X39 | +5 | LONDON | X39o | 0.505 [-,-] | 0.505 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +5 | POOLED | X40 | 0.515 [-,-] | 0.504 [0.47,0.55] | - | 0.505 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| X38 | pre | POOLED | X38o | 0.502 [-,-] | 0.504 [0.48,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| X36 | +5 | ASIA | X36b | 0.536 [-,-] | 0.503 [0.45,0.58] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X39 | +30 | POOLED | X39o | 0.512 [-,-] | 0.503 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| XALL2 | +30 | NY | XALL2 | 0.490 [-,-] | 0.503 [0.44,0.58] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X39 | pre | ASIA | X39b | 0.507 [-,-] | 0.503 [0.44,0.57] | - | 0.496 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X40 | +30 | ASIA | X40 | 0.535 [-,-] | 0.502 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.158 AUC, 5 of 5 econ |
| X38 | +30 | POOLED | X38o | 0.507 [-,-] | 0.501 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X39 | +15 | POOLED | X39o | 0.511 [-,-] | 0.501 [0.47,0.53] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X36 | +15 | ASIA | X36b | 0.534 [-,-] | 0.500 [0.45,0.56] | - | 0.489 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X39 | +5 | ASIA | X39o | 0.487 [-,-] | 0.500 [0.44,0.56] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X38 | +15 | POOLED | X38o | 0.505 [-,-] | 0.500 [0.46,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X36 | +5 | LONDON | X36o | 0.512 [-,-] | 0.500 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | LONDON | X36o | 0.519 [-,-] | 0.500 [0.44,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +5 | POOLED | X39b | 0.511 [-,-] | 0.499 [0.47,0.53] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X36 | +30 | ASIA | X36o | 0.519 [-,-] | 0.499 [0.43,0.56] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X39 | +30 | NY | X39o | 0.524 [-,-] | 0.499 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | pre | POOLED | X37o | 0.506 [-,-] | 0.498 [0.47,0.53] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.182 AUC, 5 of 5 econ |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| XALL2 | +30 | ASIA | XALL2 | 0.541 [-,-] | 0.498 [0.44,0.55] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X37 | +5 | ASIA | X37o | 0.489 [-,-] | 0.496 [0.44,0.56] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X37 | +5 | LONDON | X37o | 0.504 [-,-] | 0.495 [0.43,0.57] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | ASIA | X36b | 0.547 [-,-] | 0.495 [0.44,0.54] | - | 0.486 | - | - | - | - | - | - | stack | WF-only (dead) |
| X39 | pre | NY | X39o | 0.474 [-,-] | 0.495 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | LONDON | X38o | 0.523 [-,-] | 0.495 [0.43,0.57] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | pre | ASIA | X36o | 0.537 [-,-] | 0.494 [0.44,0.55] | - | 0.500 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X38 | +5 | LONDON | X38o | 0.509 [-,-] | 0.493 [0.43,0.55] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +5 | POOLED | X39o | 0.489 [-,-] | 0.493 [0.46,0.52] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X36 | +5 | POOLED | X36b | 0.510 [-,-] | 0.493 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X37 | +5 | POOLED | X37o | 0.496 [-,-] | 0.493 [0.45,0.53] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X38 | +5 | POOLED | X38o | 0.498 [-,-] | 0.493 [0.46,0.52] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +5 | POOLED | X37b | 0.500 [-,-] | 0.492 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| X38 | +5 | POOLED | X38b | 0.506 [-,-] | 0.492 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| X37 | pre | ASIA | X37o | 0.495 [-,-] | 0.492 [0.42,0.56] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X37 | +30 | ASIA | X37b | 0.527 [-,-] | 0.491 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - | stack | WF-only (dead) |
| X36 | +15 | POOLED | X36o | 0.514 [-,-] | 0.491 [0.45,0.54] | - | 0.488 | - | - | - | - | - | - | stack | short by 0.189 AUC, 5 of 5 econ |
| X40 | +30 | NY | X40 | 0.501 [-,-] | 0.490 [0.43,0.56] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +15 | POOLED | X37o | 0.503 [-,-] | 0.490 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - | stack | short by 0.190 AUC, 5 of 5 econ |
| X38 | +5 | ASIA | X38b | 0.514 [-,-] | 0.488 [0.43,0.56] | - | 0.475 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| XALL2 | +15 | NY | XALL2 | 0.514 [-,-] | 0.488 [0.43,0.55] | - | 0.487 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +5 | NY | X37o | 0.495 [-,-] | 0.487 [0.42,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +30 | NY | X38o | 0.494 [-,-] | 0.487 [0.41,0.55] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X36 | +15 | NY | X36b | 0.506 [-,-] | 0.486 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +5 | NY | X39b | 0.485 [-,-] | 0.486 [0.43,0.53] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | pre | LONDON | X36o | 0.499 [-,-] | 0.486 [0.43,0.55] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | POOLED | X36o | 0.507 [-,-] | 0.486 [0.45,0.53] | - | 0.482 | - | - | - | - | - | - | stack | short by 0.194 AUC, 5 of 5 econ |
| X39 | +30 | LONDON | X39o | 0.520 [-,-] | 0.485 [0.41,0.56] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | pre | NY | X37o | 0.499 [-,-] | 0.485 [0.42,0.55] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +5 | ASIA | X36o | 0.518 [-,-] | 0.484 [0.43,0.55] | - | 0.494 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X36 | +5 | POOLED | X36o | 0.504 [-,-] | 0.484 [0.45,0.53] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| XALL2 | +5 | NY | XALL2 | 0.478 [-,-] | 0.484 [0.43,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X40 | +5 | NY | X40 | 0.500 [-,-] | 0.482 [0.43,0.54] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +5 | NY | X36b | 0.486 [-,-] | 0.481 [0.42,0.54] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X39 | +5 | NY | X39o | 0.474 [-,-] | 0.480 [0.42,0.55] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | pre | NY | X38o | 0.482 [-,-] | 0.479 [0.40,0.55] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | pre | POOLED | X36o | 0.502 [-,-] | 0.479 [0.44,0.52] | - | 0.478 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X38 | +5 | NY | X38o | 0.483 [-,-] | 0.475 [0.41,0.54] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +5 | NY | X36o | 0.480 [-,-] | 0.472 [0.41,0.53] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X38 | +5 | NY | X38b | 0.478 [-,-] | 0.472 [0.42,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X36 | pre | NY | X36o | 0.474 [-,-] | 0.464 [0.41,0.53] | - | 0.466 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +30 | NY | X36o | 0.480 [-,-] | 0.463 [0.41,0.53] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X37 | +5 | NY | X37b | 0.475 [-,-] | 0.463 [0.40,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X36 | +15 | NY | X36o | 0.485 [-,-] | 0.461 [0.41,0.53] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X39 | +15 | NY | X39o | 0.484 [-,-] | 0.459 [0.40,0.52] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X38 | +15 | NY | X38o | 0.461 [-,-] | 0.452 [0.39,0.52] | - | 0.457 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| X37 | +15 | NY | X37o | 0.473 [-,-] | 0.425 [0.36,0.49] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X36 0 POOLED: r9_u X36b; cond hold 0.520 strata 0.518; headline=True
- X36 0 ASIA: r9_u X36b; cond hold 0.520 strata 0.513; headline=True
- X36 0 LONDON: r9_u X36b; cond hold 0.530 strata 0.520; headline=True
- X36 0 NY: r9_u X36b; cond hold 0.514 strata 0.526; headline=True
- X36 5 POOLED: r9_u X36b; cond hold 0.493 strata 0.491; headline=True
- X36 5 ASIA: r9_u X36b; cond hold 0.503 strata 0.493; headline=True
- X36 5 LONDON: r9_u X36b; cond hold 0.508 strata 0.509; headline=True
- X36 5 NY: r9_u X36b; cond hold 0.481 strata 0.492; headline=True
- X36 15 POOLED: r9_u X36b; cond hold 0.513 strata 0.510; headline=False
- X36 15 ASIA: r9_u X36b; cond hold 0.500 strata 0.489; headline=False
- X36 15 LONDON: r9_u X36b; cond hold 0.553 strata 0.546; headline=False
- X36 15 NY: r9_u X36b; cond hold 0.486 strata 0.486; headline=False
- X36 30 POOLED: r9_u X36b; cond hold 0.527 strata 0.523; headline=True
- X36 30 ASIA: r9_u X36b; cond hold 0.495 strata 0.486; headline=True
- X36 30 LONDON: r9_u X36b; cond hold 0.547 strata 0.539; headline=True
- X36 30 NY: r9_u X36b; cond hold 0.535 strata 0.537; headline=True
- X36 0 POOLED: r9_u X36o; cond hold 0.479 strata 0.478; headline=False
- X36 0 ASIA: r9_u X36o; cond hold 0.494 strata 0.500; headline=False
- X36 0 LONDON: r9_u X36o; cond hold 0.486 strata 0.481; headline=False
- X36 0 NY: r9_u X36o; cond hold 0.464 strata 0.466; headline=False
- X36 5 POOLED: r9_u X36o; cond hold 0.484 strata 0.484; headline=False
- X36 5 ASIA: r9_u X36o; cond hold 0.484 strata 0.494; headline=False
- X36 5 LONDON: r9_u X36o; cond hold 0.500 strata 0.500; headline=False
- X36 5 NY: r9_u X36o; cond hold 0.472 strata 0.478; headline=False
- X36 15 POOLED: r9_u X36o; cond hold 0.491 strata 0.488; headline=True
- X36 15 ASIA: r9_u X36o; cond hold 0.509 strata 0.513; headline=True
- X36 15 LONDON: r9_u X36o; cond hold 0.510 strata 0.507; headline=True
- X36 15 NY: r9_u X36o; cond hold 0.461 strata 0.469; headline=True
- X36 30 POOLED: r9_u X36o; cond hold 0.486 strata 0.482; headline=False
- X36 30 ASIA: r9_u X36o; cond hold 0.499 strata 0.499; headline=False
- X36 30 LONDON: r9_u X36o; cond hold 0.500 strata 0.504; headline=False
- X36 30 NY: r9_u X36o; cond hold 0.463 strata 0.465; headline=False
- X37 0 POOLED: r9_u X37b; cond hold 0.522 strata 0.520; headline=False
- X37 0 ASIA: r9_u X37b; cond hold 0.515 strata 0.508; headline=False
- X37 0 LONDON: r9_u X37b; cond hold 0.510 strata 0.507; headline=False
- X37 0 NY: r9_u X37b; cond hold 0.535 strata 0.539; headline=False
- X37 5 POOLED: r9_u X37b; cond hold 0.492 strata 0.490; headline=True
- X37 5 ASIA: r9_u X37b; cond hold 0.510 strata 0.501; headline=True
- X37 5 LONDON: r9_u X37b; cond hold 0.511 strata 0.507; headline=True
- X37 5 NY: r9_u X37b; cond hold 0.463 strata 0.467; headline=True
- X37 15 POOLED: r9_u X37b; cond hold 0.520 strata 0.517; headline=True
- X37 15 ASIA: r9_u X37b; cond hold 0.522 strata 0.506; headline=True
- X37 15 LONDON: r9_u X37b; cond hold 0.531 strata 0.527; headline=True
- X37 15 NY: r9_u X37b; cond hold 0.510 strata 0.512; headline=True
- X37 30 POOLED: r9_u X37b; cond hold 0.510 strata 0.506; headline=False
- X37 30 ASIA: r9_u X37b; cond hold 0.491 strata 0.482; headline=False
- X37 30 LONDON: r9_u X37b; cond hold 0.507 strata 0.503; headline=False
- X37 30 NY: r9_u X37b; cond hold 0.522 strata 0.527; headline=False
- X37 0 POOLED: r9_u X37o; cond hold 0.498 strata 0.496; headline=True
- X37 0 ASIA: r9_u X37o; cond hold 0.492 strata 0.486; headline=True
- X37 0 LONDON: r9_u X37o; cond hold 0.521 strata 0.523; headline=True
- X37 0 NY: r9_u X37o; cond hold 0.485 strata 0.491; headline=True
- X37 5 POOLED: r9_u X37o; cond hold 0.493 strata 0.494; headline=False
- X37 5 ASIA: r9_u X37o; cond hold 0.496 strata 0.497; headline=False
- X37 5 LONDON: r9_u X37o; cond hold 0.495 strata 0.500; headline=False
- X37 5 NY: r9_u X37o; cond hold 0.487 strata 0.491; headline=False
- X37 15 POOLED: r9_u X37o; cond hold 0.490 strata 0.489; headline=False
- X37 15 ASIA: r9_u X37o; cond hold 0.506 strata 0.505; headline=False
- X37 15 LONDON: r9_u X37o; cond hold 0.536 strata 0.539; headline=False
- X37 15 NY: r9_u X37o; cond hold 0.425 strata 0.429; headline=False
- X37 30 POOLED: r9_u X37o; cond hold 0.507 strata 0.506; headline=True
- X37 30 ASIA: r9_u X37o; cond hold 0.507 strata 0.506; headline=True
- X37 30 LONDON: r9_u X37o; cond hold 0.514 strata 0.513; headline=True
- X37 30 NY: r9_u X37o; cond hold 0.506 strata 0.508; headline=True
- X38 0 POOLED: r9_u X38b; cond hold 0.519 strata 0.519; headline=True
- X38 0 ASIA: r9_u X38b; cond hold 0.514 strata 0.512; headline=True
- X38 0 LONDON: r9_u X38b; cond hold 0.520 strata 0.517; headline=True
- X38 0 NY: r9_u X38b; cond hold 0.520 strata 0.528; headline=True
- X38 5 POOLED: r9_u X38b; cond hold 0.492 strata 0.491; headline=True
- X38 5 ASIA: r9_u X38b; cond hold 0.488 strata 0.475; headline=True
- X38 5 LONDON: r9_u X38b; cond hold 0.522 strata 0.519; headline=True
- X38 5 NY: r9_u X38b; cond hold 0.472 strata 0.475; headline=True
- X38 15 POOLED: r9_u X38b; cond hold 0.529 strata 0.527; headline=False
- X38 15 ASIA: r9_u X38b; cond hold 0.541 strata 0.531; headline=False
- X38 15 LONDON: r9_u X38b; cond hold 0.526 strata 0.522; headline=False
- X38 15 NY: r9_u X38b; cond hold 0.519 strata 0.520; headline=False
- X38 30 POOLED: r9_u X38b; cond hold 0.538 strata 0.534; headline=True
- X38 30 ASIA: r9_u X38b; cond hold 0.521 strata 0.509; headline=True
- X38 30 LONDON: r9_u X38b; cond hold 0.542 strata 0.535; headline=True
- X38 30 NY: r9_u X38b; cond hold 0.548 strata 0.551; headline=True
- X38 0 POOLED: r9_u X38o; cond hold 0.504 strata 0.502; headline=False
- X38 0 ASIA: r9_u X38o; cond hold 0.515 strata 0.511; headline=False
- X38 0 LONDON: r9_u X38o; cond hold 0.515 strata 0.513; headline=False
- X38 0 NY: r9_u X38o; cond hold 0.479 strata 0.478; headline=False
- X38 5 POOLED: r9_u X38o; cond hold 0.493 strata 0.492; headline=False
- X38 5 ASIA: r9_u X38o; cond hold 0.505 strata 0.500; headline=False
- X38 5 LONDON: r9_u X38o; cond hold 0.493 strata 0.492; headline=False
- X38 5 NY: r9_u X38o; cond hold 0.475 strata 0.480; headline=False
- X38 15 POOLED: r9_u X38o; cond hold 0.500 strata 0.499; headline=True
- X38 15 ASIA: r9_u X38o; cond hold 0.521 strata 0.519; headline=True
- X38 15 LONDON: r9_u X38o; cond hold 0.523 strata 0.519; headline=True
- X38 15 NY: r9_u X38o; cond hold 0.452 strata 0.457; headline=True
- X38 30 POOLED: r9_u X38o; cond hold 0.501 strata 0.499; headline=False
- X38 30 ASIA: r9_u X38o; cond hold 0.521 strata 0.517; headline=False
- X38 30 LONDON: r9_u X38o; cond hold 0.495 strata 0.498; headline=False
- X38 30 NY: r9_u X38o; cond hold 0.487 strata 0.483; headline=False
- X39 0 POOLED: r9_u X39b; cond hold 0.517 strata 0.518; headline=True
- X39 0 ASIA: r9_u X39b; cond hold 0.503 strata 0.496; headline=True
- X39 0 LONDON: r9_u X39b; cond hold 0.512 strata 0.516; headline=True
- X39 0 NY: r9_u X39b; cond hold 0.536 strata 0.544; headline=True
- X39 5 POOLED: r9_u X39b; cond hold 0.499 strata 0.498; headline=True
- X39 5 ASIA: r9_u X39b; cond hold 0.508 strata 0.497; headline=True
- X39 5 LONDON: r9_u X39b; cond hold 0.514 strata 0.510; headline=True
- X39 5 NY: r9_u X39b; cond hold 0.486 strata 0.489; headline=True
- X39 15 POOLED: r9_u X39b; cond hold 0.529 strata 0.527; headline=True
- X39 15 ASIA: r9_u X39b; cond hold 0.541 strata 0.535; headline=True
- X39 15 LONDON: r9_u X39b; cond hold 0.521 strata 0.516; headline=True
- X39 15 NY: r9_u X39b; cond hold 0.522 strata 0.522; headline=True
- X39 30 POOLED: r9_u X39b; cond hold 0.533 strata 0.529; headline=True
- X39 30 ASIA: r9_u X39b; cond hold 0.509 strata 0.497; headline=True
- X39 30 LONDON: r9_u X39b; cond hold 0.534 strata 0.527; headline=True
- X39 30 NY: r9_u X39b; cond hold 0.549 strata 0.552; headline=True
- X39 0 POOLED: r9_u X39o; cond hold 0.513 strata 0.513; headline=False
- X39 0 ASIA: r9_u X39o; cond hold 0.507 strata 0.511; headline=False
- X39 0 LONDON: r9_u X39o; cond hold 0.545 strata 0.546; headline=False
- X39 0 NY: r9_u X39o; cond hold 0.495 strata 0.500; headline=False
- X39 5 POOLED: r9_u X39o; cond hold 0.493 strata 0.493; headline=False
- X39 5 ASIA: r9_u X39o; cond hold 0.500 strata 0.498; headline=False
- X39 5 LONDON: r9_u X39o; cond hold 0.505 strata 0.503; headline=False
- X39 5 NY: r9_u X39o; cond hold 0.480 strata 0.483; headline=False
- X39 15 POOLED: r9_u X39o; cond hold 0.501 strata 0.500; headline=False
- X39 15 ASIA: r9_u X39o; cond hold 0.523 strata 0.521; headline=False
- X39 15 LONDON: r9_u X39o; cond hold 0.513 strata 0.515; headline=False
- X39 15 NY: r9_u X39o; cond hold 0.459 strata 0.461; headline=False
- X39 30 POOLED: r9_u X39o; cond hold 0.503 strata 0.502; headline=False
- X39 30 ASIA: r9_u X39o; cond hold 0.520 strata 0.521; headline=False
- X39 30 LONDON: r9_u X39o; cond hold 0.485 strata 0.485; headline=False
- X39 30 NY: r9_u X39o; cond hold 0.499 strata 0.494; headline=False
- X40 0 POOLED: r9_u X40; cond hold 0.533 strata 0.535; headline=True
- X40 0 ASIA: r9_u X40; cond hold 0.533 strata 0.541; headline=True
- X40 0 LONDON: r9_u X40; cond hold 0.532 strata 0.533; headline=True
- X40 0 NY: r9_u X40; cond hold 0.534 strata 0.538; headline=True
- X40 5 POOLED: r9_u X40; cond hold 0.504 strata 0.505; headline=True
- X40 5 ASIA: r9_u X40; cond hold 0.515 strata 0.515; headline=True
- X40 5 LONDON: r9_u X40; cond hold 0.519 strata 0.523; headline=True
- X40 5 NY: r9_u X40; cond hold 0.482 strata 0.479; headline=True
- X40 15 POOLED: r9_u X40; cond hold 0.525 strata 0.521; headline=True
- X40 15 ASIA: r9_u X40; cond hold 0.524 strata 0.522; headline=True
- X40 15 LONDON: r9_u X40; cond hold 0.537 strata 0.531; headline=True
- X40 15 NY: r9_u X40; cond hold 0.514 strata 0.511; headline=True
- X40 30 POOLED: r9_u X40; cond hold 0.512 strata 0.510; headline=True
- X40 30 ASIA: r9_u X40; cond hold 0.502 strata 0.502; headline=True
- X40 30 LONDON: r9_u X40; cond hold 0.540 strata 0.535; headline=True
- X40 30 NY: r9_u X40; cond hold 0.490 strata 0.492; headline=True
- XALL2 0 POOLED: r9_u XALL2; cond hold 0.523 strata 0.523; headline=True
- XALL2 0 ASIA: r9_u XALL2; cond hold 0.520 strata 0.518; headline=True
- XALL2 0 LONDON: r9_u XALL2; cond hold 0.530 strata 0.529; headline=True
- XALL2 0 NY: r9_u XALL2; cond hold 0.525 strata 0.529; headline=True
- XALL2 5 POOLED: r9_u XALL2; cond hold 0.506 strata 0.506; headline=True
- XALL2 5 ASIA: r9_u XALL2; cond hold 0.516 strata 0.511; headline=True
- XALL2 5 LONDON: r9_u XALL2; cond hold 0.528 strata 0.535; headline=True
- XALL2 5 NY: r9_u XALL2; cond hold 0.484 strata 0.482; headline=True
- XALL2 15 POOLED: r9_u XALL2; cond hold 0.516 strata 0.513; headline=True
- XALL2 15 ASIA: r9_u XALL2; cond hold 0.520 strata 0.513; headline=True
- XALL2 15 LONDON: r9_u XALL2; cond hold 0.543 strata 0.541; headline=True
- XALL2 15 NY: r9_u XALL2; cond hold 0.488 strata 0.487; headline=True
- XALL2 30 POOLED: r9_u XALL2; cond hold 0.513 strata 0.509; headline=True
- XALL2 30 ASIA: r9_u XALL2; cond hold 0.498 strata 0.493; headline=True
- XALL2 30 LONDON: r9_u XALL2; cond hold 0.541 strata 0.536; headline=True
- XALL2 30 NY: r9_u XALL2; cond hold 0.503 strata 0.505; headline=True
- X16-cond-lgbm 0 POOLED: r9_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r9_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r9_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r9_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r9_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r9_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r9_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r9_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r9_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r9_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r9_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r9_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r9_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r9_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r9_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r9_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r9_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r9_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r9_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r9_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r9_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r9_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r9_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r9_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r9_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r9_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r9_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r9_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r9_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r9_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r9_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r9_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
