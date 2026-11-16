# DS3_FLOW PART A (W-CF2 contribution): wide order-by-order library, FIRST PASS (table level; engine actions are W-FL1's)
VERDICT (data ends 2026-11-13): of 449 order-by-order features (4,647 scored items after the 2%-70% yes-share rule, each at latency 0/1/2/5 s) 453 distinct items in 282 near-duplicate clusters pass at least one cell on the pooled statistic (calibrated bar) or the within-book-session-month statistic with the same sign in >= 3 of 4 years and in L6M; pooled ALL cell: 8 clusters (all 'busy book' raw activity items: more own-side adds / cancels / flicker is worse, about -$130 per trade, t -4.2 to -4.5); within-month ALL cell: 143 clusters. The arrival-imbalance lead is the same finding as before (own-side adds high versus the other side is bad, LOW good, about $110-127 per trade, t 2.5-2.9 pooled, 2.4-2.7 within months) and is NOT the strongest member of the family; NY AM adds a depth reading (own minus other depth low, +$155..217, t 3.4-3.9, L6M +$125..$930). Nothing is a PASS for D7: engine actions (skip / half / x1.5 / x2 / wait) are W-FL1's. Nearly all items need the live L3 feed (table at the end).

Basis: JN05W2 taken trades to 2026-11-13 (20,138), net $ per trade at base lots (engine fee), R per trade; weekly-cluster t. Library = code/th_confl_cf2/flow_lib.py over the per-second order-by-order tables (cf2_mbo3). Windows 1,5,15,30,60,120,300 s ending the second before the entry second; own / other / difference; raw and percentile of the previous 20 sessions at the same ET clock minute +-2 (20 x 5 samples); tails LOW <= 20th and HIGH >= 80th percentile; levels L0 = touch, L2 = within 2 ticks (levels 1-3), L9 = within 9 ticks (levels 1-10). Pre-registration: autopilot/PREREG_FLOW_PARTA_20261116.md sha256 ec3f22f4... with three amendments logged in DECISIONS.md (planted effects raised after the first check failed on power; bar calibrated on the shuffled-outcome null; within-month statistic ADDED AFTER READING the pooled summary, labelled).

## 1. Planted-edge check (before any real result was read)

First run (+150/+80/+40/0): recovered 114/19/-12/-47, t 2.5/0.5/-0.4/-1.2 -> FAIL on power (standard error of a lift at a 14% share is about $46, minimum detectable effect about $155). Second run (+600/+350/+200/0): recovered 560/278/146/-31 (93%/80%/73% of planted), t 12.3/6.9/5.1/-0.8, ranks 1/18.5/62.5/2,470 of 4,647. Null run (shuffled outcomes, no plant): 3.7% of lag-0 items beat the placebo-shift p99 bar (instead of 1%), because lag-0 features share the outcome's month/regime structure; so the pass bar is the larger of the placebo-shift p99 and the null lag-0 p99 (ALL 4.15; at that bar the null false-positive share is 1.0%). PASS with that bar.

## 2. Bars used

Pooled statistic: ALL 4.15, session 0 2.83, session 1 2.78, session 3 2.92, session 4 2.84. Within-book-session-month statistic (outcomes demeaned inside each book x session x month): ALL 2.43, session 0 2.70, session 1 2.90, session 3 2.32, session 4 3.12. A 'stable' item additionally has the same sign in >= 3 of 4 years and in L6M in the cell. Minimum detectable effect at the bar is about 3.4-4.2 x the item's standard error (about $155 pooled at a 14% share; larger in a session cell); 'not detected' never means 'no effect'.

## 3. Passing counts

| stat   | cell     |   rows |   items |   clusters |
|:-------|:---------|-------:|--------:|-----------:|
| pooled | ALL      |     16 |      16 |          8 |
| pooled | sess:0.0 |     20 |      20 |         14 |
| pooled | sess:1.0 |     14 |      14 |         10 |
| pooled | sess:3.0 |     53 |      53 |         29 |
| pooled | sess:4.0 |     26 |      26 |         21 |
| within | ALL      |    209 |     209 |        145 |
| within | sess:0.0 |     33 |      33 |         25 |
| within | sess:1.0 |      6 |       6 |          5 |
| within | sess:3.0 |    235 |     235 |        124 |
| within | sess:4.0 |      5 |       5 |          5 |

## 4. Family map (stable passing items, within-month statistic, by cell)

