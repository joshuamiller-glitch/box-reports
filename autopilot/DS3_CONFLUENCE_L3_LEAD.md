# DS3_CONFLUENCE_L3_LEAD (W-CF2): the L3 lead as gate, size and ladder input, with its expansion battery - FIRST PASS (table level; the exact-engine sets are W-CF3's)
VERDICT (data ends 2026-10-30): arrival_imb60_lo (own-side order adds minus opposite-side adds over 60 s, low versus the previous 20 days) lifts taken trades by $144 per trade at base lots ($252 at x1.75, $144 on the $4.84 basis), weekly-cluster t = 3.39 against a nonsense 99th-percentile bar of 2.69 (beats it); its mirror ctr_mine60_hi is $-116 (t -2.97). With the plain (independent-trade) z test 6% of 200 nonsense conditions with realistic day-to-day persistence pass |z|>2; with weekly-cluster t 4% pass, so cluster-robust t and the nonsense 99th-percentile bar are used here. Nothing is a PASS; the engine decides.

Basis: JN05W2 taken trades (19,798), net $ per trade at base lots with the engine fee $1.18/contract; 'x1.75' = live lot scale (lift x 1.75); '$4.84' = the FEES.md fee basis (pnl484). Statistics are weekly-cluster robust (regression of $ on the yes/no, clusters = calendar weeks, CR1). Nonsense = 200 binary conditions, P(yes)=0.2, a day-level shared component (weight 0.6) so they persist like real day-driven conditions; the bar is the 99th percentile of their |t| in the same cell. Unknown (no MBO value) = keep, no gate. FIRST PASS: no engine, no path effect (a skip frees the book), no cap effects.

## 1. The lead and its mirror, pooled and per cell (book x session)

### c_imb_n5_60_lo

| cond    |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |     t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:--------|--------:|-------:|-------:|------------:|-----------:|------:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| ALL     |    3861 |  15920 |    144 |         252 |        144 |  3.39 |                 2.7  | True                 |          75 |         200 |         114 |         160 |        249 |
| sess:0  |    1666 |   5628 |    178 |         311 |        178 |  2.23 |                 2.47 | False                |         112 |          49 |         254 |         222 |        324 |
| sess:1  |    1279 |   5171 |    100 |         175 |        100 |  1.56 |                 3.65 | False                |          66 |         251 |          21 |          89 |        148 |
| sess:3  |     755 |   4150 |    111 |         194 |        110 |  1.92 |                 2.48 | False                |          33 |         284 |         -63 |         159 |        268 |
| sess:4  |     161 |    975 |     -4 |          -7 |         -4 | -0.04 |                 2.33 | False                |         -90 |         142 |          97 |        -273 |       -207 |
| book:A7 |     207 |    948 |     92 |         161 |         92 |  1.06 |                 2.36 | False                |         nan |         212 |         256 |          -4 |         35 |
| book:H7 |     348 |    699 |     36 |          62 |         35 |  0.26 |                 2.48 | False                |         233 |         -81 |          17 |          63 |        335 |
| book:K7 |    1252 |   5823 |    -11 |         -20 |        -11 | -0.27 |                 2.3  | False                |        -122 |          63 |         -15 |         -15 |        -39 |
| book:M7 |     601 |   3382 |    122 |         214 |        122 |  2.14 |                 2.84 | False                |         352 |          72 |          54 |         137 |        204 |
| book:O7 |     145 |    306 |    266 |         466 |        266 |  2.26 |                 2.91 | False                |         nan |         438 |         130 |         315 |        427 |
| book:P7 |     937 |   3807 |    264 |         462 |        263 |  2    |                 2.24 | False                |          15 |         382 |         253 |         272 |        487 |
| book:U7 |     371 |    959 |    358 |         626 |        358 |  2.02 |                 2.46 | False                |         259 |         366 |         190 |         531 |        484 |
| bs:A7_0 |     207 |    948 |     92 |         161 |         92 |  1.06 |                 2.36 | False                |         nan |         212 |         256 |          -4 |         35 |
| bs:H7_0 |     255 |    444 |     -4 |          -7 |         -4 | -0.02 |                 2.22 | False                |         260 |        -193 |          28 |          89 |        293 |
| bs:H7_3 |      93 |    255 |     73 |         127 |         73 |  0.56 |                 2.48 | False                |         nan |         103 |         -11 |         nan |        nan |
| bs:K7_0 |     538 |   2057 |     27 |          46 |         27 |  0.39 |                 2.52 | False                |         -90 |          57 |         -29 |          91 |         79 |
| bs:K7_1 |     351 |   1430 |    -50 |         -88 |        -50 | -0.58 |                 2.19 | False                |        -170 |         -18 |         -13 |         -55 |       -124 |
| bs:K7_3 |     202 |   1361 |    -75 |        -132 |        -75 | -1.01 |                 2.57 | False                |        -122 |          91 |        -102 |        -232 |       -266 |
| bs:K7_4 |     161 |    975 |     -4 |          -7 |         -4 | -0.04 |                 2.33 | False                |         -90 |         142 |          97 |        -273 |       -207 |
| bs:M7_1 |     406 |   2082 |    154 |         269 |        153 |  2.02 |                 2.86 | False                |         319 |         181 |          68 |         167 |        236 |
| bs:M7_3 |     195 |   1300 |     67 |         118 |         67 |  0.94 |                 2.39 | False                |         373 |         -64 |          31 |          80 |        126 |
| bs:O7_3 |     145 |    306 |    266 |         466 |        266 |  2.26 |                 2.91 | False                |         nan |         438 |         130 |         315 |        427 |
| bs:P7_0 |     460 |   1700 |    296 |         518 |        296 |  1.19 |                 2.12 | False                |         103 |        -175 |         659 |         304 |        604 |
| bs:P7_1 |     357 |   1179 |    168 |         294 |        168 |  1.24 |                 3.18 | False                |          72 |         627 |         -31 |         117 |        234 |
| bs:P7_3 |     120 |    928 |    252 |         440 |        250 |  1.07 |                 2.66 | False                |        -255 |         917 |        -762 |         nan |        nan |
| bs:U7_0 |     206 |    479 |    560 |         980 |        560 |  2.16 |                 2.35 | False                |         413 |         568 |         217 |         861 |        555 |
| bs:U7_1 |     165 |    480 |     92 |         162 |         93 |  0.35 |                 2.69 | False                |          20 |         215 |         103 |          36 |        355 |
### c_ctr_mine_60_hi

