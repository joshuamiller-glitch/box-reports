# DS3_OPEN_BLOCK1 - T-OPEN block (i): calendar, reference levels, opening-type classifier, pre-open / 14:30 feature tables, labels, tape windows (D3OP, 2026-10-27)
Infrastructure only: NO strategy P&L, no cell scored, no holdout look (outcome-label base rates below use the clean span 2024-02..2025-06 only). Definitions, schema, as-of rules and audits: `l2vast/ds3/out/open/README_OPEN.md`; gaps and what would fix them: `l2vast/ds3/out/open/NEEDS_OPEN.md`.

## What exists (l2vast/ds3/out/open/)
calendar (965 label days 2023-02-01..2026-10-23, 962 with RTH), levels (54 columns, 09:29 as-of), opentype (4 cuts x 965 days = 3,860 rows, Dalton OD/OTD/ORR/OA + 30 quantitative columns), preopen_0929 (49 columns), morning_1430 (38 columns), labels_open_close (target file, separate), nq_min (NQ 1-min, one adjusted price space, per-minute raw offset), NQ 1-s rows and 174.5M trade ticks for 09:00-12:00 and 15:45-16:15 ET (tape/), 1-min series for ES, RTY, YM, CL, GC, SI, ZN, 6E, NKD (x1m/, to 2026-10-16).

## Audit results (all 0 mismatches)
- As-of truncation + poison, 16 days x 7 cut points, 4 feature tables: 11,702,682 cells compared, 0 mismatches; positive control (cut too early) flags 38-49 / 11-13 cells, so the audit has power.
- Identity: nq_min vs the bar library minute bars 1,321,205 minutes OHLC 0 mismatches (volume: the 1,200 known dupwin minutes only); ON/PM H/L/C 962/962, prior-day RTH O/H/L/C 961/961 (also vs the tape-layer daily_levels), prior week 954/954, ATR20 942/942, SMA200 746/746, raw-price mapping vs last tape tick 962/962, slow-loop Dalton re-implementation 476/476, RTH minute delta vs tape layer 369,180/369,180.

## Distribution tables
Label days 20230201..20261023: 965 rows, 962 with a 09:30 RTH session, 34 half/short sessions (8 cash-open early closes, 26 cash-holiday short futures sessions), 3 sessions without RTH.

### Opening types by year (rows = year x cut, share of RTH days)

|              |   n |   OD |   OTD |   ORR |   OA |   OD% |   OTD% |   ORR% |   OA% |
|:-------------|----:|-----:|------:|------:|-----:|------:|-------:|-------:|------:|
| (935, 2023)  | 236 |   16 |    37 |    17 |  166 |   6.8 |   15.7 |    7.2 |  70.3 |
| (935, 2024)  | 259 |   12 |    48 |    23 |  176 |   4.6 |   18.5 |    8.9 |  68   |
| (935, 2025)  | 257 |   10 |    67 |    22 |  158 |   3.9 |   26.1 |    8.6 |  61.5 |
| (935, 2026)  | 210 |    6 |    44 |    24 |  136 |   2.9 |   21   |   11.4 |  64.8 |
| (940, 2023)  | 236 |   16 |    25 |    23 |  172 |   6.8 |   10.6 |    9.7 |  72.9 |
| (940, 2024)  | 259 |   12 |    43 |    26 |  178 |   4.6 |   16.6 |   10   |  68.7 |
| (940, 2025)  | 257 |   10 |    53 |    31 |  163 |   3.9 |   20.6 |   12.1 |  63.4 |
| (940, 2026)  | 210 |    5 |    33 |    24 |  148 |   2.4 |   15.7 |   11.4 |  70.5 |
| (945, 2023)  | 236 |   15 |    26 |    18 |  177 |   6.4 |   11   |    7.6 |  75   |
| (945, 2024)  | 259 |    5 |    38 |    23 |  193 |   1.9 |   14.7 |    8.9 |  74.5 |
| (945, 2025)  | 257 |    8 |    57 |    32 |  160 |   3.1 |   22.2 |   12.5 |  62.3 |
| (945, 2026)  | 210 |    3 |    31 |    30 |  146 |   1.4 |   14.8 |   14.3 |  69.5 |
| (1000, 2023) | 236 |   11 |    21 |    27 |  177 |   4.7 |    8.9 |   11.4 |  75   |
| (1000, 2024) | 259 |    5 |    32 |    30 |  192 |   1.9 |   12.4 |   11.6 |  74.1 |
| (1000, 2025) | 257 |    6 |    51 |    42 |  158 |   2.3 |   19.8 |   16.3 |  61.5 |
| (1000, 2026) | 210 |    5 |    30 |    30 |  145 |   2.4 |   14.3 |   14.3 |  69   |