| family                  |   ALL |   sess:0.0 |   sess:1.0 |   sess:3.0 |   sess:4.0 |
|:------------------------|------:|-----------:|-----------:|-----------:|-----------:|
| absorption              |     1 |          0 |          0 |          2 |          0 |
| arrivals (count)        |    21 |          1 |          1 |         11 |          0 |
| arrivals (size)         |    20 |          2 |          0 |         12 |          0 |
| book at stop/target     |     1 |          1 |          0 |          7 |          0 |
| cancels                 |    42 |          9 |          0 |         31 |          2 |
| cancels (cancel-to-add) |     0 |          1 |          2 |         13 |          1 |
| cancels (fleeting)      |    12 |          1 |          0 |          9 |          0 |
| hidden size             |     0 |          0 |          0 |          3 |          0 |
| liquidity pulling       |     2 |          0 |          0 |          5 |          0 |
| order size mix          |     1 |          0 |          0 |          1 |          0 |
| price impact            |     1 |          0 |          0 |          1 |          0 |
| queue                   |    15 |          6 |          0 |          8 |          1 |
| queue (flicker)         |     3 |          0 |          2 |          0 |          0 |
| queue / depth           |    37 |          3 |          0 |         33 |          1 |
| sweeps                  |     0 |          0 |          0 |          2 |          0 |
| sweeps (refill)         |     1 |          0 |          0 |          0 |          0 |
| trades                  |     2 |          2 |          0 |          2 |          0 |
| trades / size mix       |     4 |          0 |          0 |          4 |          0 |

## 5. Top cluster representatives per cell and statistic ($/trade and R/trade vs the cell, by year, latency ok = same sign and above the bar when the value is 1/2/5 s late, cluster size = near-duplicate items)


### within statistic, cell ALL

| item                        |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:----------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| cancn_L2|W30|own|pct|hi     |    7487 |   -125 |    -0.031 | -3.92 | 2.43376 |         -54 |        -133 |        -125 |        -102 |       -117 | True      | True      | True      | NOT-yes=favourable |              5 | L3                                                     |
| addv_L0|W60|diff|pct|hi     |    6968 |   -112 |    -0.044 | -3.85 | 2.43376 |        -153 |         -89 |        -172 |         -73 |       -109 | True      | True      | True      | NOT-yes=favourable |              2 | L3                                                     |
| orders_L9|W120|other|pct|lo |    5662 |   -147 |    -0.037 | -3.85 | 2.43376 |        -136 |          -6 |        -115 |        -209 |       -233 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| orders_L2|W60|other|pct|lo  |    5260 |   -143 |    -0.045 | -3.84 | 2.43376 |         -38 |           2 |        -152 |        -211 |       -233 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| depth_L9|W120|other|pct|lo  |    5218 |   -152 |    -0.045 | -3.82 | 2.43376 |        -129 |         -31 |         -94 |        -214 |       -247 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| cancn_L2|W60|diff|raw|hi    |    5657 |   -119 |    -0.047 | -3.76 | 2.43376 |        -205 |        -176 |        -143 |        -152 |       -183 | True      | True      | True      | NOT-yes=favourable |              2 | L3                                                     |
| depth_L2|W60|other|pct|lo   |    4849 |   -142 |    -0.053 | -3.74 | 2.43376 |         -61 |          21 |        -138 |        -230 |       -239 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| fleetn|W5|diff|pct|hi       |    5343 |   -132 |    -0.049 | -3.67 | 2.43376 |         -43 |        -185 |         -89 |        -156 |       -212 | True      | True      | True      | NOT-yes=favourable |              1 | L3                                                     |
| depth_L2|W120|diff|raw|lo   |    3708 |    156 |     0.065 |  3.63 | 2.43376 |          50 |         131 |         246 |         241 |        419 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| addv_L2|W30|own|pct|hi      |    7862 |   -110 |    -0.027 | -3.61 | 2.43376 |          13 |        -139 |        -109 |        -104 |       -112 | True      | True      | True      | NOT-yes=favourable |              4 | L3                                                     |

### within statistic, cell sess:3.0

