# FD_LIQ - T-FIND-DRESSED, NQ / ES / RTY candidates dressed with the FULL stack (FD-LIQ). Updated 2026-11-10 03:10Z

Post-hoc, Shadow only, no PASS claims. First-order per-trade re-simulation on 1-s paths (ES/RTY L2 state arrays built slim from raw mbp-10; coverage per candidate in column l2cov); exact engine only where the DS7 replica covers the instrument/book: NOT used here (first-order, flagged). Lots continuous at equal $1,200 risk per trade. Pair (RV) books and daily books are not dressed here (no stop distance / two legs).
Procedure per candidate (own trades): layer screens -> top-3 per layer (CUT loss cut L2/PP, PRO profit rule, SIZ ER sizer, ZON zones, LCK cooldown/locks, STK stack-rule slots) by all-weeks Calmar -> joint 3^6 stack, pick = max in-sample Calmar -> validation of the WHOLE procedure: purged monthly walk-forward (26 w train, 7 d embargo, from 2024-02) and a permuted-effect null that repeats the whole screen+joint search on layer effects re-assigned to random trades (B=60). In-sample dressed numbers are search maxima and are NOT evidence by themselves.

Candidates dressed so far: 1816. L2 variant WF ok: 51; with null p <= .10 as well: 4.

