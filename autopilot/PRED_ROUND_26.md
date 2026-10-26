# PRED ROUND 26 - block X1 round 2 - X2+X4+X5

Best HOLDOUT F-R AUC: +15 POOLED 0.541 [0.49,0.58] | ASIA 0.546 [0.49,0.61] | LONDON 0.596 [0.52,0.67] | NY 0.589 [0.49,0.68]
Best HOLDOUT F-R AUC: +30 POOLED 0.558 [0.52,0.60] | ASIA 0.559 [0.50,0.62] | LONDON 0.571 [0.50,0.64] | NY 0.594 [0.48,0.69]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg eb0e21a8ef788ca8e4848138babc30512330c6778fbd3e0bf8c9ffa2c5b8c0ee ; trials added 1500 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False, 'source': 'X_r2_feat audit 360 decisions (X4,X5); X2 inherits FAILPRED R9'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X4X5-stack | +20 | NY | X45stack:stack | 0.559 [0.49,0.62] | 0.651 [0.56,0.74] | - | 0.644 | 0.862 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +45 | LONDON | X4stack:rf | 0.549 [0.50,0.60] | 0.640 [0.55,0.72] | - | 0.640 | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +20 | NY | X5stack:stack | 0.547 [0.48,0.61] | 0.624 [0.54,0.71] | - | 0.628 | 0.872 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +45 | NY | mono30 | 0.527 [0.45,0.60] | 0.617 [0.52,0.71] | - | 0.603 | 0.675 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +60 | NY | X4stack:stack | 0.545 [0.47,0.62] | 0.615 [0.51,0.71] | - | 0.619 | 0.876 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +60 | LONDON | mono30 | 0.522 [0.46,0.58] | 0.614 [0.53,0.69] | - | 0.602 | 0.629 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +20 | NY | X4stack:stack | 0.534 [0.46,0.61] | 0.606 [0.50,0.71] | - | 0.600 | 0.837 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +15 | LONDON | mono15 | 0.552 [0.50,0.61] | 0.596 [0.52,0.67] | - | 0.568 | 0.615 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +30 | NY | free15 | 0.548 [0.47,0.62] | 0.594 [0.48,0.69] | - | 0.589 | 0.675 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +15 | NY | X45stack:stack | 0.530 [0.46,0.59] | 0.589 [0.49,0.68] | - | 0.606 | 0.807 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +45 | ASIA | mono30 | 0.553 [0.51,0.59] | 0.588 [0.53,0.64] | - | 0.573 | 0.552 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +60 | LONDON | free30 | 0.518 [0.46,0.57] | 0.587 [0.52,0.65] | - | 0.579 | 0.609 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +15 | LONDON | X4stack:rf | 0.545 [0.50,0.60] | 0.586 [0.51,0.67] | - | 0.556 | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +20 | NY | X5only:gbt3 | 0.563 [0.49,0.63] | 0.585 [0.48,0.69] | - | 0.594 | 0.803 | N | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +20 | LONDON | mono30 | 0.534 [0.48,0.58] | 0.582 [0.51,0.66] | - | 0.537 | 0.617 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +45 | NY | free30 | 0.511 [0.44,0.58] | 0.581 [0.48,0.67] | - | 0.564 | 0.635 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +45 | LONDON | mono30 | 0.533 [0.48,0.58] | 0.578 [0.50,0.65] | - | 0.570 | 0.605 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +45 | ASIA | X45stack:logit2 | 0.547 [0.50,0.59] | 0.577 [0.52,0.63] | - | 0.561 | 0.570 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +15 | LONDON | free30 | 0.524 [0.47,0.58] | 0.574 [0.49,0.65] | - | 0.558 | 0.637 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +30 | LONDON | mono30 | 0.534 [0.48,0.58] | 0.571 [0.50,0.64] | - | 0.555 | 0.606 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +45 | LONDON | X5only:rf | 0.513 [0.46,0.57] | 0.567 [0.48,0.64] | - | 0.557 | 0.711 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +30 | LONDON | free15 | 0.541 [0.49,0.59] | 0.567 [0.49,0.65] | - | 0.543 | 0.601 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +45 | NY | X4stack:gbt3 | 0.525 [0.45,0.59] | 0.564 [0.46,0.66] | - | 0.543 | 0.799 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +10 | NY | X4stack:stack | 0.516 [0.45,0.58] | 0.564 [0.48,0.65] | - | 0.586 | 0.769 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +30 | NY | mono15 | 0.536 [0.47,0.60] | 0.563 [0.45,0.67] | - | 0.562 | 0.663 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +45 | POOLED | mono30 | 0.530 [0.50,0.56] | 0.562 [0.51,0.61] | - | 0.548 | 0.656 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | pre | LONDON | free30 | 0.550 [0.50,0.60] | 0.562 [0.47,0.64] | - | 0.552 | 0.673 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +20 | NY | mono15 | 0.518 [0.45,0.58] | 0.561 [0.47,0.66] | - | 0.539 | 0.672 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +15 | NY | free30 | 0.498 [0.43,0.56] | 0.559 [0.46,0.66] | - | 0.516 | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +30 | ASIA | X4stack:gbt3 | 0.533 [0.49,0.57] | 0.559 [0.50,0.62] | - | 0.556 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +30 | ASIA | mono15 | 0.547 [0.50,0.59] | 0.559 [0.50,0.62] | - | 0.544 | 0.540 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +10 | LONDON | mono15 | 0.523 [0.47,0.57] | 0.559 [0.50,0.63] | - | 0.518 | 0.589 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +30 | NY | X45stack:rf | 0.503 [0.42,0.58] | 0.559 [0.45,0.67] | - | 0.557 | 0.814 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | pre | LONDON | mono30 | 0.533 [0.48,0.59] | 0.558 [0.48,0.64] | - | 0.533 | 0.649 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +30 | POOLED | X5stack:rf | 0.515 [0.49,0.55] | 0.558 [0.52,0.60] | - | 0.546 | 0.712 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +45 | POOLED | X4stack:rf | 0.522 [0.49,0.55] | 0.557 [0.51,0.60] | - | 0.548 | 0.684 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +30 | ASIA | X4only:stack | 0.570 [0.53,0.61] | 0.556 [0.50,0.61] | - | 0.543 | 0.547 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +15 | NY | X5stack:stack | 0.512 [0.44,0.57] | 0.556 [0.46,0.65] | - | 0.583 | 0.811 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +30 | NY | X4stack:rf | 0.487 [0.41,0.56] | 0.555 [0.44,0.68] | - | 0.564 | 0.793 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +60 | POOLED | mono15 | 0.531 [0.50,0.56] | 0.555 [0.51,0.59] | - | 0.544 | 0.657 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +20 | LONDON | free30 | 0.518 [0.47,0.57] | 0.554 [0.48,0.63] | - | 0.512 | 0.614 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +10 | NY | X45stack:rf | 0.515 [0.45,0.58] | 0.554 [0.46,0.64] | - | 0.594 | 0.780 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +10 | LONDON | X4stack:gbt3 | 0.513 [0.47,0.56] | 0.553 [0.48,0.63] | - | 0.550 | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +5 | ASIA | X5stack:gbt3 | 0.549 [0.51,0.59] | 0.552 [0.50,0.61] | - | 0.542 | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +45 | NY | X5stack:gbt3 | 0.525 [0.45,0.60] | 0.551 [0.45,0.66] | - | 0.548 | 0.821 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +60 | NY | X45stack:gbt3 | 0.517 [0.44,0.59] | 0.551 [0.45,0.65] | - | 0.561 | 0.857 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +30 | NY | X5stack:rf | 0.486 [0.41,0.56] | 0.550 [0.43,0.67] | - | 0.566 | 0.818 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +10 | NY | X4only:stack | 0.464 [0.39,0.54] | 0.550 [0.47,0.65] | - | 0.551 | 0.682 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +45 | ASIA | free15 | 0.535 [0.49,0.58] | 0.549 [0.49,0.60] | - | 0.532 | 0.526 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | pre | NY | X5only:logit2 | 0.524 [0.46,0.59] | 0.547 [0.46,0.63] | - | 0.572 | 0.800 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +5 | NY | X4only:logit2 | 0.485 [0.42,0.55] | 0.547 [0.46,0.64] | - | 0.488 | 0.649 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | pre | ASIA | X5stack:gbt3 | 0.558 [0.52,0.60] | 0.546 [0.49,0.61] | - | 0.520 | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +15 | ASIA | mono15 | 0.561 [0.52,0.60] | 0.546 [0.49,0.61] | - | 0.534 | 0.536 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +60 | NY | mono30 | 0.502 [0.43,0.57] | 0.545 [0.45,0.65] | - | 0.535 | 0.662 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +5 | ASIA | mono30 | 0.541 [0.50,0.58] | 0.544 [0.48,0.61] | - | 0.527 | 0.544 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +30 | ASIA | X5stack:rf | 0.539 [0.50,0.58] | 0.544 [0.49,0.60] | - | 0.535 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +45 | POOLED | free30 | 0.518 [0.48,0.55] | 0.544 [0.49,0.59] | - | 0.533 | 0.637 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +60 | NY | free30 | 0.508 [0.43,0.58] | 0.543 [0.45,0.65] | - | 0.521 | 0.649 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +20 | NY | free15 | 0.533 [0.46,0.60] | 0.543 [0.44,0.64] | - | 0.521 | 0.654 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +60 | ASIA | mono15 | 0.535 [0.49,0.58] | 0.543 [0.49,0.60] | - | 0.517 | 0.519 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +45 | NY | X45stack:gbt3 | 0.516 [0.45,0.58] | 0.541 [0.43,0.65] | - | 0.533 | 0.817 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +30 | POOLED | X45stack:rf | 0.509 [0.48,0.54] | 0.541 [0.50,0.59] | - | 0.529 | 0.701 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +15 | POOLED | X4stack:rf | 0.515 [0.48,0.55] | 0.541 [0.49,0.58] | - | 0.525 | 0.692 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +60 | LONDON | X5stack:rf | 0.488 [0.44,0.54] | 0.541 [0.46,0.61] | - | 0.541 | 0.723 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +5 | ASIA | free30 | 0.545 [0.50,0.59] | 0.541 [0.48,0.61] | - | 0.528 | 0.542 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | pre | ASIA | mono30 | 0.532 [0.49,0.57] | 0.540 [0.48,0.60] | - | 0.503 | 0.538 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +10 | ASIA | mono30 | 0.556 [0.51,0.60] | 0.540 [0.48,0.61] | - | 0.523 | 0.530 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +30 | POOLED | mono15 | 0.526 [0.49,0.56] | 0.540 [0.49,0.59] | - | 0.520 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +60 | POOLED | free30 | 0.518 [0.49,0.55] | 0.540 [0.50,0.58] | - | 0.534 | 0.651 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +30 | LONDON | X4only:gbt3 | 0.519 [0.46,0.58] | 0.539 [0.46,0.61] | - | 0.533 | 0.580 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +30 | ASIA | X5only:gbt3 | 0.518 [0.47,0.56] | 0.539 [0.47,0.61] | - | 0.545 | 0.538 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +5 | ASIA | X45stack:gbt3 | 0.545 [0.51,0.58] | 0.539 [0.48,0.60] | - | 0.531 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +20 | LONDON | X5stack:logit2 | 0.515 [0.47,0.56] | 0.539 [0.47,0.61] | - | 0.536 | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | pre | ASIA | X4stack:rf | 0.553 [0.51,0.59] | 0.538 [0.48,0.60] | - | 0.517 | 0.536 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +15 | ASIA | X4stack:rf | 0.548 [0.50,0.59] | 0.538 [0.48,0.60] | - | 0.527 | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +10 | NY | free30 | 0.489 [0.42,0.56] | 0.538 [0.44,0.65] | - | 0.553 | 0.658 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +10 | ASIA | X5stack:stack | 0.557 [0.52,0.60] | 0.538 [0.48,0.59] | - | 0.537 | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +20 | POOLED | X5stack:rf | 0.498 [0.47,0.52] | 0.537 [0.50,0.58] | - | 0.526 | 0.706 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +45 | LONDON | free15 | 0.498 [0.44,0.55] | 0.537 [0.45,0.62] | - | 0.512 | 0.578 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +15 | NY | mono15 | 0.492 [0.42,0.56] | 0.536 [0.44,0.64] | - | 0.492 | 0.645 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +45 | ASIA | X4stack:rf | 0.531 [0.49,0.57] | 0.536 [0.48,0.59] | - | 0.520 | 0.519 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +15 | NY | X4stack:rf | 0.498 [0.43,0.56] | 0.534 [0.44,0.62] | - | 0.521 | 0.783 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +10 | ASIA | X4stack:gbt3 | 0.552 [0.51,0.60] | 0.534 [0.47,0.60] | - | 0.525 | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +20 | LONDON | X5only:rf | 0.496 [0.45,0.55] | 0.534 [0.46,0.61] | - | 0.506 | 0.686 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | pre | ASIA | X45stack:rf | 0.548 [0.51,0.59] | 0.533 [0.47,0.60] | - | 0.515 | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +15 | POOLED | mono15 | 0.515 [0.49,0.54] | 0.533 [0.49,0.58] | - | 0.510 | 0.643 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +20 | ASIA | X4stack:stack | 0.542 [0.49,0.59] | 0.533 [0.47,0.60] | - | 0.531 | 0.517 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +30 | POOLED | free15 | 0.519 [0.49,0.55] | 0.533 [0.48,0.58] | - | 0.516 | 0.637 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +60 | LONDON | X4only:stack | 0.495 [0.44,0.55] | 0.533 [0.44,0.61] | - | 0.533 | 0.623 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +5 | NY | X45stack:rf | 0.496 [0.43,0.56] | 0.532 [0.43,0.63] | - | 0.521 | 0.764 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +20 | POOLED | X4stack:stack | 0.508 [0.48,0.54] | 0.532 [0.48,0.58] | - | 0.525 | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +45 | ASIA | X5stack:gbt3 | 0.518 [0.47,0.56] | 0.532 [0.46,0.60] | - | 0.510 | 0.522 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +60 | POOLED | X5stack:rf | 0.497 [0.47,0.53] | 0.532 [0.49,0.57] | - | 0.530 | 0.722 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +60 | ASIA | X5stack:stack | 0.509 [0.46,0.55] | 0.532 [0.48,0.58] | - | 0.531 | 0.534 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +30 | POOLED | X4stack:rf | 0.501 [0.47,0.53] | 0.531 [0.49,0.58] | - | 0.521 | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +10 | NY | mono30 | 0.480 [0.41,0.55] | 0.530 [0.44,0.62] | - | 0.557 | 0.644 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +45 | NY | X5only:rf | 0.505 [0.44,0.57] | 0.530 [0.42,0.63] | - | 0.559 | 0.824 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +20 | POOLED | X45stack:stack | 0.511 [0.48,0.54] | 0.529 [0.48,0.57] | - | 0.517 | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +30 | ASIA | free15 | 0.518 [0.47,0.56] | 0.529 [0.47,0.59] | - | 0.518 | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +5 | LONDON | mono30 | 0.517 [0.47,0.57] | 0.529 [0.47,0.60] | - | 0.513 | 0.622 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +15 | POOLED | X45stack:rf | 0.514 [0.48,0.55] | 0.528 [0.48,0.57] | - | 0.515 | 0.694 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +60 | ASIA | X4only:rf | 0.540 [0.49,0.59] | 0.528 [0.46,0.60] | - | 0.530 | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +5 | ASIA | X4stack:gbt3 | 0.537 [0.50,0.57] | 0.527 [0.47,0.59] | - | 0.517 | 0.524 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +60 | POOLED | X4stack:rf | 0.495 [0.46,0.53] | 0.527 [0.48,0.58] | - | 0.529 | 0.704 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +60 | LONDON | X5only:rf | 0.524 [0.47,0.58] | 0.527 [0.44,0.61] | - | 0.537 | 0.701 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +30 | LONDON | X4stack:gbt3 | 0.502 [0.44,0.56] | 0.526 [0.43,0.62] | - | 0.506 | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | pre | ASIA | X4only:rf | 0.559 [0.51,0.60] | 0.526 [0.47,0.59] | - | 0.516 | 0.528 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +60 | ASIA | free30 | 0.531 [0.48,0.58] | 0.525 [0.47,0.58] | - | 0.514 | 0.527 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +15 | ASIA | X4only:rf | 0.545 [0.50,0.59] | 0.525 [0.46,0.59] | - | 0.518 | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +5 | ASIA | X4only:logit2 | 0.534 [0.49,0.58] | 0.525 [0.46,0.59] | - | 0.507 | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +45 | POOLED | X45stack:gbt3 | 0.504 [0.47,0.54] | 0.524 [0.47,0.58] | - | 0.519 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +20 | LONDON | X4only:gbt3 | 0.521 [0.47,0.57] | 0.523 [0.44,0.60] | - | 0.508 | 0.568 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +15 | LONDON | X4only:rf | 0.514 [0.46,0.57] | 0.523 [0.44,0.60] | - | 0.497 | 0.570 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +10 | LONDON | free30 | 0.525 [0.47,0.57] | 0.522 [0.45,0.59] | - | 0.532 | 0.591 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +30 | ASIA | X45stack:rf | 0.525 [0.48,0.57] | 0.521 [0.46,0.58] | - | 0.507 | 0.504 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +45 | POOLED | X5stack:gbt3 | 0.499 [0.47,0.53] | 0.520 [0.47,0.57] | - | 0.511 | 0.695 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +20 | ASIA | X5stack:rf | 0.524 [0.48,0.57] | 0.520 [0.46,0.58] | - | 0.508 | 0.500 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +5 | NY | X5stack:rf | 0.496 [0.43,0.56] | 0.520 [0.42,0.62] | - | 0.495 | 0.768 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +30 | POOLED | X5only:rf | 0.482 [0.45,0.51] | 0.520 [0.47,0.57] | - | 0.525 | 0.696 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +20 | ASIA | X45stack:stack | 0.536 [0.49,0.58] | 0.519 [0.45,0.59] | - | 0.512 | 0.500 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +20 | POOLED | mono15 | 0.507 [0.48,0.53] | 0.517 [0.48,0.56] | - | 0.494 | 0.640 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +10 | ASIA | X45stack:rf | 0.546 [0.51,0.59] | 0.517 [0.46,0.57] | - | 0.505 | 0.512 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | pre | ASIA | free30 | 0.514 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.481 | 0.518 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +30 | POOLED | X4only:logit2 | 0.515 [0.48,0.54] | 0.516 [0.48,0.56] | - | 0.503 | 0.649 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +10 | POOLED | X4stack:rf | 0.500 [0.47,0.53] | 0.516 [0.47,0.56] | - | 0.502 | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +15 | POOLED | free30 | 0.500 [0.47,0.53] | 0.515 [0.47,0.56] | - | 0.509 | 0.645 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +15 | POOLED | X5stack:rf | 0.496 [0.47,0.53] | 0.515 [0.47,0.56] | - | 0.493 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +10 | ASIA | free15 | 0.553 [0.51,0.60] | 0.515 [0.45,0.58] | - | 0.499 | 0.507 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +45 | ASIA | X4only:gbt3 | 0.536 [0.50,0.58] | 0.515 [0.46,0.57] | - | 0.528 | 0.525 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +60 | LONDON | X45stack:rf | 0.480 [0.42,0.53] | 0.514 [0.43,0.59] | - | 0.512 | 0.703 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +45 | POOLED | X4only:rf | 0.508 [0.48,0.54] | 0.514 [0.46,0.56] | - | 0.514 | 0.669 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +15 | ASIA | X45stack:rf | 0.544 [0.50,0.59] | 0.514 [0.45,0.57] | - | 0.504 | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +20 | POOLED | X5only:rf | 0.500 [0.47,0.53] | 0.514 [0.46,0.56] | - | 0.518 | 0.687 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +15 | LONDON | X5stack:gbt3 | 0.486 [0.43,0.54] | 0.513 [0.44,0.59] | - | 0.488 | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +45 | LONDON | X4only:rf | 0.516 [0.47,0.57] | 0.513 [0.43,0.58] | - | 0.519 | 0.609 | N | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +20 | ASIA | mono15 | 0.536 [0.49,0.58] | 0.512 [0.45,0.57] | - | 0.494 | 0.497 | ok | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +10 | POOLED | X45stack:rf | 0.504 [0.48,0.53] | 0.512 [0.47,0.55] | - | 0.500 | 0.679 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +60 | ASIA | X4stack:stack | 0.492 [0.44,0.54] | 0.512 [0.45,0.58] | - | 0.509 | 0.502 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +60 | POOLED | X45stack:rf | 0.489 [0.46,0.52] | 0.512 [0.47,0.55] | - | 0.512 | 0.713 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +30 | LONDON | X45stack:gbt3 | 0.498 [0.44,0.56] | 0.511 [0.42,0.60] | - | 0.485 | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +30 | LONDON | X5only:rf | 0.468 [0.42,0.52] | 0.511 [0.42,0.59] | - | 0.480 | 0.687 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +10 | NY | X5stack:rf | 0.491 [0.42,0.56] | 0.511 [0.41,0.60] | - | 0.561 | 0.767 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +30 | LONDON | X5stack:logit2 | 0.524 [0.47,0.58] | 0.510 [0.43,0.60] | - | 0.497 | 0.630 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +10 | ASIA | X4only:logit2 | 0.554 [0.51,0.59] | 0.509 [0.44,0.57] | - | 0.490 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +5 | POOLED | X45stack:rf | 0.493 [0.46,0.52] | 0.508 [0.46,0.55] | - | 0.491 | 0.678 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +60 | POOLED | X4only:rf | 0.497 [0.46,0.53] | 0.508 [0.46,0.55] | - | 0.507 | 0.665 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +60 | ASIA | X45stack:stack | 0.490 [0.45,0.54] | 0.508 [0.45,0.56] | - | 0.509 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +20 | ASIA | X4only:rf | 0.557 [0.52,0.60] | 0.507 [0.45,0.56] | - | 0.505 | 0.514 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +45 | POOLED | X5only:gbt3 | 0.505 [0.47,0.53] | 0.507 [0.46,0.55] | - | 0.517 | 0.696 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +10 | POOLED | X5stack:rf | 0.499 [0.47,0.53] | 0.506 [0.46,0.55] | - | 0.501 | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +45 | LONDON | X45stack:gbt3 | 0.487 [0.44,0.54] | 0.506 [0.42,0.60] | - | 0.518 | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +15 | NY | X5only:stack | 0.520 [0.45,0.58] | 0.505 [0.40,0.61] | - | 0.520 | 0.767 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | pre | LONDON | X4stack:logit2 | 0.526 [0.47,0.58] | 0.505 [0.42,0.59] | - | 0.471 | 0.601 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +5 | NY | X4stack:stack | 0.468 [0.40,0.53] | 0.505 [0.41,0.60] | - | 0.539 | 0.692 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | +15 | LONDON | X45stack:stack | 0.524 [0.47,0.58] | 0.504 [0.42,0.59] | - | 0.483 | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +20 | POOLED | free15 | 0.501 [0.47,0.53] | 0.503 [0.46,0.54] | - | 0.490 | 0.620 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +15 | ASIA | X5stack:rf | 0.533 [0.49,0.58] | 0.502 [0.44,0.56] | - | 0.493 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +15 | ASIA | free30 | 0.521 [0.47,0.57] | 0.501 [0.44,0.56] | - | 0.502 | 0.500 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +10 | LONDON | X5stack:logit2 | 0.514 [0.47,0.56] | 0.498 [0.42,0.58] | - | 0.484 | 0.660 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +10 | POOLED | mono30 | 0.487 [0.46,0.52] | 0.497 [0.45,0.54] | - | 0.483 | 0.623 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +60 | LONDON | X4stack:rf | 0.478 [0.43,0.53] | 0.497 [0.41,0.58] | - | 0.493 | 0.659 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +45 | LONDON | X5stack:gbt3 | 0.469 [0.41,0.52] | 0.496 [0.42,0.57] | - | 0.509 | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| X4X5-stack | pre | POOLED | X45stack:rf | 0.501 [0.47,0.53] | 0.493 [0.45,0.53] | - | 0.469 | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +45 | ASIA | X5only:gbt3 | 0.510 [0.47,0.56] | 0.491 [0.42,0.56] | - | 0.505 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +20 | POOLED | X4only:rf | 0.494 [0.46,0.52] | 0.491 [0.45,0.53] | - | 0.482 | 0.628 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +5 | NY | X5only:logit2 | 0.536 [0.47,0.60] | 0.491 [0.39,0.60] | - | 0.468 | 0.707 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +60 | POOLED | X5only:rf | 0.510 [0.48,0.54] | 0.490 [0.45,0.53] | - | 0.505 | 0.687 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +5 | POOLED | X5stack:rf | 0.485 [0.46,0.51] | 0.490 [0.45,0.53] | - | 0.473 | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +15 | POOLED | X4only:stack | 0.502 [0.47,0.53] | 0.490 [0.44,0.53] | - | 0.473 | 0.613 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | pre | POOLED | free30 | 0.485 [0.45,0.51] | 0.489 [0.44,0.54] | - | 0.475 | 0.651 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +10 | POOLED | free30 | 0.492 [0.47,0.52] | 0.488 [0.44,0.53] | - | 0.480 | 0.619 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +10 | POOLED | X4only:stack | 0.497 [0.47,0.53] | 0.487 [0.44,0.53] | - | 0.464 | 0.606 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +5 | POOLED | X4only:logit2 | 0.492 [0.46,0.52] | 0.487 [0.45,0.53] | - | 0.463 | 0.607 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +5 | ASIA | X5only:rf | 0.520 [0.48,0.57] | 0.487 [0.43,0.55] | - | 0.481 | 0.480 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +20 | ASIA | free15 | 0.512 [0.47,0.55] | 0.486 [0.43,0.55] | - | 0.478 | 0.467 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | pre | ASIA | X5only:rf | 0.524 [0.48,0.57] | 0.486 [0.42,0.56] | - | 0.480 | 0.483 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +15 | LONDON | X5only:rf | 0.487 [0.44,0.54] | 0.486 [0.41,0.55] | - | 0.470 | 0.659 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +10 | LONDON | X5only:rf | 0.495 [0.45,0.54] | 0.485 [0.41,0.55] | - | 0.459 | 0.667 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | pre | NY | X45stack:rf | 0.508 [0.44,0.58] | 0.485 [0.38,0.58] | - | 0.511 | 0.790 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | pre | LONDON | X4only:rf | 0.492 [0.44,0.54] | 0.484 [0.40,0.56] | - | 0.462 | 0.496 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +20 | ASIA | X5only:logit2 | 0.536 [0.49,0.58] | 0.484 [0.42,0.54] | - | 0.489 | 0.484 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +5 | POOLED | X5only:rf | 0.500 [0.47,0.53] | 0.483 [0.44,0.53] | - | 0.478 | 0.657 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +5 | LONDON | X4only:rf | 0.491 [0.45,0.54] | 0.482 [0.41,0.56] | - | 0.460 | 0.514 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | +60 | NY | X5stack:stack | 0.477 [0.40,0.55] | 0.482 [0.38,0.58] | - | 0.478 | 0.835 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | pre | POOLED | X5stack:rf | 0.490 [0.46,0.52] | 0.482 [0.44,0.52] | - | 0.463 | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | pre | POOLED | X5only:rf | 0.497 [0.47,0.52] | 0.481 [0.44,0.52] | - | 0.481 | 0.659 | N | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | pre | POOLED | mono30 | 0.474 [0.45,0.50] | 0.480 [0.44,0.52] | - | 0.467 | 0.643 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +15 | ASIA | X5only:logit2 | 0.520 [0.47,0.56] | 0.480 [0.42,0.54] | - | 0.479 | 0.474 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | pre | POOLED | X4stack:rf | 0.487 [0.46,0.51] | 0.479 [0.44,0.52] | - | 0.463 | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | pre | POOLED | X4only:rf | 0.491 [0.46,0.52] | 0.478 [0.43,0.52] | - | 0.465 | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +15 | POOLED | X5only:rf | 0.488 [0.46,0.52] | 0.477 [0.44,0.52] | - | 0.479 | 0.663 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +30 | NY | X5only:rf | 0.442 [0.37,0.51] | 0.477 [0.38,0.57] | - | 0.485 | 0.802 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +20 | LONDON | X4stack:gbt3 | 0.486 [0.44,0.54] | 0.476 [0.41,0.55] | - | 0.456 | 0.641 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-monotone-gbm | +5 | NY | mono30 | 0.461 [0.40,0.53] | 0.474 [0.38,0.57] | - | 0.471 | 0.637 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +10 | POOLED | X5only:rf | 0.492 [0.46,0.52] | 0.472 [0.43,0.52] | - | 0.472 | 0.657 | N | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | +5 | POOLED | mono30 | 0.465 [0.43,0.49] | 0.471 [0.43,0.51] | - | 0.466 | 0.632 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-state | pre | NY | X5stack:rf | 0.496 [0.43,0.57] | 0.471 [0.37,0.57] | - | 0.515 | 0.794 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +15 | NY | X4only:gbt3 | 0.458 [0.39,0.52] | 0.469 [0.36,0.57] | - | 0.460 | 0.684 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +60 | NY | X5only:rf | 0.494 [0.43,0.56] | 0.465 [0.37,0.57] | - | 0.480 | 0.748 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | pre | LONDON | X45stack:logit2 | 0.517 [0.47,0.57] | 0.465 [0.39,0.53] | - | 0.422 | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +10 | ASIA | X5only:logit2 | 0.524 [0.48,0.57] | 0.464 [0.40,0.53] | - | 0.461 | 0.461 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +5 | NY | free30 | 0.464 [0.40,0.53] | 0.461 [0.37,0.56] | - | 0.469 | 0.640 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +60 | ASIA | X5only:rf | 0.500 [0.45,0.55] | 0.460 [0.39,0.53] | - | 0.476 | 0.467 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +10 | LONDON | X4only:rf | 0.472 [0.42,0.53] | 0.460 [0.37,0.55] | - | 0.432 | 0.541 | N | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | pre | NY | free30 | 0.488 [0.42,0.55] | 0.460 [0.37,0.55] | - | 0.479 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X2-ctrl | +5 | LONDON | free30 | 0.476 [0.42,0.53] | 0.459 [0.39,0.54] | - | 0.433 | 0.608 | ok | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | +5 | LONDON | X5only:rf | 0.479 [0.43,0.53] | 0.458 [0.39,0.54] | - | 0.449 | 0.638 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +10 | LONDON | X45stack:rf | 0.483 [0.43,0.54] | 0.458 [0.38,0.54] | - | 0.452 | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density | +5 | POOLED | X4stack:rf | 0.461 [0.43,0.49] | 0.456 [0.41,0.50] | - | 0.447 | 0.632 | ok | - | - | - | - | stack | locked label (reference only) |
| X2-ctrl | +5 | POOLED | free30 | 0.463 [0.43,0.49] | 0.455 [0.41,0.50] | - | 0.447 | 0.623 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | +5 | LONDON | X4stack:logit2 | 0.498 [0.45,0.55] | 0.454 [0.38,0.53] | - | 0.436 | 0.571 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | +5 | LONDON | X5stack:logit2 | 0.506 [0.45,0.56] | 0.451 [0.37,0.53] | - | 0.421 | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-only | +10 | NY | X5only:rf | 0.495 [0.43,0.57] | 0.451 [0.36,0.55] | - | 0.494 | 0.731 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | pre | NY | X4only:gbt3 | 0.466 [0.40,0.53] | 0.448 [0.35,0.55] | - | 0.448 | 0.551 | N | - | - | - | - |  | locked label (reference only) |
| X5-trade-path-only | pre | LONDON | X5only:rf | 0.477 [0.43,0.53] | 0.447 [0.38,0.52] | - | 0.424 | 0.623 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +20 | LONDON | X45stack:gbt3 | 0.474 [0.43,0.53] | 0.445 [0.37,0.52] | - | 0.437 | 0.643 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +60 | NY | X4only:rf | 0.454 [0.38,0.54] | 0.438 [0.31,0.56] | - | 0.458 | 0.785 | N | - | - | - | - |  | locked label (reference only) |
| X2-monotone-gbm | pre | NY | mono30 | 0.463 [0.40,0.52] | 0.437 [0.36,0.52] | - | 0.450 | 0.680 | ok | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +30 | NY | X4only:logit2 | 0.450 [0.39,0.51] | 0.432 [0.33,0.53] | - | 0.448 | 0.735 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density | pre | NY | X4stack:rf | 0.471 [0.40,0.53] | 0.431 [0.35,0.53] | - | 0.484 | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| X4-signal-density-only | +45 | NY | X4only:gbt3 | 0.453 [0.38,0.53] | 0.431 [0.33,0.53] | - | 0.451 | 0.781 | N | - | - | - | - |  | locked label (reference only) |
| X4-signal-density-only | +20 | NY | X4only:logit2 | 0.412 [0.35,0.48] | 0.429 [0.33,0.53] | - | 0.450 | 0.666 | N | - | - | - | - |  | locked label (reference only) |
| X4X5-stack | +5 | LONDON | X45stack:rf | 0.475 [0.42,0.53] | 0.417 [0.35,0.49] | - | 0.407 | 0.624 | ok | - | - | - | - | stack | locked label (reference only) |
| X5-trade-path-state | pre | LONDON | X5stack:gbt3 | 0.481 [0.43,0.53] | 0.405 [0.32,0.48] | - | 0.372 | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X2-monotone-gbm 0 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 0 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 0 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 0 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 5 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 5 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 5 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 5 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 10 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 10 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 10 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 10 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 15 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 15 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 15 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 15 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 20 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 20 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 20 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 20 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 30 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 30 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 30 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 30 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 45 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 45 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 45 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 45 NY: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 60 POOLED: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 60 ASIA: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 60 LONDON: selected by WF-PRE AUC among mono30,mono15
- X2-monotone-gbm 60 NY: selected by WF-PRE AUC among mono30,mono15
- X4-signal-density 0 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 0 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 0 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 0 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 5 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 5 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 5 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 5 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 10 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 10 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 10 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 10 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 15 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 15 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 15 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 15 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 20 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 20 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 20 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 20 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 30 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 30 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 30 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 30 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 45 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 45 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 45 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 45 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 60 POOLED: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 60 ASIA: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 60 LONDON: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X4-signal-density 60 NY: selected by WF-PRE AUC among X4stack:logit2,X4stack:gbt3,X4stack:rf,X4stack:stack
- X5-trade-path-state 0 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 0 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 0 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 0 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 5 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 5 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 5 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 5 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 10 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 10 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 10 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 10 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 15 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 15 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 15 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 15 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 20 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 20 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 20 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 20 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 30 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 30 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 30 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 30 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 45 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 45 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 45 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 45 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 60 POOLED: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 60 ASIA: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 60 LONDON: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X5-trade-path-state 60 NY: selected by WF-PRE AUC among X5stack:logit2,X5stack:gbt3,X5stack:rf,X5stack:stack
- X4X5-stack 0 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 0 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 0 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 0 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 5 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 5 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 5 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 5 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 10 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 10 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 10 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 10 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 15 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 15 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 15 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 15 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 20 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 20 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 20 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 20 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 30 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 30 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 30 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 30 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 45 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 45 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 45 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 45 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 60 POOLED: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 60 ASIA: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 60 LONDON: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4X5-stack 60 NY: selected by WF-PRE AUC among X45stack:logit2,X45stack:gbt3,X45stack:rf,X45stack:stack
- X4-signal-density-only 0 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 0 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 0 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 0 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 5 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 5 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 5 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 5 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 10 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 10 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 10 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 10 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 15 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 15 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 15 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 15 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 20 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 20 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 20 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 20 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 30 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 30 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 30 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 30 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 45 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 45 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 45 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 45 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 60 POOLED: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 60 ASIA: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 60 LONDON: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X4-signal-density-only 60 NY: selected by WF-PRE AUC among X4only:logit2,X4only:gbt3,X4only:rf,X4only:stack
- X5-trade-path-only 0 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 0 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 0 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 0 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 5 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 5 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 5 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 5 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 10 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 10 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 10 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 10 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 15 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 15 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 15 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 15 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 20 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 20 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 20 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 20 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 30 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 30 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 30 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 30 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 45 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 45 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 45 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 45 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 60 POOLED: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 60 ASIA: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 60 LONDON: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X5-trade-path-only 60 NY: selected by WF-PRE AUC among X5only:logit2,X5only:gbt3,X5only:rf,X5only:stack
- X2-ctrl 0 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 0 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 0 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 0 NY: control: unconstrained GBM on identical columns
- X2-ctrl 5 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 5 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 5 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 5 NY: control: unconstrained GBM on identical columns
- X2-ctrl 10 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 10 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 10 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 10 NY: control: unconstrained GBM on identical columns
- X2-ctrl 15 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 15 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 15 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 15 NY: control: unconstrained GBM on identical columns
- X2-ctrl 20 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 20 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 20 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 20 NY: control: unconstrained GBM on identical columns
- X2-ctrl 30 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 30 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 30 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 30 NY: control: unconstrained GBM on identical columns
- X2-ctrl 45 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 45 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 45 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 45 NY: control: unconstrained GBM on identical columns
- X2-ctrl 60 POOLED: control: unconstrained GBM on identical columns
- X2-ctrl 60 ASIA: control: unconstrained GBM on identical columns
- X2-ctrl 60 LONDON: control: unconstrained GBM on identical columns
- X2-ctrl 60 NY: control: unconstrained GBM on identical columns