| item                           |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:-------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| depth_L2|W5|diff|raw|lo        |    1014 |    188 |     0.142 |  3.84 | 2.31668 |         220 |         258 |         116 |         216 |        125 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| depth_L2|W30|diff|raw|lo       |     867 |    217 |     0.156 |  3.81 | 2.31668 |         226 |         199 |         112 |         495 |        933 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| depth_L9|W30|diff|raw|lo       |    1170 |    183 |     0.103 |  3.78 | 2.31668 |         202 |         212 |          77 |         291 |        386 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| cancv_ratio_L9|W15|diff|pct|lo |    1256 |    161 |     0.069 |  3.61 | 2.31668 |         115 |         286 |          48 |          94 |        146 | True      | False     | False     | yes=favourable     |              2 | L3                                                     |
| absorb_ratio|W5|own|pct|lo     |     681 |   -196 |    -0.082 | -3.59 | 2.31668 |        -133 |        -174 |        -181 |        -213 |       -136 | False     | False     | False     | NOT-yes=favourable |              1 | L1 trades + price (D7 own series)                      |
| touch_sz|W300|diff|pct|lo      |    1216 |    156 |     0.076 |  3.58 | 2.31668 |         247 |         148 |          54 |         272 |        398 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes; order counts need L3               |
| pull_n_L2|W60|diff|pct|hi      |    1943 |   -145 |    -0.106 | -3.55 | 2.31668 |         -73 |         -95 |        -212 |        -303 |       -183 | True      | True      | True      | NOT-yes=favourable |             12 | L3                                                     |
| addn_L9|W60|other|pct|hi       |    1463 |   -174 |    -0.094 | -3.47 | 2.31668 |        -110 |         -99 |        -133 |        -331 |       -165 | True      | True      | True      | NOT-yes=favourable |              9 | L3                                                     |
| addv_L9|W120|other|pct|hi      |    1397 |   -174 |    -0.095 | -3.4  | 2.31668 |         -55 |        -134 |        -149 |        -323 |       -194 | True      | True      | True      | NOT-yes=favourable |              9 | L3                                                     |
| depth_L2|W60|diff|raw|lo       |     888 |    195 |     0.118 |  3.39 | 2.31668 |         227 |         251 |          58 |         333 |        559 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |

### within statistic, cell sess:0.0

| item                             |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:---------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| cancv_ratio_L2|W15|diff|raw|lo   |    1855 |    244 |     0.047 |  3.37 | 2.70005 |         430 |          82 |           6 |         501 |        535 | False     | False     | False     | yes=favourable     |              2 | L3                                                     |
| addv_L0|W60|diff|pct|hi          |    2685 |   -196 |    -0.041 | -3.12 | 2.70005 |        -128 |         -89 |        -417 |        -131 |       -179 | True      | True      | True      | NOT-yes=favourable |              2 | L3                                                     |
| touch_meansize|W120|own|raw|lo   |    2867 |   -199 |    -0.036 | -3.02 | 2.70005 |         nan |        -549 |        -259 |        -201 |       -174 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes; order counts need L3               |
| touch_meansize|W120|own|pct|lo   |    1604 |   -257 |    -0.068 | -3.01 | 2.70005 |         -42 |        -323 |        -176 |        -306 |       -302 | True      | True      | True      | NOT-yes=favourable |              1 | L2 depth for sizes; order counts need L3               |
| depth_L9|W300|diff|pct|lo        |    1473 |    269 |     0.059 |  2.97 | 2.70005 |           9 |         217 |         235 |         341 |        344 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| orders_L9|W60|other|pct|lo       |    2209 |   -247 |    -0.054 | -2.96 | 2.70005 |         -55 |         109 |        -117 |        -482 |       -595 | True      | True      | False     | NOT-yes=favourable |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| touch_meansize|W300|other|pct|hi |    1740 |    242 |     0.065 |  2.93 | 2.70005 |         345 |         -60 |         462 |         168 |        121 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes; order counts need L3               |
| cancn_L2|W15|diff|raw|lo         |    1167 |    256 |     0.07  |  2.89 | 2.70005 |         150 |         219 |         451 |         167 |        274 | True      | False     | False     | yes=favourable     |              2 | L3                                                     |
| cancv_L0|W15|diff|raw|lo         |    1104 |    269 |     0.059 |  2.89 | 2.70005 |         -95 |         385 |         573 |         153 |        300 | False     | False     | False     | yes=favourable     |              2 | L3                                                     |
| cancv_L9|W60|diff|pct|hi         |    2006 |   -205 |    -0.057 | -2.88 | 2.70005 |         237 |        -240 |        -258 |        -244 |       -275 | True      | True      | False     | NOT-yes=favourable |              2 | L3                                                     |

