# PRED ROUND 0 - block A round 1 - A1A2A3

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.608 [0.55,0.67]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg cc667270ab8698902309fcd43db21248411058de40297d8c937156f9f152775c ; trials added 1100 ; truncation audit {'decisions': 90000, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A1A2A3_dense.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A1A2A3-G | sig | NY/ST | baseline:M0_y | 0.608 [0.57,0.65] | 0.608 [0.55,0.67] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | LONDON/ST | best:M4_y | 0.603 [0.56,0.64] | 0.607 [0.55,0.67] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | NY/ST | best:M4_y | 0.617 [0.58,0.66] | 0.603 [0.55,0.66] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | LONDON/ST | baseline:M0_y | 0.586 [0.55,0.63] | 0.600 [0.54,0.66] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | NY | baseline:M0_y | 0.609 [0.57,0.65] | 0.600 [0.55,0.65] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | NY | best:M4_y | 0.612 [0.57,0.65] | 0.599 [0.55,0.65] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | NY/HM | best:M0_y | 0.611 [0.56,0.67] | 0.593 [0.52,0.68] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | LONDON | best:M4_y | 0.580 [0.55,0.61] | 0.586 [0.54,0.63] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | LONDON | baseline:M0_y | 0.573 [0.54,0.60] | 0.582 [0.54,0.63] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | ASIA | best:M3_y | 0.550 [0.52,0.58] | 0.576 [0.54,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | POOLED/HM | best:M4_y | 0.564 [0.54,0.59] | 0.575 [0.54,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | POOLED | best:M4_y | 0.567 [0.55,0.59] | 0.573 [0.54,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | POOLED/ST | best:M4_y | 0.570 [0.55,0.59] | 0.573 [0.54,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | ASIA/HM | best:M4_y | 0.553 [0.51,0.59] | 0.571 [0.51,0.63] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-G | sig | LONDON/HM | baseline:M0_y | 0.558 [0.52,0.60] | 0.566 [0.51,0.62] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | POOLED/ST | baseline:M0_y | 0.551 [0.53,0.57] | 0.559 [0.53,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | POOLED | baseline:M0_y | 0.552 [0.53,0.57] | 0.556 [0.53,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | POOLED/HM | baseline:M0_y | 0.552 [0.53,0.58] | 0.555 [0.52,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | ASIA/ST | best:M3_y | 0.532 [0.50,0.57] | 0.549 [0.51,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | ASIA/HM | baseline:M0_y | 0.523 [0.49,0.56] | 0.537 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | LONDON/HM | best:RAW_a1_fp(neg) | 0.542 [0.50,0.59] | 0.526 [0.46,0.59] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | ASIA | baseline:M0_y | 0.509 [0.48,0.54] | 0.525 [0.49,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-G | sig | ASIA/ST | baseline:M0_y | 0.496 [0.47,0.53] | 0.516 [0.47,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| A1A2A3-FR | pre | POOLED | rf | - | - | - | - | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | POOLED | stack | - | - | - | - | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | ASIA | rf | - | - | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | ASIA | stack | - | - | - | - | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | LONDON | gbt3 | - | - | - | - | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | LONDON | stack | - | - | - | - | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | NY | rf | - | - | - | - | 0.708 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | pre | NY | stack | - | - | - | - | 0.695 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | POOLED | rf | - | - | - | - | 0.649 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | POOLED | stack | - | - | - | - | 0.642 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | ASIA | gbt3 | - | - | - | - | 0.535 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | ASIA | stack | - | - | - | - | 0.536 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | LONDON | logit2 | - | - | - | - | 0.583 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | LONDON | stack | - | - | - | - | 0.617 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | NY | rf | - | - | - | - | 0.709 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +5 | NY | stack | - | - | - | - | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | POOLED | rf | - | - | - | - | 0.649 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | POOLED | stack | - | - | - | - | 0.650 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | ASIA | rf | - | - | - | - | 0.498 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | ASIA | stack | - | - | - | - | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | LONDON | gbt3 | - | - | - | - | 0.622 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | LONDON | stack | - | - | - | - | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | NY | rf | - | - | - | - | 0.706 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +10 | NY | stack | - | - | - | - | 0.712 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | POOLED | rf | - | - | - | - | 0.670 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | POOLED | stack | - | - | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | ASIA | rf | - | - | - | - | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | ASIA | stack | - | - | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | LONDON | rf | - | - | - | - | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | LONDON | stack | - | - | - | - | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | NY | stack | - | - | - | - | 0.763 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +15 | NY | stack | - | - | - | - | 0.763 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | POOLED | rf | - | - | - | - | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | POOLED | stack | - | - | - | - | 0.679 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | ASIA | rf | - | - | - | - | 0.482 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | ASIA | stack | - | - | - | - | 0.506 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | LONDON | gbt3 | - | - | - | - | 0.638 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | LONDON | stack | - | - | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | NY | stack | - | - | - | - | 0.815 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +20 | NY | stack | - | - | - | - | 0.815 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | POOLED | rf | - | - | - | - | 0.691 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | POOLED | stack | - | - | - | - | 0.693 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | ASIA | stack | - | - | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | ASIA | stack | - | - | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | LONDON | rf | - | - | - | - | 0.696 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | LONDON | stack | - | - | - | - | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | NY | rf | - | - | - | - | 0.786 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +30 | NY | stack | - | - | - | - | 0.790 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | POOLED | rf | - | - | - | - | 0.683 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | POOLED | stack | - | - | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | ASIA | logit2 | - | - | - | - | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | ASIA | stack | - | - | - | - | 0.574 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | LONDON | rf | - | - | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | LONDON | stack | - | - | - | - | 0.658 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | NY | gbt3 | - | - | - | - | 0.745 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +45 | NY | stack | - | - | - | - | 0.730 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | POOLED | rf | - | - | - | - | 0.713 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | POOLED | stack | - | - | - | - | 0.717 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | ASIA | stack | - | - | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | ASIA | stack | - | - | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | LONDON | rf | - | - | - | - | 0.684 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | LONDON | stack | - | - | - | - | 0.650 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | NY | gbt3 | - | - | - | - | 0.880 | ok | - | - | - | - | stack | locked label (reference only) |
| A1A2A3-FR | +60 | NY | stack | - | - | - | - | 0.871 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- A1A2A3-G -1 POOLED: best-by-WF-PRE G model for scope
- A1A2A3-G -1 POOLED: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 POOLED: best-by-WF-PRE G model for scope
- A1A2A3-G -1 POOLED: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 POOLED: best-by-WF-PRE G model for scope
- A1A2A3-G -1 POOLED: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 ASIA: best-by-WF-PRE G model for scope
- A1A2A3-G -1 ASIA: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 ASIA: best-by-WF-PRE G model for scope
- A1A2A3-G -1 ASIA: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 ASIA: best-by-WF-PRE G model for scope
- A1A2A3-G -1 ASIA: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 LONDON: best-by-WF-PRE G model for scope
- A1A2A3-G -1 LONDON: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 LONDON: best-by-WF-PRE G model for scope
- A1A2A3-G -1 LONDON: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 LONDON: best-by-WF-PRE G model for scope
- A1A2A3-G -1 LONDON: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 NY: best-by-WF-PRE G model for scope
- A1A2A3-G -1 NY: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 NY: best-by-WF-PRE G model for scope
- A1A2A3-G -1 NY: FAILPRED-feature meta-label baseline for G
- A1A2A3-G -1 NY: best-by-WF-PRE G model for scope
- A1A2A3-FR 0 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 0 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 5 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 10 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 15 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 20 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 30 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 45 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 POOLED: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 ASIA: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 LONDON: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
- A1A2A3-FR 60 NY: FAILPRED stack + A dense scores; WF-PRE gain <0.02 vs R0_lite