### Opening types by VIX tercile (0 low,1 mid,2 high; trailing-756d terciles of the prior VIX close)

|             |   n |   OD |   OTD |   ORR |   OA |   OD% |   OTD% |   ORR% |   OA% |
|:------------|----:|-----:|------:|------:|-----:|------:|-------:|-------:|------:|
| (935, 0.0)  | 438 |   27 |    66 |    32 |  313 |   6.2 |   15.1 |    7.3 |  71.5 |
| (935, 1.0)  | 343 |   10 |    84 |    36 |  213 |   2.9 |   24.5 |   10.5 |  62.1 |
| (935, 2.0)  | 179 |    7 |    46 |    18 |  108 |   3.9 |   25.7 |   10.1 |  60.3 |
| (940, 0.0)  | 438 |   27 |    56 |    41 |  314 |   6.2 |   12.8 |    9.4 |  71.7 |
| (940, 1.0)  | 343 |   10 |    68 |    43 |  222 |   2.9 |   19.8 |   12.5 |  64.7 |
| (940, 2.0)  | 179 |    6 |    30 |    20 |  123 |   3.4 |   16.8 |   11.2 |  68.7 |
| (945, 0.0)  | 438 |   20 |    54 |    32 |  332 |   4.6 |   12.3 |    7.3 |  75.8 |
| (945, 1.0)  | 343 |    8 |    68 |    47 |  220 |   2.3 |   19.8 |   13.7 |  64.1 |
| (945, 2.0)  | 179 |    3 |    30 |    23 |  123 |   1.7 |   16.8 |   12.8 |  68.7 |
| (1000, 0.0) | 438 |   16 |    44 |    47 |  331 |   3.7 |   10   |   10.7 |  75.6 |
| (1000, 1.0) | 343 |    8 |    61 |    51 |  223 |   2.3 |   17.8 |   14.9 |  65   |
| (1000, 2.0) | 179 |    3 |    29 |    30 |  117 |   1.7 |   16.2 |   16.8 |  65.4 |

### Drive direction among OD/OTD/ORR (10:00 cut): up share by type

| t   |   n |   up_share |
|:----|----:|-----------:|
| OA  | 672 |      0.54  |
| OD  |  27 |      0.667 |
| ORR | 129 |      0.519 |
| OTD | 134 |      0.455 |

### Gap classes at the 09:30 open (share of RTH days, 10:00 cut rows)

|              |   vs 16:00 close |   vs 16:15 settle |
|:-------------|-----------------:|------------------:|
| down>=1.0    |               12 |                12 |
| down 0.5-1.0 |               75 |                66 |
| down 0.3-0.5 |               83 |                84 |
| flat<0.3     |              573 |               558 |
| up 0.3-0.5   |              109 |               104 |
| up 0.5-1.0   |               95 |                91 |
| up>=1.0      |               15 |                13 |
| n            |              962 |               928 |
(class thresholds on |gap|/ATR20; ATR20 = mean true range of the prior 20 full label days)


### Other quantitative opening conditions (10:00 cut rows, n=962)

|                                               |   share |
|:----------------------------------------------|--------:|
| open above ON range                           |   0.001 |
| open inside ON range                          |   0.999 |
| open below ON range                           |   0     |
| open above prior-day RTH range                |   0.24  |
| open inside prior-day range                   |   0.596 |
| open below prior-day range                    |   0.164 |
| first-1-min volume >=1.5x 20d median          |   0.051 |
| >=2x                                          |   0.001 |
| pre-market drive (08:30->09:29) >=0.5 ATR up  |   0.007 |
| ... down                                      |   0.006 |
| ES/RTY/YM all 3 agree with NQ (10:00 window)  |   0.402 |
| 0 of 3 agree                                  |   0.158 |
| abs first-5-min delta share >=0.1             |   0.029 |
| abs first-5-min delta share >=0.2             |   0     |
| pre-market drive >=0.25 ATR (either way)      |   0.089 |
| pre-market drive >=0.1 ATR                    |   0.41  |
| open in top/bottom 10% of ON range or outside |   0.226 |

