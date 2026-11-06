
## GATE 0 CHECK - VALID V1 sealed list (2026-11-06T18:59Z)

| gate | value | threshold | result |
|---|---|---|---|
| 1 trades matched / union | 0.494 | >= 0.85 | FAIL |
| 2 net gap |engine-live|/|live| | 0.665 | <= 0.15 | FAIL |
| 3 cuts matched / union of cuts | 0.180 | >= 0.85 | FAIL |
| 4 cut dollars |engine cuts - live cuts| / |live cuts| | 0.006 | <= 0.10 | PASS |

**GATE 0: FAIL (1, 2, 3)**

Informational: trades engine 182 live 187 matched 122 (matched/live 0.652, matched/engine 0.670); net engine +34879 live +104095; exit-type agreement 0.645; maxDD engine 25893 live 14490 gap 0.440.
Cuts: live 92, engine 85, matched (same trade, cut, exit within 10 s) 27; recall 0.293, precision 0.318; live cut $ -140350, engine cut $ -139546; matched-pair cut $ delta (live-engine, pairs where either side cuts) +31119 = 0.222 of |live cut $|.

### Cuts per book

| book | live cuts | engine cuts | matched cuts | live cut $ | engine cut $ | missed | false |
|---|---|---|---|---|---|---|---|
| A7 | 14 | 0 | 0 | -9925 | +0 | 14 | 0 |
| H7 | 2 | 9 | 0 | -1970 | -12634 | 2 | 9 |
| K7 | 30 | 29 | 9 | -26355 | -23679 | 21 | 20 |
| M7 | 13 | 17 | 5 | -13615 | -15988 | 8 | 12 |
| O7 | 2 | 0 | 0 | -1140 | +0 | 2 | 0 |
| P7 | 24 | 27 | 10 | -73500 | -79219 | 14 | 17 |
| U7 | 3 | 3 | 3 | -7760 | -8027 | 0 | 0 |
| X3 | 2 | 0 | 0 | -2910 | +0 | 2 | 0 |
| X4 | 1 | 0 | 0 | -1770 | +0 | 1 | 0 |
| X5 | 1 | 0 | 0 | -1405 | +0 | 1 | 0 |

### False cuts (engine cut, live held / no live trade / timing off): 58

