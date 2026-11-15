# DS3_LONDON_RANGE - T-LONDON-RANGE: range-used-up rule applied LONDON ONLY (W-LR, PRIORITY 2 of DIRECTIVE_BACK_TO_D7_20261114). Rebuilt 2026-11-15T09:44Z by code/th_londonrange/lr_page.py. Research only, NO PASS claim.
**VERDICT (plain): 610 cell-months done; 17 (cell,scope) pass the tolerant gate in every present window incl. recent and older (leads, before placebo read): LS075/london beats-all-3-placebos in 0 of 3 windows; LS1/all beats-all-3-placebos in 2 of 3 windows; LS1/london beats-all-3-placebos in 0 of 3 windows; LS125/london beats-all-3-placebos in 3 of 3 windows; LS15/london beats-all-3-placebos in 0 of 0 windows; LS2/london beats-all-3-placebos in 0 of 0 windows; LH1/all beats-all-3-placebos in 0 of 0 windows; LH1/london beats-all-3-placebos in 0 of 0 windows. No PASS claim.**

Prereg autopilot/LONDON_RANGE_PREREG.md (sha in DECISIONS.md, logged before scoring). Base JN05W2 exact engine, all layers ON, measured fills, shared TP cache. Identity (hook path active at k=1e9-neutral and empty rule): TL3_LR_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_LR_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## Reference JN05W2 per window (the numbers every delta below is against)

| scope | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| all | mean 19136 $/wk, maxDD -52233, worst wk -36371, stops/wk 10.35, n 1875 | mean 25135 $/wk, maxDD -52233, worst wk -36371, stops/wk 10.99, n 4169 | mean 18260 $/wk, maxDD -92044, worst wk -55145, stops/wk 10.66, n 7452 | mean 12678 $/wk, maxDD -82063, worst wk -68947, stops/wk 9.90, n 1677 | mean 10345 $/wk, maxDD -92243, worst wk -52547, stops/wk 9.43, n 7520 | mean 3609 $/wk, maxDD -76154, worst wk -21663, stops/wk 10.82, n 3149 | mean 11196 $/wk, maxDD -92243, worst wk -68947, stops/wk 10.14, n 19798 |
| london | mean 3518 $/wk, maxDD -65592, worst wk -34041, stops/wk 2.74, n 673 | mean 2048 $/wk, maxDD -65592, worst wk -34041, stops/wk 2.89, n 1406 | mean 2247 $/wk, maxDD -65592, worst wk -34041, stops/wk 2.61, n 2567 | mean 2516 $/wk, maxDD -38672, worst wk -16453, stops/wk 2.16, n 523 | mean 27 $/wk, maxDD -107771, worst wk -39833, stops/wk 2.98, n 2527 | mean 727 $/wk, maxDD -37099, worst wk -16566, stops/wk 2.42, n 835 | mean 1043 $/wk, maxDD -107771, worst wk -39833, stops/wk 2.67, n 6452 |
| asia | mean 13845 $/wk, maxDD -48376, worst wk -29690, stops/wk 6.24, n 875 | mean 19655 $/wk, maxDD -48376, worst wk -29690, stops/wk 6.35, n 2012 | mean 14670 $/wk, maxDD -102727, worst wk -62327, stops/wk 5.87, n 3332 | mean 8167 $/wk, maxDD -46389, worst wk -30201, stops/wk 4.50, n 566 | mean 9132 $/wk, maxDD -63865, worst wk -37135, stops/wk 4.19, n 2497 | mean 2595 $/wk, maxDD -61311, worst wk -34597, stops/wk 4.16, n 904 | mean 9057 $/wk, maxDD -102727, worst wk -62327, stops/wk 4.68, n 7299 |
| nyam | mean 971 $/wk, maxDD -16913, worst wk -8442, stops/wk 1.29, n 271 | mean 1708 $/wk, maxDD -21686, worst wk -11029, stops/wk 1.67, n 600 | mean 944 $/wk, maxDD -65217, worst wk -23257, stops/wk 2.15, n 1265 | mean 586 $/wk, maxDD -37519, worst wk -30584, stops/wk 3.24, n 492 | mean 1083 $/wk, maxDD -41313, worst wk -15070, stops/wk 2.22, n 2011 | mean -105 $/wk, maxDD -52582, worst wk -17426, stops/wk 4.21, n 1143 | mean 720 $/wk, maxDD -83868, worst wk -30584, stops/wk 2.76, n 4911 |
| nypm | mean 801 $/wk, maxDD -6510, worst wk -3362, stops/wk 0.08, n 56 | mean 1724 $/wk, maxDD -6510, worst wk -3362, stops/wk 0.08, n 151 | mean 400 $/wk, maxDD -31119, worst wk -8513, stops/wk 0.04, n 288 | mean 1409 $/wk, maxDD -4387, worst wk -2150, stops/wk 0.00, n 96 | mean 103 $/wk, maxDD -41773, worst wk -6944, stops/wk 0.03, n 485 | mean 392 $/wk, maxDD -14720, worst wk -6465, stops/wk 0.02, n 267 | mean 376 $/wk, maxDD -41773, worst wk -8513, stops/wk 0.03, n 1136 |

**LOT BASIS AND FEES.** All JN05W2-family sets run at BASE (box) lots; live trades x1.75 of these lots, so every $ figure here scales by about 1.75 for live. The raw exact engine charges $1.18 per contract round trip (not the FEES.md $4.84) with the engine own fills, and lr_score sums that raw net_fee. A skip rule removes contracts and so saves fees: the second figure in each mean cell, "at $4.84 RT", is the delta mean/wk repriced at $4.84 RT per contract (d mean - 3.66 x delta lots/wk). No rerun was needed.

