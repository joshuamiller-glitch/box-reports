# PRED ROUND 35 - block E round 3 - E13-E17 cross-market

Best HOLDOUT F-R AUC: +15 POOLED 0.529 [0.48,0.57] | ASIA 0.571 [0.51,0.63] | LONDON 0.595 [0.52,0.67] | NY 0.554 [0.46,0.65]
Best HOLDOUT F-R AUC: +30 POOLED 0.548 [0.50,0.59] | ASIA 0.589 [0.53,0.65] | LONDON 0.545 [0.46,0.62] | NY 0.552 [0.45,0.66]
Best G HOLDOUT AUC: 0.620 [0.55,0.69]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg f53188642b51ff1d75539688aa9642fdfa2dc2311c82000ef7108291d1521de7 ; trials added 1800 ; truncation audit {'decisions': 720, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E3.parquet', 'l2vast/pred/store/E3_sig.parquet', 'l2vast/pred/store/E13.parquet', 'l2vast/pred/store/E14.parquet', 'l2vast/pred/store/E15.parquet', 'l2vast/pred/store/E16.parquet', 'l2vast/pred/store/E17.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1-17-G+base | sig | LONDON/ST | logit2 | 0.633 [0.59,0.67] | 0.620 [0.55,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.624 [0.58,0.67] | 0.613 [0.54,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.629 [0.59,0.66] | 0.607 [0.56,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | NY | rf | 0.611 [0.57,0.65] | 0.605 [0.56,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA | gbt3 | 0.576 [0.55,0.61] | 0.605 [0.57,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | LONDON/HM | logit2 | 0.592 [0.55,0.63] | 0.604 [0.55,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | LONDON | logit2 | 0.620 [0.59,0.65] | 0.604 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY | logit2 | 0.611 [0.58,0.64] | 0.603 [0.56,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/ST | gbt3 | 0.585 [0.53,0.63] | 0.602 [0.54,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | NY/ST | rf | 0.585 [0.53,0.63] | 0.601 [0.52,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | LONDON | logit2 | 0.625 [0.59,0.66] | 0.601 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED | rf | 0.588 [0.57,0.60] | 0.596 [0.57,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +15 | LONDON | logit2 | 0.546 [0.49,0.60] | 0.595 [0.52,0.67] | - | 0.595 | 0.620 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA/HM | rf | 0.567 [0.53,0.60] | 0.594 [0.54,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED/ST | logit2 | 0.586 [0.56,0.61] | 0.593 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/HM | rf | 0.607 [0.56,0.65] | 0.592 [0.53,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | NY | rf | 0.597 [0.56,0.64] | 0.592 [0.54,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | LONDON/ST | logit2 | 0.614 [0.57,0.66] | 0.591 [0.52,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED/HM | rf | 0.578 [0.56,0.60] | 0.590 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +30 | ASIA | rf | 0.567 [0.52,0.61] | 0.589 [0.53,0.65] | - | 0.580 | 0.581 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +60 | LONDON | logit2 | 0.530 [0.48,0.58] | 0.589 [0.52,0.65] | - | 0.593 | 0.605 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/ST | logit2 | 0.582 [0.56,0.60] | 0.588 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | NY/ST | gbt3 | 0.582 [0.53,0.63] | 0.587 [0.52,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | ASIA | rf | 0.561 [0.53,0.59] | 0.585 [0.55,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | POOLED | logit2 | 0.579 [0.56,0.60] | 0.585 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | NY/HM | rf | 0.605 [0.55,0.65] | 0.585 [0.51,0.67] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.582 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | ASIA/HM | stack | 0.555 [0.52,0.59] | 0.581 [0.53,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | POOLED/ST | logit2 | 0.581 [0.56,0.60] | 0.580 [0.55,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA/ST | logit2 | 0.550 [0.52,0.58] | 0.576 [0.54,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | POOLED/HM | rf | 0.571 [0.55,0.59] | 0.574 [0.54,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | LONDON/HM | rf | 0.592 [0.55,0.63] | 0.573 [0.52,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +10 | LONDON | logit2 | 0.547 [0.50,0.60] | 0.572 [0.50,0.65] | - | 0.562 | 0.602 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +15 | ASIA | rf | 0.558 [0.51,0.60] | 0.571 [0.51,0.63] | - | 0.571 | 0.568 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/HM | rf | 0.571 [0.55,0.59] | 0.571 [0.54,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | ASIA/HM | stack | 0.559 [0.53,0.59] | 0.571 [0.52,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +10 | ASIA | logit2 | 0.542 [0.50,0.58] | 0.569 [0.50,0.64] | - | 0.558 | 0.552 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +60 | ASIA | rf | 0.528 [0.48,0.58] | 0.569 [0.50,0.64] | - | 0.567 | 0.566 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | NY/HM | rf | 0.594 [0.54,0.64] | 0.566 [0.49,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.542 [0.51,0.58] | 0.563 [0.51,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/HM | rf | 0.588 [0.55,0.63] | 0.562 [0.51,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | ASIA/ST | logit2 | 0.551 [0.52,0.58] | 0.561 [0.52,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +45 | ASIA | gbt3 | 0.541 [0.49,0.58] | 0.560 [0.49,0.63] | - | 0.559 | 0.553 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA | gbt3 | 0.543 [0.51,0.57] | 0.559 [0.52,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +20 | LONDON | gbt3 | 0.534 [0.48,0.59] | 0.559 [0.47,0.64] | - | 0.548 | 0.620 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | ASIA/HM | logit2 | 0.545 [0.51,0.58] | 0.559 [0.51,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base-pertype | +15 | ASIA | stack | 0.563 [0.52,0.61] | 0.558 [0.50,0.62] | - | 0.550 | 0.542 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/HM | logit2 | 0.550 [0.51,0.59] | 0.558 [0.51,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | ASIA | gbt3 | 0.540 [0.51,0.57] | 0.556 [0.52,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.535 [0.49,0.59] | 0.555 [0.48,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E16 | +15 | ASIA | logit2 | 0.554 [0.51,0.60] | 0.555 [0.49,0.62] | - | 0.551 | 0.549 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/ST | logit2 | 0.544 [0.51,0.57] | 0.555 [0.52,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E15 | +15 | NY | logit2 | 0.534 [0.46,0.60] | 0.554 [0.46,0.65] | - | 0.540 | 0.554 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +45 | NY | rf | 0.520 [0.45,0.60] | 0.552 [0.44,0.66] | - | 0.560 | 0.579 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +30 | NY | logit2 | 0.545 [0.47,0.61] | 0.552 [0.45,0.66] | - | 0.560 | 0.553 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +45 | LONDON | gbt3 | 0.512 [0.46,0.56] | 0.551 [0.48,0.62] | - | 0.556 | 0.572 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +20 | ASIA | rf | 0.539 [0.49,0.58] | 0.550 [0.49,0.61] | - | 0.545 | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +60 | NY | gbt3 | 0.508 [0.43,0.59] | 0.550 [0.43,0.66] | - | 0.561 | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +45 | NY | gbt3 | 0.525 [0.46,0.59] | 0.550 [0.45,0.65] | - | 0.539 | 0.649 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA/HM | logit2 | 0.517 [0.48,0.55] | 0.550 [0.50,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +15 | ASIA | logit2 | 0.535 [0.50,0.58] | 0.550 [0.49,0.61] | - | 0.547 | 0.545 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +30 | POOLED | rf | 0.527 [0.50,0.56] | 0.548 [0.50,0.59] | - | 0.541 | 0.667 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | LONDON/ST | stack | 0.509 [0.47,0.55] | 0.547 [0.48,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/HM | rf | 0.573 [0.52,0.63] | 0.547 [0.46,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | LONDON/ST | logit2 | 0.522 [0.48,0.57] | 0.546 [0.49,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +5 | ASIA | rf | 0.537 [0.49,0.59] | 0.545 [0.48,0.61] | - | 0.527 | 0.544 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +30 | LONDON | logit2 | 0.544 [0.50,0.59] | 0.545 [0.46,0.62] | - | 0.509 | 0.588 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA | gbt3 | 0.524 [0.49,0.55] | 0.545 [0.51,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +15 | NY | logit2 | 0.521 [0.46,0.58] | 0.543 [0.45,0.63] | - | 0.570 | 0.535 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +20 | LONDON | rf | 0.523 [0.47,0.58] | 0.543 [0.47,0.62] | - | 0.506 | 0.573 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +30 | ASIA | rf | 0.541 [0.49,0.59] | 0.543 [0.48,0.61] | - | 0.526 | 0.549 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +20 | NY | rf | 0.504 [0.43,0.57] | 0.543 [0.43,0.64] | - | 0.508 | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | POOLED/HM | rf | 0.533 [0.51,0.56] | 0.542 [0.51,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | POOLED/HM | rf | 0.539 [0.51,0.56] | 0.541 [0.51,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +60 | POOLED | rf | 0.508 [0.48,0.54] | 0.540 [0.49,0.59] | - | 0.540 | 0.678 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +30 | NY | rf | 0.509 [0.43,0.58] | 0.540 [0.43,0.64] | - | 0.521 | 0.672 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | LONDON/ST | logit2 | 0.524 [0.48,0.56] | 0.538 [0.47,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/HM | rf | 0.560 [0.53,0.59] | 0.538 [0.49,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +15 | LONDON | gbt3 | 0.525 [0.47,0.58] | 0.538 [0.47,0.60] | - | 0.512 | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +20 | POOLED | gbt3 | 0.507 [0.47,0.54] | 0.538 [0.49,0.59] | - | 0.528 | 0.651 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | +45 | POOLED | gbt3 | 0.520 [0.49,0.55] | 0.537 [0.49,0.58] | - | 0.537 | 0.639 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E15 | +30 | NY | rf | 0.472 [0.39,0.55] | 0.535 [0.42,0.65] | - | 0.523 | 0.532 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | pre | ASIA | stack | 0.528 [0.49,0.57] | 0.533 [0.47,0.60] | - | 0.510 | 0.526 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E16 | +30 | ASIA | gbt3 | 0.519 [0.48,0.56] | 0.533 [0.48,0.60] | - | 0.520 | 0.531 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base-pertype | +15 | LONDON | stack | 0.545 [0.49,0.59] | 0.533 [0.46,0.61] | - | 0.533 | 0.495 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.530 [0.49,0.56] | 0.533 [0.48,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/ST | gbt3 | 0.538 [0.50,0.57] | 0.531 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | POOLED | logit2 | 0.523 [0.51,0.54] | 0.530 [0.51,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +15 | POOLED | rf | 0.503 [0.47,0.53] | 0.529 [0.48,0.57] | - | 0.518 | 0.650 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED/HM | logit2 | 0.518 [0.50,0.54] | 0.528 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA | rf | 0.526 [0.50,0.56] | 0.528 [0.49,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED | rf | 0.514 [0.49,0.54] | 0.527 [0.50,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/HM | logit2 | 0.520 [0.49,0.55] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E13 | +30 | LONDON | stack | 0.539 [0.49,0.59] | 0.526 [0.46,0.60] | - | 0.508 | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-G+base | sig | LONDON | logit2 | 0.528 [0.49,0.56] | 0.526 [0.48,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED | logit2 | 0.514 [0.49,0.53] | 0.524 [0.50,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +20 | ASIA | rf | 0.526 [0.48,0.57] | 0.524 [0.47,0.59] | - | 0.520 | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +60 | NY | gbt3 | 0.527 [0.46,0.60] | 0.524 [0.42,0.64] | - | 0.521 | 0.717 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +20 | NY | logit2 | 0.517 [0.45,0.59] | 0.524 [0.41,0.62] | - | 0.532 | 0.519 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED | rf | 0.511 [0.49,0.53] | 0.522 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY | rf | 0.522 [0.48,0.56] | 0.522 [0.46,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | NY/HM | rf | 0.545 [0.49,0.60] | 0.521 [0.44,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | NY/ST | stack | 0.507 [0.45,0.56] | 0.521 [0.44,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | ASIA/ST | logit2 | 0.534 [0.51,0.57] | 0.521 [0.48,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/HM | gbt3 | 0.522 [0.46,0.58] | 0.521 [0.43,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +15 | NY | logit2 | 0.489 [0.42,0.56] | 0.521 [0.43,0.62] | - | 0.498 | 0.646 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E16 | +30 | LONDON | logit2 | 0.487 [0.43,0.55] | 0.520 [0.44,0.59] | - | 0.494 | 0.555 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-G+base | sig | NY | rf | 0.519 [0.48,0.56] | 0.518 [0.46,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/ST | stack | 0.521 [0.47,0.57] | 0.518 [0.45,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E14 | +30 | ASIA | rf | 0.511 [0.47,0.55] | 0.518 [0.45,0.59] | - | 0.521 | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA | stack | 0.500 [0.47,0.53] | 0.518 [0.48,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E14 | +15 | ASIA | stack | 0.533 [0.49,0.58] | 0.517 [0.45,0.58] | - | 0.518 | 0.519 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.515 [0.48,0.55] | 0.517 [0.46,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +10 | NY | gbt3 | 0.489 [0.42,0.55] | 0.516 [0.42,0.62] | - | 0.557 | 0.541 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | pre | LONDON | gbt3 | 0.517 [0.46,0.57] | 0.516 [0.44,0.60] | - | 0.501 | 0.511 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +60 | LONDON | rf | 0.511 [0.46,0.57] | 0.516 [0.45,0.59] | - | 0.517 | 0.558 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/HM | rf | 0.512 [0.49,0.53] | 0.515 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | POOLED/HM | rf | 0.506 [0.48,0.53] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | POOLED/ST | gbt3 | 0.521 [0.49,0.55] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +15 | NY | logit2 | 0.525 [0.46,0.59] | 0.514 [0.41,0.62] | - | 0.520 | 0.539 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY | stack | 0.515 [0.48,0.55] | 0.512 [0.45,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | ASIA | gbt3 | 0.502 [0.47,0.53] | 0.511 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | POOLED/ST | logit2 | 0.499 [0.47,0.52] | 0.511 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +15 | POOLED | logit2 | 0.498 [0.47,0.53] | 0.510 [0.47,0.55] | - | 0.517 | 0.599 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | ASIA/ST | rf | 0.515 [0.48,0.55] | 0.509 [0.46,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E16 | +15 | NY | logit2 | 0.531 [0.47,0.59] | 0.509 [0.41,0.60] | - | 0.541 | 0.554 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/ST | stack | 0.504 [0.48,0.53] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | NY/ST | gbt3 | 0.517 [0.47,0.57] | 0.508 [0.44,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-G+base | sig | LONDON/HM | logit2 | 0.509 [0.46,0.55] | 0.507 [0.45,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +20 | POOLED | stack | 0.510 [0.48,0.54] | 0.507 [0.46,0.55] | - | 0.508 | 0.613 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E16 | +15 | POOLED | logit2 | 0.498 [0.47,0.53] | 0.507 [0.46,0.55] | - | 0.508 | 0.609 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base-pertype | +15 | POOLED | stack | 0.507 [0.48,0.54] | 0.507 [0.46,0.55] | - | 0.505 | 0.616 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | ASIA/ST | logit2 | 0.501 [0.47,0.54] | 0.506 [0.46,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base-pertype | +30 | POOLED | logit2 | 0.499 [0.47,0.53] | 0.506 [0.46,0.55] | - | 0.507 | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | POOLED/ST | stack | 0.499 [0.48,0.52] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | ASIA/HM | stack | 0.506 [0.47,0.55] | 0.506 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | NY/ST | stack | 0.515 [0.47,0.57] | 0.505 [0.43,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +30 | LONDON | logit2 | 0.487 [0.43,0.54] | 0.505 [0.43,0.58] | - | 0.496 | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | POOLED/ST | rf | 0.517 [0.49,0.54] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/ST | logit2 | 0.506 [0.47,0.54] | 0.505 [0.45,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | LONDON/HM | rf | 0.503 [0.45,0.55] | 0.504 [0.43,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +15 | LONDON | gbt3 | 0.483 [0.43,0.53] | 0.504 [0.43,0.58] | - | 0.518 | 0.526 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +10 | POOLED | logit2 | 0.494 [0.47,0.52] | 0.503 [0.46,0.55] | - | 0.495 | 0.627 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E13 | +15 | NY | gbt3 | 0.525 [0.46,0.59] | 0.503 [0.40,0.60] | - | 0.510 | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E16 | +30 | POOLED | logit2 | 0.483 [0.45,0.52] | 0.503 [0.46,0.54] | - | 0.500 | 0.606 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-G+base | sig | NY/ST | stack | 0.515 [0.47,0.57] | 0.503 [0.43,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E13 | +15 | LONDON | stack | 0.519 [0.46,0.57] | 0.501 [0.43,0.58] | - | 0.502 | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | pre | ASIA | logit2 | 0.508 [0.46,0.56] | 0.499 [0.44,0.56] | - | 0.499 | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +15 | POOLED | logit2 | 0.492 [0.46,0.52] | 0.499 [0.45,0.54] | - | 0.500 | 0.566 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +5 | LONDON | logit2 | 0.514 [0.47,0.56] | 0.498 [0.43,0.56] | - | 0.501 | 0.569 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E17 | +15 | ASIA | logit2 | 0.535 [0.49,0.58] | 0.498 [0.43,0.57] | - | 0.497 | 0.492 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | LONDON/HM | rf | 0.501 [0.45,0.55] | 0.497 [0.43,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/ST | gbt3 | 0.534 [0.48,0.59] | 0.496 [0.42,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +45 | ASIA | logit2 | 0.529 [0.48,0.58] | 0.496 [0.42,0.56] | - | 0.491 | 0.501 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +30 | NY | rf | 0.527 [0.46,0.60] | 0.495 [0.42,0.58] | - | 0.488 | 0.533 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | POOLED | gbt3 | 0.505 [0.49,0.52] | 0.495 [0.47,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | POOLED/HM | gbt3 | 0.514 [0.49,0.54] | 0.494 [0.45,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/ST | stack | 0.498 [0.45,0.54] | 0.494 [0.43,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base-pertype | +30 | ASIA | stack | 0.517 [0.47,0.56] | 0.493 [0.44,0.55] | - | 0.479 | 0.484 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | ASIA/ST | gbt3 | 0.501 [0.47,0.54] | 0.493 [0.45,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +10 | ASIA | gbt3 | 0.507 [0.46,0.55] | 0.492 [0.43,0.55] | - | 0.484 | 0.498 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/HM | stack | 0.529 [0.48,0.58] | 0.491 [0.42,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | NY/ST | rf | 0.525 [0.48,0.57] | 0.491 [0.43,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base-pertype | +15 | NY | logit2 | 0.503 [0.44,0.56] | 0.491 [0.39,0.58] | - | 0.462 | 0.632 | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/HM | gbt3 | 0.488 [0.44,0.54] | 0.491 [0.43,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +30 | POOLED | logit2 | 0.481 [0.45,0.51] | 0.491 [0.45,0.53] | - | 0.497 | 0.601 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | NY | logit2 | 0.511 [0.47,0.55] | 0.490 [0.44,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +60 | POOLED | logit2 | 0.499 [0.47,0.53] | 0.489 [0.44,0.53] | - | 0.496 | 0.582 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +10 | POOLED | logit2 | 0.485 [0.46,0.51] | 0.488 [0.44,0.53] | - | 0.496 | 0.576 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA/ST | gbt3 | 0.521 [0.49,0.55] | 0.488 [0.44,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +5 | ASIA | gbt3 | 0.500 [0.46,0.55] | 0.487 [0.43,0.55] | - | 0.477 | 0.491 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +45 | POOLED | logit2 | 0.507 [0.47,0.54] | 0.486 [0.44,0.52] | - | 0.490 | 0.586 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +15 | LONDON | logit2 | 0.480 [0.43,0.53] | 0.486 [0.41,0.57] | - | 0.509 | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | LONDON | gbt3 | 0.519 [0.48,0.56] | 0.485 [0.43,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-all | +10 | LONDON | logit2 | 0.492 [0.44,0.54] | 0.485 [0.40,0.57] | - | 0.476 | 0.515 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +60 | ASIA | logit2 | 0.502 [0.46,0.54] | 0.484 [0.42,0.54] | - | 0.486 | 0.484 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | POOLED/ST | rf | 0.485 [0.46,0.51] | 0.484 [0.45,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON | gbt3 | 0.479 [0.45,0.51] | 0.484 [0.43,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | pre | POOLED | stack | 0.484 [0.46,0.51] | 0.484 [0.44,0.53] | - | 0.460 | 0.605 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | NY | logit2 | 0.496 [0.45,0.54] | 0.484 [0.42,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +30 | ASIA | stack | 0.527 [0.49,0.57] | 0.482 [0.43,0.54] | - | 0.475 | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +30 | NY | logit2 | 0.478 [0.40,0.55] | 0.482 [0.38,0.57] | - | 0.506 | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/HM | gbt3 | 0.487 [0.44,0.54] | 0.482 [0.41,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED | rf | 0.484 [0.46,0.51] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +15 | ASIA | stack | 0.531 [0.49,0.57] | 0.480 [0.42,0.54] | - | 0.473 | 0.481 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA | stack | 0.510 [0.48,0.54] | 0.480 [0.44,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E16 | +15 | LONDON | rf | 0.460 [0.40,0.51] | 0.480 [0.41,0.55] | - | 0.478 | 0.526 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +15 | POOLED | logit2 | 0.492 [0.46,0.52] | 0.478 [0.43,0.52] | - | 0.474 | 0.553 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | pre | NY | logit2 | 0.504 [0.43,0.58] | 0.478 [0.38,0.57] | - | 0.489 | 0.606 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | LONDON/HM | logit2 | 0.477 [0.43,0.52] | 0.478 [0.41,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +10 | NY | gbt3 | 0.485 [0.41,0.55] | 0.477 [0.39,0.58] | - | 0.491 | 0.632 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G+base | sig | LONDON/HM | rf | 0.478 [0.43,0.53] | 0.477 [0.42,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-G+base | sig | NY/HM | logit2 | 0.522 [0.47,0.58] | 0.475 [0.39,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base-pertype | +30 | LONDON | stack | 0.518 [0.46,0.57] | 0.475 [0.40,0.55] | - | 0.478 | 0.448 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E13 | +30 | ASIA | logit2 | 0.513 [0.47,0.56] | 0.472 [0.40,0.54] | - | 0.475 | 0.454 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | NY/HM | rf | 0.522 [0.47,0.57] | 0.472 [0.39,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +45 | LONDON | logit2 | 0.498 [0.45,0.55] | 0.469 [0.40,0.54] | - | 0.463 | 0.487 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +30 | POOLED | stack | 0.493 [0.46,0.52] | 0.469 [0.42,0.51] | - | 0.462 | 0.570 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E13 | +15 | POOLED | stack | 0.490 [0.46,0.52] | 0.468 [0.43,0.51] | - | 0.471 | 0.558 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | POOLED | gbt3 | 0.486 [0.46,0.51] | 0.467 [0.44,0.49] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +5 | LONDON | stack | 0.490 [0.44,0.54] | 0.466 [0.40,0.53] | - | 0.475 | 0.511 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +30 | POOLED | logit2 | 0.481 [0.45,0.51] | 0.465 [0.42,0.51] | - | 0.468 | 0.542 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | ASIA | gbt3 | 0.488 [0.46,0.52] | 0.465 [0.43,0.50] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/ST | gbt3 | 0.479 [0.44,0.52] | 0.464 [0.41,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G+base | sig | NY | gbt3 | 0.498 [0.46,0.53] | 0.464 [0.41,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E13 | +15 | ASIA | logit2 | 0.497 [0.45,0.54] | 0.461 [0.40,0.53] | - | 0.460 | 0.454 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E13 | +30 | NY | rf | 0.451 [0.39,0.51] | 0.458 [0.36,0.56] | - | 0.482 | 0.474 | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +5 | POOLED | logit2 | 0.467 [0.44,0.49] | 0.457 [0.41,0.50] | - | 0.452 | 0.612 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base-pertype | +30 | NY | logit2 | 0.481 [0.42,0.55] | 0.457 [0.36,0.55] | - | 0.472 | 0.739 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | LONDON | logit2 | 0.471 [0.44,0.50] | 0.456 [0.41,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +15 | NY | gbt3 | 0.507 [0.44,0.57] | 0.456 [0.36,0.55] | - | 0.447 | 0.418 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | LONDON/ST | gbt3 | 0.481 [0.45,0.52] | 0.456 [0.40,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +30 | ASIA | gbt3 | 0.499 [0.46,0.54] | 0.455 [0.38,0.52] | - | 0.461 | 0.454 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E13 | +30 | POOLED | stack | 0.491 [0.46,0.52] | 0.454 [0.41,0.50] | - | 0.455 | 0.546 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | pre | NY | gbt3 | 0.500 [0.43,0.57] | 0.453 [0.37,0.53] | - | 0.468 | 0.513 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | LONDON | rf | 0.484 [0.44,0.52] | 0.451 [0.39,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-17-all+base | +5 | NY | logit2 | 0.469 [0.41,0.53] | 0.450 [0.35,0.54] | - | 0.477 | 0.622 | - | - | - | - | - | stack | locked label (reference only) |
| E1-17-all+base | pre | LONDON | gbt3 | 0.484 [0.43,0.54] | 0.448 [0.38,0.52] | - | 0.424 | 0.547 | - | - | - | - | - | stack | locked label (reference only) |
| E13-17-G | sig | NY/HM | rf | 0.518 [0.46,0.58] | 0.447 [0.37,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +5 | POOLED | gbt3 | 0.467 [0.44,0.49] | 0.447 [0.41,0.48] | - | 0.449 | 0.567 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | pre | POOLED | gbt3 | 0.463 [0.43,0.49] | 0.445 [0.41,0.48] | - | 0.446 | 0.546 | - | - | - | - | - |  | locked label (reference only) |
| E13-17-G | sig | NY | rf | 0.489 [0.45,0.53] | 0.444 [0.39,0.50] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E13-17-all | +5 | NY | gbt3 | 0.465 [0.41,0.53] | 0.441 [0.33,0.56] | - | 0.445 | 0.472 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +30 | POOLED | rf | 0.473 [0.44,0.50] | 0.441 [0.40,0.49] | - | 0.444 | 0.549 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E16 | +30 | NY | stack | 0.481 [0.41,0.56] | 0.438 [0.35,0.52] | - | 0.457 | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON | gbt3 | 0.454 [0.42,0.49] | 0.433 [0.38,0.48] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +15 | POOLED | stack | 0.483 [0.46,0.51] | 0.432 [0.39,0.47] | - | 0.419 | 0.538 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E17 | +30 | LONDON | logit2 | 0.447 [0.39,0.50] | 0.418 [0.34,0.49] | - | 0.409 | 0.415 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E14 | +30 | LONDON | gbt3 | 0.472 [0.42,0.53] | 0.404 [0.33,0.49] | - | 0.382 | 0.434 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +30 | LONDON | gbt3 | 0.462 [0.41,0.51] | 0.397 [0.33,0.46] | - | 0.383 | 0.479 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E15 | +15 | LONDON | rf | 0.451 [0.40,0.51] | 0.383 [0.30,0.46] | - | 0.370 | 0.417 | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- E13-17-all 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-all 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 10 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 60 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 5 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 45 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 5 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 20 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 10 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 0 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 45 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 0 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 45 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 20 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 0 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 10 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 60 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 60 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 10 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 45 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 5 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 60 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 5 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 20 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 20 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base 0 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E13 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E14 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E15 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E16 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E-sub-E17 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 15 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 15 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 30 LONDON: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 15 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 30 NY: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 15 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 30 POOLED: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E1-17-all+base-pertype 30 ASIA: block E; model selected on conditional WF-PRE; econ grid not run (conditional WF-PRE far below FOUND bar); conditional holdout max over cells is selection noise, not a WF-confirmed gain
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 NY: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 POOLED: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 NY: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 POOLED: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-baseline-FAILPRED -1 ASIA: G per-signal; no gain over FAILPRED+context
- E13-17-G -1 LONDON: G per-signal; no gain over FAILPRED+context
- E13-17-G+base -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
- E1-17-G+base -1 ASIA: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
- G-context -1 LONDON: G per-signal; no gain over FAILPRED+context
