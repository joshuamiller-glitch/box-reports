# DS3_CONFLUENCE_L3_LEAD (W-CF2): the L3 lead as gate, size and ladder input, with its expansion battery - FIRST PASS (table level; the exact-engine sets are W-CF3's)
VERDICT (data ends 2026-11-13): arrival_imb60_lo (own-side order adds minus opposite-side adds over 60 s, low versus the previous 20 days) lifts taken trades by $141 per trade at base lots ($247 at x1.75, $140 on the $4.84 basis), weekly-cluster t = 3.34 against a nonsense 99th-percentile bar of 2.49 (beats it); its mirror ctr_mine60_hi is $-119 (t -3.05). With the plain (independent-trade) z test 8% of 200 nonsense conditions with realistic day-to-day persistence pass |z|>2; with weekly-cluster t 6% pass, so cluster-robust t and the nonsense 99th-percentile bar are used here. Nothing is a PASS; the engine decides.

Basis: JN05W2 taken trades (19,798), net $ per trade at base lots with the engine fee $1.18/contract; 'x1.75' = live lot scale (lift x 1.75); '$4.84' = the FEES.md fee basis (pnl484). Statistics are weekly-cluster robust (regression of $ on the yes/no, clusters = calendar weeks, CR1). Nonsense = 200 binary conditions, P(yes)=0.2, a day-level shared component (weight 0.6) so they persist like real day-driven conditions; the bar is the 99th percentile of their |t| in the same cell. Unknown (no MBO value) = keep, no gate. FIRST PASS: no engine, no path effect (a skip frees the book), no cap effects.

## 1. The lead and its mirror, pooled and per cell (book x session)

### c_imb_n5_60_lo

