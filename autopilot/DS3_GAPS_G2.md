# DS3_GAPS_G2 - GAPS order G2 (book level: M7, P7 Asia by slot, cost-after-edge by book x session) - W-G2

Written 2026-11-14 19:18Z. Shadow only. No PASS claims. Prereg GAPS_G2_PREREG.md (sha 9668b1102c521a14 in DECISIONS.md). **Caveat on every row: the engine state cut fires in the engine but did NOT fire live on 11-11 (DS3_P7_CUT_FIDELITY.md); "cut OFF" rows are the live-realistic world.** All numbers are after live costs (fee $4.84/contract RT + live-excess slip: entry +0.23 pt, market cut +0.40, stop +0.44, target 0, +1.36 pt at 08:30-08:44 ET) from the exact trade lists; stack effects in section A are first-order (trade-list subtraction, no path change) until the exact rows in section E land. Windows: L6M 202605-202610, HOLD 202511-202604, PRE 202402-202506, X' 202304-202401. User lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2, caps x1.75): all rules here are count/slot/session rules and transfer unchanged; $ figures scale with lots (x1.75 on the panel).

## 0. Exact status (months done of 43; stage 1 = L6M+HOLD = 12 months)

| set          |   months |
|:-------------|---------:|
| G2JN_ID      |        1 |
| G2JN_M7_HALF |       43 |
| G2JN_M7_LON  |       12 |
| G2JN_M7_NYAM |       43 |
| G2JN_M7_OFF  |       43 |
| G2JN_P7A_BW  |       43 |
| G2JN_P7A_BWD |       43 |
| G2JN_P7A_PRE |       12 |
| G2J_ID       |        1 |
| G2J_M7_HALF  |       43 |
| G2J_M7_LON   |       43 |
| G2J_M7_NYAM  |       43 |
| G2J_M7_OFF   |       43 |
| G2J_P7A_BW   |       12 |
| G2J_P7A_BWD  |       12 |
| G2J_P7A_PRE  |       43 |
| G2N_ID       |        1 |
| G2N_M7_HALF  |       12 |
| G2N_M7_LON   |       12 |
| G2N_M7_NYAM  |       12 |
| G2N_M7_OFF   |       43 |
| G2N_P7A_BW   |       43 |
| G2N_P7A_BWD  |       43 |
| G2N_P7A_PRE  |       12 |
| G2_ID        |        1 |
| G2_M7_HALF   |       12 |
| G2_M7_LON    |       12 |
| G2_M7_NYAM   |       12 |
| G2_M7_OFF    |       12 |
| G2_P7A_BW    |       12 |
| G2_P7A_BWD   |       12 |
| G2_P7A_PRE   |       43 |


## C. Cost-after-edge by book x session ($/wk after fees+live-excess slip; trade lists)


#### JN05W2 (five survivors on the live panel; state cut ON)

|                  |   L6M |   HOLD |   PRE |   X' |   gross_L6M |   cost_L6M |   trades_L6M | NEG L6M&HOLD   | NEG all 3 (L6M,HOLD,PRE)   |
|:-----------------|------:|-------:|------:|-----:|------------:|-----------:|-------------:|:---------------|:---------------------------|
| ('A7', 'asia')   |   586 |    715 |   980 |  223 |         767 |        181 |          353 | False          | False                      |
| ('H7', 'asia')   |  1645 |   -619 |  1403 |  -19 |        1796 |        151 |          140 | False          | False                      |
| ('H7', 'nyam')   |   162 |   -199 |    12 |  176 |         180 |         18 |           36 | False          | False                      |
| ('K7', 'asia')   |  2130 |   2489 |   727 |   48 |        2607 |        478 |          787 | False          | False                      |
| ('K7', 'london') |   168 |    626 |  -176 |  -61 |         440 |        272 |          427 | False          | False                      |
| ('K7', 'nyam')   |    93 |   -812 |   153 |  220 |         192 |         98 |          188 | False          | False                      |
| ('K7', 'nypm')   |  1598 |  -1026 |     0 |  292 |        1686 |         88 |          151 | False          | False                      |
| ('M7', 'london') |  -676 |   -630 |  -183 |  204 |        -312 |        364 |          519 | True           | True                       |
| ('M7', 'nyam')   |   281 |     53 |   512 | -339 |         393 |        112 |          214 | False          | False                      |
| ('O7', 'nyam')   |   372 |    644 |   588 | -162 |         398 |         26 |           46 | False          | False                      |
| ('P7', 'asia')   | 10435 |   5042 |  3897 |  356 |       11710 |       1276 |          575 | False          | False                      |
| ('P7', 'london') |    98 |   1354 |  -714 |  498 |         520 |        422 |          346 | False          | False                      |
| ('P7', 'nyam')   |   405 |     54 |  -644 | -435 |         533 |        128 |          116 | False          | False                      |
| ('U7', 'asia')   |  2237 |    355 |   896 | 1303 |        2454 |        217 |          157 | False          | False                      |
| ('U7', 'london') |  1291 |    105 |   315 | -396 |        1442 |        151 |          114 | False          | False                      |

**Net negative on L6M AND HOLD:** M7 london


#### LPB_BASE (live panel base; state cut ON)

