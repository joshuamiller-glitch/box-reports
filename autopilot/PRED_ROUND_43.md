# PRED ROUND 43 - block B round 7 - B123+B1+B2+B3+B57+B5+B7+B469+B4+B6+B9

Best HOLDOUT F-R AUC: +15 POOLED 0.589 [0.55,0.63] | ASIA 0.546 [0.48,0.62] | LONDON 0.611 [0.53,0.69] | NY 0.574 [0.45,0.70]
Best HOLDOUT F-R AUC: +30 POOLED 0.595 [0.55,0.63] | ASIA 0.553 [0.49,0.61] | LONDON 0.624 [0.55,0.70] | NY 0.596 [0.49,0.69]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5436a15b60dd8c70a7c43c47e34b8e822c05f4740c77e6b2660b34cf441b061c ; trials added 1000 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'rounds 1-3 audits 0 mismatches (41280/35200/50560 checks)'} ; holdout scored True ; feature store ['l2vast/pred/store/B10_round5.parquet', 'l2vast/pred/store/B10_round5_sig.parquet', 'l2vast/pred/store/B11_round5.parquet', 'l2vast/pred/store/B11_round5_sig.parquet', 'l2vast/pred/store/B12_round5.parquet', 'l2vast/pred/store/B12_round5_sig.parquet', 'l2vast/pred/store/B13_round5.parquet', 'l2vast/pred/store/B13_round5_sig.parquet', 'l2vast/pred/store/B14_round5.parquet', 'l2vast/pred/store/B14_round5_sig.parquet', 'l2vast/pred/store/B15_round5.parquet', 'l2vast/pred/store/B15_round5_sig.parquet', 'l2vast/pred/store/B1_round1.parquet', 'l2vast/pred/store/B1_round1_sig.parquet', 'l2vast/pred/store/B2_round1.parquet', 'l2vast/pred/store/B2_round1_sig.parquet', 'l2vast/pred/store/B3_round1.parquet', 'l2vast/pred/store/B3_round1_sig.parquet', 'l2vast/pred/store/B4_round3.parquet', 'l2vast/pred/store/B4_round3_sig.parquet', 'l2vast/pred/store/B5_round2.parquet', 'l2vast/pred/store/B5_round2_sig.parquet', 'l2vast/pred/store/B6_round3.parquet', 'l2vast/pred/store/B6_round3_sig.parquet', 'l2vast/pred/store/B7_round2.parquet', 'l2vast/pred/store/B7_round2_sig.parquet', 'l2vast/pred/store/B9_round3.parquet', 'l2vast/pred/store/B9_round3_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B123-cond | +30 | LONDON | rf | 0.577 [0.53,0.63] | 0.624 [0.55,0.70] | - | 0.593 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +30 | LONDON | rf | 0.533 [0.48,0.59] | 0.618 [0.54,0.68] | - | 0.602 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | LONDON | stack | 0.499 [0.44,0.56] | 0.611 [0.53,0.69] | - | 0.620 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +20 | LONDON | rf | 0.583 [0.53,0.64] | 0.608 [0.52,0.69] | - | 0.580 | - | - | - | - | - | - |  | locked label (reference only) |
| B9-cond | +15 | LONDON | stack | 0.522 [0.46,0.58] | 0.606 [0.52,0.69] | - | 0.619 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | POOLED | stack | 0.580 [0.55,0.61] | 0.603 [0.56,0.65] | - | 0.580 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | LONDON | logit2 | 0.506 [0.46,0.56] | 0.602 [0.53,0.68] | - | 0.569 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | LONDON | gbt3 | 0.509 [0.45,0.57] | 0.601 [0.52,0.68] | - | 0.589 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +30 | NY | rf | 0.547 [0.48,0.61] | 0.596 [0.49,0.69] | - | 0.563 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +30 | POOLED | rf | 0.571 [0.54,0.60] | 0.595 [0.55,0.63] | - | 0.563 | - | - | - | - | - | - |  | locked label (reference only) |
| B1-cond | +10 | NY | stack | 0.543 [0.48,0.60] | 0.595 [0.50,0.69] | - | 0.577 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +10 | POOLED | stack | 0.585 [0.55,0.62] | 0.594 [0.55,0.64] | - | 0.579 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | POOLED | stack | 0.577 [0.55,0.61] | 0.590 [0.54,0.64] | - | 0.572 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | POOLED | logit2 | 0.545 [0.51,0.58] | 0.589 [0.55,0.63] | - | 0.558 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +30 | POOLED | logit2 | 0.549 [0.52,0.58] | 0.589 [0.55,0.63] | - | 0.568 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +10 | POOLED | stack | 0.575 [0.54,0.61] | 0.589 [0.54,0.63] | - | 0.566 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | POOLED | gbt3 | 0.547 [0.52,0.58] | 0.589 [0.55,0.63] | - | 0.558 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | POOLED | logit2 | 0.546 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.563 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +30 | POOLED | rf | 0.555 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.561 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | POOLED | stack | 0.563 [0.53,0.59] | 0.588 [0.54,0.63] | - | 0.570 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | POOLED | logit2 | 0.549 [0.52,0.58] | 0.588 [0.55,0.63] | - | 0.571 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +10 | POOLED | stack | 0.576 [0.54,0.61] | 0.587 [0.54,0.63] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +10 | POOLED | stack | 0.571 [0.54,0.60] | 0.587 [0.54,0.63] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | LONDON | logit2 | 0.511 [0.45,0.57] | 0.587 [0.51,0.67] | - | 0.563 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +20 | POOLED | rf | 0.575 [0.55,0.60] | 0.586 [0.54,0.63] | - | 0.558 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +30 | LONDON | logit2 | 0.504 [0.45,0.56] | 0.586 [0.51,0.66] | - | 0.562 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | POOLED | stack | 0.568 [0.54,0.60] | 0.585 [0.54,0.63] | - | 0.570 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | POOLED | logit2 | 0.548 [0.52,0.58] | 0.584 [0.55,0.63] | - | 0.558 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | LONDON | stack | 0.515 [0.46,0.57] | 0.584 [0.50,0.66] | - | 0.609 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | LONDON | rf | 0.511 [0.46,0.56] | 0.582 [0.51,0.66] | - | 0.567 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +30 | LONDON | rf | 0.536 [0.48,0.59] | 0.581 [0.50,0.65] | - | 0.587 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | POOLED | stack | 0.565 [0.53,0.59] | 0.581 [0.54,0.62] | - | 0.564 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | POOLED | rf | 0.573 [0.55,0.60] | 0.580 [0.54,0.62] | - | 0.558 | - | - | - | - | - | - |  | locked label (reference only) |
| B3-cond | +10 | POOLED | stack | 0.581 [0.55,0.61] | 0.580 [0.53,0.62] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | NY | stack | 0.523 [0.46,0.58] | 0.579 [0.48,0.67] | - | 0.555 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +10 | POOLED | rf | 0.558 [0.53,0.59] | 0.579 [0.53,0.63] | - | 0.555 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | LONDON | gbt3 | 0.558 [0.51,0.61] | 0.578 [0.49,0.66] | - | 0.583 | - | - | - | - | - | - |  | locked label (reference only) |
| B2-cond | +30 | POOLED | rf | 0.538 [0.51,0.57] | 0.578 [0.54,0.62] | - | 0.555 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +20 | POOLED | stack | 0.567 [0.54,0.60] | 0.577 [0.53,0.62] | - | 0.567 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | LONDON | logit2 | 0.534 [0.48,0.59] | 0.576 [0.49,0.66] | - | 0.560 | - | - | - | - | - | - |  | locked label (reference only) |
| B57-cond | +15 | POOLED | logit2 | 0.563 [0.53,0.59] | 0.576 [0.53,0.62] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +15 | LONDON | rf | 0.579 [0.53,0.64] | 0.575 [0.49,0.66] | - | 0.559 | - | - | - | - | - | - |  | locked label (reference only) |
| B7-cond | +10 | LONDON | rf | 0.522 [0.47,0.57] | 0.575 [0.50,0.65] | - | 0.573 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +15 | LONDON | rf | 0.547 [0.50,0.59] | 0.575 [0.51,0.64] | - | 0.592 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +15 | NY | stack | 0.521 [0.45,0.60] | 0.574 [0.45,0.70] | - | 0.547 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | POOLED | rf | 0.564 [0.53,0.59] | 0.573 [0.53,0.61] | - | 0.550 | - | - | - | - | - | - |  | locked label (reference only) |
| B57-cond | +15 | LONDON | rf | 0.540 [0.49,0.59] | 0.572 [0.50,0.64] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| B3-cond | +15 | POOLED | stack | 0.558 [0.53,0.59] | 0.571 [0.53,0.61] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | POOLED | stack | 0.555 [0.52,0.58] | 0.570 [0.53,0.61] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | POOLED | stack | 0.558 [0.53,0.59] | 0.570 [0.53,0.61] | - | 0.559 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | POOLED | stack | 0.557 [0.53,0.59] | 0.569 [0.52,0.61] | - | 0.549 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | LONDON | stack | 0.560 [0.51,0.61] | 0.569 [0.49,0.64] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +30 | POOLED | stack | 0.555 [0.52,0.58] | 0.569 [0.52,0.61] | - | 0.554 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | POOLED | stack | 0.549 [0.52,0.58] | 0.568 [0.52,0.61] | - | 0.554 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +20 | POOLED | stack | 0.568 [0.54,0.60] | 0.568 [0.52,0.61] | - | 0.556 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +10 | ASIA | stack | 0.546 [0.50,0.59] | 0.567 [0.50,0.64] | - | 0.558 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | POOLED | gbt3 | 0.527 [0.50,0.56] | 0.567 [0.52,0.61] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | POOLED | stack | 0.548 [0.52,0.58] | 0.567 [0.52,0.61] | - | 0.548 | - | - | - | - | - | - |  | locked label (reference only) |
| B7-cond | +15 | POOLED | rf | 0.560 [0.53,0.58] | 0.566 [0.52,0.61] | - | 0.547 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | POOLED | stack | 0.546 [0.52,0.58] | 0.565 [0.52,0.60] | - | 0.549 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | POOLED | stack | 0.563 [0.53,0.59] | 0.565 [0.52,0.61] | - | 0.548 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +30 | POOLED | rf | 0.554 [0.52,0.59] | 0.564 [0.52,0.61] | - | 0.540 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | ASIA | logit2 | 0.572 [0.53,0.61] | 0.564 [0.51,0.63] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | NY | logit2 | 0.436 [0.37,0.51] | 0.562 [0.44,0.69] | - | 0.537 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +10 | POOLED | rf | 0.551 [0.52,0.58] | 0.562 [0.52,0.61] | - | 0.541 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | LONDON | gbt3 | 0.521 [0.48,0.57] | 0.562 [0.49,0.63] | - | 0.590 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +10 | ASIA | stack | 0.565 [0.53,0.61] | 0.561 [0.50,0.62] | - | 0.548 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | POOLED | stack | 0.547 [0.52,0.58] | 0.561 [0.51,0.61] | - | 0.531 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | NY | gbt3 | 0.500 [0.44,0.56] | 0.559 [0.47,0.64] | - | 0.532 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +30 | POOLED | stack | 0.542 [0.51,0.57] | 0.559 [0.52,0.60] | - | 0.543 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | LONDON | logit2 | 0.511 [0.45,0.57] | 0.558 [0.48,0.64] | - | 0.534 | - | - | - | - | - | - |  | locked label (reference only) |
| B7-cond | +15 | LONDON | gbt3 | 0.536 [0.49,0.59] | 0.557 [0.49,0.63] | - | 0.584 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +10 | ASIA | logit2 | 0.564 [0.51,0.61] | 0.557 [0.50,0.62] | - | 0.545 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +15 | POOLED | gbt3 | 0.550 [0.52,0.58] | 0.556 [0.52,0.59] | - | 0.537 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | LONDON | stack | 0.497 [0.45,0.55] | 0.556 [0.48,0.63] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | NY | stack | 0.537 [0.47,0.59] | 0.556 [0.47,0.65] | - | 0.502 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +10 | POOLED | logit2 | 0.538 [0.51,0.56] | 0.556 [0.51,0.60] | - | 0.541 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | NY | stack | 0.524 [0.45,0.59] | 0.556 [0.44,0.67] | - | 0.531 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | POOLED | gbt3 | 0.546 [0.52,0.58] | 0.555 [0.51,0.60] | - | 0.529 | - | - | - | - | - | - |  | locked label (reference only) |
| B469-cond | +10 | ASIA | stack | 0.553 [0.51,0.60] | 0.554 [0.48,0.63] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | POOLED | stack | 0.540 [0.51,0.57] | 0.553 [0.51,0.60] | - | 0.522 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | ASIA | gbt3 | 0.541 [0.50,0.58] | 0.553 [0.49,0.61] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | LONDON | stack | 0.547 [0.50,0.60] | 0.553 [0.47,0.63] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | POOLED | stack | 0.547 [0.52,0.57] | 0.550 [0.51,0.59] | - | 0.518 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | ASIA | stack | 0.523 [0.48,0.57] | 0.549 [0.49,0.62] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | LONDON | logit2 | 0.464 [0.41,0.52] | 0.548 [0.48,0.62] | - | 0.519 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +15 | ASIA | rf | 0.548 [0.51,0.59] | 0.546 [0.48,0.62] | - | 0.531 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +10 | LONDON | rf | 0.524 [0.48,0.57] | 0.545 [0.48,0.62] | - | 0.543 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | ASIA | stack | 0.569 [0.53,0.61] | 0.545 [0.48,0.60] | - | 0.533 | - | - | - | - | - | - |  | locked label (reference only) |
| B3-cond | +15 | NY | stack | 0.511 [0.45,0.58] | 0.545 [0.44,0.64] | - | 0.525 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +10 | LONDON | stack | 0.518 [0.46,0.57] | 0.544 [0.46,0.63] | - | 0.541 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | POOLED | logit2 | 0.541 [0.51,0.57] | 0.544 [0.50,0.59] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +20 | LONDON | stack | 0.514 [0.46,0.57] | 0.543 [0.46,0.62] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | ASIA | logit2 | 0.549 [0.50,0.59] | 0.542 [0.47,0.61] | - | 0.518 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | ASIA | logit2 | 0.553 [0.51,0.60] | 0.542 [0.48,0.60] | - | 0.528 | - | - | - | - | - | - |  | locked label (reference only) |
| B123-cond | +30 | ASIA | logit2 | 0.545 [0.50,0.59] | 0.542 [0.48,0.61] | - | 0.517 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | LONDON | stack | 0.495 [0.44,0.54] | 0.541 [0.48,0.60] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | LONDON | gbt3 | 0.478 [0.42,0.53] | 0.540 [0.46,0.62] | - | 0.551 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | POOLED | gbt3 | 0.524 [0.49,0.55] | 0.540 [0.50,0.58] | - | 0.523 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | ASIA | logit2 | 0.545 [0.51,0.59] | 0.540 [0.48,0.60] | - | 0.537 | - | - | - | - | - | - |  | locked label (reference only) |
| B469-cond | +10 | ASIA | logit2 | 0.562 [0.52,0.60] | 0.537 [0.48,0.60] | - | 0.521 | - | - | - | - | - | - |  | locked label (reference only) |
| B9-cond | +15 | NY | stack | 0.505 [0.44,0.57] | 0.537 [0.43,0.63] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +20 | LONDON | stack | 0.539 [0.49,0.59] | 0.536 [0.46,0.61] | - | 0.531 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +15 | POOLED | stack | 0.534 [0.50,0.56] | 0.535 [0.49,0.58] | - | 0.514 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | NY | rf | 0.474 [0.41,0.54] | 0.535 [0.42,0.64] | - | 0.530 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +30 | ASIA | stack | 0.548 [0.50,0.59] | 0.534 [0.47,0.60] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | ASIA | gbt3 | 0.536 [0.49,0.58] | 0.532 [0.48,0.59] | - | 0.517 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | ASIA | rf | 0.540 [0.50,0.58] | 0.532 [0.46,0.60] | - | 0.524 | - | - | - | - | - | - |  | locked label (reference only) |
| B2-cond | +15 | NY | stack | 0.505 [0.44,0.57] | 0.532 [0.42,0.65] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +20 | NY | stack | 0.474 [0.41,0.54] | 0.531 [0.43,0.63] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | ASIA | stack | 0.523 [0.48,0.57] | 0.531 [0.47,0.59] | - | 0.508 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | NY | stack | 0.544 [0.48,0.60] | 0.531 [0.44,0.63] | - | 0.503 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | LONDON | stack | 0.494 [0.44,0.55] | 0.530 [0.45,0.61] | - | 0.537 | - | - | - | - | - | - |  | locked label (reference only) |
| B469-cond | +30 | ASIA | logit2 | 0.553 [0.51,0.59] | 0.530 [0.48,0.58] | - | 0.513 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +30 | POOLED | stack | 0.541 [0.51,0.57] | 0.529 [0.48,0.58] | - | 0.495 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | LONDON | stack | 0.498 [0.44,0.56] | 0.529 [0.44,0.61] | - | 0.564 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | LONDON | stack | 0.542 [0.48,0.60] | 0.528 [0.45,0.60] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | POOLED | stack | 0.532 [0.50,0.56] | 0.528 [0.48,0.57] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | NY | stack | 0.522 [0.46,0.58] | 0.528 [0.43,0.62] | - | 0.508 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | NY | gbt3 | 0.508 [0.44,0.57] | 0.527 [0.43,0.62] | - | 0.544 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | POOLED | logit2 | 0.526 [0.49,0.56] | 0.527 [0.48,0.57] | - | 0.510 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +20 | NY | rf | 0.521 [0.46,0.59] | 0.527 [0.43,0.63] | - | 0.508 | - | - | - | - | - | - |  | locked label (reference only) |
| B2-cond | +30 | ASIA | rf | 0.532 [0.49,0.57] | 0.526 [0.47,0.59] | - | 0.502 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | NY | logit2 | 0.514 [0.45,0.58] | 0.526 [0.41,0.64] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +10 | NY | stack | 0.497 [0.43,0.56] | 0.525 [0.43,0.61] | - | 0.469 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | POOLED | stack | 0.537 [0.51,0.57] | 0.525 [0.48,0.57] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +10 | NY | stack | 0.472 [0.40,0.53] | 0.524 [0.43,0.61] | - | 0.501 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | LONDON | stack | 0.492 [0.44,0.54] | 0.523 [0.45,0.60] | - | 0.520 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +30 | ASIA | rf | 0.546 [0.50,0.58] | 0.522 [0.46,0.58] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +30 | ASIA | rf | 0.543 [0.50,0.59] | 0.521 [0.46,0.59] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | ASIA | stack | 0.519 [0.47,0.57] | 0.521 [0.45,0.59] | - | 0.504 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | ASIA | stack | 0.521 [0.48,0.56] | 0.521 [0.46,0.58] | - | 0.491 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +10 | ASIA | rf | 0.552 [0.51,0.60] | 0.521 [0.44,0.60] | - | 0.508 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | ASIA | logit2 | 0.517 [0.47,0.56] | 0.520 [0.46,0.58] | - | 0.498 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +10 | LONDON | logit2 | 0.496 [0.44,0.55] | 0.520 [0.42,0.61] | - | 0.528 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +30 | LONDON | stack | 0.492 [0.44,0.55] | 0.520 [0.43,0.60] | - | 0.515 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | NY | logit2 | 0.509 [0.44,0.57] | 0.518 [0.41,0.63] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | LONDON | logit2 | 0.506 [0.44,0.56] | 0.518 [0.43,0.61] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | ASIA | stack | 0.531 [0.49,0.57] | 0.518 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | ASIA | stack | 0.531 [0.48,0.57] | 0.517 [0.46,0.58] | - | 0.487 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | ASIA | stack | 0.542 [0.50,0.58] | 0.517 [0.46,0.58] | - | 0.476 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | POOLED | logit2 | 0.519 [0.49,0.55] | 0.517 [0.47,0.56] | - | 0.497 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | ASIA | stack | 0.515 [0.47,0.56] | 0.517 [0.45,0.58] | - | 0.494 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | ASIA | stack | 0.527 [0.48,0.57] | 0.516 [0.45,0.58] | - | 0.483 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +15 | ASIA | stack | 0.529 [0.48,0.57] | 0.516 [0.45,0.58] | - | 0.501 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +30 | NY | rf | 0.484 [0.42,0.55] | 0.515 [0.41,0.61] | - | 0.515 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +10 | ASIA | rf | 0.556 [0.51,0.60] | 0.514 [0.45,0.58] | - | 0.507 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +15 | ASIA | rf | 0.536 [0.49,0.59] | 0.514 [0.44,0.59] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +15 | LONDON | stack | 0.507 [0.46,0.56] | 0.514 [0.44,0.59] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +20 | ASIA | rf | 0.535 [0.49,0.58] | 0.511 [0.45,0.58] | - | 0.485 | - | - | - | - | - | - |  | locked label (reference only) |
| B9-cond | +30 | ASIA | stack | 0.534 [0.49,0.57] | 0.511 [0.44,0.57] | - | 0.485 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | ASIA | stack | 0.538 [0.50,0.58] | 0.511 [0.44,0.58] | - | 0.495 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | NY | stack | 0.511 [0.45,0.57] | 0.510 [0.41,0.61] | - | 0.494 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +10 | ASIA | stack | 0.531 [0.49,0.58] | 0.510 [0.43,0.58] | - | 0.500 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +30 | ASIA | rf | 0.523 [0.48,0.57] | 0.508 [0.44,0.57] | - | 0.491 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +30 | ASIA | stack | 0.534 [0.49,0.58] | 0.508 [0.44,0.57] | - | 0.492 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | POOLED | stack | 0.525 [0.50,0.56] | 0.507 [0.46,0.55] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | ASIA | logit2 | 0.504 [0.46,0.55] | 0.507 [0.44,0.57] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +10 | ASIA | stack | 0.542 [0.49,0.59] | 0.506 [0.44,0.58] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +10 | NY | stack | 0.534 [0.48,0.60] | 0.506 [0.41,0.61] | - | 0.494 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +30 | LONDON | stack | 0.561 [0.51,0.61] | 0.505 [0.42,0.58] | - | 0.474 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | LONDON | logit2 | 0.517 [0.46,0.57] | 0.505 [0.42,0.59] | - | 0.502 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | LONDON | stack | 0.548 [0.50,0.61] | 0.504 [0.42,0.58] | - | 0.469 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +10 | LONDON | stack | 0.525 [0.47,0.58] | 0.504 [0.43,0.59] | - | 0.491 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | ASIA | gbt3 | 0.524 [0.48,0.57] | 0.504 [0.45,0.56] | - | 0.489 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | POOLED | stack | 0.518 [0.49,0.55] | 0.502 [0.46,0.55] | - | 0.467 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +10 | LONDON | stack | 0.523 [0.47,0.57] | 0.501 [0.43,0.57] | - | 0.513 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +20 | ASIA | stack | 0.531 [0.49,0.57] | 0.501 [0.43,0.56] | - | 0.492 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | ASIA | stack | 0.511 [0.47,0.55] | 0.501 [0.44,0.56] | - | 0.483 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +10 | LONDON | stack | 0.482 [0.43,0.53] | 0.500 [0.43,0.57] | - | 0.507 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | NY | gbt3 | 0.531 [0.45,0.60] | 0.499 [0.40,0.61] | - | 0.492 | - | - | - | - | - | - |  | locked label (reference only) |
| B4-cond | +15 | ASIA | stack | 0.538 [0.50,0.58] | 0.499 [0.43,0.57] | - | 0.485 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +30 | ASIA | stack | 0.540 [0.50,0.58] | 0.499 [0.44,0.56] | - | 0.482 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | LONDON | stack | 0.543 [0.49,0.60] | 0.498 [0.42,0.58] | - | 0.456 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +15 | ASIA | gbt3 | 0.532 [0.48,0.58] | 0.497 [0.42,0.57] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +20 | NY | stack | 0.476 [0.41,0.54] | 0.496 [0.39,0.60] | - | 0.510 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | NY | stack | 0.522 [0.46,0.59] | 0.496 [0.37,0.61] | - | 0.488 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | ASIA | stack | 0.527 [0.48,0.57] | 0.496 [0.43,0.56] | - | 0.473 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +10 | ASIA | stack | 0.527 [0.48,0.58] | 0.495 [0.42,0.57] | - | 0.484 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +30 | NY | logit2 | 0.512 [0.45,0.57] | 0.495 [0.38,0.60] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | NY | stack | 0.514 [0.45,0.58] | 0.495 [0.36,0.62] | - | 0.456 | - | - | - | - | - | - |  | locked label (reference only) |
| B4-cond | +15 | ASIA | stack | 0.514 [0.48,0.56] | 0.494 [0.42,0.56] | - | 0.472 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +15 | LONDON | stack | 0.535 [0.49,0.59] | 0.493 [0.42,0.56] | - | 0.463 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | LONDON | stack | 0.465 [0.41,0.52] | 0.492 [0.42,0.57] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | ASIA | stack | 0.529 [0.49,0.57] | 0.490 [0.43,0.55] | - | 0.474 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | LONDON | stack | 0.528 [0.47,0.59] | 0.488 [0.41,0.57] | - | 0.457 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +30 | ASIA | gbt3 | 0.501 [0.46,0.55] | 0.488 [0.43,0.55] | - | 0.472 | - | - | - | - | - | - |  | locked label (reference only) |
| B7-cond | +15 | NY | gbt3 | 0.487 [0.41,0.56] | 0.487 [0.40,0.58] | - | 0.462 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | NY | rf | 0.514 [0.44,0.58] | 0.484 [0.39,0.58] | - | 0.466 | - | - | - | - | - | - |  | locked label (reference only) |
| B4-cond | +30 | NY | rf | 0.495 [0.42,0.57] | 0.484 [0.37,0.60] | - | 0.475 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +10 | NY | logit2 | 0.436 [0.37,0.50] | 0.484 [0.39,0.58] | - | 0.464 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +20 | ASIA | stack | 0.510 [0.47,0.55] | 0.482 [0.41,0.55] | - | 0.471 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +15 | NY | logit2 | 0.510 [0.43,0.58] | 0.481 [0.37,0.60] | - | 0.470 | - | - | - | - | - | - |  | locked label (reference only) |
| B3-cond | +15 | ASIA | stack | 0.511 [0.47,0.55] | 0.480 [0.42,0.54] | - | 0.466 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | LONDON | stack | 0.498 [0.44,0.56] | 0.480 [0.40,0.57] | - | 0.475 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +10 | NY | stack | 0.465 [0.40,0.53] | 0.478 [0.38,0.58] | - | 0.466 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +30 | NY | stack | 0.449 [0.39,0.51] | 0.478 [0.37,0.58] | - | 0.484 | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-cond | +30 | NY | stack | 0.495 [0.42,0.57] | 0.476 [0.36,0.60] | - | 0.485 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +30 | NY | stack | 0.492 [0.43,0.56] | 0.475 [0.39,0.57] | - | 0.479 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +15 | LONDON | stack | 0.447 [0.40,0.50] | 0.475 [0.40,0.55] | - | 0.456 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | NY | stack | 0.461 [0.40,0.52] | 0.475 [0.37,0.59] | - | 0.450 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +15 | NY | stack | 0.499 [0.43,0.57] | 0.470 [0.35,0.59] | - | 0.430 | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-cond | +15 | NY | rf | 0.504 [0.44,0.57] | 0.469 [0.35,0.58] | - | 0.450 | - | - | - | - | - | - |  | locked label (reference only) |
| B6-cond | +15 | LONDON | stack | 0.502 [0.45,0.55] | 0.468 [0.40,0.54] | - | 0.449 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +10 | LONDON | stack | 0.478 [0.42,0.53] | 0.468 [0.39,0.55] | - | 0.463 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +30 | LONDON | stack | 0.491 [0.44,0.54] | 0.467 [0.40,0.54] | - | 0.454 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +15 | ASIA | stack | 0.482 [0.43,0.53] | 0.467 [0.40,0.53] | - | 0.448 | - | - | - | - | - | - | stack | locked label (reference only) |
| B6-cond | +10 | NY | rf | 0.441 [0.37,0.51] | 0.466 [0.38,0.56] | - | 0.459 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | NY | logit2 | 0.496 [0.43,0.57] | 0.466 [0.37,0.56] | - | 0.474 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +10 | NY | rf | 0.468 [0.40,0.53] | 0.463 [0.36,0.55] | - | 0.443 | - | - | - | - | - | - | stack | locked label (reference only) |
| B4-cond | +15 | NY | stack | 0.533 [0.47,0.60] | 0.463 [0.35,0.58] | - | 0.438 | - | - | - | - | - | - | stack | locked label (reference only) |
| B469-cond | +10 | NY | logit2 | 0.448 [0.39,0.51] | 0.458 [0.36,0.56] | - | 0.479 | - | - | - | - | - | - |  | locked label (reference only) |
| B7-cond | +15 | NY | rf | 0.489 [0.42,0.56] | 0.456 [0.35,0.56] | - | 0.427 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +30 | NY | stack | 0.488 [0.42,0.55] | 0.450 [0.34,0.57] | - | 0.456 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | LONDON | logit2 | 0.495 [0.44,0.55] | 0.449 [0.36,0.54] | - | 0.448 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +30 | NY | stack | 0.459 [0.39,0.53] | 0.446 [0.36,0.53] | - | 0.448 | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-cond | +15 | NY | gbt3 | 0.450 [0.37,0.53] | 0.446 [0.35,0.55] | - | 0.396 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | NY | logit2 | 0.478 [0.41,0.55] | 0.445 [0.36,0.53] | - | 0.449 | - | - | - | - | - | - | stack | locked label (reference only) |
| B1-cond | +15 | NY | stack | 0.509 [0.44,0.58] | 0.444 [0.34,0.57] | - | 0.421 | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-cond | +30 | NY | stack | 0.468 [0.40,0.54] | 0.442 [0.33,0.56] | - | 0.440 | - | - | - | - | - | - | stack | locked label (reference only) |
| B9-cond | +15 | NY | stack | 0.497 [0.43,0.57] | 0.439 [0.33,0.55] | - | 0.440 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +10 | NY | logit2 | 0.432 [0.36,0.50] | 0.431 [0.34,0.53] | - | 0.437 | - | - | - | - | - | - | stack | locked label (reference only) |
| B5-cond | +30 | LONDON | stack | 0.454 [0.40,0.51] | 0.428 [0.36,0.50] | - | 0.418 | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-cond | +30 | NY | stack | 0.460 [0.39,0.54] | 0.401 [0.29,0.53] | - | 0.400 | - | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- B123-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B123-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B123-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B123-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B123-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B123-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B123-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B1-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B1-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B1-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B1-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B1-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B1-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B2-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B2-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B2-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B2-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B2-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B2-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B3-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B3-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B3-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B3-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B3-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B3-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B469-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B4-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B4-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B4-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B4-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B4-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B57-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B57-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B57-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B57-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B57-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B57-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B57-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B57-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B57-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B57-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B57-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B57-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B57-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B5-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B5-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B5-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B5-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B5-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B5-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B6-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 20 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 20 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 20 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 20 NY: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B7-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B9-cond 10 POOLED: conditional-trained; selected on conditional WF-PRE
- B9-cond 10 ASIA: conditional-trained; selected on conditional WF-PRE
- B9-cond 10 LONDON: conditional-trained; selected on conditional WF-PRE
- B9-cond 10 NY: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 NY: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 POOLED: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 ASIA: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 LONDON: conditional-trained; selected on conditional WF-PRE
- B9-cond 30 NY: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 POOLED: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 ASIA: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 LONDON: conditional-trained; selected on conditional WF-PRE
- B9-cond 15 NY: conditional-trained; selected on conditional WF-PRE