| cond      |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |     t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:----------|--------:|-------:|-------:|------------:|-----------:|------:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| ALL       |    3906 |  16060 |    141 |         247 |        140 |  3.34 |                 2.49 | True                 |          75 |         200 |         114 |         150 |        230 |
| sess:0.0  |    1698 |   5734 |    181 |         316 |        181 |  2.3  |                 2.35 | False                |         112 |          49 |         254 |         227 |        324 |
| sess:1.0  |    1292 |   5194 |     89 |         156 |         89 |  1.4  |                 2.82 | False                |          66 |         251 |          21 |          60 |        100 |
| sess:3.0  |     755 |   4155 |    109 |         190 |        108 |  1.88 |                 2.66 | False                |          33 |         284 |         -63 |         150 |        252 |
| sess:4.0  |     161 |    975 |     -4 |          -7 |         -4 | -0.04 |                 2.43 | False                |         -90 |         142 |          97 |        -273 |       -207 |
| book:A7   |     211 |    966 |    105 |         184 |        105 |  1.23 |                 2.28 | False                |         nan |         212 |         256 |          30 |         79 |
| book:H7   |     350 |    706 |     15 |          27 |         15 |  0.11 |                 2.53 | False                |         233 |         -81 |          17 |         -16 |        215 |
| book:K7   |    1273 |   5869 |     -8 |         -15 |         -8 | -0.2  |                 2.43 | False                |        -122 |          63 |         -15 |          -7 |        -25 |
| book:M7   |     606 |   3400 |    112 |         196 |        112 |  1.96 |                 2.7  | False                |         352 |          72 |          54 |         106 |        149 |
| book:O7   |     145 |    306 |    266 |         466 |        266 |  2.26 |                 2.32 | False                |         nan |         438 |         130 |         315 |        427 |
| book:P7   |     948 |   3844 |    262 |         458 |        261 |  2    |                 2.79 | False                |          15 |         382 |         253 |         267 |        472 |
| book:U7   |     373 |    967 |    354 |         619 |        354 |  2    |                 2.58 | False                |         259 |         366 |         190 |         519 |        461 |
| bs:A7_0.0 |     211 |    966 |    105 |         184 |        105 |  1.23 |                 2.28 | False                |         nan |         212 |         256 |          30 |         79 |
| bs:H7_0.0 |     257 |    451 |    -33 |         -57 |        -33 | -0.17 |                 2.65 | False                |         260 |        -193 |          28 |         -11 |        151 |
| bs:H7_3.0 |      93 |    255 |     73 |         127 |         73 |  0.56 |                 2.83 | False                |         nan |         103 |         -11 |         nan |        nan |
| bs:K7_0.0 |     555 |   2095 |     33 |          57 |         33 |  0.49 |                 2.34 | False                |         -90 |          57 |         -29 |         100 |         96 |
| bs:K7_1.0 |     355 |   1438 |    -51 |         -90 |        -51 | -0.6  |                 2.54 | False                |        -170 |         -18 |         -13 |         -59 |       -126 |
| bs:K7_3.0 |     202 |   1361 |    -75 |        -132 |        -75 | -1.01 |                 2.82 | False                |        -122 |          91 |        -102 |        -232 |       -266 |
| bs:K7_4.0 |     161 |    975 |     -4 |          -7 |         -4 | -0.04 |                 2.43 | False                |         -90 |         142 |          97 |        -273 |       -207 |
| bs:M7_1.0 |     410 |   2093 |    144 |         252 |        144 |  1.9  |                 2.44 | False                |         319 |         181 |          68 |         141 |        191 |
| bs:M7_3.0 |     195 |   1304 |     64 |         111 |         64 |  0.89 |                 2.82 | False                |         373 |         -64 |          31 |          65 |        103 |
| bs:O7_3.0 |     145 |    306 |    266 |         466 |        266 |  2.26 |                 2.32 | False                |         nan |         438 |         130 |         315 |        427 |
| bs:P7_0.0 |     467 |   1733 |    310 |         542 |        310 |  1.27 |                 2.54 | False                |         103 |        -175 |         659 |         336 |        639 |
| bs:P7_1.0 |     361 |   1182 |    152 |         265 |        152 |  1.12 |                 2.81 | False                |          72 |         627 |         -31 |          77 |        171 |
| bs:P7_3.0 |     120 |    929 |    248 |         434 |        246 |  1.05 |                 2.72 | False                |        -255 |         917 |        -762 |         nan |        nan |
| bs:U7_0.0 |     207 |    486 |    575 |        1006 |        575 |  2.23 |                 2.23 | True                 |         413 |         568 |         217 |         897 |        616 |
| bs:U7_1.0 |     166 |    481 |     70 |         122 |         70 |  0.27 |                 2.6  | False                |          20 |         215 |         103 |         -41 |        207 |
### c_ctr_mine_60_hi