| book | live time ET | live $ | engine time | engine $ | reason |
|---|---|---|---|---|---|
| K7 | - | - | Mon 01:21:10 | -721 | no live trade |
| P7 | - | - | Mon 01:10:40 | -2659 | no live trade |
| M7 | Mon 04:18:39 | -2420 | Mon 04:15:50 | -1870 | live cut +169 s off |
| K7 | - | - | Mon 04:14:04 | -1716 | no live trade |
| P7 | Mon 04:18:39 | -2050 | Mon 03:46:30 | -1248 | live cut +1929 s off |
| M7 | Mon 10:47:27 | -715 | Mon 10:39:00 | -609 | live cut +507 s off |
| H7 | - | - | Mon 11:31:40 | -676 | no live trade |
| K7 | Mon 18:45:37 | -615 | Mon 18:46:11 | -613 | live cut -34 s off |
| H7 | - | - | Mon 19:20:50 | -1239 | no live trade |
| K7 | Mon 19:47:21 | -635 | Mon 20:06:10 | -643 | live cut -1129 s off |
| K7 | Mon 22:36:58 | -805 | Mon 22:36:42 | -665 | live cut +16 s off |
| H7 | - | - | Mon 21:59:51 | -1289 | no live trade |
| P7 | - | - | Mon 23:30:10 | -3819 | no live trade |
| H7 | - | - | Tue 01:40:00 | -1104 | no live trade |
| P7 | - | - | Tue 01:38:10 | +7716 | no live trade |
| K7 | Tue 02:55:35 | -1660 | Tue 01:51:32 | -618 | live held (exit stop) |
| M7 | Tue 02:47:29 | -1615 | Tue 02:28:10 | -717 | live held (exit stop) |
| M7 | - | - | Tue 03:03:10 | -563 | no live trade |
| P7 | - | - | Tue 03:39:20 | -2207 | no live trade |
| P7 | - | - | Tue 05:24:20 | -2447 | no live trade |
| M7 | - | - | Tue 06:18:21 | -1373 | no live trade |
| M7 | - | - | Tue 07:15:50 | -1268 | no live trade |
| M7 | - | - | Tue 07:49:20 | -568 | no live trade |
| M7 | Tue 10:32:06 | -645 | Tue 10:32:30 | -575 | live cut -24 s off |
| H7 | - | - | Tue 10:45:20 | -673 | no live trade |
| M7 | - | - | Tue 11:18:40 | -616 | no live trade |
| K7 | Tue 11:39:37 | -595 | Tue 11:41:20 | -636 | live cut -103 s off |
| K7 | - | - | Tue 12:34:00 | -630 | no live trade |
| K7 | Tue 18:37:42 | -1780 | Tue 18:34:20 | -1281 | live cut +202 s off |
| P7 | - | - | Tue 18:31:20 | -4613 | no live trade |
| K7 | Tue 22:02:00 | +2395 | Tue 21:50:10 | -1101 | live held (exit target) |
| H7 | - | - | Tue 21:46:50 | -2482 | no live trade |
| P7 | Tue 22:02:00 | +4800 | Tue 21:56:20 | -2515 | live held (exit target) |
| H7 | - | - | Tue 22:03:20 | -1423 | no live trade |
| P7 | Tue 22:16:23 | -2440 | Tue 22:16:50 | -3287 | live cut -27 s off |
| P7 | Wed 01:24:11 | -4030 | Wed 01:19:40 | -4500 | live cut +271 s off |
| K7 | Wed 01:19:12 | -1365 | Wed 01:14:50 | -1216 | live cut +262 s off |
| K7 | Wed 02:21:31 | -655 | Wed 02:21:00 | -595 | live cut +31 s off |
| P7 | Wed 04:02:07 | -4105 | Wed 03:59:10 | -2473 | live cut +177 s off |
| K7 | Wed 04:02:07 | -1095 | Wed 03:59:10 | -613 | live cut +177 s off |
| M7 | Wed 04:02:07 | -1745 | Wed 04:01:30 | -1434 | live cut +37 s off |
| P7 | Wed 07:25:04 | -90 | Wed 07:31:40 | -5137 | live held (exit lock) |
| P7 | - | - | Wed 08:05:40 | -4873 | no live trade |
| K7 | Wed 11:08:05 | -655 | Wed 11:08:30 | -843 | live cut -25 s off |
| M7 | Wed 11:53:08 | -650 | Wed 12:02:30 | -800 | live cut -562 s off |
| K7 | Wed 12:36:43 | -650 | Wed 12:38:50 | -743 | live cut -127 s off |
| K7 | Wed 14:17:26 | -585 | Wed 14:17:50 | -665 | live cut -24 s off |
| P7 | Wed 19:57:29 | +8390 | Wed 19:30:20 | -4527 | live held (exit target) |
| K7 | Wed 21:35:06 | -580 | Wed 21:48:50 | -737 | live cut -824 s off |
| H7 | - | - | Wed 23:45:10 | -2381 | no live trade |
| H7 | - | - | Thu 01:11:40 | -1367 | no live trade |
| K7 | Thu 01:00:38 | -650 | Thu 01:11:20 | -609 | live cut -642 s off |
| P7 | Thu 01:47:21 | -3640 | Thu 01:47:00 | -2517 | live cut +21 s off |
| P7 | Thu 03:17:20 | +7190 | Thu 02:57:50 | -3983 | live held (exit target) |
| M7 | Thu 03:17:20 | +2400 | Thu 02:57:50 | -1163 | live held (exit target) |
| K7 | Thu 04:09:53 | -695 | Thu 04:11:40 | -783 | live cut -107 s off |
| P7 | Thu 03:48:37 | -1295 | Thu 03:48:11 | -1259 | live cut +26 s off |
| K7 | - | - | Thu 06:27:10 | -635 | no live trade |

