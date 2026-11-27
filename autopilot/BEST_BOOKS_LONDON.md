# BEST_BOOKS_LONDON - own-merit scorecard, London session (W-BEST; GENERATED AT 2026-11-27 01:37:03Z UTC (a stale page = the cron has stopped; heartbeat /mnt/l2/l2vast/_split/best_books_*.status mtime); first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 1898 distinct cells scored (392 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 4 live-book rows; L6M $/wk > 0: 604; L6M and L3M > 0: 356; labels {'BEST-AVAILABLE-NOT-PROVEN': 1294, 'WEAK-BUT-POSITIVE': 558, 'LEAD': 46}. Job errors: 0. Run 437 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## London TOP 10 on own merit (plain words; old rank = rank before the stale re-runs started, 22:07Z)

| rank | old rank | cell | side | bar | trigger | bracket | L6M $/wk | L6M ulcer | status |
|---|---|---|---|---|---|---|---|---|---|
| 1 | new | L07c1dd1c | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 2075 | 3233 | ok |
| 2 | new | LA5 | BOTH SIDES | volume bar 500 contracts | trig_levels_vwap / break {"n": 3, "k": 0.25} | asym15u/30u | 2138 | 3819 | ok |
| 3 | new | Lc137237a | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 2294 | 4335 | ok |
| 4 | new | Lcc77efb7 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1732 | 3486 | ok |
| 5 | new | L2075382d | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 937 | 3259 | ok |
| 7 | new | M40e194d4 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 791 | 3089 | ok |
| 8 | new | L11af14bc | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1709 | 7085 | ok |
| 9 | new | M1dfc2f39 | LONG ONLY | time bar 2 min | trig_xmarket_nkd / follow {"w": 1, "thr": 1.0} | plain60/60 | 968 | 4021 | ok |
| 10 | new | Meea462cd | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 755 | 3448 | ok |
| 11 | new | L839c4619 | ? | unresolved (cell not in ladder_cells.json) | ? | ? | 1128 | 5456 | ok |

Stale-pending cells (their old results are NOT ranked until re-run; listed in the _full.csv with stale=1 and no rank): 0; of them in the OLD top 50: 0 (none in the old top 10).

## Legend: bar codes (plain name, what the size number means, bars per hour)

Bars per hour = mean over every London session (02:00-08:30, 6.5 h ET) in 2026-05..2026-10 of (bars in the session / session hours), measured from the bar stores /mnt/l2/l2vast/_bars (live tm-rows: stores time_m_N / time_s_N, else 3600/N). Fast bars cost processing: a rate of 500 bars/hour is a bar every 7 seconds.

**Time bars: "time_m_3" = 3 MINUTES; "time_s_30" = 30 SECONDS; "tm180" = 180 SECONDS = 3 minutes (the number after tm is always seconds; tm60 = 1 minute, tm600 = 10 minutes).** Source: code/th_grid/gjob.py row_info (tm = time_m size N seconds) and autopilot/BAR_REGISTRY.md.