| cond      |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |     t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:----------|--------:|-------:|-------:|------------:|-----------:|------:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| ALL       |    3927 |  16040 |   -119 |        -208 |       -120 | -3.05 |                 2.49 | True                 |         -43 |        -158 |        -108 |        -139 |       -107 |
| sess:0.0  |    1782 |   5650 |   -201 |        -351 |       -203 | -2.35 |                 2.35 | True                 |         -94 |        -387 |        -209 |        -143 |       -127 |
| sess:1.0  |    1524 |   4962 |    -87 |        -152 |        -87 | -1.36 |                 2.82 | False                |         -81 |         -76 |           2 |        -173 |       -124 |
| sess:3.0  |     501 |   4409 |   -105 |        -183 |       -105 | -1.59 |                 2.66 | False                |          -5 |         -67 |        -181 |        -122 |        260 |
| sess:4.0  |     120 |   1016 |   -125 |        -219 |       -125 | -1.01 |                 2.43 | False                |          83 |          22 |        -343 |         nan |        nan |
| book:A7   |     234 |    943 |   -258 |        -451 |       -258 | -3.16 |                 2.28 | True                 |         -68 |        -628 |        -117 |        -185 |       -104 |
| book:H7   |     233 |    823 |   -243 |        -425 |       -243 | -1.69 |                 2.53 | False                |         428 |        -325 |        -540 |        -300 |       -247 |
| book:K7   |    1108 |   6034 |     39 |          67 |         38 |  1    |                 2.43 | False                |          50 |          42 |          69 |           1 |         -7 |
| book:M7   |     779 |   3227 |   -112 |        -197 |       -113 | -2.21 |                 2.7  | False                |        -220 |        -153 |         -44 |        -104 |        -47 |
| book:P7   |    1310 |   3482 |   -189 |        -331 |       -190 | -1.75 |                 2.79 | False                |         -19 |        -325 |        -140 |        -242 |       -240 |
| book:U7   |     243 |   1097 |   -493 |        -863 |       -493 | -2.17 |                 2.58 | False                |        -463 |         149 |        -897 |        -639 |       -461 |
| bs:A7_0.0 |     234 |    943 |   -258 |        -451 |       -258 | -3.16 |                 2.28 | True                 |         -68 |        -628 |        -117 |        -185 |       -104 |
| bs:H7_0.0 |     185 |    523 |   -344 |        -602 |       -343 | -1.86 |                 2.65 | False                |         347 |        -464 |        -691 |        -349 |       -324 |
| bs:K7_0.0 |     513 |   2137 |     89 |         155 |         89 |  1.36 |                 2.34 | False                |         432 |           6 |         146 |          31 |          7 |
| bs:K7_1.0 |     357 |   1436 |     22 |          38 |         22 |  0.31 |                 2.54 | False                |        -103 |         -55 |         188 |         -61 |         53 |
| bs:K7_3.0 |     118 |   1445 |     -4 |          -6 |         -4 | -0.04 |                 2.82 | False                |        -141 |         290 |        -149 |         nan |        nan |
| bs:K7_4.0 |     120 |   1016 |   -125 |        -219 |       -125 | -1.01 |                 2.43 | False                |          83 |          22 |        -343 |         nan |        nan |
| bs:M7_1.0 |     604 |   1899 |    -97 |        -170 |        -97 | -1.56 |                 2.44 | False                |        -318 |        -104 |         -54 |         -60 |        -32 |
| bs:M7_3.0 |     173 |   1326 |   -122 |        -214 |       -122 | -1.54 |                 2.82 | False                |        -115 |        -235 |          -3 |         nan |        nan |
| bs:P7_0.0 |     724 |   1476 |   -438 |        -767 |       -438 | -2.09 |                 2.54 | False                |        -708 |        -871 |        -337 |        -328 |       -418 |
| bs:P7_1.0 |     444 |   1099 |    -33 |         -59 |        -33 | -0.25 |                 2.81 | False                |         626 |        -116 |          39 |        -221 |       -178 |
| bs:P7_3.0 |     142 |    907 |    -85 |        -149 |        -85 | -0.46 |                 2.72 | False                |         111 |         169 |        -457 |         nan |        nan |
| bs:U7_0.0 |     124 |    569 |   -488 |        -853 |       -488 | -1.52 |                 2.23 | False                |         nan |         144 |       -1446 |        -350 |         26 |
| bs:U7_1.0 |     119 |    528 |   -495 |        -866 |       -495 | -1.56 |                 2.6  | False                |         nan |         138 |        -372 |        -979 |      -1041 |

## 2. Gate and size tables (table level, taken trades, base lots; sum of pnl x multiplier; keeps/multipliers from L3_LEAD_TABLE.parquet)

