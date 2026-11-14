# DS3_EVENT_WINDOWS - P10 event windows per book (W-TD)

**VERDICT (plain): P10 first page: window tables on the base trades are in (section 1); 5 of 61 engine cells have L3M so far. No PASS claim.**

Rebuilt 2026-11-14T20:24Z (epoch 1794687849) by code/th_trendevent/td_loop.sh. Research only, NO PASS claim. Prereg autopilot/TRENDEVENT_PREREG.md (sha 902e8acf65f05aa0 + addenda A b7faa5d87fc820e1, B 69bc618cfb2721f2, C faab906024e809c7, D 6bf6f88e5100fc03, E c61df02737498986 in DECISIONS.md, logged before scoring).

Identity: TL3_TD_ID 202610 (hook path active, neutral): 598 trades net_fee 25943.82 vs JN05W2 598 / 25943.82 -> IDENTICAL (trade lists equal row by row).
Base JN05W2 exact engine, all layers ON; score = MEASURED net (gross - $4.84/ct RT - excess slip entry +0.23 / cut +0.40 / stop +0.44 / target 0 pt, +1.36 pt on non-target exits 08:30-08:44 ET); Globex label day; windows L3M (08-01..10-31) L6M (05-01..) HOLD (2025-11-01..) GAP (2025-07..10) PRE (2024-10..2025-06) X' (2023-04..2024-09). Max DD of the recent windows is one week (2026-W44): every row shows the DD cut with and without that week. Calendar /mnt/l2/l2vast/_calendar/events.csv: 562 events from 2024-10-01 (CPI, NFP, PCE, PPI, GDP, RETAIL, ISM, FOMC and minutes, chair speeches, Treasury auction closes, megacap after-close earnings). X' (2023-04..2024-09) has NO calendar: event rules are identity there and no X' number is given. Existing engine guards: entries blocked 09:00-10:00 ET and 15:00-18:05 ET, lot table 0 in the 08:30-09:30 'pre' session for all books, so entries around the 08:30 prints can only come before 08:30 and the effect of the 08:30 events is mostly on open positions.

## 1. P&L and slippage around each event type, JN05W2 measured net, 2024-10..2026-10 (25 months, 13512 trades, mean $97 per trade)

Entries by ENTRY time (in_preX = entered X minutes or less before the event; in_postX = entered within X minutes after), per trade = mean measured net per trade; slip = mean entry slippage proxy (entry price minus the signal-bar close, points, day offset removed; positive = worse); placebo = the same statistic with the event dates shifted 11 / 23 / 37 business days (mean of the three). n < 15 cells carry no weight.

