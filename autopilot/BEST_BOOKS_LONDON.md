# BEST_BOOKS_LONDON - own-merit scorecard, London session (W-BEST; GENERATED AT 2026-11-21 06:37:02Z UTC (a stale page = the cron has stopped; heartbeat /mnt/l2/l2vast/_split/best_books_*.status mtime); first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 408 distinct cells scored (26 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 4 live-book rows; L6M $/wk > 0: 129; L6M and L3M > 0: 75; labels {'BEST-AVAILABLE-NOT-PROVEN': 279, 'WEAK-BUT-POSITIVE': 111, 'LEAD': 18}. Job errors: 0. Run 787 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## London TOP 10 on own merit (plain words; old rank = rank before the stale re-runs started, 22:07Z)

| rank | old rank | cell | side | bar | trigger | bracket | L6M $/wk | L6M ulcer | status |
|---|---|---|---|---|---|---|---|---|---|
| 1 | new | LA5 | BOTH SIDES | volume bar 500 contracts | trig_levels_vwap / break {"n": 3, "k": 0.25} | asym15u/30u | 2138 | 3819 | ok |
| 2 | new | L19201dfc | BOTH SIDES | trend bar 20 ticks | trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0} | plain60/60 | 937 | 3259 | ok |
| 4 | new | M1dfc2f39 | LONG ONLY | time bar 2 min | trig_xmarket_nkd / follow {"w": 1, "thr": 1.0} | plain60/60 | 968 | 4021 | ok |
| 5 | new | L7f4c2c7f | BOTH SIDES | session-volume-clock bar 200 bars/session | trig_levels_stack / reject_native {"k": 2, "cw": 1.0} | asym20u/10u | 1500 | 7957 | ok |
| 6 | new | LB5 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1243 | 7443 | ok |
| 7 | new | M5e60d82e | LONG ONLY | UniRenko bar 40 ticks | trig_book_cancel / net_follow {"L": 50, "z": 1.0} | plain60/60 | 548 | 3310 | ok |
| 8 | new | L1de6d125 | BOTH SIDES | CUSUM-event bar 28 ticks | trig_trend_macd / hist_turn_native {"len": 26, "width": 0.03} | sym15u | 1137 | 6934 | ok |
| 9 | new | LB7 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 638 | 4019 | ok |
| 10 | new | Lcc09204f | BOTH SIDES | time bar 7 min (tm420 = 420 seconds) | trig_momentum_stoch / zone_break {"len": 5, "lvl": 70} | plain60/60 | 893 | 6011 | ok |
| 11 | new | Ld8d62c36 | BOTH SIDES | delta-or-range bar B320 | trig_levels_ob5 / false_break {"M": 2, "k": 0.5} | plain60/60 | 737 | 5305 | ok |

Stale-pending cells (their old results are NOT ranked until re-run; listed in the _full.csv with stale=1 and no rank): 0; of them in the OLD top 50: 0 (none in the old top 10).

## Legend: bar codes (plain name, what the size number means, bars per hour)

Bars per hour = mean over every London session (02:00-08:30, 6.5 h ET) in 2026-05..2026-10 of (bars in the session / session hours), measured from the bar stores /mnt/l2/l2vast/_bars (live tm-rows: stores time_m_N / time_s_N, else 3600/N). Fast bars cost processing: a rate of 500 bars/hour is a bar every 7 seconds.

**Time bars: "time_m_3" = 3 MINUTES; "time_s_30" = 30 SECONDS; "tm180" = 180 SECONDS = 3 minutes (the number after tm is always seconds; tm60 = 1 minute, tm600 = 10 minutes).** Source: code/th_grid/gjob.py row_info (tm = time_m size N seconds) and autopilot/BAR_REGISTRY.md.

