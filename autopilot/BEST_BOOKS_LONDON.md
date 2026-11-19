# BEST_BOOKS_LONDON - own-merit scorecard, London session (W-BEST; GENERATED AT 2026-11-19 22:07:51Z UTC (a stale page = the cron has stopped; heartbeat /mnt/l2/l2vast/_split/best_books_*.status mtime); first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 20 distinct cells scored (0 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 0 live-book rows; L6M $/wk > 0: 13; L6M and L3M > 0: 10; labels {'WEAK-BUT-POSITIVE': 10, 'BEST-AVAILABLE-NOT-PROVEN': 7, 'LEAD': 3}. Job errors: 0. Run 373 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## Legend: bar codes (plain name, what the size number means, bars per hour)

Bars per hour = mean over every London session (02:00-08:30, 6.5 h ET) in 2026-05..2026-10 of (bars in the session / session hours), measured from the bar stores /mnt/l2/l2vast/_bars (live tm-rows: stores time_m_N / time_s_N, else 3600/N). Fast bars cost processing: a rate of 500 bars/hour is a bar every 7 seconds.

**Time bars: "time_m_3" = 3 MINUTES; "time_s_30" = 30 SECONDS; "tm180" = 180 SECONDS = 3 minutes (the number after tm is always seconds; tm60 = 1 minute, tm600 = 10 minutes).** Source: code/th_grid/gjob.py row_info (tm = time_m size N seconds) and autopilot/BAR_REGISTRY.md.

| code | plain name | size number means | bars/hour over all sizes in the store (min - max) | used in this top 50: size -> bars/hour |
|---|---|---|---|---|
| ? | ? bar | see BAR_REGISTRY.md | n/a (no store) | ?: nan |
| rng | range bar | ticks of high-low range per bar (1 tick = 0.25 pt) | 1 - 129 | rng_14: 72; rng_28: 20; rng_80: 3 |
| tick | tick-count bar | trade prints per bar (scaled daily by trailing print count) | 1 - 21 | tick_1300: 5 |
| time_m | time bar | minutes per bar | 0 - 60 | time_m_3: 20; time_m_4: 15; time_m_5: 12 |
| tm | time bar | seconds per bar (tm180 = 180 s = 3 min) | 3600 / seconds (tm60 = 60/h, tm180 = 20/h, tm600 = 6/h) | tm120: 30 |
| vol | volume bar | contracts per bar (scaled daily by trailing volume) | 2 - 27 | vol_500: 19; vol_4000: 2 |
| vrb | volume-run bar | expected prints per bar (information-driven) | 0 - 91 | vrb_700: 15 |
| anch | anchored equal-volume bar | anchor_B: bucket size | 0 - 1 |  |
| bmsg | book-message bar | one bar per N MBO book messages (B-code = size step, 500 to 64,000 messages) | 5 - 88 |  |
| bmsgq | quote-message bar | B-code size step | 5 - 88 |  |
| cdr | cumulative-delta-range bar | contracts: range of the running cumulative delta inside a bar | 0 - 14 |  |
| cusum | CUSUM-event bar | threshold in ticks (scaled by trailing daily range) | 1 - 131 |  |
| dchg | directional-change bar | reversal threshold in ticks (scaled) | 1 - 70 |  |
| dib | dollar-imbalance bar | expected prints per bar (information-driven) | 1 - 199 |  |
| dlt | delta bar | contracts of net aggressor delta per bar | 1 - 61 |  |
| dltor | delta-or-range bar | composite | 8 - 133 |  |
| dol | dollar bar | contract-equivalents at 15,000 (bar closes at N x 20 x 15,000 dollars traded; scaled daily) | 2 - 25 |  |
| drb | dollar-run bar | expected prints per bar (information-driven) | 0 - 80 |  |
| entropy | entropy bar | surprise threshold (B-code) | 5 - 83 |  |
| frenko | flex Renko bar | ticks per brick (reversal bar half size) | 1 - 148 |  |
| ha | Heikin-Ashi bar | on top of another bar | 13 - 55 |  |
| kagi | Kagi bar | reversal ticks | 1 - 70 |  |
| kal | kal bar | see BAR_REGISTRY.md | 13 - 55 |  |
| lbrk | line-break bar | id lbrk_N_B: N lines, base box B ticks | 2 - 23 |  |
| med | med bar | see BAR_REGISTRY.md | 13 - 55 |  |
| micro | microprice-change bar | changes per bar | 5 - 89 |  |
| mom | momentum bar | ticks of net one-direction move per bar | 1 - 79 |  |
| mrenko | median Renko bar | ticks per brick | 0 - 56 |  |
| pasl | price-action swing-leg bar | ticks | 2 - 13 |  |
| pnf | point-and-figure column bar | ticks per box (3-box reversal) | 0 - 27 |  |
| qmid | mid-change bar | mid-price changes per bar | 5 - 89 |  |
| renko | Renko bar | ticks per brick | 0 - 42 |  |
| rngor | range-or-time bar | ticks_seconds | 7 - 122 |  |
| sessrng | session-range-clock bar | bars per session | 6 - 96 |  |
| swing_atr | swing bar | retrace in ATR multiples | 2 - 110 |  |
| swing_pct | swing bar | retrace in basis points of price | 0 - 14 |  |
| t3 | t3 bar | see BAR_REGISTRY.md | 13 - 55 |  |
| tib | tick-imbalance bar | expected prints per bar (information-driven; scaled by trailing prints) | 1 - 183 |  |
| time_s | time bar | seconds per bar | 80 - 664 |  |
| tpo | tpo bar | see BAR_REGISTRY.md | 2 - 2 |  |
| trb | tick-run bar | expected prints per bar (information-driven) | 0 - 78 |  |
| trend | trend bar | ticks | 0 - 42 |  |
| tsf | trade-size-filtered volume bar | contracts per bar counting only large prints (id tsf_L_N: L = min print size) | 0 - 37 |  |
| typ | typ bar | see BAR_REGISTRY.md | 13 - 55 |  |
| urenko | UniRenko bar | ticks per brick | 1 - 80 |  |
| vfp | footprint bar | base series | 3 - 275 |  |
| vfpL | vfpL bar | see BAR_REGISTRY.md | 614 - 3115 |  |
| vib | volume-imbalance bar | expected prints per bar (information-driven) | 1 - 200 |  |
| vnorm | variance-normalised bar | bars per day-equivalent | 1 - 41 |  |
| volor | volume-or-range bar | composite | 7 - 118 |  |
| vsess | session-volume-clock bar | bars per session (vsess 30 = a bar every 1/30 of the session volume) | 5 - 99 |  |
| wrenko | Renko-with-wicks bar | ticks per brick | 0 - 42 |  |

