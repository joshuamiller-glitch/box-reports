# DS3_JOINT_V20 - joint of the shelved candidates on JN05W2 (PRIORITY 4) - W-JV

VERDICT (5 of 5 windows complete for the leader): best joint set so far is JV_B: worst-window max-DD cut -1.0 % vs JN05W2, mean 555 $/wk avg; passes the tolerant gate in every complete window. Recent max DD is the single week 2026-W44, so read section 2 and section 5 before believing any recent cut. Strength: weak - see 6b (C rejected, A recent-only, D pending older windows); no PASS claim.

Generated 2026-11-16 15:57 UTC (epoch 1794844665). Exact engine (TP), base JN05W2 = live panel + F3 + E1 + C22 + BR3S + FLAT45K, all layers ON, measured fills (engine slip 0.8; structure stop 1.4 adverse). LOT/FEE BASIS: base lots (user lots are x1.75, so multiply every $ by 1.75); the engine charges $1.18 per contract round trip inside net_fee (what every table sums); the column d mean @4.84 reprices the change in mean at $4.84 RT per contract using the change in contracts traded (d mean - 3.66 x change in lots/wk), no rerun. Shadow only, no PASS claim. Prereg autopilot/JOINTV20_PREREG.md (sha in DECISIONS.md).

Candidates: **A** = SM_A6_halfNP7 (first trade of a book-session lost -> later signals of that book-session at half lots, books K7 M7 U7 H7 A7; P7 untouched). **B** = U7 time stop on fresh entries (at 15:00 after the first fill, if open P&L < -10 pts: market exit, fresh context only). **C** = U7 Keltner-mid structure stop (stop at 5-min EMA20 mid - 2 pts, filled 1.4 pt adverse, lots x 60/stop distance clamped 25..60). Full specs in section 6.

Identity: TL3_JV_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

**DD basis, shown both ways in every table: WEEKLY = max drawdown of the cumulative weekly P&L series (program convention, DS3_JOINT_V20 / jv_score, DS3_V20_BUILD_LIST; the max DD of a recent window is the single week W44). DAILY = max drawdown of cumulative daily P&L by Globex label day (used by W-LR lr_score, W-RU ru_score, W-CH ch_score, W-RA ra pages). Same trades, different basis: a rule can change sign between them (London LS1 HOLD: +13.6 % daily, -3.7 % weekly).**

## 1. Drawdown first: all combinations vs JN05W2 (cut % = max-DD of the weekly series vs JN05W2, + = shallower; worst wk d = change of the worst week; stops/wk; 5 best JN05W2 weeks kept; winning weeks turned losing; d mean $/wk)

### L1M

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 4 | 32090 | 36371 | 11.8 | 8.2 | -32090 | 4280 | 13.8 (13.2) | - | 0 (2) | -1561 | -2168 | -2148 |
| JV_B | 4 | 31572 | 36371 | 13.2 | 9.2 | -31572 | 4799 | 12.0 (13.2) | - | 0 (2) | 3190 | 2584 | 2583 |
| JV_C | 4 | 35985 | 36371 | 1.1 | 0.7 | -35985 | 385 | 11.0 (13.2) | - | 0 (2) | 2962 | 2356 | 2327 |
| JV_AB | 4 | 27291 | 36371 | 25.0 | 17.4 | -27291 | 9079 | 12.2 (13.2) | - | 0 (2) | 849 | 242 | 261 |
| JV_AC | 4 | 31705 | 36371 | 12.8 | 8.9 | -31705 | 4666 | 11.0 (13.2) | - | 0 (2) | 2468 | 1861 | 1859 |
| JV_BC | 4 | 32311 | 36371 | 11.2 | 7.8 | -32311 | 4059 | 10.5 (13.2) | - | 0 (2) | 4757 | 4150 | 4127 |
| JV_ABC | 4 | 28031 | 36371 | 22.9 | 16.0 | -28031 | 8340 | 10.8 (13.2) | - | 0 (2) | 3627 | 3021 | 3018 |
| JV_ABF | 4 | 21764 | 36371 | 40.2 | 27.7 | -21764 | 14607 | 6.2 (13.2) | - | 0 (2) | 7047 | 6441 | 6439 |
| JV_DV | 4 | 29031 | 36371 | 20.2 | 5.5 | -29031 | 7339 | 13.0 (13.2) | - | 0 (2) | 6474 | 5868 | 5896 |
| JV_AR | 4 | 32184 | 36371 | 11.5 | 5.6 | -32184 | 4187 | 13.8 (13.2) | - | 0 (2) | 693 | 86 | 124 |
| JV_BR | 4 | 31665 | 36371 | 12.9 | 6.6 | -31665 | 4705 | 12.0 (13.2) | - | 0 (2) | 4854 | 4248 | 4264 |
| JV_BD | 4 | 24653 | 36371 | 32.2 | 13.9 | -24653 | 11718 | 11.2 (13.2) | - | 0 (2) | 9035 | 8428 | 8451 |
| JV_F | 4 | 30843 | 36371 | 15.2 | 10.3 | -30843 | 5527 | 7.2 (13.2) | - | 0 (2) | 6428 | 5821 | 5800 |
| JV_T | 4 | 36371 | 36371 | 0.0 | 0.0 | -36371 | 0 | 13.0 (13.2) | - | 0 (2) | 2583 | 1977 | 1962 |
| JV_R | 4 | 36464 | 36371 | -0.3 | -2.6 | -36464 | -94 | 13.2 (13.2) | - | 0 (2) | 2466 | 1860 | 1878 |
| JV_P | 4 | 25139 | 36371 | 30.9 | 28.6 | -25139 | 11232 | 13.2 (13.2) | - | 0 (2) | 4308 | 3701 | 3687 |
| JV_V | 4 | 35774 | 36371 | 1.6 | -1.6 | -35774 | 596 | 13.8 (13.2) | - | 0 (2) | 434 | -172 | -157 |
| JV_D | 4 | 29452 | 36371 | 19.0 | 4.7 | -29452 | 6919 | 12.5 (13.2) | - | 0 (2) | 6969 | 6362 | 6386 |
| JV_BF | 4 | 26044 | 36371 | 28.4 | 19.5 | -26044 | 10326 | 6.0 (13.2) | - | 0 (2) | 8487 | 7881 | 7855 |
| JV_BP | 4 | 20340 | 36371 | 44.1 | 37.8 | -20340 | 16031 | 12.0 (13.2) | - | 0 (2) | 6341 | 5734 | 5716 |
| JV_BV | 4 | 30975 | 36371 | 14.8 | 7.6 | -30975 | 5395 | 12.5 (13.2) | - | 0 (2) | 3018 | 2411 | 2426 |
| JV_ABD | 4 | 22946 | 36371 | 36.9 | 17.2 | -22946 | 13424 | 11.8 (13.2) | - | 0 (2) | 8165 | 7559 | 7605 |
| JV_AD | 4 | 27745 | 36371 | 23.7 | 8.0 | -27745 | 8625 | 13.0 (13.2) | - | 0 (2) | 5852 | 5245 | 5292 |
| JV_DP | 4 | 20618 | 36371 | 43.3 | 37.3 | -20618 | 15752 | 12.5 (13.2) | - | 0 (2) | 10334 | 9728 | 9735 |
| JV_DR | 4 | 29721 | 36371 | 18.3 | 4.2 | -29721 | 6649 | 12.5 (13.2) | - | 0 (2) | 6901 | 6295 | 6323 |
| JV_PR | 4 | 25233 | 36371 | 30.6 | 28.4 | -25233 | 11138 | 13.2 (13.2) | - | 0 (2) | 6291 | 5685 | 5687 |
| JV_PV | 4 | 25865 | 36371 | 28.9 | 27.2 | -25865 | 10506 | 13.8 (13.2) | - | 0 (2) | 4158 | 3551 | 3550 |
| JV_AP | 4 | 20858 | 36371 | 42.7 | 29.7 | -20858 | 15512 | 13.8 (13.2) | - | 0 (2) | 1589 | 983 | 989 |
| JV_AV | 4 | 31494 | 36371 | 13.4 | 6.6 | -31494 | 4877 | 14.2 (13.2) | - | 0 (2) | -1714 | -2320 | -2287 |
| JV_BT | 4 | 31572 | 36371 | 13.2 | 9.2 | -31572 | 4799 | 11.8 (13.2) | - | 0 (2) | 5167 | 4560 | 4545 |

