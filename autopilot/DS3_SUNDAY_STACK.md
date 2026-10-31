# DS3_SUNDAY_STACK - D6 v2.3b exactly as coded, jointly on the lock-engine stack (FOLLOW-UP section 1) - FINAL (stage 2: QUANT-LAYER, placebos, sensitivity)

Research only. No live/execution/chart change. UNTOUCHED never read (every frame capped at label day 20260206). Own masks: L3M 20251106.. (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131, all to 20260206. Code `l2vast/ds3/code/sundaystack/` (ss_lib.py scenario runner on stack2/s2_lib + a sized-governor lock engine and the PE confirmation kernel; run_all.py, quant_A.py (sensitivity), quant_P.py (placebos), quant_total.py (QUANT columns), make_final.py / write_final.py), outputs `l2vast/ds3/out/sundaystack/`. Prereg `autopilot/SUNDAYSTACK_prereg.md` (written after the first scoring run of the coded composite; no selection in it). Basis N (no target-fill correction); stop cost Native 1.28 as coded, 2.45 (live JoinThenMarket) beside. $/wk = lock-engine stack weekly mean; SD / maxDD / worst-20 (sum of the 20 worst weeks) from the weekly series; MDE = 2.8 x SE of the paired weekly delta; [CI] = 4-week-block bootstrap of the weekly delta (2,000 draws). Tie-out: the same engine reproduces DS3_SPLIT_2 (S73 N L6M 79,055; market 61,477 at the 1.01 stop) to the dollar.

## 0. Plain sentences and verdict (page 1)
**as coded, Sunday's D6 vs the stack as it is (LIVE lots on the four engine books K6 P6 U6 H6): +22.3k $/wk L6M (MDE 18.9k), +20.0k HOLD (MDE 18.3k), +3.3k PRE (MDE 14.4k) [+11.1k X' (MDE 14.7k)].**
**as coded, Sunday's D6 vs the stack as it is (LIVE lots + ST/WT at research/2.35): +35.9k $/wk L6M (MDE 27.7k), +33.6k HOLD (MDE 26.3k), +14.7k PRE (MDE 19.2k) [+9.5k X' (MDE 19.1k)].**
**as coded, Sunday's D6 vs the stack as it is (RESEARCH lots): +82.8k $/wk L6M (MDE 51.7k), +76.1k HOLD (MDE 50.7k), +27.0k PRE (MDE 33.3k) [+13.0k X' (MDE 34.6k)].**