### Missed cuts (live cut, engine held / no trade / timing off): 65

| book | live time ET | live $ | engine time | engine $ | reason |
|---|---|---|---|---|---|
| K7 | Mon 01:20:34 | -1900 | - | - | no engine trade |
| H7 | Mon 01:21:10 | -1370 | - | - | no engine trade |
| P7 | Mon 01:21:10 | -1405 | - | - | no engine trade |
| M7 | Mon 04:18:39 | -2420 | Mon 04:15:50 | -1870 | engine cut +169 s off |
| P7 | Mon 04:18:39 | -2050 | Mon 03:46:30 | -1248 | engine cut +1929 s off |
| X5 | Mon 04:06:50 | -1405 | - | - | no engine trade |
| X4 | Mon 07:06:08 | -1770 | Mon 07:35:54 | -3108 | engine held (exit stop) |
| K7 | Mon 08:36:49 | -640 | - | - | no engine trade |
| M7 | Mon 08:36:50 | -1775 | - | - | no engine trade |
| X3 | Mon 08:36:46 | -1685 | Mon 08:37:00 | -3108 | engine held (exit stop) |
| X3 | Mon 08:43:22 | -1225 | - | - | no engine trade |
| M7 | Mon 10:09:45 | -575 | - | - | no engine trade |
| P7 | Mon 10:09:42 | -2865 | - | - | no engine trade |
| M7 | Mon 10:47:27 | -715 | Mon 10:39:00 | -609 | engine cut +507 s off |
| H7 | Mon 10:38:19 | -600 | - | - | no engine trade |
| K7 | Mon 10:38:42 | -625 | - | - | no engine trade |
| K7 | Mon 12:56:12 | -1300 | - | - | no engine trade |
| K7 | Mon 18:45:37 | -615 | Mon 18:46:11 | -613 | engine cut -34 s off |
| K7 | Mon 19:47:21 | -635 | Mon 20:06:10 | -643 | engine cut -1129 s off |
| K7 | Mon 22:36:58 | -805 | Mon 22:36:42 | -665 | engine cut +16 s off |
| P7 | Mon 21:03:11 | -2495 | - | - | no engine trade |
| A7 | Tue 00:42:01 | -805 | Tue 02:55:28 | -1254 | engine held (exit stop) |
| A7 | Tue 01:30:05 | -700 | - | - | no engine trade |
| K7 | Tue 01:47:31 | -1030 | - | - | no engine trade |
| O7 | Tue 09:53:39 | -445 | - | - | no engine trade |
| P7 | Tue 10:23:25 | -2745 | - | - | no engine trade |
| M7 | Tue 10:32:06 | -645 | Tue 10:32:30 | -575 | engine cut -24 s off |
| K7 | Tue 11:39:37 | -595 | Tue 11:41:20 | -636 | engine cut -103 s off |
| K7 | Tue 18:37:42 | -1780 | Tue 18:34:20 | -1281 | engine cut +202 s off |
| A7 | Tue 18:31:21 | -565 | Tue 18:38:49 | -1254 | engine held (exit stop) |
| P7 | Tue 18:37:42 | -6510 | - | - | no engine trade |
| A7 | Tue 20:35:04 | -655 | Tue 20:40:41 | +1195 | engine held (exit target) |
| A7 | Tue 20:41:30 | -850 | - | - | no engine trade |
| A7 | Tue 21:30:20 | -700 | Tue 22:01:44 | +1195 | engine held (exit target) |
| A7 | Tue 22:16:47 | -635 | Tue 22:07:18 | +1195 | engine held (exit target) |
| P7 | Tue 22:16:23 | -2440 | Tue 22:16:50 | -3287 | engine cut -27 s off |
| A7 | Wed 00:15:23 | -680 | Wed 00:24:24 | +1195 | engine held (exit target) |
| A7 | Wed 00:21:54 | -670 | - | - | no engine trade |
| A7 | Wed 00:27:18 | -520 | - | - | no engine trade |
| A7 | Wed 01:24:11 | -885 | - | - | no engine trade |
| P7 | Wed 01:24:11 | -4030 | Wed 01:19:40 | -4500 | engine cut +271 s off |
| K7 | Wed 01:19:12 | -1365 | Wed 01:14:50 | -1216 | engine cut +262 s off |
| K7 | Wed 02:21:31 | -655 | Wed 02:21:00 | -595 | engine cut +31 s off |
| K7 | Wed 04:02:07 | -1095 | Wed 03:59:10 | -613 | engine cut +177 s off |
| P7 | Wed 04:02:07 | -4105 | Wed 03:59:10 | -2473 | engine cut +177 s off |
| M7 | Wed 04:02:07 | -1745 | Wed 04:01:30 | -1434 | engine cut +37 s off |
| K7 | Wed 11:08:05 | -655 | Wed 11:08:30 | -843 | engine cut -25 s off |
| M7 | Wed 11:53:08 | -650 | Wed 12:02:30 | -800 | engine cut -562 s off |
| K7 | Wed 12:36:43 | -650 | Wed 12:38:50 | -743 | engine cut -127 s off |
| K7 | Wed 14:17:26 | -585 | Wed 14:17:50 | -665 | engine cut -24 s off |
| K7 | Wed 15:31:33 | -605 | Wed 15:39:42 | +1244 | engine held (exit target) |
| A7 | Wed 19:10:07 | -685 | Wed 19:13:18 | -1254 | engine held (exit stop) |
| A7 | Wed 19:44:04 | -685 | Wed 19:58:31 | +1195 | engine held (exit target) |
| K7 | Wed 21:35:06 | -580 | Wed 21:48:50 | -737 | engine cut -824 s off |
| P7 | Wed 21:48:29 | -2620 | - | - | no engine trade |
| K7 | Thu 01:00:38 | -650 | Thu 01:11:20 | -609 | engine cut -642 s off |
| A7 | Thu 01:13:43 | -890 | Thu 01:15:01 | -1005 | engine held (exit lock) |
| P7 | Thu 01:47:21 | -3640 | Thu 01:47:00 | -2517 | engine cut +21 s off |
| K7 | Thu 04:09:53 | -695 | Thu 04:11:40 | -783 | engine cut -107 s off |
| P7 | Thu 03:48:37 | -1295 | Thu 03:48:11 | -1259 | engine cut +26 s off |
## GATE 0 CHECK - VALID V2 variant allea+kfix+1s (2026-11-06T18:59Z)