### L3M

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 13 | 32090 | 36371 | 11.8 | 8.2 | -32090 | 4280 | 10.6 (10.5) | 94% | 0 (9) | 15324 | -691 | -678 |
| JV_B | 13 | 32117 | 36371 | 11.7 | 9.2 | -31572 | 4799 | 9.5 (10.5) | 106% | 0 (9) | 17259 | 1244 | 1243 |
| JV_C | 13 | 35985 | 36371 | 1.1 | 0.7 | -35985 | 385 | 8.1 (10.5) | 108% | 0 (9) | 17761 | 1746 | 1710 |
| JV_AB | 13 | 27291 | 36371 | 25.0 | 17.4 | -27291 | 9079 | 9.6 (10.5) | 99% | 0 (9) | 16651 | 636 | 651 |
| JV_AC | 13 | 31705 | 36371 | 12.8 | 8.9 | -31705 | 4666 | 8.3 (10.5) | 105% | 0 (9) | 17218 | 1203 | 1192 |
| JV_BC | 13 | 32311 | 36371 | 11.2 | 7.8 | -32311 | 4059 | 7.6 (10.5) | 112% | 0 (9) | 18754 | 2739 | 2705 |
| JV_ABC | 13 | 28031 | 36371 | 22.9 | 16.0 | -28031 | 8340 | 7.9 (10.5) | 108% | 0 (9) | 18016 | 2001 | 1990 |
| JV_ABF | 13 | 21764 | 36371 | 40.2 | 27.7 | -21764 | 14607 | 5.8 (10.5) | 110% | 0 (9) | 18662 | 2647 | 2653 |
| JV_DV | 13 | 30941 | 36371 | 14.9 | 5.5 | -30941 | 5429 | 9.6 (10.5) | 95% | 0 (9) | 18356 | 2341 | 2418 |
| JV_AR | 13 | 32184 | 36371 | 11.5 | 5.6 | -32184 | 4187 | 10.5 (10.5) | 96% | 0 (9) | 17029 | 1014 | 1046 |
| JV_BR | 13 | 34107 | 36371 | 6.2 | 6.6 | -32937 | 3433 | 9.4 (10.5) | 105% | 0 (9) | 17870 | 1855 | 1871 |
| JV_BD | 13 | 32902 | 36371 | 9.5 | 13.9 | -32902 | 3469 | 9.0 (10.5) | 99% | 0 (9) | 19457 | 3442 | 3513 |
| JV_F | 13 | 30843 | 36371 | 15.2 | 10.3 | -30843 | 5527 | 6.6 (10.5) | 112% | 0 (9) | 18079 | 2064 | 2047 |
| JV_T | 13 | 36371 | 36371 | 0.0 | -0.0 | -36371 | 0 | 10.4 (10.5) | 106% | 0 (9) | 17080 | 1065 | 1057 |
| JV_R | 13 | 36464 | 36371 | -0.3 | -2.6 | -36464 | -94 | 10.3 (10.5) | 99% | 0 (9) | 16687 | 671 | 689 |
| JV_P | 13 | 30683 | 36371 | 15.6 | 16.9 | -26176 | 10195 | 10.4 (10.5) | 100% | 0 (9) | 16818 | 803 | 794 |
| JV_V | 13 | 36696 | 36371 | -0.9 | -1.6 | -35774 | 596 | 10.5 (10.5) | 97% | 0 (9) | 15159 | -856 | -841 |
| JV_D | 13 | 31318 | 36371 | 13.9 | 4.7 | -31318 | 5052 | 9.6 (10.5) | 97% | 0 (9) | 18740 | 2725 | 2797 |
| JV_BF | 13 | 30845 | 36371 | 15.2 | 18.4 | -26044 | 10326 | 5.7 (10.5) | 116% | 0 (9) | 19001 | 2986 | 2967 |
| JV_BP | 13 | 32267 | 36371 | 11.3 | 13.9 | -27759 | 8611 | 9.5 (10.5) | 105% | 0 (9) | 17892 | 1877 | 1867 |
| JV_BV | 13 | 38280 | 36371 | -5.2 | 7.6 | -33725 | 2645 | 9.5 (10.5) | 103% | 0 (9) | 16402 | 387 | 402 |
| JV_ABD | 13 | 27032 | 36371 | 25.7 | 17.2 | -27032 | 9338 | 9.2 (10.5) | 97% | 0 (9) | 19113 | 3098 | 3184 |
| JV_AD | 13 | 27745 | 36371 | 23.7 | 8.0 | -27745 | 8625 | 9.8 (10.5) | 94% | 0 (9) | 18183 | 2168 | 2254 |
| JV_DP | 13 | 31468 | 36371 | 13.5 | 22.1 | -31468 | 4902 | 9.5 (10.5) | 95% | 0 (9) | 19563 | 3548 | 3613 |
| JV_DR | 13 | 30845 | 36371 | 15.2 | 4.2 | -30845 | 5525 | 9.5 (10.5) | 97% | 0 (9) | 19104 | 3089 | 3166 |
| JV_PR | 13 | 32674 | 36371 | 10.2 | 16.9 | -31504 | 4867 | 10.3 (10.5) | 99% | 0 (9) | 17527 | 1512 | 1521 |
| JV_PV | 13 | 36846 | 36371 | -1.3 | 12.3 | -32292 | 4079 | 10.5 (10.5) | 97% | 0 (9) | 15968 | -47 | -40 |
| JV_AP | 13 | 22242 | 36371 | 38.8 | 28.5 | -22242 | 14129 | 10.5 (10.5) | 92% | 1 (9) | 15496 | -519 | -513 |
| JV_AV | 13 | 31494 | 36371 | 13.4 | 6.6 | -31494 | 4877 | 10.6 (10.5) | 94% | 0 (9) | 15470 | -545 | -515 |
| JV_BT | 13 | 37713 | 36371 | -3.7 | 7.3 | -34772 | 1599 | 9.5 (10.5) | 111% | 0 (9) | 18258 | 2243 | 2235 |

