# JOINT STAGE TABLE - NY AM own-checks pool (W-LAYERS, STAMP 2026-11-21 11:43Z; refreshed every 15 min by joint_verdict.py --loop; only rows from the corrected JNT9 array count, the voided 80-combo run feeds nothing)

Per book: BRK/LOSS/LOCK/TAKE varied TOGETHER (reference + top-2 of the stage-1 screen per group, OA(9,4,3,2) = 8 combos + BASE). PICK = best combo on L6M (ulcer, drawdown first, 15% guard); cells = `ulcer fitted/unfitted; $/wk fitted/unfitted; eq = $/wk at equal risk`, 1 lot. Gates: ROLLING walk-forward among the combos + reference (>= 0.58), year colours 2023/24/25 on equal-risk $/wk (RED > 30% fails), search-aware null >= 4/5; 27/30 info only (stage-1 table). KEPT = all gates; otherwise the book keeps today's settings.

| book | pick (levels) | L6M | L3M | rolling WF (fixed) | years | null | verdict |
|---|---|---|---|---|---|---|---|
| B6f77f23d | BRK:BRK4, LOSS:FR_LOSS8, LOCK:LK8, TAKE:ref | 4599/5391; 2556/1393; eq 2995/1393 | 3140/5171; 2638/1214; eq 4344/1214 | 0.54 (fixed 0.452) | GREEN/RED/RED | 2/5 | NOT KEPT: rolling WF 0.54 < 0.58; RED year; null 2/5 |
| B7bfd33b7 | none | - | - | - | - | - | NOT KEPT: no combo beats the reference on L6M within the guard; keeps today's |
| L05350e98 | BRK:ref, LOSS:CU4, LOCK:LK2, TAKE:FR_TAKE4 | 3557/3617; 1137/989; eq 1157/989 | 3754/3761; 1080/1043; eq 1082/1043 | 0.71 (fixed 0.882) | GREEN/RED/GREEN | 1/5 | NOT KEPT: RED year; null 1/5 |
| L488784d8 | BRK:BRK2, LOSS:ref, LOCK:LK5, TAKE:TK5 | 1838/3081; 807/915; eq 1352/915 | 1727/3026; 886/838; eq 1552/838 | 0.69 (fixed 0.699) | RED/RED/RED | 4/5 | NOT KEPT: RED year |
| L6547965c | BRK:BRK4, LOSS:STC4, LOCK:LK7, TAKE:ref | 2107/2993; 1632/1275; eq 2318/1275 | 2289/3163; 377/588; eq 521/588 | 0.42 (fixed 0.57) | RED/GREEN/AMBER | 3/5 | NOT KEPT: rolling WF 0.42 < 0.58; RED year; null 3/5 |
| L7cc56d99 | BRK:ref, LOSS:CU4, LOCK:LK9, TAKE:FR_TAKE6 | 4176/4793; 1304/2445; eq 1496/2445 | 3777/4755; 1182/2166; eq 1488/2166 | 0.48 (fixed 0.548) | GREEN/RED/RED | 1/5 | NOT KEPT: rolling WF 0.48 < 0.58; RED year; null 1/5 |

## INFORMATION FOR JOSH (not a gate)

