# BEST_BOOKS_NYAM - own-merit scorecard, NY AM session (W-BEST; refreshed 2026-11-19 18:12Z; first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 705 distinct cells scored (348 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 5 live-book rows; L6M $/wk > 0: 524; L6M and L3M > 0: 391; labels {'WEAK-BUT-POSITIVE': 385, 'BEST-AVAILABLE-NOT-PROVEN': 181, 'LEAD': 139}. Job errors: 0. Run 66 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## Formula
- Daily own P&L = sum of the book's own trades by exit date (ET+7h trading day), net of fees ($4.84 x lots), at **1 lot** (gross/lots - 4.84; new books are 1 lot already; live books are divided by their lots), zero-filled over the weekday calendar.
- **SCORE = L6M $/week divided by L6M own ulcer index** (ulcer = sqrt(mean(drawdown^2)) of the daily cumulative own P&L inside the window; $/week = total / (weekdays/5)). Ranking is by SCORE L6M descending (recent window first); L3M score and L3M rank are shown beside. Cells with L6M <= 0 rank last by construction. "(thin)" = under 1 trade per week.
- Own max drawdown = deepest peak-to-trough of the daily cumulative own P&L in the window; worst week = lowest weekly own sum; win% / avg win / avg loss per trade (net of fee).
- **Persistence** (target >= 0.58): share of non-overlapping 14-calendar-day windows with own P&L > 0; "L6M" = the 13 windows inside the L6M window; "all landed" = all landed months (L6M plus any landed prior years).
- **Prior years "not a disaster" vs the book's OWN recent level** (standing rule, 15-30% AMBER, >30% RED): worse% = max of (own L6M $/wk minus year $/wk) / L6M $/wk and (own L6M SCORE minus year SCORE) / L6M SCORE; shown beside the absolute $/wk and ulcer. Only defined when L6M $/wk > 0 (else blank / n/a). A year with a lower ulcer-adjusted score but a lower absolute level is flagged by the larger of the two.
- **Labels** (mine, from the standing list): CONFIRMED = L6M>0, L3M>0, persistence L6M >= 0.58, all 3 prior years landed and none RED, and screen p_ALL <= 0.05 (live books: no p needed); LEAD = same but prior years not all landed (or p not met), none RED; WEAK-BUT-POSITIVE = L6M > 0 but fails L3M, persistence or has a RED year; BEST-AVAILABLE-NOT-PROVEN = L6M <= 0. Controls (30 date-shifts) and the exit run are NOT in this table, so CONFIRMED here is not the final CONFIRMED of the ladder.
- **Calibration / luck (per cell when available):** screen p_L6M / p_ALL = share of same-bracket random-entry draws that did as well (n_draws in the CSV; 30 draws => finest 0.032), from the W-SHORT screen; block = the module block used for the family FDR. These are screen numbers (NOT FDR-corrected, "NOT calibrated" per the screen source). Family FDR (partial draw 1, autopilot/SURVIVOR_COUNTS.md CALIBRATION): see the lines below.

| NYAM | 763 / 1,915 (0.40) | 730 / 1,821 | 728 / 1814 | p_L6M (null / real families at threshold = FDR) | 87 / 223 = 39% | 39 / 66 = 59% | 14 / 20 = 70% | 5 / 8 = 62% |

## Where the live books rank (same table, same scoring; 710 rows in this session)