| type | window | n | net | per_trade | slip_pts | cost_per_trade | placebo_n | placebo_per_trade |
|---|---|---|---|---|---|---|---|---|
| FOMC | in_pre30 | 5 | 2152 | 430 | 0.05 | 16 | 3 | 248 |
| FOMC | in_pre15 | 4 | 2780 | 695 | -0.16 | 16 | 3 | -558 |
| FOMC | in_post5 | 4 | -862 | -215 | 0.92 | 18 | 1 | -227 |
| FOMC | in_post15 | 8 | 1724 | 216 | 0.62 | 15 | 1 | -419 |
| FOMC | in_post30 | 9 | 848 | 94 | 0.75 | 15 | 3 | -473 |
| FOMC | in_post60 | 23 | 6435 | 280 | 0.83 | 14 | 3 | 61 |
| CPI | in_pre30 | 7 | 6468 | 924 | -0.35 | 22 | 16 | 148 |
| CPI | in_pre15 | 3 | 4767 | 1589 | -0.29 | 13 | 8 | 96 |
| CPI | in_pre5 | 3 | 4767 | 1589 | -0.29 | 13 | 1 | 1103 |
| NFP | in_pre30 | 10 | 5909 | 591 | -0.04 | 29 | 15 | 2 |
| NFP | in_pre15 | 5 | 3972 | 794 | 0.20 | 17 | 7 | -374 |
| NFP | in_pre5 | 1 | 1191 | 1191 | 0.00 | 9 | 2 | 259 |
| PCE | in_pre30 | 17 | 14801 | 871 | -0.61 | 27 | 19 | 146 |
| PCE | in_pre15 | 3 | -4953 | -1651 | -0.92 | 74 | 7 | 89 |
| PCE | in_pre5 | 1 | -1906 | -1906 | -1.50 | 89 | 2 | 112 |
| PCE | in_post15 | 4 | 1298 | 324 | 2.86 | 31 | 5 | -273 |
| PCE | in_post30 | 8 | -747 | -93 | 2.53 | 28 | 8 | 164 |
| PCE | in_post60 | 16 | 1459 | 91 | -0.62 | 22 | 12 | 222 |
| ISM | in_pre30 | 22 | 6368 | 289 | 0.75 | 15 | 17 | 364 |
| ISM | in_pre15 | 1 | 1791 | 1791 | -2.25 | 9 | 1 | 1791 |
| ISM | in_post5 | 13 | -10842 | -834 | -1.46 | 18 | 17 | -282 |
| ISM | in_post15 | 49 | -8876 | -181 | -0.86 | 18 | 42 | -31 |
| ISM | in_post30 | 95 | 2696 | 28 | 0.87 | 17 | 70 | 107 |
| ISM | in_post60 | 148 | 6939 | 47 | 0.70 | 17 | 117 | -8 |
| AUC | in_pre30 | 77 | 11835 | 154 | 0.13 | 17 | 73 | 105 |
| AUC | in_pre15 | 39 | -3187 | -82 | 0.09 | 18 | 34 | 168 |
| AUC | in_pre5 | 9 | -616 | -68 | 0.01 | 19 | 5 | -128 |
| AUC | in_post5 | 19 | 3706 | 195 | -0.18 | 16 | 20 | 146 |
| AUC | in_post15 | 45 | 3896 | 87 | -0.19 | 16 | 39 | 41 |
| AUC | in_post30 | 76 | -6506 | -86 | 0.21 | 17 | 68 | 49 |
| AUC | in_post60 | 121 | -17308 | -143 | 0.14 | 17 | 109 | -7 |
| OTH830 | in_pre30 | 39 | 10896 | 279 | -0.33 | 36 | 42 | 277 |
| OTH830 | in_pre15 | 17 | -3043 | -179 | 0.51 | 39 | 21 | 230 |
| OTH830 | in_pre5 | 2 | -1574 | -787 | -0.25 | 31 | 7 | 484 |

### 1b. Exits inside the post windows and trades OPEN across the event

| type | window | n | net | per_trade | stop_share | cost_per_trade | placebo_per_trade |
|---|---|---|---|---|---|---|---|
| FOMC | open_across | 21 | 17834 | 849 | 0.14 | 15 | -186 |
| FOMC | out_post5 | 12 | 4253 | 354 | 0.25 | 16 | -359 |
| FOMC | out_post15 | 15 | 7824 | 522 | 0.20 | 15 | -357 |
| FOMC | out_post30 | 18 | 5019 | 279 | 0.17 | 15 | -313 |
| FOMC | out_post60 | 40 | 21108 | 528 | 0.07 | 14 | 322 |
| CPI | open_across | 56 | 23568 | 421 | 0.25 | 47 | 433 |
| CPI | out_post5 | 50 | 23927 | 479 | 0.28 | 49 | 498 |
| CPI | out_post15 | 52 | 21775 | 419 | 0.27 | 49 | 238 |
| CPI | out_post30 | 52 | 21775 | 419 | 0.27 | 49 | 75 |
| CPI | out_post60 | 53 | 22966 | 433 | 0.26 | 48 | 294 |
| NFP | open_across | 68 | 50277 | 739 | 0.24 | 36 | 465 |
| NFP | out_post5 | 54 | 36537 | 677 | 0.30 | 42 | 253 |
| NFP | out_post15 | 57 | 40108 | 704 | 0.28 | 40 | 263 |
| NFP | out_post30 | 57 | 40108 | 704 | 0.28 | 40 | 544 |
| NFP | out_post60 | 58 | 41299 | 712 | 0.28 | 40 | 318 |
| PCE | open_across | 45 | 12438 | 276 | 0.11 | 34 | 357 |
| PCE | out_post5 | 15 | 1167 | 78 | 0.13 | 46 | 488 |
| PCE | out_post15 | 24 | -6531 | -272 | 0.12 | 47 | -61 |
| PCE | out_post30 | 33 | 3461 | 105 | 0.09 | 39 | -31 |
| PCE | out_post60 | 42 | 2147 | 51 | 0.10 | 36 | 114 |
| ISM | open_across | 10 | 14300 | 1430 | 0.00 | 14 | 750 |
| ISM | out_post5 | 6 | 1827 | 304 | 0.33 | 14 | 650 |
| ISM | out_post15 | 24 | -7418 | -309 | 0.17 | 18 | 2 |
| ISM | out_post30 | 59 | -10028 | -170 | 0.17 | 16 | 128 |
| ISM | out_post60 | 110 | -4155 | -38 | 0.12 | 16 | -28 |
| AUC | open_across | 185 | 72000 | 389 | 0.05 | 16 | 240 |
| AUC | out_post5 | 25 | 10014 | 401 | 0.08 | 16 | 405 |
| AUC | out_post15 | 54 | 20481 | 379 | 0.07 | 17 | 227 |
| AUC | out_post30 | 96 | 32604 | 340 | 0.05 | 16 | 249 |
| AUC | out_post60 | 145 | 36652 | 253 | 0.05 | 16 | 178 |
| OTH830 | open_across | 148 | 8857 | 60 | 0.17 | 41 | 490 |
| OTH830 | out_post5 | 59 | -25496 | -432 | 0.31 | 58 | -378 |
| OTH830 | out_post15 | 78 | -22790 | -292 | 0.26 | 56 | -124 |
| OTH830 | out_post30 | 94 | -13501 | -144 | 0.21 | 50 | -26 |
| OTH830 | out_post60 | 107 | -16751 | -157 | 0.21 | 47 | 217 |