| gate | value | threshold | result |
|---|---|---|---|
| 1 trades matched / union | 0.496 | >= 0.85 | FAIL |
| 2 net gap |engine-live|/|live| | 0.484 | <= 0.15 | FAIL |
| 3 cuts matched / union of cuts | 0.176 | >= 0.85 | FAIL |
| 4 cut dollars |engine cuts - live cuts| / |live cuts| | 0.179 | <= 0.10 | FAIL |

**GATE 0: FAIL (1, 2, 3, 4)**

Informational: trades engine 217 live 187 matched 134 (matched/live 0.717, matched/engine 0.618); net engine +53710 live +104095; exit-type agreement 0.632; maxDD engine 24024 live 14490 gap 0.397.
Cuts: live 92, engine 102, matched (same trade, cut, exit within 10 s) 29; recall 0.315, precision 0.284; live cut $ -140350, engine cut $ -165505; matched-pair cut $ delta (live-engine, pairs where either side cuts) +23770 = 0.169 of |live cut $|.

### Cuts per book

| book | live cuts | engine cuts | matched cuts | live cut $ | engine cut $ | missed | false |
|---|---|---|---|---|---|---|---|
| A7 | 14 | 0 | 0 | -9925 | +0 | 14 | 0 |
| H7 | 2 | 9 | 0 | -1970 | -14160 | 2 | 9 |
| K7 | 30 | 41 | 13 | -26355 | -29234 | 17 | 28 |
| M7 | 13 | 17 | 4 | -13615 | -14675 | 9 | 13 |
| O7 | 2 | 0 | 0 | -1140 | +0 | 2 | 0 |
| P7 | 24 | 32 | 10 | -73500 | -99889 | 14 | 22 |
| U7 | 3 | 3 | 2 | -7760 | -7548 | 1 | 1 |
| X3 | 2 | 0 | 0 | -2910 | +0 | 2 | 0 |
| X4 | 1 | 0 | 0 | -1770 | +0 | 1 | 0 |
| X5 | 1 | 0 | 0 | -1405 | +0 | 1 | 0 |

