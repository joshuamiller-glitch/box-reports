# BEST_BOOKS_ASIA - own-merit scorecard, Asia session (W-BEST; refreshed 2026-11-19 18:12Z; first looks as landed; data end 2026-10-31)

**Purpose (order 20261119_1806Z item 1):** every cell with a landed first look is scored BY ITSELF (its own trades, tag MF*, 1 lot), live books are ordinary rows from the JL3 baseline. D7 is not the judge here.

**Counts:** 1240 distinct cells scored (156 twin cells merged and counted once, autopilot/DEDUP_TWINS.md) + 5 live-book rows; L6M $/wk > 0: 765; L6M and L3M > 0: 585; labels {'WEAK-BUT-POSITIVE': 544, 'BEST-AVAILABLE-NOT-PROVEN': 475, 'LEAD': 219, 'CONFIRMED': 2}. Job errors: 0. Run 66 s.

**Source per cell:** REPLACE set (RA7 for Asia, RK7 for NY AM) when its L6M is landed, else the ADD set (column src). Windows: L6M = 2026-05..10 (26 wk), L3M = 2026-08..10 (13 wk); prior years 2023/2024/2025 only where all of the year's months (202511 excluded: tape hole) are landed for that set; otherwise blank / "not landed".

## Formula
- Daily own P&L = sum of the book's own trades by exit date (ET+7h trading day), net of fees ($4.84 x lots), at **1 lot** (gross/lots - 4.84; new books are 1 lot already; live books are divided by their lots), zero-filled over the weekday calendar.
- **SCORE = L6M $/week divided by L6M own ulcer index** (ulcer = sqrt(mean(drawdown^2)) of the daily cumulative own P&L inside the window; $/week = total / (weekdays/5)). Ranking is by SCORE L6M descending (recent window first); L3M score and L3M rank are shown beside. Cells with L6M <= 0 rank last by construction. "(thin)" = under 1 trade per week.
- Own max drawdown = deepest peak-to-trough of the daily cumulative own P&L in the window; worst week = lowest weekly own sum; win% / avg win / avg loss per trade (net of fee).
- **Persistence** (target >= 0.58): share of non-overlapping 14-calendar-day windows with own P&L > 0; "L6M" = the 13 windows inside the L6M window; "all landed" = all landed months (L6M plus any landed prior years).
- **Prior years "not a disaster" vs the book's OWN recent level** (standing rule, 15-30% AMBER, >30% RED): worse% = max of (own L6M $/wk minus year $/wk) / L6M $/wk and (own L6M SCORE minus year SCORE) / L6M SCORE; shown beside the absolute $/wk and ulcer. Only defined when L6M $/wk > 0 (else blank / n/a). A year with a lower ulcer-adjusted score but a lower absolute level is flagged by the larger of the two.
- **Labels** (mine, from the standing list): CONFIRMED = L6M>0, L3M>0, persistence L6M >= 0.58, all 3 prior years landed and none RED, and screen p_ALL <= 0.05 (live books: no p needed); LEAD = same but prior years not all landed (or p not met), none RED; WEAK-BUT-POSITIVE = L6M > 0 but fails L3M, persistence or has a RED year; BEST-AVAILABLE-NOT-PROVEN = L6M <= 0. Controls (30 date-shifts) and the exit run are NOT in this table, so CONFIRMED here is not the final CONFIRMED of the ladder.
- **Calibration / luck (per cell when available):** screen p_L6M / p_ALL = share of same-bracket random-entry draws that did as well (n_draws in the CSV; 30 draws => finest 0.032), from the W-SHORT screen; block = the module block used for the family FDR. These are screen numbers (NOT FDR-corrected, "NOT calibrated" per the screen source). Family FDR (partial draw 1, autopilot/SURVIVOR_COUNTS.md CALIBRATION): see the lines below.

| Asia | 380 / 963 (0.39) | 372 / 904 | 364 / 900 | p_L6M (null / real families at threshold = FDR) | 88 / 281 = 31% | 28 / 93 = 30% | 14 / 13 = 110% | 7 / 2 = 356% |

## Where the live books rank (same table, same scoring; 1245 rows in this session)