### L6M

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 26 | 32090 | 36371 | 11.8 | 8.2 | -32090 | 4280 | 11.1 (11.1) | 104% | 0 (19) | 25520 | 383 | 407 |
| JV_B | 26 | 32117 | 36371 | 11.7 | 9.2 | -31572 | 4799 | 10.4 (11.1) | 97% | 0 (19) | 25710 | 573 | 571 |
| JV_C | 26 | 35985 | 36371 | 1.1 | 0.7 | -35985 | 385 | 8.8 (11.1) | 107% | 1 (19) | 25849 | 712 | 683 |
| JV_AB | 26 | 27641 | 36371 | 24.0 | 17.4 | -27641 | 8729 | 10.3 (11.1) | 101% | 0 (19) | 26083 | 946 | 969 |
| JV_AC | 26 | 33171 | 36371 | 8.8 | 8.9 | -33171 | 3199 | 8.9 (11.1) | 109% | 1 (19) | 26253 | 1116 | 1115 |
| JV_BC | 26 | 33163 | 36371 | 8.8 | 7.8 | -33163 | 3207 | 8.5 (11.1) | 105% | 1 (19) | 26354 | 1217 | 1188 |
| JV_ABC | 26 | 33171 | 36371 | 8.8 | 16.0 | -33171 | 3199 | 8.6 (11.1) | 108% | 1 (19) | 26608 | 1472 | 1469 |
| JV_ABF | 26 | 28498 | 36371 | 21.6 | 27.7 | -28498 | 7873 | 6.5 (11.1) | 102% | 0 (19) | 27603 | 2466 | 2479 |
| JV_DV | 26 | 30941 | 36371 | 14.9 | 5.5 | -30941 | 5429 | 10.4 (11.1) | 98% | 1 (19) | 26776 | 1639 | 1726 |
| JV_AR | 26 | 32184 | 36371 | 11.5 | 5.6 | -32184 | 4187 | 10.9 (11.1) | 106% | 0 (19) | 26501 | 1364 | 1409 |
| JV_BR | 26 | 34107 | 36371 | 6.2 | 6.6 | -32937 | 3433 | 10.3 (11.1) | 100% | 0 (19) | 26744 | 1607 | 1627 |
| JV_BD | 26 | 32902 | 36371 | 9.5 | 13.9 | -32902 | 3469 | 9.9 (11.1) | 97% | 1 (19) | 27669 | 2532 | 2611 |
| JV_F | 26 | 30843 | 36371 | 15.2 | 10.3 | -30843 | 5527 | 7.2 (11.1) | 102% | 0 (19) | 27009 | 1872 | 1857 |
| JV_T | 26 | 36371 | 36371 | 0.0 | 0.0 | -36371 | 0 | 11.0 (11.1) | 102% | 0 (19) | 26333 | 1196 | 1191 |
| JV_R | 26 | 36464 | 36371 | -0.3 | -2.6 | -36464 | -94 | 11.0 (11.1) | 103% | 0 (19) | 26202 | 1065 | 1086 |
| JV_P | 26 | 30683 | 36371 | 15.6 | 16.9 | -26176 | 10195 | 11.3 (11.1) | 103% | 0 (19) | 26857 | 1720 | 1720 |
| JV_V | 26 | 36696 | 36371 | -0.9 | -1.6 | -35774 | 596 | 11.1 (11.1) | 102% | 0 (19) | 24834 | -303 | -286 |
| JV_D | 26 | 31318 | 36371 | 13.9 | 4.7 | -31318 | 5052 | 10.5 (11.1) | 97% | 1 (19) | 27082 | 1945 | 2024 |
| JV_BF | 26 | 30845 | 36371 | 15.2 | 18.4 | -26360 | 10011 | 6.5 (11.1) | 99% | 0 (19) | 27228 | 2091 | 2074 |
| JV_BP | 26 | 32267 | 36371 | 11.3 | 13.9 | -27759 | 8611 | 10.5 (11.1) | 100% | 0 (19) | 27309 | 2172 | 2170 |
| JV_BV | 26 | 38280 | 36371 | -5.2 | 7.6 | -33725 | 2645 | 10.3 (11.1) | 99% | 0 (19) | 25407 | 270 | 286 |
| JV_ABD | 26 | 27032 | 36371 | 25.7 | 17.2 | -27032 | 9338 | 9.8 (11.1) | 99% | 0 (19) | 28165 | 3028 | 3127 |
| JV_AD | 26 | 27745 | 36371 | 23.7 | 8.0 | -27745 | 8625 | 10.4 (11.1) | 100% | 0 (19) | 27523 | 2386 | 2484 |
| JV_DP | 26 | 31468 | 36371 | 13.5 | 22.1 | -31468 | 4902 | 10.5 (11.1) | 99% | 1 (19) | 28395 | 3258 | 3344 |
| JV_DR | 26 | 30923 | 36371 | 15.0 | 4.2 | -30845 | 5525 | 10.4 (11.1) | 98% | 1 (19) | 27029 | 1892 | 1977 |
| JV_PR | 26 | 32674 | 36371 | 10.2 | 16.9 | -31504 | 4867 | 11.1 (11.1) | 105% | 0 (19) | 27690 | 2553 | 2577 |
| JV_PV | 26 | 36846 | 36371 | -1.3 | 12.3 | -32292 | 4079 | 11.2 (11.1) | 104% | 0 (19) | 27067 | 1930 | 1947 |
| JV_AP | 26 | 29468 | 36371 | 19.0 | 28.5 | -29468 | 6902 | 11.2 (11.1) | 107% | 1 (19) | 26813 | 1676 | 1699 |
| JV_AV | 26 | 31494 | 36371 | 13.4 | 6.6 | -31494 | 4877 | 11.0 (11.1) | 104% | 0 (19) | 25393 | 256 | 296 |
| JV_BT | 26 | 37713 | 36371 | -3.7 | 7.3 | -34772 | 1599 | 10.3 (11.1) | 99% | 0 (19) | 26873 | 1736 | 1729 |

