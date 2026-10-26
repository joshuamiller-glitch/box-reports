# PRED ROUND 16 - block E round 2 - E8-E12 cross-market

Best HOLDOUT F-R AUC: +15 POOLED 0.540 [-,-] | ASIA 0.561 [-,-] | LONDON 0.606 [-,-] | NY 0.585 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.551 [-,-] | ASIA 0.601 [-,-] | LONDON 0.622 [-,-] | NY 0.576 [-,-]
Best G HOLDOUT AUC: 0.626 [0.56,0.69]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 688778e9c151a9cb44037b7a3a59e604c5c52562fdf13df76f404851ba940f04 ; trials added 1800 ; truncation audit {'decisions': 720, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/E2.parquet', 'l2vast/pred/store/E2_sig.parquet', 'l2vast/pred/store/E8.parquet', 'l2vast/pred/store/E9.parquet', 'l2vast/pred/store/E10.parquet', 'l2vast/pred/store/E11.parquet', 'l2vast/pred/store/E12.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1-12-G+base | sig | LONDON/ST | logit2 | 0.635 [0.59,0.68] | 0.626 [0.56,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | NY/ST | logit2 | 0.606 [0.56,0.65] | 0.626 [0.56,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +30 | LONDON | rf | - | 0.622 [-,-] | - | - | 0.635 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | LONDON | logit2 | 0.638 [0.60,0.67] | 0.619 [0.57,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | NY/HM | rf | 0.616 [0.57,0.66] | 0.618 [0.55,0.69] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | ASIA | gbt3 | 0.581 [0.55,0.61] | 0.618 [0.58,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | NY/ST | rf | 0.601 [0.55,0.65] | 0.617 [0.54,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | LONDON/ST | logit2 | 0.630 [0.59,0.67] | 0.616 [0.54,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +45 | LONDON | rf | - | 0.613 [-,-] | - | - | 0.636 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.624 [0.58,0.67] | 0.613 [0.54,0.67] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +20 | LONDON | rf | - | 0.612 [-,-] | - | - | 0.617 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | NY | stack | 0.614 [0.57,0.65] | 0.611 [0.56,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.629 [0.59,0.66] | 0.607 [0.56,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | ASIA/HM | gbt3 | 0.578 [0.54,0.61] | 0.606 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +15 | LONDON | gbt3 | - | 0.606 [-,-] | - | - | 0.593 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY | logit2 | 0.611 [0.58,0.64] | 0.603 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | LONDON | logit2 | 0.622 [0.59,0.65] | 0.603 [0.55,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | LONDON/HM | logit2 | 0.588 [0.55,0.63] | 0.602 [0.55,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/ST | gbt3 | 0.585 [0.53,0.63] | 0.602 [0.54,0.66] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +30 | ASIA | stack | - | 0.601 [-,-] | - | - | 0.586 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +45 | LONDON | gbt3 | - | 0.600 [-,-] | - | - | 0.610 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | POOLED | rf | 0.589 [0.57,0.61] | 0.598 [0.57,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | NY/HM | rf | 0.607 [0.56,0.66] | 0.597 [0.52,0.68] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | POOLED | rf | 0.591 [0.57,0.61] | 0.597 [0.57,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | POOLED/ST | logit2 | 0.586 [0.56,0.61] | 0.595 [0.57,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | POOLED/HM | rf | 0.580 [0.56,0.60] | 0.595 [0.57,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | POOLED/ST | logit2 | 0.588 [0.57,0.61] | 0.594 [0.56,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | ASIA | rf | 0.561 [0.53,0.59] | 0.593 [0.55,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/HM | rf | 0.607 [0.56,0.65] | 0.592 [0.53,0.67] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | LONDON/ST | logit2 | 0.549 [0.51,0.59] | 0.591 [0.52,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | POOLED/HM | rf | 0.586 [0.56,0.61] | 0.590 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9 | +15 | LONDON | rf | - | 0.590 [-,-] | - | - | 0.576 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | NY | rf | 0.598 [0.56,0.64] | 0.589 [0.53,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/ST | logit2 | 0.582 [0.56,0.60] | 0.588 [0.56,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +20 | LONDON | logit2 | - | 0.587 [-,-] | - | - | 0.613 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | ASIA/HM | gbt3 | 0.573 [0.53,0.61] | 0.586 [0.53,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +15 | LONDON | logit2 | - | 0.586 [-,-] | - | - | 0.609 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-E12 | +15 | NY | logit2 | - | 0.585 [-,-] | - | - | 0.585 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED | logit2 | 0.582 [0.56,0.60] | 0.582 [0.56,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | NY | logit2 | 0.566 [0.53,0.61] | 0.582 [0.52,0.64] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | LONDON/ST | logit2 | 0.540 [0.50,0.58] | 0.581 [0.53,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-pertype | +15 | LONDON | logit2 | - | 0.579 [-,-] | - | - | 0.573 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9 | +30 | LONDON | gbt3 | - | 0.579 [-,-] | - | - | 0.585 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | NY/ST | gbt3 | 0.564 [0.51,0.61] | 0.577 [0.50,0.64] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +30 | NY | gbt3 | - | 0.576 [-,-] | - | - | 0.677 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | LONDON/HM | rf | 0.596 [0.56,0.64] | 0.575 [0.52,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +60 | LONDON | logit2 | - | 0.573 [-,-] | - | - | 0.604 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | ASIA | stack | 0.547 [0.51,0.58] | 0.571 [0.53,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +60 | ASIA | rf | - | 0.571 [-,-] | - | - | 0.568 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/HM | rf | 0.571 [0.55,0.59] | 0.571 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | ASIA/ST | logit2 | 0.541 [0.51,0.57] | 0.566 [0.53,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | ASIA/ST | logit2 | 0.545 [0.51,0.57] | 0.565 [0.53,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +60 | NY | logit2 | - | 0.564 [-,-] | - | - | 0.659 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.542 [0.51,0.58] | 0.563 [0.51,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | POOLED/HM | rf | 0.548 [0.52,0.58] | 0.563 [0.53,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +10 | LONDON | logit2 | - | 0.563 [-,-] | - | - | 0.596 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +10 | ASIA | rf | - | 0.563 [-,-] | - | - | 0.560 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/HM | rf | 0.588 [0.55,0.63] | 0.562 [0.51,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | LONDON/HM | rf | 0.541 [0.50,0.59] | 0.561 [0.50,0.63] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +15 | ASIA | rf | - | 0.561 [-,-] | - | - | 0.555 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | POOLED | rf | 0.550 [0.53,0.57] | 0.561 [0.53,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +15 | NY | logit2 | - | 0.560 [-,-] | - | - | 0.594 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E9 | +15 | ASIA | stack | - | 0.560 [-,-] | - | - | 0.552 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA | gbt3 | 0.543 [0.51,0.57] | 0.559 [0.52,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | NY/ST | stack | 0.548 [0.49,0.60] | 0.559 [0.47,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/HM | logit2 | 0.550 [0.51,0.59] | 0.558 [0.51,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +60 | LONDON | stack | - | 0.558 [-,-] | - | - | 0.597 | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/ST | logit2 | 0.535 [0.49,0.59] | 0.555 [0.48,0.63] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +5 | LONDON | gbt3 | - | 0.555 [-,-] | - | - | 0.593 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | NY/HM | gbt3 | 0.566 [0.51,0.62] | 0.555 [0.48,0.63] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/ST | logit2 | 0.544 [0.51,0.57] | 0.555 [0.52,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | NY/HM | rf | 0.558 [0.51,0.62] | 0.554 [0.47,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | pre | LONDON | logit2 | - | 0.553 [-,-] | - | - | 0.549 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +30 | POOLED | rf | - | 0.551 [-,-] | - | - | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +30 | POOLED | rf | - | 0.551 [-,-] | - | - | 0.652 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +10 | LONDON | rf | - | 0.551 [-,-] | - | - | 0.579 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +45 | POOLED | logit2 | - | 0.550 [-,-] | - | - | 0.638 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +15 | NY | logit2 | - | 0.549 [-,-] | - | - | 0.593 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +30 | NY | rf | - | 0.548 [-,-] | - | - | 0.546 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +30 | LONDON | logit2 | - | 0.547 [-,-] | - | - | 0.592 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +60 | NY | gbt3 | - | 0.547 [-,-] | - | - | 0.722 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/HM | rf | 0.573 [0.52,0.63] | 0.547 [0.46,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +30 | NY | rf | - | 0.544 [-,-] | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +45 | ASIA | gbt3 | - | 0.544 [-,-] | - | - | 0.531 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | pre | ASIA | logit2 | - | 0.544 [-,-] | - | - | 0.539 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10 | +30 | NY | gbt3 | - | 0.543 [-,-] | - | - | 0.623 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +20 | NY | logit2 | - | 0.541 [-,-] | - | - | 0.641 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +30 | ASIA | stack | - | 0.541 [-,-] | - | - | 0.532 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | ASIA/HM | logit2 | 0.515 [0.48,0.55] | 0.541 [0.49,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +60 | POOLED | rf | - | 0.541 [-,-] | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +15 | POOLED | rf | - | 0.540 [-,-] | - | - | 0.657 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +20 | POOLED | rf | - | 0.539 [-,-] | - | - | 0.638 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | POOLED/ST | rf | 0.538 [0.51,0.56] | 0.539 [0.51,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +15 | POOLED | logit2 | - | 0.538 [-,-] | - | - | 0.614 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/HM | rf | 0.560 [0.53,0.59] | 0.538 [0.49,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | POOLED | rf | 0.521 [0.50,0.54] | 0.538 [0.51,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | POOLED/HM | logit2 | 0.511 [0.49,0.54] | 0.537 [0.50,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | LONDON | logit2 | 0.534 [0.50,0.57] | 0.537 [0.48,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | ASIA/HM | stack | 0.510 [0.48,0.55] | 0.536 [0.49,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10 | +30 | ASIA | gbt3 | - | 0.535 [-,-] | - | - | 0.527 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | NY | logit2 | 0.530 [0.49,0.57] | 0.535 [0.48,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +15 | NY | logit2 | - | 0.534 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +45 | NY | gbt3 | - | 0.533 [-,-] | - | - | 0.636 | ok | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON | logit2 | 0.530 [0.49,0.56] | 0.533 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +20 | ASIA | rf | - | 0.533 [-,-] | - | - | 0.520 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | POOLED/HM | logit2 | 0.522 [0.50,0.55] | 0.532 [0.50,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +45 | POOLED | gbt3 | - | 0.532 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA/ST | gbt3 | 0.538 [0.50,0.57] | 0.531 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +30 | ASIA | stack | - | 0.530 [-,-] | - | - | 0.527 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +20 | POOLED | rf | - | 0.530 [-,-] | - | - | 0.654 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | POOLED | rf | 0.520 [0.50,0.54] | 0.528 [0.51,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | NY/HM | stack | 0.531 [0.48,0.58] | 0.528 [0.45,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +15 | ASIA | gbt3 | - | 0.528 [-,-] | - | - | 0.539 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | ASIA | rf | 0.526 [0.50,0.56] | 0.528 [0.49,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED | rf | 0.514 [0.49,0.54] | 0.527 [0.50,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/HM | logit2 | 0.520 [0.49,0.55] | 0.527 [0.49,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | LONDON/HM | rf | 0.524 [0.48,0.58] | 0.527 [0.45,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +5 | ASIA | stack | - | 0.527 [-,-] | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-G+base | sig | ASIA | stack | 0.510 [0.48,0.54] | 0.526 [0.49,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | ASIA | gbt3 | 0.522 [0.49,0.55] | 0.525 [0.48,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +20 | NY | stack | - | 0.525 [-,-] | - | - | 0.653 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | LONDON/ST | gbt3 | 0.521 [0.48,0.57] | 0.524 [0.46,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +10 | POOLED | rf | - | 0.524 [-,-] | - | - | 0.641 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | ASIA/HM | gbt3 | 0.528 [0.49,0.57] | 0.523 [0.47,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | LONDON | rf | 0.542 [0.51,0.58] | 0.523 [0.47,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +30 | ASIA | logit2 | - | 0.522 [-,-] | - | - | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED | rf | 0.511 [0.49,0.53] | 0.522 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY | rf | 0.522 [0.48,0.56] | 0.522 [0.46,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +60 | POOLED | rf | - | 0.521 [-,-] | - | - | 0.635 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/HM | gbt3 | 0.522 [0.46,0.58] | 0.521 [0.43,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | POOLED/HM | logit2 | 0.509 [0.49,0.53] | 0.520 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +45 | NY | gbt3 | - | 0.519 [-,-] | - | - | 0.662 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | NY/ST | stack | 0.532 [0.48,0.58] | 0.518 [0.44,0.59] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | NY/ST | stack | 0.521 [0.47,0.57] | 0.518 [0.45,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA | stack | 0.500 [0.47,0.53] | 0.518 [0.48,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | ASIA | stack | 0.511 [0.48,0.54] | 0.517 [0.48,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/HM | stack | 0.515 [0.48,0.55] | 0.517 [0.46,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | NY | rf | 0.523 [0.48,0.56] | 0.516 [0.45,0.58] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/HM | rf | 0.512 [0.49,0.53] | 0.515 [0.49,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | LONDON | gbt3 | 0.525 [0.49,0.56] | 0.515 [0.46,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +45 | ASIA | logit2 | - | 0.515 [-,-] | - | - | 0.499 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/ST | gbt3 | 0.521 [0.49,0.55] | 0.515 [0.48,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | ASIA/ST | rf | 0.512 [0.48,0.54] | 0.514 [0.47,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | LONDON/ST | rf | 0.540 [0.49,0.59] | 0.514 [0.45,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | ASIA/HM | stack | 0.505 [0.47,0.54] | 0.514 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +20 | ASIA | stack | - | 0.513 [-,-] | - | - | 0.503 | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | NY | stack | 0.515 [0.48,0.55] | 0.512 [0.45,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +15 | LONDON | gbt3 | - | 0.511 [-,-] | - | - | 0.531 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +15 | NY | rf | - | 0.511 [-,-] | - | - | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11 | +30 | LONDON | rf | - | 0.510 [-,-] | - | - | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | POOLED/ST | stack | 0.504 [0.48,0.53] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/ST | gbt3 | 0.517 [0.47,0.57] | 0.508 [0.44,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | POOLED/ST | stack | 0.503 [0.48,0.53] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G+base | sig | POOLED/ST | stack | 0.508 [0.48,0.53] | 0.507 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9 | +15 | POOLED | stack | - | 0.506 [-,-] | - | - | 0.619 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +15 | POOLED | rf | - | 0.505 [-,-] | - | - | 0.621 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | POOLED | gbt3 | 0.508 [0.49,0.53] | 0.505 [0.48,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10 | +15 | ASIA | gbt3 | - | 0.505 [-,-] | - | - | 0.496 | N | - | - | - | - |  | locked label (reference only) |
| G-baseline-FAILPRED | sig | ASIA/ST | logit2 | 0.506 [0.47,0.54] | 0.505 [0.45,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | ASIA/ST | stack | 0.506 [0.47,0.54] | 0.504 [0.45,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10 | +30 | POOLED | stack | - | 0.503 [-,-] | - | - | 0.608 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | ASIA/ST | gbt3 | 0.526 [0.49,0.56] | 0.503 [0.46,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +30 | POOLED | stack | - | 0.502 [-,-] | - | - | 0.620 | - | - | - | - | - | stack | locked label (reference only) |
| E8-12-G | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.502 [0.47,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9 | +30 | ASIA | stack | - | 0.501 [-,-] | - | - | 0.492 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +5 | NY | rf | - | 0.501 [-,-] | - | - | 0.672 | ok | - | - | - | - | stack | locked label (reference only) |
| E-sub-E9 | +30 | POOLED | logit2 | - | 0.501 [-,-] | - | - | 0.601 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +15 | ASIA | logit2 | - | 0.500 [-,-] | - | - | 0.500 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E10 | +30 | LONDON | stack | - | 0.499 [-,-] | - | - | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +30 | NY | stack | - | 0.499 [-,-] | - | - | 0.560 | - | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +30 | LONDON | logit2 | - | 0.498 [-,-] | - | - | 0.546 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E10 | +15 | LONDON | stack | - | 0.497 [-,-] | - | - | 0.530 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/ST | gbt3 | 0.534 [0.48,0.59] | 0.496 [0.42,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/ST | gbt3 | 0.516 [0.49,0.54] | 0.496 [0.46,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED/HM | gbt3 | 0.514 [0.49,0.54] | 0.494 [0.45,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/ST | stack | 0.498 [0.45,0.54] | 0.494 [0.43,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +15 | POOLED | logit2 | - | 0.494 [-,-] | - | - | 0.595 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +30 | NY | gbt3 | - | 0.493 [-,-] | - | - | 0.549 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +10 | NY | logit2 | - | 0.492 [-,-] | - | - | 0.587 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E9 | +30 | NY | stack | - | 0.492 [-,-] | - | - | 0.592 | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY/HM | stack | 0.529 [0.48,0.58] | 0.491 [0.42,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | LONDON/HM | logit2 | 0.490 [0.45,0.53] | 0.491 [0.43,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-baseline-FAILPRED | sig | LONDON/HM | gbt3 | 0.488 [0.44,0.54] | 0.491 [0.43,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +15 | LONDON | gbt3 | - | 0.489 [-,-] | - | - | 0.515 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA/ST | gbt3 | 0.521 [0.49,0.55] | 0.488 [0.44,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E10 | +15 | POOLED | rf | - | 0.487 [-,-] | - | - | 0.601 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | NY/HM | logit2 | 0.514 [0.47,0.57] | 0.487 [0.41,0.57] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E12 | +30 | POOLED | logit2 | - | 0.486 [-,-] | - | - | 0.573 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-G+base | sig | ASIA/ST | logit2 | 0.495 [0.46,0.53] | 0.486 [0.44,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +5 | LONDON | rf | - | 0.485 [-,-] | - | - | 0.590 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | LONDON | gbt3 | 0.479 [0.45,0.51] | 0.484 [0.43,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +15 | ASIA | logit2 | - | 0.484 [-,-] | - | - | 0.476 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | NY | logit2 | 0.496 [0.45,0.54] | 0.484 [0.42,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +10 | ASIA | rf | - | 0.482 [-,-] | - | - | 0.481 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | LONDON/HM | logit2 | 0.509 [0.46,0.56] | 0.482 [0.42,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | LONDON/HM | gbt3 | 0.487 [0.44,0.54] | 0.482 [0.41,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +30 | LONDON | logit2 | - | 0.481 [-,-] | - | - | 0.501 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +30 | LONDON | gbt3 | - | 0.481 [-,-] | - | - | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | POOLED | rf | 0.484 [0.46,0.51] | 0.481 [0.45,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-context | sig | ASIA | stack | 0.510 [0.48,0.54] | 0.480 [0.44,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E9 | +15 | NY | rf | - | 0.479 [-,-] | - | - | 0.586 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/HM | logit2 | 0.477 [0.43,0.52] | 0.478 [0.41,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | NY/ST | gbt3 | 0.488 [0.44,0.54] | 0.478 [0.42,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-G+base | sig | NY | gbt3 | 0.501 [0.46,0.54] | 0.476 [0.41,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | +10 | NY | gbt3 | - | 0.476 [-,-] | - | - | 0.639 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base-pertype | +15 | NY | logit2 | - | 0.474 [-,-] | - | - | 0.636 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E11 | +30 | POOLED | stack | - | 0.470 [-,-] | - | - | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +10 | POOLED | rf | - | 0.470 [-,-] | - | - | 0.598 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +15 | POOLED | rf | - | 0.470 [-,-] | - | - | 0.568 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-G | sig | LONDON | gbt3 | 0.502 [0.46,0.54] | 0.469 [0.42,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +15 | ASIA | rf | - | 0.469 [-,-] | - | - | 0.462 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E10 | +15 | NY | logit2 | - | 0.468 [-,-] | - | - | 0.578 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +15 | POOLED | logit2 | - | 0.468 [-,-] | - | - | 0.564 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | +5 | POOLED | rf | - | 0.466 [-,-] | - | - | 0.626 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | pre | ASIA | gbt3 | - | 0.464 [-,-] | - | - | 0.467 | N | - | - | - | - |  | locked label (reference only) |
| G-context | sig | LONDON/ST | gbt3 | 0.479 [0.44,0.52] | 0.464 [0.41,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | pre | POOLED | logit2 | - | 0.461 [-,-] | - | - | 0.559 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base-pertype | +30 | NY | logit2 | - | 0.460 [-,-] | - | - | 0.739 | - | - | - | - | - | stack | locked label (reference only) |
| E-sub-E8 | +30 | ASIA | gbt3 | - | 0.460 [-,-] | - | - | 0.471 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +5 | ASIA | gbt3 | - | 0.459 [-,-] | - | - | 0.464 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +30 | ASIA | stack | - | 0.459 [-,-] | - | - | 0.466 | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E11 | +15 | ASIA | stack | - | 0.455 [-,-] | - | - | 0.453 | - | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +60 | ASIA | gbt3 | - | 0.454 [-,-] | - | - | 0.451 | N | - | - | - | - |  | locked label (reference only) |
| E-sub-E8 | +30 | POOLED | gbt3 | - | 0.452 [-,-] | - | - | 0.561 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | pre | LONDON | gbt3 | - | 0.449 [-,-] | - | - | 0.547 | ok | - | - | - | - | stack | locked label (reference only) |
| E8-12-all | +5 | NY | logit2 | - | 0.447 [-,-] | - | - | 0.563 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | +5 | POOLED | gbt3 | - | 0.443 [-,-] | - | - | 0.589 | N | - | - | - | - |  | locked label (reference only) |
| E1-12-all+base | pre | NY | gbt3 | - | 0.436 [-,-] | - | - | 0.598 | ok | - | - | - | - | stack | locked label (reference only) |
| E1-12-all+base | pre | POOLED | gbt3 | - | 0.433 [-,-] | - | - | 0.586 | ok | - | - | - | - | stack | locked label (reference only) |
| G-context | sig | LONDON | gbt3 | 0.454 [0.42,0.49] | 0.433 [0.38,0.48] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| E-sub-E12 | +15 | LONDON | gbt3 | - | 0.427 [-,-] | - | - | 0.452 | N | - | - | - | - |  | locked label (reference only) |
| E8-12-all | pre | NY | stack | - | 0.400 [-,-] | - | - | 0.495 | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- E8-12-all 10 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 45 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 20 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 60 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 45 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 5 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 0 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 0 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 10 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 10 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 5 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 20 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 10 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 60 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 5 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 5 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 0 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 45 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 20 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 0 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 20 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 45 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 60 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-all 60 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 60 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 45 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 5 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 45 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 10 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 10 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 60 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 5 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 20 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 20 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 0 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 5 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 5 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 10 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 0 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 10 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 60 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 45 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 20 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 45 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 0 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 20 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 0 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base 60 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E10 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E11 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E12 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E8 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E-sub-E9 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 30 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 30 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 30 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 15 POOLED: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 15 LONDON: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 15 NY: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 15 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E1-12-all+base-pertype 30 ASIA: E8-E12 block; econ grid not run (no WF-PRE gain >= 0.02 pooled over Round-0)
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 ASIA: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 NY: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 NY: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- E8-12-G -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 NY: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- E8-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 NY: G per-signal; no E8-E12 gain
- E8-12-G -1 NY: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 POOLED: G per-signal; no E8-E12 gain
- E1-12-G+base -1 POOLED: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 LONDON: G per-signal; no E8-E12 gain
- E8-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
- E1-12-G+base -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 POOLED: G per-signal; no E8-E12 gain
- E8-12-G -1 ASIA: G per-signal; no E8-E12 gain
- G-baseline-FAILPRED -1 ASIA: G per-signal; no E8-E12 gain
- E1-12-G+base -1 ASIA: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
- G-context -1 LONDON: G per-signal; no E8-E12 gain