| rank | rank L3M | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 68 | 17 | LIVE_H7 | LIVE | JL3 | 0.272 | 0.746 | 339 | 546 | 1249 | 733 | -3149 | -1773 | 1.5 | 0.62 | 981 | -977 | 0.64 | 0.53 | 110 | 3142 | +87 | RED | -215 | 12674 | +163 | RED | 118 | 2700 | +84 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 156 | 210 | LIVE_O7 | LIVE | JL3 | 0.161 | 0.155 | 410 | 335 | 2548 | 2156 | -5970 | -2146 | 1.9 | 0.39 | 1640 | -680 | 0.64 | 0.66 | -150 | 8854 | +137 | RED | 743 | 1395 | -81 | GREEN | 525 | 2374 | -28 | GREEN | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 381 | 109 | LIVE_M7 | LIVE | JL3 | 0.047 | 0.301 | 338 | 843 | 7240 | 2806 | -14132 | -5751 | 9.2 | 0.42 | 1173 | -788 | 0.50 | 0.55 | -175 | 10942 | +152 | RED | 603 | 5798 | -78 | GREEN | 261 | 4989 | +23 | AMBER | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 400 | 413 | LIVE_P7 | LIVE | JL3 | 0.042 | 0.022 | 110 | 80 | 2646 | 3696 | -7712 | -3001 | 1.7 | 0.49 | 995 | -826 | 0.64 | 0.40 | 379 | 1091 | -244 | GREEN | -275 | 5952 | +349 | RED | -107 | 6270 | +197 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 694 | 635 | LIVE_K7 | LIVE | JL3 | -0.053 | -0.072 | -453 | -591 | 8572 | 8191 | -20010 | -5409 | 7.9 | 0.39 | 1165 | -827 | 0.43 | 0.49 | 27 | 11431 |  | n/a | 265 | 8709 |  | n/a | -53 | 7958 |  | n/a | not landed | BEST-AVAILABLE-NOT-PROVEN |  |  | 0 |

(live rows are JL3 own trades normalised to 1 lot; as-run base-lot numbers are in the CSV-side table below.)

| live book | L6M $/wk at 1 lot | L6M $/wk as run (base lots) | L3M $/wk as run | L6M ulcer as run | avg lots L6M |
|---|---|---|---|---|---|
| LIVE_H7 | 339 | 339 | 546 | 1249 | 1.00 |
| LIVE_O7 | 410 | 410 | 335 | 2548 | 1.00 |
| LIVE_M7 | 338 | 338 | 843 | 7240 | 1.00 |
| LIVE_P7 | 110 | 230 | 429 | 2299 | 1.22 |
| LIVE_K7 | -453 | -453 | -591 | 8572 | 1.00 |

## Top 50 NY AM cells by own-merit SCORE (live rows appear in the live table above with their rank in the same pool)

