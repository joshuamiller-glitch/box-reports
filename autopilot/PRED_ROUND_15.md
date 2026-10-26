# PRED ROUND 15 - block C round 2 - C2-vol (vol surface + put/call + max-pain, on-disk)

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 4ea2411d1d6d549c225d15673a29d34b34659c8c5826bb6554eabda084451631 ; trials added 2600 ; truncation audit {'decisions': 360, 'checks': 80811, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'C1/C2 session features, 4 seeds x 90 decisions, bars>=cut randomised and option file column groups with last record >= cut-300s shuffled'} ; holdout scored True ; feature store ['l2vast/pred/store/C2_vol.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C2-vol-only | pre | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.571 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | pre | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.517 | - | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| C2-vol-only | pre | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.492 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | pre | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.570 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +10 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.562 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +10 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.497 | - | -1809 | -44211 | - | 1/5 |  | locked label (reference only) |
| C2-vol-only | +10 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.482 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +10 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.565 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +15 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.582 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +15 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.515 | - | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| C2-vol-only | +15 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.510 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +15 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.583 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +20 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +20 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.459 | - | -305 | -5161 | - | 1/5 |  | locked label (reference only) |
| C2-vol-only | +20 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.505 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +20 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +30 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.572 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +30 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.472 | - | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| C2-vol-only | +30 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.507 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +30 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.544 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +45 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.594 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +45 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.507 | - | 1894 | 0 | - | 1/5 |  | locked label (reference only) |
| C2-vol-only | +45 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.476 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +45 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.579 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +5 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.576 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +5 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.513 | - | 615 | 0 | - | 1/5 |  | locked label (reference only) |
| C2-vol-only | +5 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +5 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.572 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +60 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.585 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +60 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.491 | - | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| C2-vol-only | +60 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.462 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol-only | +60 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.574 | - | - | - | - | - |  | locked label (reference only) |
| C2-vol+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.651 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.509 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.669 | - | 6948 | 41053 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | pre | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.685 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.667 | - | 855 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.527 | - | 895 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.660 | - | 8415 | -90073 | 0.99 | 5/5 | stack | locked label (reference only) |
| C2-vol+base | +10 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.751 | - | -837 | 79208 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.701 | - | 312 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.549 | - | 313 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.670 | - | 8404 | -58257 | 0.99 | 4/5 | stack | locked label (reference only) |
| C2-vol+base | +15 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.806 | - | 11 | 58690 | - | 2/5 | stack | locked label (reference only) |
| C2-vol+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.683 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.490 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.662 | - | 2389 | 224302 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +20 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.827 | - | 689 | -785 | - | 2/5 | stack | locked label (reference only) |
| C2-vol+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.683 | - | 6147 | 46363 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.517 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.668 | - | 5125 | -47764 | - | 2/5 | stack | locked label (reference only) |
| C2-vol+base | +30 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.791 | - | 155 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.679 | - | 147 | 117647 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.538 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.635 | - | 3757 | -53622 | - | 2/5 | stack | locked label (reference only) |
| C2-vol+base | +45 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.783 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.635 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.531 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.603 | - | 8448 | 46362 | - | 2/5 | stack | locked label (reference only) |
| C2-vol+base | +5 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.701 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.703 | - | 143 | 0 | - | 1/5 | stack | locked label (reference only) |
| C2-vol+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.527 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.636 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C2-vol+base | +60 | NY | lite-stack (logit2,gbt3,rf) | - | - | - | - | 0.874 | - | 329 | 0 | - | 1/5 | stack | locked label (reference only) |

One-sentence notes:
- C2-vol-only 0 POOLED: C_round2_V1 ALL: WF 0.562 hold 0.571 vs baseline 0.626/0.648
- C2-vol-only 0 ASIA: C_round2_V1 ASIA: WF 0.543 hold 0.517 vs baseline 0.567/0.529; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol-only 0 LONDON: C_round2_V1 LONDON: WF 0.522 hold 0.492 vs baseline 0.602/0.658
- C2-vol-only 0 NY: C_round2_V1 NY: WF 0.544 hold 0.570 vs baseline 0.638/0.669
- C2-vol-only 10 POOLED: C_round2_V1 ALL: WF 0.555 hold 0.562 vs baseline 0.650/0.682
- C2-vol-only 10 ASIA: C_round2_V1 ASIA: WF 0.527 hold 0.497 vs baseline 0.569/0.525; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol-only 10 LONDON: C_round2_V1 LONDON: WF 0.508 hold 0.482 vs baseline 0.624/0.682
- C2-vol-only 10 NY: C_round2_V1 NY: WF 0.554 hold 0.565 vs baseline 0.697/0.773
- C2-vol-only 15 POOLED: C_round2_V1 ALL: WF 0.562 hold 0.582 vs baseline 0.665/0.703
- C2-vol-only 15 ASIA: C_round2_V1 ASIA: WF 0.533 hold 0.515 vs baseline 0.576/0.570; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol-only 15 LONDON: C_round2_V1 LONDON: WF 0.505 hold 0.510 vs baseline 0.629/0.668
- C2-vol-only 15 NY: C_round2_V1 NY: WF 0.573 hold 0.583 vs baseline 0.726/0.802
- C2-vol-only 20 POOLED: C_round2_V1 ALL: WF 0.562 hold 0.581 vs baseline 0.628/0.686
- C2-vol-only 20 ASIA: C_round2_V1 ASIA: WF 0.520 hold 0.459 vs baseline 0.498/0.503; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol-only 20 LONDON: C_round2_V1 LONDON: WF 0.521 hold 0.505 vs baseline 0.592/0.663
- C2-vol-only 20 NY: C_round2_V1 NY: WF 0.565 hold 0.578 vs baseline 0.723/0.832
- C2-vol-only 30 POOLED: C_round2_V1 ALL: WF 0.545 hold 0.572 vs baseline 0.644/0.687
- C2-vol-only 30 ASIA: C_round2_V1 ASIA: WF 0.497 hold 0.472 vs baseline 0.524/0.514; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol-only 30 LONDON: C_round2_V1 LONDON: WF 0.521 hold 0.507 vs baseline 0.612/0.661
- C2-vol-only 30 NY: C_round2_V1 NY: WF 0.529 hold 0.544 vs baseline 0.716/0.804
- C2-vol-only 45 POOLED: C_round2_V1 ALL: WF 0.536 hold 0.594 vs baseline 0.624/0.674
- C2-vol-only 45 ASIA: C_round2_V1 ASIA: WF 0.496 hold 0.507 vs baseline 0.494/0.504; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol-only 45 LONDON: C_round2_V1 LONDON: WF 0.500 hold 0.476 vs baseline 0.603/0.642
- C2-vol-only 45 NY: C_round2_V1 NY: WF 0.528 hold 0.579 vs baseline 0.676/0.790
- C2-vol-only 5 POOLED: C_round2_V1 ALL: WF 0.561 hold 0.576 vs baseline 0.606/0.632
- C2-vol-only 5 ASIA: C_round2_V1 ASIA: WF 0.532 hold 0.513 vs baseline 0.541/0.528; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol-only 5 LONDON: C_round2_V1 LONDON: WF 0.516 hold 0.481 vs baseline 0.568/0.595
- C2-vol-only 5 NY: C_round2_V1 NY: WF 0.547 hold 0.572 vs baseline 0.633/0.692
- C2-vol-only 60 POOLED: C_round2_V1 ALL: WF 0.541 hold 0.585 vs baseline 0.652/0.707
- C2-vol-only 60 ASIA: C_round2_V1 ASIA: WF 0.499 hold 0.491 vs baseline 0.498/0.527; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol-only 60 LONDON: C_round2_V1 LONDON: WF 0.478 hold 0.462 vs baseline 0.597/0.650
- C2-vol-only 60 NY: C_round2_V1 NY: WF 0.559 hold 0.574 vs baseline 0.780/0.873
- C2-vol+base 0 POOLED: C_round2_V2 ALL: WF 0.627 hold 0.651 vs baseline 0.626/0.648; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 0 ASIA: C_round2_V2 ASIA: WF 0.557 hold 0.509 vs baseline 0.567/0.529; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 0 LONDON: C_round2_V2 LONDON: WF 0.609 hold 0.669 vs baseline 0.602/0.658; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 0 NY: C_round2_V2 NY: WF 0.642 hold 0.685 vs baseline 0.638/0.669; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 10 POOLED: C_round2_V2 ALL: WF 0.646 hold 0.667 vs baseline 0.650/0.682; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 10 ASIA: C_round2_V2 ASIA: WF 0.572 hold 0.527 vs baseline 0.569/0.525; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 10 LONDON: C_round2_V2 LONDON: WF 0.622 hold 0.660 vs baseline 0.624/0.682; econ best-theta pass 5/5 (selected pre-holdout, hard halt)
- C2-vol+base 10 NY: C_round2_V2 NY: WF 0.681 hold 0.751 vs baseline 0.697/0.773; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 15 POOLED: C_round2_V2 ALL: WF 0.662 hold 0.701 vs baseline 0.665/0.703; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 15 ASIA: C_round2_V2 ASIA: WF 0.566 hold 0.549 vs baseline 0.576/0.570; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 15 LONDON: C_round2_V2 LONDON: WF 0.630 hold 0.670 vs baseline 0.629/0.668; econ best-theta pass 4/5 (selected pre-holdout, hard halt)
- C2-vol+base 15 NY: C_round2_V2 NY: WF 0.724 hold 0.806 vs baseline 0.726/0.802; econ best-theta pass 2/5 (selected pre-holdout, hard halt)
- C2-vol+base 20 POOLED: C_round2_V2 ALL: WF 0.629 hold 0.683 vs baseline 0.628/0.686; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 20 ASIA: C_round2_V2 ASIA: WF 0.499 hold 0.490 vs baseline 0.498/0.503; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 20 LONDON: C_round2_V2 LONDON: WF 0.597 hold 0.662 vs baseline 0.592/0.663; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 20 NY: C_round2_V2 NY: WF 0.719 hold 0.827 vs baseline 0.723/0.832; econ best-theta pass 2/5 (selected pre-holdout, hard halt)
- C2-vol+base 30 POOLED: C_round2_V2 ALL: WF 0.641 hold 0.683 vs baseline 0.644/0.687; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 30 ASIA: C_round2_V2 ASIA: WF 0.525 hold 0.517 vs baseline 0.524/0.514; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 30 LONDON: C_round2_V2 LONDON: WF 0.616 hold 0.668 vs baseline 0.612/0.661; econ best-theta pass 2/5 (selected pre-holdout, hard halt)
- C2-vol+base 30 NY: C_round2_V2 NY: WF 0.702 hold 0.791 vs baseline 0.716/0.804; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 45 POOLED: C_round2_V2 ALL: WF 0.628 hold 0.679 vs baseline 0.624/0.674; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 45 ASIA: C_round2_V2 ASIA: WF 0.519 hold 0.538 vs baseline 0.494/0.504; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 45 LONDON: C_round2_V2 LONDON: WF 0.596 hold 0.635 vs baseline 0.603/0.642; econ best-theta pass 2/5 (selected pre-holdout, hard halt)
- C2-vol+base 45 NY: C_round2_V2 NY: WF 0.675 hold 0.783 vs baseline 0.676/0.790; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 5 POOLED: C_round2_V2 ALL: WF 0.606 hold 0.635 vs baseline 0.606/0.632; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 5 ASIA: C_round2_V2 ASIA: WF 0.545 hold 0.531 vs baseline 0.541/0.528; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 5 LONDON: C_round2_V2 LONDON: WF 0.568 hold 0.603 vs baseline 0.568/0.595; econ best-theta pass 2/5 (selected pre-holdout, hard halt)
- C2-vol+base 5 NY: C_round2_V2 NY: WF 0.634 hold 0.701 vs baseline 0.633/0.692; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 60 POOLED: C_round2_V2 ALL: WF 0.648 hold 0.703 vs baseline 0.652/0.707; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
- C2-vol+base 60 ASIA: C_round2_V2 ASIA: WF 0.507 hold 0.527 vs baseline 0.498/0.527; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 60 LONDON: C_round2_V2 LONDON: WF 0.590 hold 0.636 vs baseline 0.597/0.650; econ best-theta pass 0/5 (selected pre-holdout, hard halt)
- C2-vol+base 60 NY: C_round2_V2 NY: WF 0.769 hold 0.874 vs baseline 0.780/0.873; econ best-theta pass 1/5 (selected pre-holdout, hard halt)
