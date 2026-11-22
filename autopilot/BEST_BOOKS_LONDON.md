# BEST_BOOKS_LONDON - own-merit scorecard, London session (W-BEST; GENERATED AT 2026-11-22 11:07:03Z UTC (a stale page = the cron has stopped; heartbeat /mnt/l2/l2vast/_split/best_books_*.status mtime); first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 732 distinct cells scored (96 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 4 live-book rows; L6M $/wk > 0: 222; L6M and L3M > 0: 126; labels {'BEST-AVAILABLE-NOT-PROVEN': 510, 'WEAK-BUT-POSITIVE': 194, 'LEAD': 28}. Job errors: 0. Run 339 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## London TOP 10 on own merit (plain words; old rank = rank before the stale re-runs started, 22:07Z)

| rank | old rank | cell | side | bar | trigger | bracket | L6M $/wk | L6M ulcer | status |
|---|---|---|---|---|---|---|---|---|---|
| 1 | new | LA5 | BOTH SIDES | volume bar 500 contracts | trig_levels_vwap / break {"n": 3, "k": 0.25} | asym15u/30u | 2138 | 3819 | ok |
| 2 | new | Lc78f2492 | BOTH SIDES | Renko bar 20 ticks | trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0} | plain60/60 | 937 | 3259 | ok |
| 4 | new | M1dfc2f39 | LONG ONLY | time bar 2 min | trig_xmarket_nkd / follow {"w": 1, "thr": 1.0} | plain60/60 | 968 | 4021 | ok |
| 5 | new | M823f025d | LONG ONLY | tick-count bar 500 prints | trig_xmarket_rates / with_ZB {"w": 5, "thr": 1.0} | plain60/60 | 1037 | 5022 | ok |
| 6 | new | L1dcd5850 | BOTH SIDES | tick-count bar 8000 prints | trig_book_imb / delta_fade {"lv": 5, "thr": 0.2} | plain60/60 | 542 | 2700 | ok |
| 7 | new | L7f4c2c7f | BOTH SIDES | session-volume-clock bar 200 bars/session | trig_levels_stack / reject_native {"k": 2, "cw": 1.0} | asym20u/10u | 1500 | 7957 | ok |
| 8 | new | LB5 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1243 | 7443 | ok |
| 9 | new | M5e60d82e | LONG ONLY | UniRenko bar 40 ticks | trig_book_cancel / net_follow {"L": 50, "z": 1.0} | plain60/60 | 548 | 3310 | ok |
| 10 | new | L1de6d125 | BOTH SIDES | CUSUM-event bar 28 ticks | trig_trend_macd / hist_turn_native {"len": 26, "width": 0.03} | sym15u | 1137 | 6934 | ok |
| 11 | new | Lf53aa68f | BOTH SIDES | momentum bar 40 ticks | trig_book_imb / delta_fade {"lv": 10, "thr": 0.4} | sym15u | 741 | 4585 | ok |

Stale-pending cells (their old results are NOT ranked until re-run; listed in the _full.csv with stale=1 and no rank): 0; of them in the OLD top 50: 0 (none in the old top 10).

## Legend: bar codes (plain name, what the size number means, bars per hour)

Bars per hour = mean over every London session (02:00-08:30, 6.5 h ET) in 2026-05..2026-10 of (bars in the session / session hours), measured from the bar stores /mnt/l2/l2vast/_bars (live tm-rows: stores time_m_N / time_s_N, else 3600/N). Fast bars cost processing: a rate of 500 bars/hour is a bar every 7 seconds.

**Time bars: "time_m_3" = 3 MINUTES; "time_s_30" = 30 SECONDS; "tm180" = 180 SECONDS = 3 minutes (the number after tm is always seconds; tm60 = 1 minute, tm600 = 10 minutes).** Source: code/th_grid/gjob.py row_info (tm = time_m size N seconds) and autopilot/BAR_REGISTRY.md.