### within statistic, cell sess:1.0

| item                           |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live            |
|:-------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:----------------|
| cancv_ratio_L9|W1|other|pct|lo |    1021 |   -185 |    -0.075 | -3.35 | 2.89509 |        -178 |        -253 |        -252 |        -113 |       -145 | False     | False     | False     | NOT-yes=favourable |              2 | L3              |
| flicker|W60|diff|pct|hi        |    2347 |   -153 |    -0.032 | -3.18 | 2.89509 |          -6 |        -119 |        -186 |        -179 |       -175 | False     | False     | False     | NOT-yes=favourable |              1 | L1 quotes (NT8) |
| addn_L2|W15|diff|pct|hi        |    2190 |   -137 |    -0.058 | -3.01 | 2.89509 |          32 |        -340 |        -132 |         -65 |        -14 | True      | False     | False     | NOT-yes=favourable |              2 | L3              |
| flicker|W60|diff|raw|hi        |    2278 |   -151 |    -0.044 | -3    | 2.89509 |         -43 |        -197 |        -165 |        -145 |       -169 | True      | True      | True      | NOT-yes=favourable |              1 | L1 quotes (NT8) |

### within statistic, cell sess:4.0

| item                          |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| depth_L2|W1|diff|raw|hi       |     341 |    260 |     0.19  |  3.89 | 3.12374 |         226 |         466 |         194 |         197 |        250 | False     | False     | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| cancv_LD|W300|diff|pct|hi     |     487 |    273 |     0.163 |  3.5  | 3.12374 |         715 |         -48 |         428 |         200 |        371 | True      | True      | True      | yes=favourable     |              1 | L3                                                     |
| cancn_ratio_L0|W30|own|pct|hi |     231 |   -253 |    -0.18  | -3.32 | 3.12374 |        -197 |        -124 |        -420 |        -232 |        -26 | True      | False     | False     | NOT-yes=favourable |              1 | L3                                                     |
| touch_meansize|W1|diff|raw|hi |     238 |    299 |     0.165 |  3.21 | 3.12374 |        -140 |         528 |         226 |         422 |        401 | False     | False     | False     | yes=favourable     |              1 | L2 depth for sizes; order counts need L3               |
| cancn_LD|W300|diff|pct|hi     |     639 |    233 |     0.163 |  3.15 | 3.12374 |         470 |         142 |         378 |          66 |         72 | False     | True      | False     | yes=favourable     |              1 | L3                                                     |

### pooled statistic, cell ALL

| item                          |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live            |
|:------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:----------------|
| fleetn|W5|other|raw|hi        |    6073 |   -135 |    -0.025 | -4.52 | 4.15488 |         -50 |        -154 |        -119 |        -165 |       -201 | False     | False     | False     | NOT-yes=favourable |              7 | L3              |
| cancn_L2|W60|diff|raw|hi      |    5657 |   -142 |    -0.047 | -4.38 | 4.15488 |        -205 |        -176 |        -143 |        -152 |       -183 | False     | False     | False     | NOT-yes=favourable |              2 | L3              |
| cancv_L9|W30|own|raw|hi       |    6093 |   -131 |    -0.019 | -4.35 | 4.15488 |         -77 |        -124 |        -125 |        -156 |       -177 | True      | True      | True      | NOT-yes=favourable |              1 | L3              |
| fleet_share|W30|other|raw|hi  |    6584 |   -132 |    -0.029 | -4.34 | 4.15488 |         -49 |        -118 |        -131 |        -176 |       -221 | True      | False     | False     | NOT-yes=favourable |              1 | L3              |
| refill_full|W120|other|raw|hi |    5659 |   -129 |    -0.021 | -4.31 | 4.15488 |         -72 |        -122 |        -114 |        -171 |       -181 | False     | False     | False     | NOT-yes=favourable |              2 | L2              |
| flicker|W30|own|raw|hi        |    7268 |   -139 |    -0.029 | -4.24 | 4.15488 |         -43 |        -127 |        -179 |        -180 |       -231 | True      | True      | True      | NOT-yes=favourable |              1 | L1 quotes (NT8) |
| addv_L0|W60|diff|raw|hi       |    7120 |   -130 |    -0.041 | -4.2  | 4.15488 |         -51 |        -163 |        -188 |        -103 |       -141 | False     | True      | False     | NOT-yes=favourable |              2 | L3              |
| flicker|W120|own|raw|hi       |    7028 |   -140 |    -0.026 | -4.18 | 4.15488 |         -74 |        -127 |        -149 |        -188 |       -201 | False     | False     | True      | NOT-yes=favourable |              1 | L1 quotes (NT8) |

