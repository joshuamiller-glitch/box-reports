# FD_LIQ - T-FIND-DRESSED, NQ / ES / RTY candidates dressed with the FULL stack (FD-LIQ). Updated 2026-11-09 19:24Z

Post-hoc, Shadow only, no PASS claims. First-order per-trade re-simulation on 1-s paths (ES/RTY L2 state arrays built slim from raw mbp-10; coverage per candidate in column l2cov); exact engine only where the DS7 replica covers the instrument/book: NOT used here (first-order, flagged). Lots continuous at equal $1,200 risk per trade. Pair (RV) books and daily books are not dressed here (no stop distance / two legs).
Procedure per candidate (own trades): layer screens -> top-3 per layer (CUT loss cut L2/PP, PRO profit rule, SIZ ER sizer, ZON zones, LCK cooldown/locks, STK stack-rule slots) by all-weeks Calmar -> joint 3^6 stack, pick = max in-sample Calmar -> validation of the WHOLE procedure: purged monthly walk-forward (26 w train, 7 d embargo, from 2024-02) and a permuted-effect null that repeats the whole screen+joint search on layer effects re-assigned to random trades (B=60). In-sample dressed numbers are search maxima and are NOT evidence by themselves.

Candidates dressed so far: 26. L2 variant WF ok: 3; with null p <= .10 as well: 0.

## Top 40 by WF Calmar of the whole procedure (L2 variant); naked beside dressed
| id | instr | sess | l2cov | naked L6M / PRE mean $/wk | naked L6M / PRE maxDD | dressed L6M / PRE mean | dressed L6M / PRE maxDD | WF OOS Calmar dressed vs naked | WF OOS total d / n | null p | carrier layer | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| NQ.T2FNQ.3fd226db | NQ | close | 1.00 | 1682 / -454 | 2933 / 37266 | 510 / 144 | 1755 / 4765 | 0.61 vs 0.08 | 12261 / 7801 | 0.36 | LCK LK(120, 99, 4.0) | WATCH (WF ok, null not) |
| RTY.T2F1B.a5592148 | RTY | pre | 0.08 | 276 / 33 | 369 / 7655 | -8 / 71 | 158 / 1235 | 0.57 vs 0.08 | 3210 / 2533 | 0.36 | SIZ ER(20, 0.4, 'high', 0.25) | no |
| NQ.T2FNQ.2665fb2e | NQ | close | 1.00 | 1360 / -362 | 4201 / 33902 | 564 / 118 | 3373 / 3701 | 0.19 vs -0.07 | 5829 / -6110 | 0.28 | CUT PP(0.45, 5, 0.15, 3) | WATCH (WF ok, null not) |
| RTY.T2F1B.0ad97ac4 | RTY | pre | 0.08 | 276 / 30 | 290 / 7587 | -8 / 71 | 158 / 1301 | 0.28 vs 0.08 | 1950 / 2343 | 0.41 | SIZ ER(20, 0.4, 'high', 0.25) | no |
| NQ.T2F1B.e3dde7b1 | NQ | nyam | 1.00 | 405 / -11 | 5214 / 32705 | 583 / 184 | 6261 / 6349 | 0.25 vs 0.58 | 10165 / 52476 | 0.92 | STK SK(15, 0, 5) | in-sample only (WF/null fail) |
| NQ.T2FNQ.b204fb7b | NQ | pre | 1.00 | 402 / -97 | 9728 / 13928 | 450 / 116 | 2413 / 1965 | -0.06 vs -0.25 | -3808 / -54371 | n/a | SIZ ER(10, 0.4, 'low', 0.25) | in-sample only (WF/null fail) |
| ES.T2F1B.4da4042b | ES | nyam | 0.05 | 203 / -437 | 5351 / 30183 | 230 / 15 | 408 / 1965 | -0.11 vs -0.30 | -2946 / -35922 | n/a | STK SK(15, 0, 4) | in-sample only (WF/null fail) |
| ES.rev_h30_pre_q0.85_atr_2.0_1.5R_s0.74d040bd | ES | pre | 0.10 | 650 / -383 | 13009 / 35266 | 692 / -1 | 3596 / 6085 | -0.13 vs -0.20 | -6779 / -24421 | n/a | STK SK(0, 15, 4) | no |
| RTY.LRS.d36509c0 | RTY | nypm | 0.06 | 88 / -608 | 8346 / 34559 | 103 / 99 | 1879 / 3281 | -0.13 vs -0.26 | -2907 / -31808 | n/a | STK SK(15, 15, 5) | in-sample only (WF/null fail) |
| RTY.T2FRTY.e937a5f9 | RTY | pre | 0.08 | 624 / -244 | 3780 / 19035 | 199 / -10 | 1531 / 5102 | -0.17 vs -0.15 | -6518 / -10360 | n/a | PRO NT(0.8,) | no |
| ES.T2F1B.d10fa1f2 | ES | nyam | 0.05 | 151 / -58 | 3341 / 8574 | 209 / 131 | 480 / 1678 | -0.20 vs -0.10 | -7850 / -2623 | n/a | STK SK(15, 0, 4) | in-sample only (WF/null fail) |
| RTY.LRS.07220fef | RTY | nypm | 0.06 | 742 / -375 | 2631 / 27757 | -44 / 194 | 1554 / 3250 | -0.21 vs -0.17 | -8582 / -16452 | n/a | STK SK(15, 0, 5) | no |
| RTY.T2FRTY.c41bf3d8 | RTY | asia | 0.06 | 381 / -97 | 1797 / 10289 | 47 / -36 | 574 / 5312 | -0.23 vs -0.03 | -10492 / -1767 | n/a | PRO BE(0.5, 0.15) | no |
| RTY.T2FRTY.39f12c69 | RTY | pre | 0.08 | 418 / -86 | 1308 / 9202 | 142 / 34 | 1208 / 3544 | -0.26 vs 0.06 | -7282 / 1280 | n/a | SIZ ER(20, 0.2, 'high', 0.25) | in-sample only (WF/null fail) |
| ES.T2FES.85aaaa9d | ES | close | 0.05 | 280 / -222 | 2629 / 23521 | 160 / 100 | 338 / 4210 | -0.28 vs -0.02 | -6069 / -1220 | n/a | STK SK(15, 0, 0) | in-sample only (WF/null fail) |
| ES.T2FES.ff72ff59 | ES | close | 0.05 | 94 / -310 | 2681 / 25251 | 69 / -25 | 1250 / 5969 | -0.33 vs -0.19 | -13280 / -12975 | n/a | ZON ZN('RN', 'behind', 0.8, 0.0) | no |
| ES.T2FES.7602e234 | ES | close | 0.05 | 245 / -299 | 2629 / 27689 | 132 / 59 | 338 / 4192 | -0.35 vs -0.14 | -11044 / -10955 | n/a | ZON ZN('RN', 'behind', 0.8, 0.0) | in-sample only (WF/null fail) |
| ES.T2FES.5130e274 | ES | nypm | 0.07 | 1781 / -1095 | 7674 / 93490 | 276 / 70 | 5602 / 15007 | -0.40 vs -0.32 | -33097 / -117617 | n/a | LCK LK(120, 99, 99.0) | in-sample only (WF/null fail) |
| RTY.T2FRTY.a97a6d32 | RTY | close | 0.07 | -89 / 12 | 1200 / 4182 | -12 / 19 | 300 / 1084 | n/a vs n/a | n/a / n/a | n/a | SIZ ER(40, 0.3, 'high', 0.25) | no |
| RTY.T2FRTY.67cb478e | RTY | asia | 0.06 | 874 / -148 | 2094 / 12356 | 67 / -33 | 599 / 4781 | n/a vs n/a | n/a / n/a | n/a | ZON ZN('RN', 'ahead', 0.8, 0.0) | no |
| NQ.T2FNQ.e8cab6aa | NQ | pre | 1.00 | 72 / -106 | 1227 / 11526 | -12 / -11 | 1160 / 2137 | n/a vs n/a | n/a / n/a | n/a | SIZ ER(20, 0.3, 'low', 0.25) | no |
| ES.T2FES.b231e0b6 | ES | london | 0.07 | 138 / -144 | 5695 / 24182 | -9 / -88 | 1891 / 11458 | n/a vs n/a | n/a / n/a | n/a | SIZ ER(40, 0.4, 'high', 0.25) | no |
| RTY.T2FRTY.14ce1141 | RTY | asia | 0.06 | 777 / -83 | 1797 / 8384 | 150 / -42 | 574 / 4893 | n/a vs n/a | n/a / n/a | n/a | ZON ZN('RN', 'ahead', 0.8, 0.0) | no |
| ES.T2FES.a1a4ddf8 | ES | london | 0.06 | -23 / -1048 | 24134 / 83416 | 625 / -433 | 4151 / 40097 | n/a vs n/a | n/a / n/a | n/a | SIZ ER(20, 0.3, 'high', 0.25) | no |
| RTY.T2FRTY.ed5ee382 | RTY | london | 0.08 | 783 / -77 | 5445 / 21847 | 567 / -8 | 3822 / 7144 | n/a vs n/a | n/a / n/a | n/a | SIZ ER(10, 0.4, 'high', 0.25) | no |
| ES.T2FES.64408a9e | ES | london | 0.06 | 494 / -187 | 1173 / 13334 | 338 / -104 | 1766 / 8383 | n/a vs n/a | n/a / n/a | n/a | ZON ZN('PD', 'behind', 0.8, 0.0) | no |