### HOLD

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 52 | 55870 | 63185 | 11.6 | 19.4 | -55870 | -725 | 10.7 (10.7) | 103% | 0 (37) | 18213 | 724 | 745 |
| JV_B | 52 | 61073 | 63185 | 3.3 | 4.9 | -55145 | 0 | 10.1 (10.7) | 99% | 0 (37) | 18288 | 799 | 798 |
| JV_C | 52 | 73536 | 63185 | -16.4 | 20.1 | -57536 | -2390 | 8.3 (10.7) | 97% | 2 (37) | 17634 | 145 | 101 |
| JV_AB | 52 | 53321 | 63185 | 15.6 | 17.9 | -53321 | 1825 | 10.0 (10.7) | 102% | 0 (37) | 18881 | 1391 | 1411 |
| JV_AC | 52 | 76099 | 63185 | -20.4 | 17.3 | -57490 | -2345 | 8.4 (10.7) | 98% | 1 (37) | 18093 | 604 | 586 |
| JV_BC | 52 | 71971 | 63185 | -13.9 | 21.8 | -56582 | -1437 | 8.1 (10.7) | 95% | 2 (37) | 18186 | 697 | 653 |
| JV_ABC | 52 | 74738 | 63185 | -18.3 | 18.8 | -56878 | -1732 | 8.2 (10.7) | 97% | 1 (37) | 18406 | 917 | 897 |
| JV_ABF | 52 | 53389 | 63185 | 15.5 | 17.5 | -51508 | 3638 | 6.9 (10.7) | 103% | 0 (37) | 19356 | 1867 | 1884 |
| JV_DV | 52 | 55456 | 63185 | 12.2 | 16.5 | -51173 | 3973 | 10.1 (10.7) | 97% | 3 (37) | 18344 | 855 | 939 |
| JV_AR | 52 | 53366 | 63185 | 15.5 | 16.5 | -53366 | 1780 | 10.6 (10.7) | 105% | 0 (37) | 18840 | 1351 | 1387 |
| JV_BR | 52 | 51830 | 63185 | 18.0 | 8.4 | -51830 | 3315 | 10.0 (10.7) | 101% | 0 (37) | 19273 | 1783 | 1796 |
| JV_BD | 52 | 63408 | 63185 | -0.4 | 15.9 | -51715 | 3431 | 9.6 (10.7) | 95% | 3 (37) | 18988 | 1498 | 1577 |
| JV_F | 52 | 64485 | 63185 | -2.1 | -0.5 | -54382 | 763 | 7.6 (10.7) | 103% | 1 (37) | 17959 | 469 | 466 |
| JV_T | 52 | 62144 | 63185 | 1.6 | 0.0 | -50882 | 4263 | 10.6 (10.7) | 101% | 0 (37) | 19127 | 1638 | 1630 |
| JV_R | 52 | 51830 | 63185 | 18.0 | 3.5 | -51830 | 3315 | 10.6 (10.7) | 103% | 0 (37) | 18472 | 982 | 996 |
| JV_P | 52 | 69237 | 63185 | -9.6 | 6.1 | -69237 | -14091 | 10.8 (10.7) | 99% | 0 (37) | 18040 | 551 | 552 |
| JV_V | 52 | 52302 | 63185 | 17.2 | 13.5 | -52302 | 2844 | 10.7 (10.7) | 103% | 0 (37) | 17791 | 302 | 312 |
| JV_D | 52 | 65520 | 63185 | -3.7 | 13.6 | -51715 | 3431 | 10.1 (10.7) | 95% | 3 (37) | 18097 | 608 | 687 |
| JV_BF | 52 | 61614 | 63185 | 2.5 | 4.4 | -54382 | 763 | 6.9 (10.7) | 101% | 0 (37) | 18907 | 1417 | 1411 |
| JV_BP | 52 | 69237 | 63185 | -9.6 | 11.0 | -69237 | -14091 | 10.2 (10.7) | 97% | 0 (37) | 18799 | 1310 | 1310 |
| JV_BV | 52 | 51006 | 63185 | 19.3 | 17.3 | -51006 | 4139 | 10.1 (10.7) | 101% | 0 (37) | 18606 | 1117 | 1125 |
| JV_ABD | 52 | 58264 | 63185 | 7.8 | 23.7 | -50701 | 4445 | 9.6 (10.7) | 97% | 2 (37) | 19586 | 2097 | 2194 |
| JV_AD | 52 | 60376 | 63185 | 4.4 | 21.4 | -53250 | 1895 | 10.1 (10.7) | 97% | 2 (37) | 18785 | 1296 | 1394 |
| JV_DP | 52 | 63124 | 63185 | 0.1 | 15.4 | -63124 | -7979 | 10.1 (10.7) | 94% | 3 (37) | 18747 | 1258 | 1346 |
| JV_DR | 52 | 62542 | 63185 | 1.0 | 17.5 | -52254 | 2891 | 10.1 (10.7) | 96% | 2 (37) | 17999 | 510 | 593 |
| JV_PR | 52 | 64650 | 63185 | -2.3 | -2.4 | -64650 | -9505 | 10.7 (10.7) | 102% | 1 (37) | 18894 | 1404 | 1421 |
| JV_PV | 52 | 64196 | 63185 | -1.6 | 13.7 | -64196 | -9050 | 10.7 (10.7) | 102% | 0 (37) | 18699 | 1209 | 1221 |
| JV_AP | 52 | 69866 | 63185 | -10.6 | 21.6 | -69866 | -14720 | 10.8 (10.7) | 102% | 1 (37) | 18639 | 1150 | 1172 |
| JV_AV | 52 | 51135 | 63185 | 19.1 | 20.6 | -51135 | 4010 | 10.7 (10.7) | 105% | 0 (37) | 18424 | 935 | 967 |
| JV_BT | 52 | 60032 | 63185 | 5.0 | 4.9 | -49586 | 5559 | 10.0 (10.7) | 99% | 0 (37) | 19877 | 2387 | 2378 |

### PRE

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 75 | 81965 | 76186 | -7.6 | -0.7 | -51421 | 1126 | 9.2 (9.3) | 97% | 0 (48) | 10126 | -42 | -31 |
| JV_B | 75 | 76961 | 76186 | -1.0 | 0.0 | -52547 | 0 | 9.0 (9.3) | 101% | 0 (48) | 10078 | -90 | -90 |
| JV_C | 75 | 93191 | 76186 | -22.3 | -11.7 | -56666 | -4119 | 6.8 (9.3) | 100% | 2 (48) | 7415 | -2753 | -2848 |
| JV_AB | 75 | 82739 | 76186 | -8.6 | -0.7 | -51421 | 1126 | 8.9 (9.3) | 98% | 1 (48) | 10095 | -73 | -62 |

### X'

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 44 | 50995 | 55326 | 7.8 | 1.8 | -21733 | -70 | 10.8 (10.8) | 99% | 0 (25) | 3828 | 243 | 248 |
| JV_B | 44 | 45376 | 55326 | 18.0 | 11.3 | -21663 | 0 | 10.6 (10.8) | 98% | 0 (25) | 3834 | 249 | 249 |
| JV_C | 44 | 93035 | 55326 | -68.2 | -58.4 | -28687 | -7024 | 8.8 (10.8) | 74% | 2 (25) | 339 | -3246 | -3370 |
| JV_AB | 44 | 43447 | 55326 | 21.5 | 11.9 | -21733 | -70 | 10.6 (10.8) | 98% | 0 (25) | 4002 | 417 | 422 |

### GAP

| set | weeks | maxDD (weekly series) | JN05W2 | cut % WEEKLY | cut % DAILY | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk | d mean @4.84 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 18 | 67381 | 68947 | 2.3 | -0.7 | -67381 | 1566 | 9.6 (9.7) | 94% | 1 (13) | 11461 | -915 | -903 |
| JV_B | 18 | 68947 | 68947 | 0.0 | 0.0 | -68947 | 0 | 9.6 (9.7) | 101% | 0 (13) | 12381 | 5 | 5 |
| JV_C | 18 | 85805 | 68947 | -24.5 | -15.3 | -74665 | -5719 | 7.7 (9.7) | 83% | 1 (13) | 7653 | -4724 | -4831 |
| JV_AB | 18 | 67381 | 68947 | 2.3 | -0.7 | -67381 | 1566 | 9.5 (9.7) | 95% | 0 (13) | 11548 | -829 | -816 |
| JV_F | 18 | 68342 | 68947 | 0.9 | 4.0 | -68342 | 604 | 8.1 (9.7) | 99% | 0 (13) | 13913 | 1536 | 1535 |

## 2. The recent max drawdown is one week (2026-W44): L6M / L3M with W44 removed from both cell and JN05W2