| cond    |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |     t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:--------|--------:|-------:|-------:|------------:|-----------:|------:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| ALL     |    3868 |  15920 |   -116 |        -204 |       -118 | -2.97 |                 2.7  | True                 |         -43 |        -158 |        -108 |        -133 |        -97 |
| sess:0  |    1730 |   5564 |   -199 |        -348 |       -201 | -2.28 |                 2.47 | False                |         -94 |        -387 |        -209 |        -137 |       -117 |
| sess:1  |    1517 |   4933 |    -85 |        -149 |        -85 | -1.34 |                 3.65 | False                |         -81 |         -76 |           2 |        -172 |       -122 |
| sess:3  |     501 |   4404 |   -103 |        -180 |       -103 | -1.56 |                 2.48 | False                |          -5 |         -67 |        -181 |        -114 |        274 |
| sess:4  |     120 |   1016 |   -125 |        -219 |       -125 | -1.01 |                 2.33 | False                |          83 |          22 |        -343 |         nan |        nan |
| book:A7 |     226 |    929 |   -261 |        -456 |       -261 | -3.11 |                 2.36 | True                 |         -68 |        -628 |        -117 |        -189 |       -102 |
| book:H7 |     227 |    820 |   -219 |        -384 |       -220 | -1.51 |                 2.48 | False                |         428 |        -325 |        -540 |        -211 |        -84 |
| book:K7 |    1092 |   5983 |     41 |          72 |         41 |  1.06 |                 2.3  | False                |          50 |          42 |          69 |           7 |          1 |
| book:M7 |     775 |   3208 |   -110 |        -192 |       -110 | -2.15 |                 2.84 | False                |        -220 |        -153 |         -44 |         -96 |        -33 |
| book:P7 |    1288 |   3456 |   -188 |        -329 |       -189 | -1.72 |                 2.24 | False                |         -19 |        -325 |        -140 |        -244 |       -244 |
| book:U7 |     240 |   1090 |   -506 |        -886 |       -506 | -2.2  |                 2.46 | False                |        -463 |         149 |        -897 |        -685 |       -522 |
| bs:A7_0 |     226 |    929 |   -261 |        -456 |       -261 | -3.11 |                 2.36 | True                 |         -68 |        -628 |        -117 |        -189 |       -102 |
| bs:H7_0 |     179 |    520 |   -313 |        -548 |       -312 | -1.67 |                 2.22 | False                |         347 |        -464 |        -691 |        -246 |       -143 |
| bs:K7_0 |     500 |   2095 |     95 |         166 |         95 |  1.44 |                 2.52 | False                |         432 |           6 |         146 |          42 |         21 |
| bs:K7_1 |     354 |   1427 |     23 |          40 |         23 |  0.33 |                 2.19 | False                |        -103 |         -55 |         188 |         -61 |         55 |
| bs:K7_3 |     118 |   1445 |     -4 |          -6 |         -4 | -0.04 |                 2.57 | False                |        -141 |         290 |        -149 |         nan |        nan |
| bs:K7_4 |     120 |   1016 |   -125 |        -219 |       -125 | -1.01 |                 2.33 | False                |          83 |          22 |        -343 |         nan |        nan |
| bs:M7_1 |     602 |   1886 |    -99 |        -174 |       -100 | -1.59 |                 2.86 | False                |        -318 |        -104 |         -54 |         -66 |        -41 |
| bs:M7_3 |     173 |   1322 |   -119 |        -208 |       -119 | -1.5  |                 2.39 | False                |        -115 |        -235 |          -3 |         nan |        nan |
| bs:P7_0 |     703 |   1457 |   -443 |        -775 |       -443 | -2.07 |                 2.12 | False                |        -708 |        -871 |        -337 |        -339 |       -443 |
| bs:P7_1 |     443 |   1093 |    -34 |         -59 |        -33 | -0.26 |                 3.18 | False                |         626 |        -116 |          39 |        -227 |       -185 |
| bs:P7_3 |     142 |    906 |    -81 |        -142 |        -81 | -0.44 |                 2.66 | False                |         111 |         169 |        -457 |         nan |        nan |
| bs:U7_0 |     122 |    563 |   -538 |        -941 |       -538 | -1.67 |                 2.35 | False                |         nan |         144 |       -1446 |        -487 |       -163 |
| bs:U7_1 |     118 |    527 |   -470 |        -822 |       -470 | -1.48 |                 2.69 | False                |         nan |         138 |        -372 |        -908 |       -925 |