| code | plain name | size number means | bars/hour over all sizes in the store (min - max) | used in this top 50: size -> bars/hour |
|---|---|---|---|---|
| ? | ? bar | see BAR_REGISTRY.md | n/a (no store) | ?: nan |
| cusum | CUSUM-event bar | threshold in ticks (scaled by trailing daily range) | 1 - 131 | cusum_28: 20 |
| dib | dollar-imbalance bar | expected prints per bar (information-driven) | 1 - 199 | dib_400: 135; dib_2000: 37 |
| dlt | delta bar | contracts of net aggressor delta per bar | 1 - 61 | dlt_150: 5; dlt_250: 2 |
| dltor | delta-or-range bar | composite | 8 - 133 | dltor_B320: 88 |
| drb | dollar-run bar | expected prints per bar (information-driven) | 0 - 80 | drb_1200: 5 |
| frenko | flex Renko bar | ticks per brick (reversal bar half size) | 1 - 148 | frenko_28: 21; frenko_40: 10 |
| mom | momentum bar | ticks of net one-direction move per bar | 1 - 79 | mom_40: 5 |
| mrenko | median Renko bar | ticks per brick | 0 - 56 | mrenko_20: 14 |
| pasl | price-action swing-leg bar | ticks | 2 - 13 | pasl_10: 13 |
| renko | Renko bar | ticks per brick | 0 - 42 | renko_20: 11 |
| rng | range bar | ticks of high-low range per bar (1 tick = 0.25 pt) | 1 - 129 | rng_10: 129; rng_20: 38; rng_28: 20; rng_80: 3 |
| tib | tick-imbalance bar | expected prints per bar (information-driven; scaled by trailing prints) | 1 - 183 | tib_6000: 9; tib_15000: 3 |
| tick | tick-count bar | trade prints per bar (scaled daily by trailing print count) | 1 - 21 | tick_500: 12; tick_2000: 3; tick_5000: 1; tick_8000: 1 |
| time_m | time bar | minutes per bar | 0 - 60 | time_m_2: 30; time_m_5: 12; time_m_10: 6; time_m_13: 5 |
| tm | time bar | seconds per bar (tm180 = 180 s = 3 min) | 3600 / seconds (tm60 = 60/h, tm180 = 20/h, tm600 = 6/h) | tm10: 354; tm20: 180; tm60: 60; tm420: 9 |
| urenko | UniRenko bar | ticks per brick | 1 - 80 | urenko_14: 42; urenko_20: 21; urenko_40: 5 |
| vol | volume bar | contracts per bar (scaled daily by trailing volume) | 2 - 27 | vol_500: 19 |
| vsess | session-volume-clock bar | bars per session (vsess 30 = a bar every 1/30 of the session volume) | 5 - 99 | vsess_450: 75; vsess_200: 34; vsess_120: 20 |
| wrenko | Renko-with-wicks bar | ticks per brick | 0 - 42 | wrenko_10: 42 |
| anch | anchored equal-volume bar | anchor_B: bucket size | 0 - 1 |  |
| bmsg | book-message bar | one bar per N MBO book messages (B-code = size step, 500 to 64,000 messages) | 5 - 88 |  |
| bmsgq | quote-message bar | B-code size step | 5 - 88 |  |
| cdr | cumulative-delta-range bar | contracts: range of the running cumulative delta inside a bar | 0 - 14 |  |
| dchg | directional-change bar | reversal threshold in ticks (scaled) | 1 - 70 |  |
| dol | dollar bar | contract-equivalents at 15,000 (bar closes at N x 20 x 15,000 dollars traded; scaled daily) | 2 - 25 |  |
| entropy | entropy bar | surprise threshold (B-code) | 5 - 83 |  |
| ha | Heikin-Ashi bar | on top of another bar | 13 - 55 |  |
| kagi | Kagi bar | reversal ticks | 1 - 70 |  |
| kal | kal bar | see BAR_REGISTRY.md | 13 - 55 |  |
| lbrk | line-break bar | id lbrk_N_B: N lines, base box B ticks | 2 - 23 |  |
| med | med bar | see BAR_REGISTRY.md | 13 - 55 |  |
| micro | microprice-change bar | changes per bar | 5 - 89 |  |
| pnf | point-and-figure column bar | ticks per box (3-box reversal) | 0 - 27 |  |
| qmid | mid-change bar | mid-price changes per bar | 5 - 89 |  |
| rngor | range-or-time bar | ticks_seconds | 7 - 122 |  |
| sessrng | session-range-clock bar | bars per session | 6 - 96 |  |
| swing_atr | swing bar | retrace in ATR multiples | 2 - 110 |  |
| swing_pct | swing bar | retrace in basis points of price | 0 - 14 |  |
| t3 | t3 bar | see BAR_REGISTRY.md | 13 - 55 |  |
| time_s | time bar | seconds per bar | 80 - 664 |  |
| tpo | tpo bar | see BAR_REGISTRY.md | 2 - 2 |  |
| trb | tick-run bar | expected prints per bar (information-driven) | 0 - 78 |  |
| trend | trend bar | ticks | 0 - 42 |  |
| tsf | trade-size-filtered volume bar | contracts per bar counting only large prints (id tsf_L_N: L = min print size) | 0 - 37 |  |
| typ | typ bar | see BAR_REGISTRY.md | 13 - 55 |  |
| vfp | footprint bar | base series | 3 - 275 |  |
| vfpL | vfpL bar | see BAR_REGISTRY.md | 614 - 3115 |  |
| vib | volume-imbalance bar | expected prints per bar (information-driven) | 1 - 200 |  |
| vnorm | variance-normalised bar | bars per day-equivalent | 1 - 41 |  |
| volor | volume-or-range bar | composite | 7 - 118 |  |
| vrb | volume-run bar | expected prints per bar (information-driven) | 0 - 91 |  |

