# PRED ROUND 27 - block B round 2 - B57+B5+B7

Best HOLDOUT F-R AUC: +15 POOLED 0.524 [-,-] | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED 0.535 [-,-] | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.584 [0.56,0.61]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg d4f79e5416474c3e020adaf16bda775f432c34e1bcd138a0f412ffac53b2009c ; trials added 1200 ; truncation audit {'decisions': 160, 'mismatches': 0, 'fixed_and_rerun': False, 'detail': 'engine decisions 160 checks 35200 mismatches 0 {}; builder months 0 mismatching columns []'} ; holdout scored True ; feature store ['l2vast/pred/store/B5_round2.parquet.parquet', 'l2vast/pred/store/B5_round2_sig.parquet.parquet', 'l2vast/pred/store/B7_round2.parquet.parquet', 'l2vast/pred/store/B7_round2_sig.parquet.parquet', 'l2vast/pred/store/X18_round2.parquet.parquet', 'l2vast/pred/store/X18_round2_sig.parquet.parquet', 'l2vast/pred/store/X20_round2.parquet.parquet', 'l2vast/pred/store/X4_round2.parquet.parquet', 'l2vast/pred/store/X5_round2.parquet.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B5-G | sig | POOLED | rf | 0.582 [0.56,0.60] | 0.584 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B57-G | sig | POOLED | rf | 0.584 [0.56,0.60] | 0.584 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B7-G | sig | POOLED | rf | 0.583 [0.56,0.60] | 0.583 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B5 | +30 | POOLED | gbt3 | - | 0.535 [-,-] | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +15 | POOLED | stack | - | 0.524 [-,-] | - | - | 0.699 | - | - | - | - | - | stack | locked label (reference only) |
| B5 | +10 | POOLED | rf | - | 0.520 [-,-] | - | - | 0.669 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +30 | POOLED | gbt3 | - | 0.515 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | +30 | POOLED | gbt3 | - | 0.515 [-,-] | - | - | 0.673 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +15 | POOLED | rf | - | 0.515 [-,-] | - | - | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | +15 | POOLED | stack | - | 0.510 [-,-] | - | - | 0.650 | - | - | - | - | - | stack | locked label (reference only) |
| B5-G | sig | POOLED | rf | 0.499 [0.48,0.52] | 0.497 [0.47,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B7-G | sig | POOLED | gbt3 | 0.510 [0.49,0.53] | 0.490 [0.47,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B57-G | sig | POOLED | gbt3 | 0.493 [0.48,0.51] | 0.483 [0.46,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B7 | pre | POOLED | rf | - | 0.481 [-,-] | - | - | 0.644 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | pre | POOLED | rf | - | 0.479 [-,-] | - | - | 0.642 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +30 | ASIA | gbt3 | - | - | - | - | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +30 | LONDON | gbt3 | - | - | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +30 | NY | gbt3 | - | - | - | - | 0.783 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | pre | ASIA | rf | - | - | - | - | 0.542 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | pre | LONDON | rf | - | - | - | - | 0.633 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | pre | NY | rf | - | - | - | - | 0.695 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +15 | ASIA | rf | - | - | - | - | 0.524 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +15 | LONDON | rf | - | - | - | - | 0.613 | ok | - | - | - | - | stack | locked label (reference only) |
| B57 | +15 | NY | rf | - | - | - | - | 0.705 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +30 | ASIA | gbt3 | - | - | - | - | 0.547 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +30 | LONDON | gbt3 | - | - | - | - | 0.648 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +30 | NY | gbt3 | - | - | - | - | 0.804 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +10 | ASIA | rf | - | - | - | - | 0.522 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +10 | LONDON | rf | - | - | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +10 | NY | rf | - | - | - | - | 0.757 | ok | - | - | - | - | stack | locked label (reference only) |
| B5 | +15 | ASIA | stack | - | - | - | - | 0.574 | - | - | - | - | - | stack | locked label (reference only) |
| B5 | +15 | LONDON | stack | - | - | - | - | 0.663 | - | - | - | - | - | stack | locked label (reference only) |
| B5 | +15 | NY | stack | - | - | - | - | 0.803 | - | - | - | - | - | stack | locked label (reference only) |
| B7 | +30 | ASIA | gbt3 | - | - | - | - | 0.510 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | +30 | LONDON | gbt3 | - | - | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | +30 | NY | gbt3 | - | - | - | - | 0.783 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | pre | ASIA | rf | - | - | - | - | 0.537 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | pre | LONDON | rf | - | - | - | - | 0.642 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | pre | NY | rf | - | - | - | - | 0.699 | ok | - | - | - | - | stack | locked label (reference only) |
| B7 | +15 | ASIA | stack | - | - | - | - | 0.509 | - | - | - | - | - | stack | locked label (reference only) |
| B7 | +15 | LONDON | stack | - | - | - | - | 0.608 | - | - | - | - | - | stack | locked label (reference only) |
| B7 | +15 | NY | stack | - | - | - | - | 0.737 | - | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- B57 30 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 30 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 30 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 30 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 0 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 0 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 0 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 0 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 15 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 15 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 15 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57 15 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 30 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 30 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 30 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 30 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 10 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 10 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 10 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 10 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 15 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 15 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 15 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B5 15 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 30 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 30 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 30 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 30 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 0 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 0 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 0 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 0 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 15 POOLED: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 15 ASIA: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 15 LONDON: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B7 15 NY: selected on WF-PRE; below R0 baseline on holdout unless noted in report
- B57-G -1 POOLED: selected on WF-PRE
- B5-G -1 POOLED: selected on WF-PRE
- B7-G -1 POOLED: selected on WF-PRE
- B57-G -1 POOLED: selected on WF-PRE
- B5-G -1 POOLED: selected on WF-PRE
- B7-G -1 POOLED: selected on WF-PRE