Base-lot governors instead (planned-lot R, not multiplied by the day's largest multiplier): live4 L6M +13.4k (MDE 17.0k), HOLD +12.5k, PRE +0.1k, X' +12.1k; research L6M +45.7k (MDE 50.6k), HOLD +44.9k, PRE +5.6k, X' +21.9k. With the 2.45 join stop instead of Native: live4 L6M +20.6k, HOLD +18.3k, PRE +1.1k.

**Integer live-lot splits and modelled add slippage (lead request, UF-ENTRY C7), and the leave-one-out row "no add on K6".** Split at the integer lots: K6 1/1, U6 3/1, H6 3/1 (1/1 in NY-AM), P6 5/2 (run as the 0.7 cell), ST/WT 0.7; the modelled add slippage (+0.25 pt per lot, stress +0.45) is charged on every add fill (the PE-confirmed add too); the rest of the coded stack unchanged (sized governors, Native stops). "No add on K6" = K6 enters plain at market, the other books split. Delta vs the stack as it is, $k/wk; last column = change vs the coded cell.
#### LIVE lots, engine books K6 P6 U6 H6

| config | mean $k/wk L3M | L6M | HOLD | PRE | X' | delta vs as-is L6M (MDE) | HOLD | PRE | X' | change vs the coded cell L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|
| FULL (fractional 70/30, no add slippage) | 33.1 | 40.4 | 37.1 | 18.8 | 7.6 | +22.3 (18.9) | +20.0 | +3.3 | +11.1 | +0.0 / +0.0 / +0.0 / +0.0 |
| integer split, add slip 0 | 34.5 | 40.8 | 37.3 | 18.8 | 7.4 | +22.8 (19.3) | +20.2 | +3.3 | +10.9 | +0.5 / +0.3 / -0.0 / -0.3 |
| integer split, add slip +0.25 | 34.0 | 40.4 | 36.9 | 18.4 | 7.1 | +22.3 (19.3) | +19.8 | +2.9 | +10.6 | +0.0 / -0.2 / -0.4 / -0.5 |
| integer split, add slip +0.45 (stress) | 33.6 | 40.1 | 36.6 | 18.1 | 6.9 | +22.0 (19.3) | +19.5 | +2.6 | +10.4 | -0.2 / -0.4 / -0.7 / -0.7 |
| LOO: no add on K6 (fractional split) | 31.9 | 40.0 | 36.9 | 18.1 | 7.2 | +21.9 (18.7) | +19.8 | +2.6 | +10.7 | -0.4 / -0.2 / -0.7 / -0.4 |
| LOO: no add on K6, integer, +0.25 | 31.5 | 39.6 | 36.5 | 17.7 | 7.0 | +21.5 (18.7) | +19.4 | +2.2 | +10.5 | -0.8 / -0.6 / -1.1 / -0.7 |
| LOO: no add on K6, integer, +0.45 | 31.2 | 39.4 | 36.3 | 17.4 | 6.8 | +21.3 (18.7) | +19.2 | +2.0 | +10.3 | -1.0 / -0.8 / -1.3 / -0.8 |

#### LIVE lots + ST/WT research/2.35

| config | mean $k/wk L3M | L6M | HOLD | PRE | X' | delta vs as-is L6M (MDE) | HOLD | PRE | X' | change vs the coded cell L6M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|
| FULL (fractional 70/30, no add slippage) | 57.3 | 64.4 | 57.0 | 37.1 | 9.1 | +35.9 (27.7) | +33.6 | +14.7 | +9.5 | +0.0 / +0.0 / +0.0 / +0.0 |
| integer split, add slip 0 | 58.4 | 64.5 | 56.9 | 37.2 | 8.8 | +36.0 (28.1) | +33.6 | +14.8 | +9.2 | +0.1 / -0.1 / +0.1 / -0.3 |
| integer split, add slip +0.25 | 57.7 | 63.7 | 56.1 | 35.8 | 8.4 | +35.2 (28.1) | +32.8 | +13.4 | +8.8 | -0.7 / -0.8 / -1.3 / -0.7 |
| integer split, add slip +0.45 (stress) | 57.0 | 63.0 | 55.5 | 35.4 | 8.0 | +34.5 (28.0) | +32.2 | +13.0 | +8.4 | -1.4 / -1.5 / -1.8 / -1.1 |
| LOO: no add on K6 (fractional split) | 55.9 | 63.8 | 56.6 | 36.4 | 8.6 | +35.3 (27.6) | +33.3 | +14.0 | +9.1 | -0.6 / -0.4 / -0.7 / -0.4 |
| LOO: no add on K6, integer, +0.25 | 55.0 | 62.8 | 55.6 | 35.1 | 8.2 | +34.3 (27.6) | +32.3 | +12.7 | +8.6 | -1.6 / -1.3 / -2.1 / -0.9 |
| LOO: no add on K6, integer, +0.45 | 54.4 | 62.2 | 55.1 | 34.7 | 7.9 | +33.7 (27.5) | +31.8 | +12.3 | +8.4 | -2.2 / -1.9 / -2.5 / -1.2 |

Reading: the integer split changes the stack by -0.5..+0.5k before slippage; +0.25 pt per add lot costs about 0.2-0.5k a week at live lots (0.7-1.8k with ST/WT) and +0.45 about 0.4-0.7k (1.1-1.8k): nothing near the MDE. On the stack, "no add on K6" LOWERS the stack by 0.2-0.7k (L6M -0.4k at the coded cell; -0.8k at integer +0.25), so this engine does not reproduce C7's per-book K6 loss (-3.0k L6M at equal risk): the K6 add is a small positive here (K6 is 2 lots, the add 1 lot). No change recommended on this evidence; the C7 per-book K6 result and this one differ in engine (equal-risk scaling vs the lock-engine stack with ER sizing and governors).

**Verdict.** Tier CANDIDATE-RECENT, not PASS. The composite is one pre-specified configuration (1 of 1) and clears the MDE in L6M and HOLD at live lots (L6M +22.3k vs 18.9k; HOLD +20.0k vs 18.3k) and at research lots, is positive in PRE (+3.3k live, +27.0k research) and X' (+11.1k, +13.0k) but INSIDE their MDE (PRE Romano-Wolf p 0.79); the six pieces are post-hoc-selected (section 8) and the cumulative-trial adjusted p is 1.00. The gain is concentrated in the ER sizer (alone +11.6k L6M at live lots, +47.4k at research lots) and, at research lots, in the sized-governor reading (the same sizer with planned-lot governors is +17.0k); the split, the zone skip and the Native stop are positive in every window at research lots (L6M contribution +10.7k / +15.7k / +11.7k) and small at live lots (+2.6k / +1.3k / +1.7k); the PE confirmation is positive in L6M/HOLD and ~0 in PRE/X'; the Asia-stopped cut is about zero at live lots (it needs the other same-side books open: only 4 engine books are live here).

**The one change before 18:00 ET Sunday.** Applying the pre-stated rule to every piece, at every lot set and under both governor readings, the pieces for which removal improves L6M, HOLD, PRE and X' together: none. Nothing meets the rule, so the numbers support NO change. Watch items that are NOT changes (none meets the rule; all inside their MDE): at live lots the Asia-stopped cut contributes -1.1k L6M, -1.6k HOLD, -0.9k PRE, +0.7k X' (MDE of the L6M leave-one-out delta 3.5k); the sized-lot governor reading is an implementation choice worth +37k L6M at research lots / +9k at live lots, PRE +21k / +3k and X' -9k / -1k (it also lifts the drawdown: L6M maxDD 464k vs 323k at research lots, 97k vs 86k at live lots, and the SD) - confirm that D6 really multiplies the locks by the day's largest multiplier, because the number depends on it. The stage-1 pre-statement (cut = the weakest piece) is unchanged.

Change-rule table (contribution of each piece = FULL - FULL without it, $k/wk):
| lots | governors | piece | L6M | HOLD | PRE | X' | harmful in all four? |
|---|---|---|---|---|---|---|---|
| live4 | sized | split | +2.6 | +2.4 | +1.2 | +1.2 | no |
| live4 | sized | pe | +3.3 | +4.0 | -1.6 | +0.0 | no |
| live4 | sized | er | +13.7 | +12.5 | +0.6 | +0.2 | no |
| live4 | sized | cut | -1.1 | -1.6 | -0.9 | +0.7 | no |
| live4 | sized | zone | +1.3 | +0.4 | +2.7 | +3.1 | no |
| live4 | sized | stop | +1.7 | +1.7 | +2.2 | +1.8 | no |
| live4 | base | split | -0.3 | +0.0 | -0.7 | +1.9 | no |
| live4 | base | pe | +0.7 | +1.5 | +0.3 | -0.6 | no |
| live4 | base | er | +4.8 | +5.1 | -2.6 | +1.2 | no |
| live4 | base | cut | +1.3 | +1.1 | +0.0 | +0.8 | no |
| live4 | base | zone | -1.3 | -2.7 | +1.8 | +4.6 | no |
| live4 | base | stop | +3.5 | +3.2 | +1.7 | +1.4 | no |
| live+ | sized | split | +6.3 | +5.9 | +4.8 | +0.6 | no |
| live+ | sized | pe | +3.5 | +4.2 | -1.8 | +0.1 | no |
| live+ | sized | er | +15.8 | +15.5 | +7.7 | +0.2 | no |
| live+ | sized | cut | -1.7 | -1.7 | +0.3 | -1.3 | no |
| live+ | sized | zone | +1.8 | +0.3 | +4.5 | +2.7 | no |
| live+ | sized | stop | +5.0 | +4.7 | +4.9 | +3.0 | no |
| live+ | base | split | +2.9 | +2.8 | +0.9 | +2.3 | no |
| live+ | base | pe | +1.8 | +2.5 | +0.7 | -0.6 | no |
| live+ | base | er | +5.8 | +7.4 | -2.7 | +4.2 | no |
| live+ | base | cut | +4.7 | +4.4 | +0.6 | +0.2 | no |
| live+ | base | zone | +0.8 | -0.9 | +2.0 | +5.1 | no |
| live+ | base | stop | +3.3 | +3.2 | +4.1 | +2.7 | no |
| research | sized | split | +10.7 | +10.4 | +9.7 | +1.1 | no |
| research | sized | pe | +4.5 | +5.7 | -0.5 | -2.1 | no |
| research | sized | er | +26.6 | +25.1 | +12.5 | +4.5 | no |
| research | sized | cut | +4.7 | +3.5 | -1.6 | -1.9 | no |
| research | sized | zone | +15.7 | +12.5 | +5.1 | +1.3 | no |
| research | sized | stop | +11.7 | +11.0 | +9.8 | +6.3 | no |
| research | base | split | +4.0 | +3.8 | +3.5 | +2.4 | no |
| research | base | pe | +1.3 | +2.5 | -0.2 | -3.5 | no |
| research | base | er | -10.5 | -6.1 | -8.9 | +13.4 | no |
| research | base | cut | +5.1 | +4.9 | -2.4 | -1.0 | no |
| research | base | zone | +9.3 | +6.2 | +1.4 | +4.7 | no |
| research | base | stop | +7.7 | +7.4 | +8.5 | +5.4 | no |

## 1. Headline: D6 v2.3b vs the stack as it is, per lot set (recent first)
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

| config | window | mean $k/wk | SD | maxDD | worst-20 (sum $k) | delta vs as-is $k/wk (MDE) [week-block 95% CI] |
|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | L3M | 7.2 | 52 | 118 | 101 | - |
|  | L6M | 18.1 | 45 | 118 | -18 | - |
|  | HOLD | 17.1 | 53 | 166 | -243 | - |
|  | PRE | 15.5 | 49 | 273 | -842 | - |
|  | X' | -3.5 | 31 | 287 | -591 | - |
| D6 v2.3b as coded (sized-lot governors, Native 1.28) | L3M | 33.1 | 51 | 97 | 463 | +25.8 (27.4) [+15.0, +37.0] |
|  | L6M | 40.4 | 44 | 97 | 375 | +22.3 (18.9) [+16.1, +28.9] |
|  | HOLD | 37.1 | 49 | 97 | 142 | +20.0 (18.3) [+12.7, +27.1] |
|  | PRE | 18.8 | 55 | 293 | -932 | +3.3 (14.4) [-5.9, +14.4] |
|  | X' | 7.6 | 31 | 142 | -369 | +11.1 (14.7) [+2.8, +19.3] |
| D6 v2.3b, base-lot governors (Native 1.28) | L3M | 20.7 | 44 | 86 | 290 | +13.5 (26.2) [+3.4, +30.1] |
|  | L6M | 31.5 | 40 | 86 | 253 | +13.4 (17.0) [+4.6, +22.3] |
|  | HOLD | 29.6 | 44 | 86 | 63 | +12.5 (16.2) [+4.2, +20.7] |
|  | PRE | 15.6 | 45 | 239 | -774 | +0.1 (12.9) [-7.6, +9.1] |
|  | X' | 8.6 | 30 | 108 | -347 | +12.1 (14.6) [+3.9, +19.0] |
| D6 v2.3b as coded with the 2.45 join stop | L3M | 31.4 | 50 | 99 | 439 | +24.1 (28.2) [+12.9, +35.8] |
|  | L6M | 38.7 | 43 | 99 | 345 | +20.6 (19.2) [+14.0, +27.7] |
|  | HOLD | 35.4 | 49 | 99 | 113 | +18.3 (18.6) [+10.9, +25.9] |
|  | PRE | 16.6 | 55 | 314 | -985 | +1.1 (14.4) [-8.4, +12.3] |
|  | X' | 5.8 | 31 | 153 | -402 | +9.4 (14.7) [+1.2, +17.3] |
| D6 v2.3b, base-lot governors, 2.45 join stop | L3M | 15.2 | 46 | 87 | 212 | +7.9 (27.8) [-0.8, +26.1] |
|  | L6M | 28.0 | 41 | 87 | 172 | +9.9 (17.6) [+1.5, +18.9] |
|  | HOLD | 26.4 | 45 | 87 | -11 | +9.3 (16.8) [+1.5, +17.8] |
|  | PRE | 13.9 | 45 | 243 | -816 | -1.6 (13.0) [-9.5, +7.4] |
|  | X' | 7.2 | 30 | 113 | -380 | +10.7 (14.7) [+2.6, +17.6] |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)

| config | window | mean $k/wk | SD | maxDD | worst-20 (sum $k) | delta vs as-is $k/wk (MDE) [week-block 95% CI] |
|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | L3M | 12.1 | 74 | 162 | 169 | - |
|  | L6M | 28.5 | 70 | 162 | -33 | - |
|  | HOLD | 23.4 | 85 | 316 | -495 | - |
|  | PRE | 22.4 | 67 | 432 | -1212 | - |
|  | X' | -0.4 | 50 | 360 | -894 | - |
| D6 v2.3b as coded (sized-lot governors, Native 1.28) | L3M | 57.3 | 71 | 163 | 802 | +45.3 (42.5) [+27.9, +65.5] |
|  | L6M | 64.4 | 65 | 163 | 643 | +35.9 (27.7) [+21.1, +49.7] |
|  | HOLD | 57.0 | 81 | 199 | 210 | +33.6 (26.3) [+21.3, +46.9] |
|  | PRE | 37.1 | 78 | 282 | -1026 | +14.7 (19.2) [+3.9, +28.9] |
|  | X' | 9.1 | 53 | 279 | -752 | +9.5 (19.1) [-2.4, +19.5] |
| D6 v2.3b, base-lot governors (Native 1.28) | L3M | 45.9 | 53 | 119 | 642 | +33.8 (38.9) [+14.3, +55.0] |
|  | L6M | 54.4 | 57 | 119 | 574 | +25.9 (25.6) [+10.3, +39.6] |
|  | HOLD | 48.8 | 71 | 172 | 188 | +25.4 (24.0) [+12.6, +37.9] |
|  | PRE | 26.7 | 63 | 294 | -1029 | +4.4 (16.3) [-5.2, +15.4] |
|  | X' | 13.1 | 51 | 229 | -641 | +13.5 (19.9) [+1.2, +22.3] |
| D6 v2.3b as coded with the 2.45 join stop | L3M | 52.9 | 72 | 175 | 741 | +40.9 (42.1) [+24.0, +61.3] |
|  | L6M | 59.4 | 65 | 175 | 537 | +30.8 (28.6) [+14.6, +45.4] |
|  | HOLD | 52.2 | 81 | 207 | 114 | +28.9 (27.0) [+15.7, +42.7] |
|  | PRE | 32.2 | 76 | 306 | -1109 | +9.8 (18.6) [-0.4, +22.8] |
|  | X' | 6.1 | 53 | 313 | -821 | +6.5 (19.1) [-5.3, +16.4] |
| D6 v2.3b, base-lot governors, 2.45 join stop | L3M | 41.4 | 54 | 118 | 580 | +29.3 (39.5) [+10.8, +50.5] |
|  | L6M | 51.1 | 59 | 118 | 497 | +22.6 (25.9) [+7.5, +36.5] |
|  | HOLD | 45.6 | 72 | 179 | 112 | +22.2 (24.2) [+9.9, +34.5] |
|  | PRE | 22.6 | 62 | 312 | -1120 | +0.2 (16.1) [-9.5, +10.8] |
|  | X' | 10.3 | 52 | 246 | -703 | +10.8 (19.7) [-1.8, +19.5] |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

| config | window | mean $k/wk | SD | maxDD | worst-20 (sum $k) | delta vs as-is $k/wk (MDE) [week-block 95% CI] |
|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | L3M | -1.0 | 141 | 417 | -14 | - |
|  | L6M | 50.0 | 145 | 417 | -372 | - |
|  | HOLD | 37.2 | 173 | 684 | -1321 | - |
|  | PRE | 46.1 | 137 | 778 | -2620 | - |
|  | X' | 7.0 | 104 | 560 | -1661 | - |
| D6 v2.3b as coded (sized-lot governors, Native 1.28) | L3M | 99.2 | 158 | 464 | 1389 | +100.2 (77.7) [+54.4, +154.1] |
|  | L6M | 132.8 | 145 | 464 | 1324 | +82.8 (51.7) [+42.9, +118.8] |
|  | HOLD | 113.3 | 172 | 464 | 278 | +76.1 (50.7) [+44.7, +111.8] |
|  | PRE | 73.1 | 156 | 488 | -2222 | +27.0 (33.3) [+9.9, +47.9] |
|  | X' | 20.0 | 107 | 608 | -1432 | +13.0 (34.6) [-7.2, +32.2] |
| D6 v2.3b, base-lot governors (Native 1.28) | L3M | 70.5 | 110 | 323 | 987 | +71.5 (63.1) [+36.4, +109.3] |
|  | L6M | 95.7 | 120 | 323 | 832 | +45.7 (50.6) [+2.3, +78.7] |
|  | HOLD | 82.1 | 142 | 382 | 29 | +44.9 (48.7) [+6.0, +76.3] |
|  | PRE | 51.7 | 130 | 612 | -2277 | +5.6 (29.3) [-10.6, +23.6] |
|  | X' | 29.0 | 103 | 498 | -1196 | +21.9 (36.3) [-1.9, +40.2] |
| D6 v2.3b as coded with the 2.45 join stop | L3M | 89.2 | 158 | 486 | 1248 | +90.2 (77.6) [+45.3, +144.0] |
|  | L6M | 121.1 | 144 | 486 | 1127 | +71.1 (53.6) [+29.1, +107.6] |
|  | HOLD | 102.3 | 171 | 486 | 118 | +65.1 (52.1) [+31.7, +101.9] |
|  | PRE | 63.4 | 156 | 515 | -2420 | +17.2 (32.6) [+0.8, +37.5] |
|  | X' | 13.7 | 107 | 649 | -1572 | +6.7 (34.5) [-13.4, +25.5] |
| D6 v2.3b, base-lot governors, 2.45 join stop | L3M | 61.0 | 110 | 322 | 855 | +62.1 (62.1) [+31.0, +99.5] |
|  | L6M | 88.0 | 123 | 322 | 648 | +38.0 (50.7) [-4.7, +72.6] |
|  | HOLD | 74.7 | 144 | 397 | -166 | +37.5 (48.9) [-1.1, +70.2] |
|  | PRE | 43.2 | 131 | 691 | -2502 | -3.0 (29.3) [-19.3, +14.2] |
|  | X' | 23.6 | 104 | 535 | -1306 | +16.6 (36.2) [-7.2, +35.0] |

## 2. Leave-one-out and each piece alone
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

Contribution of the piece = FULL(as coded) minus FULL-without-the-piece; alone = the piece on the as-is stack. $k/wk, (MDE of the paired weekly delta). Without (6) the stop is the 2.45 join; without (1) the PE confirmation enters at market with the whole lot (no split).

| piece | view | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +0.0 (16.1) | +0.4 (9.2) | +0.5 (8.2) | -0.4 (3.8) | +3.5 (3.5) |
| | left out of FULL (sized gov) | +6.5 (7.0) | +2.6 (4.3) | +2.4 (4.0) | +1.2 (2.8) | +1.2 (2.5) |
| | left out of FULL (base gov) | -0.3 (9.6) | -0.3 (5.1) | +0.0 (4.5) | -0.7 (3.0) | +1.9 (2.5) |
| (2) PE 45-s three-bar confirmation NY-AM/NY-PM | alone vs as-is | +3.3 (7.5) | +4.0 (6.4) | +3.5 (5.8) | +0.9 (3.6) | +1.3 (5.1) |
| | left out of FULL (sized gov) | +7.4 (15.1) | +3.3 (9.0) | +4.0 (8.4) | -1.6 (6.7) | +0.0 (5.9) |
| | left out of FULL (base gov) | +2.7 (9.6) | +0.7 (5.8) | +1.5 (5.7) | +0.3 (5.3) | -0.6 (5.2) |
| (3) ER(20) 5m x1.5/x0.5 + sized governors | alone vs as-is | +10.4 (23.2) | +11.6 (13.1) | +10.5 (12.2) | -2.9 (13.3) | +3.8 (13.8) |
| | left out of FULL (sized gov) | +16.4 (28.8) | +13.7 (15.9) | +12.5 (14.7) | +0.6 (10.7) | +0.2 (8.6) |
| | left out of FULL (base gov) | +4.0 (21.2) | +4.8 (11.9) | +5.1 (10.7) | -2.6 (8.3) | +1.2 (9.2) |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +0.0 (9.8) | +1.1 (6.7) | +0.7 (6.0) | -0.5 (3.2) | +1.8 (3.9) |
| | left out of FULL (sized gov) | -1.3 (6.5) | -1.1 (3.5) | -1.6 (3.4) | -0.9 (1.7) | +0.7 (1.7) |
| | left out of FULL (base gov) | +4.3 (13.4) | +1.3 (6.9) | +1.1 (6.1) | +0.0 (2.5) | +0.8 (1.3) |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | +0.8 (13.7) | +5.3 (11.3) | +4.7 (11.8) | +0.1 (8.2) | +6.1 (9.0) |
| | left out of FULL (sized gov) | +1.7 (14.3) | +1.3 (9.6) | +0.4 (10.0) | +2.7 (8.1) | +3.1 (8.2) |
| | left out of FULL (base gov) | -1.8 (13.6) | -1.3 (9.1) | -2.7 (9.7) | +1.8 (9.0) | +4.6 (9.5) |
| (6) Native stops 1.28 | alone vs as-is | +2.4 (0.7) | +2.5 (0.6) | +2.5 (0.5) | +2.5 (0.5) | +2.1 (0.4) |
| | left out of FULL (sized gov) | +1.7 (1.7) | +1.7 (1.3) | +1.7 (1.1) | +2.2 (0.5) | +1.8 (0.5) |
| | left out of FULL (base gov) | +5.6 (6.0) | +3.5 (3.2) | +3.2 (2.8) | +1.7 (0.7) | +1.4 (0.3) |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)

