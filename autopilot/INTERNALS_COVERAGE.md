# INTERNALS_COVERAGE: NinjaTrader minute exports of market internals (loader code/th_data/load_internals.py)

Built 2026-11-28 14:48Z. Time zone assumed for the export: **UTC** (DST aware); stamp = bar END (converted to bar END, UTC). Files read: 9 in /mnt/l2/l2vast/ext_internals_drop/.

Feed files: /mnt/l2/l2vast/_dynexit/feeds/internals_<YYYY-MM>.parquet (new prefix; existing tick_/stocks_/xmkt_/age_ feeds and _manifest.json untouched). sec = bar END + 5 s. Clean series: /mnt/l2/l2vast/_internals/clean_<SYM>.parquet.

## Per-symbol load notes

| symbol | files | bars | bad lines | duplicates dropped | fall-back ambiguous rows (second pass) | spring-forward dropped |
|---|---|---|---|---|---|---|
| ADD | ^ADD.Last.txt | 388,035 | 0 | 0 | 0 (0) | 0 |
| ADV | ^ADV.Last.txt | 388,035 | 0 | 0 | 0 (0) | 0 |
| DVOL | ^DVOL.Last.txt | 388,035 | 0 | 0 | 0 (0) | 0 |
| PCR | ^PCR.Last.txt | 388,080 | 0 | 0 | 0 (0) | 0 |
| TICK | ^TICK.Last.txt | 388,281 | 0 | 0 | 0 (0) | 0 |
| TICKQ | ^TICKQ.Last.txt | 388,030 | 0 | 0 | 0 (0) | 0 |
| TRIN | ^TRIN.Last.txt | 388,030 | 0 | 0 | 0 (0) | 0 |
| TRINQ | ^TRINQ.Last.txt | 388,030 | 0 | 0 | 0 (0) | 0 |
| VIX | ^VIX.Last.txt | 5,822 | 0 | 0 | 0 (0) | 0 |

## ADD

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,035 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 979 of 980; distribution (bars: days) 390: 979, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 1 (runs of >= 2 min: 1; days affected 1)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## ADV

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,035 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 979 of 980; distribution (bars: days) 390: 979, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 1 (runs of >= 2 min: 1; days affected 1)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## DVOL

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,035 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 979 of 980; distribution (bars: days) 390: 979, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 1 (runs of >= 2 min: 1; days affected 1)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## PCR

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,080 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 390, max 390; days with exactly 390: 980 of 980; distribution (bars: days) 390: 980
- share of regular-hours minutes present: 1.0000 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 0 (runs of >= 2 min: 0; days affected 0)
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## TICK

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,281 on 1182 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 1, max 390; days with exactly 390: 978 of 983; distribution (bars: days) 390: 978, 385: 1, 345: 1, 1: 3
- share of regular-hours minutes present: 0.9968 over 983 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 8 (runs of >= 2 min: 8; days affected 5)
- largest gaps (ET day, from, to, minutes): 2025-12-25 09:31-15:56 (386); 2023-09-04 11:38-16:00 (263); 2024-03-29 09:31-12:50 (200); 2024-03-29 12:52-16:00 (189); 2023-09-04 09:31-11:36 (126); 2025-12-15 09:31-10:15 (45); 2026-02-23 13:20-13:24 (5); 2025-12-25 15:58-16:00 (3)
- days below 390 RTH bars (day: bars), first 40: 2023-09-04: 1, 2024-03-29: 1, 2025-12-15: 345, 2025-12-25: 1, 2026-02-23: 385
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,884 ; 03:15-09:30 ET: 1 ; after 16:00 ET: 5,883; days with pre-market bars 1

## TICKQ

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,030 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 978 of 980; distribution (bars: days) 390: 978, 385: 1, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 2 (runs of >= 2 min: 2; days affected 2)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45); 2026-02-23 13:20-13:24 (5)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345, 2026-02-23: 385
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## TRIN

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,030 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 978 of 980; distribution (bars: days) 390: 978, 385: 1, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 2 (runs of >= 2 min: 2; days affected 2)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45); 2026-02-23 13:20-13:24 (5)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345, 2026-02-23: 385
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## TRINQ

- first bar (END, UTC) 2023-01-03 14:31 ; last 2026-11-27 21:06 ; ET 2023-01-03 09:31 .. 2026-11-27 16:06; bars 388,030 on 980 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 390, min 345, max 390; days with exactly 390: 978 of 980; distribution (bars: days) 390: 978, 385: 1, 345: 1
- share of regular-hours minutes present: 0.9999 over 980 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 2 (runs of >= 2 min: 2; days affected 2)
- largest gaps (ET day, from, to, minutes): 2025-12-15 09:31-10:15 (45); 2026-02-23 13:20-13:24 (5)
- days below 390 RTH bars (day: bars), first 40: 2025-12-15: 345, 2026-02-23: 385
- weekdays that other symbols have RTH bars but this one has none: 3; first 30: 2023-09-04, 2024-03-29, 2025-12-25
- extended-hours bars (weekdays outside 09:31-16:00 ET): 5,880 ; 03:15-09:30 ET: 0 ; after 16:00 ET: 5,880; days with pre-market bars 0

## VIX

- first bar (END, UTC) 2026-10-14 07:16 ; last 2026-11-27 16:49 ; ET 2026-10-14 03:16 .. 2026-11-27 11:49; bars 5,822 on 8 days
- RTH (09:31-16:00 ET, bar END) bars per day: median 389, min 138, max 389; days with exactly 390: 0 of 8; distribution (bars: days) 389: 5, 388: 1, 285: 1, 138: 1
- share of regular-hours minutes present: 0.8833 over 8 days with any RTH bar (390 per day expected; half days and holidays stubs count as missing)
- gap runs inside regular hours: 10 (runs of >= 2 min: 3; days affected 8)
- largest gaps (ET day, from, to, minutes): 2026-11-27 11:50-16:00 (251); 2026-10-19 14:17-16:00 (104); 2026-11-24 09:31-09:32 (2)
- days below 390 RTH bars (day: bars), first 40: 2026-10-14: 389, 2026-10-15: 389, 2026-10-16: 389, 2026-10-19: 285, 2026-11-23: 389, 2026-11-24: 388, 2026-11-25: 389, 2026-11-27: 138
- weekdays that other symbols have RTH bars but this one has none: 975; first 30: 2023-01-03, 2023-01-04, 2023-01-05, 2023-01-06, 2023-01-09, 2023-01-10, 2023-01-11, 2023-01-12, 2023-01-13, 2023-01-17, 2023-01-18, 2023-01-19, 2023-01-20, 2023-01-23, 2023-01-24, 2023-01-25, 2023-01-26, 2023-01-27, 2023-01-30, 2023-01-31, 2023-02-01, 2023-02-02, 2023-02-03, 2023-02-06, 2023-02-07, 2023-02-08, 2023-02-09, 2023-02-10, 2023-02-13, 2023-02-14
- extended-hours bars (weekdays outside 09:31-16:00 ET): 3,066 ; 03:15-09:30 ET: 2,968 ; after 16:00 ET: 98; days with pre-market bars 8
  VIX pre-market (03:15-09:30 ET, ~375 min) bars per day: median 371, min 371, max 371; share of 375 present 0.989

Wanted symbols not yet present: UVOL, NDX

Unrecognised file-name symbols (loaded anyway): ADV

## Feed files written: 47 months (2023-01 .. 2026-11), 385,269 rows, 103 columns
Months covered per symbol are in the sections above; designs must label results by the months of the SHORTEST symbol they use.
