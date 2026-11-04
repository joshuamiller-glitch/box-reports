# DISCOVER_QUOTES_3 (DQ, 2026-11-04) - NQ history extension backward; metadata-only, NOTHING bought/downloaded
Dataset GLBX.MDP3. Symbology: continuous volume-front `X.v.0` (stype_in=continuous). Spans end 2023-02-09 exclusive (box NQ tick data starts 2023-02-09). Spans: full 2018-01-01..2023-02-09; A = 2021-01-01..2023-02-09; B = 2019-01-01..2021-01-01. Script: outputs/l2vast/ds3/code/discover/dq_q4.py (+dq_q4.json). Budget left $711.74.

## Dataset start / schema gaps
GLBX.MDP3 starts 2010-06-06 for mbp-1, mbp-10, tbbo, trades, bbo-1s/1m, ohlcv-1s/1m/1h/1d, definition, statistics, status. **mbo starts only 2017-05-21** (and cmbp-1/cbbo-* 2017-05-21). No gaps for the requested 2018-2023 span.

## KEY FINDING: 1-min history is ALREADY OWNED back to 2013
NQ, ES, YM ohlcv-1m raw per-year files 2013..2026 and RTY 2017-07..2026 at /mnt/l2/rootmoves/data_autopilot/ohlcv1m/<SYM>_<year>.dbn.zst; cached continuous series 2013-01-02..2026-10-16 in /mnt/l2/l2vast/ds3/cache_te2/<SYM>.npz and outputs/l2vast/ds3/tc/cache/<SYM>.parquet (volume-front). The 1-min rows below are quoted only for completeness; DO NOT BUY them. Also on disk: NQ drv_raw monthly files from 2013-03 (/mnt/l2/rootmoves/data_autopilot/drv_raw_NQ). Not owned: NQ ohlcv-1s/trades/tbbo/mbp-1 before 2023-02-09.

## Quote table (dataset GLBX.MDP3)
| sym | schema | span | records | GB | USD |
|---|---|---|---|---|---|
| NQ | ohlcv-1m | full 2018-01..2023-02 | 1,793,276 | 0.100 | 6.55 (owned) |
| NQ | ohlcv-1m | A 2021-01..2023-02 | 744,580 | 0.042 | 2.72 (owned) |
| NQ | ohlcv-1m | B 2019-01..2020-12 | 699,518 | 0.039 | 2.55 (owned) |
| NQ | ohlcv-1s | full | 59,832,791 | 3.351 | **218.44** |
| NQ | ohlcv-1s | A | 26,568,531 | 1.488 | **97.00** |
| NQ | ohlcv-1s | B | 23,388,391 | 1.310 | **85.39** |
| NQ | trades | full | 415,405,270 | 19.939 | 519.96 |
| NQ | trades | A | 202,915,463 | 9.740 | 253.99 |
| NQ | trades | B | 148,521,074 | 7.129 | 185.90 |
| NQ | tbbo | full | 415,405,270 | 33.232 | 866.60 |
| NQ | tbbo | A | 202,915,463 | 16.233 | 423.31 |
| NQ | tbbo | B | 148,521,074 | 11.882 | 309.84 |
| NQ | mbp-1 | full | 5,221,373,396 | 417.71 | 700.24 |
| NQ | mbp-1 | A | 2,942,795,664 | 235.42 | 394.66 |
| NQ | mbp-1 | B | 1,583,003,482 | 126.64 | 212.30 |
| ES | ohlcv-1m | full / A / B | 1.79M / 0.74M / 0.70M | 0.100/0.042/0.039 | 6.55 / 2.72 / 2.56 (owned) |
| RTY | ohlcv-1m | full / A / B | 1.69M / 0.72M / 0.67M | 0.095/0.040/0.037 | 6.19 / 2.63 / 2.44 (owned) |
| YM | ohlcv-1m | full / A / B | 1.79M / 0.74M / 0.70M | 0.100/0.042/0.039 | 6.52 / 2.71 / 2.54 (owned) |
Notes: tbbo has the same record count as trades but costs 1.67x (not cheap). mbp-1 is cheaper in USD than tbbo here but 418 GB for the full span: a disk impossibility (root 94% full; /mnt/l2 space not checked for this) and 5.2B records; not feasible. Full-span 1-min for all four = $25.8 if one insisted (do not).

## Recommendation (under $300)
1. Cross-index 1-min (ES/RTY/YM/NQ) back to 2018: **$0, already on disk**. Q4 cross-index tools can run on 2018-2023 now.
2. The one cheap genuine gap-filler: **NQ ohlcv-1s 2021-01..2023-02, $97.00** (26.6M rec, 1.49 GB) - gives a second year-regime (2022 bear/vol) at 1-s for the fill/entry model, and keeps $615 reserve. Optional add: NQ ohlcv-1s 2019-01..2020-12 $85.39 (includes Feb-Mar 2020 crash) -> both = $182.39; full 1-s 2018-01..2023-02 = $218.44.
3. Tick history: NQ trades 2021-01..2023-02 = $253.99 (9.7 GB) fits under $300 but leaves ~$458 and is worth it only after 1-s history shows the books survive; full-span trades $520, tbbo and mbp-1 not recommended.
Suggested order: ($0 items first) -> 1-s A ($97) -> 1-s B ($85) -> trades A ($254) only if justified. Wait for user OK before any pull.