|                  |   L6M |   HOLD |   PRE |    X' |   gross_L6M |   cost_L6M |   trades_L6M | NEG L6M&HOLD   | NEG all 3 (L6M,HOLD,PRE)   |
|:-----------------|------:|-------:|------:|------:|------------:|-----------:|-------------:|:---------------|:---------------------------|
| ('A7', 'asia')   |   542 |    653 |   914 |   243 |         725 |        183 |          355 | False          | False                      |
| ('H7', 'asia')   |  1704 |   -895 |  1375 |    44 |        1854 |        151 |          140 | False          | False                      |
| ('H7', 'nyam')   |   565 |    -22 |    19 |   150 |         594 |         29 |           60 | False          | False                      |
| ('K7', 'asia')   |  2062 |   2065 |  1382 |  -100 |        2508 |        447 |          730 | False          | False                      |
| ('K7', 'london') |  -464 |     88 |   283 |   -98 |        -151 |        313 |          488 | False          | False                      |
| ('K7', 'nyam')   |  -561 |   -761 |   472 |   206 |        -422 |        139 |          261 | True           | False                      |
| ('K7', 'nypm')   |   884 |   -236 |    94 |  -190 |        1017 |        132 |          212 | False          | False                      |
| ('M7', 'london') | -1320 |   -406 |  -280 |   208 |        -868 |        451 |          637 | True           | True                       |
| ('M7', 'nyam')   |   -85 |   -743 |   469 |  -339 |          98 |        183 |          346 | True           | False                      |
| ('O7', 'nyam')   |   375 |    843 |   606 |  -162 |         413 |         38 |           67 | False          | False                      |
| ('P7', 'asia')   |  5784 |   8478 |  2897 | -2144 |        7128 |       1344 |          580 | False          | False                      |
| ('P7', 'london') |  2164 |   2889 |  -526 |  1217 |        2588 |        424 |          339 | False          | False                      |
| ('P7', 'nyam')   |  -904 |  -1656 |   162 |  -265 |        -739 |        165 |          141 | True           | False                      |
| ('U7', 'asia')   |  2295 |    251 |   931 |  1262 |        2512 |        217 |          157 | False          | False                      |
| ('U7', 'london') |   351 |    916 |   390 |  -381 |         538 |        187 |          138 | False          | False                      |

**Net negative on L6M AND HOLD:** K7 nyam, M7 london, M7 nyam, P7 nyam


#### WB_C_NONE (LPB, P7 state cut OFF = live world for P7)

|                  |   L6M |   HOLD |   PRE |    X' |   gross_L6M |   cost_L6M |   trades_L6M | NEG L6M&HOLD   | NEG all 3 (L6M,HOLD,PRE)   |
|:-----------------|------:|-------:|------:|------:|------------:|-----------:|-------------:|:---------------|:---------------------------|
| ('A7', 'asia')   |   685 |    547 |   877 |   278 |         868 |        183 |          356 | False          | False                      |
| ('H7', 'asia')   |  1784 |   -934 |  1378 |   -10 |        1935 |        151 |          140 | False          | False                      |
| ('H7', 'nyam')   |   565 |    -22 |    19 |   150 |         594 |         29 |           60 | False          | False                      |
| ('K7', 'asia')   |  2473 |   1868 |  1395 |   -50 |        2924 |        451 |          738 | False          | False                      |
| ('K7', 'london') |  -480 |   -104 |   315 |  -142 |        -162 |        318 |          500 | True           | False                      |
| ('K7', 'nyam')   |  -725 |   -968 |   440 |   260 |        -582 |        143 |          268 | True           | False                      |
| ('K7', 'nypm')   |   924 |    -87 |   172 |  -108 |        1056 |        132 |          213 | False          | False                      |
| ('M7', 'london') | -1320 |   -414 |  -210 |   231 |        -868 |        451 |          637 | True           | True                       |
| ('M7', 'nyam')   |   -85 |   -743 |   469 |  -339 |          98 |        183 |          346 | True           | False                      |
| ('O7', 'nyam')   |   375 |    843 |   606 |  -162 |         413 |         38 |           67 | False          | False                      |
| ('P7', 'asia')   |  8029 |   7153 |  3683 | -1652 |        9150 |       1121 |          501 | False          | False                      |
| ('P7', 'london') |  2266 |    176 |  -289 |  -239 |        2649 |        383 |          297 | False          | False                      |
| ('P7', 'nyam')   |  -784 |    716 |   438 |   105 |        -638 |        146 |          124 | False          | False                      |
| ('U7', 'asia')   |  2476 |     58 |   975 |  1294 |        2694 |        218 |          158 | False          | False                      |
| ('U7', 'london') |   445 |    916 |   428 |  -355 |         631 |        186 |          137 | False          | False                      |

**Net negative on L6M AND HOLD:** K7 london, K7 nyam, M7 london, M7 nyam


## A. M7

Is M7 a net loser after live costs? Per base, session and window ($/wk): see the table (M7 london / nyam / total; M7 trades, lots per trade; then the stack with and without M7, and with M7 only in one session; stack maxDD = trade-by-trade cumulative net after cost, first-order).


#### JN05W2 (cost-after-edge $/wk; stack maxDD on trade-by-trade cumulative net after cost)

| window | M7 london net/wk | M7 nyam net/wk | M7 total net/wk | M7 trades | M7 lots/trade | stack net/wk | stack net/wk w/o M7 | stack maxDD | maxDD w/o M7 | w/o M7 only nyam | maxDD only nyam | w/o M7 only london | maxDD only london |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | -676 | 281 | -395 | 733 | 1.19 | 20825 | 21220 | 66289 | 65129 | 21501 | 64257 | 20544 | 67160 |
| HOLD | -631 | 53 | -577 | 675 | 1.19 | 8151 | 8728 | 107977 | 102132 | 8781 | 96616 | 8097 | 104839 |
| PRE | -183 | 512 | 329 | 1573 | 1.16 | 7766 | 7437 | 130313 | 119358 | 7949 | 113142 | 7254 | 134785 |
| X' | 204 | -339 | -135 | 654 | 1.17 | 1905 | 2040 | 100180 | 110370 | 1701 | 121070 | 2244 | 91200 |

