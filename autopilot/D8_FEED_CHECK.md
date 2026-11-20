# D8_FEED_CHECK: tape statistics for trading date 2026-11-10 (Asia and NY AM), to compare with an NT8 (CQG) tick export (W-D8SPEC, order 1424Z item 1)

Source: engine trade tape (exchange MBO trade records, action T, front-month NQ, `/mnt/l2/l2vast/_bars/trades/`). Trading date 2026-11-10: Asia = 18:00 ET Nov 9 to 02:00 ET Nov 10 (23:00 UTC Nov 9 to 07:00 UTC Nov 10, EST); NY AM = 09:30 to 12:00 ET (14:30 to 17:00 UTC) Nov 10. Aggressor side: +1 buy aggressor (Buy volume), -1 sell aggressor, 0 none (3 records on the whole UTC day).

**Definitions.** Record = one tape row (one fill of one resting order). DISTINCT timestamps = number of different ts values (ns). Order group = records merged when ts and side are equal (what a per-aggressor-order feed shows); 'order groups (ts,side,price)' additionally requires equal price (a sweep across price levels stays several groups). Timestamps are exchange event times in ns; an NT8/CQG export will have its own (coarser) timestamps, so for comparison use totals and the 15-minute tables; to compare counts, merge your export's rows with identical timestamp and side.

Bucket labels are UTC start of the 15-minute bucket (ET = UTC - 5 h).


## Asia, trading date 2026-11-10

| item                                | value                         |
|:------------------------------------|:------------------------------|
| trade records                       | 51093                         |
| total volume (contracts)            | 64484                         |
| buy-aggressor volume                | 32185                         |
| sell-aggressor volume               | 32296                         |
| no-side volume                      | 3                             |
| DISTINCT timestamps                 | 41142                         |
| order groups (ts,side)              | 41243                         |
| order groups (ts,side,price)        | 50354                         |
| first record UTC                    | 2026-11-09T23:00:00.000000000 |
| last record UTC                     | 2026-11-10T06:59:54.116239701 |
| records per distinct ts             | 1.242                         |
| mean size per record                | 1.262                         |
| mean size per order group (ts,side) | 1.564                         |

### Asia: 15-minute buckets (UTC)

| bucket_start_utc   |   records |   volume |   buy_volume |   sell_volume |   delta |   distinct_ts |
|:-------------------|----------:|---------:|-------------:|--------------:|--------:|--------------:|
| 23:00              |      1129 |     1457 |          732 |           722 |      10 |           903 |
| 23:15              |      1041 |     1296 |          622 |           674 |     -52 |           839 |
| 23:30              |      1427 |     1831 |          944 |           887 |      57 |          1097 |
| 23:45              |       956 |     1149 |          722 |           427 |     295 |           783 |
| 00:00              |      2011 |     2632 |         1331 |          1301 |      30 |          1574 |
| 00:15              |      1509 |     1987 |         1030 |           957 |      73 |          1199 |
| 00:30              |      1778 |     2216 |         1073 |          1143 |     -70 |          1371 |
| 00:45              |      2422 |     2951 |         1347 |          1604 |    -257 |          1948 |
| 01:00              |      4646 |     5951 |         2926 |          3025 |     -99 |          3485 |
| 01:15              |      2568 |     3262 |         1623 |          1639 |     -16 |          1931 |
| 01:30              |      2234 |     3349 |         1965 |          1384 |     581 |          1654 |
| 01:45              |      1066 |     1263 |          610 |           653 |     -43 |           890 |
| 02:00              |      1479 |     1962 |         1003 |           959 |      44 |          1137 |
| 02:15              |      1234 |     1607 |          766 |           841 |     -75 |           921 |
| 02:30              |      1368 |     1635 |          782 |           853 |     -71 |          1120 |
| 02:45              |      1208 |     1538 |          754 |           784 |     -30 |           967 |
| 03:00              |      1201 |     1516 |          684 |           832 |    -148 |           955 |
| 03:15              |      1166 |     1396 |          685 |           711 |     -26 |           978 |
| 03:30              |      2641 |     3387 |         1355 |          2032 |    -677 |          2123 |
| 03:45              |      2383 |     2951 |         1548 |          1403 |     145 |          2037 |
| 04:00              |      1608 |     1995 |          979 |          1016 |     -37 |          1416 |
| 04:15              |      2050 |     2561 |         1381 |          1180 |     201 |          1643 |
| 04:30              |       930 |     1150 |          564 |           586 |     -22 |           755 |
| 04:45              |       832 |     1043 |          550 |           493 |      57 |           677 |
| 05:00              |      1329 |     1647 |          814 |           833 |     -19 |          1065 |
| 05:15              |      1003 |     1218 |          637 |           581 |      56 |           849 |
| 05:30              |      1779 |     2267 |         1242 |          1025 |     217 |          1492 |
| 05:45              |      1121 |     1351 |          655 |           696 |     -41 |           958 |
| 06:00              |      1276 |     1559 |          660 |           899 |    -239 |          1097 |
| 06:15              |      1441 |     1711 |          846 |           865 |     -19 |          1283 |
| 06:30              |      1202 |     1382 |          696 |           686 |      10 |          1050 |
| 06:45              |      1055 |     1264 |          659 |           605 |      54 |           945 |

## NY AM, trading date 2026-11-10

| item                                | value                         |
|:------------------------------------|:------------------------------|
| trade records                       | 234912                        |
| total volume (contracts)            | 292676                        |
| buy-aggressor volume                | 144634                        |
| sell-aggressor volume               | 148042                        |
| no-side volume                      | 0                             |
| DISTINCT timestamps                 | 203788                        |
| order groups (ts,side)              | 204087                        |
| order groups (ts,side,price)        | 232358                        |
| first record UTC                    | 2026-11-10T14:30:00.000021317 |
| last record UTC                     | 2026-11-10T16:59:59.904831323 |
| records per distinct ts             | 1.153                         |
| mean size per record                | 1.246                         |
| mean size per order group (ts,side) | 1.434                         |

### NY AM: 15-minute buckets (UTC)

| bucket_start_utc   |   records |   volume |   buy_volume |   sell_volume |   delta |   distinct_ts |
|:-------------------|----------:|---------:|-------------:|--------------:|--------:|--------------:|
| 14:30              |     43202 |    52811 |        26090 |         26721 |    -631 |         37287 |
| 14:45              |     34811 |    43356 |        21636 |         21720 |     -84 |         30428 |
| 15:00              |     32077 |    40047 |        20091 |         19956 |     135 |         27825 |
| 15:15              |     23839 |    29449 |        14553 |         14896 |    -343 |         20787 |
| 15:30              |     20536 |    25823 |        12296 |         13527 |   -1231 |         17820 |
| 15:45              |     22861 |    29134 |        14578 |         14556 |      22 |         19419 |
| 16:00              |     16783 |    21456 |        10521 |         10935 |    -414 |         14419 |
| 16:15              |     15548 |    19306 |         9342 |          9964 |    -622 |         13542 |
| 16:30              |     12948 |    16065 |         7965 |          8100 |    -135 |         11353 |
| 16:45              |     12307 |    15229 |         7562 |          7667 |    -105 |         10908 |
