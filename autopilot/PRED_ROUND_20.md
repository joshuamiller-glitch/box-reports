# PRED ROUND 20 - block X3 round 2 - X11-oracle-gap+X14-stack-diversity+X15-conformal-abstain

Best HOLDOUT F-R AUC: +15 POOLED 0.545 [-,-] | ASIA 0.642 [-,-] | LONDON 0.547 [-,-] | NY 0.577 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.552 [-,-] | ASIA 0.608 [-,-] | LONDON 0.630 [-,-] | NY 0.573 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 8f5c9a7e18a669812db530b5b75bde6ef44e7a9ada910fb1602aad79204064c9 ; trials added 700 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/X11.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X11-oracle-gap-oracle | +30 | NY | ORACLE | 0.816 [0.78,0.85] | 0.871 [0.82,0.91] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +15 | NY | ORACLE | 0.811 [0.78,0.84] | 0.861 [0.81,0.90] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | pre | NY | ORACLE | 0.795 [0.76,0.82] | 0.837 [0.79,0.88] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +5 | NY | ORACLE | 0.780 [0.74,0.81] | 0.827 [0.78,0.87] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | pre | POOLED | ORACLE | 0.790 [0.77,0.81] | 0.823 [0.79,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +15 | POOLED | ORACLE | 0.785 [0.76,0.81] | 0.820 [0.79,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +5 | POOLED | ORACLE | 0.784 [0.76,0.80] | 0.814 [0.78,0.84] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +30 | POOLED | ORACLE | 0.774 [0.75,0.80] | 0.812 [0.78,0.84] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +15 | LONDON | ORACLE | 0.769 [0.74,0.81] | 0.810 [0.76,0.86] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | pre | LONDON | ORACLE | 0.754 [0.72,0.79] | 0.803 [0.76,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +30 | LONDON | ORACLE | 0.768 [0.73,0.80] | 0.801 [0.75,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +5 | LONDON | ORACLE | 0.761 [0.73,0.80] | 0.799 [0.75,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | pre | ASIA | ORACLE | 0.792 [0.76,0.82] | 0.798 [0.75,0.85] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +5 | ASIA | ORACLE | 0.780 [0.75,0.81] | 0.784 [0.73,0.83] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +15 | ASIA | ORACLE | 0.751 [0.71,0.79] | 0.764 [0.72,0.82] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap-oracle | +30 | ASIA | ORACLE | 0.711 [0.67,0.75] | 0.740 [0.69,0.79] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | BIN_a1_h0 | - | 0.664 [-,-] | - | - | 0.933 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | R0_a1_h0 | - | 0.651 [-,-] | - | - | 0.717 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | HpF_a1_h15 | - | 0.642 [-,-] | - | - | 0.768 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | BIN_a1_h30 | - | 0.630 [-,-] | - | - | 0.867 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | BIN_a1_h30 | - | 0.608 [-,-] | - | - | 0.693 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | HpF_a1_h5 | - | 0.602 [-,-] | - | - | 0.892 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | BIN_a1_h15 | - | 0.602 [-,-] | - | - | 0.692 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | R0_a1_h30 | - | 0.602 [-,-] | - | - | 0.736 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | HpF_a1_h0 | - | 0.595 [-,-] | - | - | 0.904 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | LONDON | M3 | - | 0.587 [-,-] | - | - | 0.677 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | ASIA | M3 | - | 0.586 [-,-] | - | - | 0.599 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | R0_a3_h30 | - | 0.586 [-,-] | - | - | 0.703 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | LONDON | M4 | - | 0.581 [-,-] | - | - | 0.660 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | R0_a2_h30 | - | 0.578 [-,-] | - | - | 0.667 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | BIN_a3_h15 | - | 0.577 [-,-] | - | - | 0.884 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | NY | M2 | - | 0.573 [-,-] | - | - | 0.784 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | NY | M1 | - | 0.573 [-,-] | - | - | 0.803 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | R0_a3_h30 | - | 0.569 [-,-] | - | - | 0.807 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | BIN_a2_h15 | - | 0.566 [-,-] | - | - | 0.614 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | NY | M5 | - | 0.566 [-,-] | - | - | 0.786 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | LONDON | M2 | - | 0.565 [-,-] | - | - | 0.666 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +15 | ASIA | X11o | - | 0.564 [-,-] | - | - | 0.577 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | R0_a3_h0 | - | 0.563 [-,-] | - | - | 0.668 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | HpF_a2_h30 | - | 0.562 [-,-] | - | - | 0.915 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | BIN_a3_h15 | - | 0.562 [-,-] | - | - | 0.597 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | HpF_a3_h30 | - | 0.561 [-,-] | - | - | 0.908 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +5 | ASIA | X11o | - | 0.561 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | LONDON | M5 | - | 0.560 [-,-] | - | - | 0.657 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | ASIA | M1 | - | 0.558 [-,-] | - | - | 0.569 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | R0_a2_h0 | - | 0.558 [-,-] | - | - | 0.656 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | BIN_a3_h30 | - | 0.557 [-,-] | - | - | 0.597 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +30 | NY | X11b | - | 0.557 [-,-] | - | - | 0.873 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | R0_a1_h5 | - | 0.556 [-,-] | - | - | 0.674 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | NY | M2 | - | 0.554 [-,-] | - | - | 0.778 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | R0_a1_h5 | - | 0.553 [-,-] | - | - | 0.540 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | ASIA | M2 | - | 0.553 [-,-] | - | - | 0.559 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | NY | HpF_a2_h0 | - | 0.553 [-,-] | - | - | 0.901 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | HpF_a1_h30 | - | 0.553 [-,-] | - | - | 0.699 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | BIN_a1_h30 | - | 0.552 [-,-] | - | - | 0.877 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | NY | X11b | - | 0.552 [-,-] | - | - | 0.858 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | R0_a2_h5 | - | 0.551 [-,-] | - | - | 0.625 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | BIN_a2_h30 | - | 0.550 [-,-] | - | - | 0.817 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | NY | M3 | - | 0.550 [-,-] | - | - | 0.776 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | HpF_a2_h30 | - | 0.549 [-,-] | - | - | 0.631 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | ASIA | M2 | - | 0.548 [-,-] | - | - | 0.526 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +15 | ASIA | X11b | - | 0.547 [-,-] | - | - | 0.570 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | BIN_a3_h15 | - | 0.547 [-,-] | - | - | 0.771 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +30 | NY | X11o | - | 0.547 [-,-] | - | - | 0.836 | N | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +5 | ASIA | X11b | - | 0.546 [-,-] | - | - | 0.569 | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +30 | ASIA | X11b | - | 0.546 [-,-] | - | - | 0.572 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | R0_a1_h30 | - | 0.546 [-,-] | - | - | 0.699 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | LONDON | X11b | - | 0.546 [-,-] | - | - | 0.710 | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +30 | ASIA | X11o | - | 0.545 [-,-] | - | - | 0.561 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | BIN_a3_h15 | - | 0.545 [-,-] | - | - | 0.777 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | BIN_a3_h30 | - | 0.544 [-,-] | - | - | 0.777 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | LONDON | M1 | - | 0.543 [-,-] | - | - | 0.660 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | LONDON | M5 | - | 0.542 [-,-] | - | - | 0.651 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | R0_a2_h30 | - | 0.542 [-,-] | - | - | 0.774 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | ASIA | X11b | - | 0.542 [-,-] | - | - | 0.566 | N | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | LONDON | M4 | - | 0.541 [-,-] | - | - | 0.617 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | NY | M5 | - | 0.540 [-,-] | - | - | 0.777 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | HpF_a3_h30 | - | 0.540 [-,-] | - | - | 0.597 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +30 | POOLED | X11b | - | 0.540 [-,-] | - | - | 0.738 | N | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | POOLED | M1 | - | 0.540 [-,-] | - | - | 0.686 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | HpF_a3_h5 | - | 0.539 [-,-] | - | - | 0.875 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | ASIA | M4 | - | 0.538 [-,-] | - | - | 0.557 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | ASIA | M5 | - | 0.538 [-,-] | - | - | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +30 | LONDON | X11b | - | 0.537 [-,-] | - | - | 0.727 | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | POOLED | X11b | - | 0.537 [-,-] | - | - | 0.726 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | HpF_a2_h15 | - | 0.537 [-,-] | - | - | 0.614 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | ASIA | X11o | - | 0.537 [-,-] | - | - | 0.550 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | BIN_a3_h30 | - | 0.537 [-,-] | - | - | 0.781 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | HpF_a1_h0 | - | 0.536 [-,-] | - | - | 0.887 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | R0_a3_h5 | - | 0.535 [-,-] | - | - | 0.531 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | ASIA | M1 | - | 0.532 [-,-] | - | - | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | NY | M4 | - | 0.532 [-,-] | - | - | 0.676 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | LONDON | M2 | - | 0.532 [-,-] | - | - | 0.673 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | NY | M3 | - | 0.532 [-,-] | - | - | 0.800 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | ASIA | M1 | - | 0.532 [-,-] | - | - | 0.528 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | R0_a1_h30 | - | 0.530 [-,-] | - | - | 0.739 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | POOLED | M3 | - | 0.530 [-,-] | - | - | 0.698 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | POOLED | M2 | - | 0.530 [-,-] | - | - | 0.681 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | BIN_a2_h30 | - | 0.530 [-,-] | - | - | 0.588 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | HpF_a3_h0 | - | 0.529 [-,-] | - | - | 0.894 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | LONDON | M2 | - | 0.528 [-,-] | - | - | 0.653 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | HpF_a3_h0 | - | 0.528 [-,-] | - | - | 0.570 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | R0_a3_h15 | - | 0.528 [-,-] | - | - | 0.818 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | POOLED | M5 | - | 0.527 [-,-] | - | - | 0.689 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | LONDON | M4 | - | 0.527 [-,-] | - | - | 0.623 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | POOLED | M1 | - | 0.526 [-,-] | - | - | 0.701 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | BIN_a2_h15 | - | 0.526 [-,-] | - | - | 0.774 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | NY | M4 | - | 0.525 [-,-] | - | - | 0.772 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | ASIA | M1 | - | 0.525 [-,-] | - | - | 0.512 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | R0_a2_h5 | - | 0.525 [-,-] | - | - | 0.520 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | NY | M3 | - | 0.524 [-,-] | - | - | 0.678 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | BIN_a2_h30 | - | 0.524 [-,-] | - | - | 0.816 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | ASIA | M2 | - | 0.523 [-,-] | - | - | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | LONDON | M1 | - | 0.523 [-,-] | - | - | 0.659 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | BIN_a3_h0 | - | 0.522 [-,-] | - | - | 0.559 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | R0_a3_h30 | - | 0.522 [-,-] | - | - | 0.703 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | R0_a2_h15 | - | 0.521 [-,-] | - | - | 0.540 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | R0_a2_h5 | - | 0.520 [-,-] | - | - | 0.677 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | NY | M1 | - | 0.519 [-,-] | - | - | 0.801 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | POOLED | M3 | - | 0.519 [-,-] | - | - | 0.676 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | ASIA | M4 | - | 0.519 [-,-] | - | - | 0.508 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +30 | POOLED | X11o | - | 0.519 [-,-] | - | - | 0.699 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | R0_a3_h15 | - | 0.518 [-,-] | - | - | 0.703 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | POOLED | M5 | - | 0.518 [-,-] | - | - | 0.663 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | HpF_a3_h15 | - | 0.518 [-,-] | - | - | 0.867 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | R0_a1_h30 | - | 0.518 [-,-] | - | - | 0.507 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | R0_a3_h15 | - | 0.518 [-,-] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | HpF_a2_h0 | - | 0.517 [-,-] | - | - | 0.589 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | NY | M2 | - | 0.517 [-,-] | - | - | 0.688 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | R0_a2_h15 | - | 0.517 [-,-] | - | - | 0.707 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | HpF_a3_h15 | - | 0.517 [-,-] | - | - | 0.575 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | POOLED | M2 | - | 0.516 [-,-] | - | - | 0.688 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | ASIA | M5 | - | 0.515 [-,-] | - | - | 0.532 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | ASIA | R0_a1_h15 | - | 0.514 [-,-] | - | - | 0.540 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | NY | X11o | - | 0.514 [-,-] | - | - | 0.805 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | HpF_a1_h15 | - | 0.513 [-,-] | - | - | 0.887 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | LONDON | M4 | - | 0.513 [-,-] | - | - | 0.651 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | POOLED | M4 | - | 0.513 [-,-] | - | - | 0.666 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | R0_a3_h0 | - | 0.513 [-,-] | - | - | 0.513 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | ASIA | M3 | - | 0.512 [-,-] | - | - | 0.504 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | LONDON | M5 | - | 0.512 [-,-] | - | - | 0.674 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | LONDON | M3 | - | 0.512 [-,-] | - | - | 0.635 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +30 | LONDON | X11o | - | 0.511 [-,-] | - | - | 0.666 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | BIN_a2_h15 | - | 0.511 [-,-] | - | - | 0.787 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | R0_a2_h0 | - | 0.510 [-,-] | - | - | 0.509 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | HpF_a3_h5 | - | 0.510 [-,-] | - | - | 0.557 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | ASIA | M2 | - | 0.508 [-,-] | - | - | 0.508 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | HpF_a1_h0 | - | 0.508 [-,-] | - | - | 0.672 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | POOLED | X11o | - | 0.507 [-,-] | - | - | 0.683 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | BIN_a2_h0 | - | 0.507 [-,-] | - | - | 0.572 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | NY | M4 | - | 0.507 [-,-] | - | - | 0.778 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | ASIA | M5 | - | 0.507 [-,-] | - | - | 0.493 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +30 | ASIA | M3 | - | 0.507 [-,-] | - | - | 0.501 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | HpF_a2_h30 | - | 0.506 [-,-] | - | - | 0.841 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | ASIA | M5 | - | 0.504 [-,-] | - | - | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | POOLED | M4 | - | 0.503 [-,-] | - | - | 0.682 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | R0_a3_h15 | - | 0.503 [-,-] | - | - | 0.708 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | BIN_a2_h30 | - | 0.503 [-,-] | - | - | 0.901 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | BIN_a1_h5 | - | 0.502 [-,-] | - | - | 0.822 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | R0_a1_h15 | - | 0.500 [-,-] | - | - | 0.721 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | HpF_a3_h15 | - | 0.500 [-,-] | - | - | 0.785 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | BIN_a3_h5 | - | 0.498 [-,-] | - | - | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | BIN_a2_h0 | - | 0.498 [-,-] | - | - | 0.790 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | BIN_a2_h5 | - | 0.498 [-,-] | - | - | 0.550 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +30 | ASIA | M4 | - | 0.498 [-,-] | - | - | 0.482 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | LONDON | M3 | - | 0.498 [-,-] | - | - | 0.609 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | HpF_a2_h5 | - | 0.497 [-,-] | - | - | 0.800 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | NY | M1 | - | 0.497 [-,-] | - | - | 0.687 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | HpF_a3_h30 | - | 0.497 [-,-] | - | - | 0.790 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | NY | M5 | - | 0.497 [-,-] | - | - | 0.652 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +5 | POOLED | X11o | - | 0.497 [-,-] | - | - | 0.671 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | R0_a2_h30 | - | 0.496 [-,-] | - | - | 0.685 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | ASIA | M4 | - | 0.496 [-,-] | - | - | 0.500 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | HpF_a1_h0 | - | 0.496 [-,-] | - | - | 0.887 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | R0_a3_h30 | - | 0.496 [-,-] | - | - | 0.492 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | ASIA | M3 | - | 0.494 [-,-] | - | - | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | NY | M4 | - | 0.494 [-,-] | - | - | 0.650 | - | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +5 | NY | X11o | - | 0.493 [-,-] | - | - | 0.778 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | R0_a3_h5 | - | 0.493 [-,-] | - | - | 0.689 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | BIN_a3_h30 | - | 0.492 [-,-] | - | - | 0.886 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | HpF_a3_h0 | - | 0.492 [-,-] | - | - | 0.780 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | NY | X11o | - | 0.491 [-,-] | - | - | 0.766 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | HpF_a3_h0 | - | 0.491 [-,-] | - | - | 0.777 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | R0_a2_h15 | - | 0.491 [-,-] | - | - | 0.709 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | HpF_a2_h0 | - | 0.490 [-,-] | - | - | 0.821 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | POOLED | M1 | - | 0.489 [-,-] | - | - | 0.647 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | POOLED | M5 | - | 0.489 [-,-] | - | - | 0.645 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | POOLED | M4 | - | 0.488 [-,-] | - | - | 0.636 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | HpF_a2_h5 | - | 0.488 [-,-] | - | - | 0.867 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +5 | LONDON | X11o | - | 0.487 [-,-] | - | - | 0.636 | N | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | pre | POOLED | X11b | - | 0.487 [-,-] | - | - | 0.701 | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | LONDON | X11b | - | 0.487 [-,-] | - | - | 0.704 | N | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | POOLED | X11o | - | 0.486 [-,-] | - | - | 0.663 | N | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | HpF_a2_h15 | - | 0.486 [-,-] | - | - | 0.820 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +15 | LONDON | X11o | - | 0.485 [-,-] | - | - | 0.632 | N | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +15 | LONDON | M1 | - | 0.483 [-,-] | - | - | 0.666 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | HpF_a3_h5 | - | 0.483 [-,-] | - | - | 0.771 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | BIN_a3_h5 | - | 0.481 [-,-] | - | - | 0.837 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | POOLED | M4 | - | 0.480 [-,-] | - | - | 0.633 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | LONDON | M5 | - | 0.478 [-,-] | - | - | 0.587 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | POOLED | M3 | - | 0.478 [-,-] | - | - | 0.637 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | HpF_a2_h5 | - | 0.477 [-,-] | - | - | 0.809 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | R0_a3_h0 | - | 0.477 [-,-] | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | NY | M3 | - | 0.477 [-,-] | - | - | 0.673 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | R0_a1_h5 | - | 0.476 [-,-] | - | - | 0.597 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +5 | NY | X11b | - | 0.476 [-,-] | - | - | 0.809 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | HpF_a1_h15 | - | 0.476 [-,-] | - | - | 0.882 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | BIN_a1_h15 | - | 0.476 [-,-] | - | - | 0.863 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +15 | LONDON | M3 | - | 0.475 [-,-] | - | - | 0.643 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | HpF_a2_h5 | - | 0.474 [-,-] | - | - | 0.559 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | LONDON | X11o | - | 0.474 [-,-] | - | - | 0.630 | N | - | - | - | - |  | locked label (reference only) |
| X11-oracle-gap | +5 | POOLED | X11b | - | 0.474 [-,-] | - | - | 0.690 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | HpF_a2_h15 | - | 0.473 [-,-] | - | - | 0.867 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | POOLED | R0_a1_h15 | - | 0.472 [-,-] | - | - | 0.726 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | HpF_a1_h5 | - | 0.472 [-,-] | - | - | 0.852 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | LONDON | M2 | - | 0.472 [-,-] | - | - | 0.608 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | POOLED | M5 | - | 0.471 [-,-] | - | - | 0.624 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | NY | M2 | - | 0.471 [-,-] | - | - | 0.668 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | pre | NY | M5 | - | 0.470 [-,-] | - | - | 0.706 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | HpF_a3_h5 | - | 0.469 [-,-] | - | - | 0.764 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | POOLED | HpF_a1_h30 | - | 0.469 [-,-] | - | - | 0.878 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | R0_a2_h15 | - | 0.469 [-,-] | - | - | 0.779 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | BIN_a1_h0 | - | 0.469 [-,-] | - | - | 0.839 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | R0_a3_h5 | - | 0.468 [-,-] | - | - | 0.607 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | HpF_a3_h30 | - | 0.466 [-,-] | - | - | 0.781 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | POOLED | M2 | - | 0.465 [-,-] | - | - | 0.639 | - | - | - | - | - |  | locked label (reference only) |
| X14-stack-diversity | +5 | POOLED | M3 | - | 0.464 [-,-] | - | - | 0.628 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | BIN_a3_h5 | - | 0.461 [-,-] | - | - | 0.741 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | ASIA | R0_a2_h30 | - | 0.461 [-,-] | - | - | 0.452 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | HpF_a2_h0 | - | 0.460 [-,-] | - | - | 0.794 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | POOLED | M1 | - | 0.460 [-,-] | - | - | 0.630 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | HpF_a2_h30 | - | 0.459 [-,-] | - | - | 0.839 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | R0_a2_h0 | - | 0.459 [-,-] | - | - | 0.641 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | HpF_a3_h15 | - | 0.456 [-,-] | - | - | 0.754 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | BIN_a1_h5 | - | 0.455 [-,-] | - | - | 0.561 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | R0_a3_h5 | - | 0.455 [-,-] | - | - | 0.639 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | BIN_a3_h5 | - | 0.455 [-,-] | - | - | 0.737 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | R0_a2_h5 | - | 0.453 [-,-] | - | - | 0.641 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | BIN_a2_h5 | - | 0.453 [-,-] | - | - | 0.753 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | R0_a1_h15 | - | 0.452 [-,-] | - | - | 0.738 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | pre | NY | X11b | - | 0.452 [-,-] | - | - | 0.807 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | HpF_a2_h15 | - | 0.451 [-,-] | - | - | 0.810 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | BIN_a3_h0 | - | 0.450 [-,-] | - | - | 0.846 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | pre | NY | M1 | - | 0.450 [-,-] | - | - | 0.662 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | R0_a1_h5 | - | 0.450 [-,-] | - | - | 0.662 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | LONDON | M1 | - | 0.445 [-,-] | - | - | 0.597 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | BIN_a2_h5 | - | 0.445 [-,-] | - | - | 0.757 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | R0_a1_h0 | - | 0.444 [-,-] | - | - | 0.440 | - | - | - | - | - | stack | locked label (reference only) |
| X14-stack-diversity | +5 | POOLED | M2 | - | 0.441 [-,-] | - | - | 0.629 | - | - | - | - | - |  | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | HpF_a1_h5 | - | 0.440 [-,-] | - | - | 0.848 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | BIN_a3_h0 | - | 0.439 [-,-] | - | - | 0.729 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | LONDON | BIN_a3_h0 | - | 0.437 [-,-] | - | - | 0.716 | - | - | - | - | - | stack | locked label (reference only) |
| X11-oracle-gap | +5 | LONDON | X11b | - | 0.437 [-,-] | - | - | 0.668 | N | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | R0_a3_h0 | - | 0.431 [-,-] | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | BIN_a2_h15 | - | 0.429 [-,-] | - | - | 0.841 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | LONDON | HpF_a1_h30 | - | 0.425 [-,-] | - | - | 0.860 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | POOLED | BIN_a1_h5 | - | 0.425 [-,-] | - | - | 0.822 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | ASIA | BIN_a1_h0 | - | 0.424 [-,-] | - | - | 0.570 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | BIN_a2_h0 | - | 0.419 [-,-] | - | - | 0.773 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | HpF_a1_h15 | - | 0.419 [-,-] | - | - | 0.864 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | R0_a2_h0 | - | 0.413 [-,-] | - | - | 0.625 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | NY | BIN_a2_h5 | - | 0.395 [-,-] | - | - | 0.794 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | R0_a1_h0 | - | 0.392 [-,-] | - | - | 0.624 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | POOLED | BIN_a1_h0 | - | 0.388 [-,-] | - | - | 0.828 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | HpF_a1_h30 | - | 0.365 [-,-] | - | - | 0.893 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | BIN_a2_h0 | - | 0.357 [-,-] | - | - | 0.824 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | pre | NY | R0_a1_h0 | - | 0.315 [-,-] | - | - | 0.549 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | LONDON | BIN_a1_h5 | - | - | - | - | 0.885 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +5 | ASIA | HpF_a1_h5 | - | - | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | LONDON | BIN_a1_h15 | - | - | - | - | 0.856 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +15 | NY | BIN_a1_h15 | - | - | - | - | 0.910 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain | +30 | NY | BIN_a1_h30 | - | - | - | - | 0.872 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | pre | POOLED | BIN | - | - | - | - | 0.699 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +5 | POOLED | BIN | - | - | - | - | 0.682 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +15 | POOLED | BIN | - | - | - | - | 0.734 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +30 | POOLED | BIN | - | - | - | - | 0.732 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | pre | POOLED | HpF | - | - | - | - | 0.706 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +5 | POOLED | HpF | - | - | - | - | 0.707 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +15 | POOLED | HpF | - | - | - | - | 0.715 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +30 | POOLED | HpF | - | - | - | - | 0.725 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | pre | POOLED | R0 | - | - | - | - | 0.648 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +5 | POOLED | R0 | - | - | - | - | 0.632 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +15 | POOLED | R0 | - | - | - | - | 0.703 | - | - | - | - | - | stack | locked label (reference only) |
| X15-conformal-abstain-fullcov | +30 | POOLED | R0 | - | - | - | - | 0.687 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X11-oracle-gap 0 POOLED: X11b; hold 0.701 vs R0 0.648 (+0.053); cond-entry hold 0.487 vs R0 0.490
- X11-oracle-gap 0 ASIA: X11b; hold 0.566 vs R0 0.529 (+0.037); cond-entry hold 0.542 vs R0 0.532
- X11-oracle-gap 0 LONDON: X11b; hold 0.704 vs R0 0.658 (+0.046); cond-entry hold 0.487 vs R0 0.522
- X11-oracle-gap 0 NY: X11b; hold 0.807 vs R0 0.669 (+0.138); cond-entry hold 0.452 vs R0 0.448
- X11-oracle-gap 5 POOLED: X11b; hold 0.690 vs R0 0.632 (+0.058); cond-entry hold 0.474 vs R0 0.460
- X11-oracle-gap 5 ASIA: X11b; hold 0.569 vs R0 0.528 (+0.041); cond-entry hold 0.546 vs R0 0.532
- X11-oracle-gap 5 LONDON: X11b; hold 0.668 vs R0 0.595 (+0.073); cond-entry hold 0.437 vs R0 0.438
- X11-oracle-gap 5 NY: X11b; hold 0.809 vs R0 0.692 (+0.117); cond-entry hold 0.476 vs R0 0.500
- X11-oracle-gap 15 POOLED: X11b; hold 0.726 vs R0 0.703 (+0.024); cond-entry hold 0.537 vs R0 0.529
- X11-oracle-gap 15 ASIA: X11b; hold 0.570 vs R0 0.570 (+0.000); cond-entry hold 0.547 vs R0 0.559
- X11-oracle-gap 15 LONDON: X11b; hold 0.710 vs R0 0.668 (+0.042); cond-entry hold 0.546 vs R0 0.486
- X11-oracle-gap 15 NY: X11b; hold 0.858 vs R0 0.802 (+0.056); cond-entry hold 0.552 vs R0 0.520
- X11-oracle-gap 30 POOLED: X11b; hold 0.738 vs R0 0.687 (+0.052); cond-entry hold 0.540 vs R0 0.541
- X11-oracle-gap 30 ASIA: X11b; hold 0.572 vs R0 0.514 (+0.058); cond-entry hold 0.546 vs R0 0.528
- X11-oracle-gap 30 LONDON: X11b; hold 0.727 vs R0 0.661 (+0.066); cond-entry hold 0.537 vs R0 0.546
- X11-oracle-gap 30 NY: X11b; hold 0.873 vs R0 0.804 (+0.069); cond-entry hold 0.557 vs R0 0.571
- X11-oracle-gap 0 POOLED: X11o; hold 0.663 vs R0 0.648 (+0.016); cond-entry hold 0.486 vs R0 0.490
- X11-oracle-gap 0 ASIA: X11o; hold 0.550 vs R0 0.529 (+0.021); cond-entry hold 0.537 vs R0 0.532
- X11-oracle-gap 0 LONDON: X11o; hold 0.630 vs R0 0.658 (-0.028); cond-entry hold 0.474 vs R0 0.522
- X11-oracle-gap 0 NY: X11o; hold 0.766 vs R0 0.669 (+0.097); cond-entry hold 0.491 vs R0 0.448
- X11-oracle-gap 5 POOLED: X11o; hold 0.671 vs R0 0.632 (+0.039); cond-entry hold 0.497 vs R0 0.460
- X11-oracle-gap 5 ASIA: X11o; hold 0.573 vs R0 0.528 (+0.044); cond-entry hold 0.561 vs R0 0.532
- X11-oracle-gap 5 LONDON: X11o; hold 0.636 vs R0 0.595 (+0.041); cond-entry hold 0.487 vs R0 0.438
- X11-oracle-gap 5 NY: X11o; hold 0.778 vs R0 0.692 (+0.086); cond-entry hold 0.493 vs R0 0.500
- X11-oracle-gap 15 POOLED: X11o; hold 0.683 vs R0 0.703 (-0.020); cond-entry hold 0.507 vs R0 0.529
- X11-oracle-gap 15 ASIA: X11o; hold 0.577 vs R0 0.570 (+0.007); cond-entry hold 0.564 vs R0 0.559
- X11-oracle-gap 15 LONDON: X11o; hold 0.632 vs R0 0.668 (-0.036); cond-entry hold 0.485 vs R0 0.486
- X11-oracle-gap 15 NY: X11o; hold 0.805 vs R0 0.802 (+0.003); cond-entry hold 0.514 vs R0 0.520
- X11-oracle-gap 30 POOLED: X11o; hold 0.699 vs R0 0.687 (+0.012); cond-entry hold 0.519 vs R0 0.541
- X11-oracle-gap 30 ASIA: X11o; hold 0.561 vs R0 0.514 (+0.047); cond-entry hold 0.545 vs R0 0.528
- X11-oracle-gap 30 LONDON: X11o; hold 0.666 vs R0 0.661 (+0.005); cond-entry hold 0.511 vs R0 0.546
- X11-oracle-gap 30 NY: X11o; hold 0.836 vs R0 0.804 (+0.032); cond-entry hold 0.547 vs R0 0.571
- X11-oracle-gap-oracle 0 POOLED: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.823 vs R0 0.648 (+0.175); cond-entry hold 0.707 vs R0 0.490
- X11-oracle-gap-oracle 0 ASIA: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.798 vs R0 0.529 (+0.269); cond-entry hold 0.789 vs R0 0.532
- X11-oracle-gap-oracle 0 LONDON: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.803 vs R0 0.658 (+0.145); cond-entry hold 0.648 vs R0 0.522
- X11-oracle-gap-oracle 0 NY: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.837 vs R0 0.669 (+0.168); cond-entry hold 0.479 vs R0 0.448
- X11-oracle-gap-oracle 5 POOLED: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.814 vs R0 0.632 (+0.182); cond-entry hold 0.697 vs R0 0.460
- X11-oracle-gap-oracle 5 ASIA: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.784 vs R0 0.528 (+0.255); cond-entry hold 0.775 vs R0 0.532
- X11-oracle-gap-oracle 5 LONDON: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.799 vs R0 0.595 (+0.204); cond-entry hold 0.638 vs R0 0.438
- X11-oracle-gap-oracle 5 NY: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.827 vs R0 0.692 (+0.134); cond-entry hold 0.484 vs R0 0.500
- X11-oracle-gap-oracle 15 POOLED: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.820 vs R0 0.703 (+0.117); cond-entry hold 0.706 vs R0 0.529
- X11-oracle-gap-oracle 15 ASIA: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.764 vs R0 0.570 (+0.194); cond-entry hold 0.761 vs R0 0.559
- X11-oracle-gap-oracle 15 LONDON: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.810 vs R0 0.668 (+0.142); cond-entry hold 0.681 vs R0 0.486
- X11-oracle-gap-oracle 15 NY: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.861 vs R0 0.802 (+0.058); cond-entry hold 0.556 vs R0 0.520
- X11-oracle-gap-oracle 30 POOLED: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.812 vs R0 0.687 (+0.125); cond-entry hold 0.686 vs R0 0.541
- X11-oracle-gap-oracle 30 ASIA: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.740 vs R0 0.514 (+0.226); cond-entry hold 0.737 vs R0 0.528
- X11-oracle-gap-oracle 30 LONDON: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.801 vs R0 0.661 (+0.140); cond-entry hold 0.660 vs R0 0.546
- X11-oracle-gap-oracle 30 NY: ORACLE [ORACLE LEAK upper bound, not a predictor]; hold 0.871 vs R0 0.804 (+0.067); cond-entry hold 0.545 vs R0 0.571
- X14-stack-diversity 0 POOLED: M1; hold 0.647 vs R0 0.648 (-0.001); cond-entry hold 0.489 vs R0 0.490
- X14-stack-diversity 0 ASIA: M1; hold 0.530 vs R0 0.529 (+0.000); cond-entry hold 0.532 vs R0 0.532
- X14-stack-diversity 0 LONDON: M1; hold 0.659 vs R0 0.658 (+0.000); cond-entry hold 0.523 vs R0 0.522
- X14-stack-diversity 0 NY: M1; hold 0.662 vs R0 0.669 (-0.007); cond-entry hold 0.450 vs R0 0.448
- X14-stack-diversity 5 POOLED: M1; hold 0.630 vs R0 0.632 (-0.001); cond-entry hold 0.460 vs R0 0.460
- X14-stack-diversity 5 ASIA: M1; hold 0.528 vs R0 0.528 (-0.000); cond-entry hold 0.532 vs R0 0.532
- X14-stack-diversity 5 LONDON: M1; hold 0.597 vs R0 0.595 (+0.001); cond-entry hold 0.445 vs R0 0.438
- X14-stack-diversity 5 NY: M1; hold 0.687 vs R0 0.692 (-0.006); cond-entry hold 0.497 vs R0 0.500
- X14-stack-diversity 15 POOLED: M1; hold 0.701 vs R0 0.703 (-0.001); cond-entry hold 0.526 vs R0 0.529
- X14-stack-diversity 15 ASIA: M1; hold 0.569 vs R0 0.570 (-0.000); cond-entry hold 0.558 vs R0 0.559
- X14-stack-diversity 15 LONDON: M1; hold 0.666 vs R0 0.668 (-0.002); cond-entry hold 0.483 vs R0 0.486
- X14-stack-diversity 15 NY: M1; hold 0.801 vs R0 0.802 (-0.001); cond-entry hold 0.519 vs R0 0.520
- X14-stack-diversity 30 POOLED: M1; hold 0.686 vs R0 0.687 (-0.000); cond-entry hold 0.540 vs R0 0.541
- X14-stack-diversity 30 ASIA: M1; hold 0.512 vs R0 0.514 (-0.002); cond-entry hold 0.525 vs R0 0.528
- X14-stack-diversity 30 LONDON: M1; hold 0.660 vs R0 0.661 (-0.001); cond-entry hold 0.543 vs R0 0.546
- X14-stack-diversity 30 NY: M1; hold 0.803 vs R0 0.804 (-0.001); cond-entry hold 0.573 vs R0 0.571
- X14-stack-diversity 0 POOLED: M2; hold 0.639 vs R0 0.648 (-0.009); cond-entry hold 0.465 vs R0 0.490
- X14-stack-diversity 0 ASIA: M2; hold 0.522 vs R0 0.529 (-0.007); cond-entry hold 0.523 vs R0 0.532
- X14-stack-diversity 0 LONDON: M2; hold 0.653 vs R0 0.658 (-0.005); cond-entry hold 0.528 vs R0 0.522
- X14-stack-diversity 0 NY: M2; hold 0.668 vs R0 0.669 (-0.001); cond-entry hold 0.471 vs R0 0.448
- X14-stack-diversity 5 POOLED: M2; hold 0.629 vs R0 0.632 (-0.003); cond-entry hold 0.441 vs R0 0.460
- X14-stack-diversity 5 ASIA: M2; hold 0.508 vs R0 0.528 (-0.021); cond-entry hold 0.508 vs R0 0.532
- X14-stack-diversity 5 LONDON: M2; hold 0.608 vs R0 0.595 (+0.013); cond-entry hold 0.472 vs R0 0.438
- X14-stack-diversity 5 NY: M2; hold 0.688 vs R0 0.692 (-0.004); cond-entry hold 0.517 vs R0 0.500
- X14-stack-diversity 15 POOLED: M2; hold 0.688 vs R0 0.703 (-0.015); cond-entry hold 0.516 vs R0 0.529
- X14-stack-diversity 15 ASIA: M2; hold 0.559 vs R0 0.570 (-0.011); cond-entry hold 0.553 vs R0 0.559
- X14-stack-diversity 15 LONDON: M2; hold 0.673 vs R0 0.668 (+0.005); cond-entry hold 0.532 vs R0 0.486
- X14-stack-diversity 15 NY: M2; hold 0.778 vs R0 0.802 (-0.024); cond-entry hold 0.554 vs R0 0.520
- X14-stack-diversity 30 POOLED: M2; hold 0.681 vs R0 0.687 (-0.006); cond-entry hold 0.530 vs R0 0.541
- X14-stack-diversity 30 ASIA: M2; hold 0.526 vs R0 0.514 (+0.012); cond-entry hold 0.548 vs R0 0.528
- X14-stack-diversity 30 LONDON: M2; hold 0.666 vs R0 0.661 (+0.005); cond-entry hold 0.565 vs R0 0.546
- X14-stack-diversity 30 NY: M2; hold 0.784 vs R0 0.804 (-0.020); cond-entry hold 0.573 vs R0 0.571
- X14-stack-diversity 0 POOLED: M3; hold 0.637 vs R0 0.648 (-0.010); cond-entry hold 0.478 vs R0 0.490
- X14-stack-diversity 0 ASIA: M3; hold 0.499 vs R0 0.529 (-0.030); cond-entry hold 0.494 vs R0 0.532
- X14-stack-diversity 0 LONDON: M3; hold 0.635 vs R0 0.658 (-0.023); cond-entry hold 0.512 vs R0 0.522
- X14-stack-diversity 0 NY: M3; hold 0.673 vs R0 0.669 (+0.004); cond-entry hold 0.477 vs R0 0.448
- X14-stack-diversity 5 POOLED: M3; hold 0.628 vs R0 0.632 (-0.003); cond-entry hold 0.464 vs R0 0.460
- X14-stack-diversity 5 ASIA: M3; hold 0.504 vs R0 0.528 (-0.024); cond-entry hold 0.512 vs R0 0.532
- X14-stack-diversity 5 LONDON: M3; hold 0.609 vs R0 0.595 (+0.014); cond-entry hold 0.498 vs R0 0.438
- X14-stack-diversity 5 NY: M3; hold 0.678 vs R0 0.692 (-0.014); cond-entry hold 0.524 vs R0 0.500
- X14-stack-diversity 15 POOLED: M3; hold 0.698 vs R0 0.703 (-0.004); cond-entry hold 0.530 vs R0 0.529
- X14-stack-diversity 15 ASIA: M3; hold 0.599 vs R0 0.570 (+0.029); cond-entry hold 0.586 vs R0 0.559
- X14-stack-diversity 15 LONDON: M3; hold 0.643 vs R0 0.668 (-0.026); cond-entry hold 0.475 vs R0 0.486
- X14-stack-diversity 15 NY: M3; hold 0.800 vs R0 0.802 (-0.003); cond-entry hold 0.532 vs R0 0.520
- X14-stack-diversity 30 POOLED: M3; hold 0.676 vs R0 0.687 (-0.011); cond-entry hold 0.519 vs R0 0.541
- X14-stack-diversity 30 ASIA: M3; hold 0.501 vs R0 0.514 (-0.013); cond-entry hold 0.507 vs R0 0.528
- X14-stack-diversity 30 LONDON: M3; hold 0.677 vs R0 0.661 (+0.016); cond-entry hold 0.587 vs R0 0.546
- X14-stack-diversity 30 NY: M3; hold 0.776 vs R0 0.804 (-0.028); cond-entry hold 0.550 vs R0 0.571
- X14-stack-diversity 0 POOLED: M4; hold 0.633 vs R0 0.648 (-0.015); cond-entry hold 0.480 vs R0 0.490
- X14-stack-diversity 0 ASIA: M4; hold 0.500 vs R0 0.529 (-0.029); cond-entry hold 0.496 vs R0 0.532
- X14-stack-diversity 0 LONDON: M4; hold 0.623 vs R0 0.658 (-0.035); cond-entry hold 0.527 vs R0 0.522
- X14-stack-diversity 0 NY: M4; hold 0.650 vs R0 0.669 (-0.019); cond-entry hold 0.494 vs R0 0.448
- X14-stack-diversity 5 POOLED: M4; hold 0.636 vs R0 0.632 (+0.005); cond-entry hold 0.488 vs R0 0.460
- X14-stack-diversity 5 ASIA: M4; hold 0.508 vs R0 0.528 (-0.020); cond-entry hold 0.519 vs R0 0.532
- X14-stack-diversity 5 LONDON: M4; hold 0.617 vs R0 0.595 (+0.022); cond-entry hold 0.541 vs R0 0.438
- X14-stack-diversity 5 NY: M4; hold 0.676 vs R0 0.692 (-0.016); cond-entry hold 0.532 vs R0 0.500
- X14-stack-diversity 15 POOLED: M4; hold 0.682 vs R0 0.703 (-0.021); cond-entry hold 0.503 vs R0 0.529
- X14-stack-diversity 15 ASIA: M4; hold 0.557 vs R0 0.570 (-0.013); cond-entry hold 0.538 vs R0 0.559
- X14-stack-diversity 15 LONDON: M4; hold 0.651 vs R0 0.668 (-0.017); cond-entry hold 0.513 vs R0 0.486
- X14-stack-diversity 15 NY: M4; hold 0.778 vs R0 0.802 (-0.025); cond-entry hold 0.507 vs R0 0.520
- X14-stack-diversity 30 POOLED: M4; hold 0.666 vs R0 0.687 (-0.021); cond-entry hold 0.513 vs R0 0.541
- X14-stack-diversity 30 ASIA: M4; hold 0.482 vs R0 0.514 (-0.032); cond-entry hold 0.498 vs R0 0.528
- X14-stack-diversity 30 LONDON: M4; hold 0.660 vs R0 0.661 (-0.001); cond-entry hold 0.581 vs R0 0.546
- X14-stack-diversity 30 NY: M4; hold 0.772 vs R0 0.804 (-0.032); cond-entry hold 0.525 vs R0 0.571
- X14-stack-diversity 0 POOLED: M5; hold 0.645 vs R0 0.648 (-0.003); cond-entry hold 0.489 vs R0 0.490
- X14-stack-diversity 0 ASIA: M5; hold 0.506 vs R0 0.529 (-0.023); cond-entry hold 0.504 vs R0 0.532
- X14-stack-diversity 0 LONDON: M5; hold 0.657 vs R0 0.658 (-0.001); cond-entry hold 0.560 vs R0 0.522
- X14-stack-diversity 0 NY: M5; hold 0.706 vs R0 0.669 (+0.037); cond-entry hold 0.470 vs R0 0.448
- X14-stack-diversity 5 POOLED: M5; hold 0.624 vs R0 0.632 (-0.008); cond-entry hold 0.471 vs R0 0.460
- X14-stack-diversity 5 ASIA: M5; hold 0.540 vs R0 0.528 (+0.012); cond-entry hold 0.538 vs R0 0.532
- X14-stack-diversity 5 LONDON: M5; hold 0.587 vs R0 0.595 (-0.008); cond-entry hold 0.478 vs R0 0.438
- X14-stack-diversity 5 NY: M5; hold 0.652 vs R0 0.692 (-0.041); cond-entry hold 0.497 vs R0 0.500
- X14-stack-diversity 15 POOLED: M5; hold 0.689 vs R0 0.703 (-0.013); cond-entry hold 0.527 vs R0 0.529
- X14-stack-diversity 15 ASIA: M5; hold 0.532 vs R0 0.570 (-0.037); cond-entry hold 0.515 vs R0 0.559
- X14-stack-diversity 15 LONDON: M5; hold 0.674 vs R0 0.668 (+0.005); cond-entry hold 0.512 vs R0 0.486
- X14-stack-diversity 15 NY: M5; hold 0.786 vs R0 0.802 (-0.017); cond-entry hold 0.566 vs R0 0.520
- X14-stack-diversity 30 POOLED: M5; hold 0.663 vs R0 0.687 (-0.024); cond-entry hold 0.518 vs R0 0.541
- X14-stack-diversity 30 ASIA: M5; hold 0.493 vs R0 0.514 (-0.021); cond-entry hold 0.507 vs R0 0.528
- X14-stack-diversity 30 LONDON: M5; hold 0.651 vs R0 0.661 (-0.010); cond-entry hold 0.542 vs R0 0.546
- X14-stack-diversity 30 NY: M5; hold 0.777 vs R0 0.804 (-0.028); cond-entry hold 0.540 vs R0 0.571
- X15-conformal-abstain 0 POOLED: conformal Mondrian R0 alpha=0.1; coverage 0.84, singleton share 0.63, AUC within singleton sets 0.624 (R0 same rows 0.624), within singleton AND >=1 entry 0.392; precision of {1} sets nan vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian R0 alpha=0.1; coverage 0.77, singleton share 0.62, AUC within singleton sets 0.440 (R0 same rows 0.440), within singleton AND >=1 entry 0.444; precision of {1} sets nan vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian R0 alpha=0.1; coverage 0.87, singleton share 0.49, AUC within singleton sets 0.717 (R0 same rows 0.717), within singleton AND >=1 entry 0.651; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian R0 alpha=0.1; coverage 0.88, singleton share 0.78, AUC within singleton sets 0.549 (R0 same rows 0.549), within singleton AND >=1 entry 0.315; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian R0 alpha=0.2; coverage 0.75, singleton share 0.81, AUC within singleton sets 0.641 (R0 same rows 0.641), within singleton AND >=1 entry 0.459; precision of {1} sets nan vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian R0 alpha=0.2; coverage 0.67, singleton share 0.84, AUC within singleton sets 0.509 (R0 same rows 0.509), within singleton AND >=1 entry 0.510; precision of {1} sets nan vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian R0 alpha=0.2; coverage 0.77, singleton share 0.74, AUC within singleton sets 0.656 (R0 same rows 0.656), within singleton AND >=1 entry 0.558; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian R0 alpha=0.2; coverage 0.82, singleton share 0.87, AUC within singleton sets 0.625 (R0 same rows 0.625), within singleton AND >=1 entry 0.413; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian R0 alpha=0.3; coverage 0.70, singleton share 0.90, AUC within singleton sets 0.649 (R0 same rows 0.649), within singleton AND >=1 entry 0.477; precision of {1} sets nan vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian R0 alpha=0.3; coverage 0.64, singleton share 0.90, AUC within singleton sets 0.513 (R0 same rows 0.513), within singleton AND >=1 entry 0.513; precision of {1} sets nan vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian R0 alpha=0.3; coverage 0.69, singleton share 0.87, AUC within singleton sets 0.668 (R0 same rows 0.668), within singleton AND >=1 entry 0.563; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian R0 alpha=0.3; coverage 0.77, singleton share 0.92, AUC within singleton sets 0.663 (R0 same rows 0.663), within singleton AND >=1 entry 0.431; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.39, AUC within singleton sets 0.828 (R0 same rows 0.652), within singleton AND >=1 entry 0.388; precision of {1} sets nan vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian BIN alpha=0.1; coverage 0.95, singleton share 0.16, AUC within singleton sets 0.570 (R0 same rows 0.484), within singleton AND >=1 entry 0.424; precision of {1} sets nan vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.34, AUC within singleton sets 0.933 (R0 same rows 0.716), within singleton AND >=1 entry 0.664; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian BIN alpha=0.1; coverage 0.93, singleton share 0.66, AUC within singleton sets 0.839 (R0 same rows 0.568), within singleton AND >=1 entry 0.469; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian BIN alpha=0.2; coverage 0.87, singleton share 0.54, AUC within singleton sets 0.773 (R0 same rows 0.683), within singleton AND >=1 entry 0.419; precision of {1} sets 0.5882352941176471 vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian BIN alpha=0.2; coverage 0.88, singleton share 0.35, AUC within singleton sets 0.572 (R0 same rows 0.543), within singleton AND >=1 entry 0.507; precision of {1} sets 0.5833333333333334 vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian BIN alpha=0.2; coverage 0.85, singleton share 0.56, AUC within singleton sets 0.790 (R0 same rows 0.682), within singleton AND >=1 entry 0.498; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian BIN alpha=0.2; coverage 0.87, singleton share 0.73, AUC within singleton sets 0.824 (R0 same rows 0.637), within singleton AND >=1 entry 0.357; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian BIN alpha=0.3; coverage 0.77, singleton share 0.70, AUC within singleton sets 0.729 (R0 same rows 0.660), within singleton AND >=1 entry 0.439; precision of {1} sets 0.4042553191489361 vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian BIN alpha=0.3; coverage 0.77, singleton share 0.59, AUC within singleton sets 0.559 (R0 same rows 0.518), within singleton AND >=1 entry 0.522; precision of {1} sets 0.4137931034482758 vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian BIN alpha=0.3; coverage 0.76, singleton share 0.71, AUC within singleton sets 0.716 (R0 same rows 0.646), within singleton AND >=1 entry 0.437; precision of {1} sets 0.4285714285714285 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian BIN alpha=0.3; coverage 0.78, singleton share 0.80, AUC within singleton sets 0.846 (R0 same rows 0.697), within singleton AND >=1 entry 0.450; precision of {1} sets nan vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian HpF alpha=0.1; coverage 0.93, singleton share 0.41, AUC within singleton sets 0.887 (R0 same rows 0.718), within singleton AND >=1 entry 0.536; precision of {1} sets 0.5833333333333334 vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian HpF alpha=0.1; coverage 0.94, singleton share 0.15, AUC within singleton sets 0.672 (R0 same rows 0.335), within singleton AND >=1 entry 0.508; precision of {1} sets 0.5 vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian HpF alpha=0.1; coverage 0.93, singleton share 0.37, AUC within singleton sets 0.887 (R0 same rows 0.772), within singleton AND >=1 entry 0.496; precision of {1} sets 0.4166666666666667 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian HpF alpha=0.1; coverage 0.93, singleton share 0.71, AUC within singleton sets 0.904 (R0 same rows 0.667), within singleton AND >=1 entry 0.595; precision of {1} sets 1.0 vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian HpF alpha=0.2; coverage 0.85, singleton share 0.55, AUC within singleton sets 0.821 (R0 same rows 0.731), within singleton AND >=1 entry 0.490; precision of {1} sets 0.5 vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian HpF alpha=0.2; coverage 0.84, singleton share 0.35, AUC within singleton sets 0.589 (R0 same rows 0.489), within singleton AND >=1 entry 0.517; precision of {1} sets 0.4705882352941176 vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian HpF alpha=0.2; coverage 0.84, singleton share 0.57, AUC within singleton sets 0.794 (R0 same rows 0.728), within singleton AND >=1 entry 0.460; precision of {1} sets 0.4827586206896552 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian HpF alpha=0.2; coverage 0.86, singleton share 0.73, AUC within singleton sets 0.901 (R0 same rows 0.718), within singleton AND >=1 entry 0.553; precision of {1} sets 0.6470588235294118 vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 POOLED: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.68, AUC within singleton sets 0.777 (R0 same rows 0.715), within singleton AND >=1 entry 0.491; precision of {1} sets 0.510989010989011 vs base 0.335; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 ASIA: conformal Mondrian HpF alpha=0.3; coverage 0.74, singleton share 0.57, AUC within singleton sets 0.570 (R0 same rows 0.544), within singleton AND >=1 entry 0.528; precision of {1} sets 0.4636363636363636 vs base 0.404; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 LONDON: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.69, AUC within singleton sets 0.780 (R0 same rows 0.701), within singleton AND >=1 entry 0.492; precision of {1} sets 0.5625 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 0 NY: conformal Mondrian HpF alpha=0.3; coverage 0.79, singleton share 0.79, AUC within singleton sets 0.894 (R0 same rows 0.761), within singleton AND >=1 entry 0.529; precision of {1} sets 0.625 vs base 0.232; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian R0 alpha=0.1; coverage 0.84, singleton share 0.60, AUC within singleton sets 0.662 (R0 same rows 0.662), within singleton AND >=1 entry 0.450; precision of {1} sets nan vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian R0 alpha=0.1; coverage 0.79, singleton share 0.53, AUC within singleton sets 0.540 (R0 same rows 0.540), within singleton AND >=1 entry 0.553; precision of {1} sets nan vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian R0 alpha=0.1; coverage 0.86, singleton share 0.47, AUC within singleton sets 0.674 (R0 same rows 0.674), within singleton AND >=1 entry 0.556; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian R0 alpha=0.1; coverage 0.88, singleton share 0.78, AUC within singleton sets 0.597 (R0 same rows 0.597), within singleton AND >=1 entry 0.476; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian R0 alpha=0.2; coverage 0.75, singleton share 0.81, AUC within singleton sets 0.641 (R0 same rows 0.641), within singleton AND >=1 entry 0.453; precision of {1} sets nan vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian R0 alpha=0.2; coverage 0.68, singleton share 0.82, AUC within singleton sets 0.520 (R0 same rows 0.520), within singleton AND >=1 entry 0.525; precision of {1} sets nan vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian R0 alpha=0.2; coverage 0.76, singleton share 0.72, AUC within singleton sets 0.625 (R0 same rows 0.625), within singleton AND >=1 entry 0.551; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian R0 alpha=0.2; coverage 0.81, singleton share 0.91, AUC within singleton sets 0.677 (R0 same rows 0.677), within singleton AND >=1 entry 0.520; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian R0 alpha=0.3; coverage 0.70, singleton share 0.91, AUC within singleton sets 0.639 (R0 same rows 0.639), within singleton AND >=1 entry 0.455; precision of {1} sets nan vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian R0 alpha=0.3; coverage 0.63, singleton share 0.93, AUC within singleton sets 0.531 (R0 same rows 0.531), within singleton AND >=1 entry 0.535; precision of {1} sets nan vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian R0 alpha=0.3; coverage 0.68, singleton share 0.87, AUC within singleton sets 0.607 (R0 same rows 0.607), within singleton AND >=1 entry 0.468; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian R0 alpha=0.3; coverage 0.78, singleton share 0.93, AUC within singleton sets 0.689 (R0 same rows 0.689), within singleton AND >=1 entry 0.493; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.39, AUC within singleton sets 0.822 (R0 same rows 0.707), within singleton AND >=1 entry 0.425; precision of {1} sets nan vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian BIN alpha=0.1; coverage 0.92, singleton share 0.23, AUC within singleton sets 0.561 (R0 same rows 0.575), within singleton AND >=1 entry 0.455; precision of {1} sets nan vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian BIN alpha=0.1; coverage 0.95, singleton share 0.32, AUC within singleton sets 0.885 (R0 same rows 0.627), within singleton AND >=1 entry nan; precision of {1} sets nan vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.63, AUC within singleton sets 0.822 (R0 same rows 0.660), within singleton AND >=1 entry 0.502; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian BIN alpha=0.2; coverage 0.85, singleton share 0.59, AUC within singleton sets 0.757 (R0 same rows 0.698), within singleton AND >=1 entry 0.445; precision of {1} sets 0.5 vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian BIN alpha=0.2; coverage 0.82, singleton share 0.46, AUC within singleton sets 0.550 (R0 same rows 0.560), within singleton AND >=1 entry 0.498; precision of {1} sets 0.4117647058823529 vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian BIN alpha=0.2; coverage 0.84, singleton share 0.58, AUC within singleton sets 0.753 (R0 same rows 0.661), within singleton AND >=1 entry 0.453; precision of {1} sets 0.7142857142857143 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian BIN alpha=0.2; coverage 0.90, singleton share 0.73, AUC within singleton sets 0.794 (R0 same rows 0.672), within singleton AND >=1 entry 0.395; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian BIN alpha=0.3; coverage 0.77, singleton share 0.71, AUC within singleton sets 0.741 (R0 same rows 0.660), within singleton AND >=1 entry 0.461; precision of {1} sets 0.5 vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian BIN alpha=0.3; coverage 0.76, singleton share 0.58, AUC within singleton sets 0.539 (R0 same rows 0.540), within singleton AND >=1 entry 0.498; precision of {1} sets 0.36 vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian BIN alpha=0.3; coverage 0.73, singleton share 0.74, AUC within singleton sets 0.737 (R0 same rows 0.624), within singleton AND >=1 entry 0.455; precision of {1} sets 0.6521739130434783 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian BIN alpha=0.3; coverage 0.81, singleton share 0.81, AUC within singleton sets 0.837 (R0 same rows 0.693), within singleton AND >=1 entry 0.481; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian HpF alpha=0.1; coverage 0.95, singleton share 0.37, AUC within singleton sets 0.848 (R0 same rows 0.652), within singleton AND >=1 entry 0.440; precision of {1} sets 0.4230769230769231 vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian HpF alpha=0.1; coverage 0.96, singleton share 0.12, AUC within singleton sets 0.663 (R0 same rows 0.470), within singleton AND >=1 entry nan; precision of {1} sets 0.3076923076923077 vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian HpF alpha=0.1; coverage 0.95, singleton share 0.36, AUC within singleton sets 0.852 (R0 same rows 0.639), within singleton AND >=1 entry 0.472; precision of {1} sets 0.4 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian HpF alpha=0.1; coverage 0.94, singleton share 0.65, AUC within singleton sets 0.892 (R0 same rows 0.662), within singleton AND >=1 entry 0.602; precision of {1} sets nan vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian HpF alpha=0.2; coverage 0.87, singleton share 0.53, AUC within singleton sets 0.809 (R0 same rows 0.662), within singleton AND >=1 entry 0.477; precision of {1} sets 0.4302325581395348 vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian HpF alpha=0.2; coverage 0.88, singleton share 0.27, AUC within singleton sets 0.559 (R0 same rows 0.476), within singleton AND >=1 entry 0.474; precision of {1} sets 0.38 vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian HpF alpha=0.2; coverage 0.85, singleton share 0.58, AUC within singleton sets 0.800 (R0 same rows 0.629), within singleton AND >=1 entry 0.497; precision of {1} sets 0.4545454545454545 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian HpF alpha=0.2; coverage 0.88, singleton share 0.74, AUC within singleton sets 0.867 (R0 same rows 0.647), within singleton AND >=1 entry 0.488; precision of {1} sets 0.5714285714285714 vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 POOLED: conformal Mondrian HpF alpha=0.3; coverage 0.78, singleton share 0.67, AUC within singleton sets 0.771 (R0 same rows 0.666), within singleton AND >=1 entry 0.483; precision of {1} sets 0.4792899408284023 vs base 0.332; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 ASIA: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.50, AUC within singleton sets 0.557 (R0 same rows 0.554), within singleton AND >=1 entry 0.510; precision of {1} sets 0.4356435643564356 vs base 0.401; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 LONDON: conformal Mondrian HpF alpha=0.3; coverage 0.76, singleton share 0.72, AUC within singleton sets 0.764 (R0 same rows 0.616), within singleton AND >=1 entry 0.469; precision of {1} sets 0.5333333333333333 vs base 0.368; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 5 NY: conformal Mondrian HpF alpha=0.3; coverage 0.81, singleton share 0.79, AUC within singleton sets 0.875 (R0 same rows 0.689), within singleton AND >=1 entry 0.539; precision of {1} sets 0.5652173913043478 vs base 0.226; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian R0 alpha=0.1; coverage 0.87, singleton share 0.60, AUC within singleton sets 0.726 (R0 same rows 0.726), within singleton AND >=1 entry 0.472; precision of {1} sets nan vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian R0 alpha=0.1; coverage 0.83, singleton share 0.50, AUC within singleton sets 0.540 (R0 same rows 0.540), within singleton AND >=1 entry 0.514; precision of {1} sets nan vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian R0 alpha=0.1; coverage 0.86, singleton share 0.53, AUC within singleton sets 0.721 (R0 same rows 0.721), within singleton AND >=1 entry 0.500; precision of {1} sets nan vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian R0 alpha=0.1; coverage 0.92, singleton share 0.76, AUC within singleton sets 0.738 (R0 same rows 0.738), within singleton AND >=1 entry 0.452; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian R0 alpha=0.2; coverage 0.78, singleton share 0.78, AUC within singleton sets 0.709 (R0 same rows 0.709), within singleton AND >=1 entry 0.491; precision of {1} sets nan vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian R0 alpha=0.2; coverage 0.71, singleton share 0.80, AUC within singleton sets 0.540 (R0 same rows 0.540), within singleton AND >=1 entry 0.521; precision of {1} sets nan vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian R0 alpha=0.2; coverage 0.78, singleton share 0.70, AUC within singleton sets 0.707 (R0 same rows 0.707), within singleton AND >=1 entry 0.517; precision of {1} sets nan vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian R0 alpha=0.2; coverage 0.86, singleton share 0.86, AUC within singleton sets 0.779 (R0 same rows 0.779), within singleton AND >=1 entry 0.469; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian R0 alpha=0.3; coverage 0.73, singleton share 0.86, AUC within singleton sets 0.708 (R0 same rows 0.708), within singleton AND >=1 entry 0.503; precision of {1} sets nan vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian R0 alpha=0.3; coverage 0.67, singleton share 0.91, AUC within singleton sets 0.534 (R0 same rows 0.534), within singleton AND >=1 entry 0.518; precision of {1} sets nan vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian R0 alpha=0.3; coverage 0.74, singleton share 0.76, AUC within singleton sets 0.703 (R0 same rows 0.703), within singleton AND >=1 entry 0.518; precision of {1} sets nan vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian R0 alpha=0.3; coverage 0.79, singleton share 0.90, AUC within singleton sets 0.818 (R0 same rows 0.818), within singleton AND >=1 entry 0.528; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian BIN alpha=0.1; coverage 0.95, singleton share 0.40, AUC within singleton sets 0.863 (R0 same rows 0.764), within singleton AND >=1 entry 0.476; precision of {1} sets nan vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian BIN alpha=0.1; coverage 0.93, singleton share 0.22, AUC within singleton sets 0.692 (R0 same rows 0.554), within singleton AND >=1 entry 0.602; precision of {1} sets nan vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian BIN alpha=0.1; coverage 0.96, singleton share 0.34, AUC within singleton sets 0.856 (R0 same rows 0.672), within singleton AND >=1 entry nan; precision of {1} sets nan vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian BIN alpha=0.1; coverage 0.95, singleton share 0.66, AUC within singleton sets 0.910 (R0 same rows 0.813), within singleton AND >=1 entry nan; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian BIN alpha=0.2; coverage 0.87, singleton share 0.61, AUC within singleton sets 0.787 (R0 same rows 0.714), within singleton AND >=1 entry 0.511; precision of {1} sets 0.6666666666666666 vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian BIN alpha=0.2; coverage 0.83, singleton share 0.50, AUC within singleton sets 0.614 (R0 same rows 0.552), within singleton AND >=1 entry 0.566; precision of {1} sets nan vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian BIN alpha=0.2; coverage 0.88, singleton share 0.52, AUC within singleton sets 0.774 (R0 same rows 0.673), within singleton AND >=1 entry 0.526; precision of {1} sets nan vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian BIN alpha=0.2; coverage 0.90, singleton share 0.83, AUC within singleton sets 0.841 (R0 same rows 0.754), within singleton AND >=1 entry 0.429; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian BIN alpha=0.3; coverage 0.78, singleton share 0.75, AUC within singleton sets 0.777 (R0 same rows 0.722), within singleton AND >=1 entry 0.545; precision of {1} sets 0.6 vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian BIN alpha=0.3; coverage 0.74, singleton share 0.71, AUC within singleton sets 0.597 (R0 same rows 0.559), within singleton AND >=1 entry 0.562; precision of {1} sets 0.6666666666666666 vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian BIN alpha=0.3; coverage 0.78, singleton share 0.65, AUC within singleton sets 0.771 (R0 same rows 0.682), within singleton AND >=1 entry 0.547; precision of {1} sets 0.5 vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian BIN alpha=0.3; coverage 0.80, singleton share 0.90, AUC within singleton sets 0.884 (R0 same rows 0.818), within singleton AND >=1 entry 0.577; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian HpF alpha=0.1; coverage 0.95, singleton share 0.40, AUC within singleton sets 0.887 (R0 same rows 0.828), within singleton AND >=1 entry 0.513; precision of {1} sets 0.5416666666666666 vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian HpF alpha=0.1; coverage 0.96, singleton share 0.15, AUC within singleton sets 0.768 (R0 same rows 0.697), within singleton AND >=1 entry 0.642; precision of {1} sets 0.5833333333333334 vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian HpF alpha=0.1; coverage 0.93, singleton share 0.36, AUC within singleton sets 0.882 (R0 same rows 0.801), within singleton AND >=1 entry 0.476; precision of {1} sets 0.5 vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian HpF alpha=0.1; coverage 0.95, singleton share 0.68, AUC within singleton sets 0.864 (R0 same rows 0.827), within singleton AND >=1 entry 0.419; precision of {1} sets nan vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian HpF alpha=0.2; coverage 0.87, singleton share 0.54, AUC within singleton sets 0.820 (R0 same rows 0.771), within singleton AND >=1 entry 0.486; precision of {1} sets 0.4603174603174603 vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian HpF alpha=0.2; coverage 0.86, singleton share 0.32, AUC within singleton sets 0.614 (R0 same rows 0.636), within singleton AND >=1 entry 0.537; precision of {1} sets 0.3684210526315789 vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian HpF alpha=0.2; coverage 0.86, singleton share 0.52, AUC within singleton sets 0.810 (R0 same rows 0.729), within singleton AND >=1 entry 0.451; precision of {1} sets 0.5294117647058824 vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian HpF alpha=0.2; coverage 0.90, singleton share 0.79, AUC within singleton sets 0.867 (R0 same rows 0.798), within singleton AND >=1 entry 0.473; precision of {1} sets 0.75 vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 POOLED: conformal Mondrian HpF alpha=0.3; coverage 0.79, singleton share 0.65, AUC within singleton sets 0.785 (R0 same rows 0.761), within singleton AND >=1 entry 0.500; precision of {1} sets 0.4814814814814814 vs base 0.312; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 ASIA: conformal Mondrian HpF alpha=0.3; coverage 0.78, singleton share 0.50, AUC within singleton sets 0.575 (R0 same rows 0.637), within singleton AND >=1 entry 0.517; precision of {1} sets 0.4444444444444444 vs base 0.389; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 LONDON: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.64, AUC within singleton sets 0.754 (R0 same rows 0.695), within singleton AND >=1 entry 0.456; precision of {1} sets 0.5161290322580645 vs base 0.353; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 15 NY: conformal Mondrian HpF alpha=0.3; coverage 0.81, singleton share 0.82, AUC within singleton sets 0.867 (R0 same rows 0.825), within singleton AND >=1 entry 0.518; precision of {1} sets 0.5714285714285714 vs base 0.193; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian R0 alpha=0.1; coverage 0.88, singleton share 0.56, AUC within singleton sets 0.739 (R0 same rows 0.739), within singleton AND >=1 entry 0.530; precision of {1} sets nan vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian R0 alpha=0.1; coverage 0.83, singleton share 0.44, AUC within singleton sets 0.507 (R0 same rows 0.507), within singleton AND >=1 entry 0.518; precision of {1} sets nan vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian R0 alpha=0.1; coverage 0.88, singleton share 0.52, AUC within singleton sets 0.736 (R0 same rows 0.736), within singleton AND >=1 entry 0.602; precision of {1} sets nan vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian R0 alpha=0.1; coverage 0.94, singleton share 0.73, AUC within singleton sets 0.699 (R0 same rows 0.699), within singleton AND >=1 entry 0.546; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian R0 alpha=0.2; coverage 0.81, singleton share 0.74, AUC within singleton sets 0.685 (R0 same rows 0.685), within singleton AND >=1 entry 0.496; precision of {1} sets nan vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian R0 alpha=0.2; coverage 0.75, singleton share 0.70, AUC within singleton sets 0.452 (R0 same rows 0.452), within singleton AND >=1 entry 0.461; precision of {1} sets nan vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian R0 alpha=0.2; coverage 0.81, singleton share 0.70, AUC within singleton sets 0.667 (R0 same rows 0.667), within singleton AND >=1 entry 0.578; precision of {1} sets nan vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian R0 alpha=0.2; coverage 0.88, singleton share 0.83, AUC within singleton sets 0.774 (R0 same rows 0.774), within singleton AND >=1 entry 0.542; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian R0 alpha=0.3; coverage 0.74, singleton share 0.84, AUC within singleton sets 0.703 (R0 same rows 0.703), within singleton AND >=1 entry 0.522; precision of {1} sets nan vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian R0 alpha=0.3; coverage 0.69, singleton share 0.86, AUC within singleton sets 0.492 (R0 same rows 0.492), within singleton AND >=1 entry 0.496; precision of {1} sets nan vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian R0 alpha=0.3; coverage 0.72, singleton share 0.81, AUC within singleton sets 0.703 (R0 same rows 0.703), within singleton AND >=1 entry 0.586; precision of {1} sets nan vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian R0 alpha=0.3; coverage 0.81, singleton share 0.85, AUC within singleton sets 0.807 (R0 same rows 0.807), within singleton AND >=1 entry 0.569; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian BIN alpha=0.1; coverage 0.95, singleton share 0.42, AUC within singleton sets 0.877 (R0 same rows 0.727), within singleton AND >=1 entry 0.552; precision of {1} sets nan vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.21, AUC within singleton sets 0.693 (R0 same rows 0.463), within singleton AND >=1 entry 0.608; precision of {1} sets nan vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian BIN alpha=0.1; coverage 0.94, singleton share 0.39, AUC within singleton sets 0.867 (R0 same rows 0.705), within singleton AND >=1 entry 0.630; precision of {1} sets nan vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian BIN alpha=0.1; coverage 0.97, singleton share 0.66, AUC within singleton sets 0.872 (R0 same rows 0.624), within singleton AND >=1 entry nan; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian BIN alpha=0.2; coverage 0.87, singleton share 0.59, AUC within singleton sets 0.816 (R0 same rows 0.719), within singleton AND >=1 entry 0.524; precision of {1} sets nan vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian BIN alpha=0.2; coverage 0.84, singleton share 0.48, AUC within singleton sets 0.588 (R0 same rows 0.508), within singleton AND >=1 entry 0.530; precision of {1} sets nan vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian BIN alpha=0.2; coverage 0.88, singleton share 0.51, AUC within singleton sets 0.817 (R0 same rows 0.683), within singleton AND >=1 entry 0.550; precision of {1} sets nan vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian BIN alpha=0.2; coverage 0.90, singleton share 0.77, AUC within singleton sets 0.901 (R0 same rows 0.775), within singleton AND >=1 entry 0.503; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian BIN alpha=0.3; coverage 0.77, singleton share 0.73, AUC within singleton sets 0.781 (R0 same rows 0.698), within singleton AND >=1 entry 0.537; precision of {1} sets 0.4444444444444444 vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian BIN alpha=0.3; coverage 0.75, singleton share 0.67, AUC within singleton sets 0.597 (R0 same rows 0.500), within singleton AND >=1 entry 0.557; precision of {1} sets 0.375 vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian BIN alpha=0.3; coverage 0.77, singleton share 0.69, AUC within singleton sets 0.777 (R0 same rows 0.675), within singleton AND >=1 entry 0.544; precision of {1} sets 0.5 vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian BIN alpha=0.3; coverage 0.79, singleton share 0.85, AUC within singleton sets 0.886 (R0 same rows 0.777), within singleton AND >=1 entry 0.492; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian HpF alpha=0.1; coverage 0.94, singleton share 0.43, AUC within singleton sets 0.878 (R0 same rows 0.740), within singleton AND >=1 entry 0.469; precision of {1} sets 0.4642857142857143 vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian HpF alpha=0.1; coverage 0.94, singleton share 0.18, AUC within singleton sets 0.699 (R0 same rows 0.396), within singleton AND >=1 entry 0.553; precision of {1} sets 0.4375 vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian HpF alpha=0.1; coverage 0.93, singleton share 0.42, AUC within singleton sets 0.860 (R0 same rows 0.701), within singleton AND >=1 entry 0.425; precision of {1} sets 0.5 vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian HpF alpha=0.1; coverage 0.96, singleton share 0.70, AUC within singleton sets 0.893 (R0 same rows 0.732), within singleton AND >=1 entry 0.365; precision of {1} sets nan vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian HpF alpha=0.2; coverage 0.86, singleton share 0.57, AUC within singleton sets 0.841 (R0 same rows 0.764), within singleton AND >=1 entry 0.506; precision of {1} sets 0.5064935064935064 vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian HpF alpha=0.2; coverage 0.85, singleton share 0.38, AUC within singleton sets 0.631 (R0 same rows 0.559), within singleton AND >=1 entry 0.549; precision of {1} sets 0.48 vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian HpF alpha=0.2; coverage 0.86, singleton share 0.52, AUC within singleton sets 0.839 (R0 same rows 0.704), within singleton AND >=1 entry 0.459; precision of {1} sets 0.5263157894736842 vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian HpF alpha=0.2; coverage 0.88, singleton share 0.80, AUC within singleton sets 0.915 (R0 same rows 0.831), within singleton AND >=1 entry 0.562; precision of {1} sets 0.625 vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 POOLED: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.67, AUC within singleton sets 0.790 (R0 same rows 0.730), within singleton AND >=1 entry 0.497; precision of {1} sets 0.472 vs base 0.301; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 ASIA: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.55, AUC within singleton sets 0.597 (R0 same rows 0.539), within singleton AND >=1 entry 0.540; precision of {1} sets 0.419753086419753 vs base 0.377; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 LONDON: conformal Mondrian HpF alpha=0.3; coverage 0.77, singleton share 0.66, AUC within singleton sets 0.781 (R0 same rows 0.692), within singleton AND >=1 entry 0.466; precision of {1} sets 0.53125 vs base 0.344; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain 30 NY: conformal Mondrian HpF alpha=0.3; coverage 0.76, singleton share 0.80, AUC within singleton sets 0.908 (R0 same rows 0.822), within singleton AND >=1 entry 0.561; precision of {1} sets 0.6666666666666666 vs base 0.182; singleton selection inflates AUC by removing the mid-range
- X15-conformal-abstain-fullcov 0 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 5 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 15 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 30 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 0 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 5 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 15 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 30 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 0 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 5 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 15 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
- X15-conformal-abstain-fullcov 30 POOLED: full-coverage unconditional AUC of the same predictor as the X15 conformal cells
