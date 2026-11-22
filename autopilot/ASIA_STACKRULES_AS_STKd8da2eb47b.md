# ASIA_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_AS_STKd8da2eb47b (W-LAYERS, 2026-11-22 09:53Z)

BASIS OF EVERY NUMBER ON THIS PAGE: weighted native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $850); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_AS_STKd8da2eb47b). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard)
- BL: BL4 BookLock arm 2.0R give-back 33% (d ulcer -89); BL1 BookLock arm 1.5R give-back 33% (d ulcer -85); BL2 BookLock arm 1.5R give-back 50% (d ulcer -35)
- CAP: CAP1 per-book day profit stop +5R ($4250) (d ulcer -344); CAP2 per-book day profit stop +7.5R ($6375) (d ulcer -333); CAP3 per-book day profit stop +10R ($8500) (d ulcer -333)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($3400) (d ulcer -96); STK3 WHOLE-STACK day profit stop +8R of one book ($6800) (d ulcer -86); STK2 WHOLE-STACK day profit stop +6R of one book ($5100) (d ulcer -27)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: TL3_SR_AS_STKd8da2eb47b_N2_JT3 -> {'SC': 0, 'BL': 4, 'CAP': 1, 'STK': 1, 'SZ': 0}; rolling walk-forward 0.633 over 60 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +0%/+6%/+1%; verdict: passes walk-forward and bands (null still pending)

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 2581 / -8577 / -5079 / -6093 / 7468 (days stopped 0) | 2604 / -9644 / -5258 / -5258 / 7107 (days stopped 0) | 1989 / -9294 / -5258 / -5258 / 7229 (days stopped 0) | 4414 / -9644 / -6524 / 1293 (x0.27) |
| L3M | 2875 / -8526 / 1248 / -5933 / 6327 (days stopped 0) | 3364 / -9644 / -3643 / -5153 / 5884 (days stopped 0) | 2476 / -9294 / -4382 / -5153 / 6689 (days stopped 0) | 4181 / -9644 / -7345 / 791 (x0.30) |
| 2023 | 2825 / -6313 / -3586 / -2849 / 931 (days stopped 0) | 3459 / -9138 / -3561 / -4097 / 727 (days stopped 0) | 3460 / -9138 / -3561 / -4097 / 720 (days stopped 0) | - |
| 2024 | 5723 / -15575 / -7296 / -5368 / 1234 (days stopped 0) | 5254 / -12638 / -6521 / -5218 / 1214 (days stopped 0) | 5482 / -13033 / -6521 / -5218 / 1142 (days stopped 0) | - |
| 2025 | 5950 / -14678 / -9221 / -7158 / 1441 (days stopped 0) | 6809 / -17334 / -10920 / -6603 / 890 (days stopped 0) | 6921 / -17657 / -10726 / -6846 / 885 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
