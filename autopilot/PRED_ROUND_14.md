# PRED ROUND 14 - block X1 round 1 - X3-multitask+X1-ranking-loss

Best HOLDOUT F-R AUC: +15 POOLED 0.549 [-,-] | ASIA 0.553 [-,-] | LONDON 0.550 [-,-] | NY 0.556 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.577 [-,-] | ASIA 0.554 [-,-] | LONDON 0.566 [-,-] | NY 0.573 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg dc15418ff43726d433c5fadc77f2893eda19059fc52b12eb70801f29f7eb96d2 ; trials added 1000 ; truncation audit {'decisions': 48, 'mismatches': 0, 'fixed_and_rerun': False, 'source': 'FAILPRED R9 inherited + pipeline test'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X3-multitask | +60 | NY | mt_rf | - | 0.626 [-,-] | - | 0.637 | 0.856 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | LONDON | ctrl_logit2 | - | 0.603 [-,-] | - | 0.606 | 0.615 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +60 | NY | prod_ll | - | 0.596 [-,-] | - | 0.609 | 0.873 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +20 | NY | mt_rf | - | 0.594 [-,-] | - | 0.600 | 0.851 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | NY | ctrl_gbt3 | - | 0.588 [-,-] | - | 0.595 | 0.798 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +60 | ASIA | mt_gbt3 | - | 0.585 [-,-] | - | 0.565 | 0.555 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | LONDON | ctrl_gbt3 | - | 0.584 [-,-] | - | 0.577 | 0.699 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +45 | NY | prod_pair | - | 0.582 [-,-] | - | 0.606 | 0.827 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +45 | NY | mt_rf | - | 0.578 [-,-] | - | 0.579 | 0.833 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +30 | POOLED | mt_rf | - | 0.577 [-,-] | - | 0.566 | 0.719 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +45 | ASIA | mt_gbt3 | - | 0.574 [-,-] | - | 0.559 | 0.551 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | NY | ctrl_gbt3 | - | 0.573 [-,-] | - | 0.599 | 0.818 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +30 | POOLED | cs_pair | - | 0.572 [-,-] | - | 0.550 | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +5 | ASIA | mt_gbt3 | - | 0.569 [-,-] | - | 0.556 | 0.571 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +5 | POOLED | cs_ll | - | 0.566 [-,-] | - | 0.547 | 0.500 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | LONDON | ctrl_gbt3 | - | 0.566 [-,-] | - | 0.550 | 0.673 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | LONDON | ctrl_logit2 | - | 0.564 [-,-] | - | 0.558 | 0.585 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +45 | POOLED | mt_rf | - | 0.564 [-,-] | - | 0.559 | 0.710 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | NY | ctrl_logit2 | - | 0.564 [-,-] | - | 0.560 | 0.713 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +20 | POOLED | mt_rf | - | 0.564 [-,-] | - | 0.554 | 0.711 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +60 | POOLED | mt_rf | - | 0.562 [-,-] | - | 0.557 | 0.716 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +30 | NY | mt_gbt3 | - | 0.561 [-,-] | - | 0.574 | 0.842 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | ASIA | ctrl_logit2 | - | 0.561 [-,-] | - | 0.542 | 0.563 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | NY | ctrl_gbt3 | - | 0.560 [-,-] | - | 0.554 | 0.827 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | pre | LONDON | mt_rf | - | 0.559 [-,-] | - | 0.555 | 0.666 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +60 | LONDON | mt_rf | - | 0.558 [-,-] | - | 0.562 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +45 | LONDON | cs_ll | - | 0.557 [-,-] | - | 0.535 | 0.584 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | NY | ctrl_gbt3 | - | 0.557 [-,-] | - | 0.586 | 0.862 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +10 | POOLED | cs_pair | - | 0.556 [-,-] | - | 0.523 | 0.489 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +20 | ASIA | mt_gbt3 | - | 0.556 [-,-] | - | 0.547 | 0.554 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +10 | ASIA | mt_rf | - | 0.556 [-,-] | - | 0.546 | 0.547 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | LONDON | ctrl_gbt3 | - | 0.556 [-,-] | - | 0.546 | 0.693 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +15 | NY | mt_rf | - | 0.556 [-,-] | - | 0.564 | 0.833 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +45 | POOLED | cs_ll | - | 0.555 [-,-] | - | 0.526 | 0.537 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +20 | LONDON | mt_rf | - | 0.554 [-,-] | - | 0.549 | 0.672 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +30 | ASIA | mt_gbt3 | - | 0.554 [-,-] | - | 0.542 | 0.543 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | ASIA | ctrl_gbt3 | - | 0.553 [-,-] | - | 0.553 | 0.572 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | ASIA | ctrl_logit2 | - | 0.550 [-,-] | - | 0.539 | 0.554 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +30 | NY | cs_pair | - | 0.550 [-,-] | - | 0.533 | 0.575 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +15 | LONDON | mt_rf | - | 0.550 [-,-] | - | 0.552 | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +10 | LONDON | cs_pair | - | 0.550 [-,-] | - | 0.524 | 0.522 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +5 | ASIA | cs_ll | - | 0.549 [-,-] | - | 0.537 | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +20 | POOLED | cs_pair | - | 0.549 [-,-] | - | 0.532 | 0.506 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +15 | POOLED | mt_rf | - | 0.549 [-,-] | - | 0.537 | 0.700 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +20 | LONDON | cs_ll | - | 0.549 [-,-] | - | 0.538 | 0.579 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | pre | ASIA | mt_rf | - | 0.547 [-,-] | - | 0.539 | 0.545 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +30 | LONDON | mt_rf | - | 0.546 [-,-] | - | 0.541 | 0.680 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +15 | ASIA | mt_rf | - | 0.546 [-,-] | - | 0.539 | 0.537 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | pre | ASIA | cs_ll | - | 0.546 [-,-] | - | 0.521 | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | POOLED | ctrl_gbt3 | - | 0.545 [-,-] | - | 0.535 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | ASIA | ctrl_gbt3 | - | 0.545 [-,-] | - | 0.539 | 0.530 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +30 | LONDON | cs_pair | - | 0.545 [-,-] | - | 0.546 | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | POOLED | ctrl_logit2 | - | 0.544 [-,-] | - | 0.543 | 0.663 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +30 | NY | prod_pair | - | 0.544 [-,-] | - | 0.556 | 0.835 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +15 | POOLED | cs_pair | - | 0.543 [-,-] | - | 0.516 | 0.505 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | ASIA | ctrl_logit2 | - | 0.543 [-,-] | - | 0.533 | 0.548 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +45 | LONDON | mt_rf | - | 0.542 [-,-] | - | 0.557 | 0.672 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +30 | ASIA | cs_pair | - | 0.541 [-,-] | - | 0.530 | 0.519 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +5 | LONDON | cs_ll | - | 0.539 [-,-] | - | 0.534 | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | LONDON | ctrl_logit2 | - | 0.539 [-,-] | - | 0.550 | 0.593 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | ASIA | ctrl_logit2 | - | 0.539 [-,-] | - | 0.532 | 0.554 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | POOLED | ctrl_gbt3 | - | 0.538 [-,-] | - | 0.531 | 0.687 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +60 | POOLED | cs_pair | - | 0.537 [-,-] | - | 0.515 | 0.491 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +10 | POOLED | mt_rf | - | 0.537 [-,-] | - | 0.528 | 0.690 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | NY | ctrl_gbt3 | - | 0.536 [-,-] | - | 0.549 | 0.721 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +10 | LONDON | mt_rf | - | 0.533 [-,-] | - | 0.532 | 0.656 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +15 | NY | cs_pair | - | 0.533 [-,-] | - | 0.483 | 0.566 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | pre | ASIA | prod_ll | - | 0.533 [-,-] | - | 0.514 | 0.544 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +60 | NY | cs_pair | - | 0.532 [-,-] | - | 0.522 | 0.576 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | ASIA | ctrl_gbt3 | - | 0.532 [-,-] | - | 0.518 | 0.526 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +30 | ASIA | prod_pair | - | 0.531 [-,-] | - | 0.521 | 0.526 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | LONDON | ctrl_logit2 | - | 0.530 [-,-] | - | 0.513 | 0.594 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +5 | LONDON | mt_rf | - | 0.530 [-,-] | - | 0.535 | 0.654 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | ASIA | ctrl_gbt3 | - | 0.529 [-,-] | - | 0.504 | 0.529 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | ASIA | ctrl_logit2 | - | 0.528 [-,-] | - | 0.510 | 0.527 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | ASIA | ctrl_gbt3 | - | 0.528 [-,-] | - | 0.517 | 0.531 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | ASIA | ctrl_logit2 | - | 0.528 [-,-] | - | 0.517 | 0.510 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | ASIA | ctrl_gbt3 | - | 0.528 [-,-] | - | 0.516 | 0.502 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | pre | POOLED | cs_ll | - | 0.528 [-,-] | - | 0.498 | 0.493 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +5 | ASIA | rk_lam | - | 0.528 [-,-] | - | 0.521 | 0.530 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +20 | ASIA | rk_pair | - | 0.527 [-,-] | - | 0.519 | 0.512 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | pre | LONDON | rk_xe | - | 0.527 [-,-] | - | 0.517 | 0.671 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +60 | ASIA | cs_pair | - | 0.526 [-,-] | - | 0.494 | 0.511 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | NY | ctrl_logit2 | - | 0.526 [-,-] | - | 0.524 | 0.661 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +45 | ASIA | cs_ll | - | 0.526 [-,-] | - | 0.502 | 0.503 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | POOLED | ctrl_gbt3 | - | 0.526 [-,-] | - | 0.519 | 0.686 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +15 | ASIA | rk_pair | - | 0.525 [-,-] | - | 0.512 | 0.533 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | ASIA | ctrl_logit2 | - | 0.524 [-,-] | - | 0.515 | 0.527 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | LONDON | ctrl_gbt3 | - | 0.524 [-,-] | - | 0.524 | 0.646 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | POOLED | ctrl_gbt3 | - | 0.524 [-,-] | - | 0.524 | 0.697 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +5 | POOLED | mt_rf | - | 0.522 [-,-] | - | 0.516 | 0.684 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | ASIA | ctrl_logit2 | - | 0.522 [-,-] | - | 0.517 | 0.514 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +20 | NY | prod_ll | - | 0.521 [-,-] | - | 0.540 | 0.856 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | NY | ctrl_gbt3 | - | 0.521 [-,-] | - | 0.583 | 0.773 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | LONDON | ctrl_gbt3 | - | 0.520 [-,-] | - | 0.502 | 0.665 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | pre | POOLED | mt_rf | - | 0.519 [-,-] | - | 0.514 | 0.678 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | ASIA | ctrl_gbt3 | - | 0.519 [-,-] | - | 0.503 | 0.518 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +45 | NY | ctrl_logit2 | - | 0.519 [-,-] | - | 0.521 | 0.675 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | LONDON | ctrl_logit2 | - | 0.518 [-,-] | - | 0.524 | 0.579 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | POOLED | ctrl_gbt3 | - | 0.516 [-,-] | - | 0.502 | 0.698 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +15 | ASIA | cs_pair | - | 0.514 [-,-] | - | 0.499 | 0.502 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +20 | LONDON | rk_xe | - | 0.514 [-,-] | - | 0.512 | 0.670 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | ASIA | ctrl_gbt3 | - | 0.513 [-,-] | - | 0.494 | 0.498 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +5 | NY | rk_lam | - | 0.513 [-,-] | - | 0.534 | 0.697 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | POOLED | ctrl_gbt3 | - | 0.512 [-,-] | - | 0.496 | 0.684 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +20 | ASIA | cs_pair | - | 0.512 [-,-] | - | 0.502 | 0.502 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | LONDON | ctrl_logit2 | - | 0.512 [-,-] | - | 0.510 | 0.591 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +45 | NY | cs_pair | - | 0.511 [-,-] | - | 0.508 | 0.589 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +30 | POOLED | prod_pair | - | 0.511 [-,-] | - | 0.515 | 0.696 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | POOLED | ctrl_logit2 | - | 0.510 [-,-] | - | 0.520 | 0.659 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +20 | POOLED | prod_pair | - | 0.510 [-,-] | - | 0.506 | 0.703 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +10 | ASIA | rk_lam | - | 0.507 [-,-] | - | 0.498 | 0.512 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +15 | LONDON | rk_xe | - | 0.507 [-,-] | - | 0.484 | 0.670 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | LONDON | ctrl_gbt3 | - | 0.506 [-,-] | - | 0.487 | 0.670 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +60 | POOLED | prod_pair | - | 0.506 [-,-] | - | 0.506 | 0.703 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +15 | POOLED | rk_xe | - | 0.506 [-,-] | - | 0.497 | 0.682 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +30 | POOLED | ctrl_logit2 | - | 0.504 [-,-] | - | 0.496 | 0.630 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | LONDON | ctrl_logit2 | - | 0.500 [-,-] | - | 0.504 | 0.574 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +60 | LONDON | cs_pair | - | 0.499 [-,-] | - | 0.501 | 0.512 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | POOLED | ctrl_gbt3 | - | 0.498 [-,-] | - | 0.492 | 0.665 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +10 | ASIA | cs_pair | - | 0.494 [-,-] | - | 0.476 | 0.481 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | POOLED | ctrl_logit2 | - | 0.493 [-,-] | - | 0.492 | 0.621 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +15 | NY | prod_pair | - | 0.491 [-,-] | - | 0.437 | 0.818 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | POOLED | ctrl_logit2 | - | 0.490 [-,-] | - | 0.489 | 0.637 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | POOLED | ctrl_logit2 | - | 0.490 [-,-] | - | 0.481 | 0.631 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | pre | NY | cs_pair | - | 0.490 [-,-] | - | 0.469 | 0.529 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +60 | ASIA | prod_pair | - | 0.486 [-,-] | - | 0.480 | 0.490 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +5 | NY | cs_pair | - | 0.484 [-,-] | - | 0.535 | 0.492 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +5 | POOLED | rk_xe | - | 0.480 [-,-] | - | 0.478 | 0.634 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +15 | LONDON | cs_pair | - | 0.477 [-,-] | - | 0.457 | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | NY | ctrl_gbt3 | - | 0.476 [-,-] | - | 0.472 | 0.801 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | POOLED | ctrl_gbt3 | - | 0.474 [-,-] | - | 0.468 | 0.648 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +45 | POOLED | prod_ll | - | 0.474 [-,-] | - | 0.476 | 0.672 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +10 | POOLED | prod_ll | - | 0.474 [-,-] | - | 0.480 | 0.668 | N | - | - | - | - |  | locked label (reference only) |
| X3-multitask | pre | NY | mt_rf | - | 0.474 [-,-] | - | 0.533 | 0.781 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | pre | POOLED | rk_xe | - | 0.473 [-,-] | - | 0.474 | 0.648 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +20 | NY | ctrl_logit2 | - | 0.473 [-,-] | - | 0.465 | 0.662 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +15 | NY | ctrl_logit2 | - | 0.473 [-,-] | - | 0.476 | 0.665 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +60 | LONDON | prod_pair | - | 0.471 [-,-] | - | 0.479 | 0.665 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | POOLED | ctrl_logit2 | - | 0.471 [-,-] | - | 0.472 | 0.615 | ok | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | pre | LONDON | cs_pair | - | 0.468 [-,-] | - | 0.446 | 0.495 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +20 | NY | cs_pair | - | 0.467 [-,-] | - | 0.457 | 0.533 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | LONDON | ctrl_gbt3 | - | 0.461 [-,-] | - | 0.453 | 0.621 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +10 | NY | mt_gbt3 | - | 0.459 [-,-] | - | 0.537 | 0.796 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +45 | ASIA | prod_ll | - | 0.457 [-,-] | - | 0.454 | 0.463 | N | - | - | - | - |  | locked label (reference only) |
| X1-cond-ranker | +10 | NY | cs_ll | - | 0.455 [-,-] | - | 0.473 | 0.524 | N | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +30 | LONDON | prod_ll | - | 0.455 [-,-] | - | 0.453 | 0.655 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +60 | LONDON | ctrl_gbt3 | - | 0.452 [-,-] | - | 0.450 | 0.627 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | POOLED | ctrl_logit2 | - | 0.447 [-,-] | - | 0.441 | 0.599 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +10 | NY | prod_ll | - | 0.446 [-,-] | - | 0.512 | 0.796 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +10 | NY | ctrl_logit2 | - | 0.445 [-,-] | - | 0.507 | 0.607 | ok | - | - | - | - |  | locked label (reference only) |
| X3-multitask | +5 | NY | mt_gbt3 | - | 0.441 [-,-] | - | 0.498 | 0.781 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +45 | LONDON | prod_ll | - | 0.440 [-,-] | - | 0.450 | 0.636 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | LONDON | ctrl_logit2 | - | 0.439 [-,-] | - | 0.432 | 0.528 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +5 | LONDON | rk_xe | - | 0.437 [-,-] | - | 0.439 | 0.578 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | NY | ctrl_logit2 | - | 0.437 [-,-] | - | 0.449 | 0.613 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | +10 | LONDON | prod_pair | - | 0.433 [-,-] | - | 0.437 | 0.639 | N | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | +5 | NY | ctrl_logit2 | - | 0.425 [-,-] | - | 0.478 | 0.606 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ctrl | pre | NY | ctrl_gbt3 | - | 0.423 [-,-] | - | 0.487 | 0.699 | ok | - | - | - | - |  | locked label (reference only) |
| X1-ranking-loss | pre | NY | rk_lam | - | 0.366 [-,-] | - | 0.442 | 0.664 | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- X3-multitask 0 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 0 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 0 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 0 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 5 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 5 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 5 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 5 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 10 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 10 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 10 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 10 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 15 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 15 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 15 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 15 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 20 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 20 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 20 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 20 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 30 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 30 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 30 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 30 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 45 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 45 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 45 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 45 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 60 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 60 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 60 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X3-multitask 60 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 0 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 0 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 0 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 0 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 5 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 5 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 5 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 5 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 10 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 10 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 10 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 10 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 15 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 15 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 15 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 15 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 20 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 20 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 20 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 20 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 30 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 30 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 30 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 30 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 45 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 45 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 45 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 45 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 60 POOLED: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 60 ASIA: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 60 LONDON: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-ranking-loss 60 NY: selected by WF-PRE AUC; model-only family on FAILPRED features
- X1-cond-ranker 0 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 0 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 0 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 0 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 5 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 5 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 5 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 5 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 10 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 10 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 10 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 10 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 15 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 15 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 15 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 15 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 20 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 20 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 20 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 20 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 30 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 30 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 30 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 30 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 45 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 45 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 45 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 45 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 60 POOLED: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 60 ASIA: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 60 LONDON: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-cond-ranker 60 NY: selected by WF-PRE cond-entry AUC; cs_* scorer applied to all sessions, unconditional AUC reported honestly; model-only family on FAILPRED features
- X1-ctrl 0 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 0 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 0 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 0 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 5 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 5 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 5 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 5 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 10 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 10 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 10 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 10 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 15 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 15 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 15 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 15 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 20 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 20 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 20 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 20 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 30 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 30 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 30 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 30 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 45 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 45 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 45 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 45 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 60 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 60 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 60 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 60 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 0 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 0 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 0 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 0 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 5 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 5 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 5 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 5 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 10 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 10 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 10 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 10 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 15 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 15 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 15 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 15 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 20 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 20 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 20 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 20 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 30 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 30 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 30 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 30 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 45 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 45 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 45 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 45 NY: control: same pipeline, logloss, single horizon
- X1-ctrl 60 POOLED: control: same pipeline, logloss, single horizon
- X1-ctrl 60 ASIA: control: same pipeline, logloss, single horizon
- X1-ctrl 60 LONDON: control: same pipeline, logloss, single horizon
- X1-ctrl 60 NY: control: same pipeline, logloss, single horizon
