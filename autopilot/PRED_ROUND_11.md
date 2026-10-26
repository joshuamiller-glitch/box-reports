# PRED ROUND 11 - block X3 round 1 - X12-ordinal-loss-tier+X13-two-stage-count

Best HOLDOUT F-R AUC: +15 POOLED 0.546 [-,-] | ASIA 0.552 [-,-] | LONDON 0.546 [-,-] | NY 0.574 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.552 [-,-] | ASIA 0.550 [-,-] | LONDON 0.533 [-,-] | NY 0.580 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 0e9d89da6e6a6d397c1bf251b8b67b72a90a34aa0085779130f59e4bf46ccfb4 ; trials added 600 ; truncation audit {'decisions': 0, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'no new features; FAILPRED features_full audited 0/74810'} ; holdout scored True ; feature store []

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X12-ordinal-loss-tier-control | +30 | NY | BIN | - | 0.580 [-,-] | - | - | 0.877 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | NY | BIN | - | 0.580 [-,-] | - | - | 0.877 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +15 | NY | H_pFpois | - | 0.574 [-,-] | - | - | 0.864 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +15 | NY | BIN | - | 0.566 [-,-] | - | - | 0.865 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | NY | BIN | - | 0.566 [-,-] | - | - | 0.865 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | NY | H_pE | - | 0.562 [-,-] | - | - | 0.884 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +30 | NY | H_pFpois | - | 0.559 [-,-] | - | - | 0.872 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | ASIA | H_Q | - | 0.556 [-,-] | - | - | 0.551 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +5 | ASIA | FH_tail | - | 0.556 [-,-] | - | - | 0.576 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +15 | ASIA | BIN | - | 0.552 [-,-] | - | - | 0.571 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | ASIA | BIN | - | 0.552 [-,-] | - | - | 0.571 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +30 | POOLED | MC_nz | - | 0.552 [-,-] | - | - | 0.739 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | pre | ASIA | MC_nz | - | 0.551 [-,-] | - | - | 0.575 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +30 | ASIA | MC_nz | - | 0.550 [-,-] | - | - | 0.573 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | pre | ASIA | H_pF | - | 0.549 [-,-] | - | - | 0.572 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +15 | LONDON | BIN | - | 0.546 [-,-] | - | - | 0.719 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | LONDON | BIN | - | 0.546 [-,-] | - | - | 0.719 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +15 | POOLED | BIN | - | 0.546 [-,-] | - | - | 0.734 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | POOLED | BIN | - | 0.546 [-,-] | - | - | 0.734 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +15 | ASIA | ER_hub | - | 0.544 [-,-] | - | - | 0.563 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | pre | ASIA | BIN | - | 0.541 [-,-] | - | - | 0.565 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | ASIA | BIN | - | 0.541 [-,-] | - | - | 0.565 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | NY | H_pE | - | 0.541 [-,-] | - | - | 0.865 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | ASIA | H_Q | - | 0.537 [-,-] | - | - | 0.520 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | POOLED | H_Q | - | 0.536 [-,-] | - | - | 0.421 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +5 | NY | H_pFpois | - | 0.535 [-,-] | - | - | 0.836 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | ASIA | H_Q | - | 0.534 [-,-] | - | - | 0.533 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +30 | LONDON | BIN | - | 0.533 [-,-] | - | - | 0.721 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | LONDON | BIN | - | 0.533 [-,-] | - | - | 0.721 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | NY | H_Q | - | 0.532 [-,-] | - | - | 0.357 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +30 | POOLED | BIN | - | 0.532 [-,-] | - | - | 0.732 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | POOLED | BIN | - | 0.532 [-,-] | - | - | 0.732 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | NY | H_Q | - | 0.529 [-,-] | - | - | 0.361 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +30 | NY | MC_nz | - | 0.529 [-,-] | - | - | 0.862 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | POOLED | H_Q | - | 0.527 [-,-] | - | - | 0.423 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +30 | ASIA | H_pF | - | 0.525 [-,-] | - | - | 0.561 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +30 | ASIA | BIN | - | 0.523 [-,-] | - | - | 0.552 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | ASIA | BIN | - | 0.523 [-,-] | - | - | 0.552 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +5 | ASIA | H_pF | - | 0.522 [-,-] | - | - | 0.546 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | POOLED | H_Q | - | 0.522 [-,-] | - | - | 0.418 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | NY | H_Q | - | 0.522 [-,-] | - | - | 0.368 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | ASIA | H_Q | - | 0.519 [-,-] | - | - | 0.501 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | pre | NY | H_pFpois | - | 0.516 [-,-] | - | - | 0.832 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +15 | ASIA | H_pF | - | 0.515 [-,-] | - | - | 0.545 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | LONDON | H_pE | - | 0.513 [-,-] | - | - | 0.731 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | POOLED | H_Q | - | 0.513 [-,-] | - | - | 0.421 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | ASIA | H_pE | - | 0.506 [-,-] | - | - | 0.542 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | LONDON | H_pE | - | 0.505 [-,-] | - | - | 0.709 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +30 | LONDON | FH_exp | - | 0.502 [-,-] | - | - | 0.709 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | NY | H_pE | - | 0.502 [-,-] | - | - | 0.838 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | LONDON | H_pE | - | 0.500 [-,-] | - | - | 0.726 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +30 | POOLED | H_pF | - | 0.497 [-,-] | - | - | 0.725 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | ASIA | H_pE | - | 0.495 [-,-] | - | - | 0.521 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | pre | POOLED | H_pF | - | 0.495 [-,-] | - | - | 0.706 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +15 | POOLED | H_pF | - | 0.495 [-,-] | - | - | 0.715 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | pre | LONDON | BIN | - | 0.495 [-,-] | - | - | 0.703 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | LONDON | BIN | - | 0.495 [-,-] | - | - | 0.703 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | LONDON | H_pE | - | 0.495 [-,-] | - | - | 0.713 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +15 | NY | FH_exp | - | 0.494 [-,-] | - | - | 0.839 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +5 | ASIA | BIN | - | 0.493 [-,-] | - | - | 0.518 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | ASIA | BIN | - | 0.493 [-,-] | - | - | 0.518 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +15 | LONDON | FH_exp | - | 0.493 [-,-] | - | - | 0.700 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | pre | POOLED | BIN | - | 0.489 [-,-] | - | - | 0.699 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | POOLED | BIN | - | 0.489 [-,-] | - | - | 0.699 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +5 | NY | BIN | - | 0.489 [-,-] | - | - | 0.812 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | NY | BIN | - | 0.489 [-,-] | - | - | 0.812 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | NY | H_pE | - | 0.488 [-,-] | - | - | 0.840 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | ASIA | H_pE | - | 0.486 [-,-] | - | - | 0.539 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +5 | POOLED | H_pF | - | 0.486 [-,-] | - | - | 0.707 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | NY | H_Q | - | 0.485 [-,-] | - | - | 0.359 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +5 | NY | FH_exp | - | 0.485 [-,-] | - | - | 0.814 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +5 | LONDON | H_pF | - | 0.481 [-,-] | - | - | 0.718 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | LONDON | H_Q | - | 0.480 [-,-] | - | - | 0.447 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | ASIA | H_pE | - | 0.479 [-,-] | - | - | 0.503 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | LONDON | H_Q | - | 0.477 [-,-] | - | - | 0.468 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | pre | LONDON | H_pF | - | 0.476 [-,-] | - | - | 0.698 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +15 | POOLED | FH_exp | - | 0.471 [-,-] | - | - | 0.703 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | LONDON | H_Q | - | 0.470 [-,-] | - | - | 0.433 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +5 | POOLED | MC_nz | - | 0.470 [-,-] | - | - | 0.690 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +30 | LONDON | H_pF | - | 0.467 [-,-] | - | - | 0.703 | ok | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +5 | POOLED | BIN | - | 0.463 [-,-] | - | - | 0.682 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | POOLED | BIN | - | 0.463 [-,-] | - | - | 0.682 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | pre | NY | BIN | - | 0.461 [-,-] | - | - | 0.808 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | NY | BIN | - | 0.461 [-,-] | - | - | 0.808 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | +5 | LONDON | FH_exp | - | 0.457 [-,-] | - | - | 0.684 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +15 | POOLED | H_pE | - | 0.455 [-,-] | - | - | 0.704 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier-control | +5 | LONDON | BIN | - | 0.454 [-,-] | - | - | 0.674 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | LONDON | BIN | - | 0.454 [-,-] | - | - | 0.674 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | POOLED | H_pE | - | 0.452 [-,-] | - | - | 0.714 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +30 | LONDON | H_Q | - | 0.450 [-,-] | - | - | 0.451 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count | +15 | LONDON | H_pFpois | - | 0.447 [-,-] | - | - | 0.679 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | pre | POOLED | FH_exp | - | 0.444 [-,-] | - | - | 0.682 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | pre | LONDON | FH_exp | - | 0.444 [-,-] | - | - | 0.683 | N | - | - | - | - | stack | locked label (reference only) |
| X12-ordinal-loss-tier | pre | NY | FH_exp | - | 0.441 [-,-] | - | - | 0.804 | N | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | pre | POOLED | H_pE | - | 0.428 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| X13-two-stage-count-control | +5 | POOLED | H_pE | - | 0.421 [-,-] | - | - | 0.680 | N | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- X12-ordinal-loss-tier 0 POOLED: FH_exp (selected); hold 0.682 vs R0 0.648 (+0.034); cond-entry hold 0.444 vs R0 0.490; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 0 ASIA: MC_nz (selected); hold 0.575 vs R0 0.529 (+0.046); cond-entry hold 0.551 vs R0 0.532; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 0 LONDON: FH_exp (selected); hold 0.683 vs R0 0.658 (+0.025); cond-entry hold 0.444 vs R0 0.522; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 0 NY: FH_exp (selected); hold 0.804 vs R0 0.669 (+0.135); cond-entry hold 0.441 vs R0 0.448; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 0 POOLED: BIN (control); hold 0.699 vs R0 0.648 (+0.052); cond-entry hold 0.489 vs R0 0.490; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 0 ASIA: BIN (control); hold 0.565 vs R0 0.529 (+0.035); cond-entry hold 0.541 vs R0 0.532; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 0 LONDON: BIN (control); hold 0.703 vs R0 0.658 (+0.044); cond-entry hold 0.495 vs R0 0.522; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 0 NY: BIN (control); hold 0.808 vs R0 0.669 (+0.139); cond-entry hold 0.461 vs R0 0.448; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 5 POOLED: MC_nz (selected); hold 0.690 vs R0 0.632 (+0.059); cond-entry hold 0.470 vs R0 0.460; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 5 ASIA: FH_tail (selected); hold 0.576 vs R0 0.528 (+0.048); cond-entry hold 0.556 vs R0 0.532; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 5 LONDON: FH_exp (selected); hold 0.684 vs R0 0.595 (+0.089); cond-entry hold 0.457 vs R0 0.438; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 5 NY: FH_exp (selected); hold 0.814 vs R0 0.692 (+0.121); cond-entry hold 0.485 vs R0 0.500; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 5 POOLED: BIN (control); hold 0.682 vs R0 0.632 (+0.051); cond-entry hold 0.463 vs R0 0.460; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 5 ASIA: BIN (control); hold 0.518 vs R0 0.528 (-0.010); cond-entry hold 0.493 vs R0 0.532; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 5 LONDON: BIN (control); hold 0.674 vs R0 0.595 (+0.079); cond-entry hold 0.454 vs R0 0.438; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 5 NY: BIN (control); hold 0.812 vs R0 0.692 (+0.120); cond-entry hold 0.489 vs R0 0.500; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 15 POOLED: FH_exp (selected); hold 0.703 vs R0 0.703 (-0.000); cond-entry hold 0.471 vs R0 0.529; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 15 ASIA: ER_hub (selected); hold 0.563 vs R0 0.570 (-0.007); cond-entry hold 0.544 vs R0 0.559; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 15 LONDON: FH_exp (selected); hold 0.700 vs R0 0.668 (+0.032); cond-entry hold 0.493 vs R0 0.486; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 15 NY: FH_exp (selected); hold 0.839 vs R0 0.802 (+0.037); cond-entry hold 0.494 vs R0 0.520; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 15 POOLED: BIN (control); hold 0.734 vs R0 0.703 (+0.031); cond-entry hold 0.546 vs R0 0.529; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 15 ASIA: BIN (control); hold 0.571 vs R0 0.570 (+0.001); cond-entry hold 0.552 vs R0 0.559; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 15 LONDON: BIN (control); hold 0.719 vs R0 0.668 (+0.051); cond-entry hold 0.546 vs R0 0.486; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 15 NY: BIN (control); hold 0.865 vs R0 0.802 (+0.063); cond-entry hold 0.566 vs R0 0.520; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 30 POOLED: MC_nz (selected); hold 0.739 vs R0 0.687 (+0.053); cond-entry hold 0.552 vs R0 0.541; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 30 ASIA: MC_nz (selected); hold 0.573 vs R0 0.514 (+0.059); cond-entry hold 0.550 vs R0 0.528; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 30 LONDON: FH_exp (selected); hold 0.709 vs R0 0.661 (+0.048); cond-entry hold 0.502 vs R0 0.546; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier 30 NY: MC_nz (selected); hold 0.862 vs R0 0.804 (+0.058); cond-entry hold 0.529 vs R0 0.571; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 30 POOLED: BIN (control); hold 0.732 vs R0 0.687 (+0.045); cond-entry hold 0.532 vs R0 0.541; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 30 ASIA: BIN (control); hold 0.552 vs R0 0.514 (+0.038); cond-entry hold 0.523 vs R0 0.528; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 30 LONDON: BIN (control); hold 0.721 vs R0 0.661 (+0.060); cond-entry hold 0.533 vs R0 0.546; activity-driven, no cond-entry signal
- X12-ordinal-loss-tier-control 30 NY: BIN (control); hold 0.877 vs R0 0.804 (+0.073); cond-entry hold 0.580 vs R0 0.571; activity-driven, no cond-entry signal
- X13-two-stage-count 0 POOLED: H_pF (selected); hold 0.706 vs R0 0.648 (+0.058); cond-entry hold 0.495 vs R0 0.490; activity-driven, no cond-entry signal
- X13-two-stage-count 0 ASIA: H_pF (selected); hold 0.572 vs R0 0.529 (+0.043); cond-entry hold 0.549 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count 0 LONDON: H_pF (selected); hold 0.698 vs R0 0.658 (+0.040); cond-entry hold 0.476 vs R0 0.522; activity-driven, no cond-entry signal
- X13-two-stage-count 0 NY: H_pFpois (selected); hold 0.832 vs R0 0.669 (+0.163); cond-entry hold 0.516 vs R0 0.448; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 POOLED: H_Q (control); hold 0.421 vs R0 0.648 (-0.227); cond-entry hold 0.536 vs R0 0.490; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 ASIA: H_Q (control); hold 0.551 vs R0 0.529 (+0.022); cond-entry hold 0.556 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 LONDON: H_Q (control); hold 0.433 vs R0 0.658 (-0.225); cond-entry hold 0.470 vs R0 0.522; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 NY: H_Q (control); hold 0.357 vs R0 0.669 (-0.312); cond-entry hold 0.532 vs R0 0.448; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 POOLED: H_pE (control); hold 0.681 vs R0 0.648 (+0.033); cond-entry hold 0.428 vs R0 0.490; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 ASIA: H_pE (control); hold 0.521 vs R0 0.529 (-0.008); cond-entry hold 0.495 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 LONDON: H_pE (control); hold 0.713 vs R0 0.658 (+0.055); cond-entry hold 0.495 vs R0 0.522; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 NY: H_pE (control); hold 0.840 vs R0 0.669 (+0.171); cond-entry hold 0.488 vs R0 0.448; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 POOLED: BIN (control); hold 0.699 vs R0 0.648 (+0.052); cond-entry hold 0.489 vs R0 0.490; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 ASIA: BIN (control); hold 0.565 vs R0 0.529 (+0.035); cond-entry hold 0.541 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 LONDON: BIN (control); hold 0.703 vs R0 0.658 (+0.044); cond-entry hold 0.495 vs R0 0.522; activity-driven, no cond-entry signal
- X13-two-stage-count-control 0 NY: BIN (control); hold 0.808 vs R0 0.669 (+0.139); cond-entry hold 0.461 vs R0 0.448; activity-driven, no cond-entry signal
- X13-two-stage-count 5 POOLED: H_pF (selected); hold 0.707 vs R0 0.632 (+0.076); cond-entry hold 0.486 vs R0 0.460; activity-driven, no cond-entry signal
- X13-two-stage-count 5 ASIA: H_pF (selected); hold 0.546 vs R0 0.528 (+0.018); cond-entry hold 0.522 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count 5 LONDON: H_pF (selected); hold 0.718 vs R0 0.595 (+0.123); cond-entry hold 0.481 vs R0 0.438; activity-driven, no cond-entry signal
- X13-two-stage-count 5 NY: H_pFpois (selected); hold 0.836 vs R0 0.692 (+0.144); cond-entry hold 0.535 vs R0 0.500; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 POOLED: H_Q (control); hold 0.423 vs R0 0.632 (-0.208); cond-entry hold 0.527 vs R0 0.460; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 ASIA: H_Q (control); hold 0.533 vs R0 0.528 (+0.005); cond-entry hold 0.534 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 LONDON: H_Q (control); hold 0.447 vs R0 0.595 (-0.149); cond-entry hold 0.480 vs R0 0.438; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 NY: H_Q (control); hold 0.368 vs R0 0.692 (-0.325); cond-entry hold 0.522 vs R0 0.500; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 POOLED: H_pE (control); hold 0.680 vs R0 0.632 (+0.049); cond-entry hold 0.421 vs R0 0.460; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 ASIA: H_pE (control); hold 0.503 vs R0 0.528 (-0.025); cond-entry hold 0.479 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 LONDON: H_pE (control); hold 0.726 vs R0 0.595 (+0.131); cond-entry hold 0.500 vs R0 0.438; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 NY: H_pE (control); hold 0.838 vs R0 0.692 (+0.146); cond-entry hold 0.502 vs R0 0.500; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 POOLED: BIN (control); hold 0.682 vs R0 0.632 (+0.051); cond-entry hold 0.463 vs R0 0.460; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 ASIA: BIN (control); hold 0.518 vs R0 0.528 (-0.010); cond-entry hold 0.493 vs R0 0.532; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 LONDON: BIN (control); hold 0.674 vs R0 0.595 (+0.079); cond-entry hold 0.454 vs R0 0.438; activity-driven, no cond-entry signal
- X13-two-stage-count-control 5 NY: BIN (control); hold 0.812 vs R0 0.692 (+0.120); cond-entry hold 0.489 vs R0 0.500; activity-driven, no cond-entry signal
- X13-two-stage-count 15 POOLED: H_pF (selected); hold 0.715 vs R0 0.703 (+0.012); cond-entry hold 0.495 vs R0 0.529; activity-driven, no cond-entry signal
- X13-two-stage-count 15 ASIA: H_pF (selected); hold 0.545 vs R0 0.570 (-0.025); cond-entry hold 0.515 vs R0 0.559; activity-driven, no cond-entry signal
- X13-two-stage-count 15 LONDON: H_pFpois (selected); hold 0.679 vs R0 0.668 (+0.011); cond-entry hold 0.447 vs R0 0.486; activity-driven, no cond-entry signal
- X13-two-stage-count 15 NY: H_pFpois (selected); hold 0.864 vs R0 0.802 (+0.062); cond-entry hold 0.574 vs R0 0.520; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 POOLED: H_Q (control); hold 0.418 vs R0 0.703 (-0.284); cond-entry hold 0.522 vs R0 0.529; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 ASIA: H_Q (control); hold 0.501 vs R0 0.570 (-0.069); cond-entry hold 0.519 vs R0 0.559; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 LONDON: H_Q (control); hold 0.468 vs R0 0.668 (-0.200); cond-entry hold 0.477 vs R0 0.486; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 NY: H_Q (control); hold 0.361 vs R0 0.802 (-0.442); cond-entry hold 0.529 vs R0 0.520; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 POOLED: H_pE (control); hold 0.704 vs R0 0.703 (+0.001); cond-entry hold 0.455 vs R0 0.529; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 ASIA: H_pE (control); hold 0.542 vs R0 0.570 (-0.028); cond-entry hold 0.506 vs R0 0.559; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 LONDON: H_pE (control); hold 0.709 vs R0 0.668 (+0.041); cond-entry hold 0.505 vs R0 0.486; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 NY: H_pE (control); hold 0.865 vs R0 0.802 (+0.062); cond-entry hold 0.541 vs R0 0.520; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 POOLED: BIN (control); hold 0.734 vs R0 0.703 (+0.031); cond-entry hold 0.546 vs R0 0.529; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 ASIA: BIN (control); hold 0.571 vs R0 0.570 (+0.001); cond-entry hold 0.552 vs R0 0.559; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 LONDON: BIN (control); hold 0.719 vs R0 0.668 (+0.051); cond-entry hold 0.546 vs R0 0.486; activity-driven, no cond-entry signal
- X13-two-stage-count-control 15 NY: BIN (control); hold 0.865 vs R0 0.802 (+0.063); cond-entry hold 0.566 vs R0 0.520; activity-driven, no cond-entry signal
- X13-two-stage-count 30 POOLED: H_pF (selected); hold 0.725 vs R0 0.687 (+0.038); cond-entry hold 0.497 vs R0 0.541; activity-driven, no cond-entry signal
- X13-two-stage-count 30 ASIA: H_pF (selected); hold 0.561 vs R0 0.514 (+0.047); cond-entry hold 0.525 vs R0 0.528; activity-driven, no cond-entry signal
- X13-two-stage-count 30 LONDON: H_pF (selected); hold 0.703 vs R0 0.661 (+0.042); cond-entry hold 0.467 vs R0 0.546; activity-driven, no cond-entry signal
- X13-two-stage-count 30 NY: H_pFpois (selected); hold 0.872 vs R0 0.804 (+0.068); cond-entry hold 0.559 vs R0 0.571; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 POOLED: H_Q (control); hold 0.421 vs R0 0.687 (-0.266); cond-entry hold 0.513 vs R0 0.541; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 ASIA: H_Q (control); hold 0.520 vs R0 0.514 (+0.006); cond-entry hold 0.537 vs R0 0.528; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 LONDON: H_Q (control); hold 0.451 vs R0 0.661 (-0.210); cond-entry hold 0.450 vs R0 0.546; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 NY: H_Q (control); hold 0.359 vs R0 0.804 (-0.445); cond-entry hold 0.485 vs R0 0.571; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 POOLED: H_pE (control); hold 0.714 vs R0 0.687 (+0.027); cond-entry hold 0.452 vs R0 0.541; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 ASIA: H_pE (control); hold 0.539 vs R0 0.514 (+0.025); cond-entry hold 0.486 vs R0 0.528; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 LONDON: H_pE (control); hold 0.731 vs R0 0.661 (+0.070); cond-entry hold 0.513 vs R0 0.546; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 NY: H_pE (control); hold 0.884 vs R0 0.804 (+0.080); cond-entry hold 0.562 vs R0 0.571; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 POOLED: BIN (control); hold 0.732 vs R0 0.687 (+0.045); cond-entry hold 0.532 vs R0 0.541; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 ASIA: BIN (control); hold 0.552 vs R0 0.514 (+0.038); cond-entry hold 0.523 vs R0 0.528; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 LONDON: BIN (control); hold 0.721 vs R0 0.661 (+0.060); cond-entry hold 0.533 vs R0 0.546; activity-driven, no cond-entry signal
- X13-two-stage-count-control 30 NY: BIN (control); hold 0.877 vs R0 0.804 (+0.073); cond-entry hold 0.580 vs R0 0.571; activity-driven, no cond-entry signal
