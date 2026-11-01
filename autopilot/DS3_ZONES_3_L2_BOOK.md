# DS3_ZONES_3_L2_BOOK - ZL-1 order-book zone streams (OLD CAP interim, label day <= 20260206; written 2026-11-01)

## DATA line
NQ 1-s L2 table (aggregates of mbp-10; /mnt/l2/l2vast/tables/NQ/1s) on disk 2023-02..2026-10; used 2023-08..2026-02-06 (651 label days, OLD CAP; no post-cap file rows read). The 1-s table has no duplicated timestamps in the 11 tape-defect months (checked), so tape_dedup copies are not needed for these streams (they matter for ZL-2 tape streams and for the cap extension: post-cap tape months). Everything derivable from the table; nothing to buy. Raw MBO is not on disk: level prices are exact only for contiguous 10-level books (bspan = 9 ticks), used for DEF/PUL; ABS/ICE use the best price. 10-s/100-ms tables not needed.

## Streams (96 files, out/zl/streams_book/, POI format + strength/side/formed/ntouch/decay; README out/zl/README_streams_book.md)
ABS 10 params x 3 keeps (primary k5N10 = L2 gate g1; plus loosened k1/k2/k3 since the gate definition gives 0.3 events/day); ICE 4 x 3 (primary R2N30); DEF 4 x 3 (primary k3N30); PUL 2 x 3; SWP (level + extreme) x (prior-day, session, swing) x (N5, N15) x 3 keeps = 36. Events/day (counts_summary.csv): ABS k5N10 0.30, k1N10 6.8; ICE R2N30 35.8; DEF k3N30 3.2; PUL k3 23.3; SWP pd 0.85, session 8.2, swing 44.6. Preregs: ZL1_book_streams_prereg.md sha256 d84ca7c09038b5f17207aa35c55b505894e8a31403bac6fe00726ce119909b2d, ADD1 sha256 342e59e6a66ae3a56c750bbcb2b980835858671b311fbfa57311606aee8e76a5 (both in DECISIONS.md before any outcome statistic).