**Rolling walk-forward, exact definition (wf_gate.rolling).** Periods = 14-day blocks counted from 2023-04-03. For each period P that has at least 182 days of history before it: (i) the TRAILING window is the 182 days before P; (ii) on that window the ULCER (RMS drawdown of the daily P&L at 1 lot) is computed for each of the 8 joint combos and for the reference (the book's own settings); (iii) the combo with the lowest trailing ulcer is chosen if its ulcer is strictly below the reference's, otherwise the REFERENCE is chosen; (iv) when the reference is chosen the period is LEFT OUT (neither win nor loss; it is not in the denominator); (v) otherwise the chosen combo is compared with the reference IN PERIOD P: it WINS when its max drawdown inside the period (cumulative daily P&L from the period start, 1 lot, no scaling) is NOT DEEPER than the reference's (tolerance 1e-9); if the two drawdowns are equal (e.g. both 0), it wins when its period net $ (1 lot) is not lower than the reference's. Periods with no trade in either version are left out. Persistence = wins / counted periods. So 'beats' = period max drawdown first, net $ at 1 lot only as the tie-break; it is NOT equal-risk $, not ulcer of the period, not worst day. A tie on both drawdown and $ counts as a WIN.

Per complete book: (A) ROLLING pick (re-picked each period) and (B) FIXED pick (the L6M pick held in every period, same periods). Cells `win/tie/loss (share ties as losses; share ties left out)`. NOTE the FIXED pick is the L6M pick, so it is in-sample for the last 6 months. Each cell of the counted periods and the share with ties counted as losses / ties left out, for: net $ at 1 lot; $ at equal risk (chosen combo scaled by trailing-window ulcer ratio reference/combo); lower period max drawdown; better worst day (higher min daily P&L in the period). `ref` = periods where the reference was the rolling choice (left out).

| book | mode | periods (ref left out; dd ties) | net $ 1 lot | $ equal risk | lower period max DD | better worst day |
|---|---|---|---|---|---|---|
| B6f77f23d | rolling | 71 (ref 9; dd ties 12; GATE number 0.54) | 32/0/39 (0.45; 0.45) | 35/0/36 (0.49; 0.49) | 31/12/28 (0.44; 0.53) | 29/18/24 (0.41; 0.55) |
| B6f77f23d | fixed c4 | 80 (ref 0; dd ties 1; GATE number 0.44) | 34/0/46 (0.42; 0.42) | 29/0/51 (0.36; 0.36) | 35/1/44 (0.44; 0.44) | 40/10/30 (0.5; 0.57) |
| L05350e98 | rolling | 73 (ref 7; dd ties 13; GATE number 0.71) | 33/6/34 (0.45; 0.49) | 42/0/31 (0.58; 0.58) | 42/13/18 (0.58; 0.7) | 43/15/15 (0.59; 0.74) |
| L05350e98 | fixed c2 | 80 (ref 0; dd ties 66; GATE number 0.86) | 10/58/12 (0.12; 0.45) | 40/4/36 (0.5; 0.53) | 8/66/6 (0.1; 0.57) | 3/75/2 (0.04; 0.6) |
| L488784d8 | rolling | 72 (ref 7; dd ties 3; GATE number 0.69) | 29/0/43 (0.4; 0.4) | 37/0/35 (0.51; 0.51) | 50/3/19 (0.69; 0.72) | 49/5/18 (0.68; 0.73) |
| L488784d8 | fixed c3 | 79 (ref 0; dd ties 1; GATE number 0.67) | 33/0/46 (0.42; 0.42) | 39/0/40 (0.49; 0.49) | 53/1/25 (0.67; 0.68) | 58/1/20 (0.73; 0.74) |
| L6547965c | rolling | 76 (ref 4; dd ties 9; GATE number 0.42) | 36/2/38 (0.47; 0.49) | 41/0/35 (0.54; 0.54) | 28/9/39 (0.37; 0.42) | 21/24/31 (0.28; 0.4) |
| L6547965c | fixed c8 | 80 (ref 0; dd ties 14; GATE number 0.56) | 43/0/37 (0.54; 0.54) | 41/0/39 (0.51; 0.51) | 39/14/27 (0.49; 0.59) | 28/32/20 (0.35; 0.58) |
| L7cc56d99 | rolling | 66 (ref 14; dd ties 14; GATE number 0.48) | 24/6/36 (0.36; 0.4) | 30/0/36 (0.45; 0.45) | 22/14/30 (0.33; 0.42) | 18/23/25 (0.27; 0.42) |
| L7cc56d99 | fixed c1 | 80 (ref 0; dd ties 46; GATE number 0.50) | 16/21/43 (0.2; 0.27) | 28/0/52 (0.35; 0.35) | 12/46/22 (0.15; 0.35) | 6/66/8 (0.07; 0.43) |

Drawdown-first summary over ALL 42 months (2023-04..2026-10), unfitted -> joint L6M pick, 1 lot:

| book | pick | ulcer | max DD | worst week | $/wk |
|---|---|---|---|---|---|
| B6f77f23d | c4 | 9701 -> 19862 | -34800 -> -60285 | -12718 -> -13295 | 966 -> 622 |
| L05350e98 | c2 | 6139 -> 6395 | -19697 -> -19102 | -10924 -> -10924 | 603 -> 549 |
| L488784d8 | c3 | 6695 -> 5404 | -21871 -> -17608 | -14550 -> -9963 | 568 -> 266 |
| L6547965c | c8 | 10976 -> 8957 | -34749 -> -29681 | -10217 -> -9288 | 833 -> 819 |
| L7cc56d99 | c1 | 7938 -> 9209 | -31363 -> -34953 | -15443 -> -15443 | 961 -> 686 |

### Year table behind the colours (information only)

Per period, unfitted -> joint pick at 1 lot. k = equal-risk factor = unfitted ulcer / pick ulcer in that period; equal-risk $/wk of the pick = pick $/wk x k, compared with the unfitted $/wk. The 30% band (AMBER 15-30, RED > 30) is applied to (unfitted $/wk - pick equal-risk $/wk) / |unfitted $/wk|; positive = pick worse. L6M and L3M have no colour. RED-year TYPE (drawdown = period max DD at 1 lot): (a) pick worse on BOTH drawdown and $/wk, (b) drawdown lower but $/wk lower (the unfitted $/wk of that year is shown so a tiny base is visible), (c) drawdown higher but $/wk higher.

| book | period | ulcer | max DD | worst week | $/wk 1 lot | k | equal-risk $/wk (pick vs unfitted) | band % | colour (RED type) |
|---|---|---|---|---|---|---|---|---|---|
| B6f77f23d | 2023 | 4432 -> 4164 | -13355 -> -10966 | -5874 -> -5824 | 619 -> 613 | 1.06 | 653 vs 619 | -5% | GREEN |
| B6f77f23d | 2024 | 6434 -> 15050 | -18598 -> -27743 | -6219 -> -9011 | 941 -> 159 | 0.43 | 68 vs 941 | +93% | RED (a; unfitted \$/wk that year 941) |
| B6f77f23d | 2025 | 9307 -> 14129 | -28409 -> -31782 | -12718 -> -10130 | 1271 -> 1082 | 0.66 | 712 vs 1271 | +44% | RED (a; unfitted \$/wk that year 1271) |
| B6f77f23d | L6M | 5391 -> 4599 | -12737 -> -12216 | -6864 -> -7875 | 1393 -> 2556 | 1.17 | 2995 vs 1393 | -115% | shown only |
| B6f77f23d | L3M | 5171 -> 3140 | -12737 -> -9896 | -6864 -> -4622 | 1214 -> 2638 | 1.65 | 4344 vs 1214 | -258% | shown only |
| L05350e98 | 2023 | 4292 -> 4291 | -10685 -> -10685 | -4944 -> -4944 | 489 -> 503 | 1.00 | 503 vs 489 | -3% | GREEN |
| L05350e98 | 2024 | 4797 -> 5890 | -12566 -> -16451 | -7030 -> -7030 | 715 -> 585 | 0.81 | 477 vs 715 | +33% | RED (a; unfitted \$/wk that year 715) |
| L05350e98 | 2025 | 7040 -> 6912 | -16013 -> -16013 | -10924 -> -10924 | 155 -> 135 | 1.02 | 137 vs 155 | +12% | GREEN |
| L05350e98 | L6M | 3617 -> 3557 | -9608 -> -9608 | -6124 -> -6124 | 989 -> 1137 | 1.02 | 1157 vs 989 | -17% | shown only |
| L05350e98 | L3M | 3761 -> 3754 | -9608 -> -9608 | -6124 -> -6124 | 1043 -> 1080 | 1.00 | 1082 vs 1043 | -4% | shown only |
| L488784d8 | 2023 | 4814 -> 4773 | -14442 -> -10976 | -4269 -> -3834 | 472 -> 182 | 1.01 | 183 vs 472 | +61% | RED (b; unfitted \$/wk that year 472) |
| L488784d8 | 2024 | 4950 -> 4524 | -12964 -> -11321 | -8343 -> -8443 | 382 -> 124 | 1.09 | 136 vs 382 | +64% | RED (b; unfitted \$/wk that year 382) |
| L488784d8 | 2025 | 10663 -> 7909 | -21871 -> -17608 | -14550 -> -9963 | 623 -> 288 | 1.35 | 388 vs 623 | +38% | RED (b; unfitted \$/wk that year 623) |
| L488784d8 | L6M | 3081 -> 1838 | -7378 -> -5341 | -3569 -> -2944 | 915 -> 807 | 1.68 | 1352 vs 915 | -48% | shown only |
| L488784d8 | L3M | 3026 -> 1727 | -6446 -> -5341 | -3569 -> -2944 | 838 -> 886 | 1.75 | 1552 vs 838 | -85% | shown only |
| L6547965c | 2023 | 4358 -> 4690 | -11284 -> -13984 | -5513 -> -8568 | 1140 -> 851 | 0.93 | 791 vs 1140 | +31% | RED (a; unfitted \$/wk that year 1140) |
| L6547965c | 2024 | 11279 -> 6765 | -28664 -> -19502 | -6871 -> -5493 | 959 -> 1202 | 1.67 | 2004 vs 959 | -109% | GREEN |
| L6547965c | 2025 | 9535 -> 8654 | -20324 -> -17306 | -6793 -> -9288 | 915 -> 698 | 1.10 | 768 vs 915 | +16% | AMBER |
| L6547965c | L6M | 2993 -> 2107 | -8124 -> -7256 | -4533 -> -4798 | 1275 -> 1632 | 1.42 | 2318 vs 1275 | -82% | shown only |
| L6547965c | L3M | 3163 -> 2289 | -8124 -> -7256 | -4533 -> -4798 | 588 -> 377 | 1.38 | 521 vs 588 | +11% | shown only |
| L7cc56d99 | 2023 | 3944 -> 4269 | -11074 -> -11883 | -4734 -> -5544 | 1067 -> 1098 | 0.92 | 1014 vs 1067 | +5% | GREEN |
| L7cc56d99 | 2024 | 9348 -> 8676 | -17987 -> -17119 | -6954 -> -8024 | 263 -> 79 | 1.08 | 85 vs 263 | +68% | RED (b; unfitted \$/wk that year 263) |
| L7cc56d99 | 2025 | 10051 -> 13738 | -31363 -> -34953 | -15443 -> -15443 | 873 -> 462 | 0.73 | 338 vs 873 | +61% | RED (a; unfitted \$/wk that year 873) |
| L7cc56d99 | L6M | 4793 -> 4176 | -13326 -> -13192 | -7749 -> -5163 | 2445 -> 1304 | 1.15 | 1496 vs 2445 | +39% | shown only |
| L7cc56d99 | L3M | 4755 -> 3777 | -11089 -> -11458 | -7749 -> -5163 | 2166 -> 1182 | 1.26 | 1488 vs 2166 | +31% | shown only |

42-month totals (2023-04..2026-10, 1 lot), unfitted -> pick:

| book | ulcer | max DD | worst week | $/wk |
|---|---|---|---|---|
| B6f77f23d | 9701 -> 19862 | -34800 -> -60285 | -12718 -> -13295 | 966 -> 622 |
| L05350e98 | 6139 -> 6395 | -19697 -> -19102 | -10924 -> -10924 | 603 -> 549 |
| L488784d8 | 6695 -> 5404 | -21871 -> -17608 | -14550 -> -9963 | 568 -> 266 |
| L6547965c | 10976 -> 8957 | -34749 -> -29681 | -10217 -> -9288 | 833 -> 819 |
| L7cc56d99 | 7938 -> 9209 | -31363 -> -34953 | -15443 -> -15443 | 961 -> 686 |

**SUMMARY (6 of 6 books complete, 0 KEPT):** NOT KEPT on rolling walk-forward (any reason incl. others): 3; on the RED-year band ONLY (walk-forward and null pass): 1; on the null ONLY: 0; RED years of the band-only group by type: (a) 0, (b) 3, (c) 0, other 0.