| rank | rank L3M | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 7 | LIVE_P7 | LIVE | JL3 | 2.321 | 0.999 | 3918 | 2132 | 1688 | 2134 | -5295 | -4359 | 22.8 | 0.52 | 980 | -706 | 0.86 | 0.66 | -12 | 9402 | +100 | RED | 174 | 6192 | +99 | RED | 831 | 2821 | +87 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 10 | 47 | LIVE_K7 | LIVE | JL3 | 0.511 | 0.519 | 2086 | 1863 | 4081 | 3587 | -11810 | -6339 | 30.7 | 0.45 | 1150 | -812 | 0.71 | 0.53 | -67 | 11976 | +103 | RED | 250 | 7191 | +93 | RED | 210 | 7273 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 55 | 411 | LIVE_U7 | LIVE | JL3 | 0.250 | 0.110 | 724 | 418 | 2892 | 3809 | -8510 | -3510 | 6.1 | 0.49 | 1156 | -879 | 0.64 | 0.61 | -105 | 4967 | +115 | RED | 257 | 7086 | +86 | RED | 210 | 5786 | +86 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 102 | 525 | LIVE_H7 | LIVE | JL3 | 0.182 | 0.066 | 735 | 251 | 4029 | 3781 | -8544 | -4368 | 5.3 | 0.52 | 1004 | -807 | 0.71 | 0.64 | 405 | 2683 | +45 | RED | 767 | 2395 | -4 | GREEN | 123 | 4840 | +86 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 123 | 997 | LIVE_A7 | LIVE | JL3 | 0.164 | -0.056 | 664 | -245 | 4053 | 4356 | -11290 | -6560 | 13.5 | 0.49 | 1193 | -1032 | 0.71 | 0.60 | 89 | 6771 | +92 | RED | 871 | 2520 | -31 | GREEN | 952 | 3258 | -43 | GREEN | RED | WEAK-BUT-POSITIVE |  |  | 0 |

(live rows are JL3 own trades normalised to 1 lot; as-run base-lot numbers are in the CSV-side table below.)

| live book | L6M $/wk at 1 lot | L6M $/wk as run (base lots) | L3M $/wk as run | L6M ulcer as run | avg lots L6M |
|---|---|---|---|---|---|
| LIVE_P7 | 3918 | 10048 | 7614 | 5232 | 2.53 |
| LIVE_K7 | 2086 | 2623 | 2583 | 7304 | 1.12 |
| LIVE_U7 | 724 | 1487 | 1318 | 6860 | 2.40 |
| LIVE_H7 | 735 | 1400 | 632 | 6129 | 1.84 |
| LIVE_A7 | 664 | 664 | -245 | 4053 | 1.00 |

## Top 50 Asia cells by own-merit SCORE (live rows appear in the live table above with their rank in the same pool)

