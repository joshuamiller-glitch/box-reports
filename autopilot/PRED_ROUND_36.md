# PRED ROUND 36 - block E round 4 - conditional-label runs + conditional rescoring of rounds 1-2

Best HOLDOUT F-R AUC: +15 POOLED 0.582 [0.53,0.62] | ASIA 0.582 [0.52,0.65] | LONDON 0.631 [0.57,0.70] | NY 0.603 [0.51,0.69]
Best HOLDOUT F-R AUC: +30 POOLED 0.579 [0.53,0.63] | ASIA 0.601 [0.53,0.66] | LONDON 0.602 [0.53,0.68] | NY 0.577 [0.49,0.66]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 5b827a61b4340360ef379bbe6484ebf21c3b5ce21ec3ac5eda99d5b93965fd72 ; trials added 1000 ; truncation audit {'decisions': 720, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E1.parquet', 'l2vast/pred/store/E2.parquet', 'l2vast/pred/store/E3.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E8-12-all-condrescore | +45 | LONDON | stack | 0.584 [0.53,0.64] | 0.651 [0.58,0.71] | - | 0.635 | 0.655 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +20 | LONDON | gbt3 | 0.576 [0.52,0.63] | 0.635 [0.56,0.70] | - | 0.626 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +15 | LONDON | gbt3 | 0.585 [0.54,0.63] | 0.631 [0.57,0.70] | - | 0.609 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +20 | LONDON | rf | 0.574 [0.52,0.63] | 0.622 [0.54,0.70] | - | 0.597 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +15 | LONDON | stack | 0.562 [0.52,0.61] | 0.618 [0.55,0.69] | - | 0.606 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +60 | LONDON | logit2 | 0.517 [0.47,0.57] | 0.616 [0.55,0.68] | - | 0.614 | 0.616 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +5 | NY | gbt3 | 0.541 [0.48,0.60] | 0.614 [0.53,0.71] | - | 0.642 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +20 | LONDON | gbt3 | 0.566 [0.51,0.62] | 0.610 [0.53,0.69] | - | 0.593 | 0.608 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +15 | LONDON | stack | 0.565 [0.51,0.62] | 0.610 [0.54,0.68] | - | 0.593 | 0.600 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +15 | LONDON | gbt3 | 0.559 [0.51,0.61] | 0.606 [0.52,0.68] | - | 0.603 | 0.593 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +60 | LONDON | logit2 | 0.540 [0.49,0.59] | 0.605 [0.54,0.67] | - | 0.585 | 0.638 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +15 | NY | logit2 | 0.566 [0.51,0.63] | 0.603 [0.51,0.69] | - | 0.592 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Erates-condrescore | +30 | LONDON | rf | 0.567 [0.52,0.62] | 0.602 [0.53,0.68] | - | 0.585 | 0.591 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +30 | ASIA | stack | 0.575 [0.53,0.62] | 0.601 [0.53,0.66] | - | 0.588 | 0.586 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +15 | LONDON | rf | 0.511 [0.45,0.57] | 0.600 [0.53,0.67] | - | 0.555 | 0.620 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +15 | LONDON | logit2 | 0.570 [0.52,0.62] | 0.599 [0.52,0.67] | - | 0.586 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +30 | LONDON | logit2 | 0.540 [0.49,0.60] | 0.598 [0.52,0.66] | - | 0.575 | 0.590 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +20 | LONDON | logit2 | 0.530 [0.48,0.58] | 0.596 [0.52,0.67] | - | 0.594 | 0.577 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +30 | LONDON | stack | 0.546 [0.48,0.60] | 0.594 [0.52,0.66] | - | 0.542 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +10 | POOLED | rf | 0.558 [0.53,0.59] | 0.594 [0.55,0.63] | - | 0.571 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +20 | LONDON | logit2 | 0.518 [0.47,0.57] | 0.593 [0.52,0.67] | - | 0.577 | 0.620 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +45 | ASIA | stack | 0.565 [0.51,0.62] | 0.593 [0.52,0.66] | - | 0.580 | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +15 | LONDON | gbt3 | 0.590 [0.54,0.64] | 0.593 [0.52,0.66] | - | 0.600 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +10 | LONDON | gbt3 | 0.551 [0.50,0.61] | 0.592 [0.52,0.67] | - | 0.568 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +5 | LONDON | gbt3 | 0.543 [0.48,0.60] | 0.589 [0.50,0.67] | - | 0.555 | 0.595 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc-condrescore | +15 | LONDON | gbt3 | 0.539 [0.49,0.59] | 0.589 [0.53,0.65] | - | 0.573 | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +20 | LONDON | logit2 | 0.533 [0.48,0.58] | 0.587 [0.51,0.66] | - | 0.573 | 0.613 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +20 | LONDON | logit2 | 0.546 [0.50,0.60] | 0.586 [0.51,0.67] | - | 0.548 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +15 | LONDON | logit2 | 0.550 [0.50,0.60] | 0.586 [0.51,0.66] | - | 0.584 | 0.609 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +10 | POOLED | rf | 0.546 [0.52,0.58] | 0.585 [0.54,0.63] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E12-condrescore | +15 | NY | logit2 | 0.514 [0.44,0.58] | 0.585 [0.47,0.69] | - | 0.594 | 0.585 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc-condrescore | +30 | LONDON | logit2 | 0.511 [0.46,0.56] | 0.583 [0.51,0.66] | - | 0.568 | 0.585 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx-condrescore | +30 | ASIA | rf | 0.574 [0.53,0.62] | 0.582 [0.51,0.65] | - | 0.572 | 0.573 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +15 | POOLED | stack | 0.566 [0.54,0.60] | 0.582 [0.53,0.62] | - | 0.570 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +15 | LONDON | logit2 | 0.537 [0.48,0.59] | 0.582 [0.51,0.66] | - | 0.577 | 0.608 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +15 | ASIA | rf | 0.547 [0.50,0.59] | 0.582 [0.52,0.65] | - | 0.576 | 0.583 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +30 | ASIA | rf | 0.583 [0.54,0.63] | 0.580 [0.51,0.65] | - | 0.570 | 0.574 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +20 | POOLED | logit2 | 0.553 [0.52,0.59] | 0.579 [0.53,0.63] | - | 0.562 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +15 | LONDON | logit2 | 0.551 [0.50,0.61] | 0.579 [0.50,0.65] | - | 0.572 | 0.573 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +30 | POOLED | rf | 0.548 [0.51,0.58] | 0.579 [0.53,0.63] | - | 0.555 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +30 | POOLED | logit2 | 0.541 [0.51,0.57] | 0.579 [0.54,0.62] | - | 0.565 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +20 | POOLED | rf | 0.560 [0.53,0.59] | 0.579 [0.53,0.62] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9-condrescore | +30 | LONDON | gbt3 | 0.513 [0.46,0.57] | 0.579 [0.49,0.65] | - | 0.535 | 0.585 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +15 | POOLED | rf | 0.556 [0.53,0.59] | 0.578 [0.53,0.62] | - | 0.557 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E12-condrescore | +30 | NY | gbt3 | 0.533 [0.47,0.59] | 0.577 [0.49,0.66] | - | 0.571 | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +45 | LONDON | stack | 0.541 [0.49,0.60] | 0.576 [0.50,0.66] | - | 0.553 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +10 | ASIA | logit2 | 0.524 [0.48,0.57] | 0.576 [0.50,0.65] | - | 0.559 | 0.558 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +5 | POOLED | rf | 0.544 [0.52,0.57] | 0.576 [0.53,0.62] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +10 | LONDON | stack | 0.544 [0.49,0.60] | 0.575 [0.50,0.64] | - | 0.556 | 0.569 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +60 | ASIA | rf | 0.522 [0.47,0.57] | 0.575 [0.50,0.64] | - | 0.580 | 0.568 | - | - | - | - | - | stack | locked label (reference only) |
| C0-pertype | +15 | POOLED | stack | 0.561 [0.53,0.59] | 0.575 [0.53,0.61] | - | 0.560 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Efx-condrescore | +30 | ASIA | logit2 | 0.548 [0.50,0.60] | 0.575 [0.50,0.64] | - | 0.574 | 0.566 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +5 | POOLED | rf | 0.549 [0.52,0.58] | 0.575 [0.53,0.62] | - | 0.559 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +30 | LONDON | stack | 0.564 [0.51,0.62] | 0.574 [0.50,0.65] | - | 0.533 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +60 | LONDON | logit2 | 0.531 [0.48,0.58] | 0.573 [0.50,0.64] | - | 0.576 | 0.604 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +5 | POOLED | rf | 0.527 [0.49,0.56] | 0.572 [0.53,0.62] | - | 0.550 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +45 | POOLED | rf | 0.551 [0.52,0.58] | 0.572 [0.53,0.61] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +60 | LONDON | gbt3 | 0.536 [0.48,0.59] | 0.571 [0.50,0.64] | - | 0.571 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +30 | ASIA | gbt3 | 0.552 [0.51,0.60] | 0.571 [0.50,0.64] | - | 0.567 | 0.561 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-cond-trained | +15 | LONDON | stack | 0.557 [0.50,0.61] | 0.570 [0.50,0.64] | - | 0.540 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +60 | LONDON | logit2 | 0.540 [0.49,0.59] | 0.568 [0.50,0.63] | - | 0.557 | 0.608 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +15 | POOLED | gbt3 | 0.559 [0.53,0.59] | 0.568 [0.53,0.61] | - | 0.552 | - | - | - | - | - | - |  | locked label (reference only) |
| C0-pertype | +15 | LONDON | gbt3 | 0.558 [0.51,0.60] | 0.568 [0.49,0.63] | - | 0.600 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | pre | POOLED | rf | 0.545 [0.51,0.57] | 0.567 [0.52,0.61] | - | 0.550 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +45 | LONDON | logit2 | 0.515 [0.46,0.57] | 0.567 [0.50,0.63] | - | 0.543 | 0.598 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | pre | POOLED | stack | 0.544 [0.51,0.57] | 0.566 [0.53,0.61] | - | 0.541 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +30 | POOLED | stack | 0.561 [0.53,0.59] | 0.566 [0.52,0.61] | - | 0.544 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +60 | NY | logit2 | 0.556 [0.49,0.63] | 0.564 [0.47,0.66] | - | 0.570 | 0.659 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +10 | LONDON | logit2 | 0.536 [0.49,0.59] | 0.563 [0.49,0.64] | - | 0.562 | 0.596 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-cond-trained | +15 | ASIA | gbt3 | 0.565 [0.52,0.61] | 0.563 [0.50,0.63] | - | 0.566 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +45 | LONDON | stack | 0.573 [0.52,0.62] | 0.563 [0.50,0.63] | - | 0.536 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-cond-trained | +30 | LONDON | stack | 0.572 [0.52,0.62] | 0.563 [0.49,0.63] | - | 0.529 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +20 | ASIA | stack | 0.561 [0.52,0.60] | 0.563 [0.50,0.62] | - | 0.559 | 0.557 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +10 | LONDON | logit2 | 0.546 [0.50,0.60] | 0.563 [0.49,0.64] | - | 0.566 | 0.596 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +10 | ASIA | rf | 0.558 [0.52,0.60] | 0.563 [0.50,0.62] | - | 0.548 | 0.560 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +20 | POOLED | rf | 0.565 [0.53,0.60] | 0.562 [0.52,0.61] | - | 0.548 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9-condrescore | +15 | LONDON | gbt3 | 0.508 [0.46,0.57] | 0.562 [0.49,0.64] | - | 0.534 | 0.583 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +10 | POOLED | logit2 | 0.546 [0.52,0.58] | 0.561 [0.51,0.61] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-cond-trained | +15 | POOLED | stack | 0.559 [0.53,0.59] | 0.561 [0.52,0.61] | - | 0.547 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +15 | ASIA | rf | 0.549 [0.50,0.59] | 0.561 [0.50,0.63] | - | 0.557 | 0.555 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +45 | POOLED | rf | 0.553 [0.53,0.58] | 0.561 [0.52,0.60] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-cond-trained | +15 | POOLED | logit2 | 0.552 [0.52,0.58] | 0.560 [0.51,0.61] | - | 0.554 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11-condrescore | +15 | NY | logit2 | 0.563 [0.50,0.63] | 0.560 [0.46,0.66] | - | 0.571 | 0.594 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9-condrescore | +15 | ASIA | stack | 0.571 [0.53,0.61] | 0.560 [0.50,0.63] | - | 0.565 | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +15 | ASIA | gbt3 | 0.549 [0.51,0.59] | 0.560 [0.50,0.62] | - | 0.557 | 0.557 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +10 | ASIA | stack | 0.552 [0.51,0.59] | 0.560 [0.49,0.63] | - | 0.544 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +45 | ASIA | stack | 0.548 [0.50,0.59] | 0.559 [0.49,0.62] | - | 0.553 | 0.548 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +60 | POOLED | rf | 0.541 [0.51,0.57] | 0.559 [0.52,0.60] | - | 0.550 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +45 | POOLED | stack | 0.544 [0.51,0.58] | 0.558 [0.51,0.60] | - | 0.550 | 0.642 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +45 | NY | gbt3 | 0.526 [0.46,0.59] | 0.557 [0.45,0.66] | - | 0.558 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +5 | LONDON | rf | 0.538 [0.49,0.59] | 0.557 [0.49,0.62] | - | 0.546 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc-condrescore | +15 | ASIA | logit2 | 0.581 [0.54,0.63] | 0.557 [0.50,0.62] | - | 0.553 | 0.541 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +30 | ASIA | logit2 | 0.562 [0.52,0.60] | 0.557 [0.50,0.61] | - | 0.551 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +60 | POOLED | logit2 | 0.517 [0.48,0.55] | 0.557 [0.51,0.60] | - | 0.558 | 0.659 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +60 | ASIA | gbt3 | 0.532 [0.48,0.57] | 0.556 [0.49,0.62] | - | 0.553 | 0.557 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +15 | ASIA | logit2 | 0.560 [0.52,0.59] | 0.556 [0.50,0.62] | - | 0.545 | 0.556 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-cond-trained | +30 | POOLED | rf | 0.551 [0.52,0.58] | 0.556 [0.50,0.61] | - | 0.547 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +5 | LONDON | gbt3 | 0.516 [0.47,0.57] | 0.555 [0.49,0.62] | - | 0.539 | 0.593 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | pre | ASIA | rf | 0.546 [0.50,0.59] | 0.555 [0.49,0.63] | - | 0.538 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +60 | POOLED | gbt3 | 0.539 [0.51,0.57] | 0.555 [0.51,0.60] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | pre | POOLED | logit2 | 0.535 [0.50,0.56] | 0.555 [0.51,0.60] | - | 0.552 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +30 | POOLED | stack | 0.560 [0.53,0.59] | 0.554 [0.51,0.60] | - | 0.526 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | pre | LONDON | stack | 0.534 [0.48,0.59] | 0.554 [0.48,0.62] | - | 0.553 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +60 | POOLED | gbt3 | 0.535 [0.51,0.57] | 0.553 [0.51,0.60] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-cond-trained | +15 | LONDON | rf | 0.541 [0.48,0.60] | 0.553 [0.48,0.64] | - | 0.562 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +45 | POOLED | rf | 0.529 [0.50,0.56] | 0.553 [0.50,0.60] | - | 0.548 | 0.657 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +45 | LONDON | gbt3 | 0.505 [0.45,0.56] | 0.552 [0.49,0.62] | - | 0.550 | 0.574 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eidx-condrescore | +30 | LONDON | gbt3 | 0.537 [0.48,0.59] | 0.552 [0.48,0.63] | - | 0.535 | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +30 | POOLED | rf | 0.524 [0.50,0.55] | 0.551 [0.51,0.59] | - | 0.545 | 0.668 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +30 | LONDON | logit2 | 0.531 [0.48,0.58] | 0.551 [0.47,0.63] | - | 0.517 | 0.593 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +30 | POOLED | rf | 0.524 [0.50,0.55] | 0.551 [0.51,0.59] | - | 0.537 | 0.652 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +10 | LONDON | rf | 0.534 [0.48,0.59] | 0.551 [0.47,0.63] | - | 0.541 | 0.579 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +5 | ASIA | rf | 0.526 [0.48,0.57] | 0.550 [0.49,0.60] | - | 0.547 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +10 | ASIA | rf | 0.531 [0.48,0.58] | 0.550 [0.48,0.63] | - | 0.541 | 0.550 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8-condrescore | +15 | NY | logit2 | 0.536 [0.47,0.60] | 0.549 [0.45,0.64] | - | 0.597 | 0.593 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +15 | POOLED | logit2 | 0.542 [0.51,0.57] | 0.548 [0.50,0.59] | - | 0.530 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +30 | LONDON | gbt3 | 0.544 [0.49,0.60] | 0.547 [0.47,0.63] | - | 0.520 | 0.595 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +30 | LONDON | logit2 | 0.546 [0.50,0.60] | 0.547 [0.47,0.62] | - | 0.517 | 0.592 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +60 | NY | gbt3 | 0.546 [0.48,0.62] | 0.547 [0.44,0.66] | - | 0.547 | 0.722 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +30 | ASIA | stack | 0.531 [0.49,0.58] | 0.546 [0.48,0.61] | - | 0.534 | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +5 | ASIA | rf | 0.525 [0.48,0.57] | 0.546 [0.48,0.61] | - | 0.534 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +15 | POOLED | stack | 0.538 [0.51,0.57] | 0.545 [0.50,0.59] | - | 0.524 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | pre | ASIA | logit2 | 0.536 [0.49,0.58] | 0.545 [0.49,0.61] | - | 0.531 | 0.541 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +60 | NY | gbt3 | 0.523 [0.45,0.60] | 0.544 [0.44,0.66] | - | 0.547 | 0.734 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +45 | ASIA | gbt3 | 0.541 [0.49,0.58] | 0.544 [0.47,0.61] | - | 0.545 | 0.531 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | pre | ASIA | logit2 | 0.529 [0.49,0.57] | 0.544 [0.48,0.60] | - | 0.531 | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +30 | POOLED | rf | 0.517 [0.49,0.55] | 0.543 [0.50,0.58] | - | 0.539 | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecmd-condrescore | +30 | LONDON | gbt3 | 0.520 [0.47,0.58] | 0.543 [0.46,0.62] | - | 0.548 | 0.592 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +15 | NY | logit2 | 0.532 [0.47,0.59] | 0.543 [0.44,0.63] | - | 0.555 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10-condrescore | +30 | NY | gbt3 | 0.512 [0.44,0.58] | 0.543 [0.45,0.63] | - | 0.532 | 0.623 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +30 | ASIA | logit2 | 0.547 [0.51,0.59] | 0.542 [0.47,0.61] | - | 0.539 | 0.526 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +20 | NY | logit2 | 0.501 [0.43,0.58] | 0.541 [0.44,0.64] | - | 0.546 | 0.641 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +30 | ASIA | stack | 0.551 [0.50,0.60] | 0.541 [0.47,0.61] | - | 0.530 | 0.532 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | pre | LONDON | stack | 0.574 [0.53,0.63] | 0.541 [0.46,0.62] | - | 0.524 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +5 | LONDON | rf | 0.512 [0.46,0.56] | 0.540 [0.46,0.62] | - | 0.539 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +20 | POOLED | rf | 0.513 [0.49,0.54] | 0.539 [0.50,0.58] | - | 0.532 | 0.638 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx-condrescore | +30 | LONDON | rf | 0.535 [0.48,0.60] | 0.539 [0.46,0.62] | - | 0.543 | 0.564 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +20 | NY | rf | 0.506 [0.43,0.57] | 0.539 [0.43,0.64] | - | 0.518 | 0.665 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +15 | POOLED | logit2 | 0.524 [0.49,0.55] | 0.538 [0.50,0.58] | - | 0.528 | 0.614 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +30 | NY | logit2 | 0.525 [0.46,0.59] | 0.538 [0.44,0.63] | - | 0.552 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eidx-condrescore | +15 | LONDON | stack | 0.506 [0.46,0.56] | 0.538 [0.46,0.60] | - | 0.508 | 0.577 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +30 | LONDON | stack | 0.545 [0.49,0.60] | 0.538 [0.46,0.62] | - | 0.546 | 0.506 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +5 | ASIA | rf | 0.540 [0.49,0.59] | 0.537 [0.47,0.60] | - | 0.523 | 0.536 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Exc-condrescore | +30 | POOLED | logit2 | 0.528 [0.50,0.56] | 0.537 [0.49,0.59] | - | 0.530 | 0.617 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm-condrescore | +15 | ASIA | gbt3 | 0.534 [0.49,0.58] | 0.537 [0.47,0.60] | - | 0.527 | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd-condrescore | +15 | LONDON | gbt3 | 0.512 [0.46,0.57] | 0.537 [0.46,0.62] | - | 0.518 | 0.573 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +60 | ASIA | gbt3 | 0.526 [0.48,0.57] | 0.537 [0.48,0.60] | - | 0.524 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +15 | POOLED | logit2 | 0.525 [0.50,0.55] | 0.536 [0.49,0.58] | - | 0.526 | 0.615 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +30 | NY | logit2 | 0.509 [0.44,0.58] | 0.536 [0.43,0.65] | - | 0.567 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10-condrescore | +30 | ASIA | gbt3 | 0.531 [0.49,0.58] | 0.535 [0.47,0.60] | - | 0.527 | 0.527 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +60 | ASIA | gbt3 | 0.535 [0.49,0.58] | 0.534 [0.47,0.61] | - | 0.521 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +15 | NY | logit2 | 0.491 [0.42,0.56] | 0.534 [0.43,0.64] | - | 0.539 | 0.625 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +15 | ASIA | rf | 0.525 [0.48,0.57] | 0.534 [0.47,0.60] | - | 0.525 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +15 | LONDON | stack | 0.535 [0.48,0.59] | 0.534 [0.45,0.61] | - | 0.531 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +30 | ASIA | rf | 0.541 [0.50,0.58] | 0.534 [0.47,0.60] | - | 0.514 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +45 | NY | gbt3 | 0.533 [0.47,0.60] | 0.533 [0.42,0.64] | - | 0.519 | 0.636 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +45 | POOLED | gbt3 | 0.521 [0.49,0.55] | 0.533 [0.49,0.57] | - | 0.524 | 0.633 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +45 | ASIA | rf | 0.534 [0.49,0.57] | 0.533 [0.47,0.60] | - | 0.510 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +15 | LONDON | stack | 0.517 [0.47,0.57] | 0.533 [0.46,0.61] | - | 0.512 | 0.508 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +20 | ASIA | rf | 0.548 [0.50,0.59] | 0.533 [0.46,0.60] | - | 0.520 | 0.520 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +15 | NY | stack | 0.527 [0.46,0.59] | 0.532 [0.42,0.64] | - | 0.512 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecot-condrescore | +15 | LONDON | logit2 | 0.510 [0.46,0.57] | 0.532 [0.45,0.62] | - | 0.519 | 0.528 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +45 | POOLED | gbt3 | 0.520 [0.49,0.55] | 0.532 [0.49,0.57] | - | 0.533 | 0.633 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +10 | LONDON | stack | 0.501 [0.44,0.56] | 0.531 [0.45,0.61] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | pre | LONDON | stack | 0.529 [0.48,0.58] | 0.531 [0.44,0.62] | - | 0.508 | 0.544 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx-condrescore | +15 | ASIA | logit2 | 0.551 [0.51,0.59] | 0.531 [0.47,0.59] | - | 0.522 | 0.518 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +20 | NY | gbt3 | 0.517 [0.45,0.58] | 0.531 [0.44,0.63] | - | 0.510 | 0.670 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +60 | LONDON | gbt3 | 0.526 [0.47,0.57] | 0.531 [0.46,0.60] | - | 0.546 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +30 | NY | gbt3 | 0.508 [0.43,0.58] | 0.531 [0.42,0.64] | - | 0.549 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc-condrescore | +30 | NY | logit2 | 0.535 [0.47,0.60] | 0.531 [0.43,0.63] | - | 0.505 | 0.626 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +30 | ASIA | stack | 0.529 [0.48,0.58] | 0.530 [0.46,0.59] | - | 0.516 | 0.527 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-pertype | +30 | POOLED | rf | 0.526 [0.50,0.56] | 0.530 [0.48,0.58] | - | 0.504 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +20 | POOLED | rf | 0.502 [0.47,0.53] | 0.530 [0.49,0.57] | - | 0.521 | 0.654 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +45 | NY | rf | 0.525 [0.45,0.59] | 0.530 [0.42,0.64] | - | 0.519 | 0.631 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | pre | ASIA | rf | 0.526 [0.48,0.57] | 0.530 [0.47,0.59] | - | 0.518 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-pertype | +30 | POOLED | logit2 | 0.524 [0.49,0.55] | 0.529 [0.49,0.57] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-cond-trained | +30 | NY | gbt3 | 0.551 [0.47,0.63] | 0.528 [0.43,0.63] | - | 0.539 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +15 | ASIA | gbt3 | 0.531 [0.49,0.57] | 0.528 [0.46,0.60] | - | 0.520 | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +45 | POOLED | logit2 | 0.537 [0.51,0.57] | 0.528 [0.48,0.57] | - | 0.532 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +20 | ASIA | stack | 0.540 [0.49,0.59] | 0.528 [0.46,0.60] | - | 0.528 | 0.517 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +30 | POOLED | gbt3 | 0.528 [0.50,0.56] | 0.527 [0.48,0.57] | - | 0.520 | 0.626 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx-condrescore | +30 | POOLED | gbt3 | 0.517 [0.49,0.55] | 0.527 [0.49,0.56] | - | 0.525 | 0.625 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +5 | ASIA | stack | 0.543 [0.50,0.59] | 0.527 [0.46,0.59] | - | 0.513 | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +15 | NY | logit2 | 0.514 [0.45,0.57] | 0.526 [0.44,0.63] | - | 0.543 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +45 | LONDON | stack | 0.561 [0.51,0.61] | 0.526 [0.46,0.60] | - | 0.532 | - | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +10 | LONDON | logit2 | 0.491 [0.43,0.55] | 0.526 [0.44,0.61] | - | 0.533 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | pre | ASIA | gbt3 | 0.530 [0.49,0.57] | 0.526 [0.47,0.58] | - | 0.516 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm-condrescore | +30 | NY | rf | 0.516 [0.44,0.59] | 0.525 [0.42,0.63] | - | 0.514 | 0.520 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +15 | NY | rf | 0.497 [0.43,0.57] | 0.525 [0.42,0.63] | - | 0.489 | 0.665 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +15 | ASIA | stack | 0.548 [0.50,0.59] | 0.524 [0.47,0.58] | - | 0.515 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +15 | POOLED | rf | 0.501 [0.47,0.53] | 0.524 [0.48,0.56] | - | 0.508 | 0.650 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm-condrescore | +15 | LONDON | rf | 0.523 [0.47,0.57] | 0.523 [0.44,0.60] | - | 0.478 | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +10 | NY | gbt3 | 0.522 [0.46,0.58] | 0.523 [0.42,0.62] | - | 0.581 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +45 | LONDON | gbt3 | 0.490 [0.44,0.54] | 0.523 [0.45,0.60] | - | 0.528 | 0.559 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecot-condrescore | +30 | ASIA | stack | 0.536 [0.49,0.58] | 0.523 [0.46,0.59] | - | 0.519 | 0.529 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +30 | ASIA | stack | 0.531 [0.49,0.57] | 0.523 [0.46,0.59] | - | 0.489 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +20 | POOLED | gbt3 | 0.514 [0.48,0.54] | 0.523 [0.48,0.57] | - | 0.521 | 0.629 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12-condrescore | +30 | ASIA | logit2 | 0.528 [0.48,0.58] | 0.522 [0.45,0.59] | - | 0.520 | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +5 | NY | gbt3 | 0.514 [0.45,0.58] | 0.522 [0.41,0.64] | - | 0.561 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +15 | POOLED | gbt3 | 0.501 [0.47,0.53] | 0.522 [0.48,0.56] | - | 0.508 | 0.631 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +15 | NY | logit2 | 0.512 [0.44,0.58] | 0.522 [0.41,0.63] | - | 0.504 | 0.628 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Exc-condrescore | +15 | POOLED | stack | 0.530 [0.50,0.56] | 0.522 [0.48,0.56] | - | 0.523 | 0.622 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +45 | ASIA | rf | 0.549 [0.51,0.59] | 0.521 [0.47,0.59] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +45 | ASIA | gbt3 | 0.534 [0.48,0.58] | 0.521 [0.45,0.59] | - | 0.506 | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-cond-trained | +15 | ASIA | stack | 0.557 [0.51,0.60] | 0.520 [0.45,0.59] | - | 0.513 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +20 | POOLED | stack | 0.505 [0.47,0.53] | 0.520 [0.48,0.56] | - | 0.515 | 0.647 | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +20 | ASIA | stack | 0.528 [0.49,0.57] | 0.520 [0.46,0.58] | - | 0.511 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +5 | ASIA | stack | 0.527 [0.48,0.57] | 0.519 [0.46,0.58] | - | 0.519 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +45 | NY | gbt3 | 0.514 [0.44,0.59] | 0.519 [0.41,0.63] | - | 0.534 | 0.662 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +60 | POOLED | logit2 | 0.493 [0.46,0.52] | 0.519 [0.47,0.56] | - | 0.518 | 0.648 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Exc-condrescore | +15 | NY | rf | 0.505 [0.43,0.57] | 0.519 [0.41,0.63] | - | 0.504 | 0.588 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +15 | POOLED | logit2 | 0.491 [0.46,0.52] | 0.519 [0.47,0.56] | - | 0.519 | 0.624 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Exc-condrescore | +30 | ASIA | rf | 0.557 [0.52,0.60] | 0.519 [0.46,0.58] | - | 0.510 | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-cond-trained | +30 | LONDON | rf | 0.529 [0.47,0.58] | 0.518 [0.43,0.61] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +15 | POOLED | stack | 0.511 [0.48,0.54] | 0.518 [0.47,0.56] | - | 0.515 | 0.615 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-cond-trained | +30 | ASIA | stack | 0.538 [0.49,0.58] | 0.518 [0.45,0.59] | - | 0.496 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot-condrescore | +15 | ASIA | rf | 0.542 [0.50,0.58] | 0.516 [0.46,0.57] | - | 0.516 | 0.520 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +45 | ASIA | rf | 0.529 [0.49,0.57] | 0.516 [0.46,0.58] | - | 0.506 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +60 | ASIA | stack | 0.520 [0.48,0.56] | 0.516 [0.46,0.58] | - | 0.491 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +45 | NY | rf | 0.511 [0.44,0.58] | 0.515 [0.41,0.62] | - | 0.497 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9-condrescore | +30 | NY | logit2 | 0.495 [0.43,0.57] | 0.515 [0.41,0.63] | - | 0.517 | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +30 | POOLED | rf | 0.507 [0.48,0.54] | 0.515 [0.48,0.56] | - | 0.514 | 0.615 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | pre | ASIA | gbt3 | 0.564 [0.52,0.61] | 0.515 [0.45,0.59] | - | 0.509 | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +30 | NY | rf | 0.504 [0.43,0.58] | 0.514 [0.41,0.61] | - | 0.502 | 0.672 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +30 | NY | gbt3 | 0.501 [0.43,0.58] | 0.513 [0.41,0.61] | - | 0.506 | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +20 | ASIA | stack | 0.524 [0.48,0.57] | 0.513 [0.44,0.58] | - | 0.513 | 0.503 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | pre | NY | logit2 | 0.500 [0.43,0.57] | 0.512 [0.41,0.61] | - | 0.533 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11-condrescore | +30 | LONDON | gbt3 | 0.524 [0.46,0.58] | 0.512 [0.42,0.60] | - | 0.506 | 0.491 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | pre | LONDON | gbt3 | 0.521 [0.47,0.57] | 0.511 [0.42,0.59] | - | 0.495 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecot-condrescore | +15 | NY | gbt3 | 0.552 [0.49,0.61] | 0.511 [0.41,0.61] | - | 0.513 | 0.574 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +60 | POOLED | logit2 | 0.492 [0.46,0.52] | 0.511 [0.46,0.56] | - | 0.516 | 0.645 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8-condrescore | +15 | LONDON | gbt3 | 0.519 [0.47,0.57] | 0.511 [0.44,0.59] | - | 0.519 | 0.531 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-cond-trained | +30 | POOLED | logit2 | 0.524 [0.49,0.56] | 0.509 [0.46,0.56] | - | 0.497 | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +60 | POOLED | stack | 0.507 [0.48,0.54] | 0.508 [0.47,0.54] | - | 0.500 | 0.602 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +15 | ASIA | rf | 0.509 [0.47,0.55] | 0.508 [0.45,0.57] | - | 0.491 | - | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +60 | NY | rf | 0.526 [0.45,0.60] | 0.507 [0.40,0.61] | - | 0.509 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-pertype | +30 | ASIA | rf | 0.517 [0.47,0.56] | 0.507 [0.45,0.56] | - | 0.480 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +30 | LONDON | logit2 | 0.529 [0.47,0.58] | 0.506 [0.44,0.58] | - | 0.508 | 0.560 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9-condrescore | +15 | POOLED | stack | 0.508 [0.48,0.54] | 0.506 [0.46,0.55] | - | 0.508 | 0.619 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm-condrescore | +15 | POOLED | gbt3 | 0.500 [0.47,0.53] | 0.506 [0.46,0.55] | - | 0.496 | 0.568 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx-condrescore | +30 | POOLED | gbt3 | 0.495 [0.46,0.53] | 0.506 [0.46,0.55] | - | 0.507 | 0.580 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +10 | ASIA | rf | 0.518 [0.47,0.56] | 0.506 [0.45,0.57] | - | 0.493 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11-condrescore | +30 | NY | logit2 | 0.513 [0.45,0.58] | 0.506 [0.41,0.61] | - | 0.492 | 0.584 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +45 | NY | stack | 0.533 [0.46,0.60] | 0.505 [0.41,0.60] | - | 0.541 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10-condrescore | +15 | ASIA | gbt3 | 0.522 [0.48,0.56] | 0.505 [0.45,0.56] | - | 0.489 | 0.496 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm-condrescore | +15 | NY | rf | 0.531 [0.46,0.60] | 0.504 [0.40,0.61] | - | 0.524 | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx-condrescore | +15 | LONDON | stack | 0.515 [0.45,0.57] | 0.504 [0.42,0.58] | - | 0.513 | 0.506 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +30 | ASIA | logit2 | 0.514 [0.47,0.56] | 0.504 [0.44,0.57] | - | 0.484 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +20 | ASIA | gbt3 | 0.503 [0.45,0.55] | 0.503 [0.43,0.57] | - | 0.492 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10-condrescore | +30 | POOLED | stack | 0.507 [0.47,0.54] | 0.503 [0.46,0.55] | - | 0.489 | 0.608 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +30 | NY | rf | 0.529 [0.46,0.60] | 0.503 [0.40,0.61] | - | 0.489 | 0.544 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot-condrescore | +15 | POOLED | logit2 | 0.507 [0.48,0.54] | 0.502 [0.46,0.55] | - | 0.486 | 0.559 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +5 | LONDON | logit2 | 0.512 [0.47,0.56] | 0.502 [0.44,0.57] | - | 0.509 | 0.577 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecmd-condrescore | +30 | ASIA | logit2 | 0.517 [0.47,0.56] | 0.502 [0.44,0.56] | - | 0.495 | 0.483 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +30 | POOLED | logit2 | 0.501 [0.47,0.53] | 0.501 [0.46,0.54] | - | 0.503 | 0.623 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9-condrescore | +30 | ASIA | stack | 0.534 [0.49,0.58] | 0.501 [0.44,0.56] | - | 0.513 | 0.492 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9-condrescore | +30 | POOLED | logit2 | 0.493 [0.46,0.52] | 0.501 [0.46,0.54] | - | 0.490 | 0.601 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +20 | NY | rf | 0.534 [0.47,0.60] | 0.501 [0.39,0.61] | - | 0.487 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8-condrescore | +15 | POOLED | gbt3 | 0.501 [0.47,0.53] | 0.500 [0.46,0.54] | - | 0.494 | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12-condrescore | +15 | ASIA | logit2 | 0.512 [0.47,0.55] | 0.500 [0.43,0.57] | - | 0.498 | 0.500 | - | - | - | - | - |  | locked label (reference only) |
| C0-pertype | +30 | LONDON | logit2 | 0.510 [0.45,0.57] | 0.499 [0.41,0.59] | - | 0.496 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10-condrescore | +30 | LONDON | stack | 0.521 [0.47,0.58] | 0.499 [0.42,0.58] | - | 0.463 | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +15 | POOLED | stack | 0.493 [0.47,0.52] | 0.499 [0.46,0.55] | - | 0.492 | 0.613 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot-condrescore | +30 | POOLED | logit2 | 0.505 [0.47,0.54] | 0.499 [0.45,0.54] | - | 0.489 | 0.565 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +10 | POOLED | logit2 | 0.482 [0.46,0.51] | 0.499 [0.45,0.55] | - | 0.492 | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm-condrescore | +30 | LONDON | gbt3 | 0.508 [0.46,0.56] | 0.499 [0.42,0.57] | - | 0.479 | 0.490 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-cond-trained | +30 | NY | rf | 0.528 [0.45,0.60] | 0.499 [0.39,0.60] | - | 0.509 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-cond-trained | +15 | NY | logit2 | 0.498 [0.43,0.57] | 0.498 [0.40,0.59] | - | 0.498 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +60 | ASIA | logit2 | 0.489 [0.44,0.54] | 0.497 [0.43,0.57] | - | 0.496 | 0.488 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +10 | NY | rf | 0.515 [0.45,0.57] | 0.497 [0.39,0.59] | - | 0.505 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +30 | ASIA | logit2 | 0.521 [0.48,0.56] | 0.497 [0.43,0.56] | - | 0.501 | 0.502 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10-condrescore | +15 | LONDON | stack | 0.532 [0.48,0.58] | 0.497 [0.42,0.57] | - | 0.482 | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +5 | ASIA | gbt3 | 0.513 [0.47,0.55] | 0.497 [0.45,0.55] | - | 0.488 | 0.498 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +30 | ASIA | stack | 0.529 [0.48,0.57] | 0.497 [0.44,0.56] | - | 0.478 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17+base-cond-trained | +15 | ASIA | rf | 0.515 [0.47,0.56] | 0.496 [0.44,0.56] | - | 0.480 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eidx-condrescore | +15 | POOLED | stack | 0.495 [0.46,0.53] | 0.496 [0.45,0.54] | - | 0.484 | 0.600 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +10 | NY | rf | 0.489 [0.42,0.56] | 0.496 [0.40,0.60] | - | 0.526 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +15 | ASIA | stack | 0.525 [0.48,0.57] | 0.496 [0.44,0.56] | - | 0.475 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +10 | POOLED | logit2 | 0.487 [0.46,0.51] | 0.496 [0.45,0.54] | - | 0.487 | 0.625 | - | - | - | - | - | stack | locked label (reference only) |
| C0-pertype | +15 | NY | stack | 0.521 [0.46,0.58] | 0.495 [0.39,0.61] | - | 0.473 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Efx-condrescore | +15 | NY | gbt3 | 0.531 [0.46,0.60] | 0.495 [0.39,0.60] | - | 0.484 | 0.507 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +30 | NY | logit2 | 0.498 [0.42,0.57] | 0.494 [0.39,0.59] | - | 0.492 | 0.619 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx-condrescore | +30 | NY | gbt3 | 0.514 [0.44,0.58] | 0.494 [0.40,0.61] | - | 0.496 | 0.500 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +30 | LONDON | gbt3 | 0.505 [0.45,0.56] | 0.494 [0.41,0.57] | - | 0.477 | 0.502 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd-condrescore | +15 | ASIA | gbt3 | 0.500 [0.46,0.54] | 0.494 [0.44,0.55] | - | 0.487 | 0.498 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8-condrescore | +30 | NY | gbt3 | 0.553 [0.48,0.63] | 0.493 [0.39,0.59] | - | 0.516 | 0.549 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot-condrescore | +30 | LONDON | logit2 | 0.525 [0.48,0.57] | 0.493 [0.43,0.57] | - | 0.492 | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | pre | NY | logit2 | 0.512 [0.44,0.58] | 0.492 [0.40,0.58] | - | 0.501 | 0.622 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecmd-condrescore | +30 | POOLED | rf | 0.494 [0.46,0.53] | 0.492 [0.44,0.54] | - | 0.497 | 0.597 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +30 | POOLED | logit2 | 0.492 [0.46,0.52] | 0.492 [0.45,0.53] | - | 0.492 | 0.625 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +10 | NY | logit2 | 0.475 [0.40,0.54] | 0.492 [0.40,0.59] | - | 0.537 | 0.587 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +60 | LONDON | logit2 | 0.520 [0.47,0.57] | 0.492 [0.41,0.56] | - | 0.521 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +5 | LONDON | logit2 | 0.523 [0.48,0.57] | 0.492 [0.42,0.56] | - | 0.496 | 0.576 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | pre | NY | logit2 | 0.521 [0.46,0.58] | 0.491 [0.40,0.58] | - | 0.516 | 0.561 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecot-condrescore | +30 | NY | logit2 | 0.519 [0.45,0.59] | 0.491 [0.40,0.58] | - | 0.456 | 0.537 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +10 | POOLED | stack | 0.499 [0.47,0.53] | 0.491 [0.45,0.53] | - | 0.486 | 0.603 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecmd-condrescore | +15 | NY | logit2 | 0.545 [0.47,0.61] | 0.491 [0.39,0.58] | - | 0.529 | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Efx-condrescore | +15 | ASIA | gbt3 | 0.495 [0.45,0.54] | 0.489 [0.42,0.56] | - | 0.479 | 0.498 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11-condrescore | +15 | LONDON | gbt3 | 0.507 [0.45,0.56] | 0.489 [0.41,0.57] | - | 0.482 | 0.515 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +20 | NY | logit2 | 0.520 [0.46,0.58] | 0.487 [0.37,0.59] | - | 0.486 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +20 | ASIA | stack | 0.550 [0.51,0.59] | 0.487 [0.43,0.55] | - | 0.474 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10-condrescore | +15 | POOLED | rf | 0.500 [0.47,0.53] | 0.487 [0.45,0.53] | - | 0.468 | 0.601 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12-condrescore | +30 | POOLED | logit2 | 0.493 [0.46,0.52] | 0.486 [0.44,0.53] | - | 0.492 | 0.573 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | pre | NY | logit2 | 0.515 [0.44,0.59] | 0.486 [0.38,0.58] | - | 0.498 | 0.610 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Eterm-condrescore | +30 | POOLED | stack | 0.497 [0.47,0.53] | 0.486 [0.44,0.53] | - | 0.480 | 0.564 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +30 | LONDON | stack | 0.512 [0.46,0.57] | 0.485 [0.41,0.57] | - | 0.456 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +10 | NY | gbt3 | 0.494 [0.42,0.56] | 0.484 [0.40,0.58] | - | 0.490 | 0.669 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8-condrescore | +15 | ASIA | logit2 | 0.509 [0.46,0.55] | 0.484 [0.42,0.55] | - | 0.477 | 0.476 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +60 | NY | gbt3 | 0.488 [0.42,0.56] | 0.484 [0.37,0.59] | - | 0.527 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | pre | LONDON | gbt3 | 0.512 [0.46,0.56] | 0.483 [0.41,0.56] | - | 0.452 | 0.551 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +20 | NY | logit2 | 0.493 [0.43,0.56] | 0.483 [0.39,0.59] | - | 0.478 | 0.564 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-cond-trained | +30 | ASIA | gbt3 | 0.511 [0.46,0.56] | 0.483 [0.42,0.55] | - | 0.476 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | +10 | ASIA | logit2 | 0.508 [0.47,0.55] | 0.483 [0.42,0.54] | - | 0.479 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +15 | ASIA | gbt3 | 0.508 [0.47,0.55] | 0.483 [0.42,0.55] | - | 0.483 | 0.479 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-cond-trained | +30 | NY | stack | 0.543 [0.47,0.61] | 0.482 [0.38,0.59] | - | 0.473 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +15 | NY | logit2 | 0.487 [0.42,0.56] | 0.482 [0.37,0.60] | - | 0.474 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +10 | ASIA | rf | 0.526 [0.48,0.57] | 0.482 [0.42,0.55] | - | 0.461 | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +15 | NY | logit2 | 0.483 [0.41,0.56] | 0.482 [0.37,0.59] | - | 0.497 | 0.493 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12-condrescore | +30 | LONDON | logit2 | 0.496 [0.44,0.54] | 0.481 [0.40,0.55] | - | 0.498 | 0.501 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8-condrescore | +30 | LONDON | gbt3 | 0.512 [0.46,0.56] | 0.481 [0.39,0.56] | - | 0.454 | 0.526 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-cond-trained | pre | NY | logit2 | 0.477 [0.40,0.55] | 0.480 [0.37,0.58] | - | 0.518 | - | - | - | - | - | - |  | locked label (reference only) |
| C0-pertype | +15 | ASIA | stack | 0.501 [0.46,0.54] | 0.480 [0.42,0.54] | - | 0.457 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-cond-trained | +20 | NY | rf | 0.521 [0.46,0.59] | 0.479 [0.38,0.57] | - | 0.495 | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +30 | POOLED | gbt3 | 0.495 [0.46,0.52] | 0.479 [0.43,0.53] | - | 0.481 | 0.569 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +5 | NY | stack | 0.459 [0.39,0.53] | 0.479 [0.36,0.60] | - | 0.495 | 0.610 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +15 | LONDON | gbt3 | 0.505 [0.45,0.56] | 0.479 [0.40,0.57] | - | 0.456 | 0.515 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9-condrescore | +15 | NY | rf | 0.499 [0.43,0.56] | 0.479 [0.38,0.58] | - | 0.475 | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +30 | NY | gbt3 | 0.488 [0.43,0.55] | 0.477 [0.38,0.58] | - | 0.469 | 0.488 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | pre | POOLED | stack | 0.484 [0.46,0.51] | 0.476 [0.44,0.52] | - | 0.449 | 0.602 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +10 | NY | gbt3 | 0.485 [0.41,0.55] | 0.476 [0.38,0.57] | - | 0.459 | 0.639 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +30 | NY | gbt3 | 0.497 [0.43,0.57] | 0.475 [0.38,0.56] | - | 0.472 | 0.515 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +15 | NY | gbt3 | 0.471 [0.40,0.54] | 0.475 [0.38,0.58] | - | 0.448 | 0.634 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Efx-condrescore | +15 | POOLED | gbt3 | 0.479 [0.45,0.51] | 0.475 [0.42,0.52] | - | 0.465 | 0.564 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Erates-condrescore | +15 | NY | rf | 0.466 [0.40,0.53] | 0.474 [0.37,0.58] | - | 0.479 | 0.511 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +15 | NY | logit2 | 0.491 [0.43,0.56] | 0.474 [0.37,0.57] | - | 0.441 | 0.636 | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all-condrescore | +5 | POOLED | gbt3 | 0.481 [0.46,0.51] | 0.474 [0.43,0.51] | - | 0.465 | 0.601 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +15 | NY | logit2 | 0.510 [0.45,0.57] | 0.473 [0.37,0.58] | - | 0.489 | 0.581 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | pre | POOLED | stack | 0.499 [0.47,0.53] | 0.473 [0.43,0.51] | - | 0.473 | 0.613 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eterm-condrescore | +30 | ASIA | stack | 0.500 [0.46,0.54] | 0.472 [0.41,0.53] | - | 0.466 | 0.469 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | pre | POOLED | stack | 0.482 [0.46,0.51] | 0.471 [0.43,0.51] | - | 0.453 | 0.607 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11-condrescore | +30 | POOLED | stack | 0.510 [0.48,0.54] | 0.470 [0.43,0.52] | - | 0.472 | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +10 | POOLED | rf | 0.486 [0.46,0.51] | 0.470 [0.43,0.51] | - | 0.467 | 0.598 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-trained | +60 | NY | stack | 0.502 [0.43,0.56] | 0.470 [0.36,0.57] | - | 0.479 | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +15 | ASIA | rf | 0.519 [0.47,0.57] | 0.469 [0.41,0.53] | - | 0.458 | 0.462 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | pre | LONDON | gbt3 | 0.479 [0.43,0.54] | 0.468 [0.39,0.55] | - | 0.459 | 0.577 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10-condrescore | +15 | NY | logit2 | 0.494 [0.43,0.56] | 0.468 [0.36,0.57] | - | 0.438 | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11-condrescore | +15 | POOLED | logit2 | 0.491 [0.46,0.52] | 0.468 [0.42,0.51] | - | 0.467 | 0.564 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-cond-trained | +30 | LONDON | rf | 0.499 [0.45,0.55] | 0.467 [0.40,0.54] | - | 0.458 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +30 | LONDON | logit2 | 0.522 [0.47,0.57] | 0.467 [0.39,0.54] | - | 0.457 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecmd-condrescore | +15 | POOLED | gbt3 | 0.476 [0.45,0.51] | 0.466 [0.41,0.52] | - | 0.459 | 0.591 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-condrescore | +5 | POOLED | rf | 0.477 [0.45,0.51] | 0.466 [0.42,0.51] | - | 0.459 | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | +5 | NY | logit2 | 0.463 [0.40,0.53] | 0.465 [0.37,0.57] | - | 0.492 | 0.640 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | pre | ASIA | gbt3 | 0.507 [0.46,0.55] | 0.464 [0.40,0.53] | - | 0.444 | 0.467 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +60 | ASIA | stack | 0.499 [0.46,0.54] | 0.463 [0.41,0.51] | - | 0.454 | 0.450 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-condrescore | +5 | POOLED | logit2 | 0.471 [0.45,0.50] | 0.461 [0.42,0.50] | - | 0.453 | 0.616 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E12-condrescore | +15 | POOLED | gbt3 | 0.473 [0.44,0.51] | 0.461 [0.42,0.51] | - | 0.463 | 0.556 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype-condrescore | +30 | NY | logit2 | 0.495 [0.43,0.56] | 0.460 [0.36,0.56] | - | 0.480 | 0.739 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8-condrescore | +30 | ASIA | gbt3 | 0.500 [0.45,0.55] | 0.460 [0.40,0.53] | - | 0.438 | 0.471 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | +5 | ASIA | gbt3 | 0.514 [0.47,0.56] | 0.459 [0.40,0.52] | - | 0.446 | 0.464 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | pre | NY | stack | 0.512 [0.45,0.57] | 0.459 [0.35,0.56] | - | 0.461 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11-condrescore | +30 | ASIA | stack | 0.529 [0.48,0.58] | 0.459 [0.40,0.52] | - | 0.454 | 0.466 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +45 | NY | gbt3 | 0.526 [0.46,0.60] | 0.458 [0.35,0.57] | - | 0.413 | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11-condrescore | +15 | ASIA | stack | 0.503 [0.46,0.55] | 0.455 [0.39,0.52] | - | 0.451 | 0.453 | - | - | - | - | - |  | locked label (reference only) |
| C0-FAILPRED-cond-trained | +5 | LONDON | stack | 0.504 [0.45,0.56] | 0.454 [0.39,0.52] | - | 0.447 | - | - | - | - | - | - | stack | locked label (reference only) |
| C0-FAILPRED-cond-trained | +5 | NY | gbt3 | 0.495 [0.42,0.56] | 0.453 [0.36,0.55] | - | 0.464 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8-condrescore | +30 | POOLED | gbt3 | 0.499 [0.47,0.53] | 0.452 [0.41,0.49] | - | 0.441 | 0.561 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all+base-pertype-condrescore | +30 | NY | logit2 | 0.496 [0.43,0.56] | 0.450 [0.35,0.55] | - | 0.465 | 0.720 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-condrescore | pre | LONDON | gbt3 | 0.476 [0.42,0.53] | 0.449 [0.38,0.53] | - | 0.425 | 0.547 | - | - | - | - | - | stack | locked label (reference only) |
| C0-pertype | +30 | NY | logit2 | 0.480 [0.41,0.55] | 0.449 [0.36,0.54] | - | 0.452 | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-7-all+base-condrescore | +5 | NY | logit2 | 0.458 [0.39,0.52] | 0.446 [0.35,0.55] | - | 0.473 | 0.623 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all-condrescore | +5 | POOLED | gbt3 | 0.469 [0.44,0.49] | 0.443 [0.40,0.49] | - | 0.441 | 0.589 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | pre | POOLED | stack | 0.487 [0.46,0.51] | 0.442 [0.40,0.48] | - | 0.436 | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx-condrescore | +30 | NY | logit2 | 0.464 [0.40,0.53] | 0.438 [0.36,0.52] | - | 0.462 | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +15 | POOLED | gbt3 | 0.471 [0.44,0.50] | 0.431 [0.39,0.48] | - | 0.434 | 0.543 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +60 | NY | logit2 | 0.464 [0.40,0.53] | 0.429 [0.33,0.54] | - | 0.431 | 0.517 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12-condrescore | +15 | LONDON | gbt3 | 0.497 [0.43,0.56] | 0.427 [0.35,0.51] | - | 0.420 | 0.452 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-cond-trained | +15 | NY | stack | 0.499 [0.43,0.56] | 0.423 [0.30,0.55] | - | 0.419 | - | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +5 | NY | logit2 | 0.478 [0.42,0.54] | 0.415 [0.33,0.50] | - | 0.419 | 0.539 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Ecrypto-condrescore | +15 | ASIA | gbt3 | 0.485 [0.44,0.53] | 0.411 [0.36,0.46] | - | 0.415 | 0.413 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all-condrescore | pre | NY | stack | 0.454 [0.40,0.51] | 0.400 [0.30,0.50] | - | 0.413 | 0.495 | - | - | - | - | - |  | locked label (reference only) |
| E1-17+base-cond-pertype | +30 | NY | rf | 0.459 [0.39,0.54] | 0.399 [0.30,0.52] | - | 0.396 | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-Ecmd-condrescore | +30 | NY | rf | 0.463 [0.39,0.53] | 0.394 [0.29,0.50] | - | 0.407 | 0.419 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-Eidx-condrescore | +15 | NY | gbt3 | 0.461 [0.40,0.53] | 0.357 [0.28,0.44] | - | 0.352 | 0.450 | - | - | - | - | - |  | locked label (reference only) |
| E1-7-all-condrescore | +10 | NY | gbt3 | 0.464 [0.40,0.53] | 0.339 [0.26,0.43] | - | 0.341 | 0.481 | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- C0-FAILPRED-cond-trained 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-FAILPRED-cond-trained 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-cond-trained 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-trained 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17+base-cond-pertype 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- C0-pertype 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-cond-trained 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-condrescore 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecmd-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecot-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Ecrypto-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Efx-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eidx-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Erates-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Eterm-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-Exc-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-7-all+base-pertype-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E8-12-all-condrescore 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E10-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E11-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E12-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E8-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E9-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-12-all+base-pertype-condrescore 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
