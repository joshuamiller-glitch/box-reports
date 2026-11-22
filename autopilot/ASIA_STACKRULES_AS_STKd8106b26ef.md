# ASIA_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_AS_STKd8106b26ef [PROVISIONAL: loop not final; members ['Lb0e6dfa3.BRF40_80', 'L385f4f2e.J502', 'L92a90948', 'L6b373671.BRP60', 'L578701ed.BRF30_90']; the last fit on the complete pool is the real one] (W-LAYERS, 2026-11-22 10:56Z)

BASIS OF EVERY NUMBER ON THIS PAGE: weighted native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $1200); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_AS_STKd8106b26ef). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -925, fails guard); BL2 BookLock arm 1.5R give-back 50% (d ulcer -628, fails guard); BL3 BookLock arm 1.5R give-back 67% (d ulcer -592, fails guard)
- CAP: CAP8 per-book day loss stop -6R ($7200) (d ulcer -31); CAP5 per-book day loss stop -2R ($2400) (d ulcer -155, fails guard); CAP1 per-book day profit stop +5R ($6000) (d ulcer +0, fails guard)
- STK: STK3 WHOLE-STACK day profit stop +8R of one book ($9600) (d ulcer +0, fails guard); STK4 WHOLE-STACK day profit stop +12R of one book ($14400) (d ulcer +0, fails guard); STK2 WHOLE-STACK day profit stop +6R of one book ($7200) (d ulcer +51, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: TL3_SR_AS_STKd8106b26ef_N2_JT1 -> {'SC': 1, 'BL': 0, 'CAP': 8, 'STK': 4, 'SZ': 0}; rolling walk-forward 0.633 over 79 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +0%/+0%/-0%; verdict: passes walk-forward and bands (null still pending)

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 3046 / -9450 / -4971 / -6578 / 10834 (days stopped 0) | 3462 / -11350 / -4928 / -7931 / 9103 (days stopped 0) | 3431 / -11350 / -4928 / -7931 / 9074 (days stopped 0) | 5195 / -11350 / -7678 / 1521 (x0.32) |
| L3M | 3375 / -9283 / -1858 / -6578 / 10600 (days stopped 0) | 3894 / -11350 / -4928 / -7313 / 9641 (days stopped 0) | 3902 / -11350 / -4928 / -7313 / 9626 (days stopped 0) | 4921 / -11350 / -8644 / 931 (x0.36) |
| 2023 | 5200 / -11178 / -7756 / -4718 / 1042 (days stopped 0) | 6638 / -15799 / -8770 / -7498 / 837 (days stopped 0) | 6638 / -15799 / -8770 / -7498 / 837 (days stopped 0) | - |
| 2024 | 4545 / -16311 / -8171 / -8853 / 1917 (days stopped 0) | 6967 / -18012 / -7046 / -7253 / 1279 (days stopped 0) | 6967 / -18012 / -7046 / -7253 / 1279 (days stopped 0) | - |
| 2025 | 6567 / -17403 / -9888 / -11445 / 1982 (days stopped 0) | 7313 / -19861 / -10513 / -9256 / 1245 (days stopped 0) | 7309 / -19861 / -10513 / -9256 / 1250 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