M7 by session x 30-min slot, L6M+HOLD pooled (n, gross, cost, net $ over 53 weeks)

|                     |   n |   gross |   cost |    net |
|:--------------------|----:|--------:|-------:|-------:|
| ('london', '02:00') | 176 |   15250 |   3185 |  12065 |
| ('london', '02:30') |  71 |    7821 |   1234 |   6587 |
| ('london', '03:00') |  89 |  -10556 |   1605 | -12161 |
| ('london', '03:30') |  72 |    9035 |   1408 |   7627 |
| ('london', '04:00') |  79 |    8242 |   1392 |   6849 |
| ('london', '04:30') |  73 |    5796 |   1411 |   4385 |
| ('london', '05:00') |  73 |   -7012 |   1567 |  -8579 |
| ('london', '05:30') |  51 |   -7888 |    996 |  -8884 |
| ('london', '06:00') |  53 |   -6163 |    987 |  -7150 |
| ('london', '06:30') |  57 |  -24770 |   1206 | -25977 |
| ('london', '07:00') |  70 |   -4549 |   1291 |  -5840 |
| ('london', '07:30') |  48 |    2204 |   1154 |   1050 |
| ('london', '08:00') |  64 |   -3098 |   1514 |  -4612 |
| ('nyam', '10:00')   | 166 |   -6159 |   2408 |  -8567 |
| ('nyam', '10:30')   | 106 |   28355 |   1408 |  26947 |
| ('nyam', '11:00')   |  80 |    5405 |   1124 |   4281 |
| ('nyam', '11:30')   |  80 |  -12493 |   1187 | -13681 |

#### LPB_BASE (cost-after-edge $/wk; stack maxDD on trade-by-trade cumulative net after cost)

| window | M7 london net/wk | M7 nyam net/wk | M7 total net/wk | M7 trades | M7 lots/trade | stack net/wk | stack net/wk w/o M7 | stack maxDD | maxDD w/o M7 | w/o M7 only nyam | maxDD only nyam | w/o M7 only london | maxDD only london |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | -1320 | -85 | -1404 | 983 | 1.17 | 13394 | 14798 | 137023 | 109274 | 14713 | 113879 | 13478 | 133258 |
| HOLD | -407 | -743 | -1150 | 823 | 1.18 | 11463 | 12613 | 129887 | 114927 | 11870 | 121186 | 12206 | 120851 |
| PRE | -279 | 469 | 189 | 1706 | 1.16 | 9189 | 9000 | 157559 | 139175 | 9469 | 140876 | 8720 | 155858 |
| X' | 208 | -339 | -132 | 653 | 1.17 | -348 | -217 | 182334 | 197158 | -556 | 207231 | -9 | 171141 |

M7 by session x 30-min slot, L6M+HOLD pooled (n, gross, cost, net $ over 53 weeks)

|                     |   n |   gross |   cost |    net |
|:--------------------|----:|--------:|-------:|-------:|
| ('london', '02:00') | 179 |   14191 |   3230 |  10961 |
| ('london', '02:30') |  76 |    7861 |   1305 |   6555 |
| ('london', '03:00') |  96 |  -15674 |   1800 | -17474 |
| ('london', '03:30') |  79 |    4330 |   1558 |   2772 |
| ('london', '04:00') |  97 |    2232 |   1719 |    512 |
| ('london', '04:30') |  80 |    3104 |   1536 |   1568 |
| ('london', '05:00') |  83 |   -1057 |   1730 |  -2787 |
| ('london', '05:30') |  65 |   -1018 |   1274 |  -2292 |
| ('london', '06:00') |  66 |  -10264 |   1262 | -11527 |
| ('london', '06:30') |  68 |  -25424 |   1411 | -26835 |
| ('london', '07:00') |  93 |   -3231 |   1659 |  -4890 |
| ('london', '07:30') |  81 |    2338 |   1845 |    492 |
| ('london', '08:00') |  94 |    -997 |   2259 |  -3256 |
| ('nyam', '10:00')   | 230 |  -11730 |   3337 | -15067 |
| ('nyam', '10:30')   | 163 |   13932 |   2285 |  11646 |
| ('nyam', '11:00')   | 127 |    5175 |   1800 |   3374 |
| ('nyam', '11:30')   | 129 |  -19632 |   1923 | -21555 |

#### JN05W2J (cost-after-edge $/wk; stack maxDD on trade-by-trade cumulative net after cost)

| window | M7 london net/wk | M7 nyam net/wk | M7 total net/wk | M7 trades | M7 lots/trade | stack net/wk | stack net/wk w/o M7 | stack maxDD | maxDD w/o M7 | w/o M7 only nyam | maxDD only nyam | w/o M7 only london | maxDD only london |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L6M | -1009 | 325 | -684 | 719 | 1.12 | 17716 | 18401 | 42832 | 41626 | 18725 | 40283 | 17392 | 44152 |
| HOLD | -582 | 443 | -139 | 662 | 1.13 | 6518 | 6657 | 96108 | 93284 | 7100 | 90786 | 6075 | 98888 |
| PRE | -775 | 484 | -291 | 1533 | 1.10 | 5402 | 5693 | 91692 | 79649 | 6177 | 77688 | 4918 | 91245 |
| X' | 144 | -365 | -221 | 639 | 1.13 | 2462 | 2682 | 66539 | 74556 | 2318 | 80531 | 2826 | 62082 |

