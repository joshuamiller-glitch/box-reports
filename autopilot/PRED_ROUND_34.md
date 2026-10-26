# PRED ROUND 34 - block X2 round 1 - X6-X10

Best HOLDOUT F-R AUC: +15 POOLED 0.590 [0.55,0.63] | ASIA 0.572 [0.51,0.64] | LONDON 0.559 [0.48,0.64] | NY 0.581 [0.48,0.69]
Best HOLDOUT F-R AUC: +30 POOLED 0.591 [0.55,0.64] | ASIA 0.559 [0.49,0.63] | LONDON 0.524 [0.45,0.60] | NY 0.568 [0.46,0.68]
Best G HOLDOUT AUC: 0.645 [0.61,0.68]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg b5df6b4cac8b9190ea37b2b951ee14a593278632a101040ad95dd5ce43ee37ae ; trials added 2700 ; truncation audit {'decisions': 1440, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X2_X6.parquet', 'l2vast/pred/store/X2_X10.parquet', 'l2vast/pred/store/X2_X6_sig.parquet', 'l2vast/pred/store/X2_X10_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X6-sibling-session-G | sig | ASIA/HM | gbt3 | 0.614 [0.58,0.65] | 0.645 [0.61,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA/HM | gbt3 | 0.607 [0.57,0.64] | 0.641 [0.60,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA | gbt3 | 0.600 [0.58,0.63] | 0.627 [0.60,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA/HM | gbt3 | 0.587 [0.56,0.62] | 0.624 [0.59,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | LONDON/ST | logit2 | 0.634 [0.59,0.68] | 0.618 [0.55,0.69] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA/ST | gbt3 | 0.594 [0.56,0.63] | 0.617 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED/ST | rf | 0.603 [0.58,0.63] | 0.616 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | POOLED/ST | gbt3 | 0.604 [0.58,0.63] | 0.616 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | ASIA | gbt3 | 0.587 [0.56,0.61] | 0.615 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON/ST | logit2 | 0.640 [0.60,0.69] | 0.614 [0.55,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | POOLED | gbt3 | 0.600 [0.58,0.62] | 0.613 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED | rf | 0.603 [0.58,0.62] | 0.613 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON/ST | logit2 | 0.636 [0.60,0.68] | 0.612 [0.54,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED/HM | rf | 0.603 [0.58,0.62] | 0.611 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON | logit2 | 0.630 [0.60,0.66] | 0.611 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON/HM | logit2 | 0.621 [0.58,0.66] | 0.610 [0.55,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA | gbt3 | 0.576 [0.55,0.60] | 0.609 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | NY | stack | 0.614 [0.57,0.65] | 0.608 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED/ST | rf | 0.597 [0.57,0.62] | 0.608 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | LONDON | logit2 | 0.622 [0.59,0.65] | 0.607 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | LONDON | gbt3 | 0.548 [0.49,0.60] | 0.605 [0.53,0.68] | - | 0.602 | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | NY/HM | rf | 0.616 [0.57,0.66] | 0.601 [0.53,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +45 | LONDON | logit2 | 0.524 [0.47,0.58] | 0.600 [0.53,0.67] | - | 0.593 | 0.631 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED | logit2 | 0.591 [0.57,0.61] | 0.599 [0.58,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | LONDON/HM | logit2 | 0.609 [0.57,0.65] | 0.599 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON | logit2 | 0.618 [0.59,0.65] | 0.598 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +5 | POOLED | gbt3 | 0.541 [0.51,0.57] | 0.598 [0.55,0.65] | - | 0.573 | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +60 | LONDON | gbt3 | 0.554 [0.49,0.62] | 0.597 [0.52,0.67] | - | 0.593 | 0.651 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA/ST | gbt3 | 0.568 [0.54,0.60] | 0.597 [0.56,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED/HM | logit2 | 0.586 [0.57,0.61] | 0.593 [0.57,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | ASIA/ST | gbt3 | 0.565 [0.53,0.60] | 0.593 [0.56,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | NY/ST | gbt3 | 0.591 [0.54,0.64] | 0.593 [0.52,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | POOLED/HM | logit2 | 0.586 [0.56,0.61] | 0.592 [0.56,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.591 [0.55,0.64] | - | 0.576 | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | POOLED | logit2 | 0.549 [0.52,0.58] | 0.590 [0.55,0.63] | - | 0.571 | 0.650 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | POOLED | logit2 | 0.546 [0.52,0.58] | 0.590 [0.55,0.64] | - | 0.567 | 0.651 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON/HM | logit2 | 0.601 [0.56,0.64] | 0.589 [0.54,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +20 | POOLED | rf | 0.550 [0.52,0.58] | 0.588 [0.54,0.63] | - | 0.561 | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +30 | POOLED | logit2 | 0.549 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.573 | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +10 | POOLED | rf | 0.553 [0.53,0.58] | 0.587 [0.54,0.63] | - | 0.554 | 0.659 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +45 | LONDON | logit2 | 0.528 [0.48,0.58] | 0.584 [0.52,0.66] | - | 0.583 | 0.631 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +10 | POOLED | rf | 0.554 [0.53,0.58] | 0.583 [0.54,0.63] | - | 0.550 | 0.660 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +20 | NY | rf | 0.558 [0.50,0.62] | 0.581 [0.47,0.68] | - | 0.593 | 0.820 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | NY | gbt3 | 0.545 [0.48,0.61] | 0.581 [0.48,0.69] | - | 0.567 | 0.740 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | NY | logit2 | 0.590 [0.56,0.62] | 0.580 [0.53,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +5 | POOLED | logit2 | 0.528 [0.50,0.56] | 0.579 [0.54,0.62] | - | 0.563 | 0.631 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | POOLED | logit2 | 0.556 [0.52,0.59] | 0.578 [0.53,0.63] | - | 0.560 | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +10 | POOLED | rf | 0.547 [0.52,0.58] | 0.577 [0.53,0.62] | - | 0.548 | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | NY/ST | gbt3 | 0.595 [0.54,0.64] | 0.576 [0.50,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | LONDON | logit2 | 0.561 [0.51,0.62] | 0.576 [0.50,0.66] | - | 0.545 | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | POOLED | logit2 | 0.542 [0.51,0.57] | 0.576 [0.53,0.62] | - | 0.557 | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | pre | POOLED | gbt3 | 0.538 [0.51,0.57] | 0.575 [0.53,0.62] | - | 0.548 | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | POOLED | gbt3 | 0.545 [0.52,0.57] | 0.575 [0.53,0.62] | - | 0.538 | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | NY | logit2 | 0.598 [0.56,0.63] | 0.574 [0.52,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | POOLED | rf | 0.536 [0.50,0.57] | 0.574 [0.53,0.62] | - | 0.556 | 0.634 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | ASIA | logit2 | 0.553 [0.51,0.60] | 0.572 [0.51,0.64] | - | 0.557 | 0.563 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | LONDON | logit2 | 0.528 [0.48,0.58] | 0.572 [0.50,0.65] | - | 0.545 | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | NY | rf | 0.564 [0.50,0.63] | 0.571 [0.46,0.68] | - | 0.592 | 0.820 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | NY/ST | gbt3 | 0.583 [0.53,0.63] | 0.569 [0.50,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | NY | logit2 | 0.543 [0.47,0.61] | 0.568 [0.46,0.68] | - | 0.606 | 0.708 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +45 | POOLED | rf | 0.544 [0.52,0.57] | 0.568 [0.53,0.61] | - | 0.544 | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +45 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.567 [0.49,0.64] | - | 0.545 | 0.557 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +5 | POOLED | rf | 0.533 [0.50,0.56] | 0.566 [0.52,0.61] | - | 0.531 | 0.614 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +45 | LONDON | gbt3 | 0.526 [0.47,0.58] | 0.566 [0.49,0.64] | - | 0.552 | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +45 | POOLED | rf | 0.546 [0.52,0.57] | 0.565 [0.53,0.61] | - | 0.541 | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.564 [0.51,0.62] | - | 0.532 | 0.604 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +5 | ASIA | logit2 | 0.542 [0.50,0.59] | 0.564 [0.50,0.63] | - | 0.557 | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | pre | ASIA | gbt3 | 0.542 [0.50,0.59] | 0.563 [0.50,0.63] | - | 0.546 | 0.568 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | POOLED | stack | 0.556 [0.53,0.59] | 0.562 [0.52,0.61] | - | 0.548 | 0.634 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +10 | POOLED | logit2 | 0.548 [0.52,0.58] | 0.562 [0.52,0.61] | - | 0.525 | 0.590 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +5 | ASIA | logit2 | 0.542 [0.50,0.59] | 0.561 [0.50,0.62] | - | 0.560 | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | POOLED | gbt3 | 0.549 [0.51,0.58] | 0.560 [0.52,0.60] | - | 0.532 | 0.649 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +20 | LONDON | logit2 | 0.517 [0.47,0.57] | 0.560 [0.49,0.64] | - | 0.536 | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | ASIA | gbt3 | 0.554 [0.51,0.60] | 0.560 [0.50,0.62] | - | 0.543 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +5 | NY | stack | 0.539 [0.48,0.61] | 0.559 [0.45,0.67] | - | 0.571 | 0.708 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | LONDON | logit2 | 0.499 [0.45,0.55] | 0.559 [0.48,0.64] | - | 0.579 | 0.607 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | ASIA | logit2 | 0.562 [0.52,0.61] | 0.559 [0.49,0.63] | - | 0.536 | 0.547 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | pre | NY | logit2 | 0.564 [0.50,0.63] | 0.558 [0.45,0.66] | - | 0.580 | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | POOLED | stack | 0.546 [0.52,0.58] | 0.558 [0.51,0.61] | - | 0.534 | 0.700 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | POOLED | gbt3 | 0.536 [0.51,0.56] | 0.557 [0.51,0.60] | - | 0.521 | 0.603 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +30 | POOLED | logit2 | 0.559 [0.53,0.59] | 0.557 [0.50,0.61] | - | 0.529 | 0.612 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +10 | LONDON | stack | 0.543 [0.49,0.60] | 0.557 [0.47,0.64] | - | 0.572 | 0.471 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +15 | NY | logit2 | 0.576 [0.51,0.65] | 0.556 [0.45,0.65] | - | 0.553 | 0.563 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +30 | NY | logit2 | 0.530 [0.46,0.60] | 0.555 [0.45,0.67] | - | 0.602 | 0.707 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | ASIA | gbt3 | 0.549 [0.51,0.59] | 0.555 [0.49,0.62] | - | 0.523 | 0.568 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | NY | gbt3 | 0.521 [0.45,0.60] | 0.555 [0.44,0.67] | - | 0.570 | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +10 | LONDON | stack | 0.517 [0.46,0.57] | 0.555 [0.48,0.63] | - | 0.518 | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | LONDON | logit2 | 0.507 [0.46,0.55] | 0.555 [0.48,0.63] | - | 0.577 | 0.598 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | POOLED | logit2 | 0.555 [0.52,0.59] | 0.554 [0.50,0.61] | - | 0.530 | 0.604 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +45 | POOLED | logit2 | 0.533 [0.50,0.57] | 0.554 [0.50,0.60] | - | 0.532 | 0.616 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +10 | POOLED | rf | 0.542 [0.51,0.58] | 0.553 [0.50,0.60] | - | 0.531 | 0.559 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality-G | sig | NY/HM | logit2 | 0.589 [0.54,0.64] | 0.553 [0.48,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +45 | POOLED | rf | 0.547 [0.52,0.57] | 0.553 [0.51,0.60] | - | 0.527 | 0.679 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | NY | logit2 | 0.556 [0.48,0.63] | 0.552 [0.42,0.67] | - | 0.551 | 0.575 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +60 | POOLED | logit2 | 0.532 [0.50,0.56] | 0.551 [0.51,0.59] | - | 0.536 | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | NY | stack | 0.537 [0.47,0.60] | 0.551 [0.44,0.65] | - | 0.543 | 0.787 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | ASIA | logit2 | 0.556 [0.51,0.60] | 0.549 [0.48,0.62] | - | 0.531 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +10 | LONDON | stack | 0.517 [0.46,0.57] | 0.549 [0.47,0.63] | - | 0.513 | 0.649 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | POOLED | rf | 0.541 [0.51,0.57] | 0.549 [0.51,0.59] | - | 0.532 | 0.700 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | LONDON | stack | 0.558 [0.51,0.61] | 0.549 [0.47,0.63] | - | 0.560 | 0.501 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +60 | NY | logit2 | 0.525 [0.46,0.60] | 0.549 [0.45,0.65] | - | 0.530 | 0.716 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | ASIA | stack | 0.558 [0.52,0.60] | 0.548 [0.48,0.61] | - | 0.528 | 0.570 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | POOLED | logit2 | 0.529 [0.50,0.56] | 0.547 [0.50,0.59] | - | 0.531 | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +10 | NY | logit2 | 0.531 [0.46,0.59] | 0.547 [0.44,0.65] | - | 0.493 | 0.512 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +60 | LONDON | stack | 0.529 [0.47,0.58] | 0.546 [0.47,0.62] | - | 0.540 | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON/ST | gbt3 | 0.548 [0.50,0.60] | 0.546 [0.47,0.62] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | LONDON | gbt3 | 0.508 [0.45,0.56] | 0.546 [0.46,0.63] | - | 0.521 | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | NY | logit2 | 0.523 [0.45,0.60] | 0.544 [0.44,0.65] | - | 0.530 | 0.716 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA/HM | gbt3 | 0.526 [0.49,0.56] | 0.543 [0.50,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | ASIA | gbt3 | 0.554 [0.51,0.60] | 0.542 [0.48,0.60] | - | 0.517 | 0.573 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | pre | LONDON | stack | 0.545 [0.48,0.60] | 0.542 [0.47,0.62] | - | 0.536 | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | NY/HM | logit2 | 0.594 [0.55,0.64] | 0.541 [0.46,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | POOLED | logit2 | 0.527 [0.49,0.56] | 0.540 [0.49,0.59] | - | 0.518 | 0.633 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +15 | POOLED | stack | 0.544 [0.52,0.57] | 0.540 [0.50,0.59] | - | 0.524 | 0.577 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +10 | ASIA | rf | 0.540 [0.49,0.59] | 0.539 [0.48,0.60] | - | 0.531 | 0.445 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | pre | ASIA | gbt3 | 0.560 [0.52,0.60] | 0.539 [0.48,0.59] | - | 0.518 | 0.586 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +15 | NY | stack | 0.537 [0.48,0.60] | 0.537 [0.43,0.63] | - | 0.556 | 0.768 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +45 | ASIA | logit2 | 0.555 [0.51,0.60] | 0.537 [0.47,0.61] | - | 0.524 | 0.588 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +30 | ASIA | logit2 | 0.534 [0.49,0.58] | 0.536 [0.47,0.60] | - | 0.524 | 0.564 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA/ST | logit2 | 0.519 [0.49,0.55] | 0.536 [0.50,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | ASIA | logit2 | 0.519 [0.49,0.55] | 0.535 [0.50,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +30 | POOLED | logit2 | 0.533 [0.50,0.56] | 0.533 [0.49,0.58] | - | 0.518 | 0.638 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | ASIA/ST | logit2 | 0.523 [0.49,0.56] | 0.533 [0.50,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | LONDON | stack | 0.530 [0.48,0.58] | 0.532 [0.46,0.61] | - | 0.521 | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | ASIA | rf | 0.558 [0.51,0.60] | 0.532 [0.46,0.60] | - | 0.508 | 0.587 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON | logit2 | 0.535 [0.50,0.57] | 0.532 [0.48,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | ASIA | logit2 | 0.547 [0.50,0.59] | 0.532 [0.46,0.60] | - | 0.507 | 0.549 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610-G | sig | LONDON/ST | logit2 | 0.528 [0.48,0.57] | 0.532 [0.47,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | ASIA | logit2 | 0.505 [0.45,0.55] | 0.532 [0.47,0.60] | - | 0.524 | 0.512 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | ASIA | stack | 0.541 [0.50,0.58] | 0.530 [0.46,0.59] | - | 0.530 | 0.546 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +45 | ASIA | logit2 | 0.548 [0.50,0.59] | 0.530 [0.47,0.60] | - | 0.527 | 0.569 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +10 | ASIA | gbt3 | 0.557 [0.52,0.60] | 0.529 [0.47,0.59] | - | 0.506 | 0.560 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality-G | sig | LONDON/HM | logit2 | 0.531 [0.49,0.58] | 0.528 [0.47,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +45 | POOLED | rf | 0.532 [0.50,0.56] | 0.528 [0.49,0.57] | - | 0.513 | 0.595 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +10 | NY | logit2 | 0.559 [0.50,0.62] | 0.527 [0.44,0.62] | - | 0.547 | 0.529 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +45 | ASIA | rf | 0.537 [0.49,0.58] | 0.526 [0.46,0.59] | - | 0.513 | 0.507 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +5 | ASIA | stack | 0.538 [0.50,0.58] | 0.526 [0.47,0.59] | - | 0.520 | 0.569 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610-G | sig | POOLED/ST | logit2 | 0.518 [0.49,0.54] | 0.526 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | NY | gbt3 | 0.560 [0.48,0.63] | 0.526 [0.42,0.63] | - | 0.497 | 0.590 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +15 | NY | rf | 0.511 [0.44,0.59] | 0.524 [0.42,0.63] | - | 0.522 | 0.685 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | LONDON | stack | 0.543 [0.49,0.60] | 0.524 [0.45,0.60] | - | 0.483 | 0.666 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | ASIA | logit2 | 0.520 [0.47,0.56] | 0.523 [0.46,0.59] | - | 0.516 | 0.473 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610-G | sig | POOLED | logit2 | 0.517 [0.50,0.54] | 0.523 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | LONDON | logit2 | 0.524 [0.49,0.56] | 0.522 [0.47,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | ASIA | logit2 | 0.523 [0.48,0.57] | 0.522 [0.45,0.59] | - | 0.517 | 0.513 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED/ST | logit2 | 0.515 [0.49,0.54] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | NY | gbt3 | 0.523 [0.46,0.60] | 0.521 [0.41,0.63] | - | 0.570 | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON/ST | logit2 | 0.525 [0.48,0.57] | 0.521 [0.45,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | POOLED | stack | 0.542 [0.51,0.57] | 0.521 [0.48,0.57] | - | 0.505 | 0.585 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +10 | NY | gbt3 | 0.523 [0.46,0.59] | 0.520 [0.43,0.62] | - | 0.565 | 0.750 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +45 | LONDON | rf | 0.517 [0.46,0.57] | 0.520 [0.44,0.60] | - | 0.518 | 0.515 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610-G | sig | POOLED/HM | logit2 | 0.516 [0.49,0.54] | 0.519 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED | logit2 | 0.513 [0.49,0.53] | 0.519 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | ASIA | rf | 0.533 [0.49,0.57] | 0.518 [0.46,0.58] | - | 0.489 | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | ASIA | stack | 0.522 [0.48,0.56] | 0.518 [0.45,0.58] | - | 0.504 | 0.529 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | LONDON | gbt3 | 0.480 [0.43,0.53] | 0.518 [0.43,0.59] | - | 0.489 | 0.541 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +5 | LONDON | stack | 0.505 [0.45,0.56] | 0.517 [0.44,0.59] | - | 0.520 | 0.603 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED | logit2 | 0.515 [0.50,0.53] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | NY | logit2 | 0.503 [0.44,0.57] | 0.517 [0.41,0.61] | - | 0.521 | 0.558 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | NY/ST | rf | 0.493 [0.44,0.54] | 0.517 [0.44,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | NY/ST | stack | 0.517 [0.47,0.56] | 0.517 [0.44,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | NY | rf | 0.515 [0.45,0.58] | 0.516 [0.41,0.62] | - | 0.516 | 0.535 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +30 | POOLED | stack | 0.527 [0.50,0.56] | 0.516 [0.47,0.56] | - | 0.476 | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | NY | stack | 0.513 [0.48,0.55] | 0.516 [0.46,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED/HM | rf | 0.516 [0.49,0.54] | 0.516 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +5 | NY | rf | 0.526 [0.47,0.59] | 0.516 [0.42,0.62] | - | 0.533 | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | POOLED | logit2 | 0.515 [0.49,0.54] | 0.515 [0.48,0.55] | - | 0.506 | 0.586 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +45 | ASIA | gbt3 | 0.540 [0.50,0.58] | 0.515 [0.45,0.58] | - | 0.493 | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | ASIA | stack | 0.542 [0.50,0.58] | 0.514 [0.45,0.58] | - | 0.493 | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON | logit2 | 0.515 [0.48,0.55] | 0.514 [0.46,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | LONDON | logit2 | 0.503 [0.45,0.56] | 0.514 [0.43,0.60] | - | 0.517 | 0.558 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +60 | ASIA | logit2 | 0.538 [0.49,0.58] | 0.514 [0.45,0.58] | - | 0.496 | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | LONDON | logit2 | 0.529 [0.48,0.58] | 0.513 [0.43,0.59] | - | 0.520 | 0.582 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | LONDON | stack | 0.524 [0.47,0.58] | 0.513 [0.44,0.59] | - | 0.494 | 0.597 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | LONDON/HM | logit2 | 0.518 [0.47,0.56] | 0.513 [0.46,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +60 | ASIA | logit2 | 0.533 [0.49,0.58] | 0.513 [0.45,0.58] | - | 0.494 | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +45 | NY | rf | 0.512 [0.44,0.58] | 0.512 [0.42,0.60] | - | 0.503 | 0.738 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +20 | ASIA | gbt3 | 0.521 [0.48,0.57] | 0.512 [0.45,0.58] | - | 0.490 | 0.559 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +10 | LONDON | stack | 0.531 [0.48,0.58] | 0.512 [0.44,0.59] | - | 0.503 | 0.685 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | NY | logit2 | 0.536 [0.46,0.61] | 0.512 [0.41,0.61] | - | 0.487 | 0.580 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA/HM | stack | 0.514 [0.48,0.55] | 0.511 [0.46,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | ASIA | stack | 0.544 [0.51,0.58] | 0.511 [0.45,0.57] | - | 0.501 | 0.471 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +60 | ASIA | stack | 0.541 [0.49,0.59] | 0.511 [0.45,0.57] | - | 0.479 | 0.518 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | LONDON/HM | logit2 | 0.506 [0.46,0.55] | 0.510 [0.45,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | POOLED | logit2 | 0.526 [0.50,0.56] | 0.510 [0.46,0.56] | - | 0.497 | 0.541 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +20 | ASIA | stack | 0.520 [0.48,0.56] | 0.510 [0.44,0.57] | - | 0.480 | 0.556 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +30 | ASIA | rf | 0.541 [0.50,0.58] | 0.510 [0.44,0.58] | - | 0.481 | 0.538 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | POOLED/ST | gbt3 | 0.513 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA | logit2 | 0.502 [0.47,0.53] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | POOLED | gbt3 | 0.515 [0.49,0.54] | 0.508 [0.46,0.55] | - | 0.497 | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +10 | NY | rf | 0.532 [0.47,0.59] | 0.508 [0.41,0.60] | - | 0.533 | 0.747 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +5 | LONDON | stack | 0.510 [0.46,0.56] | 0.506 [0.44,0.57] | - | 0.490 | 0.600 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +45 | LONDON | logit2 | 0.498 [0.44,0.55] | 0.505 [0.43,0.58] | - | 0.511 | 0.550 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +10 | ASIA | rf | 0.551 [0.51,0.59] | 0.505 [0.45,0.57] | - | 0.477 | 0.550 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +15 | ASIA | stack | 0.518 [0.48,0.56] | 0.503 [0.45,0.55] | - | 0.491 | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +5 | NY | rf | 0.525 [0.47,0.58] | 0.502 [0.40,0.59] | - | 0.458 | 0.574 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +10 | ASIA | rf | 0.551 [0.50,0.60] | 0.501 [0.44,0.57] | - | 0.479 | 0.556 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | LONDON | gbt3 | 0.503 [0.45,0.56] | 0.500 [0.42,0.58] | - | 0.482 | 0.492 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | NY | rf | 0.508 [0.47,0.55] | 0.499 [0.44,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | ASIA/ST | gbt3 | 0.501 [0.47,0.53] | 0.498 [0.45,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +60 | LONDON | gbt3 | 0.497 [0.45,0.55] | 0.498 [0.42,0.58] | - | 0.501 | 0.470 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +60 | NY | rf | 0.539 [0.47,0.61] | 0.498 [0.41,0.59] | - | 0.495 | 0.864 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +15 | NY | stack | 0.522 [0.46,0.58] | 0.497 [0.41,0.58] | - | 0.454 | 0.561 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +10 | NY | logit2 | 0.531 [0.47,0.60] | 0.497 [0.40,0.59] | - | 0.508 | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | NY | rf | 0.514 [0.47,0.55] | 0.496 [0.43,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | ASIA | rf | 0.510 [0.47,0.55] | 0.495 [0.44,0.55] | - | 0.486 | 0.483 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +30 | LONDON | stack | 0.519 [0.47,0.58] | 0.494 [0.41,0.58] | - | 0.478 | 0.672 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +45 | NY | stack | 0.513 [0.44,0.59] | 0.494 [0.40,0.59] | - | 0.463 | 0.738 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality-G | sig | NY/HM | rf | 0.521 [0.47,0.58] | 0.493 [0.42,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | NY | rf | 0.549 [0.48,0.61] | 0.492 [0.38,0.61] | - | 0.504 | 0.705 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | LONDON | logit2 | 0.522 [0.47,0.57] | 0.490 [0.41,0.57] | - | 0.471 | 0.550 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | POOLED/HM | stack | 0.508 [0.48,0.53] | 0.490 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +30 | NY | gbt3 | 0.544 [0.48,0.61] | 0.490 [0.39,0.59] | - | 0.503 | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +30 | LONDON | stack | 0.503 [0.45,0.56] | 0.490 [0.41,0.58] | - | 0.473 | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | pre | LONDON | stack | 0.513 [0.46,0.57] | 0.489 [0.40,0.57] | - | 0.474 | 0.650 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.489 [0.43,0.56] | - | 0.485 | 0.497 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +10 | ASIA | rf | 0.515 [0.47,0.56] | 0.486 [0.43,0.55] | - | 0.473 | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +5 | LONDON | logit2 | 0.532 [0.48,0.58] | 0.486 [0.41,0.57] | - | 0.463 | 0.459 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610-G | sig | NY/ST | logit2 | 0.502 [0.45,0.56] | 0.485 [0.41,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +45 | NY | gbt3 | 0.510 [0.45,0.58] | 0.485 [0.39,0.59] | - | 0.473 | 0.547 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +20 | NY | logit2 | 0.530 [0.47,0.59] | 0.484 [0.37,0.58] | - | 0.480 | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +30 | POOLED | gbt3 | 0.514 [0.48,0.54] | 0.483 [0.44,0.53] | - | 0.471 | 0.585 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +20 | LONDON | logit2 | 0.506 [0.45,0.56] | 0.481 [0.40,0.57] | - | 0.463 | 0.547 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | NY/HM | rf | 0.525 [0.47,0.58] | 0.477 [0.40,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +15 | LONDON | logit2 | 0.490 [0.44,0.55] | 0.477 [0.40,0.56] | - | 0.452 | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | pre | NY | gbt3 | 0.523 [0.45,0.59] | 0.476 [0.37,0.58] | - | 0.504 | 0.691 | ok | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | +10 | LONDON | logit2 | 0.478 [0.43,0.53] | 0.476 [0.40,0.56] | - | 0.456 | 0.548 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +45 | NY | stack | 0.509 [0.44,0.58] | 0.476 [0.38,0.57] | - | 0.472 | 0.796 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610 | +30 | LONDON | logit2 | 0.504 [0.44,0.56] | 0.474 [0.39,0.55] | - | 0.468 | 0.552 | ok | - | - | - | - | stack | locked label (reference only) |
| combo-X610-G | sig | NY/HM | rf | 0.522 [0.47,0.58] | 0.474 [0.40,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session | pre | NY | stack | 0.510 [0.45,0.57] | 0.472 [0.39,0.57] | - | 0.448 | 0.588 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session-G | sig | ASIA/HM | stack | 0.510 [0.47,0.55] | 0.471 [0.42,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X6-sibling-session-G | sig | ASIA | stack | 0.503 [0.47,0.54] | 0.470 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X10-trend-quality | +20 | LONDON | stack | 0.526 [0.47,0.58] | 0.466 [0.40,0.53] | - | 0.462 | 0.546 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | pre | NY | gbt3 | 0.492 [0.43,0.56] | 0.465 [0.38,0.54] | - | 0.477 | 0.521 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +60 | NY | gbt3 | 0.493 [0.42,0.56] | 0.464 [0.37,0.57] | - | 0.458 | 0.604 | ok | - | - | - | - |  | locked label (reference only) |
| X10-trend-quality | +30 | LONDON | stack | 0.515 [0.46,0.57] | 0.463 [0.38,0.55] | - | 0.460 | 0.555 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +5 | LONDON | gbt3 | 0.458 [0.40,0.52] | 0.455 [0.38,0.54] | - | 0.432 | 0.569 | ok | - | - | - | - |  | locked label (reference only) |
| X6-sibling-session | +45 | NY | gbt3 | 0.500 [0.44,0.57] | 0.445 [0.36,0.53] | - | 0.448 | 0.585 | ok | - | - | - | - |  | locked label (reference only) |
| combo-X610 | +30 | NY | logit2 | 0.482 [0.42,0.56] | 0.429 [0.33,0.53] | - | 0.435 | 0.733 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X6-sibling-session 0 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.437; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.449; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.486; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.487; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.491; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 LONDON: run X2_r1c_X6; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 POOLED: run X2_r1c_X6; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.559; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.564; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.567; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 ASIA: run X2_r1c_X6; model chosen by cond WF-PRE 0.568; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.572; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.574; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 NY: run X2_r1c_X6; model chosen by cond WF-PRE 0.584; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.494; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.529; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 POOLED: run X2_r1c_X10; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 LONDON: run X2_r1c_X10; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 ASIA: run X2_r1c_X10; model chosen by cond WF-PRE 0.554; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 NY: run X2_r1c_X10; model chosen by cond WF-PRE 0.581; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.436; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.456; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.479; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.488; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.492; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 LONDON: run X2_r1c_X6b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 POOLED: run X2_r1c_X6b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.535; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 5 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 60 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 30 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.547; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 15 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 10 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 45 ASIA: run X2_r1c_X6b; model chosen by cond WF-PRE 0.563; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 20 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.564; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session 0 NY: run X2_r1c_X6b; model chosen by cond WF-PRE 0.579; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.478; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.494; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 5 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 10 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 30 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 POOLED: run X2_r1c_X10b; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 15 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 LONDON: run X2_r1c_X10b; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 0 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.555; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 45 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.560; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 20 NY: run X2_r1c_X10b; model chosen by cond WF-PRE 0.564; econ/CPCV not run (cond pre AUC<0.60)
- X10-trend-quality 60 ASIA: run X2_r1c_X10b; model chosen by cond WF-PRE 0.569; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 10 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.467; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.473; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 45 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.476; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 5 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.482; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 20 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 20 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.492; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 5 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 0 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 60 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 45 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 20 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 60 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 5 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 60 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 0 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 10 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 45 POOLED: run X2_r1c_X610b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 0 LONDON: run X2_r1c_X610b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 20 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 5 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.546; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 60 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 10 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 10 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.565; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 45 ASIA: run X2_r1c_X610b; model chosen by cond WF-PRE 0.565; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 0 NY: run X2_r1c_X610b; model chosen by cond WF-PRE 0.574; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 NY: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 ASIA: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 NY: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 ASIA: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 LONDON: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 30 POOLED: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.529; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 LONDON: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- combo-X610 15 POOLED: run X2_r1c_X610pt; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 ASIA: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 POOLED: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 NY: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X6-sibling-session-G -1 LONDON: FAILPRED feats + X6 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 ASIA: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 POOLED: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 NY: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X10-trend-quality-G -1 LONDON: FAILPRED feats + X10 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 ASIA: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 POOLED: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 NY: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-X610-G -1 LONDON: FAILPRED feats + X610 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
