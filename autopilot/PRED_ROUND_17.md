# PRED ROUND 17 - block F round 2 - F5-F8 (rotation, acceptance/rejection, wick tails, path volume)

Best HOLDOUT F-R AUC: +15 POOLED 0.541 [-,-] | ASIA 0.575 [-,-] | LONDON 0.585 [-,-] | NY 0.563 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.535 [-,-] | ASIA 0.551 [-,-] | LONDON 0.538 [-,-] | NY 0.588 [-,-]
Best G HOLDOUT AUC: 0.614 [0.58,0.64]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 6954c24979e66dfa65cf8689a275985476c650234e39c4425f43e8506679aaf1 ; trials added 3000 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/F5678_auction2.parquet', 'l2vast/pred/store/F5678_auction2_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G-F1-8+base | sig | ASIA | rf | 0.579 [0.55,0.61] | 0.614 [0.58,0.64] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | LONDON | logit2 | 0.620 [0.59,0.65] | 0.610 [0.56,0.66] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | LONDON | logit2 | 0.628 [0.59,0.66] | 0.606 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | NY | logit2 | 0.611 [0.58,0.64] | 0.604 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +20 | NY | logit2 | - | 0.598 [-,-] | - | - | 0.613 | N | - | - | - | - |  | locked label (reference only) |
| G-F1-8+base | sig | POOLED/ST | logit2 | 0.586 [0.56,0.61] | 0.590 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +30 | NY | logit2 | - | 0.588 [-,-] | - | - | 0.711 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +15 | LONDON | stack | - | 0.585 [-,-] | - | - | 0.607 | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | logit2 | 0.582 [0.56,0.60] | 0.583 [0.55,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +60 | NY | logit2 | - | 0.583 [-,-] | - | - | 0.708 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | POOLED | logit2 | 0.583 [0.57,0.60] | 0.582 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +30 | NY | logit2 | - | 0.581 [-,-] | - | - | 0.632 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +60 | NY | logit2 | - | 0.579 [-,-] | - | - | 0.716 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | POOLED/HM | rf | 0.567 [0.54,0.59] | 0.579 [0.55,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | ASIA | gbt3 | 0.565 [0.53,0.60] | 0.577 [0.54,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F5678 | sig | ASIA | logit2 | 0.568 [0.54,0.60] | 0.576 [0.54,0.61] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F7-wick+base | +15 | ASIA | logit2 | - | 0.575 [-,-] | - | - | 0.585 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED | logit2 | 0.578 [0.56,0.59] | 0.574 [0.55,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | POOLED | rf | 0.564 [0.54,0.59] | 0.574 [0.55,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8+base | sig | POOLED/HM | logit2 | 0.579 [0.55,0.60] | 0.573 [0.54,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +45 | LONDON | stack | - | 0.571 [-,-] | - | - | 0.587 | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | POOLED/ST | rf | 0.562 [0.54,0.59] | 0.568 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F5678 | sig | POOLED/HM | gbt3 | 0.565 [0.54,0.59] | 0.568 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F5678 | sig | POOLED | gbt3 | 0.562 [0.54,0.58] | 0.567 [0.55,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | LONDON | logit2 | 0.554 [0.52,0.59] | 0.567 [0.53,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/HM | logit2 | 0.575 [0.55,0.59] | 0.566 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | pre | ASIA | logit2 | - | 0.565 [-,-] | - | - | 0.569 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +30 | NY | logit2 | - | 0.565 [-,-] | - | - | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +60 | NY | logit2 | - | 0.565 [-,-] | - | - | 0.599 | N | - | - | - | - |  | locked label (reference only) |
| F5678-only | +15 | NY | logit2 | - | 0.563 [-,-] | - | - | 0.610 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base-pertype | +15 | ASIA | logit2 | - | 0.561 [-,-] | - | - | 0.570 | - | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | POOLED/ST | logit2 | 0.555 [0.53,0.58] | 0.560 [0.53,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F5678 | sig | LONDON | logit2 | 0.538 [0.50,0.57] | 0.559 [0.51,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | ASIA | gbt3 | 0.543 [0.52,0.57] | 0.559 [0.52,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678+base | pre | ASIA | logit2 | - | 0.558 [-,-] | - | - | 0.563 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +60 | ASIA | stack | - | 0.557 [-,-] | - | - | 0.553 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +45 | NY | logit2 | - | 0.557 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| F6-acceptance+base | +30 | NY | gbt3 | - | 0.557 [-,-] | - | - | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +10 | ASIA | logit2 | - | 0.557 [-,-] | - | - | 0.552 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +45 | POOLED | rf | - | 0.556 [-,-] | - | - | 0.664 | ok | - | - | - | - | stack | locked label (reference only) |
| F7-wick+base | +15 | NY | stack | - | 0.556 [-,-] | - | - | 0.811 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +10 | ASIA | logit2 | - | 0.554 [-,-] | - | - | 0.544 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | NY | logit2 | 0.592 [0.55,0.63] | 0.554 [0.49,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +45 | POOLED | rf | - | 0.553 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +30 | ASIA | gbt3 | - | 0.551 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| F7-wick+base | +30 | ASIA | logit2 | - | 0.550 [-,-] | - | - | 0.532 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +45 | ASIA | stack | - | 0.548 [-,-] | - | - | 0.534 | - | - | - | - | - | stack | locked label (reference only) |
| F6-acceptance+base | +15 | ASIA | logit2 | - | 0.548 [-,-] | - | - | 0.561 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +45 | LONDON | stack | - | 0.547 [-,-] | - | - | 0.633 | - | - | - | - | - | stack | locked label (reference only) |
| F5-rotation+base | +15 | ASIA | logit2 | - | 0.544 [-,-] | - | - | 0.558 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +10 | LONDON | gbt3 | - | 0.543 [-,-] | - | - | 0.653 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | POOLED/HM | gbt3 | 0.536 [0.51,0.56] | 0.543 [0.51,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F8-pathvol+base | +15 | ASIA | logit2 | - | 0.543 [-,-] | - | - | 0.557 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +15 | LONDON | stack | - | 0.542 [-,-] | - | - | 0.676 | - | - | - | - | - | stack | locked label (reference only) |
| F8-pathvol+base | +15 | POOLED | gbt3 | - | 0.541 [-,-] | - | - | 0.708 | ok | - | - | - | - | stack | locked label (reference only) |
| F5-rotation+base | +30 | ASIA | logit2 | - | 0.541 [-,-] | - | - | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base-pertype | +30 | ASIA | logit2 | - | 0.541 [-,-] | - | - | 0.550 | - | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | NY | rf | 0.561 [0.52,0.60] | 0.540 [0.49,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F8-pathvol+base | +30 | NY | gbt3 | - | 0.539 [-,-] | - | - | 0.797 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +30 | LONDON | stack | - | 0.538 [-,-] | - | - | 0.664 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +45 | NY | logit2 | - | 0.538 [-,-] | - | - | 0.593 | N | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +45 | LONDON | stack | - | 0.537 [-,-] | - | - | 0.599 | - | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | LONDON | rf | 0.523 [0.49,0.55] | 0.537 [0.50,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +60 | ASIA | stack | - | 0.536 [-,-] | - | - | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +10 | ASIA | logit2 | - | 0.536 [-,-] | - | - | 0.529 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +45 | ASIA | stack | - | 0.536 [-,-] | - | - | 0.525 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +15 | POOLED | stack | - | 0.536 [-,-] | - | - | 0.694 | - | - | - | - | - | stack | locked label (reference only) |
| F6-acceptance+base | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | LONDON | logit2 | 0.510 [0.48,0.55] | 0.533 [0.49,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F6-acceptance+base | +15 | POOLED | gbt3 | - | 0.532 [-,-] | - | - | 0.702 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | LONDON | logit2 | 0.530 [0.49,0.56] | 0.532 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F6-acceptance+base | +30 | ASIA | logit2 | - | 0.531 [-,-] | - | - | 0.514 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +5 | ASIA | logit2 | - | 0.530 [-,-] | - | - | 0.527 | N | - | - | - | - |  | locked label (reference only) |
| F7-wick+base | +30 | LONDON | gbt3 | - | 0.530 [-,-] | - | - | 0.658 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +10 | NY | gbt3 | - | 0.530 [-,-] | - | - | 0.722 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +15 | ASIA | stack | - | 0.529 [-,-] | - | - | 0.515 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +45 | ASIA | stack | - | 0.529 [-,-] | - | - | 0.521 | - | - | - | - | - |  | locked label (reference only) |
| G-F5678 | sig | ASIA | gbt3 | 0.540 [0.51,0.56] | 0.528 [0.49,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +30 | ASIA | gbt3 | - | 0.528 [-,-] | - | - | 0.527 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +30 | POOLED | rf | - | 0.528 [-,-] | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | POOLED | gbt3 | 0.525 [0.51,0.54] | 0.527 [0.51,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +20 | LONDON | stack | - | 0.527 [-,-] | - | - | 0.544 | - | - | - | - | - |  | locked label (reference only) |
| F8-pathvol+base | +30 | POOLED | gbt3 | - | 0.527 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +15 | ASIA | stack | - | 0.526 [-,-] | - | - | 0.533 | - | - | - | - | - | stack | locked label (reference only) |
| F8-pathvol+base | +30 | ASIA | logit2 | - | 0.526 [-,-] | - | - | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +60 | POOLED | logit2 | - | 0.526 [-,-] | - | - | 0.625 | N | - | - | - | - |  | locked label (reference only) |
| F7-wick+base | +30 | POOLED | gbt3 | - | 0.526 [-,-] | - | - | 0.679 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | ASIA | stack | 0.503 [0.48,0.53] | 0.526 [0.48,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | POOLED | rf | 0.523 [0.50,0.54] | 0.525 [0.50,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678+base | +30 | ASIA | gbt3 | - | 0.525 [-,-] | - | - | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| F5-rotation+base | +15 | POOLED | gbt3 | - | 0.524 [-,-] | - | - | 0.690 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +15 | POOLED | stack | - | 0.524 [-,-] | - | - | 0.621 | - | - | - | - | - |  | locked label (reference only) |
| F5678+base-pertype | +15 | NY | stack | - | 0.524 [-,-] | - | - | 0.670 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +45 | POOLED | rf | - | 0.523 [-,-] | - | - | 0.622 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base-pertype | +30 | LONDON | gbt3 | - | 0.523 [-,-] | - | - | 0.580 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +10 | POOLED | gbt3 | - | 0.523 [-,-] | - | - | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +60 | ASIA | stack | - | 0.522 [-,-] | - | - | 0.527 | - | - | - | - | - | stack | locked label (reference only) |
| F6-acceptance+base | +15 | NY | stack | - | 0.522 [-,-] | - | - | 0.800 | - | - | - | - | - | stack | locked label (reference only) |
| F5-rotation+base | +30 | POOLED | gbt3 | - | 0.521 [-,-] | - | - | 0.675 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | NY | rf | 0.521 [0.48,0.56] | 0.521 [0.46,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +5 | ASIA | logit2 | - | 0.521 [-,-] | - | - | 0.517 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | NY | gbt3 | 0.558 [0.52,0.60] | 0.520 [0.46,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8+base | sig | POOLED/HM | logit2 | 0.527 [0.50,0.56] | 0.520 [0.48,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | logit2 | 0.504 [0.48,0.53] | 0.519 [0.48,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F8-pathvol+base | +15 | NY | stack | - | 0.519 [-,-] | - | - | 0.801 | - | - | - | - | - | stack | locked label (reference only) |
| F7-wick+base | +30 | NY | gbt3 | - | 0.519 [-,-] | - | - | 0.792 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED | rf | 0.509 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | pre | LONDON | stack | - | 0.518 [-,-] | - | - | 0.657 | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/HM | rf | 0.520 [0.50,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F7-wick+base | +15 | POOLED | gbt3 | - | 0.518 [-,-] | - | - | 0.687 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +30 | LONDON | stack | - | 0.518 [-,-] | - | - | 0.626 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base-pertype | +15 | LONDON | stack | - | 0.517 [-,-] | - | - | 0.530 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +15 | POOLED | stack | - | 0.517 [-,-] | - | - | 0.654 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +20 | NY | logit2 | - | 0.516 [-,-] | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +30 | POOLED | rf | - | 0.515 [-,-] | - | - | 0.624 | N | - | - | - | - |  | locked label (reference only) |
| F6-acceptance+base | +30 | LONDON | gbt3 | - | 0.515 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +5 | ASIA | logit2 | - | 0.515 [-,-] | - | - | 0.512 | ok | - | - | - | - | stack | locked label (reference only) |
| F5-rotation+base | +15 | NY | stack | - | 0.514 [-,-] | - | - | 0.799 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | pre | LONDON | stack | - | 0.513 [-,-] | - | - | 0.654 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +30 | POOLED | rf | - | 0.513 [-,-] | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| F8-pathvol+base | +30 | LONDON | gbt3 | - | 0.513 [-,-] | - | - | 0.651 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | POOLED | logit2 | 0.517 [0.50,0.54] | 0.513 [0.49,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +60 | POOLED | logit2 | - | 0.512 [-,-] | - | - | 0.656 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +45 | NY | logit2 | - | 0.512 [-,-] | - | - | 0.666 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | POOLED/ST | gbt3 | 0.515 [0.49,0.54] | 0.511 [0.48,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5-rotation+base | +30 | LONDON | gbt3 | - | 0.511 [-,-] | - | - | 0.641 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +20 | POOLED | stack | - | 0.510 [-,-] | - | - | 0.615 | - | - | - | - | - |  | locked label (reference only) |
| F5-rotation+base | +30 | NY | gbt3 | - | 0.509 [-,-] | - | - | 0.790 | ok | - | - | - | - | stack | locked label (reference only) |
| F8-pathvol+base | +15 | LONDON | stack | - | 0.509 [-,-] | - | - | 0.682 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +60 | POOLED | logit2 | - | 0.508 [-,-] | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +20 | NY | logit2 | - | 0.508 [-,-] | - | - | 0.677 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | POOLED/HM | logit2 | 0.516 [0.49,0.54] | 0.508 [0.47,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | +15 | ASIA | stack | - | 0.508 [-,-] | - | - | 0.496 | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +15 | LONDON | stack | - | 0.507 [-,-] | - | - | 0.618 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +30 | LONDON | stack | - | 0.506 [-,-] | - | - | 0.540 | - | - | - | - | - |  | locked label (reference only) |
| F5678+base | +20 | POOLED | stack | - | 0.506 [-,-] | - | - | 0.678 | - | - | - | - | - | stack | locked label (reference only) |
| G-F5678 | sig | NY | gbt3 | 0.515 [0.47,0.56] | 0.506 [0.44,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5-rotation+base | +15 | LONDON | stack | - | 0.503 [-,-] | - | - | 0.670 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +5 | LONDON | stack | - | 0.503 [-,-] | - | - | 0.513 | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +10 | POOLED | gbt3 | - | 0.502 [-,-] | - | - | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +60 | LONDON | stack | - | 0.502 [-,-] | - | - | 0.479 | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8+base | sig | ASIA | gbt3 | 0.516 [0.49,0.55] | 0.501 [0.47,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +20 | ASIA | rf | - | 0.498 [-,-] | - | - | 0.494 | N | - | - | - | - |  | locked label (reference only) |
| F5678-only | +10 | LONDON | gbt3 | - | 0.497 [-,-] | - | - | 0.503 | N | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +15 | NY | logit2 | - | 0.497 [-,-] | - | - | 0.672 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +20 | ASIA | rf | - | 0.495 [-,-] | - | - | 0.482 | ok | - | - | - | - | stack | locked label (reference only) |
| F7-wick+base | +15 | LONDON | stack | - | 0.495 [-,-] | - | - | 0.661 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +10 | LONDON | gbt3 | - | 0.495 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | LONDON | logit2 | 0.519 [0.48,0.55] | 0.494 [0.45,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +20 | POOLED | stack | - | 0.494 [-,-] | - | - | 0.665 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +20 | LONDON | stack | - | 0.493 [-,-] | - | - | 0.653 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +20 | ASIA | rf | - | 0.490 [-,-] | - | - | 0.470 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F1-8+base | sig | POOLED/ST | gbt3 | 0.502 [0.47,0.53] | 0.489 [0.45,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | pre | POOLED | gbt3 | - | 0.488 [-,-] | - | - | 0.654 | ok | - | - | - | - | stack | locked label (reference only) |
| F6-acceptance+base | +15 | LONDON | stack | - | 0.488 [-,-] | - | - | 0.671 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +5 | POOLED | logit2 | - | 0.487 [-,-] | - | - | 0.582 | N | - | - | - | - |  | locked label (reference only) |
| G-F1-8 | sig | NY | rf | 0.515 [0.47,0.55] | 0.487 [0.43,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | pre | LONDON | stack | - | 0.484 [-,-] | - | - | 0.533 | - | - | - | - | - |  | locked label (reference only) |
| G-F1-8+base | sig | NY | rf | 0.515 [0.48,0.55] | 0.483 [0.42,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +20 | LONDON | stack | - | 0.482 [-,-] | - | - | 0.652 | - | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | ASIA | gbt3 | 0.508 [0.48,0.54] | 0.481 [0.44,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | pre | ASIA | logit2 | - | 0.480 [-,-] | - | - | 0.483 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | pre | POOLED | gbt3 | - | 0.479 [-,-] | - | - | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +10 | POOLED | gbt3 | - | 0.474 [-,-] | - | - | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +10 | NY | gbt3 | - | 0.473 [-,-] | - | - | 0.740 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +60 | LONDON | stack | - | 0.471 [-,-] | - | - | 0.635 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +60 | LONDON | stack | - | 0.469 [-,-] | - | - | 0.653 | - | - | - | - | - | stack | locked label (reference only) |
| G-F1-8 | sig | POOLED/ST | gbt3 | 0.497 [0.47,0.53] | 0.468 [0.44,0.50] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F5678-only | pre | NY | stack | - | 0.465 [-,-] | - | - | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| F1-8+base | +5 | LONDON | stack | - | 0.460 [-,-] | - | - | 0.609 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +5 | LONDON | stack | - | 0.460 [-,-] | - | - | 0.612 | - | - | - | - | - | stack | locked label (reference only) |
| F5678+base | +15 | NY | logit2 | - | 0.460 [-,-] | - | - | 0.661 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | pre | NY | stack | - | 0.455 [-,-] | - | - | 0.686 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +5 | POOLED | logit2 | - | 0.454 [-,-] | - | - | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base | pre | NY | stack | - | 0.453 [-,-] | - | - | 0.673 | - | - | - | - | - | stack | locked label (reference only) |
| F5678-only | pre | POOLED | gbt3 | - | 0.445 [-,-] | - | - | 0.551 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +5 | POOLED | logit2 | - | 0.441 [-,-] | - | - | 0.608 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +5 | NY | gbt3 | - | 0.439 [-,-] | - | - | 0.560 | N | - | - | - | - |  | locked label (reference only) |
| F5678+base | +5 | NY | gbt3 | - | 0.439 [-,-] | - | - | 0.685 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678+base-pertype | +30 | NY | gbt3 | - | 0.437 [-,-] | - | - | 0.758 | - | - | - | - | - | stack | locked label (reference only) |
| F1-8+base | +5 | NY | gbt3 | - | 0.429 [-,-] | - | - | 0.649 | ok | - | - | - | - | stack | locked label (reference only) |
| F5678-only | +10 | NY | gbt3 | - | 0.418 [-,-] | - | - | 0.541 | N | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- F5678-only 0 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 0 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 0 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 0 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 0 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 0 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 0 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 0 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 0 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 0 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 0 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 0 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 5 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 5 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 5 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 5 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 5 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 5 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 5 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 5 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 5 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 5 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 5 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 5 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 10 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 10 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 10 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 10 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 10 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 10 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 10 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 10 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 10 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 10 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 10 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 10 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5-rotation+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F6-acceptance+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F7-wick+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F8-pathvol+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base-pertype 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 20 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 20 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 20 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 20 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 20 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 20 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 20 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 20 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 20 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 20 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 20 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 20 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 45 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 45 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 45 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 45 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 45 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 45 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 45 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 45 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 45 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 45 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 45 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 45 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 60 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 60 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 60 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 60 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 60 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 60 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 60 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 60 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 60 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678-only 60 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F5678+base 60 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-8+base 60 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F5678 -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F1-8+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
