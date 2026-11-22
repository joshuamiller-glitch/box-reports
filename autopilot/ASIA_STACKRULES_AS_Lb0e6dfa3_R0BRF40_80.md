# ASIA_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_AS_Lb0e6dfa3_R0BRF40_80 (W-LAYERS, 2026-11-22 07:26Z)

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $800); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_AS_Lb0e6dfa3_R0BRF40_80). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +48, fails guard); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +48, fails guard); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer +48, fails guard)
- BL: BL3 BookLock arm 1.5R give-back 67% (d ulcer -241); BL1 BookLock arm 1.5R give-back 33% (d ulcer -23); BL8 BookLock arm 3.0R give-back 50% (d ulcer +32, fails guard)
- CAP: CAP1 per-book day profit stop +5R ($4000) (d ulcer -57); CAP2 per-book day profit stop +7.5R ($6000) (d ulcer -56); CAP3 per-book day profit stop +10R ($8000) (d ulcer -56)
- STK: STK6 WHOLE-STACK day loss stop -4R of one book ($3200) (d ulcer -56); STK3 WHOLE-STACK day profit stop +8R of one book ($6400) (d ulcer +48, fails guard); STK4 WHOLE-STACK day profit stop +12R of one book ($9600) (d ulcer +48, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +48, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +48, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +48, fails guard)

JOINT PICK: TL3_SR_AS_Lb0e6dfa3_R0BRF40_80_N2_JT5 -> {'SC': 2, 'BL': 3, 'CAP': 0, 'STK': 3, 'SZ': 0}; rolling walk-forward 0.646 over 48 periods; year colours GREEN/GREEN/RED; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +3%/+7%/+46%; verdict: FAILS: RED year

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 2643 / -8614 / -4590 / -5594 / 2969 (days stopped 0) | 2643 / -8614 / -4590 / -5594 / 2969 (days stopped 0) | 2402 / -7664 / -5046 / -5559 / 2407 (days stopped 0) | 3943 / -8614 / -5828 / 1155 (x0.24) |
| L3M | 3040 / -8614 / -3461 / -5594 / 1930 (days stopped 0) | 3040 / -8614 / -3461 / -5594 / 1930 (days stopped 0) | 1387 / -5544 / -2892 / -2979 / 2126 (days stopped 0) | 3735 / -8614 / -6561 / 707 (x0.27) |
| 2023 | 2942 / -9402 / -2099 / -3189 / 386 (days stopped 0) | 2942 / -9402 / -2099 / -3189 / 386 (days stopped 0) | 3144 / -9722 / -2099 / -3189 / 384 (days stopped 0) | - |
| 2024 | 4048 / -10907 / -5123 / -3764 / 506 (days stopped 0) | 4048 / -10907 / -5123 / -3764 / 506 (days stopped 0) | 4127 / -11206 / -5123 / -3764 / 441 (days stopped 0) | - |
| 2025 | 4306 / -12361 / -5081 / -5558 / 690 (days stopped 0) | 4306 / -12361 / -5081 / -5558 / 690 (days stopped 0) | 4908 / -13445 / -5081 / -5558 / 264 (days stopped 0) | - |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).

## LOT CHECK and CONTROLS (automatic, 07:41Z)

Per-lot results of the final combo at 1x / 2x / 4x the native lots (dollar columns divided by the lot multiple; ulcer / max DD / worst week / $ per week):

| window | 1x | 2x per lot | 4x per lot |
|---|---|---|---|
| L6M | 2402 / -7664 / -5046 / 2407 | 2515 / -7937 / -5141 / 2321 | 2426 / -7643 / -4943 / 2248 |
| L3M | 1387 / -5544 / -2892 / 2126 | 1512 / -6256 / -3634 / 2039 | 1532 / -6302 / -3689 / 1858 |
| 2023 | 3144 / -9722 / -2099 / 384 | 3174 / -9762 / -2099 / 378 | 3313 / -9987 / -2121 / 361 |
| 2024 | 4127 / -11206 / -5123 / 441 | 4197 / -11391 / -5108 / 428 | 4248 / -11342 / -5256 / 416 |
| 2025 | 4908 / -13445 / -5081 / 264 | 5148 / -13632 / -5136 / 265 | 5280 / -13681 / -5110 / 230 |

30 date-shift controls (same setting on the control sets): real gain beats 13 of 30 controls (27/30 shown only, not a gate).