| code | plain name | size number means | bars/hour over all sizes in the store (min - max) | used in this top 50: size -> bars/hour |
|---|---|---|---|---|
| ? | ? bar | see BAR_REGISTRY.md | n/a (no store) | ?: nan |
| cusum | CUSUM-event bar | threshold in ticks (scaled by trailing daily range) | 1 - 131 | cusum_28: 20 |
| dltor | delta-or-range bar | composite | 8 - 133 | dltor_B320: 88 |
| mom | momentum bar | ticks of net one-direction move per bar | 1 - 79 | mom_40: 5 |
| mrenko | median Renko bar | ticks per brick | 0 - 56 | mrenko_20: 14 |
| tib | tick-imbalance bar | expected prints per bar (information-driven; scaled by trailing prints) | 1 - 183 | tib_15000: 3 |
| tick | tick-count bar | trade prints per bar (scaled daily by trailing print count) | 1 - 21 | tick_500: 12; tick_8000: 1 |
| time_m | time bar | minutes per bar | 0 - 60 | time_m_2: 30; time_m_5: 12 |
| tm | time bar | seconds per bar (tm180 = 180 s = 3 min) | 3600 / seconds (tm60 = 60/h, tm180 = 20/h, tm600 = 6/h) | tm60: 60; tm420: 9 |
| urenko | UniRenko bar | ticks per brick | 1 - 80 | urenko_14: 42; urenko_20: 21; urenko_40: 5 |
| vol | volume bar | contracts per bar (scaled daily by trailing volume) | 2 - 27 | vol_500: 19 |
| vsess | session-volume-clock bar | bars per session (vsess 30 = a bar every 1/30 of the session volume) | 5 - 99 | vsess_200: 34 |
| anch | anchored equal-volume bar | anchor_B: bucket size | 0 - 1 |  |
| bmsg | book-message bar | one bar per N MBO book messages (B-code = size step, 500 to 64,000 messages) | 5 - 88 |  |
| bmsgq | quote-message bar | B-code size step | 5 - 88 |  |
| cdr | cumulative-delta-range bar | contracts: range of the running cumulative delta inside a bar | 0 - 14 |  |
| dchg | directional-change bar | reversal threshold in ticks (scaled) | 1 - 70 |  |
| dib | dollar-imbalance bar | expected prints per bar (information-driven) | 1 - 199 |  |
| dlt | delta bar | contracts of net aggressor delta per bar | 1 - 61 |  |
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
| pasl | price-action swing-leg bar | ticks | 2 - 13 |  |
| pnf | point-and-figure column bar | ticks per box (3-box reversal) | 0 - 27 |  |
| qmid | mid-change bar | mid-price changes per bar | 5 - 89 |  |
| renko | Renko bar | ticks per brick | 0 - 42 |  |
| rng | range bar | ticks of high-low range per bar (1 tick = 0.25 pt) | 1 - 129 |  |
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
| wrenko | Renko-with-wicks bar | ticks per brick | 0 - 42 |  |

## Prior-year colour summary (REPORT ONLY; the rule and the labels are unchanged)

- New books, top 200 by own-merit rank (200 books): GREEN 0 / AMBER 1 / RED 51 / not landed 148.
  Prior years positive in absolute $/wk, books with all 3 years landed (51): 0 of 3: 0, 1 of 3: 2, 2 of 3: 12, 3 of 3: 37. Books with 1-2 years landed (1): 2 of 2 positive: 1.
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

## Where the live books rank (same table, same scoring; 1902 rows in this session)

