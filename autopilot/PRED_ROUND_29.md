# PRED ROUND 29 - block A round 6 - A-cond

Best HOLDOUT F-R AUC: +15 POOLED 0.574 [0.53,0.62] | ASIA 0.517 [0.46,0.57] | LONDON 0.600 [0.52,0.68] | NY 0.543 [0.43,0.64]
Best HOLDOUT F-R AUC: +30 POOLED 0.564 [0.52,0.61] | ASIA 0.546 [0.48,0.61] | LONDON 0.543 [0.46,0.63] | NY 0.502 [0.39,0.61]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 451d24f4f804d5a5c1afc8f06f701de6b33662a4b80be1cb831916c7f392831e ; trials added 1500 ; truncation audit {'decisions': 74810, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A1A2A3_dense.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A-cond-rescore | +15 | LONDON | r4_A10_lamS|oriented | 0.585 [0.53,0.64] | 0.600 [0.52,0.68] | - | 0.580 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | POOLED | r3_pE|oriented | 0.583 [0.56,0.62] | 0.593 [0.55,0.64] | - | 0.575 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | POOLED | r5_pE|oriented | 0.583 [0.56,0.62] | 0.593 [0.55,0.64] | - | 0.575 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | POOLED | r4_A6_lamS|oriented | 0.589 [0.56,0.62] | 0.593 [0.54,0.64] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | POOLED | r2_lamS|oriented | 0.589 [0.56,0.62] | 0.593 [0.54,0.64] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | POOLED | r5_pE|oriented | 0.590 [0.56,0.62] | 0.588 [0.54,0.63] | - | 0.559 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | POOLED | r3_pE|oriented | 0.590 [0.56,0.62] | 0.588 [0.54,0.63] | - | 0.559 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | POOLED | r4_A9_q25|oriented | 0.581 [0.56,0.61] | 0.583 [0.53,0.63] | - | 0.569 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | POOLED | r4_A10_lamS|oriented | 0.582 [0.55,0.61] | 0.574 [0.53,0.62] | - | 0.545 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | POOLED | r4_A9_q25|oriented | 0.580 [0.55,0.61] | 0.573 [0.53,0.62] | - | 0.556 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | POOLED | r5_pE|oriented | 0.585 [0.55,0.62] | 0.569 [0.52,0.61] | - | 0.545 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | POOLED | r3_pE|oriented | 0.585 [0.55,0.62] | 0.569 [0.52,0.61] | - | 0.545 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | POOLED | r4_A9_q25|oriented | 0.580 [0.55,0.61] | 0.567 [0.52,0.62] | - | 0.546 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | POOLED | r5_pE|oriented | 0.577 [0.55,0.62] | 0.564 [0.52,0.61] | - | 0.531 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +10 | LONDON | stack(cond-trained) | 0.517 [0.47,0.57] | 0.562 [0.49,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-base | +10 | POOLED | stack(cond-trained) | 0.529 [0.50,0.56] | 0.561 [0.52,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +5 | ASIA | r4_A8_H2|oriented | 0.585 [0.55,0.62] | 0.560 [0.50,0.63] | - | 0.538 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | ASIA | r4_A6_lamS|oriented | 0.578 [0.54,0.62] | 0.557 [0.50,0.62] | - | 0.536 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | NY | r4_A10_sE|oriented | 0.559 [0.49,0.62] | 0.552 [0.46,0.65] | - | 0.543 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | ASIA | r4_A8_H1|oriented | 0.580 [0.54,0.62] | 0.550 [0.50,0.61] | - | 0.529 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | ASIA | r4_A8_H2|oriented | 0.580 [0.54,0.62] | 0.550 [0.50,0.61] | - | 0.529 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +30 | ASIA | stack(cond-trained) | 0.537 [0.50,0.58] | 0.546 [0.48,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +10 | NY | r5_C5rf|oriented | 0.550 [0.49,0.62] | 0.546 [0.46,0.62] | - | 0.479 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | ASIA | r4_A6_lamS|oriented | 0.579 [0.54,0.62] | 0.545 [0.49,0.60] | - | 0.520 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | ASIA | r2_lamS|oriented | 0.579 [0.54,0.62] | 0.545 [0.49,0.60] | - | 0.520 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | LONDON | r5_C5rf|oriented | 0.549 [0.50,0.60] | 0.543 [0.46,0.63] | - | 0.534 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +15 | NY | stack(cond-trained) | 0.532 [0.46,0.60] | 0.543 [0.43,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +30 | POOLED | r5_C5gbt3|oriented | 0.561 [0.53,0.59] | 0.542 [0.50,0.59] | - | 0.528 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | ASIA | r3_lamE|oriented | 0.569 [0.54,0.61] | 0.541 [0.49,0.60] | - | 0.515 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +5 | POOLED | stack(cond-trained) | 0.526 [0.50,0.55] | 0.540 [0.50,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +10 | ASIA | r2_lamS|oriented | 0.574 [0.54,0.61] | 0.540 [0.48,0.60] | - | 0.510 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +15 | POOLED | stack(cond-trained) | 0.535 [0.51,0.56] | 0.539 [0.49,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +15 | NY | r4_A9_q25|oriented | 0.554 [0.47,0.62] | 0.538 [0.43,0.66] | - | 0.498 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | NY | r5_Qlogit2|oriented | 0.542 [0.48,0.61] | 0.537 [0.44,0.63] | - | 0.514 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +10 | NY | stack(cond-trained) | 0.504 [0.44,0.57] | 0.537 [0.43,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +10 | POOLED | r5_C5logit2|oriented | 0.562 [0.53,0.59] | 0.536 [0.50,0.58] | - | 0.525 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | pre | POOLED | stack(cond-trained) | 0.515 [0.48,0.54] | 0.534 [0.48,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-base | +20 | LONDON | stack(cond-trained) | 0.517 [0.47,0.57] | 0.533 [0.45,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +5 | NY | r5_Qlogit2|oriented | 0.536 [0.47,0.61] | 0.533 [0.44,0.63] | - | 0.514 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | NY | r5_C5logit2|oriented | 0.555 [0.49,0.62] | 0.532 [0.45,0.60] | - | 0.485 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +10 | POOLED | stack(cond-trained) | 0.532 [0.50,0.56] | 0.531 [0.49,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | LONDON | r4_A10_sE|fixed | 0.540 [0.49,0.60] | 0.531 [0.46,0.61] | - | 0.528 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | LONDON | r5_Qstack|oriented | 0.523 [0.46,0.58] | 0.530 [0.45,0.61] | - | 0.513 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +5 | ASIA | stack(cond-trained) | 0.523 [0.48,0.56] | 0.528 [0.46,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-base | +30 | POOLED | stack(cond-trained) | 0.517 [0.49,0.55] | 0.525 [0.48,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +10 | ASIA | r5_pE|oriented | 0.559 [0.52,0.60] | 0.525 [0.47,0.59] | - | 0.503 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +20 | LONDON | stack(cond-trained) | 0.514 [0.46,0.57] | 0.524 [0.46,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | ASIA | r4_A6_lamS|oriented | 0.574 [0.54,0.62] | 0.521 [0.46,0.58] | - | 0.489 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | ASIA | r2_lamS|oriented | 0.574 [0.54,0.62] | 0.521 [0.46,0.58] | - | 0.489 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | LONDON | r5_C5stack|oriented | 0.541 [0.49,0.59] | 0.520 [0.43,0.61] | - | 0.518 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +15 | POOLED | stack(cond-trained) | 0.536 [0.51,0.57] | 0.520 [0.47,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +30 | POOLED | stack(cond-trained) | 0.523 [0.49,0.55] | 0.520 [0.48,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | pre | ASIA | stack(cond-trained) | 0.513 [0.47,0.55] | 0.520 [0.46,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | pre | LONDON | r5_Qlogit2|oriented | 0.515 [0.46,0.57] | 0.519 [0.44,0.61] | - | 0.516 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | POOLED | r5_C5rf|oriented | 0.549 [0.52,0.58] | 0.518 [0.47,0.57] | - | 0.512 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | ASIA | r4_A8_H1|oriented | 0.555 [0.52,0.60] | 0.517 [0.46,0.57] | - | 0.493 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +15 | ASIA | stack(cond-trained) | 0.532 [0.49,0.58] | 0.516 [0.45,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +20 | POOLED | stack(cond-trained) | 0.528 [0.50,0.56] | 0.515 [0.47,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | ASIA | r4_A8_H2|oriented | 0.567 [0.53,0.61] | 0.515 [0.45,0.58] | - | 0.479 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | LONDON | r5_Qlogit2|oriented | 0.518 [0.46,0.58] | 0.515 [0.44,0.61] | - | 0.526 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +20 | POOLED | stack(cond-trained) | 0.526 [0.50,0.55] | 0.513 [0.47,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +20 | ASIA | r2_lamS|oriented | 0.563 [0.52,0.61] | 0.513 [0.45,0.57] | - | 0.482 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | NY | r4_A7_lamS|oriented | 0.532 [0.48,0.59] | 0.511 [0.40,0.61] | - | 0.426 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | LONDON | r5_C5et|oriented | 0.542 [0.49,0.59] | 0.511 [0.41,0.60] | - | 0.496 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | LONDON | r5_C5et|oriented | 0.536 [0.48,0.58] | 0.511 [0.43,0.59] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | ASIA | r4_A10_lamS|oriented | 0.551 [0.51,0.59] | 0.508 [0.45,0.57] | - | 0.488 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | NY | r4_A8_H4|oriented | 0.534 [0.47,0.60] | 0.508 [0.42,0.60] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +5 | POOLED | stack(cond-trained) | 0.526 [0.50,0.55] | 0.506 [0.46,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +15 | LONDON | stack(cond-trained) | 0.520 [0.47,0.57] | 0.506 [0.43,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +10 | LONDON | r5_C5gbt3|oriented | 0.534 [0.49,0.58] | 0.505 [0.42,0.59] | - | 0.491 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +5 | LONDON | stack(cond-trained) | 0.527 [0.48,0.58] | 0.505 [0.44,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +20 | ASIA | r5_pE|oriented | 0.552 [0.51,0.59] | 0.504 [0.45,0.57] | - | 0.474 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | ASIA | r3_pE|oriented | 0.552 [0.51,0.59] | 0.504 [0.45,0.57] | - | 0.474 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | NY | r5_C5rf|oriented | 0.555 [0.49,0.63] | 0.502 [0.39,0.61] | - | 0.494 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | LONDON | r5_C5gbt3|oriented | 0.524 [0.47,0.57] | 0.502 [0.41,0.59] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +30 | LONDON | stack(cond-trained) | 0.535 [0.48,0.59] | 0.500 [0.44,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +10 | ASIA | stack(cond-trained) | 0.537 [0.49,0.58] | 0.499 [0.44,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | LONDON | r5_C5rf|oriented | 0.532 [0.48,0.58] | 0.496 [0.40,0.59] | - | 0.480 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +10 | ASIA | stack(cond-trained) | 0.525 [0.48,0.57] | 0.496 [0.43,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-only | +10 | NY | stack(cond-trained) | 0.478 [0.41,0.54] | 0.496 [0.39,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | pre | POOLED | stack(cond-trained) | 0.508 [0.48,0.53] | 0.494 [0.45,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +15 | ASIA | stack(cond-trained) | 0.525 [0.48,0.57] | 0.494 [0.43,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-only | +5 | LONDON | stack(cond-trained) | 0.519 [0.47,0.57] | 0.491 [0.42,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +30 | ASIA | stack(cond-trained) | 0.511 [0.47,0.56] | 0.491 [0.43,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +30 | LONDON | stack(cond-trained) | 0.515 [0.46,0.57] | 0.491 [0.42,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-only | +5 | ASIA | stack(cond-trained) | 0.532 [0.49,0.57] | 0.490 [0.42,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | NY | r4_A8_H2|fixed | 0.517 [0.46,0.57] | 0.489 [0.39,0.59] | - | 0.563 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | pre | NY | r4_A8_H1|fixed | 0.517 [0.46,0.57] | 0.489 [0.39,0.59] | - | 0.563 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | NY | r5_C5et|oriented | 0.550 [0.48,0.63] | 0.489 [0.39,0.60] | - | 0.475 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | LONDON | r5_C5et|oriented | 0.521 [0.46,0.57] | 0.489 [0.38,0.58] | - | 0.489 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +10 | LONDON | stack(cond-trained) | 0.519 [0.47,0.57] | 0.489 [0.41,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | LONDON | r5_C5rf|oriented | 0.523 [0.47,0.57] | 0.488 [0.40,0.57] | - | 0.468 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | pre | LONDON | stack(cond-trained) | 0.499 [0.45,0.55] | 0.488 [0.42,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +15 | NY | r4_A6_sE|oriented | 0.527 [0.47,0.59] | 0.488 [0.41,0.57] | - | 0.471 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | POOLED | r5_C5et|oriented | 0.535 [0.50,0.57] | 0.485 [0.44,0.53] | - | 0.489 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +30 | LONDON | r5_Qrf|oriented | 0.512 [0.46,0.57] | 0.485 [0.40,0.56] | - | 0.504 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +20 | ASIA | stack(cond-trained) | 0.517 [0.48,0.56] | 0.485 [0.43,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +5 | NY | r3_C4|oriented | 0.530 [0.47,0.59] | 0.483 [0.39,0.57] | - | 0.419 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | pre | NY | stack(cond-trained) | 0.514 [0.45,0.58] | 0.483 [0.38,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +15 | POOLED | r5_C5et|oriented | 0.525 [0.49,0.55] | 0.481 [0.43,0.53] | - | 0.490 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | LONDON | r4_A8_H4|fixed | 0.523 [0.47,0.57] | 0.481 [0.40,0.55] | - | 0.501 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +15 | LONDON | stack(cond-trained) | 0.506 [0.45,0.56] | 0.475 [0.40,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +20 | ASIA | stack(cond-trained) | 0.527 [0.49,0.57] | 0.473 [0.41,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +5 | LONDON | r5_Qrf|oriented | 0.513 [0.47,0.57] | 0.473 [0.39,0.56] | - | 0.504 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +15 | ASIA | r4_A7_sP|oriented | 0.537 [0.49,0.58] | 0.472 [0.41,0.54] | - | 0.469 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | pre | LONDON | stack(cond-trained) | 0.483 [0.43,0.54] | 0.472 [0.40,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +30 | NY | stack(cond-trained) | 0.461 [0.39,0.53] | 0.472 [0.36,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +5 | NY | stack(cond-trained) | 0.485 [0.42,0.55] | 0.472 [0.37,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +20 | NY | r3_pE|oriented | 0.532 [0.45,0.60] | 0.467 [0.36,0.58] | - | 0.434 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | NY | r5_pE|oriented | 0.532 [0.45,0.60] | 0.467 [0.36,0.58] | - | 0.434 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +15 | NY | stack(cond-trained) | 0.529 [0.47,0.59] | 0.460 [0.36,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | pre | NY | stack(cond-trained) | 0.452 [0.39,0.51] | 0.460 [0.38,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | pre | ASIA | stack(cond-trained) | 0.518 [0.47,0.56] | 0.457 [0.40,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +20 | NY | r5_C5et|oriented | 0.537 [0.46,0.61] | 0.451 [0.34,0.57] | - | 0.427 | - | - | - | - | - | - |  | locked label (reference only) |
| A-cond-rescore | +10 | LONDON | r5_Qrf|oriented | 0.509 [0.45,0.57] | 0.451 [0.38,0.52] | - | 0.469 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +30 | NY | stack(cond-trained) | 0.456 [0.39,0.53] | 0.440 [0.35,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-cond-rescore | +30 | NY | r5_Qet|oriented | 0.532 [0.46,0.62] | 0.424 [0.33,0.53] | - | 0.420 | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-base | +20 | NY | stack(cond-trained) | 0.497 [0.43,0.57] | 0.416 [0.31,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| A-condtrain-only | +20 | NY | stack(cond-trained) | 0.441 [0.37,0.51] | 0.396 [0.28,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| A-condtrain-only | +5 | NY | stack(cond-trained) | 0.458 [0.39,0.53] | 0.379 [0.28,0.47] | - | - | - | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- A-cond-rescore 5 LONDON: conditional AUC; R0 stack cond hold 0.438; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.526
- A-cond-rescore 20 LONDON: conditional AUC; R0 stack cond hold 0.504; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.497
- A-cond-rescore 0 LONDON: conditional AUC; R0 stack cond hold 0.522; oriented=fixed (activity-induced if oriented); strata(actual N entries) 0.528
- A-cond-rescore 0 NY: conditional AUC; R0 stack cond hold 0.448; oriented=fixed (activity-induced if oriented); strata(actual N entries) 0.563
- A-cond-rescore 0 NY: conditional AUC; R0 stack cond hold 0.448; oriented=fixed (activity-induced if oriented); strata(actual N entries) 0.563
- A-cond-rescore 0 LONDON: conditional AUC; R0 stack cond hold 0.522; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.513
- A-cond-rescore 5 LONDON: conditional AUC; R0 stack cond hold 0.438; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.504
- A-cond-rescore 10 NY: conditional AUC; R0 stack cond hold 0.551; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.479
- A-cond-rescore 20 LONDON: conditional AUC; R0 stack cond hold 0.504; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.489
- A-cond-rescore 15 LONDON: conditional AUC; R0 stack cond hold 0.486; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.468
- A-cond-rescore 5 LONDON: conditional AUC; R0 stack cond hold 0.438; oriented=fixed (activity-induced if oriented); strata(actual N entries) 0.501
- A-cond-rescore 15 NY: conditional AUC; R0 stack cond hold 0.520; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.498
- A-cond-rescore 30 LONDON: conditional AUC; R0 stack cond hold 0.546; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.504
- A-cond-rescore 30 LONDON: conditional AUC; R0 stack cond hold 0.546; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.497
- A-cond-rescore 30 LONDON: conditional AUC; R0 stack cond hold 0.546; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.534
- A-cond-rescore 15 NY: conditional AUC; R0 stack cond hold 0.520; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.497
- A-cond-rescore 15 NY: conditional AUC; R0 stack cond hold 0.520; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.471
- A-cond-rescore 0 NY: conditional AUC; R0 stack cond hold 0.448; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.543
- A-cond-rescore 5 NY: conditional AUC; R0 stack cond hold 0.500; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.514
- A-cond-rescore 15 LONDON: conditional AUC; R0 stack cond hold 0.486; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.580
- A-cond-rescore 20 LONDON: conditional AUC; R0 stack cond hold 0.504; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.518
- A-cond-rescore 10 LONDON: conditional AUC; R0 stack cond hold 0.537; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.491
- A-cond-rescore 5 NY: conditional AUC; R0 stack cond hold 0.500; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.419
- A-cond-rescore 10 NY: conditional AUC; R0 stack cond hold 0.551; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.485
- A-cond-rescore 10 LONDON: conditional AUC; R0 stack cond hold 0.537; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.480
- A-cond-rescore 0 LONDON: conditional AUC; R0 stack cond hold 0.522; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.516
- A-cond-rescore 0 POOLED: conditional AUC; R0 stack cond hold 0.490; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.575
- A-cond-rescore 0 POOLED: conditional AUC; R0 stack cond hold 0.490; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.575
- A-cond-rescore 15 LONDON: conditional AUC; R0 stack cond hold 0.486; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.496
- A-cond-rescore 5 NY: conditional AUC; R0 stack cond hold 0.500; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.426
- A-cond-rescore 15 POOLED: conditional AUC; R0 stack cond hold 0.529; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.490
- A-cond-rescore 0 POOLED: conditional AUC; R0 stack cond hold 0.490; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.569
- A-cond-rescore 10 ASIA: conditional AUC; R0 stack cond hold 0.531; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.503
- A-cond-rescore 30 POOLED: conditional AUC; R0 stack cond hold 0.541; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.531
- A-cond-rescore 5 POOLED: conditional AUC; R0 stack cond hold 0.460; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.555
- A-cond-rescore 5 POOLED: conditional AUC; R0 stack cond hold 0.460; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.555
- A-cond-rescore 15 POOLED: conditional AUC; R0 stack cond hold 0.529; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.545
- A-cond-rescore 30 POOLED: conditional AUC; R0 stack cond hold 0.541; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.512
- A-cond-rescore 10 NY: conditional AUC; R0 stack cond hold 0.551; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.514
- A-cond-rescore 15 ASIA: conditional AUC; R0 stack cond hold 0.559; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.493
- A-cond-rescore 15 ASIA: conditional AUC; R0 stack cond hold 0.559; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.488
- A-cond-rescore 10 ASIA: conditional AUC; R0 stack cond hold 0.531; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.515
- A-cond-rescore 10 LONDON: conditional AUC; R0 stack cond hold 0.537; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.469
- A-cond-rescore 20 POOLED: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.489
- A-cond-rescore 15 POOLED: conditional AUC; R0 stack cond hold 0.529; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.556
- A-cond-rescore 5 POOLED: conditional AUC; R0 stack cond hold 0.460; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.546
- A-cond-rescore 30 POOLED: conditional AUC; R0 stack cond hold 0.541; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.528
- A-cond-rescore 15 ASIA: conditional AUC; R0 stack cond hold 0.559; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.469
- A-cond-rescore 10 POOLED: conditional AUC; R0 stack cond hold 0.536; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.559
- A-cond-rescore 10 POOLED: conditional AUC; R0 stack cond hold 0.536; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.559
- A-cond-rescore 20 ASIA: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.474
- A-cond-rescore 20 ASIA: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.474
- A-cond-rescore 10 POOLED: conditional AUC; R0 stack cond hold 0.536; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.525
- A-cond-rescore 0 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.536
- A-cond-rescore 20 NY: conditional AUC; R0 stack cond hold 0.575; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.427
- A-cond-rescore 30 NY: conditional AUC; R0 stack cond hold 0.571; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.420
- A-cond-rescore 20 POOLED: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.545
- A-cond-rescore 20 POOLED: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.545
- A-cond-rescore 30 NY: conditional AUC; R0 stack cond hold 0.571; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.494
- A-cond-rescore 10 ASIA: conditional AUC; R0 stack cond hold 0.531; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.510
- A-cond-rescore 30 ASIA: conditional AUC; R0 stack cond hold 0.528; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.479
- A-cond-rescore 20 NY: conditional AUC; R0 stack cond hold 0.575; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.434
- A-cond-rescore 20 NY: conditional AUC; R0 stack cond hold 0.575; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.434
- A-cond-rescore 30 NY: conditional AUC; R0 stack cond hold 0.571; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.475
- A-cond-rescore 0 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.529
- A-cond-rescore 0 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.529
- A-cond-rescore 20 ASIA: conditional AUC; R0 stack cond hold 0.521; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.482
- A-cond-rescore 5 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.538
- A-cond-rescore 5 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.520
- A-cond-rescore 5 ASIA: conditional AUC; R0 stack cond hold 0.532; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.520
- A-cond-rescore 30 ASIA: conditional AUC; R0 stack cond hold 0.528; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.489
- A-cond-rescore 30 ASIA: conditional AUC; R0 stack cond hold 0.528; oriented=oriented (activity-induced if oriented); strata(actual N entries) 0.489
- A-condtrain-base 0 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 0 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 0 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 0 NY: cond-trained harness stack with A-dense features
- A-condtrain-base 10 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 10 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 10 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 10 NY: cond-trained harness stack with A-dense features
- A-condtrain-base 15 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 15 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 15 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 15 NY: cond-trained harness stack with A-dense features
- A-condtrain-base 20 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 20 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 20 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 20 NY: cond-trained harness stack with A-dense features
- A-condtrain-base 30 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 30 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 30 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 30 NY: cond-trained harness stack with A-dense features
- A-condtrain-base 5 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-base 5 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-base 5 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-base 5 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 0 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 0 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 0 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 0 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 10 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 10 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 10 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 10 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 15 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 15 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 15 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 15 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 20 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 20 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 20 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 20 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 30 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 30 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 30 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 30 NY: cond-trained harness stack with A-dense features
- A-condtrain-only 5 POOLED: cond-trained harness stack with A-dense features
- A-condtrain-only 5 ASIA: cond-trained harness stack with A-dense features
- A-condtrain-only 5 LONDON: cond-trained harness stack with A-dense features
- A-condtrain-only 5 NY: cond-trained harness stack with A-dense features