## 2. Gate and size tables (table level, taken trades, base lots; sum of pnl x multiplier; keeps/multipliers from L3_LEAD_TABLE.parquet)

| rule                                       |   trades_kept |   sum_pnl |   mean_per_kept |   sum_x175 |   max_dd_trade_order |   worst_week |   weeks_negative_pct |
|:-------------------------------------------|--------------:|----------:|----------------:|-----------:|---------------------:|-------------:|---------------------:|
| all trades (reference)                     |         19798 |   2095255 |             106 |    3666695 |               118579 |       -63941 |                 33.5 |
| skip when lead is NO (keep_lead)           |          3874 |    859854 |             222 |    1504745 |                44919 |       -26984 |                 33.5 |
| skip when mirror is HIGH (keep_not_mirror) |         15930 |   2048975 |             129 |    3585706 |               112793 |       -54702 |                 33.5 |
| keep_both                                  |          3306 |    776906 |             235 |    1359586 |                41391 |       -22426 |                 35.6 |
| size x1.5 when lead yes                    |         19798 |   2523293 |             127 |    4415763 |               132320 |       -71805 |                 33.5 |
| size x0.5 when lead no                     |         19798 |   1477554 |              75 |    2585720 |                73030 |       -39834 |                 32.4 |
| x1.5 yes / x0.5 no                         |         19798 |   1905593 |              96 |    3334788 |                87499 |       -50220 |                 31.9 |
| x0.5 when mirror high                      |         19798 |   2072115 |             105 |    3626201 |                99355 |       -59321 |                 32.4 |
| combo (lead x1.5/x0.5 and mirror x0.5)     |         19798 |   1852549 |              94 |    3241961 |                76942 |       -47008 |                 34   |

Per book x session (same rules): file /mnt/l2/l2vast/_confl/cols_cf2/L3_LEAD_TABLE.parquet; columns sig_id, book7, sess, side, ld, sig_ts, taken, lots_base, pnl, pnl484, lead_value, lead_lo, lead_hi, mirror_value, mirror_hi, keep_lead, keep_not_mirror, keep_both, size_up15_if_lead, size_dn05_if_not_lead, size_up15_dn05, size_dn05_if_mirror, size_combo, ladder_score (-1/0/+1), lead_lo_lag1/2/5. W-CF3: join on sig_id; every universe row (taken and skipped) has the columns so skip-gates apply to replacement signals too.

Per book x session table-level $ (base lots):

