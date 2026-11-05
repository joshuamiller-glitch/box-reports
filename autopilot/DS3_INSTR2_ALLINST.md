# DS3_INSTR2_ALLINST - all-instrument family null (2026-11-05T20:41Z, ALLINST fork)
Prereg: /mnt/l2/l2vast/ALLINST_PREREG.md sha256 d7912c18 (DECISIONS.md, filed before any statistic). Base: 1-min owned engine, equal-risk lots (RISK/(stop*pv)), fees per FEES.md, window means in $/week as in each cells_all table; forward-only, epoch-second hash worlds.

**Plain sentence: no instrument clears.**

## Tier A - exact joint null (ES, RTY, YM)
All three tables use i2eval.hash_u(entry epoch-second, world w), W=200, statistic zj = min(z_L6M, z_HOLD): the same world index and the same clock across instruments, so the joint max M_joint[w] = max(M_ES, M_RTY, M_YM)[w] is a valid Westfall-Young null over all 1,371,510 eligible cells. Joint null max: median 3.81, p95 4.27 (single-instrument medians 3.57/3.60/3.57). World maxima are nearly uncorrelated across instruments (ES-RTY 0.005, ES-YM -0.09).

| inst | eligible cells | tolerant | best tolerant zj | best tolerant joint family p | cells with joint p <= .10 (all) | BH q <= .10 (tolerant / all) |
|---|---|---|---|---|---|---|
| ES | 456,498 | 8,149 | 3.47 | 0.970 | 6 (non-tolerant, see below) | 0 / 0 |
| RTY | 457,338 | 8,490 | 3.40 | 0.995 | 0 | 0 / 0 |
| YM | 457,674 | 11,605 | 3.36 | 0.995 | 0 | 0 / 0 |
| pooled | 1,371,510 | 28,244 | | | 6 | 0 / 0 |
BH q uses one-sided normal p from zj (approximation, labelled); the family p is the exact one. Pooled table: /mnt/l2/l2vast/allinst_pooled.parquet.

The 6 ES cells with joint p .06-.07 are one pattern: Keltner b3 ema34 atr14 m1.0 contrarian, london session, 30-min time stop (A3/A4/A6, 1.5-2R). Not tolerant: HOLD mean -$170 to -$570/wk, MID/PRE/X'/PRE23 all negative (PRE23 -$4.0k to -$8.5k), persistence 42-50%. L1M/L6M positive only: a NOW-ONLY regime fit, failed gate.

## 13-year check (top-30 tolerant by zj, from the cells_all window columns; the $ at equal-risk lots is approximately scale-free so no separate percent re-scaling was applied - labelled)
| inst | PRE23 mean > 0 | PRE (2024-25) > 0 | X' > 0 | HOLD > 0 | median PRE23 $/wk |
|---|---|---|---|---|---|
| ES | 0/30 | 17/30 | 0/30 | 30/30 | -287 |
| RTY | 2/30 | 7/30 | 3/30 | 30/30 | -94 |
| YM | 0/30 | 10/30 | 9/30 | 30/30 | -300 |
Pre-2023 sign negative for essentially all (>= 50% positive-years criterion fails). Per-year tick/1-s calibration (weekly corr >= .90) was not run by this fork: it is moot because the joint null already rejects; Z2's 13-year check owns the per-year tables.

## Tier B - no per-world artifacts (GC, CL, ZN, ZB, 6E, 6J, MBT/BTCM/BTC, NKD)
No new world draws (different engines/clocks; the artifacts hold only owner finalist nulls). Owner results: GC best p_book 0.05 but family 1.00 (Bonferroni over 132,286 cells); CL 30 finalists p_book 0.13-0.95; 6E no book (winners lost money 2024-25); ZN/ZB/6J/BTC/NKD pages are interim, no verdict yet. A Sidak union over 12 instruments cannot lower any reported family p, so nothing in Tier B clears either; Tier B is NOT a joint-null result and is labelled as such. To make it joint, owners must expose per-world maxima with the same hash_u clock (request logged in MORNING_FLAGS).

