# PRED ROUND 5 - block F round 1 - F-auction (F1 volume profile, F2 TPO, F3 composites, F4 delta/absorption)

Best HOLDOUT F-R AUC: +15 POOLED 0.529 [-,-] | ASIA 0.563 [-,-] | LONDON 0.541 [-,-] | NY 0.565 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.512 [-,-] | ASIA 0.569 [-,-] | LONDON 0.523 [-,-] | NY 0.550 [-,-]
Best G HOLDOUT AUC: 0.607 [0.56,0.65]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg b226916074c81cb5b813a6a0efe53a6b991761404851e55f35e80a707d4cdcba ; trials added 2600 ; truncation audit {'decisions': 360, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/F_auction.parquet', 'l2vast/pred/store/F_auction_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1234-auction+base | +45 | NY | gbt3 | - | 0.612 [-,-] | - | - | 0.752 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +60 | NY | logit2 | - | 0.610 [-,-] | - | - | 0.703 | N | - | - | - | - |  | locked label (reference only) |
| G-F+base | sig | LONDON | logit2 | 0.628 [0.60,0.66] | 0.607 [0.56,0.65] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | LONDON | logit2 | 0.628 [0.59,0.66] | 0.606 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | NY | logit2 | 0.611 [0.58,0.64] | 0.604 [0.56,0.65] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | ASIA | stack | 0.581 [0.55,0.61] | 0.599 [0.56,0.63] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +60 | NY | logit2 | - | 0.598 [-,-] | - | - | 0.718 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | POOLED/ST | logit2 | 0.592 [0.57,0.61] | 0.593 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | POOLED | rf | 0.589 [0.57,0.61] | 0.590 [0.57,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | POOLED/HM | rf | 0.588 [0.57,0.61] | 0.587 [0.56,0.62] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | logit2 | 0.582 [0.56,0.60] | 0.583 [0.55,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F+base | sig | NY | stack | 0.604 [0.56,0.64] | 0.583 [0.53,0.63] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| G-F-auction | sig | POOLED/HM | rf | 0.570 [0.54,0.59] | 0.582 [0.55,0.62] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +45 | NY | gbt3 | - | 0.579 [-,-] | - | - | 0.695 | N | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | POOLED | rf | 0.568 [0.55,0.59] | 0.578 [0.55,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED | logit2 | 0.578 [0.56,0.59] | 0.574 [0.55,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | POOLED/ST | rf | 0.565 [0.54,0.59] | 0.573 [0.55,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F+base | sig | ASIA | gbt3 | 0.564 [0.54,0.59] | 0.572 [0.54,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +60 | LONDON | logit2 | - | 0.570 [-,-] | - | - | 0.604 | N | - | - | - | - |  | locked label (reference only) |
| F1-volprofile+base | +30 | ASIA | gbt3 | - | 0.569 [-,-] | - | - | 0.551 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +45 | ASIA | gbt3 | - | 0.567 [-,-] | - | - | 0.552 | N | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/HM | logit2 | 0.575 [0.55,0.59] | 0.566 [0.54,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-volprofile+base | +15 | NY | stack | - | 0.565 [-,-] | - | - | 0.791 | - | - | - | - | - | stack | locked label (reference only) |
| G-F-auction | sig | LONDON | logit2 | 0.556 [0.52,0.59] | 0.565 [0.52,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F3-composite+base | +15 | ASIA | stack | - | 0.563 [-,-] | - | - | 0.575 | - | - | - | - | - | stack | locked label (reference only) |
| F3-composite+base | +30 | ASIA | gbt3 | - | 0.560 [-,-] | - | - | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | ASIA | gbt3 | 0.543 [0.52,0.57] | 0.559 [0.52,0.60] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +60 | POOLED | logit2 | - | 0.557 [-,-] | - | - | 0.661 | N | - | - | - | - |  | locked label (reference only) |
| F1-volprofile+base | +15 | ASIA | stack | - | 0.556 [-,-] | - | - | 0.562 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +60 | ASIA | logit2 | - | 0.552 [-,-] | - | - | 0.532 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +45 | POOLED | logit2 | - | 0.550 [-,-] | - | - | 0.666 | ok | - | - | - | - | stack | locked label (reference only) |
| F2-tpo+base | +30 | NY | logit2 | - | 0.550 [-,-] | - | - | 0.680 | ok | - | - | - | - | stack | locked label (reference only) |
| F4-delta+base | +30 | ASIA | gbt3 | - | 0.546 [-,-] | - | - | 0.530 | ok | - | - | - | - | stack | locked label (reference only) |
| F2-tpo+base | +30 | ASIA | gbt3 | - | 0.546 [-,-] | - | - | 0.526 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-volprofile+base | +30 | NY | logit2 | - | 0.543 [-,-] | - | - | 0.697 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +30 | NY | rf | - | 0.543 [-,-] | - | - | 0.677 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | pre | ASIA | stack | - | 0.542 [-,-] | - | - | 0.538 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +30 | ASIA | logit2 | - | 0.542 [-,-] | - | - | 0.516 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-volprofile+base | +15 | LONDON | gbt3 | - | 0.541 [-,-] | - | - | 0.688 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +30 | ASIA | gbt3 | - | 0.541 [-,-] | - | - | 0.557 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +10 | ASIA | gbt3 | - | 0.540 [-,-] | - | - | 0.533 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +30 | NY | rf | - | 0.539 [-,-] | - | - | 0.785 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +15 | NY | stack | - | 0.535 [-,-] | - | - | 0.673 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +30 | ASIA | logit2 | - | 0.533 [-,-] | - | - | 0.516 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +45 | LONDON | stack | - | 0.532 [-,-] | - | - | 0.611 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +15 | LONDON | gbt3 | - | 0.532 [-,-] | - | - | 0.593 | - | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | LONDON | logit2 | 0.530 [0.49,0.56] | 0.532 [0.48,0.58] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F2-tpo+base | +15 | ASIA | stack | - | 0.531 [-,-] | - | - | 0.526 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | pre | LONDON | gbt3 | - | 0.530 [-,-] | - | - | 0.667 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +15 | ASIA | rf | - | 0.529 [-,-] | - | - | 0.515 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-volprofile+base | +15 | POOLED | rf | - | 0.529 [-,-] | - | - | 0.687 | ok | - | - | - | - | stack | locked label (reference only) |
| F3-composite+base | +15 | POOLED | rf | - | 0.528 [-,-] | - | - | 0.698 | ok | - | - | - | - | stack | locked label (reference only) |
| F2-tpo+base | +15 | POOLED | rf | - | 0.527 [-,-] | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +60 | LONDON | logit2 | - | 0.527 [-,-] | - | - | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | ASIA | stack | 0.503 [0.48,0.53] | 0.526 [0.48,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | POOLED/HM | rf | 0.532 [0.51,0.56] | 0.525 [0.49,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F2-tpo+base | +15 | NY | stack | - | 0.524 [-,-] | - | - | 0.768 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +20 | LONDON | logit2 | - | 0.523 [-,-] | - | - | 0.581 | N | - | - | - | - |  | locked label (reference only) |
| F3-composite+base | +30 | LONDON | logit2 | - | 0.523 [-,-] | - | - | 0.588 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | NY | rf | 0.521 [0.48,0.56] | 0.521 [0.46,0.59] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | POOLED | rf | 0.528 [0.51,0.55] | 0.521 [0.50,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +5 | ASIA | rf | - | 0.520 [-,-] | - | - | 0.512 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +60 | ASIA | logit2 | - | 0.520 [-,-] | - | - | 0.516 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | pre | NY | stack | - | 0.520 [-,-] | - | - | 0.598 | - | - | - | - | - |  | locked label (reference only) |
| F4-delta+base | +15 | POOLED | rf | - | 0.520 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/ST | logit2 | 0.504 [0.48,0.53] | 0.519 [0.48,0.56] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +5 | LONDON | gbt3 | - | 0.519 [-,-] | - | - | 0.600 | N | - | - | - | - |  | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED | rf | 0.509 [0.49,0.53] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1-volprofile+base | +30 | LONDON | logit2 | - | 0.518 [-,-] | - | - | 0.579 | ok | - | - | - | - | stack | locked label (reference only) |
| G-base(FAILPRED-asof) | sig | POOLED/HM | rf | 0.520 [0.50,0.54] | 0.518 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +20 | NY | logit2 | - | 0.518 [-,-] | - | - | 0.663 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +10 | LONDON | logit2 | - | 0.518 [-,-] | - | - | 0.566 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +10 | ASIA | gbt3 | - | 0.518 [-,-] | - | - | 0.525 | N | - | - | - | - |  | locked label (reference only) |
| F4-delta+base | +30 | LONDON | logit2 | - | 0.518 [-,-] | - | - | 0.580 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +45 | POOLED | logit2 | - | 0.518 [-,-] | - | - | 0.636 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +5 | ASIA | rf | - | 0.517 [-,-] | - | - | 0.513 | N | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | POOLED/ST | rf | 0.525 [0.50,0.55] | 0.517 [0.49,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | NY | rf | 0.550 [0.51,0.58] | 0.516 [0.46,0.57] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F4-delta+base | +15 | ASIA | stack | - | 0.516 [-,-] | - | - | 0.527 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +45 | ASIA | gbt3 | - | 0.516 [-,-] | - | - | 0.495 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | ASIA | gbt3 | 0.511 [0.48,0.54] | 0.514 [0.47,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +10 | NY | logit2 | - | 0.513 [-,-] | - | - | 0.631 | N | - | - | - | - |  | locked label (reference only) |
| G-F-auction | sig | ASIA | stack | 0.530 [0.50,0.56] | 0.513 [0.47,0.55] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F2-tpo+base | +30 | LONDON | logit2 | - | 0.513 [-,-] | - | - | 0.578 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +15 | NY | logit2 | - | 0.513 [-,-] | - | - | 0.641 | N | - | - | - | - |  | locked label (reference only) |
| F4-delta+base | +15 | NY | stack | - | 0.513 [-,-] | - | - | 0.790 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +30 | POOLED | logit2 | - | 0.512 [-,-] | - | - | 0.638 | N | - | - | - | - |  | locked label (reference only) |
| G-F+base | sig | POOLED/HM | rf | 0.529 [0.51,0.55] | 0.512 [0.48,0.54] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +20 | LONDON | logit2 | - | 0.511 [-,-] | - | - | 0.603 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +20 | ASIA | gbt3 | - | 0.510 [-,-] | - | - | 0.498 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +60 | POOLED | logit2 | - | 0.508 [-,-] | - | - | 0.655 | ok | - | - | - | - | stack | locked label (reference only) |
| F4-delta+base | +30 | NY | logit2 | - | 0.507 [-,-] | - | - | 0.687 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | LONDON | logit2 | 0.537 [0.50,0.57] | 0.507 [0.46,0.56] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +15 | LONDON | gbt3 | - | 0.505 [-,-] | - | - | 0.569 | N | - | - | - | - |  | locked label (reference only) |
| F3-composite+base | +15 | NY | stack | - | 0.505 [-,-] | - | - | 0.801 | - | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | POOLED | rf | 0.518 [0.50,0.54] | 0.503 [0.48,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F4-delta+base | +15 | LONDON | gbt3 | - | 0.503 [-,-] | - | - | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +30 | LONDON | logit2 | - | 0.502 [-,-] | - | - | 0.567 | - | - | - | - | - | stack | locked label (reference only) |
| F2-tpo+base | +15 | LONDON | gbt3 | - | 0.502 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +5 | NY | logit2 | - | 0.502 [-,-] | - | - | 0.641 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +30 | POOLED | logit2 | - | 0.501 [-,-] | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| F1-volprofile+base | +30 | POOLED | logit2 | - | 0.500 [-,-] | - | - | 0.637 | ok | - | - | - | - | stack | locked label (reference only) |
| F3-composite+base | +30 | POOLED | logit2 | - | 0.498 [-,-] | - | - | 0.631 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +15 | ASIA | rf | - | 0.498 [-,-] | - | - | 0.487 | N | - | - | - | - |  | locked label (reference only) |
| F2-tpo+base | +30 | POOLED | logit2 | - | 0.497 [-,-] | - | - | 0.623 | ok | - | - | - | - | stack | locked label (reference only) |
| F3-composite+base | +30 | NY | logit2 | - | 0.497 [-,-] | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +15 | ASIA | stack | - | 0.496 [-,-] | - | - | 0.492 | - | - | - | - | - | stack | locked label (reference only) |
| G-F+base | sig | POOLED/ST | rf | 0.507 [0.48,0.53] | 0.496 [0.47,0.53] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F4-delta+base | +30 | POOLED | logit2 | - | 0.495 [-,-] | - | - | 0.631 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +20 | POOLED | logit2 | - | 0.493 [-,-] | - | - | 0.634 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | pre | LONDON | gbt3 | - | 0.493 [-,-] | - | - | 0.562 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +15 | NY | logit2 | - | 0.493 [-,-] | - | - | 0.678 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +20 | ASIA | gbt3 | - | 0.493 [-,-] | - | - | 0.494 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +45 | LONDON | stack | - | 0.492 [-,-] | - | - | 0.556 | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +15 | POOLED | logit2 | - | 0.491 [-,-] | - | - | 0.641 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +20 | POOLED | logit2 | - | 0.490 [-,-] | - | - | 0.626 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | pre | ASIA | stack | - | 0.489 [-,-] | - | - | 0.503 | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +15 | POOLED | logit2 | - | 0.489 [-,-] | - | - | 0.617 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | pre | POOLED | rf | - | 0.487 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F-auction | sig | NY | rf | 0.512 [0.47,0.55] | 0.486 [0.42,0.54] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +30 | LONDON | gbt3 | - | 0.484 [-,-] | - | - | 0.630 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +30 | LONDON | gbt3 | - | 0.483 [-,-] | - | - | 0.571 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +20 | NY | logit2 | - | 0.483 [-,-] | - | - | 0.668 | ok | - | - | - | - | stack | locked label (reference only) |
| G-F-auction | sig | LONDON | gbt3 | 0.508 [0.47,0.54] | 0.477 [0.43,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| F3-composite+base | +15 | LONDON | gbt3 | - | 0.475 [-,-] | - | - | 0.651 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +10 | POOLED | logit2 | - | 0.475 [-,-] | - | - | 0.616 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | pre | POOLED | rf | - | 0.474 [-,-] | - | - | 0.603 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +5 | NY | logit2 | - | 0.472 [-,-] | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +10 | POOLED | logit2 | - | 0.465 [-,-] | - | - | 0.605 | N | - | - | - | - |  | locked label (reference only) |
| G-F+base | sig | NY | rf | 0.510 [0.47,0.55] | 0.462 [0.40,0.52] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction-only | +10 | LONDON | logit2 | - | 0.461 [-,-] | - | - | 0.537 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction-only | +5 | POOLED | logit2 | - | 0.461 [-,-] | - | - | 0.612 | N | - | - | - | - |  | locked label (reference only) |
| F1234-auction+base | +10 | NY | logit2 | - | 0.461 [-,-] | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +15 | LONDON | gbt3 | - | 0.457 [-,-] | - | - | 0.624 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +5 | POOLED | logit2 | - | 0.453 [-,-] | - | - | 0.616 | ok | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | pre | NY | stack | - | 0.451 [-,-] | - | - | 0.687 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base-pertype | +30 | NY | logit2 | - | 0.447 [-,-] | - | - | 0.735 | - | - | - | - | - | stack | locked label (reference only) |
| F1234-auction+base | +5 | LONDON | gbt3 | - | 0.444 [-,-] | - | - | 0.596 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- F1234-auction-only 0 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 0 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 0 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 0 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 0 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 0 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 0 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 0 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 5 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 5 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 5 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 5 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 5 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 5 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 5 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 5 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 10 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 10 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 10 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 10 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 10 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 10 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 10 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 10 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base-pertype 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1-volprofile+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F2-tpo+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F3-composite+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F4-delta+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 15 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 15 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 15 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 15 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 20 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 20 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 20 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 20 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 20 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 20 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 20 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 20 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 30 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 30 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 30 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 30 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 45 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 45 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 45 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 45 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 45 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 45 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 45 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 45 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 60 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 60 POOLED: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 60 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 60 ASIA: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 60 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 60 LONDON: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction-only 60 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- F1234-auction+base 60 NY: F-R with auction features; econ/CPCV not run (no pre-holdout gain over R0 baseline)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-base(FAILPRED-asof) -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F-auction -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 ASIA: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 LONDON: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 NY: G gate features; no gate economics run (AUC far below 0.68)
- G-F+base -1 POOLED: G gate features; no gate economics run (AUC far below 0.68)