| set | window | maxDD (W44 out) | JN05W2 (W44 out) | cut % | d mean $/wk (W44 out) | cut % with W44 in |
|--|--|--|--|--|--|--|
| JV_A | L3M | 22092 | 30533 | 27.6 | -1106 | 11.8 |
| JV_A | L6M | 28644 | 30533 | 6.2 | 228 | 11.8 |
| JV_B | L3M | 32117 | 30533 | -5.2 | 947 | 11.7 |
| JV_B | L6M | 32117 | 30533 | -5.2 | 404 | 11.7 |
| JV_C | L3M | 21896 | 30533 | 28.3 | 1859 | 1.1 |
| JV_C | L6M | 33163 | 30533 | -8.6 | 725 | 1.1 |
| JV_AB | L3M | 21889 | 30533 | 28.3 | -67 | 25.0 |
| JV_AB | L6M | 27641 | 30533 | 9.5 | 620 | 24.0 |
| JV_AC | L3M | 17808 | 30533 | 41.7 | 915 | 12.8 |
| JV_AC | L6M | 33171 | 30533 | -8.6 | 974 | 8.8 |
| JV_BC | L3M | 21896 | 30533 | 28.3 | 2629 | 11.2 |
| JV_BC | L6M | 33163 | 30533 | -8.6 | 1104 | 8.8 |
| JV_ABC | L3M | 17808 | 30533 | 41.7 | 1473 | 22.9 |
| JV_ABC | L6M | 33171 | 30533 | -8.6 | 1197 | 8.8 |
| JV_ABF | L3M | 19449 | 30533 | 36.3 | 1650 | 40.2 |
| JV_ABF | L6M | 28498 | 30533 | 6.7 | 1981 | 21.6 |
| JV_DV | L3M | 30941 | 30533 | -1.3 | 1924 | 14.9 |
| JV_DV | L6M | 30941 | 30533 | -1.3 | 1411 | 14.9 |
| JV_AR | L3M | 23100 | 30533 | 24.3 | 749 | 11.5 |
| JV_AR | L6M | 30703 | 30533 | -0.6 | 1251 | 11.5 |
| JV_BR | L3M | 34107 | 30533 | -11.7 | 1617 | 6.2 |
| JV_BR | L6M | 34107 | 30533 | -11.7 | 1483 | 6.2 |
| JV_BD | L3M | 32902 | 30533 | -7.8 | 2752 | 9.5 |
| JV_BD | L6M | 32902 | 30533 | -7.8 | 2165 | 9.5 |
| JV_F | L3M | 29261 | 30533 | 4.2 | 1775 | 15.2 |
| JV_F | L6M | 29261 | 30533 | 4.2 | 1726 | 15.2 |
| JV_T | L3M | 36129 | 30533 | -18.3 | 1153 | 0.0 |
| JV_T | L6M | 36129 | 30533 | -18.3 | 1244 | 0.0 |
| JV_R | L3M | 32524 | 30533 | -6.5 | 735 | -0.3 |
| JV_R | L6M | 32524 | 30533 | -6.5 | 1111 | -0.3 |
| JV_P | L3M | 30683 | 30533 | -0.5 | -66 | 15.6 |
| JV_P | L6M | 30683 | 30533 | -0.5 | 1340 | 15.6 |
| JV_V | L3M | 36696 | 30533 | -20.2 | -978 | -0.9 |
| JV_V | L6M | 36696 | 30533 | -20.2 | -339 | -0.9 |
| JV_D | L3M | 31318 | 30533 | -2.6 | 2376 | 13.9 |
| JV_D | L6M | 31318 | 30533 | -2.6 | 1746 | 13.9 |
| JV_BF | L3M | 30845 | 30533 | -1.0 | 2374 | 15.2 |
| JV_BF | L6M | 30845 | 30533 | -1.0 | 1761 | 15.2 |
| JV_BP | L3M | 32267 | 30533 | -5.7 | 697 | 11.3 |
| JV_BP | L6M | 32267 | 30533 | -5.7 | 1618 | 11.3 |
| JV_BV | L3M | 38280 | 30533 | -25.4 | -30 | -5.2 |
| JV_BV | L6M | 38280 | 30533 | -25.4 | 65 | -5.2 |
| JV_ABD | L3M | 27032 | 30533 | 11.5 | 2237 | 25.7 |
| JV_ABD | L6M | 27032 | 30533 | 11.5 | 2612 | 25.7 |
| JV_AD | L3M | 27235 | 30533 | 10.8 | 1630 | 23.7 |
| JV_AD | L6M | 27235 | 30533 | 10.8 | 2137 | 23.7 |
| JV_DP | L3M | 31468 | 30533 | -3.1 | 2531 | 13.5 |
| JV_DP | L6M | 31468 | 30533 | -3.1 | 2759 | 13.5 |
| JV_DR | L3M | 30845 | 30533 | -1.0 | 2792 | 15.2 |
| JV_DR | L6M | 30923 | 30533 | -1.3 | 1701 | 15.0 |
| JV_PR | L3M | 32674 | 30533 | -7.0 | 710 | 10.2 |
| JV_PR | L6M | 32674 | 30533 | -7.0 | 2210 | 10.2 |
| JV_PV | L3M | 36846 | 30533 | -20.7 | -926 | -1.3 |
| JV_PV | L6M | 36846 | 30533 | -20.7 | 1587 | -1.3 |
| JV_AP | L3M | 22242 | 30533 | 27.2 | -1855 | 38.8 |
| JV_AP | L6M | 29468 | 30533 | 3.5 | 1122 | 19.0 |
| JV_AV | L3M | 21994 | 30533 | 28.0 | -997 | 13.4 |
| JV_AV | L6M | 26379 | 30533 | 13.6 | 71 | 13.4 |
| JV_BT | L3M | 37713 | 30533 | -23.5 | 2030 | -3.7 |
| JV_BT | L6M | 37713 | 30533 | -23.5 | 1613 | -3.7 |

## 3. Trend-week clause (L6M, program convention: 5 best LPB_BASE weeks) and bi-weekly walk-forward vs JN05W2 (43 months)

| set | 5 best LPB wks $ (cell / JN05W2 / LPB_BASE) | LPB winning wks turned losing | weeks beating JN05W2 (of 26) | WF beat % | WF cut % | WF d mean $/wk |
|--|--|--|--|--|--|--|
| JV_A | 253399 / 255545 / 331449 | 0 of 19 | 9 | 41.8 | 0.8 | 88.5 |
| JV_B | 261019 / 255545 / 331449 | 0 of 19 | 15 | 16.5 | 0.0 | 24.5 |
| JV_C | 257064 / 255545 / 331449 | 3 of 19 | 14 | 3.8 | 0.0 | -353.5 |
| JV_AB | 258872 / 255545 / 331449 | 0 of 19 | 13 | 44.3 | -0.2 | 312.0 |
| JV_AC | 258347 / 255545 / 331449 | 2 of 19 | 12 | - | - | - |
| JV_BC | 265480 / 255545 / 331449 | 2 of 19 | 14 | - | - | - |
| JV_ABC | 266763 / 255545 / 331449 | 2 of 19 | 14 | - | - | - |
| JV_ABF | 258229 / 255545 / 331449 | 0 of 19 | 17 | - | - | - |
| JV_DV | 259955 / 255545 / 331449 | 2 of 19 | 15 | - | - | - |
| JV_AR | 250476 / 255545 / 331449 | 1 of 19 | 13 | - | - | - |
| JV_BR | 257482 / 255545 / 331449 | 1 of 19 | 16 | - | - | - |
| JV_BD | 261528 / 255545 / 331449 | 1 of 19 | 17 | - | - | - |
| JV_F | 262917 / 255545 / 331449 | 1 of 19 | 15 | - | - | - |
| JV_T | 286235 / 255545 / 331449 | 2 of 19 | 10 | - | - | - |
| JV_R | 252008 / 255545 / 331449 | 1 of 19 | 16 | - | - | - |
| JV_P | 250077 / 255545 / 331449 | 0 of 19 | 9 | - | - | - |
| JV_V | 247372 / 255545 / 331449 | 1 of 19 | 10 | - | - | - |
| JV_D | 260399 / 255545 / 331449 | 2 of 19 | 16 | - | - | - |
| JV_BF | 263469 / 255545 / 331449 | 0 of 19 | 14 | - | - | - |
| JV_BP | 255550 / 255545 / 331449 | 0 of 19 | 16 | - | - | - |
| JV_BV | 252846 / 255545 / 331449 | 1 of 19 | 10 | - | - | - |
| JV_ABD | 259024 / 255545 / 331449 | 0 of 19 | 15 | - | - | - |
| JV_AD | 257895 / 255545 / 331449 | 0 of 19 | 15 | - | - | - |
| JV_DP | 254930 / 255545 / 331449 | 1 of 19 | 15 | - | - | - |
| JV_DR | 256469 / 255545 / 331449 | 2 of 19 | 15 | - | - | - |
| JV_PR | 248980 / 255545 / 331449 | 0 of 19 | 15 | - | - | - |
| JV_PV | 244344 / 255545 / 331449 | 0 of 19 | 14 | - | - | - |
| JV_AP | 247930 / 255545 / 331449 | 1 of 19 | 14 | - | - | - |
| JV_AV | 244641 / 255545 / 331449 | 0 of 19 | 11 | - | - | - |
| JV_BT | 290855 / 255545 / 331449 | 0 of 19 | 17 | - | - | - |

