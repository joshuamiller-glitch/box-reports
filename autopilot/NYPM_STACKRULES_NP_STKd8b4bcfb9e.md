# NYPM_STACKRULES - stack-rule + daily-stop fit for TL3_ALN_NP_STKd8b4bcfb9e (W-LAYERS, 2026-11-24 17:33Z)

BASIS OF EVERY NUMBER ON THIS PAGE: native lot basis: 1 lot(s) per trade (weighted finals: whole-number lots = weights x4); wrapper = R1 = today's wrapper on that lot basis (lin), R0 = truly bare (every wrapper rule off). Native lot basis 1 (R = $1800); R0 = truly bare, R1 = today's wrapper at this lot basis (TL3_ALN_NP_STKd8b4bcfb9e). Families SC / BL / CAP / STK / SZ varied together on an OA(27,13,3,2) (reference + top-2 of the screen per family), 26 combos x 42 months. Gates: rolling walk-forward vs R1 >= 0.58, year band equal-risk $/wk (RED > 30%) with the whole-history-dollars band beside it, null >= 4/5 (PENDING: needs W-SHORT stack-level null files for this stack), 27/30 not a gate. WEAK = nothing passes; the best setting is still shown.

Screen top-3 per family (one setting at a time, L6M, d ulcer vs R1; negative = better):

- SC: SC1 StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -82); SC2 StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -82); SC3 StackCut share 100% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots) (d ulcer -82)
- BL: BL1 BookLock arm 1.5R give-back 33% (d ulcer -114); BL2 BookLock arm 1.5R give-back 50% (d ulcer -37); BL3 BookLock arm 1.5R give-back 67% (d ulcer -14)
- CAP: CAP1 per-book day profit stop +5R ($9000) (d ulcer +0, fails guard); CAP2 per-book day profit stop +7.5R ($13500) (d ulcer +0, fails guard); CAP3 per-book day profit stop +10R ($18000) (d ulcer +0, fails guard)
- STK: STK1 WHOLE-STACK day profit stop +4R of one book ($7200) (d ulcer +0, fails guard); STK2 WHOLE-STACK day profit stop +6R of one book ($10800) (d ulcer +0, fails guard); STK3 WHOLE-STACK day profit stop +8R of one book ($14400) (d ulcer +0, fails guard)
- SZ: SZ1 sizer today thr 0.3 lo 0.5 (d ulcer +0, fails guard); SZ2 sizer thr 0.2 lo 0.5 (d ulcer +0, fails guard); SZ3 sizer thr 0.4 lo 0.5 (d ulcer +0, fails guard)

JOINT PICK: TL3_SR_NP_STKd8b4bcfb9e_N2_JT4 -> {'SC': 1, 'BL': 1, 'CAP': 2, 'STK': 0, 'SZ': 0}; rolling walk-forward 0.797 over 69 periods; year colours GREEN/GREEN/GREEN; whole-history-dollars band (equal-risk $/wk change as % of the whole-history $/wk of R1) +4%/+8%/+4%; verdict: passes walk-forward and bands (null still pending)

| window | R0 bare (this stack) | R1 today | joint pick | bare D7 R0 (BARE_D7_YARDSTICK, scaled to this stack's R1 max DD; bare beside bare only) |
|---|---|---|---|---|
| L6M | 2227 / -6395 / -5112 / -4439 / 2433 (days stopped 0) | 2227 / -6395 / -5112 / -4439 / 2433 (days stopped 0) | 2030 / -5386 / -4707 / -4369 / 2481 (days stopped 0) | no bare D7 R0 rows for this session (NY PM: none) |
| L3M | 2053 / -5889 / -2342 / -4439 / 2204 (days stopped 0) | 2053 / -5889 / -2342 / -4439 / 2204 (days stopped 0) | 1717 / -4839 / -2272 / -4369 / 2619 (days stopped 0) | no bare D7 R0 rows for this session (NY PM: none) |
| 2023 | 8468 / -17458 / -4783 / -4594 / 503 (days stopped 0) | 8468 / -17458 / -4783 / -4594 / 503 (days stopped 0) | 9147 / -19173 / -4783 / -4594 / 500 (days stopped 0) | no bare D7 R0 rows for this session (NY PM: none) |
| 2024 | 10425 / -25100 / -8162 / -5135 / 944 (days stopped 0) | 10425 / -25100 / -8162 / -5135 / 867 (days stopped 0) | 10632 / -25180 / -8052 / -5120 / 793 (days stopped 0) | no bare D7 R0 rows for this session (NY PM: none) |
| 2025 | 4340 / -16310 / -6186 / -6308 / 1419 (days stopped 0) | 4462 / -18105 / -6184 / -8103 / 1358 (days stopped 0) | 4551 / -12435 / -6325 / -6094 / 1344 (days stopped 0) | no bare D7 R0 rows for this session (NY PM: none) |

Cells: ulcer / max DD / worst week / worst DAY / $ per week. Not yet automatic here: NULL (needs W-SHORT null files for this stack), 30 CONTROLS (W-COMBO control sets), LOT CHECK at 2x and 4x the native lots (stage built next).

## LOT CHECK and CONTROLS (automatic, 17:41Z)

Per-lot results of the final combo at 1x / 2x / 4x the native lots (dollar columns divided by the lot multiple; ulcer / max DD / worst week / $ per week):

| window | 1x | 2x per lot | 4x per lot |
|---|---|---|---|
| L6M | 2030 / -5386 / -4707 / 2481 | 2001 / -5276 / -4158 / 2384 | 1895 / -4970 / -4189 / 2407 |
| L3M | 1717 / -4839 / -2272 / 2619 | 1745 / -4902 / -2314 / 2439 | 1776 / -4970 / -2367 / 2384 |
| 2023 | 9147 / -19173 / -4783 / 500 | 8322 / -17366 / -5056 / 516 | 9445 / -18878 / -5070 / 459 |
| 2024 | 10632 / -25180 / -8052 / 793 | 8822 / -23284 / -8404 / 936 | 9393 / -23456 / -8451 / 875 |
| 2025 | 4551 / -12435 / -6325 / 1344 | 4102 / -16138 / -6387 / 1252 | 4186 / -16334 / -6447 / 1208 |

Controls: no ctl_prefix / control sets for this final: not run (W-COMBO).