Contribution of the piece = FULL(as coded) minus FULL-without-the-piece; alone = the piece on the as-is stack. $k/wk, (MDE of the paired weekly delta). Without (6) the stop is the 2.45 join; without (1) the PE confirmation enters at market with the whole lot (no split).

| piece | view | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +4.2 (16.5) | +4.6 (9.8) | +4.7 (8.7) | +0.9 (4.9) | +2.9 (4.6) |
| | left out of FULL (sized gov) | +9.4 (8.2) | +6.3 (5.2) | +5.9 (4.6) | +4.8 (4.7) | +0.6 (3.2) |
| | left out of FULL (base gov) | +1.7 (15.7) | +2.9 (8.6) | +2.8 (7.5) | +0.9 (5.2) | +2.3 (3.6) |
| (2) PE 45-s three-bar confirmation NY-AM/NY-PM | alone vs as-is | +3.3 (7.5) | +4.0 (6.4) | +3.5 (5.8) | +0.9 (3.6) | +1.3 (5.1) |
| | left out of FULL (sized gov) | +9.2 (14.8) | +3.5 (9.6) | +4.2 (8.9) | -1.8 (6.9) | +0.1 (5.9) |
| | left out of FULL (base gov) | +3.0 (8.2) | +1.8 (5.8) | +2.5 (5.6) | +0.7 (5.4) | -0.6 (5.2) |
| (3) ER(20) 5m x1.5/x0.5 + sized governors | alone vs as-is | +23.4 (35.7) | +20.8 (21.7) | +19.2 (20.4) | +1.6 (17.2) | +2.4 (17.8) |
| | left out of FULL (sized gov) | +17.6 (43.0) | +15.8 (24.2) | +15.5 (22.5) | +7.7 (13.6) | +0.2 (11.3) |
| | left out of FULL (base gov) | +6.2 (31.0) | +5.8 (20.1) | +7.4 (18.1) | -2.7 (11.7) | +4.2 (12.1) |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +8.2 (17.7) | +7.0 (12.8) | +7.0 (11.5) | -1.4 (7.0) | +1.9 (7.0) |
| | left out of FULL (sized gov) | +2.3 (14.5) | -1.7 (9.1) | -1.7 (8.4) | +0.3 (4.2) | -1.3 (3.7) |
| | left out of FULL (base gov) | +10.9 (12.7) | +4.7 (8.9) | +4.4 (7.8) | +0.6 (4.9) | +0.2 (3.8) |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | +4.2 (14.8) | +5.2 (12.6) | +5.0 (13.7) | +2.6 (9.8) | +5.5 (11.4) |
| | left out of FULL (sized gov) | +6.9 (17.5) | +1.8 (12.4) | +0.3 (12.8) | +4.5 (9.8) | +2.7 (10.8) |
| | left out of FULL (base gov) | +2.0 (25.5) | +0.8 (16.2) | -0.9 (15.4) | +2.0 (10.1) | +5.1 (11.1) |
| (6) Native stops 1.28 | alone vs as-is | +4.5 (2.0) | +4.4 (1.6) | +4.3 (1.5) | +4.4 (1.6) | +3.3 (0.5) |
| | left out of FULL (sized gov) | +4.4 (1.4) | +5.0 (3.0) | +4.7 (2.6) | +4.9 (2.5) | +3.0 (0.6) |
| | left out of FULL (base gov) | +4.5 (4.3) | +3.3 (2.3) | +3.2 (2.0) | +4.1 (2.0) | +2.7 (1.1) |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

Contribution of the piece = FULL(as coded) minus FULL-without-the-piece; alone = the piece on the as-is stack. $k/wk, (MDE of the paired weekly delta). Without (6) the stop is the 2.45 join; without (1) the PE confirmation enters at market with the whole lot (no split).

| piece | view | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +16.1 (24.4) | +15.1 (15.8) | +16.0 (14.7) | +3.8 (11.2) | +2.5 (8.4) |
| | left out of FULL (sized gov) | +11.0 (13.0) | +10.7 (8.7) | +10.4 (7.7) | +9.7 (8.7) | +1.1 (5.5) |
| | left out of FULL (base gov) | +2.6 (26.9) | +4.0 (16.7) | +3.8 (14.7) | +3.5 (9.2) | +2.4 (6.6) |
| (2) PE 45-s three-bar confirmation NY-AM/NY-PM | alone vs as-is | +7.0 (7.5) | +4.6 (5.8) | +4.3 (5.4) | +0.5 (3.6) | +0.7 (5.3) |
| | left out of FULL (sized gov) | +9.9 (12.8) | +4.5 (9.2) | +5.7 (8.4) | -0.5 (5.8) | -2.1 (6.8) |
| | left out of FULL (base gov) | +2.4 (6.3) | +1.3 (5.7) | +2.5 (5.4) | -0.2 (5.1) | -3.5 (5.7) |
| (3) ER(20) 5m x1.5/x0.5 + sized governors | alone vs as-is | +61.5 (90.7) | +47.4 (56.8) | +40.8 (52.5) | +5.0 (29.8) | +3.6 (32.8) |
| | left out of FULL (sized gov) | +14.8 (88.2) | +26.6 (52.6) | +25.1 (47.6) | +12.5 (26.4) | +4.5 (21.7) |
| | left out of FULL (base gov) | -13.9 (57.0) | -10.5 (42.2) | -6.1 (37.8) | -8.9 (25.8) | +13.4 (22.6) |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +15.3 (30.6) | +17.7 (21.8) | +14.6 (19.7) | -0.0 (11.9) | +3.5 (13.9) |
| | left out of FULL (sized gov) | +14.8 (26.9) | +4.7 (16.7) | +3.5 (15.5) | -1.6 (6.3) | -1.9 (5.8) |
| | left out of FULL (base gov) | +15.5 (17.5) | +5.1 (14.0) | +4.9 (12.2) | -2.4 (8.0) | -1.0 (6.4) |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | +39.4 (34.4) | +22.4 (29.2) | +19.4 (30.5) | +3.3 (18.9) | +7.0 (21.7) |
| | left out of FULL (sized gov) | +27.7 (43.9) | +15.7 (29.0) | +12.5 (29.4) | +5.1 (18.3) | +1.3 (22.1) |
| | left out of FULL (base gov) | +11.6 (48.1) | +9.3 (30.8) | +6.2 (29.5) | +1.4 (17.9) | +4.7 (22.2) |
| (6) Native stops 1.28 | alone vs as-is | +9.4 (4.8) | +9.4 (4.0) | +9.1 (3.6) | +9.8 (3.7) | +7.1 (1.2) |
| | left out of FULL (sized gov) | +10.0 (4.0) | +11.7 (6.7) | +11.0 (5.9) | +9.8 (2.6) | +6.3 (1.4) |
| | left out of FULL (base gov) | +9.4 (10.8) | +7.7 (5.9) | +7.4 (5.2) | +8.5 (3.5) | +5.4 (1.5) |

## 3. Per-session tables (entry session)
Sessions are the research tags (asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-15:15 ET). Rows sum to the totals of section 1 (checked).
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

