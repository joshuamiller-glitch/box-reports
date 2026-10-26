# PRED ROUND 58 - block X3 round 7 - X3 round 7

Best HOLDOUT F-R AUC: +15 POOLED 0.535 [0.49,0.58] | ASIA 0.563 [0.51,0.62] | LONDON 0.571 [0.50,0.63] | NY 0.539 [0.48,0.59]
Best HOLDOUT F-R AUC: +30 POOLED 0.554 [0.52,0.59] | ASIA 0.550 [0.49,0.61] | LONDON 0.552 [0.50,0.61] | NY 0.560 [0.50,0.63]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.097 AUC, 5 of 5 economic conditions short.
not found - short by 0.097 AUC and 5 of 5 economic conditions

prereg 9d850e9cea2c39a4d9acd8177961ae2ff2835b15947c8950ac9857511caeea04 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X3/X21_hmm.parquet', 'l2vast/pred/store/X3/X22_drawdown.parquet', 'l2vast/pred/store/X3/X23_handoff.parquet', 'l2vast/pred/store/X3/X24_hazard.parquet', 'l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X27-count-quantile | +15 | LONDON | X27_pneg | 0.523 [-,-] | 0.571 [0.50,0.63] | - | 0.566 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +15 | LONDON | X27_q50 | 0.519 [-,-] | 0.571 [0.50,0.64] | - | 0.564 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +15 | ASIA | X26 | 0.535 [-,-] | 0.563 [0.51,0.62] | - | 0.558 | - | - | - | - | - | - | stack | short by 0.097 AUC, 5 of 5 econ |
| X26-pair-rank | +30 | NY | X26 | 0.517 [-,-] | 0.560 [0.50,0.63] | - | 0.565 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +5 | LONDON | X27_q50 | 0.514 [-,-] | 0.559 [0.49,0.62] | - | 0.556 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +5 | LONDON | X27_pneg | 0.517 [-,-] | 0.558 [0.49,0.62] | - | 0.553 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +15 | LONDON | X28_mean | 0.524 [-,-] | 0.557 [0.49,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +15 | LONDON | X28_gate | 0.520 [-,-] | 0.557 [0.49,0.62] | - | 0.552 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +15 | ASIA | X30 | 0.546 [-,-] | 0.555 [0.49,0.60] | - | 0.548 | - | - | - | - | - | - | stack | short by 0.105 AUC, 5 of 5 econ |
| X26-pair-rank | +30 | POOLED | X26 | 0.533 [-,-] | 0.554 [0.52,0.59] | - | 0.554 | - | - | - | - | - | - | stack | promising: short by 0.126 AUC, 5 of 5 econ |
| X26-pair-rank | +30 | LONDON | X26 | 0.537 [-,-] | 0.552 [0.50,0.61] | - | 0.549 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +30 | ASIA | X26 | 0.544 [-,-] | 0.550 [0.49,0.61] | - | 0.547 | - | - | - | - | - | - | stack | short by 0.110 AUC, 5 of 5 econ |
| X29-pertype-strata | +30 | ASIA | X29 | 0.550 [-,-] | 0.547 [0.48,0.60] | - | 0.540 | - | - | - | - | - | - | stack | short by 0.113 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +15 | LONDON | Q1 | 0.517 [-,-] | 0.546 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | pre | LONDON | X26 | 0.528 [-,-] | 0.540 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +30 | LONDON | X27_pneg | 0.505 [-,-] | 0.540 [0.47,0.61] | - | 0.538 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +30 | ASIA | R0 | 0.546 [-,-] | 0.540 [0.48,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.120 AUC, 5 of 5 econ |
| X28-defer | +30 | NY | X28_mean | 0.494 [-,-] | 0.540 [0.48,0.61] | - | 0.542 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +5 | LONDON | X26 | 0.532 [-,-] | 0.540 [0.49,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +30 | NY | X28_gate | 0.494 [-,-] | 0.539 [0.48,0.61] | - | 0.541 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | +15 | NY | X29 | 0.524 [-,-] | 0.539 [0.48,0.59] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +30 | LONDON | X27_q50 | 0.501 [-,-] | 0.538 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | pre | LONDON | X27_q50 | 0.507 [-,-] | 0.538 [0.46,0.61] | - | 0.543 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +5 | ASIA | X26 | 0.525 [-,-] | 0.537 [0.49,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X29-pertype-strata | +5 | ASIA | X29 | 0.537 [-,-] | 0.536 [0.47,0.60] | - | 0.533 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X27-count-quantile | +5 | ASIA | X27_pneg | 0.526 [-,-] | 0.536 [0.47,0.60] | - | 0.521 | - | - | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +5 | ASIA | Q1 | 0.537 [-,-] | 0.535 [0.48,0.59] | - | 0.528 | - | - | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X28-defer | pre | LONDON | X28_mean | 0.526 [-,-] | 0.535 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +15 | POOLED | X30 | 0.522 [-,-] | 0.535 [0.49,0.58] | - | 0.532 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X28-defer | pre | LONDON | X28_gate | 0.522 [-,-] | 0.535 [0.47,0.60] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +15 | LONDON | X30 | 0.513 [-,-] | 0.534 [0.47,0.60] | - | 0.524 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +30 | POOLED | X28_mean | 0.514 [-,-] | 0.532 [0.50,0.56] | - | 0.530 | - | - | - | - | - | - | stack | promising: short by 0.148 AUC, 5 of 5 econ |
| X28-defer | +30 | POOLED | X28_gate | 0.518 [-,-] | 0.532 [0.50,0.56] | - | 0.529 | - | - | - | - | - | - | stack | promising: short by 0.148 AUC, 5 of 5 econ |
| X26-pair-rank | +15 | POOLED | X26 | 0.522 [-,-] | 0.531 [0.49,0.57] | - | 0.531 | - | - | - | - | - | - | stack | short by 0.149 AUC, 5 of 5 econ |
| R0-ref-ref | +15 | ASIA | R0 | 0.542 [-,-] | 0.531 [0.47,0.60] | - | 0.530 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X27-count-quantile | +5 | ASIA | X27_q50 | 0.521 [-,-] | 0.531 [0.47,0.59] | - | 0.516 | - | - | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X26-pair-rank | pre | ASIA | X26 | 0.523 [-,-] | 0.530 [0.47,0.59] | - | 0.521 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm-ref | +30 | NY | Q1 | 0.492 [-,-] | 0.529 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | pre | ASIA | Q1 | 0.529 [-,-] | 0.529 [0.46,0.60] | - | 0.520 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X27-count-quantile | pre | LONDON | X27_pneg | 0.505 [-,-] | 0.528 [0.46,0.60] | - | 0.525 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +30 | LONDON | X28_mean | 0.502 [-,-] | 0.528 [0.46,0.60] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +30 | ASIA | X30 | 0.535 [-,-] | 0.528 [0.47,0.58] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.132 AUC, 5 of 5 econ |
| X26-pair-rank | pre | POOLED | X26 | 0.519 [-,-] | 0.528 [0.49,0.57] | - | 0.527 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X28-defer | +30 | LONDON | X28_gate | 0.512 [-,-] | 0.527 [0.46,0.60] | - | 0.521 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | pre | NY | Q1 | 0.506 [-,-] | 0.527 [0.48,0.58] | - | 0.532 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +5 | LONDON | X28_gate | 0.509 [-,-] | 0.527 [0.46,0.60] | - | 0.528 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | pre | NY | X30 | 0.516 [-,-] | 0.527 [0.47,0.59] | - | 0.533 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +5 | LONDON | X28_mean | 0.518 [-,-] | 0.526 [0.46,0.60] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | +15 | POOLED | Q1 | 0.520 [-,-] | 0.526 [0.48,0.57] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | pre | POOLED | Q1 | 0.519 [-,-] | 0.526 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X29-pertype-strata | +15 | POOLED | X29 | 0.517 [-,-] | 0.526 [0.49,0.56] | - | 0.520 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X28-defer | +30 | ASIA | X28_mean | 0.544 [-,-] | 0.525 [0.47,0.57] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X28-defer | pre | POOLED | X28_mean | 0.519 [-,-] | 0.525 [0.49,0.56] | - | 0.524 | - | - | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X28-defer | +30 | ASIA | X28_gate | 0.548 [-,-] | 0.525 [0.47,0.57] | - | 0.514 | - | - | - | - | - | - | stack | short by 0.135 AUC, 5 of 5 econ |
| X28-defer | pre | POOLED | X28_gate | 0.525 [-,-] | 0.524 [0.49,0.56] | - | 0.523 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | pre | LONDON | Q1 | 0.523 [-,-] | 0.523 [0.46,0.59] | - | 0.516 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | pre | ASIA | X28_mean | 0.535 [-,-] | 0.523 [0.46,0.59] | - | 0.518 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X27-count-quantile | +5 | POOLED | X27_q50 | 0.505 [-,-] | 0.523 [0.49,0.57] | - | 0.522 | - | - | - | - | - | - | stack | short by 0.157 AUC, 5 of 5 econ |
| X29-pertype-strata | +15 | ASIA | X29 | 0.526 [-,-] | 0.523 [0.47,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.137 AUC, 5 of 5 econ |
| X29-pertype-strata | pre | NY | X29 | 0.499 [-,-] | 0.522 [0.47,0.58] | - | 0.535 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | pre | ASIA | X28_gate | 0.550 [-,-] | 0.522 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X29-pertype-strata | +5 | LONDON | X29 | 0.502 [-,-] | 0.522 [0.46,0.59] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +5 | ASIA | X28_gate | 0.536 [-,-] | 0.522 [0.47,0.58] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.138 AUC, 5 of 5 econ |
| X27-count-quantile | +30 | POOLED | X27_q50 | 0.505 [-,-] | 0.522 [0.49,0.55] | - | 0.520 | - | - | - | - | - | - | stack | promising: short by 0.158 AUC, 5 of 5 econ |
| X28-defer | +5 | ASIA | X28_mean | 0.527 [-,-] | 0.521 [0.47,0.58] | - | 0.513 | - | - | - | - | - | - | stack | short by 0.139 AUC, 5 of 5 econ |
| X28-defer | +15 | POOLED | X28_gate | 0.512 [-,-] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +15 | NY | Q1 | 0.523 [-,-] | 0.520 [0.46,0.58] | - | 0.523 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +30 | POOLED | X27_pneg | 0.506 [-,-] | 0.520 [0.49,0.55] | - | 0.518 | - | - | - | - | - | - | stack | promising: short by 0.160 AUC, 5 of 5 econ |
| X26-pair-rank | +15 | LONDON | X26 | 0.505 [-,-] | 0.520 [0.46,0.57] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +15 | POOLED | X28_mean | 0.519 [-,-] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X30-bagged-cond | +30 | NY | X30 | 0.494 [-,-] | 0.520 [0.46,0.59] | - | 0.527 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +5 | ASIA | X30 | 0.514 [-,-] | 0.520 [0.47,0.58] | - | 0.509 | - | - | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X30-bagged-cond | pre | POOLED | X30 | 0.518 [-,-] | 0.520 [0.48,0.56] | - | 0.518 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X27-count-quantile | +5 | POOLED | X27_pneg | 0.504 [-,-] | 0.520 [0.48,0.56] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X27-count-quantile | +30 | NY | X27_q50 | 0.513 [-,-] | 0.519 [0.47,0.59] | - | 0.529 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | +30 | POOLED | Q1 | 0.509 [-,-] | 0.519 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | promising: short by 0.161 AUC, 5 of 5 econ |
| X30-bagged-cond | +30 | POOLED | X30 | 0.514 [-,-] | 0.518 [0.49,0.55] | - | 0.513 | - | - | - | - | - | - | stack | promising: short by 0.162 AUC, 5 of 5 econ |
| X28-defer | pre | NY | X28_mean | 0.498 [-,-] | 0.518 [0.47,0.57] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | pre | NY | X28_gate | 0.506 [-,-] | 0.518 [0.47,0.57] | - | 0.526 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | +30 | LONDON | Q1 | 0.497 [-,-] | 0.518 [0.45,0.60] | - | 0.513 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | pre | ASIA | X30 | 0.530 [-,-] | 0.517 [0.45,0.59] | - | 0.509 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X16-cond-lgbm-ref | +5 | LONDON | Q1 | 0.515 [-,-] | 0.517 [0.45,0.58] | - | 0.520 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | pre | ASIA | R0 | 0.540 [-,-] | 0.517 [0.45,0.58] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X30-bagged-cond | pre | LONDON | X30 | 0.508 [-,-] | 0.517 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +15 | NY | X26 | 0.526 [-,-] | 0.516 [0.45,0.58] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | pre | NY | X26 | 0.500 [-,-] | 0.516 [0.43,0.59] | - | 0.518 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +15 | POOLED | X27_q50 | 0.509 [-,-] | 0.516 [0.48,0.55] | - | 0.515 | - | - | - | - | - | - | stack | short by 0.164 AUC, 5 of 5 econ |
| X27-count-quantile | pre | POOLED | X27_q50 | 0.499 [-,-] | 0.515 [0.48,0.55] | - | 0.517 | - | - | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X28-defer | +15 | ASIA | X28_gate | 0.523 [-,-] | 0.515 [0.45,0.57] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.145 AUC, 5 of 5 econ |
| X28-defer | +15 | ASIA | X28_mean | 0.525 [-,-] | 0.514 [0.45,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.146 AUC, 5 of 5 econ |
| X30-bagged-cond | +15 | NY | X30 | 0.508 [-,-] | 0.513 [0.45,0.58] | - | 0.519 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | +15 | LONDON | X29 | 0.498 [-,-] | 0.513 [0.44,0.59] | - | 0.507 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X16-cond-lgbm-ref | +15 | ASIA | Q1 | 0.519 [-,-] | 0.513 [0.46,0.57] | - | 0.503 | - | - | - | - | - | - | stack | short by 0.147 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +5 | POOLED | Q1 | 0.507 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X26-pair-rank | +5 | POOLED | X26 | 0.515 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X27-count-quantile | +15 | POOLED | X27_pneg | 0.508 [-,-] | 0.512 [0.48,0.55] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.168 AUC, 5 of 5 econ |
| X27-count-quantile | pre | POOLED | X27_pneg | 0.497 [-,-] | 0.509 [0.48,0.54] | - | 0.511 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X27-count-quantile | pre | ASIA | X27_pneg | 0.499 [-,-] | 0.509 [0.44,0.58] | - | 0.506 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X27-count-quantile | pre | ASIA | X27_q50 | 0.500 [-,-] | 0.509 [0.44,0.58] | - | 0.500 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X29-pertype-strata | +30 | POOLED | X29 | 0.510 [-,-] | 0.509 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.171 AUC, 5 of 5 econ |
| X27-count-quantile | +15 | ASIA | X27_pneg | 0.510 [-,-] | 0.509 [0.45,0.55] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.151 AUC, 5 of 5 econ |
| X27-count-quantile | +30 | NY | X27_pneg | 0.509 [-,-] | 0.508 [0.46,0.58] | - | 0.515 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | +5 | POOLED | X29 | 0.500 [-,-] | 0.508 [0.47,0.54] | - | 0.506 | - | - | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X27-count-quantile | +30 | ASIA | X27_pneg | 0.505 [-,-] | 0.508 [0.45,0.56] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X27-count-quantile | +15 | ASIA | X27_q50 | 0.509 [-,-] | 0.507 [0.45,0.56] | - | 0.500 | - | - | - | - | - | - | stack | short by 0.153 AUC, 5 of 5 econ |
| X28-defer | +5 | POOLED | X28_gate | 0.507 [-,-] | 0.506 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +30 | ASIA | Q1 | 0.536 [-,-] | 0.506 [0.44,0.56] | - | 0.494 | - | - | - | - | - | - | stack | short by 0.154 AUC, 5 of 5 econ |
| X28-defer | +5 | POOLED | X28_mean | 0.505 [-,-] | 0.506 [0.47,0.54] | - | 0.504 | - | - | - | - | - | - | stack | short by 0.174 AUC, 5 of 5 econ |
| X29-pertype-strata | +30 | NY | X29 | 0.497 [-,-] | 0.505 [0.45,0.56] | - | 0.506 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +5 | LONDON | X30 | 0.503 [-,-] | 0.504 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +30 | ASIA | X27_q50 | 0.500 [-,-] | 0.504 [0.45,0.55] | - | 0.499 | - | - | - | - | - | - | stack | short by 0.156 AUC, 5 of 5 econ |
| X29-pertype-strata | pre | POOLED | X29 | 0.497 [-,-] | 0.503 [0.47,0.54] | - | 0.502 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| R0-ref-ref | +30 | POOLED | R0 | 0.508 [-,-] | 0.503 [0.47,0.54] | - | 0.496 | - | - | - | - | - | - | stack | short by 0.177 AUC, 5 of 5 econ |
| X30-bagged-cond | +30 | LONDON | X30 | 0.508 [-,-] | 0.501 [0.44,0.56] | - | 0.495 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +30 | NY | R0 | 0.495 [-,-] | 0.500 [0.42,0.57] | - | 0.500 | - | - | - | - | - | - | stack | baseline |
| X27-count-quantile | pre | NY | X27_q50 | 0.489 [-,-] | 0.498 [0.44,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +5 | ASIA | R0 | 0.526 [-,-] | 0.498 [0.44,0.55] | - | 0.486 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X27-count-quantile | pre | NY | X27_pneg | 0.489 [-,-] | 0.498 [0.43,0.56] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | pre | ASIA | X29 | 0.528 [-,-] | 0.496 [0.43,0.57] | - | 0.487 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X30-bagged-cond | +5 | POOLED | X30 | 0.494 [-,-] | 0.496 [0.46,0.53] | - | 0.495 | - | - | - | - | - | - | stack | short by 0.184 AUC, 5 of 5 econ |
| X16-cond-lgbm-ref | +5 | NY | Q1 | 0.469 [-,-] | 0.493 [0.43,0.55] | - | 0.499 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +15 | NY | X28_gate | 0.496 [-,-] | 0.492 [0.44,0.55] | - | 0.494 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | pre | LONDON | X29 | 0.460 [-,-] | 0.491 [0.43,0.55] | - | 0.489 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +15 | NY | X28_mean | 0.508 [-,-] | 0.490 [0.44,0.55] | - | 0.492 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +5 | NY | X27_q50 | 0.481 [-,-] | 0.487 [0.43,0.55] | - | 0.497 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +30 | LONDON | R0 | 0.488 [-,-] | 0.486 [0.42,0.55] | - | 0.475 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | +15 | POOLED | R0 | 0.493 [-,-] | 0.478 [0.44,0.52] | - | 0.479 | - | - | - | - | - | - | stack | short by 0.202 AUC, 5 of 5 econ |
| X27-count-quantile | +5 | NY | X27_pneg | 0.474 [-,-] | 0.477 [0.42,0.54] | - | 0.486 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +5 | NY | X28_mean | 0.468 [-,-] | 0.475 [0.43,0.53] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-defer | +5 | NY | X28_gate | 0.477 [-,-] | 0.474 [0.42,0.53] | - | 0.482 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-count-quantile | +15 | NY | X27_q50 | 0.497 [-,-] | 0.473 [0.42,0.52] | - | 0.472 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | +30 | LONDON | X29 | 0.476 [-,-] | 0.469 [0.40,0.54] | - | 0.469 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +15 | NY | R0 | 0.481 [-,-] | 0.469 [0.40,0.53] | - | 0.482 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | pre | POOLED | R0 | 0.499 [-,-] | 0.468 [0.43,0.51] | - | 0.459 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| X27-count-quantile | +15 | NY | X27_pneg | 0.494 [-,-] | 0.467 [0.41,0.52] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-pair-rank | +5 | NY | X26 | 0.489 [-,-] | 0.463 [0.41,0.53] | - | 0.467 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X29-pertype-strata | +5 | NY | X29 | 0.456 [-,-] | 0.462 [0.40,0.52] | - | 0.470 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X30-bagged-cond | +5 | NY | X30 | 0.460 [-,-] | 0.460 [0.40,0.52] | - | 0.461 | - | - | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| R0-ref-ref | +5 | NY | R0 | 0.469 [-,-] | 0.460 [0.40,0.51] | - | 0.478 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | pre | NY | R0 | 0.475 [-,-] | 0.459 [0.39,0.53] | - | 0.473 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | +5 | POOLED | R0 | 0.488 [-,-] | 0.454 [0.42,0.49] | - | 0.447 | - | - | - | - | - | - | stack | dead (no gain over baseline) |
| R0-ref-ref | +15 | LONDON | R0 | 0.456 [-,-] | 0.442 [0.37,0.51] | - | 0.436 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | pre | LONDON | R0 | 0.483 [-,-] | 0.437 [0.38,0.50] | - | 0.417 | - | - | - | - | - | - | stack | baseline |
| R0-ref-ref | +5 | LONDON | R0 | 0.467 [-,-] | 0.406 [0.35,0.46] | - | 0.395 | - | - | - | - | - | - | stack | baseline |

One-sentence notes:
- X26-pair-rank 0 POOLED: r5_u X26; cond hold 0.528 strata 0.527; headline=True
- X26-pair-rank 0 ASIA: r5_u X26; cond hold 0.530 strata 0.521; headline=True
- X26-pair-rank 0 LONDON: r5_u X26; cond hold 0.540 strata 0.534; headline=True
- X26-pair-rank 0 NY: r5_u X26; cond hold 0.516 strata 0.518; headline=True
- X26-pair-rank 5 POOLED: r5_u X26; cond hold 0.512 strata 0.511; headline=True
- X26-pair-rank 5 ASIA: r5_u X26; cond hold 0.537 strata 0.528; headline=True
- X26-pair-rank 5 LONDON: r5_u X26; cond hold 0.540 strata 0.534; headline=True
- X26-pair-rank 5 NY: r5_u X26; cond hold 0.463 strata 0.467; headline=True
- X26-pair-rank 15 POOLED: r5_u X26; cond hold 0.531 strata 0.531; headline=True
- X26-pair-rank 15 ASIA: r5_u X26; cond hold 0.563 strata 0.558; headline=True
- X26-pair-rank 15 LONDON: r5_u X26; cond hold 0.520 strata 0.519; headline=True
- X26-pair-rank 15 NY: r5_u X26; cond hold 0.516 strata 0.515; headline=True
- X26-pair-rank 30 POOLED: r5_u X26; cond hold 0.554 strata 0.554; headline=True
- X26-pair-rank 30 ASIA: r5_u X26; cond hold 0.550 strata 0.547; headline=True
- X26-pair-rank 30 LONDON: r5_u X26; cond hold 0.552 strata 0.549; headline=True
- X26-pair-rank 30 NY: r5_u X26; cond hold 0.560 strata 0.565; headline=True
- X27-count-quantile 0 POOLED: r5_u X27_pneg; cond hold 0.509 strata 0.511; headline=False
- X27-count-quantile 0 ASIA: r5_u X27_pneg; cond hold 0.509 strata 0.506; headline=False
- X27-count-quantile 0 LONDON: r5_u X27_pneg; cond hold 0.528 strata 0.525; headline=False
- X27-count-quantile 0 NY: r5_u X27_pneg; cond hold 0.498 strata 0.499; headline=False
- X27-count-quantile 5 POOLED: r5_u X27_pneg; cond hold 0.520 strata 0.517; headline=False
- X27-count-quantile 5 ASIA: r5_u X27_pneg; cond hold 0.536 strata 0.521; headline=False
- X27-count-quantile 5 LONDON: r5_u X27_pneg; cond hold 0.558 strata 0.553; headline=False
- X27-count-quantile 5 NY: r5_u X27_pneg; cond hold 0.477 strata 0.486; headline=False
- X27-count-quantile 15 POOLED: r5_u X27_pneg; cond hold 0.512 strata 0.511; headline=False
- X27-count-quantile 15 ASIA: r5_u X27_pneg; cond hold 0.509 strata 0.499; headline=False
- X27-count-quantile 15 LONDON: r5_u X27_pneg; cond hold 0.571 strata 0.566; headline=False
- X27-count-quantile 15 NY: r5_u X27_pneg; cond hold 0.467 strata 0.467; headline=False
- X27-count-quantile 30 POOLED: r5_u X27_pneg; cond hold 0.520 strata 0.518; headline=True
- X27-count-quantile 30 ASIA: r5_u X27_pneg; cond hold 0.508 strata 0.504; headline=True
- X27-count-quantile 30 LONDON: r5_u X27_pneg; cond hold 0.540 strata 0.538; headline=True
- X27-count-quantile 30 NY: r5_u X27_pneg; cond hold 0.508 strata 0.515; headline=True
- X27-count-quantile 0 POOLED: r5_u X27_q50; cond hold 0.515 strata 0.517; headline=True
- X27-count-quantile 0 ASIA: r5_u X27_q50; cond hold 0.509 strata 0.500; headline=True
- X27-count-quantile 0 LONDON: r5_u X27_q50; cond hold 0.538 strata 0.543; headline=True
- X27-count-quantile 0 NY: r5_u X27_q50; cond hold 0.498 strata 0.499; headline=True
- X27-count-quantile 5 POOLED: r5_u X27_q50; cond hold 0.523 strata 0.522; headline=True
- X27-count-quantile 5 ASIA: r5_u X27_q50; cond hold 0.531 strata 0.516; headline=True
- X27-count-quantile 5 LONDON: r5_u X27_q50; cond hold 0.559 strata 0.556; headline=True
- X27-count-quantile 5 NY: r5_u X27_q50; cond hold 0.487 strata 0.497; headline=True
- X27-count-quantile 15 POOLED: r5_u X27_q50; cond hold 0.516 strata 0.515; headline=True
- X27-count-quantile 15 ASIA: r5_u X27_q50; cond hold 0.507 strata 0.500; headline=True
- X27-count-quantile 15 LONDON: r5_u X27_q50; cond hold 0.571 strata 0.564; headline=True
- X27-count-quantile 15 NY: r5_u X27_q50; cond hold 0.473 strata 0.472; headline=True
- X27-count-quantile 30 POOLED: r5_u X27_q50; cond hold 0.522 strata 0.520; headline=False
- X27-count-quantile 30 ASIA: r5_u X27_q50; cond hold 0.504 strata 0.499; headline=False
- X27-count-quantile 30 LONDON: r5_u X27_q50; cond hold 0.538 strata 0.534; headline=False
- X27-count-quantile 30 NY: r5_u X27_q50; cond hold 0.519 strata 0.529; headline=False
- X28-defer 0 POOLED: r5_u X28_gate; cond hold 0.524 strata 0.523; headline=True
- X28-defer 0 ASIA: r5_u X28_gate; cond hold 0.522 strata 0.519; headline=True
- X28-defer 0 LONDON: r5_u X28_gate; cond hold 0.535 strata 0.532; headline=True
- X28-defer 0 NY: r5_u X28_gate; cond hold 0.518 strata 0.526; headline=True
- X28-defer 5 POOLED: r5_u X28_gate; cond hold 0.506 strata 0.504; headline=True
- X28-defer 5 ASIA: r5_u X28_gate; cond hold 0.522 strata 0.515; headline=True
- X28-defer 5 LONDON: r5_u X28_gate; cond hold 0.527 strata 0.528; headline=True
- X28-defer 5 NY: r5_u X28_gate; cond hold 0.474 strata 0.482; headline=True
- X28-defer 15 POOLED: r5_u X28_gate; cond hold 0.520 strata 0.517; headline=False
- X28-defer 15 ASIA: r5_u X28_gate; cond hold 0.515 strata 0.502; headline=False
- X28-defer 15 LONDON: r5_u X28_gate; cond hold 0.557 strata 0.552; headline=False
- X28-defer 15 NY: r5_u X28_gate; cond hold 0.492 strata 0.494; headline=False
- X28-defer 30 POOLED: r5_u X28_gate; cond hold 0.532 strata 0.529; headline=True
- X28-defer 30 ASIA: r5_u X28_gate; cond hold 0.525 strata 0.514; headline=True
- X28-defer 30 LONDON: r5_u X28_gate; cond hold 0.527 strata 0.521; headline=True
- X28-defer 30 NY: r5_u X28_gate; cond hold 0.539 strata 0.541; headline=True
- X28-defer 0 POOLED: r5_u X28_mean; cond hold 0.525 strata 0.524; headline=False
- X28-defer 0 ASIA: r5_u X28_mean; cond hold 0.523 strata 0.518; headline=False
- X28-defer 0 LONDON: r5_u X28_mean; cond hold 0.535 strata 0.534; headline=False
- X28-defer 0 NY: r5_u X28_mean; cond hold 0.518 strata 0.526; headline=False
- X28-defer 5 POOLED: r5_u X28_mean; cond hold 0.506 strata 0.504; headline=False
- X28-defer 5 ASIA: r5_u X28_mean; cond hold 0.521 strata 0.513; headline=False
- X28-defer 5 LONDON: r5_u X28_mean; cond hold 0.526 strata 0.527; headline=False
- X28-defer 5 NY: r5_u X28_mean; cond hold 0.475 strata 0.482; headline=False
- X28-defer 15 POOLED: r5_u X28_mean; cond hold 0.520 strata 0.517; headline=True
- X28-defer 15 ASIA: r5_u X28_mean; cond hold 0.514 strata 0.503; headline=True
- X28-defer 15 LONDON: r5_u X28_mean; cond hold 0.557 strata 0.552; headline=True
- X28-defer 15 NY: r5_u X28_mean; cond hold 0.490 strata 0.492; headline=True
- X28-defer 30 POOLED: r5_u X28_mean; cond hold 0.532 strata 0.530; headline=False
- X28-defer 30 ASIA: r5_u X28_mean; cond hold 0.525 strata 0.514; headline=False
- X28-defer 30 LONDON: r5_u X28_mean; cond hold 0.528 strata 0.523; headline=False
- X28-defer 30 NY: r5_u X28_mean; cond hold 0.540 strata 0.542; headline=False
- X29-pertype-strata 0 POOLED: r5_u X29; cond hold 0.503 strata 0.502; headline=True
- X29-pertype-strata 0 ASIA: r5_u X29; cond hold 0.496 strata 0.487; headline=True
- X29-pertype-strata 0 LONDON: r5_u X29; cond hold 0.491 strata 0.489; headline=True
- X29-pertype-strata 0 NY: r5_u X29; cond hold 0.522 strata 0.535; headline=True
- X29-pertype-strata 5 POOLED: r5_u X29; cond hold 0.508 strata 0.506; headline=True
- X29-pertype-strata 5 ASIA: r5_u X29; cond hold 0.536 strata 0.533; headline=True
- X29-pertype-strata 5 LONDON: r5_u X29; cond hold 0.522 strata 0.519; headline=True
- X29-pertype-strata 5 NY: r5_u X29; cond hold 0.462 strata 0.470; headline=True
- X29-pertype-strata 15 POOLED: r5_u X29; cond hold 0.526 strata 0.520; headline=True
- X29-pertype-strata 15 ASIA: r5_u X29; cond hold 0.523 strata 0.513; headline=True
- X29-pertype-strata 15 LONDON: r5_u X29; cond hold 0.513 strata 0.507; headline=True
- X29-pertype-strata 15 NY: r5_u X29; cond hold 0.539 strata 0.534; headline=True
- X29-pertype-strata 30 POOLED: r5_u X29; cond hold 0.509 strata 0.506; headline=True
- X29-pertype-strata 30 ASIA: r5_u X29; cond hold 0.547 strata 0.540; headline=True
- X29-pertype-strata 30 LONDON: r5_u X29; cond hold 0.469 strata 0.469; headline=True
- X29-pertype-strata 30 NY: r5_u X29; cond hold 0.505 strata 0.506; headline=True
- X30-bagged-cond 0 POOLED: r5_u X30; cond hold 0.520 strata 0.518; headline=True
- X30-bagged-cond 0 ASIA: r5_u X30; cond hold 0.517 strata 0.509; headline=True
- X30-bagged-cond 0 LONDON: r5_u X30; cond hold 0.517 strata 0.510; headline=True
- X30-bagged-cond 0 NY: r5_u X30; cond hold 0.527 strata 0.533; headline=True
- X30-bagged-cond 5 POOLED: r5_u X30; cond hold 0.496 strata 0.495; headline=True
- X30-bagged-cond 5 ASIA: r5_u X30; cond hold 0.520 strata 0.509; headline=True
- X30-bagged-cond 5 LONDON: r5_u X30; cond hold 0.504 strata 0.502; headline=True
- X30-bagged-cond 5 NY: r5_u X30; cond hold 0.460 strata 0.461; headline=True
- X30-bagged-cond 15 POOLED: r5_u X30; cond hold 0.535 strata 0.532; headline=True
- X30-bagged-cond 15 ASIA: r5_u X30; cond hold 0.555 strata 0.548; headline=True
- X30-bagged-cond 15 LONDON: r5_u X30; cond hold 0.534 strata 0.524; headline=True
- X30-bagged-cond 15 NY: r5_u X30; cond hold 0.513 strata 0.519; headline=True
- X30-bagged-cond 30 POOLED: r5_u X30; cond hold 0.518 strata 0.513; headline=True
- X30-bagged-cond 30 ASIA: r5_u X30; cond hold 0.528 strata 0.517; headline=True
- X30-bagged-cond 30 LONDON: r5_u X30; cond hold 0.501 strata 0.495; headline=True
- X30-bagged-cond 30 NY: r5_u X30; cond hold 0.520 strata 0.527; headline=True
- X16-cond-lgbm-ref 0 POOLED: r5_u Q1 (comparator); cond hold 0.526 strata 0.523; headline=False
- X16-cond-lgbm-ref 0 ASIA: r5_u Q1 (comparator); cond hold 0.529 strata 0.520; headline=False
- X16-cond-lgbm-ref 0 LONDON: r5_u Q1 (comparator); cond hold 0.523 strata 0.516; headline=False
- X16-cond-lgbm-ref 0 NY: r5_u Q1 (comparator); cond hold 0.527 strata 0.532; headline=False
- X16-cond-lgbm-ref 5 POOLED: r5_u Q1 (comparator); cond hold 0.512 strata 0.511; headline=False
- X16-cond-lgbm-ref 5 ASIA: r5_u Q1 (comparator); cond hold 0.535 strata 0.528; headline=False
- X16-cond-lgbm-ref 5 LONDON: r5_u Q1 (comparator); cond hold 0.517 strata 0.520; headline=False
- X16-cond-lgbm-ref 5 NY: r5_u Q1 (comparator); cond hold 0.493 strata 0.499; headline=False
- X16-cond-lgbm-ref 15 POOLED: r5_u Q1 (comparator); cond hold 0.526 strata 0.524; headline=False
- X16-cond-lgbm-ref 15 ASIA: r5_u Q1 (comparator); cond hold 0.513 strata 0.503; headline=False
- X16-cond-lgbm-ref 15 LONDON: r5_u Q1 (comparator); cond hold 0.546 strata 0.542; headline=False
- X16-cond-lgbm-ref 15 NY: r5_u Q1 (comparator); cond hold 0.520 strata 0.523; headline=False
- X16-cond-lgbm-ref 30 POOLED: r5_u Q1 (comparator); cond hold 0.519 strata 0.515; headline=False
- X16-cond-lgbm-ref 30 ASIA: r5_u Q1 (comparator); cond hold 0.506 strata 0.494; headline=False
- X16-cond-lgbm-ref 30 LONDON: r5_u Q1 (comparator); cond hold 0.518 strata 0.513; headline=False
- X16-cond-lgbm-ref 30 NY: r5_u Q1 (comparator); cond hold 0.529 strata 0.534; headline=False
- R0-ref-ref 0 POOLED: r5_u R0 (comparator); cond hold 0.468 strata 0.459; headline=False
- R0-ref-ref 0 ASIA: r5_u R0 (comparator); cond hold 0.517 strata 0.487; headline=False
- R0-ref-ref 0 LONDON: r5_u R0 (comparator); cond hold 0.437 strata 0.417; headline=False
- R0-ref-ref 0 NY: r5_u R0 (comparator); cond hold 0.459 strata 0.473; headline=False
- R0-ref-ref 5 POOLED: r5_u R0 (comparator); cond hold 0.454 strata 0.447; headline=False
- R0-ref-ref 5 ASIA: r5_u R0 (comparator); cond hold 0.498 strata 0.486; headline=False
- R0-ref-ref 5 LONDON: r5_u R0 (comparator); cond hold 0.406 strata 0.395; headline=False
- R0-ref-ref 5 NY: r5_u R0 (comparator); cond hold 0.460 strata 0.478; headline=False
- R0-ref-ref 15 POOLED: r5_u R0 (comparator); cond hold 0.478 strata 0.479; headline=False
- R0-ref-ref 15 ASIA: r5_u R0 (comparator); cond hold 0.531 strata 0.530; headline=False
- R0-ref-ref 15 LONDON: r5_u R0 (comparator); cond hold 0.442 strata 0.436; headline=False
- R0-ref-ref 15 NY: r5_u R0 (comparator); cond hold 0.469 strata 0.482; headline=False
- R0-ref-ref 30 POOLED: r5_u R0 (comparator); cond hold 0.503 strata 0.496; headline=False
- R0-ref-ref 30 ASIA: r5_u R0 (comparator); cond hold 0.540 strata 0.530; headline=False
- R0-ref-ref 30 LONDON: r5_u R0 (comparator); cond hold 0.486 strata 0.475; headline=False
- R0-ref-ref 30 NY: r5_u R0 (comparator); cond hold 0.500 strata 0.500; headline=False