## 0. Method (short)
- Rule (London = engine session 1, 02:00-08:30 ET; Asia, NY AM, NY PM untouched): at a fresh entry signal F = ATR-only forecast ln range x last close; rem = F - range so far since 02:00; target dist = stop_pts x target_r. Skip (S) if target dist > k x rem; half size (H) same trigger; shrink (T) target to k x rem (floor 0.35 x target). rem <= 0 counts as used up. Gate applies to the seven live books K7 P7 U7 H7 M7 A7 O7.
- Forecast (a): ridge walk-forward (expanding, min 120 days, refit every 10 days) of the session ln range on prior-day / 5 / 20 / 14-day session range and RTH range history; rebuilt from NQ 1-min bars for the FULL history (identity with W-RU fc.parquet on 2024-10+: max abs diff 0.0). First prediction 2023-07-21: about 3.5 months of X' (2023-04..07-20) the rule is inactive = JN05W2. London R2 out of sample (2023-07..2026-11) 0.247.
- Windows: L3M 2026-08..10, L6M 2026-05..10, HOLD 2025-11..2026-10, GAP 2025-07..10, PRE 2024-02..2025-06, X' 2023-04..2024-01, FULL 43 months. Metrics per window vs JN05W2 on the same months: d mean $/wk, max DD (cum daily) cut % (positive = smaller), d worst week $, full stops/wk cell(ref), best-5 weeks kept (cell $ in the 5 best JN05W2 weeks / their $), winning weeks turned losing (w2l).
- Tolerant gate per window: maxDD not worse by more than 2%, worst week not worse by more than 2% of the ref worst week, mean not lower by more than 3% of the ref mean. LEAD = gate in L3M, L6M AND every present older window (HOLD, PRE, X'), drawdown cut > 0 in L6M. GAP reported, not gated.
- Placebos (exact engine): forecast row and range-so-far both taken 11 / 23 / 37 panel days earlier, same rule, same k. Beside every skip row. A lead is only called strong if it beats all three placebos on DD cut AND mean in most windows.
- Recent max DD is one week (2026-W44): section 6 shows DD with that week removed from cell and reference.

## 1. Variant (i) skip, London only, all books

**(i) skip k grid** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS05 | -4109 $/wk (at $4.84 RT: -3965), DD -4.3%, ww +2290, stops 9.21(10.35), b5 69%, w2l 0 | -1178 $/wk (at $4.84 RT: -1028), DD -4.3%, ww +2290, stops 9.78(10.99), b5 91%, w2l 1 | -1456 $/wk (at $4.84 RT: -1307), DD -5.4%, ww -7707, stops 9.45(10.66), b5 97%, w2l 3 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD -3/-5/-4, mean -4570/-3831/-1928 | pl11/23/37 DD -3/-5/-4, mean -2878/-642/-901 | pl11/23/37 DD -20/-26/-65, mean -2158/-484/-2275 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS075 | -475 $/wk (at $4.84 RT: -380), DD +5.0%, ww +6113, stops 9.51(10.35), b5 84%, w2l 0 | +248 $/wk (at $4.84 RT: +350), DD +5.0%, ww +6113, stops 10.23(10.99), b5 95%, w2l 1 | -539 $/wk (at $4.84 RT: -433), DD +4.4%, ww -4438, stops 9.95(10.66), b5 92%, w2l 2 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD +3/-12/+1, mean -3005/-2686/-1904 | pl11/23/37 DD +3/-12/+1, mean -2600/-167/-1133 | pl11/23/37 DD -4/-10/-26, mean -1271/+6/-1770 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS1 | +2847 $/wk (at $4.84 RT: +2918), DD +4.7%, ww +5052, stops 9.51(10.35), b5 94%, w2l 0 | +1746 $/wk (at $4.84 RT: +1824), DD +4.7%, ww +5052, stops 10.35(10.99), b5 97%, w2l 1 | +466 $/wk (at $4.84 RT: +546), DD +13.6%, ww +3431, stops 10.11(10.66), b5 95%, w2l 3 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD -7/-19/-2, mean -5037/-2811/-482 | pl11/23/37 DD -7/-19/-2, mean -1947/-17/-21 | pl11/23/37 DD +4/+5/-6, mean -772/+527/-796 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS125 | +3978 $/wk (at $4.84 RT: +4036), DD +4.7%, ww +4283, stops 9.59(10.35), b5 100%, w2l 0 | +2375 $/wk (at $4.84 RT: +2444), DD +4.7%, ww +4283, stops 10.39(10.99), b5 100%, w2l 1 | +782 $/wk (at $4.84 RT: +850), DD +18.0%, ww -4704, stops 10.15(10.66), b5 98%, w2l 2 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD -10/-10/-2, mean -2776/-2396/+52 | pl11/23/37 DD -10/-10/-2, mean -657/+574/-3 | pl11/23/37 DD +7/+1/+1, mean -130/+495/-264 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS15 | +2748 $/wk (at $4.84 RT: +2804), DD +3.7%, ww +4283, stops 9.66(10.35), b5 99%, w2l 0 | +2047 $/wk (at $4.84 RT: +2110), DD +3.7%, ww +4283, stops 10.42(10.99), b5 101%, w2l 1 | +758 $/wk (at $4.84 RT: +820), DD +9.7%, ww -1619, stops 10.16(10.66), b5 98%, w2l 2 | n/a | n/a | n/a | n/a |
| LS2 | +726 $/wk (at $4.84 RT: +772), DD -5.4%, ww +1551, stops 10.12(10.35), b5 94%, w2l 0 | +772 $/wk (at $4.84 RT: +825), DD -5.4%, ww +1551, stops 10.69(10.99), b5 102%, w2l 1 | +536 $/wk (at $4.84 RT: +590), DD +9.7%, ww -1619, stops 10.30(10.66), b5 98%, w2l 2 | n/a | n/a | n/a | n/a |

**(i) skip k grid** (scope london; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS05 | -2489 $/wk (at $4.84 RT: -2299), DD +36.8%, ww +15553, stops 0.91(2.74), b5 39%, w2l 4 | +218 $/wk (at $4.84 RT: +409), DD +36.8%, ww +15553, stops 1.07(2.89), b5 55%, w2l 5 | -441 $/wk (at $4.84 RT: -254), DD +36.8%, ww +15553, stops 0.88(2.61), b5 61%, w2l 11 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD +52/+55/+71, mean -2693/-285/-925 | pl11/23/37 DD +36/+55/+35, mean -1686/+1056/-242 | pl11/23/37 DD +36/+55/+28, mean -979/+856/-1186 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS075 | -75 $/wk (at $4.84 RT: +50), DD +26.5%, ww +8176, stops 1.52(2.74), b5 63%, w2l 2 | +477 $/wk (at $4.84 RT: +606), DD +26.5%, ww +8176, stops 1.71(2.89), b5 74%, w2l 5 | -43 $/wk (at $4.84 RT: +91), DD +26.5%, ww +8176, stops 1.53(2.61), b5 80%, w2l 11 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD +42/+29/+37, mean -1454/-1086/-1314 | pl11/23/37 DD +4/+29/+37, mean -1690/+418/-868 | pl11/23/37 DD +4/+29/+37, mean -549/+292/-1055 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS1 | +3622 $/wk (at $4.84 RT: +3723), DD +28.5%, ww +9375, stops 1.52(2.74), b5 106%, w2l 1 | +2124 $/wk (at $4.84 RT: +2225), DD +28.5%, ww +9375, stops 1.90(2.89), b5 91%, w2l 1 | +991 $/wk (at $4.84 RT: +1094), DD +28.5%, ww +9375, stops 1.76(2.61), b5 95%, w2l 5 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD +26/+13/+30, mean -3747/-1659/-761 | pl11/23/37 DD +9/+13/+30, mean -1365/+848/-296 | pl11/23/37 DD +9/+13/+30, mean -446/+1210/-643 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS125 | +4623 $/wk (at $4.84 RT: +4711), DD +35.3%, ww +14170, stops 1.60(2.74), b5 114%, w2l 1 | +2532 $/wk (at $4.84 RT: +2621), DD +35.3%, ww +14170, stops 1.94(2.89), b5 99%, w2l 1 | +1171 $/wk (at $4.84 RT: +1261), DD +35.3%, ww +10461, stops 1.84(2.61), b5 101%, w2l 4 | n/a | n/a | n/a | n/a |
| &nbsp;&nbsp;placebo | pl11/23/37 DD +29/+5/+25, mean -1770/-1451/+12 | pl11/23/37 DD +17/+5/+25, mean -188/+1174/-159 | pl11/23/37 DD +17/+5/+25, mean +156/+1013/+7 | placebo n/a | placebo n/a | placebo n/a | placebo n/a |
| LS15 | +3568 $/wk (at $4.84 RT: +3648), DD +35.3%, ww +13238, stops 1.75(2.74), b5 113%, w2l 1 | +2437 $/wk (at $4.84 RT: +2520), DD +35.3%, ww +13238, stops 2.02(2.89), b5 99%, w2l 1 | +1193 $/wk (at $4.84 RT: +1275), DD +35.3%, ww +8786, stops 1.90(2.61), b5 97%, w2l 3 | n/a | n/a | n/a | n/a |
| LS2 | +1923 $/wk (at $4.84 RT: +1984), DD +34.5%, ww +9293, stops 2.28(2.74), b5 103%, w2l 0 | +1520 $/wk (at $4.84 RT: +1587), DD +34.5%, ww +9293, stops 2.32(2.89), b5 87%, w2l 0 | +1100 $/wk (at $4.84 RT: +1169), DD +34.5%, ww +8786, stops 2.05(2.61), b5 87%, w2l 1 | n/a | n/a | n/a | n/a |

**Max DD with the single week 2026-W44 removed from cell and reference** (scope all; ref DD vs cell DD, cut %, d mean x W44)

| cell | L3M | L6M | HOLD | FULL |
|---|---|---|---|---|
| LS05 | DD -40708 vs ref -43405 (+6.2%), mean -4636; with W44: -4.3% | DD -40708 vs ref -43405 (+6.2%), mean -1316; with W44: -4.3% | DD -96974 vs ref -92044 (-5.4%), mean -1529; with W44: -5.4% | n/a |
| LS075 | DD -37743 vs ref -43405 (+13.0%), mean -1097; with W44: +5.0% | DD -37743 vs ref -43405 (+13.0%), mean -23; with W44: +5.0% | DD -88016 vs ref -92044 (+4.4%), mean -688; with W44: +4.4% | n/a |
| LS1 | DD -40680 vs ref -43405 (+6.3%), mean +2512; with W44: +4.7% | DD -40680 vs ref -43405 (+6.3%), mean +1542; with W44: +4.7% | DD -79523 vs ref -92044 (+13.6%), mean +340; with W44: +13.6% | n/a |
| LS125 | DD -40680 vs ref -43405 (+6.3%), mean +3736; with W44: +4.7% | DD -40680 vs ref -43405 (+6.3%), mean +2196; with W44: +4.7% | DD -75512 vs ref -92044 (+18.0%), mean +662; with W44: +18.0% | n/a |
| LS15 | DD -40680 vs ref -43405 (+6.3%), mean +2446; with W44: +3.7% | DD -40680 vs ref -43405 (+6.3%), mean +1874; with W44: +3.7% | DD -83151 vs ref -92044 (+9.7%), mean +647; with W44: +9.7% | n/a |
| LS2 | DD -41109 vs ref -43405 (+5.3%), mean +658; with W44: -5.4% | DD -41109 vs ref -43405 (+5.3%), mean +741; with W44: -5.4% | DD -83151 vs ref -92044 (+9.7%), mean +516; with W44: +9.7% | n/a |

### Lead check (skip)

| cell | scope | lead? | windows present | gate passed | beats placebos (DD and mean) per window |
|---|---|---|---|---|---|
| LS05 | all | no | L3M,L6M,HOLD |  | L3M:N, L6M:N, HOLD:dd |
| LS05 | london | no | L3M,L6M,HOLD | L6M | L3M:N, L6M:N, HOLD:N |
| LS075 | all | no | L3M,L6M,HOLD | L3M,L6M | L3M:Y, L6M:Y, HOLD:dd |
| LS075 | london | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD | L3M:mean, L6M:mean, HOLD:N |
| LS1 | all | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD | L3M:Y, L6M:Y, HOLD:dd |
| LS1 | london | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD | L3M:mean, L6M:mean, HOLD:N |
| LS125 | all | no | L3M,L6M,HOLD | L3M,L6M | L3M:Y, L6M:Y, HOLD:Y |
| LS125 | london | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD | L3M:Y, L6M:Y, HOLD:Y |
| LS15 | all | no | L3M,L6M,HOLD | L3M,L6M |  |
| LS15 | london | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD |  |
| LS2 | all | no | L3M,L6M,HOLD |  |  |
| LS2 | london | LEAD | L3M,L6M,HOLD | L3M,L6M,HOLD |  |

## 2. Variants (ii) half size and (iii) shrink target to the remaining range (no placebos queued unless a lead; section 7 lists what is queued)

**(ii) half size** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LH05 | -2210 $/wk (at $4.84 RT: -2159), DD +4.1%, ww +3328, stops 10.58(10.35), b5 88%, w2l 0 | -470 $/wk (at $4.84 RT: -419), DD +4.1%, ww +3328, stops 11.11(10.99), b5 97%, w2l 1 | -462 $/wk (at $4.84 RT: -413), DD +13.5%, ww -487, stops 10.70(10.66), b5 98%, w2l 1 | n/a | n/a | n/a | n/a |
| LH075 | -812 $/wk (at $4.84 RT: -776), DD +8.7%, ww +4727, stops 10.50(10.35), b5 94%, w2l 0 | +151 $/wk (at $4.84 RT: +187), DD +8.7%, ww +4727, stops 11.07(10.99), b5 100%, w2l 0 | -27 $/wk (at $4.84 RT: +8), DD +16.0%, ww -487, stops 10.74(10.66), b5 98%, w2l 0 | n/a | n/a | n/a | n/a |
| LH1 | +102 $/wk (at $4.84 RT: +131), DD +8.7%, ww +2327, stops 10.50(10.35), b5 97%, w2l 0 | +423 $/wk (at $4.84 RT: +452), DD +8.7%, ww +2327, stops 11.07(10.99), b5 99%, w2l 0 | +156 $/wk (at $4.84 RT: +180), DD +16.5%, ww +1916, stops 10.72(10.66), b5 98%, w2l 0 | n/a | n/a | n/a | n/a |
| LH125 | +319 $/wk (at $4.84 RT: +343), DD +8.7%, ww +1945, stops 10.50(10.35), b5 98%, w2l 0 | +473 $/wk (at $4.84 RT: +497), DD +8.7%, ww +1945, stops 11.07(10.99), b5 101%, w2l 0 | +90 $/wk (at $4.84 RT: +110), DD +15.7%, ww +765, stops 10.74(10.66), b5 100%, w2l 0 | n/a | n/a | n/a | n/a |

**(ii) half size** (scope london; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LH05 | -1611 $/wk (at $4.84 RT: -1553), DD +22.2%, ww +1607, stops 2.89(2.74), b5 70%, w2l 1 | -187 $/wk (at $4.84 RT: -129), DD +22.2%, ww +1607, stops 2.97(2.89), b5 72%, w2l 1 | -614 $/wk (at $4.84 RT: -558), DD +22.2%, ww +1607, stops 2.59(2.61), b5 77%, w2l 3 | n/a | n/a | n/a | n/a |
| LH075 | -672 $/wk (at $4.84 RT: -631), DD +16.1%, ww +1357, stops 2.82(2.74), b5 80%, w2l 0 | +80 $/wk (at $4.84 RT: +121), DD +16.1%, ww +1357, stops 2.93(2.89), b5 84%, w2l 0 | -284 $/wk (at $4.84 RT: -243), DD +16.1%, ww +1357, stops 2.63(2.61), b5 87%, w2l 1 | n/a | n/a | n/a | n/a |
| LH1 | +658 $/wk (at $4.84 RT: +691), DD +10.3%, ww +1357, stops 2.82(2.74), b5 99%, w2l 0 | +687 $/wk (at $4.84 RT: +719), DD +10.3%, ww +1357, stops 2.93(2.89), b5 92%, w2l 0 | +172 $/wk (at $4.84 RT: +204), DD +10.3%, ww +1357, stops 2.63(2.61), b5 94%, w2l 1 | n/a | n/a | n/a | n/a |
| LH125 | +875 $/wk (at $4.84 RT: +903), DD +7.8%, ww +2556, stops 2.82(2.74), b5 104%, w2l 0 | +737 $/wk (at $4.84 RT: +764), DD +7.8%, ww +2556, stops 2.93(2.89), b5 96%, w2l 0 | +191 $/wk (at $4.84 RT: +219), DD +7.8%, ww +2556, stops 2.65(2.61), b5 98%, w2l 1 | n/a | n/a | n/a | n/a |

**(iii) shrink target** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LT05 | -1822 $/wk (at $4.84 RT: -1882), DD -13.1%, ww -10823, stops 10.20(10.35), b5 90%, w2l 0 | -1661 $/wk (at $4.84 RT: -1715), DD -13.1%, ww -10823, stops 10.65(10.99), b5 97%, w2l 1 | -547 $/wk (at $4.84 RT: -603), DD +19.9%, ww +3558, stops 10.26(10.66), b5 100%, w2l 2 | n/a | n/a | n/a | n/a |
| LT075 | -1117 $/wk (at $4.84 RT: -1156), DD -7.4%, ww -7260, stops 10.35(10.35), b5 96%, w2l 0 | -708 $/wk (at $4.84 RT: -745), DD -7.4%, ww -7260, stops 10.80(10.99), b5 102%, w2l 0 | -47 $/wk (at $4.84 RT: -88), DD +5.2%, ww +5333, stops 10.36(10.66), b5 100%, w2l 1 | n/a | n/a | n/a | n/a |
| LT1 | -212 $/wk (at $4.84 RT: -250), DD -5.9%, ww -5000, stops 10.35(10.35), b5 96%, w2l 0 | -544 $/wk (at $4.84 RT: -579), DD -5.9%, ww -5000, stops 10.80(10.99), b5 98%, w2l 0 | +187 $/wk (at $4.84 RT: +150), DD +10.7%, ww +5491, stops 10.36(10.66), b5 100%, w2l 2 | n/a | n/a | n/a | n/a |
| LT125 | +308 $/wk (at $4.84 RT: +277), DD -4.7%, ww -4370, stops 10.50(10.35), b5 98%, w2l 0 | +84 $/wk (at $4.84 RT: +54), DD -4.7%, ww -4370, stops 10.88(10.99), b5 101%, w2l 0 | +363 $/wk (at $4.84 RT: +331), DD +4.8%, ww -1931, stops 10.45(10.66), b5 101%, w2l 2 | n/a | n/a | n/a | n/a |

**(iii) shrink target** (scope london; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LT05 | -521 $/wk (at $4.84 RT: -572), DD +4.0%, ww +6317, stops 2.43(2.74), b5 84%, w2l 0 | -942 $/wk (at $4.84 RT: -993), DD +4.0%, ww +6317, stops 2.51(2.89), b5 88%, w2l 1 | -540 $/wk (at $4.84 RT: -593), DD +4.0%, ww +6317, stops 2.21(2.61), b5 92%, w2l 2 | n/a | n/a | n/a | n/a |
| LT075 | +156 $/wk (at $4.84 RT: +122), DD +7.9%, ww +8464, stops 2.66(2.74), b5 94%, w2l 0 | -126 $/wk (at $4.84 RT: -160), DD +7.9%, ww +8464, stops 2.70(2.89), b5 92%, w2l 1 | +124 $/wk (at $4.84 RT: +86), DD +7.9%, ww +8464, stops 2.32(2.61), b5 97%, w2l 3 | n/a | n/a | n/a | n/a |
| LT1 | +1178 $/wk (at $4.84 RT: +1146), DD +14.6%, ww +9330, stops 2.66(2.74), b5 101%, w2l 0 | +289 $/wk (at $4.84 RT: +257), DD +14.6%, ww +9330, stops 2.70(2.89), b5 94%, w2l 0 | +447 $/wk (at $4.84 RT: +414), DD +14.6%, ww +9330, stops 2.32(2.61), b5 99%, w2l 0 | n/a | n/a | n/a | n/a |
| LT125 | +1450 $/wk (at $4.84 RT: +1423), DD +15.2%, ww +9526, stops 2.82(2.74), b5 102%, w2l 0 | +607 $/wk (at $4.84 RT: +579), DD +15.2%, ww +9526, stops 2.78(2.89), b5 95%, w2l 0 | +512 $/wk (at $4.84 RT: +483), DD +15.2%, ww +3761, stops 2.38(2.61), b5 99%, w2l 0 | n/a | n/a | n/a | n/a |

## 3. Per book (London slice of the all-books skip runs: delta of the book own London trades; books interact only through the shared engine) and exact per-book-gated cells if run


**LS05** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -1689 $/wk (at $4.84 RT: -1669), DD +7.8%, ww +120, stops 0.23(0.38), b5 67%, w2l 1 | -1055 $/wk (at $4.84 RT: -1031), DD -20.6%, ww +120, stops 0.27(0.46), b5 93%, w2l 2 | -899 $/wk (at $4.84 RT: -874), DD +13.5%, ww +604, stops 0.23(0.40), b5 76%, w2l 4 | n/a | n/a |
| P7 | -1298 $/wk (at $4.84 RT: -1235), DD +0.0%, ww +0, stops 0.68(0.61), b5 84%, w2l 0 | +306 $/wk (at $4.84 RT: +368), DD +0.0%, ww +0, stops 0.42(0.49), b5 110%, w2l 0 | -526 $/wk (at $4.84 RT: -467), DD -35.3%, ww +0, stops 0.52(0.52), b5 99%, w2l 2 | n/a | n/a |
| U7 | -1910 $/wk (at $4.84 RT: -1885), DD -69.0%, ww -1644, stops 2.51(3.27), b5 76%, w2l 1 | -1228 $/wk (at $4.84 RT: -1200), DD -2.0%, ww +39, stops 2.51(3.42), b5 83%, w2l 3 | -748 $/wk (at $4.84 RT: -721), DD +25.4%, ww +3611, stops 2.42(3.39), b5 62%, w2l 5 | n/a | n/a |
| H7 | +183 $/wk (at $4.84 RT: +182), DD -14.2%, ww -1196, stops 0.68(0.61), b5 100%, w2l 0 | +161 $/wk (at $4.84 RT: +160), DD +9.5%, ww +0, stops 0.95(0.84), b5 103%, w2l 0 | +142 $/wk (at $4.84 RT: +141), DD +7.2%, ww +0, stops 1.27(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +788 $/wk (at $4.84 RT: +826), DD +52.9%, ww +10957, stops 0.53(1.14), b5 67%, w2l 1 | +773 $/wk (at $4.84 RT: +814), DD +53.3%, ww +9162, stops 0.88(1.26), b5 58%, w2l 3 | +625 $/wk (at $4.84 RT: +666), DD +36.5%, ww +4986, stops 0.94(1.27), b5 64%, w2l 5 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -183 $/wk (at $4.84 RT: -185), DD -62.5%, ww -321, stops 0.53(0.30), b5 86%, w2l 0 | -136 $/wk (at $4.84 RT: -138), DD -43.7%, ww -646, stops 0.80(0.57), b5 94%, w2l 0 | -50 $/wk (at $4.84 RT: -52), DD -43.7%, ww -646, stops 0.81(0.61), b5 96%, w2l 2 | n/a | n/a |

**LS075** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -1102 $/wk (at $4.84 RT: -1094), DD +7.8%, ww +1146, stops 0.38(0.38), b5 76%, w2l 1 | -467 $/wk (at $4.84 RT: -453), DD -13.6%, ww +1146, stops 0.38(0.46), b5 90%, w2l 1 | -526 $/wk (at $4.84 RT: -509), DD +5.0%, ww +1965, stops 0.33(0.40), b5 80%, w2l 3 | n/a | n/a |
| P7 | +445 $/wk (at $4.84 RT: +489), DD +0.0%, ww +0, stops 0.61(0.61), b5 95%, w2l 0 | +882 $/wk (at $4.84 RT: +924), DD +0.0%, ww +0, stops 0.38(0.49), b5 110%, w2l 0 | -282 $/wk (at $4.84 RT: -239), DD -35.3%, ww +0, stops 0.48(0.52), b5 100%, w2l 2 | n/a | n/a |
| U7 | -530 $/wk (at $4.84 RT: -516), DD -18.2%, ww -4026, stops 2.74(3.27), b5 84%, w2l 2 | -690 $/wk (at $4.84 RT: -674), DD -11.4%, ww +0, stops 2.93(3.42), b5 86%, w2l 4 | -284 $/wk (at $4.84 RT: -267), DD +25.4%, ww +1525, stops 2.80(3.39), b5 76%, w2l 6 | n/a | n/a |
| H7 | +274 $/wk (at $4.84 RT: +273), DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | +161 $/wk (at $4.84 RT: +160), DD -9.1%, ww +0, stops 0.88(0.84), b5 103%, w2l 0 | +142 $/wk (at $4.84 RT: +141), DD +1.8%, ww +0, stops 1.23(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +657 $/wk (at $4.84 RT: +687), DD +34.7%, ww +3714, stops 0.68(1.14), b5 79%, w2l 1 | +584 $/wk (at $4.84 RT: +616), DD +35.2%, ww +3714, stops 0.95(1.26), b5 70%, w2l 2 | +441 $/wk (at $4.84 RT: +473), DD +3.1%, ww +3714, stops 1.09(1.27), b5 76%, w2l 4 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -218 $/wk (at $4.84 RT: -219), DD -42.1%, ww -229, stops 0.46(0.30), b5 86%, w2l 0 | -222 $/wk (at $4.84 RT: -223), DD -43.7%, ww -646, stops 0.76(0.57), b5 94%, w2l 0 | -30 $/wk (at $4.84 RT: -32), DD -43.7%, ww -646, stops 0.75(0.61), b5 96%, w2l 1 | n/a | n/a |

**LS1** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -609 $/wk (at $4.84 RT: -605), DD +9.4%, ww +1375, stops 0.38(0.38), b5 79%, w2l 1 | -439 $/wk (at $4.84 RT: -429), DD -9.2%, ww +1375, stops 0.38(0.46), b5 88%, w2l 1 | -247 $/wk (at $4.84 RT: -235), DD +8.9%, ww +1455, stops 0.33(0.40), b5 84%, w2l 4 | n/a | n/a |
| P7 | +1049 $/wk (at $4.84 RT: +1083), DD +0.0%, ww +0, stops 0.61(0.61), b5 101%, w2l 0 | +1251 $/wk (at $4.84 RT: +1284), DD +0.0%, ww +0, stops 0.38(0.49), b5 110%, w2l 0 | +191 $/wk (at $4.84 RT: +224), DD -15.4%, ww +0, stops 0.46(0.52), b5 100%, w2l 1 | n/a | n/a |
| U7 | +321 $/wk (at $4.84 RT: +333), DD -18.2%, ww -4026, stops 2.74(3.27), b5 88%, w2l 1 | -527 $/wk (at $4.84 RT: -516), DD -44.9%, ww +0, stops 3.08(3.42), b5 96%, w2l 3 | -548 $/wk (at $4.84 RT: -535), DD -12.0%, ww +1525, stops 2.99(3.39), b5 86%, w2l 5 | n/a | n/a |
| H7 | +274 $/wk (at $4.84 RT: +273), DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | +92 $/wk (at $4.84 RT: +92), DD -9.1%, ww +0, stops 0.88(0.84), b5 100%, w2l 0 | +84 $/wk (at $4.84 RT: +83), DD -0.9%, ww +0, stops 1.23(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +2030 $/wk (at $4.84 RT: +2054), DD +39.8%, ww +3714, stops 0.68(1.14), b5 98%, w2l 0 | +1532 $/wk (at $4.84 RT: +1557), DD +40.3%, ww +3714, stops 0.95(1.26), b5 92%, w2l 0 | +1022 $/wk (at $4.84 RT: +1045), DD +21.9%, ww +3634, stops 1.09(1.27), b5 90%, w2l 1 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -218 $/wk (at $4.84 RT: -219), DD -42.1%, ww -229, stops 0.46(0.30), b5 86%, w2l 0 | -163 $/wk (at $4.84 RT: -164), DD -28.0%, ww -646, stops 0.72(0.57), b5 100%, w2l 0 | -36 $/wk (at $4.84 RT: -36), DD -28.0%, ww -646, stops 0.73(0.61), b5 100%, w2l 1 | n/a | n/a |

**LS125** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -59 $/wk (at $4.84 RT: -57), DD +9.4%, ww +1375, stops 0.38(0.38), b5 87%, w2l 1 | -152 $/wk (at $4.84 RT: -143), DD -9.2%, ww +1375, stops 0.38(0.46), b5 90%, w2l 1 | -79 $/wk (at $4.84 RT: -70), DD +7.0%, ww +1455, stops 0.33(0.40), b5 87%, w2l 4 | n/a | n/a |
| P7 | +1088 $/wk (at $4.84 RT: +1117), DD +0.0%, ww +0, stops 0.61(0.61), b5 103%, w2l 0 | +1336 $/wk (at $4.84 RT: +1365), DD +0.0%, ww +0, stops 0.38(0.49), b5 110%, w2l 0 | +475 $/wk (at $4.84 RT: +504), DD -10.2%, ww +0, stops 0.44(0.52), b5 99%, w2l 1 | n/a | n/a |
| U7 | +811 $/wk (at $4.84 RT: +820), DD -18.2%, ww -4795, stops 2.74(3.27), b5 100%, w2l 1 | -298 $/wk (at $4.84 RT: -289), DD -44.9%, ww -411, stops 3.08(3.42), b5 106%, w2l 3 | -578 $/wk (at $4.84 RT: -568), DD -18.7%, ww +0, stops 3.05(3.39), b5 93%, w2l 5 | n/a | n/a |
| H7 | +274 $/wk (at $4.84 RT: +273), DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | +92 $/wk (at $4.84 RT: +92), DD -9.1%, ww +0, stops 0.88(0.84), b5 100%, w2l 0 | +61 $/wk (at $4.84 RT: +60), DD -3.6%, ww +0, stops 1.23(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +2082 $/wk (at $4.84 RT: +2102), DD +44.1%, ww +4913, stops 0.76(1.14), b5 99%, w2l 0 | +1561 $/wk (at $4.84 RT: +1583), DD +41.3%, ww +4913, stops 0.99(1.26), b5 92%, w2l 2 | +924 $/wk (at $4.84 RT: +945), DD +21.4%, ww +2270, stops 1.11(1.27), b5 92%, w2l 3 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -218 $/wk (at $4.84 RT: -219), DD -42.1%, ww -229, stops 0.46(0.30), b5 86%, w2l 0 | -163 $/wk (at $4.84 RT: -164), DD -28.0%, ww -646, stops 0.72(0.57), b5 100%, w2l 0 | -21 $/wk (at $4.84 RT: -22), DD -28.0%, ww -646, stops 0.71(0.61), b5 100%, w2l 0 | n/a | n/a |

**LS15** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -339 $/wk (at $4.84 RT: -335), DD +9.4%, ww +1375, stops 0.38(0.38), b5 81%, w2l 1 | -394 $/wk (at $4.84 RT: -386), DD -13.8%, ww +1375, stops 0.38(0.46), b5 90%, w2l 1 | -294 $/wk (at $4.84 RT: -285), DD -4.6%, ww +1455, stops 0.33(0.40), b5 87%, w2l 3 | n/a | n/a |
| P7 | +899 $/wk (at $4.84 RT: +927), DD +0.0%, ww +0, stops 0.61(0.61), b5 102%, w2l 0 | +1512 $/wk (at $4.84 RT: +1539), DD +0.0%, ww +0, stops 0.38(0.49), b5 110%, w2l 0 | +640 $/wk (at $4.84 RT: +666), DD -20.4%, ww +0, stops 0.44(0.52), b5 101%, w2l 1 | n/a | n/a |
| U7 | +811 $/wk (at $4.84 RT: +820), DD -18.2%, ww -4795, stops 2.74(3.27), b5 100%, w2l 1 | -252 $/wk (at $4.84 RT: -243), DD -39.9%, ww -411, stops 3.08(3.42), b5 106%, w2l 3 | -437 $/wk (at $4.84 RT: -428), DD -7.6%, ww +0, stops 3.07(3.39), b5 93%, w2l 4 | n/a | n/a |
| H7 | +274 $/wk (at $4.84 RT: +273), DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | +92 $/wk (at $4.84 RT: +92), DD -9.1%, ww +0, stops 0.88(0.84), b5 100%, w2l 0 | +83 $/wk (at $4.84 RT: +83), DD -1.0%, ww +0, stops 1.21(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +1260 $/wk (at $4.84 RT: +1278), DD +44.1%, ww +4913, stops 0.91(1.14), b5 102%, w2l 0 | +1222 $/wk (at $4.84 RT: +1242), DD +42.3%, ww +4913, stops 1.07(1.26), b5 95%, w2l 2 | +762 $/wk (at $4.84 RT: +781), DD +21.6%, ww +2270, stops 1.15(1.27), b5 92%, w2l 3 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -157 $/wk (at $4.84 RT: -158), DD -20.8%, ww +0, stops 0.38(0.30), b5 86%, w2l 0 | -133 $/wk (at $4.84 RT: -134), DD -28.0%, ww -646, stops 0.68(0.57), b5 100%, w2l 0 | +4 $/wk (at $4.84 RT: +4), DD -28.0%, ww -646, stops 0.69(0.61), b5 100%, w2l 0 | n/a | n/a |

**LS2** per-book London slice, windows L3M / L6M / HOLD / PRE / X'

| book | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| K7 | -94 $/wk (at $4.84 RT: -89), DD +9.4%, ww +1375, stops 0.46(0.38), b5 90%, w2l 1 | -137 $/wk (at $4.84 RT: -129), DD -9.6%, ww -58, stops 0.46(0.46), b5 90%, w2l 1 | -27 $/wk (at $4.84 RT: -19), DD -5.2%, ww +1134, stops 0.36(0.40), b5 88%, w2l 3 | n/a | n/a |
| P7 | +340 $/wk (at $4.84 RT: +364), DD +0.0%, ww +0, stops 0.61(0.61), b5 99%, w2l 0 | +929 $/wk (at $4.84 RT: +951), DD +0.0%, ww +0, stops 0.38(0.49), b5 108%, w2l 0 | +250 $/wk (at $4.84 RT: +273), DD -20.4%, ww +0, stops 0.44(0.52), b5 101%, w2l 1 | n/a | n/a |
| U7 | -3 $/wk (at $4.84 RT: +1), DD +13.4%, ww +0, stops 3.04(3.27), b5 100%, w2l 1 | -510 $/wk (at $4.84 RT: -504), DD -29.9%, ww +0, stops 3.23(3.42), b5 106%, w2l 3 | -268 $/wk (at $4.84 RT: -261), DD +5.2%, ww +0, stops 3.15(3.39), b5 93%, w2l 3 | n/a | n/a |
| H7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | -45 $/wk (at $4.84 RT: -45), DD -9.1%, ww +0, stops 0.88(0.84), b5 100%, w2l 0 | -9 $/wk (at $4.84 RT: -9), DD -1.0%, ww +0, stops 1.21(1.19), b5 100%, w2l 0 | n/a | n/a |
| M7 | +579 $/wk (at $4.84 RT: +595), DD +27.1%, ww +3275, stops 1.07(1.14), b5 96%, w2l 0 | +638 $/wk (at $4.84 RT: +656), DD +27.7%, ww +3275, stops 1.14(1.26), b5 90%, w2l 2 | +570 $/wk (at $4.84 RT: +588), DD +22.7%, ww +1755, stops 1.19(1.27), b5 88%, w2l 2 | n/a | n/a |
| A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 4.03(4.03), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.96(3.96), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 3.28(3.28), b5 100%, w2l 0 | n/a | n/a |
| O7 | -97 $/wk (at $4.84 RT: -98), DD +0.0%, ww +0, stops 0.30(0.30), b5 86%, w2l 0 | -103 $/wk (at $4.84 RT: -104), DD -28.0%, ww -646, stops 0.65(0.57), b5 100%, w2l 0 | +19 $/wk (at $4.84 RT: +19), DD -28.0%, ww -646, stops 0.67(0.61), b5 100%, w2l 0 | n/a | n/a |

**exact per-book gated LS1_K7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_K7 | -613 $/wk (at $4.84 RT: -604), DD +2.6%, ww +1375, stops 10.35(10.35), b5 97%, w2l 0 | -785 $/wk (at $4.84 RT: -774), DD +2.6%, ww +1375, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_P7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_P7 | +198 $/wk (at $4.84 RT: +232), DD +0.0%, ww +0, stops 10.35(10.35), b5 98%, w2l 0 | +371 $/wk (at $4.84 RT: +403), DD +0.0%, ww +0, stops 10.99(10.99), b5 98%, w2l 1 | -119 $/wk (at $4.84 RT: -89), DD +6.3%, ww -6481, stops 10.80(10.66), b5 98%, w2l 1 | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_U7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_U7 | +1053 $/wk (at $4.84 RT: +1060), DD +4.7%, ww +3863, stops 9.97(10.35), b5 99%, w2l 0 | -303 $/wk (at $4.84 RT: -292), DD +4.7%, ww +2661, stops 10.69(10.99), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_H7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_H7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_M7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_M7 | +1454 $/wk (at $4.84 RT: +1479), DD +0.2%, ww +1485, stops 9.97(10.35), b5 100%, w2l 0 | +644 $/wk (at $4.84 RT: +670), DD +0.2%, ww +1485, stops 10.73(10.99), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_A7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS1_O7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS1_O7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_K7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_K7 | -62 $/wk (at $4.84 RT: -56), DD +2.6%, ww +1375, stops 10.35(10.35), b5 99%, w2l 0 | -395 $/wk (at $4.84 RT: -386), DD +2.6%, ww +1375, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_P7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_P7 | +237 $/wk (at $4.84 RT: +267), DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | +384 $/wk (at $4.84 RT: +412), DD +0.0%, ww +0, stops 10.99(10.99), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_U7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_U7 | +1542 $/wk (at $4.84 RT: +1548), DD +4.7%, ww +3094, stops 9.97(10.35), b5 101%, w2l 0 | -74 $/wk (at $4.84 RT: -65), DD +4.7%, ww +2661, stops 10.69(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_H7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_H7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_M7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_M7 | +1009 $/wk (at $4.84 RT: +1027), DD +0.2%, ww +1485, stops 10.04(10.35), b5 97%, w2l 0 | +805 $/wk (at $4.84 RT: +824), DD +0.2%, ww +1485, stops 10.80(10.99), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_A7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_A7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

**exact per-book gated LS125_O7** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| LS125_O7 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +0 $/wk (at $4.84 RT: +0), DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | n/a |

## 4. D5SK13F_a, D3C_a, D3C_c London only

D5SK13F_a = skip when the forecast ratio pred/fref >= 1.3 (ATR-only forecast, full history). D3C = loss-cut level multiplier by forecast ratio, continuous [0.7, 1.4], exponent 1 (a = ATR-only full history; c = full-UW forecast from W-RU, exists from 2025-03 only so X' and most of PRE are inactive = JN05W2). All with the London-only gate.

**D5SK13F_a / D3C_a / D3C_c** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| D5SK13F_a | -1657 $/wk (at $4.84 RT: -1613), DD -4.2%, ww -2212, stops 10.20(10.35), b5 101%, w2l 1 | +438 $/wk (at $4.84 RT: +520), DD -4.2%, ww -2212, stops 10.31(10.99), b5 97%, w2l 1 | -552 $/wk (at $4.84 RT: -467), DD -42.9%, ww -28699, stops 10.01(10.66), b5 98%, w2l 3 | n/a | n/a | n/a | n/a |
| D3C_a | -3366 $/wk (at $4.84 RT: -3359), DD +8.6%, ww +4479, stops 12.55(10.35), b5 88%, w2l 1 | -3159 $/wk (at $4.84 RT: -3146), DD +8.6%, ww -1196, stops 14.04(10.99), b5 87%, w2l 1 | -1172 $/wk (at $4.84 RT: -1165), DD +5.7%, ww -508, stops 13.54(10.66), b5 90%, w2l 2 | n/a | n/a | n/a | n/a |
| D3C_c | -231 $/wk (at $4.84 RT: -240), DD +7.3%, ww -376, stops 11.03(10.35), b5 94%, w2l 0 | -516 $/wk (at $4.84 RT: -512), DD +7.3%, ww -376, stops 12.71(10.99), b5 93%, w2l 0 | -105 $/wk (at $4.84 RT: -105), DD +8.8%, ww -6089, stops 12.73(10.66), b5 98%, w2l 1 | n/a | n/a | n/a | n/a |

**D5SK13F_a / D3C_a / D3C_c** (scope london; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| D5SK13F_a | -599 $/wk (at $4.84 RT: -543), DD +9.8%, ww +0, stops 2.21(2.74), b5 75%, w2l 0 | +267 $/wk (at $4.84 RT: +366), DD +9.8%, ww +0, stops 1.83(2.89), b5 70%, w2l 1 | +53 $/wk (at $4.84 RT: +162), DD +9.8%, ww +0, stops 1.63(2.61), b5 52%, w2l 3 | n/a | n/a | n/a | n/a |
| D3C_a | -798 $/wk (at $4.84 RT: -785), DD -10.0%, ww -2054, stops 4.79(2.74), b5 73%, w2l 0 | -1599 $/wk (at $4.84 RT: -1585), DD -10.0%, ww -2054, stops 5.90(2.89), b5 62%, w2l 0 | -473 $/wk (at $4.84 RT: -463), DD -10.0%, ww -2054, stops 5.45(2.61), b5 75%, w2l 1 | n/a | n/a | n/a | n/a |
| D3C_c | +1480 $/wk (at $4.84 RT: +1481), DD -12.9%, ww +693, stops 3.20(2.74), b5 104%, w2l 0 | +549 $/wk (at $4.84 RT: +554), DD -12.9%, ww +693, stops 4.57(2.89), b5 102%, w2l 0 | +341 $/wk (at $4.84 RT: +344), DD -12.9%, ww +693, stops 4.58(2.61), b5 97%, w2l 2 | n/a | n/a | n/a | n/a |

**Max DD with the single week 2026-W44 removed from cell and reference** (scope all; ref DD vs cell DD, cut %, d mean x W44)

| cell | L3M | L6M | HOLD | FULL |
|---|---|---|---|---|
| D5SK13F_a | DD -40291 vs ref -43405 (+7.2%), mean -1611; with W44: -4.2% | DD -40291 vs ref -43405 (+7.2%), mean +542; with W44: -4.2% | DD -131531 vs ref -92044 (-42.9%), mean -520; with W44: -42.9% | n/a |
| D3C_a | DD -41711 vs ref -43405 (+3.9%), mean -4012; with W44: +8.6% | DD -41711 vs ref -43405 (+3.9%), mean -3461; with W44: +8.6% | DD -86829 vs ref -92044 (+5.7%), mean -1283; with W44: +5.7% | n/a |
| D3C_c | DD -47428 vs ref -43405 (-9.3%), mean -380; with W44: +7.3% | DD -47428 vs ref -43405 (-9.3%), mean -598; with W44: +7.3% | DD -83986 vs ref -92044 (+8.8%), mean -138; with W44: +8.8% | n/a |

## 5. NY AM version (engine session 3, 09:30-12:00; forecast R2 before 10:00 else R3; never Asia)

**NY AM** (scope all; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| NS05 | -485 $/wk (at $4.84 RT: -458), DD -2.3%, ww -1199, stops 9.97(10.35), b5 93%, w2l 0 | -1357 $/wk (at $4.84 RT: -1325), DD -2.3%, ww -1199, stops 10.61(10.99), b5 91%, w2l 0 | -577 $/wk (at $4.84 RT: -536), DD -1.6%, ww -1134, stops 9.80(10.66), b5 93%, w2l 1 | n/a | n/a | n/a | n/a |
| NS075 | -57 $/wk (at $4.84 RT: -39), DD -2.3%, ww -1199, stops 10.20(10.35), b5 95%, w2l 0 | -857 $/wk (at $4.84 RT: -835), DD -2.3%, ww -1199, stops 10.84(10.99), b5 93%, w2l 0 | +111 $/wk (at $4.84 RT: +137), DD +0.9%, ww +0, stops 10.16(10.66), b5 94%, w2l 1 | n/a | n/a | n/a | n/a |
| NS1 | -250 $/wk (at $4.84 RT: -233), DD -2.3%, ww -1199, stops 10.27(10.35), b5 95%, w2l 0 | -890 $/wk (at $4.84 RT: -872), DD -2.3%, ww -1199, stops 10.88(10.99), b5 94%, w2l 0 | +256 $/wk (at $4.84 RT: +276), DD -9.8%, ww +0, stops 10.41(10.66), b5 99%, w2l 0 | n/a | n/a | n/a | n/a |
| NS125 | -18 $/wk (at $4.84 RT: -7), DD -2.3%, ww -1199, stops 10.27(10.35), b5 98%, w2l 0 | -866 $/wk (at $4.84 RT: -852), DD -2.3%, ww -1199, stops 10.88(10.99), b5 96%, w2l 0 | +107 $/wk (at $4.84 RT: +125), DD -7.2%, ww +0, stops 10.41(10.66), b5 99%, w2l 0 | n/a | n/a | n/a | n/a |

**NY AM** (scope nyam; delta vs JN05W2 on the same months; placebos in the line below each row)

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL |
|---|---|---|---|---|---|---|---|
| NS05 | -469 $/wk (at $4.84 RT: -438), DD +34.5%, ww +2291, stops 0.84(1.29), b5 51%, w2l 3 | -1152 $/wk (at $4.84 RT: -1114), DD +20.4%, ww +4878, stops 1.26(1.67), b5 49%, w2l 6 | -126 $/wk (at $4.84 RT: -77), DD +58.4%, ww +4975, stops 1.23(2.15), b5 62%, w2l 8 | n/a | n/a | n/a | n/a |
| NS075 | -123 $/wk (at $4.84 RT: -103), DD +39.7%, ww +755, stops 1.14(1.29), b5 67%, w2l 2 | -884 $/wk (at $4.84 RT: -858), DD +15.9%, ww +3342, stops 1.52(1.67), b5 61%, w2l 4 | +277 $/wk (at $4.84 RT: +309), DD +64.0%, ww +2745, stops 1.61(2.15), b5 75%, w2l 4 | n/a | n/a | n/a | n/a |
| NS1 | -315 $/wk (at $4.84 RT: -297), DD +23.9%, ww +0, stops 1.22(1.29), b5 70%, w2l 2 | -951 $/wk (at $4.84 RT: -930), DD +18.2%, ww +2587, stops 1.56(1.67), b5 62%, w2l 4 | +327 $/wk (at $4.84 RT: +352), DD +51.6%, ww +1832, stops 1.86(2.15), b5 83%, w2l 3 | n/a | n/a | n/a | n/a |
| NS125 | -151 $/wk (at $4.84 RT: -139), DD +12.7%, ww +0, stops 1.22(1.29), b5 79%, w2l 2 | -897 $/wk (at $4.84 RT: -880), DD +11.1%, ww +2587, stops 1.56(1.67), b5 66%, w2l 3 | +169 $/wk (at $4.84 RT: +190), DD +46.3%, ww +3031, stops 1.88(2.15), b5 81%, w2l 3 | n/a | n/a | n/a | n/a |

## 6. Winning JN05W2 weeks turned losing, and what the rule skipped in them

### LS05

**HOLD: 3 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2025-12-15/2025-12-21: JN05W2 +3178 -> cell -1159 (delta -4336); rule fired on 281 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 12-15 04:08 M7 +1 lots 1: ref +1199; 12-15 04:43 P7 +1 lots 3: ref +3591; 12-15 04:45 P7 +1 lots 3: ref +3591; 12-15 04:57 K7 +1 lots 1: ref +1199; 12-15 06:28 M7 +1 lots 1: ref +1199; 12-16 02:38 M7 -1 lots 1: ref -692; 12-16 02:57 K7 +1 lots 1: ref +1199; 12-16 03:11 M7 +1 lots 1: ref +1199; 12-16 03:20 U7 +1 lots 2: ref +2398; 12-16 04:06 K7 +1 lots 1: ref +1199; 12-16 04:26 M7 +1 lots 2: ref -1639; 12-16 04:34 P7 +1 lots 4: ref -1439; 12-16 05:11 P7 +1 lots 1: ref +1199; 12-16 05:18 M7 +1 lots 1: ref +1199; 12-16 06:02 P7 +1 lots 2: ref +2398; 12-16 06:39 K7 +1 lots 1: ref +1199; 12-16 07:30 K7 +1 lots 2: ref -1739; 12-16 07:33 M7 +1 lots 2: ref -1324; 12-16 07:34 P7 +1 lots 4: ref -2539; 12-17 05:32 M7 +1 lots 2: ref -1414; 12-17 08:20 U7 -1 lots 4: ref -4410; 12-18 02:20 U7 +1 lots 1: ref +1199; 12-18 02:42 K7 +1 lots 1: ref +1199; 12-18 04:00 M7 +1 lots 1: ref +1199; 12-18 05:33 K7 +1 lots 1: ref +1199; 12-18 07:21 M7 +1 lots 1: ref +1199; 12-19 02:48 K7 -1 lots 1: ref -882; 12-19 03:00 M7 +1 lots 2: ref -1459; 12-19 03:03 K7 +1 lots 2: ref -1854; 12-19 06:18 K7 -1 lots 1: ref +1199; 12-19 07:36 M7 -1 lots 1: ref -740; 12-19 07:40 U7 -1 lots 2: ref -2322
- week 2026-04-27/2026-05-03: JN05W2 +13603 -> cell -1956 (delta -15559); rule fired on 117 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 04-28 03:03 P7 -1 lots 2: ref +2393; 04-28 04:03 K7 -1 lots 1: ref -815; 04-28 04:39 K7 +1 lots 1: ref -920; 04-28 05:26 M7 -1 lots 1: ref +1199; 04-28 06:09 P7 -1 lots 2: ref +2398; 04-28 06:12 K7 -1 lots 2: ref +2398; 04-28 06:25 M7 -1 lots 2: ref +2398; 04-28 07:48 K7 -1 lots 1: ref +1199; 04-28 08:08 M7 -1 lots 2: ref -1654; 04-28 08:10 P7 -1 lots 4: ref -2404; 04-28 08:24 K7 -1 lots 2: ref -1192; 04-30 02:33 K7 +1 lots 1: ref +1199; 04-30 02:53 P7 +1 lots 2: ref +2398; 04-30 03:10 U7 +1 lots 2: ref +2403; 04-30 03:24 K7 +1 lots 1: ref +1199; 04-30 03:31 M7 +1 lots 1: ref +1199; 04-30 03:48 P7 +1 lots 2: ref -1259; 04-30 04:31 P7 +1 lots 4: ref -2624; 04-30 05:21 K7 -1 lots 1: ref -960; 04-30 05:30 K7 +1 lots 1: ref -642; 04-30 05:36 M7 +1 lots 1: ref -662; 04-30 06:03 P7 +1 lots 2: ref +2398; 04-30 06:22 M7 +1 lots 1: ref -615; 04-30 07:11 M7 +1 lots 1: ref +1199; 04-30 07:12 K7 +1 lots 1: ref +1199; 04-30 07:48 M7 +1 lots 1: ref +1199; 04-30 08:11 P7 +1 lots 1: ref +1199; 04-30 08:12 K7 +1 lots 1: ref +1199
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -9181 (delta -14587); rule fired on 123 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 05-26 03:56 P7 -1 lots 2: ref -1244; 05-26 04:36 P7 -1 lots 2: ref -1234; 05-26 05:22 M7 +1 lots 2: ref +2403; 05-26 05:27 P7 +1 lots 1: ref +1199; 05-26 05:27 K7 +1 lots 1: ref +1199; 05-26 05:30 U7 +1 lots 2: ref +2403; 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 04:00 K7 +1 lots 1: ref +1199; 05-27 04:10 U7 +1 lots 4: ref +4790; 05-27 04:40 M7 +1 lots 2: ref +2398; 05-27 04:41 P7 +1 lots 4: ref +4790; 05-27 04:42 K7 +1 lots 1: ref +1199; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398; 05-29 03:37 M7 -1 lots 1: ref -762; 05-29 03:40 U7 -1 lots 2: ref -2492; 05-29 04:03 K7 +1 lots 1: ref +1199; 05-29 05:11 M7 +1 lots 1: ref -840; 05-29 05:20 U7 +1 lots 4: ref -4740; 05-29 07:06 M7 +1 lots 1: ref -665

### LS075

**HOLD: 2 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2025-12-15/2025-12-21: JN05W2 +3178 -> cell -6700 (delta -9878); rule fired on 191 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 12-15 04:43 P7 +1 lots 3: ref +3591; 12-15 04:45 P7 +1 lots 3: ref +3591; 12-15 04:57 K7 +1 lots 1: ref +1199; 12-15 06:28 M7 +1 lots 1: ref +1199; 12-16 03:11 M7 +1 lots 1: ref +1199; 12-16 03:20 U7 +1 lots 2: ref +2398; 12-16 04:06 K7 +1 lots 1: ref +1199; 12-16 04:26 M7 +1 lots 2: ref -1639; 12-16 04:34 P7 +1 lots 4: ref -1439; 12-16 05:11 P7 +1 lots 1: ref +1199; 12-16 05:18 M7 +1 lots 1: ref +1199; 12-16 06:02 P7 +1 lots 2: ref +2398; 12-16 06:39 K7 +1 lots 1: ref +1199; 12-16 07:30 K7 +1 lots 2: ref -1739; 12-16 07:33 M7 +1 lots 2: ref -1324; 12-16 07:34 P7 +1 lots 4: ref -2539; 12-18 04:00 M7 +1 lots 1: ref +1199; 12-18 05:33 K7 +1 lots 1: ref +1199; 12-18 07:21 M7 +1 lots 1: ref +1199; 12-19 06:18 K7 -1 lots 1: ref +1199; 12-19 07:36 M7 -1 lots 1: ref -740; 12-19 07:40 U7 -1 lots 2: ref -2322
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -4768 (delta -10174); rule fired on 65 signals (A7, H7, K7, M7, P7); ref trades removed: 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 04:40 M7 +1 lots 2: ref +2398; 05-27 04:41 P7 +1 lots 4: ref +4790; 05-27 04:42 K7 +1 lots 1: ref +1199; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398

### LS1

**HOLD: 3 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2025-12-15/2025-12-21: JN05W2 +3178 -> cell -2398 (delta -5576); rule fired on 110 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 12-15 04:57 K7 +1 lots 1: ref +1199; 12-15 06:28 M7 +1 lots 1: ref +1199; 12-16 03:20 U7 +1 lots 2: ref +2398; 12-16 04:06 K7 +1 lots 1: ref +1199; 12-16 04:26 M7 +1 lots 2: ref -1639; 12-16 04:34 P7 +1 lots 4: ref -1439; 12-16 05:11 P7 +1 lots 1: ref +1199; 12-16 05:18 M7 +1 lots 1: ref +1199; 12-16 06:02 P7 +1 lots 2: ref +2398; 12-16 06:39 K7 +1 lots 1: ref +1199; 12-16 07:30 K7 +1 lots 2: ref -1739; 12-16 07:33 M7 +1 lots 2: ref -1324; 12-16 07:34 P7 +1 lots 4: ref -2539; 12-18 05:33 K7 +1 lots 1: ref +1199; 12-18 07:21 M7 +1 lots 1: ref +1199
- week 2026-04-20/2026-04-26: JN05W2 +4715 -> cell -370 (delta -5086); rule fired on 37 signals (A7, H7, K7, M7, P7, U7); ref trades removed: 04-23 05:24 K7 +1 lots 1: ref +1199; 04-23 05:49 P7 -1 lots 2: ref -1299; 04-23 06:02 M7 -1 lots 1: ref -622; 04-23 06:04 M7 -1 lots 1: ref -622; 04-23 06:56 M7 +1 lots 1: ref +1199; 04-23 07:09 P7 +1 lots 2: ref -1389; 04-23 07:50 U7 +1 lots 3: ref +3596; 04-24 07:06 K7 +1 lots 1: ref +2403
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -4768 (delta -10174); rule fired on 60 signals (A7, H7, K7, M7, P7); ref trades removed: 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 04:40 M7 +1 lots 2: ref +2398; 05-27 04:41 P7 +1 lots 4: ref +4790; 05-27 04:42 K7 +1 lots 1: ref +1199; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398

### LS125

**HOLD: 2 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2026-04-20/2026-04-26: JN05W2 +4715 -> cell -370 (delta -5086); rule fired on 33 signals (A7, K7, M7, P7, U7); ref trades removed: 04-23 05:24 K7 +1 lots 1: ref +1199; 04-23 05:49 P7 -1 lots 2: ref -1299; 04-23 06:02 M7 -1 lots 1: ref -622; 04-23 06:04 M7 -1 lots 1: ref -622; 04-23 06:56 M7 +1 lots 1: ref +1199; 04-23 07:09 P7 +1 lots 2: ref -1389; 04-23 07:50 U7 +1 lots 3: ref +3596; 04-24 07:06 K7 +1 lots 1: ref +2403
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -4768 (delta -10174); rule fired on 58 signals (A7, H7, K7, M7, P7); ref trades removed: 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 04:40 M7 +1 lots 2: ref +2398; 05-27 04:41 P7 +1 lots 4: ref +4790; 05-27 04:42 K7 +1 lots 1: ref +1199; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398

### LS15

**HOLD: 2 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2026-04-20/2026-04-26: JN05W2 +4715 -> cell -370 (delta -5086); rule fired on 33 signals (A7, K7, M7, P7, U7); ref trades removed: 04-23 05:24 K7 +1 lots 1: ref +1199; 04-23 05:49 P7 -1 lots 2: ref -1299; 04-23 06:02 M7 -1 lots 1: ref -622; 04-23 06:04 M7 -1 lots 1: ref -622; 04-23 06:56 M7 +1 lots 1: ref +1199; 04-23 07:09 P7 +1 lots 2: ref -1389; 04-23 07:50 U7 +1 lots 3: ref +3596; 04-24 07:06 K7 +1 lots 1: ref +2403
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -232 (delta -5638); rule fired on 36 signals (A7, H7, K7, M7, P7); ref trades removed: 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398

### LS2

**HOLD: 2 JN05W2 winning weeks turned losing** (of 38 winning weeks)

- week 2026-04-20/2026-04-26: JN05W2 +4715 -> cell -1284 (delta -5999); rule fired on 5 signals (A7, K7, U7); ref trades removed: 04-23 07:50 U7 +1 lots 3: ref +3596; 04-24 07:06 K7 +1 lots 1: ref +2403
- week 2026-05-25/2026-05-31: JN05W2 +5406 -> cell -232 (delta -5638); rule fired on 35 signals (A7, H7, K7, M7, P7); ref trades removed: 05-26 07:00 K7 -1 lots 1: ref -920; 05-26 07:12 P7 -1 lots 2: ref -1244; 05-26 08:06 M7 +1 lots 1: ref -600; 05-27 07:03 K7 +1 lots 2: ref +2403; 05-27 07:18 P7 +1 lots 1: ref +2403; 05-27 07:34 M7 +1 lots 2: ref +2398

## 7. Bi-weekly walk-forward (re-pick cell vs JN05W2 every 2 weeks on a 26-week train window; needs all 43 months)

| cell | WF beat % | WF DD cut % | WF d mean $/wk |
|---|---|---|---|

## 8. Best setting per book / session with plain strength (filled as windows complete)

| scope | best setting (lowest max DD in L6M among gate-passing, then mean) | L3M | L6M | HOLD | PRE | X' | strength |
|---|---|---|---|---|---|---|---|
| all | LH125 | +319 $/wk (at $4.84 RT: +343), DD +8.7%, ww +1945, stops 10.50(10.35), b5 98%, w2l 0 | +473 $/wk (at $4.84 RT: +497), DD +8.7%, ww +1945, stops 11.07(10.99), b5 101%, w2l 0 | +90 $/wk (at $4.84 RT: +110), DD +15.7%, ww +765, stops 10.74(10.66), b5 100%, w2l 0 | n/a | n/a | LEAD; beats 3 placebos on DD and mean in 0 of 0 windows |
| london | LS15 | +3568 $/wk (at $4.84 RT: +3648), DD +35.3%, ww +13238, stops 1.75(2.74), b5 113%, w2l 1 | +2437 $/wk (at $4.84 RT: +2520), DD +35.3%, ww +13238, stops 2.02(2.89), b5 99%, w2l 1 | +1193 $/wk (at $4.84 RT: +1275), DD +35.3%, ww +8786, stops 1.90(2.61), b5 97%, w2l 3 | n/a | n/a | LEAD; beats 3 placebos on DD and mean in 0 of 0 windows |