| session (research tag) | window | as-is $k/wk | D6 v2.3b $k/wk | delta | trades/wk as-is | trades/wk D6 |
|---|---|---|---|---|---|---|
| asia | L3M | 2.2 | 17.8 | +15.5 | 35.3 | 32.9 |
| asia | L6M | 10.6 | 21.1 | +10.4 | 32.1 | 28.0 |
| asia | HOLD | 8.9 | 19.2 | +10.3 | 31.6 | 26.7 |
| asia | PRE | 9.7 | 10.5 | +0.8 | 29.5 | 24.2 |
| asia | X' | -4.6 | 3.6 | +8.1 | 19.5 | 11.4 |
| london | L3M | 8.7 | 5.0 | -3.7 | 11.5 | 17.0 |
| london | L6M | 7.2 | 7.7 | +0.5 | 11.7 | 14.1 |
| london | HOLD | 8.3 | 7.8 | -0.5 | 11.6 | 13.4 |
| london | PRE | -0.0 | -0.8 | -0.8 | 12.8 | 13.9 |
| london | X' | 0.5 | 1.2 | +0.7 | 8.6 | 7.0 |
| pre | L3M | -3.1 | -0.6 | +2.5 | 2.4 | 4.1 |
| pre | L6M | 0.1 | 0.5 | +0.3 | 2.6 | 3.8 |
| pre | HOLD | -1.1 | -0.6 | +0.5 | 2.6 | 3.6 |
| pre | PRE | 0.1 | -0.7 | -0.7 | 3.4 | 4.1 |
| pre | X' | 0.0 | -0.2 | -0.3 | 3.1 | 2.8 |
| nyam | L3M | 0.3 | 10.2 | +9.9 | 14.6 | 22.1 |
| nyam | L6M | 0.4 | 10.6 | +10.2 | 15.5 | 20.9 |
| nyam | HOLD | 1.2 | 10.1 | +8.9 | 15.5 | 20.2 |
| nyam | PRE | 5.3 | 9.6 | +4.4 | 15.9 | 19.1 |
| nyam | X' | 0.4 | 3.1 | +2.8 | 15.8 | 15.0 |
| nypm | L3M | -1.0 | 0.6 | +1.7 | 0.6 | 4.6 |
| nypm | L6M | -0.2 | 0.6 | +0.8 | 2.1 | 4.9 |
| nypm | HOLD | -0.1 | 0.7 | +0.8 | 2.0 | 4.6 |
| nypm | PRE | 0.5 | 0.2 | -0.3 | 2.4 | 4.7 |
| nypm | X' | 0.1 | -0.0 | -0.1 | 2.7 | 3.9 |
| close | L6M | -0.0 | -0.0 | -0.0 | 0.0 | 0.0 |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)

| session (research tag) | window | as-is $k/wk | D6 v2.3b $k/wk | delta | trades/wk as-is | trades/wk D6 |
|---|---|---|---|---|---|---|
| asia | L3M | 3.5 | 31.9 | +28.5 | 61.8 | 60.4 |
| asia | L6M | 15.0 | 30.6 | +15.6 | 56.4 | 50.7 |
| asia | HOLD | 10.1 | 25.5 | +15.4 | 55.4 | 48.6 |
| asia | PRE | 13.4 | 19.3 | +5.9 | 51.2 | 43.2 |
| asia | X' | -3.8 | 3.5 | +7.4 | 32.3 | 19.6 |
| london | L3M | 11.0 | 4.6 | -6.5 | 23.4 | 36.0 |
| london | L6M | 11.0 | 10.7 | -0.2 | 24.0 | 30.9 |
| london | HOLD | 11.7 | 11.7 | -0.0 | 23.6 | 29.5 |
| london | PRE | 0.2 | 0.5 | +0.3 | 25.5 | 30.3 |
| london | X' | 2.2 | 2.6 | +0.3 | 17.8 | 15.4 |
| pre | L3M | -5.6 | 1.3 | +6.9 | 5.1 | 9.5 |
| pre | L6M | -2.1 | 0.6 | +2.7 | 5.2 | 8.2 |
| pre | HOLD | -3.9 | -1.1 | +2.8 | 5.2 | 7.9 |
| pre | PRE | 0.5 | -0.2 | -0.6 | 6.3 | 8.6 |
| pre | X' | -0.3 | 0.5 | +0.8 | 6.2 | 5.9 |
| nyam | L3M | 6.4 | 19.6 | +13.1 | 23.4 | 45.6 |
| nyam | L6M | 5.8 | 19.7 | +13.8 | 25.7 | 43.0 |
| nyam | HOLD | 6.7 | 18.3 | +11.6 | 25.8 | 42.1 |
| nyam | PRE | 8.1 | 14.8 | +6.7 | 26.4 | 38.1 |
| nyam | X' | 0.1 | 1.8 | +1.7 | 27.5 | 29.7 |
| nypm | L3M | -3.3 | -0.1 | +3.2 | 3.4 | 15.8 |
| nypm | L6M | -1.1 | 2.9 | +4.0 | 6.1 | 16.0 |
| nypm | HOLD | -1.1 | 2.6 | +3.8 | 6.0 | 15.6 |
| nypm | PRE | 0.2 | 2.9 | +2.7 | 7.1 | 16.5 |
| nypm | X' | 1.4 | 0.5 | -0.9 | 9.2 | 13.4 |
| close | L6M | -0.0 | -0.0 | +0.0 | 0.0 | 0.1 |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

| session (research tag) | window | as-is $k/wk | D6 v2.3b $k/wk | delta | trades/wk as-is | trades/wk D6 |
|---|---|---|---|---|---|---|
| asia | L3M | 14.5 | 63.5 | +49.0 | 61.8 | 60.4 |
| asia | L6M | 27.4 | 56.7 | +29.3 | 56.4 | 50.7 |
| asia | HOLD | 17.1 | 45.7 | +28.5 | 55.4 | 48.6 |
| asia | PRE | 24.2 | 34.3 | +10.1 | 51.2 | 43.2 |
| asia | X' | -3.5 | 6.8 | +10.3 | 32.3 | 19.6 |
| london | L3M | 7.8 | -0.7 | -8.5 | 27.6 | 42.3 |
| london | L6M | 18.6 | 23.3 | +4.7 | 28.5 | 36.5 |
| london | HOLD | 19.2 | 22.9 | +3.7 | 28.0 | 34.8 |
| london | PRE | 3.5 | 5.6 | +2.1 | 30.4 | 35.1 |
| london | X' | 9.5 | 10.2 | +0.7 | 20.5 | 17.5 |
| pre | L3M | -10.5 | 2.7 | +13.3 | 5.4 | 10.5 |
| pre | L6M | -6.4 | 0.5 | +6.9 | 5.8 | 9.2 |
| pre | HOLD | -10.1 | -2.1 | +8.0 | 5.9 | 8.9 |
| pre | PRE | -0.1 | -3.0 | -2.9 | 7.3 | 10.2 |
| pre | X' | -2.5 | 1.0 | +3.6 | 7.2 | 6.8 |
| nyam | L3M | 3.7 | 37.6 | +33.9 | 22.8 | 46.9 |
| nyam | L6M | 13.8 | 42.6 | +28.8 | 26.0 | 44.6 |
| nyam | HOLD | 15.5 | 39.5 | +24.0 | 26.2 | 43.8 |
| nyam | PRE | 17.9 | 31.6 | +13.7 | 26.4 | 40.1 |
| nyam | X' | 1.9 | 2.6 | +0.8 | 28.6 | 31.5 |
| nypm | L3M | -15.6 | -3.1 | +12.5 | 6.5 | 23.7 |
| nypm | L6M | -2.8 | 10.8 | +13.6 | 10.4 | 24.5 |
| nypm | HOLD | -3.7 | 8.7 | +12.3 | 10.4 | 23.7 |
| nypm | PRE | 0.8 | 5.0 | +4.2 | 12.7 | 26.1 |
| nypm | X' | 1.5 | -1.1 | -2.6 | 15.8 | 20.8 |
| close | L6M | -0.5 | -1.0 | -0.5 | 0.1 | 0.1 |

#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

Per-session $k/wk contribution of each piece (FULL - FULL-without-the-piece, sized governors), research session tags.

| piece | window | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | L6M | +0.5 | +1.0 | +0.2 | +0.8 | +0.1 | +0.0 |
|  | HOLD | +0.8 | +1.0 | +0.2 | +0.4 | +0.0 | +0.0 |
|  | PRE | -0.0 | +0.3 | +0.2 | +0.8 | +0.1 | +0.0 |
| (2) PE 45-s three-bar confirmation NY-AM/NY-PM | L6M | +0.0 | +0.0 | +0.0 | +3.3 | +0.0 | +0.0 |
|  | HOLD | +0.0 | +0.0 | +0.0 | +4.0 | +0.0 | +0.0 |
|  | PRE | +0.0 | +0.1 | -0.1 | -1.6 | +0.0 | +0.0 |
| (3) ER(20) 5m x1.5/x0.5 + sized governors | L6M | +5.5 | +2.1 | +1.1 | +5.0 | +0.0 | -0.0 |
|  | HOLD | +5.7 | +1.8 | +0.9 | +4.0 | +0.1 | -0.0 |
|  | PRE | -0.5 | -1.4 | -0.4 | +3.2 | -0.4 | -0.0 |
| (4) Asia-stopped -> cut other same-side 50% | L6M | -0.1 | -0.2 | -1.2 | +0.6 | -0.2 | +0.0 |
|  | HOLD | +0.1 | -0.4 | -1.1 | -0.0 | -0.2 | +0.0 |
|  | PRE | -0.3 | -0.4 | +0.1 | -0.3 | -0.0 | +0.0 |
| (5) no-trade set (8 lines, D 20, fresh) | L6M | -0.4 | +0.7 | +0.5 | +0.8 | -0.1 | +0.0 |
|  | HOLD | -1.7 | +0.4 | +0.8 | +0.7 | +0.2 | +0.0 |
|  | PRE | +1.2 | +0.4 | +0.5 | +0.3 | +0.3 | +0.0 |
| (6) Native stops 1.28 | L6M | +0.9 | +0.7 | -0.6 | +0.5 | +0.1 | +0.0 |
|  | HOLD | +0.9 | +0.6 | -0.5 | +0.5 | +0.1 | +0.0 |
|  | PRE | +0.8 | +0.6 | +0.3 | +0.4 | +0.1 | +0.0 |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

Per-session $k/wk contribution of each piece (FULL - FULL-without-the-piece, sized governors), research session tags.

| piece | window | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | L6M | +3.4 | +2.0 | +0.1 | +0.8 | +4.4 | -0.0 |
|  | HOLD | +3.6 | +1.8 | +0.2 | +0.1 | +4.8 | -0.0 |
|  | PRE | +0.9 | +2.8 | +0.8 | +3.6 | +1.5 | -0.0 |
| (2) PE 45-s three-bar confirmation NY-AM/NY-PM | L6M | +0.0 | -0.1 | +0.0 | +2.9 | +1.7 | +0.0 |
|  | HOLD | +0.0 | -0.1 | +0.0 | +3.5 | +2.3 | +0.0 |
|  | PRE | -0.0 | +0.0 | +0.0 | -1.3 | +0.7 | +0.1 |
| (3) ER(20) 5m x1.5/x0.5 + sized governors | L6M | +10.7 | -5.0 | +6.8 | +5.5 | +9.1 | -0.6 |
|  | HOLD | +11.5 | -3.5 | +7.1 | +3.2 | +7.5 | -0.7 |
|  | PRE | +5.4 | -4.0 | -2.7 | +10.5 | +3.4 | -0.2 |
| (4) Asia-stopped -> cut other same-side 50% | L6M | -0.5 | +0.1 | -0.4 | +5.1 | +0.4 | -0.0 |
|  | HOLD | -0.3 | -0.0 | -0.3 | +4.0 | +0.2 | -0.0 |
|  | PRE | +0.3 | -0.2 | -0.8 | +0.1 | -1.1 | +0.1 |
| (5) no-trade set (8 lines, D 20, fresh) | L6M | -1.0 | +2.0 | +2.4 | +8.4 | +3.1 | +0.8 |
|  | HOLD | -4.6 | +2.5 | +2.9 | +6.7 | +4.3 | +0.7 |
|  | PRE | +2.5 | +0.7 | +1.3 | -1.9 | +2.3 | +0.2 |
| (6) Native stops 1.28 | L6M | +2.3 | +3.6 | -0.3 | +3.9 | +2.1 | +0.0 |
|  | HOLD | +2.3 | +3.3 | -0.2 | +3.6 | +1.9 | +0.0 |
|  | PRE | +2.6 | +2.7 | +1.0 | +2.1 | +1.5 | +0.0 |