### pooled statistic, cell sess:3.0

| item                      |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:--------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| depth_L2|W5|diff|raw|lo   |    1014 |    196 |     0.142 |  3.87 | 2.92373 |         220 |         258 |         116 |         216 |        125 | True      | False     | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| pull_n_L2|W60|diff|pct|hi |    1943 |   -169 |    -0.106 | -3.72 | 2.92373 |         -73 |         -95 |        -212 |        -303 |       -183 | True      | True      | True      | NOT-yes=favourable |             12 | L3                                                     |
| depth_L2|W30|diff|raw|lo  |     867 |    214 |     0.156 |  3.67 | 2.92373 |         226 |         199 |         112 |         495 |        933 | False     | True      | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| touch_sz|W300|diff|pct|lo |    1216 |    161 |     0.076 |  3.62 | 2.92373 |         247 |         148 |          54 |         272 |        398 | True      | True      | True      | yes=favourable     |              1 | L2 depth for sizes; order counts need L3               |
| cancv_L2|W5|diff|pct|hi   |    1074 |   -156 |    -0.105 | -3.42 | 2.92373 |           0 |        -269 |         -24 |        -311 |       -419 | False     | False     | False     | NOT-yes=favourable |              1 | L3                                                     |
| hidden|W60|own|raw|lo     |     121 |   -352 |    -0.219 | -3.41 | 2.92373 |         nan |        -873 |        -166 |        -298 |       -179 | False     | False     | False     | NOT-yes=favourable |              1 | L3 (refill) / L2+trades (hidden proxy)                 |
| depth_L2|W60|diff|raw|lo  |     888 |    194 |     0.118 |  3.37 | 2.92373 |         227 |         251 |          58 |         333 |        559 | True      | True      | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| pull_v_L9|W120|own|pct|hi |    2095 |   -153 |    -0.103 | -3.35 | 2.92373 |        -106 |         -37 |        -200 |        -293 |       -170 | True      | True      | False     | NOT-yes=favourable |              8 | L3                                                     |
| depth_L2|W60|diff|pct|lo  |    1119 |    169 |     0.119 |  3.33 | 2.92373 |         292 |         170 |          51 |         228 |        376 | True      | True      | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| hidden|W15|own|pct|hi     |    1273 |   -157 |    -0.068 | -3.33 | 2.92373 |        -222 |        -109 |        -158 |        -145 |       -190 | True      | True      | False     | NOT-yes=favourable |              1 | L3 (refill) / L2+trades (hidden proxy)                 |

### pooled statistic, cell sess:0.0

| item                                |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                         |
|:------------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:---------------------------------------------|
| cancv_ratio_L2|W15|diff|raw|lo      |    1855 |    238 |     0.047 |  3.28 | 2.82524 |         430 |          82 |           6 |         501 |        535 | False     | False     | False     | yes=favourable     |              2 | L3                                           |
| touch_meansize|W1|own|raw|hi        |    1338 |   -269 |    -0.096 | -3.1  | 2.82524 |        -543 |        -100 |        -402 |        -201 |       -222 | False     | False     | False     | NOT-yes=favourable |              2 | L2 depth for sizes; order counts need L3     |
| addv_L0|W60|diff|pct|hi             |    2685 |   -197 |    -0.041 | -3.05 | 2.82524 |        -128 |         -89 |        -417 |        -131 |       -179 | False     | True      | True      | NOT-yes=favourable |              2 | L3                                           |
| cancn_L2|W30|own|pct|hi             |    3020 |   -203 |    -0.032 | -3    | 2.82524 |          56 |        -377 |        -300 |        -128 |       -232 | False     | True      | True      | NOT-yes=favourable |              5 | L3                                           |
| addv_L2|W30|own|pct|hi              |    3167 |   -199 |    -0.037 | -2.96 | 2.82524 |         102 |        -333 |        -251 |        -183 |       -276 | True      | False     | False     | NOT-yes=favourable |              4 | L3                                           |
| cancn_L2|W60|diff|raw|hi            |    1743 |   -240 |    -0.057 | -2.96 | 2.82524 |       -1009 |        -372 |        -282 |        -214 |       -286 | False     | False     | False     | NOT-yes=favourable |              2 | L3                                           |
| addn_L2|W300|diff|pct|hi            |    2950 |   -217 |    -0.057 | -2.95 | 2.82524 |        -237 |        -365 |         -88 |        -247 |       -538 | True      | True      | True      | NOT-yes=favourable |              2 | L3                                           |
| absorb_ratio|W120|diff|raw|hi       |    1330 |   -236 |    -0.059 | -2.95 | 2.82524 |         -82 |        -496 |          19 |        -332 |       -180 | False     | False     | False     | NOT-yes=favourable |              1 | L1 trades + price (D7 own series)            |
| cancn_L9|W60|diff|raw|hi            |    1635 |   -236 |    -0.066 | -2.95 | 2.82524 |        -319 |        -479 |        -238 |        -234 |       -289 | False     | True      | True      | NOT-yes=favourable |              2 | L3                                           |
| targetdepth_chg_40|W60|other|raw|hi |    1279 |   -240 |    -0.043 | -2.91 | 2.82524 |        -172 |         -27 |        -440 |        -207 |       -102 | True      | True      | False     | NOT-yes=favourable |              2 | needs full-depth book (beyond 10 levels): L3 |