M7 by session x 30-min slot, L6M+HOLD pooled (n, gross, cost, net $ over 53 weeks)

|                     |   n |   gross |   cost |    net |
|:--------------------|----:|--------:|-------:|-------:|
| ('london', '02:00') | 141 |   16473 |   2232 |  14241 |
| ('london', '02:30') |  66 |    7123 |   1190 |   5933 |
| ('london', '03:00') |  99 |   -7809 |   1733 |  -9542 |
| ('london', '03:30') |  70 |     876 |   1156 |   -280 |
| ('london', '04:00') |  77 |   14054 |   1315 |  12739 |
| ('london', '04:30') |  72 |    1730 |   1295 |    434 |
| ('london', '05:00') |  68 |   -8614 |   1348 |  -9962 |
| ('london', '05:30') |  54 |   -7486 |    979 |  -8466 |
| ('london', '06:00') |  52 |   -8361 |    913 |  -9274 |
| ('london', '06:30') |  58 |  -21974 |   1109 | -23083 |
| ('london', '07:00') |  68 |   -3892 |   1219 |  -5111 |
| ('london', '07:30') |  52 |    6711 |   1067 |   5644 |
| ('london', '08:00') |  63 |  -14129 |   1529 | -15658 |
| ('nyam', '10:00')   | 169 |   -6842 |   2452 |  -9294 |
| ('nyam', '10:30')   | 107 |   33859 |   1400 |  32459 |
| ('nyam', '11:00')   |  83 |    9180 |   1152 |   8028 |
| ('nyam', '11:30')   |  82 |   -9690 |   1206 | -10896 |

#### A.4 Entry filter screen (family null + placebo)