| code | plain name | size number means | bars/hour over all sizes in the store (min - max) | used in this top 50: size -> bars/hour |
|---|---|---|---|---|
| ? | ? bar | see BAR_REGISTRY.md | n/a (no store) | ?: nan |
| bmsg | book-message bar | one bar per N MBO book messages (B-code = size step, 500 to 64,000 messages) | 5 - 88 | bmsg_B500: 88 |
| bmsgq | quote-message bar | B-code size step | 5 - 88 | bmsgq_B080: 14 |
| cusum | CUSUM-event bar | threshold in ticks (scaled by trailing daily range) | 1 - 131 | cusum_20: 39; cusum_28: 20 |
| dchg | directional-change bar | reversal threshold in ticks (scaled) | 1 - 70 | dchg_28: 10 |
| dib | dollar-imbalance bar | expected prints per bar (information-driven) | 1 - 199 | dib_400: 135; dib_2000: 37 |
| dlt | delta bar | contracts of net aggressor delta per bar | 1 - 61 | dlt_150: 5; dlt_250: 2 |
| dltor | delta-or-range bar | composite | 8 - 133 | dltor_B320: 88 |
| drb | dollar-run bar | expected prints per bar (information-driven) | 0 - 80 | drb_1200: 5 |
| frenko | flex Renko bar | ticks per brick (reversal bar half size) | 1 - 148 | frenko_28: 21; frenko_40: 10 |
| kagi | Kagi bar | reversal ticks | 1 - 70 | kagi_20: 20 |
| pasl | price-action swing-leg bar | ticks | 2 - 13 | pasl_10: 13 |
| renko | Renko bar | ticks per brick | 0 - 42 | renko_56: 1 |
| rng | range bar | ticks of high-low range per bar (1 tick = 0.25 pt) | 1 - 129 | rng_10: 129; rng_20: 38; rng_28: 20; rng_80: 3 |
| tib | tick-imbalance bar | expected prints per bar (information-driven; scaled by trailing prints) | 1 - 183 | tib_15000: 3 |
| tick | tick-count bar | trade prints per bar (scaled daily by trailing print count) | 1 - 21 | tick_1300: 5 |
| time_m | time bar | minutes per bar | 0 - 60 | time_m_2: 30; time_m_3: 20; time_m_5: 12; time_m_10: 6 |
| tm | time bar | seconds per bar (tm180 = 180 s = 3 min) | 3600 / seconds (tm60 = 60/h, tm180 = 20/h, tm600 = 6/h) | tm10: 354; tm20: 180; tm60: 60; tm420: 9 |
| trend | trend bar | ticks | 0 - 42 | trend_20: 11 |
| urenko | UniRenko bar | ticks per brick | 1 - 80 | urenko_40: 5 |
| vol | volume bar | contracts per bar (scaled daily by trailing volume) | 2 - 27 | vol_500: 19; vol_1700: 6; vol_4000: 2 |
| vsess | session-volume-clock bar | bars per session (vsess 30 = a bar every 1/30 of the session volume) | 5 - 99 | vsess_600: 99; vsess_450: 75; vsess_200: 34 |
| anch | anchored equal-volume bar | anchor_B: bucket size | 0 - 1 |  |
| cdr | cumulative-delta-range bar | contracts: range of the running cumulative delta inside a bar | 0 - 14 |  |
| dol | dollar bar | contract-equivalents at 15,000 (bar closes at N x 20 x 15,000 dollars traded; scaled daily) | 2 - 25 |  |
| entropy | entropy bar | surprise threshold (B-code) | 5 - 83 |  |
| ha | Heikin-Ashi bar | on top of another bar | 13 - 55 |  |
| kal | kal bar | see BAR_REGISTRY.md | 13 - 55 |  |
| lbrk | line-break bar | id lbrk_N_B: N lines, base box B ticks | 2 - 23 |  |
| med | med bar | see BAR_REGISTRY.md | 13 - 55 |  |
| micro | microprice-change bar | changes per bar | 5 - 89 |  |
| mom | momentum bar | ticks of net one-direction move per bar | 1 - 79 |  |
| mrenko | median Renko bar | ticks per brick | 0 - 56 |  |
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
| tsf | trade-size-filtered volume bar | contracts per bar counting only large prints (id tsf_L_N: L = min print size) | 0 - 37 |  |
| typ | typ bar | see BAR_REGISTRY.md | 13 - 55 |  |
| vfp | footprint bar | base series | 3 - 275 |  |
| vfpL | vfpL bar | see BAR_REGISTRY.md | 614 - 3115 |  |
| vib | volume-imbalance bar | expected prints per bar (information-driven) | 1 - 200 |  |
| vnorm | variance-normalised bar | bars per day-equivalent | 1 - 41 |  |
| volor | volume-or-range bar | composite | 7 - 118 |  |
| vrb | volume-run bar | expected prints per bar (information-driven) | 0 - 91 |  |
| wrenko | Renko-with-wicks bar | ticks per brick | 0 - 42 |  |

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