| book7   |   sess |    n |   kept |   sum_all |   sum_kept |   x15_x05 |
|:--------|-------:|-----:|-------:|----------:|-----------:|----------:|
| A7      |      0 | 1156 |    208 |    132929 |      40397 |    106262 |
| H7      |      0 |  700 |    256 |    151044 |      52954 |    129642 |
| H7      |      3 |  348 |     93 |     14775 |       8899 |     16286 |
| K7      |      0 | 2596 |    539 |    230880 |      60143 |    174984 |
| K7      |      1 | 1781 |    351 |     63317 |      -1641 |     30017 |
| K7      |      3 | 1565 |    204 |     15808 |     -12784 |     -3957 |
| K7      |      4 | 1136 |    161 |     70357 |       9441 |     44619 |
| M7      |      1 | 2489 |    407 |     -7466 |      50321 |     46972 |
| M7      |      3 | 1496 |    196 |     59838 |      18468 |     48802 |
| O7      |      3 |  452 |    146 |     79582 |      51377 |     91484 |
| P7      |      0 | 2161 |    461 |    915893 |     308809 |    762559 |
| P7      |      1 | 1537 |    358 |     52869 |      56068 |     83921 |
| P7      |      3 | 1050 |    122 |    -35242 |      20457 |      4111 |
| U7      |      0 |  686 |    207 |    264266 |     163514 |    293255 |
| U7      |      1 |  645 |    165 |     86403 |      33433 |     76635 |

## 3. Expansion battery (pooled, taken trades): window x distance x count/size, weekly-cluster t, nonsense p99 bar

| cond            |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:----------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| c_imb_v5_30_lo  |    3735 |  16050 |    181 |         316 |        180 | 3.97 |                  2.7 | True                 |         126 |         349 |         138 |         124 |        159 |
| c_imb_n5_30_lo  |    3782 |  16000 |    165 |         289 |        164 | 3.8  |                  2.7 | True                 |         104 |         319 |         108 |         134 |        171 |
| c_imb_n5_60_lo  |    3861 |  15920 |    144 |         252 |        144 | 3.39 |                  2.7 | True                 |          75 |         200 |         114 |         160 |        249 |
| c_imb_v5_60_lo  |    3902 |  15880 |    136 |         239 |        136 | 3.24 |                  2.7 | True                 |          27 |         148 |         125 |         183 |        281 |
| c_imb_n5_15_lo  |    3675 |  16110 |    128 |         225 |        127 | 2.77 |                  2.7 | True                 |        -113 |         402 |          96 |          65 |        165 |
| c_imb_v5_120_lo |    3533 |  16250 |    116 |         204 |        116 | 2.72 |                  2.7 | True                 |           8 |         242 |           6 |         181 |        273 |
| c_imb_v5_15_lo  |    3700 |  16080 |    126 |         221 |        125 | 2.7  |                  2.7 | True                 |        -103 |         362 |          98 |          79 |        162 |
| c_imb_v5_300_lo |    3390 |  16400 |    118 |         206 |        117 | 2.63 |                  2.7 | False                |         177 |         124 |          46 |         153 |        258 |
| c_imb_n5_120_lo |    3519 |  16270 |    102 |         179 |        102 | 2.19 |                  2.7 | False                |          73 |         221 |          -9 |         134 |        258 |
| c_imb_n5_300_lo |    3396 |  16390 |    104 |         182 |        103 | 2.16 |                  2.7 | False                |         314 |          71 |         -25 |         157 |        264 |

7 of 10 lo-versions beat the nonsense p99 bar pooled. These variants are strongly correlated (the 60 s count and size versions at 2/5/10/20 ticks correlate 0.94-0.97 in the entry sample), so they are one finding seen eight times, not eight findings; windows 15 s and 300 s are the only really different readings (correlation 0.5).

## 4. Latency: the value computed 1 / 2 / 5 s late (the whole reading, including its 20-day reference, shifted)

| cond                |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:--------------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| c_imb_n5_60_lo      |    3861 |  15920 |    144 |         252 |        144 | 3.39 |                  2.7 | True                 |          75 |         200 |         114 |         160 |        249 |
| c_imb_n5_60_lag1_lo |    3874 |  15910 |    147 |         258 |        147 | 3.46 |                  2.7 | True                 |          98 |         196 |         120 |         157 |        277 |
| c_imb_n5_60_lag2_lo |    3875 |  15910 |    144 |         252 |        143 | 3.38 |                  2.7 | True                 |          33 |         156 |         144 |         180 |        276 |
| c_imb_n5_60_lag5_lo |    3893 |  15890 |    158 |         277 |        158 | 3.81 |                  2.7 | True                 |          39 |         148 |         156 |         219 |        276 |

## 5. At level clusters and levels (strata from W-CF1 category B)