| rule                                       |   trades_kept |   sum_pnl |   mean_per_kept |   sum_x175 |   max_dd_trade_order |   worst_week |   weeks_negative_pct |
|:-------------------------------------------|--------------:|----------:|----------------:|-----------:|---------------------:|-------------:|---------------------:|
| all trades (reference)                     |         20138 |   2114481 |             105 |    3700342 |               118579 |       -63941 |                 33.7 |
| skip when lead is NO (keep_lead)           |          4080 |    897328 |             220 |    1570323 |                44919 |       -26984 |                 33.7 |
| skip when mirror is HIGH (keep_not_mirror) |         16211 |   2083794 |             129 |    3646640 |               112793 |       -54702 |                 33.2 |
| keep_both                                  |          3496 |    819141 |             234 |    1433496 |                41391 |       -22426 |                 35.8 |
| size x1.5 when lead yes                    |         20138 |   2537924 |             126 |    4441367 |               132320 |       -71805 |                 33.7 |
| size x0.5 when lead no                     |         20138 |   1505904 |              75 |    2635332 |                73030 |       -39834 |                 32.6 |
| x1.5 yes / x0.5 no                         |         20138 |   1929347 |              96 |    3376358 |                87499 |       -50220 |                 32.1 |
| x0.5 when mirror high                      |         20138 |   2099138 |             104 |    3673491 |                99355 |       -59321 |                 32.1 |
| combo (lead x1.5/x0.5 and mirror x0.5)     |         20138 |   1882582 |              93 |    3294519 |                76942 |       -47008 |                 34.2 |

Per book x session (same rules): file /mnt/l2/l2vast/_confl/cols_cf2/L3_LEAD_TABLE.parquet; columns sig_id, book7, sess, side, ld, sig_ts, taken, lots_base, pnl, pnl484, lead_value, lead_lo, lead_hi, mirror_value, mirror_hi, keep_lead, keep_not_mirror, keep_both, size_up15_if_lead, size_dn05_if_not_lead, size_up15_dn05, size_dn05_if_mirror, size_combo, ladder_score (-1/0/+1), lead_lo_lag1/2/5. W-CF3: join on sig_id; every universe row (taken and skipped) has the columns so skip-gates apply to replacement signals too.

Per book x session table-level $ (base lots):

| book7   |   sess |    n |   kept |   sum_all |   sum_kept |   x15_x05 |
|:--------|-------:|-----:|-------:|----------:|-----------:|----------:|
| A7      |      0 | 1197 |    231 |    138147 |      47288 |    113756 |
| H7      |      0 |  710 |    259 |    152843 |      47747 |    126034 |
| H7      |      3 |  348 |     93 |     14775 |       8899 |     16286 |
| K7      |      0 | 2686 |    591 |    256313 |      77948 |    199845 |
| K7      |      1 | 1808 |    370 |     55880 |      -3566 |     24402 |
| K7      |      3 | 1567 |    206 |     18205 |     -10387 |     -1559 |
| K7      |      4 | 1136 |    161 |     70357 |       9441 |     44619 |
| M7      |      0 |    4 |      1 |     -2170 |      -1309 |     -2394 |
| M7      |      1 | 2531 |    438 |     -8716 |      49755 |     44305 |
| M7      |      3 | 1503 |    199 |     63941 |      17776 |     50507 |
| O7      |      3 |  455 |    149 |     82543 |      54337 |     94444 |
| P7      |      0 | 2232 |    499 |    912724 |     329027 |    771791 |
| P7      |      1 | 1560 |    378 |     41918 |      47037 |     71042 |
| P7      |      3 | 1053 |    124 |    -32761 |      19336 |      4791 |
| U7      |      0 |  696 |    210 |    260842 |     169723 |    294160 |
| U7      |      1 |  652 |    171 |     89639 |      34276 |     77317 |

## 3. Expansion battery (pooled, taken trades): window x distance x count/size, weekly-cluster t, nonsense p99 bar

