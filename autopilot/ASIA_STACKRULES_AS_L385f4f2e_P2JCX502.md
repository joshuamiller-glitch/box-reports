# ASIA_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_AS_L385f4f2e_P2JCX502 (W-LAYERS, 2026-11-22 10:27Z)

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $1200); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_AS_L385f4f2e_P2JCX502). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (0 of 5 draws beaten (real best-of -0.000 vs null [-0.13, -0.004, -0.024, -0.206, -0.032]) FAIL), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +0, fails guard)
- BL: BL4 BookLock arm 2.0R give-back 33% (d ulcer -0); BL2 BookLock arm 1.5R give-back 50% (d ulcer +0, fails guard); BL5 BookLock arm 2.0R give-back 50% (d ulcer +0, fails guard)
- CAP: CAP1 per-book day profit stop +5R ($6000) (d ulcer +0, fails guard); CAP2 per-book day profit stop +7.5R ($9000) (d ulcer +0, fails guard); CAP3 per-book day profit stop +10R ($12000) (d ulcer +0, fails guard)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($4800) (d ulcer +0, fails guard); STK2 WHOLE-STACK day profit stop +6R of one book ($7200) (d ulcer +0, fails guard); STK3 WHOLE-STACK day profit stop +8R of one book ($9600) (d ulcer +0, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: TL3_SR_AS_L385f4f2e_P2JCX502_N2_JT3 -> {'SC': 0, 'BL': 4, 'CAP': 1, 'STK': 1, 'SZ': 0}; rolling walk-forward 0.968 over 31 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +0%/+0%/-1%; verdict: passes walk-forward and bands (null still pending)

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 492 / -1915 / -1600 / -1915 / 2123 (days stopped 0) | 492 / -1915 / -1600 / -1915 / 2157 (days stopped 0) | 492 / -1915 / -1600 / -1915 / 2202 (days stopped 0) | 876 / -1915 / -1295 / 257 (x0.05) |
| L3M | 551 / -1915 / -219 / -1915 / 2501 (days stopped 0) | 551 / -1915 / -219 / -1915 / 2514 (days stopped 0) | 551 / -1915 / -219 / -1915 / 2514 (days stopped 0) | 830 / -1915 / -1458 / 157 (x0.06) |
| 2023 | 2247 / -4696 / -2024 / -1250 / 44 (days stopped 0) | 2247 / -4696 / -2024 / -1250 / 44 (days stopped 0) | 2247 / -4696 / -2024 / -1250 / 44 (days stopped 0) | - |
| 2024 | 4445 / -11407 / -3539 / -1210 / 240 (days stopped 0) | 4445 / -11407 / -3539 / -1210 / 240 (days stopped 0) | 4445 / -11407 / -3539 / -1210 / 240 (days stopped 0) | - |
| 2025 | 4406 / -10172 / -3904 / -3610 / 179 (days stopped 0) | 4406 / -10172 / -3904 / -3610 / 179 (days stopped 0) | 4405 / -10172 / -3904 / -3610 / 182 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
