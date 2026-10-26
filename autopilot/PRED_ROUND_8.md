# PRED ROUND 8 - block A round 5 - C5-entrygated

Best HOLDOUT F-R AUC: +15 POOLED 0.558 [-,-] | ASIA 0.505 [-,-] | LONDON 0.517 [-,-] | NY 0.514 [-,-]
Best HOLDOUT F-R AUC: +30 POOLED 0.521 [-,-] | ASIA 0.510 [-,-] | LONDON 0.502 [-,-] | NY 0.503 [-,-]
Best G HOLDOUT AUC: -
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg ad95c29c5f1a1f4643e03a09bbf2787695740c1f1e3468c401b2116871dcde3b ; trials added 1200 ; truncation audit {'decisions': 74810, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/A/r5_scores.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C5-entrygated | +10 | POOLED | Qstack | - | 0.575 [-,-] | - | - | 0.499 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | POOLED | Qstack | - | 0.570 [-,-] | - | - | 0.502 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | POOLED | Qstack | - | 0.558 [-,-] | - | - | 0.497 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | POOLED | Qstack | - | 0.550 [-,-] | - | - | 0.496 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | POOLED | Qstack | - | 0.544 [-,-] | - | - | 0.459 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | ASIA | Qstack | - | 0.541 [-,-] | - | - | 0.538 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +20 | NY | pE | - | 0.533 [-,-] | - | - | 0.883 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | LONDON | Qstack | - | 0.531 [-,-] | - | - | 0.550 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | LONDON | Qstack | - | 0.530 [-,-] | - | - | 0.578 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | NY | C5stack | - | 0.529 [-,-] | - | - | 0.880 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | NY | Qstack | - | 0.527 [-,-] | - | - | 0.596 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | ASIA | C5stack | - | 0.526 [-,-] | - | - | 0.551 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | NY | Qstack | - | 0.523 [-,-] | - | - | 0.541 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | POOLED | Qstack | - | 0.521 [-,-] | - | - | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | POOLED | C5stack | - | 0.517 [-,-] | - | - | 0.733 | - | 755 | 0 | - | 1/5 |  | locked label (reference only) |
| C5-entrygated | +15 | LONDON | Qstack | - | 0.517 [-,-] | - | - | 0.547 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | LONDON | C5stack | - | 0.515 [-,-] | - | - | 0.731 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | NY | C5stack | - | 0.514 [-,-] | - | - | 0.874 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | ASIA | Qstack | - | 0.512 [-,-] | - | - | 0.496 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | ASIA | Qstack | - | 0.510 [-,-] | - | - | 0.503 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | ASIA | C5stack | - | 0.508 [-,-] | - | - | 0.539 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +15 | ASIA | pE | - | 0.505 [-,-] | - | - | 0.537 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | POOLED | C5stack | - | 0.505 [-,-] | - | - | 0.730 | - | 707 | 0 | - | 1/5 |  | locked label (reference only) |
| C5-entrygated | +20 | ASIA | C5stack | - | 0.505 [-,-] | - | - | 0.524 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | ASIA | Qstack | - | 0.505 [-,-] | - | - | 0.497 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +30 | NY | pE | - | 0.503 [-,-] | - | - | 0.873 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | ASIA | Qstack | - | 0.502 [-,-] | - | - | 0.509 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | LONDON | Qstack | - | 0.502 [-,-] | - | - | 0.571 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +15 | NY | pE | - | 0.501 [-,-] | - | - | 0.871 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | ASIA | Qstack | - | 0.500 [-,-] | - | - | 0.492 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | ASIA | C5stack | - | 0.499 [-,-] | - | - | 0.525 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +30 | ASIA | pE | - | 0.497 [-,-] | - | - | 0.543 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +20 | ASIA | pE | - | 0.496 [-,-] | - | - | 0.528 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | NY | Qstack | - | 0.496 [-,-] | - | - | 0.560 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +15 | LONDON | C5stack | - | 0.493 [-,-] | - | - | 0.727 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +5 | ASIA | pE | - | 0.493 [-,-] | - | - | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | POOLED | C5stack | - | 0.492 [-,-] | - | - | 0.715 | - | 82 | 0 | - | 1/5 |  | locked label (reference only) |
| C5-entrygated | pre | ASIA | C5stack | - | 0.489 [-,-] | - | - | 0.516 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +10 | LONDON | pE | - | 0.488 [-,-] | - | - | 0.718 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | NY | C5stack | - | 0.487 [-,-] | - | - | 0.847 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | ASIA | C5stack | - | 0.484 [-,-] | - | - | 0.514 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +20 | LONDON | C5stack | - | 0.480 [-,-] | - | - | 0.721 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +15 | LONDON | pE | - | 0.480 [-,-] | - | - | 0.715 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +10 | ASIA | pE | - | 0.475 [-,-] | - | - | 0.502 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +5 | NY | pE | - | 0.473 [-,-] | - | - | 0.842 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +10 | NY | C5stack | - | 0.473 [-,-] | - | - | 0.851 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | POOLED | C5stack | - | 0.473 [-,-] | - | - | 0.708 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | LONDON | Qstack | - | 0.470 [-,-] | - | - | 0.489 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +10 | NY | pE | - | 0.470 [-,-] | - | - | 0.852 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | POOLED | C5stack | - | 0.470 [-,-] | - | - | 0.719 | - | 15 | 0 | - | 1/5 |  | locked label (reference only) |
| C5-entrygated | +5 | NY | Qstack | - | 0.468 [-,-] | - | - | 0.523 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | NY | C5stack | - | 0.464 [-,-] | - | - | 0.864 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +5 | LONDON | pE | - | 0.464 [-,-] | - | - | 0.710 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | NY | Qstack | - | 0.462 [-,-] | - | - | 0.533 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +30 | LONDON | pE | - | 0.461 [-,-] | - | - | 0.720 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | POOLED | C5stack | - | 0.461 [-,-] | - | - | 0.694 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | NY | C5stack | - | 0.460 [-,-] | - | - | 0.833 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | pre | LONDON | pE | - | 0.459 [-,-] | - | - | 0.701 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +30 | LONDON | C5stack | - | 0.458 [-,-] | - | - | 0.721 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | pre | ASIA | pE | - | 0.458 [-,-] | - | - | 0.486 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | LONDON | C5stack | - | 0.457 [-,-] | - | - | 0.700 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | pre | NY | Qstack | - | 0.457 [-,-] | - | - | 0.462 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | pre | NY | pE | - | 0.453 [-,-] | - | - | 0.835 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +20 | LONDON | pE | - | 0.446 [-,-] | - | - | 0.702 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | LONDON | C5stack | - | 0.445 [-,-] | - | - | 0.705 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +15 | POOLED | pE | - | 0.437 [-,-] | - | - | 0.701 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +30 | POOLED | pE | - | 0.436 [-,-] | - | - | 0.708 | - | - | - | - | - |  | locked label (reference only) |
| C5-entrygated | +5 | LONDON | Qstack | - | 0.435 [-,-] | - | - | 0.522 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +20 | POOLED | pE | - | 0.431 [-,-] | - | - | 0.698 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +5 | POOLED | pE | - | 0.414 [-,-] | - | - | 0.679 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | +10 | POOLED | pE | - | 0.412 [-,-] | - | - | 0.680 | - | - | - | - | - |  | locked label (reference only) |
| A-ctrl-pEntry | pre | POOLED | pE | - | 0.407 [-,-] | - | - | 0.672 | - | - | - | - | - |  | locked label (reference only) |

One-sentence notes:
- C5-entrygated 0 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count 1
- C5-entrygated 10 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count 1
- C5-entrygated 15 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count 1
- C5-entrygated 20 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count 1
- C5-entrygated 30 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 0 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 5 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 10 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 15 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 20 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- C5-entrygated 30 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 0 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 0 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 0 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 0 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 5 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 5 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 5 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 5 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 10 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 10 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 10 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 10 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 15 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 15 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 15 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 15 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 20 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 20 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 20 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 20 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 30 POOLED: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 30 ASIA: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 30 LONDON: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
- A-ctrl-pEntry 30 NY: entry-prediction (cond-on-entry AUC ~0.5); econ hard-halt best pass_count n/a