## 4. Interaction table (joint vs sum of the singles, L6M and HOLD; d = cell - JN05W2; synergy = joint - sum of singles; DD synergy in cut-% points)

| joint | window | joint DD cut % | sum of singles' cut % | synergy | joint d mean | sum singles d mean | synergy $/wk |
|--|--|--|--|--|--|--|--|
| JV_AB | L6M | 24.0 | 23.5 | 0.5 | 946 | 956 | -10 |
| JV_AB | HOLD | 15.6 | 14.9 | 0.7 | 1391 | 1523 | -131 |
| JV_AC | L6M | 8.8 | 12.8 | -4.0 | 1116 | 1095 | 21 |
| JV_AC | HOLD | -20.4 | -4.8 | -15.6 | 604 | 868 | -264 |
| JV_BC | L6M | 8.8 | 12.8 | -3.9 | 1217 | 1284 | -67 |
| JV_BC | HOLD | -13.9 | -13.0 | -0.9 | 697 | 944 | -247 |
| JV_ABC | L6M | 8.8 | 24.5 | -15.7 | 1472 | 1668 | -196 |
| JV_ABC | HOLD | -18.3 | -1.5 | -16.8 | 917 | 1667 | -750 |
| JV_ABF | L6M | 21.6 | 38.7 | -17.0 | 2466 | 2828 | -362 |
| JV_ABF | HOLD | 15.5 | 12.9 | 2.6 | 1867 | 1992 | -125 |
| JV_DV | L6M | 14.9 | 13.0 | 1.9 | 1639 | 1642 | -3 |
| JV_DV | HOLD | 12.2 | 13.5 | -1.3 | 855 | 910 | -55 |
| JV_AR | L6M | 11.5 | 11.5 | -0.0 | 1364 | 1448 | -84 |
| JV_AR | HOLD | 15.5 | 29.5 | -14.0 | 1351 | 1706 | -355 |
| JV_BR | L6M | 6.2 | 11.4 | -5.2 | 1607 | 1637 | -30 |
| JV_BR | HOLD | 18.0 | 21.3 | -3.3 | 1783 | 1781 | 2 |
| JV_BD | L6M | 9.5 | 25.6 | -16.0 | 2532 | 2517 | 15 |
| JV_BD | HOLD | -0.4 | -0.4 | -0.0 | 1498 | 1407 | 92 |
| JV_BF | L6M | 15.2 | 26.9 | -11.7 | 2091 | 2445 | -354 |
| JV_BF | HOLD | 2.5 | 1.3 | 1.2 | 1417 | 1268 | 149 |
| JV_BP | L6M | 11.3 | 27.3 | -16.0 | 2172 | 2293 | -121 |
| JV_BP | HOLD | -9.6 | -6.2 | -3.3 | 1310 | 1350 | -40 |
| JV_BV | L6M | -5.2 | 10.8 | -16.0 | 270 | 270 | 0 |
| JV_BV | HOLD | 19.3 | 20.6 | -1.3 | 1117 | 1101 | 16 |
| JV_ABD | L6M | 25.7 | 37.4 | -11.7 | 3028 | 2901 | 127 |
| JV_ABD | HOLD | 7.8 | 11.2 | -3.4 | 2097 | 2130 | -33 |
| JV_AD | L6M | 23.7 | 25.7 | -1.9 | 2386 | 2328 | 58 |
| JV_AD | HOLD | 4.4 | 7.9 | -3.4 | 1296 | 1331 | -35 |
| JV_DP | L6M | 13.5 | 29.5 | -16.0 | 3258 | 3665 | -407 |
| JV_DP | HOLD | 0.1 | -13.3 | 13.4 | 1258 | 1158 | 99 |
| JV_DR | L6M | 15.0 | 13.6 | 1.3 | 1892 | 3010 | -1118 |
| JV_DR | HOLD | 1.0 | 14.3 | -13.3 | 510 | 1590 | -1080 |
| JV_PR | L6M | 10.2 | 15.4 | -5.2 | 2553 | 2785 | -232 |
| JV_PR | HOLD | -2.3 | 8.4 | -10.7 | 1404 | 1533 | -129 |
| JV_PV | L6M | -1.3 | 14.7 | -16.0 | 1930 | 1417 | 512 |
| JV_PV | HOLD | -1.6 | 7.6 | -9.2 | 1209 | 853 | 357 |
| JV_AP | L6M | 19.0 | 27.4 | -8.4 | 1676 | 2104 | -428 |
| JV_AP | HOLD | -10.6 | 2.0 | -12.6 | 1150 | 1274 | -125 |
| JV_AV | L6M | 13.4 | 10.9 | 2.5 | 256 | 80 | 176 |
| JV_AV | HOLD | 19.1 | 28.8 | -9.7 | 935 | 1026 | -90 |
| JV_BT | L6M | -3.7 | 11.7 | -15.4 | 1736 | 1769 | -33 |
| JV_BT | HOLD | 5.0 | 5.0 | 0.0 | 2387 | 2437 | -50 |

## 5. Exact placebos (A: first-trade-lost read from 11 / 23 / 37 days earlier; B and C: same trigger, exit at a random later second 1..60 min if still open; PLk_ABC = all three placebos together)

