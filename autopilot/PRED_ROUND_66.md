# PRED ROUND 66 - block X3 round 8 - X3 round 8

Best HOLDOUT F-R AUC: +15 POOLED 0.532 [0.49,0.58] | ASIA 0.553 [0.49,0.62] | LONDON 0.549 [0.47,0.62] | NY 0.520 [0.46,0.58]
Best HOLDOUT F-R AUC: +30 POOLED 0.527 [0.49,0.56] | ASIA 0.545 [0.48,0.60] | LONDON 0.524 [0.47,0.59] | NY 0.532 [0.47,0.60]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.107 AUC, 5 of 5 economic conditions short.
not found - short by 0.107 AUC and 5 of 5 economic conditions

prereg 6f9c08c7f50da0e67b91927308d4db5c61db8092df32b0d529e5ae3195439482 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X31 | +15 | ASIA | X31b | 0.547 [-,-] | 0.553 [0.49,0.62] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.107 AUC, 5 of 5 econ |
| X33 | +15 | LONDON | X33b | 0.524 [-,-] | 0.549 [0.47,0.62] | - | 0.547 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +15 | ASIA | X32o | 0.546 [-,-] | 0.548 [0.49,0.62] | - | 0.550 | - | - | - | - | - | - | stack | short by 0.112 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +30 | ASIA | X32b | 0.558 [-,-] | 0.545 [0.48,0.60] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.115 AUC, 5 of 5 econ |
| X34 | +15 | ASIA | X34b | 0.541 [-,-] | 0.544 [0.48,0.60] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.116 AUC, 5 of 5 econ |
| X34 | +15 | LONDON | X34b | 0.511 [-,-] | 0.543 [0.47,0.61] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +30 | ASIA | X31b | 0.555 [-,-] | 0.543 [0.48,0.59] | - | 0.537 | - | - | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X33 | pre | NY | X33b | 0.518 [-,-] | 0.539 [0.48,0.60] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | pre | LONDON | X35b | 0.518 [-,-] | 0.539 [0.48,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +30 | ASIA | X34b | 0.539 [-,-] | 0.538 [0.48,0.59] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X35 | +15 | LONDON | X35o | 0.550 [-,-] | 0.537 [0.48,0.61] | - | 0.540 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | pre | LONDON | X33o | 0.531 [-,-] | 0.537 [0.47,0.59] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +15 | ASIA | X32b | 0.545 [-,-] | 0.537 [0.47,0.60] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X35 | +15 | ASIA | X35o | 0.513 [-,-] | 0.536 [0.48,0.60] | - | 0.542 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X31 | +15 | LONDON | X31b | 0.520 [-,-] | 0.536 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +5 | ASIA | X31b | 0.533 [-,-] | 0.536 [0.48,0.59] | - | 0.526 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X33 | +5 | LONDON | X33b | 0.526 [-,-] | 0.536 [0.47,0.60] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X32 | +30 | ASIA | X32o | 0.542 [-,-] | 0.534 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| X35 | pre | LONDON | X35o | 0.529 [-,-] | 0.533 [0.47,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +30 | NY | X33o | 0.521 [-,-] | 0.532 [0.47,0.60] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +15 | POOLED | X31b | 0.524 [-,-] | 0.532 [0.49,0.58] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| X32 | pre | ASIA | X32o | 0.524 [-,-] | 0.532 [0.47,0.60] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X31 | +15 | LONDON | X31o | 0.530 [-,-] | 0.530 [0.46,0.60] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | pre | POOLED | X35b | 0.525 [-,-] | 0.529 [0.50,0.56] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X33 | +15 | LONDON | X33o | 0.540 [-,-] | 0.529 [0.46,0.60] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +30 | ASIA | X35o | 0.523 [-,-] | 0.529 [0.47,0.60] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X33 | pre | POOLED | X33b | 0.522 [-,-] | 0.528 [0.49,0.56] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X35 | pre | ASIA | X35b | 0.527 [-,-] | 0.528 [0.46,0.60] | - | 0.523 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X34 | pre | NY | X34b | 0.527 [-,-] | 0.528 [0.48,0.59] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +30 | NY | X34b | 0.494 [-,-] | 0.528 [0.47,0.59] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | pre | LONDON | X32b | 0.529 [-,-] | 0.527 [0.45,0.59] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +15 | ASIA | X35b | 0.536 [-,-] | 0.527 [0.46,0.60] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.133 AUC, 5 of 5 econ |
| X33 | +30 | POOLED | X33o | 0.522 [-,-] | 0.527 [0.49,0.56] | - | 0.528 | - | - | - | - | - | - | stack | promising: short by 0.153 AUC, 5 of 5 econ |
| X32 | pre | NY | X32b | 0.512 [-,-] | 0.527 [0.47,0.58] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | pre | LONDON | X33b | 0.531 [-,-] | 0.526 [0.46,0.59] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +15 | POOLED | X34b | 0.516 [-,-] | 0.526 [0.48,0.57] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X33 | +15 | ASIA | X33b | 0.541 [-,-] | 0.525 [0.46,0.59] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X35 | +5 | ASIA | X35b | 0.528 [-,-] | 0.525 [0.46,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X34 | +30 | POOLED | X34b | 0.510 [-,-] | 0.525 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | promising: short by 0.155 AUC, 5 of 5 econ |
| X33 | +30 | LONDON | X33o | 0.529 [-,-] | 0.524 [0.47,0.59] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +30 | ASIA | X33o | 0.511 [-,-] | 0.524 [0.47,0.58] | - | 0.526 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | pre | POOLED | X32b | 0.520 [-,-] | 0.523 [0.49,0.56] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X31 | +30 | POOLED | X31b | 0.514 [-,-] | 0.523 [0.49,0.56] | - | 0.519 | - | - | - | - | - | - | stack | promising: short by 0.157 AUC, 5 of 5 econ |
| X31 | pre | LONDON | X31b | 0.522 [-,-] | 0.522 [0.45,0.58] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +30 | LONDON | X31o | 0.540 [-,-] | 0.522 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +30 | LONDON | X32o | 0.540 [-,-] | 0.522 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | pre | NY | X31b | 0.511 [-,-] | 0.521 [0.47,0.57] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +5 | ASIA | X34b | 0.522 [-,-] | 0.521 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X35 | pre | NY | X35b | 0.529 [-,-] | 0.521 [0.46,0.58] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +15 | POOLED | X35b | 0.526 [-,-] | 0.521 [0.48,0.57] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +15 | POOLED | X33b | 0.524 [-,-] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X33 | +15 | ASIA | X33o | 0.502 [-,-] | 0.520 [0.47,0.58] | - | 0.519 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X32 | +30 | POOLED | X32b | 0.518 [-,-] | 0.520 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - | stack | promising: short by 0.160 AUC, 5 of 5 econ |
| X31 | pre | POOLED | X31b | 0.516 [-,-] | 0.520 [0.49,0.55] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X35 | +5 | LONDON | X35b | 0.513 [-,-] | 0.520 [0.44,0.59] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +5 | ASIA | X33b | 0.536 [-,-] | 0.520 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X35 | +5 | LONDON | X35o | 0.521 [-,-] | 0.519 [0.45,0.58] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +15 | LONDON | X34o | 0.531 [-,-] | 0.518 [0.46,0.59] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +15 | LONDON | X35b | 0.515 [-,-] | 0.518 [0.45,0.59] | - | 0.514 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | pre | ASIA | X31b | 0.515 [-,-] | 0.518 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X33 | +5 | LONDON | X33o | 0.513 [-,-] | 0.518 [0.46,0.59] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +15 | POOLED | X32b | 0.513 [-,-] | 0.518 [0.48,0.56] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +5 | ASIA | X32o | 0.522 [-,-] | 0.517 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X31 | pre | LONDON | X31o | 0.524 [-,-] | 0.516 [0.46,0.57] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | pre | ASIA | X33b | 0.515 [-,-] | 0.516 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X34 | +5 | LONDON | X34b | 0.527 [-,-] | 0.516 [0.45,0.58] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +30 | NY | X33b | 0.489 [-,-] | 0.516 [0.46,0.58] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +15 | NY | X35b | 0.528 [-,-] | 0.516 [0.46,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +30 | NY | X32b | 0.494 [-,-] | 0.516 [0.46,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | pre | POOLED | X34b | 0.520 [-,-] | 0.516 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X32 | +15 | LONDON | X32b | 0.501 [-,-] | 0.514 [0.43,0.58] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +30 | LONDON | X31b | 0.496 [-,-] | 0.514 [0.45,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +30 | POOLED | X33b | 0.509 [-,-] | 0.514 [0.48,0.54] | - | 0.510 | - | - | - | - | - | - | stack | promising: short by 0.166 AUC, 5 of 5 econ |
| X33 | +15 | POOLED | X33o | 0.513 [-,-] | 0.514 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X33 | +30 | ASIA | X33b | 0.542 [-,-] | 0.513 [0.45,0.56] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X33 | pre | ASIA | X33o | 0.485 [-,-] | 0.513 [0.45,0.57] | - | 0.518 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X34 | pre | LONDON | X34b | 0.523 [-,-] | 0.513 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | pre | ASIA | X32b | 0.522 [-,-] | 0.512 [0.44,0.58] | - | 0.500 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X34 | +15 | ASIA | X34o | 0.495 [-,-] | 0.512 [0.45,0.58] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| X35 | +30 | LONDON | X35o | 0.551 [-,-] | 0.512 [0.45,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | pre | ASIA | X31o | 0.504 [-,-] | 0.511 [0.46,0.56] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X31 | +5 | LONDON | X31b | 0.513 [-,-] | 0.510 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +30 | ASIA | X31o | 0.510 [-,-] | 0.510 [0.44,0.57] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X35 | +5 | ASIA | X35o | 0.504 [-,-] | 0.510 [0.45,0.57] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X33 | +30 | LONDON | X33b | 0.495 [-,-] | 0.510 [0.45,0.57] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +5 | ASIA | X34o | 0.489 [-,-] | 0.510 [0.45,0.56] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X35 | +30 | NY | X35b | 0.491 [-,-] | 0.510 [0.45,0.58] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +30 | ASIA | X34o | 0.498 [-,-] | 0.509 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X31 | +5 | POOLED | X31b | 0.508 [-,-] | 0.509 [0.48,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X35 | +30 | LONDON | X35b | 0.506 [-,-] | 0.509 [0.44,0.58] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +5 | LONDON | X31o | 0.525 [-,-] | 0.508 [0.45,0.57] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +5 | ASIA | X33o | 0.477 [-,-] | 0.508 [0.45,0.56] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X33 | pre | POOLED | X33o | 0.500 [-,-] | 0.508 [0.48,0.54] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X33 | +5 | POOLED | X33b | 0.510 [-,-] | 0.508 [0.47,0.54] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X31 | +15 | ASIA | X31o | 0.507 [-,-] | 0.507 [0.44,0.56] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X31 | +30 | NY | X31b | 0.488 [-,-] | 0.505 [0.44,0.57] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | pre | ASIA | X34b | 0.512 [-,-] | 0.505 [0.44,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X35 | +30 | POOLED | X35b | 0.512 [-,-] | 0.505 [0.47,0.54] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| X33 | +5 | POOLED | X33o | 0.494 [-,-] | 0.505 [0.47,0.54] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.175 AUC, 5 of 5 econ |
| X31 | +15 | NY | X31b | 0.504 [-,-] | 0.505 [0.44,0.56] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +30 | LONDON | X34b | 0.493 [-,-] | 0.504 [0.45,0.56] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +15 | NY | X32b | 0.492 [-,-] | 0.504 [0.45,0.57] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +30 | POOLED | X31o | 0.514 [-,-] | 0.504 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| X32 | +5 | ASIA | X32b | 0.532 [-,-] | 0.504 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X35 | +30 | POOLED | X35o | 0.521 [-,-] | 0.504 [0.47,0.55] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| X32 | pre | LONDON | X32o | 0.516 [-,-] | 0.504 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | pre | POOLED | X31o | 0.501 [-,-] | 0.503 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X34 | pre | ASIA | X34o | 0.500 [-,-] | 0.503 [0.44,0.56] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X34 | pre | NY | X34o | 0.474 [-,-] | 0.502 [0.44,0.57] | - | 0.505 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +5 | POOLED | X34b | 0.511 [-,-] | 0.502 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| X32 | pre | POOLED | X32o | 0.511 [-,-] | 0.502 [0.47,0.53] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X35 | +15 | POOLED | X35o | 0.515 [-,-] | 0.500 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X32 | +15 | LONDON | X32o | 0.520 [-,-] | 0.500 [0.44,0.57] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +30 | POOLED | X32o | 0.520 [-,-] | 0.500 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X32 | +15 | POOLED | X32o | 0.516 [-,-] | 0.499 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| X35 | +5 | POOLED | X35b | 0.501 [-,-] | 0.499 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.181 AUC, 5 of 5 econ |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X35 | +30 | ASIA | X35b | 0.537 [-,-] | 0.497 [0.43,0.55] | - | 0.485 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X31 | +15 | POOLED | X31o | 0.508 [-,-] | 0.497 [0.45,0.53] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.183 AUC, 5 of 5 econ |
| X35 | +5 | POOLED | X35o | 0.500 [-,-] | 0.496 [0.47,0.53] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X34 | +15 | POOLED | X34o | 0.501 [-,-] | 0.496 [0.46,0.53] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X34 | pre | POOLED | X34o | 0.497 [-,-] | 0.496 [0.47,0.53] | - | 0.497 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X34 | +30 | NY | X34o | 0.493 [-,-] | 0.496 [0.43,0.56] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | pre | ASIA | X35o | 0.507 [-,-] | 0.495 [0.44,0.56] | - | 0.488 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X34 | +30 | POOLED | X34o | 0.506 [-,-] | 0.495 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.185 AUC, 5 of 5 econ |
| X34 | +15 | NY | X34b | 0.494 [-,-] | 0.493 [0.43,0.56] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +5 | LONDON | X32b | 0.512 [-,-] | 0.493 [0.43,0.55] | - | 0.493 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +5 | LONDON | X32o | 0.503 [-,-] | 0.492 [0.43,0.55] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +5 | POOLED | X32b | 0.507 [-,-] | 0.489 [0.45,0.53] | - | 0.489 | - | - | - | - | - | - | stack | short by 0.191 AUC, 5 of 5 econ |
| X32 | +5 | POOLED | X32o | 0.504 [-,-] | 0.489 [0.45,0.52] | - | 0.488 | - | - | - | - | - | - | stack | short by 0.191 AUC, 5 of 5 econ |
| X31 | pre | NY | X31o | 0.476 [-,-] | 0.489 [0.42,0.57] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | pre | LONDON | X34o | 0.518 [-,-] | 0.489 [0.42,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +30 | LONDON | X32b | 0.497 [-,-] | 0.488 [0.43,0.55] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +15 | NY | X33b | 0.509 [-,-] | 0.487 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | pre | POOLED | X35o | 0.504 [-,-] | 0.487 [0.46,0.52] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X34 | +5 | POOLED | X34o | 0.486 [-,-] | 0.486 [0.45,0.51] | - | 0.485 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X31 | +5 | POOLED | X31o | 0.495 [-,-] | 0.485 [0.44,0.52] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X32 | pre | NY | X32o | 0.495 [-,-] | 0.484 [0.43,0.55] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +5 | NY | X31b | 0.479 [-,-] | 0.484 [0.43,0.54] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +5 | NY | X33o | 0.488 [-,-] | 0.484 [0.42,0.55] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +5 | ASIA | X31o | 0.495 [-,-] | 0.483 [0.43,0.54] | - | 0.482 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X31 | +30 | NY | X31o | 0.490 [-,-] | 0.483 [0.42,0.54] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | pre | NY | X33o | 0.486 [-,-] | 0.481 [0.42,0.55] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X33 | +15 | NY | X33o | 0.492 [-,-] | 0.481 [0.42,0.55] | - | 0.487 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +30 | LONDON | X34o | 0.523 [-,-] | 0.481 [0.43,0.54] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +5 | NY | X34o | 0.473 [-,-] | 0.480 [0.42,0.55] | - | 0.493 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X33 | +5 | NY | X33b | 0.468 [-,-] | 0.478 [0.43,0.53] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +5 | NY | X32b | 0.473 [-,-] | 0.475 [0.43,0.53] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +5 | NY | X34b | 0.482 [-,-] | 0.473 [0.42,0.53] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +30 | NY | X35o | 0.488 [-,-] | 0.470 [0.41,0.54] | - | 0.468 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| X34 | +5 | LONDON | X34o | 0.491 [-,-] | 0.468 [0.40,0.53] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X32 | +5 | NY | X32o | 0.484 [-,-] | 0.465 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X31 | +5 | NY | X31o | 0.465 [-,-] | 0.464 [0.40,0.54] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +5 | NY | X35o | 0.477 [-,-] | 0.464 [0.41,0.54] | - | 0.471 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| X35 | +5 | NY | X35b | 0.460 [-,-] | 0.460 [0.40,0.51] | - | 0.464 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X31 | +15 | NY | X31o | 0.483 [-,-] | 0.459 [0.38,0.53] | - | 0.463 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X34 | +15 | NY | X34o | 0.476 [-,-] | 0.458 [0.40,0.52] | - | 0.463 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X32 | +15 | NY | X32o | 0.484 [-,-] | 0.457 [0.40,0.52] | - | 0.459 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X32 | +30 | NY | X32o | 0.475 [-,-] | 0.449 [0.38,0.51] | - | 0.448 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| X35 | pre | NY | X35o | 0.477 [-,-] | 0.436 [0.38,0.50] | - | 0.438 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X35 | +15 | NY | X35o | 0.485 [-,-] | 0.430 [0.37,0.51] | - | 0.429 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X31 0 POOLED: r8_u X31b; cond hold 0.520 strata 0.518; headline=True
- X31 0 ASIA: r8_u X31b; cond hold 0.518 strata 0.516; headline=True
- X31 0 LONDON: r8_u X31b; cond hold 0.522 strata 0.524; headline=True
- X31 0 NY: r8_u X31b; cond hold 0.521 strata 0.524; headline=True
- X31 5 POOLED: r8_u X31b; cond hold 0.509 strata 0.506; headline=True
- X31 5 ASIA: r8_u X31b; cond hold 0.536 strata 0.526; headline=True
- X31 5 LONDON: r8_u X31b; cond hold 0.510 strata 0.509; headline=True
- X31 5 NY: r8_u X31b; cond hold 0.484 strata 0.489; headline=True
- X31 15 POOLED: r8_u X31b; cond hold 0.532 strata 0.528; headline=True
- X31 15 ASIA: r8_u X31b; cond hold 0.553 strata 0.547; headline=True
- X31 15 LONDON: r8_u X31b; cond hold 0.536 strata 0.527; headline=True
- X31 15 NY: r8_u X31b; cond hold 0.505 strata 0.504; headline=True
- X31 30 POOLED: r8_u X31b; cond hold 0.523 strata 0.519; headline=False
- X31 30 ASIA: r8_u X31b; cond hold 0.543 strata 0.537; headline=False
- X31 30 LONDON: r8_u X31b; cond hold 0.514 strata 0.509; headline=False
- X31 30 NY: r8_u X31b; cond hold 0.505 strata 0.508; headline=False
- X31 0 POOLED: r8_u X31o; cond hold 0.503 strata 0.502; headline=False
- X31 0 ASIA: r8_u X31o; cond hold 0.511 strata 0.512; headline=False
- X31 0 LONDON: r8_u X31o; cond hold 0.516 strata 0.512; headline=False
- X31 0 NY: r8_u X31o; cond hold 0.489 strata 0.497; headline=False
- X31 5 POOLED: r8_u X31o; cond hold 0.485 strata 0.484; headline=False
- X31 5 ASIA: r8_u X31o; cond hold 0.483 strata 0.482; headline=False
- X31 5 LONDON: r8_u X31o; cond hold 0.508 strata 0.510; headline=False
- X31 5 NY: r8_u X31o; cond hold 0.464 strata 0.476; headline=False
- X31 15 POOLED: r8_u X31o; cond hold 0.497 strata 0.494; headline=False
- X31 15 ASIA: r8_u X31o; cond hold 0.507 strata 0.508; headline=False
- X31 15 LONDON: r8_u X31o; cond hold 0.530 strata 0.530; headline=False
- X31 15 NY: r8_u X31o; cond hold 0.459 strata 0.463; headline=False
- X31 30 POOLED: r8_u X31o; cond hold 0.504 strata 0.504; headline=True
- X31 30 ASIA: r8_u X31o; cond hold 0.510 strata 0.512; headline=True
- X31 30 LONDON: r8_u X31o; cond hold 0.522 strata 0.524; headline=True
- X31 30 NY: r8_u X31o; cond hold 0.483 strata 0.485; headline=True
- X32 0 POOLED: r8_u X32b; cond hold 0.523 strata 0.521; headline=True
- X32 0 ASIA: r8_u X32b; cond hold 0.512 strata 0.500; headline=True
- X32 0 LONDON: r8_u X32b; cond hold 0.527 strata 0.523; headline=True
- X32 0 NY: r8_u X32b; cond hold 0.527 strata 0.529; headline=True
- X32 5 POOLED: r8_u X32b; cond hold 0.489 strata 0.489; headline=True
- X32 5 ASIA: r8_u X32b; cond hold 0.504 strata 0.495; headline=True
- X32 5 LONDON: r8_u X32b; cond hold 0.493 strata 0.493; headline=True
- X32 5 NY: r8_u X32b; cond hold 0.475 strata 0.479; headline=True
- X32 15 POOLED: r8_u X32b; cond hold 0.518 strata 0.515; headline=False
- X32 15 ASIA: r8_u X32b; cond hold 0.537 strata 0.528; headline=False
- X32 15 LONDON: r8_u X32b; cond hold 0.514 strata 0.507; headline=False
- X32 15 NY: r8_u X32b; cond hold 0.504 strata 0.499; headline=False
- X32 30 POOLED: r8_u X32b; cond hold 0.520 strata 0.516; headline=False
- X32 30 ASIA: r8_u X32b; cond hold 0.545 strata 0.536; headline=False
- X32 30 LONDON: r8_u X32b; cond hold 0.488 strata 0.483; headline=False
- X32 30 NY: r8_u X32b; cond hold 0.516 strata 0.520; headline=False
- X32 0 POOLED: r8_u X32o; cond hold 0.502 strata 0.501; headline=False
- X32 0 ASIA: r8_u X32o; cond hold 0.532 strata 0.536; headline=False
- X32 0 LONDON: r8_u X32o; cond hold 0.504 strata 0.502; headline=False
- X32 0 NY: r8_u X32o; cond hold 0.484 strata 0.486; headline=False
- X32 5 POOLED: r8_u X32o; cond hold 0.489 strata 0.488; headline=False
- X32 5 ASIA: r8_u X32o; cond hold 0.517 strata 0.515; headline=False
- X32 5 LONDON: r8_u X32o; cond hold 0.492 strata 0.495; headline=False
- X32 5 NY: r8_u X32o; cond hold 0.465 strata 0.474; headline=False
- X32 15 POOLED: r8_u X32o; cond hold 0.499 strata 0.498; headline=True
- X32 15 ASIA: r8_u X32o; cond hold 0.548 strata 0.550; headline=True
- X32 15 LONDON: r8_u X32o; cond hold 0.500 strata 0.501; headline=True
- X32 15 NY: r8_u X32o; cond hold 0.457 strata 0.459; headline=True
- X32 30 POOLED: r8_u X32o; cond hold 0.500 strata 0.498; headline=True
- X32 30 ASIA: r8_u X32o; cond hold 0.534 strata 0.534; headline=True
- X32 30 LONDON: r8_u X32o; cond hold 0.522 strata 0.521; headline=True
- X32 30 NY: r8_u X32o; cond hold 0.449 strata 0.448; headline=True
- X33 0 POOLED: r8_u X33b; cond hold 0.528 strata 0.528; headline=True
- X33 0 ASIA: r8_u X33b; cond hold 0.516 strata 0.509; headline=True
- X33 0 LONDON: r8_u X33b; cond hold 0.526 strata 0.528; headline=True
- X33 0 NY: r8_u X33b; cond hold 0.539 strata 0.549; headline=True
- X33 5 POOLED: r8_u X33b; cond hold 0.508 strata 0.509; headline=True
- X33 5 ASIA: r8_u X33b; cond hold 0.520 strata 0.513; headline=True
- X33 5 LONDON: r8_u X33b; cond hold 0.536 strata 0.536; headline=True
- X33 5 NY: r8_u X33b; cond hold 0.478 strata 0.482; headline=True
- X33 15 POOLED: r8_u X33b; cond hold 0.520 strata 0.517; headline=True
- X33 15 ASIA: r8_u X33b; cond hold 0.525 strata 0.514; headline=True
- X33 15 LONDON: r8_u X33b; cond hold 0.549 strata 0.547; headline=True
- X33 15 NY: r8_u X33b; cond hold 0.487 strata 0.484; headline=True
- X33 30 POOLED: r8_u X33b; cond hold 0.514 strata 0.510; headline=False
- X33 30 ASIA: r8_u X33b; cond hold 0.513 strata 0.504; headline=False
- X33 30 LONDON: r8_u X33b; cond hold 0.510 strata 0.509; headline=False
- X33 30 NY: r8_u X33b; cond hold 0.516 strata 0.522; headline=False
- X33 0 POOLED: r8_u X33o; cond hold 0.508 strata 0.510; headline=False
- X33 0 ASIA: r8_u X33o; cond hold 0.513 strata 0.518; headline=False
- X33 0 LONDON: r8_u X33o; cond hold 0.537 strata 0.538; headline=False
- X33 0 NY: r8_u X33o; cond hold 0.481 strata 0.486; headline=False
- X33 5 POOLED: r8_u X33o; cond hold 0.505 strata 0.503; headline=False
- X33 5 ASIA: r8_u X33o; cond hold 0.508 strata 0.503; headline=False
- X33 5 LONDON: r8_u X33o; cond hold 0.518 strata 0.522; headline=False
- X33 5 NY: r8_u X33o; cond hold 0.484 strata 0.485; headline=False
- X33 15 POOLED: r8_u X33o; cond hold 0.514 strata 0.514; headline=False
- X33 15 ASIA: r8_u X33o; cond hold 0.520 strata 0.519; headline=False
- X33 15 LONDON: r8_u X33o; cond hold 0.529 strata 0.536; headline=False
- X33 15 NY: r8_u X33o; cond hold 0.481 strata 0.487; headline=False
- X33 30 POOLED: r8_u X33o; cond hold 0.527 strata 0.528; headline=True
- X33 30 ASIA: r8_u X33o; cond hold 0.524 strata 0.526; headline=True
- X33 30 LONDON: r8_u X33o; cond hold 0.524 strata 0.524; headline=True
- X33 30 NY: r8_u X33o; cond hold 0.532 strata 0.532; headline=True
- X34 0 POOLED: r8_u X34b; cond hold 0.516 strata 0.517; headline=True
- X34 0 ASIA: r8_u X34b; cond hold 0.505 strata 0.501; headline=True
- X34 0 LONDON: r8_u X34b; cond hold 0.513 strata 0.510; headline=True
- X34 0 NY: r8_u X34b; cond hold 0.528 strata 0.532; headline=True
- X34 5 POOLED: r8_u X34b; cond hold 0.502 strata 0.502; headline=True
- X34 5 ASIA: r8_u X34b; cond hold 0.521 strata 0.513; headline=True
- X34 5 LONDON: r8_u X34b; cond hold 0.516 strata 0.517; headline=True
- X34 5 NY: r8_u X34b; cond hold 0.473 strata 0.479; headline=True
- X34 15 POOLED: r8_u X34b; cond hold 0.526 strata 0.522; headline=True
- X34 15 ASIA: r8_u X34b; cond hold 0.544 strata 0.532; headline=True
- X34 15 LONDON: r8_u X34b; cond hold 0.543 strata 0.536; headline=True
- X34 15 NY: r8_u X34b; cond hold 0.493 strata 0.495; headline=True
- X34 30 POOLED: r8_u X34b; cond hold 0.525 strata 0.520; headline=False
- X34 30 ASIA: r8_u X34b; cond hold 0.538 strata 0.529; headline=False
- X34 30 LONDON: r8_u X34b; cond hold 0.504 strata 0.495; headline=False
- X34 30 NY: r8_u X34b; cond hold 0.528 strata 0.529; headline=False
- X34 0 POOLED: r8_u X34o; cond hold 0.496 strata 0.497; headline=False
- X34 0 ASIA: r8_u X34o; cond hold 0.503 strata 0.507; headline=False
- X34 0 LONDON: r8_u X34o; cond hold 0.489 strata 0.490; headline=False
- X34 0 NY: r8_u X34o; cond hold 0.502 strata 0.505; headline=False
- X34 5 POOLED: r8_u X34o; cond hold 0.486 strata 0.485; headline=False
- X34 5 ASIA: r8_u X34o; cond hold 0.510 strata 0.508; headline=False
- X34 5 LONDON: r8_u X34o; cond hold 0.468 strata 0.465; headline=False
- X34 5 NY: r8_u X34o; cond hold 0.480 strata 0.493; headline=False
- X34 15 POOLED: r8_u X34o; cond hold 0.496 strata 0.494; headline=False
- X34 15 ASIA: r8_u X34o; cond hold 0.512 strata 0.515; headline=False
- X34 15 LONDON: r8_u X34o; cond hold 0.518 strata 0.521; headline=False
- X34 15 NY: r8_u X34o; cond hold 0.458 strata 0.463; headline=False
- X34 30 POOLED: r8_u X34o; cond hold 0.495 strata 0.493; headline=True
- X34 30 ASIA: r8_u X34o; cond hold 0.509 strata 0.510; headline=True
- X34 30 LONDON: r8_u X34o; cond hold 0.481 strata 0.484; headline=True
- X34 30 NY: r8_u X34o; cond hold 0.496 strata 0.492; headline=True
- X35 0 POOLED: r8_u X35b; cond hold 0.529 strata 0.527; headline=True
- X35 0 ASIA: r8_u X35b; cond hold 0.528 strata 0.523; headline=True
- X35 0 LONDON: r8_u X35b; cond hold 0.539 strata 0.534; headline=True
- X35 0 NY: r8_u X35b; cond hold 0.521 strata 0.526; headline=True
- X35 5 POOLED: r8_u X35b; cond hold 0.499 strata 0.498; headline=False
- X35 5 ASIA: r8_u X35b; cond hold 0.525 strata 0.515; headline=False
- X35 5 LONDON: r8_u X35b; cond hold 0.520 strata 0.523; headline=False
- X35 5 NY: r8_u X35b; cond hold 0.460 strata 0.464; headline=False
- X35 15 POOLED: r8_u X35b; cond hold 0.521 strata 0.515; headline=True
- X35 15 ASIA: r8_u X35b; cond hold 0.527 strata 0.515; headline=True
- X35 15 LONDON: r8_u X35b; cond hold 0.518 strata 0.514; headline=True
- X35 15 NY: r8_u X35b; cond hold 0.516 strata 0.509; headline=True
- X35 30 POOLED: r8_u X35b; cond hold 0.505 strata 0.500; headline=False
- X35 30 ASIA: r8_u X35b; cond hold 0.497 strata 0.485; headline=False
- X35 30 LONDON: r8_u X35b; cond hold 0.509 strata 0.501; headline=False
- X35 30 NY: r8_u X35b; cond hold 0.510 strata 0.508; headline=False
- X35 0 POOLED: r8_u X35o; cond hold 0.487 strata 0.484; headline=False
- X35 0 ASIA: r8_u X35o; cond hold 0.495 strata 0.488; headline=False
- X35 0 LONDON: r8_u X35o; cond hold 0.533 strata 0.528; headline=False
- X35 0 NY: r8_u X35o; cond hold 0.436 strata 0.438; headline=False
- X35 5 POOLED: r8_u X35o; cond hold 0.496 strata 0.495; headline=True
- X35 5 ASIA: r8_u X35o; cond hold 0.510 strata 0.509; headline=True
- X35 5 LONDON: r8_u X35o; cond hold 0.519 strata 0.514; headline=True
- X35 5 NY: r8_u X35o; cond hold 0.464 strata 0.471; headline=True
- X35 15 POOLED: r8_u X35o; cond hold 0.500 strata 0.501; headline=False
- X35 15 ASIA: r8_u X35o; cond hold 0.536 strata 0.542; headline=False
- X35 15 LONDON: r8_u X35o; cond hold 0.537 strata 0.540; headline=False
- X35 15 NY: r8_u X35o; cond hold 0.430 strata 0.429; headline=False
- X35 30 POOLED: r8_u X35o; cond hold 0.504 strata 0.502; headline=True
- X35 30 ASIA: r8_u X35o; cond hold 0.529 strata 0.531; headline=True
- X35 30 LONDON: r8_u X35o; cond hold 0.512 strata 0.516; headline=True
- X35 30 NY: r8_u X35o; cond hold 0.470 strata 0.468; headline=True
- X16-cond-lgbm 0 POOLED: r8_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r8_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r8_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r8_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r8_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r8_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r8_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r8_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r8_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r8_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r8_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r8_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r8_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r8_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r8_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r8_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r8_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r8_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r8_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r8_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r8_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r8_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r8_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r8_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r8_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r8_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r8_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r8_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r8_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r8_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r8_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r8_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
