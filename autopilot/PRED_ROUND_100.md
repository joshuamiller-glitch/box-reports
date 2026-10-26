# PRED ROUND 100 - block I round 11 - I5-rocket-vet

Best HOLDOUT F-R AUC: +15 POOLED - | ASIA 0.609 [0.55,0.67] | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED - | ASIA 0.569 [0.50,0.62] | LONDON - | NY -
Best G HOLDOUT AUC: -
Gap to FOUND: 0.051 AUC, 5 of 5 economic conditions short.
not found - short by 0.051 AUC and 5 of 5 economic conditions

prereg 111110ccdf5131f55571ae0ab37a8bb5e430e3f068915cf93609c0a704143996 ; trials added 6857 ; truncation audit {'decisions': 240, 'mismatches': 0, 'fixed_and_rerun': False} ; holdout scored True ; feature store ['l2vast/pred/store/I5.parquet', 'l2vast/pred/store/I5b.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I5-rocket-vet | +15 | ASIA | rf/pooled/BOTH | 0.585 [0.54,0.63] | 0.609 [0.55,0.67] | 0.582 | 0.599 | - | - | - | - | - | - | stack | promising: short by 0.051 AUC, 5 of 5 econ |
| I5-rocket-replication(fresh kernels,seed777,shifted folds) | +15 | ASIA | rf/pooled/BOTH | 0.569 [-,-] | 0.592 [0.53,0.65] | - | 0.584 | - | - | - | - | - | - | stack | promising: short by 0.068 AUC, 5 of 5 econ |
| I5-rocket-replication(fresh kernels,seed777,shifted folds) | +10 | ASIA | rf/pooled/BOTH | 0.580 [-,-] | 0.591 [0.53,0.65] | - | 0.581 | - | - | - | - | - | - | stack | short by 0.069 AUC, 5 of 5 econ |
| I5-rocket-replication(fresh kernels,seed777,shifted folds) | +30 | ASIA | rf/pooled/BOTH | 0.549 [-,-] | 0.569 [0.50,0.62] | - | 0.556 | - | - | - | - | - | - | stack | short by 0.091 AUC, 5 of 5 econ |
| I5-rocket-replication(fresh kernels,seed777,shifted folds) | +20 | ASIA | rf/pooled/BOTH | 0.559 [-,-] | 0.566 [0.50,0.63] | - | 0.560 | - | - | - | - | - | - | stack | short by 0.094 AUC, 5 of 5 econ |
| I5-rocket-reverse-time(2023-04..2024-01) | +10 | ASIA | rf/pooled/BOTH | 0.533 [0.46,0.60] | - | - | - | - | - | - | - | - | - | stack | no-holdout |
| I5-rocket-reverse-time(2023-04..2024-01) | +15 | ASIA | rf/pooled/BOTH | 0.556 [0.48,0.62] | - | - | - | - | - | - | - | - | - | stack | no-holdout |
| I5-rocket-reverse-time(2023-04..2024-01) | +20 | ASIA | rf/pooled/BOTH | 0.530 [0.46,0.60] | - | - | - | - | - | - | - | - | - | stack | no-holdout |
| I5-rocket-reverse-time(2023-04..2024-01) | +30 | ASIA | rf/pooled/BOTH | 0.564 [0.48,0.65] | - | - | - | - | - | - | - | - | - | stack | no-holdout |

One-sentence notes:
- I5-rocket-vet 15 ASIA: vetted: holdout 0.609 vs bar 0.66, strata 0.599, noise share 0.24 fails, econ max 2/5, placebo(20 seeds) hold mean 0.508 sd 0.032 max 0.571, fresh-kernel replication 0.592, reverse-time 2023-04..2024-01 0.556 [0.481,0.624]; best-of-864 pick
- I5-rocket-replication(fresh kernels,seed777,shifted folds) 10 ASIA: replication of the family with fresh kernels
- I5-rocket-replication(fresh kernels,seed777,shifted folds) 15 ASIA: replication of the family with fresh kernels
- I5-rocket-replication(fresh kernels,seed777,shifted folds) 20 ASIA: replication of the family with fresh kernels
- I5-rocket-replication(fresh kernels,seed777,shifted folds) 30 ASIA: replication of the family with fresh kernels
- I5-rocket-reverse-time(2023-04..2024-01) 10 ASIA: train 2024-02..2026-10, test never-scored 2023-04..2024-01
- I5-rocket-reverse-time(2023-04..2024-01) 15 ASIA: train 2024-02..2026-10, test never-scored 2023-04..2024-01
- I5-rocket-reverse-time(2023-04..2024-01) 20 ASIA: train 2024-02..2026-10, test never-scored 2023-04..2024-01
- I5-rocket-reverse-time(2023-04..2024-01) 30 ASIA: train 2024-02..2026-10, test never-scored 2023-04..2024-01