| cond             |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:-----------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| c_imb_v5_30_lo   |    3778 |  16190 |    173 |         303 |        172 | 3.8  |                 2.49 | True                 |         126 |         349 |         138 |         103 |        126 |
| c_imb_n5_30_lo   |    3825 |  16140 |    158 |         276 |        157 | 3.64 |                 2.49 | True                 |         104 |         319 |         108 |         113 |        137 |
| c_imb_n10_30_lo  |    3781 |  16180 |    164 |         286 |        162 | 3.57 |                 2.49 | True                 |          91 |         420 |          26 |         138 |        131 |
| c_imb_v10_30_lo  |    3792 |  16170 |    162 |         284 |        161 | 3.55 |                 2.49 | True                 |          85 |         402 |          49 |         131 |        127 |
| c_imb_v2_30_lo   |    3854 |  16110 |    143 |         251 |        142 | 3.35 |                 2.49 | True                 |          83 |         374 |          89 |          59 |         75 |
| c_imb_n5_60_lo   |    3906 |  16060 |    141 |         247 |        140 | 3.34 |                 2.49 | True                 |          75 |         200 |         114 |         150 |        230 |
| c_imb_n2_30_lo   |    3865 |  16100 |    140 |         245 |        139 | 3.17 |                 2.49 | True                 |          31 |         389 |          71 |          73 |         99 |
| c_imb_v5_60_lo   |    3947 |  16020 |    131 |         230 |        131 | 3.12 |                 2.49 | True                 |          27 |         148 |         125 |         166 |        251 |
| c_imb_v2_120_lo  |    3577 |  16390 |    137 |         239 |        136 | 3.11 |                 2.49 | True                 |          55 |         246 |          60 |         167 |        238 |
| c_imb_v2_15_lo   |    3784 |  16180 |    126 |         220 |        124 | 2.97 |                 2.49 | True                 |         -26 |         325 |         113 |          61 |        128 |
| c_imb_v10_15_lo  |    3726 |  16240 |    149 |         260 |        147 | 2.97 |                 2.49 | True                 |         -51 |         399 |         124 |          77 |        150 |
| c_imb_v2_60_lo   |    3917 |  16050 |    122 |         214 |        122 | 2.96 |                 2.49 | True                 |           2 |         112 |         138 |         164 |        224 |
| c_imb_n20_15_lo  |    3731 |  16230 |    136 |         237 |        134 | 2.95 |                 2.49 | True                 |         -31 |         416 |          68 |          69 |        132 |
| c_imb_n2_60_lo   |    3928 |  16040 |    126 |         221 |        126 | 2.93 |                 2.49 | True                 |          69 |         144 |         128 |         137 |        209 |
| c_imb_n2_15_lo   |    3782 |  16180 |    126 |         220 |        124 | 2.91 |                 2.49 | True                 |         -25 |         409 |          71 |          43 |        130 |
| c_imb_n10_15_lo  |    3736 |  16230 |    139 |         243 |        137 | 2.91 |                 2.49 | True                 |         -43 |         385 |          99 |          76 |        125 |
| c_imb_v20_15_lo  |    3750 |  16210 |    136 |         238 |        135 | 2.88 |                 2.49 | True                 |         -65 |         395 |          99 |          67 |        137 |
| c_imb_v20_30_lo  |    3829 |  16140 |    122 |         213 |        121 | 2.83 |                 2.49 | True                 |          24 |         309 |          15 |         126 |        120 |
| c_imb_v5_120_lo  |    3570 |  16390 |    117 |         204 |        116 | 2.75 |                 2.49 | True                 |           8 |         242 |           6 |         180 |        267 |
| c_imb_v5_300_lo  |    3426 |  16540 |    121 |         212 |        120 | 2.72 |                 2.49 | True                 |         177 |         124 |          46 |         161 |        264 |
| c_imb_n20_30_lo  |    3786 |  16180 |    123 |         216 |        122 | 2.71 |                 2.49 | True                 |         145 |         354 |         -37 |         101 |         76 |
| c_imb_v10_60_lo  |    3938 |  16030 |    121 |         212 |        121 | 2.68 |                 2.49 | True                 |          -2 |          83 |          77 |         235 |        327 |
| c_imb_n5_15_lo   |    3708 |  16260 |    124 |         217 |        122 | 2.68 |                 2.49 | True                 |        -113 |         402 |          96 |          54 |        145 |
| c_imb_v5_15_lo   |    3733 |  16230 |    122 |         213 |        121 | 2.61 |                 2.49 | True                 |        -103 |         362 |          98 |          68 |        142 |
| c_imb_n10_120_lo |    3581 |  16380 |    116 |         203 |        115 | 2.56 |                 2.49 | True                 |           9 |         184 |         -28 |         244 |        311 |
| c_imb_n20_60_lo  |    3948 |  16020 |    111 |         194 |        110 | 2.55 |                 2.49 | True                 |          84 |         125 |          10 |         198 |        245 |
| c_imb_n10_60_lo  |    3928 |  16040 |    107 |         188 |        107 | 2.5  |                 2.49 | True                 |          30 |         136 |          27 |         187 |        255 |
| c_imb_v10_120_lo |    3601 |  16360 |    112 |         195 |        111 | 2.45 |                 2.49 | False                |         -44 |         171 |           4 |         232 |        304 |
| c_imb_n2_120_lo  |    3561 |  16400 |    106 |         186 |        106 | 2.32 |                 2.49 | False                |          14 |         256 |          -2 |         140 |        226 |
| c_imb_n5_120_lo  |    3555 |  16410 |    103 |         180 |        102 | 2.22 |                 2.49 | False                |          73 |         221 |          -9 |         135 |        255 |
| c_imb_n5_300_lo  |    3434 |  16530 |    106 |         185 |        104 | 2.22 |                 2.49 | False                |         314 |          71 |         -25 |         160 |        264 |
| c_imb_n10_300_lo |    3495 |  16470 |     99 |         174 |         98 | 2.13 |                 2.49 | False                |         178 |         134 |           2 |         127 |        212 |
| c_imb_v20_120_lo |    3657 |  16310 |     90 |         157 |         89 | 2.02 |                 2.49 | False                |         -21 |         141 |         -18 |         199 |        256 |
| c_imb_v20_60_lo  |    3925 |  16040 |     85 |         149 |         85 | 1.92 |                 2.49 | False                |         -31 |          54 |           7 |         223 |        298 |
| c_imb_v10_300_lo |    3443 |  16520 |     81 |         142 |         80 | 1.73 |                 2.49 | False                |         122 |         106 |          28 |          92 |        178 |
| c_imb_n20_120_lo |    3580 |  16380 |     74 |         129 |         73 | 1.7  |                 2.49 | False                |         -13 |          49 |          35 |         165 |        240 |
| c_imb_v2_300_lo  |    3437 |  16530 |     68 |         120 |         67 | 1.39 |                 2.49 | False                |         166 |          65 |         -18 |         104 |        151 |
| c_imb_n2_300_lo  |    3436 |  16530 |     68 |         119 |         67 | 1.35 |                 2.49 | False                |         239 |          27 |         -18 |         101 |        154 |
| c_imb_v20_300_lo |    3496 |  16470 |     45 |          78 |         44 | 1    |                 2.49 | False                |          14 |          77 |         -50 |         118 |        167 |
| c_imb_n20_300_lo |    3508 |  16460 |     41 |          72 |         40 | 0.9  |                 2.49 | False                |         117 |          43 |         -82 |         114 |        186 |

