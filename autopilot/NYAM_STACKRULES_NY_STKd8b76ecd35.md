# NYAM_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_NY_STKd8b76ecd35 (W-LAYERS, 2026-11-22 12:12Z)

> **FIT ON AN INCOMPLETE-ROUND FINAL**: ny-own / ny-own-l3g add round 4 re-opened by W-COMBO (10:58Z audit) (the search round was re-opened by W-COMBO; this stack was decided on a partial add round; a corrected final will be fitted as a new final and this fit marked SUPERSEDED).

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $1200); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_NY_STKd8b76ecd35). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1437, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1437, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +1437, fails guard)
- BL: BL6 BookLock arm 2.0R give-back 67% (d ulcer -83); BL1 BookLock arm 1.5R give-back 33% (d ulcer -161, fails guard); BL4 BookLock arm 2.0R give-back 33% (d ulcer -71, fails guard)
- CAP: CAP1 per-book day profit stop +5R ($6000) (d ulcer +0, fails guard); CAP2 per-book day profit stop +7.5R ($9000) (d ulcer +0, fails guard); CAP3 per-book day profit stop +10R ($12000) (d ulcer +0, fails guard)
- STK: STK2 WHOLE-STACK day profit stop +6R of one book ($7200) (d ulcer -5); STK1 WHOLE-STACK day profit stop +4R of one book ($4800) (d ulcer -212, fails guard); STK4 WHOLE-STACK day profit stop +12R of one book ($14400) (d ulcer +0, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: TL3_SR_NY_STKd8b76ecd35_N2_JT3 -> {'SC': 0, 'BL': 6, 'CAP': 1, 'STK': 2, 'SZ': 0}; rolling walk-forward 0.562 over 64 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +3%/-31%/-6%; verdict: FAILS: rolling WF 0.56 < 0.58

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 4372 / -15007 / -14493 / -7608 / 7495 (days stopped 0) | 3779 / -12120 / -1591 / -7157 / 8283 (days stopped 0) | 3681 / -12120 / -1406 / -7157 / 8151 (days stopped 0) | 6862 / -12120 / -5315 / -137 (x0.19) |
| L3M | 3540 / -9765 / -3445 / -7157 / 6747 (days stopped 0) | 3469 / -9765 / -1591 / -7157 / 7047 (days stopped 0) | 3483 / -9765 / -1406 / -7157 / 6501 (days stopped 0) | 5475 / -9765 / -3392 / -392 (x0.18) |
| 2023 | 11117 / -31342 / -13132 / -12462 / 2016 (days stopped 0) | 11621 / -32662 / -13132 / -12462 / 1942 (days stopped 0) | 11777 / -33057 / -13132 / -12462 / 1877 (days stopped 0) | - |
| 2024 | 10668 / -31020 / -19393 / -10792 / 2349 (days stopped 0) | 12543 / -35875 / -19393 / -10792 / 1942 (days stopped 0) | 10014 / -28407 / -19393 / -10792 / 2308 (days stopped 0) | - |
| 2025 | 15583 / -59504 / -30226 / -17236 / 3561 (days stopped 0) | 12442 / -45085 / -24022 / -16111 / 3102 (days stopped 0) | 12920 / -45601 / -24897 / -16111 / 3405 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