### pooled statistic, cell sess:1.0

| item                           |   n_yes |   lift |   R_trade |     t |     bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                    |
|:-------------------------------|--------:|-------:|----------:|------:|--------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:------------------------|
| cancv_ratio_L9|W1|other|pct|lo |    1021 |   -198 |    -0.075 | -3.42 | 2.78002 |        -178 |        -253 |        -252 |        -113 |       -145 | False     | False     | False     | NOT-yes=favourable |              2 | L3                      |
| cancv_ratio_L2|W1|other|pct|lo |    1027 |   -181 |    -0.063 | -3.13 | 2.78002 |        -325 |        -240 |        -241 |         -42 |        -52 | False     | False     | False     | NOT-yes=favourable |              2 | L3                      |
| cancv_L2|W1|own|pct|lo         |     939 |   -198 |    -0.076 | -3.1  | 2.78002 |        -397 |        -286 |        -105 |        -165 |       -186 | False     | False     | False     | NOT-yes=favourable |              2 | L3                      |
| flicker|W60|diff|pct|hi        |    2347 |   -150 |    -0.032 | -3.05 | 2.78002 |          -6 |        -119 |        -186 |        -179 |       -175 | False     | False     | False     | NOT-yes=favourable |              1 | L1 quotes (NT8)         |
| addn_L2|W15|diff|pct|hi        |    2190 |   -142 |    -0.058 | -3.03 | 2.78002 |          32 |        -340 |        -132 |         -65 |        -14 | True      | False     | False     | NOT-yes=favourable |              2 | L3                      |
| addn_L9|W15|diff|pct|lo        |    1147 |    181 |     0.079 |  2.93 | 2.78002 |        -216 |         464 |         144 |         161 |        194 | False     | False     | False     | yes=favourable     |              1 | L3                      |
| addn_L2|W30|diff|pct|lo        |    1036 |    194 |     0.081 |  2.91 | 2.78002 |         208 |         427 |         154 |          83 |          3 | False     | False     | False     | yes=favourable     |              1 | L3                      |
| gshare_1lot|W120|diff|raw|lo   |    2307 |    137 |     0.047 |  2.88 | 2.78002 |         400 |          90 |          87 |         135 |        110 | False     | False     | False     | yes=favourable     |              1 | L1 trades (approximate) |
| flicker|W60|diff|raw|hi        |    2278 |   -145 |    -0.044 | -2.85 | 2.78002 |         -43 |        -197 |        -165 |        -145 |       -169 | True      | True      | True      | NOT-yes=favourable |              1 | L1 quotes (NT8)         |
| cancn_L0|W1|other|pct|lo       |    1049 |   -165 |    -0.055 | -2.8  | 2.78002 |        -231 |        -267 |        -134 |         -97 |        -72 | False     | False     | False     | NOT-yes=favourable |              2 | L3                      |

### pooled statistic, cell sess:4.0

