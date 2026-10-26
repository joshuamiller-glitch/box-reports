# PRED ROUND 12 - block G round 1 - G-regime-sequence

Best HOLDOUT F-R AUC: +15 POOLED 0.536 [-,-] | ASIA 0.555 [-,-] | LONDON 0.586 [-,-] | NY 0.552 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.542 [-,-] | ASIA 0.560 [-,-] | LONDON 0.584 [-,-] | NY 0.579 [-,-]
Best G HOLDOUT AUC: 0.616 [0.57,0.66]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 8168b9e8e4c2bf9f1fa7b9f87557c50e5f9f19a001bd5b5cd1904bdcdd1e9dc8 ; trials added 2400 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': True, 'note': 'G1/G2/G4/G5/G7: first audit had 266 mismatches (HMM float32 refit nondeterminism: audit used a re-fit parameter file); canonicalised on G_series2.npz, features rebuilt, re-run 0/43,920. G3/G6 prefix audit 0/10,086,582. decisions 360 (A full-refilter 36); feature checks 43920; mismatches 0; by feature {} | G3/G6 prefix audit: cuts 5; feature checks 10086582; mismatches 0; detail {}'} ; holdout scored True ; feature store ['l2vast/pred/store/G1.parquet', 'l2vast/pred/store/G2.parquet', 'l2vast/pred/store/G4.parquet', 'l2vast/pred/store/G5.parquet', 'l2vast/pred/store/G7.parquet', 'l2vast/pred/store/G1_sig.parquet', 'l2vast/pred/store/G2_sig.parquet', 'l2vast/pred/store/G4_sig.parquet', 'l2vast/pred/store/G5_sig.parquet', 'l2vast/pred/store/G7_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1 | +45 | LONDON | rf | - | 0.617 [-,-] | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | NY | rf | 0.605 [0.57,0.64] | 0.616 [0.57,0.66] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | LONDON | logit2 | 0.627 [0.59,0.66] | 0.606 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | LONDON | logit2 | 0.626 [0.59,0.66] | 0.604 [0.56,0.65] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | LONDON | rf | - | 0.604 [-,-] | - | - | 0.658 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED/ST | rf | 0.589 [0.57,0.62] | 0.600 [0.57,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +20 | NY | stack | - | 0.600 [-,-] | - | - | 0.835 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +60 | NY | gbt3 | - | 0.599 [-,-] | - | - | 0.880 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +60 | NY | gbt3 | - | 0.599 [-,-] | - | - | 0.880 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | NY | logit2 | 0.604 [0.57,0.64] | 0.599 [0.55,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +60 | NY | gbt3 | - | 0.598 [-,-] | - | - | 0.878 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +60 | NY | gbt3 | - | 0.598 [-,-] | - | - | 0.878 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | NY | gbt3 | - | 0.598 [-,-] | - | - | 0.878 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +60 | NY | gbt3 | - | 0.598 [-,-] | - | - | 0.878 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED | rf | 0.588 [0.57,0.61] | 0.594 [0.57,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +10 | LONDON | rf | - | 0.591 [-,-] | - | - | 0.611 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | LONDON | gbt3 | - | 0.590 [-,-] | - | - | 0.617 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED/HM | rf | 0.588 [0.57,0.60] | 0.589 [0.56,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +20 | NY | stack | - | 0.588 [-,-] | - | - | 0.814 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | ASIA | stack | 0.564 [0.54,0.59] | 0.586 [0.56,0.62] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | LONDON | rf | - | 0.586 [-,-] | - | - | 0.588 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +30 | LONDON | rf | - | 0.584 [-,-] | - | - | 0.605 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED/HM | rf | 0.587 [0.57,0.60] | 0.583 [0.55,0.61] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED | rf | 0.583 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED/ST | rf | 0.580 [0.56,0.61] | 0.582 [0.55,0.62] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | NY | stack | - | 0.582 [-,-] | - | - | 0.833 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +30 | LONDON | gbt3 | - | 0.581 [-,-] | - | - | 0.601 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +20 | ASIA | stack | - | 0.580 [-,-] | - | - | 0.571 | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +30 | NY | stack | - | 0.579 [-,-] | - | - | 0.798 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +20 | NY | stack | - | 0.575 [-,-] | - | - | 0.829 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +45 | ASIA | logit2 | - | 0.573 [-,-] | - | - | 0.573 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +20 | LONDON | logit2 | - | 0.572 [-,-] | - | - | 0.606 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | NY | rf | - | 0.571 [-,-] | - | - | 0.766 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +45 | NY | gbt3 | - | 0.571 [-,-] | - | - | 0.805 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | pre | LONDON | gbt3 | - | 0.571 [-,-] | - | - | 0.599 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | ASIA | logit2 | 0.544 [0.52,0.57] | 0.569 [0.53,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | NY | logit2 | 0.572 [0.54,0.61] | 0.567 [0.51,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +10 | NY | rf | - | 0.567 [-,-] | - | - | 0.767 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +45 | LONDON | logit2 | - | 0.566 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +30 | LONDON | logit2 | - | 0.564 [-,-] | - | - | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +10 | LONDON | logit2 | - | 0.564 [-,-] | - | - | 0.587 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +10 | LONDON | logit2 | - | 0.564 [-,-] | - | - | 0.587 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +45 | LONDON | stack | - | 0.564 [-,-] | - | - | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | LONDON | gbt3 | - | 0.563 [-,-] | - | - | 0.599 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +10 | NY | rf | - | 0.561 [-,-] | - | - | 0.767 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +30 | ASIA | stack | - | 0.560 [-,-] | - | - | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +15 | LONDON | rf | - | 0.560 [-,-] | - | - | 0.588 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +45 | ASIA | logit2 | - | 0.560 [-,-] | - | - | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +20 | ASIA | logit2 | - | 0.558 [-,-] | - | - | 0.546 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +45 | POOLED | rf | - | 0.558 [-,-] | - | - | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | POOLED/ST | rf | 0.543 [0.52,0.56] | 0.557 [0.53,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | NY | gbt3 | - | 0.557 [-,-] | - | - | 0.808 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +30 | NY | gbt3 | - | 0.557 [-,-] | - | - | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +30 | NY | gbt3 | - | 0.557 [-,-] | - | - | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +60 | LONDON | rf | - | 0.557 [-,-] | - | - | 0.622 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | POOLED | logit2 | 0.549 [0.53,0.57] | 0.556 [0.53,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | NY | rf | - | 0.555 [-,-] | - | - | 0.749 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | ASIA | stack | 0.529 [0.50,0.56] | 0.555 [0.51,0.59] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | ASIA | rf | - | 0.555 [-,-] | - | - | 0.565 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +20 | NY | stack | - | 0.554 [-,-] | - | - | 0.828 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +5 | ASIA | gbt3 | - | 0.553 [-,-] | - | - | 0.550 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +5 | ASIA | gbt3 | - | 0.553 [-,-] | - | - | 0.550 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | LONDON | rf | - | 0.553 [-,-] | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | POOLED/ST | rf | 0.546 [0.53,0.57] | 0.552 [0.52,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | NY | stack | - | 0.552 [-,-] | - | - | 0.807 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +20 | NY | stack | - | 0.552 [-,-] | - | - | 0.812 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +5 | NY | logit2 | - | 0.552 [-,-] | - | - | 0.581 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | NY | rf | - | 0.552 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +45 | ASIA | logit2 | - | 0.551 [-,-] | - | - | 0.552 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | POOLED | rf | 0.541 [0.52,0.56] | 0.551 [0.53,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +30 | ASIA | stack | - | 0.550 [-,-] | - | - | 0.540 | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | POOLED | rf | - | 0.550 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +20 | LONDON | gbt3 | - | 0.548 [-,-] | - | - | 0.535 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | ASIA | stack | 0.542 [0.51,0.57] | 0.548 [0.51,0.59] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +45 | ASIA | logit2 | - | 0.548 [-,-] | - | - | 0.536 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +45 | NY | rf | - | 0.547 [-,-] | - | - | 0.660 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +10 | LONDON | gbt3 | - | 0.546 [-,-] | - | - | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +20 | NY | gbt3 | - | 0.546 [-,-] | - | - | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +30 | NY | rf | - | 0.546 [-,-] | - | - | 0.665 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +30 | ASIA | gbt3 | - | 0.545 [-,-] | - | - | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +15 | ASIA | stack | - | 0.545 [-,-] | - | - | 0.540 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | POOLED/HM | logit2 | 0.552 [0.53,0.58] | 0.545 [0.52,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +10 | LONDON | stack | - | 0.545 [-,-] | - | - | 0.678 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +30 | NY | gbt3 | - | 0.544 [-,-] | - | - | 0.795 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | LONDON | rf | 0.549 [0.52,0.58] | 0.544 [0.51,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | LONDON | logit2 | - | 0.544 [-,-] | - | - | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +45 | NY | gbt3 | - | 0.543 [-,-] | - | - | 0.802 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +45 | POOLED | rf | - | 0.543 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | ASIA | rf | - | 0.542 [-,-] | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +45 | LONDON | rf | - | 0.542 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| GALL | pre | LONDON | logit2 | - | 0.542 [-,-] | - | - | 0.585 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +30 | POOLED | rf | - | 0.542 [-,-] | - | - | 0.683 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +30 | POOLED | gbt3 | - | 0.541 [-,-] | - | - | 0.683 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +30 | LONDON | gbt3 | - | 0.541 [-,-] | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +30 | POOLED | rf | - | 0.540 [-,-] | - | - | 0.616 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +30 | NY | gbt3 | - | 0.540 [-,-] | - | - | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | pre | NY | stack | - | 0.540 [-,-] | - | - | 0.506 | ok | - | - | - | - |  | locked label (reference only) |
| G5 | +30 | ASIA | stack | - | 0.540 [-,-] | - | - | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +45 | NY | gbt3 | - | 0.540 [-,-] | - | - | 0.795 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +45 | NY | gbt3 | - | 0.540 [-,-] | - | - | 0.795 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +45 | NY | gbt3 | - | 0.540 [-,-] | - | - | 0.795 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +30 | ASIA | stack | - | 0.539 [-,-] | - | - | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +30 | ASIA | rf | - | 0.539 [-,-] | - | - | 0.543 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | LONDON | rf | - | 0.539 [-,-] | - | - | 0.659 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +15 | ASIA | gbt3 | - | 0.539 [-,-] | - | - | 0.527 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +30 | ASIA | gbt3 | - | 0.539 [-,-] | - | - | 0.516 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +5 | LONDON | gbt3 | - | 0.538 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +10 | LONDON | stack | - | 0.538 [-,-] | - | - | 0.525 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | POOLED/HM | gbt3 | 0.527 [0.50,0.55] | 0.538 [0.51,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | ASIA | stack | - | 0.538 [-,-] | - | - | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +30 | NY | rf | - | 0.538 [-,-] | - | - | 0.791 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +60 | ASIA | stack | - | 0.537 [-,-] | - | - | 0.525 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +45 | POOLED | logit2 | - | 0.537 [-,-] | - | - | 0.639 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | NY | gbt3 | - | 0.536 [-,-] | - | - | 0.586 | N | - | - | - | - |  | locked label (reference only) |
| G5 | pre | ASIA | logit2 | - | 0.536 [-,-] | - | - | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| G7 | pre | ASIA | rf | - | 0.536 [-,-] | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | POOLED/HM | rf | 0.518 [0.49,0.54] | 0.536 [0.51,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +60 | POOLED | rf | - | 0.536 [-,-] | - | - | 0.703 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | POOLED | rf | - | 0.536 [-,-] | - | - | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +5 | NY | logit2 | - | 0.536 [-,-] | - | - | 0.488 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +60 | LONDON | rf | - | 0.535 [-,-] | - | - | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | ASIA | rf | - | 0.535 [-,-] | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.525 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +10 | ASIA | rf | - | 0.535 [-,-] | - | - | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +5 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +5 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +5 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | LONDON | rf | 0.542 [0.51,0.57] | 0.535 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +30 | POOLED | rf | - | 0.535 [-,-] | - | - | 0.607 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | ASIA | rf | - | 0.535 [-,-] | - | - | 0.545 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +5 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +45 | LONDON | rf | - | 0.534 [-,-] | - | - | 0.547 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +5 | NY | rf | - | 0.534 [-,-] | - | - | 0.723 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +60 | ASIA | stack | - | 0.534 [-,-] | - | - | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | pre | ASIA | rf | - | 0.534 [-,-] | - | - | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | pre | ASIA | rf | - | 0.533 [-,-] | - | - | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G4 | sig | NY | gbt3 | 0.534 [0.51,0.57] | 0.533 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +20 | POOLED | stack | - | 0.533 [-,-] | - | - | 0.604 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | NY | rf | - | 0.533 [-,-] | - | - | 0.717 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | pre | ASIA | rf | - | 0.532 [-,-] | - | - | 0.530 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | pre | ASIA | stack | - | 0.532 [-,-] | - | - | 0.530 | ok | - | - | - | - |  | locked label (reference only) |
| GALL | +45 | POOLED | rf | - | 0.532 [-,-] | - | - | 0.621 | N | - | - | - | - |  | locked label (reference only) |
| G2 | pre | NY | gbt3 | - | 0.532 [-,-] | - | - | 0.563 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +5 | NY | rf | - | 0.532 [-,-] | - | - | 0.715 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +15 | ASIA | rf | - | 0.531 [-,-] | - | - | 0.543 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +60 | POOLED | rf | - | 0.531 [-,-] | - | - | 0.703 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +60 | POOLED | rf | - | 0.531 [-,-] | - | - | 0.703 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +30 | ASIA | stack | - | 0.531 [-,-] | - | - | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | pre | NY | logit2 | - | 0.530 [-,-] | - | - | 0.571 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +30 | POOLED | gbt3 | - | 0.530 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +60 | ASIA | stack | - | 0.530 [-,-] | - | - | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +10 | NY | rf | - | 0.530 [-,-] | - | - | 0.741 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | LONDON | logit2 | 0.533 [0.50,0.57] | 0.530 [0.48,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +60 | ASIA | gbt3 | - | 0.529 [-,-] | - | - | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | ASIA | rf | - | 0.529 [-,-] | - | - | 0.525 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +15 | POOLED | rf | - | 0.529 [-,-] | - | - | 0.699 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +15 | POOLED | rf | - | 0.528 [-,-] | - | - | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +20 | POOLED | gbt3 | - | 0.528 [-,-] | - | - | 0.691 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | NY | stack | - | 0.528 [-,-] | - | - | 0.763 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | POOLED | gbt3 | - | 0.528 [-,-] | - | - | 0.705 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +5 | NY | stack | - | 0.528 [-,-] | - | - | 0.531 | ok | - | - | - | - |  | locked label (reference only) |
| G5 | +10 | ASIA | rf | - | 0.528 [-,-] | - | - | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | POOLED | gbt3 | 0.514 [0.50,0.53] | 0.527 [0.50,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | NY | gbt3 | 0.547 [0.51,0.58] | 0.527 [0.47,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G5 | +45 | ASIA | gbt3 | - | 0.526 [-,-] | - | - | 0.532 | N | - | - | - | - |  | locked label (reference only) |
| G1 | pre | ASIA | stack | - | 0.526 [-,-] | - | - | 0.523 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +10 | ASIA | rf | - | 0.525 [-,-] | - | - | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +10 | POOLED | rf | - | 0.525 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED/ST | logit2 | 0.511 [0.49,0.54] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G2 | +30 | NY | rf | - | 0.525 [-,-] | - | - | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | POOLED/ST | logit2 | 0.510 [0.49,0.53] | 0.525 [0.50,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G7 | sig | ASIA | rf | 0.518 [0.49,0.55] | 0.525 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | POOLED/HM | stack | 0.512 [0.49,0.53] | 0.525 [0.49,0.56] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| GALL | +30 | NY | logit2 | - | 0.525 [-,-] | - | - | 0.638 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +10 | POOLED | rf | - | 0.524 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +15 | ASIA | rf | - | 0.524 [-,-] | - | - | 0.536 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +45 | ASIA | rf | - | 0.523 [-,-] | - | - | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +10 | POOLED | rf | - | 0.523 [-,-] | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +15 | POOLED | rf | - | 0.523 [-,-] | - | - | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +30 | ASIA | logit2 | - | 0.523 [-,-] | - | - | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +5 | LONDON | rf | - | 0.521 [-,-] | - | - | 0.549 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | ASIA | rf | - | 0.521 [-,-] | - | - | 0.508 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +15 | ASIA | logit2 | - | 0.521 [-,-] | - | - | 0.514 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | NY | logit2 | 0.517 [0.48,0.55] | 0.521 [0.47,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| GALL | +5 | NY | rf | - | 0.520 [-,-] | - | - | 0.704 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +60 | LONDON | rf | - | 0.520 [-,-] | - | - | 0.574 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +60 | ASIA | stack | - | 0.520 [-,-] | - | - | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +60 | POOLED | rf | - | 0.520 [-,-] | - | - | 0.618 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +60 | ASIA | stack | - | 0.520 [-,-] | - | - | 0.509 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | pre | LONDON | gbt3 | - | 0.519 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +10 | ASIA | rf | - | 0.519 [-,-] | - | - | 0.517 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | NY | gbt3 | 0.526 [0.49,0.56] | 0.519 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | NY | stack | - | 0.518 [-,-] | - | - | 0.798 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +45 | ASIA | gbt3 | - | 0.518 [-,-] | - | - | 0.516 | N | - | - | - | - |  | locked label (reference only) |
| G7 | pre | LONDON | gbt3 | - | 0.518 [-,-] | - | - | 0.651 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G5 | sig | POOLED/HM | gbt3 | 0.533 [0.51,0.56] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | ASIA | gbt3 | 0.520 [0.50,0.54] | 0.517 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED | logit2 | 0.513 [0.49,0.53] | 0.517 [0.49,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| GALL | +15 | LONDON | gbt3 | - | 0.517 [-,-] | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +60 | LONDON | rf | - | 0.517 [-,-] | - | - | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL+BASE | sig | LONDON | gbt3 | 0.521 [0.48,0.55] | 0.517 [0.47,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G2 | +10 | ASIA | rf | - | 0.517 [-,-] | - | - | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +15 | NY | stack | - | 0.517 [-,-] | - | - | 0.531 | ok | - | - | - | - |  | locked label (reference only) |
| G5 | +5 | NY | stack | - | 0.517 [-,-] | - | - | 0.480 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G7 | sig | NY | gbt3 | 0.549 [0.51,0.59] | 0.517 [0.45,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +15 | NY | stack | - | 0.516 [-,-] | - | - | 0.799 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +30 | LONDON | logit2 | - | 0.516 [-,-] | - | - | 0.574 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | pre | NY | rf | - | 0.516 [-,-] | - | - | 0.580 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +15 | POOLED | rf | - | 0.516 [-,-] | - | - | 0.692 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +15 | POOLED | stack | - | 0.516 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G2 | sig | POOLED/ST | stack | 0.516 [0.49,0.54] | 0.516 [0.48,0.55] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | POOLED | gbt3 | - | 0.516 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | LONDON | gbt3 | 0.527 [0.50,0.56] | 0.516 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +10 | LONDON | gbt3 | - | 0.516 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | LONDON | rf | 0.520 [0.49,0.55] | 0.516 [0.48,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL | sig | ASIA | logit2 | 0.502 [0.48,0.53] | 0.516 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +60 | LONDON | rf | - | 0.516 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | POOLED | gbt3 | 0.514 [0.50,0.53] | 0.515 [0.49,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +60 | POOLED | logit2 | - | 0.515 [-,-] | - | - | 0.613 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +10 | POOLED | rf | - | 0.515 [-,-] | - | - | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G7 | sig | NY | gbt3 | 0.524 [0.48,0.56] | 0.515 [0.46,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +30 | LONDON | gbt3 | - | 0.515 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +30 | LONDON | gbt3 | - | 0.515 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +30 | LONDON | gbt3 | - | 0.515 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-BASE | sig | POOLED/HM | rf | 0.514 [0.49,0.54] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +20 | ASIA | stack | - | 0.515 [-,-] | - | - | 0.502 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +20 | POOLED | rf | - | 0.515 [-,-] | - | - | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +45 | POOLED | gbt3 | - | 0.515 [-,-] | - | - | 0.674 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +60 | POOLED | gbt3 | - | 0.515 [-,-] | - | - | 0.694 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +60 | POOLED | gbt3 | - | 0.515 [-,-] | - | - | 0.694 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +5 | NY | rf | - | 0.514 [-,-] | - | - | 0.709 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +15 | ASIA | gbt3 | - | 0.514 [-,-] | - | - | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | ASIA | logit2 | - | 0.514 [-,-] | - | - | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +20 | ASIA | logit2 | - | 0.514 [-,-] | - | - | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +20 | POOLED | rf | - | 0.514 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +20 | ASIA | logit2 | - | 0.513 [-,-] | - | - | 0.505 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | NY | logit2 | - | 0.513 [-,-] | - | - | 0.572 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +30 | POOLED | stack | - | 0.513 [-,-] | - | - | 0.582 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +20 | ASIA | rf | - | 0.513 [-,-] | - | - | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +60 | LONDON | rf | - | 0.513 [-,-] | - | - | 0.663 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +60 | NY | logit2 | - | 0.513 [-,-] | - | - | 0.521 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | POOLED | rf | - | 0.513 [-,-] | - | - | 0.602 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +30 | NY | logit2 | - | 0.513 [-,-] | - | - | 0.553 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G7 | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.512 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +60 | LONDON | rf | - | 0.512 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G2 | sig | LONDON | stack | 0.502 [0.47,0.53] | 0.511 [0.47,0.55] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +5 | NY | rf | - | 0.511 [-,-] | - | - | 0.709 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +15 | POOLED | logit2 | - | 0.511 [-,-] | - | - | 0.615 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +15 | NY | stack | - | 0.511 [-,-] | - | - | 0.797 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +45 | ASIA | rf | - | 0.510 [-,-] | - | - | 0.492 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +20 | POOLED | rf | - | 0.510 [-,-] | - | - | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G1 | sig | POOLED/HM | rf | 0.517 [0.49,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +15 | LONDON | rf | - | 0.509 [-,-] | - | - | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | LONDON | gbt3 | 0.511 [0.48,0.54] | 0.509 [0.47,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G7 | sig | POOLED/HM | gbt3 | 0.522 [0.50,0.54] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | LONDON | gbt3 | - | 0.509 [-,-] | - | - | 0.658 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | LONDON | gbt3 | - | 0.509 [-,-] | - | - | 0.507 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | POOLED/HM | rf | 0.519 [0.49,0.54] | 0.509 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED | logit2 | 0.502 [0.48,0.52] | 0.508 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | POOLED/HM | gbt3 | 0.503 [0.48,0.53] | 0.508 [0.47,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | LONDON | logit2 | - | 0.507 [-,-] | - | - | 0.491 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | POOLED/HM | logit2 | 0.514 [0.49,0.54] | 0.507 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| G4 | +10 | NY | gbt3 | - | 0.507 [-,-] | - | - | 0.567 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +20 | ASIA | rf | - | 0.506 [-,-] | - | - | 0.497 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +30 | POOLED | rf | - | 0.506 [-,-] | - | - | 0.590 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | POOLED/HM | rf | 0.520 [0.50,0.54] | 0.506 [0.47,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G5 | +15 | LONDON | stack | - | 0.506 [-,-] | - | - | 0.520 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-GALL+BASE | sig | ASIA | logit2 | 0.504 [0.47,0.53] | 0.506 [0.46,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| GALL | +20 | POOLED | gbt3 | - | 0.505 [-,-] | - | - | 0.570 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +30 | ASIA | stack | - | 0.505 [-,-] | - | - | 0.491 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | ASIA | rf | 0.501 [0.48,0.52] | 0.505 [0.47,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | LONDON | gbt3 | - | 0.505 [-,-] | - | - | 0.511 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +20 | LONDON | gbt3 | - | 0.505 [-,-] | - | - | 0.487 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | ASIA | stack | - | 0.505 [-,-] | - | - | 0.508 | ok | - | - | - | - |  | locked label (reference only) |
| GALL | +20 | POOLED | stack | - | 0.505 [-,-] | - | - | 0.672 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | pre | LONDON | rf | - | 0.505 [-,-] | - | - | 0.640 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +20 | ASIA | logit2 | - | 0.505 [-,-] | - | - | 0.494 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +45 | NY | gbt3 | - | 0.504 [-,-] | - | - | 0.618 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +15 | NY | stack | - | 0.504 [-,-] | - | - | 0.757 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +45 | POOLED | gbt3 | - | 0.504 [-,-] | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +45 | POOLED | gbt3 | - | 0.504 [-,-] | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G2 | sig | NY | gbt3 | 0.520 [0.48,0.55] | 0.503 [0.46,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +30 | NY | logit2 | - | 0.503 [-,-] | - | - | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | LONDON | gbt3 | - | 0.503 [-,-] | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +10 | ASIA | gbt3 | - | 0.503 [-,-] | - | - | 0.495 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | NY | gbt3 | 0.510 [0.47,0.55] | 0.503 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +15 | NY | gbt3 | - | 0.502 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +60 | LONDON | rf | - | 0.502 [-,-] | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +30 | NY | stack | - | 0.502 [-,-] | - | - | 0.554 | ok | - | - | - | - |  | locked label (reference only) |
| G4 | +45 | LONDON | gbt3 | - | 0.501 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +45 | LONDON | gbt3 | - | 0.501 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +45 | LONDON | gbt3 | - | 0.501 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | pre | LONDON | rf | - | 0.501 [-,-] | - | - | 0.638 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +30 | ASIA | rf | - | 0.501 [-,-] | - | - | 0.480 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G4 | sig | POOLED | gbt3 | 0.494 [0.47,0.51] | 0.501 [0.48,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | ASIA | stack | 0.506 [0.48,0.53] | 0.500 [0.47,0.54] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +30 | LONDON | gbt3 | - | 0.500 [-,-] | - | - | 0.503 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | POOLED | stack | - | 0.500 [-,-] | - | - | 0.660 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G5 | sig | POOLED | gbt3 | 0.512 [0.50,0.53] | 0.499 [0.48,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G5 | +45 | LONDON | stack | - | 0.499 [-,-] | - | - | 0.504 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +45 | POOLED | rf | - | 0.499 [-,-] | - | - | 0.578 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +30 | LONDON | stack | - | 0.499 [-,-] | - | - | 0.506 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | LONDON | logit2 | 0.496 [0.46,0.53] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | ASIA | rf | - | 0.498 [-,-] | - | - | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | NY | gbt3 | - | 0.497 [-,-] | - | - | 0.549 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +15 | POOLED | rf | - | 0.497 [-,-] | - | - | 0.595 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | ASIA | gbt3 | - | 0.497 [-,-] | - | - | 0.500 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | POOLED | gbt3 | 0.507 [0.49,0.53] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | POOLED/ST | gbt3 | 0.519 [0.50,0.54] | 0.497 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +60 | NY | rf | - | 0.496 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +10 | POOLED | rf | - | 0.496 [-,-] | - | - | 0.597 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | ASIA | stack | 0.497 [0.47,0.53] | 0.496 [0.46,0.54] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | POOLED | logit2 | 0.497 [0.48,0.51] | 0.496 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G5 | +10 | LONDON | gbt3 | - | 0.496 [-,-] | - | - | 0.533 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | POOLED/ST | gbt3 | 0.494 [0.47,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | POOLED/HM | gbt3 | 0.500 [0.48,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | POOLED/ST | gbt3 | 0.514 [0.49,0.54] | 0.496 [0.46,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | +10 | ASIA | stack | - | 0.495 [-,-] | - | - | 0.490 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +60 | POOLED | rf | - | 0.494 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | POOLED | rf | 0.510 [0.49,0.53] | 0.494 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +60 | ASIA | logit2 | - | 0.494 [-,-] | - | - | 0.473 | N | - | - | - | - |  | locked label (reference only) |
| G2 | pre | LONDON | logit2 | - | 0.494 [-,-] | - | - | 0.583 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-GALL | sig | POOLED/ST | rf | 0.495 [0.47,0.52] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | POOLED | rf | - | 0.494 [-,-] | - | - | 0.663 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | POOLED | gbt3 | - | 0.493 [-,-] | - | - | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G2 | sig | POOLED/HM | rf | 0.508 [0.48,0.53] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | POOLED | rf | 0.501 [0.49,0.52] | 0.492 [0.47,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | POOLED | gbt3 | - | 0.492 [-,-] | - | - | 0.555 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | ASIA | stack | 0.509 [0.48,0.54] | 0.492 [0.46,0.53] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G5 | pre | LONDON | stack | - | 0.492 [-,-] | - | - | 0.510 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | NY | gbt3 | 0.508 [0.47,0.55] | 0.491 [0.43,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | POOLED | rf | 0.499 [0.48,0.52] | 0.490 [0.47,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| GALL | pre | LONDON | logit2 | - | 0.490 [-,-] | - | - | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +15 | POOLED | rf | - | 0.490 [-,-] | - | - | 0.586 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +45 | ASIA | logit2 | - | 0.490 [-,-] | - | - | 0.478 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | LONDON | gbt3 | - | 0.489 [-,-] | - | - | 0.520 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +20 | LONDON | gbt3 | - | 0.489 [-,-] | - | - | 0.531 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +45 | POOLED | gbt3 | - | 0.489 [-,-] | - | - | 0.565 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | LONDON | rf | - | 0.489 [-,-] | - | - | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +5 | ASIA | gbt3 | - | 0.487 [-,-] | - | - | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +30 | POOLED | rf | - | 0.487 [-,-] | - | - | 0.576 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | LONDON | stack | 0.493 [0.46,0.53] | 0.487 [0.44,0.53] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G4 | +10 | POOLED | rf | - | 0.487 [-,-] | - | - | 0.577 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +10 | POOLED | rf | - | 0.486 [-,-] | - | - | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G1 | sig | ASIA | logit2 | 0.504 [0.48,0.53] | 0.485 [0.45,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | pre | POOLED | rf | - | 0.485 [-,-] | - | - | 0.646 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +15 | LONDON | gbt3 | - | 0.485 [-,-] | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | ASIA | rf | - | 0.485 [-,-] | - | - | 0.482 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +30 | ASIA | rf | - | 0.485 [-,-] | - | - | 0.471 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +20 | LONDON | gbt3 | - | 0.484 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +20 | LONDON | gbt3 | - | 0.484 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +20 | LONDON | gbt3 | - | 0.484 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +5 | LONDON | stack | - | 0.484 [-,-] | - | - | 0.499 | ok | - | - | - | - |  | locked label (reference only) |
| GALL | pre | POOLED | rf | - | 0.484 [-,-] | - | - | 0.646 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +15 | ASIA | gbt3 | - | 0.484 [-,-] | - | - | 0.483 | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | POOLED | rf | - | 0.483 [-,-] | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G1 | sig | NY | gbt3 | 0.513 [0.47,0.56] | 0.483 [0.42,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +45 | ASIA | rf | - | 0.483 [-,-] | - | - | 0.473 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | NY | stack | - | 0.483 [-,-] | - | - | 0.535 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +20 | POOLED | rf | - | 0.483 [-,-] | - | - | 0.572 | N | - | - | - | - |  | locked label (reference only) |
| G7 | pre | POOLED | rf | - | 0.483 [-,-] | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G4 | sig | POOLED | gbt3 | 0.493 [0.48,0.51] | 0.483 [0.46,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +60 | ASIA | logit2 | - | 0.483 [-,-] | - | - | 0.485 | N | - | - | - | - |  | locked label (reference only) |
| G2 | pre | POOLED | rf | - | 0.482 [-,-] | - | - | 0.646 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G5 | sig | LONDON | gbt3 | 0.501 [0.47,0.54] | 0.482 [0.43,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | ASIA | rf | - | 0.482 [-,-] | - | - | 0.464 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G5 | sig | POOLED/ST | gbt3 | 0.493 [0.47,0.51] | 0.482 [0.45,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | ASIA | gbt3 | - | 0.482 [-,-] | - | - | 0.473 | N | - | - | - | - |  | locked label (reference only) |
| G5 | pre | POOLED | rf | - | 0.482 [-,-] | - | - | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | +10 | ASIA | logit2 | - | 0.481 [-,-] | - | - | 0.470 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +20 | POOLED | gbt3 | - | 0.481 [-,-] | - | - | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-BASE | sig | POOLED/ST | gbt3 | 0.486 [0.46,0.51] | 0.481 [0.45,0.51] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | ASIA | rf | - | 0.481 [-,-] | - | - | 0.478 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | LONDON | gbt3 | 0.502 [0.47,0.54] | 0.480 [0.43,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | POOLED | logit2 | - | 0.480 [-,-] | - | - | 0.558 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | ASIA | stack | 0.489 [0.46,0.51] | 0.480 [0.45,0.51] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G4 | +10 | ASIA | stack | - | 0.479 [-,-] | - | - | 0.483 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | LONDON | gbt3 | - | 0.479 [-,-] | - | - | 0.479 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +15 | NY | stack | - | 0.478 [-,-] | - | - | 0.527 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +60 | ASIA | rf | - | 0.478 [-,-] | - | - | 0.457 | N | - | - | - | - |  | locked label (reference only) |
| G7 | pre | LONDON | gbt3 | - | 0.477 [-,-] | - | - | 0.484 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | LONDON | stack | - | 0.476 [-,-] | - | - | 0.478 | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G2 | sig | ASIA | stack | 0.490 [0.46,0.52] | 0.475 [0.43,0.51] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | POOLED | rf | - | 0.474 [-,-] | - | - | 0.572 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +20 | NY | gbt3 | - | 0.474 [-,-] | - | - | 0.556 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +45 | POOLED | rf | - | 0.474 [-,-] | - | - | 0.568 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | NY | gbt3 | 0.509 [0.48,0.54] | 0.474 [0.43,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +30 | LONDON | stack | - | 0.473 [-,-] | - | - | 0.479 | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | POOLED | rf | - | 0.473 [-,-] | - | - | 0.572 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +5 | ASIA | stack | - | 0.473 [-,-] | - | - | 0.466 | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +5 | NY | rf | - | 0.473 [-,-] | - | - | 0.589 | N | - | - | - | - |  | locked label (reference only) |
| GALL | pre | POOLED | logit2 | - | 0.473 [-,-] | - | - | 0.570 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +15 | LONDON | gbt3 | - | 0.473 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | pre | POOLED | rf | - | 0.472 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | ASIA | stack | 0.469 [0.44,0.50] | 0.472 [0.44,0.51] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| G-sig-G5 | sig | NY | gbt3 | 0.508 [0.47,0.54] | 0.472 [0.41,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +60 | LONDON | stack | - | 0.471 [-,-] | - | - | 0.467 | ok | - | - | - | - |  | locked label (reference only) |
| G1 | pre | ASIA | gbt3 | - | 0.470 [-,-] | - | - | 0.476 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +20 | POOLED | stack | - | 0.469 [-,-] | - | - | 0.564 | ok | - | - | - | - |  | locked label (reference only) |
| G4 | +5 | ASIA | rf | - | 0.469 [-,-] | - | - | 0.465 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +60 | NY | gbt3 | - | 0.469 [-,-] | - | - | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +15 | LONDON | gbt3 | - | 0.469 [-,-] | - | - | 0.503 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +20 | NY | gbt3 | - | 0.468 [-,-] | - | - | 0.570 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +5 | POOLED | rf | - | 0.468 [-,-] | - | - | 0.635 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | pre | POOLED | rf | - | 0.466 [-,-] | - | - | 0.560 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +45 | NY | gbt3 | - | 0.466 [-,-] | - | - | 0.484 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +60 | POOLED | rf | - | 0.466 [-,-] | - | - | 0.571 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +5 | POOLED | rf | - | 0.465 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | pre | POOLED | rf | - | 0.465 [-,-] | - | - | 0.551 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +5 | LONDON | gbt3 | - | 0.464 [-,-] | - | - | 0.494 | N | - | - | - | - |  | locked label (reference only) |
| G7 | pre | ASIA | gbt3 | - | 0.464 [-,-] | - | - | 0.461 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +5 | POOLED | rf | - | 0.464 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +30 | LONDON | stack | - | 0.464 [-,-] | - | - | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | LONDON | rf | - | 0.464 [-,-] | - | - | 0.509 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | POOLED/ST | logit2 | 0.472 [0.45,0.50] | 0.463 [0.43,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | +5 | POOLED | rf | - | 0.463 [-,-] | - | - | 0.634 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +20 | LONDON | gbt3 | - | 0.463 [-,-] | - | - | 0.630 | ok | - | - | - | - | stack | locked label (reference only) |
| G-sig-G2 | sig | NY | rf | 0.496 [0.46,0.54] | 0.463 [0.40,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | POOLED | rf | - | 0.463 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +5 | POOLED | rf | - | 0.462 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | POOLED | rf | - | 0.462 [-,-] | - | - | 0.576 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +15 | POOLED | gbt3 | - | 0.461 [-,-] | - | - | 0.546 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +5 | LONDON | rf | - | 0.460 [-,-] | - | - | 0.454 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | POOLED/ST | gbt3 | 0.484 [0.46,0.51] | 0.460 [0.43,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G7 | +60 | NY | gbt3 | - | 0.459 [-,-] | - | - | 0.503 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +30 | POOLED | rf | - | 0.457 [-,-] | - | - | 0.559 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +5 | POOLED | rf | - | 0.456 [-,-] | - | - | 0.563 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | LONDON | gbt3 | 0.476 [0.45,0.51] | 0.455 [0.41,0.50] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G5 | +10 | POOLED | rf | - | 0.455 [-,-] | - | - | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +10 | NY | gbt3 | - | 0.455 [-,-] | - | - | 0.537 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | POOLED | rf | - | 0.455 [-,-] | - | - | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +15 | NY | stack | - | 0.454 [-,-] | - | - | 0.593 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | POOLED | gbt3 | - | 0.454 [-,-] | - | - | 0.533 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | ASIA | rf | - | 0.453 [-,-] | - | - | 0.442 | N | - | - | - | - |  | locked label (reference only) |
| G5 | pre | POOLED | rf | - | 0.453 [-,-] | - | - | 0.551 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +20 | NY | gbt3 | - | 0.452 [-,-] | - | - | 0.567 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +5 | ASIA | rf | - | 0.451 [-,-] | - | - | 0.453 | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | ASIA | stack | - | 0.450 [-,-] | - | - | 0.442 | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +45 | NY | stack | - | 0.450 [-,-] | - | - | 0.545 | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +5 | POOLED | rf | - | 0.450 [-,-] | - | - | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +15 | ASIA | stack | - | 0.449 [-,-] | - | - | 0.446 | ok | - | - | - | - |  | locked label (reference only) |
| G2 | +5 | LONDON | logit2 | - | 0.448 [-,-] | - | - | 0.539 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | +5 | LONDON | logit2 | - | 0.448 [-,-] | - | - | 0.539 | ok | - | - | - | - | stack | locked label (reference only) |
| G1 | +10 | NY | gbt3 | - | 0.448 [-,-] | - | - | 0.730 | ok | - | - | - | - | stack | locked label (reference only) |
| GALL | pre | NY | gbt3 | - | 0.448 [-,-] | - | - | 0.516 | N | - | - | - | - |  | locked label (reference only) |
| GALL | pre | ASIA | rf | - | 0.446 [-,-] | - | - | 0.452 | N | - | - | - | - |  | locked label (reference only) |
| G-sig-G4 | sig | LONDON | logit2 | 0.478 [0.45,0.51] | 0.446 [0.40,0.49] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | LONDON | stack | - | 0.445 [-,-] | - | - | 0.467 | ok | - | - | - | - |  | locked label (reference only) |
| G1 | +5 | ASIA | gbt3 | - | 0.444 [-,-] | - | - | 0.446 | N | - | - | - | - |  | locked label (reference only) |
| G4 | pre | NY | rf | - | 0.443 [-,-] | - | - | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +5 | POOLED | rf | - | 0.443 [-,-] | - | - | 0.563 | N | - | - | - | - |  | locked label (reference only) |
| G2 | pre | NY | rf | - | 0.442 [-,-] | - | - | 0.689 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | NY | rf | - | 0.442 [-,-] | - | - | 0.478 | N | - | - | - | - |  | locked label (reference only) |
| GALL | pre | NY | rf | - | 0.442 [-,-] | - | - | 0.693 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +60 | ASIA | gbt3 | - | 0.441 [-,-] | - | - | 0.434 | N | - | - | - | - |  | locked label (reference only) |
| GALL | +5 | NY | logit2 | - | 0.438 [-,-] | - | - | 0.520 | N | - | - | - | - |  | locked label (reference only) |
| G2 | pre | LONDON | stack | - | 0.438 [-,-] | - | - | 0.444 | ok | - | - | - | - |  | locked label (reference only) |
| G7 | +15 | LONDON | gbt3 | - | 0.438 [-,-] | - | - | 0.454 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +10 | NY | gbt3 | - | 0.437 [-,-] | - | - | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +15 | NY | gbt3 | - | 0.437 [-,-] | - | - | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| G1 | +5 | LONDON | logit2 | - | 0.436 [-,-] | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +5 | LONDON | logit2 | - | 0.436 [-,-] | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +5 | POOLED | rf | - | 0.436 [-,-] | - | - | 0.546 | N | - | - | - | - |  | locked label (reference only) |
| G1 | pre | NY | rf | - | 0.436 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | pre | NY | rf | - | 0.436 [-,-] | - | - | 0.687 | ok | - | - | - | - | stack | locked label (reference only) |
| G7 | pre | NY | rf | - | 0.434 [-,-] | - | - | 0.689 | ok | - | - | - | - | stack | locked label (reference only) |
| G5 | +5 | LONDON | rf | - | 0.434 [-,-] | - | - | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +5 | POOLED | gbt3 | - | 0.434 [-,-] | - | - | 0.536 | N | - | - | - | - |  | locked label (reference only) |
| G7 | +5 | LONDON | rf | - | 0.434 [-,-] | - | - | 0.582 | ok | - | - | - | - | stack | locked label (reference only) |
| G2 | +20 | NY | stack | - | 0.429 [-,-] | - | - | 0.519 | ok | - | - | - | - |  | locked label (reference only) |
| GALL | +20 | LONDON | gbt3 | - | 0.428 [-,-] | - | - | 0.610 | ok | - | - | - | - | stack | locked label (reference only) |
| G4 | +45 | NY | rf | - | 0.426 [-,-] | - | - | 0.459 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +10 | NY | stack | - | 0.424 [-,-] | - | - | 0.486 | ok | - | - | - | - |  | locked label (reference only) |
| G4 | pre | POOLED | rf | - | 0.423 [-,-] | - | - | 0.543 | N | - | - | - | - |  | locked label (reference only) |
| G5 | +45 | NY | gbt3 | - | 0.419 [-,-] | - | - | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| G2 | +60 | NY | rf | - | 0.411 [-,-] | - | - | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| G4 | +45 | LONDON | stack | - | 0.410 [-,-] | - | - | 0.433 | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- G1 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G1 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G2 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G4 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G5 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G7 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 0 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 5 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 10 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 15 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 20 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 30 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 45 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 POOLED: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 ASIA: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 LONDON: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- GALL 60 NY: no econ grid (WF-PRE AUC below baseline+0.02); cond-entry AUC reported per SCHEMA s8
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 NY: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G1 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G2 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G4 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G5 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 NY: no gate econ (AUC far below 0.68)
- G-sig-G7 -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 NY: no gate econ (AUC far below 0.68)
- G-sig-GALL -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 ASIA: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 LONDON: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 NY: no gate econ (AUC far below 0.68)
- G-sig-GALL+BASE -1 POOLED: no gate econ (AUC far below 0.68)