| rank | rank L3M | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 68 | L2b25565a | NEW | RK7 | 0.945 | 0.426 | 3034 | 1827 | 3210 | 4288 | -8639 | -6274 | 6.9 | 0.56 | 1977 | -1547 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.226 | 0.065 | 1 |
| 2 | 35 | Lb44a3e99 | NEW | RK7 | 0.907 | 0.552 | 1721 | 1287 | 1897 | 2332 | -7884 | -3298 | 8.1 | 0.59 | 1084 | -1064 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.032 | 1 |
| 3 | 76 | L678ebadd | NEW | RK7 | 0.771 | 0.394 | 2702 | 1857 | 3504 | 4711 | -10918 | -6169 | 5.2 | 0.60 | 2148 | -1911 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.097 | 0.129 | 1 |
| 4 | 30 | L6c84f416 | NEW | RK7 | 0.764 | 0.565 | 2081 | 1518 | 2723 | 2686 | -7529 | -7025 | 4.0 | 0.58 | 2243 | -1829 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.161 | 0.032 | 1 |
| 5 | 71 | L641a7c4d | NEW | RK7 | 0.710 | 0.422 | 2850 | 1973 | 4015 | 4672 | -12159 | -7369 | 7.3 | 0.58 | 1977 | -1810 | 0.86 | 0.86 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.194 | 0.032 | 0 |
| 6 | 42 | L2176f633 | NEW | RK7 | 0.680 | 0.536 | 2252 | 1751 | 3312 | 3268 | -12199 | -5049 | 6.4 | 0.56 | 1998 | -1765 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.226 | 0.065 | 0 |
| 7 | 64 | L39470318 | NEW | RK7 | 0.646 | 0.443 | 1531 | 1303 | 2369 | 2942 | -5983 | -5929 | 10.2 | 0.56 | 1160 | -1135 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.065 | 0.032 | 1 |
| 8 | 51 | Lc739d497 | NEW | RK7 | 0.610 | 0.478 | 2155 | 1883 | 3532 | 3942 | -11817 | -6672 | 14.6 | 0.55 | 1158 | -1085 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE |  |  | 2 |
| 9 | 36 | L4eba93d7 | NEW | RK7 | 0.575 | 0.550 | 2003 | 1849 | 3485 | 3359 | -10948 | -9539 | 5.0 | 0.57 | 2070 | -1803 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.097 | 0.005 | 0 |
| 10 | 123 | L2010fec9 | NEW | RK7 | 0.544 | 0.273 | 2075 | 1397 | 3816 | 5119 | -10773 | -5589 | 11.8 | 0.57 | 1136 | -1086 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.484 | 0.065 | 0 |
| 11 | 92 | L908c5381 | NEW | RK7 | 0.535 | 0.331 | 1713 | 1342 | 3200 | 4055 | -10804 | -9319 | 5.3 | 0.59 | 1890 | -1898 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.085 | 0.005 | 1 |
| 12 | 9 | Ld45733db | NEW | RK7 | 0.527 | 0.935 | 2430 | 2307 | 4610 | 2468 | -13312 | -3624 | 7.3 | 0.59 | 1951 | -1961 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 1 |
| 13 | 20 | Lc338b47b | NEW | RK7 | 0.500 | 0.672 | 2045 | 2303 | 4087 | 3430 | -11338 | -8714 | 5.3 | 0.59 | 2061 | -2061 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.106 | 0.002 | 0 |
| 14 | 14 | Lf82cdf44 | NEW | RK7 | 0.499 | 0.776 | 1484 | 2049 | 2974 | 2642 | -7817 | -6738 | 9.4 | 0.56 | 1141 | -1098 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.032 | 0.097 | 1 |
| 15 | 50 | L4fd10b76 | NEW | RK7 | 0.493 | 0.481 | 2173 | 1705 | 4407 | 3545 | -14123 | -7544 | 5.2 | 0.59 | 2118 | -1971 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 1 |
| 16 | 135 | Lfa1de080 | NEW | RK7 | 0.481 | 0.256 | 2240 | 1131 | 4654 | 4418 | -13690 | -10246 | 18.5 | 0.54 | 1132 | -1077 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 1 |
| 17 | 32 | Lddba3fab | NEW | RK7 | 0.467 | 0.560 | 1479 | 1385 | 3165 | 2472 | -8946 | -4412 | 10.5 | 0.53 | 1116 | -979 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.419 | 0.355 | 1 |
| 18 | 26 | L33bc9e87 | NEW | RK7 | 0.467 | 0.633 | 1942 | 1886 | 4159 | 2980 | -12283 | -7569 | 4.8 | 0.58 | 2083 | -1949 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.194 | 0.032 | 0 |
| 19 | 103 | L0e94fade | NEW | RK7 | 0.455 | 0.317 | 1582 | 1273 | 3474 | 4017 | -9139 | -9139 | 5.6 | 0.55 | 2000 | -1854 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.226 | 0.032 | 0 |
| 20 | 155 | L12e67af0 | NEW | ADD | 0.443 | 0.225 | 1420 | 974 | 3206 | 4335 | -11490 | -6923 | 10.2 | 0.55 | 1165 | -1108 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 21 | 110 | L59b66d32 | NEW | RK7 | 0.438 | 0.298 | 2279 | 1037 | 5200 | 3480 | -16656 | -7459 | 5.6 | 0.58 | 2109 | -1960 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 0 |
| 22 | 417 | Le0d40091 | NEW | RK7 | 0.426 | 0.020 | 1995 | 107 | 4683 | 5236 | -11552 | -6074 | 5.4 | 0.57 | 2097 | -1928 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.212 | 0.013 | 0 |
| 23 | 82 | Ld37dea46 | NEW | RK7 | 0.426 | 0.368 | 1497 | 1363 | 3518 | 3699 | -9589 | -3459 | 6.6 | 0.55 | 1942 | -1838 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.226 | 0.032 | 0 |
| 24 | 54 | L1b44d5f3 | NEW | RK7 | 0.419 | 0.473 | 1300 | 1275 | 3104 | 2695 | -8079 | -4699 | 10.0 | 0.55 | 1140 | -1122 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.118 | 0.004 | 1 |
| 25 | 5 | L34d66961 | NEW | RK7 | 0.416 | 1.302 | 2756 | 3522 | 6622 | 2706 | -19445 | -7400 | 23.2 | 0.55 | 1111 | -1079 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.419 | 0.097 | 0 |
| 26 | 187 | Ld5cdb3c6 | NEW | RK7 | 0.406 | 0.187 | 1080 | 651 | 2661 | 3491 | -6256 | -3922 | 8.7 | 0.55 | 1151 | -1111 | 0.86 | 0.86 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.226 | 0.032 | 1 |
| 27 | 104 | L06eab808 | NEW | RK7 | 0.403 | 0.317 | 1400 | 1273 | 3474 | 4017 | -9139 | -9139 | 5.6 | 0.55 | 1995 | -1862 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.290 | 0.032 | 1 |
| 28 | 43 | L21f079b6 | NEW | RK7 | 0.398 | 0.526 | 2040 | 2038 | 5126 | 3875 | -16312 | -9404 | 5.2 | 0.58 | 2073 | -1935 | 0.64 | 0.59 | 538 | 6041 | +78 | RED | 753 | 8658 | +78 | RED | 605 | 7048 | +78 | RED | RED | WEAK-BUT-POSITIVE | 0.097 | 0.032 | 7 |
| 29 | 143 | L7678a6c4 | NEW | RK7 | 0.378 | 0.242 | 2297 | 1266 | 6082 | 5220 | -17045 | -6094 | 11.3 | 0.56 | 1897 | -1930 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.228 | 0.005 | 0 |
| 30 | 86 | L0dc67ba7 | NEW | RK7 | 0.378 | 0.352 | 1529 | 961 | 4051 | 2733 | -12764 | -8014 | 4.4 | 0.57 | 2073 | -1893 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.323 | 0.032 | 1 |
| 31 | 102 | L9e98b767 | NEW | RK7 | 0.372 | 0.317 | 1730 | 1646 | 4646 | 5193 | -12286 | -6659 | 7.4 | 0.54 | 2112 | -1960 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.226 | 0.032 | 0 |
| 32 | 99 | Lfe9994ff | NEW | RK7 | 0.368 | 0.323 | 1895 | 1602 | 5149 | 4962 | -14149 | -14149 | 5.3 | 0.58 | 2077 | -2011 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.202 | 0.009 | 0 |
| 33 | 95 | L3bbe44f5 | NEW | RK7 | 0.357 | 0.326 | 924 | 933 | 2586 | 2863 | -6469 | -4745 | 2.6 | 0.59 | 1968 | -2017 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.355 | 0.032 | 0 |
| 34 | 78 | Lc9217645 | NEW | RK7 | 0.355 | 0.389 | 1822 | 1428 | 5129 | 3672 | -16847 | -7559 | 5.0 | 0.58 | 2072 | -1957 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.161 | 0.065 | 0 |
| 35 | 134 | L1ba33a2b | NEW | RK7 | 0.353 | 0.260 | 1199 | 876 | 3396 | 3365 | -7038 | -4684 | 6.7 | 0.57 | 1187 | -1133 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.484 | 0.290 | 0 |
| 36 | 120 | L04aaa969 | NEW | RK7 | 0.352 | 0.279 | 2028 | 1480 | 5753 | 5306 | -13673 | -9324 | 5.3 | 0.59 | 2068 | -2007 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.216 | 0.004 | 2 |
| 37 | 46 | L1af20032 | NEW | RK7 | 0.350 | 0.512 | 1342 | 1762 | 3833 | 3442 | -11464 | -6738 | 9.5 | 0.55 | 1143 | -1095 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.032 | 1 |
| 38 | 191 | L37c9625a | NEW | RK7 | 0.349 | 0.182 | 2257 | 1163 | 6473 | 6403 | -18893 | -13104 | 5.0 | 0.60 | 2077 | -1981 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.290 | 0.032 | 3 |
| 39 | 138 | Lb92ba8f9 | NEW | RK7 | 0.346 | 0.252 | 2222 | 1229 | 6431 | 4874 | -24768 | -13319 | 7.3 | 0.57 | 2008 | -1959 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 3 |
| 40 | 44 | L79cd626b | NEW | RK7 | 0.345 | 0.526 | 1298 | 1724 | 3758 | 3279 | -12338 | -8359 | 4.8 | 0.54 | 2098 | -1910 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.205 | 0.005 | 1 |
| 41 | 272 | L15a07e54 | NEW | RK7 | 0.345 | 0.095 | 1390 | 477 | 4030 | 5002 | -11248 | -9379 | 5.5 | 0.55 | 1960 | -1792 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.206 | 0.005 | 1 |
| 42 | 402 | L1d0ec711 | NEW | RK7 | 0.343 | 0.026 | 2374 | 251 | 6921 | 9676 | -18119 | -4634 | 5.7 | 0.61 | 1985 | -2043 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD |  |  | 1 |
| 43 | 122 | L5e9c702b | NEW | RK7 | 0.341 | 0.276 | 1709 | 1894 | 5010 | 6856 | -14121 | -8752 | 12.0 | 0.55 | 1147 | -1082 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.065 | 0.032 | 0 |
| 44 | 139 | L4604d23b | NEW | RK7 | 0.338 | 0.252 | 1808 | 1432 | 5347 | 5679 | -15578 | -13204 | 5.1 | 0.60 | 2012 | -2103 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.202 | 0.004 | 1 |
| 45 | 111 | Lfa8c13c0 | NEW | RK7 | 0.325 | 0.296 | 1729 | 1448 | 5312 | 4887 | -14747 | -9319 | 5.4 | 0.59 | 1875 | -1935 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.161 | 0.032 | 0 |
| 46 | 8 | L33d4983b | NEW | RK7 | 0.324 | 1.067 | 1370 | 2154 | 4230 | 2019 | -11473 | -8634 | 5.0 | 0.47 | 2148 | -1390 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.097 | 0.065 | 1 |
| 47 | 39 | Lb939a293 | NEW | RK7 | 0.324 | 0.546 | 870 | 1246 | 2686 | 2282 | -7686 | -4134 | 8.3 | 0.54 | 1104 | -1086 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.484 | 0.097 | 0 |
| 48 | 85 | Lb66c583e | NEW | RK7 | 0.321 | 0.354 | 1977 | 1653 | 6158 | 4666 | -15242 | -10674 | 5.2 | 0.59 | 2054 | -1973 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.290 | 0.032 | 1 |
| 49 | 144 | Ldcfbef89 | NEW | RK7 | 0.317 | 0.241 | 1406 | 1144 | 4436 | 4751 | -12752 | -5849 | 4.8 | 0.56 | 2003 | -1880 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.433 | 0.040 | 0 |
| 50 | 79 | L3a102d84 | NEW | RK7 | 0.312 | 0.388 | 1998 | 1299 | 6407 | 3348 | -20567 | -10762 | 16.6 | 0.53 | 1156 | -1069 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.065 | 0.032 | 1 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| K7 | -11868 | 207 | 323 | -11852 | -16905 / -5271 | 1686 | 14.2% | 202 |
| P7 | 6016 | 45 | 1304 | 5353 | 2289 / 9824 | 637 | 10.6% | 45 |
| H7 | 8886 | 39 | 1304 | 9196 | 4686 / 11026 | 830 | 9.3% | 39 |
| M7 | 8851 | 240 | 1302 | 9295 | 1365 / 15669 | 2127 | 24.0% | 240 |
| O7 | 10744 | 49 | 1320 | 10744 | 8949 / 12002 | 213 | 2.0% | 49 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 267 pairs over 223 cells): mean abs difference of its own L6M total $1525 = 23.2% of |total| (median 4.9%, 90th pct 23.1%); trade-count differences: mean abs 1.5 trades (primary mean 219).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_nyam.csv; all columns: best_books_nyam_full.csv; status file best_books_nyam.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
