# PRED ROUND 71 - block X1 round 5 - X-unlocked-conditional

Best HOLDOUT F-R AUC: +15 POOLED 0.540 [0.50,0.58] | ASIA 0.580 [0.52,0.63] | LONDON 0.557 [0.49,0.62] | NY 0.579 [0.52,0.64]
Best HOLDOUT F-R AUC: +30 POOLED 0.524 [0.48,0.57] | ASIA 0.542 [0.48,0.61] | LONDON 0.530 [0.48,0.59] | NY 0.536 [0.47,0.60]
Best G HOLDOUT AUC: -
Gap to FOUND: 0.080 AUC, 5 of 5 economic conditions short.
not found - short by 0.080 AUC and 5 of 5 economic conditions

prereg 341a251134a2f71aea15fba50a46fdb84a7c77c33fa16bac47995c081ffacb5f ; trials added 1500 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X4u_round5.parquet', 'l2vast/pred/store/X5u_round5.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X26-condranker-X45u | +15 | ASIA | d_pair | 0.539 [0.49,0.58] | 0.580 [0.52,0.63] | - | 0.580 | 0.574 | N | - | - | - | - | stack | short by 0.080 AUC, 5 of 5 econ |
| X26-condranker-X45u | +15 | NY | d_xe | 0.532 [0.48,0.58] | 0.579 [0.52,0.64] | - | 0.582 | 0.572 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +15 | ASIA | X5u:logit2 | 0.543 [0.50,0.59] | 0.575 [0.52,0.63] | - | 0.574 | 0.577 | ok | - | - | - | - | stack | short by 0.085 AUC, 5 of 5 econ |
| X1-condranker-unl | +45 | ASIA | cc_xe | 0.548 [0.50,0.59] | 0.574 [0.51,0.65] | - | 0.582 | 0.573 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +15 | ASIA | X4u:logit2 | 0.537 [0.49,0.58] | 0.570 [0.51,0.63] | - | 0.571 | 0.571 | ok | - | - | - | - | stack | short by 0.090 AUC, 5 of 5 econ |
| X5-pathstate-unl | +45 | ASIA | X5u:logit2 | 0.531 [0.49,0.58] | 0.558 [0.49,0.62] | - | 0.556 | 0.565 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +60 | ASIA | cmt_rf | 0.552 [0.50,0.59] | 0.558 [0.49,0.62] | - | 0.558 | 0.540 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +15 | LONDON | d_pair | 0.515 [0.47,0.56] | 0.557 [0.49,0.62] | - | 0.552 | 0.528 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +60 | ASIA | d_xe | 0.525 [0.48,0.57] | 0.557 [0.49,0.63] | - | 0.552 | 0.548 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | pre | ASIA | d_xe | 0.548 [0.50,0.59] | 0.555 [0.50,0.61] | - | 0.550 | 0.556 | N | - | - | - | - | stack | short by 0.105 AUC, 5 of 5 econ |
| X1-condranker-unl | +20 | LONDON | cc_pair | 0.538 [0.50,0.58] | 0.553 [0.50,0.61] | - | 0.558 | 0.527 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +60 | ASIA | cc_xe | 0.530 [0.49,0.57] | 0.553 [0.49,0.62] | - | 0.547 | 0.548 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +15 | ASIA | cfree30 | 0.518 [0.47,0.56] | 0.552 [0.48,0.63] | - | 0.551 | 0.547 | N | - | - | - | - |  | short by 0.108 AUC, 5 of 5 econ |
| X2-monotone-unl | +5 | LONDON | cmono15 | 0.522 [0.47,0.57] | 0.550 [0.48,0.62] | - | 0.551 | 0.533 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +20 | LONDON | d_etbag | 0.498 [0.45,0.54] | 0.550 [0.49,0.61] | - | 0.553 | 0.518 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +45 | ASIA | d_xe | 0.539 [0.49,0.59] | 0.547 [0.48,0.62] | - | 0.549 | 0.541 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +60 | LONDON | X45u:gbt3 | 0.544 [0.50,0.59] | 0.546 [0.49,0.60] | - | 0.540 | 0.533 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | pre | ASIA | cfree15 | 0.550 [0.51,0.59] | 0.546 [0.49,0.61] | - | 0.535 | 0.547 | N | - | - | - | - |  | short by 0.114 AUC, 5 of 5 econ |
| X2-monotone-unl | +45 | NY | cfree15 | 0.516 [0.47,0.56] | 0.546 [0.48,0.61] | - | 0.551 | 0.543 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +15 | LONDON | d_etbag | 0.499 [0.46,0.55] | 0.545 [0.48,0.61] | - | 0.538 | 0.523 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +60 | LONDON | X4u:gbt3 | 0.543 [0.50,0.58] | 0.545 [0.49,0.60] | - | 0.539 | 0.533 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +60 | ASIA | d_etbag | 0.533 [0.49,0.58] | 0.542 [0.48,0.61] | - | 0.532 | 0.527 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +30 | ASIA | cfree15 | 0.548 [0.51,0.59] | 0.542 [0.48,0.61] | - | 0.528 | 0.533 | N | - | - | - | - |  | short by 0.118 AUC, 5 of 5 econ |
| X27-etbag-X45u | +10 | LONDON | d_etbag | 0.513 [0.47,0.56] | 0.542 [0.48,0.60] | - | 0.543 | 0.522 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +5 | LONDON | cc_pair | 0.524 [0.48,0.57] | 0.541 [0.47,0.61] | - | 0.544 | 0.512 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +15 | POOLED | d_pair | 0.514 [0.49,0.54] | 0.540 [0.50,0.58] | - | 0.534 | 0.528 | N | - | - | - | - | stack | promising: short by 0.140 AUC, 5 of 5 econ |
| X3-multitask-unl | pre | NY | cmt_logit2 | 0.522 [0.48,0.57] | 0.538 [0.48,0.60] | - | 0.533 | 0.534 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +10 | ASIA | cfree15 | 0.537 [0.49,0.58] | 0.538 [0.47,0.60] | - | 0.536 | 0.532 | N | - | - | - | - |  | short by 0.122 AUC, 5 of 5 econ |
| X26-condranker-X45u | +10 | LONDON | d_gbt3 | 0.526 [0.49,0.57] | 0.538 [0.48,0.60] | - | 0.530 | 0.524 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +30 | ASIA | d_xe | 0.529 [0.49,0.57] | 0.537 [0.47,0.60] | - | 0.524 | 0.537 | N | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X27-etbag-X45u | +30 | ASIA | d_etbag | 0.536 [0.50,0.58] | 0.537 [0.48,0.59] | - | 0.533 | 0.527 | N | - | - | - | - | stack | short by 0.123 AUC, 5 of 5 econ |
| X4-density-unl | pre | ASIA | X4u:rf | 0.547 [0.51,0.59] | 0.536 [0.48,0.59] | - | 0.528 | 0.537 | ok | - | - | - | - | stack | short by 0.124 AUC, 5 of 5 econ |
| X4-density-unl | +30 | NY | X4u:gbt3 | 0.522 [0.48,0.57] | 0.536 [0.47,0.60] | - | 0.536 | 0.528 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +30 | NY | cmt_pair | 0.512 [0.46,0.56] | 0.535 [0.48,0.59] | - | 0.531 | 0.529 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | pre | ASIA | X5u:rf | 0.545 [0.50,0.59] | 0.535 [0.48,0.59] | - | 0.526 | 0.536 | ok | - | - | - | - | stack | short by 0.125 AUC, 5 of 5 econ |
| X26-condranker-X45u | +60 | NY | d_pair | 0.494 [0.45,0.54] | 0.535 [0.47,0.60] | - | 0.536 | 0.529 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +60 | POOLED | X4u:gbt3 | 0.517 [0.49,0.54] | 0.534 [0.50,0.57] | - | 0.530 | 0.527 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +20 | LONDON | cfree15 | 0.522 [0.48,0.57] | 0.534 [0.48,0.59] | - | 0.536 | 0.506 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +15 | POOLED | cfree30 | 0.511 [0.48,0.54] | 0.533 [0.49,0.58] | - | 0.531 | 0.527 | N | - | - | - | - |  | short by 0.147 AUC, 5 of 5 econ |
| X45-stack-unl | +60 | POOLED | X45u:gbt3 | 0.516 [0.49,0.54] | 0.533 [0.50,0.57] | - | 0.528 | 0.524 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +60 | LONDON | emt_rf | 0.526 [0.48,0.57] | 0.533 [0.47,0.60] | - | 0.536 | 0.513 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | pre | ASIA | X45u:rf | 0.545 [0.50,0.59] | 0.533 [0.47,0.59] | - | 0.524 | 0.534 | ok | - | - | - | - | stack | short by 0.127 AUC, 5 of 5 econ |
| X3-multitask-unl | +10 | LONDON | cmt_pair | 0.506 [0.46,0.55] | 0.532 [0.46,0.60] | - | 0.537 | 0.508 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +15 | ASIA | d_etbag | 0.494 [0.45,0.54] | 0.531 [0.48,0.59] | - | 0.531 | 0.528 | N | - | - | - | - | stack | short by 0.129 AUC, 5 of 5 econ |
| X1-condranker-unl | +60 | POOLED | cc_xe | 0.513 [0.49,0.54] | 0.531 [0.50,0.57] | - | 0.531 | 0.528 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +10 | ASIA | cmt_pair | 0.537 [0.49,0.58] | 0.530 [0.48,0.58] | - | 0.518 | 0.526 | N | - | - | - | - |  | short by 0.130 AUC, 5 of 5 econ |
| X26-condranker-X45u | +10 | NY | d_xe | 0.513 [0.47,0.55] | 0.530 [0.47,0.59] | - | 0.535 | 0.530 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +5 | NY | cc_xe | 0.521 [0.48,0.56] | 0.530 [0.47,0.59] | - | 0.537 | 0.521 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +30 | LONDON | cfree30 | 0.516 [0.47,0.56] | 0.530 [0.48,0.59] | - | 0.530 | 0.509 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +60 | POOLED | d_xe | 0.505 [0.48,0.53] | 0.529 [0.49,0.57] | - | 0.528 | 0.527 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +60 | NY | X5u:gbt3 | 0.486 [0.44,0.53] | 0.529 [0.46,0.60] | - | 0.523 | 0.525 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +15 | LONDON | cmt_pair | 0.510 [0.47,0.56] | 0.529 [0.46,0.60] | - | 0.534 | 0.506 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +20 | LONDON | cmt_pair | 0.506 [0.46,0.55] | 0.528 [0.45,0.60] | - | 0.533 | 0.505 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | pre | NY | X4u:rf | 0.527 [0.48,0.57] | 0.528 [0.46,0.59] | - | 0.531 | 0.526 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +15 | POOLED | d_etbag | 0.499 [0.47,0.53] | 0.528 [0.49,0.57] | - | 0.526 | 0.517 | N | - | - | - | - | stack | short by 0.152 AUC, 5 of 5 econ |
| X1-condranker-unl | +15 | POOLED | cc_logit2 | 0.521 [0.50,0.54] | 0.528 [0.49,0.56] | - | 0.529 | 0.524 | N | - | - | - | - |  | short by 0.152 AUC, 5 of 5 econ |
| X2-monotone-unl | +15 | LONDON | cfree30 | 0.507 [0.46,0.55] | 0.527 [0.46,0.59] | - | 0.519 | 0.523 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +20 | POOLED | cmt_pair | 0.521 [0.49,0.55] | 0.527 [0.49,0.57] | - | 0.526 | 0.516 | N | - | - | - | - |  | short by 0.153 AUC, 5 of 5 econ |
| X3-multitask-unl | +20 | ASIA | cmt_pair | 0.543 [0.50,0.58] | 0.527 [0.47,0.58] | - | 0.518 | 0.519 | N | - | - | - | - |  | dead (no gain over baseline) |
| X1-condranker-unl | +45 | LONDON | cc_pair | 0.528 [0.48,0.58] | 0.527 [0.46,0.60] | - | 0.529 | 0.521 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +20 | LONDON | X4u:gbt3 | 0.528 [0.49,0.57] | 0.527 [0.47,0.59] | - | 0.532 | 0.505 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +60 | LONDON | cmt_pair | 0.519 [0.48,0.57] | 0.527 [0.46,0.59] | - | 0.531 | 0.508 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +20 | LONDON | d_gbt3 | 0.502 [0.46,0.54] | 0.526 [0.47,0.58] | - | 0.520 | 0.508 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +60 | POOLED | d_etbag | 0.514 [0.49,0.54] | 0.525 [0.49,0.56] | - | 0.528 | 0.514 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +60 | POOLED | X5u:gbt3 | 0.508 [0.48,0.53] | 0.525 [0.49,0.56] | - | 0.523 | 0.516 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +20 | LONDON | X5u:rf | 0.516 [0.48,0.56] | 0.525 [0.47,0.58] | - | 0.528 | 0.500 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +20 | NY | cmt_pair | 0.515 [0.47,0.56] | 0.525 [0.47,0.58] | - | 0.526 | 0.521 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +10 | POOLED | X4u:rf | 0.520 [0.50,0.55] | 0.525 [0.48,0.57] | - | 0.525 | 0.519 | ok | - | - | - | - | stack | short by 0.155 AUC, 5 of 5 econ |
| X3-multitask-unl | +10 | POOLED | cmt_pair | 0.515 [0.49,0.54] | 0.524 [0.49,0.56] | - | 0.524 | 0.513 | N | - | - | - | - |  | short by 0.156 AUC, 5 of 5 econ |
| X28-multitask-X45u | +60 | ASIA | emt_gbt3 | 0.526 [0.48,0.57] | 0.524 [0.46,0.59] | - | 0.509 | 0.504 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +30 | POOLED | cmt_pair | 0.513 [0.49,0.54] | 0.524 [0.48,0.57] | - | 0.520 | 0.511 | N | - | - | - | - |  | promising: short by 0.156 AUC, 5 of 5 econ |
| X3-multitask-unl | +30 | LONDON | cmt_pair | 0.502 [0.46,0.55] | 0.524 [0.45,0.59] | - | 0.530 | 0.502 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +10 | ASIA | X4u:stack | 0.553 [0.52,0.59] | 0.524 [0.46,0.60] | - | 0.517 | 0.517 | ok | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X45-stack-unl | pre | NY | X45u:rf | 0.518 [0.47,0.57] | 0.524 [0.46,0.59] | - | 0.524 | 0.522 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +5 | ASIA | d_pair | 0.523 [0.49,0.56] | 0.524 [0.47,0.58] | - | 0.512 | 0.521 | N | - | - | - | - | stack | short by 0.136 AUC, 5 of 5 econ |
| X45-stack-unl | +20 | ASIA | X45u:stack | 0.527 [0.49,0.56] | 0.523 [0.46,0.59] | - | 0.512 | 0.522 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X2-monotone-unl | pre | POOLED | cmono30 | 0.519 [0.50,0.54] | 0.523 [0.49,0.55] | - | 0.522 | 0.514 | N | - | - | - | - |  | short by 0.157 AUC, 5 of 5 econ |
| X1-condranker-unl | +5 | ASIA | cc_xe | 0.529 [0.49,0.57] | 0.522 [0.47,0.58] | - | 0.518 | 0.521 | N | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| X5-pathstate-unl | +60 | ASIA | X5u:logit2 | 0.513 [0.47,0.56] | 0.522 [0.46,0.59] | - | 0.518 | 0.519 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +15 | POOLED | cmt_pair | 0.518 [0.49,0.55] | 0.522 [0.48,0.57] | - | 0.522 | 0.512 | N | - | - | - | - |  | short by 0.158 AUC, 5 of 5 econ |
| X3-multitask-unl | +5 | ASIA | cmt_pair | 0.525 [0.48,0.56] | 0.522 [0.48,0.57] | - | 0.514 | 0.522 | N | - | - | - | - |  | short by 0.138 AUC, 5 of 5 econ |
| X5-pathstate-unl | +45 | POOLED | X5u:rf | 0.513 [0.49,0.54] | 0.522 [0.49,0.56] | - | 0.521 | 0.510 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +45 | POOLED | X45u:rf | 0.506 [0.48,0.53] | 0.522 [0.49,0.56] | - | 0.519 | 0.512 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | pre | ASIA | cc_rf | 0.536 [0.49,0.58] | 0.522 [0.46,0.58] | - | 0.515 | 0.524 | N | - | - | - | - |  | dead (no gain over baseline) |
| X5-pathstate-unl | +10 | LONDON | X5u:rf | 0.520 [0.48,0.57] | 0.522 [0.45,0.59] | - | 0.520 | 0.506 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +20 | LONDON | X45u:gbt3 | 0.526 [0.48,0.57] | 0.522 [0.46,0.59] | - | 0.518 | 0.496 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +60 | ASIA | X4u:logit2 | 0.531 [0.48,0.57] | 0.521 [0.46,0.58] | - | 0.518 | 0.519 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +60 | ASIA | X45u:logit2 | 0.531 [0.48,0.57] | 0.521 [0.46,0.58] | - | 0.518 | 0.519 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +20 | POOLED | d_etbag | 0.504 [0.48,0.53] | 0.521 [0.49,0.55] | - | 0.516 | 0.508 | N | - | - | - | - | stack | short by 0.159 AUC, 5 of 5 econ |
| X1-condranker-unl | +45 | POOLED | cc_xe | 0.506 [0.48,0.53] | 0.521 [0.48,0.56] | - | 0.521 | 0.520 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +10 | POOLED | X45u:rf | 0.516 [0.49,0.54] | 0.520 [0.48,0.56] | - | 0.520 | 0.515 | ok | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X27-etbag-X45u | +10 | POOLED | d_etbag | 0.525 [0.50,0.55] | 0.520 [0.48,0.56] | - | 0.520 | 0.513 | N | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X5-pathstate-unl | +10 | POOLED | X5u:rf | 0.520 [0.49,0.55] | 0.520 [0.48,0.56] | - | 0.521 | 0.513 | ok | - | - | - | - | stack | short by 0.160 AUC, 5 of 5 econ |
| X1-condranker-unl | +60 | NY | cc_logit2 | 0.473 [0.43,0.51] | 0.520 [0.46,0.58] | - | 0.520 | 0.510 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +5 | ASIA | X4u:gbt3 | 0.531 [0.49,0.57] | 0.520 [0.46,0.58] | - | 0.527 | 0.520 | ok | - | - | - | - | stack | short by 0.140 AUC, 5 of 5 econ |
| X5-pathstate-unl | pre | NY | X5u:rf | 0.519 [0.47,0.56] | 0.520 [0.46,0.58] | - | 0.524 | 0.519 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +45 | ASIA | cmt_pair | 0.534 [0.49,0.58] | 0.520 [0.46,0.58] | - | 0.509 | 0.508 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +20 | POOLED | cc_stack | 0.507 [0.48,0.54] | 0.520 [0.48,0.56] | - | 0.515 | 0.511 | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X26-condranker-X45u | +5 | LONDON | d_pair | 0.500 [0.45,0.55] | 0.520 [0.44,0.60] | - | 0.515 | 0.498 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +45 | LONDON | cmt_pair | 0.509 [0.46,0.56] | 0.519 [0.44,0.59] | - | 0.524 | 0.499 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | pre | POOLED | cmt_pair | 0.510 [0.48,0.54] | 0.519 [0.48,0.56] | - | 0.518 | 0.511 | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| X28-multitask-X45u | +20 | ASIA | emt_gbt3 | 0.531 [0.49,0.57] | 0.519 [0.46,0.58] | - | 0.505 | 0.509 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +45 | POOLED | X4u:rf | 0.509 [0.48,0.53] | 0.519 [0.48,0.56] | - | 0.518 | 0.509 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +45 | ASIA | emt_gbt3 | 0.524 [0.48,0.57] | 0.519 [0.47,0.57] | - | 0.501 | 0.505 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +5 | POOLED | cmono15 | 0.508 [0.48,0.53] | 0.519 [0.48,0.56] | - | 0.516 | 0.514 | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| X5-pathstate-unl | +30 | ASIA | X5u:logit2 | 0.535 [0.49,0.58] | 0.519 [0.46,0.58] | - | 0.511 | 0.520 | ok | - | - | - | - | stack | short by 0.141 AUC, 5 of 5 econ |
| X3-multitask-unl | +5 | LONDON | cmt_pair | 0.503 [0.46,0.55] | 0.519 [0.45,0.59] | - | 0.526 | 0.498 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +5 | POOLED | cmt_pair | 0.509 [0.48,0.54] | 0.519 [0.48,0.56] | - | 0.519 | 0.510 | N | - | - | - | - |  | short by 0.161 AUC, 5 of 5 econ |
| X3-multitask-unl | pre | LONDON | cmt_pair | 0.499 [0.46,0.55] | 0.518 [0.45,0.59] | - | 0.525 | 0.497 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +15 | ASIA | cc_pair | 0.526 [0.48,0.57] | 0.518 [0.45,0.59] | - | 0.519 | 0.515 | N | - | - | - | - |  | short by 0.142 AUC, 5 of 5 econ |
| X4-density-unl | +60 | NY | X4u:gbt3 | 0.489 [0.45,0.53] | 0.518 [0.45,0.59] | - | 0.510 | 0.515 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +20 | NY | cfree15 | 0.516 [0.47,0.56] | 0.518 [0.47,0.58] | - | 0.512 | 0.511 | ok | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +30 | POOLED | cmono30 | 0.505 [0.48,0.53] | 0.518 [0.48,0.55] | - | 0.511 | 0.503 | N | - | - | - | - |  | promising: short by 0.162 AUC, 5 of 5 econ |
| X1-condranker-unl | +15 | LONDON | cc_pair | 0.512 [0.47,0.55] | 0.518 [0.46,0.58] | - | 0.512 | 0.501 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +30 | ASIA | emt_gbt3 | 0.524 [0.48,0.57] | 0.517 [0.46,0.57] | - | 0.505 | 0.506 | N | - | - | - | - | stack | short by 0.143 AUC, 5 of 5 econ |
| X27-etbag-X45u | +20 | ASIA | d_etbag | 0.506 [0.47,0.55] | 0.517 [0.47,0.57] | - | 0.504 | 0.516 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X3-multitask-unl | +60 | POOLED | cmt_pair | 0.520 [0.49,0.55] | 0.517 [0.48,0.56] | - | 0.517 | 0.501 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | pre | NY | d_xe | 0.542 [0.49,0.58] | 0.517 [0.45,0.58] | - | 0.521 | 0.516 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +10 | LONDON | cc_gbt3 | 0.531 [0.49,0.57] | 0.517 [0.45,0.58] | - | 0.513 | 0.501 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +10 | ASIA | d_gbt3 | 0.528 [0.48,0.57] | 0.517 [0.45,0.58] | - | 0.513 | 0.513 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X3-multitask-unl | +15 | ASIA | cmt_pair | 0.533 [0.49,0.58] | 0.516 [0.46,0.57] | - | 0.508 | 0.510 | N | - | - | - | - |  | short by 0.144 AUC, 5 of 5 econ |
| X28-multitask-X45u | +10 | ASIA | emt_gbt3 | 0.536 [0.49,0.58] | 0.515 [0.46,0.57] | - | 0.500 | 0.508 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X3-multitask-unl | pre | ASIA | cmt_pair | 0.523 [0.48,0.56] | 0.515 [0.47,0.57] | - | 0.506 | 0.514 | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-etbag-X45u | pre | ASIA | d_etbag | 0.538 [0.49,0.58] | 0.515 [0.45,0.58] | - | 0.505 | 0.517 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X27-etbag-X45u | +45 | ASIA | d_etbag | 0.509 [0.46,0.55] | 0.515 [0.45,0.58] | - | 0.504 | 0.504 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +10 | POOLED | d_gbt3 | 0.516 [0.50,0.54] | 0.515 [0.48,0.55] | - | 0.512 | 0.509 | N | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X2-monotone-unl | pre | NY | cmono30 | 0.514 [0.47,0.56] | 0.514 [0.45,0.58] | - | 0.519 | 0.511 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +5 | ASIA | emt_gbt3 | 0.535 [0.49,0.58] | 0.514 [0.46,0.57] | - | 0.499 | 0.512 | N | - | - | - | - | stack | short by 0.146 AUC, 5 of 5 econ |
| X2-monotone-unl | +20 | POOLED | cfree15 | 0.511 [0.49,0.54] | 0.514 [0.48,0.55] | - | 0.513 | 0.500 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X26-condranker-X45u | pre | POOLED | d_xe | 0.523 [0.50,0.55] | 0.514 [0.47,0.55] | - | 0.513 | 0.513 | N | - | - | - | - | stack | short by 0.166 AUC, 5 of 5 econ |
| X3-multitask-unl | +45 | POOLED | cmt_pair | 0.514 [0.49,0.54] | 0.514 [0.47,0.56] | - | 0.512 | 0.501 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +10 | ASIA | d_etbag | 0.549 [0.51,0.60] | 0.514 [0.44,0.59] | - | 0.511 | 0.513 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X3-multitask-unl | +30 | ASIA | cmt_pair | 0.528 [0.49,0.57] | 0.514 [0.46,0.57] | - | 0.504 | 0.504 | N | - | - | - | - |  | short by 0.146 AUC, 5 of 5 econ |
| X3-multitask-unl | +5 | NY | cmt_pair | 0.500 [0.45,0.55] | 0.514 [0.45,0.58] | - | 0.519 | 0.509 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +20 | POOLED | X5u:rf | 0.505 [0.48,0.53] | 0.514 [0.48,0.55] | - | 0.507 | 0.503 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X5-pathstate-unl | +5 | POOLED | X5u:rf | 0.511 [0.49,0.54] | 0.513 [0.47,0.55] | - | 0.511 | 0.502 | ok | - | - | - | - | stack | short by 0.167 AUC, 5 of 5 econ |
| X2-monotone-unl | +45 | POOLED | cmono30 | 0.510 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.511 | 0.499 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +45 | POOLED | d_gbt3 | 0.513 [0.49,0.54] | 0.513 [0.48,0.55] | - | 0.510 | 0.502 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +60 | NY | X45u:gbt3 | 0.486 [0.44,0.53] | 0.513 [0.44,0.59] | - | 0.505 | 0.506 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | pre | NY | d_etbag | 0.508 [0.47,0.55] | 0.513 [0.45,0.57] | - | 0.518 | 0.510 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +20 | ASIA | X5u:stack | 0.532 [0.50,0.57] | 0.513 [0.45,0.57] | - | 0.500 | 0.515 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X28-multitask-X45u | pre | ASIA | emt_gbt3 | 0.528 [0.49,0.57] | 0.512 [0.46,0.57] | - | 0.496 | 0.510 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X5-pathstate-unl | +5 | NY | X5u:rf | 0.504 [0.47,0.54] | 0.512 [0.46,0.57] | - | 0.522 | 0.503 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +30 | NY | X45u:gbt3 | 0.507 [0.47,0.56] | 0.512 [0.45,0.58] | - | 0.514 | 0.501 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +15 | ASIA | emt_gbt3 | 0.527 [0.49,0.57] | 0.512 [0.45,0.57] | - | 0.500 | 0.503 | N | - | - | - | - | stack | short by 0.148 AUC, 5 of 5 econ |
| X5-pathstate-unl | +10 | ASIA | X5u:stack | 0.547 [0.51,0.59] | 0.512 [0.45,0.58] | - | 0.505 | 0.503 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X1-condranker-unl | +20 | ASIA | cc_stack | 0.505 [0.46,0.55] | 0.512 [0.46,0.57] | - | 0.502 | 0.511 | N | - | - | - | - |  | dead (no gain over baseline) |
| X4-density-unl | pre | POOLED | X4u:rf | 0.517 [0.49,0.54] | 0.511 [0.47,0.55] | - | 0.510 | 0.511 | ok | - | - | - | - | stack | short by 0.169 AUC, 5 of 5 econ |
| X4-density-unl | +10 | NY | X4u:rf | 0.519 [0.48,0.56] | 0.511 [0.45,0.57] | - | 0.517 | 0.511 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +5 | POOLED | cc_lam | 0.507 [0.48,0.53] | 0.511 [0.47,0.55] | - | 0.508 | 0.503 | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| X1-condranker-unl | +10 | POOLED | cc_rf | 0.517 [0.49,0.54] | 0.511 [0.47,0.55] | - | 0.510 | 0.506 | N | - | - | - | - |  | short by 0.169 AUC, 5 of 5 econ |
| X3-multitask-unl | +10 | NY | cmt_pair | 0.502 [0.46,0.55] | 0.511 [0.45,0.58] | - | 0.521 | 0.506 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +20 | POOLED | d_gbt3 | 0.503 [0.48,0.53] | 0.510 [0.48,0.55] | - | 0.504 | 0.501 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X5-pathstate-unl | +15 | NY | X5u:logit2 | 0.520 [0.48,0.57] | 0.510 [0.44,0.58] | - | 0.515 | 0.500 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | pre | POOLED | X5u:rf | 0.513 [0.49,0.54] | 0.510 [0.47,0.55] | - | 0.508 | 0.510 | ok | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X2-monotone-unl | +10 | NY | cfree30 | 0.517 [0.48,0.56] | 0.510 [0.44,0.58] | - | 0.512 | 0.507 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +30 | NY | X5u:rf | 0.507 [0.46,0.55] | 0.510 [0.44,0.58] | - | 0.507 | 0.500 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +5 | POOLED | d_pair | 0.509 [0.48,0.54] | 0.510 [0.47,0.55] | - | 0.504 | 0.501 | N | - | - | - | - | stack | short by 0.170 AUC, 5 of 5 econ |
| X28-multitask-X45u | pre | NY | emt_rf | 0.521 [0.48,0.57] | 0.509 [0.44,0.57] | - | 0.503 | 0.509 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | pre | POOLED | X45u:rf | 0.513 [0.49,0.54] | 0.508 [0.47,0.55] | - | 0.507 | 0.507 | ok | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X45-stack-unl | +5 | POOLED | X45u:rf | 0.509 [0.49,0.54] | 0.508 [0.47,0.55] | - | 0.507 | 0.497 | ok | - | - | - | - | stack | short by 0.172 AUC, 5 of 5 econ |
| X1-condranker-unl | +10 | NY | cc_rf | 0.516 [0.48,0.56] | 0.508 [0.44,0.58] | - | 0.510 | 0.506 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +45 | ASIA | cmono30 | 0.533 [0.49,0.58] | 0.508 [0.45,0.58] | - | 0.508 | 0.496 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | pre | POOLED | d_etbag | 0.512 [0.49,0.54] | 0.507 [0.47,0.54] | - | 0.505 | 0.505 | N | - | - | - | - | stack | short by 0.173 AUC, 5 of 5 econ |
| X27-etbag-X45u | +15 | NY | d_etbag | 0.500 [0.46,0.54] | 0.507 [0.44,0.58] | - | 0.510 | 0.498 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +45 | NY | X5u:rf | 0.494 [0.45,0.53] | 0.506 [0.45,0.57] | - | 0.502 | 0.501 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +10 | ASIA | X45u:stack | 0.541 [0.51,0.58] | 0.506 [0.44,0.58] | - | 0.498 | 0.500 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +5 | LONDON | X4u:stack | 0.517 [0.47,0.57] | 0.506 [0.44,0.56] | - | 0.501 | 0.496 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +60 | LONDON | d_etbag | 0.520 [0.47,0.57] | 0.506 [0.43,0.57] | - | 0.512 | 0.497 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +60 | LONDON | X5u:gbt3 | 0.522 [0.48,0.57] | 0.506 [0.44,0.56] | - | 0.498 | 0.493 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +45 | NY | X4u:rf | 0.489 [0.45,0.53] | 0.506 [0.44,0.57] | - | 0.506 | 0.501 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +5 | NY | X45u:rf | 0.499 [0.46,0.54] | 0.506 [0.45,0.55] | - | 0.517 | 0.496 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +10 | NY | X5u:rf | 0.515 [0.47,0.56] | 0.505 [0.44,0.57] | - | 0.509 | 0.505 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +15 | NY | X45u:logit2 | 0.518 [0.48,0.57] | 0.504 [0.43,0.57] | - | 0.509 | 0.497 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +5 | LONDON | d_etbag | 0.487 [0.44,0.53] | 0.504 [0.44,0.58] | - | 0.500 | 0.476 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +10 | NY | d_etbag | 0.510 [0.47,0.55] | 0.504 [0.44,0.56] | - | 0.510 | 0.501 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +5 | POOLED | X4u:rf | 0.509 [0.49,0.54] | 0.504 [0.47,0.54] | - | 0.500 | 0.494 | ok | - | - | - | - | stack | short by 0.176 AUC, 5 of 5 econ |
| X2-monotone-unl | +15 | NY | cmono30 | 0.506 [0.46,0.55] | 0.504 [0.44,0.57] | - | 0.507 | 0.496 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +45 | NY | cmt_pair | 0.503 [0.46,0.55] | 0.504 [0.44,0.57] | - | 0.506 | 0.495 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +60 | LONDON | d_gbt3 | 0.520 [0.47,0.56] | 0.504 [0.44,0.56] | - | 0.496 | 0.490 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +10 | NY | X45u:rf | 0.512 [0.47,0.56] | 0.503 [0.44,0.57] | - | 0.507 | 0.503 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +20 | ASIA | X4u:stack | 0.541 [0.50,0.58] | 0.503 [0.44,0.56] | - | 0.487 | 0.509 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +5 | NY | X4u:rf | 0.498 [0.46,0.54] | 0.503 [0.44,0.56] | - | 0.506 | 0.495 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +20 | POOLED | X45u:stack | 0.509 [0.49,0.54] | 0.502 [0.46,0.54] | - | 0.500 | 0.498 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X27-etbag-X45u | pre | LONDON | d_etbag | 0.489 [0.44,0.53] | 0.502 [0.44,0.56] | - | 0.494 | 0.493 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +20 | LONDON | emt_gbt3 | 0.506 [0.46,0.56] | 0.502 [0.43,0.57] | - | 0.506 | 0.483 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +15 | NY | cc_logit2 | 0.522 [0.48,0.56] | 0.501 [0.43,0.57] | - | 0.500 | 0.491 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +45 | LONDON | cfree15 | 0.500 [0.45,0.55] | 0.501 [0.43,0.57] | - | 0.495 | 0.473 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +30 | POOLED | d_etbag | 0.492 [0.47,0.52] | 0.500 [0.47,0.53] | - | 0.494 | 0.485 | N | - | - | - | - | stack | short by 0.180 AUC, 5 of 5 econ |
| X28-multitask-X45u | pre | LONDON | emt_gbt3 | 0.502 [0.46,0.56] | 0.500 [0.43,0.57] | - | 0.499 | 0.484 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +60 | LONDON | cc_xe | 0.531 [0.48,0.58] | 0.500 [0.44,0.56] | - | 0.495 | 0.501 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +45 | POOLED | d_etbag | 0.497 [0.47,0.52] | 0.500 [0.47,0.54] | - | 0.497 | 0.488 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +30 | POOLED | cc_pair | 0.501 [0.48,0.53] | 0.500 [0.46,0.54] | - | 0.494 | 0.485 | N | - | - | - | - |  | short by 0.180 AUC, 5 of 5 econ |
| X1-condranker-unl | +30 | ASIA | cc_pair | 0.536 [0.49,0.58] | 0.500 [0.44,0.56] | - | 0.487 | 0.488 | N | - | - | - | - |  | short by 0.160 AUC, 5 of 5 econ |
| X26-condranker-X45u | +20 | ASIA | d_gbt3 | 0.513 [0.47,0.55] | 0.500 [0.45,0.56] | - | 0.485 | 0.497 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-multitask-X45u | +15 | LONDON | emt_gbt3 | 0.505 [0.46,0.56] | 0.500 [0.43,0.57] | - | 0.502 | 0.482 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +45 | LONDON | X5u:rf | 0.513 [0.46,0.56] | 0.500 [0.43,0.57] | - | 0.494 | 0.480 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +20 | NY | emt_rf | 0.512 [0.47,0.55] | 0.500 [0.44,0.55] | - | 0.497 | 0.500 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +60 | NY | cmt_pair | 0.512 [0.47,0.56] | 0.499 [0.43,0.57] | - | 0.495 | 0.489 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +20 | NY | cc_logit2 | 0.513 [0.47,0.56] | 0.499 [0.43,0.57] | - | 0.511 | 0.497 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +20 | NY | d_pair | 0.510 [0.47,0.55] | 0.498 [0.44,0.56] | - | 0.499 | 0.495 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +20 | NY | d_etbag | 0.507 [0.47,0.55] | 0.498 [0.44,0.56] | - | 0.495 | 0.489 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +15 | POOLED | emt_gbt3 | 0.512 [0.49,0.54] | 0.498 [0.46,0.54] | - | 0.496 | 0.488 | N | - | - | - | - | stack | short by 0.182 AUC, 5 of 5 econ |
| X26-condranker-X45u | pre | LONDON | d_pair | 0.526 [0.48,0.57] | 0.498 [0.44,0.56] | - | 0.493 | 0.500 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +5 | NY | cfree30 | 0.495 [0.46,0.54] | 0.497 [0.44,0.56] | - | 0.495 | 0.491 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +45 | NY | d_etbag | 0.479 [0.44,0.52] | 0.497 [0.44,0.56] | - | 0.497 | 0.491 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +20 | POOLED | emt_gbt3 | 0.508 [0.48,0.53] | 0.496 [0.46,0.53] | - | 0.493 | 0.486 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X2-monotone-unl | +10 | POOLED | cfree15 | 0.506 [0.48,0.53] | 0.496 [0.46,0.54] | - | 0.497 | 0.491 | N | - | - | - | - |  | short by 0.184 AUC, 5 of 5 econ |
| X1-condranker-unl | +30 | NY | cc_lam | 0.490 [0.45,0.53] | 0.495 [0.43,0.57] | - | 0.488 | 0.482 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +30 | NY | emt_rf | 0.512 [0.47,0.56] | 0.495 [0.44,0.56] | - | 0.496 | 0.497 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +5 | NY | d_pair | 0.504 [0.46,0.54] | 0.495 [0.44,0.55] | - | 0.498 | 0.490 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +15 | ASIA | X45u:stack | 0.522 [0.48,0.56] | 0.495 [0.43,0.56] | - | 0.474 | 0.487 | ok | - | - | - | - | stack | short by 0.165 AUC, 5 of 5 econ |
| X28-multitask-X45u | +10 | LONDON | emt_gbt3 | 0.500 [0.45,0.55] | 0.495 [0.43,0.56] | - | 0.499 | 0.477 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +60 | NY | d_etbag | 0.474 [0.44,0.52] | 0.495 [0.43,0.56] | - | 0.493 | 0.484 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +15 | NY | X4u:logit2 | 0.510 [0.47,0.56] | 0.495 [0.42,0.56] | - | 0.498 | 0.487 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +5 | LONDON | emt_gbt3 | 0.498 [0.45,0.55] | 0.495 [0.42,0.56] | - | 0.498 | 0.478 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +30 | ASIA | X45u:stack | 0.544 [0.51,0.58] | 0.494 [0.43,0.55] | - | 0.501 | 0.486 | ok | - | - | - | - | stack | WF-only (dead) |
| X1-condranker-unl | +10 | ASIA | cc_rf | 0.515 [0.47,0.56] | 0.494 [0.43,0.57] | - | 0.492 | 0.488 | N | - | - | - | - |  | dead (no gain over baseline) |
| X2-monotone-unl | pre | LONDON | cmono15 | 0.499 [0.45,0.54] | 0.493 [0.43,0.56] | - | 0.492 | 0.488 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +5 | POOLED | d_etbag | 0.501 [0.47,0.53] | 0.493 [0.45,0.53] | - | 0.490 | 0.482 | N | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X28-multitask-X45u | +5 | NY | emt_rf | 0.508 [0.47,0.55] | 0.493 [0.43,0.56] | - | 0.494 | 0.494 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +30 | POOLED | d_gbt3 | 0.499 [0.48,0.52] | 0.493 [0.46,0.53] | - | 0.492 | 0.483 | N | - | - | - | - | stack | short by 0.187 AUC, 5 of 5 econ |
| X28-multitask-X45u | +15 | NY | emt_rf | 0.515 [0.48,0.56] | 0.493 [0.43,0.55] | - | 0.493 | 0.493 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +10 | POOLED | emt_gbt3 | 0.509 [0.48,0.53] | 0.492 [0.46,0.53] | - | 0.491 | 0.483 | N | - | - | - | - | stack | short by 0.188 AUC, 5 of 5 econ |
| X26-condranker-X45u | +45 | NY | d_gbt3 | 0.494 [0.45,0.54] | 0.492 [0.43,0.56] | - | 0.488 | 0.487 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | pre | POOLED | emt_gbt3 | 0.510 [0.48,0.54] | 0.491 [0.45,0.53] | - | 0.488 | 0.484 | N | - | - | - | - | stack | short by 0.189 AUC, 5 of 5 econ |
| X2-monotone-unl | +5 | ASIA | cfree30 | 0.519 [0.48,0.56] | 0.490 [0.44,0.55] | - | 0.484 | 0.492 | N | - | - | - | - |  | dead (no gain over baseline) |
| X27-etbag-X45u | +5 | NY | d_etbag | 0.492 [0.46,0.54] | 0.490 [0.43,0.55] | - | 0.495 | 0.481 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +5 | ASIA | d_etbag | 0.521 [0.48,0.56] | 0.490 [0.44,0.55] | - | 0.475 | 0.489 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X28-multitask-X45u | +30 | POOLED | emt_gbt3 | 0.510 [0.48,0.53] | 0.490 [0.45,0.53] | - | 0.486 | 0.480 | N | - | - | - | - | stack | short by 0.190 AUC, 5 of 5 econ |
| X28-multitask-X45u | +45 | POOLED | emt_gbt3 | 0.506 [0.48,0.53] | 0.490 [0.45,0.53] | - | 0.484 | 0.479 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +20 | POOLED | X4u:stack | 0.513 [0.49,0.54] | 0.489 [0.45,0.53] | - | 0.485 | 0.485 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X28-multitask-X45u | +60 | NY | emt_mlp | 0.487 [0.45,0.53] | 0.489 [0.44,0.54] | - | 0.486 | 0.486 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +5 | POOLED | emt_gbt3 | 0.509 [0.48,0.54] | 0.488 [0.45,0.53] | - | 0.487 | 0.481 | N | - | - | - | - | stack | dead (no gain over baseline) |
| X45-stack-unl | +45 | NY | X45u:gbt3 | 0.486 [0.44,0.53] | 0.488 [0.43,0.55] | - | 0.481 | 0.487 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +60 | POOLED | emt_gbt3 | 0.503 [0.48,0.53] | 0.488 [0.45,0.53] | - | 0.484 | 0.477 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +30 | NY | d_gbt3 | 0.500 [0.46,0.54] | 0.488 [0.42,0.55] | - | 0.484 | 0.481 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X3-multitask-unl | +15 | NY | cmt_gbt3 | 0.498 [0.46,0.54] | 0.486 [0.43,0.54] | - | 0.491 | 0.482 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +10 | LONDON | cfree15 | 0.496 [0.45,0.54] | 0.485 [0.42,0.55] | - | 0.491 | 0.477 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +45 | NY | emt_mlp | 0.499 [0.46,0.54] | 0.484 [0.43,0.55] | - | 0.488 | 0.485 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X26-condranker-X45u | +30 | LONDON | d_gbt3 | 0.478 [0.43,0.52] | 0.484 [0.43,0.54] | - | 0.489 | 0.468 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +45 | LONDON | emt_gbt3 | 0.501 [0.45,0.55] | 0.484 [0.42,0.56] | - | 0.490 | 0.471 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X28-multitask-X45u | +10 | NY | emt_rf | 0.513 [0.48,0.56] | 0.484 [0.42,0.55] | - | 0.487 | 0.484 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | pre | NY | cc_xe | 0.515 [0.46,0.56] | 0.483 [0.41,0.55] | - | 0.491 | 0.486 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +30 | NY | cmono30 | 0.478 [0.44,0.52] | 0.483 [0.42,0.54] | - | 0.478 | 0.469 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +20 | ASIA | cmono15 | 0.488 [0.44,0.53] | 0.483 [0.43,0.54] | - | 0.474 | 0.476 | ok | - | - | - | - |  | dead (no gain over baseline) |
| X28-multitask-X45u | +30 | LONDON | emt_gbt3 | 0.502 [0.45,0.55] | 0.481 [0.41,0.55] | - | 0.486 | 0.465 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +30 | ASIA | X4u:stack | 0.540 [0.51,0.58] | 0.481 [0.42,0.54] | - | 0.479 | 0.482 | ok | - | - | - | - | stack | WF-only (dead) |
| X1-condranker-unl | pre | LONDON | cc_gbt3 | 0.496 [0.45,0.54] | 0.480 [0.42,0.55] | - | 0.484 | 0.481 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +10 | LONDON | X4u:stack | 0.496 [0.45,0.54] | 0.479 [0.41,0.54] | - | 0.470 | 0.466 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +30 | LONDON | cc_logit2 | 0.474 [0.43,0.52] | 0.479 [0.42,0.53] | - | 0.477 | 0.474 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | +45 | NY | cc_rf | 0.475 [0.43,0.52] | 0.479 [0.41,0.54] | - | 0.479 | 0.473 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X1-condranker-unl | pre | POOLED | cc_stack | 0.505 [0.48,0.53] | 0.478 [0.44,0.51] | - | 0.473 | 0.476 | N | - | - | - | - |  | dead (no gain over baseline) |
| X2-monotone-unl | +60 | POOLED | cfree15 | 0.503 [0.48,0.53] | 0.476 [0.44,0.51] | - | 0.474 | 0.463 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +15 | POOLED | X45u:stack | 0.509 [0.48,0.54] | 0.475 [0.43,0.52] | - | 0.464 | 0.464 | ok | - | - | - | - | stack | short by 0.205 AUC, 5 of 5 econ |
| X27-etbag-X45u | +30 | NY | d_etbag | 0.475 [0.43,0.52] | 0.474 [0.40,0.55] | - | 0.475 | 0.462 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +60 | ASIA | cfree30 | 0.500 [0.45,0.54] | 0.474 [0.41,0.54] | - | 0.473 | 0.463 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +20 | NY | X4u:stack | 0.520 [0.48,0.57] | 0.474 [0.41,0.54] | - | 0.477 | 0.469 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +20 | NY | X45u:stack | 0.510 [0.46,0.55] | 0.472 [0.41,0.54] | - | 0.472 | 0.469 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +10 | LONDON | X45u:stack | 0.491 [0.45,0.54] | 0.470 [0.40,0.54] | - | 0.460 | 0.456 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | pre | LONDON | X5u:stack | 0.489 [0.45,0.54] | 0.469 [0.41,0.53] | - | 0.464 | 0.451 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +60 | LONDON | cfree15 | 0.520 [0.48,0.57] | 0.468 [0.40,0.53] | - | 0.465 | 0.447 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +5 | LONDON | X5u:stack | 0.495 [0.45,0.54] | 0.467 [0.41,0.53] | - | 0.465 | 0.459 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +30 | LONDON | d_etbag | 0.443 [0.40,0.49] | 0.466 [0.40,0.53] | - | 0.459 | 0.447 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +15 | POOLED | X5u:stack | 0.506 [0.48,0.53] | 0.466 [0.42,0.51] | - | 0.457 | 0.455 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X26-condranker-X45u | +45 | LONDON | d_pair | 0.489 [0.44,0.54] | 0.465 [0.40,0.52] | - | 0.454 | 0.451 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +15 | POOLED | X4u:stack | 0.507 [0.48,0.53] | 0.465 [0.42,0.51] | - | 0.459 | 0.453 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X45-stack-unl | +45 | LONDON | X45u:stack | 0.504 [0.46,0.55] | 0.464 [0.40,0.53] | - | 0.451 | 0.444 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +15 | LONDON | X45u:stack | 0.505 [0.46,0.55] | 0.464 [0.41,0.53] | - | 0.444 | 0.445 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X2-monotone-unl | +60 | NY | cfree15 | 0.478 [0.44,0.52] | 0.463 [0.39,0.53] | - | 0.460 | 0.458 | N | - | - | - | - |  | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +5 | ASIA | X45u:stack | 0.514 [0.48,0.55] | 0.462 [0.40,0.52] | - | 0.458 | 0.462 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +30 | LONDON | X4u:stack | 0.482 [0.44,0.53] | 0.462 [0.40,0.52] | - | 0.462 | 0.457 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +20 | NY | X5u:stack | 0.503 [0.46,0.55] | 0.461 [0.39,0.53] | - | 0.465 | 0.456 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | pre | LONDON | X45u:stack | 0.486 [0.45,0.53] | 0.460 [0.40,0.52] | - | 0.454 | 0.442 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +15 | LONDON | X4u:stack | 0.505 [0.46,0.55] | 0.457 [0.40,0.52] | - | 0.444 | 0.436 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +5 | LONDON | X45u:stack | 0.495 [0.45,0.54] | 0.456 [0.39,0.52] | - | 0.444 | 0.448 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +30 | LONDON | X5u:stack | 0.503 [0.46,0.55] | 0.456 [0.40,0.52] | - | 0.469 | 0.451 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +30 | LONDON | X45u:stack | 0.495 [0.45,0.54] | 0.456 [0.40,0.51] | - | 0.456 | 0.448 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +15 | LONDON | X5u:stack | 0.509 [0.46,0.55] | 0.455 [0.39,0.52] | - | 0.434 | 0.432 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X27-etbag-X45u | +45 | LONDON | d_etbag | 0.488 [0.43,0.54] | 0.454 [0.38,0.52] | - | 0.446 | 0.434 | N | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +5 | ASIA | X5u:stack | 0.510 [0.47,0.55] | 0.451 [0.39,0.51] | - | 0.441 | 0.451 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X45-stack-unl | +30 | POOLED | X45u:stack | 0.498 [0.47,0.52] | 0.449 [0.42,0.49] | - | 0.449 | 0.444 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +45 | LONDON | X4u:stack | 0.496 [0.45,0.54] | 0.448 [0.39,0.51] | - | 0.433 | 0.429 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X4-density-unl | +30 | POOLED | X4u:stack | 0.493 [0.47,0.52] | 0.447 [0.41,0.49] | - | 0.444 | 0.445 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | pre | LONDON | X4u:stack | 0.470 [0.43,0.52] | 0.445 [0.38,0.51] | - | 0.440 | 0.430 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X5-pathstate-unl | +30 | POOLED | X5u:stack | 0.495 [0.47,0.52] | 0.443 [0.41,0.48] | - | 0.443 | 0.440 | ok | - | - | - | - | stack | dead (no gain over baseline) |
| X4-density-unl | +45 | ASIA | X4u:stack | 0.499 [0.45,0.54] | 0.443 [0.38,0.50] | - | 0.435 | 0.428 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |
| X45-stack-unl | +45 | ASIA | X45u:stack | 0.497 [0.45,0.54] | 0.438 [0.37,0.51] | - | 0.431 | 0.422 | ok | - | - | - | - | stack | info (not a FOUND cell: h>30 or LONDON/NY) |

One-sentence notes:
- X1-condranker-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X1-condranker-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X2-monotone-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X26-condranker-X45u 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X27-etbag-X45u 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X28-multitask-X45u 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X3-multitask-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X4-density-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X45-stack-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
- X5-pathstate-unl 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B-unl(X1_round5_B)