| real set | window | real cut % | real d mean | placebo cut % (11/23/37 or seeds 1/2/3) | placebo d mean | real beats all 3 placebos on cut? |
|--|--|--|--|--|--|--|
| JV_A | L3M | 11.8 | -691 | 7.0 / 21.8 / 11.2 | -253 / -1637 / -926 | no |
| JV_A | L6M | 11.8 | 383 | 7.0 / 21.8 / 11.2 | -1112 / -914 / -526 | no |
| JV_A | HOLD | 11.6 | 724 | 13.1 / -3.8 | -553 / 304 | partial (2 placebos) |
| JV_B | L3M | 11.7 | 1244 | 10.5 / 11.8 / 11.7 | 297 / 514 / 487 | no |
| JV_B | L6M | 11.7 | 573 | 10.5 / 11.8 / 11.7 | 390 / 548 / 238 | no |
| JV_B | HOLD | 3.3 | 799 | 2.0 | 625 | partial (1 placebos) |
| JV_C | L3M | 1.1 | 1746 | -9.1 / -6.6 / -17.4 | -577 / 1085 / -620 | yes |
| JV_C | L6M | 1.1 | 712 | -9.1 / -6.6 / -17.4 | 1428 / 1717 / 1027 | yes |
| JV_AB | L3M | 25.0 | 636 | 17.5 / 17.6 / 21.9 | -12 / -1161 / -790 | yes |
| JV_AB | L6M | 24.0 | 946 | 17.5 / 17.6 / 21.9 | -803 / -405 / -600 | yes |
| JV_AB | HOLD | 15.6 | 1391 | 15.1 / 4.6 / -2.6 | 5 / -285 / 503 | yes |
| JV_ABC | L3M | 22.9 | 2001 | 6.3 / 33.2 / -12.0 | -777 / 773 / -976 | no |
| JV_ABC | L6M | 8.8 | 1472 | 6.3 / 26.0 / -12.0 | 663 / 1146 / 645 | no |

## 6. Ranking (tolerant gate in every complete window of L3M L6M HOLD PRE X': DD cut > -2 %, mean not lower than -3 %; then by the WORST-window DD cut)

| rank | set | passes gate | worst-window DD cut % | mean d $/wk (avg of windows) | complete windows |
|--|--|--|--|--|--|
| 1 | JV_B | yes | -1.0 | 555 | 5 |
| 2 | JV_A | no | -7.6 | 123 | 5 |
| 3 | JV_AB | no | -8.6 | 663 | 5 |
| 4 | JV_C | no | -68.2 | -679 | 5 |
| 5 | JV_ABF | yes | 15.5 | 2327 | 3 |
| 6 | JV_DV | yes | 12.2 | 1612 | 3 |
| 7 | JV_AR | yes | 11.5 | 1243 | 3 |
| 8 | JV_ABD | yes | 7.8 | 2741 | 3 |
| 9 | JV_BR | yes | 6.2 | 1748 | 3 |
| 10 | JV_AD | yes | 4.4 | 1950 | 3 |
| 11 | JV_BF | yes | 2.5 | 2165 | 3 |
| 12 | JV_DR | yes | 1.0 | 1830 | 3 |
| 13 | JV_DP | yes | 0.1 | 2688 | 3 |
| 14 | JV_T | yes | 0.0 | 1300 | 3 |
| 15 | JV_R | yes | -0.3 | 906 | 3 |
| 16 | JV_BD | yes | -0.4 | 2491 | 3 |
| 17 | JV_PV | yes | -1.6 | 1031 | 3 |
| 18 | JV_AV | no | 13.4 | 215 | 3 |
| 19 | JV_V | no | -0.9 | -286 | 3 |
| 20 | JV_F | no | -2.1 | 1468 | 3 |
| 21 | JV_PR | no | -2.3 | 1823 | 3 |
| 22 | JV_BT | no | -3.7 | 2122 | 3 |
| 23 | JV_D | no | -3.7 | 1759 | 3 |
| 24 | JV_BV | no | -5.2 | 591 | 3 |
| 25 | JV_P | no | -9.6 | 1025 | 3 |
| 26 | JV_BP | no | -9.6 | 1786 | 3 |
| 27 | JV_AP | no | -10.6 | 769 | 3 |
| 28 | JV_BC | no | -13.9 | 1551 | 3 |
| 29 | JV_ABC | no | -18.3 | 1463 | 3 |
| 30 | JV_AC | no | -20.4 | 974 | 3 |

Sets with fewer than 4 complete windows (the D = London range-used-up combinations so far) are listed but cannot lead.

**PATH EFFECT = FREED-BOOK REPLACEMENT (generic; PATH_EFFECT_RULE.md: a random 50 pct skip alone takes L6M DD 52k -> 86k, net 661k -> 428k): every skip-type rule (R, W, V, D, L, P, and F with its stack cut) is read against an engine random skip of the same keep share, see column vs random skip in DS3_V20_BUILD_LIST.md. F (A7 flat -40) is a path effect / stack-cut (W-PM: A7 itself +345 of +1,869 $/wk; StackCut exits 40 -> 15). BF, ABF, AF and any R-type skip pair inherit the flag until W-CF3 PX runs land.

**CONTROL VALIDITY:** W-LR found its London random-skip controls (RK69/RK72, RKMP68/72, RKUC65) INVALID (per-second redraw lets a skipped signal re-enter a second later; keep share 0.87-0.92 vs 0.60-0.73 for the rule). Every E/G/D/L (London range-used-up) comparison against a random skip is marked INVALID CONTROL / not finished: no claim of beating random. The random sources of W-PR (random blocks), W-RA (PL seeds) and W-CF3 (RS_*) are unverified until each owner confirms the draw is per signal/event and not redrawn each second.

**STANDING CONTROL RULE (user order 11-16):** a skip-type rule is NOT a lead until it has its persistent-draw random-skip control (bucket=300: one draw per 5-minute bucket per book and side, no re-draw of a skipped signal; keep share within 0.05 of the rule). See autopilot/DS3_CONTROL_AUDIT.md (rule x owner x control x draw type x keep share x status; list of void statements).

## 6b. Reading (written by W-JV)