### 1c. Per book (entries within 15 min before / 15 and 60 min after the event; n / $ per trade)

| type | book | in_pre15 | in_post15 | in_post60 | open_across |
|---|---|---|---|---|---|
| FOMC | K7 | 4 / 695 | 8 / 216 | 23 / 280 | 12 / 555 |
| FOMC | P7 | 0 | 0 | 0 | 3 / 1935 |
| FOMC | M7 | 0 | 0 | 0 | 4 / 450 |
| FOMC | U7 | 0 | 0 | 0 | 1 / 2381 |
| FOMC | H7 | 0 | 0 | 0 | 0 |
| FOMC | A7 | 0 | 0 | 0 | 1 / 1191 |
| FOMC | O7 | 0 | 0 | 0 | 0 |
| CPI | K7 | 2 / 1191 | 0 | 0 | 12 / 662 |
| CPI | P7 | 1 / 2386 | 0 | 0 | 12 / 233 |
| CPI | M7 | 0 | 0 | 0 | 13 / 899 |
| CPI | U7 | 0 | 0 | 0 | 9 / 676 |
| CPI | H7 | 0 | 0 | 0 | 5 / -1384 |
| CPI | A7 | 0 | 0 | 0 | 5 / 397 |
| CPI | O7 | 0 | 0 | 0 | 0 |
| NFP | K7 | 1 / 1191 | 0 | 0 | 17 / 279 |
| NFP | P7 | 3 / 530 | 0 | 0 | 16 / 1834 |
| NFP | M7 | 1 / 1191 | 0 | 0 | 14 / 614 |
| NFP | U7 | 0 | 0 | 0 | 14 / 247 |
| NFP | H7 | 0 | 0 | 0 | 3 / 276 |
| NFP | A7 | 0 | 0 | 0 | 4 / 827 |
| NFP | O7 | 0 | 0 | 0 | 0 |
| PCE | K7 | 1 / -1906 | 0 | 6 / 163 | 13 / 162 |
| PCE | P7 | 0 | 2 / 486 | 5 / 64 | 11 / 565 |
| PCE | M7 | 1 / -896 | 2 / 162 | 5 / 32 | 9 / 749 |
| PCE | U7 | 1 / -2151 | 0 | 0 | 7 / -213 |
| PCE | H7 | 0 | 0 | 0 | 1 / -2231 |
| PCE | A7 | 0 | 0 | 0 | 3 / -233 |
| PCE | O7 | 0 | 0 | 0 | 1 / 1791 |
| ISM | K7 | 0 | 19 / -235 | 55 / -39 | 1 / 511 |
| ISM | P7 | 0 | 7 / 338 | 23 / -212 | 2 / 1116 |
| ISM | M7 | 0 | 20 / -197 | 54 / 202 | 2 / 1788 |
| ISM | U7 | 0 | 0 | 0 | 0 |
| ISM | H7 | 0 | 3 / -947 | 16 / 193 | 0 |
| ISM | A7 | 0 | 0 | 0 | 0 |
| ISM | O7 | 1 / 1791 | 0 | 0 | 5 / 1596 |
| AUC | K7 | 30 / -140 | 37 / -65 | 102 / -136 | 94 / 169 |
| AUC | P7 | 2 / 512 | 2 / 507 | 7 / -745 | 32 / 826 |
| AUC | M7 | 5 / 6 | 6 / 882 | 12 / 145 | 41 / 503 |
| AUC | U7 | 0 | 0 | 0 | 1 / -2456 |
| AUC | H7 | 2 / -21 | 0 | 0 | 15 / 606 |
| AUC | A7 | 0 | 0 | 0 | 0 |
| AUC | O7 | 0 | 0 | 0 | 2 / 1218 |
| EARN | K7 | 0 | 0 | 0 | 0 |
| EARN | P7 | 0 | 0 | 0 | 0 |
| EARN | M7 | 0 | 0 | 0 | 0 |
| EARN | U7 | 0 | 0 | 0 | 0 |
| EARN | H7 | 0 | 0 | 0 | 0 |
| EARN | A7 | 0 | 0 | 0 | 0 |
| EARN | O7 | 0 | 0 | 0 | 0 |
| OTH830 | K7 | 5 / -99 | 0 | 0 | 46 / 20 |
| OTH830 | P7 | 5 / -412 | 0 | 0 | 35 / 127 |
| OTH830 | M7 | 5 / -74 | 0 | 0 | 39 / 80 |
| OTH830 | U7 | 2 / -60 | 0 | 0 | 20 / -371 |
| OTH830 | H7 | 0 | 0 | 0 | 2 / 1261 |
| OTH830 | A7 | 0 | 0 | 0 | 6 / 880 |
| OTH830 | O7 | 0 | 0 | 0 | 0 |

