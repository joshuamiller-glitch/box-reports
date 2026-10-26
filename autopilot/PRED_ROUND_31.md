# PRED ROUND 31 - block C round 3 - C3-stack (C1+C2 stacks, G)

Best HOLDOUT F-R AUC: +15 POOLED 0.543 [0.50,0.58] | ASIA 0.550 [0.50,0.61] | LONDON 0.543 [0.47,0.61] | NY 0.549 [0.46,0.63]
Best HOLDOUT F-R AUC: +30 POOLED 0.548 [0.50,0.60] | ASIA 0.553 [0.48,0.62] | LONDON 0.550 [0.46,0.64] | NY 0.574 [0.47,0.68]
Best G HOLDOUT AUC: 0.558 [0.48,0.63]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 0b4e405051aa260342c7960f5b80337ce844732ef600c3b780b12b8c912ed175 ; trials added 3500 ; truncation audit {'decisions': 360, 'checks': 80811, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'C1/C2 session features, 4 seeds x 90 decisions, bars>=cut randomised and option file column groups with last record >= cut-300s shuffled'} ; holdout scored True ; feature store ['l2vast/pred/store/C1_gex.parquet', 'l2vast/pred/store/C2_vol.parquet', 'l2vast/pred/store/C1_gex_sig.parquet', 'l2vast/pred/store/C1_hyp.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C3-stack+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.538 [0.46,0.61] | 0.626 [0.52,0.73] | - | - | 0.877 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.513 [0.44,0.59] | 0.591 [0.49,0.69] | - | - | 0.837 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.521 [0.45,0.60] | 0.586 [0.47,0.69] | - | - | 0.874 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.522 [0.45,0.58] | 0.582 [0.48,0.68] | - | - | 0.825 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.498 [0.43,0.57] | 0.574 [0.47,0.68] | - | - | 0.807 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.486 [0.42,0.56] | 0.560 [0.46,0.67] | - | - | 0.785 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | LONDON/ST | stack | 0.472 [0.42,0.52] | 0.558 [0.48,0.63] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.494 [0.43,0.56] | 0.553 [0.47,0.64] | - | - | 0.755 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.585 [0.54,0.63] | 0.553 [0.48,0.62] | - | - | 0.544 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.498 [0.43,0.57] | 0.552 [0.44,0.66] | - | - | 0.795 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | LONDON | stack | 0.474 [0.44,0.51] | 0.551 [0.51,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.504 [0.45,0.56] | 0.550 [0.46,0.64] | - | - | 0.666 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.545 [0.50,0.59] | 0.550 [0.50,0.61] | - | - | 0.562 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.497 [0.43,0.56] | 0.549 [0.46,0.63] | - | - | 0.789 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.540 [0.50,0.58] | 0.549 [0.49,0.60] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.494 [0.43,0.56] | 0.548 [0.46,0.64] | - | - | 0.773 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.509 [0.44,0.57] | 0.548 [0.46,0.63] | - | - | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.514 [0.48,0.55] | 0.548 [0.50,0.60] | - | - | 0.692 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.495 [0.44,0.55] | 0.547 [0.46,0.64] | - | - | 0.664 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.478 [0.40,0.56] | 0.546 [0.43,0.67] | - | - | 0.802 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.507 [0.48,0.54] | 0.543 [0.50,0.58] | - | - | 0.696 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.513 [0.46,0.56] | 0.543 [0.47,0.61] | - | - | 0.521 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | LONDON/HM | stack | 0.476 [0.44,0.52] | 0.543 [0.49,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.522 [0.48,0.57] | 0.541 [0.47,0.61] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.47,0.54] | 0.541 [0.49,0.59] | - | - | 0.686 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.546 [0.50,0.59] | 0.539 [0.49,0.60] | - | - | 0.540 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.542 [0.50,0.59] | 0.537 [0.48,0.59] | - | - | 0.523 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.531 [0.47,0.59] | 0.537 [0.46,0.61] | - | - | 0.551 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.500 [0.47,0.53] | 0.537 [0.49,0.58] | - | - | 0.709 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.519 [0.47,0.57] | 0.537 [0.45,0.62] | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.517 [0.47,0.56] | 0.537 [0.48,0.60] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.506 [0.46,0.55] | 0.537 [0.47,0.60] | - | - | 0.529 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.520 [0.46,0.57] | 0.536 [0.46,0.61] | - | - | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.490 [0.44,0.54] | 0.534 [0.46,0.62] | - | - | 0.680 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.546 [0.50,0.59] | 0.533 [0.47,0.60] | - | - | 0.521 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.496 [0.46,0.53] | 0.533 [0.49,0.58] | - | - | 0.708 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.48,0.53] | 0.533 [0.49,0.58] | - | - | 0.680 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.494 [0.44,0.55] | 0.531 [0.45,0.61] | - | - | 0.635 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.503 [0.47,0.53] | 0.530 [0.49,0.58] | - | - | 0.680 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.495 [0.45,0.55] | 0.530 [0.46,0.61] | - | - | 0.655 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.547 [0.50,0.59] | 0.530 [0.46,0.60] | - | - | 0.523 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.485 [0.44,0.54] | 0.530 [0.45,0.61] | - | - | 0.674 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | NY/ST | stack | 0.515 [0.46,0.57] | 0.529 [0.46,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.504 [0.43,0.56] | 0.529 [0.44,0.62] | - | - | 0.808 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.530 [0.49,0.57] | 0.528 [0.47,0.59] | - | - | 0.524 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.505 [0.48,0.54] | 0.528 [0.48,0.57] | - | - | 0.703 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.539 [0.49,0.59] | 0.527 [0.45,0.61] | - | - | 0.549 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.491 [0.46,0.52] | 0.526 [0.48,0.57] | - | - | 0.687 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.502 [0.47,0.53] | 0.525 [0.48,0.57] | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.524 [0.48,0.57] | 0.524 [0.47,0.59] | - | - | 0.513 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.526 [0.48,0.57] | 0.523 [0.46,0.58] | - | - | 0.504 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.504 [0.44,0.56] | 0.523 [0.44,0.60] | - | - | 0.537 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.550 [0.51,0.59] | 0.523 [0.46,0.59] | - | - | 0.520 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.494 [0.45,0.54] | 0.522 [0.45,0.58] | - | - | 0.520 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.498 [0.47,0.53] | 0.519 [0.47,0.57] | - | - | 0.678 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.522 [0.47,0.57] | 0.519 [0.44,0.59] | - | - | 0.524 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.498 [0.47,0.53] | 0.518 [0.47,0.57] | - | - | 0.678 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.541 [0.50,0.58] | 0.518 [0.46,0.58] | - | - | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.501 [0.45,0.55] | 0.515 [0.43,0.60] | - | - | 0.651 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | NY/ST | stack | 0.489 [0.44,0.55] | 0.514 [0.45,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | NY/HM | stack | 0.504 [0.45,0.56] | 0.514 [0.45,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | NY | stack | 0.496 [0.46,0.53] | 0.513 [0.46,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | ASIA | lite-stack (logit2,gbt3,rf) | 0.545 [0.51,0.59] | 0.512 [0.45,0.57] | - | - | 0.508 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.470 [0.42,0.52] | 0.510 [0.44,0.59] | - | - | 0.662 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.527 [0.46,0.59] | 0.510 [0.42,0.60] | - | - | 0.572 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +45 | LONDON | lite-stack (logit2,gbt3,rf) | 0.492 [0.43,0.55] | 0.508 [0.43,0.59] | - | - | 0.629 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | POOLED/ST | stack | 0.493 [0.47,0.52] | 0.507 [0.48,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.477 [0.41,0.54] | 0.506 [0.42,0.60] | - | - | 0.694 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.539 [0.49,0.59] | 0.506 [0.44,0.57] | - | - | 0.508 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.532 [0.48,0.59] | 0.505 [0.42,0.59] | - | - | 0.513 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.519 [0.47,0.56] | 0.504 [0.44,0.57] | - | - | 0.486 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | POOLED | stack | 0.487 [0.47,0.51] | 0.503 [0.48,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.521 [0.49,0.56] | 0.498 [0.46,0.55] | - | - | 0.596 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gc | sig | POOLED/HM | stack | 0.481 [0.46,0.50] | 0.498 [0.47,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +15 | NY | lite-stack (logit2,gbt3,rf) | 0.505 [0.43,0.57] | 0.498 [0.39,0.61] | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | ASIA/ST | stack | 0.476 [0.44,0.51] | 0.494 [0.45,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | ASIA/HM | stack | 0.497 [0.46,0.53] | 0.493 [0.44,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +15 | LONDON | lite-stack (logit2,gbt3,rf) | 0.474 [0.42,0.53] | 0.492 [0.41,0.57] | - | - | 0.673 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | ASIA | stack | 0.490 [0.46,0.52] | 0.492 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-Gc | sig | NY | stack | 0.486 [0.45,0.53] | 0.492 [0.44,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +30 | ASIA | lite-stack (logit2,gbt3,rf) | 0.512 [0.47,0.55] | 0.491 [0.43,0.55] | - | - | 0.487 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gs | sig | POOLED/ST | stack | 0.474 [0.45,0.50] | 0.489 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | ASIA/HM | stack | 0.505 [0.47,0.54] | 0.489 [0.43,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +5 | NY | lite-stack (logit2,gbt3,rf) | 0.460 [0.39,0.52] | 0.488 [0.40,0.58] | - | - | 0.692 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.491 [0.46,0.52] | 0.488 [0.45,0.53] | - | - | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | POOLED | stack | 0.482 [0.46,0.50] | 0.488 [0.46,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.504 [0.47,0.53] | 0.487 [0.44,0.53] | - | - | 0.627 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | POOLED/HM | stack | 0.492 [0.47,0.52] | 0.487 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.490 [0.46,0.51] | 0.487 [0.45,0.53] | - | - | 0.646 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | +20 | LONDON | lite-stack (logit2,gbt3,rf) | 0.477 [0.43,0.53] | 0.487 [0.42,0.56] | - | - | 0.642 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +10 | LONDON | lite-stack (logit2,gbt3,rf) | 0.510 [0.46,0.56] | 0.487 [0.42,0.56] | - | - | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gc | sig | ASIA | stack | 0.496 [0.46,0.53] | 0.485 [0.44,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.473 [0.41,0.53] | 0.485 [0.40,0.57] | - | - | 0.651 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.511 [0.48,0.54] | 0.485 [0.44,0.52] | - | - | 0.579 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +15 | POOLED | lite-stack (logit2,gbt3,rf) | 0.478 [0.45,0.51] | 0.484 [0.43,0.54] | - | - | 0.607 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +20 | ASIA | lite-stack (logit2,gbt3,rf) | 0.529 [0.49,0.57] | 0.482 [0.43,0.54] | - | - | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +30 | LONDON | lite-stack (logit2,gbt3,rf) | 0.513 [0.46,0.57] | 0.479 [0.41,0.55] | - | - | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +10 | ASIA | lite-stack (logit2,gbt3,rf) | 0.546 [0.50,0.59] | 0.479 [0.43,0.53] | - | - | 0.477 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +20 | POOLED | lite-stack (logit2,gbt3,rf) | 0.507 [0.48,0.54] | 0.478 [0.43,0.52] | - | - | 0.571 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +60 | POOLED | lite-stack (logit2,gbt3,rf) | 0.487 [0.46,0.52] | 0.477 [0.44,0.52] | - | - | 0.577 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gc | sig | ASIA/ST | stack | 0.495 [0.46,0.53] | 0.477 [0.44,0.52] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +5 | ASIA | lite-stack (logit2,gbt3,rf) | 0.541 [0.50,0.58] | 0.477 [0.42,0.54] | - | - | 0.473 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +45 | POOLED | lite-stack (logit2,gbt3,rf) | 0.516 [0.48,0.55] | 0.473 [0.43,0.52] | - | - | 0.577 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +30 | POOLED | lite-stack (logit2,gbt3,rf) | 0.501 [0.47,0.54] | 0.473 [0.43,0.52] | - | - | 0.563 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gs | sig | LONDON/HM | stack | 0.467 [0.43,0.51] | 0.472 [0.41,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +20 | NY | lite-stack (logit2,gbt3,rf) | 0.482 [0.41,0.54] | 0.472 [0.38,0.56] | - | - | 0.570 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +15 | ASIA | lite-stack (logit2,gbt3,rf) | 0.504 [0.46,0.55] | 0.470 [0.40,0.54] | - | - | 0.466 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | pre | POOLED | lite-stack (logit2,gbt3,rf) | 0.496 [0.47,0.52] | 0.467 [0.43,0.51] | - | - | 0.554 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | pre | LONDON | lite-stack (logit2,gbt3,rf) | 0.493 [0.44,0.55] | 0.467 [0.39,0.55] | - | - | 0.474 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +10 | NY | lite-stack (logit2,gbt3,rf) | 0.482 [0.41,0.55] | 0.466 [0.38,0.56] | - | - | 0.529 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +60 | LONDON | lite-stack (logit2,gbt3,rf) | 0.446 [0.39,0.51] | 0.464 [0.38,0.56] | - | - | 0.652 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | LONDON | stack | 0.463 [0.43,0.50] | 0.464 [0.43,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.460 [0.39,0.52] | 0.462 [0.38,0.55] | - | - | 0.679 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +10 | POOLED | lite-stack (logit2,gbt3,rf) | 0.509 [0.48,0.54] | 0.462 [0.42,0.50] | - | - | 0.565 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.465 [0.44,0.49] | 0.458 [0.41,0.51] | - | - | 0.629 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack+base | pre | NY | lite-stack (logit2,gbt3,rf) | 0.456 [0.39,0.51] | 0.458 [0.37,0.54] | - | - | 0.689 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.483 [0.42,0.55] | 0.457 [0.37,0.54] | - | - | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +5 | POOLED | lite-stack (logit2,gbt3,rf) | 0.467 [0.44,0.49] | 0.455 [0.41,0.50] | - | - | 0.627 | - | - | - | - | - | stack | locked label (reference only) |
| C3-Gs | sig | LONDON/ST | stack | 0.458 [0.41,0.51] | 0.455 [0.40,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +45 | ASIA | lite-stack (logit2,gbt3,rf) | 0.510 [0.47,0.55] | 0.453 [0.39,0.51] | - | - | 0.458 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | +60 | ASIA | lite-stack (logit2,gbt3,rf) | 0.493 [0.45,0.54] | 0.450 [0.39,0.51] | - | - | 0.456 | - | - | - | - | - |  | locked label (reference only) |
| C3-Gc | sig | NY/HM | stack | 0.452 [0.40,0.51] | 0.447 [0.37,0.53] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| C3-stack-only | pre | NY | lite-stack (logit2,gbt3,rf) | 0.468 [0.40,0.53] | 0.445 [0.35,0.54] | - | - | 0.482 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.451 [0.40,0.50] | 0.429 [0.36,0.51] | - | - | 0.598 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +45 | NY | lite-stack (logit2,gbt3,rf) | 0.484 [0.41,0.56] | 0.425 [0.31,0.54] | - | - | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +5 | LONDON | lite-stack (logit2,gbt3,rf) | 0.447 [0.40,0.50] | 0.423 [0.35,0.50] | - | - | 0.587 | - | - | - | - | - | stack | locked label (reference only) |
| C3-stack-only | +60 | NY | lite-stack (logit2,gbt3,rf) | 0.443 [0.37,0.52] | 0.419 [0.32,0.52] | - | - | 0.459 | - | - | - | - | - |  | locked label (reference only) |
| C3-stack+base | +30 | NY | lite-stack (logit2,gbt3,rf) | 0.466 [0.41,0.53] | 0.407 [0.31,0.51] | - | - | 0.731 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- C3-stack+base 0 POOLED: C_round3_V2 ALL: WF 0.623 hold 0.649 vs baseline 0.626/0.648
- C3-stack+base 0 ASIA: C_round3_V2 ASIA: WF 0.558 hold 0.508 vs baseline 0.567/0.529
- C3-stack+base 0 LONDON: C_round3_V2 LONDON: WF 0.603 hold 0.663 vs baseline 0.602/0.658
- C3-stack+base 0 NY: C_round3_V2 NY: WF 0.638 hold 0.689 vs baseline 0.638/0.669
- C3-stack+base 10 POOLED: C_round3_V2 ALL: WF 0.639 hold 0.663 vs baseline 0.650/0.682
- C3-stack+base 10 ASIA: C_round3_V2 ASIA: WF 0.564 hold 0.521 vs baseline 0.569/0.525
- C3-stack+base 10 LONDON: C_round3_V2 LONDON: WF 0.610 hold 0.655 vs baseline 0.624/0.682
- C3-stack+base 10 NY: C_round3_V2 NY: WF 0.680 hold 0.755 vs baseline 0.697/0.773
- C3-stack+base 15 POOLED: C_round3_V2 ALL: WF 0.659 hold 0.696 vs baseline 0.665/0.703
- C3-stack+base 15 ASIA: C_round3_V2 ASIA: WF 0.568 hold 0.540 vs baseline 0.576/0.570
- C3-stack+base 15 LONDON: C_round3_V2 LONDON: WF 0.631 hold 0.674 vs baseline 0.629/0.668
- C3-stack+base 15 NY: C_round3_V2 NY: WF 0.712 hold 0.789 vs baseline 0.726/0.802
- C3-stack+base 20 POOLED: C_round3_V2 ALL: WF 0.629 hold 0.678 vs baseline 0.628/0.686
- C3-stack+base 20 ASIA: C_round3_V2 ASIA: WF 0.505 hold 0.486 vs baseline 0.498/0.503
- C3-stack+base 20 LONDON: C_round3_V2 LONDON: WF 0.595 hold 0.642 vs baseline 0.592/0.663
- C3-stack+base 20 NY: C_round3_V2 NY: WF 0.713 hold 0.825 vs baseline 0.723/0.832
- C3-stack+base 30 POOLED: C_round3_V2 ALL: WF 0.639 hold 0.686 vs baseline 0.644/0.687
- C3-stack+base 30 ASIA: C_round3_V2 ASIA: WF 0.526 hold 0.528 vs baseline 0.524/0.514
- C3-stack+base 30 LONDON: C_round3_V2 LONDON: WF 0.608 hold 0.664 vs baseline 0.612/0.661
- C3-stack+base 30 NY: C_round3_V2 NY: WF 0.705 hold 0.802 vs baseline 0.716/0.804
- C3-stack+base 45 POOLED: C_round3_V2 ALL: WF 0.627 hold 0.680 vs baseline 0.624/0.674
- C3-stack+base 45 ASIA: C_round3_V2 ASIA: WF 0.517 hold 0.534 vs baseline 0.494/0.504
- C3-stack+base 45 LONDON: C_round3_V2 LONDON: WF 0.594 hold 0.635 vs baseline 0.603/0.642
- C3-stack+base 45 NY: C_round3_V2 NY: WF 0.672 hold 0.785 vs baseline 0.676/0.790
- C3-stack+base 5 POOLED: C_round3_V2 ALL: WF 0.601 hold 0.629 vs baseline 0.606/0.632
- C3-stack+base 5 ASIA: C_round3_V2 ASIA: WF 0.531 hold 0.513 vs baseline 0.541/0.528
- C3-stack+base 5 LONDON: C_round3_V2 LONDON: WF 0.564 hold 0.598 vs baseline 0.568/0.595
- C3-stack+base 5 NY: C_round3_V2 NY: WF 0.627 hold 0.692 vs baseline 0.633/0.692
- C3-stack+base 60 POOLED: C_round3_V2 ALL: WF 0.650 hold 0.709 vs baseline 0.652/0.707
- C3-stack+base 60 ASIA: C_round3_V2 ASIA: WF 0.496 hold 0.520 vs baseline 0.498/0.527
- C3-stack+base 60 LONDON: C_round3_V2 LONDON: WF 0.602 hold 0.651 vs baseline 0.597/0.650
- C3-stack+base 60 NY: C_round3_V2 NY: WF 0.768 hold 0.877 vs baseline 0.780/0.873
- C3-stack+base 15 POOLED: C_round3_V3 ALL: WF 0.596 hold 0.607 vs baseline nan/nan
- C3-stack+base 15 ASIA: C_round3_V3 ASIA: WF 0.484 hold 0.466 vs baseline nan/nan
- C3-stack+base 15 LONDON: C_round3_V3 LONDON: WF 0.523 hold 0.521 vs baseline nan/nan
- C3-stack+base 15 NY: C_round3_V3 NY: WF 0.622 hold 0.663 vs baseline nan/nan
- C3-stack+base 30 POOLED: C_round3_V3 ALL: WF 0.629 hold 0.627 vs baseline nan/nan
- C3-stack+base 30 ASIA: C_round3_V3 ASIA: WF 0.573 hold 0.544 vs baseline nan/nan
- C3-stack+base 30 LONDON: C_round3_V3 LONDON: WF 0.539 hold 0.524 vs baseline nan/nan
- C3-stack+base 30 NY: C_round3_V3 NY: WF 0.670 hold 0.731 vs baseline nan/nan
- C3-stack-only 0 POOLED: C_round3_H1 ALL: WF 0.550 hold 0.554 vs baseline 0.626/0.648
- C3-stack-only 0 ASIA: C_round3_H1 ASIA: WF 0.527 hold 0.516 vs baseline 0.567/0.529
- C3-stack-only 0 LONDON: C_round3_H1 LONDON: WF 0.501 hold 0.474 vs baseline 0.602/0.658
- C3-stack-only 0 NY: C_round3_H1 NY: WF 0.520 hold 0.482 vs baseline 0.638/0.669
- C3-stack-only 10 POOLED: C_round3_H1 ALL: WF 0.560 hold 0.565 vs baseline 0.650/0.682
- C3-stack-only 10 ASIA: C_round3_H1 ASIA: WF 0.533 hold 0.477 vs baseline 0.569/0.525
- C3-stack-only 10 LONDON: C_round3_H1 LONDON: WF 0.525 hold 0.524 vs baseline 0.624/0.682
- C3-stack-only 10 NY: C_round3_H1 NY: WF 0.538 hold 0.529 vs baseline 0.697/0.773
- C3-stack-only 15 POOLED: C_round3_H1 ALL: WF 0.572 hold 0.596 vs baseline 0.665/0.703
- C3-stack-only 15 ASIA: C_round3_H1 ASIA: WF 0.530 hold 0.508 vs baseline 0.576/0.570
- C3-stack-only 15 LONDON: C_round3_H1 LONDON: WF 0.542 hold 0.551 vs baseline 0.629/0.668
- C3-stack-only 15 NY: C_round3_H1 NY: WF 0.570 hold 0.572 vs baseline 0.726/0.802
- C3-stack-only 20 POOLED: C_round3_H1 ALL: WF 0.555 hold 0.571 vs baseline 0.628/0.686
- C3-stack-only 20 ASIA: C_round3_H1 ASIA: WF 0.517 hold 0.481 vs baseline 0.498/0.503
- C3-stack-only 20 LONDON: C_round3_H1 LONDON: WF 0.532 hold 0.513 vs baseline 0.592/0.663
- C3-stack-only 20 NY: C_round3_H1 NY: WF 0.546 hold 0.570 vs baseline 0.723/0.832
- C3-stack-only 30 POOLED: C_round3_H1 ALL: WF 0.542 hold 0.563 vs baseline 0.644/0.687
- C3-stack-only 30 ASIA: C_round3_H1 ASIA: WF 0.498 hold 0.487 vs baseline 0.524/0.514
- C3-stack-only 30 LONDON: C_round3_H1 LONDON: WF 0.519 hold 0.506 vs baseline 0.612/0.661
- C3-stack-only 30 NY: C_round3_H1 NY: WF 0.525 hold 0.506 vs baseline 0.716/0.804
- C3-stack-only 45 POOLED: C_round3_H1 ALL: WF 0.548 hold 0.577 vs baseline 0.624/0.674
- C3-stack-only 45 ASIA: C_round3_H1 ASIA: WF 0.491 hold 0.458 vs baseline 0.494/0.504
- C3-stack-only 45 LONDON: C_round3_H1 LONDON: WF 0.545 hold 0.549 vs baseline 0.603/0.642
- C3-stack-only 45 NY: C_round3_H1 NY: WF 0.536 hold 0.521 vs baseline 0.676/0.790
- C3-stack-only 5 POOLED: C_round3_H1 ALL: WF 0.566 hold 0.579 vs baseline 0.606/0.632
- C3-stack-only 5 ASIA: C_round3_H1 ASIA: WF 0.527 hold 0.473 vs baseline 0.541/0.528
- C3-stack-only 5 LONDON: C_round3_H1 LONDON: WF 0.524 hold 0.530 vs baseline 0.568/0.595
- C3-stack-only 5 NY: C_round3_H1 NY: WF 0.565 hold 0.586 vs baseline 0.633/0.692
- C3-stack-only 60 POOLED: C_round3_H1 ALL: WF 0.537 hold 0.577 vs baseline 0.652/0.707
- C3-stack-only 60 ASIA: C_round3_H1 ASIA: WF 0.485 hold 0.456 vs baseline 0.498/0.527
- C3-stack-only 60 LONDON: C_round3_H1 LONDON: WF 0.522 hold 0.537 vs baseline 0.597/0.650
- C3-stack-only 60 NY: C_round3_H1 NY: WF 0.497 hold 0.459 vs baseline 0.780/0.873
- C3-stack+base 0 POOLED: C_round3_H2 ALL: WF 0.623 hold 0.646 vs baseline 0.626/0.648
- C3-stack+base 0 ASIA: C_round3_H2 ASIA: WF 0.563 hold 0.520 vs baseline 0.567/0.529
- C3-stack+base 0 LONDON: C_round3_H2 LONDON: WF 0.596 hold 0.651 vs baseline 0.602/0.658
- C3-stack+base 0 NY: C_round3_H2 NY: WF 0.640 hold 0.679 vs baseline 0.638/0.669
- C3-stack+base 10 POOLED: C_round3_H2 ALL: WF 0.648 hold 0.680 vs baseline 0.650/0.682
- C3-stack+base 10 ASIA: C_round3_H2 ASIA: WF 0.567 hold 0.523 vs baseline 0.569/0.525
- C3-stack+base 10 LONDON: C_round3_H2 LONDON: WF 0.622 hold 0.680 vs baseline 0.624/0.682
- C3-stack+base 10 NY: C_round3_H2 NY: WF 0.695 hold 0.773 vs baseline 0.697/0.773
- C3-stack+base 15 POOLED: C_round3_H2 ALL: WF 0.664 hold 0.703 vs baseline 0.665/0.703
- C3-stack+base 15 ASIA: C_round3_H2 ASIA: WF 0.573 hold 0.562 vs baseline 0.576/0.570
- C3-stack+base 15 LONDON: C_round3_H2 LONDON: WF 0.628 hold 0.673 vs baseline 0.629/0.668
- C3-stack+base 15 NY: C_round3_H2 NY: WF 0.729 hold 0.808 vs baseline 0.726/0.802
- C3-stack+base 20 POOLED: C_round3_H2 ALL: WF 0.628 hold 0.687 vs baseline 0.628/0.686
- C3-stack+base 20 ASIA: C_round3_H2 ASIA: WF 0.506 hold 0.504 vs baseline 0.498/0.503
- C3-stack+base 20 LONDON: C_round3_H2 LONDON: WF 0.591 hold 0.662 vs baseline 0.592/0.663
- C3-stack+base 20 NY: C_round3_H2 NY: WF 0.723 hold 0.837 vs baseline 0.723/0.832
- C3-stack+base 30 POOLED: C_round3_H2 ALL: WF 0.647 hold 0.692 vs baseline 0.644/0.687
- C3-stack+base 30 ASIA: C_round3_H2 ASIA: WF 0.530 hold 0.523 vs baseline 0.524/0.514
- C3-stack+base 30 LONDON: C_round3_H2 LONDON: WF 0.614 hold 0.666 vs baseline 0.612/0.661
- C3-stack+base 30 NY: C_round3_H2 NY: WF 0.715 hold 0.807 vs baseline 0.716/0.804
- C3-stack+base 45 POOLED: C_round3_H2 ALL: WF 0.625 hold 0.678 vs baseline 0.624/0.674
- C3-stack+base 45 ASIA: C_round3_H2 ASIA: WF 0.508 hold 0.528 vs baseline 0.494/0.504
- C3-stack+base 45 LONDON: C_round3_H2 LONDON: WF 0.595 hold 0.629 vs baseline 0.603/0.642
- C3-stack+base 45 NY: C_round3_H2 NY: WF 0.679 hold 0.795 vs baseline 0.676/0.790
- C3-stack+base 5 POOLED: C_round3_H2 ALL: WF 0.604 hold 0.627 vs baseline 0.606/0.632
- C3-stack+base 5 ASIA: C_round3_H2 ASIA: WF 0.541 hold 0.524 vs baseline 0.541/0.528
- C3-stack+base 5 LONDON: C_round3_H2 LONDON: WF 0.563 hold 0.587 vs baseline 0.568/0.595
- C3-stack+base 5 NY: C_round3_H2 NY: WF 0.633 hold 0.694 vs baseline 0.633/0.692
- C3-stack+base 60 POOLED: C_round3_H2 ALL: WF 0.649 hold 0.708 vs baseline 0.652/0.707
- C3-stack+base 60 ASIA: C_round3_H2 ASIA: WF 0.493 hold 0.529 vs baseline 0.498/0.527
- C3-stack+base 60 LONDON: C_round3_H2 LONDON: WF 0.596 hold 0.652 vs baseline 0.597/0.650
- C3-stack+base 60 NY: C_round3_H2 NY: WF 0.779 hold 0.874 vs baseline 0.780/0.873
- C3-Gc -1 POOLED: C_round3_Gc G POOLED/ALL: WF 0.487 hold 0.503 vs R0 0.492/0.507
- C3-Gc -1 POOLED: C_round3_Gc G POOLED/ST: WF 0.493 hold 0.507 vs R0 0.485/0.510
- C3-Gc -1 POOLED: C_round3_Gc G POOLED/HM: WF 0.481 hold 0.498 vs R0 0.501/0.505
- C3-Gc -1 ASIA: C_round3_Gc G ASIA/ALL: WF 0.496 hold 0.485 vs R0 0.491/0.498
- C3-Gc -1 ASIA: C_round3_Gc G ASIA/ST: WF 0.495 hold 0.477 vs R0 0.478/0.501
- C3-Gc -1 ASIA: C_round3_Gc G ASIA/HM: WF 0.497 hold 0.493 vs R0 0.507/0.496
- C3-Gc -1 LONDON: C_round3_Gc G LONDON/ALL: WF 0.474 hold 0.551 vs R0 0.486/0.526
- C3-Gc -1 LONDON: C_round3_Gc G LONDON/ST: WF 0.472 hold 0.558 vs R0 0.487/0.529
- C3-Gc -1 LONDON: C_round3_Gc G LONDON/HM: WF 0.476 hold 0.543 vs R0 0.484/0.523
- C3-Gc -1 NY: C_round3_Gc G NY/ALL: WF 0.486 hold 0.492 vs R0 0.506/0.502
- C3-Gc -1 NY: C_round3_Gc G NY/ST: WF 0.515 hold 0.529 vs R0 0.498/0.501
- C3-Gc -1 NY: C_round3_Gc G NY/HM: WF 0.452 hold 0.447 vs R0 0.514/0.502
- C3-Gs -1 POOLED: C_round3_Gs G POOLED/ALL: WF 0.482 hold 0.488 vs R0 0.492/0.507
- C3-Gs -1 POOLED: C_round3_Gs G POOLED/ST: WF 0.474 hold 0.489 vs R0 0.485/0.510
- C3-Gs -1 POOLED: C_round3_Gs G POOLED/HM: WF 0.492 hold 0.487 vs R0 0.501/0.505
- C3-Gs -1 ASIA: C_round3_Gs G ASIA/ALL: WF 0.490 hold 0.492 vs R0 0.491/0.498
- C3-Gs -1 ASIA: C_round3_Gs G ASIA/ST: WF 0.476 hold 0.494 vs R0 0.478/0.501
- C3-Gs -1 ASIA: C_round3_Gs G ASIA/HM: WF 0.505 hold 0.489 vs R0 0.507/0.496
- C3-Gs -1 LONDON: C_round3_Gs G LONDON/ALL: WF 0.463 hold 0.464 vs R0 0.486/0.526
- C3-Gs -1 LONDON: C_round3_Gs G LONDON/ST: WF 0.458 hold 0.455 vs R0 0.487/0.529
- C3-Gs -1 LONDON: C_round3_Gs G LONDON/HM: WF 0.467 hold 0.472 vs R0 0.484/0.523
- C3-Gs -1 NY: C_round3_Gs G NY/ALL: WF 0.496 hold 0.513 vs R0 0.506/0.502
- C3-Gs -1 NY: C_round3_Gs G NY/ST: WF 0.489 hold 0.514 vs R0 0.498/0.501
- C3-Gs -1 NY: C_round3_Gs G NY/HM: WF 0.504 hold 0.514 vs R0 0.514/0.502
