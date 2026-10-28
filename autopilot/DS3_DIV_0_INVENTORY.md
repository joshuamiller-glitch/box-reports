# DS3_DIV_0_INVENTORY - what exists per market, and what a proper intraday program would need (D3DV1, 2026-10-28)

Research only. No purchase, no download, no live/execution/chart change. The Databento key was used only inside a `bash -ic` subprocess for `metadata.get_cost` (a free quote endpoint; script l2vast/ds3/code/div1/cost_estimates.py, raw quotes l2vast/ds3/out/div1/cost_estimates.json, 156 quotes, 0 errors); it is not in any file or output. Spend so far (autopilot/SPEND.json) is $7,188.62 of the $8,000 cap: headroom $811.38.

## 0. Two corrections to earlier inventories (read first)
1. **Tick-level trades ARE on disk for ES, RTY, CL, GC, ZN (not only NQ).** INSTRUMENT_INVENTORY.md (D3INS, 10-26) and DS3_CRT_XINSTR.md (D3CX) say "1-min OHLCV only, no tick". The directory data/databento/<SYM>/trades/GLBX-20261013-*/ holds Databento `trades` schema, `ES.FUT`-style PARENT symbology (all contracts of the product, filter to front by instrument_id), monthly files 2023-02-01 .. 2026-10-12 (CL/GC/ZN: 45 files, 4.2 / 1.7 / 1.4 GB zst; ES 47 files 6.2 GB and RTY 47 files 1.6 GB, both to 2026-10-23 where the last file is L2-derived per DERIVED_FROM_L2.txt; NQ 47 files 5.9 GB). They have been there since 10-13 (condition.json: every day 'available'). **No trades for YM or 6E** and none before 2023-02-01 for any market. So D3CX's 'mapped, no direct replay' label was too pessimistic for ES/RTY/CL/GC/ZN: print-level stop/limit fill checks are possible there without any purchase (a 1-min-bar program still cannot see them; a trades-based fill loader has to be written, ~1 day).
2. **mbp-10 L2 is on disk for ES and RTY** (INGEST_LOG.csv: ES 2023-08..2026-10 52 files 243 GB raw, RTY 2023-08..2026-10 39 files 85 GB, NQ 2023-02..2026-10 85 files 643 GB). A superset of mbp-1, so ES/RTY need no mbp-1 purchase. CL, GC, ZN, 6E, YM have no quote data.

## 1. Inventory
Common basis for every row: Databento CME Globex `.v.0` (volume-roll continuous front) 1-min OHLCV, `instrument_id` carried (cache /mnt/l2/l2vast/ds3/cache_te2/<SYM>.npz = raw, <SYM>_adj.npz = back-adjusted). **Roll method:** the bar where instrument_id changes is flagged `roll`; its open-minus-previous-close gap is removed additively from all earlier prices (back-adjust to the latest contract). Volume-roll, so roll dates differ from NT8 expiry-roll at the roll dates only. Rolls column = roll bars since 2022-06 (CL monthly 52). 1-min bars exist only for minutes with trades. Session coverage measured on weekdays since 2022-06 (ET minute-of-day with a bar on >=50% of days): full 23 h for all but RB/HO. Fee line = FEES.md; WEAK = proxy or absent (verdict ceiling CANDIDATE under the program rule).

| mkt | symbol | resolution | first / last 1-min bar (UTC date) | session coverage | rolls since 2022-06 | fee line |
|---|---|---|---|---|---|---|
| NQ | NQ.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,551,555); 1-s bars to 2026-10-23; trades 2023-02..2026-10-23; mbp-10 L2 2023-02..2026-10 | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET, 1-h halt) | 18 | 4.84 RT, PROXY of ES (FEES.md STANDARD) |
| ES | ES.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,551,291); trades (parent) 2023-02-01..2026-10-23; mbp-10 L2 2023-08..2026-10 | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 18 | 4.84 RT, NT-published (FEES.md STANDARD) |
| RTY | RTY.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,503,992); trades (parent) 2023-02-01..2026-10-23; mbp-10 L2 2023-08..2026-10 | 2017-07-09 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 18 | WEAK: no standard-size line; FEES.md has only M2K 1.78 (micro, proxy of MES); 4.84 ES proxy used by D3CX |
| YM | YM.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,530,027) | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 18 | WEAK: no standard-size line; only MYM 1.78 micro proxy; 4.84 ES proxy used |
| CL | CL.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,530,522); trades (parent) 2023-02-01..2026-10-12 | 2013-01-01 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 52 | WEAK: no CL line; only MCL 2.08 (weak); 4.84 ES proxy used |
| ZN | ZN.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,453,997); trades (parent) 2023-02-01..2026-10-12 | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 17 | WEAK: absent from FEES.md; 4.84 ES proxy (probably conservative, CME rates fees lower) |
| GC | GC.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,533,246); trades (parent) 2023-02-01..2026-10-12 | 2013-01-01 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 21 | WEAK: absent; 4.84 ES proxy (COMEX metals fees are likely at/above this) |
| 6E | 6E.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,524,830) | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 18 | 5.30 RT (FEES.md 6E ADDENDUM: NT commission/clearing/routing published; exchange+NFA third-party = WEAK) |
| ZB | ZB.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,336,346) | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 17 | WEAK: absent; 4.84 proxy |
| ZF | ZF.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,401,111) | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 17 | WEAK: absent; 4.84 proxy |
| RB | RB.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,098,500) | 2013-01-01 / 2026-10-16 | thin overnight (bars only in 64% of ET minutes; RTH 02:00-17:00 dense) | 97 | WEAK: absent; 4.84 proxy (no MCL-like sibling line) |
| HO | HO.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,119,333) | 2013-01-01 / 2026-10-16 | thin overnight (65% of ET minutes) | 71 | WEAK: absent; 4.84 proxy |
| SI | SI.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,473,842) | 2013-01-01 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 22 | WEAK: absent; 4.84 proxy |
| 6B | 6B.v.0 (Databento GLBX.MDP3) | 1-min OHLCV (bars since 2022-06: 1,427,760) | 2013-01-02 / 2026-10-16 | full 23 h (18:00-17:00 ET) | 18 | WEAK: absent (not in the 6E addendum); 4.84 proxy; 6E 5.30 is the nearest line |