| item                            |   n_yes |   lift |   R_trade |     t |    bar |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M | ok_lag1   | ok_lag2   | ok_lag5   | dir                |   cluster_size | live                                                   |
|:--------------------------------|--------:|-------:|----------:|------:|-------:|------------:|------------:|------------:|------------:|-----------:|:----------|:----------|:----------|:-------------------|---------------:|:-------------------------------------------------------|
| depth_L2|W1|diff|raw|hi         |     341 |    280 |     0.19  |  3.91 | 2.8389 |         226 |         466 |         194 |         197 |        250 | False     | False     | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| cancn_LD|W300|diff|pct|hi       |     639 |    266 |     0.163 |  3.62 | 2.8389 |         470 |         142 |         378 |          66 |         72 | True      | True      | True      | yes=favourable     |              1 | L3                                                     |
| cancv_LD|W300|diff|pct|hi       |     487 |    280 |     0.163 |  3.55 | 2.8389 |         715 |         -48 |         428 |         200 |        371 | True      | True      | True      | yes=favourable     |              1 | L3                                                     |
| cancn_ratio_L9|W15|other|pct|hi |     205 |   -296 |    -0.185 | -3.23 | 2.8389 |        -152 |        -354 |        -164 |        -557 |       -624 | False     | False     | False     | NOT-yes=favourable |              2 | L3                                                     |
| stopdepth_chg_58|W60|own|pct|hi |     205 |    300 |     0.206 |  3.21 | 2.8389 |         231 |         211 |         376 |         391 |        367 | True      | True      | False     | yes=favourable     |              2 | needs full-depth book (beyond 10 levels): L3           |
| cancv_ratio_L2|W300|own|pct|lo  |     425 |    231 |     0.141 |  3.2  | 2.8389 |          96 |         201 |         177 |         466 |        535 | True      | True      | True      | yes=favourable     |              2 | L3                                                     |
| cancn_ratio_L2|W15|other|pct|hi |     207 |   -310 |    -0.193 | -3.18 | 2.8389 |        -246 |        -313 |        -239 |        -458 |       -476 | False     | False     | False     | NOT-yes=favourable |              2 | L3                                                     |
| hidden|W300|other|pct|hi        |     353 |    259 |     0.154 |  3.15 | 2.8389 |         267 |         266 |         263 |         232 |        282 | True      | True      | True      | yes=favourable     |              1 | L3 (refill) / L2+trades (hidden proxy)                 |
| orders_L2|W1|diff|pct|hi        |     237 |    258 |     0.194 |  3.11 | 2.8389 |          96 |         276 |         297 |         294 |        312 | False     | False     | False     | yes=favourable     |              1 | L2 depth for sizes (levels 1-10); order counts need L3 |
| targetdepth_58|W15|other|raw|hi |     376 |    224 |     0.131 |  3.1  | 2.8389 |          10 |         362 |         593 |          73 |        243 | False     | False     | False     | yes=favourable     |              2 | needs full-depth book (beyond 10 levels): L3           |

## 6. The arrival-imbalance lead inside the library (ALL cell, lag 0)

