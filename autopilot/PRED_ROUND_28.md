# PRED ROUND 28 - block C round 1 - C1-gex (options dealer gamma, on-disk daily OI)

Best HOLDOUT F-R AUC: +15 POOLED 0.553 [0.51,0.60] | ASIA 0.534 [0.48,0.59] | LONDON 0.550 [0.48,0.61] | NY 0.546 [0.45,0.64]
Best HOLDOUT F-R AUC: +30 POOLED 0.542 [0.49,0.59] | ASIA 0.540 [0.48,0.60] | LONDON 0.594 [0.52,0.66] | NY 0.552 [0.43,0.67]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 83734d249f8f8597b722d592b0d597480ee9c1e19b4322c976d4fd5d1bc900e0 ; trials added 3500 ; truncation audit {'decisions': 360, 'checks': 80811, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'C1/C2 session features, 4 seeds x 90 decisions, bars>=cut randomised and option file column groups with last record >= cut-300s shuffled'} ; holdout scored True ; feature store ['l2vast/pred/store/C1_gex.parquet', 'l2vast/pred/store/C1_gex_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C1-gex+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.531 [0.45,0.60] | 0.614 [0.51,0.71] | - | - | 0.876 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.554 [0.50,0.61] | 0.594 [0.52,0.66] | - | - | 0.591 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.559 [0.51,0.61] | 0.577 [0.51,0.64] | - | - | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.502 [0.44,0.57] | 0.573 [0.49,0.66] | - | - | 0.629 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | pre | NY | lite-stack (logit2,gbt3,rf) | 0.486 [0.43,0.54] | 0.572 [0.48,0.67] | - | - | 0.590 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.529 [0.47,0.58] | 0.564 [0.49,0.63] | - | - | 0.593 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.518 [0.45,0.58] | 0.562 [0.46,0.67] | - | - | 0.825 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.599 [0.54,0.65] | 0.561 [0.49,0.63] | - | - | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.533 [0.48,0.59] | 0.561 [0.48,0.64] | - | - | 0.597 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.539 [0.51,0.57] | 0.557 [0.51,0.60] | - | - | 0.505 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.500 [0.45,0.55] | 0.555 [0.47,0.64] | - | - | 0.666 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.546 [0.52,0.58] | 0.553 [0.51,0.60] | - | - | 0.533 | - | 525 | -13790 | - | 2/5 | stack | locked label (reference only) |
| C1-gex-only | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.533 [0.48,0.58] | 0.553 [0.48,0.62] | - | - | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.478 [0.41,0.55] | 0.553 [0.44,0.67] | - | - | 0.790 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.541 [0.49,0.60] | 0.552 [0.48,0.62] | - | - | 0.579 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.482 [0.41,0.56] | 0.552 [0.43,0.67] | - | - | 0.800 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.523 [0.47,0.57] | 0.550 [0.48,0.61] | - | - | 0.540 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.524 [0.46,0.59] | 0.549 [0.43,0.65] | - | - | 0.636 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.518 [0.47,0.56] | 0.547 [0.47,0.63] | - | - | 0.545 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.521 [0.49,0.55] | 0.546 [0.50,0.59] | - | - | 0.538 | - | 801 | -31256 | - | 2/5 | stack | locked label (reference only) |
| C1-gex+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.527 [0.46,0.59] | 0.546 [0.45,0.64] | - | - | 0.581 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.527 [0.49,0.56] | 0.543 [0.50,0.58] | - | - | 0.523 | - | 1768 | 0 | - | 3/5 | stack | locked label (reference only) |
| C1-gex+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.507 [0.48,0.54] | 0.543 [0.49,0.59] | - | - | 0.484 | - | 247 | 32006 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.48,0.54] | 0.542 [0.49,0.59] | - | - | 0.686 | - | 1208 | 12325 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.512 [0.45,0.58] | 0.541 [0.45,0.63] | - | - | 0.522 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.553 [0.50,0.61] | 0.540 [0.45,0.63] | - | - | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.520 [0.45,0.58] | 0.540 [0.43,0.64] | - | - | 0.596 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.534 [0.49,0.58] | 0.540 [0.48,0.60] | - | - | 0.522 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.552 [0.50,0.61] | 0.539 [0.46,0.62] | - | - | 0.565 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.490 [0.42,0.56] | 0.538 [0.45,0.63] | - | - | 0.760 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.490 [0.43,0.56] | 0.537 [0.45,0.63] | - | - | 0.604 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.576 [0.53,0.62] | 0.534 [0.47,0.60] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.543 [0.50,0.59] | 0.534 [0.48,0.59] | - | - | 0.546 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.550 [0.51,0.59] | 0.533 [0.47,0.60] | - | - | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.496 [0.45,0.55] | 0.531 [0.45,0.61] | - | - | 0.662 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.517 [0.47,0.56] | 0.531 [0.47,0.60] | - | - | 0.512 | - | 202 | -31256 | - | 2/5 | stack | locked label (reference only) |
| C1-gex+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.511 [0.47,0.55] | 0.531 [0.47,0.59] | - | - | 0.531 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.539 [0.49,0.59] | 0.530 [0.47,0.60] | - | - | 0.523 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.538 [0.51,0.57] | 0.529 [0.49,0.58] | - | - | 0.501 | - | 210 | 7196 | - | 1/5 | stack | locked label (reference only) |
| C1-gex-only | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.545 [0.50,0.60] | 0.528 [0.46,0.59] | - | - | 0.533 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.563 [0.51,0.62] | 0.528 [0.46,0.60] | - | - | 0.504 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.519 [0.49,0.55] | 0.525 [0.48,0.57] | - | - | 0.506 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.494 [0.46,0.53] | 0.524 [0.48,0.57] | - | - | 0.697 | - | 102 | 15313 | - | 1/5 | stack | locked label (reference only) |
| C1-gex-only | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.498 [0.45,0.55] | 0.523 [0.45,0.60] | - | - | 0.532 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.500 [0.47,0.53] | 0.523 [0.48,0.57] | - | - | 0.669 | - | 1166 | 0 | - | 1/5 | stack | locked label (reference only) |
| C1-gex-only | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.490 [0.42,0.56] | 0.523 [0.41,0.63] | - | - | 0.583 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.493 [0.44,0.55] | 0.523 [0.44,0.61] | - | - | 0.638 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.513 [0.47,0.55] | 0.523 [0.46,0.59] | - | - | 0.519 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.495 [0.43,0.57] | 0.522 [0.41,0.64] | - | - | 0.591 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.534 [0.50,0.57] | 0.520 [0.47,0.57] | - | - | 0.625 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.490 [0.46,0.52] | 0.520 [0.47,0.57] | - | - | 0.701 | - | 143 | 0 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.526 [0.48,0.57] | 0.519 [0.46,0.58] | - | - | 0.510 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.478 [0.41,0.54] | 0.518 [0.44,0.61] | - | - | 0.792 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.530 [0.48,0.58] | 0.518 [0.46,0.58] | - | - | 0.517 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.476 [0.41,0.54] | 0.517 [0.43,0.60] | - | - | 0.694 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.519 [0.48,0.56] | 0.517 [0.45,0.58] | - | - | 0.518 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex-only | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.539 [0.51,0.57] | 0.516 [0.47,0.56] | - | - | 0.611 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.495 [0.46,0.53] | 0.516 [0.47,0.56] | - | - | 0.676 | - | 802 | 45485 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.548 [0.50,0.60] | 0.516 [0.43,0.60] | - | - | 0.556 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.509 [0.46,0.55] | 0.515 [0.45,0.58] | - | - | 0.483 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.506 [0.46,0.55] | 0.514 [0.43,0.60] | - | - | 0.654 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.49,0.56] | 0.514 [0.45,0.58] | - | - | 0.498 | - | 223 | -7688 | - | 2/5 | stack | locked label (reference only) |
| C1-gex-only | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.524 [0.45,0.59] | 0.514 [0.42,0.61] | - | - | 0.605 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.492 [0.46,0.52] | 0.514 [0.47,0.56] | - | - | 0.679 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex-only | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.527 [0.50,0.56] | 0.513 [0.46,0.56] | - | - | 0.601 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.493 [0.45,0.53] | 0.509 [0.45,0.57] | - | - | 0.506 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.538 [0.50,0.58] | 0.509 [0.44,0.58] | - | - | 0.503 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.515 [0.47,0.56] | 0.507 [0.45,0.57] | - | - | 0.489 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.513 [0.46,0.56] | 0.506 [0.43,0.58] | - | - | 0.490 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.48,0.53] | 0.506 [0.47,0.55] | - | - | 0.516 | - | 588 | -14374 | - | 2/5 | stack | locked label (reference only) |
| C1-gex+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.517 [0.44,0.59] | 0.503 [0.40,0.61] | - | - | 0.658 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.484 [0.44,0.53] | 0.502 [0.43,0.58] | - | - | 0.652 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.57] | 0.502 [0.44,0.56] | - | - | 0.480 | - | 166 | 7196 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.536 [0.49,0.59] | 0.501 [0.44,0.57] | - | - | 0.541 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.526 [0.49,0.56] | 0.500 [0.43,0.57] | - | - | 0.490 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex-only | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.512 [0.49,0.54] | 0.500 [0.46,0.54] | - | - | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.510 [0.45,0.57] | 0.497 [0.40,0.61] | - | - | 0.543 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.457 [0.41,0.51] | 0.497 [0.42,0.58] | - | - | 0.672 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.510 [0.48,0.54] | 0.496 [0.45,0.54] | - | - | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.508 [0.46,0.55] | 0.494 [0.44,0.56] | - | - | 0.493 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.503 [0.47,0.53] | 0.491 [0.45,0.53] | - | - | 0.629 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.493 [0.47,0.52] | 0.491 [0.45,0.53] | - | - | 0.652 | - | -1627 | -104213 | - | 1/5 | stack | locked label (reference only) |
| C1-gex+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.483 [0.45,0.51] | 0.490 [0.45,0.53] | - | - | 0.616 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.533 [0.49,0.58] | 0.484 [0.42,0.55] | - | - | 0.487 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.504 [0.43,0.58] | 0.481 [0.38,0.59] | - | - | 0.648 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.493 [0.46,0.53] | 0.480 [0.44,0.52] | - | - | 0.576 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.499 [0.44,0.55] | 0.478 [0.40,0.56] | - | - | 0.563 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.512 [0.47,0.55] | 0.472 [0.40,0.54] | - | - | 0.478 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.510 [0.48,0.54] | 0.471 [0.43,0.51] | - | - | 0.568 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.477 [0.43,0.53] | 0.469 [0.39,0.55] | - | - | 0.480 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.466 [0.40,0.53] | 0.466 [0.38,0.56] | - | - | 0.693 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.495 [0.47,0.52] | 0.466 [0.42,0.50] | - | - | 0.555 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.521 [0.48,0.56] | 0.462 [0.41,0.51] | - | - | 0.453 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.463 [0.44,0.49] | 0.460 [0.42,0.51] | - | - | 0.628 | - | 0 | 0 | - | 0/5 | stack | locked label (reference only) |
| C1-gex+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.468 [0.40,0.54] | 0.459 [0.37,0.55] | - | - | 0.571 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.510 [0.47,0.55] | 0.457 [0.39,0.52] | - | - | 0.452 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex-only | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.511 [0.47,0.55] | 0.457 [0.40,0.51] | - | - | 0.453 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.490 [0.41,0.56] | 0.455 [0.35,0.56] | - | - | 0.537 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex-only | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.497 [0.46,0.54] | 0.452 [0.40,0.51] | - | - | 0.453 | - | - | - | - | - |  | locked label (reference only) |
| C1-gex+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.434 [0.38,0.49] | 0.447 [0.36,0.53] | - | - | 0.643 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.450 [0.38,0.52] | 0.443 [0.34,0.55] | - | - | 0.548 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.443 [0.39,0.49] | 0.433 [0.36,0.52] | - | - | 0.594 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.441 [0.37,0.51] | 0.427 [0.30,0.55] | - | - | 0.532 | - | - | - | - | - | stack | locked label (reference only) |
| C1-gex+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.473 [0.41,0.54] | 0.393 [0.30,0.49] | - | - | 0.729 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- C1-gex-only 0 POOLED: C_round1_V1 ALL: WF 0.544 hold 0.581 vs baseline 0.626/0.648
- C1-gex-only 0 ASIA: C_round1_V1 ASIA: WF 0.520 hold 0.487 vs baseline 0.567/0.529
- C1-gex-only 0 LONDON: C_round1_V1 LONDON: WF 0.538 hold 0.540 vs baseline 0.602/0.658
- C1-gex-only 0 NY: C_round1_V1 NY: WF 0.516 hold 0.590 vs baseline 0.638/0.669
- C1-gex-only 10 POOLED: C_round1_V1 ALL: WF 0.548 hold 0.555 vs baseline 0.650/0.682
- C1-gex-only 10 ASIA: C_round1_V1 ASIA: WF 0.508 hold 0.453 vs baseline 0.569/0.525
- C1-gex-only 10 LONDON: C_round1_V1 LONDON: WF 0.511 hold 0.490 vs baseline 0.624/0.682
- C1-gex-only 10 NY: C_round1_V1 NY: WF 0.552 hold 0.604 vs baseline 0.697/0.773
- C1-gex-only 15 POOLED: C_round1_V1 ALL: WF 0.549 hold 0.576 vs baseline 0.665/0.703
- C1-gex-only 15 ASIA: C_round1_V1 ASIA: WF 0.489 hold 0.453 vs baseline 0.576/0.570
- C1-gex-only 15 LONDON: C_round1_V1 LONDON: WF 0.524 hold 0.532 vs baseline 0.629/0.668
- C1-gex-only 15 NY: C_round1_V1 NY: WF 0.559 hold 0.596 vs baseline 0.726/0.802
- C1-gex-only 20 POOLED: C_round1_V1 ALL: WF 0.558 hold 0.581 vs baseline 0.628/0.686
- C1-gex-only 20 ASIA: C_round1_V1 ASIA: WF 0.501 hold 0.452 vs baseline 0.498/0.503
- C1-gex-only 20 LONDON: C_round1_V1 LONDON: WF 0.530 hold 0.552 vs baseline 0.592/0.663
- C1-gex-only 20 NY: C_round1_V1 NY: WF 0.564 hold 0.636 vs baseline 0.723/0.832
- C1-gex-only 30 POOLED: C_round1_V1 ALL: WF 0.563 hold 0.601 vs baseline 0.644/0.687
- C1-gex-only 30 ASIA: C_round1_V1 ASIA: WF 0.505 hold 0.478 vs baseline 0.524/0.514
- C1-gex-only 30 LONDON: C_round1_V1 LONDON: WF 0.560 hold 0.591 vs baseline 0.612/0.661
- C1-gex-only 30 NY: C_round1_V1 NY: WF 0.570 hold 0.605 vs baseline 0.716/0.804
- C1-gex-only 45 POOLED: C_round1_V1 ALL: WF 0.580 hold 0.611 vs baseline 0.624/0.674
- C1-gex-only 45 ASIA: C_round1_V1 ASIA: WF 0.517 hold 0.517 vs baseline 0.494/0.504
- C1-gex-only 45 LONDON: C_round1_V1 LONDON: WF 0.566 hold 0.540 vs baseline 0.603/0.642
- C1-gex-only 45 NY: C_round1_V1 NY: WF 0.547 hold 0.583 vs baseline 0.676/0.790
- C1-gex-only 5 POOLED: C_round1_V1 ALL: WF 0.551 hold 0.568 vs baseline 0.606/0.632
- C1-gex-only 5 ASIA: C_round1_V1 ASIA: WF 0.496 hold 0.453 vs baseline 0.541/0.528
- C1-gex-only 5 LONDON: C_round1_V1 LONDON: WF 0.538 hold 0.504 vs baseline 0.568/0.595
- C1-gex-only 5 NY: C_round1_V1 NY: WF 0.553 hold 0.629 vs baseline 0.633/0.692
- C1-gex-only 60 POOLED: C_round1_V1 ALL: WF 0.578 hold 0.625 vs baseline 0.652/0.707
- C1-gex-only 60 ASIA: C_round1_V1 ASIA: WF 0.536 hold 0.533 vs baseline 0.498/0.527
- C1-gex-only 60 LONDON: C_round1_V1 LONDON: WF 0.540 hold 0.530 vs baseline 0.597/0.650
- C1-gex-only 60 NY: C_round1_V1 NY: WF 0.561 hold 0.591 vs baseline 0.780/0.873
- C1-gex+base 0 POOLED: C_round1_V2 ALL: WF 0.623 hold 0.652 vs baseline 0.626/0.648
- C1-gex+base 0 ASIA: C_round1_V2 ASIA: WF 0.560 hold 0.530 vs baseline 0.567/0.529
- C1-gex+base 0 LONDON: C_round1_V2 LONDON: WF 0.595 hold 0.654 vs baseline 0.602/0.658
- C1-gex+base 0 NY: C_round1_V2 NY: WF 0.648 hold 0.693 vs baseline 0.638/0.669
- C1-gex+base 10 POOLED: C_round1_V2 ALL: WF 0.643 hold 0.669 vs baseline 0.650/0.682
- C1-gex+base 10 ASIA: C_round1_V2 ASIA: WF 0.561 hold 0.523 vs baseline 0.569/0.525
- C1-gex+base 10 LONDON: C_round1_V2 LONDON: WF 0.620 hold 0.662 vs baseline 0.624/0.682
- C1-gex+base 10 NY: C_round1_V2 NY: WF 0.685 hold 0.760 vs baseline 0.697/0.773
- C1-gex+base 15 POOLED: C_round1_V2 ALL: WF 0.658 hold 0.697 vs baseline 0.665/0.703
- C1-gex+base 15 ASIA: C_round1_V2 ASIA: WF 0.571 hold 0.546 vs baseline 0.576/0.570
- C1-gex+base 15 LONDON: C_round1_V2 LONDON: WF 0.622 hold 0.672 vs baseline 0.629/0.668
- C1-gex+base 15 NY: C_round1_V2 NY: WF 0.712 hold 0.792 vs baseline 0.726/0.802
- C1-gex+base 20 POOLED: C_round1_V2 ALL: WF 0.630 hold 0.679 vs baseline 0.628/0.686
- C1-gex+base 20 ASIA: C_round1_V2 ASIA: WF 0.501 hold 0.489 vs baseline 0.498/0.503
- C1-gex+base 20 LONDON: C_round1_V2 LONDON: WF 0.601 hold 0.652 vs baseline 0.592/0.663
- C1-gex+base 20 NY: C_round1_V2 NY: WF 0.716 hold 0.825 vs baseline 0.723/0.832
- C1-gex+base 30 POOLED: C_round1_V2 ALL: WF 0.636 hold 0.686 vs baseline 0.644/0.687
- C1-gex+base 30 ASIA: C_round1_V2 ASIA: WF 0.522 hold 0.522 vs baseline 0.524/0.514
- C1-gex+base 30 LONDON: C_round1_V2 LONDON: WF 0.605 hold 0.666 vs baseline 0.612/0.661
- C1-gex+base 30 NY: C_round1_V2 NY: WF 0.701 hold 0.800 vs baseline 0.716/0.804
- C1-gex+base 45 POOLED: C_round1_V2 ALL: WF 0.624 hold 0.676 vs baseline 0.624/0.674
- C1-gex+base 45 ASIA: C_round1_V2 ASIA: WF 0.511 hold 0.519 vs baseline 0.494/0.504
- C1-gex+base 45 LONDON: C_round1_V2 LONDON: WF 0.597 hold 0.638 vs baseline 0.603/0.642
- C1-gex+base 45 NY: C_round1_V2 NY: WF 0.668 hold 0.790 vs baseline 0.676/0.790
- C1-gex+base 5 POOLED: C_round1_V2 ALL: WF 0.601 hold 0.628 vs baseline 0.606/0.632
- C1-gex+base 5 ASIA: C_round1_V2 ASIA: WF 0.534 hold 0.510 vs baseline 0.541/0.528
- C1-gex+base 5 LONDON: C_round1_V2 LONDON: WF 0.563 hold 0.594 vs baseline 0.568/0.595
- C1-gex+base 5 NY: C_round1_V2 NY: WF 0.631 hold 0.694 vs baseline 0.633/0.692
- C1-gex+base 60 POOLED: C_round1_V2 ALL: WF 0.644 hold 0.701 vs baseline 0.652/0.707
- C1-gex+base 60 ASIA: C_round1_V2 ASIA: WF 0.487 hold 0.506 vs baseline 0.498/0.527
- C1-gex+base 60 LONDON: C_round1_V2 LONDON: WF 0.589 hold 0.643 vs baseline 0.597/0.650
- C1-gex+base 60 NY: C_round1_V2 NY: WF 0.769 hold 0.876 vs baseline 0.780/0.873
- C1-gex+base 15 POOLED: C_round1_V3 ALL: WF 0.598 hold 0.616 vs baseline nan/nan
- C1-gex+base 15 ASIA: C_round1_V3 ASIA: WF 0.488 hold 0.493 vs baseline nan/nan
- C1-gex+base 15 LONDON: C_round1_V3 LONDON: WF 0.528 hold 0.540 vs baseline nan/nan
- C1-gex+base 15 NY: C_round1_V3 NY: WF 0.630 hold 0.658 vs baseline nan/nan
- C1-gex+base 30 POOLED: C_round1_V3 ALL: WF 0.629 hold 0.629 vs baseline nan/nan
- C1-gex+base 30 ASIA: C_round1_V3 ASIA: WF 0.563 hold 0.528 vs baseline nan/nan
- C1-gex+base 30 LONDON: C_round1_V3 LONDON: WF 0.539 hold 0.545 vs baseline nan/nan
- C1-gex+base 30 NY: C_round1_V3 NY: WF 0.675 hold 0.729 vs baseline nan/nan
- C1-gex+base 0 POOLED: C_round1_V2c ALL: WF 0.499 hold 0.484 vs baseline 0.626/0.648
- C1-gex+base 0 ASIA: C_round1_V2c ASIA: WF 0.505 hold 0.531 vs baseline 0.567/0.529
- C1-gex+base 0 LONDON: C_round1_V2c LONDON: WF 0.485 hold 0.480 vs baseline 0.602/0.658
- C1-gex+base 0 NY: C_round1_V2c NY: WF 0.532 hold 0.522 vs baseline 0.638/0.669
- C1-gex+base 10 POOLED: C_round1_V2c ALL: WF 0.527 hold 0.505 vs baseline 0.650/0.682
- C1-gex+base 10 ASIA: C_round1_V2c ASIA: WF 0.514 hold 0.490 vs baseline 0.569/0.525
- C1-gex+base 10 LONDON: C_round1_V2c LONDON: WF 0.551 hold 0.579 vs baseline 0.624/0.682
- C1-gex+base 10 NY: C_round1_V2c NY: WF 0.547 hold 0.543 vs baseline 0.697/0.773
- C1-gex+base 15 POOLED: C_round1_V2c ALL: WF 0.538 hold 0.533 vs baseline 0.665/0.703
- C1-gex+base 15 ASIA: C_round1_V2c ASIA: WF 0.522 hold 0.503 vs baseline 0.576/0.570
- C1-gex+base 15 LONDON: C_round1_V2c LONDON: WF 0.544 hold 0.565 vs baseline 0.629/0.668
- C1-gex+base 15 NY: C_round1_V2c NY: WF 0.569 hold 0.581 vs baseline 0.726/0.802
- C1-gex+base 20 POOLED: C_round1_V2c ALL: WF 0.524 hold 0.501 vs baseline 0.628/0.686
- C1-gex+base 20 ASIA: C_round1_V2c ASIA: WF 0.501 hold 0.480 vs baseline 0.498/0.503
- C1-gex+base 20 LONDON: C_round1_V2c LONDON: WF 0.558 hold 0.556 vs baseline 0.592/0.663
- C1-gex+base 20 NY: C_round1_V2c NY: WF 0.538 hold 0.537 vs baseline 0.723/0.832
- C1-gex+base 30 POOLED: C_round1_V2c ALL: WF 0.516 hold 0.516 vs baseline 0.644/0.687
- C1-gex+base 30 ASIA: C_round1_V2c ASIA: WF 0.510 hold 0.498 vs baseline 0.524/0.514
- C1-gex+base 30 LONDON: C_round1_V2c LONDON: WF 0.532 hold 0.563 vs baseline 0.612/0.661
- C1-gex+base 30 NY: C_round1_V2c NY: WF 0.516 hold 0.532 vs baseline 0.716/0.804
- C1-gex+base 45 POOLED: C_round1_V2c ALL: WF 0.513 hold 0.538 vs baseline 0.624/0.674
- C1-gex+base 45 ASIA: C_round1_V2c ASIA: WF 0.501 hold 0.512 vs baseline 0.494/0.504
- C1-gex+base 45 LONDON: C_round1_V2c LONDON: WF 0.541 hold 0.597 vs baseline 0.603/0.642
- C1-gex+base 45 NY: C_round1_V2c NY: WF 0.525 hold 0.571 vs baseline 0.676/0.790
- C1-gex+base 5 POOLED: C_round1_V2c ALL: WF 0.521 hold 0.506 vs baseline 0.606/0.632
- C1-gex+base 5 ASIA: C_round1_V2c ASIA: WF 0.513 hold 0.518 vs baseline 0.541/0.528
- C1-gex+base 5 LONDON: C_round1_V2c LONDON: WF 0.544 hold 0.541 vs baseline 0.568/0.595
- C1-gex+base 5 NY: C_round1_V2c NY: WF 0.527 hold 0.548 vs baseline 0.633/0.692
- C1-gex+base 60 POOLED: C_round1_V2c ALL: WF 0.516 hold 0.523 vs baseline 0.652/0.707
- C1-gex+base 60 ASIA: C_round1_V2c ASIA: WF 0.469 hold 0.483 vs baseline 0.498/0.527
- C1-gex+base 60 LONDON: C_round1_V2c LONDON: WF 0.553 hold 0.593 vs baseline 0.597/0.650
- C1-gex+base 60 NY: C_round1_V2c NY: WF 0.582 hold 0.648 vs baseline 0.780/0.873
