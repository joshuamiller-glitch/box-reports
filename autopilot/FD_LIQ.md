# FD_LIQ - T-FIND-DRESSED, NQ / ES / RTY candidates dressed with the FULL stack (FD-LIQ). Updated 2026-11-09 19:38Z

Post-hoc, Shadow only, no PASS claims. First-order per-trade re-simulation on 1-s paths (ES/RTY L2 state arrays built slim from raw mbp-10; coverage per candidate in column l2cov); exact engine only where the DS7 replica covers the instrument/book: NOT used here (first-order, flagged). Lots continuous at equal $1,200 risk per trade. Pair (RV) books and daily books are not dressed here (no stop distance / two legs).
Procedure per candidate (own trades): layer screens -> top-3 per layer (CUT loss cut L2/PP, PRO profit rule, SIZ ER sizer, ZON zones, LCK cooldown/locks, STK stack-rule slots) by all-weeks Calmar -> joint 3^6 stack, pick = max in-sample Calmar -> validation of the WHOLE procedure: purged monthly walk-forward (26 w train, 7 d embargo, from 2024-02) and a permuted-effect null that repeats the whole screen+joint search on layer effects re-assigned to random trades (B=60). In-sample dressed numbers are search maxima and are NOT evidence by themselves.

Candidates dressed so far: 224. L2 variant WF ok: 20; with null p <= .10 as well: 4.

