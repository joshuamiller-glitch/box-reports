# DS3_MAJOR_B_BOOKS - diversifying books from the shelf, scored against the JL3 stack (W-MB, part B of the MAJOR-CHANGES programme)

**FIVE-LINE SUMMARY (plain; refreshed 2026-11-23 07:19 UTC by an unattended loop)**
1. Tried: all 6836 exported shelf books (NQ 345, 11 other instruments) as daily P&L against the JL3 stack on its 20 worst weeks and five deepest drawdowns, plus 65 NQ books added to JL3 on the exact engine (event injection, shared stack rules).
2. Holds: on the harness screen 72 NQ books are positive in both L6M and HOLD; engine stage 1 so far: 25 of 65 sets cut stack ulcer over the last 12 months, beat the date-shift null (p<=0.2) with positive own P&L (see section 4).
3. Does not: no non-NQ book can be engine-tested (the engine is NQ-only; no price store or product path exists for ES/RTY on the engine, none for the rest); their screen is HARNESS BASIS only; almost all candidates are 2026 regime earners (PRE / X' negative) and the ulcer gain of a screened book is mostly its mean (r=-0.95), so only the excess over the date-shift null counts.
4. Needs in DS7: every candidate here is a NEW book (fade / failed-break / gap / time-of-day / structure), none is a mean-reversion slot that exists today; code needs are in section 6 per book. A candidate counts only after it passes stage 2 (older windows) and the placebo draws.
5. Next: stage 2 (PREUW, X') and lot variants for the best six, shifted-event placebos, then the best 3-5 together and on the part A lot vector; this page refreshes every 30 minutes.

**VERDICT (data ends 2026-10-31; FIRST PASS, no tier claim yet):** header - trials counted = 6836 screened lists (harness basis) + 65 engine cells; correction = date-shift null (30 circular shifts, weekday kept) and excess over null median; no White RC/DSR yet (screen is a first pass; engine finalists get FIRST PASS labels only); PBO not computed (no fitted choice besides the frozen stage-1 rule: selection on the screen, which included HOLD and L6M, so engine HOLD/L6M are NOT untouched; PREUW and X' are the untouched windows for stage 2). In-sample = harness screen; walk-forward = engine windows stage 2. Costs: $4.84 RT per base lot, base lots (x1.75 live column where shown). Data end: engine months to 202610; harness lists to 2026-10-30.

## 1. The JL3 stack reference (what a diversifier must help)
Engine JL3 (TL3_EV_JL3), base lots, $4.84, day = ET exit + 6 h, weeks Mon-Sun. Window table (mean $/wk, ulcer, max DD, worst week):
| window | mean $/wk | ulcer | max DD | worst week |
|--|--|--|--|--|
| L3M | 15923 | 11153 | -31109 | -15728 |
| L6M | 19265 | 9597 | -31109 | -15728 |
| HOLD | 9331 | 29479 | -83756 | -37324 |
| GAP | 8525 | 17905 | -42260 | -38896 |
| PREUW | 5811 | 33238 | -91441 | -37617 |
| X' | 2858 | 24248 | -72026 | -37355 |
| ALL | 7493 | 25991 | -91441 | -38896 |

Five deepest drawdowns (daily equity, non-overlapping):
| # | peak day | trough day | depth $ |
|--|--|--|--|
| 1 | 20250128 | 20250307 | -91441 |
| 2 | 20251118 | 20251210 | -83756 |
| 3 | 20240903 | 20240918 | -72026 |
| 4 | 20240131 | 20240410 | -63240 |
| 5 | 20260203 | 20260325 | -58740 |

Twenty worst weeks: 2025-07-07 -38896; 2025-02-17 -37617; 2024-09-02 -37355; 2025-12-01 -37324; 2024-11-18 -30447; 2024-02-05 -30238; 2024-09-30 -30156; 2025-02-03 -27906; 2024-09-09 -22455; 2026-03-23 -19819; 2026-02-02 -19403; 2025-08-11 -17668; 2025-02-24 -17568; 2023-08-28 -17538; 2025-06-09 -17525; 2024-04-08 -17286; 2023-11-13 -17211; 2023-07-31 -16707; 2024-04-01 -16493; 2026-08-31 -15728

## 2. Inventory
Full inventory with engine status and validity: autopilot/SHELF_INVENTORY.md (A fade/ORB/RSI2/PRO/TB/X books, B open/close/session/zone/UW/TICK/FLOW, C other instruments). Route: NQ books reach the engine through th_uwbooks/uw_inject.py as an injected book; identity TL3_MB_ID = JL3 trade for trade on 202610 (691 / 37,159.82) and 202504 (637 / 41,239.76). X1, X2, X6-X8, S7: no engine definition; X3-X5: 0 raw engine trades; O7 is live (lot change = part A).

## 3. Harness screen of the whole shelf against JL3 (no engine; screen only)
Each list scaled to equal risk (1,200 $/trade), P&L in base-lot dollars, $4.84 where the list carries costs (harness proxy costs otherwise). "ww" = candidate P&L on the 20 worst JL3 weeks; "dd" = inside the five deepest JL3 drawdowns; "exc" = change in stack ulcer minus the median change of 30 date-shifted copies (negative = better than chance; units $). Rows are chosen by the frozen rules named in each caption, never by hand.
**3a. NQ books positive in L6M and HOLD (n >= 100), best excess ulcer first (London and NY AM first marked by session):**
| book | session | trades | L6M $/wk | HOLD | PREUW | X' | corr | P&L on 20 worst wks | P&L in 5 deep DDs | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.T2FNQ.5f51c2c9 | nyam | 2590 | 451 | 668 | -871 | -68 | -0.06 | 9315 | 12826 | -2313 | 0.00 |
| NQ.T2FNQ.cb3c2fd8 | nyam | 2590 | 501 | 690 | -794 | -48 | -0.07 | 8027 | 11796 | -2105 | 0.00 |
| NQ.DIST_Q13lead.ecd086 | nyam | 275 | 936 | 287 | 156 | -20 | -0.04 | 10769 | 14922 | -1810 | 0.00 |
| NQ.T2FNQ.e77382a9 | pre | 813 | 6 | 314 | 229 | 172 | -0.05 | 15912 | 16696 | -1255 | 0.07 |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | 304 | 1259 | 528 | -883 | 402 | -0.03 | 5578 | 18599 | -1169 | 0.03 |
| NQ.FADE_LV.d6f9339b | nypm | 999 | 34 | 547 | -476 | -265 | -0.06 | -8101 | 8087 | -985 | 0.17 |
| NQ.FADE_LV.b6a2c134 | nyam | 505 | 202 | 354 | -245 | -290 | -0.08 | -3078 | 12819 | -920 | 0.13 |
| NQ.FADE_LV.02ddffde | nyam | 891 | 624 | 351 | 549 | -322 | -0.11 | -2832 | 13471 | -870 | 0.30 |
| NQ.T2FNQ.80f7f135 | pre | 799 | 93 | 153 | -19 | 125 | -0.06 | 11327 | 11057 | -812 | 0.23 |
| NQ.FADE_LV.628da3af | nyam | 890 | 875 | 382 | 250 | -365 | -0.13 | -658 | 12078 | -767 | 0.23 |
| NQ.LRS.ef7b7bdf | nypm | 1710 | 551 | 358 | -400 | -197 | 0.06 | -185 | 11944 | -634 | 0.07 |
| NQ.T2F1B.0d6b7e92 | nyam | 578 | 246 | 159 | 678 | -237 | -0.01 | -8864 | 6720 | -596 | 0.20 |
| NQ.FADE_LV.90b9322c | nyam | 486 | 189 | 40 | 288 | -88 | 0.01 | -3453 | -1376 | -562 | 0.13 |
| NQ.DIST_DISQ1550drift.78db2c | close | 891 | 668 | 463 | 64 | -429 | 0.03 | -4891 | -106 | -468 | 0.23 |
| NQ.FADE_LV.0a316e6d | nyam | 1158 | 1020 | 876 | -984 | -549 | 0.03 | -12753 | 20726 | -448 | 0.30 |
| NQ.T2F1B.6f26737b | nyam | 578 | 883 | 253 | 1062 | -297 | -0.02 | -10151 | 6621 | -217 | 0.37 |
| NQ.T2F1B.f3379ae5 | nyam | 578 | 407 | 145 | 560 | -126 | -0.02 | -9534 | 5071 | -208 | 0.37 |
| NQ.T2F1B.1624de42 | nyam | 578 | 1393 | 861 | 1290 | -446 | -0.02 | -10506 | 13028 | -131 | 0.40 |
| NQ.FADE_LV.a22a708e | nyam | 502 | 888 | 62 | 298 | -140 | 0.01 | -6466 | -4608 | -94 | 0.47 |
| NQ.FADE_LV.9ed009c4 | nyam | 502 | 919 | 47 | 176 | -146 | 0.01 | -7313 | -4987 | -69 | 0.47 |
| NQ.FADE_LV.4edbfdf0 | asia | 317 | 385 | 555 | 489 | -79 | -0.09 | 1985 | 5016 | -63 | 0.40 |
| NQ.FADE_LV.64f81a6c | asia | 313 | 467 | 705 | 174 | -133 | -0.11 | 6530 | 6529 | -43 | 0.43 |
| NQ.T2F1B.c690abeb | nyam | 578 | 587 | 339 | 728 | -168 | -0.02 | -10066 | 9035 | -31 | 0.47 |
| NQ.FADE_LV.ee0bd493 | nyam | 894 | 19 | 215 | 313 | -75 | -0.12 | -4175 | 7533 | -20 | 0.50 |
| NQ.FADE_LV.ea5594c4 | nyam | 388 | 578 | 309 | -97 | -90 | -0.05 | -1032 | -93 | -7 | 0.50 |
| NQ.T2FNQ.951c87a7 | close | 1393 | 652 | 123 | -476 | 6 | 0.02 | -6183 | -810 | -0 | 0.50 |
| NQ.FADE_LV.95f735fd | asia | 317 | 128 | 658 | 267 | -109 | -0.10 | 2919 | 3896 | 28 | 0.53 |
| NQ.FADE_LV.b5c93a40 | nyam | 894 | 17 | 78 | 481 | -67 | -0.13 | -893 | 7479 | 79 | 0.57 |
| NQ.FADE_LV.a8632973 | nypm | 523 | 815 | 173 | -175 | 205 | -0.01 | 5434 | 1598 | 83 | 0.53 |
| NQ.FADE_LV.ddd22834 | asia | 317 | 406 | 602 | 50 | -40 | -0.11 | 3585 | 7652 | 126 | 0.60 |

**3b. NQ London / NY AM / pre books, any sign (n >= 60), best excess first (the sessions where D7 has no edge):**
| book | session | trades | L6M $/wk | HOLD | PREUW | X' | corr | P&L on 20 worst wks | P&L in 5 deep DDs | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.T2FNQ.ad35592c | nyam | 5820 | -6377 | -3686 | -1155 | -747 | 0.04 | -77308 | -119232 | -13202 | 0.27 |
| NQ.T2FNQ.9420e96f | nyam | 8499 | -6078 | -3479 | -3941 | -1160 | -0.05 | -49003 | -64105 | -11411 | 0.40 |
| NQ.T2FNQ.f122c2fa | pre | 2697 | -2544 | -532 | -272 | -387 | -0.05 | -18154 | 14586 | -4985 | 0.00 |
| NQ.T2FNQ.110f76b8 | nyam | 5999 | -4014 | -1079 | -1711 | -497 | 0.02 | -16933 | -48632 | -3841 | 0.00 |
| NQ.T2FNQ.a03b92a3 | nyam | 6662 | -6262 | -6596 | -1789 | -955 | -0.00 | -79266 | -136101 | -3142 | 0.20 |
| NQ.T2FNQ.7e707179 | nyam | 2837 | -1472 | -1333 | -1233 | -213 | -0.05 | -7184 | -379 | -3068 | 0.00 |
| NQ.T2FNQ.a812abc9 | pre | 2697 | -2001 | -1401 | -1210 | -337 | -0.15 | -9919 | -12977 | -2977 | 0.00 |
| NQ.T2FNQ.5f51c2c9 | nyam | 2590 | 451 | 668 | -871 | -68 | -0.06 | 9315 | 12826 | -2313 | 0.00 |
| NQ.T2FNQ.db20c9e9 | nyam | 2439 | -131 | 11 | -1275 | -169 | -0.05 | -1334 | -1705 | -2131 | 0.10 |
| NQ.T2FNQ.cb3c2fd8 | nyam | 2590 | 501 | 690 | -794 | -48 | -0.07 | 8027 | 11796 | -2105 | 0.00 |
| NQ.T2FNQ.889c8257 | pre | 2494 | -357 | -1251 | -866 | -420 | -0.11 | 10031 | -8547 | -2102 | 0.07 |
| NQ.T2FNQ.819ac99e | pre | 2969 | -987 | -1427 | -576 | -467 | -0.00 | -10543 | -3889 | -2012 | 0.00 |
| NQ.FADE_LV.13aae8f0 | nyam | 893 | 133 | -285 | 687 | -201 | -0.15 | 7329 | 21906 | -1910 | 0.17 |
| NQ.DIST_Q13lead.ecd086 | nyam | 275 | 936 | 287 | 156 | -20 | -0.04 | 10769 | 14922 | -1810 | 0.00 |
| NQ.T2FNQ.58e02ca4 | nyam | 5820 | -3625 | -4075 | -2013 | -573 | -0.06 | -53304 | -82279 | -1624 | 0.40 |
| NQ.T2FNQ.ce5a2a7a | nyam | 2439 | -25 | -100 | -1233 | -150 | -0.05 | -2878 | -6075 | -1618 | 0.20 |
| NQ.T2FNQ.69c22cdf | pre | 810 | -124 | 235 | 386 | 123 | -0.05 | 21107 | 17098 | -1602 | 0.07 |
| NQ.T2FNQ.2c9e1db3 | nyam | 5999 | -2874 | -1780 | -2363 | -697 | -0.09 | -33691 | -43073 | -1593 | 0.23 |
| NQ.T2FNQ.e59db09a | pre | 810 | -101 | 94 | 415 | 125 | -0.06 | 20605 | 15715 | -1551 | 0.07 |
| NQ.T2FNQ.f4072305 | pre | 815 | -1758 | -294 | -147 | 18 | -0.06 | -588 | 1300 | -1534 | 0.00 |

**3c. Non-NQ books (HARNESS BASIS ONLY, no engine path, own-instrument dollars at equal risk; DS7 would need a new instrument path):**
| book | session | trades | L6M $/wk | HOLD | PREUW | X' | corr | P&L on 20 worst wks | P&L in 5 deep DDs | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|
| GC.donchian.1deefb1e (GC) | nyam | 3794 | 5436 | 4662 | 2 | -162 | 0.02 | 58977 | 25079 | -4435 | 0.03 |
| GC.donchian.4c0dd205 (GC) | nyam | 2463 | 1421 | 5331 | 114 | -699 | 0.00 | 75175 | -14358 | -1556 | 0.23 |
| YM.60.3f877350 (YM) | nyam | 650 | 1699 | 663 | -12 | -140 | -0.01 | 17630 | 24268 | -1494 | 0.13 |
| YM.vwap_reclaim.69ed4e93 (YM) | nyam | 1118 | 1490 | 844 | -419 | -22 | -0.01 | 12015 | 34924 | -1349 | 0.20 |
| GC.T2FGC.cf582995 (GC) | nypm | 426 | 1231 | 1105 | 15 | -100 | -0.04 | 76459 | 29869 | -1260 | 0.07 |
| YM.60.d508c6f5 (YM) | close | 1444 | 455 | 482 | -352 | 2 | -0.04 | 3756 | 9859 | -1066 | 0.00 |
| GC.T2FGC.103248f0 (GC) | asia | 372 | 1283 | 2473 | -180 | -165 | -0.04 | 77792 | 44033 | -1059 | 0.03 |
| YM.60.42e6e2cb (YM) | close | 1444 | 454 | 566 | -390 | 28 | -0.03 | 5616 | 9788 | -1032 | 0.00 |
| YM.60.01f1c4e3 (YM) | close | 1444 | 454 | 538 | -390 | 32 | -0.04 | 4980 | 10072 | -1024 | 0.00 |
| GC.T2FGC.5d326597 (GC) | nypm | 449 | 364 | 252 | 216 | -172 | -0.04 | 61905 | 21386 | -946 | 0.00 |
| ES.F_K.466a42b9 (ES) | pre | 470 | 636 | 304 | -160 | -4 | 0.03 | 4833 | 9160 | -858 | 0.10 |
| CL.T2FCL.2577fc67 (CL) | nypm | 117 | 637 | 396 | 99 | -77 | -0.00 | 4163 | 11176 | -851 | 0.00 |
| GC.T120.140e446e (GC) | nyam | 305 | 339 | 575 | -16 | 116 | -0.04 | 8803 | 14971 | -800 | 0.00 |
| ES.F_K.40623030 (ES) | close | 1073 | 432 | 109 | 365 | 98 | 0.01 | 5959 | 1086 | -798 | 0.00 |
| GC.T2FGC.645d7f69 (GC) | asia | 372 | 651 | 1667 | -133 | -221 | -0.02 | 59849 | 15838 | -794 | 0.13 |
| GC.T30.a695b6ca (GC) | nyam | 1125 | 814 | 247 | -163 | -177 | 0.00 | 11979 | 17219 | -786 | 0.23 |
| ES.F_K.8f15fbb8 (ES) | close | 1069 | 867 | 229 | 444 | 45 | 0.01 | 7502 | -6742 | -758 | 0.03 |
| RTY.F_DC_b5_n55.aa46c4a6 (RTY) | close | 320 | 265 | 201 | 413 | 36 | 0.01 | -100 | 6946 | -710 | 0.03 |
| ES.F_K.669d6618 (ES) | close | 1428 | 1133 | 681 | 470 | -77 | 0.06 | 1200 | 8213 | -670 | 0.40 |
| GC.T2FGC.3f595fd7 (GC) | asia | 372 | 1486 | 1487 | -153 | -161 | -0.01 | 59031 | 19362 | -669 | 0.10 |

By instrument, count positive in L6M and HOLD and ALL: {'GC': 122, 'NQ': 56, 'YM': 44, 'ES': 37, 'RTY': 36, 'CL': 20, 'BTC': 13, 'MBT': 11, 'NKD': 7, 'ZB': 1}; count with p_ALL <= 0.05: 572 of 6836 (chance expects 342).

## 4. Engine marginal test (JL3 + one injected book, same stack cap, day rules, protection layers)
**Window RECENT12** (stack = JL3 + MB1; d = set minus JL3; base lots $4.84; mean in $/wk; "freed" = change in the other books' P&L $/wk; p = fraction of 30 date-shifted copies of the book that did as well on ulcer):
| book | session | lots | trades | book $/wk | d mean | d ulcer | d maxDD | d worst wk | book on JL3 worst wks | book in JL3 deep DDs | corr | freed $/wk | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TL3_MB_IBST20_L4 |  |  | 21 | 1790 | 1458 | -4135 | 4951 | 0 | 1041 | 16783 | -0.14 | -332 | -4343 | 0.00 |
| TL3_MB_COMBO5 |  |  | 323 | 3387 | 3396 | -4616 | 17280 | 3957 | -3095 | 22083 | -0.06 | 9 | -3282 | 0.07 |
| TL3_MB_COMBO3 |  |  | 173 | 1675 | 1665 | -3838 | 6527 | 2176 | -8171 | 14049 | -0.12 | -10 | -2569 | 0.13 |
| TL3_MB_ORBASIA15S75_L4 |  |  | 40 | 424 | 231 | -3321 | 8880 | 0 | 4962 | 11049 | -0.05 | -193 | -2326 | 0.00 |
| TL3_MB_FADELVd6f9339b_L4 |  |  | 159 | 601 | 496 | -1902 | 5306 | 2416 | -9581 | 8090 | -0.01 | -105 | -2243 | 0.00 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P11 |  |  | 46 | 95 | 118 | -1909 | 8630 | 165 | 14406 | 13456 | -0.02 | 23 | -1978 | 0.00 |
| TL3_MB_O7V1000_k10_L4 |  |  | 44 | 945 | 906 | -1942 | 0 | 0 | 6161 | 11133 | 0.04 | -38 | -1932 | 0.00 |
| old-harness sleeve IBS_t20_n1 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 20 | 710 | 480 | -1998 | 2475 | 0 | -8604 | 19977 | -0.15 | -230 | -1922 | 0.20 |
| O7 variant t0=1000 k=1.0 stop40/tgt90 flat 1600 | nyam | 2 | 44 | 476 | 472 | -1835 | 0 | 0 | 3091 | 5607 | 0.03 | -4 | -1752 | 0.00 |
| NQ.FADE_LV.d6f9339b | nypm | 2 | 187 | 339 | 347 | -1740 | 6822 | 3341 | -5682 | 7407 | -0.07 | 8 | -1706 | 0.10 |
| TL3_MB_O7V1000_k10_L1 |  |  | 44 | 391 | 341 | -1571 | -0 | 0 | 3590 | 6436 | 0.12 | -50 | -1542 | 0.00 |
| old-harness sleeve ORB_ASIA_15_v1__s75 (asia), replayed by clock, stop 75 pts, no target | asia | 2 | 40 | 523 | 488 | -1028 | 1885 | 0 | -1599 | 1112 | 0.02 | -35 | -1435 | 0.10 |
| old-harness sleeve ORB_ASIA_15_v1__s60 (asia), replayed by clock, stop 60 pts, no target | asia | 2 | 40 | 458 | 418 | -1008 | 1385 | 0 | -1464 | 3237 | 0.07 | -39 | -1384 | 0.03 |
| NQ.LRS.69f1daac | pre | 1 | 76 | 871 | 639 | -857 | 2406 | 1475 | 6651 | 21037 | 0.04 | -232 | -1351 | 0.03 |
| TL3_MB_IBST20_L1 |  |  | 21 | 379 | 335 | -1004 | 890 | 0 | -2570 | 7596 | -0.18 | -43 | -1194 | 0.00 |
| O7 variant t0=0830 k=0.5 stop40/tgt90 flat 1600 | pre | 2 | 109 | -100 | -164 | -516 | -2712 | -660 | 171 | 8431 | -0.01 | -64 | -1128 | 0.00 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P37 |  |  | 48 | 514 | 379 | -1139 | 5329 | 860 | -4410 | 12422 | 0.02 | -135 | -1074 | 0.00 |
| NQ.FADE_LV.4edbfdf0 | asia | 2 | 120 | 504 | 667 | -1750 | 4051 | 2176 | 1224 | 8317 | -0.10 | 163 | -973 | 0.20 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P23 |  |  | 46 | 527 | 490 | -1089 | 4994 | 675 | -6009 | 9947 | 0.03 | -36 | -944 | 0.00 |
| TL3_MB_FADELVd6f9339b_L1 |  |  | 187 | 198 | 222 | -1212 | 3220 | 1670 | -2834 | 3361 | -0.06 | 24 | -942 | 0.00 |
| NQ.DIST_DISBPRELcont.7bb655 | pre | 3 | 67 | 151 | 320 | -412 | -1261 | 315 | 1152 | 11087 | -0.01 | 169 | -812 | 0.00 |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | 2 | 55 | 915 | 952 | -975 | -2623 | 0 | -2864 | 6203 | 0.08 | 38 | -783 | 0.17 |
| NQ.FADE_LV.a8632973 | nypm | 3 | 78 | 457 | 434 | -1000 | 1922 | 2156 | 5103 | 4695 | 0.08 | -23 | -772 | 0.03 |
| TL3_MB_ORBASIA15S75_L1 |  |  | 40 | 439 | 423 | -475 | -480 | 0 | -790 | 21 | 0.04 | -16 | -717 | 0.03 |
| NQ.DIST_DISQ1550drift.78db2c | close | 1 | 163 | 519 | 519 | -734 | 2241 | 355 | 2836 | 3594 | 0.07 | 0 | -503 | 0.10 |
| NQ.MONDAY_LONG_A.1c2b44c6 | daily | 1 | 42 | 1166 | 1222 | -1049 | 9944 | 0 | -390 | 5231 | 0.04 | 57 | -429 | 0.30 |
| TL3_MB_FADELV4edbfdf0_L1 |  |  | 120 | 254 | 527 | -1431 | 2210 | 471 | 207 | 3369 | -0.09 | 273 | -386 | 0.00 |
| NQ.FADE_LV.b6a2c134 | nyam | 2 | 94 | 100 | -15 | 58 | -1958 | 3041 | 592 | 4636 | -0.06 | -116 | -322 | 0.07 |
| TL3_MB_AG1_COMBO3 |  |  | 180 | 1485 | 1450 | -914 | 2151 | 2385 | -16810 | 7845 | -0.12 | -35 | -315 | 0.37 |
| NQ.FADE_LV.90b9322c | nyam | 1 | 101 | 247 | 253 | -2 | 2236 | 3380 | 3026 | -4993 | 0.00 | 6 | -107 | 0.37 |
| TL3_MB_MONDAYLONGA1c2b44c6_L2 |  |  | 42 | 2316 | 2334 | -778 | 14231 | 0 | 2841 | 6602 | 0.02 | 18 | -71 | 0.40 |
| NQ.T2FNQ.e77382a9 | pre | 1 | 195 | 384 | 24 | -267 | 1358 | 5782 | 2182 | 9839 | -0.05 | -360 | 5 | 0.53 |
| NQ.FADE_LV.6fb3aa4d | london | 3 | 41 | -84 | 145 | -806 | 3721 | 4461 | 2881 | -262 | 0.00 | 229 | 97 | 0.77 |
| NQ.LRS.ef7b7bdf | nypm | 1 | 183 | 326 | 305 | 81 | -2764 | -530 | 898 | -1366 | 0.17 | -21 | 102 | 0.77 |
| NQ.T2F1B.6f26737b | nyam | 7 | 112 | 253 | 289 | -764 | -1877 | 774 | -6753 | 957 | 0.02 | 36 | 139 | 0.90 |
| TL3_MB_IBST20_L2_P23 |  |  | 25 | 448 | 375 | 342 | 621 | -740 | -1030 | -2188 | -0.01 | -74 | 157 | 0.63 |
| TL3_MB_ORBASIA15S75_L2_P11 |  |  | 42 | -46 | 180 | -1399 | 3195 | 3669 | -1364 | -1196 | 0.07 | 225 | 258 | 0.90 |
| TL3_MB_FADELV4edbfdf0_L4 |  |  | 119 | 582 | 413 | 621 | 259 | 3598 | 3792 | 9240 | -0.14 | -169 | 274 | 0.60 |
| O7 variant t0=0200 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 79 | -368 | -15 | -542 | -1986 | 0 | 7577 | 4134 | 0.06 | 353 | 500 | 0.90 |
| NQ.T2F1B.fa471237 | nyam | 7 | 115 | -60 | -14 | -511 | -1877 | 774 | -6568 | -1968 | 0.00 | 46 | 508 | 1.00 |
| O7 variant t0=0300 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 66 | 111 | 99 | -635 | 421 | 3590 | -2218 | -3195 | 0.02 | -12 | 554 | 1.00 |
| NQ.T2F1B.f3379ae5 | nyam | 5 | 122 | -140 | -42 | -440 | -2198 | 1619 | -5475 | -3043 | -0.00 | 99 | 694 | 1.00 |
| NQ.FADE_LV.02ddffde | nyam | 2 | 168 | -215 | -396 | 1457 | 1178 | 2081 | -2512 | -4060 | -0.09 | -182 | 705 | 0.97 |
| NQ.T2FNQ.80f7f135 | pre | 1 | 201 | 286 | -55 | -183 | 2972 | 7396 | -623 | 7384 | -0.01 | -341 | 816 | 0.90 |
| NQ.FADE_LV.628da3af | nyam | 2 | 168 | -225 | -407 | 1633 | 1103 | 2081 | -2567 | -4915 | -0.09 | -182 | 837 | 0.97 |
| NQ.FADE_LV.0a316e6d | nyam | 2 | 225 | 930 | 863 | 70 | -6433 | -2615 | -430 | 2747 | 0.05 | -67 | 895 | 0.90 |
| O7 variant t0=0200 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 134 | -381 | -246 | -604 | -1450 | 2156 | 7958 | 297 | 0.09 | 134 | 962 | 1.00 |
| NQ.T2F1B.e3dde7b1 | nyam | 10 | 102 | 40 | 109 | -10 | 1096 | 3361 | -2090 | -10567 | -0.04 | 69 | 1328 | 1.00 |
| old-harness sleeve RSI2_t10 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 15 | 9 | -28 | 1751 | -11970 | 0 | 0 | -979 | -0.10 | -37 | 1583 | 0.87 |
| TL3_MB_ORBASIA15S75_L2_P23 |  |  | 43 | -297 | -356 | 2309 | -8034 | -570 | -4994 | -7676 | 0.09 | -59 | 1712 | 1.00 |
| TL3_MB_O7V1000_k10_L2_P11 |  |  | 41 | -384 | -362 | 1188 | 1881 | 7855 | 3590 | -9157 | -0.01 | 22 | 1758 | 0.97 |
| TL3_MB_O7V1000_k10_L2_P23 |  |  | 39 | -871 | -782 | 2147 | -3814 | -3899 | -3899 | -14501 | -0.02 | 89 | 1899 | 1.00 |
| O7 variant t0=0300 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 137 | -143 | -310 | 1397 | -3913 | 3590 | 1449 | -11381 | 0.07 | -166 | 1913 | 1.00 |
| TL3_MB_FADELV4edbfdf0_L2_P37 |  |  | 112 | -800 | -568 | 1603 | -5688 | -504 | -5392 | -5790 | 0.06 | 232 | 1941 | 1.00 |
| TL3_MB_FADELV4edbfdf0_L2_P23 |  |  | 113 | -947 | -1098 | 2840 | -7973 | -1029 | -2242 | -8810 | -0.03 | -150 | 1971 | 1.00 |
| TL3_MB_FADELVd6f9339b_L2_P23 |  |  | 203 | -2230 | -2033 | 3054 | -3752 | 576 | -1611 | -16523 | 0.07 | 197 | 1989 | 0.93 |
| TL3_MB_O7V1000_k10_L2_P37 |  |  | 47 | -1016 | -984 | 2328 | -1590 | -1590 | -5629 | -13611 | 0.05 | 32 | 2281 | 1.00 |
| TL3_MB_FADELV4edbfdf0_L2_P11 |  |  | 113 | -1113 | -933 | 2094 | -98 | 5591 | -3518 | -12401 | -0.01 | 180 | 2498 | 0.97 |
| TL3_MB_ORBASIA15S75_L2_P37 |  |  | 43 | -141 | -355 | 2649 | -5694 | -925 | -2429 | -14887 | 0.08 | -214 | 2543 | 1.00 |
| TL3_MB_AG1_COMBO5 |  |  | 367 | 3461 | 3490 | 1377 | -10963 | 2150 | -3542 | 24233 | -0.03 | 30 | 2622 | 1.00 |
| TL3_MB_IBST20_L2_P11 |  |  | 27 | -854 | -717 | 3221 | -11970 | 0 | 0 | -4534 | -0.04 | 137 | 2836 | 0.97 |
| TL3_MB_FADELVd6f9339b_L2_P11 |  |  | 220 | -2616 | -2752 | 6772 | -7033 | -1040 | -13666 | -20303 | 0.06 | -137 | 3599 | 0.97 |
| l2vast/ds3/out/SF/trades_CRT_M15_M1_close_ib.parquet | london | 9 | 287 | -2410 | -2473 | 6051 | -16314 | -302 | -13965 | -30528 | 0.01 | -63 | 4961 | 0.93 |
| TL3_MB_FADELVd6f9339b_L2_P37 |  |  | 198 | -2305 | -2013 | 5830 | -9001 | -2248 | -12305 | -30329 | 0.07 | 292 | 5817 | 1.00 |
| TL3_MB_IBST20_L2_P37 |  |  | 29 | -1111 | -1218 | 9395 | -4435 | -740 | -6114 | -21873 | -0.04 | -107 | 6237 | 1.00 |

**Window L6M** (stack = JL3 + MB1; d = set minus JL3; base lots $4.84; mean in $/wk; "freed" = change in the other books' P&L $/wk; p = fraction of 30 date-shifted copies of the book that did as well on ulcer):
| book | session | lots | trades | book $/wk | d mean | d ulcer | d maxDD | d worst wk | book on JL3 worst wks | book in JL3 deep DDs | corr | freed $/wk | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.FADE_LV.4edbfdf0 | asia | 2 | 68 | 230 | 114 | -560 | 3492 | -8206 | -680 | 0 | -0.11 | -116 | -997 | 0.03 |
| TL3_MB_FADELV4edbfdf0_L4 |  |  | 67 | 514 | 10 | 1197 | -3767 | -17205 | -1389 | 0 | -0.13 | -504 | -871 | 0.20 |
| TL3_MB_COMBO5 |  |  | 162 | 3768 | 3749 | -842 | 2822 | -5543 | -2630 | 0 | -0.06 | -19 | -836 | 0.13 |
| TL3_MB_IBST20_L2_P37 |  |  | 10 | 98 | 162 | 272 | -1575 | -889 | -1575 | 0 | -0.02 | 65 | -684 | 0.20 |
| TL3_MB_FADELV4edbfdf0_L1 |  |  | 68 | 161 | 178 | -446 | 1181 | -3737 | -185 | 0 | -0.11 | 17 | -619 | 0.03 |
| TL3_MB_IBST20_L2_P11 |  |  | 12 | -1243 | -937 | -162 | 1229 | 0 | 0 | 0 | 0.01 | 306 | -480 | 0.33 |
| NQ.FADE_LV.90b9322c | nyam | 1 | 51 | 386 | 338 | -50 | -156 | -3470 | -1035 | 0 | 0.10 | -47 | -399 | 0.27 |
| TL3_MB_FADELV4edbfdf0_L2_P23 |  |  | 64 | -1187 | -1326 | 560 | -796 | -5021 | -419 | 0 | -0.07 | -139 | -370 | 0.33 |
| TL3_MB_O7V1000_k10_L2_P37 |  |  | 23 | -955 | -960 | 402 | -3145 | -615 | -615 | 0 | 0.07 | -6 | -349 | 0.13 |
| NQ.FADE_LV.02ddffde | nyam | 2 | 85 | -90 | -120 | 348 | -497 | -2911 | -1169 | 0 | 0.03 | -29 | -322 | 0.30 |
| NQ.FADE_LV.628da3af | nyam | 2 | 84 | -133 | -162 | 361 | -397 | -2966 | -1224 | 0 | 0.02 | -29 | -281 | 0.30 |
| NQ.FADE_LV.b6a2c134 | nyam | 2 | 42 | -30 | -107 | -60 | -830 | 0 | 0 | 0 | -0.07 | -76 | -269 | 0.37 |
| TL3_MB_IBST20_L2_P23 |  |  | 8 | 1328 | 1322 | 310 | 0 | 0 | 0 | 0 | -0.01 | -6 | -245 | 0.30 |
| TL3_MB_O7V1000_k10_L2_P23 |  |  | 19 | -786 | -681 | 379 | -3145 | 0 | 0 | 0 | 0.05 | 105 | -240 | 0.20 |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | 2 | 27 | 1049 | 1269 | 128 | 674 | -3540 | 91 | 0 | 0.10 | 220 | -236 | 0.23 |
| NQ.FADE_LV.d6f9339b | nypm | 2 | 76 | -79 | -191 | 183 | 406 | -3451 | -1260 | 0 | -0.07 | -112 | -217 | 0.40 |
| TL3_MB_COMBO3 |  |  | 92 | 1161 | 788 | 334 | -2811 | -9558 | -6645 | 0 | -0.16 | -374 | -212 | 0.37 |
| NQ.DIST_DISBPRELcont.7bb655 | pre | 3 | 34 | -23 | 405 | -201 | 4071 | 1169 | 2711 | 0 | -0.00 | 428 | -160 | 0.33 |
| TL3_MB_ORBASIA15S75_L4 |  |  | 15 | 375 | -267 | 25 | 0 | 3133 | 8871 | 0 | -0.07 | -643 | -157 | 0.37 |
| old-harness sleeve IBS_t20_n1 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 5 | -296 | -546 | 118 | -832 | -2959 | -3645 | 0 | -0.21 | -250 | -147 | 0.40 |
| NQ.T2FNQ.80f7f135 | pre | 1 | 97 | 165 | -395 | 277 | -1012 | -2897 | 41 | 0 | -0.00 | -560 | -144 | 0.27 |
| old-harness sleeve RSI2_t10 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 6 | -966 | -1006 | 173 | 0 | 0 | 0 | 0 | -0.09 | -40 | -121 | 0.37 |
| O7 variant t0=0830 k=0.5 stop40/tgt90 flat 1600 | pre | 2 | 55 | -209 | -106 | -14 | 2611 | 2441 | 2441 | 0 | 0.01 | 103 | -111 | 0.33 |
| TL3_MB_O7V1000_k10_L2_P11 |  |  | 20 | 8 | -142 | 340 | -3899 | 0 | 0 | 0 | 0.04 | -150 | -105 | 0.37 |
| NQ.T2FNQ.e77382a9 | pre | 1 | 92 | 152 | -442 | 313 | -1297 | -3182 | -244 | 0 | -0.00 | -594 | -84 | 0.37 |
| TL3_MB_ORBASIA15S75_L2_P37 |  |  | 19 | -11 | -86 | -79 | 2013 | -932 | -404 | 0 | 0.16 | -74 | -81 | 0.40 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P11 |  |  | 24 | -478 | -502 | 498 | 13 | -1127 | 385 | 0 | -0.02 | -23 | -78 | 0.40 |
| TL3_MB_FADELVd6f9339b_L1 |  |  | 76 | 46 | -1 | -7 | 1030 | -630 | -630 | 0 | -0.05 | -47 | -68 | 0.43 |
| O7 variant t0=0200 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 74 | -873 | -1473 | 296 | 4135 | -1311 | 1976 | 0 | 0.11 | -600 | -33 | 0.47 |
| TL3_MB_FADELVd6f9339b_L2_P37 |  |  | 88 | -2785 | -2241 | 1516 | -4163 | -1904 | -615 | 0 | 0.06 | 544 | -25 | 0.50 |
| NQ.FADE_LV.0a316e6d | nyam | 2 | 109 | 1283 | 1386 | -256 | 2700 | -106 | 3162 | 0 | 0.04 | 103 | -22 | 0.43 |
| NQ.FADE_LV.6fb3aa4d | london | 3 | 22 | 105 | 427 | -519 | 2042 | 2042 | 755 | 0 | 0.03 | 322 | 6 | 0.50 |
| NQ.DIST_DISQ1550drift.78db2c | close | 1 | 78 | 610 | 610 | -50 | -400 | -275 | -275 | 0 | 0.13 | -0 | 9 | 0.53 |
| old-harness sleeve ORB_ASIA_15_v1__s75 (asia), replayed by clock, stop 75 pts, no target | asia | 2 | 15 | 281 | 125 | 224 | 0 | -142 | 4445 | 0 | 0.07 | -156 | 27 | 0.53 |
| NQ.LRS.69f1daac | pre | 1 | 43 | 235 | 100 | 509 | -2841 | -5860 | -2230 | 0 | 0.02 | -135 | 29 | 0.53 |
| O7 variant t0=0200 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 41 | -571 | -578 | -80 | 3440 | 0 | 0 | 0 | 0.09 | -7 | 32 | 0.60 |
| TL3_MB_O7V1000_k10_L4 |  |  | 22 | 1549 | 1567 | -192 | 0 | 0 | 0 | 0 | 0.03 | 18 | 32 | 0.53 |
| TL3_MB_FADELV4edbfdf0_L2_P11 |  |  | 68 | -1022 | -776 | 943 | -3737 | -2014 | -724 | 0 | -0.02 | 246 | 37 | 0.77 |
| old-harness sleeve ORB_ASIA_15_v1__s60 (asia), replayed by clock, stop 60 pts, no target | asia | 2 | 15 | 388 | 182 | 217 | 0 | 3 | 3315 | 0 | 0.12 | -207 | 67 | 0.53 |
| TL3_MB_ORBASIA15S75_L1 |  |  | 15 | 301 | 165 | 142 | 0 | 1378 | 2225 | 0 | 0.06 | -137 | 86 | 0.67 |
| NQ.FADE_LV.a8632973 | nypm | 3 | 37 | 295 | 295 | -32 | 0 | 665 | 665 | 0 | 0.11 | 0 | 94 | 0.70 |
| O7 variant t0=0300 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 32 | -59 | -214 | -195 | 2484 | 2484 | 300 | 0 | -0.08 | -156 | 101 | 0.67 |
| O7 variant t0=0300 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 66 | -114 | -517 | 820 | -3310 | -3520 | -449 | 0 | -0.03 | -403 | 128 | 0.63 |
| NQ.LRS.ef7b7bdf | nypm | 1 | 81 | 273 | 273 | -6 | -220 | -1614 | -1614 | 0 | 0.17 | -0 | 138 | 0.67 |
| TL3_MB_ORBASIA15S75_L2_P23 |  |  | 18 | -313 | -417 | 416 | -2285 | 0 | 0 | 0 | 0.01 | -104 | 141 | 0.77 |
| TL3_MB_O7V1000_k10_L1 |  |  | 22 | 490 | 450 | -6 | 0 | 0 | 0 | 0 | 0.12 | -40 | 151 | 0.83 |
| TL3_MB_IBST20_L1 |  |  | 5 | 301 | 227 | 421 | -2713 | -4839 | -3550 | 0 | -0.16 | -74 | 157 | 0.67 |
| TL3_MB_FADELVd6f9339b_L2_P23 |  |  | 94 | -2851 | -2456 | 2007 | -6715 | -3971 | -615 | 0 | 0.08 | 396 | 163 | 0.60 |
| TL3_MB_FADELVd6f9339b_L4 |  |  | 67 | 660 | 354 | 902 | -1952 | -11241 | -2524 | 0 | -0.00 | -306 | 184 | 0.57 |
| O7 variant t0=1000 k=1.0 stop40/tgt90 flat 1600 | nyam | 2 | 22 | 685 | 677 | 5 | 0 | 0 | 0 | 0 | 0.03 | -7 | 184 | 0.83 |
| TL3_MB_ORBASIA15S75_L2_P11 |  |  | 17 | -352 | -240 | 150 | -1175 | 0 | 0 | 0 | -0.02 | 112 | 233 | 0.80 |
| TL3_MB_IBST20_L4 |  |  | 5 | -729 | -1054 | 1033 | -4547 | -5988 | -7299 | 0 | -0.20 | -325 | 415 | 0.60 |
| TL3_MB_FADELVd6f9339b_L2_P11 |  |  | 107 | -3096 | -3107 | 2594 | -5695 | -4503 | -3214 | 0 | 0.09 | -11 | 484 | 0.70 |
| NQ.T2F1B.e3dde7b1 | nyam | 10 | 45 | 216 | 142 | 562 | -3551 | -4537 | -4537 | 0 | -0.09 | -74 | 502 | 0.97 |
| TL3_MB_FADELV4edbfdf0_L2_P37 |  |  | 66 | -1093 | -1058 | 835 | -3145 | -1377 | -1134 | 0 | 0.15 | 35 | 708 | 0.97 |
| NQ.T2F1B.f3379ae5 | nyam | 5 | 53 | -148 | -169 | 996 | -5984 | -6579 | -5453 | 0 | -0.01 | -21 | 828 | 1.00 |
| NQ.T2F1B.fa471237 | nyam | 7 | 51 | -302 | -348 | 1334 | -7577 | -6923 | -5798 | 0 | -0.07 | -45 | 1253 | 1.00 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P23 |  |  | 23 | 268 | 234 | 1198 | -7335 | 525 | 520 | 0 | 0.09 | -33 | 1270 | 0.87 |
| NQ.T2F1B.6f26737b | nyam | 7 | 49 | 167 | 103 | 1249 | -7577 | -6923 | -5798 | 0 | -0.03 | -65 | 1303 | 1.00 |
| NQ.MONDAY_LONG_A.1c2b44c6 | daily | 1 | 22 | 1766 | 1938 | 1436 | -7989 | -5414 | -4125 | 0 | 0.16 | 172 | 1321 | 0.97 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P37 |  |  | 24 | 288 | 170 | 1207 | -7335 | 525 | 520 | 0 | 0.09 | -118 | 1360 | 0.87 |
| TL3_MB_AG1_COMBO3 |  |  | 96 | 816 | 529 | 681 | -360 | -4981 | -8184 | 0 | -0.12 | -287 | 1363 | 0.83 |
| l2vast/ds3/out/SF/trades_CRT_M15_M1_close_ib.parquet | london | 9 | 137 | -2093 | -2264 | 4180 | -20086 | -14312 | -6313 | 0 | 0.04 | -172 | 1808 | 0.93 |
| TL3_MB_AG1_COMBO5 |  |  | 183 | 2830 | 2647 | 1047 | -1927 | -6690 | -7598 | 0 | -0.03 | -182 | 1915 | 0.77 |
| TL3_MB_MONDAYLONGA1c2b44c6_L2 |  |  | 22 | 3693 | 3699 | 2743 | -12429 | -3924 | -4610 | 0 | 0.13 | 6 | 2026 | 0.93 |

**Window HOLD** (stack = JL3 + MB1; d = set minus JL3; base lots $4.84; mean in $/wk; "freed" = change in the other books' P&L $/wk; p = fraction of 30 date-shifted copies of the book that did as well on ulcer):
| book | session | lots | trades | book $/wk | d mean | d ulcer | d maxDD | d worst wk | book on JL3 worst wks | book in JL3 deep DDs | corr | freed $/wk | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TL3_MB_IBST20_L4 |  |  | 16 | 4350 | 4012 | -6712 | 4951 | 0 | 8341 | 16783 | -0.08 | -338 | -6837 | 0.00 |
| TL3_MB_COMBO5 |  |  | 161 | 2999 | 3038 | -6645 | 17280 | 3957 | -465 | 22083 | -0.07 | 39 | -4568 | 0.10 |
| TL3_MB_COMBO3 |  |  | 81 | 2197 | 2557 | -5936 | 6527 | 2176 | -1526 | 14049 | -0.07 | 359 | -3731 | 0.13 |
| TL3_MB_ORBASIA15S75_L4 |  |  | 25 | 473 | 737 | -5016 | 8880 | 0 | -3909 | 11049 | -0.04 | 264 | -3495 | 0.00 |
| TL3_MB_FADELVd6f9339b_L4 |  |  | 92 | 541 | 639 | -3202 | 5306 | 2416 | -7056 | 8090 | -0.02 | 98 | -3266 | 0.00 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P11 |  |  | 22 | 678 | 749 | -3051 | 8630 | 165 | 14020 | 13456 | -0.01 | 70 | -3031 | 0.00 |
| TL3_MB_O7V1000_k10_L4 |  |  | 22 | 330 | 235 | -2845 | 0 | 0 | 6161 | 11133 | 0.03 | -95 | -2846 | 0.00 |
| O7 variant t0=1000 k=1.0 stop40/tgt90 flat 1600 | nyam | 2 | 22 | 263 | 263 | -2755 | 0 | 0 | 3091 | 5607 | 0.03 | 0 | -2669 | 0.00 |
| old-harness sleeve IBS_t20_n1 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 15 | 1732 | 1523 | -3042 | 2475 | 0 | -4960 | 19977 | -0.11 | -209 | -2601 | 0.23 |
| NQ.FADE_LV.d6f9339b | nypm | 2 | 111 | 764 | 893 | -2677 | 6822 | 3341 | -4422 | 7407 | -0.06 | 129 | -2560 | 0.10 |
| TL3_MB_O7V1000_k10_L1 |  |  | 22 | 291 | 230 | -2352 | -0 | 0 | 3590 | 6436 | 0.11 | -61 | -2353 | 0.00 |
| NQ.LRS.69f1daac | pre | 1 | 33 | 1516 | 1186 | -1464 | 2406 | 1475 | 8881 | 21037 | 0.08 | -330 | -2197 | 0.03 |
| old-harness sleeve ORB_ASIA_15_v1__s75 (asia), replayed by clock, stop 75 pts, no target | asia | 2 | 25 | 768 | 857 | -1617 | 1885 | 0 | -6044 | 1112 | -0.01 | 89 | -2178 | 0.10 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P37 |  |  | 24 | 744 | 591 | -2159 | 5329 | 860 | -4930 | 12422 | -0.07 | -153 | -2065 | 0.00 |
| old-harness sleeve ORB_ASIA_15_v1__s60 (asia), replayed by clock, stop 60 pts, no target | asia | 2 | 25 | 528 | 659 | -1584 | 1385 | 0 | -4779 | 3237 | 0.02 | 131 | -2036 | 0.07 |
| TL3_MB_MONDAYLONGA1c2b44c6_L1_P23 |  |  | 23 | 790 | 751 | -2080 | 4994 | 675 | -6530 | 9947 | -0.04 | -40 | -1831 | 0.00 |
| TL3_MB_IBST20_L1 |  |  | 16 | 458 | 445 | -1653 | 890 | 0 | 980 | 7596 | -0.21 | -13 | -1733 | 0.00 |
| O7 variant t0=0830 k=0.5 stop40/tgt90 flat 1600 | pre | 2 | 54 | 11 | -223 | -766 | -2712 | -660 | -2270 | 8431 | -0.03 | -234 | -1531 | 0.00 |
| TL3_MB_AG1_COMBO3 |  |  | 84 | 2164 | 2386 | -1942 | 2151 | 2385 | -8626 | 7845 | -0.11 | 222 | -1393 | 0.13 |
| TL3_MB_FADELVd6f9339b_L1 |  |  | 111 | 353 | 449 | -1812 | 3220 | 1670 | -2204 | 3361 | -0.07 | 95 | -1375 | 0.00 |
| NQ.FADE_LV.a8632973 | nypm | 3 | 41 | 622 | 576 | -1484 | 1922 | 2156 | 4438 | 4695 | 0.06 | -46 | -1319 | 0.03 |
| NQ.MONDAY_LONG_A.1c2b44c6 | daily | 1 | 20 | 556 | 495 | -2115 | 9944 | 0 | 3735 | 5231 | -0.13 | -61 | -1291 | 0.33 |
| TL3_MB_MONDAYLONGA1c2b44c6_L2 |  |  | 20 | 915 | 947 | -2265 | 14231 | 0 | 7450 | 6602 | -0.15 | 31 | -1242 | 0.20 |
| NQ.DIST_DISBPRELcont.7bb655 | pre | 3 | 33 | 328 | 233 | -548 | -1261 | 315 | -1559 | 11087 | -0.01 | -95 | -1175 | 0.00 |
| TL3_MB_ORBASIA15S75_L1 |  |  | 25 | 579 | 687 | -759 | -480 | 0 | -3015 | 21 | 0.03 | 107 | -1155 | 0.07 |
| NQ.FADE_LV.4edbfdf0 | asia | 2 | 52 | 783 | 1229 | -2427 | 4051 | 2176 | 1903 | 8317 | -0.07 | 446 | -1106 | 0.20 |
| NQ.DIST_DISBNRELrev.6628b1 | nyam | 2 | 28 | 778 | 630 | -1504 | -2623 | 0 | -2954 | 6203 | 0.06 | -148 | -1074 | 0.13 |
| NQ.DIST_DISQ1550drift.78db2c | close | 1 | 85 | 426 | 426 | -1081 | 2241 | 355 | 3111 | 3594 | 0.01 | 0 | -799 | 0.10 |
| TL3_MB_FADELV4edbfdf0_L1 |  |  | 52 | 349 | 882 | -1990 | 2210 | 471 | 392 | 3369 | -0.06 | 533 | -360 | 0.00 |
| NQ.FADE_LV.b6a2c134 | nyam | 2 | 52 | 233 | 77 | 106 | -1958 | 3041 | 592 | 4636 | -0.05 | -155 | -359 | 0.10 |
| NQ.T2F1B.6f26737b | nyam | 7 | 63 | 341 | 479 | -1605 | -1877 | 774 | -956 | 957 | 0.10 | 139 | -268 | 0.23 |
| NQ.FADE_LV.90b9322c | nyam | 1 | 50 | 106 | 166 | 14 | 2236 | 3380 | 4061 | -4993 | -0.13 | 60 | -65 | 0.43 |
| NQ.T2FNQ.e77382a9 | pre | 1 | 103 | 621 | 498 | -506 | 1358 | 5782 | 2426 | 9839 | -0.10 | -123 | 20 | 0.60 |
| NQ.LRS.ef7b7bdf | nypm | 1 | 102 | 381 | 337 | 122 | -2764 | -530 | 2512 | -1366 | 0.17 | -43 | 119 | 0.67 |
| NQ.FADE_LV.6fb3aa4d | london | 3 | 19 | -276 | -142 | -1033 | 3721 | 4461 | 2126 | -262 | -0.04 | 135 | 176 | 0.80 |
| NQ.T2F1B.fa471237 | nyam | 7 | 64 | 187 | 325 | -1253 | -1877 | 774 | -771 | -1968 | 0.09 | 139 | 245 | 0.87 |
| TL3_MB_ORBASIA15S75_L2_P11 |  |  | 25 | 265 | 606 | -2150 | 3195 | 3669 | -1364 | -1196 | 0.13 | 341 | 295 | 0.90 |
| TL3_MB_IBST20_L2_P23 |  |  | 17 | -446 | -588 | 407 | 621 | -740 | -1030 | -2188 | -0.03 | -143 | 412 | 0.73 |
| TL3_MB_FADELV4edbfdf0_L4 |  |  | 52 | 651 | 822 | 514 | 259 | 3598 | 5181 | 9240 | -0.17 | 171 | 507 | 0.63 |
| NQ.T2F1B.f3379ae5 | nyam | 5 | 69 | -132 | 88 | -1014 | -2198 | 1619 | -21 | -3043 | 0.01 | 220 | 716 | 0.90 |
| O7 variant t0=0200 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 38 | -162 | 557 | -782 | -1986 | 0 | 7577 | 4134 | 0.03 | 720 | 728 | 0.90 |
| O7 variant t0=0300 k=1.0 stop40/tgt90 flat 0825 | london | 2 | 34 | 284 | 418 | -884 | 421 | 3590 | -2519 | -3195 | 0.13 | 134 | 803 | 1.00 |
| NQ.FADE_LV.02ddffde | nyam | 2 | 83 | -341 | -677 | 2058 | 1178 | 2081 | -1343 | -4060 | -0.22 | -336 | 1168 | 0.97 |
| NQ.T2FNQ.80f7f135 | pre | 1 | 104 | 409 | 290 | -366 | 2972 | 7396 | -664 | 7384 | -0.01 | -118 | 1267 | 0.97 |
| NQ.FADE_LV.0a316e6d | nyam | 2 | 116 | 570 | 331 | 187 | -6433 | -2615 | -3592 | 2747 | 0.06 | -239 | 1348 | 0.90 |
| NQ.FADE_LV.628da3af | nyam | 2 | 84 | -320 | -656 | 2315 | 1103 | 2081 | -1343 | -4915 | -0.22 | -336 | 1410 | 0.97 |
| O7 variant t0=0200 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 60 | 120 | 1001 | -1006 | -1450 | 2156 | 5982 | 297 | 0.08 | 880 | 1475 | 1.00 |
| NQ.T2F1B.e3dde7b1 | nyam | 10 | 57 | -139 | 76 | -207 | 1096 | 3361 | 2447 | -10567 | 0.05 | 215 | 1788 | 1.00 |
| TL3_MB_ORBASIA15S75_L2_P23 |  |  | 25 | -281 | -295 | 3303 | -8034 | -570 | -4994 | -7676 | 0.14 | -14 | 2489 | 1.00 |
| old-harness sleeve RSI2_t10 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 9 | 1000 | 966 | 2550 | -11970 | 0 | 0 | -979 | -0.10 | -34 | 2545 | 0.97 |
| TL3_MB_FADELV4edbfdf0_L2_P37 |  |  | 46 | -502 | -70 | 2115 | -5688 | -504 | -4258 | -5790 | -0.06 | 432 | 2598 | 1.00 |
| TL3_MB_O7V1000_k10_L2_P11 |  |  | 21 | -783 | -586 | 1661 | 1881 | 7855 | 3590 | -9157 | -0.09 | 197 | 2651 | 0.97 |
| O7 variant t0=0300 k=0.5 stop40/tgt90 flat 0825 | london | 2 | 71 | -173 | -99 | 1813 | -3913 | 3590 | 1898 | -11381 | 0.17 | 75 | 2800 | 1.00 |
| TL3_MB_O7V1000_k10_L2_P23 |  |  | 20 | -957 | -885 | 3073 | -3814 | -3899 | -3899 | -14501 | -0.11 | 72 | 2912 | 1.00 |
| TL3_MB_FADELV4edbfdf0_L2_P23 |  |  | 49 | -704 | -865 | 4046 | -7973 | -1029 | -1823 | -8810 | 0.05 | -161 | 3010 | 1.00 |
| TL3_MB_FADELVd6f9339b_L2_P23 |  |  | 109 | -1598 | -1603 | 3887 | -3752 | 576 | -997 | -16523 | 0.07 | -6 | 3323 | 0.90 |
| TL3_MB_AG1_COMBO5 |  |  | 184 | 4102 | 4347 | 1646 | -10963 | 2150 | 4056 | 24233 | -0.02 | 245 | 3366 | 1.00 |
| TL3_MB_FADELV4edbfdf0_L2_P11 |  |  | 45 | -1206 | -1093 | 2813 | -98 | 5591 | -2794 | -12401 | 0.00 | 112 | 3631 | 0.97 |
| TL3_MB_O7V1000_k10_L2_P37 |  |  | 24 | -1079 | -1008 | 3334 | -1590 | -1590 | -5014 | -13611 | 0.03 | 71 | 3642 | 1.00 |
| TL3_MB_ORBASIA15S75_L2_P37 |  |  | 24 | -274 | -630 | 3954 | -5694 | -925 | -2025 | -14887 | 0.00 | -356 | 3858 | 1.00 |
| TL3_MB_IBST20_L2_P11 |  |  | 15 | -458 | -492 | 4821 | -11970 | 0 | 0 | -4534 | -0.08 | -34 | 4480 | 1.00 |
| TL3_MB_FADELVd6f9339b_L2_P11 |  |  | 113 | -2127 | -2392 | 9247 | -7033 | -1040 | -10452 | -20303 | 0.03 | -265 | 5390 | 0.97 |
| l2vast/ds3/out/SF/trades_CRT_M15_M1_close_ib.parquet | london | 9 | 150 | -2732 | -2685 | 7613 | -16314 | -302 | -7651 | -30528 | -0.02 | 47 | 6713 | 0.93 |
| TL3_MB_FADELVd6f9339b_L2_P37 |  |  | 110 | -1817 | -1782 | 8184 | -9001 | -2248 | -11690 | -30329 | 0.10 | 35 | 8412 | 1.00 |
| TL3_MB_IBST20_L2_P37 |  |  | 19 | -2339 | -2620 | 13739 | -4435 | -740 | -4539 | -21873 | -0.07 | -281 | 9628 | 1.00 |

**Window PREUW** (stack = JL3 + MB1; d = set minus JL3; base lots $4.84; mean in $/wk; "freed" = change in the other books' P&L $/wk; p = fraction of 30 date-shifted copies of the book that did as well on ulcer):
| book | session | lots | trades | book $/wk | d mean | d ulcer | d maxDD | d worst wk | book on JL3 worst wks | book in JL3 deep DDs | corr | freed $/wk | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TL3_MB_COMBO5 |  |  | 237 | 253 | 376 | -5449 | 1849 | 6651 | 235 | -3967 | -0.11 | 123 | -7308 | 0.00 |
| NQ.FADE_LV.d6f9339b | nypm | 2 | 171 | 279 | 208 | -3583 | 1841 | 1157 | 1322 | -28 | -0.09 | -71 | -4299 | 0.03 |
| old-harness sleeve IBS_t20_n1 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 21 | 165 | 146 | -942 | -4519 | 0 | -1800 | -3019 | -0.10 | -19 | -3126 | 0.37 |
| NQ.MONDAY_LONG_A.1c2b44c6 | daily | 1 | 32 | 371 | 488 | -3606 | 4576 | 0 | 1185 | 4815 | 0.03 | 117 | -2693 | 0.00 |
| old-harness sleeve ORB_ASIA_15_v1__s75 (asia), replayed by clock, stop 75 pts, no target | asia | 2 | 38 | -98 | -310 | -534 | 338 | 0 | -3539 | 6257 | 0.22 | -212 | -2367 | 0.20 |
| NQ.FADE_LV.4edbfdf0 | asia | 2 | 59 | 552 | 828 | -3799 | 6661 | 5099 | -902 | 253 | -0.10 | 276 | 799 | 0.83 |
| old-harness sleeve ORB_ASIA_15_v1__s60 (asia), replayed by clock, stop 60 pts, no target | asia | 2 | 38 | 115 | -95 | 1224 | -3716 | 0 | -5064 | 357 | 0.21 | -210 | 977 | 0.77 |
| O7 variant t0=1000 k=1.0 stop40/tgt90 flat 1600 | nyam | 2 | 33 | 102 | -25 | 1355 | -3679 | 0 | 1857 | -1998 | 0.23 | -127 | 1454 | 0.73 |
| TL3_MB_COMBO3 |  |  | 103 | -153 | 1 | 1071 | -12701 | 5099 | -929 | -17075 | -0.11 | 154 | 2201 | 0.70 |

**Window X'** (stack = JL3 + MB1; d = set minus JL3; base lots $4.84; mean in $/wk; "freed" = change in the other books' P&L $/wk; p = fraction of 30 date-shifted copies of the book that did as well on ulcer):
| book | session | lots | trades | book $/wk | d mean | d ulcer | d maxDD | d worst wk | book on JL3 worst wks | book in JL3 deep DDs | corr | freed $/wk | exc ulcer | p null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.FADE_LV.d6f9339b | nypm | 2 | 399 | -87 | -102 | 650 | 487 | -330 | 2067 | 3257 | -0.06 | -14 | -1117 | 0.37 |
| O7 variant t0=1000 k=1.0 stop40/tgt90 flat 1600 | nyam | 2 | 97 | 66 | 55 | -1065 | 0 | 0 | 9987 | 2222 | 0.06 | -11 | -978 | 0.33 |
| NQ.FADE_LV.4edbfdf0 | asia | 2 | 107 | -25 | -89 | 258 | -2243 | -1663 | 1625 | -1124 | -0.10 | -65 | -433 | 0.33 |
| old-harness sleeve ORB_ASIA_15_v1__s60 (asia), replayed by clock, stop 60 pts, no target | asia | 2 | 65 | 24 | -22 | 382 | 3545 | 0 | 1796 | 6873 | 0.13 | -46 | 998 | 0.60 |
| old-harness sleeve ORB_ASIA_15_v1__s75 (asia), replayed by clock, stop 75 pts, no target | asia | 2 | 65 | 282 | 216 | -33 | 4440 | 0 | 461 | 9043 | 0.14 | -66 | 1515 | 0.97 |
| NQ.MONDAY_LONG_A.1c2b44c6 | daily | 1 | 63 | 339 | 333 | 1451 | 2512 | 0 | 3936 | -1608 | 0.03 | -6 | 2830 | 0.97 |
| old-harness sleeve IBS_t20_n1 (close/overnight), replayed by clock, stop 300 pts, no target | close | 2 | 62 | 911 | 773 | 2631 | -755 | 0 | 3375 | -13697 | -0.01 | -138 | 3845 | 1.00 |


## 5. Method notes and open items (hand-written by W-MB, 2026-11-17)
- Engine route: NQ books only, through code/th_major_b/mb_inject.py (copy of th_uwbooks/uw_inject.py plus the CDE-sizer SB_BI fix), appended outermost to the JL3 set; identity TL3_MB_ID = JL3 trade for trade on 202610 and 202504 after the fix. Conversion of a harness list = replay by clock (entry time, stop, target, flat at the harness exit time); the engine then applies its own fills, caps and day rules.
- O7 extension: events generated from replica/ports.py OpenDrive logic (501 of the 506 raw O7 signal times reproduced), windows 02:00, 03:00, 08:30, 10:00 x arm threshold 0.5 / 1.0 median5, stop 40 / target 90. DR5m_pb1 (DS3_OPEN) re-tested the same way. Shelved-for-non-edge families not yet rebuilt as events (ORB NY k3, RSI2 t10, washout, session-lock, TOPEN variants): their old-harness trade lists are in the inventory; they need the same conversion and are the next build.
- Stages are automatic (autostage.py, frozen rules in its header): finalists = top 6 by RECENT12 ulcer change that beat the date-shift null; then older months, shifted-event placebos, lot variants x0.5 and x2, then best-3 and best-5 combinations. Combination on the part A lot vector is not wired (A page not final); add by building a base JSON from the A set and calling mk_mb.build_multi(base=...).
- Queue: /mnt/l2/l2vast/_major_b/pending.txt (410 set-months at stage 1, about 540 more at stage 2). Throughput is limited by queue position behind the DD queue and by box-1 priority.
- DS7 need for every row: new code (a book); none maps to an existing mean-reversion slot. X3-X5 slots are empty, X1/X2/X6-X8 and S7 have no definition.


PARTIAL TABLE: engine set-months landed so far: 1050 (a window is scored only when all its months have landed; sets with fewer months are not shown).
Status (auto): engine sets scored 65; queue: /mnt/l2/l2vast/_major_b/pending.txt (59 lines open); page rebuilt 2026-11-23 07:19 UTC.
