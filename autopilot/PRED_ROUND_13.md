# PRED ROUND 13 - block I round 2 - I4-autoencoder

Best HOLDOUT F-R AUC: +15 POOLED 0.524 [-,-] | ASIA 0.521 [-,-] | LONDON 0.542 [-,-] | NY 0.524 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.510 [-,-] | ASIA 0.526 [-,-] | LONDON 0.512 [-,-] | NY 0.514 [-,-]
Best G HOLDOUT AUC: 0.607 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg aefdd1cbf5710621d522fab3569143d632ca2c9e5d5ea0b4ce99933584c379c5 ; trials added 231 ; truncation audit {'decisions': 240, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I4-autoencoder | sig | LONDON | logit2/pooled | 0.627 [0.59,0.66] | 0.607 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | NY | logit2/pooled | 0.607 [0.58,0.64] | 0.603 [0.56,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +60 | NY | gbt3/pooled | - | 0.602 [-,-] | - | - | 0.877 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +45 | NY | gbt3/pooled | - | 0.600 [-,-] | - | - | 0.788 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED/ST | logit2/pooled | 0.584 [0.56,0.61] | 0.593 [0.56,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED | logit2/pooled | 0.580 [0.56,0.59] | 0.582 [0.56,0.61] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED/HM | logit2/pooled | 0.576 [0.55,0.59] | 0.573 [0.55,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +45 | ASIA | logit2/pooled | - | 0.566 [-,-] | - | - | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | ASIA | stack/pooled | 0.545 [0.51,0.58] | 0.563 [0.53,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +20 | NY | stack/pooled | - | 0.563 [-,-] | - | - | 0.823 | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +10 | NY | rf/pooled | - | 0.559 [-,-] | - | - | 0.758 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +20 | LONDON | logit2/pooled | - | 0.549 [-,-] | - | - | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +20 | ASIA | gbt3/pooled | - | 0.545 [-,-] | - | - | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +15 | LONDON | rf/pooled | - | 0.542 [-,-] | - | - | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +60 | ASIA | stack/pooled | - | 0.541 [-,-] | - | - | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +45 | POOLED | gbt3/pooled | - | 0.539 [-,-] | - | - | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED/ST | logit2/pooled | 0.534 [0.51,0.56] | 0.538 [0.51,0.58] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | pre | ASIA | gbt3/pooled | - | 0.533 [-,-] | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +5 | ASIA | rf/pooled | - | 0.531 [-,-] | - | - | 0.524 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +45 | LONDON | gbt3/pooled | - | 0.530 [-,-] | - | - | 0.629 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | LONDON | logit2/pooled | 0.559 [0.52,0.60] | 0.530 [0.47,0.59] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | ASIA | stack/pooled | 0.517 [0.49,0.55] | 0.528 [0.49,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED | logit2/pooled | 0.528 [0.51,0.54] | 0.527 [0.50,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +30 | ASIA | stack/pooled | - | 0.526 [-,-] | - | - | 0.512 | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +10 | LONDON | gbt3/pooled | - | 0.525 [-,-] | - | - | 0.637 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +15 | POOLED | rf/pooled | - | 0.524 [-,-] | - | - | 0.674 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +15 | NY | stack/pooled | - | 0.524 [-,-] | - | - | 0.761 | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | NY | logit2/pooled | 0.544 [0.51,0.58] | 0.522 [0.47,0.57] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +20 | POOLED | rf/pooled | - | 0.522 [-,-] | - | - | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +15 | ASIA | rf/pooled | - | 0.521 [-,-] | - | - | 0.511 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +5 | NY | rf/pooled | - | 0.520 [-,-] | - | - | 0.705 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | sig | POOLED/HM | logit2/pooled | 0.523 [0.50,0.54] | 0.518 [0.49,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +60 | POOLED | gbt3/pooled | - | 0.516 [-,-] | - | - | 0.702 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | pre | LONDON | gbt3/pooled | - | 0.516 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +30 | NY | gbt3/pooled | - | 0.514 [-,-] | - | - | 0.780 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +30 | LONDON | logit2/pooled | - | 0.512 [-,-] | - | - | 0.571 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +30 | POOLED | rf/pooled | - | 0.510 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +10 | POOLED | gbt3/pooled | - | 0.501 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +10 | ASIA | stack/pooled | - | 0.492 [-,-] | - | - | 0.479 | - | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | pre | POOLED | rf/pooled | - | 0.479 [-,-] | - | - | 0.640 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +5 | POOLED | rf/pooled | - | 0.474 [-,-] | - | - | 0.642 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | pre | NY | rf/pooled | - | 0.446 [-,-] | - | - | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +60 | LONDON | gbt3/pooled | - | 0.439 [-,-] | - | - | 0.627 | ok | - | - | - | - | stack | locked label (reference only) |
| I4-autoencoder | +5 | LONDON | logit2/pooled | - | 0.435 [-,-] | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I4-autoencoder 0 POOLED: I4-autoencoder: same-cell BASE hold 0.646; delta -0.005
- I4-autoencoder 0 ASIA: I4-autoencoder: same-cell BASE hold 0.532; delta +0.001
- I4-autoencoder 0 LONDON: I4-autoencoder: same-cell BASE hold 0.651; delta +0.001
- I4-autoencoder 0 NY: I4-autoencoder: same-cell BASE hold 0.680; delta +0.008
- I4-autoencoder 5 POOLED: I4-autoencoder: same-cell BASE hold 0.634; delta +0.008
- I4-autoencoder 5 ASIA: I4-autoencoder: same-cell BASE hold 0.532; delta -0.007
- I4-autoencoder 5 LONDON: I4-autoencoder: same-cell BASE hold 0.583; delta -0.034
- I4-autoencoder 5 NY: I4-autoencoder: same-cell BASE hold 0.716; delta -0.011
- I4-autoencoder 10 POOLED: I4-autoencoder: same-cell BASE hold 0.672; delta -0.020
- I4-autoencoder 10 ASIA: I4-autoencoder: same-cell BASE hold 0.521; delta -0.042
- I4-autoencoder 10 LONDON: I4-autoencoder: same-cell BASE hold 0.587; delta +0.050
- I4-autoencoder 10 NY: I4-autoencoder: same-cell BASE hold 0.765; delta -0.007
- I4-autoencoder 15 POOLED: I4-autoencoder: same-cell BASE hold 0.695; delta -0.022
- I4-autoencoder 15 ASIA: I4-autoencoder: same-cell BASE hold 0.543; delta -0.032
- I4-autoencoder 15 LONDON: I4-autoencoder: same-cell BASE hold 0.658; delta -0.005
- I4-autoencoder 15 NY: I4-autoencoder: same-cell BASE hold 0.802; delta -0.041
- I4-autoencoder 20 POOLED: I4-autoencoder: same-cell BASE hold 0.681; delta -0.001
- I4-autoencoder 20 ASIA: I4-autoencoder: same-cell BASE hold 0.506; delta +0.025
- I4-autoencoder 20 LONDON: I4-autoencoder: same-cell BASE hold 0.647; delta -0.029
- I4-autoencoder 20 NY: I4-autoencoder: same-cell BASE hold 0.832; delta -0.009
- I4-autoencoder 30 POOLED: I4-autoencoder: same-cell BASE hold 0.686; delta -0.021
- I4-autoencoder 30 ASIA: I4-autoencoder: same-cell BASE hold 0.514; delta -0.002
- I4-autoencoder 30 LONDON: I4-autoencoder: same-cell BASE hold 0.652; delta -0.081
- I4-autoencoder 30 NY: I4-autoencoder: same-cell BASE hold 0.804; delta -0.024
- I4-autoencoder 45 POOLED: I4-autoencoder: same-cell BASE hold 0.667; delta +0.014
- I4-autoencoder 45 ASIA: I4-autoencoder: same-cell BASE hold 0.499; delta +0.059
- I4-autoencoder 45 LONDON: I4-autoencoder: same-cell BASE hold 0.627; delta +0.002
- I4-autoencoder 45 NY: I4-autoencoder: same-cell BASE hold 0.795; delta -0.007
- I4-autoencoder 60 POOLED: I4-autoencoder: same-cell BASE hold 0.705; delta -0.003
- I4-autoencoder 60 ASIA: I4-autoencoder: same-cell BASE hold 0.527; delta +0.011
- I4-autoencoder 60 LONDON: I4-autoencoder: same-cell BASE hold 0.663; delta -0.035
- I4-autoencoder 60 NY: I4-autoencoder: same-cell BASE hold 0.878; delta -0.001
- I4-autoencoder -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta +0.000
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta +0.001
- I4-autoencoder -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 POOLED: G HM: same-cell GBASE hold 0.579; delta -0.006
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta +0.000
- I4-autoencoder -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 NY: G NY: same-cell GBASE hold 0.603; delta +0.000
- I4-autoencoder -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I4-autoencoder -1 POOLED: G ST: same-cell GBASE hold 0.587; delta +0.006
- I4-autoencoder -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