## Prior-year colour summary (REPORT ONLY; the rule and the labels are unchanged)

- New books, top 200 by own-merit rank (20 books): GREEN 0 / AMBER 0 / RED 3 / not landed 17.
  Prior years positive in absolute $/wk, books with all 3 years landed (3): 0 of 3: 0, 1 of 3: 0, 2 of 3: 1, 3 of 3: 2. Books with 1-2 years landed (0): none.
- Live books: none

**For Josh:** the colour compares a prior year with the book's OWN recent six months (RED = more than 30% worse than that level on $/week or on the ulcer-adjusted score), so a book that had a very good recent half-year is RED against any ordinary year by construction, even when the prior year was profitable; the absolute prior-year $/wk and ulcer are shown in the table so the two readings can be compared.

## Formula
- Daily own P&L = sum of the book's own trades by exit date (ET+7h trading day), net of fees ($4.84 x lots), at **1 lot** (gross/lots - 4.84; new books are 1 lot already; live books are divided by their lots), zero-filled over the weekday calendar.
- **SCORE = L6M $/week divided by L6M own ulcer index** (ulcer = sqrt(mean(drawdown^2)) of the daily cumulative own P&L inside the window; $/week = total / (weekdays/5)). Ranking is by SCORE L6M descending (recent window first); L3M score and L3M rank are shown beside. Cells with L6M <= 0 rank last by construction. "(thin)" = under 1 trade per week.
- Own max drawdown = deepest peak-to-trough of the daily cumulative own P&L in the window; worst week = lowest weekly own sum; win% / avg win / avg loss per trade (net of fee).
- **What it is** comes from the cell definition: grid cell id -> /mnt/l2/l2vast/_lon/ladder_cells.json (Asia) or _nye/ladder_cells.json (NY AM) fields row (bar type_size) x module/variant/params x bracket x mode, with the median stop/target points of the cell events from _asi_lad/ev_meta.json or _nye/ev_meta.json. M-ids are the side-filtered rebuild of the L-id. Live books: as run in JL3.
- **L3M ranking:** rank L3M = rank by the L3M score (L3M $/wk / L3M ulcer) in the same pool; top-50 flag = rank <= 50 on both L6M and L3M.
- **Persistence** (target >= 0.58): share of non-overlapping 14-calendar-day windows with own P&L > 0; "L6M" = the 13 windows inside the L6M window; "all landed" = all landed months (L6M plus any landed prior years).
- **Prior years "not a disaster" vs the book's OWN recent level** (standing rule, 15-30% AMBER, >30% RED): worse% = max of (own L6M $/wk minus year $/wk) / L6M $/wk and (own L6M SCORE minus year SCORE) / L6M SCORE; shown beside the absolute $/wk and ulcer. Only defined when L6M $/wk > 0 (else blank / n/a). A year with a lower ulcer-adjusted score but a lower absolute level is flagged by the larger of the two.
- **Labels** (mine, from the standing list): CONFIRMED = L6M>0, L3M>0, persistence L6M >= 0.58, all 3 prior years landed and none RED, and screen p_ALL <= 0.05 (live books: no p needed); LEAD = same but prior years not all landed (or p not met), none RED; WEAK-BUT-POSITIVE = L6M > 0 but fails L3M, persistence or has a RED year; BEST-AVAILABLE-NOT-PROVEN = L6M <= 0. Controls (30 date-shifts) and the exit run are NOT in this table, so CONFIRMED here is not the final CONFIRMED of the ladder.
- **Calibration / luck (per cell when available):** screen p_L6M / p_ALL = share of same-bracket random-entry draws that did as well (n_draws in the CSV; 30 draws => finest 0.032), from the W-SHORT screen; block = the module block used for the family FDR. These are screen numbers (NOT FDR-corrected, "NOT calibrated" per the screen source). Family FDR (partial draw 1, autopilot/SURVIVOR_COUNTS.md CALIBRATION): see the lines below.

| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 728 / 1814 | p_L6M (null / real families at threshold = FDR) | 87 / 223 = 39% | 39 / 66 = 59% | 14 / 20 = 70% | 5 / 8 = 62% |

## Where the live books rank (same table, same scoring; 20 rows in this session)

| rank | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

(live rows are JL3 own trades normalised to 1 lot; as-run base-lot numbers are in the CSV-side table below.)

| live book | L6M $/wk at 1 lot | L6M $/wk as run (base lots) | L3M $/wk as run | L6M ulcer as run | avg lots L6M |
|---|---|---|---|---|---|

## Top 50 London cells by own-merit SCORE (live rows appear in the live table above with their rank in the same pool)

| rank | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | YES | volume bar 500 contracts [vol_500]; ~19 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.25}; side both; bracket asym15u/30u | 19 | LA5 | NEW | RM7 | 0.560 | 0.606 | 2138 | 2262 | 3819 | 3731 | -9472 | -4964 | 7.6 | 0.56 | 1693 | -1536 | 0.71 | 0.55 | 311 | 2588 | +85 | RED | -71 | 13068 | +103 | RED | 384 | 11549 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 | 8 | YES | unresolved (cell not in ladder_cells.json) |  | LB5 | NEW | RM7 | 0.167 | 0.157 | 1243 | 660 | 7443 | 4202 | -19947 | -10749 | 8.9 | 0.50 | 1798 | -1504 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 3 | 13 | YES | unresolved (cell not in ladder_cells.json) |  | LB7 | NEW | RM7 | 0.159 | -0.010 | 638 | -55 | 4019 | 5258 | -11993 | -5989 | 7.7 | 0.52 | 1064 | -1000 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 4 | 3 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"}; side both; bracket sym15u | 12 | LA4 | NEW | RM7 | 0.137 | 0.545 | 1187 | 1920 | 8659 | 3525 | -23834 | -10953 | 8.4 | 0.54 | 1683 | -1691 | 0.57 | 0.52 | 388 | 4949 | +67 | RED | 161 | 6285 | +86 | RED | 557 | 7407 | +53 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 5 | 7 | YES | unresolved (cell not in ladder_cells.json) |  | LB4 | NEW | RM7 | 0.124 | 0.237 | 913 | 1160 | 7374 | 4895 | -15711 | -8339 | 7.5 | 0.51 | 1653 | -1457 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 6 | 1 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_zones / reject_native {"tol": 1.0, "conf": "body"}; side both; bracket sym8u | 3 | LA1 | NEW | RM7 | 0.111 | 0.680 | 751 | 2284 | 6794 | 3360 | -14518 | -9369 | 6.1 | 0.54 | 1559 | -1589 | 0.64 | 0.56 | 582 | 2818 | +22 | AMBER | 342 | 5252 | +54 | RED | 212 | 6632 | +72 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 7 | 6 | YES | tick-count bar 1300 prints [tick_1300]; ~5 bars/hour; trigger trig_levels_opens / reject_native {"tol": 1.0, "conf": "close"}; side both; bracket asym20u/10u | 5 | LA6 | NEW | RM7 | 0.058 | 0.383 | 657 | 2053 | 11236 | 5362 | -24998 | -13363 | 6.9 | 0.54 | 1656 | -1707 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 8 | 16 | YES | volume bar 4000 contracts [vol_4000]; ~2 bars/hour; trigger trig_levels_vwap_bands / reject_native {"tol": 1.0, "conf": "close"}; side both; bracket sym30u | 2 | LA2 | NEW | RM7 | 0.048 | -0.041 | 410 | -442 | 8484 | 10887 | -23025 | -9414 | 7.9 | 0.48 | 1679 | -1455 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 9 | 11 | YES | unresolved (cell not in ladder_cells.json) |  | LB6 | NEW | RM7 | 0.040 | 0.023 | 708 | 387 | 17740 | 17006 | -42968 | -8522 | 18.7 | 0.51 | 1082 | -1037 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 10 | 19 | YES | unresolved (cell not in ladder_cells.json) |  | LB8 | NEW | ADD | 0.035 | -0.082 | 437 | -1393 | 12645 | 17080 | -25061 | -10874 | 8.7 | 0.48 | 1850 | -1585 | 0.29 | 0.29 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 11 | 10 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_round / retest {"M": 6, "tol": 0.0}; side both; bracket sym8u | 3 | WL2 | NEW | RM7 | 0.003 | 0.067 | 42 | 722 | 12945 | 10818 | -27581 | -9149 | 7.6 | 0.52 | 1559 | -1645 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 12 | 4 | YES | unresolved (cell not in ladder_cells.json) |  | LB2 | NEW | RM7 | 0.003 | 0.535 | 53 | 2212 | 19008 | 4135 | -29863 | -10777 | 17.0 | 0.50 | 1069 | -1058 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 13 | 5 | YES | unresolved (cell not in ladder_cells.json) |  | LB1 | NEW | RM7 | 0.000 | 0.418 | 8 | 1451 | 19297 | 3475 | -32982 | -10309 | 10.1 | 0.47 | 1769 | -1578 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 14 | 18 | YES | unresolved (cell not in ladder_cells.json) |  | LB3 | NEW | ADD | -0.007 | -0.074 | -78 | -1037 | 10722 | 13961 | -26731 | -9764 | 8.5 | 0.47 | 1726 | -1568 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 15 | 14 | YES | range bar 14 ticks [rng_14]; ~72 bars/hour; trigger trig_tape_delta / follow_sm {"L": 200, "z": 2.0, "sm": 3}; side both; bracket sym15u | 72 | WL6 | NEW | RM7 | -0.008 | -0.028 | -98 | -339 | 12936 | 12109 | -31719 | -13403 | 9.4 | 0.52 | 1534 | -1671 | 0.29 | 0.29 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 16 | 9 | YES | range bar 28 ticks [rng_28]; ~20 bars/hour; trigger trig_levels_vwap_bands / break_native {"n": 1, "k": 0.5}; side both; bracket sym8u | 20 | WL1 | NEW | ADD | -0.008 | 0.077 | -60 | 373 | 7481 | 4880 | -18933 | -9388 | 9.3 | 0.49 | 1675 | -1607 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 17 | 15 | YES | time bar 3 min [time_m_3]; ~20 bars/hour; trigger trig_tape_delta / cvd_fade {"N": 10, "L": 100, "z": 1.5}; side both; bracket sym8u | 20 | WL7 | NEW | RM7 | -0.013 | -0.033 | -206 | -176 | 16110 | 5396 | -31113 | -8209 | 8.7 | 0.50 | 1384 | -1456 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 18 | 17 | YES | time bar 4 min [time_m_4]; ~15 bars/hour; trigger trig_momentum_roc / break {"len": 10, "wd": 1.0}; side both; bracket asym20u/10u | 15 | WL9 | NEW | RM7 | -0.019 | -0.061 | -484 | -508 | 25229 | 8333 | -42863 | -15163 | 8.0 | 0.50 | 1467 | -1559 | 0.21 | 0.21 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 19 | 12 | YES | volume-run bar 700 [vrb_700]; ~15 bars/hour; trigger trig_levels_trendline / break_native {"n": 2, "k": 0.25}; side both; bracket sym15u | 15 | WL4 | NEW | ADD | -0.033 | 0.020 | -346 | 153 | 10555 | 7689 | -21995 | -12384 | 7.5 | 0.48 | 1671 | -1629 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 20 | 20 | YES | time bar 2 min (tm120 = 120 seconds) [tm120]; ~30 bars/hour; trigger trig_levels_vwap_bands / retest_native {"M": 10, "tol": 0.5}; side both; bracket sym30u | 30 | LA3 | NEW | RM7 | -0.040 | -0.149 | -1025 | -2465 | 25459 | 16599 | -57283 | -13228 | 9.3 | 0.48 | 1646 | -1715 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 32 pairs over 16 cells): mean abs difference of its own L6M total $4712 = 310.5% of |total| (median 31.6%, 90th pct 342.0%); trade-count differences: mean abs 5.6 trades (primary mean 246).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_london.csv; all columns: best_books_london_full.csv; status file best_books_london.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