Plain strength statement (written 2026-11-14 21:50Z; numbers are in the tables above, base-lot dollars, x1.75 for the user's lots):

1. **B (U7 time stop on fresh entries) is the only rule that holds in BOTH recent and older windows**: max-DD cut L3M +11.7 %, L6M +11.7 %, HOLD +3.3 %, PRE -1.0 %, X' +18.0 %, GAP 0.0 %; mean +1244 / +573 / +799 / -90 / +249 / +5 $/wk; no winning week turned losing; the 5 best weeks kept (98-101 %). It passes the tolerant gate in every window. Strength: SMALL. The delayed-exit placebo (same trigger, exit 1-60 min later) gives the same DD cut on L3M/L6M (10.5 / 11.8 / 11.7 %), so the drawdown cut is NOT specific to the timing of the exit; only the mean is (real +573 vs placebo +238..+548 on L6M, +1244 vs +297..+514 on L3M). The recent DD is one week (W44): with W44 removed from both, B's DD cut turns -5.2 % (L3M and L6M).
2. **A (half size after a lost first trade, non-P7 books)** cuts recent DD (L3M +11.8 %, L6M +11.8 %, HOLD +11.6 %, X' +7.8 %) but makes PRE worse (-7.6 %), costs mean in L3M (-691) and sits inside the day-shifted placebo range on the DD cut (placebo 7.0 / 21.8 / 11.2 % on L3M). With W44 removed A still cuts L3M +27.6 % / L6M +6.2 %. Fails the tolerant gate in PRE.
3. **C (U7 Keltner-mid structure stop with equal-$ lots) is OUT**: it helps L3M mean (+1746) but is clearly worse in the older windows (HOLD DD -16.4 %, PRE -22.3 %, X' -68.2 %, mean -2753 / -3246 $/wk PRE / X'), 2-3 winning weeks turned losing, WF -354 $/wk. Every combination containing C inherits that (AC HOLD -20.4 %, BC -13.9 %, ABC -18.3 %).
4. **AB**: recent best (L3M +25.0 %, L6M +24.0 %, HOLD +15.6 %, mean +636 / +946 / +1391) but PRE -8.6 % and GAP mean -829; interaction is additive (L6M synergy +0.5 cut points, -10 $/wk). AB fails the tolerant gate on PRE; its recent gain comes from A.
5. **D (London range-used-up skip, W-LR, provisional)**: combinations with D are scored only on L3M/L6M so far (no older windows, no placebos on the combos); they cannot lead yet. ABD looks best on recent windows.
6. Candidate for the v2.0 build list now: **B alone** (switch Off/Shadow/Live), with A as a Shadow-only second item pending PRE; C rejected; D pending older windows. This is a weak, small improvement judged against placebos; not a PASS.
7. Recent max DD (-36.4k, 2026-W44) is one week for the stack; most recent DD cuts are about whether a rule trims that week.
Status of work at this write: JV_AB has 42 of 43 months (X' incomplete: 202304 queued), exact AB placebos have L3M/L6M and part of HOLD, D-combinations run L3M..HOLD only. The driver keeps queuing; the page rebuilds only when results land.


## 7. FULL SPEC of each rule exactly as scored (for the v2.0 build)

Order of evaluation inside the engine (outermost last): wb_hooks (F3 context cut, E1/C22/BR3S panel) -> **sm_hooks (K7 flat -45, then B, then C; all three are exit rules plus C's lot scaling)** -> scr_hooks / c_gov (entry gates: skip rules, P7 governor) -> **A (sm1_hooks, outermost: entry-time lot multiplier)**. Exits B and C and the K7 flat are evaluated on 1-second rows of the state-base mid, decision at the close of row r, market exit at row r+1; the first rule of a trade that fires ends it (rule list order: K7 flat, B, C). The engine's native bracket (60-pt stop, 60-pt target for these books) and the 80-pt catastrophe stop stay in place as backstops; an engine exit that happens first simply wins (the rule exit event is dropped if the trade is no longer open).

**A = SM_A6_halfNP7 (entry sizing).** Books K7, M7, U7, H7, A7 (P7 and O7 untouched). At a signal of book B at time t, key K = the six-session ET key of t. Look at the book's CLOSED trades (exit already booked at the signal second) whose own signal key is K; take the first of them by entry time. If its net P&L after fees is < 0 (a loser, whatever the exit type: Stop, StateCut, EarlyCut/time-stop/structure exit all count), the lots of this signal are multiplied by 0.5 in trend_size, applied AFTER the live sizers and after C's equal-$ scaling: lots = max(1, floor(lots*0.5 + 0.5)). A winning (or no) first trade -> normal lots. No skip, no re-arming, applies to every later signal of that book-session (including the third, fourth ...). Stack caps and locks that clamp P7 are not touched (P7 is outside the rule); the day-done and lot-cap clamps for the other books see the already-halved lots. State carried: none beyond the trade list; resets with each new session key. In the live code this needs the per-book session ledger (first closed trade of the session and its sign), nothing else.

**B = U7 time stop on fresh entries.** Book U7 only. Context 'fresh' = chase_k <= 1.0 (side x (close - session first close)/ATR5 at the signal), at most the 2nd U7 entry of the session since the session start (n <= 2) and >= 30 min since the last U7 exit (P7_CONTEXT_DEFS, wb_ctx.Ctx). Rule: exactly 15.0 minutes (900 one-second rows) after the first fill row, if the open P&L at that second (mid, side x (mid - entry_px)) is < -10.0 points, exit the full position at market at the next row: mid - side*0.80 pts slip (engine); exit name EarlyCut. One check only (not a rolling condition); a trade that is at -10 or better at minute 15 is never touched by B. Interaction: B closes the trade, so for A it is a loser (a later U7 signal in the session gets half lots), and the post-cut blackout rules of the engine for EarlyCut exits apply as in the reference.

**C = U7 Keltner-mid structure stop (stop + equal-$ lots).** Book U7 only, all contexts. Level = Keltner mid = EMA20 of 5-min closes (struct_a3 kc), read at the last completed bar at least 60 s old. At the first fill, u0 = side x (kc - entry); the rule is armed only if -60 <= u0 <= -0.5 (mid on the loss side of the entry by 0.5..60 pts) and S = |u0| + 2.0 <= 60; S is then clamped to 25..60 (for lot scaling). The stop is dynamic: each second the level is re-read (same 60-s lag) and the trade exits when side x (mid - entry) <= side x (kc_now - entry) - 2.0 (long: mid <= kc - 2; short: mid >= kc + 2), i.e. the stop trails the mid in both directions. Fill: price = entry + side x (min(stop level in points, current u) - 1.4), i.e. 1.4 pts adverse of the level or the current price whichever is worse (live native central), exit name EarlyCut. Lots: after the live sizers lots x 60/S (S as above, so up to x2.4; round to nearest, min 1; computed from the signal-time level and the last 1-min close as entry proxy), so the $ risk at the structure stop equals the live 60-pt risk. Day caps/locks then apply to those lots. Interaction with B: B's check at minute 15 and C's stop run on the same trades; whichever fires first ends the trade. C changes the lots, which A then halves on a lost-first session.

**Common switch for every rule (v2.0 build): `<Rule>Mode` = Off | Shadow | Live.** Off: rule code skipped. Shadow: the rule is evaluated every time it would act and the would-be action (skip, half size, exit, with the numbers that triggered it) is printed to the log and a CSV, but orders are not changed. Live: the action is taken. Default Shadow for every rule below until it has run live in Shadow for a full period; Live only by explicit decision.

**D = London range-used-up SKIP (W-LR, k = 1; L = same with k = 1.25).** Hook lr_hooks, variant skip, London only (entry session 1, 02:00-08:30 ET), all seven live books. At a fresh entry signal: skip when stop_pts x target_r (the target distance, 60 pts for the live books) > k x (F - R), where R = London range so far (high - low since 02:00 ET) and F = the ATR-only walk-forward forecast of the day's ln range x last close (fc_lr.parquet; defined from 2023-07-21 on, rule inactive before that date). Other sessions untouched (Asia delta 0.0, identity proven by W-LR). Evaluated at the entry gate, before sizing; a skipped signal is not queued. Status PROVISIONAL (W-LR).

**P = P7 Asia same-side block after a loser (W-PR BLK_M30).** Hook pr_hooks par {"blk":{"ev":"min","N":30}}. P7 only, Asia session (18:00-02:00 ET): after a P7 Asia trade closes with net P&L < 0, P7 signals on that same side are blocked for 30 minutes from the exit; the other side and every other book are untouched. Recent-window evidence only (W-PR).

**R = M7 London trade cap (W-RA CAP3; W = CAP2).** Hook ra_hooks, rule capn N=3, books [M7], sess [1]. Instance = (M7, Globex day, London). Once N trades of the instance have closed, any new M7 London entry that day is blocked. Win or lose counts. **V = M7 London block same-side re-entry until an opposite-side signal (W-RA BLKiv).** Hook ra_hooks rule blk ev=iv, books [M7], sess [1]: a candidate entry that has the same side as the most recent closed trade of the instance, and that trade was a loser, is blocked unless an opposite-direction signal of the book has occurred since the loser closed (signals counted whether taken or not). R/W/V are mutually exclusive (same hook, same code path).

**Order of evaluation of the entry-side rules (outermost evaluated first at a signal):** R/W/V block -> P block -> D/L skip -> A half-size flag -> c_gov / scr_hooks gates -> sizers (incl. C) -> day caps/locks. All blocks are before sizing, A changes only lots. Exit-side: K7 flat45, B, C inside sm_hooks.
