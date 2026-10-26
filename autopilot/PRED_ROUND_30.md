# PRED ROUND 30 - block X1 round 3 - X-conditional-rerun

Best HOLDOUT F-R AUC: +15 POOLED 0.592 [0.55,0.63] | ASIA 0.553 [0.49,0.61] | LONDON 0.600 [0.51,0.68] | NY 0.575 [0.47,0.68]
Best HOLDOUT F-R AUC: +30 POOLED 0.575 [0.53,0.62] | ASIA 0.559 [0.50,0.62] | LONDON 0.639 [0.56,0.71] | NY 0.594 [0.48,0.69]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 9dcabb7084b9cbd42fff66f96a48a559b33b52d2a5757e5275fe7abbd5953565 ; trials added 1500 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X4_round2.parquet', 'l2vast/pred/store/X5_round2.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X45-rescored | +20 | NY | X45stack:stack | 0.559 [0.49,0.62] | 0.651 [0.56,0.74] | - | 0.644 | 0.862 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +45 | LONDON | X4stack:rf | 0.549 [0.50,0.60] | 0.640 [0.55,0.72] | - | 0.640 | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +30 | LONDON | cfree15 | 0.545 [0.49,0.60] | 0.639 [0.56,0.71] | - | 0.605 | 0.647 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +20 | LONDON | X45c:rf | 0.575 [0.53,0.62] | 0.636 [0.57,0.70] | - | 0.614 | 0.624 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +45 | LONDON | X5c:rf | 0.548 [0.49,0.60] | 0.627 [0.56,0.69] | - | 0.618 | 0.613 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +45 | NY | rk_pair | 0.572 [0.51,0.63] | 0.626 [0.53,0.72] | - | 0.628 | 0.657 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +20 | NY | X5stack:stack | 0.547 [0.48,0.61] | 0.624 [0.54,0.71] | - | 0.628 | 0.872 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +60 | NY | X4stack:stack | 0.545 [0.47,0.62] | 0.615 [0.51,0.71] | - | 0.619 | 0.876 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | pre | LONDON | mt_pair | 0.557 [0.50,0.61] | 0.610 [0.55,0.67] | - | 0.587 | 0.656 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +20 | NY | X4stack:stack | 0.534 [0.46,0.61] | 0.606 [0.50,0.71] | - | 0.600 | 0.837 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +60 | LONDON | mt_pair | 0.549 [0.49,0.60] | 0.605 [0.54,0.67] | - | 0.599 | 0.661 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +60 | LONDON | X5c:gbt3 | 0.543 [0.49,0.60] | 0.601 [0.52,0.67] | - | 0.607 | 0.590 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +15 | LONDON | X4c:gbt3 | 0.546 [0.49,0.60] | 0.600 [0.51,0.68] | - | 0.597 | 0.598 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +60 | NY | X45c:gbt3 | 0.577 [0.51,0.65] | 0.598 [0.50,0.69] | - | 0.562 | 0.520 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +45 | LONDON | cfree30 | 0.561 [0.51,0.61] | 0.597 [0.53,0.66] | - | 0.583 | 0.619 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +15 | LONDON | mono15 | 0.552 [0.50,0.61] | 0.596 [0.52,0.67] | - | 0.568 | 0.615 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +45 | LONDON | mt_pair | 0.544 [0.49,0.60] | 0.595 [0.52,0.65] | - | 0.578 | 0.653 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +30 | NY | free15 | 0.548 [0.47,0.62] | 0.594 [0.48,0.69] | - | 0.589 | 0.675 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +15 | POOLED | X4c:logit2 | 0.546 [0.52,0.57] | 0.592 [0.55,0.63] | - | 0.579 | 0.522 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +20 | LONDON | X5c:logit2 | 0.549 [0.50,0.60] | 0.591 [0.51,0.67] | - | 0.554 | 0.625 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +5 | LONDON | mt_pair | 0.553 [0.50,0.61] | 0.590 [0.53,0.65] | - | 0.566 | 0.644 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +45 | LONDON | X4c:rf | 0.539 [0.49,0.59] | 0.589 [0.52,0.66] | - | 0.575 | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +45 | LONDON | X45c:rf | 0.536 [0.48,0.59] | 0.589 [0.51,0.66] | - | 0.578 | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +15 | LONDON | cmono30 | 0.542 [0.49,0.59] | 0.588 [0.51,0.66] | - | 0.556 | 0.610 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +45 | ASIA | mono30 | 0.553 [0.51,0.59] | 0.588 [0.53,0.64] | - | 0.573 | 0.552 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +45 | NY | ctrl_gbt3 | 0.533 [0.46,0.61] | 0.588 [0.47,0.70] | - | 0.595 | 0.798 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +20 | LONDON | cmt_pair | 0.537 [0.48,0.59] | 0.588 [0.51,0.67] | - | 0.592 | 0.567 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +10 | POOLED | cmt_pair | 0.550 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.568 | 0.511 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +20 | NY | cfree30 | 0.566 [0.50,0.63] | 0.587 [0.49,0.69] | - | 0.564 | 0.678 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +60 | LONDON | free30 | 0.518 [0.46,0.57] | 0.587 [0.52,0.65] | - | 0.579 | 0.609 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +15 | LONDON | X4stack:rf | 0.545 [0.50,0.60] | 0.586 [0.51,0.67] | - | 0.556 | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +20 | LONDON | mt_pair | 0.552 [0.49,0.61] | 0.584 [0.51,0.65] | - | 0.555 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +15 | LONDON | mt_pair | 0.554 [0.50,0.61] | 0.583 [0.51,0.65] | - | 0.552 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +45 | POOLED | X5c:rf | 0.562 [0.53,0.59] | 0.583 [0.54,0.62] | - | 0.559 | 0.541 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +30 | NY | cmt_gbt3 | 0.544 [0.47,0.61] | 0.582 [0.47,0.68] | - | 0.563 | 0.613 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +60 | LONDON | cmt_pair | 0.522 [0.47,0.58] | 0.582 [0.51,0.66] | - | 0.596 | 0.570 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +10 | LONDON | mt_pair | 0.551 [0.49,0.60] | 0.582 [0.52,0.65] | - | 0.555 | 0.638 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +15 | LONDON | cmt_pair | 0.537 [0.48,0.59] | 0.582 [0.50,0.66] | - | 0.578 | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +10 | POOLED | X5c:rf | 0.553 [0.52,0.59] | 0.582 [0.53,0.63] | - | 0.554 | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +20 | LONDON | mono30 | 0.534 [0.48,0.58] | 0.582 [0.51,0.66] | - | 0.537 | 0.617 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | pre | POOLED | cmt_pair | 0.547 [0.52,0.58] | 0.581 [0.54,0.63] | - | 0.563 | 0.507 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +30 | LONDON | cmt_pair | 0.534 [0.48,0.59] | 0.581 [0.51,0.66] | - | 0.582 | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +5 | POOLED | cfree30 | 0.532 [0.50,0.56] | 0.580 [0.53,0.63] | - | 0.556 | 0.490 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +15 | POOLED | X45c:gbt3 | 0.549 [0.52,0.58] | 0.580 [0.54,0.62] | - | 0.552 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +20 | POOLED | X5c:logit2 | 0.554 [0.52,0.59] | 0.580 [0.54,0.62] | - | 0.566 | 0.528 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +30 | LONDON | mt_pair | 0.545 [0.49,0.60] | 0.580 [0.51,0.64] | - | 0.546 | 0.645 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +10 | LONDON | X5c:gbt3 | 0.513 [0.46,0.57] | 0.580 [0.48,0.67] | - | 0.547 | 0.587 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +5 | POOLED | cmt_pair | 0.542 [0.51,0.57] | 0.580 [0.54,0.62] | - | 0.558 | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +45 | LONDON | cc_pair | 0.545 [0.49,0.60] | 0.579 [0.51,0.65] | - | 0.570 | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +45 | ASIA | X4stack:logit2 | 0.546 [0.50,0.59] | 0.579 [0.51,0.64] | - | 0.557 | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +5 | POOLED | X5c:logit2 | 0.530 [0.50,0.56] | 0.578 [0.54,0.62] | - | 0.561 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +45 | LONDON | mono30 | 0.533 [0.48,0.58] | 0.578 [0.50,0.65] | - | 0.570 | 0.605 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +5 | LONDON | cmt_pair | 0.528 [0.48,0.58] | 0.578 [0.50,0.66] | - | 0.575 | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +15 | POOLED | cmt_logit2 | 0.538 [0.51,0.57] | 0.578 [0.53,0.63] | - | 0.571 | 0.499 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +45 | ASIA | X45stack:logit2 | 0.547 [0.50,0.59] | 0.577 [0.52,0.63] | - | 0.561 | 0.570 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +45 | LONDON | X5stack:logit2 | 0.529 [0.48,0.58] | 0.577 [0.49,0.65] | - | 0.589 | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +15 | POOLED | X5c:gbt3 | 0.548 [0.52,0.58] | 0.576 [0.53,0.62] | - | 0.547 | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +20 | POOLED | X45c:logit2 | 0.550 [0.52,0.58] | 0.576 [0.53,0.62] | - | 0.561 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +10 | POOLED | X4c:rf | 0.544 [0.51,0.58] | 0.576 [0.53,0.62] | - | 0.549 | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +15 | POOLED | cmono30 | 0.544 [0.52,0.57] | 0.576 [0.53,0.62] | - | 0.546 | 0.529 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +60 | LONDON | X45c:gbt3 | 0.552 [0.50,0.61] | 0.576 [0.50,0.64] | - | 0.564 | 0.544 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +20 | LONDON | cmono30 | 0.538 [0.49,0.59] | 0.576 [0.50,0.65] | - | 0.530 | 0.624 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +20 | POOLED | cmono30 | 0.545 [0.52,0.57] | 0.576 [0.53,0.62] | - | 0.544 | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +30 | POOLED | X4c:rf | 0.541 [0.51,0.57] | 0.575 [0.53,0.62] | - | 0.552 | 0.519 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +15 | NY | X45stack:rf | 0.515 [0.44,0.58] | 0.575 [0.47,0.68] | - | 0.586 | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +10 | POOLED | X45c:rf | 0.550 [0.52,0.58] | 0.575 [0.53,0.62] | - | 0.544 | 0.504 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +45 | ASIA | mt_gbt3 | 0.550 [0.51,0.59] | 0.574 [0.51,0.63] | - | 0.559 | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +10 | POOLED | cc_xe | 0.542 [0.51,0.57] | 0.574 [0.53,0.62] | - | 0.559 | 0.504 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +45 | ASIA | X5stack:logit2 | 0.541 [0.49,0.59] | 0.574 [0.51,0.63] | - | 0.556 | 0.568 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +20 | POOLED | X4c:logit2 | 0.550 [0.52,0.58] | 0.573 [0.53,0.62] | - | 0.554 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +30 | NY | ctrl_gbt3 | 0.491 [0.42,0.56] | 0.573 [0.46,0.68] | - | 0.599 | 0.818 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +15 | NY | X5c:gbt3 | 0.523 [0.46,0.59] | 0.573 [0.49,0.66] | - | 0.548 | 0.545 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +30 | POOLED | cs_pair | 0.545 [0.51,0.58] | 0.572 [0.53,0.62] | - | 0.550 | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +10 | LONDON | cmt_pair | 0.531 [0.47,0.59] | 0.572 [0.49,0.65] | - | 0.571 | 0.557 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +45 | NY | mono15 | 0.530 [0.46,0.59] | 0.571 [0.47,0.66] | - | 0.560 | 0.662 | ok | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +30 | POOLED | cfree15 | 0.540 [0.51,0.57] | 0.571 [0.53,0.61] | - | 0.534 | 0.534 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +60 | LONDON | X4c:gbt3 | 0.545 [0.49,0.60] | 0.570 [0.49,0.64] | - | 0.572 | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +10 | POOLED | cmono30 | 0.533 [0.50,0.56] | 0.569 [0.53,0.61] | - | 0.544 | 0.504 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +60 | POOLED | X45c:gbt3 | 0.553 [0.52,0.59] | 0.569 [0.53,0.62] | - | 0.552 | 0.493 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +20 | POOLED | cc_logit2 | 0.549 [0.52,0.58] | 0.569 [0.52,0.62] | - | 0.556 | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | pre | LONDON | cmt_pair | 0.523 [0.47,0.58] | 0.568 [0.49,0.65] | - | 0.571 | 0.554 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | pre | POOLED | X5c:rf | 0.553 [0.52,0.58] | 0.568 [0.52,0.62] | - | 0.544 | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +60 | LONDON | cc_stack | 0.538 [0.48,0.59] | 0.568 [0.50,0.64] | - | 0.565 | 0.553 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +60 | POOLED | X4c:gbt3 | 0.541 [0.51,0.58] | 0.568 [0.52,0.62] | - | 0.553 | 0.499 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +45 | LONDON | cmt_pair | 0.515 [0.46,0.57] | 0.567 [0.49,0.65] | - | 0.576 | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +30 | LONDON | free15 | 0.541 [0.49,0.59] | 0.567 [0.49,0.65] | - | 0.543 | 0.601 | ok | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +15 | NY | cfree30 | 0.484 [0.42,0.55] | 0.567 [0.46,0.68] | - | 0.544 | 0.622 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +5 | ASIA | X45c:logit2 | 0.544 [0.50,0.59] | 0.567 [0.51,0.63] | - | 0.564 | 0.562 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +20 | LONDON | X4c:logit2 | 0.539 [0.49,0.59] | 0.567 [0.49,0.64] | - | 0.529 | 0.603 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +5 | ASIA | X5c:logit2 | 0.532 [0.49,0.58] | 0.565 [0.51,0.63] | - | 0.564 | 0.561 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | pre | POOLED | cmono30 | 0.534 [0.50,0.56] | 0.565 [0.52,0.61] | - | 0.539 | 0.490 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | pre | POOLED | X4c:rf | 0.542 [0.51,0.57] | 0.565 [0.52,0.61] | - | 0.545 | 0.504 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +15 | POOLED | cc_lam | 0.538 [0.51,0.57] | 0.565 [0.53,0.61] | - | 0.543 | 0.522 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +10 | LONDON | ctrl_logit2 | 0.551 [0.50,0.61] | 0.564 [0.49,0.64] | - | 0.558 | 0.585 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +45 | NY | X4stack:gbt3 | 0.525 [0.45,0.59] | 0.564 [0.46,0.66] | - | 0.543 | 0.799 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +10 | NY | X4stack:stack | 0.516 [0.45,0.58] | 0.564 [0.48,0.65] | - | 0.586 | 0.769 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +45 | POOLED | X4c:rf | 0.551 [0.52,0.58] | 0.564 [0.52,0.61] | - | 0.539 | 0.511 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | pre | ASIA | X5c:rf | 0.557 [0.51,0.60] | 0.563 [0.50,0.63] | - | 0.548 | 0.571 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +5 | POOLED | cc_stack | 0.531 [0.50,0.56] | 0.562 [0.52,0.61] | - | 0.553 | 0.475 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +45 | POOLED | X45c:rf | 0.546 [0.52,0.58] | 0.562 [0.52,0.60] | - | 0.537 | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +45 | POOLED | mono30 | 0.530 [0.50,0.56] | 0.562 [0.51,0.61] | - | 0.548 | 0.656 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +10 | LONDON | X4stack:logit2 | 0.540 [0.49,0.59] | 0.562 [0.48,0.65] | - | 0.567 | 0.604 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | pre | LONDON | free30 | 0.550 [0.50,0.60] | 0.562 [0.47,0.64] | - | 0.552 | 0.673 | ok | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | pre | POOLED | X45c:rf | 0.549 [0.52,0.58] | 0.561 [0.51,0.61] | - | 0.539 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +45 | POOLED | cc_rf | 0.549 [0.52,0.58] | 0.561 [0.52,0.60] | - | 0.542 | 0.529 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | pre | ASIA | X45c:gbt3 | 0.550 [0.51,0.59] | 0.561 [0.50,0.62] | - | 0.536 | 0.562 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +45 | ASIA | ctrl_logit2 | 0.538 [0.49,0.58] | 0.561 [0.50,0.62] | - | 0.542 | 0.563 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +20 | NY | ctrl_gbt3 | 0.512 [0.44,0.58] | 0.560 [0.45,0.67] | - | 0.554 | 0.827 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +15 | NY | free30 | 0.498 [0.43,0.56] | 0.559 [0.46,0.66] | - | 0.516 | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +30 | ASIA | mono15 | 0.547 [0.50,0.59] | 0.559 [0.50,0.62] | - | 0.544 | 0.540 | ok | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +10 | LONDON | cmono30 | 0.494 [0.44,0.55] | 0.559 [0.49,0.64] | - | 0.539 | 0.594 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +30 | NY | X45c:logit2 | 0.533 [0.47,0.60] | 0.558 [0.46,0.65] | - | 0.556 | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +15 | LONDON | rk_pair | 0.553 [0.50,0.61] | 0.558 [0.47,0.64] | - | 0.525 | 0.643 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +60 | POOLED | X5c:gbt3 | 0.539 [0.50,0.58] | 0.558 [0.51,0.60] | - | 0.545 | 0.505 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +10 | NY | X45stack:stack | 0.517 [0.45,0.58] | 0.558 [0.46,0.64] | - | 0.593 | 0.777 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +45 | LONDON | cs_ll | 0.530 [0.47,0.58] | 0.557 [0.49,0.63] | - | 0.535 | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +5 | LONDON | cfree30 | 0.486 [0.43,0.54] | 0.557 [0.47,0.64] | - | 0.547 | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +30 | POOLED | cc_logit2 | 0.532 [0.50,0.56] | 0.557 [0.51,0.60] | - | 0.545 | 0.491 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +60 | NY | ctrl_gbt3 | 0.529 [0.45,0.60] | 0.557 [0.46,0.67] | - | 0.586 | 0.862 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +10 | POOLED | cs_pair | 0.550 [0.52,0.58] | 0.556 [0.51,0.60] | - | 0.523 | 0.489 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +60 | LONDON | cmono30 | 0.531 [0.48,0.59] | 0.555 [0.48,0.63] | - | 0.552 | 0.567 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +45 | POOLED | cfree30 | 0.546 [0.52,0.57] | 0.555 [0.51,0.59] | - | 0.528 | 0.539 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +60 | POOLED | mono15 | 0.531 [0.50,0.56] | 0.555 [0.51,0.59] | - | 0.544 | 0.657 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +5 | ASIA | cc_logit2 | 0.525 [0.48,0.57] | 0.555 [0.50,0.62] | - | 0.549 | 0.544 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +45 | POOLED | cs_ll | 0.542 [0.51,0.57] | 0.555 [0.51,0.60] | - | 0.526 | 0.537 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +30 | ASIA | mt_gbt3 | 0.535 [0.49,0.58] | 0.554 [0.49,0.61] | - | 0.542 | 0.543 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +30 | NY | X45stack:logit2 | 0.499 [0.42,0.57] | 0.553 [0.45,0.66] | - | 0.550 | 0.733 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +5 | ASIA | X4c:logit2 | 0.527 [0.48,0.57] | 0.553 [0.50,0.61] | - | 0.547 | 0.547 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +15 | ASIA | ctrl_gbt3 | 0.549 [0.50,0.60] | 0.553 [0.49,0.61] | - | 0.553 | 0.572 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +5 | ASIA | X5stack:gbt3 | 0.549 [0.51,0.59] | 0.552 [0.50,0.61] | - | 0.542 | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +60 | NY | X4c:gbt3 | 0.550 [0.48,0.62] | 0.552 [0.45,0.65] | - | 0.530 | 0.505 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +10 | LONDON | cc_stack | 0.519 [0.47,0.57] | 0.552 [0.47,0.63] | - | 0.543 | 0.574 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +30 | NY | cc_xe | 0.545 [0.48,0.61] | 0.551 [0.44,0.65] | - | 0.563 | 0.557 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +45 | NY | X5stack:gbt3 | 0.525 [0.45,0.60] | 0.551 [0.45,0.66] | - | 0.548 | 0.821 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +5 | ASIA | cfree30 | 0.525 [0.48,0.57] | 0.550 [0.48,0.61] | - | 0.540 | 0.544 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +30 | NY | cs_pair | 0.529 [0.47,0.61] | 0.550 [0.46,0.66] | - | 0.533 | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +60 | NY | mono15 | 0.538 [0.46,0.61] | 0.550 [0.46,0.65] | - | 0.551 | 0.649 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +45 | POOLED | cmt_rf | 0.522 [0.49,0.55] | 0.550 [0.51,0.59] | - | 0.529 | 0.468 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +10 | NY | cmt_rf | 0.546 [0.48,0.61] | 0.550 [0.45,0.65] | - | 0.557 | 0.538 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | pre | ASIA | X4c:rf | 0.540 [0.49,0.59] | 0.550 [0.48,0.62] | - | 0.531 | 0.556 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +5 | ASIA | cs_ll | 0.532 [0.49,0.57] | 0.549 [0.50,0.60] | - | 0.537 | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +20 | POOLED | cs_pair | 0.539 [0.51,0.57] | 0.549 [0.51,0.59] | - | 0.532 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +60 | ASIA | X45c:logit2 | 0.534 [0.49,0.58] | 0.549 [0.49,0.61] | - | 0.531 | 0.547 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +20 | LONDON | cs_ll | 0.523 [0.48,0.57] | 0.549 [0.49,0.62] | - | 0.538 | 0.579 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | pre | LONDON | X45c:stack | 0.539 [0.49,0.59] | 0.549 [0.47,0.63] | - | 0.541 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | pre | POOLED | cc_lam | 0.541 [0.51,0.57] | 0.548 [0.50,0.60] | - | 0.533 | 0.488 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +20 | NY | rk_xe | 0.524 [0.46,0.59] | 0.547 [0.45,0.64] | - | 0.550 | 0.813 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | pre | ASIA | mt_rf | 0.548 [0.50,0.59] | 0.547 [0.48,0.61] | - | 0.539 | 0.545 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | pre | NY | cmt_logit2 | 0.553 [0.49,0.61] | 0.547 [0.45,0.64] | - | 0.550 | 0.500 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +30 | POOLED | cmt_gbt3 | 0.527 [0.50,0.56] | 0.546 [0.50,0.59] | - | 0.522 | 0.491 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | pre | ASIA | X5stack:gbt3 | 0.558 [0.52,0.60] | 0.546 [0.49,0.61] | - | 0.520 | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +10 | LONDON | X45c:rf | 0.489 [0.44,0.54] | 0.546 [0.46,0.62] | - | 0.527 | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +15 | LONDON | X45c:stack | 0.532 [0.48,0.59] | 0.546 [0.46,0.62] | - | 0.488 | 0.548 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +15 | ASIA | mono15 | 0.561 [0.52,0.60] | 0.546 [0.49,0.61] | - | 0.534 | 0.536 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +20 | POOLED | cmt_gbt3 | 0.535 [0.51,0.57] | 0.546 [0.50,0.59] | - | 0.525 | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | pre | ASIA | cs_ll | 0.573 [0.53,0.62] | 0.546 [0.48,0.61] | - | 0.521 | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +20 | NY | cmt_rf | 0.555 [0.48,0.62] | 0.546 [0.42,0.65] | - | 0.531 | 0.555 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +30 | POOLED | ctrl_gbt3 | 0.507 [0.48,0.54] | 0.545 [0.50,0.59] | - | 0.535 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +60 | ASIA | ctrl_gbt3 | 0.507 [0.46,0.55] | 0.545 [0.48,0.60] | - | 0.539 | 0.530 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +30 | LONDON | cs_pair | 0.517 [0.46,0.58] | 0.545 [0.47,0.62] | - | 0.546 | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +60 | POOLED | cmono30 | 0.542 [0.51,0.58] | 0.545 [0.50,0.59] | - | 0.527 | 0.520 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +45 | POOLED | X5stack:logit2 | 0.516 [0.48,0.55] | 0.545 [0.50,0.59] | - | 0.538 | 0.685 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +45 | NY | X45c:gbt3 | 0.536 [0.47,0.61] | 0.545 [0.45,0.65] | - | 0.540 | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +45 | POOLED | ctrl_logit2 | 0.512 [0.48,0.54] | 0.544 [0.49,0.59] | - | 0.543 | 0.663 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +30 | ASIA | X5stack:rf | 0.539 [0.50,0.58] | 0.544 [0.49,0.60] | - | 0.535 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +30 | NY | X5c:logit2 | 0.513 [0.45,0.57] | 0.544 [0.44,0.64] | - | 0.557 | 0.573 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +20 | NY | free15 | 0.533 [0.46,0.60] | 0.543 [0.44,0.64] | - | 0.521 | 0.654 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +60 | ASIA | mono15 | 0.535 [0.49,0.58] | 0.543 [0.49,0.60] | - | 0.517 | 0.519 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +30 | NY | X5stack:gbt3 | 0.487 [0.41,0.57] | 0.542 [0.42,0.67] | - | 0.550 | 0.813 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +60 | ASIA | X4c:logit2 | 0.531 [0.48,0.58] | 0.542 [0.49,0.60] | - | 0.523 | 0.539 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +45 | NY | X45stack:gbt3 | 0.516 [0.45,0.58] | 0.541 [0.43,0.65] | - | 0.533 | 0.817 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +30 | POOLED | X45stack:rf | 0.509 [0.48,0.54] | 0.541 [0.50,0.59] | - | 0.529 | 0.701 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +15 | POOLED | X4stack:rf | 0.515 [0.48,0.55] | 0.541 [0.49,0.58] | - | 0.525 | 0.692 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +5 | ASIA | free30 | 0.545 [0.50,0.59] | 0.541 [0.48,0.61] | - | 0.528 | 0.542 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | pre | ASIA | mono30 | 0.532 [0.49,0.57] | 0.540 [0.48,0.60] | - | 0.503 | 0.538 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +30 | POOLED | mono15 | 0.526 [0.49,0.56] | 0.540 [0.49,0.59] | - | 0.520 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +20 | LONDON | X4stack:logit2 | 0.528 [0.48,0.58] | 0.539 [0.47,0.61] | - | 0.537 | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +5 | ASIA | X45stack:gbt3 | 0.545 [0.51,0.58] | 0.539 [0.48,0.60] | - | 0.531 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +20 | LONDON | X5stack:logit2 | 0.515 [0.47,0.56] | 0.539 [0.47,0.61] | - | 0.536 | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | pre | ASIA | cc_lam | 0.550 [0.51,0.59] | 0.539 [0.48,0.59] | - | 0.528 | 0.545 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | pre | ASIA | cfree15 | 0.518 [0.47,0.56] | 0.539 [0.48,0.60] | - | 0.524 | 0.534 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +60 | LONDON | ctrl_logit2 | 0.503 [0.45,0.55] | 0.539 [0.47,0.61] | - | 0.550 | 0.593 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | pre | ASIA | X4stack:rf | 0.553 [0.51,0.59] | 0.538 [0.48,0.60] | - | 0.517 | 0.536 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +60 | NY | cmono30 | 0.543 [0.47,0.61] | 0.538 [0.43,0.63] | - | 0.551 | 0.609 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +15 | ASIA | X4stack:rf | 0.548 [0.50,0.59] | 0.538 [0.48,0.60] | - | 0.527 | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +10 | NY | free30 | 0.489 [0.42,0.56] | 0.538 [0.44,0.65] | - | 0.553 | 0.658 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +5 | ASIA | cmt_gbt3 | 0.523 [0.48,0.56] | 0.538 [0.48,0.59] | - | 0.528 | 0.535 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +10 | ASIA | X5stack:stack | 0.557 [0.52,0.60] | 0.538 [0.48,0.59] | - | 0.537 | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +20 | POOLED | X5stack:rf | 0.498 [0.47,0.52] | 0.537 [0.50,0.58] | - | 0.526 | 0.706 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +30 | ASIA | X4stack:stack | 0.533 [0.49,0.58] | 0.537 [0.48,0.59] | - | 0.527 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +60 | POOLED | cs_pair | 0.545 [0.51,0.58] | 0.537 [0.50,0.58] | - | 0.515 | 0.491 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +20 | LONDON | cc_logit2 | 0.533 [0.48,0.59] | 0.537 [0.47,0.61] | - | 0.522 | 0.583 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +45 | NY | cmt_rf | 0.509 [0.43,0.58] | 0.536 [0.42,0.65] | - | 0.525 | 0.533 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +5 | POOLED | X45c:stack | 0.530 [0.50,0.56] | 0.536 [0.49,0.58] | - | 0.508 | 0.502 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +30 | ASIA | cc_rf | 0.544 [0.50,0.59] | 0.535 [0.48,0.60] | - | 0.516 | 0.517 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +20 | LONDON | X45stack:logit2 | 0.527 [0.48,0.58] | 0.535 [0.46,0.61] | - | 0.532 | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +10 | ASIA | X4stack:gbt3 | 0.552 [0.51,0.60] | 0.534 [0.47,0.60] | - | 0.525 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +60 | POOLED | cmt_logit2 | 0.513 [0.48,0.54] | 0.534 [0.49,0.58] | - | 0.525 | 0.481 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +30 | ASIA | X45c:rf | 0.533 [0.49,0.57] | 0.533 [0.48,0.59] | - | 0.520 | 0.519 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | pre | ASIA | X45stack:rf | 0.548 [0.51,0.59] | 0.533 [0.47,0.60] | - | 0.515 | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +15 | POOLED | mono15 | 0.515 [0.49,0.54] | 0.533 [0.49,0.58] | - | 0.510 | 0.643 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +15 | NY | cs_pair | 0.518 [0.45,0.58] | 0.533 [0.44,0.63] | - | 0.483 | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +60 | NY | X5c:rf | 0.537 [0.46,0.61] | 0.533 [0.43,0.63] | - | 0.518 | 0.617 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +5 | NY | X45stack:rf | 0.496 [0.43,0.56] | 0.532 [0.43,0.63] | - | 0.521 | 0.764 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +20 | POOLED | X4stack:stack | 0.508 [0.48,0.54] | 0.532 [0.48,0.58] | - | 0.525 | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +60 | ASIA | X5stack:stack | 0.509 [0.46,0.55] | 0.532 [0.48,0.58] | - | 0.531 | 0.534 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +15 | LONDON | cc_lam | 0.520 [0.47,0.57] | 0.531 [0.46,0.60] | - | 0.528 | 0.543 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +30 | POOLED | X4stack:rf | 0.501 [0.47,0.53] | 0.531 [0.49,0.58] | - | 0.521 | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +30 | ASIA | prod_pair | 0.546 [0.50,0.59] | 0.531 [0.46,0.60] | - | 0.521 | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +15 | NY | cmt_rf | 0.543 [0.47,0.61] | 0.531 [0.41,0.63] | - | 0.511 | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +30 | LONDON | ctrl_logit2 | 0.536 [0.48,0.59] | 0.530 [0.44,0.62] | - | 0.513 | 0.594 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +45 | ASIA | cc_rf | 0.554 [0.51,0.60] | 0.530 [0.47,0.59] | - | 0.516 | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +45 | ASIA | X4c:logit2 | 0.536 [0.49,0.58] | 0.530 [0.46,0.59] | - | 0.524 | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +5 | NY | X45c:gbt3 | 0.516 [0.45,0.58] | 0.530 [0.42,0.64] | - | 0.564 | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +15 | POOLED | rk_pair | 0.526 [0.49,0.56] | 0.529 [0.48,0.58] | - | 0.497 | 0.620 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +20 | POOLED | X45stack:stack | 0.511 [0.48,0.54] | 0.529 [0.48,0.57] | - | 0.517 | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +30 | NY | X4c:logit2 | 0.510 [0.45,0.57] | 0.529 [0.43,0.62] | - | 0.532 | 0.515 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | pre | ASIA | ctrl_gbt3 | 0.537 [0.50,0.58] | 0.529 [0.47,0.60] | - | 0.504 | 0.529 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +45 | NY | X5c:rf | 0.518 [0.45,0.59] | 0.529 [0.44,0.62] | - | 0.513 | 0.612 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +5 | LONDON | mono30 | 0.517 [0.47,0.57] | 0.529 [0.47,0.60] | - | 0.513 | 0.622 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +10 | POOLED | X4stack:stack | 0.511 [0.48,0.54] | 0.529 [0.49,0.57] | - | 0.519 | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | pre | POOLED | mt_pair | 0.523 [0.49,0.55] | 0.529 [0.49,0.57] | - | 0.515 | 0.617 | ok | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +15 | ASIA | cfree30 | 0.531 [0.49,0.57] | 0.528 [0.46,0.59] | - | 0.509 | 0.518 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +30 | ASIA | X4c:stack | 0.544 [0.50,0.58] | 0.528 [0.47,0.59] | - | 0.502 | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +30 | ASIA | X45stack:stack | 0.532 [0.49,0.58] | 0.528 [0.47,0.59] | - | 0.516 | 0.511 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +5 | NY | cmt_gbt3 | 0.534 [0.47,0.60] | 0.528 [0.42,0.63] | - | 0.558 | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +10 | ASIA | ctrl_gbt3 | 0.536 [0.49,0.59] | 0.528 [0.46,0.60] | - | 0.517 | 0.531 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +15 | POOLED | X45stack:rf | 0.514 [0.48,0.55] | 0.528 [0.48,0.57] | - | 0.515 | 0.694 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +30 | ASIA | ctrl_gbt3 | 0.526 [0.48,0.57] | 0.528 [0.47,0.59] | - | 0.516 | 0.502 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | pre | POOLED | cs_ll | 0.541 [0.51,0.57] | 0.528 [0.48,0.57] | - | 0.498 | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +5 | ASIA | X4stack:gbt3 | 0.537 [0.50,0.57] | 0.527 [0.47,0.59] | - | 0.517 | 0.524 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +20 | ASIA | rk_pair | 0.539 [0.50,0.58] | 0.527 [0.47,0.59] | - | 0.519 | 0.512 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | pre | ASIA | cmt_gbt3 | 0.523 [0.48,0.56] | 0.527 [0.47,0.59] | - | 0.517 | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +15 | NY | X4c:stack | 0.513 [0.44,0.57] | 0.526 [0.42,0.61] | - | 0.535 | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +60 | ASIA | cs_pair | 0.530 [0.48,0.57] | 0.526 [0.47,0.58] | - | 0.494 | 0.511 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +30 | LONDON | X4stack:logit2 | 0.526 [0.48,0.58] | 0.526 [0.44,0.61] | - | 0.507 | 0.584 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +10 | ASIA | cmt_pair | 0.519 [0.48,0.56] | 0.526 [0.46,0.58] | - | 0.521 | 0.507 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +30 | LONDON | cc_xe | 0.506 [0.45,0.56] | 0.526 [0.46,0.61] | - | 0.552 | 0.539 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +20 | ASIA | X45c:logit2 | 0.505 [0.46,0.55] | 0.526 [0.46,0.59] | - | 0.516 | 0.520 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +45 | ASIA | X45c:logit2 | 0.535 [0.49,0.58] | 0.525 [0.46,0.59] | - | 0.523 | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +15 | ASIA | rk_pair | 0.543 [0.51,0.58] | 0.525 [0.47,0.58] | - | 0.512 | 0.533 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +45 | POOLED | X45stack:gbt3 | 0.504 [0.47,0.54] | 0.524 [0.47,0.58] | - | 0.519 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | pre | NY | cc_xe | 0.541 [0.48,0.61] | 0.524 [0.42,0.62] | - | 0.490 | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +45 | LONDON | ctrl_gbt3 | 0.503 [0.45,0.56] | 0.524 [0.45,0.60] | - | 0.524 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +5 | LONDON | cc_stack | 0.489 [0.44,0.54] | 0.524 [0.45,0.61] | - | 0.529 | 0.533 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +60 | POOLED | ctrl_gbt3 | 0.493 [0.46,0.53] | 0.524 [0.48,0.57] | - | 0.524 | 0.697 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +60 | LONDON | X45stack:logit2 | 0.502 [0.45,0.55] | 0.523 [0.44,0.61] | - | 0.525 | 0.687 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +60 | LONDON | X5stack:logit2 | 0.498 [0.45,0.55] | 0.523 [0.44,0.60] | - | 0.537 | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +10 | ASIA | cfree15 | 0.529 [0.48,0.57] | 0.523 [0.46,0.59] | - | 0.502 | 0.512 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +5 | POOLED | X4c:stack | 0.517 [0.49,0.54] | 0.522 [0.48,0.57] | - | 0.486 | 0.501 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +10 | LONDON | free30 | 0.525 [0.47,0.57] | 0.522 [0.45,0.59] | - | 0.532 | 0.591 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +5 | NY | X5c:gbt3 | 0.510 [0.44,0.58] | 0.522 [0.42,0.63] | - | 0.562 | 0.573 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +60 | POOLED | mt_pair | 0.515 [0.48,0.55] | 0.522 [0.48,0.56] | - | 0.504 | 0.613 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +10 | LONDON | X4c:stack | 0.509 [0.46,0.56] | 0.522 [0.44,0.61] | - | 0.474 | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | pre | NY | X45c:gbt3 | 0.541 [0.47,0.61] | 0.521 [0.41,0.62] | - | 0.524 | 0.557 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +45 | NY | cfree15 | 0.541 [0.48,0.61] | 0.521 [0.42,0.63] | - | 0.487 | 0.617 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +20 | ASIA | X4c:logit2 | 0.505 [0.46,0.55] | 0.521 [0.46,0.59] | - | 0.511 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +5 | NY | cfree15 | 0.512 [0.45,0.58] | 0.521 [0.42,0.62] | - | 0.520 | 0.571 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +20 | ASIA | cmono30 | 0.512 [0.47,0.56] | 0.521 [0.46,0.58] | - | 0.496 | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +30 | NY | X4stack:gbt3 | 0.487 [0.41,0.56] | 0.521 [0.41,0.64] | - | 0.517 | 0.789 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +10 | NY | ctrl_gbt3 | 0.504 [0.44,0.57] | 0.521 [0.43,0.61] | - | 0.583 | 0.773 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +60 | POOLED | cc_pair | 0.522 [0.49,0.55] | 0.521 [0.47,0.57] | - | 0.501 | 0.496 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +20 | ASIA | X5stack:rf | 0.524 [0.48,0.57] | 0.520 [0.46,0.58] | - | 0.508 | 0.500 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +45 | POOLED | X4stack:gbt3 | 0.503 [0.47,0.53] | 0.520 [0.46,0.58] | - | 0.515 | 0.672 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +5 | NY | X5stack:rf | 0.496 [0.43,0.56] | 0.520 [0.42,0.62] | - | 0.495 | 0.768 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +60 | NY | cc_rf | 0.544 [0.47,0.62] | 0.520 [0.42,0.62] | - | 0.535 | 0.628 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +60 | POOLED | X5stack:stack | 0.492 [0.46,0.52] | 0.520 [0.48,0.56] | - | 0.520 | 0.718 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +20 | ASIA | cc_gbt3 | 0.511 [0.46,0.56] | 0.519 [0.45,0.58] | - | 0.498 | 0.511 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +5 | ASIA | ctrl_gbt3 | 0.511 [0.47,0.55] | 0.519 [0.45,0.59] | - | 0.503 | 0.518 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +45 | ASIA | cmt_logit2 | 0.499 [0.46,0.54] | 0.518 [0.46,0.58] | - | 0.516 | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +45 | ASIA | X5c:gbt3 | 0.542 [0.49,0.59] | 0.518 [0.46,0.58] | - | 0.501 | 0.500 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +5 | POOLED | mt_pair | 0.523 [0.49,0.55] | 0.518 [0.48,0.55] | - | 0.504 | 0.615 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +30 | ASIA | X5c:rf | 0.524 [0.48,0.56] | 0.518 [0.46,0.58] | - | 0.498 | 0.503 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +60 | ASIA | X5c:gbt3 | 0.516 [0.47,0.56] | 0.518 [0.46,0.58] | - | 0.493 | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +15 | LONDON | ctrl_logit2 | 0.522 [0.47,0.58] | 0.518 [0.43,0.61] | - | 0.524 | 0.579 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +20 | POOLED | mono15 | 0.507 [0.48,0.53] | 0.517 [0.48,0.56] | - | 0.494 | 0.640 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +10 | NY | cc_rf | 0.516 [0.44,0.59] | 0.517 [0.42,0.61] | - | 0.545 | 0.531 | N | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | +10 | ASIA | cc_xe | 0.522 [0.48,0.57] | 0.517 [0.45,0.58] | - | 0.515 | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +10 | ASIA | X45stack:rf | 0.546 [0.51,0.59] | 0.517 [0.46,0.57] | - | 0.505 | 0.512 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +10 | NY | X45c:rf | 0.517 [0.45,0.59] | 0.517 [0.42,0.61] | - | 0.552 | 0.544 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +30 | POOLED | X5c:stack | 0.524 [0.50,0.55] | 0.516 [0.47,0.56] | - | 0.488 | 0.535 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +15 | POOLED | ctrl_gbt3 | 0.497 [0.46,0.53] | 0.516 [0.47,0.56] | - | 0.502 | 0.698 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +15 | POOLED | X5stack:rf | 0.496 [0.47,0.53] | 0.515 [0.47,0.56] | - | 0.493 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +10 | ASIA | free15 | 0.553 [0.51,0.60] | 0.515 [0.45,0.58] | - | 0.499 | 0.507 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +15 | ASIA | X45stack:rf | 0.544 [0.50,0.59] | 0.514 [0.45,0.57] | - | 0.504 | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +15 | ASIA | X5c:stack | 0.533 [0.49,0.58] | 0.514 [0.45,0.58] | - | 0.483 | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +15 | NY | X4stack:gbt3 | 0.499 [0.43,0.56] | 0.514 [0.42,0.61] | - | 0.524 | 0.772 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +20 | ASIA | ctrl_gbt3 | 0.524 [0.48,0.57] | 0.513 [0.45,0.57] | - | 0.494 | 0.498 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +60 | NY | X45stack:stack | 0.499 [0.43,0.57] | 0.513 [0.41,0.61] | - | 0.511 | 0.833 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | +20 | ASIA | mono15 | 0.536 [0.49,0.58] | 0.512 [0.45,0.57] | - | 0.494 | 0.497 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +10 | POOLED | X45stack:rf | 0.504 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.500 | 0.679 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +20 | POOLED | ctrl_gbt3 | 0.496 [0.47,0.52] | 0.512 [0.47,0.55] | - | 0.496 | 0.684 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +60 | ASIA | X4stack:stack | 0.492 [0.44,0.54] | 0.512 [0.45,0.58] | - | 0.509 | 0.502 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +60 | POOLED | X4stack:logit2 | 0.491 [0.46,0.52] | 0.512 [0.46,0.56] | - | 0.526 | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +20 | LONDON | ctrl_logit2 | 0.511 [0.46,0.57] | 0.512 [0.43,0.59] | - | 0.510 | 0.591 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +10 | POOLED | mt_pair | 0.519 [0.49,0.55] | 0.511 [0.47,0.55] | - | 0.494 | 0.609 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +10 | NY | X5stack:rf | 0.491 [0.42,0.56] | 0.511 [0.41,0.60] | - | 0.561 | 0.767 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +30 | LONDON | X5stack:logit2 | 0.524 [0.47,0.58] | 0.510 [0.43,0.60] | - | 0.497 | 0.630 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +15 | NY | cc_logit2 | 0.508 [0.44,0.57] | 0.510 [0.41,0.61] | - | 0.507 | 0.539 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +30 | POOLED | X5stack:logit2 | 0.493 [0.46,0.52] | 0.510 [0.47,0.55] | - | 0.499 | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +20 | ASIA | X45stack:rf | 0.537 [0.50,0.58] | 0.510 [0.45,0.57] | - | 0.502 | 0.489 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +60 | ASIA | cmono30 | 0.520 [0.47,0.56] | 0.510 [0.45,0.58] | - | 0.476 | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| X45-condtrained | +15 | NY | X45c:stack | 0.506 [0.44,0.57] | 0.510 [0.42,0.60] | - | 0.489 | 0.576 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +15 | LONDON | X5c:stack | 0.528 [0.48,0.58] | 0.510 [0.43,0.59] | - | 0.494 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +20 | ASIA | X5c:stack | 0.514 [0.47,0.56] | 0.509 [0.45,0.57] | - | 0.481 | 0.488 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +10 | POOLED | X5stack:stack | 0.505 [0.48,0.53] | 0.509 [0.47,0.55] | - | 0.507 | 0.684 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +5 | LONDON | X5c:stack | 0.526 [0.48,0.58] | 0.509 [0.44,0.58] | - | 0.509 | 0.535 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +20 | POOLED | mt_pair | 0.515 [0.48,0.55] | 0.508 [0.47,0.55] | - | 0.491 | 0.611 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +15 | LONDON | X5stack:logit2 | 0.522 [0.47,0.57] | 0.508 [0.44,0.58] | - | 0.518 | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +30 | POOLED | mt_pair | 0.510 [0.48,0.54] | 0.508 [0.47,0.55] | - | 0.483 | 0.607 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +60 | ASIA | X45stack:stack | 0.490 [0.45,0.54] | 0.508 [0.45,0.56] | - | 0.509 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +45 | NY | cc_pair | 0.509 [0.45,0.57] | 0.507 [0.41,0.60] | - | 0.498 | 0.586 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +45 | LONDON | X45stack:gbt3 | 0.487 [0.44,0.54] | 0.506 [0.42,0.60] | - | 0.518 | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +5 | ASIA | mt_pair | 0.514 [0.47,0.56] | 0.506 [0.46,0.56] | - | 0.509 | 0.510 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +60 | POOLED | X45stack:logit2 | 0.489 [0.45,0.52] | 0.506 [0.45,0.56] | - | 0.512 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +20 | ASIA | cmt_gbt3 | 0.505 [0.46,0.55] | 0.505 [0.44,0.56] | - | 0.495 | 0.500 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | +45 | ASIA | cfree30 | 0.521 [0.47,0.56] | 0.505 [0.44,0.57] | - | 0.490 | 0.487 | N | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +15 | NY | X5stack:gbt3 | 0.480 [0.41,0.54] | 0.505 [0.40,0.61] | - | 0.544 | 0.789 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | pre | LONDON | X4stack:logit2 | 0.526 [0.47,0.58] | 0.505 [0.42,0.59] | - | 0.471 | 0.601 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +15 | POOLED | mt_pair | 0.518 [0.48,0.55] | 0.505 [0.46,0.55] | - | 0.487 | 0.609 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +15 | ASIA | cmt_pair | 0.511 [0.47,0.55] | 0.505 [0.45,0.56] | - | 0.499 | 0.487 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +45 | POOLED | mt_pair | 0.512 [0.48,0.55] | 0.505 [0.47,0.54] | - | 0.480 | 0.602 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +15 | LONDON | X45stack:stack | 0.524 [0.47,0.58] | 0.504 [0.42,0.59] | - | 0.483 | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | pre | NY | X5c:rf | 0.528 [0.45,0.60] | 0.503 [0.38,0.61] | - | 0.497 | 0.574 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-condtrained | +30 | ASIA | cmt_gbt3 | 0.501 [0.46,0.54] | 0.503 [0.44,0.55] | - | 0.493 | 0.496 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +10 | NY | X5c:gbt3 | 0.513 [0.45,0.58] | 0.503 [0.41,0.60] | - | 0.549 | 0.543 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +30 | LONDON | X45stack:logit2 | 0.514 [0.47,0.57] | 0.502 [0.43,0.58] | - | 0.502 | 0.624 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +5 | LONDON | X45c:stack | 0.529 [0.48,0.58] | 0.502 [0.43,0.57] | - | 0.498 | 0.517 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | pre | LONDON | X5c:stack | 0.517 [0.46,0.57] | 0.502 [0.42,0.58] | - | 0.507 | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-rescored | +20 | ASIA | X4stack:rf | 0.533 [0.49,0.58] | 0.502 [0.44,0.56] | - | 0.494 | 0.480 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +15 | ASIA | X5stack:rf | 0.533 [0.49,0.58] | 0.502 [0.44,0.56] | - | 0.493 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +15 | ASIA | X45c:gbt3 | 0.523 [0.48,0.56] | 0.501 [0.44,0.56] | - | 0.483 | 0.491 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +5 | POOLED | X45stack:logit2 | 0.494 [0.47,0.52] | 0.500 [0.46,0.55] | - | 0.483 | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | pre | LONDON | ctrl_logit2 | 0.499 [0.45,0.55] | 0.500 [0.42,0.59] | - | 0.504 | 0.574 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +15 | ASIA | X4c:gbt3 | 0.513 [0.47,0.55] | 0.499 [0.44,0.55] | - | 0.472 | 0.490 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +30 | POOLED | X45c:stack | 0.514 [0.48,0.54] | 0.498 [0.45,0.54] | - | 0.471 | 0.535 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +5 | POOLED | rk_pair | 0.498 [0.47,0.52] | 0.498 [0.46,0.54] | - | 0.465 | 0.589 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | pre | POOLED | ctrl_gbt3 | 0.479 [0.45,0.51] | 0.498 [0.46,0.55] | - | 0.492 | 0.665 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +10 | LONDON | X5stack:logit2 | 0.514 [0.47,0.56] | 0.498 [0.42,0.58] | - | 0.484 | 0.660 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +10 | ASIA | X4c:stack | 0.535 [0.49,0.57] | 0.496 [0.43,0.56] | - | 0.462 | 0.490 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +45 | NY | X4c:rf | 0.506 [0.44,0.58] | 0.495 [0.39,0.60] | - | 0.476 | 0.547 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | +5 | POOLED | X5stack:logit2 | 0.492 [0.47,0.52] | 0.495 [0.45,0.54] | - | 0.476 | 0.663 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +10 | ASIA | cs_pair | 0.525 [0.48,0.57] | 0.494 [0.43,0.57] | - | 0.476 | 0.481 | N | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +10 | ASIA | X5c:rf | 0.519 [0.47,0.56] | 0.494 [0.43,0.56] | - | 0.474 | 0.485 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-rescored | +10 | LONDON | X45stack:logit2 | 0.522 [0.47,0.58] | 0.494 [0.42,0.58] | - | 0.483 | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +30 | ASIA | cfree15 | 0.526 [0.48,0.57] | 0.493 [0.43,0.55] | - | 0.472 | 0.479 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | pre | POOLED | X45stack:rf | 0.501 [0.47,0.53] | 0.493 [0.45,0.53] | - | 0.469 | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +10 | POOLED | ctrl_logit2 | 0.489 [0.46,0.52] | 0.493 [0.45,0.53] | - | 0.492 | 0.621 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +30 | LONDON | X4c:stack | 0.501 [0.45,0.56] | 0.493 [0.42,0.56] | - | 0.465 | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +60 | ASIA | cc_lam | 0.503 [0.46,0.55] | 0.492 [0.43,0.55] | - | 0.481 | 0.478 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | pre | LONDON | X4c:stack | 0.512 [0.46,0.57] | 0.492 [0.42,0.56] | - | 0.477 | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +30 | LONDON | X45c:stack | 0.519 [0.47,0.58] | 0.491 [0.41,0.57] | - | 0.458 | 0.553 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +10 | ASIA | mt_pair | 0.515 [0.47,0.56] | 0.490 [0.44,0.55] | - | 0.493 | 0.495 | ok | - | - | - | - |  | locked label (reference only) |
| X5-condtrained | +30 | LONDON | X5c:stack | 0.533 [0.48,0.59] | 0.490 [0.40,0.57] | - | 0.456 | 0.577 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | pre | NY | cs_pair | 0.536 [0.47,0.59] | 0.490 [0.41,0.58] | - | 0.469 | 0.529 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | pre | POOLED | X4stack:stack | 0.501 [0.47,0.53] | 0.489 [0.45,0.53] | - | 0.477 | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +20 | NY | cc_logit2 | 0.517 [0.45,0.58] | 0.489 [0.38,0.59] | - | 0.489 | 0.547 | N | - | - | - | - |  | locked label (reference only) |
| X2-rescored | pre | POOLED | free30 | 0.485 [0.45,0.51] | 0.489 [0.44,0.54] | - | 0.475 | 0.651 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +5 | NY | free15 | 0.479 [0.41,0.54] | 0.489 [0.39,0.59] | - | 0.482 | 0.602 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +60 | ASIA | cmt_pair | 0.496 [0.45,0.54] | 0.489 [0.43,0.54] | - | 0.479 | 0.467 | N | - | - | - | - |  | locked label (reference only) |
| X2-condtrained | pre | LONDON | cfree15 | 0.475 [0.42,0.53] | 0.488 [0.41,0.57] | - | 0.474 | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | pre | NY | X45stack:rf | 0.508 [0.44,0.58] | 0.485 [0.38,0.58] | - | 0.511 | 0.790 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +15 | ASIA | cc_gbt3 | 0.504 [0.46,0.54] | 0.485 [0.43,0.53] | - | 0.473 | 0.487 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +5 | NY | cs_pair | 0.507 [0.45,0.57] | 0.484 [0.40,0.59] | - | 0.535 | 0.492 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +10 | NY | X4c:rf | 0.490 [0.42,0.56] | 0.483 [0.38,0.58] | - | 0.526 | 0.534 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-condtrained | +20 | NY | X5c:logit2 | 0.518 [0.46,0.58] | 0.483 [0.36,0.59] | - | 0.498 | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +10 | ASIA | X45c:rf | 0.525 [0.48,0.57] | 0.483 [0.42,0.55] | - | 0.461 | 0.474 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +20 | ASIA | mt_pair | 0.503 [0.46,0.55] | 0.482 [0.43,0.54] | - | 0.480 | 0.485 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +10 | POOLED | free15 | 0.491 [0.46,0.52] | 0.482 [0.44,0.52] | - | 0.469 | 0.598 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +60 | NY | X5stack:stack | 0.477 [0.40,0.55] | 0.482 [0.38,0.58] | - | 0.478 | 0.835 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-rescored | +10 | LONDON | rk_pair | 0.498 [0.44,0.55] | 0.482 [0.41,0.56] | - | 0.519 | 0.536 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +60 | LONDON | X4stack:logit2 | 0.480 [0.43,0.53] | 0.481 [0.41,0.55] | - | 0.489 | 0.582 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-condtrained | +5 | NY | cc_gbt3 | 0.499 [0.43,0.57] | 0.479 [0.38,0.58] | - | 0.504 | 0.538 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +60 | NY | mt_pair | 0.527 [0.45,0.60] | 0.478 [0.38,0.58] | - | 0.494 | 0.671 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +15 | ASIA | mt_pair | 0.506 [0.46,0.55] | 0.477 [0.43,0.53] | - | 0.478 | 0.482 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +15 | NY | ctrl_gbt3 | 0.470 [0.39,0.54] | 0.476 [0.38,0.57] | - | 0.472 | 0.801 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | pre | POOLED | X5stack:gbt3 | 0.497 [0.47,0.52] | 0.476 [0.44,0.51] | - | 0.454 | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +30 | NY | cfree15 | 0.470 [0.40,0.54] | 0.474 [0.37,0.58] | - | 0.437 | 0.600 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +5 | NY | X4stack:gbt3 | 0.463 [0.39,0.53] | 0.472 [0.37,0.57] | - | 0.501 | 0.685 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +20 | NY | X4c:logit2 | 0.529 [0.46,0.59] | 0.472 [0.36,0.58] | - | 0.465 | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-rescored | pre | NY | X5stack:rf | 0.496 [0.43,0.57] | 0.471 [0.37,0.57] | - | 0.515 | 0.794 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | pre | NY | mt_pair | 0.524 [0.46,0.58] | 0.469 [0.36,0.57] | - | 0.475 | 0.654 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | pre | LONDON | cs_pair | 0.485 [0.43,0.54] | 0.468 [0.39,0.55] | - | 0.446 | 0.495 | N | - | - | - | - |  | locked label (reference only) |
| X45-rescored | +5 | LONDON | X45stack:logit2 | 0.512 [0.46,0.56] | 0.468 [0.39,0.55] | - | 0.437 | 0.632 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +60 | ASIA | mt_pair | 0.482 [0.43,0.53] | 0.468 [0.40,0.53] | - | 0.456 | 0.458 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +60 | LONDON | rk_pair | 0.498 [0.43,0.55] | 0.467 [0.39,0.55] | - | 0.433 | 0.564 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +60 | NY | rk_pair | 0.536 [0.46,0.61] | 0.465 [0.37,0.58] | - | 0.486 | 0.672 | ok | - | - | - | - |  | locked label (reference only) |
| X45-rescored | pre | LONDON | X45stack:logit2 | 0.517 [0.47,0.57] | 0.465 [0.39,0.53] | - | 0.422 | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| X45-condtrained | +20 | NY | X45c:logit2 | 0.524 [0.46,0.59] | 0.464 [0.34,0.57] | - | 0.478 | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-rescored | pre | NY | free30 | 0.488 [0.42,0.55] | 0.460 [0.37,0.55] | - | 0.479 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +45 | ASIA | prod_ll | 0.527 [0.47,0.57] | 0.457 [0.39,0.53] | - | 0.454 | 0.463 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +30 | NY | mt_pair | 0.512 [0.44,0.59] | 0.457 [0.34,0.57] | - | 0.438 | 0.660 | ok | - | - | - | - |  | locked label (reference only) |
| X2-rescored | +5 | POOLED | free30 | 0.463 [0.43,0.49] | 0.455 [0.41,0.50] | - | 0.447 | 0.623 | ok | - | - | - | - |  | locked label (reference only) |
| X3-condtrained | +60 | NY | cmt_logit2 | 0.506 [0.43,0.58] | 0.455 [0.35,0.57] | - | 0.466 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +10 | NY | cs_ll | 0.492 [0.43,0.56] | 0.455 [0.36,0.55] | - | 0.473 | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +5 | LONDON | X4stack:logit2 | 0.498 [0.45,0.55] | 0.454 [0.38,0.53] | - | 0.436 | 0.571 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-condtrained | +5 | LONDON | X4c:stack | 0.509 [0.46,0.56] | 0.453 [0.40,0.51] | - | 0.434 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | pre | NY | cfree30 | 0.509 [0.44,0.58] | 0.453 [0.34,0.55] | - | 0.449 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +10 | NY | mt_pair | 0.505 [0.44,0.57] | 0.452 [0.34,0.56] | - | 0.477 | 0.661 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | +5 | LONDON | X5stack:logit2 | 0.506 [0.45,0.56] | 0.451 [0.37,0.53] | - | 0.421 | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +5 | POOLED | ctrl_logit2 | 0.467 [0.44,0.50] | 0.447 [0.40,0.49] | - | 0.441 | 0.599 | ok | - | - | - | - |  | locked label (reference only) |
| X1-condtrained | pre | LONDON | cc_pair | 0.461 [0.41,0.51] | 0.447 [0.38,0.52] | - | 0.464 | 0.437 | N | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | +5 | NY | X4c:gbt3 | 0.472 [0.40,0.54] | 0.446 [0.36,0.55] | - | 0.456 | 0.522 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +5 | NY | mt_pair | 0.520 [0.45,0.58] | 0.443 [0.34,0.55] | - | 0.473 | 0.656 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | +5 | POOLED | X4stack:logit2 | 0.465 [0.44,0.49] | 0.441 [0.40,0.48] | - | 0.430 | 0.610 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +20 | NY | mt_pair | 0.497 [0.42,0.57] | 0.440 [0.33,0.56] | - | 0.444 | 0.657 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | +5 | LONDON | ctrl_logit2 | 0.502 [0.45,0.56] | 0.439 [0.36,0.51] | - | 0.432 | 0.528 | ok | - | - | - | - |  | locked label (reference only) |
| X1-rescored | +5 | LONDON | rk_xe | 0.477 [0.42,0.53] | 0.437 [0.37,0.52] | - | 0.439 | 0.578 | ok | - | - | - | - |  | locked label (reference only) |
| X4-condtrained | pre | NY | X4c:stack | 0.504 [0.44,0.56] | 0.437 [0.34,0.53] | - | 0.412 | 0.501 | ok | - | - | - | - | stack | locked label (reference only) |
| X3-rescored | +15 | NY | mt_pair | 0.499 [0.43,0.57] | 0.437 [0.32,0.56] | - | 0.435 | 0.650 | ok | - | - | - | - |  | locked label (reference only) |
| X4-rescored | pre | NY | X4stack:rf | 0.471 [0.40,0.53] | 0.431 [0.35,0.53] | - | 0.484 | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| X1-ctrl-uncond | +5 | NY | ctrl_logit2 | 0.460 [0.39,0.53] | 0.425 [0.31,0.55] | - | 0.478 | 0.606 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl-uncond | pre | NY | ctrl_gbt3 | 0.478 [0.41,0.53] | 0.423 [0.34,0.51] | - | 0.487 | 0.699 | ok | - | - | - | - |  | locked label (reference only) |
| X3-rescored | +45 | NY | mt_pair | 0.502 [0.42,0.58] | 0.411 [0.30,0.53] | - | 0.400 | 0.634 | ok | - | - | - | - |  | locked label (reference only) |
| X5-rescored | pre | LONDON | X5stack:gbt3 | 0.481 [0.43,0.53] | 0.405 [0.32,0.48] | - | 0.372 | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-condtrained | +10 | NY | cmono15 | 0.466 [0.40,0.53] | 0.404 [0.30,0.50] | - | 0.440 | 0.523 | N | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X1-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-ctrl-uncond 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X1-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X2-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X3-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X4-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X45-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-condtrained 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 0 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 0 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 0 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 0 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 5 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 5 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 5 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 5 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 10 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 10 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 10 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 10 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 15 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 15 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 15 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 15 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 20 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 20 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 20 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 20 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 30 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 30 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 30 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 30 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 45 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 45 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 45 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 45 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 60 ASIA: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 60 LONDON: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 60 NY: selected by WF-PRE conditional AUC; baseline R0c-B
- X5-rescored 60 POOLED: selected by WF-PRE conditional AUC; baseline R0c-B