## Ranking (Standing Rule 2): (1) recent L6M drawdown and mean, (2) bi-weekly WF of the whole procedure (primary OOS), (3) PRE/X tolerant. Top 40 by share of refit periods beating naked, then recent OOS $
| id | instr | sess | l2cov | naked L6M mean / maxDD | dressed L6M mean / maxDD | dressed L3M mean | biweekly WF: % periods beating naked / n periods | OOS total d vs n | last 13 periods d vs n | WF cal d vs n | null p | PRE check | carrier | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.T2FNQ.590a38d0 | NQ | nypm | 1.00 | -3177 / 60946 | 314 / 4400 | -115 | 92 / 65 | -65848 vs -609375 | 5732 vs -61623 | -0.35 vs -0.40 | n/a | ok | PRO NT(0.65,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.d70f2c27 | NQ | nypm | 1.00 | -1968 / 39395 | 757 / 2383 | 1520 | 92 / 65 | 7178 vs -312966 | -6108 vs -39395 | 0.14 vs -0.40 | 0.54 | ok | PRO NT(0.5,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.b4d6bcb2 | NQ | nyam | 1.00 | -1869 / 61849 | 968 / 2039 | 600 | 92 / 65 | -19321 vs -423060 | -6544 vs -62001 | -0.27 vs -0.40 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.58e02ca4 | NQ | nyam | 1.00 | -1865 / 76225 | 237 / 9819 | 73 | 92 / 65 | -22071 vs -372766 | -8722 vs -76377 | -0.33 vs -0.40 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| ES.T2F1B.418ebba1 | ES | nyam | 1.00 | -9 / 3932 | 296 / 401 | -19 | 89 / 72 | 9541 vs -46721 | 2539 vs -2479 | 1.14 vs -0.36 | 0.67 | ok | PRO NT(0.9,) | WATCH (WF ok, null not) |
| ES.T2F1B.ead810fa | ES | nyam | 1.00 | -11 / 3012 | 251 / 290 | -14 | 89 / 72 | 14174 vs -39771 | 982 vs -1954 | 2.46 vs -0.36 | 0.56 | ok | PRO TR(0.7, 0.25) | WATCH (WF ok, null not) |
| NQ.T2FNQ.63f3f762 | NQ | close | 1.00 | -1567 / 61562 | 1014 / 1395 | 424 | 88 / 65 | -28862 vs -309046 | -1787 vs -61562 | -0.37 vs -0.40 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.2c9e1db3 | NQ | nyam | 1.00 | -1325 / 57948 | 1160 / 1407 | 1030 | 88 / 65 | -1432 vs -306592 | -11458 vs -58245 | -0.03 vs -0.40 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| ES.T2F1B.d0b5d0fb | ES | nyam | 1.00 | -14 / 3932 | 227 / 451 | -27 | 88 / 72 | 11049 vs -45727 | 1766 vs -2552 | 1.29 vs -0.36 | 0.39 | ok | PRO NT(0.5,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.102364a8 | NQ | close | 1.00 | -1316 / 40879 | 149 / 776 | -62 | 88 / 64 | -9114 vs -244096 | 1651 vs -40879 | -0.17 vs -0.41 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| ES.T2F1B.e8b78ed4 | ES | nyam | 1.00 | -20 / 5663 | 275 / 403 | -39 | 85 / 72 | 9263 vs -52214 | 3611 vs -3677 | 0.73 vs -0.36 | 0.36 | ok | PRO NT(0.65,) | WATCH (WF ok, null not) |
| ES.T2F1B.c607e3ab | ES | nyam | 1.00 | -11 / 3012 | 165 / 400 | -4 | 83 / 72 | 7572 vs -38861 | 605 vs -1954 | 1.02 vs -0.36 | 0.66 | ok | PRO TR(0.5, 0.25) | WATCH (WF ok, null not) |
| ES.T2F1B.c450ea77 | ES | nyam | 1.00 | -72 / 5663 | 231 / 447 | -22 | 82 / 72 | -534 vs -55789 | 2720 vs -4449 | -0.02 vs -0.36 | n/a | ok | PRO NT(0.8,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.6883cc0b | NQ | nyam | 1.00 | -753 / 26687 | 1189 / 2316 | 1170 | 79 / 63 | 21773 vs -114216 | 20293 vs -27310 | 0.80 vs -0.41 | 0.30 | ok | PRO NT(0.65,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.e5a76808 | NQ | nypm | 1.00 | -1110 / 25360 | 38 / 1471 | 185 | 78 / 65 | 8051 vs -179713 | 11671 vs -25530 | 0.33 vs -0.40 | 0.43 | ok | PRO NT(0.5,) | WATCH (WF ok, null not) |
| RTY.T2FRTY.f171b7f3 | RTY | nypm | 1.00 | -1290 / 39127 | 128 / 2580 | 8 | 78 / 65 | -33855 vs -279510 | -103 vs -35280 | -0.32 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | no |
| NQ.T2FNQ.a03b92a3 | NQ | nyam | 1.00 | -6486 / 141828 | -38 / 7182 | 153 | 75 / 65 | -38931 vs -506923 | -6878 vs -140143 | -0.36 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | no |
| RTY.T2FRTY.e5779119 | RTY | close | 1.00 | -1181 / 49871 | -267 / 4055 | -277 | 75 / 65 | -37978 vs -201921 | -16705 vs -43946 | -0.37 vs -0.40 | n/a | ok | STK SK(30, 15, 0) | no |
| ES.T2FES.4a0a7f1a | ES | nypm | 1.00 | -134 / 25896 | 1052 / 1390 | -112 | 75 / 64 | -13186 vs -220368 | -9 vs -8780 | -0.22 vs -0.40 | n/a | ok | LCK LK(60, 99, 2.0) | no |
| ES.T2FES.9bbbd5f8 | ES | close | 1.00 | -1743 / 61046 | 143 / 3826 | 377 | 75 / 64 | -21366 vs -161572 | -8221 vs -62458 | -0.22 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | in-sample only (WF/null fail) |
| RTY.T2FRTY.375dae00 | RTY | nyam | 1.00 | -588 / 24011 | 758 / 904 | -139 | 74 / 65 | -9063 vs -188604 | 321 vs -14555 | -0.34 vs -0.40 | n/a | ok | LCK LK(120, 99, 99.0) | in-sample only (WF/null fail) |
| RTY.T2FRTY.33a85f54 | RTY | nyam | 1.00 | -569 / 17269 | -112 / 3238 | -81 | 74 / 65 | -17913 vs -156296 | -2279 vs -16473 | -0.39 vs -0.40 | n/a | ok | LCK LK(60, 2, 4.0) | no |
| RTY.T2FRTY.100f4882 | RTY | nypm | 1.00 | -2402 / 60418 | 78 / 1195 | -133 | 74 / 65 | -49888 vs -295789 | -2759 vs -57879 | -0.40 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | in-sample only (WF/null fail) |
| RTY.T2FRTY.e2e9ff5d | RTY | close | 1.00 | -1103 / 20544 | 28 / 1944 | -165 | 74 / 65 | -31954 vs -127230 | -3556 vs -18176 | -0.37 vs -0.40 | n/a | ok | SIZ ER(10, 0.2, 'high', 0.25) | in-sample only (WF/null fail) |
| RTY.T2FRTY.c3cc82a0 | RTY | nypm | 1.00 | -420 / 22646 | 165 / 2828 | -120 | 74 / 65 | -13800 vs -202150 | -4051 vs -15586 | -0.36 vs -0.40 | n/a | ok | STK SK(30, 15, 5) | in-sample only (WF/null fail) |
| ES.T2FES.df1ee8d5 | ES | nyam | 1.00 | -2283 / 61183 | 238 / 4341 | -80 | 74 / 65 | -19920 vs -353276 | -5949 vs -58519 | -0.33 vs -0.40 | n/a | ok | STK SK(30, 15, 0) | in-sample only (WF/null fail) |
| ES.T2FES.07de187f | ES | close | 1.00 | 509 / 4175 | 225 / 816 | 150 | 72 / 65 | -17338 vs -86911 | 4464 vs 7493 | -0.31 vs -0.35 | n/a | ok | STK SK(30, 15, 5) | no |
| RTY.T2FRTY.78edb266 | RTY | nypm | 1.00 | -2051 / 55135 | 2 / 2083 | -77 | 72 / 65 | -33534 vs -281253 | -4087 vs -52731 | -0.33 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | in-sample only (WF/null fail) |
| RTY.T2FRTY.ac27f1a7 | RTY | nypm | 1.00 | -493 / 41195 | -251 / 5648 | -17 | 72 / 65 | -64365 vs -288955 | -5652 vs -36409 | -0.39 vs -0.40 | n/a | ok | LCK LK(120, 99, 2.0) | no |
| RTY.T2FRTY.23d16e7c | RTY | nypm | 1.00 | -2613 / 52372 | -364 / 7172 | -378 | 72 / 65 | -32052 vs -151699 | -9508 vs -52824 | -0.40 vs -0.40 | n/a | ok | STK SK(0, 15, 5) | no |
| ES.T2FES.ca426c2e | ES | nypm | 0.92 | 0 / 18068 | 118 / 2617 | 66 | 72 / 72 | -27562 vs -89874 | -11417 vs -14576 | -0.33 vs -0.32 | n/a | ok | SIZ ER(40, 0.2, 'low', 0.25) | in-sample only (WF/null fail) |
| NQ.T2FNQ.ad49c4fb | NQ | nypm | 1.00 | -1212 / 23388 | 140 / 4067 | 317 | 71 / 65 | 25588 vs -88799 | 8583 vs -23386 | 1.22 vs -0.40 | 0.38 | ok | PRO NT(0.65,) | WATCH (WF ok, null not) |
| ES.T2FES.a3f7360d | ES | nyam | 1.00 | -305 / 22000 | 757 / 4201 | 517 | 71 / 65 | -21744 vs -265982 | 5487 vs -5462 | -0.30 vs -0.40 | n/a | ok | LCK LK(60, 2, 2.0) | in-sample only (WF/null fail) |
| ES.T2FES.15595767 | ES | close | 1.00 | 672 / 5768 | 319 / 583 | 38 | 71 / 65 | -10238 vs -60112 | 4515 vs 10004 | -0.27 vs -0.34 | n/a | ok | STK SK(30, 0, 5) | in-sample only (WF/null fail) |
| NQ.T2FNQ.f7fb214c | NQ | nypm | 1.00 | -2113 / 48462 | 905 / 5354 | 194 | 71 / 65 | -6474 vs -216457 | 1598 vs -45639 | -0.10 vs -0.40 | n/a | ok | PRO NT(0.5,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.3f378067 | NQ | nypm | 1.00 | -2635 / 53953 | 184 / 1770 | 58 | 71 / 65 | -32285 vs -391559 | 209 vs -49788 | -0.36 vs -0.40 | n/a | ok | SIZ ER(40, 0.2, 'low', 0.25) | no |
| NQ.T2FNQ.f6617bd0 | NQ | nyam | 1.00 | -814 / 32457 | -63 / 2257 | -17 | 71 / 65 | -8116 vs -185407 | -1611 vs -29880 | -0.18 vs -0.39 | n/a | ok | LCK LK(120, 99, 2.0) | no |
| ES.T2FES.c26754ae | ES | pre | 1.00 | -2865 / 37609 | -399 / 7369 | 57 | 71 / 65 | -22914 vs -173118 | -4555 vs -36433 | -0.33 vs -0.40 | n/a | ok | LCK LK(60, 99, 2.0) | no |
| NQ.T2FNQ.b3b5afd0 | NQ | nyam | 1.00 | -638 / 17825 | -119 / 3132 | 141 | 71 / 65 | -12924 vs -124996 | -7466 vs -17825 | -0.28 vs -0.40 | n/a | ok | PRO NT(0.65,) | no |
| RTY.T2FRTY.b10ff90d | RTY | nypm | 1.00 | -347 / 26646 | 324 / 1932 | -25 | 71 / 65 | -28809 vs -181504 | -7533 vs -13378 | -0.37 vs -0.40 | n/a | ok | STK SK(30, 15, 5) | in-sample only (WF/null fail) |

## REFIT 2026-11-22 (the pick the whole procedure would trade from the next bi-weekly refit: trailing 26 weeks; top 15 of the ranking)
| id | refit stack (L2 variant) |
|--|--|
| NQ.T2FNQ.590a38d0 | {"CUT": "L2(0.8, 20.0, 15, 1)", "PRO": "NT(0.65,)", "SIZ": "ER(10, 0.3, 'low', 0.25)", "ZON": "ZN('PD', 'behind', 0.8, 0.5)", "LCK": "LK(30, 99, 2.0)", "STK": "SK(15, 15, 4)"} |
| NQ.T2FNQ.d70f2c27 | {"CUT": "L2(0.8, 2.0, 5, 1)", "PRO": "NT(0.65,)", "SIZ": "ER(20, 0.4, 'low', 0.25)", "ZON": "ZN('PD', 'behind', 0.8, 0.5)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(0, 0, 4)"} |
| NQ.T2FNQ.b4d6bcb2 | {"CUT": "L2(0.8, 20.0, 5, 3)", "PRO": "NT(0.5,)", "SIZ": "ER(40, 0.4, 'high', 0.5)", "ZON": "ZN('RN', 'ahead', 0.8, 0.0)", "LCK": "LK(30, 2, 99.0)", "STK": "SK(30, 15, 3)"} |
| NQ.T2FNQ.58e02ca4 | {"CUT": "PP(0.45, 5, 0.15, 3)", "PRO": "NT(0.5,)", "SIZ": "ER(40, 0.3, 'low', 0.25)", "ZON": "ZN('RN', 'behind', 0.8, 0.5)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(0, 0, 4)"} |
| ES.T2F1B.418ebba1 | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "TR(0.7, 0.25)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('PD', 'behind', 0.8, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 0, 1)"} |
| ES.T2F1B.ead810fa | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "TR(0.5, 0.25)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('PD', 'behind', 0.4, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 0, 1)"} |
| NQ.T2FNQ.63f3f762 | {"CUT": "L2(0.45, 6.0, 5, 1)", "PRO": "NT(0.65,)", "SIZ": "ER(10, 0.2, 'high', 0.25)", "ZON": "ZN('PD', 'ahead', 0.8, 0.5)", "LCK": "LK(30, 3, 99.0)", "STK": "SK(30, 15, 3)"} |
| NQ.T2FNQ.2c9e1db3 | {"CUT": "PP(0.3, 30, 0.15, 3)", "PRO": "NT(0.5,)", "SIZ": "ER(40, 0.2, 'high', 0.25)", "ZON": "ZN('PD', 'ahead', 0.4, 0.5)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 15, 2)"} |
| ES.T2F1B.d0b5d0fb | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "NT(0.9,)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('VW', 'behind', 0.4, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 0, 1)"} |
| NQ.T2FNQ.102364a8 | {"CUT": "L2(0.45, 2.0, 15, 3)", "PRO": "NT(0.5,)", "SIZ": "ER(10, 0.2, 'high', 0.25)", "ZON": "ZN('RN', 'ahead', 0.4, 0.0)", "LCK": "LK(0, 2, 2.0)", "STK": "SK(0, 15, 4)"} |
| ES.T2F1B.e8b78ed4 | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "TR(0.7, 0.25)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('PD', 'behind', 0.8, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 0, 0)"} |
| ES.T2F1B.c607e3ab | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "NT(0.9,)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('PD', 'behind', 0.4, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(30, 0, 1)"} |
| ES.T2F1B.c450ea77 | {"CUT": "L2(0.3, 20.0, 15, 1)", "PRO": "NT(0.5,)", "SIZ": "ER(20, 0.3, 'high', 0.25)", "ZON": "ZN('PD', 'behind', 0.8, 0.0)", "LCK": "LK(120, 99, 99.0)", "STK": "SK(15, 15, 4)"} |
| NQ.T2FNQ.6883cc0b | {"CUT": "PP(0.6, 5, 0.15, 1)", "PRO": "NT(0.65,)", "SIZ": "ER(10, 0.4, 'high', 0.25)", "ZON": "ZN('RN', 'behind', 0.8, 0.0)", "LCK": "LK(30, 2, 2.0)", "STK": "SK(0, 0, 2)"} |
| NQ.T2FNQ.e5a76808 | {"CUT": "L2(0.8, 2.0, 15, 3)", "PRO": "NT(0.65,)", "SIZ": "ER(10, 0.3, 'high', 0.5)", "ZON": "ZN('VW', 'ahead', 0.4, 0.0)", "LCK": "LK(60, 99, 99.0)", "STK": "SK(30, 15, 4)"} |

## What the L2 layers add (WALK-FORWARD columns only: dressed-with-L2 minus dressed-without-L2, same candidate, bi-weekly refit OOS, $ at R=$1,200 per trade)
| instrument | family | n cand | share with WF dTotal > 0 | median WF dTotal $ | sum WF dTotal $ | sum last-13-period dTotal $ | l2cov median |
|--|--|--|--|--|--|--|--|
| ES | T2F1B | 18 | 0.67 | 487 | 69469 | 46 | 1.00 |
| ES | T2FES | 935 | 0.53 | 215 | 50962 | 34073 | 0.91 |
| ES | mom_h30_nypm_q0.7_atr_3.0_None_s2 | 1 | 1.00 | 2189 | 2189 | 3555 | 0.91 |
| ES | rev_h30_pre_q0.85_atr_2.0_1.5R_s0 | 1 | 1.00 | 6540 | 6540 | 3140 | 0.88 |
| ES | rev_h30_pre_q0.85_atr_3.0_2R_s0 | 1 | 1.00 | 3961 | 3961 | 5096 | 0.88 |
| NQ | LRS | 3 | 0.33 | -3031 | -9267 | -3605 | 1.00 |
| NQ | T2F1B | 36 | 0.32 | -580 | -30386 | -24588 | 1.00 |
| NQ | T2FNQ | 192 | 0.59 | 1496 | 393971 | 29858 | 1.00 |
| RTY | LRS | 3 | 0.67 | 31 | -1182 | 77 | 0.89 |
| RTY | T2F1B | 36 | 0.58 | 214 | 5475 | -1586 | 1.00 |
| RTY | T2FRTY | 590 | 0.51 | 75 | 5848 | 25320 | 0.92 |

Plain sentence: across 596 candidates the L2 variant adds a median of $192 and a sum of $497581 of OOS P&L over the no-L2 variant (positive for 0.53 of candidates).

## L2 adds per instrument (bi-weekly WF OOS, dressed-L2 minus dressed-noL2; candidates where both variants had a WF)
| instrument | n cand | median dMean $/wk (OOS, ~70 wk) | share > 0 | median OOS maxDD cut L2 vs no-L2 (pct pts of naked OOS maxDD) | l2cov median |
|--|--|--|--|--|--|
| ES | 212 | 3.9 | 0.55 | 0.6 | 0.94 |
| NQ | 142 | 8.0 | 0.53 | 0.4 | 1.00 |
| RTY | 242 | 1.3 | 0.52 | 0.2 | 0.97 |

Family null (F.family_p_fd, all NQ/ES/RTY dressed + naked rows): best p_fam = 0.39 (a naked row); no dressed candidate has p_fam <= .10. Nothing clears; per-candidate own-null p <= .10 hits are consistent with chance across ~1,800 tests.
ROLL-FIXED note: the dressed lists on NQ/ES/RTY were built on the OLD state tape (1-s state/series, pre roll-fixed engine base) with roll exclusion (rollx==1 rows and trades alive across a 1-s jump > 30/10/6 pts dropped, not weighted). They are first-order re-simulations, not engine runs, so no rerun is needed. Pair (RV) and daily books are not dressed. Held-out live week: n/a (lists end before 2026-11-02).