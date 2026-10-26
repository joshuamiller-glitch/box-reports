# PRED ROUND 4 - block A round 3 - A4-validation

Best HOLDOUT F-R AUC: +15 POOLED 0.547 [-,-] | ASIA 0.520 [-,-] | LONDON 0.546 [-,-] | NY 0.553 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.533 [-,-] | ASIA 0.518 [-,-] | LONDON 0.541 [-,-] | NY 0.534 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 570a6c19a82e77b765974039a4b3f1f1300be82b44725ff5023915482619b131 ; trials added 450 ; truncation audit {'decisions': 74810, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A/r3_preds.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4-ctrl-C4 | +15 | NY | C4 | - | 0.553 [-,-] | - | - | 0.874 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +15 | POOLED | C4 | - | 0.547 [-,-] | - | - | 0.736 | N | 1055 | 45341 | - | 1/5 |  | locked label (reference only) |
| A4-ctrl-C4 | +15 | LONDON | C4 | - | 0.546 [-,-] | - | - | 0.730 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | pre | ASIA | C4 | - | 0.542 [-,-] | - | - | 0.567 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +30 | LONDON | C4 | - | 0.541 [-,-] | - | - | 0.747 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +20 | NY | C4 | - | 0.540 [-,-] | - | - | 0.880 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +20 | POOLED | C4 | - | 0.539 [-,-] | - | - | 0.741 | N | 9118 | 31255 | - | 1/5 |  | locked label (reference only) |
| A4-ctrl-C4 | +30 | NY | C4 | - | 0.534 [-,-] | - | - | 0.875 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +10 | NY | C4 | - | 0.533 [-,-] | - | - | 0.859 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +20 | NY | pE | - | 0.533 [-,-] | - | - | 0.883 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +30 | POOLED | C4 | - | 0.533 [-,-] | - | - | 0.740 | N | 3815 | -9515 | - | 2/5 |  | locked label (reference only) |
| A4-ctrl-C4 | +10 | POOLED | C4 | - | 0.532 [-,-] | - | - | 0.727 | N | 3906 | 42575 | - | 1/5 |  | locked label (reference only) |
| A4-ctrl-C4 | +5 | ASIA | C4 | - | 0.532 [-,-] | - | - | 0.555 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +20 | ASIA | C4 | - | 0.527 [-,-] | - | - | 0.554 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +20 | LONDON | C4 | - | 0.523 [-,-] | - | - | 0.730 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +15 | ASIA | C4 | - | 0.520 [-,-] | - | - | 0.544 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +30 | ASIA | C4 | - | 0.518 [-,-] | - | - | 0.546 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +5 | NY | C4 | - | 0.517 [-,-] | - | - | 0.840 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +10 | ASIA | C4 | - | 0.515 [-,-] | - | - | 0.540 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +10 | LONDON | C4 | - | 0.513 [-,-] | - | - | 0.722 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +5 | POOLED | C4 | - | 0.509 [-,-] | - | - | 0.711 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +20 | NY | lamS | - | 0.506 [-,-] | - | - | 0.848 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +15 | ASIA | pE | - | 0.505 [-,-] | - | - | 0.537 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | pre | POOLED | C4 | - | 0.505 [-,-] | - | - | 0.710 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +30 | NY | pE | - | 0.503 [-,-] | - | - | 0.873 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +15 | NY | pE | - | 0.501 [-,-] | - | - | 0.871 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +10 | NY | lamS | - | 0.498 [-,-] | - | - | 0.826 | ok | 729 | 15872 | - | 1/5 |  | locked label (reference only) |
| A4-ctrl-pEntry | +30 | ASIA | pE | - | 0.497 [-,-] | - | - | 0.543 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +20 | ASIA | pE | - | 0.496 [-,-] | - | - | 0.528 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | pre | NY | C4 | - | 0.495 [-,-] | - | - | 0.836 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +20 | NY | lamE | - | 0.494 [-,-] | - | - | 0.871 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +5 | ASIA | pE | - | 0.493 [-,-] | - | - | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +5 | NY | lamS | - | 0.489 [-,-] | - | - | 0.816 | N | 2237 | 0 | - | 2/5 |  | locked label (reference only) |
| A4-ctrl-entrycount | +30 | NY | lamE | - | 0.489 [-,-] | - | - | 0.869 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | pre | NY | lamE | - | 0.489 [-,-] | - | - | 0.844 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +10 | LONDON | pE | - | 0.488 [-,-] | - | - | 0.718 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +20 | ASIA | lamS | - | 0.487 [-,-] | - | - | 0.523 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +30 | NY | lamS | - | 0.487 [-,-] | - | - | 0.836 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | pre | NY | lamS | - | 0.485 [-,-] | - | - | 0.807 | N | 1112 | 66436 | - | 2/5 |  | locked label (reference only) |
| A4-lambda | +15 | ASIA | lamS | - | 0.480 [-,-] | - | - | 0.514 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +15 | LONDON | pE | - | 0.480 [-,-] | - | - | 0.715 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +30 | ASIA | lamS | - | 0.479 [-,-] | - | - | 0.528 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +20 | ASIA | lamE | - | 0.478 [-,-] | - | - | 0.516 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +5 | NY | lamE | - | 0.475 [-,-] | - | - | 0.845 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +10 | ASIA | pE | - | 0.475 [-,-] | - | - | 0.502 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +15 | NY | lamS | - | 0.474 [-,-] | - | - | 0.830 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +5 | NY | pE | - | 0.473 [-,-] | - | - | 0.842 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +15 | ASIA | lamE | - | 0.473 [-,-] | - | - | 0.510 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +10 | NY | pE | - | 0.470 [-,-] | - | - | 0.852 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +10 | NY | lamE | - | 0.469 [-,-] | - | - | 0.847 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +30 | ASIA | lamE | - | 0.468 [-,-] | - | - | 0.520 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | pre | LONDON | C4 | - | 0.465 [-,-] | - | - | 0.699 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +5 | LONDON | pE | - | 0.464 [-,-] | - | - | 0.710 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +30 | LONDON | pE | - | 0.461 [-,-] | - | - | 0.720 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-C4 | +5 | LONDON | C4 | - | 0.461 [-,-] | - | - | 0.693 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +10 | ASIA | lamS | - | 0.460 [-,-] | - | - | 0.495 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | pre | LONDON | pE | - | 0.459 [-,-] | - | - | 0.701 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +10 | ASIA | lamE | - | 0.459 [-,-] | - | - | 0.494 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +5 | ASIA | lamE | - | 0.458 [-,-] | - | - | 0.485 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | pre | ASIA | pE | - | 0.458 [-,-] | - | - | 0.486 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +5 | ASIA | lamS | - | 0.455 [-,-] | - | - | 0.482 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | pre | NY | pE | - | 0.453 [-,-] | - | - | 0.835 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +15 | NY | lamE | - | 0.453 [-,-] | - | - | 0.853 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | pre | ASIA | lamE | - | 0.450 [-,-] | - | - | 0.478 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +20 | LONDON | pE | - | 0.446 [-,-] | - | - | 0.702 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | pre | ASIA | lamS | - | 0.443 [-,-] | - | - | 0.472 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +15 | POOLED | pE | - | 0.437 [-,-] | - | - | 0.701 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +20 | POOLED | lamE | - | 0.437 [-,-] | - | - | 0.696 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +30 | POOLED | pE | - | 0.436 [-,-] | - | - | 0.708 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +15 | POOLED | lamE | - | 0.436 [-,-] | - | - | 0.694 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +20 | POOLED | lamS | - | 0.433 [-,-] | - | - | 0.685 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +20 | POOLED | pE | - | 0.431 [-,-] | - | - | 0.698 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +30 | POOLED | lamE | - | 0.429 [-,-] | - | - | 0.700 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +10 | POOLED | lamE | - | 0.426 [-,-] | - | - | 0.682 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +30 | POOLED | lamS | - | 0.425 [-,-] | - | - | 0.689 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +15 | POOLED | lamS | - | 0.423 [-,-] | - | - | 0.678 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +5 | POOLED | lamE | - | 0.419 [-,-] | - | - | 0.676 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | pre | POOLED | lamE | - | 0.419 [-,-] | - | - | 0.674 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | pre | POOLED | lamS | - | 0.418 [-,-] | - | - | 0.663 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +10 | POOLED | lamS | - | 0.417 [-,-] | - | - | 0.668 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | pre | LONDON | lamS | - | 0.416 [-,-] | - | - | 0.665 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +5 | POOLED | pE | - | 0.414 [-,-] | - | - | 0.679 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | +10 | POOLED | pE | - | 0.412 [-,-] | - | - | 0.680 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | pre | LONDON | lamE | - | 0.410 [-,-] | - | - | 0.678 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +5 | POOLED | lamS | - | 0.407 [-,-] | - | - | 0.659 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-pEntry | pre | POOLED | pE | - | 0.407 [-,-] | - | - | 0.672 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +10 | LONDON | lamS | - | 0.397 [-,-] | - | - | 0.654 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +5 | LONDON | lamE | - | 0.397 [-,-] | - | - | 0.675 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +10 | LONDON | lamE | - | 0.395 [-,-] | - | - | 0.673 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +15 | LONDON | lamE | - | 0.392 [-,-] | - | - | 0.674 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +5 | LONDON | lamS | - | 0.392 [-,-] | - | - | 0.651 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +30 | LONDON | lamS | - | 0.389 [-,-] | - | - | 0.663 | N | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +20 | LONDON | lamS | - | 0.389 [-,-] | - | - | 0.650 | ok | - | - | - | - |  | locked label (reference only) |
| A4-lambda | +15 | LONDON | lamS | - | 0.387 [-,-] | - | - | 0.650 | N | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +20 | LONDON | lamE | - | 0.376 [-,-] | - | - | 0.662 | ok | - | - | - | - |  | locked label (reference only) |
| A4-ctrl-entrycount | +30 | LONDON | lamE | - | 0.373 [-,-] | - | - | 0.675 | ok | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- A4-lambda 0 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.418; econ best pass_count n/a
- A4-lambda 0 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.443; econ best pass_count n/a
- A4-lambda 0 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.416; econ best pass_count n/a
- A4-lambda 0 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.485; econ best pass_count 2
- A4-lambda 5 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.407; econ best pass_count n/a
- A4-lambda 5 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.455; econ best pass_count n/a
- A4-lambda 5 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.392; econ best pass_count n/a
- A4-lambda 5 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.489; econ best pass_count 2
- A4-lambda 10 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.417; econ best pass_count n/a
- A4-lambda 10 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.460; econ best pass_count n/a
- A4-lambda 10 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.397; econ best pass_count n/a
- A4-lambda 10 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.498; econ best pass_count 1
- A4-lambda 15 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.423; econ best pass_count n/a
- A4-lambda 15 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.480; econ best pass_count n/a
- A4-lambda 15 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.387; econ best pass_count n/a
- A4-lambda 15 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.474; econ best pass_count n/a
- A4-lambda 20 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.433; econ best pass_count n/a
- A4-lambda 20 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.487; econ best pass_count n/a
- A4-lambda 20 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.389; econ best pass_count n/a
- A4-lambda 20 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.506; econ best pass_count n/a
- A4-lambda 30 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.425; econ best pass_count n/a
- A4-lambda 30 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.479; econ best pass_count n/a
- A4-lambda 30 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.389; econ best pass_count n/a
- A4-lambda 30 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.487; econ best pass_count n/a
- A4-ctrl-entrycount 0 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.419; econ best pass_count n/a
- A4-ctrl-entrycount 0 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.450; econ best pass_count n/a
- A4-ctrl-entrycount 0 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.410; econ best pass_count n/a
- A4-ctrl-entrycount 0 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.489; econ best pass_count n/a
- A4-ctrl-entrycount 5 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.419; econ best pass_count n/a
- A4-ctrl-entrycount 5 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.458; econ best pass_count n/a
- A4-ctrl-entrycount 5 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.397; econ best pass_count n/a
- A4-ctrl-entrycount 5 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.475; econ best pass_count n/a
- A4-ctrl-entrycount 10 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.426; econ best pass_count n/a
- A4-ctrl-entrycount 10 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.459; econ best pass_count n/a
- A4-ctrl-entrycount 10 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.395; econ best pass_count n/a
- A4-ctrl-entrycount 10 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.469; econ best pass_count n/a
- A4-ctrl-entrycount 15 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.436; econ best pass_count n/a
- A4-ctrl-entrycount 15 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.473; econ best pass_count n/a
- A4-ctrl-entrycount 15 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.392; econ best pass_count n/a
- A4-ctrl-entrycount 15 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.453; econ best pass_count n/a
- A4-ctrl-entrycount 20 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.437; econ best pass_count n/a
- A4-ctrl-entrycount 20 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.478; econ best pass_count n/a
- A4-ctrl-entrycount 20 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.376; econ best pass_count n/a
- A4-ctrl-entrycount 20 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.494; econ best pass_count n/a
- A4-ctrl-entrycount 30 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.429; econ best pass_count n/a
- A4-ctrl-entrycount 30 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.468; econ best pass_count n/a
- A4-ctrl-entrycount 30 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.373; econ best pass_count n/a
- A4-ctrl-entrycount 30 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.489; econ best pass_count n/a
- A4-ctrl-pEntry 0 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.407; econ best pass_count n/a
- A4-ctrl-pEntry 0 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.458; econ best pass_count n/a
- A4-ctrl-pEntry 0 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.459; econ best pass_count n/a
- A4-ctrl-pEntry 0 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.453; econ best pass_count n/a
- A4-ctrl-pEntry 5 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.414; econ best pass_count n/a
- A4-ctrl-pEntry 5 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.493; econ best pass_count n/a
- A4-ctrl-pEntry 5 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.464; econ best pass_count n/a
- A4-ctrl-pEntry 5 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.473; econ best pass_count n/a
- A4-ctrl-pEntry 10 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.412; econ best pass_count n/a
- A4-ctrl-pEntry 10 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.475; econ best pass_count n/a
- A4-ctrl-pEntry 10 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.488; econ best pass_count n/a
- A4-ctrl-pEntry 10 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.470; econ best pass_count n/a
- A4-ctrl-pEntry 15 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.437; econ best pass_count n/a
- A4-ctrl-pEntry 15 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.505; econ best pass_count n/a
- A4-ctrl-pEntry 15 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.480; econ best pass_count n/a
- A4-ctrl-pEntry 15 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.501; econ best pass_count n/a
- A4-ctrl-pEntry 20 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.431; econ best pass_count n/a
- A4-ctrl-pEntry 20 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.496; econ best pass_count n/a
- A4-ctrl-pEntry 20 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.446; econ best pass_count n/a
- A4-ctrl-pEntry 20 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.533; econ best pass_count n/a
- A4-ctrl-pEntry 30 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.436; econ best pass_count n/a
- A4-ctrl-pEntry 30 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.497; econ best pass_count n/a
- A4-ctrl-pEntry 30 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.461; econ best pass_count n/a
- A4-ctrl-pEntry 30 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.503; econ best pass_count n/a
- A4-ctrl-C4 0 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.505; econ best pass_count n/a
- A4-ctrl-C4 0 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.542; econ best pass_count n/a
- A4-ctrl-C4 0 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.465; econ best pass_count n/a
- A4-ctrl-C4 0 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.495; econ best pass_count n/a
- A4-ctrl-C4 5 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.509; econ best pass_count n/a
- A4-ctrl-C4 5 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.532; econ best pass_count n/a
- A4-ctrl-C4 5 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.461; econ best pass_count n/a
- A4-ctrl-C4 5 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.517; econ best pass_count n/a
- A4-ctrl-C4 10 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.532; econ best pass_count 1
- A4-ctrl-C4 10 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.515; econ best pass_count n/a
- A4-ctrl-C4 10 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.513; econ best pass_count n/a
- A4-ctrl-C4 10 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.533; econ best pass_count n/a
- A4-ctrl-C4 15 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.547; econ best pass_count 1
- A4-ctrl-C4 15 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.520; econ best pass_count n/a
- A4-ctrl-C4 15 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.546; econ best pass_count n/a
- A4-ctrl-C4 15 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.553; econ best pass_count n/a
- A4-ctrl-C4 20 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.539; econ best pass_count 1
- A4-ctrl-C4 20 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.527; econ best pass_count n/a
- A4-ctrl-C4 20 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.523; econ best pass_count n/a
- A4-ctrl-C4 20 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.540; econ best pass_count n/a
- A4-ctrl-C4 30 POOLED: activity-driven: AUC on sessions with >=1 entry (hold) 0.533; econ best pass_count 2
- A4-ctrl-C4 30 ASIA: activity-driven: AUC on sessions with >=1 entry (hold) 0.518; econ best pass_count n/a
- A4-ctrl-C4 30 LONDON: activity-driven: AUC on sessions with >=1 entry (hold) 0.541; econ best pass_count n/a
- A4-ctrl-C4 30 NY: activity-driven: AUC on sessions with >=1 entry (hold) 0.534; econ best pass_count n/a