### 1d. The 08:30 fill cost (+1.36 pt on non-target exits 08:30-08:44 ET) in this sample
Non-target exits in 08:30-08:44 ET: 203 trades, 346 contracts, extra cost $9,411 over 25 months ($87 per week); by book: A7 $190, H7 $326, K7 $1,958, M7 $1,741, P7 $3,237, U7 $1,958.

### 1e. STATIC first estimate of every rule (not the engine; change in measured $ over the window if the rule had been applied to the JN05W2 trade list)
B = drop trades entered in the window, H = half their P&L, F = flatten at T-x using the 1-min close; real events vs the mean of the three shifted-date placebos. Negative = the rule loses money. This is a shortlist and a cross-check only; the drawdown verdict comes from the exact-engine cells in section 2.

| type | rule | L3M_real | L3M_placebo | L6M_real | L6M_placebo | HOLD_real | HOLD_placebo | PRE_real | PRE_placebo |
|---|---|---|---|---|---|---|---|---|---|
| AUC | B15_15 | -3191 | -5711 | -5425 | -11094 | -1640 | -5835 | 7256 | 162 |
| AUC | B30_30 | -2881 | -4970 | -8177 | -17636 | -6260 | -7628 | 4618 | -777 |
| AUC | B5_5 | -548 | -785 | -4741 | -3016 | -109 | -192 | 590 | -1048 |
| AUC | F15 | -853 | 1424 | -4601 | -5933 | -8023 | -5373 | 103197 | 81278 |
| AUC | H15_15 | -1595 | -2855 | -2713 | -5547 | -820 | -2918 | 3628 | 81 |
| AUC | H30_30 | -1441 | -2485 | -4088 | -8818 | -3130 | -3814 | 2309 | -388 |
| CPI | B15_0 | -1191 | 0 | -3577 | -1612 | -3577 | -288 | 0 | -1854 |
| CPI | B30_0 | -1191 | -1795 | -1705 | -4598 | -1705 | -522 | -2381 | -1076 |
| CPI | B5_0 | -1191 | 0 | -3577 | 504 | -3577 | -56 | 0 | -1589 |
| CPI | F15 | -10132 | -1367 | -7746 | -5340 | -22720 | 1131 | 43333 | 25291 |
| CPI | F30 | -6226 | 3564 | -2781 | 1999 | -19875 | 2858 | 43660 | 20785 |
| CPI | F5 | -8737 | -1672 | -3001 | -2617 | -19365 | 3088 | 44667 | 24081 |
| CPI | H15_0 | -595 | 0 | -1788 | -806 | -1788 | -144 | 0 | -927 |
| CPI | H30_0 | -595 | -898 | -853 | -2299 | -853 | -261 | -1191 | -538 |
| CPI | H5_0 | -595 | 0 | -1788 | 252 | -1788 | -28 | 0 | -795 |
| EARN | B0_150 | -13508 | -5320 | -8265 | -6508 | -42585 | 8274 | -36866 | 896 |
| EARN | B0_90 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| EARN | H0_150 | -6754 | -2660 | -4133 | -3254 | -21292 | 4137 | -18433 | 448 |
| FOMC | B15_15 | 0 | 636 | -1467 | 1199 | -728 | 1553 | -2586 | 303 |
| FOMC | B15_60 | 0 | 963 | -2972 | 1453 | -2590 | 2129 | -4743 | 110 |
| FOMC | B30_30 | 0 | 567 | -591 | 733 | 148 | 1409 | -1957 | 110 |
| FOMC | B5_5 | 0 | 636 | 1156 | 636 | 2052 | 636 | -1191 | 76 |
| FOMC | F15 | 0 | -291 | 0 | -1001 | -1090 | -1351 | 94372 | 17160 |
| FOMC | F30 | 0 | 432 | 0 | 73 | -496 | -165 | 96757 | 17961 |
| FOMC | F5 | 0 | -386 | -3285 | -717 | -3794 | -712 | 98014 | 17276 |
| FOMC | H15_15 | 0 | 318 | -733 | 599 | -364 | 777 | -1293 | 151 |
| FOMC | H30_30 | 0 | 283 | -295 | 366 | 74 | 705 | -979 | 55 |
| FOMC | H30_60 | 0 | 283 | -1486 | 329 | -1295 | 668 | -2057 | 55 |
| ISM | B0_15 | 266 | 1407 | 6444 | 1136 | 6972 | 3590 | -8 | 439 |
| ISM | B0_30 | -9688 | 143 | -2358 | -262 | -7150 | -1120 | 1711 | -1767 |
| ISM | B0_5 | 0 | 1698 | 2645 | 1698 | 4262 | 2644 | 4913 | -984 |
| ISM | B0_60 | -11249 | 1981 | 687 | 1574 | -2714 | 494 | -5698 | 2547 |
| ISM | H0_15 | 133 | 704 | 3222 | 568 | 3486 | 1795 | -4 | 219 |
| ISM | H0_30 | -4844 | 71 | -1179 | -131 | -3575 | -560 | 856 | -883 |
| NFP | B15_0 | -1191 | 2336 | -2381 | -47 | -2781 | 162 | -1191 | 1692 |
| NFP | B30_0 | -1191 | 2874 | -7143 | -4858 | -5549 | -853 | -1191 | 215 |
| NFP | B5_0 | 0 | 0 | -1191 | -795 | -1191 | -795 | 0 | 1245 |
| NFP | F15 | 2413 | -506 | -5867 | -3680 | -6120 | -12216 | 33077 | 8031 |
| NFP | F30 | 6707 | -774 | 3 | 906 | 652 | -9754 | 28037 | 9409 |
| NFP | F5 | 2225 | 1438 | -10605 | -2713 | -18321 | -8652 | 30734 | 9724 |
| NFP | H15_0 | -595 | 1168 | -1191 | -23 | -1391 | 81 | -595 | 846 |
| NFP | H30_0 | -595 | 1437 | -3572 | -2429 | -2774 | -426 | -595 | 108 |
| NFP | H5_0 | 0 | 0 | -595 | -398 | -595 | -398 | 0 | 623 |
| OTH830 | B15_0 | 806 | -2689 | -2355 | -4552 | -701 | -2674 | 2222 | -851 |
| OTH830 | B30_0 | 1567 | -6251 | -2184 | -9256 | -6134 | -3784 | -988 | -5437 |
| OTH830 | B5_0 | 0 | 27 | 903 | -1224 | 1574 | -595 | 0 | -3305 |
| OTH830 | F15 | 4274 | -6110 | -1927 | -7839 | -3329 | -17286 | 113467 | 64808 |
| OTH830 | F30 | 5918 | 668 | -337 | -81 | -4320 | -13808 | 106096 | 70259 |
| OTH830 | F5 | 8533 | -12570 | 606 | -14360 | -3843 | -24381 | 112800 | 71189 |
| OTH830 | H15_0 | 403 | -1345 | -1177 | -2276 | -350 | -1337 | 1111 | -425 |
| OTH830 | H30_0 | 783 | -3125 | -1092 | -4628 | -3067 | -1892 | -494 | -2718 |
| OTH830 | H5_0 | 0 | 14 | 452 | -612 | 787 | -298 | 0 | -1652 |
| PCE | B15_0 | 0 | -2506 | 0 | -3085 | 0 | -2520 | 4953 | -191 |
| PCE | B30_0 | 0 | -4965 | -1191 | -4701 | -9534 | -4102 | 1886 | -2404 |
| PCE | B5_0 | 0 | -397 | 0 | -480 | 0 | -480 | 1906 | 0 |
| PCE | F15 | 2030 | -2360 | 472 | -1783 | -10250 | -3211 | 17948 | 30049 |
| PCE | F30 | 2341 | -176 | 3776 | -387 | -933 | -4551 | 33338 | 31183 |
| PCE | F5 | 2900 | -4401 | 1252 | -2241 | -8273 | -2824 | 28294 | 30706 |
| PCE | H15_0 | 0 | -1253 | 0 | -1543 | 0 | -1260 | 2477 | -95 |
| PCE | H30_0 | 0 | -2482 | -595 | -2351 | -4767 | -2051 | 943 | -1202 |
| PCE | H5_0 | 0 | -198 | 0 | -240 | 0 | -240 | 953 | 0 |

