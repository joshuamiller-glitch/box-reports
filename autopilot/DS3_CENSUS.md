# DS3 CENSUS (D3C, 2026-10-26; 6-h edition, revisable: T-B top 20 and T-ENTRY top 20 sections to be added when they land)

Research only. Descriptive: a census, not a search. Protocol `l2vast/ds3/prereg/CENSUS_DESC.md` sha256 68b63b9e9d471e36e3847997edc1a63e8ca7888ae67935e582bc237ad7b2d4d6 (DECISIONS.md 2026-10-26); ledger line `DS3_CENSUS` cells=0 (re-read of already-counted trials); holdout and 2023-04..2024-01 looks logged as `DS3_CENSUS`. Code `l2vast/ds3/code/c1..c8*.py`. Machine-readable: `l2vast/ds3/out/pool.parquet` (+ `series/<id>.parquet`, `daily_pool_live.parquet`, `weekly_pool_live.parquet`, `census_all.parquet`).

## 0. Answer in ten lines

1. **The library** = `outputs/library/INDEX.csv`: 40,041 rows (40,023 loadable), 524 families, every row status "active". Series = daily USD at standard size (R = $9,600, 8 NQ-contract-equivalents at a 60-pt stop; 30,412 rows are vol-matched to one 8-contract book). Stored cost is mostly 1 tick/side + $4.36/contract. Window metrics computed on: X = 2023-04..2024-01 (never scored for library series), WF-PRE 2024-02..2025-06, WF 2024-02+, HOLD 2025-07+ (68 weeks).
2. **Excluded** (counted, not scored for verdict): 1,694 VOID (1,629 BASIS-VOID FVG/ICT with a look-ahead warning, WITHDRAWN rows, and the 9 K4-pack cells removed for look-ahead 2026-10-19), 130 overlay deltas, 1,192 with <10 active days in HOLD or X. Eligible 37,007; **deduped at |daily corr| >= 0.9 -> 31,081 series scored** (ordered by 2023-08..2025-07 Sharpe; greedy, so each cluster is represented by its best-clean member).
3. **Census tiers on the deduped set (re-costed to the live model by approximation, section 2)**: T1 (WF-PRE, HOLD and X means all > 0 and WF weekly t >= 2) **1,019**; T2 (all three > 0, t < 2) 3,019; fail 27,043 (HOLD <= 0: 19,760; X <= 0: 5,321; WF-PRE <= 0: 1,962).
4. **Selection from ~31k series is the whole story of the best-of-library number.** Highest re-costed HOLD Sharpe = **3.76**. With 68 holdout weeks the annualised-Sharpe SE is about 0.87, and the expected maximum of 31,000 standard normals is 4.0 sigma, i.e. **3.5 Sharpe with zero true edge** (upper bound, since the series are correlated). The timing-destroyed null (200 reps, the assembly daemon's method) gives best-of-library HOLD Sharpe mean 3.87 (p95 4.53), rank-10 3.10, rank-50 2.68 (p95 2.73); the real ranks 10 / 20 / 50 are 3.21 / 3.03 / 2.78, only +0.1 above the null mean and about at its p95. **The top-50 list is not distinguishable from chance by that null.**
5. T1 count: real 1,021 (re-costed, incl. the live books) vs timing-destroyed null 977 (p95 1,003) vs weekly-sign-flip (edge-destroyed) null 313 (p95 343). The shift null keeps each series' full-sample mean, so it mostly reproduces T1; the sign-flip null says roughly 30% of T1 would appear with zero edge at this t >= 2 filter. Net: about 700 T1 series are above the zero-edge expectation, but they are highly clustered (a few MA-cross / indicator families on NQ at 1-5 min: 895 of 1,019 T1 are NQ, 675 are T3S1_G_G variants that share the same trades), so the number of independent edges is of order tens, not hundreds.
6. **Where T1 lives**: NQ intraday trend / MA-cross / indicator systems (T3S1_G, V5, WT, ST/HM-type), BTC/ETH trend books, some ES/RTY/YM dip-buy and breakout. ES 28, RTY 11, YM 15, BTC 26, CL 6, GC 12, ZN 1, 6E 1, 6J 0, ZB 0 of T1. Mean-reversion / calendar / ICT / order-flow / cross-asset: almost no T1 (29 + 5 + 3 + 4 + 2).
7. **Top-50 versus DS2** (section 4): corr to DS2 (ST10/HM10/WT7 per-book, WF weekly) ranges -0.13 to 0.63 and 36 of 50 lie between 0.4 and 0.6, i.e. few are independent diversifiers; the s48score sleeve verdict on all 50 is DEAD-provisional (neighbours and a library-book placebo are missing; 9 of 50 have a negative 2023-04..2024-01 Sharpe and 16 a WF-PRE Sharpe below 0.5; 44 of the 50 are T3S1_G variants). Per-series timing placebo P(shifted >= real) is <= 0.05 for 37 of the top 50 (16 of the NQ top 20), but the placebo keeps the full-sample mean, so it is a weak test.
8. **ST / HM / WT as ordinary books** (section 5): at live cost (DS2 per-book, corrected P9, $4.84) ST10 HOLD Sharpe 1.91, HM10 1.34, WT7 0.20, pair 10/10 2.01, ST10/HM10/WT7 1.77; X-span 0.97 / 0.71 / 0.33 / 1.01 / 0.92. The library 8-lot rows of ST and HM (old engine, 1 tick/side) are not the same series: ST 0.64, HM 2.00 on HOLD, so the pool carries both and labels the source.
9. **PAPER-ALL** (1.2): 50 struct48 cells and 205 m2-league rows, **0 official forward weeks** for all; no forward evidence for or against any DS3 candidate. **MBO seven** (1.3): no paper-soak P&L exists on this box; all seven are L2-dependent at runtime, NOT DELIVERABLE for DS3. **K4** (1.4): nine pack cells not in the live 17 were removed for look-ahead (NOT DELIVERABLE, excluded). **Leads** (1.5): all four are DEAD-provisional under V2 (missing placebo/neighbour evidence); details in sections 7-8.
10. **Pool**: `pool.parquet` has 31,098 rows (31,081 deduped eligible library series + ST/HM/PAIR/WT10/WT_LIVE/WT_B10/WT_TOP1/WThist forced in + 10 DS2 per-book rows at 8/10/12/14 lots). Want 8 cores, used 8 (corepool), min 2.

## 1. Library and method (how the numbers were made)

- Loader `code/c1_load.py` (every family file; daily axis 2023-02-01..2026-10-23, zero where no trade; series end 2026-10-13..16). Windows: weekly (ISO) sums of daily P&L, Sharpe = mean/SD x sqrt(52), t = mean/SD x sqrt(weeks).
- Stored vs live cost. The library keeps daily P&L only; there are no per-trade counts. **Re-cost = stored daily P&L minus (extra live cost per active day)**, one trade per active day assumed (a LOWER bound on trades, so the re-cost is optimistic for multi-trade/day books): NQ rows -$84 per active day (+0.5 pt x $20 x 8 contracts for the live 1.0 pt vs the stored 1 tick/side, plus $0.48 x 8 for $4.84 vs $4.36); ES and RTY rows -$3.84 per active day (commission only); other instruments unchanged. T4-style L2 replay of ES/RTY books was NOT run (not feasible for 31k series; the T-A/T-C agents must replay any ES/RTY candidate). NQ P9 point-table replay needs trades; pool rows carry `live_cost_adj_per_active_day_usd` so the track agents can re-cost properly. DS2 per-book rows (from `l2vast/struct48/out/ASM/series.pkl`) are already at live cost and are not re-costed.
- Dedupe: greedy, series ordered by 2023-08..2025-07 weekly Sharpe, drop any series with |daily corr| >= 0.9 (2023-04..2026-10) to a kept one (`dedup_rep` in `census_all.parquet`). 5,926 eligible series dropped as duplicates.
- Mechanism family: classified from family/series name and spec text (T3S1_G groups G1-G5 by indicator class); the "other/unclassified" and "trend/momentum" buckets are coarse. Horizon from the library `horizon` field (intraday 30,088 of 31,081). Executability: from the library `executability` text; **nothing was identity-tested**: "NT8-BARS" means only that the source says codable.
- Nulls: timing-destroyed = per-series random circular day shift within its own span (as `ap_assembly.py`), 200 reps over all 31,084 candidate columns; edge-destroyed = weekly random sign flip of de-meaned series, 200 reps; same re-cost and tier rule. Per-series placebo (top 50, NQ top 20, ST/HM/WT): 1,000 shifts, p = share of shifted-series HOLD Sharpe >= real.
- Ledger: no cells added (descriptive re-read; the library series are already inside the corrected PRED / STRUCT48 trial counts). The multiple-testing consequence is the one in 0.4: 31,081 series (about 40,000 before exclusions and dedupe) were read on the same HOLD; any single-series holdout number below is a draw from the maximum of that set unless it also passes an independent test.
- Disclosure: all-window metrics were computed before the look was logged; I glanced only at the top-10 raw HOLD Sharpe rows to catch look-ahead artefacts (they were FVG/ICT BASIS-VOID rows, now excluded). Library ST/HM in the pool are the library's own 8-lot series (old B11 engine) and differ from the DS2 per-book series (corrected P9 engine).

## 2. Counts (section 1.1)

#### A. All rows by tier (raw, before dedupe)
| tier0                                          |   rows |
|:-----------------------------------------------|-------:|
| F-HOLD (holdout <=0)                           |  22923 |
| F-X (2023-04..2024-01 <=0)                     |   6519 |
| T2 (3 spans +, t<2)                            |   3715 |
| F-WFPRE (WF-PRE <=0)                           |   2472 |
| EXCL-VOID(look-ahead/withdrawn)                |   1694 |
| T1 (3 spans +, WF t>=2)                        |   1378 |
| EXCL-NODATA(<10 active days in HOLD/X or flat) |   1192 |
| EXCL-OVERLAY(delta, not standalone)            |    130 |

#### B. Deduped eligible set (n=31081) by tier
| tier0                      |   series |
|:---------------------------|---------:|
| F-HOLD (holdout <=0)       |    19760 |
| F-X (2023-04..2024-01 <=0) |     5321 |
| T2 (3 spans +, t<2)        |     3019 |
| F-WFPRE (WF-PRE <=0)       |     1962 |
| T1 (3 spans +, WF t>=2)    |     1019 |

#### C. Deduped eligible by instrument x tier
| inst2   |   F-HOLD (holdout <=0) |   F-WFPRE (WF-PRE <=0) |   F-X (2023-04..2024-01 <=0) |   T1 (3 spans +, WF t>=2) |   T2 (3 spans +, t<2) |   total |
|:--------|-----------------------:|-----------------------:|-----------------------------:|--------------------------:|----------------------:|--------:|
| NQ      |                   5261 |                   1279 |                         2361 |                       895 |                  1937 |   11733 |
| ES      |                   2213 |                    162 |                          489 |                        28 |                   232 |    3124 |
| CL      |                   1849 |                    117 |                          432 |                         6 |                    90 |    2494 |
| GC      |                   1386 |                     89 |                          856 |                        12 |                   110 |    2453 |
| ZN      |                   2354 |                     17 |                           32 |                         1 |                    20 |    2424 |
| 6E      |                   1373 |                     53 |                          315 |                         1 |                    31 |    1773 |
| 6J      |                   1571 |                     55 |                           89 |                         0 |                    38 |    1753 |
| RTY     |                    946 |                     50 |                          240 |                        11 |                   120 |    1367 |
| ZB      |                   1048 |                      1 |                            7 |                         0 |                     1 |    1057 |
| multi   |                    486 |                     59 |                          178 |                        13 |                    88 |     824 |
| BTC     |                    307 |                     15 |                          109 |                        26 |                   134 |     591 |
| other   |                    433 |                     21 |                           83 |                         2 |                    48 |     587 |
| YM      |                    266 |                     28 |                           86 |                        15 |                    94 |     489 |
| ETH     |                    169 |                      5 |                           19 |                         9 |                    39 |     241 |
| HO      |                     98 |                     11 |                           25 |                         0 |                    37 |     171 |

#### C. Deduped eligible by mechanism family x tier
| mech                                                        |   F-HOLD (holdout <=0) |   F-WFPRE (WF-PRE <=0) |   F-X (2023-04..2024-01 <=0) |   T1 (3 spans +, WF t>=2) |   T2 (3 spans +, t<2) |   total |
|:------------------------------------------------------------|-----------------------:|-----------------------:|-----------------------------:|--------------------------:|----------------------:|--------:|
| trend/momentum                                              |                   7533 |                    682 |                         1642 |                        91 |                   732 |   10680 |
| other/unclassified                                          |                   3940 |                    178 |                         1109 |                       202 |                   870 |    6299 |
| breakout/opening-range                                      |                   3520 |                    207 |                          659 |                         7 |                   175 |    4568 |
| mean-reversion/fade                                         |                   1838 |                    158 |                          441 |                        29 |                    86 |    2552 |
| trend: MA cross / price-vs-MA                               |                    504 |                    259 |                          369 |                       262 |                   429 |    1823 |
| trend/momentum other                                        |                    702 |                    108 |                          304 |                        59 |                   141 |    1314 |
| ICT/FVG pattern                                             |                    733 |                     68 |                          244 |                         3 |                    34 |    1082 |
| trend: indicator systems (ichimoku/psar/chandelier/lrslope) |                    168 |                    130 |                          147 |                       161 |                   204 |     810 |
| momentum oscillators (MACD/ROC/TSI/elder)                   |                    115 |                     62 |                           87 |                       129 |                   153 |     546 |
| calendar/time-of-day                                        |                    352 |                     11 |                           56 |                         5 |                    22 |     446 |
| order-flow/volatility-state                                 |                    200 |                     27 |                          101 |                         4 |                    29 |     361 |
| volume-based trend (OBV/VWAP)                               |                     68 |                     23 |                           80 |                        45 |                    78 |     294 |
| breakout: channel/Donchian/BB                               |                     43 |                     26 |                           62 |                        19 |                    52 |     202 |
| cross-asset/relative-value                                  |                     44 |                     23 |                           20 |                         2 |                    13 |     102 |
| live-book (ST/HM)                                           |                      0 |                      0 |                            0 |                         1 |                     1 |       2 |

#### C. Deduped eligible by horizon x tier
| hor       |   F-HOLD (holdout <=0) |   F-WFPRE (WF-PRE <=0) |   F-X (2023-04..2024-01 <=0) |   T1 (3 spans +, WF t>=2) |   T2 (3 spans +, t<2) |   total |
|:----------|-----------------------:|-----------------------:|-----------------------------:|--------------------------:|----------------------:|--------:|
| intraday  |                  19236 |                   1870 |                         5115 |                       975 |                  2892 |   30088 |
| multi-day |                    418 |                     78 |                          158 |                        38 |                    82 |     774 |
| daily     |                     75 |                      9 |                           23 |                         5 |                    22 |     134 |
| weekly+   |                     18 |                      3 |                           21 |                         1 |                    14 |      57 |
| unknown   |                     13 |                      2 |                            3 |                         0 |                     4 |      22 |
| overnight |                      0 |                      0 |                            1 |                         0 |                     5 |       6 |

#### C. Deduped eligible by bar type x tier
| barclass     |   F-HOLD (holdout <=0) |   F-WFPRE (WF-PRE <=0) |   F-X (2023-04..2024-01 <=0) |   T1 (3 spans +, WF t>=2) |   T2 (3 spans +, t<2) |   total |
|:-------------|-----------------------:|-----------------------:|-----------------------------:|--------------------------:|----------------------:|--------:|
| 1m-30m/other |                  17381 |                   1239 |                         3925 |                       194 |                  1758 |   24497 |
| daily        |                   2372 |                    719 |                         1389 |                       798 |                  1254 |    6532 |
| 1s           |                      5 |                      3 |                            5 |                        27 |                     4 |      44 |
| tick         |                      2 |                      1 |                            2 |                         0 |                     3 |       8 |

#### D. Excluded rows
| tier0                                          |   rows |
|:-----------------------------------------------|-------:|
| EXCL-VOID(look-ahead/withdrawn)                |   1694 |
| EXCL-NODATA(<10 active days in HOLD/X or flat) |   1192 |
| EXCL-OVERLAY(delta, not standalone)            |    130 |

## 3. Best-of-library against chance (timing-destroyed and edge-destroyed nulls)

#### E. Null vs real (n=31084 series)
| null                               |   reps |   T1_mean |   T1_p95 |   T12_mean |   T12_p95 |   hold_pos_mean |   hold_t2_mean |   top1_mean |   top1_p95 |   top10_mean |   top50_mean |   top50_p95 |
|:-----------------------------------|-------:|----------:|---------:|-----------:|----------:|----------------:|---------------:|------------:|-----------:|-------------:|-------------:|------------:|
| timing-destroyed (circular shift)  |    200 |    977.01 |   1003   |    4107.11 |   4168.05 |         11797.7 |         825.08 |        3.87 |       4.53 |         3.1  |         2.68 |        2.73 |
| edge-destroyed (weekly sign flip)  |    200 |    313.08 |    343.1 |    3646.29 |   3732.1  |         15230.4 |         713.38 |        3.73 |       4.29 |         3.03 |         2.59 |        2.65 |
| REAL (deduped eligible, re-costed) |      1 |   1021    |    nan   |    4040    |    nan    |         11324   |        1038    |        3.76 |     nan    |         3.21 |         2.78 |      nan    |

#### F. Holdout Sharpe by rank: real vs nulls (ranks 1,5,10,20,30,40,50)
|    |   real |   shift_mean |   shift_p95 |   sign_mean |   sign_p95 |
|---:|-------:|-------------:|------------:|------------:|-----------:|
|  1 |   3.76 |         3.87 |        4.53 |        3.73 |       4.29 |
|  5 |   3.36 |         3.29 |        3.5  |        3.22 |       3.44 |
| 10 |   3.21 |         3.1  |        3.22 |        3.03 |       3.17 |
| 20 |   3.03 |         2.92 |        3.01 |        2.84 |       2.93 |
| 30 |   2.94 |         2.82 |        2.9  |        2.73 |       2.82 |
| 40 |   2.85 |         2.74 |        2.81 |        2.66 |       2.72 |
| 50 |   2.78 |         2.68 |        2.73 |        2.59 |       2.65 |

Reading: at ranks 1-5 the real Sharpes are inside the null spread; at ranks 10-50 they are 0.1 above the null mean and at about its 95th percentile. The best-of-library number is therefore what a library of this size and this holdout length produces with the timing destroyed (and with zero edge, 3.7 / 3.0 / 2.6 at ranks 1 / 10 / 50). It is a reason to give **no standalone holdout number from this library any weight without an independent test** (X-span sign, forward weeks, placebo vs random library books at equal count).


## 4. Top 50 by re-costed holdout Sharpe (deduped, eligible), with corr to DS2

columns: l_ = re-costed (weekly Sharpe, annualised), s_HOLD_sh = stored cost, l_HOLD_mean = $/wk at library std size, corr_DS2 = WF weekly corr with DS2 (ST10/HM10/WT7 per-book, ASM_10_10_7_PB), plc_p = timing-shift placebo p (1,000 shifts; small = real beats shifted), sleeve_vs_DS2 = s48score sleeve criterion (standalone holdout > 0, marginal Sharpe up at 0.5 SD ratio, corr <= 0.5, vs DS2 as the base) / provisional verdict.

#### G. Top 50 by re-costed holdout Sharpe (deduped, eligible)
|   rank | name                                                       | inst   | mech                                                        | hor       |   l_HOLD_sh |   l_HOLD_mean |   l_WF_sh |   l_WFPRE_sh |   l_X_sh |   s_HOLD_sh |   l_HOLD_dd |   corr_DS2 |   corr_ST10 |   corr_HM10 |   plc_p | tier0                      | exec_tag                                                | sleeve_vs_DS2   |
|-------:|:-----------------------------------------------------------|:-------|:------------------------------------------------------------|:----------|------------:|--------------:|----------:|-------------:|---------:|------------:|------------:|-----------:|------------:|------------:|--------:|:---------------------------|:--------------------------------------------------------|:----------------|
|      1 | T3S1_G_G_v1/G_G3_chandelier_n22_k2.0_tf1_eNone_t5          | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        3.76 |       26110.4 |      1.62 |        -0.38 |    -0.32 |        3.81 |      165404 |       0.53 |        0.49 |        0.41 |    0.01 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|      2 | T3S1_G_G_v1/G_G4_elder__tf5_eNone_delta                    | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        3.65 |       27196.3 |      2.25 |         0.8  |    -2.39 |        3.71 |      347927 |       0.15 |        0.18 |        0.12 |    0.05 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|      3 | T3S1_G_G_v1/G_G4_elder__tf5_eNone_none                     | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        3.54 |       24062.4 |      2.59 |         1.66 |    -2.08 |        3.6  |      313848 |       0.19 |        0.2  |        0.17 |    0.03 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|      4 | T3S1_G_G_v1/G_G1_pxma_kindDEMA_n50_tf1_eNone_t5            | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.43 |       21426.8 |      1.66 |         0.18 |     0.54 |        3.49 |      140361 |       0.57 |        0.53 |        0.45 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|      5 | T3S1_G_G_v1/G_G1_macross_kindSMA_f9_s21_tf1_eNone_t5       | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.36 |       21444.4 |      1.82 |         0.47 |     1.04 |        3.43 |      184660 |       0.53 |        0.45 |        0.44 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|      6 | T3S1_G_G_v1/G_G5_obv_n60_tf5_eNone_delta                   | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        3.26 |       22141.5 |      2.26 |         1.27 |     1.12 |        3.32 |      211149 |       0.43 |        0.3  |        0.35 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|      7 | T3S1_L/L_VX1_c0.02_v30_t0.02_lag1                          | VX     | other/unclassified                                          | daily     |        3.23 |       17071   |      1.71 |         0.42 |     3.1  |        3.23 |      156314 |      -0.11 |       -0.17 |        0.05 |    0.03 | T1 (3 spans +, WF t>=2)    | NOT-DELIVERABLE (instrument not available)              | crit_ok/DEAD    |
|      8 | T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_delta                    | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        3.23 |       21941.4 |      2.47 |         1.71 |     1.34 |        3.29 |      154879 |       0.44 |        0.38 |        0.39 |    0.22 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|      9 | T3S1_BOOKS_B/B_HM_24_90_200                                | NQ     | other/unclassified                                          | intraday  |        3.22 |       29228.6 |      1.97 |         0.42 |    -1.39 |        3.26 |      340146 |       0.3  |        0.21 |        0.31 |    0.09 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     10 | T4B/YM_B1_dip_rsi5_rsi80_stop2                             | YM     | mean-reversion/fade                                         | multi-day |        3.21 |       28229.9 |      1.66 |        -0.24 |     0.96 |        3.21 |      141966 |      -0.13 |       -0.13 |       -0.05 |    0.01 | F-WFPRE (WF-PRE <=0)       | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     11 | T3S1_G_G_v1/G_G3_squeeze__tf1_e200_t15                     | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        3.18 |       20238.6 |      1.88 |         0.71 |     2.05 |        3.24 |      153272 |       0.45 |        0.39 |        0.39 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     12 | T3S1_G_G_v1/G_G1_pxma_kindWMA_n10_tf5_e200_t15             | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.18 |       22836.9 |      2.02 |         0.83 |     0.82 |        3.23 |      121114 |       0.43 |        0.44 |        0.31 |    0.03 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     13 | T3S1_G_G_v1/G_G4_macd_f5_s35_g5_modezero_tf1_e200_t15      | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        3.16 |       22074.4 |      2.4  |         1.63 |     0.5  |        3.21 |      181599 |       0.49 |        0.42 |        0.38 |    0.07 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     14 | T3S1_G_G_v1/G_G3_ichi_t7_k22_sb44_modecloud_tf1_e200_t15   | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        3.15 |       28411.6 |      2.2  |         1.07 |     0.73 |        3.19 |      152097 |       0.45 |        0.4  |        0.36 |    0.05 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     15 | T3S1_G_G_v1/G_G1_macross_kindWMA_f9_s21_tf1_eNone_t5       | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.15 |       20446.8 |      1.64 |         0.31 |     0.79 |        3.21 |      153606 |       0.53 |        0.45 |        0.43 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     16 | T3S1_G_G_v1/G_G3_alligator__tf1_e200_t5                    | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        3.13 |       19372.6 |      2.12 |         1.2  |     0.16 |        3.2  |      173095 |       0.63 |        0.53 |        0.49 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     17 | T3S1_G_G_v1/G_G1_pxma_kindHMA_n100_tf1_eNone_t5            | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.11 |       17109.5 |      1.38 |         0.06 |     0.21 |        3.19 |      166438 |       0.55 |        0.52 |        0.43 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     18 | T3S1_G_G_v1/G_G1_pxma_kindSMA_n10_tf5_e200_t15             | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.08 |       17499.5 |      1.68 |         0.52 |     0.26 |        3.15 |      149769 |       0.43 |        0.38 |        0.33 |    0    | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     19 | T3S1_G_G_v1/G_G4_elder__tf5_e200_t15                       | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        3.06 |       21594.6 |      1.67 |         0.23 |     1.57 |        3.12 |      199080 |       0.45 |        0.41 |        0.39 |    0.04 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     20 | T3S1_G_G_v1/G_G1_macross_kindHMA_f20_s50_tf1_eNone_t5      | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.03 |       22504.1 |      1.89 |         0.72 |     0.79 |        3.08 |      184092 |       0.5  |        0.39 |        0.5  |    0.04 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     21 | T3S1_G_G_v1/G_G1_pxma_kindHMA_n10_tf5_e200_t15             | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        3.03 |       22250   |      1.76 |         0.41 |     1.4  |        3.08 |      226610 |       0.41 |        0.39 |        0.32 |    0.05 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     22 | T3S1_G_G_v1/G_G5_obv_n60_tf5_e200_t15                      | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        3.02 |       20698   |      2.57 |         2.08 |     0.49 |        3.08 |      185526 |       0.5  |        0.4  |        0.4  |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     23 | T3S1_G_G_v1/G_G5_obv_n60_tf5_eNone_t5                      | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        3    |       21034.7 |      2.32 |         1.59 |     0.8  |        3.06 |      168650 |       0.47 |        0.34 |        0.42 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     24 | T3S1_G_G_v1/G_G1_macross_kindWMA_f9_s21_tf1_e200_t5        | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.99 |       20386.8 |      1.92 |         0.9  |     1.29 |        3.05 |      176869 |       0.54 |        0.48 |        0.43 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     25 | T3S1_G_G_v1/G_G3_lrslope_n30_r2t0.3_tf1_e200_t5            | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.99 |       18956.2 |      1.9  |         0.93 |    -0.02 |        3.05 |      216652 |       0.57 |        0.49 |        0.47 |    0.01 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     26 | T3S1_G_G_v1/G_G3_lrslope_n30_r2t0.5_tf5_e200_t15           | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.96 |       21598.6 |      1.86 |         0.62 |     0.32 |        3.02 |      182292 |       0.33 |        0.28 |        0.21 |    0.1  | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     27 | T3S1_G_G_v1/G_G1_macross_kindT3_f5_s20_tf1_e200_t15        | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.96 |       23444.1 |      2.02 |         1.01 |     1.44 |        3.01 |      184170 |       0.53 |        0.46 |        0.43 |    0.06 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     28 | T3S1_G_G_v1/G_G4_tsi_r13_s7_modezero_tf1_eNone_t5          | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        2.96 |       18471.1 |      1.56 |         0.35 |     0.09 |        3.02 |      172734 |       0.55 |        0.48 |        0.46 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     29 | T3S1_BOOKS_B/B_ST_60_3.0_300                               | NQ     | other/unclassified                                          | intraday  |        2.95 |       17657.1 |      2.28 |         1.68 |     1.92 |        3.01 |      191174 |       0.56 |        0.55 |        0.41 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     30 | T3S1_G_G_v1/G_G1_pxma_kindTEMA_n10_tf5_eNone_t5            | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.94 |       20993.1 |      1.33 |        -0.32 |     0.51 |        3    |      208917 |       0.42 |        0.36 |        0.36 |    0.04 | F-WFPRE (WF-PRE <=0)       | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     31 | T3S1_G_G_v1/G_G3_lrslope_n30_r2t0.5_tf1_e200_delta         | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.93 |       18971.7 |      1.81 |         0.75 |    -0.11 |        2.99 |      164506 |       0.4  |        0.31 |        0.34 |    0.06 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     32 | T3S1_G_G_v1/G_G3_ichi_t9_k26_sb52_modecross_tf1_e200_delta | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.91 |       19571.3 |      2.37 |         1.81 |     0.43 |        2.97 |      153651 |       0.51 |        0.49 |        0.36 |    0.06 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     33 | T3S1_G_G_v1/G_G3_psar_af0.02_mx0.2_tf5_e200_adx20          | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.91 |       17682.9 |      1.54 |         0.35 |     1.49 |        2.98 |      164333 |       0.44 |        0.34 |        0.39 |    0.04 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     34 | T3S1_G_G_v1/G_G3_ichi_t9_k26_sb52_modecross_tf1_e200_t15   | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.91 |       24205.9 |      2.49 |         2.03 |     1.28 |        2.96 |      195833 |       0.42 |        0.41 |        0.29 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     35 | C11DIP/NQ_dip_rsi5_rsi80_stop2                             | NQ     | mean-reversion/fade                                         | multi-day |        2.91 |       24816.7 |      1.81 |         0.51 |     0.96 |        2.91 |      251112 |      -0.08 |       -0.06 |       -0.03 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     36 | T3S1_G_G_v1/G_G5_obv_n30_tf1_e200_delta                    | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        2.9  |       19109.1 |      2.02 |         1.15 |     0.32 |        2.96 |      227548 |       0.42 |        0.43 |        0.23 |    0    | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     37 | T3S1_G_G_v1/G_G1_pxma_kindHMA_n50_tf1_eNone_t5             | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.9  |       19375.2 |      1.16 |        -0.45 |     1.81 |        2.96 |      190793 |       0.43 |        0.39 |        0.34 |    0.03 | F-WFPRE (WF-PRE <=0)       | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     38 | T3S1_G_G_v1/G_G1_macross_kindVIDYA_f5_s20_tf1_eNone_t15    | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.89 |       18404.8 |      1.15 |        -0.49 |     0.1  |        2.95 |      170075 |       0.3  |        0.26 |        0.23 |    0.01 | F-WFPRE (WF-PRE <=0)       | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     39 | T3S1_G_G_v1/G_G3_lrslope_n30_r2t0.5_tf5_e200_t5            | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.85 |       19380.1 |      2.09 |         1.25 |    -0.14 |        2.91 |      157135 |       0.45 |        0.35 |        0.41 |    0.1  | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     40 | T3S1_G_G_v1/G_G1_macross_kindDEMA_f9_s21_tf5_e200_delta    | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.85 |       17743.2 |      1.7  |         0.66 |     0.42 |        2.91 |      230733 |       0.33 |        0.28 |        0.31 |    0.07 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     41 | T3S1_G_G_v1/G_G2_donchian_n20_tf5_eNone_adx20              | NQ     | breakout: channel/Donchian/BB                               | intraday  |        2.84 |       19021.9 |      2.3  |         1.74 |    -0.58 |        2.91 |      182333 |       0.33 |        0.27 |        0.26 |    0.06 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     42 | T3S1_G_G_v1/G_G1_pxma_kindEMA_n10_tf5_e200_t15             | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.84 |       17294.5 |      1.84 |         0.94 |     0.81 |        2.91 |      138274 |       0.48 |        0.4  |        0.37 |    0.01 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     43 | T3S1_G_G_v1/G_G5_obv_n30_tf5_e200_t15                      | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        2.84 |       18810   |      2.15 |         1.45 |     1.48 |        2.9  |      226473 |       0.4  |        0.34 |        0.29 |    0    | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     44 | T3S1_G_G_v1/G_G4_roc_n10_tf5_e200_none                     | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        2.83 |       22106.3 |      1.86 |         0.77 |    -0.38 |        2.88 |      155157 |       0.45 |        0.41 |        0.33 |    0.02 | F-X (2023-04..2024-01 <=0) | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     45 | T3S1_G_G_v1/G_G5_obv_n60_tf5_eNone_adx20                   | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        2.83 |       21164.9 |      2.08 |         1.26 |     0.98 |        2.88 |      213936 |       0.41 |        0.28 |        0.35 |    0.03 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     46 | T3S1_G_G_v1/G_G3_alligator__tf1_e200_t15                   | NQ     | trend: indicator systems (ichimoku/psar/chandelier/lrslope) | intraday  |        2.82 |       19696.3 |      2.08 |         1.34 |     0.34 |        2.88 |      217545 |       0.51 |        0.46 |        0.39 |    0.02 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     47 | T3S1_G_G_v1/G_G4_coppock__tf1_e200_t15                     | NQ     | momentum oscillators (MACD/ROC/TSI/elder)                   | intraday  |        2.8  |       21070.3 |      1.88 |         0.92 |     1.41 |        2.86 |      191939 |       0.51 |        0.46 |        0.38 |    0.08 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |
|     48 | T4B/ES_B1_dip_rsi10_rsi65_stop3                            | ES     | mean-reversion/fade                                         | multi-day |        2.8  |       14970.5 |      2.42 |         2.09 |     0.45 |        2.8  |      179982 |       0.1  |        0.01 |        0.18 |    0.16 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     49 | T3S1_G_G_v1/G_G1_pxma_kindZLEMA_n10_tf5_e200_t15           | NQ     | trend: MA cross / price-vs-MA                               | intraday  |        2.8  |       22771.2 |      1.99 |         1.05 |     1.39 |        2.85 |      170555 |       0.47 |        0.43 |        0.36 |    0.04 | T1 (3 spans +, WF t>=2)    | NT8-BARS (source states codable; identity test pending) | crit_ok/DEAD    |
|     50 | T3S1_G_G_v1/G_G5_vwap_anchor2_slope_n0_tf5_eNone_none      | NQ     | volume-based trend (OBV/VWAP)                               | intraday  |        2.78 |       15423.1 |      0.2  |        -1.9  |     0.33 |        2.86 |      120563 |      -0.1  |       -0.05 |       -0.05 |    0.01 | F-WFPRE (WF-PRE <=0)       | NT8-BARS (source states codable; identity test pending) | crit_fail/DEAD  |

## 5. Top 20 NQ intraday books beside ST, HM, pair and WT (same windows; library rows re-costed to the live approximation; DS2_* rows at live P9 cost)

#### H. Top 20 NQ intraday books beside ST/HM/WT
|    | book                                                     | kind                |   HOLD_sh |   HOLD_mean_wk |   WF_sh |   X_sh |   HOLD_maxdd |   corr_DS2 |   plc_p |
|---:|:---------------------------------------------------------|:--------------------|----------:|---------------:|--------:|-------:|-------------:|-----------:|--------:|
|  0 | T3S1_G_G_v1/G_G3_chandelier_n22_k2.0_tf1_eNone_t5        | library NQ intraday |      3.76 |       26110.4  |    1.62 |  -0.32 |       165404 |       0.53 |    0.01 |
|  1 | T3S1_G_G_v1/G_G4_elder__tf5_eNone_delta                  | library NQ intraday |      3.65 |       27196.3  |    2.25 |  -2.39 |       347927 |       0.15 |    0.05 |
|  2 | T3S1_G_G_v1/G_G4_elder__tf5_eNone_none                   | library NQ intraday |      3.54 |       24062.4  |    2.59 |  -2.08 |       313848 |       0.19 |    0.03 |
|  3 | T3S1_G_G_v1/G_G1_pxma_kindDEMA_n50_tf1_eNone_t5          | library NQ intraday |      3.43 |       21426.8  |    1.66 |   0.54 |       140361 |       0.57 |    0.02 |
|  4 | T3S1_G_G_v1/G_G1_macross_kindSMA_f9_s21_tf1_eNone_t5     | library NQ intraday |      3.36 |       21444.4  |    1.82 |   1.04 |       184660 |       0.53 |    0.01 |
|  5 | T3S1_G_G_v1/G_G5_obv_n60_tf5_eNone_delta                 | library NQ intraday |      3.26 |       22141.5  |    2.26 |   1.12 |       211149 |       0.43 |    0.01 |
|  6 | T3S1_G_G_v1/G_G4_roc_n60_tf1_e200_delta                  | library NQ intraday |      3.23 |       21941.4  |    2.47 |   1.34 |       154879 |       0.44 |    0.22 |
|  7 | T3S1_BOOKS_B/B_HM_24_90_200                              | library NQ intraday |      3.22 |       29228.6  |    1.97 |  -1.39 |       340146 |       0.3  |    0.09 |
|  8 | T3S1_G_G_v1/G_G3_squeeze__tf1_e200_t15                   | library NQ intraday |      3.18 |       20238.6  |    1.88 |   2.05 |       153272 |       0.45 |    0.01 |
|  9 | T3S1_G_G_v1/G_G1_pxma_kindWMA_n10_tf5_e200_t15           | library NQ intraday |      3.18 |       22836.9  |    2.02 |   0.82 |       121114 |       0.43 |    0.03 |
| 10 | T3S1_G_G_v1/G_G4_macd_f5_s35_g5_modezero_tf1_e200_t15    | library NQ intraday |      3.16 |       22074.4  |    2.4  |   0.5  |       181599 |       0.49 |    0.07 |
| 11 | T3S1_G_G_v1/G_G3_ichi_t7_k22_sb44_modecloud_tf1_e200_t15 | library NQ intraday |      3.15 |       28411.6  |    2.2  |   0.73 |       152097 |       0.45 |    0.05 |
| 12 | T3S1_G_G_v1/G_G1_macross_kindWMA_f9_s21_tf1_eNone_t5     | library NQ intraday |      3.15 |       20446.8  |    1.64 |   0.79 |       153606 |       0.53 |    0.01 |
| 13 | T3S1_G_G_v1/G_G3_alligator__tf1_e200_t5                  | library NQ intraday |      3.13 |       19372.6  |    2.12 |   0.16 |       173095 |       0.63 |    0.02 |
| 14 | T3S1_G_G_v1/G_G1_pxma_kindHMA_n100_tf1_eNone_t5          | library NQ intraday |      3.11 |       17109.5  |    1.38 |   0.21 |       166438 |       0.55 |    0.01 |
| 15 | T3S1_G_G_v1/G_G1_pxma_kindSMA_n10_tf5_e200_t15           | library NQ intraday |      3.08 |       17499.5  |    1.68 |   0.26 |       149769 |       0.43 |    0    |
| 16 | T3S1_G_G_v1/G_G4_elder__tf5_e200_t15                     | library NQ intraday |      3.06 |       21594.6  |    1.67 |   1.57 |       199080 |       0.45 |    0.04 |
| 17 | T3S1_G_G_v1/G_G1_macross_kindHMA_f20_s50_tf1_eNone_t5    | library NQ intraday |      3.03 |       22504.1  |    1.89 |   0.79 |       184092 |       0.5  |    0.04 |
| 18 | T3S1_G_G_v1/G_G1_pxma_kindHMA_n10_tf5_e200_t15           | library NQ intraday |      3.03 |       22250    |    1.76 |   1.4  |       226610 |       0.41 |    0.05 |
| 19 | T3S1_G_G_v1/G_G5_obv_n60_tf5_e200_t15                    | library NQ intraday |      3.02 |       20698    |    2.57 |   0.49 |       185526 |       0.5  |    0.02 |
| 20 | ST (library, 8-ct std, 1tick+recost)                     | live-book ref       |      0.64 |        4894.06 |    1.13 |   0.68 |       230148 |       0.58 |    0.66 |
| 21 | HM (library, 8-ct std, 1tick+recost)                     | live-book ref       |      2    |       13851.1  |    1.62 |   1.03 |       287706 |       0.7  |    0.06 |
| 22 | PAIR (library, 8-ct std, 1tick+recost)                   | live-book ref       |      2.36 |       20230.8  |    2.05 |   0.8  |       218180 |       0.74 |    0.14 |
| 23 | WT10 (library, 8-ct std, 1tick+recost)                   | live-book ref       |      2.04 |        8377.4  |    1.76 |   1.77 |       196941 |       0.06 |    0.29 |
| 24 | WT_LIVE (library, 8-ct std, 1tick+recost)                | live-book ref       |      2.53 |       14749    |    1.98 |  -0.16 |       194224 |       0.52 |    0.02 |
| 25 | DS2_ST10_pb (report-scale $, live P9 cost)               | live-book ref       |      1.91 |       16224.7  |    1.8  |   0.97 |       263432 |       0.85 |    0.32 |
| 26 | DS2_HM10_pb (report-scale $, live P9 cost)               | live-book ref       |      1.34 |       10444.8  |    1.36 |   0.71 |       243469 |       0.77 |    0.38 |
| 27 | DS2_WT7_pb (report-scale $, live P9 cost)                | live-book ref       |      0.2  |         774.73 |    0.37 |   0.33 |       225128 |       0.59 |    0.61 |

Additional DS2 reference rows (report-scale $, live cost, per-book locks): **pair ST10/HM10 per-book**: X 1.01, WF-PRE 1.77, WF 1.89, HOLD 2.01 (HOLD mean $27,062/wk, WF mean $24,402/wk, SD $92,858, maxDD $390,605; timing placebo p 0.29). **DS2 ST10/HM10/WT7**: X 0.92, WF-PRE 1.72, WF 1.75, HOLD 1.77 (WF $25,840/wk, SD $106,637, maxDD $537,851; placebo p 0.42). Units differ (library std = 8-contract R=$9,600; DS2 = 10 lots at its own R), so compare Sharpe, not dollars. Reading: the top NQ library books hold HOLD Sharpe 3.0-3.8 versus 1.3-2.4 for the live books, but 4 of the 20 have a negative X-span Sharpe, corr to DS2 is 0.15-0.63 (most 0.4-0.55), and 16 of 20 pass the per-series timing placebo (p <= 0.05), which is no evidence by itself because the 20 are the best HOLD Sharpes of ~31k series (a 5% placebo passes ~1,500 zero-edge series); the live ST/HM/pair have placebo p 0.3-0.4, i.e. their 68-week holdout alone does not beat their own shifted versions either.

#### DS2 books as pool rows

### I. DS2 pool rows (per-book, live cost)
| name            |   l_X_sh |   l_WFPRE_sh |   l_WF_sh |   l_HOLD_sh |   l_WF_mean |   l_WF_sd |   l_WF_dd |   l_HOLD_mean |   corr_DS2 |   corr_ST10 |   corr_HM10 |   corr_WT7 |   trades_wk_WF |   plc_p |
|:----------------|---------:|-------------:|----------:|------------:|------------:|----------:|----------:|--------------:|-----------:|------------:|------------:|-----------:|---------------:|--------:|
| DS2_ST10_pb     |     0.97 |         1.67 |      1.8  |        1.91 |    14249.6  |   57141   |    263432 |      16224.7  |       0.85 |        1    |        0.41 |       0.43 |          25.8  |    0.32 |
| DS2_HM10_pb     |     0.71 |         1.36 |      1.36 |        1.34 |     9981.64 |   53113.5 |    251800 |      10444.8  |       0.77 |        0.41 |        1    |       0.21 |          23.73 |    0.38 |
| DS2_WT7_pb      |     0.33 |         0.53 |      0.37 |        0.2  |     1428.19 |   27652.1 |    244807 |        774.73 |       0.59 |        0.43 |        0.21 |       1    |          37.9  |    0.61 |
| DS2_ST8_pb      |     0.97 |         1.67 |      1.8  |        1.91 |    11399.7  |   45712.8 |    210746 |      12979.8  |       0.85 |        1    |        0.41 |       0.43 |          25.8  |    0.32 |
| DS2_HM8_pb      |     0.71 |         1.36 |      1.36 |        1.34 |     7985.31 |   42490.8 |    201440 |       8355.82 |       0.77 |        0.41 |        1    |       0.21 |          23.73 |    0.38 |
| DS2_ST12_pb     |     0.97 |         1.67 |      1.8  |        1.91 |    17099.5  |   68569.2 |    316119 |      19469.7  |       0.85 |        1    |        0.41 |       0.43 |          25.8  |    0.32 |
| DS2_HM12_pb     |     0.71 |         1.36 |      1.36 |        1.34 |    11978    |   63736.2 |    302160 |      12533.7  |       0.77 |        0.41 |        1    |       0.21 |          23.73 |    0.38 |
| DS2_ST14_pb_s14 |     0.43 |         1.53 |      1.79 |        2.04 |    16840.9  |   67895.3 |    327441 |      19573.3  |       0.8  |        0.93 |        0.41 |       0.38 |          30.34 |    0.19 |
| DS2_HM10_pb_s14 |     0.87 |         1.34 |      1.49 |        1.62 |    13491    |   65386.7 |    397395 |      16046.7  |       0.75 |        0.42 |        0.93 |       0.25 |          26.87 |    0.23 |
| DS2_WT7_pb_s14  |     0.33 |         0.53 |      0.37 |        0.2  |     1428.19 |   27652.1 |    244807 |        774.73 |       0.59 |        0.43 |        0.21 |       1    |          37.9  |    0.61 |

Note: ST8/12 and HM8/12 carry the same Sharpes as ST10/HM10 (lots scale; per-book locks scale with R).


## 5b. T-B top 20 NQ intraday books (new DS3 books, live cost) beside ST10, HM10 and the pair

Source `autopilot/DS3_TB_top20.md` / `l2vast/ds3/out/TB_top20.parquet` (series `l2vast/ds3/out/series/TB_*.parquet`; report `autopilot/DS3_TB.md`: 279 cells, 0 PASS / 4 CANDIDATE / 275 DEAD). Cost: P9-style live (market 0.995 pt, stop 1.01 pt, $4.84/lot), closed-trade approximation of the per-book locks. "pool pct NQ intraday" = percentile of the book's holdout Sharpe within the census NQ-intraday library pool; "shift-null HOLD p95" and "rank vs null" = timing-destroyed placebo for that book. Reading: the best T-B holdout Sharpe is 1.34 against ST10 1.93, HM10 1.35 and the pair 2.01; the library top-20 NQ books (section 5) show 3.0-3.8 but that sits at the chance level for a 31k-series pool, whereas T-B's best of 279 (1.34) is below the T-B best-of-N null mean (1.64) and nothing exceeds its p95 (2.21). No T-B book beats the live books and none is above chance.

All 10 T-B preregs (279 cells, trials in ledger: see DS3_TB.md). Best-of-N timing-destroyed null over 279 cells: holdout Sharpe of the best cell in a null draw has mean 1.64, p95 2.21 (100 draws). Locks are the closed-trade approximation, not the exact engine.

| book | WF $/wk | WF SD | WF Sh | HOLD $/wk | HOLD Sh | L8W | IS | span23 | tr/wk | corr ST/HM/pair | shift-null HOLD p95 | rank vs null | pool pct NQ intraday | > best-of-N p95 | DSR | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST10 (10 lots, DS2 per-book locks) | 14,350 | 57,331 | 1.80 | 16,463 | 1.93 | 22,235 | - | - | - | - | - | - | - | - | - | benchmark |
| HM10 (10 lots, DS2 per-book locks) | 10,052 | 53,295 | 1.36 | 10,598 | 1.35 | 8,765 | - | - | - | - | - | - | - | - | - | benchmark |
| PAIR (10 lots, DS2 per-book locks) | 24,402 | 92,858 | 1.89 | 27,062 | 2.01 | 31,000 | - | - | - | - | - | - | - | - | - | benchmark |
| TB1_ST_k15_P60_N | 10,933 | 78,905 | 1.00 | 17,494 | 1.34 | -6,235 | 2,692 | -2,415 | 16.3 | 0.40/0.26/0.40 | 0.63 | 1.00 | 0.84 | False | 0.030 | CANDIDATE |
| TB9_RENKO_c2_k1_P60_N | 9,418 | 65,953 | 1.03 | 13,025 | 1.34 | 47,774 | -8,609 | -6,056 | 18.4 | 0.40/0.40/0.48 | 0.29 | 1.00 | 0.84 | False | 0.040 | CANDIDATE |
| TB5_RSI_k15_P60_FV | 3,985 | 69,979 | 0.41 | 14,384 | 1.31 | -6,562 | -891 | -343 | 12.9 | 0.39/0.41/0.48 | 0.90 | 0.98 | 0.83 | False | 0.003 | DEAD |
| TB3_EMA_k3_P60_FV | 3,339 | 75,980 | 0.32 | 15,315 | 1.24 | 4,212 | -16,549 | -15,441 | 32.4 | 0.28/0.34/0.37 | 0.74 | 0.99 | 0.82 | False | 0.002 | DEAD |
| TB2_WIL_k5_A3_FV | 16,764 | 118,377 | 1.02 | 19,529 | 1.20 | -6,999 | -12,651 | -11,771 | 19.7 | 0.28/0.39/0.39 | 1.32 | 0.91 | 0.81 | False | 0.024 | DEAD |
| TB4_DON_k15_P60_N | 8,491 | 83,191 | 0.74 | 15,506 | 1.18 | -2,165 | -3,317 | -4,093 | 10.4 | 0.31/0.48/0.47 | 0.77 | 0.98 | 0.80 | False | 0.011 | DEAD |
| TB8_CLIM_k2_P60_FV | -85 | 31,857 | -0.02 | 5,532 | 1.11 | -4,423 | -10,898 | -10,286 | 12.0 | 0.19/0.07/0.15 | 0.09 | 1.00 | 0.79 | False | 0.000 | DEAD |
| TB9_RENKO_c1_k1_T_N | 4,412 | 66,298 | 0.48 | 10,200 | 0.99 | 37,131 | -6,975 | -6,406 | 30.3 | 0.27/0.31/0.34 | -0.01 | 1.00 | 0.75 | False | 0.004 | DEAD |
| TB3_EMA_k15_P60_N | 8,162 | 82,064 | 0.72 | 11,956 | 0.93 | -8,005 | 1,913 | 3,331 | 9.2 | 0.43/0.48/0.54 | 0.60 | 0.98 | 0.74 | False | 0.009 | DEAD |
| TB10_DST_N3_S3.0 | 178 | 2,986 | 0.43 | 363 | 0.92 | 1,404 | 200 | 237 | 0.1 | 0.04/-0.14/-0.05 | 1.60 | 0.80 | 0.73 | False | 0.004 | DEAD |
| TB5_RSI_k15_A3_N | 11,028 | 88,244 | 0.90 | 13,254 | 0.91 | 17,156 | -9,909 | -11,086 | 14.3 | 0.36/0.37/0.44 | 0.86 | 0.96 | 0.73 | False | 0.021 | DEAD |
| TB10_DST_N3_S2.0 | 329 | 4,145 | 0.57 | 538 | 0.90 | 2,106 | 300 | 355 | 0.1 | 0.04/-0.13/-0.05 | 1.60 | 0.80 | 0.73 | False | 0.007 | DEAD |
| TB4_KEL_k15_P60_FV | 6,253 | 68,392 | 0.66 | 9,473 | 0.85 | -20,653 | -3,385 | -3,926 | 9.5 | 0.29/0.36/0.39 | 0.93 | 0.93 | 0.71 | False | 0.007 | DEAD |
| TB9_RENKO_c5_k1_A3_N | 14,628 | 121,657 | 0.87 | 16,284 | 0.85 | -11,067 | 2,288 | 7,866 | 7.2 | 0.16/0.29/0.26 | 0.66 | 0.98 | 0.71 | False | 0.016 | CANDIDATE |
| TB4_KEL_k3_P60_N | 4,716 | 70,106 | 0.49 | 8,887 | 0.76 | 18,400 | -14,717 | -14,468 | 31.4 | 0.32/0.26/0.34 | -0.21 | 1.00 | 0.69 | False | 0.004 | DEAD |
| TB6_VWAP_k15_P60_N | -1,164 | 75,402 | -0.11 | 8,968 | 0.74 | -13,176 | -2,008 | -2,096 | 23.0 | 0.47/0.40/0.52 | 0.01 | 0.99 | 0.68 | False | 0.000 | DEAD |
| TB5_RSI_k15_A3_FV | 6,171 | 89,412 | 0.50 | 10,515 | 0.72 | -203 | -9,521 | -9,928 | 11.7 | 0.30/0.30/0.35 | 0.95 | 0.89 | 0.67 | False | 0.004 | DEAD |
| TB6_VWAP_k15_T_N | -2,257 | 62,570 | -0.26 | 6,435 | 0.71 | -5,477 | -7,666 | -7,753 | 28.0 | 0.49/0.35/0.50 | -0.23 | 1.00 | 0.67 | False | 0.000 | DEAD |
| TB2_WIL_k15_P60_N | 7,014 | 78,174 | 0.65 | 7,438 | 0.66 | 985 | -6,714 | -8,970 | 16.7 | 0.33/0.29/0.37 | 0.71 | 0.93 | 0.66 | False | 0.008 | DEAD |
| TB3_EMA_k15_P60_FV | 1,767 | 72,829 | 0.17 | 6,777 | 0.64 | -32,755 | -1,137 | -1,653 | 16.1 | 0.37/0.44/0.48 | 1.15 | 0.78 | 0.65 | False | 0.001 | DEAD |


## 6. Pool (deliverable for track agents and the DS3 lead)

`l2vast/ds3/out/pool.parquet`: one row per series (31,098): id, name, family, instrument, mechanism_family, horizon, bar_type, source, series_kind (library | ds2_asm), unit, size_basis, stored_cost, live_cost_adj_per_active_day_usd, tier, exec_tag, is_ds2_component, lead_tag (V5 / D2 prior-day break / dip-buy / WT / DS2), plc_p, corr_DS2/ST10/HM10/WT7 (WF weekly), s_* (stored cost) and l_* (re-costed) mean/sd/sh/t/dd/worst/n/act for windows X, WFPRE, WF, HOLD, series_file. Daily + weekly paths: `series/<id>.parquet` (day, wk, pnl_stored, pnl_live; unit = library std size, DS2 rows = report-scale $ at stated lots), and wide matrices `daily_pool_live.parquet` (day x id) and `weekly_pool_live.parquet` (ISO wk x id), live column = re-costed. Executability tags: NT8-BARS 30,690 (source says codable; identity test pending), L2/TICK-DEPENDENT 283, UNCONFIRMED 59, UNKNOWN 43, NOT-DELIVERABLE 9, DS2-RULE-CHANGE 4, NT8 LIVE 10. ST/HM/WT inclusion: ids for `ST`, `HM`, `PAIR`, `WT10`, `WT_LIVE` (= WT_MODAL: 1-min ATR20 x 2.0 EMA100 TH 10/2/30), `WT_B10`, `WT_TOP1`, `WThist*` and DS2_ST/HM/WT at 8/10/12/14 lots. Not in the pool (in `census_all.parquet` with tier EXCL-*): void, overlay and no-data rows.

Caveats for users of the pool: (i) library std units differ from DS2 report-scale dollars; (ii) re-cost is a per-active-day approximation, a lower bound on trades; (iii) tiers are descriptive, not V2 verdicts (a PASS needs placebo, neighbours, identity test, executability); (iv) the 40,041-row library contains many near-duplicates of the same trades, so counts overstate independent evidence; (v) the T3S1_G family (5,276 series, vol-matched, "B10 NQ harness, opposed cost") dominates the NQ top lists: confirm their cost model before trusting them.



## 7-8. Sections 1.2 / 1.3 (PAPER-ALL and the MBO seven)

(verbatim from `l2vast/ds3/out/SEC_1_2_1_3.md`)

# DS3 census, sections 1.2 (PAPER-ALL / forward shadows) and 1.3 (MBO seven)

Written by fork F1 of D3C, 2026-10-26. Read-only census; nothing was run on the live side. Machine-readable: `l2vast/ds3/out/paperall_register.csv` (255 rows) and `l2vast/ds3/out/mbo7.csv`.

## 1.2 PAPER-ALL and forward shadows: record to date

There are TWO registries and they must not be confused.

### A. struct48 PAPER-ALL register (V2 sec 5): 50 cells, all with 0 official weeks

Sources: `outputs/autopilot/FORWARD_REGISTER.md` (generated 2026-10-25 18:12 ET), `outputs/autopilot/forward/series/PAPERALL_CELLS.json` (50 cells + 1 removed TEST_dryrun; frozen expectation, sha256 per cell).
Official forward weeks start at 2026-W44 (Mon 2026-10-26); W43 (10-19..10-23) is informational and never counted. The live tape ends 2026-10-23, so **every one of the 50 cells has 0 official weeks, 0 trades, realised $0 and no z.** All carry "ON TRACK (0 weeks live)" by construction. Verdict rules (FORWARD_REGISTER.md header): PROMOTE >= 6 weeks and z >= -1 and sign right; RETIRE >= 8 weeks and z < -2; BEHIND z < -1.

Composition by tier (from the register, counted from the csv): PASS 15, PASS (was CANDIDATE) 6, CANDIDATE 19, CANDIDATE (was PASS) 4, CANDIDATE by user ruling 1, DEAD (was PASS) 4, DEAD (was CANDIDATE) 1 = 50. 14 rows are flagged MERGED into another exposure (B05/B06/B07 and BK1 into B01_SetB; NM_E_ES_RSI2_t10, NM_E_NQ_RSI2C_s20, RSI2C_s20 into DIPBUY_RSI2_2lot), so independent tests are fewer than 50.

Evaluator status: 23 cells have a live script evaluator (W43 informational $ shown for 19 of them, none counted); 27 are AWAITING or NOT EVALUABLE (e.g. all ORB_ASIA_15/30 sizes and ON_none: no evaluator wired; GSHORT_t90: needs Set A daily P&L on the extended calendar; YM_RSI2_t10: no extended 1-min source for YM; T4.2_Y4, B05-B07 variants: awaiting). These cannot produce a forward number in W44 until an evaluator is wired.

Expectation of the DS3-relevant sleeves (PAPERALL_CELLS.json `expect_mean_wk`, $/wk at registered size): DIPBUY_RSI2_2lot 3,091; RSI2_t10 10,197; RSI2T_t10 8,882; NM_E_ES_RSI2_t10 6,279; NM_E_RTY_RSI2_t10 8,005; YM_RSI2_t10 8,274; NM_E_NQ_IBS_t20_n1 4,232; ORB_ASIA_15_v1__s60 at 0.25/0.5/1.0 = 4,069/8,138/16,276; ORB_ASIA_30_v1__s60 4,001/8,001/16,003; NM_E_GSHORT_t90 2,970; T14_S_s50_t1.5_n14 7,914; B01_SetB +8,131 vs Set A (SD of difference 44,800).

Set A reference in the same file: expectation $24,975/wk, SD $104,500; W43 realised -$184,580 (39 trades, z -2.01, informational). Set A vs B forward column: W43 A -134,500 vs B -86,278 (flat natural fills, informational).

### B. m2 PAPER-ALL league (older registry, frozen 2026-10-17): 205 rows

Sources: `outputs/autopilot/forward/m2/LEAGUE.md`, `LEAGUE.json`, `PRED_PAPERALL.json`, `PAPERALL_WEEKS.csv` (asof 2026-10-16). Zero-capital rows at a common size of 20% of pair risk ($12,534/wk SD); weights fit 2025-08-01..2026-07-31, OOS series cut 2026-10-09.

- Status: 171 counted (CLEAN 76, FLAGGED-LIVE-FORM 92, PROVISIONAL 2, FAIL 1), 9 LOOKAHEAD-VOID and 25 REPORT-ONLY (not counted). 
- "Weeks scored" is the post-cut partial week 2026-W42 only (days 10-12..10-16): 158 rows have >0 weeks scored, 47 rows 0 (STALE or no series), 98 rows have n_eff 1.0. **None of this is official forward evidence**: the freeze (2026-10-17) came after W42 had been traded, and the V2 official clock starts W44. Treat as at most 1 informational week; all kill/promotion rules need >= 6 weeks ("n/a (<6 weeks)" for every row).
- Result on the 140 counted rows with a scored week: cumulative sum +$165,056; 74 positive; mean cum z +0.10, SD 0.70 across rows; 5 rows z >= 1.645 (nominal), 8 rows z <= -1; position vs band: 146 within band, 4 above 95th pct, 8 below 5th pct (all 8 below are within the "chance" 5% expectation of 12 for 171 rows). The best-of-N repeated-look z line is ~3.3, crossed by **0 rows**; nominal promotions 0, CONFIRMED (corrected) 0, kill-watch/off 0.
- Best-scoring rows are the M2 non-time-bar family (M2-A-A9-stk2-V1 z +2.71, $34,010; M2-A-A9-ooat-V1 +2.66; M2-B-A9-ffw-Range +2.22), all FLAGGED-LIVE-FORM and the Range/Renko ones carry "CONSTRUCTION-ARTIFACT" notes, so they are not DS3 candidates. Worst: B1leg_BTC z -1.98 (-$24.8k), B1 -1.94, N10-CSVOL-MENR -1.75, B7XC -1.52, N7-MRZ-NQ -1.40.
- 47 rows have 0 weeks scored; 106 rows carry a STALE flag (matrix not extended past 2026-10-12/13).
- Frozen LEAD forward confirmation table (LEAGUE.md): S21P_NQ_span_asym+can_imb410 and S39_SW10_NQ, 0 of 26 weeks, "needs forward L2 feed". S130_ES (`forward_s130_es`, SHADOW_S130.json), DS15 9_tf5_size8 and Track P are REPORT-ONLY shadows with clock from 2026-W44, 0 weeks. 
- Pair reference series in LEAGUE.md: BENCH3 weekly Sharpe 1.90, maxDD $497,048 (history, all-in net $5.73M).

Bottom line 1.2: no PAPER-ALL cell has an official week. The only forward-style numbers are one informational W43 (struct48 cells, Set A z -2.01) and one partial pre-freeze W42 (m2 league, mean z +0.10: indistinguishable from chance). Nothing here supports or refutes any candidate for DS3; the registers are an expectation ledger, not evidence.

## 1.3 The MBO seven

**Finding that changes the premise: there is no paper-soak P&L for the MBO seven on this box.** No MBO trades file exists in `data/live/` (files there: StratTrades_DualStrat2/DualStrat (ST, HM, WT only), DualStrat_<sim-acct>, DualStrat_<sim-acct>, K4Trades_*). MBO is not in PAPER-ALL (`outputs/autopilot/FR_SEC4.md`: "MBO seven ... provisional | no H2 data ... | not registered"; `REPORT_EXTENSION_20261017.md`: "series end 2026-02-06 (no MBO beyond)"; `REPORT_EXTENSION_RESCORE.md`: "MBO has no data"). The only post-Feb-2026 MBO artefact is `outputs/h2/emission_latency_sep24_oct15.csv.gz`: 2,655,277 model-pass timestamps for the seven setups, 2026-09-24..2026-10-15 (per-setup passes: tb_long_xgboost_Q750 1,760,525; histgb_Q675, catboost_Q625, lightgbm_Q700 213,738 each; xgboost_Q725 108,034; histgb_Q700 and extratrees_Q575 72,752 each). That shows the models were emitting live scores on an execution server, but it contains no fills or P&L. So "P&L to date vs expectation" can only be given for the backtest; **realised paper P&L = not available (0 rows on box)**; to be obtained from the execution server if it logs trades (not on this box).

Backtest series: `outputs/h2/NQ7_3Y_TRADES_RECONSTRUCTED.parquet` (4,314 trades, 2023-02-09..2026-02-06; reconstructed from frozen Stage-6 scores + NQ BBO tape, verified to count and net vs `NQ230_3Y_RESULTS.csv`; 25 ms latency, 1 tick slippage per fill). P&L below = `net_usd_mnq` x 10 (MNQ-equivalent costs expressed per NQ contract, as in REPORT_MBO_VS_PAIR.md); with true NQ costs (`net_usd_nq`: $4.50 + 1 tick/side) results are lower. Library copies: `outputs/library/MBO7*.parquet`, `fam_T3S1_MBO.parquet`. Sizes: 1 NQ per setup (7 contracts when all on). "Hold" = 2026-02 window available (2025-07-01..2026-02-06, about 31 weeks, a backtest, not forward). The span 2023-04..2024-01 is inside the IS period of the original selection (setups were frozen from Stage 6, which was fit before; it is "never scored by DS3", not never seen by MBO research).

| setup | trades | trades/wk (2024-02+) | mean $/wk (2024-02..2026-02) | SD $/wk | weekly Sharpe | hold 2025-07+ net $ / Sharpe | 2023-04..2024-01 net $ / Sharpe |
|---|---|---|---|---|---|---|---|
| H120000_competing_dir_xgboost_Q725 | 341 | 2.6 | 882 | 7,308 | 0.87 | 2,340 / 0.24 | 12,656 / 0.90 |
| H250_tb_long_xgboost_Q750 | 483 | 3.7 | 452 | 7,957 | 0.41 | 24,534 / 1.03 | 19,977 / 1.69 |
| H300000_competing_dir_extratrees_Q575 | 810 | 6.0 | 620 | 7,525 | 0.59 | 73,241 / 2.56 | 18,742 / 0.95 |
| H300000_competing_dir_histgb_Q700 | 814 | 4.3 | 558 | 3,833 | 1.05 | 4,223 / 0.51 | -563 / -0.03 |
| H60000_competing_dir_histgb_Q675 | 342 | 2.5 | 1,138 | 7,395 | 1.11 | -6,270 / -0.82 | 3,952 / 0.41 |
| H60000_y_exec_best_catboost_Q625 | 1,072 | 7.0 | 961 | 7,513 | 0.92 | -10,322 / -1.16 | 6,472 / 0.29 |
| H60000_y_exec_best_lightgbm_Q700 | 452 | 3.6 | 755 | 7,160 | 0.76 | 2,512 / 0.31 | -5,259 / -0.47 |
| **all seven** | 4,314 | 29.8 | 5,367 | 38,967 | 0.99 | 90,258 / 1.78 | 55,977 / 0.84 |

(The "hold" figures are over the last ~31 weeks of backtest; three of seven setups are negative or near zero there, and the all-seven total is driven by extratrees_Q575 (+73k of 90k). The trades/wk column is the backtest 1-NQ rate before the live admission gate; all seven are time-exit books with a 16:59 ET flat.) Other earlier numbers: all-seven 1 NQ/setup overlap Sharpe 0.95, maxDD $231k, worst week -$136k, corr to the pair -0.005 (REPORT_MBO_VS_PAIR.md); random-entry null rank 1.00 (Sharpe 0.95 vs null p95 0.34, CANDIDATES.md). Verdict on record: PROVISIONAL SURVIVOR only, no H2.

**Executability (every setup): L2-DEPENDENT AT RUNTIME, NOT deliverable to NT8 chart data.** Reason: the models' inputs are order-book features built from MBO/mbp data at 1 s stride (`outputs/h2/02_unified_features_labels.py`: imbalance_1/3/5/10, OFI, signed flow, sweep counts, replenishment failure, Hawkes imbalance, vpin proxy, micro bias, liquidity support), the signal timestamps are on a sub-second grid (entries at signal + 25 ms, fills at the next BBO event), and the live emitter runs on the execution server. These cannot be computed from NT8 1-minute or tick bars. Under the DS3 rule (section 3 of the directive) they are NOT DELIVERABLE for DS3 and can stay as MBO setups on the execution server. The implied trade timing (entries on arbitrary seconds, holds of 250 ms to 6 h; five of seven with holds >= 60 s) does not change that.


## 9-10. Sections 1.4 / 1.5 (K4 and the STATUS leads)

(verbatim from `l2vast/ds3/out/SEC_1_4_1_5.md`)

# DS3 census sections 1.4 and 1.5 (fork F2 of D3C, 2026-10-26)

Descriptive census. No holdout look function called (`log_holdout_look` not used). Where holdout numbers appear they are descriptive re-reads of stored library series (the holdouts of these leads were already looked at by earlier tracks, see their reports). Code: `l2vast/ds3/code/f2_leads.py` (output `l2vast/ds3/out/f2_leads.json`), K4 table `l2vast/ds3/out/k4_cells.csv`. Library stored cost: 1 tick/side + $4.36/contract (ES/NQ 4.84 not applied: stored series, not re-costed; no trade counts in the library). Series are volmatch/standard-size; the sleeve test rescales to weekly SD ratio vs Set A (s48score.sleeve_score, benchmark Set A = 14/14 live locks, Sharpe 1.72 on WF, NOT DS2 ST10/HM10/WT7).

## 1.4 K4 cells not in the live K4 file

**What "live K4 file" is.** Three candidates were found: (a) `data/live/K4Trades_<acct>.csv` / `K4Trades_<sim-acct>.csv` are NT8 trade logs (only 2026-10-22 has entries; cells seen: R2_FULL, R2_FULL-VIX, R3_ridge_0.08_1, R4_fixed_2_0.06, RX5_ens, ES_HEDGE, plus TEST_* rows on <sim-acct>; most days are NOFILE) - too thin to define a "file"; (b) the retired box writer `outputs/k4/k4_writer.py` (26-cell pack, 18 cells representable, `RETIRED_26_CELL_LOGIC_SEE_vps_v4`); (c) the deployed family: **17-cell K4-EXACT family, `outputs/k4/vps_v4/CELLS_WEIGHTS_17.csv`** (clock 16:17 ET; `outputs/autopilot/REPORT_K4_EXACT.md`). I use (c). Pack of 26 = `outputs/codepack/K4H/CELLS_WEIGHTS.csv`. The 9 cells not in the live 17 were removed as research errors (look-ahead) by the user decision of 2026-10-19 (REPORT_K4_EXACT sec 2; DECISIONS.md "RESEARCH ERRORS"); they hold 53% of the pack's tilt weight.

Scores below are weekly Sharpe (zero-filled weeks, library series, stored cost, volmatch size) from the library files named in `k4_cells.csv`; IS = 2023-04..2024-01 (never-scored span), WFPRE 2024-02..2025-06, HOLD 2025-07+ (descriptive re-read).

| cell | pack weight | exactness verdict (K4_EXACT_CELLS.csv) | library verdict | Sh 2023-04..2024-01 | Sh WF-PRE | Sh HOLD | HOLD mean $/wk (vol-matched) | Sh WF |
|---|---|---|---|---|---|---|---|---|
| R12_d2_1_0.08_longonly | 0.053 | LOOKAHEAD_HARD (same-day SKEW, end-of-day index) | LEAD | -1.16 | 2.06 | 2.78 | 8,596 | 2.34 |
| R12P_d2_1_0.08_longonly | 0.053 | LOOKAHEAD_HARD | see report | -1.16 | 2.06 | 2.78 | 8,596 | 2.34 |
| R10_0.1_0.0 | 0.063 | LOOKAHEAD_HARD (filled at 16:00 close, filtered by 16:17 p) | LEAD | 1.57 | 1.55 | 2.68 | 18,319 | 2.13 |
| R9_2.0_4 | 0.060 | LOOKAHEAD_SAME_BAR (IBS from 16:00 bar, filled at same close) | LEAD | 1.69 | 1.72 | 2.46 | 15,438 | 2.10 |
| RX1_k4lo_half | 0.062 | LOOKAHEAD_SAME_BAR | LEAD | 1.65 | 1.94 | 2.52 | 17,406 | 2.24 |
| RX2_2_2_0.5 | 0.062 | LOOKAHEAD_SAME_BAR | LEAD | 1.69 | 1.72 | 2.51 | 15,867 | 2.13 |
| RX3_r5b_3 | 0.063 | LOOKAHEAD_SAME_BAR | LEAD | 1.69 | 1.72 | 2.54 | 16,224 | 2.14 |
| RX8_10_rsi65 | 0.058 | LOOKAHEAD_HARD (signal kept only if a stop/RSI exit occurs within 7 days = selection on the future) | LEAD | 2.29 | 1.14 | 2.74 | 23,258 | 1.98 |
| RX11_F_shorten | 0.060 | LOOKAHEAD_SAME_BAR | NO | 1.83 | 1.67 | 2.40 | 15,174 | 2.05 |

Reading: **all nine are NOT DELIVERABLE for DS3** (look-ahead by construction; their Sharpes are inflated by the error, not evidence of edge). R9/RX2/RX3 are near-duplicates (identical IS/WF-PRE stats). Do not enter these in the pool as candidate books; if tagged, tag `LOOKAHEAD_REMOVED`. R12/R12P additionally have a negative 2023-04..2024-01 span. The 17 live cells are one family (K4_FAMILY.md: evidence not additive, ~3.9 effective independent trials of 145; best-of-F at F_eff 594-1208 about 0 per REPORT_K4_EXACT sec 3; hedged Sharpe 1.16 / unhedged 1.42 for the 17-cell family; edge dies when ES-hedged beta-neutral per K4_FAMILY.md; beta/long-only index timing; needs 16:17 ET features incl. VIX-family closes, i.e. an external signal file, not NT8 chart data alone -> likely not a DS3 book by the NT8-chart-data rule). The 17 live cells' own scores are in `k4_cells.csv` (in_live17 = True) for the pool.

## 1.5 Leads from autopilot/STATUS.md under V2

Method: the leads' library series were read descriptively with `s48score.sleeve_score` (stage final, enforce=False, track DS3_CENSUS_DESC) and `s48score.verdict(..., 'sleeve')`. verdict() needs a placebo rank and neighbour agreement in the V2 form; none of these leads has been re-scored in STRUCT48 rows (grep of `l2vast/struct48/rows/*.json`: no V5P1, T4D, C11DIP cells), so **the computed verdict is DEAD-provisional with `needs` = placebo>=0.90, neighbours_agree for every lead**. That is "missing evidence", not a measured failure. What the data do support is the sleeve criterion (standalone holdout mean > 0, marginal Sharpe up vs Set A at ratio 0.25 and 0.5, corr <= 0.5), reported below. Multiplicity: leads were selected from large grids (V5: 5,480 books at T3 S1 then 2,016 cells in V5P2; T4 D 276 cells; C11/T4B dip 64+ cells), PRED corrected trial total 27,682 + STRUCT48 ledger; family counts below are chance-referenced (about half of random-sign series have positive holdout).

| lead | library series | object under V2 | sleeve criterion (descriptive) | V2 verdict state | legacy evidence |
|---|---|---|---|---|---|
| 5-min NQ trend family / V5 | `V5P1/*` (11 books + `V5P1/ENSEMBLE5`); V5P2 lead `V5P2/c0832` (MACD(19,39) zero-cross 5-min, 120-min stop); `V5P2/c0000..c2015` | signal (standalone) or sleeve | V5P1: 11/12 have holdout mean > 0, 11/12 meet the criterion at ratio 0.25 and 0.5 (the exception `G1_macross_kindWMA_f50_s200_tf1`: HOLD Sh -0.13); median corr to Set A -0.18. ENSEMBLE5: Sh IS -0.44 / WF-PRE 0.58 / HOLD 1.32, corr -0.20, port Sh 1.72 -> 2.00 at 0.25. But IS (2023-04..2024-01) mean > 0 for only 4/12 and the edge is a 2025-07+ result. c0832: IS 2.66, WF-PRE 1.16, HOLD 0.74, crit True. V5P2 grid (2,016 cells): 918 hold>0, 455 meet criterion at 0.25 = chance level for a selected grid | DEAD-provisional (no placebo, no neighbours); sleeve criterion met by the ensemble and c0832 | T3 S1 chose 11 of 5,480; V5 P1 (CANDIDATES.md) = LEADS, fails 2x slippage (clean uplift +0.07) and plateau (0.73 < 0.75); V5 P2 "does not survive as a family" (real clean uplift +0.193 = null median +0.190); C3-H3 ruled out on 2013-2022 (Sharpe +0.07). Library `verdict` LEAD |
| NQ prior-day high/low break (D2 family, T4 D) | `T4D/D*_D2_*` (72 cells; top 3 `D54`, `D58`, `D82`) | signal / sleeve | 38/72 hold>0, 25/72 meet criterion at 0.25 (19 at 0.5); median corr 0.03. D54: IS 3,236 $/wk, WF-PRE 131, HOLD 4,383 (Sh 1.79/0.08/2.09); D58: Sh 1.08/0.36/1.27; D82: Sh 0.31/0.72/1.82; all corr ~0.0-0.1, crit True | DEAD-provisional; D54 edge sits in IS and HOLD, WF-PRE near zero | T4 D: 0 SURVIVOR / 0 INSURANCE of 276, top cells "selected after the fact among 276", null ranks 0.99-1.00; D2 here is NOT `D2E9/*` (that is the ddmin/D2 direction-2 family, all 37 NO: fails verification) |
| HM-heavy split (D1 F3, ST:HM 4:12) | no per-split library series (only `D1F4`, `D1F8`); evidence is the engine table in `outputs/d1/REPORT_D1_F3.md` | sizing-lock-session | not computable from library: needs a Set A engine run (per-book locks) of ST:HM splits. Report figures (old corrected engine, wk_floor 8, $34.88 per 8 lots): 4:12 clean/H1/H2 Sharpe 1.75/2.61/3.26 vs 8:8 1.35/1.65/2.26, all-in net +46%, maxDD +1%; matched null (random tilt direction, 200 draws): share as good net clean 0.20, H1 0.07, H2 0.03, all 0.01; ST weekly Sh clean 1.06 / H1 -0.11 / H2 0.68, HM 1.25 / 2.61 / 2.72, so the gain tracks HM beating ST in H1/H2 | not scorable under V2 as is; missing: Set A-engine re-run with paired WF CI for SD/maxDD, neighbour splits (3:13, 5:11 are SURVIVES/INSURANCE-labelled too), placebo | B19 (REPORT_B19.md): static 4:12 "stays hindsight regime tilt"; dynamic tilts fail H1/H2. Addendum: under DS3 ST/HM weights are free pool parameters, so this lead becomes a sizing choice inside the pool, not a separate book |
| ES/YM dip-buy (RSI2<5, exits rsi65/5d, stop 2-3 ATR) | `C11DIP/ES_*` (16), `C11DIP/NQ_*` (16), `T4B/ES_B1_dip*` (16), `T4B/YM_B1_dip*` (16); FOUND-labelled `C11DIP/ES_dip_rsi5_days5_stop3` | sleeve | ES (C11DIP): 16/16 hold>0, 16/16 meet criterion, 16/16 IS>0. ES T4B: 16/16 hold>0, IS>0 13/16. YM T4B: 16/16 hold>0, but WF-PRE>0 only 8/16, IS>0 12/16. FOUND cell: Sh IS 1.46 / WF-PRE 1.86 / HOLD 2.30, corr -0.01, port Sh 1.72 -> 2.18 at 0.25, 2.48 at 0.5. Median corr 0.02 (ES), -0.11 (YM) | cell-level DEAD-provisional (no placebo/neighbours); **the closest V2-scored relatives are PASS**: NM_E `ES_RSI2_t10` PASS, `NQ_RSI2_t10` PASS, `RTY_RSI2_t10` PASS (RSI2<10 at 15:55, 1-day exit; `autopilot/nm/NM_E.md`, `l2vast/struct48/out/NM_E_leadverdict.json`), `ES_IBS_t20_n1` DEAD, NQ/RTY IBS CANDIDATE, `COMB_c3_R` PASS; all one correlated dip-buy exposure (NQ-ES RSI2 corr 0.73) | C11-DIP: FOUND-PENDING-REPLICATED, small-sample (23 trades in the pair window, 40 trades 2013-22 Sharpe 0.08), lost money in all 17 worst pair weeks; mechanism: dips in uptrend recover within a week. The 15:55 RSI2<10 NM_E cells are NOT the C11 RSI2<5 rsi65/5d cells (different exits): tag accordingly |

### Library names for pool tagging
- V5 / 5-min trend: all `V5P1/*` (12), `V5P2/c0832`, `B2356ERA/V5__*` is a different V5 (ES/NQ/RTY/YM relative strength, NO) - exclude from this lead.
- Prior-day break: `T4D/D*_D2_*` (72). Top: `T4D/D54_D2_{'mode':0,'levset':0,'s':0.25,'tm':1.0,'filt':0.0}`, `T4D/D58_D2_{...'tm':2.0...}`, `T4D/D82_D2_{'mode':0,'levset':2,...'tm':2.0...}`.
- HM-heavy split: none in library; ST and HM are `ST`, `HM`, `PAIR` (library/ST.parquet, HM.parquet, PAIR.parquet; LIVE family, 8 contracts each, wk_floor 8 engine).
- Dip-buy: `C11DIP/ES_*`, `C11DIP/NQ_*`, `T4B/ES_B1_dip*`, `T4B/YM_B1_dip*`, `T4B/RTY_B1_dip*`, `T4B/NQ_B1_dip*`; NM_E sleeves live in `l2vast/struct48/paper_all/NM_E_*.json` (series in struct48/out `*_RSI2*_daily.parquet`, `IBS_t20_n1_daily.parquet`, `COMB_c3_R_daily.parquet`).

### Caveats
- Sleeve criterion here is against Set A, not DS2 ST10/HM10/WT7 and not DS3-internal marginal Sharpe (addendum). It is a screen; the pool-level marginal Sharpe is the lead's job.
- "Executable from NT8 data": V5P1 5-min NQ (yes, 5-min bars; library note "NT8-codable"), T4 D prior-day break NQ 1-min (yes), dip-buy ES/YM daily 15:55 ET (yes, daily/minute bars), K4 (needs VIX-family intraday closes: external feed, not chart data), HM/ST (live L2/1-s engine for P9 costing).
- No re-costing to P9/live cost was done here (library carries no trade counts; belongs to the pool builder).


## 11. Pending additions (T-B added 2026-10-26; T-ENTRY still pending)

- T-ENTRY top 20 with NT8-deliverable vs execution-server-only flags (l2vast/ds3/out/TENTRY_top20.parquet, autopilot/DS3_TENTRY.md): sections to be added on arrival (revision after the 6-h edition).
- Open: T4-style L2 replay of ES/RTY top candidates; proper trade-count re-cost of NQ candidates (P9 table); identity tests (only after a book is selected).


## 12. What the tracks found (addendum; one page; sources autopilot/DS3_T*.md and l2vast/ds3/rows/DS3_*.json)

Verdict counts (cells scored, by DS3 verdict of record): tracks A-K: no PASS, 5 CANDIDATE; T-ENTRY: 6 PASS, 14 CANDIDATE (section 13).

| track | what | cells | PASS | CANDIDATE | DEAD | one-line finding |
|---|---|---|---|---|---|---|
| T-A | survivors re-scored as books (RSI2/IBS dip-buy, ON drift, ORB Asia, WT variants, S130_ES, GSHORT, MBO seven) | 22 | 0 | 0 | 22 | dip-buy sleeves positive on all three spans with corr ~0 to DS2 and identity tests clean (0/312, 0/301 mismatches), but 0.4-0.9 trades/wk (< 3) and own-timing placebo 0.64-0.92; ON_none scorer-CANDIDATE but placebo-dead; ORB Asia negative on 2023-04..2024-01; WT library series lose their edge under the P9 mapping |
| T-B | NQ at other horizons, 10 preregs | 279 | 0 | 4 | 275 | best holdout Sharpe 1.34 (TB1_ST_k15, TB9_RENKO_c2) vs ST10 1.93 / HM10 1.35; no cell above best-of-N null p95 2.21; CANDIDATEs fragile (DSR 0.01-0.04) |
| T-C | CTA, 10 markets, hourly/daily trend | 28 | 0 | 0 | 28 | WF means within +-$100/wk at $1,000/day risk, pre-2023 t ~0; nothing to add |
| T-D | mean reversion where cost allows (ES/YM C2O, ZN VWAP, gap fade, basis) | 7 | 0 | 0 | 7 | TD5_NQ_GAPFADE scorer-CANDIDATE (+$1,154/wk) dies on 2.68 trades/wk and a negative 2023 span; ZN VWAP and NQ-ES basis lose at live cost |
| T-E | cross-asset lead-lag filters | 3 | 0 | 0 | 3 | +0.5 to +1.3 pts/trade, every CI includes 0, below paired MDE |
| T-F | calendar structure | 4 | 0 | 1 | 3 | TF1_FOMC_NY block (filter on a net-negative proxy book) CANDIDATE, below power, registered as filter lead; ES TOM/opex dead and under 3 trades/wk |
| T-H | slow 27-market TSM panel | 14 | 0 | 0 | 14 | report-only; true MDE ~$4.4k/wk exceeds the predicted effect |
| T-I | cross-sectional momentum, 27 markets | 24 | 0 | 0 | 24 | report-only, WF means -$471 to +$958/wk |
| T-J | vol-state sizing of ST/HM/WT | 3 (12 prereg) | 0 | 0 | 3 | lowers SD 11% and maxDD 15% but costs the same fraction of mean: de-leveraging, not timing |
| T-K | first-30 to last-30 intraday momentum | 19 | 0 | 0 | 19 | loss equals cost (ALL8_D1 -$2,499/wk WF, scales linearly with cost) |
| T-ENTRY | entry signals, DS2 bracket and execution fixed (L2 replay) | 191 (38 replayed) | 6 | 14 | 171 | see section 13; no entry beats ST/HM paired; PASSes are ST-family re-parameterisations |
| **total** | | **594** | **6** | **19** | **569** | (T-ENTRY only; tracks A-K have no PASS) |

The CANDIDATE total is TB 4 (TB_P1 1, P7 1, P9 2) and TF1 1; row-file counts (DS3_TB.json 279; the per-prereg final files sum to 279 as well) agree. Pool consequence: no track produced a PASS, so DS3's candidate set from new hypotheses is empty; T-G must assemble from library T1 books and the DS2 components themselves. Combined with the census: (1) the library's best standalone holdout numbers are inside the selection-from-31k noise band; (2) the only evidence classes that survive an independent span are the ES/NQ dip-buy sleeves (low frequency, so not forward-measurable at 3 trades/wk) and the live ST/HM/pair books themselves (HOLD Sharpe 1.3-2.0 at live cost, X-span 0.7-1.0).

Trial accounting: this census added 0 cells; T-A 22, T-B 279, T-C 28, T-D 21 (incl. neighbours), T-E 9, T-F 12, T-H 14, T-I 24, T-J 12, T-K 19 per their reports and the ledger.


## 13. T-ENTRY top 20 entry signals (DS2 bracket and execution held fixed) beside ST10 and HM10

Source `autopilot/DS3_TENTRY.md` and `l2vast/ds3/out/TENTRY_top20.parquet` (first two rows = ST10 and HM10). Per the track: 191 cells scored, 38 re-priced by direct L2 replay, **6 PASS and 14 CANDIDATE** (PASS: TE1_st_10m = TE6_st10m_n10_m3.0 [identical series], TE6_st10m_n7_m3.0, TE6_st10m_n14_m3.0, TE7_emax5m_f30_s50, TE7_kelt3m_n14_m1.0); no tape-based, structure or MBO entry passes; **no entry beats ST or HM on a paired basis** (dST/dHM columns are the paired differences); all 20 are registered as paper_all/ds3_TE_*.json. Note these PASS verdicts are the track agent's, with the DS2 bracket fixed, i.e. they are re-parameterisations of the ST/Supertrend-family entry that DS2 already trades (high corr to ST, see corrST), not independent diversifiers. Flag column = NT8-deliverable vs execution-server-only as given by the track. Census context: the library pool has nothing comparable at live-cost L2 pricing, so section 3 selection noise applies to the library, not to these directly replayed cells (but 191 scored cells and the ledger DSR in the last column still apply).

|   rank | cell                     | flag     | verdict_direct   |    tpw |       wf |     hold |      span2 |   hold_sh |   wf_sd |   wf_maxdd | basis                                 |   corrST |   corrHM |   plc_pre |       dST |       dHM |   dsr_ledger |
|-------:|:-------------------------|:---------|:-----------------|-------:|---------:|---------:|-----------:|----------:|--------:|-----------:|:--------------------------------------|---------:|---------:|----------:|----------:|----------:|-------------:|
|    nan | ST10 (DS2 book, true P9) | live     | benchmark        | 26.077 | 14511.8  | 16768.1  |   6054.54  |     1.975 | 57161.2 |     263432 | true corrected P9 (direct)            |  nan     |  nan     |   nan     |    nan    |   nan     |      nan     |
|    nan | HM10 (DS2 book, true P9) | live     | benchmark        | 23.909 |  9785.42 | 10038.1  |   3807.75  |     1.285 | 53202.4 |     251800 | true corrected P9 (direct)            |  nan     |  nan     |   nan     |    nan    |   nan     |      nan     |
|      1 | TE1_kelt_10m             | NT8-bars | DEAD             | 19.727 |  9377    | 17785.1  |  -1924.8   |     2.589 | 46549.6 |     339073 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.378 |    0.374 |     0.75  |  -5134.78 |  -408.417 |        0.476 |
|      2 | TE7_emax5m_f30_s50       | NT8-bars | PASS             | 11.797 |  7141.57 |  9150.3  |   1348.6   |     1.894 | 34206.2 |     177083 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.068 |    0.23  |     0.975 |  -7370.21 | -2643.84  |        0.511 |
|      3 | TE6_st10m_n7_m3.0        | NT8-bars | PASS             | 12.245 |  8748.57 |  8627.96 |   3467.65  |     1.84  | 35698.1 |     197422 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.088 |   -0.026 |     1     |  -5763.22 | -1036.85  |        0.671 |
|      4 | TE7_kelt3m_n20_m1.0      | NT8-bars | CANDIDATE        | 26.364 | 17235.3  | 15580.1  |  -6666.69  |     1.837 | 59053.6 |     305190 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.189 |    0.171 |     1     |   2723.52 |  7449.88  |        0.842 |
|      5 | TE7_kelt3m_n30_m1.0      | NT8-bars | CANDIDATE        | 25.091 | 13603.4  | 14489.1  | -11612     |     1.828 | 55795.7 |     429363 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.32  |    0.26  |     0.975 |   -908.41 |  3817.96  |        0.669 |
|      6 | TE7_boll3m_n20_m1.5      | NT8-bars | CANDIDATE        | 25.769 | 10601.6  | 13008.8  |  -8782.99  |     1.682 | 51380.5 |     265894 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.155 |    0.301 |     1     |  -3910.18 |   816.189 |        0.499 |
|      7 | TE6_st10m_n10_m3.0       | NT8-bars | PASS             | 12.14  |  8799.3  |  8476.62 |   9914.23  |     1.542 | 40458.6 |     289223 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.028 |   -0.065 |     0.975 |  -5712.49 |  -986.122 |        0.553 |
|      8 | TE1_don_15m              | NT8-bars | DEAD             | 18.713 |  5479.34 | 10619.6  |  -3531.34  |     1.445 | 50917.5 |     460008 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.432 |    0.439 |     0.775 |  -9032.45 | -4306.08  |        0.121 |
|      9 | TE7_kelt3m_n14_m1.0      | NT8-bars | PASS             | 26.776 | 16863.5  | 12885.4  |   6365.47  |     1.369 | 59362.5 |     336626 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.329 |    0.328 |     1     |   2351.68 |  7078.05  |        0.817 |
|     10 | TE7_kelt3m_n14_m2.0      | NT8-bars | DEAD             | 21.042 |  8564.57 | 10198.2  |  -2769.18  |     1.361 | 52660.5 |     415253 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.357 |    0.288 |     0.95  |  -5947.22 | -1220.85  |        0.297 |
|     11 | TE6_st10m_n14_m2.5       | NT8-bars | DEAD             | 14.643 |  7373.37 |  7833.87 |   5849.79  |     1.306 | 43598.2 |     220562 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.155 |    0.069 |     0.9   |  -7138.41 | -2412.05  |        0.328 |
|     12 | TE1_kelt_5m              | NT8-bars | DEAD             | 23.797 |  5685.29 | 11047.9  |  -3413.26  |     1.298 | 52842.3 |     687060 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.289 |    0.235 |     0.625 |  -8826.5  | -4100.13  |        0.124 |
|     13 | TE4_vwb_k2_all           | NT8-bars | DEAD             | 19.469 |  4362.81 |  8855.68 |  -9551.93  |     1.235 | 48744.2 |     479857 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.287 |    0.329 |     0.75  | -10149    | -5422.61  |        0.083 |
|     14 | TE6_st10m_n14_m3.0       | NT8-bars | PASS             | 12.175 |  6980.08 |  6172.08 |   6761.39  |     1.154 | 40565.7 |     238431 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.07  |    0.051 |     0.975 |  -7531.71 | -2805.34  |        0.341 |
|     15 | TE7_boll3m_n20_m2.0      | NT8-bars | CANDIDATE        | 24.727 | 10404.6  | 10395.4  | -11680.9   |     1.105 | 59143.9 |     540010 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.261 |    0.149 |     0.975 |  -4107.2  |   619.17  |        0.358 |
|     16 | TE6_st10m_n10_m3.5       | NT8-bars | CANDIDATE        | 10.706 |  5303.78 |  4630.44 |   4113.79  |     1.066 | 35401.8 |     405993 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.266 |    0.099 |     0.975 |  -9208    | -4481.64  |        0.256 |
|     17 | TE1B_emax_5m             | NT8-bars | CANDIDATE        | 12.818 |  6816.76 |  5353.38 |   -944.713 |     0.982 | 40313.7 |     291574 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.02  |    0.047 |     0.975 |  -7695.02 | -2968.66  |        0.335 |
|     18 | TE4_vwb_k1_all           | NT8-bars | DEAD             | 23.608 |  4675.24 |  7722.58 |   2273.24  |     0.896 | 55144.1 |     353995 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.395 |    0.411 |     0.775 |  -9836.54 | -5110.18  |        0.073 |
|     19 | TE4_orb_london_60        | NT8-bars | DEAD             |  4.888 |  2703.71 |  3578.81 |   4007.45  |     0.873 | 28601.4 |     306227 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.183 |    0.252 |     0.825 | -11808.1  | -7081.7   |        0.092 |
|     20 | TE7_kelt3m_n20_m2.0      | NT8-bars | DEAD             | 23.832 |  7586.26 |  6361.39 |  -1088.02  |     0.803 | 52212.8 |     406666 | DIRECT L2 (S10x1+XJ3, exec_engine_l2) |    0.364 |    0.248 |     1     |  -6925.52 | -2199.16  |        0.23  |


## 14. T-PULLBACK top 10 pullback entries beside ST10 and HM10 (MAPPED basis, edition of 2026-10-26)

Source `l2vast/ds3/out/TPULLBACK_top10.parquet` (rank 0 = ST10/HM10 benchmarks), report `autopilot/DS3_TPULLBACK.md`. Basis is MAPPED (best of 157 cells; all NT8-bar executable); the direct-L2 replay of 40 cells is still running and will regenerate the parquet in place, so re-read it for the final census. Track headline: no pullback cell beats ST10 as a book (weekly difference vs ST negative for all 117 first-pass cells); per-trade paired vs ST is positive in 97/117 but MDE-limited.

|   rank | cell                              | verdict   | basis                        | flag                                                                                 |    tpw |       wf |    hold |     span2 |   hold_sh |   wf_sd |   wf_maxdd |   corrST |   corrHM |
|-------:|:----------------------------------|:----------|:-----------------------------|:-------------------------------------------------------------------------------------|-------:|---------:|--------:|----------:|----------:|--------:|-----------:|---------:|---------:|
|      0 | ST10 (DS2, true P9)               | benchmark | true corrected P9 (direct)   | nan                                                                                  | 26.077 | 14511.8  | 16768.1 |  6054.54  |     1.975 |   nan   |        nan |  nan     |  nan     |
|      0 | HM10 (DS2, true P9)               | benchmark | true corrected P9 (direct)   | nan                                                                                  | 23.909 |  9785.42 | 10038.1 |  3807.75  |     1.285 |   nan   |        nan |  nan     |  nan     |
|      1 | PB7_PB_HMA55_EMA1_T2_W15_s+3      | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 29.399 | 16210.7  | 21996.2 | -1260.07  |     2.664 | 55851.6 |     393543 |    0.341 |    0.322 |
|      2 | PB_ST10_SWZ_T3                    | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 26.965 | 12066.8  | 18413.5 |  2529.52  |     2.385 | 56933.2 |     431079 |    0.45  |    0.382 |
|      3 | PB_EMA200_KELT_T1                 | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 25.168 |  9204.28 | 18850.5 |   515.739 |     2.351 | 52497.4 |     658971 |    0.392 |    0.466 |
|      4 | PB_EMA200_EMA5_T1                 | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 25.077 |  8885.78 | 17621.9 |    24.369 |     2.288 | 51837.5 |     611799 |    0.407 |    0.443 |
|      5 | PB5_depth_swing38                 | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 25.399 | 11614.1  | 19535.7 | 10739.8   |     2.266 | 58027.4 |     388641 |    0.508 |    0.393 |
|      6 | PB6_ST5m_EMA20_2m_T1              | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 28.343 | 13748.8  | 16995.7 |  -287.143 |     2.074 | 55607.5 |     313823 |    0.481 |    0.418 |
|      7 | PB7_PB_HMA55_EMA1_T2_W15_s+0      | PASS      | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 28.434 | 16311.2  | 17397.4 | 12075.9   |     2.037 | 58281.4 |     399067 |    0.394 |    0.333 |
|      8 | PB5_depth_atr1.5                  | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 26.762 | 11714.4  | 17901.7 |  1700.34  |     2.001 | 57904   |     439825 |    0.48  |    0.344 |
|      9 | PB7_PB6_ST60m_EMA20_3m_T1_W30_s+3 | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 23.93  | 10055.6  | 16529.8 |  4704.64  |     1.987 | 55121.1 |     402256 |    0.246 |    0.19  |
|     10 | PB7_PB_ST10_SWZ_T1_W15_s+0        | CANDIDATE | MAPPED (1-s path + P9 table) | NT8-bars (executable on bars; entry via stop/limit-free market on the next bar open) | 24.455 | 10232    | 15817   | 10878.9   |     1.985 | 55417.5 |     500894 |    0.465 |    0.374 |


## 15. T-PULLBACK (3)+(5) top cells (D3PB2; MAPPED basis; direct replay of the top-10 M/S cells still running)

Source `l2vast/ds3/rows/DS3_TPULLBACK2.json`, report `autopilot/DS3_TPULLBACK2.md`. Verdict: 0 PASS, 2 CANDIDATE, 50 DEAD of 52 cells. Top by WF-PRE ($/wk at 10 lots): PB2_B2_M_Hvol 5,546 (DEAD: placebo 0.88, WF CI), PB2_B1_S 4,793 (CANDIDATE, WF CI fails), PB2_B4_M_Hvol 4,600 (CANDIDATE, placebo 0.92, subset-of-base placebo 0.82), PB2_B1_M 3,781, PB2_B2_M_Hcd 3,461, PB2_B1_M_Habs 3,418, PB2_B3_M 3,360, PB2_B3_S 2,661, PB2_B4_M_Habs 2,592, PB2_B2_S 2,318. Every one has a WF CI that includes 0 except PB2_B4_M_Hvol. Executability: Hvol and S cells are NT8-bars; Hcd and Habs need bid/ask-classified ticks (NT8-ticks, not L2); passive limit and ladder cells are mapped-only and all DEAD. Re-read the report after the direct replay lands.


## 16. T-PULLBACK sub-minute top 10 (D3PB4; MAPPED screen only)

Source `l2vast/ds3/rows/DS3_TPULLBACK4.json` (177 cells; 13 PASS, 15 CANDIDATE on the mapped screen), report `autopilot/DS3_TPULLBACK4.md`. **Verdicts are mapped-only**: the direct L2 replay is still running (`out/pb4/direct_final.pkl` not yet landed); re-read before the final census. Track's key point: sub-minute cells earn about $1.7k/wk LESS than the same rule on 1-min bars and the median cell is negative at 2x cost. exec_status DELIVERABLE-PENDING-IDENTITY (D3X identity test not run). Top-10 cells (nt8_bar = exact NT8 BarsPeriod):

| cell | NT8 bar | verdict | WF mean | HOLD | exec_status |
|---|---|---|---|---|---|
| TB4A_time_14_time_30s_ST5_E20_1_T2 | BarsPeriodType.Second, Value 30 | PASS | 16396 | 20405 | DELIVERABLE-PENDING-IDENTITY |
| TB4A_time_21_time_30s_ST10_E20_1_T2 | BarsPeriodType.Second, Value 30 | DEAD | 11518 | 18579 | DELIVERABLE-PENDING-IDENTITY |
| TB4B_tick_11_tick_2000_ST10_SW50_T3 | BarsPeriodType.Tick, Value 2000 | DEAD | 6529 | 11644 | DELIVERABLE-PENDING-IDENTITY |
| TB4B_tick_18_tick_250_ST5_SW50_T1 | BarsPeriodType.Tick, Value 250 | DEAD | 10688 | 17069 | DELIVERABLE-PENDING-IDENTITY |
| TB4D_volume_00_volume_1000_ST15_E20_1_T1 | BarsPeriodType.Volume, Value 1000 | PASS | 18143 | 22621 | DELIVERABLE-PENDING-IDENTITY |
| TB4D_volume_07_volume_500_ST15_E20_1_T1 | BarsPeriodType.Volume, Value 500 | PASS | 15641 | 18702 | DELIVERABLE-PENDING-IDENTITY |
| TB4W_04_time_15s_ST5_E20_1_T2_ntime14 | BarsPeriodType.Second, Value 15 | PASS | 16630 | 18175 | DELIVERABLE-PENDING-IDENTITY |
| TB4W_06_time_30s_ST3_E20_1_T2_ntime14 | BarsPeriodType.Second, Value 30 | PASS | 17654 | 18295 | DELIVERABLE-PENDING-IDENTITY |
| TB4W_12_volume_1000_ST10_E20_1_T1_nvolume00 | BarsPeriodType.Volume, Value 1000 | PASS | 14708 | 17776 | DELIVERABLE-PENDING-IDENTITY |
| TB4W_18_volume_500_ST10_E20_1_T2_nvolume21 | BarsPeriodType.Volume, Value 500 | DEAD | 9211 | 17299 | DELIVERABLE-PENDING-IDENTITY |