| rank | OLD rank (before re-runs) | rank L3M | top-50 on both L6M and L3M | what it is (bar, trigger, settings, side, bracket) | bars per hour (L6M mean, this session) | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6 |  | 90 |  | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 414 |  | 215 |  | live book M7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_M7 | LIVE | JL3 | 0.017 | 0.146 | 144 | 1130 | 8679 | 7722 | -17285 | -11717 | 19.8 | 0.40 | 1172 | -762 | 0.43 | 0.40 | 95 | 5555 | +34 | RED | -376 | 26105 | +360 | RED | -356 | 16712 | +347 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 747 |  | 463 |  | live book K7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 3 min (tm180 = 180 seconds) [tm180]; ~20 bars/hour | 20 | LIVE_K7 | LIVE | JL3 | -0.008 | 0.030 | -40 | 164 | 5193 | 5366 | -12034 | -6678 | 17.6 | 0.41 | 1154 | -820 | 0.43 | 0.54 | 210 | 8189 |  | n/a | 150 | 9556 |  | n/a | 569 | 6933 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |
| 991 |  | 908 |  | live book U7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 10 min (tm600 = 600 seconds) [tm600]; ~6 bars/hour | 6 | LIVE_U7 | LIVE | JL3 | -0.019 | -0.045 | -76 | -204 | 3917 | 4543 | -7975 | -3125 | 4.2 | 0.45 | 1150 | -992 | 0.43 | 0.45 | 29 | 4390 |  | n/a | -65 | 10025 |  | n/a | -67 | 4691 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

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
| 1 |  | 2 | YES | unresolved (cell not in ladder_cells.json) |  | L07c1dd1c | NEW | RM7 | 0.642 | 1.411 | 2075 | 2877 | 3233 | 2039 | -8839 | -7209 | 6.8 | 0.59 | 1602 | -1581 | 0.86 | 0.61 | 451 | 3528 | +80 | RED | 321 | 4300 | +88 | RED | 284 | 9565 | +95 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 |  | 29 | YES | volume bar 500 contracts [vol_500]; ~19 bars/hour; trigger trig_levels_vwap / break {"n": 3, "k": 0.25}; SIDE: BOTH SIDES; bracket asym15u/30u | 19 | LA5 | NEW | RM7 | 0.560 | 0.606 | 2138 | 2262 | 3819 | 3731 | -9472 | -4964 | 7.6 | 0.56 | 1693 | -1536 | 0.71 | 0.55 | 311 | 2588 | +85 | RED | -71 | 13068 | +103 | RED | 384 | 11549 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 3 |  | 111 |  | unresolved (cell not in ladder_cells.json) |  | Lc137237a | NEW | RM7 | 0.529 | 0.269 | 2294 | 1393 | 4335 | 5172 | -12221 | -8060 | 21.5 | 0.53 | 1103 | -1010 | 0.79 | 0.60 | 437 | 4123 | +81 | RED | 436 | 7140 | +88 | RED | 537 | 9637 | +89 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 4 |  | 152 |  | unresolved (cell not in ladder_cells.json) |  | Lcc77efb7 | NEW | RM7 | 0.497 | 0.209 | 1732 | 661 | 3486 | 3158 | -8995 | -5354 | 7.4 | 0.57 | 1631 | -1634 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 5 |  | 131 |  | unresolved (cell not in ladder_cells.json) |  | L2075382d | NEW | RM7 | 0.287 | 0.247 | 937 | 851 | 3259 | 3450 | -9043 | -4829 | 7.5 | 0.54 | 1069 | -976 | 0.50 | 0.60 | 253 | 3079 | +73 | RED | 288 | 2813 | +69 | RED | 119 | 15394 | +97 | RED | RED | WEAK-BUT-POSITIVE |  |  | 2 |
| 6 |  | 90 |  | live book P7 as run in JL3 (own trades, 1-lot normalised); live bar row per LIVE_BOOKS_REFERENCE.md time bar 1 min (tm60 = 60 seconds) [tm60]; ~60 bars/hour | 60 | LIVE_P7 | LIVE | JL3 | 0.278 | 0.321 | 822 | 933 | 2957 | 2902 | -8357 | -4856 | 15.3 | 0.46 | 965 | -714 | 0.50 | 0.45 | 76 | 3808 | +93 | RED | -54 | 6226 | +107 | RED | -1075 | 38795 | +231 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 7 |  | 436 |  | unresolved (cell not in ladder_cells.json) |  | M40e194d4 | NEW | RM7 | 0.256 | 0.039 | 791 | 130 | 3089 | 3350 | -7885 | -6413 | 8.2 | 0.54 | 1019 | -974 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 8 |  | 174 |  | unresolved (cell not in ladder_cells.json) |  | L11af14bc | NEW | RM7 | 0.241 | 0.179 | 1709 | 1249 | 7085 | 6986 | -15950 | -7618 | 9.9 | 0.55 | 1649 | -1661 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 9 |  | 188 |  | time bar 2 min [time_m_2]; ~30 bars/hour; trigger trig_xmarket_nkd / follow {"w": 1, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 30 | M1dfc2f39 | NEW | RM7 | 0.241 | 0.170 | 968 | 795 | 4021 | 4686 | -10910 | -3609 | 10.5 | 0.54 | 1088 | -1076 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.423 | 0.008 | 0 |
| 10 |  | 20 | YES | unresolved (cell not in ladder_cells.json) |  | Meea462cd | NEW | RM7 | 0.219 | 0.700 | 755 | 1064 | 3448 | 1520 | -7702 | -3658 | 9.2 | 0.53 | 1014 | -983 | 0.64 | 0.66 | 147 | 5016 | +87 | RED | 515 | 3998 | +41 | RED | 191 | 8888 | +90 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 11 |  | 139 |  | unresolved (cell not in ladder_cells.json) |  | L839c4619 | NEW | RM7 | 0.207 | 0.236 | 1128 | 1246 | 5456 | 5286 | -13783 | -9703 | 6.6 | 0.58 | 1563 | -1760 | 0.57 | 0.59 | 205 | 3187 | +82 | RED | 339 | 5788 | +72 | RED | 312 | 7230 | +79 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 12 |  | 585 |  | tick-count bar 500 prints [tick_500]; ~12 bars/hour; trigger trig_xmarket_rates / with_ZB {"w": 5, "thr": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 12 | M823f025d | NEW | RM7 | 0.207 | 0.000 | 1037 | 0 | 5022 | 4171 | -11738 | -4438 | 12.1 | 0.52 | 1041 | -964 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.145 | 0.003 | 0 |
| 13 |  | 276 |  | tick-count bar 8000 prints [tick_8000]; ~1 bars/hour; trigger trig_book_imb / delta_fade {"lv": 5, "thr": 0.2}; SIDE: BOTH SIDES; bracket plain60/60 | 1 | L1dcd5850 | NEW | RM7 | 0.201 | 0.101 | 542 | 272 | 2700 | 2694 | -7657 | -4838 | 7.6 | 0.51 | 1052 | -939 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.353 | 0.025 | 0 |
| 14 |  | 1186 |  | session-volume-clock bar 200 bars/session [vsess_200]; ~34 bars/hour; trigger trig_levels_stack / reject_native {"k": 2, "cw": 1.0}; SIDE: BOTH SIDES; bracket asym20u/10u | 34 | L7f4c2c7f | NEW | RM7 | 0.189 | -0.072 | 1500 | -629 | 7957 | 8680 | -21449 | -9924 | 9.5 | 0.52 | 1722 | -1565 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 1.000 | 1.000 | 0 |
| 15 |  | 301 |  | unresolved (cell not in ladder_cells.json) |  | M9ed09420 | NEW | RM7 | 0.174 | 0.093 | 861 | 584 | 4952 | 6275 | -14936 | -5169 | 8.9 | 0.55 | 1436 | -1521 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 16 |  | 531 |  | unresolved (cell not in ladder_cells.json) |  | L8a16da98 | NEW | RM7 | 0.173 | 0.013 | 1164 | 81 | 6711 | 6323 | -19473 | -8443 | 18.1 | 0.51 | 1091 | -1020 | 0.50 | 0.58 | 269 | 2776 | +77 | RED | 123 | 8205 | +91 | RED | 151 | 5593 | +87 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 17 |  | 202 |  | unresolved (cell not in ladder_cells.json) |  | LB5 | NEW | RM7 | 0.167 | 0.157 | 1243 | 660 | 7443 | 4202 | -19947 | -10749 | 8.9 | 0.50 | 1798 | -1504 | 0.79 | 0.61 | 575 | 2787 | +54 | RED | 715 | 4719 | +42 | RED | 174 | 9970 | +90 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 18 |  | 660 |  | UniRenko bar 40 ticks [urenko_40]; ~5 bars/hour; trigger trig_book_cancel / net_follow {"L": 50, "z": 1.0}; SIDE: LONG ONLY; bracket plain60/60 | 5 | M5e60d82e | NEW | RM7 | 0.166 | -0.011 | 548 | -33 | 3310 | 3106 | -8227 | -5723 | 9.5 | 0.52 | 1063 | -1040 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.405 | 0.010 | 0 |
| 19 |  | 283 |  | CUSUM-event bar 28 ticks [cusum_28]; ~20 bars/hour; trigger trig_trend_macd / hist_turn_native {"len": 26, "width": 0.03}; SIDE: BOTH SIDES; bracket sym15u | 20 | L1de6d125 | NEW | RM7 | 0.164 | 0.100 | 1137 | 409 | 6934 | 4100 | -18182 | -8329 | 8.9 | 0.53 | 1630 | -1596 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.403 | 0.027 | 0 |
| 20 |  | 398 |  | unresolved (cell not in ladder_cells.json) |  | M085c7522 | NEW | RM7 | 0.163 | 0.051 | 477 | 160 | 2915 | 3120 | -7467 | -4799 | 4.8 | 0.54 | 1069 | -1038 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 1 |
| 21 |  | 79 |  | unresolved (cell not in ladder_cells.json) |  | Ldae32385 | NEW | RM7 | 0.162 | 0.354 | 588 | 910 | 3628 | 2575 | -10048 | -4999 | 4.1 | 0.56 | 1302 | -1307 | 0.57 | 0.54 | 403 | 1601 | +31 | RED | 214 | 4496 | +71 | RED | 250 | 18737 | +92 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 22 |  | 542 |  | momentum bar 40 ticks [mom_40]; ~5 bars/hour; trigger trig_book_imb / delta_fade {"lv": 10, "thr": 0.4}; SIDE: BOTH SIDES; bracket sym15u | 5 | Lf53aa68f | NEW | RM7 | 0.162 | 0.010 | 741 | 62 | 4585 | 6264 | -11819 | -4359 | 5.8 | 0.51 | 1569 | -1392 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.473 | 0.040 | 0 |
| 23 |  | 282 |  | unresolved (cell not in ladder_cells.json) |  | Mf82ae69e | NEW | RM7 | 0.161 | 0.100 | 491 | 288 | 3041 | 2888 | -6595 | -3024 | 6.8 | 0.54 | 1005 | -1045 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 1 |
| 24 |  | 657 |  | unresolved (cell not in ladder_cells.json) |  | LB7 | NEW | RM7 | 0.159 | -0.010 | 638 | -55 | 4019 | 5258 | -11993 | -5989 | 7.7 | 0.52 | 1064 | -1000 | 0.50 | 0.63 | 547 | 3121 | +14 | GREEN |  |  |  | n/a | 545 | 5140 | +33 | RED | RED (2 of 3 yrs) | WEAK-BUT-POSITIVE |  |  | 0 |
| 25 |  | 310 |  | unresolved (cell not in ladder_cells.json) |  | Mdc845568 | NEW | RM7 | 0.158 | 0.088 | 464 | 278 | 2947 | 3149 | -6747 | -4784 | 6.2 | 0.50 | 1110 | -960 | 0.57 | 0.53 | 10 | 5594 | +99 | RED | -247 | 8113 | +153 | RED | -105 | 10315 | +123 | RED | RED | WEAK-BUT-POSITIVE |  |  | 1 |
| 26 |  | 457 |  | unresolved (cell not in ladder_cells.json) |  | M021c36a3 | NEW | RM7 | 0.155 | 0.034 | 884 | 245 | 5706 | 7292 | -13162 | -8789 | 7.2 | 0.51 | 1690 | -1530 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 27 |  | 74 |  | unresolved (cell not in ladder_cells.json) |  | L49bac51a | NEW | RM7 | 0.151 | 0.360 | 518 | 1079 | 3425 | 2992 | -8647 | -3658 | 6.5 | 0.52 | 1087 | -1001 | 0.57 | 0.59 | 326 | 2507 | +37 | RED | 364 | 2738 | +30 | AMBER | 395 | 2417 | +24 | AMBER | RED | WEAK-BUT-POSITIVE |  |  | 1 |
| 28 |  | 256 |  | time bar 7 min (tm420 = 420 seconds) [tm420]; ~9 bars/hour; trigger trig_momentum_stoch / zone_break {"len": 5, "lvl": 70}; SIDE: BOTH SIDES; bracket plain60/60 | 9 | Lcc09204f | NEW | RM7 | 0.149 | 0.114 | 893 | 611 | 6011 | 5373 | -15820 | -9743 | 17.2 | 0.52 | 1088 | -1055 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.234 | 0.001 | 1 |
| 29 |  | 484 |  | CUSUM-event bar 28 ticks [cusum_28]; ~20 bars/hour; trigger trig_book_micro / fade_native {"L": 3600, "z": 2.0}; SIDE: BOTH SIDES; bracket sym15u | 20 | L242d12c9 | NEW | RM7 | 0.146 | 0.024 | 882 | 175 | 6034 | 7303 | -17565 | -10274 | 7.2 | 0.51 | 1728 | -1535 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.283 | 0.016 | 0 |
| 30 |  | 161 |  | unresolved (cell not in ladder_cells.json) |  | Lf684ced8 | NEW | RM7 | 0.142 | 0.195 | 666 | 981 | 4676 | 5031 | -11231 | -6618 | 13.5 | 0.53 | 1040 | -1060 | 0.50 | 0.65 | 262 | 4215 | +61 | RED | 793 | 4146 | -19 | GREEN | -21 | 8481 | +103 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 31 |  | 198 |  | delta-or-range bar B320 [dltor_B320]; ~88 bars/hour; trigger trig_levels_ob5 / false_break {"M": 2, "k": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 88 | Ld8d62c36 | NEW | RM7 | 0.139 | 0.161 | 737 | 691 | 5305 | 4283 | -15346 | -5299 | 7.3 | 0.52 | 1123 | -999 | 0.50 | 0.50 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.245 | 0.037 | 0 |
| 32 |  | 48 | YES | unresolved (cell not in ladder_cells.json) |  | L9b6bee82 | NEW | RM7 | 0.139 | 0.460 | 1091 | 1177 | 7854 | 2560 | -17825 | -9872 | 18.0 | 0.52 | 1088 | -1038 | 0.43 | 0.59 | 309 | 3886 | +72 | RED | 214 | 8087 | +81 | RED | 1028 | 4435 | +6 | GREEN | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 33 |  | 107 |  | unresolved (cell not in ladder_cells.json) |  | Me31e426d | NEW | RM7 | 0.139 | 0.275 | 582 | 774 | 4200 | 2815 | -10217 | -5233 | 14.4 | 0.51 | 890 | -856 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 34 |  | 38 | YES | time bar 5 min [time_m_5]; ~12 bars/hour; trigger trig_levels_vwap / reject_native {"tol": 1.0, "conf": "body"}; SIDE: BOTH SIDES; bracket sym15u | 12 | LA4 | NEW | RM7 | 0.137 | 0.545 | 1187 | 1920 | 8659 | 3525 | -23834 | -10953 | 8.4 | 0.54 | 1683 | -1691 | 0.57 | 0.52 | 388 | 4949 | +67 | RED | 161 | 6285 | +86 | RED | 557 | 7407 | +53 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 35 |  | 110 |  | unresolved (cell not in ladder_cells.json) |  | M0cbb95be | NEW | RM7 | 0.136 | 0.271 | 622 | 890 | 4585 | 3285 | -10141 | -5349 | 4.7 | 0.53 | 1415 | -1330 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 36 |  | 46 | YES | unresolved (cell not in ladder_cells.json) |  | Mf8d54bf1 | NEW | RM7 | 0.136 | 0.495 | 490 | 710 | 3615 | 1435 | -7446 | -3589 | 4.7 | 0.52 | 1092 | -985 | 0.64 | 0.62 | 203 | 2275 | +59 | RED | 156 | 4741 | +76 | RED | 20 | 7560 | +98 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 37 |  | 87 |  | unresolved (cell not in ladder_cells.json) |  | L2c53d3a2 | NEW | RM7 | 0.134 | 0.331 | 1134 | 2047 | 8486 | 6179 | -20186 | -11775 | 21.4 | 0.52 | 1077 | -1063 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 4 |
| 38 |  | 206 |  | tick-imbalance bar 15000 [tib_15000]; ~3 bars/hour; trigger trig_manual_macd / sigcross_native {"f": 5, "s": 13, "g": 4}; SIDE: LONG ONLY; bracket plain60/60 | 3 | Md12eae61 | NEW | RM7 | 0.133 | 0.153 | 610 | 604 | 4591 | 3940 | -10661 | -4163 | 12.3 | 0.50 | 1075 | -982 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.622 | 0.169 | 0 |
| 39 |  | 9 | YES | unresolved (cell not in ladder_cells.json) |  | M919e3a77 | NEW | RM7 | 0.133 | 0.981 | 531 | 1063 | 4000 | 1084 | -9752 | -2414 | 3.9 | 0.55 | 1063 | -1015 | 0.71 | 0.58 | 145 | 1955 | +73 | RED | 195 | 1635 | +63 | RED | 142 | 4729 | +77 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 40 |  | 11 | YES | unresolved (cell not in ladder_cells.json) |  | Lcf783247 | NEW | RM7 | 0.133 | 0.947 | 1423 | 2490 | 10731 | 2629 | -26278 | -16038 | 9.8 | 0.53 | 1716 | -1607 | 0.57 | 0.59 | 679 | 3904 | +52 | RED | 485 | 4202 | +66 | RED | 175 | 8934 | +88 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 41 |  | 381 |  | unresolved (cell not in ladder_cells.json) |  | M5de424cc | NEW | RM7 | 0.132 | 0.055 | 633 | 330 | 4790 | 5945 | -14074 | -6738 | 12.9 | 0.50 | 1090 | -1011 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 0 |
| 42 |  | 44 | YES | UniRenko bar 14 ticks [urenko_14]; ~42 bars/hour; trigger trig_levels_sdx5 / retest {"d": "E", "M": 6, "tol": 0.5}; SIDE: BOTH SIDES; bracket plain60/60 | 42 | L431323b6 | NEW | RM7 | 0.132 | 0.514 | 535 | 1016 | 4050 | 1975 | -8507 | -3124 | 5.8 | 0.53 | 1025 | -958 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.348 | 0.025 | 0 |
| 43 |  | 453 |  | unresolved (cell not in ladder_cells.json) |  | Mf2b6c3b6 | NEW | RM7 | 0.131 | 0.034 | 655 | 210 | 4988 | 6159 | -13152 | -5478 | 7.6 | 0.54 | 1564 | -1632 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 1 |
| 44 |  | 37 | YES | unresolved (cell not in ladder_cells.json) |  | L90fa58e0 | NEW | RM7 | 0.129 | 0.556 | 1370 | 2395 | 10618 | 4307 | -21862 | -8754 | 7.6 | 0.55 | 1623 | -1567 | 0.64 | 0.51 | 239 | 2831 | +83 | RED | 255 | 4668 | +81 | RED | -37 | 11209 | +103 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 45 |  | 281 |  | unresolved (cell not in ladder_cells.json) |  | M11807a21 | NEW | RM7 | 0.128 | 0.100 | 505 | 345 | 3936 | 3453 | -9671 | -7383 | 9.2 | 0.51 | 1073 | -1016 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 46 |  | 157 |  | UniRenko bar 20 ticks [urenko_20]; ~21 bars/hour; trigger trig_levels_fibr_pd / break_native {"n": 3, "k": 0.5}; SIDE: LONG ONLY; bracket plain60/60 | 21 | M9123cdc8 | NEW | RM7 | 0.126 | 0.202 | 633 | 811 | 5029 | 4017 | -9620 | -5788 | 9.1 | 0.54 | 1033 | -1061 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.387 | 0.452 | 0 |
| 47 |  | 350 |  | median Renko bar 20 ticks [mrenko_20]; ~14 bars/hour; trigger trig_levels_trendline / break {"n": 2, "k": 0.0}; SIDE: LONG ONLY; bracket plain60/60 | 14 | M45234700 | NEW | RM7 | 0.125 | 0.067 | 623 | 372 | 4984 | 5544 | -14165 | -5178 | 10.5 | 0.52 | 1076 | -1034 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.613 | 0.323 | 0 |
| 48 |  | 362 |  | unresolved (cell not in ladder_cells.json) |  | L73b40f7a | NEW | RM7 | 0.124 | 0.064 | 1043 | 691 | 8392 | 10876 | -22001 | -9473 | 8.4 | 0.51 | 1682 | -1477 | 0.50 | 0.56 | 94 | 6383 | +91 | RED | 427 | 4885 | +59 | RED | -22 | 10534 | +102 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 49 |  | 136 |  | unresolved (cell not in ladder_cells.json) |  | LB4 | NEW | RM7 | 0.124 | 0.237 | 913 | 1160 | 7374 | 4895 | -15711 | -8339 | 7.5 | 0.51 | 1653 | -1457 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 50 |  | 226 |  | unresolved (cell not in ladder_cells.json) |  | Lff8c6f0f | NEW | RM7 | 0.123 | 0.137 | 904 | 977 | 7382 | 7108 | -17611 | -8893 | 11.4 | 0.53 | 1471 | -1501 | 0.50 | 0.61 | 294 | 4610 | +68 | RED | 903 | 4498 | +0 | GREEN | 403 | 5908 | +55 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| K7 | -2142 | 461 | 2271 | 3747 | -6415 / 14472 | 6001 | 280.1% | 474 |
| P7 | 27768 | 400 | 2272 | 21319 | 12117 / 31768 | 6237 | 22.5% | 422 |
| U7 | 18214 | 110 | 2272 | 20518 | 6985 / 30542 | 3282 | 18.0% | 119 |
| M7 | -7247 | 518 | 1 | -4602 | -4602 / -4602 | 2645 | 36.5% | 524 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 34 pairs over 17 cells): mean abs difference of its own L6M total $4898 = 294.7% of |total| (median 37.1%, 90th pct 320.6%); trade-count differences: mean abs 5.5 trades (primary mean 245).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_london.csv; all columns: best_books_london_full.csv; status file best_books_london.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