413 cells (128 W-I causal features x 33/50/67th-percentile thresholds fitted on PRE+X' only x skip-above/skip-below) scored OUT OF SAMPLE on HOLD+L6M after cost; consistent = also > 0 on PRE. Placebo = random removal of the same count. Family null = within-month permutation of every feature (200 perms), max OOS gain.

```
cells 413 consistent 82 best_oos_gain_wk 1304 family_null_q95 1593 family_p 0.525
            feat   q   dirn  n_oos  gain_oos_wk  gain_pre_wk  cons  placebo_p
208      ZN_r60m  67  below    872       1224.0        599.3  True        0.0
189    nq_sess_r  67  above    490       1107.6        296.3  True        0.0
256       et_min  67  below   1048        966.0         12.3  True        0.0
227      6J_r60m  33  above   1147        906.6         31.5  True        0.1
233       risk30  33  above    757        839.1         90.6  True        0.1
185    nq_sess_r  33  above    980        827.2         53.2  True        0.1
239       risk60  33  above    666        785.0        217.5  True        0.1
250      et_hour  67  below    976        666.2        183.0  True        0.2
200      ZN_r30m  50  below    528        647.9        115.1  True        0.1
49   room_struct  67  above    656        640.2         47.5  True        0.2
```

Reading: see section R below.


## B. P7 Asia by 30-min ET entry slot after costs (net $/wk), state cut ON vs OFF


#### LPB_BASE cut ON

| slot   |   L6M net/wk |   HOLD net/wk |   PRE net/wk |   X' net/wk |   L6M trades |   L6M lots | pays L6M&HOLD&PRE   |
|:-------|-------------:|--------------:|-------------:|------------:|-------------:|-----------:|:--------------------|
| 00:00  |          654 |          -400 |         -165 |         189 |           28 |        127 | False               |
| 00:30  |         2100 |          1179 |          259 |         297 |           23 |        111 | True                |
| 01:00  |          456 |           -61 |          436 |         410 |           30 |        138 | False               |
| 01:30  |          614 |          -357 |          172 |         474 |           21 |         97 | False               |
| 18:00  |          412 |         -1057 |         1760 |       -2452 |           59 |        261 | False               |
| 18:30  |         1855 |          2039 |         -494 |        -851 |           56 |        257 | False               |
| 19:00  |         1634 |           367 |          768 |         708 |           34 |        167 | True                |
| 19:30  |        -1625 |          1276 |          136 |        -207 |           38 |        176 | False               |
| 20:00  |         -206 |          1944 |          108 |          86 |           55 |        233 | False               |
| 20:30  |        -1222 |           528 |          603 |        -135 |           50 |        218 | False               |
| 21:00  |         1476 |          1155 |          651 |         190 |           42 |        178 | True                |
| 21:30  |         -241 |             9 |          237 |        -141 |           37 |        171 | False               |
| 22:00  |         -474 |          1604 |        -1094 |        -364 |           43 |        175 | False               |
| 22:30  |         1136 |          -320 |         -246 |        -345 |           24 |        113 | False               |
| 23:00  |         -574 |          1077 |         -570 |         -52 |           19 |         96 | False               |
| 23:30  |         -211 |          -505 |          334 |          49 |           21 |         96 | False               |

Slots that pay on L6M, HOLD and PRE: 00:30, 19:00, 21:00


#### WB_C_NONE cut OFF (live world)

| slot   |   L6M net/wk |   HOLD net/wk |   PRE net/wk |   X' net/wk |   L6M trades |   L6M lots | pays L6M&HOLD&PRE   |
|:-------|-------------:|--------------:|-------------:|------------:|-------------:|-----------:|:--------------------|
| 00:00  |          969 |            30 |           15 |         189 |           19 |         97 | True                |
| 00:30  |         1883 |          1148 |          283 |         297 |           21 |         99 | True                |
| 01:00  |         2136 |           717 |          328 |        -110 |           27 |        128 | True                |
| 01:30  |          776 |           469 |          -52 |         382 |           16 |         74 | False               |
| 18:00  |          231 |         -1031 |         1814 |       -2116 |           59 |        261 | False               |
| 18:30  |         2391 |          1177 |           78 |        -965 |           53 |        248 | True                |
| 19:00  |         1252 |           510 |         1207 |        1191 |           31 |        153 | True                |
| 19:30  |        -1896 |          1634 |          -21 |        -209 |           30 |        137 | False               |
| 20:00  |          126 |          1127 |           74 |        -194 |           42 |        171 | True                |
| 20:30  |        -1248 |             0 |          576 |         246 |           44 |        193 | False               |
| 21:00  |          843 |          1480 |           50 |        -192 |           34 |        145 | True                |
| 21:30  |        -1560 |          -179 |          336 |          64 |           32 |        141 | False               |
| 22:00  |          362 |          -622 |         -808 |         350 |           37 |        151 | False               |
| 22:30  |         1584 |          -315 |         -534 |        -210 |           21 |         97 | False               |
| 23:00  |          452 |          1280 |           13 |        -193 |           20 |         92 | True                |
| 23:30  |         -272 |          -272 |          324 |        -184 |           15 |         75 | False               |

Slots that pay on L6M, HOLD and PRE: 00:00, 00:30, 01:00, 18:30, 19:00, 20:00, 21:00, 23:00


#### JN05W2 cut ON

| slot   |   L6M net/wk |   HOLD net/wk |   PRE net/wk |   X' net/wk |   L6M trades |   L6M lots | pays L6M&HOLD&PRE   |
|:-------|-------------:|--------------:|-------------:|------------:|-------------:|-----------:|:--------------------|
| 00:00  |         1874 |            54 |          354 |         189 |           33 |        155 | True                |
| 00:30  |         2240 |           333 |          413 |         297 |           23 |        103 | True                |
| 01:00  |         1204 |          -492 |           13 |         195 |           25 |        108 | False               |
| 01:30  |          184 |           924 |          106 |         -93 |           21 |        102 | True                |
| 18:00  |         1339 |           265 |         1104 |         486 |           25 |         94 | True                |
| 18:30  |          733 |            -5 |         -173 |       -1338 |           59 |        264 | False               |
| 19:00  |         2106 |           442 |          539 |         791 |           49 |        218 | True                |
| 19:30  |         -632 |           409 |          676 |        -220 |           28 |        115 | False               |
| 20:00  |         -690 |           -98 |          453 |         -23 |           44 |        159 | False               |
| 20:30  |           24 |          -704 |          211 |        -203 |           50 |        217 | False               |
| 21:00  |         1498 |           948 |          561 |         121 |           47 |        193 | True                |
| 21:30  |         -655 |          1491 |          358 |         160 |           36 |        161 | False               |
| 22:00  |         -816 |          1537 |         -372 |         113 |           46 |        190 | False               |
| 22:30  |         1739 |           114 |          265 |        -127 |           37 |        153 | True                |
| 23:00  |          852 |           197 |         -972 |         -18 |           27 |        130 | False               |
| 23:30  |         -566 |          -374 |          360 |          25 |           25 |        110 | False               |

Slots that pay on L6M, HOLD and PRE: 00:00, 00:30, 01:30, 18:00, 19:00, 21:00, 22:30


#### B.4 12/7/4/0 slot tables, FIRST-ORDER (lot scaling of the trade list; placebo = random tier permutation of the PRE-fit table, 500 draws)

|    | base    | win   | table   |   dnet_wk |   dd_base |   dd_new |   p7asia_lots_ratio |   dd_cut_pct |   placebo_p_dnet |
|---:|:--------|:------|:--------|----------:|----------:|---------:|--------------------:|-------------:|-----------------:|
|  0 | JN05W2  | L6M   | pre     |   1540.12 |   66288.7 |  53834.5 |                0.81 |        18.79 |             0.22 |
|  1 | JN05W2  | L6M   | bw      |   2016.57 |   66288.7 |  50267.2 |                0.77 |        24.17 |           nan    |
|  2 | JN05W2  | L6M   | bwd     |  -2542.99 |   66288.7 |  48890.4 |                0.47 |        26.25 |           nan    |
|  3 | JN05W2  | HOLD  | pre     |   -975.18 |  107977   | 121078   |                0.84 |       -12.13 |             0.6  |
|  4 | JN05W2  | HOLD  | bw      |  -3511.77 |  107977   | 122349   |                0.91 |       -13.31 |           nan    |
|  5 | JN05W2  | HOLD  | bwd     |  -3430.18 |  107977   | 117712   |                0.64 |        -9.02 |           nan    |
|  6 | JN05W2  | PRE   | pre     |   3026.68 |  130313   | 133571   |                0.76 |        -2.5  |           nan    |
|  7 | JN05W2  | PRE   | bw      |     -6.03 |  130313   | 144495   |                0.87 |       -10.88 |           nan    |
|  8 | JN05W2  | PRE   | bwd     |  -1035.08 |  130313   | 141117   |                0.69 |        -8.29 |           nan    |
|  9 | JN05W2  | X'    | pre     |   1801.32 |  100180   |  97332.3 |                0.69 |         2.84 |           nan    |
| 10 | JN05W2  | X'    | bw      |   -528.14 |  100180   | 100180   |                0.92 |         0    |           nan    |
| 11 | JN05W2  | X'    | bwd     |   -651.78 |  100180   | 100180   |                0.85 |         0    |           nan    |
| 12 | JN05W2J | L6M   | pre     |  -1702.67 |   42831.7 |  40261.4 |                0.87 |         6    |           nan    |
| 13 | JN05W2J | L6M   | bw      |    621.29 |   42831.7 |  46679.6 |                0.83 |        -8.98 |           nan    |
| 14 | JN05W2J | L6M   | bwd     |  -3369.53 |   42831.7 |  51581.4 |                0.49 |       -20.43 |           nan    |
| 15 | JN05W2J | HOLD  | pre     |    -77.1  |   96108.4 | 105755   |                0.85 |       -10.04 |           nan    |
| 16 | JN05W2J | HOLD  | bw      |   -996.63 |   96108.4 |  99198.1 |                0.94 |        -3.21 |           nan    |
| 17 | JN05W2J | HOLD  | bwd     |  -1537.29 |   96108.4 |  96281.7 |                0.66 |        -0.18 |           nan    |
| 18 | JN05W2J | PRE   | pre     |   1641.22 |   91691.8 |  96940.2 |                0.76 |        -5.72 |           nan    |
| 19 | JN05W2J | PRE   | bw      |   -790.66 |   91691.8 | 105268   |                0.82 |       -14.81 |           nan    |
| 20 | JN05W2J | PRE   | bwd     |   -947.42 |   91691.8 | 105117   |                0.66 |       -14.64 |           nan    |
| 21 | JN05W2J | X'    | pre     |   1265.06 |   66538.6 |  61105.5 |                0.57 |         8.17 |           nan    |
| 22 | JN05W2J | X'    | bw      |    359.69 |   66538.6 |  66538.6 |                0.9  |         0    |           nan    |
| 23 | JN05W2J | X'    | bwd     |    208.61 |   66538.6 |  66538.6 |                0.84 |         0    |           nan    |

## R. Readings

### Readings (W-G2, trade-list tables; exact rows in section E decide)

**A.5 M7.** After live costs M7 is a net loser on the live-panel base: LPB_BASE L6M -$1,404/wk (london -1,320, nyam -85), HOLD -$1,150/wk (london -407, nyam -743), PRE +$189, X' -$132. On JN05W2 (state cut ON, five layers) it is -$395/wk L6M, -$577 HOLD, +$329 PRE, -$135 X'; the whole loss is **London** (-676 / -631 / -183 / +204 per wk on L6M / HOLD / PRE / X'); **NY-AM** is +281 / +53 / +512 / -339. First-order stack effects (no path change): without M7 on LPB_BASE the stack gains +$1,404/wk (L6M) and +$1,150/wk (HOLD) and maxDD falls 137.0k -> 109.3k (-20 %) and 129.9k -> 114.9k (-12 %); on JN05W2 +$395 / +$577 per wk with maxDD -1.7 % / -5.4 % (PRE -$329/wk, maxDD -8 %). M7 only in NY-AM on JN05W2: L6M +$676/wk, maxDD 66.3k -> 64.3k (-3 %); HOLD +$630/wk, 108.0k -> 96.6k (-11 %); PRE +$183/wk, 130.3k -> 113.1k (-13 %); X' -$204/wk and maxDD +21 % worse. M7 at 1-2 lots: the panel M7 sizes are already 1.2 lots/trade, so M7_HALF is a pure min-1-lot rounding test (exact set G2_M7_HALF). **No M7 entry filter makes it pay on the family null:** 413 cells, best out-of-sample gain +$1,304/wk vs family-null q95 +$1,593/wk (p 0.53); the cells with the largest gain skip 50-85 % of M7 trades, i.e. they are size dials (ZN 60-min return, NQ session range, ET minute, risk).

**B.5 P7 Asia by slot.** Slot results are unstable. Slots paying on L6M, HOLD and PRE: LPB_BASE (cut ON) 00:30, 19:00, 21:00; WB_C_NONE (cut OFF, live world) 00:00, 00:30, 01:00, 18:30, 19:00, 20:00, 21:00, 23:00; JN05W2 00:00, 00:30, 01:30, 18:00, 19:00, 21:00, 22:30 - only **00:30, 19:00 and 21:00 pay in all three**. With the cut OFF the clear L6M losers are 19:30 (-$1,896/wk), 20:30 (-1,248), 21:30 (-1,560) and 23:30 (-272), but HOLD is positive at 19:30 (+1,634) so none is a stable dead hour. First-order, the 12/7/4/0 tables fail: PRE-fit table +$1,540/wk and -18.8 % maxDD on L6M but -$975/wk and +12 % worse on HOLD, placebo p 0.22 (L6M) / 0.60 (HOLD); bi-weekly 12/7/4/0 +$2,017 L6M, -$3,512 HOLD. Treat the slot tables as noise unless the exact rows say otherwise.

**C.5 Net negative on L6M AND HOLD** (after live costs): JN05W2: M7 london. LPB_BASE (live panel base): K7 nyam, M7 london, M7 nyam, P7 nyam. WB_C_NONE (P7 cut OFF): K7 london, K7 nyam, M7 london, M7 nyam. Common to the live-realistic views: **M7 london, M7 nyam (on LPB), K7 nyam**. M7 costs about $494/wk of fees+slip on L6M for $84/wk gross on the base list (W-SM4 audit); K7 london runs 62 % cost/gross.


## E. Exact rows (JN05W2 / JN05W2J bases, one set per job; scored vs the base on the same months by score_nf.py: all-weeks d mean, maxDD cut, trend-week clause, same-side run, WF at 43 months)

Identity checks: PASS G2_ID: 598 trades net 25943.82 vs JN05W2 598 trades net 25943.82 | PASS G2J_ID: 658 trades net 23596.16 vs JN05W2J 658 trades net 23596.16 | PASS G2N_ID: 574 trades net 15110.42 vs JN05W2_NOCUT 574 trades net 15110.42 | PASS G2JN_ID: 590 trades net -2703.40 vs JN05W2J_NOCUT 590 trades net -2703.40

| set          | base          |   months | identity   | L6M cut%/dmean_all   | HOLD cut%/dmean_all   | trend 5best (ref->cell), winning wks turned losing   | run max/p95 (ref)   | promote           | acceptance_p7                       | PRE cut%/dmean_all   | X' cut%/dmean_all   | WF beat%/cut/mean   |
|:-------------|:--------------|---------:|:-----------|:---------------------|:----------------------|:-----------------------------------------------------|:--------------------|:------------------|:------------------------------------|:---------------------|:--------------------|:--------------------|
| G2_M7_OFF    | JN05W2        |       12 | PASS       | -8.7 / -587          | 28.0 / -21            | 316k -> 312k, 0 of 20                                | 13/5.0 (13/6.0)     | no (stage 1 only) | ACCEPT G2_M7_OFF PASS fails=1/20    | nan                  | nan                 | nan                 |
| G2_M7_NYAM   | JN05W2        |       12 | PASS       | -8.0 / -1178         | 25.7 / -315           | 316k -> 316k, 1 of 20                                | 13/5.1 (13/6.0)     | no (stage 1 only) | ACCEPT G2_M7_NYAM PASS fails=1/20   | nan                  | nan                 | nan                 |
| G2_M7_LON    | JN05W2        |       12 | PASS       | -4.9 / -676          | 2.1 / -114            | 316k -> 311k, 0 of 20                                | 13/6.0 (13/6.0)     | no (stage 1 only) | ACCEPT G2_M7_LON PASS fails=1/20    | nan                  | nan                 | nan                 |
| G2_M7_HALF   | JN05W2        |       12 | PASS       | 1.7 / -178           | 14.2 / +314           | 316k -> 322k, 0 of 20                                | 13/6.0 (13/6.0)     | no (stage 1 only) | ACCEPT G2_M7_HALF PASS fails=1/20   | nan                  | nan                 | nan                 |
| G2_P7A_PRE   | JN05W2        |       43 | PASS       | 32.2 / +2636         | 13.9 / +956           | 316k -> 241k, 0 of 20                                | 12/6.0 (13/6.0)     | YES               | ACCEPT G2_P7A_PRE FAIL fails=3/20   | -14.6 / -361         | -10.8 / +1022       | 22 / -23.1 / -326   |
| G2_P7A_BW    | JN05W2        |       12 | PASS       | 16.1 / +602          | -29.6 / -2770         | 316k -> 308k, 2 of 20                                | 13/6.0 (13/6.0)     | no (stage 1 only) | ACCEPT G2_P7A_BW PASS fails=1/20    | nan                  | nan                 | nan                 |
| G2_P7A_BWD   | JN05W2        |       12 | PASS       | 22.2 / -1874         | -21.8 / -2331         | 316k -> 243k, 3 of 20                                | 13/6.0 (13/6.0)     | no (stage 1 only) | ACCEPT G2_P7A_BWD PASS fails=1/20   | nan                  | nan                 | nan                 |
| G2J_M7_OFF   | JN05W2J       |       43 | PASS       | 20.7 / -345          | 27.2 / -186           | 244k -> 236k, 0 of 21                                | 14/5.0 (14/6.0)     | YES               | ACCEPT G2J_M7_OFF PASS fails=1/20   | 8.9 / +20            | -41.4 / +233        | 63 / 8.9 / -0       |
| G2J_M7_NYAM  | JN05W2J       |       43 | PASS       | 15.2 / -257          | 17.4 / -260           | 244k -> 238k, 0 of 21                                | 14/6.0 (14/6.0)     | YES               | ACCEPT G2J_M7_NYAM PASS fails=1/20  | 13.4 / +641          | -32.7 / +29         | 35 / 13.4 / +197    |
| G2J_M7_LON   | JN05W2J       |       43 | PASS       | 5.5 / -528           | 6.7 / -494            | 244k -> 241k, 0 of 21                                | 14/6.0 (14/6.0)     | YES               | ACCEPT G2J_M7_LON PASS fails=1/20   | -3.6 / -648          | 2.0 / +309          | 44 / -3.6 / -223    |
| G2J_M7_HALF  | JN05W2J       |       43 | PASS       | 5.1 / +490           | 12.6 / +347           | 244k -> 248k, 0 of 21                                | 14/6.0 (14/6.0)     | YES               | ACCEPT G2J_M7_HALF PASS fails=1/20  | -2.3 / +230          | -12.4 / +107        | 49 / -2.3 / +170    |
| G2J_P7A_PRE  | JN05W2J       |       43 | PASS       | 60.4 / -1294         | -18.1 / -476          | 244k -> 187k, 0 of 21                                | 11/6.0 (14/6.0)     | YES               | ACCEPT G2J_P7A_PRE FAIL fails=3/20  | -13.1 / -1488        | 11.3 / -161         | 6 / 0.0 / -221      |
| G2J_P7A_BW   | JN05W2J       |       12 | PASS       | 14.2 / +246          | -49.8 / -2007         | 244k -> 222k, 2 of 21                                | 10/6.0 (14/6.0)     | no (stage 1 only) | ACCEPT G2J_P7A_BW PASS fails=1/20   | nan                  | nan                 | nan                 |
| G2J_P7A_BWD  | JN05W2J       |       12 | PASS       | -12.7 / -4494        | -29.3 / -4200         | 244k -> 197k, 1 of 21                                | 10/6.0 (14/6.0)     | no (stage 1 only) | ACCEPT G2J_P7A_BWD PASS fails=2/20  | nan                  | nan                 | nan                 |
| G2N_M7_OFF   | JN05W2_NOCUT  |       43 | PASS       | -9.2 / +62           | 9.9 / +551            | 309k -> 274k, 0 of 19                                | 10/4.0 (10/5.0)     | YES               | ACCEPT G2N_M7_OFF PASS fails=1/20   | 25.5 / -846          | -3.9 / -181         | 63 / 12.3 / -500    |
| G2N_M7_NYAM  | JN05W2_NOCUT  |       12 | PASS       | -10.1 / -364         | -0.1 / +388           | 309k -> 291k, 0 of 19                                | 10/5.0 (10/5.0)     | no (stage 1 only) | ACCEPT G2N_M7_NYAM PASS fails=1/20  | nan                  | nan                 | nan                 |
| G2N_M7_LON   | JN05W2_NOCUT  |       12 | PASS       | 3.2 / -64            | 11.2 / +18            | 309k -> 296k, 0 of 19                                | 10/5.0 (10/5.0)     | no (stage 1 only) | ACCEPT G2N_M7_LON PASS fails=1/20   | nan                  | nan                 | nan                 |
| G2N_M7_HALF  | JN05W2_NOCUT  |       12 | PASS       | 4.3 / -214           | 5.1 / +167            | 309k -> 300k, 0 of 19                                | 10/5.0 (10/5.0)     | no (stage 1 only) | ACCEPT G2N_M7_HALF PASS fails=1/20  | nan                  | nan                 | nan                 |
| G2N_P7A_PRE  | JN05W2_NOCUT  |       12 | PASS       | -12.4 / -3388        | 26.9 / -1296          | 309k -> 266k, 1 of 19                                | 9/5.0 (10/5.0)      | no (stage 1 only) | ACCEPT G2N_P7A_PRE PASS fails=0/20  | nan                  | nan                 | nan                 |
| G2N_P7A_BW   | JN05W2_NOCUT  |       43 | PASS       | 11.6 / +9044         | 17.3 / +5632          | 309k -> 318k, 1 of 19                                | 11/5.0 (10/5.0)     | YES               | ACCEPT G2N_P7A_BW PASS fails=0/20   | -14.9 / -2123        | 0.0 / +895          | 38 / 0.0 / +1496    |
| G2N_P7A_BWD  | JN05W2_NOCUT  |       43 | PASS       | 6.1 / +3351          | 3.7 / +2129           | 309k -> 282k, 1 of 19                                | 11/5.0 (10/5.0)     | YES               | ACCEPT G2N_P7A_BWD PASS fails=0/20  | 8.5 / -1862          | 0.0 / +477          | 30 / -14.3 / -663   |
| G2JN_M7_OFF  | JN05W2J_NOCUT |       43 | PASS       | 19.2 / +2090         | -4.4 / +885           | 249k -> 205k, 0 of 18                                | 10/4.0 (10/5.0)     | YES               | ACCEPT G2JN_M7_OFF PASS fails=1/20  | 12.0 / -30           | -28.2 / -49         | 37 / -4.4 / +39     |
| G2JN_M7_NYAM | JN05W2J_NOCUT |       43 | PASS       | 14.8 / +1786         | 3.3 / +919            | 249k -> 226k, 0 of 18                                | 10/5.0 (10/5.0)     | YES               | ACCEPT G2JN_M7_NYAM PASS fails=1/20 | 4.6 / +685           | -14.5 / -151        | 39 / 0.0 / +698     |
| G2JN_M7_LON  | JN05W2J_NOCUT |       12 | PASS       | 4.5 / -33            | 7.3 / -185            | 249k -> 235k, 0 of 18                                | 10/5.0 (10/5.0)     | no (stage 1 only) | ACCEPT G2JN_M7_LON PASS fails=1/20  | nan                  | nan                 | nan                 |
| G2JN_M7_HALF | JN05W2J_NOCUT |       43 | PASS       | -3.9 / +1211         | 15.0 / +1096          | 249k -> 242k, 0 of 18                                | 10/5.0 (10/5.0)     | YES               | ACCEPT G2JN_M7_HALF PASS fails=1/20 | 7.9 / +176           | 0.7 / +23           | 37 / 0.0 / +260     |
| G2JN_P7A_PRE | JN05W2J_NOCUT |       12 | PASS       | -36.3 / -1270        | 26.9 / -474           | 249k -> 220k, 0 of 18                                | 10/5.0 (10/5.0)     | no (stage 1 only) | ACCEPT G2JN_P7A_PRE PASS fails=2/20 | nan                  | nan                 | nan                 |
| G2JN_P7A_BW  | JN05W2J_NOCUT |       43 | PASS       | 3.9 / +4559          | 14.2 / +2835          | 249k -> 267k, 0 of 18                                | 10/5.0 (10/5.0)     | YES               | ACCEPT G2JN_P7A_BW FAIL fails=3/20  | -14.0 / -424         | 0.0 / +110          | 34 / 14.2 / +1234   |
| G2JN_P7A_BWD | JN05W2J_NOCUT |       43 | PASS       | -9.1 / +203          | 21.2 / +953           | 249k -> 235k, 1 of 18                                | 10/5.0 (10/5.0)     | YES               | ACCEPT G2JN_P7A_BWD FAIL fails=3/20 | -23.7 / -359         | 0.0 / +224          | 30 / 0.0 / +76      |