### Release-slot presence (RTH days)

|                                               |   days |
|:----------------------------------------------|-------:|
| 08:30 any listed (CPI/NFP/CLAIMS-rule)        |    266 |
| CPI                                           |     44 |
| NFP                                           |     41 |
| jobless claims (RULE, unverified)             |    181 |
| 10:00 ISM mfg/svc (RULE-inferred, unverified) |     90 |
| FOMC 14:00 statement days                     |     30 |
| monthly opex                                  |     45 |
| weekly (Friday non-monthly) opex              |    148 |
| quad witching                                 |     15 |
| roll day (library roll_day)                   |     15 |
| roll week                                     |     75 |
| month end (last tradable weekday)             |     44 |
| quarter end                                   |     15 |
| day after holiday                             |     37 |
| earnings reaction day (AMC prev, >=1 of 10)   |    108 |
| earnings BMO today                            |      1 |

### Release-slot validation (post-hoc, descriptive): 10:00-10:02 range / 20d median, by rule flag; 08:30 5-min |move| spike by listed type

|   rel1000_rule |   n |   median |   mean |   share>=3x |
|---------------:|----:|---------:|-------:|------------:|
|              0 | 872 |    0.94  |  1.107 |       0.017 |
|              1 |  90 |    1.565 |  1.763 |       0.078 |
| t      |   n |   median spike_x |   share>=3x |
|:-------|----:|-----------------:|------------:|
| CLAIMS | 181 |            1.37  |       0.249 |
| CPI    |  44 |            6.437 |       0.727 |
| NFP    |  41 |            4.967 |       0.854 |
| none   | 696 |            0.811 |       0.101 |

Days with an 08:30 5-min spike >= 3x median and NO listed release (unlisted-release candidates, e.g. PPI/retail sales/GDP/PCE): 70 of 696.


### Coverage / NaN rates (RTH days)

|                    |   levels |   pre-open |   classifier |
|:-------------------|---------:|-----------:|-------------:|
| sma200             |    0     |    nan     |      nan     |
| atr20              |    0     |    nan     |      nan     |
| pd_POC             |    0.001 |    nan     |      nan     |
| pd_s1615           |    0.035 |    nan     |      nan     |
| pw_H               |    0     |    nan     |      nan     |
| orm60              |    0     |    nan     |      nan     |
| pq_ny              |  nan     |      0.027 |        0.027 |
| pq_asia            |  nan     |      0.028 |      nan     |
| gap_pre_settle_atr |  nan     |      0.035 |      nan     |
| vix_tercile        |  nan     |      0.002 |        0.002 |
| spike0830_x        |  nan     |      0     |      nan     |
| agree3             |  nan     |    nan     |        0.005 |

### 10:00 release inside the opening window
The 10:00 slot lies inside 09:30-10:30; rule-inferred ISM days: 90 of 962 RTH days (9.4%); the classifier 10:00 cut uses bars up to 09:59 only (the release minute 10:00 is NOT in the cut). Every cell carries cal.rel1000_rule / rel1000_type.


### Pre-open and 14:30 day types (share of RTH days)

|          |   prior-day type (pre-open table) |   day type 09:30-14:30 (14:30 table) |
|:---------|----------------------------------:|-------------------------------------:|
| V        |                             0.03  |                                0.02  |
| gap_fill |                           nan     |                                0.128 |
| gap_go   |                           nan     |                                0.182 |
| mixed    |                             0.47  |                                0.305 |
| range    |                             0.185 |                                0.161 |
| trend    |                             0.315 |                                0.205 |

### Label base rates, clean span 2024-02..2025-06 only (n=363 RTH days; holdout and 2023 span NOT tabulated)

