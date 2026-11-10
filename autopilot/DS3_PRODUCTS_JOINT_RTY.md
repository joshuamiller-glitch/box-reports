# DS3_PRODUCTS_JOINT - RTY section (FD-LIQ, T-NEXT A1/A3). Updated 2026-11-10 21:42Z

FIRST-ORDER, PRE-PROOF, Shadow only, no PASS claims. D7 book families ported with families.py (KB keltner_flip, PE/PB7 pullback_band, SM supertrend_flip, HM hma_vwap_cross, MV momentum_vote, O7 orb_break) on RTY 1-min bars built from the 1-s series; grids of parameters x ATR14(5m) stop multiples (2/3/4) x target (1R/2R), 60-min time stop, per session; per (family,session) the top-3 by naked Calmar plus 2 mid-rank cells are dressed with the full layer set (CUT L2/PP, PRO, SIZ, ZON, LCK, STK) top-3 per layer -> joint 3^6 -> bi-weekly WF of the whole procedure (26 wk train, next 2 wk, 7 d embargo) -> permuted-effect null. Exact engine: pending SZ-CORE (RTY base not yet built); the D7 families here are the instr2 family code, not the DS7.cs port, so definitions differ in details (45-s confirm of PE not modelled).

Dressed cells: 140 (groups family x session). With bi-weekly WF share >= 60%: 16; with own null p <= .10 as well: 5.

