# ORDER 20261120_1432Z: NT8 (CQG) tick fingerprint for the feed check: compare with your tape
(Written by the relay, Claude. Josh exported the ticks himself from NT8 at 14:26Z; the numbers below are the relay's counts from that file. Research data only.)

Source: NT8 Historical Data export, NQ 12-26, Tick, Last (format: UTC time; last; bid; ask; volume), 2026-11-09 05:00 UTC to 2026-11-11 05:00 UTC, 1,327,128 records.
Facts: timestamps are UTC with MILLISECOND resolution only (no sub-millisecond digits); 96.7% of records are size 1; volume / records = 1.08; 45% of records share a timestamp with the previous record (expected at 1 ms resolution). So this feed looks PER-FILL, not bundled per aggressor order.
ASIA session, trading date 20261110 (2026-11-09 23:00 UTC to 2026-11-10 07:00 UTC): 59,887 records, volume 64,484, distinct timestamps 33,019, groups (same ms + same side) 34,458, buy volume 32,187, sell volume 32,297 (side = last >= ask buy, last <= bid sell, using the bid/ask in the export).

Do now (extends order 1424Z item 1; answer in autopilot/D8_FEED_CHECK.md and one MORNING.md line):
1. The same numbers from your tape for the same window: records, volume, buy / sell volume (your aggressor flag), and the 15-minute table below side by side with differences. If records and volume match within a fraction of a percent, say so plainly.
2. Rebuild cdr_100, vsess_600 and the 1-minute bars for that Asia session from YOUR tape with (a) timestamps truncated to the millisecond and prints inside one millisecond kept in tape order, and (b) aggressor side taken from last-vs-bid/ask instead of your flag (if you hold the quote at print time): how many bar closes move, by how much, and do the triggers of Ldcdb0b6e and Lfb608c7b still fire at the same times? That is the fidelity test for D8 on this feed.
3. s_vol looks like the average print size (thr = N x s_vol; cdr_100 = 110.0): confirm the exact definition and its value for 20261110 Asia; on the NT8 file volume / records for that session is 1.077.

NT8 (CQG) 15-minute table, Asia td 20261110:
| 15-min UTC | records | volume | buy vol | sell vol |
|---|---|---|---|---|
| 09 23:00 | 1260 | 1457 | 735 | 722 |
| 09 23:15 | 1207 | 1296 | 622 | 674 |
| 09 23:30 | 1713 | 1831 | 944 | 887 |
| 09 23:45 | 1105 | 1149 | 722 | 427 |
| 10 00:00 | 2416 | 2632 | 1331 | 1301 |
| 10 00:15 | 1788 | 1987 | 1030 | 957 |
| 10 00:30 | 2059 | 2216 | 1073 | 1143 |
| 10 00:45 | 2778 | 2951 | 1347 | 1604 |
| 10 01:00 | 5559 | 5951 | 2926 | 3025 |
| 10 01:15 | 3105 | 3262 | 1623 | 1639 |
| 10 01:30 | 2717 | 3349 | 1965 | 1384 |
| 10 01:45 | 1202 | 1263 | 610 | 653 |
| 10 02:00 | 1789 | 1962 | 1003 | 959 |
| 10 02:15 | 1497 | 1607 | 766 | 841 |
| 10 02:30 | 1570 | 1635 | 782 | 853 |
| 10 02:45 | 1459 | 1538 | 754 | 784 |
| 10 03:00 | 1419 | 1516 | 684 | 832 |
| 10 03:15 | 1315 | 1396 | 685 | 711 |
| 10 03:30 | 3129 | 3387 | 1355 | 2032 |
| 10 03:45 | 2768 | 2951 | 1547 | 1404 |
| 10 04:00 | 1836 | 1995 | 979 | 1016 |
| 10 04:15 | 2416 | 2561 | 1381 | 1180 |
| 10 04:30 | 1096 | 1150 | 564 | 586 |
| 10 04:45 | 959 | 1043 | 550 | 493 |
| 10 05:00 | 1547 | 1647 | 814 | 833 |
| 10 05:15 | 1137 | 1218 | 637 | 581 |
| 10 05:30 | 2136 | 2267 | 1242 | 1025 |
| 10 05:45 | 1292 | 1351 | 655 | 696 |
| 10 06:00 | 1484 | 1559 | 660 | 899 |
| 10 06:15 | 1623 | 1711 | 846 | 865 |
| 10 06:30 | 1336 | 1382 | 696 | 686 |
| 10 06:45 | 1170 | 1264 | 659 | 605 |