27 of 40 lo-versions beat the nonsense p99 bar pooled. These variants are strongly correlated (the 60 s count and size versions at 2/5/10/20 ticks correlate 0.94-0.97 in the entry sample), so they are one finding seen eight times, not eight findings; windows 15 s and 300 s are the only really different readings (correlation 0.5).

## 4. Latency: the value computed 1 / 2 / 5 s late (the whole reading, including its 20-day reference, shifted)

| cond                |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:--------------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| c_imb_n5_60_lo      |    3906 |  16060 |    141 |         247 |        140 | 3.34 |                 2.49 | True                 |          75 |         200 |         114 |         150 |        230 |
| c_imb_n5_60_lag1_lo |    3918 |  16050 |    145 |         254 |        144 | 3.44 |                 2.49 | True                 |          98 |         196 |         120 |         150 |        260 |
| c_imb_n5_60_lag2_lo |    3920 |  16040 |    142 |         248 |        141 | 3.36 |                 2.49 | True                 |          33 |         156 |         144 |         173 |        260 |
| c_imb_n5_60_lag5_lo |    3938 |  16030 |    153 |         268 |        153 | 3.7  |                 2.49 | True                 |          39 |         148 |         156 |         202 |        247 |

## 5. At level clusters and levels (strata from W-CF1 category B)