### False cuts (engine cut, live held / no live trade / timing off): 73

| book | live time ET | live $ | engine time | engine $ | reason |
|---|---|---|---|---|---|
| K7 | - | - | Sun 19:21:13 | -1116 | no live trade |
| P7 | - | - | Sun 19:31:05 | -6561 | no live trade |
| K7 | - | - | Sun 19:55:49 | -562 | no live trade |
| M7 | Mon 04:18:39 | -2420 | Mon 04:14:22 | -1655 | live cut +257 s off |
| P7 | Mon 04:18:39 | -2050 | Mon 03:40:01 | -1299 | live cut +2318 s off |
| P7 | - | - | Mon 04:15:57 | -591 | no live trade |
| M7 | Mon 10:47:27 | -715 | Mon 10:38:52 | -604 | live cut +515 s off |
| K7 | Mon 18:45:37 | -615 | Mon 18:45:55 | -624 | live cut -18 s off |
| P7 | Mon 20:29:16 | -2405 | Mon 20:07:24 | -2231 | live cut +1312 s off |
| H7 | - | - | Mon 19:20:48 | -1373 | no live trade |
| K7 | Mon 22:36:58 | -805 | Mon 20:11:33 | -618 | live cut +8725 s off |
| K7 | - | - | Mon 20:38:14 | -644 | no live trade |
| H7 | - | - | Mon 20:38:46 | -1258 | no live trade |
| H7 | - | - | Mon 21:59:44 | -1261 | no live trade |
| K7 | - | - | Mon 22:22:33 | -653 | no live trade |
| H7 | - | - | Tue 01:39:55 | -1114 | no live trade |
| K7 | Tue 01:47:31 | -1030 | Tue 01:45:34 | -656 | live cut +117 s off |
| K7 | Tue 02:55:35 | -1660 | Tue 01:51:22 | -613 | live held (exit stop) |
| K7 | - | - | Tue 02:29:09 | -608 | no live trade |
| M7 | Tue 02:47:29 | -1615 | Tue 02:28:03 | -640 | live held (exit stop) |
| K7 | - | - | Tue 02:37:19 | -566 | no live trade |
| M7 | - | - | Tue 03:02:36 | -553 | no live trade |
| M7 | - | - | Tue 05:55:28 | -1229 | no live trade |
| M7 | - | - | Tue 07:14:25 | -1289 | no live trade |
| M7 | - | - | Tue 07:48:58 | -563 | no live trade |
| M7 | Tue 10:32:06 | -645 | Tue 10:27:42 | -575 | live cut +264 s off |
| H7 | - | - | Tue 10:45:04 | -585 | no live trade |
| M7 | - | - | Tue 11:18:33 | -601 | no live trade |
| K7 | Tue 11:39:37 | -595 | Tue 11:41:20 | -636 | live cut -103 s off |
| K7 | - | - | Tue 12:33:58 | -630 | no live trade |
| K7 | - | - | Tue 13:19:07 | -634 | no live trade |
| K7 | - | - | Tue 14:20:04 | -594 | no live trade |
| K7 | Tue 18:37:42 | -1780 | Tue 18:34:17 | -1218 | live cut +205 s off |
| P7 | Tue 18:37:42 | -6510 | Tue 18:34:15 | -4287 | live cut +207 s off |
| P7 | - | - | Tue 18:38:52 | -4557 | no live trade |
| P7 | Tue 19:04:10 | -1405 | Tue 19:03:59 | -2243 | live cut +11 s off |
| K7 | Tue 19:04:10 | -870 | Tue 19:03:25 | -644 | live cut +45 s off |
| K7 | Tue 22:02:00 | +2395 | Tue 21:50:08 | -1121 | live held (exit target) |
| H7 | - | - | Tue 21:46:41 | -2482 | no live trade |
| P7 | Tue 22:02:00 | +4800 | Tue 21:56:19 | -2229 | live held (exit target) |
| H7 | - | - | Tue 22:03:19 | -1444 | no live trade |
| P7 | Tue 22:16:23 | -2440 | Tue 22:16:41 | -2464 | live cut -18 s off |
| P7 | Tue 23:09:26 | -2700 | Tue 23:09:15 | -2458 | live cut +11 s off |
| P7 | Wed 01:24:11 | -4030 | Wed 00:59:22 | -3916 | live cut +1489 s off |
| P7 | - | - | Wed 01:19:12 | -3857 | no live trade |
| K7 | Wed 01:19:12 | -1365 | Wed 01:14:44 | -1216 | live cut +268 s off |
| K7 | Wed 02:21:31 | -655 | Wed 02:20:56 | -628 | live cut +35 s off |
| K7 | Wed 04:02:07 | -1095 | Wed 03:59:09 | -613 | live cut +178 s off |
| P7 | Wed 04:02:07 | -4105 | Wed 03:59:09 | -2473 | live cut +178 s off |
| M7 | Wed 04:02:07 | -1745 | Wed 04:01:24 | -1260 | live cut +43 s off |
| K7 | Wed 04:08:30 | -760 | Wed 04:08:13 | -624 | live cut +17 s off |
| P7 | Wed 07:25:04 | -90 | Wed 07:31:39 | -4638 | live held (exit lock) |
| P7 | - | - | Wed 08:05:26 | -4730 | no live trade |
| M7 | Wed 11:53:08 | -650 | Wed 12:02:12 | -634 | live cut -544 s off |
| K7 | Wed 14:17:26 | -585 | Wed 14:17:47 | -639 | live cut -21 s off |
| K7 | Wed 15:31:33 | -605 | Wed 15:35:42 | -561 | live cut -249 s off |
| P7 | Wed 19:57:29 | +8390 | Wed 19:30:12 | -3990 | live held (exit target) |
| K7 | Wed 19:30:26 | -650 | Wed 19:30:12 | -580 | live cut +14 s off |
| P7 | - | - | Wed 19:45:22 | -2209 | no live trade |
| K7 | Wed 22:53:11 | +1200 | Wed 22:19:09 | -555 | live held (exit target) |