## 4. Per-book table
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

| book | window | as-is $k/wk | D6 v2.3b $k/wk | delta |
|---|---|---|---|---|
| HM | L3M | 7.0 | 11.5 | +4.5 |
| HM | L6M | 5.4 | 9.8 | +4.4 |
| HM | HOLD | 4.9 | 8.7 | +3.8 |
| HM | PRE | 2.7 | 2.9 | +0.2 |
| HM | X' | -0.8 | -0.4 | +0.4 |
| KB | L3M | -2.4 | 3.0 | +5.4 |
| KB | L6M | 2.8 | 5.6 | +2.7 |
| KB | HOLD | 2.1 | 4.3 | +2.2 |
| KB | PRE | 3.9 | 3.8 | -0.1 |
| KB | X' | -0.5 | 1.0 | +1.5 |
| SM | L3M | -0.3 | -1.1 | -0.8 |
| SM | L6M | 0.8 | 0.9 | +0.1 |
| SM | HOLD | 1.1 | 1.3 | +0.2 |
| SM | PRE | 2.3 | 2.6 | +0.2 |
| SM | X' | 0.9 | 2.1 | +1.2 |
| PE | L3M | 2.9 | 19.7 | +16.8 |
| PE | L6M | 9.0 | 24.1 | +15.1 |
| PE | HOLD | 9.1 | 22.8 | +13.7 |
| PE | PRE | 6.5 | 9.6 | +3.1 |
| PE | X' | -3.1 | 4.9 | +8.0 |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

| book | window | as-is $k/wk | D6 v2.3b $k/wk | delta |
|---|---|---|---|---|
| ST | L3M | 8.7 | 38.1 | +29.4 |
| ST | L6M | 18.3 | 44.3 | +26.0 |
| ST | HOLD | 10.6 | 38.1 | +27.6 |
| ST | PRE | 15.3 | 26.8 | +11.4 |
| ST | X' | 7.4 | 4.6 | -2.9 |
| HM | L3M | -7.4 | 21.1 | +28.5 |
| HM | L6M | 9.8 | 38.6 | +28.8 |
| HM | HOLD | 6.8 | 30.8 | +24.0 |
| HM | PRE | 7.1 | 9.3 | +2.2 |
| HM | X' | 2.2 | 4.0 | +1.8 |
| WT | L3M | 2.6 | 18.7 | +16.0 |
| WT | L6M | 6.2 | 16.1 | +9.9 |
| WT | HOLD | 4.1 | 12.0 | +7.9 |
| WT | PRE | 0.8 | 11.2 | +10.4 |
| WT | X' | -0.2 | 2.9 | +3.1 |
| KB | L3M | -6.1 | 8.5 | +14.6 |
| KB | L6M | 7.4 | 15.3 | +7.9 |
| KB | HOLD | 5.4 | 11.9 | +6.5 |
| KB | PRE | 10.2 | 9.3 | -0.8 |
| KB | X' | -1.4 | 2.3 | +3.7 |
| SM | L3M | 3.1 | 0.1 | -3.0 |
| SM | L6M | 2.0 | 2.2 | +0.2 |
| SM | HOLD | 4.2 | 5.0 | +0.8 |
| SM | PRE | 6.2 | 5.6 | -0.6 |
| SM | X' | 1.7 | 3.3 | +1.6 |
| PE | L3M | -1.9 | 12.8 | +14.7 |
| PE | L6M | 6.3 | 16.3 | +9.9 |
| PE | HOLD | 6.1 | 15.5 | +9.4 |
| PE | PRE | 6.5 | 10.9 | +4.5 |
| PE | X' | -2.7 | 3.0 | +5.7 |

## 5. QUANT-LAYER one-page header for the composite (D6 v2.3b as coded, sized governors, Native stops; delta vs the stack as it is)
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