|                                     |    up |   down |   neither |   n |   tied_in_1s |
|:------------------------------------|------:|-------:|----------:|----:|-------------:|
| +30 before -30 from 0930 (to 11:00) | 0.455 |  0.54  |     0.006 | 363 |            0 |
| +30 before -30 from 0935 (to 11:00) | 0.49  |  0.493 |     0.017 | 363 |            0 |
| +30 before -30 from 0945 (to 11:00) | 0.501 |  0.482 |     0.017 | 363 |            0 |
| +30 before -30 from 1000 (to 11:00) | 0.529 |  0.449 |     0.022 | 363 |            0 |
|                      |    OD |   OTD |   ORR |    OA |
|:---------------------|------:|------:|------:|------:|
| opening type at 0935 | 0.036 | 0.206 | 0.082 | 0.673 |
| opening type at 0945 | 0.016 | 0.165 | 0.085 | 0.731 |
| opening type at 1000 | 0.016 | 0.129 | 0.129 | 0.723 |
T-CLOSE labels (clean span): 15:49->16:00 direction up 0.497 / down 0.503 (n=350); after the 15:50:30 reaction up 0.517 (n=350); median |react_30s| = 8.38 pts; median |15:49->16:00 move| = 21.8 pts.


## Data gaps and flags (read before block (ii))
1. Earnings: 10 of the top-15 NQ names from EDGAR 8-K 2.02 times (AAPL MSFT NVDA AMZN GOOGL META TSLA AVGO COST NFLX); PEP CSCO AMD TMUS ADBE LIN UNAVAILABLE; ticker lists end 2026-09-25..10-15, so late-October reports are missing (earn_cov_n). 108 RTH days carry >= 1 known after-close report the previous evening (reaction day), 1 carries a pre-market report.
2. Releases: CPI, NFP, FOMC verified; jobless claims and ISM (the only 10:00 releases filled) are RULES, unverified; PPI, retail sales, GDP, PCE, Consumer Confidence, JOLTS, home sales, UMich: UNAVAILABLE. Empirical check: 70 of 696 non-listed days have an 08:30 spike >= 3x (unlisted-release candidates; column spike0830_x).
3. 10:00 release inside the window: ISM rule days = 90 of 962 RTH days (9.4%); the 10:00 cut stops at 09:59:59.
4. open_vs_on is degenerate (the open sits next to the 09:29 price, inside the ON range on 99.9% of days); use open_pos_on / open_pos_pd. The 0.5-ATR pre-market drive threshold is met on 1.3% of days (0.25 ATR: 8.9%, 0.1 ATR: 41%). First-5-min delta share >= 0.2 never occurs (>= 0.1: 2.9%).
5. Strict open-drive (no trade back through the open beyond 1 pt) is rare: 1.4-6.8% of days depending on year and cut; OTD 9-26%, ORR 7-16%, OA 61-75%. A looser flag (od_loose) and the raw excursions are in the table.
6. Other instruments end 2026-10-16 (5 NQ days without ES/RTY/YM agreement); VIX and the compression forecaster end 2026-10-16 (forecaster also NaN on 2.7% of days); tercile NaN for 2026-10-22/23 (VIX stale > 5 days).
7. Sunday-open dupwin windows (13) double the tape volume of the bar library; nq_min and every volume column here use the minute table (correct). 14 library minutes are absent from the minute table.
8. pq_ny (forecaster) is evaluated at the 09:30 session-open instant: treat as known at 09:30:00.

## What block (ii) can rely on
- One price space (library adjusted); raw = adj - off (per minute / per second row / levels.off_pts); levels, round numbers and the tape windows are mutually consistent and identity-checked to the replay's raw tick prices.
- Every feature row is as-of audited (truncation + poison) at its decision time: levels/pre-open 09:29, opening types at 09:35/09:40/09:45/10:00, morning table at 14:29; outcome labels are in a separate file.
- 1-s quotes/book and ticks for 09:00-12:00 (and 15:45-16:15) are ready per month (tape/s1_YYYYMM, tk_YYYYMM): no re-extraction needed for the replay or the L2 families.
- NOT available: full 10:00 release calendar, five of the top-15 earnings names, other-instrument data after 2026-10-16, any non-NQ tick/book (ES/RTY tape/1s tables exist under /mnt/l2/l2vast/tables but are not extracted).
