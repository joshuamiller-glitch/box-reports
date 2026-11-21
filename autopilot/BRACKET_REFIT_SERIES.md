# BRACKET REFIT SERIES (order 1558Z; Josh: "if a bracket size works better recently, we should use that" / "is it a disaster?" / "that is why we re-fit")

Written 2026-11-21 15:58 UTC by W-BRKT from the landed per-month series (no engine run, no gate changed). 43 pool books, 17 shapes each (the own bracket + 16). ROLLING REFIT = every 14 days (periods from 2023-10-02) pick, on the trailing window (6 months; 3 months beside), the shape with the highest $/wk at EQUAL ULCER to the own bracket (must be > 0 and > the own bracket's; else keep the own bracket), trade it for the next 14 days at that equal-risk scale (shape daily P&L x ulcer_own / ulcer_shape of the trailing window). No drawdown / worst-week guard, no walk-forward gate in this series. Columns: EQ = refit $/wk scaled to the own bracket's ulcer in the SAME window (refit mean x own ulcer / refit ulcer), OWN = fixed own bracket $/wk; windows L6M, L3M, 2023, 2024, 2025, whole span (2023-10-02..2026-10-31).

## Table 1 (6-month trailing pick): refit vs own, equal risk

| book | own | L6M EQ / OWN | L3M EQ / OWN | 2023 EQ / OWN | 2024 EQ / OWN | 2025 EQ / OWN | ALL EQ / OWN | periods refit won / differed | shape changes | picks (top) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| AS_L018fb0c0 | S15U | 978 / 617 | 293 / 1606 | 516 / 324 | 55 / 510 | 196 / 184 | 296 / 451 | 39 / 77 | 27 | F40_80 x16, S8U x11, F60_120 x10, P90 x9 |
| AS_L130cb48e | P60 | -96 / 1465 | 1141 / 946 | 9 / 196 | 14 / 115 | 28 / 104 | 29 / 349 | 33 / 65 | 27 | F40_80 x21, P60 x15, P120 x8, F120_60 x5 |
| AS_L15f14deb | P60 | 1216 / 1482 | 742 / 1208 | 531 / 508 | -288 / 80 | 247 / 795 | 127 / 859 | 19 / 52 | 23 | P60 x28, F40_80 x14, S8U x13, P30 x8 |
| AS_L1756b913 | P60 | 1581 / 2107 | 2782 / 3272 | 249 / 1189 | 260 / 236 | -69 / 456 | 459 / 935 | 42 / 68 | 19 | F60_120 x26, F40_80 x25, P60 x12, P30 x9 |
| AS_L1edb9fab | P60 | 3217 / 2167 | 1065 / 2289 | 859 / 717 | 456 / 643 | 457 / 645 | 1058 / 960 | 38 / 69 | 25 | P45 x26, P60 x11, F60_120 x10, F40_80 x10 |
| AS_L29b1bc3f | P60 | 734 / 2028 | 874 / 2095 | 717 / 913 | 621 / 325 | -22 / 520 | 353 / 831 | 30 / 66 | 24 | P60 x14, S8U x13, P30 x11, A15U30U x9 |
| AS_L385f4f2e | P60 | 8 / 476 | 27 / 457 | 507 / 576 | 37 / 189 | 433 / 502 | 197 / 366 | 41 / 74 | 24 | P30 x29, F60_120 x12, F80_40 x9, F40_80 x9 |
| AS_L385f4f2eJ502 | P60 | 483 / 2157 | 542 / 2514 | -88 / -89 | 475 / 240 | 164 / 179 | 475 / 514 | 46 / 68 | 15 | P30 x32, P45 x17, F120_60 x11, P60 x11 |
| AS_L3a2258bd | S15U | 199 / 1760 | -359 / 1346 | 175 / 348 | 262 / 584 | -32 / 37 | 352 / 539 | 45 / 80 | 24 | P30 x28, P60 x13, P45 x9, F40_80 x7 |
| AS_L3faac8df | P60 | 2732 / 1314 | 835 / 1186 | 284 / 144 | 152 / 44 | 282 / 489 | 1242 / 344 | 60 / 80 | 14 | F40_80 x40, F60_120 x14, S15U x9, P45 x9 |
| AS_L40bde9ea | P60 | 1358 / 937 | 1902 / 1664 | 818 / 733 | 808 / 381 | 70 / 835 | 387 / 725 | 42 / 73 | 27 | P45 x16, A15U30U x12, S8U x10, P120 x10 |
| AS_L47a9c81c | P60 | 39 / 851 | -388 / 202 | 466 / 1141 | 554 / 57 | 498 / 406 | 492 / 524 | 42 / 74 | 22 | S8U x17, P30 x12, A10U20U x12, F40_80 x10 |
| AS_L578701ed | P60 | 680 / 2207 | 114 / 614 | 417 / 929 | 177 / 40 | 36 / 530 | 369 / 779 | 31 / 68 | 30 | F40_80 x18, S8U x14, P45 x13, P60 x12 |
| AS_L5dee2059 | A10U20U | 55 / 1142 | -269 / 1986 | 776 / 724 | 234 / 463 | 949 / 598 | 455 / 690 | 35 / 58 | 28 | A10U20U x22, P45 x16, P30 x13, P60 x11 |
| AS_L65a26c02 | P60 | -115 / 1666 | 290 / 2028 | 940 / 879 | 377 / 440 | 520 / 1313 | 188 / 958 | 29 / 68 | 28 | P45 x17, P60 x12, S8U x10, P90 x10 |
| AS_L7c368a4f | P60 | 2821 / 2456 | 1260 / 2434 | 859 / 717 | 336 / 654 | 292 / 528 | 589 / 977 | 33 / 61 | 26 | P60 x19, P45 x18, F40_80 x15, P30 x7 |
| AS_L7ea48296 | P60 | 129 / 1927 | 1429 / 2122 | 1071 / 1158 | 796 / 711 | 787 / 556 | 700 / 902 | 43 / 72 | 14 | S8U x29, P45 x18, A10U20U x9, P60 x8 |
| AS_L7f41b347 | P60 | 172 / 2095 | -300 / 1738 | 923 / 1209 | 249 / 546 | 175 / 463 | 578 / 738 | 40 / 72 | 19 | P45 x24, F40_80 x12, S45U x9, P60 x8 |
| AS_L92a90948 | P60 | 16 / 613 | 490 / 1141 | 308 / 294 | 200 / 280 | 868 / 485 | 157 / 374 | 38 / 67 | 22 | P90 x19, P45 x15, F120_60 x14, P60 x13 |
| AS_L973b5c8a | P60 | 1375 / 1211 | 166 / 1310 | 873 / 1093 | 450 / 359 | 283 / 771 | 652 / 793 | 42 / 72 | 23 | P30 x33, P90 x14, F40_80 x8, F60_120 x8 |
| AS_L9aa7805c | P60 | 80 / 1691 | -110 / 1635 | 1099 / 607 | 431 / 318 | 137 / 896 | 208 / 761 | 39 / 74 | 32 | F60_120 x18, P30 x17, F40_80 x12, F80_40 x7 |
| AS_L9e4754b9 | P60 | 124 / 1218 | 2096 / 1118 | 1128 / 1064 | 284 / 257 | 322 / 196 | 251 / 523 | 42 / 76 | 17 | F40_80 x19, A10U20U x13, F120_60 x10, P120 x9 |
| AS_La010c3eb | P60 | 8 / 861 | -147 / 906 | 631 / 564 | 106 / 414 | -268 / 90 | 163 / 420 | 33 / 64 | 24 | P30 x18, P60 x16, F80_40 x10, F120_60 x10 |
| AS_La776664b | P60 | -154 / 576 | -496 / 579 | 956 / 859 | 184 / 420 | 35 / 340 | 86 / 539 | 35 / 77 | 25 | A20U10U x19, A10U20U x9, F80_40 x9, S8U x9 |
| AS_Lb68a132d | P60 | 297 / 1090 | 311 / 1273 | 440 / 915 | 287 / 510 | 431 / 900 | 318 / 818 | 36 / 77 | 26 | P30 x26, F40_80 x14, F60_120 x11, S8U x10 |
| AS_Lc754cf58 | A20U10U | 361 / 1368 | -349 / 431 | 948 / 862 | 789 / 520 | 128 / 133 | 531 / 694 | 36 / 68 | 30 | A10U20U x16, A20U10U x12, P30 x11, S8U x8 |
| AS_Lcbc8a7ec | P60 | 2011 / 1880 | 341 / 2105 | 870 / 953 | 55 / 239 | 162 / 550 | 517 / 627 | 47 / 79 | 23 | P45 x20, F40_80 x9, A15U30U x8, S8U x7 |
| AS_Lec335094 | P60 | 25 / 934 | 19 / 1005 | 798 / 828 | 94 / 246 | 17 / 627 | 127 / 597 | 40 / 80 | 19 | F40_80 x15, P30 x14, F60_120 x11, P90 x10 |
| AS_Lff52ec0c | P60 | 282 / 1882 | -240 / 1357 | 919 / 1207 | 285 / 549 | 406 / 569 | 711 / 815 | 44 / 74 | 12 | P45 x28, F40_80 x11, S45U x9, P90 x7 |
| AS_M7423c0d9 | S8U | 642 / 1055 | 140 / 860 | -153 / -153 | 231 / 74 | 442 / 458 | 330 / 423 | 34 / 62 | 28 | S8U x18, P90 x13, F40_80 x12, A10U20U x12 |
| AS_M7ea48296 | P60 | 288 / 429 | 802 / 862 | 346 / 299 | 449 / 644 | 112 / 318 | 210 / 491 | 41 / 73 | 23 | S8U x21, F80_40 x11, P45 x10, S15U x7 |
| AS_M817db5df | P60 | 173 / 512 | 257 / 325 | 29 / 164 | 395 / 400 | 184 / 417 | 91 / 370 | 38 / 76 | 39 | A15U30U x10, P30 x10, F60_120 x8, F40_80 x8 |
| AS_M86781ac0 | P60 | 461 / 734 | 204 / 439 | 332 / 204 | 424 / 426 | 139 / 323 | 209 / 420 | 46 / 79 | 29 | F40_80 x23, S15U x10, A10U20U x9, A20U10U x7 |
| AS_Ma010c3eb | P60 | -10 / 705 | 130 / 706 | 68 / 139 | 615 / 254 | 150 / 458 | 220 / 459 | 32 / 70 | 28 | P120 x14, F120_60 x11, P60 x10, P45 x9 |
| AS_Mcae177ba | P60 | -101 / 341 | -132 / 22 | 242 / 208 | 878 / 503 | -22 / 182 | 133 / 353 | 37 / 78 | 28 | F60_120 x20, A20U10U x11, P45 x10, F120_60 x9 |
| NY_B57507767 | S15U | -219 / 1556 | 228 / 1587 | 534 / 897 | 1979 / 862 | 1610 / 1254 | 539 / 959 | 39 / 70 | 27 | P45 x27, F80_40 x15, F60_120 x12, S15U x10 |
| NY_B6f77f23d | A15U30U | 442 / 1393 | -382 / 1214 | 262 / 839 | 1317 / 941 | 2370 / 1271 | 446 / 1042 | 38 / 68 | 22 | F40_80 x22, A15U30U x12, P90 x10, P60 x10 |
| NY_B7bfd33b7 | P60 | 1120 / 1440 | 239 / 1270 | 58 / 30 | -378 / 20 | 238 / 527 | 254 / 328 | 31 / 70 | 24 | F60_120 x13, P45 x10, P60 x10, F120_60 x10 |
| NY_L05350e98 | S15U | 125 / 989 | -177 / 1043 | 516 / 833 | 307 / 715 | -25 / 155 | 259 / 650 | 36 / 80 | 25 | S8U x20, F60_120 x14, F120_60 x12, P90 x12 |
| NY_L488784d8 | P60 | 179 / 915 | 1458 / 838 | 413 / 690 | 389 / 382 | 2679 / 623 | 905 / 601 | 43 / 80 | 17 | F40_80 x22, F80_40 x14, P30 x10, F120_60 x8 |
| NY_L6547965c | P60 | -2 / 1275 | -172 / 588 | 468 / 2465 | 2634 / 959 | 163 / 915 | 302 / 892 | 35 / 70 | 30 | F60_120 x15, F80_40 x12, P45 x11, P60 x10 |
| NY_L7cc56d99 | S15U | 1996 / 2445 | 2166 / 2166 | 873 / 1064 | 160 / 263 | -183 / 873 | 155 / 943 | 22 / 60 | 26 | S15U x20, F60_120 x20, P90 x13, S8U x10 |
| NY_Le0da99e2 | S15U | -277 / 1580 | 486 / 1680 | -145 / 227 | 1651 / 753 | 1503 / 340 | 360 / 742 | 37 / 74 | 26 | P30 x18, F40_80 x15, P45 x7, F80_40 x7 |

Books where the 6-month refit series beats the fixed own bracket at equal risk over the whole span: 3 of 43.

## Table 2 (3-month trailing pick), same columns

| book | L6M EQ / OWN | L3M EQ / OWN | 2023 EQ / OWN | 2024 EQ / OWN | 2025 EQ / OWN | ALL EQ / OWN | won / differed | changes |
|---|---|---|---|---|---|---|---|---|
| AS_L018fb0c0 | 1757 / 617 | 2127 / 1606 | 471 / 324 | 43 / 510 | -63 / 184 | 115 / 451 | 40 / 74 | 35 |
| AS_L130cb48e | -89 / 1465 | 380 / 946 | -53 / 196 | -131 / 115 | -115 / 104 | -39 / 349 | 30 / 69 | 37 |
| AS_L15f14deb | 1436 / 1482 | 868 / 1208 | 728 / 508 | 42 / 80 | 476 / 795 | 614 / 859 | 32 / 57 | 31 |
| AS_L1756b913 | 928 / 2107 | 2449 / 3272 | 1199 / 1189 | 252 / 236 | 2 / 456 | 226 / 935 | 36 / 68 | 35 |
| AS_L1edb9fab | 802 / 2167 | 1611 / 2289 | 468 / 717 | 426 / 643 | 339 / 645 | 616 / 960 | 38 / 66 | 31 |
| AS_L29b1bc3f | 724 / 2028 | 1747 / 2095 | 1013 / 913 | 549 / 325 | 237 / 520 | 351 / 831 | 31 / 61 | 36 |
| AS_L385f4f2e | 1071 / 476 | -48 / 457 | 307 / 576 | -38 / 189 | 610 / 502 | 316 / 366 | 35 / 63 | 37 |
| AS_L385f4f2eJ502 | 398 / 2157 | 2349 / 2514 | -111 / -89 | 100 / 240 | 363 / 179 | 632 / 514 | 24 / 46 | 32 |
| AS_L3a2258bd | 305 / 1760 | 416 / 1346 | 186 / 348 | 103 / 584 | 1090 / 37 | 668 / 539 | 45 / 76 | 34 |
| AS_L3faac8df | 2590 / 1314 | 1526 / 1186 | 616 / 144 | 153 / 44 | 155 / 489 | 980 / 344 | 48 / 72 | 34 |
| AS_L40bde9ea | 817 / 937 | 749 / 1664 | 105 / 733 | 649 / 381 | 74 / 835 | 362 / 725 | 41 / 71 | 35 |
| AS_L47a9c81c | 178 / 851 | 586 / 202 | 777 / 1141 | 323 / 57 | 265 / 406 | 359 / 524 | 38 / 70 | 39 |
| AS_L578701ed | 82 / 2207 | 321 / 614 | 1242 / 929 | 1838 / 40 | -105 / 530 | 320 / 779 | 38 / 75 | 35 |
| AS_L5dee2059 | -65 / 1142 | -373 / 1986 | 765 / 724 | 262 / 463 | 1130 / 598 | 269 / 690 | 39 / 69 | 37 |
| AS_L65a26c02 | 316 / 1666 | 1145 / 2028 | 308 / 879 | 421 / 440 | 393 / 1313 | 444 / 958 | 31 / 68 | 33 |
| AS_L7c368a4f | 802 / 2456 | 1762 / 2434 | 403 / 717 | 438 / 654 | 116 / 528 | 460 / 977 | 29 / 61 | 31 |
| AS_L7ea48296 | 797 / 1927 | 1810 / 2122 | 972 / 1158 | 1468 / 711 | 835 / 556 | 1234 / 902 | 43 / 72 | 36 |
| AS_L7f41b347 | 924 / 2095 | 1233 / 1738 | 499 / 1209 | 504 / 546 | -106 / 463 | 510 / 738 | 36 / 72 | 38 |
| AS_L92a90948 | -23 / 613 | 274 / 1141 | 291 / 294 | 94 / 280 | 497 / 485 | 90 / 374 | 34 / 61 | 37 |
| AS_L973b5c8a | 1770 / 1211 | 296 / 1310 | 1067 / 1093 | 46 / 359 | 980 / 771 | 1003 / 793 | 39 / 66 | 28 |
| AS_L9aa7805c | 1022 / 1691 | 91 / 1635 | 554 / 607 | 1001 / 318 | 110 / 896 | 614 / 761 | 39 / 71 | 35 |
| AS_L9e4754b9 | 168 / 1218 | 872 / 1118 | 809 / 1064 | 250 / 257 | 132 / 196 | 547 / 523 | 36 / 68 | 31 |
| AS_La010c3eb | -160 / 861 | -234 / 906 | 1414 / 564 | 236 / 414 | -352 / 90 | -78 / 420 | 37 / 70 | 34 |
| AS_La776664b | -121 / 576 | -580 / 579 | 1169 / 859 | 163 / 420 | -158 / 340 | 27 / 539 | 33 / 72 | 41 |
| AS_Lb68a132d | 851 / 1090 | 299 / 1273 | 734 / 915 | 196 / 510 | 632 / 900 | 344 / 818 | 30 / 72 | 37 |
| AS_Lc754cf58 | 162 / 1368 | -317 / 431 | 1001 / 862 | 615 / 520 | 136 / 133 | 613 / 694 | 38 / 69 | 47 |
| AS_Lcbc8a7ec | 2653 / 1880 | 659 / 2105 | 484 / 953 | 10 / 239 | 4 / 550 | 692 / 627 | 48 / 77 | 32 |
| AS_Lec335094 | 311 / 934 | -369 / 1005 | 917 / 828 | 249 / 246 | 364 / 627 | 468 / 597 | 46 / 78 | 24 |
| AS_Lff52ec0c | 719 / 1882 | 705 / 1357 | 502 / 1207 | 605 / 549 | 199 / 569 | 671 / 815 | 39 / 72 | 35 |
| AS_M7423c0d9 | 363 / 1055 | 194 / 860 | -198 / -153 | 206 / 74 | -33 / 458 | 42 / 423 | 42 / 70 | 34 |
| AS_M7ea48296 | 213 / 429 | 1312 / 862 | 350 / 299 | 284 / 644 | 48 / 318 | 143 / 491 | 48 / 77 | 28 |
| AS_M817db5df | -204 / 512 | -321 / 325 | 128 / 164 | 358 / 400 | 636 / 417 | 69 / 370 | 39 / 75 | 40 |
| AS_M86781ac0 | 1050 / 734 | 908 / 439 | 299 / 204 | 520 / 426 | 139 / 323 | 350 / 420 | 50 / 79 | 33 |
| AS_Ma010c3eb | 199 / 705 | 778 / 706 | 111 / 139 | 177 / 254 | 131 / 458 | 125 / 459 | 38 / 74 | 39 |
| AS_Mcae177ba | 440 / 341 | 322 / 22 | 235 / 208 | 667 / 503 | 93 / 182 | 276 / 353 | 43 / 76 | 37 |
| NY_B57507767 | -121 / 1556 | 372 / 1587 | 371 / 897 | 866 / 862 | -53 / 1254 | 43 / 959 | 35 / 71 | 41 |
| NY_B6f77f23d | 495 / 1393 | -323 / 1214 | 322 / 839 | 837 / 941 | 711 / 1271 | 669 / 1042 | 42 / 74 | 36 |
| NY_B7bfd33b7 | 241 / 1440 | 464 / 1270 | 492 / 30 | -6 / 20 | -153 / 527 | -22 / 328 | 36 / 73 | 32 |
| NY_L05350e98 | 746 / 989 | -8 / 1043 | 427 / 833 | 132 / 715 | -101 / 155 | 303 / 650 | 32 / 69 | 42 |
| NY_L488784d8 | 574 / 915 | 684 / 838 | 422 / 690 | 844 / 382 | 2448 / 623 | 1351 / 601 | 52 / 76 | 35 |
| NY_L6547965c | 716 / 1275 | 761 / 588 | 2690 / 2465 | -13 / 959 | 707 / 915 | 190 / 892 | 31 / 70 | 38 |
| NY_L7cc56d99 | 2314 / 2445 | 2166 / 2166 | 1288 / 1064 | 31 / 263 | -182 / 873 | 87 / 943 | 30 / 60 | 29 |
| NY_Le0da99e2 | -16 / 1580 | 1762 / 1680 | 9 / 227 | 2159 / 753 | -35 / 340 | 282 / 742 | 38 / 76 | 43 |

## Which prior-year band the bracket verdicts used

FROZEN: the band in stage2.json / BRACKET_SHAPES_*.md is the CURRENT PICK (one fixed shape, the screen winner) traded over the whole of 2023, 2024 and 2025 against the own bracket (wf_gate.year_band: worst of the 1-lot ulcer change and the equal-risk $/wk change; RED > 30% fails). That is not what a re-fit does: a re-fit would have traded a different shape in those years. Below: the band recomputed on the ROLLING-REFIT series (6-month pick), same function, per year, for the 13 books whose shape won in both recent windows; a band is the worse of ulcer change and equal-risk $/wk change of the refit series vs the own bracket in that year.

| book | own | today pick | WF (verdict file) | WF rolling (wf_gate) | frozen band 2023/24/25 | refit-series band 2023/24/25 | refit EQ $/wk by year vs own 2023 / 2024 / 2025 | gate that stopped it (old) | verdict on refit band |
|---|---|---|---|---|---|---|---|---|---|
| AS_L018fb0c0 | S15U | A20U10U | 0.529 | 0.529 | GREEN/RED/GREEN | GREEN/RED/GREEN | 516 v 324 / 55 v 510 / 196 v 184 | not kept: walk-forward persistence 0.529 over 70 periods prior-year RE | band unchanged |
| AS_L15f14deb | P60 | F40_80 | 0.466 | 0.466 | RED/GREEN/GREEN | GREEN/RED/RED | 531 v 508 / -288 v 80 / 247 v 795 | not kept: walk-forward persistence 0.466 over 73 periods prior-year RE | band unchanged |
| AS_L1edb9fab | P60 | P30 | 0.514 | 0.514 | GREEN/RED/RED | GREEN/AMBER/AMBER | 859 v 717 / 456 v 643 / 457 v 645 | not kept: walk-forward persistence 0.514 over 74 periods prior-year RE | band no longer RED |
| AS_L40bde9ea | P60 | P45 | 0.57 | 0.57 | GREEN/RED/GREEN | GREEN/GREEN/RED | 818 v 733 / 808 v 381 / 70 v 835 | not kept: walk-forward persistence 0.57 over 79 periods prior-year RED | band unchanged |
| AS_L7c368a4f | P60 | P30 | 0.543 | 0.543 | GREEN/RED/RED | GREEN/RED/RED | 859 v 717 / 336 v 654 / 292 v 528 | not kept: walk-forward persistence 0.543 over 70 periods prior-year RE | band unchanged |
| AS_L7ea48296 | P60 | P45 | 0.515 | 0.515 | AMBER/GREEN/GREEN | GREEN/GREEN/GREEN | 1071 v 1158 / 796 v 711 / 787 v 556 | not kept: walk-forward persistence 0.515 over 68 periods | band unchanged |
| AS_Lc754cf58 | A20U10U | F60_120 | 0.713 | 0.713 | GREEN/GREEN/GREEN | GREEN/GREEN/GREEN | 948 v 862 / 789 v 520 / 128 v 133 | walk-forward pass, UNCONFIRMED (real_gain 0.00 on L6M: the bracket doe | band unchanged |
| AS_M7ea48296 | P60 | P45 | 0.595 | 0.595 | GREEN/AMBER/GREEN | GREEN/RED/RED | 346 v 299 / 449 v 644 / 112 v 318 | PASSES walk-forward + prior-year band + null | band now RED |
| AS_Ma010c3eb | P60 | P45 | 0.551 | 0.551 | GREEN/GREEN/RED | RED/GREEN/RED | 68 v 139 / 615 v 254 / 150 v 458 | not kept: walk-forward persistence 0.551 over 69 periods prior-year RE | band unchanged |
| NY_B57507767 | S15U | S8U | 0.603 | 0.603 | GREEN/AMBER/GREEN | RED/GREEN/GREEN | 534 v 897 / 1979 v 862 / 1610 v 1254 | walk-forward pass, UNCONFIRMED (real_gain 0 on L6M: the bracket does n | band now RED |
| NY_L05350e98 | S15U | S8U | 0.7 | 0.7 | AMBER/GREEN/GREEN | RED/RED/RED | 516 v 833 / 307 v 715 / -25 v 155 | walk-forward pass, UNCONFIRMED (real_gain 0 on L6M: the bracket does n | band now RED |
| NY_L488784d8 | P60 | P30 | 0.667 | 0.667 | RED/GREEN/RED | RED/GREEN/GREEN | 413 v 690 / 389 v 382 / 2679 v 623 | not kept:  prior-year RED (shared band) | band unchanged |
| NY_L7cc56d99 | S15U | S8U | 0.676 | 0.676 | RED/GREEN/GREEN | AMBER/RED/RED | 873 v 1064 / 160 v 263 / -183 v 873 | not kept:  prior-year RED (shared band) | band unchanged |

Books among these 13 whose band verdict (RED / not RED) changes from frozen to refit-series: 4.

## The 15% max-DD / worst-week guard

Who and where: it is MY rule (W-BRKT), in code/th_brkt/brkt_score.py function judge(): "scaled max drawdown and scaled worst week in L6M not worse than the own bracket by more than 15%" plus scaled $/wk >= own in BOTH L6M and L3M. I copied the 15% number from W-LAYERS pool_run.py (its stage-1 pick rule, guard=0.15 on mean / worst week / max DD) and from the standing "15% guard on adds, swaps and drops" of the stack rules (order 1351Z). It is NOT one of the four gates Josh approved at 18:10Z Nov 20 (recent pick, walk-forward >= 58%, prior-year band, null >= 4 of 5). Of the 23 books with some shape beating the own bracket in both recent windows, 10 were removed by it BEFORE walk-forward. Their results without the guard follow (best L6M equal-risk shape, then walk-forward persistence of wf_gate.rolling over all 17 shapes, the refit share, and the refit-series band):

| book | own | best shape L6M eq (no guard) | wf_gate.rolling persistence | refit won / differed (6M) | refit-series band 2023/24/25 | refit EQ vs own, whole span |
|---|---|---|---|---|---|---|
| AS_L130cb48e | P60 | F40_80 2097 vs 1465 | 0.578 | 33 / 65 | RED/RED/RED | 29 vs 349 |
| AS_L29b1bc3f | P60 | P30 3326 vs 2027 | 0.628 | 30 / 66 | AMBER/GREEN/RED | 353 vs 831 |
| AS_L3faac8df | P60 | P45 4929 vs 1313 | 0.627 | 60 / 80 | GREEN/GREEN/RED | 1242 vs 344 |
| AS_L47a9c81c | P60 | F120_60 1310 vs 851 | 0.521 | 42 / 74 | RED/GREEN/GREEN | 492 vs 524 |
| AS_L578701ed | P60 | A10U20U 2483 vs 2207 | 0.597 | 31 / 68 | RED/GREEN/RED | 369 vs 779 |
| AS_L9e4754b9 | P60 | P45 2893 vs 1217 | 0.671 | 42 / 76 | GREEN/GREEN/GREEN | 251 vs 523 |
| AS_La010c3eb | P60 | P45 1009 vs 861 | 0.571 | 33 / 64 | GREEN/RED/RED | 163 vs 420 |
| AS_Lcbc8a7ec | P60 | F40_80 4593 vs 1879 | 0.513 | 47 / 79 | GREEN/RED/RED | 517 vs 627 |
| AS_M7423c0d9 | S8U | P45 1086 vs 1054 | 0.603 | 34 / 62 | GREEN/GREEN/GREEN | 330 vs 423 |
| AS_M817db5df | P60 | F40_80 610 vs 512 | 0.521 | 38 / 76 | RED/GREEN/RED | 91 vs 370 |
| AS_M86781ac0 | P60 | P45 1060 vs 734 | 0.681 | 46 / 79 | GREEN/GREEN/RED | 209 vs 420 |
| AS_Mcae177ba | P60 | F40_80 500 vs 340 | 0.697 | 37 / 78 | GREEN/GREEN/RED | 133 vs 353 |
| NY_B7bfd33b7 | P60 | F80_40 1495 vs 1386 | 0.466 | 31 / 70 | GREEN/RED/RED | 254 vs 328 |

PLAIN READING (fill after the numbers below are checked): see the MORNING.md block.