| cond                    |   n_yes |   n_no |   lift |   lift_x175 |   lift_484 |    t |   nonsense_abs_t_p99 | beats_p99_nonsense   |   lift_2023 |   lift_2024 |   lift_2025 |   lift_2026 |   lift_L6M |
|:------------------------|--------:|-------:|-------:|------------:|-----------:|-----:|---------------------:|:---------------------|------------:|------------:|------------:|------------:|-----------:|
| lvl:behind<=3pts        |     873 |   3446 |     98 |         171 |         97 | 1.05 |                 2.82 | False                |          -1 |         222 |         106 |          26 |        318 |
| lvl:ahead<=10pts        |    2508 |   9893 |    132 |         230 |        131 | 2.48 |                 2.63 | False                |          88 |         253 |          86 |          90 |        206 |
| lvl:cluster_behind10    |    2508 |  10280 |    168 |         294 |        168 | 3.27 |                 2.31 | True                 |          87 |         154 |         135 |         270 |        400 |
| lvl:cluster_ahead10     |    2166 |   9013 |    191 |         334 |        190 | 3.03 |                 2.8  | True                 |         -21 |         228 |         246 |         198 |        291 |
| lvl:behind<=5&ahead>=20 |     210 |    952 |     56 |          98 |         56 | 0.33 |                 3.05 | False                |         438 |         156 |         275 |        -239 |       -158 |

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

| stage    |   nonsense_pass_abs_t_gt2_pct |   nonsense_p99_abs_t |   real_L3_conditions |   real_pass_abs_t_gt2_pct |   real_beat_p99_pct |
|:---------|------------------------------:|---------------------:|---------------------:|--------------------------:|--------------------:|
| ALL      |                           6   |                 2.49 |                   90 |                      44.4 |                35.6 |
| sess:0.0 |                           2.5 |                 2.34 |                   90 |                      18.9 |                 8.9 |
| sess:1.0 |                           5   |                 2.82 |                   90 |                      15.6 |                 3.3 |
| sess:3.0 |                           7   |                 2.66 |                   90 |                      13.3 |                 2.2 |
| sess:4.0 |                           4.5 |                 2.43 |                   55 |                       5.5 |                 0   |

## 8. ES and RTY order arrival as confirmation: NOT TESTABLE
No decoded order-by-order source exists for ES or RTY: ES MBO is quote-only (2023-04..2026-04 $844.71, not bought) and RTY MBO is not on the box; the ES/RTY mbp-10 raw files (raw/ES, raw/RTY) are depth by level, not orders, and are not decoded to per-second tables. A depth-added proxy cannot stand in: the same proxy on NQ (depth added over 60 s) did not reproduce the NQ lead (lift +$12 versus +$141; years -116/+86/+10/+9). Intermarket confirmation by returns and lead-lag (ES, RTY, YM z; NQ vs ES) is in cols_cf2/I.parquet and joins with the lead in the normal combination step.

## 9. The in-trade mirror (high own-side cancel-to-trade) as a cut/hold trigger, with a matched random trigger (FIRST PASS; table cols_cf2/L3_MIRROR_CUT_TABLE.parquet)
For each taken trade still open at entry+offset: mirror_yes = value above the 80th percentile of the previous 20 days of entry values; random_yes = a random trigger with the same share inside book x session x month x offset. Outcome = the trade's final net $ (base lots) and its Target rate; 'unreal<0' = already losing at that time. Weekly-cluster t; the placebo rows are the bar.

