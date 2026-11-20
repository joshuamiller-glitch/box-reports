# BEST_BOOKS_LONDON - own-merit scorecard, London session (W-BEST; GENERATED AT 2026-11-20 05:37:02Z UTC (a stale page = the cron has stopped; heartbeat /mnt/l2/l2vast/_split/best_books_*.status mtime); first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 44 distinct cells scored (1 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 4 live-book rows; L6M $/wk > 0: 26; L6M and L3M > 0: 19; labels {'WEAK-BUT-POSITIVE': 22, 'BEST-AVAILABLE-NOT-PROVEN': 18, 'LEAD': 4}. Job errors: 0. Run 626 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## London TOP 10 on own merit (plain words; old rank = rank before the stale re-runs started, 22:07Z)

| rank | old rank | cell | side | bar | trigger | bracket | L6M $/wk | L6M ulcer | status |
|---|---|---|---|---|---|---|---|---|---|
| 1 | new | LA5 | BOTH SIDES | volume bar 500 contracts | trig_levels_vwap / break {"n": 3, "k": 0.25} | asym15u/30u | 2138 | 3819 | ok |
| 3 | new | M1dfc2f39 | LONG ONLY | time bar 2 min | trig_xmarket_nkd / follow {"w": 1, "thr": 1.0} | plain60/60 | 968 | 4021 | ok |
| 4 | new | LB5 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1243 | 7443 | ok |
| 5 | new | LB7 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 638 | 4019 | ok |
| 6 | new | LA4 | BOTH SIDES | time bar 5 min | trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"} | sym15u | 1187 | 8659 | ok |
| 7 | new | LB4 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 913 | 7374 | ok |
| 8 | new | LA1 | BOTH SIDES | range bar 80 ticks | trig_levels_zones / reject_native {"tol": 1.0, "conf": "body"} | sym8u | 751 | 6794 | ok |
| 9 | new | L59c87ce9 | BOTH SIDES | flex Renko bar 28 ticks | trig_levels_prior_day / retest_native {"M": 6, "tol": 0.5} | plain60/60 | 425 | 4505 | ok |
| 10 | new | L0783eb1c | BOTH SIDES | time bar 10 min | trig_xmarket_rty / revert {"w": 1, "thr": 1.0} | sym15u | 685 | 8123 | ok |
| 11 | new | LB8 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 725 | 12275 | ok |

Stale-pending cells (their old results are NOT ranked until re-run; listed in the _full.csv with stale=1 and no rank): 0; of them in the OLD top 50: 0 (none in the old top 10).

## Legend: bar codes (plain name, what the size number means, bars per hour)

Bars per hour = mean over every London session (02:00-08:30, 6.5 h ET) in 2026-05..2026-10 of (bars in the session / session hours), measured from the bar stores /mnt/l2/l2vast/_bars (live tm-rows: stores time_m_N / time_s_N, else 3600/N). Fast bars cost processing: a rate of 500 bars/hour is a bar every 7 seconds.

**Time bars: "time_m_3" = 3 MINUTES; "time_s_30" = 30 SECONDS; "tm180" = 180 SECONDS = 3 minutes (the number after tm is always seconds; tm60 = 1 minute, tm600 = 10 minutes).** Source: code/th_grid/gjob.py row_info (tm = time_m size N seconds) and autopilot/BAR_REGISTRY.md.