| feature      | tail   |   n_yes |    lift |     t |   w |
|:-------------|:-------|--------:|--------:|------:|----:|
| addn_L0|W120 | hi     |    7088 |  -71.35 | -2.42 | 120 |
| addn_L0|W120 | lo     |    2932 |   31.19 |  0.71 | 120 |
| addn_L0|W15  | hi     |    5971 |  -71.42 | -2.23 |  15 |
| addn_L0|W15  | lo     |    3955 |   87.39 |  2.24 |  15 |
| addn_L0|W30  | hi     |    6362 | -104.89 | -3.13 |  30 |
| addn_L0|W30  | lo     |    3586 |   77.35 |  1.79 |  30 |
| addn_L0|W60  | hi     |    7018 | -106.85 | -3.46 |  60 |
| addn_L0|W60  | lo     |    3201 |  109.68 |  2.53 |  60 |
| addn_L2|W120 | hi     |    7691 |  -79.85 | -2.39 | 120 |
| addn_L2|W120 | lo     |    2626 |   64.98 |  1.48 | 120 |
| addn_L2|W15  | hi     |    6350 |  -94.31 | -2.87 |  15 |
| addn_L2|W15  | lo     |    3632 |  107.76 |  2.55 |  15 |
| addn_L2|W30  | hi     |    6985 |  -53.47 | -1.58 |  30 |
| addn_L2|W30  | lo     |    3281 |   96.17 |  2.09 |  30 |
| addn_L2|W60  | hi     |    7637 |  -93.26 | -2.89 |  60 |
| addn_L2|W60  | lo     |    2801 |  127.05 |  2.9  |  60 |
| addn_L9|W120 | hi     |    7491 |  -39.46 | -1.14 | 120 |
| addn_L9|W120 | lo     |    2762 |   66.78 |  1.55 | 120 |
| addn_L9|W15  | hi     |    6265 |  -75.43 | -2.43 |  15 |
| addn_L9|W15  | lo     |    3679 |  115.15 |  2.51 |  15 |
| addn_L9|W30  | hi     |    6819 |  -66.4  | -2.02 |  30 |
| addn_L9|W30  | lo     |    3392 |  107.74 |  2.37 |  30 |
| addn_L9|W60  | hi     |    7442 |  -73.61 | -2.29 |  60 |
| addn_L9|W60  | lo     |    2977 |  109.64 |  2.45 |  60 |
| addv_L0|W120 | hi     |    7010 |  -58.61 | -1.97 | 120 |
| addv_L0|W120 | lo     |    3005 |   31.81 |  0.71 | 120 |
| addv_L0|W15  | hi     |    5878 |  -74.87 | -2.27 |  15 |
| addv_L0|W15  | lo     |    3995 |   81.52 |  2.1  |  15 |
| addv_L0|W30  | hi     |    6290 | -115.84 | -3.49 |  30 |
| addv_L0|W30  | lo     |    3628 |   57.34 |  1.35 |  30 |
| addv_L0|W60  | hi     |    6968 | -117.76 | -3.93 |  60 |
| addv_L0|W60  | lo     |    3253 |   85.02 |  1.92 |  60 |
| addv_L2|W120 | hi     |    7718 |  -63.09 | -1.8  | 120 |
| addv_L2|W120 | lo     |    2644 |  115.19 |  2.57 | 120 |
| addv_L2|W15  | hi     |    6327 |  -98.14 | -2.86 |  15 |
| addv_L2|W15  | lo     |    3643 |   81.66 |  1.89 |  15 |
| addv_L2|W30  | hi     |    6921 |  -73.82 | -2.15 |  30 |
| addv_L2|W30  | lo     |    3288 |   97.88 |  2.19 |  30 |
| addv_L2|W60  | hi     |    7660 | -113.5  | -3.4  |  60 |
| addv_L2|W60  | lo     |    2815 |  100.34 |  2.18 |  60 |
| addv_L9|W120 | hi     |    7560 |  -67.09 | -1.87 | 120 |
| addv_L9|W120 | lo     |    2735 |   95.12 |  2.19 | 120 |
| addv_L9|W15  | hi     |    6249 |  -80.12 | -2.5  |  15 |
| addv_L9|W15  | lo     |    3658 |  105.98 |  2.38 |  15 |
| addv_L9|W30  | hi     |    6867 |  -75.7  | -2.3  |  30 |
| addv_L9|W30  | lo     |    3352 |   96.64 |  2.1  |  30 |
| addv_L9|W60  | hi     |    7486 |  -91.11 | -2.69 |  60 |
| addv_L9|W60  | lo     |    2941 |  128.47 |  2.77 |  60 |

## 7. Can D7 compute it today
Almost everything that passes is built from order counts, ages and cancels by level (L3: needs the live market-by-order feed and a VPS sidecar; spec in DS3_CONFLUENCE_L3_LIVE_SPEC.md). Exceptions: depth-by-level readings (depth_L2 / depth_L9 / touch_sz: NT8 depth, 10 levels, computable today once the depth-pollution bug is fixed), trade-flow and price-impact readings (NT8 prints and D7 bars: computable, aggressor-order grouping approximate), flicker (L1 quotes). Family column in the tables above gives the data each needs.

## 8. Files
/mnt/l2/l2vast/_confl/cols_cf2/FLOW_PARTA.parquet (sig_id keyed, all 193,628 universe rows, cluster representatives: <id>_v0, _d0, _d1, _d2, _d5, _d30, _d60, _d120), flow_items.csv (id, item, dir, best cell, cells, cluster), /mnt/l2/l2vast/_confl/cf2_flow/flow_passing.csv (every passing item x cell x statistic with years, latency, direction, cluster), flow_scores.parquet / flow_scores_within.parquet (all 162,570 item x tag x cell rows), planted_scores.parquet, null_scores*.parquet. Code: code/th_confl_cf2/mbo_sec3.py, flow_lib.py, flow_pass1.py, flow_score.py, flow_report2.py, flow_export.py.