## 2. Engine cells (exact JN05W2 + event hook): no-entry window (B pre_post), half size (H pre_post), flatten before (F minutes)

Same columns as the trend-day page (see DS3_TREND_DAYS.md section 3). Months without an event of the type are identical to JN05W2 by construction (rule cannot act). Event windows exist only from 2024-10 (no X').

| cell | win | dMean | DDcut | DDcut_noW44 | dWorstWk | stops_wk | best5 | w2l | wf2w | gate |
|---|---|---|---|---|---|---|---|---|---|---|
| EV_CPI_B15_0 | L3M | -92 | 0.0 | 0.0 | 0 | 10.46(10.46) | 99 | 0 | 86 | n |
| EV_NFP_B15_0 | L3M | -92 | 0.0 | 0.0 | 0 | 10.46(10.46) | 100 | 0 | 86 | n |
| EV_NFP_F15 | L3M | 86 | 0.0 | 6.8 | 0 | 10.31(10.46) | 100 | 0 | 86 | Y |
| EV_PCE_F15 | L3M | 158 | 0.0 | 0.0 | 0 | 10.46(10.46) | 100 | 0 | 100 | n |
| EV_FOMC_F15 | L3M | 0 | 0.0 | 0.0 | 0 | 10.46(10.46) | 100 | 0 | 100 | n |

## 3. Best action per event type (by L6M drawdown cut among cells with a gate pass in L3M and L6M; otherwise best partial)

(no cell has L6M yet)

## 4. Per-book slices of the best cells (same run, books interact through the shared engine)

(none yet)

## 5. Placebos (events shifted 11 / 23 / 37 business days)

| cell | win | dMean | DDcut | DDcut_noW44 | dWorstWk | stops_wk | best5 | w2l | wf2w | gate |
|---|---|---|---|---|---|---|---|---|---|---|
| EV_CPI_B15_0 | L3M | -92 | 0.0 | 0.0 | 0 | 10.46(10.46) | 99 | 0 | 86 | n |
| EV_NFP_B15_0 | L3M | -92 | 0.0 | 0.0 | 0 | 10.46(10.46) | 100 | 0 | 86 | n |
| EV_NFP_F15 | L3M | 86 | 0.0 | 6.8 | 0 | 10.31(10.46) | 100 | 0 | 86 | Y |

## 6. Would a competent discretionary trader do it?
- Flat before CPI/NFP/FOMC: a common desk rule, but D7 trades that are open across the prints are net positive in the sample (section 1b); it must show a drawdown gain at equal mean to be worth the lost trend capture.
- No new entries 5-15 minutes before and after a print: normal practice (spreads widen, first move is noise); costs little because the engine already blocks 09:00-10:00 and the 08:30-09:30 session has no lots.
- Half size inside the window: the standard compromise when a trader will not skip the trade.
- Megacap earnings: after-close prints (16:01-16:47 ET) sit in the engine's 15:00-18:05 block; only the Asia open (18:05+) can be hit, so the EARN cells test no-entry / half size until 19:00.

## 7. Hand-off
Best rules go to W-JV (a5266a6235f1c7bbb). Cell spec: td_cells.py (EVG grid), hook td_hooks.py (ev rules). Calendar caveat: X' has no calendar.