Coverage detail: ES/NQ/RTY/YM/CL/ZN/GC/6E/ZB/ZF/6B/SI bars in 96% of ET minutes (every minute except the 17:00-18:00 ET maintenance hour; ZB/ZF/ZN/6B have occasional empty minutes overnight, median bars/day 1,203-1,379 of 1,380). RB/HO: dense 02:00-17:00 ET, sparse in the evening (minutes with no trade are absent; any 15-min map for them needs the empty-window rule). Nothing on disk before 2013 and no pre-2022-06 data is used by this program. Last 1-min bar 2026-10-16 (ES/RTY/NQ extended to 10-23 from L2, not in the cache used here). Date convention for scoring/maps: see DS3_DIV_1_MAPS.md (UNTOUCHED = after 2026-02-06 is never read here).

## 2. What a proper intraday program on the other markets would need
- **Bars (have).** Enough for time-of-day maps, window-drift rules, bracket rules with the D3CX tick-conservative fill model (market +1 tick, stop +2 ticks, limit needs 1-tick trade-through). Limits: no intrabar order of high/low, so stop-first is assumed; a 1-min bar cannot tell whether a stop was gapped through by a news print.
- **Trades (print level).** Needed to check (i) stop fill price at the 08:30/10:30/14:30 events, where the stop-first assumption and the +2 tick stop slippage are weakest, (ii) limit fill realism (trade-through vs touch), (iii) the opening-print and settlement-window profiles for the events in Section 1. Have it for ES/RTY/CL/GC/ZN from 2023-02. Missing: YM, 6E, and 2022-06..2023-01 for all seven.
- **mbp-1 (top of book).** Gives the spread and displayed depth at the moment a stop triggers, i.e. the stop-fill slippage distribution by clock time, which trades alone cannot give. Worth it where the book is thin or events gap: CL, GC, 6E, YM, ZN (ES/RTY already have mbp-10). 12 months is enough to calibrate a slippage-by-clock-time table; the full span is not needed for that and costs 3-4x more.
- **Not needed:** full-span mbp-1 (ES $1,097, RTY $383, YM $383, ZN $332, CL $265, GC $221, 6E $236: sum $2,917, well over the cap), mbp-10/MBO for the other markets (no program on them would use queue position), and the micro contracts (same price series).

## 3. Purchase list (NOTHING IS BOUGHT; user must OK each line)
Quotes are get_cost at today's price, GLBX.MDP3. 'ES.FUT-style parent' = same format as the existing files; '.v.0' = front month only (cheaper for CL/RB/HO where back months are heavy). Headroom $811.38.