## Ranking (recents first): STANDALONE bar columns, then SEAT bar where run
| id | family | session | n_search | naked L6M mean / maxDD | dressed L6M Cal / maxDD / mean | dressed L3M Cal / maxDD | bi-weekly WF % beat / n | WF OOS d vs n | PRE (2a) | own null p | carrier | standalone bar |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RTY.GEN_KB_nypm.7a57bf9d | GEN_KB_nypm | nypm | 216 | -248 / 21326 | 2.63 / 3017 / 152 | 4.95 / 2203 | 71 / 72 | -39050 vs -173746 | ok | 0.39 | SIZ ER(20, 0.2, 'high', 0.25) | no |
| RTY.GEN_HM_nypm.ab459a47 | GEN_HM_nypm | nypm | 24 | 553 / 30237 | 5.76 / 2035 / 225 | 7.38 / 2035 | 69 / 72 | 4491 vs -92608 | ok | 0.46 | ZON ZN('VW', 'ahead', 0.4, 0.0) | no |
| RTY.GEN_KB_close.46afaa2a | GEN_KB_close | close | 216 | -183 / 11567 | -1.42 / 2182 / -60 | -1.78 / 1158 | 69 / 72 | -18127 vs -48972 | ok | 0.58 | ZON ZN('VW', 'behind', 0.4, 0.0) | no |
| RTY.GEN_PE_pre.be7424f7 | GEN_PE_pre | pre | 36 | -1155 / 78579 | -1.31 / 15082 / -380 | -4.00 / 11492 | 68 / 72 | -27159 vs -182118 | ok | 0.07 | SIZ ER(10, 0.4, 'low', 0.25) | no |
| RTY.GEN_PE_pre.b3c0aa26 | GEN_PE_pre | pre | 36 | -196 / 29409 | 5.31 / 2168 / 221 | 5.00 / 2168 | 67 / 72 | -18068 vs -105265 | ok | 0.09 | PRO NT(0.8,) | YES (WF>=60, null<=.10, L6M Cal>0) |
| RTY.GEN_KB_pre.c3324d1e | GEN_KB_pre | pre | 216 | 995 / 36328 | 2.98 / 4687 / 269 | 10.49 / 1554 | 65 / 72 | -56829 vs -175664 | ok | 0.44 | PRO NT(0.5,) | no |
| RTY.GEN_KB_nyam.e3220920 | GEN_KB_nyam | nyam | 216 | -334 / 22600 | 2.12 / 3633 / 148 | 13.59 / 1144 | 65 / 72 | -15752 vs -64531 | ok | 0.51 | SIZ ER(10, 0.4, 'high', 0.25) | no |
| RTY.GEN_SM_london.772f61bb | GEN_SM_london | london | 108 | -1794 / 34364 | -1.85 / 4999 / -178 | -3.22 / 1289 | 65 / 72 | -14171 vs -84855 | ok | 0.09 | ZON ZN('VW', 'ahead', 0.4, 0.0) | no |
| RTY.GEN_MV_pre.90f8b873 | GEN_MV_pre | pre | 36 | -265 / 18886 | 13.45 / 1749 / 452 | 7.19 / 1749 | 64 / 72 | -33742 vs -79779 | ok | 0.86 | SIZ ER(40, 0.2, 'low', 0.25) | no |
| RTY.GEN_SM_nyam.28bc2c2c | GEN_SM_nyam | nyam | 108 | -130 / 10007 | 0.27 / 3290 / 17 | -2.51 / 3290 | 64 / 72 | -261 vs -21513 | ok | 0.10 | STK SK(15, 15, 3) | YES (WF>=60, null<=.10, L6M Cal>0) |
| RTY.GEN_PE_pre.b83797c9 | GEN_PE_pre | pre | 36 | 471 / 29638 | -1.21 / 5712 / -133 | 0.41 / 3054 | 64 / 72 | -20964 vs -90711 | ok | 0.44 | SIZ ER(20, 0.3, 'low', 0.25) | no |
| RTY.GEN_HM_close.1ba5e96e | GEN_HM_close | close | 24 | -190 / 10528 | 3.21 / 1231 / 76 | -2.70 / 1231 | 62 / 72 | -3209 vs -61371 | ok | 0.26 | ZON ZN('VW', 'ahead', 0.4, 0.0) | no |
| RTY.GEN_MV_close.719a4138 | GEN_MV_close | close | 36 | 318 / 5144 | 2.08 / 2106 / 84 | 27.97 / 374 | 62 / 72 | -834 vs -22107 | ok | 0.40 | SIZ ER(10, 0.4, 'high', 0.25) | no |
| RTY.GEN_KB_pre.b9106422 | GEN_KB_pre | pre | 216 | -228 / 41473 | -0.74 / 5875 / -83 | 11.14 / 1235 | 62 / 72 | -25666 vs -102948 | ok | 0.18 | PRO NT(0.65,) | no |
| RTY.GEN_KB_nypm.9cdf8dd0 | GEN_KB_nypm | nypm | 216 | -19 / 5187 | -0.76 / 2691 / -40 | -3.76 / 1451 | 61 / 72 | 6558 vs -6671 | ok | 0.64 | STK SK(30, 15, 4) | no |
| RTY.GEN_SM_pre.0381345a | GEN_SM_pre | pre | 108 | -429 / 12666 | -2.00 / 907 / -35 | n/a / 0 | 61 / 72 | -8826 vs -55129 | ok | 0.07 | STK SK(0, 15, 4) | no |
| RTY.GEN_MV_pre.d4ffdc6a | GEN_MV_pre | pre | 36 | 345 / 10635 | 11.01 / 1732 / 367 | 6.44 / 1732 | 60 / 72 | -41989 vs -68714 | ok | n/a | SIZ ER(40, 0.2, 'low', 0.25) | no |
| RTY.GEN_PE_nyam.f965dde8 | GEN_PE_nyam | nyam | 36 | -204 / 32399 | 3.50 / 1825 / 123 | 8.83 / 1239 | 60 / 72 | -20058 vs -86123 | ok | n/a | LCK LK(120, 99, 2.0) | no |
| RTY.GEN_PE_nypm.683cdc6f | GEN_PE_nypm | nypm | 36 | -661 / 11710 | 2.09 / 2025 / 82 | 0.08 / 970 | 60 / 72 | -2823 vs -28895 | ok | n/a | STK SK(30, 15, 5) | no |
| RTY.GEN_PE_close.e59213d0 | GEN_PE_close | close | 36 | -18 / 8777 | 0.49 / 3218 / 30 | 16.50 / 781 | 60 / 72 | -25955 vs -56512 | ok | n/a | STK SK(0, 15, 5) | no |
| RTY.GEN_PE_pre.39724654 | GEN_PE_pre | pre | 36 | 383 / 27942 | -0.58 / 3972 / -44 | 1.93 / 2372 | 60 / 72 | -20069 vs -89869 | ok | n/a | SIZ ER(20, 0.3, 'low', 0.25) | no |
| RTY.GEN_PE_nypm.c9c9960f | GEN_PE_nypm | nypm | 36 | -1103 / 13230 | -0.94 / 5731 / -103 | -3.01 / 3844 | 60 / 72 | -17755 vs -79166 | ok | n/a | SIZ ER(10, 0.3, 'low', 0.25) | no |
| RTY.GEN_MV_close.0a2e04c8 | GEN_MV_close | close | 36 | -49 / 14358 | 6.04 / 1324 / 154 | 20.03 / 581 | 58 / 72 | -7602 vs -46158 | ok | n/a | SIZ ER(10, 0.2, 'high', 0.25) | no |
| RTY.GEN_MV_close.f3d6b013 | GEN_MV_close | close | 36 | 314 / 5144 | 1.59 / 2181 / 67 | 0.56 / 668 | 58 / 72 | -4729 vs -23163 | ok | n/a | SIZ ER(10, 0.4, 'high', 0.25) | no |
| RTY.GEN_KB_close.9a12387e | GEN_KB_close | close | 216 | 198 / 8970 | 1.06 / 1475 / 30 | -1.28 / 1475 | 58 / 72 | -6287 vs -36558 | ok | n/a | STK SK(30, 0, 4) | no |
| RTY.GEN_MV_nypm.6d05066a | GEN_MV_nypm | nypm | 36 | -116 / 10477 | 0.25 / 2297 / 11 | -1.28 / 1518 | 58 / 72 | -24327 vs -44753 | ok | n/a | SIZ ER(10, 0.2, 'high', 0.25) | no |
| RTY.GEN_MV_pre.011ef344 | GEN_MV_pre | pre | 36 | -70 / 17849 | 0.05 / 1417 / 1 | -4.00 / 1417 | 58 / 72 | -16381 vs -39568 | ok | n/a | ZON ZN('VW', 'ahead', 0.4, 0.0) | no |
| RTY.GEN_PE_close.354c4354 | GEN_PE_close | close | 36 | -153 / 8009 | -0.49 / 3721 / -35 | 7.91 / 918 | 58 / 72 | -5520 vs -38553 | ok | n/a | ZON ZN('VW', 'ahead', 0.4, 0.5) | no |
| RTY.GEN_SM_london.a87dc706 | GEN_SM_london | london | 108 | -789 / 12793 | -0.80 / 2958 / -46 | 3.63 / 1164 | 58 / 72 | -15329 vs -34829 | ok | n/a | ZON ZN('ON', 'ahead', 0.4, 0.0) | no |
| RTY.GEN_MV_nypm.99eaea29 | GEN_MV_nypm | nypm | 36 | -710 / 10895 | -1.93 / 1753 / -65 | -3.27 / 1634 | 58 / 72 | -12399 vs -39801 | ok | n/a | STK SK(30, 15, 3) | no |

L2 adds on RTY (WF OOS, dressed-L2 minus dressed-noL2 over 88 cells): median $1161 per OOS period-set, positive for 0.60 of cells.