# PRED ROUND 6 - block I round 4 - I2-gp

Best HOLDOUT F-R AUC: +15 POOLED 0.533 [-,-] | ASIA 0.555 [-,-] | LONDON 0.490 [-,-] | NY 0.546 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.525 [-,-] | ASIA 0.559 [-,-] | LONDON 0.505 [-,-] | NY 0.507 [-,-]
Best G HOLDOUT AUC: 0.606 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg a0e82b83bd84cdbd2a62db2cf5487f2349fd297e04bb5ff59ede3cfc32c134b1 ; trials added 1425636 ; truncation audit {'decisions': 480, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I2-gp | sig | NY | logit2/pooled | 0.607 [0.57,0.64] | 0.606 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | LONDON | logit2/pooled | 0.626 [0.59,0.66] | 0.605 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +60 | NY | gbt3/pooled | - | 0.600 [-,-] | - | - | 0.867 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED/ST | logit2/pooled | 0.590 [0.57,0.61] | 0.590 [0.56,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED | logit2/pooled | 0.583 [0.57,0.60] | 0.583 [0.56,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +10 | LONDON | logit2/pooled | - | 0.579 [-,-] | - | - | 0.609 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED/HM | logit2/pooled | 0.577 [0.56,0.60] | 0.577 [0.55,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | ASIA | stack/pooled | 0.556 [0.53,0.59] | 0.572 [0.54,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +30 | ASIA | gbt3/pooled | - | 0.559 [-,-] | - | - | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +15 | ASIA | rf/pooled | - | 0.555 [-,-] | - | - | 0.564 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +10 | NY | rf/pooled | - | 0.552 [-,-] | - | - | 0.745 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +20 | NY | gbt3/pooled | - | 0.550 [-,-] | - | - | 0.832 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +20 | LONDON | logit2/pooled | - | 0.546 [-,-] | - | - | 0.617 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +15 | NY | stack/pooled | - | 0.546 [-,-] | - | - | 0.802 | - | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | ASIA | stack/pooled | 0.528 [0.50,0.56] | 0.537 [0.50,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +45 | NY | gbt3/pooled | - | 0.537 [-,-] | - | - | 0.794 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED/ST | logit2/pooled | 0.542 [0.52,0.57] | 0.536 [0.50,0.57] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +15 | POOLED | rf/pooled | - | 0.533 [-,-] | - | - | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | NY | logit2/pooled | 0.547 [0.51,0.58] | 0.532 [0.48,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | pre | ASIA | rf/pooled | - | 0.532 [-,-] | - | - | 0.529 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED | logit2/pooled | 0.535 [0.52,0.55] | 0.530 [0.50,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | LONDON | logit2/pooled | 0.560 [0.52,0.60] | 0.528 [0.47,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +60 | POOLED | gbt3/pooled | - | 0.527 [-,-] | - | - | 0.704 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | sig | POOLED/HM | logit2/pooled | 0.529 [0.51,0.55] | 0.526 [0.50,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +30 | POOLED | gbt3/pooled | - | 0.525 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +10 | ASIA | rf/pooled | - | 0.524 [-,-] | - | - | 0.516 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +60 | ASIA | gbt3/pooled | - | 0.523 [-,-] | - | - | 0.511 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | pre | LONDON | stack/pooled | - | 0.522 [-,-] | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +20 | POOLED | rf/pooled | - | 0.522 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +5 | ASIA | gbt3/pooled | - | 0.522 [-,-] | - | - | 0.520 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +10 | POOLED | rf/pooled | - | 0.520 [-,-] | - | - | 0.664 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +45 | ASIA | gbt3/pooled | - | 0.520 [-,-] | - | - | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +60 | LONDON | rf/pooled | - | 0.519 [-,-] | - | - | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +5 | NY | rf/pooled | - | 0.516 [-,-] | - | - | 0.710 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +45 | POOLED | gbt3/pooled | - | 0.511 [-,-] | - | - | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +20 | ASIA | rf/pooled | - | 0.510 [-,-] | - | - | 0.489 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +30 | NY | gbt3/pooled | - | 0.507 [-,-] | - | - | 0.785 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +30 | LONDON | gbt3/pooled | - | 0.505 [-,-] | - | - | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +15 | LONDON | stack/pooled | - | 0.490 [-,-] | - | - | 0.648 | - | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +45 | LONDON | gbt3/pooled | - | 0.478 [-,-] | - | - | 0.614 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +5 | POOLED | rf/pooled | - | 0.476 [-,-] | - | - | 0.639 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | pre | POOLED | rf/pooled | - | 0.474 [-,-] | - | - | 0.637 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | +5 | LONDON | logit2/pooled | - | 0.455 [-,-] | - | - | 0.563 | ok | - | - | - | - | stack | locked label (reference only) |
| I2-gp | pre | NY | rf/pooled | - | 0.408 [-,-] | - | - | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I2-gp 0 POOLED: I2-gp: same-cell BASE hold 0.646; delta -0.009
- I2-gp 0 ASIA: I2-gp: same-cell BASE hold 0.532; delta -0.003
- I2-gp 0 LONDON: I2-gp: same-cell BASE hold 0.651; delta -0.002
- I2-gp 0 NY: I2-gp: same-cell BASE hold 0.680; delta -0.011
- I2-gp 5 POOLED: I2-gp: same-cell BASE hold 0.634; delta +0.005
- I2-gp 5 ASIA: I2-gp: same-cell BASE hold 0.532; delta -0.011
- I2-gp 5 LONDON: I2-gp: same-cell BASE hold 0.583; delta -0.020
- I2-gp 5 NY: I2-gp: same-cell BASE hold 0.716; delta -0.006
- I2-gp 10 POOLED: I2-gp: same-cell BASE hold 0.672; delta -0.007
- I2-gp 10 ASIA: I2-gp: same-cell BASE hold 0.521; delta -0.005
- I2-gp 10 LONDON: I2-gp: same-cell BASE hold 0.587; delta +0.022
- I2-gp 10 NY: I2-gp: same-cell BASE hold 0.765; delta -0.020
- I2-gp 15 POOLED: I2-gp: same-cell BASE hold 0.695; delta +0.001
- I2-gp 15 ASIA: I2-gp: same-cell BASE hold 0.543; delta +0.021
- I2-gp 15 LONDON: I2-gp: same-cell BASE hold 0.658; delta -0.010
- I2-gp 15 NY: I2-gp: same-cell BASE hold 0.802; delta +0.000
- I2-gp 20 POOLED: I2-gp: same-cell BASE hold 0.681; delta -0.001
- I2-gp 20 ASIA: I2-gp: same-cell BASE hold 0.506; delta -0.017
- I2-gp 20 LONDON: I2-gp: same-cell BASE hold 0.647; delta -0.030
- I2-gp 20 NY: I2-gp: same-cell BASE hold 0.832; delta -0.000
- I2-gp 30 POOLED: I2-gp: same-cell BASE hold 0.686; delta -0.010
- I2-gp 30 ASIA: I2-gp: same-cell BASE hold 0.514; delta +0.023
- I2-gp 30 LONDON: I2-gp: same-cell BASE hold 0.652; delta -0.008
- I2-gp 30 NY: I2-gp: same-cell BASE hold 0.804; delta -0.019
- I2-gp 45 POOLED: I2-gp: same-cell BASE hold 0.667; delta +0.003
- I2-gp 45 ASIA: I2-gp: same-cell BASE hold 0.499; delta +0.008
- I2-gp 45 LONDON: I2-gp: same-cell BASE hold 0.627; delta -0.013
- I2-gp 45 NY: I2-gp: same-cell BASE hold 0.795; delta -0.001
- I2-gp 60 POOLED: I2-gp: same-cell BASE hold 0.705; delta -0.002
- I2-gp 60 ASIA: I2-gp: same-cell BASE hold 0.527; delta -0.017
- I2-gp 60 LONDON: I2-gp: same-cell BASE hold 0.663; delta -0.006
- I2-gp 60 NY: I2-gp: same-cell BASE hold 0.878; delta -0.011
- I2-gp -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta +0.000
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta +0.010
- I2-gp -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 POOLED: G HM: same-cell GBASE hold 0.579; delta -0.002
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta -0.002
- I2-gp -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 NY: G NY: same-cell GBASE hold 0.603; delta +0.003
- I2-gp -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I2-gp -1 POOLED: G ST: same-cell GBASE hold 0.587; delta +0.002
- I2-gp -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