### Missed cuts (live cut, engine held / no trade / timing off): 63

| book | live time ET | live $ | engine time | engine $ | reason |
|---|---|---|---|---|---|
| K7 | Mon 01:20:34 | -1900 | - | - | no engine trade |
| H7 | Mon 01:21:10 | -1370 | - | - | no engine trade |
| P7 | Mon 01:21:10 | -1405 | - | - | no engine trade |
| M7 | Mon 04:18:39 | -2420 | Mon 04:14:22 | -1655 | engine cut +257 s off |
| P7 | Mon 04:18:39 | -2050 | Mon 03:40:01 | -1299 | engine cut +2318 s off |
| X5 | Mon 04:06:50 | -1405 | - | - | no engine trade |
| X4 | Mon 07:06:08 | -1770 | Mon 07:35:54 | -3108 | engine held (exit stop) |
| K7 | Mon 08:36:49 | -640 | - | - | no engine trade |
| M7 | Mon 08:36:50 | -1775 | - | - | no engine trade |
| X3 | Mon 08:36:46 | -1685 | Mon 08:37:00 | -3108 | engine held (exit stop) |
| X3 | Mon 08:43:22 | -1225 | - | - | no engine trade |
| M7 | Mon 10:09:45 | -575 | - | - | no engine trade |
| P7 | Mon 10:09:42 | -2865 | - | - | no engine trade |
| M7 | Mon 10:47:27 | -715 | Mon 10:38:52 | -604 | engine cut +515 s off |
| H7 | Mon 10:38:19 | -600 | - | - | no engine trade |
| K7 | Mon 10:38:42 | -625 | - | - | no engine trade |
| K7 | Mon 12:56:12 | -1300 | - | - | no engine trade |
| K7 | Mon 18:45:37 | -615 | Mon 18:45:55 | -624 | engine cut -18 s off |
| P7 | Mon 20:29:16 | -2405 | Mon 20:07:24 | -2231 | engine cut +1312 s off |
| K7 | Mon 22:36:58 | -805 | Mon 20:11:33 | -618 | engine cut +8725 s off |
| A7 | Tue 00:42:01 | -805 | Tue 02:55:28 | -1254 | engine held (exit stop) |
| A7 | Tue 01:30:05 | -700 | - | - | no engine trade |
| K7 | Tue 01:47:31 | -1030 | Tue 01:45:34 | -656 | engine cut +117 s off |
| O7 | Tue 09:53:39 | -445 | - | - | no engine trade |
| P7 | Tue 10:23:25 | -2745 | - | - | no engine trade |
| M7 | Tue 10:32:06 | -645 | Tue 10:27:42 | -575 | engine cut +264 s off |
| K7 | Tue 11:39:37 | -595 | Tue 11:41:20 | -636 | engine cut -103 s off |
| K7 | Tue 18:37:42 | -1780 | Tue 18:34:17 | -1218 | engine cut +205 s off |
| A7 | Tue 18:31:21 | -565 | Tue 18:38:49 | -1254 | engine held (exit stop) |
| P7 | Tue 18:37:42 | -6510 | Tue 18:34:15 | -4287 | engine cut +207 s off |
| P7 | Tue 19:04:10 | -1405 | Tue 19:03:59 | -2243 | engine cut +11 s off |
| K7 | Tue 19:04:10 | -870 | Tue 19:03:25 | -644 | engine cut +45 s off |
| A7 | Tue 20:35:04 | -655 | Tue 20:40:41 | +1195 | engine held (exit target) |
| A7 | Tue 20:41:30 | -850 | - | - | no engine trade |
| A7 | Tue 21:30:20 | -700 | Tue 22:01:44 | +1195 | engine held (exit target) |
| A7 | Tue 22:16:47 | -635 | Tue 22:07:18 | +1195 | engine held (exit target) |
| P7 | Tue 22:16:23 | -2440 | Tue 22:16:41 | -2464 | engine cut -18 s off |
| P7 | Tue 23:09:26 | -2700 | Tue 23:09:15 | -2458 | engine cut +11 s off |
| A7 | Wed 00:15:23 | -680 | Wed 00:24:24 | +1195 | engine held (exit target) |
| A7 | Wed 00:21:54 | -670 | - | - | no engine trade |
| A7 | Wed 00:27:18 | -520 | - | - | no engine trade |
| A7 | Wed 01:24:11 | -885 | - | - | no engine trade |
| P7 | Wed 01:24:11 | -4030 | Wed 00:59:22 | -3916 | engine cut +1489 s off |
| K7 | Wed 01:19:12 | -1365 | Wed 01:14:44 | -1216 | engine cut +268 s off |
| K7 | Wed 02:21:31 | -655 | Wed 02:20:56 | -628 | engine cut +35 s off |
| K7 | Wed 04:02:07 | -1095 | Wed 03:59:09 | -613 | engine cut +178 s off |
| P7 | Wed 04:02:07 | -4105 | Wed 03:59:09 | -2473 | engine cut +178 s off |
| M7 | Wed 04:02:07 | -1745 | Wed 04:01:24 | -1260 | engine cut +43 s off |
| K7 | Wed 04:08:30 | -760 | Wed 04:08:13 | -624 | engine cut +17 s off |
| M7 | Wed 11:53:08 | -650 | Wed 12:02:12 | -634 | engine cut -544 s off |
| K7 | Wed 14:17:26 | -585 | Wed 14:17:47 | -639 | engine cut -21 s off |
| K7 | Wed 15:31:33 | -605 | Wed 15:35:42 | -561 | engine cut -249 s off |
| A7 | Wed 19:10:07 | -685 | Wed 19:13:18 | -1254 | engine held (exit stop) |
| K7 | Wed 19:30:26 | -650 | Wed 19:30:12 | -580 | engine cut +14 s off |
| A7 | Wed 19:44:04 | -685 | Wed 19:58:31 | +1195 | engine held (exit target) |
| A7 | Thu 01:13:43 | -890 | Thu 01:15:01 | -1005 | engine held (exit lock) |
| P7 | Thu 01:47:21 | -3640 | Thu 01:46:49 | -2477 | engine cut +32 s off |
| U7 | Thu 02:16:10 | -1320 | Thu 02:15:25 | -1248 | engine cut +45 s off |
| P7 | Thu 03:48:37 | -1295 | Thu 03:48:05 | -1248 | engine cut +32 s off |
| M7 | Thu 03:48:37 | -640 | Thu 03:48:06 | -594 | engine cut +31 s off |
## GATE 0 CHECK - VALID control live-as-engine (2026-11-06T18:59Z)