| prio | id | mkt | schema | symbology | period | USD | why |
|---|---|---|---|---|---|---|---|
| 1 | P1 | YM | trades | ES.FUT-style parent | B_2023-02_to_2026-10 | 98.62 | only index future with no tick data; completes ES<->YM sibling replication and the YM time-of-day events at print level (parent format = same as the on-disk ES/RTY/CL/GC/ZN files) |
| 1 | P2 | 6E | trades | ES.FUT-style parent | B_2023-02_to_2026-10 | 60.01 | 6E has bars only; London-close/08:30 stop-run behaviour needs prints; parent format as on disk |
| 2 | P3 | CL | mbp-1 | continuous .v.0 | D_last12m | 57.31 | top-of-book for stop-fill realism, last 12 months (2025-10..2026-10): thinnest overnight book, 10:30 inventory spike: stop-fill slippage is the main unknown |
| 2 | P3 | 6E | mbp-1 | continuous .v.0 | D_last12m | 47.33 | top-of-book for stop-fill realism, last 12 months (2025-10..2026-10): tight but event-gappy (08:30, London close) |
| 2 | P3 | GC | mbp-1 | continuous .v.0 | D_last12m | 70.26 | top-of-book for stop-fill realism, last 12 months (2025-10..2026-10): London fix / settle gaps |
| 2 | P3 | YM | mbp-1 | continuous .v.0 | D_last12m | 87.50 | top-of-book for stop-fill realism, last 12 months (2025-10..2026-10): 1-pt tick, wide quote spread in the 1-min median volume of 30 |
| 2 | P3 | ZN | mbp-1 | continuous .v.0 | D_last12m | 88.59 | top-of-book for stop-fill realism, last 12 months (2025-10..2026-10): 1/64 tick: slippage is mostly quote depth at 08:30 releases |
| 3 | P4 | ES | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 120.53 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | CL | trades | continuous .v.0 | A_2022-06_to_2023-01 | 26.77 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | ZN | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 21.99 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | GC | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 18.44 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | 6E | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 15.94 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | RTY | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 23.16 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |
| 3 | P4 | YM | trades | ES.FUT-style parent | A_2022-06_to_2023-01 | 25.90 | 2022-06..2023-01 (the 2022 rate-hike year; every on-disk trades file starts 2023-02-01). CL via .v.0 because parent costs 2.3x for back months the loader discards |

Priority subtotals: P1 (YM + 6E trades 2023-02..2026-10) $158.63; P3-stop-fill (mbp-1 last 12 months, CL/6E/GC/YM/ZN) $350.99; P4 (2022-06..2023-01 trades, all seven) $252.73. **All lines $762.35 of $811.38 headroom ($49.03 left).** Recommended order: P1 first ($158.63, lets the sibling and print-level checks run on all seven), then the mbp-1 12-month block only for the markets where a rule survives the bar-level scoring (buy per market, CL first at $57.31), P4 only if a surviving rule needs the 2022 regime (the program's WF years are 2024-2026; 2022 is outside it). Do not buy P3/P4 speculatively: the program scores on what exists now.

Full quote matrix (USD; .v.0 = continuous front, FUT = parent):

| mkt | mbp-1 v0 2022-06..2026-10 | mbp-1 v0 last 12m | trades v0 2023-02..2026-10 | trades FUT 2023-02..2026-10 | trades v0 2022-06..2023-01 | trades FUT 2022-06..2023-01 |
|---|---|---|---|---|---|---|
| ES | 1,096.96 | 305.41 | 522.89 | 552.35 | 111.62 | 120.53 |
| CL | 264.50 | 57.31 | 123.85 | 334.57 | 26.77 | 61.00 |
| ZN | 331.92 | 88.59 | 118.15 | 125.84 | 21.03 | 21.99 |
| GC | 221.17 | 70.26 | 115.80 | 135.29 | 16.04 | 18.44 |
| 6E | 236.46 | 47.33 | 55.78 | 60.01 | 15.09 | 15.94 |
| RTY | 382.93 | 106.51 | 115.26 | 121.42 | 22.08 | 23.16 |
| YM | 383.06 | 87.50 | 94.52 | 98.62 | 24.75 | 25.90 |

Siblings (priced for completeness, not recommended now): 

| mkt | mbp-1 v0 full | mbp-1 v0 12m | trades v0 2023-02..2026-10 | trades FUT 2023-02..2026-10 | trades v0 2022-06..2023-01 | trades FUT 2022-06..2023-01 |
|---|---|---|---|---|---|---|
| ZB | 185.33 | 41.24 | 55.26 | 59.00 | 11.40 | 12.00 |
| ZF | 280.72 | 71.27 | 94.52 | 100.86 | 17.16 | 17.98 |
| RB | 97.45 | 39.16 | 23.53 | 97.64 | 3.26 | 13.62 |
| HO | 95.50 | 40.32 | 23.23 | 93.96 | 3.27 | 14.89 |
| SI | 124.73 | 43.83 | 39.98 | 48.27 | 5.73 | 6.56 |
| 6B | 118.44 | 26.72 | 24.28 | 26.18 | 7.28 | 7.67 |

Trades v0 for all six siblings over the full span would be $308.89.

## 4. Fee-line gaps to close (free, user side)
FEES.md grades only ES and (as a micro proxy) the 1.78 lines as published. RTY, YM, CL, GC, ZN, ZB, ZF, RB, HO, SI, 6B have NO standard-size line: they run on the 4.84 ES proxy (WEAK). 6E is 5.30 with a third-party exchange fee. One NT statement line per product (a 1-lot round trip) settles it; until then every verdict on these markets is capped at CANDIDATE and the 2x-cost column is always shown.

## 5. Scoring basis for the rest of the program
Everything is scored on what exists now: 1-min bars for all seven plus NQ reference, with trades available as a later fill check for ES/RTY/CL/GC/ZN. Dates: see MAPS file (no read after 2026-02-06 in section 1).