|   offset_min | bucket   |   lift_mirror_yes |   lift_random_yes |   n_yes_mirror_yes |   n_yes_random_yes |   t_mirror_yes |   t_random_yes |
|-------------:|:---------|------------------:|------------------:|-------------------:|-------------------:|---------------:|---------------:|
|            2 | all      |            -30.83 |              1.33 |               3652 |               3648 |          -0.68 |           0.03 |
|            2 | unreal<0 |             35.71 |             21.83 |               1802 |               1790 |           0.6  |           0.35 |
|            5 | all      |           -105.1  |             11.34 |               3948 |               3944 |          -2.54 |           0.26 |
|            5 | unreal<0 |            -36.27 |              0.79 |               2138 |               1913 |          -0.6  |           0.01 |
|           10 | all      |           -124.1  |             14.9  |               3803 |               3793 |          -2.7  |           0.35 |
|           10 | unreal<0 |            -25.86 |            -49.82 |               1969 |               1799 |          -0.39 |          -0.79 |
|           15 | all      |           -132.2  |             55.81 |               3697 |               3687 |          -3    |           1.29 |
|           15 | unreal<0 |             -5.84 |             -3.78 |               1835 |               1765 |          -0.09 |          -0.06 |
|           20 | all      |           -110.1  |            -30.35 |               3457 |               3442 |          -2.31 |          -0.6  |
|           20 | unreal<0 |            -37.32 |             22.63 |               1706 |               1581 |          -0.56 |           0.33 |
|           30 | all      |            -72.09 |             38.59 |               3040 |               3013 |          -1.5  |           0.81 |
|           30 | unreal<0 |             19.13 |             78.47 |               1416 |               1357 |           0.26 |           1.16 |
|           45 | all      |            -23.57 |            126.2  |               2647 |               2630 |          -0.4  |           2.39 |
|           45 | unreal<0 |              0.07 |             75.14 |               1221 |               1124 |           0    |           0.96 |
|           60 | all      |            -57.02 |             14.68 |               2467 |               2427 |          -0.95 |           0.28 |
|           60 | unreal<0 |             53.55 |             66.24 |               1101 |               1067 |           0.71 |           0.89 |

Target-rate lift (points of probability), all open trades:

|   offset_min |   target_rate_lift_mirror_yes |   target_rate_lift_random_yes |   target_rate_t_mirror_yes |   target_rate_t_random_yes |
|-------------:|------------------------------:|------------------------------:|---------------------------:|---------------------------:|
|            2 |                        -0.017 |                        -0.008 |                     -1.676 |                     -0.865 |
|            5 |                        -0.046 |                        -0.003 |                     -4.483 |                     -0.387 |
|           10 |                        -0.044 |                        -0.008 |                     -4.557 |                     -0.927 |
|           15 |                        -0.04  |                        -0.001 |                     -4     |                     -0.122 |
|           20 |                        -0.034 |                        -0.003 |                     -3.412 |                     -0.244 |
|           30 |                        -0.027 |                        -0.011 |                     -2.498 |                     -1.162 |
|           45 |                        -0.013 |                         0.036 |                     -1.065 |                      3.422 |
|           60 |                        -0.012 |                         0.007 |                     -0.938 |                      0.59  |

Reading: over all open trades the mirror trigger lowers the final result (-$105 to -$132 at +5..+15 min, t -2.5 to -3.0; Target rate -4 to -4.6 points, t about -4 to -4.6) while the random trigger with the same share does nothing (|t| < 1.3), so the signal is real in the pooled sense. But among trades that are ALREADY losing (unrealised < 0) the effect is gone (-$36 to +$54, |t| < 0.8): the mirror mostly flags trades that are not in profit, so it adds no demonstrated information beyond the price path at the cut decision. As a stand-alone cut trigger it is therefore NOT supported; as an input to a model that already knows the unrealised state it is untested here (W-LA / W-CF3 step 7). FIRST PASS, final-outcome based, survivors only.