| cond                    |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| lvl:behind<=3pts        |     873 |   3435 |     94 |         165 |         94 | 1.02 |                 2.51 | False                |          -1 |         222 |         106 |          10 |        295 |
| lvl:ahead<=10pts        |    2495 |   9842 |    130 |         228 |        130 | 2.44 |                 2.57 | False                |          88 |         253 |          86 |          84 |        200 |
| lvl:cluster_behind10    |    2492 |  10250 |    167 |         293 |        167 | 3.24 |                 2.48 | True                 |          87 |         154 |         135 |         270 |        404 |
| lvl:cluster_ahead10     |    2133 |   8898 |    196 |         343 |        195 | 3.07 |                 2.16 | True                 |         -21 |         228 |         246 |         210 |        316 |
| lvl:behind<=5&ahead>=20 |     210 |    942 |     47 |          83 |         47 | 0.28 |                 2.58 | False                |         438 |         156 |         275 |        -255 |       -182 |

## 6. The same reading while in a trade (hold/cut and take/hold, FIRST PASS: readings at entry+5/15/30 min for trades still open; outcome = final net $ and Target rate; survivors only)

|   offset_min | reading        |   n_alive |   n_yes |   n_no |   lift_final_pnl |      t |   mean_yes |   mean_no |   target_rate_lift |   t_target |
|-------------:|:---------------|----------:|--------:|-------:|-----------------:|-------:|-----------:|----------:|-------------------:|-----------:|
|            5 | imb_n5_60_lo   |     18161 |    5937 |  12110 |           -89.82 | -2.286 |     100.7  |     190.5 |             -0.026 |     -3.14  |
|            5 | ctr_mine_60_hi |     18161 |    3887 |  14160 |          -100.7  | -2.433 |      81.91 |     182.7 |             -0.044 |     -4.341 |
|           15 | imb_n5_60_lo   |     15648 |    5419 |  10150 |          -152.7  | -3.822 |     115.8  |     268.4 |             -0.029 |     -3.372 |
|           15 | ctr_mine_60_hi |     15648 |    3639 |  11930 |          -131.9  | -2.931 |     114.3  |     246.1 |             -0.039 |     -3.835 |
|           30 | imb_n5_60_lo   |     12963 |    4639 |   8274 |           -97.33 | -2.098 |     189.4  |     286.8 |             -0.023 |     -2.437 |
|           30 | ctr_mine_60_hi |     12963 |    3005 |   9908 |           -61.35 | -1.283 |     204.7  |     266.1 |             -0.025 |     -2.298 |

Reading: while in a trade the arrival-imbalance reading does NOT carry the entry sign (lift -$90 to -$153 at +5/+15/+30 min, t about -2 to -3.8; 33% of open trades read yes instead of 20%, so the in-trade value is confounded by the price path since entry: own-side adds fall when price moves with the trade). It is therefore not a hold/take signal as it stands. The mirror reading (high own-side cancel-to-trade) keeps its sign in trade (-$61 to -$132 final, Target rate -2.5 to -4.4 points, t -2.3 to -4.3 at +5 and +15 min): a candidate cut/hold input for W-CF3 step 7. FIRST PASS: survivors only, no path control.

## 7. Nonsense pass rates beside every stage

| stage   |   nonsense_pass_abs_t_gt2_pct |   nonsense_p99_abs_t |   real_L3_conditions |   real_pass_abs_t_gt2_pct |   real_beat_p99_pct |
|:--------|------------------------------:|---------------------:|---------------------:|--------------------------:|--------------------:|
| ALL     |                           3.5 |                 2.69 |                   30 |                      53.3 |                36.7 |
| sess:0  |                           5.5 |                 2.47 |                   30 |                      26.7 |                 6.7 |
| sess:1  |                           5   |                 3.65 |                   30 |                      20   |                 0   |
| sess:3  |                           5.5 |                 2.48 |                   30 |                      10   |                 3.3 |
| sess:4  |                           4.5 |                 2.33 |                   19 |                       0   |                 0   |

## 8. ES and RTY order arrival as confirmation: NOT built as order data
ES and RTY MBO is quote-only (ES MBO 2023-04..2026-04 $844.71), so no ES/RTY order-by-order arrival exists on the box. The ES/RTY mbp-10 raw files (raw/ES, raw/RTY) are on disk but not decoded to per-second tables, and the NQ L2 depth-added proxy of this very lead failed to reproduce it (lift +$12 versus +$144, DS3_CONFLUENCE_L3_LIVE_SPEC.md), so an ES/RTY L2 proxy would test something else. Intermarket confirmation by trades/returns (ES, RTY, YM z, NQ lead-lag) is in cols_cf2/I.parquet and joins with the lead through the normal combination step.