## What the L2 layers add (dressed with L2 minus dressed without L2, same candidate)
In-sample dcal is >= 0 by construction (superset search); the honest number is the WF OOS total difference (dressed-L2 minus dressed-noL2, $ at R=$1,200 per trade over the WF months) and its sign share.
| instrument | family | n cand | mean in-sample dCalmar | share with WF dTotal > 0 | median WF dTotal $ | sum WF dTotal $ | l2cov median |
|--|--|--|--|--|--|--|--|
| ES | T2F1B | 2 | 0.077 | 0.00 | -1585 | -3170 | 0.05 |
| ES | T2FES | 7 | 0.033 | 0.25 | -630 | 4521 | 0.06 |
| ES | rev_h30_pre_q0.85_atr_2.0_1.5R_s0 | 1 | 0.000 | 1.00 | 9753 | 9753 | 0.10 |
| NQ | T2F1B | 1 | 0.005 | 1.00 | 2061 | 2061 | 1.00 |
| NQ | T2FNQ | 4 | -0.001 | 0.33 | -2264 | -8317 | 1.00 |
| RTY | LRS | 2 | -0.009 | 0.50 | 250 | 499 | 0.06 |
| RTY | T2F1B | 2 | 0.000 | 0.00 | 0 | 0 | 0.08 |
| RTY | T2FRTY | 7 | 0.000 | 0.00 | 0 | 0 | 0.07 |
