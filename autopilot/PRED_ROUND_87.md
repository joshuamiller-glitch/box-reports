# PRED ROUND 87 - block X3 round 12 - X3 round 12

Best HOLDOUT F-R AUC: +15 POOLED 0.542 [0.50,0.58] | ASIA 0.554 [0.49,0.62] | LONDON 0.551 [0.49,0.60] | NY 0.548 [0.49,0.60]
Best HOLDOUT F-R AUC: +30 POOLED 0.536 [0.50,0.57] | ASIA 0.557 [0.50,0.61] | LONDON 0.554 [0.48,0.61] | NY 0.567 [0.49,0.64]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.088 AUC, 5 of 5 economic conditions short.
not found - short by 0.088 AUC and 5 of 5 economic conditions

prereg 4ae1289998397a4c7e9b4d1c5e013b3a1032857235c1ac23847009721532f9b8 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X54 | +5 | ASIA | X54_fh | 0.536 [-,-] | 0.572 [0.52,0.63] | - | 0.572 | - | - | - | - | - | - | stack | short by 0.088 AUC, 5 of 5 econ |
| X53 | +30 | NY | X53 | 0.536 [-,-] | 0.567 [0.49,0.64] | - | 0.572 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | pre | LONDON | X55 | 0.529 [-,-] | 0.559 [0.50,0.62] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | +5 | LONDON | X55 | 0.522 [-,-] | 0.558 [0.49,0.62] | - | 0.566 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +30 | ASIA | X52_ntau | 0.546 [-,-] | 0.557 [0.50,0.61] | - | 0.561 | - | - | - | - | - | - | stack | short by 0.103 AUC, 5 of 5 econ |
| X54 | pre | ASIA | X54_fh | 0.535 [-,-] | 0.556 [0.49,0.63] | - | 0.551 | - | - | - | - | - | - | stack | short by 0.104 AUC, 5 of 5 econ |
| X54 | +30 | LONDON | X54_mc | 0.503 [-,-] | 0.554 [0.48,0.61] | - | 0.550 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | pre | ASIA | X51a | 0.531 [-,-] | 0.554 [0.50,0.60] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.106 AUC, 5 of 5 econ |
| X54 | +5 | ASIA | X54_mc | 0.525 [-,-] | 0.554 [0.48,0.62] | - | 0.543 | - | - | - | - | - | - | stack | short by 0.106 AUC, 5 of 5 econ |
| X51 | +15 | ASIA | X51b | 0.535 [-,-] | 0.554 [0.49,0.62] | - | 0.549 | - | - | - | - | - | - | stack | short by 0.106 AUC, 5 of 5 econ |
| X55 | +15 | ASIA | X55 | 0.524 [-,-] | 0.551 [0.50,0.61] | - | 0.552 | - | - | - | - | - | - | stack | short by 0.109 AUC, 5 of 5 econ |
| X55 | +15 | LONDON | X55 | 0.518 [-,-] | 0.551 [0.49,0.60] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +15 | LONDON | X54_mc | 0.531 [-,-] | 0.550 [0.47,0.62] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +30 | ASIA | X51a | 0.548 [-,-] | 0.549 [0.48,0.61] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.111 AUC, 5 of 5 econ |
| X52 | pre | LONDON | X52_ntau | 0.505 [-,-] | 0.549 [0.48,0.62] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | NY | X52_comb | 0.520 [-,-] | 0.548 [0.49,0.60] | - | 0.562 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | pre | NY | X52_ntau | 0.529 [-,-] | 0.547 [0.49,0.62] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +15 | ASIA | X54_mc | 0.529 [-,-] | 0.546 [0.49,0.61] | - | 0.538 | - | - | - | - | - | - | stack | short by 0.114 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | ASIA | X52_comb | 0.537 [-,-] | 0.545 [0.49,0.60] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| X54 | +15 | LONDON | X54_fh | 0.513 [-,-] | 0.544 [0.47,0.61] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | pre | LONDON | X51b | 0.521 [-,-] | 0.544 [0.47,0.61] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | +30 | LONDON | X55 | 0.509 [-,-] | 0.544 [0.48,0.60] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | pre | LONDON | X54_mc | 0.536 [-,-] | 0.543 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | pre | POOLED | X52_ntau | 0.519 [-,-] | 0.543 [0.51,0.58] | - | 0.546 | - | - | - | - | - | - | stack | promising: short by 0.137 AUC, 5 of 5 econ |
| X52 | +5 | LONDON | X52_ntau | 0.485 [-,-] | 0.543 [0.50,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | +15 | POOLED | X51b | 0.524 [-,-] | 0.542 [0.50,0.58] | - | 0.540 | - | - | - | - | - | - | stack | promising: short by 0.138 AUC, 5 of 5 econ |
| X51 | +15 | LONDON | X51b | 0.513 [-,-] | 0.542 [0.47,0.61] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X54 | pre | ASIA | X54_mc | 0.520 [-,-] | 0.538 [0.47,0.61] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X54 | +15 | ASIA | X54_fh | 0.521 [-,-] | 0.537 [0.48,0.61] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X52 | +30 | POOLED | X52_ntau | 0.521 [-,-] | 0.536 [0.50,0.57] | - | 0.539 | - | - | - | - | - | - | stack | promising: short by 0.144 AUC, 5 of 5 econ |
| X54 | +15 | POOLED | X54_mc | 0.525 [-,-] | 0.536 [0.49,0.58] | - | 0.535 | - | - | - | - | - | - | stack | short by 0.144 AUC, 5 of 5 econ |
| X51 | pre | ASIA | X51b | 0.522 [-,-] | 0.536 [0.48,0.59] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X51 | +30 | LONDON | X51b | 0.504 [-,-] | 0.536 [0.47,0.60] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +30 | POOLED | X54_mc | 0.509 [-,-] | 0.535 [0.50,0.57] | - | 0.535 | - | - | - | - | - | - | stack | promising: short by 0.145 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X51a | +15 | LONDON | X51a | 0.511 [-,-] | 0.535 [0.47,0.59] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | pre | POOLED | X54_fh | 0.525 [-,-] | 0.534 [0.51,0.57] | - | 0.537 | - | - | - | - | - | - | stack | promising: short by 0.146 AUC, 5 of 5 econ |
| X54 | +15 | POOLED | X54_fh | 0.516 [-,-] | 0.534 [0.49,0.58] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.146 AUC, 5 of 5 econ |
| X51a | +30 | POOLED | X51a | 0.520 [-,-] | 0.533 [0.50,0.57] | - | 0.532 | - | - | - | - | - | - | stack | promising: short by 0.147 AUC, 5 of 5 econ |
| X53 | +5 | NY | X53 | 0.519 [-,-] | 0.532 [0.47,0.58] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +5 | LONDON | X54_mc | 0.517 [-,-] | 0.531 [0.47,0.59] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | LONDON | X52_comb | 0.535 [-,-] | 0.531 [0.46,0.60] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X52 | pre | ASIA | X52_comb | 0.523 [-,-] | 0.531 [0.47,0.60] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X51a | pre | LONDON | X51a | 0.511 [-,-] | 0.530 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +30 | LONDON | X51a | 0.492 [-,-] | 0.529 [0.46,0.60] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +15 | ASIA | X51a | 0.520 [-,-] | 0.529 [0.47,0.58] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| X54 | +30 | ASIA | X54_mc | 0.513 [-,-] | 0.529 [0.47,0.59] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| X52 | +5 | ASIA | X52_tau | 0.496 [-,-] | 0.529 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X54 | pre | POOLED | X54_mc | 0.519 [-,-] | 0.529 [0.50,0.56] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X55 | pre | POOLED | X55 | 0.517 [-,-] | 0.527 [0.50,0.56] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | NY | X52_tau | 0.496 [-,-] | 0.527 [0.47,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +30 | NY | X52_ntau | 0.519 [-,-] | 0.526 [0.47,0.59] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X55 | +5 | ASIA | X55 | 0.514 [-,-] | 0.526 [0.46,0.59] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.134 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X55 | +30 | ASIA | X55 | 0.519 [-,-] | 0.525 [0.47,0.59] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X52 | +15 | ASIA | X52_ntau | 0.524 [-,-] | 0.525 [0.46,0.59] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X51 | +5 | LONDON | X51b | 0.510 [-,-] | 0.525 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | pre | POOLED | X51b | 0.512 [-,-] | 0.525 [0.48,0.57] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X54 | +30 | ASIA | X54_fh | 0.521 [-,-] | 0.524 [0.47,0.58] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X54 | pre | LONDON | X54_fh | 0.521 [-,-] | 0.524 [0.47,0.58] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | +30 | POOLED | X51b | 0.516 [-,-] | 0.524 [0.48,0.56] | - | 0.523 | - | - | - | - | - | - | stack | promising: short by 0.156 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | +15 | POOLED | X55 | 0.509 [-,-] | 0.523 [0.49,0.56] | - | 0.525 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X51 | +15 | NY | X51b | 0.519 [-,-] | 0.523 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +30 | POOLED | X53 | 0.515 [-,-] | 0.522 [0.49,0.55] | - | 0.521 | - | - | - | - | - | - | stack | promising: short by 0.158 AUC, 5 of 5 econ |
| X55 | pre | ASIA | X55 | 0.517 [-,-] | 0.522 [0.46,0.59] | - | 0.530 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +5 | POOLED | X52_ntau | 0.502 [-,-] | 0.521 [0.49,0.56] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X51 | +5 | ASIA | X51b | 0.523 [-,-] | 0.521 [0.47,0.57] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | pre | LONDON | X53 | 0.498 [-,-] | 0.520 [0.46,0.58] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +5 | POOLED | X54_mc | 0.505 [-,-] | 0.519 [0.48,0.55] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X52 | pre | ASIA | X52_ntau | 0.542 [-,-] | 0.519 [0.47,0.58] | - | 0.522 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X54 | +5 | POOLED | X54_fh | 0.505 [-,-] | 0.519 [0.48,0.55] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X52 | +15 | POOLED | X52_comb | 0.518 [-,-] | 0.519 [0.48,0.56] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | +30 | NY | X51b | 0.512 [-,-] | 0.518 [0.45,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +15 | POOLED | X51a | 0.514 [-,-] | 0.517 [0.48,0.55] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X55 | +30 | POOLED | X55 | 0.511 [-,-] | 0.517 [0.49,0.55] | - | 0.513 | - | - | - | - | - | - | stack | promising: short by 0.163 AUC, 5 of 5 econ |
| X54 | pre | NY | X54_fh | 0.515 [-,-] | 0.516 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +15 | NY | X54_fh | 0.511 [-,-] | 0.516 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | pre | POOLED | X51a | 0.507 [-,-] | 0.515 [0.47,0.55] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X54 | +30 | NY | X54_mc | 0.507 [-,-] | 0.514 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +5 | LONDON | X54_fh | 0.505 [-,-] | 0.514 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X51 | +5 | POOLED | X51b | 0.512 [-,-] | 0.512 [0.47,0.55] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X51a | +30 | NY | X51a | 0.515 [-,-] | 0.512 [0.46,0.57] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | +5 | POOLED | X55 | 0.503 [-,-] | 0.511 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X54 | +15 | NY | X54_mc | 0.511 [-,-] | 0.511 [0.45,0.57] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +15 | LONDON | X53 | 0.499 [-,-] | 0.510 [0.44,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +30 | POOLED | X54_fh | 0.502 [-,-] | 0.510 [0.48,0.54] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X52 | +15 | LONDON | X52_ntau | 0.480 [-,-] | 0.509 [0.43,0.57] | - | 0.511 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | POOLED | X52_ntau | 0.506 [-,-] | 0.509 [0.47,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X52 | +30 | LONDON | X52_comb | 0.517 [-,-] | 0.508 [0.43,0.59] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | NY | X52_ntau | 0.514 [-,-] | 0.508 [0.44,0.58] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +30 | ASIA | X53 | 0.517 [-,-] | 0.508 [0.45,0.56] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X51 | +30 | ASIA | X51b | 0.523 [-,-] | 0.507 [0.45,0.57] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X52 | +30 | NY | X52_comb | 0.489 [-,-] | 0.505 [0.44,0.58] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | pre | NY | X55 | 0.503 [-,-] | 0.504 [0.44,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X52 | +30 | LONDON | X52_tau | 0.514 [-,-] | 0.502 [0.44,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | pre | POOLED | X53 | 0.494 [-,-] | 0.501 [0.46,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X54 | pre | NY | X54_mc | 0.498 [-,-] | 0.500 [0.44,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +30 | LONDON | X54_fh | 0.492 [-,-] | 0.499 [0.43,0.57] | - | 0.493 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +30 | LONDON | X52_ntau | 0.486 [-,-] | 0.498 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +5 | LONDON | X51a | 0.485 [-,-] | 0.497 [0.43,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51 | +5 | NY | X51b | 0.503 [-,-] | 0.497 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +15 | ASIA | X53 | 0.468 [-,-] | 0.496 [0.44,0.55] | - | 0.490 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X51 | pre | NY | X51b | 0.487 [-,-] | 0.496 [0.43,0.56] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | pre | ASIA | X53 | 0.490 [-,-] | 0.496 [0.44,0.54] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | pre | LONDON | X52_comb | 0.508 [-,-] | 0.493 [0.43,0.56] | - | 0.491 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +5 | POOLED | X53 | 0.485 [-,-] | 0.493 [0.45,0.53] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X53 | +5 | LONDON | X53 | 0.459 [-,-] | 0.493 [0.42,0.56] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | POOLED | X52_comb | 0.504 [-,-] | 0.493 [0.46,0.53] | - | 0.491 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | NY | X52_tau | 0.486 [-,-] | 0.492 [0.42,0.56] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +30 | NY | X54_fh | 0.487 [-,-] | 0.492 [0.44,0.55] | - | 0.496 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | LONDON | X52_comb | 0.523 [-,-] | 0.491 [0.42,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | POOLED | X52_tau | 0.494 [-,-] | 0.491 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - | stack | short by 0.189 AUC, 5 of 5 econ |
| X52 | +15 | LONDON | X52_tau | 0.520 [-,-] | 0.491 [0.43,0.57] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +15 | NY | X51a | 0.510 [-,-] | 0.490 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | pre | NY | X53 | 0.492 [-,-] | 0.489 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | +5 | NY | X51a | 0.483 [-,-] | 0.489 [0.43,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +30 | POOLED | X52_comb | 0.500 [-,-] | 0.487 [0.45,0.53] | - | 0.486 | - | - | - | - | - | - | stack | short by 0.193 AUC, 5 of 5 econ |
| X51a | +5 | POOLED | X51a | 0.488 [-,-] | 0.487 [0.45,0.52] | - | 0.485 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X53 | +15 | POOLED | X53 | 0.478 [-,-] | 0.487 [0.45,0.52] | - | 0.485 | - | - | - | - | - | - | stack | short by 0.193 AUC, 5 of 5 econ |
| X53 | +30 | LONDON | X53 | 0.487 [-,-] | 0.486 [0.41,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X52 | pre | POOLED | X52_comb | 0.498 [-,-] | 0.486 [0.45,0.52] | - | 0.480 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | pre | NY | X52_comb | 0.477 [-,-] | 0.486 [0.42,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | ASIA | X52_comb | 0.503 [-,-] | 0.486 [0.43,0.55] | - | 0.466 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +5 | NY | X52_comb | 0.465 [-,-] | 0.484 [0.43,0.54] | - | 0.498 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | pre | ASIA | X52_tau | 0.458 [-,-] | 0.481 [0.42,0.53] | - | 0.478 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +5 | POOLED | X52_tau | 0.498 [-,-] | 0.479 [0.44,0.51] | - | 0.478 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X51a | +5 | ASIA | X51a | 0.498 [-,-] | 0.479 [0.42,0.53] | - | 0.472 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X55 | +30 | NY | X55 | 0.498 [-,-] | 0.476 [0.43,0.54] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | ASIA | X52_tau | 0.476 [-,-] | 0.475 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +30 | NY | X52_tau | 0.481 [-,-] | 0.474 [0.41,0.53] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X51a | pre | NY | X51a | 0.478 [-,-] | 0.473 [0.41,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +15 | NY | X52_ntau | 0.504 [-,-] | 0.473 [0.41,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X55 | +15 | NY | X55 | 0.483 [-,-] | 0.472 [0.42,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X54 | +5 | NY | X54_mc | 0.468 [-,-] | 0.471 [0.40,0.53] | - | 0.473 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +5 | ASIA | X52_ntau | 0.504 [-,-] | 0.471 [0.41,0.54] | - | 0.472 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| X54 | +5 | NY | X54_fh | 0.470 [-,-] | 0.468 [0.40,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +30 | ASIA | X52_comb | 0.510 [-,-] | 0.464 [0.41,0.52] | - | 0.457 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | +30 | POOLED | X52_tau | 0.479 [-,-] | 0.464 [0.43,0.50] | - | 0.461 | - | - | - | - | - | - | stack | short by 0.216 AUC, 5 of 5 econ |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X52 | +5 | LONDON | X52_tau | 0.515 [-,-] | 0.457 [0.39,0.50] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | pre | POOLED | X52_tau | 0.481 [-,-] | 0.457 [0.42,0.49] | - | 0.454 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X55 | +5 | NY | X55 | 0.471 [-,-] | 0.455 [0.40,0.52] | - | 0.451 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X53 | +15 | NY | X53 | 0.469 [-,-] | 0.454 [0.40,0.52] | - | 0.452 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | pre | NY | X52_tau | 0.471 [-,-] | 0.453 [0.38,0.51] | - | 0.455 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X53 | +5 | ASIA | X53 | 0.474 [-,-] | 0.452 [0.38,0.52] | - | 0.446 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X52 | pre | LONDON | X52_tau | 0.495 [-,-] | 0.451 [0.38,0.52] | - | 0.454 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X52 | +30 | ASIA | X52_tau | 0.454 [-,-] | 0.443 [0.39,0.50] | - | 0.439 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X51a 0 POOLED: r12_u X51a; cond hold 0.515 strata 0.514; headline=True
- X51a 0 ASIA: r12_u X51a; cond hold 0.554 strata 0.548; headline=True
- X51a 0 LONDON: r12_u X51a; cond hold 0.530 strata 0.528; headline=True
- X51a 0 NY: r12_u X51a; cond hold 0.473 strata 0.475; headline=True
- X51a 5 POOLED: r12_u X51a; cond hold 0.487 strata 0.485; headline=True
- X51a 5 ASIA: r12_u X51a; cond hold 0.479 strata 0.472; headline=True
- X51a 5 LONDON: r12_u X51a; cond hold 0.497 strata 0.500; headline=True
- X51a 5 NY: r12_u X51a; cond hold 0.489 strata 0.490; headline=True
- X51a 15 POOLED: r12_u X51a; cond hold 0.517 strata 0.519; headline=True
- X51a 15 ASIA: r12_u X51a; cond hold 0.529 strata 0.528; headline=True
- X51a 15 LONDON: r12_u X51a; cond hold 0.535 strata 0.535; headline=True
- X51a 15 NY: r12_u X51a; cond hold 0.490 strata 0.489; headline=True
- X51a 30 POOLED: r12_u X51a; cond hold 0.533 strata 0.532; headline=True
- X51a 30 ASIA: r12_u X51a; cond hold 0.549 strata 0.547; headline=True
- X51a 30 LONDON: r12_u X51a; cond hold 0.529 strata 0.531; headline=True
- X51a 30 NY: r12_u X51a; cond hold 0.512 strata 0.514; headline=True
- X51 0 POOLED: r12_u X51b; cond hold 0.525 strata 0.525; headline=True
- X51 0 ASIA: r12_u X51b; cond hold 0.536 strata 0.533; headline=True
- X51 0 LONDON: r12_u X51b; cond hold 0.544 strata 0.545; headline=True
- X51 0 NY: r12_u X51b; cond hold 0.496 strata 0.498; headline=True
- X51 5 POOLED: r12_u X51b; cond hold 0.512 strata 0.512; headline=True
- X51 5 ASIA: r12_u X51b; cond hold 0.521 strata 0.517; headline=True
- X51 5 LONDON: r12_u X51b; cond hold 0.525 strata 0.527; headline=True
- X51 5 NY: r12_u X51b; cond hold 0.497 strata 0.494; headline=True
- X51 15 POOLED: r12_u X51b; cond hold 0.542 strata 0.540; headline=True
- X51 15 ASIA: r12_u X51b; cond hold 0.554 strata 0.549; headline=True
- X51 15 LONDON: r12_u X51b; cond hold 0.542 strata 0.539; headline=True
- X51 15 NY: r12_u X51b; cond hold 0.523 strata 0.522; headline=True
- X51 30 POOLED: r12_u X51b; cond hold 0.524 strata 0.523; headline=True
- X51 30 ASIA: r12_u X51b; cond hold 0.507 strata 0.506; headline=True
- X51 30 LONDON: r12_u X51b; cond hold 0.536 strata 0.533; headline=True
- X51 30 NY: r12_u X51b; cond hold 0.518 strata 0.517; headline=True
- X52 0 POOLED: r12_u X52_tau; cond hold 0.457 strata 0.454; headline=True
- X52 0 ASIA: r12_u X52_tau; cond hold 0.481 strata 0.478; headline=True
- X52 0 LONDON: r12_u X52_tau; cond hold 0.451 strata 0.454; headline=True
- X52 0 NY: r12_u X52_tau; cond hold 0.453 strata 0.455; headline=True
- X52 5 POOLED: r12_u X52_tau; cond hold 0.479 strata 0.478; headline=True
- X52 5 ASIA: r12_u X52_tau; cond hold 0.529 strata 0.528; headline=True
- X52 5 LONDON: r12_u X52_tau; cond hold 0.457 strata 0.458; headline=True
- X52 5 NY: r12_u X52_tau; cond hold 0.492 strata 0.497; headline=True
- X52 15 POOLED: r12_u X52_tau; cond hold 0.491 strata 0.489; headline=True
- X52 15 ASIA: r12_u X52_tau; cond hold 0.475 strata 0.468; headline=True
- X52 15 LONDON: r12_u X52_tau; cond hold 0.491 strata 0.489; headline=True
- X52 15 NY: r12_u X52_tau; cond hold 0.527 strata 0.525; headline=True
- X52 30 POOLED: r12_u X52_tau; cond hold 0.464 strata 0.461; headline=True
- X52 30 ASIA: r12_u X52_tau; cond hold 0.443 strata 0.439; headline=True
- X52 30 LONDON: r12_u X52_tau; cond hold 0.502 strata 0.505; headline=True
- X52 30 NY: r12_u X52_tau; cond hold 0.474 strata 0.485; headline=True
- X52 0 POOLED: r12_u X52_ntau; cond hold 0.543 strata 0.546; headline=True
- X52 0 ASIA: r12_u X52_ntau; cond hold 0.519 strata 0.522; headline=True
- X52 0 LONDON: r12_u X52_ntau; cond hold 0.549 strata 0.546; headline=True
- X52 0 NY: r12_u X52_ntau; cond hold 0.547 strata 0.545; headline=True
- X52 5 POOLED: r12_u X52_ntau; cond hold 0.521 strata 0.522; headline=True
- X52 5 ASIA: r12_u X52_ntau; cond hold 0.471 strata 0.472; headline=True
- X52 5 LONDON: r12_u X52_ntau; cond hold 0.543 strata 0.542; headline=True
- X52 5 NY: r12_u X52_ntau; cond hold 0.508 strata 0.503; headline=True
- X52 15 POOLED: r12_u X52_ntau; cond hold 0.509 strata 0.511; headline=True
- X52 15 ASIA: r12_u X52_ntau; cond hold 0.525 strata 0.532; headline=True
- X52 15 LONDON: r12_u X52_ntau; cond hold 0.509 strata 0.511; headline=True
- X52 15 NY: r12_u X52_ntau; cond hold 0.473 strata 0.475; headline=True
- X52 30 POOLED: r12_u X52_ntau; cond hold 0.536 strata 0.539; headline=True
- X52 30 ASIA: r12_u X52_ntau; cond hold 0.557 strata 0.561; headline=True
- X52 30 LONDON: r12_u X52_ntau; cond hold 0.498 strata 0.495; headline=True
- X52 30 NY: r12_u X52_ntau; cond hold 0.526 strata 0.515; headline=True
- X52 0 POOLED: r12_u X52_comb; cond hold 0.486 strata 0.480; headline=True
- X52 0 ASIA: r12_u X52_comb; cond hold 0.531 strata 0.516; headline=True
- X52 0 LONDON: r12_u X52_comb; cond hold 0.493 strata 0.491; headline=True
- X52 0 NY: r12_u X52_comb; cond hold 0.486 strata 0.489; headline=True
- X52 5 POOLED: r12_u X52_comb; cond hold 0.493 strata 0.491; headline=True
- X52 5 ASIA: r12_u X52_comb; cond hold 0.545 strata 0.533; headline=True
- X52 5 LONDON: r12_u X52_comb; cond hold 0.491 strata 0.490; headline=True
- X52 5 NY: r12_u X52_comb; cond hold 0.484 strata 0.498; headline=True
- X52 15 POOLED: r12_u X52_comb; cond hold 0.519 strata 0.514; headline=True
- X52 15 ASIA: r12_u X52_comb; cond hold 0.486 strata 0.466; headline=True
- X52 15 LONDON: r12_u X52_comb; cond hold 0.531 strata 0.517; headline=True
- X52 15 NY: r12_u X52_comb; cond hold 0.548 strata 0.562; headline=True
- X52 30 POOLED: r12_u X52_comb; cond hold 0.487 strata 0.486; headline=True
- X52 30 ASIA: r12_u X52_comb; cond hold 0.464 strata 0.457; headline=True
- X52 30 LONDON: r12_u X52_comb; cond hold 0.508 strata 0.503; headline=True
- X52 30 NY: r12_u X52_comb; cond hold 0.505 strata 0.512; headline=True
- X53 0 POOLED: r12_u X53; cond hold 0.501 strata 0.502; headline=True
- X53 0 ASIA: r12_u X53; cond hold 0.496 strata 0.497; headline=True
- X53 0 LONDON: r12_u X53; cond hold 0.520 strata 0.527; headline=True
- X53 0 NY: r12_u X53; cond hold 0.489 strata 0.490; headline=True
- X53 5 POOLED: r12_u X53; cond hold 0.493 strata 0.495; headline=True
- X53 5 ASIA: r12_u X53; cond hold 0.452 strata 0.446; headline=True
- X53 5 LONDON: r12_u X53; cond hold 0.493 strata 0.496; headline=True
- X53 5 NY: r12_u X53; cond hold 0.532 strata 0.528; headline=True
- X53 15 POOLED: r12_u X53; cond hold 0.487 strata 0.485; headline=True
- X53 15 ASIA: r12_u X53; cond hold 0.496 strata 0.490; headline=True
- X53 15 LONDON: r12_u X53; cond hold 0.510 strata 0.510; headline=True
- X53 15 NY: r12_u X53; cond hold 0.454 strata 0.452; headline=True
- X53 30 POOLED: r12_u X53; cond hold 0.522 strata 0.521; headline=True
- X53 30 ASIA: r12_u X53; cond hold 0.508 strata 0.508; headline=True
- X53 30 LONDON: r12_u X53; cond hold 0.486 strata 0.485; headline=True
- X53 30 NY: r12_u X53; cond hold 0.567 strata 0.572; headline=True
- X54 0 POOLED: r12_u X54_fh; cond hold 0.534 strata 0.537; headline=True
- X54 0 ASIA: r12_u X54_fh; cond hold 0.556 strata 0.551; headline=True
- X54 0 LONDON: r12_u X54_fh; cond hold 0.524 strata 0.525; headline=True
- X54 0 NY: r12_u X54_fh; cond hold 0.516 strata 0.523; headline=True
- X54 5 POOLED: r12_u X54_fh; cond hold 0.519 strata 0.520; headline=True
- X54 5 ASIA: r12_u X54_fh; cond hold 0.572 strata 0.572; headline=True
- X54 5 LONDON: r12_u X54_fh; cond hold 0.514 strata 0.513; headline=True
- X54 5 NY: r12_u X54_fh; cond hold 0.468 strata 0.468; headline=True
- X54 15 POOLED: r12_u X54_fh; cond hold 0.534 strata 0.533; headline=True
- X54 15 ASIA: r12_u X54_fh; cond hold 0.537 strata 0.528; headline=True
- X54 15 LONDON: r12_u X54_fh; cond hold 0.544 strata 0.537; headline=True
- X54 15 NY: r12_u X54_fh; cond hold 0.516 strata 0.520; headline=True
- X54 30 POOLED: r12_u X54_fh; cond hold 0.510 strata 0.507; headline=True
- X54 30 ASIA: r12_u X54_fh; cond hold 0.524 strata 0.514; headline=True
- X54 30 LONDON: r12_u X54_fh; cond hold 0.499 strata 0.493; headline=True
- X54 30 NY: r12_u X54_fh; cond hold 0.492 strata 0.496; headline=True
- X54 0 POOLED: r12_u X54_mc; cond hold 0.529 strata 0.531; headline=True
- X54 0 ASIA: r12_u X54_mc; cond hold 0.538 strata 0.532; headline=True
- X54 0 LONDON: r12_u X54_mc; cond hold 0.543 strata 0.542; headline=True
- X54 0 NY: r12_u X54_mc; cond hold 0.500 strata 0.504; headline=True
- X54 5 POOLED: r12_u X54_mc; cond hold 0.519 strata 0.519; headline=True
- X54 5 ASIA: r12_u X54_mc; cond hold 0.554 strata 0.543; headline=True
- X54 5 LONDON: r12_u X54_mc; cond hold 0.531 strata 0.529; headline=True
- X54 5 NY: r12_u X54_mc; cond hold 0.471 strata 0.473; headline=True
- X54 15 POOLED: r12_u X54_mc; cond hold 0.536 strata 0.535; headline=True
- X54 15 ASIA: r12_u X54_mc; cond hold 0.546 strata 0.538; headline=True
- X54 15 LONDON: r12_u X54_mc; cond hold 0.550 strata 0.542; headline=True
- X54 15 NY: r12_u X54_mc; cond hold 0.511 strata 0.514; headline=True
- X54 30 POOLED: r12_u X54_mc; cond hold 0.535 strata 0.535; headline=True
- X54 30 ASIA: r12_u X54_mc; cond hold 0.529 strata 0.525; headline=True
- X54 30 LONDON: r12_u X54_mc; cond hold 0.554 strata 0.550; headline=True
- X54 30 NY: r12_u X54_mc; cond hold 0.514 strata 0.515; headline=True
- X55 0 POOLED: r12_u X55; cond hold 0.527 strata 0.528; headline=True
- X55 0 ASIA: r12_u X55; cond hold 0.522 strata 0.530; headline=True
- X55 0 LONDON: r12_u X55; cond hold 0.559 strata 0.551; headline=True
- X55 0 NY: r12_u X55; cond hold 0.504 strata 0.510; headline=True
- X55 5 POOLED: r12_u X55; cond hold 0.511 strata 0.517; headline=True
- X55 5 ASIA: r12_u X55; cond hold 0.526 strata 0.532; headline=True
- X55 5 LONDON: r12_u X55; cond hold 0.558 strata 0.566; headline=True
- X55 5 NY: r12_u X55; cond hold 0.455 strata 0.451; headline=True
- X55 15 POOLED: r12_u X55; cond hold 0.523 strata 0.525; headline=True
- X55 15 ASIA: r12_u X55; cond hold 0.551 strata 0.552; headline=True
- X55 15 LONDON: r12_u X55; cond hold 0.551 strata 0.551; headline=True
- X55 15 NY: r12_u X55; cond hold 0.472 strata 0.468; headline=True
- X55 30 POOLED: r12_u X55; cond hold 0.517 strata 0.513; headline=True
- X55 30 ASIA: r12_u X55; cond hold 0.525 strata 0.514; headline=True
- X55 30 LONDON: r12_u X55; cond hold 0.544 strata 0.545; headline=True
- X55 30 NY: r12_u X55; cond hold 0.476 strata 0.472; headline=True
- X16-cond-lgbm 0 POOLED: r12_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r12_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r12_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r12_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r12_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r12_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r12_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r12_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r12_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r12_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r12_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r12_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r12_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r12_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r12_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r12_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r12_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r12_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r12_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r12_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r12_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r12_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r12_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r12_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r12_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r12_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r12_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r12_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r12_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r12_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r12_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r12_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
