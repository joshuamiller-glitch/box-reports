# PRED ROUND 51 - block X3 round 6 - X3 round 6

Best HOLDOUT F-R AUC: +15 POOLED 0.535 [0.49,0.58] | ASIA 0.540 [0.48,0.60] | LONDON 0.578 [0.50,0.65] | NY 0.527 [0.47,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.558 [0.52,0.59] | ASIA 0.552 [0.49,0.61] | LONDON 0.557 [0.49,0.62] | NY 0.577 [0.52,0.64]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.108 AUC, 5 of 5 economic conditions short.
not found - short by 0.108 AUC and 5 of 5 economic conditions

prereg 175901cc2d5f66b00bf2ef187b790d6a687ef0f2a7aa8e31dda74645e6a79bf9 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X25-strata-weighted | +15 | LONDON | X25 | 0.526 [-,-] | 0.578 [0.50,0.65] | - | 0.569 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +30 | NY | X25 | 0.516 [-,-] | 0.577 [0.52,0.64] | - | 0.578 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +15 | LONDON | XALL | 0.533 [-,-] | 0.568 [0.50,0.63] | - | 0.567 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +15 | LONDON | X21b | 0.519 [-,-] | 0.566 [0.49,0.63] | - | 0.561 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | pre | LONDON | X25 | 0.543 [-,-] | 0.563 [0.49,0.63] | - | 0.565 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +15 | LONDON | X21o | 0.552 [-,-] | 0.560 [0.49,0.62] | - | 0.563 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +30 | POOLED | X25 | 0.528 [-,-] | 0.558 [0.52,0.59] | - | 0.554 | - | - | - | - | - | - | stack | promising: short by 0.122 AUC, 5 of 5 econ |
| X21-hmm-path | +30 | LONDON | X21o | 0.572 [-,-] | 0.557 [0.49,0.62] | - | 0.565 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +15 | LONDON | X22b | 0.524 [-,-] | 0.556 [0.48,0.62] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +30 | ASIA | X24b | 0.544 [-,-] | 0.552 [0.49,0.61] | - | 0.544 | - | - | - | - | - | - | stack | short by 0.108 AUC, 5 of 5 econ |
| X20-cond-top40 | pre | NY | Q5 | 0.529 [-,-] | 0.551 [0.49,0.62] | - | 0.558 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | pre | NY | X23b | 0.530 [-,-] | 0.550 [0.50,0.60] | - | 0.558 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | LONDON | X24o | 0.534 [-,-] | 0.548 [0.49,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | pre | LONDON | X21b | 0.530 [-,-] | 0.548 [0.49,0.61] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | pre | LONDON | X21o | 0.540 [-,-] | 0.547 [0.49,0.61] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | pre | LONDON | XALL | 0.526 [-,-] | 0.546 [0.48,0.61] | - | 0.551 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | pre | NY | X21b | 0.508 [-,-] | 0.545 [0.49,0.60] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +30 | LONDON | X25 | 0.521 [-,-] | 0.545 [0.48,0.63] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +15 | LONDON | X22o | 0.546 [-,-] | 0.545 [0.47,0.62] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +30 | NY | X23b | 0.501 [-,-] | 0.545 [0.49,0.61] | - | 0.553 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | pre | NY | Q2 | 0.533 [-,-] | 0.544 [0.49,0.60] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | pre | LONDON | X22b | 0.532 [-,-] | 0.544 [0.47,0.61] | - | 0.543 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +5 | ASIA | Q3 | 0.498 [-,-] | 0.543 [0.48,0.60] | - | 0.546 | - | - | - | - | - | - | stack | short by 0.117 AUC, 5 of 5 econ |
| X23-handoff-open | +15 | LONDON | X23b | 0.517 [-,-] | 0.543 [0.47,0.61] | - | 0.537 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +30 | NY | XALL | 0.494 [-,-] | 0.542 [0.48,0.60] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +30 | ASIA | X25 | 0.544 [-,-] | 0.541 [0.49,0.59] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.119 AUC, 5 of 5 econ |
| XALL-unweighted | +30 | POOLED | XALL | 0.517 [-,-] | 0.541 [0.51,0.57] | - | 0.537 | - | - | - | - | - | - | stack | promising: short by 0.139 AUC, 5 of 5 econ |
| X23-handoff-open | +5 | LONDON | X23b | 0.527 [-,-] | 0.540 [0.47,0.60] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| R0-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X18-cond-loss | pre | LONDON | Q3 | 0.530 [-,-] | 0.540 [0.48,0.60] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | +15 | ASIA | Q2 | 0.534 [-,-] | 0.540 [0.48,0.60] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X22-drawdown-state | +30 | NY | X22b | 0.487 [-,-] | 0.540 [0.48,0.60] | - | 0.544 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +30 | ASIA | XALL | 0.545 [-,-] | 0.540 [0.48,0.59] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X25-strata-weighted | pre | NY | X25 | 0.502 [-,-] | 0.539 [0.47,0.60] | - | 0.546 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | pre | POOLED | X25 | 0.526 [-,-] | 0.539 [0.51,0.57] | - | 0.540 | - | - | - | - | - | - | stack | promising: short by 0.141 AUC, 5 of 5 econ |
| X21-hmm-path | pre | POOLED | X21b | 0.519 [-,-] | 0.539 [0.51,0.57] | - | 0.538 | - | - | - | - | - | - | stack | promising: short by 0.141 AUC, 5 of 5 econ |
| X22-drawdown-state | +15 | ASIA | X22b | 0.541 [-,-] | 0.538 [0.48,0.60] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X21-hmm-path | +5 | ASIA | X21b | 0.526 [-,-] | 0.538 [0.49,0.60] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X21-hmm-path | +15 | ASIA | X21b | 0.545 [-,-] | 0.538 [0.48,0.60] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.122 AUC, 5 of 5 econ |
| X17-cond-x11 | +30 | NY | Q2 | 0.504 [-,-] | 0.538 [0.48,0.61] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X20-cond-top40 | +30 | NY | Q5 | 0.492 [-,-] | 0.538 [0.48,0.60] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +30 | LONDON | X22o | 0.554 [-,-] | 0.538 [0.47,0.61] | - | 0.545 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +5 | LONDON | XALL | 0.519 [-,-] | 0.537 [0.47,0.61] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +30 | LONDON | XALL | 0.510 [-,-] | 0.536 [0.47,0.60] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | pre | ASIA | Q3 | 0.507 [-,-] | 0.536 [0.48,0.60] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X21-hmm-path | +30 | ASIA | X21b | 0.552 [-,-] | 0.535 [0.48,0.58] | - | 0.536 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X21-hmm-path | +15 | POOLED | X21b | 0.523 [-,-] | 0.535 [0.49,0.58] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X21-hmm-path | +5 | LONDON | X21o | 0.528 [-,-] | 0.535 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +30 | POOLED | X22b | 0.514 [-,-] | 0.535 [0.50,0.56] | - | 0.532 | - | - | - | - | - | - | stack | promising: short by 0.145 AUC, 5 of 5 econ |
| X19-cond-book | +30 | ASIA | Q4 | 0.524 [-,-] | 0.535 [0.48,0.59] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X20-cond-top40 | pre | POOLED | Q5 | 0.524 [-,-] | 0.535 [0.49,0.58] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X24-event-hazard | pre | LONDON | X24o | 0.519 [-,-] | 0.534 [0.48,0.59] | - | 0.539 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +30 | ASIA | X23o | 0.511 [-,-] | 0.534 [0.47,0.59] | - | 0.537 | - | - | - | - | - | - | stack | short by 0.126 AUC, 5 of 5 econ |
| X21-hmm-path | +30 | POOLED | X21o | 0.521 [-,-] | 0.533 [0.49,0.57] | - | 0.534 | - | - | - | - | - | - | stack | promising: short by 0.147 AUC, 5 of 5 econ |
| X23-handoff-open | +15 | ASIA | X23b | 0.549 [-,-] | 0.532 [0.47,0.60] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| X25-strata-weighted | +15 | POOLED | X25 | 0.523 [-,-] | 0.532 [0.49,0.57] | - | 0.529 | - | - | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| X22-drawdown-state | +30 | ASIA | X22b | 0.540 [-,-] | 0.532 [0.47,0.58] | - | 0.526 | - | - | - | - | - | - | stack | short by 0.128 AUC, 5 of 5 econ |
| X17-cond-x11 | +30 | LONDON | Q2 | 0.511 [-,-] | 0.532 [0.47,0.59] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +15 | POOLED | X22b | 0.526 [-,-] | 0.531 [0.49,0.58] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| X18-cond-loss | +15 | ASIA | Q3 | 0.512 [-,-] | 0.531 [0.47,0.59] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X24-event-hazard | pre | NY | X24b | 0.517 [-,-] | 0.531 [0.47,0.59] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| R0-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X17-cond-x11 | pre | LONDON | Q2 | 0.520 [-,-] | 0.531 [0.46,0.60] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | pre | POOLED | Q3 | 0.517 [-,-] | 0.531 [0.49,0.57] | - | 0.538 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| X17-cond-x11 | +30 | POOLED | Q2 | 0.517 [-,-] | 0.531 [0.50,0.56] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.149 AUC, 5 of 5 econ |
| X23-handoff-open | pre | POOLED | X23b | 0.524 [-,-] | 0.530 [0.50,0.56] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X22-drawdown-state | +30 | NY | X22o | 0.512 [-,-] | 0.530 [0.46,0.60] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | pre | LONDON | X23o | 0.525 [-,-] | 0.529 [0.46,0.59] | - | 0.531 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | +15 | LONDON | Q2 | 0.506 [-,-] | 0.529 [0.46,0.60] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +30 | POOLED | X21b | 0.515 [-,-] | 0.529 [0.50,0.56] | - | 0.527 | - | - | - | - | - | - | stack | promising: short by 0.151 AUC, 5 of 5 econ |
| X24-event-hazard | +5 | LONDON | X24o | 0.515 [-,-] | 0.529 [0.47,0.60] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +15 | ASIA | X25 | 0.535 [-,-] | 0.529 [0.46,0.59] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.131 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X20-cond-top40 | +15 | ASIA | Q5 | 0.527 [-,-] | 0.528 [0.46,0.61] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| X17-cond-x11 | pre | POOLED | Q2 | 0.525 [-,-] | 0.528 [0.49,0.56] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X21-hmm-path | +30 | NY | X21b | 0.495 [-,-] | 0.528 [0.46,0.60] | - | 0.536 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +30 | ASIA | X21o | 0.508 [-,-] | 0.528 [0.47,0.59] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| X20-cond-top40 | pre | ASIA | Q5 | 0.525 [-,-] | 0.527 [0.46,0.59] | - | 0.517 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X21-hmm-path | pre | ASIA | X21o | 0.507 [-,-] | 0.527 [0.47,0.58] | - | 0.534 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +30 | NY | X24o | 0.510 [-,-] | 0.527 [0.45,0.60] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +30 | POOLED | X23o | 0.517 [-,-] | 0.527 [0.49,0.56] | - | 0.528 | - | - | - | - | - | - | stack | promising: short by 0.153 AUC, 5 of 5 econ |
| X18-cond-loss | +15 | NY | Q3 | 0.516 [-,-] | 0.527 [0.47,0.59] | - | 0.512 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | +30 | NY | Q4 | 0.502 [-,-] | 0.526 [0.47,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X22-drawdown-state | +30 | LONDON | X22b | 0.510 [-,-] | 0.526 [0.47,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X19-cond-book | +30 | POOLED | Q4 | 0.509 [-,-] | 0.526 [0.49,0.56] | - | 0.525 | - | - | - | - | - | - | stack | promising: short by 0.154 AUC, 5 of 5 econ |
| X18-cond-loss | +15 | POOLED | Q3 | 0.502 [-,-] | 0.525 [0.48,0.57] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X23-handoff-open | +30 | NY | X23o | 0.509 [-,-] | 0.525 [0.47,0.58] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | +5 | ASIA | Q2 | 0.532 [-,-] | 0.525 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X17-cond-x11 | +5 | LONDON | Q2 | 0.525 [-,-] | 0.525 [0.46,0.59] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | pre | POOLED | X22b | 0.520 [-,-] | 0.525 [0.49,0.56] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X24-event-hazard | +15 | ASIA | X24b | 0.543 [-,-] | 0.524 [0.47,0.59] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X21-hmm-path | +15 | ASIA | X21o | 0.516 [-,-] | 0.524 [0.47,0.59] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X23-handoff-open | +5 | ASIA | X23b | 0.546 [-,-] | 0.524 [0.47,0.59] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| XALL-unweighted | pre | POOLED | XALL | 0.518 [-,-] | 0.524 [0.49,0.56] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X23-handoff-open | +15 | ASIA | X23o | 0.501 [-,-] | 0.524 [0.47,0.57] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | +15 | NY | Q4 | 0.521 [-,-] | 0.523 [0.45,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | pre | ASIA | X21b | 0.519 [-,-] | 0.523 [0.45,0.59] | - | 0.517 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X20-cond-top40 | pre | LONDON | Q5 | 0.517 [-,-] | 0.523 [0.46,0.58] | - | 0.522 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +30 | POOLED | X24b | 0.514 [-,-] | 0.523 [0.49,0.55] | - | 0.519 | - | - | - | - | - | - | stack | promising: short by 0.157 AUC, 5 of 5 econ |
| X21-hmm-path | +30 | NY | X21o | 0.486 [-,-] | 0.523 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +30 | LONDON | X21b | 0.495 [-,-] | 0.522 [0.47,0.58] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +30 | POOLED | X23b | 0.507 [-,-] | 0.522 [0.49,0.55] | - | 0.516 | - | - | - | - | - | - | stack | promising: short by 0.158 AUC, 5 of 5 econ |
| X23-handoff-open | +15 | LONDON | X23o | 0.533 [-,-] | 0.522 [0.46,0.60] | - | 0.530 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | pre | NY | Q4 | 0.507 [-,-] | 0.522 [0.47,0.58] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | +5 | ASIA | Q4 | 0.517 [-,-] | 0.522 [0.46,0.57] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X22-drawdown-state | pre | NY | X22b | 0.515 [-,-] | 0.522 [0.47,0.58] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | LONDON | X24b | 0.499 [-,-] | 0.521 [0.45,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | ASIA | X24o | 0.504 [-,-] | 0.521 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X19-cond-book | +5 | LONDON | Q4 | 0.520 [-,-] | 0.521 [0.45,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +5 | LONDON | X23o | 0.520 [-,-] | 0.520 [0.45,0.59] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +5 | LONDON | X21b | 0.518 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +15 | ASIA | XALL | 0.532 [-,-] | 0.520 [0.45,0.58] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X25-strata-weighted | +5 | ASIA | X25 | 0.522 [-,-] | 0.520 [0.46,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X22-drawdown-state | pre | LONDON | X22o | 0.524 [-,-] | 0.519 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X23-handoff-open | pre | LONDON | X23b | 0.525 [-,-] | 0.518 [0.45,0.58] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +30 | ASIA | X24o | 0.501 [-,-] | 0.518 [0.46,0.58] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X20-cond-top40 | +5 | ASIA | Q5 | 0.506 [-,-] | 0.518 [0.46,0.59] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | pre | NY | XALL | 0.494 [-,-] | 0.518 [0.45,0.57] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +15 | POOLED | X23b | 0.521 [-,-] | 0.518 [0.47,0.56] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.162 AUC, 5 of 5 econ |
| X22-drawdown-state | +5 | ASIA | X22b | 0.529 [-,-] | 0.518 [0.46,0.58] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.142 AUC, 5 of 5 econ |
| X19-cond-book | pre | POOLED | Q4 | 0.516 [-,-] | 0.517 [0.47,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X24-event-hazard | +15 | POOLED | X24b | 0.517 [-,-] | 0.517 [0.48,0.56] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.163 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +5 | ASIA | X24b | 0.522 [-,-] | 0.517 [0.46,0.57] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| X23-handoff-open | +30 | ASIA | X23b | 0.536 [-,-] | 0.517 [0.46,0.56] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| X18-cond-loss | +30 | NY | Q3 | 0.487 [-,-] | 0.517 [0.46,0.58] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | pre | ASIA | X23b | 0.516 [-,-] | 0.517 [0.44,0.59] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X19-cond-book | +15 | ASIA | Q4 | 0.538 [-,-] | 0.517 [0.45,0.57] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| X23-handoff-open | +30 | LONDON | X23o | 0.525 [-,-] | 0.516 [0.46,0.58] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | +5 | LONDON | X25 | 0.518 [-,-] | 0.516 [0.45,0.59] | - | 0.517 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | +15 | POOLED | Q2 | 0.511 [-,-] | 0.516 [0.48,0.56] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| XALL-unweighted | +15 | POOLED | XALL | 0.519 [-,-] | 0.516 [0.48,0.55] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X21-hmm-path | +5 | POOLED | X21b | 0.511 [-,-] | 0.515 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X24-event-hazard | pre | POOLED | X24b | 0.512 [-,-] | 0.515 [0.48,0.55] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X17-cond-x11 | +30 | ASIA | Q2 | 0.531 [-,-] | 0.514 [0.46,0.56] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.146 AUC, 5 of 5 econ |
| X22-drawdown-state | pre | ASIA | X22b | 0.517 [-,-] | 0.514 [0.45,0.58] | - | 0.506 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X17-cond-x11 | pre | ASIA | Q2 | 0.522 [-,-] | 0.513 [0.44,0.58] | - | 0.505 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X21-hmm-path | +15 | POOLED | X21o | 0.507 [-,-] | 0.513 [0.48,0.55] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X24-event-hazard | +30 | POOLED | X24o | 0.507 [-,-] | 0.513 [0.48,0.55] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X19-cond-book | pre | LONDON | Q4 | 0.512 [-,-] | 0.513 [0.44,0.59] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X25-strata-weighted | pre | ASIA | X25 | 0.533 [-,-] | 0.513 [0.45,0.58] | - | 0.512 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X20-cond-top40 | +15 | POOLED | Q5 | 0.511 [-,-] | 0.513 [0.47,0.56] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| XALL-unweighted | pre | ASIA | XALL | 0.538 [-,-] | 0.512 [0.46,0.58] | - | 0.507 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X21-hmm-path | pre | POOLED | X21o | 0.505 [-,-] | 0.512 [0.48,0.54] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X17-cond-x11 | +5 | POOLED | Q2 | 0.511 [-,-] | 0.511 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X22-drawdown-state | +30 | POOLED | X22o | 0.519 [-,-] | 0.511 [0.48,0.55] | - | 0.510 | - | - | - | - | - | - | stack | promising: short by 0.169 AUC, 5 of 5 econ |
| X20-cond-top40 | +15 | LONDON | Q5 | 0.515 [-,-] | 0.511 [0.44,0.57] | - | 0.508 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +5 | ASIA | X23o | 0.485 [-,-] | 0.510 [0.45,0.56] | - | 0.512 | - | - | - | - | - | - | stack | short by 0.150 AUC, 5 of 5 econ |
| X24-event-hazard | +5 | LONDON | X24b | 0.528 [-,-] | 0.510 [0.44,0.58] | - | 0.509 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X20-cond-top40 | +30 | POOLED | Q5 | 0.505 [-,-] | 0.510 [0.48,0.54] | - | 0.505 | - | - | - | - | - | - | stack | promising: short by 0.170 AUC, 5 of 5 econ |
| X19-cond-book | pre | ASIA | Q4 | 0.527 [-,-] | 0.510 [0.45,0.57] | - | 0.501 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X23-handoff-open | +5 | POOLED | X23b | 0.510 [-,-] | 0.509 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X18-cond-loss | +30 | POOLED | Q3 | 0.488 [-,-] | 0.509 [0.47,0.55] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X24-event-hazard | pre | LONDON | X24b | 0.506 [-,-] | 0.509 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | POOLED | X24o | 0.509 [-,-] | 0.509 [0.47,0.55] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X23-handoff-open | +15 | POOLED | X23o | 0.510 [-,-] | 0.509 [0.48,0.54] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X24-event-hazard | +30 | NY | X24b | 0.487 [-,-] | 0.509 [0.45,0.57] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | NY | X24b | 0.507 [-,-] | 0.509 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | +5 | POOLED | Q4 | 0.497 [-,-] | 0.508 [0.47,0.54] | - | 0.508 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X23-handoff-open | +5 | POOLED | X23o | 0.501 [-,-] | 0.508 [0.47,0.54] | - | 0.507 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X20-cond-top40 | +5 | LONDON | Q5 | 0.520 [-,-] | 0.508 [0.44,0.57] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +5 | ASIA | XALL | 0.518 [-,-] | 0.507 [0.45,0.57] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X22-drawdown-state | +5 | LONDON | X22b | 0.525 [-,-] | 0.507 [0.43,0.58] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | pre | ASIA | X24o | 0.507 [-,-] | 0.507 [0.45,0.57] | - | 0.506 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X19-cond-book | +30 | LONDON | Q4 | 0.499 [-,-] | 0.507 [0.45,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X20-cond-top40 | +30 | ASIA | Q5 | 0.541 [-,-] | 0.507 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X25-strata-weighted | +5 | POOLED | X25 | 0.511 [-,-] | 0.506 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X19-cond-book | +15 | POOLED | Q4 | 0.514 [-,-] | 0.506 [0.46,0.55] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X18-cond-loss | +30 | ASIA | Q3 | 0.486 [-,-] | 0.506 [0.45,0.55] | - | 0.510 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X22-drawdown-state | +5 | ASIA | X22o | 0.499 [-,-] | 0.506 [0.45,0.56] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X22-drawdown-state | pre | ASIA | X22o | 0.496 [-,-] | 0.504 [0.45,0.56] | - | 0.505 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X22-drawdown-state | +15 | ASIA | X22o | 0.510 [-,-] | 0.504 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X24-event-hazard | +30 | LONDON | X24b | 0.507 [-,-] | 0.504 [0.45,0.56] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +15 | NY | X21b | 0.503 [-,-] | 0.504 [0.44,0.57] | - | 0.503 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | pre | ASIA | X24b | 0.511 [-,-] | 0.503 [0.44,0.57] | - | 0.495 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X20-cond-top40 | +15 | NY | Q5 | 0.493 [-,-] | 0.503 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| R0-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X22-drawdown-state | +15 | NY | X22b | 0.512 [-,-] | 0.502 [0.44,0.57] | - | 0.504 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +5 | POOLED | XALL | 0.504 [-,-] | 0.502 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.178 AUC, 5 of 5 econ |
| X24-event-hazard | pre | POOLED | X24o | 0.497 [-,-] | 0.501 [0.47,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X24-event-hazard | +5 | POOLED | X24o | 0.496 [-,-] | 0.501 [0.47,0.54] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X21-hmm-path | +5 | POOLED | X21o | 0.496 [-,-] | 0.501 [0.46,0.54] | - | 0.501 | - | - | - | - | - | - | stack | short by 0.179 AUC, 5 of 5 econ |
| X23-handoff-open | pre | POOLED | X23o | 0.497 [-,-] | 0.500 [0.47,0.54] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X22-drawdown-state | +15 | POOLED | X22o | 0.513 [-,-] | 0.500 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X20-cond-top40 | +5 | POOLED | Q5 | 0.503 [-,-] | 0.500 [0.46,0.54] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X22-drawdown-state | +5 | LONDON | X22o | 0.524 [-,-] | 0.500 [0.43,0.57] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +15 | LONDON | Q3 | 0.475 [-,-] | 0.499 [0.43,0.56] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | pre | NY | Q3 | 0.519 [-,-] | 0.499 [0.43,0.56] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +5 | ASIA | X21o | 0.488 [-,-] | 0.498 [0.44,0.57] | - | 0.498 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X24-event-hazard | +30 | LONDON | X24o | 0.508 [-,-] | 0.498 [0.44,0.56] | - | 0.500 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X22-drawdown-state | +5 | POOLED | X22b | 0.508 [-,-] | 0.496 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X23-handoff-open | +30 | LONDON | X23b | 0.481 [-,-] | 0.496 [0.44,0.55] | - | 0.487 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | pre | ASIA | X23o | 0.483 [-,-] | 0.495 [0.43,0.56] | - | 0.497 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X25-strata-weighted | +15 | NY | X25 | 0.508 [-,-] | 0.495 [0.44,0.56] | - | 0.501 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +5 | POOLED | X24b | 0.507 [-,-] | 0.494 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - | stack | short by 0.186 AUC, 5 of 5 econ |
| X22-drawdown-state | pre | POOLED | X22o | 0.497 [-,-] | 0.493 [0.46,0.52] | - | 0.492 | - | - | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +5 | POOLED | Q3 | 0.475 [-,-] | 0.492 [0.45,0.53] | - | 0.498 | - | - | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| X21-hmm-path | +5 | NY | X21b | 0.487 [-,-] | 0.491 [0.44,0.55] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +5 | ASIA | X24o | 0.483 [-,-] | 0.491 [0.45,0.54] | - | 0.484 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X17-cond-x11 | +5 | NY | Q2 | 0.476 [-,-] | 0.488 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X20-cond-top40 | +5 | NY | Q5 | 0.481 [-,-] | 0.487 [0.42,0.55] | - | 0.490 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| X24-event-hazard | +5 | NY | X24o | 0.487 [-,-] | 0.486 [0.43,0.55] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +5 | NY | X23o | 0.495 [-,-] | 0.484 [0.42,0.55] | - | 0.484 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +5 | POOLED | X22o | 0.499 [-,-] | 0.483 [0.45,0.52] | - | 0.481 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X25-strata-weighted | +5 | NY | X25 | 0.493 [-,-] | 0.483 [0.44,0.54] | - | 0.488 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +15 | NY | X23b | 0.499 [-,-] | 0.481 [0.42,0.54] | - | 0.480 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X17-cond-x11 | +15 | NY | Q2 | 0.493 [-,-] | 0.479 [0.43,0.53] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| R0-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X19-cond-book | +5 | NY | Q4 | 0.456 [-,-] | 0.478 [0.42,0.53] | - | 0.483 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | pre | NY | X23o | 0.484 [-,-] | 0.478 [0.41,0.54] | - | 0.485 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X20-cond-top40 | +30 | LONDON | Q5 | 0.479 [-,-] | 0.477 [0.42,0.54] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X21-hmm-path | +5 | NY | X21o | 0.475 [-,-] | 0.477 [0.41,0.55] | - | 0.481 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X19-cond-book | +15 | LONDON | Q4 | 0.479 [-,-] | 0.475 [0.40,0.55] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +30 | ASIA | X22o | 0.492 [-,-] | 0.474 [0.42,0.54] | - | 0.472 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X24-event-hazard | pre | NY | X24o | 0.469 [-,-] | 0.474 [0.41,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +5 | LONDON | Q3 | 0.473 [-,-] | 0.473 [0.41,0.53] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | pre | NY | X22o | 0.476 [-,-] | 0.473 [0.41,0.54] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +15 | NY | X23o | 0.495 [-,-] | 0.472 [0.42,0.55] | - | 0.476 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +15 | NY | X24o | 0.493 [-,-] | 0.470 [0.42,0.53] | - | 0.479 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X23-handoff-open | +5 | NY | X23b | 0.457 [-,-] | 0.469 [0.42,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X21-hmm-path | pre | NY | X21o | 0.470 [-,-] | 0.467 [0.40,0.53] | - | 0.475 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +30 | LONDON | Q3 | 0.475 [-,-] | 0.467 [0.41,0.53] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +5 | NY | X22b | 0.466 [-,-] | 0.467 [0.41,0.52] | - | 0.478 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X18-cond-loss | +5 | NY | Q3 | 0.464 [-,-] | 0.466 [0.40,0.53] | - | 0.458 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +5 | NY | XALL | 0.474 [-,-] | 0.465 [0.42,0.52] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +15 | NY | X22o | 0.483 [-,-] | 0.465 [0.41,0.53] | - | 0.474 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| XALL-unweighted | +15 | NY | XALL | 0.495 [-,-] | 0.464 [0.41,0.52] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| X21-hmm-path | +15 | NY | X21o | 0.456 [-,-] | 0.459 [0.40,0.52] | - | 0.462 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X24-event-hazard | +5 | NY | X24b | 0.470 [-,-] | 0.459 [0.41,0.52] | - | 0.465 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X22-drawdown-state | +5 | NY | X22o | 0.472 [-,-] | 0.455 [0.39,0.52] | - | 0.470 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| R0-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |
| R0-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X16-cond-lgbm 0 POOLED: r3_u Q1; cond hold 0.526 strata 0.523; headline=True
- X16-cond-lgbm 0 ASIA: r3_u Q1; cond hold 0.529 strata 0.520; headline=True
- X16-cond-lgbm 0 LONDON: r3_u Q1; cond hold 0.523 strata 0.516; headline=True
- X16-cond-lgbm 0 NY: r3_u Q1; cond hold 0.527 strata 0.532; headline=True
- X16-cond-lgbm 5 POOLED: r3_u Q1; cond hold 0.512 strata 0.511; headline=True
- X16-cond-lgbm 5 ASIA: r3_u Q1; cond hold 0.535 strata 0.528; headline=True
- X16-cond-lgbm 5 LONDON: r3_u Q1; cond hold 0.517 strata 0.520; headline=True
- X16-cond-lgbm 5 NY: r3_u Q1; cond hold 0.493 strata 0.499; headline=True
- X16-cond-lgbm 15 POOLED: r3_u Q1; cond hold 0.526 strata 0.524; headline=True
- X16-cond-lgbm 15 ASIA: r3_u Q1; cond hold 0.513 strata 0.503; headline=True
- X16-cond-lgbm 15 LONDON: r3_u Q1; cond hold 0.546 strata 0.542; headline=True
- X16-cond-lgbm 15 NY: r3_u Q1; cond hold 0.520 strata 0.523; headline=True
- X16-cond-lgbm 30 POOLED: r3_u Q1; cond hold 0.519 strata 0.515; headline=True
- X16-cond-lgbm 30 ASIA: r3_u Q1; cond hold 0.506 strata 0.494; headline=True
- X16-cond-lgbm 30 LONDON: r3_u Q1; cond hold 0.518 strata 0.513; headline=True
- X16-cond-lgbm 30 NY: r3_u Q1; cond hold 0.529 strata 0.534; headline=True
- X17-cond-x11 0 POOLED: r3_u Q2; cond hold 0.528 strata 0.527; headline=True
- X17-cond-x11 0 ASIA: r3_u Q2; cond hold 0.513 strata 0.505; headline=True
- X17-cond-x11 0 LONDON: r3_u Q2; cond hold 0.531 strata 0.531; headline=True
- X17-cond-x11 0 NY: r3_u Q2; cond hold 0.544 strata 0.549; headline=True
- X17-cond-x11 5 POOLED: r3_u Q2; cond hold 0.511 strata 0.509; headline=True
- X17-cond-x11 5 ASIA: r3_u Q2; cond hold 0.525 strata 0.516; headline=True
- X17-cond-x11 5 LONDON: r3_u Q2; cond hold 0.525 strata 0.526; headline=True
- X17-cond-x11 5 NY: r3_u Q2; cond hold 0.488 strata 0.489; headline=True
- X17-cond-x11 15 POOLED: r3_u Q2; cond hold 0.516 strata 0.515; headline=True
- X17-cond-x11 15 ASIA: r3_u Q2; cond hold 0.540 strata 0.529; headline=True
- X17-cond-x11 15 LONDON: r3_u Q2; cond hold 0.529 strata 0.522; headline=True
- X17-cond-x11 15 NY: r3_u Q2; cond hold 0.479 strata 0.476; headline=True
- X17-cond-x11 30 POOLED: r3_u Q2; cond hold 0.531 strata 0.529; headline=True
- X17-cond-x11 30 ASIA: r3_u Q2; cond hold 0.514 strata 0.511; headline=True
- X17-cond-x11 30 LONDON: r3_u Q2; cond hold 0.532 strata 0.525; headline=True
- X17-cond-x11 30 NY: r3_u Q2; cond hold 0.538 strata 0.545; headline=True
- X18-cond-loss 0 POOLED: r3_u Q3; cond hold 0.531 strata 0.538; headline=True
- X18-cond-loss 0 ASIA: r3_u Q3; cond hold 0.536 strata 0.547; headline=True
- X18-cond-loss 0 LONDON: r3_u Q3; cond hold 0.540 strata 0.546; headline=True
- X18-cond-loss 0 NY: r3_u Q3; cond hold 0.499 strata 0.489; headline=True
- X18-cond-loss 5 POOLED: r3_u Q3; cond hold 0.492 strata 0.498; headline=True
- X18-cond-loss 5 ASIA: r3_u Q3; cond hold 0.543 strata 0.546; headline=True
- X18-cond-loss 5 LONDON: r3_u Q3; cond hold 0.473 strata 0.478; headline=True
- X18-cond-loss 5 NY: r3_u Q3; cond hold 0.466 strata 0.458; headline=True
- X18-cond-loss 15 POOLED: r3_u Q3; cond hold 0.525 strata 0.533; headline=True
- X18-cond-loss 15 ASIA: r3_u Q3; cond hold 0.531 strata 0.533; headline=True
- X18-cond-loss 15 LONDON: r3_u Q3; cond hold 0.499 strata 0.513; headline=True
- X18-cond-loss 15 NY: r3_u Q3; cond hold 0.527 strata 0.512; headline=True
- X18-cond-loss 30 POOLED: r3_u Q3; cond hold 0.509 strata 0.513; headline=True
- X18-cond-loss 30 ASIA: r3_u Q3; cond hold 0.506 strata 0.510; headline=True
- X18-cond-loss 30 LONDON: r3_u Q3; cond hold 0.467 strata 0.472; headline=True
- X18-cond-loss 30 NY: r3_u Q3; cond hold 0.517 strata 0.526; headline=True
- X19-cond-book 0 POOLED: r3_u Q4; cond hold 0.517 strata 0.518; headline=True
- X19-cond-book 0 ASIA: r3_u Q4; cond hold 0.510 strata 0.501; headline=True
- X19-cond-book 0 LONDON: r3_u Q4; cond hold 0.513 strata 0.509; headline=True
- X19-cond-book 0 NY: r3_u Q4; cond hold 0.522 strata 0.529; headline=True
- X19-cond-book 5 POOLED: r3_u Q4; cond hold 0.508 strata 0.508; headline=True
- X19-cond-book 5 ASIA: r3_u Q4; cond hold 0.522 strata 0.520; headline=True
- X19-cond-book 5 LONDON: r3_u Q4; cond hold 0.521 strata 0.516; headline=True
- X19-cond-book 5 NY: r3_u Q4; cond hold 0.478 strata 0.483; headline=True
- X19-cond-book 15 POOLED: r3_u Q4; cond hold 0.506 strata 0.506; headline=True
- X19-cond-book 15 ASIA: r3_u Q4; cond hold 0.517 strata 0.512; headline=True
- X19-cond-book 15 LONDON: r3_u Q4; cond hold 0.475 strata 0.472; headline=True
- X19-cond-book 15 NY: r3_u Q4; cond hold 0.523 strata 0.520; headline=True
- X19-cond-book 30 POOLED: r3_u Q4; cond hold 0.526 strata 0.525; headline=True
- X19-cond-book 30 ASIA: r3_u Q4; cond hold 0.535 strata 0.531; headline=True
- X19-cond-book 30 LONDON: r3_u Q4; cond hold 0.507 strata 0.504; headline=True
- X19-cond-book 30 NY: r3_u Q4; cond hold 0.526 strata 0.534; headline=True
- X20-cond-top40 0 POOLED: r3_u Q5; cond hold 0.535 strata 0.531; headline=True
- X20-cond-top40 0 ASIA: r3_u Q5; cond hold 0.527 strata 0.517; headline=True
- X20-cond-top40 0 LONDON: r3_u Q5; cond hold 0.523 strata 0.522; headline=True
- X20-cond-top40 0 NY: r3_u Q5; cond hold 0.551 strata 0.558; headline=True
- X20-cond-top40 5 POOLED: r3_u Q5; cond hold 0.500 strata 0.498; headline=True
- X20-cond-top40 5 ASIA: r3_u Q5; cond hold 0.518 strata 0.506; headline=True
- X20-cond-top40 5 LONDON: r3_u Q5; cond hold 0.508 strata 0.506; headline=True
- X20-cond-top40 5 NY: r3_u Q5; cond hold 0.487 strata 0.490; headline=True
- X20-cond-top40 15 POOLED: r3_u Q5; cond hold 0.513 strata 0.509; headline=True
- X20-cond-top40 15 ASIA: r3_u Q5; cond hold 0.528 strata 0.523; headline=True
- X20-cond-top40 15 LONDON: r3_u Q5; cond hold 0.511 strata 0.508; headline=True
- X20-cond-top40 15 NY: r3_u Q5; cond hold 0.503 strata 0.502; headline=True
- X20-cond-top40 30 POOLED: r3_u Q5; cond hold 0.510 strata 0.505; headline=True
- X20-cond-top40 30 ASIA: r3_u Q5; cond hold 0.507 strata 0.495; headline=True
- X20-cond-top40 30 LONDON: r3_u Q5; cond hold 0.477 strata 0.475; headline=True
- X20-cond-top40 30 NY: r3_u Q5; cond hold 0.538 strata 0.536; headline=True
- R0-ref 0 POOLED: r3_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r3_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r3_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r3_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r3_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r3_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r3_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r3_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r3_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r3_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r3_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r3_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r3_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r3_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r3_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r3_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
- X21-hmm-path 0 POOLED: r4_u X21b; cond hold 0.539 strata 0.538; headline=True
- X21-hmm-path 0 ASIA: r4_u X21b; cond hold 0.523 strata 0.517; headline=True
- X21-hmm-path 0 LONDON: r4_u X21b; cond hold 0.548 strata 0.546; headline=True
- X21-hmm-path 0 NY: r4_u X21b; cond hold 0.545 strata 0.549; headline=True
- X21-hmm-path 5 POOLED: r4_u X21b; cond hold 0.515 strata 0.514; headline=True
- X21-hmm-path 5 ASIA: r4_u X21b; cond hold 0.538 strata 0.524; headline=True
- X21-hmm-path 5 LONDON: r4_u X21b; cond hold 0.520 strata 0.523; headline=True
- X21-hmm-path 5 NY: r4_u X21b; cond hold 0.491 strata 0.495; headline=True
- X21-hmm-path 15 POOLED: r4_u X21b; cond hold 0.535 strata 0.533; headline=True
- X21-hmm-path 15 ASIA: r4_u X21b; cond hold 0.538 strata 0.527; headline=True
- X21-hmm-path 15 LONDON: r4_u X21b; cond hold 0.566 strata 0.561; headline=True
- X21-hmm-path 15 NY: r4_u X21b; cond hold 0.504 strata 0.503; headline=True
- X21-hmm-path 30 POOLED: r4_u X21b; cond hold 0.529 strata 0.527; headline=False
- X21-hmm-path 30 ASIA: r4_u X21b; cond hold 0.535 strata 0.536; headline=False
- X21-hmm-path 30 LONDON: r4_u X21b; cond hold 0.522 strata 0.510; headline=False
- X21-hmm-path 30 NY: r4_u X21b; cond hold 0.528 strata 0.536; headline=False
- X21-hmm-path 0 POOLED: r4_u X21o; cond hold 0.512 strata 0.514; headline=False
- X21-hmm-path 0 ASIA: r4_u X21o; cond hold 0.527 strata 0.534; headline=False
- X21-hmm-path 0 LONDON: r4_u X21o; cond hold 0.547 strata 0.551; headline=False
- X21-hmm-path 0 NY: r4_u X21o; cond hold 0.467 strata 0.475; headline=False
- X21-hmm-path 5 POOLED: r4_u X21o; cond hold 0.501 strata 0.501; headline=False
- X21-hmm-path 5 ASIA: r4_u X21o; cond hold 0.498 strata 0.498; headline=False
- X21-hmm-path 5 LONDON: r4_u X21o; cond hold 0.535 strata 0.534; headline=False
- X21-hmm-path 5 NY: r4_u X21o; cond hold 0.477 strata 0.481; headline=False
- X21-hmm-path 15 POOLED: r4_u X21o; cond hold 0.513 strata 0.514; headline=False
- X21-hmm-path 15 ASIA: r4_u X21o; cond hold 0.524 strata 0.524; headline=False
- X21-hmm-path 15 LONDON: r4_u X21o; cond hold 0.560 strata 0.563; headline=False
- X21-hmm-path 15 NY: r4_u X21o; cond hold 0.459 strata 0.462; headline=False
- X21-hmm-path 30 POOLED: r4_u X21o; cond hold 0.533 strata 0.534; headline=True
- X21-hmm-path 30 ASIA: r4_u X21o; cond hold 0.528 strata 0.524; headline=True
- X21-hmm-path 30 LONDON: r4_u X21o; cond hold 0.557 strata 0.565; headline=True
- X21-hmm-path 30 NY: r4_u X21o; cond hold 0.523 strata 0.524; headline=True
- X22-drawdown-state 0 POOLED: r4_u X22b; cond hold 0.525 strata 0.524; headline=True
- X22-drawdown-state 0 ASIA: r4_u X22b; cond hold 0.514 strata 0.506; headline=True
- X22-drawdown-state 0 LONDON: r4_u X22b; cond hold 0.544 strata 0.543; headline=True
- X22-drawdown-state 0 NY: r4_u X22b; cond hold 0.522 strata 0.529; headline=True
- X22-drawdown-state 5 POOLED: r4_u X22b; cond hold 0.496 strata 0.493; headline=True
- X22-drawdown-state 5 ASIA: r4_u X22b; cond hold 0.518 strata 0.506; headline=True
- X22-drawdown-state 5 LONDON: r4_u X22b; cond hold 0.507 strata 0.501; headline=True
- X22-drawdown-state 5 NY: r4_u X22b; cond hold 0.467 strata 0.478; headline=True
- X22-drawdown-state 15 POOLED: r4_u X22b; cond hold 0.531 strata 0.527; headline=True
- X22-drawdown-state 15 ASIA: r4_u X22b; cond hold 0.538 strata 0.528; headline=True
- X22-drawdown-state 15 LONDON: r4_u X22b; cond hold 0.556 strata 0.551; headline=True
- X22-drawdown-state 15 NY: r4_u X22b; cond hold 0.502 strata 0.504; headline=True
- X22-drawdown-state 30 POOLED: r4_u X22b; cond hold 0.535 strata 0.532; headline=False
- X22-drawdown-state 30 ASIA: r4_u X22b; cond hold 0.532 strata 0.526; headline=False
- X22-drawdown-state 30 LONDON: r4_u X22b; cond hold 0.526 strata 0.516; headline=False
- X22-drawdown-state 30 NY: r4_u X22b; cond hold 0.540 strata 0.544; headline=False
- X22-drawdown-state 0 POOLED: r4_u X22o; cond hold 0.493 strata 0.492; headline=False
- X22-drawdown-state 0 ASIA: r4_u X22o; cond hold 0.504 strata 0.505; headline=False
- X22-drawdown-state 0 LONDON: r4_u X22o; cond hold 0.519 strata 0.516; headline=False
- X22-drawdown-state 0 NY: r4_u X22o; cond hold 0.473 strata 0.482; headline=False
- X22-drawdown-state 5 POOLED: r4_u X22o; cond hold 0.483 strata 0.481; headline=False
- X22-drawdown-state 5 ASIA: r4_u X22o; cond hold 0.506 strata 0.499; headline=False
- X22-drawdown-state 5 LONDON: r4_u X22o; cond hold 0.500 strata 0.494; headline=False
- X22-drawdown-state 5 NY: r4_u X22o; cond hold 0.455 strata 0.470; headline=False
- X22-drawdown-state 15 POOLED: r4_u X22o; cond hold 0.500 strata 0.498; headline=False
- X22-drawdown-state 15 ASIA: r4_u X22o; cond hold 0.504 strata 0.502; headline=False
- X22-drawdown-state 15 LONDON: r4_u X22o; cond hold 0.545 strata 0.549; headline=False
- X22-drawdown-state 15 NY: r4_u X22o; cond hold 0.465 strata 0.474; headline=False
- X22-drawdown-state 30 POOLED: r4_u X22o; cond hold 0.511 strata 0.510; headline=True
- X22-drawdown-state 30 ASIA: r4_u X22o; cond hold 0.474 strata 0.472; headline=True
- X22-drawdown-state 30 LONDON: r4_u X22o; cond hold 0.538 strata 0.545; headline=True
- X22-drawdown-state 30 NY: r4_u X22o; cond hold 0.530 strata 0.532; headline=True
- X23-handoff-open 0 POOLED: r4_u X23b; cond hold 0.530 strata 0.531; headline=True
- X23-handoff-open 0 ASIA: r4_u X23b; cond hold 0.517 strata 0.512; headline=True
- X23-handoff-open 0 LONDON: r4_u X23b; cond hold 0.518 strata 0.519; headline=True
- X23-handoff-open 0 NY: r4_u X23b; cond hold 0.550 strata 0.558; headline=True
- X23-handoff-open 5 POOLED: r4_u X23b; cond hold 0.509 strata 0.511; headline=True
- X23-handoff-open 5 ASIA: r4_u X23b; cond hold 0.524 strata 0.515; headline=True
- X23-handoff-open 5 LONDON: r4_u X23b; cond hold 0.540 strata 0.544; headline=True
- X23-handoff-open 5 NY: r4_u X23b; cond hold 0.469 strata 0.474; headline=True
- X23-handoff-open 15 POOLED: r4_u X23b; cond hold 0.518 strata 0.515; headline=True
- X23-handoff-open 15 ASIA: r4_u X23b; cond hold 0.532 strata 0.524; headline=True
- X23-handoff-open 15 LONDON: r4_u X23b; cond hold 0.543 strata 0.537; headline=True
- X23-handoff-open 15 NY: r4_u X23b; cond hold 0.481 strata 0.480; headline=True
- X23-handoff-open 30 POOLED: r4_u X23b; cond hold 0.522 strata 0.516; headline=False
- X23-handoff-open 30 ASIA: r4_u X23b; cond hold 0.517 strata 0.502; headline=False
- X23-handoff-open 30 LONDON: r4_u X23b; cond hold 0.496 strata 0.487; headline=False
- X23-handoff-open 30 NY: r4_u X23b; cond hold 0.545 strata 0.553; headline=False
- X23-handoff-open 0 POOLED: r4_u X23o; cond hold 0.500 strata 0.503; headline=False
- X23-handoff-open 0 ASIA: r4_u X23o; cond hold 0.495 strata 0.497; headline=False
- X23-handoff-open 0 LONDON: r4_u X23o; cond hold 0.529 strata 0.531; headline=False
- X23-handoff-open 0 NY: r4_u X23o; cond hold 0.478 strata 0.485; headline=False
- X23-handoff-open 5 POOLED: r4_u X23o; cond hold 0.508 strata 0.507; headline=False
- X23-handoff-open 5 ASIA: r4_u X23o; cond hold 0.510 strata 0.512; headline=False
- X23-handoff-open 5 LONDON: r4_u X23o; cond hold 0.520 strata 0.520; headline=False
- X23-handoff-open 5 NY: r4_u X23o; cond hold 0.484 strata 0.484; headline=False
- X23-handoff-open 15 POOLED: r4_u X23o; cond hold 0.509 strata 0.509; headline=False
- X23-handoff-open 15 ASIA: r4_u X23o; cond hold 0.524 strata 0.523; headline=False
- X23-handoff-open 15 LONDON: r4_u X23o; cond hold 0.522 strata 0.530; headline=False
- X23-handoff-open 15 NY: r4_u X23o; cond hold 0.472 strata 0.476; headline=False
- X23-handoff-open 30 POOLED: r4_u X23o; cond hold 0.527 strata 0.528; headline=True
- X23-handoff-open 30 ASIA: r4_u X23o; cond hold 0.534 strata 0.537; headline=True
- X23-handoff-open 30 LONDON: r4_u X23o; cond hold 0.516 strata 0.516; headline=True
- X23-handoff-open 30 NY: r4_u X23o; cond hold 0.525 strata 0.525; headline=True
- X24-event-hazard 0 POOLED: r4_u X24b; cond hold 0.515 strata 0.513; headline=True
- X24-event-hazard 0 ASIA: r4_u X24b; cond hold 0.503 strata 0.495; headline=True
- X24-event-hazard 0 LONDON: r4_u X24b; cond hold 0.509 strata 0.506; headline=True
- X24-event-hazard 0 NY: r4_u X24b; cond hold 0.531 strata 0.535; headline=True
- X24-event-hazard 5 POOLED: r4_u X24b; cond hold 0.494 strata 0.493; headline=True
- X24-event-hazard 5 ASIA: r4_u X24b; cond hold 0.517 strata 0.513; headline=True
- X24-event-hazard 5 LONDON: r4_u X24b; cond hold 0.510 strata 0.509; headline=True
- X24-event-hazard 5 NY: r4_u X24b; cond hold 0.459 strata 0.465; headline=True
- X24-event-hazard 15 POOLED: r4_u X24b; cond hold 0.517 strata 0.514; headline=True
- X24-event-hazard 15 ASIA: r4_u X24b; cond hold 0.524 strata 0.511; headline=True
- X24-event-hazard 15 LONDON: r4_u X24b; cond hold 0.521 strata 0.520; headline=True
- X24-event-hazard 15 NY: r4_u X24b; cond hold 0.509 strata 0.504; headline=True
- X24-event-hazard 30 POOLED: r4_u X24b; cond hold 0.523 strata 0.519; headline=True
- X24-event-hazard 30 ASIA: r4_u X24b; cond hold 0.552 strata 0.544; headline=True
- X24-event-hazard 30 LONDON: r4_u X24b; cond hold 0.504 strata 0.495; headline=True
- X24-event-hazard 30 NY: r4_u X24b; cond hold 0.509 strata 0.513; headline=True
- X24-event-hazard 0 POOLED: r4_u X24o; cond hold 0.501 strata 0.501; headline=False
- X24-event-hazard 0 ASIA: r4_u X24o; cond hold 0.507 strata 0.506; headline=False
- X24-event-hazard 0 LONDON: r4_u X24o; cond hold 0.534 strata 0.539; headline=False
- X24-event-hazard 0 NY: r4_u X24o; cond hold 0.474 strata 0.482; headline=False
- X24-event-hazard 5 POOLED: r4_u X24o; cond hold 0.501 strata 0.499; headline=False
- X24-event-hazard 5 ASIA: r4_u X24o; cond hold 0.491 strata 0.484; headline=False
- X24-event-hazard 5 LONDON: r4_u X24o; cond hold 0.529 strata 0.528; headline=False
- X24-event-hazard 5 NY: r4_u X24o; cond hold 0.486 strata 0.494; headline=False
- X24-event-hazard 15 POOLED: r4_u X24o; cond hold 0.509 strata 0.509; headline=False
- X24-event-hazard 15 ASIA: r4_u X24o; cond hold 0.521 strata 0.523; headline=False
- X24-event-hazard 15 LONDON: r4_u X24o; cond hold 0.548 strata 0.552; headline=False
- X24-event-hazard 15 NY: r4_u X24o; cond hold 0.470 strata 0.479; headline=False
- X24-event-hazard 30 POOLED: r4_u X24o; cond hold 0.513 strata 0.512; headline=False
- X24-event-hazard 30 ASIA: r4_u X24o; cond hold 0.518 strata 0.521; headline=False
- X24-event-hazard 30 LONDON: r4_u X24o; cond hold 0.498 strata 0.500; headline=False
- X24-event-hazard 30 NY: r4_u X24o; cond hold 0.527 strata 0.526; headline=False
- XALL-unweighted 0 POOLED: r4_u XALL; cond hold 0.524 strata 0.524; headline=True
- XALL-unweighted 0 ASIA: r4_u XALL; cond hold 0.512 strata 0.507; headline=True
- XALL-unweighted 0 LONDON: r4_u XALL; cond hold 0.546 strata 0.551; headline=True
- XALL-unweighted 0 NY: r4_u XALL; cond hold 0.518 strata 0.527; headline=True
- XALL-unweighted 5 POOLED: r4_u XALL; cond hold 0.502 strata 0.501; headline=True
- XALL-unweighted 5 ASIA: r4_u XALL; cond hold 0.507 strata 0.500; headline=True
- XALL-unweighted 5 LONDON: r4_u XALL; cond hold 0.537 strata 0.538; headline=True
- XALL-unweighted 5 NY: r4_u XALL; cond hold 0.465 strata 0.472; headline=True
- XALL-unweighted 15 POOLED: r4_u XALL; cond hold 0.516 strata 0.512; headline=True
- XALL-unweighted 15 ASIA: r4_u XALL; cond hold 0.520 strata 0.508; headline=True
- XALL-unweighted 15 LONDON: r4_u XALL; cond hold 0.568 strata 0.567; headline=True
- XALL-unweighted 15 NY: r4_u XALL; cond hold 0.464 strata 0.461; headline=True
- XALL-unweighted 30 POOLED: r4_u XALL; cond hold 0.541 strata 0.537; headline=True
- XALL-unweighted 30 ASIA: r4_u XALL; cond hold 0.540 strata 0.532; headline=True
- XALL-unweighted 30 LONDON: r4_u XALL; cond hold 0.536 strata 0.531; headline=True
- XALL-unweighted 30 NY: r4_u XALL; cond hold 0.542 strata 0.535; headline=True
- X25-strata-weighted 0 POOLED: r4_u X25; cond hold 0.539 strata 0.540; headline=True
- X25-strata-weighted 0 ASIA: r4_u X25; cond hold 0.513 strata 0.512; headline=True
- X25-strata-weighted 0 LONDON: r4_u X25; cond hold 0.563 strata 0.565; headline=True
- X25-strata-weighted 0 NY: r4_u X25; cond hold 0.539 strata 0.546; headline=True
- X25-strata-weighted 5 POOLED: r4_u X25; cond hold 0.506 strata 0.506; headline=True
- X25-strata-weighted 5 ASIA: r4_u X25; cond hold 0.520 strata 0.513; headline=True
- X25-strata-weighted 5 LONDON: r4_u X25; cond hold 0.516 strata 0.517; headline=True
- X25-strata-weighted 5 NY: r4_u X25; cond hold 0.483 strata 0.488; headline=True
- X25-strata-weighted 15 POOLED: r4_u X25; cond hold 0.532 strata 0.529; headline=True
- X25-strata-weighted 15 ASIA: r4_u X25; cond hold 0.529 strata 0.517; headline=True
- X25-strata-weighted 15 LONDON: r4_u X25; cond hold 0.578 strata 0.569; headline=True
- X25-strata-weighted 15 NY: r4_u X25; cond hold 0.495 strata 0.501; headline=True
- X25-strata-weighted 30 POOLED: r4_u X25; cond hold 0.558 strata 0.554; headline=True
- X25-strata-weighted 30 ASIA: r4_u X25; cond hold 0.541 strata 0.536; headline=True
- X25-strata-weighted 30 LONDON: r4_u X25; cond hold 0.545 strata 0.531; headline=True
- X25-strata-weighted 30 NY: r4_u X25; cond hold 0.577 strata 0.578; headline=True
- X16-cond-lgbm 0 POOLED: r4_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm 0 ASIA: r4_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm 0 LONDON: r4_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm 0 NY: r4_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm 5 POOLED: r4_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm 5 ASIA: r4_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm 5 LONDON: r4_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm 5 NY: r4_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm 15 POOLED: r4_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm 15 ASIA: r4_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm 15 LONDON: r4_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm 15 NY: r4_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm 30 POOLED: r4_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm 30 ASIA: r4_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm 30 LONDON: r4_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm 30 NY: r4_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref 0 POOLED: r4_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref 0 ASIA: r4_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref 0 LONDON: r4_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref 0 NY: r4_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref 5 POOLED: r4_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref 5 ASIA: r4_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref 5 LONDON: r4_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref 5 NY: r4_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref 15 POOLED: r4_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref 15 ASIA: r4_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref 15 LONDON: r4_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref 15 NY: r4_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref 30 POOLED: r4_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref 30 ASIA: r4_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref 30 LONDON: r4_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref 30 NY: r4_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
