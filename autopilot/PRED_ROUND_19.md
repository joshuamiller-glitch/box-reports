# PRED ROUND 19 - block I round 3 - I3-interactions

Best HOLDOUT F-R AUC: +15 POOLED 0.509 [-,-] | ASIA 0.548 [-,-] | LONDON 0.522 [-,-] | NY 0.520 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.540 [-,-] | ASIA 0.574 [-,-] | LONDON 0.539 [-,-] | NY 0.498 [-,-]
Best G HOLDOUT AUC: 0.578 [0.53,0.63]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 46baa80a4f3ff265bd1f18a173714f947229e09d07a0af7ae6a13648ebc4dd8b ; trials added 1335051 ; truncation audit {'decisions': 480, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I3-interactions | +45 | LONDON | logit2/pooled | - | 0.601 [-,-] | - | - | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +60 | NY | stack/pooled | - | 0.588 [-,-] | - | - | 0.657 | - | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | LONDON | rf/pooled | 0.599 [0.57,0.63] | 0.578 [0.53,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +30 | ASIA | rf/pooled | - | 0.574 [-,-] | - | - | 0.553 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +20 | NY | logit2/pooled | - | 0.570 [-,-] | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED/HM | rf/pooled | 0.570 [0.55,0.59] | 0.567 [0.53,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | NY | gbt3/pooled | 0.580 [0.54,0.62] | 0.566 [0.51,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED | rf/pooled | 0.567 [0.55,0.59] | 0.562 [0.53,0.59] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED/ST | rf/pooled | 0.564 [0.54,0.59] | 0.559 [0.52,0.60] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +60 | LONDON | gbt3/pooled | - | 0.559 [-,-] | - | - | 0.566 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +45 | ASIA | gbt3/pooled | - | 0.556 [-,-] | - | - | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | pre | ASIA | rf/pooled | - | 0.550 [-,-] | - | - | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +15 | ASIA | rf/pooled | - | 0.548 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +5 | ASIA | stack/pooled | - | 0.548 [-,-] | - | - | 0.542 | - | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +5 | LONDON | rf/pooled | - | 0.545 [-,-] | - | - | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +20 | LONDON | stack/pooled | - | 0.542 [-,-] | - | - | 0.565 | - | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +10 | LONDON | rf/pooled | - | 0.540 [-,-] | - | - | 0.579 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +30 | POOLED | rf/pooled | - | 0.540 [-,-] | - | - | 0.643 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +30 | LONDON | gbt3/pooled | - | 0.539 [-,-] | - | - | 0.540 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | pre | LONDON | gbt3/pooled | - | 0.528 [-,-] | - | - | 0.594 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +45 | NY | gbt3/pooled | - | 0.528 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +60 | POOLED | rf/pooled | - | 0.525 [-,-] | - | - | 0.637 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +15 | LONDON | gbt3/pooled | - | 0.522 [-,-] | - | - | 0.549 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +15 | NY | stack/pooled | - | 0.520 [-,-] | - | - | 0.642 | - | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +20 | ASIA | rf/pooled | - | 0.520 [-,-] | - | - | 0.505 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED/HM | rf/pooled | 0.527 [0.50,0.55] | 0.519 [0.49,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +45 | POOLED | logit2/pooled | - | 0.515 [-,-] | - | - | 0.636 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | ASIA | gbt3/pooled | 0.524 [0.50,0.55] | 0.513 [0.47,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED | rf/pooled | 0.522 [0.50,0.55] | 0.512 [0.48,0.54] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +10 | ASIA | rf/pooled | - | 0.510 [-,-] | - | - | 0.497 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +15 | POOLED | stack/pooled | - | 0.509 [-,-] | - | - | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +60 | ASIA | gbt3/pooled | - | 0.507 [-,-] | - | - | 0.498 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | POOLED/ST | rf/pooled | 0.519 [0.49,0.55] | 0.507 [0.46,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +20 | POOLED | logit2/pooled | - | 0.505 [-,-] | - | - | 0.634 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | NY | gbt3/pooled | 0.519 [0.48,0.56] | 0.504 [0.45,0.56] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +30 | NY | gbt3/pooled | - | 0.498 [-,-] | - | - | 0.614 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +10 | POOLED | rf/pooled | - | 0.497 [-,-] | - | - | 0.599 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | LONDON | rf/pooled | 0.532 [0.50,0.57] | 0.495 [0.44,0.55] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | sig | ASIA | gbt3/pooled | 0.509 [0.48,0.54] | 0.495 [0.46,0.53] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +10 | NY | logit2/pooled | - | 0.486 [-,-] | - | - | 0.620 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | pre | POOLED | gbt3/pooled | - | 0.481 [-,-] | - | - | 0.600 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +5 | POOLED | logit2/pooled | - | 0.476 [-,-] | - | - | 0.615 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | +5 | NY | logit2/pooled | - | 0.470 [-,-] | - | - | 0.598 | ok | - | - | - | - | stack | locked label (reference only) |
| I3-interactions | pre | NY | gbt3/pooled | - | 0.417 [-,-] | - | - | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- I3-interactions 0 POOLED: I3-interactions: same-cell BASE hold 0.646; delta -0.046
- I3-interactions 0 ASIA: I3-interactions: same-cell BASE hold 0.532; delta +0.010
- I3-interactions 0 LONDON: I3-interactions: same-cell BASE hold 0.651; delta -0.057
- I3-interactions 0 NY: I3-interactions: same-cell BASE hold 0.680; delta -0.100
- I3-interactions 5 POOLED: I3-interactions: same-cell BASE hold 0.634; delta -0.019
- I3-interactions 5 ASIA: I3-interactions: same-cell BASE hold 0.532; delta +0.011
- I3-interactions 5 LONDON: I3-interactions: same-cell BASE hold 0.583; delta -0.025
- I3-interactions 5 NY: I3-interactions: same-cell BASE hold 0.716; delta -0.118
- I3-interactions 10 POOLED: I3-interactions: same-cell BASE hold 0.672; delta -0.073
- I3-interactions 10 ASIA: I3-interactions: same-cell BASE hold 0.521; delta -0.024
- I3-interactions 10 LONDON: I3-interactions: same-cell BASE hold 0.587; delta -0.008
- I3-interactions 10 NY: I3-interactions: same-cell BASE hold 0.765; delta -0.146
- I3-interactions 15 POOLED: I3-interactions: same-cell BASE hold 0.695; delta -0.070
- I3-interactions 15 ASIA: I3-interactions: same-cell BASE hold 0.543; delta -0.011
- I3-interactions 15 LONDON: I3-interactions: same-cell BASE hold 0.658; delta -0.109
- I3-interactions 15 NY: I3-interactions: same-cell BASE hold 0.802; delta -0.160
- I3-interactions 20 POOLED: I3-interactions: same-cell BASE hold 0.681; delta -0.047
- I3-interactions 20 ASIA: I3-interactions: same-cell BASE hold 0.506; delta -0.001
- I3-interactions 20 LONDON: I3-interactions: same-cell BASE hold 0.647; delta -0.082
- I3-interactions 20 NY: I3-interactions: same-cell BASE hold 0.832; delta -0.176
- I3-interactions 30 POOLED: I3-interactions: same-cell BASE hold 0.686; delta -0.043
- I3-interactions 30 ASIA: I3-interactions: same-cell BASE hold 0.514; delta +0.039
- I3-interactions 30 LONDON: I3-interactions: same-cell BASE hold 0.652; delta -0.112
- I3-interactions 30 NY: I3-interactions: same-cell BASE hold 0.804; delta -0.190
- I3-interactions 45 POOLED: I3-interactions: same-cell BASE hold 0.667; delta -0.030
- I3-interactions 45 ASIA: I3-interactions: same-cell BASE hold 0.499; delta +0.043
- I3-interactions 45 LONDON: I3-interactions: same-cell BASE hold 0.627; delta -0.020
- I3-interactions 45 NY: I3-interactions: same-cell BASE hold 0.795; delta -0.130
- I3-interactions 60 POOLED: I3-interactions: same-cell BASE hold 0.705; delta -0.069
- I3-interactions 60 ASIA: I3-interactions: same-cell BASE hold 0.527; delta -0.029
- I3-interactions 60 LONDON: I3-interactions: same-cell BASE hold 0.663; delta -0.097
- I3-interactions 60 NY: I3-interactions: same-cell BASE hold 0.878; delta -0.221
- I3-interactions -1 POOLED: G ALL: same-cell GBASE hold 0.582; delta -0.020
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 ASIA: G ASIA: same-cell GBASE hold 0.562; delta -0.049
- I3-interactions -1 ASIA: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 POOLED: G HM: same-cell GBASE hold 0.579; delta -0.011
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 LONDON: G LONDON: same-cell GBASE hold 0.607; delta -0.028
- I3-interactions -1 LONDON: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 NY: G NY: same-cell GBASE hold 0.603; delta -0.037
- I3-interactions -1 NY: stop_vs_target variant of the stop_vs_rest-selected model
- I3-interactions -1 POOLED: G ST: same-cell GBASE hold 0.587; delta -0.028
- I3-interactions -1 POOLED: stop_vs_target variant of the stop_vs_rest-selected model