| code | plain name | size number means | bars/hour over all sizes in the store (min - max) | used in this top 50: size -> bars/hour |
|---|---|---|---|---|
| ? | ? bar | see BAR_REGISTRY.md | n/a (no store) | ?: nan |
| dib | dollar-imbalance bar | expected prints per bar (information-driven) | 1 - 199 | dib_6000: 13 |
| drb | dollar-run bar | expected prints per bar (information-driven) | 0 - 80 | drb_1200: 5; drb_2000: 3 |
| frenko | flex Renko bar | ticks per brick (reversal bar half size) | 1 - 148 | frenko_28: 21 |
| rng | range bar | ticks of high-low range per bar (1 tick = 0.25 pt) | 1 - 129 | rng_14: 72; rng_20: 38; rng_28: 20; rng_80: 3 |
| tib | tick-imbalance bar | expected prints per bar (information-driven; scaled by trailing prints) | 1 - 183 | tib_1200: 46; tib_6000: 9 |
| tick | tick-count bar | trade prints per bar (scaled daily by trailing print count) | 1 - 21 | tick_1300: 5 |
| time_m | time bar | minutes per bar | 0 - 60 | time_m_1: 60; time_m_2: 30; time_m_3: 20; time_m_4: 15; time_m_5: 12; time_m_10: 6 |
| time_s | time bar | seconds per bar | 80 - 664 | time_s_45: 80 |
| tm | time bar | seconds per bar (tm180 = 180 s = 3 min) | 3600 / seconds (tm60 = 60/h, tm180 = 20/h, tm600 = 6/h) | tm20: 180; tm60: 60; tm120: 30; tm180: 20; tm420: 9; tm600: 6; tm1800: 2 |
| vol | volume bar | contracts per bar (scaled daily by trailing volume) | 2 - 27 | vol_500: 19; vol_1700: 6; vol_4000: 2 |
| vrb | volume-run bar | expected prints per bar (information-driven) | 0 - 91 | vrb_400: 44; vrb_700: 15 |
| vsess | session-volume-clock bar | bars per session (vsess 30 = a bar every 1/30 of the session volume) | 5 - 99 | vsess_80: 13 |
| anch | anchored equal-volume bar | anchor_B: bucket size | 0 - 1 |  |
| bmsg | book-message bar | one bar per N MBO book messages (B-code = size step, 500 to 64,000 messages) | 5 - 88 |  |
| bmsgq | quote-message bar | B-code size step | 5 - 88 |  |
| cdr | cumulative-delta-range bar | contracts: range of the running cumulative delta inside a bar | 0 - 14 |  |
| cusum | CUSUM-event bar | threshold in ticks (scaled by trailing daily range) | 1 - 131 |  |
| dchg | directional-change bar | reversal threshold in ticks (scaled) | 1 - 70 |  |
| dlt | delta bar | contracts of net aggressor delta per bar | 1 - 61 |  |
| dltor | delta-or-range bar | composite | 8 - 133 |  |
| dol | dollar bar | contract-equivalents at 15,000 (bar closes at N x 20 x 15,000 dollars traded; scaled daily) | 2 - 25 |  |
| entropy | entropy bar | surprise threshold (B-code) | 5 - 83 |  |
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
| wrenko | Renko-with-wicks bar | ticks per brick | 0 - 42 |  |

## Prior-year colour summary (REPORT ONLY; the rule and the labels are unchanged)

- New books, top 200 by own-merit rank (44 books): GREEN 0 / AMBER 0 / RED 7 / not landed 37.
  Prior years positive in absolute $/wk, books with all 3 years landed (6): 0 of 3: 0, 1 of 3: 0, 2 of 3: 2, 3 of 3: 4. Books with 1-2 years landed (1): 2 of 2 positive: 1.
- Live books (4 books): GREEN 0 / AMBER 0 / RED 2 / not landed 2.
  Prior years positive in absolute $/wk, books with all 3 years landed (4): 0 of 3: 0, 1 of 3: 3, 2 of 3: 0, 3 of 3: 1. Books with 1-2 years landed (0): none.

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

| NYAM | 2,713 / 7,764 (0.35) | 2,617 / 7,377 | 728 / 1814 | p_L6M (null / real families at threshold = FDR) | 313 / 903 = 35% | 140 / 268 = 52% | 50 / 81 = 62% | 18 / 33 = 55% |

## Where the live books rank (same table, same scoring; 48 rows in this session)

| rank | OLD rank (before re-runs) | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2 |  | 10 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 18 |  | 15 | YES | live book M7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_M7 | LIVE | JL3 | 0.017 | 0.146 | 144 | 1130 | 8679 | 7722 | -17285 | -11717 | 19.8 | 0.40 | 1172 | -762 | 0.43 | 0.40 | 95 | 5555 | +34 | RED | -376 | 26105 | +360 | RED | -356 | 16712 | +347 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 31 |  | 23 | YES | live book K7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour | 20 | LIVE_K7 | LIVE | JL3 | -0.008 | 0.030 | -40 | 164 | 5193 | 5366 | -12034 | -6678 | 17.6 | 0.41 | 1154 | -820 | 0.43 | 0.54 | 210 | 8189 |  | n/a | 150 | 9556 |  | n/a | 569 | 6933 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 38 |  | 36 | YES | live book U7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 10 min (tm600 = 600 seconds) [tm600]; ~6 bars/hour | 6 | LIVE_U7 | LIVE | JL3 | -0.019 | -0.045 | -76 | -204 | 3917 | 4543 | -7975 | -3125 | 4.2 | 0.45 | 1150 | -992 | 0.43 | 0.45 | 29 | 4390 |  | n/a | -65 | 10025 |  | n/a | -67 | 4691 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

