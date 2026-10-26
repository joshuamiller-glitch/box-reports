# PRED ROUND 32 - block C round 4 - C4-cond (conditionally trained C stacks)

Best HOLDOUT F-R AUC: +15 POOLED 0.549 [0.51,0.59] | ASIA 0.519 [0.46,0.58] | LONDON 0.544 [0.47,0.62] | NY 0.555 [0.45,0.65]
Best HOLDOUT F-R AUC: +30 POOLED 0.520 [0.48,0.56] | ASIA 0.567 [0.50,0.63] | LONDON 0.514 [0.43,0.59] | NY 0.521 [0.40,0.61]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 60fe21cb8d94577453183af7289cdd796498ef8114070084d5bcb9f51c9ce042 ; trials added 3500 ; truncation audit {'decisions': 360, 'checks': 80811, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'C1/C2 session features, 4 seeds x 90 decisions, bars>=cut randomised and option file column groups with last record >= cut-300s shuffled'} ; holdout scored True ; feature store ['l2vast/pred/store/C1_gex.parquet', 'l2vast/pred/store/C2_vol.parquet', 'l2vast/pred/store/C1_hyp.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C4-cond+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.519 [0.46,0.57] | 0.600 [0.52,0.67] | - | - | 0.599 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.540 [0.47,0.61] | 0.596 [0.50,0.69] | - | - | 0.575 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.541 [0.49,0.59] | 0.579 [0.51,0.66] | - | - | 0.586 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.540 [0.48,0.60] | 0.578 [0.51,0.66] | - | - | 0.595 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.521 [0.47,0.57] | 0.576 [0.49,0.65] | - | - | 0.594 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.538 [0.51,0.57] | 0.570 [0.53,0.61] | - | - | 0.518 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.550 [0.51,0.59] | 0.567 [0.50,0.63] | - | - | 0.556 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.534 [0.50,0.56] | 0.564 [0.51,0.61] | - | - | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.526 [0.49,0.56] | 0.562 [0.52,0.61] | - | - | 0.532 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.535 [0.48,0.59] | 0.561 [0.48,0.64] | - | - | 0.596 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.534 [0.51,0.56] | 0.560 [0.51,0.61] | - | - | 0.518 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.527 [0.47,0.58] | 0.560 [0.49,0.63] | - | - | 0.572 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.526 [0.49,0.56] | 0.559 [0.52,0.60] | - | - | 0.507 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.558 [0.53,0.59] | 0.558 [0.51,0.60] | - | - | 0.496 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.524 [0.49,0.56] | 0.555 [0.51,0.60] | - | - | 0.520 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.519 [0.45,0.59] | 0.555 [0.45,0.65] | - | - | 0.620 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.529 [0.49,0.56] | 0.553 [0.51,0.60] | - | - | 0.537 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.509 [0.46,0.57] | 0.550 [0.47,0.63] | - | - | 0.557 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.527 [0.49,0.56] | 0.549 [0.50,0.60] | - | - | 0.536 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.540 [0.51,0.57] | 0.549 [0.51,0.59] | - | - | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.540 [0.49,0.59] | 0.549 [0.47,0.63] | - | - | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.516 [0.47,0.57] | 0.548 [0.47,0.63] | - | - | 0.570 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | pre | NY | lite-stack (logit2,gbt3,rf) | 0.456 [0.39,0.52] | 0.547 [0.45,0.64] | - | - | 0.556 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.512 [0.47,0.55] | 0.547 [0.49,0.60] | - | - | 0.553 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.536 [0.51,0.56] | 0.546 [0.51,0.59] | - | - | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.48,0.54] | 0.546 [0.49,0.60] | - | - | 0.481 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.536 [0.51,0.57] | 0.546 [0.50,0.59] | - | - | 0.536 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.530 [0.49,0.57] | 0.545 [0.48,0.60] | - | - | 0.543 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.548 [0.50,0.60] | 0.544 [0.47,0.62] | - | - | 0.575 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.520 [0.49,0.55] | 0.544 [0.50,0.59] | - | - | 0.521 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.519 [0.49,0.55] | 0.543 [0.50,0.59] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.532 [0.50,0.56] | 0.543 [0.50,0.59] | - | - | 0.525 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.541 [0.51,0.57] | 0.543 [0.49,0.59] | - | - | 0.523 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.535 [0.51,0.56] | 0.540 [0.49,0.59] | - | - | 0.516 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.513 [0.46,0.56] | 0.539 [0.46,0.61] | - | - | 0.527 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.529 [0.50,0.56] | 0.537 [0.49,0.58] | - | - | 0.508 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.521 [0.49,0.55] | 0.536 [0.49,0.58] | - | - | 0.507 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.498 [0.44,0.56] | 0.536 [0.47,0.61] | - | - | 0.552 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.512 [0.49,0.54] | 0.536 [0.49,0.58] | - | - | 0.475 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.541 [0.51,0.57] | 0.535 [0.49,0.58] | - | - | 0.489 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.532 [0.49,0.57] | 0.535 [0.48,0.60] | - | - | 0.518 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.523 [0.48,0.57] | 0.534 [0.48,0.60] | - | - | 0.519 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.458 [0.39,0.53] | 0.533 [0.44,0.62] | - | - | 0.529 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.522 [0.49,0.55] | 0.533 [0.48,0.58] | - | - | 0.515 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.57] | 0.532 [0.47,0.59] | - | - | 0.502 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.531 [0.48,0.59] | 0.532 [0.46,0.61] | - | - | 0.559 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.489 [0.43,0.56] | 0.531 [0.43,0.63] | - | - | 0.581 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.507 [0.44,0.57] | 0.531 [0.41,0.63] | - | - | 0.581 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.536 [0.51,0.57] | 0.530 [0.48,0.57] | - | - | 0.491 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.516 [0.49,0.55] | 0.529 [0.49,0.57] | - | - | 0.510 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.512 [0.45,0.57] | 0.529 [0.44,0.63] | - | - | 0.565 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.515 [0.44,0.58] | 0.527 [0.43,0.62] | - | - | 0.602 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.519 [0.48,0.56] | 0.527 [0.46,0.59] | - | - | 0.520 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.520 [0.48,0.56] | 0.525 [0.46,0.59] | - | - | 0.529 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.515 [0.48,0.54] | 0.524 [0.47,0.58] | - | - | 0.463 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.508 [0.46,0.55] | 0.524 [0.46,0.59] | - | - | 0.505 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.568 [0.53,0.61] | 0.523 [0.45,0.58] | - | - | 0.511 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.56] | 0.523 [0.46,0.59] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.516 [0.48,0.55] | 0.522 [0.48,0.56] | - | - | 0.497 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.56] | 0.522 [0.46,0.58] | - | - | 0.514 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.58] | 0.522 [0.44,0.61] | - | - | 0.572 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.498 [0.43,0.57] | 0.521 [0.40,0.61] | - | - | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond-only | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.548 [0.49,0.60] | 0.521 [0.44,0.60] | - | - | 0.519 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.521 [0.49,0.55] | 0.520 [0.48,0.56] | - | - | 0.532 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.537 [0.48,0.59] | 0.520 [0.45,0.59] | - | - | 0.523 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.521 [0.48,0.56] | 0.520 [0.46,0.58] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.536 [0.51,0.56] | 0.519 [0.48,0.56] | - | - | 0.507 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.487 [0.42,0.55] | 0.519 [0.41,0.62] | - | - | 0.571 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.541 [0.50,0.58] | 0.519 [0.46,0.58] | - | - | 0.513 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.493 [0.42,0.56] | 0.519 [0.43,0.60] | - | - | 0.607 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.538 [0.49,0.58] | 0.519 [0.46,0.58] | - | - | 0.512 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.539 [0.50,0.58] | 0.519 [0.46,0.58] | - | - | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.500 [0.46,0.54] | 0.519 [0.45,0.58] | - | - | 0.477 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.527 [0.48,0.57] | 0.516 [0.45,0.58] | - | - | 0.512 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.500 [0.45,0.56] | 0.516 [0.45,0.59] | - | - | 0.517 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.523 [0.48,0.56] | 0.515 [0.45,0.58] | - | - | 0.490 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.517 [0.49,0.55] | 0.514 [0.47,0.56] | - | - | 0.518 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.521 [0.48,0.56] | 0.514 [0.45,0.58] | - | - | 0.508 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.538 [0.50,0.58] | 0.514 [0.45,0.58] | - | - | 0.505 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.501 [0.44,0.57] | 0.514 [0.40,0.62] | - | - | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.537 [0.48,0.59] | 0.514 [0.43,0.59] | - | - | 0.539 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.547 [0.50,0.60] | 0.513 [0.44,0.59] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.513 [0.47,0.56] | 0.512 [0.44,0.58] | - | - | 0.496 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.543 [0.49,0.60] | 0.509 [0.43,0.60] | - | - | 0.541 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.472 [0.40,0.54] | 0.508 [0.41,0.61] | - | - | 0.472 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.525 [0.48,0.57] | 0.504 [0.44,0.57] | - | - | 0.499 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.512 [0.46,0.56] | 0.503 [0.43,0.57] | - | - | 0.484 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.504 [0.48,0.53] | 0.503 [0.46,0.55] | - | - | 0.519 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.485 [0.42,0.55] | 0.502 [0.41,0.59] | - | - | 0.476 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.514 [0.49,0.54] | 0.502 [0.46,0.54] | - | - | 0.488 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.518 [0.48,0.56] | 0.500 [0.45,0.56] | - | - | 0.491 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.515 [0.47,0.56] | 0.500 [0.43,0.56] | - | - | 0.476 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.515 [0.47,0.56] | 0.500 [0.43,0.56] | - | - | 0.476 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.516 [0.46,0.57] | 0.498 [0.43,0.57] | - | - | 0.493 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.531 [0.49,0.57] | 0.498 [0.44,0.56] | - | - | 0.487 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.517 [0.47,0.57] | 0.498 [0.43,0.57] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.501 [0.44,0.57] | 0.494 [0.39,0.59] | - | - | 0.637 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.532 [0.48,0.58] | 0.494 [0.42,0.57] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.532 [0.48,0.58] | 0.493 [0.42,0.56] | - | - | 0.494 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond-only | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.504 [0.45,0.55] | 0.492 [0.42,0.57] | - | - | 0.511 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.483 [0.41,0.55] | 0.492 [0.40,0.57] | - | - | 0.594 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.490 [0.41,0.57] | 0.492 [0.37,0.60] | - | - | 0.525 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond-only | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.476 [0.41,0.55] | 0.489 [0.39,0.58] | - | - | 0.551 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond-only | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.523 [0.48,0.57] | 0.487 [0.43,0.54] | - | - | 0.475 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond-only | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.528 [0.48,0.57] | 0.487 [0.43,0.55] | - | - | 0.475 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.515 [0.47,0.57] | 0.487 [0.41,0.57] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.515 [0.45,0.58] | 0.485 [0.38,0.58] | - | - | 0.567 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.509 [0.45,0.57] | 0.484 [0.41,0.57] | - | - | 0.559 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.487 [0.42,0.55] | 0.480 [0.38,0.58] | - | - | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.521 [0.47,0.57] | 0.478 [0.42,0.55] | - | - | 0.504 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.506 [0.43,0.58] | 0.473 [0.36,0.58] | - | - | 0.586 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.483 [0.44,0.53] | 0.467 [0.41,0.52] | - | - | 0.443 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.517 [0.46,0.58] | 0.466 [0.36,0.56] | - | - | 0.471 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.522 [0.47,0.58] | 0.465 [0.41,0.53] | - | - | 0.546 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.480 [0.43,0.54] | 0.463 [0.39,0.54] | - | - | 0.477 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.453 [0.39,0.52] | 0.455 [0.35,0.58] | - | - | 0.537 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.479 [0.41,0.54] | 0.453 [0.36,0.54] | - | - | 0.546 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.525 [0.48,0.57] | 0.452 [0.40,0.51] | - | - | 0.433 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.481 [0.43,0.53] | 0.451 [0.37,0.53] | - | - | 0.478 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.470 [0.40,0.55] | 0.447 [0.35,0.55] | - | - | 0.560 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.510 [0.46,0.56] | 0.445 [0.37,0.52] | - | - | 0.546 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.496 [0.43,0.57] | 0.439 [0.33,0.54] | - | - | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.479 [0.42,0.54] | 0.438 [0.34,0.53] | - | - | 0.457 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.468 [0.40,0.53] | 0.437 [0.33,0.54] | - | - | 0.523 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.477 [0.41,0.55] | 0.433 [0.34,0.54] | - | - | 0.599 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond-only | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.514 [0.44,0.58] | 0.427 [0.31,0.54] | - | - | 0.485 | - | - | - | - | - |  | locked label (reference only) |
| C4-cond+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.436 [0.37,0.51] | 0.407 [0.30,0.52] | - | - | 0.512 | - | - | - | - | - | stack | locked label (reference only) |
| C4-cond+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.442 [0.37,0.51] | 0.401 [0.29,0.53] | - | - | 0.505 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- C4-cond-only 0 POOLED: C_round1_V1c ALL: WF 0.517 hold 0.506 vs baseline 0.626/0.648
- C4-cond-only 0 ASIA: C_round1_V1c ASIA: WF 0.525 hold 0.509 vs baseline 0.567/0.529
- C4-cond-only 0 LONDON: C_round1_V1c LONDON: WF 0.524 hold 0.522 vs baseline 0.602/0.658
- C4-cond-only 0 NY: C_round1_V1c NY: WF 0.510 hold 0.556 vs baseline 0.638/0.669
- C4-cond-only 10 POOLED: C_round1_V1c ALL: WF 0.530 hold 0.496 vs baseline 0.650/0.682
- C4-cond-only 10 ASIA: C_round1_V1c ASIA: WF 0.550 hold 0.511 vs baseline 0.569/0.525
- C4-cond-only 10 LONDON: C_round1_V1c LONDON: WF 0.530 hold 0.519 vs baseline 0.624/0.682
- C4-cond-only 10 NY: C_round1_V1c NY: WF 0.498 hold 0.472 vs baseline 0.697/0.773
- C4-cond-only 15 POOLED: C_round1_V1c ALL: WF 0.520 hold 0.491 vs baseline 0.665/0.703
- C4-cond-only 15 ASIA: C_round1_V1c ASIA: WF 0.504 hold 0.475 vs baseline 0.576/0.570
- C4-cond-only 15 LONDON: C_round1_V1c LONDON: WF 0.506 hold 0.527 vs baseline 0.629/0.668
- C4-cond-only 15 NY: C_round1_V1c NY: WF 0.547 hold 0.485 vs baseline 0.726/0.802
- C4-cond-only 20 POOLED: C_round1_V1c ALL: WF 0.533 hold 0.489 vs baseline 0.628/0.686
- C4-cond-only 20 ASIA: C_round1_V1c ASIA: WF 0.512 hold 0.475 vs baseline 0.498/0.503
- C4-cond-only 20 LONDON: C_round1_V1c LONDON: WF 0.547 hold 0.523 vs baseline 0.592/0.663
- C4-cond-only 20 NY: C_round1_V1c NY: WF 0.546 hold 0.525 vs baseline 0.723/0.832
- C4-cond-only 30 POOLED: C_round1_V1c ALL: WF 0.535 hold 0.507 vs baseline 0.644/0.687
- C4-cond-only 30 ASIA: C_round1_V1c ASIA: WF 0.507 hold 0.433 vs baseline 0.524/0.514
- C4-cond-only 30 LONDON: C_round1_V1c LONDON: WF 0.543 hold 0.539 vs baseline 0.612/0.661
- C4-cond-only 30 NY: C_round1_V1c NY: WF 0.569 hold 0.586 vs baseline 0.716/0.804
- C4-cond-only 45 POOLED: C_round1_V1c ALL: WF 0.506 hold 0.488 vs baseline 0.624/0.674
- C4-cond-only 45 ASIA: C_round1_V1c ASIA: WF 0.461 hold 0.443 vs baseline 0.494/0.504
- C4-cond-only 45 LONDON: C_round1_V1c LONDON: WF 0.513 hold 0.493 vs baseline 0.603/0.642
- C4-cond-only 45 NY: C_round1_V1c NY: WF 0.538 hold 0.522 vs baseline 0.676/0.790
- C4-cond-only 5 POOLED: C_round1_V1c ALL: WF 0.518 hold 0.499 vs baseline 0.606/0.632
- C4-cond-only 5 ASIA: C_round1_V1c ASIA: WF 0.526 hold 0.513 vs baseline 0.541/0.528
- C4-cond-only 5 LONDON: C_round1_V1c LONDON: WF 0.522 hold 0.494 vs baseline 0.568/0.595
- C4-cond-only 5 NY: C_round1_V1c NY: WF 0.506 hold 0.529 vs baseline 0.633/0.692
- C4-cond-only 60 POOLED: C_round1_V1c ALL: WF 0.512 hold 0.497 vs baseline 0.652/0.707
- C4-cond-only 60 ASIA: C_round1_V1c ASIA: WF 0.487 hold 0.476 vs baseline 0.498/0.527
- C4-cond-only 60 LONDON: C_round1_V1c LONDON: WF 0.530 hold 0.511 vs baseline 0.597/0.650
- C4-cond-only 60 NY: C_round1_V1c NY: WF 0.539 hold 0.551 vs baseline 0.780/0.873
- C4-cond+base 0 POOLED: C_round2_V2c ALL: WF 0.509 hold 0.475 vs baseline 0.626/0.648
- C4-cond+base 0 ASIA: C_round2_V2c ASIA: WF 0.520 hold 0.528 vs baseline 0.567/0.529
- C4-cond+base 0 LONDON: C_round2_V2c LONDON: WF 0.515 hold 0.517 vs baseline 0.602/0.658
- C4-cond+base 0 NY: C_round2_V2c NY: WF 0.519 hold 0.457 vs baseline 0.638/0.669
- C4-cond+base 10 POOLED: C_round2_V2c ALL: WF 0.516 hold 0.520 vs baseline 0.650/0.682
- C4-cond+base 10 ASIA: C_round2_V2c ASIA: WF 0.513 hold 0.512 vs baseline 0.569/0.525
- C4-cond+base 10 LONDON: C_round2_V2c LONDON: WF 0.518 hold 0.552 vs baseline 0.624/0.682
- C4-cond+base 10 NY: C_round2_V2c NY: WF 0.545 hold 0.565 vs baseline 0.697/0.773
- C4-cond+base 15 POOLED: C_round2_V2c ALL: WF 0.531 hold 0.536 vs baseline 0.665/0.703
- C4-cond+base 15 ASIA: C_round2_V2c ASIA: WF 0.521 hold 0.512 vs baseline 0.576/0.570
- C4-cond+base 15 LONDON: C_round2_V2c LONDON: WF 0.508 hold 0.528 vs baseline 0.629/0.668
- C4-cond+base 15 NY: C_round2_V2c NY: WF 0.585 hold 0.620 vs baseline 0.726/0.802
- C4-cond+base 20 POOLED: C_round2_V2c ALL: WF 0.525 hold 0.525 vs baseline 0.628/0.686
- C4-cond+base 20 ASIA: C_round2_V2c ASIA: WF 0.508 hold 0.491 vs baseline 0.498/0.503
- C4-cond+base 20 LONDON: C_round2_V2c LONDON: WF 0.534 hold 0.570 vs baseline 0.592/0.663
- C4-cond+base 20 NY: C_round2_V2c NY: WF 0.556 hold 0.567 vs baseline 0.723/0.832
- C4-cond+base 30 POOLED: C_round2_V2c ALL: WF 0.533 hold 0.532 vs baseline 0.644/0.687
- C4-cond+base 30 ASIA: C_round2_V2c ASIA: WF 0.539 hold 0.556 vs baseline 0.524/0.514
- C4-cond+base 30 LONDON: C_round2_V2c LONDON: WF 0.547 hold 0.546 vs baseline 0.612/0.661
- C4-cond+base 30 NY: C_round2_V2c NY: WF 0.513 hold 0.505 vs baseline 0.716/0.804
- C4-cond+base 45 POOLED: C_round2_V2c ALL: WF 0.513 hold 0.536 vs baseline 0.624/0.674
- C4-cond+base 45 ASIA: C_round2_V2c ASIA: WF 0.488 hold 0.484 vs baseline 0.494/0.504
- C4-cond+base 45 LONDON: C_round2_V2c LONDON: WF 0.535 hold 0.595 vs baseline 0.603/0.642
- C4-cond+base 45 NY: C_round2_V2c NY: WF 0.541 hold 0.594 vs baseline 0.676/0.790
- C4-cond+base 5 POOLED: C_round2_V2c ALL: WF 0.531 hold 0.518 vs baseline 0.606/0.632
- C4-cond+base 5 ASIA: C_round2_V2c ASIA: WF 0.526 hold 0.543 vs baseline 0.541/0.528
- C4-cond+base 5 LONDON: C_round2_V2c LONDON: WF 0.547 hold 0.541 vs baseline 0.568/0.595
- C4-cond+base 5 NY: C_round2_V2c NY: WF 0.547 hold 0.571 vs baseline 0.633/0.692
- C4-cond+base 60 POOLED: C_round2_V2c ALL: WF 0.514 hold 0.532 vs baseline 0.652/0.707
- C4-cond+base 60 ASIA: C_round2_V2c ASIA: WF 0.484 hold 0.502 vs baseline 0.498/0.527
- C4-cond+base 60 LONDON: C_round2_V2c LONDON: WF 0.538 hold 0.599 vs baseline 0.597/0.650
- C4-cond+base 60 NY: C_round2_V2c NY: WF 0.567 hold 0.626 vs baseline 0.780/0.873
- C4-cond+base 0 POOLED: C_round3_V2c ALL: WF 0.490 hold 0.481 vs baseline 0.626/0.648
- C4-cond+base 0 ASIA: C_round3_V2c ASIA: WF 0.510 hold 0.553 vs baseline 0.567/0.529
- C4-cond+base 0 LONDON: C_round3_V2c LONDON: WF 0.491 hold 0.478 vs baseline 0.602/0.658
- C4-cond+base 0 NY: C_round3_V2c NY: WF 0.489 hold 0.476 vs baseline 0.638/0.669
- C4-cond+base 10 POOLED: C_round3_V2c ALL: WF 0.527 hold 0.518 vs baseline 0.650/0.682
- C4-cond+base 10 ASIA: C_round3_V2c ASIA: WF 0.510 hold 0.508 vs baseline 0.569/0.525
- C4-cond+base 10 LONDON: C_round3_V2c LONDON: WF 0.540 hold 0.559 vs baseline 0.624/0.682
- C4-cond+base 10 NY: C_round3_V2c NY: WF 0.565 hold 0.575 vs baseline 0.697/0.773
- C4-cond+base 15 POOLED: C_round3_V2c ALL: WF 0.531 hold 0.523 vs baseline 0.665/0.703
- C4-cond+base 15 ASIA: C_round3_V2c ASIA: WF 0.520 hold 0.505 vs baseline 0.576/0.570
- C4-cond+base 15 LONDON: C_round3_V2c LONDON: WF 0.530 hold 0.534 vs baseline 0.629/0.668
- C4-cond+base 15 NY: C_round3_V2c NY: WF 0.571 hold 0.602 vs baseline 0.726/0.802
- C4-cond+base 20 POOLED: C_round3_V2c ALL: WF 0.517 hold 0.508 vs baseline 0.628/0.686
- C4-cond+base 20 ASIA: C_round3_V2c ASIA: WF 0.505 hold 0.519 vs baseline 0.498/0.503
- C4-cond+base 20 LONDON: C_round3_V2c LONDON: WF 0.542 hold 0.534 vs baseline 0.592/0.663
- C4-cond+base 20 NY: C_round3_V2c NY: WF 0.524 hold 0.523 vs baseline 0.723/0.832
- C4-cond+base 30 POOLED: C_round3_V2c ALL: WF 0.526 hold 0.518 vs baseline 0.644/0.687
- C4-cond+base 30 ASIA: C_round3_V2c ASIA: WF 0.521 hold 0.518 vs baseline 0.524/0.514
- C4-cond+base 30 LONDON: C_round3_V2c LONDON: WF 0.542 hold 0.546 vs baseline 0.612/0.661
- C4-cond+base 30 NY: C_round3_V2c NY: WF 0.524 hold 0.537 vs baseline 0.716/0.804
- C4-cond+base 45 POOLED: C_round3_V2c ALL: WF 0.512 hold 0.534 vs baseline 0.624/0.674
- C4-cond+base 45 ASIA: C_round3_V2c ASIA: WF 0.493 hold 0.505 vs baseline 0.494/0.504
- C4-cond+base 45 LONDON: C_round3_V2c LONDON: WF 0.546 hold 0.596 vs baseline 0.603/0.642
- C4-cond+base 45 NY: C_round3_V2c NY: WF 0.524 hold 0.560 vs baseline 0.676/0.790
- C4-cond+base 5 POOLED: C_round3_V2c ALL: WF 0.517 hold 0.507 vs baseline 0.606/0.632
- C4-cond+base 5 ASIA: C_round3_V2c ASIA: WF 0.517 hold 0.529 vs baseline 0.541/0.528
- C4-cond+base 5 LONDON: C_round3_V2c LONDON: WF 0.523 hold 0.504 vs baseline 0.568/0.595
- C4-cond+base 5 NY: C_round3_V2c NY: WF 0.540 hold 0.581 vs baseline 0.633/0.692
- C4-cond+base 60 POOLED: C_round3_V2c ALL: WF 0.508 hold 0.521 vs baseline 0.652/0.707
- C4-cond+base 60 ASIA: C_round3_V2c ASIA: WF 0.459 hold 0.477 vs baseline 0.498/0.527
- C4-cond+base 60 LONDON: C_round3_V2c LONDON: WF 0.537 hold 0.572 vs baseline 0.597/0.650
- C4-cond+base 60 NY: C_round3_V2c NY: WF 0.575 hold 0.637 vs baseline 0.780/0.873
- C4-cond+base 0 POOLED: C_round3_H2c ALL: WF 0.499 hold 0.463 vs baseline 0.626/0.648
- C4-cond+base 0 ASIA: C_round3_H2c ASIA: WF 0.515 hold 0.528 vs baseline 0.567/0.529
- C4-cond+base 0 LONDON: C_round3_H2c LONDON: WF 0.490 hold 0.477 vs baseline 0.602/0.658
- C4-cond+base 0 NY: C_round3_H2c NY: WF 0.519 hold 0.471 vs baseline 0.638/0.669
- C4-cond+base 10 POOLED: C_round3_H2c ALL: WF 0.516 hold 0.507 vs baseline 0.650/0.682
- C4-cond+base 10 ASIA: C_round3_H2c ASIA: WF 0.513 hold 0.499 vs baseline 0.569/0.525
- C4-cond+base 10 LONDON: C_round3_H2c LONDON: WF 0.524 hold 0.557 vs baseline 0.624/0.682
- C4-cond+base 10 NY: C_round3_H2c NY: WF 0.533 hold 0.530 vs baseline 0.697/0.773
- C4-cond+base 15 POOLED: C_round3_H2c ALL: WF 0.534 hold 0.530 vs baseline 0.665/0.703
- C4-cond+base 15 ASIA: C_round3_H2c ASIA: WF 0.515 hold 0.487 vs baseline 0.576/0.570
- C4-cond+base 15 LONDON: C_round3_H2c LONDON: WF 0.539 hold 0.575 vs baseline 0.629/0.668
- C4-cond+base 15 NY: C_round3_H2c NY: WF 0.568 hold 0.581 vs baseline 0.726/0.802
- C4-cond+base 20 POOLED: C_round3_H2c ALL: WF 0.526 hold 0.516 vs baseline 0.628/0.686
- C4-cond+base 20 ASIA: C_round3_H2c ASIA: WF 0.509 hold 0.490 vs baseline 0.498/0.503
- C4-cond+base 20 LONDON: C_round3_H2c LONDON: WF 0.544 hold 0.572 vs baseline 0.592/0.663
- C4-cond+base 20 NY: C_round3_H2c NY: WF 0.557 hold 0.586 vs baseline 0.723/0.832
- C4-cond+base 30 POOLED: C_round3_H2c ALL: WF 0.517 hold 0.519 vs baseline 0.644/0.687
- C4-cond+base 30 ASIA: C_round3_H2c ASIA: WF 0.517 hold 0.514 vs baseline 0.524/0.514
- C4-cond+base 30 LONDON: C_round3_H2c LONDON: WF 0.529 hold 0.559 vs baseline 0.612/0.661
- C4-cond+base 30 NY: C_round3_H2c NY: WF 0.505 hold 0.512 vs baseline 0.716/0.804
- C4-cond+base 45 POOLED: C_round3_H2c ALL: WF 0.514 hold 0.537 vs baseline 0.624/0.674
- C4-cond+base 45 ASIA: C_round3_H2c ASIA: WF 0.493 hold 0.496 vs baseline 0.494/0.504
- C4-cond+base 45 LONDON: C_round3_H2c LONDON: WF 0.536 hold 0.586 vs baseline 0.603/0.642
- C4-cond+base 45 NY: C_round3_H2c NY: WF 0.543 hold 0.607 vs baseline 0.676/0.790
- C4-cond+base 5 POOLED: C_round3_H2c ALL: WF 0.517 hold 0.510 vs baseline 0.606/0.632
- C4-cond+base 5 ASIA: C_round3_H2c ASIA: WF 0.512 hold 0.520 vs baseline 0.541/0.528
- C4-cond+base 5 LONDON: C_round3_H2c LONDON: WF 0.526 hold 0.534 vs baseline 0.568/0.595
- C4-cond+base 5 NY: C_round3_H2c NY: WF 0.528 hold 0.546 vs baseline 0.633/0.692
- C4-cond+base 60 POOLED: C_round3_H2c ALL: WF 0.512 hold 0.515 vs baseline 0.652/0.707
- C4-cond+base 60 ASIA: C_round3_H2c ASIA: WF 0.477 hold 0.476 vs baseline 0.498/0.527
- C4-cond+base 60 LONDON: C_round3_H2c LONDON: WF 0.544 hold 0.594 vs baseline 0.597/0.650
- C4-cond+base 60 NY: C_round3_H2c NY: WF 0.557 hold 0.599 vs baseline 0.780/0.873