| rank | rank L3M | cell | kind | src | SCORE L6M ($/wk / ulcer) | score L3M | L6M $/wk | L3M $/wk | L6M ulcer | L3M ulcer | L6M maxDD | L6M worst wk | trades/wk | win% | avg win | avg loss | pers 2wk L6M | pers 2wk all landed | 2023 $/wk | 2023 ulcer | 2023 worse% | 2023 | 2024 $/wk | 2024 ulcer | 2024 worse% | 2024 | 2025 $/wk | 2025 ulcer | 2025 worse% | 2025 | prior yrs | label | screen p L6M | screen p ALL | twins merged |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 7 | LIVE_P7 | LIVE | JL3 | 2.321 | 0.999 | 3918 | 2132 | 1688 | 2134 | -5295 | -4359 | 22.8 | 0.52 | 980 | -706 | 0.86 | 0.66 | -12 | 9402 | +100 | RED | 174 | 6192 | +99 | RED | 831 | 2821 | +87 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 2 | 63 | Ldcdb0b6e | NEW | RA7 | 0.768 | 0.449 | 2623 | 1859 | 3414 | 4145 | -11609 | -6262 | 20.8 | 0.54 | 1114 | -1035 | 0.86 | 0.86 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.205 | 0.011 | 0 |
| 3 | 181 | L86781ac0 | NEW | RA7 | 0.669 | 0.230 | 2448 | 1125 | 3659 | 4889 | -12409 | -6896 | 21.9 | 0.53 | 1088 | -1011 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.032 | 0 |
| 4 | 166 | Lc4e74264 | NEW | RA7 | 0.667 | 0.249 | 2294 | 993 | 3441 | 3986 | -8813 | -7594 | 28.5 | 0.53 | 1085 | -1053 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.032 | 0 |
| 5 | 23 | L7ea48296 | NEW | RA7 | 0.588 | 0.630 | 1951 | 2406 | 3315 | 3818 | -9193 | -5460 | 21.2 | 0.53 | 1093 | -1016 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.164 | 0.025 | 0 |
| 6 | 397 | L548972b6 | NEW | RA7 | 0.570 | 0.117 | 1768 | 460 | 3100 | 3939 | -10091 | -4596 | 18.0 | 0.54 | 1090 | -1043 | 0.64 | 0.54 | 268 | 3565 | +87 | RED | 182 | 4291 | +93 | RED | 186 | 7164 | +95 | RED | RED | WEAK-BUT-POSITIVE | 0.290 | 0.065 | 0 |
| 7 | 171 | Lbe8a8e54 | NEW | RA7 | 0.551 | 0.243 | 1948 | 965 | 3532 | 3967 | -8853 | -7529 | 28.8 | 0.53 | 1083 | -1058 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.097 | 0.032 | 0 |
| 8 | 1 | L7c368a4f | NEW | RA7 | 0.551 | 1.707 | 2433 | 2712 | 4414 | 1589 | -12119 | -8599 | 26.2 | 0.53 | 1082 | -1041 | 0.86 | 0.61 | 232 | 3402 | +90 | RED | 671 | 4077 | +72 | RED | 587 | 5907 | +82 | RED | RED | WEAK-BUT-POSITIVE | 0.097 | 0.032 | 0 |
| 9 | 243 | L224050e7 | NEW | RA7 | 0.517 | 0.186 | 2412 | 872 | 4666 | 4677 | -11874 | -9598 | 10.8 | 0.55 | 1722 | -1605 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.355 | 0.032 | 0 |
| 10 | 47 | LIVE_K7 | LIVE | JL3 | 0.511 | 0.519 | 2086 | 1863 | 4081 | 3587 | -11810 | -6339 | 30.7 | 0.45 | 1150 | -812 | 0.71 | 0.53 | -67 | 11976 | +103 | RED | 250 | 7191 | +93 | RED | 210 | 7273 | +94 | RED | RED | WEAK-BUT-POSITIVE |  |  | 0 |
| 11 | 72 | Lfb608c7b | NEW | RA7 | 0.501 | 0.426 | 2116 | 2120 | 4221 | 4980 | -11188 | -5501 | 28.7 | 0.52 | 1095 | -1044 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.161 | 0.032 | 0 |
| 12 | 102 | L15f14deb | NEW | RA7 | 0.465 | 0.349 | 1565 | 1176 | 3367 | 3370 | -10247 | -7692 | 23.0 | 0.52 | 1092 | -1033 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.104 | 0.005 | 1 |
| 13 | 27 | Lda55d973 | NEW | RA7 | 0.462 | 0.599 | 1733 | 1691 | 3751 | 2820 | -9470 | -4931 | 22.7 | 0.53 | 1097 | -1052 | 0.64 | 0.54 | 199 | 4274 | +90 | RED | 137 | 6685 | +96 | RED | 259 | 14212 | +96 | RED | RED | WEAK-BUT-POSITIVE | 0.226 | 0.065 | 0 |
| 14 | 2 | L1edb9fab | NEW | RA7 | 0.450 | 1.550 | 2156 | 2568 | 4789 | 1657 | -12819 | -8599 | 26.3 | 0.53 | 1081 | -1047 | 0.86 | 0.62 | 232 | 3374 | +89 | RED | 661 | 4294 | +69 | RED | 717 | 5732 | +72 | RED | RED | WEAK-BUT-POSITIVE | 0.161 | 0.032 | 0 |
| 15 | 202 | Ledfbf4d2 | NEW | RA7 | 0.436 | 0.219 | 2138 | 1203 | 4902 | 5484 | -14074 | -7477 | 22.3 | 0.53 | 1103 | -1051 | 0.79 | 0.65 | 320 | 4254 | +85 | RED | 409 | 8629 | +89 | RED | 439 | 8696 | +88 | RED | RED | WEAK-BUT-POSITIVE | 0.209 | 0.035 | 0 |
| 16 | 15 | L40bde9ea | NEW | RA7 | 0.424 | 0.761 | 1403 | 1910 | 3310 | 2511 | -8398 | -3762 | 17.2 | 0.53 | 1085 | -1060 | 0.79 | 0.64 | 271 | 3669 | +83 | RED | 402 | 5001 | +81 | RED | 697 | 8158 | +80 | RED | RED | WEAK-BUT-POSITIVE | 0.203 | 0.014 | 0 |
| 17 | 114 | Leee81e35 | NEW | RA7 | 0.410 | 0.324 | 2066 | 1466 | 5043 | 4523 | -15812 | -5832 | 10.6 | 0.56 | 1656 | -1634 | 0.86 | 0.56 | 345 | 1672 | +83 | RED | -44 | 10454 | +102 | RED | -244 | 12244 | +112 | RED | RED | WEAK-BUT-POSITIVE | 0.279 | 0.090 | 0 |
| 18 | 385 | Lcae177ba | NEW | RA7 | 0.405 | 0.123 | 1753 | 696 | 4330 | 5637 | -9864 | -5301 | 17.3 | 0.53 | 1093 | -1011 | 0.79 | 0.62 | 157 | 3643 | +91 | RED | 351 | 5587 | +84 | RED | 632 | 5706 | +73 | RED | RED | WEAK-BUT-POSITIVE | 0.129 | 0.065 | 0 |
| 19 | 141 | Lc754cf58 | NEW | RA7 | 0.402 | 0.287 | 1630 | 1176 | 4052 | 4091 | -10188 | -6593 | 10.8 | 0.54 | 1691 | -1649 | 0.93 | 0.93 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.194 | 0.032 | 0 |
| 20 | 204 | Lcb276f27 | NEW | RA7 | 0.381 | 0.218 | 1929 | 1107 | 5057 | 5074 | -12858 | -7278 | 13.3 | 0.52 | 1499 | -1314 | 0.64 | 0.62 | 468 | 1188 | +76 | RED | 409 | 4236 | +79 | RED | 387 | 12721 | +92 | RED | RED | WEAK-BUT-POSITIVE | 0.134 | 0.005 | 0 |
| 21 | 59 | L973b5c8a | NEW | RA7 | 0.371 | 0.466 | 1421 | 1509 | 3825 | 3236 | -12635 | -6217 | 17.9 | 0.54 | 1059 | -1054 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.161 | 0.032 | 1 |
| 22 | 3 | L1756b913 | NEW | ADD | 0.369 | 1.351 | 2020 | 3102 | 5480 | 2295 | -15767 | -4911 | 21.9 | 0.53 | 1068 | -988 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.084 | 0.001 | 0 |
| 23 | 185 | L29b1bc3f | NEW | RA7 | 0.361 | 0.228 | 1393 | 1020 | 3856 | 4465 | -11560 | -3767 | 17.7 | 0.54 | 1067 | -1061 | 0.64 | 0.60 | 55 | 4823 | +97 | RED | 248 | 8652 | +92 | RED | 235 | 9700 | +93 | RED | RED | WEAK-BUT-POSITIVE | 0.290 | 0.032 | 0 |
| 24 | 214 | M7423c0d9 | NEW | RA7 | 0.359 | 0.209 | 1071 | 687 | 2988 | 3290 | -8103 | -3664 | 6.7 | 0.53 | 1464 | -1285 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.219 | 0.035 | 0 |
| 25 | 256 | La5b5d03a | NEW | RA7 | 0.349 | 0.179 | 1915 | 1060 | 5484 | 5918 | -13048 | -7283 | 13.3 | 0.52 | 1505 | -1313 | 0.64 | 0.64 | 484 | 1217 | +75 | RED | 442 | 3718 | +77 | RED | 343 | 12523 | +92 | RED | RED | WEAK-BUT-POSITIVE | 0.113 | 0.002 | 0 |
| 26 | 446 | L6cff0af0 | NEW | RA7 | 0.348 | 0.095 | 1502 | 457 | 4312 | 4796 | -14725 | -11155 | 21.4 | 0.51 | 1098 | -1010 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.065 | 0.032 | 0 |
| 27 | 28 | L2ccc12bf | NEW | RA7 | 0.341 | 0.598 | 1283 | 1714 | 3761 | 2867 | -10118 | -8396 | 17.4 | 0.53 | 1090 | -1056 | 0.86 | 0.86 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.065 | 0.032 | 0 |
| 28 | 98 | Lb68a132d | NEW | RA7 | 0.340 | 0.368 | 1125 | 1173 | 3310 | 3190 | -8621 | -3723 | 12.7 | 0.53 | 1085 | -1042 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.161 | 0.032 | 0 |
| 29 | 89 | Lbe5ac95b | NEW | RA7 | 0.333 | 0.389 | 1455 | 1821 | 4370 | 4677 | -10568 | -4592 | 16.6 | 0.53 | 1087 | -1049 | 0.79 | 0.64 | 222 | 3029 | +85 | RED | 434 | 5913 | +78 | RED | 150 | 8647 | +95 | RED | RED | WEAK-BUT-POSITIVE | 0.387 | 0.226 | 0 |
| 30 | 176 | L59536e17 | NEW | RA7 | 0.333 | 0.234 | 2171 | 1057 | 6525 | 4523 | -19587 | -6678 | 10.5 | 0.53 | 1674 | -1417 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.125 | 0.001 | 0 |
| 31 | 151 | L81e89115 | NEW | RA7 | 0.321 | 0.275 | 1337 | 1234 | 4169 | 4483 | -14342 | -5038 | 8.4 | 0.54 | 1632 | -1576 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.355 | 0.032 | 0 |
| 32 | 100 | L358e61be | NEW | RA7 | 0.321 | 0.351 | 1817 | 1798 | 5669 | 5127 | -16122 | -11729 | 28.8 | 0.52 | 1101 | -1043 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.032 | 0 |
| 33 | 4 | Lc44703e7 | NEW | RA7 | 0.316 | 1.271 | 2016 | 2968 | 6388 | 2335 | -15197 | -6503 | 15.8 | 0.54 | 1077 | -965 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.154 | 0.005 | 0 |
| 34 | 279 | L4d206c8c | NEW | RA7 | 0.311 | 0.167 | 1557 | 935 | 5011 | 5611 | -11017 | -7174 | 8.6 | 0.51 | 1790 | -1517 | 0.64 | 0.62 | 133 | 3808 | +91 | RED | 507 | 7406 | +78 | RED | 470 | 6602 | +77 | RED | RED | WEAK-BUT-POSITIVE | 0.355 | 0.032 | 0 |
| 35 | 567 | L7a477a4a | NEW | RA7 | 0.303 | 0.052 | 2051 | 340 | 6760 | 6559 | -18851 | -12626 | 23.8 | 0.53 | 1093 | -1033 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.303 | 0.025 | 0 |
| 36 | 76 | L3ee2d289 | NEW | RA7 | 0.299 | 0.412 | 1795 | 2235 | 6007 | 5430 | -16578 | -9432 | 17.2 | 0.53 | 1104 | -1028 | 0.64 | 0.55 | 122 | 5015 | +93 | RED | 325 | 5507 | +82 | RED | 601 | 10129 | +80 | RED | RED | WEAK-BUT-POSITIVE | 0.290 | 0.032 | 0 |
| 37 | 56 | M3f6f752c | NEW | RA7 | 0.296 | 0.469 | 1032 | 1144 | 3492 | 2441 | -9985 | -3933 | 10.9 | 0.53 | 1068 | -1017 | 0.79 | 0.79 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.097 | 0.097 | 0 |
| 38 | 37 | L5c9e11b3 | NEW | RA7 | 0.295 | 0.561 | 1314 | 1889 | 4457 | 3365 | -12045 | -8360 | 19.8 | 0.52 | 1108 | -1068 | 0.57 | 0.65 | 472 | 1638 | +64 | RED | 593 | 4258 | +55 | RED | 819 | 9219 | +70 | RED | RED | WEAK-BUT-POSITIVE | 0.258 | 0.065 | 0 |
| 39 | 111 | Md2a3a7d6 | NEW | RA7 | 0.295 | 0.328 | 783 | 714 | 2659 | 2176 | -6341 | -5018 | 9.7 | 0.52 | 1059 | -969 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.129 | 0.065 | 0 |
| 40 | 150 | La4bf1d85 | NEW | RA7 | 0.293 | 0.276 | 1709 | 1035 | 5834 | 3753 | -20512 | -6228 | 12.3 | 0.53 | 1532 | -1439 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.199 | 0.010 | 1 |
| 41 | 108 | L2d89766e | NEW | RA7 | 0.291 | 0.338 | 1743 | 1864 | 5998 | 5507 | -17505 | -14766 | 17.6 | 0.53 | 1121 | -1035 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.226 | 0.032 | 0 |
| 42 | 414 | Lb2f695b9 | NEW | RA7 | 0.287 | 0.109 | 1664 | 535 | 5796 | 4927 | -15855 | -4668 | 10.0 | 0.52 | 1803 | -1627 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.353 | 0.025 | 0 |
| 43 | 478 | L8c18be1c | NEW | RA7 | 0.281 | 0.083 | 858 | 304 | 3052 | 3667 | -7552 | -6533 | 11.8 | 0.52 | 1102 | -1047 | 0.43 | 0.43 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.194 | 0.032 | 0 |
| 44 | 138 | Lb0bab78f | NEW | RA7 | 0.279 | 0.296 | 732 | 657 | 2625 | 2217 | -7330 | -4818 | 8.0 | 0.55 | 997 | -1005 | 0.64 | 0.64 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.387 | 0.032 | 0 |
| 45 | 250 | Le50c8ff3 | NEW | RA7 | 0.275 | 0.182 | 1539 | 1055 | 5588 | 5792 | -15835 | -11126 | 22.7 | 0.53 | 1070 | -1049 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.129 | 0.032 | 0 |
| 46 | 73 | Mac97d189 | NEW | RA7 | 0.270 | 0.425 | 1106 | 1054 | 4100 | 2477 | -13627 | -4934 | 7.0 | 0.54 | 1590 | -1492 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.258 | 0.032 | 0 |
| 47 | 433 | L85abf719 | NEW | RA7 | 0.266 | 0.100 | 776 | 305 | 2916 | 3051 | -7458 | -5708 | 11.5 | 0.52 | 1099 | -1042 | 0.36 | 0.36 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.194 | 0.032 | 0 |
| 48 | 97 | L54f4c7df | NEW | RA7 | 0.265 | 0.371 | 1685 | 1727 | 6358 | 4654 | -17710 | -10180 | 27.2 | 0.52 | 1098 | -1050 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.105 | 0.003 | 0 |
| 49 | 137 | L7c4a36ab | NEW | RA7 | 0.265 | 0.296 | 1141 | 997 | 4311 | 3363 | -10384 | -8378 | 8.2 | 0.50 | 1709 | -1433 | 0.57 | 0.57 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | WEAK-BUT-POSITIVE | 0.194 | 0.032 | 0 |
| 50 | 210 | L252e1154 | NEW | RA7 | 0.263 | 0.214 | 954 | 873 | 3621 | 4078 | -7631 | -5042 | 13.3 | 0.53 | 1065 | -1062 | 0.71 | 0.71 |  |  |  | n/a |  |  |  | n/a |  |  |  | n/a | not landed | LEAD | 0.419 | 0.419 | 0 |