## Descriptive table (keep 1 h; reaction = after first return to the level, price moves X pts away on the approach side before X pts through, 30 min; p = share of 200 placebo draws >= observed; A = random level, same count, offset within the stream's own q95; B = observed offsets shuffled across events; <=20k events per stream)
| stream               |     n |   ev_day |   touched_keep |   X5_obs |   X5_A |   X5_pA |   X5_B |   X5_pB |   X10_obs |   X10_A |   X10_pA |
|:---------------------|------:|---------:|---------------:|---------:|-------:|--------:|-------:|--------:|----------:|--------:|---------:|
| ABS|k10N10|1h        |    46 |    0.071 |          0.913 |    0.429 |  0.464 |   0.725 |  0.447 |   0.675 |     0.5   |   0.518 |    0.625 |
| ABS|k1N10|1h         |  4427 |    6.8   |          0.919 |    0.498 |  0.496 |   0.435 |  0.504 |   0.855 |     0.496 |   0.491 |    0.29  |
| ABS|k1N30|1h         |   261 |    0.401 |          0.843 |    0.516 |  0.538 |   0.74  |  0.553 |   0.89  |     0.484 |   0.511 |    0.725 |
| ABS|k2N10|1h         |  1048 |    1.61  |          0.912 |    0.496 |  0.477 |   0.125 |  0.486 |   0.195 |     0.495 |   0.483 |    0.225 |
| ABS|k2N30|1h         |    76 |    0.117 |          0.855 |    0.436 |  0.515 |   0.91  |  0.576 |   0.995 |     0.5   |   0.549 |    0.745 |
| ABS|k3N10|1h         |   481 |    0.739 |          0.909 |    0.493 |  0.476 |   0.22  |  0.494 |   0.545 |     0.494 |   0.479 |    0.295 |
| ABS|k3N30|1h         |    27 |    0.041 |          0.963 |    0.364 |  0.465 |   0.865 |  0.582 |   1     |     0.5   |   0.586 |    0.795 |
| ABS|k5N10|1h         |   194 |    0.298 |          0.912 |    0.517 |  0.473 |   0.08  |  0.507 |   0.37  |     0.553 |   0.495 |    0.08  |
| ABS|k5N30|1h         |    15 |    0.023 |          1     |    0.615 |  0.642 |   0.68  |  0.705 |   0.98  |     0.636 |   0.669 |    0.67  |
| ABS|k5N5|1h          |   465 |    0.714 |          0.89  |    0.519 |  0.491 |   0.11  |  0.509 |   0.26  |     0.492 |   0.491 |    0.525 |
| DEF|k3N10|1h         | 15438 |   23.714 |          0.939 |    0.494 |  0.504 |   1     |  0.504 |   0.99  |     0.485 |   0.5   |    1     |
| DEF|k3N30|1h         |  2095 |    3.218 |          0.918 |    0.477 |  0.501 |   0.995 |  0.502 |   0.995 |     0.486 |   0.493 |    0.68  |
| DEF|k3N60|1h         |   431 |    0.662 |          0.926 |    0.48  |  0.502 |   0.815 |  0.506 |   0.87  |     0.422 |   0.481 |    0.95  |
| DEF|k5N30|1h         |   750 |    1.152 |          0.917 |    0.452 |  0.495 |   0.995 |  0.496 |   0.995 |     0.465 |   0.486 |    0.865 |
| ICE|R2N10|1h         | 23061 |   35.424 |          0.958 |    0.504 |  0.504 |   0.55  |  0.505 |   0.645 |     0.499 |   0.501 |    0.67  |
| ICE|R2N30|1h         | 23329 |   35.836 |          0.957 |    0.504 |  0.506 |   0.735 |  0.506 |   0.83  |     0.501 |   0.502 |    0.59  |
| ICE|R3N30|1h         |  1211 |    1.86  |          0.945 |    0.503 |  0.488 |   0.125 |  0.497 |   0.25  |     0.503 |   0.491 |    0.24  |
| ICE|R5N30|1h         |    10 |    0.015 |          0.9   |    0.286 |  0.515 |   0.915 |  0.316 |   0.92  |     0.333 |   0.455 |    0.855 |
| PUL|k3|1h            | 15144 |   23.263 |          0.939 |    0.499 |  0.497 |   0.225 |  0.498 |   0.35  |     0.492 |   0.499 |    0.97  |
| PUL|k5|1h            |  4201 |    6.453 |          0.944 |    0.499 |  0.495 |   0.31  |  0.495 |   0.35  |     0.496 |   0.501 |    0.75  |
| SWP|ext_pd_N15|1h    |   577 |    0.886 |          0.808 |    0.403 |  0.491 |   1     |  0.476 |   1     |     0.396 |   0.479 |    1     |
| SWP|ext_pd_N5|1h     |   554 |    0.851 |          0.825 |    0.403 |  0.491 |   1     |  0.474 |   1     |     0.396 |   0.477 |    1     |
| SWP|ext_sess_N15|1h  |  5519 |    8.478 |          0.884 |    0.482 |  0.504 |   1     |  0.494 |   0.98  |     0.488 |   0.5   |    0.93  |
| SWP|ext_sess_N5|1h   |  5362 |    8.237 |          0.897 |    0.483 |  0.503 |   0.995 |  0.494 |   0.955 |     0.49  |   0.499 |    0.9   |
| SWP|ext_swing_N15|1h | 29747 |   45.694 |          0.9   |    0.494 |  0.507 |   1     |  0.502 |   0.99  |     0.495 |   0.503 |    0.985 |
| SWP|ext_swing_N5|1h  | 29002 |   44.55  |          0.909 |    0.492 |  0.505 |   1     |  0.501 |   1     |     0.496 |   0.503 |    0.99  |
| SWP|lvl_pd_N15|1h    |   577 |    0.886 |          0.929 |    0.439 |  0.461 |   0.93  |  0.469 |   0.95  |     0.443 |   0.472 |    0.92  |
| SWP|lvl_pd_N5|1h     |   554 |    0.851 |          0.928 |    0.44  |  0.46  |   0.825 |  0.47  |   0.955 |     0.435 |   0.47  |    0.95  |
| SWP|lvl_sess_N15|1h  |  5519 |    8.478 |          0.947 |    0.491 |  0.491 |   0.515 |  0.49  |   0.485 |     0.488 |   0.491 |    0.7   |
| SWP|lvl_sess_N5|1h   |  5362 |    8.237 |          0.947 |    0.491 |  0.49  |   0.48  |  0.49  |   0.425 |     0.487 |   0.491 |    0.725 |
| SWP|lvl_swing_N15|1h | 29747 |   45.694 |          0.953 |    0.493 |  0.501 |   1     |  0.499 |   0.985 |     0.499 |   0.501 |    0.71  |
| SWP|lvl_swing_N5|1h  | 29002 |   44.55  |          0.953 |    0.495 |  0.499 |   0.915 |  0.498 |   0.86  |     0.502 |   0.501 |    0.365 |
Full table (all keeps, windows PRE/HOLD/L6M/X, undecided shares): out/zl/desc_table.csv. Plain reading: no book stream reacts better than its placebo in a way that stands out (best: ABS k5N10 X5 0.517 vs 0.473, p 0.08, n 194, one of 96); defended walls (DEF) and prior-day sweep extremes react WORSE than random levels (SWP ext_pd 0.40 vs 0.49: price tends to go through where the stops were). Descriptive only; ZL-3 scores drawdown.

