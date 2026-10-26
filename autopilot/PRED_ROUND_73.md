# PRED ROUND 73 - block X5 round 5 - X36+X37+X38+X39-flow-state-conditional-FR+X40-meta-stack

Best HOLDOUT F-R AUC: +15 POOLED 0.546 [0.50,0.59] | ASIA 0.500 [0.44,0.56] | LONDON 0.540 [0.46,0.62] | NY 0.517 [0.41,0.62]
Best HOLDOUT F-R AUC: +30 POOLED 0.493 [0.45,0.54] | ASIA 0.501 [0.44,0.56] | LONDON 0.508 [0.43,0.59] | NY 0.389 [0.28,0.50]
Best G HOLDOUT AUC: 0.631 [0.59,0.67]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg db9ef386bd06c112e3f1fc8ec77269fee18e8efd73c5f2fb6a5a7655708463a4 ; trials added 150 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'X39 by construction esec<cutoff,xsec<cutoff; others reuse audited stores'} ; holdout scored True ; feature store ['l2vast/pred/store/X39_flow.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X37-micro-plus-base | sig | ASIA/HM | MBR:stack | 0.603 [0.57,0.63] | 0.631 [0.59,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON/ST | MBR:stack | 0.629 [0.59,0.67] | 0.629 [0.56,0.70] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | ASIA/HM | M40R:meta | 0.601 [0.57,0.64] | 0.628 [0.59,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON/ST | M40R:meta | 0.627 [0.58,0.67] | 0.625 [0.56,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | ASIA | MBR:stack | 0.592 [0.57,0.62] | 0.623 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | ASIA/HM | MUR:stack | 0.588 [0.56,0.62] | 0.621 [0.58,0.66] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED/ST | MBR:stack | 0.601 [0.58,0.62] | 0.620 [0.59,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | ASIA | M40R:meta | 0.588 [0.56,0.62] | 0.619 [0.59,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | ASIA/ST | MBR:stack | 0.583 [0.55,0.61] | 0.616 [0.58,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | POOLED/ST | M40R:meta | 0.598 [0.57,0.63] | 0.615 [0.59,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED | MBR:stack | 0.598 [0.58,0.61] | 0.614 [0.59,0.64] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | ASIA/ST | M40R:meta | 0.577 [0.54,0.61] | 0.613 [0.58,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | NY/HM | MCB:stack | 0.570 [0.52,0.62] | 0.612 [0.54,0.69] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | POOLED | M40R:meta | 0.599 [0.58,0.62] | 0.611 [0.59,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED/HM | MBR:stack | 0.595 [0.57,0.61] | 0.610 [0.59,0.63] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | ASIA | MUR:stack | 0.582 [0.55,0.61] | 0.610 [0.58,0.64] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON | MBR:stack | 0.613 [0.58,0.64] | 0.609 [0.56,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | POOLED/HM | M40R:meta | 0.600 [0.58,0.62] | 0.608 [0.58,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY/ST | MBR:stack | 0.592 [0.55,0.64] | 0.605 [0.54,0.67] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON | M40R:meta | 0.614 [0.58,0.65] | 0.604 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | ASIA/ST | MUR:stack | 0.578 [0.55,0.61] | 0.603 [0.57,0.64] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X40-meta-stack | sig | NY/ST | M40R:meta | 0.593 [0.54,0.65] | 0.602 [0.54,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | NY | M40R:meta | 0.601 [0.56,0.64] | 0.601 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY | MBR:stack | 0.594 [0.55,0.63] | 0.599 [0.55,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | NY/HM | M40R:meta | 0.605 [0.55,0.66] | 0.597 [0.53,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON/HM | MBR:stack | 0.598 [0.56,0.64] | 0.592 [0.53,0.65] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY/HM | MBR:stack | 0.593 [0.55,0.64] | 0.590 [0.52,0.66] | - | - | - | ok | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON/HM | M40R:meta | 0.601 [0.56,0.64] | 0.587 [0.53,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | POOLED/HM | MUR:stack | 0.559 [0.54,0.58] | 0.582 [0.55,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | POOLED | MUR:stack | 0.558 [0.54,0.58] | 0.580 [0.56,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | POOLED/ST | MUR:stack | 0.558 [0.54,0.58] | 0.578 [0.55,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X39-flow-state-conditional-FR | +10 | LONDON | stack cond-trained | 0.519 [0.47,0.57] | 0.566 [0.50,0.64] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | ASIA/HM | M40T:meta | 0.535 [0.50,0.58] | 0.564 [0.52,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | NY/HM | MCB:stack | 0.541 [0.49,0.59] | 0.563 [0.48,0.64] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | NY | MCB:stack | 0.546 [0.51,0.58] | 0.560 [0.50,0.61] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +10 | POOLED | stack cond-trained | 0.525 [0.49,0.55] | 0.555 [0.51,0.60] | - | 0.517 | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | NY/ST | M40T:meta | 0.503 [0.44,0.56] | 0.551 [0.46,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | LONDON/ST | MUR:stack | 0.522 [0.48,0.56] | 0.549 [0.48,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X39-flow-state-conditional-FR | +15 | POOLED | stack cond-trained | 0.543 [0.51,0.57] | 0.546 [0.50,0.59] | - | 0.525 | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | ASIA/HM | MUT:stack | 0.525 [0.49,0.56] | 0.546 [0.50,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X40-meta-stack | sig | POOLED/HM | M40T:meta | 0.532 [0.51,0.56] | 0.546 [0.51,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | LONDON | MUR:stack | 0.521 [0.48,0.56] | 0.545 [0.49,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | LONDON/ST | MUT:stack | 0.501 [0.45,0.55] | 0.544 [0.48,0.60] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | LONDON/HM | MUR:stack | 0.520 [0.48,0.56] | 0.544 [0.48,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | ASIA | MUT:stack | 0.521 [0.49,0.55] | 0.541 [0.50,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | NY/HM | MUR:stack | 0.559 [0.51,0.61] | 0.541 [0.47,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X40-meta-stack | sig | ASIA | M40T:meta | 0.515 [0.49,0.55] | 0.540 [0.50,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +15 | LONDON | stack cond-trained | 0.543 [0.49,0.60] | 0.540 [0.46,0.62] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | NY | M40T:meta | 0.520 [0.48,0.56] | 0.539 [0.48,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON/HM | MCB:stack | 0.490 [0.44,0.54] | 0.539 [0.48,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | NY | MUR:stack | 0.549 [0.51,0.59] | 0.539 [0.49,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | ASIA/ST | MUT:stack | 0.518 [0.48,0.55] | 0.537 [0.49,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | NY/ST | MUR:stack | 0.543 [0.49,0.59] | 0.537 [0.48,0.59] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | POOLED/ST | MUT:stack | 0.507 [0.48,0.53] | 0.534 [0.50,0.57] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON/HM | MCB:stack | 0.486 [0.44,0.54] | 0.533 [0.47,0.59] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | NY/HM | M40T:meta | 0.537 [0.49,0.60] | 0.530 [0.45,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | ASIA/ST | M40T:meta | 0.503 [0.47,0.54] | 0.529 [0.49,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | POOLED | MUT:stack | 0.505 [0.48,0.53] | 0.528 [0.50,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X40-meta-stack | sig | POOLED | M40T:meta | 0.515 [0.50,0.53] | 0.526 [0.50,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON | MCB:stack | 0.501 [0.46,0.54] | 0.524 [0.48,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | NY/HM | MUT:stack | 0.521 [0.47,0.58] | 0.524 [0.43,0.61] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | POOLED/HM | MUT:stack | 0.504 [0.47,0.53] | 0.523 [0.49,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X38-marginal-label-micro | sig | NY/ST | MCB:stack | 0.525 [0.48,0.57] | 0.519 [0.45,0.60] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON/HM | M40T:meta | 0.519 [0.47,0.57] | 0.517 [0.44,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +15 | NY | stack cond-trained | 0.514 [0.45,0.58] | 0.517 [0.41,0.62] | - | 0.494 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON | MCB:stack | 0.492 [0.46,0.53] | 0.517 [0.47,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | NY | MCB:stack | 0.519 [0.48,0.55] | 0.516 [0.46,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | NY | MUT:stack | 0.503 [0.47,0.54] | 0.516 [0.46,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED/HM | MCB:stack | 0.503 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | POOLED/ST | M40T:meta | 0.503 [0.48,0.52] | 0.515 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED | MCB:stack | 0.508 [0.49,0.53] | 0.513 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +10 | ASIA | stack cond-trained | 0.526 [0.48,0.57] | 0.512 [0.45,0.57] | - | 0.479 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED/ST | MCB:stack | 0.512 [0.48,0.54] | 0.511 [0.48,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON/ST | MCB:stack | 0.512 [0.47,0.55] | 0.510 [0.45,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | NY/ST | MUT:stack | 0.487 [0.44,0.53] | 0.510 [0.44,0.58] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X36-micro-union | sig | LONDON | MUT:stack | 0.479 [0.44,0.51] | 0.509 [0.46,0.56] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X39-flow-state-conditional-FR | +30 | LONDON | stack cond-trained | 0.522 [0.47,0.58] | 0.508 [0.43,0.59] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA/ST | MCB:stack | 0.501 [0.47,0.53] | 0.507 [0.46,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON/ST | MBT:stack | 0.461 [0.41,0.51] | 0.504 [0.44,0.58] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY/ST | MBT:stack | 0.479 [0.43,0.53] | 0.504 [0.43,0.57] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | LONDON/ST | MCB:stack | 0.500 [0.46,0.54] | 0.502 [0.45,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA/ST | MCB:stack | 0.495 [0.46,0.53] | 0.502 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +30 | ASIA | stack cond-trained | 0.524 [0.48,0.56] | 0.501 [0.44,0.56] | - | 0.469 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED/HM | MCB:stack | 0.491 [0.46,0.51] | 0.501 [0.46,0.54] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +15 | ASIA | stack cond-trained | 0.534 [0.49,0.58] | 0.500 [0.44,0.56] | - | 0.479 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED | MCB:stack | 0.494 [0.47,0.51] | 0.498 [0.47,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | POOLED/ST | MCB:stack | 0.497 [0.47,0.52] | 0.496 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON | MBT:stack | 0.474 [0.44,0.51] | 0.495 [0.45,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED/ST | MBT:stack | 0.476 [0.45,0.50] | 0.493 [0.46,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +30 | POOLED | stack cond-trained | 0.512 [0.48,0.54] | 0.493 [0.45,0.54] | - | 0.459 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA | MCB:stack | 0.490 [0.46,0.52] | 0.491 [0.45,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | LONDON/HM | MBT:stack | 0.487 [0.44,0.53] | 0.488 [0.42,0.55] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +10 | NY | stack cond-trained | 0.495 [0.43,0.56] | 0.487 [0.38,0.59] | - | 0.502 | - | - | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA | MCB:stack | 0.484 [0.45,0.51] | 0.486 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | ASIA/ST | MBT:stack | 0.483 [0.46,0.51] | 0.484 [0.45,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON | M40T:meta | 0.510 [0.47,0.55] | 0.484 [0.43,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED | MBT:stack | 0.480 [0.46,0.50] | 0.482 [0.46,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | ASIA | MBT:stack | 0.489 [0.46,0.51] | 0.479 [0.44,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | NY/ST | MCB:stack | 0.499 [0.45,0.55] | 0.478 [0.41,0.56] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | ASIA/HM | MBT:stack | 0.498 [0.47,0.53] | 0.476 [0.43,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X36-micro-union | sig | LONDON/HM | MUT:stack | 0.456 [0.41,0.50] | 0.475 [0.41,0.54] | - | - | - | N | - | - | - | - |  | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA/HM | MCB:stack | 0.478 [0.44,0.51] | 0.473 [0.43,0.52] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY | MBT:stack | 0.468 [0.43,0.51] | 0.472 [0.42,0.53] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | POOLED/HM | MBT:stack | 0.484 [0.46,0.51] | 0.472 [0.44,0.50] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X38-marginal-label-micro | sig | ASIA/HM | MCB:stack | 0.471 [0.43,0.50] | 0.467 [0.42,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X40-meta-stack | sig | LONDON/ST | M40T:meta | 0.501 [0.45,0.55] | 0.452 [0.39,0.51] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| X37-micro-plus-base | sig | NY/HM | MBT:stack | 0.455 [0.41,0.50] | 0.433 [0.36,0.51] | - | - | - | N | - | - | - | - | stack | locked label (reference only) |
| X39-flow-state-conditional-FR | +30 | NY | stack cond-trained | 0.463 [0.40,0.53] | 0.389 [0.28,0.50] | - | 0.395 | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X36-micro-union -1 POOLED: union; econ not run (holdout stop_vs_target AUC < 0.58)
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X36-micro-union -1 POOLED: union
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X36-micro-union -1 POOLED: union
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X36-micro-union -1 POOLED: union; econ not run (holdout stop_vs_target AUC < 0.58)
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X36-micro-union -1 POOLED: union
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X36-micro-union -1 POOLED: union
- X36-micro-union -1 ASIA: union
- X36-micro-union -1 LONDON: union
- X36-micro-union -1 NY: union
- X37-micro-plus-base -1 POOLED: union+R0; econ not run (holdout stop_vs_target AUC < 0.58)
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X37-micro-plus-base -1 POOLED: union+R0
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X37-micro-plus-base -1 POOLED: union+R0
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X37-micro-plus-base -1 POOLED: union+R0; econ not run (holdout stop_vs_target AUC < 0.58)
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X37-micro-plus-base -1 POOLED: union+R0
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X37-micro-plus-base -1 POOLED: union+R0
- X37-micro-plus-base -1 ASIA: union+R0
- X37-micro-plus-base -1 LONDON: union+R0
- X37-micro-plus-base -1 NY: union+R0
- X38-marginal-label-micro -1 POOLED: ycf; econ not run (holdout stop_vs_target AUC < 0.58)
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X38-marginal-label-micro -1 POOLED: ycf
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X38-marginal-label-micro -1 POOLED: ycf
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X38-marginal-label-micro -1 POOLED: ycf; econ not run (holdout stop_vs_target AUC < 0.58)
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X38-marginal-label-micro -1 POOLED: ycf
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X38-marginal-label-micro -1 POOLED: ycf
- X38-marginal-label-micro -1 ASIA: ycf
- X38-marginal-label-micro -1 LONDON: ycf
- X38-marginal-label-micro -1 NY: ycf
- X40-meta-stack -1 POOLED: stage2; econ not run (holdout stop_vs_target AUC < 0.58)
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X40-meta-stack -1 POOLED: stage2
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X40-meta-stack -1 POOLED: stage2
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X40-meta-stack -1 POOLED: stage2; econ not run (holdout stop_vs_target AUC < 0.58)
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X40-meta-stack -1 POOLED: stage2
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X40-meta-stack -1 POOLED: stage2
- X40-meta-stack -1 ASIA: stage2
- X40-meta-stack -1 LONDON: stage2
- X40-meta-stack -1 NY: stage2
- X39-flow-state-conditional-FR 10 POOLED: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 10 ASIA: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 10 LONDON: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 10 NY: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 15 POOLED: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 15 ASIA: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 15 LONDON: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 15 NY: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 30 POOLED: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 30 ASIA: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 30 LONDON: flow-state session features add nothing: conditional holdout AUC ~0.5
- X39-flow-state-conditional-FR 30 NY: flow-state session features add nothing: conditional holdout AUC ~0.5
