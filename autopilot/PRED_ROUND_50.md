# PRED ROUND 50 - block X2 round 3 - X26-X30

Best HOLDOUT F-R AUC: +15 POOLED 0.596 [0.56,0.64] | ASIA 0.532 [0.46,0.60] | LONDON 0.606 [0.53,0.68] | NY 0.613 [0.52,0.71]
Best HOLDOUT F-R AUC: +30 POOLED 0.582 [0.54,0.63] | ASIA 0.546 [0.48,0.60] | LONDON 0.545 [0.45,0.63] | NY 0.554 [0.45,0.66]
Best G HOLDOUT AUC: 0.640 [0.60,0.68]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 08bbb9d176888ae0a024bba9fc965ff270900fd8a8ef383f3cf20b8d24f8de2d ; trials added 3200 ; truncation audit {'decisions': 3600, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X2_X26.parquet', 'l2vast/pred/store/X2_X27.parquet', 'l2vast/pred/store/X2_X28.parquet', 'l2vast/pred/store/X2_X29.parquet', 'l2vast/pred/store/X2_X30.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X27-compression-G | sig | ASIA/HM | gbt3 | 0.606 [0.57,0.64] | 0.640 [0.60,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | LONDON/ST | logit2 | 0.649 [0.61,0.69] | 0.630 [0.56,0.70] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA/HM | gbt3 | 0.605 [0.57,0.64] | 0.629 [0.58,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON/ST | rf | 0.647 [0.60,0.69] | 0.627 [0.56,0.70] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA/HM | rf | 0.595 [0.56,0.63] | 0.627 [0.58,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | ASIA/HM | gbt3 | 0.610 [0.58,0.64] | 0.626 [0.59,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | LONDON | logit2 | 0.640 [0.61,0.67] | 0.625 [0.57,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | LONDON/HM | logit2 | 0.632 [0.59,0.67] | 0.625 [0.57,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +60 | LONDON | gbt3 | 0.578 [0.52,0.64] | 0.625 [0.55,0.70] | - | 0.635 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | POOLED/ST | gbt3 | 0.611 [0.59,0.63] | 0.622 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | LONDON | gbt3 | 0.553 [0.50,0.61] | 0.621 [0.55,0.68] | - | 0.617 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA | gbt3 | 0.582 [0.55,0.61] | 0.620 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | ASIA | gbt3 | 0.595 [0.57,0.62] | 0.618 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | POOLED/HM | rf | 0.602 [0.58,0.62] | 0.618 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | ASIA | gbt3 | 0.587 [0.56,0.61] | 0.618 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | POOLED | gbt3 | 0.607 [0.59,0.62] | 0.617 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED/HM | rf | 0.604 [0.58,0.62] | 0.616 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA/HM | stack | 0.595 [0.57,0.62] | 0.616 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA | gbt3 | 0.584 [0.56,0.61] | 0.615 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | ASIA/ST | gbt3 | 0.584 [0.56,0.61] | 0.615 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED/HM | rf | 0.601 [0.58,0.62] | 0.615 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY/ST | logit2 | 0.607 [0.56,0.65] | 0.614 [0.55,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | NY | stack | 0.553 [0.49,0.61] | 0.613 [0.52,0.71] | - | 0.591 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | POOLED/HM | gbt3 | 0.604 [0.58,0.62] | 0.613 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | NY | rf | 0.599 [0.53,0.66] | 0.613 [0.51,0.71] | - | 0.637 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY/ST | logit2 | 0.603 [0.56,0.65] | 0.613 [0.55,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | POOLED/ST | gbt3 | 0.604 [0.58,0.63] | 0.612 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED/ST | gbt3 | 0.604 [0.58,0.63] | 0.612 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED/HM | rf | 0.600 [0.58,0.62] | 0.611 [0.58,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED | rf | 0.599 [0.58,0.61] | 0.611 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | NY | gbt3 | 0.609 [0.57,0.65] | 0.611 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +5 | NY | logit2 | 0.557 [0.50,0.62] | 0.610 [0.52,0.70] | - | 0.617 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED | rf | 0.602 [0.58,0.62] | 0.610 [0.59,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +10 | LONDON | gbt3 | 0.533 [0.48,0.59] | 0.609 [0.53,0.69] | - | 0.612 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA/ST | gbt3 | 0.574 [0.54,0.60] | 0.609 [0.57,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +20 | LONDON | logit2 | 0.559 [0.51,0.61] | 0.608 [0.54,0.68] | - | 0.600 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED | gbt3 | 0.597 [0.58,0.61] | 0.607 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +10 | LONDON | rf | 0.517 [0.46,0.57] | 0.607 [0.53,0.68] | - | 0.578 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | LONDON/ST | logit2 | 0.638 [0.60,0.68] | 0.607 [0.54,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED/ST | gbt3 | 0.596 [0.58,0.62] | 0.606 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED/ST | rf | 0.600 [0.57,0.63] | 0.606 [0.57,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | pre | NY | logit2 | 0.547 [0.48,0.61] | 0.606 [0.52,0.70] | - | 0.614 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +15 | LONDON | gbt3 | 0.560 [0.51,0.61] | 0.606 [0.53,0.68] | - | 0.589 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA/ST | gbt3 | 0.567 [0.54,0.60] | 0.606 [0.57,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON/ST | logit2 | 0.633 [0.59,0.68] | 0.605 [0.54,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | NY | logit2 | 0.609 [0.58,0.64] | 0.604 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA | stack | 0.581 [0.56,0.61] | 0.604 [0.58,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON/ST | logit2 | 0.636 [0.59,0.68] | 0.603 [0.53,0.68] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON/HM | logit2 | 0.610 [0.57,0.65] | 0.602 [0.55,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | LONDON | logit2 | 0.623 [0.59,0.65] | 0.602 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON | logit2 | 0.623 [0.59,0.65] | 0.601 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | LONDON | gbt3 | 0.550 [0.50,0.60] | 0.601 [0.52,0.67] | - | 0.592 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | ASIA/ST | gbt3 | 0.571 [0.54,0.60] | 0.601 [0.56,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA/ST | gbt3 | 0.566 [0.54,0.59] | 0.600 [0.56,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +20 | LONDON | logit2 | 0.562 [0.51,0.61] | 0.599 [0.52,0.67] | - | 0.581 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON | logit2 | 0.620 [0.59,0.65] | 0.599 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | LONDON/HM | logit2 | 0.608 [0.57,0.65] | 0.598 [0.54,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +20 | LONDON | logit2 | 0.550 [0.50,0.60] | 0.598 [0.52,0.67] | - | 0.570 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | POOLED | logit2 | 0.546 [0.52,0.57] | 0.596 [0.56,0.64] | - | 0.577 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON | logit2 | 0.621 [0.59,0.65] | 0.596 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +5 | POOLED | gbt3 | 0.555 [0.52,0.58] | 0.596 [0.55,0.64] | - | 0.570 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON/HM | logit2 | 0.606 [0.57,0.64] | 0.595 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY | logit2 | 0.604 [0.57,0.64] | 0.595 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | POOLED | logit2 | 0.592 [0.58,0.61] | 0.594 [0.57,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | LONDON | gbt3 | 0.565 [0.51,0.62] | 0.594 [0.51,0.66] | - | 0.601 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +10 | LONDON | rf | 0.519 [0.47,0.57] | 0.594 [0.51,0.67] | - | 0.567 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +60 | POOLED | gbt3 | 0.564 [0.53,0.60] | 0.593 [0.55,0.64] | - | 0.582 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +10 | POOLED | rf | 0.562 [0.53,0.59] | 0.592 [0.54,0.64] | - | 0.567 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON/HM | logit2 | 0.608 [0.57,0.65] | 0.592 [0.54,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +45 | LONDON | stack | 0.540 [0.48,0.60] | 0.592 [0.52,0.66] | - | 0.569 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +10 | LONDON | stack | 0.573 [0.53,0.62] | 0.592 [0.53,0.65] | - | 0.572 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +5 | POOLED | gbt3 | 0.541 [0.51,0.57] | 0.591 [0.55,0.64] | - | 0.569 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +45 | LONDON | rf | 0.537 [0.48,0.59] | 0.591 [0.52,0.66] | - | 0.578 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +10 | POOLED | rf | 0.551 [0.52,0.58] | 0.590 [0.54,0.64] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +10 | POOLED | rf | 0.563 [0.53,0.59] | 0.590 [0.54,0.64] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | POOLED | gbt3 | 0.555 [0.53,0.58] | 0.589 [0.55,0.63] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY | logit2 | 0.599 [0.57,0.63] | 0.589 [0.54,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +10 | POOLED | rf | 0.564 [0.54,0.59] | 0.589 [0.54,0.63] | - | 0.561 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | NY/ST | gbt3 | 0.599 [0.55,0.64] | 0.588 [0.53,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | NY/ST | gbt3 | 0.601 [0.55,0.65] | 0.588 [0.52,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +20 | LONDON | logit2 | 0.550 [0.50,0.60] | 0.587 [0.51,0.67] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +5 | POOLED | gbt3 | 0.539 [0.51,0.57] | 0.587 [0.54,0.63] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | LONDON | logit2 | 0.550 [0.50,0.61] | 0.586 [0.51,0.67] | - | 0.549 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +60 | NY | logit2 | 0.535 [0.46,0.62] | 0.585 [0.49,0.68] | - | 0.590 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | POOLED | logit2 | 0.532 [0.50,0.56] | 0.585 [0.55,0.63] | - | 0.571 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY | logit2 | 0.599 [0.57,0.64] | 0.585 [0.54,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | NY/HM | logit2 | 0.607 [0.56,0.66] | 0.584 [0.51,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +20 | POOLED | logit2 | 0.553 [0.52,0.59] | 0.584 [0.54,0.63] | - | 0.568 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +5 | ASIA | gbt3 | 0.554 [0.51,0.60] | 0.584 [0.53,0.64] | - | 0.568 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | POOLED | rf | 0.551 [0.52,0.58] | 0.583 [0.54,0.63] | - | 0.554 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +10 | POOLED | rf | 0.558 [0.53,0.59] | 0.583 [0.54,0.63] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | LONDON | logit2 | 0.549 [0.50,0.60] | 0.582 [0.51,0.66] | - | 0.547 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | POOLED | logit2 | 0.539 [0.51,0.57] | 0.582 [0.54,0.63] | - | 0.569 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | POOLED | rf | 0.565 [0.54,0.59] | 0.582 [0.54,0.63] | - | 0.559 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | POOLED | logit2 | 0.553 [0.52,0.58] | 0.580 [0.53,0.63] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +45 | LONDON | stack | 0.580 [0.53,0.64] | 0.580 [0.50,0.66] | - | 0.546 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +30 | POOLED | logit2 | 0.539 [0.51,0.57] | 0.580 [0.54,0.62] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | POOLED | logit2 | 0.540 [0.51,0.57] | 0.580 [0.54,0.63] | - | 0.564 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | POOLED | rf | 0.553 [0.52,0.58] | 0.579 [0.53,0.63] | - | 0.557 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +10 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.579 [0.54,0.63] | - | 0.559 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +20 | POOLED | logit2 | 0.557 [0.53,0.59] | 0.578 [0.53,0.63] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | pre | POOLED | gbt3 | 0.549 [0.52,0.58] | 0.578 [0.54,0.62] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | pre | POOLED | rf | 0.552 [0.52,0.58] | 0.577 [0.53,0.63] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +20 | POOLED | logit2 | 0.554 [0.52,0.59] | 0.577 [0.53,0.62] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | POOLED | logit2 | 0.546 [0.51,0.58] | 0.577 [0.53,0.62] | - | 0.558 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | POOLED | gbt3 | 0.550 [0.52,0.58] | 0.577 [0.53,0.62] | - | 0.571 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +45 | LONDON | stack | 0.550 [0.49,0.61] | 0.576 [0.49,0.66] | - | 0.547 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | POOLED | logit2 | 0.546 [0.52,0.57] | 0.576 [0.53,0.62] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +30 | POOLED | logit2 | 0.542 [0.51,0.57] | 0.576 [0.53,0.62] | - | 0.561 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | pre | ASIA | rf | 0.555 [0.51,0.60] | 0.575 [0.51,0.64] | - | 0.561 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +20 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.575 [0.53,0.62] | - | 0.557 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +60 | LONDON | rf | 0.528 [0.47,0.58] | 0.573 [0.50,0.65] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY/HM | logit2 | 0.602 [0.55,0.65] | 0.573 [0.50,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +60 | LONDON | gbt3 | 0.542 [0.49,0.59] | 0.572 [0.50,0.64] | - | 0.580 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | NY | rf | 0.555 [0.48,0.63] | 0.572 [0.47,0.67] | - | 0.590 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | POOLED | stack | 0.550 [0.52,0.58] | 0.572 [0.52,0.61] | - | 0.558 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +45 | POOLED | rf | 0.558 [0.53,0.59] | 0.571 [0.53,0.61] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | LONDON | logit2 | 0.524 [0.46,0.58] | 0.571 [0.49,0.65] | - | 0.554 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +5 | NY | stack | 0.530 [0.47,0.60] | 0.571 [0.48,0.66] | - | 0.586 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +10 | LONDON | gbt3 | 0.516 [0.46,0.57] | 0.571 [0.48,0.65] | - | 0.562 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | ASIA | rf | 0.528 [0.48,0.57] | 0.570 [0.51,0.63] | - | 0.563 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +5 | POOLED | logit2 | 0.523 [0.49,0.55] | 0.569 [0.53,0.61] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | LONDON | stack | 0.547 [0.50,0.60] | 0.569 [0.51,0.64] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +45 | POOLED | rf | 0.552 [0.52,0.58] | 0.568 [0.53,0.61] | - | 0.544 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +45 | LONDON | rf | 0.526 [0.47,0.58] | 0.568 [0.49,0.64] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | NY | logit2 | 0.528 [0.47,0.59] | 0.568 [0.46,0.66] | - | 0.536 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | NY | gbt3 | 0.536 [0.47,0.60] | 0.568 [0.47,0.66] | - | 0.575 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +45 | POOLED | rf | 0.557 [0.53,0.58] | 0.567 [0.52,0.61] | - | 0.540 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY/HM | logit2 | 0.600 [0.55,0.65] | 0.566 [0.49,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | NY/HM | logit2 | 0.597 [0.55,0.64] | 0.565 [0.49,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +45 | POOLED | rf | 0.556 [0.53,0.58] | 0.565 [0.53,0.61] | - | 0.544 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | pre | POOLED | rf | 0.539 [0.51,0.57] | 0.565 [0.52,0.61] | - | 0.547 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | pre | POOLED | gbt3 | 0.540 [0.51,0.57] | 0.565 [0.53,0.60] | - | 0.539 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | POOLED | rf | 0.563 [0.54,0.59] | 0.565 [0.53,0.60] | - | 0.540 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | pre | NY | logit2 | 0.539 [0.47,0.60] | 0.564 [0.46,0.67] | - | 0.519 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +60 | POOLED | gbt3 | 0.545 [0.51,0.58] | 0.564 [0.52,0.61] | - | 0.548 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +45 | LONDON | stack | 0.580 [0.53,0.63] | 0.564 [0.49,0.64] | - | 0.541 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | pre | ASIA | logit2 | 0.550 [0.50,0.60] | 0.564 [0.50,0.62] | - | 0.552 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | pre | POOLED | rf | 0.543 [0.51,0.57] | 0.564 [0.52,0.61] | - | 0.547 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | LONDON | stack | 0.527 [0.48,0.58] | 0.564 [0.49,0.64] | - | 0.520 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | NY | rf | 0.539 [0.47,0.61] | 0.564 [0.46,0.66] | - | 0.575 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +5 | LONDON | stack | 0.576 [0.52,0.63] | 0.563 [0.49,0.63] | - | 0.540 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +45 | POOLED | rf | 0.555 [0.53,0.58] | 0.562 [0.52,0.60] | - | 0.538 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY/ST | gbt3 | 0.580 [0.53,0.63] | 0.561 [0.49,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | pre | NY | logit2 | 0.538 [0.48,0.60] | 0.561 [0.46,0.65] | - | 0.593 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +5 | ASIA | rf | 0.534 [0.49,0.58] | 0.561 [0.50,0.61] | - | 0.556 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | pre | ASIA | rf | 0.556 [0.50,0.60] | 0.560 [0.49,0.62] | - | 0.544 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +5 | ASIA | rf | 0.535 [0.49,0.58] | 0.558 [0.50,0.62] | - | 0.546 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | NY | gbt3 | 0.549 [0.48,0.62] | 0.557 [0.45,0.66] | - | 0.558 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +5 | ASIA | rf | 0.531 [0.49,0.58] | 0.557 [0.49,0.62] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +45 | ASIA | gbt3 | 0.566 [0.52,0.61] | 0.556 [0.50,0.62] | - | 0.550 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | pre | LONDON | gbt3 | 0.524 [0.47,0.58] | 0.556 [0.48,0.64] | - | 0.557 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | pre | ASIA | rf | 0.545 [0.50,0.59] | 0.556 [0.49,0.63] | - | 0.538 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | POOLED | gbt3 | 0.539 [0.51,0.58] | 0.556 [0.51,0.61] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY/HM | logit2 | 0.588 [0.54,0.63] | 0.556 [0.49,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | POOLED | stack | 0.554 [0.52,0.59] | 0.555 [0.51,0.59] | - | 0.539 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | LONDON | logit2 | 0.538 [0.48,0.59] | 0.555 [0.48,0.63] | - | 0.549 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +30 | NY | gbt3 | 0.540 [0.48,0.60] | 0.554 [0.45,0.66] | - | 0.567 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | pre | ASIA | rf | 0.544 [0.50,0.59] | 0.553 [0.49,0.62] | - | 0.536 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | LONDON | stack | 0.576 [0.52,0.63] | 0.552 [0.46,0.65] | - | 0.513 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +15 | POOLED | rf | 0.538 [0.51,0.57] | 0.552 [0.51,0.60] | - | 0.532 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +10 | POOLED | stack | 0.558 [0.53,0.59] | 0.552 [0.51,0.60] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +30 | POOLED | rf | 0.542 [0.51,0.57] | 0.551 [0.51,0.60] | - | 0.530 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +5 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.551 [0.49,0.61] | - | 0.546 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | NY | gbt3 | 0.504 [0.44,0.58] | 0.550 [0.44,0.65] | - | 0.587 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +10 | LONDON | stack | 0.535 [0.48,0.59] | 0.550 [0.48,0.63] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | POOLED | rf | 0.551 [0.52,0.58] | 0.550 [0.51,0.59] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | pre | ASIA | gbt3 | 0.546 [0.50,0.59] | 0.550 [0.50,0.61] | - | 0.534 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +60 | POOLED | rf | 0.538 [0.51,0.57] | 0.547 [0.51,0.59] | - | 0.529 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +20 | POOLED | rf | 0.544 [0.52,0.57] | 0.547 [0.50,0.59] | - | 0.534 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +10 | NY | gbt3 | 0.540 [0.47,0.60] | 0.547 [0.45,0.64] | - | 0.605 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +5 | LONDON | stack | 0.546 [0.50,0.60] | 0.546 [0.47,0.62] | - | 0.539 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +15 | POOLED | rf | 0.533 [0.50,0.56] | 0.546 [0.51,0.58] | - | 0.526 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +5 | LONDON | stack | 0.547 [0.50,0.60] | 0.546 [0.48,0.62] | - | 0.564 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +45 | NY | gbt3 | 0.543 [0.48,0.60] | 0.546 [0.44,0.65] | - | 0.536 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +30 | ASIA | stack | 0.545 [0.50,0.59] | 0.546 [0.48,0.60] | - | 0.521 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | LONDON | stack | 0.541 [0.49,0.59] | 0.545 [0.47,0.63] | - | 0.557 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +15 | POOLED | stack | 0.530 [0.50,0.56] | 0.545 [0.51,0.58] | - | 0.514 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | LONDON/ST | logit2 | 0.538 [0.49,0.58] | 0.545 [0.47,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +5 | NY | logit2 | 0.563 [0.50,0.62] | 0.545 [0.45,0.63] | - | 0.514 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +20 | NY | rf | 0.546 [0.48,0.62] | 0.545 [0.44,0.65] | - | 0.534 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +30 | LONDON | rf | 0.523 [0.47,0.57] | 0.545 [0.45,0.63] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +60 | POOLED | rf | 0.537 [0.50,0.57] | 0.545 [0.50,0.59] | - | 0.525 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +5 | POOLED | rf | 0.548 [0.52,0.57] | 0.544 [0.51,0.58] | - | 0.534 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +45 | NY | rf | 0.523 [0.46,0.60] | 0.544 [0.45,0.65] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +5 | POOLED | rf | 0.543 [0.51,0.57] | 0.544 [0.50,0.59] | - | 0.524 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +60 | LONDON | stack | 0.542 [0.49,0.59] | 0.544 [0.45,0.62] | - | 0.544 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +30 | NY | gbt3 | 0.530 [0.46,0.60] | 0.544 [0.43,0.65] | - | 0.555 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +20 | NY | logit2 | 0.513 [0.44,0.58] | 0.543 [0.44,0.65] | - | 0.555 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | pre | POOLED | rf | 0.547 [0.52,0.58] | 0.543 [0.51,0.58] | - | 0.523 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +5 | POOLED | rf | 0.542 [0.52,0.57] | 0.542 [0.50,0.58] | - | 0.524 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +30 | NY | logit2 | 0.522 [0.45,0.59] | 0.542 [0.43,0.65] | - | 0.573 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +30 | NY | logit2 | 0.518 [0.45,0.58] | 0.542 [0.44,0.64] | - | 0.545 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | POOLED | stack | 0.538 [0.51,0.57] | 0.542 [0.50,0.59] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | NY | logit2 | 0.548 [0.48,0.63] | 0.542 [0.45,0.63] | - | 0.554 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +60 | ASIA | gbt3 | 0.530 [0.48,0.58] | 0.542 [0.47,0.61] | - | 0.531 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +45 | NY | stack | 0.523 [0.46,0.59] | 0.542 [0.43,0.65] | - | 0.520 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | pre | NY | rf | 0.538 [0.48,0.60] | 0.541 [0.44,0.64] | - | 0.560 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +30 | ASIA | logit2 | 0.537 [0.49,0.58] | 0.540 [0.48,0.61] | - | 0.521 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | ASIA | stack | 0.536 [0.50,0.57] | 0.540 [0.48,0.60] | - | 0.503 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +60 | POOLED | gbt3 | 0.531 [0.50,0.57] | 0.540 [0.49,0.58] | - | 0.534 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +15 | POOLED | rf | 0.540 [0.51,0.57] | 0.539 [0.50,0.58] | - | 0.522 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +15 | POOLED | stack | 0.532 [0.50,0.56] | 0.539 [0.49,0.58] | - | 0.509 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +20 | NY | rf | 0.547 [0.48,0.62] | 0.539 [0.43,0.65] | - | 0.553 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +45 | ASIA | logit2 | 0.554 [0.51,0.60] | 0.538 [0.47,0.61] | - | 0.538 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +15 | POOLED | stack | 0.535 [0.51,0.56] | 0.538 [0.50,0.58] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | NY | gbt3 | 0.535 [0.46,0.61] | 0.538 [0.42,0.65] | - | 0.576 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +30 | ASIA | stack | 0.553 [0.52,0.59] | 0.537 [0.48,0.59] | - | 0.518 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | pre | POOLED | rf | 0.534 [0.50,0.57] | 0.537 [0.50,0.58] | - | 0.512 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +60 | ASIA | gbt3 | 0.526 [0.47,0.58] | 0.537 [0.47,0.60] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +30 | NY | logit2 | 0.544 [0.48,0.61] | 0.537 [0.43,0.63] | - | 0.555 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +15 | NY | logit2 | 0.508 [0.44,0.57] | 0.537 [0.44,0.63] | - | 0.508 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | POOLED/HM | rf | 0.531 [0.51,0.55] | 0.537 [0.51,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | POOLED | rf | 0.531 [0.50,0.56] | 0.537 [0.49,0.57] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +45 | NY | rf | 0.529 [0.46,0.60] | 0.536 [0.44,0.64] | - | 0.519 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | NY | logit2 | 0.524 [0.46,0.59] | 0.536 [0.43,0.64] | - | 0.553 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | POOLED | gbt3 | 0.539 [0.51,0.57] | 0.536 [0.49,0.58] | - | 0.518 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | pre | LONDON | gbt3 | 0.509 [0.46,0.56] | 0.536 [0.45,0.61] | - | 0.524 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +10 | POOLED | stack | 0.544 [0.52,0.57] | 0.536 [0.49,0.58] | - | 0.514 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +20 | NY | logit2 | 0.537 [0.47,0.61] | 0.535 [0.42,0.65] | - | 0.537 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +45 | ASIA | gbt3 | 0.559 [0.51,0.60] | 0.535 [0.47,0.60] | - | 0.524 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +10 | NY | logit2 | 0.533 [0.47,0.60] | 0.535 [0.44,0.62] | - | 0.502 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +10 | NY | rf | 0.526 [0.46,0.60] | 0.535 [0.44,0.63] | - | 0.586 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | POOLED | rf | 0.540 [0.51,0.57] | 0.535 [0.49,0.58] | - | 0.517 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY/ST | stack | 0.520 [0.47,0.57] | 0.533 [0.46,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | NY | gbt3 | 0.564 [0.50,0.63] | 0.533 [0.44,0.64] | - | 0.542 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | pre | LONDON | stack | 0.539 [0.48,0.60] | 0.533 [0.46,0.61] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | ASIA | stack | 0.547 [0.50,0.59] | 0.532 [0.46,0.60] | - | 0.529 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall-G | sig | POOLED | rf | 0.521 [0.50,0.54] | 0.532 [0.50,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | POOLED | stack | 0.550 [0.52,0.58] | 0.531 [0.49,0.57] | - | 0.508 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +10 | ASIA | rf | 0.529 [0.48,0.57] | 0.531 [0.47,0.60] | - | 0.515 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | POOLED/ST | logit2 | 0.515 [0.49,0.54] | 0.531 [0.50,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | NY | stack | 0.519 [0.46,0.58] | 0.530 [0.43,0.65] | - | 0.542 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | NY | gbt3 | 0.544 [0.47,0.62] | 0.530 [0.42,0.65] | - | 0.506 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +15 | LONDON | logit2 | 0.534 [0.48,0.58] | 0.529 [0.45,0.61] | - | 0.548 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +45 | ASIA | rf | 0.551 [0.51,0.59] | 0.529 [0.47,0.59] | - | 0.514 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +10 | NY | rf | 0.530 [0.46,0.60] | 0.529 [0.43,0.63] | - | 0.565 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +30 | POOLED | stack | 0.532 [0.50,0.56] | 0.529 [0.48,0.58] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +60 | ASIA | logit2 | 0.531 [0.49,0.58] | 0.529 [0.46,0.60] | - | 0.516 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | ASIA/HM | stack | 0.534 [0.50,0.57] | 0.528 [0.47,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +10 | NY | stack | 0.513 [0.45,0.58] | 0.528 [0.42,0.63] | - | 0.544 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | NY | stack | 0.516 [0.45,0.58] | 0.528 [0.43,0.63] | - | 0.511 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +15 | LONDON | stack | 0.535 [0.48,0.59] | 0.527 [0.45,0.61] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY | rf | 0.514 [0.48,0.55] | 0.527 [0.47,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +30 | ASIA | stack | 0.534 [0.50,0.57] | 0.527 [0.47,0.58] | - | 0.503 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | NY/ST | stack | 0.512 [0.46,0.56] | 0.527 [0.46,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +45 | LONDON | stack | 0.535 [0.48,0.59] | 0.527 [0.45,0.61] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +20 | POOLED | stack | 0.545 [0.52,0.58] | 0.527 [0.48,0.57] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall-G | sig | ASIA/ST | stack | 0.505 [0.47,0.54] | 0.527 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | pre | ASIA | stack | 0.546 [0.50,0.59] | 0.526 [0.46,0.59] | - | 0.512 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +45 | ASIA | logit2 | 0.536 [0.49,0.58] | 0.526 [0.46,0.59] | - | 0.516 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +45 | POOLED | gbt3 | 0.531 [0.50,0.56] | 0.526 [0.48,0.57] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +45 | ASIA | rf | 0.546 [0.50,0.59] | 0.526 [0.47,0.59] | - | 0.515 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | LONDON | stack | 0.525 [0.47,0.58] | 0.526 [0.44,0.62] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +5 | POOLED | stack | 0.518 [0.49,0.55] | 0.526 [0.48,0.57] | - | 0.502 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | LONDON | stack | 0.541 [0.49,0.59] | 0.526 [0.44,0.60] | - | 0.513 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +20 | ASIA | logit2 | 0.511 [0.47,0.56] | 0.525 [0.46,0.59] | - | 0.517 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | ASIA | stack | 0.513 [0.49,0.54] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +20 | NY | logit2 | 0.553 [0.49,0.61] | 0.524 [0.41,0.63] | - | 0.523 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED/HM | rf | 0.518 [0.49,0.54] | 0.524 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +5 | POOLED | stack | 0.542 [0.51,0.57] | 0.523 [0.48,0.57] | - | 0.511 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +30 | POOLED | stack | 0.534 [0.51,0.56] | 0.523 [0.48,0.56] | - | 0.491 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +5 | NY | gbt3 | 0.533 [0.46,0.60] | 0.523 [0.42,0.62] | - | 0.535 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | ASIA/HM | stack | 0.522 [0.49,0.55] | 0.523 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | NY | logit2 | 0.534 [0.46,0.60] | 0.522 [0.42,0.63] | - | 0.548 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall-G | sig | LONDON | rf | 0.532 [0.49,0.57] | 0.522 [0.47,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.522 [0.50,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | POOLED | stack | 0.527 [0.50,0.55] | 0.522 [0.48,0.56] | - | 0.501 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression-G | sig | POOLED/HM | rf | 0.518 [0.50,0.54] | 0.522 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | ASIA | stack | 0.534 [0.50,0.57] | 0.522 [0.46,0.59] | - | 0.507 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +60 | NY | rf | 0.532 [0.46,0.61] | 0.521 [0.42,0.62] | - | 0.527 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON/ST | gbt3 | 0.529 [0.48,0.58] | 0.521 [0.44,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | ASIA | logit2 | 0.537 [0.49,0.58] | 0.521 [0.46,0.58] | - | 0.496 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED/HM | rf | 0.528 [0.51,0.55] | 0.521 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON/ST | rf | 0.524 [0.47,0.57] | 0.521 [0.45,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +20 | POOLED | rf | 0.527 [0.50,0.56] | 0.521 [0.48,0.56] | - | 0.503 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +30 | ASIA | rf | 0.529 [0.48,0.57] | 0.521 [0.46,0.59] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +45 | NY | rf | 0.496 [0.43,0.57] | 0.521 [0.42,0.62] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | pre | POOLED | stack | 0.535 [0.51,0.56] | 0.520 [0.48,0.56] | - | 0.498 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | pre | LONDON | gbt3 | 0.518 [0.47,0.57] | 0.520 [0.43,0.60] | - | 0.502 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY/ST | rf | 0.497 [0.44,0.55] | 0.520 [0.44,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +60 | NY | stack | 0.536 [0.47,0.61] | 0.520 [0.42,0.61] | - | 0.512 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | LONDON/HM | rf | 0.527 [0.48,0.57] | 0.520 [0.46,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | ASIA | logit2 | 0.521 [0.48,0.56] | 0.520 [0.46,0.58] | - | 0.509 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | LONDON | stack | 0.540 [0.49,0.59] | 0.519 [0.43,0.60] | - | 0.483 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | LONDON | stack | 0.539 [0.49,0.59] | 0.519 [0.44,0.60] | - | 0.496 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +20 | ASIA | logit2 | 0.509 [0.46,0.56] | 0.519 [0.46,0.59] | - | 0.507 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | LONDON | stack | 0.514 [0.46,0.57] | 0.519 [0.45,0.60] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED | rf | 0.511 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | ASIA | gbt3 | 0.552 [0.51,0.59] | 0.518 [0.46,0.58] | - | 0.500 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED | rf | 0.513 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +45 | ASIA | logit2 | 0.550 [0.50,0.59] | 0.518 [0.45,0.58] | - | 0.512 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | POOLED | rf | 0.526 [0.50,0.56] | 0.517 [0.48,0.56] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | pre | LONDON | gbt3 | 0.514 [0.46,0.56] | 0.517 [0.42,0.60] | - | 0.502 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | ASIA | stack | 0.504 [0.48,0.53] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +10 | ASIA | rf | 0.537 [0.49,0.58] | 0.517 [0.46,0.58] | - | 0.503 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON | logit2 | 0.517 [0.48,0.55] | 0.517 [0.47,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY/HM | gbt3 | 0.563 [0.52,0.61] | 0.516 [0.44,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | POOLED | gbt3 | 0.531 [0.50,0.56] | 0.516 [0.47,0.56] | - | 0.508 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +5 | NY | stack | 0.502 [0.44,0.57] | 0.516 [0.41,0.62] | - | 0.546 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +45 | POOLED | rf | 0.528 [0.50,0.56] | 0.516 [0.47,0.56] | - | 0.504 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +45 | NY | rf | 0.505 [0.44,0.57] | 0.515 [0.41,0.62] | - | 0.499 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +30 | NY | logit2 | 0.534 [0.47,0.59] | 0.515 [0.40,0.62] | - | 0.525 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +20 | ASIA | stack | 0.531 [0.49,0.57] | 0.515 [0.45,0.57] | - | 0.492 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | ASIA | stack | 0.535 [0.49,0.58] | 0.515 [0.45,0.58] | - | 0.484 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA/HM | stack | 0.525 [0.49,0.56] | 0.514 [0.47,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +30 | NY | rf | 0.540 [0.47,0.61] | 0.514 [0.41,0.62] | - | 0.528 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +15 | NY | stack | 0.515 [0.45,0.58] | 0.514 [0.41,0.62] | - | 0.502 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | NY/HM | rf | 0.535 [0.49,0.59] | 0.514 [0.44,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| combo-Xall-G | sig | NY | gbt3 | 0.525 [0.49,0.56] | 0.514 [0.45,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | ASIA | stack | 0.539 [0.49,0.58] | 0.513 [0.45,0.58] | - | 0.494 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +10 | ASIA | rf | 0.535 [0.49,0.58] | 0.513 [0.45,0.58] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED/HM | rf | 0.519 [0.50,0.54] | 0.513 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | ASIA | stack | 0.533 [0.49,0.58] | 0.513 [0.45,0.57] | - | 0.491 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +30 | POOLED | rf | 0.525 [0.49,0.55] | 0.513 [0.47,0.55] | - | 0.495 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +15 | LONDON | gbt3 | 0.509 [0.45,0.57] | 0.513 [0.44,0.59] | - | 0.498 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +5 | LONDON | stack | 0.521 [0.47,0.58] | 0.513 [0.45,0.58] | - | 0.497 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | NY | rf | 0.516 [0.48,0.55] | 0.512 [0.45,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | ASIA | stack | 0.520 [0.48,0.57] | 0.512 [0.45,0.58] | - | 0.489 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | LONDON | gbt3 | 0.519 [0.47,0.57] | 0.512 [0.44,0.58] | - | 0.508 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +10 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.512 [0.44,0.59] | - | 0.498 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.512 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | POOLED | gbt3 | 0.521 [0.49,0.55] | 0.512 [0.47,0.55] | - | 0.495 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +10 | POOLED | logit2 | 0.518 [0.49,0.55] | 0.512 [0.47,0.55] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | pre | LONDON | gbt3 | 0.519 [0.46,0.58] | 0.512 [0.44,0.58] | - | 0.509 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +5 | LONDON | stack | 0.533 [0.48,0.58] | 0.512 [0.44,0.59] | - | 0.494 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA/HM | stack | 0.518 [0.48,0.55] | 0.511 [0.46,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | ASIA | stack | 0.546 [0.50,0.59] | 0.511 [0.44,0.58] | - | 0.489 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +20 | ASIA | stack | 0.514 [0.47,0.56] | 0.511 [0.45,0.58] | - | 0.495 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | ASIA | rf | 0.547 [0.51,0.59] | 0.511 [0.45,0.57] | - | 0.504 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA | stack | 0.498 [0.47,0.53] | 0.510 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +10 | ASIA | rf | 0.529 [0.48,0.57] | 0.510 [0.45,0.58] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +15 | NY | logit2 | 0.505 [0.44,0.57] | 0.510 [0.41,0.61] | - | 0.551 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +45 | NY | rf | 0.509 [0.44,0.58] | 0.510 [0.41,0.60] | - | 0.501 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | POOLED/ST | gbt3 | 0.502 [0.48,0.53] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +15 | ASIA | stack | 0.535 [0.50,0.58] | 0.510 [0.45,0.57] | - | 0.495 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +60 | ASIA | rf | 0.520 [0.48,0.57] | 0.510 [0.45,0.57] | - | 0.492 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +20 | ASIA | stack | 0.512 [0.47,0.55] | 0.510 [0.45,0.57] | - | 0.488 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON/HM | rf | 0.526 [0.48,0.57] | 0.509 [0.45,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +60 | ASIA | logit2 | 0.521 [0.48,0.57] | 0.509 [0.44,0.58] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY/ST | gbt3 | 0.505 [0.46,0.56] | 0.508 [0.44,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA | stack | 0.501 [0.48,0.53] | 0.508 [0.47,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +15 | NY | stack | 0.514 [0.45,0.58] | 0.508 [0.41,0.61] | - | 0.482 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +15 | ASIA | stack | 0.532 [0.49,0.58] | 0.508 [0.44,0.57] | - | 0.496 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +5 | NY | gbt3 | 0.503 [0.44,0.57] | 0.508 [0.40,0.61] | - | 0.588 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | POOLED/ST | gbt3 | 0.500 [0.47,0.53] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | POOLED | rf | 0.531 [0.50,0.56] | 0.507 [0.46,0.55] | - | 0.495 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON/ST | rf | 0.527 [0.48,0.58] | 0.507 [0.44,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | NY | rf | 0.516 [0.44,0.59] | 0.507 [0.40,0.62] | - | 0.517 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | NY | rf | 0.537 [0.46,0.62] | 0.507 [0.41,0.60] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | LONDON | rf | 0.526 [0.49,0.56] | 0.507 [0.46,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | LONDON | rf | 0.515 [0.48,0.55] | 0.506 [0.46,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels-G | sig | ASIA/ST | gbt3 | 0.492 [0.46,0.52] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +10 | NY | rf | 0.518 [0.46,0.58] | 0.506 [0.41,0.59] | - | 0.527 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +15 | ASIA | stack | 0.523 [0.48,0.57] | 0.506 [0.44,0.57] | - | 0.483 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +45 | POOLED | logit2 | 0.520 [0.49,0.55] | 0.506 [0.46,0.55] | - | 0.494 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +30 | ASIA | logit2 | 0.525 [0.48,0.57] | 0.506 [0.45,0.56] | - | 0.490 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +45 | ASIA | logit2 | 0.529 [0.49,0.57] | 0.505 [0.44,0.58] | - | 0.499 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +20 | ASIA | stack | 0.537 [0.50,0.58] | 0.504 [0.45,0.56] | - | 0.498 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +45 | POOLED | stack | 0.528 [0.50,0.56] | 0.504 [0.47,0.54] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +20 | LONDON | stack | 0.537 [0.48,0.60] | 0.504 [0.42,0.58] | - | 0.467 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +60 | ASIA | logit2 | 0.514 [0.47,0.56] | 0.504 [0.44,0.56] | - | 0.493 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | ASIA | stack | 0.543 [0.50,0.58] | 0.503 [0.45,0.56] | - | 0.482 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall-G | sig | LONDON/ST | gbt3 | 0.529 [0.48,0.58] | 0.503 [0.43,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | pre | ASIA | stack | 0.525 [0.49,0.56] | 0.503 [0.44,0.56] | - | 0.488 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +30 | LONDON | stack | 0.509 [0.45,0.57] | 0.503 [0.42,0.58] | - | 0.477 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels-G | sig | LONDON/HM | logit2 | 0.504 [0.46,0.55] | 0.502 [0.45,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +30 | POOLED | rf | 0.528 [0.50,0.55] | 0.502 [0.46,0.55] | - | 0.482 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY | rf | 0.515 [0.48,0.55] | 0.501 [0.44,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +45 | ASIA | rf | 0.523 [0.48,0.57] | 0.501 [0.44,0.56] | - | 0.486 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON | rf | 0.517 [0.48,0.55] | 0.501 [0.45,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | pre | LONDON | stack | 0.532 [0.48,0.58] | 0.501 [0.42,0.58] | - | 0.479 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +20 | ASIA | stack | 0.523 [0.48,0.56] | 0.501 [0.43,0.56] | - | 0.485 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +30 | ASIA | rf | 0.527 [0.49,0.57] | 0.500 [0.44,0.56] | - | 0.475 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +5 | LONDON | stack | 0.524 [0.47,0.58] | 0.500 [0.43,0.58] | - | 0.481 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +60 | POOLED | rf | 0.512 [0.48,0.54] | 0.500 [0.46,0.54] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +30 | ASIA | rf | 0.513 [0.47,0.56] | 0.500 [0.44,0.56] | - | 0.470 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +10 | ASIA | rf | 0.524 [0.48,0.57] | 0.500 [0.44,0.56] | - | 0.490 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +15 | LONDON | stack | 0.529 [0.48,0.58] | 0.500 [0.41,0.58] | - | 0.476 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +60 | ASIA | logit2 | 0.514 [0.47,0.56] | 0.499 [0.44,0.56] | - | 0.487 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | NY/ST | stack | 0.499 [0.45,0.55] | 0.499 [0.44,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | ASIA | rf | 0.521 [0.48,0.56] | 0.499 [0.44,0.56] | - | 0.488 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | LONDON | stack | 0.524 [0.47,0.58] | 0.499 [0.42,0.58] | - | 0.455 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +15 | LONDON | rf | 0.499 [0.45,0.55] | 0.499 [0.43,0.57] | - | 0.481 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +15 | ASIA | stack | 0.534 [0.49,0.58] | 0.499 [0.44,0.56] | - | 0.473 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | NY | gbt3 | 0.532 [0.46,0.61] | 0.498 [0.39,0.61] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | ASIA | logit2 | 0.519 [0.48,0.56] | 0.498 [0.44,0.56] | - | 0.485 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | pre | POOLED | stack | 0.524 [0.49,0.55] | 0.498 [0.45,0.54] | - | 0.484 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +45 | NY | rf | 0.504 [0.44,0.57] | 0.497 [0.39,0.60] | - | 0.482 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +15 | NY | rf | 0.508 [0.45,0.58] | 0.496 [0.41,0.59] | - | 0.515 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +45 | LONDON | gbt3 | 0.527 [0.47,0.58] | 0.496 [0.42,0.56] | - | 0.490 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +20 | ASIA | stack | 0.532 [0.49,0.57] | 0.496 [0.43,0.57] | - | 0.485 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | pre | LONDON | stack | 0.511 [0.46,0.57] | 0.496 [0.42,0.58] | - | 0.513 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +5 | LONDON | stack | 0.511 [0.46,0.56] | 0.496 [0.43,0.56] | - | 0.464 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +20 | NY | logit2 | 0.518 [0.45,0.58] | 0.495 [0.38,0.60] | - | 0.490 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression-G | sig | ASIA/ST | gbt3 | 0.485 [0.45,0.52] | 0.495 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | pre | NY | stack | 0.498 [0.43,0.56] | 0.495 [0.39,0.60] | - | 0.508 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA | stack | 0.492 [0.46,0.52] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA/HM | stack | 0.512 [0.48,0.55] | 0.495 [0.44,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +20 | NY | logit2 | 0.518 [0.46,0.57] | 0.494 [0.38,0.60] | - | 0.498 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | pre | LONDON | stack | 0.510 [0.45,0.57] | 0.494 [0.40,0.58] | - | 0.495 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +30 | LONDON | stack | 0.520 [0.47,0.58] | 0.494 [0.41,0.58] | - | 0.465 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | ASIA | stack | 0.512 [0.47,0.56] | 0.493 [0.43,0.56] | - | 0.459 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +10 | LONDON | stack | 0.490 [0.43,0.54] | 0.492 [0.42,0.58] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +45 | LONDON | stack | 0.503 [0.45,0.56] | 0.492 [0.41,0.57] | - | 0.481 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock-G | sig | POOLED/ST | gbt3 | 0.492 [0.47,0.52] | 0.492 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | LONDON | gbt3 | 0.511 [0.46,0.56] | 0.491 [0.40,0.58] | - | 0.493 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +60 | POOLED | gbt3 | 0.502 [0.47,0.53] | 0.490 [0.44,0.54] | - | 0.476 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +10 | ASIA | stack | 0.554 [0.51,0.59] | 0.490 [0.43,0.55] | - | 0.475 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | POOLED/ST | gbt3 | 0.494 [0.47,0.52] | 0.490 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | ASIA | gbt3 | 0.528 [0.48,0.57] | 0.490 [0.42,0.56] | - | 0.469 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression-G | sig | LONDON/HM | rf | 0.504 [0.46,0.55] | 0.489 [0.43,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +30 | LONDON | stack | 0.516 [0.46,0.57] | 0.489 [0.41,0.57] | - | 0.456 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +30 | NY | rf | 0.530 [0.45,0.60] | 0.489 [0.35,0.62] | - | 0.497 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +60 | LONDON | stack | 0.512 [0.45,0.57] | 0.489 [0.40,0.58] | - | 0.490 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +10 | NY | logit2 | 0.509 [0.45,0.58] | 0.488 [0.38,0.59] | - | 0.509 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +20 | NY | logit2 | 0.539 [0.48,0.60] | 0.487 [0.37,0.59] | - | 0.486 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +30 | LONDON | logit2 | 0.509 [0.45,0.56] | 0.487 [0.41,0.57] | - | 0.493 | - | ok | - | - | - | - | stack | locked label (reference only) |
| combo-Xall | +15 | ASIA | rf | 0.513 [0.47,0.56] | 0.486 [0.43,0.54] | - | 0.471 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | NY | stack | 0.527 [0.46,0.60] | 0.485 [0.37,0.59] | - | 0.488 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +5 | NY | gbt3 | 0.489 [0.43,0.56] | 0.485 [0.39,0.59] | - | 0.540 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | NY | logit2 | 0.520 [0.46,0.58] | 0.484 [0.36,0.59] | - | 0.478 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow-G | sig | LONDON/HM | rf | 0.508 [0.46,0.55] | 0.484 [0.42,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | ASIA/ST | gbt3 | 0.475 [0.44,0.50] | 0.483 [0.44,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock-G | sig | NY/HM | gbt3 | 0.536 [0.49,0.59] | 0.482 [0.41,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | LONDON | stack | 0.525 [0.47,0.58] | 0.482 [0.41,0.56] | - | 0.466 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +30 | LONDON | stack | 0.531 [0.48,0.58] | 0.482 [0.40,0.56] | - | 0.453 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +5 | LONDON | stack | 0.516 [0.46,0.57] | 0.481 [0.41,0.55] | - | 0.451 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +10 | LONDON | stack | 0.512 [0.46,0.57] | 0.481 [0.40,0.56] | - | 0.477 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock-G | sig | NY | gbt3 | 0.514 [0.48,0.55] | 0.481 [0.42,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | ASIA | rf | 0.521 [0.47,0.57] | 0.480 [0.41,0.54] | - | 0.468 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +5 | ASIA | gbt3 | 0.540 [0.50,0.58] | 0.479 [0.42,0.54] | - | 0.474 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +45 | LONDON | gbt3 | 0.502 [0.45,0.55] | 0.479 [0.40,0.56] | - | 0.471 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +10 | NY | logit2 | 0.492 [0.42,0.56] | 0.479 [0.38,0.57] | - | 0.463 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +10 | ASIA | logit2 | 0.540 [0.49,0.59] | 0.479 [0.42,0.54] | - | 0.465 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | pre | ASIA | rf | 0.531 [0.48,0.58] | 0.478 [0.41,0.54] | - | 0.472 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | pre | ASIA | stack | 0.531 [0.49,0.57] | 0.477 [0.42,0.54] | - | 0.469 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +30 | LONDON | rf | 0.504 [0.45,0.56] | 0.477 [0.40,0.54] | - | 0.474 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +20 | ASIA | stack | 0.527 [0.48,0.57] | 0.477 [0.41,0.54] | - | 0.461 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +20 | LONDON | stack | 0.505 [0.45,0.56] | 0.475 [0.40,0.55] | - | 0.452 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +10 | NY | rf | 0.497 [0.43,0.56] | 0.475 [0.38,0.57] | - | 0.514 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X30-week-state | +20 | LONDON | rf | 0.508 [0.45,0.57] | 0.474 [0.41,0.55] | - | 0.490 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +60 | NY | gbt3 | 0.513 [0.45,0.58] | 0.474 [0.37,0.59] | - | 0.466 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +15 | ASIA | stack | 0.517 [0.47,0.56] | 0.474 [0.41,0.53] | - | 0.449 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +5 | LONDON | stack | 0.520 [0.47,0.57] | 0.473 [0.41,0.54] | - | 0.468 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression-G | sig | NY/HM | rf | 0.524 [0.48,0.58] | 0.472 [0.40,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | pre | NY | rf | 0.508 [0.44,0.57] | 0.472 [0.37,0.57] | - | 0.471 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +60 | NY | logit2 | 0.512 [0.44,0.58] | 0.472 [0.35,0.59] | - | 0.479 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | ASIA/ST | gbt3 | 0.476 [0.44,0.51] | 0.471 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +10 | ASIA | gbt3 | 0.522 [0.48,0.57] | 0.471 [0.40,0.53] | - | 0.462 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | pre | NY | rf | 0.499 [0.43,0.57] | 0.470 [0.36,0.57] | - | 0.470 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +30 | LONDON | stack | 0.494 [0.44,0.55] | 0.469 [0.38,0.56] | - | 0.427 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X26-volume-clock | +60 | ASIA | stack | 0.505 [0.46,0.55] | 0.469 [0.41,0.54] | - | 0.446 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow-G | sig | NY/HM | rf | 0.529 [0.48,0.58] | 0.469 [0.40,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +10 | ASIA | logit2 | 0.513 [0.47,0.56] | 0.469 [0.40,0.53] | - | 0.455 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | pre | NY | stack | 0.514 [0.45,0.57] | 0.468 [0.36,0.56] | - | 0.476 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +5 | ASIA | gbt3 | 0.505 [0.46,0.55] | 0.468 [0.40,0.53] | - | 0.467 | - | ok | - | - | - | - |  | locked label (reference only) |
| X28-prior-day-levels | +20 | LONDON | gbt3 | 0.493 [0.44,0.54] | 0.464 [0.39,0.53] | - | 0.446 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +30 | NY | logit2 | 0.483 [0.42,0.55] | 0.462 [0.37,0.55] | - | 0.460 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +15 | LONDON | gbt3 | 0.497 [0.44,0.55] | 0.461 [0.40,0.53] | - | 0.440 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +5 | ASIA | stack | 0.534 [0.49,0.57] | 0.460 [0.39,0.53] | - | 0.452 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | pre | NY | stack | 0.514 [0.45,0.57] | 0.460 [0.37,0.55] | - | 0.456 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | pre | NY | stack | 0.488 [0.43,0.55] | 0.459 [0.35,0.56] | - | 0.453 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +20 | ASIA | stack | 0.519 [0.48,0.56] | 0.458 [0.40,0.52] | - | 0.449 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +15 | LONDON | gbt3 | 0.494 [0.44,0.54] | 0.458 [0.39,0.53] | - | 0.450 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +60 | LONDON | logit2 | 0.489 [0.43,0.55] | 0.457 [0.38,0.53] | - | 0.466 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +5 | ASIA | rf | 0.518 [0.48,0.56] | 0.453 [0.38,0.52] | - | 0.445 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +15 | LONDON | logit2 | 0.514 [0.45,0.57] | 0.451 [0.37,0.54] | - | 0.435 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | pre | ASIA | gbt3 | 0.512 [0.47,0.55] | 0.449 [0.39,0.51] | - | 0.437 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +5 | NY | gbt3 | 0.496 [0.42,0.57] | 0.448 [0.35,0.55] | - | 0.470 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +15 | NY | rf | 0.518 [0.45,0.58] | 0.448 [0.36,0.54] | - | 0.453 | - | ok | - | - | - | - |  | locked label (reference only) |
| X30-week-state | +10 | LONDON | stack | 0.519 [0.47,0.57] | 0.444 [0.37,0.52] | - | 0.438 | - | ok | - | - | - | - |  | locked label (reference only) |
| X26-volume-clock | +5 | LONDON | stack | 0.507 [0.46,0.56] | 0.443 [0.38,0.52] | - | 0.447 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X27-compression | +45 | NY | stack | 0.503 [0.43,0.57] | 0.438 [0.34,0.54] | - | 0.459 | - | ok | - | - | - | - |  | locked label (reference only) |
| combo-Xall | +15 | NY | stack | 0.510 [0.44,0.58] | 0.427 [0.31,0.54] | - | 0.415 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X28-prior-day-levels | +45 | NY | stack | 0.485 [0.41,0.56] | 0.418 [0.31,0.52] | - | 0.422 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +5 | NY | gbt3 | 0.487 [0.42,0.57] | 0.415 [0.31,0.54] | - | 0.445 | - | ok | - | - | - | - | stack | locked label (reference only) |
| X29-tick-rule-flow | +60 | NY | rf | 0.472 [0.39,0.55] | 0.395 [0.30,0.50] | - | 0.350 | - | ok | - | - | - | - |  | locked label (reference only) |
| X29-tick-rule-flow | +45 | NY | gbt3 | 0.472 [0.41,0.54] | 0.395 [0.30,0.49] | - | 0.385 | - | ok | - | - | - | - |  | locked label (reference only) |
| X27-compression | +30 | LONDON | stack | 0.478 [0.42,0.54] | 0.395 [0.32,0.48] | - | 0.401 | - | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X26-volume-clock 60 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.490; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 NY: run X2_r3c_X26; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 POOLED: run X2_r3c_X26; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 LONDON: run X2_r3c_X26; model chosen by cond WF-PRE 0.559; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.569; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 ASIA: run X2_r3c_X26; model chosen by cond WF-PRE 0.576; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.468; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.483; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.483; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.485; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.487; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 30 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 15 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 5 LONDON: run X2_r3c_X26b; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 10 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 POOLED: run X2_r3c_X26b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 0 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 60 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 20 NY: run X2_r3c_X26b; model chosen by cond WF-PRE 0.554; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock 45 ASIA: run X2_r3c_X26b; model chosen by cond WF-PRE 0.571; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.457; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 POOLED: run X2_r3c_X27; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.552; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.557; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 NY: run X2_r3c_X27; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 LONDON: run X2_r3c_X27; model chosen by cond WF-PRE 0.563; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.569; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.578; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 ASIA: run X2_r3c_X27; model chosen by cond WF-PRE 0.597; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.464; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.491; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 60 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 10 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 5 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 0 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 30 LONDON: run X2_r3c_X27b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 20 NY: run X2_r3c_X27b; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 POOLED: run X2_r3c_X27b; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 15 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X27-compression 45 ASIA: run X2_r3c_X27b; model chosen by cond WF-PRE 0.575; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.459; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 POOLED: run X2_r3c_X28; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.535; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 ASIA: run X2_r3c_X28; model chosen by cond WF-PRE 0.547; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 LONDON: run X2_r3c_X28; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 NY: run X2_r3c_X28; model chosen by cond WF-PRE 0.579; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.476; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.477; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.488; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.492; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.497; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.500; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 10 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 5 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.525; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 60 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 30 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 15 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 POOLED: run X2_r3c_X28b; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 LONDON: run X2_r3c_X28b; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 0 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.553; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 45 ASIA: run X2_r3c_X28b; model chosen by cond WF-PRE 0.557; econ/CPCV not run (cond pre AUC<0.60)
- X28-prior-day-levels 20 NY: run X2_r3c_X28b; model chosen by cond WF-PRE 0.570; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.487; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.496; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.499; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.510; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.529; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.545; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 POOLED: run X2_r3c_X29; model chosen by cond WF-PRE 0.547; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.551; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.555; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.557; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.558; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.563; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 NY: run X2_r3c_X29; model chosen by cond WF-PRE 0.566; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 ASIA: run X2_r3c_X29; model chosen by cond WF-PRE 0.567; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.585; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 LONDON: run X2_r3c_X29; model chosen by cond WF-PRE 0.587; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.468; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.486; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.486; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.488; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.498; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.507; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.513; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.519; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 30 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 15 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 10 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 5 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.529; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 0 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 LONDON: run X2_r3c_X29b; model chosen by cond WF-PRE 0.531; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 POOLED: run X2_r3c_X29b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 60 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 20 NY: run X2_r3c_X29b; model chosen by cond WF-PRE 0.539; econ/CPCV not run (cond pre AUC<0.60)
- X29-tick-rule-flow 45 ASIA: run X2_r3c_X29b; model chosen by cond WF-PRE 0.561; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.526; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 LONDON: run X2_r3c_X30; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.529; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.536; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.544; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.549; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 POOLED: run X2_r3c_X30; model chosen by cond WF-PRE 0.553; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.561; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.562; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.563; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.587; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 ASIA: run X2_r3c_X30; model chosen by cond WF-PRE 0.587; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 NY: run X2_r3c_X30; model chosen by cond WF-PRE 0.594; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.458; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.478; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.480; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.487; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.489; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.493; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.494; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.508; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.512; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.514; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.516; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.517; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.522; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.528; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 60 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 POOLED: run X2_r3c_X30b; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 LONDON: run X2_r3c_X30b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 10 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 30 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 0 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.537; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 15 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 20 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.543; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 5 NY: run X2_r3c_X30b; model chosen by cond WF-PRE 0.548; econ/CPCV not run (cond pre AUC<0.60)
- X30-week-state 45 ASIA: run X2_r3c_X30b; model chosen by cond WF-PRE 0.565; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 10 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.440; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.490; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 20 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.501; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.502; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.503; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 45 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.506; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 5 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.511; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.515; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 0 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.518; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 0 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.521; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 20 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 60 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 60 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.523; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 5 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 60 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 0 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.527; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 60 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.530; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 10 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.532; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 10 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.533; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 20 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.534; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.538; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 10 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 45 POOLED: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 5 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.540; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.541; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 0 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.550; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 45 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.554; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 45 ASIA: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.573; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 20 NY: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.574; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 5 LONDON: run X2_r3c_Xallb; model chosen by cond WF-PRE 0.574; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 ASIA: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 NY: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.504; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 ASIA: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.505; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 LONDON: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.509; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 30 POOLED: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.520; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 LONDON: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.524; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 POOLED: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.542; econ/CPCV not run (cond pre AUC<0.60)
- combo-Xall 15 NY: run X2_r3c_Xallpt; model chosen by cond WF-PRE 0.555; econ/CPCV not run (cond pre AUC<0.60)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 ASIA: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 POOLED: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 NY: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X26-volume-clock-G -1 LONDON: FAILPRED feats + X26 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 ASIA: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 POOLED: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 NY: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X27-compression-G -1 LONDON: FAILPRED feats + X27 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 ASIA: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 POOLED: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 NY: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X28-prior-day-levels-G -1 LONDON: FAILPRED feats + X28 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 ASIA: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 POOLED: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 NY: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- X29-tick-rule-flow-G -1 LONDON: FAILPRED feats + X29 signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 ASIA: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 POOLED: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 NY: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
- combo-Xall-G -1 LONDON: FAILPRED feats + Xall signal features; model by WF-PRE; no gate/R11 (pre AUC<0.68)
