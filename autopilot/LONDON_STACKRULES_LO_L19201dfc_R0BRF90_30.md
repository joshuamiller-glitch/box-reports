# LONDON_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_LO_L19201dfc_R0BRF90_30 (W-LAYERS, 2026-11-23 21:24Z)

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $1800); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_LO_L19201dfc_R0BRF90_30). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer +0, fails guard); BL2 BookLock arm 1.5R give-back 50% (d ulcer +0, fails guard); BL3 BookLock arm 1.5R give-back 67% (d ulcer +0, fails guard)
- CAP: CAP1 per-book day profit stop +5R ($9000) (d ulcer +0, fails guard); CAP2 per-book day profit stop +7.5R ($13500) (d ulcer +0, fails guard); CAP3 per-book day profit stop +10R ($18000) (d ulcer +0, fails guard)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($7200) (d ulcer +0, fails guard); STK2 WHOLE-STACK day profit stop +6R of one book ($10800) (d ulcer +0, fails guard); STK3 WHOLE-STACK day profit stop +8R of one book ($14400) (d ulcer +0, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: none of the combos lowers L6M ulcer inside the 15% guard: R1 stays; WEAK.

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 1253 / -3809 / -2673 / -3310 / 1768 (days stopped 0) | 1253 / -3809 / -2673 / -3310 / 1768 (days stopped 0) | - | 1828 / -3809 / -2103 / 26 (x0.08) |
| L3M | 1390 / -3402 / -2449 / -3310 / 1643 (days stopped 0) | 1390 / -3402 / -2449 / -3310 / 1643 (days stopped 0) | - | 1654 / -3402 / -2311 / 73 (x0.08) |
| 2023 | 1935 / -5238 / -2549 / -1800 / 273 (days stopped 0) | 1935 / -5238 / -2549 / -1800 / 273 (days stopped 0) | - | - |
| 2024 | 4315 / -11780 / -5793 / -4164 / 261 (days stopped 0) | 4315 / -11780 / -5793 / -4164 / 261 (days stopped 0) | - | - |
| 2025 | 5068 / -12803 / -4448 / -3005 / 183 (days stopped 0) | 5068 / -12803 / -4448 / -3005 / 183 (days stopped 0) | - | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