## Prior-year colour summary (REPORT ONLY; the rule and the labels are unchanged)

- New books, top 200 by own-merit rank (200 books): GREEN 0 / AMBER 0 / RED 7 / not landed 193.
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

## Where the live books rank (same table, same scoring; 736 rows in this session)

| rank | OLD rank (before re-runs) | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3 |  | 36 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 151 |  | 72 |  | live book M7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_M7 | LIVE | JL3 | 0.017 | 0.146 | 144 | 1130 | 8679 | 7722 | -17285 | -11717 | 19.8 | 0.40 | 1172 | -762 | 0.43 | 0.40 | 95 | 5555 | +34 | RED | -376 | 26105 | +360 | RED | -356 | 16712 | +347 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 279 |  | 165 |  | live book K7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour | 20 | LIVE_K7 | LIVE | JL3 | -0.008 | 0.030 | -40 | 164 | 5193 | 5366 | -12034 | -6678 | 17.6 | 0.41 | 1154 | -820 | 0.43 | 0.54 | 210 | 8189 |  | n/a | 150 | 9556 |  | n/a | 569 | 6933 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 363 |  | 346 |  | live book U7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 10 min (tm600 = 600 seconds) [tm600]; ~6 bars/hour | 6 | LIVE_U7 | LIVE | JL3 | -0.019 | -0.045 | -76 | -204 | 3917 | 4543 | -7975 | -3125 | 4.2 | 0.45 | 1150 | -992 | 0.43 | 0.45 | 29 | 4390 |  | n/a | -65 | 10025 |  | n/a | -67 | 4691 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

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
| 1 |  | 9 | YES | volume bar 500 contracts [vol_500]; ~19 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.25}; SIDE: BOTH SIDES; bracket asym15u/30u | 19 | LA5 | NEW | RM7 | 0.560 | 0.606 | 2138 | 2262 | 3819 | 3731 | -9472 | -4964 | 7.6 | 0.56 | 1693 | -1536 | 0.71 | 0.55 | 311 | 2588 | +85 | RED | -71 | 13068 | +103 | RED | 384 | 11549 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 |  | 48 | YES | Renko bar 20 ticks [renko_20]; ~11 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 11 | Lc78f2492 | NEW | RM7 | 0.287 | 0.247 | 937 | 851 | 3259 | 3450 | -9043 | -4829 | 7.5 | 0.54 | 1069 | -976 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.214 | 0.002 | 1 |
| 3 |  | 36 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 4 |  | 60 |  | time bar 2 min [time_m_2]; ~30 bars/hour; trigger trig_xmarket_nkd / follow {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 30 | M1dfc2f39 | NEW | RM7 | 0.241 | 0.170 | 968 | 795 | 4021 | 4686 | -10910 | -3609 | 10.5 | 0.54 | 1088 | -1076 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.423 | 0.008 | 0 |
| 5 |  | 211 |  | tick-count bar 500 prints [tick_500]; ~12 bars/hour; trigger trig_xmarket_rates / with_ZB {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 12 | M823f025d | NEW | RM7 | 0.207 | 0.000 | 1037 | 0 | 5022 | 4171 | -11738 | -4438 | 12.1 | 0.52 | 1041 | -964 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.145 | 0.003 | 0 |
| 6 |  | 90 |  | tick-count bar 8000 prints [tick_8000]; ~1 bars/hour; trigger trig_book_imb / delta_fade {"lv": 5, "thr": 0.2}; SIDE: BOTH SIDES; bracket plain60/60 | 1 | L1dcd5850 | NEW | RM7 | 0.201 | 0.101 | 542 | 272 | 2700 | 2694 | -7657 | -4838 | 7.6 | 0.51 | 1052 | -939 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.353 | 0.025 | 0 |
| 7 |  | 454 |  | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_levels_stack / reject_native {"k": 2, "cw": 1.0}; SIDE: BOTH SIDES; bracket asym20u/10u | 34 | L7f4c2c7f | NEW | RM7 | 0.189 | -0.072 | 1500 | -629 | 7957 | 8680 | -21449 | -9924 | 9.5 | 0.52 | 1722 | -1565 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 1.000 | 1.000 | 0 |
| 8 |  | 65 |  | unresolved (cell not in ladder_cells.json) |  | LB5 | NEW | RM7 | 0.167 | 0.157 | 1243 | 660 | 7443 | 4202 | -19947 | -10749 | 8.9 | 0.50 | 1798 | -1504 | 0.79 | 0.61 | 575 | 2787 | +54 | RED | 715 | 4719 | +42 | RED | 174 | 9970 | +90 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 9 |  | 248 |  | UniRenko bar 40 ticks [urenko_40]; ~5 bars/hour; trigger trig_book_cancel / net_follow {"L": 50, "z": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 5 | M5e60d82e | NEW | RM7 | 0.166 | -0.011 | 548 | -33 | 3310 | 3106 | -8227 | -5723 | 9.5 | 0.52 | 1063 | -1040 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.405 | 0.010 | 0 |
| 10 |  | 93 |  | CUSUM-event bar 28 ticks [cusum_28]; ~20 bars/hour; trigger trig_trend_macd / hist_turn_native {"len": 26, "width": 0.03}; SIDE: BOTH SIDES; bracket sym15u | 20 | L1de6d125 | NEW | RM7 | 0.164 | 0.100 | 1137 | 409 | 6934 | 4100 | -18182 | -8329 | 8.9 | 0.53 | 1630 | -1596 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.403 | 0.027 | 0 |
| 11 |  | 199 |  | momentum bar 40 ticks [mom_40]; ~5 bars/hour; trigger trig_book_imb / delta_fade {"lv": 10, "thr": 0.4}; SIDE: BOTH SIDES; bracket sym15u | 5 | Lf53aa68f | NEW | RM7 | 0.162 | 0.010 | 741 | 62 | 4585 | 6264 | -11819 | -4359 | 5.8 | 0.51 | 1569 | -1392 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.473 | 0.040 | 0 |
| 12 |  | 247 |  | unresolved (cell not in ladder_cells.json) |  | LB7 | NEW | RM7 | 0.159 | -0.010 | 638 | -55 | 4019 | 5258 | -11993 | -5989 | 7.7 | 0.52 | 1064 | -1000 | 0.50 | 0.63 | 547 | 3121 | +14 | GREEN |  |  |  | n/a | 545 | 5140 | +33 | RED | RED (2 of 3 yrs) | WEAK-BUT-POSITIVE |  |  | 0 |
| 13 |  | 87 |  | time bar 7 min (tm420 = 420 seconds) [tm420]; ~9 bars/hour; trigger trig_momentum_stoch / zone_break {"len": 5, "lvl": 70}; SIDE: BOTH SIDES; bracket plain60/60 | 9 | Lcc09204f | NEW | RM7 | 0.149 | 0.114 | 893 | 611 | 6011 | 5373 | -15820 | -9743 | 17.2 | 0.52 | 1088 | -1055 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.234 | 0.001 | 1 |
| 14 |  | 174 |  | CUSUM-event bar 28 ticks [cusum_28]; ~20 bars/hour; trigger trig_book_micro / fade_native {"L": 3600, "z": 2.0}; SIDE: BOTH SIDES; bracket sym15u | 20 | L242d12c9 | NEW | RM7 | 0.146 | 0.024 | 882 | 175 | 6034 | 7303 | -17565 | -10274 | 7.2 | 0.51 | 1728 | -1535 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.283 | 0.016 | 0 |
| 15 |  | 63 |  | delta-or-range bar B320 [dltor_B320]; ~88 bars/hour; trigger trig_levels_ob5 / false_break {"M": 2, "k": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 88 | Ld8d62c36 | NEW | RM7 | 0.139 | 0.161 | 737 | 691 | 5305 | 4283 | -15346 | -5299 | 7.3 | 0.52 | 1123 | -999 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.245 | 0.037 | 0 |
| 16 |  | 13 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym15u | 12 | LA4 | NEW | RM7 | 0.137 | 0.545 | 1187 | 1920 | 8659 | 3525 | -23834 | -10953 | 8.4 | 0.54 | 1683 | -1691 | 0.57 | 0.52 | 388 | 4949 | +67 | RED | 161 | 6285 | +86 | RED | 557 | 7407 | +53 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 17 |  | 67 |  | tick-imbalance bar 15000 [tib_15000]; ~3 bars/hour; trigger trig_manual_macd / sigcross_native {"f": 5, "s": 13, "g": 4}; SIDE: LONG ONLY; bracket plain60/60 | 3 | Md12eae61 | NEW | RM7 | 0.133 | 0.153 | 610 | 604 | 4591 | 3940 | -10661 | -4163 | 12.3 | 0.50 | 1075 | -982 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.622 | 0.169 | 0 |
| 18 |  | 17 | YES | UniRenko bar 14 ticks [urenko_14]; ~42 bars/hour; trigger trig_levels_sdx5 / retest {"d": "E", "M": 6, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 42 | L431323b6 | NEW | RM7 | 0.132 | 0.514 | 535 | 1016 | 4050 | 1975 | -8507 | -3124 | 5.8 | 0.53 | 1025 | -958 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.348 | 0.025 | 0 |
| 19 |  | 53 |  | UniRenko bar 20 ticks [urenko_20]; ~21 bars/hour; trigger trig_levels_fibr_pd / break_native {"n": 3, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 21 | M9123cdc8 | NEW | RM7 | 0.126 | 0.202 | 633 | 811 | 5029 | 4017 | -9620 | -5788 | 9.1 | 0.54 | 1033 | -1061 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.387 | 0.452 | 0 |
| 20 |  | 117 |  | median Renko bar 20 ticks [mrenko_20]; ~14 bars/hour; trigger trig_levels_trendline / break {"n": 2, "k": 0.0}; SIDE: LONG ONLY; bracket plain60/60 | 14 | M45234700 | NEW | RM7 | 0.125 | 0.067 | 623 | 372 | 4984 | 5544 | -14165 | -5178 | 10.5 | 0.52 | 1076 | -1034 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.613 | 0.323 | 0 |
| 21 |  | 49 | YES | unresolved (cell not in ladder_cells.json) |  | LB4 | NEW | RM7 | 0.124 | 0.237 | 913 | 1160 | 7374 | 4895 | -15711 | -8339 | 7.5 | 0.51 | 1653 | -1457 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 22 |  | 132 |  | tick-imbalance bar 6000 [tib_6000]; ~9 bars/hour; trigger trig_levels_fib5 / retest_native {"M": 10, "tol": 0.5}; SIDE: LONG ONLY; bracket sym15u | 9 | Mcec644cc | NEW | RM7 | 0.117 | 0.055 | 615 | 341 | 5263 | 6195 | -16697 | -6024 | 7.3 | 0.51 | 1669 | -1569 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.642 | 0.139 | 0 |
| 23 |  | 275 |  | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_levels_vwap_bands / break_native {"n": 2, "k": 0.0}; SIDE: LONG ONLY; bracket sym30u | 180 | M66f019e6 | NEW | RM7 | 0.115 | -0.022 | 725 | -161 | 6323 | 7400 | -15302 | -6724 | 10.3 | 0.50 | 1670 | -1541 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.756 | 0.040 | 1 |
| 24 |  | 164 |  | time bar 10 s (tm10 = 10 seconds) [tm10]; ~354 bars/hour; trigger trig_structure_orb / orb {"or_min": 10, "buf": 0.0}; SIDE: LONG ONLY; bracket asym10u/20u | 354 | M1846cba7 | NEW | RM7 | 0.114 | 0.032 | 260 | 57 | 2275 | 1780 | -4512 | -1989 | 4.2 | 0.33 | 1213 | -515 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.486 | 0.007 | 0 |
| 25 |  | 314 |  | price-action swing-leg bar 10 [pasl_10]; ~13 bars/hour; trigger trig_xmarket_ym / follow {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 13 | M918c3f7e | NEW | RM7 | 0.113 | -0.036 | 668 | -178 | 5913 | 4995 | -11436 | -5103 | 9.1 | 0.52 | 1088 | -1021 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.537 | 0.070 | 0 |
| 26 |  | 7 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_zones / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym8u | 3 | LA1 | NEW | RM7 | 0.111 | 0.680 | 751 | 2284 | 6794 | 3360 | -14518 | -9369 | 6.1 | 0.54 | 1559 | -1589 | 0.64 | 0.56 | 582 | 2818 | +22 | AMBER | 342 | 5252 | +54 | RED | 212 | 6632 | +72 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 27 |  | 66 |  | range bar 10 ticks [rng_10]; ~129 bars/hour; trigger trig_levels_fib15 / retest {"M": 3, "tol": 0.0}; SIDE: LONG ONLY; bracket plain60/60 | 129 | Mc430fce3 | NEW | RM7 | 0.108 | 0.154 | 533 | 712 | 4944 | 4617 | -12226 | -8236 | 14.6 | 0.51 | 1070 | -1025 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.548 | 0.258 | 1 |
| 28 |  | 80 |  | tick-count bar 2000 prints [tick_2000]; ~3 bars/hour; trigger trig_tape_delta / follow_native {"L": 900, "z": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 3 | L0770c130 | NEW | RM7 | 0.106 | 0.128 | 393 | 320 | 3703 | 2511 | -7990 | -3240 | 5.0 | 0.53 | 1058 | -1029 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.391 | 0.005 | 0 |
| 29 |  | 220 |  | dollar-imbalance bar 400 [dib_400]; ~135 bars/hour; trigger trig_levels_fib15 / break_native {"n": 3, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 135 | Maf90bb1d | NEW | RM7 | 0.103 | -0.001 | 477 | -7 | 4650 | 5382 | -13700 | -9426 | 15.9 | 0.50 | 1078 | -1028 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.548 | 0.355 | 0 |
| 30 |  | 4 | YES | dollar-imbalance bar 2000 [dib_2000]; ~37 bars/hour; trigger trig_book_imb / delta_fade {"lv": 1, "thr": 0.2}; SIDE: BOTH SIDES; bracket plain60/60 | 37 | L7821cba9 | NEW | RM7 | 0.102 | 0.788 | 958 | 2626 | 9426 | 3331 | -22628 | -10126 | 21.8 | 0.50 | 1091 | -1017 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.303 | 0.003 | 0 |
| 31 |  | 82 |  | tick-count bar 5000 prints [tick_5000]; ~1 bars/hour; trigger trig_tape_run / run_fade {"thr": 6}; SIDE: BOTH SIDES; bracket sym15u | 1 | L4fda6ab6 | NEW | RM7 | 0.096 | 0.125 | 417 | 425 | 4368 | 3395 | -9147 | -3829 | 4.5 | 0.47 | 1601 | -1270 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.394 | 0.002 | 0 |
| 32 |  | 12 | YES | dollar-run bar 1200 [drb_1200]; ~5 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 5 | Ldb5d7d6f | NEW | RM7 | 0.095 | 0.601 | 644 | 1273 | 6785 | 2120 | -13344 | -4759 | 6.8 | 0.54 | 1020 | -976 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.262 | 0.002 | 0 |
| 33 |  | 1 | YES | flex Renko bar 28 ticks [frenko_28]; ~21 bars/hour; trigger trig_levels_prior_day / retest_native {"M": 6, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 21 | L59c87ce9 | NEW | RM7 | 0.094 | 1.421 | 425 | 1388 | 4505 | 977 | -10097 | -3529 | 4.9 | 0.55 | 1044 | -1068 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.351 | 0.013 | 0 |
| 34 |  | 43 | YES | delta bar 150 contracts [dlt_150]; ~5 bars/hour; trigger trig_levels_round / retest {"M": 6, "tol": 0.5}; SIDE: LONG ONLY; bracket sym15u | 5 | M02d86c09 | NEW | RM7 | 0.094 | 0.264 | 627 | 831 | 6650 | 3146 | -14257 | -5189 | 6.8 | 0.56 | 1480 | -1647 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.509 | 0.013 | 0 |
| 35 |  | 131 |  | Renko-with-wicks bar 10 ticks [wrenko_10]; ~42 bars/hour; trigger trig_trend_ma_hma / price_native {"len": 50, "width": 1.0}; SIDE: BOTH SIDES; bracket plain60/60 | 42 | Ldbb25a85 | NEW | RM7 | 0.093 | 0.055 | 840 | 609 | 9028 | 11055 | -24326 | -11347 | 19.5 | 0.51 | 1068 | -1039 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.358 | 0.239 | 0 |
| 36 |  | 64 |  | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_bands_bollinger / fade_native {"clk": 5, "k": 2.0}; SIDE: LONG ONLY; bracket plain60/60 | 34 | M940d156a | NEW | RM7 | 0.093 | 0.161 | 437 | 520 | 4694 | 3236 | -9393 | -4184 | 7.3 | 0.51 | 1036 | -958 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.271 | 0.012 | 0 |
| 37 |  | 98 |  | median Renko bar 20 ticks [mrenko_20]; ~14 bars/hour; trigger trig_book_pslope / fade_native {"L": 3600, "z": 2.0}; SIDE: LONG ONLY; bracket sym15u | 14 | Mea408185 | NEW | RM7 | 0.090 | 0.093 | 466 | 404 | 5161 | 4339 | -12508 | -5200 | 5.7 | 0.52 | 1592 | -1577 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.435 | 0.005 | 0 |
| 38 |  | 2 | YES | range bar 20 ticks [rng_20]; ~38 bars/hour; trigger trig_book_pslope / fade_native {"L": 3600, "z": 1.0}; SIDE: BOTH SIDES; bracket asym10u/20u | 38 | L56530558 | NEW | RM7 | 0.089 | 1.096 | 1519 | 2812 | 17054 | 2566 | -38833 | -11214 | 10.3 | 0.52 | 1741 | -1557 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.433 | 0.017 | 0 |
| 39 |  | 3 | YES | flex Renko bar 40 ticks [frenko_40]; ~10 bars/hour; trigger trig_tape_div / conf_follow {"N": 40, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 10 | M98f68a20 | NEW | RM7 | 0.089 | 1.008 | 355 | 813 | 3986 | 806 | -8841 | -3614 | 3.3 | 0.55 | 1034 | -1035 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.393 | 0.008 | 0 |
| 40 |  | 186 |  | price-action swing-leg bar 10 [pasl_10]; ~13 bars/hour; trigger trig_book_imb / delta_fade {"lv": 1, "thr": 0.2}; SIDE: LONG ONLY; bracket plain60/60 | 13 | M9960e766 | NEW | RM7 | 0.089 | 0.016 | 588 | 131 | 6637 | 8259 | -15008 | -5517 | 16.3 | 0.50 | 1111 | -1039 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.355 | 0.419 | 0 |
| 41 |  | 285 |  | delta-or-range bar B320 [dltor_B320]; ~88 bars/hour; trigger trig_levels_fib60 / break_native {"n": 3, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 88 | M59901361 | NEW | RM7 | 0.088 | -0.026 | 529 | -217 | 6045 | 8194 | -14809 | -5582 | 12.3 | 0.50 | 1079 | -1012 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.355 | 0.290 | 0 |
| 42 |  | 32 | YES | delta bar 250 contracts [dlt_250]; ~2 bars/hour; trigger trig_tape_stack / r5_follow {"k": 2}; SIDE: LONG ONLY; bracket plain60/60 | 2 | M02a97742 | NEW | RM7 | 0.087 | 0.339 | 430 | 613 | 4912 | 1811 | -10680 | -5993 | 8.9 | 0.51 | 1039 | -995 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.239 | 0.045 | 0 |
| 43 |  | 15 | YES | time bar 10 min [time_m_10]; ~6 bars/hour; trigger trig_xmarket_rty / revert {"w": 1, "thr": 1.0}; SIDE: BOTH SIDES; bracket sym15u | 6 | L0783eb1c | NEW | RM7 | 0.084 | 0.536 | 685 | 1654 | 8123 | 3084 | -21367 | -8993 | 6.7 | 0.50 | 1712 | -1489 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.478 | 0.025 | 0 |
| 44 |  | 110 |  | time bar 13 min [time_m_13]; ~5 bars/hour; trigger trig_book_dwm / drift_fade {"L": 100, "z": 1.5}; SIDE: BOTH SIDES; bracket plain60/60 | 5 | L6516b348 | NEW | RM7 | 0.084 | 0.077 | 314 | 363 | 3745 | 4739 | -8879 | -4229 | 6.2 | 0.52 | 1070 | -1034 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.338 | 0.016 | 0 |
| 45 |  | 45 | YES | delta bar 250 contracts [dlt_250]; ~2 bars/hour; trigger trig_xmarket_ym / confirm {"w": 5}; SIDE: LONG ONLY; bracket plain60/60 | 2 | Ma900a4e2 | NEW | RM7 | 0.083 | 0.257 | 364 | 537 | 4386 | 2091 | -9633 | -6403 | 6.4 | 0.51 | 1072 | -995 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.252 | 0.010 | 0 |
| 46 |  | 327 |  | session-volume-clock bar 450 bars/session [vsess_450]; ~75 bars/hour; trigger trig_tape_stoprun / follow_native {"N": 600, "k": 0.0}; SIDE: LONG ONLY; bracket sym15u | 75 | Mfb46e9fd | NEW | RM7 | 0.083 | -0.039 | 534 | -337 | 6442 | 8644 | -17093 | -5308 | 9.5 | 0.53 | 1537 | -1588 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.512 | 0.055 | 0 |
| 47 |  | 163 |  | session-volume-clock bar 120 bars/session [vsess_120]; ~20 bars/hour; trigger trig_levels_vwap / break {"n": 1, "k": 0.0}; SIDE: LONG ONLY; bracket sym30u | 20 | Mfe8e3605 | NEW | RM7 | 0.082 | 0.033 | 496 | 223 | 6046 | 6795 | -16672 | -8168 | 7.5 | 0.53 | 1584 | -1666 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.582 | 0.045 | 1 |
| 48 |  | 37 | YES | delta bar 150 contracts [dlt_150]; ~5 bars/hour; trigger trig_levels_fib5 / reject_native {"tol": 0.0, "conf": "close"}; SIDE: BOTH SIDES; bracket plain60/60 | 5 | Laf761091 | NEW | RM7 | 0.080 | 0.303 | 519 | 1309 | 6530 | 4317 | -13631 | -5773 | 14.1 | 0.51 | 1084 | -1051 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.311 | 0.005 | 1 |
| 49 |  | 97 |  | range bar 28 ticks [rng_28]; ~20 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 20 | Ld35a3b52 | NEW | RM7 | 0.078 | 0.094 | 537 | 680 | 6898 | 7229 | -18101 | -5513 | 9.7 | 0.51 | 1104 | -1019 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.318 | 0.003 | 0 |
| 50 |  | 188 |  | price-action swing-leg bar 10 [pasl_10]; ~13 bars/hour; trigger trig_book_imb / fade {"lv": 1, "thr": 0.35}; SIDE: LONG ONLY; bracket sym15u | 13 | M80c65587 | NEW | RM7 | 0.077 | 0.015 | 449 | 96 | 5800 | 6609 | -11748 | -6409 | 6.9 | 0.47 | 1784 | -1472 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.602 | 0.224 | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| K7 | -2142 | 461 | 809 | 3634 | -6155 / 12315 | 5914 | 276.0% | 474 |
| P7 | 27768 | 400 | 810 | 21494 | 13697 / 29549 | 6231 | 22.4% | 422 |
| U7 | 18214 | 110 | 810 | 19889 | 6985 / 30542 | 3142 | 17.2% | 119 |
| M7 | -7247 | 518 | 1 | -4602 | -4602 / -4602 | 2645 | 36.5% | 524 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 34 pairs over 17 cells): mean abs difference of its own L6M total $4898 = 294.7% of |total| (median 37.1%, 90th pct 320.6%); trade-count differences: mean abs 5.5 trades (primary mean 245).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_london.csv; all columns: best_books_london_full.csv; status file best_books_london.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
