# PRED ROUND 49 - block R0 round 0 - R0-baselines

Best HOLDOUT F-R AUC: +15 POOLED 0.545 [0.50,0.59] | ASIA 0.559 [-,-] | LONDON 0.534 [0.45,0.61] | NY 0.532 [0.42,0.64]
Best HOLDOUT F-R AUC: +30 POOLED 0.541 [-,-] | ASIA 0.541 [0.48,0.60] | LONDON 0.546 [-,-] | NY 0.571 [-,-]
Best G HOLDOUT AUC: 0.630 [0.56,0.69]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5684bb40b1646e70bc0235e65bdefb03b65251ac079274f41b66557c72e1dfa7 ; trials added 0 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False, 'source': 'FAILPRED R9'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R0-FAILPRED-G-all | sig | NY/ST | lite-stack (logit2,gbt3,rf) | 0.608 [0.56,0.65] | 0.630 [0.56,0.69] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | LONDON/ST | lite-stack (logit2,gbt3,rf) | 0.634 [0.59,0.67] | 0.626 [0.55,0.69] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | NY | lite-stack (logit2,gbt3,rf) | 0.610 [0.57,0.64] | 0.618 [0.57,0.66] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | POOLED/ST | lite-stack (logit2,gbt3,rf) | 0.602 [0.58,0.62] | 0.615 [0.58,0.65] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | ASIA/HM | lite-stack (logit2,gbt3,rf) | 0.583 [0.55,0.61] | 0.606 [0.57,0.64] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | POOLED | lite-stack (logit2,gbt3,rf) | 0.595 [0.58,0.61] | 0.606 [0.58,0.63] | - | - | - | ok | 288 | 0 | - | 1/5 |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | ASIA | lite-stack (logit2,gbt3,rf) | 0.577 [0.55,0.60] | 0.604 [0.57,0.63] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | ASIA/ST | lite-stack (logit2,gbt3,rf) | 0.571 [0.54,0.60] | 0.603 [0.57,0.64] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | LONDON | lite-stack (logit2,gbt3,rf) | 0.611 [0.58,0.64] | 0.603 [0.55,0.65] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | POOLED/HM | lite-stack (logit2,gbt3,rf) | 0.587 [0.57,0.61] | 0.598 [0.57,0.63] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | NY/HM | lite-stack (logit2,gbt3,rf) | 0.606 [0.56,0.65] | 0.598 [0.52,0.67] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G-all | sig | LONDON/HM | lite-stack (logit2,gbt3,rf) | 0.588 [0.55,0.63] | 0.583 [0.53,0.64] | - | - | - | ok | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +60 | NY | lite-stack (logit2,gbt3,rf) | - | 0.578 [-,-] | - | - | 0.873 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +60 | NY | lite-stack | 0.524 [0.45,0.60] | 0.578 [0.47,0.68] | - | 0.585 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +45 | LONDON | lite-stack | 0.541 [0.49,0.60] | 0.576 [0.50,0.66] | - | 0.553 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +20 | NY | lite-stack (logit2,gbt3,rf) | - | 0.575 [-,-] | - | - | 0.832 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +20 | NY | lite-stack | 0.502 [0.43,0.58] | 0.575 [0.47,0.68] | - | 0.576 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +30 | NY | lite-stack (logit2,gbt3,rf) | - | 0.571 [-,-] | - | - | 0.804 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +30 | NY | lite-stack | 0.499 [0.43,0.57] | 0.571 [0.46,0.68] | - | 0.584 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +10 | LONDON | lite-stack | 0.521 [0.47,0.57] | 0.570 [0.50,0.64] | - | 0.537 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +60 | LONDON | lite-stack | 0.523 [0.47,0.58] | 0.566 [0.49,0.64] | - | 0.559 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +45 | ASIA | lite-stack | 0.512 [0.47,0.56] | 0.563 [0.50,0.62] | - | 0.572 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | +15 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.559 [-,-] | - | - | 0.570 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +15 | ASIA | lite-stack | 0.548 [0.50,0.59] | 0.559 [0.50,0.61] | - | 0.560 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +10 | POOLED | lite-stack | 0.526 [0.49,0.56] | 0.556 [0.51,0.60] | - | 0.517 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +45 | POOLED | lite-stack | 0.529 [0.50,0.56] | 0.553 [0.51,0.60] | - | 0.530 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +10 | NY | lite-stack (logit2,gbt3,rf) | - | 0.551 [-,-] | - | - | 0.773 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +10 | NY | lite-stack | 0.497 [0.43,0.56] | 0.551 [0.47,0.64] | - | 0.560 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +5 | ASIA | lite-stack | 0.525 [0.49,0.57] | 0.547 [0.48,0.61] | - | 0.534 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | NY/HM | lite-stack (logit2,gbt3,rf) | 0.534 [0.51,0.56] | 0.547 [0.51,0.58] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | +30 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.546 [-,-] | - | - | 0.661 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +30 | LONDON | lite-stack | 0.508 [0.45,0.56] | 0.546 [0.46,0.64] | - | 0.512 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +15 | POOLED | lite-stack | 0.538 [0.51,0.57] | 0.545 [0.50,0.59] | - | 0.524 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +45 | NY | lite-stack (logit2,gbt3,rf) | - | 0.541 [-,-] | - | - | 0.790 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +45 | NY | lite-stack | 0.497 [0.42,0.57] | 0.541 [0.43,0.65] | - | 0.531 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | NY | lite-stack (logit2,gbt3,rf) | 0.534 [0.52,0.55] | 0.541 [0.52,0.57] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | +30 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.541 [-,-] | - | - | 0.687 | ok | 10664 | 41307 | - | 2/5 |  | locked label (reference only) |
| R0c-FR-A | +30 | POOLED | lite-stack | 0.512 [0.48,0.54] | 0.541 [0.49,0.59] | - | 0.529 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +30 | ASIA | lite-stack | 0.525 [0.48,0.57] | 0.541 [0.48,0.60] | - | 0.535 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | +10 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.537 [-,-] | - | - | 0.682 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +10 | LONDON | lite-stack | 0.496 [0.45,0.55] | 0.537 [0.46,0.62] | - | 0.534 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +20 | POOLED | lite-stack | 0.535 [0.51,0.56] | 0.536 [0.49,0.59] | - | 0.519 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +10 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.536 [-,-] | - | - | 0.682 | ok | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| R0c-FR-A | +10 | POOLED | lite-stack | 0.509 [0.48,0.54] | 0.536 [0.49,0.58] | - | 0.524 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | NY/ST | lite-stack (logit2,gbt3,rf) | 0.534 [0.52,0.55] | 0.536 [0.51,0.56] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | +45 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.536 [-,-] | - | - | 0.642 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +45 | LONDON | lite-stack | 0.505 [0.45,0.56] | 0.536 [0.46,0.62] | - | 0.542 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +60 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.535 [-,-] | - | - | 0.527 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +60 | ASIA | lite-stack | 0.509 [0.46,0.56] | 0.535 [0.47,0.60] | - | 0.534 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +5 | POOLED | lite-stack | 0.518 [0.49,0.55] | 0.534 [0.49,0.58] | - | 0.507 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +15 | LONDON | lite-stack | 0.535 [0.48,0.59] | 0.534 [0.45,0.61] | - | 0.531 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +60 | POOLED | lite-stack | 0.525 [0.49,0.56] | 0.532 [0.49,0.58] | - | 0.512 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +15 | NY | lite-stack | 0.527 [0.46,0.59] | 0.532 [0.42,0.64] | - | 0.512 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +5 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.532 [-,-] | - | - | 0.528 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +5 | ASIA | lite-stack | 0.529 [0.49,0.57] | 0.532 [0.47,0.59] | - | 0.518 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | pre | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.532 [-,-] | - | - | 0.529 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | pre | ASIA | lite-stack | 0.555 [0.51,0.59] | 0.532 [0.46,0.60] | - | 0.510 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +60 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.531 [-,-] | - | - | 0.707 | ok | 1366 | 49884 | - | 1/5 |  | locked label (reference only) |
| R0c-FR-A | +60 | POOLED | lite-stack | 0.500 [0.47,0.53] | 0.531 [0.49,0.57] | - | 0.533 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +10 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.531 [-,-] | - | - | 0.525 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +10 | ASIA | lite-stack | 0.548 [0.50,0.59] | 0.531 [0.47,0.60] | - | 0.510 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +15 | ASIA | lite-stack | 0.515 [0.47,0.56] | 0.531 [0.46,0.59] | - | 0.529 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-G | sig | LONDON/ST | lite-stack (logit2,gbt3,rf) | 0.487 [0.44,0.53] | 0.529 [0.47,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +15 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.529 [-,-] | - | - | 0.703 | ok | 1396 | -23203 | - | 2/5 |  | locked label (reference only) |
| R0c-FR-A | +15 | POOLED | lite-stack | 0.506 [0.48,0.54] | 0.529 [0.48,0.57] | - | 0.519 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +30 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.528 [-,-] | - | - | 0.514 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +30 | ASIA | lite-stack | 0.535 [0.49,0.58] | 0.528 [0.47,0.58] | - | 0.516 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | LONDON | lite-stack (logit2,gbt3,rf) | 0.486 [0.45,0.52] | 0.526 [0.48,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | LONDON/HM | lite-stack (logit2,gbt3,rf) | 0.484 [0.44,0.53] | 0.523 [0.46,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | pre | POOLED | lite-stack | 0.510 [0.48,0.54] | 0.523 [0.48,0.58] | - | 0.512 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +30 | ASIA | lite-stack | 0.531 [0.49,0.57] | 0.523 [0.46,0.59] | - | 0.489 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +10 | NY | lite-stack | 0.511 [0.47,0.55] | 0.522 [0.46,0.59] | - | 0.524 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | pre | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.522 [-,-] | - | - | 0.658 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | pre | LONDON | lite-stack | 0.511 [0.46,0.56] | 0.522 [0.44,0.61] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +20 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.521 [-,-] | - | - | 0.503 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +20 | ASIA | lite-stack | 0.517 [0.47,0.56] | 0.521 [0.46,0.58] | - | 0.519 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +20 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.521 [-,-] | - | - | 0.686 | ok | 1069 | 9540 | - | 1/5 |  | locked label (reference only) |
| R0c-FR-A | +20 | POOLED | lite-stack | 0.486 [0.46,0.52] | 0.521 [0.48,0.57] | - | 0.516 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +15 | NY | lite-stack (logit2,gbt3,rf) | - | 0.520 [-,-] | - | - | 0.802 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +15 | NY | lite-stack | 0.501 [0.43,0.56] | 0.520 [0.43,0.61] | - | 0.517 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +20 | ASIA | lite-stack | 0.528 [0.49,0.57] | 0.520 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +45 | NY | lite-stack | 0.489 [0.42,0.56] | 0.519 [0.43,0.61] | - | 0.517 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | POOLED/ST | lite-stack (logit2,gbt3,rf) | 0.515 [0.50,0.53] | 0.518 [0.50,0.53] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FAILPRED-G-all | sig | POOLED | lite-stack (logit2,gbt3,rf) | 0.515 [0.50,0.53] | 0.516 [0.50,0.53] | - | - | - | N | 777 | -3179 | - | 2/5 |  | baseline |
| R0c-FR-B | +20 | LONDON | lite-stack | 0.513 [0.46,0.56] | 0.516 [0.44,0.60] | - | 0.482 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +10 | ASIA | lite-stack | 0.527 [0.48,0.57] | 0.515 [0.45,0.57] | - | 0.482 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | pre | ASIA | lite-stack | 0.517 [0.47,0.56] | 0.515 [0.45,0.58] | - | 0.510 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +45 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.514 [-,-] | - | - | 0.674 | ok | 2367 | -36144 | - | 2/5 |  | locked label (reference only) |
| R0c-FR-A | +45 | POOLED | lite-stack | 0.497 [0.47,0.53] | 0.514 [0.46,0.56] | - | 0.506 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | POOLED/HM | lite-stack (logit2,gbt3,rf) | 0.515 [0.50,0.53] | 0.514 [0.49,0.54] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +60 | ASIA | lite-stack | 0.511 [0.47,0.55] | 0.514 [0.45,0.58] | - | 0.518 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +10 | ASIA | lite-stack | 0.512 [0.47,0.55] | 0.513 [0.46,0.58] | - | 0.517 | - | - | - | - | - | - |  | reference (unconditional) |
| R0c-FR-B | +45 | ASIA | lite-stack | 0.516 [0.47,0.56] | 0.513 [0.45,0.58] | - | 0.493 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G | sig | ASIA/ST | lite-stack (logit2,gbt3,rf) | 0.502 [0.47,0.53] | 0.512 [0.47,0.55] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-B | +20 | ASIA | lite-stack | 0.541 [0.50,0.58] | 0.511 [0.45,0.57] | - | 0.491 | - | - | - | - | - | - |  | baseline |
| R0u-FAILPRED-G-all | sig | ASIA/ST | lite-stack (logit2,gbt3,rf) | 0.509 [0.48,0.54] | 0.510 [0.48,0.54] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-G | sig | POOLED/ST | lite-stack (logit2,gbt3,rf) | 0.485 [0.46,0.51] | 0.510 [0.48,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +30 | POOLED | lite-stack | 0.512 [0.48,0.54] | 0.510 [0.47,0.55] | - | 0.477 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | pre | ASIA | lite-stack | 0.534 [0.50,0.57] | 0.510 [0.45,0.57] | - | 0.490 | - | - | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | +45 | ASIA | lite-stack (logit2,gbt3,rf) | - | 0.510 [-,-] | - | - | 0.504 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +45 | ASIA | lite-stack | 0.502 [0.46,0.55] | 0.510 [0.45,0.57] | - | 0.495 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | POOLED | lite-stack (logit2,gbt3,rf) | 0.492 [0.47,0.51] | 0.507 [0.47,0.54] | - | - | - | N | 2508 | 171368 | - | 1/5 |  | locked label (reference only) |
| R0u-FR-B | +20 | LONDON | lite-stack | 0.481 [0.43,0.53] | 0.507 [0.44,0.57] | - | 0.502 | - | - | - | - | - | - |  | baseline |
| R0u-FAILPRED-G-all | sig | ASIA | lite-stack (logit2,gbt3,rf) | 0.508 [0.48,0.53] | 0.506 [0.48,0.53] | - | - | - | N | - | - | - | - |  | baseline |
| R0c-FR-B | +60 | ASIA | lite-stack | 0.518 [0.47,0.56] | 0.505 [0.44,0.57] | - | 0.473 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | POOLED/HM | lite-stack (logit2,gbt3,rf) | 0.501 [0.47,0.53] | 0.505 [0.47,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +5 | LONDON | lite-stack | 0.472 [0.43,0.51] | 0.505 [0.45,0.56] | - | 0.520 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | +20 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.504 [-,-] | - | - | 0.663 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +20 | LONDON | lite-stack | 0.467 [0.42,0.52] | 0.504 [0.43,0.58] | - | 0.504 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | NY | lite-stack (logit2,gbt3,rf) | 0.506 [0.47,0.54] | 0.502 [0.44,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | pre | ASIA | lite-stack | 0.523 [0.48,0.56] | 0.502 [0.45,0.55] | - | 0.499 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-G | sig | NY/HM | lite-stack (logit2,gbt3,rf) | 0.514 [0.46,0.57] | 0.502 [0.43,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +60 | ASIA | lite-stack | 0.510 [0.46,0.56] | 0.502 [0.44,0.57] | - | 0.478 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +10 | ASIA | lite-stack | 0.539 [0.50,0.58] | 0.501 [0.44,0.57] | - | 0.490 | - | - | - | - | - | - |  | baseline |
| R0-FAILPRED-G | sig | NY/ST | lite-stack (logit2,gbt3,rf) | 0.498 [0.45,0.55] | 0.501 [0.43,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | ASIA/ST | lite-stack (logit2,gbt3,rf) | 0.478 [0.44,0.51] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +45 | POOLED | lite-stack | 0.494 [0.47,0.52] | 0.501 [0.46,0.54] | - | 0.504 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | +5 | NY | lite-stack (logit2,gbt3,rf) | - | 0.500 [-,-] | - | - | 0.692 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +5 | NY | lite-stack | 0.472 [0.41,0.53] | 0.500 [0.42,0.59] | - | 0.548 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G-all | sig | ASIA/HM | lite-stack (logit2,gbt3,rf) | 0.506 [0.48,0.54] | 0.500 [0.47,0.54] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +20 | NY | lite-stack | 0.523 [0.48,0.57] | 0.500 [0.43,0.57] | - | 0.489 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | pre | LONDON | lite-stack | 0.505 [0.46,0.55] | 0.499 [0.44,0.56] | - | 0.502 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-G | sig | ASIA | lite-stack (logit2,gbt3,rf) | 0.491 [0.46,0.52] | 0.498 [0.46,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +20 | POOLED | lite-stack | 0.511 [0.49,0.54] | 0.498 [0.46,0.53] | - | 0.490 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +45 | ASIA | lite-stack | 0.505 [0.46,0.55] | 0.496 [0.43,0.56] | - | 0.494 | - | - | - | - | - | - |  | baseline |
| R0c-FR-B | +15 | ASIA | lite-stack | 0.525 [0.48,0.57] | 0.496 [0.44,0.56] | - | 0.475 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-G | sig | ASIA/HM | lite-stack (logit2,gbt3,rf) | 0.507 [0.47,0.55] | 0.496 [0.44,0.55] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G | sig | LONDON/HM | lite-stack (logit2,gbt3,rf) | 0.492 [0.47,0.52] | 0.495 [0.46,0.53] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FAILPRED-G | sig | ASIA | lite-stack (logit2,gbt3,rf) | 0.486 [0.46,0.51] | 0.494 [0.46,0.53] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FAILPRED-G-all | sig | LONDON/ST | lite-stack (logit2,gbt3,rf) | 0.480 [0.46,0.50] | 0.493 [0.46,0.52] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | pre | POOLED | lite-stack | 0.512 [0.49,0.54] | 0.493 [0.46,0.53] | - | 0.493 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +15 | POOLED | lite-stack | 0.492 [0.47,0.52] | 0.492 [0.45,0.53] | - | 0.496 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-B | +5 | LONDON | lite-stack | 0.502 [0.46,0.55] | 0.492 [0.43,0.55] | - | 0.494 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +15 | LONDON | lite-stack | 0.464 [0.41,0.51] | 0.492 [0.42,0.56] | - | 0.492 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +20 | POOLED | lite-stack | 0.504 [0.48,0.53] | 0.491 [0.45,0.53] | - | 0.492 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G | sig | LONDON | lite-stack (logit2,gbt3,rf) | 0.483 [0.46,0.50] | 0.491 [0.46,0.52] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | pre | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.490 [-,-] | - | - | 0.648 | ok | 1384 | 44245 | - | 1/5 |  | locked label (reference only) |
| R0c-FR-A | pre | POOLED | lite-stack | 0.495 [0.47,0.52] | 0.490 [0.45,0.53] | - | 0.485 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G | sig | POOLED/ST | lite-stack (logit2,gbt3,rf) | 0.489 [0.48,0.50] | 0.490 [0.47,0.51] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +60 | POOLED | lite-stack | 0.498 [0.47,0.52] | 0.490 [0.45,0.53] | - | 0.488 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G | sig | POOLED | lite-stack (logit2,gbt3,rf) | 0.489 [0.48,0.50] | 0.487 [0.47,0.50] | - | - | - | N | 744 | -7581 | - | 3/5 |  | baseline |
| R0u-FAILPRED-G | sig | LONDON/ST | lite-stack (logit2,gbt3,rf) | 0.476 [0.45,0.50] | 0.486 [0.46,0.52] | - | - | - | N | - | - | - | - |  | baseline |
| R0-FAILPRED-FR | +15 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.486 [-,-] | - | - | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +15 | LONDON | lite-stack | 0.474 [0.42,0.53] | 0.486 [0.40,0.56] | - | 0.471 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +20 | LONDON | lite-stack | 0.488 [0.44,0.54] | 0.486 [0.42,0.55] | - | 0.481 | - | - | - | - | - | - |  | reference (unconditional) |
| R0c-FR-B | +10 | NY | lite-stack | 0.494 [0.43,0.56] | 0.485 [0.38,0.59] | - | 0.502 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +30 | LONDON | lite-stack | 0.512 [0.46,0.57] | 0.485 [0.41,0.57] | - | 0.456 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FAILPRED-G | sig | NY/HM | lite-stack (logit2,gbt3,rf) | 0.504 [0.48,0.53] | 0.484 [0.45,0.52] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +10 | POOLED | lite-stack | 0.494 [0.47,0.52] | 0.484 [0.45,0.52] | - | 0.487 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G-all | sig | LONDON | lite-stack (logit2,gbt3,rf) | 0.482 [0.46,0.50] | 0.484 [0.46,0.51] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FAILPRED-G | sig | POOLED/HM | lite-stack (logit2,gbt3,rf) | 0.489 [0.47,0.50] | 0.482 [0.46,0.51] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-B | +20 | NY | lite-stack | 0.512 [0.47,0.55] | 0.482 [0.42,0.54] | - | 0.489 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +60 | POOLED | lite-stack | 0.503 [0.48,0.53] | 0.482 [0.44,0.53] | - | 0.478 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +20 | ASIA | lite-stack | 0.502 [0.45,0.55] | 0.481 [0.42,0.54] | - | 0.482 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G | sig | NY | lite-stack (logit2,gbt3,rf) | 0.496 [0.48,0.51] | 0.480 [0.46,0.51] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-B | +5 | ASIA | lite-stack | 0.515 [0.48,0.56] | 0.480 [0.42,0.54] | - | 0.464 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | pre | NY | lite-stack | 0.517 [0.48,0.56] | 0.479 [0.42,0.54] | - | 0.489 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +30 | POOLED | lite-stack | 0.489 [0.46,0.52] | 0.479 [0.44,0.51] | - | 0.481 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +45 | LONDON | lite-stack | 0.481 [0.43,0.52] | 0.478 [0.42,0.53] | - | 0.490 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G | sig | NY/ST | lite-stack (logit2,gbt3,rf) | 0.491 [0.47,0.51] | 0.478 [0.45,0.50] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +60 | NY | lite-stack | 0.494 [0.45,0.54] | 0.477 [0.41,0.55] | - | 0.478 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-B | +30 | ASIA | lite-stack | 0.505 [0.46,0.55] | 0.475 [0.42,0.53] | - | 0.463 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +5 | POOLED | lite-stack | 0.484 [0.46,0.51] | 0.474 [0.43,0.51] | - | 0.475 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G | sig | ASIA/HM | lite-stack (logit2,gbt3,rf) | 0.468 [0.44,0.49] | 0.473 [0.43,0.52] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +5 | ASIA | lite-stack | 0.504 [0.46,0.55] | 0.472 [0.42,0.53] | - | 0.466 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +30 | LONDON | lite-stack | 0.470 [0.42,0.52] | 0.472 [0.41,0.54] | - | 0.481 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FAILPRED-G-all | sig | LONDON/HM | lite-stack (logit2,gbt3,rf) | 0.484 [0.46,0.51] | 0.472 [0.44,0.51] | - | - | - | N | - | - | - | - |  | baseline |
| R0u-FR-B | +60 | LONDON | lite-stack | 0.520 [0.47,0.57] | 0.471 [0.41,0.54] | - | 0.464 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +15 | ASIA | lite-stack | 0.522 [0.48,0.56] | 0.470 [0.41,0.53] | - | 0.458 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +5 | POOLED | lite-stack | 0.494 [0.47,0.52] | 0.469 [0.43,0.51] | - | 0.469 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | pre | POOLED | lite-stack | 0.490 [0.47,0.52] | 0.468 [0.43,0.51] | - | 0.464 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +15 | NY | lite-stack | 0.503 [0.46,0.55] | 0.468 [0.40,0.54] | - | 0.470 | - | - | - | - | - | - |  | reference (unconditional) |
| R0-FAILPRED-FR | +60 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.467 [-,-] | - | - | 0.650 | ok | - | - | - | - |  | locked label (reference only) |
| R0c-FR-A | +60 | LONDON | lite-stack | 0.452 [0.39,0.51] | 0.467 [0.38,0.55] | - | 0.468 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +5 | NY | lite-stack | 0.481 [0.42,0.55] | 0.465 [0.37,0.56] | - | 0.488 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +10 | LONDON | lite-stack | 0.492 [0.45,0.54] | 0.465 [0.40,0.53] | - | 0.457 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +10 | POOLED | lite-stack | 0.504 [0.48,0.53] | 0.463 [0.42,0.51] | - | 0.455 | - | - | - | - | - | - |  | baseline |
| R0c-FR-B | pre | LONDON | lite-stack | 0.473 [0.42,0.53] | 0.463 [0.39,0.54] | - | 0.469 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +60 | NY | lite-stack | 0.479 [0.43,0.53] | 0.463 [0.39,0.54] | - | 0.460 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +5 | NY | lite-stack | 0.484 [0.44,0.53] | 0.461 [0.39,0.53] | - | 0.458 | - | - | - | - | - | - |  | reference (unconditional) |
| R0c-FR-B | +20 | NY | lite-stack | 0.519 [0.45,0.59] | 0.461 [0.35,0.56] | - | 0.448 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +5 | POOLED | lite-stack (logit2,gbt3,rf) | - | 0.460 [-,-] | - | - | 0.632 | ok | 0 | 0 | - | 0/5 |  | locked label (reference only) |
| R0c-FR-A | +5 | POOLED | lite-stack | 0.470 [0.44,0.50] | 0.460 [0.42,0.51] | - | 0.456 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | pre | NY | lite-stack | 0.512 [0.45,0.57] | 0.459 [0.35,0.56] | - | 0.461 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-A-uncond | +60 | LONDON | lite-stack | 0.482 [0.43,0.53] | 0.459 [0.39,0.53] | - | 0.460 | - | - | - | - | - | - |  | reference (unconditional) |
| R0c-FR-B | +5 | LONDON | lite-stack | 0.504 [0.45,0.56] | 0.454 [0.39,0.52] | - | 0.447 | - | - | - | - | - | - |  | locked label (reference only) |
| R0c-FR-B | +60 | NY | lite-stack | 0.493 [0.42,0.56] | 0.454 [0.35,0.56] | - | 0.440 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +15 | POOLED | lite-stack | 0.503 [0.48,0.53] | 0.453 [0.41,0.50] | - | 0.443 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | pre | LONDON | lite-stack | 0.477 [0.43,0.52] | 0.452 [0.39,0.52] | - | 0.448 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +45 | NY | lite-stack | 0.484 [0.44,0.53] | 0.452 [0.40,0.51] | - | 0.450 | - | - | - | - | - | - |  | reference (unconditional) |
| R0c-FR-A | pre | NY | lite-stack | 0.459 [0.39,0.52] | 0.448 [0.37,0.54] | - | 0.515 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | pre | NY | lite-stack (logit2,gbt3,rf) | - | 0.448 [-,-] | - | - | 0.669 | ok | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | pre | NY | lite-stack | 0.458 [0.41,0.50] | 0.447 [0.39,0.51] | - | 0.455 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +15 | NY | lite-stack | 0.495 [0.45,0.54] | 0.446 [0.38,0.53] | - | 0.452 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +45 | POOLED | lite-stack | 0.482 [0.46,0.51] | 0.443 [0.40,0.49] | - | 0.441 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +15 | LONDON | lite-stack | 0.494 [0.45,0.54] | 0.442 [0.38,0.50] | - | 0.425 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +30 | POOLED | lite-stack | 0.488 [0.46,0.51] | 0.439 [0.40,0.48] | - | 0.437 | - | - | - | - | - | - |  | baseline |
| R0c-FR-A | +5 | LONDON | lite-stack | 0.460 [0.41,0.51] | 0.438 [0.37,0.51] | - | 0.427 | - | - | - | - | - | - |  | locked label (reference only) |
| R0-FAILPRED-FR | +5 | LONDON | lite-stack (logit2,gbt3,rf) | - | 0.438 [-,-] | - | - | 0.595 | ok | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +30 | LONDON | lite-stack | 0.495 [0.45,0.54] | 0.438 [0.38,0.50] | - | 0.444 | - | - | - | - | - | - |  | baseline |
| R0u-FR-A-uncond | +30 | NY | lite-stack | 0.483 [0.44,0.53] | 0.434 [0.37,0.49] | - | 0.435 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-A-uncond | +10 | LONDON | lite-stack | 0.468 [0.42,0.52] | 0.434 [0.37,0.50] | - | 0.441 | - | - | - | - | - | - |  | reference (unconditional) |
| R0u-FR-B | +5 | NY | lite-stack | 0.467 [0.42,0.51] | 0.433 [0.38,0.49] | - | 0.447 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +45 | LONDON | lite-stack | 0.467 [0.42,0.52] | 0.432 [0.37,0.50] | - | 0.427 | - | - | - | - | - | - |  | baseline |
| R0c-FR-B | +30 | NY | lite-stack | 0.451 [0.38,0.52] | 0.426 [0.32,0.54] | - | 0.419 | - | - | - | - | - | - |  | locked label (reference only) |
| R0u-FR-B | +10 | NY | lite-stack | 0.481 [0.44,0.53] | 0.424 [0.36,0.49] | - | 0.419 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +45 | NY | lite-stack | 0.474 [0.43,0.52] | 0.400 [0.34,0.46] | - | 0.399 | - | - | - | - | - | - |  | baseline |
| R0u-FR-B | +30 | NY | lite-stack | 0.466 [0.42,0.52] | 0.396 [0.33,0.47] | - | 0.404 | - | - | - | - | - | - |  | baseline |
| REF-FR-full | pre | POOLED | full-stack (11 models) | - | - | - | - | 0.644 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | pre | ASIA | full-stack (11 models) | - | - | - | - | 0.497 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | pre | LONDON | full-stack (11 models) | - | - | - | - | 0.672 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | pre | NY | full-stack (11 models) | - | - | - | - | 0.653 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +10 | POOLED | full-stack (11 models) | - | - | - | - | 0.681 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +10 | ASIA | full-stack (11 models) | - | - | - | - | 0.571 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +10 | LONDON | full-stack (11 models) | - | - | - | - | 0.664 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +10 | NY | full-stack (11 models) | - | - | - | - | 0.767 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +15 | POOLED | full-stack (11 models) | - | - | - | - | 0.707 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +15 | ASIA | full-stack (11 models) | - | - | - | - | 0.593 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +15 | LONDON | full-stack (11 models) | - | - | - | - | 0.670 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +15 | NY | full-stack (11 models) | - | - | - | - | 0.806 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +20 | POOLED | full-stack (11 models) | - | - | - | - | 0.693 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +20 | ASIA | full-stack (11 models) | - | - | - | - | 0.527 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +20 | LONDON | full-stack (11 models) | - | - | - | - | 0.679 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +20 | NY | full-stack (11 models) | - | - | - | - | 0.831 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +30 | POOLED | full-stack (11 models) | - | - | - | - | 0.682 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +30 | ASIA | full-stack (11 models) | - | - | - | - | 0.531 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +30 | LONDON | full-stack (11 models) | - | - | - | - | 0.658 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +30 | NY | full-stack (11 models) | - | - | - | - | 0.785 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +45 | POOLED | full-stack (11 models) | - | - | - | - | 0.665 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +45 | ASIA | full-stack (11 models) | - | - | - | - | 0.490 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +45 | LONDON | full-stack (11 models) | - | - | - | - | 0.655 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +45 | NY | full-stack (11 models) | - | - | - | - | 0.746 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +5 | POOLED | full-stack (11 models) | - | - | - | - | 0.627 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +5 | ASIA | full-stack (11 models) | - | - | - | - | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +5 | LONDON | full-stack (11 models) | - | - | - | - | 0.597 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +5 | NY | full-stack (11 models) | - | - | - | - | 0.679 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +60 | POOLED | full-stack (11 models) | - | - | - | - | 0.696 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +60 | ASIA | full-stack (11 models) | - | - | - | - | 0.519 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +60 | LONDON | full-stack (11 models) | - | - | - | - | 0.640 | - | - | - | - | - |  | locked label (reference only) |
| REF-FR-full | +60 | NY | full-stack (11 models) | - | - | - | - | 0.860 | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- R0-FAILPRED-FR 0 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 0 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 0 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 0 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 10 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 10 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 10 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 10 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 15 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 15 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 15 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 15 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 20 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 20 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 20 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 20 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 30 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 30 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 30 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 30 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 45 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 45 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 45 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 45 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 5 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 5 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 5 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 5 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 60 POOLED: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 60 ASIA: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 60 LONDON: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0-FAILPRED-FR 60 NY: FAILPRED residual-stack F-R, exact predictions from failpred/out/pred; CPCV = mean-rank of logit2/gbt3/rf fixed-hp
- R0c-FR-A 0 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 0 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 0 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 0 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 10 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 10 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 10 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 10 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 15 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 15 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 15 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 15 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 20 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 20 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 20 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 20 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 30 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 30 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 30 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 30 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 45 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 45 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 45 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 45 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 5 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 5 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 5 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 5 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 60 POOLED: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 60 ASIA: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 60 LONDON: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-A 60 NY: unconditionally-trained FAILPRED stack scored on sessions with an entry
- R0c-FR-B 0 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 0 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 0 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 0 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 10 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 10 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 10 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 10 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 15 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 15 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 15 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 15 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 20 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 20 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 20 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 20 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 30 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 30 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 30 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 30 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 45 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 45 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 45 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 45 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 5 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 5 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 5 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 5 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 60 POOLED: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 60 ASIA: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 60 LONDON: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0c-FR-B 60 NY: FAILPRED stack TRAINED on entry sessions, scored on entry sessions (PRIMARY conditional baseline)
- R0u-FR-A-uncond 0 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 0 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 0 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 0 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 10 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 10 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 10 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 10 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 15 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 15 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 15 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 15 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 20 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 20 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 20 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 20 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 30 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 30 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 30 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 30 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 45 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 45 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 45 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 45 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 5 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 5 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 5 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 5 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 60 POOLED: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 60 ASIA: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 60 LONDON: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-A-uncond 60 NY: UNLOCKED label; FAILPRED stack trained on all sessions, scored on entry sessions
- R0u-FR-B 0 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 0 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 0 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 0 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 10 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 10 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 10 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 10 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 15 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 15 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 15 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 15 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 20 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 20 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 20 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 20 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 30 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 30 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 30 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 30 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 45 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 45 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 45 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 45 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 5 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 5 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 5 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 5 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 60 POOLED: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 60 ASIA: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 60 LONDON: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- R0u-FR-B 60 NY: UNLOCKED label; FAILPRED stack TRAINED on entry sessions (PRIMARY unlocked baseline)
- REF-FR-full 0 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 0 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 0 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 0 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 10 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 10 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 10 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 10 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 15 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 15 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 15 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 15 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 20 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 20 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 20 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 20 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 30 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 30 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 30 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 30 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 45 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 45 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 45 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 45 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 5 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 5 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 5 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 5 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 60 POOLED: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 60 ASIA: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 60 LONDON: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- REF-FR-full 60 NY: R0 reference: full 11-model set on the FR label (the FAILPRED baseline is the lite set)
- R0-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0u-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 POOLED: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 ASIA: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 LONDON: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
- R0-FAILPRED-G-all -1 NY: FAILPRED features as-of latest grid horizon + signal-instant block; label STOP vs TARGET; LOCK/TIME excluded; perm = stratified label shuffle
