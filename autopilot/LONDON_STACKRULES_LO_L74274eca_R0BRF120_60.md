# LONDON_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_LO_L74274eca_R0BRF120_60 (W-LAYERS, 2026-11-23 22:04Z)

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $2400); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_LO_L74274eca_R0BRF120_60). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -12); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -12); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -12)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -836); BL2 BookLock arm 1.5R give-back 50% (d ulcer -759); BL3 BookLock arm 1.5R give-back 67% (d ulcer -666)
- CAP: CAP5 per-book day loss stop -2R ($4800) (d ulcer -14); CAP1 per-book day profit stop +5R ($12000) (d ulcer -12); CAP2 per-book day profit stop +7.5R ($18000) (d ulcer -12)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($9600) (d ulcer -12); STK2 WHOLE-STACK day profit stop +6R of one book ($14400) (d ulcer -12); STK3 WHOLE-STACK day profit stop +8R of one book ($19200) (d ulcer -12)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer -12); SZ2 sizer thr 0.2 lo 0.5 (d ulcer -12); SZ3 sizer thr 0.4 lo 0.5 (d ulcer -12)

JOINT PICK: TL3_SR_LO_L74274eca_R0BRF120_60_N2_JT3 -> {'SC': 0, 'BL': 1, 'CAP': 5, 'STK': 1, 'SZ': 0}; rolling walk-forward 0.96 over 25 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +0%/-3%/-45%; verdict: passes walk-forward and bands (null still pending)

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 5148 / -11653 / -6683 / -6194 / 1584 (days stopped 0) | 5148 / -11653 / -6683 / -6194 / 1584 (days stopped 0) | 4307 / -10904 / -6683 / -7055 / 1914 (days stopped 0) | 5592 / -11653 / -6434 / 81 (x0.23) |
| L3M | 4632 / -10904 / -6683 / -5200 / 2144 (days stopped 0) | 4632 / -10904 / -6683 / -5200 / 2144 (days stopped 0) | 4654 / -10904 / -6683 / -4815 / 2564 (days stopped 0) | 5300 / -10904 / -7406 / 235 (x0.27) |
| 2023 | 9104 / -17549 / -8734 / -4220 / 74 (days stopped 0) | 9104 / -17549 / -8734 / -4220 / 74 (days stopped 0) | 9104 / -17549 / -8734 / -4220 / 74 (days stopped 0) | - |
| 2024 | 5746 / -15827 / -5004 / -4170 / 826 (days stopped 0) | 5746 / -15827 / -5004 / -4170 / 826 (days stopped 0) | 5746 / -15827 / -5004 / -4170 / 843 (days stopped 0) | - |
| 2025 | 6414 / -21198 / -9163 / -12248 / 538 (days stopped 0) | 6414 / -21198 / -9163 / -12248 / 538 (days stopped 0) | 4692 / -14398 / -9163 / -6890 / 580 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).
