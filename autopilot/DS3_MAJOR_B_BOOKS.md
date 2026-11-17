# DS3_MAJOR_B_BOOKS - diversifying books from the shelf, scored against the JL3 stack (W-MB, part B of the MAJOR-CHANGES programme)

**FIVE-LINE SUMMARY (plain; refreshed 2026-11-17 14:12 UTC by an unattended loop)**
1. Tried: all 6836 exported shelf books (NQ 345, 11 other instruments) as daily P&L against the JL3 stack on its 20 worst weeks and five deepest drawdowns, plus 0 NQ books added to JL3 on the exact engine (event injection, shared stack rules).
2. Holds: on the harness screen 72 NQ books are positive in both L6M and HOLD; engine stage 1 so far: 0 of 0 sets cut stack ulcer over the last 12 months, beat the date-shift null (p<=0.2) with positive own P&L (see section 4).
3. Does not: no non-NQ book can be engine-tested (the engine is NQ-only; no price store or product path exists for ES/RTY on the engine, none for the rest); their screen is HARNESS BASIS only; almost all candidates are 2026 regime earners (PRE / X' negative) and the ulcer gain of a screened book is mostly its mean (r=-0.95), so only the excess over the date-shift null counts.
4. Needs in DS7: every candidate here is a NEW book (fade / failed-break / gap / time-of-day / structure), none is a mean-reversion slot that exists today; code needs are in section 6 per book. A candidate counts only after it passes stage 2 (older windows) and the placebo draws.
5. Next: stage 2 (PREUW, X') and lot variants for the best six, shifted-event placebos, then the best 3-5 together and on the part A lot vector; this page refreshes every 30 minutes.

**VERDICT (data ends 2026-10-31; FIRST PASS, no tier claim yet):** header - trials counted = 6836 screened lists (harness basis) + 0 engine cells; correction = date-shift null (30 circular shifts, weekday kept) and excess over null median; no White RC/DSR yet (screen is a first pass; engine finalists get FIRST PASS labels only); PBO not computed (no fitted choice besides the frozen stage-1 rule: selection on the screen, which included HOLD and L6M, so engine HOLD/L6M are NOT untouched; PREUW and X' are the untouched windows for stage 2). In-sample = harness screen; walk-forward = engine windows stage 2. Costs: $4.84 RT per base lot, base lots (x1.75 live column where shown). Data end: engine months to 202610; harness lists to 2026-10-30.

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
(engine results not landed yet)



Status (auto): engine sets scored 0; queue: /mnt/l2/l2vast/_major_b/pending.txt (296 lines open); page rebuilt 2026-11-17 14:12 UTC.