## Top 40 by WF Calmar of the whole procedure (L2 variant); naked beside dressed
| id | instr | sess | l2cov | naked L6M / PRE mean $/wk | naked L6M / PRE maxDD | dressed L6M / PRE mean | dressed L6M / PRE maxDD | WF OOS Calmar dressed vs naked | WF OOS total d / n | null p | carrier layer | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.T2F1B.00025790 | NQ | nyam | 1.00 | -119 / -230 | 1710 / 18322 | -13 / 43 | 1928 / 4663 | 1.37 vs -0.35 | 12097 / -20577 | 0.85 | PRO NT(0.65,) | no |
| NQ.T2F1B.35b394b7 | NQ | nyam | 1.00 | -256 / -378 | 3680 / 30689 | 154 / 87 | 1946 / 5188 | 0.70 vs -0.34 | 19551 / -35492 | 0.90 | PRO NT(0.8,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.a4d978b9 | NQ | close | 1.00 | 1267 / -449 | 2449 / 38247 | 758 / 213 | 3426 / 5169 | 0.61 vs -0.07 | 12175 / -8503 | 0.25 | LCK LK(120, 99, 4.0) | WATCH (WF ok, null not) |
| NQ.T2FNQ.6883cc0b | NQ | nyam | 1.00 | -753 / -608 | 26687 / 44579 | 1189 / 36 | 2316 / 6421 | 0.60 vs -0.42 | 12793 / -113175 | 0.30 | PRO NT(0.65,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.b3b5afd0 | NQ | nyam | 1.00 | -638 / -606 | 17825 / 51943 | -119 / 282 | 3132 / 3860 | 0.57 vs -0.41 | 14143 / -124832 | 0.10 | PRO NT(0.65,) | no |
| NQ.T2F1B.ec704457 | NQ | nyam | 1.00 | -119 / -229 | 1710 / 18252 | -0 / 54 | 1694 / 3654 | 0.54 vs -0.35 | 5183 / -22657 | 0.90 | PRO NT(0.9,) | no |
| NQ.LRS.234b08c5 | NQ | nypm | 1.00 | 621 / -593 | 10322 / 55460 | 906 / 347 | 2764 / 9452 | 0.51 vs -0.22 | 19008 / -41870 | 0.26 | SIZ ER(40, 0.2, 'low', 0.25) | WATCH (WF ok, null not) |
| NQ.T2FNQ.eb709d83 | NQ | nypm | 1.00 | -5264 / -353 | 65838 / 48647 | 21 / 177 | 3687 / 4882 | 0.47 vs -0.41 | 7285 / -155584 | 0.41 | LCK LK(120, 99, 99.0) | WATCH (WF ok, null not) |
| NQ.T2FNQ.3fd226db | NQ | close | 1.00 | 1682 / -454 | 2933 / 37266 | 862 / 218 | 2385 / 6306 | 0.41 vs 0.08 | 10102 / 7801 | 0.49 | ZON ZN('RN', 'ahead', 0.8, 0.0) | WATCH (WF ok, null not) |
| NQ.T2FNQ.ad49c4fb | NQ | nypm | 1.00 | -1212 / -266 | 23388 / 19529 | 140 / 129 | 4067 / 6079 | 0.20 vs -0.40 | 7922 / -90775 | 0.38 | PRO NT(0.65,) | WATCH (WF ok, null not) |
| NQ.T2F1B.3acc51f0 | NQ | pre | 1.00 | -102 / 133 | 8787 / 10129 | 114 / 15 | 1099 / 2828 | 0.13 vs -0.06 | 1598 / -2833 | 0.49 | ZON ZN('ON', 'behind', 0.4, 0.0) | WATCH (WF ok, null not) |
| NQ.T2FNQ.049c2dc6 | NQ | pre | 1.00 | -65 / -21 | 1754 / 1501 | 60 / 8 | 428 / 95 | 0.11 vs -0.57 | 352 / -3845 | 0.05 | PRO NT(0.5,) | LEAD (dressed; WF ok, null p<=.10) |
| NQ.T2FNQ.2c9e1db3 | NQ | nyam | 1.00 | -1325 / -2458 | 57948 / 185558 | 1160 / 735 | 1407 / 2575 | 0.10 vs -0.40 | 5199 / -311836 | 0.02 | PRO NT(0.5,) | LEAD (dressed; WF ok, null p<=.10) |
| NQ.T2FNQ.80f7f135 | NQ | pre | 1.00 | -80 / -30 | 9456 / 23410 | -36 / 117 | 2147 / 2966 | 0.10 vs 0.00 | 1777 / 397 | 0.46 | STK SK(0, 15, 4) | no |
| NQ.T2F1B.26417cae | NQ | pre | 1.00 | -102 / 0 | 8787 / 11101 | 118 / -12 | 605 / 2461 | 0.10 vs -0.24 | 1269 / -12271 | 0.77 | STK SK(0, 15, 5) | WATCH (WF ok, null not) |
| NQ.T2F1B.19ef2130 | NQ | pre | 1.00 | -75 / 4 | 8101 / 9964 | 61 / 24 | 605 / 2034 | 0.08 vs -0.25 | 1205 / -11969 | 0.67 | ZON ZN('ON', 'behind', 0.4, 0.0) | WATCH (WF ok, null not) |
| NQ.T2F1B.a91ab286 | NQ | pre | 1.00 | 140 / 20 | 5161 / 9486 | 105 / 34 | 383 / 1371 | 0.07 vs -0.11 | 707 / -3140 | 0.10 | ZON ZN('ON', 'behind', 0.4, 0.0) | LEAD (dressed; WF ok, null p<=.10) |
| NQ.T2FNQ.7f1ed3cb | NQ | nyam | 1.00 | -702 / -2277 | 32778 / 172642 | 634 / 96 | 5443 / 10809 | 0.04 vs -0.39 | 1743 / -264751 | 0.56 | LCK LK(120, 99, 99.0) | WATCH (WF ok, null not) |
| NQ.T2FNQ.d70f2c27 | NQ | nypm | 1.00 | -1968 / -2229 | 39395 / 160338 | 757 / 461 | 2383 / 935 | 0.01 vs -0.40 | 906 / -314152 | 0.54 | PRO NT(0.5,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.841cd289 | NQ | nyam | 1.00 | -1143 / -378 | 29133 / 27134 | 75 / -17 | 2277 / 5072 | 0.01 vs -0.40 | 321 / -118567 | 0.62 | PRO NT(0.65,) | WATCH (WF ok, null not) |
| NQ.T2FNQ.434f1d49 | NQ | pre | 1.00 | 229 / 7 | 964 / 4690 | 25 / 8 | 135 / 223 | 0.74 vs 0.99 | 1065 / 6356 | 0.34 | STK SK(0, 15, 3) | in-sample only (WF/null fail) |
| NQ.T2F1B.f285cabb | NQ | pre | 1.00 | 113 / 93 | 2707 / 6086 | 48 / 45 | 301 / 614 | 0.40 vs 0.38 | 5205 / 6464 | 0.13 | PRO TR(0.5, 0.25) | in-sample only (WF/null fail) |
| NQ.T2F1B.0156ad55 | NQ | pre | 1.00 | 113 / 77 | 2707 / 6086 | 48 / 41 | 301 / 896 | 0.32 vs 0.32 | 4194 / 5336 | 0.28 | ZON ZN('ON', 'behind', 0.4, 0.0) | in-sample only (WF/null fail) |
| NQ.T2F1B.f5c1adc0 | NQ | pre | 1.00 | 130 / 93 | 2413 / 6041 | 48 / 47 | 301 / 604 | 0.29 vs 0.48 | 3659 / 7957 | 0.26 | PRO TR(0.5, 0.25) | in-sample only (WF/null fail) |
| NQ.T2F1B.e3dde7b1 | NQ | nyam | 1.00 | 405 / -11 | 5214 / 32705 | 102 / 177 | 4933 / 14584 | 0.13 vs 0.58 | 4605 / 52476 | 0.80 | STK SK(0, 0, 5) | in-sample only (WF/null fail) |
| NQ.T2F1B.1624de42 | NQ | nyam | 1.00 | 405 / -11 | 5214 / 32705 | 102 / 177 | 4933 / 14584 | 0.13 vs 0.58 | 4605 / 52476 | 0.77 | STK SK(0, 0, 5) | in-sample only (WF/null fail) |
| NQ.T2FNQ.2c8563a6 | NQ | nyam | 1.00 | -314 / -195 | 16890 / 37585 | -46 / 137 | 2968 / 3370 | -0.02 vs -0.28 | -1170 / -35383 | n/a | CUT L2(0.3, 2.0, 15, 3) | no |
| NQ.T2FNQ.0d6c206d | NQ | nyam | 1.00 | -1129 / -120 | 42470 / 44356 | 66 / 101 | 2342 / 4546 | -0.02 vs -0.30 | -1392 / -57299 | n/a | PRO NT(0.8,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.e77382a9 | NQ | pre | 1.00 | -99 / 167 | 11290 / 10105 | 89 / 81 | 3598 / 3986 | -0.04 vs 0.29 | -1016 / 15883 | n/a | ZON ZN('ON', 'ahead', 0.8, 0.0) | in-sample only (WF/null fail) |
| NQ.T2FNQ.5d4a6fb1 | NQ | close | 1.00 | 615 / -644 | 19671 / 51911 | 377 / 53 | 3462 / 3024 | -0.05 vs -0.37 | -1110 / -57812 | n/a | SIZ ER(20, 0.3, 'low', 0.25) | in-sample only (WF/null fail) |
| NQ.T2F1B.3c29769b | NQ | pre | 1.00 | 54 / -18 | 1207 / 5509 | 81 / 45 | 922 / 1188 | -0.06 vs 0.29 | -845 / 4363 | n/a | ZON ZN('ON', 'behind', 0.4, 0.0) | in-sample only (WF/null fail) |
| NQ.T2FNQ.db3caf71 | NQ | nyam | 1.00 | -1441 / -512 | 41088 / 36341 | 810 / -15 | 1901 / 4088 | -0.06 vs -0.42 | -2250 / -138655 | n/a | PRO NT(0.65,) | no |
| NQ.T2FNQ.205b3ae9 | NQ | pre | 1.00 | -148 / -37 | 16358 / 10707 | 324 / 68 | 2650 / 4521 | -0.06 vs -0.34 | -1983 / -33148 | n/a | ZON ZN('ON', 'ahead', 0.8, 0.0) | in-sample only (WF/null fail) |
| NQ.T2FNQ.844d975a | NQ | nyam | 1.00 | 178 / -238 | 9520 / 68834 | 54 / 13 | 1828 / 4921 | -0.07 vs -0.39 | -3207 / -135665 | n/a | ZON ZN('VW', 'ahead', 0.4, 0.0) | in-sample only (WF/null fail) |
| NQ.T2FNQ.b661f321 | NQ | nyam | 1.00 | -461 / -2783 | 23488 / 208168 | 16 / -5 | 2713 / 5928 | -0.07 vs -0.38 | -3626 / -253930 | n/a | LCK LK(120, 99, 99.0) | no |
| NQ.T2FNQ.58c72bab | NQ | nyam | 1.00 | -1800 / -688 | 31817 / 52611 | 32 / -14 | 620 / 4070 | -0.08 vs -0.40 | -2548 / -166821 | n/a | LCK LK(120, 99, 2.0) | no |
| NQ.T2F1B.c690abeb | NQ | nyam | 1.00 | 230 / 62 | 3116 / 15796 | 133 / 124 | 1578 / 6485 | -0.10 vs 0.54 | -2685 / 23623 | n/a | SIZ ER(20, 0.4, 'high', 0.25) | in-sample only (WF/null fail) |
| NQ.T2F1B.283da795 | NQ | nyam | 1.00 | 230 / 62 | 3116 / 15796 | 133 / 124 | 1578 / 6485 | -0.10 vs 0.54 | -2685 / 23623 | n/a | SIZ ER(20, 0.4, 'high', 0.25) | in-sample only (WF/null fail) |
| NQ.T2FNQ.f77481dd | NQ | nypm | 1.00 | 250 / -680 | 12255 / 62203 | 605 / 135 | 862 / 3573 | -0.10 vs -0.21 | -7849 / -54256 | n/a | PRO NT(0.8,) | in-sample only (WF/null fail) |
| NQ.T2FNQ.69c22cdf | NQ | pre | 1.00 | -132 / 143 | 11374 / 13539 | 184 / 129 | 1578 / 2340 | -0.10 vs 0.14 | -2328 / 7853 | n/a | ZON ZN('ON', 'ahead', 0.8, 0.0) | in-sample only (WF/null fail) |

## What the L2 layers add (dressed with L2 minus dressed without L2, same candidate)
In-sample dcal is >= 0 by construction (superset search); the honest number is the WF OOS total difference (dressed-L2 minus dressed-noL2, $ at R=$1,200 per trade over the WF months) and its sign share.
| instrument | family | n cand | mean in-sample dCalmar | share with WF dTotal > 0 | median WF dTotal $ | sum WF dTotal $ | l2cov median |
|--|--|--|--|--|--|--|--|
| NQ | LRS | 3 | 0.046 | 0.67 | 1215 | -4066 | 1.00 |
| NQ | T2F1B | 36 | 0.100 | 0.23 | -502 | -23773 | 1.00 |
| NQ | T2FNQ | 185 | 0.640 | 0.53 | 127 | 289516 | 1.00 |
