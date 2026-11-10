# DS3_PRODUCTS_JOINT - ES section (FD-LIQ, T-NEXT A1/A3). Updated 2026-11-10 17:14Z

FIRST-ORDER, PRE-PROOF, Shadow only, no PASS claims. D7 book families ported with families.py (KB keltner_flip, PE/PB7 pullback_band, SM supertrend_flip, HM hma_vwap_cross, MV momentum_vote, O7 orb_break) on ES 1-min bars built from the 1-s series; grids of parameters x ATR14(5m) stop multiples (2/3/4) x target (1R/2R), 60-min time stop, per session; per (family,session) the top-3 by naked Calmar plus 2 mid-rank cells are dressed with the full layer set (CUT L2/PP, PRO, SIZ, ZON, LCK, STK) top-3 per layer -> joint 3^6 -> bi-weekly WF of the whole procedure (26 wk train, next 2 wk, 7 d embargo) -> permuted-effect null. Exact engine: pending SZ-CORE (ES base not yet built); the D7 families here are the instr2 family code, not the DS7.cs port, so definitions differ in details (45-s confirm of PE not modelled).

Dressed cells: 145 (groups family x session). With bi-weekly WF share >= 60%: 13; with own null p <= .10 as well: 1.

## Ranking (recents first): STANDALONE bar columns, then SEAT bar where run
| id | family | session | n_search | naked L6M mean / maxDD | dressed L6M Cal / maxDD / mean | dressed L3M Cal / maxDD | bi-weekly WF % beat / n | WF OOS d vs n | PRE (2a) | own null p | carrier | standalone bar |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES.GEN_PE_pre.0d015f4f | GEN_PE_pre | pre | 36 | -1554 / 26652 | -1.29 / 4914 / -122 | -2.66 / 2984 | 71 / 72 | -15832 vs -64676 | ok | n/a | ZON ZN('PD', 'behind', 0.8, 0.0) | no |
| ES.GEN_PE_close.a26ab4c1 | GEN_PE_close | close | 36 | -258 / 28326 | -0.41 / 2704 / -21 | 0.35 / 1624 | 67 / 72 | -22185 vs -100083 | ok | n/a | STK SK(30, 15, 3) | no |
| ES.GEN_HM_close.220bc3f9 | GEN_HM_close | close | 24 | -85 / 3359 | 10.67 / 904 / 186 | 16.42 / 313 | 65 / 72 | 4817 vs -25984 | ok | 0.64 | PRO NT(0.5,) | no |
| ES.GEN_PE_pre.9d0e84a4 | GEN_PE_pre | pre | 36 | -1664 / 30384 | -1.21 / 5137 / -119 | -1.52 / 3208 | 64 / 72 | -15932 vs -110710 | ok | n/a | PRO NT(0.5,) | no |
| ES.GEN_MV_close.70069fbb | GEN_MV_close | close | 36 | -92 / 7153 | 12.91 / 320 / 79 | 3.64 / 320 | 62 / 72 | -4468 vs -29867 | ok | n/a | PRO NT(0.5,) | no |
| ES.GEN_KB_pre.b460ed27 | GEN_KB_pre | pre | 216 | -306 / 17480 | 5.32 / 1670 / 171 | 37.68 / 286 | 62 / 72 | -228 vs -70430 | ok | n/a | SIZ ER(40, 0.3, 'low', 0.25) | no |
| ES.GEN_KB_pre.ad9faee7 | GEN_KB_pre | pre | 216 | -1593 / 29017 | -0.96 / 4621 / -86 | -0.44 / 4297 | 62 / 72 | -37319 vs -106717 | ok | n/a | SIZ ER(20, 0.3, 'low', 0.25) | no |
| ES.GEN_PE_pre.233d0830 | GEN_PE_pre | pre | 36 | -1462 / 24377 | -1.31 / 7427 / -187 | -4.00 / 2445 | 62 / 72 | -16720 vs -66352 | ok | n/a | ZON ZN('PD', 'behind', 0.8, 0.0) | no |
| ES.GEN_MV_nypm.897a8587 | GEN_MV_nypm | nypm | 36 | -489 / 14114 | 3.19 / 2781 / 170 | -0.46 / 2674 | 61 / 72 | -11030 vs -43632 | ok | n/a | PRO NT(0.65,) | no |
| ES.GEN_SM_nypm.11e3c421 | GEN_SM_nypm | nypm | 108 | -47 / 1713 | 1.61 / 923 / 29 | -0.68 / 923 | 61 / 72 | 12970 vs 7761 | ok | 0.08 | SIZ ER(40, 0.3, 'low', 0.25) | YES (WF>=60, null<=.10, L6M Cal>0) |
| ES.GEN_KB_close.9f75a538 | GEN_KB_close | close | 216 | 471 / 23427 | 1.26 / 4154 / 101 | 5.45 / 1061 | 61 / 72 | -7164 vs -33856 | ok | n/a | SIZ ER(40, 0.2, 'high', 0.25) | no |
| ES.GEN_MV_pre.9b1fcbc2 | GEN_MV_pre | pre | 36 | -588 / 11456 | 0.85 / 1387 / 23 | 0.10 / 1387 | 61 / 72 | -10484 vs -38485 | ok | n/a | STK SK(0, 15, 4) | no |
| ES.GEN_MV_nyam.7ed3be01 | GEN_MV_nyam | nyam | 36 | -250 / 9128 | -1.23 / 4343 / -102 | -3.14 / 4343 | 61 / 72 | 2637 vs -35266 | ok | 0.57 | STK SK(30, 0, 0) | no |
| ES.GEN_KB_nypm.73abb31e | GEN_KB_nypm | nypm | 216 | 128 / 3476 | 9.35 / 2418 / 434 | 11.13 / 1135 | 60 / 72 | -690 vs -22468 | ok | n/a | ZON ZN('PD', 'ahead', 0.8, 0.0) | no |
| ES.GEN_HM_nypm.0bf276e6 | GEN_HM_nypm | nypm | 24 | 83 / 32682 | 11.82 / 1515 / 344 | 14.70 / 1159 | 58 / 72 | 2836 vs -90987 | ok | 0.82 | SIZ ER(10, 0.4, 'low', 0.25) | no |
| ES.GEN_SM_pre.fd6347e2 | GEN_SM_pre | pre | 108 | -185 / 3916 | 9.62 / 305 / 56 | n/a / 0 | 58 / 72 | -522 vs -23403 | ok | n/a | PRO NT(0.8,) | no |
| ES.GEN_KB_nypm.34c83c8f | GEN_KB_nypm | nypm | 216 | 416 / 7634 | 1.14 / 1874 / 41 | 2.81 / 1874 | 58 / 72 | -15244 vs -57931 | ok | n/a | SIZ ER(40, 0.3, 'low', 0.25) | no |
| ES.GEN_MV_nyam.52f25bc2 | GEN_MV_nyam | nyam | 36 | 197 / 13910 | 10.37 / 767 / 153 | 2.45 / 647 | 57 / 72 | 8520 vs -13420 | ok | 0.49 | STK SK(30, 15, 1) | no |
| ES.GEN_SM_asia.3de57be1 | GEN_SM_asia | asia | 108 | 78 / 20357 | 8.31 / 1411 / 226 | 13.63 / 1411 | 57 / 72 | -15871 vs -79768 | ok | n/a | ZON ZN('VW', 'ahead', 0.4, 0.0) | no |
| ES.GEN_KB_close.9d8a2deb | GEN_KB_close | close | 216 | 102 / 16675 | 2.69 / 1776 / 92 | 3.10 / 1542 | 57 / 72 | -11271 vs -36609 | ok | n/a | STK SK(30, 15, 4) | no |
| ES.GEN_PE_pre.85695bee | GEN_PE_pre | pre | 36 | -382 / 19249 | 2.26 / 2867 / 124 | 4.09 / 1707 | 57 / 72 | -25775 vs -49912 | ok | n/a | ZON ZN('PD', 'behind', 0.8, 0.0) | no |
| ES.GEN_PE_nypm.b858ac75 | GEN_PE_nypm | nypm | 36 | -138 / 9307 | 0.90 / 2846 / 49 | -3.94 / 2846 | 57 / 72 | -29011 vs -45999 | ok | n/a | SIZ ER(20, 0.2, 'low', 0.25) | no |
| ES.GEN_KB_close.0a862756 | GEN_KB_close | close | 216 | 200 / 16055 | 0.18 / 5726 / 20 | -1.90 / 3479 | 57 / 72 | -10441 vs -38435 | ok | n/a | SIZ ER(40, 0.3, 'high', 0.25) | no |
| ES.GEN_HM_nyam.1fb9b55e | GEN_HM_nyam | nyam | 24 | -176 / 28760 | -0.01 / 5769 / -1 | -3.37 / 5769 | 57 / 72 | -19393 vs -65484 | ok | n/a | SIZ ER(40, 0.2, 'low', 0.25) | no |
| ES.GEN_HM_close.6719904d | GEN_HM_close | close | 24 | -256 / 10852 | -0.63 / 2716 / -33 | 9.44 / 600 | 57 / 72 | -12813 vs -44081 | ok | n/a | STK SK(30, 0, 5) | no |
| ES.GEN_MV_pre.2e1c3f95 | GEN_MV_pre | pre | 36 | 467 / 7737 | 16.66 / 2057 / 659 | 13.05 / 2057 | 56 / 72 | -27283 vs -65927 | ok | n/a | ZON ZN('VW', 'behind', 0.8, 0.5) | no |
| ES.GEN_HM_nyam.452f3ef5 | GEN_HM_nyam | nyam | 24 | 164 / 10550 | 10.65 / 972 / 199 | 17.63 / 733 | 56 / 72 | 3745 vs -15367 | ok | 0.26 | STK SK(15, 15, 4) | no |
| ES.GEN_SM_nypm.612a6453 | GEN_SM_nypm | nypm | 108 | -57 / 2192 | 4.69 / 1201 / 108 | 6.94 / 1201 | 56 / 72 | 8878 vs 11194 | ok | 0.43 | SIZ ER(10, 0.4, 'high', 0.25) | no |
| ES.GEN_HM_nypm.67609534 | GEN_HM_nypm | nypm | 24 | 25 / 9952 | 3.33 / 3555 / 228 | -1.26 / 3555 | 56 / 72 | 12188 vs -3408 | ok | 0.84 | STK SK(0, 15, 5) | no |
| ES.GEN_KB_nypm.61d3d6bb | GEN_KB_nypm | nypm | 216 | 220 / 16165 | 0.08 / 7373 / 11 | 0.02 / 5348 | 56 / 72 | -16278 vs -71704 | ok | n/a | STK SK(30, 15, 4) | no |

L2 adds on ES (WF OOS, dressed-L2 minus dressed-noL2 over 96 cells): median $1287 per OOS period-set, positive for 0.64 of cells.