## Causality audit
100 random rows recomputed from raw 1-s rows truncated at the end of the event bin: 100/100 found, max price diff 0.0, max strength diff 0.0; independent pandas check of ABS 20/20; global check SS[ek] >= event second and cap >= ek on 702,696 rows: 0 violations (out/zl/audit_rows.csv). A roll-day frame defect (L2 table carries another contract than the path on 10 days) was found and fixed (static per label-day/instr offset table); the v0/v1 outputs are kept aside, not used.

## LIVE definitions (D7 has the 10-level book, print tape and absorption/iceberg/sweep/pulled detectors)
* ABS: per side, over the last N s: best price unchanged, contracts traded at my best >= k x median(my 10 level sizes now), no clear of my best. D7 computes it live from its book + prints. Event latched once per episode; keep 1/4/24 h, weight exp(-age/(keep/2)).
* ICE: refill row = print at best, in-second touch dip below previous size, size restored >= previous, price unchanged, no clear; event = >= R such rows at one price in N s. Live from book.
* DEF: wall = level size >= k x median, tracked by price while in the 10 visible levels; accumulate seconds while within 2 ticks of best; event at >= N s, discard if a print trades through it. Live from the 10-level book (needs a contiguous book). PUL: wall (>= 5 s old, was within 3 ticks) vanishes (size < 0.3 x peak or best moves past it) with no print at/through it. Live.
* SWP: needs the levels: prior-day H/L, last completed session H/L and 5-min fractal-5 swings (confirmed 2 bars later). Prior-day and session H/L are in the daily zones file or computed from D7's own tape since 18:00 ET (needs a 2-day warm start); swing levels from D7's own 5-min bars. Event = trade >= 1 tick beyond, last print back inside within N min; emit level and extreme. Live once levels are loaded; the daily file is the safe route for prior-day.
* Freshness: end = first return after the price was > 0.5 pt away; D7 tracks it from its own ticks.

## OLD CAP interim: checkpoint (STOPPED at lead order; no workers running)
Built: events, 96 streams, desc (96 json), counts, audit, README. Code: l2vast/ds3/code/zl/ zl1_kernels.py (numba detectors), zl1_build.py (CAP_LD MONTH... ; static frame table frame_off_ldinstr.csv via make_fo_table(months, cap)), zl1_streams.py (CAP_LD), zl1_desc.py (CAP_LD NAME...), zl1_audit.py (CAP_LD), zl1_report.py. Outputs: l2vast/ds3/out/zl/{events,streams_book,desc,desc_table.csv,counts_*.csv,audit_rows.csv}.
Resume/extend to 20261031 after REDO-1 announces de-duplicated tables: (1) set ZL_CAP=20261031 in env (path_arrays reads it); call zl1_build.make_fo_table(new_months, cap) to append offsets; (2) run zl1_build.py 20261031 2026-02 ... 2026-10 (existing month files are never overwritten, so 2026-02 must be re-run into a new file name: delete nothing, add the month files for 2026-02 days after 20260206 by moving the old 2026-02 event files to a _oldcap suffix first); (3) zl1_streams.py 20261031 would skip existing stream files: for extension write new stream files with suffix _ext (or move old ones aside) because stream ek indices are positions in SS and SS extends only at the end, so existing rows stay valid and only new events need appending; (4) rerun zl1_desc.py on the extended streams, 2 workers, about 1 h; (5) audit. Windows to report on the new REDO columns: L1M..MID.
Not done: tape/volume streams (ZL-2); window columns on new REDO windows; the 2-h MORNING updates after this one.