(live rows are JL3 own trades normalised to 1 lot; as-run base-lot numbers are in the CSV-side table below.)

| live book | L6M $/wk at 1 lot | L6M $/wk as run (base lots) | L3M $/wk as run | L6M ulcer as run | avg lots L6M |
|---|---|---|---|---|---|
| LIVE_P7 | 822 | 1060 | 1092 | 4975 | 1.35 |
| LIVE_M7 | 144 | -277 | 792 | 14241 | 1.17 |
| LIVE_K7 | -40 | -82 | 107 | 6199 | 1.08 |
| LIVE_U7 | -76 | 695 | 396 | 4244 | 2.11 |

## Top 50 London cells by own-merit SCORE (live rows appear in the live table above with their rank in the same pool)

| rank | OLD rank (before re-runs) | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 |  | 3 | YES | volume bar 500 contracts [vol_500]; ~19 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.25}; SIDE: BOTH SIDES; bracket asym15u/30u | 19 | LA5 | NEW | RM7 | 0.560 | 0.606 | 2138 | 2262 | 3819 | 3731 | -9472 | -4964 | 7.6 | 0.56 | 1693 | -1536 | 0.71 | 0.55 | 311 | 2588 | +85 | RED | -71 | 13068 | +103 | RED | 384 | 11549 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 |  | 10 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 3 |  | 13 | YES | time bar 2 min [time_m_2]; ~30 bars/hour; trigger trig_xmarket_nkd / follow {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 30 | M1dfc2f39 | NEW | RM7 | 0.241 | 0.170 | 968 | 795 | 4021 | 4686 | -10910 | -3609 | 10.5 | 0.54 | 1088 | -1076 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.423 | 0.008 | 0 |
| 4 |  | 14 | YES | unresolved (cell not in ladder_cells.json) |  | LB5 | NEW | RM7 | 0.167 | 0.157 | 1243 | 660 | 7443 | 4202 | -19947 | -10749 | 8.9 | 0.50 | 1798 | -1504 | 0.79 | 0.61 | 575 | 2787 | +54 | RED | 715 | 4719 | +42 | RED | 174 | 9970 | +90 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 5 |  | 29 | YES | unresolved (cell not in ladder_cells.json) |  | LB7 | NEW | RM7 | 0.159 | -0.010 | 638 | -55 | 4019 | 5258 | -11993 | -5989 | 7.7 | 0.52 | 1064 | -1000 | 0.50 | 0.63 | 547 | 3121 | +14 | GREEN |  |  |  | n/a | 545 | 5140 | +33 | RED | RED (2 of 3 yrs) | WEAK-BUT-POSITIVE |  |  | 0 |
| 6 |  | 4 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym15u | 12 | LA4 | NEW | RM7 | 0.137 | 0.545 | 1187 | 1920 | 8659 | 3525 | -23834 | -10953 | 8.4 | 0.54 | 1683 | -1691 | 0.57 | 0.52 | 388 | 4949 | +67 | RED | 161 | 6285 | +86 | RED | 557 | 7407 | +53 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 7 |  | 11 | YES | unresolved (cell not in ladder_cells.json) |  | LB4 | NEW | RM7 | 0.124 | 0.237 | 913 | 1160 | 7374 | 4895 | -15711 | -8339 | 7.5 | 0.51 | 1653 | -1457 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 8 |  | 2 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_zones / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym8u | 3 | LA1 | NEW | RM7 | 0.111 | 0.680 | 751 | 2284 | 6794 | 3360 | -14518 | -9369 | 6.1 | 0.54 | 1559 | -1589 | 0.64 | 0.56 | 582 | 2818 | +22 | AMBER | 342 | 5252 | +54 | RED | 212 | 6632 | +72 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 9 |  | 1 | YES | flex Renko bar 28 ticks [frenko_28]; ~21 bars/hour; trigger trig_levels_prior_day / retest_native {"M": 6, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 21 | L59c87ce9 | NEW | RM7 | 0.094 | 1.421 | 425 | 1388 | 4505 | 977 | -10097 | -3529 | 4.9 | 0.55 | 1044 | -1068 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.355 | 0.032 | 0 |
| 10 |  | 5 | YES | time bar 10 min [time_m_10]; ~6 bars/hour; trigger trig_xmarket_rty / revert {"w": 1, "thr": 1.0}; SIDE: BOTH SIDES; bracket sym15u | 6 | L0783eb1c | NEW | RM7 | 0.084 | 0.536 | 685 | 1654 | 8123 | 3084 | -21367 | -8993 | 6.7 | 0.50 | 1712 | -1489 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.478 | 0.025 | 0 |
| 11 |  | 42 | YES | unresolved (cell not in ladder_cells.json) |  | LB8 | NEW | RM7 | 0.059 | -0.081 | 725 | -1356 | 12275 | 16763 | -24586 | -5943 | 9.0 | 0.49 | 1834 | -1571 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 12 |  | 9 | YES | tick-count bar 1300 prints [tick_1300]; ~5 bars/hour; trigger trig_levels_opens / reject_native {"tol": 1.0, "conf": "close"}; SIDE: BOTH SIDES; bracket asym20u/10u | 5 | LA6 | NEW | RM7 | 0.058 | 0.383 | 657 | 2053 | 11236 | 5362 | -24998 | -13363 | 6.9 | 0.54 | 1656 | -1707 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 13 |  | 34 | YES | volume bar 4000 contracts [vol_4000]; ~2 bars/hour; trigger trig_levels_vwap_bands / reject_native {"tol": 1.0, "conf": "close"}; SIDE: BOTH SIDES; bracket sym30u | 2 | LA2 | NEW | RM7 | 0.048 | -0.041 | 410 | -442 | 8484 | 10887 | -23025 | -9414 | 7.9 | 0.48 | 1679 | -1455 | 0.57 | 0.52 | 491 | 5149 | -20 | GREEN | -41 | 10912 | +110 | RED | 169 | 7911 | +59 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 14 |  | 24 | YES | unresolved (cell not in ladder_cells.json) |  | LB6 | NEW | RM7 | 0.040 | 0.023 | 708 | 387 | 17740 | 17006 | -42968 | -8522 | 18.7 | 0.51 | 1082 | -1037 | 0.43 | 0.59 | 601 | 3485 | +15 | AMBER | 440 | 7088 | +38 | RED | 214 | 12913 | +70 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 15 |  | 26 | YES | time bar 10 min [time_m_10]; ~6 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket asym10u/20u | 6 | M0b9cb93a | NEW | RM7 | 0.033 | 0.002 | 175 | 14 | 5347 | 6154 | -14902 | -6574 | 7.1 | 0.52 | 1493 | -1592 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.645 | 0.258 | 0 |
| 16 |  | 21 | YES | time bar 45 s [time_s_45]; ~80 bars/hour; trigger trig_xmarket_rates / with_ZN {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 80 | M84c5552a | NEW | RM7 | 0.026 | 0.047 | 232 | 304 | 9023 | 6498 | -17958 | -7292 | 20.0 | 0.50 | 1059 | -1039 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.388 | 0.004 | 0 |
| 17 |  | 12 | YES | dollar-imbalance bar 6000 [dib_6000]; ~13 bars/hour; trigger trig_bands_keltner / break {"ema": 30, "atr": 10, "mult": 2.5}; SIDE: BOTH SIDES; bracket sym15u | 13 | L33ea71d5 | NEW | RM7 | 0.025 | 0.193 | 268 | 982 | 10859 | 5081 | -19030 | -6314 | 6.5 | 0.50 | 1547 | -1447 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.484 | 0.065 | 0 |
| 18 |  | 15 | YES | live book M7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_M7 | LIVE | JL3 | 0.017 | 0.146 | 144 | 1130 | 8679 | 7722 | -17285 | -11717 | 19.8 | 0.40 | 1172 | -762 | 0.43 | 0.40 | 95 | 5555 | +34 | RED | -376 | 26105 | +360 | RED | -356 | 16712 | +347 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 19 |  | 7 | YES | dollar-run bar 2000 [drb_2000]; ~3 bars/hour; trigger trig_bands_vwap / break {"minbars": 5, "k": 1.0}; SIDE: BOTH SIDES; bracket sym15u | 3 | L132040d5 | NEW | RM7 | 0.011 | 0.444 | 149 | 1281 | 13864 | 2888 | -28302 | -10754 | 5.5 | 0.52 | 1430 | -1518 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.419 | 0.097 | 0 |
| 20 |  | 17 | YES | time bar 7 min (tm420 = 420 seconds) [tm420]; ~9 bars/hour; trigger trig_xmarket_commod / with_GC {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 9 | Mb9a3dd42 | NEW | RM7 | 0.010 | 0.068 | 138 | 297 | 13474 | 4353 | -25713 | -9868 | 12.6 | 0.49 | 1078 | -1018 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.226 | 0.032 | 0 |
| 21 |  | 28 | YES | time bar 2 min [time_m_2]; ~30 bars/hour; trigger trig_xmarket_ym / diverge {"w": 30}; SIDE: LONG ONLY; bracket asym20u/10u | 30 | M5c2d1aaf | NEW | RM7 | 0.009 | -0.005 | 95 | -75 | 10805 | 14443 | -24535 | -10534 | 8.4 | 0.53 | 1469 | -1614 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.258 | 0.065 | 0 |
| 22 |  | 31 | YES | time bar 30 min (tm1800 = 1800 seconds) [tm1800]; ~2 bars/hour; trigger trig_xmarket_fast / follow_ES {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 2 | M3431b271 | NEW | RM7 | 0.008 | -0.024 | 40 | -125 | 4713 | 5220 | -12802 | -6209 | 3.7 | 0.50 | 1067 | -1045 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.419 | 0.032 | 0 |
| 23 |  | 27 | YES | range bar 20 ticks [rng_20]; ~38 bars/hour; trigger trig_levels_vwap_bands / break_native {"n": 1, "k": 0.0}; SIDE: LONG ONLY; bracket sym8u | 38 | M00720f70 | NEW | RM7 | 0.008 | -0.002 | 59 | -12 | 7467 | 6580 | -13931 | -5538 | 11.5 | 0.50 | 1477 | -1438 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.398 | 0.204 | 0 |
| 24 |  | 22 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_xmarket_rates / with_ZB {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket sym15u | 12 | M939512c1 | NEW | RM7 | 0.007 | 0.045 | 48 | 236 | 6908 | 5262 | -14633 | -6239 | 6.7 | 0.49 | 1475 | -1395 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.233 | 0.004 | 0 |
| 25 |  | 19 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_round / retest {"M": 6, "tol": 0.0}; SIDE: BOTH SIDES; bracket sym8u | 3 | WL2 | NEW | RM7 | 0.003 | 0.067 | 42 | 722 | 12945 | 10818 | -27581 | -9149 | 7.6 | 0.52 | 1559 | -1645 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 26 |  | 6 | YES | unresolved (cell not in ladder_cells.json) |  | LB2 | NEW | RM7 | 0.003 | 0.535 | 53 | 2212 | 19008 | 4135 | -29863 | -10777 | 17.0 | 0.50 | 1069 | -1058 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 27 |  | 39 | YES | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_xmarket_rates / with_ZN {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 180 | Me6b7eea5 | NEW | RM7 | 0.001 | -0.068 | 7 | -507 | 12108 | 7432 | -23018 | -8362 | 19.8 | 0.50 | 1057 | -1045 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.267 | 0.000 | 1 |
| 28 |  | 8 | YES | unresolved (cell not in ladder_cells.json) |  | LB1 | NEW | RM7 | 0.000 | 0.418 | 8 | 1451 | 19297 | 3475 | -32982 | -10309 | 10.1 | 0.47 | 1769 | -1578 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 29 |  | 40 | YES | unresolved (cell not in ladder_cells.json) |  | LB3 | NEW | ADD | -0.007 | -0.074 | -78 | -1037 | 10722 | 13961 | -26731 | -9764 | 8.5 | 0.47 | 1726 | -1568 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 30 |  | 32 | YES | range bar 14 ticks [rng_14]; ~72 bars/hour; trigger trig_tape_delta / follow_sm {"L": 200, "z": 2.0, "sm": 3}; SIDE: BOTH SIDES; bracket sym15u | 72 | WL6 | NEW | RM7 | -0.008 | -0.028 | -98 | -339 | 12936 | 12109 | -31719 | -13403 | 9.4 | 0.52 | 1534 | -1671 | 0.29 | 0.29 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 31 |  | 23 | YES | live book K7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour | 20 | LIVE_K7 | LIVE | JL3 | -0.008 | 0.030 | -40 | 164 | 5193 | 5366 | -12034 | -6678 | 17.6 | 0.41 | 1154 | -820 | 0.43 | 0.54 | 210 | 8189 |  | n/a | 150 | 9556 |  | n/a | 569 | 6933 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 32 |  | 16 | YES | range bar 28 ticks [rng_28]; ~20 bars/hour; trigger trig_levels_vwap_bands / break_native {"n": 1, "k": 0.5}; SIDE: BOTH SIDES; bracket sym8u | 20 | WL1 | NEW | ADD | -0.008 | 0.077 | -60 | 373 | 7481 | 4880 | -18933 | -9388 | 9.3 | 0.49 | 1675 | -1607 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 33 |  | 46 | YES | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_xmarket_fx / against_6E {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket sym15u | 180 | M544bd4e8 | NEW | RM7 | -0.012 | -0.124 | -98 | -1365 | 8264 | 11016 | -24840 | -6578 | 15.5 | 0.48 | 1192 | -1092 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.368 | 0.060 | 0 |
| 34 |  | 33 | YES | time bar 3 min [time_m_3]; ~20 bars/hour; trigger trig_tape_delta / cvd_fade {"N": 10, "L": 100, "z": 1.5}; SIDE: BOTH SIDES; bracket sym8u | 20 | WL7 | NEW | RM7 | -0.013 | -0.033 | -206 | -176 | 16110 | 5396 | -31113 | -8209 | 8.7 | 0.50 | 1384 | -1456 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 35 |  | 30 | YES | tick-imbalance bar 6000 [tib_6000]; ~9 bars/hour; trigger trig_bands_regchan / fade_linreg_native {"clk": 10, "k": 2.0}; SIDE: LONG ONLY; bracket plain60/60 | 9 | M517f5c7f | NEW | RM7 | -0.015 | -0.016 | -112 | -60 | 7552 | 3821 | -12220 | -3504 | 6.3 | 0.48 | 1040 | -977 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.355 | 0.032 | 0 |
| 36 |  | 44 | YES | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_xmarket_fx / with_6J {"w": 3, "thr": 1.0}; SIDE: LONG ONLY; bracket asym10u/20u | 180 | M21669c30 | NEW | RM7 | -0.018 | -0.097 | -149 | -782 | 8279 | 8070 | -17210 | -7647 | 13.7 | 0.38 | 1303 | -806 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.191 | 0.003 | 0 |
| 37 |  | 38 | YES | time bar 4 min [time_m_4]; ~15 bars/hour; trigger trig_momentum_roc / break {"len": 10, "wd": 1.0}; SIDE: BOTH SIDES; bracket asym20u/10u | 15 | WL9 | NEW | RM7 | -0.019 | -0.061 | -484 | -508 | 25229 | 8333 | -42863 | -15163 | 8.0 | 0.50 | 1467 | -1559 | 0.21 | 0.21 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 38 |  | 36 | YES | live book U7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 10 min (tm600 = 600 seconds) [tm600]; ~6 bars/hour | 6 | LIVE_U7 | LIVE | JL3 | -0.019 | -0.045 | -76 | -204 | 3917 | 4543 | -7975 | -3125 | 4.2 | 0.45 | 1150 | -992 | 0.43 | 0.45 | 29 | 4390 |  | n/a | -65 | 10025 |  | n/a | -67 | 4691 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 39 |  | 18 | YES | dollar-run bar 1200 [drb_1200]; ~5 bars/hour; trigger trig_bands_regchan / fade_linreg {"n": 20, "k": 2.0}; SIDE: LONG ONLY; bracket plain60/60 | 5 | M91376a6b | NEW | RM7 | -0.020 | 0.067 | -123 | 275 | 6203 | 4087 | -11357 | -4624 | 4.8 | 0.46 | 1043 | -951 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.168 | 0.002 | 0 |
| 40 |  | 20 | YES | time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour; trigger trig_xmarket_rty / diverge {"w": 60}; SIDE: LONG ONLY; bracket plain60/60 | 20 | M4b005962 | NEW | RM7 | -0.025 | 0.060 | -285 | 242 | 11589 | 4052 | -18904 | -6873 | 9.7 | 0.48 | 1066 | -1034 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.194 | 0.194 | 0 |
| 41 |  | 25 | YES | volume-run bar 700 [vrb_700]; ~15 bars/hour; trigger trig_levels_trendline / break_native {"n": 2, "k": 0.25}; SIDE: BOTH SIDES; bracket sym15u | 15 | WL4 | NEW | ADD | -0.033 | 0.020 | -346 | 153 | 10555 | 7689 | -21995 | -12384 | 7.5 | 0.48 | 1671 | -1629 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 42 |  | 45 | YES | time bar 1 min [time_m_1]; ~60 bars/hour; trigger trig_manual_cci / zero {"len": 20}; SIDE: LONG ONLY; bracket asym10u/20u | 60 | M3c4b265f | NEW | RM7 | -0.038 | -0.104 | -594 | -1288 | 15545 | 12393 | -33094 | -5928 | 10.4 | 0.45 | 1571 | -1392 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.581 | 0.258 | 0 |
| 43 |  | 41 | YES | session-volume-clock bar 80 bars/session [vsess_80]; ~13 bars/hour; trigger trig_trend_libstack / ema_hold {"len": 13, "hold": 3}; SIDE: LONG ONLY; bracket sym8u | 13 | Mf71d5bc4 | NEW | RM7 | -0.039 | -0.081 | -397 | -658 | 10192 | 8176 | -24600 | -8319 | 6.7 | 0.49 | 1496 | -1528 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.468 | 0.144 | 0 |
| 44 |  | 48 | YES | time bar 2 min (tm120 = 120 seconds) [tm120]; ~30 bars/hour; trigger trig_levels_vwap_bands / retest_native {"M": 10, "tol": 0.5}; SIDE: BOTH SIDES; bracket sym30u | 30 | LA3 | NEW | RM7 | -0.040 | -0.149 | -1025 | -2465 | 25459 | 16599 | -57283 | -13228 | 9.3 | 0.48 | 1646 | -1715 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 45 |  | 35 | YES | time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour; trigger trig_xmarket_commod / with_GC {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket sym15u | 60 | M7c0e6e7c | NEW | RM7 | -0.043 | -0.043 | -739 | -405 | 17174 | 9426 | -28797 | -7943 | 9.9 | 0.50 | 1433 | -1571 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.419 | 0.613 | 0 |
| 46 |  | 43 | YES | volume bar 1700 contracts [vol_1700]; ~6 bars/hour; trigger trig_levels_vwap_bands / reject {"tol": 1.0, "conf": "body"}; SIDE: LONG ONLY; bracket plain60/60 | 6 | M31df28a3 | NEW | RM7 | -0.045 | -0.095 | -1024 | -566 | 22912 | 5925 | -33872 | -6062 | 14.2 | 0.45 | 1083 | -1003 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.226 | 0.032 | 0 |
| 47 |  | 37 | YES | volume-run bar 400 [vrb_400]; ~44 bars/hour; trigger trig_bands_regchan / break_stderr {"n": 40, "k": 2.5}; SIDE: LONG ONLY; bracket sym15u | 44 | M758f3025 | NEW | RM7 | -0.045 | -0.048 | -736 | -309 | 16387 | 6401 | -27221 | -8149 | 6.6 | 0.47 | 1525 | -1586 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.359 | 0.012 | 0 |
| 48 |  | 47 | YES | tick-imbalance bar 1200 [tib_1200]; ~46 bars/hour; trigger trig_bands_bollinger / break {"n": 20, "k": 1.5}; SIDE: LONG ONLY; bracket sym15u | 46 | M5b908be1 | NEW | RM7 | -0.051 | -0.131 | -577 | -1228 | 11412 | 9347 | -27035 | -8254 | 8.6 | 0.52 | 1466 | -1713 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN | 0.548 | 0.258 | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| K7 | -2142 | 461 | 26 | 3589 | -1678 / 9868 | 5661 | 264.2% | 478 |
| P7 | 27768 | 400 | 27 | 22654 | 13971 / 28485 | 5982 | 21.5% | 421 |
| U7 | 18214 | 110 | 27 | 19845 | 12734 / 27121 | 3189 | 17.5% | 118 |
| M7 | -7247 | 518 | 1 | -4602 | -4602 / -4602 | 2645 | 36.5% | 524 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 34 pairs over 17 cells): mean abs difference of its own L6M total $4898 = 294.7% of |total| (median 37.1%, 90th pct 320.6%); trade-count differences: mean abs 5.5 trades (primary mean 245).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_london.csv; all columns: best_books_london_full.csv; status file best_books_london.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