## Caveat: account-layer effect on a book's own stream (L6M own total, p484 as run, base lots)

Method: the same live book / the same new cell in different stacks. Stacks (excluding stacks that REPLACE that very book) = every first-look set of this session's ladder landed in L6M (each is JL3 plus one new book, ADD or REPLACE of one live book, other live books/layers unchanged) versus TL3_EV_JL3.

| live book (session) | JL3 own L6M total $ | JL3 trades | n stacks | median over stacks $ | min / max $ | mean abs diff vs JL3 $ | mean abs diff as % of |JL3 total| | median trade count |
|---|---|---|---|---|---|---|---|---|
| A7 | 17396 | 354 | 1004 | 17396 | 6717 / 29503 | 1988 | 11.4% | 353 |
| K7 | 68732 | 805 | 2290 | 65685 | 52359 / 84114 | 4219 | 6.1% | 798 |
| P7 | 263246 | 597 | 2294 | 260602 | 223930 / 272053 | 4592 | 1.7% | 596 |
| H7 | 36684 | 140 | 2295 | 36071 | 27700 / 42819 | 1308 | 3.6% | 140 |
| U7 | 38955 | 159 | 2295 | 39589 | 24339 / 51542 | 1830 | 4.7% | 158 |

The NEW book itself, primary set vs another stack of the same cell (e.g. RA7 vs ADD vs RK7/RP7/RH7/RU7, 970 pairs over 683 cells): mean abs difference of its own L6M total $6806 = 135.1% of |total| (median 32.9%, 90th pct 170.9%); trade-count differences: mean abs 11.6 trades (primary mean 340).

Reading: the day halt / stack cuts / re-entry rules mean a book's own trades differ slightly between stacks. Rankings use the primary (REPLACE) stack for every cell, so the effect is a common-mode offset in the ordering; it is bounded by the percentages above.

## Files
- CSV contract (rank, cell, session, score, l6m_wk, l6m_ulcer, l3m_wk, persistence, kind): /mnt/l2/l2vast/_split/best_books_asia.csv; all columns: best_books_asia_full.csv; status file best_books_asia.status
- Code: code/th_best/best_books.py (cron every 30 min, flock, nice 10, read-only on result trees; own cache /mnt/l2/l2vast/_best/cache)