| column | value |
|---|---|
| per-contract pts after all costs: D6 / as-is / delta [week-block CI] L6M | 7.54 / 3.50 / +4.04 [+2.45, +5.67] |
|   same HOLD / PRE / X' | HOLD +3.86 [+2.40, +5.51]; PRE +0.77 [-1.02, +3.04]; X' +3.35 [+0.99, +5.39] |
| costs inside the points | commission+fee 0.242 pt RT per lot, entry slip 1 tick on market fills, stop cost 1.28 (Native; 2.45 join in the _join_ rows), target-fill correction 0 (basis N; M and LIVE-P9 target-fill bases not re-run for the composite), 0.995 on time exits and cuts |
| delta $k/wk L3M / L6M / HOLD / PRE / X'  | +25.8 / +22.3 / +20.0 / +3.3 / +11.1 |
| MDE (2.8 SE) same windows | 27.4 / 18.9 / 18.3 / 14.4 / 14.7 |
| trades per week D6 / as-is (L6M, HOLD, PRE, X') | 72 / 64 ; 68 / 63 ; 66 / 64 ; 40 / 50 |
| fire rates | PE confirmation 55-59% (nyam) / 68-70% (nypm) of PE signals; zone skip 15.1% of all signals (12.2% L6M); ER >= 0.30 on 39%; Asia-stopped cut 2.6 a week at live lots / 4.1 at research lots (149 weeks) |
| 1 of N cells | 1 of 1 coded composite (the six pieces are fixed by the directive); program cells for RC/RW = 14 (the composite, its base-governor twin, 6 alone, 6 leave-one-out); cumulative 2,467,648 trials in UF_TRIALS (cited by the split report) |
| White RC p over the 14 cells (best cell; dominated by Native stops, a constant) | L6M 0.000 / HOLD 0.000 / PRE 0.000 / X' 0.000 |
| Romano-Wolf adjusted p of the composite (stepdown over the 14) | L6M 0.002 / HOLD 0.002 / PRE 0.789 / X' 0.051; survivors at 5%: 9 / 9 / 1 / 5 |
| cumulative-count adjusted (x 2,467,648) | p = 1.00 in every window (Bonferroni bound; not PASS) |
| DSR (weekly delta; N=14 / N=2,467,648) L6M / ALL | 0.235 / 3e-16 ; 0.000 / 5e-134 |
| PBO (CSCV, 10 blocks, 14 cells / without the constant Native-stop cell) | 0.00 / 0.45 |
| neighbourhood mean (+-25% / +-50%) L6M / HOLD / PRE | see section 6 |
| breakeven extra cost per lot (L6M / HOLD / PRE / X') | 3.9 / 3.8 / 0.7 / 3.6 |
| capacity (contracts the fills could absorb) | NOT measured: mbp-10 depth is not joined to the PE confirm / cut seconds. Largest single D6 entry at live lots: PE 7 x1.5 = 10.5 (+ the add, up to 2x risk-capped) = flagged as at-risk (< 10-contract depth not excluded) |
| top-5% share of the gain (rows / weeks), L6M / HOLD / PRE | L6M rows 3.7x weeks 15% ; HOLD rows 4.0x weeks 15% ; PRE rows 21.6x weeks 144%  (a row share above 100% means the 5% biggest row deltas exceed the net delta: the gain is a few large days offset by many small negative rows) |
| stack correlation of the weekly delta with the as-is stack (L6M / HOLD / PRE / all) | -0.43 / -0.44 / -0.32 / -0.38 |
| weekly Sharpe as-is -> D6 (L6M / HOLD / PRE / X' / all) | 0.40 -> 0.93 / 0.33 -> 0.76 / 0.32 -> 0.34 / -0.11 -> 0.25 / 0.23 -> 0.40 |
| Newey-West t (4 lags) of the weekly delta L6M / HOLD / PRE / X' / all | 6.3 / 5.3 / 0.6 / 2.7 / 2.9; lag-1 autocorrelation of the weekly delta -0.35 / -0.28 / 0.01 / 0.01 / -0.01 |
| drift: quarters with a positive delta (12 quarters 2023Q2..2026Q1) | 9 of 12; first half vs second half of L6M +20.3k / +24.2k, of HOLD +16.7k / +23.3k |
| regime it works in | sessions asia, nyam (section 3); entry-day vol tercile 2 (high) in L6M/HOLD (section 7), not in PRE |
| plain sentence | see section 0 |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

| column | value |
|---|---|
| per-contract pts after all costs: D6 / as-is / delta [week-block CI] L6M | 5.96 / 2.64 / +3.32 [+0.95, +5.42] |
|   same HOLD / PRE / X' | HOLD +3.28 [+1.35, +5.33]; PRE +1.04 [+0.16, +2.05]; X' +1.01 [-0.43, +2.27] |
| costs inside the points | commission+fee 0.242 pt RT per lot, entry slip 1 tick on market fills, stop cost 1.28 (Native; 2.45 join in the _join_ rows), target-fill correction 0 (basis N; M and LIVE-P9 target-fill bases not re-run for the composite), 0.995 on time exits and cuts |
| delta $k/wk L3M / L6M / HOLD / PRE / X'  | +100.2 / +82.8 / +76.1 / +27.0 / +13.0 |
| MDE (2.8 SE) same windows | 77.7 / 51.7 / 50.7 / 33.3 / 34.6 |
| trades per week D6 / as-is (L6M, HOLD, PRE, X') | 166 / 127 ; 160 / 126 ; 155 / 128 ; 96 / 105 |
| fire rates | PE confirmation 55-59% (nyam) / 68-70% (nypm) of PE signals; zone skip 15.1% of all signals (12.2% L6M); ER >= 0.30 on 39%; Asia-stopped cut 2.6 a week at live lots / 4.1 at research lots (149 weeks) |
| 1 of N cells | 1 of 1 coded composite (the six pieces are fixed by the directive); program cells for RC/RW = 14 (the composite, its base-governor twin, 6 alone, 6 leave-one-out); cumulative 2,467,648 trials in UF_TRIALS (cited by the split report) |
| White RC p over the 14 cells (best cell; dominated by Native stops, a constant) | L6M 0.000 / HOLD 0.000 / PRE 0.000 / X' 0.000 |
| Romano-Wolf adjusted p of the composite (stepdown over the 14) | L6M 0.000 / HOLD 0.000 / PRE 0.092 / X' 0.412; survivors at 5%: 14 / 11 / 1 / 1 |
| cumulative-count adjusted (x 2,467,648) | p = 1.00 in every window (Bonferroni bound; not PASS) |
| DSR (weekly delta; N=14 / N=2,467,648) L6M / ALL | 0.993 / 0.07 ; 0.274 / 1e-22 |
| PBO (CSCV, 10 blocks, 14 cells / without the constant Native-stop cell) | 0.00 / 0.21 |
| neighbourhood mean (+-25% / +-50%) L6M / HOLD / PRE | see section 6 |
| breakeven extra cost per lot (L6M / HOLD / PRE / X') | 3.8 / 3.6 / 1.2 / 0.9 |
| capacity (contracts the fills could absorb) | NOT measured: mbp-10 depth is not joined to the PE confirm / cut seconds. Largest single D6 entry at live lots: PE 7 x1.5 = 10.5 (+ the add, up to 2x risk-capped) = flagged as at-risk (< 10-contract depth not excluded) |
| top-5% share of the gain (rows / weeks), L6M / HOLD / PRE | L6M rows 2.1x weeks 14% ; HOLD rows 2.2x weeks 14% ; PRE rows 5.5x weeks 41%  (a row share above 100% means the 5% biggest row deltas exceed the net delta: the gain is a few large days offset by many small negative rows) |
| stack correlation of the weekly delta with the as-is stack (L6M / HOLD / PRE / all) | -0.33 / -0.30 / -0.18 / -0.23 |
| weekly Sharpe as-is -> D6 (L6M / HOLD / PRE / X' / all) | 0.35 -> 0.92 / 0.22 -> 0.66 / 0.34 -> 0.47 / 0.07 -> 0.19 / 0.24 -> 0.44 |
| Newey-West t (4 lags) of the weekly delta L6M / HOLD / PRE / X' / all | 4.0 / 3.9 / 2.6 / 1.4 / 4.0; lag-1 autocorrelation of the weekly delta 0.21 / 0.21 / -0.04 / -0.05 / 0.08 |
| drift: quarters with a positive delta (12 quarters 2023Q2..2026Q1) | 11 of 12; first half vs second half of L6M +69.2k / +96.4k, of HOLD +72.6k / +79.6k |
| regime it works in | sessions asia, nyam (section 3); entry-day vol tercile 2 (high) in L6M/HOLD (section 7), not in PRE |
| plain sentence | see section 0 |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)

| column | value |
|---|---|
| per-contract pts after all costs: D6 / as-is / delta [week-block CI] L6M | 6.39 / 3.19 / +3.20 [+1.21, +4.96] |
|   same HOLD / PRE / X' | HOLD +3.20 [+1.61, +4.93]; PRE +1.42 [+0.26, +2.92]; X' +1.60 [-0.29, +3.11] |
| costs inside the points | commission+fee 0.242 pt RT per lot, entry slip 1 tick on market fills, stop cost 1.28 (Native; 2.45 join in the _join_ rows), target-fill correction 0 (basis N; M and LIVE-P9 target-fill bases not re-run for the composite), 0.995 on time exits and cuts |
| delta $k/wk L3M / L6M / HOLD / PRE / X'  | +45.3 / +35.9 / +33.6 / +14.7 / +9.5 |
| MDE (2.8 SE) same windows | 42.5 / 27.7 / 26.3 / 19.2 / 19.1 |
| trades per week D6 / as-is (L6M, HOLD, PRE, X') | 149 / 117 ; 144 / 116 ; 137 / 117 ; 84 / 93 |
| fire rates | PE confirmation 55-59% (nyam) / 68-70% (nypm) of PE signals; zone skip 15.1% of all signals (12.2% L6M); ER >= 0.30 on 39%; Asia-stopped cut 2.6 a week at live lots / 4.1 at research lots (149 weeks) |
| 1 of N cells | 1 of 1 coded composite (the six pieces are fixed by the directive); program cells for RC/RW = 14 (the composite, its base-governor twin, 6 alone, 6 leave-one-out); cumulative 2,467,648 trials in UF_TRIALS (cited by the split report) |
| White RC p over the 14 cells (best cell; dominated by Native stops, a constant) | L6M 0.000 / HOLD 0.000 / PRE 0.000 / X' 0.000 |
| Romano-Wolf adjusted p of the composite (stepdown over the 14) | L6M 0.001 / HOLD 0.000 / PRE 0.123 / X' 0.210; survivors at 5%: 10 / 10 / 1 / 1 |
| cumulative-count adjusted (x 2,467,648) | p = 1.00 in every window (Bonferroni bound; not PASS) |
| DSR (weekly delta; N=14 / N=2,467,648) L6M / ALL | 0.934 / 0.003 ; 0.125 / 2e-27 |
| PBO (CSCV, 10 blocks, 14 cells / without the constant Native-stop cell) | 0.00 / 0.13 |
| neighbourhood mean (+-25% / +-50%) L6M / HOLD / PRE | see section 6 |
| breakeven extra cost per lot (L6M / HOLD / PRE / X') | 3.6 / 3.5 / 1.5 / 1.6 |
| capacity (contracts the fills could absorb) | NOT measured: mbp-10 depth is not joined to the PE confirm / cut seconds. Largest single D6 entry at live lots: PE 7 x1.5 = 10.5 (+ the add, up to 2x risk-capped) = flagged as at-risk (< 10-contract depth not excluded) |
| top-5% share of the gain (rows / weeks), L6M / HOLD / PRE | L6M rows 2.6x weeks 14% ; HOLD rows 2.7x weeks 13% ; PRE rows 5.5x weeks 43%  (a row share above 100% means the 5% biggest row deltas exceed the net delta: the gain is a few large days offset by many small negative rows) |
| stack correlation of the weekly delta with the as-is stack (L6M / HOLD / PRE / all) | -0.47 / -0.39 / -0.25 / -0.29 |
| weekly Sharpe as-is -> D6 (L6M / HOLD / PRE / X' / all) | 0.40 -> 0.99 / 0.27 -> 0.70 / 0.33 -> 0.48 / -0.01 -> 0.17 / 0.24 -> 0.45 |
| Newey-West t (4 lags) of the weekly delta L6M / HOLD / PRE / X' / all | 4.6 / 4.7 / 2.2 / 1.9 / 4.1; lag-1 autocorrelation of the weekly delta -0.08 / -0.07 / 0.02 / 0.02 / 0.04 |
| drift: quarters with a positive delta (12 quarters 2023Q2..2026Q1) | 10 of 12; first half vs second half of L6M +27.7k / +44.1k, of HOLD +30.3k / +37.0k |
| regime it works in | sessions asia, nyam (section 3); entry-day vol tercile 2 (high) in L6M/HOLD (section 7), not in PRE |
| plain sentence | see section 0 |

## 6. Sensitivity (+-25% / +-50%), latency, breakeven cost
#### LIVE lots, engine books only (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM; ST, WT 0)

delta vs the stack as it is, $k/wk (L3M | L6M | HOLD | PRE | X'); one parameter at a time, nothing else changed; no variant is a selection (the coded cell is the centre).

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| **coded (centre)** | +25.8 | +22.3 | +20.0 | +3.3 | +11.1 |
| ER threshold 0.30 -> 0.150 (x0.5) | +12.0 | +16.9 | +14.6 | +8.9 | +13.7 |
| ER threshold 0.30 -> 0.225 (x0.75) | +23.6 | +23.2 | +20.0 | +8.1 | +14.1 |
| ER threshold 0.30 -> 0.375 (x1.25) | +23.2 | +17.1 | +14.8 | +1.8 | +12.1 |
| ER threshold 0.30 -> 0.450 (x1.5) | +15.0 | +13.3 | +12.5 | +0.0 | +10.6 |
| ER up-size 1.5 -> 1.250 (x0.5) | +22.8 | +17.3 | +15.4 | +0.8 | +10.2 |
| ER up-size 1.5 -> 1.375 (x0.75) | +25.0 | +20.4 | +18.2 | +2.2 | +10.7 |
| ER up-size 1.5 -> 1.625 (x1.25) | +28.1 | +25.6 | +23.0 | +5.2 | +11.5 |
| ER up-size 1.5 -> 1.750 (x1.5) | +30.0 | +28.3 | +25.5 | +6.7 | +11.7 |
| ER down-size 0.5 -> 0.250 (x0.5) | +25.4 | +20.7 | +18.7 | +2.7 | +9.6 |
| ER down-size 0.5 -> 0.375 (x0.75) | +26.0 | +22.9 | +20.6 | +3.2 | +10.3 |
| ER down-size 0.5 -> 0.625 (x1.25) | +29.6 | +25.0 | +22.3 | +3.8 | +11.7 |
| ER down-size 0.5 -> 0.750 (x1.5) | +27.8 | +24.0 | +21.1 | +5.5 | +12.2 |
| zone distance D 20 -> 10 (x0.5) | +21.6 | +19.4 | +18.1 | +0.9 | +8.2 |
| zone distance D 20 -> 15 (x0.75) | +26.0 | +22.0 | +19.7 | +1.7 | +10.4 |
| zone distance D 20 -> 25 (x1.25) | +25.4 | +21.2 | +18.7 | +2.5 | +10.6 |
| zone distance D 20 -> 30 (x1.5) | +26.2 | +20.0 | +17.1 | +1.3 | +8.7 |
| cut fraction 0.5 -> 0.250 (x0.5) | +27.0 | +23.1 | +20.7 | +3.8 | +10.8 |
| cut fraction 0.5 -> 0.375 (x0.75) | +26.7 | +22.9 | +20.5 | +3.6 | +10.8 |
| cut fraction 0.5 -> 0.625 (x1.25) | +25.1 | +22.8 | +20.4 | +3.6 | +11.2 |
| cut fraction 0.5 -> 0.750 (x1.5) | +25.1 | +22.7 | +20.3 | +3.6 | +11.3 |
| PE add dip 3 pt -> 1.50 (x0.5) | +25.8 | +22.2 | +19.9 | +3.0 | +11.2 |
| PE add dip 3 pt -> 2.25 (x0.75) | +25.9 | +22.3 | +19.9 | +3.3 | +11.2 |
| PE add dip 3 pt -> 3.75 (x1.25) | +26.5 | +22.6 | +20.3 | +3.2 | +11.1 |
| PE add dip 3 pt -> 4.50 (x1.5) | +26.0 | +23.0 | +20.6 | +2.7 | +11.1 |
| **mean of the 12 +-25% neighbours** | +25.9 | +22.3 | +19.9 | +3.5 | +11.3 |
| **mean of the 12 +-50% neighbours** | +23.7 | +20.9 | +18.7 | +3.3 | +10.8 |
| min over the 24 neighbours | +12.0 | +13.3 | +12.5 | +0.0 | +8.2 |
| ER up-size reads 1+0.5f: 1.25..1.75; ER down-size 0.5f: 0.25..0.75 (rows above state the value) | | | | | |

Latency (a decision delay between the trigger and the order; the ER sizer and the zone skip act at the signal and have no latency) and the uniform extra cost per lot on every D6 trade:

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| PE confirm market fill delayed 1s | +25.2 | +22.2 | +19.9 | +3.3 | +11.7 |
| PE confirm market fill delayed 3s | +25.9 | +22.9 | +20.5 | +3.1 | +12.2 |
| cut delayed 1s | +25.7 | +22.2 | +19.9 | +3.3 | +11.1 |
| cut delayed 3s | +25.8 | +22.2 | +19.9 | +3.3 | +11.1 |
| both delayed 1s | +25.1 | +22.2 | +19.9 | +3.2 | +11.7 |
| both delayed 3s | +25.9 | +22.8 | +20.4 | +3.1 | +12.2 |
| extra cost 0 pt per lot on every D6 trade | +25.8 | +22.3 | +20.0 | +3.3 | +11.1 |
| extra cost 0.5 pt per lot on every D6 trade | +21.8 | +19.7 | +17.7 | +1.0 | +9.4 |
| extra cost 1 pt per lot on every D6 trade | +20.0 | +17.7 | +15.8 | -1.1 | +7.8 |
| extra cost 2 pt per lot on every D6 trade | +13.3 | +11.8 | +10.0 | -6.2 | +4.6 |
| extra cost 3 pt per lot on every D6 trade | +6.7 | +6.0 | +4.7 | -11.0 | +1.8 |
| extra cost 4 pt per lot on every D6 trade | +0.2 | -0.6 | -1.5 | -16.1 | -1.2 |
| extra cost 6 pt per lot on every D6 trade | -13.9 | -12.0 | -12.3 | -24.7 | -7.0 |
| **breakeven extra cost (pt per lot, linear interpolation)** | 4.0 | 3.9 | 3.8 | 0.7 | 3.6 |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6)

delta vs the stack as it is, $k/wk (L3M | L6M | HOLD | PRE | X'); one parameter at a time, nothing else changed; no variant is a selection (the coded cell is the centre).

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| **coded (centre)** | +100.2 | +82.8 | +76.1 | +27.0 | +13.0 |
| ER threshold 0.30 -> 0.150 (x0.5) | +116.0 | +88.3 | +77.1 | +29.3 | +13.5 |
| ER threshold 0.30 -> 0.225 (x0.75) | +101.2 | +94.5 | +84.3 | +28.6 | +18.8 |
| ER threshold 0.30 -> 0.375 (x1.25) | +98.4 | +65.5 | +61.7 | +15.7 | +10.6 |
| ER threshold 0.30 -> 0.450 (x1.5) | +78.9 | +52.2 | +49.8 | +7.2 | +11.0 |
| ER up-size 1.5 -> 1.250 (x0.5) | +85.6 | +63.3 | +59.0 | +17.4 | +9.9 |
| ER up-size 1.5 -> 1.375 (x0.75) | +95.9 | +73.3 | +67.8 | +22.4 | +11.9 |
| ER up-size 1.5 -> 1.625 (x1.25) | +105.2 | +91.1 | +83.4 | +30.2 | +14.2 |
| ER up-size 1.5 -> 1.750 (x1.5) | +114.4 | +101.6 | +92.3 | +34.4 | +13.8 |
| ER down-size 0.5 -> 0.250 (x0.5) | +97.3 | +72.4 | +68.5 | +15.7 | +9.5 |
| ER down-size 0.5 -> 0.375 (x0.75) | +97.4 | +79.5 | +74.0 | +18.6 | +10.3 |
| ER down-size 0.5 -> 0.625 (x1.25) | +105.3 | +87.5 | +79.4 | +30.5 | +13.3 |
| ER down-size 0.5 -> 0.750 (x1.5) | +110.1 | +88.7 | +80.2 | +35.6 | +12.3 |
| zone distance D 20 -> 10 (x0.5) | +78.1 | +62.9 | +59.8 | +24.4 | +10.2 |
| zone distance D 20 -> 15 (x0.75) | +100.2 | +76.7 | +70.9 | +24.5 | +11.0 |
| zone distance D 20 -> 25 (x1.25) | +90.6 | +77.8 | +70.4 | +26.1 | +12.3 |
| zone distance D 20 -> 30 (x1.5) | +89.4 | +70.3 | +62.5 | +21.8 | +7.0 |
| cut fraction 0.5 -> 0.250 (x0.5) | +104.8 | +86.1 | +78.9 | +26.4 | +13.4 |
| cut fraction 0.5 -> 0.375 (x0.75) | +101.9 | +84.0 | +77.1 | +26.7 | +13.1 |
| cut fraction 0.5 -> 0.625 (x1.25) | +99.7 | +81.7 | +75.1 | +27.8 | +12.3 |
| cut fraction 0.5 -> 0.750 (x1.5) | +103.1 | +83.5 | +76.7 | +27.6 | +11.9 |
| PE add dip 3 pt -> 1.50 (x0.5) | +100.3 | +82.6 | +75.9 | +26.6 | +13.0 |
| PE add dip 3 pt -> 2.25 (x0.75) | +100.2 | +82.8 | +76.0 | +27.0 | +13.1 |
| PE add dip 3 pt -> 3.75 (x1.25) | +100.2 | +82.8 | +76.1 | +26.9 | +12.8 |
| PE add dip 3 pt -> 4.50 (x1.5) | +99.5 | +83.0 | +76.3 | +26.7 | +12.9 |
| **mean of the 12 +-25% neighbours** | +99.7 | +81.4 | +74.7 | +25.4 | +12.8 |
| **mean of the 12 +-50% neighbours** | +98.1 | +77.9 | +71.4 | +24.4 | +11.5 |
| min over the 24 neighbours | +78.1 | +52.2 | +49.8 | +7.2 | +7.0 |
| ER up-size reads 1+0.5f: 1.25..1.75; ER down-size 0.5f: 0.25..0.75 (rows above state the value) | | | | | |

Latency (a decision delay between the trigger and the order; the ER sizer and the zone skip act at the signal and have no latency) and the uniform extra cost per lot on every D6 trade:

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| PE confirm market fill delayed 1s | +98.9 | +82.3 | +75.7 | +27.0 | +13.3 |
| PE confirm market fill delayed 3s | +100.1 | +83.1 | +76.4 | +27.0 | +13.6 |
| cut delayed 1s | +100.8 | +83.2 | +76.5 | +26.9 | +13.0 |
| cut delayed 3s | +101.0 | +83.3 | +76.7 | +26.8 | +13.0 |
| both delayed 1s | +99.5 | +82.7 | +76.1 | +26.9 | +13.3 |
| both delayed 3s | +100.5 | +83.4 | +76.8 | +26.8 | +13.7 |
| extra cost 0 pt per lot on every D6 trade | +100.2 | +82.8 | +76.1 | +27.0 | +13.0 |
| extra cost 0.5 pt per lot on every D6 trade | +86.7 | +68.1 | +62.7 | +16.4 | +5.5 |
| extra cost 1 pt per lot on every D6 trade | +76.1 | +56.9 | +51.9 | +4.7 | -0.9 |
| extra cost 2 pt per lot on every D6 trade | +55.3 | +38.6 | +33.7 | -16.5 | -16.0 |
| extra cost 3 pt per lot on every D6 trade | +31.1 | +16.6 | +12.4 | -37.0 | -28.8 |
| extra cost 4 pt per lot on every D6 trade | +9.1 | -3.2 | -7.1 | -55.9 | -40.4 |
| extra cost 6 pt per lot on every D6 trade | -36.8 | -43.4 | -45.3 | -96.2 | -65.7 |
| **breakeven extra cost (pt per lot, linear interpolation)** | 4.4 | 3.8 | 3.6 | 1.2 | 0.9 |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)

delta vs the stack as it is, $k/wk (L3M | L6M | HOLD | PRE | X'); one parameter at a time, nothing else changed; no variant is a selection (the coded cell is the centre).

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| **coded (centre)** | +45.3 | +35.9 | +33.6 | +14.7 | +9.5 |
| ER threshold 0.30 -> 0.150 (x0.5) | +46.4 | +39.3 | +34.4 | +17.1 | +12.5 |
| ER threshold 0.30 -> 0.225 (x0.75) | +48.2 | +44.0 | +39.7 | +17.1 | +14.1 |
| ER threshold 0.30 -> 0.375 (x1.25) | +42.4 | +27.5 | +25.7 | +8.2 | +9.1 |
| ER threshold 0.30 -> 0.450 (x1.5) | +28.9 | +19.6 | +18.9 | +3.3 | +9.3 |
| ER up-size 1.5 -> 1.250 (x0.5) | +37.1 | +26.4 | +25.0 | +9.4 | +8.5 |
| ER up-size 1.5 -> 1.375 (x0.75) | +43.5 | +32.0 | +30.1 | +12.0 | +9.1 |
| ER up-size 1.5 -> 1.625 (x1.25) | +49.1 | +41.1 | +38.4 | +16.7 | +10.0 |
| ER up-size 1.5 -> 1.750 (x1.5) | +53.8 | +46.0 | +42.7 | +19.1 | +10.2 |
| ER down-size 0.5 -> 0.250 (x0.5) | +43.4 | +32.0 | +30.7 | +12.1 | +7.7 |
| ER down-size 0.5 -> 0.375 (x0.75) | +44.7 | +35.6 | +33.7 | +12.1 | +8.5 |
| ER down-size 0.5 -> 0.625 (x1.25) | +46.8 | +37.4 | +34.7 | +15.7 | +10.4 |
| ER down-size 0.5 -> 0.750 (x1.5) | +50.4 | +39.2 | +36.3 | +17.1 | +10.4 |
| zone distance D 20 -> 10 (x0.5) | +38.0 | +30.7 | +30.1 | +11.5 | +6.0 |
| zone distance D 20 -> 15 (x0.75) | +46.1 | +33.6 | +31.7 | +12.5 | +7.4 |
| zone distance D 20 -> 25 (x1.25) | +44.0 | +34.6 | +32.2 | +12.6 | +8.9 |
| zone distance D 20 -> 30 (x1.5) | +43.3 | +32.4 | +29.7 | +10.6 | +6.0 |
| cut fraction 0.5 -> 0.250 (x0.5) | +48.1 | +38.9 | +36.2 | +13.7 | +9.9 |
| cut fraction 0.5 -> 0.375 (x0.75) | +45.3 | +36.4 | +34.1 | +13.8 | +9.6 |
| cut fraction 0.5 -> 0.625 (x1.25) | +44.5 | +35.2 | +33.0 | +15.9 | +9.1 |
| cut fraction 0.5 -> 0.750 (x1.5) | +45.8 | +36.3 | +34.1 | +16.1 | +8.8 |
| PE add dip 3 pt -> 1.50 (x0.5) | +45.2 | +35.8 | +33.5 | +14.5 | +9.6 |
| PE add dip 3 pt -> 2.25 (x0.75) | +45.2 | +35.8 | +33.5 | +14.7 | +9.6 |
| PE add dip 3 pt -> 3.75 (x1.25) | +46.3 | +36.4 | +34.1 | +14.7 | +9.4 |
| PE add dip 3 pt -> 4.50 (x1.5) | +45.3 | +36.5 | +34.2 | +14.2 | +9.5 |
| **mean of the 12 +-25% neighbours** | +45.5 | +35.8 | +33.4 | +13.8 | +9.6 |
| **mean of the 12 +-50% neighbours** | +43.8 | +34.4 | +32.2 | +13.2 | +9.0 |
| min over the 24 neighbours | +28.9 | +19.6 | +18.9 | +3.3 | +6.0 |
| ER up-size reads 1+0.5f: 1.25..1.75; ER down-size 0.5f: 0.25..0.75 (rows above state the value) | | | | | |

Latency (a decision delay between the trigger and the order; the ER sizer and the zone skip act at the signal and have no latency) and the uniform extra cost per lot on every D6 trade:

| variant | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| PE confirm market fill delayed 1s | +44.6 | +35.8 | +33.5 | +14.8 | +10.1 |
| PE confirm market fill delayed 3s | +45.8 | +36.7 | +34.4 | +14.7 | +10.6 |
| cut delayed 1s | +45.1 | +35.8 | +33.6 | +14.2 | +9.5 |
| cut delayed 3s | +46.0 | +36.3 | +34.1 | +14.3 | +9.5 |
| both delayed 1s | +44.5 | +35.7 | +33.6 | +14.2 | +10.1 |
| both delayed 3s | +46.0 | +36.8 | +34.6 | +14.2 | +10.6 |
| extra cost 0 pt per lot on every D6 trade | +45.3 | +35.9 | +33.6 | +14.7 | +9.5 |
| extra cost 0.5 pt per lot on every D6 trade | +38.4 | +29.5 | +27.9 | +9.3 | +6.6 |
| extra cost 1 pt per lot on every D6 trade | +33.7 | +24.1 | +22.8 | +4.6 | +3.7 |
| extra cost 2 pt per lot on every D6 trade | +24.3 | +15.6 | +14.3 | -5.2 | -2.3 |
| extra cost 3 pt per lot on every D6 trade | +13.4 | +5.8 | +4.8 | -14.2 | -7.5 |
| extra cost 4 pt per lot on every D6 trade | +3.1 | -3.5 | -4.3 | -22.6 | -12.6 |
| extra cost 6 pt per lot on every D6 trade | -19.7 | -22.2 | -22.2 | -40.1 | -23.6 |
| **breakeven extra cost (pt per lot, linear interpolation)** | 4.3 | 3.6 | 3.5 | 1.5 | 1.6 |

## 7. Placebos, drift, regime, information
Placebos (rank = share of the placebo deltas below the real delta; 1.00 = the real composite beats every draw). Each placebo changes ONE piece of the composite and keeps the rest real, so it tests that piece's information given the rest. STRUCTURE note: the shuffled-ER placebo still earns most of the composite's recent gain at research lots (+54k L6M of +83k; +9k of +22k at live lots) because shuffled multipliers under the sized-governor reading still loosen the day/week locks on days that hold a 1.5; the real ER information is the margin over the placebo (rank 0.99-1.00 L6M/HOLD, PRE 0.88 live / 1.00 research, X' 0.46 live).
#### LIVE lots (engine books)
| placebo (draws) | what is randomised | rank of the real D6 delta L6M | HOLD | PRE | X' | placebo mean delta L6M $k | HOLD | PRE |
|---|---|---|---|---|---|---|---|---|
| ER (100) | ER multiplier shuffled within book x session x ~2-month stratum (sized governors follow the shuffled multipliers) | 1.00 | 1.00 | 0.88 | 0.46 | +9.4 | +8.1 | +0.1 |
| ZONE (100) | zone skip: random signals at the same fire rate (book x session x side x target-distance strata) | 0.98 | 0.99 | 0.98 | 0.94 | +11.4 | +10.5 | -1.2 |
| PE (100) | PE confirmation at random print seconds of the same ET day (same events, same direction) | 1.00 | 1.00 | 0.85 | 0.73 | +17.8 | +15.3 | +2.2 |

#### RESEARCH lots
| placebo (draws) | what is randomised | rank of the real D6 delta L6M | HOLD | PRE | X' | placebo mean delta L6M $k | HOLD | PRE |
|---|---|---|---|---|---|---|---|---|
| ER (100) | ER multiplier shuffled within book x session x ~2-month stratum (sized governors follow the shuffled multipliers) | 0.99 | 1.00 | 1.00 | 0.87 | +54.3 | +49.5 | +8.1 |
| ZONE (100) | zone skip: random signals at the same fire rate (book x session x side x target-distance strata) | 1.00 | 1.00 | 1.00 | 0.99 | +47.2 | +45.3 | +9.1 |
| PE (100) | PE confirmation at random print seconds of the same ET day (same events, same direction) | 0.87 | 0.93 | 0.92 | 0.29 | +80.3 | +73.3 | +25.3 |

Quarterly delta, $k/wk, live lots (engine books):
| 2023Q2 (13w) | 2023Q3 (13w) | 2023Q4 (13w) | 2024Q1 (13w) | 2024Q2 (13w) | 2024Q3 (14w) | 2024Q4 (13w) | 2025Q1 (13w) | 2025Q2 (13w) | 2025Q3 (13w) | 2025Q4 (13w) | 2026Q1 (5w) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| +11.3 | +18.2 | -1.2 | +4.7 | +16.0 | +12.8 | +7.8 | -1.4 | -14.9 | +19.2 | +17.9 | +37.6 |

Quarterly delta, $k/wk, research lots:
| 2023Q2 (13w) | 2023Q3 (13w) | 2023Q4 (13w) | 2024Q1 (13w) | 2024Q2 (13w) | 2024Q3 (14w) | 2024Q4 (13w) | 2025Q1 (13w) | 2025Q2 (13w) | 2025Q3 (13w) | 2025Q4 (13w) | 2026Q1 (5w) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| +21.1 | +14.4 | -17.4 | +19.6 | +46.7 | +45.5 | +42.7 | +6.6 | +6.7 | +86.2 | +43.5 | +177.1 |

Regime (entry-day vol tercile of the library, row-level delta $k/wk), live lots:
| window | vol tercile 0 (low) $k/wk (rows) | tercile 1 | tercile 2 (high) |
|---|---|---|---|
| L6M | +4.7 (1432) | +2.1 (1321) | +15.5 (3883) |
| HOLD | +5.7 (1786) | +0.2 (1531) | +14.1 (4014) |
| PRE | +3.0 (4365) | +0.7 (4192) | -0.4 (8059) |
| X' | +1.8 (1790) | +3.1 (1383) | +6.3 (2680) |

research lots:
| window | vol tercile 0 (low) $k/wk (rows) | tercile 1 | tercile 2 (high) |
|---|---|---|---|
| L6M | +20.4 (1432) | +18.0 (1321) | +44.4 (3883) |
| HOLD | +20.9 (1786) | +12.5 (1531) | +42.6 (4014) |
| PRE | +11.9 (4365) | +0.4 (4192) | +14.6 (8059) |
| X' | +4.7 (1790) | +2.2 (1383) | +6.2 (2680) |

Information (the ER sizer is the only predictor-type piece; IC is of the ER(20) value at the signal vs the S73 N outcome, engine books, week-clustered t; IC decay by horizon, the time-shifted-feature placebo and the calibration curve were NOT run: the sizer acts at the signal only):
| window | Spearman IC (ER20 vs outcome pts/planned lot, S73 N, engine rows) | week-clustered t | hit rate ER>=0.30 | ER<0.30 | mean pts ER>=0.30 | ER<0.30 | n |
|---|---|---|---|---|---|---|---|
| L6M | +0.045 | 2.5 | 0.577 | 0.539 | +5.77 | +0.54 | 2441 / 4195 |
| HOLD | +0.042 | 1.5 | 0.572 | 0.535 | +5.16 | +0.17 | 2706 / 4625 |
| PRE | +0.019 | 1.5 | 0.552 | 0.538 | +2.76 | +0.77 | 6365 / 10251 |
| X' | +0.020 | 1.0 | 0.532 | 0.536 | +0.67 | +0.53 | 2476 / 3377 |

## 8. What was coded, what could not be, and the labels (read before using a number)
* **Selection labels.** Every piece was chosen in earlier programs after looking at L6M/HOLD/L3M: the split (L2SE pooled PRE-selected cell: the dip/F grid was selected on PRE+X'; its recent look was one look), the ER sizer (T2/TG-1: post-hoc-selected threshold 0.30 and 1.5/0.5), the Asia-stopped cut (STACK-2: post-hoc premise, condition selected on PRE+X'), the 8-line no-trade set (ZONES-2: post-hoc-selected set, its own walk-forward chain is negative and the PRE+X'-only fit picks different lines), the PE 45-s three-bar (CONFIRM-2: PRE+X' winner of 2,820 PE cells; restricted to NY-AM/NY-PM post hoc after the recent look), Native stops (LIVE_STOP_JOIN: lead, live n=8). This composite is a joint read-out of those choices, not a new selection; nothing here was tuned.
* **Tag -> research-book mapping:** K6 = KB, P6 = PE (PB3B), U6 = SM (D6 tag table: SM Asia/London = U6), H6 = HM, M6 = MV, A6 = PB, N6 = DN, O6 not in the tag table. The lock-engine stack has 6 books (ST HM WT KB SM PE). **M6 (MV, live 2), A6 (PB, live 1) and O6 (live 1) are NOT in this stack**: their lots are not scored, so every live-lot number is the four engine books K6 P6 U6 H6 only (`live4`; `live+` adds ST and WT at research/2.35 as the brief allows). The unscored books also feed the real stack's cut rule and day/week governors (the governors here are per book, as in the lock engine).
* **Live lots per session** (research tags; pre follows London, close follows NY-PM: an ASSUMPTION): KB 2 everywhere; PE 7 in asia/london/pre/nyam, 0 in nypm/close (so the NY-PM PE confirmation is research-lot only); SM 4 in asia/london/pre; HM 4 in asia, 2 in nyam. A session with lot 0 takes no trade and holds none. The governors' planned-lot R uses each book's nominal (maximum) live lot; a smaller session lot is a fraction of it.
* **(1) split:** the L2SE pooled cell used everywhere (S73: 70/30, dip 3, 1-of-8 gate, veto imb5 <= -0.40; stop at the original level; target re-based from the average).
* **(2) PE confirmation:** held PE signal in nyam/nypm -> the first 45-s three-bar (`c2_pat` R_three on `bars_store/tc/45s`: two down candles then a candle closing above the previous high; short mirrored; known at the candle's last print second) after the signal, before the original stop level is touched and before the library arm end (opposite signal / time block) -> MARKET at that candle's close + 1 tick, filled the next print second; 70% there, the 30% on a 3-pt dip after the fill (risk-capped on the original stop distance, MAXLOTS 2), stop at the ORIGINAL level, target = average + the original target distance. No confirmation = no trade in those sessions. Not reproducible from the library: the split's gate/veto on the confirmed add (not applied: the add fills more often than S73's), "session lots 0" as a hold-killer (handled by the lot table, not as a mid-hold event), and the old target does not kill the hold. Confirmed on 67% of PE nyam/nypm signals (nyam 55-59%, nypm 68-70% in L6M/PRE), mean wait about 14 min; per planned lot in L6M the confirmed rows earn +4.4 (nyam) / +1.0 (nypm) more than the plain split.
* **(3) ER sizer:** Kaufman ER(20) on 5-min bars at the signal, x1.5 at/above 0.30, x0.5 below (39% of engine signals at/above). Governors (sl_lib BASE: day entry test +5R/-2R, day give-back arm 2R keep 50%, week floor 12R): `sized` = R multiplied, per book and per day, by the largest ER multiplier among that book's admitted trades of the day (the week floor by the largest day multiplier of the week); a day-static reading: it is not causal inside the day (an earlier trade's lock sees a later 1.5); `base` = unmultiplied planned-lot R. The multiplier is applied BEFORE the stack rule.
* **(4) stack rule:** a book that ENTERED in Asia stopped (first stop of the episode) -> the other same-side open books cut 50% at the market (next second, 0.995 + 0.242 fee per lot); brackets keep their levels, sizes halve; fires about 2.6 a week at live lots, 4.1 at research lots (all in Asia by construction, ~149 weeks).
* **(5) no-trade set:** a FRESH line among the 8 coded (PD mid, 1-h kijun, 4-h Keltner upper, 4-h bar mid, RTH Camarilla H3, 15-m OTE 62 / 70.5 / 79) within 20 pts of the entry and not beyond the target -> skip, decided at the signal (all sessions; for PE nyam/nypm before the hold starts). Fires on 15.1% of all signals (12.2% in L6M). The three profile lines are absent.
* **(6) stops:** Native 1.28 pts per stop exit vs the library's 1.01 (p0 reduced by 0.27 per lot on stop-type exits); the 2.45 join = LIVE-CAL basis. Target-fill correction: none (basis N). M and LIVE-P9 target bases were not re-run for the composite.
* **Lock-engine feedback:** every scenario runs the exact 3-pass loop; the cut and the sizer change which later signals the day/week governors admit (most of the cut's recent gain in STACK-2).
* **Not done:** capacity at depth (no mbp-10 join at the PE/cut seconds), IC decay by horizon, calibration, anchored/rolling walk-forward (the composite has no fitted parameter; each piece's own chain is in its report), M-basis rerun, MV/PB/O6 books.

## 9. Bookkeeping
UF_TRIALS side=followup_sundaystack (62 configurations, n_eff 6); DECISIONS.md prereg line (sha in the line); RECENT_WINS `out/recent_wins/sundaystack.csv`; result pickles `out/sundaystack/res_<lots>.pkl`, `qA_<lots>.pkl` (sensitivity), `qP_<lots>.pkl` (placebo daily series), `qT_<lots>.pkl` (QUANT columns). Reproduce: `python3 -I run_all.py <research|live4|live+>` (about 2 min each), `quant_A.py`, `quant_P.py <lots> 100`, `quant_total.py`, `write_final.py`.