## Where the live books rank (same table, same scoring; 412 rows in this session)

| rank | OLD rank (before re-runs) | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3 |  | 23 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 88 |  | 46 |  | live book M7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_M7 | LIVE | JL3 | 0.017 | 0.146 | 144 | 1130 | 8679 | 7722 | -17285 | -11717 | 19.8 | 0.40 | 1172 | -762 | 0.43 | 0.40 | 95 | 5555 | +34 | RED | -376 | 26105 | +360 | RED | -356 | 16712 | +347 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 163 |  | 101 |  | live book K7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour | 20 | LIVE_K7 | LIVE | JL3 | -0.008 | 0.030 | -40 | 164 | 5193 | 5366 | -12034 | -6678 | 17.6 | 0.41 | 1154 | -820 | 0.43 | 0.54 | 210 | 8189 |  | n/a | 150 | 9556 |  | n/a | 569 | 6933 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 208 |  | 195 |  | live book U7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 10 min (tm600 = 600 seconds) [tm600]; ~6 bars/hour | 6 | LIVE_U7 | LIVE | JL3 | -0.019 | -0.045 | -76 | -204 | 3917 | 4543 | -7975 | -3125 | 4.2 | 0.45 | 1150 | -992 | 0.43 | 0.45 | 29 | 4390 |  | n/a | -65 | 10025 |  | n/a | -67 | 4691 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

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
| 1 |  | 6 | YES | volume bar 500 contracts [vol_500]; ~19 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.25}; SIDE: BOTH SIDES; bracket asym15u/30u | 19 | LA5 | NEW | RM7 | 0.560 | 0.606 | 2138 | 2262 | 3819 | 3731 | -9472 | -4964 | 7.6 | 0.56 | 1693 | -1536 | 0.71 | 0.55 | 311 | 2588 | +85 | RED | -71 | 13068 | +103 | RED | 384 | 11549 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 |  | 32 | YES | trend bar 20 ticks [trend_20]; ~11 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 11 | L19201dfc | NEW | RM7 | 0.287 | 0.247 | 937 | 851 | 3259 | 3450 | -9043 | -4829 | 7.5 | 0.54 | 1069 | -976 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.211 | 0.002 | 0 |
| 3 |  | 23 | YES | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 4 |  | 38 | YES | time bar 2 min [time_m_2]; ~30 bars/hour; trigger trig_xmarket_nkd / follow {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 30 | M1dfc2f39 | NEW | RM7 | 0.241 | 0.170 | 968 | 795 | 4021 | 4686 | -10910 | -3609 | 10.5 | 0.54 | 1088 | -1076 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.423 | 0.008 | 0 |
| 5 |  | 255 |  | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_levels_stack / reject_native {"k": 2, "cw": 1.0}; SIDE: BOTH SIDES; bracket asym20u/10u | 34 | L7f4c2c7f | NEW | RM7 | 0.189 | -0.072 | 1500 | -629 | 7957 | 8680 | -21449 | -9924 | 9.5 | 0.52 | 1722 | -1565 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 1.000 | 1.000 | 0 |
| 6 |  | 42 | YES | unresolved (cell not in ladder_cells.json) |  | LB5 | NEW | RM7 | 0.167 | 0.157 | 1243 | 660 | 7443 | 4202 | -19947 | -10749 | 8.9 | 0.50 | 1798 | -1504 | 0.79 | 0.61 | 575 | 2787 | +54 | RED | 715 | 4719 | +42 | RED | 174 | 9970 | +90 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 7 |  | 145 |  | UniRenko bar 40 ticks [urenko_40]; ~5 bars/hour; trigger trig_book_cancel / net_follow {"L": 50, "z": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 5 | M5e60d82e | NEW | RM7 | 0.166 | -0.011 | 548 | -33 | 3310 | 3106 | -8227 | -5723 | 9.5 | 0.52 | 1063 | -1040 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.405 | 0.010 | 0 |
| 8 |  | 60 |  | CUSUM-event bar 28 ticks [cusum_28]; ~20 bars/hour; trigger trig_trend_macd / hist_turn_native {"len": 26, "width": 0.03}; SIDE: BOTH SIDES; bracket sym15u | 20 | L1de6d125 | NEW | RM7 | 0.164 | 0.100 | 1137 | 409 | 6934 | 4100 | -18182 | -8329 | 8.9 | 0.53 | 1630 | -1596 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.368 | 0.015 | 0 |
| 9 |  | 144 |  | unresolved (cell not in ladder_cells.json) |  | LB7 | NEW | RM7 | 0.159 | -0.010 | 638 | -55 | 4019 | 5258 | -11993 | -5989 | 7.7 | 0.52 | 1064 | -1000 | 0.50 | 0.63 | 547 | 3121 | +14 | GREEN |  |  |  | n/a | 545 | 5140 | +33 | RED | RED (2 of 3 yrs) | WEAK-BUT-POSITIVE |  |  | 0 |
| 10 |  | 55 |  | time bar 7 min (tm420 = 420 seconds) [tm420]; ~9 bars/hour; trigger trig_momentum_stoch / zone_break {"len": 5, "lvl": 70}; SIDE: BOTH SIDES; bracket plain60/60 | 9 | Lcc09204f | NEW | RM7 | 0.149 | 0.114 | 893 | 611 | 6011 | 5373 | -15820 | -9743 | 17.2 | 0.52 | 1088 | -1055 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.234 | 0.001 | 1 |
| 11 |  | 40 | YES | delta-or-range bar B320 [dltor_B320]; ~88 bars/hour; trigger trig_levels_ob5 / false_break {"M": 2, "k": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 88 | Ld8d62c36 | NEW | RM7 | 0.139 | 0.161 | 737 | 691 | 5305 | 4283 | -15346 | -5299 | 7.3 | 0.52 | 1123 | -999 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.245 | 0.037 | 0 |
| 12 |  | 9 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym15u | 12 | LA4 | NEW | RM7 | 0.137 | 0.545 | 1187 | 1920 | 8659 | 3525 | -23834 | -10953 | 8.4 | 0.54 | 1683 | -1691 | 0.57 | 0.52 | 388 | 4949 | +67 | RED | 161 | 6285 | +86 | RED | 557 | 7407 | +53 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 13 |  | 33 | YES | unresolved (cell not in ladder_cells.json) |  | LB4 | NEW | RM7 | 0.124 | 0.237 | 913 | 1160 | 7374 | 4895 | -15711 | -8339 | 7.5 | 0.51 | 1653 | -1457 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 14 |  | 100 |  | time bar 10 s (tm10 = 10 seconds) [tm10]; ~354 bars/hour; trigger trig_structure_orb / orb {"or_min": 10, "buf": 0.0}; SIDE: LONG ONLY; bracket asym10u/20u | 354 | M1846cba7 | NEW | RM7 | 0.114 | 0.032 | 260 | 57 | 2275 | 1780 | -4512 | -1989 | 4.2 | 0.33 | 1213 | -515 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.486 | 0.007 | 0 |
| 15 |  | 181 |  | price-action swing-leg bar 10 [pasl_10]; ~13 bars/hour; trigger trig_xmarket_ym / follow {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 13 | M918c3f7e | NEW | RM7 | 0.113 | -0.036 | 668 | -178 | 5913 | 4995 | -11436 | -5103 | 9.1 | 0.52 | 1088 | -1021 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.537 | 0.070 | 0 |
| 16 |  | 4 | YES | range bar 80 ticks [rng_80]; ~3 bars/hour; trigger trig_levels_zones / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym8u | 3 | LA1 | NEW | RM7 | 0.111 | 0.680 | 751 | 2284 | 6794 | 3360 | -14518 | -9369 | 6.1 | 0.54 | 1559 | -1589 | 0.64 | 0.56 | 582 | 2818 | +22 | AMBER | 342 | 5252 | +54 | RED | 212 | 6632 | +72 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 17 |  | 43 | YES | range bar 10 ticks [rng_10]; ~129 bars/hour; trigger trig_levels_fib15 / retest_native {"M": 3, "tol": 0.0}; SIDE: LONG ONLY; bracket plain60/60 | 129 | Mfdd53715 | NEW | RM7 | 0.108 | 0.154 | 533 | 712 | 4944 | 4617 | -12226 | -8236 | 14.6 | 0.51 | 1070 | -1025 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.527 | 0.129 | 0 |
| 18 |  | 131 |  | dollar-imbalance bar 400 [dib_400]; ~135 bars/hour; trigger trig_levels_fib15 / break_native {"n": 3, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 135 | Maf90bb1d | NEW | RM7 | 0.103 | -0.001 | 477 | -7 | 4650 | 5382 | -13700 | -9426 | 15.9 | 0.50 | 1078 | -1028 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.548 | 0.355 | 0 |
| 19 |  | 8 | YES | dollar-run bar 1200 [drb_1200]; ~5 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 5 | Ldb5d7d6f | NEW | RM7 | 0.095 | 0.601 | 644 | 1273 | 6785 | 2120 | -13344 | -4759 | 6.8 | 0.54 | 1020 | -976 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.262 | 0.002 | 0 |
| 20 |  | 1 | YES | flex Renko bar 28 ticks [frenko_28]; ~21 bars/hour; trigger trig_levels_prior_day / retest_native {"M": 6, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 21 | L59c87ce9 | NEW | RM7 | 0.094 | 1.421 | 425 | 1388 | 4505 | 977 | -10097 | -3529 | 4.9 | 0.55 | 1044 | -1068 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.351 | 0.013 | 0 |
| 21 |  | 28 | YES | delta bar 150 contracts [dlt_150]; ~5 bars/hour; trigger trig_levels_round / retest {"M": 6, "tol": 0.5}; SIDE: LONG ONLY; bracket sym15u | 5 | M02d86c09 | NEW | RM7 | 0.094 | 0.264 | 627 | 831 | 6650 | 3146 | -14257 | -5189 | 6.8 | 0.56 | 1480 | -1647 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.509 | 0.013 | 0 |
| 22 |  | 41 | YES | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_bands_bollinger / fade_native {"clk": 5, "k": 2.0}; SIDE: LONG ONLY; bracket plain60/60 | 34 | M940d156a | NEW | RM7 | 0.093 | 0.161 | 437 | 520 | 4694 | 3236 | -9393 | -4184 | 7.3 | 0.51 | 1036 | -958 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.271 | 0.012 | 0 |
| 23 |  | 2 | YES | flex Renko bar 40 ticks [frenko_40]; ~10 bars/hour; trigger trig_tape_div / conf_follow {"N": 40, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 10 | M98f68a20 | NEW | RM7 | 0.089 | 1.008 | 355 | 813 | 3986 | 806 | -8841 | -3614 | 3.3 | 0.55 | 1034 | -1035 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.393 | 0.008 | 0 |
| 24 |  | 20 | YES | delta bar 250 contracts [dlt_250]; ~2 bars/hour; trigger trig_tape_stack / r5_follow {"k": 2}; SIDE: LONG ONLY; bracket plain60/60 | 2 | M02a97742 | NEW | RM7 | 0.087 | 0.339 | 430 | 613 | 4912 | 1811 | -10680 | -5993 | 8.9 | 0.51 | 1039 | -995 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.239 | 0.045 | 0 |
| 25 |  | 11 | YES | time bar 10 min [time_m_10]; ~6 bars/hour; trigger trig_xmarket_rty / revert {"w": 1, "thr": 1.0}; SIDE: BOTH SIDES; bracket sym15u | 6 | L0783eb1c | NEW | RM7 | 0.084 | 0.536 | 685 | 1654 | 8123 | 3084 | -21367 | -8993 | 6.7 | 0.50 | 1712 | -1489 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.478 | 0.025 | 0 |
| 26 |  | 186 |  | session-volume-clock bar 450 bars/session [vsess_450]; ~75 bars/hour; trigger trig_tape_stoprun / follow_native {"N": 600, "k": 0.0}; SIDE: LONG ONLY; bracket sym15u | 75 | Mfb46e9fd | NEW | RM7 | 0.083 | -0.039 | 534 | -337 | 6442 | 8644 | -17093 | -5308 | 9.5 | 0.53 | 1537 | -1588 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.512 | 0.055 | 0 |
| 27 |  | 24 | YES | delta bar 150 contracts [dlt_150]; ~5 bars/hour; trigger trig_levels_fib5 / reject {"tol": 0.0, "conf": "close"}; SIDE: BOTH SIDES; bracket plain60/60 | 5 | Lc03cf521 | NEW | RM7 | 0.080 | 0.303 | 519 | 1309 | 6530 | 4317 | -13631 | -5773 | 14.1 | 0.51 | 1084 | -1051 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.360 | 0.002 | 0 |
| 28 |  | 63 |  | range bar 28 ticks [rng_28]; ~20 bars/hour; trigger trig_xmarket_commod / against_CL {"w": 15, "thr": 2.0}; SIDE: BOTH SIDES; bracket plain60/60 | 20 | Ld35a3b52 | NEW | RM7 | 0.078 | 0.094 | 537 | 680 | 6898 | 7229 | -18101 | -5513 | 9.7 | 0.51 | 1104 | -1019 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.318 | 0.003 | 0 |
| 29 |  | 115 |  | price-action swing-leg bar 10 [pasl_10]; ~13 bars/hour; trigger trig_book_imb / fade {"lv": 1, "thr": 0.35}; SIDE: LONG ONLY; bracket sym15u | 13 | M80c65587 | NEW | RM7 | 0.077 | 0.015 | 449 | 96 | 5800 | 6609 | -11748 | -6409 | 6.9 | 0.47 | 1784 | -1472 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.581 | 0.194 | 0 |
| 30 |  | 39 | YES | Renko bar 56 ticks [renko_56]; ~1 bars/hour; trigger trig_book_ice / follow {"thr": 1}; SIDE: BOTH SIDES; bracket plain60/60 | 1 | L4aff1799 | NEW | RM7 | 0.077 | 0.161 | 576 | 1005 | 7459 | 6228 | -14863 | -4448 | 11.3 | 0.52 | 1043 | -1032 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.384 | 0.015 | 0 |
| 31 |  | 29 | YES | quote-message bar B080 [bmsgq_B080]; ~14 bars/hour; trigger trig_structure_fvg / cont {"w": 0.75}; SIDE: LONG ONLY; bracket plain60/60 | 14 | M3904346f | NEW | RM7 | 0.075 | 0.263 | 311 | 714 | 4138 | 2719 | -7566 | -4679 | 5.6 | 0.51 | 1103 | -1021 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.444 | 0.006 | 0 |
| 32 |  | 114 |  | volume bar 1700 contracts [vol_1700]; ~6 bars/hour; trigger trig_levels_round / false_break {"M": 1, "k": 0.5}; SIDE: LONG ONLY; bracket sym8u | 6 | M3227e9eb | NEW | RM7 | 0.074 | 0.016 | 452 | 82 | 6076 | 4968 | -15255 | -6534 | 8.1 | 0.52 | 1643 | -1640 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.607 | 0.114 | 0 |
| 33 |  | 104 |  | directional-change bar 28 ticks [dchg_28]; ~10 bars/hour; trigger trig_confluence_user / u3b {"k": 2, "w": 1}; SIDE: LONG ONLY; bracket sym15u | 10 | Mbdf219dc | NEW | RM7 | 0.074 | 0.028 | 341 | 169 | 4603 | 6004 | -15787 | -8914 | 5.1 | 0.50 | 1606 | -1495 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.677 | 0.134 | 0 |
| 34 |  | 76 |  | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_levels_vwap_bands / reject_native {"tol": 0.5, "conf": "close"}; SIDE: LONG ONLY; bracket plain60/60 | 180 | M341f6a5e | NEW | RM7 | 0.071 | 0.066 | 442 | 444 | 6190 | 6689 | -14233 | -6557 | 19.7 | 0.49 | 1105 | -1007 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.587 | 0.139 | 0 |
| 35 |  | 47 | YES | tick-imbalance bar 15000 [tib_15000]; ~3 bars/hour; trigger trig_manual_macd / zero_native {"f": 2, "s": 5, "g": 2}; SIDE: LONG ONLY; bracket plain60/60 | 3 | Mb997fd88 | NEW | RM7 | 0.069 | 0.146 | 415 | 587 | 6028 | 4028 | -14143 | -4999 | 10.9 | 0.51 | 1023 | -989 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.581 | 0.258 | 0 |
| 36 |  | 34 | YES | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_tape_delta / cvd_fade {"N": 5, "L": 100, "z": 2.0}; SIDE: LONG ONLY; bracket sym8u | 34 | M50e9574c | NEW | RM7 | 0.063 | 0.223 | 522 | 898 | 8320 | 4031 | -15975 | -6524 | 6.3 | 0.51 | 1465 | -1368 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.499 | 0.001 | 0 |
| 37 |  | 279 |  | unresolved (cell not in ladder_cells.json) |  | LB8 | NEW | RM7 | 0.059 | -0.081 | 725 | -1356 | 12275 | 16763 | -24586 | -5943 | 9.0 | 0.49 | 1834 | -1571 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 38 |  | 17 | YES | tick-count bar 1300 prints [tick_1300]; ~5 bars/hour; trigger trig_levels_opens / reject_native {"tol": 1.0, "conf": "close"}; SIDE: BOTH SIDES; bracket asym20u/10u | 5 | LA6 | NEW | RM7 | 0.058 | 0.383 | 657 | 2053 | 11236 | 5362 | -24998 | -13363 | 6.9 | 0.54 | 1656 | -1707 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 39 |  | 147 |  | session-volume-clock bar 600 bars/session [vsess_600]; ~99 bars/hour; trigger trig_levels_vwap / false_break_native {"M": 1, "k": 0.0}; SIDE: LONG ONLY; bracket sym15u | 99 | M7257e618 | NEW | RM7 | 0.058 | -0.012 | 338 | -78 | 5867 | 6683 | -13648 | -8529 | 8.4 | 0.52 | 1520 | -1537 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.662 | 0.179 | 0 |
| 40 |  | 67 |  | delta-or-range bar B320 [dltor_B320]; ~88 bars/hour; trigger trig_levels_fibr_pd / break_native {"n": 2, "k": 0.25}; SIDE: LONG ONLY; bracket plain60/60 | 88 | M232538e7 | NEW | RM7 | 0.056 | 0.082 | 380 | 558 | 6749 | 6770 | -14721 | -7128 | 12.4 | 0.50 | 1104 | -1056 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.323 | 0.258 | 0 |
| 41 |  | 59 |  | CUSUM-event bar 20 ticks [cusum_20]; ~39 bars/hour; trigger trig_levels_fib60 / false_break_native {"M": 2, "k": 0.5}; SIDE: BOTH SIDES; bracket sym15u | 39 | L77c60218 | NEW | RM7 | 0.056 | 0.101 | 513 | 546 | 9131 | 5436 | -20468 | -11934 | 6.6 | 0.55 | 1475 | -1643 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.403 | 0.030 | 0 |
| 42 |  | 48 | YES | book-message bar B500 [bmsg_B500]; ~88 bars/hour; trigger trig_book_ofi / follow_native {"L": 1800, "z": 1.5}; SIDE: BOTH SIDES; bracket sym15u | 88 | L0f18ba2e | NEW | RM7 | 0.055 | 0.142 | 627 | 728 | 11365 | 5130 | -28966 | -9789 | 7.7 | 0.50 | 1751 | -1573 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.323 | 0.323 | 0 |
| 43 |  | 143 |  | time bar 20 s (tm20 = 20 seconds) [tm20]; ~180 bars/hour; trigger trig_momentum_libosc / fisher {"len": 5}; SIDE: LONG ONLY; bracket plain60/60 | 180 | Mf662a4b4 | NEW | RM7 | 0.054 | -0.010 | 489 | -74 | 9004 | 7814 | -18205 | -5971 | 21.3 | 0.50 | 1078 | -1044 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.516 | 0.387 | 0 |
| 44 |  | 56 |  | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_xmarket_rates / with_ZB {"w": 5, "thr": 1.0}; SIDE: BOTH SIDES; bracket plain60/60 | 34 | L74274eca | NEW | RM7 | 0.052 | 0.105 | 487 | 751 | 9345 | 7150 | -19344 | -9807 | 18.9 | 0.50 | 1075 | -1024 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.343 | 0.002 | 0 |
| 45 |  | 36 | YES | delta bar 250 contracts [dlt_250]; ~2 bars/hour; trigger trig_xmarket_nkd / confirm {"w": 5}; SIDE: BOTH SIDES; bracket sym15u | 2 | Led4240ee | NEW | RM7 | 0.051 | 0.181 | 439 | 603 | 8580 | 3324 | -20797 | -11084 | 5.9 | 0.51 | 1575 | -1486 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.378 | 0.040 | 0 |
| 46 |  | 264 |  | Kagi bar 20 ticks [kagi_20]; ~20 bars/hour; trigger trig_tape_block / b10_follow_sm {"L": 200, "z": 2.0, "sm": 3}; SIDE: LONG ONLY; bracket sym15u | 20 | Mf5a94210 | NEW | RM7 | 0.051 | -0.076 | 256 | -523 | 5037 | 6852 | -16851 | -5444 | 4.7 | 0.52 | 1466 | -1452 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.572 | 0.124 | 1 |
| 47 |  | 66 |  | range bar 20 ticks [rng_20]; ~38 bars/hour; trigger trig_book_pslope / fade_sm {"L": 50, "z": 1.0, "sm": 3}; SIDE: BOTH SIDES; bracket sym8u | 38 | L3e5ef673 | NEW | RM7 | 0.049 | 0.087 | 657 | 827 | 13415 | 9485 | -28840 | -13443 | 12.3 | 0.51 | 1516 | -1455 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.323 | 0.055 | 0 |
| 48 |  | 189 |  | volume bar 4000 contracts [vol_4000]; ~2 bars/hour; trigger trig_levels_vwap_bands / reject_native {"tol": 1.0, "conf": "close"}; SIDE: BOTH SIDES; bracket sym30u | 2 | LA2 | NEW | RM7 | 0.048 | -0.041 | 410 | -442 | 8484 | 10887 | -23025 | -9414 | 7.9 | 0.48 | 1679 | -1455 | 0.57 | 0.52 | 491 | 5149 | -20 | GREEN | -41 | 10912 | +110 | RED | 169 | 7911 | +59 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 49 |  | 88 |  | time bar 3 min [time_m_3]; ~20 bars/hour; trigger trig_manual_macd / sigcross_native {"f": 10, "s": 26, "g": 9}; SIDE: LONG ONLY; bracket plain60/60 | 20 | M582451dd | NEW | RM7 | 0.047 | 0.041 | 265 | 197 | 5668 | 4828 | -10884 | -9722 | 16.0 | 0.50 | 1064 | -1046 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.363 | 0.109 | 0 |
| 50 |  | 197 |  | dollar-imbalance bar 2000 [dib_2000]; ~37 bars/hour; trigger trig_book_ofi / follow_sm {"L": 50, "z": 1.0, "sm": 3}; SIDE: LONG ONLY; bracket sym15u | 37 | M8fa80a89 | NEW | RM7 | 0.043 | -0.047 | 259 | -289 | 5965 | 6141 | -12555 | -8239 | 8.8 | 0.52 | 1607 | -1676 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.592 | 0.194 | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| K7 | -2142 | 461 | 415 | 3710 | -6155 / 11389 | 5877 | 274.3% | 474 |
| P7 | 27768 | 400 | 416 | 21493 | 13697 / 29460 | 6246 | 22.5% | 422 |
| U7 | 18214 | 110 | 416 | 19885 | 6985 / 30542 | 3185 | 17.5% | 119 |
| M7 | -7247 | 518 | 1 | -4602 | -4602 / -4602 | 2645 | 36.5% | 524 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 34 pairs over 17 cells): mean abs difference of its own L6M total $4898 = 294.7% of |total| (median 37.1%, 90th pct 320.6%); trade-count differences: mean abs 5.5 trades (primary mean 245).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_london.csv; all columns: best_books_london_full.csv; status file best_books_london.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