| gate | value | threshold | result |
|---|---|---|---|
| 1 trades matched / union | 1.000 | >= 0.85 | PASS |
| 2 net gap |engine-live|/|live| | 0.000 | <= 0.15 | PASS |
| 3 cuts matched / union of cuts | 1.000 | >= 0.85 | PASS |
| 4 cut dollars |engine cuts - live cuts| / |live cuts| | 0.000 | <= 0.10 | PASS |

**GATE 0: PASS (all four)**

Informational: trades engine 187 live 187 matched 187 (matched/live 1.000, matched/engine 1.000); net engine +104095 live +104095; exit-type agreement 1.000; maxDD engine 14490 live 14490 gap 0.000.
Cuts: live 92, engine 92, matched (same trade, cut, exit within 10 s) 92; recall 1.000, precision 1.000; live cut $ -140350, engine cut $ -140350; matched-pair cut $ delta (live-engine, pairs where either side cuts) +0 = 0.000 of |live cut $|.

### Cuts per book

| book | live cuts | engine cuts | matched cuts | live cut $ | engine cut $ | missed | false |
|---|---|---|---|---|---|---|---|
| A7 | 14 | 14 | 14 | -9925 | -9925 | 0 | 0 |
| H7 | 2 | 2 | 2 | -1970 | -1970 | 0 | 0 |
| K7 | 30 | 30 | 30 | -26355 | -26355 | 0 | 0 |
| M7 | 13 | 13 | 13 | -13615 | -13615 | 0 | 0 |
| O7 | 2 | 2 | 2 | -1140 | -1140 | 0 | 0 |
| P7 | 24 | 24 | 24 | -73500 | -73500 | 0 | 0 |
| U7 | 3 | 3 | 3 | -7760 | -7760 | 0 | 0 |
| X3 | 2 | 2 | 2 | -2910 | -2910 | 0 | 0 |
| X4 | 1 | 1 | 1 | -1770 | -1770 | 0 | 0 |
| X5 | 1 | 1 | 1 | -1405 | -1405 | 0 | 0 |

### False cuts (engine cut, live held / no live trade / timing off): 0


### Missed cuts (live cut, engine held / no trade / timing off): 0