## Diversifier-bar verdict
No cell passes tolerant gate + joint family p <= .10 (or q <= .10) + 13-year sign. Walk-forward, corr to NQ stack and Calmar tests not triggered for lack of a candidate. No MORNING alert.

## BLOCK ZL-1 (2026-11-05): joint family null EXTENDED to CL, 6E, 6J (addendum l2vast/ds3/prereg/ALLINST_addendum_ZL1.md, sha256 824a3087...; filed in DECISIONS.md before any draw)
Same worlds as Tier A: u = hash_u(entry-bar epoch second, world w), w = 1..200, random side per trade (long when u < the cell's real long share), statistic zj = min(z_L6M, z_HOLD), family max over ALL eligible cells; the difference from the fork is exact re-simulation per world (my cells are one-position greedy cells, so a flipped side changes which trades are taken). Joint maximum over ES, RTY, YM, CL, 6E, 6J: median 3.83, p95 4.27 (single-instrument null maxima: CL 3.28/3.81, 6E 3.20/3.68, 6J 3.13/3.66). GC (S4a, own engine) and ZN / ZB / BTC / MBT / NKD are NOT in this joint null yet (no saved per-world maxima on the same clock; the native NKD / MBT books of addendum A are a separate family).
**Plain sentence: with the three new instruments in the joint null (about 192,000 more eligible cells, 1.56 million in total) no tolerant cell has a joint family p <= .10 (best joint p 1.00 for CL, 6E and 6J; best tolerant zj 3.24 / 2.63 / 1.12 against a joint null median of 3.83) and no cell has a BH q <= .10; the 13-year percent-frame check of the 30 best tolerant cells of each instrument shows a positive pre-2023 mean in only 3 (CL), 0 (6E) and 1 (6J) of 30.**
| inst | eligible cells | tolerant | best tolerant zj | best tolerant joint family p | cells with joint p <= .10 (all / tolerant) | BH q <= .10 | own null max median / p95 |
|--|--|--|--|--|--|--|--|
| CL | 64,230 | 7,883 | 3.24 | 1.000 | 0 / 0 | 0 | 3.28 / 3.81 |
| 6E | 63,888 | 2,676 | 2.63 | 1.000 | 0 / 0 | 0 | 3.20 / 3.68 |
| 6J | 64,323 | 310 | 1.12 | 1.000 | 0 / 0 | 0 | 3.13 / 3.66 |
Every tolerant cell with its joint p and BH q: /mnt/l2/l2vast/allinst_zl1_tolerant_{CL,6E,6J}.csv (full eligible tables: instr2_<sym>/allinst_table.pkl; per-world maxima: instr2_<sym>/allinst_M.npy, 200 values each). BH q uses the one-sided normal p of zj over all pooled eligible cells (ES / RTY / YM from allinst_pooled.parquet plus the new cells; labelled approximation).

### 13-year percent-frame check - top 30 tolerant cells by zj per instrument (1-minute 2013-06..2023-03, per-roll-segment rescale; integer equal-$ lots, session caps; weekly $ by year; full tables in instr2_<sym>/allinst_y13.pkl)

**CL**: positive pre-2023 mean $/trade in 3 of 30; negative in every year with >= 15 trades in 0; median mean $/trade -20.2; median years positive 3 of 11.
| # | family | session | params | bracket | zj | n | mean $/trade | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | keltner_flip | london | {'k': 10, 'n': 14, 'n_atr': 14, 'm | ('atr', 4) 1R T120 | 3.24 | 6646 | -18.8 | -734 | -649 | -727 | 570 | -639 | -206 | -255 | 1828 | -1139 | -295 | -159 |
| 2 | keltner_flip | london | {'k': 10, 'n': 8, 'n_atr': 14, 'mu | ('atr', 4) 1R T120 | 3.03 | 7423 | -20.5 | -871 | -1151 | -965 | -19 | -1063 | -679 | -420 | 3146 | -550 | -408 | 60 |
| 3 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('atr', 4) 2R T120 | 2.88 | 5743 | -25.5 | -827 | -398 | -874 | 279 | -1171 | -283 | -628 | 3219 | -1190 | -772 | -177 |
| 4 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('atr', 3) 2R T30 | 2.84 | 4414 | -19.1 | -338 | -407 | -649 | 95 | -284 | -283 | -638 | 1496 | -803 | 39 | 149 |
| 5 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('atr', 2) 1.5R T30 | 2.83 | 4652 | -46.1 | -509 | -761 | -1363 | -143 | -165 | -119 | -921 | 418 | -726 | 79 | 88 |
| 6 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('atr', 3) 1.5R T30 | 2.82 | 4455 | -26.4 | -336 | -376 | -681 | 101 | -93 | -223 | -675 | 691 | -826 | -26 | 182 |
| 7 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('usd', 600) 1.5R T30 | 2.80 | 4552 | -32.4 | -140 | -220 | -559 | 88 | -176 | 58 | -388 | -1066 | -586 | -75 | 229 |
| 8 | keltner_flip | london | {'k': 3, 'n': 14, 'n_atr': 14, 'mu | ('atr', 3) 1R T30 | 2.79 | 4606 | -36.7 | -424 | -410 | -612 | -86 | -32 | -180 | -554 | -598 | -643 | 151 | 142 |
| 9 | momentum_vote | nyam | {'k': 1, 'thr': 3, 'windows': (12, | ('atr', 2) 1.5R T30 | 2.78 | 9543 | -12.4 | -705 | -60 | 288 | -227 | -330 | -865 | 402 | -1223 | 458 | 194 | -218 |
| 10 | keltner_flip | london | {'k': 3, 'n': 8, 'n_atr': 14, 'mul | ('usd', 600) 1R T30 | 2.76 | 4504 | -38.3 | -107 | -76 | -286 | 288 | -99 | -109 | -520 | -1729 | -551 | -348 | 222 |
(rows 1-10 shown; rows 11-30 in the pickle.)

**6E**: positive pre-2023 mean $/trade in 0 of 30; negative in every year with >= 15 trades in 17; median mean $/trade -22.9; median years positive 0 of 11.
| # | family | session | params | bracket | zj | n | mean $/trade | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 2400) 1R T60 | 2.63 | 1832 | -15.1 | -71 | -81 | 62 | -62 | -146 | -55 | 6 | -40 | -82 | -63 | -2 |
| 2 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 2400) 1.5R T60 | 2.63 | 1832 | -15.1 | -71 | -81 | 62 | -62 | -146 | -55 | 6 | -40 | -82 | -63 | -2 |
| 3 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 1200) 1R T60 | 2.63 | 1837 | -26.5 | -71 | -128 | -274 | -73 | -146 | -55 | 6 | -40 | -82 | -72 | -2 |
| 4 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 1200) 2R T60 | 2.63 | 1837 | -26.4 | -71 | -128 | -274 | -70 | -146 | -55 | 6 | -40 | -82 | -73 | -2 |
| 5 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 2400) 2R T60 | 2.63 | 1832 | -15.1 | -71 | -81 | 62 | -62 | -146 | -55 | 6 | -40 | -82 | -63 | -2 |
| 6 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 1200) 1.5R T60 | 2.63 | 1837 | -26.2 | -71 | -128 | -274 | -61 | -146 | -55 | 6 | -40 | -82 | -73 | -2 |
| 7 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 600) 2R T60 | 2.61 | 1852 | -74.9 | -277 | -400 | -1029 | -138 | -285 | -112 | 12 | -110 | -163 | -143 | -22 |
| 8 | keltner_flip | pre | {'k': 5, 'n': 34, 'n_atr': 14, 'mu | ('usd', 600) 1.5R T60 | 2.61 | 1852 | -73.2 | -277 | -400 | -961 | -149 | -285 | -112 | 12 | -106 | -163 | -144 | -22 |
| 9 | momentum_vote | london | {'k': 5, 'thr': 2, 'windows': (12, | ('usd', 1200) 2R T120 | 2.60 | 5180 | -17.6 | -129 | -282 | -337 | -63 | -58 | -107 | -242 | -133 | -116 | -248 | -38 |
| 10 | momentum_vote | london | {'k': 5, 'thr': 2, 'windows': (12, | ('usd', 1200) 1.5R T120 | 2.60 | 5180 | -17.3 | -129 | -282 | -305 | -63 | -58 | -107 | -242 | -133 | -116 | -248 | -38 |
(rows 1-10 shown; rows 11-30 in the pickle.)

**6J**: positive pre-2023 mean $/trade in 1 of 30; negative in every year with >= 15 trades in 2; median mean $/trade -61.5; median years positive 2 of 11.
| # | family | session | params | bracket | zj | n | mean $/trade | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | supertrend_flip | nyam | {'k': 15, 'n': 5, 'm': 1.5} | ('atr', 4) 1R T120 | 1.12 | 1386 | -91.9 | 23 | -97 | -263 | -62 | -154 | -359 | -766 | -177 | -325 | -299 | 30 |
| 2 | keltner_flip | pre | {'k': 10, 'n': 34, 'n_atr': 14, 'm | ('atr', 3) 2R T120 | 0.57 | 1196 | -150.3 | -533 | -1161 | -499 | -318 | -224 | -349 | -315 | 101 | -275 | 12 | 105 |
| 3 | supertrend_flip | nyam | {'k': 10, 'n': 5, 'm': 2.0} | ('atr', 2) 2R T120 | 0.53 | 1515 | -148.0 | -319 | -331 | -106 | -164 | -338 | -739 | -1058 | -660 | -352 | -285 | 40 |
| 4 | supertrend_flip | nyam | {'k': 10, 'n': 14, 'm': 2.0} | ('atr', 2) 1.5R T120 | 0.50 | 1820 | -143.2 | -117 | -494 | -364 | -509 | -347 | -801 | -976 | -770 | -510 | -165 | 43 |
| 5 | supertrend_flip | nyam | {'k': 10, 'n': 5, 'm': 2.0} | ('atr', 2) 1.5R T120 | 0.43 | 1525 | -141.3 | -203 | -315 | -85 | -294 | -337 | -699 | -973 | -675 | -359 | -193 | -13 |
| 6 | supertrend_flip | nyam | {'k': 15, 'n': 5, 'm': 1.5} | ('atr', 2) 2R T120 | 0.42 | 1535 | -153.4 | -103 | -609 | -344 | -157 | -321 | -531 | -1144 | -555 | -390 | -403 | 28 |
| 7 | supertrend_flip | nyam | {'k': 10, 'n': 14, 'm': 2.0} | ('atr', 2) 2R T120 | 0.41 | 1798 | -152.0 | -198 | -581 | -424 | -358 | -451 | -831 | -1089 | -749 | -469 | -234 | 129 |
| 8 | supertrend_flip | nyam | {'k': 10, 'n': 7, 'm': 3.0} | ('atr', 2) 1R T120 | 0.40 | 921 | -148.6 | -124 | -342 | -230 | -6 | -10 | -455 | -542 | -292 | -319 | -365 | 55 |
| 9 | supertrend_flip | nypm | {'k': 15, 'n': 7, 'm': 4.0} | ('atr', 6) 2R T30 | 0.33 | 252 | -41.2 | -42 | -37 | 7 | 22 | -56 | -49 | 19 | -55 | 2 | -9 | -4 |
| 10 | supertrend_flip | nypm | {'k': 15, 'n': 7, 'm': 4.0} | ('atr', 6) 1.5R T30 | 0.31 | 252 | -41.8 | -42 | -37 | 7 | 22 | -56 | -49 | 17 | -55 | 2 | -9 | -4 |
(rows 1-10 shown; rows 11-30 in the pickle.)

Diversifier-bar verdict for CL / 6E / 6J: no cell passes tolerant gate + joint family p <= .10 (or q <= .10) + 13-year sign; walk-forward, correlation and Calmar tests were already negative for the stage-2 finalists (DS3_INSTR2_CL.md / _6E.md / _6J.md). No MORNING alert.
